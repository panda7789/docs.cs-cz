---
title: Monitorování stavu
description: Prozkoumejte jeden ze způsobů implementace monitorování stavu.
ms.date: 03/02/2020
ms.openlocfilehash: 3b8ba57149061e629bee441672718eba8a79da63
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/03/2020
ms.locfileid: "78241153"
---
# <a name="health-monitoring"></a>Monitorování stavu

Sledování stavu může poskytnout informace téměř v reálném čase o stavu vašich kontejnerů a mikroslužeb. Monitorování stavu je důležité pro více aspektů provozních mikroslužeb a je obzvláště důležité, když orchestrace provádí částečné upgrady aplikací ve fázích, jak je vysvětleno později.

Aplikace založené na mikroslužbách často využívají prezenční signály nebo kontroly stavu, které umožňují monitorovat výkon, plánovače a orchestraci a sledovat velké množství služeb. Pokud služba nemůže odeslat nějaký druh signálu "I" Alive, a to buď na vyžádání, nebo podle plánu, může vaše aplikace při nasazování aktualizací čelit rizikům, nebo může jenom odhalit selhání, která můžou skončit v hlavních výpadkech.

V typickém modelu odesílají služby zprávy o jejich stavu a tyto informace jsou agregované tak, aby poskytovaly celkový přehled o stavu vaší aplikace. Pokud používáte nástroj Orchestrator, můžete poskytnout informace o stavu do clusteru nástroje Orchestrator, aby cluster mohl pracovat odpovídajícím způsobem. Pokud investujete do vysoce kvalitních sestav o stavu, které jsou pro vaši aplikaci přizpůsobené, můžete zjistit a opravit problémy pro vaši běžící aplikaci mnohem snadněji.

## <a name="implement-health-checks-in-aspnet-core-services"></a>Implementace kontrol stavu ve službě ASP.NET Core Services

