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
ms.openlocfilehash: 9fd0900e61c57d105439d83430284dc8634d2a1e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62000503"
---
# <a name="icorprofilerinfo4initializecurrentthread-method"></a><span data-ttu-id="6100a-102">ICorProfilerInfo4::InitializeCurrentThread – metoda</span><span class="sxs-lookup"><span data-stu-id="6100a-102">ICorProfilerInfo4::InitializeCurrentThread Method</span></span>
<span data-ttu-id="6100a-103">Inicializuje aktuální vlákno s předstihem následné profiler volání rozhraní API ve stejném vlákně, takže se lze vyvarovat této zablokování.</span><span class="sxs-lookup"><span data-stu-id="6100a-103">Initializes the current thread in advance of subsequent profiler API calls on the same thread, so that deadlock can be avoided.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6100a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6100a-104">Syntax</span></span>  
  
```  
HRESULT InitializeCurrentThread ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="6100a-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6100a-105">Remarks</span></span>  
 <span data-ttu-id="6100a-106">Doporučujeme vám, že zavoláte `InitializeCurrentThread` v libovolném vlákně, který bude volat profilování rozhraní API, i když existují pozastavená vlákna.</span><span class="sxs-lookup"><span data-stu-id="6100a-106">We recommend that you call `InitializeCurrentThread` on any thread that will call a profiler API while there are suspended threads.</span></span> <span data-ttu-id="6100a-107">Tato metoda je obvykle používána vzorkování profilovací programy, které vytvoření vlastních vláken k volání [ICorProfilerInfo2::DoStackSnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) metodu za účelem zásobníku vás během cílové vlákno je pozastaveno.</span><span class="sxs-lookup"><span data-stu-id="6100a-107">This method is typically used by sampling profilers that create their own thread to call the [ICorProfilerInfo2::DoStackSnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) method to perform stack walks while the target thread is suspended.</span></span> <span data-ttu-id="6100a-108">Voláním `InitializeCurrentThread` až když profiler nejprve vytvoří vlákno vzorkování, profilery můžete zajistit, že opožděná vlákno inicializace, které modul CLR by jinak provádět při prvním volání `DoStackSnapshot` nyní provést bezpečně kdy mají být nejsou žádná jiná vlákna pozastaveno.</span><span class="sxs-lookup"><span data-stu-id="6100a-108">By calling `InitializeCurrentThread` once when the profiler first creates the sampling thread, profilers can ensure that lazy per-thread initialization that the CLR would otherwise perform during the first call to `DoStackSnapshot` can now occur safely when no other threads are suspended.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6100a-109">`InitializeCurrentThread` provede inicializaci předem na dokončení úlohy, které povede a může zablokování.</span><span class="sxs-lookup"><span data-stu-id="6100a-109">`InitializeCurrentThread` does the initialization in advance to finish tasks that take locks, and may deadlock.</span></span> <span data-ttu-id="6100a-110">Volání `InitializeCurrentThread` pouze v případě, že neexistují žádná pozastavená vlákna.</span><span class="sxs-lookup"><span data-stu-id="6100a-110">Call `InitializeCurrentThread` only when there are no suspended threads.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6100a-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6100a-111">Requirements</span></span>  
 <span data-ttu-id="6100a-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6100a-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6100a-113">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="6100a-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="6100a-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6100a-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6100a-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6100a-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6100a-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6100a-116">See also</span></span>

- [<span data-ttu-id="6100a-117">ICorProfilerInfo4 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6100a-117">ICorProfilerInfo4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)
- [<span data-ttu-id="6100a-118">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="6100a-118">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="6100a-119">Profilace</span><span class="sxs-lookup"><span data-stu-id="6100a-119">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
