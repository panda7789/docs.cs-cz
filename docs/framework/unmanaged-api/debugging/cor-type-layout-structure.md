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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6bd274b1eb14532629580e777288317186544912
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2019
ms.locfileid: "71274167"
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
|`parentID`|Identifikátor nadřazeného typu na tento typ. Toto bude identifikátor typu s hodnotou NULL (token1 = 0, token2 = 0), pokud ID typu odpovídá <xref:System.Object?displayProperty=nameWithType>.|  
|`objectSize`|Základní velikost objektu tohoto typu. Toto je celková velikost pro objekty, které nejsou proměnné velikosti.|  
|`numFields`|Počet polí, která jsou součástí objektů tohoto typu.|  
|`boxOffset`|Pokud je tento typ zabalený, počáteční posun pole objektu. Toto pole je platné pouze pro typy hodnot, jako jsou primitivní prvky a struktury.|  
|`type`|CorElementType –, ke kterému patří tento typ.|  
  
## <a name="remarks"></a>Poznámky  
 Pokud `numFields` je větší než nula, můžete zavolat metodu [ICorDebugProcess5:: GetTypeFields –](icordebugprocess5-gettypefields-method.md) a získat informace o polích v tomto typu. Pokud `type` je `ELEMENT_TYPE_STRING` ,`ELEMENT_TYPE_ARRAY` [](cor-typeid-structure.md) nebo ,`ELEMENT_TYPE_SZARRAY`velikost objektů tohoto typu je proměnná, a můžete předat strukturu COR_TYPEID do metody [ICorDebugProcess5:: GetArrayLayout –](icordebugprocess5-getarraylayout-method.md) .  
  
## <a name="requirements"></a>Požadavky  
 **Platformu** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlaviček** CorDebug. idl, CorDebug. h  
  
 **Knihovna** CorGuids.lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Struktury pro ladění](debugging-structures.md)
- [Ladění](index.md)
