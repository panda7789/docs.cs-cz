---
title: ICorDebugEval::Abort – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugEval.Abort
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval::Abort
helpviewer_keywords:
- Abort method, ICorDebugEval interface [.NET Framework debugging]
- ICorDebugEval::Abort method [.NET Framework debugging]
ms.assetid: 7070b6d0-f2e0-44ff-b124-0944cd807e69
topic_type:
- apiref
ms.openlocfilehash: 78402e5e099815fe309618e692285de91b8b29f7
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124242"
---
# <a name="icordebugevalabort-method"></a>ICorDebugEval::Abort – metoda
Přeruší výpočet, který tento objekt ICorDebugEval aktuálně provádí.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT Abort ();  
```  
  
## <a name="remarks"></a>Poznámky  
 Pokud je vyhodnocení vnořené a nejedná se o poslední z nich, `Abort` metoda může selhat.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
