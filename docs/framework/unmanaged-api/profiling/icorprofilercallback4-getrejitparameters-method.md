---
title: ICorProfilerCallback4::GetReJITParameters – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback4.GetReJITParameters
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback4::GetReJITParameters
helpviewer_keywords:
- ICorProfilerCallback4::GetReJITParameters method [.NET Framework profiling]
- GetReJITParameters method, ICorProfilerCallback4 interface [.NET Framework profiling]
ms.assetid: 0e9bfe07-9f20-498c-b568-9017c8f6056c
topic_type:
- apiref
ms.openlocfilehash: d81d7275d197de1dfc99b135377459f509c2651f
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74439434"
---
# <a name="icorprofilercallback4getrejitparameters-method"></a>ICorProfilerCallback4::GetReJITParameters – metoda
Allows the code profiler to set alternate code generation flags for a new recompiled method body.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetReJITParameters(     [in] ModuleID moduleId,     [in] mdMethodDef methodId,     [in] ICorProfilerFunctionControl *pFunctionControl);  
```  
  
## <a name="parameters"></a>Parametry  
 `moduleID`  
 [in] The module that contains the method for which the CLR needs JIT recompilation parameters.  
  
 `methodId`  
 [in] The `MethodDef` of the method for which the CLR needs JIT recompilation parameters.  
  
 `pFunctionControl`  
 [in] A pointer to an [ICorProfilerFunctionControl](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-interface.md) interface that the profiler can use to provide JIT recompilation information for the method being recompiled.  
  
## <a name="remarks"></a>Poznámky  
 The CLR issues a `GetReJITParameters` callback so that the profiler can specify the parameters for recompiling a given method. The `GetReJITParameters` callback is issued only once per function; the parameters supplied by the profiler apply to all instances of that function.  
  
## <a name="requirements"></a>Požadavky  
 **Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Header:** CorProf.idl, CorProf.h  
  
 **Library:** CorGuids.lib  
  
 **.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerCallback – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [ICorProfilerCallback4 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)
- [JITCompilationStarted – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md)
- [ReJITCompilationStarted – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationstarted-method.md)
