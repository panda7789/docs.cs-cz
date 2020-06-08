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
ms.openlocfilehash: d19d7ed2262db6d3c6e7f15db0e96da52f86db4a
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500855"
---
# <a name="cor_prf_jit_cache-enumeration"></a><span data-ttu-id="a3fb3-102">COR_PRF_JIT_CACHE – výčet</span><span class="sxs-lookup"><span data-stu-id="a3fb3-102">COR_PRF_JIT_CACHE Enumeration</span></span>
<span data-ttu-id="a3fb3-103">Označuje výsledek hledání funkce uložené v mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="a3fb3-103">Indicates the result of a cached function search.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a3fb3-104">`COR_PRF_CACHED_FUNCTION_FOUND`má hodnotu nula, `COR_PRF_JIT_CACHE` nelze ji proto použít jako logickou náhradu.</span><span class="sxs-lookup"><span data-stu-id="a3fb3-104">`COR_PRF_CACHED_FUNCTION_FOUND` has a value of zero, so `COR_PRF_JIT_CACHE` cannot be used as a Boolean surrogate.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a3fb3-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a3fb3-105">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PRF_CACHED_FUNCTION_FOUND,  
    COR_PRF_CACHED_FUNCTION_NOT_FOUND  
} COR_PRF_JIT_CACHE;  
```  
  
## <a name="members"></a><span data-ttu-id="a3fb3-106">Členové</span><span class="sxs-lookup"><span data-stu-id="a3fb3-106">Members</span></span>  
  
|<span data-ttu-id="a3fb3-107">Člen</span><span class="sxs-lookup"><span data-stu-id="a3fb3-107">Member</span></span>|<span data-ttu-id="a3fb3-108">Description</span><span class="sxs-lookup"><span data-stu-id="a3fb3-108">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_FUNCTION_FOUND`|<span data-ttu-id="a3fb3-109">Hledání nalezlo funkci.</span><span class="sxs-lookup"><span data-stu-id="a3fb3-109">The search found the function.</span></span>|  
|`COR_PRF_FUNCTION_NOT_FOUND`|<span data-ttu-id="a3fb3-110">Hledání nenalezlo funkci.</span><span class="sxs-lookup"><span data-stu-id="a3fb3-110">The search did not find the function.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a3fb3-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a3fb3-111">Requirements</span></span>  
 <span data-ttu-id="a3fb3-112">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a3fb3-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a3fb3-113">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="a3fb3-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a3fb3-114">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="a3fb3-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a3fb3-115">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a3fb3-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3fb3-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a3fb3-116">See also</span></span>

- [<span data-ttu-id="a3fb3-117">Výčty pro profilaci</span><span class="sxs-lookup"><span data-stu-id="a3fb3-117">Profiling Enumerations</span></span>](profiling-enumerations.md)
