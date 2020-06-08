---
title: ICorProfilerCallback4 – rozhraní
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback4
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback4
helpviewer_keywords:
- ICorProfilerCallback4 interface [.NET Framework profiling]
ms.assetid: 665f3cfc-cd6f-4880-906c-ea65ad384783
topic_type:
- apiref
ms.openlocfilehash: 295d3d440529623f4569fd6c5f4debe7e4558990
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84499438"
---
# <a name="icorprofilercallback4-interface"></a>ICorProfilerCallback4 – rozhraní
Poskytuje metody zpětného volání, které modul CLR (Common Language Runtime) používá ke sdělování informací do profileru.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Description|  
|------------|-----------------|  
|[GetReJITParameters – metoda](icorprofilercallback4-getrejitparameters-method.md)|Umožňuje profileru kódu nastavit alternativní příznaky generování kódu pro nový text nové kompilované metody.|  
|[MovedReferences2 – metoda](icorprofilercallback4-movedreferences2-method.md)|Nahlásí nové rozložení objektů v haldě jako výsledek komprimace uvolňování paměti.|  
|[ReJITCompilationFinished – metoda](icorprofilercallback4-rejitcompilationfinished-method.md)|Upozorní profileru, že kompilátor JIT (just-in-time) dokončil rekompilaci funkce.|  
|[ReJITCompilationStarted – metoda](icorprofilercallback4-rejitcompilationstarted-method.md)|Upozorní profileru, že kompilátor JIT (just-in-time) začal znovu kompilovat funkci.|  
|[ReJITError – metoda](icorprofilercallback4-rejiterror-method.md)|Oznamuje chybu při zpracování žádosti o opětovnou kompilaci.|  
|[SurvivingReferences2 – metoda](icorprofilercallback4-survivingreferences2-method.md)|Oznamuje rozložení objektů v haldě v důsledku nekomprimace uvolňování paměti.|  
  
## <a name="remarks"></a>Poznámky  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerCallback2 – rozhraní](icorprofilercallback2-interface.md)
- [Rozhraní pro profilaci](profiling-interfaces.md)
- [ICorProfilerInfo – rozhraní](icorprofilerinfo-interface.md)
