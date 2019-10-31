---
title: ICorDebugThread::CreateEval – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugThread.CreateEval
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::CreateEval
helpviewer_keywords:
- CreateEval method [.NET Framework debugging]
- ICorDebugThread::CreateEval method [.NET Framework debugging]
ms.assetid: 36605067-33d3-4579-9c72-fb0e551ab0f1
topic_type:
- apiref
ms.openlocfilehash: 0c622e0eba27f501446d2b7d9d264ee0834e869c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133619"
---
# <a name="icordebugthreadcreateeval-method"></a>ICorDebugThread::CreateEval – metoda
Vytvoří objekt ICorDebugEval, který shromažďuje a zpřístupňuje funkce tohoto ICorDebugThread.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT CreateEval (  
    [out] ICorDebugEval   **ppEval  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `ppEval`  
 mimo Ukazatel na adresu `ICorDebugEval` objektu, který shromažďuje a zpřístupňuje funkce tohoto vlákna.  
  
## <a name="remarks"></a>Poznámky  
 Objekt vyhodnocení před provedením výpočtu napředá do vlákna nový řetěz. Tím se přeruší výpočet, který se právě provádí ve vlákně, dokud se nedokončí vyhodnocení.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
