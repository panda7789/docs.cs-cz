---
title: ICorDebugType::GetFirstTypeParameter – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugType.GetFirstTypeParameter
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType::GetFirstTypeParameter
helpviewer_keywords:
- ICorDebugType::GetFirstTypeParameter method [.NET Framework debugging]
- GetFirstTypeParameter method [.NET Framework debugging]
ms.assetid: 35bb594f-af6a-4349-83fe-e98702674e03
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6d6754d7a8224249582df56ab674932f065f581d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
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
 `GetFirstTypeParameter` je možné volat v případech, kde Další informace o typu zahrnuje, maximálně jeden parametr typu. Konkrétně může sloužit Pokud je typ ELEMENT_TYPE_ARRAY, ELEMENT_TYPE_SZARRAY, typu ELEMENT_TYPE_BYREF nebo ELEMENT_TYPE_PTR, jak [icordebugtype::gettype –](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-gettype-method.md) metoda.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
