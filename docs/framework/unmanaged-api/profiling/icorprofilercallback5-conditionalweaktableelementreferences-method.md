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
ms.openlocfilehash: 08b35dd1744dbbb64d202718b61a9db5684d3bc3
ms.sourcegitcommit: 4735bb7741555bcb870d7b42964d3774f4897a6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/30/2019
ms.locfileid: "66380366"
---
# <a name="icorprofilercallback5conditionalweaktableelementreferences-method"></a>ICorProfilerCallback5::ConditionalWeakTableElementReferences – metoda

Identifikuje přechodné uzavření objekty odkazují tyto kořenové adresáře prostřednictvím oba odkazy na pole přímé členy a prostřednictvím `ConditionalWeakTable` závislosti.

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
[in] Počet prvků v `keyRefIds`, `valueRefIds`, a `rootIds` pole.

`keyRefIds`\
[in] ID objektů, z nichž každý obsahuje pole `ObjectID` pro primární element v páru závislý popisovač.

`valueRefIds`\
[in] ID objektů, z nichž každý obsahuje pole `ObjectID` pro sekundární element v páru závislý popisovač. (`keyRefIds[i]` udržuje `valueRefIds[i]` zachování připojení.)

`rootIds`\
[in] Pole `GCHandleID` hodnoty, které odkazují na celé číslo, které obsahuje další informace o kořenové kolekce uvolnění paměti.

Žádná z `ObjectID` hodnot vrácených `ConditionalWeakTableElementReferences` metoda jsou platné během zpětného volání, protože probíhá přesun objektů ze starého do nového umístění může být systému uvolňování paměti. Proto by se neměly pokoušet profilery pro kontrolu objektů během `ConditionalWeakTableElementReferences` volání. Na `GarbageCollectionFinished`přesunuly taky všechny objekty do nového umístění a se obvykle provádí kontroly.

## <a name="example"></a>Příklad

Následující příklad kódu ukazuje, jak implementovat [icorprofilercallback5 –](icorprofilercallback5-interface.md) a použít tuto metodu.

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

Profiler pro rozhraní .NET Framework 4.5 nebo novější verze implementuje [icorprofilercallback5 –](icorprofilercallback5-interface.md) rozhraní a záznamů závislosti určené `ConditionalWeakTableElementReferences` metody. `ICorProfilerCallback5` poskytuje kompletní sadu závislosti mezi živé objekty reprezentována `ConditionalWeakTable` položky. Tyto závislosti a člena pole určené odkazy [ICorProfilerCallback::ObjectReferences](icorprofilercallback-objectreferences-method.md) metoda povolit spravovaný profiler se vygenerovat graf úplný objekt živých objektů.

## <a name="requirements"></a>Požadavky

**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).

**Záhlaví:** CorProf.idl, CorProf.h

**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]

## <a name="see-also"></a>Viz také:

- [ICorProfilerCallback5 – rozhraní](icorprofilercallback5-interface.md)
