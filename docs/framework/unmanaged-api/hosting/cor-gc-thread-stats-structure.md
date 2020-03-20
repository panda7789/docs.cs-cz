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
ms.openlocfilehash: 64e0c466edcd8863244e6ed184c18422b5f66875
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178270"
---
# <a name="cor_gc_thread_stats-structure"></a><span data-ttu-id="c895c-102">COR_GC_THREAD_STATS – struktura</span><span class="sxs-lookup"><span data-stu-id="c895c-102">COR_GC_THREAD_STATS Structure</span></span>
<span data-ttu-id="c895c-103">Obsahuje statistiky podle vlákna týkající se uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="c895c-103">Contains per-thread statistics pertaining to garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c895c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c895c-104">Syntax</span></span>  
  
```cpp  
typedef struct _COR_GC_THREAD_STATS {  
    ULONGLONG  PerThreadAllocation;
    ULONG      Flags;
} COR_GC_THREAD_STATS;  
```  
  
## <a name="members"></a><span data-ttu-id="c895c-105">Členové</span><span class="sxs-lookup"><span data-stu-id="c895c-105">Members</span></span>  
  
|<span data-ttu-id="c895c-106">Člen</span><span class="sxs-lookup"><span data-stu-id="c895c-106">Member</span></span>|<span data-ttu-id="c895c-107">Popis</span><span class="sxs-lookup"><span data-stu-id="c895c-107">Description</span></span>|  
|------------|-----------------|  
|`PerThreadAllocation`|<span data-ttu-id="c895c-108">Počet bajtů paměti přidělené ve vlákně, která `COR_GC_THREAD_STATS` je přidružena k aktuální instanci.</span><span class="sxs-lookup"><span data-stu-id="c895c-108">The number of bytes of memory allocated on the thread that is associated with the current `COR_GC_THREAD_STATS` instance.</span></span> <span data-ttu-id="c895c-109">Toto číslo je vymazána na nulu pokaždé, když dojde k uvolnění paměti generace nula.</span><span class="sxs-lookup"><span data-stu-id="c895c-109">This number is cleared to zero each time a generation-zero garbage collection occurs.</span></span>|  
|`Flags`|<span data-ttu-id="c895c-110">Počet bajtů povýšen na vyšší generace na poslední uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="c895c-110">The number of bytes promoted to a higher generation at the most recent garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c895c-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c895c-111">Remarks</span></span>  
 <span data-ttu-id="c895c-112">[ICLRTask::GetMemStats](../../../../docs/framework/unmanaged-api/hosting/iclrtask-getmemstats-method.md) přebírá výstupní parametr `COR_GC_THREAD_STATS`typu .</span><span class="sxs-lookup"><span data-stu-id="c895c-112">[ICLRTask::GetMemStats](../../../../docs/framework/unmanaged-api/hosting/iclrtask-getmemstats-method.md) takes an output parameter of type `COR_GC_THREAD_STATS`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c895c-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c895c-113">Requirements</span></span>  
 <span data-ttu-id="c895c-114">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c895c-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c895c-115">**Záhlaví:** GCHost.idl</span><span class="sxs-lookup"><span data-stu-id="c895c-115">**Header:** GCHost.idl</span></span>  
  
 <span data-ttu-id="c895c-116">**Knihovna:** Zahrnuto jako prostředek v souboru MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c895c-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c895c-117">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c895c-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c895c-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="c895c-118">See also</span></span>

- [<span data-ttu-id="c895c-119">Struktury pro hostování</span><span class="sxs-lookup"><span data-stu-id="c895c-119">Hosting Structures</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
- [<span data-ttu-id="c895c-120">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c895c-120">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
