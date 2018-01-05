---
title: "COR_GC_STAT_TYPES – výčet"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COR_GC_STAT_TYPES
api_location: mscoree.dll
api_type: COM
f1_keywords: COR_GC_STAT_TYPES
helpviewer_keywords: COR_GC_STAT_TYPES enumeration [.NET Framework hosting]
ms.assetid: fc51d6db-f7f8-408b-b93d-c166fc712c99
topic_type: apiref
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 86d0ce931518fa50dbd3b0d6d7f2755d19042eca
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="corgcstattypes-enumeration"></a>COR_GC_STAT_TYPES – výčet
Určuje statistiky, které mají být zaznamenány pro uvolnění paměti.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef enum {  
    COR_GC_COUNTS                 = 0x00000001  
    COR_GC_MEMORYUSAGE            = 0x00000002  
} COR_GC_STAT_TYPES;  
```  
  
## <a name="remarks"></a>Poznámky  
 Tento výčet Určuje, jaké statistické údaje ve [cor_gc_stats –](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md) struktura jsou nastavení [iclrgcmanager::getstats –](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-getstats-method.md) metoda.  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|`COR_GC_COUNTS`|Zaznamenává počet kolekce provést pro každou generaci.|  
|`COR_GC_MEMORYUSAGE`|Zaznamenává paměť a využití paměti kolekce velikost statistiky.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** GCHost.idl, GCHost.h  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [COR_GC_STATS – struktura](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md)  
 [Výčty pro hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
