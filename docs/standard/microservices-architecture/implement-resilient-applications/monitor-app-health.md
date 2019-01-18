---
title: Monitorování stavu
description: Prozkoumejte jedním ze způsobů implementace monitorování stavu.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/16/2018
ms.openlocfilehash: 666b55608ca4e5d18448e1a0b4a1735f3e856474
ms.sourcegitcommit: 542aa405b295955eb055765f33723cb8b588d0d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2019
ms.locfileid: "54362480"
---
# <a name="health-monitoring"></a><span data-ttu-id="ce525-103">Monitorování stavu</span><span class="sxs-lookup"><span data-stu-id="ce525-103">Health monitoring</span></span>

<span data-ttu-id="ce525-104">Monitorování stavu umožňuje téměř v reálném čase informace o stavu kontejnerů a mikroslužeb.</span><span class="sxs-lookup"><span data-stu-id="ce525-104">Health monitoring can allow near-real-time information about the state of your containers and microservices.</span></span> <span data-ttu-id="ce525-105">Monitorování stavu je zásadní pro několik aspektů provoz mikroslužeb a je zvlášť důležité při orchestrátorů provést upgrady částečné použití argumentů ve fázích, jak je popsáno později.</span><span class="sxs-lookup"><span data-stu-id="ce525-105">Health monitoring is critical to multiple aspects of operating microservices and is especially important when orchestrators perform partial application upgrades in phases, as explained later.</span></span>

<span data-ttu-id="ce525-106">Aplikace založená na Mikroslužbách často používají prezenční signály nebo povolit jejich sledování výkonu, plánovače a orchestrátory můžete sledovat různé služby, doplněk pro kontroly stavu.</span><span class="sxs-lookup"><span data-stu-id="ce525-106">Microservices-based applications often use heartbeats or health checks to enable their performance monitors, schedulers, and orchestrators to keep track of the multitude of services.</span></span> <span data-ttu-id="ce525-107">Pokud služby nelze odeslat nějaký druh "Jsem aktivní" signálu na vyžádání nebo podle plánu, může vaše aplikace musí rizika při nasazení aktualizací, nebo může být příliš pozdě. stačí zjišťování chyb a nebylo možné zastavit kaskádové chyby, ke kterým může ukládaly do hlavní výpadků.</span><span class="sxs-lookup"><span data-stu-id="ce525-107">If services cannot send some sort of “I’m alive” signal, either on demand or on a schedule, your application might face risks when you deploy updates, or it might just detect failures too late and not be able to stop cascading failures that can end up in major outages.</span></span>

<span data-ttu-id="ce525-108">V typické modelu služby odesílat zprávy o stavu a zobrazují se tyto informace poskytnout celkový přehled o stavu stavu aplikace.</span><span class="sxs-lookup"><span data-stu-id="ce525-108">In the typical model, services send reports about their status, and that information is aggregated to provide an overall view of the state of health of your application.</span></span> <span data-ttu-id="ce525-109">Pokud používáte orchestrator, můžete zadat informace o stavu vaší orchestrator clusteru tak, aby cluster můžete příslušně na ně reagovat.</span><span class="sxs-lookup"><span data-stu-id="ce525-109">If you're using an orchestrator, you can provide health information to your orchestrator’s cluster, so that the cluster can act accordingly.</span></span> <span data-ttu-id="ce525-110">Pokud Investujete do sestav stavu vysoce kvalitní, který je přizpůsobený pro vaši aplikaci, můžete zjistit a opravit problémy pro běžící aplikaci mnohem snadněji.</span><span class="sxs-lookup"><span data-stu-id="ce525-110">If you invest in high-quality health reporting that's customized for your application, you can detect and fix issues for your running application much more easily.</span></span>

## <a name="implement-health-checks-in-aspnet-core-services"></a><span data-ttu-id="ce525-111">Doplněk pro kontroly stavu implementace služby ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="ce525-111">Implement health checks in ASP.NET Core services</span></span>

<span data-ttu-id="ce525-112">Při vytváření mikroslužeb nebo webové aplikace ASP.NET Core, můžete použít experimentální knihovny out-of-band (ne oficiální jako součástí ASP.NETCore a jsou nyní zastaralé) s názvem *doplněk pro kontroly stavu* od týmu služby ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="ce525-112">When developing an ASP.NET Core microservice or web application, you can use an experimental out-of-band library (not official as part of ASP.NETCore and now deprecated) named *Health Checks* from the ASP.NET team.</span></span> <span data-ttu-id="ce525-113">Je k dispozici na tomto [dotnet architektury úložiště GitHub](https://github.com/dotnet-architecture/HealthChecks).</span><span class="sxs-lookup"><span data-stu-id="ce525-113">It's available at this [dotnet-architecture GitHub repository](https://github.com/dotnet-architecture/HealthChecks).</span></span> <span data-ttu-id="ce525-114">Ale oficiální verzi *doplněk pro kontroly stavu* [budou vydané v ASP.NET Core 2.2](https://github.com/aspnet/Announcements/issues/307) (by měl být oficiálním vydání do konce roku 2018).</span><span class="sxs-lookup"><span data-stu-id="ce525-114">However, the official version of *Health Checks* [will be released in ASP.NET Core 2.2](https://github.com/aspnet/Announcements/issues/307) (Should be officially released by the end of 2018).</span></span>

<span data-ttu-id="ce525-115">Tato knihovna se snadno používá a nabízí funkce, které umožňují, ověřte, že žádné konkrétní externího zdroje potřebné pro vaši aplikaci (například databáze systému SQL Server nebo vzdálené rozhraní API) správně funguje.</span><span class="sxs-lookup"><span data-stu-id="ce525-115">This library is easy to use and provides features that let you validate that any specific external resource needed for your application (like a SQL Server database or remote API) is working properly.</span></span> <span data-ttu-id="ce525-116">Při použití této knihovny, můžete také rozhodnout, co znamená to, jestli prostředek je v pořádku, protože vám vysvětlíme, později.</span><span class="sxs-lookup"><span data-stu-id="ce525-116">When you use this library, you can also decide what it means that the resource is healthy, as we explain later.</span></span>

<span data-ttu-id="ce525-117">Chcete-li použít tuto knihovnu, budete muset nejdřív použít knihovnu v mikroslužby.</span><span class="sxs-lookup"><span data-stu-id="ce525-117">In order to use this library, you need to first use the library in your microservices.</span></span> <span data-ttu-id="ce525-118">Za druhé budete potřebovat front-endové aplikace, který se dotazuje sestavy o stavu.</span><span class="sxs-lookup"><span data-stu-id="ce525-118">Second, you need a front-end application that queries for the health reports.</span></span> <span data-ttu-id="ce525-119">Který aplikace front-endu může být vlastní aplikace pro vytváření sestav, nebo to může být orchestrátor samotného, můžete odpovídajícím způsobem reagovat na stav.</span><span class="sxs-lookup"><span data-stu-id="ce525-119">That front-end application could be a custom reporting application, or it could be an orchestrator itself that can react accordingly to the health states.</span></span>

### <a name="use-the-healthchecks-library-in-your-back-end-aspnet-microservices"></a><span data-ttu-id="ce525-120">Použít knihovnu HealthChecks v back-end ASP.NET mikroslužby</span><span class="sxs-lookup"><span data-stu-id="ce525-120">Use the HealthChecks library in your back-end ASP.NET microservices</span></span>

<span data-ttu-id="ce525-121">Uvidíte jak knihovny HealthChecks slouží v aplikaci eShopOnContainers ukázkovou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="ce525-121">You can see how the HealthChecks library is used in the eShopOnContainers sample application.</span></span> <span data-ttu-id="ce525-122">Pokud chcete začít, musíte definovat, co se považuje za bezproblémového stavu u jednotlivých mikroslužeb.</span><span class="sxs-lookup"><span data-stu-id="ce525-122">To begin, you need to define what constitutes a healthy status for each microservice.</span></span> <span data-ttu-id="ce525-123">V ukázkové aplikaci mikroslužby jsou v pořádku, pokud mikroslužeb rozhraní API jsou přístupná přes protokol HTTP a pokud jeho související databáze systému SQL Server je také k dispozici.</span><span class="sxs-lookup"><span data-stu-id="ce525-123">In the sample application, the microservices are healthy if the microservice API is accessible via HTTP and if its related SQL Server database is also available.</span></span>

<span data-ttu-id="ce525-124">V budoucnu budete mít k instalaci knihovny HealthChecks jako balíček NuGet.</span><span class="sxs-lookup"><span data-stu-id="ce525-124">In the future, you'll be able to install the HealthChecks library as a NuGet package.</span></span> <span data-ttu-id="ce525-125">Ale v době psaní tohoto návodu budete muset stáhnout a kompilaci kódu jako součást vašeho řešení.</span><span class="sxs-lookup"><span data-stu-id="ce525-125">But as of this writing, you need to download and compile the code as part of your solution.</span></span> <span data-ttu-id="ce525-126">Klonování kódu, které jsou k dispozici na <https://github.com/dotnet-architecture/HealthChecks> a zkopírujte následující složky do vašeho řešení:</span><span class="sxs-lookup"><span data-stu-id="ce525-126">Clone the code available at <https://github.com/dotnet-architecture/HealthChecks> and copy the following folders to your solution:</span></span>

- <span data-ttu-id="ce525-127">src/common</span><span class="sxs-lookup"><span data-stu-id="ce525-127">src/common</span></span>
- <span data-ttu-id="ce525-128">src/Microsoft.AspNetCore.HealthChecks</span><span class="sxs-lookup"><span data-stu-id="ce525-128">src/Microsoft.AspNetCore.HealthChecks</span></span>
- <span data-ttu-id="ce525-129">src/Microsoft.Extensions.HealthChecks</span><span class="sxs-lookup"><span data-stu-id="ce525-129">src/Microsoft.Extensions.HealthChecks</span></span>
- <span data-ttu-id="ce525-130">src/Microsoft.Extensions.HealthChecks.SqlServer</span><span class="sxs-lookup"><span data-stu-id="ce525-130">src/Microsoft.Extensions.HealthChecks.SqlServer</span></span>

<span data-ttu-id="ce525-131">Můžete také použít další kontroly, jako jsou pro Azure (Microsoft.Extensions.HealthChecks.AzureStorage), ale vzhledem k tomu, že tato verze aplikaci eShopOnContainers nemá závislost na Azure, není nutné.</span><span class="sxs-lookup"><span data-stu-id="ce525-131">You could also use additional checks like the ones for Azure (Microsoft.Extensions.HealthChecks.AzureStorage), but since this version of eShopOnContainers does not have any dependency on Azure, you do not need it.</span></span> <span data-ttu-id="ce525-132">Není nutné ASP.NET kontroly stavu, protože aplikaci eShopOnContainers je založena na technologii ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="ce525-132">You do not need the ASP.NET health checks, because eShopOnContainers is based on ASP.NET Core.</span></span>

<span data-ttu-id="ce525-133">Obrázek 8-7 znázorňuje HealthChecks knihovny v sadě Visual Studio, můžete využívat jako stavební blok všechny mikroslužby.</span><span class="sxs-lookup"><span data-stu-id="ce525-133">Figure 8-7 shows the HealthChecks library in Visual Studio, ready to be used as a building block by any microservices.</span></span>

![Zobrazení Průzkumníka řešení ve složce HealthChecks zobrazující tří projektů.](./media/image6.png)

<span data-ttu-id="ce525-135">**Obrázek 8-7**.</span><span class="sxs-lookup"><span data-stu-id="ce525-135">**Figure 8-7**.</span></span> <span data-ttu-id="ce525-136">Zdrojový kód knihovny ASP.NET Core HealthChecks v řešení sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="ce525-136">ASP.NET Core HealthChecks library source code in a Visual Studio solution</span></span>

<span data-ttu-id="ce525-137">První věc, kterou provedete v každém projektu mikroslužeb zavedeném dříve, je přidejte odkaz na tři HealthChecks knihovny.</span><span class="sxs-lookup"><span data-stu-id="ce525-137">As introduced earlier, the first thing to do in each microservice project is to add a reference to the three HealthChecks libraries.</span></span> <span data-ttu-id="ce525-138">Potom přidáte stav vrácení akce, které chcete provést v tomto mikroslužeb.</span><span class="sxs-lookup"><span data-stu-id="ce525-138">After that, you add the health check actions that you want to perform in that microservice.</span></span> <span data-ttu-id="ce525-139">Tyto akce jsou v podstatě závislosti na jiných mikroslužby (HttpUrlCheck) nebo databází (aktuálně SqlCheck\* databází systému SQL Server).</span><span class="sxs-lookup"><span data-stu-id="ce525-139">These actions are basically dependencies on other microservices (HttpUrlCheck) or databases (currently SqlCheck\* for SQL Server databases).</span></span> <span data-ttu-id="ce525-140">Můžete přidat akce v rámci třídy spuštění jednotlivých mikroslužeb technologie ASP.NET nebo webové aplikace ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="ce525-140">You add the action within the Startup class of each ASP.NET microservice or ASP.NET web application.</span></span>

<span data-ttu-id="ce525-141">Každá služba nebo webové aplikace musí být nakonfigurovaný tak, že přidáte všechny její závislosti protokolu HTTP nebo databází jako jednu metodu AddHealthCheck.</span><span class="sxs-lookup"><span data-stu-id="ce525-141">Each service or web application should be configured by adding all its HTTP or database dependencies as one AddHealthCheck method.</span></span> <span data-ttu-id="ce525-142">Například webové aplikace MVC v aplikaci eShopOnContainers závisí na mnoha službách, proto má několik metod AddCheck přidán na kontroly stavu.</span><span class="sxs-lookup"><span data-stu-id="ce525-142">For example, the MVC web application from eShopOnContainers depends on many services, therefore has several AddCheck methods added to the health checks.</span></span>

<span data-ttu-id="ce525-143">V následujícím kódu (zjednodušená), uvidíte jak mikroslužeb katalogu přidá závislost na jeho databáze systému SQL Server.</span><span class="sxs-lookup"><span data-stu-id="ce525-143">For instance, in the following (simplified) code you can see how the catalog microservice adds a dependency on its SQL Server database.</span></span>

```csharp
// Startup.cs from Catalog.api microservice
//
public class Startup
{
    public void ConfigureServices(IServiceCollection services)
    {
        // Add framework services
        services.AddHealthChecks(checks =>
        {
            checks.AddSqlCheck("CatalogDb", Configuration["ConnectionString"]);
        });
        // Other services
    }
}
```

<span data-ttu-id="ce525-144">Webovou aplikaci MVC aplikaci eShopOnContainers má ale více závislostí na zbývajících mikroslužby.</span><span class="sxs-lookup"><span data-stu-id="ce525-144">However, the MVC web application of eShopOnContainers has multiple dependencies on the rest of the microservices.</span></span> <span data-ttu-id="ce525-145">Proto volání metod AddUrlCheck u jednotlivých mikroslužeb, jak je znázorněno v následujícím příkladu (zjednodušená):</span><span class="sxs-lookup"><span data-stu-id="ce525-145">Therefore, it calls one AddUrlCheck method for each microservice, as shown in the following (simplified) example:</span></span>

```csharp
// Startup.cs from the MVC web app
public class Startup
{
    public void ConfigureServices(IServiceCollection services)
    {
        services.AddMvc();
        services.Configure<AppSettings>(Configuration);
        services.AddHealthChecks(checks =>
        {
            checks.AddUrlCheck(Configuration["CatalogUrl"]);
            checks.AddUrlCheck(Configuration["OrderingUrl"]);
            checks.AddUrlCheck(Configuration["BasketUrl"]);
            checks.AddUrlCheck(Configuration["IdentityUrl"]);
        });
    }
}
```

<span data-ttu-id="ce525-146">Mikroslužby proto neposkytne "v pořádku" stav, dokud všechny jeho kontroly jsou také v pořádku.</span><span class="sxs-lookup"><span data-stu-id="ce525-146">Thus, a microservice will not provide a “healthy” status until all its checks are healthy as well.</span></span>

<span data-ttu-id="ce525-147">Pokud mikroslužbách nemá závislost na službě nebo na serveru SQL Server, měli byste přidat jenom kontrolu Healthy("Ok").</span><span class="sxs-lookup"><span data-stu-id="ce525-147">If the microservice does not have a dependency on a service or on SQL Server, you should just add a Healthy("Ok") check.</span></span> <span data-ttu-id="ce525-148">Následující kód je aplikaci eShopOnContainers `basket.api` mikroslužeb.</span><span class="sxs-lookup"><span data-stu-id="ce525-148">The following code is from the eShopOnContainers `basket.api` microservice.</span></span> <span data-ttu-id="ce525-149">(Nákupní košík mikroslužeb používá mezipaměť Redis, ale knihovny zatím nezahrnuje zprostředkovatele Redis stav kontroly.)</span><span class="sxs-lookup"><span data-stu-id="ce525-149">(The basket microservice uses the Redis cache, but the library does not yet include a Redis health check provider.)</span></span>

```csharp
services.AddHealthChecks(checks =>
{
    checks.AddValueTaskCheck("HTTP Endpoint", () => new
        ValueTask<IHealthCheckResult>(HealthCheckResult.Healthy("Ok")));
});
```

<span data-ttu-id="ce525-150">Služby nebo webové aplikace zveřejněte koncový bod kontroly stavu, je třeba povolit `UseHealthChecks([*url_for_health_checks*])` – metoda rozšíření.</span><span class="sxs-lookup"><span data-stu-id="ce525-150">For a service or web application to expose the health check endpoint, it has to enable the `UseHealthChecks([*url_for_health_checks*])` extension method.</span></span> <span data-ttu-id="ce525-151">Tato metoda přejde na `WebHostBuilder` úrovni v hlavní metodě `Program` tříd ASP.NET Core service nebo webové aplikaci hned po <xref:Microsoft.AspNetCore.WebHost.CreateDefaultBuilder> jak je znázorněno v následujícím kódu jednodušší:</span><span class="sxs-lookup"><span data-stu-id="ce525-151">This method goes at the `WebHostBuilder` level in the main method of the `Program` class of your ASP.NET Core service or web application, right after <xref:Microsoft.AspNetCore.WebHost.CreateDefaultBuilder> as shown in the following simplified code:</span></span>

```csharp
namespace Microsoft.eShopOnContainers.WebMVC
{
    public class Program
    {
        public static void Main(string[] args)
        {
            var host = WebHost.CreateDefaultBuilder(args)
                .UseHealthChecks("/hc")
                .UseContentRoot(Directory.GetCurrentDirectory())
                .UseStartup<Startup>()
                .Build();

            host.Run();
        }
    }
}
```

<span data-ttu-id="ce525-152">Tento proces funguje takto: jednotlivých mikroslužeb poskytuje HC koncový bod.</span><span class="sxs-lookup"><span data-stu-id="ce525-152">The process works this way: each microservice exposes the endpoint /hc.</span></span> <span data-ttu-id="ce525-153">Tento koncový bod se vytvořil HealthChecks knihovna middlewarových ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="ce525-153">That endpoint is created by the HealthChecks library ASP.NET Core middleware.</span></span> <span data-ttu-id="ce525-154">Při vyvolání tohoto koncového bodu, spustí všechny kontroly stavu, které jsou nakonfigurované v metodě AddHealthChecks ve třídě spuštění.</span><span class="sxs-lookup"><span data-stu-id="ce525-154">When that endpoint is invoked, it runs all the health checks that are configured in the AddHealthChecks method in the Startup class.</span></span>

<span data-ttu-id="ce525-155">Metoda UseHealthChecks očekává, že port nebo cestu.</span><span class="sxs-lookup"><span data-stu-id="ce525-155">The UseHealthChecks method expects a port or a path.</span></span> <span data-ttu-id="ce525-156">Tento port nebo cesta jsou koncový bod, který slouží ke kontrole stavu služby.</span><span class="sxs-lookup"><span data-stu-id="ce525-156">That port or path is the endpoint to use to check the health state of the service.</span></span> <span data-ttu-id="ce525-157">Například mikroslužeb katalogu používá HC cestu.</span><span class="sxs-lookup"><span data-stu-id="ce525-157">For instance, the catalog microservice uses the path /hc.</span></span>

### <a name="cache-health-check-responses"></a><span data-ttu-id="ce525-158">Odpovědi na kontrolu stavu mezipaměti</span><span class="sxs-lookup"><span data-stu-id="ce525-158">Cache health check responses</span></span>

<span data-ttu-id="ce525-159">Vzhledem k tomu, že nechcete způsobit odepření služby (DoS) ve vašich službách nebo jednoduše nechcete dopad na výkon služby tak, že zkontrolujete prostředky příliš často, můžete vrátí do mezipaměti a nakonfigurovat doba mezipaměti pro každou kontrolu stavu.</span><span class="sxs-lookup"><span data-stu-id="ce525-159">Since you do not want to cause a Denial of Service (DoS) in your services, or you simply do not want to impact service performance by checking resources too frequently, you can cache the returns and configure a cache duration for each health check.</span></span>

<span data-ttu-id="ce525-160">Ve výchozím nastavení Doba uložení do mezipaměti interně nastavena na 5 minut, ale můžete změnit této mezipaměti na každé kontrolu stavu, stejně jako v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="ce525-160">By default, the cache duration is internally set to 5 minutes, but you can change that cache duration on each health check, as in the following code:</span></span>

```csharp
checks.AddUrlCheck(Configuration["CatalogUrl"],1); // 1 min as cache duration
```

### <a name="query-your-microservices-to-report-about-their-health-status"></a><span data-ttu-id="ce525-161">Dotazování mikroslužby na zprávu o jejich stavu</span><span class="sxs-lookup"><span data-stu-id="ce525-161">Query your microservices to report about their health status</span></span>

<span data-ttu-id="ce525-162">Pokud jste nakonfigurovali kontroly stavu, jak je popsáno v tomto článku a máte mikroslužeb spuštěné v Dockeru, můžete přímo zkontrolovat z prohlížeče pokud je v pořádku.</span><span class="sxs-lookup"><span data-stu-id="ce525-162">When you've configured health checks as described in this article and you have the microservice running in Docker, you can directly check from a browser if it's healthy.</span></span>

<span data-ttu-id="ce525-163">Máte-li publikovat port kontejneru do hostitele Docker, aby měli přístup k kontejneru prostřednictvím externí IP adresa hostitele Dockeru nebo prostřednictvím `localhost`, jak je znázorněno na obrázku 8-8.</span><span class="sxs-lookup"><span data-stu-id="ce525-163">You have to publish the container port in the Docker host, so you can access the container through the external Docker host IP or through `localhost`, as shown in figure 8-8.</span></span>

![Zobrazení prohlížeče s JSON odpovědi vrácené Kontrola stavu](./media/image7.png)

<span data-ttu-id="ce525-165">**Obrázek 8 – 8**.</span><span class="sxs-lookup"><span data-stu-id="ce525-165">**Figure 8-8**.</span></span> <span data-ttu-id="ce525-166">Kontroluje se stav jedinou službou v prohlížeči</span><span class="sxs-lookup"><span data-stu-id="ce525-166">Checking health status of a single service from a browser</span></span>

<span data-ttu-id="ce525-167">V testu uvidíte, že je v pořádku, mikroslužbách catalog.api (spuštěné na portu 5101) vrací stav protokolu HTTP 200 a informace o stavu ve formátu JSON.</span><span class="sxs-lookup"><span data-stu-id="ce525-167">In that test, you can see that the catalog.api microservice (running on port 5101) is healthy, returning HTTP status 200 and status information in JSON.</span></span> <span data-ttu-id="ce525-168">To také znamená, že interně služba zkontrolovány také stav jeho závislost databáze systému SQL Server a, kontrola stavu samotné byl nahlášen jako v pořádku.</span><span class="sxs-lookup"><span data-stu-id="ce525-168">It also means that internally the service also checked the health of its SQL Server database dependency and that health check was reported itself as healthy.</span></span>

## <a name="use-watchdogs"></a><span data-ttu-id="ce525-169">Použití watchdogs</span><span class="sxs-lookup"><span data-stu-id="ce525-169">Use watchdogs</span></span>

<span data-ttu-id="ce525-170">Sledovacího zařízení je samostatná služba, která může sledovat stav a načíst pomocí dotazu s napříč službami a stavu sestavy o mikroslužbách `HealthChecks` dříve zavedené knihovny.</span><span class="sxs-lookup"><span data-stu-id="ce525-170">A watchdog is a separate service that can watch health and load across services, and report health about the microservices by querying with the `HealthChecks` library introduced earlier.</span></span> <span data-ttu-id="ce525-171">To může pomoci zabránit chybám, které nebudou zjištěny založené na zobrazení jedné služby.</span><span class="sxs-lookup"><span data-stu-id="ce525-171">This can help prevent errors that would not be detected based on the view of a single service.</span></span> <span data-ttu-id="ce525-172">Watchdogs je také vhodné místo pro hostování kódu, který může provádět nápravné akce pro známé podmínky bez zásahu uživatele.</span><span class="sxs-lookup"><span data-stu-id="ce525-172">Watchdogs also are a good place to host code that can perform remediation actions for known conditions without user interaction.</span></span>

<span data-ttu-id="ce525-173">Ukázkové aplikaci eShopOnContainers obsahuje webovou stránku, která zobrazí ukázkové sestavy stavu zaškrtnutí, jak ukazuje obrázek 8 až 9.</span><span class="sxs-lookup"><span data-stu-id="ce525-173">The eShopOnContainers sample contains a web page that displays sample health check reports, as shown in Figure 8-9.</span></span> <span data-ttu-id="ce525-174">Toto je nejjednodušší sledovacího zařízení, které by mohly mít, protože pouze zobrazuje stav mikroslužbách a webových aplikací v aplikaci eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="ce525-174">This is the simplest watchdog you could have since it only shows the state of the microservices and web applications in eShopOnContainers.</span></span> <span data-ttu-id="ce525-175">Obvykle sledovacího zařízení také provede akce při zjišťuje stavy není v pořádku.</span><span class="sxs-lookup"><span data-stu-id="ce525-175">Usually a watchdog also takes actions when it detects unhealthy states.</span></span>

![Zobrazit v prohlížeči WebStatus aplikace, která zobrazuje stav pět mikroslužeb v aplikaci eShopOnContainers](./media/image8.png)

<span data-ttu-id="ce525-177">**Obrázek 8 až 9**.</span><span class="sxs-lookup"><span data-stu-id="ce525-177">**Figure 8-9**.</span></span> <span data-ttu-id="ce525-178">Ukázková sestava kontroly stavu v aplikaci eShopOnContainers</span><span class="sxs-lookup"><span data-stu-id="ce525-178">Sample health check report in eShopOnContainers</span></span>

<span data-ttu-id="ce525-179">Stručně řečeno middleware ASP.NET knihovny ASP.NET Core HealthChecks poskytuje koncový bod jednoho stavu zaškrtnutí u jednotlivých mikroslužeb.</span><span class="sxs-lookup"><span data-stu-id="ce525-179">In summary, the ASP.NET middleware of the ASP.NET Core HealthChecks library provides a single health check endpoint for each microservice.</span></span> <span data-ttu-id="ce525-180">To spustí všechny kontroly stavu, v něm definovanou a vrátit celkového přehledu o stavu v závislosti na těchto kontrol.</span><span class="sxs-lookup"><span data-stu-id="ce525-180">This will execute all the health checks defined within it and return an overall health state depending on all those checks.</span></span>

<span data-ttu-id="ce525-181">Knihovna HealthChecks je rozšiřitelný prostřednictvím nové kontroly stavu budoucí externích prostředků.</span><span class="sxs-lookup"><span data-stu-id="ce525-181">The HealthChecks library is extensible through new health checks of future external resources.</span></span> <span data-ttu-id="ce525-182">Například Očekáváme, že v budoucnu knihovny bude mít kontroly stavu pro mezipaměť Redis a pro ostatní databáze.</span><span class="sxs-lookup"><span data-stu-id="ce525-182">For example, we expect that in the future the library will have health checks for Redis cache and for other databases.</span></span> <span data-ttu-id="ce525-183">Knihovny umožňuje zdraví, vytváření sestav ve více závislostí služby nebo aplikace, a pak můžete provádět akce založené na tyto kontroly stavu.</span><span class="sxs-lookup"><span data-stu-id="ce525-183">The library allows health reporting by multiple service or application dependencies, and you can then take actions based on those health checks.</span></span>

## <a name="health-checks-when-using-orchestrators"></a><span data-ttu-id="ce525-184">Kontroly stavu při použití orchestrátorů</span><span class="sxs-lookup"><span data-stu-id="ce525-184">Health checks when using orchestrators</span></span>

<span data-ttu-id="ce525-185">Pokud chcete monitorovat dostupnost mikroslužby, orchestrátorů, jako je Kubernetes a Service Fabric pravidelně provádět kontroly stavu pomocí zasílání požadavků na test mikroslužby.</span><span class="sxs-lookup"><span data-stu-id="ce525-185">To monitor the availability of your microservices, orchestrators like Kubernetes and Service Fabric periodically perform health checks by sending requests to test the microservices.</span></span> <span data-ttu-id="ce525-186">Když orchestrátor zjistí, že služby/kontejneru není v pořádku, že zastaví směrování požadavků do této instance.</span><span class="sxs-lookup"><span data-stu-id="ce525-186">When an orchestrator determines that a service/container is unhealthy, it stops routing requests to that instance.</span></span> <span data-ttu-id="ce525-187">Také obvykle vytvoří novou instanci kontejneru.</span><span class="sxs-lookup"><span data-stu-id="ce525-187">It also usually creates a new instance of that container.</span></span>

<span data-ttu-id="ce525-188">Většina orchestrátorů, můžete použít kontroly stavu pro správu nasazení s nulovými výpadky.</span><span class="sxs-lookup"><span data-stu-id="ce525-188">For instance, most orchestrators can use health checks to manage zero-downtime deployments.</span></span> <span data-ttu-id="ce525-189">Pouze v případě, že bude stav kontejneru služby/změny v pořádku orchestrátoru start směrování provozu do služby a container instances.</span><span class="sxs-lookup"><span data-stu-id="ce525-189">Only when the status of a service/container changes to healthy will the orchestrator start routing traffic to service/container instances.</span></span>

<span data-ttu-id="ce525-190">Monitorování stavu je obzvláště důležité, když orchestrátor provádí upgrade aplikace.</span><span class="sxs-lookup"><span data-stu-id="ce525-190">Health monitoring is especially important when an orchestrator performs an application upgrade.</span></span> <span data-ttu-id="ce525-191">Některé zvolené orchestrátory (jako je Azure Service Fabric) aktualizovat služby ve fázích – například může aktualizovat jeden pátého povrchu clusteru pro každý upgrade aplikace.</span><span class="sxs-lookup"><span data-stu-id="ce525-191">Some orchestrators (like Azure Service Fabric) update services in phases—for example, they might update one-fifth of the cluster surface for each application upgrade.</span></span> <span data-ttu-id="ce525-192">Sada uzlů, který se upgraduje ve stejnou dobu se označuje jako *upgradovací doména*.</span><span class="sxs-lookup"><span data-stu-id="ce525-192">The set of nodes that's upgraded at the same time is referred to as an *upgrade domain*.</span></span> <span data-ttu-id="ce525-193">Po každé upgradovací doména byl upgradován a je k dispozici pro uživatele, že upgradovací doména musí uplynout kontroly stavu nasazení přejde k další upgradovací doméně.</span><span class="sxs-lookup"><span data-stu-id="ce525-193">After each upgrade domain has been upgraded and is available to users, that upgrade domain must pass health checks before the deployment moves to the next upgrade domain.</span></span>

<span data-ttu-id="ce525-194">Dalším aspektem služby service health je generování sestav metrik ze služby.</span><span class="sxs-lookup"><span data-stu-id="ce525-194">Another aspect of service health is reporting metrics from the service.</span></span> <span data-ttu-id="ce525-195">Toto je rozšířená možnost modelu stavu některé zvolené orchestrátory, jako je Service Fabric.</span><span class="sxs-lookup"><span data-stu-id="ce525-195">This is an advanced capability of the health model of some orchestrators, like Service Fabric.</span></span> <span data-ttu-id="ce525-196">Metriky jsou důležité při použití orchestrator, protože se používají k vyrovnávání využití prostředků.</span><span class="sxs-lookup"><span data-stu-id="ce525-196">Metrics are important when using an orchestrator because they are used to balance resource usage.</span></span> <span data-ttu-id="ce525-197">Metriky taky může být indikátor stavu systému.</span><span class="sxs-lookup"><span data-stu-id="ce525-197">Metrics also can be an indicator of system health.</span></span> <span data-ttu-id="ce525-198">Například může mít aplikaci, která má mnoho mikroslužeb a každá instance sestav metriky požadavků za sekundu (předávajících stran).</span><span class="sxs-lookup"><span data-stu-id="ce525-198">For example, you might have an application that has many microservices, and each instance reports a requests-per-second (RPS) metric.</span></span> <span data-ttu-id="ce525-199">Pokud jedna služba používá další prostředky (paměť, procesor, atd.) než jiné službě, orchestrator může pohybovat instance služby v clusteru se pokouší spravovat i využití prostředků.</span><span class="sxs-lookup"><span data-stu-id="ce525-199">If one service is using more resources (memory, processor, etc.) than another service, the orchestrator could move service instances around in the cluster to try to maintain even resource utilization.</span></span>

<span data-ttu-id="ce525-200">Všimněte si, že Azure Service Fabric nabízí svůj vlastní [monitorování stavu modelu](/azure/service-fabric/service-fabric-health-introduction), což je složitější než kontroly stavu jednoduché.</span><span class="sxs-lookup"><span data-stu-id="ce525-200">Note that Azure Service Fabric provides its own [Health Monitoring model](/azure/service-fabric/service-fabric-health-introduction), which is more advanced than simple health checks.</span></span>

## <a name="advanced-monitoring-visualization-analysis-and-alerts"></a><span data-ttu-id="ce525-201">Rozšířené monitorování: vizualizace, analýzy a upozornění</span><span class="sxs-lookup"><span data-stu-id="ce525-201">Advanced monitoring: visualization, analysis, and alerts</span></span>

<span data-ttu-id="ce525-202">Poslední část monitorování je vizualizace datového proudu událostí, vytváření sestav o výkonu služby a upozorní při zjištění problému.</span><span class="sxs-lookup"><span data-stu-id="ce525-202">The final part of monitoring is visualizing the event stream, reporting on service performance, and alerting when an issue is detected.</span></span> <span data-ttu-id="ce525-203">Můžete použít různá řešení pro tento aspekt monitorování.</span><span class="sxs-lookup"><span data-stu-id="ce525-203">You can use different solutions for this aspect of monitoring.</span></span>

<span data-ttu-id="ce525-204">Můžete použít jednoduchý vlastní aplikace zobrazuje stav služeb, jako je vlastní stránka při s vysvětlením, [ASP.NET Core HealthChecks](https://github.com/dotnet-architecture/HealthChecks).</span><span class="sxs-lookup"><span data-stu-id="ce525-204">You can use simple custom applications showing the state of your services, like the custom page shown when explaining the [ASP.NET Core HealthChecks](https://github.com/dotnet-architecture/HealthChecks).</span></span> <span data-ttu-id="ce525-205">Nebo můžete použít rozšířené nástroje, jako je Azure Application Insights budou generovány výstrahy založené na události datového proudu.</span><span class="sxs-lookup"><span data-stu-id="ce525-205">Or you could use more advanced tools like Azure Application Insights to raise alerts based on the stream of events.</span></span>

<span data-ttu-id="ce525-206">Nakonec pokud uložená všechny streamy událostí, můžete použít Microsoft Power BI nebo jiné řešení, jako je Kibana nebo Splunk k vizualizaci dat.</span><span class="sxs-lookup"><span data-stu-id="ce525-206">Finally, if you're storing all the event streams, you can use Microsoft Power BI or other solutions like Kibana or Splunk to visualize the data.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="ce525-207">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="ce525-207">Additional resources</span></span>

- <span data-ttu-id="ce525-208">**ASP.NET Core HealthChecks** (experimentální verzi) \\</span><span class="sxs-lookup"><span data-stu-id="ce525-208">**ASP.NET Core HealthChecks** (experimental release)\\</span></span>
  [*https://github.com/dotnet-architecture/HealthChecks/*](https://github.com/dotnet-architecture/HealthChecks/)

- <span data-ttu-id="ce525-209">**Úvod do monitorování stavu Service Fabric**\\</span><span class="sxs-lookup"><span data-stu-id="ce525-209">**Introduction to Service Fabric health monitoring**\\</span></span>
  [*https://docs.microsoft.com/azure/service-fabric/service-fabric-health-introduction*](/azure/service-fabric/service-fabric-health-introduction)

- <span data-ttu-id="ce525-210">**Azure Application Insights**\\</span><span class="sxs-lookup"><span data-stu-id="ce525-210">**Azure Application Insights**\\</span></span>
  [*https://azure.microsoft.com/services/application-insights/*](https://azure.microsoft.com/services/application-insights/)

- <span data-ttu-id="ce525-211">**Microsoft Operations Management Suite**\\</span><span class="sxs-lookup"><span data-stu-id="ce525-211">**Microsoft Operations Management Suite**\\</span></span>
  [*https://www.microsoft.com/cloud-platform/operations-management-suite*](https://www.microsoft.com/cloud-platform/operations-management-suite)

>[!div class="step-by-step"]
><span data-ttu-id="ce525-212">[Předchozí](implement-circuit-breaker-pattern.md)
>[další](../secure-net-microservices-web-applications/index.md)</span><span class="sxs-lookup"><span data-stu-id="ce525-212">[Previous](implement-circuit-breaker-pattern.md)
[Next](../secure-net-microservices-web-applications/index.md)</span></span>