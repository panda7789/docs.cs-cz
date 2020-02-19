---
title: ICorProfilerInfo10 – rozhraní
ms.date: 08/06/2019
author: davmason
ms.author: davmason
ms.openlocfilehash: 30179c7c198a343baa3fa01ae64f6d580a3f9e7e
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452198"
---
# <a name="icorprofilerinfo10-interface"></a><span data-ttu-id="c9299-102">ICorProfilerInfo10 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c9299-102">ICorProfilerInfo10 Interface</span></span>

<span data-ttu-id="c9299-103">Podtřída [ICorProfilerInfo9](icorprofilerinfo9-interface.md) , která poskytuje metody pro úpravu Il funkce, dotazování na informace z modulu runtime a pozastavení a obnovení modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="c9299-103">A subclass of [ICorProfilerInfo9](icorprofilerinfo9-interface.md) that provides methods to modify function IL, query information from the runtime, and suspend and resume the runtime.</span></span>

## <a name="methods"></a><span data-ttu-id="c9299-104">Metody</span><span class="sxs-lookup"><span data-stu-id="c9299-104">Methods</span></span>  

| <span data-ttu-id="c9299-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="c9299-105">Method</span></span>|<span data-ttu-id="c9299-106">Popis</span><span class="sxs-lookup"><span data-stu-id="c9299-106">Description</span></span>|  
| ------------|-----------------|  
|[<span data-ttu-id="c9299-107">Metoda EnumerateObjectReferences</span><span class="sxs-lookup"><span data-stu-id="c9299-107">EnumerateObjectReferences Method</span></span>](icorprofilerinfo10-enumerateobjectreferences-method.md)|<span data-ttu-id="c9299-108">Po předaném identifikátoru ObjectID, zpětnému volání a clientData vytvoří výčet jednotlivých odkazů na objekty (pokud existuje).</span><span class="sxs-lookup"><span data-stu-id="c9299-108">Given an ObjectID, callback and clientData, enumerates each object reference (if any).</span></span> |
|[<span data-ttu-id="c9299-109">Metoda IsFrozenObject</span><span class="sxs-lookup"><span data-stu-id="c9299-109">IsFrozenObject Method</span></span>](icorprofilerinfo10-isfrozenobject-method.md)|<span data-ttu-id="c9299-110">V případě objektu ObjectID určuje, zda je objekt v segmentu určeném jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="c9299-110">Given an ObjectID, determines whether the object is in a read-only segment.</span></span> |
|[<span data-ttu-id="c9299-111">Metoda GetLOHObjectSizeThreshold</span><span class="sxs-lookup"><span data-stu-id="c9299-111">GetLOHObjectSizeThreshold Method</span></span>](icorprofilerinfo10-getlohobjectsizethreshold-method.md)|<span data-ttu-id="c9299-112">Získá hodnotu nakonfigurované prahové hodnoty LOH.</span><span class="sxs-lookup"><span data-stu-id="c9299-112">Gets the value of the configured LOH threshold.</span></span> |
|[<span data-ttu-id="c9299-113">Metoda RequestReJITWithInliners</span><span class="sxs-lookup"><span data-stu-id="c9299-113">RequestReJITWithInliners Method</span></span>](icorprofilerinfo10-requestrejitwithinliners-method.md)| <span data-ttu-id="c9299-114">ReJITs požadované metody, jakož i všechny zažádané metody.</span><span class="sxs-lookup"><span data-stu-id="c9299-114">ReJITs the methods requested, as well as any inliners of the methods requested.</span></span>  |
|[<span data-ttu-id="c9299-115">Metoda SuspendRuntime</span><span class="sxs-lookup"><span data-stu-id="c9299-115">SuspendRuntime Method</span></span>](icorprofilerinfo10-suspendruntime-method.md)| <span data-ttu-id="c9299-116">Pozastaví modul runtime bez provedení GC.</span><span class="sxs-lookup"><span data-stu-id="c9299-116">Suspends the runtime without performing a GC.</span></span> |
|[<span data-ttu-id="c9299-117">Metoda ResumeRuntime</span><span class="sxs-lookup"><span data-stu-id="c9299-117">ResumeRuntime Method</span></span>](icorprofilerinfo10-resumeruntime-method.md)| <span data-ttu-id="c9299-118">Obnoví modul runtime bez provedení GC.</span><span class="sxs-lookup"><span data-stu-id="c9299-118">Resumes the runtime without performing a GC.</span></span> |

## <a name="requirements"></a><span data-ttu-id="c9299-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c9299-119">Requirements</span></span>  
<span data-ttu-id="c9299-120">**Platformy:** Viz [podporované operační systémy .NET Core](../../../core/install/dependencies.md?pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="c9299-120">**Platforms:** See [.NET Core supported operating systems](../../../core/install/dependencies.md?pivots=os-windows).</span></span>  
<span data-ttu-id="c9299-121">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="c9299-121">**Header:** CorProf.idl, CorProf.h</span></span>  
<span data-ttu-id="c9299-122">**Verze rozhraní .NET:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c9299-122">**.NET Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span></span> 

## <a name="see-also"></a><span data-ttu-id="c9299-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="c9299-123">See also</span></span>

- [<span data-ttu-id="c9299-124">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="c9299-124">Profiling Interfaces</span></span>](profiling-interfaces.md)
