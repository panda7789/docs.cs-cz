---
title: "Monitorování stavu"
description: "Architektura Mikroslužeb .NET pro aplikace .NET Kontejnerizované | Monitorování stavu"
keywords: "Docker, Mikroslužeb, ASP.NET, kontejneru"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: cbbad72f06bcaa882bc50083d9103b0872f51754
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="health-monitoring"></a><span data-ttu-id="0e88e-104">Monitorování stavu</span><span class="sxs-lookup"><span data-stu-id="0e88e-104">Health monitoring</span></span>

<span data-ttu-id="0e88e-105">Sledování stavu můžete povolit téměř v reálném čase informací o stavu kontejnery a mikroslužeb.</span><span class="sxs-lookup"><span data-stu-id="0e88e-105">Health monitoring can allow near-real-time information about the state of your containers and microservices.</span></span> <span data-ttu-id="0e88e-106">Sledování stavu je pro několik aspektů operačního mikroslužeb a je zvlášť důležité při orchestrators částečné aplikace upgrady provádět v fází, jak je popsáno později.</span><span class="sxs-lookup"><span data-stu-id="0e88e-106">Health monitoring is critical to multiple aspects of operating microservices and is especially important when orchestrators perform partial application upgrades in phases, as explained later.</span></span>

<span data-ttu-id="0e88e-107">Aplikace založené na Mikroslužeb často používají prezenčních signálů nebo stavu ověří jejich monitorování výkonu, plánovače a orchestrators ke sledování velkého množství services povolit.</span><span class="sxs-lookup"><span data-stu-id="0e88e-107">Microservices-based applications often use heartbeats or health checks to enable their performance monitors, schedulers, and orchestrators to keep track of the multitude of services.</span></span> <span data-ttu-id="0e88e-108">Pokud služby nelze odeslat nějaká "Jsem zachování" signálu na vyžádání nebo podle plánu, může aplikace čelí rizika při nasazení aktualizací, nebo může být jednoduše příliš pozdní rozpoznala chyby a není možné zastavit kaskádových chyb, které se můžou skončit ve hlavní výpadků.</span><span class="sxs-lookup"><span data-stu-id="0e88e-108">If services cannot send some sort of “I’m alive” signal, either on demand or on a schedule, your application might face risks when you deploy updates, or it might simply detect failures too late and not be able to stop cascading failures that can end up in major outages.</span></span>

<span data-ttu-id="0e88e-109">V typické modelu služby odesílat zprávy o jejich stavu a zobrazují se tyto informace k poskytování celkový přehled o stavu stavu aplikace.</span><span class="sxs-lookup"><span data-stu-id="0e88e-109">In the typical model, services send reports about their status, and that information is aggregated to provide an overall view of the state of health of your application.</span></span> <span data-ttu-id="0e88e-110">Pokud používáte orchestrator, zajistíte tak, aby cluster může fungovat odpovídajícím způsobem informace o stavu vaší orchestrator clusteru.</span><span class="sxs-lookup"><span data-stu-id="0e88e-110">If you are using an orchestrator, you can provide health information to your orchestrator’s cluster, so that the cluster can act accordingly.</span></span> <span data-ttu-id="0e88e-111">Pokud jste investovat do vysoce kvalitní stavu vytváření sestav, které je přizpůsobené pro vaši aplikaci, můžete zjistit a opravit problémy mnohem snadněji pro běžící aplikaci.</span><span class="sxs-lookup"><span data-stu-id="0e88e-111">If you invest in high-quality health reporting that is customized for your application, you can detect and fix issues for your running application much more easily.</span></span>

## <a name="implementing-health-checks-in-aspnet-core-services"></a><span data-ttu-id="0e88e-112">Implementace stavu změnami ASP.NET Core services</span><span class="sxs-lookup"><span data-stu-id="0e88e-112">Implementing health checks in ASP.NET Core services</span></span>

<span data-ttu-id="0e88e-113">Při vývoji aplikace ASP.NET Core mikroslužbu nebo webové aplikace, můžete použít knihovny s názvem HealthChecks od týmu ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="0e88e-113">When developing an ASP.NET Core microservice or web application, you can use a library named HealthChecks from the ASP.NET team.</span></span> <span data-ttu-id="0e88e-114">(Od může 2017 je dostupná na Githubu předběžnou verzi).</span><span class="sxs-lookup"><span data-stu-id="0e88e-114">(As of May 2017, an early release is available on GitHub).</span></span>

