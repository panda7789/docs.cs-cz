---
title: ICorProfilerInfo10 – rozhraní
ms.date: 08/06/2019
author: davmason
ms.author: davmason
ms.openlocfilehash: f2bc716110c14972e5b2c32bceb3123b16e87c61
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449841"
---
# <a name="icorprofilerinfo10-interface"></a><span data-ttu-id="4f66b-102">ICorProfilerInfo10 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="4f66b-102">ICorProfilerInfo10 Interface</span></span>

<span data-ttu-id="4f66b-103">Podtřída [ICorProfilerInfo9](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo9-interface.md) , která poskytuje metody pro úpravu Il funkce, dotazování na informace z modulu runtime a pozastavení a obnovení modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="4f66b-103">A subclass of [ICorProfilerInfo9](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo9-interface.md) that provides methods to modify function IL, query information from the runtime, and suspend and resume the runtime.</span></span>

## <a name="methods"></a><span data-ttu-id="4f66b-104">Metody</span><span class="sxs-lookup"><span data-stu-id="4f66b-104">Methods</span></span>  

| <span data-ttu-id="4f66b-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="4f66b-105">Method</span></span>|<span data-ttu-id="4f66b-106">Popis</span><span class="sxs-lookup"><span data-stu-id="4f66b-106">Description</span></span>|  
| ------------|-----------------|  
|[<span data-ttu-id="4f66b-107">Metoda EnumerateObjectReferences</span><span class="sxs-lookup"><span data-stu-id="4f66b-107">EnumerateObjectReferences Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-enumerateobjectreferences-method.md)|<span data-ttu-id="4f66b-108">Po předaném identifikátoru ObjectID, zpětnému volání a clientData vytvoří výčet jednotlivých odkazů na objekty (pokud existuje).</span><span class="sxs-lookup"><span data-stu-id="4f66b-108">Given an ObjectID, callback and clientData, enumerates each object reference (if any).</span></span> |
|[<span data-ttu-id="4f66b-109">Metoda IsFrozenObject</span><span class="sxs-lookup"><span data-stu-id="4f66b-109">IsFrozenObject Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-isfrozenobject-method.md)|<span data-ttu-id="4f66b-110">V případě objektu ObjectID určuje, zda je objekt v segmentu určeném jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="4f66b-110">Given an ObjectID, determines whether the object is in a read-only segment.</span></span> |
|[<span data-ttu-id="4f66b-111">Metoda GetLOHObjectSizeThreshold</span><span class="sxs-lookup"><span data-stu-id="4f66b-111">GetLOHObjectSizeThreshold Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-getlohobjectsizethreshold-method.md)|<span data-ttu-id="4f66b-112">Získá hodnotu nakonfigurované prahové hodnoty LOH.</span><span class="sxs-lookup"><span data-stu-id="4f66b-112">Gets the value of the configured LOH threshold.</span></span> |
|[<span data-ttu-id="4f66b-113">Metoda RequestReJITWithInliners</span><span class="sxs-lookup"><span data-stu-id="4f66b-113">RequestReJITWithInliners Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-requestrejitwithinliners-method.md)| <span data-ttu-id="4f66b-114">ReJITs požadované metody, jakož i všechny zažádané metody.</span><span class="sxs-lookup"><span data-stu-id="4f66b-114">ReJITs the methods requested, as well as any inliners of the methods requested.</span></span>  |
|[<span data-ttu-id="4f66b-115">Metoda SuspendRuntime</span><span class="sxs-lookup"><span data-stu-id="4f66b-115">SuspendRuntime Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-suspendruntime-method.md)| <span data-ttu-id="4f66b-116">Pozastaví modul runtime bez provedení GC.</span><span class="sxs-lookup"><span data-stu-id="4f66b-116">Suspends the runtime without performing a GC.</span></span> |
|[<span data-ttu-id="4f66b-117">Metoda ResumeRuntime</span><span class="sxs-lookup"><span data-stu-id="4f66b-117">ResumeRuntime Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo10-resumeruntime-method.md)| <span data-ttu-id="4f66b-118">Obnoví modul runtime bez provedení GC.</span><span class="sxs-lookup"><span data-stu-id="4f66b-118">Resumes the runtime without performing a GC.</span></span> |

## <a name="requirements"></a><span data-ttu-id="4f66b-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4f66b-119">Requirements</span></span>  
<span data-ttu-id="4f66b-120">**Platformy:** Viz [podporované operační systémy .NET Core](../../../core/install/dependencies.md?tabs=netcore30&pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="4f66b-120">**Platforms:** See [.NET Core supported operating systems](../../../core/install/dependencies.md?tabs=netcore30&pivots=os-windows).</span></span>  
<span data-ttu-id="4f66b-121">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="4f66b-121">**Header:** CorProf.idl, CorProf.h</span></span>  
<span data-ttu-id="4f66b-122">**Verze rozhraní .NET:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4f66b-122">**.NET Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span></span> 

## <a name="see-also"></a><span data-ttu-id="4f66b-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4f66b-123">See also</span></span>

- [<span data-ttu-id="4f66b-124">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="4f66b-124">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
