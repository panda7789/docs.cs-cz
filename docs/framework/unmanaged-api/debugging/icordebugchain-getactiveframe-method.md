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
ms.openlocfilehash: 2f67188539d5ad5523c255fbc663e990e1b8245f
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82894682"
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
 Pokud není k dispozici žádný spravovaný rámec `ppFrame` zásobníku, je nastaven na hodnotu null.  
  
 Pokud aktivní rámec není k dispozici, volání bude úspěšné a `ppFrame` bude mít hodnotu null. Aktivní rámce nebudou k dispozici pro řetězy iniciované v důsledku CHAIN_ENTER_UNMANAGED a pro některé řetězy iniciované z CHAIN_CLASS_INIT. Podívejte se na výčet CorDebugChainReason –.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
