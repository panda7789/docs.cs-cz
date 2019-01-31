---
title: Monitorování stavu
description: Prozkoumejte jedním ze způsobů implementace monitorování stavu.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 01/07/2019
ms.openlocfilehash: 4ad13fa4596cc852317a367852b76a9f769caf78
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55259355"
---
# <a name="health-monitoring"></a>Monitorování stavu

Monitorování stavu umožňuje téměř v reálném čase informace o stavu kontejnerů a mikroslužeb. Monitorování stavu je zásadní pro několik aspektů provoz mikroslužeb a je zvlášť důležité při orchestrátorů provést upgrady částečné použití argumentů ve fázích, jak je popsáno později.

Aplikace založená na Mikroslužbách často používají prezenční signály nebo povolit jejich sledování výkonu, plánovače a orchestrátory můžete sledovat různé služby, doplněk pro kontroly stavu. Pokud služby nelze odeslat nějaký druh "Jsem aktivní" signálu na vyžádání nebo podle plánu, může vaše aplikace musí rizika při nasazení aktualizací, nebo může být příliš pozdě. stačí zjišťování chyb a nebylo možné zastavit kaskádové chyby, ke kterým může ukládaly do hlavní výpadků.

V typické modelu služby odesílat zprávy o stavu a zobrazují se tyto informace poskytnout celkový přehled o stavu stavu aplikace. Pokud používáte orchestrator, můžete zadat informace o stavu vaší orchestrator clusteru tak, aby cluster můžete příslušně na ně reagovat. Pokud Investujete do sestav stavu vysoce kvalitní, který je přizpůsobený pro vaši aplikaci, můžete zjistit a opravit problémy pro běžící aplikaci mnohem snadněji.

## <a name="implement-health-checks-in-aspnet-core-services"></a>Doplněk pro kontroly stavu implementace služby ASP.NET Core

Při vytváření mikroslužeb nebo webové aplikace ASP.NET Core, můžete použít funkci kontroly integrované stavu, který byl v prostředí ASP .NET Core 2.2. ASP.NET Core funkce, stav, který kontroluje obsahuje sadu služeb a middleware položek stejně jako mnoho.

Kontrola služby Health a middleware jsou snadné použití a poskytují funkce, které umožňují, kterou můžete ověřit, jestli všechny externí zdroj, vaše aplikace (jako je databáze systému SQL Server nebo vzdálené rozhraní API) potřebuje pracuje správně. Při použití této funkce můžete také rozhodnout, co znamená to, jestli prostředek je v pořádku, protože vám vysvětlíme, později.

Tato funkce efektivně používat, musíte nejdřív nakonfigurovat v mikroslužby. Za druhé budete potřebovat front-endové aplikace, který se dotazuje sestavy o stavu. Který aplikace front-endu může být vlastní aplikace pro vytváření sestav, nebo to může být orchestrátor samotného, můžete odpovídajícím způsobem reagovat na stav.

### <a name="use-the-healthchecks-feature-in-your-back-end-aspnet-microservices"></a>Použití funkce HealthChecks v back-end ASP.NET mikroslužby

V této části se dozvíte, jak se používá funkci HealthChecks v ukázkové aplikaci rozhraní Web API 2.2 technologie ASP.NET Core. Implementaci této funkce ve velkém měřítku mikroslužeb, stejně jako aplikaci eShopOnContainers je vysvětleno v další části. Pokud chcete začít, musíte definovat, co se považuje za bezproblémového stavu u jednotlivých mikroslužeb. V ukázkové aplikaci mikroslužby jsou v pořádku, pokud rozhraní API mikroslužby je přístupná přes protokol HTTP a její související databáze systému SQL Server je také k dispozici.

V .NET Core 2.2 s integrovaná rozhraní API můžete nakonfigurovat služby, přidejte kontroly stavu mikroslužbách a jeho závislé databáze SQL serveru tímto způsobem:

