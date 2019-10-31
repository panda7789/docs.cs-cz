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
ms.openlocfilehash: 20315dfc426b63f2d526f3481756e165b388b41e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137601"
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
 mimo Ukazatel na adresu `ICorDebugValue`ho objektu, který představuje hodnotu.  
  
## <a name="remarks"></a>Poznámky  
 `CreateValueForType` generalizace [ICorDebugEval:: CreateValue –](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-createvalue-method.md) umožňuje určit libovolný typ objektu, včetně konstruovaných typů, jako je například `List<int>`. Jediným účelem této metody je generovat hodnotu, která může být předána vyhodnocení funkce.  
  
 Typ musí být typ třída nebo hodnota. Tuto metodu nelze použít k vytvoření hodnot pole nebo hodnot řetězců.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
