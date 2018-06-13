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
ms.openlocfilehash: 24a386fe82bbd004954924a573c090af7f58824a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33431825"
---
# <a name="corgcthreadstats-structure"></a><span data-ttu-id="77aa8-102">COR_GC_THREAD_STATS – struktura</span><span class="sxs-lookup"><span data-stu-id="77aa8-102">COR_GC_THREAD_STATS Structure</span></span>
<span data-ttu-id="77aa8-103">Obsahuje vlákno statistiky týkající se uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="77aa8-103">Contains per-thread statistics pertaining to garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="77aa8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="77aa8-104">Syntax</span></span>  
  
```  
typedef struct _COR_GC_THREAD_STATS {  
    ULONGLONG  PerThreadAllocation;   
    ULONG      Flags;   
} COR_GC_THREAD_STATS;  
```  
  
## <a name="members"></a><span data-ttu-id="77aa8-105">Členové</span><span class="sxs-lookup"><span data-stu-id="77aa8-105">Members</span></span>  
  
|<span data-ttu-id="77aa8-106">Člen</span><span class="sxs-lookup"><span data-stu-id="77aa8-106">Member</span></span>|<span data-ttu-id="77aa8-107">Popis</span><span class="sxs-lookup"><span data-stu-id="77aa8-107">Description</span></span>|  
|------------|-----------------|  
|`PerThreadAllocation`|<span data-ttu-id="77aa8-108">Počet bajtů paměti přidělené na vlákno, které souvisí s aktuálním `COR_GC_THREAD_STATS` instance.</span><span class="sxs-lookup"><span data-stu-id="77aa8-108">The number of bytes of memory allocated on the thread that is associated with the current `COR_GC_THREAD_STATS` instance.</span></span> <span data-ttu-id="77aa8-109">Toto číslo je zrušeno na nulu pokaždé, když dojde k nule generování uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="77aa8-109">This number is cleared to zero each time a generation-zero garbage collection occurs.</span></span>|  
|`Flags`|<span data-ttu-id="77aa8-110">Počet bajtů povýšen na vyšší generace uvolňování paměti na poslední.</span><span class="sxs-lookup"><span data-stu-id="77aa8-110">The number of bytes promoted to a higher generation at the most recent garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="77aa8-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="77aa8-111">Remarks</span></span>  
 <span data-ttu-id="77aa8-112">[Iclrtask::getmemstats –](../../../../docs/framework/unmanaged-api/hosting/iclrtask-getmemstats-method.md) trvá výstupní parametr typu `COR_GC_THREAD_STATS`.</span><span class="sxs-lookup"><span data-stu-id="77aa8-112">[ICLRTask::GetMemStats](../../../../docs/framework/unmanaged-api/hosting/iclrtask-getmemstats-method.md) takes an output parameter of type `COR_GC_THREAD_STATS`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="77aa8-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="77aa8-113">Requirements</span></span>  
 <span data-ttu-id="77aa8-114">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="77aa8-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="77aa8-115">**Záhlaví:** GCHost.idl</span><span class="sxs-lookup"><span data-stu-id="77aa8-115">**Header:** GCHost.idl</span></span>  
  
 <span data-ttu-id="77aa8-116">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="77aa8-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="77aa8-117">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="77aa8-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77aa8-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="77aa8-118">See Also</span></span>  
 [<span data-ttu-id="77aa8-119">Struktury pro hostování</span><span class="sxs-lookup"><span data-stu-id="77aa8-119">Hosting Structures</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)  
 [<span data-ttu-id="77aa8-120">IHostTask – rozhraní</span><span class="sxs-lookup"><span data-stu-id="77aa8-120">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
