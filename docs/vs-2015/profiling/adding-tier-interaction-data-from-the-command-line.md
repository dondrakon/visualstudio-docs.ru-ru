---
title: Добавление данных взаимодействия уровней из командной строки | Документы Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- tier interaction profiling method
- profiling tools,tier interaction method
ms.assetid: 5a35647f-03f2-4555-8eeb-fda7e0080e67
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ce7713b39acb7736e34f6ab6017b0cd32b1e1cfa
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/05/2018
ms.locfileid: "47593057"
---
# <a name="adding-tier-interaction-data-from-the-command-line"></a>Добавление данных взаимодействия уровней из командной строки
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [Добавление данных взаимодействия уровней из командной строки](https://docs.microsoft.com/visualstudio/profiling/adding-tier-interaction-data-from-the-command-line).  
  
Профилирование уровневого взаимодействия позволяет получить дополнительные сведения о времени выполнения синхронных вызовов [!INCLUDE[vstecado](../includes/vstecado-md.md)] в функциях многоуровневых приложений, взаимодействующих с одной или несколькими базами данных.  
  
 **Windows 8 или Windows Server 2012**  
  
 Чтобы собрать данные об уровневом взаимодействии на классических приложениях Windows 8 и приложениях Windows Server 2012, необходимо использовать метод инструментирования. Сбор данных об уровневом взаимодействии в приложениях для Магазина Windows не поддерживается.  
  
 **Выпуски Visual Studio**  
  
 Профилирование уровневого взаимодействия можно собирать с помощью [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)] или [!INCLUDE[vs_pro_current_short](../includes/vs-pro-current-short-md.md)]. Однако данные профилирования уровневого взаимодействия можно просматривать только в [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)] и [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)].  
  
 **Сбор данных об уровневом взаимодействии на удаленном компьютере**  
  
 Чтобы собрать данные об уровневом взаимодействии на удаленном компьютере, необходимо скопировать **vs\_профилировщика\_**_\<платформы >_ **\_**  _\<Языка >_**.exe** файла из _% VSInstallDir %_**\Team Tools\Performance Tools\Setups**папку Visual Studio компьютера на удаленный компьютер и установить его. Нельзя использовать средства профилирования в [инструменты удаленной отладки для Visual Studio](http://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c) загрузить пакет.  
  
 **Отчеты TIP**  
  
 Данные об уровневом взаимодействии можно просматривать только в интегрированной среде разработки [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)]. Получение отчетов об уровневом взаимодействии (TIP) на основе файлов с помощью [VSPerfReport](../profiling/vsperfreport.md) недоступно.  
  
## <a name="adding-tier-interaction-data-with-vsperfcmd"></a>Добавление данных об уровневом взаимодействии с помощью VSPerfCmd  
 Программа командной строки VSPerfASPNETCmd позволяет получить доступ к полному набору функций, доступных в средствах профилирования. Чтобы добавить сведения об уровневом взаимодействии в данные профилирования, собранные с помощью VSPerfCmd, необходимо использовать программу **VSPerfCLREnv** для установки и удаления переменных среды, которые обеспечивают сбор данных о взаимодействии. Указываемые параметры и процедуры, необходимые для сбора данных, зависят от типа профилируемого приложения.  
  
### <a name="profiling-stand-alone-applications"></a>Профилирование автономных приложений  
 Чтобы добавить данные об уровневом взаимодействии в приложение, которое выполняется другим процессом (например, в классическое приложение Windows, осуществляющее синхронные вызовы [!INCLUDE[vstecado](../includes/vstecado-md.md)] к базе данных SQLServer), используйте параметр **VSPerfClrEnv /InteractionOn**, чтобы задать переменные среды, и параметр **VSPerfClrEnv /InteractionOff** для их удаления.  
  
 В следующем примере выполняется профилирование классического приложения Windows с помощью метода инструментирования и сбор данных об уровневом взаимодействии.  
  
##### <a name="profiling-a-windows-desktop-application-example"></a>Пример профилирования классического приложения Windows  
  
1.  Откройте окно командной строки как администратор. В меню **Пуск** наведите указатель мыши на пункт **Все программы**, выберите пункт **Стандартные**. Щелкните правой кнопкой мыши пункт **Командная строка** и выберите команду **Запуск от имени администратора**.  
  
2.  Инициализируйте профилирование .NET и переменные среды TIP. Введите следующие команды:  
  
    ```  
    vsperfclrenv /traceon  
    vsperfclrenv /interactionon  
    ```  
  
3.  Запуск профилировщика. Введите следующую команду:  
  
    ```  
    vsperfcmd /start:trace /output:Desktop_tip.vsp   
    ```  
  
