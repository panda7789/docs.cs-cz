---
title: ICorDebugStepper::IsActive – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugStepper.IsActive
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper::IsActive
helpviewer_keywords:
- IsActive method, ICorDebugStepper interface [.NET Framework debugging]
- ICorDebugStepper::IsActive method [.NET Framework debugging]
ms.assetid: 8b35e7a9-b40e-40a9-8d8e-b82e823fc575
topic_type:
- apiref
ms.openlocfilehash: a242764710d92e81e8089bc2919734bfac4bcdb2
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137562"
---
# <a name="icordebugstepperisactive-method"></a>ICorDebugStepper::IsActive – metoda
Načte hodnotu, která označuje, jestli tento ICorDebugStepper aktuálně provádí krok.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT IsActive (  
    [out] BOOL   *pbActive  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pbActive`  
 mimo Vrátí `true`, pokud stepper aktuálně provádí krok; v opačném případě vrátí `false`.  
  
## <a name="remarks"></a>Poznámky  
 Jakákoli akce kroku zůstane aktivní, dokud ladicí program nepřijme volání [ICorDebugManagedCallback:: StepComplete –](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-stepcomplete-method.md) , které automaticky deaktivuje stepper. Stepper se může předčasně deaktivovat také voláním [ICorDebugStepper::D eactivate](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-deactivate-method.md) před dosažením podmínky zpětného volání.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
