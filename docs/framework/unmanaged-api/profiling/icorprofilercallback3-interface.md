---
title: ICorProfilerCallback3 – rozhraní
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback3
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback3
helpviewer_keywords:
- ICorProfilerCallback3 interface [.NET Framework profiling]
ms.assetid: be83af41-3dec-4c77-8529-9dd6b8042af6
topic_type:
- apiref
ms.openlocfilehash: 25d674a143019ac5d724e36f03f36c79602b1e11
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74439510"
---
# <a name="icorprofilercallback3-interface"></a>ICorProfilerCallback3 – rozhraní
Provides callback methods that the common language runtime (CLR) uses to communicate attach and detach state information to the profiler.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[InitializeForAttach – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-initializeforattach-method.md)|Called by the CLR to give the profiler an opportunity to initialize its state after an attach operation.|  
|[ProfilerAttachComplete – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-profilerattachcomplete-method.md)|Called by the CLR to indicate that the profiler can now call the catch-up methods.|  
|[ProfilerDetachSucceeded – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-profilerdetachsucceeded-method.md)|Notifies the profiler that the common language runtime (CLR) is about to unload the profiler DLL.|  
  
## <a name="remarks"></a>Poznámky  
  
## <a name="requirements"></a>Požadavky  
 **Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Header:** CorProf.idl, CorProf.h  
  
 **Library:** CorGuids.lib  
  
 **.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [ICorProfilerInfo – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [ICorProfilerCallback2 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
- [ICorProfilerCallback4 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)
