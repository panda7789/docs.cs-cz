---
title: ICorDebugChain::GetActiveFrame – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugChain.GetActiveFrame
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::GetActiveFrame
helpviewer_keywords:
- ICorDebugChain::GetActiveFrame method [.NET Framework debugging]
- GetActiveFrame method, ICorDebugChain interface [.NET Framework debugging]
ms.assetid: 36887017-670b-4f21-b406-8fab956f84a3
topic_type:
- apiref
ms.openlocfilehash: 03cb1556ee971124ed4c591f38d9f892fc7df7b0
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73192143"
---
# <a name="icordebugchaingetactiveframe-method"></a>ICorDebugChain::GetActiveFrame – metoda
Získá aktivní (tj. poslední) rámec v řetězu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetActiveFrame (  
    [out] ICorDebugFrame   **ppFrame  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `ppFrame`  
 mimo Ukazatel na adresu objektu ICorDebugFrame, který představuje aktivní (tj. poslední) rámec v řetězci.  
  
## <a name="remarks"></a>Poznámky  
 Pokud není k dispozici žádný spravovaný rámec zásobníku, je `ppFrame` nastavena na hodnotu null.  
  
 Pokud aktivní rámec není k dispozici, bude volání úspěšné a `ppFrame` bude mít hodnotu null. Aktivní rámce nebudou k dispozici pro řetězy iniciované v důsledku CHAIN_ENTER_UNMANAGED a pro některé řetězy iniciované z CHAIN_CLASS_INIT. Podívejte se na výčet CorDebugChainReason –.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
