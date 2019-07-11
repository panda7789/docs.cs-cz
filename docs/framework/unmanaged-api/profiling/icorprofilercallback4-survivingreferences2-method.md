---
title: ICorProfilerCallback4::SurvivingReferences2 – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback4.SurvivingReferences2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback4::SurvivingReferences2
helpviewer_keywords:
- ICorProfilerCallback4::SurvivingReferences2 method [.NET Framework profiling]
- SurvivingReferences2 method, ICorProfilerCallback4 interface [.NET Framework profiling]
ms.assetid: 02b51888-5d89-4e50-a915-45b7e329aad9
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: beb260030914de211d227342e497daa3db287c9e
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67758071"
---
# <a name="icorprofilercallback4survivingreferences2-method"></a>ICorProfilerCallback4::SurvivingReferences2 – metoda
Ohlásí rozložení objektů v haldě v důsledku uvolnění nekompaktním. Tato metoda je volána, pokud profiler implementoval [icorprofilercallback4 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) rozhraní. Nahradí tato zpětné volání [ICorProfilerCallback2::SurvivingReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-survivingreferences-method.md) metody, protože ho může hlásit větší rozsah objektů, jejichž délky překročit, co lze vyjádřit v typu ULONG.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SurvivingReferences2(  
    [in] ULONG  cSurvivingObjectIDRanges,  
    [in, size_is(cSurvivingObjectIDRanges)] ObjectID  
                objectIDRangeStart[] ,  
    [in, size_is(cSurvivingObjectIDRanges)] SIZE_T  
                cObjectIDRangeLength[] );  
```  
  
## <a name="parameters"></a>Parametry  
 `cSurvivingObjectIDRanges`  
 [in] Počet bloků souvislých objektů, které zůstat naživu při uvolňování nekompaktním v důsledku. To znamená, že hodnota `cSurvivingObjectIDRanges` je velikost `objectIDRangeStart` a `cObjectIDRangeLength` pole, které úložiště `ObjectID` a délku, pro každý blok objektů.  
  
 Následující dva argumenty `SurvivingReferences2` jsou paralelní pole. Jinými slovy `objectIDRangeStart` a `cObjectIDRangeLength` týkají stejný blok souvislé objektů.  
  
 `objectIDRangeStart`  
 [in] Pole `ObjectID` hodnot, z nichž každý je počáteční adresa blok souvislé, živé objekty v paměti.  
  
 `cObjectIDRangeLength`  
 [in] Pole celých čísel, z nichž každý je velikost bloku zbývající souvislých objektů v paměti.  
  
 Zadat velikost pro každý blok, na který odkazuje `objectIDRangeStart` pole.  
  
## <a name="remarks"></a>Poznámky  
 Prvky `objectIDRangeStart` a `cObjectIDRangeLength` pole by měl být interpretován takto k určení, zda objekt zůstat naživu kolekce uvolnění paměti. Předpokládejme, že `ObjectID` hodnotu (`ObjectID`) najdete v následujícím rozsahu:  
  
 `ObjectIDRangeStart[i]` <= `ObjectID` < `ObjectIDRangeStart[i]` + `cObjectIDRangeLength[i]`  
  
 Jakoukoli hodnotu z `i` , který je v následujícím rozsahu, objekt má zůstat naživu při uvolňování paměti kolekce:  
  
 0 <= `i` < `cSurvivingObjectIDRanges`  
  
 Uvolnění nekompaktním uvolňuje paměť obsazenou neživými "" objekty, ale ne compact toto uvolněné místo. V důsledku toho paměti se vrátí do haldy, ale žádné objekty "živé" přesunou.  
  
 Common language runtime (CLR) zavolá `SurvivingReferences2` pro nekompaktním kolekce uvolnění paměti. Pro uvolnění komprimaci [movedreferences2 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-movedreferences2-method.md) je použita místo ní. Jeden uvolňování paměti může být komprimaci pro jeden generování a nekompaktním dalších. Pro uvolnění paměti na žádné konkrétní generování, profiler obdrží, buď `SurvivingReferences2` zpětného volání nebo [movedreferences2 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-movedreferences2-method.md) zpětné volání, ale ne obojí.  
  
 Více `SurvivingReferences2` zpětná volání může přijmout během konkrétní uvolňování kvůli omezené interní ukládání do vyrovnávací paměti, více zpětných volání během uvolnění paměti serveru a z jiných důvodů. V případě více zpětných volání během uvolňování paměti informace jsou kumulativní; všechny odkazy, které jsou hlášeny v libovolném `SurvivingReferences2` zpětného volání byly zachovány při uvolnění paměti.  
  
 Pokud profiler implementuje oba [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) a [icorprofilercallback4 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) rozhraní, `SurvivingReferences2` metoda je volána před provedením [ICorProfilerCallback2:: Survivingreferences –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-survivingreferences-method.md) metody, ale pouze v případě `SurvivingReferences2` úspěšně vrátí. Profilovací programy mohou vrátit HRESULT označující selhání z `SurvivingReferences2` metoda Vyhněte se volání druhá metoda.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerCallback – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [ICorProfilerCallback2 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
- [ICorProfilerCallback4 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)
