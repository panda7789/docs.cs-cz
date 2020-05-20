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
ms.openlocfilehash: 88e81779fc9c20c506f3b0aa11ac2da3958dfe86
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616694"
---
# <a name="cor_gc_thread_stats-structure"></a><span data-ttu-id="25cf4-102">COR_GC_THREAD_STATS – struktura</span><span class="sxs-lookup"><span data-stu-id="25cf4-102">COR_GC_THREAD_STATS Structure</span></span>
<span data-ttu-id="25cf4-103">Obsahuje statistiku jednotlivých vláken, která souvisí s uvolňováním paměti.</span><span class="sxs-lookup"><span data-stu-id="25cf4-103">Contains per-thread statistics pertaining to garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="25cf4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="25cf4-104">Syntax</span></span>  
  
```cpp  
typedef struct _COR_GC_THREAD_STATS {  
    ULONGLONG  PerThreadAllocation;
    ULONG      Flags;
} COR_GC_THREAD_STATS;  
```  
  
## <a name="members"></a><span data-ttu-id="25cf4-105">Členové</span><span class="sxs-lookup"><span data-stu-id="25cf4-105">Members</span></span>  
  
|<span data-ttu-id="25cf4-106">Člen</span><span class="sxs-lookup"><span data-stu-id="25cf4-106">Member</span></span>|<span data-ttu-id="25cf4-107">Popis</span><span class="sxs-lookup"><span data-stu-id="25cf4-107">Description</span></span>|  
|------------|-----------------|  
|`PerThreadAllocation`|<span data-ttu-id="25cf4-108">Počet bajtů paměti přidělených vláknu, které je přidruženo k aktuální `COR_GC_THREAD_STATS` instanci.</span><span class="sxs-lookup"><span data-stu-id="25cf4-108">The number of bytes of memory allocated on the thread that is associated with the current `COR_GC_THREAD_STATS` instance.</span></span> <span data-ttu-id="25cf4-109">U tohoto čísla se vymaže nula pokaždé, když dojde k uvolnění paměti bez generace.</span><span class="sxs-lookup"><span data-stu-id="25cf4-109">This number is cleared to zero each time a generation-zero garbage collection occurs.</span></span>|  
|`Flags`|<span data-ttu-id="25cf4-110">Počet bajtů povýšených na vyšší generaci při nejnovějším uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="25cf4-110">The number of bytes promoted to a higher generation at the most recent garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="25cf4-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="25cf4-111">Remarks</span></span>  
 <span data-ttu-id="25cf4-112">[ICLRTask:: getmemstats –](iclrtask-getmemstats-method.md) přebírá výstupní parametr typu `COR_GC_THREAD_STATS` .</span><span class="sxs-lookup"><span data-stu-id="25cf4-112">[ICLRTask::GetMemStats](iclrtask-getmemstats-method.md) takes an output parameter of type `COR_GC_THREAD_STATS`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="25cf4-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="25cf4-113">Requirements</span></span>  
 <span data-ttu-id="25cf4-114">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="25cf4-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="25cf4-115">**Hlavička:** GCHost. idl</span><span class="sxs-lookup"><span data-stu-id="25cf4-115">**Header:** GCHost.idl</span></span>  
  
 <span data-ttu-id="25cf4-116">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="25cf4-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="25cf4-117">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="25cf4-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25cf4-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="25cf4-118">See also</span></span>

- [<span data-ttu-id="25cf4-119">Struktury pro hostování</span><span class="sxs-lookup"><span data-stu-id="25cf4-119">Hosting Structures</span></span>](hosting-structures.md)
- [<span data-ttu-id="25cf4-120">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="25cf4-120">IHostTask Interface</span></span>](ihosttask-interface.md)
