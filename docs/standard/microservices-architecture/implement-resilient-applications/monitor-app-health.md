---
title: Monitorování stavu
description: Architektura Mikroslužeb .NET pro Kontejnerizované aplikace .NET | Monitorování stavu
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 12/11/2017
ms.openlocfilehash: 35f6d773d714878f56a5e9151320072ebcd51e06
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53145972"
---
# <a name="health-monitoring"></a><span data-ttu-id="1f767-103">Monitorování stavu</span><span class="sxs-lookup"><span data-stu-id="1f767-103">Health monitoring</span></span>

<span data-ttu-id="1f767-104">Monitorování stavu umožňuje téměř v reálném čase informace o stavu kontejnerů a mikroslužeb.</span><span class="sxs-lookup"><span data-stu-id="1f767-104">Health monitoring can allow near-real-time information about the state of your containers and microservices.</span></span> <span data-ttu-id="1f767-105">Monitorování stavu je zásadní pro několik aspektů provoz mikroslužeb a je zvlášť důležité při orchestrátorů provést upgrady částečné použití argumentů ve fázích, jak je popsáno později.</span><span class="sxs-lookup"><span data-stu-id="1f767-105">Health monitoring is critical to multiple aspects of operating microservices and is especially important when orchestrators perform partial application upgrades in phases, as explained later.</span></span>

<span data-ttu-id="1f767-106">Aplikace založená na Mikroslužbách často používají prezenční signály nebo povolit jejich sledování výkonu, plánovače a orchestrátory můžete sledovat různé služby, doplněk pro kontroly stavu.</span><span class="sxs-lookup"><span data-stu-id="1f767-106">Microservices-based applications often use heartbeats or health checks to enable their performance monitors, schedulers, and orchestrators to keep track of the multitude of services.</span></span> <span data-ttu-id="1f767-107">Pokud služby nelze odeslat nějaký druh "Jsem aktivní" signálu na vyžádání nebo podle plánu, může vaše aplikace musí rizika při nasazení aktualizací, nebo může být příliš pozdě. stačí zjišťování chyb a nebylo možné zastavit kaskádové chyby, ke kterým může ukládaly do hlavní výpadků.</span><span class="sxs-lookup"><span data-stu-id="1f767-107">If services cannot send some sort of “I’m alive” signal, either on demand or on a schedule, your application might face risks when you deploy updates, or it might simply detect failures too late and not be able to stop cascading failures that can end up in major outages.</span></span>

<span data-ttu-id="1f767-108">V typické modelu služby odesílat zprávy o stavu a zobrazují se tyto informace poskytnout celkový přehled o stavu stavu aplikace.</span><span class="sxs-lookup"><span data-stu-id="1f767-108">In the typical model, services send reports about their status, and that information is aggregated to provide an overall view of the state of health of your application.</span></span> <span data-ttu-id="1f767-109">Pokud používáte orchestrator, můžete zadat informace o stavu vaší orchestrator clusteru tak, aby cluster můžete příslušně na ně reagovat.</span><span class="sxs-lookup"><span data-stu-id="1f767-109">If you are using an orchestrator, you can provide health information to your orchestrator’s cluster, so that the cluster can act accordingly.</span></span> <span data-ttu-id="1f767-110">Pokud Investujete do sestav stavu vysoce kvalitní, který je přizpůsobený pro vaši aplikaci, můžete zjistit a opravit problémy pro běžící aplikaci mnohem snadněji.</span><span class="sxs-lookup"><span data-stu-id="1f767-110">If you invest in high-quality health reporting that is customized for your application, you can detect and fix issues for your running application much more easily.</span></span>

## <a name="implementing-health-checks-in-aspnet-core-services"></a><span data-ttu-id="1f767-111">Implementace stavu kontroluje služby ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="1f767-111">Implementing health checks in ASP.NET Core services</span></span>

