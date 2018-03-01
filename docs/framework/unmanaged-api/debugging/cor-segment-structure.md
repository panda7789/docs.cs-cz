---
title: "COR_SEGMENT – struktura"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 9414aa1c36ba059d9ee1101f6183dc8a669f9e6f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="corsegment-structure"></a>COR_SEGMENT – struktura
Obsahuje informace o oblasti spravovaná halda paměti.  
  
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
|`gen`|A [CorDebugGenerationTypes](../../../../docs/framework/unmanaged-api/debugging/cordebuggenerationtypes-enumeration.md) – člen výčtu určující generování oblasti paměti.|  
|`heap`|Číslo haldy, ve kterém se nachází oblasti paměti. Další informace naleznete v části Poznámky.|  
  
## <a name="remarks"></a>Poznámky  
 `COR_SEGMENTS` Struktura představuje oblast spravovaná halda paměti.  `COR_SEGMENTS`objekty jsou členy [ICorDebugHeapRegionEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md) kolekce objektu, který je naplněn volání[icordebugprocess5::enumerateheapregions –](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheapregions-method.md) metoda.  
  
 `heap` Pole je číslo procesoru, který odpovídá haldě nehlásí. Kolektory uvolňování paměti pracovních stanic jeho hodnota je vždy nula, protože pracovní stanice mají jenom jeden kolekce halda paměti. Pro Kolektory paměti serveru jeho hodnota odpovídá procesoru, který halda je připojen k. Všimněte si, že může existovat více nebo méně uvolňování haldách, než je skutečný procesory z důvodu podrobnosti implementace systému uvolňování paměti.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Struktury pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [Ladění](../../../../docs/framework/unmanaged-api/debugging/index.md)
