---
title: Вспомогательные пакеты SDK для отладки | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- dbgmetric.lib
- registry, Debugging SDK
- Debugging SDK, registry locations
- dbgmetric.h
- metrics [Debugging SDK]
ms.assetid: 80a52e93-4a04-4ab2-8adc-a7847c2dc20b
caps.latest.revision: 29
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 010827bc484ceed7c24c12759a2d6e610abad95e
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47571772"
---
# <a name="sdk-helpers-for-debugging"></a>Вспомогательные пакеты SDK для отладки
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [вспомогательные пакеты SDK для отладки](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/sdk-helpers-for-debugging).  
  
Эти функции и объявления — это глобальный вспомогательные функции для реализации обработчиков отладки, вычислители выражений и поставщики символов в C++.  
  
> [!NOTE]
>  В настоящее время нет управляемых версий этих функций и объявления.  
  
## <a name="overview"></a>Обзор  
 Чтобы отладчиков, вычислители выражений и поставщики символ для использования в Visual Studio они должны быть зарегистрированы. Это делается заданием, разделы и подразделы реестра, также известный как «параметр метрики». Следующие глобальные функции предназначены для упрощения процесса обновления этих метрик. См. в разделе области реестра, чтобы узнать, макет каждого подраздела реестра, который обновляется этими функциями.  
  
## <a name="general-metric-functions"></a>Общие метрики функции  
 Это общие функции, используемые отладчиков. Специализированные функции для вычислители выражений и поставщики символов будут описаны далее.  
  
### <a name="getmetric-method"></a>Метод GetMetric  
 Извлекает значение метрики из реестра.  
  
```cpp#  
HRESULT GetMetric(  
   LPCWSTR pszMachine,  
   LPCWSTR pszType,  
   REFGUID guidSection,  
   LPCWSTR pszMetric,  
   DWORD * pdwValue,  
   LPCWSTR pszAltRoot  
);  
```  
  
|Параметр|Описание|  
|---------------|-----------------|  
|pszMachine|[in] Имя возможно удаленного компьютера, регистрация которого будет записываться (`NULL` означает, что локальный компьютер).|  
|pszType|[in] Один из типов метрик.|  
|guidSection|[in] Идентификатор GUID определенного модуля, средство оценки, исключение, и т.д. Это задает подраздел в разделе типа metric поиск заданного элемента.|  
|pszMetric|[in] Метрика, получить невозможно. Это соответствует имени конкретного значения.|  
|pdwValue|[in] Место хранения метрики по максимуму. Существует несколько видов GetMetric, который может возвращать значение типа DWORD (как в этом примере), строку BSTR, GUID или массив идентификаторов GUID.|  
|pszAltRoot|[in] Корень альтернативный реестра для использования. Значение `NULL` по умолчанию.|  
  
### <a name="setmetric-method"></a>Метод SetMetric  
 Задает указанное значение метрики в реестре.  
  
```cpp#  
HRESULT SetMetric(  
         LPCWSTR pszType,  
         REFGUID guidSection,  
         LPCWSTR pszMetric,  
   const DWORD   dwValue,  
         bool    fUserSpecific,  
         LPCWSTR pszAltRoot  
);  
```  
  
|Параметр|Описание|  
|---------------|-----------------|  
|pszType|[in] Один из типов метрик.|  
|guidSection|[in] Идентификатор GUID определенного модуля, средство оценки, исключение, и т.д. Это задает подраздел в разделе типа metric поиск заданного элемента.|  
|pszMetric|[in] Метрика, получить невозможно. Это соответствует имени конкретного значения.|  
|dwValue|[in] Место хранения значение метрики. Существует несколько видов SetMetric, который может хранить DWORD (в данном примере), строку BSTR, GUID или массив идентификаторов GUID.|  
|fUserSpecific|[in] Значение TRUE, если метрика конкретного пользователя и должен быть записан в куст пользователя вместо hive локального компьютера.|  
|pszAltRoot|[in] Корень альтернативный реестра для использования. Значение `NULL` по умолчанию.|  
  
### <a name="removemetric-method"></a>Метод RemoveMetric  
 Удаляет заданной метрики из реестра.  
  
