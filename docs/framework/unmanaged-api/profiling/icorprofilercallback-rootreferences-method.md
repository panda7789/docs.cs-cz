---
title: "ICorProfilerCallback::RootReferences – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.RootReferences
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::RootReferences
helpviewer_keywords:
- RootReferences method [.NET Framework profiling]
- ICorProfilerCallback::RootReferences method [.NET Framework profiling]
ms.assetid: dbdf853b-d1a4-4828-8ef7-53d121d8e6ae
topic_type: apiref
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: dd057538450deeb46a72178c725103e04a8dd126
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallbackrootreferences-method"></a>ICorProfilerCallback::RootReferences – metoda
Upozorní profileru s informacemi o odkazů na kořenový po uvolnění paměti.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT RootReferences(  
    [in] ULONG    cRootRefs,  
    [in, size_is(cRootRefs)] ObjectID rootRefIds[] );  
```  
  
#### <a name="parameters"></a>Parametry  
 `cRootRefs`  
 [v] Počet odkazů v `rootRefIds` pole.  
  
 `rootRefIds`  
 [v] Pole ID objektů, které odkazují na statický objekt nebo objekt v zásobníku.  
  
## <a name="remarks"></a>Poznámky  
 Obě `RootReferences` a [icorprofilercallback2::rootreferences2 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md) se nazývají oznámit profileru. Profilery bude obvykle implementovat jednu nebo druhou, ale ne pomocí obou, protože předaná informace `RootReferences2` je nadmnožinou, je předaná `RootReferences`.  
  
 Je možné `rootRefIds` pole tak, aby obsahovala objekt s hodnotou null. Například všechny odkazy na objekty deklarované v zásobníku se považují za kořeny modulem garbage collector a bude vždy hlášena.  
  
 Vrácený objekt ID `RootReferences` nejsou platné během zpětného volání sebe, protože kolekce paměti může být uprostřed přesun objektů z původní adresy na nové adresy. Proto se profilery nesmíte pokoušet zkontrolovat objekty během `RootReferences` volání. Když [icorprofilercallback2::garbagecollectionfinished –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) je volána, všechny objekty byly přesunuty do nového umístění a může být prověřovány bezpečně.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICorProfilerCallback – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
