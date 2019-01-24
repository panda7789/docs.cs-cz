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
ms.openlocfilehash: a6c480af921fb0259ef85beec8d8f65bdd430522
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54689305"
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
