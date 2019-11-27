---
title: ICorProfilerInfo2::GetGenerationBounds – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetGenerationBounds
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetGenerationBounds
helpviewer_keywords:
- ICorProfilerInfo2::GetGenerationBounds method [.NET Framework profiling]
- GetGenerationBounds method [.NET Framework profiling]
ms.assetid: 9c37185f-d1e0-4a6e-8b99-707f7df61d88
topic_type:
- apiref
ms.openlocfilehash: 11157bca2d0f0be2b9b9bc36c382188a43db22a9
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74433124"
---
# <a name="icorprofilerinfo2getgenerationbounds-method"></a>ICorProfilerInfo2::GetGenerationBounds – metoda
Získá oblasti paměti, které jsou segmenty haldy, které tvoří různé generace uvolňování paměti.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetGenerationBounds(  
    [in]  ULONG cObjectRanges,  
    [out] ULONG *pcObjectRanges,  
    [out, size_is(cObjectRanges), length_is(*pcObjectRanges)] COR_PRF_GC_GENERATION_RANGE ranges[]);  
```  
  
## <a name="parameters"></a>Parametry  
 `cObjectRanges`  
 pro Počet prvků přidělených volajícím pro pole `ranges`.  
  
 `pcObjectRanges`  
 mimo Ukazatel na celé číslo, které určuje celkový počet rozsahů, některé nebo všechny, které budou vráceny v poli `ranges`.  
  
 `ranges`  
 mimo Pole struktur [COR_PRF_GC_GENERATION_RANGE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-range-structure.md) , z nichž každý popisuje rozsah (tj. blok) paměti v rámci generace, která je podchází uvolňování paměti.  
  
## <a name="remarks"></a>Poznámky  
 Metodu `GetGenerationBounds` lze volat z jakéhokoli zpětného volání profileru za předpokladu, že uvolňování paměti neprobíhá.

 Při uvolňování paměti dojde k většině posunutí generací. Generace se můžou zvětšovat mezi kolekcemi, ale obecně se nepřesouvá. Nejzajímavější místa pro volání `GetGenerationBounds` jsou proto v `ICorProfilerCallback2::GarbageCollectionStarted` a `ICorProfilerCallback2::GarbageCollectionFinished`.  
  
 Během spouštění programu jsou některé objekty přiděleny samotným modulem CLR (Common Language Runtime), obecně v generacích 3 a 0. Proto se v době spuštění spravovaného kódu bude tato generace již obsahovat. Generace 1 a 2 budou normálně prázdné, s výjimkou fiktivních objektů, které jsou generovány systémem uvolňování paměti. (Velikost fiktivních objektů je 12 bajtů v 32 bitových implementacích CLR; velikost je větší v 64 implementacích.) Můžete se také podívat na rozsahy generace 2, které jsou uvnitř modulů generovaných generátorem nativních imagí (NGen. exe). V tomto případě jsou objekty v generaci 2 *zmrazeny objekty*, které jsou přiděleny při spuštění nástroje Ngen. exe, nikoli systémem uvolňování paměti.  
  
 Tato funkce používá vyrovnávací paměti přidělené volajícím.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerInfo – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [ICorProfilerInfo2 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
- [Rozhraní pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Profilace](../../../../docs/framework/unmanaged-api/profiling/index.md)
