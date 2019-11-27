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
ms.openlocfilehash: 39882a554f9d47040bef00ff320d15b56abea533
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445725"
---
# <a name="icorprofilerinfo4initializecurrentthread-method"></a><span data-ttu-id="dc127-102">ICorProfilerInfo4::InitializeCurrentThread – metoda</span><span class="sxs-lookup"><span data-stu-id="dc127-102">ICorProfilerInfo4::InitializeCurrentThread Method</span></span>
<span data-ttu-id="dc127-103">Inicializuje aktuální vlákno předem v následných voláních rozhraní API profileru ve stejném vlákně, aby bylo možné zablokování zabránit.</span><span class="sxs-lookup"><span data-stu-id="dc127-103">Initializes the current thread in advance of subsequent profiler API calls on the same thread, so that deadlock can be avoided.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dc127-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dc127-104">Syntax</span></span>  
  
```cpp  
HRESULT InitializeCurrentThread ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="dc127-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="dc127-105">Remarks</span></span>  
 <span data-ttu-id="dc127-106">Doporučujeme, abyste volali `InitializeCurrentThread` na jakémkoli vlákně, které bude volat rozhraní API profileru, když dojde k pozastaveným vláknům.</span><span class="sxs-lookup"><span data-stu-id="dc127-106">We recommend that you call `InitializeCurrentThread` on any thread that will call a profiler API while there are suspended threads.</span></span> <span data-ttu-id="dc127-107">Tato metoda je obvykle používána vzorkovacími profily, které vytvoří vlastní vlákno pro volání metody [ICorProfilerInfo2::D ostacksnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) pro provádění procházení zásobníku, zatímco cílové vlákno je pozastaveno.</span><span class="sxs-lookup"><span data-stu-id="dc127-107">This method is typically used by sampling profilers that create their own thread to call the [ICorProfilerInfo2::DoStackSnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) method to perform stack walks while the target thread is suspended.</span></span> <span data-ttu-id="dc127-108">Zavoláním `InitializeCurrentThread`, když Profiler nejprve vytvoří vlákno vzorkování, profilery mohou zajistit, že při prvním volání metody, které by CLR jinak prováděl během prvního volání `DoStackSnapshot`, může nyní dojít k bezpečnému výskytu v případě, že nejsou pozastavena žádná jiná vlákna.</span><span class="sxs-lookup"><span data-stu-id="dc127-108">By calling `InitializeCurrentThread` once when the profiler first creates the sampling thread, profilers can ensure that lazy per-thread initialization that the CLR would otherwise perform during the first call to `DoStackSnapshot` can now occur safely when no other threads are suspended.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="dc127-109">`InitializeCurrentThread` provede inicializaci předem k dokončení úkolů, které přijímají zámky, a může zablokovat.</span><span class="sxs-lookup"><span data-stu-id="dc127-109">`InitializeCurrentThread` does the initialization in advance to finish tasks that take locks, and may deadlock.</span></span> <span data-ttu-id="dc127-110">Volání `InitializeCurrentThread` pouze v případě, že nejsou k dispozici žádná pozastavená vlákna.</span><span class="sxs-lookup"><span data-stu-id="dc127-110">Call `InitializeCurrentThread` only when there are no suspended threads.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dc127-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="dc127-111">Requirements</span></span>  
 <span data-ttu-id="dc127-112">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dc127-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dc127-113">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="dc127-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="dc127-114">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="dc127-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dc127-115">**Verze .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dc127-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc127-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="dc127-116">See also</span></span>

- [<span data-ttu-id="dc127-117">ICorProfilerInfo4 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="dc127-117">ICorProfilerInfo4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)
- [<span data-ttu-id="dc127-118">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="dc127-118">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="dc127-119">Profilace</span><span class="sxs-lookup"><span data-stu-id="dc127-119">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
