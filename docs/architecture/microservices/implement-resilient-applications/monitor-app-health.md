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
# <a name="health-monitoring"></a><span data-ttu-id="e6837-103">Monitorování stavu</span><span class="sxs-lookup"><span data-stu-id="e6837-103">Health monitoring</span></span>

<span data-ttu-id="e6837-104">Monitorování stavu můžete povolit téměř v reálném čase informace o stavu kontejnerů a mikroslužeb.</span><span class="sxs-lookup"><span data-stu-id="e6837-104">Health monitoring can allow near-real-time information about the state of your containers and microservices.</span></span> <span data-ttu-id="e6837-105">Monitorování stavu je důležité pro více aspektů provoznímikroslužeb a je zvláště důležité, když orchestrátory provádět částečné upgrady aplikací ve fázích, jak je vysvětleno později.</span><span class="sxs-lookup"><span data-stu-id="e6837-105">Health monitoring is critical to multiple aspects of operating microservices and is especially important when orchestrators perform partial application upgrades in phases, as explained later.</span></span>

<span data-ttu-id="e6837-106">Aplikace založené na mikroslužbách často používají prezenční signály nebo kontroly stavu k povolení jejich sledování výkonu, plánovače a orchestrátory sledovat velké množství služeb.</span><span class="sxs-lookup"><span data-stu-id="e6837-106">Microservices-based applications often use heartbeats or health checks to enable their performance monitors, schedulers, and orchestrators to keep track of the multitude of services.</span></span> <span data-ttu-id="e6837-107">Pokud služby nelze odeslat nějaký signál "Jsem naživu", a to buď na vyžádání nebo podle plánu, aplikace může čelit rizikům při nasazování aktualizací, nebo to může jen zjistit selhání příliš pozdě a není schopen zastavit kaskádové selhání, které mohou skončit v hlavních výpadků.</span><span class="sxs-lookup"><span data-stu-id="e6837-107">If services cannot send some sort of “I’m alive” signal, either on demand or on a schedule, your application might face risks when you deploy updates, or it might just detect failures too late and not be able to stop cascading failures that can end up in major outages.</span></span>

<span data-ttu-id="e6837-108">V typickém modelu služby odesílají sestavy o jejich stavu a tyto informace jsou agregovány tak, aby poskytovaly celkový přehled o stavu vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="e6837-108">In the typical model, services send reports about their status, and that information is aggregated to provide an overall view of the state of health of your application.</span></span> <span data-ttu-id="e6837-109">Pokud používáte orchestrator, můžete poskytnout informace o stavu clusteru orchestrátoru, aby cluster mohl podle toho jednat.</span><span class="sxs-lookup"><span data-stu-id="e6837-109">If you're using an orchestrator, you can provide health information to your orchestrator’s cluster, so that the cluster can act accordingly.</span></span> <span data-ttu-id="e6837-110">Pokud investujete do vysoce kvalitních sestav stavu, které jsou přizpůsobeny pro vaši aplikaci, můžete mnohem snadněji zjistit a opravit problémy pro spuštěnou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="e6837-110">If you invest in high-quality health reporting that's customized for your application, you can detect and fix issues for your running application much more easily.</span></span>

## <a name="implement-health-checks-in-aspnet-core-services"></a><span data-ttu-id="e6837-111">Implementace kontrol stavu v ASP.NET základních služeb</span><span class="sxs-lookup"><span data-stu-id="e6837-111">Implement health checks in ASP.NET Core services</span></span>

