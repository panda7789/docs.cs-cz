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
ms.openlocfilehash: 9d6713a7f54f6a6d8dbf261ad45304e6ddbe24c0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33450714"
---
# <a name="corprfsnapshotinfo-enumeration"></a><span data-ttu-id="c79f1-102">COR_PRF_SNAPSHOT_INFO – výčet</span><span class="sxs-lookup"><span data-stu-id="c79f1-102">COR_PRF_SNAPSHOT_INFO Enumeration</span></span>
<span data-ttu-id="c79f1-103">Určuje, kolik předání dat zpět snímkem zásobníku při každém volání do okna profilování [stacksnapshotcallback –](../../../../docs/framework/unmanaged-api/profiling/stacksnapshotcallback-function.md) funkce.</span><span class="sxs-lookup"><span data-stu-id="c79f1-103">Specifies how much data to pass back with a stack snapshot in each call to the profiler's [StackSnapshotCallback](../../../../docs/framework/unmanaged-api/profiling/stacksnapshotcallback-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c79f1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c79f1-104">Syntax</span></span>  
  
```  
typedef enum _COR_PRF_SNAPSHOT_INFO {  
    COR_PRF_SNAPSHOT_DEFAULT = 0x0,  
    COR_PRF_SNAPSHOT_REGISTER_CONTEXT = 0x1,  
    COR_PRF_SNAPSHOT_X86_OPTIMIZED = 0X2  
} COR_PRF_SNAPSHOT_INFO;  
```  
  
## <a name="members"></a><span data-ttu-id="c79f1-105">Členové</span><span class="sxs-lookup"><span data-stu-id="c79f1-105">Members</span></span>  
  
|<span data-ttu-id="c79f1-106">Členové</span><span class="sxs-lookup"><span data-stu-id="c79f1-106">Members</span></span>|<span data-ttu-id="c79f1-107">Popis</span><span class="sxs-lookup"><span data-stu-id="c79f1-107">Description</span></span>|  
|-------------|-----------------|  
|`COR_PRF_SNAPSHOT_DEFAULT`|<span data-ttu-id="c79f1-108">Označuje, že hodnoty musí být předána pro všechny `StackSnapshotCallback` parametrů, s výjimkou `context` parametr.</span><span class="sxs-lookup"><span data-stu-id="c79f1-108">Indicates that values must be passed for all `StackSnapshotCallback` parameters, except the `context` parameter.</span></span>|  
|`COR_PRF_SNAPSHOT_REGISTER_CONTEXT`|<span data-ttu-id="c79f1-109">Označuje, že hodnoty musí být předána pro všechny `StackSnapshotCallback` parametry, včetně `context` parametr.</span><span class="sxs-lookup"><span data-stu-id="c79f1-109">Indicates that values must be passed for all `StackSnapshotCallback` parameters, including the `context` parameter.</span></span>|  
|`COR_PRF_SNAPSHOT_X86_OPTIMIZED`|<span data-ttu-id="c79f1-110">Označuje, že jednodušší, alternativní algoritmus procházení zásobníku se použije.</span><span class="sxs-lookup"><span data-stu-id="c79f1-110">Indicates that a simpler, alternative stack-walking algorithm will be used.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c79f1-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c79f1-111">Remarks</span></span>  
 <span data-ttu-id="c79f1-112">Hodnoty, které jsou poskytovány `COR_PRF_SNAPSHOT_INFO` výčtu jsou předány jako parametry, které [dostacksnapshot –](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="c79f1-112">Values that are provided by the `COR_PRF_SNAPSHOT_INFO` enumeration are passed as parameters to the [DoStackSnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c79f1-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c79f1-113">Requirements</span></span>  
 <span data-ttu-id="c79f1-114">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c79f1-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c79f1-115">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="c79f1-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c79f1-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c79f1-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c79f1-117">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c79f1-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c79f1-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="c79f1-118">See Also</span></span>  
 [<span data-ttu-id="c79f1-119">DoStackSnapshot – metoda</span><span class="sxs-lookup"><span data-stu-id="c79f1-119">DoStackSnapshot Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md)  
 [<span data-ttu-id="c79f1-120">Výčty pro profilaci</span><span class="sxs-lookup"><span data-stu-id="c79f1-120">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
