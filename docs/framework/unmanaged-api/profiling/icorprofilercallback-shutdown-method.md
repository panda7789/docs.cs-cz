---
title: ICorProfilerCallback::Shutdown – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.Shutdown
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::Shutdown
helpviewer_keywords:
- ICorProfilerCallback::Shutdown method [.NET Framework profiling]
- Shutdown method [.NET Framework profiling]
ms.assetid: 1ea194f0-a331-4855-a2ce-37393b8e5f84
topic_type:
- apiref
ms.openlocfilehash: 63e41df8af85d94df068526ef69708687b341e78
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446940"
---
# <a name="icorprofilercallbackshutdown-method"></a>ICorProfilerCallback::Shutdown – metoda
Notifies the profiler that the application is shutting down.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT Shutdown();  
```  
  
## <a name="remarks"></a>Poznámky  
 The profiler code cannot safely call methods of the [ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md) interface after the `Shutdown` method is called. Any calls to `ICorProfilerInfo` methods result in undefined behavior after the `Shutdown` method returns. Certain immutable events may still occur after shutdown; the profiler should take care to return immediately when this occurs.  
  
 The `Shutdown` method will be called only if the managed application that is being profiled started as managed code (that is, the initial frame on the process stack is managed). If the application started as unmanaged code but later jumped into managed code, thereby creating an instance of the common language runtime (CLR), then `Shutdown` will not be called. For these cases, the profiler should include in its library a `DllMain` routine that uses the DLL_PROCESS_DETACH value to free any resources and perform clean-up processing of its data, such as flushing traces to disk and so on.  
  
 In general, the profiler must cope with unexpected shutdowns. For example, a process might be halted by Win32's `TerminateProcess` method (declared in Winbase.h). In other cases, the CLR will halt certain managed threads (background threads) without delivering orderly destruction messages for them.  
  
## <a name="requirements"></a>Požadavky  
 **Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Header:** CorProf.idl, CorProf.h  
  
 **Library:** CorGuids.lib  
  
 **.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerCallback – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [Initialize – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md)
