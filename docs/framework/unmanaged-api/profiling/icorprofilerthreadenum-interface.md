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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7b9662ccb854345d41bb73a5cf01a94b9949891d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33457192"
---
# <a name="icorprofilerthreadenum-interface"></a><span data-ttu-id="18092-102">ICorProfilerThreadEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="18092-102">ICorProfilerThreadEnum Interface</span></span>
<span data-ttu-id="18092-103">Poskytuje metody pro postupně iteraci prostřednictvím kolekce vláken v modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="18092-103">Provides methods to sequentially iterate through a collection of threads in the common language runtime.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="18092-104">Metody</span><span class="sxs-lookup"><span data-stu-id="18092-104">Methods</span></span>  
  
|<span data-ttu-id="18092-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="18092-105">Method</span></span>|<span data-ttu-id="18092-106">Popis</span><span class="sxs-lookup"><span data-stu-id="18092-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="18092-107">Clone – metoda</span><span class="sxs-lookup"><span data-stu-id="18092-107">Clone Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-clone-method.md)|<span data-ttu-id="18092-108">Získá ukazatele rozhraní v kopii `ICorProfilerThreadEnum` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="18092-108">Gets an interface pointer to a copy of this `ICorProfilerThreadEnum` interface.</span></span>|  
|[<span data-ttu-id="18092-109">GetCount – metoda</span><span class="sxs-lookup"><span data-stu-id="18092-109">GetCount Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-getcount-method.md)|<span data-ttu-id="18092-110">Získá počet vláken, které používají aplikace.</span><span class="sxs-lookup"><span data-stu-id="18092-110">Gets the number of threads that are used by the application.</span></span>|  
|[<span data-ttu-id="18092-111">Next – metoda</span><span class="sxs-lookup"><span data-stu-id="18092-111">Next Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-next-method.md)|<span data-ttu-id="18092-112">Získá zadaný počet vláken, souvislý z kolekce sekvenčních vláken, začínající na enumerátor na aktuální pozici v pořadí.</span><span class="sxs-lookup"><span data-stu-id="18092-112">Gets the specified number of contiguous threads from a sequential collection of threads, starting at the enumerator's current position in the sequence.</span></span>|  
|[<span data-ttu-id="18092-113">Reset – metoda</span><span class="sxs-lookup"><span data-stu-id="18092-113">Reset Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-reset-method.md)|<span data-ttu-id="18092-114">Posune kurzor enumerátor počáteční pozice pořadí.</span><span class="sxs-lookup"><span data-stu-id="18092-114">Moves the enumerator's cursor to the starting position of the sequence.</span></span>|  
|[<span data-ttu-id="18092-115">Skip – metoda</span><span class="sxs-lookup"><span data-stu-id="18092-115">Skip Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-skip-method.md)|<span data-ttu-id="18092-116">Posune kurzor enumerátor z aktuálního umístění tak, aby přeskočil zadaný počet elementů.</span><span class="sxs-lookup"><span data-stu-id="18092-116">Advances the enumerator's cursor from its current position to skip the specified number of elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="18092-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="18092-117">Remarks</span></span>  
 <span data-ttu-id="18092-118">`ICorProfilerThreadEnum` Rozhraní je enumerátor.</span><span class="sxs-lookup"><span data-stu-id="18092-118">The `ICorProfilerThreadEnum` interface is an enumerator.</span></span> <span data-ttu-id="18092-119">Příjemce pole umožňuje na vyžádání elementy od odesílatele rychlostí, který je vhodný pro příjemce.</span><span class="sxs-lookup"><span data-stu-id="18092-119">It allows the receiver of an array to pull elements from the sender at a rate that is appropriate for the receiver.</span></span> <span data-ttu-id="18092-120">Jinými slovy příjemce je schopen explicitně řízení toku prvků pole, aby se předešlo problémy spojené se předávání velké pole jako parametry metody.</span><span class="sxs-lookup"><span data-stu-id="18092-120">In other words, the receiver is able to explicitly control the flow of array elements, thereby avoiding the problems associated with passing large arrays as method parameters.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="18092-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="18092-121">Requirements</span></span>  
 <span data-ttu-id="18092-122">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="18092-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="18092-123">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="18092-123">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="18092-124">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="18092-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="18092-125">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="18092-125">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18092-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="18092-126">See Also</span></span>  
 [<span data-ttu-id="18092-127">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="18092-127">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="18092-128">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="18092-128">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
