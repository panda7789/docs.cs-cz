---
title: ICorProfilerInfo10 – rozhraní
ms.date: 08/06/2019
author: davmason
ms.author: davmason
ms.openlocfilehash: 4c5d553744008734037975d6e63e1b07b89cf886
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175067"
---
# <a name="icorprofilerinfo10-interface"></a><span data-ttu-id="96c37-102">ICorProfilerInfo10 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="96c37-102">ICorProfilerInfo10 Interface</span></span>

<span data-ttu-id="96c37-103">Podtřída [ICorProfilerInfo9,](icorprofilerinfo9-interface.md) která poskytuje metody pro úpravu funkce IL, informace o dotazu z běhu a pozastavení a obnovení běhu.</span><span class="sxs-lookup"><span data-stu-id="96c37-103">A subclass of [ICorProfilerInfo9](icorprofilerinfo9-interface.md) that provides methods to modify function IL, query information from the runtime, and suspend and resume the runtime.</span></span>

## <a name="methods"></a><span data-ttu-id="96c37-104">Metody</span><span class="sxs-lookup"><span data-stu-id="96c37-104">Methods</span></span>  

| <span data-ttu-id="96c37-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="96c37-105">Method</span></span>|<span data-ttu-id="96c37-106">Popis</span><span class="sxs-lookup"><span data-stu-id="96c37-106">Description</span></span>|  
| ------------|-----------------|  
|[<span data-ttu-id="96c37-107">EnumerateObjectReferences – metoda</span><span class="sxs-lookup"><span data-stu-id="96c37-107">EnumerateObjectReferences Method</span></span>](icorprofilerinfo10-enumerateobjectreferences-method.md)|<span data-ttu-id="96c37-108">Dané ObjectID, zpětné volání a clientData, vyjmenovává každý odkaz na objekt (pokud existuje).</span><span class="sxs-lookup"><span data-stu-id="96c37-108">Given an ObjectID, callback and clientData, enumerates each object reference (if any).</span></span> |
|[<span data-ttu-id="96c37-109">IsFrozenObject – metoda</span><span class="sxs-lookup"><span data-stu-id="96c37-109">IsFrozenObject Method</span></span>](icorprofilerinfo10-isfrozenobject-method.md)|<span data-ttu-id="96c37-110">Dané ObjectID, určuje, zda je objekt v segmentu jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="96c37-110">Given an ObjectID, determines whether the object is in a read-only segment.</span></span> |
|[<span data-ttu-id="96c37-111">GetLOHObjectSizeThreshold – metoda</span><span class="sxs-lookup"><span data-stu-id="96c37-111">GetLOHObjectSizeThreshold Method</span></span>](icorprofilerinfo10-getlohobjectsizethreshold-method.md)|<span data-ttu-id="96c37-112">Získá hodnotu nakonfigurované prahové hodnoty LOH.</span><span class="sxs-lookup"><span data-stu-id="96c37-112">Gets the value of the configured LOH threshold.</span></span> |
|[<span data-ttu-id="96c37-113">RequestReJITWithInliners – metoda</span><span class="sxs-lookup"><span data-stu-id="96c37-113">RequestReJITWithInliners Method</span></span>](icorprofilerinfo10-requestrejitwithinliners-method.md)| <span data-ttu-id="96c37-114">Požadované metody, jakož i všechny vložky požadovaných metod.</span><span class="sxs-lookup"><span data-stu-id="96c37-114">ReJITs the methods requested, as well as any inliners of the methods requested.</span></span>  |
|[<span data-ttu-id="96c37-115">SuspendRuntime – metoda</span><span class="sxs-lookup"><span data-stu-id="96c37-115">SuspendRuntime Method</span></span>](icorprofilerinfo10-suspendruntime-method.md)| <span data-ttu-id="96c37-116">Pozastaví dobu běhu bez provedení gc.</span><span class="sxs-lookup"><span data-stu-id="96c37-116">Suspends the runtime without performing a GC.</span></span> |
|[<span data-ttu-id="96c37-117">ResumeRuntime – metoda</span><span class="sxs-lookup"><span data-stu-id="96c37-117">ResumeRuntime Method</span></span>](icorprofilerinfo10-resumeruntime-method.md)| <span data-ttu-id="96c37-118">Obnoví dobu běhu bez provedení gc.</span><span class="sxs-lookup"><span data-stu-id="96c37-118">Resumes the runtime without performing a GC.</span></span> |

## <a name="requirements"></a><span data-ttu-id="96c37-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="96c37-119">Requirements</span></span>  
<span data-ttu-id="96c37-120">**Platformy:** Viz [operační systémy podporované rozhraním .NET Core](../../../core/install/dependencies.md?pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="96c37-120">**Platforms:** See [.NET Core supported operating systems](../../../core/install/dependencies.md?pivots=os-windows).</span></span>  
<span data-ttu-id="96c37-121">**Záhlaví:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="96c37-121">**Header:** CorProf.idl, CorProf.h</span></span>  
<span data-ttu-id="96c37-122">**Verze rozhraní .NET:**[!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span><span class="sxs-lookup"><span data-stu-id="96c37-122">**.NET Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-30-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="96c37-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="96c37-123">See also</span></span>

- [<span data-ttu-id="96c37-124">Rozhraní pro profilaci</span><span class="sxs-lookup"><span data-stu-id="96c37-124">Profiling Interfaces</span></span>](profiling-interfaces.md)
