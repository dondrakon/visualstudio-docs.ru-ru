---
title: IDebugEvent2 | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugEvent2
helpviewer_keywords:
- IDebugEvent2 interface
ms.assetid: de3d714d-96fb-4e12-b66b-a75391472153
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7fc387733e1472afe5f21f5e0638374ebda9f677
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47573266"
---
# <a name="idebugevent2"></a>IDebugEvent2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [IDebugEvent2](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugevent2).  
  
Этот интерфейс используется для обмена данными критически важная отладочная информация, например, по остановке в точке останова и не являющиеся критически сведения, такие как сообщение отладки.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
IDebugEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Примечания для разработчиков  
 Модуль отладки (DE) и поставщика пользовательского порта реализация этого интерфейса на один и тот же объект как все другие интерфейсы событий.  
  
## <a name="notes-for-callers"></a>Заметки о вызывающих объектов  
 С помощью интерфейса IID интерфейса, аргумент, заданный для [событий](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) или [событий](../../../extensibility/debugger/reference/idebugportevents2-event.md), диспетчер отладки сеансов (SDM) вызывает [QueryInterface](http://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) на `IDebugEvent2` интерфейс для получения интерфейс соответствующее событие.  
  
## <a name="methods-in-vtable-order"></a>Методы в порядке таблицы Vtable  
 В следующей таблице показаны методы `IDebugEvent2`.  
  
|Метод|Описание|  
|------------|-----------------|  
|[GetAttributes](../../../extensibility/debugger/reference/idebugevent2-getattributes.md)|Получает атрибуты для этого события отладки.|  
  
## <a name="remarks"></a>Примечания  
 Интерфейсы более конкретные события, такие как [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md), не являющихся производными от интерфейса IDebugEvent2, но вместо этого реализуются как отдельный интерфейс на один и тот же объект как `IDebugEvent2`.  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Базовых интерфейсов](../../../extensibility/debugger/reference/core-interfaces.md)   
 [Событие](../../../extensibility/debugger/reference/idebugportevents2-event.md)   
 [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
