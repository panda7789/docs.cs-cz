---
title: Monitorování stavu
description: Prozkoumejte jeden ze způsobů implementace monitorování stavu.
ms.date: 01/07/2019
ms.openlocfilehash: f1d63e04bbea95fcf0a9f9d3b50aef0e7d4a830e
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2019
ms.locfileid: "73732883"
---
# <a name="health-monitoring"></a><span data-ttu-id="50c32-103">Monitorování stavu</span><span class="sxs-lookup"><span data-stu-id="50c32-103">Health monitoring</span></span>

<span data-ttu-id="50c32-104">Sledování stavu může poskytnout informace téměř v reálném čase o stavu vašich kontejnerů a mikroslužeb.</span><span class="sxs-lookup"><span data-stu-id="50c32-104">Health monitoring can allow near-real-time information about the state of your containers and microservices.</span></span> <span data-ttu-id="50c32-105">Monitorování stavu je důležité pro více aspektů provozních mikroslužeb a je obzvláště důležité, když orchestrace provádí částečné upgrady aplikací ve fázích, jak je vysvětleno později.</span><span class="sxs-lookup"><span data-stu-id="50c32-105">Health monitoring is critical to multiple aspects of operating microservices and is especially important when orchestrators perform partial application upgrades in phases, as explained later.</span></span>

<span data-ttu-id="50c32-106">Aplikace založené na mikroslužbách často využívají prezenční signály nebo kontroly stavu, které umožňují monitorovat výkon, plánovače a orchestraci a sledovat velké množství služeb.</span><span class="sxs-lookup"><span data-stu-id="50c32-106">Microservices-based applications often use heartbeats or health checks to enable their performance monitors, schedulers, and orchestrators to keep track of the multitude of services.</span></span> <span data-ttu-id="50c32-107">Pokud služba nemůže odeslat nějaký druh signálu "I" Alive, a to buď na vyžádání, nebo podle plánu, může vaše aplikace při nasazování aktualizací čelit rizikům, nebo může jenom odhalit selhání, která můžou skončit v hlavních výpadkech.</span><span class="sxs-lookup"><span data-stu-id="50c32-107">If services cannot send some sort of “I’m alive” signal, either on demand or on a schedule, your application might face risks when you deploy updates, or it might just detect failures too late and not be able to stop cascading failures that can end up in major outages.</span></span>

<span data-ttu-id="50c32-108">V typickém modelu odesílají služby zprávy o jejich stavu a tyto informace jsou agregované tak, aby poskytovaly celkový přehled o stavu vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="50c32-108">In the typical model, services send reports about their status, and that information is aggregated to provide an overall view of the state of health of your application.</span></span> <span data-ttu-id="50c32-109">Pokud používáte nástroj Orchestrator, můžete poskytnout informace o stavu do clusteru nástroje Orchestrator, aby cluster mohl pracovat odpovídajícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="50c32-109">If you're using an orchestrator, you can provide health information to your orchestrator’s cluster, so that the cluster can act accordingly.</span></span> <span data-ttu-id="50c32-110">Pokud investujete do vysoce kvalitních sestav o stavu, které jsou pro vaši aplikaci přizpůsobené, můžete zjistit a opravit problémy pro vaši běžící aplikaci mnohem snadněji.</span><span class="sxs-lookup"><span data-stu-id="50c32-110">If you invest in high-quality health reporting that's customized for your application, you can detect and fix issues for your running application much more easily.</span></span>

## <a name="implement-health-checks-in-aspnet-core-services"></a><span data-ttu-id="50c32-111">Implementace kontrol stavu ve službě ASP.NET Core Services</span><span class="sxs-lookup"><span data-stu-id="50c32-111">Implement health checks in ASP.NET Core services</span></span>

<span data-ttu-id="50c32-112">Při vývoji ASP.NET Core mikroslužeb nebo webové aplikace můžete použít integrovanou funkci kontroly stavu, která byla vydaná v prostředí ASP .NET Core 2,2.</span><span class="sxs-lookup"><span data-stu-id="50c32-112">When developing an ASP.NET Core microservice or web application, you can use the built-in health checks feature that was released in ASP .NET Core 2.2.</span></span> <span data-ttu-id="50c32-113">Stejně jako mnoho funkcí ASP.NET Core, jsou kontroly stavu dodávány se sadou služeb a middlewaru.</span><span class="sxs-lookup"><span data-stu-id="50c32-113">Like many ASP.NET Core features, health checks come with a set of services and a middleware.</span></span>

