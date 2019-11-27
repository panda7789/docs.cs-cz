---
title: ICorProfilerCallback::RuntimeThreadSuspended – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RuntimeThreadSuspended
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RuntimeThreadSuspended
helpviewer_keywords:
- RuntimeThreadSuspended method [.NET Framework profiling]
- ICorProfilerCallback::RuntimeThreadSuspended method [.NET Framework profiling]
ms.assetid: de830a8b-6ee1-4900-ace3-4237108f6b12
topic_type:
- apiref
ms.openlocfilehash: 509d6cd2e65c2eb8c92f6d79deae9e01e75298f6
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74433443"
---
# <a name="icorprofilercallbackruntimethreadsuspended-method"></a>ICorProfilerCallback::RuntimeThreadSuspended – metoda
Upozorní profileru, že zadané vlákno je pozastavené nebo se chystá pozastavit.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT RuntimeThreadSuspended(  
    [in] ThreadID threadId);  
```  
  
## <a name="parameters"></a>Parametry  
 `threadId`  
 pro ID podprocesu, který byl pozastaven.  
  
## <a name="remarks"></a>Poznámky  
 Oznámení `RuntimeThreadSuspended` může nastat kdykoli mezi [ICorProfilerCallback:: runtimesuspendstarted –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md) a přidruženými zpětnými voláními [ICorProfilerCallback:: RuntimeResumeStarted –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimeresumestarted-method.md) . Oznámení, ke kterým dochází mezi [ICorProfilerCallback:: RuntimeSuspendFinished –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md) a `RuntimeResumeStarted`, jsou pro vlákna, která byla spuštěna v nespravovaném kódu a byla pozastavena při vstupu do modulu runtime.  
  
 Obecně platí, že toto zpětné volání proběhne hned po pozastavení vlákna. Nicméně pokud je aktuálně spuštěné vlákno (vlákno, které volalo toto zpětné volání), které je pozastaveno, toto zpětné volání proběhne těsně před pozastavením vlákna.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerCallback – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [RuntimeThreadResumed – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimethreadresumed-method.md)
