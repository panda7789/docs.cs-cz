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
ms.openlocfilehash: cc63a0a42c1da11daa5d38ecce505296a893616b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33453932"
---
# <a name="icorprofilercallback3-interface"></a><span data-ttu-id="925e5-102">ICorProfilerCallback3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="925e5-102">ICorProfilerCallback3 Interface</span></span>
<span data-ttu-id="925e5-103">Poskytuje metody zpětného volání, které modul CLR (CLR) používá ke komunikaci připojení a odpojení informace o stavu do profileru.</span><span class="sxs-lookup"><span data-stu-id="925e5-103">Provides callback methods that the common language runtime (CLR) uses to communicate attach and detach state information to the profiler.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="925e5-104">Metody</span><span class="sxs-lookup"><span data-stu-id="925e5-104">Methods</span></span>  
  
|<span data-ttu-id="925e5-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="925e5-105">Method</span></span>|<span data-ttu-id="925e5-106">Popis</span><span class="sxs-lookup"><span data-stu-id="925e5-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="925e5-107">InitializeForAttach – metoda</span><span class="sxs-lookup"><span data-stu-id="925e5-107">InitializeForAttach Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-initializeforattach-method.md)|<span data-ttu-id="925e5-108">Voláno rozhraním CLR umožnit profileru příležitost k chybě při inicializaci stav po operaci připojení.</span><span class="sxs-lookup"><span data-stu-id="925e5-108">Called by the CLR to give the profiler an opportunity to initialize its state after an attach operation.</span></span>|  
|[<span data-ttu-id="925e5-109">ProfilerAttachComplete – metoda</span><span class="sxs-lookup"><span data-stu-id="925e5-109">ProfilerAttachComplete Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-profilerattachcomplete-method.md)|<span data-ttu-id="925e5-110">Voláno k označení, že profileru nyní mohou volat metodu opravný modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="925e5-110">Called by the CLR to indicate that the profiler can now call the catch-up methods.</span></span>|  
|[<span data-ttu-id="925e5-111">ProfilerDetachSucceeded – metoda</span><span class="sxs-lookup"><span data-stu-id="925e5-111">ProfilerDetachSucceeded Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-profilerdetachsucceeded-method.md)|<span data-ttu-id="925e5-112">Upozorní profileru, že modul CLR (CLR) má uvolnit knihovnu DLL profileru.</span><span class="sxs-lookup"><span data-stu-id="925e5-112">Notifies the profiler that the common language runtime (CLR) is about to unload the profiler DLL.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="925e5-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="925e5-113">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="925e5-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="925e5-114">Requirements</span></span>  
 <span data-ttu-id="925e5-115">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="925e5-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="925e5-116">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="925e5-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="925e5-117">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="925e5-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="925e5-118">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="925e5-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="925e5-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="925e5-119">See Also</span></span>  
 [<span data-ttu-id="925e5-120">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="925e5-120">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="925e5-121">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="925e5-121">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="925e5-122">ICorProfilerCallback2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="925e5-122">ICorProfilerCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)  
 [<span data-ttu-id="925e5-123">ICorProfilerCallback4 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="925e5-123">ICorProfilerCallback4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)
