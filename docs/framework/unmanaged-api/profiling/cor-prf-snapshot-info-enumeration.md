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
ms.openlocfilehash: 97bf3e69a8ea155d53479ba6f61988e56e3bd396
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76867019"
---
# <a name="cor_prf_snapshot_info-enumeration"></a><span data-ttu-id="9966e-102">COR_PRF_SNAPSHOT_INFO – výčet</span><span class="sxs-lookup"><span data-stu-id="9966e-102">COR_PRF_SNAPSHOT_INFO Enumeration</span></span>
<span data-ttu-id="9966e-103">Určuje, kolik dat se má zpětně předat snímku zásobníku v každém volání funkce [StackSnapshotCallback –](stacksnapshotcallback-function.md) profileru.</span><span class="sxs-lookup"><span data-stu-id="9966e-103">Specifies how much data to pass back with a stack snapshot in each call to the profiler's [StackSnapshotCallback](stacksnapshotcallback-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9966e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9966e-104">Syntax</span></span>  
  
```cpp  
typedef enum _COR_PRF_SNAPSHOT_INFO {  
    COR_PRF_SNAPSHOT_DEFAULT = 0x0,  
    COR_PRF_SNAPSHOT_REGISTER_CONTEXT = 0x1,  
    COR_PRF_SNAPSHOT_X86_OPTIMIZED = 0X2  
} COR_PRF_SNAPSHOT_INFO;  
```  
  
## <a name="members"></a><span data-ttu-id="9966e-105">Členové</span><span class="sxs-lookup"><span data-stu-id="9966e-105">Members</span></span>  
  
|<span data-ttu-id="9966e-106">Členové</span><span class="sxs-lookup"><span data-stu-id="9966e-106">Members</span></span>|<span data-ttu-id="9966e-107">Popis</span><span class="sxs-lookup"><span data-stu-id="9966e-107">Description</span></span>|  
|-------------|-----------------|  
|`COR_PRF_SNAPSHOT_DEFAULT`|<span data-ttu-id="9966e-108">Určuje, že hodnoty musí být předány pro všechny parametry `StackSnapshotCallback` s výjimkou parametru `context`.</span><span class="sxs-lookup"><span data-stu-id="9966e-108">Indicates that values must be passed for all `StackSnapshotCallback` parameters, except the `context` parameter.</span></span>|  
|`COR_PRF_SNAPSHOT_REGISTER_CONTEXT`|<span data-ttu-id="9966e-109">Určuje, že hodnoty musí být předány pro všechny parametry `StackSnapshotCallback`, včetně parametru `context`.</span><span class="sxs-lookup"><span data-stu-id="9966e-109">Indicates that values must be passed for all `StackSnapshotCallback` parameters, including the `context` parameter.</span></span>|  
|`COR_PRF_SNAPSHOT_X86_OPTIMIZED`|<span data-ttu-id="9966e-110">Indikuje, že se použije jednodušší algoritmus procházení zásobníku.</span><span class="sxs-lookup"><span data-stu-id="9966e-110">Indicates that a simpler, alternative stack-walking algorithm will be used.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9966e-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9966e-111">Remarks</span></span>  
 <span data-ttu-id="9966e-112">Hodnoty, které jsou poskytovány výčtem `COR_PRF_SNAPSHOT_INFO`, jsou předány jako parametry do metody [DoStackSnapshot –](icorprofilerinfo2-dostacksnapshot-method.md) .</span><span class="sxs-lookup"><span data-stu-id="9966e-112">Values that are provided by the `COR_PRF_SNAPSHOT_INFO` enumeration are passed as parameters to the [DoStackSnapshot](icorprofilerinfo2-dostacksnapshot-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9966e-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9966e-113">Requirements</span></span>  
 <span data-ttu-id="9966e-114">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9966e-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9966e-115">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="9966e-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="9966e-116">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="9966e-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9966e-117">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9966e-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9966e-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9966e-118">See also</span></span>

- [<span data-ttu-id="9966e-119">DoStackSnapshot – metoda</span><span class="sxs-lookup"><span data-stu-id="9966e-119">DoStackSnapshot Method</span></span>](icorprofilerinfo2-dostacksnapshot-method.md)
- [<span data-ttu-id="9966e-120">Výčty pro profilaci</span><span class="sxs-lookup"><span data-stu-id="9966e-120">Profiling Enumerations</span></span>](profiling-enumerations.md)
