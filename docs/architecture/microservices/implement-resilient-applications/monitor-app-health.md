---
title: Monitorování stavu
description: Prozkoumejte jeden způsob implementace monitorování stavu.
ms.date: 03/02/2020
ms.openlocfilehash: d3d2bc72cf29b3d1ac93191e7ff2bd827c9ee68d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79401709"
---
# <a name="health-monitoring"></a>Monitorování stavu

Monitorování stavu můžete povolit téměř v reálném čase informace o stavu kontejnerů a mikroslužeb. Monitorování stavu je důležité pro více aspektů provoznímikroslužeb a je zvláště důležité, když orchestrátory provádět částečné upgrady aplikací ve fázích, jak je vysvětleno později.

Aplikace založené na mikroslužbách často používají prezenční signály nebo kontroly stavu k povolení jejich sledování výkonu, plánovače a orchestrátory sledovat velké množství služeb. Pokud služby nelze odeslat nějaký signál "Jsem naživu", a to buď na vyžádání nebo podle plánu, aplikace může čelit rizikům při nasazování aktualizací, nebo to může jen zjistit selhání příliš pozdě a není schopen zastavit kaskádové selhání, které mohou skončit v hlavních výpadků.

V typickém modelu služby odesílají sestavy o jejich stavu a tyto informace jsou agregovány tak, aby poskytovaly celkový přehled o stavu vaší aplikace. Pokud používáte orchestrator, můžete poskytnout informace o stavu clusteru orchestrátoru, aby cluster mohl podle toho jednat. Pokud investujete do vysoce kvalitních sestav stavu, které jsou přizpůsobeny pro vaši aplikaci, můžete mnohem snadněji zjistit a opravit problémy pro spuštěnou aplikaci.

## <a name="implement-health-checks-in-aspnet-core-services"></a>Implementace kontrol stavu v ASP.NET základních služeb

