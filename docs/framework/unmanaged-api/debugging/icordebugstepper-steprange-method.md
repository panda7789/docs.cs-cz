---
title: ICorDebugStepper::StepRange – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugStepper.StepRange
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper::StepRange
helpviewer_keywords:
- StepRange method [.NET Framework debugging]
- ICorDebugStepper::StepRange method [.NET Framework debugging]
ms.assetid: b9776112-6e6d-4708-892a-8873db02e16f
topic_type:
- apiref
ms.openlocfilehash: 21b8bf618e197372e301d5f56e7592c20710014d
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791710"
---
# <a name="icordebugsteppersteprange-method"></a>ICorDebugStepper::StepRange – metoda
Způsobí, že se toto ICorDebugStepper do jednoho kroku prostřednictvím jeho obsahujícího vlákna a vrátí se, když dosáhne kódu za poslední z určených rozsahů.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT StepRange (  
    [in] BOOL     bStepIn,  
    [in, size_is(cRangeCount)] COR_DEBUG_STEP_RANGE ranges[],  
    [in] ULONG32  cRangeCount  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `bStepIn`  
 pro Nastavte na `true` pro krokování do funkce, která je volána v rámci vlákna. Nastavte na `false` pro krok nad funkcí.  
  
 `ranges`  
 pro Pole struktur COR_DEBUG_STEP_RANGE, z nichž každý určuje rozsah.  
  
 `cRangeCount`  
 pro Velikost pole `ranges`.  
  
## <a name="remarks"></a>Poznámky  
 Metoda `StepRange` funguje podobně jako metoda [ICorDebugStepper:: Step](icordebugstepper-step-method.md) , s tím rozdílem, že není dokončena, dokud není dosaženo kódu mimo daný rozsah.  
  
 To může být efektivnější než v jednom okamžiku krokování jednotlivých instrukcí. Rozsahy jsou zadány jako seznam párů posunů od začátku rámce stepper.  
  
 Rozsahy jsou relativní vzhledem k kódu jazyka MSIL (Microsoft Intermediate Language) metody. Zavolejte [ICorDebugStepper:: SetRangeIL –](icordebugstepper-setrangeil-method.md) s `false`, aby byly rozsahy relativní vzhledem k nativnímu kódu metody.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