<span data-ttu-id="50c32-114">Služby kontroly stavu a middleware se snadno používají a poskytují možnosti, které vám umožní ověřit, jestli nějaký externí prostředek potřebný pro vaši aplikaci (třeba databáze SQL Server nebo vzdálené rozhraní API) pracuje správně.</span><span class="sxs-lookup"><span data-stu-id="50c32-114">Health check services and middleware are easy to use and provide capabilities that let you validate if any external resource needed for your application (like a SQL Server database or a remote API) is working properly.</span></span> <span data-ttu-id="50c32-115">Když použijete tuto funkci, můžete se také rozhodnout, co znamená, že je prostředek v pořádku, jak je vysvětleno později.</span><span class="sxs-lookup"><span data-stu-id="50c32-115">When you use this feature, you can also decide what it means that the resource is healthy, as we explain later.</span></span>

<span data-ttu-id="50c32-116">Abyste tuto funkci mohli efektivně používat, musíte nejdřív nakonfigurovat služby ve svých mikroslužbách.</span><span class="sxs-lookup"><span data-stu-id="50c32-116">To use this feature effectively, you need to first configure services in your microservices.</span></span> <span data-ttu-id="50c32-117">Za druhé budete potřebovat front-endové aplikaci, která se dotazuje na sestavy stavu.</span><span class="sxs-lookup"><span data-stu-id="50c32-117">Second, you need a front-end application that queries for the health reports.</span></span> <span data-ttu-id="50c32-118">Tato aplikace front-end může být vlastní aplikací pro vytváření sestav, nebo může být samotným nástrojem Orchestrator, který může odpovídajícím způsobem reagovat na stav.</span><span class="sxs-lookup"><span data-stu-id="50c32-118">That front-end application could be a custom reporting application, or it could be an orchestrator itself that can react accordingly to the health states.</span></span>

### <a name="use-the-healthchecks-feature-in-your-back-end-aspnet-microservices"></a><span data-ttu-id="50c32-119">Použití funkce HealthChecks v ASP.NET mikroslužbách back-endu</span><span class="sxs-lookup"><span data-stu-id="50c32-119">Use the HealthChecks feature in your back-end ASP.NET microservices</span></span>

<span data-ttu-id="50c32-120">V této části se dozvíte, jak se funkce HealthChecks používá v ukázkové aplikaci webového rozhraní API ASP.NET Core 2,2.</span><span class="sxs-lookup"><span data-stu-id="50c32-120">In this section, you will learn how the HealthChecks feature is used in a sample ASP.NET Core 2.2 Web API application.</span></span> <span data-ttu-id="50c32-121">Implementace této funkce v rozsáhlých mikroslužbách škály, jako je eShopOnContainers, je vysvětleno v další části.</span><span class="sxs-lookup"><span data-stu-id="50c32-121">Implementation of this feature in a large scale microservices like the eShopOnContainers is explained in the later section.</span></span> <span data-ttu-id="50c32-122">Chcete-li začít, je třeba definovat, co znamená dobrý stav pro jednotlivé mikroslužby.</span><span class="sxs-lookup"><span data-stu-id="50c32-122">To begin, you need to define what constitutes a healthy status for each microservice.</span></span> <span data-ttu-id="50c32-123">V ukázkové aplikaci jsou mikroslužby v dobrém stavu, pokud je k dispozici rozhraní API mikroslužeb přes protokol HTTP a k dispozici je také související databáze SQL Server.</span><span class="sxs-lookup"><span data-stu-id="50c32-123">In the sample application, the microservices are healthy if the microservice API is accessible via HTTP and its related SQL Server database is also available.</span></span>

<span data-ttu-id="50c32-124">V rozhraní .NET Core 2,2 s integrovanými rozhraními API můžete nakonfigurovat služby a přidat kontrolu stavu pro mikroslužbu a její závislé SQL Server databázi tímto způsobem:</span><span class="sxs-lookup"><span data-stu-id="50c32-124">In .NET Core 2.2, with the built-in APIs, you can configure the services, add a Health Check for the microservice and its dependent SQL Server database in this way:</span></span>

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

