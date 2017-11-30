---
title: "ICorDebugObjectValue::GetFieldValue – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugObjectValue.GetFieldValue
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugObjectValue::GetFieldValue
helpviewer_keywords:
- ICorDebugObjectValue::GetFieldValue method [.NET Framework debugging]
- GetFieldValue method [.NET Framework debugging]
ms.assetid: c96770b0-3e09-47bb-bd29-20353b043459
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 33c3f368d9b78b899f54c989427ea1f660346487
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugobjectvaluegetfieldvalue-method"></a>ICorDebugObjectValue::GetFieldValue – metoda
Získá hodnotu zadaného pole pro zadanou třídu pro tuto hodnotu objektu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetFieldValue (  
    [in]  ICorDebugClass     *pClass,  
    [in]  mdFieldDef         fieldDef,  
    [out] ICorDebugValue     **ppValue  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pClass`  
 [v] Ukazatel na objekt "ICorDebugClass", který představuje třídu, pro kterou má být získána hodnota pole.  
  
 `fieldDef`  
 [v] `mdFieldDef` Token, který odkazuje na metadata popisující pole.  
  
 `ppValue`  
 [out] Ukazatel na objekt "ICorDebugValue", který představuje hodnotu zadaného pole.  
  
## <a name="remarks"></a>Poznámky  
 Zadaná třída, v `pClass` parametr, musí být v hierarchii třídy hodnota objektu, a v poli musí být pole této třídy.  
  
 `GetFieldValue` Metoda bude stále úspěšné pro obecné objekty a obecné třídy. Například pokud MyDictionary\<V > dědí ze slovníku\<řetězce, V >, a hodnota objekt je typu MyDictionary\<int32 >, předejte `ICorDebugClass` objekt pro slovník\<tisíc, V > bude byl úspěšně načten pole slovník\<string, int32 >.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
    
 
