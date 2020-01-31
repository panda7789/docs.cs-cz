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
ms.openlocfilehash: 25ffbf73fbefbb3c584450283c3080dfc11ee598
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791242"
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
 Pokud je hodnota `ty` buď ELEMENT_TYPE_CLASS nebo ELEMENT_TYPE_VALUETYPE, může být volána metoda [ICorDebugType:: GetClass](icordebugtype-getclass-method.md) pro získání typu bez instance pro obecný typ; v opačném případě Nevolejte `ICorDebugType::GetClass`.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
