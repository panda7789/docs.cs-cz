---
title: Správa výkonu aplikací – gRPC pro vývojáře WCF
description: Protokolování, metriky a trasování pro aplikace ASP.NET Core gRPC.
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: 6ba67fd069e7efc232f912e50c0e283facb79e9c
ms.sourcegitcommit: 337bdc5a463875daf2cc6883e5a2da97d56f5000
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2019
ms.locfileid: "72846723"
---
# <a name="application-performance-management"></a>Správa výkonu aplikace

V moderních produkčních prostředích, jako je Kubernetes, je velmi důležité, abyste mohli monitorovat aplikace, aby se zajistila optimální provoz. Obavy, jako protokolování a metriky, nebyly nikdy důležitější. ASP.NET Core, včetně gRPC, má prvotřídní podporu pro vytváření a správu zpráv protokolu a dat metrik a také pro *trasování* dat. V této části se podrobněji Prozkoumejte tyto oblasti.

## <a name="logging-vs-metrics"></a>Protokolování vs – metriky

Než začnete s podrobnostmi implementace, je nutné pochopit rozdíl mezi protokolováním a metrikami.

V souvislosti s textovými zprávami, které zaznamenávají podrobné informace o akcích, ke kterým došlo v systému, se jedná o protokol. Zprávy protokolu mohou zahrnovat data výjimek, jako jsou trasování zásobníku, nebo strukturovaná data, která poskytují kontext zprávy. Výstup protokolování se obvykle zapisuje do vyhledávacího úložiště textu.

Metriky odkazují na číselná data, která jsou navržena pro agregaci a jsou prezentována pomocí grafů a grafů na řídicím panelu, který poskytuje přehled o celkovém stavu a výkonu aplikace. Data metriky je také možné použít ke spuštění automatizovaných výstrah při překročení prahové hodnoty. V následujícím seznamu jsou uvedeny některé příklady dat metrik:

- Doba potřebná pro zpracování požadavků.
- Počet požadavků za sekundu, které jsou zpracovávány instancí služby.
- Počet neúspěšných žádostí o instanci.

## <a name="logging-in-aspnet-core-grpc"></a>Přihlášení ASP.NET Core gRPC

