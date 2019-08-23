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
# <a name="cor_gc_stats-structure"></a><span data-ttu-id="98f11-102">COR_GC_STATS – struktura</span><span class="sxs-lookup"><span data-stu-id="98f11-102">COR_GC_STATS Structure</span></span>
<span data-ttu-id="98f11-103">Poskytuje statistiku o mechanizmu uvolňování paměti modulu CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="98f11-103">Provides statistics about the garbage collection mechanism of the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="98f11-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="98f11-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="98f11-105">Členové</span><span class="sxs-lookup"><span data-stu-id="98f11-105">Members</span></span>  
  
|<span data-ttu-id="98f11-106">Člen</span><span class="sxs-lookup"><span data-stu-id="98f11-106">Member</span></span>|<span data-ttu-id="98f11-107">Popis</span><span class="sxs-lookup"><span data-stu-id="98f11-107">Description</span></span>|  
|------------|-----------------|  
|`Flags`|<span data-ttu-id="98f11-108">Určuje, které hodnoty pole se mají vypočítat a vrátit.</span><span class="sxs-lookup"><span data-stu-id="98f11-108">Indicates which field values should be calculated and returned.</span></span>|  
|`ExplicitGCCount`|<span data-ttu-id="98f11-109">Označuje počet uvolňování paměti, které byly vynuceny externím požadavkem.</span><span class="sxs-lookup"><span data-stu-id="98f11-109">Indicates the number of garbage collections that were forced by external request.</span></span>|  
|`GenCollectionsTaken`|<span data-ttu-id="98f11-110">Označuje počet uvolňování paměti provedených pro každou generaci.</span><span class="sxs-lookup"><span data-stu-id="98f11-110">Indicates the number of garbage collections performed for each generation.</span></span>|  
|`CommittedKBytes`|<span data-ttu-id="98f11-111">Celkový počet kilobajtů potvrzených ve všech haldách.</span><span class="sxs-lookup"><span data-stu-id="98f11-111">The total number of kilobytes committed in all heaps.</span></span>|  
|`ReservedKBytes`|<span data-ttu-id="98f11-112">Celkový počet kilobajtů rezervovaných ve všech haldách.</span><span class="sxs-lookup"><span data-stu-id="98f11-112">The total number of kilobytes reserved in all heaps.</span></span>|  
|`Gen0HeapSizeKBytes`|<span data-ttu-id="98f11-113">Velikost haldy generace s hodnotou v kilobajtech.</span><span class="sxs-lookup"><span data-stu-id="98f11-113">The size, in kilobytes, of the generation-zero heap.</span></span>|  
|`Gen1HeapSizeKBytes`|<span data-ttu-id="98f11-114">Velikost haldy generace-jedna v kilobajtech.</span><span class="sxs-lookup"><span data-stu-id="98f11-114">The size, in kilobytes, of the generation-one heap.</span></span>|  
|`Gen2HeapSizeKBytes`|<span data-ttu-id="98f11-115">Velikost haldy generace-dvě v kilobajtech.</span><span class="sxs-lookup"><span data-stu-id="98f11-115">The size, in kilobytes, of the generation-two heap.</span></span>|  
|`LargeObjectHeapSizeKBytes`|<span data-ttu-id="98f11-116">Velikost haldy velkých objektů v kilobajtech.</span><span class="sxs-lookup"><span data-stu-id="98f11-116">The size, in kilobytes, of the large object heap.</span></span>|  
|`KBytesPromotedFromGen0`|<span data-ttu-id="98f11-117">Velikost objektů pozměněných z generace na hodnotu v kilobajtech na jednu generaci.</span><span class="sxs-lookup"><span data-stu-id="98f11-117">The size, in kilobytes, of the objects promoted from generation zero to generation one.</span></span>|  
|`KBytesPromotedFromGen1`|<span data-ttu-id="98f11-118">Velikost objektů povýšených od generace od generace do 2. generace v kilobajtech.</span><span class="sxs-lookup"><span data-stu-id="98f11-118">The size, in kilobytes, of the objects promoted from generation one to generation two.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="98f11-119">Poznámky</span><span class="sxs-lookup"><span data-stu-id="98f11-119">Remarks</span></span>  
 <span data-ttu-id="98f11-120">Metoda [ICLRGCManager::](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-getstats-method.md) GetStats vyžaduje, `Flags` aby pole `COR_GC_STATS` struktury bylo nastavené na jednu nebo více hodnot výčtu [COR_GC_STAT_TYPES](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md) , aby se určilo, která Statistika se má nastavit.</span><span class="sxs-lookup"><span data-stu-id="98f11-120">The [ICLRGCManager::GetStats](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-getstats-method.md) method requires the `Flags` field of the `COR_GC_STATS` structure to be set to one or more values of the [COR_GC_STAT_TYPES](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md) enumeration to specify which statistics are to be set.</span></span>  
  
 <span data-ttu-id="98f11-121">Následující tabulka mapuje statistiky poskytované touto strukturou na dvě hodnoty `COR_GC_COUNTS` výčtu COR_GC_STAT_TYPES a. [](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md) `COR_GC_MEMORYUSAGE`</span><span class="sxs-lookup"><span data-stu-id="98f11-121">The following table maps the statistics provided by this structure to the two [COR_GC_STAT_TYPES](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md) enumeration values, `COR_GC_COUNTS` and `COR_GC_MEMORYUSAGE`.</span></span>  
  
|<span data-ttu-id="98f11-122">Určeno COR_GC_COUNTS</span><span class="sxs-lookup"><span data-stu-id="98f11-122">Specified by COR_GC_COUNTS</span></span>|<span data-ttu-id="98f11-123">Určeno COR_GC_MEMORYUSAGE</span><span class="sxs-lookup"><span data-stu-id="98f11-123">Specified by COR_GC_MEMORYUSAGE</span></span>|  
|----------------------------------|---------------------------------------|  
|`ExplicitGCCount`<br /><br /> `GenCollectionsTaken`|`CommittedKBytes`<br /><br /> `ReservedKBytes`<br /><br /> `Gen0HeapSizeKBytes`<br /><br /> `Gen1HeapSizeKBytes`<br /><br /> `Gen2HeapSizeKBytes`<br /><br /> `LargeObjectHeapSizeKBytes`<br /><br /> `KBytesPromotedFromGen0`<br /><br /> `KBytesPromotedFromGen1`|  
  
 <span data-ttu-id="98f11-124">Příklad použití je následující:</span><span class="sxs-lookup"><span data-stu-id="98f11-124">An example of the usage is as follows:</span></span>  
  
```cpp  
COR_GC_STATS GCStats;  
GCStats.Flags = COR_GC_COUNTS | COR_GC_MEMORYUSAGE;  
pCLRGCManager->GetStats(&GCStats);  
```  
  
## <a name="requirements"></a><span data-ttu-id="98f11-125">Požadavky</span><span class="sxs-lookup"><span data-stu-id="98f11-125">Requirements</span></span>  
 <span data-ttu-id="98f11-126">**Platformu** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="98f11-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="98f11-127">**Hlaviček** GCHost.idl</span><span class="sxs-lookup"><span data-stu-id="98f11-127">**Header:** GCHost.idl</span></span>  
  
 <span data-ttu-id="98f11-128">**Knihovna** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="98f11-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="98f11-129">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="98f11-129">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98f11-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="98f11-130">See also</span></span>

- [<span data-ttu-id="98f11-131">Struktury pro hostování</span><span class="sxs-lookup"><span data-stu-id="98f11-131">Hosting Structures</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
- [<span data-ttu-id="98f11-132">Automatická správa paměti</span><span class="sxs-lookup"><span data-stu-id="98f11-132">Automatic Memory Management</span></span>](../../../standard/automatic-memory-management.md)
- [<span data-ttu-id="98f11-133">Uvolňování paměti</span><span class="sxs-lookup"><span data-stu-id="98f11-133">Garbage Collection</span></span>](../../../standard/garbage-collection/index.md)
