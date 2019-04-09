---
title: ICorProfilerCallback2::SurvivingReferences – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback2.SurvivingReferences
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback2::SurvivingReferences
helpviewer_keywords:
- ICorProfilerCallback2::SurvivingReferences method [.NET Framework profiling]
- SurvivingReferences method [.NET Framework profiling]
ms.assetid: f165200e-3a91-47f7-88fc-13ff10c8babc
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: da06ce49415317393b3489c2b8f97afc58f7c83b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59191299"
---
# <a name="icorprofilercallback2survivingreferences-method"></a>ICorProfilerCallback2::SurvivingReferences – metoda
Ohlásí rozložení objektů v haldě v důsledku uvolnění nekompaktním.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT SurvivingReferences(  
    [in] ULONG  cSurvivingObjectIDRanges,  
    [in, size_is(cSurvivingObjectIDRanges)] ObjectID  
                objectIDRangeStart[] ,  
    [in, size_is(cSurvivingObjectIDRanges)] ULONG  
                cObjectIDRangeLength[] );  
```  
  
## <a name="parameters"></a>Parametry  
 `cSurvivingObjectIDRanges`  
 [in] Počet bloků souvislých objektů, které zůstat naživu při uvolňování nekompaktním v důsledku. To znamená, že hodnota `cSurvivingObjectIDRanges` je velikost `objectIDRangeStart` a `cObjectIDRangeLength` pole, které úložiště `ObjectID` a délku, pro každý blok objektů.  
  
 Následující dva argumenty `SurvivingReferences` jsou paralelní pole. Jinými slovy `objectIDRangeStart` a `cObjectIDRangeLength` týkají stejný blok souvislé objektů.  
  
 `objectIDRangeStart`  
 [in] Pole `ObjectID` hodnot, z nichž každý je počáteční adresa blok souvislé, živé objekty v paměti.  
  
 `cObjectIDRangeLength`  
 [in] Pole celých čísel, z nichž každý je velikost bloku zbývající souvislých objektů v paměti.  
  
 Zadat velikost pro každý blok, na který odkazuje `objectIDRangeStart` pole.  
  
## <a name="remarks"></a>Poznámky  
  
> [!IMPORTANT]
>  Tato metoda oznamuje velikosti jako `MAX_ULONG` pro objekty, které jsou větší než 4 GB na 64bitových platformách. Pro objekty, které jsou větší než 4 GB, použijte [icorprofilercallback4::survivingreferences2 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-survivingreferences2-method.md) metoda místo.  
  
 Prvky `objectIDRangeStart` a `cObjectIDRangeLength` pole by měl být interpretován takto k určení, zda objekt zůstat naživu kolekce uvolnění paměti. Předpokládejme, že `ObjectID` hodnotu (`ObjectID`) najdete v následujícím rozsahu:  
  
 `ObjectIDRangeStart[i]` <= `ObjectID` < `ObjectIDRangeStart[i]` + `cObjectIDRangeLength[i]`  
  
 Jakoukoli hodnotu z `i` , který je v následujícím rozsahu, objekt má zůstat naživu při uvolňování paměti kolekce:  
  
 0 <= `i` < `cSurvivingObjectIDRanges`  
  
 Uvolnění nekompaktním uvolňuje paměť obsazenou neživými "" objekty, ale ne compact toto uvolněné místo. V důsledku toho paměti se vrátí do haldy, ale žádné objekty "živé" přesunou.  
  
 Common language runtime (CLR) zavolá `SurvivingReferences` pro nekompaktním kolekce uvolnění paměti. Pro uvolnění komprimaci [icorprofilercallback::movedreferences –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-movedreferences-method.md) je použita místo ní. Jeden uvolňování paměti může být komprimaci pro jeden generování a nekompaktním dalších. Pro uvolnění paměti na žádné konkrétní generování, profiler obdrží, buď `SurvivingReferences` zpětného volání nebo `MovedReferences` zpětné volání, ale ne obojí.  
  
 Více `SurvivingReferences` zpětná volání může přijmout během konkrétní uvolňování paměti, z důvodu omezené vnitřní vyrovnávací paměť, více vláken reporting v případě uvolnění paměti serveru a z jiných důvodů. V případě více zpětných volání během uvolňování paměti je kumulativní informace – všechny odkazy, které jsou hlášeny v libovolném `SurvivingReferences` zpětného volání byly zachovány při uvolnění paměti.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerCallback – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [ICorProfilerCallback2 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)
- [SurvivingReferences2 – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-survivingreferences2-method.md)
