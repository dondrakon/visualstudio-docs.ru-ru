---
title: "Управление ссылками в проекте"
author: asb3993
ms.author: amburns
ms.date: 04/14/2017
ms.topic: article
ms.assetid: 4AD51385-B0A8-4BA7-B2D4-BF2BD167A142
ms.translationtype: HT
ms.sourcegitcommit: e2b7ff9126e1cc38ac2e58d6be339b656a024e7f
ms.openlocfilehash: 30f6c99c6ac827b7da94fd228a7034e9ce0b0fac
ms.contentlocale: ru-ru
ms.lasthandoff: 08/11/2017

---

# <a name="managing-references-in-a-project"></a>Управление ссылками в проекте

Visual Studio для Mac предоставляет три средства для добавления дополнительных ссылок в проект:

![Ссылки проекта](media/projects-and-solutions-image10.png)

Эти особые значения приведены ниже.

* Ссылки
* Пакеты NuGet (добавляются через папку "Пакеты")
* Компоненты

Кроме того, в любой проект можно добавить веб-ссылки и собственные ссылки.

## <a name="assembly-references"></a>Ссылки на сборки

Каждая платформа в Xamarin содержит более десяти различных сборок. Не все эти пакеты сборки указываются в ссылках вашего проекта по умолчанию. 

Чтобы изменить пакеты, на которые указывают ссылки в проекте, используйте диалоговое окно _Изменить ссылки_, которое отображается при двойном щелчке папки ссылок или выборе пункта "Изменить ссылки" в ее контекстном меню:

![Диалоговое окно "Ссылки на сборки"](media/projects-and-solutions-image11.png)

Сведения о сборках, доступных для каждой платформы Xamarin, см. в руководстве [Доступные сборки](https://developer.xamarin.com/guides/cross-platform/advanced/available-assemblies/).

## <a name="nuget"></a>NuGet

NuGet — это наиболее популярный диспетчер пакетов для разработки .NET. Поддержка NuGet в Visual Studio для Mac позволяет искать пакеты, которые требуется добавить в проект.

Для этого щелкните папку **Пакет** на панели решения правой кнопкой мыши и выберите пункт "Добавить пакеты".

Сведения об использовании пакета NuGet см. в пошаговом руководстве [Включение пакета NuGet в проект](~/nuget-walkthrough.md).
