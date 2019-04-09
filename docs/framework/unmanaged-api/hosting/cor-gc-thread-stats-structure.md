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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f60a4b56270318a05d0e5a480fdb56eb45593d5e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59177733"
---
# <a name="corgcthreadstats-structure"></a><span data-ttu-id="587f4-102">COR_GC_THREAD_STATS – struktura</span><span class="sxs-lookup"><span data-stu-id="587f4-102">COR_GC_THREAD_STATS Structure</span></span>
<span data-ttu-id="587f4-103">Obsahuje vlákno statistiky týkající se uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="587f4-103">Contains per-thread statistics pertaining to garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="587f4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="587f4-104">Syntax</span></span>  
  
```  
typedef struct _COR_GC_THREAD_STATS {  
    ULONGLONG  PerThreadAllocation;   
    ULONG      Flags;   
} COR_GC_THREAD_STATS;  
```  
  
## <a name="members"></a><span data-ttu-id="587f4-105">Členové</span><span class="sxs-lookup"><span data-stu-id="587f4-105">Members</span></span>  
  
|<span data-ttu-id="587f4-106">Člen</span><span class="sxs-lookup"><span data-stu-id="587f4-106">Member</span></span>|<span data-ttu-id="587f4-107">Popis</span><span class="sxs-lookup"><span data-stu-id="587f4-107">Description</span></span>|  
|------------|-----------------|  
|`PerThreadAllocation`|<span data-ttu-id="587f4-108">Počet bajtů paměti přidělené ve vlákně, které souvisí s aktuálním `COR_GC_THREAD_STATS` instance.</span><span class="sxs-lookup"><span data-stu-id="587f4-108">The number of bytes of memory allocated on the thread that is associated with the current `COR_GC_THREAD_STATS` instance.</span></span> <span data-ttu-id="587f4-109">Toto číslo se vymaže na nulu pokaždé, když dojde k uvolnění paměti generace nula.</span><span class="sxs-lookup"><span data-stu-id="587f4-109">This number is cleared to zero each time a generation-zero garbage collection occurs.</span></span>|  
|`Flags`|<span data-ttu-id="587f4-110">Počet bajtů povýšen na vyšší generaci uvolňování paměti na poslední.</span><span class="sxs-lookup"><span data-stu-id="587f4-110">The number of bytes promoted to a higher generation at the most recent garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="587f4-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="587f4-111">Remarks</span></span>  
 <span data-ttu-id="587f4-112">[Iclrtask::getmemstats –](../../../../docs/framework/unmanaged-api/hosting/iclrtask-getmemstats-method.md) trvá výstupní parametr typu `COR_GC_THREAD_STATS`.</span><span class="sxs-lookup"><span data-stu-id="587f4-112">[ICLRTask::GetMemStats](../../../../docs/framework/unmanaged-api/hosting/iclrtask-getmemstats-method.md) takes an output parameter of type `COR_GC_THREAD_STATS`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="587f4-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="587f4-113">Requirements</span></span>  
 <span data-ttu-id="587f4-114">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="587f4-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="587f4-115">**Záhlaví:** GCHost.idl</span><span class="sxs-lookup"><span data-stu-id="587f4-115">**Header:** GCHost.idl</span></span>  
  
 <span data-ttu-id="587f4-116">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="587f4-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="587f4-117">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="587f4-117">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="587f4-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="587f4-118">See also</span></span>

- [<span data-ttu-id="587f4-119">Struktury pro hostování</span><span class="sxs-lookup"><span data-stu-id="587f4-119">Hosting Structures</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
- [<span data-ttu-id="587f4-120">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="587f4-120">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
