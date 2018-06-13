---
title: ICorDebugManagedCallback2::FunctionRemapOpportunity – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback2.FunctionRemapOpportunity
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback2::FunctionRemapOpportunity
helpviewer_keywords:
- FunctionRemapOpportunity method [.NET Framework debugging]
- ICorDebugManagedCallback2::FunctionRemapOpportunity method [.NET Framework debugging]
ms.assetid: 0d6471bc-ad9b-4b1d-a307-c10443918863
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: dc900ca20ac87ddecfd8f7adf0894af21ca5d2f0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33418087"
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
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICorDebugManagedCallback2 – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)  
 [ICorDebugManagedCallback – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
