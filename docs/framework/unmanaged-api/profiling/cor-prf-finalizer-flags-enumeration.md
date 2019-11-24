---
title: COR_PRF_FINALIZER_FLAGS – výčet
ms.date: 03/30/2017
api_name:
- COR_PRF_FINALIZER_FLAGS
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_FINALIZER_FLAGS
helpviewer_keywords:
- COR_PRF_FINALIZER_FLAGS enumeration [.NET Framework profiling]
ms.assetid: 297d7721-3911-4f36-9e34-d9da0c33e22a
topic_type:
- apiref
ms.openlocfilehash: 5e718d05f033cc46fa460a81f6816a13ec32476d
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74428344"
---
# <a name="cor_prf_finalizer_flags-enumeration"></a><span data-ttu-id="3f8e3-102">COR_PRF_FINALIZER_FLAGS – výčet</span><span class="sxs-lookup"><span data-stu-id="3f8e3-102">COR_PRF_FINALIZER_FLAGS Enumeration</span></span>
<span data-ttu-id="3f8e3-103">Describes the finalizer for an object.</span><span class="sxs-lookup"><span data-stu-id="3f8e3-103">Describes the finalizer for an object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3f8e3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3f8e3-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PRF_FINALIZER_CRITICAL = 0x1  
} COR_PRF_FINALIZER_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="3f8e3-105">Členové</span><span class="sxs-lookup"><span data-stu-id="3f8e3-105">Members</span></span>  
  
|<span data-ttu-id="3f8e3-106">Člen</span><span class="sxs-lookup"><span data-stu-id="3f8e3-106">Member</span></span>|<span data-ttu-id="3f8e3-107">Popis</span><span class="sxs-lookup"><span data-stu-id="3f8e3-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_FINALIZER_CRITICAL`|<span data-ttu-id="3f8e3-108">The finalizer is critical.</span><span class="sxs-lookup"><span data-stu-id="3f8e3-108">The finalizer is critical.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3f8e3-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3f8e3-109">Remarks</span></span>  
 <span data-ttu-id="3f8e3-110">The `COR_PRF_FINALIZER_FLAGS` enumeration is used by the [ICorProfilerCallback2::FinalizeableObjectQueued](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-finalizeableobjectqueued-method.md) method to describe the finalizer for an object.</span><span class="sxs-lookup"><span data-stu-id="3f8e3-110">The `COR_PRF_FINALIZER_FLAGS` enumeration is used by the [ICorProfilerCallback2::FinalizeableObjectQueued](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-finalizeableobjectqueued-method.md) method to describe the finalizer for an object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3f8e3-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3f8e3-111">Requirements</span></span>  
 <span data-ttu-id="3f8e3-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3f8e3-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3f8e3-113">**Header:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="3f8e3-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="3f8e3-114">**Library:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3f8e3-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3f8e3-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3f8e3-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f8e3-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3f8e3-116">See also</span></span>

- [<span data-ttu-id="3f8e3-117">Výčty pro profilaci</span><span class="sxs-lookup"><span data-stu-id="3f8e3-117">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
