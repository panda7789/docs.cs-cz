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
ms.openlocfilehash: c90c790c519cc0c422657e6e2d8040a365fbf48c
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76865776"
---
# <a name="icorprofilercallback2garbagecollectionstarted-method"></a>ICorProfilerCallback2::GarbageCollectionStarted – metoda
Oznamuje profileru kódu, že se spustilo uvolňování paměti.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GarbageCollectionStarted(  
    [in] int cGenerations,  
    [in, size_is(cGenerations), length_is(cGenerations)] BOOL generationCollected[],  
    [in] COR_PRF_GC_REASON reason);  
```  
  
## <a name="parameters"></a>Parametry  
 `cGenerations`  
 pro Celkový počet položek v poli `generationCollected`.  
  
 `generationCollected`  
 pro Pole logických hodnot, které jsou `true`, pokud je generace, která odpovídá indexu pole, shromažďována tímto uvolňováním paměti; v opačném případě `false`.  
  
 Pole je indexováno hodnotou [COR_PRF_GC_GENERATION](cor-prf-gc-generation-enumeration.md) výčtu, což označuje generaci.  
  
 `reason`  
 pro Hodnota výčtu [COR_PRF_GC_REASON](cor-prf-gc-reason-enumeration.md) , která označuje důvod vystavení uvolňování paměti.  
  
## <a name="remarks"></a>Poznámky  
 Všechna zpětná volání, která souvisí s tímto uvolňováním paměti, budou provedena mezi `GarbageCollectionStarted`ovým zpětným voláním a odpovídajícím voláním [ICorProfilerCallback2:: GarbageCollectionFinished –](icorprofilercallback2-garbagecollectionfinished-method.md) . Tato zpětná volání nemusí být ve stejném vlákně.  
  
 Profiler je bezpečně kontrolovat objekty v původních umístěních během `GarbageCollectionStarted` zpětného volání. Systém uvolňování paměti začne přesouvat objekty po návratu z `GarbageCollectionStarted`. Až se Profiler vrátí z tohoto zpětného volání, Profiler by měl považovat všechna ID objektů za neplatnou, dokud neobdrží zpětné volání `ICorProfilerCallback2::GarbageCollectionFinished`.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerCallback – rozhraní](icorprofilercallback-interface.md)
- [ICorProfilerCallback2 – rozhraní](icorprofilercallback2-interface.md)
