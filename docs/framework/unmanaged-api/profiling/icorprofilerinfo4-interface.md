---
title: ICorProfilerInfo4 – rozhraní
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4
helpviewer_keywords:
- ICorProfilerInfo4 interface [.NET Framework profiling]
ms.assetid: 80a5308e-c22f-4201-ba89-31cc8562515b
topic_type:
- apiref
ms.openlocfilehash: cbd7c0d8fff55766a98e727ce22c77dd5214611b
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448002"
---
# <a name="icorprofilerinfo4-interface"></a>ICorProfilerInfo4 – rozhraní
Provides methods that code profilers use to communicate with the common language runtime (CLR) to control event monitoring and request information. . The `ICorProfilerInfo4` interface is an extension of the other `ICorProfilerInfo` interfaces. It provides new methods to support just-in-time (JIT) recompilation, added in the .NET Framework 4.5.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[EnumJITedFunctions2 – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-enumjitedfunctions2-method.md)|Returns an enumerator for all functions that were previously JIT-compiled and JIT-recompiled.|  
|[EnumThreads – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-enumthreads-method.md)|Gets an enumerator that provides methods to sequentially iterate through the collection of all managed threads in the profiled process.|  
|[GetCodeInfo3 – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getcodeinfo3-method.md)|Gets the extents of native code associated with the JIT-recompiled version of the specified function.|  
|[GetFunctionFromIP2 – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getfunctionfromip2-method.md)|Maps a managed code instruction pointer to the JIT-recompiled version of a specified function.|  
|[GetILToNativeMapping2 – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getiltonativemapping2-method.md)|Gets a map from Microsoft intermediate language (MSIL) offsets to native offsets for the code contained in the JIT-recompiled version of the specified function .|  
|[GetObjectSize2 – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getobjectsize2-method.md)|Returns the size of a specified object.|  
|[GetReJITIDs – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getrejitids-method.md)|Returns an array of IDs that identify all JIT-recompiled versions of the specified function that are still allocated.|  
|[InitializeCurrentThread – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-initializecurrentthread-method.md)|Initializes the current thread in advance of subsequent profiler API calls on the same thread, so that deadlock can be avoided.|  
|[RequestReJIT – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-requestrejit-method.md)|Requests a JIT recompilation of all instances of the specified functions.|  
|[RequestRevert – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-requestrevert-method.md)|Reverts all instances of the specified functions to their original versions.|  
  
## <a name="remarks"></a>Poznámky  
 The CLR implements the methods of the `ICorProfilerInfo4` interface by using the free-threaded model. Each method returns an HRESULT to indicate success or failure. For a list of possible return codes, see the CorError.h file.  
  
## <a name="requirements"></a>Požadavky  
 **Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Header:** CorProf.idl, CorProf.h  
  
 **Library:** CorGuids.lib  
  
 **.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [ICorProfilerInfo – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
