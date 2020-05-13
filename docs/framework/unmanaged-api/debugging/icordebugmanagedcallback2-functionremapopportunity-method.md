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
ms.openlocfilehash: d2fc59621cbb6752830c7a8392ce4e0c476ef9e7
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83210056"
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
 Toto zpětné volání umožňuje ladicímu programu možnost přemapovat ukazatel na jeho správné místo v nové verzi zadané funkce voláním metody [ICorDebugILFrame2:: RemapFunction](icordebugilframe2-remapfunction-method.md) . Pokud ladicí program nevolá `RemapFunction` před voláním metody [ICorDebugController:: Continue](icordebugcontroller-continue-method.md) , modul runtime bude pokračovat v provádění starého kódu a vyvolá jiné `FunctionRemapOpportunity` zpětné volání v dalším bodu sekvence.  
  
 Toto zpětné volání bude vyvoláno pro každý rámec, který spouští starší verzi dané funkce, dokud ladicí program nevrátí S_OK.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [ICorDebugManagedCallback2 – rozhraní](icordebugmanagedcallback2-interface.md)
- [ICorDebugManagedCallback – rozhraní](icordebugmanagedcallback-interface.md)