ASP.NET Core poskytuje integrovanou podporu pro protokolování ve formě balíčku NuGet [Microsoft. Extensions. Logging](https://www.nuget.org/packages/Microsoft.Extensions.Logging) . Základní části této knihovny jsou součástí webové sady SDK, takže je není nutné instalovat ručně. Ve výchozím nastavení se zprávy protokolu zapisují do standardního výstupu (konzola) a do libovolného připojeného ladicího programu. Pro zápis protokolů do trvalých externích úložišť dat možná budete muset importovat [volitelné balíčky jímky protokolování](https://docs.microsoft.com/aspnet/core/fundamentals/logging/?view=aspnetcore-3.0#third-party-logging-providers).

Rozhraní ASP.NET Core gRPC zapisuje podrobné zprávy protokolování diagnostiky do tohoto protokolovacího rozhraní, aby je bylo možné zpracovat/uložit společně s vlastními zprávami aplikace.

### <a name="produce-log-messages"></a>Vytváření zpráv protokolu

Rozšíření protokolování je automaticky registrováno se systémem injektáže ASP.NET Core závislostí, takže můžete zadat protokolovací nástroje jako parametr konstruktoru v typech služeb gRPC.

```csharp
public class StockData : Stocks.StocksBase
{
    private readonly ILogger<StockData> _logger;

    public StockData(ILogger<StockData> logger)
    {
        _logger = logger;
    }
}
```

Mnohé zprávy protokolu o požadavcích, výjimkách a tak dále jsou poskytovány komponentami rozhraní ASP.NET Core a gRPC. Přidejte vlastní zprávy protokolu pro poskytnutí podrobností a kontextu o logice aplikace, nikoli ke snížení úrovně otázek.

Další informace o psaní zpráv protokolu a dostupných umyvadel a cílů protokolování najdete v článku [protokolování v .NET Core a ASP.NET Core](https://docs.microsoft.com/aspnet/core/fundamentals/logging/?view=aspnetcore-3.0) .

## <a name="metrics-in-aspnet-core-grpc"></a>Metriky v ASP.NET Core gRPC

Modul runtime .NET Core poskytuje sadu komponent pro generování a sledování metrik, které obsahují rozhraní API, jako jsou <xref:System.Diagnostics.Tracing.EventSource> a <xref:System.Diagnostics.Tracing.EventCounter> třídy. Tato rozhraní API lze použít k vygenerování základních číselných dat, která lze spotřebovat externími procesy, jako jsou [globální nástroje dotnet-Counters](https://github.com/dotnet/diagnostics/blob/master/documentation/dotnet-counters-instructions.md)nebo trasování událostí pro systém Windows. Další informace o použití `EventCounter` ve vlastním kódu najdete v [úvodním](https://github.com/dotnet/corefx/blob/master/src/System.Diagnostics.Tracing/documentation/EventCounterTutorial.md) kurzu pro EventCounter.

Pro pokročilejší metriky a pro zápis dat metrik do širší škály úložišť dat je k dispozici skvělý open source projekt s názvem [metriky aplikace](https://www.app-metrics.io). Tato sada knihoven poskytuje rozsáhlou sadu typů pro instrumentaci kódu. Nabízí také balíčky pro zápis metrik do různých druhů cílů, které obsahují databáze časových řad, například Prometheus a InfluxDB, [Azure Application Insights](https://docs.microsoft.com/azure/azure-monitor/app/app-insights-overview)a další. Balíček NuGet [App. Metrics. AspNetCore. Mvc](https://www.nuget.org/packages/App.Metrics.AspNetCore.Mvc/) dokonce přidá komplexní sadu základních metrik, které se automaticky generují prostřednictvím integrace s ASP.NET Core Framework, a web nabízí [šablony](https://www.app-metrics.io/samples/grafana/) pro zobrazování těchto metrik. s platformou pro vizualizaci [Grafana](https://grafana.com/)

Další informace a dokumentaci k metrikám aplikací najdete na webu [App-Metrics.IO](https://app-metrics.io) .

### <a name="produce-metrics"></a>Vydávat metriky

Většina platforem metrik podporuje pět základních typů metriky, které jsou popsaných v následující tabulce:

| Typ metriky | Popis |
| ----------- | ----------- |
| Čítač     | Sleduje, jak často se něco stane, například požadavky, chyby a tak dále. |
| Měřená       | Zaznamenává jednu hodnotu, která se mění v průběhu času, například aktivních připojení. |
| Histogram   | Měří distribuci hodnot napříč libovolnými limity. Například histogram může sledovat velikost datové sady a počítat, kolik z nich obsahovalo < 10 záznamů, kolik 11-100 a 101-1000 a > 1000 záznamů. |
| Měřiče       | Měří rychlost, s jakou dojde k události v různých časových intervalech. |
| Časovač       | Sleduje dobu trvání událostí a rychlost, s jakou se vyskytuje, a ukládá se jako histogram. |

Pomocí *metriky aplikací*se dá rozhraní `IMetrics` získat prostřednictvím injektáže závislosti a používá se k záznamu kterékoli z těchto metrik pro službu gRPC. Následující příklad ukazuje, jak spočítat počet `Get` požadavků provedených v čase:

```csharp
public class StockData : Stocks.StocksBase
{
    private static readonly CounterOptions GetRequestCounter = new CounterOptions
    {
        Name = "StockData_Get_Requests",
        MeasurementUnit = Unit.Calls
    };

    private readonly IStockRepository _repository;
    private readonly IMetrics _metrics;

    public StockData(IStockRepository repository, IMetrics metrics)
    {
        _repository = repository;
        _metrics = metrics;
    }

    public override async Task<GetResponse> Get(GetRequest request, ServerCallContext context)
    {
        _metrics.Measure.Counter.Increment(GetRequestCounter);

        // Serve request...
    }
}
```

### <a name="store-and-visualize-metrics-data"></a>Ukládání a vizualizace dat metrik

Nejlepším způsobem, jak ukládat data metrik, je *databáze časových řad*, specializované úložiště dat navržené pro záznam numerických datových řad označených časovými razítky. Nejoblíbenější z těchto databází jsou [Prometheus](https://prometheus.io/) a [InfluxDB](https://www.influxdata.com/products/influxdb-overview/). Microsoft Azure také poskytuje vyhrazené úložiště metrik prostřednictvím služby [Azure monitor](https://docs.microsoft.com/azure/azure-monitor/overview) .

Aktuální řešení pro vizualizaci dat metrik je [Grafana](https://grafana.com), které funguje se široké škálou poskytovatelů úložiště, včetně Azure monitor, InfluxDB a Prometheus. Následující obrázek ukazuje příklad řídicího panelu Grafana, který zobrazuje metriky z sítě Linkered Service, na které běží ukázka StockData:

![Řídicí panel Grafana](media/application-performance-management/grafana-screenshot.png)

### <a name="metrics-based-alerting"></a>Výstrahy založené na metrikách

Číselná povaha dat metrik znamená, že je ideálním řešením pro systémy upozornění, informování vývojářů a technikům podpory, když hodnota spadá mimo určitou definovanou toleranci. Platformy, které jsou již zmíněny, poskytují podporu pro upozorňování prostřednictvím řady možností, včetně e-mailů, textových zpráv nebo vizualizací v řídicím panelu.

## <a name="distributed-tracing"></a>Distribuované trasování

*Distribuované trasování* je poměrně poslední vývoj v monitorování, který se objevil při rostoucím využití mikroslužeb a distribuovaných architektur. Jedna žádost z klientského prohlížeče, aplikace nebo zařízení může být rozdělená na mnoho kroků a dílčích požadavků a zahrnovat používání mnoha služeb v síti. Díky tomu je obtížné sladit zprávy protokolu a metriky se specifickým požadavkem, který je vyvolal. Distribuované trasování aplikuje identifikátory na požadavky, které umožňují korelaci protokolů a metrik s konkrétní operací. To se podobá [kompletnímu trasování služby WCF](https://docs.microsoft.com/dotnet/framework/wcf/diagnostics/tracing/end-to-end-tracing), ale používá se na různých platformách.

I když je stále nascent technologickým oddělením, distribuované trasování se rychle zvětšilo v oblíbenosti a teď prochází normalizačním procesem. Cloud Native Computing Foundation vytvořila [Open Tracing Standard](https://opentracing.io)a při práci s back-endy, jako je [Jaeger](https://www.jaegertracing.io/) a [elastické APM](https://www.elastic.co/products/apm), se snaží poskytnout neutrální knihovny nezávislé na dodavatelích. Ve stejnou dobu vytvořil [projekt OpenCensus](https://opencensus.io/) pro řešení stejné sady problémů. Tyto dva projekty se teď slučují do nového projektu [OpenTelemetry](https://opentelemetry.io), což se zaměřuje na budoucí standardní oborové standardy.

### <a name="how-distributed-tracing-works"></a>Jak funguje distribuované trasování

Distribuované trasování vychází z konceptu různých *rozsahů*: pojmenovaných, časovanéch operací, které jsou součástí jednoho *trasování*, což může zahrnovat zpracování na více uzlech systému. Při zahájení nové operace se vytvoří trasování s jedinečným identifikátorem. Pro každou dílčí operaci je vytvořen rozsah s vlastním identifikátorem a identifikátorem trasování. V případě, že požadavek projde do systému, mohou různé komponenty vytvořit *podřízené* rozsahy, které obsahují identifikátor své *nadřazené položky*. Rozsah má *kontext*, který obsahuje identifikátory trasování a rozsahu a také užitečná data ve formě párů klíč/hodnota (tzv. *zavazadla*).

### <a name="distributed-tracing-with-diagnosticsource"></a>Distribuované trasování pomocí DiagnosticSource

.NET Core má interní modul, který se mapuje dobře na distribuované trasování a zahrnuje: [DiagnosticSource](https://github.com/dotnet/corefx/blob/master/src/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md#diagnosticsource-users-guide). A také poskytnutí jednoduchého způsobu, jak vytvořit a používat diagnostiku v rámci procesu, má modul `DiagnosticSource` koncept *aktivity*, což je efektivně implementace distribuovaného trasování nebo rozpětí v rámci trasování. Interní moduly se postarou o aktivity nadřazené/podřízené, včetně přidělování identifikátorů. Další informace o použití typu `Activity` najdete v [uživatelské příručce aktivity na GitHubu](https://github.com/dotnet/corefx/blob/master/src/System.Diagnostics.DiagnosticSource/src/ActivityUserGuide.md#activity-user-guide) .

Vzhledem k tomu, že DiagnosticSource je součástí základní architektury, je podporována několika základními součástmi, včetně <xref:System.Net.Http.HttpClient>, Entity Framework Core a ASP.NET Core, včetně explicitní podpory v gRPC Framework. Když ASP.NET Core obdrží požadavek, zkontroluje dvojici hlaviček HTTP, které odpovídají standardu [trasování W3C](https://www.w3.org/TR/trace-context) Standard. Pokud jsou hlavičky nalezeny, aktivita se spustí s použitím hodnot identity a kontextu z hlaviček. Pokud se nenajde žádná záhlaví, spustí se aktivita s generovanými hodnotami identity, které odpovídají standardnímu formátu. Jakékoli diagnostiky vygenerované rozhraním nebo kódem aplikace během životnosti této aktivity lze označit pomocí identifikátorů trasování a rozpětí. Podpora `HttpClient` tuto možnost dále rozšiřuje kontrolou aktuální aktivity pro každý požadavek a automatickým přidáním hlaviček trasování do odchozího požadavku.

Mezi klientské a serverové knihovny ASP.NET Core gRPC patří explicitní podpora pro DiagnosticSource a aktivitu a vytvoří se aktivity a použije se k automatickému použití informací v hlavičce.

> [!NOTE]
> K tomuto problému dochází pouze v případě, že *naslouchací proces* spotřebovává diagnostické informace. Pokud žádný naslouchací proces neexistuje, nevytvoří se žádná Diagnostika a nevytvoří se žádné aktivity.

### <a name="add-your-own-diagnosticsources-and-activities"></a>Přidat vlastní DiagnosticSources a aktivity

I když je správné množství dat vygenerováno ASP.NET Core, včetně gRPC, a také Entity Framework Core a `HttpClient`, můžete chtít přidat vlastní diagnostiku nebo vytvořit explicitní rozsahy v rámci kódu aplikace. Podrobnosti o tom, jak implementovat vlastní diagnostiku, najdete v uživatelské příručce pro [uživatele DiagnosticSource](https://github.com/dotnet/corefx/blob/master/src/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md#instrumenting-with-diagnosticsourcediagnosticlistener) a v [uživatelské příručce aktivity](https://github.com/dotnet/corefx/blob/master/src/System.Diagnostics.DiagnosticSource/src/ActivityUserGuide.md#activity-usage) .

### <a name="store-distributed-trace-data"></a>Ukládat data distribuovaného trasování

V době psaní projektu OpenTelemetry je stále v počátečních fázích a k dispozici jsou pouze balíčky s kvalitou alfa pro aplikace .NET. Projekt OpenTracing nabízí více vyspělých knihoven, ale ty budou v budoucnu nahrazeny knihovnami OpenTelemetry.

Rozhraní OpenTracing API je popsané níže. Pokud dáváte přednost použití novějšího rozhraní OpenTelemetry API v aplikaci, podívejte se na [úložiště sady OpenTelemetry .NET SDK na GitHubu](https://github.com/open-telemetry/opentelemetry-dotnet).

#### <a name="use-the-opentracing-package-to-store-distributed-trace-data"></a>Použití balíčku OpenTracing k ukládání dat distribuovaných trasování

[Balíček OpenTracing NuGet](https://www.nuget.org/packages/OpenTracing/) , který podporuje všechny back-endy kompatibilní s OpenTracing, které se dají používat nezávisle na `DiagnosticSource`). K dispozici je další balíček z projektu příspěvky OpenTracing API [OpenTracing. contrib. Netcore](https://www.nuget.org/packages/OpenTracing.Contrib.NetCore/), který přidává `DiagnosticSource` naslouchací proces a zapisuje události a aktivity do back-endu automaticky. Povolení tohoto balíčku je jednoduché, protože ho nainstalujete z NuGet a přidáte ho jako službu ve vaší třídě `Startup`.

```csharp
public class Startup
{
    public void ConfigureServices(IServiceCollection services)
    {
        services.AddOpenTracing();
    }
}
```

Balíček OpenTracing je abstraktní vrstva a jako takový vyžaduje implementaci pro back-end specifickou. Implementace rozhraní API OpenTracing jsou k dispozici pro následující back-endy open source.

| Name | Balíček | Web |
| ---- | ------- | -------- |
| Jaeger | [Jaeger](https://www.nuget.org/packages/Jaeger/) | [jaegertracing.io](https://jaegertracing.io) |
| Elastický APM | [Elastický. APM. NetCoreAll](https://www.nuget.org/packages/Elastic.Apm.NetCoreAll/) | [elastic.co/products/apm](https://www.elastic.co/products/apm) |

Další informace o rozhraní OpenTracing API pro .NET najdete v tématu [OpenTracing for C# ](https://github.com/opentracing/opentracing-csharp) a [OpenTracing C#contrib/.NET Core](https://github.com/opentracing-contrib/csharp-netcore) úložiště na GitHubu.

>[!div class="step-by-step"]
>[Předchozí](load-balancing.md)
>[Další](appendix.md)
