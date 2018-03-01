---
title: "ICorProfilerInfo4::InitializeCurrentThread – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorProfilerInfo4::InitializeCurrentThread
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::InitializeCurrentThread
helpviewer_keywords:
- ICorProfilerInfo4::InitializeCurrentThread method [.NET Framework profiling]
- InitializeCurrentThread method, ICorProfilerInfo4 interface [.NET Framework profiling]
ms.assetid: 18a3335c-8c75-476c-b6de-72c0bfedae5d
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 4f3c261068b38861dca2633a490e46d9f44371d7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo4initializecurrentthread-method"></a><span data-ttu-id="6cd69-102">ICorProfilerInfo4::InitializeCurrentThread – metoda</span><span class="sxs-lookup"><span data-stu-id="6cd69-102">ICorProfilerInfo4::InitializeCurrentThread Method</span></span>
<span data-ttu-id="6cd69-103">Inicializuje aktuální vlákno předem následné profileru, které volání rozhraní API ve stejném vlákně, takže se vyhnout této vzájemného zablokování.</span><span class="sxs-lookup"><span data-stu-id="6cd69-103">Initializes the current thread in advance of subsequent profiler API calls on the same thread, so that deadlock can be avoided.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6cd69-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6cd69-104">Syntax</span></span>  
  
```  
HRESULT InitializeCurrentThread ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="6cd69-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6cd69-105">Remarks</span></span>  
 <span data-ttu-id="6cd69-106">Doporučujeme vám, že zavoláte `InitializeCurrentThread` na jakékoli vlákno, které bude volat profileru rozhraní API, protože existují pozastaveno vláken.</span><span class="sxs-lookup"><span data-stu-id="6cd69-106">We recommend that you call `InitializeCurrentThread` on any thread that will call a profiler API while there are suspended threads.</span></span> <span data-ttu-id="6cd69-107">Tato metoda se obvykle používá ve profilery vzorkování, které vytvořit své vlastní vlákno k volání [ICorProfilerInfo2::dostacksnapshot –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) metodu za účelem zásobníku provede při cíl vlákno je pozastaveno.</span><span class="sxs-lookup"><span data-stu-id="6cd69-107">This method is typically used by sampling profilers that create their own thread to call the [ICorProfilerInfo2::DoStackSnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) method to perform stack walks while the target thread is suspended.</span></span> <span data-ttu-id="6cd69-108">Při volání `InitializeCurrentThread` po profileru při první vytvoří vlákno vzorkování, profilery můžete zajistit, že inicializaci opožděné podle vláken, která modulu CLR by jinak prováděných při prvním volání `DoStackSnapshot` nyní dochází bezpečně když jsou nejsou žádná jiná vlákna pozastaveno.</span><span class="sxs-lookup"><span data-stu-id="6cd69-108">By calling `InitializeCurrentThread` once when the profiler first creates the sampling thread, profilers can ensure that lazy per-thread initialization that the CLR would otherwise perform during the first call to `DoStackSnapshot` can now occur safely when no other threads are suspended.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6cd69-109">`InitializeCurrentThread`provede inicializaci předem na dokončení úlohy, které trvat zámků a může zablokování.</span><span class="sxs-lookup"><span data-stu-id="6cd69-109">`InitializeCurrentThread` does the initialization in advance to finish tasks that take locks, and may deadlock.</span></span> <span data-ttu-id="6cd69-110">Volání `InitializeCurrentThread` jenom v případě, že neexistují žádné pozastavenou vláken.</span><span class="sxs-lookup"><span data-stu-id="6cd69-110">Call `InitializeCurrentThread` only when there are no suspended threads.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6cd69-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6cd69-111">Requirements</span></span>  
 <span data-ttu-id="6cd69-112">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6cd69-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6cd69-113">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="6cd69-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="6cd69-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6cd69-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6cd69-115">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6cd69-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6cd69-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="6cd69-116">See Also</span></span>  
 [<span data-ttu-id="6cd69-117">ICorProfilerInfo4 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6cd69-117">ICorProfilerInfo4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)  
 [<span data-ttu-id="6cd69-118">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="6cd69-118">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="6cd69-119">Profilace</span><span class="sxs-lookup"><span data-stu-id="6cd69-119">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
