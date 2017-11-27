---
title: "COR_GC_STATS – struktura"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COR_GC_STATS
api_location: mscoree.dll
api_type: COM
f1_keywords: COR_GC_STATS
helpviewer_keywords: COR_GC_STATS structure [.NET Framework hosting]
ms.assetid: 8d4ff73e-739b-40f6-9349-359fbc99c2f9
topic_type: apiref
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e7c620c4a33032711abc0d7b82af908018bd44cf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="corgcstats-structure"></a><span data-ttu-id="0b1e8-102">COR_GC_STATS – struktura</span><span class="sxs-lookup"><span data-stu-id="0b1e8-102">COR_GC_STATS Structure</span></span>
<span data-ttu-id="0b1e8-103">Poskytuje statistiky o mechanismus kolekce paměti common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="0b1e8-103">Provides statistics about the garbage collection mechanism of the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0b1e8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0b1e8-104">Syntax</span></span>  
  
```  
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
  
## <a name="members"></a><span data-ttu-id="0b1e8-105">Členové</span><span class="sxs-lookup"><span data-stu-id="0b1e8-105">Members</span></span>  
  
|<span data-ttu-id="0b1e8-106">Člen</span><span class="sxs-lookup"><span data-stu-id="0b1e8-106">Member</span></span>|<span data-ttu-id="0b1e8-107">Popis</span><span class="sxs-lookup"><span data-stu-id="0b1e8-107">Description</span></span>|  
|------------|-----------------|  
|`Flags`|<span data-ttu-id="0b1e8-108">Určuje pole hodnot, které by mělo být vypočtena a vrátil.</span><span class="sxs-lookup"><span data-stu-id="0b1e8-108">Indicates which field values should be calculated and returned.</span></span>|  
|`ExplicitGCCount`|<span data-ttu-id="0b1e8-109">Označuje počet kolekce paměti, které byly vynutit externí požadavek.</span><span class="sxs-lookup"><span data-stu-id="0b1e8-109">Indicates the number of garbage collections that were forced by external request.</span></span>|  
|`GenCollectionsTaken`|<span data-ttu-id="0b1e8-110">Označuje počet provést pro každou generaci kolekce.</span><span class="sxs-lookup"><span data-stu-id="0b1e8-110">Indicates the number of garbage collections performed for each generation.</span></span>|  
|`CommittedKBytes`|<span data-ttu-id="0b1e8-111">Celkový počet kilobajtů potvrzené ve všech haldách</span><span class="sxs-lookup"><span data-stu-id="0b1e8-111">The total number of kilobytes committed in all heaps.</span></span>|  
|`ReservedKBytes`|<span data-ttu-id="0b1e8-112">Celkový počet kilobajtů vyhrazené ve všech haldách</span><span class="sxs-lookup"><span data-stu-id="0b1e8-112">The total number of kilobytes reserved in all heaps.</span></span>|  
|`Gen0HeapSizeKBytes`|<span data-ttu-id="0b1e8-113">Velikost v kilobajtech haldě generování než nula.</span><span class="sxs-lookup"><span data-stu-id="0b1e8-113">The size, in kilobytes, of the generation-zero heap.</span></span>|  
|`Gen1HeapSizeKBytes`|<span data-ttu-id="0b1e8-114">Velikost v kilobajtech haldy 1. generace.</span><span class="sxs-lookup"><span data-stu-id="0b1e8-114">The size, in kilobytes, of the generation-one heap.</span></span>|  
|`Gen2HeapSizeKBytes`|<span data-ttu-id="0b1e8-115">Velikost v kilobajtech haldě generování dva.</span><span class="sxs-lookup"><span data-stu-id="0b1e8-115">The size, in kilobytes, of the generation-two heap.</span></span>|  
|`LargeObjectHeapSizeKBytes`|<span data-ttu-id="0b1e8-116">Velikost v kilobajtech haldě velkého objektu.</span><span class="sxs-lookup"><span data-stu-id="0b1e8-116">The size, in kilobytes, of the large object heap.</span></span>|  
|`KBytesPromotedFromGen0`|<span data-ttu-id="0b1e8-117">Velikost v kilobajtech objekty povýší z generování nula generace jeden.</span><span class="sxs-lookup"><span data-stu-id="0b1e8-117">The size, in kilobytes, of the objects promoted from generation zero to generation one.</span></span>|  
|`KBytesPromotedFromGen1`|<span data-ttu-id="0b1e8-118">Velikost v kilobajtech povýší z generace, jedna generace dva objekty.</span><span class="sxs-lookup"><span data-stu-id="0b1e8-118">The size, in kilobytes, of the objects promoted from generation one to generation two.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0b1e8-119">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0b1e8-119">Remarks</span></span>  
 <span data-ttu-id="0b1e8-120">[Iclrgcmanager::getstats –](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-getstats-method.md) metoda vyžaduje, `Flags` pole z `COR_GC_STATS` struktura bude nastaven na jeden nebo více hodnot [COR_GC_STAT_TYPES](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md) výčtu k určete, které statistiky se nastavit.</span><span class="sxs-lookup"><span data-stu-id="0b1e8-120">The [ICLRGCManager::GetStats](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-getstats-method.md) method requires the `Flags` field of the `COR_GC_STATS` structure to be set to one or more values of the [COR_GC_STAT_TYPES](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md) enumeration to specify which statistics are to be set.</span></span>  
  
 <span data-ttu-id="0b1e8-121">Následující tabulka mapuje statistiky poskytované tuto strukturu pro dvě [COR_GC_STAT_TYPES](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md) hodnoty výčtu, `COR_GC_COUNTS` a `COR_GC_MEMORYUSAGE`.</span><span class="sxs-lookup"><span data-stu-id="0b1e8-121">The following table maps the statistics provided by this structure to the two [COR_GC_STAT_TYPES](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md) enumeration values, `COR_GC_COUNTS` and `COR_GC_MEMORYUSAGE`.</span></span>  
  
|<span data-ttu-id="0b1e8-122">Určeného COR_GC_COUNTS</span><span class="sxs-lookup"><span data-stu-id="0b1e8-122">Specified by COR_GC_COUNTS</span></span>|<span data-ttu-id="0b1e8-123">Určeného COR_GC_MEMORYUSAGE</span><span class="sxs-lookup"><span data-stu-id="0b1e8-123">Specified by COR_GC_MEMORYUSAGE</span></span>|  
|----------------------------------|---------------------------------------|  
|`ExplicitGCCount`<br /><br /> `GenCollectionsTaken`|`CommittedKBytes`<br /><br /> `ReservedKBytes`<br /><br /> `Gen0HeapSizeKBytes`<br /><br /> `Gen1HeapSizeKBytes`<br /><br /> `Gen2HeapSizeKBytes`<br /><br /> `LargeObjectHeapSizeKBytes`<br /><br /> `KBytesPromotedFromGen0`<br /><br /> `KBytesPromotedFromGen1`|  
  
 <span data-ttu-id="0b1e8-124">Příklad použití je následující:</span><span class="sxs-lookup"><span data-stu-id="0b1e8-124">An example of the usage is as follows:</span></span>  
  
```  
COR_GC_STATS GCStats;  
GCStats.Flags = COR_GC_COUNTS | COR_GC_MEMORYUSAGE;  
pCLRGCManager->GetStats(&GCStats);  
```  
  
## <a name="requirements"></a><span data-ttu-id="0b1e8-125">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0b1e8-125">Requirements</span></span>  
 <span data-ttu-id="0b1e8-126">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0b1e8-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0b1e8-127">**Záhlaví:** GCHost.idl</span><span class="sxs-lookup"><span data-stu-id="0b1e8-127">**Header:** GCHost.idl</span></span>  
  
 <span data-ttu-id="0b1e8-128">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="0b1e8-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0b1e8-129">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0b1e8-129">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b1e8-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="0b1e8-130">See Also</span></span>  
 [<span data-ttu-id="0b1e8-131">Struktury pro hostování</span><span class="sxs-lookup"><span data-stu-id="0b1e8-131">Hosting Structures</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)  
 [<span data-ttu-id="0b1e8-132">Automatická správa paměti</span><span class="sxs-lookup"><span data-stu-id="0b1e8-132">Automatic Memory Management</span></span>](../../../../docs/standard/automatic-memory-management.md)  
 [<span data-ttu-id="0b1e8-133">Uvolňování paměti</span><span class="sxs-lookup"><span data-stu-id="0b1e8-133">Garbage Collection</span></span>](../../../../docs/standard/garbage-collection/index.md)
