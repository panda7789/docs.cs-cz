---
title: Trasování a ladění schématu nastavení
ms.date: 03/30/2017
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
ms.openlocfilehash: 037d08b33e9aa6a64d236b36ebcf821b604b03df
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "69927123"
---
# <a name="trace-and-debug-settings-schema"></a><span data-ttu-id="e8a79-102">Trasování a ladění schématu nastavení</span><span class="sxs-lookup"><span data-stu-id="e8a79-102">Trace and Debug Settings Schema</span></span>
<span data-ttu-id="e8a79-103">Nastavení trasování a ladění určují naslouchací procesy trasování, které shromažďují, ukládají a směrují zprávy a úroveň, kde je nastaven přepínač trasování.</span><span class="sxs-lookup"><span data-stu-id="e8a79-103">Trace and debug settings specify trace listeners that collect, store, and route messages, and the level where a trace switch is set.</span></span>  
  
 <span data-ttu-id="e8a79-104">Následující tabulka popisuje funkci každého prvku nastavení trasování a ladění.</span><span class="sxs-lookup"><span data-stu-id="e8a79-104">The following table describes the function of each trace and debug settings element.</span></span>  
  
|<span data-ttu-id="e8a79-105">Prvek</span><span class="sxs-lookup"><span data-stu-id="e8a79-105">Element</span></span>|<span data-ttu-id="e8a79-106">Description</span><span class="sxs-lookup"><span data-stu-id="e8a79-106">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add-element-for-listeners-for-source.md)|<span data-ttu-id="e8a79-107">Přidá naslouchací proces do `Listeners` kolekce pro zdroj trasování.</span><span class="sxs-lookup"><span data-stu-id="e8a79-107">Adds a listener to the `Listeners` collection for a trace source.</span></span>|  
|[\<add>](add-element-for-listeners-for-trace.md)|<span data-ttu-id="e8a79-108">Přidá naslouchací proces do `Listeners` kolekce.</span><span class="sxs-lookup"><span data-stu-id="e8a79-108">Adds a listener to the `Listeners` collection.</span></span>|  
|[\<add>](add-element-for-sharedlisteners.md)|<span data-ttu-id="e8a79-109">Přidá naslouchací proces do `sharedListeners` kolekce.</span><span class="sxs-lookup"><span data-stu-id="e8a79-109">Adds a listener to the `sharedListeners` collection.</span></span>|  
|[\<add>](add-element-for-switches.md)|<span data-ttu-id="e8a79-110">Určuje úroveň, kde je nastaven přepínač trasování.</span><span class="sxs-lookup"><span data-stu-id="e8a79-110">Specifies the level where a trace switch is set.</span></span>|  
|[\<assert>](assert-element.md)|<span data-ttu-id="e8a79-111">Určuje, zda se má při volání metody zobrazit okno se zprávou <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> . určuje také název souboru, do kterého budou zapsány zprávy.</span><span class="sxs-lookup"><span data-stu-id="e8a79-111">Specifies whether to display a message box when you call the <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> method; also specifies the name of the file to write messages to.</span></span>|  
|[\<clear>](clear-element-for-listeners-for-source.md)|<span data-ttu-id="e8a79-112">Vymaže `Listeners` kolekci zdroje trasování.</span><span class="sxs-lookup"><span data-stu-id="e8a79-112">Clears the `Listeners` collection for a trace source.</span></span>|  
|[\<clear>](clear-element-for-listeners-for-trace.md)|<span data-ttu-id="e8a79-113">Vymaže `Listeners` kolekci pro Trace.</span><span class="sxs-lookup"><span data-stu-id="e8a79-113">Clears the `Listeners` collection for trace.</span></span>|  
|[\<filter>](filter-element-for-add-for-listeners-for-source.md)|<span data-ttu-id="e8a79-114">Přidá filtr do naslouchacího procesu v `Listeners` kolekci pro zdroj trasování.</span><span class="sxs-lookup"><span data-stu-id="e8a79-114">Adds a filter to a listener in the `Listeners` collection for a trace source.</span></span>|  
|[\<filter>](filter-element-for-add-for-listeners-for-trace.md)|<span data-ttu-id="e8a79-115">Přidá filtr do naslouchacího procesu v `Listeners` kolekci pro trasování.</span><span class="sxs-lookup"><span data-stu-id="e8a79-115">Adds a filter to a listener in the `Listeners` collection for trace.</span></span>|  
|[\<filter>](filter-element-for-add-for-sharedlisteners.md)|<span data-ttu-id="e8a79-116">Přidá filtr do naslouchacího procesu v `sharedListeners` kolekci.</span><span class="sxs-lookup"><span data-stu-id="e8a79-116">Adds a filter to a listener in the `sharedListeners` collection.</span></span>|  
|[\<listeners>](listeners-element-for-source.md)|<span data-ttu-id="e8a79-117">Určuje naslouchací procesy pro `Listeners` kolekci pro zdroj trasování.</span><span class="sxs-lookup"><span data-stu-id="e8a79-117">Specifies listeners for the `Listeners` collection for a trace source.</span></span>|  
|[\<listeners>](listeners-element-for-trace.md)|<span data-ttu-id="e8a79-118">Určuje naslouchací procesy pro `Listeners` kolekci pro trasování.</span><span class="sxs-lookup"><span data-stu-id="e8a79-118">Specifies listeners for the `Listeners` collection for trace.</span></span>|  
|[\<performanceCounters>](performancecounters-element.md)|<span data-ttu-id="e8a79-119">Určuje velikost globální paměti sdílené čítači výkonu.</span><span class="sxs-lookup"><span data-stu-id="e8a79-119">Specifies the size of the global memory shared by performance counters.</span></span>|  
|[\<remove>](remove-element-for-listeners-for-trace.md)|<span data-ttu-id="e8a79-120">Odebere naslouchací proces z `Listeners` kolekce pro trasování.</span><span class="sxs-lookup"><span data-stu-id="e8a79-120">Removes a listener from the `Listeners` collection for trace.</span></span>|  
|[\<remove>](remove-element-for-listeners-for-source.md)|<span data-ttu-id="e8a79-121">Odebere naslouchací proces z `Listeners` kolekce pro zdroj trasování.</span><span class="sxs-lookup"><span data-stu-id="e8a79-121">Removes a listener from the `Listeners` collection for a trace source.</span></span>|  
|[\<sharedListeners>](sharedlisteners-element.md)|<span data-ttu-id="e8a79-122">Obsahuje naslouchací procesy, na které může odkazovat jakýkoliv element source nebo Trace.</span><span class="sxs-lookup"><span data-stu-id="e8a79-122">Contains listeners that any source or trace element can reference.</span></span>|  
|[\<sources>](sources-element.md)|<span data-ttu-id="e8a79-123">Obsahuje zdroje trasování, které spouštějí trasovací zprávy.</span><span class="sxs-lookup"><span data-stu-id="e8a79-123">Contains trace sources that initiate tracing messages.</span></span>|  
|[\<source>](source-element.md)|<span data-ttu-id="e8a79-124">Určuje zdroj trasování, který inicializuje trasovací zprávy.</span><span class="sxs-lookup"><span data-stu-id="e8a79-124">Specifies a trace source that initiates tracing messages.</span></span>|  
|[\<switches>](switches-element.md)|<span data-ttu-id="e8a79-125">Obsahuje přepínače trasování a úroveň, kde jsou nastaveny přepínače trasování.</span><span class="sxs-lookup"><span data-stu-id="e8a79-125">Contains trace switches and the level where the trace switches are set.</span></span>|  
|[\<system.diagnostics>](system-diagnostics-element.md)|<span data-ttu-id="e8a79-126">Určuje naslouchací procesy trasování, které shromažďují, ukládají a směrují zprávy a úroveň, kde je nastaven přepínač trasování.</span><span class="sxs-lookup"><span data-stu-id="e8a79-126">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|[\<trace>](trace-element.md)|<span data-ttu-id="e8a79-127">Obsahuje naslouchací procesy, které shromažďují, ukládají a směrují trasovací zprávy.</span><span class="sxs-lookup"><span data-stu-id="e8a79-127">Contains listeners that collect, store, and route tracing messages.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e8a79-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="e8a79-128">See also</span></span>

- <xref:System.Diagnostics.Trace>
- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.Debug>
- [<span data-ttu-id="e8a79-129">Schéma konfiguračního souboru</span><span class="sxs-lookup"><span data-stu-id="e8a79-129">Configuration File Schema</span></span>](../index.md)
