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
# <a name="tutorial-measure-performance-using-eventcounters-in-net-core"></a>Kurz: měření výkonu pomocí EventCounters v .NET Core

**Tento článek se týká: ✔️** .net Core 3,0 SDK a novějších verzí

V tomto kurzu se dozvíte, jak <xref:System.Diagnostics.Tracing.EventCounter> lze použít k měření výkonu s vysokou četností událostí. Můžete využít [Dostupné čítače](event-counters.md#available-counters) publikované různými oficiálními balíčky .NET Core, poskytovateli jiných výrobců nebo vytvořit vlastní metriky pro monitorování.

V tomto kurzu provedete následující:

> [!div class="checklist"]
>
> - Implementujte <xref:System.Diagnostics.Tracing.EventSource> .
> - Sledujte čítače pomocí [dotnet-Counters](dotnet-counters.md).

## <a name="prerequisites"></a>Požadavky

V tomto kurzu se používá:

- [.NET Core 3,1 SDK](https://dotnet.microsoft.com/download/dotnet-core) nebo novější verze.
- [dotnet – čítače](dotnet-counters.md) pro monitorování čítačů událostí
- [Ukázková cílová aplikace ladění](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios) , která se má diagnostikovat

## <a name="get-the-source"></a>Získat zdroj

Ukázková aplikace se použije jako základ pro monitorování. [Ukázkové ASP.NET Core úložiště](https://docs.microsoft.com/samples/dotnet/samples/diagnostic-scenarios) je k dispozici v prohlížeči ukázek. Stáhli jste soubor zip, extrahujete ho po stažení a otevřete ho ve svém oblíbeném integrovaném vývojovém prostředí (IDE). Sestavte a spusťte aplikaci, abyste zajistili správné fungování a pak zastavte aplikaci.

## <a name="implement-an-eventsource"></a>Implementace EventSource

Pro události, ke kterým dochází každých několik milisekund, budete chtít, aby režie na událost byla nízká (méně než milisekunda). V opačném případě bude dopad na výkon významný. Protokolování události znamená, že budete psát něco na disk. Pokud disk není dostatečně rychlý, ztratíte události. Potřebujete jiné řešení než protokolování samotné události.

Při práci s velkým počtem událostí není důležité vědět, jak měření na událost není užitečné. Většina času, kterou potřebujete, je z nich jenom několik statistik. Takže můžete získat statistiku v rámci samotného procesu a pak za běhu napsat událost, která bude hlásit statistiku, to je to, co <xref:System.Diagnostics.Tracing.EventCounter> dělat.

Níže je uveden příklad, jak implementovat <xref:System.Diagnostics.Tracing.EventSource?displayProperty=fullName> . Vytvořte nový soubor s názvem *MinimalEventCounterSource.cs* a jako svůj zdroj použijte fragment kódu:

:::code language="csharp" source="snippets/EventCounters/MinimalEventCounterSource.cs":::

<xref:System.Diagnostics.Tracing.EventSource.WriteEvent%2A?displayProperty=nameWithType>Řádkem je <xref:System.Diagnostics.Tracing.EventSource> součást a není součástí <xref:System.Diagnostics.Tracing.EventCounter> , byla zapsána za účelem zobrazení, že můžete protokolovat zprávu spolu s čítačem události.

## <a name="add-an-action-filter"></a>Přidat filtr akcí

Vzorový zdrojový kód je ASP.NET Core projekt. Můžete přidat [Filtr akcí](/aspnet/core/mvc/controllers/filters#action-filters) globálně, který bude protokolovat celkovou dobu požadavku. Vytvořte nový soubor s názvem *LogRequestTimeFilterAttribute.cs*a použijte následující kód:

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

Filtr akcí spustí <xref:System.Diagnostics.Stopwatch> , jakmile se zahájí požadavek, a zastaví se po jeho dokončení a zachytí uplynulý čas. Celkový počet milisekund je protokolován do `MinimalEventCounterSource` instance singleton. Aby se tento filtr mohl použít, musíte ho přidat do kolekce filters. V souboru *Startup.cs* aktualizujte `ConfigureServices` metodu v zahrnutí tohoto filtru.

```csharp
public void ConfigureServices(IServiceCollection services) =>
    services.AddControllers(options => options.Filters.Add<LogRequestTimeFilterAttribute>())
            .AddNewtonsoftJson();
```

## <a name="monitor-event-counter"></a>Monitorovat čítač událostí

S implementací <xref:System.Diagnostics.Tracing.EventSource> a vlastním filtrem akce Sestavte a spusťte aplikaci.
Metriku jste zaznamenali do, ale nebudete <xref:System.Diagnostics.Tracing.EventCounter> ji používat, pokud nebudete mít ke statistikám přístup. Chcete-li získat statistiku, je nutné ji povolit <xref:System.Diagnostics.Tracing.EventCounter> vytvořením časovače, který se aktivuje tak často, jak budete chtít události, a také naslouchací proces pro zachycení událostí. K tomu můžete použít [dotnet-Counters](dotnet-counters.md).

Pomocí příkazu [dotnet-Counters PS](dotnet-counters.md#dotnet-counters-ps) zobrazte seznam procesů .NET, které je možné monitorovat.

```console
dotnet-counters ps
```

Pomocí identifikátoru procesu z výstupu `dotnet-counters ps` příkazu můžete začít monitorovat čítač událostí pomocí následujícího `dotnet-counters monitor` příkazu:

```console
dotnet-counters monitor --process-id 2196 Sample.EventCounter.Minimal Microsoft.AspNetCore.Hosting[total-requests,requests-per-second] System.Runtime[cpu-usage]
```

Když `dotnet-counters monitor` je příkaz spuštěný, podržením <kbd>F5</kbd> v prohlížeči začněte vystavovat průběžné požadavky na `https://localhost:5001/api/values` koncový bod. Po několika sekundách zastavte stisknutím <kbd>q</kbd>

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

`dotnet-counters monitor`Příkaz je ideální pro aktivní monitorování. Tyto diagnostické metriky ale můžete chtít shromažďovat pro následné zpracování a analýzu. V takovém případě použijte `dotnet-counters collect` příkaz. `collect`Příkaz switch je podobný `monitor` příkazu, ale přijímá několik dalších parametrů. Můžete zadat požadovaný název a formát výstupního souboru. Pro soubor JSON s názvem *diagnostics.js* použijte následující příkaz:

```console
dotnet-counters collect --process-id 2196 --format json -o diagnostics.json Sample.EventCounter.Minimal Microsoft.AspNetCore.Hosting[total-requests,requests-per-second] System.Runtime[cpu-usage]
```

Až bude příkaz spuštěný, podržením klávesy <kbd>F5</kbd> v prohlížeči začněte vystavovat průběžné požadavky na `https://localhost:5001/api/values` koncový bod. Po několika sekundách zastavte stisknutím <kbd>q</kbd>. *diagnostics.js* soubor je zapsán. Napsaný soubor JSON se ale nesadí. v případě čitelnosti se tady odsadí.

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

## <a name="next-steps"></a>Další kroky

> [!div class="nextstepaction"]
> [EventCounters](event-counters.md)
