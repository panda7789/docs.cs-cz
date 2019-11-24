---
title: ICorProfilerCallback3::ProfilerAttachComplete – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback3.ProfilerAttachComplete Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback3::ProfilerAttachComplete
helpviewer_keywords:
- ProfilerAttachComplete method [.NET Framework profiling]
- ICorProfilerCallback3::ProfilerAttachComplete method [.NET Framework profiling]
ms.assetid: 257d6076-06e0-4d93-bb33-651fbb2b92d7
topic_type:
- apiref
ms.openlocfilehash: 4c5b8f18424ba54d9e8e14ba0a518a89e0d54796
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74439461"
---
# <a name="icorprofilercallback3profilerattachcomplete-method"></a><span data-ttu-id="4497b-102">ICorProfilerCallback3::ProfilerAttachComplete – metoda</span><span class="sxs-lookup"><span data-stu-id="4497b-102">ICorProfilerCallback3::ProfilerAttachComplete Method</span></span>
<span data-ttu-id="4497b-103">Called by the common language runtime (CLR) to indicate that the profiler can now call the [ICorProfilerInfo3::EnumJITedFunctions](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enumjitedfunctions-method.md) and [ICorProfilerInfo3::EnumModules](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enummodules-method.md) catch-up methods.</span><span class="sxs-lookup"><span data-stu-id="4497b-103">Called by the common language runtime (CLR) to indicate that the profiler can now call the [ICorProfilerInfo3::EnumJITedFunctions](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enumjitedfunctions-method.md) and [ICorProfilerInfo3::EnumModules](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enummodules-method.md) catch-up methods.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4497b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4497b-104">Syntax</span></span>  
  
```cpp  
HRESULT ProfilerAttachComplete ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="4497b-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4497b-105">Remarks</span></span>  
 <span data-ttu-id="4497b-106">The `ProfilerAttachComplete` callback is issued after the [ICorProfilerCallback3::InitializeForAttach](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-initializeforattach-method.md) method is called.</span><span class="sxs-lookup"><span data-stu-id="4497b-106">The `ProfilerAttachComplete` callback is issued after the [ICorProfilerCallback3::InitializeForAttach](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-initializeforattach-method.md) method is called.</span></span> <span data-ttu-id="4497b-107">It indicates the following:</span><span class="sxs-lookup"><span data-stu-id="4497b-107">It indicates the following:</span></span>  
  
- <span data-ttu-id="4497b-108">The callbacks that were requested by the profiler in `InitializeForAttach` have been activated.</span><span class="sxs-lookup"><span data-stu-id="4497b-108">The callbacks that were requested by the profiler in `InitializeForAttach` have been activated.</span></span>  
  
- <span data-ttu-id="4497b-109">The profiler can now perform catch-up on the associated IDs without being concerned about missing notifications.</span><span class="sxs-lookup"><span data-stu-id="4497b-109">The profiler can now perform catch-up on the associated IDs without being concerned about missing notifications.</span></span>  
  
 <span data-ttu-id="4497b-110">The CLR ignores the return value from this callback.</span><span class="sxs-lookup"><span data-stu-id="4497b-110">The CLR ignores the return value from this callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4497b-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4497b-111">Requirements</span></span>  
 <span data-ttu-id="4497b-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4497b-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4497b-113">**Header:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="4497b-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="4497b-114">**Library:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4497b-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4497b-115">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4497b-115">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4497b-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4497b-116">See also</span></span>

- [<span data-ttu-id="4497b-117">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4497b-117">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="4497b-118">ICorProfilerInfo3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4497b-118">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [<span data-ttu-id="4497b-119">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="4497b-119">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="4497b-120">Profilace</span><span class="sxs-lookup"><span data-stu-id="4497b-120">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
