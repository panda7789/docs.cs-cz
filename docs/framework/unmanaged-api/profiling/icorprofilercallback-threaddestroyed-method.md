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
ms.openlocfilehash: d4c45290b1ef4360e51b5ed8e1b0fac3dcdde727
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62041623"
---
# <a name="icorprofilercallbackthreaddestroyed-method"></a>ICorProfilerCallback::ThreadDestroyed – metoda
Oznámí profileru, že došlo ke zničení vlákno.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT ThreadDestroyed(  
    [in] ThreadID threadId);  
```  
  
## <a name="parameters"></a>Parametry  
 `threadId`  
 [in] ID vlákna, která byla zničena.  
  
## <a name="remarks"></a>Poznámky  
 `threadId` Již není platný v okamžiku tohoto volání.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerCallback – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [ThreadCreated – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-threadcreated-method.md)
