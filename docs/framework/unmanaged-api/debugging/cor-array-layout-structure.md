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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2cccb862a0dfd16eb0bbfe557e3c35373cd7e7b8
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67740818"
---
# <a name="corarraylayout-structure"></a>COR_ARRAY_LAYOUT – struktura
Poskytuje informace o rozložení objektu array v paměti.  
  
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
|`componentID`|Identifikátor typu objektů, které obsahuje pole.|  
|`componentType`|Corelementtype – hodnotu výčtu, která určuje, zda je součást odkaz kolekce uvolnění paměti, hodnotová třída nebo jednoduchého typu.|  
|`firstElementOffset`|Posun na první prvek v poli.|  
|`elementSize`|Velikost jednotlivých prvků.|  
|`countOffset`|Posun do počtu prvků v poli.|  
|`rankSize`|Velikost pořadí, v bajtech.|  
|`numRanks`|Číslo pořadí v poli.|  
|`rankOffset`|Posun, ve kterém je pořadí spuštění.|  
  
## <a name="remarks"></a>Poznámky  
 `rankSize` Pole určuje velikost pořadí v vícerozměrné pole. Je přesné pro také jednorozměrná pole.  
  
 Hodnota `numRanks` 1 pro jednorozměrné pole a `N` pro vícerozměrná pole `N` dimenze.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Struktury pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [Ladění](../../../../docs/framework/unmanaged-api/debugging/index.md)