```cpp#  
HRESULT RemoveMetric(  
   LPCWSTR pszType,  
   REFGUID guidSection,  
   LPCWSTR pszMetric,  
   LPCWSTR pszAltRoot  
);  
```  
  
|Параметр|Описание|  
|---------------|-----------------|  
|pszType|[in] Один из типов метрик.|  
|guidSection|[in] Идентификатор GUID определенного модуля, средство оценки, исключение, и т.д. Это задает подраздел в разделе типа metric поиск заданного элемента.|  
|pszMetric|[in] Метрика для удаления. Это соответствует имени конкретного значения.|  
|pszAltRoot|[in] Корень альтернативный реестра для использования. Значение `NULL` по умолчанию.|  
  
### <a name="enummetricsections-method"></a>Метод EnumMetricSections  
 Перечисляет различные метрики разделы в реестре.  
  
```cpp#  
HRESULT EnumMetricSections(  
   LPCWSTR pszMachine,  
   LPCWSTR pszType,  
   GUID *  rgguidSections,  
   DWORD * pdwSize,  
   LPCWSTR pszAltRoot  
);  
```  
  
|Параметр|Описание|  
|---------------|-----------------|  
|pszMachine|[in] Имя возможно удаленного компьютера, регистрация которого будет записываться (`NULL` означает, что локальный компьютер).|  
|pszType|[in] Один из типов метрик.|  
|rgguidSections|[in, out] Предварительно выделяемые массив идентификаторов GUID для заполнения.|  
|pdwSize|[in] Максимальное количество идентификаторов GUID, которые могут храниться в `rgguidSections` массива.|  
|pszAltRoot|[in] Корень альтернативный реестра для использования. Значение `NULL` по умолчанию.|  
  
## <a name="expression-evaluator-functions"></a>Функции вычислителя выражений  
  
|Функция|Описание|  
|--------------|-----------------|  
|GetEEMetric|Извлекает значение метрики из реестра.|  
|SetEEMetric|Задает указанное значение метрики в реестре.|  
|RemoveEEMetric|Удаляет заданной метрики из реестра.|  
|GetEEMetricFile|Получает имя файла из заданной метрики и загружает их, возвращая содержимое файла в виде строки.|  
  
## <a name="exception-functions"></a>Исключение функции  
  
|Функция|Описание|  
|--------------|-----------------|  
|GetExceptionMetric|Извлекает значение метрики из реестра.|  
|SetExceptionMetric|Задает указанное значение метрики в реестре.|  
|RemoveExceptionMetric|Удаляет заданной метрики из реестра.|  
|RemoveAllExceptionMetrics|Удаляет все метрики исключение из реестра.|  
  
## <a name="symbol-provider-functions"></a>Функции поставщика символов  
  
|Функция|Описание|  
|--------------|-----------------|  
|GetSPMetric|Извлекает значение метрики из реестра.|  
|SetSPMetric|Задает указанное значение метрики в реестре.|  
|RemoveSPMetric|Удаляет заданной метрики из реестра.|  
  
## <a name="enumeration-functions"></a>Функции перечисления  
  
|Функция|Описание|  
|--------------|-----------------|  
|EnumMetricSections|Перечисляет все метрики для указанного типа метрик.|  
|EnumDebugEngine|Перечисляет зарегистрированные отладчики.|  
|EnumEEs|Перечисляет вычислители выражений зарегистрированных.|  
|EnumExceptionMetrics|Перечисляет все метрики исключение.|  
  
## <a name="metric-definitions"></a>Определения метрик  
 Эти определения можно использовать стандартные имена метрик. Имена соответствуют разные разделы реестра и имена значений и определены как строки расширенных символов: например, `extern LPCWSTR metrictypeEngine`.  
  
|Предопределенных типов метрик|Описание: Базовый раздел для...|  
|-----------------------------|---------------------------------------|  
|metrictypeEngine|Все отладочные метрики ядра.|  
|metrictypePortSupplier|Все метрики поставщика порта.|  
|metrictypeException|Все метрики исключение.|  
|metricttypeEEExtension|Все расширения вычислителя выражений.|  
  
