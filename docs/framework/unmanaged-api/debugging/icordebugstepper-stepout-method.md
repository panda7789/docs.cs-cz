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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 36a33b74a692761d772a888ce918aa28a2d92678
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67760553"
---
# <a name="icordebugstepperstepout-method"></a>ICorDebugStepper::StepOut – metoda
Způsobí, že tento icordebugstepper – jedním krokem prostřednictvím jeho nadřazeného vlákna a dokončit, jakmile aktuální rámec vrátí řízení volající rámec.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT StepOut ();  
```  
  
## <a name="remarks"></a>Poznámky  
 A `StepOut` operace se dokončí po návratu obvykle aktuální rámec volání rámce.  
  
 Pokud `StepOut` je volána, když v nespravovaném kódu, krok dokončí aktuální rámec návratu do spravovaného kódu, která ji zavolala.  
  
 V rozhraní .NET Framework verze 2.0, nepoužívejte `StepOut` s STOP_UNMANAGED příznak nastaven, protože se nezdaří. (Použití [icordebugstepper::setunmappedstopmask –](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md) nastavení příznaků pro krokování.) Spolupráce ladicí programy musí Krok ven do nativního kódu sami.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
