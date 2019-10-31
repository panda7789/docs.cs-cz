---
title: ICorDebugStepper::SetRangeIL – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugStepper.SetRangeIL
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper::SetRangeIL
helpviewer_keywords:
- SetRangeIL method [.NET Framework debugging]
- ICorDebugStepper::SetRangeIL method [.NET Framework debugging]
ms.assetid: a20c95f0-6da7-4b41-b27f-584211cebb92
topic_type:
- apiref
ms.openlocfilehash: 88270cb73515cc1a671bfb3fb5c479697ad7b359
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137547"
---
# <a name="icordebugsteppersetrangeil-method"></a>ICorDebugStepper::SetRangeIL – metoda
Nastaví hodnotu, která určuje, zda volání [ICorDebugStepper:: StepRange –](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md) předávají hodnoty argumentů, které jsou relativní vzhledem k nativnímu kódu nebo relativně k kódu jazyka MSIL (Microsoft Intermediate Language) metody, která je laděna prostřednictvím.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetRangeIL (  
    [in] BOOL    bIL  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `bIL`  
 pro Nastavte na `true` a určete tak, že rozsahy jsou relativní vzhledem k kódu jazyka MSIL. Nastavte na `false` a určete tak, že rozsahy jsou relativní vzhledem k nativnímu kódu. Výchozí hodnota je `true`.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
