---
title: COR_SEGMENT – struktura
ms.date: 03/30/2017
api_name:
- COR_SEGMENT
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_SEGMENT
helpviewer_keywords:
- COR_SEGMENT structure [.NET Framework debugging]
ms.assetid: 93aeecb9-7fef-4545-8daf-f566dfc47084
topic_type:
- apiref
ms.openlocfilehash: a5c743064b8ca645cf45d02b8800c88187bf4c6c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179287"
---
# <a name="cor_segment-structure"></a>COR_SEGMENT – struktura
Obsahuje informace o oblasti paměti ve spravované haldě.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef struct _COR_SEGMENT {  
    CORDB_ADDRESS start;
    CORDB_ADDRESS end;
    CorDebugGenerationTypes gen;
    ULONG heap;
} COR_SEGMENT;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|`start`|Počáteční adresa oblasti paměti.|  
|`end`|Koncová adresa oblasti paměti.|  
|`gen`|[CorDebugGenerationTypes](cordebuggenerationtypes-enumeration.md) výčtu člena, který označuje generování oblasti paměti.|  
|`heap`|Číslo haldy, ve kterém je umístěna oblast paměti. Další informace naleznete v části Poznámky.|  
  
## <a name="remarks"></a>Poznámky  
 Struktura `COR_SEGMENTS` představuje oblast paměti ve spravované haldě.  `COR_SEGMENTS`objekty jsou členy objektu kolekce [ICorDebugHeapRegionEnum,](icordebugheapsegmentenum-interface.md) který je naplněn voláním metody [ICorDebugProcess5::EnumerateHeapRegions.](icordebugprocess5-enumerateheapregions-method.md)  
  
 Pole `heap` je číslo procesoru, které odpovídá nahlášené haldě. Pro uvolňování paměti pracovní stanice jeho hodnota je vždy nula, protože pracovní stanice mají pouze jednu haldu uvolňování paměti. Pro server uvolňování odpovídá jeho hodnota procesoru haldy je připojen. Všimněte si, že může být více nebo méně hromady uvolňování paměti, než jsou skutečné procesory z důvodu podrobnosti implementace uvolňování paměti.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [Systémové požadavky](../../get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Struktury pro ladění](debugging-structures.md)
- [ladění](index.md)