Při vývoji ASP.NET Core mikroslužeb nebo webové aplikace můžete použít integrovanou funkci kontroly stavu, která byla vydaná v prostředí ASP .NET Core 2,2 ([Microsoft. Extensions. Diagnostics. HealthChecks](https://www.nuget.org/packages/Microsoft.Extensions.Diagnostics.HealthChecks)). Stejně jako mnoho funkcí ASP.NET Core, jsou kontroly stavu dodávány se sadou služeb a middlewaru.

Služby kontroly stavu a middleware se snadno používají a poskytují možnosti, které vám umožní ověřit, jestli nějaký externí prostředek potřebný pro vaši aplikaci (třeba databáze SQL Server nebo vzdálené rozhraní API) pracuje správně. Když použijete tuto funkci, můžete se také rozhodnout, co znamená, že je prostředek v pořádku, jak je vysvětleno později.

Abyste tuto funkci mohli efektivně používat, musíte nejdřív nakonfigurovat služby ve svých mikroslužbách. Za druhé budete potřebovat front-endové aplikaci, která se dotazuje na sestavy stavu. Tato aplikace front-end může být vlastní aplikací pro vytváření sestav, nebo může být samotným nástrojem Orchestrator, který může odpovídajícím způsobem reagovat na stav.

### <a name="use-the-healthchecks-feature-in-your-back-end-aspnet-microservices"></a>Použití funkce HealthChecks v ASP.NET mikroslužbách back-endu

V této části se dozvíte, jak implementovat funkci HealthChecks v ukázkové aplikaci webového rozhraní API ASP.NET Core 3,1 při použití balíčku [Microsoft. Extensions. Diagnostics. HealthChecks](https://www.nuget.org/packages/Microsoft.Extensions.Diagnostics.HealthChecks) . Implementace této funkce v rozsáhlých mikroslužbách, jako je eShopOnContainers, je vysvětleno v další části.

Chcete-li začít, je třeba definovat, co znamená dobrý stav pro jednotlivé mikroslužby. V ukázkové aplikaci definujeme, že mikroslužba je v pořádku, pokud je její rozhraní API přístupné přes protokol HTTP a k dispozici je také související databáze SQL Server.

V rozhraní .NET Core 3,1 s integrovanými rozhraními API můžete nakonfigurovat služby a přidat kontrolu stavu pro mikroslužbu a její závislé SQL Server databázi tímto způsobem:

```csharp
// Startup.cs from .NET Core 3.1 Web API sample
//
public void ConfigureServices(IServiceCollection services)
{
    //...
    // Registers required services for health checks
    services.AddHealthChecks()
        // Add a health check for a SQL Server database
        .AddCheck(
            "OrderingDB-check", 
            new SqlConnectionHealthCheck(Configuration["ConnectionString"]), 
            HealthStatus.Unhealthy, 
            new string[] { "orderingdb" });
}
```

V předchozím kódu metoda `services.AddHealthChecks()` konfiguruje základní kontrolu HTTP, která vrátí stavový kód **200** s "dobrým".  Dále metoda rozšíření `AddCheck()` konfiguruje vlastní `SqlConnectionHealthCheck`, která kontroluje stav souvisejících SQL Database.

Metoda `AddCheck()` přidá novou kontrolu stavu se zadaným názvem a implementací typu `IHealthCheck`. Pomocí metody AddCheck můžete přidat několik kontrol stavu, takže mikroslužba neposkytne stav "dobrý", dokud nebudou všechny jeho kontroly v pořádku.

`SqlConnectionHealthCheck` je vlastní třída, která implementuje `IHealthCheck`, která používá připojovací řetězec jako parametr konstruktoru a spustí jednoduchý dotaz pro kontrolu úspěšného připojení k databázi SQL. Vrátí `HealthCheckResult.Healthy()`, pokud se dotaz úspěšně provedl a při neúspěchu `FailureStatus` se skutečnou výjimkou.

```csharp
// Sample SQL Connection Health Check
public class SqlConnectionHealthCheck : IHealthCheck
{
    private static readonly string DefaultTestQuery = "Select 1";

    public string ConnectionString { get; }

    public string TestQuery { get; }

    public SqlConnectionHealthCheck(string connectionString)
        : this(connectionString, testQuery: DefaultTestQuery)
    {
    }

    public SqlConnectionHealthCheck(string connectionString, string testQuery)
    {
        ConnectionString = connectionString ?? throw new ArgumentNullException(nameof(connectionString));
        TestQuery = testQuery;
    }

    public async Task<HealthCheckResult> CheckHealthAsync(HealthCheckContext context, CancellationToken cancellationToken = default(CancellationToken))
    {
        using (var connection = new SqlConnection(ConnectionString))
        {
            try
            {
                await connection.OpenAsync(cancellationToken);

                if (TestQuery != null)
                {
                    var command = connection.CreateCommand();
                    command.CommandText = TestQuery;

                    await command.ExecuteNonQueryAsync(cancellationToken);
                }
            }
            catch (DbException ex)
            {
                return new HealthCheckResult(status: context.Registration.FailureStatus, exception: ex);
            }
        }

        return HealthCheckResult.Healthy();
    }
}
```

Všimněte si, že v předchozím kódu je `Select 1` dotazem, který slouží ke kontrole stavu databáze. Aby bylo možné monitorovat dostupnost mikroslužeb, orchestrace, jako je Kubernetes, pravidelně provádějí kontroly stavu tím, že odesílají požadavky na testování mikroslužeb. Je důležité uchovávat dotazy v databázi efektivně, aby tyto operace byly rychlé a nevedly k vyššímu využití prostředků.

Nakonec přidejte middleware, který reaguje na cestu URL `/hc`:

```csharp
// Startup.cs from .NET Core 3.1 Web Api sample
//
public void Configure(IApplicationBuilder app, IHostingEnvironment env)
{
    //…
    app.UseEndpoints(endpoints =>
    {
        //...
        endpoints.MapHealthChecks("/hc");
        //...
    });
    //…
}
```

Po vyvolání koncového bodu `<yourmicroservice>/hc` spustí všechny kontroly stavu, které jsou konfigurovány v metodě `AddHealthChecks()` ve třídě Startup a zobrazí výsledek.

### <a name="healthchecks-implementation-in-eshoponcontainers"></a>Implementace HealthChecks v eShopOnContainers

Mikroslužby v eShopOnContainers spoléhají na provádění svých úkolů více službami. Například `Catalog.API` mikroslužba z eShopOnContainers závisí na mnoha službách, jako je Azure Blob Storage, SQL Server a RabbitMQ. Proto má pomocí metody `AddCheck()` přidáno několik kontrol stavu. Pro každou závislou službu se musí přidat vlastní implementace `IHealthCheck` definující příslušný stav jeho stavu.

Open source projekt [AspNetCore. Diagnostics. HealthChecks](https://github.com/Xabaril/AspNetCore.Diagnostics.HealthChecks) tento problém řeší tím, že poskytuje implementace vlastních kontrol stavu pro každou z těchto podnikových služeb, které jsou postaveny na .net Core 3,1. Každá kontrolu stavu je k dispozici jako samostatný balíček NuGet, který lze snadno přidat do projektu. eShopOnContainers je často používá ve všech mikroslužbách.

Například v `Catalog.API` mikroslužeb byly přidány následující balíčky NuGet:

![Snímek obrazovky s balíčky NuGet AspNetCore. Diagnostics. HealthChecks](./media/monitor-app-health/aspnet-core-diagnostics-health-checks.png)

**Obrázek 8-7**. Vlastní kontroly stavu implementované v katalogu. API pomocí AspNetCore. Diagnostics. HealthChecks

V následujícím kódu jsou pro každou závislou službu přidány implementace kontroly stavu a potom je nakonfigurován middleware:

```csharp
// Startup.cs from Catalog.api microservice
//
public static IServiceCollection AddCustomHealthCheck(this IServiceCollection services, IConfiguration configuration)
{
    var accountName = configuration.GetValue<string>("AzureStorageAccountName");
    var accountKey = configuration.GetValue<string>("AzureStorageAccountKey");

    var hcBuilder = services.AddHealthChecks();

    hcBuilder
        .AddSqlServer(
            configuration["ConnectionString"],
            name: "CatalogDB-check",
            tags: new string[] { "catalogdb" });

    if (!string.IsNullOrEmpty(accountName) && !string.IsNullOrEmpty(accountKey))
    {
        hcBuilder
            .AddAzureBlobStorage(
                $"DefaultEndpointsProtocol=https;AccountName={accountName};AccountKey={accountKey};EndpointSuffix=core.windows.net",
                name: "catalog-storage-check",
                tags: new string[] { "catalogstorage" });
    }
    if (configuration.GetValue<bool>("AzureServiceBusEnabled"))
    {
        hcBuilder
            .AddAzureServiceBusTopic(
                configuration["EventBusConnection"],
                topicName: "eshop_event_bus",
                name: "catalog-servicebus-check",
                tags: new string[] { "servicebus" });
    }
    else
    {
        hcBuilder
            .AddRabbitMQ(
                $"amqp://{configuration["EventBusConnection"]}",
                name: "catalog-rabbitmqbus-check",
                tags: new string[] { "rabbitmqbus" });
    }

    return services;
}
```

Nakonec přidejte middleware HealthCheck pro poslech koncového bodu "/HC":

```csharp
// HealthCheck middleware
app.UseHealthChecks("/hc", new HealthCheckOptions()
{
    Predicate = _ => true,
    ResponseWriter = UIResponseWriter.WriteHealthCheckUIResponse
});
}
```

### <a name="query-your-microservices-to-report-about-their-health-status"></a>Dotazování mikroslužeb na zprávu o jejich stavu

Pokud jste nakonfigurovali kontroly stavu, jak je popsáno v tomto článku, a máte mikroslužbu spuštěnou v Docker, můžete přímo z prohlížeče zkontrolovat, jestli je v pořádku. Musíte publikovat port kontejneru v hostiteli Docker, abyste mohli ke kontejneru přistupovat prostřednictvím IP adresy externího hostitele Docker nebo prostřednictvím `localhost`, jak ukazuje obrázek 8-8.

![Snímek obrazovky s odpovědí JSON vrácenou kontrolou stavu](./media/monitor-app-health/health-check-json-response.png)

**Obrázek 8-8**. Kontrola stavu jedné služby z prohlížeče

V tomto testu vidíte, že `Catalog.API` mikroslužba (běžící na portu 5101) je v pořádku, vrací stav HTTP 200 a informace o stavu ve formátu JSON. Služba také kontrolovala stav své SQL Server závislosti databáze a RabbitMQ, takže se kontrola stavu hlásí jako v pořádku.

## <a name="use-watchdogs"></a>Použití sledovacích zařízení

Sledovací zařízení je samostatná služba, která může sledovat stav a zatížení napříč službami a nahlásit stav mikroslužeb pomocí dotazování pomocí knihovny `HealthChecks` představené dříve. To může zabránit chybám, které se nezjistily na základě zobrazení jedné služby. Sledovací zařízení jsou také dobrým místem pro hostování kódu, který může provádět nápravné akce pro známé podmínky bez zásahu uživatele.

Ukázka eShopOnContainers obsahuje webovou stránku, která zobrazuje ukázkové sestavy kontroly stavu, jak je znázorněno na obrázku 8-9. Toto je nejjednodušší sledovací zařízení, které byste mohli mít, protože zobrazuje jenom stav mikroslužeb a webových aplikací v eShopOnContainers. K tomu obvykle dochází v případě, že zařízení detekuje stav, který není v pořádku.

Naštěstí [AspNetCore. Diagnostics. HealthChecks](https://github.com/Xabaril/AspNetCore.Diagnostics.HealthChecks) také poskytuje balíček NuGet [AspNetCore. HealthChecks. UI](https://www.nuget.org/packages/AspNetCore.HealthChecks.UI/) , který se dá použít k zobrazení výsledků kontroly stavu z konfigurovaných identifikátorů URI.

![Snímek obrazovky eShopOnContainers stavu uživatelského rozhraní kontroly stavu.](./media/monitor-app-health/health-check-status-ui.png)

**Obrázek 8-9**. Ukázka sestavy kontroly stavu v eShopOnContainers

V souhrnu tato služba sledovacích služeb dotazuje každý koncový bod/HC pro jednotlivé mikroslužby. Tím se spustí všechny kontroly stavu, které jsou v něm definované, a vrátí celkový stav v závislosti na všech těchto kontrolách. HealthChecksUI se dá snadno spotřebovat s několika položkami konfigurace a dvěma řádky kódu, které je třeba přidat do Startup.cs služby sledovacích zařízení.

Ukázkový konfigurační soubor pro uživatelské rozhraní kontroly stavu:

```json
// Configuration
{
  "HealthChecks-UI": {
    "HealthChecks": [
      {
        "Name": "Ordering HTTP Check",
        "Uri": "http://localhost:5102/hc"
      },
      {
        "Name": "Ordering HTTP Background Check",
        "Uri": "http://localhost:5111/hc"
      },
      //...
    ]}
}
```

Soubor Startup.cs, který přidává HealthChecksUI:

```csharp
// Startup.cs from WebStatus(Watch Dog) service
//
public void ConfigureServices(IServiceCollection services)
{
    //…
    // Registers required services for health checks
    services.AddHealthChecksUI();
}
//…
public void Configure(IApplicationBuilder app, IHostingEnvironment env)
{
    //…
    app.UseHealthChecksUI(config=> config.UIPath = “/hc-ui”);
    //…
}
```

## <a name="health-checks-when-using-orchestrators"></a>Kontroly stavu při použití orchestrací

Aby bylo možné monitorovat dostupnost mikroslužeb, orchestrace, jako je Kubernetes, a Service Fabric pravidelně provádět kontroly stavu tím, že odesílají požadavky na testování mikroslužeb. Když nástroj Orchestrator zjistí, že služba nebo kontejner není v pořádku, zastaví požadavky na směrování do této instance. Obvykle se tím vytvoří nová instance tohoto kontejneru.

Například většina orchestrací může pomocí kontrol stavu spravovat nasazení s nulovými výpadky. Pouze v případě, že se stav služby nebo kontejneru změní na v pořádku, bude nástroj Orchestrator zahájit směrování provozu do instancí služby/kontejneru.

Monitorování stavu je obzvláště důležité, když nástroj Orchestrator provede upgrade aplikace. Některé orchestrace (jako Azure Service Fabric) aktualizují služby aktualizací ve fázích, například můžou u každého upgradu aplikace aktualizovat jednu pětinu plochy clusteru. Sada uzlů, které jsou upgradovány ve stejnou dobu, se označuje jako *upgradovací doména*. Po upgradu každé upgradované domény a dostupnosti pro uživatele je tato upgradovací doména před přechodem na další upgradovací doménu před nasazením předána kontrolám stavu.

Dalším aspektem stavu služby je hlášení metrik ze služby. Toto je pokročilá funkce modelu stavu některých orchestrací, jako je Service Fabric. Metriky jsou důležité při použití nástroje Orchestrator, protože se používají k vyrovnávání využití prostředků. Metriky také mohou být indikátorem stavu systému. Můžete mít například aplikaci, která má mnoho mikroslužeb a každá instance hlásí metriku požadavků za sekundu (RPS). Pokud jedna služba používá více prostředků (paměť, procesor atd.) než jiná služba, může nástroj Orchestrator přesunout instance služby v rámci clusteru, aby se pokusila udržet ještě využití prostředků.

Všimněte si, že Azure Service Fabric poskytuje svůj vlastní [model monitorování stavu](/azure/service-fabric/service-fabric-health-introduction), což je pokročilejší než jednoduché kontroly stavu.

## <a name="advanced-monitoring-visualization-analysis-and-alerts"></a>Rozšířené monitorování: vizualizace, analýza a výstrahy

Poslední součástí monitorování je vizualizace streamu událostí, generování sestav o výkonu služby a výstraha při zjištění problému. Pro tento aspekt monitorování můžete použít různá řešení.

Můžete použít jednoduché vlastní aplikace ukazující stav vašich služeb, jako je například vlastní stránka, která je zobrazena při vysvětlení rozhraní [AspNetCore. Diagnostics. HealthChecks](https://github.com/Xabaril/AspNetCore.Diagnostics.HealthChecks). Nebo můžete použít pokročilejší nástroje, jako je [Azure monitor](https://azure.microsoft.com/services/monitor/) k vyvolání výstrah na základě datového proudu událostí.

Nakonec, pokud ukládáte všechny streamy událostí, můžete k vizualizaci dat použít Microsoft Power BI nebo jiná řešení, jako je Kibana nebo Splunk.

## <a name="additional-resources"></a>Další zdroje

- **Uživatelské rozhraní HealthChecks a HealthChecks pro ASP.NET Core** \
  <https://github.com/Xabaril/AspNetCore.Diagnostics.HealthChecks>

- **Úvod do Service Fabric monitoring stavu** \
  [https://docs.microsoft.com/azure/service-fabric/service-fabric-health-introduction](/azure/service-fabric/service-fabric-health-introduction)

- **Azure Monitor** \
  <https://azure.microsoft.com/services/monitor/>

>[!div class="step-by-step"]
>[Předchozí](implement-circuit-breaker-pattern.md)
>[Další](../secure-net-microservices-web-applications/index.md)
