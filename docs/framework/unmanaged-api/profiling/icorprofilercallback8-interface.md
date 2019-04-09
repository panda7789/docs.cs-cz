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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e536e61a8d812e442e1e54188c99d6a1d4586757
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59125564"
---
# <a name="icorprofilercallback8-interface"></a>ICorProfilerCallback8 – rozhraní
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
