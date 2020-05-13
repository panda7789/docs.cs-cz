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
ms.openlocfilehash: 83ac91133b226e2ac263356941c3fc3288355e7e
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379940"
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
 pro `mdFieldDef`Token, který určuje statické pole.  
  
 `pFrame`  
 pro Ukazatel na ICorDebugFrame, který představuje rámec zásobníku.  
  
 `ppValue`  
 mimo Ukazatel na adresu `ICorDebugValue` , která obsahuje hodnotu statického pole.  
  
## <a name="remarks"></a>Poznámky  
 `GetStaticFieldValue`Metoda může být použita pouze v případě, že je typ ELEMENT_TYPE_CLASS nebo ELEMENT_TYPE_VALUETYPE, jak je uvedeno v metodě [ICorDebugType:: GetType](icordebugtype-gettype-method.md) .  
  
 U neobecných typů operace prováděná `GetStaticFieldValue` je shodná s voláním [ICorDebugClass:: GetStaticFieldValue](icordebugclass-getstaticfieldvalue-method.md) na objektu ICorDebugClass, který vrací [ICorDebugType:: GetClass](icordebugtype-getclass-method.md).  
  
 U obecných typů bude hodnota statického pole relativní vzhledem k konkrétní instanci. Také, pokud by mohlo být statické pole relativní vzhledem ke vláknu, kontextu nebo doméně aplikace, pak rámec zásobníku pomůže ladicímu programu určit správnou hodnotu.  
  
## <a name="remarks"></a>Poznámky  
 `GetStaticFieldValue`lze ji použít pouze v případě, že volání `ICorDebugType::GetType` vrátí hodnotu ELEMENT_TYPE_CLASS nebo ELEMENT_TYPE_VALUETYPE.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
