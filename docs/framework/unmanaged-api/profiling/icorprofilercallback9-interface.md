---
title: ICorProfilerCallback9 – rozhraní
ms.date: 04/10/2018
api_name:
- ICorProfilerCallback9
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.openlocfilehash: c383a2e221e61770d3c28a65c561c48f6059b6d6
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136566"
---
# <a name="icorprofilercallback9-interface"></a>ICorProfilerCallback9 – rozhraní
[Podporováno v .NET Framework 4.7.2 a novějších verzích]  

 Podtřída [ICorProfilerCallback8](icorprofilercallback8-interface.md) , která poskytuje metodu zpětného volání, kterou používá modul CLR (Common Language Runtime) k upozornění profileru, že dynamická metoda byla uvolněna z paměti a následně uvolněna.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[DynamicMethodUnloaded – metoda](ICorProfilerCallback9-dynamicmethodunloaded-method.md)|Upozorní profileru, že dynamická metoda byla uvolněna z paměti a následně uvolněna.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
**Verze .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]  

## <a name="see-also"></a>Viz také:

- [Rozhraní pro profilaci](profiling-interfaces.md)
- [ICorProfilerCallback8 – rozhraní](icorprofilercallback9-interface.md)
- [ICorProfilerCallback8. DynamicMethodJITCompilationStarted – metoda](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)
- [ICorProfilerCallback8. DynamicMethodJITCompilationFinished – metoda](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)
