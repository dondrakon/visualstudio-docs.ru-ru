---
title: Практическое руководство. Отображение вкладки "Разработчик" на ленте
ms.date: 08/14/2019
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Ribbon [Office development in Visual Studio], tabs
- Developer tab [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 7b6641cca4ef2288452b2f6959482b311a5b07a4
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/16/2019
ms.locfileid: "69551787"
---
# <a name="how-to-show-the-developer-tab-on-the-ribbon"></a>Практическое руководство. Отображение вкладки "Разработчик" на ленте
  Для доступа к вкладке **разработчик** на ленте приложения Office необходимо настроить для него отображение вкладки, так как она не отображается по умолчанию. Например, необходимо отобразить эту вкладку, если требуется добавить <xref:Microsoft.Office.Tools.Word.GroupContentControl> в настройку уровня документа для Word.

> [!NOTE]
> Это руководство применимо только к приложениям Office 2010 или более поздней версии. Если вы хотите отобразить эту вкладку в системе 2007 Microsoft Office, см. следующую версию этого раздела [: Отображение вкладки "Разработчик" на ленте](https://web.archive.org/web/20140303033431/msdn.microsoft.com/library/bb608625(v=vs.90).aspx
).

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

> [!NOTE]
> У Access нет вкладки **разработчика** .

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="to-show-the-developer-tab"></a>Отображение вкладки "Разработчик"

1. Запустите любое приложение Office, указанное в этом разделе. См. раздел **применение к:** Примечание ранее в этом разделе.

2. На вкладке **файл** нажмите кнопку **Параметры** .

     На следующем рисунке показана кнопка на вкладке **файла** и **параметры** в Office 2010.

     ![Выбор файла, параметров в Outlook 2010](../vsto/media/vsto-office-file-tab.png "Выбор файла, параметров в Outlook 2010")

     На следующем рисунке показана вкладка **файл** в Office 2013.

     ![Вкладка "файл" в Outlook 2013](../vsto/media/vsto-office2013-filetab.png "Вкладка \"файл\" в Outlook 2013")

     На следующем рисунке показана кнопка **Параметры** в Office 2013.

     ![Кнопка "Параметры" в предварительной версии Outlook 2013](../vsto/media/vsto-office2013-optionsbutton.png "Кнопка \"Параметры\" в предварительной версии Outlook 2013")

3. В диалоговом окне**Параметры** _applicationName_нажмите кнопку **Настройка ленты** .

     На следующем рисунке показано диалоговое окно **Параметры** и кнопка **Настройка ленты** в Excel 2010. Расположение этой кнопки аналогично и во всех остальных приложениях, перечисленных в приведенном выше подразделе "Применимо к".

     ![Кнопка настройки ленты](../vsto/media/vsto-office2010-customizeribbonbutton.png "Кнопка настройки ленты")

4. В списке основных вкладок установите флажок **разработчик** .

     На следующем рисунке показан флажок **разработчик** в Word 2010 и [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)]. Расположение этого флажка аналогично и во всех остальных приложениях, перечисленных в приведенном выше подразделе "Применимо к".

     ![Флажок "Разработчик" в диалоговом окне "Параметры Word"](../vsto/media/vsto-office2010-developercheckbox.png "Флажок \"Разработчик\" в диалоговом окне \"Параметры Word\"")

5. Нажмите кнопку **ОК** , чтобы закрыть диалоговое окно **Параметры** .

## <a name="see-also"></a>См. также
- [Настройка пользовательского интерфейса Office](../vsto/office-ui-customization.md)
