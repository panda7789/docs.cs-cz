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
ms.openlocfilehash: 2ab0c38645a8e5fbd9e71b3c1787e88bfe2c0604
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176523"
---
# <a name="cor_gc_stats-structure"></a>COR_GC_STATS – struktura
Poskytuje statistiky o mechanismu uvolňování paměti za běhu společného jazyka (CLR).  
  
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
|`Flags`|Označuje, které hodnoty polí by měly být vypočteny a vráceny.|  
|`ExplicitGCCount`|Označuje počet uvolnění paměti, které byly vynuceny externí požadavek.|  
|`GenCollectionsTaken`|Označuje počet uvolnění paměti provedených pro každou generaci.|  
|`CommittedKBytes`|Celkový počet kilobajtů spáchaných ve všech hromadách.|  
|`ReservedKBytes`|Celkový počet kilobajtů rezervovaných ve všech hromadách.|  
|`Gen0HeapSizeKBytes`|Velikost v kilobajtech haldy generace nula.|  
|`Gen1HeapSizeKBytes`|Velikost v kilobajtech haldy generace.|  
|`Gen2HeapSizeKBytes`|Velikost v kilobajtech haldy generace-dvě.|  
|`LargeObjectHeapSizeKBytes`|Velikost haldy velkého objektu v kilobajtech.|  
|`KBytesPromotedFromGen0`|Velikost objektů v kilobajtech, které jsou povýšeny z generace nula na generaci první.|  
|`KBytesPromotedFromGen1`|Velikost objektů v kilobajtech povýšenz generace jedna generace na dvě generace.|  
  
## <a name="remarks"></a>Poznámky  
 [Metoda ICLRGCManager::GetStats](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-getstats-method.md) vyžaduje, aby `Flags` pole `COR_GC_STATS` struktury bylo nastaveno na jednu nebo více hodnot [výčtu COR_GC_STAT_TYPES](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md) k určení, které statistiky mají být nastaveny.  
  
 Následující tabulka mapuje statistiky poskytované touto strukturou na dvě `COR_GC_COUNTS` `COR_GC_MEMORYUSAGE` [COR_GC_STAT_TYPES](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md) výčtové hodnoty a .  
  
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
 **Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** GCHost.idl  
  
 **Knihovna:** Zahrnuto jako prostředek v souboru MSCorEE.dll  
  
 **Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Struktury pro hostování](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
- [Automatická správa paměti](../../../standard/automatic-memory-management.md)
- [Kolekce paměti](../../../standard/garbage-collection/index.md)
