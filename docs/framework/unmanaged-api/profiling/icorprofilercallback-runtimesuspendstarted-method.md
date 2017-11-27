---
title: "ICorProfilerCallback::RuntimeSuspendStarted – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.RuntimeSuspendStarted
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::RuntimeSuspendStarted
helpviewer_keywords:
- ICorProfilerCallback::RuntimeSuspendStarted method [.NET Framework profiling]
- RuntimeSuspendStarted method [.NET Framework profiling]
ms.assetid: c8461cac-e31b-4efa-ad2c-26598173eb96
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 358536aa51dfef2d079813b34eddbd1b01294bcc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilercallbackruntimesuspendstarted-method"></a>ICorProfilerCallback::RuntimeSuspendStarted – metoda
Upozorní profileru, že běhové prostředí se chystá pozastavit všechna vlákna modulu runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT RuntimeSuspendStarted(  
    [in] COR_PRF_SUSPEND_REASON suspendReason);  
```  
  
#### <a name="parameters"></a>Parametry  
 `suspendReason`  
 [v] Hodnota [COR_PRF_SUSPEND_REASON](../../../../docs/framework/unmanaged-api/profiling/cor-prf-suspend-reason-enumeration.md) výčet, který označuje důvod pro pozastavení.  
  
## <a name="remarks"></a>Poznámky  
 Všechna vlákna modulu runtime, které jsou v nespravovaném kódu budou moci pokračovat, spuštění, dokud se snaží znovu zadat modulu runtime. V tomto bodě se bude také pozastavuje, dokud nebude obnoví modulu runtime. To platí také pro nové vláken, která zadejte modulu runtime. Všechna vlákna v modulu runtime jsou že buď pozastaveno okamžitě, pokud jsou již v přerušitelné kódu, nebo jsou vyzváni k pozastavení po uplynutí přerušitelné kódu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Icorprofilercallback – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [Runtimesuspendaborted – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendaborted-method.md)  
 [Runtimesuspendfinished – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-runtimesuspendfinished-method.md)
