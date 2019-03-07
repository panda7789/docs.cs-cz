---
title: ICorProfilerInfo2::SetEnterLeaveFunctionHooks2 – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.SetEnterLeaveFunctionHooks2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::SetEnterLeaveFunctionHooks2
helpviewer_keywords:
- ICorProfilerInfo2::SetEnterLeaveFunctionHooks2 method [.NET Framework profiling]
- SetEnterLeaveFunctionHooks2 method [.NET Framework profiling]
ms.assetid: 3c26b3e7-f72b-48a5-bf8c-edc122523a4b
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1fc679ee7deb644dba3e18a15e330ee4ceca6ca7
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57472962"
---
# <a name="icorprofilerinfo2setenterleavefunctionhooks2-method"></a>ICorProfilerInfo2::SetEnterLeaveFunctionHooks2 – metoda
Určuje funkce implementované profileru mají být volány v aktualizované verze "zadejte", "ponechte" a "tailcall" háky spravované funkce.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT SetEnterLeaveFunctionHooks2(  
    [in] FunctionEnter2    *pFuncEnter,  
    [in] FunctionLeave2    *pFuncLeave,  
    [in] FunctionTailcall2 *pFuncTailcall);  
```  
  
## <a name="parameters"></a>Parametry  
 `pFuncEnter`  
 [in] Ukazatel na implementaci pro použití jako [FunctionEnter2](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md) zpětného volání.  
  
 `pFuncLeave`  
 [in] Ukazatel na implementaci pro použití jako [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md) zpětného volání.  
  
 `pFuncTailcall`  
 [in] Ukazatel na implementaci pro použití jako [functiontailcall2 –](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md) zpětného volání.  
  
## <a name="remarks"></a>Poznámky  
 `SetEnterLeaveFunctionHooks2` Metoda je podobná [icorprofilerinfo::setenterleavefunctionhooks –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setenterleavefunctionhooks-method.md) metody. Použijte nejprve zadat jako novější verze enter/ponechání a koncové volání zpětná volání a jeho použití k určení funkce má být použit jako starší verze zpětná volání enter/ponechání a koncové volání funkcí.  
  
 Najednou může být aktivní pouze jednu sadu zpětná volání. Proto pokud profiler volá obě `ICorProfilerInfo::SetEnterLeaveFunctionHooks` a `SetEnterLeaveFunctionHooks2`, `SetEnterLeaveFunctionHooks2` se používá.  
  
 `SetEnterLeaveFunctionHooks2` Metoda může volat pouze z okna profilování [ICorProfilerCallback::Initialize](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) zpětného volání.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:
- [ICorProfilerInfo – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [ICorProfilerInfo2 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