<span data-ttu-id="50c32-125">V předchozím kódu metoda `services.AddHealthChecks()` konfiguruje základní kontrolu HTTP, která vrátí stavový kód **200** s "dobrým".</span><span class="sxs-lookup"><span data-stu-id="50c32-125">In the previous code, the `services.AddHealthChecks()` method configures a basic HTTP check that returns a status code **200** with “Healthy”.</span></span>  <span data-ttu-id="50c32-126">Dále metoda rozšíření `AddCheck()` konfiguruje vlastní `SqlConnectionHealthCheck`, která kontroluje stav souvisejících SQL Database.</span><span class="sxs-lookup"><span data-stu-id="50c32-126">Further, the `AddCheck()` extension method configures a custom `SqlConnectionHealthCheck` that checks the related SQL Database’s health.</span></span>

<span data-ttu-id="50c32-127">Metoda `AddCheck()` přidá novou kontrolu stavu se zadaným názvem a implementací typu `IHealthCheck`.</span><span class="sxs-lookup"><span data-stu-id="50c32-127">The `AddCheck()` method adds a new health check with a specified name and the implementation of type `IHealthCheck`.</span></span> <span data-ttu-id="50c32-128">Pomocí metody AddCheck můžete přidat několik kontrol stavu, takže mikroslužba neposkytne stav "dobrý", dokud nebudou všechny jeho kontroly v pořádku.</span><span class="sxs-lookup"><span data-stu-id="50c32-128">You can add multiple Health Checks using AddCheck method, so a microservice won't provide a “healthy” status until all its checks are healthy.</span></span>

<span data-ttu-id="50c32-129">`SqlConnectionHealthCheck` je vlastní třída, která implementuje `IHealthCheck`, která používá připojovací řetězec jako parametr konstruktoru a spustí jednoduchý dotaz pro kontrolu úspěšného připojení k databázi SQL.</span><span class="sxs-lookup"><span data-stu-id="50c32-129">`SqlConnectionHealthCheck` is a custom class that implements `IHealthCheck`, which takes a connection string as a constructor parameter and executes a simple query to check if the connection to the SQL database is successful.</span></span> <span data-ttu-id="50c32-130">Vrátí `HealthCheckResult.Healthy()`, pokud se dotaz úspěšně provedl a při neúspěchu `FailureStatus` se skutečnou výjimkou.</span><span class="sxs-lookup"><span data-stu-id="50c32-130">It returns `HealthCheckResult.Healthy()` if the query was executed successfully and a `FailureStatus` with the actual exception when it fails.</span></span>

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

<span data-ttu-id="50c32-131">Všimněte si, že v předchozím kódu je `Select 1` dotazem, který slouží ke kontrole stavu databáze.</span><span class="sxs-lookup"><span data-stu-id="50c32-131">Note that in the previous code, `Select 1` is the query used to check the Health of the database.</span></span> <span data-ttu-id="50c32-132">Aby bylo možné monitorovat dostupnost mikroslužeb, orchestrace, jako je Kubernetes, a Service Fabric pravidelně provádět kontroly stavu tím, že odesílají požadavky na testování mikroslužeb.</span><span class="sxs-lookup"><span data-stu-id="50c32-132">To monitor the availability of your microservices, orchestrators like Kubernetes and Service Fabric periodically perform health checks by sending requests to test the microservices.</span></span> <span data-ttu-id="50c32-133">Je důležité uchovávat dotazy v databázi efektivně, aby tyto operace byly rychlé a nevedly k vyššímu využití prostředků.</span><span class="sxs-lookup"><span data-stu-id="50c32-133">It's important to keep your database queries efficient so that these operations are quick and don’t result in a higher utilization of resources.</span></span>

<span data-ttu-id="50c32-134">Nakonec vytvořte middleware, který reaguje na cestu URL/HC:</span><span class="sxs-lookup"><span data-stu-id="50c32-134">Finally, create a middleware that responds to the url path “/hc”:</span></span>

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

<span data-ttu-id="50c32-135">Po vyvolání koncového bodu `<yourmicroservice>/hc` spustí všechny kontroly stavu, které jsou konfigurovány v metodě `AddHealthChecks()` ve třídě Startup a zobrazí výsledek.</span><span class="sxs-lookup"><span data-stu-id="50c32-135">When the endpoint `<yourmicroservice>/hc` is invoked, it runs all the health checks that are configured in the `AddHealthChecks()` method in the Startup class and shows the result.</span></span>

### <a name="healthchecks-implementation-in-eshoponcontainers"></a><span data-ttu-id="50c32-136">Implementace HealthChecks v eShopOnContainers</span><span class="sxs-lookup"><span data-stu-id="50c32-136">HealthChecks implementation in eShopOnContainers</span></span>

