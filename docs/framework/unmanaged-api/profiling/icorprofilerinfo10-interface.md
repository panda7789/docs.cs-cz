---
title: ICorProfilerInfo10 – rozhraní
ms.date: 08/06/2019
author: davmason
ms.author: davmason
ms.openlocfilehash: e90a1ffbc037636e4296bbd4f4c3c5082885e9f3
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76863241"
---
# <a name="icorprofilerinfo10-interface"></a><span data-ttu-id="d74e7-102">ICorProfilerInfo10 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d74e7-102">ICorProfilerInfo10 Interface</span></span>

<span data-ttu-id="d74e7-103">Podtřída [ICorProfilerInfo9](icorprofilerinfo9-interface.md) , která poskytuje metody pro úpravu Il funkce, dotazování na informace z modulu runtime a pozastavení a obnovení modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="d74e7-103">A subclass of [ICorProfilerInfo9](icorprofilerinfo9-interface.md) that provides methods to modify function IL, query information from the runtime, and suspend and resume the runtime.</span></span>

## <a name="methods"></a><span data-ttu-id="d74e7-104">Metody</span><span class="sxs-lookup"><span data-stu-id="d74e7-104">Methods</span></span>  

| <span data-ttu-id="d74e7-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="d74e7-105">Method</span></span>|<span data-ttu-id="d74e7-106">Popis</span><span class="sxs-lookup"><span data-stu-id="d74e7-106">Description</span></span>|  
| ------------|-----------------|  
|[<span data-ttu-id="d74e7-107">Metoda EnumerateObjectReferences</span><span class="sxs-lookup"><span data-stu-id="d74e7-107">EnumerateObjectReferences Method</span></span>](icorprofilerinfo10-enumerateobjectreferences-method.md)|<span data-ttu-id="d74e7-108">Po předaném identifikátoru ObjectID, zpětnému volání a clientData vytvoří výčet jednotlivých odkazů na objekty (pokud existuje).</span><span class="sxs-lookup"><span data-stu-id="d74e7-108">Given an ObjectID, callback and clientData, enumerates each object reference (if any).</span></span> |
|[<span data-ttu-id="d74e7-109">Metoda IsFrozenObject</span><span class="sxs-lookup"><span data-stu-id="d74e7-109">IsFrozenObject Method</span></span>](icorprofilerinfo10-isfrozenobject-method.md)|<span data-ttu-id="d74e7-110">V případě objektu ObjectID určuje, zda je objekt v segmentu určeném jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="d74e7-110">Given an ObjectID, determines whether the object is in a read-only segment.</span></span> |
|[<span data-ttu-id="d74e7-111">Metoda GetLOHObjectSizeThreshold</span><span class="sxs-lookup"><span data-stu-id="d74e7-111">GetLOHObjectSizeThreshold Method</span></span>](icorprofilerinfo10-getlohobjectsizethreshold-method.md)|<span data-ttu-id="d74e7-112">Získá hodnotu nakonfigurované prahové hodnoty LOH.</span><span class="sxs-lookup"><span data-stu-id="d74e7-112">Gets the value of the configured LOH threshold.</span></span> |
|[<span data-ttu-id="d74e7-113">Metoda RequestReJITWithInliners</span><span class="sxs-lookup"><span data-stu-id="d74e7-113">RequestReJITWithInliners Method</span></span>](icorprofilerinfo10-requestrejitwithinliners-method.md)| <span data-ttu-id="d74e7-114">ReJITs požadované metody, jakož i všechny zažádané metody.</span><span class="sxs-lookup"><span data-stu-id="d74e7-114">ReJITs the methods requested, as well as any inliners of the methods requested.</span></span>  |
|[<span data-ttu-id="d74e7-115">Metoda SuspendRuntime</span><span class="sxs-lookup"><span data-stu-id="d74e7-115">SuspendRuntime Method</span></span>](icorprofilerinfo10-suspendruntime-method.md)| <span data-ttu-id="d74e7-116">Pozastaví modul runtime bez provedení GC.</span><span class="sxs-lookup"><span data-stu-id="d74e7-116">Suspends the runtime without performing a GC.</span></span> |
|[<span data-ttu-id="d74e7-117">Metoda ResumeRuntime</span><span class="sxs-lookup"><span data-stu-id="d74e7-117">ResumeRuntime Method</span></span>](icorprofilerinfo10-resumeruntime-method.md)| <span data-ttu-id="d74e7-118">Obnoví modul runtime bez provedení GC.</span><span class="sxs-lookup"><span data-stu-id="d74e7-118">Resumes the runtime without performing a GC.</span></span> |

## <a name="requirements"></a><span data-ttu-id="d74e7-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d74e7-119">Requirements</span></span>  
<span data-ttu-id="d74e7-120">**Platformy:** Viz [podporované operační systémy .NET Core](../../../core/install/dependencies.md?tabs=netcore30&pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="d74e7-120">**Platforms:** See [.NET Core supported operating systems](../../../core/install/dependencies.md?tabs=netcore30&pivots=os-windows).</span></span>  
<span data-ttu-id="d74e7-121">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="d74e7-121">**Header:** CorProf.idl, CorProf.h</span></span>  
<span data-ttu-id="d74e7-122">**Verze rozhraní .NET:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d74e7-122">**.NET Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span></span> 

## <a name="see-also"></a><span data-ttu-id="d74e7-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d74e7-123">See also</span></span>

- [<span data-ttu-id="d74e7-124">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="d74e7-124">Profiling Interfaces</span></span>](profiling-interfaces.md)
