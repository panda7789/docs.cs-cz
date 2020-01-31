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
ms.openlocfilehash: fabbcd497dc2f321da90188cebbac6ed4e147492
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76867084"
---
# <a name="cor_prf_rejit_flags-enumeration"></a><span data-ttu-id="46a3f-102">COR_PRF_REJIT_FLAGS – výčet</span><span class="sxs-lookup"><span data-stu-id="46a3f-102">COR_PRF_REJIT_FLAGS Enumeration</span></span>
<span data-ttu-id="46a3f-103">Obsahuje hodnoty, které určují, jak by se mělo chovat rozhraní API [ICorProfilerInfo10:: RequestReJITWithInliners](icorprofilerinfo10-requestrejitwithinliners-method.md) .</span><span class="sxs-lookup"><span data-stu-id="46a3f-103">Contains values that indicate how the [ICorProfilerInfo10::RequestReJITWithInliners](icorprofilerinfo10-requestrejitwithinliners-method.md) API should behave.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="46a3f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="46a3f-104">Syntax</span></span>  
  
```cpp  
typedef enum  
{      
    COR_PRF_REJIT_BLOCK_INLINING = 0x1,
    COR_PRF_REJIT_INLINING_CALLBACKS    = 0x2
} COR_PRF_REJIT_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="46a3f-105">Členové</span><span class="sxs-lookup"><span data-stu-id="46a3f-105">Members</span></span>  
  
|<span data-ttu-id="46a3f-106">Člen</span><span class="sxs-lookup"><span data-stu-id="46a3f-106">Member</span></span>|<span data-ttu-id="46a3f-107">Popis</span><span class="sxs-lookup"><span data-stu-id="46a3f-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_REJIT_BLOCK_INLINING`| <span data-ttu-id="46a3f-108">Metody ReJITted budou zablokovány, aby byly vloženy do jiných metod.</span><span class="sxs-lookup"><span data-stu-id="46a3f-108">ReJITted methods will be blocked from being inlined in other methods.</span></span> |  
|`COR_PRF_REJIT_INLINING_CALLBACKS`| <span data-ttu-id="46a3f-109">Dostanou zpětná volání `GetFunctionParameters` pro všechny metody, které vloží metody požadované k ReJITted.</span><span class="sxs-lookup"><span data-stu-id="46a3f-109">Receive `GetFunctionParameters` callbacks for any methods that inline the methods requested to be ReJITted.</span></span> |  

## <a name="requirements"></a><span data-ttu-id="46a3f-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="46a3f-110">Requirements</span></span>  
 <span data-ttu-id="46a3f-111">**Platformy:** Viz [podporované operační systémy .NET Core](../../../core/install/dependencies.md?tabs=netcore30&pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="46a3f-111">**Platforms:** See [.NET Core supported operating systems](../../../core/install/dependencies.md?tabs=netcore30&pivots=os-windows).</span></span>  
  
 <span data-ttu-id="46a3f-112">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="46a3f-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="46a3f-113">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="46a3f-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="46a3f-114">**Verze .NET Framework:** [!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]</span><span class="sxs-lookup"><span data-stu-id="46a3f-114">**.NET Framework Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]</span></span> 
  
## <a name="see-also"></a><span data-ttu-id="46a3f-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="46a3f-115">See also</span></span>

- [<span data-ttu-id="46a3f-116">Výčty pro profilaci</span><span class="sxs-lookup"><span data-stu-id="46a3f-116">Profiling Enumerations</span></span>](profiling-enumerations.md)
