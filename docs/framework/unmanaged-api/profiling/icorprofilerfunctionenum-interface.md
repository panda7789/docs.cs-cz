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
ms.openlocfilehash: add30952588ace0cbc80191617c37d7222cffee7
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76864489"
---
# <a name="icorprofilerfunctionenum-interface"></a><span data-ttu-id="78afd-102">ICorProfilerFunctionEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="78afd-102">ICorProfilerFunctionEnum Interface</span></span>
<span data-ttu-id="78afd-103">Poskytuje metody pro sekvenční iteraci kolekcí funkcí v modulu CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="78afd-103">Provides methods to sequentially iterate through a collection of functions in the common language runtime.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="78afd-104">Metody</span><span class="sxs-lookup"><span data-stu-id="78afd-104">Methods</span></span>  
  
|<span data-ttu-id="78afd-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="78afd-105">Method</span></span>|<span data-ttu-id="78afd-106">Popis</span><span class="sxs-lookup"><span data-stu-id="78afd-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="78afd-107">Clone – metoda</span><span class="sxs-lookup"><span data-stu-id="78afd-107">Clone Method</span></span>](icorprofilerfunctionenum-clone-method.md)|<span data-ttu-id="78afd-108">Získá ukazatel rozhraní na kopii tohoto `ICorProfilerFunctionEnum`ho rozhraní.</span><span class="sxs-lookup"><span data-stu-id="78afd-108">Gets an interface pointer to a copy of this `ICorProfilerFunctionEnum` interface.</span></span>|  
|[<span data-ttu-id="78afd-109">GetCount – metoda</span><span class="sxs-lookup"><span data-stu-id="78afd-109">GetCount Method</span></span>](icorprofilerfunctionenum-getcount-method.md)|<span data-ttu-id="78afd-110">Získá počet funkcí, které byly načteny aplikací nebo vynuceně načteny profilerem.</span><span class="sxs-lookup"><span data-stu-id="78afd-110">Gets the number of functions that were loaded by the application or forcibly loaded by the profiler.</span></span>|  
|[<span data-ttu-id="78afd-111">Next – metoda</span><span class="sxs-lookup"><span data-stu-id="78afd-111">Next Method</span></span>](icorprofilerfunctionenum-next-method.md)|<span data-ttu-id="78afd-112">Získá zadaný počet souvislých funkcí z sekvenční kolekce funkcí počínaje aktuální pozicí čítače výčtu v sekvenci.</span><span class="sxs-lookup"><span data-stu-id="78afd-112">Gets the specified number of contiguous functions from a sequential collection of functions, starting at the enumerator's current position in the sequence.</span></span>|  
|[<span data-ttu-id="78afd-113">Reset – metoda</span><span class="sxs-lookup"><span data-stu-id="78afd-113">Reset Method</span></span>](icorprofilerfunctionenum-reset-method.md)|<span data-ttu-id="78afd-114">Přesune kurzor enumerátoru na počáteční pozici sekvence.</span><span class="sxs-lookup"><span data-stu-id="78afd-114">Moves the enumerator's cursor to the starting position of the sequence.</span></span>|  
|[<span data-ttu-id="78afd-115">Skip – metoda</span><span class="sxs-lookup"><span data-stu-id="78afd-115">Skip Method</span></span>](icorprofilerfunctionenum-skip-method.md)|<span data-ttu-id="78afd-116">Posune kurzor čítače výčtu z aktuální pozice tak, aby byl zadaný počet prvků vynechán.</span><span class="sxs-lookup"><span data-stu-id="78afd-116">Advances the enumerator's cursor from its current position so that the specified number of elements are skipped.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="78afd-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="78afd-117">Remarks</span></span>  
 <span data-ttu-id="78afd-118">Rozhraní `ICorProfilerFunctionEnum` je enumerátor.</span><span class="sxs-lookup"><span data-stu-id="78afd-118">The `ICorProfilerFunctionEnum` interface is an enumerator.</span></span> <span data-ttu-id="78afd-119">Umožňuje přijímači pole vyžádat si prvky od odesilatele v sazbě, která je vhodná pro příjemce.</span><span class="sxs-lookup"><span data-stu-id="78afd-119">It allows the receiver of an array to pull elements from the sender at a rate that is appropriate for the receiver.</span></span> <span data-ttu-id="78afd-120">Jinými slovy, přijímač je schopný explicitně řídit tok prvků pole, čímž se vyhnete problémům souvisejícím s předáváním velkých polí jako parametrů metody.</span><span class="sxs-lookup"><span data-stu-id="78afd-120">In other words, the receiver is able to explicitly control the flow of array elements, thereby avoiding the problems associated with passing large arrays as method parameters.</span></span>  
  
 <span data-ttu-id="78afd-121">`ICorProfilerFunctionEnum` se vyčíslují nad funkcemi, které již byly kompilovány JIT, ale nezahrnují funkce, které jsou načteny z nativních imagí vygenerovaných pomocí nástroje Ngen. exe.</span><span class="sxs-lookup"><span data-stu-id="78afd-121">`ICorProfilerFunctionEnum` enumerates over functions that have already been JIT-compiled, but does not include functions that are loaded from native images generated with Ngen.exe.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="78afd-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="78afd-122">Requirements</span></span>  
 <span data-ttu-id="78afd-123">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="78afd-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="78afd-124">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="78afd-124">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="78afd-125">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="78afd-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="78afd-126">**Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="78afd-126">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78afd-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="78afd-127">See also</span></span>

- [<span data-ttu-id="78afd-128">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="78afd-128">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="78afd-129">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="78afd-129">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="78afd-130">EnumJITedFunctions – metoda</span><span class="sxs-lookup"><span data-stu-id="78afd-130">EnumJITedFunctions Method</span></span>](icorprofilerinfo3-enumjitedfunctions-method.md)
