---
title: "ICorProfilerModuleEnum – rozhraní"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerModuleEnum
api_location: mscorwks.cll
api_type: COM
f1_keywords: ICorProfilerModuleEnum
helpviewer_keywords: ICorProfilerModuleEnum interface [.NET Framework profiling]
ms.assetid: 24d0fcfa-1601-4fba-868f-da8c97303467
topic_type: apiref
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 43cc6afc42fc1a02fd7d7b3df2973cc9b3e31251
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilermoduleenum-interface"></a><span data-ttu-id="2869a-102">ICorProfilerModuleEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2869a-102">ICorProfilerModuleEnum Interface</span></span>
<span data-ttu-id="2869a-103">Poskytuje metody pro postupně iteraci prostřednictvím kolekce moduly zavedené aplikace nebo profileru.</span><span class="sxs-lookup"><span data-stu-id="2869a-103">Provides methods to sequentially iterate through a collection of modules loaded by the application or the profiler.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2869a-104">Metody</span><span class="sxs-lookup"><span data-stu-id="2869a-104">Methods</span></span>  
  
|<span data-ttu-id="2869a-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="2869a-105">Method</span></span>|<span data-ttu-id="2869a-106">Popis</span><span class="sxs-lookup"><span data-stu-id="2869a-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2869a-107">Clone – metoda</span><span class="sxs-lookup"><span data-stu-id="2869a-107">Clone Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-clone-method.md)|<span data-ttu-id="2869a-108">Získá ukazatele rozhraní v kopii `ICorProfilerModuleEnum` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="2869a-108">Gets an interface pointer to a copy of this `ICorProfilerModuleEnum` interface.</span></span>|  
|[<span data-ttu-id="2869a-109">GetCount – metoda</span><span class="sxs-lookup"><span data-stu-id="2869a-109">GetCount Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-getcount-method.md)|<span data-ttu-id="2869a-110">Získá počet spravované moduly, které byly načteny do aplikace.</span><span class="sxs-lookup"><span data-stu-id="2869a-110">Gets the number of managed modules that were loaded into the application.</span></span>|  
|[<span data-ttu-id="2869a-111">Next – metoda</span><span class="sxs-lookup"><span data-stu-id="2869a-111">Next Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-next-method.md)|<span data-ttu-id="2869a-112">Získá zadaný počet souvislý moduly z sekvenční kolekcí objektů, počínaje na enumerátor na aktuální pozici v pořadí.</span><span class="sxs-lookup"><span data-stu-id="2869a-112">Gets the specified number of contiguous modules from a sequential collection of objects, starting at the enumerator's current position in the sequence.</span></span>|  
|[<span data-ttu-id="2869a-113">Reset – metoda</span><span class="sxs-lookup"><span data-stu-id="2869a-113">Reset Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-reset-method.md)|<span data-ttu-id="2869a-114">Posune kurzor enumerátor počáteční pozice pořadí.</span><span class="sxs-lookup"><span data-stu-id="2869a-114">Moves the enumerator's cursor to the starting position of the sequence.</span></span>|  
|[<span data-ttu-id="2869a-115">Skip – metoda</span><span class="sxs-lookup"><span data-stu-id="2869a-115">Skip Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-skip-method.md)|<span data-ttu-id="2869a-116">Přejde z pozice kurzoru enumerátor tak, aby se přeskočí zadaný počet elementů.</span><span class="sxs-lookup"><span data-stu-id="2869a-116">Advances the position of the enumerator's cursor so that the specified number of elements are skipped.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2869a-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2869a-117">Remarks</span></span>  
 <span data-ttu-id="2869a-118">`ICorProfilerModuleEnum` Rozhraní je enumerátor.</span><span class="sxs-lookup"><span data-stu-id="2869a-118">The `ICorProfilerModuleEnum` interface is an enumerator.</span></span> <span data-ttu-id="2869a-119">Příjemce pole umožňuje na vyžádání elementy od odesílatele rychlostí, který je vhodný pro příjemce.</span><span class="sxs-lookup"><span data-stu-id="2869a-119">It allows the receiver of an array to pull elements from the sender at a rate that is appropriate for the receiver.</span></span> <span data-ttu-id="2869a-120">Jinými slovy příjemce je schopen explicitně řízení toku prvků pole, aby se předešlo problémy spojené se předávání velké pole jako parametry metody.</span><span class="sxs-lookup"><span data-stu-id="2869a-120">In other words, the receiver is able to explicitly control the flow of array elements, thereby avoiding the problems associated with passing large arrays as method parameters.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2869a-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2869a-121">Requirements</span></span>  
 <span data-ttu-id="2869a-122">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2869a-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2869a-123">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="2869a-123">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="2869a-124">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2869a-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2869a-125">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2869a-125">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2869a-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="2869a-126">See Also</span></span>  
 [<span data-ttu-id="2869a-127">Icorprofilerinfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2869a-127">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="2869a-128">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="2869a-128">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="2869a-129">Enummodules – metoda</span><span class="sxs-lookup"><span data-stu-id="2869a-129">EnumModules Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enummodules-method.md)
