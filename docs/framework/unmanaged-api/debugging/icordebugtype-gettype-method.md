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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d881a1fe3965b6e1d89e6172c887061434cd52ff
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugtypegettype-method"></a>ICorDebugType::GetType – metoda
Získá hodnotu CorElementType, která popisuje typ nativní common language runtime (CLR) <xref:System.Type> reprezentována tento ICorDebugType.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetType (  
    [out] CorElementType   *ty  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ty`  
 [out] Ukazatel na hodnotu `CorElementType` výčet, který označuje modulu CLR <xref:System.Type> které tento `ICorDebugType` představuje.  
  
## <a name="remarks"></a>Poznámky  
 Pokud hodnota `ty` ELEMENT_TYPE_CLASS nebo Typ ELEMENT_TYPE_VALUETYPE, který, [icordebugtype::getclass –](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getclass-method.md) metoda může být volána k získání bez instancí typu pro obecný typ; jinak, nevolejte `ICorDebugType::GetClass`.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
