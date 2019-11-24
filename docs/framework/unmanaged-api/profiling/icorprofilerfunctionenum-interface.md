---
title: ICorProfilerFunctionEnum – rozhraní
ms.date: 03/30/2017
api_name:
- ICorProfilerFunctionEnum
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerFunctionEnum
helpviewer_keywords:
- ICorProfilerFunctionEnum interface [.NET Framework profiling]
ms.assetid: 0a1d4a38-cd0b-4231-91df-13646218ae72
topic_type:
- apiref
ms.openlocfilehash: 17f7243096b7ac18e456f8f31196055492015346
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447805"
---
# <a name="icorprofilerfunctionenum-interface"></a><span data-ttu-id="ccc08-102">ICorProfilerFunctionEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ccc08-102">ICorProfilerFunctionEnum Interface</span></span>
<span data-ttu-id="ccc08-103">Provides methods to sequentially iterate through a collection of functions in the common language runtime.</span><span class="sxs-lookup"><span data-stu-id="ccc08-103">Provides methods to sequentially iterate through a collection of functions in the common language runtime.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ccc08-104">Metody</span><span class="sxs-lookup"><span data-stu-id="ccc08-104">Methods</span></span>  
  
|<span data-ttu-id="ccc08-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="ccc08-105">Method</span></span>|<span data-ttu-id="ccc08-106">Popis</span><span class="sxs-lookup"><span data-stu-id="ccc08-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ccc08-107">Clone – metoda</span><span class="sxs-lookup"><span data-stu-id="ccc08-107">Clone Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-clone-method.md)|<span data-ttu-id="ccc08-108">Gets an interface pointer to a copy of this `ICorProfilerFunctionEnum` interface.</span><span class="sxs-lookup"><span data-stu-id="ccc08-108">Gets an interface pointer to a copy of this `ICorProfilerFunctionEnum` interface.</span></span>|  
|[<span data-ttu-id="ccc08-109">GetCount – metoda</span><span class="sxs-lookup"><span data-stu-id="ccc08-109">GetCount Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-getcount-method.md)|<span data-ttu-id="ccc08-110">Gets the number of functions that were loaded by the application or forcibly loaded by the profiler.</span><span class="sxs-lookup"><span data-stu-id="ccc08-110">Gets the number of functions that were loaded by the application or forcibly loaded by the profiler.</span></span>|  
|[<span data-ttu-id="ccc08-111">Next – metoda</span><span class="sxs-lookup"><span data-stu-id="ccc08-111">Next Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-next-method.md)|<span data-ttu-id="ccc08-112">Gets the specified number of contiguous functions from a sequential collection of functions, starting at the enumerator's current position in the sequence.</span><span class="sxs-lookup"><span data-stu-id="ccc08-112">Gets the specified number of contiguous functions from a sequential collection of functions, starting at the enumerator's current position in the sequence.</span></span>|  
|[<span data-ttu-id="ccc08-113">Reset – metoda</span><span class="sxs-lookup"><span data-stu-id="ccc08-113">Reset Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-reset-method.md)|<span data-ttu-id="ccc08-114">Moves the enumerator's cursor to the starting position of the sequence.</span><span class="sxs-lookup"><span data-stu-id="ccc08-114">Moves the enumerator's cursor to the starting position of the sequence.</span></span>|  
|[<span data-ttu-id="ccc08-115">Skip – metoda</span><span class="sxs-lookup"><span data-stu-id="ccc08-115">Skip Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-skip-method.md)|<span data-ttu-id="ccc08-116">Advances the enumerator's cursor from its current position so that the specified number of elements are skipped.</span><span class="sxs-lookup"><span data-stu-id="ccc08-116">Advances the enumerator's cursor from its current position so that the specified number of elements are skipped.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ccc08-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ccc08-117">Remarks</span></span>  
 <span data-ttu-id="ccc08-118">The `ICorProfilerFunctionEnum` interface is an enumerator.</span><span class="sxs-lookup"><span data-stu-id="ccc08-118">The `ICorProfilerFunctionEnum` interface is an enumerator.</span></span> <span data-ttu-id="ccc08-119">It allows the receiver of an array to pull elements from the sender at a rate that is appropriate for the receiver.</span><span class="sxs-lookup"><span data-stu-id="ccc08-119">It allows the receiver of an array to pull elements from the sender at a rate that is appropriate for the receiver.</span></span> <span data-ttu-id="ccc08-120">In other words, the receiver is able to explicitly control the flow of array elements, thereby avoiding the problems associated with passing large arrays as method parameters.</span><span class="sxs-lookup"><span data-stu-id="ccc08-120">In other words, the receiver is able to explicitly control the flow of array elements, thereby avoiding the problems associated with passing large arrays as method parameters.</span></span>  
  
 <span data-ttu-id="ccc08-121">`ICorProfilerFunctionEnum` enumerates over functions that have already been JIT-compiled, but does not include functions that are loaded from native images generated with Ngen.exe.</span><span class="sxs-lookup"><span data-stu-id="ccc08-121">`ICorProfilerFunctionEnum` enumerates over functions that have already been JIT-compiled, but does not include functions that are loaded from native images generated with Ngen.exe.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ccc08-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ccc08-122">Requirements</span></span>  
 <span data-ttu-id="ccc08-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ccc08-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ccc08-124">**Header:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ccc08-124">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ccc08-125">**Library:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ccc08-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ccc08-126">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ccc08-126">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ccc08-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ccc08-127">See also</span></span>

- [<span data-ttu-id="ccc08-128">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ccc08-128">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="ccc08-129">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="ccc08-129">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="ccc08-130">EnumJITedFunctions – metoda</span><span class="sxs-lookup"><span data-stu-id="ccc08-130">EnumJITedFunctions Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enumjitedfunctions-method.md)
