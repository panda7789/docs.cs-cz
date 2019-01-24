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
ms.openlocfilehash: 0af820b590271e16cbfb443c193fd0afb4ed3358
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54604109"
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
 [in] Hodnota [corelementtype –](../../../../docs/framework/unmanaged-api/metadata/corelementtype-enumeration.md) výčet, který určuje typ hodnoty.  
  
 `pElementClass`  
 [in] Ukazatel [ICorDebugClass](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-interface.md) objekt, který určuje třída hodnotu, pokud typ není primitivním typem.  
  
 `ppValue`  
 [out] Ukazatel na adresu "ICorDebugValue" objekt, který představuje hodnotu.  
  
## <a name="remarks"></a>Poznámky  
 `CreateValue` vytvoří `ICorDebugValue` objekt daného typu pouze za účelem použití v vyhodnocení funkce. Tento objekt hodnotu lze předat jako parametry konstanty uživatele.  
  
 Pokud je typ hodnoty primitivní typ, jeho počáteční hodnota je nula nebo mít hodnotu null. Použití [icordebuggenericvalue::SetValue –](../../../../docs/framework/unmanaged-api/debugging/icordebuggenericvalue-setvalue-method.md) k nastavení hodnoty primitivního typu.  
  
 Pokud hodnota `elementType` je za řetězcem ELEMENT_TYPE_CLASS, získáte "ICorDebugReferenceValue" (vrácené v `ppValue`) představující odkaz na objekt s hodnotou null. Tento objekt slouží k vyhodnocení funkce, která má parametry objektů reference předat hodnotu null. Nelze nastavit `ICorDebugValue` k ničemu; vždy zůstane hodnotu null.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** 1.1, 1.0  
  
## <a name="see-also"></a>Viz také:

- [CreateValueForType Method](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-createvaluefortype-method.md) ICorDebugValue
