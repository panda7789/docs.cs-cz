---
title: ICorProfilerFunctionEnum – rozhraní
ms.date: 03/30/2017
api_name:
- ICorProfilerFunctionEnum
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerFunctionEnum
helpviewer_keywords:
- ICorProfilerFunctionEnum interface [.NET Framework profiling]
ms.assetid: 0a1d4a38-cd0b-4231-91df-13646218ae72
topic_type:
- apiref
ms.openlocfilehash: 17f7243096b7ac18e456f8f31196055492015346
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447805"
---
# <a name="icorprofilerfunctionenum-interface"></a>ICorProfilerFunctionEnum – rozhraní
Provides methods to sequentially iterate through a collection of functions in the common language runtime.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[Clone – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-clone-method.md)|Gets an interface pointer to a copy of this `ICorProfilerFunctionEnum` interface.|  
|[GetCount – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-getcount-method.md)|Gets the number of functions that were loaded by the application or forcibly loaded by the profiler.|  
|[Next – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-next-method.md)|Gets the specified number of contiguous functions from a sequential collection of functions, starting at the enumerator's current position in the sequence.|  
|[Reset – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-reset-method.md)|Moves the enumerator's cursor to the starting position of the sequence.|  
|[Skip – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-skip-method.md)|Advances the enumerator's cursor from its current position so that the specified number of elements are skipped.|  
  
## <a name="remarks"></a>Poznámky  
 The `ICorProfilerFunctionEnum` interface is an enumerator. It allows the receiver of an array to pull elements from the sender at a rate that is appropriate for the receiver. In other words, the receiver is able to explicitly control the flow of array elements, thereby avoiding the problems associated with passing large arrays as method parameters.  
  
 `ICorProfilerFunctionEnum` enumerates over functions that have already been JIT-compiled, but does not include functions that are loaded from native images generated with Ngen.exe.  
  
## <a name="requirements"></a>Požadavky  
 **Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Header:** CorProf.idl, CorProf.h  
  
 **Library:** CorGuids.lib  
  
 **.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerInfo – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [Rozhraní pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [EnumJITedFunctions – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enumjitedfunctions-method.md)
