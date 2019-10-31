---
title: ICorProfilerCallback8 – rozhraní
ms.date: 04/10/2018
api_name:
- ICorProfilerCallback8
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: 4516c8f9673052b521c1f0f594978236fef1e0ec
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136454"
---
# <a name="icorprofilercallback8-interface"></a>ICorProfilerCallback8 – rozhraní
[Podporováno v .NET Framework 4,7 a novějších verzích]  

 Podtřída [ICorProfilerCallback7](icorprofilercallback7-interface.md) , která poskytuje metody zpětného volání používané modulem CLR (Common Language Runtime) k informování profileru o zahájení a dokončení kompilace JIT dynamické metody. 
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[DynamicMethodJITCompilationStarted – metoda](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)|Upozorní profileru, že byla spuštěna kompilace JIT pro dynamickou metodu.|  
|[DynamicMethodJITCompilationFinished – metoda](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)|Upozorní profileru, že byla dokončena kompilace dynamické metody JIT.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
**Verze .NET Framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>Viz také:

- [Rozhraní pro profilaci](profiling-interfaces.md)
- [ICorProfilerCallback9 – rozhraní](icorprofilercallback9-interface.md)
