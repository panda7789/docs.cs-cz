---
title: ICorProfilerInfo4::RequestRevert – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4.RequestRevert
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::RequestRevert
helpviewer_keywords:
- RequestRevert method, ICorProfilerInfo4 interface [.NET Framework profiling]
- ICorProfilerInfo4::RequestRevert method [.NET Framework profiling]
ms.assetid: 70261da5-5933-4e25-9de0-ddf51cba56cc
topic_type:
- apiref
ms.openlocfilehash: c7ced05692e3030bace10dab9a6793a29fac6c26
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74444834"
---
# <a name="icorprofilerinfo4requestrevert-method"></a>ICorProfilerInfo4::RequestRevert – metoda
Reverts all instances of the specified functions to their original versions.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT RequestRevert (  
   [in] ULONG    cFunctions,  
   [in, size_is(cFunctions)]  ModuleID    moduleIds[],  
   [in, size_is(cFunctions)]  mdMethodDef methodIds[],  
   [out, size_is(cFunctions)]  HRESULT status[]);  
```  
  
## <a name="parameters"></a>Parametry  
 `cFunctions`  
 [in] The number of functions to revert.  
  
 `moduleIds`  
 [in] Specifies the `moduleId` portion of the (`module`, `methodDef`) pairs that identify the functions to be reverted.  
  
 `methodIds`  
 [in] Specifies the `methodId` portion of the (`module`, `methodDef`) pairs that identify the functions to be reverted.  
  
 `status`  
 [out] An array of HRESULTs listed in the "Status HRESULTs" section later in this topic. Each HRESULT indicates the success or failure of trying to revert each function specified in the parallel arrays `moduleIds` and `methodIds`.  
  
## <a name="return-value"></a>Návratová hodnota  
 This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.  
  
|HRESULT|Popis|  
|-------------|-----------------|  
|S_OK|An attempt was made to revert all requests; however, the returned status array must be checked to determine which functions were successfully reverted.|  
|CORPROF_E_CALLBACK4_REQUIRED|The profiler must implement the [ICorProfilerCallback4](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) interface for this call to be supported.|  
|CORPROF_E_REJIT_NOT_ENABLED|JIT recompilation has not been enabled. You must enable JIT recompilation during initialization by using the [ICorProfilerInfo::SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) method to set the `COR_PRF_ENABLE_REJIT` flag.|  
|E_INVALIDARG|`cFunctions` is 0, or `moduleIds` or `methodIds` is `NULL`.|  
|E_OUTOFMEMORY|The CLR was unable to complete the request because it ran out of memory.|  
  
## <a name="status-hresults"></a>Status HRESULTS  
  
|Status array HRESULT|Popis|  
|--------------------------|-----------------|  
|S_OK|The corresponding function was successfully reverted.|  
|E_INVALIDARG|The `moduleID` or `methodDef` parameter is `NULL`.|  
|CORPROF_E_DATAINCOMPLETE|The module is not fully loaded yet, or it is in the process of being unloaded.|  
|CORPROF_E_MODULE_IS_DYNAMIC|The specified module was dynamically generated (for example by `Reflection.Emit`). Therefore, it is not supported by this method.|  
|CORPROF_E_ACTIVE_REJIT_REQUEST_NOT_FOUND|The CLR could not revert the specified function, because a corresponding active recompilation request was not found. Either the recompilation was never requested or the function was already reverted.|  
|Ostatní|The operating system returned a failure outside the control of the CLR. For example, if a system call to change the access protection of a page of memory fails, the operating system error will be displayed.|  
  
## <a name="remarks"></a>Poznámky  
 The next time any of the revereted function instances are called, the original versions of the functions will be run. If a function is already running, it will finish executing the version that is running.  
  
## <a name="requirements"></a>Požadavky  
 **Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Header:** CorProf.idl, CorProf.h  
  
 **Library:** CorGuids.lib  
  
 **.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerInfo4 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)
- [Rozhraní pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Profilace](../../../../docs/framework/unmanaged-api/profiling/index.md)
