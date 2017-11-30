---
title: "ICorProfilerCallback4::MovedReferences2 – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback4.MovedReferences2
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback4::MovedReferences2
helpviewer_keywords:
- MovedReferences2 method, ICorProfilerCallback4 interface [.NET Framework profiling]
- ICorProfilerCallback4::MovedReferences2 method [.NET Framework profiling]
ms.assetid: d17a065b-5bc6-4817-b3e1-1e413fcb33a8
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 8137d944081475095509150cce84a611b7030eb2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilercallback4movedreferences2-method"></a>ICorProfilerCallback4::MovedReferences2 – metoda
Volá se pro sestavy nové rozložení objektů v haldě v důsledku komprimaci uvolnění paměti. Tato metoda je volána, pokud má implementovaný profileru [icorprofilercallback4 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) rozhraní. Nahradí tato zpětného volání [icorprofilercallback::movedreferences –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-movedreferences-method.md) metoda, protože ho může hlásit větší rozsah objektů, jejichž délky překročit, co může být vyjádřený v typu ULONG.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT MovedReferences2(  
    [in]  ULONG  cMovedObjectIDRanges,  
    [in, size_is(cMovedObjectIDRanges)] ObjectID oldObjectIDRangeStart[] ,  
    [in, size_is(cMovedObjectIDRanges)] ObjectID newObjectIDRangeStart[] ,  
    [in, size_is(cMovedObjectIDRanges)] SIZE_T    cObjectIDRangeLength[] );  
```  
  
#### <a name="parameters"></a>Parametry  
 `cMovedObjectIDRanges`  
 [v] Počet bloků souvislý objektů, které přesunout v důsledku komprimaci uvolnění paměti. To znamená, hodnota `cMovedObjectIDRanges` je celková velikost `oldObjectIDRangeStart`, `newObjectIDRangeStart`, a `cObjectIDRangeLength` pole.  
  
 Následující tři argumenty `MovedReferences2` jsou paralelní pole. Jinými slovy `oldObjectIDRangeStart[i]`, `newObjectIDRangeStart[i]`, a `cObjectIDRangeLength[i]` všechny jeden blok souvislý objektů, které se týkají.  
  
 `oldObjectIDRangeStart`  
 [v] Pole `ObjectID` hodnoty, z nichž každý je starý (předběžné uvolňování paměti) počáteční adresa blok souvislý, live objekty v paměti.  
  
 `newObjectIDRangeStart`  
 [v] Pole `ObjectID` hodnoty, z nichž každý je nové počáteční adresa (po uvolnění paměti) blok souvislý, live objekty v paměti.  
  
 `cObjectIDRangeLength`  
 [v] Pole celých čísel, z nichž každý je velikost bloku souvislý objektů v paměti.  
  
 Velikost je zadán pro každý blok, který se odkazuje v `oldObjectIDRangeStart` a `newObjectIDRangeStart` pole.  
  
## <a name="remarks"></a>Poznámky  
 Komprimaci uvolňování paměti získá paměť obsazená neaktivní objekty a zkomprimuje uvolní místo. V důsledku toho může přesunout živé objekty v rámci haldy, a `ObjectID` mohou změnit hodnoty distribuovat předchozí oznámení.  
  
 Předpokládáme, že existující `ObjectID` hodnotu (`oldObjectID`) v rozmezí následující:  
  
 `oldObjectIDRangeStart[i]` <= `oldObjectID` < `oldObjectIDRangeStart[i]` + `cObjectIDRangeLength[i]`  
  
 Posun od začátku rozsahu na začátek objekt v tomto případě je následující:  
  
 `oldObjectID` - `oldObjectRangeStart[i]`  
  
 Pro všechny hodnotu `i` , je v následujícím rozsahu:  
  
 0 <= `i` < `cMovedObjectIDRanges`  
  
 můžete vypočítat nové `ObjectID` následujícím způsobem:  
  
 `newObjectID` = `newObjectIDRangeStart[i]` + (`oldObjectID` – `oldObjectIDRangeStart[i]`)  
  
 Žádná z `ObjectID` hodnotu předanou `MovedReferences2` jsou platné během zpětného volání sebe, protože systém uvolňování paměti může být uprostřed přesun objektů z původního umístění do nového umístění. Proto profilery neměli zkontrolovat objekty během `MovedReferences2` volání. A [icorprofilercallback2::garbagecollectionfinished –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) zpětného volání označuje, že všechny objekty byly přesunuty do nového umístění a provádět kontroly.  
  
 Pokud profileru implementuje i [icorprofilercallback –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) a [icorprofilercallback4 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) rozhraní, `MovedReferences2` metoda je volána před provedením [icorprofilercallback –:: Movedreferences –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-movedreferences-method.md) metoda, ale jenom Pokud `MovedReferences2` metoda vrátí úspěšně. Profilery může vrátit HRESULT označující selhání z `MovedReferences2` metoda, aby se zabránilo volání druhé metody.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Icorprofilercallback – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [Movedreferences – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-movedreferences-method.md)  
 [Icorprofilercallback4 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)  
 [Rozhraní pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [Profilace](../../../../docs/framework/unmanaged-api/profiling/index.md)
