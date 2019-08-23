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
ms.openlocfilehash: 1085bec812d797d3fbe4ea63ef447d4c466149f2
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965060"
---
# <a name="cor_gc_stats-structure"></a>COR_GC_STATS – struktura
Poskytuje statistiku o mechanizmu uvolňování paměti modulu CLR (Common Language Runtime).  
  
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
|`Flags`|Určuje, které hodnoty pole se mají vypočítat a vrátit.|  
|`ExplicitGCCount`|Označuje počet uvolňování paměti, které byly vynuceny externím požadavkem.|  
|`GenCollectionsTaken`|Označuje počet uvolňování paměti provedených pro každou generaci.|  
|`CommittedKBytes`|Celkový počet kilobajtů potvrzených ve všech haldách.|  
|`ReservedKBytes`|Celkový počet kilobajtů rezervovaných ve všech haldách.|  
|`Gen0HeapSizeKBytes`|Velikost haldy generace s hodnotou v kilobajtech.|  
|`Gen1HeapSizeKBytes`|Velikost haldy generace-jedna v kilobajtech.|  
|`Gen2HeapSizeKBytes`|Velikost haldy generace-dvě v kilobajtech.|  
|`LargeObjectHeapSizeKBytes`|Velikost haldy velkých objektů v kilobajtech.|  
|`KBytesPromotedFromGen0`|Velikost objektů pozměněných z generace na hodnotu v kilobajtech na jednu generaci.|  
|`KBytesPromotedFromGen1`|Velikost objektů povýšených od generace od generace do 2. generace v kilobajtech.|  
  
## <a name="remarks"></a>Poznámky  
 Metoda [ICLRGCManager::](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-getstats-method.md) GetStats vyžaduje, `Flags` aby pole `COR_GC_STATS` struktury bylo nastavené na jednu nebo více hodnot výčtu [COR_GC_STAT_TYPES](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md) , aby se určilo, která Statistika se má nastavit.  
  
 Následující tabulka mapuje statistiky poskytované touto strukturou na dvě hodnoty `COR_GC_COUNTS` výčtu COR_GC_STAT_TYPES a. [](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md) `COR_GC_MEMORYUSAGE`  
  
|Určeno COR_GC_COUNTS|Určeno COR_GC_MEMORYUSAGE|  
|----------------------------------|---------------------------------------|  
|`ExplicitGCCount`<br /><br /> `GenCollectionsTaken`|`CommittedKBytes`<br /><br /> `ReservedKBytes`<br /><br /> `Gen0HeapSizeKBytes`<br /><br /> `Gen1HeapSizeKBytes`<br /><br /> `Gen2HeapSizeKBytes`<br /><br /> `LargeObjectHeapSizeKBytes`<br /><br /> `KBytesPromotedFromGen0`<br /><br /> `KBytesPromotedFromGen1`|  
  
 Příklad použití je následující:  
  
```cpp  
COR_GC_STATS GCStats;  
GCStats.Flags = COR_GC_COUNTS | COR_GC_MEMORYUSAGE;  
pCLRGCManager->GetStats(&GCStats);  
```  
  
## <a name="requirements"></a>Požadavky  
 **Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlaviček** GCHost.idl  
  
 **Knihovna** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Struktury pro hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
- [Automatická správa paměti](../../../standard/automatic-memory-management.md)
- [Uvolňování paměti](../../../standard/garbage-collection/index.md)