<span data-ttu-id="e6837-112">Při vývoji mikroslužby ASP.NET Core nebo webové aplikace můžete použít předdefinovanou funkci kontrolstavu, která byla vydána v prostředí ASP .NET Core 2.2 ([Microsoft.Extensions.Diagnostics.HealthChecks](https://www.nuget.org/packages/Microsoft.Extensions.Diagnostics.HealthChecks)).</span><span class="sxs-lookup"><span data-stu-id="e6837-112">When developing an ASP.NET Core microservice or web application, you can use the built-in health checks feature that was released in ASP .NET Core 2.2 ([Microsoft.Extensions.Diagnostics.HealthChecks](https://www.nuget.org/packages/Microsoft.Extensions.Diagnostics.HealthChecks)).</span></span> <span data-ttu-id="e6837-113">Stejně jako mnoho ASP.NET funkcí core, zdravotní kontroly přicházejí se sadou služeb a middleware.</span><span class="sxs-lookup"><span data-stu-id="e6837-113">Like many ASP.NET Core features, health checks come with a set of services and a middleware.</span></span>

<span data-ttu-id="e6837-114">Služby kontroly stavu a middleware jsou snadno použitelné a poskytují funkce, které umožňují ověřit, zda všechny externí prostředky potřebné pro vaši aplikaci (jako je databáze SERVERU SQL Server nebo vzdálené rozhraní API) funguje správně.</span><span class="sxs-lookup"><span data-stu-id="e6837-114">Health check services and middleware are easy to use and provide capabilities that let you validate if any external resource needed for your application (like a SQL Server database or a remote API) is working properly.</span></span> <span data-ttu-id="e6837-115">Při použití této funkce můžete také rozhodnout, co to znamená, že prostředek je v pořádku, jak vysvětlíme později.</span><span class="sxs-lookup"><span data-stu-id="e6837-115">When you use this feature, you can also decide what it means that the resource is healthy, as we explain later.</span></span>

<span data-ttu-id="e6837-116">Chcete-li tuto funkci efektivně používat, musíte nejprve nakonfigurovat služby v mikroslužbách.</span><span class="sxs-lookup"><span data-stu-id="e6837-116">To use this feature effectively, you need to first configure services in your microservices.</span></span> <span data-ttu-id="e6837-117">Za druhé potřebujete front-endovou aplikaci, která se dotazuje na sestavy stavu.</span><span class="sxs-lookup"><span data-stu-id="e6837-117">Second, you need a front-end application that queries for the health reports.</span></span> <span data-ttu-id="e6837-118">Tato front-endová aplikace může být vlastní aplikace pro vykazování nebo samotná orchestrator, která může odpovídajícím způsobem reagovat na stavy.</span><span class="sxs-lookup"><span data-stu-id="e6837-118">That front-end application could be a custom reporting application, or it could be an orchestrator itself that can react accordingly to the health states.</span></span>

### <a name="use-the-healthchecks-feature-in-your-back-end-aspnet-microservices"></a><span data-ttu-id="e6837-119">Použití funkce HealthChecks v back-endu ASP.NET mikroslužeb</span><span class="sxs-lookup"><span data-stu-id="e6837-119">Use the HealthChecks feature in your back-end ASP.NET microservices</span></span>

<span data-ttu-id="e6837-120">V této části se dozvíte, jak implementovat funkci HealthChecks v ukázkové ASP.NET aplikaci webového rozhraní API Core 3.1 při použití balíčku [Microsoft.Extensions.Diagnostics.HealthChecks.](https://www.nuget.org/packages/Microsoft.Extensions.Diagnostics.HealthChecks)</span><span class="sxs-lookup"><span data-stu-id="e6837-120">In this section, you'll learn how to implement the HealthChecks feature in a sample ASP.NET Core 3.1 Web API application when using the [Microsoft.Extensions.Diagnostics.HealthChecks](https://www.nuget.org/packages/Microsoft.Extensions.Diagnostics.HealthChecks) package.</span></span> <span data-ttu-id="e6837-121">Implementace této funkce ve velkém měřítku mikroslužeb, jako je eShopOnContainers je vysvětleno v další části.</span><span class="sxs-lookup"><span data-stu-id="e6837-121">The Implementation of this feature in a large-scale microservices like the eShopOnContainers is explained in the next section.</span></span>

<span data-ttu-id="e6837-122">Chcete-li začít, musíte definovat, co představuje stav v pořádku pro každou mikroslužbu.</span><span class="sxs-lookup"><span data-stu-id="e6837-122">To begin, you need to define what constitutes a healthy status for each microservice.</span></span> <span data-ttu-id="e6837-123">V ukázkové aplikaci definujeme, že mikroslužba je v pořádku, pokud je jeho rozhraní API přístupné přes HTTP a jeho související databáze SQL Serveru je také k dispozici.</span><span class="sxs-lookup"><span data-stu-id="e6837-123">In the sample application, we define the microservice is healthy if its API is accessible via HTTP and its related SQL Server database is also available.</span></span>

<span data-ttu-id="e6837-124">V rozhraní .NET Core 3.1 můžete pomocí integrovaných rozhraní API nakonfigurovat služby, přidat kontrolu stavu pro mikroslužbu a její závislou databázi serveru SQL Server tímto způsobem:</span><span class="sxs-lookup"><span data-stu-id="e6837-124">In .NET Core 3.1, with the built-in APIs, you can configure the services, add a Health Check for the microservice and its dependent SQL Server database in this way:</span></span>

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

<span data-ttu-id="e6837-125">V předchozím kódu `services.AddHealthChecks()` metoda konfiguruje základní kontrolu HTTP, která vrací stavový kód **200** s "V pořádku".</span><span class="sxs-lookup"><span data-stu-id="e6837-125">In the previous code, the `services.AddHealthChecks()` method configures a basic HTTP check that returns a status code **200** with “Healthy”.</span></span>  <span data-ttu-id="e6837-126">Dále `AddCheck()` metoda rozšíření konfiguruje vlastní, `SqlConnectionHealthCheck` který kontroluje stav související databáze SQL.</span><span class="sxs-lookup"><span data-stu-id="e6837-126">Further, the `AddCheck()` extension method configures a custom `SqlConnectionHealthCheck` that checks the related SQL Database’s health.</span></span>

<span data-ttu-id="e6837-127">Metoda `AddCheck()` přidá novou kontrolu stavu se zadaným `IHealthCheck`názvem a implementací typu .</span><span class="sxs-lookup"><span data-stu-id="e6837-127">The `AddCheck()` method adds a new health check with a specified name and the implementation of type `IHealthCheck`.</span></span> <span data-ttu-id="e6837-128">Pomocí metody AddCheck můžete přidat více kontrol stavu, takže mikroslužba neposkytne stav "v pořádku", dokud nebudou všechny kontroly v pořádku.</span><span class="sxs-lookup"><span data-stu-id="e6837-128">You can add multiple Health Checks using AddCheck method, so a microservice won't provide a “healthy” status until all its checks are healthy.</span></span>

<span data-ttu-id="e6837-129">`SqlConnectionHealthCheck`je vlastní třída, `IHealthCheck`která implementuje , která přebírá připojovací řetězec jako parametr konstruktoru a provede jednoduchý dotaz ke kontrole, zda je připojení k databázi SQL úspěšné.</span><span class="sxs-lookup"><span data-stu-id="e6837-129">`SqlConnectionHealthCheck` is a custom class that implements `IHealthCheck`, which takes a connection string as a constructor parameter and executes a simple query to check if the connection to the SQL database is successful.</span></span> <span data-ttu-id="e6837-130">Vrátí, `HealthCheckResult.Healthy()` pokud byl dotaz úspěšně proveden `FailureStatus` a s skutečnou výjimkou, když se nezdaří.</span><span class="sxs-lookup"><span data-stu-id="e6837-130">It returns `HealthCheckResult.Healthy()` if the query was executed successfully and a `FailureStatus` with the actual exception when it fails.</span></span>

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

<span data-ttu-id="e6837-131">Všimněte si, `Select 1` že v předchozím kódu je dotaz slouží ke kontrole stavu databáze.</span><span class="sxs-lookup"><span data-stu-id="e6837-131">Note that in the previous code, `Select 1` is the query used to check the Health of the database.</span></span> <span data-ttu-id="e6837-132">Chcete-li sledovat dostupnost mikroslužeb, orchestrátory jako Kubernetes pravidelně provádět kontroly stavu odesíláním požadavků na testování mikroslužeb.</span><span class="sxs-lookup"><span data-stu-id="e6837-132">To monitor the availability of your microservices, orchestrators like Kubernetes periodically perform health checks by sending requests to test the microservices.</span></span> <span data-ttu-id="e6837-133">Je důležité, aby vaše databázové dotazy efektivní tak, aby tyto operace jsou rychlé a nevedou k vyšší využití prostředků.</span><span class="sxs-lookup"><span data-stu-id="e6837-133">It's important to keep your database queries efficient so that these operations are quick and don’t result in a higher utilization of resources.</span></span>

<span data-ttu-id="e6837-134">Nakonec přidejte middleware, který reaguje `/hc`na cestu url :</span><span class="sxs-lookup"><span data-stu-id="e6837-134">Finally, add a middleware that responds to the url path `/hc`:</span></span>

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

<span data-ttu-id="e6837-135">Při vyvolání `<yourmicroservice>/hc` koncového bodu spustí všechny kontroly stavu, `AddHealthChecks()` které jsou nakonfigurovány v metodě ve třídě Startup a zobrazí výsledek.</span><span class="sxs-lookup"><span data-stu-id="e6837-135">When the endpoint `<yourmicroservice>/hc` is invoked, it runs all the health checks that are configured in the `AddHealthChecks()` method in the Startup class and shows the result.</span></span>

### <a name="healthchecks-implementation-in-eshoponcontainers"></a><span data-ttu-id="e6837-136">Implementace HealthChecks v eShopOnContainers</span><span class="sxs-lookup"><span data-stu-id="e6837-136">HealthChecks implementation in eShopOnContainers</span></span>

<span data-ttu-id="e6837-137">Mikroslužby v eShopOnContainers spoléhají na více služeb k provedení své úlohy.</span><span class="sxs-lookup"><span data-stu-id="e6837-137">Microservices in eShopOnContainers rely on multiple services to perform its task.</span></span> <span data-ttu-id="e6837-138">Například `Catalog.API` mikroslužba z eShopOnContainers závisí na mnoha službách, jako je azure blob storage, SQL Server a RabbitMQ.</span><span class="sxs-lookup"><span data-stu-id="e6837-138">For example, the `Catalog.API` microservice from eShopOnContainers depends on many services, such as Azure Blob Storage, SQL Server, and RabbitMQ.</span></span> <span data-ttu-id="e6837-139">Proto má několik kontrol stavu `AddCheck()` přidané pomocí metody.</span><span class="sxs-lookup"><span data-stu-id="e6837-139">Therefore, it has several health checks added using the `AddCheck()` method.</span></span> <span data-ttu-id="e6837-140">Pro každou závislou `IHealthCheck` službu by bylo nutné přidat vlastní implementaci, která definuje jeho příslušný stav.</span><span class="sxs-lookup"><span data-stu-id="e6837-140">For every dependent service, a custom `IHealthCheck` implementation that defines its respective health status would need to be added.</span></span>

<span data-ttu-id="e6837-141">Open source projekt [AspNetCore.Diagnostics.HealthChecks](https://github.com/Xabaril/AspNetCore.Diagnostics.HealthChecks) tento problém řeší poskytnutím vlastních implementací kontroly stavu pro každou z těchto podnikových služeb, které jsou postaveny na rozhraní .NET Core 3.1.</span><span class="sxs-lookup"><span data-stu-id="e6837-141">The open-source project [AspNetCore.Diagnostics.HealthChecks](https://github.com/Xabaril/AspNetCore.Diagnostics.HealthChecks) solves this problem by providing custom health check implementations for each of these enterprise services, that are built on top of .NET Core 3.1.</span></span> <span data-ttu-id="e6837-142">Každá kontrola stavu je k dispozici jako samostatný balíček NuGet, který lze snadno přidat do projektu.</span><span class="sxs-lookup"><span data-stu-id="e6837-142">Each health check is available as an individual NuGet package that can be easily added to the project.</span></span> <span data-ttu-id="e6837-143">eShopOnContainers je ve velké míře využívá ve všech svých mikroslužbách.</span><span class="sxs-lookup"><span data-stu-id="e6837-143">eShopOnContainers uses them extensively in all its microservices.</span></span>

<span data-ttu-id="e6837-144">Například v `Catalog.API` mikroslužbě byly přidány následující balíčky NuGet:</span><span class="sxs-lookup"><span data-stu-id="e6837-144">For instance, in the `Catalog.API` microservice, the following NuGet packages were added:</span></span>

![Snímek obrazovky balíčků AspNetCore.Diagnostics.HealthChecks NuGet.](./media/monitor-app-health/aspnet-core-diagnostics-health-checks.png)

<span data-ttu-id="e6837-146">**Obrázek 8-7**.</span><span class="sxs-lookup"><span data-stu-id="e6837-146">**Figure 8-7**.</span></span> <span data-ttu-id="e6837-147">Vlastní kontroly stavu implementované v rozhraní Catalog.API pomocí rozhraní AspNetCore.Diagnostics.HealthChecks</span><span class="sxs-lookup"><span data-stu-id="e6837-147">Custom Health Checks implemented in Catalog.API using AspNetCore.Diagnostics.HealthChecks</span></span>

<span data-ttu-id="e6837-148">V následujícím kódu jsou přidány implementace kontroly stavu pro každou závislou službu a potom je nakonfigurován middleware:</span><span class="sxs-lookup"><span data-stu-id="e6837-148">In the following code, the health check implementations are added for each dependent service and then the middleware is configured:</span></span>

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

<span data-ttu-id="e6837-149">Nakonec přidejte middleware HealthCheck pro poslech koncového bodu "/hc":</span><span class="sxs-lookup"><span data-stu-id="e6837-149">Finally, add the HealthCheck middleware to listen to “/hc” endpoint:</span></span>

```csharp
// HealthCheck middleware
app.UseHealthChecks("/hc", new HealthCheckOptions()
{
    Predicate = _ => true,
    ResponseWriter = UIResponseWriter.WriteHealthCheckUIResponse
});
}
```

### <a name="query-your-microservices-to-report-about-their-health-status"></a><span data-ttu-id="e6837-150">Dotaz mikroslužeb pro hlášení o jejich stavu</span><span class="sxs-lookup"><span data-stu-id="e6837-150">Query your microservices to report about their health status</span></span>

<span data-ttu-id="e6837-151">Když jste nakonfigurovali kontroly stavu, jak je popsáno v tomto článku a máte mikroslužbu spuštěnou v Dockeru, můžete přímo zkontrolovat z prohlížeče, pokud je v pořádku.</span><span class="sxs-lookup"><span data-stu-id="e6837-151">When you've configured health checks as described in this article and you have the microservice running in Docker, you can directly check from a browser if it's healthy.</span></span> <span data-ttu-id="e6837-152">Musíte publikovat port kontejneru v hostiteli Dockeru, takže můžete přistupovat ke `localhost`kontejneru prostřednictvím externí ip adresy hostitele Dockeru nebo prostřednictvím , jak je znázorněno na obrázku 8-8.</span><span class="sxs-lookup"><span data-stu-id="e6837-152">You have to publish the container port in the Docker host, so you can access the container through the external Docker host IP or through `localhost`, as shown in figure 8-8.</span></span>

![Snímek obrazovky s odpovědí JSON vrácenou kontrolou stavu.](./media/monitor-app-health/health-check-json-response.png)

<span data-ttu-id="e6837-154">**Obrázek 8-8**.</span><span class="sxs-lookup"><span data-stu-id="e6837-154">**Figure 8-8**.</span></span> <span data-ttu-id="e6837-155">Kontrola stavu jedné služby z prohlížeče</span><span class="sxs-lookup"><span data-stu-id="e6837-155">Checking health status of a single service from a browser</span></span>

<span data-ttu-id="e6837-156">V tomto testu uvidíte, `Catalog.API` že mikroslužba (spuštěná na portu 5101) je v pořádku, vrací stav HTTP 200 a informace o stavu v JSON.</span><span class="sxs-lookup"><span data-stu-id="e6837-156">In that test, you can see that the `Catalog.API` microservice (running on port 5101) is healthy, returning HTTP status 200 and status information in JSON.</span></span> <span data-ttu-id="e6837-157">Služba také zkontrolovala stav závislosti databáze serveru SQL Server a RabbitMQ, takže kontrola stavu se sama hlásila jako v pořádku.</span><span class="sxs-lookup"><span data-stu-id="e6837-157">The service also checked the health of its SQL Server database dependency and RabbitMQ, so the health check reported itself as healthy.</span></span>

## <a name="use-watchdogs"></a><span data-ttu-id="e6837-158">Použití hlídacích psů</span><span class="sxs-lookup"><span data-stu-id="e6837-158">Use watchdogs</span></span>

<span data-ttu-id="e6837-159">Watchdog je samostatná služba, která můžete sledovat stav a zatížení napříč službami `HealthChecks` a sestavy stavu o mikroslužeb dotazem s knihovnou zavedenou dříve.</span><span class="sxs-lookup"><span data-stu-id="e6837-159">A watchdog is a separate service that can watch health and load across services, and report health about the microservices by querying with the `HealthChecks` library introduced earlier.</span></span> <span data-ttu-id="e6837-160">To může pomoci zabránit chybám, které by nebyly zjištěny na základě zobrazení jedné služby.</span><span class="sxs-lookup"><span data-stu-id="e6837-160">This can help prevent errors that would not be detected based on the view of a single service.</span></span> <span data-ttu-id="e6837-161">Watchdogs jsou také vhodné místo pro hostování kódu, který může provádět nápravné akce pro známé podmínky bez interakce s uživatelem.</span><span class="sxs-lookup"><span data-stu-id="e6837-161">Watchdogs also are a good place to host code that can perform remediation actions for known conditions without user interaction.</span></span>

<span data-ttu-id="e6837-162">Ukázka eShopOnContainers obsahuje webovou stránku, která zobrazuje ukázkové zprávy o kontrole stavu, jak je znázorněno na obrázku 8-9.</span><span class="sxs-lookup"><span data-stu-id="e6837-162">The eShopOnContainers sample contains a web page that displays sample health check reports, as shown in Figure 8-9.</span></span> <span data-ttu-id="e6837-163">Toto je nejjednodušší hlídací pes, který můžete mít, protože zobrazuje pouze stav mikroslužeb a webových aplikací v eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="e6837-163">This is the simplest watchdog you could have since it only shows the state of the microservices and web applications in eShopOnContainers.</span></span> <span data-ttu-id="e6837-164">Obvykle watchdog také provede akce, když zjistí stavy není v pořádku.</span><span class="sxs-lookup"><span data-stu-id="e6837-164">Usually a watchdog also takes actions when it detects unhealthy states.</span></span>

<span data-ttu-id="e6837-165">Naštěstí [AspNetCore.Diagnostics.HealthChecks](https://github.com/Xabaril/AspNetCore.Diagnostics.HealthChecks) také poskytuje balíček [AspNetCore.HealthChecks.UI](https://www.nuget.org/packages/AspNetCore.HealthChecks.UI/) NuGet, který lze použít k zobrazení výsledků kontroly stavu z nakonfigurovaných identifikátorů URI.</span><span class="sxs-lookup"><span data-stu-id="e6837-165">Fortunately, [AspNetCore.Diagnostics.HealthChecks](https://github.com/Xabaril/AspNetCore.Diagnostics.HealthChecks) also provides [AspNetCore.HealthChecks.UI](https://www.nuget.org/packages/AspNetCore.HealthChecks.UI/) NuGet package that can be used to display the health check results from the configured URIs.</span></span>

![Screenshot of the Health Checks UI eShopOnContainers health statuses.](./media/monitor-app-health/health-check-status-ui.png)

<span data-ttu-id="e6837-167">**Obrázek 8-9**.</span><span class="sxs-lookup"><span data-stu-id="e6837-167">**Figure 8-9**.</span></span> <span data-ttu-id="e6837-168">Ukázková zpráva o kontrole stavu v eShopOnContainers</span><span class="sxs-lookup"><span data-stu-id="e6837-168">Sample health check report in eShopOnContainers</span></span>

<span data-ttu-id="e6837-169">V souhrnu tato služba watchdog dotazy každý mikroslužeb "/hc" koncový bod.</span><span class="sxs-lookup"><span data-stu-id="e6837-169">In summary, this watchdog service queries each microservice’s "/hc" endpoint.</span></span> <span data-ttu-id="e6837-170">Tím se spustí všechny kontroly stavu definované v něm a vrátí celkový stav v závislosti na všech těchto kontrol.</span><span class="sxs-lookup"><span data-stu-id="e6837-170">This will execute all the health checks defined within it and return an overall health state depending on all those checks.</span></span> <span data-ttu-id="e6837-171">HealthChecksUI je snadno spotřebovávat s několika položek konfigurace a dva řádky kódu, které je třeba přidat do Startup.cs služby hlídacího psa.</span><span class="sxs-lookup"><span data-stu-id="e6837-171">The HealthChecksUI is easy to consume with a few configuration entries and two lines of code that needs to be added into the Startup.cs of the watchdog service.</span></span>

<span data-ttu-id="e6837-172">Ukázkový konfigurační soubor pro ui kontroly stavu:</span><span class="sxs-lookup"><span data-stu-id="e6837-172">Sample configuration file for health check UI:</span></span>

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

<span data-ttu-id="e6837-173">Startup.cs soubor, který přidává HealthChecksUI:</span><span class="sxs-lookup"><span data-stu-id="e6837-173">Startup.cs file that adds HealthChecksUI:</span></span>

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

## <a name="health-checks-when-using-orchestrators"></a><span data-ttu-id="e6837-174">Zdravotní kontroly při použití orchestrátorů</span><span class="sxs-lookup"><span data-stu-id="e6837-174">Health checks when using orchestrators</span></span>

<span data-ttu-id="e6837-175">Chcete-li sledovat dostupnost mikroslužeb, orchestrátory jako Kubernetes a Service Fabric pravidelně provádět kontroly stavu odesíláním požadavků na testování mikroslužeb.</span><span class="sxs-lookup"><span data-stu-id="e6837-175">To monitor the availability of your microservices, orchestrators like Kubernetes and Service Fabric periodically perform health checks by sending requests to test the microservices.</span></span> <span data-ttu-id="e6837-176">Když orchestrator zjistí, že služba nebo kontejner není v pořádku, zastaví směrování požadavků na tuto instanci.</span><span class="sxs-lookup"><span data-stu-id="e6837-176">When an orchestrator determines that a service/container is unhealthy, it stops routing requests to that instance.</span></span> <span data-ttu-id="e6837-177">Také obvykle vytvoří novou instanci tohoto kontejneru.</span><span class="sxs-lookup"><span data-stu-id="e6837-177">It also usually creates a new instance of that container.</span></span>

<span data-ttu-id="e6837-178">Většina orchestrátorů může například používat kontroly stavu ke správě nasazení s nulovými prostoji.</span><span class="sxs-lookup"><span data-stu-id="e6837-178">For instance, most orchestrators can use health checks to manage zero-downtime deployments.</span></span> <span data-ttu-id="e6837-179">Pouze v případě, že se stav služby/kontejneru změní na v pořádku, spustí orchestrator směrování provozu do instancí služby/kontejneru.</span><span class="sxs-lookup"><span data-stu-id="e6837-179">Only when the status of a service/container changes to healthy will the orchestrator start routing traffic to service/container instances.</span></span>

<span data-ttu-id="e6837-180">Monitorování stavu je zvláště důležité, když orchestrátor provede upgrade aplikace.</span><span class="sxs-lookup"><span data-stu-id="e6837-180">Health monitoring is especially important when an orchestrator performs an application upgrade.</span></span> <span data-ttu-id="e6837-181">Některé orchestrators (jako Azure Service Fabric) aktualizovat služby ve fázích – například mohou aktualizovat jednu pětinu povrchu clusteru pro každou inovost aplikace.</span><span class="sxs-lookup"><span data-stu-id="e6837-181">Some orchestrators (like Azure Service Fabric) update services in phases—for example, they might update one-fifth of the cluster surface for each application upgrade.</span></span> <span data-ttu-id="e6837-182">Sada uzlů, která je upgradována současně se označuje jako *doména upgradu*.</span><span class="sxs-lookup"><span data-stu-id="e6837-182">The set of nodes that's upgraded at the same time is referred to as an *upgrade domain*.</span></span> <span data-ttu-id="e6837-183">Po upgradu každé domény upgradu a je k dispozici uživatelům, že upgrade domény musí projít kontroly stavu před nasazení přesune do další domény upgradu.</span><span class="sxs-lookup"><span data-stu-id="e6837-183">After each upgrade domain has been upgraded and is available to users, that upgrade domain must pass health checks before the deployment moves to the next upgrade domain.</span></span>

<span data-ttu-id="e6837-184">Dalším aspektem stavu služby je vykazování metrikze služby.</span><span class="sxs-lookup"><span data-stu-id="e6837-184">Another aspect of service health is reporting metrics from the service.</span></span> <span data-ttu-id="e6837-185">Toto je pokročilá schopnost modelu stavu některých orchestrátorů, jako je Service Fabric.</span><span class="sxs-lookup"><span data-stu-id="e6837-185">This is an advanced capability of the health model of some orchestrators, like Service Fabric.</span></span> <span data-ttu-id="e6837-186">Metriky jsou důležité při použití orchestrator, protože se používají k vyrovnání využití prostředků.</span><span class="sxs-lookup"><span data-stu-id="e6837-186">Metrics are important when using an orchestrator because they are used to balance resource usage.</span></span> <span data-ttu-id="e6837-187">Metriky mohou být také ukazatelem stavu systému.</span><span class="sxs-lookup"><span data-stu-id="e6837-187">Metrics also can be an indicator of system health.</span></span> <span data-ttu-id="e6837-188">Můžete mít například aplikaci, která má mnoho mikroslužeb a každá instance hlásí metriku požadavků za sekundu (RPS).</span><span class="sxs-lookup"><span data-stu-id="e6837-188">For example, you might have an application that has many microservices, and each instance reports a requests-per-second (RPS) metric.</span></span> <span data-ttu-id="e6837-189">Pokud jedna služba používá více prostředků (paměť, procesor atd.) než jiná služba, může orchestrator přesunout instance služby v clusteru a pokusit se zachovat i využití prostředků.</span><span class="sxs-lookup"><span data-stu-id="e6837-189">If one service is using more resources (memory, processor, etc.) than another service, the orchestrator could move service instances around in the cluster to try to maintain even resource utilization.</span></span>

<span data-ttu-id="e6837-190">Všimněte si, že Azure Service Fabric poskytuje vlastní [model monitorování stavu](/azure/service-fabric/service-fabric-health-introduction), který je pokročilejší než jednoduché kontroly stavu.</span><span class="sxs-lookup"><span data-stu-id="e6837-190">Note that Azure Service Fabric provides its own [Health Monitoring model](/azure/service-fabric/service-fabric-health-introduction), which is more advanced than simple health checks.</span></span>

## <a name="advanced-monitoring-visualization-analysis-and-alerts"></a><span data-ttu-id="e6837-191">Pokročilé monitorování: vizualizace, analýza a výstrahy</span><span class="sxs-lookup"><span data-stu-id="e6837-191">Advanced monitoring: visualization, analysis, and alerts</span></span>

<span data-ttu-id="e6837-192">Poslední část monitorování je vizualizace datového proudu událostí, hlášení o výkonu služby a upozornění při zjištění problému.</span><span class="sxs-lookup"><span data-stu-id="e6837-192">The final part of monitoring is visualizing the event stream, reporting on service performance, and alerting when an issue is detected.</span></span> <span data-ttu-id="e6837-193">Pro tento aspekt monitorování můžete použít různá řešení.</span><span class="sxs-lookup"><span data-stu-id="e6837-193">You can use different solutions for this aspect of monitoring.</span></span>

<span data-ttu-id="e6837-194">Můžete použít jednoduché vlastní aplikace zobrazující stav vašich služeb, například vlastní stránku zobrazenou při vysvětlování [aspNetCore.Diagnostics.HealthChecks](https://github.com/Xabaril/AspNetCore.Diagnostics.HealthChecks).</span><span class="sxs-lookup"><span data-stu-id="e6837-194">You can use simple custom applications showing the state of your services, like the custom page shown when explaining the [AspNetCore.Diagnostics.HealthChecks](https://github.com/Xabaril/AspNetCore.Diagnostics.HealthChecks).</span></span> <span data-ttu-id="e6837-195">Nebo můžete použít pokročilejší nástroje, jako je [Azure Monitor](https://azure.microsoft.com/services/monitor/) pro zvýšení výstrah na základě proudu událostí.</span><span class="sxs-lookup"><span data-stu-id="e6837-195">Or you could use more advanced tools like [Azure Monitor](https://azure.microsoft.com/services/monitor/) to raise alerts based on the stream of events.</span></span>

<span data-ttu-id="e6837-196">Pokud ukládáte všechny streamy událostí, můžete k vizualizaci dat použít Microsoft Power BI nebo jiná řešení, jako je Kibana nebo Splunk.</span><span class="sxs-lookup"><span data-stu-id="e6837-196">Finally, if you're storing all the event streams, you can use Microsoft Power BI or other solutions like Kibana or Splunk to visualize the data.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="e6837-197">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="e6837-197">Additional resources</span></span>

- <span data-ttu-id="e6837-198">**Stavové kontroly a kontroly stavu u ASP.NET core** </span><span class="sxs-lookup"><span data-stu-id="e6837-198">**HealthChecks and HealthChecks UI for ASP.NET Core** </span></span>\
  <https://github.com/Xabaril/AspNetCore.Diagnostics.HealthChecks>

- <span data-ttu-id="e6837-199">**Úvod do monitorování stavu service fabric** </span><span class="sxs-lookup"><span data-stu-id="e6837-199">**Introduction to Service Fabric health monitoring** </span></span>\
  [https://docs.microsoft.com/azure/service-fabric/service-fabric-health-introduction](/azure/service-fabric/service-fabric-health-introduction)

- <span data-ttu-id="e6837-200">**Azure Monitor** </span><span class="sxs-lookup"><span data-stu-id="e6837-200">**Azure Monitor** </span></span>\
  <https://azure.microsoft.com/services/monitor/>

>[!div class="step-by-step"]
><span data-ttu-id="e6837-201">[Předchozí](implement-circuit-breaker-pattern.md)
>[další](../secure-net-microservices-web-applications/index.md)</span><span class="sxs-lookup"><span data-stu-id="e6837-201">[Previous](implement-circuit-breaker-pattern.md)
[Next](../secure-net-microservices-web-applications/index.md)</span></span>
