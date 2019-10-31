---
title: ICorDebugThread::GetUserState – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugThread.GetUserState
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::GetUserState
helpviewer_keywords:
- GetUserState method, ICorDebugThread interface [.NET Framework debugging]
- ICorDebugThread::GetUserState method [.NET Framework debugging]
ms.assetid: ae0cfd73-8ead-4d36-9310-dccaac9db0bd
topic_type:
- apiref
ms.openlocfilehash: f3511ff5ee9b9221037c64a5e17d61f6bf52e5f3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133417"
---
# <a name="icordebugthreadgetuserstate-method"></a>ICorDebugThread::GetUserState – metoda
Načte aktuální stav uživatele tohoto ICorDebugThread.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetUserState (  
    [out] CorDebugUserState   *pState  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pState`  
 mimo Ukazatel na bitovou kombinaci hodnot výčtu CorDebugUserState –, které popisují aktuální stav uživatele tohoto vlákna.  
  
## <a name="remarks"></a>Poznámky  
 Stav uživatele vlákna je stav vlákna, když je testován program, který je právě laděn. Vlákno může mít několik sad bitů stavu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
