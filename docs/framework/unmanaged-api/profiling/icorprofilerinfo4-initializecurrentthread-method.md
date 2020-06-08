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
ms.openlocfilehash: 1f3ff3e9b68aa30f424f4b2fe6c7cacd2cddd544
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84495928"
---
# <a name="icorprofilerinfo4initializecurrentthread-method"></a><span data-ttu-id="e87c3-102">ICorProfilerInfo4::InitializeCurrentThread – metoda</span><span class="sxs-lookup"><span data-stu-id="e87c3-102">ICorProfilerInfo4::InitializeCurrentThread Method</span></span>
<span data-ttu-id="e87c3-103">Inicializuje aktuální vlákno předem v následných voláních rozhraní API profileru ve stejném vlákně, aby bylo možné zablokování zabránit.</span><span class="sxs-lookup"><span data-stu-id="e87c3-103">Initializes the current thread in advance of subsequent profiler API calls on the same thread, so that deadlock can be avoided.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e87c3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e87c3-104">Syntax</span></span>  
  
```cpp  
HRESULT InitializeCurrentThread ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="e87c3-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e87c3-105">Remarks</span></span>  
 <span data-ttu-id="e87c3-106">Doporučujeme, abyste volali `InitializeCurrentThread` jakékoli vlákno, které bude volat rozhraní API profileru, když dojde k pozastaveným vláknům.</span><span class="sxs-lookup"><span data-stu-id="e87c3-106">We recommend that you call `InitializeCurrentThread` on any thread that will call a profiler API while there are suspended threads.</span></span> <span data-ttu-id="e87c3-107">Tato metoda je obvykle používána vzorkovacími profily, které vytvoří vlastní vlákno pro volání metody [ICorProfilerInfo2::D ostacksnapshot](icorprofilerinfo2-dostacksnapshot-method.md) pro provádění procházení zásobníku, zatímco cílové vlákno je pozastaveno.</span><span class="sxs-lookup"><span data-stu-id="e87c3-107">This method is typically used by sampling profilers that create their own thread to call the [ICorProfilerInfo2::DoStackSnapshot](icorprofilerinfo2-dostacksnapshot-method.md) method to perform stack walks while the target thread is suspended.</span></span> <span data-ttu-id="e87c3-108">Zavoláním metody `InitializeCurrentThread` jednou, když Profiler nejprve vytvoří vlákno vzorkování, profilery mohou zajistit, aby při opožděné inicializaci po vláknech, které by CLR jinak prováděly během prvního volání, bylo `DoStackSnapshot` nyní možné bezpečně vyskytnout, když nejsou žádná jiná vlákna pozastavena.</span><span class="sxs-lookup"><span data-stu-id="e87c3-108">By calling `InitializeCurrentThread` once when the profiler first creates the sampling thread, profilers can ensure that lazy per-thread initialization that the CLR would otherwise perform during the first call to `DoStackSnapshot` can now occur safely when no other threads are suspended.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e87c3-109">`InitializeCurrentThread`provádí inicializaci předem úlohy, které přijímají zámky a mohou zablokovat.</span><span class="sxs-lookup"><span data-stu-id="e87c3-109">`InitializeCurrentThread` does the initialization in advance to finish tasks that take locks, and may deadlock.</span></span> <span data-ttu-id="e87c3-110">Volat `InitializeCurrentThread` pouze v případě, že nejsou k dispozici žádná pozastavená vlákna.</span><span class="sxs-lookup"><span data-stu-id="e87c3-110">Call `InitializeCurrentThread` only when there are no suspended threads.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e87c3-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e87c3-111">Requirements</span></span>  
 <span data-ttu-id="e87c3-112">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e87c3-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e87c3-113">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="e87c3-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e87c3-114">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="e87c3-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e87c3-115">**Verze .NET Framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e87c3-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e87c3-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e87c3-116">See also</span></span>

- [<span data-ttu-id="e87c3-117">ICorProfilerInfo4 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e87c3-117">ICorProfilerInfo4 Interface</span></span>](icorprofilerinfo4-interface.md)
- [<span data-ttu-id="e87c3-118">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="e87c3-118">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="e87c3-119">Profilace</span><span class="sxs-lookup"><span data-stu-id="e87c3-119">Profiling</span></span>](index.md)
