---
title: Uvolňování paměti .NET
description: Přečtěte si o uvolňování paměti v .NET. Systém uvolňování paměti .NET spravuje přidělování a uvolňování paměti pro vaši aplikaci.
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
ms.openlocfilehash: dde0012ff7233eb7ee13efab1931f129b0eae276
ms.sourcegitcommit: 7137e12f54c4e83a94ae43ec320f8cf59c1772ea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/10/2020
ms.locfileid: "84662482"
---
# <a name="garbage-collection"></a><span data-ttu-id="46e86-104">Uvolnění paměti</span><span class="sxs-lookup"><span data-stu-id="46e86-104">Garbage collection</span></span>

<span data-ttu-id="46e86-105">. Systém uvolňování paměti sítě spravuje přidělování a uvolňování paměti pro vaši aplikaci.</span><span class="sxs-lookup"><span data-stu-id="46e86-105">.NET's garbage collector manages the allocation and release of memory for your application.</span></span> <span data-ttu-id="46e86-106">Při každém vytvoření nového objektu modul CLR přidělí objektu paměť ze spravované haldy.</span><span class="sxs-lookup"><span data-stu-id="46e86-106">Each time you create a new object, the common language runtime allocates memory for the object from the managed heap.</span></span> <span data-ttu-id="46e86-107">Dokud je ve spravované haldě k dispozici adresní prostor, modul runtime bude pokračovat v přidělování prostoru pro nové objekty.</span><span class="sxs-lookup"><span data-stu-id="46e86-107">As long as address space is available in the managed heap, the runtime continues to allocate space for new objects.</span></span> <span data-ttu-id="46e86-108">Paměť však není neomezená.</span><span class="sxs-lookup"><span data-stu-id="46e86-108">However, memory is not infinite.</span></span> <span data-ttu-id="46e86-109">Z důvodu získání paměti musí nakonec systém uvolňování paměti provést uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="46e86-109">Eventually the garbage collector must perform a collection in order to free some memory.</span></span> <span data-ttu-id="46e86-110">Optimalizující modul systému uvolňování paměti určuje nejvhodnější čas k provedení uvolnění paměti na základě způsobu přidělování paměti.</span><span class="sxs-lookup"><span data-stu-id="46e86-110">The garbage collector's optimizing engine determines the best time to perform a collection, based upon the allocations being made.</span></span> <span data-ttu-id="46e86-111">Při uvolňování paměti systém ověřuje, zda objekty ve spravované haldě již nejsou používány aplikací, a provede nezbytné úkony k opětovnému získání paměti.</span><span class="sxs-lookup"><span data-stu-id="46e86-111">When the garbage collector performs a collection, it checks for objects in the managed heap that are no longer being used by the application and performs the necessary operations to reclaim their memory.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="46e86-112">V této části</span><span class="sxs-lookup"><span data-stu-id="46e86-112">In this section</span></span>
  
