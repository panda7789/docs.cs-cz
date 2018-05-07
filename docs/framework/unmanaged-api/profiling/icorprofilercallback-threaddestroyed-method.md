---
title: ICorProfilerCallback::ThreadDestroyed – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ThreadDestroyed
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ThreadDestroyed
helpviewer_keywords:
- ThreadDestroyed method [.NET Framework profiling]
- ICorProfilerCallback::ThreadDestroyed method [.NET Framework profiling]
ms.assetid: 4c2b66fd-0595-40a3-8931-f9c4fff97ac8
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4929d9aaf7de9af72ec5ba93f5d7e35c712ac6cd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilercallbackthreaddestroyed-method"></a>ICorProfilerCallback::ThreadDestroyed – metoda
Upozorní profileru, byl zničen vlákna.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT ThreadDestroyed(  
    [in] ThreadID threadId);  
```  
  
#### <a name="parameters"></a>Parametry  
 `threadId`  
 [v] ID podprocesu, který byl zničen.  
  
## <a name="remarks"></a>Poznámky  
 `threadId` Hodnota již není platný v době toto volání.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICorProfilerCallback – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [ThreadCreated – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-threadcreated-method.md)
