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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0b243c507171a4d907ef4594ae0c715a074c965a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilercallbackruntimesuspendfinished-method"></a>ICorProfilerCallback::RuntimeSuspendFinished – metoda
Upozorní profileru, modul runtime byla dokončena pozastavení všechna vlákna modulu runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT RuntimeSuspendFinished();  
```  
  
## <a name="remarks"></a>Poznámky  
 Všechna vlákna modulu runtime, které jsou v nespravovaném kódu budou moci pokračovat, spuštění, dokud se snaží znovu zadat modulu runtime. V tomto bodě se bude také pozastavuje, dokud nebude obnoví modulu runtime. To platí také pro nové vláken, která zadejte modulu runtime. Všechna vlákna v modulu runtime jsou že buď pozastaveno okamžitě, pokud jsou již v přerušitelné kódu, nebo jsou vyzváni k pozastavení po uplynutí přerušitelné kódu.  
  
 `RuntimeSuspendFinished` Zpětného volání záruku, že dojde k ve stejném vlákně, jako [icorprofilercallback::runtimesuspendstarted –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendstarted-method.md) zpětného volání.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICorProfilerCallback – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [RuntimeSuspendAborted – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendaborted-method.md)