<span data-ttu-id="0e88e-115">Tato knihovna je snadno použitelný a poskytuje funkce, která umožňují, které jste ověřte, že žádné konkrétní externí prostředek pro vaši aplikaci (například databáze systému SQL Server nebo rozhraní API pro vzdálené) správně funguje.</span><span class="sxs-lookup"><span data-stu-id="0e88e-115">This library is easy to use and provides features that let you validate that any specific external resource needed for your application (like a SQL Server database or remote API) is working properly.</span></span> <span data-ttu-id="0e88e-116">Při použití této knihovny, můžete také určit, co znamená, že je prostředek v pořádku, protože objasníme později.</span><span class="sxs-lookup"><span data-stu-id="0e88e-116">When you use this library, you can also decide what it means that the resource is healthy, as we explain later.</span></span>

<span data-ttu-id="0e88e-117">Chcete-li použít tuto knihovnu, musíte nejprve použít knihovnu v vaší mikroslužeb.</span><span class="sxs-lookup"><span data-stu-id="0e88e-117">In order to use this library, you need to first use the library in your microservices.</span></span> <span data-ttu-id="0e88e-118">Druhý musíte aplikace front-endu, který se dotazuje pro sestavy stavu.</span><span class="sxs-lookup"><span data-stu-id="0e88e-118">Second, you need a front-end application that queries for the health reports.</span></span> <span data-ttu-id="0e88e-119">Který front-endu aplikace může být vlastní vytváření sestav aplikace, nebo může být orchestrator sám sebe, který můžete odpovídajícím způsobem reagovat na stav.</span><span class="sxs-lookup"><span data-stu-id="0e88e-119">That front end application could be a custom reporting application, or it could be an orchestrator itself that can react accordingly to the health states.</span></span>

### <a name="using-the-healthchecks-library-in-your-back-end-aspnet-microservices"></a><span data-ttu-id="0e88e-120">Použití knihovny HealthChecks v back-end vašeho mikroslužeb ASP.NET</span><span class="sxs-lookup"><span data-stu-id="0e88e-120">Using the HealthChecks library in your back end ASP.NET microservices</span></span>

<span data-ttu-id="0e88e-121">Uvidíte použití knihovny HealthChecks v eShopOnContainers ukázkovou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="0e88e-121">You can see how the HealthChecks library is used in the eShopOnContainers sample application.</span></span> <span data-ttu-id="0e88e-122">Pokud chcete začít, musíte definovat, co se považuje za dobrý stav pro každý mikroslužby.</span><span class="sxs-lookup"><span data-stu-id="0e88e-122">To begin, you need to define what constitutes a healthy status for each microservice.</span></span> <span data-ttu-id="0e88e-123">V ukázkové aplikace jsou v pořádku, pokud mikroslužbu rozhraní API je přístupná prostřednictvím protokolu HTTP a jeho souvisejících databáze systému SQL Server je také k dispozici mikroslužeb.</span><span class="sxs-lookup"><span data-stu-id="0e88e-123">In the sample application, the microservices are healthy if the microservice API is accessible via HTTP and if its related SQL Server database is also available.</span></span>

<span data-ttu-id="0e88e-124">V budoucnu nebudete moct instalovat knihovně HealthChecks jako balíčku NuGet.</span><span class="sxs-lookup"><span data-stu-id="0e88e-124">In the future, you will be able to install the HealthChecks library as a NuGet package.</span></span> <span data-ttu-id="0e88e-125">Ale v době psaní tohoto textu, budete muset stáhnout a zkompilovat kód v rámci vašeho řešení.</span><span class="sxs-lookup"><span data-stu-id="0e88e-125">But as of this writing, you need to download and compile the code as part of your solution.</span></span> <span data-ttu-id="0e88e-126">Zkopírujte kód, který je k dispozici na https://github.com/aspnet/HealthChecks a zkopírujte následující složky pro vaše řešení.</span><span class="sxs-lookup"><span data-stu-id="0e88e-126">Clone the code available at https://github.com/aspnet/HealthChecks and copy the following folders to your solution.</span></span>

  - <span data-ttu-id="0e88e-127">src/společné</span><span class="sxs-lookup"><span data-stu-id="0e88e-127">src/common</span></span>
  - <span data-ttu-id="0e88e-128">src/Microsoft.AspNetCore.HealthChecks</span><span class="sxs-lookup"><span data-stu-id="0e88e-128">src/Microsoft.AspNetCore.HealthChecks</span></span>
  - <span data-ttu-id="0e88e-129">src/Microsoft.Extensions.HealthChecks</span><span class="sxs-lookup"><span data-stu-id="0e88e-129">src/Microsoft.Extensions.HealthChecks</span></span>
  - <span data-ttu-id="0e88e-130">src/Microsoft.Extensions.HealthChecks.SqlServer</span><span class="sxs-lookup"><span data-stu-id="0e88e-130">src/Microsoft.Extensions.HealthChecks.SqlServer</span></span>

