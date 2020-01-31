---
title: ICorDebugType::GetStaticFieldValue – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugType.GetStaticFieldValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType::GetStaticFieldValue
helpviewer_keywords:
- GetStaticFieldValue method, ICorDebugType interface [.NET Framework debugging]
- ICorDebugType::GetStaticFieldValue method [.NET Framework debugging]
ms.assetid: 62eb5d55-53ee-4fb3-8d47-7b6c96808f9e
topic_type:
- apiref
ms.openlocfilehash: 37bf5abf66b613d8432af84c7d73aff60e9127cb
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791264"
---
# <a name="icordebugtypegetstaticfieldvalue-method"></a>ICorDebugType::GetStaticFieldValue – metoda
Získá ukazatel rozhraní na objekt ICorDebugValue, který obsahuje hodnotu statického pole, na které se odkazuje pomocí zadaného tokenu pole v zadaném bloku zásobníku.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetStaticFieldValue (  
    [in]  mdFieldDef        fieldDef,  
    [in]  ICorDebugFrame    *pFrame,  
    [out] ICorDebugValue    **ppValue  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `fieldDef`  
 pro `mdFieldDef` token, který určuje statické pole.  
  
 `pFrame`  
 pro Ukazatel na ICorDebugFrame, který představuje rámec zásobníku.  
  
 `ppValue`  
 mimo Ukazatel na adresu `ICorDebugValue`, která obsahuje hodnotu statického pole.  
  
## <a name="remarks"></a>Poznámky  
 Metodu `GetStaticFieldValue` lze použít pouze v případě, že je typ ELEMENT_TYPE_CLASS nebo ELEMENT_TYPE_VALUETYPE, jak je uvedeno v metodě [ICorDebugType:: GetType](icordebugtype-gettype-method.md) .  
  
 U neobecných typů je operace prováděná `GetStaticFieldValue` shodná s voláním metody [ICorDebugClass:: GetStaticFieldValue](icordebugclass-getstaticfieldvalue-method.md) na objektu ICorDebugClass, který vrací [ICorDebugType:: GetClass](icordebugtype-getclass-method.md).  
  
 U obecných typů bude hodnota statického pole relativní vzhledem k konkrétní instanci. Také, pokud by mohlo být statické pole relativní vzhledem ke vláknu, kontextu nebo doméně aplikace, pak rámec zásobníku pomůže ladicímu programu určit správnou hodnotu.  
  
## <a name="remarks"></a>Poznámky  
 `GetStaticFieldValue` lze použít pouze v případě, že volání `ICorDebugType::GetType` vrátí hodnotu ELEMENT_TYPE_CLASS nebo ELEMENT_TYPE_VALUETYPE.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
