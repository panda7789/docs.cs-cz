---
title: Rozhraní ICorProfilerAssemblyReferenceProvider
ms.date: 03/30/2017
api_name:
- ICorProfilerAssemblyReferenceProvider
api_location:
- mscorwks.dll
api_type:
- COM
ms.assetid: 17205116-66e1-4acc-8f01-532fb3867028
topic_type:
- apiref
ms.openlocfilehash: f5ba72dca25889fb57c0ae1bb2429e54a8cf2228
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128720"
---
# <a name="icorprofilerassemblyreferenceprovider-interface"></a>Rozhraní ICorProfilerAssemblyReferenceProvider
[Podporované v .NET Framework 4.5.2 a novějších verzích]  
  
 Umožňuje profileru informovat modul CLR (Common Language Runtime) se odkazy na sestavení, které Profiler přidá do zpětného volání [ICorProfilerCallback:: ModuleLoadFinished –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) .  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[AddAssemblyReference – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-addassemblyreference-method.md)|Informuje modul CLR odkazu na sestavení, který Profiler plánuje přidat do zpětného volání [ModuleLoadFinished –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) .|  
  
## <a name="remarks"></a>Poznámky  
 Modul CLR předá profileru objekt `ICorProfilerAssemblyReferenceProvider` rozhraní ve zpětném volání [ICorProfilerCallback6:: GetAssemblyReferences –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) . To umožňuje profileru informovat modul CLR o odkazech na sestavení, které plány profileru později přidají do [ICorProfilerCallback:: ModuleLoadFinished –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md). onCuePoint. Tím se zlepší přesnost prohlížeč ukončení odkazu sestavení CLR a jeho algoritmy pro určení, zda lze sdílet sestavení.  
  
 Toto rozhraní lze použít pouze ve zpětném volání [ICorProfilerCallback6:: GetAssemblyReferences –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) , které předá tento objekt rozhraní profileru.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
