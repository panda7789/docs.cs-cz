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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 66e6a67ce022365fa8c9e1005dfecbe4b23abd10
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59158377"
---
# <a name="icorprofilercallback3-interface"></a><span data-ttu-id="b6b03-102">ICorProfilerCallback3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b6b03-102">ICorProfilerCallback3 Interface</span></span>
<span data-ttu-id="b6b03-103">Poskytuje metody zpětného volání, které modul CLR (CLR) používá ke komunikaci připojení a odpojení profileru informace o stavu.</span><span class="sxs-lookup"><span data-stu-id="b6b03-103">Provides callback methods that the common language runtime (CLR) uses to communicate attach and detach state information to the profiler.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b6b03-104">Metody</span><span class="sxs-lookup"><span data-stu-id="b6b03-104">Methods</span></span>  
  
|<span data-ttu-id="b6b03-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="b6b03-105">Method</span></span>|<span data-ttu-id="b6b03-106">Popis</span><span class="sxs-lookup"><span data-stu-id="b6b03-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b6b03-107">InitializeForAttach – metoda</span><span class="sxs-lookup"><span data-stu-id="b6b03-107">InitializeForAttach Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-initializeforattach-method.md)|<span data-ttu-id="b6b03-108">Volá se, platformou CLR, která poskytující nástroji pro profilování příležitost k inicializaci svého stavu po operaci připojení.</span><span class="sxs-lookup"><span data-stu-id="b6b03-108">Called by the CLR to give the profiler an opportunity to initialize its state after an attach operation.</span></span>|  
|[<span data-ttu-id="b6b03-109">ProfilerAttachComplete – metoda</span><span class="sxs-lookup"><span data-stu-id="b6b03-109">ProfilerAttachComplete Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-profilerattachcomplete-method.md)|<span data-ttu-id="b6b03-110">Volá se, platformou CLR, která označuje, že profiler nyní volat metody můžete projít.</span><span class="sxs-lookup"><span data-stu-id="b6b03-110">Called by the CLR to indicate that the profiler can now call the catch-up methods.</span></span>|  
|[<span data-ttu-id="b6b03-111">ProfilerDetachSucceeded – metoda</span><span class="sxs-lookup"><span data-stu-id="b6b03-111">ProfilerDetachSucceeded Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-profilerdetachsucceeded-method.md)|<span data-ttu-id="b6b03-112">Oznámí profileru, že modul CLR (CLR) se chystá uvolnění knihovny DLL profileru.</span><span class="sxs-lookup"><span data-stu-id="b6b03-112">Notifies the profiler that the common language runtime (CLR) is about to unload the profiler DLL.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b6b03-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b6b03-113">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b6b03-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b6b03-114">Requirements</span></span>  
 <span data-ttu-id="b6b03-115">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b6b03-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b6b03-116">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="b6b03-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b6b03-117">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b6b03-117">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="b6b03-118">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="b6b03-118">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="b6b03-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b6b03-119">See also</span></span>

- [<span data-ttu-id="b6b03-120">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="b6b03-120">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="b6b03-121">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b6b03-121">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="b6b03-122">ICorProfilerCallback2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b6b03-122">ICorProfilerCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
- [<span data-ttu-id="b6b03-123">ICorProfilerCallback4 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b6b03-123">ICorProfilerCallback4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)
