---
title: "ICorProfilerFunctionEnum – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerFunctionEnum
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerFunctionEnum
helpviewer_keywords: ICorProfilerFunctionEnum interface [.NET Framework profiling]
ms.assetid: 0a1d4a38-cd0b-4231-91df-13646218ae72
topic_type: apiref
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1a3014c8b00cb431c2c5b101e17dc51f49bf73f0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerfunctionenum-interface"></a><span data-ttu-id="0244e-102">ICorProfilerFunctionEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0244e-102">ICorProfilerFunctionEnum Interface</span></span>
<span data-ttu-id="0244e-103">Poskytuje metody pro postupně iteraci přes kolekci funkcí v modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="0244e-103">Provides methods to sequentially iterate through a collection of functions in the common language runtime.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0244e-104">Metody</span><span class="sxs-lookup"><span data-stu-id="0244e-104">Methods</span></span>  
  
|<span data-ttu-id="0244e-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="0244e-105">Method</span></span>|<span data-ttu-id="0244e-106">Popis</span><span class="sxs-lookup"><span data-stu-id="0244e-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0244e-107">Clone – metoda</span><span class="sxs-lookup"><span data-stu-id="0244e-107">Clone Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-clone-method.md)|<span data-ttu-id="0244e-108">Získá ukazatele rozhraní v kopii `ICorProfilerFunctionEnum` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="0244e-108">Gets an interface pointer to a copy of this `ICorProfilerFunctionEnum` interface.</span></span>|  
|[<span data-ttu-id="0244e-109">GetCount – metoda</span><span class="sxs-lookup"><span data-stu-id="0244e-109">GetCount Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-getcount-method.md)|<span data-ttu-id="0244e-110">Získá počet funkcí, které byly v aplikaci nebo vynuceně načteny profileru.</span><span class="sxs-lookup"><span data-stu-id="0244e-110">Gets the number of functions that were loaded by the application or forcibly loaded by the profiler.</span></span>|  
|[<span data-ttu-id="0244e-111">Next – metoda</span><span class="sxs-lookup"><span data-stu-id="0244e-111">Next Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-next-method.md)|<span data-ttu-id="0244e-112">Získá zadaný počet souvislý funkce z sekvenční kolekce funkcí, začínající na enumerátor na aktuální pozici v pořadí.</span><span class="sxs-lookup"><span data-stu-id="0244e-112">Gets the specified number of contiguous functions from a sequential collection of functions, starting at the enumerator's current position in the sequence.</span></span>|  
|[<span data-ttu-id="0244e-113">Reset – metoda</span><span class="sxs-lookup"><span data-stu-id="0244e-113">Reset Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-reset-method.md)|<span data-ttu-id="0244e-114">Posune kurzor enumerátor počáteční pozice pořadí.</span><span class="sxs-lookup"><span data-stu-id="0244e-114">Moves the enumerator's cursor to the starting position of the sequence.</span></span>|  
|[<span data-ttu-id="0244e-115">Skip – metoda</span><span class="sxs-lookup"><span data-stu-id="0244e-115">Skip Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-skip-method.md)|<span data-ttu-id="0244e-116">Posune kurzor enumerátor z aktuálního umístění tak, aby se přeskočí zadaný počet elementů.</span><span class="sxs-lookup"><span data-stu-id="0244e-116">Advances the enumerator's cursor from its current position so that the specified number of elements are skipped.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0244e-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0244e-117">Remarks</span></span>  
 <span data-ttu-id="0244e-118">`ICorProfilerFunctionEnum` Rozhraní je enumerátor.</span><span class="sxs-lookup"><span data-stu-id="0244e-118">The `ICorProfilerFunctionEnum` interface is an enumerator.</span></span> <span data-ttu-id="0244e-119">Příjemce pole umožňuje na vyžádání elementy od odesílatele rychlostí, který je vhodný pro příjemce.</span><span class="sxs-lookup"><span data-stu-id="0244e-119">It allows the receiver of an array to pull elements from the sender at a rate that is appropriate for the receiver.</span></span> <span data-ttu-id="0244e-120">Jinými slovy příjemce je schopen explicitně řízení toku prvků pole, aby se předešlo problémy spojené se předávání velké pole jako parametry metody.</span><span class="sxs-lookup"><span data-stu-id="0244e-120">In other words, the receiver is able to explicitly control the flow of array elements, thereby avoiding the problems associated with passing large arrays as method parameters.</span></span>  
  
 <span data-ttu-id="0244e-121">`ICorProfilerFunctionEnum`Vytvoří výčet prostřednictvím funkce, které již bylo kompilováno za běhu, ale neobsahuje funkce, které jsou načteny z vygeneroval s Ngen.exe nativní bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="0244e-121">`ICorProfilerFunctionEnum` enumerates over functions that have already been JIT-compiled, but does not include functions that are loaded from native images generated with Ngen.exe.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0244e-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0244e-122">Requirements</span></span>  
 <span data-ttu-id="0244e-123">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0244e-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0244e-124">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="0244e-124">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="0244e-125">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0244e-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0244e-126">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0244e-126">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0244e-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="0244e-127">See Also</span></span>  
 [<span data-ttu-id="0244e-128">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0244e-128">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="0244e-129">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="0244e-129">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="0244e-130">EnumJITedFunctions – metoda</span><span class="sxs-lookup"><span data-stu-id="0244e-130">EnumJITedFunctions Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enumjitedfunctions-method.md)
