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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 19288b5631fea8865530f936ac6d77c0286ee169
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61791662"
---
# <a name="icorprofilerinfo2getgenerationbounds-method"></a>ICorProfilerInfo2::GetGenerationBounds – metoda
Získá oblastí paměti, které jsou segmenty haldy, které společně tvoří různých generací kolekce uvolnění paměti.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetGenerationBounds(  
    [in]  ULONG cObjectRanges,  
    [out] ULONG *pcObjectRanges,  
    [out, size_is(cObjectRanges), length_is(*pcObjectRanges)] COR_PRF_GC_GENERATION_RANGE ranges[]);  
```  
  
## <a name="parameters"></a>Parametry  
 `cObjectRanges`  
 [in] Počet prvků přidělenou volajícím pro `ranges` pole.  
  
 `pcObjectRanges`  
 [out] Ukazatel na celé číslo, který určuje celkový počet rozsahů, některé nebo všechny z nich, vrátí `ranges` pole.  
  
 `ranges`  
 [out] Pole [cor_prf_gc_generation_range –](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-range-structure.md) struktury, z nichž každý popisuje rozsah (bloku) paměti v rámci ke generaci, kterou provádí uvolňování paměti.  
  
## <a name="remarks"></a>Poznámky  
 `GetGenerationBounds` Metodu lze volat z jakékoli zpětného volání profileru, za předpokladu, že uvolňování paměti není v průběhu. To znamená, může být volána z jakékoli zpětného volání s výjimkou těch, ke kterým dochází mezi [ICorProfilerCallback2::GarbageCollectionStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionstarted-method.md) a [ICorProfilerCallback2::GarbageCollectionFinished](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md).  
  
 Většina posunutí generací probíhá během uvolnění paměti. Generace rozrůstat mezi kolekcí, ale obecně není pohyb. Proto zajímá nejvíce místa, kde volání `GetGenerationBounds` v `ICorProfilerCallback2::GarbageCollectionStarted` a `ICorProfilerCallback2::GarbageCollectionFinished`.  
  
 Při spuštění programu některé objekty se přidělují modulem common language runtime (CLR), obvykle v generacích 3 a 0. Proto době spravovaný kód začne provádět tyto generace již obsahuje objekty. Obvykle bude prázdný, s výjimkou fiktivní objekty, které jsou generovány pomocí systému uvolňování paměti generace 1 a 2. (Velikost fiktivní objektů je 12 bajtů v implementacích 32bitová verze modulu CLR, velikost je větší v implementacích 64bitová verze) Můžete si také prohlédnout rozsahy 2. generace, které jsou uvnitř modulů vytvářených Native Image Generator (NGen.exe). V takovém případě objekty v 2. generace jsou *zmrazené objekty*, které jsou přiděleny po spuštění NGen.exe, nikoli podle systému uvolňování paměti.  
  
 Tato funkce využívá volající – přidělené vyrovnávací paměti.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerInfo – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [ICorProfilerInfo2 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
- [Rozhraní pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [Profilace](../../../../docs/framework/unmanaged-api/profiling/index.md)