<span data-ttu-id="1f767-112">Při vytváření mikroslužeb nebo webové aplikace ASP.NET Core, můžete použít knihovnu out-of-band (ne official je přínosné jako součást ASP.NETCore) s názvem `HealthChecks` od týmu služby ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="1f767-112">When developing an ASP.NET Core microservice or web application, you can use an out-of-band library (not official as part of ASP.NETCore) named `HealthChecks` from the ASP.NET team.</span></span> <span data-ttu-id="1f767-113">Je k dispozici na tomto [úložiště GitHub se vzorovými](https://github.com/dotnet-architecture/HealthChecks).</span><span class="sxs-lookup"><span data-stu-id="1f767-113">It is available at this [GitHub repo](https://github.com/dotnet-architecture/HealthChecks).</span></span>

<span data-ttu-id="1f767-114">Tato knihovna se snadno používá a nabízí funkce, které umožňují, ověřte, že žádné konkrétní externího zdroje potřebné pro vaši aplikaci (například databáze systému SQL Server nebo vzdálené rozhraní API) správně funguje.</span><span class="sxs-lookup"><span data-stu-id="1f767-114">This library is easy to use and provides features that let you validate that any specific external resource needed for your application (like a SQL Server database or remote API) is working properly.</span></span> <span data-ttu-id="1f767-115">Při použití této knihovny, můžete také rozhodnout, co znamená to, jestli prostředek je v pořádku, protože vám vysvětlíme, později.</span><span class="sxs-lookup"><span data-stu-id="1f767-115">When you use this library, you can also decide what it means that the resource is healthy, as we explain later.</span></span>

<span data-ttu-id="1f767-116">Chcete-li použít tuto knihovnu, budete muset nejdřív použít knihovnu v mikroslužby.</span><span class="sxs-lookup"><span data-stu-id="1f767-116">In order to use this library, you need to first use the library in your microservices.</span></span> <span data-ttu-id="1f767-117">Za druhé budete potřebovat front-endové aplikace, který se dotazuje sestavy o stavu.</span><span class="sxs-lookup"><span data-stu-id="1f767-117">Second, you need a front-end application that queries for the health reports.</span></span> <span data-ttu-id="1f767-118">Který aplikace front-endu může být vlastní aplikace pro vytváření sestav, nebo to může být orchestrátor samotného, můžete odpovídajícím způsobem reagovat na stav.</span><span class="sxs-lookup"><span data-stu-id="1f767-118">That front end application could be a custom reporting application, or it could be an orchestrator itself that can react accordingly to the health states.</span></span>

### <a name="using-the-healthchecks-library-in-your-back-end-aspnet-microservices"></a><span data-ttu-id="1f767-119">Použití knihovny HealthChecks v back-endu ASP.NET mikroslužeb</span><span class="sxs-lookup"><span data-stu-id="1f767-119">Using the HealthChecks library in your back end ASP.NET microservices</span></span>

<span data-ttu-id="1f767-120">Uvidíte jak knihovny HealthChecks slouží v aplikaci eShopOnContainers ukázkovou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="1f767-120">You can see how the HealthChecks library is used in the eShopOnContainers sample application.</span></span> <span data-ttu-id="1f767-121">Pokud chcete začít, musíte definovat, co se považuje za bezproblémového stavu u jednotlivých mikroslužeb.</span><span class="sxs-lookup"><span data-stu-id="1f767-121">To begin, you need to define what constitutes a healthy status for each microservice.</span></span> <span data-ttu-id="1f767-122">V ukázkové aplikaci mikroslužby jsou v pořádku, pokud mikroslužeb rozhraní API jsou přístupná přes protokol HTTP a pokud jeho související databáze systému SQL Server je také k dispozici.</span><span class="sxs-lookup"><span data-stu-id="1f767-122">In the sample application, the microservices are healthy if the microservice API is accessible via HTTP and if its related SQL Server database is also available.</span></span>

<span data-ttu-id="1f767-123">V budoucnu bude možné ji nainstalovat HealthChecks jako balíček NuGet.</span><span class="sxs-lookup"><span data-stu-id="1f767-123">In the future, you will be able to install the HealthChecks library as a NuGet package.</span></span> <span data-ttu-id="1f767-124">Ale v době psaní tohoto návodu budete muset stáhnout a kompilaci kódu jako součást vašeho řešení.</span><span class="sxs-lookup"><span data-stu-id="1f767-124">But as of this writing, you need to download and compile the code as part of your solution.</span></span> <span data-ttu-id="1f767-125">Klonování kódu, které jsou k dispozici na https://github.com/dotnet-architecture/HealthChecks a zkopírujte následující složky do vašeho řešení:</span><span class="sxs-lookup"><span data-stu-id="1f767-125">Clone the code available at https://github.com/dotnet-architecture/HealthChecks and copy the following folders to your solution:</span></span>

  - <span data-ttu-id="1f767-126">src/common</span><span class="sxs-lookup"><span data-stu-id="1f767-126">src/common</span></span>
  - <span data-ttu-id="1f767-127">src/Microsoft.AspNetCore.HealthChecks</span><span class="sxs-lookup"><span data-stu-id="1f767-127">src/Microsoft.AspNetCore.HealthChecks</span></span>
  - <span data-ttu-id="1f767-128">src/Microsoft.Extensions.HealthChecks</span><span class="sxs-lookup"><span data-stu-id="1f767-128">src/Microsoft.Extensions.HealthChecks</span></span>
  - <span data-ttu-id="1f767-129">src/Microsoft.Extensions.HealthChecks.SqlServer</span><span class="sxs-lookup"><span data-stu-id="1f767-129">src/Microsoft.Extensions.HealthChecks.SqlServer</span></span>

<span data-ttu-id="1f767-130">Můžete také použít další kontroly, jako jsou pro Azure (Microsoft.Extensions.HealthChecks.AzureStorage), ale vzhledem k tomu, že tato verze aplikaci eShopOnContainers nemá závislost na Azure, není nutné.</span><span class="sxs-lookup"><span data-stu-id="1f767-130">You could also use additional checks like the ones for Azure (Microsoft.Extensions.HealthChecks.AzureStorage), but since this version of eShopOnContainers does not have any dependency on Azure, you do not need it.</span></span> <span data-ttu-id="1f767-131">Není nutné ASP.NET kontroly stavu, protože aplikaci eShopOnContainers je založena na technologii ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="1f767-131">You do not need the ASP.NET health checks, because eShopOnContainers is based on ASP.NET Core.</span></span>

<span data-ttu-id="1f767-132">Obrázek 10 až 6 ukazuje HealthChecks knihovny v sadě Visual Studio, můžete využívat jako stavební blok všechny mikroslužby.</span><span class="sxs-lookup"><span data-stu-id="1f767-132">Figure 10-6 shows the HealthChecks library in Visual Studio, ready to be used as a building block by any microservices.</span></span>

![](./media/image6.png)

<span data-ttu-id="1f767-133">**Obrázek 10 až 6**.</span><span class="sxs-lookup"><span data-stu-id="1f767-133">**Figure 10-6**.</span></span> <span data-ttu-id="1f767-134">Zdrojový kód knihovny ASP.NET Core HealthChecks v řešení sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="1f767-134">ASP.NET Core HealthChecks library source code in a Visual Studio solution</span></span>

<span data-ttu-id="1f767-135">První věc, kterou provedete v každém projektu mikroslužeb zavedeném dříve, je přidejte odkaz na tři HealthChecks knihovny.</span><span class="sxs-lookup"><span data-stu-id="1f767-135">As introduced earlier, the first thing to do in each microservice project is to add a reference to the three HealthChecks libraries.</span></span> <span data-ttu-id="1f767-136">Potom přidáte stav vrácení akce, které chcete provést v tomto mikroslužeb.</span><span class="sxs-lookup"><span data-stu-id="1f767-136">After that, you add the health check actions that you want to perform in that microservice.</span></span> <span data-ttu-id="1f767-137">Tyto akce jsou v podstatě závislosti na jiných mikroslužby (HttpUrlCheck) nebo databází (aktuálně SqlCheck\* databází systému SQL Server).</span><span class="sxs-lookup"><span data-stu-id="1f767-137">These actions are basically dependencies on other microservices (HttpUrlCheck) or databases (currently SqlCheck\* for SQL Server databases).</span></span> <span data-ttu-id="1f767-138">Můžete přidat akce v rámci třídy spuštění jednotlivých mikroslužeb technologie ASP.NET nebo webové aplikace ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="1f767-138">You add the action within the Startup class of each ASP.NET microservice or ASP.NET web application.</span></span>

<span data-ttu-id="1f767-139">Každá služba nebo webové aplikace musí být nakonfigurovaný tak, že přidáte všechny její závislosti protokolu HTTP nebo databází jako jednu metodu AddHealthCheck.</span><span class="sxs-lookup"><span data-stu-id="1f767-139">Each service or web application should be configured by adding all its HTTP or database dependencies as one AddHealthCheck method.</span></span> <span data-ttu-id="1f767-140">Například webové aplikace MVC v aplikaci eShopOnContainers závisí na mnoha službách, proto má několik metod AddCheck přidán na kontroly stavu.</span><span class="sxs-lookup"><span data-stu-id="1f767-140">For example, the MVC web application from eShopOnContainers depends on many services, therefore has several AddCheck methods added to the health checks.</span></span>

<span data-ttu-id="1f767-141">V následujícím kódu, uvidíte jak mikroslužeb katalogu přidá závislost na jeho databáze systému SQL Server.</span><span class="sxs-lookup"><span data-stu-id="1f767-141">For instance, in the following code you can see how the catalog microservice adds a dependency on its SQL Server database.</span></span>

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

<span data-ttu-id="1f767-142">Webovou aplikaci MVC aplikaci eShopOnContainers má ale více závislostí na zbývajících mikroslužby.</span><span class="sxs-lookup"><span data-stu-id="1f767-142">However, the MVC web application of eShopOnContainers has multiple dependencies on the rest of the microservices.</span></span> <span data-ttu-id="1f767-143">Proto volání metod AddUrlCheck u jednotlivých mikroslužeb, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="1f767-143">Therefore, it calls one AddUrlCheck method for each microservice, as shown in the following example:</span></span>

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

<span data-ttu-id="1f767-144">Mikroslužby proto neposkytne "v pořádku" stav, dokud všechny jeho kontroly jsou také v pořádku.</span><span class="sxs-lookup"><span data-stu-id="1f767-144">Thus, a microservice will not provide a “healthy” status until all its checks are healthy as well.</span></span>

<span data-ttu-id="1f767-145">Pokud mikroslužbách nemá závislost na službě nebo na serveru SQL Server, měli byste přidat jenom kontrolu Healthy("Ok").</span><span class="sxs-lookup"><span data-stu-id="1f767-145">If the microservice does not have a dependency on a service or on SQL Server, you should just add a Healthy("Ok") check.</span></span> <span data-ttu-id="1f767-146">Následující kód se z mikroslužeb basket.api aplikaci eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="1f767-146">The following code is from the eShopOnContainers basket.api microservice.</span></span> <span data-ttu-id="1f767-147">(Nákupní košík mikroslužeb používá mezipaměť Redis, ale knihovny zatím nezahrnuje zprostředkovatele Redis stav kontroly.)</span><span class="sxs-lookup"><span data-stu-id="1f767-147">(The basket microservice uses the Redis cache, but the library does not yet include a Redis health check provider.)</span></span>

```csharp
services.AddHealthChecks(checks =>
{
    checks.AddValueTaskCheck("HTTP Endpoint", () => new
        ValueTask<IHealthCheckResult>(HealthCheckResult.Healthy("Ok")));
});
```

<span data-ttu-id="1f767-148">Služby nebo webové aplikace zveřejněte koncový bod kontroly stavu, je třeba povolit UseHealthChecks (\[*url\_pro\_stavu\_kontroluje*\]) rozšíření Metoda.</span><span class="sxs-lookup"><span data-stu-id="1f767-148">For a service or web application to expose the health check endpoint, it has to enable the UseHealthChecks(\[*url\_for\_health\_checks*\]) extension method.</span></span> <span data-ttu-id="1f767-149">Tato metoda přejde na WebHostBuilder úrovně v hlavní metodě třídy aplikace ASP.NET Core service nebo webové aplikace, hned po UseKestrel, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="1f767-149">This method goes at the WebHostBuilder level in the main method of the Program class of your ASP.NET Core service or web application, right after UseKestrel as shown in the code below.</span></span>

```csharp
namespace Microsoft.eShopOnContainers.WebMVC
{
    public class Program
    {
        public static void Main(string[] args)
        {
            var host = new WebHostBuilder()
                .UseKestrel()
                .UseHealthChecks("/hc")
                .UseContentRoot(Directory.GetCurrentDirectory())
                .UseIISIntegration()
                .UseStartup<Startup>()
                .Build();
            host.Run();
        }
    }
}
```

<span data-ttu-id="1f767-150">Tento proces funguje takto: jednotlivých mikroslužeb poskytuje HC koncový bod.</span><span class="sxs-lookup"><span data-stu-id="1f767-150">The process works like this: each microservice exposes the endpoint /hc.</span></span> <span data-ttu-id="1f767-151">Tento koncový bod se vytvořil HealthChecks knihovna middlewarových ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="1f767-151">That endpoint is created by the HealthChecks library ASP.NET Core middleware.</span></span> <span data-ttu-id="1f767-152">Při vyvolání tohoto koncového bodu, spustí všechny kontroly stavu, které jsou nakonfigurované v metodě AddHealthChecks ve třídě spuštění.</span><span class="sxs-lookup"><span data-stu-id="1f767-152">When that endpoint is invoked, it runs all the health checks that are configured in the AddHealthChecks method in the Startup class.</span></span>

<span data-ttu-id="1f767-153">Metoda UseHealthChecks očekává, že port nebo cestu.</span><span class="sxs-lookup"><span data-stu-id="1f767-153">The UseHealthChecks method expects a port or a path.</span></span> <span data-ttu-id="1f767-154">Tento port nebo cesta jsou koncový bod, který slouží ke kontrole stavu služby.</span><span class="sxs-lookup"><span data-stu-id="1f767-154">That port or path is the endpoint to use to check the health state of the service.</span></span> <span data-ttu-id="1f767-155">Například mikroslužeb katalogu používá HC cestu.</span><span class="sxs-lookup"><span data-stu-id="1f767-155">For instance, the catalog microservice uses the path /hc.</span></span>

### <a name="caching-health-check-responses"></a><span data-ttu-id="1f767-156">Ukládání do mezipaměti odpovědi na kontrolu stavu</span><span class="sxs-lookup"><span data-stu-id="1f767-156">Caching health check responses</span></span>

<span data-ttu-id="1f767-157">Vzhledem k tomu, že nechcete způsobit odepření služby (DoS) ve vašich službách nebo jednoduše nechcete dopad na výkon služby tak, že zkontrolujete prostředky příliš často, můžete vrátí do mezipaměti a nakonfigurovat doba mezipaměti pro každou kontrolu stavu.</span><span class="sxs-lookup"><span data-stu-id="1f767-157">Since you do not want to cause a Denial of Service (DoS) in your services, or you simply do not want to impact service performance by checking resources too frequently, you can cache the returns and configure a cache duration for each health check.</span></span>

<span data-ttu-id="1f767-158">Ve výchozím nastavení Doba uložení do mezipaměti interně nastavena na 5 minut, ale můžete změnit této mezipaměti na každé kontrolu stavu, stejně jako v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="1f767-158">By default, the cache duration is internally set to 5 minutes, but you can change that cache duration on each health check, as in the following code:</span></span>

```csharp
checks.AddUrlCheck(Configuration["CatalogUrl"],1); // 1 min as cache duration
```

### <a name="querying-your-microservices-to-report-about-their-health-status"></a><span data-ttu-id="1f767-159">Dotazování na mikroslužby na zprávu o jejich stavu</span><span class="sxs-lookup"><span data-stu-id="1f767-159">Querying your microservices to report about their health status</span></span>

<span data-ttu-id="1f767-160">Kontroly stavu jste nakonfigurovali podle postupu popsaného tady, jakmile je spuštěna mikroslužby v Dockeru, můžete přímo zkontrolovat z prohlížeče pokud je v pořádku.</span><span class="sxs-lookup"><span data-stu-id="1f767-160">When you have configured health checks as described here, once the microservice is running in Docker, you can directly check from a browser if it is healthy.</span></span> <span data-ttu-id="1f767-161">(To vyžaduje, že publikujete port kontejneru Dockeru hostitele, tak prostřednictvím místního hostitele nebo externí IP adresa hostitele Docker můžete přístup ke kontejneru.) Obrázek 10-7 ukazuje požadavek v prohlížeči a odpovídající odpověď.</span><span class="sxs-lookup"><span data-stu-id="1f767-161">(This does require that you are publishing the container port out of the Docker host, so you can access the container through localhost or through the external Docker host IP.) Figure 10-7 shows a request in a browser and the corresponding response.</span></span>

![](./media/image7.png)

<span data-ttu-id="1f767-162">**Obrázek 10-7**.</span><span class="sxs-lookup"><span data-stu-id="1f767-162">**Figure 10-7**.</span></span> <span data-ttu-id="1f767-163">Kontroluje se stav jedinou službou v prohlížeči</span><span class="sxs-lookup"><span data-stu-id="1f767-163">Checking health status of a single service from a browser</span></span>

<span data-ttu-id="1f767-164">V testu uvidíte, že je v pořádku, mikroslužbách catalog.api (spuštěné na portu 5101) vrací stav protokolu HTTP 200 a informace o stavu ve formátu JSON.</span><span class="sxs-lookup"><span data-stu-id="1f767-164">In that test, you can see that the catalog.api microservice (running on port 5101) is healthy, returning HTTP status 200 and status information in JSON.</span></span> <span data-ttu-id="1f767-165">To také znamená, že interně služba zkontrolovány také stav jeho závislost databáze systému SQL Server a, kontrola stavu samotné byl nahlášen jako v pořádku.</span><span class="sxs-lookup"><span data-stu-id="1f767-165">It also means that internally the service also checked the health of its SQL Server database dependency and that health check was reported itself as healthy.</span></span>

## <a name="using-watchdogs"></a><span data-ttu-id="1f767-166">Pomocí watchdogs</span><span class="sxs-lookup"><span data-stu-id="1f767-166">Using watchdogs</span></span>

<span data-ttu-id="1f767-167">Sledovacího zařízení je samostatná služba, která může sledovat stav a zatížení napříč službami a stavu sestavy o mikroslužby pomocí dotazu s knihovnou HealthChecks zavedené dříve.</span><span class="sxs-lookup"><span data-stu-id="1f767-167">A watchdog is a separate service that can watch health and load across services, and report health about the microservices by querying with the HealthChecks library introduced earlier.</span></span> <span data-ttu-id="1f767-168">To může pomoci zabránit chybám, které nebudou zjištěny založené na zobrazení jedné služby.</span><span class="sxs-lookup"><span data-stu-id="1f767-168">This can help prevent errors that would not be detected based on the view of a single service.</span></span> <span data-ttu-id="1f767-169">Watchdogs je také vhodné místo pro hostování kódu, který může provádět nápravné akce pro známé podmínky bez zásahu uživatele.</span><span class="sxs-lookup"><span data-stu-id="1f767-169">Watchdogs also are a good place to host code that can perform remediation actions for known conditions without user interaction.</span></span>

<span data-ttu-id="1f767-170">Ukázkové aplikaci eShopOnContainers obsahuje webovou stránku, která zobrazí ukázkové sestavy stavu zaškrtnutí, jak ukazuje obrázek 10-8.</span><span class="sxs-lookup"><span data-stu-id="1f767-170">The eShopOnContainers sample contains a web page that displays sample health check reports, as shown in Figure 10-8.</span></span> <span data-ttu-id="1f767-171">Toto je nejjednodušší sledovacího zařízení může mít, protože celá jeho se zobrazují stav mikroslužbách a webových aplikací v aplikaci eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="1f767-171">This is the simplest watchdog you could have, since all it does is shows the state of the microservices and web applications in eShopOnContainers.</span></span> <span data-ttu-id="1f767-172">Obvykle sledovacího zařízení také provede akce při zjišťuje stavy není v pořádku.</span><span class="sxs-lookup"><span data-stu-id="1f767-172">Usually a watchdog also takes actions when it detects unhealthy states.</span></span>

![](./media/image8.png)

<span data-ttu-id="1f767-173">**Obrázek 10-8**.</span><span class="sxs-lookup"><span data-stu-id="1f767-173">**Figure 10-8**.</span></span> <span data-ttu-id="1f767-174">Ukázková sestava kontroly stavu v aplikaci eShopOnContainers</span><span class="sxs-lookup"><span data-stu-id="1f767-174">Sample health check report in eShopOnContainers</span></span>

<span data-ttu-id="1f767-175">Stručně řečeno middleware ASP.NET knihovny ASP.NET Core HealthChecks poskytuje koncový bod jednoho stavu zaškrtnutí u jednotlivých mikroslužeb.</span><span class="sxs-lookup"><span data-stu-id="1f767-175">In summary, the ASP.NET middleware of the ASP.NET Core HealthChecks library provides a single health check endpoint for each microservice.</span></span> <span data-ttu-id="1f767-176">To spustí všechny kontroly stavu, v něm definovanou a vrátit celkového přehledu o stavu v závislosti na těchto kontrol.</span><span class="sxs-lookup"><span data-stu-id="1f767-176">This will execute all the health checks defined within it and return an overall health state depending on all those checks.</span></span>

<span data-ttu-id="1f767-177">Knihovna HealthChecks je rozšiřitelný prostřednictvím nové kontroly stavu budoucí externích prostředků.</span><span class="sxs-lookup"><span data-stu-id="1f767-177">The HealthChecks library is extensible through new health checks of future external resources.</span></span> <span data-ttu-id="1f767-178">Například Očekáváme, že v budoucnu knihovny bude mít kontroly stavu pro mezipaměť Redis a pro ostatní databáze.</span><span class="sxs-lookup"><span data-stu-id="1f767-178">For example, we expect that in the future the library will have health checks for Redis cache and for other databases.</span></span> <span data-ttu-id="1f767-179">Knihovny umožňuje zdraví, vytváření sestav ve více závislostí služby nebo aplikace, a pak můžete provádět akce založené na tyto kontroly stavu.</span><span class="sxs-lookup"><span data-stu-id="1f767-179">The library allows health reporting by multiple service or application dependencies, and you can then take actions based on those health checks.</span></span>

## <a name="health-checks-when-using-orchestrators"></a><span data-ttu-id="1f767-180">Kontroly stavu při použití orchestrátorů</span><span class="sxs-lookup"><span data-stu-id="1f767-180">Health checks when using orchestrators</span></span>

<span data-ttu-id="1f767-181">Pokud chcete monitorovat dostupnost mikroslužby, orchestrátorů, jako je Docker Swarm, Kubernetes a Service Fabric pravidelně provádět kontroly stavu pomocí zasílání požadavků na test mikroslužby.</span><span class="sxs-lookup"><span data-stu-id="1f767-181">To monitor the availability of your microservices, orchestrators like Docker Swarm, Kubernetes, and Service Fabric periodically perform health checks by sending requests to test the microservices.</span></span> <span data-ttu-id="1f767-182">Když orchestrátor zjistí, že služby/kontejneru není v pořádku, že zastaví směrování požadavků do této instance.</span><span class="sxs-lookup"><span data-stu-id="1f767-182">When an orchestrator determines that a service/container is unhealthy, it stops routing requests to that instance.</span></span> <span data-ttu-id="1f767-183">Také obvykle vytvoří novou instanci kontejneru.</span><span class="sxs-lookup"><span data-stu-id="1f767-183">It also usually creates a new instance of that container.</span></span>

<span data-ttu-id="1f767-184">Většina orchestrátorů, můžete použít kontroly stavu pro správu nasazení s nulovými výpadky.</span><span class="sxs-lookup"><span data-stu-id="1f767-184">For instance, most orchestrators can use health checks to manage zero-downtime deployments.</span></span> <span data-ttu-id="1f767-185">Pouze v případě, že bude stav kontejneru služby/změny v pořádku orchestrátoru start směrování provozu do služby a container instances.</span><span class="sxs-lookup"><span data-stu-id="1f767-185">Only when the status of a service/container changes to healthy will the orchestrator start routing traffic to service/container instances.</span></span>

<span data-ttu-id="1f767-186">Monitorování stavu je obzvláště důležité, když orchestrátor provádí upgrade aplikace.</span><span class="sxs-lookup"><span data-stu-id="1f767-186">Health monitoring is especially important when an orchestrator performs an application upgrade.</span></span> <span data-ttu-id="1f767-187">Některé zvolené orchestrátory (jako je Azure Service Fabric) aktualizovat služby ve fázích – například může aktualizovat jeden pátého povrchu clusteru pro každý upgrade aplikace.</span><span class="sxs-lookup"><span data-stu-id="1f767-187">Some orchestrators (like Azure Service Fabric) update services in phases—for example, they might update one-fifth of the cluster surface for each application upgrade.</span></span> <span data-ttu-id="1f767-188">Sada uzlů, který se upgraduje ve stejnou dobu se označuje jako *upgradovací doména*.</span><span class="sxs-lookup"><span data-stu-id="1f767-188">The set of nodes that is upgraded at the same time is referred to as an *upgrade domain*.</span></span> <span data-ttu-id="1f767-189">Po každé upgradovací doména byl upgradován a je k dispozici pro uživatele, že upgradovací doména musí uplynout kontroly stavu nasazení přejde k další upgradovací doméně.</span><span class="sxs-lookup"><span data-stu-id="1f767-189">After each upgrade domain has been upgraded and is available to users, that upgrade domain must pass health checks before the deployment moves to the next upgrade domain.</span></span>

<span data-ttu-id="1f767-190">Dalším aspektem služby service health je generování sestav metrik ze služby.</span><span class="sxs-lookup"><span data-stu-id="1f767-190">Another aspect of service health is reporting metrics from the service.</span></span> <span data-ttu-id="1f767-191">Toto je rozšířená možnost modelu stavu některé zvolené orchestrátory, jako je Service Fabric.</span><span class="sxs-lookup"><span data-stu-id="1f767-191">This is an advanced capability of the health model of some orchestrators, like Service Fabric.</span></span> <span data-ttu-id="1f767-192">Metriky jsou důležité při použití orchestrator, protože se používají k vyrovnávání využití prostředků.</span><span class="sxs-lookup"><span data-stu-id="1f767-192">Metrics are important when using an orchestrator because they are used to balance resource usage.</span></span> <span data-ttu-id="1f767-193">Metriky taky může být indikátor stavu systému.</span><span class="sxs-lookup"><span data-stu-id="1f767-193">Metrics also can be an indicator of system health.</span></span> <span data-ttu-id="1f767-194">Například může mít aplikaci, která má mnoho mikroslužeb a každá instance sestav metriky požadavků za sekundu (předávajících stran).</span><span class="sxs-lookup"><span data-stu-id="1f767-194">For example, you might have an application that has many microservices, and each instance reports a requests-per-second (RPS) metric.</span></span> <span data-ttu-id="1f767-195">Pokud jedna služba používá další prostředky (paměť, procesor, atd.) než jiné službě, orchestrator může pohybovat instance služby v clusteru se pokouší spravovat i využití prostředků.</span><span class="sxs-lookup"><span data-stu-id="1f767-195">If one service is using more resources (memory, processor, etc.) than another service, the orchestrator could move service instances around in the cluster to try to maintain even resource utilization.</span></span>

<span data-ttu-id="1f767-196">Všimněte si, že pokud používáte Azure Service Fabric, poskytuje vlastní [monitorování stavu modelu](https://docs.microsoft.com/azure/service-fabric/service-fabric-health-introduction), což je složitější než kontroly stavu jednoduché.</span><span class="sxs-lookup"><span data-stu-id="1f767-196">Note that if you are using Azure Service Fabric, it provides its own [Health Monitoring model](https://docs.microsoft.com/azure/service-fabric/service-fabric-health-introduction), which is more advanced than simple health checks.</span></span>

## <a name="advanced-monitoring-visualization-analysis-and-alerts"></a><span data-ttu-id="1f767-197">Rozšířené monitorování: vizualizace, analýzy a upozornění</span><span class="sxs-lookup"><span data-stu-id="1f767-197">Advanced monitoring: visualization, analysis, and alerts</span></span>

<span data-ttu-id="1f767-198">Poslední část monitorování je vizualizace datového proudu událostí, vytváření sestav o výkonu služby a upozorní při zjištění problému.</span><span class="sxs-lookup"><span data-stu-id="1f767-198">The final part of monitoring is visualizing the event stream, reporting on service performance, and alerting when an issue is detected.</span></span> <span data-ttu-id="1f767-199">Můžete použít různá řešení pro tento aspekt monitorování.</span><span class="sxs-lookup"><span data-stu-id="1f767-199">You can use different solutions for this aspect of monitoring.</span></span>

<span data-ttu-id="1f767-200">Můžete použít jednoduchý vlastní aplikace zobrazuje stav služeb, stejně jako vlastní stránku jsme ukázali, když jsme vysvětlení [ASP.NET Core HealthChecks](https://github.com/aspnet/HealthChecks).</span><span class="sxs-lookup"><span data-stu-id="1f767-200">You can use simple custom applications showing the state of your services, like the custom page we showed when we explained [ASP.NET Core HealthChecks](https://github.com/aspnet/HealthChecks).</span></span> <span data-ttu-id="1f767-201">Nebo můžete použít rozšířené nástroje, jako je Azure Application Insights a Operations Management Suite budou generovány výstrahy založené na události datového proudu.</span><span class="sxs-lookup"><span data-stu-id="1f767-201">Or you could use more advanced tools like Azure Application Insights and Operations Management Suite to raise alerts based on the stream of events.</span></span>

<span data-ttu-id="1f767-202">Nakonec pokud byly ukládání všech datových proudů událostí, můžete použít Microsoft Power BI nebo řešení třetí strany, jako je Kibana nebo Splunk k vizualizaci dat.</span><span class="sxs-lookup"><span data-stu-id="1f767-202">Finally, if you were storing all the event streams, you can use Microsoft Power BI or a third-party solution like Kibana or Splunk to visualize the data.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="1f767-203">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="1f767-203">Additional resources</span></span>

-   <span data-ttu-id="1f767-204">**ASP.NET Core HealthChecks** (dřívější verze) [*https://github.com/aspnet/HealthChecks/*](https://github.com/aspnet/HealthChecks/)</span><span class="sxs-lookup"><span data-stu-id="1f767-204">**ASP.NET Core HealthChecks** (early release) [*https://github.com/aspnet/HealthChecks/*](https://github.com/aspnet/HealthChecks/)</span></span>

-   <span data-ttu-id="1f767-205">**Úvod do monitorování stavu Service Fabric**
    [*https://docs.microsoft.com/azure/service-fabric/service-fabric-health-introduction*](https://docs.microsoft.com/azure/service-fabric/service-fabric-health-introduction)</span><span class="sxs-lookup"><span data-stu-id="1f767-205">**Introduction to Service Fabric health monitoring**
[*https://docs.microsoft.com/azure/service-fabric/service-fabric-health-introduction*](https://docs.microsoft.com/azure/service-fabric/service-fabric-health-introduction)</span></span>

-   <span data-ttu-id="1f767-206">**Azure Application Insights**
    [*https://azure.microsoft.com/services/application-insights/*](https://azure.microsoft.com/services/application-insights/)</span><span class="sxs-lookup"><span data-stu-id="1f767-206">**Azure Application Insights**
[*https://azure.microsoft.com/services/application-insights/*](https://azure.microsoft.com/services/application-insights/)</span></span>

-   <span data-ttu-id="1f767-207">**Microsoft Operations Management Suite**
    [*https://www.microsoft.com/en-us/cloud-platform/operations-management-suite*](https://www.microsoft.com/en-us/cloud-platform/operations-management-suite)</span><span class="sxs-lookup"><span data-stu-id="1f767-207">**Microsoft Operations Management Suite**
[*https://www.microsoft.com/en-us/cloud-platform/operations-management-suite*](https://www.microsoft.com/en-us/cloud-platform/operations-management-suite)</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="1f767-208">[Předchozí](implement-circuit-breaker-pattern.md)
>[další](../secure-net-microservices-web-applications/index.md)</span><span class="sxs-lookup"><span data-stu-id="1f767-208">[Previous](implement-circuit-breaker-pattern.md)
[Next](../secure-net-microservices-web-applications/index.md)</span></span>