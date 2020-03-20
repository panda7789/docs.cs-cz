---
title: COR_ARRAY_LAYOUT – struktura
ms.date: 03/30/2017
api_name:
- COR_ARRAY_LAYOUT
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_ARRAY_LAYOUT
helpviewer_keywords:
- COR_DEBUG_IL_TO_NATIVE_MAP structure [.NET Framework debugging]
ms.assetid: aa20ac3d-6f60-4aa2-91c5-f3a86f82eba8
topic_type:
- apiref
ms.openlocfilehash: ca2d00611a7530dfb0d1c2a27123947bdf69820d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179343"
---
# <a name="cor_array_layout-structure"></a>COR_ARRAY_LAYOUT – struktura
Obsahuje informace o rozložení objektu pole v paměti.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef struct COR_ARRAY_LAYOUT {  
    COR_TYPEID componentID;  
    CorElementType componentType;  
    ULONG32 firstElementOffset;  
    ULONG32 elementSize;  
    ULONG32 countOffset;
    ULONG32 rankSize;
    ULONG32 numRanks;
    ULONG32 rankOffset;
} COR_ARRAY_LAYOUT;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|`componentID`|Identifikátor typu objektů, které pole obsahuje.|  
|`componentType`|Hodnota výčtu CorElementType, která označuje, zda je komponenta odkaz emitovaného, třída hodnoty nebo primitivní.|  
|`firstElementOffset`|Posun na první prvek v poli.|  
|`elementSize`|Velikost každého prvku.|  
|`countOffset`|Posun k počtu prvků v poli.|  
|`rankSize`|Velikost pořadí v bajtů.|  
|`numRanks`|Počet řad v poli.|  
|`rankOffset`|Posun, při kterém začínají hodnosti.|  
  
## <a name="remarks"></a>Poznámky  
 Toto `rankSize` pole určuje velikost pořadí ve vícerozměrném poli. Je také přesná i pro jednorozměrná pole.  
  
 Hodnota `numRanks` je 1 pro jednorozměrné `N` pole a pro vícerozměrné pole dimenzí. `N`  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [Systémové požadavky](../../get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Struktury pro ladění](debugging-structures.md)
- [ladění](index.md)
