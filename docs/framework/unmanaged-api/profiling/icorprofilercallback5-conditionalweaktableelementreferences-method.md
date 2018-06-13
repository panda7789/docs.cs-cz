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
- CondiitonalWeakTableElementReferences
helpviewer_keywords:
- ConditionalWeakTableElementReferences method, ICorProfilerCallback5 interface [.NET Framework profiling]
- ICorProfilerCallback5::ConditionalWeakTableElementReferences method [.NET Framework profiling]
ms.assetid: 532c7a02-a9de-4cea-bb2b-7f470da594de
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4ee3c3302d77bcc7b807c01ccb5bab172153ddda
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33459948"
---
# <a name="icorprofilercallback5conditionalweaktableelementreferences-method"></a>ICorProfilerCallback5::ConditionalWeakTableElementReferences – metoda
Identifikuje přechodné uzavření objekty odkazují tyto kořenové adresáře prostřednictvím i odkazy na pole přímé členy a prostřednictvím `ConditionalWeakTable` závislosti.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT ConditionalWeakTableElementReferences(     [in]                     ULONG    cRootRefs,     [in, size_is(cRootRefs)] ObjectID keyRefIds[],     [in, size_is(cRootRefs)] ObjectID valueRefIds[],     [in, size_is(cRootRefs)] GCHandleID rootIds[]);};  
```  
  
#### <a name="parameters"></a>Parametry  
 `cRootRefs`  
 [v] Počet elementů ve `keyRefIds`, `valueRefIds`, a `rootIds` pole.  
  
 `keyRefIds`  
 [v] Pole ID objektů, z nichž každý obsahuje `ObjectID` primární elementu v páru závislé popisovač.  
  
 `valueRefIds`  
 [v] Pole ID objektů, z nichž každý obsahuje `ObjectID` sekundární elementu v páru závislé popisovač. (`keyRefIds[i]` udržuje `valueRefIds[i]` zachování připojení.)  
  
 `rootIds`  
 [v] Pole `GCHandleID` hodnoty, které odkazují na celé číslo, které obsahuje další informace o kořenové kolekce paměti.  
  
 Žádná z `ObjectID` hodnot vrácených `ConditionalWeakTableElementReferences` metoda jsou platné během zpětného volání sebe, protože uvolňování paměti může být přesouvá objekty ze starého na nové umístění. Proto profilery neměli zkontrolovat objekty během `ConditionalWeakTableElementReferences` volání. V `GarbageCollectionFinished`, všechny objekty byly přesunuty do nového umístění a může provést kontroly.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje, jak implementovat [icorprofilercallback5 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback5-interface.md) a použít tuto metodu.  
  
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
  
## <a name="remarks"></a>Poznámky  
 Profileru pro [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)] nebo novější verze implementuje [icorprofilercallback5 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback5-interface.md) rozhraní a záznamy závislosti určeného `ConditionalWeakTableElementReferences` metoda. `ICorProfilerCallback5` poskytuje kompletní sadu závislosti mezi živé objekty reprezentována `ConditionalWeakTable` položky. Tyto závislosti a člen pole určeného odkazy [icorprofilercallback::objectreferences –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md) metoda povolit spravované profileru ke generování grafu úplné objektu objektů za provozu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICorProfilerCallback5 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback5-interface.md)
