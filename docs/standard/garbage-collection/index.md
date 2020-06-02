---
title: Uvolňování paměti .NET
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
ms.openlocfilehash: ef7e078c6ef2f0b4081c49aa0db09316e79f0702
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84286051"
---
# <a name="garbage-collection"></a><span data-ttu-id="dc6e6-102">Uvolnění paměti</span><span class="sxs-lookup"><span data-stu-id="dc6e6-102">Garbage collection</span></span>

<span data-ttu-id="dc6e6-103">. Systém uvolňování paměti sítě spravuje přidělování a uvolňování paměti pro vaši aplikaci.</span><span class="sxs-lookup"><span data-stu-id="dc6e6-103">.NET's garbage collector manages the allocation and release of memory for your application.</span></span> <span data-ttu-id="dc6e6-104">Při každém vytvoření nového objektu modul CLR přidělí objektu paměť ze spravované haldy.</span><span class="sxs-lookup"><span data-stu-id="dc6e6-104">Each time you create a new object, the common language runtime allocates memory for the object from the managed heap.</span></span> <span data-ttu-id="dc6e6-105">Dokud je ve spravované haldě k dispozici adresní prostor, modul runtime bude pokračovat v přidělování prostoru pro nové objekty.</span><span class="sxs-lookup"><span data-stu-id="dc6e6-105">As long as address space is available in the managed heap, the runtime continues to allocate space for new objects.</span></span> <span data-ttu-id="dc6e6-106">Paměť však není neomezená.</span><span class="sxs-lookup"><span data-stu-id="dc6e6-106">However, memory is not infinite.</span></span> <span data-ttu-id="dc6e6-107">Z důvodu získání paměti musí nakonec systém uvolňování paměti provést uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="dc6e6-107">Eventually the garbage collector must perform a collection in order to free some memory.</span></span> <span data-ttu-id="dc6e6-108">Optimalizující modul systému uvolňování paměti určuje nejvhodnější čas k provedení uvolnění paměti na základě způsobu přidělování paměti.</span><span class="sxs-lookup"><span data-stu-id="dc6e6-108">The garbage collector's optimizing engine determines the best time to perform a collection, based upon the allocations being made.</span></span> <span data-ttu-id="dc6e6-109">Při uvolňování paměti systém ověřuje, zda objekty ve spravované haldě již nejsou používány aplikací, a provede nezbytné úkony k opětovnému získání paměti.</span><span class="sxs-lookup"><span data-stu-id="dc6e6-109">When the garbage collector performs a collection, it checks for objects in the managed heap that are no longer being used by the application and performs the necessary operations to reclaim their memory.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="dc6e6-110">V této části</span><span class="sxs-lookup"><span data-stu-id="dc6e6-110">In this section</span></span>
  
