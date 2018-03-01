---
title: "ICorDebugType::GetType – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: c07f9974d0178a1a7502a97d54d7103ee795425f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
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
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
