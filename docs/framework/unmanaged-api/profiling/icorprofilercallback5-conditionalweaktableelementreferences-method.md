---
title: ICorProfilerCallback5::ConditionalWeakTableElementReferences – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback5.ConditionalWeakTableReferences
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ConditionalWeakTableElementReferences
helpviewer_keywords:
- ConditionalWeakTableElementReferences method, ICorProfilerCallback5 interface [.NET Framework profiling]
- ICorProfilerCallback5::ConditionalWeakTableElementReferences method [.NET Framework profiling]
ms.assetid: 532c7a02-a9de-4cea-bb2b-7f470da594de
topic_type:
- apiref
ms.openlocfilehash: ad721d28f6a7dc6ae0370ce10178990cb02fb9f9
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74430048"
---
# <a name="icorprofilercallback5conditionalweaktableelementreferences-method"></a><span data-ttu-id="2b4fc-102">ICorProfilerCallback5::ConditionalWeakTableElementReferences – metoda</span><span class="sxs-lookup"><span data-stu-id="2b4fc-102">ICorProfilerCallback5::ConditionalWeakTableElementReferences Method</span></span>

<span data-ttu-id="2b4fc-103">Určuje přenosný uzávěr objektů, na které odkazují tyto kořeny, prostřednictvím odkazů na přímé členské pole a prostřednictvím závislostí `ConditionalWeakTable`.</span><span class="sxs-lookup"><span data-stu-id="2b4fc-103">Identifies the transitive closure of objects referenced by those roots through both direct member field references and through `ConditionalWeakTable` dependencies.</span></span>

## <a name="syntax"></a><span data-ttu-id="2b4fc-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2b4fc-104">Syntax</span></span>

```cpp
HRESULT ConditionalWeakTableElementReferences(
     [in]                     ULONG    cRootRefs,
     [in, size_is(cRootRefs)] ObjectID keyRefIds[],
     [in, size_is(cRootRefs)] ObjectID valueRefIds[],
     [in, size_is(cRootRefs)] GCHandleID rootIds[]
);
```

## <a name="parameters"></a><span data-ttu-id="2b4fc-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2b4fc-105">Parameters</span></span>

`cRootRefs`\
<span data-ttu-id="2b4fc-106">pro Počet prvků v polích `keyRefIds`, `valueRefIds`a `rootIds`.</span><span class="sxs-lookup"><span data-stu-id="2b4fc-106">[in] The number of elements in the `keyRefIds`, `valueRefIds`, and `rootIds` arrays.</span></span>

`keyRefIds`\
<span data-ttu-id="2b4fc-107">pro Pole ID objektů, z nichž každý obsahuje `ObjectID` pro primární element v páru závislých popisovačů.</span><span class="sxs-lookup"><span data-stu-id="2b4fc-107">[in] An array of object IDs, each of which contains the `ObjectID` for the primary element in the dependent handle pair.</span></span>

`valueRefIds`\
<span data-ttu-id="2b4fc-108">pro Pole ID objektů, z nichž každý obsahuje `ObjectID` pro sekundární prvek v páru závislých popisovačů.</span><span class="sxs-lookup"><span data-stu-id="2b4fc-108">[in] An array of object IDs, each of which contains the `ObjectID` for the secondary element in the dependent handle pair.</span></span> <span data-ttu-id="2b4fc-109">(`keyRefIds[i]` udržuje `valueRefIds[i]` Alive.)</span><span class="sxs-lookup"><span data-stu-id="2b4fc-109">(`keyRefIds[i]` keeps `valueRefIds[i]` alive.)</span></span>

`rootIds`\
<span data-ttu-id="2b4fc-110">pro Pole hodnot `GCHandleID`, které odkazují na celé číslo, které obsahuje další informace o kořenu uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="2b4fc-110">[in] An array of `GCHandleID` values that point to an integer that contains additional information about the garbage collection root.</span></span>

