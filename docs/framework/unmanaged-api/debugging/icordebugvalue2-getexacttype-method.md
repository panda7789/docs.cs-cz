---
title: ICorDebugValue2::GetExactType – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugValue2.GetExactType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValue2::GetExactType
helpviewer_keywords:
- ICorDebugValue2::GetExactType method [.NET Framework debugging]
- GetExactType method [.NET Framework debugging]
ms.assetid: 8e9aae1b-d1b7-4b6e-b577-6faf36dcec85
topic_type:
- apiref
ms.openlocfilehash: 6c5e5d1c9f734e097fc9e871d7a0cffdc9bb9138
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791127"
---
# <a name="icordebugvalue2getexacttype-method"></a>ICorDebugValue2::GetExactType – metoda
Získá ukazatel rozhraní na objekt "ICorDebugType", který představuje <xref:System.Type> této hodnoty.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetExactType (  
    [out] ICorDebugType   **ppType  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `ppType`  
 mimo Ukazatel na adresu `ICorDebugType`ho objektu, který představuje <xref:System.Type> hodnoty reprezentované tímto objektem "ICorDebugValue2".  
  
## <a name="remarks"></a>Poznámky  
 Metoda `GetExactType` s obecnými typy nahrazuje obě metody [ICorDebugObjectValue:: GetClass](icordebugobjectvalue-getclass-method.md) a [ICorDebugValue:: GetType](icordebugvalue-gettype-method.md) , z nichž každý vrací informace o typu hodnoty.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:
