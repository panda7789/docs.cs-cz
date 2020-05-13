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
ms.openlocfilehash: 9f6962f987079da1ccb04ea368307d7c119910a6
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379497"
---
# <a name="icordebugstepperstepout-method"></a>ICorDebugStepper::StepOut – metoda
Způsobí, že se toto ICorDebugStepper do jediného kroku prostřednictvím jeho obsahujícího vlákna a bude dokončeno, když aktuální rámec vrátí řízení volajícímu snímku.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT StepOut ();  
```  
  
## <a name="remarks"></a>Poznámky  
 `StepOut`Operace se dokončí po běžném návratu z aktuálního rámce do volajícího rámce.  
  
 Pokud `StepOut` je volána při v nespravovaném kódu, krok bude dokončen, když se aktuální rámec vrátí ke spravovanému kódu, který jej volal.  
  
 V .NET Framework verze 2,0 Nepoužívejte `StepOut` s nastaveným příznakem STOP_UNMANAGED, protože selže. (K nastavení příznaků pro krokování použijte [ICorDebugStepper:: SetUnmappedStopMask –](icordebugstepper-setunmappedstopmask-method.md) .) Ladicí program spolupráce musí Krokovat s nativním samotným kódem.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
