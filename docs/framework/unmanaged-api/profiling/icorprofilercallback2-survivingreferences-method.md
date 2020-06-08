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
ms.openlocfilehash: 3681106bca94f1fefb2f24a1aa4254eb2b1b0531
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84499737"
---
# <a name="icorprofilercallback2survivingreferences-method"></a>ICorProfilerCallback2::SurvivingReferences – metoda
Oznamuje rozložení objektů v haldě v důsledku nekomprimace uvolňování paměti.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SurvivingReferences(  
    [in] ULONG  cSurvivingObjectIDRanges,  
    [in, size_is(cSurvivingObjectIDRanges)] ObjectID  
                objectIDRangeStart[] ,  
    [in, size_is(cSurvivingObjectIDRanges)] ULONG  
                cObjectIDRangeLength[] );  
```  
  
## <a name="parameters"></a>Parametry  
 `cSurvivingObjectIDRanges`  
 pro Počet bloků souvislých objektů, které byly zachovány v důsledku nekomprimace uvolňování paměti. To znamená, že hodnota `cSurvivingObjectIDRanges` je velikost pole `objectIDRangeStart` a `cObjectIDRangeLength` , který ukládá `ObjectID` a délku, v uvedeném pořadí pro každý blok objektů.  
  
 Další dva argumenty `SurvivingReferences` jsou paralelní pole. Jinými slovy `objectIDRangeStart` a `cObjectIDRangeLength` týká se stejného bloku souvislých objektů.  
  
 `objectIDRangeStart`  
 pro Pole `ObjectID` hodnot, z nichž každá je počáteční adresou bloku souvislých objektů, živé objekty v paměti.  
  
 `cObjectIDRangeLength`  
 pro Pole celých čísel, z nichž každá je velikost zbývajícího bloku souvislých objektů v paměti.  
  
 Velikost je určena pro každý blok, na který je odkazováno v `objectIDRangeStart` poli.  
  
## <a name="remarks"></a>Poznámky  
  
> [!IMPORTANT]
> Tato metoda oznamuje velikost `MAX_ULONG` pro objekty, které jsou větší než 4 GB na 64 bitů. Pro objekty, které jsou větší než 4 GB, použijte místo toho metodu [ICorProfilerCallback4:: SurvivingReferences2 –](icorprofilercallback4-survivingreferences2-method.md) .  
  
 Prvky `objectIDRangeStart` `cObjectIDRangeLength` polí a by měly být interpretovány následujícím způsobem, aby bylo možné určit, zda objekt držel uvolňování paměti. Předpokládejme, že `ObjectID` hodnota ( `ObjectID` ) leží v následujícím rozsahu:  
  
 `ObjectIDRangeStart[i]` <= `ObjectID` < `ObjectIDRangeStart[i]` + `cObjectIDRangeLength[i]`  
  
 Pro všechny hodnoty `i` , které jsou v následujícím rozsahu, objekt předržel uvolňování paměti:  
  
 0 <=`i` < `cSurvivingObjectIDRanges`  
  
 Nekomprimace uvolňování paměti znovu uvolňuje paměť obsazenou "nemrtvými" objekty, ale nekomprimuje volné místo. V důsledku toho se do haldy vrátí paměť, ale nebudou přesunuty žádné "živé" objekty.  
  
 Modul CLR (Common Language Runtime) volá `SurvivingReferences` pro nekomprimaci uvolňování paměti. Pro komprimaci uvolňování paměti je místo toho volána metoda [ICorProfilerCallback:: MovedReferences –](icorprofilercallback-movedreferences-method.md) . Jedno uvolnění paměti může být zkomprimováno pro jednu generaci a nekomprimaci pro jiné. Pro uvolňování paměti v jakékoli konkrétní generaci získá Profiler buď `SurvivingReferences` zpětné volání `MovedReferences` , nebo zpětné volání, ale ne obojí.  
  
 `SurvivingReferences`V průběhu konkrétního uvolňování paměti může být přijato více zpětných volání, z důvodu omezené vnitřní vyrovnávací paměti, více vláken hlásí v případě uvolňování paměti serveru a z jiných důvodů. V případě více zpětných volání během uvolňování paměti jsou informace kumulativní – všechny odkazy, které jsou hlášeny v jakémkoli `SurvivingReferences` zpětném volání, se zachová do uvolňování paměti.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerCallback – rozhraní](icorprofilercallback-interface.md)
- [ICorProfilerCallback2 – rozhraní](icorprofilercallback2-interface.md)
- [SurvivingReferences2 – metoda](icorprofilercallback4-survivingreferences2-method.md)
