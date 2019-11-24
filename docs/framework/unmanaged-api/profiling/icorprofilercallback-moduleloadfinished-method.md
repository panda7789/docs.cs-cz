---
title: ICorProfilerCallback::ModuleLoadFinished – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ModuleLoadFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ModuleLoadFinished
helpviewer_keywords:
- ModuleLoadFinished method [.NET Framework profiling]
- ICorProfilerCallback::ModuleLoadFinished method [.NET Framework profiling]
ms.assetid: 050649e5-ffc0-4458-a0a4-d9ee128a219e
topic_type:
- apiref
ms.openlocfilehash: 08fbf49e6944de4934a9fe7a960405ee96a7d8e3
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445935"
---
# <a name="icorprofilercallbackmoduleloadfinished-method"></a>ICorProfilerCallback::ModuleLoadFinished – metoda
Notifies the profiler that a module has finished loading.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT ModuleLoadFinished(  
    [in] ModuleID moduleId,  
    [in] HRESULT  hrStatus);  
```  
  
## <a name="parameters"></a>Parametry  
 `moduleId`  
 [in] The ID of the module that has finished loading.  
  
 `hrStatus`  
 [in] An HRESULT that indicates whether the module was loaded successfully.  
  
## <a name="remarks"></a>Poznámky  
 The value of `moduleId` is not valid for an information request until the `ModuleLoadFinished` method is called.  
  
 Some parts of loading the module might continue after the `ModuleLoadFinished` callback. A failure HRESULT in `hrStatus` indicates a failure. However, a success HRESULT in `hrStatus` indicates only that the first part of loading the module has succeeded.  
  
## <a name="requirements"></a>Požadavky  
 **Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Header:** CorProf.idl, CorProf.h  
  
 **Library:** CorGuids.lib  
  
 **.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerCallback – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [ModuleLoadStarted – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadstarted-method.md)
