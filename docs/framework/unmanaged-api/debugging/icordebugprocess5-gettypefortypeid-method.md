---
title: ICorDebugProcess5::GetTypeForTypeID – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.GetTypeForTypeID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::GetTypeForTypeID
helpviewer_keywords:
- GetTypeForTypeID method, ICorDebugProcess5 interface [.NET Framework debugging]
- ICorDebugProcess5::GetTypeForTypeID method [.NET Framework debugging]
ms.assetid: e0eed5a8-fa6d-4818-bd00-7babcea30325
topic_type:
- apiref
ms.openlocfilehash: ea7f7a9d4589e4f08b1b1e20b4d073bb5f822714
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212760"
---
# <a name="icordebugprocess5gettypefortypeid-method"></a>ICorDebugProcess5::GetTypeForTypeID – metoda
Převede identifikátor typu na hodnotu ICorDebugType.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetTypeForTypeID(  
    [in] COR_TYPEID id, [  
    out] ICorDebugType **ppType  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `id`  
 pro Identifikátor typu.  
  
 `ppType`  
 mimo Ukazatel na adresu ICorDebugType objektu.  
  
## <a name="remarks"></a>Poznámky  
 V některých případech metody, které vracejí identifikátor typu, mohou vracet hodnotu null `COR_TYPEID` . Pokud je tato hodnota předána jako `id` argument, `GetTypeForTypeID` metoda selže a vrátí `E_FAIL` .  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [ICorDebugProcess5 – rozhraní](icordebugprocess5-interface.md)
- [Debugging – rozhraní](debugging-interfaces.md)
