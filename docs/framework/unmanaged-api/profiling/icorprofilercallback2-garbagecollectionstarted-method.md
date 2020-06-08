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
ms.openlocfilehash: f025f4c0bc0ec8e11decddcdf64be50f68955266
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84499802"
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
 pro Celkový počet položek v `generationCollected` poli.  
  
 `generationCollected`  
 pro Pole logických hodnot, které jsou `true` v případě, že je kolekce, která odpovídá indexu pole, shromažďována tímto uvolňováním paměti; v opačném případě `false` .  
  
 Pole je indexováno hodnotou [COR_PRF_GC_GENERATION](cor-prf-gc-generation-enumeration.md) výčtu, což označuje generaci.  
  
 `reason`  
 pro Hodnota výčtu [COR_PRF_GC_REASON](cor-prf-gc-reason-enumeration.md) , která označuje důvod vystavení uvolňování paměti.  
  
## <a name="remarks"></a>Poznámky  
 Všechna zpětná volání, která se týkají tohoto uvolňování paměti, proběhnou mezi `GarbageCollectionStarted` zpětným voláním a odpovídajícím voláním [ICorProfilerCallback2:: GarbageCollectionFinished –](icorprofilercallback2-garbagecollectionfinished-method.md) . Tato zpětná volání nemusí být ve stejném vlákně.  
  
 Profiler je bezpečně kontrolovat objekty v původních umístěních během `GarbageCollectionStarted` zpětného volání. Systém uvolňování paměti začne přesouvat objekty po návratu z `GarbageCollectionStarted` . Po návratu profileru z tohoto zpětného volání by měl Profiler považovat všechna ID objektů za neplatnou, dokud neobdrží `ICorProfilerCallback2::GarbageCollectionFinished` zpětné volání.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerCallback – rozhraní](icorprofilercallback-interface.md)
- [ICorProfilerCallback2 – rozhraní](icorprofilercallback2-interface.md)
