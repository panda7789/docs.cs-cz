---
title: ICorDebugProcess5::GetTypeFields – metoda
ms.date: 03/30/2017
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
ms.openlocfilehash: 29006eba3d3a523fd24a461207ab12222a639782
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178594"
---
# <a name="icordebugprocess5gettypefields-method"></a>ICorDebugProcess5::GetTypeFields – metoda
Obsahuje informace o polích, která patří k typu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetTypeFields(  
    [in] COR_TYPEID id,  
    [in] ULONG32 celt,  
    [out] COR_FIELD fields[],
    [out] ULONG32 *pceltNeeded  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `id`  
 [v] Identifikátor typu, jehož informace o poli jsou načteny.  
  
 `celt`  
 [v] Počet [COR_FIELD](cor-field-structure.md) objektů, jejichž informace o poli má být načten.  
  
 `fields`  
 [out] Pole [COR_FIELD](cor-field-structure.md) objekty, které poskytují informace o polích, které patří k typu.  
  
 `pceltNeeded`  
 [out] Ukazatel na počet [COR_FIELD](cor-field-structure.md) objektů `fields`zahrnutých v .  
  
## <a name="remarks"></a>Poznámky  
 Parametr, `celt` který určuje počet polí, jejichž informace o `fields`polích, které metoda `COR_TYPE_LAYOUT::numFields` používá k naplnění , by měl odpovídat hodnotě pole.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [ICorDebugProcess5 – rozhraní](icordebugprocess5-interface.md)
- [Debugging – rozhraní](debugging-interfaces.md)
