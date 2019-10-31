---
title: ICorDebugArrayValue::GetElementAtPosition – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugArrayValue.GetElementAtPosition
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugArrayValue::GetElementAtPosition
helpviewer_keywords:
- GetElementAtPosition method [.NET Framework debugging]
- ICorDebugArrayValue::GetElementAtPosition method [.NET Framework debugging]
ms.assetid: 6fd5eaa4-1997-4910-82f5-3887480db764
topic_type:
- apiref
ms.openlocfilehash: 10584442d7e0bd61e6decaf2b494dfe39f339d6d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73088419"
---
# <a name="icordebugarrayvaluegetelementatposition-method"></a>ICorDebugArrayValue::GetElementAtPosition – metoda
Získá prvek na dané pozici, což zpracuje pole jako jednorozměrné jednorozměrné pole s nulovým základem.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetElementAtPosition (  
    [in]  ULONG32          nPosition,  
    [out] ICorDebugValue   **ppValue  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `nPosition`  
 pro Pozice prvku, který má být načten.  
  
 `ppValue`  
 mimo Ukazatel na adresu objektu ICorDebugValue, který představuje hodnotu prvku.  
  
## <a name="remarks"></a>Poznámky  
 Rozložení pole s více dimenzemi se řídí C++ stylem rozložení pole.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