Při vývoji mikroslužby ASP.NET Core nebo webové aplikace můžete použít předdefinovanou funkci kontrolstavu, která byla vydána v prostředí ASP .NET Core 2.2 ([Microsoft.Extensions.Diagnostics.HealthChecks](https://www.nuget.org/packages/Microsoft.Extensions.Diagnostics.HealthChecks)). Stejně jako mnoho ASP.NET funkcí core, zdravotní kontroly přicházejí se sadou služeb a middleware.

Služby kontroly stavu a middleware jsou snadno použitelné a poskytují funkce, které umožňují ověřit, zda všechny externí prostředky potřebné pro vaši aplikaci (jako je databáze SERVERU SQL Server nebo vzdálené rozhraní API) funguje správně. Při použití této funkce můžete také rozhodnout, co to znamená, že prostředek je v pořádku, jak vysvětlíme později.

Chcete-li tuto funkci efektivně používat, musíte nejprve nakonfigurovat služby v mikroslužbách. Za druhé potřebujete front-endovou aplikaci, která se dotazuje na sestavy stavu. Tato front-endová aplikace může být vlastní aplikace pro vykazování nebo samotná orchestrator, která může odpovídajícím způsobem reagovat na stavy.

### <a name="use-the-healthchecks-feature-in-your-back-end-aspnet-microservices"></a>Použití funkce HealthChecks v back-endu ASP.NET mikroslužeb

V této části se dozvíte, jak implementovat funkci HealthChecks v ukázkové ASP.NET aplikaci webového rozhraní API Core 3.1 při použití balíčku [Microsoft.Extensions.Diagnostics.HealthChecks.](https://www.nuget.org/packages/Microsoft.Extensions.Diagnostics.HealthChecks) Implementace této funkce ve velkém měřítku mikroslužeb, jako je eShopOnContainers je vysvětleno v další části.

Chcete-li začít, musíte definovat, co představuje stav v pořádku pro každou mikroslužbu. V ukázkové aplikaci definujeme, že mikroslužba je v pořádku, pokud je jeho rozhraní API přístupné přes HTTP a jeho související databáze SQL Serveru je také k dispozici.

V rozhraní .NET Core 3.1 můžete pomocí integrovaných rozhraní API nakonfigurovat služby, přidat kontrolu stavu pro mikroslužbu a její závislou databázi serveru SQL Server tímto způsobem:

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

V předchozím kódu `services.AddHealthChecks()` metoda konfiguruje základní kontrolu HTTP, která vrací stavový kód **200** s "V pořádku".  Dále `AddCheck()` metoda rozšíření konfiguruje vlastní, `SqlConnectionHealthCheck` který kontroluje stav související databáze SQL.

Metoda `AddCheck()` přidá novou kontrolu stavu se zadaným `IHealthCheck`názvem a implementací typu . Pomocí metody AddCheck můžete přidat více kontrol stavu, takže mikroslužba neposkytne stav "v pořádku", dokud nebudou všechny kontroly v pořádku.

`SqlConnectionHealthCheck`je vlastní třída, `IHealthCheck`která implementuje , která přebírá připojovací řetězec jako parametr konstruktoru a provede jednoduchý dotaz ke kontrole, zda je připojení k databázi SQL úspěšné. Vrátí, `HealthCheckResult.Healthy()` pokud byl dotaz úspěšně proveden `FailureStatus` a s skutečnou výjimkou, když se nezdaří.

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

Všimněte si, `Select 1` že v předchozím kódu je dotaz slouží ke kontrole stavu databáze. Chcete-li sledovat dostupnost mikroslužeb, orchestrátory jako Kubernetes pravidelně provádět kontroly stavu odesíláním požadavků na testování mikroslužeb. Je důležité, aby vaše databázové dotazy efektivní tak, aby tyto operace jsou rychlé a nevedou k vyšší využití prostředků.

Nakonec přidejte middleware, který reaguje `/hc`na cestu url :

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

Při vyvolání `<yourmicroservice>/hc` koncového bodu spustí všechny kontroly stavu, `AddHealthChecks()` které jsou nakonfigurovány v metodě ve třídě Startup a zobrazí výsledek.

### <a name="healthchecks-implementation-in-eshoponcontainers"></a>Implementace HealthChecks v eShopOnContainers

Mikroslužby v eShopOnContainers spoléhají na více služeb k provedení své úlohy. Například `Catalog.API` mikroslužba z eShopOnContainers závisí na mnoha službách, jako je azure blob storage, SQL Server a RabbitMQ. Proto má několik kontrol stavu `AddCheck()` přidané pomocí metody. Pro každou závislou `IHealthCheck` službu by bylo nutné přidat vlastní implementaci, která definuje jeho příslušný stav.

Open source projekt [AspNetCore.Diagnostics.HealthChecks](https://github.com/Xabaril/AspNetCore.Diagnostics.HealthChecks) tento problém řeší poskytnutím vlastních implementací kontroly stavu pro každou z těchto podnikových služeb, které jsou postaveny na rozhraní .NET Core 3.1. Každá kontrola stavu je k dispozici jako samostatný balíček NuGet, který lze snadno přidat do projektu. eShopOnContainers je ve velké míře využívá ve všech svých mikroslužbách.

Například v `Catalog.API` mikroslužbě byly přidány následující balíčky NuGet:

![Snímek obrazovky balíčků AspNetCore.Diagnostics.HealthChecks NuGet.](./media/monitor-app-health/aspnet-core-diagnostics-health-checks.png)

**Obrázek 8-7**. Vlastní kontroly stavu implementované v rozhraní Catalog.API pomocí rozhraní AspNetCore.Diagnostics.HealthChecks

V následujícím kódu jsou přidány implementace kontroly stavu pro každou závislou službu a potom je nakonfigurován middleware:

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

Nakonec přidejte middleware HealthCheck pro poslech koncového bodu "/hc":

```csharp
// HealthCheck middleware
app.UseHealthChecks("/hc", new HealthCheckOptions()
{
    Predicate = _ => true,
    ResponseWriter = UIResponseWriter.WriteHealthCheckUIResponse
});
}
```

### <a name="query-your-microservices-to-report-about-their-health-status"></a>Dotaz mikroslužeb pro hlášení o jejich stavu

Když jste nakonfigurovali kontroly stavu, jak je popsáno v tomto článku a máte mikroslužbu spuštěnou v Dockeru, můžete přímo zkontrolovat z prohlížeče, pokud je v pořádku. Musíte publikovat port kontejneru v hostiteli Dockeru, takže můžete přistupovat ke `localhost`kontejneru prostřednictvím externí ip adresy hostitele Dockeru nebo prostřednictvím , jak je znázorněno na obrázku 8-8.

![Snímek obrazovky s odpovědí JSON vrácenou kontrolou stavu.](./media/monitor-app-health/health-check-json-response.png)

**Obrázek 8-8**. Kontrola stavu jedné služby z prohlížeče

V tomto testu uvidíte, `Catalog.API` že mikroslužba (spuštěná na portu 5101) je v pořádku, vrací stav HTTP 200 a informace o stavu v JSON. Služba také zkontrolovala stav závislosti databáze serveru SQL Server a RabbitMQ, takže kontrola stavu se sama hlásila jako v pořádku.

## <a name="use-watchdogs"></a>Použití hlídacích psů

Watchdog je samostatná služba, která můžete sledovat stav a zatížení napříč službami `HealthChecks` a sestavy stavu o mikroslužeb dotazem s knihovnou zavedenou dříve. To může pomoci zabránit chybám, které by nebyly zjištěny na základě zobrazení jedné služby. Watchdogs jsou také vhodné místo pro hostování kódu, který může provádět nápravné akce pro známé podmínky bez interakce s uživatelem.

Ukázka eShopOnContainers obsahuje webovou stránku, která zobrazuje ukázkové zprávy o kontrole stavu, jak je znázorněno na obrázku 8-9. Toto je nejjednodušší hlídací pes, který můžete mít, protože zobrazuje pouze stav mikroslužeb a webových aplikací v eShopOnContainers. Obvykle watchdog také provede akce, když zjistí stavy není v pořádku.

Naštěstí [AspNetCore.Diagnostics.HealthChecks](https://github.com/Xabaril/AspNetCore.Diagnostics.HealthChecks) také poskytuje balíček [AspNetCore.HealthChecks.UI](https://www.nuget.org/packages/AspNetCore.HealthChecks.UI/) NuGet, který lze použít k zobrazení výsledků kontroly stavu z nakonfigurovaných identifikátorů URI.

![Screenshot of the Health Checks UI eShopOnContainers health statuses.](./media/monitor-app-health/health-check-status-ui.png)

**Obrázek 8-9**. Ukázková zpráva o kontrole stavu v eShopOnContainers

V souhrnu tato služba watchdog dotazy každý mikroslužeb "/hc" koncový bod. Tím se spustí všechny kontroly stavu definované v něm a vrátí celkový stav v závislosti na všech těchto kontrol. HealthChecksUI je snadno spotřebovávat s několika položek konfigurace a dva řádky kódu, které je třeba přidat do Startup.cs služby hlídacího psa.

Ukázkový konfigurační soubor pro ui kontroly stavu:

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

Startup.cs soubor, který přidává HealthChecksUI:

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

## <a name="health-checks-when-using-orchestrators"></a>Zdravotní kontroly při použití orchestrátorů

Chcete-li sledovat dostupnost mikroslužeb, orchestrátory jako Kubernetes a Service Fabric pravidelně provádět kontroly stavu odesíláním požadavků na testování mikroslužeb. Když orchestrator zjistí, že služba nebo kontejner není v pořádku, zastaví směrování požadavků na tuto instanci. Také obvykle vytvoří novou instanci tohoto kontejneru.

Většina orchestrátorů může například používat kontroly stavu ke správě nasazení s nulovými prostoji. Pouze v případě, že se stav služby/kontejneru změní na v pořádku, spustí orchestrator směrování provozu do instancí služby/kontejneru.

Monitorování stavu je zvláště důležité, když orchestrátor provede upgrade aplikace. Některé orchestrators (jako Azure Service Fabric) aktualizovat služby ve fázích – například mohou aktualizovat jednu pětinu povrchu clusteru pro každou inovost aplikace. Sada uzlů, která je upgradována současně se označuje jako *doména upgradu*. Po upgradu každé domény upgradu a je k dispozici uživatelům, že upgrade domény musí projít kontroly stavu před nasazení přesune do další domény upgradu.

Dalším aspektem stavu služby je vykazování metrikze služby. Toto je pokročilá schopnost modelu stavu některých orchestrátorů, jako je Service Fabric. Metriky jsou důležité při použití orchestrator, protože se používají k vyrovnání využití prostředků. Metriky mohou být také ukazatelem stavu systému. Můžete mít například aplikaci, která má mnoho mikroslužeb a každá instance hlásí metriku požadavků za sekundu (RPS). Pokud jedna služba používá více prostředků (paměť, procesor atd.) než jiná služba, může orchestrator přesunout instance služby v clusteru a pokusit se zachovat i využití prostředků.

Všimněte si, že Azure Service Fabric poskytuje vlastní [model monitorování stavu](/azure/service-fabric/service-fabric-health-introduction), který je pokročilejší než jednoduché kontroly stavu.

## <a name="advanced-monitoring-visualization-analysis-and-alerts"></a>Pokročilé monitorování: vizualizace, analýza a výstrahy

Poslední část monitorování je vizualizace datového proudu událostí, hlášení o výkonu služby a upozornění při zjištění problému. Pro tento aspekt monitorování můžete použít různá řešení.

Můžete použít jednoduché vlastní aplikace zobrazující stav vašich služeb, například vlastní stránku zobrazenou při vysvětlování [aspNetCore.Diagnostics.HealthChecks](https://github.com/Xabaril/AspNetCore.Diagnostics.HealthChecks). Nebo můžete použít pokročilejší nástroje, jako je [Azure Monitor](https://azure.microsoft.com/services/monitor/) pro zvýšení výstrah na základě proudu událostí.

Pokud ukládáte všechny streamy událostí, můžete k vizualizaci dat použít Microsoft Power BI nebo jiná řešení, jako je Kibana nebo Splunk.

## <a name="additional-resources"></a>Další zdroje

- **Stavové kontroly a kontroly stavu u ASP.NET core** \
  <https://github.com/Xabaril/AspNetCore.Diagnostics.HealthChecks>

- **Úvod do monitorování stavu service fabric** \
  [https://docs.microsoft.com/azure/service-fabric/service-fabric-health-introduction](/azure/service-fabric/service-fabric-health-introduction)

- **Azure Monitor** \
  <https://azure.microsoft.com/services/monitor/>

>[!div class="step-by-step"]
>[Předchozí](implement-circuit-breaker-pattern.md)
>[další](../secure-net-microservices-web-applications/index.md)
