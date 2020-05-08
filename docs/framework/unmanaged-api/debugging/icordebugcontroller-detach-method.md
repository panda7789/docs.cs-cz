---
title: ICorDebugController::Detach – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugController.Detach
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugController::Detach
helpviewer_keywords:
- Detach method, ICorDebugController interface [.NET Framework debugging]
- ICorDebugController::Detach method [.NET Framework debugging]
ms.assetid: 06fae364-f2c6-4a50-aa7e-3da9f2684dc3
topic_type:
- apiref
ms.openlocfilehash: 480fec4897dac73594515ba8bc0f0e96ceb79ace
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82892905"
---
# <a name="icordebugcontrollerdetach-method"></a>ICorDebugController::Detach – metoda
Odpojí ladicí program od domény procesu nebo aplikace.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT Detach ();  
```  
  
## <a name="remarks"></a>Poznámky  
 Proces nebo aplikační doména pokračuje v normálním provádění, ale objekt "ICorDebugProcess" nebo "ICorDebugAppDomain" již není platný a žádné další zpětné volání nebudou provedeny.  
  
 Pokud je v .NET Framework verze 2,0, pokud je povoleno ladění nespravovaného kódu, nebude tato metoda v důsledku omezení operačního systému úspěšná.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také
