---
title: ICorDebugEval2::CreateValueForType – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugEval2.CreateValueForType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval2::CreateValueForType
helpviewer_keywords:
- CreateValueForType method [.NET Framework debugging]
- ICorDebugEval2::CreateValueForType method [.NET Framework debugging]
ms.assetid: ea38ae20-7e0a-427a-be77-d78fae719d82
topic_type:
- apiref
ms.openlocfilehash: fd7acaa8bcb4d53893855bcd25ff68cf26e30354
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976158"
---
# <a name="icordebugeval2createvaluefortype-method"></a>ICorDebugEval2::CreateValueForType – metoda
Získá ukazatel na nový ICorDebugValue zadaného typu s počáteční hodnotou 0 nebo null.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT CreateValueForType (  
    [in] ICorDebugType         *pType,  
    [out] ICorDebugValue       **ppValue  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pType`  
 pro Ukazatel na objekt ICorDebugType, který představuje typ.  
  
 `ppValue`  
 mimo Ukazatel na adresu `ICorDebugValue` objektu, který představuje hodnotu.  
  
## <a name="remarks"></a>Poznámky  
 `CreateValueForType`generalizes [ICorDebugEval:: CreateValue –](icordebugeval-createvalue-method.md) vám umožní určit libovolný typ objektu, včetně konstruovaných typů, jako je `List<int>`. Jediným účelem této metody je generovat hodnotu, která může být předána vyhodnocení funkce.  
  
 Typ musí být typ třída nebo hodnota. Tuto metodu nelze použít k vytvoření hodnot pole nebo hodnot řetězců.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
