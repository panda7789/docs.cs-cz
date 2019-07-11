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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0fc65f5b55082970a0cd59a6850aaaa6779d0821
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67766408"
---
# <a name="icordebugobjectvaluegetfieldvalue-method"></a>ICorDebugObjectValue::GetFieldValue – metoda
Získá hodnotu zadaného pole ze zadané třídy pro tuto hodnotu objektu.  
  
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
 [in] Ukazatel na objekt "ICorDebugClass", který představuje třídu, pro kterou má být získána hodnota pole.  
  
 `fieldDef`  
 [in] `mdFieldDef` Token, který odkazuje na metadata popisující pole.  
  
 `ppValue`  
 [out] Ukazatel na objekt "ICorDebugValue", která představuje hodnotu zadaného pole.  
  
## <a name="remarks"></a>Poznámky  
 Třída zadaná v `pClass` parametr, musí být v hierarchii třídy hodnota objektu a pole této třídy musí být pole.  
  
 `GetFieldValue` Metoda i tak proběhne úspěšně obecných objektů a obecné třídy. Například pokud MyDictionary\<V > dědí ze slovníku\<string, V >, a hodnota objekt je typu MyDictionary\<int32 >, předejte `ICorDebugClass` objekt slovníku\<K, V > bude úspěšně získat pole slovníku\<řetězec, int32 >.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:
