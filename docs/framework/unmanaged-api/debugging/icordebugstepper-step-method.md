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
ms.openlocfilehash: 39d2fd0163b0e61295187461d5dbdf5742450306
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379519"
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
 pro Nastavte na `true` pro krokování do funkce, která je volána v rámci vlákna. Nastavte na `false` krok nad funkcí.  
  
## <a name="remarks"></a>Poznámky  
 Krok se dokončí, když modul CLR (Common Language Runtime) provede další spravovanou instrukci v tomto stepper snímku. Pokud `Step` je volána na stepper, který není ve spravovaném kódu, krok bude dokončen, když vlákno provede další instrukci spravovaného kódu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
