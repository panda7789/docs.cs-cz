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
ms.openlocfilehash: 7a6553de31d4f9627809af7691218c39dc734c6f
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501661"
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
  
|Člen|Description|  
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
 Metoda [ICLRGCManager:: GetStats](iclrgcmanager-getstats-method.md) vyžaduje, aby se `Flags` pole `COR_GC_STATS` struktury nastavilo na jednu nebo více hodnot výčtu [COR_GC_STAT_TYPES](cor-gc-stat-types-enumeration.md) , aby se určilo, která Statistika se má nastavit.  
  
 Následující tabulka mapuje statistiky poskytované touto strukturou na dvě [COR_GC_STAT_TYPES](cor-gc-stat-types-enumeration.md) výčtové hodnoty `COR_GC_COUNTS` a `COR_GC_MEMORYUSAGE` .  
  
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
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** GCHost. idl  
  
 **Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Struktury pro hostování](hosting-structures.md)
- [Automatická správa paměti](../../../standard/automatic-memory-management.md)
- [Uvolňování paměti](../../../standard/garbage-collection/index.md)
