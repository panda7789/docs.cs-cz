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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a984e8645bec0f58d8a31965b762e0a3a190ba59
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67768015"
---
# <a name="corgcthreadstatstypes-enumeration"></a><span data-ttu-id="2b425-102">COR_GC_THREAD_STATS_TYPES – výčet</span><span class="sxs-lookup"><span data-stu-id="2b425-102">COR_GC_THREAD_STATS_TYPES Enumeration</span></span>
<span data-ttu-id="2b425-103">Určuje kolekci statistiky uvolňování paměti pro vlákno.</span><span class="sxs-lookup"><span data-stu-id="2b425-103">Indicates the garbage collection statistics for a thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2b425-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2b425-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_GC_THREAD_HAS_PROMOTED_BYTES  = 0x00000001  
} COR_GC_THREAD_STATS_TYPES;  
```  
  
## <a name="members"></a><span data-ttu-id="2b425-105">Členové</span><span class="sxs-lookup"><span data-stu-id="2b425-105">Members</span></span>  
  
|<span data-ttu-id="2b425-106">Člen</span><span class="sxs-lookup"><span data-stu-id="2b425-106">Member</span></span>|<span data-ttu-id="2b425-107">Popis</span><span class="sxs-lookup"><span data-stu-id="2b425-107">Description</span></span>|  
|------------|-----------------|  
|`COR_GC_THREAD_HAS_PROMOTED_BYTES`|<span data-ttu-id="2b425-108">Vlákno má bajtů, které byly přesunuty v aktuální kolekci uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="2b425-108">The thread has bytes that were promoted in the most recent garbage collection.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="2b425-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2b425-109">Requirements</span></span>  
 <span data-ttu-id="2b425-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2b425-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2b425-111">**Záhlaví:** GCHost.idl, GCHost.h</span><span class="sxs-lookup"><span data-stu-id="2b425-111">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="2b425-112">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2b425-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b425-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2b425-113">See also</span></span>

- [<span data-ttu-id="2b425-114">Výčty pro hostování</span><span class="sxs-lookup"><span data-stu-id="2b425-114">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
