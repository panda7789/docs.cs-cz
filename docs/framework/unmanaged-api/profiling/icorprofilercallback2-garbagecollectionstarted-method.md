---
title: "ICorProfilerCallback2::GarbageCollectionStarted – metoda"
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
- ICorProfilerCallback2.GarbageCollectionStarted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback2::GarbageCollectionStarted
helpviewer_keywords:
- GarbageCollectionStarted method [.NET Framework profiling]
- ICorProfilerCallback2::GarbageCollectionStarted method [.NET Framework profiling]
ms.assetid: 44eef087-f21f-4fe2-b481-f8a0ee022e7d
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 3b721b990312f9acda5c9e0208f998793735d2cd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallback2garbagecollectionstarted-method"></a>ICorProfilerCallback2::GarbageCollectionStarted – metoda
Upozorní profileru kódu, aby bylo zahájeno uvolňování paměti.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GarbageCollectionStarted(  
    [in] int cGenerations,  
    [in, size_is(cGenerations), length_is(cGenerations)] BOOL generationCollected[],  
    [in] COR_PRF_GC_REASON reason);  
```  
  
#### <a name="parameters"></a>Parametry  
 `cGenerations`  
 [v] Celkový počet záznamů v `generationCollected` pole.  
  
 `generationCollected`  
 [v] Pole logické hodnoty, které jsou `true` Pokud generace, která odpovídá pole indexu je shromažďují tento uvolňování paměti; v opačném `false`.  
  
 Pole není indexované podle hodnotu [COR_PRF_GC_GENERATION](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-enumeration.md) výčtu, který označuje generování.  
  
 `reason`  
 [v] Hodnota [COR_PRF_GC_REASON](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-reason-enumeration.md) byla vyvolané výčet, který označuje z důvodu uvolnění paměti.  
  
## <a name="remarks"></a>Poznámky  
 Všechny zpětná volání, které se vztahují k této kolekci paměti dojde k mezi `GarbageCollectionStarted` zpětného volání a odpovídající [icorprofilercallback2::garbagecollectionfinished –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md) zpětného volání. Ve stejném vlákně, nemusí dojít tyto zpětných volání.  
  
 Je bezpečné pro přístup z profileru ke kontrole objekty do jejich původního umístění během `GarbageCollectionStarted` zpětného volání. Uvolňování paměti zahájíte přesunutí objekty po návratu z `GarbageCollectionStarted`. Po profileru vrátila z této zpětné volání, profileru měli zvážit všechna ID objektu je neplatná, dokud neobdrží `ICorProfilerCallback2::GarbageCollectionFinished` zpětného volání.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICorProfilerCallback – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [ICorProfilerCallback2 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
