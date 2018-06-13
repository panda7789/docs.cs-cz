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
ms.openlocfilehash: eac378a48900d5820ad35587a6d269648ef99a77
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33428896"
---
# <a name="corgcstattypes-enumeration"></a><span data-ttu-id="04167-102">COR_GC_STAT_TYPES – výčet</span><span class="sxs-lookup"><span data-stu-id="04167-102">COR_GC_STAT_TYPES Enumeration</span></span>
<span data-ttu-id="04167-103">Určuje statistiky, které mají být zaznamenány pro uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="04167-103">Specifies the statistics to be recorded for a garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="04167-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="04167-104">Syntax</span></span>  
  
```  
typedef enum {  
    COR_GC_COUNTS                 = 0x00000001  
    COR_GC_MEMORYUSAGE            = 0x00000002  
} COR_GC_STAT_TYPES;  
```  
  
## <a name="remarks"></a><span data-ttu-id="04167-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="04167-105">Remarks</span></span>  
 <span data-ttu-id="04167-106">Tento výčet Určuje, jaké statistické údaje ve [cor_gc_stats –](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md) struktura jsou nastavení [iclrgcmanager::getstats –](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-getstats-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="04167-106">This enumeration specifies which statistics in the [COR_GC_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md) structure are to be set by [ICLRGCManager::GetStats](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-getstats-method.md) method.</span></span>  
  
## <a name="members"></a><span data-ttu-id="04167-107">Členové</span><span class="sxs-lookup"><span data-stu-id="04167-107">Members</span></span>  
  
|<span data-ttu-id="04167-108">Člen</span><span class="sxs-lookup"><span data-stu-id="04167-108">Member</span></span>|<span data-ttu-id="04167-109">Popis</span><span class="sxs-lookup"><span data-stu-id="04167-109">Description</span></span>|  
|------------|-----------------|  
|`COR_GC_COUNTS`|<span data-ttu-id="04167-110">Zaznamenává počet kolekce provést pro každou generaci.</span><span class="sxs-lookup"><span data-stu-id="04167-110">Records the number of garbage collections performed for each generation.</span></span>|  
|`COR_GC_MEMORYUSAGE`|<span data-ttu-id="04167-111">Zaznamenává paměť a využití paměti kolekce velikost statistiky.</span><span class="sxs-lookup"><span data-stu-id="04167-111">Records memory usage and garbage collection size statistics.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="04167-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="04167-112">Requirements</span></span>  
 <span data-ttu-id="04167-113">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="04167-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="04167-114">**Záhlaví:** GCHost.idl, GCHost.h</span><span class="sxs-lookup"><span data-stu-id="04167-114">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="04167-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="04167-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04167-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="04167-116">See Also</span></span>  
 [<span data-ttu-id="04167-117">COR_GC_STATS – struktura</span><span class="sxs-lookup"><span data-stu-id="04167-117">COR_GC_STATS Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md)  
 [<span data-ttu-id="04167-118">Výčty pro hostování</span><span class="sxs-lookup"><span data-stu-id="04167-118">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
