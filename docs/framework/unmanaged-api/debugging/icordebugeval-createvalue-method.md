---
title: ICorDebugEval::CreateValue – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugEval.CreateValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval::CreateValue
helpviewer_keywords:
- ICorDebugEval::CreateValue method [.NET Framework debugging]
- CreateValue method [.NET Framework debugging]
ms.assetid: 9a1c0b47-6f10-4fcb-844a-4ab2d7990140
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6d67784daee055106f104d74d098b9926c6de2ec
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugevalcreatevalue-method"></a>ICorDebugEval::CreateValue – metoda
Vytvoří hodnotu zadaného typu, s počáteční hodnotou nula nebo hodnotu null.  
  
 Tato metoda je zastaralé v rozhraní .NET Framework verze 2.0. Použití [icordebugeval2::createvaluefortype –](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-createvaluefortype-method.md) místo.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT CreateValue (  
    [in] CorElementType     elementType,  
    [in] ICorDebugClass     *pElementClass,  
    [out] ICorDebugValue    **ppValue  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `elementType`  
 [v] Hodnota [CorElementType](../../../../docs/framework/unmanaged-api/metadata/corelementtype-enumeration.md) výčet, který určuje typ hodnoty.  
  
 `pElementClass`  
 [v] Ukazatel na [ICorDebugClass](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-interface.md) objekt, který určuje třída hodnoty, pokud typ není primitivní typ.  
  
 `ppValue`  
 [out] Ukazatel na adresu "ICorDebugValue" objekt, který představuje hodnotu.  
  
## <a name="remarks"></a>Poznámky  
 `CreateValue` vytvoří `ICorDebugValue` objekt daného typu za účelem používání ve vyhodnocení funkce. Tento objekt hodnota slouží k předávání konstanty uživatele jako parametry.  
  
 Pokud je typ hodnoty primitivní typ, jeho počáteční hodnota je nulová nebo má hodnotu null. Použití [icordebuggenericvalue::SetValue –](../../../../docs/framework/unmanaged-api/debugging/icordebuggenericvalue-setvalue-method.md) nastavit hodnotu primitivního typu.  
  
 Pokud hodnota `elementType` je ELEMENT_TYPE_CLASS, získat "ICorDebugReferenceValue" (vrátí `ppValue`) představující odkaz na hodnotu null. Tento objekt můžete použít k vyhodnocení funkce, s parametry odkaz na objekt předat hodnotu null. Nelze nastavit `ICorDebugValue` k ničemu; vždy zůstává hodnotu null.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** 1.1, 1.0  
  
## <a name="see-also"></a>Viz také  
    
 [CreateValueForType – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-createvaluefortype-method.md)  
 ICorDebugValue
