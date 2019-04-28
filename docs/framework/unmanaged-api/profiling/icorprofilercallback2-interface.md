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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 83c72704ccb01baf68a3cacb6252367e07909fa8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61638419"
---
# <a name="icorprofilercallback2-interface"></a>ICorProfilerCallback2 – rozhraní
Poskytuje metody, které se používají modulem common language runtime (CLR) pro oznámení profileru kód, pokud dojde k událostem, ke kterým se připojila profileru. `ICorProfilerCallback2` Rozhraní je rozšířením [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) rozhraní. To znamená, že poskytuje nové zpětná volání zavedena v rozhraní .NET Framework verze 2.0.  
  
> [!NOTE]
>  Každá implementace metoda musí vracet HRESULT s hodnotou S_OK na úspěch nebo E_FAIL při selhání. V současné době CLR ignoruje hodnota HRESULT, který je vrácený každou zpětného volání s výjimkou [ICorProfilerCallback::ObjectReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md).  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[FinalizeableObjectQueued – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-finalizeableobjectqueued-method.md)|Upozornění profileru kódu, že objekt s finalizační metody se zařadila do vlákna finalizační metody pro provádění jeho `Finalize` metoda.|  
|[GarbageCollectionFinished – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md)|Profiler upozorní, že dokončení procesu uvolnění paměti a všechny zpětná volání kolekce uvolnění paměti byly vydány pro něj.|  
|[GarbageCollectionStarted – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionstarted-method.md)|Upozornění profileru kódu, uvolňování paměti byla spuštěna.|  
|[HandleCreated – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-handlecreated-method.md)|Upozornění profileru kódu, není vytvořen popisovač kolekce uvolnění paměti.|  
|[HandleDestroyed – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-handledestroyed-method.md)|Upozornění profileru kód zlikvidování popisovač kolekce uvolnění paměti.|  
|[RootReferences2 – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md)|Oznámí profileru odkazy na kořenové po uvolňování paměti došlo k chybě. Tato metoda je rozšířením [ICorProfilerCallback::RootReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md) metody.|  
|[SurvivingReferences – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-survivingreferences-method.md)|Upozornění profileru o odkazy na objekty, které mají zůstat naživu při uvolňování paměti.|  
|[ThreadNameChanged – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-threadnamechanged-method.md)|Upozornění profileru kód, název vlákna se změnila.|  
  
## <a name="remarks"></a>Poznámky  
 CLR volá metodu v `ICorProfilerCallback` (nebo `ICorProfilerCallback2`) rozhraní pro oznámení profileru po události, ke kterému měl profiler odběru, vyvolá. Toto je primární zpětného volání rozhraní, pomocí kterého CLR komunikuje s profileru kód.  
  
 Profiler kódu musí implementovat metody `ICorProfilerCallback` rozhraní. Pro rozhraní .NET Framework 2.0 a novější verze, musí také implementovat profiler `ICorProfilerCallback2` metody. Každá implementace metoda musí vracet HRESULT s hodnotou S_OK na úspěch nebo E_FAIL při selhání. V současné době CLR ignoruje hodnota HRESULT, který je vrácený každou zpětného volání s výjimkou [ICorProfilerCallback::ObjectReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md).  
  
 Profiler kódu musí registrovat v registru Microsoft Windows, jeho objekt modelu COM, který implementuje `ICorProfilerCallback` a `ICorProfilerCallback2` rozhraní. Profiler kódu přihlásí se k odběru událostí, pro které chce přijmout oznámení voláním [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md). To se obvykle provádí v implementaci profileru [ICorProfilerCallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md). Profiler je pak moci přijímat oznámení z modulu runtime při události dojde nebo došlo k právě v spuštěného procesu modulu runtime.  
  
> [!NOTE]
>  Profiler zaregistruje jeden objekt modelu COM. Pokud profiler je cílen na verzi rozhraní .NET Framework verze 1.0 nebo 1.1, tento objekt modelu COM musí implementovat pouze metody `ICorProfilerCallback`. Pokud je cílen na verzi rozhraní .NET Framework verze 2.0 a novější, musí implementovat objekt modelu COM také metody `ICorProfilerCallback2`.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [ICorProfilerCallback – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [ICorProfilerCallback3 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-interface.md)
- [ICorProfilerCallback4 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)
