---
title: Метод marker_series::write_alert | Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- cvmarkersobj/Concurrency::diagnostic:marker_series::write_alert
helpviewer_keywords:
- Concurrency::diagnostic:marker_series::write_alert method
ms.assetid: 9d5465c7-f862-47a7-b249-4116605075a6
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 635f767f97ea3d237aeff843e99735eccae31efc
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/18/2020
ms.locfileid: "62831388"
---
# <a name="marker_serieswrite_alert-method"></a>Метод marker_series::write_alert
Записывает оповещение в файл трассировки визуализатора параллелизма.

## <a name="syntax"></a>Синтаксис

```cpp
void write_alert(
   _In_ LPCTSTR _Format,
   ...
);
```

#### <a name="parameters"></a>Параметры
 `_Format` Строка составного формата, содержащая текст, перемежаемый нулями или другими элементами форматирования, которые соответствуют объектам в списке аргументов.

## <a name="requirements"></a>Требования
 **Заголовок:** *cvmarkersobj.h*

 **Пространство имен:** Concurrency::diagnostic

## <a name="see-also"></a>См. также
- [Класс marker_series](../profiling/marker-series-class.md)