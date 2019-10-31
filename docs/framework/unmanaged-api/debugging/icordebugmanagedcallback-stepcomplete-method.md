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
ms.openlocfilehash: e044b1a2ad777868e33cd64bc8d09a9b76d547aa
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130670"
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

- [ICorDebugManagedCallback – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
