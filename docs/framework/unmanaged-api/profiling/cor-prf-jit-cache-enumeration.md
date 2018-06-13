---
title: COR_PRF_JIT_CACHE – výčet
ms.date: 03/30/2017
api_name:
- COR_PRF_JIT_CACHE
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_JIT_CACHE
helpviewer_keywords:
- COR_PRF_JIT_CACHE enumeration [.NET Framework profiling]
ms.assetid: e7b8f6b4-95bc-4ba5-b9eb-f5590a7326a4
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b8c972bcace3ba3d855a3b5eebc16e6b76994eb7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33450701"
---
# <a name="corprfjitcache-enumeration"></a><span data-ttu-id="75266-102">COR_PRF_JIT_CACHE – výčet</span><span class="sxs-lookup"><span data-stu-id="75266-102">COR_PRF_JIT_CACHE Enumeration</span></span>
<span data-ttu-id="75266-103">Určuje výsledky hledání v mezipaměti funkce.</span><span class="sxs-lookup"><span data-stu-id="75266-103">Indicates the result of a cached function search.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="75266-104">`COR_PRF_CACHED_FUNCTION_FOUND` má hodnotu nula, takže `COR_PRF_JIT_CACHE` nelze použít jako logická hodnota náhradní.</span><span class="sxs-lookup"><span data-stu-id="75266-104">`COR_PRF_CACHED_FUNCTION_FOUND` has a value of zero, so `COR_PRF_JIT_CACHE` cannot be used as a Boolean surrogate.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="75266-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="75266-105">Syntax</span></span>  
  
```  
typedef enum {  
    COR_PRF_CACHED_FUNCTION_FOUND,  
    COR_PRF_CACHED_FUNCTION_NOT_FOUND  
} COR_PRF_JIT_CACHE;  
```  
  
## <a name="members"></a><span data-ttu-id="75266-106">Členové</span><span class="sxs-lookup"><span data-stu-id="75266-106">Members</span></span>  
  
|<span data-ttu-id="75266-107">Člen</span><span class="sxs-lookup"><span data-stu-id="75266-107">Member</span></span>|<span data-ttu-id="75266-108">Popis</span><span class="sxs-lookup"><span data-stu-id="75266-108">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_FUNCTION_FOUND`|<span data-ttu-id="75266-109">Při hledání nebyly nalezeny funkce.</span><span class="sxs-lookup"><span data-stu-id="75266-109">The search found the function.</span></span>|  
|`COR_PRF_FUNCTION_NOT_FOUND`|<span data-ttu-id="75266-110">Funkce hledání nebyl nalezen.</span><span class="sxs-lookup"><span data-stu-id="75266-110">The search did not find the function.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="75266-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="75266-111">Requirements</span></span>  
 <span data-ttu-id="75266-112">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="75266-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="75266-113">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="75266-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="75266-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="75266-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="75266-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="75266-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75266-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="75266-116">See Also</span></span>  
 [<span data-ttu-id="75266-117">Výčty pro profilaci</span><span class="sxs-lookup"><span data-stu-id="75266-117">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