<span data-ttu-id="50c32-137">Mikroslužby v eShopOnContainers spoléhají na provádění svých úkolů více službami.</span><span class="sxs-lookup"><span data-stu-id="50c32-137">Microservices in eShopOnContainers rely on multiple services to perform its task.</span></span> <span data-ttu-id="50c32-138">Například `Catalog.API` mikroslužba z eShopOnContainers závisí na mnoha službách, jako je Azure Blob Storage, SQL Server a RabbitMQ.</span><span class="sxs-lookup"><span data-stu-id="50c32-138">For example, the `Catalog.API` microservice from eShopOnContainers depends on many services, such as Azure Blob Storage, SQL Server, and RabbitMQ.</span></span> <span data-ttu-id="50c32-139">Proto má pomocí metody `AddCheck()` přidáno několik kontrol stavu.</span><span class="sxs-lookup"><span data-stu-id="50c32-139">Therefore, it has several health checks added using the `AddCheck()` method.</span></span> <span data-ttu-id="50c32-140">Pro každou závislou službu musí být přidána vlastní implementace `IHealthCheck` definující příslušný stav jeho stavu.</span><span class="sxs-lookup"><span data-stu-id="50c32-140">For every dependent service, a custom `IHealthCheck` implementation that defines its respective health status needs to be added.</span></span>