|<span data-ttu-id="dc6e6-111">Nadpis</span><span class="sxs-lookup"><span data-stu-id="dc6e6-111">Title</span></span>|<span data-ttu-id="dc6e6-112">Popis</span><span class="sxs-lookup"><span data-stu-id="dc6e6-112">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="dc6e6-113">Základní informace o uvolňování paměti</span><span class="sxs-lookup"><span data-stu-id="dc6e6-113">Fundamentals of garbage collection</span></span>](fundamentals.md)|<span data-ttu-id="dc6e6-114">Popisuje způsob, jakým funguje systém uvolňování paměti, jakým způsobem jsou objekty přidělovány na spravované haldě, a další základní pojmy.</span><span class="sxs-lookup"><span data-stu-id="dc6e6-114">Describes how garbage collection works, how objects are allocated on the managed heap, and other core concepts.</span></span>|  
|[<span data-ttu-id="dc6e6-115">Uvolnění paměti pracovní stanice a serveru</span><span class="sxs-lookup"><span data-stu-id="dc6e6-115">Workstation and server garbage collection</span></span>](workstation-server-gc.md)|<span data-ttu-id="dc6e6-116">Popisuje rozdíly mezi uvolňováním paměti pracovní stanice pro klientské aplikace a shromažďování paměti serveru pro serverové aplikace.</span><span class="sxs-lookup"><span data-stu-id="dc6e6-116">Describes the differences between workstation garbage collection for client apps and server garbage collection for server apps.</span></span>|
|[<span data-ttu-id="dc6e6-117">Uvolňování paměti na pozadí</span><span class="sxs-lookup"><span data-stu-id="dc6e6-117">Background garbage collection</span></span>](background-gc.md)|<span data-ttu-id="dc6e6-118">Popisuje shromažďování paměti na pozadí, což je kolekce objektů generace 0 a 1, zatímco probíhá shromažďování 2. generace.</span><span class="sxs-lookup"><span data-stu-id="dc6e6-118">Describes background garbage collection, which is the collection of generation 0 and 1 objects while generation 2 collection is in progress.</span></span>|
|[<span data-ttu-id="dc6e6-119">Halda pro velké objekty</span><span class="sxs-lookup"><span data-stu-id="dc6e6-119">The large object heap</span></span>](large-object-heap.md)|<span data-ttu-id="dc6e6-120">Popisuje haldu rozsáhlých objektů (LOH) a jak velké objekty jsou uvolněny z paměti.</span><span class="sxs-lookup"><span data-stu-id="dc6e6-120">Describes the large object heap (LOH) and how large objects are garbage-collected.</span></span>|
|[<span data-ttu-id="dc6e6-121">Uvolňování paměti a výkon</span><span class="sxs-lookup"><span data-stu-id="dc6e6-121">Garbage collection and performance</span></span>](performance.md)|<span data-ttu-id="dc6e6-122">Popisuje kontroly výkonu, které slouží k diagnostice problémů uvolňování paměti a výkonu.</span><span class="sxs-lookup"><span data-stu-id="dc6e6-122">Describes the performance checks you can use to diagnose garbage collection and performance issues.</span></span>|  
|[<span data-ttu-id="dc6e6-123">Vyvolané kolekce</span><span class="sxs-lookup"><span data-stu-id="dc6e6-123">Induced collections</span></span>](induced.md)|<span data-ttu-id="dc6e6-124">Popisuje způsob aktivace uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="dc6e6-124">Describes how to make a garbage collection occur.</span></span>|  
|[<span data-ttu-id="dc6e6-125">Režimy latence</span><span class="sxs-lookup"><span data-stu-id="dc6e6-125">Latency modes</span></span>](latency.md)|<span data-ttu-id="dc6e6-126">Popisuje režimy, které určují parametry systému uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="dc6e6-126">Describes the modes that determine the intrusiveness of garbage collection.</span></span>|  
|[<span data-ttu-id="dc6e6-127">Optimalizace pro sdílené hostování webů</span><span class="sxs-lookup"><span data-stu-id="dc6e6-127">Optimization for shared web hosting</span></span>](optimization-for-shared-web-hosting.md)|<span data-ttu-id="dc6e6-128">Popisuje způsob optimalizace uvolňování paměti na serverech, které jsou sdíleny několika malými weby.</span><span class="sxs-lookup"><span data-stu-id="dc6e6-128">Describes how to optimize garbage collection on servers shared by several small Web sites.</span></span>|  
|[<span data-ttu-id="dc6e6-129">Oznámení o uvolňování paměti</span><span class="sxs-lookup"><span data-stu-id="dc6e6-129">Garbage collection notifications</span></span>](notifications.md)|<span data-ttu-id="dc6e6-130">Popisuje, jakým způsobem lze zjistit, kdy se blíží termín úplného uvolňování paměti a kdy bude uvolňování dokončeno.</span><span class="sxs-lookup"><span data-stu-id="dc6e6-130">Describes how to determine when a full garbage collection is approaching and when it has completed.</span></span>|  
|[<span data-ttu-id="dc6e6-131">Sledování prostředků domény aplikace</span><span class="sxs-lookup"><span data-stu-id="dc6e6-131">Application domain resource monitoring</span></span>](app-domain-resource-monitoring.md)|<span data-ttu-id="dc6e6-132">Popisuje sledování využití procesoru a paměti doménou aplikace.</span><span class="sxs-lookup"><span data-stu-id="dc6e6-132">Describes how to monitor CPU and memory usage by an application domain.</span></span>|  
|[<span data-ttu-id="dc6e6-133">Slabé odkazy</span><span class="sxs-lookup"><span data-stu-id="dc6e6-133">Weak references</span></span>](weak-references.md)|<span data-ttu-id="dc6e6-134">Popisuje funkce, které systému uvolňování paměti umožňují získat paměť objektu a zároveň podporují přístup aplikace k danému objektu.</span><span class="sxs-lookup"><span data-stu-id="dc6e6-134">Describes features that permit the garbage collector to collect an object while still allowing the application to access that object.</span></span>|  
  
## <a name="reference"></a><span data-ttu-id="dc6e6-135">Odkaz</span><span class="sxs-lookup"><span data-stu-id="dc6e6-135">Reference</span></span>

- <xref:System.GC?displayProperty=nameWithType>  
- <xref:System.GCCollectionMode?displayProperty=nameWithType>  
- <xref:System.GCNotificationStatus?displayProperty=nameWithType>  
- <xref:System.Runtime.GCLatencyMode?displayProperty=nameWithType>  
- <xref:System.Runtime.GCSettings?displayProperty=nameWithType>  
- <xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode%2A?displayProperty=nameWithType>  
- <xref:System.Object.Finalize%2A?displayProperty=nameWithType>  
- <xref:System.IDisposable?displayProperty=nameWithType>  
  
## <a name="see-also"></a><span data-ttu-id="dc6e6-136">Viz také</span><span class="sxs-lookup"><span data-stu-id="dc6e6-136">See also</span></span>

- [<span data-ttu-id="dc6e6-137">Vyčištění nespravovaných prostředků</span><span class="sxs-lookup"><span data-stu-id="dc6e6-137">Clean up unmanaged resources</span></span>](unmanaged.md)