<span data-ttu-id="0e88e-131">Můžete také použít další kontroly, jako jsou pro Azure (Microsoft.Extensions.HealthChecks.AzureStorage), ale vzhledem k tomu, že tato verze eShopOnContainers nemá žádné závislosti na platformě Azure, není nutné.</span><span class="sxs-lookup"><span data-stu-id="0e88e-131">You could also use additional checks like the ones for Azure (Microsoft.Extensions.HealthChecks.AzureStorage), but since this version of eShopOnContainers does not have any dependency on Azure, you do not need it.</span></span> <span data-ttu-id="0e88e-132">Není nutné kontroly stavu ASP.NET, protože eShopOnContainers je založena na ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="0e88e-132">You do not need the ASP.NET health checks, because eShopOnContainers is based on ASP.NET Core.</span></span>

<span data-ttu-id="0e88e-133">Obrázek 10-6 ukazuje knihovně HealthChecks v sadě Visual Studio, budete moct používat jako stavební blok ve všech mikroslužeb.</span><span class="sxs-lookup"><span data-stu-id="0e88e-133">Figure 10-6 shows the HealthChecks library in Visual Studio, ready to be used as a building block by any microservices.</span></span>

![](./media/image6.png)

<span data-ttu-id="0e88e-134">**Obrázek 10-6**.</span><span class="sxs-lookup"><span data-stu-id="0e88e-134">**Figure 10-6**.</span></span> <span data-ttu-id="0e88e-135">ASP.NET Core HealthChecks knihovny zdrojový kód v řešení sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="0e88e-135">ASP.NET Core HealthChecks library source code in a Visual Studio solution</span></span>

<span data-ttu-id="0e88e-136">Zavádí dříve, je první věc, kterou chcete provést v jednotlivých projektů mikroslužbu se přidat odkaz na tři HealthChecks knihovny.</span><span class="sxs-lookup"><span data-stu-id="0e88e-136">As introduced earlier, the first thing to do in each microservice project is to add a reference to the three HealthChecks libraries.</span></span> <span data-ttu-id="0e88e-137">Potom přidáte akce kontroly stavu, které chcete provést v této mikroslužby.</span><span class="sxs-lookup"><span data-stu-id="0e88e-137">After that, you add the health check actions that you want to perform in that microservice.</span></span> <span data-ttu-id="0e88e-138">Tyto akce jsou v podstatě závislosti na jiných mikroslužeb (HttpUrlCheck) nebo databáze (aktuálně SqlCheck\* databází systému SQL Server).</span><span class="sxs-lookup"><span data-stu-id="0e88e-138">These actions are basically dependencies on other microservices (HttpUrlCheck) or databases (currently SqlCheck\* for SQL Server databases).</span></span> <span data-ttu-id="0e88e-139">Můžete přidat akce v rámci třídy spuštění každé mikroslužbu ASP.NET nebo webové aplikace ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="0e88e-139">You add the action within the Startup class of each ASP.NET microservice or ASP.NET web application.</span></span>

<span data-ttu-id="0e88e-140">Každá služba nebo webové aplikace musí být nakonfigurovaný tak, že přidáte všechny jeho závislosti protokolu HTTP nebo databáze jako jednu metodu AddHealthCheck.</span><span class="sxs-lookup"><span data-stu-id="0e88e-140">Each service or web application should be configured by adding all its HTTP or database dependencies as one AddHealthCheck method.</span></span> <span data-ttu-id="0e88e-141">Například webové aplikace MVC z eShopOnContainers závisí na mnoha službách, proto má několik metod AddCheck přidány do kontroly stavu.</span><span class="sxs-lookup"><span data-stu-id="0e88e-141">For example, the MVC web application from eShopOnContainers depends on many services, therefore has several AddCheck methods added to the health checks.</span></span>

<span data-ttu-id="0e88e-142">Následující kód například uvidíte jak mikroslužbu katalogu přidá závislost na svou databázi systému SQL Server.</span><span class="sxs-lookup"><span data-stu-id="0e88e-142">For instance, in the following code you can see how the catalog microservice adds a dependency on its SQL Server database.</span></span>

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

<span data-ttu-id="0e88e-143">Webová aplikace MVC z eShopOnContainers však má více závislostí na zbytek mikroslužeb.</span><span class="sxs-lookup"><span data-stu-id="0e88e-143">However, the MVC web application of eShopOnContainers has multiple dependencies on the rest of the microservices.</span></span> <span data-ttu-id="0e88e-144">Proto volá metodu jeden AddUrlCheck pro každý mikroslužbu, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="0e88e-144">Therefore, it calls one AddUrlCheck method for each microservice, as shown in the following example:</span></span>

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

