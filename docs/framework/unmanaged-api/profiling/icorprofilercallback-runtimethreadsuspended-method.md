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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a0748802599926f4ec218362e6f7d086aab2d8f9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62041740"
---
# <a name="icorprofilercallbackruntimethreadsuspended-method"></a>ICorProfilerCallback::RuntimeThreadSuspended – metoda
Profiler upozorní, že zadaného vlákna se pozastavilo, nebo se pozastaví.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT RuntimeThreadSuspended(  
    [in] ThreadID threadId);  
```  
  
## <a name="parameters"></a>Parametry  
 `threadId`  
 [in] ID vlákna, které bylo pozastaveno.  
  
## <a name="remarks"></a>Poznámky  
 `RuntimeThreadSuspended` Oznámení může dojít kdykoliv mezi [icorprofilercallback::runtimesuspendstarted –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md) a přidružené [ICorProfilerCallback::RuntimeResumeStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimeresumestarted-method.md) zpětná volání. Oznámení, ke kterým dochází mezi [ICorProfilerCallback::RuntimeSuspendFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md) a `RuntimeResumeStarted` jsou vlákna, které byly spuštěny v nespravovaného kódu a pozastavené při vstupu do modulu runtime.  
  
 Obecně platí tato zpětné volání nastane bezprostředně po vlákno je pozastaveno. Nicméně pokud aktuálně spuštěné vlákno (podproces, který volá tento zpětného volání) je ten, který je pozastavená, tato zpětné volání dojde k těsně před plánovaným začátkem vlákno je pozastaveno.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerCallback – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [RuntimeThreadResumed – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimethreadresumed-method.md)
