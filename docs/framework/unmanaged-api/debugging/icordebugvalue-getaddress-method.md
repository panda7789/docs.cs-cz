---
title: ICorDebugValue::GetAddress – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugValue.GetAddress
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValue::GetAddress
helpviewer_keywords:
- ICorDebugValue::GetAddress method [.NET Framework debugging]
- GetAddress method, ICorDebugValue interface [.NET Framework debugging]
ms.assetid: a247c792-45e1-4538-9e1f-b46acca4a463
topic_type:
- apiref
ms.openlocfilehash: 467ba53f90081f0c3499fb22acab96b5e380a3f4
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2020
ms.locfileid: "83395834"
---
# <a name="icordebugvaluegetaddress-method"></a>ICorDebugValue::GetAddress – metoda
Získá adresu tohoto objektu "ICorDebugValue", který je právě laděn.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetAddress (  
    [out] CORDB_ADDRESS   *pAddress  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pAddress`  
 mimo Ukazatel na `CORDB_ADDRESS` objekt, který určuje adresu tohoto objektu hodnoty.  
  
## <a name="remarks"></a>Poznámky  
 Pokud je hodnota nedostupná, vrátí se 0 (nula). K tomu může dojít, pokud je hodnota nejméně částečně v registrech nebo uložená v popisovači systému uvolňování paměti ( `GCHandle` ).  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také
