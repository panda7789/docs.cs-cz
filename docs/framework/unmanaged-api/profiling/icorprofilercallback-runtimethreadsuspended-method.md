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
ms.openlocfilehash: c8645bf828d0ad99bd25c1909cbee3314a11abf9
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76865867"
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
 Oznámení `RuntimeThreadSuspended` může nastat kdykoli mezi [ICorProfilerCallback:: runtimesuspendstarted –](icorprofilercallback-runtimesuspendstarted-method.md) a přidruženými zpětnými voláními [ICorProfilerCallback:: RuntimeResumeStarted –](icorprofilercallback-runtimeresumestarted-method.md) . Oznámení, ke kterým dochází mezi [ICorProfilerCallback:: RuntimeSuspendFinished –](icorprofilercallback-runtimesuspendfinished-method.md) a `RuntimeResumeStarted`, jsou pro vlákna, která byla spuštěna v nespravovaném kódu a byla pozastavena při vstupu do modulu runtime.  
  
 Obecně platí, že toto zpětné volání proběhne hned po pozastavení vlákna. Nicméně pokud je aktuálně spuštěné vlákno (vlákno, které volalo toto zpětné volání), které je pozastaveno, toto zpětné volání proběhne těsně před pozastavením vlákna.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerCallback – rozhraní](icorprofilercallback-interface.md)
- [RuntimeThreadResumed – metoda](icorprofilercallback-runtimethreadresumed-method.md)
