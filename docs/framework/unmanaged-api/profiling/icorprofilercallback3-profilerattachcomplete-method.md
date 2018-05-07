---
title: ICorProfilerCallback3::ProfilerAttachComplete – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback3.ProfilerAttachComplete Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback3::ProfilerAttachComplete
helpviewer_keywords:
- ProfilerAttachComplete method [.NET Framework profiling]
- ICorProfilerCallback3::ProfilerAttachComplete method [.NET Framework profiling]
ms.assetid: 257d6076-06e0-4d93-bb33-651fbb2b92d7
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8397900e2dafb69807417090cbb30c85dd884c59
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilercallback3profilerattachcomplete-method"></a>ICorProfilerCallback3::ProfilerAttachComplete – metoda
Modul CLR (CLR) k označení, že můžete nyní volat profileru je voláno [icorprofilerinfo3::enumjitedfunctions –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enumjitedfunctions-method.md) a [icorprofilerinfo3::enummodules –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enummodules-method.md) opravný metody.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT ProfilerAttachComplete ();  
```  
  
## <a name="remarks"></a>Poznámky  
 `ProfilerAttachComplete` Zpětné volání se objeví po [icorprofilercallback3::initializeforattach –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback3-initializeforattach-method.md) metoda je volána. Znamená to následující:  
  
-   Zpětná volání, které byly požadoval profileru v `InitializeForAttach` aktivoval.  
  
-   Profileru teď můžete dělat zjištěná v přidružené ID aniž by musel být zajímá chybějící oznámení.  
  
 Modul CLR ignoruje návratovou hodnotou z této zpětného volání.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICorProfilerCallback – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [ICorProfilerInfo3 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)  
 [Rozhraní pro profilaci](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [Profilace](../../../../docs/framework/unmanaged-api/profiling/index.md)
