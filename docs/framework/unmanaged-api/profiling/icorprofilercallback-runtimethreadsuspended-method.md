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
ms.openlocfilehash: 54f7dae511c8bf25dc96451e6477acf26655430a
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503195"
---
# <a name="icorprofilercallbackruntimethreadsuspended-method"></a><span data-ttu-id="d13bb-102">ICorProfilerCallback::RuntimeThreadSuspended – metoda</span><span class="sxs-lookup"><span data-stu-id="d13bb-102">ICorProfilerCallback::RuntimeThreadSuspended Method</span></span>
<span data-ttu-id="d13bb-103">Upozorní profileru, že zadané vlákno je pozastavené nebo se chystá pozastavit.</span><span class="sxs-lookup"><span data-stu-id="d13bb-103">Notifies the profiler that the specified thread has been suspended or is about to be suspended.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d13bb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d13bb-104">Syntax</span></span>  
  
```cpp  
HRESULT RuntimeThreadSuspended(  
    [in] ThreadID threadId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d13bb-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d13bb-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="d13bb-106">pro ID podprocesu, který byl pozastaven.</span><span class="sxs-lookup"><span data-stu-id="d13bb-106">[in] The ID of the thread that has been suspended.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d13bb-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d13bb-107">Remarks</span></span>  
 <span data-ttu-id="d13bb-108">`RuntimeThreadSuspended`Oznámení může nastat kdykoli mezi [ICorProfilerCallback:: runtimesuspendstarted –](icorprofilercallback-runtimesuspendstarted-method.md) a přidruženými zpětnými voláními [ICorProfilerCallback:: RuntimeResumeStarted –](icorprofilercallback-runtimeresumestarted-method.md) .</span><span class="sxs-lookup"><span data-stu-id="d13bb-108">The `RuntimeThreadSuspended` notification can occur any time between the [ICorProfilerCallback::RuntimeSuspendStarted](icorprofilercallback-runtimesuspendstarted-method.md) and the associated [ICorProfilerCallback::RuntimeResumeStarted](icorprofilercallback-runtimeresumestarted-method.md) callbacks.</span></span> <span data-ttu-id="d13bb-109">Oznámení, ke kterým dochází mezi [ICorProfilerCallback:: RuntimeSuspendFinished –](icorprofilercallback-runtimesuspendfinished-method.md) a `RuntimeResumeStarted` jsou pro vlákna, která byla spuštěna v nespravovaném kódu a byla pozastavena při vstupu do modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="d13bb-109">Notifications that occur between [ICorProfilerCallback::RuntimeSuspendFinished](icorprofilercallback-runtimesuspendfinished-method.md) and `RuntimeResumeStarted` are for threads that had been running in unmanaged code and were suspended upon entry to the runtime.</span></span>  
  
 <span data-ttu-id="d13bb-110">Obecně platí, že toto zpětné volání proběhne hned po pozastavení vlákna.</span><span class="sxs-lookup"><span data-stu-id="d13bb-110">Generally, this callback occurs just after a thread is suspended.</span></span> <span data-ttu-id="d13bb-111">Nicméně pokud je aktuálně spuštěné vlákno (vlákno, které volalo toto zpětné volání), které je pozastaveno, toto zpětné volání proběhne těsně před pozastavením vlákna.</span><span class="sxs-lookup"><span data-stu-id="d13bb-111">However, if the currently executing thread (the thread that called this callback) is the one that is being suspended, this callback will occur just before the thread is suspended.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d13bb-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d13bb-112">Requirements</span></span>  
 <span data-ttu-id="d13bb-113">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d13bb-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d13bb-114">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="d13bb-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d13bb-115">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="d13bb-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d13bb-116">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d13bb-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d13bb-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d13bb-117">See also</span></span>

- [<span data-ttu-id="d13bb-118">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d13bb-118">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="d13bb-119">RuntimeThreadResumed – metoda</span><span class="sxs-lookup"><span data-stu-id="d13bb-119">RuntimeThreadResumed Method</span></span>](icorprofilercallback-runtimethreadresumed-method.md)
