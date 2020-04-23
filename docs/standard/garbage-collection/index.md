---
title: Uvolňování paměti rozhraní .NET
ms.date: 04/21/2020
ms.technology: dotnet-standard
helpviewer_keywords:
- memory, garbage collection
- garbage collection, automatic memory management
- GC [.NET Framework]
- memory, allocating
- common language runtime, garbage collection
- garbage collector
- cleanup operations
- garbage collection
- memory, releasing
- common language runtime, automatic memory management
- automatic memory management
- runtime, automatic memory management
- runtime, garbage collection
- garbage collection, about
ms.assetid: 22b6cb97-0c80-4eeb-a2cf-5ed7655e37f9
ms.openlocfilehash: c087deb033a373dd8b3980feb7ec6901c7909569
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102239"
---
# <a name="garbage-collection"></a><span data-ttu-id="13c2b-102">Uvolnění paměti</span><span class="sxs-lookup"><span data-stu-id="13c2b-102">Garbage collection</span></span>

<span data-ttu-id="13c2b-103">. NET systém uvolňování paměti spravuje přidělení a uvolnění paměti pro vaši aplikaci.</span><span class="sxs-lookup"><span data-stu-id="13c2b-103">.NET's garbage collector manages the allocation and release of memory for your application.</span></span> <span data-ttu-id="13c2b-104">Při každém vytvoření nového objektu modul CLR přidělí objektu paměť ze spravované haldy.</span><span class="sxs-lookup"><span data-stu-id="13c2b-104">Each time you create a new object, the common language runtime allocates memory for the object from the managed heap.</span></span> <span data-ttu-id="13c2b-105">Dokud je ve spravované haldě k dispozici adresní prostor, modul runtime bude pokračovat v přidělování prostoru pro nové objekty.</span><span class="sxs-lookup"><span data-stu-id="13c2b-105">As long as address space is available in the managed heap, the runtime continues to allocate space for new objects.</span></span> <span data-ttu-id="13c2b-106">Paměť však není neomezená.</span><span class="sxs-lookup"><span data-stu-id="13c2b-106">However, memory is not infinite.</span></span> <span data-ttu-id="13c2b-107">Z důvodu získání paměti musí nakonec systém uvolňování paměti provést uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="13c2b-107">Eventually the garbage collector must perform a collection in order to free some memory.</span></span> <span data-ttu-id="13c2b-108">Optimalizující modul systému uvolňování paměti určuje nejvhodnější čas k provedení uvolnění paměti na základě způsobu přidělování paměti.</span><span class="sxs-lookup"><span data-stu-id="13c2b-108">The garbage collector's optimizing engine determines the best time to perform a collection, based upon the allocations being made.</span></span> <span data-ttu-id="13c2b-109">Při uvolňování paměti systém ověřuje, zda objekty ve spravované haldě již nejsou používány aplikací, a provede nezbytné úkony k opětovnému získání paměti.</span><span class="sxs-lookup"><span data-stu-id="13c2b-109">When the garbage collector performs a collection, it checks for objects in the managed heap that are no longer being used by the application and performs the necessary operations to reclaim their memory.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="13c2b-110">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="13c2b-110">In this section</span></span>
  
