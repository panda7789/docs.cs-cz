---
title: Měření výkonu pomocí EventCounters v .NET Core
description: V tomto kurzu se dozvíte, jak změřit výkon pomocí EventCounters.
ms.date: 08/07/2020
ms.topic: tutorial
ms.openlocfilehash: 7b4940e17d01e7ec5a50d11e3c818ecdec2d48cf
ms.sourcegitcommit: 1e6439ec4d5889fc08cf3bfb4dac2b91931eb827
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/08/2020
ms.locfileid: "88025009"
---
# <a name="tutorial-measure-performance-using-eventcounters-in-net-core"></a><span data-ttu-id="12dc8-103">Kurz: měření výkonu pomocí EventCounters v .NET Core</span><span class="sxs-lookup"><span data-stu-id="12dc8-103">Tutorial: Measure performance using EventCounters in .NET Core</span></span>

<span data-ttu-id="12dc8-104">**Tento článek se týká: ✔️** .net Core 3,0 SDK a novějších verzí</span><span class="sxs-lookup"><span data-stu-id="12dc8-104">**This article applies to: ✔️** .NET Core 3.0 SDK and later versions</span></span>

<span data-ttu-id="12dc8-105">V tomto kurzu se dozvíte, jak <xref:System.Diagnostics.Tracing.EventCounter> lze použít k měření výkonu s vysokou četností událostí.</span><span class="sxs-lookup"><span data-stu-id="12dc8-105">In this tutorial, you'll learn how an <xref:System.Diagnostics.Tracing.EventCounter> can be used to measure performance with a high frequency of events.</span></span> <span data-ttu-id="12dc8-106">Můžete využít [Dostupné čítače](event-counters.md#available-counters) publikované různými oficiálními balíčky .NET Core, poskytovateli jiných výrobců nebo vytvořit vlastní metriky pro monitorování.</span><span class="sxs-lookup"><span data-stu-id="12dc8-106">You can use the [available counters](event-counters.md#available-counters) published by various official .NET Core packages, third-party providers, or create your own metrics for monitoring.</span></span>

