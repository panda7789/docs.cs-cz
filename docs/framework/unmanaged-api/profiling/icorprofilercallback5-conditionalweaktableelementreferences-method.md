---
title: "ICorProfilerCallback5::ConditionalWeakTableElementReferences – metoda"
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
- ICorProfilerCallback5.ConditionalWeakTableReferences
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- CondiitonalWeakTableElementReferences
helpviewer_keywords:
- ConditionalWeakTableElementReferences method, ICorProfilerCallback5 interface [.NET Framework profiling]
- ICorProfilerCallback5::ConditionalWeakTableElementReferences method [.NET Framework profiling]
ms.assetid: 532c7a02-a9de-4cea-bb2b-7f470da594de
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 8cfe86ac7d0cd5b4a5c6adb9f12ffe9577b6e611
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallback5conditionalweaktableelementreferences-method"></a><span data-ttu-id="14bba-102">ICorProfilerCallback5::ConditionalWeakTableElementReferences – metoda</span><span class="sxs-lookup"><span data-stu-id="14bba-102">ICorProfilerCallback5::ConditionalWeakTableElementReferences Method</span></span>
<span data-ttu-id="14bba-103">Identifikuje přechodné uzavření objekty odkazují tyto kořenové adresáře prostřednictvím i odkazy na pole přímé členy a prostřednictvím `ConditionalWeakTable` závislosti.</span><span class="sxs-lookup"><span data-stu-id="14bba-103">Identifies the transitive closure of objects referenced by those roots through both direct member field references and through `ConditionalWeakTable` dependencies.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="14bba-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="14bba-104">Syntax</span></span>  
  
```  
HRESULT ConditionalWeakTableElementReferences(     [in]                     ULONG    cRootRefs,     [in, size_is(cRootRefs)] ObjectID keyRefIds[],     [in, size_is(cRootRefs)] ObjectID valueRefIds[],     [in, size_is(cRootRefs)] GCHandleID rootIds[]);};  
```  
  
#### <a name="parameters"></a><span data-ttu-id="14bba-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="14bba-105">Parameters</span></span>  
 `cRootRefs`  
 <span data-ttu-id="14bba-106">[v] Počet elementů ve `keyRefIds`, `valueRefIds`, a `rootIds` pole.</span><span class="sxs-lookup"><span data-stu-id="14bba-106">[in] The number of elements in the `keyRefIds`, `valueRefIds`, and `rootIds` arrays.</span></span>  
  
 `keyRefIds`  
 <span data-ttu-id="14bba-107">[v] Pole ID objektů, z nichž každý obsahuje `ObjectID` primární elementu v páru závislé popisovač.</span><span class="sxs-lookup"><span data-stu-id="14bba-107">[in] An array of object IDs, each of which contains the `ObjectID` for the primary element in the dependent handle pair.</span></span>  
  
 `valueRefIds`  
 <span data-ttu-id="14bba-108">[v] Pole ID objektů, z nichž každý obsahuje `ObjectID` sekundární elementu v páru závislé popisovač.</span><span class="sxs-lookup"><span data-stu-id="14bba-108">[in] An array of object IDs, each of which contains the `ObjectID` for the secondary element in the dependent handle pair.</span></span> <span data-ttu-id="14bba-109">(`keyRefIds[i]` udržuje `valueRefIds[i]` zachování připojení.)</span><span class="sxs-lookup"><span data-stu-id="14bba-109">(`keyRefIds[i]` keeps `valueRefIds[i]` alive.)</span></span>  
  
 `rootIds`  
 <span data-ttu-id="14bba-110">[v] Pole `GCHandleID` hodnoty, které odkazují na celé číslo, které obsahuje další informace o kořenové kolekce paměti.</span><span class="sxs-lookup"><span data-stu-id="14bba-110">[in] An array of `GCHandleID` values that point to an integer that contains additional information about the garbage collection root.</span></span>  
  
 <span data-ttu-id="14bba-111">Žádná z `ObjectID` hodnot vrácených `ConditionalWeakTableElementReferences` metoda jsou platné během zpětného volání sebe, protože uvolňování paměti může být přesouvá objekty ze starého na nové umístění.</span><span class="sxs-lookup"><span data-stu-id="14bba-111">None of the `ObjectID` values returned by the `ConditionalWeakTableElementReferences` method are valid during the callback itself, because the garbage collector may be in the process of moving objects from old to new locations.</span></span> <span data-ttu-id="14bba-112">Proto profilery neměli zkontrolovat objekty během `ConditionalWeakTableElementReferences` volání.</span><span class="sxs-lookup"><span data-stu-id="14bba-112">Therefore, profilers should not attempt to inspect objects during a `ConditionalWeakTableElementReferences` call.</span></span> <span data-ttu-id="14bba-113">V `GarbageCollectionFinished`, všechny objekty byly přesunuty do nového umístění a může provést kontroly.</span><span class="sxs-lookup"><span data-stu-id="14bba-113">At `GarbageCollectionFinished`, all objects have been moved to their new locations, and inspection may be done.</span></span>  
  
