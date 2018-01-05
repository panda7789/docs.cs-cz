---
title: "ICorProfilerInfo2::SetEnterLeaveFunctionHooks2 – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo2.SetEnterLeaveFunctionHooks2
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo2::SetEnterLeaveFunctionHooks2
helpviewer_keywords:
- ICorProfilerInfo2::SetEnterLeaveFunctionHooks2 method [.NET Framework profiling]
- SetEnterLeaveFunctionHooks2 method [.NET Framework profiling]
ms.assetid: 3c26b3e7-f72b-48a5-bf8c-edc122523a4b
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0c460cfd24a83ca2a6c75e061b7a797c8f455bc1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo2setenterleavefunctionhooks2-method"></a>ICorProfilerInfo2::SetEnterLeaveFunctionHooks2 – metoda
Určuje implementované profileru funkce k volání na aktualizované verze "zadejte", "nechte" a "tailcall" háky spravovaných funkcí.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT SetEnterLeaveFunctionHooks2(  
    [in] FunctionEnter2    *pFuncEnter,  
    [in] FunctionLeave2    *pFuncLeave,  
    [in] FunctionTailcall2 *pFuncTailcall);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pFuncEnter`  
 [v] Ukazatel na implementaci má být použit jako [functionenter2 –](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md) zpětného volání.  
  
 `pFuncLeave`  
 [v] Ukazatel na implementaci má být použit jako [functionleave2 –](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md) zpětného volání.  
  
 `pFuncTailcall`  
 [v] Ukazatel na implementaci má být použit jako [functiontailcall2 –](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md) zpětného volání.  
  
## <a name="remarks"></a>Poznámky  
 `SetEnterLeaveFunctionHooks2` Metoda je podobná [icorprofilerinfo::setenterleavefunctionhooks –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setenterleavefunctionhooks-method.md) metoda. Pomocí bývalé můžete určit funkce, které má být použit jako novější verze enter nebo ponechejte/tailcall zpětná volání a k tomu, chcete-li určit funkce, které má být použit jako starší verze enter nebo ponechejte/tailcall zpětných volání.  
  
 Najednou může být aktivní jen jednu sadu zpětných volání. Proto pokud profileru volá obě `ICorProfilerInfo::SetEnterLeaveFunctionHooks` a `SetEnterLeaveFunctionHooks2`, `SetEnterLeaveFunctionHooks2` se používá.  
  
 `SetEnterLeaveFunctionHooks2` Metoda může volat pouze z okna profilování [icorprofilercallback::Initialize –](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md) zpětného volání.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICorProfilerInfo – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [ICorProfilerInfo2 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
