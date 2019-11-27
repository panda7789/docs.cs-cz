---
title: ICorProfilerInfo2::SetEnterLeaveFunctionHooks2 – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.SetEnterLeaveFunctionHooks2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::SetEnterLeaveFunctionHooks2
helpviewer_keywords:
- ICorProfilerInfo2::SetEnterLeaveFunctionHooks2 method [.NET Framework profiling]
- SetEnterLeaveFunctionHooks2 method [.NET Framework profiling]
ms.assetid: 3c26b3e7-f72b-48a5-bf8c-edc122523a4b
topic_type:
- apiref
ms.openlocfilehash: 4068c8fee13a6086bc6b48bcc6d4117357062747
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449782"
---
# <a name="icorprofilerinfo2setenterleavefunctionhooks2-method"></a>ICorProfilerInfo2::SetEnterLeaveFunctionHooks2 – metoda
Určuje funkce implementované profilerem, které mají být volány v aktualizovaných verzích zapojování spravovaných funkcí "Enter", "opustit" a "Tailcall".  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetEnterLeaveFunctionHooks2(  
    [in] FunctionEnter2    *pFuncEnter,  
    [in] FunctionLeave2    *pFuncLeave,  
    [in] FunctionTailcall2 *pFuncTailcall);  
```  
  
## <a name="parameters"></a>Parametry  
 `pFuncEnter`  
 pro Ukazatel na implementaci, která se má použít jako [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md) zpětné volání.  
  
 `pFuncLeave`  
 pro Ukazatel na implementaci, která se má použít jako [FunctionLeave2 –](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md) zpětné volání.  
  
 `pFuncTailcall`  
 pro Ukazatel na implementaci, která se má použít jako [FunctionTailcall2 –](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md) zpětné volání.  
  
## <a name="remarks"></a>Poznámky  
 Metoda `SetEnterLeaveFunctionHooks2` je podobná metodě [ICorProfilerInfo:: SetEnterLeaveFunctionHooks –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setenterleavefunctionhooks-method.md) . Použijte předchozí, pokud chcete určit funkce, které mají být použity jako novější verze zpětných volání ENTER/opustit/Tailcall, a druhý pro určení funkcí, které mají být použity jako starší verze zpětných volání ENTER/opustit/Tailcall.  
  
 V jednom okamžiku může být aktivní jenom jedna sada zpětných volání. Proto pokud profiler zavolá jak `ICorProfilerInfo::SetEnterLeaveFunctionHooks`, tak `SetEnterLeaveFunctionHooks2`, `SetEnterLeaveFunctionHooks2` se používá.  
  
 Metodu `SetEnterLeaveFunctionHooks2` lze volat pouze z zpětného volání [ICorProfilerCallback:: Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) .  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerInfo – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [ICorProfilerInfo2 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
