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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4611b8c186e0293dae73cee4f9d845bb44c167c8
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59073543"
---
# <a name="icorprofilercallbackmovedreferences-method"></a>ICorProfilerCallback::MovedReferences – metoda
Volá se, aby sestavy nové rozložení objektů v haldě jako výsledek komprimaci uvolňování paměti.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT MovedReferences(  
    [in]  ULONG  cMovedObjectIDRanges,  
    [in, size_is(cMovedObjectIDRanges)] ObjectID oldObjectIDRangeStart[] ,  
    [in, size_is(cMovedObjectIDRanges)] ObjectID newObjectIDRangeStart[] ,  
    [in, size_is(cMovedObjectIDRanges)] ULONG    cObjectIDRangeLength[] );  
```  
  
## <a name="parameters"></a>Parametry  
 `cMovedObjectIDRanges`  
 [in] Počet bloků souvislých objektů, které přesunout v důsledku komprimaci kolekce uvolnění paměti. To znamená, že hodnota `cMovedObjectIDRanges` je celková velikost `oldObjectIDRangeStart`, `newObjectIDRangeStart`, a `cObjectIDRangeLength` pole.  
  
 Následující tři argumenty `MovedReferences` jsou paralelní pole. Jinými slovy `oldObjectIDRangeStart[i]`, `newObjectIDRangeStart[i]`, a `cObjectIDRangeLength[i]` všechny týkají jeden blok souvislé objektů.  
  
 `oldObjectIDRangeStart`  
 [in] Pole `ObjectID` hodnot, z nichž každý je počáteční adresa blok souvislé původní (předběžné uvolňování), živé objekty v paměti.  
  
 `newObjectIDRangeStart`  
 [in] Pole `ObjectID` hodnot, z nichž každý je novou počáteční adresu (po uvolňování) blok souvislé, živé objekty v paměti.  
  
 `cObjectIDRangeLength`  
 [in] Pole celých čísel, z nichž každý je velikost bloku souvislých objektů v paměti.  
  
 Zadat velikost pro každý blok, na který odkazuje `oldObjectIDRangeStart` a `newObjectIDRangeStart` pole.  
  
## <a name="remarks"></a>Poznámky  
  
> [!IMPORTANT]
>  Tato metoda oznamuje velikosti jako `MAX_ULONG` pro objekty, které jsou větší než 4 GB na 64bitových platformách. Chcete-li získat velikost objekty, které jsou větší než 4 GB, použijte [icorprofilercallback4::movedreferences2 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-movedreferences2-method.md) metoda místo.  
  
 Komprimace systému uvolňování paměti získá paměť obsazené nepoužívanými objekty a zkomprimuje uvolní místo. V důsledku toho mohou být přesunuty živé objekty v rámci haldy, a `ObjectID` může změnit hodnoty distribuuje společnost předchozí oznámení.  
  
 Předpokládejme, že existující `ObjectID` hodnotu (`oldObjectID`) najdete v následujícím rozsahu:  
  
 `oldObjectIDRangeStart[i]` <= `oldObjectID` < `oldObjectIDRangeStart[i]` + `cObjectIDRangeLength[i]`  
  
 Posun od začátku rozsahu na začátek objekt v tomto případě je následujícím způsobem:  
  
 `oldObjectID` - `oldObjectRangeStart[i]`  
  
 Jakoukoli hodnotu z `i` , který je v následujícím rozsahu:  
  
 0 <= `i` < `cMovedObjectIDRanges`  
  
 můžete vypočítat nové `ObjectID` následujícím způsobem:  
  
 `newObjectID` = `newObjectIDRangeStart[i]` + (`oldObjectID` – `oldObjectIDRangeStart[i]`)  
  
 Žádná z `ObjectID` hodnotu předanou `MovedReferences` jsou platné během zpětného volání, protože kolekce uvolnění paměti může být uvnitř přesun objektů ze staré umístění do nového umístění. Proto by se neměly pokoušet profilery pro kontrolu objektů během `MovedReferences` volání. A [ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) zpětného volání znamená, že se přesunuly všechny objekty do jejich nových umístění a provést kontrolu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerCallback – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [MovedReferences2 – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-movedreferences2-method.md)
- [Rozhraní pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Profilace](../../../../docs/framework/unmanaged-api/profiling/index.md)