<span data-ttu-id="12dc8-107">V tomto kurzu provedete následující:</span><span class="sxs-lookup"><span data-stu-id="12dc8-107">In this tutorial, you will:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="12dc8-108">Implementujte <xref:System.Diagnostics.Tracing.EventSource> .</span><span class="sxs-lookup"><span data-stu-id="12dc8-108">Implement an <xref:System.Diagnostics.Tracing.EventSource>.</span></span>
> - <span data-ttu-id="12dc8-109">Sledujte čítače pomocí [dotnet-Counters](dotnet-counters.md).</span><span class="sxs-lookup"><span data-stu-id="12dc8-109">Monitor counters with [dotnet-counters](dotnet-counters.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="12dc8-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="12dc8-110">Prerequisites</span></span>

<span data-ttu-id="12dc8-111">V tomto kurzu se používá:</span><span class="sxs-lookup"><span data-stu-id="12dc8-111">The tutorial uses:</span></span>

- <span data-ttu-id="12dc8-112">[.NET Core 3,1 SDK](https://dotnet.microsoft.com/download/dotnet-core) nebo novější verze.</span><span class="sxs-lookup"><span data-stu-id="12dc8-112">[.NET Core 3.1 SDK](https://dotnet.microsoft.com/download/dotnet-core) or a later version.</span></span>
- <span data-ttu-id="12dc8-113">[dotnet – čítače](dotnet-counters.md) pro monitorování čítačů událostí</span><span class="sxs-lookup"><span data-stu-id="12dc8-113">[dotnet-counters](dotnet-counters.md) to monitor event counters.</span></span>
- <span data-ttu-id="12dc8-114">[Ukázková cílová aplikace ladění](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios) , která se má diagnostikovat</span><span class="sxs-lookup"><span data-stu-id="12dc8-114">A [sample debug target](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios) app to diagnose.</span></span>

## <a name="get-the-source"></a><span data-ttu-id="12dc8-115">Získat zdroj</span><span class="sxs-lookup"><span data-stu-id="12dc8-115">Get the source</span></span>

<span data-ttu-id="12dc8-116">Ukázková aplikace se použije jako základ pro monitorování.</span><span class="sxs-lookup"><span data-stu-id="12dc8-116">The sample application will be used as a basis for monitoring.</span></span> <span data-ttu-id="12dc8-117">[Ukázkové ASP.NET Core úložiště](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios) je k dispozici v prohlížeči ukázek.</span><span class="sxs-lookup"><span data-stu-id="12dc8-117">The [sample ASP.NET Core repository](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios) is available from the samples browser.</span></span> <span data-ttu-id="12dc8-118">Stáhli jste soubor zip, extrahujete ho po stažení a otevřete ho ve svém oblíbeném integrovaném vývojovém prostředí (IDE).</span><span class="sxs-lookup"><span data-stu-id="12dc8-118">You download the zip file, extract it once downloaded, and open it in your favorite IDE.</span></span> <span data-ttu-id="12dc8-119">Sestavte a spusťte aplikaci, abyste zajistili správné fungování a pak zastavte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="12dc8-119">Build and run the application to ensure that it works properly, then stop the application.</span></span>

## <a name="implement-an-eventsource"></a><span data-ttu-id="12dc8-120">Implementace EventSource</span><span class="sxs-lookup"><span data-stu-id="12dc8-120">Implement an EventSource</span></span>

<span data-ttu-id="12dc8-121">Pro události, ke kterým dochází každých několik milisekund, budete chtít, aby režie na událost byla nízká (méně než milisekunda).</span><span class="sxs-lookup"><span data-stu-id="12dc8-121">For events that happen every few milliseconds, you'll want the overhead per event to be low (less than a millisecond).</span></span> <span data-ttu-id="12dc8-122">V opačném případě bude dopad na výkon významný.</span><span class="sxs-lookup"><span data-stu-id="12dc8-122">Otherwise, the impact on performance will be significant.</span></span> <span data-ttu-id="12dc8-123">Protokolování události znamená, že budete psát něco na disk.</span><span class="sxs-lookup"><span data-stu-id="12dc8-123">Logging an event means you're going to write something to disk.</span></span> <span data-ttu-id="12dc8-124">Pokud disk není dostatečně rychlý, ztratíte události.</span><span class="sxs-lookup"><span data-stu-id="12dc8-124">If the disk is not fast enough, you will lose events.</span></span> <span data-ttu-id="12dc8-125">Potřebujete jiné řešení než protokolování samotné události.</span><span class="sxs-lookup"><span data-stu-id="12dc8-125">You need a solution other than logging the event itself.</span></span>

<span data-ttu-id="12dc8-126">Při práci s velkým počtem událostí není důležité vědět, jak měření na událost není užitečné.</span><span class="sxs-lookup"><span data-stu-id="12dc8-126">When dealing with a large number of events, knowing the measure per event is not useful either.</span></span> <span data-ttu-id="12dc8-127">Většina času, kterou potřebujete, je z nich jenom několik statistik.</span><span class="sxs-lookup"><span data-stu-id="12dc8-127">Most of the time all you need is just some statistics out of it.</span></span> <span data-ttu-id="12dc8-128">Takže můžete získat statistiku v rámci samotného procesu a pak za běhu napsat událost, která bude hlásit statistiku, to je to, co <xref:System.Diagnostics.Tracing.EventCounter> dělat.</span><span class="sxs-lookup"><span data-stu-id="12dc8-128">So you could get the statistics within the process itself and then write an event once in a while to report the statistics, that's what <xref:System.Diagnostics.Tracing.EventCounter> will do.</span></span>

<span data-ttu-id="12dc8-129">Níže je uveden příklad, jak implementovat <xref:System.Diagnostics.Tracing.EventSource?displayProperty=fullName> .</span><span class="sxs-lookup"><span data-stu-id="12dc8-129">Below is an example of how to implement an <xref:System.Diagnostics.Tracing.EventSource?displayProperty=fullName>.</span></span> <span data-ttu-id="12dc8-130">Vytvořte nový soubor s názvem *MinimalEventCounterSource.cs* a jako svůj zdroj použijte fragment kódu:</span><span class="sxs-lookup"><span data-stu-id="12dc8-130">Create a new file named *MinimalEventCounterSource.cs* and use the code snippet as its source:</span></span>

:::code language="csharp" source="snippets/EventCounters/MinimalEventCounterSource.cs":::

<span data-ttu-id="12dc8-131"><xref:System.Diagnostics.Tracing.EventSource.WriteEvent%2A?displayProperty=nameWithType>Řádkem je <xref:System.Diagnostics.Tracing.EventSource> součást a není součástí <xref:System.Diagnostics.Tracing.EventCounter> , byla zapsána za účelem zobrazení, že můžete protokolovat zprávu spolu s čítačem události.</span><span class="sxs-lookup"><span data-stu-id="12dc8-131">The <xref:System.Diagnostics.Tracing.EventSource.WriteEvent%2A?displayProperty=nameWithType> line is the <xref:System.Diagnostics.Tracing.EventSource> part and is not part of <xref:System.Diagnostics.Tracing.EventCounter>, it was written to show that you can log a message together with the event counter.</span></span>

## <a name="add-an-action-filter"></a><span data-ttu-id="12dc8-132">Přidat filtr akcí</span><span class="sxs-lookup"><span data-stu-id="12dc8-132">Add an action filter</span></span>

<span data-ttu-id="12dc8-133">Vzorový zdrojový kód je ASP.NET Core projekt.</span><span class="sxs-lookup"><span data-stu-id="12dc8-133">The sample source code is an ASP.NET Core project.</span></span> <span data-ttu-id="12dc8-134">Můžete přidat [Filtr akcí](/aspnet/core/mvc/controllers/filters#action-filters) globálně, který bude protokolovat celkovou dobu požadavku.</span><span class="sxs-lookup"><span data-stu-id="12dc8-134">You can add an [action filter](/aspnet/core/mvc/controllers/filters#action-filters) globally that will log the total request time.</span></span> <span data-ttu-id="12dc8-135">Vytvořte nový soubor s názvem *LogRequestTimeFilterAttribute.cs*a použijte následující kód:</span><span class="sxs-lookup"><span data-stu-id="12dc8-135">Create a new file named *LogRequestTimeFilterAttribute.cs*, and use the following code:</span></span>

```csharp
using System.Diagnostics;
using Microsoft.AspNetCore.Http.Extensions;
using Microsoft.AspNetCore.Mvc.Filters;

namespace DiagnosticScenarios
{
    public class LogRequestTimeFilterAttribute : ActionFilterAttribute
    {
        readonly Stopwatch _stopwatch = new Stopwatch();

        public override void OnActionExecuting(ActionExecutingContext context) => _stopwatch.Start();

        public override void OnActionExecuted(ActionExecutedContext context)
        {
            _stopwatch.Stop();

            MinimalEventCounterSource.Log.Request(
                context.HttpContext.Request.GetDisplayUrl(), _stopwatch.ElapsedMilliseconds);
        }
    }
}
```

<span data-ttu-id="12dc8-136">Filtr akcí spustí <xref:System.Diagnostics.Stopwatch> , jakmile se zahájí požadavek, a zastaví se po jeho dokončení a zachytí uplynulý čas.</span><span class="sxs-lookup"><span data-stu-id="12dc8-136">The action filter starts a <xref:System.Diagnostics.Stopwatch> as the request begins, and stops after it has completed, capturing the elapsed time.</span></span> <span data-ttu-id="12dc8-137">Celkový počet milisekund je protokolován do `MinimalEventCounterSource` instance singleton.</span><span class="sxs-lookup"><span data-stu-id="12dc8-137">The total milliseconds is logged to the `MinimalEventCounterSource` singleton instance.</span></span> <span data-ttu-id="12dc8-138">Aby se tento filtr mohl použít, musíte ho přidat do kolekce filters.</span><span class="sxs-lookup"><span data-stu-id="12dc8-138">In order for this filter to be applied, you need to add it to the filters collection.</span></span> <span data-ttu-id="12dc8-139">V souboru *Startup.cs* aktualizujte `ConfigureServices` metodu v zahrnutí tohoto filtru.</span><span class="sxs-lookup"><span data-stu-id="12dc8-139">In the *Startup.cs* file, update the `ConfigureServices` method in include this filter.</span></span>

```csharp
public void ConfigureServices(IServiceCollection services) =>
    services.AddControllers(options => options.Filters.Add<LogRequestTimeFilterAttribute>())
            .AddNewtonsoftJson();
```

## <a name="monitor-event-counter"></a><span data-ttu-id="12dc8-140">Monitorovat čítač událostí</span><span class="sxs-lookup"><span data-stu-id="12dc8-140">Monitor event counter</span></span>

<span data-ttu-id="12dc8-141">S implementací <xref:System.Diagnostics.Tracing.EventSource> a vlastním filtrem akce Sestavte a spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="12dc8-141">With the implementation on an <xref:System.Diagnostics.Tracing.EventSource> and the custom action filter, build and launch the application.</span></span>
<span data-ttu-id="12dc8-142">Metriku jste zaznamenali do, ale nebudete <xref:System.Diagnostics.Tracing.EventCounter> ji používat, pokud nebudete mít ke statistikám přístup.</span><span class="sxs-lookup"><span data-stu-id="12dc8-142">You logged the metric to the <xref:System.Diagnostics.Tracing.EventCounter>, but unless you access the statistics from of it, it is not useful.</span></span> <span data-ttu-id="12dc8-143">Chcete-li získat statistiku, je nutné ji povolit <xref:System.Diagnostics.Tracing.EventCounter> vytvořením časovače, který se aktivuje tak často, jak budete chtít události, a také naslouchací proces pro zachycení událostí.</span><span class="sxs-lookup"><span data-stu-id="12dc8-143">To get the statistics, you need to enable the <xref:System.Diagnostics.Tracing.EventCounter> by creating a timer that fires as frequently as you want the events, as well as a listener to capture the events.</span></span> <span data-ttu-id="12dc8-144">K tomu můžete použít [dotnet-Counters](dotnet-counters.md).</span><span class="sxs-lookup"><span data-stu-id="12dc8-144">To do that, you can use [dotnet-counters](dotnet-counters.md).</span></span>

<span data-ttu-id="12dc8-145">Pomocí příkazu [dotnet-Counters PS](dotnet-counters.md#dotnet-counters-ps) zobrazte seznam procesů .NET, které je možné monitorovat.</span><span class="sxs-lookup"><span data-stu-id="12dc8-145">Use the [dotnet-counters ps](dotnet-counters.md#dotnet-counters-ps) command to display a list of .NET processes that can be monitored.</span></span>

```console
dotnet-counters ps
```

<span data-ttu-id="12dc8-146">Pomocí identifikátoru procesu z výstupu `dotnet-counters ps` příkazu můžete začít monitorovat čítač událostí pomocí následujícího `dotnet-counters monitor` příkazu:</span><span class="sxs-lookup"><span data-stu-id="12dc8-146">Using the process identifier from the output of the `dotnet-counters ps` command, you can start monitoring the event counter with the following `dotnet-counters monitor` command:</span></span>

```console
dotnet-counters monitor --process-id 2196 Sample.EventCounter.Minimal Microsoft.AspNetCore.Hosting[total-requests,requests-per-second] System.Runtime[cpu-usage]
```

<span data-ttu-id="12dc8-147">Když `dotnet-counters monitor` je příkaz spuštěný, podržením <kbd>F5</kbd> v prohlížeči začněte vystavovat průběžné požadavky na `https://localhost:5001/api/values` koncový bod.</span><span class="sxs-lookup"><span data-stu-id="12dc8-147">While the `dotnet-counters monitor` command is running, hold <kbd>F5</kbd> on the browser to start issuing continuous requests to the `https://localhost:5001/api/values` endpoint.</span></span> <span data-ttu-id="12dc8-148">Po několika sekundách zastavte stisknutím <kbd>q</kbd></span><span class="sxs-lookup"><span data-stu-id="12dc8-148">After a few seconds stop by pressing <kbd>q</kbd></span></span>

```console
Press p to pause, r to resume, q to quit.
    Status: Running

[Microsoft.AspNetCore.Hosting]
    Request Rate / 1 sec                               9
    Total Requests                                   134
[System.Runtime]
    CPU Usage (%)                                     13
[Sample.EventCounter.Minimal]
    Request Processing Time (ms)                      34.5
```

<span data-ttu-id="12dc8-149">`dotnet-counters monitor`Příkaz je ideální pro aktivní monitorování.</span><span class="sxs-lookup"><span data-stu-id="12dc8-149">The `dotnet-counters monitor` command is great for active monitoring.</span></span> <span data-ttu-id="12dc8-150">Tyto diagnostické metriky ale můžete chtít shromažďovat pro následné zpracování a analýzu.</span><span class="sxs-lookup"><span data-stu-id="12dc8-150">However, you may want to collect these diagnostic metrics for post processing and analysis.</span></span> <span data-ttu-id="12dc8-151">V takovém případě použijte `dotnet-counters collect` příkaz.</span><span class="sxs-lookup"><span data-stu-id="12dc8-151">For that, use the `dotnet-counters collect` command.</span></span> <span data-ttu-id="12dc8-152">`collect`Příkaz switch je podobný `monitor` příkazu, ale přijímá několik dalších parametrů.</span><span class="sxs-lookup"><span data-stu-id="12dc8-152">The `collect` switch command is similar to the `monitor` command, but accepts a few additional parameters.</span></span> <span data-ttu-id="12dc8-153">Můžete zadat požadovaný název a formát výstupního souboru.</span><span class="sxs-lookup"><span data-stu-id="12dc8-153">You can specify the desired output file name and format.</span></span> <span data-ttu-id="12dc8-154">Pro soubor JSON s názvem *diagnostics.js* použijte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="12dc8-154">For a JSON file named *diagnostics.json* use the following command:</span></span>

```console
dotnet-counters collect --process-id 2196 --format json -o diagnostics.json Sample.EventCounter.Minimal Microsoft.AspNetCore.Hosting[total-requests,requests-per-second] System.Runtime[cpu-usage]
```

<span data-ttu-id="12dc8-155">Až bude příkaz spuštěný, podržením klávesy <kbd>F5</kbd> v prohlížeči začněte vystavovat průběžné požadavky na `https://localhost:5001/api/values` koncový bod.</span><span class="sxs-lookup"><span data-stu-id="12dc8-155">Again, while the command is running, hold <kbd>F5</kbd> on the browser to start issuing continuous requests to the `https://localhost:5001/api/values` endpoint.</span></span> <span data-ttu-id="12dc8-156">Po několika sekundách zastavte stisknutím <kbd>q</kbd>.</span><span class="sxs-lookup"><span data-stu-id="12dc8-156">After a few seconds stop by pressing <kbd>q</kbd>.</span></span> <span data-ttu-id="12dc8-157">*diagnostics.js* soubor je zapsán.</span><span class="sxs-lookup"><span data-stu-id="12dc8-157">The *diagnostics.json* file is written.</span></span> <span data-ttu-id="12dc8-158">Napsaný soubor JSON se ale nesadí. v případě čitelnosti se tady odsadí.</span><span class="sxs-lookup"><span data-stu-id="12dc8-158">The JSON file that is written is not indented, however; for readability it is indented here.</span></span>

```json
{
  "TargetProcess": "DiagnosticScenarios",
  "StartTime": "8/5/2020 3:02:45 PM",
  "Events": [
    {
      "timestamp": "2020-08-05 15:02:47Z",
      "provider": "System.Runtime",
      "name": "CPU Usage (%)",
      "counterType": "Metric",
      "value": 0
    },
    {
      "timestamp": "2020-08-05 15:02:47Z",
      "provider": "Microsoft.AspNetCore.Hosting",
      "name": "Request Rate / 1 sec",
      "counterType": "Rate",
      "value": 0
    },
    {
      "timestamp": "2020-08-05 15:02:47Z",
      "provider": "Microsoft.AspNetCore.Hosting",
      "name": "Total Requests",
      "counterType": "Metric",
      "value": 134
    },
    {
      "timestamp": "2020-08-05 15:02:47Z",
      "provider": "Sample.EventCounter.Minimal",
      "name": "Request Processing Time (ms)",
      "counterType": "Metric",
      "value": 0
    },
    {
      "timestamp": "2020-08-05 15:02:47Z",
      "provider": "System.Runtime",
      "name": "CPU Usage (%)",
      "counterType": "Metric",
      "value": 0
    },
    {
      "timestamp": "2020-08-05 15:02:48Z",
      "provider": "Microsoft.AspNetCore.Hosting",
      "name": "Request Rate / 1 sec",
      "counterType": "Rate",
      "value": 0
    },
    {
      "timestamp": "2020-08-05 15:02:48Z",
      "provider": "Microsoft.AspNetCore.Hosting",
      "name": "Total Requests",
      "counterType": "Metric",
      "value": 134
    },
    {
      "timestamp": "2020-08-05 15:02:48Z",
      "provider": "Sample.EventCounter.Minimal",
      "name": "Request Processing Time (ms)",
      "counterType": "Metric",
      "value": 0
    },
    {
      "timestamp": "2020-08-05 15:02:48Z",
      "provider": "System.Runtime",
      "name": "CPU Usage (%)",
      "counterType": "Metric",
      "value": 0
    },
    {
      "timestamp": "2020-08-05 15:02:50Z",
      "provider": "Microsoft.AspNetCore.Hosting",
      "name": "Request Rate / 1 sec",
      "counterType": "Rate",
      "value": 0
    },
    {
      "timestamp": "2020-08-05 15:02:50Z",
      "provider": "Microsoft.AspNetCore.Hosting",
      "name": "Total Requests",
      "counterType": "Metric",
      "value": 134
    },
    {
      "timestamp": "2020-08-05 15:02:50Z",
      "provider": "Sample.EventCounter.Minimal",
      "name": "Request Processing Time (ms)",
      "counterType": "Metric",
      "value": 0
    }
  ]
}
```

## <a name="next-steps"></a><span data-ttu-id="12dc8-159">Další kroky</span><span class="sxs-lookup"><span data-stu-id="12dc8-159">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="12dc8-160">EventCounters</span><span class="sxs-lookup"><span data-stu-id="12dc8-160">EventCounters</span></span>](event-counters.md)
