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
ms.openlocfilehash: ba9a4e32216fd6fad285397bfc48fbc54f602b88
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82894653"
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
 mimo Ukazatel na adresu objektu ICorDebugChain, který představuje pojmenovaný řetězec. Pokud tento řetěz aktuálně probíhá (tj. Pokud tento řetěz nečeká na návrat z volaného řetězce), `ppChain` bude mít hodnotu null.  
  
## <a name="remarks"></a>Poznámky  
 Tento řetěz počká, než se volaný řetězec vrátí, než obnoví provádění. Volaný řetěz může být v jiném vlákně v případě volání mezi vlákny zařazování.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
