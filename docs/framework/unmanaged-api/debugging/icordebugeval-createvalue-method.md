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
ms.openlocfilehash: 4bb04ba090be9cab551bc39d8d9f1be974c747d3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73085139"
---
# <a name="icordebugevalcreatevalue-method"></a>ICorDebugEval::CreateValue – metoda
Vytvoří hodnotu zadaného typu s počáteční hodnotou 0 nebo null.  
  
 Tato metoda je zastaralá ve verzi .NET Framework 2,0. Místo toho použijte [ICorDebugEval2:: createvaluefortype –](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-createvaluefortype-method.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT CreateValue (  
    [in] CorElementType     elementType,  
    [in] ICorDebugClass     *pElementClass,  
    [out] ICorDebugValue    **ppValue  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `elementType`  
 pro Hodnota výčtu [CorElementType –](../../../../docs/framework/unmanaged-api/metadata/corelementtype-enumeration.md) , která určuje typ hodnoty.  
  
 `pElementClass`  
 pro Ukazatel na objekt [ICorDebugClass](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-interface.md) , který určuje třídu hodnoty, pokud typ není primitivní typ.  
  
 `ppValue`  
 mimo Ukazatel na adresu objektu "ICorDebugValue", který představuje hodnotu.  
  
## <a name="remarks"></a>Poznámky  
 `CreateValue` vytvoří objekt `ICorDebugValue` daného typu pro výhradní účely jeho použití ve vyhodnocení funkce. Tento objekt hodnoty lze použít k předání konstant uživatele jako parametrů.  
  
 Pokud je typ hodnoty primitivní typ, jeho počáteční hodnota je nula nebo null. Pomocí [ICorDebugGenericValue:: SetValue](../../../../docs/framework/unmanaged-api/debugging/icordebuggenericvalue-setvalue-method.md) nastavte hodnotu primitivního typu.  
  
 Pokud je hodnota `elementType` ELEMENT_TYPE_CLASS, získáte "ICorDebugReferenceValue" (vrácený v `ppValue`) představující odkaz na objekt null. Tento objekt lze použít k předání hodnoty null do vyhodnocení funkce, které má parametry objektu reference. Nemůžete nastavit `ICorDebugValue` na cokoli. vždycky zůstane null.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** 1,1, 1,0  
  
## <a name="see-also"></a>Viz také:

- [CreateValueForType – metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-createvaluefortype-method.md)
- [Rozhraní ICorDebugEval](icordebugeval-interface.md)
