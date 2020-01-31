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
ms.openlocfilehash: b9fb308f19ff09218c97b030296b9a3d4f0f2512
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868184"
---
# <a name="icorprofilerthreadenum-interface"></a><span data-ttu-id="dcc74-102">ICorProfilerThreadEnum – rozhraní</span><span class="sxs-lookup"><span data-stu-id="dcc74-102">ICorProfilerThreadEnum Interface</span></span>
<span data-ttu-id="dcc74-103">Poskytuje metody pro sekvenční iteraci kolekcí vláken v modulu CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="dcc74-103">Provides methods to sequentially iterate through a collection of threads in the common language runtime.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="dcc74-104">Metody</span><span class="sxs-lookup"><span data-stu-id="dcc74-104">Methods</span></span>  
  
|<span data-ttu-id="dcc74-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="dcc74-105">Method</span></span>|<span data-ttu-id="dcc74-106">Popis</span><span class="sxs-lookup"><span data-stu-id="dcc74-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="dcc74-107">Clone – metoda</span><span class="sxs-lookup"><span data-stu-id="dcc74-107">Clone Method</span></span>](icorprofilerthreadenum-clone-method.md)|<span data-ttu-id="dcc74-108">Získá ukazatel rozhraní na kopii tohoto `ICorProfilerThreadEnum`ho rozhraní.</span><span class="sxs-lookup"><span data-stu-id="dcc74-108">Gets an interface pointer to a copy of this `ICorProfilerThreadEnum` interface.</span></span>|  
|[<span data-ttu-id="dcc74-109">GetCount – metoda</span><span class="sxs-lookup"><span data-stu-id="dcc74-109">GetCount Method</span></span>](icorprofilerthreadenum-getcount-method.md)|<span data-ttu-id="dcc74-110">Získá počet vláken, která aplikace používá.</span><span class="sxs-lookup"><span data-stu-id="dcc74-110">Gets the number of threads that are used by the application.</span></span>|  
|[<span data-ttu-id="dcc74-111">Next – metoda</span><span class="sxs-lookup"><span data-stu-id="dcc74-111">Next Method</span></span>](icorprofilerthreadenum-next-method.md)|<span data-ttu-id="dcc74-112">Získá zadaný počet souvislých vláken ze sekvenční kolekce vláken počínaje aktuální pozicí čítače výčtu v sekvenci.</span><span class="sxs-lookup"><span data-stu-id="dcc74-112">Gets the specified number of contiguous threads from a sequential collection of threads, starting at the enumerator's current position in the sequence.</span></span>|  
|[<span data-ttu-id="dcc74-113">Reset – metoda</span><span class="sxs-lookup"><span data-stu-id="dcc74-113">Reset Method</span></span>](icorprofilerthreadenum-reset-method.md)|<span data-ttu-id="dcc74-114">Přesune kurzor enumerátoru na počáteční pozici sekvence.</span><span class="sxs-lookup"><span data-stu-id="dcc74-114">Moves the enumerator's cursor to the starting position of the sequence.</span></span>|  
|[<span data-ttu-id="dcc74-115">Skip – metoda</span><span class="sxs-lookup"><span data-stu-id="dcc74-115">Skip Method</span></span>](icorprofilerthreadenum-skip-method.md)|<span data-ttu-id="dcc74-116">Posune kurzor čítače výčtu z aktuální pozice pro přeskočení zadaného počtu prvků.</span><span class="sxs-lookup"><span data-stu-id="dcc74-116">Advances the enumerator's cursor from its current position to skip the specified number of elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dcc74-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="dcc74-117">Remarks</span></span>  
 <span data-ttu-id="dcc74-118">Rozhraní `ICorProfilerThreadEnum` je enumerátor.</span><span class="sxs-lookup"><span data-stu-id="dcc74-118">The `ICorProfilerThreadEnum` interface is an enumerator.</span></span> <span data-ttu-id="dcc74-119">Umožňuje přijímači pole vyžádat si prvky od odesilatele v sazbě, která je vhodná pro příjemce.</span><span class="sxs-lookup"><span data-stu-id="dcc74-119">It allows the receiver of an array to pull elements from the sender at a rate that is appropriate for the receiver.</span></span> <span data-ttu-id="dcc74-120">Jinými slovy, přijímač je schopný explicitně řídit tok prvků pole, čímž se vyhnete problémům souvisejícím s předáváním velkých polí jako parametrů metody.</span><span class="sxs-lookup"><span data-stu-id="dcc74-120">In other words, the receiver is able to explicitly control the flow of array elements, thereby avoiding the problems associated with passing large arrays as method parameters.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dcc74-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="dcc74-121">Requirements</span></span>  
 <span data-ttu-id="dcc74-122">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dcc74-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dcc74-123">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="dcc74-123">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="dcc74-124">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="dcc74-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dcc74-125">**Verze .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dcc74-125">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dcc74-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="dcc74-126">See also</span></span>

- [<span data-ttu-id="dcc74-127">ICorProfilerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="dcc74-127">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="dcc74-128">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="dcc74-128">Profiling Interfaces</span></span>](profiling-interfaces.md)
