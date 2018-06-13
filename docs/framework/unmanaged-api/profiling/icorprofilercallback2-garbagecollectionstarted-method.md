---
title: ICorProfilerCallback2::GarbageCollectionStarted – metoda
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9a447dca98e5010163d5cc5f4f3da4333f4cdf7d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33455267"
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
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICorProfilerCallback – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [ICorProfilerCallback2 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
