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
ms.openlocfilehash: 0cdbe36403f830926d611ffdc655d82ea25ddeef
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59144791"
---
# <a name="corprfjitcache-enumeration"></a><span data-ttu-id="d3b36-102">COR_PRF_JIT_CACHE – výčet</span><span class="sxs-lookup"><span data-stu-id="d3b36-102">COR_PRF_JIT_CACHE Enumeration</span></span>
<span data-ttu-id="d3b36-103">Určuje výsledky hledání funkce uložené v mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="d3b36-103">Indicates the result of a cached function search.</span></span>  
  
> [!NOTE]
>  `COR_PRF_CACHED_FUNCTION_FOUND` <span data-ttu-id="d3b36-104">má hodnotu nula, takže `COR_PRF_JIT_CACHE` nelze použít jako logická náhrady.</span><span class="sxs-lookup"><span data-stu-id="d3b36-104">has a value of zero, so `COR_PRF_JIT_CACHE` cannot be used as a Boolean surrogate.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d3b36-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d3b36-105">Syntax</span></span>  
  
```  
typedef enum {  
    COR_PRF_CACHED_FUNCTION_FOUND,  
    COR_PRF_CACHED_FUNCTION_NOT_FOUND  
} COR_PRF_JIT_CACHE;  
```  
  
## <a name="members"></a><span data-ttu-id="d3b36-106">Členové</span><span class="sxs-lookup"><span data-stu-id="d3b36-106">Members</span></span>  
  
|<span data-ttu-id="d3b36-107">Člen</span><span class="sxs-lookup"><span data-stu-id="d3b36-107">Member</span></span>|<span data-ttu-id="d3b36-108">Popis</span><span class="sxs-lookup"><span data-stu-id="d3b36-108">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_FUNCTION_FOUND`|<span data-ttu-id="d3b36-109">Při hledání nebyly nalezeny funkce.</span><span class="sxs-lookup"><span data-stu-id="d3b36-109">The search found the function.</span></span>|  
|`COR_PRF_FUNCTION_NOT_FOUND`|<span data-ttu-id="d3b36-110">Hledání nebyly nalezeny funkce.</span><span class="sxs-lookup"><span data-stu-id="d3b36-110">The search did not find the function.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d3b36-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d3b36-111">Requirements</span></span>  
 <span data-ttu-id="d3b36-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d3b36-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d3b36-113">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="d3b36-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d3b36-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d3b36-114">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="d3b36-115">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="d3b36-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="d3b36-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d3b36-116">See also</span></span>

- [<span data-ttu-id="d3b36-117">Profilace výčtů</span><span class="sxs-lookup"><span data-stu-id="d3b36-117">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
