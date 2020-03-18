---
title: Application Insights – aplikace bez serveru
description: Application Insights je diagnostická platforma bez serveru, která vývojářům umožňuje detekovat, tíspat a diagnostikovat problémy ve webových aplikacích, mobilních aplikacích, desktopových aplikacích a mikroslužbách.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 7c1013ac029645a2da44aaf1c3b6ba74ca3f3dde
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "72522747"
---
# <a name="telemetry-with-application-insights"></a><span data-ttu-id="b9524-103">Telemetrie s Application Insights</span><span class="sxs-lookup"><span data-stu-id="b9524-103">Telemetry with Application Insights</span></span>

<span data-ttu-id="b9524-104">[Application Insights](https://docs.microsoft.com/azure/application-insights) je diagnostická platforma bez serveru, která vývojářům umožňuje detekovat, tíspat a diagnostikovat problémy ve webových aplikacích, mobilních aplikacích, desktopových aplikacích a mikroslužbách.</span><span class="sxs-lookup"><span data-stu-id="b9524-104">[Application Insights](https://docs.microsoft.com/azure/application-insights) is a serverless diagnostics platform that enables developers to detect, triage, and diagnose issues in web apps, mobile apps, desktop apps, and microservices.</span></span> <span data-ttu-id="b9524-105">Application Insights pro funkční aplikace můžete zapnout jednoduše přepnutím přepínače na portálu.</span><span class="sxs-lookup"><span data-stu-id="b9524-105">You can turn on Application Insights for function apps simply by flipping a switch in the portal.</span></span> <span data-ttu-id="b9524-106">Application Insights poskytuje všechny tyto funkce, aniž byste museli konfigurovat server nebo nastavit vlastní databázi.</span><span class="sxs-lookup"><span data-stu-id="b9524-106">Application Insights provides all of these capabilities without you having to configure a server or set up your own database.</span></span> <span data-ttu-id="b9524-107">Všechny funkce Application Insights jsou poskytovány jako služba, která se automaticky integruje s vašimi aplikacemi.</span><span class="sxs-lookup"><span data-stu-id="b9524-107">All of Application Insights' capabilities are provided as a service that automatically integrates with your apps.</span></span>

![Logo Application Insights](./media/application-insights-logo.png)

<span data-ttu-id="b9524-109">Přidání Application Insights do existujících aplikací je stejně snadné jako přidání klíče instrumentace do nastavení vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="b9524-109">Adding Application Insights to existing apps is as easy as adding an instrumentation key to your application's settings.</span></span> <span data-ttu-id="b9524-110">S Application Insights můžete:</span><span class="sxs-lookup"><span data-stu-id="b9524-110">With Application Insights you can:</span></span>

- <span data-ttu-id="b9524-111">Vytvoření vlastních grafů a výstrah na základě metrik, jako je počet vyvolání funkcí, doba potřebný ke spuštění funkce a výjimky</span><span class="sxs-lookup"><span data-stu-id="b9524-111">Create custom charts and alerts based on metrics such as number of function invocations, the time it takes to run a function, and exceptions</span></span>
- <span data-ttu-id="b9524-112">Analýza chyb a výjimek serveru</span><span class="sxs-lookup"><span data-stu-id="b9524-112">Analyze failures and server exceptions</span></span>
- <span data-ttu-id="b9524-113">Procházet výkon podle provozu a měřit čas potřebný k volání závislostí třetích stran</span><span class="sxs-lookup"><span data-stu-id="b9524-113">Drill into performance by operation and measure the time it takes to call third-party dependencies</span></span>
- <span data-ttu-id="b9524-114">Sledování využití procesoru, paměti a sazeb na všech serverech, které hostují vaše funkční aplikace</span><span class="sxs-lookup"><span data-stu-id="b9524-114">Monitor CPU usage, memory, and rates across all servers that host your function apps</span></span>
- <span data-ttu-id="b9524-115">Zobrazení živého datového proudu metrik včetně počtu žádostí a latence pro aplikace funkcí</span><span class="sxs-lookup"><span data-stu-id="b9524-115">View a live stream of metrics including request count and latency for your function apps</span></span>
- <span data-ttu-id="b9524-116">Použití [služby Analytics](https://docs.microsoft.com/azure/application-insights/app-insights-analytics) k vyhledávání, dotazování a vytváření vlastních grafů nad daty funkcí</span><span class="sxs-lookup"><span data-stu-id="b9524-116">Use [Analytics](https://docs.microsoft.com/azure/application-insights/app-insights-analytics) to search, query, and create custom charts over your function data</span></span>

![Průzkumník metrik](./media/metrics-explorer.png)

<span data-ttu-id="b9524-118">Kromě vestavěné telemetrie je také možné generovat vlastní telemetrii.</span><span class="sxs-lookup"><span data-stu-id="b9524-118">In addition to built-in telemetry, it's also possible to generate custom telemetry.</span></span> <span data-ttu-id="b9524-119">Následující fragment kódu vytvoří vlastní klienta telemetrie pomocí sady klíčů instrumentace pro aplikaci funkce:</span><span class="sxs-lookup"><span data-stu-id="b9524-119">The following code snippet creates a custom telemetry client using the instrumentation key set for the function app:</span></span>

```csharp
public static TelemetryClient telemetry = new TelemetryClient()
{
    InstrumentationKey = Environment.GetEnvironmentVariable("APPINSIGHTS_INSTRUMENTATIONKEY")
};
```

<span data-ttu-id="b9524-120">Následující kód měří, jak dlouho trvá vložení nového řádku do instance [Azure Table Storage:](https://docs.microsoft.com/azure/cosmos-db/table-storage-overview)</span><span class="sxs-lookup"><span data-stu-id="b9524-120">The following code measures how long it takes to insert a new row into an [Azure Table Storage](https://docs.microsoft.com/azure/cosmos-db/table-storage-overview) instance:</span></span>

```csharp
var operation = TableOperation.Insert(entry);
var startTime = DateTime.UtcNow;
var timer = System.Diagnostics.Stopwatch.StartNew();
await table.ExecuteAsync(operation);
telemetry.TrackDependency("AzureTableStorageInsert", "Insert", startTime, timer.Elapsed, true);
```

<span data-ttu-id="b9524-121">Výsledný graf výkonu je zobrazen:</span><span class="sxs-lookup"><span data-stu-id="b9524-121">The resulting performance graph is shown:</span></span>

![Vlastní telemetrická data](./media/custom-telemetry.png)

<span data-ttu-id="b9524-123">Vlastní telemetrie odhaluje průměrná doba pro vložení nového řádku je 32,6 milisekund.</span><span class="sxs-lookup"><span data-stu-id="b9524-123">The custom telemetry reveals the average time to insert a new row is 32.6 milliseconds.</span></span>

<span data-ttu-id="b9524-124">Application Insights poskytuje výkonný a pohodlný způsob protokolování podrobné telemetrie o aplikacích bez serveru.</span><span class="sxs-lookup"><span data-stu-id="b9524-124">Application Insights provides a powerful, convenient way to log detailed telemetry about your serverless applications.</span></span> <span data-ttu-id="b9524-125">Máte plnou kontrolu nad úrovní trasování a protokolování, která je k dispozici.</span><span class="sxs-lookup"><span data-stu-id="b9524-125">You have full control over the level of tracing and logging that is provided.</span></span> <span data-ttu-id="b9524-126">Můžete sledovat vlastní statistiky, jako jsou události, závislosti a zobrazení stránky.</span><span class="sxs-lookup"><span data-stu-id="b9524-126">You can track custom statistics such as events, dependencies, and page view.</span></span> <span data-ttu-id="b9524-127">A konečně, výkonná analytika umožňuje psát dotazy, které kladou důležité otázky a generují grafy a pokročilé přehledy.</span><span class="sxs-lookup"><span data-stu-id="b9524-127">Finally, the powerful analytics enable you to write queries that ask important questions and generate charts and advanced insights.</span></span>

<span data-ttu-id="b9524-128">Další informace naleznete v [tématu Sledování funkcí Azure](https://docs.microsoft.com/azure/azure-functions/functions-monitoring).</span><span class="sxs-lookup"><span data-stu-id="b9524-128">For more information, see [Monitor Azure Functions](https://docs.microsoft.com/azure/azure-functions/functions-monitoring).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="b9524-129">[Předchozí](azure-functions.md)
>[další](logic-apps.md)</span><span class="sxs-lookup"><span data-stu-id="b9524-129">[Previous](azure-functions.md)
[Next](logic-apps.md)</span></span>
