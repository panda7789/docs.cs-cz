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
ms.openlocfilehash: c6c361113a441df050a8e7cd5219819cc8332581
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131482"
---
# <a name="icordebugmanagedcallback2functionremapopportunity-method"></a>ICorDebugManagedCallback2::FunctionRemapOpportunity – metoda
Oznamuje ladicímu programu, že provádění kódu dosáhlo bodu sekvence ve starší verzi upravované funkce.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
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
 pro Ukazatel na objekt ICorDebugAppDomain, který představuje doménu aplikace obsahující upravenou funkci.  
  
 `pThread`  
 pro Ukazatel na objekt ICorDebugThread, který představuje vlákno, ve kterém byla zjištěna zarážka přemapování.  
  
 `pOldFunction`  
 pro Ukazatel na objekt ICorDebugFunction, který představuje verzi funkce, která je aktuálně spuštěna ve vlákně.  
  
 `pNewFunction`  
 pro Ukazatel na objekt ICorDebugFunction, který představuje nejnovější verzi funkce.  
  
 `oldILOffset`  
 pro Posun jazyka MSIL (Microsoft Intermediate Language) ukazatele na instrukci ve staré verzi funkce.  
  
## <a name="remarks"></a>Poznámky  
 Toto zpětné volání umožňuje ladicímu programu možnost přemapovat ukazatel na jeho správné místo v nové verzi zadané funkce voláním metody [ICorDebugILFrame2:: RemapFunction](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe2-remapfunction-method.md) . Pokud ladicí program nevolá `RemapFunction` před voláním metody [ICorDebugController:: Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) , modul runtime bude pokračovat v provádění starého kódu a vyvolá jiné zpětné volání `FunctionRemapOpportunity` v dalším bodu sekvence.  
  
 Toto zpětné volání bude vyvoláno pro každý rámec, který spouští starší verzi dané funkce, dokud ladicí program nevrátí hodnotu S_OK.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorDebugManagedCallback2 – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)
- [ICorDebugManagedCallback – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
