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
ms.openlocfilehash: 14291ced9a606cc0b2a3792c2157b7bc2a3460a3
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59190523"
---
# <a name="icordebugmanagedcallback2functionremapopportunity-method"></a>ICorDebugManagedCallback2::FunctionRemapOpportunity – metoda
Upozorní ladicího programu, že spuštění kódu bylo dosaženo bodu sekvence. ve starší verzi funkce se upravila.  
  
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
  
## <a name="parameters"></a>Parametry  
 `pAppDomain`  
 [in] Ukazatel na objekt ICorDebugAppDomain, který představuje doménu aplikace obsahující funkce se upravila.  
  
 `pThread`  
 [in] Ukazatel na objekt icordebugthread –, který představuje vlákno, na kterém byla zjištěna zarážka přemapování.  
  
 `pOldFunction`  
 [in] Ukazatel na objekt ICorDebugFunction, který představuje verzi funkce, která je aktuálně spuštěna ve vlákně.  
  
 `pNewFunction`  
 [in] Ukazatel na objekt ICorDebugFunction, který představuje nejnovější funkce.  
  
 `oldILOffset`  
 [in] Posun Microsoft intermediate language (MSIL) v původní verzi funkce ukazatele na instrukci.  
  
## <a name="remarks"></a>Poznámky  
 Toto zpětné volání poskytuje ladicího programu příležitost k přemapování ukazatele na instrukci na správné místo v nové verzi zadanou funkci pomocí volání [icordebugilframe2::remapfunction –](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe2-remapfunction-method.md) metody. Pokud ladicí program nevolá `RemapFunction` před voláním [icordebugcontroller::Continue –](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) metody, modul runtime bude pokračovat na starý kód spustit a bude platit další `FunctionRemapOpportunity` zpětného volání na další bod sekvence.  
  
 Toto zpětné volání bude volána pro každý snímek, který spouští starší verzi danou funkci dokud ladicí program vrátí hodnotu S_OK.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorDebugManagedCallback2 – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)
- [ICorDebugManagedCallback – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
