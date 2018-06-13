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
ms.openlocfilehash: 0cfac1304a3d60a418065e4fc2994705548eeac3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33458435"
---
# <a name="icorprofilerinfo2getgenerationbounds-method"></a>ICorProfilerInfo2::GetGenerationBounds – metoda
Získá oblasti paměti, které jsou segmenty haldě, které tvoří různé kolekce generace uvolňování paměti.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetGenerationBounds(  
    [in]  ULONG cObjectRanges,  
    [out] ULONG *pcObjectRanges,  
    [out, size_is(cObjectRanges), length_is(*pcObjectRanges)] COR_PRF_GC_GENERATION_RANGE ranges[]);  
```  
  
#### <a name="parameters"></a>Parametry  
 `cObjectRanges`  
 [v] Počet elementů přidělené pro volající funkcí `ranges` pole.  
  
 `pcObjectRanges`  
 [out] Ukazatel na celé číslo, který určuje celkový počet rozsahů, některé nebo všechny z nich, vrátí se `ranges` pole.  
  
 `ranges`  
 [out] Pole [cor_prf_gc_generation_range –](../../../../docs/framework/unmanaged-api/profiling/cor-prf-gc-generation-range-structure.md) struktury, z nichž každý popisuje rozsah (blok) paměti v generaci, kterou právě probíhá uvolňování paměti.  
  
## <a name="remarks"></a>Poznámky  
 `GetGenerationBounds` Metodu lze volat z jakékoli profileru zpětné volání, za předpokladu, že není v průběhu uvolňování paměti. To znamená, může být volána z jakékoli zpětného volání kromě těch, které se vyskytnou mezi [icorprofilercallback2::garbagecollectionstarted –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionstarted-method.md) a [icorprofilercallback2::garbagecollectionfinished –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-garbagecollectionfinished-method.md).  
  
 Většina s posunem generací probíhá během kolekce. Generace může růst mezi kolekcí, ale obecně není pohyb. Proto nejvíce zajímavé místech volat `GetGenerationBounds` v `ICorProfilerCallback2::GarbageCollectionStarted` a `ICorProfilerCallback2::GarbageCollectionFinished`.  
  
 Při spuštění programu některé objekty mají při přidělování modulem common language runtime (CLR) samostatně, obvykle v generace 3 a 0. Proto podle času spravovaný kód spustí provádění, tyto generace již obsahuje objekty. Generace 1 a 2 obvykle bude prázdný, s výjimkou fiktivní objekty, které jsou generovány modulem garbage collector. (Velikost fiktivní objektů je 12 bajtů v implementacích 32bitová verze modulu CLR, větší v implementacích 64-bit.) Můžete si také prohlédnout generace 2 rozsahy, které jsou uvnitř modulů vyprodukované generátor (NGen.exe). V tomto případě jsou objekty v generace 2 *pozastaveny objekty*, které jsou přiděleny při spuštění NGen.exe spíše než modulem garbage collector.  
  
 Tato funkce využívá volající přidělené vyrovnávací paměti.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICorProfilerInfo – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [ICorProfilerInfo2 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)  
 [Rozhraní pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [Profilace](../../../../docs/framework/unmanaged-api/profiling/index.md)
