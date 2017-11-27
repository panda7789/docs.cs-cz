---
title: "ICorProfilerCallback4::GetReJITParameters – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback4.GetReJITParameters
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback4::GetReJITParameters
helpviewer_keywords:
- ICorProfilerCallback4::GetReJITParameters method [.NET Framework profiling]
- GetReJITParameters method, ICorProfilerCallback4 interface [.NET Framework profiling]
ms.assetid: 0e9bfe07-9f20-498c-b568-9017c8f6056c
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: acecbe10fd79394b27e6264c337d584d9fb259b1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilercallback4getrejitparameters-method"></a>ICorProfilerCallback4::GetReJITParameters – metoda
Umožňuje profileru kódu nastavit alternativní kód pro nový text Rekompilované metoda příznaky generace.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetReJITParameters(     [in] ModuleID moduleId,     [in] mdMethodDef methodId,     [in] ICorProfilerFunctionControl *pFunctionControl);  
```  
  
#### <a name="parameters"></a>Parametry  
 `moduleID`  
 [v] Modul, který obsahuje metodu, pro niž je modulu CLR JIT rekompilace parametry.  
  
 `methodId`  
 [v] `MethodDef` Metody, pro niž je modulu CLR JIT rekompilace parametry.  
  
 `pFunctionControl`  
 [v] Ukazatel na [icorprofilerfunctioncontrol –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-interface.md) rozhraní, které profileru můžete použít k zadání informací o opětovnou kompilaci JIT pro metodu se překompilovat.  
  
## <a name="remarks"></a>Poznámky  
 Problémy CLR `GetReJITParameters` zpětného volání, aby profileru můžete zadat parametry pro nutnosti rekompilace dané metody. `GetReJITParameters` Zpětné volání se objeví pouze jednou za funkce; parametry poskytl profileru platí pro všechny instance této funkce.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Icorprofilercallback – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [Icorprofilercallback4 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)  
 [Jitcompilationstarted – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md)  
 [Rejitcompilationstarted – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationstarted-method.md)
