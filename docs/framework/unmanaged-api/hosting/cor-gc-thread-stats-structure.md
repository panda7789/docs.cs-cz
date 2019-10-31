---
title: COR_GC_THREAD_STATS – struktura
ms.date: 03/30/2017
api_name:
- COR_GC_THREAD_STATS
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- COR_GC_THREAD_STATS
helpviewer_keywords:
- COR_GC_THREAD_STATS structure [.NET Framework hosting]
ms.assetid: 01f9a59b-7679-4d42-9ced-4a8981625c3d
topic_type:
- apiref
ms.openlocfilehash: 37da471aaa8e9f802a8430d7b3289b375ff1b40a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136986"
---
# <a name="cor_gc_thread_stats-structure"></a><span data-ttu-id="e34d8-102">COR_GC_THREAD_STATS – struktura</span><span class="sxs-lookup"><span data-stu-id="e34d8-102">COR_GC_THREAD_STATS Structure</span></span>
<span data-ttu-id="e34d8-103">Obsahuje statistiku jednotlivých vláken, která souvisí s uvolňováním paměti.</span><span class="sxs-lookup"><span data-stu-id="e34d8-103">Contains per-thread statistics pertaining to garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e34d8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e34d8-104">Syntax</span></span>  
  
```cpp  
typedef struct _COR_GC_THREAD_STATS {  
    ULONGLONG  PerThreadAllocation;   
    ULONG      Flags;   
} COR_GC_THREAD_STATS;  
```  
  
## <a name="members"></a><span data-ttu-id="e34d8-105">Členové</span><span class="sxs-lookup"><span data-stu-id="e34d8-105">Members</span></span>  
  
|<span data-ttu-id="e34d8-106">Člen</span><span class="sxs-lookup"><span data-stu-id="e34d8-106">Member</span></span>|<span data-ttu-id="e34d8-107">Popis</span><span class="sxs-lookup"><span data-stu-id="e34d8-107">Description</span></span>|  
|------------|-----------------|  
|`PerThreadAllocation`|<span data-ttu-id="e34d8-108">Počet bajtů paměti přidělených vláknu, které je přidruženo k aktuální instanci `COR_GC_THREAD_STATS`.</span><span class="sxs-lookup"><span data-stu-id="e34d8-108">The number of bytes of memory allocated on the thread that is associated with the current `COR_GC_THREAD_STATS` instance.</span></span> <span data-ttu-id="e34d8-109">U tohoto čísla se vymaže nula pokaždé, když dojde k uvolnění paměti bez generace.</span><span class="sxs-lookup"><span data-stu-id="e34d8-109">This number is cleared to zero each time a generation-zero garbage collection occurs.</span></span>|  
|`Flags`|<span data-ttu-id="e34d8-110">Počet bajtů povýšených na vyšší generaci při nejnovějším uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="e34d8-110">The number of bytes promoted to a higher generation at the most recent garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e34d8-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e34d8-111">Remarks</span></span>  
 <span data-ttu-id="e34d8-112">[ICLRTask:: getmemstats –](../../../../docs/framework/unmanaged-api/hosting/iclrtask-getmemstats-method.md) přebírá výstupní parametr typu `COR_GC_THREAD_STATS`.</span><span class="sxs-lookup"><span data-stu-id="e34d8-112">[ICLRTask::GetMemStats](../../../../docs/framework/unmanaged-api/hosting/iclrtask-getmemstats-method.md) takes an output parameter of type `COR_GC_THREAD_STATS`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e34d8-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e34d8-113">Requirements</span></span>  
 <span data-ttu-id="e34d8-114">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e34d8-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e34d8-115">**Hlavička:** GCHost. idl</span><span class="sxs-lookup"><span data-stu-id="e34d8-115">**Header:** GCHost.idl</span></span>  
  
 <span data-ttu-id="e34d8-116">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="e34d8-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e34d8-117">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e34d8-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e34d8-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e34d8-118">See also</span></span>

- [<span data-ttu-id="e34d8-119">Struktury pro hostování</span><span class="sxs-lookup"><span data-stu-id="e34d8-119">Hosting Structures</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
- [<span data-ttu-id="e34d8-120">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e34d8-120">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