```csharp
// Startup.cs from .NET Core 2.2 Web Api sample
//
public void ConfigureServices(IServiceCollection services)
{
    //...
    // Registers required services for health checks
    services.AddHealthChecks()
    // Add a health check for a SQL database
    .AddCheck("MyDatabase", new SqlConnectionHealthCheck(Configuration["ConnectionStrings:DefaultConnection"]));
}
```

V předchozím kódu `services.AddHealthChecks()` metoda nakonfiguruje základní kontrolu protokolu HTTP, který vrátí stavový kód **200** s "V pořádku".  Další, `AddCheck()` – metoda rozšíření nakonfiguruje vlastní `SqlConnectionHealthCheck` , která zkontroluje stav související SQL Database.

`AddCheck()` Metoda přidá nová kontrola stavu se zadaným názvem a implementaci typu `IHealthCheck`. Můžete přidat více doplněk pro kontroly stavu pomocí metody AddCheck, takže mikroslužbě neposkytne "v pořádku" stav, dokud se všechny jeho kontroly jsou v pořádku.

`SqlConnectionHealthCheck` je vlastní třídu, která implementuje `IHealthCheck`, který přebírá jako parametr konstruktoru připojovací řetězec a provede jednoduchý dotaz ke kontrole, pokud se úspěšně připojíte ke službě SQL database. Vrátí `HealthCheckResult.Healthy()` Pokud byl dotaz proveden úspěšně a `FailureStatus` skutečné výjimku, pokud se nezdaří.

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

Všimněte si, že v předchozím kódu `Select 1` je query sloužící ke kontrole stavu databáze. Pokud chcete monitorovat dostupnost mikroslužby, orchestrátorů, jako je Kubernetes a Service Fabric pravidelně provádět kontroly stavu pomocí zasílání požadavků na test mikroslužby. Je důležité udržovat efektivní dotazy na databázi tak, aby tyto operace jsou rychlé a nemusíte mít za následek vyšší využití prostředků.

Nakonec vytvořte middlewaru, který reaguje na cesty url "HC":

```csharp
// Startup.cs from .NET Core 2.2 Web Api sample
//
public void Configure(IApplicationBuilder app, IHostingEnvironment env)
{
    //…
    app.UseHealthChecks("/hc");
    //…
} 
```

Když koncový bod `<yourmicroservice>/hc` je vyvolána, spuštění všech kontrol stavu, které jsou nakonfigurované v `AddHealthChecks()` metody ve třídě spuštění a zobrazí výsledek.

### <a name="healthchecks-implementation-in-eshoponcontainers"></a>Implementace HealthChecks v aplikaci eShopOnContainers

Mikroslužby v aplikaci eShopOnContainers využívají více služeb k provádění svých úloh. Například `Catalog.API` mikroslužeb v aplikaci eShopOnContainers závisí na mnoha službách, jako je Azure Blob Storage, SQL Server a RabbitMQ. Proto má několik kontroly stavu, které jsou přidány pomocí `AddCheck()` metody. Pro každé závislé službě vlastní `IHealthCheck` implementace, která definuje jeho příslušný stav musí být přidán.

