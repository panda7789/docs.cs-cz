---
title: ICorProfilerCallback9 Interface
ms.date: 04/10/2018
api_name:
- ICorProfilerCallback9
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e1711def5e2aa41fd63912361ef8250ad160fb88
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59227753"
---
# <a name="icorprofilercallback9-interface"></a>ICorProfilerCallback9 Interface
[Podporované v rozhraní .NET Framework 4.7.2 a novějších verzích]  

 Podtřída [icorprofilercallback8 –](icorprofilercallback8-interface.md) , která poskytuje metodu zpětného volání používané modul common language runtime pro oznámení profileru, že dynamickou metodu byla uvolňování paměti shromažďují a následně byla uvolněna.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[DynamicMethodUnloaded – metoda](ICorProfilerCallback9-dynamicmethodunloaded-method.md)|Oznámí profileru, že dynamickou metodu byla uvolňování paměti shromažďují a následně byla uvolněna.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  

## <a name="see-also"></a>Viz také:

- [Rozhraní pro profilaci](profiling-interfaces.md)
- [ICorProfilerCallback8 – rozhraní](icorprofilercallback9-interface.md)
- [ICorProfilerCallback8.DynamicMethodJITCompilationStarted – metoda](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)
- [ICorProfilerCallback8.DynamicMethodJITCompilationFinished – metoda](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)