<span data-ttu-id="0e88e-145">Mikroslužbu proto nebude poskytovat "v pořádku" stav, dokud všechny jeho kontroly jsou také v pořádku.</span><span class="sxs-lookup"><span data-stu-id="0e88e-145">Thus, a microservice will not provide a “healthy” status until all its checks are healthy as well.</span></span>

<span data-ttu-id="0e88e-146">Pokud mikroslužbu nemá závislost na službě, nebo na serveru SQL Server, měli byste přidat jenom kontrolu Healthy("Ok").</span><span class="sxs-lookup"><span data-stu-id="0e88e-146">If the microservice does not have a dependency on a service or on SQL Server, you should just add a Healthy("Ok") check.</span></span> <span data-ttu-id="0e88e-147">Následující kód je z mikroslužbu basket.api eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="0e88e-147">The following code is from the eShopOnContainers basket.api microservice.</span></span> <span data-ttu-id="0e88e-148">(Nákupní košík mikroslužbu používá mezipaměť Redis, ale knihovny ještě nezahrnuje poskytovatele Kontrola stavu Redis.)</span><span class="sxs-lookup"><span data-stu-id="0e88e-148">(The basket microservice uses the Redis cache, but the library does not yet include a Redis health check provider.)</span></span>

```csharp
services.AddHealthChecks(checks =>
{
    checks.AddValueTaskCheck("HTTP Endpoint", () => new
        ValueTask<IHealthCheckResult>(HealthCheckResult.Healthy("Ok")));
});
```

<span data-ttu-id="0e88e-149">Pro službu nebo webovou aplikaci vystavit koncový bod kontrolu stavu, je povolit UseHealthChecks (\[*url\_pro\_stavu\_kontroluje*\]) rozšíření Metoda.</span><span class="sxs-lookup"><span data-stu-id="0e88e-149">For a service or web application to expose the health check endpoint, it has to enable the UseHealthChecks(\[*url\_for\_health\_checks*\]) extension method.</span></span> <span data-ttu-id="0e88e-150">Tato metoda přejde na WebHostBuilder úrovni v metodě hlavní třídy Program ASP.NET Core služby nebo webové aplikace, hned po UseKestrel, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="0e88e-150">This method goes at the WebHostBuilder level in the main method of the Program class of your ASP.NET Core service or web application, right after UseKestrel as shown in the code below.</span></span>

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

<span data-ttu-id="0e88e-151">Probíhá proces takto: každý mikroslužbu zpřístupní HC koncový bod.</span><span class="sxs-lookup"><span data-stu-id="0e88e-151">The process works like this: each microservice exposes the endpoint /hc.</span></span> <span data-ttu-id="0e88e-152">Vytvoří tohoto koncového bodu se HealthChecks knihovny ASP.NET Core middleware.</span><span class="sxs-lookup"><span data-stu-id="0e88e-152">That endpoint is created by the HealthChecks library ASP.NET Core middleware.</span></span> <span data-ttu-id="0e88e-153">Po vyvolání tohoto koncového bodu spustí všechny kontroly stavu, které jsou nakonfigurované v metodě AddHealthChecks ve třídě spuštění.</span><span class="sxs-lookup"><span data-stu-id="0e88e-153">When that endpoint is invoked, it runs all the health checks that are configured in the AddHealthChecks method in the Startup class.</span></span>

<span data-ttu-id="0e88e-154">Metoda UseHealthChecks očekává, že port nebo cestu.</span><span class="sxs-lookup"><span data-stu-id="0e88e-154">The UseHealthChecks method expects a port or a path.</span></span> <span data-ttu-id="0e88e-155">Tento port nebo cesta je koncový bod pomocí zkontrolovat stav služby.</span><span class="sxs-lookup"><span data-stu-id="0e88e-155">That port or path is the endpoint to use to check the health state of the service.</span></span> <span data-ttu-id="0e88e-156">Mikroslužbu katalogu pro instanci používá HC cestu.</span><span class="sxs-lookup"><span data-stu-id="0e88e-156">For instance, the catalog microservice uses the path /hc.</span></span>

### <a name="caching-health-check-responses"></a><span data-ttu-id="0e88e-157">Ukládání do mezipaměti odpovědi kontroly stavu</span><span class="sxs-lookup"><span data-stu-id="0e88e-157">Caching health check responses</span></span>

