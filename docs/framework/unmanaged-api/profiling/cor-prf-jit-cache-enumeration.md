---
title: "COR_PRF_JIT_CACHE – výčet"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COR_PRF_JIT_CACHE
api_location: mscorwks.dll
api_type: COM
f1_keywords: COR_PRF_JIT_CACHE
helpviewer_keywords: COR_PRF_JIT_CACHE enumeration [.NET Framework profiling]
ms.assetid: e7b8f6b4-95bc-4ba5-b9eb-f5590a7326a4
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5041e12c6745d43518ee2ac45e3a0a79c1c50ca3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="corprfjitcache-enumeration"></a><span data-ttu-id="843e9-102">COR_PRF_JIT_CACHE – výčet</span><span class="sxs-lookup"><span data-stu-id="843e9-102">COR_PRF_JIT_CACHE Enumeration</span></span>
<span data-ttu-id="843e9-103">Určuje výsledky hledání v mezipaměti funkce.</span><span class="sxs-lookup"><span data-stu-id="843e9-103">Indicates the result of a cached function search.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="843e9-104">`COR_PRF_CACHED_FUNCTION_FOUND`má hodnotu nula, takže `COR_PRF_JIT_CACHE` nelze použít jako logická hodnota náhradní.</span><span class="sxs-lookup"><span data-stu-id="843e9-104">`COR_PRF_CACHED_FUNCTION_FOUND` has a value of zero, so `COR_PRF_JIT_CACHE` cannot be used as a Boolean surrogate.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="843e9-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="843e9-105">Syntax</span></span>  
  
```  
typedef enum {  
    COR_PRF_CACHED_FUNCTION_FOUND,  
    COR_PRF_CACHED_FUNCTION_NOT_FOUND  
} COR_PRF_JIT_CACHE;  
```  
  
## <a name="members"></a><span data-ttu-id="843e9-106">Členové</span><span class="sxs-lookup"><span data-stu-id="843e9-106">Members</span></span>  
  
|<span data-ttu-id="843e9-107">Člen</span><span class="sxs-lookup"><span data-stu-id="843e9-107">Member</span></span>|<span data-ttu-id="843e9-108">Popis</span><span class="sxs-lookup"><span data-stu-id="843e9-108">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_FUNCTION_FOUND`|<span data-ttu-id="843e9-109">Při hledání nebyly nalezeny funkce.</span><span class="sxs-lookup"><span data-stu-id="843e9-109">The search found the function.</span></span>|  
|`COR_PRF_FUNCTION_NOT_FOUND`|<span data-ttu-id="843e9-110">Funkce hledání nebyl nalezen.</span><span class="sxs-lookup"><span data-stu-id="843e9-110">The search did not find the function.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="843e9-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="843e9-111">Requirements</span></span>  
 <span data-ttu-id="843e9-112">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="843e9-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="843e9-113">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="843e9-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="843e9-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="843e9-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="843e9-115">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="843e9-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="843e9-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="843e9-116">See Also</span></span>  
 [<span data-ttu-id="843e9-117">Výčty pro profilaci</span><span class="sxs-lookup"><span data-stu-id="843e9-117">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
