---
title: ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.SetEnterLeaveFunctionHooks3WithInfo Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo
helpviewer_keywords:
- SetEnterLeaveFunctionHooks3WithInfo method [.NET Framework profiling]
- ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo method [.NET Framework profiling]
ms.assetid: ca8ea534-e441-47b8-be85-466410988c0a
topic_type:
- apiref
ms.openlocfilehash: d40cb424306535cc502d930dd61e6a1e254667da
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84496175"
---
# <a name="icorprofilerinfo3setenterleavefunctionhooks3withinfo-method"></a>ICorProfilerInfo3::SetEnterLeaveFunctionHooks3WithInfo – metoda
Určuje funkce implementované profilerem, které budou volány na [FunctionEnter3WithInfo –](functionenter3withinfo-function.md), [FunctionLeave3WithInfo –](functionleave3withinfo-function.md)a [FunctionTailcall3WithInfo –ch](functiontailcall3withinfo-function.md) zapojování spravovaných funkcí.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetEnterLeaveFunctionHooks3WithInfo(  
            [in] FunctionEnter3WithInfo    *pFuncEnter3,  
            [in] FunctionLeave3withInfo    *pFuncLeave3,  
            [in] FunctionTailcall3WithInfo *pFuncTailcall3);  
```  
  
## <a name="parameters"></a>Parametry  
 `pFuncEnter3`  
 pro Ukazatel na implementaci, která se má použít jako `FunctionEnter3WithInfo` zpětné volání.  
  
 `pFuncLeave3`  
 pro Ukazatel na implementaci, která se má použít jako `FunctionLeave3WithInfo` zpětné volání.  
  
 `pFuncTailcall3`  
 pro Ukazatel na implementaci, která se má použít jako `FunctionTailcall3WithInfo` zpětné volání.  
  
## <a name="remarks"></a>Poznámky  
 Vidlice [FunctionEnter3WithInfo –](functionenter3withinfo-function.md), [FunctionLeave3WithInfo –](functionleave3withinfo-function.md)a [FunctionTailcall3WithInfo –](functiontailcall3withinfo-function.md) poskytují kontrolu rámce zásobníku a argumentů. Pro přístup k těmto informacím `COR_PRF_ENABLE_FUNCTION_ARGS` `COR_PRF_ENABLE_FUNCTION_RETVAL` `COR_PRF_ENABLE_FRAME_INFO` musí být nastavené příznaky, a. Profiler může použít metodu [ICorProfilerInfo:: SetEventMask](icorprofilerinfo-seteventmask-method.md) pro nastavení příznaků událostí a potom použít `SetEnterLeaveFunctionHooks3WithInfo` metodu k registraci implementace této funkce.  
  
 V jednom okamžiku může být aktivní jenom jedna sada zpětných volání a nejnovější verze má přednost. Proto pokud profiler volá [SetEnterLeaveFunctionHooks2 –](icorprofilerinfo2-setenterleavefunctionhooks2-method.md) i `SetEnterLeaveFunctionHooks3WithInfo` , `SetEnterLeaveFunctionHooks3WithInfo` je použit.  
  
 `SetEnterLeaveFunctionHooks3WithInfo`Metodu lze volat pouze z zpětného volání [ICorProfilerCallback:: Initialize](icorprofilercallback-initialize-method.md) profileru.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Setenterleavefunctionhooks3 –](icorprofilerinfo3-setenterleavefunctionhooks3-method.md)
- [Functionenter3 –](functionenter3-function.md)
- [Functionleave3 –](functionleave3-function.md)
- [Functiontailcall3 –](functiontailcall3-function.md)
- [Functionenter3withinfo –](functionenter3withinfo-function.md)
- [Functionleave3withinfo –](functionleave3withinfo-function.md)
- [Functiontailcall3withinfo –](functiontailcall3withinfo-function.md)
- [Profilace globálních statických funkcí](profiling-global-static-functions.md)
- [ICorProfilerInfo3 – rozhraní](icorprofilerinfo3-interface.md)
- [Rozhraní pro profilaci](profiling-interfaces.md)
- [Profilace](index.md)
