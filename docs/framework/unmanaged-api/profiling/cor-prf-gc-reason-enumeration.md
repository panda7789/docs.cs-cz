---
title: COR_PRF_GC_REASON – výčet
ms.date: 03/30/2017
api_name:
- COR_PRF_GC_REASON
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_GC_REASON
helpviewer_keywords:
- COR_PRF_GC_REASON enumeration [.NET Framework profiling]
ms.assetid: 72822b95-a7fb-485e-9d55-1cb016d9a458
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 13740920e8db5d44b71cd3c324742945c64b3e59
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54498957"
---
# <a name="corprfgcreason-enumeration"></a><span data-ttu-id="1dded-102">COR_PRF_GC_REASON – výčet</span><span class="sxs-lookup"><span data-stu-id="1dded-102">COR_PRF_GC_REASON Enumeration</span></span>
<span data-ttu-id="1dded-103">Označuje, že uvolňování paměti dochází důvod.</span><span class="sxs-lookup"><span data-stu-id="1dded-103">Indicates the reason that garbage collection is occurring.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1dded-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1dded-104">Syntax</span></span>  
  
```  
typedef enum {  
    COR_PRF_GC_INDUCED = 1,  
    COR_PRF_GC_OTHER = 0  
} COR_PRF_GC_REASON;  
```  
  
## <a name="members"></a><span data-ttu-id="1dded-105">Členové</span><span class="sxs-lookup"><span data-stu-id="1dded-105">Members</span></span>  
  
|<span data-ttu-id="1dded-106">Člen</span><span class="sxs-lookup"><span data-stu-id="1dded-106">Member</span></span>|<span data-ttu-id="1dded-107">Popis</span><span class="sxs-lookup"><span data-stu-id="1dded-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_GC_INDUCED`|<span data-ttu-id="1dded-108">Kolekce paměti byla vyvolaná <xref:System.GC.Collect%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="1dded-108">The garbage collection was induced by a <xref:System.GC.Collect%2A> method.</span></span>|  
|`COR_PRF_GC_OTHER`|<span data-ttu-id="1dded-109">Důvod není zadána.</span><span class="sxs-lookup"><span data-stu-id="1dded-109">The reason is unspecified.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1dded-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1dded-110">Requirements</span></span>  
 <span data-ttu-id="1dded-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1dded-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1dded-112">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="1dded-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="1dded-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1dded-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1dded-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1dded-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1dded-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1dded-115">See also</span></span>
- [<span data-ttu-id="1dded-116">Výčty pro profilaci</span><span class="sxs-lookup"><span data-stu-id="1dded-116">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
