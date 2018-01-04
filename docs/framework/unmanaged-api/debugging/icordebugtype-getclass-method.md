---
title: "ICorDebugType::GetClass – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugType.GetClass
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugType::GetClass
helpviewer_keywords:
- ICorDebugType::GetClass method [.NET Framework debugging]
- GetClass method, ICorDebugType interface [.NET Framework debugging]
ms.assetid: 2644f48b-db3c-429f-ae62-76f1c98a1af5
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 32462159bc00ea766af3e3bc0f9d3d7a35eb2e38
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugtypegetclass-method"></a>ICorDebugType::GetClass – metoda
Získá ukazatele rozhraní umožňuje ICorDebugClass, který představuje bez instancí obecného typu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetClass (  
    [out] ICorDebugClass   **ppClass  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `ppClass`  
 [out] Ukazatel na adresu `ICorDebugClass` rozhraní, které představuje bez instancí obecného typu.  
  
## <a name="remarks"></a>Poznámky  
 `GetClass`je možné volat jenom za určitých podmínek. Volání [icordebugtype::gettype –](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-gettype-method.md) před voláním `GetClass`. Pokud `ICorDebugType::GetType` vrátí CorElementType hodnotu, která je ELEMENT_TYPE_CLASS nebo Typ ELEMENT_TYPE_VALUETYPE, který, `GetClass` lze volat pro získání bez instancí typu pro obecného typu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
