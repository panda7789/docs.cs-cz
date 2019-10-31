---
title: ICorDebugObjectValue::GetFieldValue – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugObjectValue.GetFieldValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugObjectValue::GetFieldValue
helpviewer_keywords:
- ICorDebugObjectValue::GetFieldValue method [.NET Framework debugging]
- GetFieldValue method [.NET Framework debugging]
ms.assetid: c96770b0-3e09-47bb-bd29-20353b043459
topic_type:
- apiref
ms.openlocfilehash: 002c6cccb3ddf29b831ba5e14baa5e51f1b82433
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73095884"
---
# <a name="icordebugobjectvaluegetfieldvalue-method"></a>ICorDebugObjectValue::GetFieldValue – metoda
Získá hodnotu zadaného pole zadané třídy pro tuto hodnotu objektu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetFieldValue (  
    [in]  ICorDebugClass     *pClass,  
    [in]  mdFieldDef         fieldDef,  
    [out] ICorDebugValue     **ppValue  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pClass`  
 pro Ukazatel na objekt "ICorDebugClass", který představuje třídu, pro kterou chcete získat hodnotu pole.  
  
 `fieldDef`  
 pro Token `mdFieldDef`, který odkazuje na metadata popisující pole.  
  
 `ppValue`  
 mimo Ukazatel na objekt "ICorDebugValue", který představuje hodnotu zadaného pole.  
  
## <a name="remarks"></a>Poznámky  
 Třída zadaná v parametru `pClass` musí být v hierarchii třídy Value objektu a pole musí být pole této třídy.  
  
 Metoda `GetFieldValue` bude stále úspěšná pro obecné objekty a obecné třídy. Například pokud MyDictionary\<V > dědí ze slovníku\<String, V > a hodnota objektu je typu MyDictionary\<Int32 >, předáním objektu `ICorDebugClass` pro slovník\<K, V > se úspěšně získá pole\<řetězec slovníku, Int32 >.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:
