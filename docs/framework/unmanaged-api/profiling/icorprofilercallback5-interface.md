---
title: ICorProfilerCallback5 – rozhraní
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback5
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback5
helpviewer_keywords:
- ICorProfilerCallback5 interface [.NET Framework profiling]
ms.assetid: 61d2e9ef-5f1f-4771-8847-239616e35d84
topic_type:
- apiref
ms.openlocfilehash: 02a690503d7b6323f19dcb66247d8a552b760b1c
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84499204"
---
# <a name="icorprofilercallback5-interface"></a><span data-ttu-id="276ad-102">ICorProfilerCallback5 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="276ad-102">ICorProfilerCallback5 Interface</span></span>
<span data-ttu-id="276ad-103">Doplňují informace, které pomůžou profileru identifikovat úplný uzávěr živých objektů při použití s metodou [ICorProfilerCallback:: RootReferences –](icorprofilercallback-rootreferences-method.md) nebo [ICorProfilerCallback2:: RootReferences2 –](icorprofilercallback2-rootreferences2-method.md) společně s metodami [ICorProfilerCallback:: objectReferences –](icorprofilercallback-objectreferences-method.md) a [ConditionalWeakTableElementReferences –](icorprofilercallback5-conditionalweaktableelementreferences-method.md) .</span><span class="sxs-lookup"><span data-stu-id="276ad-103">Supplements information to help a profiler identify the full closure of live objects, when used with either the [ICorProfilerCallback::RootReferences](icorprofilercallback-rootreferences-method.md) or [ICorProfilerCallback2::RootReferences2](icorprofilercallback2-rootreferences2-method.md) method together with the [ICorProfilerCallback::ObjectReferences](icorprofilercallback-objectreferences-method.md) and [ConditionalWeakTableElementReferences](icorprofilercallback5-conditionalweaktableelementreferences-method.md) methods.</span></span>  
  
 <span data-ttu-id="276ad-104">`ICorProfilerCallback5`musí být implementováno pomocí profileru spravované paměti pro přihlášení k odběru oznámení souvisejících s závislými popisovači.</span><span class="sxs-lookup"><span data-stu-id="276ad-104">`ICorProfilerCallback5` must be implemented by a managed memory profiler to subscribe to notifications related to dependent handles.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="276ad-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="276ad-105">Remarks</span></span>  
  
## <a name="methods"></a><span data-ttu-id="276ad-106">Metody</span><span class="sxs-lookup"><span data-stu-id="276ad-106">Methods</span></span>  
  
|<span data-ttu-id="276ad-107">Metoda</span><span class="sxs-lookup"><span data-stu-id="276ad-107">Method</span></span>|<span data-ttu-id="276ad-108">Description</span><span class="sxs-lookup"><span data-stu-id="276ad-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="276ad-109">ConditionalWeakTableElementReferences – metoda</span><span class="sxs-lookup"><span data-stu-id="276ad-109">ConditionalWeakTableElementReferences Method</span></span>](icorprofilercallback5-conditionalweaktableelementreferences-method.md)|<span data-ttu-id="276ad-110">Určuje přenosný uzávěr objektů, na které odkazují tyto kořeny, prostřednictvím přímých odkazů na pole členů a prostřednictvím `ConditionalWeakTable` závislostí.</span><span class="sxs-lookup"><span data-stu-id="276ad-110">Identifies the transitive closure of objects referenced by those roots through both direct member field references and through `ConditionalWeakTable` dependencies.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="276ad-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="276ad-111">Requirements</span></span>  
 <span data-ttu-id="276ad-112">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="276ad-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="276ad-113">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="276ad-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="276ad-114">**Verze .NET Framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="276ad-114">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="276ad-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="276ad-115">See also</span></span>

- [<span data-ttu-id="276ad-116">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="276ad-116">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="276ad-117">ICorProfilerCallback2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="276ad-117">ICorProfilerCallback2 Interface</span></span>](icorprofilercallback2-interface.md)
