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
# <a name="corgcstats-structure"></a><span data-ttu-id="c4ff6-102">COR_GC_STATS – struktura</span><span class="sxs-lookup"><span data-stu-id="c4ff6-102">COR_GC_STATS Structure</span></span>
<span data-ttu-id="c4ff6-103">Poskytuje statistické údaje o mechanismu uvolnění paměti kolekce modulu common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="c4ff6-103">Provides statistics about the garbage collection mechanism of the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c4ff6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c4ff6-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="c4ff6-105">Členové</span><span class="sxs-lookup"><span data-stu-id="c4ff6-105">Members</span></span>  
  
|<span data-ttu-id="c4ff6-106">Člen</span><span class="sxs-lookup"><span data-stu-id="c4ff6-106">Member</span></span>|<span data-ttu-id="c4ff6-107">Popis</span><span class="sxs-lookup"><span data-stu-id="c4ff6-107">Description</span></span>|  
|------------|-----------------|  
|`Flags`|<span data-ttu-id="c4ff6-108">Určuje pole hodnot, které by měl vypočítá a vrátí.</span><span class="sxs-lookup"><span data-stu-id="c4ff6-108">Indicates which field values should be calculated and returned.</span></span>|  
|`ExplicitGCCount`|<span data-ttu-id="c4ff6-109">Označuje počet uvolnění paměti, které byly vynutit externí požadavek.</span><span class="sxs-lookup"><span data-stu-id="c4ff6-109">Indicates the number of garbage collections that were forced by external request.</span></span>|  
|`GenCollectionsTaken`|<span data-ttu-id="c4ff6-110">Označuje číslo, které provádí pro každé generaci uvolňování pamětí.</span><span class="sxs-lookup"><span data-stu-id="c4ff6-110">Indicates the number of garbage collections performed for each generation.</span></span>|  
|`CommittedKBytes`|<span data-ttu-id="c4ff6-111">Celkový počet kilobajtů potvrzeny ve všech haldách.</span><span class="sxs-lookup"><span data-stu-id="c4ff6-111">The total number of kilobytes committed in all heaps.</span></span>|  
|`ReservedKBytes`|<span data-ttu-id="c4ff6-112">Celkový počet kilobajtů vyhrazené ve všech haldách.</span><span class="sxs-lookup"><span data-stu-id="c4ff6-112">The total number of kilobytes reserved in all heaps.</span></span>|  
|`Gen0HeapSizeKBytes`|<span data-ttu-id="c4ff6-113">Velikost v kilobajtech, generování nuly haldy.</span><span class="sxs-lookup"><span data-stu-id="c4ff6-113">The size, in kilobytes, of the generation-zero heap.</span></span>|  
|`Gen1HeapSizeKBytes`|<span data-ttu-id="c4ff6-114">Velikost v kilobajtech haldy generování: 1.</span><span class="sxs-lookup"><span data-stu-id="c4ff6-114">The size, in kilobytes, of the generation-one heap.</span></span>|  
|`Gen2HeapSizeKBytes`|<span data-ttu-id="c4ff6-115">Velikost v kilobajtech haldy 2. generace.</span><span class="sxs-lookup"><span data-stu-id="c4ff6-115">The size, in kilobytes, of the generation-two heap.</span></span>|  
|`LargeObjectHeapSizeKBytes`|<span data-ttu-id="c4ff6-116">Velikost v kilobajtech velkých objektových haldách.</span><span class="sxs-lookup"><span data-stu-id="c4ff6-116">The size, in kilobytes, of the large object heap.</span></span>|  
|`KBytesPromotedFromGen0`|<span data-ttu-id="c4ff6-117">Velikost v kilobajtech objektů, které jsou přesunuty z generace nula do generování jednoho.</span><span class="sxs-lookup"><span data-stu-id="c4ff6-117">The size, in kilobytes, of the objects promoted from generation zero to generation one.</span></span>|  
|`KBytesPromotedFromGen1`|<span data-ttu-id="c4ff6-118">Velikost v kilobajtech objektů, které jsou přesunuty z jednoho. generace do 2. generace.</span><span class="sxs-lookup"><span data-stu-id="c4ff6-118">The size, in kilobytes, of the objects promoted from generation one to generation two.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c4ff6-119">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c4ff6-119">Remarks</span></span>  
 <span data-ttu-id="c4ff6-120">[Iclrgcmanager::getstats –](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-getstats-method.md) metoda vyžaduje `Flags` pole `COR_GC_STATS` struktura nastavili na jeden nebo více hodnot [cor_gc_stat_types –](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md) výčet k určení statistiky jsou nastavení.</span><span class="sxs-lookup"><span data-stu-id="c4ff6-120">The [ICLRGCManager::GetStats](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-getstats-method.md) method requires the `Flags` field of the `COR_GC_STATS` structure to be set to one or more values of the [COR_GC_STAT_TYPES](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md) enumeration to specify which statistics are to be set.</span></span>  
  
 <span data-ttu-id="c4ff6-121">Následující tabulka mapuje statistiky poskytuje tuto strukturu pro dvě [cor_gc_stat_types –](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md) hodnot výčtu, `COR_GC_COUNTS` a `COR_GC_MEMORYUSAGE`.</span><span class="sxs-lookup"><span data-stu-id="c4ff6-121">The following table maps the statistics provided by this structure to the two [COR_GC_STAT_TYPES](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md) enumeration values, `COR_GC_COUNTS` and `COR_GC_MEMORYUSAGE`.</span></span>  
  
