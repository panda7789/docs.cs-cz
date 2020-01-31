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
ms.openlocfilehash: 8632799b68ae8f92835d1774472bc1432d886f3b
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793475"
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
 `CreateValueForType` generalizace [ICorDebugEval:: CreateValue –](icordebugeval-createvalue-method.md) umožňuje určit libovolný typ objektu, včetně konstruovaných typů, jako je například `List<int>`. Jediným účelem této metody je generovat hodnotu, která může být předána vyhodnocení funkce.  
  
 Typ musí být typ třída nebo hodnota. Tuto metodu nelze použít k vytvoření hodnot pole nebo hodnot řetězců.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
