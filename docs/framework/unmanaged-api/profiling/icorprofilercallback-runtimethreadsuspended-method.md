---
title: "ICorProfilerCallback::RuntimeThreadSuspended – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.RuntimeThreadSuspended
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::RuntimeThreadSuspended
helpviewer_keywords:
- RuntimeThreadSuspended method [.NET Framework profiling]
- ICorProfilerCallback::RuntimeThreadSuspended method [.NET Framework profiling]
ms.assetid: de830a8b-6ee1-4900-ace3-4237108f6b12
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: e4d2ab0244e898a60db8fe392ccbd8c0ebfd5523
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilercallbackruntimethreadsuspended-method"></a><span data-ttu-id="ccc04-102">ICorProfilerCallback::RuntimeThreadSuspended – metoda</span><span class="sxs-lookup"><span data-stu-id="ccc04-102">ICorProfilerCallback::RuntimeThreadSuspended Method</span></span>
<span data-ttu-id="ccc04-103">Profileru upozorní, že zadaný vlákno byla pozastavena, nebo se pozastaví.</span><span class="sxs-lookup"><span data-stu-id="ccc04-103">Notifies the profiler that the specified thread has been suspended or is about to be suspended.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ccc04-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ccc04-104">Syntax</span></span>  
  
```  
HRESULT RuntimeThreadSuspended(  
    [in] ThreadID threadId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ccc04-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ccc04-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="ccc04-106">[v] ID vlákno, které bylo pozastaveno.</span><span class="sxs-lookup"><span data-stu-id="ccc04-106">[in] The ID of the thread that has been suspended.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ccc04-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ccc04-107">Remarks</span></span>  
 <span data-ttu-id="ccc04-108">`RuntimeThreadSuspended` Oznámení může dojít kdykoliv mezi [icorprofilercallback::runtimesuspendstarted –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md) a přidružené [icorprofilercallback::runtimeresumestarted –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimeresumestarted-method.md) zpětných volání.</span><span class="sxs-lookup"><span data-stu-id="ccc04-108">The `RuntimeThreadSuspended` notification can occur any time between the [ICorProfilerCallback::RuntimeSuspendStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md) and the associated [ICorProfilerCallback::RuntimeResumeStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimeresumestarted-method.md) callbacks.</span></span> <span data-ttu-id="ccc04-109">Oznámení, ke kterým dochází mezi [icorprofilercallback::runtimesuspendfinished –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md) a `RuntimeResumeStarted` jsou pro vláken, které byly spuštěny v nespravovaného kódu a bylo pozastaveno při vstupu do runtime.</span><span class="sxs-lookup"><span data-stu-id="ccc04-109">Notifications that occur between [ICorProfilerCallback::RuntimeSuspendFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md) and `RuntimeResumeStarted` are for threads that had been running in unmanaged code and were suspended upon entry to the runtime.</span></span>  
  
 <span data-ttu-id="ccc04-110">Obecně platí tento zpětného volání nastane hned po vlákno je pozastaveno.</span><span class="sxs-lookup"><span data-stu-id="ccc04-110">Generally, this callback occurs just after a thread is suspended.</span></span> <span data-ttu-id="ccc04-111">Ale pokud aktuálně prováděné vlákno (podproces, který volá tento zpětného volání) je ten, který bylo pozastaveno, tento zpětné volání se provedou těsně před vlákno je pozastaveno.</span><span class="sxs-lookup"><span data-stu-id="ccc04-111">However, if the currently executing thread (the thread that called this callback) is the one that is being suspended, this callback will occur just before the thread is suspended.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ccc04-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ccc04-112">Requirements</span></span>  
 <span data-ttu-id="ccc04-113">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ccc04-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ccc04-114">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ccc04-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ccc04-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ccc04-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ccc04-116">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ccc04-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ccc04-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="ccc04-117">See Also</span></span>  
 [<span data-ttu-id="ccc04-118">Icorprofilercallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ccc04-118">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="ccc04-119">Runtimethreadresumed – metoda</span><span class="sxs-lookup"><span data-stu-id="ccc04-119">RuntimeThreadResumed Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimethreadresumed-method.md)