|<span data-ttu-id="c4ff6-122">Určená COR_GC_COUNTS</span><span class="sxs-lookup"><span data-stu-id="c4ff6-122">Specified by COR_GC_COUNTS</span></span>|<span data-ttu-id="c4ff6-123">Určená COR_GC_MEMORYUSAGE</span><span class="sxs-lookup"><span data-stu-id="c4ff6-123">Specified by COR_GC_MEMORYUSAGE</span></span>|  
|----------------------------------|---------------------------------------|  
|`ExplicitGCCount`<br /><br /> `GenCollectionsTaken`|`CommittedKBytes`<br /><br /> `ReservedKBytes`<br /><br /> `Gen0HeapSizeKBytes`<br /><br /> `Gen1HeapSizeKBytes`<br /><br /> `Gen2HeapSizeKBytes`<br /><br /> `LargeObjectHeapSizeKBytes`<br /><br /> `KBytesPromotedFromGen0`<br /><br /> `KBytesPromotedFromGen1`|  
  
 <span data-ttu-id="c4ff6-124">Příklad použití je následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="c4ff6-124">An example of the usage is as follows:</span></span>  
  
```cpp  
COR_GC_STATS GCStats;  
GCStats.Flags = COR_GC_COUNTS | COR_GC_MEMORYUSAGE;  
pCLRGCManager->GetStats(&GCStats);  
```  
  
## <a name="requirements"></a><span data-ttu-id="c4ff6-125">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c4ff6-125">Requirements</span></span>  
 <span data-ttu-id="c4ff6-126">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c4ff6-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c4ff6-127">**Záhlaví:** GCHost.idl</span><span class="sxs-lookup"><span data-stu-id="c4ff6-127">**Header:** GCHost.idl</span></span>  
  
 <span data-ttu-id="c4ff6-128">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c4ff6-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c4ff6-129">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c4ff6-129">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4ff6-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c4ff6-130">See also</span></span>

- [<span data-ttu-id="c4ff6-131">Struktury pro hostování</span><span class="sxs-lookup"><span data-stu-id="c4ff6-131">Hosting Structures</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
- [<span data-ttu-id="c4ff6-132">Automatická správa paměti</span><span class="sxs-lookup"><span data-stu-id="c4ff6-132">Automatic Memory Management</span></span>](../../../../docs/standard/automatic-memory-management.md)
- [<span data-ttu-id="c4ff6-133">Uvolňování paměti</span><span class="sxs-lookup"><span data-stu-id="c4ff6-133">Garbage Collection</span></span>](../../../../docs/standard/garbage-collection/index.md)
