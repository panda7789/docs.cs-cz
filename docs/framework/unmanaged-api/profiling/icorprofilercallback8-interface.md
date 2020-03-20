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
ms.openlocfilehash: 617b27923e96d9abc62ccbf158b076c6e45b20a8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175093"
---
# <a name="icorprofilercallback8-interface"></a>ICorProfilerCallback8 – rozhraní
[Podporováno v rozhraní .NET Framework 4.7 a novějších verzích]  

 Podtřída [ICorProfilerCallback7,](icorprofilercallback7-interface.md) která poskytuje metody zpětného volání používané běžným jazykem runtime upozornit profiler, že kompilace JIT dynamické metody byla spuštěna a dokončena.
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[DynamicMethodJITCompilationStarted – metoda](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)|Upozorní profiler, že byla spuštěna kompilace JIT dynamické metody.|  
|[DynamicMethodJITCompilationFinished – metoda](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)|Upozorní profiler, že byla dokončena kompilace JIT dynamické metody.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [Systémové požadavky](../../get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>Viz také

- [Rozhraní pro profilaci](profiling-interfaces.md)
- [ICorProfilerCallback9 – rozhraní](icorprofilercallback9-interface.md)
