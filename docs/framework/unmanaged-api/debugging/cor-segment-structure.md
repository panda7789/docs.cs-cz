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
ms.openlocfilehash: 0370c74bde9ca5bdbd0fd03515f4b174ddd0a39a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132321"
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
|`gen`|Člen výčtu [CorDebugGenerationTypes –](cordebuggenerationtypes-enumeration.md) , který označuje generování oblasti paměti.|  
|`heap`|Číslo haldy, ve které se nachází oblast paměti. Další informace naleznete v části Poznámky.|  
  
## <a name="remarks"></a>Poznámky  
 Struktura `COR_SEGMENTS` představuje oblast paměti ve spravované haldě.  objekty `COR_SEGMENTS` jsou členy objektu kolekce [ICorDebugHeapRegionEnum](icordebugheapsegmentenum-interface.md) , který je vyplněn voláním metody [ICorDebugProcess5:: EnumerateHeapRegions –](icordebugprocess5-enumerateheapregions-method.md) .  
  
 Pole `heap` je číslo procesoru, které odpovídá vyhlášené haldě. Pro kolekce uvolnění paměti pracovní stanice je jeho hodnota vždycky nula, protože pracovní stanice mají jenom jednu haldu uvolňování paměti. Pro sběrače paměti serveru odpovídá jeho hodnota procesoru, ke kterému je halda připojena. Všimněte si, že může existovat více nebo méně hald uvolňování paměti, než kolik existuje skutečným procesorům z důvodu podrobností implementace uvolňování paměti.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Struktury pro ladění](debugging-structures.md)
- [Ladění](index.md)
