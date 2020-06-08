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
ms.openlocfilehash: 78489aae840ff17e68b10bd7593fb7be4dae1af7
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84496729"
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
 pro Ukazatel na implementaci, která se má použít jako [FunctionEnter2](functionenter2-function.md) zpětné volání.  
  
 `pFuncLeave`  
 pro Ukazatel na implementaci, která se má použít jako [FunctionLeave2 –](functionleave2-function.md) zpětné volání.  
  
 `pFuncTailcall`  
 pro Ukazatel na implementaci, která se má použít jako [FunctionTailcall2 –](functiontailcall2-function.md) zpětné volání.  
  
## <a name="remarks"></a>Poznámky  
 `SetEnterLeaveFunctionHooks2`Metoda je podobná metodě [ICorProfilerInfo:: SetEnterLeaveFunctionHooks –](icorprofilerinfo-setenterleavefunctionhooks-method.md) . Použijte předchozí, pokud chcete určit funkce, které mají být použity jako novější verze zpětných volání ENTER/opustit/Tailcall, a druhý pro určení funkcí, které mají být použity jako starší verze zpětných volání ENTER/opustit/Tailcall.  
  
 V jednom okamžiku může být aktivní jenom jedna sada zpětných volání. Proto pokud profiler volá `ICorProfilerInfo::SetEnterLeaveFunctionHooks` a `SetEnterLeaveFunctionHooks2` , `SetEnterLeaveFunctionHooks2` je použit.  
  
 `SetEnterLeaveFunctionHooks2`Metodu lze volat pouze z zpětného volání [ICorProfilerCallback:: Initialize](icorprofilercallback-initialize-method.md) profileru.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerInfo – rozhraní](icorprofilerinfo-interface.md)
- [ICorProfilerInfo2 – rozhraní](icorprofilerinfo2-interface.md)
