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
ms.openlocfilehash: 3a895f432ed640cc35a492df0c91cece34893062
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122369"
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
 `GetClass` lze volat pouze za určitých podmínek. Před voláním `GetClass`volejte [ICorDebugType:: GetType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-gettype-method.md) . Pokud `ICorDebugType::GetType` vrátí hodnotu CorElementType –, která je ELEMENT_TYPE_CLASS nebo ELEMENT_TYPE_VALUETYPE, `GetClass` lze volat pro získání neinstanceho typu pro obecný typ.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
