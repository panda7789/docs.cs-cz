---
title: ICorProfilerCallback9 rozhraní
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
ms.openlocfilehash: 488af069e7798fde650abb1473df256eed2d692f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilercallback9-interface"></a>ICorProfilerCallback9 rozhraní
[Podporované v rozhraní .NET Framework 4.7.2 a novějších verzích]  

 Podtřídou třídy [ICorProfilerCallback8](icorprofilercallback8-interface.md) , který poskytuje metody zpětného volání používané modul common language runtime profileru oznámit, že dynamické metoda byla shromážděných a následně uvolňování paměti.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[DynamicMethodUnloaded – metoda](ICorProfilerCallback9-dynamicmethodunloaded-method.md)|Upozorní profileru, dynamické metoda byla shromážděných a následně uvolňování paměti.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  

## <a name="see-also"></a>Viz také  
[Rozhraní pro profilaci](profiling-interfaces.md)   
[ICorProfilerCallback8 rozhraní](icorprofilercallback9-interface.md)   
[ICorProfilerCallback8.DynamicMethodJITCompilationStarted – metoda](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)   
[ICorProfilerCallback8.DynamicMethodJITCompilationFinished – metoda](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)   
