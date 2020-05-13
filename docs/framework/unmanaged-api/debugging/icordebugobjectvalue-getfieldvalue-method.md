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
ms.openlocfilehash: 660bc13e8109994f59444c0adebbc97f54de0b43
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83207593"
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
 pro `mdFieldDef`Token, který odkazuje na metadata popisující pole.  
  
 `ppValue`  
 mimo Ukazatel na objekt "ICorDebugValue", který představuje hodnotu zadaného pole.  
  
## <a name="remarks"></a>Poznámky  
 Třída zadaná v `pClass` parametru musí být v hierarchii třídy Value objektu a pole musí být pole této třídy.  
  
 `GetFieldValue`Metoda bude stále úspěšná pro obecné objekty a obecné třídy. Například pokud MyDictionary \< V> dědí z \< řetězce slovníku, V> a hodnota objektu je typu MyDictionary \< Int32>, předáním `ICorDebugClass` objektu pro slovník \< k, v> se úspěšně získá pole \< řetězce slovníku, Int32>.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také
