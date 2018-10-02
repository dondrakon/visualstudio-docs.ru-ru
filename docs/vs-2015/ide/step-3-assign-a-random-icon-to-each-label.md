---
title: Шаг 3. Назначение каждой метке случайного значка | Документы Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0ba5ed7a-9aaa-41f4-95d2-e3c2d567bc79
caps.latest.revision: 33
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: c5b906fbae93823c106dead99534979fe78bdcd7
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47560435"
---
# <a name="step-3-assign-a-random-icon-to-each-label"></a>Шаг 3. Назначение каждой метке случайного значка
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [Step 3: назначение каждой метке случайного значка](https://docs.microsoft.com/visualstudio/ide/step-3-assign-a-random-icon-to-each-label).  
  
Если значки оказываются в одной и той же ячейке каждую игру, игра становится слишком простой. Чтобы избежать этого, назначайте значки меткам случайным образом, используя для этого метод `AssignIconsToSquares()`.  
  
### <a name="to-assign-a-random-icon-to-each-label"></a>Назначение каждой метке случайного значка  
  
1.  Перед добавлением следующего кода разберитесь в принципе его работы. В C# есть новое ключевое слово `foreach`, а в Visual Basic — `For Each`. (Одна из строк закомментирована по причине, описанной в конце этой процедуры.)  
  
     [!code-csharp[VbExpressTutorial4Step2_3_4#2](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step2_3_4/cs/form1.cs#2)]
     [!code-vb[VbExpressTutorial4Step2_3_4#2](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step2_3_4/vb/form1.vb#2)]  
  
2.  Добавьте метод `AssignIconsToSquares()`, как показано в предыдущем шаге. Вы можете поместить его сразу же после кода, добавленного в разделе [Шаг 2. Добавление случайного объекта и списка значков](../ide/step-2-add-a-random-object-and-a-list-of-icons.md).  
  
     Как было сказано выше, в методе `AssignIconsToSquares()` имеется определенное нововведение: цикл `foreach` в Visual C# и `For Each` в Visual Basic. Цикл `For Each` можно использовать в любое время для выполнения одного и того же действия несколько раз. В данном случае требуется выполнять одни и те же операторы для каждой метки в TableLayoutPanel, как показано в следующем коде. Первая строка создает переменную с именем `control`, которая хранит каждый элемент управления по одному, пока у этого элемента управления есть инструкции в цикле, выполняемом для него.  
  
     [!code-csharp[VbExpressTutorial4Step2_3_4#14](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step2_3_4/cs/form1.cs#14)]
     [!code-vb[VbExpressTutorial4Step2_3_4#14](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step2_3_4/vb/form1.vb#14)]  
  
    > [!NOTE]
    >  Используются имена iconLabel и control, поскольку они являются описательными. Можно заменить эти имена на любые другие и это не повлияет на работу кода (при условии, что имена будут изменены имена в каждом операторе внутри цикла).  
  
     Метод `AssignIconsToSquares()` перебирает все элементы управления Label в TableLayoutPanel и выполняет одни и те же операторы для каждого из них. Эти операторы запрашивают случайные значки из списка, добавленного в процедуре [Шаг 2. Добавление случайного объекта и списка значков](../ide/step-2-add-a-random-object-and-a-list-of-icons.md). (Вот почему в список включено по два значка. Это позволяет назначить пару значков случайным элементам управления Label.)  
  
     Внимательнее рассмотрите код, выполняемый внутри цикла `foreach` или `For Each`. Этот код воспроизведен здесь.  
  
     [!code-csharp[VbExpressTutorial4Step2_3_4#16](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step2_3_4/cs/form1.cs#16)]
     [!code-vb[VbExpressTutorial4Step2_3_4#16](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step2_3_4/vb/form1.vb#16)]  
  
     Первая строка преобразует переменную `control` в метку с именем `iconLabel`. Следующая строка представляет собой оператор `if`, проверяющий и обеспечивающий успешное выполнение преобразования. Если преобразование выполняется, выполняются операторы в операторе `if`. (Как можно вспомнить из предыдущих занятий, оператор `if` используется для проверки заданного условия). Первая строка в операторе `if` создает переменную с именем `randomNumber`, содержащую случайное число, соответствующее одному из элементов списка значков. Для этого используется метод `Next` объекта `Random`, созданного ранее. Метод `Next` возвращает случайное число. Эта строка также использует свойство `Count` списка `icons` для определения диапазона, из которого выбирается случайное число. В следующей строке один из элементов списка значков присваивается свойству `Text` этой метки. Пояснения относительно строки с комментариям приводятся далее в этом разделе. Наконец, последняя строка в операторе `if` удаляет из списка значок, добавленный в форму.  
  
     Помните, если вы не уверены, что делает какая-либо часть кода, можно навести указатель мыши на элемент кода и посмотреть отображаемую подсказку. Можно также выполнять каждую строку кода пошагово после запуска программы, воспользовавшись отладчиком Visual Studio. Дополнительные сведения см. в разделе [Практические советы. Пошаговая работа с отладчиком в Visual Studio](http://msdn.microsoft.com/vstudio/ee672313.aspx) или [Навигация по коду с помощью отладчика](../debugger/navigating-through-code-with-the-debugger.md).  
  
3.  Чтобы быстро заполнить игровое поле значками, необходимо вызвать метод `AssignIconsToSquares()` сразу после запуска программы. При написании кода на языке Visual C# добавьте оператор после вызова метода `InitializeComponent()` в *конструкторе* `Form1`. В этом случае форма будет вызывать новый метод для ее настройки перед отображением. Конструкторы вызываются при создании нового объекта, такого как класс или структура. Дополнительные сведения см. в разделах [Конструкторы (руководство по программированию на C#)](http://msdn.microsoft.com/library/ace5hbzh.aspx) и [Использование конструкторов и деструкторов](http://msdn.microsoft.com/library/2z08e49e%28v=vs.90%29.aspx) в Visual Basic.  
  
     [!code-csharp[VbExpressTutorial4Step2_3_4#13](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step2_3_4/cs/form1.cs#13)]  
  
     В Visual Basic добавьте вызов метода `AssignIconsToSquares()` в метод `Form1_Load`, чтобы код выглядел следующим образом.  
  
    ```vb  
    Private Sub Form1_Load(sender As Object, e As EventArgs) Handles MyBase.Load  
        AssignIconsToSquares()  
    End Sub  
    ```  
  
4.  Сохраните и выполните программу. Должна отобразиться форма со случайными значками, которые назначены каждой метке.  
  
5.  Закройте программу, а затем снова запустите ее. Обратите внимание, что теперь каждой метке назначены другие значки, как показано на следующем рисунке.  
  
     ![Игра "Подбери пару!" со случайными значками](../ide/media/express-tut4step3.png "Express_Tut4Step3")  
Игра "Подбери пару!" со случайными значками  
  
     Значки видимы, поскольку они не были скрыты. Чтобы скрыть их из игрока, можно задать для свойства `Forecolor` каждой метки тот же цвет, что и у свойства `BackColor`.  
  
    > [!TIP]
    >  Другой способ скрывать элементы управления, например метки, — задать для свойства **Visible** значение `False`.  
  
6.  Чтобы скрыть значки, остановите программу и удалите метки комментариев с соответствующей строки кода в цикле `For Each`.  
  
     [!code-csharp[VbExpressTutorial4Step2_3_4#15](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial4step2_3_4/cs/form1.cs#15)]
     [!code-vb[VbExpressTutorial4Step2_3_4#15](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial4step2_3_4/vb/form1.vb#15)]  
  
7.  На панели меню нажмите кнопку **Сохранить все**, чтобы сохранить программу, а затем запустите программу. Похоже, что значки исчезли. Отображается только голубой фон. Однако значки назначены случайным образом и по-прежнему существуют. Поскольку значки имеют тот же цвет, что и фон, они невидимы, т. е. скрыты от игрока. Наконец, игра станет неинтересной, если игрок будет сразу видеть все значки!  
  
### <a name="to-continue-or-review"></a>Продолжить или повторить пройденный материал  
  
-   Следующий шаг руководства: [Шаг 4. Добавление к каждой метке обработчика событий щелчка мышью](../ide/step-4-add-a-click-event-handler-to-each-label.md).  
  
-   Предыдущий шаг руководства: [Шаг 2. Добавление случайного объекта и списка значков](../ide/step-2-add-a-random-object-and-a-list-of-icons.md).


