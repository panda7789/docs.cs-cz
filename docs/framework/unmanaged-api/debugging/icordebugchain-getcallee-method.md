---
title: ICorDebugChain::GetCallee – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugChain.GetCallee
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::GetCallee method
helpviewer_keywords:
- ICorDebugChain::GetCallee method [.NET Framework debugging]
- GetCallee method, ICorDebugChain interface [.NET Framework debugging]
ms.assetid: 19560c79-abdc-4bdf-a5fe-eb362a59edc0
topic_type:
- apiref
ms.openlocfilehash: 5d28af09faae84b0482d438ae33f593f250490c1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73196329"
---
# <a name="icordebugchaingetcallee-method"></a>ICorDebugChain::GetCallee – metoda
Získá řetězec, který byl volán tímto řetězem.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetCallee (  
    [out] ICorDebugChain     **ppChain  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `ppChain`  
 mimo Ukazatel na adresu objektu ICorDebugChain, který představuje pojmenovaný řetězec. Pokud je tento řetěz aktuálně prováděn (tj. Pokud tento řetěz nečeká na návrat z volaného řetězce), `ppChain` bude null.  
  
## <a name="remarks"></a>Poznámky  
 Tento řetěz počká, než se volaný řetězec vrátí, než obnoví provádění. Volaný řetěz může být v jiném vlákně v případě volání mezi vlákny zařazování.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
