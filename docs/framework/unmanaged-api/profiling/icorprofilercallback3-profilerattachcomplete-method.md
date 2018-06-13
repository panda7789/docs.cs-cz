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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8397900e2dafb69807417090cbb30c85dd884c59
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33454375"
---
# <a name="icorprofilercallback3profilerattachcomplete-method"></a><span data-ttu-id="223c2-102">ICorProfilerCallback3::ProfilerAttachComplete – metoda</span><span class="sxs-lookup"><span data-stu-id="223c2-102">ICorProfilerCallback3::ProfilerAttachComplete Method</span></span>
<span data-ttu-id="223c2-103">Modul CLR (CLR) k označení, že můžete nyní volat profileru je voláno [icorprofilerinfo3::enumjitedfunctions –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enumjitedfunctions-method.md) a [icorprofilerinfo3::enummodules –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enummodules-method.md) opravný metody.</span><span class="sxs-lookup"><span data-stu-id="223c2-103">Called by the common language runtime (CLR) to indicate that the profiler can now call the [ICorProfilerInfo3::EnumJITedFunctions](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enumjitedfunctions-method.md) and [ICorProfilerInfo3::EnumModules](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enummodules-method.md) catch-up methods.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="223c2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="223c2-104">Syntax</span></span>  
  
```  
HRESULT ProfilerAttachComplete ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="223c2-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="223c2-105">Remarks</span></span>  
 <span data-ttu-id="223c2-106">`ProfilerAttachComplete` Zpětné volání se objeví po [icorprofilercallback3::initializeforattach –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-initializeforattach-method.md) metoda je volána.</span><span class="sxs-lookup"><span data-stu-id="223c2-106">The `ProfilerAttachComplete` callback is issued after the [ICorProfilerCallback3::InitializeForAttach](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-initializeforattach-method.md) method is called.</span></span> <span data-ttu-id="223c2-107">Znamená to následující:</span><span class="sxs-lookup"><span data-stu-id="223c2-107">It indicates the following:</span></span>  
  
-   <span data-ttu-id="223c2-108">Zpětná volání, které byly požadoval profileru v `InitializeForAttach` aktivoval.</span><span class="sxs-lookup"><span data-stu-id="223c2-108">The callbacks that were requested by the profiler in `InitializeForAttach` have been activated.</span></span>  
  
-   <span data-ttu-id="223c2-109">Profileru teď můžete dělat zjištěná v přidružené ID aniž by musel být zajímá chybějící oznámení.</span><span class="sxs-lookup"><span data-stu-id="223c2-109">The profiler can now perform catch-up on the associated IDs without being concerned about missing notifications.</span></span>  
  
 <span data-ttu-id="223c2-110">Modul CLR ignoruje návratovou hodnotou z této zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="223c2-110">The CLR ignores the return value from this callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="223c2-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="223c2-111">Requirements</span></span>  
 <span data-ttu-id="223c2-112">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="223c2-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="223c2-113">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="223c2-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="223c2-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="223c2-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="223c2-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="223c2-115">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="223c2-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="223c2-116">See Also</span></span>  
 [<span data-ttu-id="223c2-117">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="223c2-117">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="223c2-118">ICorProfilerInfo3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="223c2-118">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)  
 [<span data-ttu-id="223c2-119">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="223c2-119">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="223c2-120">Profilace</span><span class="sxs-lookup"><span data-stu-id="223c2-120">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
