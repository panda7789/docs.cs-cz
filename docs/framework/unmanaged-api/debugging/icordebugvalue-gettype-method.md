---
title: ICorDebugValue::GetType – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugValue.GetType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValue::GetType
helpviewer_keywords:
- ICorDebugValue::GetType method [.NET Framework debugging]
- GetType method, ICorDebugValue interface [.NET Framework debugging]
ms.assetid: 41e2d503-e1f1-407b-abe0-6a29adb3e0d1
topic_type:
- apiref
ms.openlocfilehash: 7def2bd2c0f3ab501fdb918a0e9a7ee154159b78
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791157"
---
# <a name="icordebugvaluegettype-method"></a>ICorDebugValue::GetType – metoda
Získá primitivní typ tohoto objektu "ICorDebugValue".  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetType (  
    [out] CorElementType   *pType  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pType`  
 mimo Ukazatel na hodnotu výčtu "CorElementType –", která označuje typ hodnoty.  
  
## <a name="remarks"></a>Poznámky  
 Pokud je objekt složitým typem běhu, lze tento typ prozkoumat pomocí příslušných podtříd `ICorDebugValue` rozhraní. Například "ICorDebugObjectValue", který dědí z `ICorDebugValue`představuje komplexní typ.  
  
 Metody `GetType` a [ICorDebugObjectValue:: GetClass](icordebugobjectvalue-getclass-method.md) každou vrací informace o typu hodnoty. Jsou obě nahrazeny metodou [ICorDebugValue2:: GetExactType –](icordebugvalue2-getexacttype-method.md) , která se s ohledem na obecné typy nahrazují.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:
