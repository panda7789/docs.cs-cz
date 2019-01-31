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
# <a name="health-monitoring"></a><span data-ttu-id="0f76a-103">Monitorování stavu</span><span class="sxs-lookup"><span data-stu-id="0f76a-103">Health monitoring</span></span>

<span data-ttu-id="0f76a-104">Monitorování stavu umožňuje téměř v reálném čase informace o stavu kontejnerů a mikroslužeb.</span><span class="sxs-lookup"><span data-stu-id="0f76a-104">Health monitoring can allow near-real-time information about the state of your containers and microservices.</span></span> <span data-ttu-id="0f76a-105">Monitorování stavu je zásadní pro několik aspektů provoz mikroslužeb a je zvlášť důležité při orchestrátorů provést upgrady částečné použití argumentů ve fázích, jak je popsáno později.</span><span class="sxs-lookup"><span data-stu-id="0f76a-105">Health monitoring is critical to multiple aspects of operating microservices and is especially important when orchestrators perform partial application upgrades in phases, as explained later.</span></span>

<span data-ttu-id="0f76a-106">Aplikace založená na Mikroslužbách často používají prezenční signály nebo povolit jejich sledování výkonu, plánovače a orchestrátory můžete sledovat různé služby, doplněk pro kontroly stavu.</span><span class="sxs-lookup"><span data-stu-id="0f76a-106">Microservices-based applications often use heartbeats or health checks to enable their performance monitors, schedulers, and orchestrators to keep track of the multitude of services.</span></span> <span data-ttu-id="0f76a-107">Pokud služby nelze odeslat nějaký druh "Jsem aktivní" signálu na vyžádání nebo podle plánu, může vaše aplikace musí rizika při nasazení aktualizací, nebo může být příliš pozdě. stačí zjišťování chyb a nebylo možné zastavit kaskádové chyby, ke kterým může ukládaly do hlavní výpadků.</span><span class="sxs-lookup"><span data-stu-id="0f76a-107">If services cannot send some sort of “I’m alive” signal, either on demand or on a schedule, your application might face risks when you deploy updates, or it might just detect failures too late and not be able to stop cascading failures that can end up in major outages.</span></span>

<span data-ttu-id="0f76a-108">V typické modelu služby odesílat zprávy o stavu a zobrazují se tyto informace poskytnout celkový přehled o stavu stavu aplikace.</span><span class="sxs-lookup"><span data-stu-id="0f76a-108">In the typical model, services send reports about their status, and that information is aggregated to provide an overall view of the state of health of your application.</span></span> <span data-ttu-id="0f76a-109">Pokud používáte orchestrator, můžete zadat informace o stavu vaší orchestrator clusteru tak, aby cluster můžete příslušně na ně reagovat.</span><span class="sxs-lookup"><span data-stu-id="0f76a-109">If you're using an orchestrator, you can provide health information to your orchestrator’s cluster, so that the cluster can act accordingly.</span></span> <span data-ttu-id="0f76a-110">Pokud Investujete do sestav stavu vysoce kvalitní, který je přizpůsobený pro vaši aplikaci, můžete zjistit a opravit problémy pro běžící aplikaci mnohem snadněji.</span><span class="sxs-lookup"><span data-stu-id="0f76a-110">If you invest in high-quality health reporting that's customized for your application, you can detect and fix issues for your running application much more easily.</span></span>

## <a name="implement-health-checks-in-aspnet-core-services"></a><span data-ttu-id="0f76a-111">Doplněk pro kontroly stavu implementace služby ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="0f76a-111">Implement health checks in ASP.NET Core services</span></span>

<span data-ttu-id="0f76a-112">Při vytváření mikroslužeb nebo webové aplikace ASP.NET Core, můžete použít funkci kontroly integrované stavu, který byl v prostředí ASP .NET Core 2.2.</span><span class="sxs-lookup"><span data-stu-id="0f76a-112">When developing an ASP.NET Core microservice or web application, you can use the built-in health checks feature that was released in ASP .NET Core 2.2.</span></span> <span data-ttu-id="0f76a-113">ASP.NET Core funkce, stav, který kontroluje obsahuje sadu služeb a middleware položek stejně jako mnoho.</span><span class="sxs-lookup"><span data-stu-id="0f76a-113">Like many ASP.NET Core features, health checks come with a set of services and a middleware.</span></span>

<span data-ttu-id="0f76a-114">Kontrola služby Health a middleware jsou snadné použití a poskytují funkce, které umožňují, kterou můžete ověřit, jestli všechny externí zdroj, vaše aplikace (jako je databáze systému SQL Server nebo vzdálené rozhraní API) potřebuje pracuje správně.</span><span class="sxs-lookup"><span data-stu-id="0f76a-114">Health check services and middleware are easy to use and provide capabilities that let you validate if any external resource needed for your application (like a SQL Server database or a remote API) is working properly.</span></span> <span data-ttu-id="0f76a-115">Při použití této funkce můžete také rozhodnout, co znamená to, jestli prostředek je v pořádku, protože vám vysvětlíme, později.</span><span class="sxs-lookup"><span data-stu-id="0f76a-115">When you use this feature, you can also decide what it means that the resource is healthy, as we explain later.</span></span>

<span data-ttu-id="0f76a-116">Tato funkce efektivně používat, musíte nejdřív nakonfigurovat v mikroslužby.</span><span class="sxs-lookup"><span data-stu-id="0f76a-116">To use this feature effectively, you need to first configure services in your microservices.</span></span> <span data-ttu-id="0f76a-117">Za druhé budete potřebovat front-endové aplikace, který se dotazuje sestavy o stavu.</span><span class="sxs-lookup"><span data-stu-id="0f76a-117">Second, you need a front-end application that queries for the health reports.</span></span> <span data-ttu-id="0f76a-118">Který aplikace front-endu může být vlastní aplikace pro vytváření sestav, nebo to může být orchestrátor samotného, můžete odpovídajícím způsobem reagovat na stav.</span><span class="sxs-lookup"><span data-stu-id="0f76a-118">That front-end application could be a custom reporting application, or it could be an orchestrator itself that can react accordingly to the health states.</span></span>

### <a name="use-the-healthchecks-feature-in-your-back-end-aspnet-microservices"></a><span data-ttu-id="0f76a-119">Použití funkce HealthChecks v back-end ASP.NET mikroslužby</span><span class="sxs-lookup"><span data-stu-id="0f76a-119">Use the HealthChecks feature in your back-end ASP.NET microservices</span></span>

<span data-ttu-id="0f76a-120">V této části se dozvíte, jak se používá funkci HealthChecks v ukázkové aplikaci rozhraní Web API 2.2 technologie ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="0f76a-120">In this section, you will learn how the HealthChecks feature is used in a sample ASP.NET Core 2.2 Web API application.</span></span> <span data-ttu-id="0f76a-121">Implementaci této funkce ve velkém měřítku mikroslužeb, stejně jako aplikaci eShopOnContainers je vysvětleno v další části.</span><span class="sxs-lookup"><span data-stu-id="0f76a-121">Implementation of this feature in a large scale microservices like the eShopOnContainers is explained in the later section.</span></span> <span data-ttu-id="0f76a-122">Pokud chcete začít, musíte definovat, co se považuje za bezproblémového stavu u jednotlivých mikroslužeb.</span><span class="sxs-lookup"><span data-stu-id="0f76a-122">To begin, you need to define what constitutes a healthy status for each microservice.</span></span> <span data-ttu-id="0f76a-123">V ukázkové aplikaci mikroslužby jsou v pořádku, pokud rozhraní API mikroslužby je přístupná přes protokol HTTP a její související databáze systému SQL Server je také k dispozici.</span><span class="sxs-lookup"><span data-stu-id="0f76a-123">In the sample application, the microservices are healthy if the microservice API is accessible via HTTP and its related SQL Server database is also available.</span></span>

<span data-ttu-id="0f76a-124">V .NET Core 2.2 s integrovaná rozhraní API můžete nakonfigurovat služby, přidejte kontroly stavu mikroslužbách a jeho závislé databáze SQL serveru tímto způsobem:</span><span class="sxs-lookup"><span data-stu-id="0f76a-124">In .NET Core 2.2, with the built-in APIs, you can configure the services, add a Health Check for the microservice and its dependent SQL Server database in this way:</span></span>

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

<span data-ttu-id="0f76a-125">V předchozím kódu `services.AddHealthChecks()` metoda nakonfiguruje základní kontrolu protokolu HTTP, který vrátí stavový kód **200** s "V pořádku".</span><span class="sxs-lookup"><span data-stu-id="0f76a-125">In the previous code, the `services.AddHealthChecks()` method configures a basic HTTP check that returns a status code **200** with “Healthy”.</span></span>  <span data-ttu-id="0f76a-126">Další, `AddCheck()` – metoda rozšíření nakonfiguruje vlastní `SqlConnectionHealthCheck` , která zkontroluje stav související SQL Database.</span><span class="sxs-lookup"><span data-stu-id="0f76a-126">Further, the `AddCheck()` extension method configures a custom `SqlConnectionHealthCheck` that checks the related SQL Database’s health.</span></span>

<span data-ttu-id="0f76a-127">`AddCheck()` Metoda přidá nová kontrola stavu se zadaným názvem a implementaci typu `IHealthCheck`.</span><span class="sxs-lookup"><span data-stu-id="0f76a-127">The `AddCheck()` method adds a new health check with a specified name and the implementation of type `IHealthCheck`.</span></span> <span data-ttu-id="0f76a-128">Můžete přidat více doplněk pro kontroly stavu pomocí metody AddCheck, takže mikroslužbě neposkytne "v pořádku" stav, dokud se všechny jeho kontroly jsou v pořádku.</span><span class="sxs-lookup"><span data-stu-id="0f76a-128">You can add multiple Health Checks using AddCheck method, so a microservice won't provide a “healthy” status until all its checks are healthy.</span></span>

<span data-ttu-id="0f76a-129">`SqlConnectionHealthCheck` je vlastní třídu, která implementuje `IHealthCheck`, který přebírá jako parametr konstruktoru připojovací řetězec a provede jednoduchý dotaz ke kontrole, pokud se úspěšně připojíte ke službě SQL database.</span><span class="sxs-lookup"><span data-stu-id="0f76a-129">`SqlConnectionHealthCheck` is a custom class that implements `IHealthCheck`, which takes a connection string as a constructor parameter and executes a simple query to check if the connection to the SQL database is successful.</span></span> <span data-ttu-id="0f76a-130">Vrátí `HealthCheckResult.Healthy()` Pokud byl dotaz proveden úspěšně a `FailureStatus` skutečné výjimku, pokud se nezdaří.</span><span class="sxs-lookup"><span data-stu-id="0f76a-130">It returns `HealthCheckResult.Healthy()` if the query was executed successfully and a `FailureStatus` with the actual exception when it fails.</span></span>

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

<span data-ttu-id="0f76a-131">Všimněte si, že v předchozím kódu `Select 1` je query sloužící ke kontrole stavu databáze.</span><span class="sxs-lookup"><span data-stu-id="0f76a-131">Note that in the previous code, `Select 1` is the query used to check the Health of the database.</span></span> <span data-ttu-id="0f76a-132">Pokud chcete monitorovat dostupnost mikroslužby, orchestrátorů, jako je Kubernetes a Service Fabric pravidelně provádět kontroly stavu pomocí zasílání požadavků na test mikroslužby.</span><span class="sxs-lookup"><span data-stu-id="0f76a-132">To monitor the availability of your microservices, orchestrators like Kubernetes and Service Fabric periodically perform health checks by sending requests to test the microservices.</span></span> <span data-ttu-id="0f76a-133">Je důležité udržovat efektivní dotazy na databázi tak, aby tyto operace jsou rychlé a nemusíte mít za následek vyšší využití prostředků.</span><span class="sxs-lookup"><span data-stu-id="0f76a-133">It's important to keep your database queries efficient so that these operations are quick and don’t result in a higher utilization of resources.</span></span>

<span data-ttu-id="0f76a-134">Nakonec vytvořte middlewaru, který reaguje na cesty url "HC":</span><span class="sxs-lookup"><span data-stu-id="0f76a-134">Finally, create a middleware that responds to the url path “/hc”:</span></span>

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

<span data-ttu-id="0f76a-135">Když koncový bod `<yourmicroservice>/hc` je vyvolána, spuštění všech kontrol stavu, které jsou nakonfigurované v `AddHealthChecks()` metody ve třídě spuštění a zobrazí výsledek.</span><span class="sxs-lookup"><span data-stu-id="0f76a-135">When the endpoint `<yourmicroservice>/hc` is invoked, it runs all the health checks that are configured in the `AddHealthChecks()` method in the Startup class and shows the result.</span></span>

### <a name="healthchecks-implementation-in-eshoponcontainers"></a><span data-ttu-id="0f76a-136">Implementace HealthChecks v aplikaci eShopOnContainers</span><span class="sxs-lookup"><span data-stu-id="0f76a-136">HealthChecks implementation in eShopOnContainers</span></span>

<span data-ttu-id="0f76a-137">Mikroslužby v aplikaci eShopOnContainers využívají více služeb k provádění svých úloh.</span><span class="sxs-lookup"><span data-stu-id="0f76a-137">Microservices in eShopOnContainers rely on multiple services to perform its task.</span></span> <span data-ttu-id="0f76a-138">Například `Catalog.API` mikroslužeb v aplikaci eShopOnContainers závisí na mnoha službách, jako je Azure Blob Storage, SQL Server a RabbitMQ.</span><span class="sxs-lookup"><span data-stu-id="0f76a-138">For example, the `Catalog.API` microservice from eShopOnContainers depends on many services, such as Azure Blob Storage, SQL Server, and RabbitMQ.</span></span> <span data-ttu-id="0f76a-139">Proto má několik kontroly stavu, které jsou přidány pomocí `AddCheck()` metody.</span><span class="sxs-lookup"><span data-stu-id="0f76a-139">Therefore, it has several health checks added using the `AddCheck()` method.</span></span> <span data-ttu-id="0f76a-140">Pro každé závislé službě vlastní `IHealthCheck` implementace, která definuje jeho příslušný stav musí být přidán.</span><span class="sxs-lookup"><span data-stu-id="0f76a-140">For every dependent service, a custom `IHealthCheck` implementation that defines its respective health status needs to be added.</span></span>

<span data-ttu-id="0f76a-141">Open source projektu [AspNetCore.Diagnostics.HealthChecks](https://github.com/Xabaril/AspNetCore.Diagnostics.HealthChecks) tento problém řeší tím, že poskytuje implementace vlastních stavových kontroly pro každou z těchto služeb enterprise, které jsou postavené na .NET Core 2.2.</span><span class="sxs-lookup"><span data-stu-id="0f76a-141">The open-source project [AspNetCore.Diagnostics.HealthChecks](https://github.com/Xabaril/AspNetCore.Diagnostics.HealthChecks) solves this problem by providing custom health check implementations for each of these enterprise services that are built on top of .NET Core 2.2.</span></span> <span data-ttu-id="0f76a-142">Každý kontroly stavu jsou dostupné jako nějakém balíčku NuGet, který lze snadno přidat do projektu.</span><span class="sxs-lookup"><span data-stu-id="0f76a-142">Each health check is available as an individual NuGet package that can be easily added to the project.</span></span> <span data-ttu-id="0f76a-143">aplikaci eShopOnContainers jejich použití často v jeho mikroslužeb.</span><span class="sxs-lookup"><span data-stu-id="0f76a-143">eShopOnContainers use them extensively in all its microservices.</span></span>

<span data-ttu-id="0f76a-144">Například v `Catalog.API` mikroslužeb, následující byly přidány balíčky NuGet:</span><span class="sxs-lookup"><span data-stu-id="0f76a-144">For instance, in the `Catalog.API` microservice, the following NuGet packages were added:</span></span>

![Zobrazení Průzkumníka řešení, ve kterém jsou balíčky AspNetCore.Diagnostics.HealthChecks NuGet odkazovaného projektu Catalog.API](./media/image6.png)

<span data-ttu-id="0f76a-146">**Obrázek 8-7**.</span><span class="sxs-lookup"><span data-stu-id="0f76a-146">**Figure 8-7**.</span></span> <span data-ttu-id="0f76a-147">Implementováno v Catalog.API pomocí AspNetCore.Diagnostics.HealthChecks vlastní kontroly stavu</span><span class="sxs-lookup"><span data-stu-id="0f76a-147">Custom Health Checks implemented in Catalog.API using AspNetCore.Diagnostics.HealthChecks</span></span>

<span data-ttu-id="0f76a-148">V následujícím kódu implementace kontroly stavu jsou přidány pro každé závislé služby a pak je middleware nakonfigurovat:</span><span class="sxs-lookup"><span data-stu-id="0f76a-148">In the following code, the health check implementations are added for each dependent service and then the middleware is configured:</span></span>

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

<span data-ttu-id="0f76a-149">Nakonec přidáme middleware HealthCheck tak, aby naslouchala na koncový bod "HC":</span><span class="sxs-lookup"><span data-stu-id="0f76a-149">Finally, we add the HealthCheck middleware to listen to “/hc” endpoint:</span></span>

```csharp
// HealthCheck middleware
app.UseHealthChecks("/hc", new HealthCheckOptions()
{
    Predicate = _ => true,
    ResponseWriter = UIResponseWriter.WriteHealthCheckUIResponse
});
}
```

### <a name="query-your-microservices-to-report-about-their-health-status"></a><span data-ttu-id="0f76a-150">Dotazování mikroslužby na zprávu o jejich stavu</span><span class="sxs-lookup"><span data-stu-id="0f76a-150">Query your microservices to report about their health status</span></span>

<span data-ttu-id="0f76a-151">Pokud jste nakonfigurovali kontroly stavu, jak je popsáno v tomto článku a máte mikroslužeb spuštěné v Dockeru, můžete přímo zkontrolovat z prohlížeče pokud je v pořádku.</span><span class="sxs-lookup"><span data-stu-id="0f76a-151">When you've configured health checks as described in this article and you have the microservice running in Docker, you can directly check from a browser if it's healthy.</span></span> <span data-ttu-id="0f76a-152">Máte-li publikovat port kontejneru do hostitele Docker, aby měli přístup k kontejneru prostřednictvím externí IP adresa hostitele Dockeru nebo prostřednictvím `localhost`, jak je znázorněno na obrázku 8-8.</span><span class="sxs-lookup"><span data-stu-id="0f76a-152">You have to publish the container port in the Docker host, so you can access the container through the external Docker host IP or through `localhost`, as shown in figure 8-8.</span></span>

![Zobrazení prohlížeče s JSON odpovědi vrácené Kontrola stavu](./media/image7.png)

<span data-ttu-id="0f76a-154">**Obrázek 8 – 8**.</span><span class="sxs-lookup"><span data-stu-id="0f76a-154">**Figure 8-8**.</span></span> <span data-ttu-id="0f76a-155">Kontroluje se stav jedinou službou v prohlížeči</span><span class="sxs-lookup"><span data-stu-id="0f76a-155">Checking health status of a single service from a browser</span></span>

<span data-ttu-id="0f76a-156">V testu, vidíte, že `Catalog.API` mikroslužeb (spuštěné na portu 5101) je v pořádku, vrací stav protokolu HTTP 200 a informace o stavu ve formátu JSON.</span><span class="sxs-lookup"><span data-stu-id="0f76a-156">In that test, you can see that the `Catalog.API` microservice (running on port 5101) is healthy, returning HTTP status 200 and status information in JSON.</span></span> <span data-ttu-id="0f76a-157">Službu také kontroluje stav jeho závislostí databáze systému SQL Server a RabbitMQ, tak Kontrola stavu se samo jako v pořádku.</span><span class="sxs-lookup"><span data-stu-id="0f76a-157">The service also checked the health of its SQL Server database dependency and RabbitMQ, so the health check reported itself as healthy.</span></span>

## <a name="use-watchdogs"></a><span data-ttu-id="0f76a-158">Použití watchdogs</span><span class="sxs-lookup"><span data-stu-id="0f76a-158">Use watchdogs</span></span>

<span data-ttu-id="0f76a-159">Sledovacího zařízení je samostatná služba, která může sledovat stav a načíst pomocí dotazu s napříč službami a stavu sestavy o mikroslužbách `HealthChecks` dříve zavedené knihovny.</span><span class="sxs-lookup"><span data-stu-id="0f76a-159">A watchdog is a separate service that can watch health and load across services, and report health about the microservices by querying with the `HealthChecks` library introduced earlier.</span></span> <span data-ttu-id="0f76a-160">To může pomoci zabránit chybám, které nebudou zjištěny založené na zobrazení jedné služby.</span><span class="sxs-lookup"><span data-stu-id="0f76a-160">This can help prevent errors that would not be detected based on the view of a single service.</span></span> <span data-ttu-id="0f76a-161">Watchdogs je také vhodné místo pro hostování kódu, který může provádět nápravné akce pro známé podmínky bez zásahu uživatele.</span><span class="sxs-lookup"><span data-stu-id="0f76a-161">Watchdogs also are a good place to host code that can perform remediation actions for known conditions without user interaction.</span></span>

<span data-ttu-id="0f76a-162">Ukázkové aplikaci eShopOnContainers obsahuje webovou stránku, která zobrazí ukázkové sestavy stavu zaškrtnutí, jak ukazuje obrázek 8 až 9.</span><span class="sxs-lookup"><span data-stu-id="0f76a-162">The eShopOnContainers sample contains a web page that displays sample health check reports, as shown in Figure 8-9.</span></span> <span data-ttu-id="0f76a-163">Toto je nejjednodušší sledovacího zařízení, které by mohly mít, protože pouze zobrazuje stav mikroslužbách a webových aplikací v aplikaci eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="0f76a-163">This is the simplest watchdog you could have since it only shows the state of the microservices and web applications in eShopOnContainers.</span></span> <span data-ttu-id="0f76a-164">Obvykle sledovacího zařízení také provede akce při zjišťuje stavy není v pořádku.</span><span class="sxs-lookup"><span data-stu-id="0f76a-164">Usually a watchdog also takes actions when it detects unhealthy states.</span></span>

<span data-ttu-id="0f76a-165">Naštěstí [AspNetCore.Diagnostics.HealthChecks](https://github.com/Xabaril/AspNetCore.Diagnostics.HealthChecks) také poskytuje [AspNetCore.HealthChecks.UI](https://www.nuget.org/packages/AspNetCore.HealthChecks.UI/) balíčku NuGet, který slouží k zobrazení stavu zaškrtnutí vyplývá z nakonfigurovaných identifikátorů URI.</span><span class="sxs-lookup"><span data-stu-id="0f76a-165">Fortunately, [AspNetCore.Diagnostics.HealthChecks](https://github.com/Xabaril/AspNetCore.Diagnostics.HealthChecks) also provides [AspNetCore.HealthChecks.UI](https://www.nuget.org/packages/AspNetCore.HealthChecks.UI/) NuGet package that can be used to display the health check results from the configured URIs.</span></span>

![Zobrazit v prohlížeči WebStatus aplikace, která zobrazuje stav všechny mikroslužby v aplikaci eShopOnContainers](./media/image8.png)

<span data-ttu-id="0f76a-167">**Obrázek 8 až 9**.</span><span class="sxs-lookup"><span data-stu-id="0f76a-167">**Figure 8-9**.</span></span> <span data-ttu-id="0f76a-168">Ukázková sestava kontroly stavu v aplikaci eShopOnContainers</span><span class="sxs-lookup"><span data-stu-id="0f76a-168">Sample health check report in eShopOnContainers</span></span>

<span data-ttu-id="0f76a-169">Stručně řečeno tato služba sledovacích dotazuje koncového bodu "HC" jednotlivých mikroslužeb.</span><span class="sxs-lookup"><span data-stu-id="0f76a-169">In summary, this watchdog service queries each microservice’s "/hc" endpoint.</span></span> <span data-ttu-id="0f76a-170">To spustí všechny kontroly stavu, v něm definovanou a vrátit celkového přehledu o stavu v závislosti na těchto kontrol.</span><span class="sxs-lookup"><span data-stu-id="0f76a-170">This will execute all the health checks defined within it and return an overall health state depending on all those checks.</span></span> <span data-ttu-id="0f76a-171">HealthChecksUI je jednoduše využít několik položek konfigurace a dva řádky kódu, který musí být přidán do souboru Startup.cs sady sledovacího zařízení služby.</span><span class="sxs-lookup"><span data-stu-id="0f76a-171">The HealthChecksUI is easy to consume with a few configuration entries and two lines of code that needs to be added into the Startup.cs of the watchdog service.</span></span>

<span data-ttu-id="0f76a-172">Ukázkový konfigurační soubor pro stav zkontrolujte uživatelského rozhraní:</span><span class="sxs-lookup"><span data-stu-id="0f76a-172">Sample configuration file for health check UI:</span></span>

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

<span data-ttu-id="0f76a-173">Startup.cs souboru, který přidá HealthChecksUI:</span><span class="sxs-lookup"><span data-stu-id="0f76a-173">Startup.cs file that adds HealthChecksUI:</span></span>

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

## <a name="health-checks-when-using-orchestrators"></a><span data-ttu-id="0f76a-174">Kontroly stavu při použití orchestrátorů</span><span class="sxs-lookup"><span data-stu-id="0f76a-174">Health checks when using orchestrators</span></span>

<span data-ttu-id="0f76a-175">Pokud chcete monitorovat dostupnost mikroslužby, orchestrátorů, jako je Kubernetes a Service Fabric pravidelně provádět kontroly stavu pomocí zasílání požadavků na test mikroslužby.</span><span class="sxs-lookup"><span data-stu-id="0f76a-175">To monitor the availability of your microservices, orchestrators like Kubernetes and Service Fabric periodically perform health checks by sending requests to test the microservices.</span></span> <span data-ttu-id="0f76a-176">Když orchestrátor zjistí, že služby/kontejneru není v pořádku, že zastaví směrování požadavků do této instance.</span><span class="sxs-lookup"><span data-stu-id="0f76a-176">When an orchestrator determines that a service/container is unhealthy, it stops routing requests to that instance.</span></span> <span data-ttu-id="0f76a-177">Také obvykle vytvoří novou instanci kontejneru.</span><span class="sxs-lookup"><span data-stu-id="0f76a-177">It also usually creates a new instance of that container.</span></span>

<span data-ttu-id="0f76a-178">Většina orchestrátorů, můžete použít kontroly stavu pro správu nasazení s nulovými výpadky.</span><span class="sxs-lookup"><span data-stu-id="0f76a-178">For instance, most orchestrators can use health checks to manage zero-downtime deployments.</span></span> <span data-ttu-id="0f76a-179">Pouze v případě, že bude stav kontejneru služby/změny v pořádku orchestrátoru start směrování provozu do služby a container instances.</span><span class="sxs-lookup"><span data-stu-id="0f76a-179">Only when the status of a service/container changes to healthy will the orchestrator start routing traffic to service/container instances.</span></span>

<span data-ttu-id="0f76a-180">Monitorování stavu je obzvláště důležité, když orchestrátor provádí upgrade aplikace.</span><span class="sxs-lookup"><span data-stu-id="0f76a-180">Health monitoring is especially important when an orchestrator performs an application upgrade.</span></span> <span data-ttu-id="0f76a-181">Některé zvolené orchestrátory (jako je Azure Service Fabric) aktualizovat služby ve fázích – například může aktualizovat jeden pátého povrchu clusteru pro každý upgrade aplikace.</span><span class="sxs-lookup"><span data-stu-id="0f76a-181">Some orchestrators (like Azure Service Fabric) update services in phases—for example, they might update one-fifth of the cluster surface for each application upgrade.</span></span> <span data-ttu-id="0f76a-182">Sada uzlů, který se upgraduje ve stejnou dobu se označuje jako *upgradovací doména*.</span><span class="sxs-lookup"><span data-stu-id="0f76a-182">The set of nodes that's upgraded at the same time is referred to as an *upgrade domain*.</span></span> <span data-ttu-id="0f76a-183">Po každé upgradovací doména byl upgradován a je k dispozici pro uživatele, že upgradovací doména musí uplynout kontroly stavu nasazení přejde k další upgradovací doméně.</span><span class="sxs-lookup"><span data-stu-id="0f76a-183">After each upgrade domain has been upgraded and is available to users, that upgrade domain must pass health checks before the deployment moves to the next upgrade domain.</span></span>

<span data-ttu-id="0f76a-184">Dalším aspektem služby service health je generování sestav metrik ze služby.</span><span class="sxs-lookup"><span data-stu-id="0f76a-184">Another aspect of service health is reporting metrics from the service.</span></span> <span data-ttu-id="0f76a-185">Toto je rozšířená možnost modelu stavu některé zvolené orchestrátory, jako je Service Fabric.</span><span class="sxs-lookup"><span data-stu-id="0f76a-185">This is an advanced capability of the health model of some orchestrators, like Service Fabric.</span></span> <span data-ttu-id="0f76a-186">Metriky jsou důležité při použití orchestrator, protože se používají k vyrovnávání využití prostředků.</span><span class="sxs-lookup"><span data-stu-id="0f76a-186">Metrics are important when using an orchestrator because they are used to balance resource usage.</span></span> <span data-ttu-id="0f76a-187">Metriky taky může být indikátor stavu systému.</span><span class="sxs-lookup"><span data-stu-id="0f76a-187">Metrics also can be an indicator of system health.</span></span> <span data-ttu-id="0f76a-188">Například může mít aplikaci, která má mnoho mikroslužeb a každá instance sestav metriky požadavků za sekundu (předávajících stran).</span><span class="sxs-lookup"><span data-stu-id="0f76a-188">For example, you might have an application that has many microservices, and each instance reports a requests-per-second (RPS) metric.</span></span> <span data-ttu-id="0f76a-189">Pokud jedna služba používá další prostředky (paměť, procesor, atd.) než jiné službě, orchestrator může pohybovat instance služby v clusteru se pokouší spravovat i využití prostředků.</span><span class="sxs-lookup"><span data-stu-id="0f76a-189">If one service is using more resources (memory, processor, etc.) than another service, the orchestrator could move service instances around in the cluster to try to maintain even resource utilization.</span></span>

<span data-ttu-id="0f76a-190">Všimněte si, že Azure Service Fabric nabízí svůj vlastní [monitorování stavu modelu](/azure/service-fabric/service-fabric-health-introduction), což je složitější než kontroly stavu jednoduché.</span><span class="sxs-lookup"><span data-stu-id="0f76a-190">Note that Azure Service Fabric provides its own [Health Monitoring model](/azure/service-fabric/service-fabric-health-introduction), which is more advanced than simple health checks.</span></span>

## <a name="advanced-monitoring-visualization-analysis-and-alerts"></a><span data-ttu-id="0f76a-191">Rozšířené monitorování: vizualizace, analýzy a upozornění</span><span class="sxs-lookup"><span data-stu-id="0f76a-191">Advanced monitoring: visualization, analysis, and alerts</span></span>

<span data-ttu-id="0f76a-192">Poslední část monitorování je vizualizace datového proudu událostí, vytváření sestav o výkonu služby a upozorní při zjištění problému.</span><span class="sxs-lookup"><span data-stu-id="0f76a-192">The final part of monitoring is visualizing the event stream, reporting on service performance, and alerting when an issue is detected.</span></span> <span data-ttu-id="0f76a-193">Můžete použít různá řešení pro tento aspekt monitorování.</span><span class="sxs-lookup"><span data-stu-id="0f76a-193">You can use different solutions for this aspect of monitoring.</span></span>

<span data-ttu-id="0f76a-194">Můžete použít jednoduchý vlastní aplikace zobrazuje stav služeb, jako je vlastní stránka při s vysvětlením, [AspNetCore.Diagnostics.HealthChecks](https://github.com/Xabaril/AspNetCore.Diagnostics.HealthChecks).</span><span class="sxs-lookup"><span data-stu-id="0f76a-194">You can use simple custom applications showing the state of your services, like the custom page shown when explaining the [AspNetCore.Diagnostics.HealthChecks](https://github.com/Xabaril/AspNetCore.Diagnostics.HealthChecks).</span></span> <span data-ttu-id="0f76a-195">Nebo můžete použít rozšířené nástroje, jako je Azure Application Insights budou generovány výstrahy založené na události datového proudu.</span><span class="sxs-lookup"><span data-stu-id="0f76a-195">Or you could use more advanced tools like Azure Application Insights to raise alerts based on the stream of events.</span></span>

<span data-ttu-id="0f76a-196">Nakonec pokud uložená všechny streamy událostí, můžete použít Microsoft Power BI nebo jiné řešení, jako je Kibana nebo Splunk k vizualizaci dat.</span><span class="sxs-lookup"><span data-stu-id="0f76a-196">Finally, if you're storing all the event streams, you can use Microsoft Power BI or other solutions like Kibana or Splunk to visualize the data.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="0f76a-197">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="0f76a-197">Additional resources</span></span>

-   <span data-ttu-id="0f76a-198">**HealthChecks a HealthChecks uživatelského rozhraní pro ASP.NET Core**
    [*https://github.com/Xabaril/AspNetCore.Diagnostics.HealthChecks*](https://github.com/Xabaril/AspNetCore.Diagnostics.HealthChecks )</span><span class="sxs-lookup"><span data-stu-id="0f76a-198">**HealthChecks and HealthChecks UI for ASP.NET Core**
[*https://github.com/Xabaril/AspNetCore.Diagnostics.HealthChecks*](https://github.com/Xabaril/AspNetCore.Diagnostics.HealthChecks )</span></span>

-   <span data-ttu-id="0f76a-199">**Úvod do monitorování stavu Service Fabric**
    [*https://docs.microsoft.com/azure/service-fabric/service-fabric-health-introduction*](/azure/service-fabric/service-fabric-health-introduction)</span><span class="sxs-lookup"><span data-stu-id="0f76a-199">**Introduction to Service Fabric health monitoring**
[*https://docs.microsoft.com/azure/service-fabric/service-fabric-health-introduction*](/azure/service-fabric/service-fabric-health-introduction)</span></span>

-   <span data-ttu-id="0f76a-200">**Azure Application Insights**
    [*https://azure.microsoft.com/services/application-insights/*](https://azure.microsoft.com/services/application-insights/)</span><span class="sxs-lookup"><span data-stu-id="0f76a-200">**Azure Application Insights**
[*https://azure.microsoft.com/services/application-insights/*](https://azure.microsoft.com/services/application-insights/)</span></span>

-   <span data-ttu-id="0f76a-201">**Microsoft Operations Management Suite**
    [*https://www.microsoft.com/en-us/cloud-platform/operations-management-suite*](https://www.microsoft.com/en-us/cloud-platform/operations-management-suite)</span><span class="sxs-lookup"><span data-stu-id="0f76a-201">**Microsoft Operations Management Suite**
[*https://www.microsoft.com/en-us/cloud-platform/operations-management-suite*](https://www.microsoft.com/en-us/cloud-platform/operations-management-suite)</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="0f76a-202">[Předchozí](implement-circuit-breaker-pattern.md)
>[další](../secure-net-microservices-web-applications/index.md)</span><span class="sxs-lookup"><span data-stu-id="0f76a-202">[Previous](implement-circuit-breaker-pattern.md)
[Next](../secure-net-microservices-web-applications/index.md)</span></span>