<span data-ttu-id="0e88e-158">Vzhledem k tomu, že nechcete způsobit odepření služby (DoS) v službách nebo jednoduše není chcete dopad na výkon služby kontrolou prostředky příliš často, můžete se vrátí do mezipaměti a nakonfigurovat trvání mezipaměti pro každý kontrolu stavu.</span><span class="sxs-lookup"><span data-stu-id="0e88e-158">Since you do not want to cause a Denial of Service (DoS) in your services, or you simply do not want to impact service performance by checking resources too frequently, you can cache the returns and configure a cache duration for each health check.</span></span>

<span data-ttu-id="0e88e-159">Ve výchozím nastavení Doba uložení do mezipaměti interně nastavena na 5 minut, ale můžete změnit dobu trvání této mezipaměti na každou kontrolou stavu, jako v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="0e88e-159">By default, the cache duration is internally set to 5 minutes, but you can change that cache duration on each health check, as in the following code:</span></span>

```csharp
checks.AddUrlCheck(Configuration["CatalogUrl"],1); // 1 min as cache duration
```

### <a name="querying-your-microservices-to-report-about-their-health-status"></a><span data-ttu-id="0e88e-160">Dotazování vaší mikroslužeb na zprávu o jejich stav</span><span class="sxs-lookup"><span data-stu-id="0e88e-160">Querying your microservices to report about their health status</span></span>

<span data-ttu-id="0e88e-161">Pokud jste nakonfigurovali kontroly stavu podle postupu popsaného tady, jakmile mikroslužbu běží v Docker, můžete přímo zkontrolovat z prohlížeče pokud je v pořádku.</span><span class="sxs-lookup"><span data-stu-id="0e88e-161">When you have configured health checks as described here, once the microservice is running in Docker, you can directly check from a browser if it is healthy.</span></span> <span data-ttu-id="0e88e-162">(To vyžadovat, že publikujete port kontejneru mimo Docker hostitele, dostanete kontejneru prostřednictvím místního hostitele nebo externí IP hostitelů Docker.) Obrázek 10-7 zobrazuje v prohlížeči a odpovídající reakce žádost.</span><span class="sxs-lookup"><span data-stu-id="0e88e-162">(This does require that you are publishing the container port out of the Docker host, so you can access the container through localhost or through the external Docker host IP.) Figure 10-7 shows a request in a browser and the corresponding response.</span></span>

![](./media/image7.png)

<span data-ttu-id="0e88e-163">**Obrázek 10-7**.</span><span class="sxs-lookup"><span data-stu-id="0e88e-163">**Figure 10-7**.</span></span> <span data-ttu-id="0e88e-164">Kontroluje stav služby jednoho z prohlížeče</span><span class="sxs-lookup"><span data-stu-id="0e88e-164">Checking health status of a single service from a browser</span></span>

<span data-ttu-id="0e88e-165">V testu uvidíte, že je v pořádku, mikroslužbu catalog.api (spuštěn na portu 5101) vrací informace o stavu a stav protokolu HTTP 200 ve formátu JSON.</span><span class="sxs-lookup"><span data-stu-id="0e88e-165">In that test, you can see that the catalog.api microservice (running on port 5101) is healthy, returning HTTP status 200 and status information in JSON.</span></span> <span data-ttu-id="0e88e-166">Také znamená, že interně službu také zkontrolovat stav jeho závislost databáze systému SQL Server a že kontrola stavu se samo označuje jako v pořádku.</span><span class="sxs-lookup"><span data-stu-id="0e88e-166">It also means that internally the service also checked the health of its SQL Server database dependency and that health check was reported itself as healthy.</span></span>

## <a name="using-watchdogs"></a><span data-ttu-id="0e88e-167">Pomocí watchdogs</span><span class="sxs-lookup"><span data-stu-id="0e88e-167">Using watchdogs</span></span>

<span data-ttu-id="0e88e-168">Sledovací zařízení je samostatný služba, která může sledovat stav a zatížení v rámci služeb a stavu sestavy o mikroslužeb dotazováním s knihovnou HealthChecks zavedená dříve.</span><span class="sxs-lookup"><span data-stu-id="0e88e-168">A watchdog is a separate service that can watch health and load across services, and report health about the microservices by querying with the HealthChecks library introduced earlier.</span></span> <span data-ttu-id="0e88e-169">To může pomoct zabránit chybám, které by se na základě zobrazení jedné služby.</span><span class="sxs-lookup"><span data-stu-id="0e88e-169">This can help prevent errors that would not be detected based on the view of a single service.</span></span> <span data-ttu-id="0e88e-170">Watchdogs jsou také vhodné místo pro hostitele kód, který můžete provést nápravné akce pro známé podmínky bez zásahu uživatele.</span><span class="sxs-lookup"><span data-stu-id="0e88e-170">Watchdogs also are a good place to host code that can perform remediation actions for known conditions without user interaction.</span></span>

