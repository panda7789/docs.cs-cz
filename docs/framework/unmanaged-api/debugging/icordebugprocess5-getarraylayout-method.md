---
title: "ICorDebugProcess5::GetArrayLayout – metoda"
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
- ICorDebugProcess5.GetArrayLayout
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::GetArrayLayout
helpviewer_keywords:
- ICorDebugProcess5::GetArrayLayout method [.NET Framework debugging]
- GetArrayLayout method, ICorDebugProcess5 interface [.NET Framework debugging]
ms.assetid: 9a7393b9-9735-43c6-8616-afb103c432fd
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 608cf003d71599a141b1009ef16c7b7bf89161aa
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugprocess5getarraylayout-method"></a>ICorDebugProcess5::GetArrayLayout – metoda
Poskytuje informace o rozložení typy polí.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetArrayLayout(    [in] COR_TYPEID id,     [out] COR_ARRAY_LAYOUT *pLayout);  
```  
  
#### <a name="parameters"></a>Parametry  
 `id`  
 [v] A [cor_typeid –](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) token, který určuje pole, jejichž uspořádání se požaduje.  
  
 `pLayout`  
 [out] Ukazatel [cor_array_layout –](../../../../docs/framework/unmanaged-api/debugging/cor-array-layout-structure.md) struktura, která obsahuje informace o rozložení pole v paměti.  
  
## <a name="remarks"></a>Poznámky  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICorDebugProcess5 – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)  
 [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
