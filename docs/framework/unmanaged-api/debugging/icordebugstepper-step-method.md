---
title: ICorDebugStepper::Step – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugStepper.Step
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper::Step
helpviewer_keywords:
- Step method, ICorDebugStepper interface [.NET Framework debugging]
- ICorDebugStepper::Step method [.NET Framework debugging]
ms.assetid: 38c1940b-ada1-40ba-8295-4c0833744e1e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9d0f601c4b454b55edc5fa25eb2ee33d491009b9
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67760565"
---
# <a name="icordebugstepperstep-method"></a>ICorDebugStepper::Step – metoda
Způsobí, že tento icordebugstepper – jedním krokem prostřednictvím jeho nadřazeného vlákna a volitelně do pokračujte v jedné krokování funkcí, které jsou volány vlákna.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT Step (  
    [in] BOOL   bStepIn  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `bStepIn`  
 [in] Nastavte na `true` krok do funkce, která je volána v rámci vlákna. Nastavte na `false` krok přes funkci.  
  
## <a name="remarks"></a>Poznámky  
 Krok dokončí, když modul common language runtime provádí další instrukci spravované v rámci této krokovač. Pokud `Step` se volalo krokovač, která není v spravovaného kódu, krok dokončí další instrukci spravovaný kód je spuštěn metodou vlákna.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
