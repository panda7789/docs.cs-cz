---
title: "ICorProfilerCallback2::SurvivingReferences – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback2.SurvivingReferences
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback2::SurvivingReferences
helpviewer_keywords:
- ICorProfilerCallback2::SurvivingReferences method [.NET Framework profiling]
- SurvivingReferences method [.NET Framework profiling]
ms.assetid: f165200e-3a91-47f7-88fc-13ff10c8babc
topic_type: apiref
caps.latest.revision: "16"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 3764bfb79b39af897600202e8bc0f2ffbc4da95b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilercallback2survivingreferences-method"></a>ICorProfilerCallback2::SurvivingReferences – metoda
Sestavy rozložení objektů v haldě v důsledku uvolnění paměti kompresi.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT SurvivingReferences(  
    [in] ULONG  cSurvivingObjectIDRanges,  
    [in, size_is(cSurvivingObjectIDRanges)] ObjectID  
                objectIDRangeStart[] ,  
    [in, size_is(cSurvivingObjectIDRanges)] ULONG  
                cObjectIDRangeLength[] );  
```  
  
#### <a name="parameters"></a>Parametry  
 `cSurvivingObjectIDRanges`  
 [v] Počet bloků souvislý objektů, které zůstal naživu v důsledku uvolnění paměti kompresi. To znamená, hodnota `cSurvivingObjectIDRanges` je velikost `objectIDRangeStart` a `cObjectIDRangeLength` maticových, které úložiště `ObjectID` a délky, v uvedeném pořadí, pro každý blok objektů.  
  
 Následující dva argumenty `SurvivingReferences` jsou paralelní pole. Jinými slovy `objectIDRangeStart` a `cObjectIDRangeLength` na stejný blok souvislý objektů, které se týkají.  
  
 `objectIDRangeStart`  
 [v] Pole `ObjectID` hodnoty, z nichž každý je adresa počáteční blok souvislý, live objekty v paměti.  
  
 `cObjectIDRangeLength`  
 [v] Pole celých čísel, z nichž každý je velikost bloku hostujícího souvislý objektů v paměti.  
  
 Velikost je zadán pro každý blok, který se odkazuje v `objectIDRangeStart` pole.  
  
## <a name="remarks"></a>Poznámky  
  
> [!IMPORTANT]
>  Tato metoda sestavy velikosti jako `MAX_ULONG` pro objekty, které jsou větší než 4 GB na 64bitových platformách. Pro objekty, které jsou větší než 4 GB, použijte [icorprofilercallback4::survivingreferences2 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-survivingreferences2-method.md) metoda místo.  
  
 Elementy `objectIDRangeStart` a `cObjectIDRangeLength` pole by měl být interpretován následujícím způsobem určit, zda objekt zůstal naživu uvolnění paměti. Předpokládáme, že `ObjectID` hodnotu (`ObjectID`) v rozmezí následující:  
  
 `ObjectIDRangeStart[i]` <= `ObjectID` < `ObjectIDRangeStart[i]` + `cObjectIDRangeLength[i]`  
  
 Pro všechny hodnotu `i` , je v následujícím rozsahu, objekt má zůstal naživu uvolnění paměti:  
  
 0 <= `i` < `cSurvivingObjectIDRanges`  
  
 Uvolnění paměti kompresi získá paměť obsazená "neaktivní" objekty, ale není compact toto uvolněné místo. V důsledku toho se vrátí halda paměti, ale žádné "živé" objekty přesunou.  
  
 Modul CLR (CLR) volá `SurvivingReferences` pro kompresi jiné kolekce. Pro komprimaci kolekce [icorprofilercallback::movedreferences –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-movedreferences-method.md) nazývá místo. Uvolňování paměti jednom může být komprimaci pro jedna generace a bez kompresi pro jinou. Pro kolekci paměti na žádné konkrétní generování profileru obdrží, buď `SurvivingReferences` zpětného volání nebo `MovedReferences` zpětného volání, ale ne obojí.  
  
 Více `SurvivingReferences` zpětná volání může být přijata během konkrétní uvolňování kvůli omezené interní ukládání do vyrovnávací paměti, více vláken, vytváření sestav v případě uvolňování paměti serveru a z jiných důvodů. V případě více zpětných volání během uvolňování paměti, je kumulativní informace – všechny odkazy, které jsou hlášeny v žádném `SurvivingReferences` zpětného volání, zůstanou platné i po uvolnění paměti.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Icorprofilercallback – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [Icorprofilercallback2 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)  
 [Survivingreferences2 – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-survivingreferences2-method.md)
