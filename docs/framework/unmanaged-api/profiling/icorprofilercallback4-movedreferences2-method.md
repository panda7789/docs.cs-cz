---
title: ICorProfilerCallback4::MovedReferences2 – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback4.MovedReferences2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback4::MovedReferences2
helpviewer_keywords:
- MovedReferences2 method, ICorProfilerCallback4 interface [.NET Framework profiling]
- ICorProfilerCallback4::MovedReferences2 method [.NET Framework profiling]
ms.assetid: d17a065b-5bc6-4817-b3e1-1e413fcb33a8
topic_type:
- apiref
ms.openlocfilehash: 79e54cde8757bbe690f9b7c4344a2a3cb19cf627
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84499379"
---
# <a name="icorprofilercallback4movedreferences2-method"></a>ICorProfilerCallback4::MovedReferences2 – metoda
Volá se, aby se nahlásilo nové rozložení objektů v haldě v důsledku komprimace uvolňování paměti. Tato metoda je volána, pokud profiler implementoval rozhraní [ICorProfilerCallback4](icorprofilercallback4-interface.md) . Toto zpětné volání nahrazuje metodu [ICorProfilerCallback:: MovedReferences –](icorprofilercallback-movedreferences-method.md) , protože může vykazovat větší rozsahy objektů, jejichž délka překračuje, co může být vyjádřeno v ulong.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT MovedReferences2(  
    [in]  ULONG  cMovedObjectIDRanges,  
    [in, size_is(cMovedObjectIDRanges)] ObjectID oldObjectIDRangeStart[] ,  
    [in, size_is(cMovedObjectIDRanges)] ObjectID newObjectIDRangeStart[] ,  
    [in, size_is(cMovedObjectIDRanges)] SIZE_T    cObjectIDRangeLength[] );  
```  
  
## <a name="parameters"></a>Parametry  
 `cMovedObjectIDRanges`  
 pro Počet bloků souvislých objektů, které byly přesunuty jako výsledek komprimace uvolňování paměti. To znamená, že hodnota `cMovedObjectIDRanges` je celková velikost `oldObjectIDRangeStart` `newObjectIDRangeStart` polí, a `cObjectIDRangeLength` .  
  
 Další tři argumenty `MovedReferences2` jsou paralelní pole. Jinými slovy,, `oldObjectIDRangeStart[i]` `newObjectIDRangeStart[i]` a všechny se `cObjectIDRangeLength[i]` týkají jednoho bloku souvislých objektů.  
  
 `oldObjectIDRangeStart`  
 pro Pole `ObjectID` hodnot, z nichž každá je staré (před uvolněním paměti) počáteční adresou bloku souvislých, živých objektů v paměti.  
  
 `newObjectIDRangeStart`  
 pro Pole `ObjectID` hodnot, z nichž každý je novou (po uvolnění paměti), která začíná adresou bloku souvislých objektů, živé objekty v paměti.  
  
 `cObjectIDRangeLength`  
 pro Pole celých čísel, z nichž každá je velikost bloku souvislých objektů v paměti.  
  
 Velikost je určena pro každý blok, na který je odkazováno `oldObjectIDRangeStart` v `newObjectIDRangeStart` polích a.  
  
## <a name="remarks"></a>Poznámky  
 Komprimace systému uvolňování paměti uvolní paměť, která je obsazená mrtvými objekty, a zkomprimuje uvolněné místo. V důsledku toho mohou být živé objekty přesunuty v rámci haldy a `ObjectID` hodnoty distribuované předchozími oznámeními se mohou změnit.  
  
 Předpokládat, že existující `ObjectID` hodnota ( `oldObjectID` ) leží v následujícím rozsahu:  
  
 `oldObjectIDRangeStart[i]` <= `oldObjectID` < `oldObjectIDRangeStart[i]` + `cObjectIDRangeLength[i]`  
  
 V tomto případě je posunutí od začátku rozsahu na začátek objektu následující:  
  
 `oldObjectID` - `oldObjectRangeStart[i]`  
  
 Pro libovolnou hodnotu `i` , která je v následujícím rozsahu:  
  
 0 <=`i` < `cMovedObjectIDRanges`  
  
 novou hodnotu můžete vypočítat následujícím `ObjectID` způsobem:  
  
 `newObjectID` = `newObjectIDRangeStart[i]`+ ( `oldObjectID` – `oldObjectIDRangeStart[i]` )  
  
 Žádná z `ObjectID` hodnot předaných není platná v rámci `MovedReferences2` samotného zpětného volání, protože systém uvolňování paměti může být uprostřed přesunutí objektů ze starých umístění do nových umístění. Proto by profilery neměly zkoušet při volání kontrolu objektů `MovedReferences2` . Zpětné volání [ICorProfilerCallback2:: GarbageCollectionFinished –](icorprofilercallback2-garbagecollectionfinished-method.md) označuje, že všechny objekty byly přesunuty do jejich nových umístění a lze provést kontrolu.  
  
 Pokud profiler implementuje rozhraní [ICorProfilerCallback](icorprofilercallback-interface.md) i [ICorProfilerCallback4](icorprofilercallback4-interface.md) , `MovedReferences2` je metoda volána před metodou [ICorProfilerCallback:: MovedReferences –](icorprofilercallback-movedreferences-method.md) , ale pouze v případě, že se `MovedReferences2` Metoda vrátí úspěšně. Profilery mohou vracet hodnotu HRESULT, která označuje selhání `MovedReferences2` metody, pro zamezení volání druhé metody.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerCallback – rozhraní](icorprofilercallback-interface.md)
- [MovedReferences – metoda](icorprofilercallback-movedreferences-method.md)
- [ICorProfilerCallback4 – rozhraní](icorprofilercallback4-interface.md)
- [Rozhraní pro profilaci](profiling-interfaces.md)
- [Profilace](index.md)
