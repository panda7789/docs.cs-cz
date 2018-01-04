---
title: "COR_PRF_RUNTIME_TYPE – výčet"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COR_PRF_RUNTIME_TYPE Enumeration
api_location: mscorwks.dll
api_type: COM
f1_keywords: COR_PRF_RUNTIME_TYPE
helpviewer_keywords: COR_PRF_RUNTIME_TYPE enumeration [.NET Framework profiling]
ms.assetid: 35449514-333f-4918-9c60-7aa198d655d2
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 154773e76046656e4286f4ba12717b6b45e9b069
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="corprfruntimetype-enumeration"></a><span data-ttu-id="e1de7-102">COR_PRF_RUNTIME_TYPE – výčet</span><span class="sxs-lookup"><span data-stu-id="e1de7-102">COR_PRF_RUNTIME_TYPE Enumeration</span></span>
<span data-ttu-id="e1de7-103">Obsahuje hodnoty, které označují verzí common language runtime (CLR): plocha nebo CoreCLR, který se používá v programu Silverlight.</span><span class="sxs-lookup"><span data-stu-id="e1de7-103">Contains values that indicate the version of the common language runtime (CLR): desktop or CoreCLR, which is used in Silverlight.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e1de7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e1de7-104">Syntax</span></span>  
  
```  
typedef enum  
{  
    COR_PRF_DESKTOP_CLR = 0x1,  
    COR_PRF_CORE_CLR    = 0x2,  
} COR_PRF_RUNTIME_TYPE;  
```  
  
## <a name="members"></a><span data-ttu-id="e1de7-105">Členové</span><span class="sxs-lookup"><span data-stu-id="e1de7-105">Members</span></span>  
  
|<span data-ttu-id="e1de7-106">Člen</span><span class="sxs-lookup"><span data-stu-id="e1de7-106">Member</span></span>|<span data-ttu-id="e1de7-107">Popis</span><span class="sxs-lookup"><span data-stu-id="e1de7-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_DESKTOP_CLR`|<span data-ttu-id="e1de7-108">Plochy verzi modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="e1de7-108">The desktop version of the CLR.</span></span>|  
|`COR_PRF_CORE_CLR`|<span data-ttu-id="e1de7-109">Základní verzi modulu CLR, použít v programu Silverlight.</span><span class="sxs-lookup"><span data-stu-id="e1de7-109">The core version of the CLR, used in Silverlight.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e1de7-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e1de7-110">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e1de7-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e1de7-111">Requirements</span></span>  
 <span data-ttu-id="e1de7-112">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e1de7-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e1de7-113">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="e1de7-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e1de7-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e1de7-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e1de7-115">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e1de7-115">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1de7-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="e1de7-116">See Also</span></span>  
 [<span data-ttu-id="e1de7-117">Výčty pro profilaci</span><span class="sxs-lookup"><span data-stu-id="e1de7-117">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
