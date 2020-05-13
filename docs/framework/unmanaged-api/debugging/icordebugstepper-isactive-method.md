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
ms.openlocfilehash: faddf30248b58c68037635480d8977f22ad077d0
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379026"
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
 mimo Vrátí, `true` zda stepper aktuálně provádí krok. v opačném případě vrátí hodnotu `false` .  
  
## <a name="remarks"></a>Poznámky  
 Jakákoli akce kroku zůstane aktivní, dokud ladicí program nepřijme volání [ICorDebugManagedCallback:: StepComplete –](icordebugmanagedcallback-stepcomplete-method.md) , které automaticky deaktivuje stepper. Stepper se může předčasně deaktivovat také voláním [ICorDebugStepper::D eactivate](icordebugstepper-deactivate-method.md) před dosažením podmínky zpětného volání.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
