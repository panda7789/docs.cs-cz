---
title: COR_PRF_REJIT_FLAGS – výčet
ms.date: 08/06/2019
api_name:
- COR_PRF_REJIT_FLAGS Enumeration
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_REJIT_FLAGS
helpviewer_keywords:
- COR_PRF_REJIT_FLAGS enumeration [.NET Framework profiling]
topic_type:
- apiref
author: davmason
ms.author: davmason
ms.openlocfilehash: 3b4f85072b9dcf87d696b979fa6cbf4e59393f82
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/19/2020
ms.locfileid: "77453036"
---
# <a name="cor_prf_rejit_flags-enumeration"></a><span data-ttu-id="c671f-102">COR_PRF_REJIT_FLAGS – výčet</span><span class="sxs-lookup"><span data-stu-id="c671f-102">COR_PRF_REJIT_FLAGS Enumeration</span></span>
<span data-ttu-id="c671f-103">Obsahuje hodnoty, které určují, jak by se mělo chovat rozhraní API [ICorProfilerInfo10:: RequestReJITWithInliners](icorprofilerinfo10-requestrejitwithinliners-method.md) .</span><span class="sxs-lookup"><span data-stu-id="c671f-103">Contains values that indicate how the [ICorProfilerInfo10::RequestReJITWithInliners](icorprofilerinfo10-requestrejitwithinliners-method.md) API should behave.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c671f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c671f-104">Syntax</span></span>  
  
```cpp  
typedef enum  
{      
    COR_PRF_REJIT_BLOCK_INLINING = 0x1,
    COR_PRF_REJIT_INLINING_CALLBACKS    = 0x2
} COR_PRF_REJIT_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="c671f-105">Členové</span><span class="sxs-lookup"><span data-stu-id="c671f-105">Members</span></span>  
  
|<span data-ttu-id="c671f-106">Člen</span><span class="sxs-lookup"><span data-stu-id="c671f-106">Member</span></span>|<span data-ttu-id="c671f-107">Popis</span><span class="sxs-lookup"><span data-stu-id="c671f-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_REJIT_BLOCK_INLINING`| <span data-ttu-id="c671f-108">Metody ReJITted budou zablokovány, aby byly vloženy do jiných metod.</span><span class="sxs-lookup"><span data-stu-id="c671f-108">ReJITted methods will be blocked from being inlined in other methods.</span></span> |  
|`COR_PRF_REJIT_INLINING_CALLBACKS`| <span data-ttu-id="c671f-109">Dostanou zpětná volání `GetFunctionParameters` pro všechny metody, které vloží metody požadované k ReJITted.</span><span class="sxs-lookup"><span data-stu-id="c671f-109">Receive `GetFunctionParameters` callbacks for any methods that inline the methods requested to be ReJITted.</span></span> |  

## <a name="requirements"></a><span data-ttu-id="c671f-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c671f-110">Requirements</span></span>  
 <span data-ttu-id="c671f-111">**Platformy:** Viz [podporované operační systémy .NET Core](../../../core/install/dependencies.md?pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="c671f-111">**Platforms:** See [.NET Core supported operating systems](../../../core/install/dependencies.md?pivots=os-windows).</span></span>  
  
 <span data-ttu-id="c671f-112">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="c671f-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c671f-113">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="c671f-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c671f-114">**Verze .NET Framework:** [!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c671f-114">**.NET Framework Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]</span></span> 
  
## <a name="see-also"></a><span data-ttu-id="c671f-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="c671f-115">See also</span></span>

- [<span data-ttu-id="c671f-116">Výčty pro profilaci</span><span class="sxs-lookup"><span data-stu-id="c671f-116">Profiling Enumerations</span></span>](profiling-enumerations.md)
