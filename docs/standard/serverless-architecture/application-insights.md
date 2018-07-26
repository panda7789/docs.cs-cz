---
title: Application Insights – aplikace bez serveru
description: Application Insights je platforma bez serveru diagnostiku, která vývojářům umožňuje zjišťovat, posuzovat a diagnostikovat problémy ve webových aplikacích, mobilních aplikací, aplikací klasické pracovní plochy a mikroslužeb.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 57b1f70825251c48f720dcd78d094f5e8fb1edb8
ms.sourcegitcommit: 4c158beee818c408d45a9609bfc06f209a523e22
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/03/2018
ms.locfileid: "37404894"
---
# <a name="telemetry-with-application-insights"></a><span data-ttu-id="1f83c-103">Telemetrie pomocí Application Insights</span><span class="sxs-lookup"><span data-stu-id="1f83c-103">Telemetry with Application Insights</span></span>

<span data-ttu-id="1f83c-104">[Application Insights](https://docs.microsoft.com/azure/application-insights) je platforma bez serveru diagnostiku, která vývojářům umožňuje zjišťovat, posuzovat a diagnostikovat problémy ve webových aplikacích, mobilních aplikací, aplikací klasické pracovní plochy a mikroslužeb.</span><span class="sxs-lookup"><span data-stu-id="1f83c-104">[Application Insights](https://docs.microsoft.com/azure/application-insights) is a serverless diagnostics platform that enables developers to detect, triage, and diagnose issues in web apps, mobile apps, desktop apps, and microservices.</span></span> <span data-ttu-id="1f83c-105">Jednoduše tak, že slouží přepínač na portálu můžete zapnout Application Insights pro aplikace function App.</span><span class="sxs-lookup"><span data-stu-id="1f83c-105">You can turn on Application Insights for function apps simply by flipping a switch in the portal.</span></span> <span data-ttu-id="1f83c-106">Application Insights poskytuje všechny tyto funkce, aniž by bylo nutné nakonfigurovat server nebo nastavit vlastní databázi.</span><span class="sxs-lookup"><span data-stu-id="1f83c-106">Application Insights provides all of these capabilities without you having to configure a server or set up your own database.</span></span> <span data-ttu-id="1f83c-107">Všechny funkce služby Application Insights jsou k dispozici jako služba, která se automaticky integruje s vašimi aplikacemi.</span><span class="sxs-lookup"><span data-stu-id="1f83c-107">All of Application Insights' capabilities are provided as a service that automatically integrates with your apps.</span></span>

![Application Insights logo](./media/application-insights-logo.png)

<span data-ttu-id="1f83c-109">Přidání Application Insights do stávajících aplikací je stejně jednoduché jako přidání Instrumentační klíč nastavení aplikace.</span><span class="sxs-lookup"><span data-stu-id="1f83c-109">Adding Application Insights to existing apps is as easy as adding an instrumentation key to your application's settings.</span></span> <span data-ttu-id="1f83c-110">Application Insights vám umožní:</span><span class="sxs-lookup"><span data-stu-id="1f83c-110">With Application Insights you can:</span></span>

* <span data-ttu-id="1f83c-111">Vytvoření vlastních grafů a výstrah na základě metrik, jako je počet volání funkce, čas potřebný ke spuštění funkce a výjimky</span><span class="sxs-lookup"><span data-stu-id="1f83c-111">Create custom charts and alerts based on metrics such as number of function invocations, the time it takes to run a function, and exceptions</span></span>
* <span data-ttu-id="1f83c-112">Analýza chyb a výjimek serveru</span><span class="sxs-lookup"><span data-stu-id="1f83c-112">Analyze failures and server exceptions</span></span>
* <span data-ttu-id="1f83c-113">Přejít k podrobnostem výkonu operací a měří čas potřebný k volání závislostí třetích stran</span><span class="sxs-lookup"><span data-stu-id="1f83c-113">Drill into performance by operation and measure the time it takes to call third-party dependencies</span></span>
* <span data-ttu-id="1f83c-114">Monitorování využití procesoru, paměti a rychlosti ve všech serverech, které jsou hostiteli vaše aplikace function App</span><span class="sxs-lookup"><span data-stu-id="1f83c-114">Monitor CPU usage, memory, and rates across all servers that host your function apps</span></span>
* <span data-ttu-id="1f83c-115">Zobrazit živý stream metrik, včetně počet požadavků a latencí pro vaše aplikace function App</span><span class="sxs-lookup"><span data-stu-id="1f83c-115">View a live stream of metrics including request count and latency for your function apps</span></span>
* <span data-ttu-id="1f83c-116">Použití [Analytics](https://docs.microsoft.com/azure/application-insights/app-insights-analytics) pro hledání, dotazování a vytvářet vlastní grafy vašich dat – funkce</span><span class="sxs-lookup"><span data-stu-id="1f83c-116">Use [Analytics](https://docs.microsoft.com/azure/application-insights/app-insights-analytics) to search, query, and create custom charts over your function data</span></span>

![Průzkumník metrik](./media/metrics-explorer.png)

<span data-ttu-id="1f83c-118">Kromě předdefinovaných telemetrická data je také možné generovat vlastní telemetrii.</span><span class="sxs-lookup"><span data-stu-id="1f83c-118">In addition to built-in telemetry, it's also possible to generate custom telemetry.</span></span> <span data-ttu-id="1f83c-119">Následující fragment kódu vytvoří vlastní telemetrická data klienta pomocí Instrumentační klíč nastavení aplikace function App:</span><span class="sxs-lookup"><span data-stu-id="1f83c-119">The following code snippet creates a custom telemetry client using the instrumentation key set for the function app:</span></span>

```csharp
public static TelemetryClient telemetry = new TelemetryClient()
{
    InstrumentationKey = Environment.GetEnvironmentVariable("APPINSIGHTS_INSTRUMENTATIONKEY")
};
```

<span data-ttu-id="1f83c-120">Následující kód opatření, jak dlouho trvá vložit nový řádek do [Azure Table Storage](https://docs.microsoft.com/azure/cosmos-db/table-storage-overview) instance:</span><span class="sxs-lookup"><span data-stu-id="1f83c-120">The following code measures how long it takes to insert a new row into an [Azure Table Storage](https://docs.microsoft.com/azure/cosmos-db/table-storage-overview) instance:</span></span>

```csharp
var operation = TableOperation.Insert(entry);
var startTime = DateTime.UtcNow;
var timer = System.Diagnostics.Stopwatch.StartNew();
await table.ExecuteAsync(operation);
telemetry.TrackDependency("AzureTableStorageInsert", "Insert", startTime, timer.Elapsed, true);
```

<span data-ttu-id="1f83c-121">Výsledný graf výkonu se zobrazí:</span><span class="sxs-lookup"><span data-stu-id="1f83c-121">The resulting performance graph is shown:</span></span>

![Vlastní telemetrii](./media/custom-telemetry.png)

<span data-ttu-id="1f83c-123">Vlastní telemetrii odhalí, že průměrná doba vložte nový řádek je 32.6 milisekund.</span><span class="sxs-lookup"><span data-stu-id="1f83c-123">The custom telemetry reveals the average time to insert a new row is 32.6 milliseconds.</span></span>

<span data-ttu-id="1f83c-124">Application Insights poskytuje efektivní a pohodlný způsob, jak protokolovat podrobné telemetrie o vaší aplikace bez serveru.</span><span class="sxs-lookup"><span data-stu-id="1f83c-124">Application Insights provides a powerful, convenient way to log detailed telemetry about your serverless applications.</span></span> <span data-ttu-id="1f83c-125">Máte plnou kontrolu nad úrovní trasování a protokolování, které je k dispozici.</span><span class="sxs-lookup"><span data-stu-id="1f83c-125">You have full control over the level of tracing and logging that is provided.</span></span> <span data-ttu-id="1f83c-126">Můžete sledovat vlastní statistiky, jako jsou události, závislosti a zobrazení stránky.</span><span class="sxs-lookup"><span data-stu-id="1f83c-126">You can track custom statistics such as events, dependencies, and page view.</span></span> <span data-ttu-id="1f83c-127">Nakonec výkonné analýzy vám umožňují psát dotazy, které důležité Ptejte se a generovat grafy a pokročilých přehledů.</span><span class="sxs-lookup"><span data-stu-id="1f83c-127">Finally, the powerful analytics enable you to write queries that ask important questions and generate charts and advanced insights.</span></span>

<span data-ttu-id="1f83c-128">Další informace najdete v tématu [monitorování Azure Functions](https://docs.microsoft.com/azure/azure-functions/functions-monitoring).</span><span class="sxs-lookup"><span data-stu-id="1f83c-128">For more information, see [Monitor Azure Functions](https://docs.microsoft.com/azure/azure-functions/functions-monitoring).</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="1f83c-129">[Předchozí](azure-functions.md)
[další](logic-apps.md)</span><span class="sxs-lookup"><span data-stu-id="1f83c-129">[Previous](azure-functions.md)
[Next](logic-apps.md)</span></span>