4.  Запустите приложение с помощью программы VSPerfCmd. Введите следующую команду:  
  
    ```  
    vsperfcmd /launch:DesktopApp.exe  
    ```  
  
5.  Запустите приложение для сбора данных профилирования, а затем закройте приложение обычным способом.  
  
6.  Сбросьте переменные среды TIP. Введите следующую команду:  
  
    ```  
    vsperfclrenv /off  
    ```  
  
 Дополнительные сведения см. в разделе [Профилирование автономных приложений](../profiling/command-line-profiling-of-stand-alone-applications.md).  
  
### <a name="profiling-services"></a>Профилирование служб  
 Для профилирования служб, включая приложения [!INCLUDE[vstecasp](../includes/vstecasp-md.md)], используйте параметр **VSPerfClrEnv /GlobalInteractionOn**, чтобы задать переменные среды, и параметр **VSPerfClrEnv /GlobalInteractionOff** для их удаления.  
  
 При профилировании служб, включая веб-приложения [!INCLUDE[vstecasp](../includes/vstecasp-md.md)], вам потребуется часто перезагружать компьютер, чтобы включить профилирование.  
  
 В следующем примере выполняется профилирование службы Windows с помощью метода инструментирования и сбор данных об уровневом взаимодействии.  
  
##### <a name="profiling-a-windows-service-example"></a>Пример профилирования службы Windows  
  
1.  При необходимости установите службу.  
  
2.  Откройте окно командной строки как администратор. В меню **Пуск** наведите указатель мыши на пункт **Все программы**, выберите пункт **Стандартные**. Щелкните правой кнопкой мыши пункт **Командная строка** и выберите команду **Запуск от имени администратора**.  
  
3.  Инициализируйте переменные среды профилирования .NET. Введите следующую команду:  
  
    ```  
    vsperfclrenv /globaltraceon  
    ```  
  
4.  Инициализируйте переменные среды TIP. Введите следующую команду:  
  
    ```  
    vsperfclrenv /globalinteractionon  
    ```  
  
5.  Перезагрузите компьютер, чтобы зарегистрировать переменные среды.  
  
6.  Откройте окно командной строки как администратор.  
  
7.  Запуск профилировщика. Введите следующую команду:  
  
    ```  
    vsperfcmd /start:trace /output:MiddleTier_tip.vsp /user:SYSTEM /crosssession   
    ```  
  
8.  При необходимости запустите службу.  
  
9. Подключите профилировщик к службе. Введите следующую команду:  
  
    ```  
    vsperfcmd /attach:MiddleTier.exe /output:MyService_tip.vsp /user:SYSTEM /crosssession   
    ```  
  
10. Запустите службу и сбор данных профилирования.  
  
11. Остановите профилировщик. Введите следующую команду:  
  
     `vsperfcmd /detach`  
  
12. Сбросьте переменные среды профилирования .NET и TIP. Введите следующую команду:  
  
    ```  
    vsperfclrenv /globaloff  
    ```  
  
13. Перезагрузите компьютер, чтобы зарегистрировать сброшенные переменные среды.  
  
 Дополнительные сведения см. в одном из следующих разделов.  
  
 [Профилирование веб-приложений ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)  
  
 [Профилирование служб](../profiling/command-line-profiling-of-services.md)  
  
## <a name="adding-tier-interaction-data-with-vsperfaspnetcmd"></a>Добавление данных об уровневом взаимодействии с помощью VSPerfASPNETCmd  
 Программа командной строки VSPerfASPNETCmd позволяет без труда профилировать веб-приложения [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]. У этой программы меньше параметров по сравнению с программой командной строки **VSPerfCmd**, в ней не нужно задавать переменные среды и не требуется перезагрузка компьютера. Эти возможности VSPerfASPNETCmd делают сбор данных об уровневом взаимодействии чрезвычайно простым.  
  
 Чтобы добавить сведения об уровневом взаимодействии в данные профилирования, собранные с помощью VSPerfASPNETCmd, добавьте в командную строку параметр **/TIP**. Например, используйте следующую командную строку для сбора данных об уровневом взаимодействии для веб-приложения [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] с помощью метода инструментирования:  
  
```  
vsperfaspnetcmd /tip /trace http://localhost/MyWebApp  
```  
  
 Дополнительные сведения о программе VSPerfASPNETCmd см. в статье [Rapid Web Site Profiling with VSPerfASPNETCmd](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md) (Быстрое профилирование веб-сайтов с помощью средства VSPerfASPNETCmd).


