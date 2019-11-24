---
title: ICorProfilerThreadEnum – rozhraní
ms.date: 03/30/2017
api_name:
- ICorProfilerThreadEnum
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerThreadEnum
helpviewer_keywords:
- ICorProfilerThreadEnum interface [.NET Framework profiling]
ms.assetid: 1e35031b-e095-4c14-9644-8deeb3081e0b
topic_type:
- apiref
ms.openlocfilehash: b83706176091fd70d48e0f50a0fe5988c876f606
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447616"
---
# <a name="icorprofilerthreadenum-interface"></a><span data-ttu-id="7899b-102">ICorProfilerThreadEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7899b-102">ICorProfilerThreadEnum Interface</span></span>
<span data-ttu-id="7899b-103">Provides methods to sequentially iterate through a collection of threads in the common language runtime.</span><span class="sxs-lookup"><span data-stu-id="7899b-103">Provides methods to sequentially iterate through a collection of threads in the common language runtime.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7899b-104">Metody</span><span class="sxs-lookup"><span data-stu-id="7899b-104">Methods</span></span>  
  
|<span data-ttu-id="7899b-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="7899b-105">Method</span></span>|<span data-ttu-id="7899b-106">Popis</span><span class="sxs-lookup"><span data-stu-id="7899b-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7899b-107">Clone – metoda</span><span class="sxs-lookup"><span data-stu-id="7899b-107">Clone Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-clone-method.md)|<span data-ttu-id="7899b-108">Gets an interface pointer to a copy of this `ICorProfilerThreadEnum` interface.</span><span class="sxs-lookup"><span data-stu-id="7899b-108">Gets an interface pointer to a copy of this `ICorProfilerThreadEnum` interface.</span></span>|  
|[<span data-ttu-id="7899b-109">GetCount – metoda</span><span class="sxs-lookup"><span data-stu-id="7899b-109">GetCount Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-getcount-method.md)|<span data-ttu-id="7899b-110">Gets the number of threads that are used by the application.</span><span class="sxs-lookup"><span data-stu-id="7899b-110">Gets the number of threads that are used by the application.</span></span>|  
|[<span data-ttu-id="7899b-111">Next – metoda</span><span class="sxs-lookup"><span data-stu-id="7899b-111">Next Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-next-method.md)|<span data-ttu-id="7899b-112">Gets the specified number of contiguous threads from a sequential collection of threads, starting at the enumerator's current position in the sequence.</span><span class="sxs-lookup"><span data-stu-id="7899b-112">Gets the specified number of contiguous threads from a sequential collection of threads, starting at the enumerator's current position in the sequence.</span></span>|  
|[<span data-ttu-id="7899b-113">Reset – metoda</span><span class="sxs-lookup"><span data-stu-id="7899b-113">Reset Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-reset-method.md)|<span data-ttu-id="7899b-114">Moves the enumerator's cursor to the starting position of the sequence.</span><span class="sxs-lookup"><span data-stu-id="7899b-114">Moves the enumerator's cursor to the starting position of the sequence.</span></span>|  
|[<span data-ttu-id="7899b-115">Skip – metoda</span><span class="sxs-lookup"><span data-stu-id="7899b-115">Skip Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-skip-method.md)|<span data-ttu-id="7899b-116">Advances the enumerator's cursor from its current position to skip the specified number of elements.</span><span class="sxs-lookup"><span data-stu-id="7899b-116">Advances the enumerator's cursor from its current position to skip the specified number of elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7899b-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7899b-117">Remarks</span></span>  
 <span data-ttu-id="7899b-118">The `ICorProfilerThreadEnum` interface is an enumerator.</span><span class="sxs-lookup"><span data-stu-id="7899b-118">The `ICorProfilerThreadEnum` interface is an enumerator.</span></span> <span data-ttu-id="7899b-119">It allows the receiver of an array to pull elements from the sender at a rate that is appropriate for the receiver.</span><span class="sxs-lookup"><span data-stu-id="7899b-119">It allows the receiver of an array to pull elements from the sender at a rate that is appropriate for the receiver.</span></span> <span data-ttu-id="7899b-120">In other words, the receiver is able to explicitly control the flow of array elements, thereby avoiding the problems associated with passing large arrays as method parameters.</span><span class="sxs-lookup"><span data-stu-id="7899b-120">In other words, the receiver is able to explicitly control the flow of array elements, thereby avoiding the problems associated with passing large arrays as method parameters.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7899b-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7899b-121">Requirements</span></span>  
 <span data-ttu-id="7899b-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7899b-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7899b-123">**Header:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="7899b-123">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="7899b-124">**Library:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7899b-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7899b-125">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7899b-125">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7899b-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7899b-126">See also</span></span>

- [<span data-ttu-id="7899b-127">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7899b-127">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="7899b-128">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="7899b-128">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
