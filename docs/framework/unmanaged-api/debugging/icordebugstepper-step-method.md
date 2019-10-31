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
ms.openlocfilehash: 43f86e704e4a52a702b8f563e3c613806eb061b5
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137534"
---
# <a name="icordebugstepperstep-method"></a>ICorDebugStepper::Step – metoda
Způsobí, že se toto ICorDebugStepper do jednoho kroku prostřednictvím jeho obsahujícího vlákna a volitelně také pro pokračování v jednoduchém prostředí prostřednictvím funkcí, které jsou volány ve vlákně.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT Step (  
    [in] BOOL   bStepIn  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `bStepIn`  
 pro Nastavte na `true` pro krokování do funkce, která je volána v rámci vlákna. Nastavte na `false` pro krok nad funkcí.  
  
## <a name="remarks"></a>Poznámky  
 Krok se dokončí, když modul CLR (Common Language Runtime) provede další spravovanou instrukci v tomto stepper snímku. Pokud je `Step` volána na stepper, který není ve spravovaném kódu, krok bude dokončen, když vlákno provede další instrukci spravovaného kódu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
