---
title: ICorProfilerCallback::RuntimeSuspendStarted – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RuntimeSuspendStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RuntimeSuspendStarted
helpviewer_keywords:
- ICorProfilerCallback::RuntimeSuspendStarted method [.NET Framework profiling]
- RuntimeSuspendStarted method [.NET Framework profiling]
ms.assetid: c8461cac-e31b-4efa-ad2c-26598173eb96
topic_type:
- apiref
ms.openlocfilehash: 1777fa1f2537b6d28d771661ca463564d74d8550
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74433510"
---
# <a name="icorprofilercallbackruntimesuspendstarted-method"></a>ICorProfilerCallback::RuntimeSuspendStarted – metoda
Upozorní profileru, že modul runtime chystá pozastavit všechny běhové vlákna.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT RuntimeSuspendStarted(  
    [in] COR_PRF_SUSPEND_REASON suspendReason);  
```  
  
## <a name="parameters"></a>Parametry  
 `suspendReason`  
 pro Hodnota výčtu [COR_PRF_SUSPEND_REASON](../../../../docs/framework/unmanaged-api/profiling/cor-prf-suspend-reason-enumeration.md) , která označuje důvod pro pozastavení.  
  
## <a name="remarks"></a>Poznámky  
 Všechna vlákna modulu runtime, která jsou v nespravovaném kódu, mohou pokračovat v běhu, dokud se nepokusí znovu zadat modul runtime. V tomto okamžiku se také pozastaví, dokud modul runtime nebude pokračovat. To platí také pro nová vlákna, která vstupují do modulu runtime. Všechna vlákna v modulu runtime jsou buď okamžitě pozastavena, pokud jsou již v kódu přerušitelné, nebo jsou požádány o pozastavení, když dosáhnou přerušitelné kódu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerCallback – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [RuntimeSuspendAborted – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendaborted-method.md)
- [RuntimeSuspendFinished – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md)
