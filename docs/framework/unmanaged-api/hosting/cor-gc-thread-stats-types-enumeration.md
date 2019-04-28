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
ms.openlocfilehash: c631a0a3abb3cb2a342dfd44fdffb147b742ae3c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61698119"
---
# <a name="corgcthreadstatstypes-enumeration"></a><span data-ttu-id="6cf62-102">COR_GC_THREAD_STATS_TYPES – výčet</span><span class="sxs-lookup"><span data-stu-id="6cf62-102">COR_GC_THREAD_STATS_TYPES Enumeration</span></span>
<span data-ttu-id="6cf62-103">Určuje kolekci statistiky uvolňování paměti pro vlákno.</span><span class="sxs-lookup"><span data-stu-id="6cf62-103">Indicates the garbage collection statistics for a thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6cf62-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6cf62-104">Syntax</span></span>  
  
```  
typedef enum {  
    COR_GC_THREAD_HAS_PROMOTED_BYTES  = 0x00000001  
} COR_GC_THREAD_STATS_TYPES;  
```  
  
## <a name="members"></a><span data-ttu-id="6cf62-105">Členové</span><span class="sxs-lookup"><span data-stu-id="6cf62-105">Members</span></span>  
  
|<span data-ttu-id="6cf62-106">Člen</span><span class="sxs-lookup"><span data-stu-id="6cf62-106">Member</span></span>|<span data-ttu-id="6cf62-107">Popis</span><span class="sxs-lookup"><span data-stu-id="6cf62-107">Description</span></span>|  
|------------|-----------------|  
|`COR_GC_THREAD_HAS_PROMOTED_BYTES`|<span data-ttu-id="6cf62-108">Vlákno má bajtů, které byly přesunuty v aktuální kolekci uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="6cf62-108">The thread has bytes that were promoted in the most recent garbage collection.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6cf62-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6cf62-109">Requirements</span></span>  
 <span data-ttu-id="6cf62-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6cf62-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6cf62-111">**Záhlaví:** GCHost.idl, GCHost.h</span><span class="sxs-lookup"><span data-stu-id="6cf62-111">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="6cf62-112">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6cf62-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6cf62-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6cf62-113">See also</span></span>

- [<span data-ttu-id="6cf62-114">Výčty pro hostování</span><span class="sxs-lookup"><span data-stu-id="6cf62-114">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
