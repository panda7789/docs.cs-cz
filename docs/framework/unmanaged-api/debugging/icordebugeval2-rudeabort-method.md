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
ms.openlocfilehash: a486935d5d53a6fc7d862160ed1186c5774814c7
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73084800"
---
# <a name="icordebugeval2rudeabort-method"></a>ICorDebugEval2::RudeAbort – metoda
Přeruší výpočet, který tato `ICorDebugEval2` v tuto chvíli provádí.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT RudeAbort ();  
```  
  
## <a name="remarks"></a>Poznámky  
 `RudeAbort` neuvolní žádné zámky, které filtr uchovává, takže relace ladění zůstane v nezabezpečeném stavu. Zavolejte tuto metodu s mimořádnou opatrností.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
