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
ms.openlocfilehash: 4bd12feb47352d9bb78aa8ef056072f9bdc6fba3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54710323"
---
# <a name="corgcstattypes-enumeration"></a><span data-ttu-id="804de-102">COR_GC_STAT_TYPES – výčet</span><span class="sxs-lookup"><span data-stu-id="804de-102">COR_GC_STAT_TYPES Enumeration</span></span>
<span data-ttu-id="804de-103">Určuje statistiky, které mají být zaznamenány pro uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="804de-103">Specifies the statistics to be recorded for a garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="804de-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="804de-104">Syntax</span></span>  
  
```  
typedef enum {  
    COR_GC_COUNTS                 = 0x00000001  
    COR_GC_MEMORYUSAGE            = 0x00000002  
} COR_GC_STAT_TYPES;  
```  
  
## <a name="remarks"></a><span data-ttu-id="804de-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="804de-105">Remarks</span></span>  
 <span data-ttu-id="804de-106">Tento výčet Určuje, jaké statistické údaje ve [cor_gc_stats –](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md) struktura se může nastavit [iclrgcmanager::getstats –](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-getstats-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="804de-106">This enumeration specifies which statistics in the [COR_GC_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md) structure are to be set by [ICLRGCManager::GetStats](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-getstats-method.md) method.</span></span>  
  
## <a name="members"></a><span data-ttu-id="804de-107">Členové</span><span class="sxs-lookup"><span data-stu-id="804de-107">Members</span></span>  
  
|<span data-ttu-id="804de-108">Člen</span><span class="sxs-lookup"><span data-stu-id="804de-108">Member</span></span>|<span data-ttu-id="804de-109">Popis</span><span class="sxs-lookup"><span data-stu-id="804de-109">Description</span></span>|  
|------------|-----------------|  
|`COR_GC_COUNTS`|<span data-ttu-id="804de-110">Zaznamenává počet uvolnění paměti provést pro každé generaci.</span><span class="sxs-lookup"><span data-stu-id="804de-110">Records the number of garbage collections performed for each generation.</span></span>|  
|`COR_GC_MEMORYUSAGE`|<span data-ttu-id="804de-111">Zaznamenává využití a uvolňování paměti kolekce velikost Statistika paměti.</span><span class="sxs-lookup"><span data-stu-id="804de-111">Records memory usage and garbage collection size statistics.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="804de-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="804de-112">Requirements</span></span>  
 <span data-ttu-id="804de-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="804de-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="804de-114">**Záhlaví:** GCHost.idl, GCHost.h</span><span class="sxs-lookup"><span data-stu-id="804de-114">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="804de-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="804de-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="804de-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="804de-116">See also</span></span>
- [<span data-ttu-id="804de-117">COR_GC_STATS – struktura</span><span class="sxs-lookup"><span data-stu-id="804de-117">COR_GC_STATS Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md)
- [<span data-ttu-id="804de-118">Výčty pro hostování</span><span class="sxs-lookup"><span data-stu-id="804de-118">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
