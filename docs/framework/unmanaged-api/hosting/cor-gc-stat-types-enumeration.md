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
ms.openlocfilehash: cca393ae34144787ab7800baec7c58209394f30e
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616713"
---
# <a name="cor_gc_stat_types-enumeration"></a><span data-ttu-id="cc7ad-102">COR_GC_STAT_TYPES – výčet</span><span class="sxs-lookup"><span data-stu-id="cc7ad-102">COR_GC_STAT_TYPES Enumeration</span></span>
<span data-ttu-id="cc7ad-103">Určuje statistiku, která má být zaznamenána pro uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="cc7ad-103">Specifies the statistics to be recorded for a garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cc7ad-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cc7ad-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_GC_COUNTS                 = 0x00000001  
    COR_GC_MEMORYUSAGE            = 0x00000002  
} COR_GC_STAT_TYPES;  
```  
  
## <a name="remarks"></a><span data-ttu-id="cc7ad-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="cc7ad-105">Remarks</span></span>  
 <span data-ttu-id="cc7ad-106">Tento výčet Určuje, které statistiky ve [COR_GC_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md) struktuře mají být nastaveny pomocí metody [ICLRGCManager:: getstatistics](iclrgcmanager-getstats-method.md) .</span><span class="sxs-lookup"><span data-stu-id="cc7ad-106">This enumeration specifies which statistics in the [COR_GC_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md) structure are to be set by [ICLRGCManager::GetStats](iclrgcmanager-getstats-method.md) method.</span></span>  
  
## <a name="members"></a><span data-ttu-id="cc7ad-107">Členové</span><span class="sxs-lookup"><span data-stu-id="cc7ad-107">Members</span></span>  
  
|<span data-ttu-id="cc7ad-108">Člen</span><span class="sxs-lookup"><span data-stu-id="cc7ad-108">Member</span></span>|<span data-ttu-id="cc7ad-109">Popis</span><span class="sxs-lookup"><span data-stu-id="cc7ad-109">Description</span></span>|  
|------------|-----------------|  
|`COR_GC_COUNTS`|<span data-ttu-id="cc7ad-110">Zaznamenává počet uvolňování paměti provedených pro každou generaci.</span><span class="sxs-lookup"><span data-stu-id="cc7ad-110">Records the number of garbage collections performed for each generation.</span></span>|  
|`COR_GC_MEMORYUSAGE`|<span data-ttu-id="cc7ad-111">Zaznamenává využití paměti a statistiky velikosti uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="cc7ad-111">Records memory usage and garbage collection size statistics.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="cc7ad-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="cc7ad-112">Requirements</span></span>  
 <span data-ttu-id="cc7ad-113">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cc7ad-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cc7ad-114">**Hlavička:** GCHost. idl, GCHost. h</span><span class="sxs-lookup"><span data-stu-id="cc7ad-114">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="cc7ad-115">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cc7ad-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc7ad-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="cc7ad-116">See also</span></span>

- [<span data-ttu-id="cc7ad-117">COR_GC_STATS – struktura</span><span class="sxs-lookup"><span data-stu-id="cc7ad-117">COR_GC_STATS Structure</span></span>](cor-gc-stats-structure.md)
- [<span data-ttu-id="cc7ad-118">Výčty hostování</span><span class="sxs-lookup"><span data-stu-id="cc7ad-118">Hosting Enumerations</span></span>](hosting-enumerations.md)
