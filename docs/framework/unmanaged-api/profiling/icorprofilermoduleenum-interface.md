---
title: ICorProfilerModuleEnum – rozhraní
ms.date: 03/30/2017
api_name:
- ICorProfilerModuleEnum
api_location:
- mscorwks.cll
api_type:
- COM
f1_keywords:
- ICorProfilerModuleEnum
helpviewer_keywords:
- ICorProfilerModuleEnum interface [.NET Framework profiling]
ms.assetid: 24d0fcfa-1601-4fba-868f-da8c97303467
topic_type:
- apiref
ms.openlocfilehash: fe11c0bbe273ae07cdae43f681a558e07a291ffb
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84494888"
---
# <a name="icorprofilermoduleenum-interface"></a><span data-ttu-id="3a54b-102">ICorProfilerModuleEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3a54b-102">ICorProfilerModuleEnum Interface</span></span>
<span data-ttu-id="3a54b-103">Poskytuje metody pro sekvenční iteraci kolekcí modulů načtených aplikací nebo profilerem.</span><span class="sxs-lookup"><span data-stu-id="3a54b-103">Provides methods to sequentially iterate through a collection of modules loaded by the application or the profiler.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3a54b-104">Metody</span><span class="sxs-lookup"><span data-stu-id="3a54b-104">Methods</span></span>  
  
|<span data-ttu-id="3a54b-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="3a54b-105">Method</span></span>|<span data-ttu-id="3a54b-106">Description</span><span class="sxs-lookup"><span data-stu-id="3a54b-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3a54b-107">Clone – metoda</span><span class="sxs-lookup"><span data-stu-id="3a54b-107">Clone Method</span></span>](icorprofilermoduleenum-clone-method.md)|<span data-ttu-id="3a54b-108">Získá ukazatel rozhraní na kopii tohoto `ICorProfilerModuleEnum` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="3a54b-108">Gets an interface pointer to a copy of this `ICorProfilerModuleEnum` interface.</span></span>|  
|[<span data-ttu-id="3a54b-109">GetCount – metoda</span><span class="sxs-lookup"><span data-stu-id="3a54b-109">GetCount Method</span></span>](icorprofilermoduleenum-getcount-method.md)|<span data-ttu-id="3a54b-110">Získá počet spravovaných modulů, které byly načteny do aplikace.</span><span class="sxs-lookup"><span data-stu-id="3a54b-110">Gets the number of managed modules that were loaded into the application.</span></span>|  
|[<span data-ttu-id="3a54b-111">Next – metoda</span><span class="sxs-lookup"><span data-stu-id="3a54b-111">Next Method</span></span>](icorprofilermoduleenum-next-method.md)|<span data-ttu-id="3a54b-112">Získá zadaný počet souvislých modulů ze sekvenční kolekce objektů počínaje aktuální pozicí čítače výčtu v sekvenci.</span><span class="sxs-lookup"><span data-stu-id="3a54b-112">Gets the specified number of contiguous modules from a sequential collection of objects, starting at the enumerator's current position in the sequence.</span></span>|  
|[<span data-ttu-id="3a54b-113">Reset – metoda</span><span class="sxs-lookup"><span data-stu-id="3a54b-113">Reset Method</span></span>](icorprofilermoduleenum-reset-method.md)|<span data-ttu-id="3a54b-114">Přesune kurzor enumerátoru na počáteční pozici sekvence.</span><span class="sxs-lookup"><span data-stu-id="3a54b-114">Moves the enumerator's cursor to the starting position of the sequence.</span></span>|  
|[<span data-ttu-id="3a54b-115">Skip – metoda</span><span class="sxs-lookup"><span data-stu-id="3a54b-115">Skip Method</span></span>](icorprofilermoduleenum-skip-method.md)|<span data-ttu-id="3a54b-116">Posune pozici kurzoru enumerátoru tak, aby byl zadaný počet prvků vynechán.</span><span class="sxs-lookup"><span data-stu-id="3a54b-116">Advances the position of the enumerator's cursor so that the specified number of elements are skipped.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3a54b-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3a54b-117">Remarks</span></span>  
 <span data-ttu-id="3a54b-118">`ICorProfilerModuleEnum`Rozhraní je enumerátor.</span><span class="sxs-lookup"><span data-stu-id="3a54b-118">The `ICorProfilerModuleEnum` interface is an enumerator.</span></span> <span data-ttu-id="3a54b-119">Umožňuje přijímači pole vyžádat si prvky od odesilatele v sazbě, která je vhodná pro příjemce.</span><span class="sxs-lookup"><span data-stu-id="3a54b-119">It allows the receiver of an array to pull elements from the sender at a rate that is appropriate for the receiver.</span></span> <span data-ttu-id="3a54b-120">Jinými slovy, přijímač je schopný explicitně řídit tok prvků pole, čímž se vyhnete problémům souvisejícím s předáváním velkých polí jako parametrů metody.</span><span class="sxs-lookup"><span data-stu-id="3a54b-120">In other words, the receiver is able to explicitly control the flow of array elements, thereby avoiding the problems associated with passing large arrays as method parameters.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3a54b-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3a54b-121">Requirements</span></span>  
 <span data-ttu-id="3a54b-122">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3a54b-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3a54b-123">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="3a54b-123">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="3a54b-124">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="3a54b-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3a54b-125">**Verze .NET Framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3a54b-125">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a54b-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3a54b-126">See also</span></span>

- [<span data-ttu-id="3a54b-127">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3a54b-127">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="3a54b-128">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="3a54b-128">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="3a54b-129">EnumModules – metoda</span><span class="sxs-lookup"><span data-stu-id="3a54b-129">EnumModules Method</span></span>](icorprofilerinfo3-enummodules-method.md)
