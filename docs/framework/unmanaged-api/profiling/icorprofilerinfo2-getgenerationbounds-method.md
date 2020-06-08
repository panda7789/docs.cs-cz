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
ms.openlocfilehash: 2e6e3a6432d6568532a5f5b9676b5f130eb83d0b
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502883"
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
 pro Počet prvků přidělených volajícím pro `ranges` pole.  
  
 `pcObjectRanges`  
 mimo Ukazatel na celé číslo, které určuje celkový počet rozsahů, některé nebo všechny, které budou vráceny v `ranges` poli.  
  
 `ranges`  
 mimo Pole struktur [COR_PRF_GC_GENERATION_RANGE](cor-prf-gc-generation-range-structure.md) , z nichž každý popisuje rozsah (tj. blok) paměti v rámci generace, která je podchází uvolňování paměti.  
  
## <a name="remarks"></a>Poznámky  
 `GetGenerationBounds`Metodu lze volat z jakéhokoli zpětného volání profileru za předpokladu, že uvolňování paměti neprobíhá.

 Při uvolňování paměti dojde k většině posunutí generací. Generace se můžou zvětšovat mezi kolekcemi, ale obecně se nepřesouvá. Proto nejzajímavější místa pro volání `GetGenerationBounds` jsou v `ICorProfilerCallback2::GarbageCollectionStarted` a `ICorProfilerCallback2::GarbageCollectionFinished` .  
  
 Během spouštění programu jsou některé objekty přiděleny samotným modulem CLR (Common Language Runtime), obecně v generacích 3 a 0. Proto se v době spuštění spravovaného kódu bude tato generace již obsahovat. Generace 1 a 2 budou normálně prázdné, s výjimkou fiktivních objektů, které jsou generovány systémem uvolňování paměti. (Velikost fiktivních objektů je 12 bajtů v 32 bitových implementacích CLR; velikost je větší v 64 implementacích.) Můžete se také podívat na rozsahy generace 2, které jsou uvnitř modulů generovaných generátorem nativních imagí (NGen. exe). V tomto případě jsou objekty v generaci 2 *zmrazeny objekty*, které jsou přiděleny při spuštění nástroje Ngen. exe, nikoli systémem uvolňování paměti.  
  
 Tato funkce používá vyrovnávací paměti přidělené volajícím.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerInfo – rozhraní](icorprofilerinfo-interface.md)
- [ICorProfilerInfo2 – rozhraní](icorprofilerinfo2-interface.md)
- [Rozhraní pro profilaci](profiling-interfaces.md)
- [Profilace](index.md)
