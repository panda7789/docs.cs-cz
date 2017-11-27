---
title: "ICorProfilerCallback4::SurvivingReferences2 – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback4.SurvivingReferences2
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback4::SurvivingReferences2
helpviewer_keywords:
- ICorProfilerCallback4::SurvivingReferences2 method [.NET Framework profiling]
- SurvivingReferences2 method, ICorProfilerCallback4 interface [.NET Framework profiling]
ms.assetid: 02b51888-5d89-4e50-a915-45b7e329aad9
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: ced8542d2e84b6c317e20d7ff440e6c159383bfa
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilercallback4survivingreferences2-method"></a>ICorProfilerCallback4::SurvivingReferences2 – metoda
Sestavy rozložení objektů v haldě v důsledku uvolnění paměti kompresi. Tato metoda je volána, pokud má implementovaný profileru [icorprofilercallback4 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) rozhraní. Nahradí tato zpětného volání [icorprofilercallback2::survivingreferences –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-survivingreferences-method.md) metoda, protože ho může hlásit větší rozsah objektů, jejichž délky překročit, co může být vyjádřený v typu ULONG.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT SurvivingReferences2(  
    [in] ULONG  cSurvivingObjectIDRanges,  
    [in, size_is(cSurvivingObjectIDRanges)] ObjectID  
                objectIDRangeStart[] ,  
    [in, size_is(cSurvivingObjectIDRanges)] SIZE_T  
                cObjectIDRangeLength[] );  
```  
  
#### <a name="parameters"></a>Parametry  
 `cSurvivingObjectIDRanges`  
 [v] Počet bloků souvislý objektů, které zůstal naživu v důsledku uvolnění paměti kompresi. To znamená, hodnota `cSurvivingObjectIDRanges` je velikost `objectIDRangeStart` a `cObjectIDRangeLength` maticových, které úložiště `ObjectID` a délky, v uvedeném pořadí, pro každý blok objektů.  
  
 Následující dva argumenty `SurvivingReferences2` jsou paralelní pole. Jinými slovy `objectIDRangeStart` a `cObjectIDRangeLength` na stejný blok souvislý objektů, které se týkají.  
  
 `objectIDRangeStart`  
 [v] Pole `ObjectID` hodnoty, z nichž každý je adresa počáteční blok souvislý, live objekty v paměti.  
  
 `cObjectIDRangeLength`  
 [v] Pole celých čísel, z nichž každý je velikost bloku hostujícího souvislý objektů v paměti.  
  
 Velikost je zadán pro každý blok, který se odkazuje v `objectIDRangeStart` pole.  
  
## <a name="remarks"></a>Poznámky  
 Elementy `objectIDRangeStart` a `cObjectIDRangeLength` pole by měl být interpretován následujícím způsobem určit, zda objekt zůstal naživu uvolnění paměti. Předpokládáme, že `ObjectID` hodnotu (`ObjectID`) v rozmezí následující:  
  
 `ObjectIDRangeStart[i]` <= `ObjectID` < `ObjectIDRangeStart[i]` + `cObjectIDRangeLength[i]`  
  
 Pro všechny hodnotu `i` , je v následujícím rozsahu, objekt má zůstal naživu uvolnění paměti:  
  
 0 <= `i` < `cSurvivingObjectIDRanges`  
  
 Uvolnění paměti kompresi získá paměť obsazená "neaktivní" objekty, ale není compact toto uvolněné místo. V důsledku toho se vrátí halda paměti, ale žádné "živé" objekty přesunou.  
  
 Modul CLR (CLR) volá `SurvivingReferences2` pro kompresi jiné kolekce. Pro komprimaci kolekce [movedreferences2 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-movedreferences2-method.md) nazývá místo. Uvolňování paměti jednom může být komprimaci pro jedna generace a bez kompresi pro jinou. Pro kolekci paměti na žádné konkrétní generování profileru obdrží, buď `SurvivingReferences2` zpětného volání nebo [movedreferences2 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-movedreferences2-method.md) zpětného volání, ale ne obojí.  
  
 Více `SurvivingReferences2` zpětná volání může být přijata během konkrétní uvolňování kvůli omezené interní ukládání do vyrovnávací paměti, více zpětná volání během uvolňování paměti serveru a z jiných důvodů. V případě více zpětných volání během uvolňování paměti je informace kumulativní; všechny odkazy, které jsou hlášeny v žádném `SurvivingReferences2` zpětného volání, zůstanou platné i po uvolnění paměti.  
  
 Pokud profileru implementuje i [icorprofilercallback –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) a [icorprofilercallback4 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md) rozhraní, `SurvivingReferences2` metoda je volána před provedením [icorprofilercallback2 –:: Survivingreferences –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-survivingreferences-method.md) metoda, ale jenom v případě `SurvivingReferences2` vrátí úspěšně. Profilery může vrátit HRESULT označující selhání z `SurvivingReferences2` metoda zrušení volání druhé metody.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Icorprofilercallback – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [Icorprofilercallback2 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-interface.md)  
 [Icorprofilercallback4 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)
