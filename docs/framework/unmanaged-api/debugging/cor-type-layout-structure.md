---
title: COR_TYPE_LAYOUT – struktura
ms.date: 03/30/2017
api_name:
- COR_TYPE_LAYOUT
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_TYPE_LAYOUT
helpviewer_keywords:
- COR_TYPE_LAYOUT structure [.NET Framework debugging]
ms.assetid: 43a7addd-f25a-4049-9907-abec3eb17af2
topic_type:
- apiref
ms.openlocfilehash: 12c594f157c803d5fc179e09a8ca6c0ef40f3f44
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73099028"
---
# <a name="cor_type_layout-structure"></a>COR_TYPE_LAYOUT – struktura
Poskytuje informace o rozložení objektu v paměti.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef struct COR_TYPE_LAYOUT {  
    COR_TYPEID parentID;  
    ULONG32 objectSize;  
    ULONG32 numFields;  
    ULONG32 boxOffset;  
    CorElementType type;  
} COR_TYPE_LAYOUT;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|`parentID`|Identifikátor nadřazeného typu na tento typ. Toto bude identifikátor typu NULL (token1 = 0, token2 = 0), pokud ID typu odpovídá <xref:System.Object?displayProperty=nameWithType>.|  
|`objectSize`|Základní velikost objektu tohoto typu. Toto je celková velikost pro objekty, které nejsou proměnné velikosti.|  
|`numFields`|Počet polí, která jsou součástí objektů tohoto typu.|  
|`boxOffset`|Pokud je tento typ zabalený, počáteční posun pole objektu. Toto pole je platné pouze pro typy hodnot, jako jsou primitivní prvky a struktury.|  
|`type`|CorElementType –, ke kterému patří tento typ.|  
  
## <a name="remarks"></a>Poznámky  
 Pokud je `numFields` větší než nula, můžete zavolat metodu [ICorDebugProcess5:: GetTypeFields –](icordebugprocess5-gettypefields-method.md) a získat informace o polích v tomto typu. Pokud je `type` `ELEMENT_TYPE_STRING`, `ELEMENT_TYPE_ARRAY`nebo `ELEMENT_TYPE_SZARRAY`, velikost objektů tohoto typu je proměnná a můžete předat strukturu [COR_TYPEID](cor-typeid-structure.md) do metody [ICorDebugProcess5:: GetArrayLayout –](icordebugprocess5-getarraylayout-method.md) .  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Struktury pro ladění](debugging-structures.md)
- [Ladění](index.md)
