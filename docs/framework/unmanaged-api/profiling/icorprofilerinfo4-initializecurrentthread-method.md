---
title: ICorProfilerInfo4::InitializeCurrentThread – metoda
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b9bb5a2629e435d76691d48feef6689191b66373
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69957891"
---
# <a name="icorprofilerinfo4initializecurrentthread-method"></a><span data-ttu-id="74a59-102">ICorProfilerInfo4::InitializeCurrentThread – metoda</span><span class="sxs-lookup"><span data-stu-id="74a59-102">ICorProfilerInfo4::InitializeCurrentThread Method</span></span>
<span data-ttu-id="74a59-103">Inicializuje aktuální vlákno předem v následných voláních rozhraní API profileru ve stejném vlákně, aby bylo možné zablokování zabránit.</span><span class="sxs-lookup"><span data-stu-id="74a59-103">Initializes the current thread in advance of subsequent profiler API calls on the same thread, so that deadlock can be avoided.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="74a59-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="74a59-104">Syntax</span></span>  
  
```cpp  
HRESULT InitializeCurrentThread ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="74a59-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="74a59-105">Remarks</span></span>  
 <span data-ttu-id="74a59-106">Doporučujeme, abyste volali `InitializeCurrentThread` jakékoli vlákno, které bude volat rozhraní API profileru, když dojde k pozastaveným vláknům.</span><span class="sxs-lookup"><span data-stu-id="74a59-106">We recommend that you call `InitializeCurrentThread` on any thread that will call a profiler API while there are suspended threads.</span></span> <span data-ttu-id="74a59-107">Tato metoda je obvykle používána vzorkovacími profily, které vytvoří vlastní vlákno pro volání metody [ICorProfilerInfo2::D ostacksnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) pro provádění procházení zásobníku, zatímco cílové vlákno je pozastaveno.</span><span class="sxs-lookup"><span data-stu-id="74a59-107">This method is typically used by sampling profilers that create their own thread to call the [ICorProfilerInfo2::DoStackSnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) method to perform stack walks while the target thread is suspended.</span></span> <span data-ttu-id="74a59-108">Vyvoláním metody `InitializeCurrentThread` jednou, když Profiler nejprve vytvoří vlákno vzorkování, profilery mohou zajistit, aby byla inicializace opožděného vlákna, kterou by CLR jinak prováděla během prvního `DoStackSnapshot` volání, mohla být bezpečně provedena, pokud nejsou žádná jiná vlákna. rozpuštěn.</span><span class="sxs-lookup"><span data-stu-id="74a59-108">By calling `InitializeCurrentThread` once when the profiler first creates the sampling thread, profilers can ensure that lazy per-thread initialization that the CLR would otherwise perform during the first call to `DoStackSnapshot` can now occur safely when no other threads are suspended.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="74a59-109">`InitializeCurrentThread`provádí inicializaci předem úlohy, které přijímají zámky a mohou zablokovat.</span><span class="sxs-lookup"><span data-stu-id="74a59-109">`InitializeCurrentThread` does the initialization in advance to finish tasks that take locks, and may deadlock.</span></span> <span data-ttu-id="74a59-110">Volat `InitializeCurrentThread` pouze v případě, že nejsou k dispozici žádná pozastavená vlákna.</span><span class="sxs-lookup"><span data-stu-id="74a59-110">Call `InitializeCurrentThread` only when there are no suspended threads.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="74a59-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="74a59-111">Requirements</span></span>  
 <span data-ttu-id="74a59-112">**Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="74a59-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="74a59-113">**Hlaviček** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="74a59-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="74a59-114">**Knihovna** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="74a59-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="74a59-115">**Verze .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="74a59-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74a59-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="74a59-116">See also</span></span>

- [<span data-ttu-id="74a59-117">ICorProfilerInfo4 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="74a59-117">ICorProfilerInfo4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)
- [<span data-ttu-id="74a59-118">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="74a59-118">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="74a59-119">Profilace</span><span class="sxs-lookup"><span data-stu-id="74a59-119">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
