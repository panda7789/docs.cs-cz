---
title: ICorDebugEval2::RudeAbort – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugEval2.RudeAbort
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval2::RudeAbort
helpviewer_keywords:
- ICorDebugEval2::RudeAbort method [.NET Framework debugging]
- RudeAbort method, ICorDebugEval2 interface [.NET Framework debugging]
ms.assetid: 02468edf-d32b-4cb3-aaa8-3dd2abfc8b25
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4a1adb79e5081fc909d0cd180d8161eccea7e58e
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67754351"
---
# <a name="icordebugeval2rudeabort-method"></a>ICorDebugEval2::RudeAbort – metoda
Zruší výpočet, který tato `ICorDebugEval2` v tuto chvíli provádí.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT RudeAbort ();  
```  
  
## <a name="remarks"></a>Poznámky  
 `RudeAbort` neuvolní žádné zámky, které obsahuje Chyba při vyhodnocování, tak se relace ladění zůstane ve stavu unsafe. Volání této metody s nejvyšší opatrností.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
