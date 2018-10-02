---
title: Практическое руководство. Инструментирование автономного компонента .NET Framework и сбор сведений о времени с помощью профилировщика из командной строки | Документы Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b7dcc27b-45c6-4302-9552-6fa5b1e94b56
caps.latest.revision: 33
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9d9c7083b46b6f59d28c56724722b2ea591e971b
ms.sourcegitcommit: d705e015cb525bfa87a0b93e93376c3956ec2707
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/29/2018
ms.locfileid: "47592588"
---
# <a name="how-to-instrument-a-stand-alone-net-framework-component-and-collect-timing-data-with-the-profiler-from-the-command-line"></a>Практическое руководство. Инструментирование автономного компонента .NET Framework и сбор данных о времени с помощью профилировщика из командной строки
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [как: инструментирование автономного компонента .NET Framework и сбор данных о времени с Profiler из командной строки](https://docs.microsoft.com/visualstudio/profiling/how-to-instrument-a-stand-alone-dotnet-framework-component-and-collect-timing-data-with-the-profiler-from-the-command-line).  
  
В этой статье описывается использование программ командной строки для средств профилирования [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] с целью инструментирования таких компонентов .NET Framework, как EXE- или DLL-файлы, а также для сбора подробных сведений о времени.  
  
> [!NOTE]
>  Возможности расширенной безопасности в Windows 8 и Windows Server 2012 требовали значительных изменений в способе, которым профилировщик Visual Studio собирает данные на этих платформах. Приложениям для магазина Windows также требуются новые методы сбора. См. раздел [Средства производительности в приложениях Windows 8 и Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).  
>   
>  Программы командной строки средств профилирования расположены в подкаталоге \Team Tools\Performance Tools каталога установки [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)]. На 64-разрядных компьютерах доступны 64- и 32-разрядные версии этих программ. Для использования программ командной строки профилировщика необходимо добавить путь к программам в переменную среды PATH окна командной строки или в саму команду. Дополнительные сведения см. в статье [Указание пути к средствам командной строки](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md).  
>   
>  Добавление данных об уровневом взаимодействии в сеанс профилирования требует определенных процедур со средствами профилирования командной строки. См. раздел [Сбор данных взаимодействия уровней](../profiling/adding-tier-interaction-data-from-the-command-line.md).  
  
 Для сбора подробных сведений о времени из компонента .NET Framework с помощью метода инструментирования используйте программу [VSInstr.exe](../profiling/vsinstr.md) для создания инструментированной версии компонента и программу [VSPerfCLREnv.cmd](../profiling/vsperfclrenv.md) для инициализации переменных среды профилирования. Затем запустите профилировщик.  
  
 При выполнении инструментированного компонента данные по времени автоматически сохраняются в файл данных. Вы можете приостановить и возобновить сбор данных в ходе сеанса профилирования.  
  
 Чтобы завершить сеанс профилирования, закройте целевое приложение и явным образом завершите работу профилировщика. В большинстве случаев рекомендуется сбрасывать переменные среды профилирования в конце сеанса.  
  
## <a name="starting-the-profiling-session"></a>Запуск сеанса профилирования  
  
#### <a name="to-start-profiling-by-using-the-instrumentation-method"></a>Запуск профилирования методом инструментирования  
  
1.  Откройте окно командной строки. Если необходимо, добавьте каталог средств профилировщика в переменную среды PATH. Во время установки этот путь не добавляется.  
  
2.  Используйте программу **VSInstr** для создания инструментированной версии целевого приложения.  
  
3.  Инициализируйте переменные среды профилирования .NET Framework. Тип:  
  
     **VSPerfClrEnv /traceon**  
  
