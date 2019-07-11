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
ms.openlocfilehash: 6fdfe33c5b488d8f464001a86233124d4e7df0ed
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67779067"
---
# <a name="corgcstattypes-enumeration"></a><span data-ttu-id="7ec9b-102">COR_GC_STAT_TYPES – výčet</span><span class="sxs-lookup"><span data-stu-id="7ec9b-102">COR_GC_STAT_TYPES Enumeration</span></span>
<span data-ttu-id="7ec9b-103">Určuje statistiky, které mají být zaznamenány pro uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="7ec9b-103">Specifies the statistics to be recorded for a garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7ec9b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7ec9b-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_GC_COUNTS                 = 0x00000001  
    COR_GC_MEMORYUSAGE            = 0x00000002  
} COR_GC_STAT_TYPES;  
```  
  
## <a name="remarks"></a><span data-ttu-id="7ec9b-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7ec9b-105">Remarks</span></span>  
 <span data-ttu-id="7ec9b-106">Tento výčet Určuje, jaké statistické údaje ve [cor_gc_stats –](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md) struktura se může nastavit [iclrgcmanager::getstats –](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-getstats-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="7ec9b-106">This enumeration specifies which statistics in the [COR_GC_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md) structure are to be set by [ICLRGCManager::GetStats](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-getstats-method.md) method.</span></span>  
  
## <a name="members"></a><span data-ttu-id="7ec9b-107">Členové</span><span class="sxs-lookup"><span data-stu-id="7ec9b-107">Members</span></span>  
  
|<span data-ttu-id="7ec9b-108">Člen</span><span class="sxs-lookup"><span data-stu-id="7ec9b-108">Member</span></span>|<span data-ttu-id="7ec9b-109">Popis</span><span class="sxs-lookup"><span data-stu-id="7ec9b-109">Description</span></span>|  
|------------|-----------------|  
|`COR_GC_COUNTS`|<span data-ttu-id="7ec9b-110">Zaznamenává počet uvolnění paměti provést pro každé generaci.</span><span class="sxs-lookup"><span data-stu-id="7ec9b-110">Records the number of garbage collections performed for each generation.</span></span>|  
|`COR_GC_MEMORYUSAGE`|<span data-ttu-id="7ec9b-111">Zaznamenává využití a uvolňování paměti kolekce velikost Statistika paměti.</span><span class="sxs-lookup"><span data-stu-id="7ec9b-111">Records memory usage and garbage collection size statistics.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7ec9b-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7ec9b-112">Requirements</span></span>  
 <span data-ttu-id="7ec9b-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7ec9b-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7ec9b-114">**Záhlaví:** GCHost.idl, GCHost.h</span><span class="sxs-lookup"><span data-stu-id="7ec9b-114">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="7ec9b-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7ec9b-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ec9b-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7ec9b-116">See also</span></span>

- [<span data-ttu-id="7ec9b-117">COR_GC_STATS – struktura</span><span class="sxs-lookup"><span data-stu-id="7ec9b-117">COR_GC_STATS Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md)
- [<span data-ttu-id="7ec9b-118">Výčty pro hostování</span><span class="sxs-lookup"><span data-stu-id="7ec9b-118">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