<span data-ttu-id="0e88e-171">Ukázka eShopOnContainers obsahuje webové stránky, která zobrazuje vzorové sestavy kontrolu stavu, jak ukazuje obrázek 10-8.</span><span class="sxs-lookup"><span data-stu-id="0e88e-171">The eShopOnContainers sample contains a web page that displays sample health check reports, as shown in Figure 10-8.</span></span> <span data-ttu-id="0e88e-172">Toto je nejjednodušší sledovací zařízení můžete mít, protože všechny dělá jsou ukazuje stav mikroslužeb a webové aplikace v eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="0e88e-172">This is the simplest watchdog you could have, since all it does is shows the state of the microservices and web applications in eShopOnContainers.</span></span> <span data-ttu-id="0e88e-173">Sledovací zařízení obvykle také provede akce, když zjistí stavy není v pořádku.</span><span class="sxs-lookup"><span data-stu-id="0e88e-173">Usually a watchdog also takes actions when it detects unhealthy states.</span></span>

![](./media/image8.png)

<span data-ttu-id="0e88e-174">**Obrázek 10-8**.</span><span class="sxs-lookup"><span data-stu-id="0e88e-174">**Figure 10-8**.</span></span> <span data-ttu-id="0e88e-175">Ukázková sestava kontroly stavu v eShopOnContainers</span><span class="sxs-lookup"><span data-stu-id="0e88e-175">Sample health check report in eShopOnContainers</span></span>

<span data-ttu-id="0e88e-176">V souhrnu poskytuje middleware ASP.NET knihovny ASP.NET Core HealthChecks kontrola koncový bod jednoho stavu pro každý mikroslužby.</span><span class="sxs-lookup"><span data-stu-id="0e88e-176">In summary, the ASP.NET middleware of the ASP.NET Core HealthChecks library provides a single health check endpoint for each microservice.</span></span> <span data-ttu-id="0e88e-177">Tato akce provést kontroly stavu definované v něm a vrátit celkového přehledu o stavu v závislosti na všechny tyto kontroly.</span><span class="sxs-lookup"><span data-stu-id="0e88e-177">This will execute all the health checks defined within it and return an overall health state depending on all those checks.</span></span>

<span data-ttu-id="0e88e-178">Knihovna HealthChecks je rozšiřitelný prostřednictvím nové kontroly stavu budoucí externích zdrojů.</span><span class="sxs-lookup"><span data-stu-id="0e88e-178">The HealthChecks library is extensible through new health checks of future external resources.</span></span> <span data-ttu-id="0e88e-179">Například Očekáváme, že v budoucnosti knihovny bude mít kontroly stavu pro Redis cache a pro jiné databáze.</span><span class="sxs-lookup"><span data-stu-id="0e88e-179">For example, we expect that in the future the library will have health checks for Redis cache and for other databases.</span></span> <span data-ttu-id="0e88e-180">Knihovny umožňuje stavu hlášení více závislostí služby nebo aplikace, a můžete pak proveďte akce založené na těchto kontroly stavu.</span><span class="sxs-lookup"><span data-stu-id="0e88e-180">The library allows health reporting by multiple service or application dependencies, and you can then take actions based on those health checks.</span></span>

## <a name="health-checks-when-using-orchestrators"></a><span data-ttu-id="0e88e-181">Kontroly stavu při použití orchestrators</span><span class="sxs-lookup"><span data-stu-id="0e88e-181">Health checks when using orchestrators</span></span>

<span data-ttu-id="0e88e-182">Ke sledování dostupnosti vaší mikroslužeb, orchestrators jako Docker Swarm, Kubernetes a Service Fabric pravidelně provádět kontroly stavu pomocí zasílání požadavků na test mikroslužeb.</span><span class="sxs-lookup"><span data-stu-id="0e88e-182">To monitor the availability of your microservices, orchestrators like Docker Swarm, Kubernetes, and Service Fabric periodically perform health checks by sending requests to test the microservices.</span></span> <span data-ttu-id="0e88e-183">Když orchestrator zjistí, že služba nebo kontejner není v pořádku, že zastaví směrování požadavků do této instance.</span><span class="sxs-lookup"><span data-stu-id="0e88e-183">When an orchestrator determines that a service/container is unhealthy, it stops routing requests to that instance.</span></span> <span data-ttu-id="0e88e-184">Také obvykle vytvoří novou instanci tohoto kontejneru.</span><span class="sxs-lookup"><span data-stu-id="0e88e-184">It also usually creates a new instance of that container.</span></span>

