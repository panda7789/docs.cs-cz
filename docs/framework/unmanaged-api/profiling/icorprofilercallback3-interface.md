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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61598880"
---
# <a name="icorprofilercallback3-interface"></a><span data-ttu-id="87565-102">ICorProfilerCallback3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="87565-102">ICorProfilerCallback3 Interface</span></span>
<span data-ttu-id="87565-103">Poskytuje metody zpětného volání, které modul CLR (CLR) používá ke komunikaci připojení a odpojení profileru informace o stavu.</span><span class="sxs-lookup"><span data-stu-id="87565-103">Provides callback methods that the common language runtime (CLR) uses to communicate attach and detach state information to the profiler.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="87565-104">Metody</span><span class="sxs-lookup"><span data-stu-id="87565-104">Methods</span></span>  
  
|<span data-ttu-id="87565-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="87565-105">Method</span></span>|<span data-ttu-id="87565-106">Popis</span><span class="sxs-lookup"><span data-stu-id="87565-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="87565-107">InitializeForAttach – metoda</span><span class="sxs-lookup"><span data-stu-id="87565-107">InitializeForAttach Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-initializeforattach-method.md)|<span data-ttu-id="87565-108">Volá se, platformou CLR, která poskytující nástroji pro profilování příležitost k inicializaci svého stavu po operaci připojení.</span><span class="sxs-lookup"><span data-stu-id="87565-108">Called by the CLR to give the profiler an opportunity to initialize its state after an attach operation.</span></span>|  
|[<span data-ttu-id="87565-109">ProfilerAttachComplete – metoda</span><span class="sxs-lookup"><span data-stu-id="87565-109">ProfilerAttachComplete Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-profilerattachcomplete-method.md)|<span data-ttu-id="87565-110">Volá se, platformou CLR, která označuje, že profiler nyní volat metody můžete projít.</span><span class="sxs-lookup"><span data-stu-id="87565-110">Called by the CLR to indicate that the profiler can now call the catch-up methods.</span></span>|  
|[<span data-ttu-id="87565-111">ProfilerDetachSucceeded – metoda</span><span class="sxs-lookup"><span data-stu-id="87565-111">ProfilerDetachSucceeded Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-profilerdetachsucceeded-method.md)|<span data-ttu-id="87565-112">Oznámí profileru, že modul CLR (CLR) se chystá uvolnění knihovny DLL profileru.</span><span class="sxs-lookup"><span data-stu-id="87565-112">Notifies the profiler that the common language runtime (CLR) is about to unload the profiler DLL.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="87565-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="87565-113">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="87565-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="87565-114">Requirements</span></span>  
 <span data-ttu-id="87565-115">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="87565-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="87565-116">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="87565-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="87565-117">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="87565-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="87565-118">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="87565-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87565-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="87565-119">See also</span></span>

- [<span data-ttu-id="87565-120">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="87565-120">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="87565-121">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="87565-121">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="87565-122">ICorProfilerCallback2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="87565-122">ICorProfilerCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
- [<span data-ttu-id="87565-123">ICorProfilerCallback4 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="87565-123">ICorProfilerCallback4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)
