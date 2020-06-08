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
ms.openlocfilehash: eb658d682ce589b7dfdcfc0228d0c657310e6f7a
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84496230"
---
# <a name="icorprofilerinfo3setenterleavefunctionhooks3-method"></a>ICorProfilerInfo3::SetEnterLeaveFunctionHooks3 – metoda
Určuje funkce implementované profilerem, které budou volány ve funkcích [FunctionEnter3 –](functionenter3-function.md), [FunctionLeave3 –](functionleave3-function.md)a [FunctionTailcall3 –](functiontailcall3-function.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetEnterLeaveFunctionHooks3(  
            [in] FunctionEnter3    *pFuncEnter3,  
            [in] FunctionLeave3    *pFuncLeave3,  
            [in] FunctionTailcall3 *pFuncTailcall3);  
```  
  
## <a name="parameters"></a>Parametry  
 `pFuncEnter3`  
 pro Ukazatel na implementaci, která se má použít jako `FunctionEnter3` zpětné volání.  
  
 `pFuncLeave3`  
 pro Ukazatel na implementaci, která se má použít jako `FunctionLeave3` zpětné volání.  
  
 `pFuncTailcall3`  
 pro Ukazatel na implementaci, která se má použít jako `FunctionTailcall3` zpětné volání.  
  
## <a name="remarks"></a>Poznámky  
 [FunctionEnter3 –](functionenter3-function.md), [FunctionLeave3 –](functionleave3-function.md)a [FunctionTailcall3 –](functiontailcall3-function.md) háky neposkytují kontrolu rámce zásobníku a argumentů. Pro přístup k těmto informacím `COR_PRF_ENABLE_FUNCTION_ARGS` `COR_PRF_ENABLE_FUNCTION_RETVAL` `COR_PRF_ENABLE_FRAME_INFO` musí být nastavené příznaky, a. Profiler může použít metodu [ICorProfilerInfo:: SetEventMask](icorprofilerinfo-seteventmask-method.md) pro nastavení příznaků událostí a pak použít metodu [ICorProfilerInfo3:: SetEnterLeaveFunctionHooks3WithInfo –](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md) k registraci implementace této funkce.  
  
 V jednom okamžiku může být aktivní jenom jedna sada zpětných volání a nejnovější verze má přednost. Proto pokud profiler volá [metodu SetEnterLeaveFunctionHooks2 –](icorprofilerinfo2-setenterleavefunctionhooks2-method.md) a `SetEnterLeaveFunctionHooks3` metodu, `SetEnterLeaveFunctionHooks3` je použit.  
  
 `SetEnterLeaveFunctionHooks3`Metodu lze volat pouze z zpětného volání [ICorProfilerCallback:: Initialize](icorprofilercallback-initialize-method.md) profileru.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Setenterleavefunctionhooks3withinfo –](icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)
- [Functionenter3 –](functionenter3-function.md)
- [Functionleave3 –](functionleave3-function.md)
- [Functiontailcall3 –](functiontailcall3-function.md)
- [Functionenter3withinfo –](functionenter3withinfo-function.md)
- [Functionleave3withinfo –](functionleave3withinfo-function.md)
- [Functiontailcall3withinfo –](functiontailcall3withinfo-function.md)
- [Profilace globálních statických funkcí](profiling-global-static-functions.md)
- [ICorProfilerInfo3](icorprofilerinfo3-interface.md)
- [Rozhraní pro profilaci](profiling-interfaces.md)
- [Profilace](index.md)
