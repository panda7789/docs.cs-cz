---
title: "ICorDebugType::GetFirstTypeParameter – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugType.GetFirstTypeParameter
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugType::GetFirstTypeParameter
helpviewer_keywords:
- ICorDebugType::GetFirstTypeParameter method [.NET Framework debugging]
- GetFirstTypeParameter method [.NET Framework debugging]
ms.assetid: 35bb594f-af6a-4349-83fe-e98702674e03
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e963553bfeac2d659de8fc460a938d2d523b53e0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugtypegetfirsttypeparameter-method"></a>ICorDebugType::GetFirstTypeParameter – metoda
Získá ukazatele rozhraní k ICorDebugType, který představuje první <xref:System.Type> parametr typu představovaný typem to `ICorDebugType`.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetFirstTypeParameter (  
    [out] ICorDebugType   **value  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `value`  
 [out] Ukazatel na adresu `ICorDebugType` objekt, který představuje první parametr.  
  
## <a name="remarks"></a>Poznámky  
 `GetFirstTypeParameter`je možné volat v případech, kde Další informace o typu zahrnuje, maximálně jeden parametr typu. Konkrétně může sloužit Pokud je typ ELEMENT_TYPE_ARRAY, ELEMENT_TYPE_SZARRAY, typu ELEMENT_TYPE_BYREF nebo ELEMENT_TYPE_PTR, jak [icordebugtype::gettype –](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-gettype-method.md) metoda.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
