---
title: "ICorProfilerCallback3 – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback3
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback3
helpviewer_keywords: ICorProfilerCallback3 interface [.NET Framework profiling]
ms.assetid: be83af41-3dec-4c77-8529-9dd6b8042af6
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: c62dfb9b44999309ab2be7dfdcdfba3bb5dde29c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilercallback3-interface"></a><span data-ttu-id="c111c-102">ICorProfilerCallback3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c111c-102">ICorProfilerCallback3 Interface</span></span>
<span data-ttu-id="c111c-103">Poskytuje metody zpětného volání, které modul CLR (CLR) používá ke komunikaci připojení a odpojení informace o stavu do profileru.</span><span class="sxs-lookup"><span data-stu-id="c111c-103">Provides callback methods that the common language runtime (CLR) uses to communicate attach and detach state information to the profiler.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c111c-104">Metody</span><span class="sxs-lookup"><span data-stu-id="c111c-104">Methods</span></span>  
  
|<span data-ttu-id="c111c-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="c111c-105">Method</span></span>|<span data-ttu-id="c111c-106">Popis</span><span class="sxs-lookup"><span data-stu-id="c111c-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c111c-107">Initializeforattach – metoda</span><span class="sxs-lookup"><span data-stu-id="c111c-107">InitializeForAttach Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-initializeforattach-method.md)|<span data-ttu-id="c111c-108">Voláno rozhraním CLR umožnit profileru příležitost k chybě při inicializaci stav po operaci připojení.</span><span class="sxs-lookup"><span data-stu-id="c111c-108">Called by the CLR to give the profiler an opportunity to initialize its state after an attach operation.</span></span>|  
|[<span data-ttu-id="c111c-109">Profilerattachcomplete – metoda</span><span class="sxs-lookup"><span data-stu-id="c111c-109">ProfilerAttachComplete Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-profilerattachcomplete-method.md)|<span data-ttu-id="c111c-110">Voláno k označení, že profileru nyní mohou volat metodu opravný modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="c111c-110">Called by the CLR to indicate that the profiler can now call the catch-up methods.</span></span>|  
|[<span data-ttu-id="c111c-111">Profilerdetachsucceeded – metoda</span><span class="sxs-lookup"><span data-stu-id="c111c-111">ProfilerDetachSucceeded Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-profilerdetachsucceeded-method.md)|<span data-ttu-id="c111c-112">Upozorní profileru, že modul CLR (CLR) má uvolnit knihovnu DLL profileru.</span><span class="sxs-lookup"><span data-stu-id="c111c-112">Notifies the profiler that the common language runtime (CLR) is about to unload the profiler DLL.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c111c-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c111c-113">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c111c-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c111c-114">Requirements</span></span>  
 <span data-ttu-id="c111c-115">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c111c-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c111c-116">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="c111c-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c111c-117">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c111c-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c111c-118">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c111c-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c111c-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="c111c-119">See Also</span></span>  
 [<span data-ttu-id="c111c-120">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="c111c-120">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="c111c-121">Icorprofilerinfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c111c-121">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="c111c-122">Icorprofilercallback2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c111c-122">ICorProfilerCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)  
 [<span data-ttu-id="c111c-123">Icorprofilercallback4 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c111c-123">ICorProfilerCallback4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)
