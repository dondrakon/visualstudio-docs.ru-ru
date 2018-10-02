---
title: Управление несколькими потоками в управляемом коде | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 59730063-cc29-4dae-baff-2234ad8d0c8f
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7be5763081da023742f53c3b2d22e0d0f4aad167
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47560467"
---
# <a name="managing-multiple-threads-in-managed-code"></a>Управление несколькими потоками в управляемом коде
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [как: управление несколькими потоками в управляемом коде](https://docs.microsoft.com/visualstudio/extensibility/managing-multiple-threads-in-managed-code).  
  
Если у вас есть управляемое расширение VSPackage, который вызывает асинхронные методы или имеет операции, которые выполняются в потоках, отличных от потока пользовательского интерфейса Visual Studio, необходимо следовать приведенным ниже рекомендациям. Поскольку она не требует ожидания для работы в другом потоке, чтобы завершить, можно хранить в потоке пользовательского интерфейса быстро реагирующих. Вы можете сделать свой код более эффективным, так как у вас нет дополнительных потоков, которые занимают пространство стека, и его можно сделать более надежным и простым для отладки, так как избежать взаимоблокировок и зависаний.  
  
 Как правило, вы можете из потока пользовательского интерфейса на другой поток, или наоборот. При возвращении метода текущий поток является поток, из которого он изначально был вызван.  
  
> [!IMPORTANT]
>  Следующие рекомендации использовать интерфейсы API в <xref:Microsoft.VisualStudio.Threading> пространства имен, в частности, <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory> класса. API-интерфейсы в этом пространстве имен являются новыми в [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)]. Можно получить экземпляр <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory> из <xref:Microsoft.VisualStudio.Shell.ThreadHelper> свойство `ThreadHelper.JoinableTaskFactory`.  
  
## <a name="switching-from-the-ui-thread-to-a-background-thread"></a>Переключение из потока пользовательского интерфейса в фоновый поток  
  
1.  Если вы хотите сделать асинхронной работы в фоновом потоке в потоке пользовательского интерфейса, используйте Task.Run():  
  
    ```csharp  
    await Task.Run(async delegate{  
        // Now you’re on a separate thread.  
    });  
    // Now you’re back on the UI thread.  
  
    ```  
  
2.  Если вы являетесь в потоке пользовательского интерфейса, и вы хотите заблокировать синхронно, во время работы в фоновом потоке, используйте <xref:System.Threading.Tasks.TaskScheduler> свойство `TaskScheduler.Default` внутри <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.Run%2A>:  
  
    ```csharp  
    // using Microsoft.VisualStudio.Threading;  
    ThreadHelper.JoinableTaskFactory.Run(async delegate {  
        await TaskScheduler.Default;  
        // You're now on a separate thread.  
        DoSomethingSynchronous();  
        await OrSomethingAsynchronous();  
    });  
    ```  
  
## <a name="switching-from-a-background-thread-to-the-ui-thread"></a>Переключение из фонового потока в поток пользовательского интерфейса  
  
1.  Если вы в фоновом потоке, и вы хотите сделать что-нибудь в потоке пользовательского интерфейса, используйте <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A>:  
  
    ```csharp  
    // Switch to main thread  
    await ThreadHelper.JoinableTaskFactory.SwitchToMainThreadAsync();  
    ```  
  
     Можно использовать <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.SwitchToMainThreadAsync%2A> метод, чтобы переключиться на поток пользовательского интерфейса. Этот метод отправляет сообщение в поток пользовательского интерфейса с продолжением текущего асинхронного метода и также обменивается данными с остальной частью платформы потоков для задания правильного приоритет и избежать взаимоблокировок.  
  
     Если ваш метод фонового потока не асинхронной и вы не можете принять асинхронный, по-прежнему можно использовать `await` синтаксис, чтобы переключиться на поток пользовательского интерфейса путем заключения работу с <xref:Microsoft.VisualStudio.Threading.JoinableTaskFactory.Run%2A>, как показано в этом примере:  
  
    ```csharp  
    ThreadHelper.JoinableTaskFactory.Run(async delegate {  
        // Switch to main thread  
        await ThreadHelper.JoinableTaskFactory.SwitchToMainThreadAsync();  
        // Do your work on the main thread here.  
    });  
    ```
