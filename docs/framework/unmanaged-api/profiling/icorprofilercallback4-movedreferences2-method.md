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
ms.openlocfilehash: 2f305852ae218417aa1f4d4fe9d2076c0163fd60
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76865269"
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
 pro Počet bloků souvislých objektů, které byly přesunuty jako výsledek komprimace uvolňování paměti. To znamená, že hodnota `cMovedObjectIDRanges` je celková velikost polí `oldObjectIDRangeStart`, `newObjectIDRangeStart`a `cObjectIDRangeLength`.  
  
 Další tři argumenty `MovedReferences2` jsou paralelní pole. Jinými slovy `oldObjectIDRangeStart[i]`, `newObjectIDRangeStart[i]`a `cObjectIDRangeLength[i]` všechny se týkají jednoho bloku souvislých objektů.  
  
 `oldObjectIDRangeStart`  
 pro Pole hodnot `ObjectID`, z nichž každá je stará (před uvolněním paměti) počáteční adresou bloku souvislých, živých objektů v paměti.  
  
 `newObjectIDRangeStart`  
 pro Pole hodnot `ObjectID`, z nichž každá je novou (po uvolnění paměti), která začíná adresou bloku souvislých objektů, živé objekty v paměti.  
  
 `cObjectIDRangeLength`  
 pro Pole celých čísel, z nichž každá je velikost bloku souvislých objektů v paměti.  
  
 Pro každý blok, na který je odkazováno v polích `oldObjectIDRangeStart` a `newObjectIDRangeStart`, je zadána velikost.  
  
## <a name="remarks"></a>Poznámky  
 Komprimace systému uvolňování paměti uvolní paměť, která je obsazená mrtvými objekty, a zkomprimuje uvolněné místo. V důsledku toho mohou být živé objekty přesunuty v rámci haldy a `ObjectID` hodnoty distribuované předchozími oznámeními se mohou změnit.  
  
 Předpokládejme, že existující hodnota `ObjectID` (`oldObjectID`) leží v následujícím rozsahu:  
  
 `oldObjectIDRangeStart[i]` <= `oldObjectID` < `oldObjectIDRangeStart[i]` + `cObjectIDRangeLength[i]`  
  
 V tomto případě je posunutí od začátku rozsahu na začátek objektu následující:  
  
 `oldObjectID` - `oldObjectRangeStart[i]`  
  
 Pro libovolnou hodnotu `i`, která je v následujícím rozsahu:  
  
 0 <= `i` < `cMovedObjectIDRanges`  
  
 novou `ObjectID` můžete vypočítat následujícím způsobem:  
  
 `newObjectID` = `newObjectIDRangeStart[i]` + (`oldObjectID` – `oldObjectIDRangeStart[i]`)  
  
 Žádná z hodnot `ObjectID` předaných `MovedReferences2` nejsou během samotného zpětného volání platná, protože systém uvolňování paměti může být uprostřed přesunutí objektů ze starých umístění do nových umístění. Proto by se profilery neměly pokoušet prozkoumat objekty během volání `MovedReferences2`. Zpětné volání [ICorProfilerCallback2:: GarbageCollectionFinished –](icorprofilercallback2-garbagecollectionfinished-method.md) označuje, že všechny objekty byly přesunuty do jejich nových umístění a lze provést kontrolu.  
  
 Pokud profiler implementuje rozhraní [ICorProfilerCallback](icorprofilercallback-interface.md) i [ICorProfilerCallback4](icorprofilercallback4-interface.md) , je metoda `MovedReferences2` volána před metodou [ICorProfilerCallback:: MovedReferences –](icorprofilercallback-movedreferences-method.md) , ale pouze v případě, že se metoda `MovedReferences2` úspěšně vrátí. Profilery mohou vracet hodnotu HRESULT, která označuje selhání z metody `MovedReferences2`, aby se předešlo volání druhé metody.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerCallback – rozhraní](icorprofilercallback-interface.md)
- [MovedReferences – metoda](icorprofilercallback-movedreferences-method.md)
- [ICorProfilerCallback4 – rozhraní](icorprofilercallback4-interface.md)
- [Rozhraní pro profilaci](profiling-interfaces.md)
- [Profilace](index.md)
