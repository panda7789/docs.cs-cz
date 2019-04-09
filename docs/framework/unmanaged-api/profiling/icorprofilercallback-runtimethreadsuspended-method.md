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
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59080225"
---
# <a name="icorprofilercallbackruntimethreadsuspended-method"></a><span data-ttu-id="d0a76-102">ICorProfilerCallback::RuntimeThreadSuspended – metoda</span><span class="sxs-lookup"><span data-stu-id="d0a76-102">ICorProfilerCallback::RuntimeThreadSuspended Method</span></span>
<span data-ttu-id="d0a76-103">Profiler upozorní, že zadaného vlákna se pozastavilo, nebo se pozastaví.</span><span class="sxs-lookup"><span data-stu-id="d0a76-103">Notifies the profiler that the specified thread has been suspended or is about to be suspended.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d0a76-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d0a76-104">Syntax</span></span>  
  
```  
HRESULT RuntimeThreadSuspended(  
    [in] ThreadID threadId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d0a76-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d0a76-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="d0a76-106">[in] ID vlákna, které bylo pozastaveno.</span><span class="sxs-lookup"><span data-stu-id="d0a76-106">[in] The ID of the thread that has been suspended.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d0a76-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d0a76-107">Remarks</span></span>  
 <span data-ttu-id="d0a76-108">`RuntimeThreadSuspended` Oznámení může dojít kdykoliv mezi [icorprofilercallback::runtimesuspendstarted –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md) a přidružené [ICorProfilerCallback::RuntimeResumeStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimeresumestarted-method.md) zpětná volání.</span><span class="sxs-lookup"><span data-stu-id="d0a76-108">The `RuntimeThreadSuspended` notification can occur any time between the [ICorProfilerCallback::RuntimeSuspendStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md) and the associated [ICorProfilerCallback::RuntimeResumeStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimeresumestarted-method.md) callbacks.</span></span> <span data-ttu-id="d0a76-109">Oznámení, ke kterým dochází mezi [ICorProfilerCallback::RuntimeSuspendFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md) a `RuntimeResumeStarted` jsou vlákna, které byly spuštěny v nespravovaného kódu a pozastavené při vstupu do modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="d0a76-109">Notifications that occur between [ICorProfilerCallback::RuntimeSuspendFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md) and `RuntimeResumeStarted` are for threads that had been running in unmanaged code and were suspended upon entry to the runtime.</span></span>  
  
 <span data-ttu-id="d0a76-110">Obecně platí tato zpětné volání nastane bezprostředně po vlákno je pozastaveno.</span><span class="sxs-lookup"><span data-stu-id="d0a76-110">Generally, this callback occurs just after a thread is suspended.</span></span> <span data-ttu-id="d0a76-111">Nicméně pokud aktuálně spuštěné vlákno (podproces, který volá tento zpětného volání) je ten, který je pozastavená, tato zpětné volání dojde k těsně před plánovaným začátkem vlákno je pozastaveno.</span><span class="sxs-lookup"><span data-stu-id="d0a76-111">However, if the currently executing thread (the thread that called this callback) is the one that is being suspended, this callback will occur just before the thread is suspended.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d0a76-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d0a76-112">Requirements</span></span>  
 <span data-ttu-id="d0a76-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d0a76-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d0a76-114">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="d0a76-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d0a76-115">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d0a76-115">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="d0a76-116">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="d0a76-116">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="d0a76-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d0a76-117">See also</span></span>

- [<span data-ttu-id="d0a76-118">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d0a76-118">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="d0a76-119">RuntimeThreadResumed – metoda</span><span class="sxs-lookup"><span data-stu-id="d0a76-119">RuntimeThreadResumed Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimethreadresumed-method.md)
