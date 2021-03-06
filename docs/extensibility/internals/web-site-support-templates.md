---
title: Шаблоны поддержки веб-сайта Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- we site projects, templates
ms.assetid: 37173c97-486b-4b3c-8ed3-cf5890c4de23
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0e3c139ae6f2f9ec618e6382a1551a9e35eee7ec
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703452"
---
# <a name="web-site-support-templates"></a>Шаблоны поддержки веб-сайтов
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Шаблоны проектов веб-узлов и элементов предоставляют многоразовые и настраиваемые проекты веб-узла и заглушки элементов, которые ускоряют процесс разработки, устраняя необходимость создания новых проектов веб-узлов и элементов с нуля. Для получения [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] дополнительной информации о шаблонах см. [Creating Project and Item Templates](../../ide/creating-project-and-item-templates.md)

## <a name="project-template-folder"></a>Шаблон проекта Фолдер
 Шаблоны веб-проектов, как правило, устанавливаются на*пути установки визуальной студии (Визуальная студия Установка Путь)*( «Common7»IDE»ProjectTemplates-Web\\, каждый из которых находится в подфолдере, названном в честь языка веб-программирования.

## <a name="project-file"></a>Файл проекта
 Интегрированная [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] среда разработки (IDE) требует расширения файла проекта в качестве способа отображения шаблона к правильному типу проекта. Поскольку веб-проекты не имеют файла проекта, фиктивное расширение файла проекта .webproj зарегистрировано для отображения шаблона к типу проекта.

 В качестве опционов в шаблон можно добавить строку с именами языков, чтобы система веб-проектов могла установить значение по умолчанию в диалоговом окне **Добавления нового элемента** для элементов, основанных на шаблоне. Строка должна быть первой строкой файла. Он должен соответствовать как имени, зарегистрированного в addItemLanguageName в регистрации движка IntelliSense, так и названию, зарегистрированного в project Subtype (VsTemplate). Для получения дополнительной информации смотрите [атрибуты поддержки веб-узла](../../extensibility/internals/web-site-support-attributes.md).

 Если строка не присутствует, система веб-проектов пытается определить язык по умолчанию на основе атрибута языка и расширения файлов страниц, добавленных в веб-проект шаблоном проекта.

## <a name="project-templates"></a>Шаблоны проектов
 Шаблоны проектов веб-узелей используются для создания новых веб-узлов в ответ на новую команду **website** в меню **файла.** В настоящее время поддерживаются три типа проектов веб-узла:

- Пустые проекты веб-узла

- Проекты веб-сайта

- Проекты веб-сервисов

### <a name="empty-web-site-projects"></a>Пустые проекты веб-сайта
 Эти файлы создают новый пустой веб-узел в ответ на команду **Пустой веб-узел,** который доступен после выбора **файла** > **Новый веб-сайт:**

- EmptyWeb.vstemplate

     Файл шаблонов, который направляет создание нового пустого веб-узла.

- EmptyWeb.webproj

     Этот файл является артефактом системы шаблонов проекта. Он удовлетворяет ссылку на файл проекта в файле EmptyWeb.vstemplate.

### <a name="web-site-projects"></a>Проекты веб-сайта
 Эти файлы создают новый веб-узел в ответ на ASP.NET команду **website,** которая доступна после выбора **файла** > **Новый веб-сайт:**

- Default.aspx

     Главная страница по умолчанию для нового веб-узла. Атрибут Языка определяет язык codebehind, а атрибут CodeFile определяет зависимый файл, содержащий код, связанный с этой страницей.

- Default.aspx. *расширение*

     Зависимый файл, содержащий код за кодом для главной страницы по умолчанию. Язык кода определяет *расширение* этого файла.

- web.config.

     Файл конфигурации root web.site.

- WebApplication.vstemplate

     Файл шаблона, определяющий содержимое решения веб-узла и закавышающий создание App_Data папки.

- WebApplication.webproj

     Этот файл является артефактом системы шаблонов проекта. Он удовлетворяет ссылку на файл проекта в файле WebApplication.vstemplate.

### <a name="web-service-projects"></a>Проекты веб-сервиса
 Эти файлы создают новый веб-узел в ответ на ASP.NET команду **Web Service,** которая доступна после выбора **файла** > **Новый веб-сайт:**

- Service.asmx

     Страница HTML для нового веб-сервиса. Атрибут Языка определяет язык codebehind, а атрибут CodeBehind определяет зависимый файл, содержащий код, связанный с этой службой.

- Service. *Расширение*

     Зависимый файл, реализуемый классом обслуживания. Язык кода определяет *расширение* этого файла.

- web.config.

- Файл конфигурации root web.site.

- WebService.vstemplate

     Файл шаблона, определяющий содержание решения веб-узла и закавышающие создание App_Data и App_Code папок. Служба. *файл расширения* скопирован в папку App_Code.

- WebService.webproj

     Этот файл является артефактом системы шаблонов проекта. Он удовлетворяет ссылку на файл проекта в файле WebService.vstemplate.

## <a name="project-item-template-folder"></a>Шаблон элемента проекта Folder
 Веб-шаблоны проекта-элемента, как правило, устанавливаются в *"Visual Studio Установка*\\Путь " Common7-IDE-ItemTemplates-Web , каждый в подфолдер, который назван в честь его языка веб-программирования.

## <a name="project-item-templates"></a>Шаблоны элементов проекта
 Шаблоны элементов проекта веб-узел используются для добавления новых веб-страниц на веб-узел в ответ на команду **Add Existing Item.** Эти виды веб-страниц в настоящее время поддерживаются:

- Новый класс

- Новая страница HTML

- Новая веб-форма

- Новая главная страница

### <a name="new-class"></a>Новый класс
 Этот шаблон создает новый исходный файл, который определяет пустой класс в ответ на команду **Add New Class.**

- Класс. *Расширение*

     Файл исходного кода, реализуемый в пустом классе. Язык кода определяет *расширение* этого файла.

- Class.vstemplate

     Файл шаблона, который создает исходный файл и определяет его содержимое.

### <a name="new-html-page"></a>Новая страница HTML
 Этот шаблон создает новую веб-страницу в ответ на команду **Добавить новую HTML Страницу.**

- HTMLPage.htm

     Начальное содержимое веб-страницы. Эта веб-страница обычно не имеет связанного файла, зависящих от кода. Чтобы создать смарт-страницу со связанным файлом codebehind, вместо этого используйте шаблон web Form.

- HTMLPage.vstemplate

     Файл шаблона, который создает веб-страницу и определяет ее содержимое.

### <a name="new-webform"></a>Новая веб-форма
 Этот шаблон создает новую интеллектуальную веб-страницу в ответ на команду **Добавить новую веб-форму.**

 Чтобы создать зависимый кодзаовый исходный файл, выберите **код Place в отдельном файле.** В противном случае создается одна веб-страница с \<пустым блоком скриптов и ненастывающим на % > директивами для подключения зависимого файла.

 Чтобы создать страницу содержимого для выбранной главной страницы, выберите **главную страницу.**

- WebForm.aspx

     Начальное содержимое веб-страницы. Эта веб-страница не имеет связанного кода за зависимым файлом.

- WebForm_cb.aspx

     Начальное содержимое веб-страницы. Эта веб-страница имеет связанный код-зависимый файл.

- Codebehind. *Расширение*

     Зависимый файл, реализуемый классом веб-формы. Язык кода определяет *расширение* этого файла.

- ContentPage.aspx

     Начальное содержимое веб-страницы в виде страницы содержимого. Эта веб-страница не имеет связанного кода за зависимым файлом.

- ContentPage_cb.aspx

     Начальное содержимое веб-страницы в виде страницы содержимого. Эта веб-страница имеет связанный код-зависимый файл.

- WebForm.vstemplate

     Файл шаблона, определяющий содержимое новой веб-страницы и ее зависимого файла, если таковой имеется.

### <a name="new-master-page"></a>Новая страница мастера
 Этот шаблон создает новую главную страницу в ответ на команду **Добавить новую** страницу Master Page.

 Чтобы создать зависимый кодзаовый исходный файл, выберите **код Place в отдельном файле.** В противном случае создается одна веб-страница \<с пустым блоком скриптов и не нанизаны на страницу %> директивы для подключения зависимого файла.

- MasterPage.master

     Начальное содержимое главной страницы. Эта главная страница не имеет связанного кода за зависимым файлом.

- MasterPage_cb.мастер

     Начальное содержимое главной страницы. Эта главная страница имеет связанный код-зависимый файл.

- Codebehind. *расширение*

     Зависимый файл, реализуемый на мастер-странице. Язык кода определяет *расширение* этого файла.

- MasterPage.vstemplate

     Файл шаблона, определяющий содержимое новой основной страницы и ее зависимого файла, если таковой имеется.

## <a name="see-also"></a>См. также
- [Поддержка веб-сайтов](../../extensibility/internals/web-site-support.md)
