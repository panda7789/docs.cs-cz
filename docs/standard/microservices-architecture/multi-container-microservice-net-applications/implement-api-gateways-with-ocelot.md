---
title: Implementace bran rozhraní API s Ocelotem
description: Zjistěte, jak implementovat brány rozhraní API s Ocelot a použití Ocelot v prostředí založené na kontejnerech.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/02/2018
ms.openlocfilehash: 5d4f2a3b2551f8da83359b26578d45559721f7df
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61776368"
---
# <a name="implement-api-gateways-with-ocelot"></a><span data-ttu-id="bd36c-103">Implementace brány rozhraní API s Ocelot</span><span class="sxs-lookup"><span data-stu-id="bd36c-103">Implement API Gateways with Ocelot</span></span>

<span data-ttu-id="bd36c-104">Aplikace mikroslužeb odkaz [aplikaci eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) používá [Ocelot](https://github.com/ThreeMammals/Ocelot), jednoduchý a jednoduchý bránu rozhraní API, která můžete nasadit kdekoli spolu s mikroslužby a kontejnery, jako například v kterákoli z následujících prostředích používají aplikaci eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="bd36c-104">The reference microservice application [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) is using [Ocelot](https://github.com/ThreeMammals/Ocelot), a simple and lightweight API Gateway that you can deploy anywhere along with your microservices/containers, such as in any of the following environments used by eShopOnContainers.</span></span>

- <span data-ttu-id="bd36c-105">Hostitele docker, do vašeho místního vývojového počítače, v místním nebo v cloudu.</span><span class="sxs-lookup"><span data-stu-id="bd36c-105">Docker host, in your local dev PC, on-premises or in the cloud.</span></span>
- <span data-ttu-id="bd36c-106">Kubernetes cluster, místní nebo v cloudu spravované jako je Azure Kubernetes Service (AKS).</span><span class="sxs-lookup"><span data-stu-id="bd36c-106">Kubernetes cluster, on-premises or in managed cloud such as Azure Kubernetes Service (AKS).</span></span>
- <span data-ttu-id="bd36c-107">Cluster Service Fabric, místní nebo v cloudu.</span><span class="sxs-lookup"><span data-stu-id="bd36c-107">Service Fabric cluster, on-premises or in the cloud.</span></span>
- <span data-ttu-id="bd36c-108">Service Fabric sítě jako PaaS a bez serveru v Azure.</span><span class="sxs-lookup"><span data-stu-id="bd36c-108">Service Fabric mesh, as PaaS/Serverless in Azure.</span></span>

## <a name="architect-and-design-your-api-gateways"></a><span data-ttu-id="bd36c-109">Architektury a návrhu vaší brány rozhraní API</span><span class="sxs-lookup"><span data-stu-id="bd36c-109">Architect and design your API Gateways</span></span>

<span data-ttu-id="bd36c-110">Následující diagram architektury ukazuje, jak se implementují brány rozhraní API s Ocelot v aplikaci eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="bd36c-110">The following architecture diagram shows how API Gateways are implemented with Ocelot in eShopOnContainers.</span></span>

![diagram architektury aplikaci eShopOnContainers zobrazující klientské aplikace, mikroslužby a brány rozhraní API mezi](./media/image28.png)

<span data-ttu-id="bd36c-112">**Obrázek 6 – 28**.</span><span class="sxs-lookup"><span data-stu-id="bd36c-112">**Figure 6-28**.</span></span> <span data-ttu-id="bd36c-113">aplikaci eShopOnContainers architektury s využitím brány rozhraní API</span><span class="sxs-lookup"><span data-stu-id="bd36c-113">eShopOnContainers architecture with API Gateways</span></span>

<span data-ttu-id="bd36c-114">Tento diagram znázorňuje, jak celá aplikace je nasazená do jednoho hostitele Docker nebo vývojové počítače s "Docker pro Windows" nebo "Dockeru pro Mac".</span><span class="sxs-lookup"><span data-stu-id="bd36c-114">That diagram shows how the whole application is deployed into a single Docker host or development PC with “Docker for Windows” or “Docker for Mac”.</span></span> <span data-ttu-id="bd36c-115">Nasazení do jakékoli produktu orchestrator by hodně podobné ale žádný kontejner ve diagram může být horizontálním navýšením kapacity v nástroji orchestrator.</span><span class="sxs-lookup"><span data-stu-id="bd36c-115">However, deploying into any orchestrator would be pretty similar but any container in the diagram could be scaled-out in the orchestrator.</span></span>

<span data-ttu-id="bd36c-116">Kromě toho prostředky infrastruktury, jako jsou databáze, mezipaměť a zprostředkovatele zpráv by měl být se sníženou zátěží z orchestrator a nasadí do vysoce dostupné systémy pro infrastrukturu, jako je Azure SQL Database, Azure Cosmos DB, Azure redis cache, Azure Service Bus nebo jakékoli HA clustering řešení místní.</span><span class="sxs-lookup"><span data-stu-id="bd36c-116">In addition, the infrastructure assets such as databases, cache, and message brokers should be offloaded from the orchestrator and deployed into high available systems for infrastructure, like Azure SQL Database, Azure Cosmos DB, Azure Redis, Azure Service Bus, or any HA clustering solution on-premises.</span></span>

<span data-ttu-id="bd36c-117">Jak vám může také Všimněte si, že v diagramu, s několika brány rozhraní API umožňuje několika vývojovým týmům autonomní (v tomto případě marketingové funkcí vs. Nákupní funkce) při vývoji a nasazování mikroslužeb jejich plus své vlastní brány související rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="bd36c-117">As you can also notice in the diagram, having several API Gateways allows multiple development teams to be autonomous (in this case Marketing features vs. Shopping features) when developing and deploying their microservices plus their own related API Gateways.</span></span>

<span data-ttu-id="bd36c-118">Pokud jste měli jedné monolitické rozhraní API brány, který by znamenal jediný bod aktualizovat několik vývojové týmy, které by mohly spojit všechny mikroslužby s jednou částí aplikace.</span><span class="sxs-lookup"><span data-stu-id="bd36c-118">If you had a single monolithic API Gateway that would mean a single point to be updated by several development teams, which could couple all the microservices with a single part of the application.</span></span>

<span data-ttu-id="bd36c-119">Mnohem víc do toho pustit v návrhu, někdy podrobných Brána rozhraní API může být také omezená na jednu obchodní mikroslužeb v závislosti na zvolené architektury.</span><span class="sxs-lookup"><span data-stu-id="bd36c-119">Going much further in the design, sometimes a fine-grained API Gateway can also be limited to a single business microservice depending on the chosen architecture.</span></span> <span data-ttu-id="bd36c-120">Brána rozhraní API hranice závisí firmy nebo domény s vám pomůže získat lepší návrh.</span><span class="sxs-lookup"><span data-stu-id="bd36c-120">Having the API Gateway’s boundaries dictated by the business or domain will help you to get a better design.</span></span>

<span data-ttu-id="bd36c-121">Jemnou rozlišovací schopnost na úrovni rozhraní API brány, může být užitečné zejména pro pokročilejší kompozitních aplikací uživatelského rozhraní, které jsou založené na mikroslužbách, protože koncept podrobných Brána rozhraní API se podobá službě kompozici uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="bd36c-121">For instance, fine granularity in the API Gateway tier can be especially useful for more advanced composite UI applications that are based on microservices, because the concept of a fine-grained API Gateway is similar to a UI composition service.</span></span>

<span data-ttu-id="bd36c-122">Jsme delve do další podrobnosti najdete v předchozí části [vytvoření složeného uživatelského rozhraní založeného na mikroslužbách](../architect-microservice-container-applications/microservice-based-composite-ui-shape-layout.md).</span><span class="sxs-lookup"><span data-stu-id="bd36c-122">We delve into more details in the previous section [Creating composite UI based on microservices](../architect-microservice-container-applications/microservice-based-composite-ui-shape-layout.md).</span></span>

<span data-ttu-id="bd36c-123">Jako hlavní, co vyplývá, pro mnoho aplikací střední a velké velikosti pomocí vlastními silami sestavených Brána rozhraní API produktu je obvykle dobrý nápad, ale ne jako jeden agregátor monolitické nebo jedinečné centrální vlastní bránu rozhraní API není-li tuto bránu rozhraní API umožňuje více nezávislých Konfigurace oblasti pro několik vývojové týmy vytváření autonomní mikroslužeb.</span><span class="sxs-lookup"><span data-stu-id="bd36c-123">As key takeaway, for many medium- and large-size applications, using a custom-built API Gateway product is usually a good approach, but not as a single monolithic aggregator or unique central custom API Gateway unless that API Gateway allows multiple independent configuration areas for the several development teams creating autonomous microservices.</span></span>

### <a name="sample-microservicescontainers-to-re-route-through-the-api-gateways"></a><span data-ttu-id="bd36c-124">Ukázka mikroslužeb a kontejnerů znovu směrování prostřednictvím brány rozhraní API</span><span class="sxs-lookup"><span data-stu-id="bd36c-124">Sample microservices/containers to re-route through the API Gateways</span></span>

<span data-ttu-id="bd36c-125">Jako příklad aplikaci eShopOnContainers má přibližně šest interní mikroslužeb – typy, které mají zveřejnit prostřednictvím brány rozhraní API, jak je znázorněno na následujícím obrázku.</span><span class="sxs-lookup"><span data-stu-id="bd36c-125">As an example, eShopOnContainers has around six internal microservice-types that have to be published through the API Gateways, as shown in the following image.</span></span>

![Pouze nákupní košík, katalog, umístění, Marketing, řazení a platby mikroslužeb jsou publikované prostřednictvím brány rozhraní API.](./media/image29.png)

<span data-ttu-id="bd36c-127">**Obrázek 6 – 29**.</span><span class="sxs-lookup"><span data-stu-id="bd36c-127">**Figure 6-29**.</span></span> <span data-ttu-id="bd36c-128">Mikroslužby složek v aplikaci eShopOnContainers řešení v sadě Visual Studio</span><span class="sxs-lookup"><span data-stu-id="bd36c-128">Microservice folders in eShopOnContainers solution in Visual Studio</span></span>

<span data-ttu-id="bd36c-129">O službě Identity v návrhu je ponecháno ze Brána rozhraní API, směrování, protože se jedná pouze problém vyskytující v systému, i Ocelot je taky možné zahrnout jako součást přesměrování seznamy.</span><span class="sxs-lookup"><span data-stu-id="bd36c-129">About the Identity service, in the design it's left out of the API Gateway routing because it's the only cross-cutting concern in the system, although with Ocelot it's also possible to include it as part of the rerouting lists.</span></span>

<span data-ttu-id="bd36c-130">Všechny tyto služby jsou aktuálně implementováno jako služby webového rozhraní API ASP.NET Core, jak vidíte z kódu.</span><span class="sxs-lookup"><span data-stu-id="bd36c-130">All those services are currently implemented as ASP.NET Core Web API services, as you can tell from the code.</span></span> <span data-ttu-id="bd36c-131">Zaměřme se na jednu z mikroslužeb, jako je kód mikroslužeb katalogu.</span><span class="sxs-lookup"><span data-stu-id="bd36c-131">Let’s focus on one of the microservices like the Catalog microservice code.</span></span>

![Zobrazení Průzkumníka řešení Catalog.API projektu.](./media/image30.png)

<span data-ttu-id="bd36c-133">**Obrázek 6 – 30**.</span><span class="sxs-lookup"><span data-stu-id="bd36c-133">**Figure 6-30**.</span></span> <span data-ttu-id="bd36c-134">Ukázka webového rozhraní API mikroslužby (katalogu mikroslužeb)</span><span class="sxs-lookup"><span data-stu-id="bd36c-134">Sample Web API microservice (Catalog microservice)</span></span>

<span data-ttu-id="bd36c-135">Uvidíte, že katalog mikroslužba je obvyklou pro projekty webového rozhraní API ASP.NET Core s několika řadičů a metod, jako jsou v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="bd36c-135">You can see that the Catalog microservice is a typical ASP.NET Core Web API project with several controllers and methods like in the following code.</span></span>

```csharp
[HttpGet]
[Route("items/{id:int}")]
[ProducesResponseType((int)HttpStatusCode.BadRequest)]
[ProducesResponseType((int)HttpStatusCode.NotFound)]
[ProducesResponseType(typeof(CatalogItem),(int)HttpStatusCode.OK)]
public async Task<IActionResult> GetItemById(int id)
{
    if (id <= 0)
    {
        return BadRequest();
    }
    var item = await _catalogContext.CatalogItems.
                                          SingleOrDefaultAsync(ci => ci.Id == id);
    //…

    if (item != null)
    {
        return Ok(item);
    }
    return NotFound();
}
```

<span data-ttu-id="bd36c-136">Požadavek protokolu HTTP bude uplatněna, který druh C# kód přístup k databázi mikroslužby a další požadované akce.</span><span class="sxs-lookup"><span data-stu-id="bd36c-136">The HTTP request will end up running that kind of C# code accessing the microservice database and any additional required action.</span></span>

<span data-ttu-id="bd36c-137">Týkající se adresy URL mikroslužeb při kontejnery se nasazují do vašeho místního vývojového počítače (místního hostitele Dockeru), jednotlivých mikroslužeb kontejner má vždy interní port (obvykle port 80) zadaný v jeho souboru dockerfile, stejně jako v následujícím souboru dockerfile:</span><span class="sxs-lookup"><span data-stu-id="bd36c-137">Regarding the microservice URL, when the containers are deployed in your local development PC (local Docker host), each microservice’s container has always an internal port (usually port 80) specified in its dockerfile, as in the following dockerfile:</span></span>

```Dockerfile
FROM microsoft/aspnetcore:2.0.5 AS base
WORKDIR /app
EXPOSE 80
```

<span data-ttu-id="bd36c-138">Port 80, které jsou uvedené v kódu je interní v rámci hostitele Docker, takže nemůže být dosažitelný podle klientské aplikace.</span><span class="sxs-lookup"><span data-stu-id="bd36c-138">The port 80 shown in the code is internal within the Docker host, so it can't be reached by client apps.</span></span>

<span data-ttu-id="bd36c-139">Klientské aplikace můžou přistupovat k pouze externí porty (pokud existuje) publikované při nasazování s `docker-compose`.</span><span class="sxs-lookup"><span data-stu-id="bd36c-139">Client apps can access only the external ports (if any) published when deploying with `docker-compose`.</span></span>

<span data-ttu-id="bd36c-140">Tyto externí porty nemůže být publikována při nasazení do produkčního prostředí.</span><span class="sxs-lookup"><span data-stu-id="bd36c-140">Those external ports shouldn't be published when deploying to a production environment.</span></span> <span data-ttu-id="bd36c-141">To je přesně proč chcete použít bránu rozhraní API, aby se zabránilo přímou komunikaci mezi klientské aplikace a mikroslužeb.</span><span class="sxs-lookup"><span data-stu-id="bd36c-141">This is precisely why you want to use the API Gateway, to avoid the direct communication between the client apps and the microservices.</span></span>

<span data-ttu-id="bd36c-142">Ale při vývoji, chcete získat přímo přístup k mikroslužeb a kontejnerů a spusťte ho pomocí Swaggeru.</span><span class="sxs-lookup"><span data-stu-id="bd36c-142">However, when developing, you want to access the microservice/container directly and run it through Swagger.</span></span> <span data-ttu-id="bd36c-143">To je důvod, proč v aplikaci eShopOnContainers, externích portů jsou stále zadat i v případě, že se nebude používat bránu rozhraní API nebo klientských aplikací.</span><span class="sxs-lookup"><span data-stu-id="bd36c-143">That’s why in eShopOnContainers, the external ports are still specified even when they won’t be used by the API Gateway or the client apps.</span></span>

<span data-ttu-id="bd36c-144">Tady je příklad `docker-compose.override.yml` soubor pro mikroslužby katalogu:</span><span class="sxs-lookup"><span data-stu-id="bd36c-144">Here’s an example of the `docker-compose.override.yml` file for the Catalog microservice:</span></span>

```yml
catalog.api:
  environment:
    - ASPNETCORE_ENVIRONMENT=Development
    - ASPNETCORE_URLS=http://0.0.0.0:80
    - ConnectionString=YOUR_VALUE
    - ... Other Environment Variables
  ports:
    - "5101:80"   # Important: In a production environment you should remove the external port (5101) kept here for microservice debugging purposes.
                  # The API Gateway redirects and access through the internal port (80).
```

<span data-ttu-id="bd36c-145">Uvidíte jak v konfiguraci docker-compose.override.yml interní port kontejneru katalogu je port 80, ale 5101 je port pro externí přístup.</span><span class="sxs-lookup"><span data-stu-id="bd36c-145">You can see how in the docker-compose.override.yml configuration the internal port for the Catalog container is port 80, but the port for external access is 5101.</span></span> <span data-ttu-id="bd36c-146">By ale neměly používat tento port aplikace při použití brány rozhraní API pouze pro ladění, spouštění a testování pouze mikroslužeb katalogu.</span><span class="sxs-lookup"><span data-stu-id="bd36c-146">But this port shouldn’t be used by the application when using an API Gateway, only to debug, run and test just the Catalog microservice.</span></span>

<span data-ttu-id="bd36c-147">Za normálních okolností bude nasazení pomocí docker-compose do provozního prostředí vzhledem k tomu, že provozním prostředí nasazení mikroslužeb je orchestrátor Kubernetes nebo Service Fabric.</span><span class="sxs-lookup"><span data-stu-id="bd36c-147">Normally, you won’t be deploying with docker-compose into a production environment because the right production deployment environment for microservices is an orchestrator like Kubernetes or Service Fabric.</span></span> <span data-ttu-id="bd36c-148">Při nasazování do těchto prostředí použijete jiný konfigurační soubory, pokud nebude publikovat přímo všechny externí port pro mikroslužby ale budete vždy použít reverzní proxy server ze Brána rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="bd36c-148">When deploying to those environments you use different configuration files where you won’t publish directly any external port for the microservices but, you'll always use the reverse proxy from the API Gateway.</span></span>

<span data-ttu-id="bd36c-149">Spustit mikroslužeb katalogu v místního hostitele Docker buď spuštěním řešení úplnou aplikaci eShopOnContainers ze sady Visual Studio (spouští se všechny služby v dockeru-compose soubory) nebo právě spouští mikroslužeb katalogu s následujícím docker-compose příkaz do příkazového řádku nebo Powershellu, které jsou umístěné ve složce kde `docker-compose.yml` a jsou umístěny docker-compose.override.yml.</span><span class="sxs-lookup"><span data-stu-id="bd36c-149">Run the catalog microservice in your local Docker host either by running the full eShopOnContainers solution from Visual Studio (it’ll run all the services in the docker-compose files) or just starting the Catalog microservice with the following docker-compose command in CMD or PowerShell positioned at the folder where the `docker-compose.yml` and docker-compose.override.yml are placed.</span></span>

```console
docker-compose run --service-ports catalog.api
```

<span data-ttu-id="bd36c-150">Tento příkaz spustí jenom v kontejneru služby catalog.api plus závislosti, které jsou určené v docker-compose.yml.</span><span class="sxs-lookup"><span data-stu-id="bd36c-150">This command only runs the catalog.api service container plus dependencies that are specified in the docker-compose.yml.</span></span> <span data-ttu-id="bd36c-151">V takovém kontejner SQL serveru a RabbitMQ kontejneru.</span><span class="sxs-lookup"><span data-stu-id="bd36c-151">In this case, the SQL Server container and RabbitMQ container.</span></span>

<span data-ttu-id="bd36c-152">Potom můžete přímo přístup ke katalogu mikroslužeb a zobrazit její metody prostřednictvím uživatelského rozhraní Swagger, že "externí" port, v tomto případě přístup přímo prostřednictvím k `http://localhost:5101/swagger`:</span><span class="sxs-lookup"><span data-stu-id="bd36c-152">Then, you can directly access the Catalog microservice and see its methods through the Swagger UI accessing directly through that “external” port, in this case `http://localhost:5101/swagger`:</span></span>

![Zobrazit v prohlížeči věku uživatelské rozhraní Swagger pro rozhraní REST API Catalog.API.](./media/image31.png)

<span data-ttu-id="bd36c-154">**Obrázek 6-31**.</span><span class="sxs-lookup"><span data-stu-id="bd36c-154">**Figure 6-31**.</span></span> <span data-ttu-id="bd36c-155">Testování katalogu mikroslužeb s jeho uživatelské rozhraní Swagger</span><span class="sxs-lookup"><span data-stu-id="bd36c-155">Testing the Catalog microservice with its Swagger UI</span></span>

<span data-ttu-id="bd36c-156">V tomto okamžiku můžete nastavit zarážku v kódu jazyka C# v sadě Visual Studio, testování mikroslužby pomocí metod zveřejněných v uživatelské rozhraní Swagger a nakonec Vyčistit vše, co se `docker-compose down` příkazu.</span><span class="sxs-lookup"><span data-stu-id="bd36c-156">At this point, you could set a breakpoint in C# code in Visual Studio, test the microservice with the methods exposed in Swagger UI, and finally clean-up everything with the `docker-compose down` command.</span></span>

<span data-ttu-id="bd36c-157">Komunikace přímý přístup do mikroslužeb, v tomto případě přes externí port 5101 ale přesně chcete, aby ve vaší aplikaci.</span><span class="sxs-lookup"><span data-stu-id="bd36c-157">However, direct-access communication to the microservice, in this case through the external port 5101, is precisely what you want to avoid in your application.</span></span> <span data-ttu-id="bd36c-158">A, který se můžete vyhnout tak, že nastavíte další úroveň dereference brány rozhraní API (v tomto případě Ocelot).</span><span class="sxs-lookup"><span data-stu-id="bd36c-158">And you can avoid that by setting the additional level of indirection of the API Gateway (Ocelot, in this case).</span></span> <span data-ttu-id="bd36c-159">Tímto způsobem, klientská aplikace nebude mít přístup k přímo mikroslužbách.</span><span class="sxs-lookup"><span data-stu-id="bd36c-159">That way, the client app won’t directly access the microservice.</span></span>

## <a name="implementing-your-api-gateways-with-ocelot"></a><span data-ttu-id="bd36c-160">Implementace vaší brány rozhraní API s Ocelot</span><span class="sxs-lookup"><span data-stu-id="bd36c-160">Implementing your API Gateways with Ocelot</span></span>

<span data-ttu-id="bd36c-161">Ocelot je v podstatě sadu middlewares, které můžete použít v určitém pořadí.</span><span class="sxs-lookup"><span data-stu-id="bd36c-161">Ocelot is basically a set of middlewares that you can apply in a specific order.</span></span>

<span data-ttu-id="bd36c-162">Ocelot je navržen pro práci s ASP.NET Core pouze.</span><span class="sxs-lookup"><span data-stu-id="bd36c-162">Ocelot is designed to work with ASP.NET Core only.</span></span> <span data-ttu-id="bd36c-163">Je cílena netstandard2.0, takže ho můžete použít, všude, kde se podporuje .NET Standard 2.0, včetně modulu runtime .NET Core 2.0 a modul runtime rozhraní .NET Framework 4.6.1 a novějšími verzemi.</span><span class="sxs-lookup"><span data-stu-id="bd36c-163">It targets netstandard2.0 so it can be used anywhere .NET Standard 2.0 is supported, including .NET Core 2.0 runtime and .NET Framework 4.6.1 runtime and up.</span></span>

<span data-ttu-id="bd36c-164">Nainstalujte Ocelot a jeho závislosti ve vašem projektu ASP.NET Core s [balíček NuGet pro Ocelot](https://www.nuget.org/packages/Ocelot/), ze sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="bd36c-164">You install Ocelot and its dependencies in your ASP.NET Core project with [Ocelot's NuGet package](https://www.nuget.org/packages/Ocelot/), from Visual Studio.</span></span>

```powershell
Install-Package Ocelot
```

<span data-ttu-id="bd36c-165">V aplikaci eShopOnContainers jeho implementace Brána rozhraní API je jednoduchý projekt hostitele ASP.NET Core a jeho Ocelot middlewares zpracovat všechny funkce brány rozhraní API, jak je znázorněno na následujícím obrázku:</span><span class="sxs-lookup"><span data-stu-id="bd36c-165">In eShopOnContainers, its API Gateway implementation is a simple ASP.NET Core WebHost project, and Ocelot’s middlewares handle all the API Gateway features, as shown in the following image:</span></span>

![Zobrazení Průzkumníka řešení projektu brány rozhraní Ocelot API.](./media/image32.png)

<span data-ttu-id="bd36c-167">**Obrázek 6 – 32**.</span><span class="sxs-lookup"><span data-stu-id="bd36c-167">**Figure 6-32**.</span></span> <span data-ttu-id="bd36c-168">OcelotApiGw základního projektu v aplikaci eShopOnContainers</span><span class="sxs-lookup"><span data-stu-id="bd36c-168">The OcelotApiGw base project in eShopOnContainers</span></span>

<span data-ttu-id="bd36c-169">Tento projekt hostitele ASP.NET Core je v podstatě sestavován dva jednoduché soubory: `Program.cs` a `Startup.cs`.</span><span class="sxs-lookup"><span data-stu-id="bd36c-169">This ASP.NET Core WebHost project is basically built with two simple files:  `Program.cs` and `Startup.cs`.</span></span>

<span data-ttu-id="bd36c-170">Soubor Program.cs stejně musí vytvořit a nakonfigurovat typické BuildWebHost ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="bd36c-170">The Program.cs just needs to create and configure the typical ASP.NET Core BuildWebHost.</span></span>

```csharp
namespace OcelotApiGw
{
    public class Program
    {
        public static void Main(string[] args)
        {
            BuildWebHost(args).Run();
        }

        public static IWebHost BuildWebHost(string[] args)
        {
            var builder = WebHost.CreateDefaultBuilder(args);

            builder.ConfigureServices(s => s.AddSingleton(builder))
                    .ConfigureAppConfiguration(
                          ic => ic.AddJsonFile(Path.Combine("configuration",
                                                            "configuration.json")))
                    .UseStartup<Startup>();
            var host = builder.Build();
            return host;
        }
    }
}
```

<span data-ttu-id="bd36c-171">Je důležité zde pro Ocelot `configuration.json` soubor, který je nutné zadat do Tvůrce prostřednictvím `AddJsonFile()` metoda.</span><span class="sxs-lookup"><span data-stu-id="bd36c-171">The important point here for Ocelot is the `configuration.json` file that you must provide to the builder through the `AddJsonFile()` method.</span></span> <span data-ttu-id="bd36c-172">Že `configuration.json` zadávat všechny rozhraní API brány ReRoutes, což znamená externí koncové body s konkrétní porty a korelační koncovým bodům s interním, obvykle pomocí jiné porty.</span><span class="sxs-lookup"><span data-stu-id="bd36c-172">That `configuration.json` is where you specify all the API Gateway ReRoutes, meaning the external endpoints with specific ports and the correlated internal endpoints, usually using different ports.</span></span>

```json
{
    "ReRoutes": [],
    "GlobalConfiguration": {}
}
```

<span data-ttu-id="bd36c-173">Existují dvě části ke konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="bd36c-173">There are two sections to the configuration.</span></span> <span data-ttu-id="bd36c-174">Pole zpětného odeslání a GlobalConfiguration.</span><span class="sxs-lookup"><span data-stu-id="bd36c-174">An array of Re-Routes and a GlobalConfiguration.</span></span> <span data-ttu-id="bd36c-175">Znovu směruje jsou objekty, které informují Ocelot jak zacházet s nadřazeného požadavku.</span><span class="sxs-lookup"><span data-stu-id="bd36c-175">The Re-Routes are the objects that tell Ocelot how to treat an upstream request.</span></span> <span data-ttu-id="bd36c-176">Globální konfigurace umožňuje přepsání znovu směrovat konkrétní nastavení.</span><span class="sxs-lookup"><span data-stu-id="bd36c-176">The Global configuration allows overrides of Re-Route specific settings.</span></span> <span data-ttu-id="bd36c-177">To je užitečné, pokud nechcete spravovat velké množství znovu směrovat konkrétní nastavení.</span><span class="sxs-lookup"><span data-stu-id="bd36c-177">It’s useful if you don’t want to manage lots of Re-Route specific settings.</span></span>

<span data-ttu-id="bd36c-178">Tady je zjednodušený příklad [přesměrovat konfigurační soubor](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/ApiGateways/Web.Bff.Shopping/apigw/configuration.json) z jednoho z brány rozhraní API v aplikaci eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="bd36c-178">Here’s a simplified example of [ReRoute configuration file](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/ApiGateways/Web.Bff.Shopping/apigw/configuration.json) from one of the API Gateways from eShopOnContainers.</span></span>

```json
{
  "ReRoutes": [
    {
      "DownstreamPathTemplate": "/api/{version}/{everything}",
      "DownstreamScheme": "http",
      "DownstreamHostAndPorts": [
        {
          "Host": "catalog.api",
          "Port": 80
        }
      ],
      "UpstreamPathTemplate": "/api/{version}/c/{everything}",
      "UpstreamHttpMethod": [ "POST", "PUT", "GET" ]
    },
    {
      "DownstreamPathTemplate": "/api/{version}/{everything}",
      "DownstreamScheme": "http",
      "DownstreamHostAndPorts": [
        {
          "Host": "basket.api",
          "Port": 80
        }
      ],
      "UpstreamPathTemplate": "/api/{version}/b/{everything}",
      "UpstreamHttpMethod": [ "POST", "PUT", "GET" ],
      "AuthenticationOptions": {
        "AuthenticationProviderKey": "IdentityApiKey",
        "AllowedScopes": []
      }
    }

  ],
    "GlobalConfiguration": {
      "RequestIdKey": "OcRequestId",
      "AdministrationPath": "/administration"
    }
  }
```

<span data-ttu-id="bd36c-179">Hlavní funkce brány rozhraní API Ocelot je využívat příchozích požadavků HTTP a předat je do podřízené služby, aktuálně jako jiný HTTP žádosti.</span><span class="sxs-lookup"><span data-stu-id="bd36c-179">The main functionality of an Ocelot API Gateway is to take incoming HTTP requests and forward them on to a downstream service, currently as another HTTP request.</span></span> <span data-ttu-id="bd36c-180">Společnosti ocelot popisuje směrování jeden požadavek na jiný jako znovu směrovat.</span><span class="sxs-lookup"><span data-stu-id="bd36c-180">Ocelot’s describes the routing of one request to another as a Re-Route.</span></span>

<span data-ttu-id="bd36c-181">Například zaměřme se na jednu z znovu směruje v configuration.json uvedeného konfigurace pro mikroslužby nákupní košík.</span><span class="sxs-lookup"><span data-stu-id="bd36c-181">For instance, let’s focus on one of the Re-Routes in the configuration.json from above, the configuration for the Basket microservice.</span></span>

```json
{
      "DownstreamPathTemplate": "/api/{version}/{everything}",
      "DownstreamScheme": "http",
      "DownstreamHostAndPorts": [
        {
          "Host": "basket.api",
          "Port": 80
        }
      ],
      "UpstreamPathTemplate": "/api/{version}/b/{everything}",
      "UpstreamHttpMethod": [ "POST", "PUT", "GET" ],
      "AuthenticationOptions": {
        "AuthenticationProviderKey": "IdentityApiKey",
        "AllowedScopes": []
      }
}
```

<span data-ttu-id="bd36c-182">DownstreamPathTemplate, schéma a DownstreamHostAndPorts je možné tento požadavek se předají do adresy URL interní mikroslužeb.</span><span class="sxs-lookup"><span data-stu-id="bd36c-182">The DownstreamPathTemplate, Scheme, and DownstreamHostAndPorts make the internal microservice URL that this request will be forwarded to.</span></span>

<span data-ttu-id="bd36c-183">Port, který je interní port používaný službou.</span><span class="sxs-lookup"><span data-stu-id="bd36c-183">The port is the internal port used by the service.</span></span> <span data-ttu-id="bd36c-184">Při používání kontejnerů, port zadaný v příslušným souborem dockerfile.</span><span class="sxs-lookup"><span data-stu-id="bd36c-184">When using containers, the port specified at its dockerfile.</span></span>

<span data-ttu-id="bd36c-185">`Host` Je název služby, který závisí na rozlišení názvu služby používáte.</span><span class="sxs-lookup"><span data-stu-id="bd36c-185">The `Host` is a service name that depends on the service name resolution you are using.</span></span> <span data-ttu-id="bd36c-186">Při použití docker-compose, služby názvy jsou poskytované hostitele Dockeru, který používá názvy služeb v dockeru-compose soubory.</span><span class="sxs-lookup"><span data-stu-id="bd36c-186">When using docker-compose, the services names are provided by the Docker Host, which is using the service names provided in the docker-compose files.</span></span> <span data-ttu-id="bd36c-187">Pokud používáte orchestrátoru, jako je Kubernetes nebo Service Fabric, tento název se mají překládat pomocí DNS nebo překlad poskytované jednotlivých orchestrátorů liší.</span><span class="sxs-lookup"><span data-stu-id="bd36c-187">If using an orchestrator like Kubernetes or Service Fabric, that name should be resolved by the DNS or name resolution provided by each orchestrator.</span></span>

<span data-ttu-id="bd36c-188">DownstreamHostAndPorts je pole, která obsahuje hostitele a port příjem dat, které chcete přesměrovat požadavky do služeb.</span><span class="sxs-lookup"><span data-stu-id="bd36c-188">DownstreamHostAndPorts is an array that contains the host and port of any downstream services that you wish to forward requests to.</span></span> <span data-ttu-id="bd36c-189">Obvykle bude obsahovat pouze jednu položku, ale v některých případech můžete chtít načíst z žádostí vyvažovat mezi službami pro příjem dat a Ocelot umožňuje přidat více než jednu položku a pak vyberte nástroj pro vyrovnávání zatížení.</span><span class="sxs-lookup"><span data-stu-id="bd36c-189">Usually this will just contain one entry but sometimes you might want to load balance requests to your downstream services and Ocelot lets you add more than one entry and then select a load balancer.</span></span> <span data-ttu-id="bd36c-190">Ale pokud používáte Azure a všechny nástroje orchestrator je pravděpodobně lepší představu vyrovnávat zatížení pomocí infrastruktury cloudu a nástroje orchestrator.</span><span class="sxs-lookup"><span data-stu-id="bd36c-190">But if using Azure and any orchestrator it is probably a better idea to load balance with the cloud and orchestrator infrastructure.</span></span>

<span data-ttu-id="bd36c-191">UpstreamPathTemplate je adresa URL, kterou Ocelot použije k identifikaci DownstreamPathTemplate, které chcete použít pro daný požadavek od klienta.</span><span class="sxs-lookup"><span data-stu-id="bd36c-191">The UpstreamPathTemplate is the URL that Ocelot will use to identify which DownstreamPathTemplate to use for a given request from the client.</span></span> <span data-ttu-id="bd36c-192">Nakonec UpstreamHttpMethod se používá, takže můžete Ocelot rozlišovat mezi různými požadavky (GET, POST, PUT) na stejnou adresu URL.</span><span class="sxs-lookup"><span data-stu-id="bd36c-192">Finally, the UpstreamHttpMethod is used so Ocelot can distinguish between different requests (GET, POST, PUT) to the same URL.</span></span>

<span data-ttu-id="bd36c-193">V tomto okamžiku můžete mít jednu Ocelot rozhraní API brány (hostitele ASP.NET Core) pomocí některého nebo [více sloučit soubory configuration.json](https://ocelot.readthedocs.io/en/latest/features/configuration.html#merging-configuration-files) nebo také můžete uložit [konfigurace v úložišti konzul KV](https://ocelot.readthedocs.io/en/latest/features/configuration.html#store-configuration-in-consul).</span><span class="sxs-lookup"><span data-stu-id="bd36c-193">At this point, you could have a single Ocelot API Gateway (ASP.NET Core WebHost) using one or [multiple merged configuration.json files](https://ocelot.readthedocs.io/en/latest/features/configuration.html#merging-configuration-files) or you can also store the [configuration in a Consul KV store](https://ocelot.readthedocs.io/en/latest/features/configuration.html#store-configuration-in-consul).</span></span>

<span data-ttu-id="bd36c-194">Ale zavedení v částech architektury a návrhu, pokud Opravdu chcete mít autonomní mikroslužeb, může být lepší rozdělit jeden monolitické Brána rozhraní API do více bran rozhraní API a/nebo BFF (back-endu pro front-endu).</span><span class="sxs-lookup"><span data-stu-id="bd36c-194">But as introduced in the architecture and design sections, if you really want to have autonomous microservices, it might be better to split that single monolithic API Gateway into multiple API Gateways and/or BFF (Backend for Frontend).</span></span> <span data-ttu-id="bd36c-195">Pro tento účel Podívejme se na tom, jak implementovat tento přístup se kontejnery Dockeru.</span><span class="sxs-lookup"><span data-stu-id="bd36c-195">For that purpose, let’s see how to implement that approach with Docker containers.</span></span>

### <a name="using-a-single-docker-container-image-to-run-multiple-different-api-gateway--bff-container-types"></a><span data-ttu-id="bd36c-196">Pomocí jedné image kontejneru Dockeru pro spuštění více jinou bránu rozhraní API / typy BFF kontejneru</span><span class="sxs-lookup"><span data-stu-id="bd36c-196">Using a single Docker container image to run multiple different API Gateway / BFF container types</span></span>

<span data-ttu-id="bd36c-197">V aplikaci eShopOnContainers používáme jednu image kontejneru Dockeru s bránou Ocelot rozhraní API, ale pak za běhu, vytvoříme různé služby/kontejnery pro každý typ rozhraní API – brána/BFF zadáním různých configuration.json soubor pomocí dockeru svazku přístup do jiné složky počítače pro každou službu.</span><span class="sxs-lookup"><span data-stu-id="bd36c-197">In eShopOnContainers we’re using a single Docker container image with the Ocelot API Gateway but then, at run time, we create different services/containers for each type of API-Gateway/BFF by providing a different configuration.json file, using a docker volume to access a different PC folder for each service.</span></span>

![Jedné image Dockeru pro rozhraní API Ocelot brány se používá pro všechny čtyři brány rozhraní API](./media/image33.png)

<span data-ttu-id="bd36c-199">**Obrázek 6-33**.</span><span class="sxs-lookup"><span data-stu-id="bd36c-199">**Figure 6-33**.</span></span> <span data-ttu-id="bd36c-200">Znovu pomocí jedné image Dockeru Ocelot napříč více typy brány rozhraní API</span><span class="sxs-lookup"><span data-stu-id="bd36c-200">Re-using a single Ocelot Docker image across multiple API Gateway types</span></span>

<span data-ttu-id="bd36c-201">V aplikaci eShopOnContainers, "Obecný Ocelot rozhraní API brány Image Dockeru" Vytvoření projektu s názvem 'OcelotApiGw' a obrázek název "eshop/ocelotapigw", který je zadaný v souboru docker-compose.yml.</span><span class="sxs-lookup"><span data-stu-id="bd36c-201">In eShopOnContainers, the “Generic Ocelot API Gateway Docker Image” is created with the project named 'OcelotApiGw' and the image name “eshop/ocelotapigw” that is specified in the docker-compose.yml file.</span></span> <span data-ttu-id="bd36c-202">Potom při nasazování do služby Docker, bude čtyři kontejnery Brána rozhraní API, které jsou vytvořené z této stejnou image Dockeru, jak je znázorněno v následujícím výpisu ze souboru docker-compose.yml.</span><span class="sxs-lookup"><span data-stu-id="bd36c-202">Then, when deploying to Docker, there will be four API-Gateway containers created from that same Docker image, as shown in the following extract from the docker-compose.yml file.</span></span>

```yml
  mobileshoppingapigw:
    image: eshop/ocelotapigw:${TAG:-latest}
    build:
      context: .
      dockerfile: src/ApiGateways/ApiGw-Base/Dockerfile

  mobilemarketingapigw:
    image: eshop/ocelotapigw:${TAG:-latest}
    build:
      context: .
      dockerfile: src/ApiGateways/ApiGw-Base/Dockerfile

  webshoppingapigw:
    image: eshop/ocelotapigw:${TAG:-latest}
    build:
      context: .
      dockerfile: src/ApiGateways/ApiGw-Base/Dockerfile

  webmarketingapigw:
    image: eshop/ocelotapigw:${TAG:-latest}
    build:
      context: .
      dockerfile: src/ApiGateways/ApiGw-Base/Dockerfile
```

<span data-ttu-id="bd36c-203">Kromě toho, jak je vidět v následujícím souboru docker-compose.override.yml jediným rozdílem mezi těchto kontejnerů Brána rozhraní API je Ocelot konfigurační soubor, který se liší pro každý kontejner služby a je zadán v době běhu pomocí Docker svazku.</span><span class="sxs-lookup"><span data-stu-id="bd36c-203">Additionally, as you can see in the following docker-compose.override.yml file, the only difference between those API Gateway containers is the Ocelot configuration file, which is different for each service container and it's specified at runtime through a Docker volume.</span></span>

```yml
mobileshoppingapigw:
  environment:
    - ASPNETCORE_ENVIRONMENT=Development
    - IdentityUrl=http://identity.api
  ports:
    - "5200:80"
  volumes:
    - ./src/ApiGateways/Mobile.Bff.Shopping/apigw:/app/configuration

mobilemarketingapigw:
  environment:
    - ASPNETCORE_ENVIRONMENT=Development
    - IdentityUrl=http://identity.api
  ports:
    - "5201:80"
  volumes:
    - ./src/ApiGateways/Mobile.Bff.Marketing/apigw:/app/configuration

webshoppingapigw:
  environment:
    - ASPNETCORE_ENVIRONMENT=Development
    - IdentityUrl=http://identity.api
  ports:
    - "5202:80"
  volumes:
    - ./src/ApiGateways/Web.Bff.Shopping/apigw:/app/configuration

webmarketingapigw:
  environment:
    - ASPNETCORE_ENVIRONMENT=Development
    - IdentityUrl=http://identity.api
  ports:
    - "5203:80"
  volumes:
    - ./src/ApiGateways/Web.Bff.Marketing/apigw:/app/configuration
```

<span data-ttu-id="bd36c-204">Z důvodu této předchozí kód a jak je znázorněno v Průzkumníku Visual Studio pod jediným souborem zapotřebí k definování každé konkrétní obchodní/BFF Brána rozhraní API je jenom configuration.json soubor, protože čtyři brány rozhraní API jsou založeny na stejnou image Dockeru.</span><span class="sxs-lookup"><span data-stu-id="bd36c-204">Because of that previous code, and as shown in the Visual Studio Explorer below, the only file needed to define each specific business/BFF API Gateway is just a configuration.json file, because the four API Gateways are based on the same Docker image.</span></span>

![Jediným rozdílem mezi všechny brány rozhraní API je soubor configuration.json na každé z nich.](./media/image34.png)

<span data-ttu-id="bd36c-206">**Obrázek 6 – 34**.</span><span class="sxs-lookup"><span data-stu-id="bd36c-206">**Figure 6-34**.</span></span> <span data-ttu-id="bd36c-207">Pouze soubor zapotřebí k definování každou bránu rozhraní API / BFF s Ocelot je konfigurační soubor</span><span class="sxs-lookup"><span data-stu-id="bd36c-207">The only file needed to define each API Gateway / BFF with Ocelot is a configuration file</span></span>

<span data-ttu-id="bd36c-208">Rozdělením brány rozhraní API do více bran rozhraní API můžete spravovat různé vývojové týmy, zaměřuje se na různé podmnožiny mikroslužeb své vlastní brány rozhraní API pomocí nezávislé Ocelot konfigurační soubory.</span><span class="sxs-lookup"><span data-stu-id="bd36c-208">By splitting the API Gateway into multiple API Gateways, different development teams focusing on different subsets of microservices can manage their own API Gateways by using independent Ocelot configuration files.</span></span> <span data-ttu-id="bd36c-209">Kromě toho ve stejnou dobu mohli znovu použít stejná image Dockeru Ocelot.</span><span class="sxs-lookup"><span data-stu-id="bd36c-209">Plus, at the same time they can reuse the same Ocelot Docker image.</span></span>

<span data-ttu-id="bd36c-210">Nyní Pokud spouštíte aplikaci eShopOnContainers pomocí brány rozhraní API (zahrnuté ve výchozím nastavení v sadě Visual Studio při otevírání řešení aplikaci eShopOnContainers ServicesAndWebApps.sln nebo pokud běží "docker-compose up"), budou provedeny následující ukázka trasy.</span><span class="sxs-lookup"><span data-stu-id="bd36c-210">Now, if you run eShopOnContainers with the API Gateways (included by default in VS when opening eShopOnContainers-ServicesAndWebApps.sln solution or if running “docker-compose up”), the following sample routes will be performed.</span></span>

<span data-ttu-id="bd36c-211">Například při návštěvě adresa URL upstreamu `http://localhost:5202/api/v1/c/catalog/items/2/` obsluhuje webshoppingapigw Brána rozhraní API, získáte stejný výsledek z interní adresy URL pro příjem dat `http://catalog.api/api/v1/2` v rámci hostitele Docker, stejně jako v následující prohlížeče.</span><span class="sxs-lookup"><span data-stu-id="bd36c-211">For instance, when visiting the upstream URL `http://localhost:5202/api/v1/c/catalog/items/2/` served by the webshoppingapigw API Gateway, you get the same result from the internal Downstream URL `http://catalog.api/api/v1/2` within the Docker host, as in the following browser.</span></span>

![Zobrazit v prohlížeči neodpověděla Catalog.api prostřednictvím brány rozhraní API.](./media/image35.png)

<span data-ttu-id="bd36c-213">**Obrázek 6 – 35**.</span><span class="sxs-lookup"><span data-stu-id="bd36c-213">**Figure 6-35**.</span></span> <span data-ttu-id="bd36c-214">Přístup prostřednictvím adresy URL poskytnuté brány rozhraní API mikroslužby</span><span class="sxs-lookup"><span data-stu-id="bd36c-214">Accessing a microservice through a URL provided by the API Gateway</span></span>

<span data-ttu-id="bd36c-215">Z důvodu testování nebo ladění z důvodů, pokud byste chtěli přímý přístup ke kontejneru Dockeru katalogu (pouze ve vývojovém prostředí) bez průchodu přes bránu rozhraní API, protože je "catalog.api" překlad názvů DNS, která je interní pro hostitele Docker (služba zjišťování zpracována docker-compose názvy služeb), je jediný způsob, jak přímý přístup k kontejneru prostřednictvím externího portu publikované v docker-compose.override.yml, která se poskytuje jenom pro vývoj pro testy, například `http://localhost:5101/api/v1/Catalog/items/1` v následujícím prohlížeč.</span><span class="sxs-lookup"><span data-stu-id="bd36c-215">Because of testing or debugging reasons, if you wanted to directly access to the Catalog Docker container (only at the development environment) without passing through the API Gateway, since 'catalog.api' is a DNS resolution internal to the Docker host (service discovery handled by docker-compose service names), the only way to directly access the container is through the external port published in the docker-compose.override.yml, which is provided only for development tests, such as `http://localhost:5101/api/v1/Catalog/items/1` in the following browser.</span></span>

![Zobrazit v prohlížeči neodpověděla Catalog.api přímo na Catalog.api, stejný jako ten prostřednictvím brány rozhraní API.](./media/image36.png)

<span data-ttu-id="bd36c-217">**Obrázek 6 – 36**.</span><span class="sxs-lookup"><span data-stu-id="bd36c-217">**Figure 6-36**.</span></span> <span data-ttu-id="bd36c-218">Přímý přístup k mikroslužby pro účely testování</span><span class="sxs-lookup"><span data-stu-id="bd36c-218">Direct access to a microservice for testing purposes</span></span>

<span data-ttu-id="bd36c-219">Ale aplikace je nakonfigurovaná tak přistupuje všechny mikroslužby prostřednictvím brány rozhraní API, ale není přímo portovaný "zástupce".</span><span class="sxs-lookup"><span data-stu-id="bd36c-219">But the application is configured so it accesses all the microservices through the API Gateways, not though the direct port “shortcuts”.</span></span>

### <a name="the-gateway-aggregation-pattern-in-eshoponcontainers"></a><span data-ttu-id="bd36c-220">Model agregace pomocí brány v aplikaci eShopOnContainers</span><span class="sxs-lookup"><span data-stu-id="bd36c-220">The Gateway aggregation pattern in eShopOnContainers</span></span>

<span data-ttu-id="bd36c-221">Zavedeném dříve, je flexibilní způsob, jak implementovat agregace požadavků s vlastní služby pomocí kódu.</span><span class="sxs-lookup"><span data-stu-id="bd36c-221">As introduced previously, a flexible way to implement requests aggregation is with custom services, by code.</span></span> <span data-ttu-id="bd36c-222">Může také implementovat agregace požadavků s [funkce agregace požadavků v Ocelot](https://ocelot.readthedocs.io/en/latest/features/requestaggregation.html#request-aggregation), ale nemusí být tak flexibilní podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="bd36c-222">You could also implement request aggregation with the [Request Aggregation feature in Ocelot](https://ocelot.readthedocs.io/en/latest/features/requestaggregation.html#request-aggregation), but it might not be as flexible as you need.</span></span> <span data-ttu-id="bd36c-223">Vybraný způsob implementace agregace v aplikaci eShopOnContainers tedy s explicitní služby webového rozhraní API ASP.NET Core pro každý agregátoru.</span><span class="sxs-lookup"><span data-stu-id="bd36c-223">Therefore, the selected way to implement aggregation in eShopOnContainers is with an explicit ASP.NET Core Web API services for each aggregator.</span></span>

<span data-ttu-id="bd36c-224">Podle tohoto přístupu složení diagram brány rozhraní API je ve skutečnosti o něco více rozšířené při zvažování služby agregátoru, které nejsou uvedeny v dříve uvedeném diagramu zjednodušení globální architektury.</span><span class="sxs-lookup"><span data-stu-id="bd36c-224">According to that approach, the API Gateway composition diagram is in reality a bit more extended when considering the aggregator services that are not shown in the simplified global architecture diagram shown previously.</span></span>

<span data-ttu-id="bd36c-225">V následujícím diagramu můžete také zobrazit, fungování služby agregátoru s jejich související brány rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="bd36c-225">In the following diagram, you can also see how the aggregator services work with their related API Gateways.</span></span>

![Architektura aplikaci eShopOnContainers zobrazující služby agregátoru.](./media/image37.png)

<span data-ttu-id="bd36c-227">**Obrázek 6-37**.</span><span class="sxs-lookup"><span data-stu-id="bd36c-227">**Figure 6-37**.</span></span> <span data-ttu-id="bd36c-228">aplikaci eShopOnContainers architektury s využitím služby agregátoru</span><span class="sxs-lookup"><span data-stu-id="bd36c-228">eShopOnContainers architecture with aggregator services</span></span>

<span data-ttu-id="bd36c-229">Dále přiblížení na obchodní oblast "Nákupní" na následujícím obrázku vidíte, že častá komunikace mezi klientské aplikace a mikroslužby je nižší při použití služby agregátoru v brány rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="bd36c-229">Zooming in further, on the “Shopping” business area in the following image, you can see that chattiness between the client apps and the microservices is reduced when using the aggregator services in the API Gateways.</span></span>

![aplikaci eShopOnContainers architektury přiblížit, zobrazuje služby agregátoru, který "sestaví" odpověď "propojení" odpověď z několika mikroslužeb ke snížení nadměrné komunikace s klientem end.](./media/image38.png)

<span data-ttu-id="bd36c-231">**Obrázek 6-38**.</span><span class="sxs-lookup"><span data-stu-id="bd36c-231">**Figure 6-38**.</span></span> <span data-ttu-id="bd36c-232">Přiblížit vizi služby agregátoru</span><span class="sxs-lookup"><span data-stu-id="bd36c-232">Zoom in vision of the Aggregator services</span></span>

<span data-ttu-id="bd36c-233">Můžete Všimněte si, jak při diagram znázorňuje možné požadavky přicházející z brány rozhraní API dostane poměrně složité.</span><span class="sxs-lookup"><span data-stu-id="bd36c-233">You can notice how when the diagram shows the possible requests coming from the API Gateways it can get pretty complex.</span></span> <span data-ttu-id="bd36c-234">I když se zobrazí, jak šipky modře by se dá zjednodušit, z pohledu klientských aplikací, při použití vzoru agregátoru díky snížení nadměrné komunikace a latence při komunikaci, takže v konečném důsledku výrazně zlepšuje uživatel prostředí pro vzdálené aplikace ( mobilní zařízení a aplikace SPA), zvlášť.</span><span class="sxs-lookup"><span data-stu-id="bd36c-234">Although you can see how the arrows in blue would be simplified, from a client apps perspective, when using the aggregator pattern by reducing chattiness and latency in the communication, ultimately significantly improving the user experience for the remote apps (mobile and SPA apps), especially.</span></span>

<span data-ttu-id="bd36c-235">V případě "Marketing" obchodní oblast a mikroslužeb je velmi jednoduchý případ použití tak nemusíme používat agregátorů, ale je také možné, je to možné, v případě potřeby.</span><span class="sxs-lookup"><span data-stu-id="bd36c-235">In the case of the “Marketing” business area and microservices, it is a very simple use case so there was no need to use aggregators, but it could also be possible, if needed.</span></span>

### <a name="authentication-and-authorization-in-ocelot-api-gateways"></a><span data-ttu-id="bd36c-236">Ověřování a autorizace ve Ocelot brány rozhraní API</span><span class="sxs-lookup"><span data-stu-id="bd36c-236">Authentication and authorization in Ocelot API Gateways</span></span>

<span data-ttu-id="bd36c-237">V rozhraní API brány Ocelot můžete pohodlně ověřovací služby, jako je například služba webového rozhraní API ASP.NET Core pomocí [IdentityServer](https://identityserver.io/) poskytuje ověřovací token, out nebo uvnitř brány rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="bd36c-237">In an Ocelot API Gateway you can sit the authentication service, such as an ASP.NET Core Web API service using [IdentityServer](https://identityserver.io/) providing the auth token, either out or inside the API Gateway.</span></span>

<span data-ttu-id="bd36c-238">Protože je v aplikaci eShopOnContainers více bran rozhraní API pomocí hranice založené na BFF a v oblastech obchodu, službu Identity/Auth zůstane mimo brány rozhraní API, jako zvýrazněné žlutou barvou v následujícím diagramu.</span><span class="sxs-lookup"><span data-stu-id="bd36c-238">Since eShopOnContainers is using multiple API Gateways with boundaries based on BFF and business areas, the Identity/Auth service is left out of the API Gateways, as highlighted in yellow in the following diagram.</span></span>

![diagram architektury aplikaci eShopOnContainers znázorňující Identity mikroslužeb pod bránu rozhraní API.](./media/image39.png)

<span data-ttu-id="bd36c-240">**Obrázek 6-39**.</span><span class="sxs-lookup"><span data-stu-id="bd36c-240">**Figure 6-39**.</span></span> <span data-ttu-id="bd36c-241">Pozice služba identit v aplikaci eShopOnContainers</span><span class="sxs-lookup"><span data-stu-id="bd36c-241">Position of the Identity service in eShopOnContainers</span></span>

<span data-ttu-id="bd36c-242">Ocelot ale také podporuje sedí identita a ověřování mikroslužby v rámci hranice Brána rozhraní API, stejně jako v tomto diagramu.</span><span class="sxs-lookup"><span data-stu-id="bd36c-242">However, Ocelot also supports sitting the Identity/Auth microservice within the API Gateway boundary, as in this other diagram.</span></span>

![Ověřování pomocí Identity mikroslužeb pod bránu rozhraní API (AG): (1) AG požadavků ověřovací token identity mikroslužeb, 2) Identity mikroslužeb vrátí toke AG, (3 - 4) AG žádosti z mikroslužeb pomocí tokenu ověřování.](./media/image40.png)

<span data-ttu-id="bd36c-244">**Obrázek 6 – 40**.</span><span class="sxs-lookup"><span data-stu-id="bd36c-244">**Figure 6-40**.</span></span> <span data-ttu-id="bd36c-245">Ověřování v Ocelot</span><span class="sxs-lookup"><span data-stu-id="bd36c-245">Authentication in Ocelot</span></span>

<span data-ttu-id="bd36c-246">Protože aplikace aplikaci eShopOnContainers rozdělil brány rozhraní API do více BFF (back-endu pro front-endu) a by obchodní oblasti brány rozhraní API, Další možností je vytvořit další bránu rozhraní API pro vyskytující aspekty.</span><span class="sxs-lookup"><span data-stu-id="bd36c-246">Because eShopOnContainers application has split the API Gateway into multiple BFF (Backend for Frontend) and business areas API Gateways, another option would had been to create an additional API Gateway for cross-cutting concerns.</span></span> <span data-ttu-id="bd36c-247">Volba bude veletrh v mikroslužbě složitější na základě architektury s různými mikroslužbami vyskytující aspekty.</span><span class="sxs-lookup"><span data-stu-id="bd36c-247">That choice would be fair in a more complex microservice based architecture with multiple cross-cutting concerns microservices.</span></span> <span data-ttu-id="bd36c-248">Vzhledem k tomu, že existuje pouze jeden problém vyskytující v aplikaci eShopOnContainers, rozhodla se právě zpracování služby zabezpečení ze sféry Brána rozhraní API pro jednoduchost společnosti saké.</span><span class="sxs-lookup"><span data-stu-id="bd36c-248">Since there's only one cross-cutting concern in eShopOnContainers, it was decided to just handle the security service out of the API Gateway realm, for simplicity’s sake.</span></span>

<span data-ttu-id="bd36c-249">V každém případě aplikace je zabezpečena na úrovni rozhraní API brány, modul ověřování brány rozhraní API Ocelot návštěvě zpočátku při pokusu o použití jakékoli zabezpečené mikroslužeb.</span><span class="sxs-lookup"><span data-stu-id="bd36c-249">In any case, if the app is secured at the API Gateway level, the authentication module of the Ocelot API Gateway is visited at first when trying to use any secured microservice.</span></span> <span data-ttu-id="bd36c-250">Znovu, který přesměruje požadavek HTTP na web nebo ověření Identity mikroslužeb pro získání přístupového tokenu, takže můžete navštívit chráněným službám s access_token.</span><span class="sxs-lookup"><span data-stu-id="bd36c-250">That re-directs the HTTP request to visit the Identity or auth microservice to get the access token so you can visit the protected services with the access_token.</span></span>

<span data-ttu-id="bd36c-251">Způsob zabezpečení pomocí ověřování jakékoli služby na úrovni rozhraní API brány je tak, že nastavíte AuthenticationProviderKey v jeho související nastavení na configuration.json.</span><span class="sxs-lookup"><span data-stu-id="bd36c-251">The way you secure with authentication any service at the API Gateway level is by setting the AuthenticationProviderKey in its related settings at the configuration.json.</span></span>

```json
    {
      "DownstreamPathTemplate": "/api/{version}/{everything}",
      "DownstreamScheme": "http",
      "DownstreamHostAndPorts": [
        {
          "Host": "basket.api",
          "Port": 80
        }
      ],
      "UpstreamPathTemplate": "/api/{version}/b/{everything}",
      "UpstreamHttpMethod": [],
      "AuthenticationOptions": {
        "AuthenticationProviderKey": "IdentityApiKey",
        "AllowedScopes": []
      }
    }
```

<span data-ttu-id="bd36c-252">Při spuštění Ocelot ho se podívá na AuthenticationOptions.AuthenticationProviderKey přesměruje a ověřte, zda je zaregistrován zprostředkovatele ověřování s daným klíčem.</span><span class="sxs-lookup"><span data-stu-id="bd36c-252">When Ocelot runs, it will look at the Re-Routes AuthenticationOptions.AuthenticationProviderKey and check that there is an Authentication Provider registered with the given key.</span></span> <span data-ttu-id="bd36c-253">Pokud není k dispozici, Ocelot nespustí.</span><span class="sxs-lookup"><span data-stu-id="bd36c-253">If there isn't, then Ocelot will not start up.</span></span> <span data-ttu-id="bd36c-254">Pokud existuje, pak přesměrovat použije tohoto zprostředkovatele při provádění.</span><span class="sxs-lookup"><span data-stu-id="bd36c-254">If there is, then the ReRoute will use that provider when it executes.</span></span>

<span data-ttu-id="bd36c-255">Protože má nakonfigurovanou Ocelot WebHost `authenticationProviderKey = "IdentityApiKey"`, vždy, když má libovolné požadavky bez jakékoli ověřovací token služby, které se vyžadují ověřování.</span><span class="sxs-lookup"><span data-stu-id="bd36c-255">Because the Ocelot WebHost is configured with the `authenticationProviderKey = "IdentityApiKey"`, that will require authentication whenever that service has any requests without any auth token.</span></span>

```csharp
namespace OcelotApiGw
{
    public class Startup
    {
        private readonly IConfiguration _cfg;

        public Startup(IConfiguration configuration) => _cfg = configuration;

        public void ConfigureServices(IServiceCollection services)
        {
            var identityUrl = _cfg.GetValue<string>("IdentityUrl");
            var authenticationProviderKey = "IdentityApiKey";
                         //…
            services.AddAuthentication()
                .AddJwtBearer(authenticationProviderKey, x =>
                {
                    x.Authority = identityUrl;
                    x.RequireHttpsMetadata = false;
                    x.TokenValidationParameters = new Microsoft.IdentityModel.Tokens.TokenValidationParameters()
                    {
                        ValidAudiences = new[] { "orders", "basket", "locations", "marketing", "mobileshoppingagg", "webshoppingagg" }
                    };
                });
            //...
        }
    }
}
```

<span data-ttu-id="bd36c-256">Pak také musíte nastavit autorizace pomocí atributu [Authorize] na prostředek, ke kterému lze přistupovat jako jsou mikroslužby, jako například následující mikroslužeb řadič nákupního košíku.</span><span class="sxs-lookup"><span data-stu-id="bd36c-256">Then, you also need to set authorization with the [Authorize] attribute on any resource to be accessed like the microservices, such as in the following Basket microservice controller.</span></span>

```csharp
namespace Microsoft.eShopOnContainers.Services.Basket.API.Controllers
{
    [Route("api/v1/[controller]")]
    [Authorize]
    public class BasketController : Controller
    {
      //...
    }
}
```

<span data-ttu-id="bd36c-257">ValidAudiences, jako je například "nákupní košík" se korelují s cílovou skupinou definované v jednotlivých mikroslužeb s `AddJwtBearer()` na ConfigureServices() třídu pro spuštění, jako je například následující kód.</span><span class="sxs-lookup"><span data-stu-id="bd36c-257">The ValidAudiences such as “basket” are correlated with the audience defined in each microservice with `AddJwtBearer()` at the ConfigureServices() of the Startup class, such as in the code below.</span></span>

```csharp
// prevent from mapping "sub" claim to nameidentifier.
JwtSecurityTokenHandler.DefaultInboundClaimTypeMap.Clear();

var identityUrl = Configuration.GetValue<string>("IdentityUrl");

services.AddAuthentication(options =>
{
    options.DefaultAuthenticateScheme = JwtBearerDefaults.AuthenticationScheme;
    options.DefaultChallengeScheme = JwtBearerDefaults.AuthenticationScheme;

}).AddJwtBearer(options =>
{
    options.Authority = identityUrl;
    options.RequireHttpsMetadata = false;
    options.Audience = "basket";
});
```

<span data-ttu-id="bd36c-258">Pokud se pokusíte o přístup k jakékoli zabezpečené mikroslužeb, jako košíku mikroslužeb pomocí adresy URL znovu směrovat na základě brány rozhraní API, jako je `http://localhost:5202/api/v1/b/basket/1`, a pokud nezadáte token platný získáte 401 Neautorizováno.</span><span class="sxs-lookup"><span data-stu-id="bd36c-258">If you try to access any secured microservice, like the Basket microservice with a Re-Route URL based on the API Gateway like `http://localhost:5202/api/v1/b/basket/1`, then you’ll get a 401 Unauthorized unless you provide a valid token.</span></span> <span data-ttu-id="bd36c-259">Na druhé straně Pokud ověření adresy URL znovu směrovat Ocelot vyvolá jakékoli podřízené schéma je k ní (adresu URL interní mikroslužeb) přidružen.</span><span class="sxs-lookup"><span data-stu-id="bd36c-259">On the other hand, if a Re-Route URL is authenticated, Ocelot will invoke whatever downstream scheme is associated with it (the internal microservice URL).</span></span>

<span data-ttu-id="bd36c-260">**Autorizace na úrovni ReRoutes Ocelot společnosti.**</span><span class="sxs-lookup"><span data-stu-id="bd36c-260">**Authorization at Ocelot’s ReRoutes tier.**</span></span>  <span data-ttu-id="bd36c-261">Ocelot podporuje ověřování na základě deklarací identity vyhodnocen po ověření.</span><span class="sxs-lookup"><span data-stu-id="bd36c-261">Ocelot supports claims-based authorization evaluated after the authentication.</span></span> <span data-ttu-id="bd36c-262">Nastavíte autorizaci na úrovni směrování tak, že přidáte následující řádky do konfigurace přesměrování.</span><span class="sxs-lookup"><span data-stu-id="bd36c-262">You set the authorization at a route level by adding the following lines to the ReRoute configuration.</span></span>

```json
"RouteClaimsRequirement": {
    "UserType": "employee"
}
```

<span data-ttu-id="bd36c-263">V tomto příkladu se nazývá autorizace middleware, Ocelot najdete Pokud má uživatel "UserType" typ deklarace identity v tokenu, a pokud tuto žádost má hodnotu "zaměstnance".</span><span class="sxs-lookup"><span data-stu-id="bd36c-263">In that example, when the authorization middleware is called, Ocelot will find if the user has the claim type 'UserType' in the token and if the value of that claim is 'employee'.</span></span> <span data-ttu-id="bd36c-264">Pokud tomu tak není, uživatel nebude oprávnění a odpověď bude 403 Zakázáno.</span><span class="sxs-lookup"><span data-stu-id="bd36c-264">If it isn’t, then the user will not be authorized and the response will be 403 forbidden.</span></span>

## <a name="using-kubernetes-ingress-plus-ocelot-api-gateways"></a><span data-ttu-id="bd36c-265">Pomocí příchozího přenosu dat Kubernetes plus Ocelot rozhraní API brány</span><span class="sxs-lookup"><span data-stu-id="bd36c-265">Using Kubernetes Ingress plus Ocelot API Gateways</span></span>

<span data-ttu-id="bd36c-266">Při použití Kubernetes (jako v clusteru Azure Kubernetes Service), obvykle sjednocení všechny požadavky HTTP přes [úroveň příchozího přenosu dat Kubernetes](https://kubernetes.io/docs/concepts/services-networking/ingress/) na základě *Nginx*.</span><span class="sxs-lookup"><span data-stu-id="bd36c-266">When using Kubernetes (like in an Azure Kubernetes Service cluster), you usually unify all the HTTP requests through the [Kubernetes Ingress tier](https://kubernetes.io/docs/concepts/services-networking/ingress/) based on *Nginx*.</span></span>

<span data-ttu-id="bd36c-267">V Kubernetes Pokud nepoužíváte žádné příchozí přístup, pak vaše služby a podů mají pouze směrovatelné IP adresy ve síť s clustery.</span><span class="sxs-lookup"><span data-stu-id="bd36c-267">In Kubernetes, if you don’t use any ingress approach, then your services and pods have IPs only routable by the cluster network.</span></span>

<span data-ttu-id="bd36c-268">Ale pokud používáte metodiky příchozího přenosu dat, budete mít střední vrstvy mezi Internetem a služby (včetně vaší brány rozhraní API), který funguje jako reverzní proxy server.</span><span class="sxs-lookup"><span data-stu-id="bd36c-268">But if you use an ingress approach, you'll have a middle tier between the Internet and your services (including your API Gateways), acting as a reverse proxy.</span></span>

<span data-ttu-id="bd36c-269">Příchozí přenos dat jako definice, je kolekce pravidel, která povolí příchozí připojení k dosažení Clusterové služby.</span><span class="sxs-lookup"><span data-stu-id="bd36c-269">As a definition, an Ingress is a collection of rules that allow inbound connections to reach the cluster services.</span></span> <span data-ttu-id="bd36c-270">Příchozí přenos dat je obvykle umožňují poskytovat externě dostupný adresy URL služby, načíst vyrovnávání provozu, ukončování protokolu SSL a dalších.</span><span class="sxs-lookup"><span data-stu-id="bd36c-270">An ingress is usually configured to provide services externally reachable URLs, load balance traffic, SSL termination and more.</span></span> <span data-ttu-id="bd36c-271">Uživatelé požadují příchozího přenosu dat tím, že publikuje příchozího přenosu dat prostředků do serveru rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="bd36c-271">Users request ingress by POSTing the Ingress resource to the API server.</span></span>

<span data-ttu-id="bd36c-272">V aplikaci eShopOnContainers, při vývoji místně a pomocí právě svého vývojového počítače jako hostitele Docker nepoužíváte žádné příchozí přenos dat, ale více bran rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="bd36c-272">In eShopOnContainers, when developing locally and using just your development machine as the Docker host, you are not using any ingress but only the multiple API Gateways.</span></span>

<span data-ttu-id="bd36c-273">Při cílení na "produkční" prostředí založené na Kubernetes, ale aplikaci eShopOnContainers používá příchozí přenos dat před brány rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="bd36c-273">However, when targeting a “production” environment based on Kubernetes, eShopOnContainers is using an ingress in front of the API gateways.</span></span> <span data-ttu-id="bd36c-274">Tímto způsobem klienti stále volat stejnou základní adresu URL, ale jsou požadavky směrovány do více bran rozhraní API nebo BFF.</span><span class="sxs-lookup"><span data-stu-id="bd36c-274">That way, the clients still call the same base URL but the requests are routed to multiple API Gateways or BFF.</span></span>

<span data-ttu-id="bd36c-275">Všimněte si, že brány rozhraní API jsou front endů nebo fasády zpřístupnění pouze služby, ale ne webové aplikace, které jsou obvykle mimo jejich rozsah.</span><span class="sxs-lookup"><span data-stu-id="bd36c-275">Note that API Gateways are front-ends or façades surfacing only the services but not the web applications that are usually out of their scope.</span></span> <span data-ttu-id="bd36c-276">Kromě toho brány rozhraní API může skrýt některé interní mikroslužeb.</span><span class="sxs-lookup"><span data-stu-id="bd36c-276">In addition, the API Gateways might hide certain internal microservices.</span></span>

<span data-ttu-id="bd36c-277">Příchozí přenos, ale je stejně přesměrovávání požadavků HTTP, ale pokus o skrýt všechny mikroslužby nebo do webové aplikace.</span><span class="sxs-lookup"><span data-stu-id="bd36c-277">The ingress, however, is just redirecting HTTP requests but not trying to hide any microservice or web app.</span></span>

<span data-ttu-id="bd36c-278">S vrstvou Nginx příchozího přenosu dat Kubernetes před webových aplikací a navíc několik bran rozhraní API Ocelot / BFF je ideální architekturu, jak je znázorněno v následujícím diagramu.</span><span class="sxs-lookup"><span data-stu-id="bd36c-278">Having an ingress Nginx tier in Kubernetes in front of the web applications plus the several Ocelot API Gateways / BFF is the ideal architecture, as shown in the following diagram.</span></span>

![Příchozího přenosu dat Kubernetes slouží jako reverzní proxy server pro veškerý provoz do aplikace, včetně webových aplikací, které jsou obvykle mimo rozsah brány rozhraní Api.](./media/image41.png)

<span data-ttu-id="bd36c-280">**Obrázek 6 – 41**.</span><span class="sxs-lookup"><span data-stu-id="bd36c-280">**Figure 6-41**.</span></span> <span data-ttu-id="bd36c-281">Úroveň příchozího přenosu dat v aplikaci eShopOnContainers při nasazení do Kubernetes</span><span class="sxs-lookup"><span data-stu-id="bd36c-281">The ingress tier in eShopOnContainers when deployed into Kubernetes</span></span>

<span data-ttu-id="bd36c-282">Když nasadíte aplikaci eShopOnContainers do Kubernetes, zpřístupní několika služeb nebo na koncové body prostřednictvím _příchozího přenosu dat_, v podstatě postfixes na adresy URL v následujícím seznamu:</span><span class="sxs-lookup"><span data-stu-id="bd36c-282">When you deploy eShopOnContainers into Kubernetes, it exposes just a few services or endpoints via _ingress_, basically the following list of postfixes on the URLs:</span></span>

- <span data-ttu-id="bd36c-283">`/` pro klienta webové aplikace SPA</span><span class="sxs-lookup"><span data-stu-id="bd36c-283">`/` for the client SPA web application</span></span>
- <span data-ttu-id="bd36c-284">`/webmvc` pro klienta webové aplikace MVC</span><span class="sxs-lookup"><span data-stu-id="bd36c-284">`/webmvc` for the client MVC web application</span></span>
- <span data-ttu-id="bd36c-285">`/webstatus` Zobrazení stavu/healthchecks klienta webové aplikace</span><span class="sxs-lookup"><span data-stu-id="bd36c-285">`/webstatus` for the client web app showing the status/healthchecks</span></span>
- <span data-ttu-id="bd36c-286">`/webshoppingapigw` pro web BFF a nákupního obchodních procesů</span><span class="sxs-lookup"><span data-stu-id="bd36c-286">`/webshoppingapigw` for the web BFF and shopping business processes</span></span>
- <span data-ttu-id="bd36c-287">`/webmarketingapigw` pro web BFF a marketingové obchodních procesů</span><span class="sxs-lookup"><span data-stu-id="bd36c-287">`/webmarketingapigw` for the web BFF and marketing business processes</span></span>
- <span data-ttu-id="bd36c-288">`/mobileshoppingapigw` pro mobilní BFF a nákupního obchodních procesů</span><span class="sxs-lookup"><span data-stu-id="bd36c-288">`/mobileshoppingapigw` for the mobile BFF and shopping business processes</span></span>
- <span data-ttu-id="bd36c-289">`/mobilemarketingapigw` mobilní BFF a marketingové obchodních procesů</span><span class="sxs-lookup"><span data-stu-id="bd36c-289">`/mobilemarketingapigw` for the mobile BFF and marketing business processes</span></span>

<span data-ttu-id="bd36c-290">Při nasazování do Kubernetes, každá brána rozhraní API Ocelot používá různé "configuration.json" soubor pro každý _pod_ spuštění brány rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="bd36c-290">When deploying to Kubernetes, each Ocelot API Gateway is using a different “configuration.json” file for each _pod_ running the API Gateways.</span></span> <span data-ttu-id="bd36c-291">Jsou k dispozici tyto soubory "configuration.json" tak, že připojí svazek vytvořený podle Kubernetes (původně se skriptem deploy.ps1) _mapování pro config_ s názvem "ocelot".</span><span class="sxs-lookup"><span data-stu-id="bd36c-291">Those “configuration.json” files are provided by mounting (originally with the deploy.ps1 script) a volume created based on a Kubernetes _config map_ named ‘ocelot’.</span></span> <span data-ttu-id="bd36c-292">Každý kontejner připojí souvisejících konfiguračních souborů ve složce kontejneru s názvem `/app/configuration`.</span><span class="sxs-lookup"><span data-stu-id="bd36c-292">Each container mounts its related configuration file in the container’s folder named `/app/configuration`.</span></span>

<span data-ttu-id="bd36c-293">V souborech zdrojového kódu aplikaci eShopOnContainers, původní soubory "configuration.json" lze nalézt v rámci `k8s/ocelot/` složky.</span><span class="sxs-lookup"><span data-stu-id="bd36c-293">In the source code files of eShopOnContainers, the original “configuration.json” files can be found within the `k8s/ocelot/` folder.</span></span> <span data-ttu-id="bd36c-294">Existuje jeden soubor pro každý BFF APIGateway.</span><span class="sxs-lookup"><span data-stu-id="bd36c-294">There’s one file for each BFF/APIGateway.</span></span>

## <a name="additional-cross-cutting-features-in-an-ocelot-api-gateway"></a><span data-ttu-id="bd36c-295">Další společné funkce v bránu rozhraní API Ocelot</span><span class="sxs-lookup"><span data-stu-id="bd36c-295">Additional cross-cutting features in an Ocelot API Gateway</span></span>

<span data-ttu-id="bd36c-296">Existují další důležité funkce pro výzkum a použít, při použití brány rozhraní API Ocelot popsané v následujících odkazů.</span><span class="sxs-lookup"><span data-stu-id="bd36c-296">There are other important features to research and use, when using an Ocelot API Gateway, described in the following links.</span></span>

- <span data-ttu-id="bd36c-297">**Zjišťování služby na straně klienta Ocelot integrování konzul nebo Eureka** \\</span><span class="sxs-lookup"><span data-stu-id="bd36c-297">**Service discovery in the client side integrating Ocelot with Consul or Eureka** \\</span></span>
  <https://ocelot.readthedocs.io/en/latest/features/servicediscovery.html>

- <span data-ttu-id="bd36c-298">**Ukládání do mezipaměti na úrovni rozhraní API brány** \\</span><span class="sxs-lookup"><span data-stu-id="bd36c-298">**Caching at the API Gateway tier** \\</span></span>
  <https://ocelot.readthedocs.io/en/latest/features/caching.html>

- <span data-ttu-id="bd36c-299">**Protokolování na úrovni rozhraní API brány** \\</span><span class="sxs-lookup"><span data-stu-id="bd36c-299">**Logging at the API Gateway tier** \\</span></span>
  <https://ocelot.readthedocs.io/en/latest/features/logging.html>

- <span data-ttu-id="bd36c-300">**Kvalita služby (opakovaných pokusů a jističe) na úrovni rozhraní API brány** \\</span><span class="sxs-lookup"><span data-stu-id="bd36c-300">**Quality of Service (Retries and Circuit breakers) at the API Gateway tier** \\</span></span>
  <https://ocelot.readthedocs.io/en/latest/features/qualityofservice.html>

- <span data-ttu-id="bd36c-301">**Omezení četnosti** \\</span><span class="sxs-lookup"><span data-stu-id="bd36c-301">**Rate limiting** \\</span></span>
  [https://ocelot.readthedocs.io/en/latest/features/ratelimiting.html](https://ocelot.readthedocs.io/en/latest/features/ratelimiting.html )

> [!div class="step-by-step"]
> <span data-ttu-id="bd36c-302">[Předchozí](background-tasks-with-ihostedservice.md)
> [další](../microservice-ddd-cqrs-patterns/index.md)</span><span class="sxs-lookup"><span data-stu-id="bd36c-302">[Previous](background-tasks-with-ihostedservice.md)
[Next](../microservice-ddd-cqrs-patterns/index.md)</span></span>
