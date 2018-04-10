---
title: Trasování a ladění schématu nastavení
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- tracing [.NET Framework], trace and debug settings schema
- configuration schema [.NET Framework], trace and debug settings
- configuration settings [.NET Framework], tracing
- schema configuration settings
- configuration settings [.NET Framework], debugging
- trace listeners, trace and debug settings schema
- configuration sections [.NET Framework]
- elements [.NET Framework], trace and debug settings
ms.assetid: 277ca5f6-e1c4-41b6-a47f-3a67ce5b94ac
caps.latest.revision: 14
author: mcleblanc
ms.author: markl
manager: markl
ms.workload:
- dotnet
ms.openlocfilehash: e6d9e5ca97e4d5940dd9de3f3ffbd4db4183196c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="trace-and-debug-settings-schema"></a><span data-ttu-id="28cc2-102">Trasování a ladění schématu nastavení</span><span class="sxs-lookup"><span data-stu-id="28cc2-102">Trace and Debug Settings Schema</span></span>
<span data-ttu-id="28cc2-103">Nastavení trasování a ladění zadejte naslouchací procesy trasování, které shromažďování, ukládání a směrování zpráv a úroveň, kde je nastaven na přepínač trasování.</span><span class="sxs-lookup"><span data-stu-id="28cc2-103">Trace and debug settings specify trace listeners that collect, store, and route messages, and the level where a trace switch is set.</span></span>  
  
 <span data-ttu-id="28cc2-104">Následující tabulka popisuje funkci jednotlivých prvků nastavení trasování a ladění.</span><span class="sxs-lookup"><span data-stu-id="28cc2-104">The following table describes the function of each trace and debug settings element.</span></span>  
  
