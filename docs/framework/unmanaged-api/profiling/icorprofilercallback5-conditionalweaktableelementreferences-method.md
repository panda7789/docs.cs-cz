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
# <a name="icorprofilercallback5conditionalweaktableelementreferences-method"></a>ICorProfilerCallback5::ConditionalWeakTableElementReferences – metoda

Určuje přenosný uzávěr objektů, na které odkazují tyto kořeny, prostřednictvím odkazů na přímé členské pole a prostřednictvím závislostí `ConditionalWeakTable`.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT ConditionalWeakTableElementReferences(
     [in]                     ULONG    cRootRefs,
     [in, size_is(cRootRefs)] ObjectID keyRefIds[],
     [in, size_is(cRootRefs)] ObjectID valueRefIds[],
     [in, size_is(cRootRefs)] GCHandleID rootIds[]
);
```

## <a name="parameters"></a>Parametry

`cRootRefs`\
pro Počet prvků v polích `keyRefIds`, `valueRefIds`a `rootIds`.

`keyRefIds`\
pro Pole ID objektů, z nichž každý obsahuje `ObjectID` pro primární element v páru závislých popisovačů.

`valueRefIds`\
pro Pole ID objektů, z nichž každý obsahuje `ObjectID` pro sekundární prvek v páru závislých popisovačů. (`keyRefIds[i]` udržuje `valueRefIds[i]` Alive.)

`rootIds`\
pro Pole hodnot `GCHandleID`, které odkazují na celé číslo, které obsahuje další informace o kořenu uvolňování paměti.

Žádná z hodnot `ObjectID` vrácených metodou `ConditionalWeakTableElementReferences` není platná v rámci samotného zpětného volání, protože systém uvolňování paměti může být v procesu přesunu objektů ze starých do nových umístění. Proto by se profilery neměly pokoušet prozkoumat objekty během volání `ConditionalWeakTableElementReferences`. V `GarbageCollectionFinished`byly všechny objekty přesunuty do jejich nových umístění a kontrola může být dokončena.

## <a name="example"></a>Příklad

Následující příklad kódu ukazuje, jak implementovat [ICorProfilerCallback5 –](icorprofilercallback5-interface.md) a použít tuto metodu.

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

## <a name="remarks"></a>Poznámky

Profiler pro .NET Framework 4,5 nebo novější verze implementuje rozhraní [ICorProfilerCallback5 –](icorprofilercallback5-interface.md) a zaznamenává závislosti určené metodou `ConditionalWeakTableElementReferences`. `ICorProfilerCallback5` poskytuje kompletní sadu závislostí mezi živými objekty reprezentovanými `ConditionalWeakTable`mi položkami. Tyto závislosti a odkazy na pole členů určené metodou [ICorProfilerCallback:: objectReferences –](icorprofilercallback-objectreferences-method.md) umožňují spravovanému profileru generovat úplný objekt grafu živých objektů.

## <a name="requirements"></a>Požadavky

**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).

**Hlavička:** CorProf. idl, CorProf. h

**Verze .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]

## <a name="see-also"></a>Viz také:

- [ICorProfilerCallback5 – rozhraní](icorprofilercallback5-interface.md)