4.  Запуск профилировщика. Тип:  
  
     **VSPerfCmd /start:trace /output:** `OutputFile` [`Options`]  
  
    -   Параметр [/start](../profiling/start.md)**:trace** инициализирует профилировщик.  
  
    -   Параметр [/output](../profiling/output.md)**:**`OutputFile` является обязательным для параметра **/start**. `OutputFile` указывает имя и расположение файла данных профилирования (VSP-файла).  
  
     С параметром **/start:trace** можно использовать любой из следующих параметров.  
  
    |Параметр|Описание|  
    |------------|-----------------|  
    |[/user](../profiling/user-vsperfcmd.md) **:**[`Domain`**\\**]`UserName`|Указывает домен и имя пользователя учетной записи, которая является владельцем профилируемого процесса. Этот параметр является обязательным только в том случае, если процесс выполняется в качестве пользователя, отличного от пользователя, вошедшего в систему. Владелец процесса указан в столбце "Имя пользователя" на вкладке "Процессы" диспетчера задач Windows.|  
    |[/crossession](../profiling/crosssession.md)|Включает профилирование процессов в других сеансах. Этот параметр является обязательным, если приложение ASP.NET выполняется в другом сеансе. Идентификатор сеанса указан в столбце "Идентификатор сеанса" на вкладке "Процессы" диспетчера задач Windows. **/CS** можно указать как краткую версию **/crosssession**.|  
    |[/globaloff](../profiling/globalon-and-globaloff.md)|Запускает профилировщик в состоянии приостановки сбора данных. Используйте параметр [/globalon](../profiling/globalon-and-globaloff.md) для возобновления профилирования.|  
    |[/counter](../profiling/counter.md) **:** `Config`|Собирает данные от счетчика производительности процессора, указанного в `Config`. Сведения о счетчике добавляются в данные, собранные для каждого события профилирования.|  
    |[/wincounter](../profiling/wincounter.md) **:** `WinCounterPath`|Задает счетчик производительности Windows, данные которого будут собираться во время профилирования.|  
    |[/automark](../profiling/automark.md) **:** `Interval`|Используется с только с параметром **/wincounter**. Указывает время (в миллисекундах) между событиями сбора счетчика производительности Windows. Значение по умолчанию — 500 мс.|  
    |[/events](../profiling/events-vsperfcmd.md) **:** `Config`|Задает события трассировки событий для Windows (ETW), собираемые во время профилирования. События трассировки событий Windows собираются в отдельный ETL-файл.|  
  
5.  Запустите целевое приложение из окна командной строки.  
  
## <a name="controlling-data-collection"></a>Управление сбором данных  
 Пока целевое приложение выполняется, вы можете управлять сбором данных путем запуска и остановки записи данных в файл данных профилировщика, используя параметры **VSPerfCmd.exe**. Управление сбором данных позволяет собирать данные на конкретных этапах выполнения программы, например при запуске или завершении работы приложения.  
  
#### <a name="to-start-and-stop-data-collection"></a>Запуск и остановка сбора данных  
  
-   Следующие пары параметров запускают и останавливают сбор данных. Каждый параметр необходимо указывать в отдельной командной строке. Сбор данных можно включать и отключать несколько раз.  
  
    |Параметр|Описание|  
    |------------|-----------------|  
    |[/globalon /globaloff](../profiling/globalon-and-globaloff.md)|Запускает (**/globalon**) или останавливает (**/globaloff**) сбор данных для всех процессов.|  
    |[/processon](../profiling/processon-and-processoff.md) **:** `PID` [/processoff](../profiling/processon-and-processoff.md) **:** `PID`|Запускает (**/processon**) или останавливает (**/processoff**) сбор данных для процесса с указанным идентификатором процесса (`PID`).|  
    |[/threadon](../profiling/threadon-and-threadoff.md) **:** `TID` [/threadoff](../profiling/threadon-and-threadoff.md) **:** `TID`|Запускает (**/threadon**) или останавливает (**/threadoff**) сбор данных для потока с указанным идентификатором потока (`TID`).|  
  
## <a name="ending-the-profiling-session"></a>Завершение сеанса профилирования  
 Чтобы завершить сеанс профилирования, закройте приложение, в котором выполняется инструментируемый компонент. Вызовите команду **VSPerfCmd** [/shutdown](../profiling/shutdown.md), чтобы завершить работу профилировщика и закрыть файл данных профилирования. Команда **VSPerfClrEnv /off** сбрасывает переменные среды профилирования.  
  
#### <a name="to-end-a-profiling-session"></a>Завершение сеанса профилирования  
  
1.  Закройте целевое приложение.  
  
2.  Завершите работу профилировщика. Тип:  
  
     **VSPerfCmd /shutdown**  
  
3.  (Необязательно) Сбросьте переменные среды профилирования. Тип:  
  
     **VSPerfClrEnv /off**  
  
## <a name="see-also"></a>См. также  
 [Профилирование автономных приложений](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Представление данных метода инструментирования](../profiling/instrumentation-method-data-views.md)


