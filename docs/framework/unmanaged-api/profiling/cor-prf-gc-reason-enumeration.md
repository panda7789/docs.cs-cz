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
ms.openlocfilehash: daf97f25b1adc30b173fcd81812a4b197915cdd1
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59196941"
---
# <a name="corprfgcreason-enumeration"></a><span data-ttu-id="af986-102">COR_PRF_GC_REASON – výčet</span><span class="sxs-lookup"><span data-stu-id="af986-102">COR_PRF_GC_REASON Enumeration</span></span>
<span data-ttu-id="af986-103">Označuje, že uvolňování paměti dochází důvod.</span><span class="sxs-lookup"><span data-stu-id="af986-103">Indicates the reason that garbage collection is occurring.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="af986-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="af986-104">Syntax</span></span>  
  
```  
typedef enum {  
    COR_PRF_GC_INDUCED = 1,  
    COR_PRF_GC_OTHER = 0  
} COR_PRF_GC_REASON;  
```  
  
## <a name="members"></a><span data-ttu-id="af986-105">Členové</span><span class="sxs-lookup"><span data-stu-id="af986-105">Members</span></span>  
  
|<span data-ttu-id="af986-106">Člen</span><span class="sxs-lookup"><span data-stu-id="af986-106">Member</span></span>|<span data-ttu-id="af986-107">Popis</span><span class="sxs-lookup"><span data-stu-id="af986-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_GC_INDUCED`|<span data-ttu-id="af986-108">Kolekce paměti byla vyvolaná <xref:System.GC.Collect%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="af986-108">The garbage collection was induced by a <xref:System.GC.Collect%2A> method.</span></span>|  
|`COR_PRF_GC_OTHER`|<span data-ttu-id="af986-109">Důvod není zadána.</span><span class="sxs-lookup"><span data-stu-id="af986-109">The reason is unspecified.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="af986-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="af986-110">Requirements</span></span>  
 <span data-ttu-id="af986-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="af986-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="af986-112">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="af986-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="af986-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="af986-113">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="af986-114">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="af986-114">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="af986-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="af986-115">See also</span></span>

- [<span data-ttu-id="af986-116">Profilace výčtů</span><span class="sxs-lookup"><span data-stu-id="af986-116">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
