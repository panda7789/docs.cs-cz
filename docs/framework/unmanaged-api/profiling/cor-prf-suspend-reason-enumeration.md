---
title: COR_PRF_SUSPEND_REASON – výčet
ms.date: 03/30/2017
api_name:
- COR_PRF_SUSPEND_REASON
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_SUSPEND_REASON
helpviewer_keywords:
- COR_PRF_SUSPEND_REASON enumeration [.NET Framework profiling]
ms.assetid: 75594833-bed3-47b2-a426-b75c5fe6fbcf
topic_type:
- apiref
ms.openlocfilehash: d2d9ca77e764fe439753f1174a42af5ef80faa59
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447704"
---
# <a name="cor_prf_suspend_reason-enumeration"></a><span data-ttu-id="2465b-102">COR_PRF_SUSPEND_REASON – výčet</span><span class="sxs-lookup"><span data-stu-id="2465b-102">COR_PRF_SUSPEND_REASON Enumeration</span></span>
<span data-ttu-id="2465b-103">Indicates the reason that the runtime is suspended.</span><span class="sxs-lookup"><span data-stu-id="2465b-103">Indicates the reason that the runtime is suspended.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2465b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2465b-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PRF_SUSPEND_OTHER                   = 0x00,  
    COR_PRF_SUSPEND_FOR_GC                  = 0x01,  
    COR_PRF_SUSPEND_FOR_APPDOMAIN_SHUTDOWN  = 0x02,  
    COR_PRF_SUSPEND_FOR_CODE_PITCHING       = 0x03,  
    COR_PRF_SUSPEND_FOR_SHUTDOWN            = 0x04,  
    COR_PRF_SUSPEND_FOR_INPROC_DEBUGGER     = 0x06,  
    COR_PRF_SUSPEND_FOR_GC_PREP             = 0x07,    COR_PRF_SUSPEND_FOR_REJIT               = 8  
} COR_PRF_SUSPEND_REASON;  
```  
  
## <a name="members"></a><span data-ttu-id="2465b-105">Členové</span><span class="sxs-lookup"><span data-stu-id="2465b-105">Members</span></span>  
  
|<span data-ttu-id="2465b-106">Člen</span><span class="sxs-lookup"><span data-stu-id="2465b-106">Member</span></span>|<span data-ttu-id="2465b-107">Popis</span><span class="sxs-lookup"><span data-stu-id="2465b-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_FIELD_SUSPEND_OTHER`|<span data-ttu-id="2465b-108">The runtime is suspended for an unspecified reason.</span><span class="sxs-lookup"><span data-stu-id="2465b-108">The runtime is suspended for an unspecified reason.</span></span>|  
|`COR_PRF_FIELD_SUSPEND_FOR_GC`|<span data-ttu-id="2465b-109">The runtime is suspended to service a garbage collection request.</span><span class="sxs-lookup"><span data-stu-id="2465b-109">The runtime is suspended to service a garbage collection request.</span></span><br /><br /> <span data-ttu-id="2465b-110">The garbage collection-related callbacks occur between the [ICorProfilerCallback::RuntimeSuspendFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md) and [ICorProfilerCallback::RuntimeResumeStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimeresumestarted-method.md) callbacks.</span><span class="sxs-lookup"><span data-stu-id="2465b-110">The garbage collection-related callbacks occur between the [ICorProfilerCallback::RuntimeSuspendFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md) and [ICorProfilerCallback::RuntimeResumeStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimeresumestarted-method.md) callbacks.</span></span>|  
|`COR_PRF_FIELD_SUSPEND_FOR_APPDOMAIN_SHUTDOWN`|<span data-ttu-id="2465b-111">The runtime is suspended so that an `AppDomain` can be shut down.</span><span class="sxs-lookup"><span data-stu-id="2465b-111">The runtime is suspended so that an `AppDomain` can be shut down.</span></span><br /><br /> <span data-ttu-id="2465b-112">While the runtime is suspended, the runtime will determine which threads are in the `AppDomain` that is being shut down and set them to abort when they resume.</span><span class="sxs-lookup"><span data-stu-id="2465b-112">While the runtime is suspended, the runtime will determine which threads are in the `AppDomain` that is being shut down and set them to abort when they resume.</span></span> <span data-ttu-id="2465b-113">There are no `AppDomain`-specific callbacks during this suspension.</span><span class="sxs-lookup"><span data-stu-id="2465b-113">There are no `AppDomain`-specific callbacks during this suspension.</span></span>|  
|`COR_PRF_FIELD_SUSPEND_FOR_CODE_PITCHING`|<span data-ttu-id="2465b-114">The runtime is suspended so that code pitching can occur.</span><span class="sxs-lookup"><span data-stu-id="2465b-114">The runtime is suspended so that code pitching can occur.</span></span><br /><br /> <span data-ttu-id="2465b-115">Code pitching ensues only when the just-in-time (JIT) compiler is active with code pitching enabled.</span><span class="sxs-lookup"><span data-stu-id="2465b-115">Code pitching ensues only when the just-in-time (JIT) compiler is active with code pitching enabled.</span></span> <span data-ttu-id="2465b-116">Code pitching callbacks occur between the `ICorProfilerCallback::RuntimeSuspendFinished` and `ICorProfilerCallback::RuntimeResumeStarted` callbacks.</span><span class="sxs-lookup"><span data-stu-id="2465b-116">Code pitching callbacks occur between the `ICorProfilerCallback::RuntimeSuspendFinished` and `ICorProfilerCallback::RuntimeResumeStarted` callbacks.</span></span> <span data-ttu-id="2465b-117">**Note:**  The CLR JIT does not pitch functions in the .NET Framework version 2.0, so this value is not used in 2.0.</span><span class="sxs-lookup"><span data-stu-id="2465b-117">**Note:**  The CLR JIT does not pitch functions in the .NET Framework version 2.0, so this value is not used in 2.0.</span></span>|  
|`COR_PRF_FIELD_SUSPEND_FOR_SHUTDOWN`|<span data-ttu-id="2465b-118">The runtime is suspended so that it can shut down.</span><span class="sxs-lookup"><span data-stu-id="2465b-118">The runtime is suspended so that it can shut down.</span></span> <span data-ttu-id="2465b-119">It must suspend all threads to complete the operation.</span><span class="sxs-lookup"><span data-stu-id="2465b-119">It must suspend all threads to complete the operation.</span></span>|  
|`COR_PRF_FIELD_SUSPEND_FOR_INPROC_DEBUGGER`|<span data-ttu-id="2465b-120">The runtime is suspended for in-process debugging.</span><span class="sxs-lookup"><span data-stu-id="2465b-120">The runtime is suspended for in-process debugging.</span></span>|  
|`COR_PRF_FIELD_SUSPEND_FOR_GC_PREP`|<span data-ttu-id="2465b-121">The runtime is suspended to prepare for a garbage collection.</span><span class="sxs-lookup"><span data-stu-id="2465b-121">The runtime is suspended to prepare for a garbage collection.</span></span>|  
|`COR_PRF_SUSPEND_FOR_REJIT`|<span data-ttu-id="2465b-122">The runtime is suspended for JIT recompilation.</span><span class="sxs-lookup"><span data-stu-id="2465b-122">The runtime is suspended for JIT recompilation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2465b-123">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2465b-123">Remarks</span></span>  
 <span data-ttu-id="2465b-124">All runtime threads that are in unmanaged code are permitted to continue running until they try to re-enter the runtime, at which point they will also be suspended until the runtime resumes.</span><span class="sxs-lookup"><span data-stu-id="2465b-124">All runtime threads that are in unmanaged code are permitted to continue running until they try to re-enter the runtime, at which point they will also be suspended until the runtime resumes.</span></span> <span data-ttu-id="2465b-125">This also applies to new threads that enter the runtime.</span><span class="sxs-lookup"><span data-stu-id="2465b-125">This also applies to new threads that enter the runtime.</span></span> <span data-ttu-id="2465b-126">All threads within the runtime are either suspended immediately if they are in interruptible code, or asked to suspend when they do reach interruptible code.</span><span class="sxs-lookup"><span data-stu-id="2465b-126">All threads within the runtime are either suspended immediately if they are in interruptible code, or asked to suspend when they do reach interruptible code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2465b-127">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2465b-127">Requirements</span></span>  
 <span data-ttu-id="2465b-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2465b-128">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2465b-129">**Header:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="2465b-129">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="2465b-130">**Library:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2465b-130">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2465b-131">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2465b-131">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2465b-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2465b-132">See also</span></span>

- [<span data-ttu-id="2465b-133">Výčty pro profilaci</span><span class="sxs-lookup"><span data-stu-id="2465b-133">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
