---
title: "Rozhraní ICorProfilerAssemblyReferenceProvider"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerAssemblyReferenceProvider
api_location: mscorwks.dll
api_type: COM
ms.assetid: 17205116-66e1-4acc-8f01-532fb3867028
topic_type: apiref
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 203362d2780d372236b05f753bedc0d59565d2b5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerassemblyreferenceprovider-interface"></a>Rozhraní ICorProfilerAssemblyReferenceProvider
[Podporované v rozhraní .NET Framework 4.5.2 a novějších verzích]  
  
 Umožňuje profileru k informování modul CLR (CLR) odkazů na sestavení, které profileru přidá [icorprofilercallback::moduleloadfinished –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) zpětného volání.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[AddAssemblyReference – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-addassemblyreference-method.md)|Informuje o modulu CLR odkaz na sestavení, který profileru přidat [moduleloadfinished –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md) zpětného volání.|  
  
## <a name="remarks"></a>Poznámky  
 Modul CLR předá profileru `ICorProfilerAssemblyReferenceProvider` objekt rozhraní v [icorprofilercallback6::getassemblyreferences –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) zpětného volání. To umožňuje profileru k informování CLR odkazů na sestavení, které profileru plánuje přidat později v [icorprofilercallback::moduleloadfinished –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadfinished-method.md). zpětné volání. Tím se zlepšuje přesnost walkera uzavření referenční sestavení modulu CLR a jeho algoritmy pro určení, zda může sdílet sestavení.  
  
 Toto rozhraní je možné pouze v [icorprofilercallback6::getassemblyreferences –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) zpětné volání, které se předá tento objekt rozhraní profileru.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Rozhraní pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
