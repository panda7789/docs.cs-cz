---
title: COR_GC_STATS – struktura
ms.date: 03/30/2017
api_name:
- COR_GC_STATS
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- COR_GC_STATS
helpviewer_keywords:
- COR_GC_STATS structure [.NET Framework hosting]
ms.assetid: 8d4ff73e-739b-40f6-9349-359fbc99c2f9
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 630c365c8710388ae3e913bedece0fb710da7cd9
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67768133"
---
# <a name="corgcstats-structure"></a>COR_GC_STATS – struktura
Poskytuje statistické údaje o mechanismu uvolnění paměti kolekce modulu common language runtime (CLR).  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef struct _COR_GC_STATS {  
    ULONG   Flags;   
    SIZE_T  ExplicitGCCount;  
    SIZE_T  GenCollectionsTaken[3];  
    SIZE_T  CommittedKBytes;   
    SIZE_T  ReservedKBytes;  
    SIZE_T  Gen0HeapSizeKBytes;  
    SIZE_T  Gen1HeapSizeKBytes;  
    SIZE_T  Gen2HeapSizeKBytes;  
    SIZE_T  LargeObjectHeapSizeKBytes;  
    SIZE_T  KBytesPromotedFromGen0;  
    SIZE_T  KBytesPromotedFromGen1;  
} COR_GC_STATS;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|`Flags`|Určuje pole hodnot, které by měl vypočítá a vrátí.|  
|`ExplicitGCCount`|Označuje počet uvolnění paměti, které byly vynutit externí požadavek.|  
|`GenCollectionsTaken`|Označuje číslo, které provádí pro každé generaci uvolňování pamětí.|  
|`CommittedKBytes`|Celkový počet kilobajtů potvrzeny ve všech haldách.|  
|`ReservedKBytes`|Celkový počet kilobajtů vyhrazené ve všech haldách.|  
|`Gen0HeapSizeKBytes`|Velikost v kilobajtech, generování nuly haldy.|  
|`Gen1HeapSizeKBytes`|Velikost v kilobajtech haldy generování: 1.|  
|`Gen2HeapSizeKBytes`|Velikost v kilobajtech haldy 2. generace.|  
|`LargeObjectHeapSizeKBytes`|Velikost v kilobajtech velkých objektových haldách.|  
|`KBytesPromotedFromGen0`|Velikost v kilobajtech objektů, které jsou přesunuty z generace nula do generování jednoho.|  
|`KBytesPromotedFromGen1`|Velikost v kilobajtech objektů, které jsou přesunuty z jednoho. generace do 2. generace.|  
  
## <a name="remarks"></a>Poznámky  
 [Iclrgcmanager::getstats –](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-getstats-method.md) metoda vyžaduje `Flags` pole `COR_GC_STATS` struktura nastavili na jeden nebo více hodnot [cor_gc_stat_types –](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md) výčet k určení statistiky jsou nastavení.  
  
 Následující tabulka mapuje statistiky poskytuje tuto strukturu pro dvě [cor_gc_stat_types –](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md) hodnot výčtu, `COR_GC_COUNTS` a `COR_GC_MEMORYUSAGE`.  
  
|Určená COR_GC_COUNTS|Určená COR_GC_MEMORYUSAGE|  
|----------------------------------|---------------------------------------|  
|`ExplicitGCCount`<br /><br /> `GenCollectionsTaken`|`CommittedKBytes`<br /><br /> `ReservedKBytes`<br /><br /> `Gen0HeapSizeKBytes`<br /><br /> `Gen1HeapSizeKBytes`<br /><br /> `Gen2HeapSizeKBytes`<br /><br /> `LargeObjectHeapSizeKBytes`<br /><br /> `KBytesPromotedFromGen0`<br /><br /> `KBytesPromotedFromGen1`|  
  
 Příklad použití je následujícím způsobem:  
  
```cpp  
COR_GC_STATS GCStats;  
GCStats.Flags = COR_GC_COUNTS | COR_GC_MEMORYUSAGE;  
pCLRGCManager->GetStats(&GCStats);  
```  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** GCHost.idl  
  
 **Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Struktury pro hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
- [Automatická správa paměti](../../../../docs/standard/automatic-memory-management.md)
- [Uvolňování paměti](../../../../docs/standard/garbage-collection/index.md)
