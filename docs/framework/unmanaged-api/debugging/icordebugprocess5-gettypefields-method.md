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
ms.openlocfilehash: 644b5ed751caaf1809250244b37badc8037b0f57
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792345"
---
# <a name="icordebugprocess5gettypefields-method"></a>ICorDebugProcess5::GetTypeFields – metoda
Poskytuje informace o polích, která patří do typu.  
  
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
 pro Identifikátor typu, jehož informace o poli jsou načteny.  
  
 `celt`  
 pro Počet objektů [COR_FIELD](cor-field-structure.md) , jejichž informace o poli mají být načteny.  
  
 `fields`  
 mimo Pole objektů [COR_FIELD](cor-field-structure.md) , které poskytují informace o polích, která patří do typu.  
  
 `pceltNeeded`  
 mimo Ukazatel na počet objektů [COR_FIELD](cor-field-structure.md) obsažených v `fields`.  
  
## <a name="remarks"></a>Poznámky  
 Parametr `celt`, který určuje počet polí, jejichž informace o poli, kterou metoda používá k naplnění `fields`, by měla odpovídat hodnotě pole `COR_TYPE_LAYOUT::numFields`.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorDebugProcess5 – rozhraní](icordebugprocess5-interface.md)
- [Rozhraní pro ladění](debugging-interfaces.md)
