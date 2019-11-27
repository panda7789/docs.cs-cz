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
ms.openlocfilehash: 6ade4f7877e39a8307a36f3a3268f79e8b4d44fd
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74427266"
---
# <a name="cor_prf_snapshot_info-enumeration"></a><span data-ttu-id="8fe30-102">COR_PRF_SNAPSHOT_INFO – výčet</span><span class="sxs-lookup"><span data-stu-id="8fe30-102">COR_PRF_SNAPSHOT_INFO Enumeration</span></span>
<span data-ttu-id="8fe30-103">Určuje, kolik dat se má zpětně předat snímku zásobníku v každém volání funkce [StackSnapshotCallback –](../../../../docs/framework/unmanaged-api/profiling/stacksnapshotcallback-function.md) profileru.</span><span class="sxs-lookup"><span data-stu-id="8fe30-103">Specifies how much data to pass back with a stack snapshot in each call to the profiler's [StackSnapshotCallback](../../../../docs/framework/unmanaged-api/profiling/stacksnapshotcallback-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8fe30-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8fe30-104">Syntax</span></span>  
  
```cpp  
typedef enum _COR_PRF_SNAPSHOT_INFO {  
    COR_PRF_SNAPSHOT_DEFAULT = 0x0,  
    COR_PRF_SNAPSHOT_REGISTER_CONTEXT = 0x1,  
    COR_PRF_SNAPSHOT_X86_OPTIMIZED = 0X2  
} COR_PRF_SNAPSHOT_INFO;  
```  
  
## <a name="members"></a><span data-ttu-id="8fe30-105">Členové</span><span class="sxs-lookup"><span data-stu-id="8fe30-105">Members</span></span>  
  
|<span data-ttu-id="8fe30-106">Členové</span><span class="sxs-lookup"><span data-stu-id="8fe30-106">Members</span></span>|<span data-ttu-id="8fe30-107">Popis</span><span class="sxs-lookup"><span data-stu-id="8fe30-107">Description</span></span>|  
|-------------|-----------------|  
|`COR_PRF_SNAPSHOT_DEFAULT`|<span data-ttu-id="8fe30-108">Určuje, že hodnoty musí být předány pro všechny parametry `StackSnapshotCallback` s výjimkou parametru `context`.</span><span class="sxs-lookup"><span data-stu-id="8fe30-108">Indicates that values must be passed for all `StackSnapshotCallback` parameters, except the `context` parameter.</span></span>|  
|`COR_PRF_SNAPSHOT_REGISTER_CONTEXT`|<span data-ttu-id="8fe30-109">Určuje, že hodnoty musí být předány pro všechny parametry `StackSnapshotCallback`, včetně parametru `context`.</span><span class="sxs-lookup"><span data-stu-id="8fe30-109">Indicates that values must be passed for all `StackSnapshotCallback` parameters, including the `context` parameter.</span></span>|  
|`COR_PRF_SNAPSHOT_X86_OPTIMIZED`|<span data-ttu-id="8fe30-110">Indikuje, že se použije jednodušší algoritmus procházení zásobníku.</span><span class="sxs-lookup"><span data-stu-id="8fe30-110">Indicates that a simpler, alternative stack-walking algorithm will be used.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8fe30-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8fe30-111">Remarks</span></span>  
 <span data-ttu-id="8fe30-112">Hodnoty, které jsou poskytovány výčtem `COR_PRF_SNAPSHOT_INFO`, jsou předány jako parametry do metody [DoStackSnapshot –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) .</span><span class="sxs-lookup"><span data-stu-id="8fe30-112">Values that are provided by the `COR_PRF_SNAPSHOT_INFO` enumeration are passed as parameters to the [DoStackSnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8fe30-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8fe30-113">Requirements</span></span>  
 <span data-ttu-id="8fe30-114">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8fe30-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8fe30-115">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="8fe30-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="8fe30-116">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="8fe30-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8fe30-117">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8fe30-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8fe30-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8fe30-118">See also</span></span>

- [<span data-ttu-id="8fe30-119">DoStackSnapshot – metoda</span><span class="sxs-lookup"><span data-stu-id="8fe30-119">DoStackSnapshot Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md)
- [<span data-ttu-id="8fe30-120">Výčty pro profilaci</span><span class="sxs-lookup"><span data-stu-id="8fe30-120">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
