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
ms.openlocfilehash: c2d282e27ec5068fa6fe7f58ba95458fdc219972
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33419221"
---
# <a name="icordebugstepperstep-method"></a>ICorDebugStepper::Step – metoda
Způsobí, že tento ICorDebugStepper jedním krokem přes jeho obsahující vláken a volitelně můžete do pokračovat jedním procházení funkce, které se nazývají vlákna.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT Step (  
    [in] BOOL   bStepIn  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `bStepIn`  
 [v] Nastavte na `true` k krokování s vnořením funkci, která je volána v rámci vlákno. Nastavte na `false` krok přes funkci.  
  
## <a name="remarks"></a>Poznámky  
 V kroku dokončení, když modul common language runtime provede další instrukce spravované v rámci této krokovač. Pokud `Step` je volána na krokovač, který se nenachází ve spravovaném kódu, krok dokončí při další instrukce spravovaného kódu vlákno.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
