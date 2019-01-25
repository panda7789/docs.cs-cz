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
ms.openlocfilehash: 78e8c3c3cb4a56063bbdb5acb810483935c72bdf
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54545105"
---
# <a name="icorprofilercallback3profilerattachcomplete-method"></a><span data-ttu-id="92668-102">ICorProfilerCallback3::ProfilerAttachComplete – metoda</span><span class="sxs-lookup"><span data-stu-id="92668-102">ICorProfilerCallback3::ProfilerAttachComplete Method</span></span>
<span data-ttu-id="92668-103">Volá se, modulem common language runtime (CLR), která označuje, že profiler nyní volat [icorprofilerinfo3::enumjitedfunctions –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enumjitedfunctions-method.md) a [ICorProfilerInfo3::EnumModules](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enummodules-method.md) můžete projít metody.</span><span class="sxs-lookup"><span data-stu-id="92668-103">Called by the common language runtime (CLR) to indicate that the profiler can now call the [ICorProfilerInfo3::EnumJITedFunctions](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enumjitedfunctions-method.md) and [ICorProfilerInfo3::EnumModules](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enummodules-method.md) catch-up methods.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="92668-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="92668-104">Syntax</span></span>  
  
```  
HRESULT ProfilerAttachComplete ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="92668-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="92668-105">Remarks</span></span>  
 <span data-ttu-id="92668-106">`ProfilerAttachComplete` Zpětného volání je vydané po [ICorProfilerCallback3::InitializeForAttach](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-initializeforattach-method.md) metoda je volána.</span><span class="sxs-lookup"><span data-stu-id="92668-106">The `ProfilerAttachComplete` callback is issued after the [ICorProfilerCallback3::InitializeForAttach](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-initializeforattach-method.md) method is called.</span></span> <span data-ttu-id="92668-107">Označuje následující:</span><span class="sxs-lookup"><span data-stu-id="92668-107">It indicates the following:</span></span>  
  
-   <span data-ttu-id="92668-108">Zpětná volání, které bylo vyžádáno profilerem v `InitializeForAttach` aktivaci.</span><span class="sxs-lookup"><span data-stu-id="92668-108">The callbacks that were requested by the profiler in `InitializeForAttach` have been activated.</span></span>  
  
-   <span data-ttu-id="92668-109">Profiler teď můžete provádět zachytávání přidružené identifikátory bez obavy z chybějícího upozornění.</span><span class="sxs-lookup"><span data-stu-id="92668-109">The profiler can now perform catch-up on the associated IDs without being concerned about missing notifications.</span></span>  
  
 <span data-ttu-id="92668-110">Modul CLR bude ignorovat návratovou hodnotu z této zpětné volání.</span><span class="sxs-lookup"><span data-stu-id="92668-110">The CLR ignores the return value from this callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="92668-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="92668-111">Requirements</span></span>  
 <span data-ttu-id="92668-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="92668-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="92668-113">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="92668-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="92668-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="92668-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="92668-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="92668-115">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92668-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="92668-116">See also</span></span>
- [<span data-ttu-id="92668-117">ICorProfilerCallback – rozhraní</span><span class="sxs-lookup"><span data-stu-id="92668-117">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="92668-118">ICorProfilerInfo3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="92668-118">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [<span data-ttu-id="92668-119">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="92668-119">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="92668-120">Profilace</span><span class="sxs-lookup"><span data-stu-id="92668-120">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
