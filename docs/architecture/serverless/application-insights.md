---
title: Aplikace bez serveru Application Insights
description: Application Insights je platforma pro diagnostiku bez serveru, která umožňuje vývojářům rozpoznávat, třídit a diagnostikovat problémy ve webových aplikacích, mobilních aplikacích, desktopových aplikacích a mikroslužbách.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 7c1013ac029645a2da44aaf1c3b6ba74ca3f3dde
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/17/2019
ms.locfileid: "72522747"
---
# <a name="telemetry-with-application-insights"></a><span data-ttu-id="50349-103">Telemetrie s Application Insights</span><span class="sxs-lookup"><span data-stu-id="50349-103">Telemetry with Application Insights</span></span>

<span data-ttu-id="50349-104">[Application Insights](https://docs.microsoft.com/azure/application-insights) je platforma pro diagnostiku bez serveru, která umožňuje vývojářům rozpoznávat, třídit a diagnostikovat problémy ve webových aplikacích, mobilních aplikacích, desktopových aplikacích a mikroslužbách.</span><span class="sxs-lookup"><span data-stu-id="50349-104">[Application Insights](https://docs.microsoft.com/azure/application-insights) is a serverless diagnostics platform that enables developers to detect, triage, and diagnose issues in web apps, mobile apps, desktop apps, and microservices.</span></span> <span data-ttu-id="50349-105">Můžete zapnout Application Insights pro aplikace Function App pouhým překlopením přepínače na portálu.</span><span class="sxs-lookup"><span data-stu-id="50349-105">You can turn on Application Insights for function apps simply by flipping a switch in the portal.</span></span> <span data-ttu-id="50349-106">Application Insights poskytuje všechny tyto možnosti, aniž byste museli konfigurovat server nebo nastavit vlastní databázi.</span><span class="sxs-lookup"><span data-stu-id="50349-106">Application Insights provides all of these capabilities without you having to configure a server or set up your own database.</span></span> <span data-ttu-id="50349-107">Všechny možnosti Application Insights se poskytují jako služba, která se automaticky integruje s vašimi aplikacemi.</span><span class="sxs-lookup"><span data-stu-id="50349-107">All of Application Insights' capabilities are provided as a service that automatically integrates with your apps.</span></span>

![Logo Application Insights](./media/application-insights-logo.png)

<span data-ttu-id="50349-109">Přidání Application Insights do stávajících aplikací je stejně snadné jako přidání klíče instrumentace do nastavení aplikace.</span><span class="sxs-lookup"><span data-stu-id="50349-109">Adding Application Insights to existing apps is as easy as adding an instrumentation key to your application's settings.</span></span> <span data-ttu-id="50349-110">Pomocí Application Insights můžete:</span><span class="sxs-lookup"><span data-stu-id="50349-110">With Application Insights you can:</span></span>

- <span data-ttu-id="50349-111">Vytvářejte vlastní grafy a výstrahy na základě metrik, jako je počet volání funkce, čas potřebný ke spuštění funkce a výjimky.</span><span class="sxs-lookup"><span data-stu-id="50349-111">Create custom charts and alerts based on metrics such as number of function invocations, the time it takes to run a function, and exceptions</span></span>
- <span data-ttu-id="50349-112">Analýza selhání a výjimek serveru</span><span class="sxs-lookup"><span data-stu-id="50349-112">Analyze failures and server exceptions</span></span>
- <span data-ttu-id="50349-113">Procházejte k podrobnostem o výkonu podle provozu a změřte čas potřebný k volání závislostí třetích stran.</span><span class="sxs-lookup"><span data-stu-id="50349-113">Drill into performance by operation and measure the time it takes to call third-party dependencies</span></span>
- <span data-ttu-id="50349-114">Monitorování využití procesoru, paměti a sazeb napříč všemi servery, které hostují aplikace Function App</span><span class="sxs-lookup"><span data-stu-id="50349-114">Monitor CPU usage, memory, and rates across all servers that host your function apps</span></span>
- <span data-ttu-id="50349-115">Zobrazení živého datového proudu metrik, včetně počtu požadavků a latence pro aplikace Function App</span><span class="sxs-lookup"><span data-stu-id="50349-115">View a live stream of metrics including request count and latency for your function apps</span></span>
- <span data-ttu-id="50349-116">Využijte funkci [Analytics](https://docs.microsoft.com/azure/application-insights/app-insights-analytics) k hledání, dotazování a vytváření vlastních grafů přes data funkcí</span><span class="sxs-lookup"><span data-stu-id="50349-116">Use [Analytics](https://docs.microsoft.com/azure/application-insights/app-insights-analytics) to search, query, and create custom charts over your function data</span></span>

![Průzkumník metrik](./media/metrics-explorer.png)

<span data-ttu-id="50349-118">Kromě integrované telemetrie je také možné vygenerovat vlastní telemetrii.</span><span class="sxs-lookup"><span data-stu-id="50349-118">In addition to built-in telemetry, it's also possible to generate custom telemetry.</span></span> <span data-ttu-id="50349-119">Následující fragment kódu vytvoří vlastního klienta telemetrie pomocí klíče instrumentace nastaveného pro aplikaci Function App:</span><span class="sxs-lookup"><span data-stu-id="50349-119">The following code snippet creates a custom telemetry client using the instrumentation key set for the function app:</span></span>

```csharp
public static TelemetryClient telemetry = new TelemetryClient()
{
    InstrumentationKey = Environment.GetEnvironmentVariable("APPINSIGHTS_INSTRUMENTATIONKEY")
};
```

<span data-ttu-id="50349-120">Následující kód měří, jak dlouho trvá vložení nového řádku do instance služby [Azure Table Storage](https://docs.microsoft.com/azure/cosmos-db/table-storage-overview) :</span><span class="sxs-lookup"><span data-stu-id="50349-120">The following code measures how long it takes to insert a new row into an [Azure Table Storage](https://docs.microsoft.com/azure/cosmos-db/table-storage-overview) instance:</span></span>

```csharp
var operation = TableOperation.Insert(entry);
var startTime = DateTime.UtcNow;
var timer = System.Diagnostics.Stopwatch.StartNew();
await table.ExecuteAsync(operation);
telemetry.TrackDependency("AzureTableStorageInsert", "Insert", startTime, timer.Elapsed, true);
```

<span data-ttu-id="50349-121">Zobrazí se výsledný graf výkonu:</span><span class="sxs-lookup"><span data-stu-id="50349-121">The resulting performance graph is shown:</span></span>

![Vlastní telemetrie](./media/custom-telemetry.png)

<span data-ttu-id="50349-123">Vlastní telemetrie odhalí průměrnou dobu vložení nového řádku je 32,6 milisekund.</span><span class="sxs-lookup"><span data-stu-id="50349-123">The custom telemetry reveals the average time to insert a new row is 32.6 milliseconds.</span></span>

<span data-ttu-id="50349-124">Application Insights poskytuje výkonný a pohodlný způsob, jak protokolovat podrobnou telemetrii k aplikacím bez serveru.</span><span class="sxs-lookup"><span data-stu-id="50349-124">Application Insights provides a powerful, convenient way to log detailed telemetry about your serverless applications.</span></span> <span data-ttu-id="50349-125">Máte plnou kontrolu nad úrovní trasování a protokolování, které je k dispozici.</span><span class="sxs-lookup"><span data-stu-id="50349-125">You have full control over the level of tracing and logging that is provided.</span></span> <span data-ttu-id="50349-126">Můžete sledovat vlastní statistiku, jako jsou události, závislosti a zobrazení stránky.</span><span class="sxs-lookup"><span data-stu-id="50349-126">You can track custom statistics such as events, dependencies, and page view.</span></span> <span data-ttu-id="50349-127">A konečně výkonná analýza vám umožní psát dotazy, které klást důležité otázky a generují grafy a rozšířené přehledy.</span><span class="sxs-lookup"><span data-stu-id="50349-127">Finally, the powerful analytics enable you to write queries that ask important questions and generate charts and advanced insights.</span></span>

<span data-ttu-id="50349-128">Další informace najdete v tématu [monitorování Azure Functions](https://docs.microsoft.com/azure/azure-functions/functions-monitoring).</span><span class="sxs-lookup"><span data-stu-id="50349-128">For more information, see [Monitor Azure Functions](https://docs.microsoft.com/azure/azure-functions/functions-monitoring).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="50349-129">[Předchozí](azure-functions.md)
>[Další](logic-apps.md)</span><span class="sxs-lookup"><span data-stu-id="50349-129">[Previous](azure-functions.md)
[Next](logic-apps.md)</span></span>
