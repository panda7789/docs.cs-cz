---
title: ICorDebugManagedCallback::StepComplete – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.StepComplete
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::StepComplete
helpviewer_keywords:
- StepComplete method [.NET Framework debugging]
- ICorDebugManagedCallback::StepComplete method [.NET Framework debugging]
ms.assetid: 5e1f2c47-81df-4530-826d-96489cd68719
topic_type:
- apiref
ms.openlocfilehash: e5d828b8252b47c2edddbe14713208ae8bc2d19d
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76777155"
---
# <a name="icordebugmanagedcallbackstepcomplete-method"></a>ICorDebugManagedCallback::StepComplete – metoda
Oznamuje ladicímu programu, že byl krok dokončen.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT StepComplete (  
    [in] ICorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugThread     *pThread,  
    [in] ICorDebugStepper    *pStepper,  
    [in] CorDebugStepReason   reason  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pAppDomain`  
 pro Ukazatel na objekt ICorDebugAppDomain, který představuje doménu aplikace obsahující vlákno, ve kterém byl krok dokončen.  
  
 `pThread`  
 pro Ukazatel na objekt ICorDebugThread, který představuje vlákno, ve kterém byl krok dokončen.  
  
 `pStepper`  
 pro Ukazatel na objekt ICorDebugStepper, který představuje krok ve spuštění kódu.  
  
 `reason`  
 pro Hodnota výčtu CorDebugStepReason –, která označuje výsledek jednotlivého kroku.  
  
## <a name="remarks"></a>Poznámky  
 Stepper může být použita k pokračování v procházení, pokud je to žádoucí, pokud ladění není ukončeno.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorDebugManagedCallback – rozhraní](icordebugmanagedcallback-interface.md)
