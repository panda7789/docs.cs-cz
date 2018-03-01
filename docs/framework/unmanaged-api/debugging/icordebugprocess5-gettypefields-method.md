---
title: "ICorDebugProcess5::GetTypeFields – metoda"
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
- ICorDebugProcess5.GetTypeFields
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::GetTypeFields
helpviewer_keywords:
- GetTypeFields method, ICorDebugProcess5 interface [.NET Framework debugging]
- ICorDebugProcess5::GetTypeFields method [.NET Framework debugging]
ms.assetid: 6a0ad3ee-dacb-47e9-abae-4536bcc4804b
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 1eb167517a33788a0d7e30663675b294d29ba3cc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugprocess5gettypefields-method"></a>ICorDebugProcess5::GetTypeFields – metoda
Poskytuje informace o pole, které patří do typu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetTypeFields(  
    [in] COR_TYPEID id,  
    [in] ULONG32 celt,  
    [out] COR_FIELD fields[],   
    [out] ULONG32 *pceltNeeded  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `id`  
 [v] Identifikátor typu je načíst informace o jejichž pole.  
  
 `celt`  
 [v] Počet [cor_field –](../../../../docs/framework/unmanaged-api/debugging/cor-field-structure.md) objekty, jejichž informace pole se mají být načteny.  
  
 `fields`  
 [out] Pole [cor_field –](../../../../docs/framework/unmanaged-api/debugging/cor-field-structure.md) objekty, které obsahují informace o pole, které patří k typu.  
  
 `pceltNeeded`  
 [out] Ukazatel na počet [cor_field –](../../../../docs/framework/unmanaged-api/debugging/cor-field-structure.md) objektů obsažených v `fields`.  
  
## <a name="remarks"></a>Poznámky  
 `celt` Parametr, který určuje počet polí, jejichž pole informace metoda používá k naplnění `fields`, by měla odpovídat hodnotě `COR_TYPE_LAYOUT::numFields` pole.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICorDebugProcess5 – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)  
 [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
