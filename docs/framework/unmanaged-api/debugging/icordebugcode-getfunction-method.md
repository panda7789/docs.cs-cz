---
title: ICorDebugCode::GetFunction – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugCode.GetFunction
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode::GetFunction
helpviewer_keywords:
- GetFunction method, ICorDebugCode interface [.NET Framework debugging]
- ICorDebugCode::GetFunction method [.NET Framework debugging]
ms.assetid: c568b737-fdb2-4816-accd-051f5ab760f1
topic_type:
- apiref
ms.openlocfilehash: 9f785eafa8925324e3bd269ca08a3b1367b74c44
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82893592"
---
# <a name="icordebugcodegetfunction-method"></a>ICorDebugCode::GetFunction – metoda
Získá "ICorDebugFunction" spojený s tímto "ICorDebugCode".  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetFunction (  
    [out] ICorDebugFunction **ppFunction  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `ppFunction`  
 mimo Ukazatel na adresu funkce.  
  
## <a name="remarks"></a>Poznámky  
 `ICorDebugCode`a `ICorDebugFunction` Udržujte relaci 1:1.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
