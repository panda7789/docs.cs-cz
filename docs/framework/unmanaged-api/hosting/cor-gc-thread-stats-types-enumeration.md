---
title: COR_GC_THREAD_STATS_TYPES – výčet
ms.date: 03/30/2017
api_name:
- COR_GC_THREAD_STATS_TYPES
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- COR_GC_THREAD_STATS_TYPES
helpviewer_keywords:
- COR_GC_THREAD_STATS_TYPES enumeration [.NET Framework hosting]
ms.assetid: aa227704-0ab1-4b08-aee2-1f439762162e
topic_type:
- apiref
ms.openlocfilehash: 2206499cad9be2a29f485ee66d468accbe00b5f5
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616673"
---
# <a name="cor_gc_thread_stats_types-enumeration"></a><span data-ttu-id="c7199-102">COR_GC_THREAD_STATS_TYPES – výčet</span><span class="sxs-lookup"><span data-stu-id="c7199-102">COR_GC_THREAD_STATS_TYPES Enumeration</span></span>
<span data-ttu-id="c7199-103">Označuje statistiku uvolňování paměti pro vlákno.</span><span class="sxs-lookup"><span data-stu-id="c7199-103">Indicates the garbage collection statistics for a thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c7199-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c7199-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_GC_THREAD_HAS_PROMOTED_BYTES  = 0x00000001  
} COR_GC_THREAD_STATS_TYPES;  
```  
  
## <a name="members"></a><span data-ttu-id="c7199-105">Členové</span><span class="sxs-lookup"><span data-stu-id="c7199-105">Members</span></span>  
  
|<span data-ttu-id="c7199-106">Člen</span><span class="sxs-lookup"><span data-stu-id="c7199-106">Member</span></span>|<span data-ttu-id="c7199-107">Popis</span><span class="sxs-lookup"><span data-stu-id="c7199-107">Description</span></span>|  
|------------|-----------------|  
|`COR_GC_THREAD_HAS_PROMOTED_BYTES`|<span data-ttu-id="c7199-108">Vlákno obsahuje bajty, které byly povýšeny v nejnovějším uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="c7199-108">The thread has bytes that were promoted in the most recent garbage collection.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c7199-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c7199-109">Requirements</span></span>  
 <span data-ttu-id="c7199-110">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c7199-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c7199-111">**Hlavička:** GCHost. idl, GCHost. h</span><span class="sxs-lookup"><span data-stu-id="c7199-111">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="c7199-112">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c7199-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7199-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="c7199-113">See also</span></span>

- [<span data-ttu-id="c7199-114">Výčty hostování</span><span class="sxs-lookup"><span data-stu-id="c7199-114">Hosting Enumerations</span></span>](hosting-enumerations.md)
