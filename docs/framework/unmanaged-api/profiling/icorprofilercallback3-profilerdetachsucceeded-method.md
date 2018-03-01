---
title: "ICorProfilerCallback3::ProfilerDetachSucceeded – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorProfilerCallback3.ProfilerDetachSucceeded Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback3::ProfilerDetachSucceeded
helpviewer_keywords:
- ProfilerDetachSucceeded method [.NET Framework profiling]
- ICorProfilerCallback3::ProfilerDetachSucceeded method [.NET Framework profiling]
ms.assetid: 05164966-16ce-4cc9-a530-43a640c00711
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: d06671917094752287836800ebc492d5f0a5b595
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallback3profilerdetachsucceeded-method"></a>ICorProfilerCallback3::ProfilerDetachSucceeded – metoda
Upozorní profileru, že modul CLR (CLR) má uvolnit knihovnu DLL profileru.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT ProfilerDetachSucceeded();  
```  
  
## <a name="return-value"></a>Návratová hodnota  
 Vrácená hodnota z této zpětné volání se ignoruje.  
  
## <a name="remarks"></a>Poznámky  
 `ProfilerDetachSucceeded` Zpětné volání se objeví po všechna vlákna se odpojili profileru kódu. Když tato metoda je volána, proveďte profileru poslední minutu úkoly, které nejsou vhodné pro jeho destruktor, jako je například upozornění jeho uživatelského rozhraní nebo součást protokolování. Ale profileru nesmějí provádět volání funkce na rozhraní, které jsou k dispozici CLR během této zpětného volání (například [icorprofilerinfo –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md) nebo `IMetaData*` rozhraní).  
  
 Modul CLR vytvoří záznam v protokolu událostí aplikace systému Windows k označení, že byla úspěšně dokončena operace odpojení.  
  
 Po návratu profileru z této zpětného volání modulu CLR uvolní objekt profileru a uvolní profileru knihovny DLL. Proto profileru nesmí provádět všechny akce, které by způsobily provádění nastat uvnitř profileru DLL po vrátí z této zpětného volání. Například nemůže vytvořit podprocesy ani registrace zpětných volání časovače.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Rozhraní pro metadata](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)  
 [ICorProfilerInfo3 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)  
 [Rozhraní pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [Profilace](../../../../docs/framework/unmanaged-api/profiling/index.md)
