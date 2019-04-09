---
title: COR_PRF_RUNTIME_TYPE – výčet
ms.date: 03/30/2017
api_name:
- COR_PRF_RUNTIME_TYPE Enumeration
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_RUNTIME_TYPE
helpviewer_keywords:
- COR_PRF_RUNTIME_TYPE enumeration [.NET Framework profiling]
ms.assetid: 35449514-333f-4918-9c60-7aa198d655d2
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e57c622780f0bc92061fd2928ea861f904d9eb37
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59122106"
---
# <a name="corprfruntimetype-enumeration"></a><span data-ttu-id="ce89b-102">COR_PRF_RUNTIME_TYPE – výčet</span><span class="sxs-lookup"><span data-stu-id="ce89b-102">COR_PRF_RUNTIME_TYPE Enumeration</span></span>
<span data-ttu-id="ce89b-103">Obsahuje hodnoty, které označují verzi modulu common language runtime (CLR): plochy nebo CoreCLR, který se používá v programu Silverlight.</span><span class="sxs-lookup"><span data-stu-id="ce89b-103">Contains values that indicate the version of the common language runtime (CLR): desktop or CoreCLR, which is used in Silverlight.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ce89b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ce89b-104">Syntax</span></span>  
  
```  
typedef enum  
{  
    COR_PRF_DESKTOP_CLR = 0x1,  
    COR_PRF_CORE_CLR    = 0x2,  
} COR_PRF_RUNTIME_TYPE;  
```  
  
## <a name="members"></a><span data-ttu-id="ce89b-105">Členové</span><span class="sxs-lookup"><span data-stu-id="ce89b-105">Members</span></span>  
  
|<span data-ttu-id="ce89b-106">Člen</span><span class="sxs-lookup"><span data-stu-id="ce89b-106">Member</span></span>|<span data-ttu-id="ce89b-107">Popis</span><span class="sxs-lookup"><span data-stu-id="ce89b-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_DESKTOP_CLR`|<span data-ttu-id="ce89b-108">Desktopová verze modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="ce89b-108">The desktop version of the CLR.</span></span>|  
|`COR_PRF_CORE_CLR`|<span data-ttu-id="ce89b-109">Základní verzi modulu CLR, použít v programu Silverlight.</span><span class="sxs-lookup"><span data-stu-id="ce89b-109">The core version of the CLR, used in Silverlight.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ce89b-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ce89b-110">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ce89b-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ce89b-111">Requirements</span></span>  
 <span data-ttu-id="ce89b-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ce89b-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ce89b-113">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ce89b-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ce89b-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ce89b-114">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="ce89b-115">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="ce89b-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="ce89b-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ce89b-116">See also</span></span>

- [<span data-ttu-id="ce89b-117">Profilace výčtů</span><span class="sxs-lookup"><span data-stu-id="ce89b-117">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
