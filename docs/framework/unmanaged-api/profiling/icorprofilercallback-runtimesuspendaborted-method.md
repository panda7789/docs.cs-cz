---
title: ICorProfilerCallback::RuntimeSuspendAborted – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RuntimeSuspendAborted
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RuntimeSuspendAborted
helpviewer_keywords:
- ICorProfilerCallback::RuntimeSuspendAborted method [.NET Framework profiling]
- RuntimeSuspendAborted method [.NET Framework profiling]
ms.assetid: 5a8a4277-345b-448b-a028-fc8cff9998aa
topic_type:
- apiref
ms.openlocfilehash: 285bdd3f2a96d3c6cb0039382d9944e48c49971a
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76865906"
---
# <a name="icorprofilercallbackruntimesuspendaborted-method"></a>ICorProfilerCallback::RuntimeSuspendAborted – metoda
Upozorní profileru, že modul runtime přerušil přerušení běhu, ke kterému došlo.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT RuntimeSuspendAborted();  
```  
  
## <a name="remarks"></a>Poznámky  
 Pozastavení běhu může být přerušeno, pokud se dvě vlákna současně pokusí pozastavit modul runtime.  
  
 Zpětné volání [ICorProfilerCallback:: RuntimeSuspendFinished –](icorprofilercallback-runtimesuspendfinished-method.md) nebo zpětné volání `RuntimeSuspendAborted` dojde v jednom vlákně po zpětném volání [ICorProfilerCallback:: runtimesuspendstarted –](icorprofilercallback-runtimesuspendstarted-method.md) .  
  
 `RuntimeSuspendAborted` zpětné volání je zaručeno, že dojde ve stejném vlákně jako `RuntimeSuspendStarted` zpětného volání.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerCallback – rozhraní](icorprofilercallback-interface.md)
