---
title: ICorProfilerCallback::ThreadAssignedToOSThread – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ThreadAssignedToOSThread
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ThreadAssignedToOSThread
helpviewer_keywords:
- ThreadAssignedToOSThread method [.NET Framework profiling]
- ICorProfilerCallback::ThreadAssignedToOSThread method [.NET Framework profiling]
ms.assetid: f9671e5a-7b14-4f5b-8404-58136422c8b2
topic_type:
- apiref
ms.openlocfilehash: 1b69c0522c47d4e675180af67adab166626da4d7
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74440023"
---
# <a name="icorprofilercallbackthreadassignedtoosthread-method"></a><span data-ttu-id="24a23-102">ICorProfilerCallback::ThreadAssignedToOSThread – metoda</span><span class="sxs-lookup"><span data-stu-id="24a23-102">ICorProfilerCallback::ThreadAssignedToOSThread Method</span></span>
<span data-ttu-id="24a23-103">Notifies the profiler that a managed thread is being implemented using a particular operating system thread.</span><span class="sxs-lookup"><span data-stu-id="24a23-103">Notifies the profiler that a managed thread is being implemented using a particular operating system thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="24a23-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="24a23-104">Syntax</span></span>  
  
```cpp  
HRESULT ThreadAssignedToOSThread(  
    [in] ThreadID managedThreadId,  
    [in] DWORD    osThreadId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="24a23-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="24a23-105">Parameters</span></span>  
 `managedThreadId`  
 <span data-ttu-id="24a23-106">[in] The identifier of the managed thread.</span><span class="sxs-lookup"><span data-stu-id="24a23-106">[in] The identifier of the managed thread.</span></span>  
  
 `osThreadId`  
 <span data-ttu-id="24a23-107">[in] The identifier of the operating system thread.</span><span class="sxs-lookup"><span data-stu-id="24a23-107">[in] The identifier of the operating system thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="24a23-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="24a23-108">Remarks</span></span>  
 <span data-ttu-id="24a23-109">The `ThreadAssignedToOSThread` callback exists so that the profiler can maintain an accurate mapping across fibers of operating system threads to managed threads.</span><span class="sxs-lookup"><span data-stu-id="24a23-109">The `ThreadAssignedToOSThread` callback exists so that the profiler can maintain an accurate mapping across fibers of operating system threads to managed threads.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="24a23-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="24a23-110">Requirements</span></span>  
 <span data-ttu-id="24a23-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="24a23-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="24a23-112">**Header:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="24a23-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="24a23-113">**Library:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="24a23-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="24a23-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="24a23-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24a23-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="24a23-115">See also</span></span>

- [<span data-ttu-id="24a23-116">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="24a23-116">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
