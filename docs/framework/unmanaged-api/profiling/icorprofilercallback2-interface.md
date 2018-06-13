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
ms.openlocfilehash: c6a218b58ed2ab40505204768f7d6071dea6db5e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33461046"
---
# <a name="icorprofilercallback2-interface"></a>ICorProfilerCallback2 – rozhraní
Poskytuje metody, které jsou používány common language runtime (CLR) profileru kód upozornit, když dojde k události, ke kterým se připojila profileru. `ICorProfilerCallback2` Rozhraní je rozšířením [icorprofilercallback –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) rozhraní. To znamená nabízí nové zpětná volání byla zavedená v rozhraní .NET Framework verze 2.0.  
  
> [!NOTE]
>  Každá metoda implementace musí vracet HRESULT s hodnotou S_OK na úspěch nebo E_FAIL při selhání. V současné době modulu CLR ignoruje HRESULT, který se vrátí po každé zpětné volání s výjimkou [icorprofilercallback::objectreferences –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md).  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[FinalizeableObjectQueued – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-finalizeableobjectqueued-method.md)|Kód profileru upozorní, že objekt s finalizační metody má finalizační metodu vlákno pro spuštění ve frontě jeho `Finalize` metoda.|  
|[GarbageCollectionFinished – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md)|Profileru upozorní, že uvolnění paměti bylo dokončeno a všechny zpětná volání kolekce paměti byl vydán pro ho.|  
|[GarbageCollectionStarted – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionstarted-method.md)|Upozorní profileru kódu, že bylo zahájeno uvolnění paměti.|  
|[HandleCreated – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-handlecreated-method.md)|Upozorní profileru kód vytvořený popisovač kolekce paměti.|  
|[HandleDestroyed – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-handledestroyed-method.md)|Upozorní profileru kódu, byl zničen popisovač kolekce paměti.|  
|[RootReferences2 – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md)|Upozorní profileru o odkazů na kořenový po uvolnění paměti došlo k chybě. Tato metoda je rozšířením [icorprofilercallback::rootreferences –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md) metoda.|  
|[SurvivingReferences – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-survivingreferences-method.md)|Upozorní profileru o odkazy na objekty, které mají zůstal naživu uvolnění paměti.|  
|[ThreadNameChanged – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-threadnamechanged-method.md)|Upozorní profileru kódu, že došlo ke změně názvu vlákna.|  
  
## <a name="remarks"></a>Poznámky  
 Modul CLR volá metodu `ICorProfilerCallback` (nebo `ICorProfilerCallback2`) rozhraní oznámit profileru události, ke kterému měl odběru profileru, když dojde k. Toto je primární zpětného volání rozhraní, pomocí kterého modulu CLR komunikuje s profileru kódu.  
  
 Kód profileru musí implementovat metody `ICorProfilerCallback` rozhraní. Pro rozhraní .NET Framework 2.0 a novější verze, musíte také implementovat profileru `ICorProfilerCallback2` metody. Každá metoda implementace musí vracet HRESULT s hodnotou S_OK na úspěch nebo E_FAIL při selhání. V současné době modulu CLR ignoruje HRESULT, který se vrátí po každé zpětné volání s výjimkou [icorprofilercallback::objectreferences –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md).  
  
 Kód profileru musí registrovat v registru systému Windows, jeho objektu COM, který implementuje `ICorProfilerCallback` a `ICorProfilerCallback2` rozhraní. Kód profileru přihlásí k událostem, pro které chce dostávat oznámení voláním [icorprofilerinfo::seteventmask –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md). To se obvykle provádí v implementaci profileru [icorprofilercallback::Initialize –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md). Profileru je pak může přijímat oznámení z modulu runtime, když událost dojde nebo došlo k jenom v provádění procesu modulu runtime.  
  
> [!NOTE]
>  Profileru zaregistruje jednoho objektu COM. Pokud profileru je cílení na rozhraní .NET Framework verze 1.0 a 1.1, tento objekt COM potřebovat pouze implementují metody `ICorProfilerCallback`. Pokud ho je cílení na rozhraní .NET Framework verze 2.0 a novější, musí implementovat objekt COM také metody `ICorProfilerCallback2`.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Rozhraní pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [ICorProfilerCallback – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [ICorProfilerCallback3 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-interface.md)  
 [ICorProfilerCallback4 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)
