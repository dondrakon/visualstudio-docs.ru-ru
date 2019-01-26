---
title: Использование указателя окна справки
ms.date: 11/02/2017
ms.prod: visual-studio-dev15
ms.topic: conceptual
helpviewer_keywords:
- Index tab [Help Viewer]
- Help Viewer, using the index
- Help Viewer, Index tab
- using the index [Help Viewer]
- index filtering [Help Viewer]
- Help Viewer, index filtering
ms.assetid: cb071e93-f297-459c-a6fa-8ae0dabc42a4
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f94b99fecdee598141504128dd47b7189afe5a4e
ms.sourcegitcommit: 75e02ed88a1ace6e8265fd4e3a82a1bc78f3adca
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/13/2018
ms.locfileid: "54406272"
---
# <a name="find-topics-by-using-the-help-viewer-index"></a>Поиск разделов с помощью указателя окна справки

Указатель содержит список ключевых слов, связанных с разделами в установленном содержимом. С каждым разделом могут быть связаны несколько ключевых слов, и каждое ключевое слово может быть связано с несколькими разделами. Используйте этот указатель таким же способом, как используете указатель в книге.

## <a name="to-find-a-topic-by-using-the-index"></a>Поиск раздела с помощью указателя

На вкладке **Указатель** выполните любую из указанных далее задач.

-   Укажите ключевое слово для поиска в текстовом поле. Например, укажите "обновление", чтобы найти разделы с ключевыми словами "обновление", "обновленный " и "обновляется".

    С помощью кнопки фильтра в верхней части вкладки можно отображать либо все записи, содержащие указанный текст, либо только те записи, которые начинаются с указанного текста.

    > [!NOTE]
    > Когда кнопка фильтра отображается на более темном фоне с границей, записи должны _содержать_ указанный текст. Если фон и граница не отображаются, записи должны _начинаться с_ указанного текста.

-   Прокрутите указатель и выберите ключевое слово.

    Если указанное ключевое слово связано только с одним разделом, отображается этот раздел. В противном случае отображается список всех разделов, связанных с этим ключевым словом.

## <a name="index-search-tips"></a>Советы по поиску в указателе

Использовать указатель просто. Однако если вы понимаете, как лучше всего ввести ключевые слова, производительность поиска в указателе может повыситься.

### <a name="general-guidelines"></a>Общие рекомендации

-   Прокрутите записи указателей. Не все разделы индексируются одинаково. Нужный раздел может находиться в списке выше или ниже, чем ожидалось.

-   Не используйте местоимения, например "какой-то" или "этот", так как указатель их игнорирует.

-   Измените порядок введенных слов, если не удается найти требуемые записи.

    Например, если при вводе поискового запроса "отладка встроенного кода сборки" соответствующие записи не обнаружены, попробуйте ввести "код сборки, отладка встроенного".

-   Чтобы уменьшить количество результатов, воспользуйтесь фильтрами на вкладке **Указатель**.

### <a name="syntax-tips"></a>Советы по синтаксису

Если вы не можете найти запись для слова или фразы, которые вы ввели, сделайте следующее:

-   Введите первые несколько букв или корень слова. Если вы указали частичное совпадение, могут отобразиться разделы, индексированные с помощью ключевых слов в единственном или множественном числе.

    Например, введите "свойст" для поиска слова "свойство" или "свойства".

-   Для задачи, которую необходимо выполнить, введите деепричастие. Чтобы выполнить более точный поиск записей указателей, добавьте слово, точно описывающее искомый элемент.

    Например, введите "выполняемые", чтобы получить больше записей, или "выполняемые программы", чтобы сократить число записей.

-   Введите отдельные прилагательные. Чтобы сузить результаты поиска, добавьте слово, точно описывающее искомый элемент.

    Например, введите COM+, чтобы получить широкий диапазон записей, или "компоненты COM+" для получения меньшего числа записей.

-   Введите синоним искомого слова или команды.

    Например, если вы ввели термин "сборка", вместо него введите "создание".

## <a name="see-also"></a>См. также

- [Практическое руководство. Поиск разделов в содержании](../help-viewer/find-topics-toc.md)
- [Практическое руководство. Поиск разделов](../help-viewer/find-topics.md)
- [Окно справки (Майкрософт)](../help-viewer/overview.md)