|Свойства ядра отладки|Описание|  
|-----------------------------|-----------------|  
|metricAddressBP|Значение ненулевое значение, чтобы указать поддержку для точки останова по адресу.|  
|metricAlwaysLoadLocal|Значение ненулевое значение, чтобы всегда загружать локально обработчика отладки.|  
|metricLoadInDebuggeeSession|НЕ ИСПОЛЬЗУЕТСЯ|  
|metricLoadedByDebuggee|Значение ненулевое значение, чтобы указать, что модуль отладки будет загружаться всегда оператором or, отлаживаемой программы.|  
|metricAttach|Значение ненулевое значение, чтобы указать поддержку для вложения в существующие программы.|  
|metricCallStackBP|Значение ненулевое значение, чтобы указать поддержку для точки останова в стеке вызова.|  
|metricConditionalBP|Значение ненулевое значение, чтобы указать поддержку для параметра условные точки останова.|  
|metricDataBP|Значение ненулевое значение, чтобы указать поддержку для параметра точек останова на изменения в данных.|  
|metricDisassembly|Значение не равно нулю, чтобы указать поддержку для производства вхождения Дизассемблированный код.|  
|metricDumpWriting|Значение ненулевое значение, чтобы указать поддержку для дампа записи (формирования дампа памяти в устройство вывода).|  
|metricENC|Значение не равно нулю, чтобы указать поддержку для изменить и продолжить. **Примечание:** пользовательского модуля отладки никогда не следует задавать, или следует всегда равно 0.|  
|metricExceptions|Значение ненулевое значение, чтобы указать поддержку для исключения.|  
|metricFunctionBP|Значение ненулевое значение, чтобы указать поддержку для именованных точки останова (установка точек останова, останавливающих выполнение при вызове функции определенным именем).|  
|metricHitCountBP|Значение ненулевое значение, чтобы указать поддержку для параметра «попадания в точку» точки останова (точки останова, которые активируются только после попадании определенное число раз).|  
|metricJITDebug|Значение не равно нулю, чтобы указать поддержку для отладки just-in-time (запуске отладчика при возникновении исключения в выполняющийся процесс).|  
|metricMemory|НЕ ИСПОЛЬЗУЕТСЯ|  
|metricPortSupplier|Установите на идентификатор CLSID поставщика порта, если она реализована.|  
|metricRegisters|НЕ ИСПОЛЬЗУЕТСЯ|  
|metricSetNextStatement|Значение ненулевое значение, чтобы указать поддержку для установка следующего оператора (который пропускает выполнение инструкций промежуточного).|  
|metricSuspendThread|Значение ненулевое значение, чтобы указать поддержку для приостановки выполнения потока.|  
|metricWarnIfNoSymbols|Значение ненулевое значение, чтобы указать, что пользователь должен получать уведомления, если символов нет.|  
|metricProgramProvider|Укажите идентификатор CLSID поставщика программы.|  
|metricAlwaysLoadProgramProviderLocal|Задайте ненулевое значение для указания, что поставщик программы должны всегда быть загружены локально.|  
|metricEngineCanWatchProcess|Задайте ненулевое значение, чтобы указать, что отладчик будет наблюдать за обработки событий, а не поставщиком программы.|  
|metricRemoteDebugging|Задайте ненулевое значение, чтобы указать поддержку для удаленной отладки.|  
|metricEncUseNativeBuilder|Задайте ненулевое значение для указания, изменить и продолжить Manager следует использовать модуль отладки encbuild.dll для создания изменить и продолжить. **Примечание:** пользовательского модуля отладки никогда не следует задавать, или следует всегда равно 0.|  
|metricLoadUnderWOW64|Задайте ненулевое значение, чтобы указать модуль отладки, которые должны загружаться в отлаживаемый процесс в режиме WOW, при отладке в 64-разрядном процессе; в противном случае модуль отладки будут загружены в процесс Visual Studio (который выполняется в эмуляторе WOW64).|  
|metricLoadProgramProviderUnderWOW64|Задайте ненулевое значение, чтобы указать, что поставщик программы должны быть загружены в отлаживаемом процессе, при отладке 64-разрядный процесс в режиме WOW; в противном случае оно будет загружено в процесс Visual Studio.|  
|metricStopOnExceptionCrossingManagedBoundary|Задайте ненулевое значение, чтобы указать, что процесс должна прекратиться, если необработанное исключение через границы управляемого и неуправляемого кода.|  
|metricAutoSelectPriority|Задайте приоритет для автоматического выбора модуля отладки (выше значения equals более высоким приоритетом).|  
|metricAutoSelectIncompatibleList|Раздел реестра, содержащий записи, укажите идентификаторы GUID для обработчиков отладки нужно игнорировать в автоматический выбор. Эти записи целый ряд (0, 1, 2 и т. д.) с идентификатором GUID, выраженное в виде строки.|  
|metricIncompatibleList|Раздел реестра, содержащий записи, укажите идентификаторы GUID для обработчиков отладки, которые несовместимы с этот модуль отладки.|  
|metricDisableJITOptimization|Задайте ненулевое значение, чтобы указать, что во время отладки следует отключить оптимизации just-in-time (для управляемого кода).|  
  
