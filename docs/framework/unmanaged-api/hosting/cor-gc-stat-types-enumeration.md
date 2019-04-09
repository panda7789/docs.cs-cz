---
title: COR_GC_STAT_TYPES – výčet
ms.date: 03/30/2017
api_name:
- COR_GC_STAT_TYPES
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- COR_GC_STAT_TYPES
helpviewer_keywords:
- COR_GC_STAT_TYPES enumeration [.NET Framework hosting]
ms.assetid: fc51d6db-f7f8-408b-b93d-c166fc712c99
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9e228cfbdade420c4d5248ffd417c6131083ee74
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59110414"
---
# <a name="corgcstattypes-enumeration"></a><span data-ttu-id="65411-102">COR_GC_STAT_TYPES – výčet</span><span class="sxs-lookup"><span data-stu-id="65411-102">COR_GC_STAT_TYPES Enumeration</span></span>
<span data-ttu-id="65411-103">Určuje statistiky, které mají být zaznamenány pro uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="65411-103">Specifies the statistics to be recorded for a garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="65411-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="65411-104">Syntax</span></span>  
  
```  
typedef enum {  
    COR_GC_COUNTS                 = 0x00000001  
    COR_GC_MEMORYUSAGE            = 0x00000002  
} COR_GC_STAT_TYPES;  
```  
  
## <a name="remarks"></a><span data-ttu-id="65411-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="65411-105">Remarks</span></span>  
 <span data-ttu-id="65411-106">Tento výčet Určuje, jaké statistické údaje ve [cor_gc_stats –](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md) struktura se může nastavit [iclrgcmanager::getstats –](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-getstats-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="65411-106">This enumeration specifies which statistics in the [COR_GC_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md) structure are to be set by [ICLRGCManager::GetStats](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-getstats-method.md) method.</span></span>  
  
## <a name="members"></a><span data-ttu-id="65411-107">Členové</span><span class="sxs-lookup"><span data-stu-id="65411-107">Members</span></span>  
  
|<span data-ttu-id="65411-108">Člen</span><span class="sxs-lookup"><span data-stu-id="65411-108">Member</span></span>|<span data-ttu-id="65411-109">Popis</span><span class="sxs-lookup"><span data-stu-id="65411-109">Description</span></span>|  
|------------|-----------------|  
|`COR_GC_COUNTS`|<span data-ttu-id="65411-110">Zaznamenává počet uvolnění paměti provést pro každé generaci.</span><span class="sxs-lookup"><span data-stu-id="65411-110">Records the number of garbage collections performed for each generation.</span></span>|  
|`COR_GC_MEMORYUSAGE`|<span data-ttu-id="65411-111">Zaznamenává využití a uvolňování paměti kolekce velikost Statistika paměti.</span><span class="sxs-lookup"><span data-stu-id="65411-111">Records memory usage and garbage collection size statistics.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="65411-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="65411-112">Requirements</span></span>  
 <span data-ttu-id="65411-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="65411-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="65411-114">**Záhlaví:** GCHost.idl, GCHost.h</span><span class="sxs-lookup"><span data-stu-id="65411-114">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 **<span data-ttu-id="65411-115">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="65411-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="65411-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="65411-116">See also</span></span>

- [<span data-ttu-id="65411-117">COR_GC_STATS – struktura</span><span class="sxs-lookup"><span data-stu-id="65411-117">COR_GC_STATS Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md)
- [<span data-ttu-id="65411-118">Výčty hostování</span><span class="sxs-lookup"><span data-stu-id="65411-118">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