<span data-ttu-id="50c32-141">Open source projekt [AspNetCore. Diagnostics. HealthChecks](https://github.com/Xabaril/AspNetCore.Diagnostics.HealthChecks) tento problém vyřeší tím, že poskytuje implementace vlastního ověření stavu pro každou z těchto podnikových služeb, které jsou postaveny na .net Core 2,2.</span><span class="sxs-lookup"><span data-stu-id="50c32-141">The open-source project [AspNetCore.Diagnostics.HealthChecks](https://github.com/Xabaril/AspNetCore.Diagnostics.HealthChecks) solves this problem by providing custom health check implementations for each of these enterprise services that are built on top of .NET Core 2.2.</span></span> <span data-ttu-id="50c32-142">Každá kontrolu stavu je k dispozici jako samostatný balíček NuGet, který lze snadno přidat do projektu.</span><span class="sxs-lookup"><span data-stu-id="50c32-142">Each health check is available as an individual NuGet package that can be easily added to the project.</span></span> <span data-ttu-id="50c32-143">eShopOnContainers je často používejte ve všech mikroslužbách.</span><span class="sxs-lookup"><span data-stu-id="50c32-143">eShopOnContainers use them extensively in all its microservices.</span></span>

<span data-ttu-id="50c32-144">Například v `Catalog.API` mikroslužeb byly přidány následující balíčky NuGet:</span><span class="sxs-lookup"><span data-stu-id="50c32-144">For instance, in the `Catalog.API` microservice, the following NuGet packages were added:</span></span>

![Snímek obrazovky s balíčky NuGet AspNetCore. Diagnostics. HealthChecks](./media/monitor-app-health/aspnet-core-diagnostics-health-checks.png)

<span data-ttu-id="50c32-146">**Obrázek 8-7**.</span><span class="sxs-lookup"><span data-stu-id="50c32-146">**Figure 8-7**.</span></span> <span data-ttu-id="50c32-147">Vlastní kontroly stavu implementované v katalogu. API pomocí AspNetCore. Diagnostics. HealthChecks</span><span class="sxs-lookup"><span data-stu-id="50c32-147">Custom Health Checks implemented in Catalog.API using AspNetCore.Diagnostics.HealthChecks</span></span>

<span data-ttu-id="50c32-148">V následujícím kódu jsou pro každou závislou službu přidány implementace kontroly stavu a potom je nakonfigurován middleware:</span><span class="sxs-lookup"><span data-stu-id="50c32-148">In the following code, the health check implementations are added for each dependent service and then the middleware is configured:</span></span>

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

<span data-ttu-id="50c32-149">Nakonec přidáme middleware HealthCheck, který bude naslouchat koncovému bodu "/HC":</span><span class="sxs-lookup"><span data-stu-id="50c32-149">Finally, we add the HealthCheck middleware to listen to “/hc” endpoint:</span></span>

```csharp
// HealthCheck middleware
app.UseHealthChecks("/hc", new HealthCheckOptions()
{
    Predicate = _ => true,
    ResponseWriter = UIResponseWriter.WriteHealthCheckUIResponse
});
}
```

### <a name="query-your-microservices-to-report-about-their-health-status"></a><span data-ttu-id="50c32-150">Dotazování mikroslužeb na zprávu o jejich stavu</span><span class="sxs-lookup"><span data-stu-id="50c32-150">Query your microservices to report about their health status</span></span>

<span data-ttu-id="50c32-151">Pokud jste nakonfigurovali kontroly stavu, jak je popsáno v tomto článku, a máte mikroslužbu spuštěnou v Docker, můžete přímo z prohlížeče zkontrolovat, jestli je v pořádku.</span><span class="sxs-lookup"><span data-stu-id="50c32-151">When you've configured health checks as described in this article and you have the microservice running in Docker, you can directly check from a browser if it's healthy.</span></span> <span data-ttu-id="50c32-152">Musíte publikovat port kontejneru v hostiteli Docker, abyste mohli ke kontejneru přistupovat prostřednictvím IP adresy externího hostitele Docker nebo prostřednictvím `localhost`, jak ukazuje obrázek 8-8.</span><span class="sxs-lookup"><span data-stu-id="50c32-152">You have to publish the container port in the Docker host, so you can access the container through the external Docker host IP or through `localhost`, as shown in figure 8-8.</span></span>

![Snímek obrazovky s odpovědí JSON vrácenou kontrolou stavu](./media/monitor-app-health/health-check-json-response.png)

<span data-ttu-id="50c32-154">**Obrázek 8-8**.</span><span class="sxs-lookup"><span data-stu-id="50c32-154">**Figure 8-8**.</span></span> <span data-ttu-id="50c32-155">Kontrola stavu jedné služby z prohlížeče</span><span class="sxs-lookup"><span data-stu-id="50c32-155">Checking health status of a single service from a browser</span></span>

<span data-ttu-id="50c32-156">V tomto testu vidíte, že `Catalog.API` mikroslužba (běžící na portu 5101) je v pořádku, vrací stav HTTP 200 a informace o stavu ve formátu JSON.</span><span class="sxs-lookup"><span data-stu-id="50c32-156">In that test, you can see that the `Catalog.API` microservice (running on port 5101) is healthy, returning HTTP status 200 and status information in JSON.</span></span> <span data-ttu-id="50c32-157">Služba také kontrolovala stav své SQL Server závislosti databáze a RabbitMQ, takže se kontrola stavu hlásí jako v pořádku.</span><span class="sxs-lookup"><span data-stu-id="50c32-157">The service also checked the health of its SQL Server database dependency and RabbitMQ, so the health check reported itself as healthy.</span></span>

## <a name="use-watchdogs"></a><span data-ttu-id="50c32-158">Použití sledovacích zařízení</span><span class="sxs-lookup"><span data-stu-id="50c32-158">Use watchdogs</span></span>

<span data-ttu-id="50c32-159">Sledovací zařízení je samostatná služba, která může sledovat stav a zatížení napříč službami a nahlásit stav mikroslužeb pomocí dotazování pomocí knihovny `HealthChecks` představené dříve.</span><span class="sxs-lookup"><span data-stu-id="50c32-159">A watchdog is a separate service that can watch health and load across services, and report health about the microservices by querying with the `HealthChecks` library introduced earlier.</span></span> <span data-ttu-id="50c32-160">To může zabránit chybám, které se nezjistily na základě zobrazení jedné služby.</span><span class="sxs-lookup"><span data-stu-id="50c32-160">This can help prevent errors that would not be detected based on the view of a single service.</span></span> <span data-ttu-id="50c32-161">Sledovací zařízení jsou také dobrým místem pro hostování kódu, který může provádět nápravné akce pro známé podmínky bez zásahu uživatele.</span><span class="sxs-lookup"><span data-stu-id="50c32-161">Watchdogs also are a good place to host code that can perform remediation actions for known conditions without user interaction.</span></span>

<span data-ttu-id="50c32-162">Ukázka eShopOnContainers obsahuje webovou stránku, která zobrazuje ukázkové sestavy kontroly stavu, jak je znázorněno na obrázku 8-9.</span><span class="sxs-lookup"><span data-stu-id="50c32-162">The eShopOnContainers sample contains a web page that displays sample health check reports, as shown in Figure 8-9.</span></span> <span data-ttu-id="50c32-163">Toto je nejjednodušší sledovací zařízení, které byste mohli mít, protože zobrazuje jenom stav mikroslužeb a webových aplikací v eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="50c32-163">This is the simplest watchdog you could have since it only shows the state of the microservices and web applications in eShopOnContainers.</span></span> <span data-ttu-id="50c32-164">K tomu obvykle dochází v případě, že zařízení detekuje stav, který není v pořádku.</span><span class="sxs-lookup"><span data-stu-id="50c32-164">Usually a watchdog also takes actions when it detects unhealthy states.</span></span>

<span data-ttu-id="50c32-165">Naštěstí [AspNetCore. Diagnostics. HealthChecks](https://github.com/Xabaril/AspNetCore.Diagnostics.HealthChecks) také poskytuje balíček NuGet [AspNetCore. HealthChecks. UI](https://www.nuget.org/packages/AspNetCore.HealthChecks.UI/) , který se dá použít k zobrazení výsledků kontroly stavu z konfigurovaných identifikátorů URI.</span><span class="sxs-lookup"><span data-stu-id="50c32-165">Fortunately, [AspNetCore.Diagnostics.HealthChecks](https://github.com/Xabaril/AspNetCore.Diagnostics.HealthChecks) also provides [AspNetCore.HealthChecks.UI](https://www.nuget.org/packages/AspNetCore.HealthChecks.UI/) NuGet package that can be used to display the health check results from the configured URIs.</span></span>

![Snímek obrazovky eShopOnContainers stavu uživatelského rozhraní kontroly stavu.](./media/monitor-app-health/health-check-status-ui.png)

<span data-ttu-id="50c32-167">**Obrázek 8-9**.</span><span class="sxs-lookup"><span data-stu-id="50c32-167">**Figure 8-9**.</span></span> <span data-ttu-id="50c32-168">Ukázka sestavy kontroly stavu v eShopOnContainers</span><span class="sxs-lookup"><span data-stu-id="50c32-168">Sample health check report in eShopOnContainers</span></span>

<span data-ttu-id="50c32-169">V souhrnu tato služba sledovacích služeb dotazuje každý koncový bod/HC pro jednotlivé mikroslužby.</span><span class="sxs-lookup"><span data-stu-id="50c32-169">In summary, this watchdog service queries each microservice’s "/hc" endpoint.</span></span> <span data-ttu-id="50c32-170">Tím se spustí všechny kontroly stavu, které jsou v něm definované, a vrátí celkový stav v závislosti na všech těchto kontrolách.</span><span class="sxs-lookup"><span data-stu-id="50c32-170">This will execute all the health checks defined within it and return an overall health state depending on all those checks.</span></span> <span data-ttu-id="50c32-171">HealthChecksUI se dá snadno spotřebovat s několika položkami konfigurace a dvěma řádky kódu, které je třeba přidat do Startup.cs služby sledovacích zařízení.</span><span class="sxs-lookup"><span data-stu-id="50c32-171">The HealthChecksUI is easy to consume with a few configuration entries and two lines of code that needs to be added into the Startup.cs of the watchdog service.</span></span>

<span data-ttu-id="50c32-172">Ukázkový konfigurační soubor pro uživatelské rozhraní kontroly stavu:</span><span class="sxs-lookup"><span data-stu-id="50c32-172">Sample configuration file for health check UI:</span></span>

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

<span data-ttu-id="50c32-173">Soubor Startup.cs, který přidává HealthChecksUI:</span><span class="sxs-lookup"><span data-stu-id="50c32-173">Startup.cs file that adds HealthChecksUI:</span></span>

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

## <a name="health-checks-when-using-orchestrators"></a><span data-ttu-id="50c32-174">Kontroly stavu při použití orchestrací</span><span class="sxs-lookup"><span data-stu-id="50c32-174">Health checks when using orchestrators</span></span>

<span data-ttu-id="50c32-175">Aby bylo možné monitorovat dostupnost mikroslužeb, orchestrace, jako je Kubernetes, a Service Fabric pravidelně provádět kontroly stavu tím, že odesílají požadavky na testování mikroslužeb.</span><span class="sxs-lookup"><span data-stu-id="50c32-175">To monitor the availability of your microservices, orchestrators like Kubernetes and Service Fabric periodically perform health checks by sending requests to test the microservices.</span></span> <span data-ttu-id="50c32-176">Když nástroj Orchestrator zjistí, že služba nebo kontejner není v pořádku, zastaví požadavky na směrování do této instance.</span><span class="sxs-lookup"><span data-stu-id="50c32-176">When an orchestrator determines that a service/container is unhealthy, it stops routing requests to that instance.</span></span> <span data-ttu-id="50c32-177">Obvykle se tím vytvoří nová instance tohoto kontejneru.</span><span class="sxs-lookup"><span data-stu-id="50c32-177">It also usually creates a new instance of that container.</span></span>

<span data-ttu-id="50c32-178">Například většina orchestrací může pomocí kontrol stavu spravovat nasazení s nulovými výpadky.</span><span class="sxs-lookup"><span data-stu-id="50c32-178">For instance, most orchestrators can use health checks to manage zero-downtime deployments.</span></span> <span data-ttu-id="50c32-179">Pouze v případě, že se stav služby nebo kontejneru změní na v pořádku, bude nástroj Orchestrator zahájit směrování provozu do instancí služby/kontejneru.</span><span class="sxs-lookup"><span data-stu-id="50c32-179">Only when the status of a service/container changes to healthy will the orchestrator start routing traffic to service/container instances.</span></span>

<span data-ttu-id="50c32-180">Monitorování stavu je obzvláště důležité, když nástroj Orchestrator provede upgrade aplikace.</span><span class="sxs-lookup"><span data-stu-id="50c32-180">Health monitoring is especially important when an orchestrator performs an application upgrade.</span></span> <span data-ttu-id="50c32-181">Některé orchestrace (jako Azure Service Fabric) aktualizují služby aktualizací ve fázích, například můžou u každého upgradu aplikace aktualizovat jednu pětinu plochy clusteru.</span><span class="sxs-lookup"><span data-stu-id="50c32-181">Some orchestrators (like Azure Service Fabric) update services in phases—for example, they might update one-fifth of the cluster surface for each application upgrade.</span></span> <span data-ttu-id="50c32-182">Sada uzlů, které jsou upgradovány ve stejnou dobu, se označuje jako *upgradovací doména*.</span><span class="sxs-lookup"><span data-stu-id="50c32-182">The set of nodes that's upgraded at the same time is referred to as an *upgrade domain*.</span></span> <span data-ttu-id="50c32-183">Po upgradu každé upgradované domény a dostupnosti pro uživatele je tato upgradovací doména před přechodem na další upgradovací doménu před nasazením předána kontrolám stavu.</span><span class="sxs-lookup"><span data-stu-id="50c32-183">After each upgrade domain has been upgraded and is available to users, that upgrade domain must pass health checks before the deployment moves to the next upgrade domain.</span></span>

<span data-ttu-id="50c32-184">Dalším aspektem stavu služby je hlášení metrik ze služby.</span><span class="sxs-lookup"><span data-stu-id="50c32-184">Another aspect of service health is reporting metrics from the service.</span></span> <span data-ttu-id="50c32-185">Toto je pokročilá funkce modelu stavu některých orchestrací, jako je Service Fabric.</span><span class="sxs-lookup"><span data-stu-id="50c32-185">This is an advanced capability of the health model of some orchestrators, like Service Fabric.</span></span> <span data-ttu-id="50c32-186">Metriky jsou důležité při použití nástroje Orchestrator, protože se používají k vyrovnávání využití prostředků.</span><span class="sxs-lookup"><span data-stu-id="50c32-186">Metrics are important when using an orchestrator because they are used to balance resource usage.</span></span> <span data-ttu-id="50c32-187">Metriky také mohou být indikátorem stavu systému.</span><span class="sxs-lookup"><span data-stu-id="50c32-187">Metrics also can be an indicator of system health.</span></span> <span data-ttu-id="50c32-188">Můžete mít například aplikaci, která má mnoho mikroslužeb a každá instance hlásí metriku požadavků za sekundu (RPS).</span><span class="sxs-lookup"><span data-stu-id="50c32-188">For example, you might have an application that has many microservices, and each instance reports a requests-per-second (RPS) metric.</span></span> <span data-ttu-id="50c32-189">Pokud jedna služba používá více prostředků (paměť, procesor atd.) než jiná služba, může nástroj Orchestrator přesunout instance služby v rámci clusteru, aby se pokusila udržet ještě využití prostředků.</span><span class="sxs-lookup"><span data-stu-id="50c32-189">If one service is using more resources (memory, processor, etc.) than another service, the orchestrator could move service instances around in the cluster to try to maintain even resource utilization.</span></span>

<span data-ttu-id="50c32-190">Všimněte si, že Azure Service Fabric poskytuje svůj vlastní [model monitorování stavu](/azure/service-fabric/service-fabric-health-introduction), což je pokročilejší než jednoduché kontroly stavu.</span><span class="sxs-lookup"><span data-stu-id="50c32-190">Note that Azure Service Fabric provides its own [Health Monitoring model](/azure/service-fabric/service-fabric-health-introduction), which is more advanced than simple health checks.</span></span>

## <a name="advanced-monitoring-visualization-analysis-and-alerts"></a><span data-ttu-id="50c32-191">Rozšířené monitorování: vizualizace, analýza a výstrahy</span><span class="sxs-lookup"><span data-stu-id="50c32-191">Advanced monitoring: visualization, analysis, and alerts</span></span>

<span data-ttu-id="50c32-192">Poslední součástí monitorování je vizualizace streamu událostí, generování sestav o výkonu služby a výstraha při zjištění problému.</span><span class="sxs-lookup"><span data-stu-id="50c32-192">The final part of monitoring is visualizing the event stream, reporting on service performance, and alerting when an issue is detected.</span></span> <span data-ttu-id="50c32-193">Pro tento aspekt monitorování můžete použít různá řešení.</span><span class="sxs-lookup"><span data-stu-id="50c32-193">You can use different solutions for this aspect of monitoring.</span></span>

<span data-ttu-id="50c32-194">Můžete použít jednoduché vlastní aplikace ukazující stav vašich služeb, jako je například vlastní stránka, která je zobrazena při vysvětlení rozhraní [AspNetCore. Diagnostics. HealthChecks](https://github.com/Xabaril/AspNetCore.Diagnostics.HealthChecks).</span><span class="sxs-lookup"><span data-stu-id="50c32-194">You can use simple custom applications showing the state of your services, like the custom page shown when explaining the [AspNetCore.Diagnostics.HealthChecks](https://github.com/Xabaril/AspNetCore.Diagnostics.HealthChecks).</span></span> <span data-ttu-id="50c32-195">Nebo můžete použít pokročilejší nástroje, jako je [Azure monitor](https://azure.microsoft.com/services/monitor/) k vyvolání výstrah na základě datového proudu událostí.</span><span class="sxs-lookup"><span data-stu-id="50c32-195">Or you could use more advanced tools like [Azure Monitor](https://azure.microsoft.com/services/monitor/) to raise alerts based on the stream of events.</span></span>

<span data-ttu-id="50c32-196">Nakonec, pokud ukládáte všechny streamy událostí, můžete k vizualizaci dat použít Microsoft Power BI nebo jiná řešení, jako je Kibana nebo Splunk.</span><span class="sxs-lookup"><span data-stu-id="50c32-196">Finally, if you're storing all the event streams, you can use Microsoft Power BI or other solutions like Kibana or Splunk to visualize the data.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="50c32-197">Další materiály a zdroje informací</span><span class="sxs-lookup"><span data-stu-id="50c32-197">Additional resources</span></span>

- <span data-ttu-id="50c32-198">**Uživatelské rozhraní HealthChecks a HealthChecks pro ASP.NET Core** </span><span class="sxs-lookup"><span data-stu-id="50c32-198">**HealthChecks and HealthChecks UI for ASP.NET Core** </span></span>\
  <https://github.com/Xabaril/AspNetCore.Diagnostics.HealthChecks>

- <span data-ttu-id="50c32-199">**Úvod do Service Fabric monitoring stavu** </span><span class="sxs-lookup"><span data-stu-id="50c32-199">**Introduction to Service Fabric health monitoring** </span></span>\
  [https://docs.microsoft.com/azure/service-fabric/service-fabric-health-introduction](/azure/service-fabric/service-fabric-health-introduction)

- <span data-ttu-id="50c32-200">**Azure Monitor**</span><span class="sxs-lookup"><span data-stu-id="50c32-200">**Azure Monitor**</span></span>  
  <https://azure.microsoft.com/services/monitor/>

>[!div class="step-by-step"]
><span data-ttu-id="50c32-201">[Předchozí](implement-circuit-breaker-pattern.md)
>[Další](../secure-net-microservices-web-applications/index.md)</span><span class="sxs-lookup"><span data-stu-id="50c32-201">[Previous](implement-circuit-breaker-pattern.md)
[Next](../secure-net-microservices-web-applications/index.md)</span></span>
