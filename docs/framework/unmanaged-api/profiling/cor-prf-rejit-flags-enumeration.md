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
ms.openlocfilehash: 8fc5f1a488826d8adc6aecb8ef122609bebbe813
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177103"
---
# <a name="cor_prf_rejit_flags-enumeration"></a><span data-ttu-id="c6369-102">COR_PRF_REJIT_FLAGS – výčet</span><span class="sxs-lookup"><span data-stu-id="c6369-102">COR_PRF_REJIT_FLAGS Enumeration</span></span>
<span data-ttu-id="c6369-103">Obsahuje hodnoty, které označují, jak by se mělo chovat rozhraní API [ICorProfilerInfo10::RequestReJITWithInliners.](icorprofilerinfo10-requestrejitwithinliners-method.md)</span><span class="sxs-lookup"><span data-stu-id="c6369-103">Contains values that indicate how the [ICorProfilerInfo10::RequestReJITWithInliners](icorprofilerinfo10-requestrejitwithinliners-method.md) API should behave.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c6369-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c6369-104">Syntax</span></span>  
  
```cpp  
typedef enum  
{
    COR_PRF_REJIT_BLOCK_INLINING = 0x1,
    COR_PRF_REJIT_INLINING_CALLBACKS    = 0x2
} COR_PRF_REJIT_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="c6369-105">Členové</span><span class="sxs-lookup"><span data-stu-id="c6369-105">Members</span></span>  
  
|<span data-ttu-id="c6369-106">Člen</span><span class="sxs-lookup"><span data-stu-id="c6369-106">Member</span></span>|<span data-ttu-id="c6369-107">Popis</span><span class="sxs-lookup"><span data-stu-id="c6369-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_REJIT_BLOCK_INLINING`| <span data-ttu-id="c6369-108">ReJITted metody budou blokovány v zařadit do jiných metod.</span><span class="sxs-lookup"><span data-stu-id="c6369-108">ReJITted methods will be blocked from being inlined in other methods.</span></span> |  
|`COR_PRF_REJIT_INLINING_CALLBACKS`| <span data-ttu-id="c6369-109">Příjem `GetFunctionParameters` zpětná volání pro všechny metody, které vinárně metody požadované reJITted.</span><span class="sxs-lookup"><span data-stu-id="c6369-109">Receive `GetFunctionParameters` callbacks for any methods that inline the methods requested to be ReJITted.</span></span> |  

## <a name="requirements"></a><span data-ttu-id="c6369-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c6369-110">Requirements</span></span>  
 <span data-ttu-id="c6369-111">**Platformy:** Viz [operační systémy podporované rozhraním .NET Core](../../../core/install/dependencies.md?pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="c6369-111">**Platforms:** See [.NET Core supported operating systems](../../../core/install/dependencies.md?pivots=os-windows).</span></span>  
  
 <span data-ttu-id="c6369-112">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="c6369-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c6369-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c6369-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c6369-114">**Verze rozhraní .NET Framework:**[!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c6369-114">**.NET Framework Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]</span></span>
  
## <a name="see-also"></a><span data-ttu-id="c6369-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="c6369-115">See also</span></span>

- [<span data-ttu-id="c6369-116">Výčty pro profilaci</span><span class="sxs-lookup"><span data-stu-id="c6369-116">Profiling Enumerations</span></span>](profiling-enumerations.md)
