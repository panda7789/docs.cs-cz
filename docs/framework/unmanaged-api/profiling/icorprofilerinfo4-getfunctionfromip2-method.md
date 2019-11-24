---
title: ICorProfilerInfo4::GetFunctionFromIP2 – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4.GetFunctionFromIP2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::GetFunctionFromIP2
helpviewer_keywords:
- ICorProfilerInfo4::GetFunctionFromIP2 method [.NET Framework profiling]
- GetFunctionFromIP2 method, ICorProfilerInfo4 interface [.NET Framework profiling]
ms.assetid: 46ff70f4-13e9-40a0-802a-0a40abcfc6a0
topic_type:
- apiref
ms.openlocfilehash: 5153a25ef87d9c06bb46b74945c8eb68eb041682
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74443140"
---
# <a name="icorprofilerinfo4getfunctionfromip2-method"></a>ICorProfilerInfo4::GetFunctionFromIP2 – metoda
Maps a managed code instruction pointer to the JIT-recompiled version of a function.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetFunctionFromIP2(  
    [in]  LPCBYTE    ip,  
    [out] FunctionID *pFunctionId,  
    [out] ReJITID *pReJitId);  
```  
  
## <a name="parameters"></a>Parametry  
 `ip`  
 [in] The instruction pointer in managed code.  
  
 `pFunctionId`  
 [out] The function ID.  
  
 `pReJitId`  
 [out] The identity of the JIT-recompiled version of the function.  
  
## <a name="remarks"></a>Poznámky  
 `GetFunctionFromIP2` is similar to `GetFunctionFromIP`, except that it gets the JIT-recompiled ID instead of the function ID of the function that contains the specified IP address.  
  
> [!NOTE]
> `GetFunctionFromIP2` can trigger a garbage collection, whereas `GetFunctionFromIP` will not.  For more information, see [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT](../../../../docs/framework/unmanaged-api/profiling/corprof-e-unsupported-call-sequence-hresult.md).  
  
## <a name="requirements"></a>Požadavky  
 **Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Header:** CorProf.idl, CorProf.h  
  
 **Library:** CorGuids.lib  
  
 **.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerInfo – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
