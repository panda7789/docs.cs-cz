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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7b18474aeaa79224de5371df3ff0cac5ed9bf4ff
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61994277"
---
# <a name="icordebugsteppersteprange-method"></a>ICorDebugStepper::StepRange – metoda
Způsobí, že tento icordebugstepper – jedním krokem prostřednictvím jeho nadřazeného vlákna a vrátit se dosáhne kódu za poslední zadaný rozsah.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT StepRange (  
    [in] BOOL     bStepIn,  
    [in, size_is(cRangeCount)] COR_DEBUG_STEP_RANGE ranges[],  
    [in] ULONG32  cRangeCount  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `bStepIn`  
 [in] Nastavte na `true` krok do funkce, která je volána v rámci vlákna. Nastavte na `false` krok přes funkci.  
  
 `ranges`  
 [in] Pole struktur cor_debug_step_range –, z nichž každý určuje rozsah.  
  
 `cRangeCount`  
 [in] Velikost `ranges` pole.  
  
## <a name="remarks"></a>Poznámky  
 `StepRange` Metoda se dá použít jako [icordebugstepper::Step –](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-step-method.md) metody, s tím rozdílem, že nedokončí až do kódu mimo zadaný rozsah je dosaženo.  
  
 To může být efektivnější než krokování jedné instrukce v čase. Rozsahy jsou zadané jako seznam dvojic posunu od začátku krokovač rámce.  
  
 Rozsahy jsou relativní vzhledem k kód Microsoft intermediate language (MSIL) metody. Volání [icordebugstepper::setrangeil –](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setrangeil-method.md) s `false` aby rozsahy vzhledem k nativního kódu metody.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
