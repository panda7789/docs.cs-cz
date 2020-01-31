---
title: ICorProfilerCallback::RuntimeSuspendFinished – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.RuntimeSuspendFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::RuntimeSuspendFinished
helpviewer_keywords:
- ICorProfilerCallback::RuntimeSuspendFinished method [.NET Framework profiling]
- RuntimeSuspendFinished method [.NET Framework profiling]
ms.assetid: b7723f58-c55c-4399-9972-1bbf3b866694
topic_type:
- apiref
ms.openlocfilehash: e6c21e5ec9491e2ccade48a5019b284e333b5ead
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76865932"
---
# <a name="icorprofilercallbackruntimesuspendfinished-method"></a>ICorProfilerCallback::RuntimeSuspendFinished – metoda
Upozorní profileru, že modul runtime dokončil pozastavení všech vláken modulu runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT RuntimeSuspendFinished();  
```  
  
## <a name="remarks"></a>Poznámky  
 Všechna vlákna modulu runtime, která jsou v nespravovaném kódu, mohou pokračovat v běhu, dokud se nepokusí znovu zadat modul runtime. V tomto okamžiku se také pozastaví, dokud modul runtime nebude pokračovat. To platí také pro nová vlákna, která vstupují do modulu runtime. Všechna vlákna v modulu runtime jsou buď okamžitě pozastavena, pokud jsou již v kódu přerušitelné, nebo jsou požádány o pozastavení, když dosáhnou přerušitelné kódu.  
  
 U `RuntimeSuspendFinished` zpětného volání je zaručeno, že bude provedeno ve stejném vlákně jako zpětné volání [ICorProfilerCallback:: runtimesuspendstarted –](icorprofilercallback-runtimesuspendstarted-method.md) .  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerCallback – rozhraní](icorprofilercallback-interface.md)
- [RuntimeSuspendAborted – metoda](icorprofilercallback-runtimesuspendaborted-method.md)
