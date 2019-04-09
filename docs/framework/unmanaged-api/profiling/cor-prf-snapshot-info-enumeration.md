---
title: COR_PRF_SNAPSHOT_INFO – výčet
ms.date: 03/30/2017
api_name:
- COR_PRF_SNAPSHOT_INFO
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_SNAPSHOT_INFO
helpviewer_keywords:
- COR_PRF_SNAPSHOT_INFO enumeration [.NET Framework profiling]
ms.assetid: a5906b2a-ad4a-4cc6-a421-2d7d8adf7468
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: fa85fb2cebb47ecbd7b0f091cb79f6ea0936b1cb
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59177837"
---
# <a name="corprfsnapshotinfo-enumeration"></a><span data-ttu-id="74a9b-102">COR_PRF_SNAPSHOT_INFO – výčet</span><span class="sxs-lookup"><span data-stu-id="74a9b-102">COR_PRF_SNAPSHOT_INFO Enumeration</span></span>
<span data-ttu-id="74a9b-103">Určuje, kolik předání dat zpět se snímek zásobníku v každé volání profileru [stacksnapshotcallback –](../../../../docs/framework/unmanaged-api/profiling/stacksnapshotcallback-function.md) funkce.</span><span class="sxs-lookup"><span data-stu-id="74a9b-103">Specifies how much data to pass back with a stack snapshot in each call to the profiler's [StackSnapshotCallback](../../../../docs/framework/unmanaged-api/profiling/stacksnapshotcallback-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="74a9b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="74a9b-104">Syntax</span></span>  
  
```  
typedef enum _COR_PRF_SNAPSHOT_INFO {  
    COR_PRF_SNAPSHOT_DEFAULT = 0x0,  
    COR_PRF_SNAPSHOT_REGISTER_CONTEXT = 0x1,  
    COR_PRF_SNAPSHOT_X86_OPTIMIZED = 0X2  
} COR_PRF_SNAPSHOT_INFO;  
```  
  
## <a name="members"></a><span data-ttu-id="74a9b-105">Členové</span><span class="sxs-lookup"><span data-stu-id="74a9b-105">Members</span></span>  
  
|<span data-ttu-id="74a9b-106">Členové</span><span class="sxs-lookup"><span data-stu-id="74a9b-106">Members</span></span>|<span data-ttu-id="74a9b-107">Popis</span><span class="sxs-lookup"><span data-stu-id="74a9b-107">Description</span></span>|  
|-------------|-----------------|  
|`COR_PRF_SNAPSHOT_DEFAULT`|<span data-ttu-id="74a9b-108">Označuje, že hodnoty musí být předán pro všechny `StackSnapshotCallback` parametrů, s výjimkou `context` parametru.</span><span class="sxs-lookup"><span data-stu-id="74a9b-108">Indicates that values must be passed for all `StackSnapshotCallback` parameters, except the `context` parameter.</span></span>|  
|`COR_PRF_SNAPSHOT_REGISTER_CONTEXT`|<span data-ttu-id="74a9b-109">Označuje, že hodnoty musí být předán pro všechny `StackSnapshotCallback` parametry, včetně `context` parametru.</span><span class="sxs-lookup"><span data-stu-id="74a9b-109">Indicates that values must be passed for all `StackSnapshotCallback` parameters, including the `context` parameter.</span></span>|  
|`COR_PRF_SNAPSHOT_X86_OPTIMIZED`|<span data-ttu-id="74a9b-110">Označuje, že se použije jednodušší a alternativní algoritmus procházení zásobníku.</span><span class="sxs-lookup"><span data-stu-id="74a9b-110">Indicates that a simpler, alternative stack-walking algorithm will be used.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="74a9b-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="74a9b-111">Remarks</span></span>  
 <span data-ttu-id="74a9b-112">Hodnoty, které jsou k dispozici v `COR_PRF_SNAPSHOT_INFO` výčtu jsou předány jako parametry [dostacksnapshot –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="74a9b-112">Values that are provided by the `COR_PRF_SNAPSHOT_INFO` enumeration are passed as parameters to the [DoStackSnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="74a9b-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="74a9b-113">Requirements</span></span>  
 <span data-ttu-id="74a9b-114">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="74a9b-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="74a9b-115">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="74a9b-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="74a9b-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="74a9b-116">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="74a9b-117">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="74a9b-117">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="74a9b-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="74a9b-118">See also</span></span>

- [<span data-ttu-id="74a9b-119">DoStackSnapshot – metoda</span><span class="sxs-lookup"><span data-stu-id="74a9b-119">DoStackSnapshot Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md)
- [<span data-ttu-id="74a9b-120">Profilace výčtů</span><span class="sxs-lookup"><span data-stu-id="74a9b-120">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
