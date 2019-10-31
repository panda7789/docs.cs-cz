---
title: Rozhraní ICorProfilerCallback6
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback6
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.assetid: edc420b7-96d1-4dec-ace0-36d907f644bc
topic_type:
- apiref
ms.openlocfilehash: 0009d935e2e3b2abf590aca270113717ceb7e2d8
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127483"
---
# <a name="icorprofilercallback6-interface"></a>Rozhraní ICorProfilerCallback6
[Podporované v .NET Framework 4.5.2 a novějších verzích]  
  
 Podtřída [ICorProfilerCallback5 –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback5-interface.md) , která poskytuje metodu zpětného volání, kterou modul CLR (Common Language Runtime) používá pro upozornění profileru, že se načítá sestavení.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[GetAssemblyReferences – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md)|Upozorní profileru, že sestavení je ve fázi brzkého nasazování, pokud modul CLR provádí procházení zavřením odkazu na sestavení.|  
  
## <a name="remarks"></a>Poznámky  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
