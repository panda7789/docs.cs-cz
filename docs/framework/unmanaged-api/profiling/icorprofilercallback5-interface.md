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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e6481d647541af40b956c38a76d281ccb84e7c7f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54602543"
---
# <a name="icorprofilercallback5-interface"></a><span data-ttu-id="87fd2-102">ICorProfilerCallback5 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="87fd2-102">ICorProfilerCallback5 Interface</span></span>
<span data-ttu-id="87fd2-103">Doplňující informace, které pomůžou profiler identifikovat úplné ukončení živé objekty při použití s buď [ICorProfilerCallback::RootReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md) nebo [ICorProfilerCallback2::RootReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md)metody společně s [ICorProfilerCallback::ObjectReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md) a [conditionalweaktableelementreferences –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback5-conditionalweaktableelementreferences-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="87fd2-103">Supplements information to help a profiler identify the full closure of live objects, when used with either the [ICorProfilerCallback::RootReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md) or [ICorProfilerCallback2::RootReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md) method together with the [ICorProfilerCallback::ObjectReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md) and [ConditionalWeakTableElementReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback5-conditionalweaktableelementreferences-method.md) methods.</span></span>  
  
 <span data-ttu-id="87fd2-104">`ICorProfilerCallback5` musí být implementované spravované paměti profileru k odběru oznámení týkajících se závislé popisovače.</span><span class="sxs-lookup"><span data-stu-id="87fd2-104">`ICorProfilerCallback5` must be implemented by a managed memory profiler to subscribe to notifications related to dependent handles.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="87fd2-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="87fd2-105">Remarks</span></span>  
  
## <a name="methods"></a><span data-ttu-id="87fd2-106">Metody</span><span class="sxs-lookup"><span data-stu-id="87fd2-106">Methods</span></span>  
  
|<span data-ttu-id="87fd2-107">Metoda</span><span class="sxs-lookup"><span data-stu-id="87fd2-107">Method</span></span>|<span data-ttu-id="87fd2-108">Popis</span><span class="sxs-lookup"><span data-stu-id="87fd2-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="87fd2-109">ConditionalWeakTableElementReferences – metoda</span><span class="sxs-lookup"><span data-stu-id="87fd2-109">ConditionalWeakTableElementReferences Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback5-conditionalweaktableelementreferences-method.md)|<span data-ttu-id="87fd2-110">Identifikuje přechodné uzavření objekty odkazují tyto kořenové adresáře prostřednictvím oba odkazy na pole přímé členy a prostřednictvím `ConditionalWeakTable` závislosti.</span><span class="sxs-lookup"><span data-stu-id="87fd2-110">Identifies the transitive closure of objects referenced by those roots through both direct member field references and through `ConditionalWeakTable` dependencies.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="87fd2-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="87fd2-111">Requirements</span></span>  
 <span data-ttu-id="87fd2-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="87fd2-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="87fd2-113">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="87fd2-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="87fd2-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="87fd2-114">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87fd2-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="87fd2-115">See also</span></span>
- [<span data-ttu-id="87fd2-116">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="87fd2-116">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="87fd2-117">ICorProfilerCallback2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="87fd2-117">ICorProfilerCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
