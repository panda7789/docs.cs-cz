---
title: ICorProfilerCallback::MovedReferences – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.MovedReferences
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::MovedReferences
helpviewer_keywords:
- MovedReferences method [.NET Framework profiling]
- ICorProfilerCallback::MovedReferences method [.NET Framework profiling]
ms.assetid: 996c71ae-0676-4616-a085-84ebf507649d
topic_type:
- apiref
ms.openlocfilehash: 1214182c95f7d0304ec920a2ea7dae91b1f4a790
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503330"
---
# <a name="icorprofilercallbackmovedreferences-method"></a>ICorProfilerCallback::MovedReferences – metoda
Volá se, aby se nahlásilo nové rozložení objektů v haldě v důsledku komprimace uvolňování paměti.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT MovedReferences(  
    [in]  ULONG  cMovedObjectIDRanges,  
    [in, size_is(cMovedObjectIDRanges)] ObjectID oldObjectIDRangeStart[] ,  
    [in, size_is(cMovedObjectIDRanges)] ObjectID newObjectIDRangeStart[] ,  
    [in, size_is(cMovedObjectIDRanges)] ULONG    cObjectIDRangeLength[] );  
```  
  
## <a name="parameters"></a>Parametry  
 `cMovedObjectIDRanges`  
 pro Počet bloků souvislých objektů, které byly přesunuty jako výsledek komprimace uvolňování paměti. To znamená, že hodnota `cMovedObjectIDRanges` je celková velikost `oldObjectIDRangeStart` `newObjectIDRangeStart` polí, a `cObjectIDRangeLength` .  
  
 Další tři argumenty `MovedReferences` jsou paralelní pole. Jinými slovy,, `oldObjectIDRangeStart[i]` `newObjectIDRangeStart[i]` a všechny se `cObjectIDRangeLength[i]` týkají jednoho bloku souvislých objektů.  
  
 `oldObjectIDRangeStart`  
 pro Pole `ObjectID` hodnot, z nichž každá je staré (před uvolněním paměti) počáteční adresou bloku souvislých, živých objektů v paměti.  
  
 `newObjectIDRangeStart`  
 pro Pole `ObjectID` hodnot, z nichž každý je novou (po uvolnění paměti), která začíná adresou bloku souvislých objektů, živé objekty v paměti.  
  
 `cObjectIDRangeLength`  
 pro Pole celých čísel, z nichž každá je velikost bloku souvislých objektů v paměti.  
  
 Velikost je určena pro každý blok, na který je odkazováno `oldObjectIDRangeStart` v `newObjectIDRangeStart` polích a.  
  
## <a name="remarks"></a>Poznámky  
  
> [!IMPORTANT]
> Tato metoda oznamuje velikost `MAX_ULONG` pro objekty, které jsou větší než 4 GB na 64 bitů. Chcete-li získat velikost objektů, které jsou větší než 4 GB, použijte místo toho metodu [ICorProfilerCallback4:: MovedReferences2 –](icorprofilercallback4-movedreferences2-method.md) .  
  
 Komprimace systému uvolňování paměti uvolní paměť, která je obsazená mrtvými objekty, a zkomprimuje uvolněné místo. V důsledku toho mohou být živé objekty přesunuty v rámci haldy a `ObjectID` hodnoty distribuované předchozími oznámeními se mohou změnit.  
  
 Předpokládat, že existující `ObjectID` hodnota ( `oldObjectID` ) leží v následujícím rozsahu:  
  
 `oldObjectIDRangeStart[i]` <= `oldObjectID` < `oldObjectIDRangeStart[i]` + `cObjectIDRangeLength[i]`  
  
 V tomto případě je posunutí od začátku rozsahu na začátek objektu následující:  
  
 `oldObjectID` - `oldObjectRangeStart[i]`  
  
 Pro libovolnou hodnotu `i` , která je v následujícím rozsahu:  
  
 0 <=`i` < `cMovedObjectIDRanges`  
  
 novou hodnotu můžete vypočítat následujícím `ObjectID` způsobem:  
  
 `newObjectID` = `newObjectIDRangeStart[i]`+ ( `oldObjectID` – `oldObjectIDRangeStart[i]` )  
  
 Žádná z `ObjectID` hodnot předaných není platná v rámci `MovedReferences` samotného zpětného volání, protože uvolňování paměti může být uprostřed přesunutí objektů ze starých umístění do nových umístění. Proto by profilery neměly zkoušet při volání kontrolu objektů `MovedReferences` . Zpětné volání [ICorProfilerCallback2:: GarbageCollectionFinished –](icorprofilercallback2-garbagecollectionfinished-method.md) označuje, že všechny objekty byly přesunuty do jejich nových umístění a lze provést kontrolu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerCallback – rozhraní](icorprofilercallback-interface.md)
- [MovedReferences2 – metoda](icorprofilercallback4-movedreferences2-method.md)
- [Rozhraní pro profilaci](profiling-interfaces.md)
- [Profilace](index.md)
