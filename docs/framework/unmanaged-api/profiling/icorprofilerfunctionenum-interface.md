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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0e77ec9de198b673bb3b5fc4dad3cd1b0316f07c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59092068"
---
# <a name="icorprofilerfunctionenum-interface"></a><span data-ttu-id="0564f-102">ICorProfilerFunctionEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0564f-102">ICorProfilerFunctionEnum Interface</span></span>
<span data-ttu-id="0564f-103">Poskytuje metody pro postupně iteraci prostřednictvím kolekce funkcí v modulu common language runtime.</span><span class="sxs-lookup"><span data-stu-id="0564f-103">Provides methods to sequentially iterate through a collection of functions in the common language runtime.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0564f-104">Metody</span><span class="sxs-lookup"><span data-stu-id="0564f-104">Methods</span></span>  
  
|<span data-ttu-id="0564f-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="0564f-105">Method</span></span>|<span data-ttu-id="0564f-106">Popis</span><span class="sxs-lookup"><span data-stu-id="0564f-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0564f-107">Clone – metoda</span><span class="sxs-lookup"><span data-stu-id="0564f-107">Clone Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-clone-method.md)|<span data-ttu-id="0564f-108">Získá ukazatel rozhraní na kopii této `ICorProfilerFunctionEnum` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="0564f-108">Gets an interface pointer to a copy of this `ICorProfilerFunctionEnum` interface.</span></span>|  
|[<span data-ttu-id="0564f-109">GetCount – metoda</span><span class="sxs-lookup"><span data-stu-id="0564f-109">GetCount Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-getcount-method.md)|<span data-ttu-id="0564f-110">Získá počet funkcí, které byly načteny aplikací nebo vynuceně načíst pomocí profileru.</span><span class="sxs-lookup"><span data-stu-id="0564f-110">Gets the number of functions that were loaded by the application or forcibly loaded by the profiler.</span></span>|  
|[<span data-ttu-id="0564f-111">Next – metoda</span><span class="sxs-lookup"><span data-stu-id="0564f-111">Next Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-next-method.md)|<span data-ttu-id="0564f-112">Získá zadaný počet souvislých funkce z sekvenční kolekce funkcí, od aktuální pozice čítače výčtu v sekvenci.</span><span class="sxs-lookup"><span data-stu-id="0564f-112">Gets the specified number of contiguous functions from a sequential collection of functions, starting at the enumerator's current position in the sequence.</span></span>|  
|[<span data-ttu-id="0564f-113">Reset – metoda</span><span class="sxs-lookup"><span data-stu-id="0564f-113">Reset Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-reset-method.md)|<span data-ttu-id="0564f-114">Přesune kurzor čítače výčtu na počáteční pozici pořadí.</span><span class="sxs-lookup"><span data-stu-id="0564f-114">Moves the enumerator's cursor to the starting position of the sequence.</span></span>|  
|[<span data-ttu-id="0564f-115">Skip – metoda</span><span class="sxs-lookup"><span data-stu-id="0564f-115">Skip Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-skip-method.md)|<span data-ttu-id="0564f-116">Posune kurzor enumerátor z aktuálního umístění tak, aby zadaný počet prvků, které se přeskočí.</span><span class="sxs-lookup"><span data-stu-id="0564f-116">Advances the enumerator's cursor from its current position so that the specified number of elements are skipped.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0564f-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0564f-117">Remarks</span></span>  
 <span data-ttu-id="0564f-118">`ICorProfilerFunctionEnum` Rozhraní je enumerátor.</span><span class="sxs-lookup"><span data-stu-id="0564f-118">The `ICorProfilerFunctionEnum` interface is an enumerator.</span></span> <span data-ttu-id="0564f-119">Umožňuje příjemce pole prvků o přijetí změn od odesílatele rychlostí, která je vhodná pro příjemce.</span><span class="sxs-lookup"><span data-stu-id="0564f-119">It allows the receiver of an array to pull elements from the sender at a rate that is appropriate for the receiver.</span></span> <span data-ttu-id="0564f-120">Jinými slovy příjemce je explicitně řídit tok prvků pole, aby se předešlo problémy související s předání velkých polí jako parametrů metody.</span><span class="sxs-lookup"><span data-stu-id="0564f-120">In other words, the receiver is able to explicitly control the flow of array elements, thereby avoiding the problems associated with passing large arrays as method parameters.</span></span>  
  
 <span data-ttu-id="0564f-121">`ICorProfilerFunctionEnum` Vytvoří výčet prostřednictvím funkcí, které již byly zkompilovány JIT, ale neobsahuje funkce, které jsou načteny z nativní bitové kopie generované nástrojem Ngen.exe.</span><span class="sxs-lookup"><span data-stu-id="0564f-121">`ICorProfilerFunctionEnum` enumerates over functions that have already been JIT-compiled, but does not include functions that are loaded from native images generated with Ngen.exe.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0564f-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0564f-122">Requirements</span></span>  
 <span data-ttu-id="0564f-123">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0564f-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0564f-124">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="0564f-124">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="0564f-125">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0564f-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0564f-126">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0564f-126">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0564f-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0564f-127">See also</span></span>

- [<span data-ttu-id="0564f-128">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0564f-128">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="0564f-129">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="0564f-129">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="0564f-130">EnumJITedFunctions – metoda</span><span class="sxs-lookup"><span data-stu-id="0564f-130">EnumJITedFunctions Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-enumjitedfunctions-method.md)
