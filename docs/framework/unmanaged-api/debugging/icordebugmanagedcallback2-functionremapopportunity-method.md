---
title: "ICorDebugManagedCallback2::FunctionRemapOpportunity – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugManagedCallback2.FunctionRemapOpportunity
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugManagedCallback2::FunctionRemapOpportunity
helpviewer_keywords:
- FunctionRemapOpportunity method [.NET Framework debugging]
- ICorDebugManagedCallback2::FunctionRemapOpportunity method [.NET Framework debugging]
ms.assetid: 0d6471bc-ad9b-4b1d-a307-c10443918863
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 208803acea65b24429938dc646e7abe70949b237
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmanagedcallback2functionremapopportunity-method"></a>ICorDebugManagedCallback2::FunctionRemapOpportunity – metoda
Upozorní ladicí program, že provádění kódu dosáhl bod sekvence ve starší verzi upravená funkce.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT FunctionRemapOpportunity (  
    [in] ICorDebugAppDomain   *pAppDomain,  
    [in] ICorDebugThread      *pThread,  
    [in] ICorDebugFunction    *pOldFunction,  
    [in] ICorDebugFunction    *pNewFunction,  
    [in] ULONG32              oldILOffset  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pAppDomain`  
 [v] Ukazatel na ICorDebugAppDomain objekt, který představuje doménu aplikace obsahující upravená funkce.  
  
 `pThread`  
 [v] Ukazatel na ICorDebugThread objekt, který reprezentuje vláken, na kterém byl zjištěn bod přemapování přerušení.  
  
 `pOldFunction`  
 [v] Ukazatel na ICorDebugFunction objekt, který představuje verzi funkce, která aktuálně běží ve vlákně.  
  
 `pNewFunction`  
 [v] Ukazatel na ICorDebugFunction objekt, který představuje nejnovější verzi funkce.  
  
 `oldILOffset`  
 [v] Posun (MSIL intermediate language) Microsoft ukazatel instrukce v předchozí verzi funkce.  
  
## <a name="remarks"></a>Poznámky  
 Tato zpětného volání umožní ladicího programu přemapovat ukazatel instrukce na správné místo v nové verzi zadaná funkce voláním [icordebugilframe2::remapfunction –](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe2-remapfunction-method.md) metoda. Pokud ladicí program nevyvolá `RemapFunction` před voláním [icordebugcontroller::Continue –](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) metoda, modul runtime budou i nadále spouštět původní kód a bude platit jiné `FunctionRemapOpportunity` zpětného volání na další bod sekvence.  
  
 Pro každý rámce, který spouští starší verzi danou funkci dokud ladicí program vrátí S_OK bude volána tento zpětného volání.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICorDebugManagedCallback2 – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)  
 [ICorDebugManagedCallback – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
