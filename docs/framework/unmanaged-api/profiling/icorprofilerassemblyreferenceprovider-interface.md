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
ms.openlocfilehash: 13a298451c3e8e1c5809cc1cb222acb5ab85714b
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866686"
---
# <a name="icorprofilerassemblyreferenceprovider-interface"></a>Rozhraní ICorProfilerAssemblyReferenceProvider
[Podporované v .NET Framework 4.5.2 a novějších verzích]  
  
 Umožňuje profileru informovat modul CLR (Common Language Runtime) se odkazy na sestavení, které Profiler přidá do zpětného volání [ICorProfilerCallback:: ModuleLoadFinished –](icorprofilercallback-moduleloadfinished-method.md) .  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[AddAssemblyReference – metoda](icorprofilerassemblyreferenceprovider-addassemblyreference-method.md)|Informuje modul CLR odkazu na sestavení, který Profiler plánuje přidat do zpětného volání [ModuleLoadFinished –](icorprofilercallback-moduleloadfinished-method.md) .|  
  
## <a name="remarks"></a>Poznámky  
 Modul CLR předá profileru objekt `ICorProfilerAssemblyReferenceProvider` rozhraní ve zpětném volání [ICorProfilerCallback6:: GetAssemblyReferences –](icorprofilercallback6-getassemblyreferences-method.md) . To umožňuje profileru informovat modul CLR o odkazech na sestavení, které plány profileru později přidají do [ICorProfilerCallback:: ModuleLoadFinished –](icorprofilercallback-moduleloadfinished-method.md). onCuePoint. Tím se zlepší přesnost prohlížeč ukončení odkazu sestavení CLR a jeho algoritmy pro určení, zda lze sdílet sestavení.  
  
 Toto rozhraní lze použít pouze ve zpětném volání [ICorProfilerCallback6:: GetAssemblyReferences –](icorprofilercallback6-getassemblyreferences-method.md) , které předá tento objekt rozhraní profileru.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro profilaci](profiling-interfaces.md)
