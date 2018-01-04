---
title: "ICorDebugProcess5::GetTypeLayout – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugProcess5.GetTypeLayout
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcess5::GetTypeLayout
helpviewer_keywords:
- ICorDebugProcess5::GetTypeLayout method [.NET Framework debugging]
- GetTypeLayout method, ICorDebugProcess5 interface [.NET Framework debugging]
ms.assetid: bd62f5d1-e874-41f1-81e5-a29a7572c15d
topic_type: apiref
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4317fd374646dd5187a94f3e91cc88df939ed762
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugprocess5gettypelayout-method"></a>ICorDebugProcess5::GetTypeLayout – metoda
Získá informace o rozložení objektu v paměti podle jeho typ identifikátoru.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetTypeLayout(    [in] COR_TYPEID id,     [out] COR_TYPE_LAYOUT *pLayout);  
```  
  
#### <a name="parameters"></a>Parametry  
 `id`  
 [v] A [cor_typeid –](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) token, který určuje typ, jejichž uspořádání se požaduje.  
  
 `pLayout`  
 [out] Ukazatel [cor_type_layout –](../../../../docs/framework/unmanaged-api/debugging/cor-type-layout-structure.md) struktura, která obsahuje informace o rozložení objektu v paměti.  
  
## <a name="remarks"></a>Poznámky  
 `ICorDebugProcess5::GetTypeLayout` Metoda poskytuje informace o objekt na základě jeho [cor_typeid –](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md), která vrátí počet dalších [ICorDebugProcess5](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md) metody. Poskytuje informace [cor_type_layout –](../../../../docs/framework/unmanaged-api/debugging/cor-type-layout-structure.md) struktura, který je vyplněný metodou.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [COR_TYPE_LAYOUT – struktura](../../../../docs/framework/unmanaged-api/debugging/cor-type-layout-structure.md)  
 [ICorDebugProcess5 – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)  
 [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
