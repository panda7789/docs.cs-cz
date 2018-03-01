---
title: "ICorProfilerCallback::MovedReferences – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 6d62fbdf4b6dd2acbb67b0655938990d625f8df8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallbackmovedreferences-method"></a>ICorProfilerCallback::MovedReferences – metoda
Volá se pro sestavy nové rozložení objektů v haldě v důsledku komprimaci uvolnění paměti.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT MovedReferences(  
    [in]  ULONG  cMovedObjectIDRanges,  
    [in, size_is(cMovedObjectIDRanges)] ObjectID oldObjectIDRangeStart[] ,  
    [in, size_is(cMovedObjectIDRanges)] ObjectID newObjectIDRangeStart[] ,  
    [in, size_is(cMovedObjectIDRanges)] ULONG    cObjectIDRangeLength[] );  
```  
  
#### <a name="parameters"></a>Parametry  
 `cMovedObjectIDRanges`  
 [v] Počet bloků souvislý objektů, které přesunout v důsledku komprimaci uvolnění paměti. To znamená, hodnota `cMovedObjectIDRanges` je celková velikost `oldObjectIDRangeStart`, `newObjectIDRangeStart`, a `cObjectIDRangeLength` pole.  
  
 Následující tři argumenty `MovedReferences` jsou paralelní pole. Jinými slovy `oldObjectIDRangeStart[i]`, `newObjectIDRangeStart[i]`, a `cObjectIDRangeLength[i]` všechny jeden blok souvislý objektů, které se týkají.  
  
 `oldObjectIDRangeStart`  
 [v] Pole `ObjectID` hodnoty, z nichž každý je starý (předběžné uvolňování paměti) počáteční adresa blok souvislý, live objekty v paměti.  
  
 `newObjectIDRangeStart`  
 [v] Pole `ObjectID` hodnoty, z nichž každý je nové počáteční adresa (po uvolnění paměti) blok souvislý, live objekty v paměti.  
  
 `cObjectIDRangeLength`  
 [v] Pole celých čísel, z nichž každý je velikost bloku souvislý objektů v paměti.  
  
 Velikost je zadán pro každý blok, který se odkazuje v `oldObjectIDRangeStart` a `newObjectIDRangeStart` pole.  
  
## <a name="remarks"></a>Poznámky  
  
> [!IMPORTANT]
>  Tato metoda sestavy velikosti jako `MAX_ULONG` pro objekty, které jsou větší než 4 GB na 64bitových platformách. Velikost objekty, které jsou větší než 4 GB, použijte [icorprofilercallback4::movedreferences2 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-movedreferences2-method.md) metoda místo.  
  
 Komprimaci uvolňování paměti získá paměť obsazená neaktivní objekty a zkomprimuje uvolní místo. V důsledku toho může přesunout živé objekty v rámci haldy, a `ObjectID` mohou změnit hodnoty distribuovat předchozí oznámení.  
  
 Předpokládáme, že existující `ObjectID` hodnotu (`oldObjectID`) v rozmezí následující:  
  
 `oldObjectIDRangeStart[i]` <= `oldObjectID` < `oldObjectIDRangeStart[i]` + `cObjectIDRangeLength[i]`  
  
 Posun od začátku rozsahu na začátek objekt v tomto případě je následující:  
  
 `oldObjectID` - `oldObjectRangeStart[i]`  
  
 Pro všechny hodnotu `i` , je v následujícím rozsahu:  
  
 0 <= `i` < `cMovedObjectIDRanges`  
  
 můžete vypočítat nové `ObjectID` následujícím způsobem:  
  
 `newObjectID` = `newObjectIDRangeStart[i]` + (`oldObjectID` – `oldObjectIDRangeStart[i]`)  
  
 Žádná z `ObjectID` hodnotu předanou `MovedReferences` jsou platné během zpětného volání sebe, protože kolekce paměti může být uprostřed přesun objektů z původního umístění do nového umístění. Proto profilery neměli zkontrolovat objekty během `MovedReferences` volání. A [icorprofilercallback2::garbagecollectionfinished –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) zpětného volání označuje, že všechny objekty byly přesunuty do nového umístění a provádět kontroly.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICorProfilerCallback – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [MovedReferences2 – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-movedreferences2-method.md)  
 [Rozhraní pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [Profilace](../../../../docs/framework/unmanaged-api/profiling/index.md)
