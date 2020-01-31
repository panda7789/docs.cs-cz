---
title: ICorProfilerCallback::ThreadCreated – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ThreadCreated
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ThreadCreated
helpviewer_keywords:
- ICorProfilerCallback::ThreadCreated method [.NET Framework profiling]
- ThreadCreated method [.NET Framework profiling]
ms.assetid: cca0f799-09b8-4689-a33c-6d6537943a9b
topic_type:
- apiref
ms.openlocfilehash: 6514606290bf006443d7011c1a428bebb4cca0f6
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76865826"
---
# <a name="icorprofilercallbackthreadcreated-method"></a>ICorProfilerCallback::ThreadCreated – metoda
Upozorní profileru, že bylo vytvořeno vlákno.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT ThreadCreated(  
    [in] ThreadID threadId);   
```  
  
## <a name="parameters"></a>Parametry  
 `threadId`  
 pro ID vlákna, které bylo vytvořeno.  
  
## <a name="remarks"></a>Poznámky  
 Hodnota `threadId` je okamžitě platná.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerCallback – rozhraní](icorprofilercallback-interface.md)
- [ThreadDestroyed – metoda](icorprofilercallback-threaddestroyed-method.md)
