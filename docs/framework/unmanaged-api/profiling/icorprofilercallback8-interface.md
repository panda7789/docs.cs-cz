---
title: ICorProfilerCallback8 Interface
ms.date: 04/10/2018
api_name:
- ICorProfilerCallback8
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a3bdf79582619777a22c80caac5b4e90d603f3a8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54675012"
---
# <a name="icorprofilercallback8-interface"></a>ICorProfilerCallback8 Interface
[Podporované v rozhraní .NET Framework 4.7 a novějších verzích]  

 Podtřída [icorprofilercallback7 –](icorprofilercallback7-interface.md) , který poskytuje metody zpětného volání používané modulem common language runtime pro oznámení profileru, který je spuštěn a dokončení kompilace JIT dynamické metody. 
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[DynamicMethodJITCompilationStarted – metoda](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)|Oznámí profileru, byla spuštěna kompilace JIT dynamické metody.|  
|[DynamicMethodJITCompilationFinished – metoda](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)|Upozornění profileru dokončení kompilace JIT dynamické metody.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>Viz také:
- [Rozhraní pro profilaci](profiling-interfaces.md)
- [ICorProfilerCallback9 – rozhraní](icorprofilercallback9-interface.md)
