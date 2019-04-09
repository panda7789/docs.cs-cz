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
ms.openlocfilehash: 47359cd71460732100364f07e0dc5efacc44c760
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59092042"
---
# <a name="icorprofilerthreadenum-interface"></a><span data-ttu-id="2b0ed-102">ICorProfilerThreadEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2b0ed-102">ICorProfilerThreadEnum Interface</span></span>
<span data-ttu-id="2b0ed-103">Poskytuje metody pro postupně iterovat přes kolekci vláken v modulu common language runtime.</span><span class="sxs-lookup"><span data-stu-id="2b0ed-103">Provides methods to sequentially iterate through a collection of threads in the common language runtime.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2b0ed-104">Metody</span><span class="sxs-lookup"><span data-stu-id="2b0ed-104">Methods</span></span>  
  
|<span data-ttu-id="2b0ed-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="2b0ed-105">Method</span></span>|<span data-ttu-id="2b0ed-106">Popis</span><span class="sxs-lookup"><span data-stu-id="2b0ed-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2b0ed-107">Clone – metoda</span><span class="sxs-lookup"><span data-stu-id="2b0ed-107">Clone Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-clone-method.md)|<span data-ttu-id="2b0ed-108">Získá ukazatel rozhraní na kopii této `ICorProfilerThreadEnum` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="2b0ed-108">Gets an interface pointer to a copy of this `ICorProfilerThreadEnum` interface.</span></span>|  
|[<span data-ttu-id="2b0ed-109">GetCount – metoda</span><span class="sxs-lookup"><span data-stu-id="2b0ed-109">GetCount Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-getcount-method.md)|<span data-ttu-id="2b0ed-110">Získá počet vláken, která jsou v aplikaci použít.</span><span class="sxs-lookup"><span data-stu-id="2b0ed-110">Gets the number of threads that are used by the application.</span></span>|  
|[<span data-ttu-id="2b0ed-111">Next – metoda</span><span class="sxs-lookup"><span data-stu-id="2b0ed-111">Next Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-next-method.md)|<span data-ttu-id="2b0ed-112">Získá zadaný počet souvislých vlákna z kolekce sekvenčních vláken, od aktuální pozice čítače výčtu v sekvenci.</span><span class="sxs-lookup"><span data-stu-id="2b0ed-112">Gets the specified number of contiguous threads from a sequential collection of threads, starting at the enumerator's current position in the sequence.</span></span>|  
|[<span data-ttu-id="2b0ed-113">Reset – metoda</span><span class="sxs-lookup"><span data-stu-id="2b0ed-113">Reset Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-reset-method.md)|<span data-ttu-id="2b0ed-114">Přesune kurzor čítače výčtu na počáteční pozici pořadí.</span><span class="sxs-lookup"><span data-stu-id="2b0ed-114">Moves the enumerator's cursor to the starting position of the sequence.</span></span>|  
|[<span data-ttu-id="2b0ed-115">Skip – metoda</span><span class="sxs-lookup"><span data-stu-id="2b0ed-115">Skip Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-skip-method.md)|<span data-ttu-id="2b0ed-116">Posune kurzor čítače výčtu ze své aktuální pozici pro přeskočení zadaný počet prvků.</span><span class="sxs-lookup"><span data-stu-id="2b0ed-116">Advances the enumerator's cursor from its current position to skip the specified number of elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2b0ed-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2b0ed-117">Remarks</span></span>  
 <span data-ttu-id="2b0ed-118">`ICorProfilerThreadEnum` Rozhraní je enumerátor.</span><span class="sxs-lookup"><span data-stu-id="2b0ed-118">The `ICorProfilerThreadEnum` interface is an enumerator.</span></span> <span data-ttu-id="2b0ed-119">Umožňuje příjemce pole prvků o přijetí změn od odesílatele rychlostí, která je vhodná pro příjemce.</span><span class="sxs-lookup"><span data-stu-id="2b0ed-119">It allows the receiver of an array to pull elements from the sender at a rate that is appropriate for the receiver.</span></span> <span data-ttu-id="2b0ed-120">Jinými slovy příjemce je explicitně řídit tok prvků pole, aby se předešlo problémy související s předání velkých polí jako parametrů metody.</span><span class="sxs-lookup"><span data-stu-id="2b0ed-120">In other words, the receiver is able to explicitly control the flow of array elements, thereby avoiding the problems associated with passing large arrays as method parameters.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2b0ed-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2b0ed-121">Requirements</span></span>  
 <span data-ttu-id="2b0ed-122">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2b0ed-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2b0ed-123">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="2b0ed-123">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="2b0ed-124">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2b0ed-124">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="2b0ed-125">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="2b0ed-125">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="2b0ed-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2b0ed-126">See also</span></span>

- [<span data-ttu-id="2b0ed-127">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2b0ed-127">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="2b0ed-128">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="2b0ed-128">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