<span data-ttu-id="0e88e-185">Většina orchestrators pro instanci, můžete použít kontroly stavu pro správu nasazení nula. výpadků.</span><span class="sxs-lookup"><span data-stu-id="0e88e-185">For instance, most orchestrators can use health checks to manage zero-downtime deployments.</span></span> <span data-ttu-id="0e88e-186">Pouze v případě, že bude stav kontejneru služby nebo změny pořádku orchestrator spustit směrování provozu do kontejneru služby nebo instancí.</span><span class="sxs-lookup"><span data-stu-id="0e88e-186">Only when the status of a service/container changes to healthy will the orchestrator start routing traffic to service/container instances.</span></span>

<span data-ttu-id="0e88e-187">Sledování stavu je obzvláště důležité, když orchestrator provádí upgrade aplikace.</span><span class="sxs-lookup"><span data-stu-id="0e88e-187">Health monitoring is especially important when an orchestrator performs an application upgrade.</span></span> <span data-ttu-id="0e88e-188">Některé orchestrators (např. Azure Service Fabric) aktualizujte služby v fáze – například může aktualizovat jeden pátý povrchu clusteru pro každý upgradu aplikace.</span><span class="sxs-lookup"><span data-stu-id="0e88e-188">Some orchestrators (like Azure Service Fabric) update services in phases—for example, they might update one-fifth of the cluster surface for each application upgrade.</span></span> <span data-ttu-id="0e88e-189">Sada uzlů, která se upgraduje současně se označuje jako *upgradovací doméně*.</span><span class="sxs-lookup"><span data-stu-id="0e88e-189">The set of nodes that is upgraded at the same time is referred to as an *upgrade domain*.</span></span> <span data-ttu-id="0e88e-190">Po každé upgradované domény byl upgradován a je k dispozici pro uživatele, že upgradovací doméně musí projít kontroly stavu, než nasazení přikročí k další upgradovací doméně.</span><span class="sxs-lookup"><span data-stu-id="0e88e-190">After each upgrade domain has been upgraded and is available to users, that upgrade domain must pass health checks before the deployment moves to the next upgrade domain.</span></span>

<span data-ttu-id="0e88e-191">Další aspekt stav služby je generování sestav metriky ze služby.</span><span class="sxs-lookup"><span data-stu-id="0e88e-191">Another aspect of service health is reporting metrics from the service.</span></span> <span data-ttu-id="0e88e-192">Toto je jednou z upřesňujících možností stavu modelu některé orchestrators, jako je Service Fabric.</span><span class="sxs-lookup"><span data-stu-id="0e88e-192">This is an advanced capability of the health model of some orchestrators, like Service Fabric.</span></span> <span data-ttu-id="0e88e-193">Metriky jsou důležité při použití orchestrator, protože se používají k vyrovnávání využití prostředků.</span><span class="sxs-lookup"><span data-stu-id="0e88e-193">Metrics are important when using an orchestrator because they are used to balance resource usage.</span></span> <span data-ttu-id="0e88e-194">Metriky taky může být indikátor stavu systému.</span><span class="sxs-lookup"><span data-stu-id="0e88e-194">Metrics also can be an indicator of system health.</span></span> <span data-ttu-id="0e88e-195">Například můžete mít aplikace, která má mnoho mikroslužeb a každá instance sestavy metrika požadavků za sekundu (RPS).</span><span class="sxs-lookup"><span data-stu-id="0e88e-195">For example, you might have an application that has many microservices, and each instance reports a requests-per-second (RPS) metric.</span></span> <span data-ttu-id="0e88e-196">Pokud se jedna služba používá více prostředků (paměť, procesor atd.) než jiné službě, orchestrator může pohyb instance služby v clusteru, a pokuste se udržovat i využití prostředků.</span><span class="sxs-lookup"><span data-stu-id="0e88e-196">If one service is using more resources (memory, processor, etc.) than another service, the orchestrator could move service instances around in the cluster to try to maintain even resource utilization.</span></span>

