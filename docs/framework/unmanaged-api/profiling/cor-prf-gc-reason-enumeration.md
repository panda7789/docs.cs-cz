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
ms.openlocfilehash: 63f6ea4a348b3035a1f0b1d3e00f61f689915fa2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33450096"
---
# <a name="corprfgcreason-enumeration"></a><span data-ttu-id="a5e99-102">COR_PRF_GC_REASON – výčet</span><span class="sxs-lookup"><span data-stu-id="a5e99-102">COR_PRF_GC_REASON Enumeration</span></span>
<span data-ttu-id="a5e99-103">Určuje, z důvodu probíhající uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="a5e99-103">Indicates the reason that garbage collection is occurring.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a5e99-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a5e99-104">Syntax</span></span>  
  
```  
typedef enum {  
    COR_PRF_GC_INDUCED = 1,  
    COR_PRF_GC_OTHER = 0  
} COR_PRF_GC_REASON;  
```  
  
## <a name="members"></a><span data-ttu-id="a5e99-105">Členové</span><span class="sxs-lookup"><span data-stu-id="a5e99-105">Members</span></span>  
  
|<span data-ttu-id="a5e99-106">Člen</span><span class="sxs-lookup"><span data-stu-id="a5e99-106">Member</span></span>|<span data-ttu-id="a5e99-107">Popis</span><span class="sxs-lookup"><span data-stu-id="a5e99-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_GC_INDUCED`|<span data-ttu-id="a5e99-108">Kolekce paměti bylo získáno <xref:System.GC.Collect%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="a5e99-108">The garbage collection was induced by a <xref:System.GC.Collect%2A> method.</span></span>|  
|`COR_PRF_GC_OTHER`|<span data-ttu-id="a5e99-109">Důvodem neurčená.</span><span class="sxs-lookup"><span data-stu-id="a5e99-109">The reason is unspecified.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a5e99-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a5e99-110">Requirements</span></span>  
 <span data-ttu-id="a5e99-111">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a5e99-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a5e99-112">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a5e99-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a5e99-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a5e99-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a5e99-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a5e99-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5e99-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="a5e99-115">See Also</span></span>  
 [<span data-ttu-id="a5e99-116">Výčty pro profilaci</span><span class="sxs-lookup"><span data-stu-id="a5e99-116">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
