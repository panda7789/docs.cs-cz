---
title: ICorProfilerInfo3::GetFunctionTailcall3Info – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.GetFunctionTailcall3Info Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::GetFunctionTailcall3Info
helpviewer_keywords:
- ICorProfilerInfo3::GetFunctionTailcall3Info method [.NET Framework profiling]
- GetFunctionTailcall3Info method [.NET Framework profiling]
ms.assetid: afdb5ac9-5bf5-4b91-b7cb-f81db23d7da3
topic_type:
- apiref
ms.openlocfilehash: e7a25fce945504cff0d07f499ae4bb79378e9f3a
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449701"
---
# <a name="icorprofilerinfo3getfunctiontailcall3info-method"></a>ICorProfilerInfo3::GetFunctionTailcall3Info – metoda
Provides the stack frame of the function that is being reported to the profiler by the [FunctionTailcall3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md) function. This method can be called only during the `FunctionTailcall3WithInfo` callback.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetFunctionTailcall3Info(   
            [in]  FunctionID functionId,   
            [in]  COR_PRF_ELT_INFO eltInfo,  
            [out] COR_PRF_FRAME_INFO *pFrameInfo);  
```  
  
## <a name="parameters"></a>Parametry  
 `functionId`  
 [in] The `FunctionID` of the function that is returning.  
  
 `eltInfo`  
 [in] An opaque handle that represents information about a given stack frame. The profiler should provide the same `eltInfo` that was given to the profiler by the `FunctionTailcall3WithInfo` function.  
  
 `pFrameInfo`  
 [out] An opaque handle that represents generics information about a given stack frame. This handle is valid only during the `FunctionTailcall3WithInfo` callback in which the profiler called the `GetFunctionTailcall3Info` method.  
  
## <a name="remarks"></a>Poznámky  
  
## <a name="requirements"></a>Požadavky  
 **Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Header:** CorProf.idl, CorProf.h  
  
 **Library:** CorGuids.lib  
  
 **.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [FunctionEnter3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)
- [FunctionLeave3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)
- [FunctionTailcall3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)
- [ICorProfilerInfo3 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [Rozhraní pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Profilace](../../../../docs/framework/unmanaged-api/profiling/index.md)
