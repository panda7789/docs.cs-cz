---
title: ICorDebugType::GetClass – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugType.GetClass
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType::GetClass
helpviewer_keywords:
- ICorDebugType::GetClass method [.NET Framework debugging]
- GetClass method, ICorDebugType interface [.NET Framework debugging]
ms.assetid: 2644f48b-db3c-429f-ae62-76f1c98a1af5
topic_type:
- apiref
ms.openlocfilehash: d403a8bfba3599a60d8af72307590f5a569480dd
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791299"
---
# <a name="icordebugtypegetclass-method"></a>ICorDebugType::GetClass – metoda
Získá ukazatel rozhraní na ICorDebugClass, který představuje nevytvořený obecný typ.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetClass (  
    [out] ICorDebugClass   **ppClass  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `ppClass`  
 mimo Ukazatel na adresu `ICorDebugClass` rozhraní, které představuje neinstanciující obecný typ.  
  
## <a name="remarks"></a>Poznámky  
 `GetClass` lze volat pouze za určitých podmínek. Před voláním `GetClass`volejte [ICorDebugType:: GetType](icordebugtype-gettype-method.md) . Pokud `ICorDebugType::GetType` vrátí hodnotu CorElementType –, která je ELEMENT_TYPE_CLASS nebo ELEMENT_TYPE_VALUETYPE, `GetClass` může být voláno pro získání neinstanceho typu pro obecný typ.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
