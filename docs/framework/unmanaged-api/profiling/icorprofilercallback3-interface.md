---
title: ICorProfilerCallback3 – rozhraní
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback3
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback3
helpviewer_keywords:
- ICorProfilerCallback3 interface [.NET Framework profiling]
ms.assetid: be83af41-3dec-4c77-8529-9dd6b8042af6
topic_type:
- apiref
ms.openlocfilehash: 25d674a143019ac5d724e36f03f36c79602b1e11
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74439510"
---
# <a name="icorprofilercallback3-interface"></a><span data-ttu-id="2df89-102">ICorProfilerCallback3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2df89-102">ICorProfilerCallback3 Interface</span></span>
<span data-ttu-id="2df89-103">Provides callback methods that the common language runtime (CLR) uses to communicate attach and detach state information to the profiler.</span><span class="sxs-lookup"><span data-stu-id="2df89-103">Provides callback methods that the common language runtime (CLR) uses to communicate attach and detach state information to the profiler.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2df89-104">Metody</span><span class="sxs-lookup"><span data-stu-id="2df89-104">Methods</span></span>  
  
|<span data-ttu-id="2df89-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="2df89-105">Method</span></span>|<span data-ttu-id="2df89-106">Popis</span><span class="sxs-lookup"><span data-stu-id="2df89-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2df89-107">InitializeForAttach – metoda</span><span class="sxs-lookup"><span data-stu-id="2df89-107">InitializeForAttach Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-initializeforattach-method.md)|<span data-ttu-id="2df89-108">Called by the CLR to give the profiler an opportunity to initialize its state after an attach operation.</span><span class="sxs-lookup"><span data-stu-id="2df89-108">Called by the CLR to give the profiler an opportunity to initialize its state after an attach operation.</span></span>|  
|[<span data-ttu-id="2df89-109">ProfilerAttachComplete – metoda</span><span class="sxs-lookup"><span data-stu-id="2df89-109">ProfilerAttachComplete Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-profilerattachcomplete-method.md)|<span data-ttu-id="2df89-110">Called by the CLR to indicate that the profiler can now call the catch-up methods.</span><span class="sxs-lookup"><span data-stu-id="2df89-110">Called by the CLR to indicate that the profiler can now call the catch-up methods.</span></span>|  
|[<span data-ttu-id="2df89-111">ProfilerDetachSucceeded – metoda</span><span class="sxs-lookup"><span data-stu-id="2df89-111">ProfilerDetachSucceeded Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-profilerdetachsucceeded-method.md)|<span data-ttu-id="2df89-112">Notifies the profiler that the common language runtime (CLR) is about to unload the profiler DLL.</span><span class="sxs-lookup"><span data-stu-id="2df89-112">Notifies the profiler that the common language runtime (CLR) is about to unload the profiler DLL.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2df89-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2df89-113">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2df89-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2df89-114">Requirements</span></span>  
 <span data-ttu-id="2df89-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2df89-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2df89-116">**Header:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="2df89-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="2df89-117">**Library:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2df89-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2df89-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2df89-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2df89-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2df89-119">See also</span></span>

- [<span data-ttu-id="2df89-120">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="2df89-120">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="2df89-121">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2df89-121">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="2df89-122">ICorProfilerCallback2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2df89-122">ICorProfilerCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
- [<span data-ttu-id="2df89-123">ICorProfilerCallback4 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2df89-123">ICorProfilerCallback4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)