## <a name="example"></a><span data-ttu-id="14bba-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="14bba-114">Example</span></span>  
 <span data-ttu-id="14bba-115">Následující příklad kódu ukazuje, jak implementovat [icorprofilercallback5 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback5-interface.md) a použít tuto metodu.</span><span class="sxs-lookup"><span data-stu-id="14bba-115">The following code example demonstrates how to implement [ICorProfilerCallback5](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback5-interface.md) and use this method.</span></span>  
  
```  
HRESULT Callback5Impl::ConditionalWeakTableElementReferences(  
    ULONG      cRootRefs,  
    ObjectID   keyRefIds[],  
    ObjectID   valueRefIds[],  
    GCHandleID rootIds[])  
{  
    printf("Callback5Impl::ConditionalWeakTableElementReferences called\n");  
    for (unsigned int i = 0; i < cRootRefs; ++i)  
    {  
        // Save dependency to XML for later retrieval  
        PersistDependencyToXml(rootIds[i], keyRefIds[i], valueRefIds[i]);  
        // or store dependency to an internal map  
        m_cwt_deps->add_dep(rootIds[i], keyRefIds[i], valueRefIds[i]);  
        // or add arc to object graph  
        m_obj_graph->add_arc(keyRefIds[i], valueRefIds[i], rootIds[i]);  
    }  
    return S_OK;  
}  
```  
  
## <a name="remarks"></a><span data-ttu-id="14bba-116">Poznámky</span><span class="sxs-lookup"><span data-stu-id="14bba-116">Remarks</span></span>  
 <span data-ttu-id="14bba-117">Profileru pro [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)] nebo novější verze implementuje [icorprofilercallback5 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback5-interface.md) rozhraní a záznamy závislosti určeného `ConditionalWeakTableElementReferences` metoda.</span><span class="sxs-lookup"><span data-stu-id="14bba-117">A profiler for the [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)] or later versions implements the [ICorProfilerCallback5](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback5-interface.md) interface and records the dependencies specified by the `ConditionalWeakTableElementReferences` method.</span></span> <span data-ttu-id="14bba-118">`ICorProfilerCallback5`poskytuje kompletní sadu závislosti mezi živé objekty reprezentována `ConditionalWeakTable` položky.</span><span class="sxs-lookup"><span data-stu-id="14bba-118">`ICorProfilerCallback5` provides the complete set of dependencies among live objects represented by `ConditionalWeakTable` entries.</span></span> <span data-ttu-id="14bba-119">Tyto závislosti a člen pole určeného odkazy [icorprofilercallback::objectreferences –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md) metoda povolit spravované profileru ke generování grafu úplné objektu objektů za provozu.</span><span class="sxs-lookup"><span data-stu-id="14bba-119">These dependencies and the member field references specified by the [ICorProfilerCallback::ObjectReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md) method enable a managed profiler to generate the full object graph of live objects.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="14bba-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="14bba-120">Requirements</span></span>  
 <span data-ttu-id="14bba-121">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="14bba-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="14bba-122">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="14bba-122">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="14bba-123">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="14bba-123">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14bba-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="14bba-124">See Also</span></span>  
 [<span data-ttu-id="14bba-125">ICorProfilerCallback5 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="14bba-125">ICorProfilerCallback5 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback5-interface.md)