|<span data-ttu-id="13c2b-111">Nadpis</span><span class="sxs-lookup"><span data-stu-id="13c2b-111">Title</span></span>|<span data-ttu-id="13c2b-112">Popis</span><span class="sxs-lookup"><span data-stu-id="13c2b-112">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="13c2b-113">Základy uvolňování paměti</span><span class="sxs-lookup"><span data-stu-id="13c2b-113">Fundamentals of garbage collection</span></span>](../../../docs/standard/garbage-collection/fundamentals.md)|<span data-ttu-id="13c2b-114">Popisuje způsob, jakým funguje systém uvolňování paměti, jakým způsobem jsou objekty přidělovány na spravované haldě, a další základní pojmy.</span><span class="sxs-lookup"><span data-stu-id="13c2b-114">Describes how garbage collection works, how objects are allocated on the managed heap, and other core concepts.</span></span>|  
|[<span data-ttu-id="13c2b-115">Uvolňování paměti pracovní stanice a serveru</span><span class="sxs-lookup"><span data-stu-id="13c2b-115">Workstation and server garbage collection</span></span>](workstation-server-gc.md)|<span data-ttu-id="13c2b-116">Popisuje rozdíly mezi uvolňování paměti pracovní stanice pro klientské aplikace a uvolňování paměti serveru pro serverové aplikace.</span><span class="sxs-lookup"><span data-stu-id="13c2b-116">Describes the differences between workstation garbage collection for client apps and server garbage collection for server apps.</span></span>|
|[<span data-ttu-id="13c2b-117">Uvolňování paměti na pozadí</span><span class="sxs-lookup"><span data-stu-id="13c2b-117">Background garbage collection</span></span>](background-gc.md)|<span data-ttu-id="13c2b-118">Popisuje uvolňování paměti na pozadí, což je kolekce generace 0 a 1 objekty, zatímco generace 2 kolekce probíhá.</span><span class="sxs-lookup"><span data-stu-id="13c2b-118">Describes background garbage collection, which is the collection of generation 0 and 1 objects while generation 2 collection is in progress.</span></span>|
|[<span data-ttu-id="13c2b-119">Halda velkého objektu</span><span class="sxs-lookup"><span data-stu-id="13c2b-119">The large object heap</span></span>](large-object-heap.md)|<span data-ttu-id="13c2b-120">Popisuje haldy velkých objektů (LOH) a jak velké objekty jsou uvolněny.</span><span class="sxs-lookup"><span data-stu-id="13c2b-120">Describes the large object heap (LOH) and how large objects are garbage-collected.</span></span>|
|[<span data-ttu-id="13c2b-121">Uvolňování paměti a výkon</span><span class="sxs-lookup"><span data-stu-id="13c2b-121">Garbage collection and performance</span></span>](../../../docs/standard/garbage-collection/performance.md)|<span data-ttu-id="13c2b-122">Popisuje kontroly výkonu, které slouží k diagnostice problémů uvolňování paměti a výkonu.</span><span class="sxs-lookup"><span data-stu-id="13c2b-122">Describes the performance checks you can use to diagnose garbage collection and performance issues.</span></span>|  
|[<span data-ttu-id="13c2b-123">Vyvolané kolekce</span><span class="sxs-lookup"><span data-stu-id="13c2b-123">Induced collections</span></span>](../../../docs/standard/garbage-collection/induced.md)|<span data-ttu-id="13c2b-124">Popisuje způsob aktivace uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="13c2b-124">Describes how to make a garbage collection occur.</span></span>|  
|[<span data-ttu-id="13c2b-125">Režimy latence</span><span class="sxs-lookup"><span data-stu-id="13c2b-125">Latency modes</span></span>](../../../docs/standard/garbage-collection/latency.md)|<span data-ttu-id="13c2b-126">Popisuje režimy, které určují parametry systému uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="13c2b-126">Describes the modes that determine the intrusiveness of garbage collection.</span></span>|  
|[<span data-ttu-id="13c2b-127">Optimalizace pro sdílené hostování webů</span><span class="sxs-lookup"><span data-stu-id="13c2b-127">Optimization for shared web hosting</span></span>](../../../docs/standard/garbage-collection/optimization-for-shared-web-hosting.md)|<span data-ttu-id="13c2b-128">Popisuje způsob optimalizace uvolňování paměti na serverech, které jsou sdíleny několika malými weby.</span><span class="sxs-lookup"><span data-stu-id="13c2b-128">Describes how to optimize garbage collection on servers shared by several small Web sites.</span></span>|  
|[<span data-ttu-id="13c2b-129">Oznámení o uvolňování paměti</span><span class="sxs-lookup"><span data-stu-id="13c2b-129">Garbage collection notifications</span></span>](../../../docs/standard/garbage-collection/notifications.md)|<span data-ttu-id="13c2b-130">Popisuje, jakým způsobem lze zjistit, kdy se blíží termín úplného uvolňování paměti a kdy bude uvolňování dokončeno.</span><span class="sxs-lookup"><span data-stu-id="13c2b-130">Describes how to determine when a full garbage collection is approaching and when it has completed.</span></span>|  
|[<span data-ttu-id="13c2b-131">Sledování prostředků domény aplikace</span><span class="sxs-lookup"><span data-stu-id="13c2b-131">Application domain resource monitoring</span></span>](../../../docs/standard/garbage-collection/app-domain-resource-monitoring.md)|<span data-ttu-id="13c2b-132">Popisuje sledování využití procesoru a paměti doménou aplikace.</span><span class="sxs-lookup"><span data-stu-id="13c2b-132">Describes how to monitor CPU and memory usage by an application domain.</span></span>|  
|[<span data-ttu-id="13c2b-133">Slabé odkazy</span><span class="sxs-lookup"><span data-stu-id="13c2b-133">Weak references</span></span>](../../../docs/standard/garbage-collection/weak-references.md)|<span data-ttu-id="13c2b-134">Popisuje funkce, které systému uvolňování paměti umožňují získat paměť objektu a zároveň podporují přístup aplikace k danému objektu.</span><span class="sxs-lookup"><span data-stu-id="13c2b-134">Describes features that permit the garbage collector to collect an object while still allowing the application to access that object.</span></span>|  
  
## <a name="reference"></a><span data-ttu-id="13c2b-135">Referenční informace</span><span class="sxs-lookup"><span data-stu-id="13c2b-135">Reference</span></span>

- <xref:System.GC?displayProperty=nameWithType>  
- <xref:System.GCCollectionMode?displayProperty=nameWithType>  
- <xref:System.GCNotificationStatus?displayProperty=nameWithType>  
- <xref:System.Runtime.GCLatencyMode?displayProperty=nameWithType>  
- <xref:System.Runtime.GCSettings?displayProperty=nameWithType>  
- <xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode%2A?displayProperty=nameWithType>  
- <xref:System.Object.Finalize%2A?displayProperty=nameWithType>  
- <xref:System.IDisposable?displayProperty=nameWithType>  
  
## <a name="see-also"></a><span data-ttu-id="13c2b-136">Viz také</span><span class="sxs-lookup"><span data-stu-id="13c2b-136">See also</span></span>

- [<span data-ttu-id="13c2b-137">Vyčištění nespravovaných prostředků</span><span class="sxs-lookup"><span data-stu-id="13c2b-137">Clean up unmanaged resources</span></span>](../../../docs/standard/garbage-collection/unmanaged.md)
