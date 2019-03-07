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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2c6b86c5ce3cc246af600d9b65d2fe12a0427f9f
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57485392"
---
# <a name="icordebugtypegetstaticfieldvalue-method"></a>ICorDebugType::GetStaticFieldValue – metoda
Získá ukazatel rozhraní na ICorDebugValue objekt, který obsahuje hodnotu statické pole určené pole odkazuje tokenu v určeném zásobníku rámce.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetStaticFieldValue (  
    [in]  mdFieldDef        fieldDef,  
    [in]  ICorDebugFrame    *pFrame,  
    [out] ICorDebugValue    **ppValue  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `fieldDef`  
 [in] `mdFieldDef` Token, který určuje statické pole.  
  
 `pFrame`  
 [in] Ukazatel na ICorDebugFrame, který představuje rámec zásobníku.  
  
 `ppValue`  
 [out] Ukazatel na adresu `ICorDebugValue` , který obsahuje hodnotu statické pole.  
  
## <a name="remarks"></a>Poznámky  
 `GetStaticFieldValue` – Metoda může použít pouze v případě, že typ je za řetězcem ELEMENT_TYPE_CLASS nebo ELEMENT_TYPE_VALUETYPE, znázorněné [icordebugtype::gettype –](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-gettype-method.md) metody.  
  
 Pro obecné typy, operace provedena `GetStaticFieldValue` je stejný jako volání [icordebugclass::getstaticfieldvalue –](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-getstaticfieldvalue-method.md) ICorDebugClass objektu, který je vrácený [icordebugtype::getclass –](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getclass-method.md).  
  
 Pro obecné typy bude hodnota statické pole vzhledem ke konkrétní vytváření instancí. Navíc pokud statické pole může být může být relativní vzhledem k vlákno, kontext nebo doménu aplikace, pak rámce zásobníku pomůže ladicí program určit správnou hodnotu.  
  
## <a name="remarks"></a>Poznámky  
 `GetStaticFieldValue` se dá použít jenom při volání `ICorDebugType::GetType` vrací hodnotu za řetězcem ELEMENT_TYPE_CLASS nebo ELEMENT_TYPE_VALUETYPE.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
