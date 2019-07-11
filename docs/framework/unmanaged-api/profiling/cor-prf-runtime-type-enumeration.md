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
ms.openlocfilehash: 6c52f96ad9458dfd5cdedc5cc73154aa570c6759
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67751961"
---
# <a name="corprfruntimetype-enumeration"></a><span data-ttu-id="14640-102">COR_PRF_RUNTIME_TYPE – výčet</span><span class="sxs-lookup"><span data-stu-id="14640-102">COR_PRF_RUNTIME_TYPE Enumeration</span></span>
<span data-ttu-id="14640-103">Obsahuje hodnoty, které označují verzi modulu common language runtime (CLR): plochy nebo CoreCLR, který se používá v programu Silverlight.</span><span class="sxs-lookup"><span data-stu-id="14640-103">Contains values that indicate the version of the common language runtime (CLR): desktop or CoreCLR, which is used in Silverlight.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="14640-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="14640-104">Syntax</span></span>  
  
```cpp  
typedef enum  
{  
    COR_PRF_DESKTOP_CLR = 0x1,  
    COR_PRF_CORE_CLR    = 0x2,  
} COR_PRF_RUNTIME_TYPE;  
```  
  
## <a name="members"></a><span data-ttu-id="14640-105">Členové</span><span class="sxs-lookup"><span data-stu-id="14640-105">Members</span></span>  
  
|<span data-ttu-id="14640-106">Člen</span><span class="sxs-lookup"><span data-stu-id="14640-106">Member</span></span>|<span data-ttu-id="14640-107">Popis</span><span class="sxs-lookup"><span data-stu-id="14640-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_DESKTOP_CLR`|<span data-ttu-id="14640-108">Desktopová verze modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="14640-108">The desktop version of the CLR.</span></span>|  
|`COR_PRF_CORE_CLR`|<span data-ttu-id="14640-109">Základní verzi modulu CLR, použít v programu Silverlight.</span><span class="sxs-lookup"><span data-stu-id="14640-109">The core version of the CLR, used in Silverlight.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="14640-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="14640-110">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="14640-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="14640-111">Requirements</span></span>  
 <span data-ttu-id="14640-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="14640-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="14640-113">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="14640-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="14640-114">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="14640-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="14640-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="14640-115">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14640-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="14640-116">See also</span></span>

- [<span data-ttu-id="14640-117">Výčty pro profilaci</span><span class="sxs-lookup"><span data-stu-id="14640-117">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