|<span data-ttu-id="46e86-113">Nadpis</span><span class="sxs-lookup"><span data-stu-id="46e86-113">Title</span></span>|<span data-ttu-id="46e86-114">Popis</span><span class="sxs-lookup"><span data-stu-id="46e86-114">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="46e86-115">Základní informace o uvolňování paměti</span><span class="sxs-lookup"><span data-stu-id="46e86-115">Fundamentals of garbage collection</span></span>](fundamentals.md)|<span data-ttu-id="46e86-116">Popisuje způsob, jakým funguje systém uvolňování paměti, jakým způsobem jsou objekty přidělovány na spravované haldě, a další základní pojmy.</span><span class="sxs-lookup"><span data-stu-id="46e86-116">Describes how garbage collection works, how objects are allocated on the managed heap, and other core concepts.</span></span>|  
|[<span data-ttu-id="46e86-117">Uvolnění paměti pracovní stanice a serveru</span><span class="sxs-lookup"><span data-stu-id="46e86-117">Workstation and server garbage collection</span></span>](workstation-server-gc.md)|<span data-ttu-id="46e86-118">Popisuje rozdíly mezi uvolňováním paměti pracovní stanice pro klientské aplikace a shromažďování paměti serveru pro serverové aplikace.</span><span class="sxs-lookup"><span data-stu-id="46e86-118">Describes the differences between workstation garbage collection for client apps and server garbage collection for server apps.</span></span>|
|[<span data-ttu-id="46e86-119">Uvolňování paměti na pozadí</span><span class="sxs-lookup"><span data-stu-id="46e86-119">Background garbage collection</span></span>](background-gc.md)|<span data-ttu-id="46e86-120">Popisuje shromažďování paměti na pozadí, což je kolekce objektů generace 0 a 1, zatímco probíhá shromažďování 2. generace.</span><span class="sxs-lookup"><span data-stu-id="46e86-120">Describes background garbage collection, which is the collection of generation 0 and 1 objects while generation 2 collection is in progress.</span></span>|
|[<span data-ttu-id="46e86-121">Halda pro velké objekty</span><span class="sxs-lookup"><span data-stu-id="46e86-121">The large object heap</span></span>](large-object-heap.md)|<span data-ttu-id="46e86-122">Popisuje haldu rozsáhlých objektů (LOH) a jak velké objekty jsou uvolněny z paměti.</span><span class="sxs-lookup"><span data-stu-id="46e86-122">Describes the large object heap (LOH) and how large objects are garbage-collected.</span></span>|
|[<span data-ttu-id="46e86-123">Uvolňování paměti a výkon</span><span class="sxs-lookup"><span data-stu-id="46e86-123">Garbage collection and performance</span></span>](performance.md)|<span data-ttu-id="46e86-124">Popisuje kontroly výkonu, které slouží k diagnostice problémů uvolňování paměti a výkonu.</span><span class="sxs-lookup"><span data-stu-id="46e86-124">Describes the performance checks you can use to diagnose garbage collection and performance issues.</span></span>|  
|[<span data-ttu-id="46e86-125">Vyvolané kolekce</span><span class="sxs-lookup"><span data-stu-id="46e86-125">Induced collections</span></span>](induced.md)|<span data-ttu-id="46e86-126">Popisuje způsob aktivace uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="46e86-126">Describes how to make a garbage collection occur.</span></span>|  
|[<span data-ttu-id="46e86-127">Režimy latence</span><span class="sxs-lookup"><span data-stu-id="46e86-127">Latency modes</span></span>](latency.md)|<span data-ttu-id="46e86-128">Popisuje režimy, které určují parametry systému uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="46e86-128">Describes the modes that determine the intrusiveness of garbage collection.</span></span>|  
|[<span data-ttu-id="46e86-129">Optimalizace pro sdílené hostování webů</span><span class="sxs-lookup"><span data-stu-id="46e86-129">Optimization for shared web hosting</span></span>](optimization-for-shared-web-hosting.md)|<span data-ttu-id="46e86-130">Popisuje způsob optimalizace uvolňování paměti na serverech, které jsou sdíleny několika malými weby.</span><span class="sxs-lookup"><span data-stu-id="46e86-130">Describes how to optimize garbage collection on servers shared by several small Web sites.</span></span>|  
|[<span data-ttu-id="46e86-131">Oznámení o uvolňování paměti</span><span class="sxs-lookup"><span data-stu-id="46e86-131">Garbage collection notifications</span></span>](notifications.md)|<span data-ttu-id="46e86-132">Popisuje, jakým způsobem lze zjistit, kdy se blíží termín úplného uvolňování paměti a kdy bude uvolňování dokončeno.</span><span class="sxs-lookup"><span data-stu-id="46e86-132">Describes how to determine when a full garbage collection is approaching and when it has completed.</span></span>|  
|[<span data-ttu-id="46e86-133">Sledování prostředků domény aplikace</span><span class="sxs-lookup"><span data-stu-id="46e86-133">Application domain resource monitoring</span></span>](app-domain-resource-monitoring.md)|<span data-ttu-id="46e86-134">Popisuje sledování využití procesoru a paměti doménou aplikace.</span><span class="sxs-lookup"><span data-stu-id="46e86-134">Describes how to monitor CPU and memory usage by an application domain.</span></span>|  
|[<span data-ttu-id="46e86-135">Slabé odkazy</span><span class="sxs-lookup"><span data-stu-id="46e86-135">Weak references</span></span>](weak-references.md)|<span data-ttu-id="46e86-136">Popisuje funkce, které systému uvolňování paměti umožňují získat paměť objektu a zároveň podporují přístup aplikace k danému objektu.</span><span class="sxs-lookup"><span data-stu-id="46e86-136">Describes features that permit the garbage collector to collect an object while still allowing the application to access that object.</span></span>|  
  
## <a name="reference"></a><span data-ttu-id="46e86-137">Referenční informace</span><span class="sxs-lookup"><span data-stu-id="46e86-137">Reference</span></span>

- <xref:System.GC?displayProperty=nameWithType>  
- <xref:System.GCCollectionMode?displayProperty=nameWithType>  
- <xref:System.GCNotificationStatus?displayProperty=nameWithType>  
- <xref:System.Runtime.GCLatencyMode?displayProperty=nameWithType>  
- <xref:System.Runtime.GCSettings?displayProperty=nameWithType>  
- <xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode%2A?displayProperty=nameWithType>  
- <xref:System.Object.Finalize%2A?displayProperty=nameWithType>  
- <xref:System.IDisposable?displayProperty=nameWithType>  
  
## <a name="see-also"></a><span data-ttu-id="46e86-138">Viz také</span><span class="sxs-lookup"><span data-stu-id="46e86-138">See also</span></span>

- [<span data-ttu-id="46e86-139">Vyčištění nespravovaných prostředků</span><span class="sxs-lookup"><span data-stu-id="46e86-139">Clean up unmanaged resources</span></span>](unmanaged.md)