|<span data-ttu-id="28cc2-105">Prvek</span><span class="sxs-lookup"><span data-stu-id="28cc2-105">Element</span></span>|<span data-ttu-id="28cc2-106">Popis</span><span class="sxs-lookup"><span data-stu-id="28cc2-106">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="28cc2-107">\<Přidat ></span><span class="sxs-lookup"><span data-stu-id="28cc2-107">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/add-element-for-listeners-for-source.md)|<span data-ttu-id="28cc2-108">Přidá naslouchací proces a `Listeners` kolekce zdroje trasování.</span><span class="sxs-lookup"><span data-stu-id="28cc2-108">Adds a listener to the `Listeners` collection for a trace source.</span></span>|  
|[<span data-ttu-id="28cc2-109">\<Přidat ></span><span class="sxs-lookup"><span data-stu-id="28cc2-109">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/add-element-for-listeners-for-trace.md)|<span data-ttu-id="28cc2-110">Přidá naslouchací proces a `Listeners` kolekce.</span><span class="sxs-lookup"><span data-stu-id="28cc2-110">Adds a listener to the `Listeners` collection.</span></span>|  
|[<span data-ttu-id="28cc2-111">\<Přidat ></span><span class="sxs-lookup"><span data-stu-id="28cc2-111">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/add-element-for-sharedlisteners.md)|<span data-ttu-id="28cc2-112">Přidá naslouchací proces a `sharedListeners` kolekce.</span><span class="sxs-lookup"><span data-stu-id="28cc2-112">Adds a listener to the `sharedListeners` collection.</span></span>|  
|[<span data-ttu-id="28cc2-113">\<Přidat ></span><span class="sxs-lookup"><span data-stu-id="28cc2-113">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/add-element-for-switches.md)|<span data-ttu-id="28cc2-114">Určuje úroveň, kde je nastaven na přepínač trasování.</span><span class="sxs-lookup"><span data-stu-id="28cc2-114">Specifies the level where a trace switch is set.</span></span>|  
|[<span data-ttu-id="28cc2-115">\<Assert – ></span><span class="sxs-lookup"><span data-stu-id="28cc2-115">\<assert></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/assert-element.md)|<span data-ttu-id="28cc2-116">Určuje, jestli se má zobrazit okno se zprávou při volání <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> metoda; také určuje název souboru pro zápis zprávy.</span><span class="sxs-lookup"><span data-stu-id="28cc2-116">Specifies whether to display a message box when you call the <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> method; also specifies the name of the file to write messages to.</span></span>|  
|[<span data-ttu-id="28cc2-117">\<Clear ></span><span class="sxs-lookup"><span data-stu-id="28cc2-117">\<clear></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/clear-element-for-listeners-for-source.md)|<span data-ttu-id="28cc2-118">Vymaže `Listeners` kolekce zdroje trasování.</span><span class="sxs-lookup"><span data-stu-id="28cc2-118">Clears the `Listeners` collection for a trace source.</span></span>|  
|[<span data-ttu-id="28cc2-119">\<Clear ></span><span class="sxs-lookup"><span data-stu-id="28cc2-119">\<clear></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/clear-element-for-listeners-for-trace.md)|<span data-ttu-id="28cc2-120">Vymaže `Listeners` kolekce pro trasování.</span><span class="sxs-lookup"><span data-stu-id="28cc2-120">Clears the `Listeners` collection for trace.</span></span>|  
|[<span data-ttu-id="28cc2-121">\<Filtr ></span><span class="sxs-lookup"><span data-stu-id="28cc2-121">\<filter></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/filter-element-for-add-for-listeners-for-source.md)|<span data-ttu-id="28cc2-122">Přidá filtr do naslouchací proces ve `Listeners` kolekce zdroje trasování.</span><span class="sxs-lookup"><span data-stu-id="28cc2-122">Adds a filter to a listener in the `Listeners` collection for a trace source.</span></span>|  
|[<span data-ttu-id="28cc2-123">\<Filtr ></span><span class="sxs-lookup"><span data-stu-id="28cc2-123">\<filter></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/filter-element-for-add-for-listeners-for-trace.md)|<span data-ttu-id="28cc2-124">Přidá filtr do naslouchací proces ve `Listeners` kolekce pro trasování.</span><span class="sxs-lookup"><span data-stu-id="28cc2-124">Adds a filter to a listener in the `Listeners` collection for trace.</span></span>|  
|[<span data-ttu-id="28cc2-125">\<Filtr ></span><span class="sxs-lookup"><span data-stu-id="28cc2-125">\<filter></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/filter-element-for-add-for-sharedlisteners.md)|<span data-ttu-id="28cc2-126">Přidá filtr do naslouchací proces ve `sharedListeners` kolekce.</span><span class="sxs-lookup"><span data-stu-id="28cc2-126">Adds a filter to a listener in the `sharedListeners` collection.</span></span>|  
|[<span data-ttu-id="28cc2-127">\<moduly pro naslouchání ></span><span class="sxs-lookup"><span data-stu-id="28cc2-127">\<listeners></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/listeners-element-for-source.md)|<span data-ttu-id="28cc2-128">Určuje naslouchací procesy pro `Listeners` kolekce zdroje trasování.</span><span class="sxs-lookup"><span data-stu-id="28cc2-128">Specifies listeners for the `Listeners` collection for a trace source.</span></span>|  
|[<span data-ttu-id="28cc2-129">\<moduly pro naslouchání ></span><span class="sxs-lookup"><span data-stu-id="28cc2-129">\<listeners></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/listeners-element-for-trace.md)|<span data-ttu-id="28cc2-130">Určuje naslouchací procesy pro `Listeners` kolekce pro trasování.</span><span class="sxs-lookup"><span data-stu-id="28cc2-130">Specifies listeners for the `Listeners` collection for trace.</span></span>|  
|[<span data-ttu-id="28cc2-131">\<čítače výkonu ></span><span class="sxs-lookup"><span data-stu-id="28cc2-131">\<performanceCounters></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/performancecounters-element.md)|<span data-ttu-id="28cc2-132">Určuje velikost globální paměť sdíleny čítače výkonu.</span><span class="sxs-lookup"><span data-stu-id="28cc2-132">Specifies the size of the global memory shared by performance counters.</span></span>|  
|[<span data-ttu-id="28cc2-133">\<Odebrat ></span><span class="sxs-lookup"><span data-stu-id="28cc2-133">\<remove></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/remove-element-for-listeners-for-trace.md)|<span data-ttu-id="28cc2-134">Odebere naslouchací proces z `Listeners` kolekce pro trasování.</span><span class="sxs-lookup"><span data-stu-id="28cc2-134">Removes a listener from the `Listeners` collection for trace.</span></span>|  
|[<span data-ttu-id="28cc2-135">\<Odebrat ></span><span class="sxs-lookup"><span data-stu-id="28cc2-135">\<remove></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/remove-element-for-listeners-for-source.md)|<span data-ttu-id="28cc2-136">Odebere naslouchací proces z `Listeners` kolekce zdroje trasování.</span><span class="sxs-lookup"><span data-stu-id="28cc2-136">Removes a listener from the `Listeners` collection for a trace source.</span></span>|  
|[<span data-ttu-id="28cc2-137">\<sharedListeners ></span><span class="sxs-lookup"><span data-stu-id="28cc2-137">\<sharedListeners></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sharedlisteners-element.md)|<span data-ttu-id="28cc2-138">Obsahuje naslouchací procesy, které může odkazovat všechny zdroje nebo element trasování.</span><span class="sxs-lookup"><span data-stu-id="28cc2-138">Contains listeners that any source or trace element can reference.</span></span>|  
|[<span data-ttu-id="28cc2-139">\<zdroje ></span><span class="sxs-lookup"><span data-stu-id="28cc2-139">\<sources></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/sources-element.md)|<span data-ttu-id="28cc2-140">Obsahuje trasování zdrojů, které zahájí trasování zpráv.</span><span class="sxs-lookup"><span data-stu-id="28cc2-140">Contains trace sources that initiate tracing messages.</span></span>|  
|[<span data-ttu-id="28cc2-141">\<zdroj ></span><span class="sxs-lookup"><span data-stu-id="28cc2-141">\<source></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/source-element.md)|<span data-ttu-id="28cc2-142">Určuje zdroj trasování, který iniciuje trasování zpráv.</span><span class="sxs-lookup"><span data-stu-id="28cc2-142">Specifies a trace source that initiates tracing messages.</span></span>|  
|[<span data-ttu-id="28cc2-143">\<přepínače ></span><span class="sxs-lookup"><span data-stu-id="28cc2-143">\<switches></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/switches-element.md)|<span data-ttu-id="28cc2-144">Obsahuje trasování – přepínače a úroveň, kde jsou nastaveny trasování – přepínače.</span><span class="sxs-lookup"><span data-stu-id="28cc2-144">Contains trace switches and the level where the trace switches are set.</span></span>|  
|[<span data-ttu-id="28cc2-145">\<System.Diagnostics ></span><span class="sxs-lookup"><span data-stu-id="28cc2-145">\<system.diagnostics></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/system-diagnostics-element.md)|<span data-ttu-id="28cc2-146">Určuje naslouchací procesy trasování, které shromažďování, ukládání a směrování zpráv a úroveň, kde je nastaven na přepínač trasování.</span><span class="sxs-lookup"><span data-stu-id="28cc2-146">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|[<span data-ttu-id="28cc2-147">\<trasování ></span><span class="sxs-lookup"><span data-stu-id="28cc2-147">\<trace></span></span>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/trace-element.md)|<span data-ttu-id="28cc2-148">Obsahuje naslouchací procesy, které shromažďování, ukládání a směrovat trasovací zprávy.</span><span class="sxs-lookup"><span data-stu-id="28cc2-148">Contains listeners that collect, store, and route tracing messages.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="28cc2-149">Viz také</span><span class="sxs-lookup"><span data-stu-id="28cc2-149">See Also</span></span>  
 <xref:System.Diagnostics.Trace>  
 <xref:System.Diagnostics.TraceSource>  
 <xref:System.Diagnostics.Debug>  
 [<span data-ttu-id="28cc2-150">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="28cc2-150">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)
