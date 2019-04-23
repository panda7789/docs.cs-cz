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
ms.openlocfilehash: faf1be65d308b223490f3ae67eed3d8a2b1688b9
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59223066"
---
# <a name="corsegment-structure"></a>COR_SEGMENT – struktura
Obsahuje informace o oblasti paměti spravované haldy.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
|`gen`|A [cordebuggenerationtypes –](../../../../docs/framework/unmanaged-api/debugging/cordebuggenerationtypes-enumeration.md) člen výčtu, která určuje generování oblasti paměti.|  
|`heap`|Číslo haldy, ve kterém se nachází oblasti paměti. Další informace naleznete v části Poznámky.|  
  
## <a name="remarks"></a>Poznámky  
 `COR_SEGMENTS` Struktura představuje oblast paměti ve spravované haldě.  `COR_SEGMENTS` objekty jsou členy [ICorDebugHeapRegionEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md) kolekci objektu, který je vyplněn volání [icordebugprocess5::enumerateheapregions –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheapregions-method.md) metody.  
  
 `heap` Pole je číslo procesoru, které odpovídá haldy hlásí. Pro kolekce uvolnění paměti pracovní stanice, jeho hodnota je vždy nula, protože mají pouze jednu haldě uvolňování paměti pracovní stanice. Pro kolekce uvolnění paměti serveru jeho hodnota odpovídá procesor, haldy je připojeno k. Všimněte si, že může existovat více nebo méně kolekce paměti haldy, než je skutečný procesory z důvodu podrobnosti implementace systému uvolňování paměti.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Struktury pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [Ladění](../../../../docs/framework/unmanaged-api/debugging/index.md)
