---
title: ICorProfilerCallback2 – rozhraní
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback2
helpviewer_keywords:
- ICorProfilerCallback2 interface [.NET Framework profiling]
ms.assetid: 4a261dba-450d-4f1f-8d98-865b58bfc992
topic_type:
- apiref
ms.openlocfilehash: 3b0e60602d2f36552c3e0e85ec51205b4128486b
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84499763"
---
# <a name="icorprofilercallback2-interface"></a>ICorProfilerCallback2 – rozhraní
Poskytuje metody, které jsou používány modulem CLR (Common Language Runtime) k oznamování profileru kódu, když dojde k odběru událostí, ke kterým má Profiler odběr. `ICorProfilerCallback2`Rozhraní je rozšířením rozhraní [ICorProfilerCallback](icorprofilercallback-interface.md) . To znamená, že poskytuje nová zpětná volání, která jsou představena ve verzi .NET Framework 2,0.  
  
> [!NOTE]
> Každá implementace metody musí vracet hodnotu HRESULT s hodnotou S_OK při úspěchu nebo E_FAIL při selhání. V současné době CLR ignoruje hodnotu HRESULT, kterou vrátí každé zpětné volání s výjimkou [ICorProfilerCallback:: objectReferences –](icorprofilercallback-objectreferences-method.md).  
  
## <a name="methods"></a>Metody  
  
|Metoda|Description|  
|------------|-----------------|  
|[FinalizeableObjectQueued – metoda](icorprofilercallback2-finalizeableobjectqueued-method.md)|Upozorní profiler kódu, že objekt s finalizační metodou byl zařazen do finalizačního vlákna pro provedení své `Finalize` metody.|  
|[GarbageCollectionFinished – metoda](icorprofilercallback2-garbagecollectionfinished-method.md)|Upozorní profileru, že se dokončilo uvolňování paměti a že se pro něj vystavila všechna zpětná volání uvolňování paměti.|  
|[GarbageCollectionStarted – metoda](icorprofilercallback2-garbagecollectionstarted-method.md)|Upozorní profiler kódu, že bylo zahájeno uvolňování paměti.|  
|[HandleCreated – metoda](icorprofilercallback2-handlecreated-method.md)|Upozorní profiler kódu, že byl vytvořen popisovač uvolňování paměti.|  
|[HandleDestroyed – metoda](icorprofilercallback2-handledestroyed-method.md)|Upozorní profiler kódu, že byl zničen popisovač uvolňování paměti.|  
|[RootReferences2 – metoda](icorprofilercallback2-rootreferences2-method.md)|Oznamuje Profiler o kořenových odkazech poté, co došlo k uvolnění paměti. Tato metoda je rozšířením metody [ICorProfilerCallback:: RootReferences –](icorprofilercallback-rootreferences-method.md) .|  
|[SurvivingReferences – metoda](icorprofilercallback2-survivingreferences-method.md)|Upozorní profiler na odkazy na objekty, které předržely uvolňování paměti.|  
|[ThreadNameChanged – metoda](icorprofilercallback2-threadnamechanged-method.md)|Upozorní profiler kódu, že se změnil název vlákna.|  
  
## <a name="remarks"></a>Poznámky  
 CLR volá metodu v `ICorProfilerCallback` rozhraní (nebo `ICorProfilerCallback2` ) k oznámení profileru, když dojde k odběru události, ke které se Profiler přihlásil. Toto je primární rozhraní zpětného volání, přes které CLR komunikuje s profilerem kódu.  
  
 Profiler kódu musí implementovat metody `ICorProfilerCallback` rozhraní. Pro .NET Framework 2,0 a novější verze musí Profiler také implementovat `ICorProfilerCallback2` metody. Každá implementace metody musí vracet hodnotu HRESULT s hodnotou S_OK při úspěchu nebo E_FAIL při selhání. V současné době CLR ignoruje hodnotu HRESULT, kterou vrátí každé zpětné volání s výjimkou [ICorProfilerCallback:: objectReferences –](icorprofilercallback-objectreferences-method.md).  
  
 Profiler kódu se musí zaregistrovat v registru Microsoft Windows, jeho objekt COM, který implementuje `ICorProfilerCallback` rozhraní a `ICorProfilerCallback2` . Profiler kódu se přihlašuje k odběru událostí, ke kterým chce dostávat oznámení voláním [ICorProfilerInfo:: SetEventMask](icorprofilerinfo-seteventmask-method.md). To se obvykle provádí v implementaci [ICorProfilerCallback:: Initialize](icorprofilercallback-initialize-method.md)v profileru. Profiler je pak schopný přijímat oznámení z modulu runtime, když dojde k události, která se chystá, nebo k ní došlo pouze v průběhu provádění procesu modulu runtime.  
  
> [!NOTE]
> Profiler registruje jeden objekt COM. Pokud je profiler cílen .NET Framework verze 1,0 nebo 1,1, musí objekt COM implementovat pouze metody `ICorProfilerCallback` . Pokud cílí na .NET Framework verze 2,0 a novější, musí objekt COM také implementovat metody `ICorProfilerCallback2` .  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro profilaci](profiling-interfaces.md)
- [ICorProfilerCallback – rozhraní](icorprofilercallback-interface.md)
- [ICorProfilerCallback3 – rozhraní](icorprofilercallback3-interface.md)
- [ICorProfilerCallback4 – rozhraní](icorprofilercallback4-interface.md)
