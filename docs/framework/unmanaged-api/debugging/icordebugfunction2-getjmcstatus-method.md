---
title: ICorDebugFunction2::GetJMCStatus – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugFunction2.GetJMCStatus
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction2::GetJMCStatus
helpviewer_keywords:
- ICorDebugFunction2::GetJMCStatus method [.NET Framework debugging]
- GetJMCStatus method [.NET Framework debugging]
ms.assetid: 840a71ed-bf5a-4f5e-8ed6-762222b34493
topic_type:
- apiref
ms.openlocfilehash: 360434fe6e08804d8c80c4ea36d585209cc6761a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137809"
---
# <a name="icordebugfunction2getjmcstatus-method"></a>ICorDebugFunction2::GetJMCStatus – metoda
Získá hodnotu, která označuje, zda je funkce reprezentovaná tímto objektem ICorDebugFunction2 označena jako uživatelský kód.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetJMCStatus (  
    [out] BOOL   *pbIsJustMyCode  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pbIsJustMyCode`  
 mimo Ukazatel na logickou hodnotu, která je `true`, pokud je tato funkce označena jako kód uživatele; v opačném případě je hodnota `false`.  
  
## <a name="remarks"></a>Poznámky  
 Pokud funkce reprezentovaná tímto `ICorDebugFunction2` nemůže být Laděna, `pbIsJustMyCode` bude vždy `false`.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