|Свойства вычислителя выражения|Описание|  
|-------------------------------------|-----------------|  
|metricEngine|Содержит количество отладчиков, которые поддерживают средство оценки указанного выражения.|  
|metricPreloadModules|Задайте ненулевое значение, чтобы указать, что предварительно модулей загружается при запуске вычислитель выражений от программы.|  
|metricThisObjectName|Задайте имя объекта «this».|  
  
|Свойства расширения вычислителя выражений|Описание|  
|-----------------------------------------------|-----------------|  
|metricExtensionDll|Имя библиотеки DLL, которая поддерживает это расширение.|  
|metricExtensionRegistersSupported|Список поддерживаемых регистров.|  
|metricExtensionRegistersEntryPoint|Точка входа для доступа к регистров.|  
|metricExtensionTypesSupported|Список поддерживаемых типов.|  
|metricExtensionTypesEntryPoint|Точка входа для доступа к типам.|  
  
|Свойства поставщика порта|Описание|  
|------------------------------|-----------------|  
|metricPortPickerCLSID|CLSID средство выбора порта (диалоговое окно пользователя можно использовать для выбора порты и добавьте порты, используемые для отладки).|  
|metricDisallowUserEnteredPorts|Ненулевое значение, если пользователь ввел порты нельзя добавить поставщика порта (это делает диалоговое окно выбора порта, по сути предназначены только для чтения).|  
|metricPidBase|Идентификатор базового процесса, используемые поставщика порта при выделении идентификаторов процессов.|  
  
|SP предопределенные типы Store|Описание|  
|-------------------------------|-----------------|  
|storetypeFile|Символы хранятся в отдельном файле.|  
|storetypeMetadata|Символы сохраняются как метаданные в сборке.|  
  
|Прочие свойства|Описание|  
|------------------------------|-----------------|  
|metricShowNonUserCode|Задайте ненулевое значение, чтобы показать являющемся код.|  
|metricJustMyCodeStepping|Задайте ненулевое значение, чтобы указать, что шаг с заходом могут возникать только в пользовательском коде.|  
|metricCLSID|CLSID для объекта определенного типа метрик.|  
|MetricName|Понятное имя для объекта определенного типа метрик.|  
|metricLanguage|Имя языка.|  
  
## <a name="registry-locations"></a>Разделы реестра  
 Считывается из метрик и записать в реестр, а именно в `VisualStudio` подраздел.  
  
> [!NOTE]
>  В большинстве случаев, метрики будут записаны в разделе HKEY_LOCAL_MACHINE. Тем не менее иногда HKEY_CURRENT_USER будет целевой ключ. Dbgmetric.LIB обрабатывает оба ключа. При получении метрики, он ищет HKEY_CURRENT_USER первой, а затем HKEY_LOCAL_MACHINE. При установке метрики, параметр указывает, какой ключ верхнего уровня, следует использовать.  
  
 *[раздел реестра]*\  
  
 `Software`\  
  
 `Microsoft`\  
  
 `VisualStudio`\  
  
 *[версия root]*\  
  
 *[метрик root]*\  
  
 *[типа metric]*\  
  
 *[метрика] = [значение метрики]*  
  
 *[метрика] = [значение метрики]*  
  
 *[метрика] = [значение метрики]*  
  
