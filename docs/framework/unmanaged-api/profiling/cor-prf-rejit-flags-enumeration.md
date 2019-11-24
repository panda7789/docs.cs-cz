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
ms.openlocfilehash: 66933b3778807b40f1d39d8b4c565c334328812f
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74450398"
---
# <a name="cor_prf_rejit_flags-enumeration"></a><span data-ttu-id="467b5-102">COR_PRF_REJIT_FLAGS – výčet</span><span class="sxs-lookup"><span data-stu-id="467b5-102">COR_PRF_REJIT_FLAGS Enumeration</span></span>
<span data-ttu-id="467b5-103">Contains values that indicate how the [ICorProfilerInfo10::RequestReJITWithInliners](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-requestrejitwithinliners-method.md) API should behave.</span><span class="sxs-lookup"><span data-stu-id="467b5-103">Contains values that indicate how the [ICorProfilerInfo10::RequestReJITWithInliners](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-requestrejitwithinliners-method.md) API should behave.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="467b5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="467b5-104">Syntax</span></span>  
  
```cpp  
typedef enum  
{      
    COR_PRF_REJIT_BLOCK_INLINING = 0x1,
    COR_PRF_REJIT_INLINING_CALLBACKS    = 0x2
} COR_PRF_REJIT_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="467b5-105">Členové</span><span class="sxs-lookup"><span data-stu-id="467b5-105">Members</span></span>  
  
|<span data-ttu-id="467b5-106">Člen</span><span class="sxs-lookup"><span data-stu-id="467b5-106">Member</span></span>|<span data-ttu-id="467b5-107">Popis</span><span class="sxs-lookup"><span data-stu-id="467b5-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_REJIT_BLOCK_INLINING`| <span data-ttu-id="467b5-108">ReJITted methods will be blocked from being inlined in other methods.</span><span class="sxs-lookup"><span data-stu-id="467b5-108">ReJITted methods will be blocked from being inlined in other methods.</span></span> |  
|`COR_PRF_REJIT_INLINING_CALLBACKS`| <span data-ttu-id="467b5-109">Receive `GetFunctionParameters` callbacks for any methods that inline the methods requested to be ReJITted.</span><span class="sxs-lookup"><span data-stu-id="467b5-109">Receive `GetFunctionParameters` callbacks for any methods that inline the methods requested to be ReJITted.</span></span> |  

## <a name="requirements"></a><span data-ttu-id="467b5-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="467b5-110">Requirements</span></span>  
 <span data-ttu-id="467b5-111">**Platforms:** See [.NET Core supported operating systems](../../../core/install/dependencies.md?tabs=netcore30&pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="467b5-111">**Platforms:** See [.NET Core supported operating systems](../../../core/install/dependencies.md?tabs=netcore30&pivots=os-windows).</span></span>  
  
 <span data-ttu-id="467b5-112">**Header:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="467b5-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="467b5-113">**Library:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="467b5-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="467b5-114">**.NET Framework Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]</span><span class="sxs-lookup"><span data-stu-id="467b5-114">**.NET Framework Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]</span></span> 
  
## <a name="see-also"></a><span data-ttu-id="467b5-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="467b5-115">See also</span></span>

- [<span data-ttu-id="467b5-116">Výčty pro profilaci</span><span class="sxs-lookup"><span data-stu-id="467b5-116">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
