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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a104d4d3cc74a6c1cb343818c9b0b3e8978b97df
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugchaingetactiveframe-method"></a>ICorDebugChain::GetActiveFrame – metoda
Získá aktivní (tedy poslední) rámce v řetězu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetActiveFrame (  
    [out] ICorDebugFrame   **ppFrame  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppFrame`  
 [out] Ukazatel na adresu ICorDebugFrame objekt, který představuje aktivní (tedy poslední) rámce v řetězu.  
  
## <a name="remarks"></a>Poznámky  
 Pokud je k dispozici, žádné spravované zásobníku `ppFrame` je nastaven na hodnotu null.  
  
 Pokud aktivní rámečku není k dispozici, volání bude úspěšné a `ppFrame` bude mít hodnotu null. Aktivní rámce nebudete mít k dispozici pro řetězy inicializovat z důvodu CHAIN_ENTER_UNMANAGED a některé řetězy inicializovat z důvodu CHAIN_CLASS_INIT. V tématu CorDebugChainReason – výčet.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
