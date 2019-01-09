---
title: Общие сведения о Visual Studio для разработчиков на Python
titleSuffix: ''
ms.date: 12/14/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
dev_langs:
- Python
ms.workload:
- python
- data-science
ms.openlocfilehash: 5c7e8c81b52744d62dbdc60259462e7dedc1388e
ms.sourcegitcommit: f6dd17b0864419083d0a1bf54910023045526437
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/27/2018
ms.locfileid: "53804907"
---
# <a name="welcome-to-the-visual-studio-ide--python"></a>Введение в интегрированную среду разработки Visual Studio (Python)

*Интегрированная среда разработки* Visual Studio — это оригинальная среда запуска для Python и других языков программирования, которая позволяет редактировать, отлаживать и тестировать код, а затем публиковать приложения. Интегрированная среда разработки (IDE) — это многофункциональная программа, которую можно использовать для различных аспектов разработки программного обеспечения. Помимо стандартного редактора и отладчика, которые предлагаются в большинстве сред IDE, Visual Studio включает средства дополнения кода, графические среды REPL и другие функции, позволяющие упростить процесс разработки программного обеспечения.

[![Visual Studio с открытым проектом Python](media/tour-ide-overview.png)](media/tour-ide-overview.png#lightbox)

На этом рисунке показана среда Visual Studio, в которой открыт проект Python и несколько окон с основными инструментами, которые вы будете часто использовать.

- [**Обозреватель решений**](../ide/solutions-and-projects-in-visual-studio.md) (правый верхний угол) позволяет просматривать файлы кода, а также перемещаться по ним и управлять ими. **Обозреватель решений** позволяет упорядочить код путем объединения файлов в [решения и проекты](/visualstudio/get-started/tutorial-projects-solutions).
    - Рядом с **обозревателем решений** располагается окно [**Среды Python**](managing-python-environments-in-visual-studio.md), где вы можете управлять интерпретаторами Python, которые установлены на компьютере.

- В [окне редактора](../ide/writing-code-in-the-code-and-text-editor.md) (центр), где вы, скорее всего, будете проводить большую часть времени, отображается содержимое файла. Здесь можно [редактировать код Python](editing-python-code-in-visual-studio.md), перемещаться по структуре кода и настраивать точки останова для сеансов отладки. Вы можете выбрать фрагмент кода Python и нажать сочетание клавиш Ctrl+ВВОД, чтобы выполнить выбранный код в [интерактивном окне REPL](python-interactive-repl-in-visual-studio.md).

- В окно [вывода](../ide/reference/output-window.md) (в центре внизу) Visual Studio отправляет уведомления, такие как сообщения об отладке и ошибках, предупреждения, сообщения о состоянии публикаций и многие другие. Каждый источник сообщений имеет собственную вкладку.
    - Объект [интерактивное окно REPL для Python](python-interactive-repl-in-visual-studio.md) отображается в той же области, что и окно вывода.

- [Team Explorer](/azure/devops/user-guide/work-team-explorer?view=vsts) (правый нижний угол) позволяет отслеживать рабочие элементы и использовать код совместно с другими пользователями с помощью технологий управления версиями, таких как [Git](https://git-scm.com/) и [система управления версиями Team Foundation (TFVC)](/azure/devops/repos/tfvc/overview?view=vsts).

## <a name="editions"></a>Выпуски

Visual Studio предоставляется для Windows и Mac, но поддержка Python доступна только в Visual Studio для Windows.

Существует три выпуска Visual Studio 2017 для Windows: Community, Professional и Enterprise. Сведения о функциях, поддерживаемых в каждом выпуске, см. в статье [Сравнение интегрированных сред разработки Visual Studio 2017](https://visualstudio.microsoft.com/vs/compare/).

## <a name="popular-productivity-features"></a>Популярные средства повышения производительности

Ниже перечислены некоторые популярные возможности Visual Studio, которые помогут вам повысить продуктивность разработки программного обеспечения.

- [IntelliSense](editing-python-code-in-visual-studio.md#intellisense)

   IntelliSense — это набор функций, отображающих сведения о коде непосредственно в редакторе и в некоторых случаях автоматически создающих небольшие отрывки кода. По сути, это базовая документация, встроенная в редактор, с которой вам не приходится искать информацию где-то еще. Функции IntelliSense зависят от языка. Подробности для Python вы найдете в этой [статье о редактировании кода Python](editing-python-code-in-visual-studio.md#intellisense). На следующем рисунке показано, как IntelliSense отображает список членов типа:

   ![Автозавершение элементов с использованием Visual Studio IntelliSense](media/code-editing-completions-simple.png)

- [Рефакторинг](refactoring-python-code.md)

   Щелкнув фрагмент кода правой кнопкой мыши и выбрав пункт меню **Быстрые действия и рефакторинг**, вы сможете применить такие операции Visual Studio, как интеллектуальное переименование переменных, извлечение одной или нескольких строк кода в новый метод, изменение порядка параметров методов и многое другое.

   ![Рефакторинг в Visual Studio](media/tour-ide-refactor-extract-method.png)

- [Выделение](refactoring-python-code.md)

   Анализ кода проверяет наличие ошибок и типичных проблем в коде Python, помогая вам придерживаться правильных шаблонов кодирования на Python.

   ![Команда PyLint в контекстном меню для проектов Python](media/code-pylint-command.png)

- [Быстрый запуск](../ide/reference/quick-launch-environment-options-dialog-box.md)

   Среда Visual Studio может показаться сложной, ведь там столько разных меню, параметров и свойств. Поле поиска **быстрого запуска** позволяет быстро найти нужное содержимое в Visual Studio. Когда вы начнете вводить в поле то, что вы ищете, Visual Studio представит результаты, один из которых точно вам подойдет. Если вам нужно добавить функциональные возможности в Visual Studio, например добавить поддержку дополнительных языков программирования, **быстрый запуск** предоставляет результаты, которые открывают Visual Studio Installer для установки рабочей нагрузки или отдельного компонента.

   ![Поле поиска в быстром запуске в Visual Studio](media/tour-ide-quick-launch.png)

- Волнистые линии и [быстрые действия](../ide/quick-actions.md)

   Волнистые линии обозначают ошибки или потенциальные проблемы кода прямо во время ввода. Эти визуальные подсказки позволяют устранять проблемы немедленно и не ждать, пока ошибка будет обнаружена во время сборки или запуска программы. Если навести указатель мыши на волнистую линию, на экран будут выведены дополнительные сведения об ошибке. Кроме того, в поле слева может появляться значок лампочки с быстрыми действиями по устранению ошибки.

   ![Волнистые линии в Visual Studio](media/tour-ide-squiggles.png)

- ["Перейти к определению" и "Показать определение"](../ide/go-to-and-peek-definition.md)

   Функция **Перейти к определению** позволяет перейти туда, где определена выбранная функция или тип. Команда **Показать определения** отображает определение в том же окне, не открывая другой файл. Команда **Поиск всех ссылок** также будет полезна для поиска мест, где используется и (или) определяется выбранный идентификатор.

   ![Команды для навигации по коду](media/tour-ide-navigation-commands.png)

## <a name="powerful-features-for-python"></a>Мощные функции для Python

- [Интерактивная оболочка REPL для Python](python-interactive-repl-in-visual-studio.md)

    Visual Studio предоставляет интерактивное окно для цикла REPL (read–eval–print loop) отдельно для каждого окружения Python, что дает ряд преимуществ над интерфейсом REPL из командной строки *python.exe*. В **интерактивном** окне вы можете ввести произвольный код Python и сразу же увидеть результаты его выполнения.

    ![Интерактивное окно Python](media/interactive-window.png)

- [Отладка](debugging-python-in-visual-studio.md)

    Visual Studio предоставляет широкие возможности отладки для Python, включая присоединение к выполняемым процессам, вычисление выражений в окнах **контрольных значений** и **интерпретации**, проверку локальных переменных, точки останова, инструкции "Шаг с заходом", "Шаг с выходом", "Шаг с обходом", команду **Задать следующий оператор** и многое другое. Также есть возможность удаленно отлаживать код Python, выполняющийся на компьютерах Linux.

    ![Отладка Python в Visual Studio](media/remote-debugging-breakpoint-hit.png)

- [Взаимодействие с C++](working-with-c-cpp-python-in-visual-studio.md)

    Многие библиотеки для Python создаются на языке C++ для повышения производительности. Visual Studio предоставляет широкие возможности для разработки расширений для C++, в том числе поддерживает [отладку в смешанном режиме](debugging-mixed-mode-c-cpp-python-in-visual-studio.md).

    ![Отладка в смешанном режиме для Python и C++](media/mixed-mode-debugging.png)

- [Профилирование](profiling-python-code-in-visual-studio.md)

    Если вы используете интерпретатор на основе CPython, производительность кода Python можно оценить прямо в Visual Studio.

    ![Отчет профилирования о производительности](media/profiling-results.png)

- [Модульное тестирование](unit-testing-python-in-visual-studio.md)

    Visual Studio предоставляет встроенную поддержку для обнаружения, запуска и отладки модульных тестов в контексте интегрированной среды разработки.

    ![Отображение неудачного результата для модульного тестирования](media/unit-test-A-fail.png)

## <a name="next-steps"></a>Следующие шаги

Подробнее изучить возможности по работе с Python в Visual Studio вам помогут следующие руководства.

> [!div class="nextstepaction"]
> [Краткое руководство. Создание веб-приложения на Flask](../ide/quickstart-python.md?toc=/visualstudio/python/toc.json&bc=/visualstudio/python/_breadcrumb/toc.json)

> [!div class="nextstepaction"]
> [Работа с Python в Visual Studio](tutorial-working-with-python-in-visual-studio-step-01-create-project.md)

> [!div class="nextstepaction"]
> [Начало работы с веб-платформой Django в Visual Studio](learn-django-in-visual-studio-step-01-project-and-solution.md)

> [!div class="nextstepaction"]
> [Начало работы с веб-платформой Flask в Visual Studio](learn-flask-visual-studio-step-01-project-solution.md)

## <a name="see-also"></a>См. также

- Откройте для себя [другие возможности Visual Studio](../ide/advanced-feature-overview.md)
- Посетите [visualstudio.microsoft.com](https://visualstudio.microsoft.com/vs/)
- Читайте [блог Visual Studio](https://blogs.msdn.microsoft.com/visualstudio/)
- Посетите бесплатные курсы по Visual Studio на сайте [Microsoft Virtual Academy](https://mva.microsoft.com/product-training/visual-studio-courses#!index=2&lang=1033)