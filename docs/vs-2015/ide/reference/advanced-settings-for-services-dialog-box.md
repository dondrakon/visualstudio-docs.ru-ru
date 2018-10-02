---
title: Диалоговое окно "Дополнительные параметры служб" | Документы Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vb.ProjectPropertiesAdvancedServices
helpviewer_keywords:
- Advanced Settings for Services dialog box
ms.assetid: 6dde4a2d-85e1-4275-aa55-24b84111be91
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: ea79a5539ad41a4f6e56a6069889e06bc45dde65
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47560158"
---
# <a name="advanced-settings-for-services-dialog-box"></a>Диалоговое окно "Дополнительные параметры служб"
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [Дополнительные параметры для диалогового окна служб](https://docs.microsoft.com/visualstudio/ide/reference/advanced-settings-for-services-dialog-box).  
  
  
Службы клиентских приложений предоставляют упрощенный доступ к службам входа, ролей и профилей [!INCLUDE[ajax_current_short](../../includes/ajax-current-short-md.md)] из приложений Windows Forms и Windows Presentation Foundation (WPF). Вы можете использовать страницу **Службы** **конструктора проектов**, чтобы настраивать службы клиентских приложений. Дополнительные сведения о странице **Службы** см. в разделе [Страница "Службы" в конструкторе проектов](../../ide/reference/services-page-project-designer.md).  
  
 Используйте диалоговое окно **Дополнительные параметры служб** на странице **Службы** **конструктора проектов** для расширенной настройки служб клиентских приложений. С помощью этих параметров можно переопределить некоторое поведение служб приложений по умолчанию, чтобы реализовать менее типичные сценарии. Дополнительные сведения см. в разделе [Службы клиентских приложений](http://msdn.microsoft.com/library/1487d8df-089e-4f21-abfb-a791a652b58e).  
  
 Чтобы открыть диалоговое окно **Дополнительные параметры служб**, выберите узел проекта в **обозревателе решений** и затем в меню **Проект** щелкните команду **Свойства**. Когда откроется окно **Конструктор проектов**, перейдите на вкладку **Службы** и нажмите кнопку **Дополнительно**. Эта кнопка остается недоступной, пока вы не включите службы клиентских приложений.  
  
## <a name="task-list"></a>список задач  
 [Практическое руководство. Настройка служб клиентских приложений](http://msdn.microsoft.com/library/34a8688a-a32c-40d3-94be-c8e610c6a4e8)  
  
 [Практическое руководство. Автономная работа со службами клиентских приложений](http://msdn.microsoft.com/en-us/f792cb16-8520-4a0f-9dc9-07bfbc454e38)  
  
## <a name="uielement-list"></a>Список элементов пользовательского интерфейса  
 **Локально сохранять хэш пароля для обеспечения входа вне сети**  
 Указывает, будет ли зашифрованный пароль пользователя кэшироваться локально, чтобы пользователь мог войти в систему из автономного режима. Дополнительные сведения см. в разделе [Практическое руководство. Работа со службами клиентских приложений в автономном режиме](http://msdn.microsoft.com/en-us/f792cb16-8520-4a0f-9dc9-07bfbc454e38). Этот параметр установлен по умолчанию.  
  
 **Требовать, чтобы пользователи повторяли вход, если у файла cookie сервера истек срок действия**  
 Указывает, проходят ли проверенные ранее пользователи повторную проверку подлинности автоматически, если приложение обращается к ролям или службе профиля, когда истек срок действия файла cookie для проверки подлинности сервера. Выберите этот параметр, чтобы запретить доступ к службам приложений и требовать явную повторную проверку подлинности после истечения срока действия файла cookie. Этот параметр полезен при развертывании приложений в общедоступных системах, чтобы пользователи, которые прекратили пользоваться приложением, не входили в систему автоматически. По умолчанию этот флажок снят.  
  
 **Тайм-аут кэша службы ролей**  
 Указывает период, когда поставщик клиентских ролей будет использовать кэшированные значения ролей вместо обращения к службе ролей. Установите небольшой срок действия для часто обновляемых ролей и более длительный срок для редко обновляемых ролей. Значение по умолчанию — один день.  
  
 Поставщик ролей получает кэшированные значения ролей или службы ролей при вызове метода <xref:System.Web.Security.RolePrincipal.IsInRole%2A>. Для программного сброса кэша и принудительного доступа метода к удаленной службе требуется вызвать метод <xref:System.Web.ClientServices.Providers.ClientRoleProvider.ResetCache%2A>.  
  
 **Использовать настраиваемую строку подключения**  
 Указывает, используют ли поставщики клиентских служб настраиваемое хранилище данных для локального кэша. По умолчанию поставщики используют для кэша локальную файловую систему. При выборе этого параметра автоматически заполняется текстовое поле со строкой подключения по умолчанию. Можно сохранить строку подключения по умолчанию для автоматического создания и использования базы данных SQL Server Compact Edition, либо указать строку подключения для существующей базы данных SQL Server. Дополнительные сведения см. в разделе [Практическое руководство. Настройка служб клиентских приложений](http://msdn.microsoft.com/library/34a8688a-a32c-40d3-94be-c8e610c6a4e8). По умолчанию этот флажок снят.  
  
## <a name="see-also"></a>См. также  
 [Службы клиентских приложений](http://msdn.microsoft.com/library/1487d8df-089e-4f21-abfb-a791a652b58e)   
 [Страница "Службы" в конструкторе проектов](../../ide/reference/services-page-project-designer.md)   
 [Практическое руководство. Настройка служб клиентских приложений](http://msdn.microsoft.com/library/34a8688a-a32c-40d3-94be-c8e610c6a4e8)   
 [Практическое руководство. Автономная работа со службами клиентских приложений](http://msdn.microsoft.com/en-us/f792cb16-8520-4a0f-9dc9-07bfbc454e38)


