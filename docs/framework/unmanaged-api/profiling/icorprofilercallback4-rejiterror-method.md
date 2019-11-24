---
title: ICorProfilerCallback4::ReJITError – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback4.ReJITError
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback4::ReJITError
helpviewer_keywords:
- ReJITError method, ICorProfilerCallback4 interface [.NET Framework profiling]
- ICorProfilerCallback4::ReJITError method [.NET Framework profiling]
ms.assetid: d7888aa9-dfaa-420f-9f99-e06ab35ca482
topic_type:
- apiref
ms.openlocfilehash: 6ea9dee6e83870d1f2e0fdccffa53f16e6f18dba
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74430104"
---
# <a name="icorprofilercallback4rejiterror-method"></a>ICorProfilerCallback4::ReJITError – metoda
Notifies the profiler that the just-in-time (JIT) compiler encountered an error in the recompilation process.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT ReJITError(  
    [in] ModuleID    moduleId,  
    [in] mdMethodDef methodId,  
    [in] FunctionID  functionId,  
    [in] HRESULT     hrStatus);  
```  
  
## <a name="parameters"></a>Parametry  
 `moduleID`  
 [in] The `ModuleID` in which the failed recompilation attempt was made.  
  
 `methodId`  
 [in] The `MethodDef` of the method on which the failed recompilation attempt was made.  
  
 `functionId`  
 [in] The function instance that is being recompiled or marked for recompilation. This value may be `NULL` if the failure occurred on a per-method basis instead of a per-instantiation basis (for example, if the profiler specified an invalid metadata token for the method to be recompiled).  
  
 `hrStatus`  
 [in] An HRESULT that indicates the nature of the failure. See the Status HRESULTS section for a list of values.  
  
## <a name="return-value"></a>Návratová hodnota  
 Return values from this callback are ignored.  
  
## <a name="status-hresults"></a>Status HRESULTS  
  
|Status array HRESULT|Popis|  
|--------------------------|-----------------|  
|E_INVALIDARG|The `moduleID` or `methodDef` token is `NULL`.|  
|CORPROF_E_DATAINCOMPLETE|The module is not fully loaded yet, or it is in the process of being unloaded.|  
|CORPROF_E_MODULE_IS_DYNAMIC|The specified module was dynamically generated (for example, by `Reflection.Emit`), and is thus not supported by this method.|  
|CORPROF_E_FUNCTION_IS_COLLECTIBLE|The method is instantiated into a collectible assembly, and is therefore not able to be recompiled. Note that types and functions defined in a non-reflection context (for example, `List<MyCollectibleStruct>`) can be instantiated into a collectible assembly.|  
|E_OUTOFMEMORY|The CLR ran out of memory while trying to mark the specified method for JIT recompilation.|  
|Ostatní|The operating system returned a failure outside the control of the CLR. For example, if a system call to change the access protection of a page of memory fails, the operating system error is displayed.|  
  
## <a name="requirements"></a>Požadavky  
 **Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Header:** CorProf.idl, CorProf.h  
  
 **Library:** CorGuids.lib  
  
 **.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerCallback – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [ICorProfilerCallback4 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)
