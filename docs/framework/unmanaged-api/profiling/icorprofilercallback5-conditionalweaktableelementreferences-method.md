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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 39ce72451f3a375f0cd3adb67a431162fc421a93
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57352201"
---
# <a name="icorprofilercallback5conditionalweaktableelementreferences-method"></a><span data-ttu-id="86d6c-102">ICorProfilerCallback5::ConditionalWeakTableElementReferences – metoda</span><span class="sxs-lookup"><span data-stu-id="86d6c-102">ICorProfilerCallback5::ConditionalWeakTableElementReferences Method</span></span>

<span data-ttu-id="86d6c-103">Identifikuje přechodné uzavření objekty odkazují tyto kořenové adresáře prostřednictvím oba odkazy na pole přímé členy a prostřednictvím `ConditionalWeakTable` závislosti.</span><span class="sxs-lookup"><span data-stu-id="86d6c-103">Identifies the transitive closure of objects referenced by those roots through both direct member field references and through `ConditionalWeakTable` dependencies.</span></span>

## <a name="syntax"></a><span data-ttu-id="86d6c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="86d6c-104">Syntax</span></span>

```cpp
HRESULT ConditionalWeakTableElementReferences(
     [in]                     ULONG    cRootRefs,
     [in, size_is(cRootRefs)] ObjectID keyRefIds[],
     [in, size_is(cRootRefs)] ObjectID valueRefIds[],
     [in, size_is(cRootRefs)] GCHandleID rootIds[]
);
```

## <a name="parameters"></a><span data-ttu-id="86d6c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="86d6c-105">Parameters</span></span>

`cRootRefs`\
<span data-ttu-id="86d6c-106">[in] Počet prvků v `keyRefIds`, `valueRefIds`, a `rootIds` pole.</span><span class="sxs-lookup"><span data-stu-id="86d6c-106">[in] The number of elements in the `keyRefIds`, `valueRefIds`, and `rootIds` arrays.</span></span>

`keyRefIds`\
<span data-ttu-id="86d6c-107">[in] ID objektů, z nichž každý obsahuje pole `ObjectID` pro primární element v páru závislý popisovač.</span><span class="sxs-lookup"><span data-stu-id="86d6c-107">[in] An array of object IDs, each of which contains the `ObjectID` for the primary element in the dependent handle pair.</span></span>

`valueRefIds`\
<span data-ttu-id="86d6c-108">[in] ID objektů, z nichž každý obsahuje pole `ObjectID` pro sekundární element v páru závislý popisovač.</span><span class="sxs-lookup"><span data-stu-id="86d6c-108">[in] An array of object IDs, each of which contains the `ObjectID` for the secondary element in the dependent handle pair.</span></span> <span data-ttu-id="86d6c-109">(`keyRefIds[i]` udržuje `valueRefIds[i]` zachování připojení.)</span><span class="sxs-lookup"><span data-stu-id="86d6c-109">(`keyRefIds[i]` keeps `valueRefIds[i]` alive.)</span></span>

`rootIds`\
<span data-ttu-id="86d6c-110">[in] Pole `GCHandleID` hodnoty, které odkazují na celé číslo, které obsahuje další informace o kořenové kolekce uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="86d6c-110">[in] An array of `GCHandleID` values that point to an integer that contains additional information about the garbage collection root.</span></span>

<span data-ttu-id="86d6c-111">Žádná z `ObjectID` hodnot vrácených `ConditionalWeakTableElementReferences` metoda jsou platné během zpětného volání, protože probíhá přesun objektů ze starého do nového umístění může být systému uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="86d6c-111">None of the `ObjectID` values returned by the `ConditionalWeakTableElementReferences` method are valid during the callback itself, because the garbage collector may be in the process of moving objects from old to new locations.</span></span> <span data-ttu-id="86d6c-112">Proto by se neměly pokoušet profilery pro kontrolu objektů během `ConditionalWeakTableElementReferences` volání.</span><span class="sxs-lookup"><span data-stu-id="86d6c-112">Therefore, profilers should not attempt to inspect objects during a `ConditionalWeakTableElementReferences` call.</span></span> <span data-ttu-id="86d6c-113">Na `GarbageCollectionFinished`přesunuly taky všechny objekty do nového umístění a se obvykle provádí kontroly.</span><span class="sxs-lookup"><span data-stu-id="86d6c-113">At `GarbageCollectionFinished`, all objects have been moved to their new locations, and inspection may be done.</span></span>

## <a name="example"></a><span data-ttu-id="86d6c-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="86d6c-114">Example</span></span>

<span data-ttu-id="86d6c-115">Následující příklad kódu ukazuje, jak implementovat [icorprofilercallback5 –](icorprofilercallback5-interface.md) a použít tuto metodu.</span><span class="sxs-lookup"><span data-stu-id="86d6c-115">The following code example demonstrates how to implement [ICorProfilerCallback5](icorprofilercallback5-interface.md) and use this method.</span></span>

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

## <a name="remarks"></a><span data-ttu-id="86d6c-116">Poznámky</span><span class="sxs-lookup"><span data-stu-id="86d6c-116">Remarks</span></span>

<span data-ttu-id="86d6c-117">Profiler pro [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)] nebo novější verze implementuje [icorprofilercallback5 –](icorprofilercallback5-interface.md) rozhraní a záznamů závislosti určené `ConditionalWeakTableElementReferences` metoda.</span><span class="sxs-lookup"><span data-stu-id="86d6c-117">A profiler for the [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)] or later versions implements the [ICorProfilerCallback5](icorprofilercallback5-interface.md) interface and records the dependencies specified by the `ConditionalWeakTableElementReferences` method.</span></span> <span data-ttu-id="86d6c-118">`ICorProfilerCallback5` poskytuje kompletní sadu závislosti mezi živé objekty reprezentována `ConditionalWeakTable` položky.</span><span class="sxs-lookup"><span data-stu-id="86d6c-118">`ICorProfilerCallback5` provides the complete set of dependencies among live objects represented by `ConditionalWeakTable` entries.</span></span> <span data-ttu-id="86d6c-119">Tyto závislosti a člena pole určené odkazy [ICorProfilerCallback::ObjectReferences](icorprofilercallback-objectreferences-method.md) metoda povolit spravovaný profiler se vygenerovat graf úplný objekt živých objektů.</span><span class="sxs-lookup"><span data-stu-id="86d6c-119">These dependencies and the member field references specified by the [ICorProfilerCallback::ObjectReferences](icorprofilercallback-objectreferences-method.md) method enable a managed profiler to generate the full object graph of live objects.</span></span>

## <a name="requirements"></a><span data-ttu-id="86d6c-120">Požadavky</span><span class="sxs-lookup"><span data-stu-id="86d6c-120">Requirements</span></span>

<span data-ttu-id="86d6c-121">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="86d6c-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="86d6c-122">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="86d6c-122">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="86d6c-123">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="86d6c-123">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="86d6c-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="86d6c-124">See also</span></span>

- [<span data-ttu-id="86d6c-125">ICorProfilerCallback5 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="86d6c-125">ICorProfilerCallback5 Interface</span></span>](icorprofilercallback5-interface.md)