|Заполнитель|Описание|  
|-----------------|-----------------|  
|*[раздел реестра]*|`HKEY_CURRENT_USER` или `HKEY_LOCAL_MACHINE`.|  
|*[версия root]*|Версия Visual Studio (например, `7.0`, `7.1`, или `8.0`). Тем не менее этот корневой можно также изменить с помощью **/rootsuffix** переключиться в режим **devenv.exe**. Для VSIP, этот модификатор обычно является **Exp**, то есть корневой версии будет, например, 8.0Exp.|  
|*[метрик root]*|Это может быть либо `AD7Metrics` или `AD7Metrics(Debug)`зависимости от того, используется ли отладочная версия dbgmetric.lib. **Примечание:** ли dbgmetric.lib используется, это соглашение об именовании следует соблюдать при наличии различий между отладочной и окончательной версий, которые должны быть отражены в реестре.|  
|*[типа metric]*|Тип метрики для записи: `Engine`, `ExpressionEvaluator`, `SymbolProvider`и т. д. Все они определяются как dbgmetric.h как `metricTypeXXXX`, где `XXXX` имя определенного типа.|  
|*[метрика]*|Имя записи для быть присвоено значение, чтобы задать метрику. Фактической организации метрик зависит от типа метрик.|  
|*[значение метрики]*|Значение, присваиваемое метрики. Тип, значение должно иметь (string, number, и т.д.), зависит от метрики.|  
  
> [!NOTE]
>  Все идентификаторы GUID хранятся в формате `{GUID}`. Например, `{123D150B-FA18-461C-B218-45B3E4589F9B}`.  
  
### <a name="debug-engines"></a>Модули отладки  
 Ниже приведен организации метрик обработчиков отладки, в реестре. `Engine` Имя типа метрик для модуля отладки и соответствует *[типа metric]* в дереве реестра выше.  
  
 `Engine`\  
  
 *[guid ядра]*\  
  
 `CLSID` = *[guid класса]*  
  
 *[метрика] = [значение метрики]*  
  
 *[метрика] = [значение метрики]*  
  
 *[метрика] = [значение метрики]*  
  
 `PortSupplier`\  
  
 `0` = *[guid поставщика порта]*  
  
 `1` = *[guid поставщика порта]*  
  
|Заполнитель|Описание|  
|-----------------|-----------------|  
|*[guid ядра]*|Идентификатор GUID модуля отладки.|  
|*[guid класса]*|Идентификатор GUID класса, реализующего этот модуль отладки.|  
|*[guid поставщика порта]*|Идентификатор GUID поставщика порта, если таковые имеются. Многие модули отладки используйте поставщика порта по умолчанию и не указывайте собственные поставщика. В данном случае подраздела `PortSupplier` будет отсутствовать.|  
  
### <a name="port-suppliers"></a>Поставщики портов  
 Ниже приведен организации метрик поставщика порта в реестре. `PortSupplier` Имя типа метрик для поставщика порта и соответствует *[типа metric]*.  
  
 `PortSupplier`\  
  
 *[guid поставщика порта]*\  
  
 `CLSID` = *[guid класса]*  
  
 *[метрика] = [значение метрики]*  
  
 *[метрика] = [значение метрики]*  
  
|Заполнитель|Описание|  
|-----------------|-----------------|  
|*[guid поставщика порта]*|Идентификатор GUID поставщика порта|  
|*[guid класса]*|Идентификатор GUID класса, реализующего этот поставщика порта|  
  
### <a name="symbol-providers"></a>Поставщики символ  
 Ниже приведен организации метрик поставщика символов в реестре. `SymbolProvider` Имя метрики типа для поставщика символов и соответствует *[типа metric]*.  
  
 `SymbolProvider`\  
  
 *[guid поставщика символов]*\  
  
 `file`\  
  
 `CLSID` = *[guid класса]*  
  
 *[метрика] = [значение метрики]*  
  
 *[метрика] = [значение метрики]*  
  
 `metadata`\  
  
 `CLSID` = *[guid класса]*  
  
 *[метрика] = [значение метрики]*  
  
 *[метрика] = [значение метрики]*  
  
