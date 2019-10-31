---
title: COR_GC_STAT_TYPES – výčet
ms.date: 03/30/2017
api_name:
- COR_GC_STAT_TYPES
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- COR_GC_STAT_TYPES
helpviewer_keywords:
- COR_GC_STAT_TYPES enumeration [.NET Framework hosting]
ms.assetid: fc51d6db-f7f8-408b-b93d-c166fc712c99
topic_type:
- apiref
ms.openlocfilehash: b0fbc462283ef1577de8100e60fd09caa53db539
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131918"
---
# <a name="cor_gc_stat_types-enumeration"></a>COR_GC_STAT_TYPES – výčet
Určuje statistiku, která má být zaznamenána pro uvolňování paměti.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum {  
    COR_GC_COUNTS                 = 0x00000001  
    COR_GC_MEMORYUSAGE            = 0x00000002  
} COR_GC_STAT_TYPES;  
```  
  
## <a name="remarks"></a>Poznámky  
 Tento výčet Určuje, které statistiky ve struktuře [COR_GC_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md) mají být nastaveny metodou [ICLRGCManager:: getstatistics](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-getstats-method.md) .  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|`COR_GC_COUNTS`|Zaznamenává počet uvolňování paměti provedených pro každou generaci.|  
|`COR_GC_MEMORYUSAGE`|Zaznamenává využití paměti a statistiky velikosti uvolňování paměti.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** GCHost. idl, GCHost. h  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [COR_GC_STATS – struktura](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md)
- [Výčty pro hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
