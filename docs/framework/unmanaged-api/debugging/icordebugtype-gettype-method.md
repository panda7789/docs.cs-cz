---
title: ICorDebugType::GetType – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugType.GetType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType::GetType
helpviewer_keywords:
- ICorDebugType::GetType method [.NET Framework debugging]
- GetType method, ICorDebugType interface [.NET Framework debugging]
ms.assetid: d6e64534-4d47-4ad0-a340-7590e07e2b4a
topic_type:
- apiref
ms.openlocfilehash: 7f3010cccc584288608b3f6ba95efbeb95f271fb
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132058"
---
# <a name="icordebugtypegettype-method"></a>ICorDebugType::GetType – metoda
Získá hodnotu CorElementType –, která popisuje nativní typ modulu CLR (Common Language Runtime) <xref:System.Type> reprezentovaného tímto ICorDebugType.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetType (  
    [out] CorElementType   *ty  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `ty`  
 mimo Ukazatel na hodnotu výčtu `CorElementType`, která označuje CLR <xref:System.Type>, který tento `ICorDebugType` představuje.  
  
## <a name="remarks"></a>Poznámky  
 Pokud je hodnota `ty` buď ELEMENT_TYPE_CLASS nebo ELEMENT_TYPE_VALUETYPE, může být volána metoda [ICorDebugType:: GetClass](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getclass-method.md) pro získání typu bez instance pro obecný typ; v opačném případě Nevolejte `ICorDebugType::GetClass`.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
