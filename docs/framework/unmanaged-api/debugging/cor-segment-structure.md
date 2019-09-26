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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: aabf3ac4e51280bd847d145e15ad804d514ede2c
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2019
ms.locfileid: "71274007"
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
 `COR_SEGMENTS` Struktura představuje oblast paměti ve spravované haldě.  `COR_SEGMENTS`objekty jsou členy objektu kolekce [ICorDebugHeapRegionEnum](icordebugheapsegmentenum-interface.md) , který je vyplněn voláním metody [ICorDebugProcess5:: EnumerateHeapRegions –](icordebugprocess5-enumerateheapregions-method.md) .  
  
 `heap` Pole je číslo procesoru, které odpovídá vyhlášené haldě. Pro kolekce uvolnění paměti pracovní stanice je jeho hodnota vždycky nula, protože pracovní stanice mají jenom jednu haldu uvolňování paměti. Pro sběrače paměti serveru odpovídá jeho hodnota procesoru, ke kterému je halda připojena. Všimněte si, že může existovat více nebo méně hald uvolňování paměti, než kolik existuje skutečným procesorům z důvodu podrobností implementace uvolňování paměti.  
  
## <a name="requirements"></a>Požadavky  
 **Platformu** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlaviček** CorDebug. idl, CorDebug. h  
  
 **Knihovna** CorGuids.lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Struktury pro ladění](debugging-structures.md)
- [Ladění](index.md)
