---
title: ICorProfilerCallback4::GetReJITParameters – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback4.GetReJITParameters
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback4::GetReJITParameters
helpviewer_keywords:
- ICorProfilerCallback4::GetReJITParameters method [.NET Framework profiling]
- GetReJITParameters method, ICorProfilerCallback4 interface [.NET Framework profiling]
ms.assetid: 0e9bfe07-9f20-498c-b568-9017c8f6056c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f628bd1270b529264c14236ca7cdc03bf7afd9d8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
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
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICorProfilerCallback – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [ICorProfilerCallback4 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)  
 [JITCompilationStarted – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-jitcompilationstarted-method.md)  
 [ReJITCompilationStarted – metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-rejitcompilationstarted-method.md)
