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
ms.openlocfilehash: a2c7f7b722abac6acf71d3b64276862441695a5f
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212786"
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
 mimo Ukazatel na počet objektů [COR_FIELD](cor-field-structure.md) obsažených v `fields` .  
  
## <a name="remarks"></a>Poznámky  
 `celt`Parametr, který určuje počet polí, jejichž informace o poli, kterou metoda používá k naplnění `fields` , by měla odpovídat hodnotě `COR_TYPE_LAYOUT::numFields` pole.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [ICorDebugProcess5 – rozhraní](icordebugprocess5-interface.md)
- [Debugging – rozhraní](debugging-interfaces.md)
