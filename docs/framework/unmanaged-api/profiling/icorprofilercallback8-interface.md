---
title: ICorProfilerCallback8 rozhraní
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
ms.openlocfilehash: b92120cc5948efca696d922448da215601f9e6b3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilercallback8-interface"></a>ICorProfilerCallback8 rozhraní
[Podporované v rozhraní .NET Framework 4.7 a novějších verzích]  

 Podtřídou třídy [ICorProfilerCallback7](icorprofilercallback7-interface.md) , který poskytuje metody zpětného volání používané modul common language runtime oznámit profileru, který má JIT – kompilace dynamické metody spuštění a dokončení. 
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[DynamicMethodJITCompilationStarted – metoda](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md)|Aby bylo zahájeno JIT – kompilace dynamické metody upozorní profileru.|  
|[DynamicMethodJITCompilationFinished – metoda](icorprofilercallback8-dynamicmethodjitcompilationfinished-method.md)|Upozorní profileru, že byla dokončena JIT – kompilace dynamické metody.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]  

## <a name="see-also"></a>Viz také  
[Rozhraní pro profilaci](profiling-interfaces.md)   
[ICorProfilerCallback9 rozhraní](icorprofilercallback9-interface.md)
