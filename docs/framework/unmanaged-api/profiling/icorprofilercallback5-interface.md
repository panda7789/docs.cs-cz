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
ms.openlocfilehash: 338bc10e02ceba5fb38c70088c4151271fca9b2d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33454402"
---
# <a name="icorprofilercallback5-interface"></a><span data-ttu-id="bff11-102">ICorProfilerCallback5 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="bff11-102">ICorProfilerCallback5 Interface</span></span>
<span data-ttu-id="bff11-103">Doplňuje informace, které pomohou určit úplnou uzavření živé objekty, použije se s profileru [icorprofilercallback::rootreferences –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md) nebo [icorprofilercallback2::rootreferences2 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md)metoda společně s [icorprofilercallback::objectreferences –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md) a [conditionalweaktableelementreferences –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback5-conditionalweaktableelementreferences-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="bff11-103">Supplements information to help a profiler identify the full closure of live objects, when used with either the [ICorProfilerCallback::RootReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-rootreferences-method.md) or [ICorProfilerCallback2::RootReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md) method together with the [ICorProfilerCallback::ObjectReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md) and [ConditionalWeakTableElementReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback5-conditionalweaktableelementreferences-method.md) methods.</span></span>  
  
 <span data-ttu-id="bff11-104">`ICorProfilerCallback5` musí být implementované spravované paměti profileru k odběru oznámení týkající se závislé obslužné rutiny.</span><span class="sxs-lookup"><span data-stu-id="bff11-104">`ICorProfilerCallback5` must be implemented by a managed memory profiler to subscribe to notifications related to dependent handles.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bff11-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="bff11-105">Remarks</span></span>  
  
## <a name="methods"></a><span data-ttu-id="bff11-106">Metody</span><span class="sxs-lookup"><span data-stu-id="bff11-106">Methods</span></span>  
  
|<span data-ttu-id="bff11-107">Metoda</span><span class="sxs-lookup"><span data-stu-id="bff11-107">Method</span></span>|<span data-ttu-id="bff11-108">Popis</span><span class="sxs-lookup"><span data-stu-id="bff11-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="bff11-109">ConditionalWeakTableElementReferences – metoda</span><span class="sxs-lookup"><span data-stu-id="bff11-109">ConditionalWeakTableElementReferences Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback5-conditionalweaktableelementreferences-method.md)|<span data-ttu-id="bff11-110">Identifikuje přechodné uzavření objekty odkazují tyto kořenové adresáře prostřednictvím i odkazy na pole přímé členy a prostřednictvím `ConditionalWeakTable` závislosti.</span><span class="sxs-lookup"><span data-stu-id="bff11-110">Identifies the transitive closure of objects referenced by those roots through both direct member field references and through `ConditionalWeakTable` dependencies.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="bff11-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="bff11-111">Requirements</span></span>  
 <span data-ttu-id="bff11-112">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bff11-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bff11-113">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="bff11-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="bff11-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bff11-114">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bff11-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="bff11-115">See Also</span></span>  
 [<span data-ttu-id="bff11-116">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="bff11-116">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="bff11-117">ICorProfilerCallback2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="bff11-117">ICorProfilerCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
