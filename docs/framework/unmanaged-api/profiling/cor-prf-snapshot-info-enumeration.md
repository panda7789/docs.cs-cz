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
ms.openlocfilehash: 6168c5b27868a261871b292e17ca02b04ae89917
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500777"
---
# <a name="cor_prf_snapshot_info-enumeration"></a><span data-ttu-id="17e55-102">COR_PRF_SNAPSHOT_INFO – výčet</span><span class="sxs-lookup"><span data-stu-id="17e55-102">COR_PRF_SNAPSHOT_INFO Enumeration</span></span>
<span data-ttu-id="17e55-103">Určuje, kolik dat se má zpětně předat snímku zásobníku v každém volání funkce [StackSnapshotCallback –](stacksnapshotcallback-function.md) profileru.</span><span class="sxs-lookup"><span data-stu-id="17e55-103">Specifies how much data to pass back with a stack snapshot in each call to the profiler's [StackSnapshotCallback](stacksnapshotcallback-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="17e55-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="17e55-104">Syntax</span></span>  
  
```cpp  
typedef enum _COR_PRF_SNAPSHOT_INFO {  
    COR_PRF_SNAPSHOT_DEFAULT = 0x0,  
    COR_PRF_SNAPSHOT_REGISTER_CONTEXT = 0x1,  
    COR_PRF_SNAPSHOT_X86_OPTIMIZED = 0X2  
} COR_PRF_SNAPSHOT_INFO;  
```  
  
## <a name="members"></a><span data-ttu-id="17e55-105">Členové</span><span class="sxs-lookup"><span data-stu-id="17e55-105">Members</span></span>  
  
|<span data-ttu-id="17e55-106">Členové</span><span class="sxs-lookup"><span data-stu-id="17e55-106">Members</span></span>|<span data-ttu-id="17e55-107">Description</span><span class="sxs-lookup"><span data-stu-id="17e55-107">Description</span></span>|  
|-------------|-----------------|  
|`COR_PRF_SNAPSHOT_DEFAULT`|<span data-ttu-id="17e55-108">Určuje, že hodnoty musí být předány pro všechny `StackSnapshotCallback` parametry s výjimkou `context` parametru.</span><span class="sxs-lookup"><span data-stu-id="17e55-108">Indicates that values must be passed for all `StackSnapshotCallback` parameters, except the `context` parameter.</span></span>|  
|`COR_PRF_SNAPSHOT_REGISTER_CONTEXT`|<span data-ttu-id="17e55-109">Určuje, že hodnoty musí být předány pro všechny `StackSnapshotCallback` parametry, včetně `context` parametru.</span><span class="sxs-lookup"><span data-stu-id="17e55-109">Indicates that values must be passed for all `StackSnapshotCallback` parameters, including the `context` parameter.</span></span>|  
|`COR_PRF_SNAPSHOT_X86_OPTIMIZED`|<span data-ttu-id="17e55-110">Indikuje, že se použije jednodušší algoritmus procházení zásobníku.</span><span class="sxs-lookup"><span data-stu-id="17e55-110">Indicates that a simpler, alternative stack-walking algorithm will be used.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="17e55-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="17e55-111">Remarks</span></span>  
 <span data-ttu-id="17e55-112">Hodnoty, které jsou poskytovány `COR_PRF_SNAPSHOT_INFO` výčtem, jsou předány jako parametry do metody [DoStackSnapshot –](icorprofilerinfo2-dostacksnapshot-method.md) .</span><span class="sxs-lookup"><span data-stu-id="17e55-112">Values that are provided by the `COR_PRF_SNAPSHOT_INFO` enumeration are passed as parameters to the [DoStackSnapshot](icorprofilerinfo2-dostacksnapshot-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="17e55-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="17e55-113">Requirements</span></span>  
 <span data-ttu-id="17e55-114">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="17e55-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="17e55-115">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="17e55-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="17e55-116">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="17e55-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="17e55-117">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="17e55-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17e55-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="17e55-118">See also</span></span>

- [<span data-ttu-id="17e55-119">DoStackSnapshot – metoda</span><span class="sxs-lookup"><span data-stu-id="17e55-119">DoStackSnapshot Method</span></span>](icorprofilerinfo2-dostacksnapshot-method.md)
- [<span data-ttu-id="17e55-120">Výčty pro profilaci</span><span class="sxs-lookup"><span data-stu-id="17e55-120">Profiling Enumerations</span></span>](profiling-enumerations.md)