<span data-ttu-id="0e88e-197">Všimněte si, že pokud používáte Azure Service Fabric, poskytuje svou vlastní [sledování stavu modelu](https://docs.microsoft.com/azure/service-fabric/service-fabric-health-introduction), což je pokročilejší než kontroly stavu jednoduché.</span><span class="sxs-lookup"><span data-stu-id="0e88e-197">Note that if you are using Azure Service Fabric, it provides its own [Health Monitoring model](https://docs.microsoft.com/azure/service-fabric/service-fabric-health-introduction), which is more advanced than simple health checks.</span></span>

## <a name="advanced-monitoring-visualization-analysis-and-alerts"></a><span data-ttu-id="0e88e-198">Rozšířené monitorování: vizualizace, analýzu a výstrahy</span><span class="sxs-lookup"><span data-stu-id="0e88e-198">Advanced monitoring: visualization, analysis, and alerts</span></span>

<span data-ttu-id="0e88e-199">Poslední část monitorování je vizualizace proudu událostí, zprávy o výkonu služby a výstrahy, když se zjistí problém.</span><span class="sxs-lookup"><span data-stu-id="0e88e-199">The final part of monitoring is visualizing the event stream, reporting on service performance, and alerting when an issue is detected.</span></span> <span data-ttu-id="0e88e-200">Různá řešení můžete použít pro tento aspekt monitorování.</span><span class="sxs-lookup"><span data-stu-id="0e88e-200">You can use different solutions for this aspect of monitoring.</span></span>

<span data-ttu-id="0e88e-201">Můžete použít jednoduchý vlastních aplikací zobrazující stavu vašich služeb, jako jsou vlastní stránky jsme vám ukázal, když jsme vysvětlené [ASP.NET Core HealthChecks](https://github.com/aspnet/HealthChecks).</span><span class="sxs-lookup"><span data-stu-id="0e88e-201">You can use simple custom applications showing the state of your services, like the custom page we showed when we explained [ASP.NET Core HealthChecks](https://github.com/aspnet/HealthChecks).</span></span> <span data-ttu-id="0e88e-202">Nebo můžete použít pokročilejší nástroje, například Azure Application Insights a Operations Management Suite budou generovány výstrahy založené na události datového proudu.</span><span class="sxs-lookup"><span data-stu-id="0e88e-202">Or you could use more advanced tools like Azure Application Insights and Operations Management Suite to raise alerts based on the stream of events.</span></span>

<span data-ttu-id="0e88e-203">Nakonec pokud byly ukládání všech datových proudů událostí, můžete Microsoft Power BI nebo řešení třetí strany, jako je Kibana nebo Splunk můžete znázorňovat data.</span><span class="sxs-lookup"><span data-stu-id="0e88e-203">Finally, if you were storing all the event streams, you can use Microsoft Power BI or a third-party solution like Kibana or Splunk to visualize the data.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="0e88e-204">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="0e88e-204">Additional resources</span></span>

-   <span data-ttu-id="0e88e-205">**ASP.NET Core HealthChecks** (předběžnou verzi) [ *https://github.com/aspnet/HealthChecks/*](https://github.com/aspnet/HealthChecks/)</span><span class="sxs-lookup"><span data-stu-id="0e88e-205">**ASP.NET Core HealthChecks** (early release) [*https://github.com/aspnet/HealthChecks/*](https://github.com/aspnet/HealthChecks/)</span></span>

-   <span data-ttu-id="0e88e-206">**Úvod do monitorování stavu Service Fabric**
    [*https://docs.microsoft.com/azure/service-fabric/service-fabric-health-introduction*](https://docs.microsoft.com/azure/service-fabric/service-fabric-health-introduction)</span><span class="sxs-lookup"><span data-stu-id="0e88e-206">**Introduction to Service Fabric health monitoring**
[*https://docs.microsoft.com/azure/service-fabric/service-fabric-health-introduction*](https://docs.microsoft.com/azure/service-fabric/service-fabric-health-introduction)</span></span>

-   <span data-ttu-id="0e88e-207">**Azure Application Insights**
    [*https://azure.microsoft.com/services/application-insights/*](https://azure.microsoft.com/services/application-insights/)</span><span class="sxs-lookup"><span data-stu-id="0e88e-207">**Azure Application Insights**
[*https://azure.microsoft.com/services/application-insights/*](https://azure.microsoft.com/services/application-insights/)</span></span>

-   <span data-ttu-id="0e88e-208">**Microsoft Operations Management Suite**
    [*https://www.microsoft.com/en-us/cloud-platform/operations-management-suite*](https://www.microsoft.com/en-us/cloud-platform/operations-management-suite)</span><span class="sxs-lookup"><span data-stu-id="0e88e-208">**Microsoft Operations Management Suite**
[*https://www.microsoft.com/en-us/cloud-platform/operations-management-suite*](https://www.microsoft.com/en-us/cloud-platform/operations-management-suite)</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="0e88e-209">[Předchozí] (implementace okruh dělení pattern.md) [Další] (.. /Secure-NET-microservices-Web-Applications/index.MD)</span><span class="sxs-lookup"><span data-stu-id="0e88e-209">[Previous] (implement-circuit-breaker-pattern.md) [Next] (../secure-net-microservices-web-applications/index.md)</span></span>
