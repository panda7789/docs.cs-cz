---
title: ICorProfilerInfo3::SetEnterLeaveFunctionHooks3 – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.SetEnterLeaveFunctionHooks3 Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::SetEnterLeaveFunctionHooks3
helpviewer_keywords:
- SetEnterLeaveFunctionHooks3 method [.NET Framework profiling]
- ICorProfilerInfo3::SetEnterLeaveFunctionHooks3 method [.NET Framework profiling]
ms.assetid: f0621465-b84f-40ab-a4e5-56a7abc776a7
topic_type:
- apiref
ms.openlocfilehash: da56018216a7c6cebdc0ec222d1cb1be3633ecc9
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449606"
---
# <a name="icorprofilerinfo3setenterleavefunctionhooks3-method"></a>ICorProfilerInfo3::SetEnterLeaveFunctionHooks3 – metoda
Určuje funkce implementované profilerem, které budou volány ve funkcích [FunctionEnter3 –](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md), [FunctionLeave3 –](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md)a [FunctionTailcall3 –](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetEnterLeaveFunctionHooks3(  
            [in] FunctionEnter3    *pFuncEnter3,  
            [in] FunctionLeave3    *pFuncLeave3,  
            [in] FunctionTailcall3 *pFuncTailcall3);  
```  
  
## <a name="parameters"></a>Parametry  
 `pFuncEnter3`  
 pro Ukazatel na implementaci, která se má použít jako zpětné volání `FunctionEnter3`.  
  
 `pFuncLeave3`  
 pro Ukazatel na implementaci, která se má použít jako zpětné volání `FunctionLeave3`.  
  
 `pFuncTailcall3`  
 pro Ukazatel na implementaci, která se má použít jako zpětné volání `FunctionTailcall3`.  
  
## <a name="remarks"></a>Poznámky  
 [FunctionEnter3 –](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md), [FunctionLeave3 –](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md)a [FunctionTailcall3 –](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md) háky neposkytují kontrolu rámce zásobníku a argumentů. Pro přístup k těmto informacím musí být nastavené příznaky `COR_PRF_ENABLE_FUNCTION_ARGS`, `COR_PRF_ENABLE_FUNCTION_RETVAL`a/nebo `COR_PRF_ENABLE_FRAME_INFO`. Profiler může použít metodu [ICorProfilerInfo:: SetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md) pro nastavení příznaků událostí a pak použít metodu [ICorProfilerInfo3:: SetEnterLeaveFunctionHooks3WithInfo –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) k registraci implementace této funkce.  
  
 V jednom okamžiku může být aktivní jenom jedna sada zpětných volání a nejnovější verze má přednost. Proto pokud profiler volá [metodu SetEnterLeaveFunctionHooks2 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md) i metodu `SetEnterLeaveFunctionHooks3`, `SetEnterLeaveFunctionHooks3` se používá.  
  
 Metodu `SetEnterLeaveFunctionHooks3` lze volat pouze z zpětného volání [ICorProfilerCallback:: Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) .  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Setenterleavefunctionhooks3withinfo –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)
- [Functionenter3 –](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md)
- [Functionleave3 –](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md)
- [Functiontailcall3 –](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md)
- [Functionenter3withinfo –](../../../../docs/framework/unmanaged-api/profiling/functionenter3withinfo-function.md)
- [Functionleave3withinfo –](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)
- [Functiontailcall3withinfo –](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3withinfo-function.md)
- [Globální statické funkce pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
- [ICorProfilerInfo3](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [Rozhraní pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Profilace](../../../../docs/framework/unmanaged-api/profiling/index.md)
