---
title: ICorDebugStepper::StepOut – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugStepper.StepOut
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper::StepOut
helpviewer_keywords:
- ICorDebugStepper::StepOut method [.NET Framework debugging]
- StepOut method [.NET Framework debugging]
ms.assetid: aae0f48c-4ede-4256-9251-a7fc85a229dc
topic_type:
- apiref
ms.openlocfilehash: 6c1d7db8aacaf81d47abd4a9cd972b44f56a3bb1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137512"
---
# <a name="icordebugstepperstepout-method"></a>ICorDebugStepper::StepOut – metoda
Způsobí, že se toto ICorDebugStepper do jediného kroku prostřednictvím jeho obsahujícího vlákna a bude dokončeno, když aktuální rámec vrátí řízení volajícímu snímku.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT StepOut ();  
```  
  
## <a name="remarks"></a>Poznámky  
 Operace `StepOut` se dokončí po běžném návratu z aktuálního rámce do volajícího rámce.  
  
 Pokud je zavolána `StepOut` v nespravovaném kódu, krok bude dokončen, když se aktuální rámec vrátí do spravovaného kódu, který jej volal.  
  
 V .NET Framework verze 2,0 nepoužívejte `StepOut` s nastaveným příznakem STOP_UNMANAGED, protože selže. (K nastavení příznaků pro krokování použijte [ICorDebugStepper:: SetUnmappedStopMask –](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md) .) Ladicí program spolupráce musí Krokovat s nativním samotným kódem.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
