---
title: "Rozhraní ICorProfilerCallback6"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback6
api_location:
- mscorwks.dll
- corprof.idl
api_type: COM
ms.assetid: edc420b7-96d1-4dec-ace0-36d907f644bc
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 733ca2f03e73852f2fef1e42fb9ec961ade2975d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallback6-interface"></a>Rozhraní ICorProfilerCallback6
[Podporované v rozhraní .NET Framework 4.5.2 a novějších verzích]  
  
 Podtřídou třídy [icorprofilercallback5 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback5-interface.md) , který poskytuje metody zpětného volání, která používá modul common language runtime oznámit profileru, který načítá sestavení.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[GetAssemblyReferences – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md)|Upozorní profileru, že sestavení v velmi brzy načítá fáze, když modul common language runtime provede procházení uzavření odkaz na sestavení.|  
  
## <a name="remarks"></a>Poznámky  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Rozhraní pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
