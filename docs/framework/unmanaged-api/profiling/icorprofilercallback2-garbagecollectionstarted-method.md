---
title: ICorProfilerCallback2::GarbageCollectionStarted – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback2.GarbageCollectionStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback2::GarbageCollectionStarted
helpviewer_keywords:
- GarbageCollectionStarted method [.NET Framework profiling]
- ICorProfilerCallback2::GarbageCollectionStarted method [.NET Framework profiling]
ms.assetid: 44eef087-f21f-4fe2-b481-f8a0ee022e7d
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d3c95bbf946cd208a1cc01463aaae76e3842c8fa
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57471261"
---
# <a name="icorprofilercallback2garbagecollectionstarted-method"></a>ICorProfilerCallback2::GarbageCollectionStarted – metoda
Upozornění profileru kódu, uvolňování paměti byla spuštěna.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GarbageCollectionStarted(  
    [in] int cGenerations,  
    [in, size_is(cGenerations), length_is(cGenerations)] BOOL generationCollected[],  
    [in] COR_PRF_GC_REASON reason);  
```  
  
## <a name="parameters"></a>Parametry  
 `cGenerations`  
 [in] Celkový počet položek v `generationCollected` pole.  
  
 `generationCollected`  
 [in] Pole logické hodnoty, které jsou `true` jestli ke generaci, kterou odpovídá index pole je shromážděných v této kolekci uvolňování paměti; v opačném případě `false`.  
  
 Pole je indexované podle hodnoty [cor_prf_gc_generation –](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-enumeration.md) výčet, který označuje jeho generaci.  
  
 `reason`  
 [in] Hodnota [cor_prf_gc_reason –](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-reason-enumeration.md) bylo získáno výčet, který označuje důvod kolekce uvolnění paměti.  
  
## <a name="remarks"></a>Poznámky  
 Všechny zpětná volání, které se týkají této kolekce uvolnění paměti dojde mezi `GarbageCollectionStarted` zpětného volání a odpovídající [ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) zpětného volání. Tato zpětná volání nemusí dojít k ve stejném vlákně.  
  
 Je bezpečný pro profiler pro kontrolu objektů v jejich původním umístění během `GarbageCollectionStarted` zpětného volání. Uvolňování paměti se začne pohybujících se objektů po návrat z `GarbageCollectionStarted`. Po profiler vrátil z této zpětné volání, profiler zvažte všechna ID objektu není platný až do obdržení `ICorProfilerCallback2::GarbageCollectionFinished` zpětného volání.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:
- [ICorProfilerCallback – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [ICorProfilerCallback2 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
