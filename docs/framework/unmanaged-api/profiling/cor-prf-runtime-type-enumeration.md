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
ms.openlocfilehash: c1767e718e597918ef59b72a4b7acc3589421de0
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76867052"
---
# <a name="cor_prf_runtime_type-enumeration"></a><span data-ttu-id="40638-102">COR_PRF_RUNTIME_TYPE – výčet</span><span class="sxs-lookup"><span data-stu-id="40638-102">COR_PRF_RUNTIME_TYPE Enumeration</span></span>
<span data-ttu-id="40638-103">Obsahuje hodnoty, které označují verzi modulu CLR (Common Language Runtime): Desktop nebo CoreCLR, který se používá v programu Silverlight.</span><span class="sxs-lookup"><span data-stu-id="40638-103">Contains values that indicate the version of the common language runtime (CLR): desktop or CoreCLR, which is used in Silverlight.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="40638-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="40638-104">Syntax</span></span>  
  
```cpp  
typedef enum  
{  
    COR_PRF_DESKTOP_CLR = 0x1,  
    COR_PRF_CORE_CLR    = 0x2,  
} COR_PRF_RUNTIME_TYPE;  
```  
  
## <a name="members"></a><span data-ttu-id="40638-105">Členové</span><span class="sxs-lookup"><span data-stu-id="40638-105">Members</span></span>  
  
|<span data-ttu-id="40638-106">Člen</span><span class="sxs-lookup"><span data-stu-id="40638-106">Member</span></span>|<span data-ttu-id="40638-107">Popis</span><span class="sxs-lookup"><span data-stu-id="40638-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_DESKTOP_CLR`|<span data-ttu-id="40638-108">Verze modulu CLR aplikace Desktop.</span><span class="sxs-lookup"><span data-stu-id="40638-108">The desktop version of the CLR.</span></span>|  
|`COR_PRF_CORE_CLR`|<span data-ttu-id="40638-109">Základní verze modulu CLR, používaná v programu Silverlight.</span><span class="sxs-lookup"><span data-stu-id="40638-109">The core version of the CLR, used in Silverlight.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="40638-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="40638-110">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="40638-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="40638-111">Requirements</span></span>  
 <span data-ttu-id="40638-112">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="40638-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="40638-113">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="40638-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="40638-114">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="40638-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="40638-115">**Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="40638-115">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40638-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="40638-116">See also</span></span>

- [<span data-ttu-id="40638-117">Výčty pro profilaci</span><span class="sxs-lookup"><span data-stu-id="40638-117">Profiling Enumerations</span></span>](profiling-enumerations.md)