Open source projektu [AspNetCore.Diagnostics.HealthChecks](https://github.com/Xabaril/AspNetCore.Diagnostics.HealthChecks) tento problém řeší tím, že poskytuje implementace vlastních stavových kontroly pro každou z těchto služeb enterprise, které jsou postavené na .NET Core 2.2. Každý kontroly stavu jsou dostupné jako nějakém balíčku NuGet, který lze snadno přidat do projektu. aplikaci eShopOnContainers jejich použití často v jeho mikroslužeb.

Například v `Catalog.API` mikroslužeb, následující byly přidány balíčky NuGet:

![Zobrazení Průzkumníka řešení, ve kterém jsou balíčky AspNetCore.Diagnostics.HealthChecks NuGet odkazovaného projektu Catalog.API](./media/image6.png)

**Obrázek 8-7**. Implementováno v Catalog.API pomocí AspNetCore.Diagnostics.HealthChecks vlastní kontroly stavu

V následujícím kódu implementace kontroly stavu jsou přidány pro každé závislé služby a pak je middleware nakonfigurovat:

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

Nakonec přidáme middleware HealthCheck tak, aby naslouchala na koncový bod "HC":

```csharp
// HealthCheck middleware
app.UseHealthChecks("/hc", new HealthCheckOptions()
{
    Predicate = _ => true,
    ResponseWriter = UIResponseWriter.WriteHealthCheckUIResponse
});
}
```

### <a name="query-your-microservices-to-report-about-their-health-status"></a>Dotazování mikroslužby na zprávu o jejich stavu

Pokud jste nakonfigurovali kontroly stavu, jak je popsáno v tomto článku a máte mikroslužeb spuštěné v Dockeru, můžete přímo zkontrolovat z prohlížeče pokud je v pořádku. Máte-li publikovat port kontejneru do hostitele Docker, aby měli přístup k kontejneru prostřednictvím externí IP adresa hostitele Dockeru nebo prostřednictvím `localhost`, jak je znázorněno na obrázku 8-8.

![Zobrazení prohlížeče s JSON odpovědi vrácené Kontrola stavu](./media/image7.png)

**Obrázek 8 – 8**. Kontroluje se stav jedinou službou v prohlížeči

V testu, vidíte, že `Catalog.API` mikroslužeb (spuštěné na portu 5101) je v pořádku, vrací stav protokolu HTTP 200 a informace o stavu ve formátu JSON. Službu také kontroluje stav jeho závislostí databáze systému SQL Server a RabbitMQ, tak Kontrola stavu se samo jako v pořádku.

## <a name="use-watchdogs"></a>Použití watchdogs

Sledovacího zařízení je samostatná služba, která může sledovat stav a načíst pomocí dotazu s napříč službami a stavu sestavy o mikroslužbách `HealthChecks` dříve zavedené knihovny. To může pomoci zabránit chybám, které nebudou zjištěny založené na zobrazení jedné služby. Watchdogs je také vhodné místo pro hostování kódu, který může provádět nápravné akce pro známé podmínky bez zásahu uživatele.

Ukázkové aplikaci eShopOnContainers obsahuje webovou stránku, která zobrazí ukázkové sestavy stavu zaškrtnutí, jak ukazuje obrázek 8 až 9. Toto je nejjednodušší sledovacího zařízení, které by mohly mít, protože pouze zobrazuje stav mikroslužbách a webových aplikací v aplikaci eShopOnContainers. Obvykle sledovacího zařízení také provede akce při zjišťuje stavy není v pořádku.

Naštěstí [AspNetCore.Diagnostics.HealthChecks](https://github.com/Xabaril/AspNetCore.Diagnostics.HealthChecks) také poskytuje [AspNetCore.HealthChecks.UI](https://www.nuget.org/packages/AspNetCore.HealthChecks.UI/) balíčku NuGet, který slouží k zobrazení stavu zaškrtnutí vyplývá z nakonfigurovaných identifikátorů URI.

![Zobrazit v prohlížeči WebStatus aplikace, která zobrazuje stav všechny mikroslužby v aplikaci eShopOnContainers](./media/image8.png)

**Obrázek 8 až 9**. Ukázková sestava kontroly stavu v aplikaci eShopOnContainers

Stručně řečeno tato služba sledovacích dotazuje koncového bodu "HC" jednotlivých mikroslužeb. To spustí všechny kontroly stavu, v něm definovanou a vrátit celkového přehledu o stavu v závislosti na těchto kontrol. HealthChecksUI je jednoduše využít několik položek konfigurace a dva řádky kódu, který musí být přidán do souboru Startup.cs sady sledovacího zařízení služby.

Ukázkový konfigurační soubor pro stav zkontrolujte uživatelského rozhraní:

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

Startup.cs souboru, který přidá HealthChecksUI:

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

## <a name="health-checks-when-using-orchestrators"></a>Kontroly stavu při použití orchestrátorů

Pokud chcete monitorovat dostupnost mikroslužby, orchestrátorů, jako je Kubernetes a Service Fabric pravidelně provádět kontroly stavu pomocí zasílání požadavků na test mikroslužby. Když orchestrátor zjistí, že služby/kontejneru není v pořádku, že zastaví směrování požadavků do této instance. Také obvykle vytvoří novou instanci kontejneru.

Většina orchestrátorů, můžete použít kontroly stavu pro správu nasazení s nulovými výpadky. Pouze v případě, že bude stav kontejneru služby/změny v pořádku orchestrátoru start směrování provozu do služby a container instances.

Monitorování stavu je obzvláště důležité, když orchestrátor provádí upgrade aplikace. Některé zvolené orchestrátory (jako je Azure Service Fabric) aktualizovat služby ve fázích – například může aktualizovat jeden pátého povrchu clusteru pro každý upgrade aplikace. Sada uzlů, který se upgraduje ve stejnou dobu se označuje jako *upgradovací doména*. Po každé upgradovací doména byl upgradován a je k dispozici pro uživatele, že upgradovací doména musí uplynout kontroly stavu nasazení přejde k další upgradovací doméně.

Dalším aspektem služby service health je generování sestav metrik ze služby. Toto je rozšířená možnost modelu stavu některé zvolené orchestrátory, jako je Service Fabric. Metriky jsou důležité při použití orchestrator, protože se používají k vyrovnávání využití prostředků. Metriky taky může být indikátor stavu systému. Například může mít aplikaci, která má mnoho mikroslužeb a každá instance sestav metriky požadavků za sekundu (předávajících stran). Pokud jedna služba používá další prostředky (paměť, procesor, atd.) než jiné službě, orchestrator může pohybovat instance služby v clusteru se pokouší spravovat i využití prostředků.

Všimněte si, že Azure Service Fabric nabízí svůj vlastní [monitorování stavu modelu](/azure/service-fabric/service-fabric-health-introduction), což je složitější než kontroly stavu jednoduché.

## <a name="advanced-monitoring-visualization-analysis-and-alerts"></a>Rozšířené monitorování: vizualizace, analýzy a upozornění

Poslední část monitorování je vizualizace datového proudu událostí, vytváření sestav o výkonu služby a upozorní při zjištění problému. Můžete použít různá řešení pro tento aspekt monitorování.

Můžete použít jednoduchý vlastní aplikace zobrazuje stav služeb, jako je vlastní stránka při s vysvětlením, [AspNetCore.Diagnostics.HealthChecks](https://github.com/Xabaril/AspNetCore.Diagnostics.HealthChecks). Nebo můžete použít rozšířené nástroje, jako je Azure Application Insights budou generovány výstrahy založené na události datového proudu.

Nakonec pokud uložená všechny streamy událostí, můžete použít Microsoft Power BI nebo jiné řešení, jako je Kibana nebo Splunk k vizualizaci dat.

## <a name="additional-resources"></a>Další zdroje

-   **HealthChecks a HealthChecks uživatelského rozhraní pro ASP.NET Core**
    [*https://github.com/Xabaril/AspNetCore.Diagnostics.HealthChecks*](https://github.com/Xabaril/AspNetCore.Diagnostics.HealthChecks )

-   **Úvod do monitorování stavu Service Fabric**
    [*https://docs.microsoft.com/azure/service-fabric/service-fabric-health-introduction*](/azure/service-fabric/service-fabric-health-introduction)

-   **Azure Application Insights**
    [*https://azure.microsoft.com/services/application-insights/*](https://azure.microsoft.com/services/application-insights/)

-   **Microsoft Operations Management Suite**
    [*https://www.microsoft.com/en-us/cloud-platform/operations-management-suite*](https://www.microsoft.com/en-us/cloud-platform/operations-management-suite)

>[!div class="step-by-step"]
>[Předchozí](implement-circuit-breaker-pattern.md)
>[další](../secure-net-microservices-web-applications/index.md)