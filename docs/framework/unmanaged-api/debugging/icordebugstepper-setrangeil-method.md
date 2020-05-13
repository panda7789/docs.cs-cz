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
ms.openlocfilehash: 7fadffaab6eee5beed513f339ea300acef5a1c6b
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378993"
---
# <a name="icordebugsteppersetrangeil-method"></a>ICorDebugStepper::SetRangeIL – metoda
Nastaví hodnotu, která určuje, zda volání [ICorDebugStepper:: StepRange –](icordebugstepper-steprange-method.md) předávají hodnoty argumentů, které jsou relativní vzhledem k nativnímu kódu nebo relativně k kódu jazyka MSIL (Microsoft Intermediate Language) metody, která je laděna prostřednictvím.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT SetRangeIL (  
    [in] BOOL    bIL  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `bIL`  
 pro Nastavte na hodnotu `true` , chcete-li určit, že rozsahy jsou relativní vzhledem k kódu jazyka MSIL. Nastavte na hodnotu `false` , chcete-li určit, že rozsahy jsou relativní vzhledem k nativnímu kódu. Výchozí hodnota je `true`.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
