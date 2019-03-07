---
title: ICorDebugProcess5::GetTypeLayout – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.GetTypeLayout
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::GetTypeLayout
helpviewer_keywords:
- ICorDebugProcess5::GetTypeLayout method [.NET Framework debugging]
- GetTypeLayout method, ICorDebugProcess5 interface [.NET Framework debugging]
ms.assetid: bd62f5d1-e874-41f1-81e5-a29a7572c15d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ffef0b7296e2742d6e6207f66f91273f41652469
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57483755"
---
# <a name="icordebugprocess5gettypelayout-method"></a>ICorDebugProcess5::GetTypeLayout – metoda
Získá informace o rozložení objektu v paměti podle jeho identifikátor typu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT GetTypeLayout(    [in] COR_TYPEID id,     [out] COR_TYPE_LAYOUT *pLayout);  
```  
  
## <a name="parameters"></a>Parametry  
 `id`  
 [in] A [cor_typeid –](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) token, který určuje typ, jehož rozložení je žádoucí.  
  
 `pLayout`  
 [out] Ukazatel [cor_type_layout –](../../../../docs/framework/unmanaged-api/debugging/cor-type-layout-structure.md) strukturu, která obsahuje informace o rozložení objektu v paměti.  
  
## <a name="remarks"></a>Poznámky  
 `ICorDebugProcess5::GetTypeLayout` Metoda poskytuje informace o objektu na základě jeho [cor_typeid –](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md), která je vrácena řadou dalších [icordebugprocess5 –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md) metody. Poskytuje informace [cor_type_layout –](../../../../docs/framework/unmanaged-api/debugging/cor-type-layout-structure.md) struktura, která je vyplněn metodu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také:
- [COR_TYPE_LAYOUT – struktura](../../../../docs/framework/unmanaged-api/debugging/cor-type-layout-structure.md)
- [ICorDebugProcess5 – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)
- [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
