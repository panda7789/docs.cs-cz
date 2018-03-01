---
title: "ICorDebugType::GetStaticFieldValue – metoda"
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
- ICorDebugType.GetStaticFieldValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType::GetStaticFieldValue
helpviewer_keywords:
- GetStaticFieldValue method, ICorDebugType interface [.NET Framework debugging]
- ICorDebugType::GetStaticFieldValue method [.NET Framework debugging]
ms.assetid: 62eb5d55-53ee-4fb3-8d47-7b6c96808f9e
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 2a6a7305017c83b539a3d5ec11fa61ccd2af90a8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugtypegetstaticfieldvalue-method"></a>ICorDebugType::GetStaticFieldValue – metoda
Získá ukazatele rozhraní ICorDebugValue objektu, která obsahuje hodnotu statické pole odkazovaná v zadaném poli token v rámci zadaného zásobníku.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetStaticFieldValue (  
    [in]  mdFieldDef        fieldDef,  
    [in]  ICorDebugFrame    *pFrame,  
    [out] ICorDebugValue    **ppValue  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `fieldDef`  
 [v] `mdFieldDef` Token, který určuje statické pole.  
  
 `pFrame`  
 [v] Ukazatel ICorDebugFrame, který představuje rámce zásobníku.  
  
 `ppValue`  
 [out] Ukazatel na adresu `ICorDebugValue` obsahující hodnotu statické pole.  
  
## <a name="remarks"></a>Poznámky  
 `GetStaticFieldValue` Metoda může používat pouze v případě typ je ELEMENT_TYPE_CLASS nebo Typ ELEMENT_TYPE_VALUETYPE, který, jak [icordebugtype::gettype –](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-gettype-method.md) metoda.  
  
 Pro typy neobecnou provádí operaci `GetStaticFieldValue` je stejný jako při volání [icordebugclass::getstaticfieldvalue –](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-getstaticfieldvalue-method.md) ICorDebugClass objektu, který je vrácen [icordebugtype::getclass –](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getclass-method.md).  
  
 Pro obecné typy hodnotu statické pole bude relativně ke konkrétní vytváření instancí. Navíc pokud statické pole může být může být relativní vzhledem k vlákno, kontextu nebo doménu aplikace, pak rámce zásobníku pomůže ladicího programu určit správnou hodnotu.  
  
## <a name="remarks"></a>Poznámky  
 `GetStaticFieldValue`lze použít pouze při volání `ICorDebugType::GetType` vrací hodnotu ELEMENT_TYPE_CLASS nebo Typ ELEMENT_TYPE_VALUETYPE, který.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