<span data-ttu-id="2b4fc-111">Žádná z hodnot `ObjectID` vrácených metodou `ConditionalWeakTableElementReferences` není platná v rámci samotného zpětného volání, protože systém uvolňování paměti může být v procesu přesunu objektů ze starých do nových umístění.</span><span class="sxs-lookup"><span data-stu-id="2b4fc-111">None of the `ObjectID` values returned by the `ConditionalWeakTableElementReferences` method are valid during the callback itself, because the garbage collector may be in the process of moving objects from old to new locations.</span></span> <span data-ttu-id="2b4fc-112">Proto by se profilery neměly pokoušet prozkoumat objekty během volání `ConditionalWeakTableElementReferences`.</span><span class="sxs-lookup"><span data-stu-id="2b4fc-112">Therefore, profilers should not attempt to inspect objects during a `ConditionalWeakTableElementReferences` call.</span></span> <span data-ttu-id="2b4fc-113">V `GarbageCollectionFinished`byly všechny objekty přesunuty do jejich nových umístění a kontrola může být dokončena.</span><span class="sxs-lookup"><span data-stu-id="2b4fc-113">At `GarbageCollectionFinished`, all objects have been moved to their new locations, and inspection may be done.</span></span>

## <a name="example"></a><span data-ttu-id="2b4fc-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="2b4fc-114">Example</span></span>

<span data-ttu-id="2b4fc-115">Následující příklad kódu ukazuje, jak implementovat [ICorProfilerCallback5 –](icorprofilercallback5-interface.md) a použít tuto metodu.</span><span class="sxs-lookup"><span data-stu-id="2b4fc-115">The following code example demonstrates how to implement [ICorProfilerCallback5](icorprofilercallback5-interface.md) and use this method.</span></span>

```cpp
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

## <a name="remarks"></a><span data-ttu-id="2b4fc-116">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2b4fc-116">Remarks</span></span>

<span data-ttu-id="2b4fc-117">Profiler pro .NET Framework 4,5 nebo novější verze implementuje rozhraní [ICorProfilerCallback5 –](icorprofilercallback5-interface.md) a zaznamenává závislosti určené metodou `ConditionalWeakTableElementReferences`.</span><span class="sxs-lookup"><span data-stu-id="2b4fc-117">A profiler for the .NET Framework 4.5 or later versions implements the [ICorProfilerCallback5](icorprofilercallback5-interface.md) interface and records the dependencies specified by the `ConditionalWeakTableElementReferences` method.</span></span> <span data-ttu-id="2b4fc-118">`ICorProfilerCallback5` poskytuje kompletní sadu závislostí mezi živými objekty reprezentovanými `ConditionalWeakTable`mi položkami.</span><span class="sxs-lookup"><span data-stu-id="2b4fc-118">`ICorProfilerCallback5` provides the complete set of dependencies among live objects represented by `ConditionalWeakTable` entries.</span></span> <span data-ttu-id="2b4fc-119">Tyto závislosti a odkazy na pole členů určené metodou [ICorProfilerCallback:: objectReferences –](icorprofilercallback-objectreferences-method.md) umožňují spravovanému profileru generovat úplný objekt grafu živých objektů.</span><span class="sxs-lookup"><span data-stu-id="2b4fc-119">These dependencies and the member field references specified by the [ICorProfilerCallback::ObjectReferences](icorprofilercallback-objectreferences-method.md) method enable a managed profiler to generate the full object graph of live objects.</span></span>

## <a name="requirements"></a><span data-ttu-id="2b4fc-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2b4fc-120">Requirements</span></span>

<span data-ttu-id="2b4fc-121">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2b4fc-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="2b4fc-122">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="2b4fc-122">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="2b4fc-123">**Verze .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2b4fc-123">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="2b4fc-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2b4fc-124">See also</span></span>

- [<span data-ttu-id="2b4fc-125">ICorProfilerCallback5 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2b4fc-125">ICorProfilerCallback5 Interface</span></span>](icorprofilercallback5-interface.md)
