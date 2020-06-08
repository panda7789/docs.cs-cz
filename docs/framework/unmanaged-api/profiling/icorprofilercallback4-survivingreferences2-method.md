---
title: ICorProfilerCallback4::SurvivingReferences2 – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback4.SurvivingReferences2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback4::SurvivingReferences2
helpviewer_keywords:
- ICorProfilerCallback4::SurvivingReferences2 method [.NET Framework profiling]
- SurvivingReferences2 method, ICorProfilerCallback4 interface [.NET Framework profiling]
ms.assetid: 02b51888-5d89-4e50-a915-45b7e329aad9
topic_type:
- apiref
ms.openlocfilehash: 208ce1d7ef8a1eab4f18a6d488f0cc480b5713d8
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84499334"
---
# <a name="icorprofilercallback4survivingreferences2-method"></a>ICorProfilerCallback4::SurvivingReferences2 – metoda
Oznamuje rozložení objektů v haldě v důsledku nekomprimace uvolňování paměti. Tato metoda je volána, pokud profiler implementoval rozhraní [ICorProfilerCallback4](icorprofilercallback4-interface.md) . Toto zpětné volání nahrazuje metodu [ICorProfilerCallback2:: SurvivingReferences –](icorprofilercallback2-survivingreferences-method.md) , protože může vykazovat větší rozsahy objektů, jejichž délka překračuje, co může být vyjádřeno v ulong.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SurvivingReferences2(  
    [in] ULONG  cSurvivingObjectIDRanges,  
    [in, size_is(cSurvivingObjectIDRanges)] ObjectID  
                objectIDRangeStart[] ,  
    [in, size_is(cSurvivingObjectIDRanges)] SIZE_T  
                cObjectIDRangeLength[] );  
```  
  
## <a name="parameters"></a>Parametry  
 `cSurvivingObjectIDRanges`  
 pro Počet bloků souvislých objektů, které byly zachovány v důsledku nekomprimace uvolňování paměti. To znamená, že hodnota `cSurvivingObjectIDRanges` je velikost pole `objectIDRangeStart` a `cObjectIDRangeLength` , který ukládá `ObjectID` a délku, v uvedeném pořadí pro každý blok objektů.  
  
 Další dva argumenty `SurvivingReferences2` jsou paralelní pole. Jinými slovy `objectIDRangeStart` a `cObjectIDRangeLength` týká se stejného bloku souvislých objektů.  
  
 `objectIDRangeStart`  
 pro Pole `ObjectID` hodnot, z nichž každá je počáteční adresou bloku souvislých objektů, živé objekty v paměti.  
  
 `cObjectIDRangeLength`  
 pro Pole celých čísel, z nichž každá je velikost zbývajícího bloku souvislých objektů v paměti.  
  
 Velikost je určena pro každý blok, na který je odkazováno v `objectIDRangeStart` poli.  
  
## <a name="remarks"></a>Poznámky  
 Prvky `objectIDRangeStart` `cObjectIDRangeLength` polí a by měly být interpretovány následujícím způsobem, aby bylo možné určit, zda objekt držel uvolňování paměti. Předpokládejme, že `ObjectID` hodnota ( `ObjectID` ) leží v následujícím rozsahu:  
  
 `ObjectIDRangeStart[i]` <= `ObjectID` < `ObjectIDRangeStart[i]` + `cObjectIDRangeLength[i]`  
  
 Pro všechny hodnoty `i` , které jsou v následujícím rozsahu, objekt předržel uvolňování paměti:  
  
 0 <=`i` < `cSurvivingObjectIDRanges`  
  
 Nekomprimace uvolňování paměti znovu uvolňuje paměť obsazenou "nemrtvými" objekty, ale nekomprimuje volné místo. V důsledku toho se do haldy vrátí paměť, ale nebudou přesunuty žádné "živé" objekty.  
  
 Modul CLR (Common Language Runtime) volá `SurvivingReferences2` pro nekomprimaci uvolňování paměti. Pro komprimaci uvolňování paměti je místo toho volána metoda [MovedReferences2 –](icorprofilercallback4-movedreferences2-method.md) . Jedno uvolnění paměti může být zkomprimováno pro jednu generaci a nekomprimaci pro jiné. Pro uvolňování paměti v jakékoli konkrétní generaci získá Profiler buď `SurvivingReferences2` zpětné volání, nebo [MovedReferences2 –](icorprofilercallback4-movedreferences2-method.md) zpětné volání, ale ne obojí.  
  
 `SurvivingReferences2`Během konkrétního uvolňování paměti může být přijato více zpětných volání, z důvodu omezené vnitřní vyrovnávací paměti, více zpětných volání během uvolňování paměti serveru a z jiných důvodů. V případě více zpětných volání během uvolňování paměti jsou informace kumulativní; všechny odkazy, které jsou hlášeny v jakémkoli `SurvivingReferences2` zpětném volání, jsou v uvolňování paměti.  
  
 Pokud profiler implementuje rozhraní [ICorProfilerCallback](icorprofilercallback-interface.md) i [ICorProfilerCallback4](icorprofilercallback4-interface.md) , `SurvivingReferences2` je metoda volána před metodou [ICorProfilerCallback2:: SurvivingReferences –](icorprofilercallback2-survivingreferences-method.md) , ale pouze v případě, že se `SurvivingReferences2` vrátí úspěšně. Profilery mohou vracet hodnotu HRESULT, která označuje selhání od `SurvivingReferences2` metody pro zamezení volání druhé metody.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerCallback – rozhraní](icorprofilercallback-interface.md)
- [ICorProfilerCallback2 – rozhraní](icorprofilercallback2-interface.md)
- [ICorProfilerCallback4 – rozhraní](icorprofilercallback4-interface.md)