|Заполнитель|Описание|  
|-----------------|-----------------|  
|*[guid поставщика символов]*|GUID поставщика символов|  
|*[guid класса]*|Идентификатор GUID класса, реализующего этот поставщик символов|  
  
### <a name="expression-evaluators"></a>Вычислители выражений  
 Ниже приведен организации метрик вычислителя выражений в реестре. `ExpressionEvaluator` Имя типа метрик для оценки выражений и соответствует *[типа metric]*.  
  
> [!NOTE]
>  Тип метрики для `ExpressionEvaluator` не определен в dbgmetric.h, так как предполагается, что все изменения метрик для вычислители выражений будет проходить через функции метрик оценки соответствующее выражение (макет `ExpressionEvaluator` подраздел доступен немного сложен, поэтому подробности скрыты внутри dbgmetric.lib).  
  
 `ExpressionEvaluator`\  
  
 *[идентификатор guid языка]*\  
  
 *[guid поставщика]*\  
  
 `CLSID` = *[guid класса]*  
  
 *[метрика] = [значение метрики]*  
  
 *[метрика] = [значение метрики]*  
  
 `Engine`\  
  
 `0` = *[guid обработчика отладки]*  
  
 `1` = *[guid обработчика отладки]*  
  
|Заполнитель|Описание|  
|-----------------|-----------------|  
|*[идентификатор guid языка]*|Идентификатор GUID языка|  
|*[guid поставщика]*|Идентификатор GUID поставщика|  
|*[guid класса]*|Идентификатор GUID класса, реализующего этот вычислитель выражений|  
|*[guid обработчика отладки]*|Идентификатор GUID модуля отладки, работу этого средство оценки выражений|  
  
### <a name="expression-evaluator-extensions"></a>Расширения вычислителя выражений  
 Ниже приведен организации метрик расширения вычислителя выражений в реестре. `EEExtensions` Имя метрики типа для выражения расширения вычислителя и соответствует *[типа metric]*.  
  
 `EEExtensions`\  
  
 *[расширение guid]*\  
  
 *[метрика] = [значение метрики]*  
  
 *[метрика] = [значение метрики]*  
  
|Заполнитель|Описание|  
|-----------------|-----------------|  
|*[расширение guid]*|Идентификатор GUID расширения вычислителя выражений|  
  
### <a name="exceptions"></a>Исключения  
 Ниже приведен организации метрик исключения в реестре. `Exception` Имя метрики типа исключений и соответствует *[типа metric]*.  
  
 `Exception`\  
  
 *[guid обработчика отладки]*\  
  
 *[типы исключений]*\  
  
 *[исключение]*\  
  
 *[метрика] = [значение метрики]*  
  
 *[метрика] = [значение метрики]*  
  
 *[исключение]*\  
  
 *[метрика] = [значение метрики]*  
  
 *[метрика] = [значение метрики]*  
  
|Заполнитель|Описание|  
|-----------------|-----------------|  
|*[guid обработчика отладки]*|Идентификатор GUID модуля отладки, который поддерживает исключения.|  
|*[типы исключений]*|Общие заголовок подраздела, который определяет класс исключений, которые могут быть обработаны. Обычно имена являются **исключения C++**, **исключения Win32**, **исключения среды CLR**, и **собственного проверок во время выполнения**. Эти имена также используются для идентификации определенного класса исключения для пользователя.|  
|*[исключение]*|Имя исключения: например, **_com_error** или **секционный**. Эти имена также используются для идентификации конкретного исключения для пользователя.|  
  
## <a name="requirements"></a>Требования  
 Эти файлы расположены в [!INCLUDE[vs_dev10_ext](../../../includes/vs-dev10-ext-md.md)] каталог установки SDK (по умолчанию *[диск]* \Program Files\Microsoft Visual Studio 2010 SDK\\).  
  
 Заголовок: includes\dbgmetric.h  
  
 Библиотека: libs\ad2de.lib, libs\dbgmetric.lib  
  
## <a name="see-also"></a>См. также  
 [Справочник по интерфейсам API](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)
