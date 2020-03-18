---
title: Implementace bran rozhraní API s Ocelotem
description: Zjistěte, jak implementovat brány rozhraní API s Ocelotem a jak používat Ocelot v prostředí založeném na kontejnerech.
ms.date: 03/02/2020
ms.openlocfilehash: 28b9ca22d232baf3545d71b876cecf72fea05c92
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "78846943"
---
# <a name="implement-api-gateways-with-ocelot"></a><span data-ttu-id="5a9e2-103">Implementace bran rozhraní API s Ocelotem</span><span class="sxs-lookup"><span data-stu-id="5a9e2-103">Implement API Gateways with Ocelot</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5a9e2-104">Referenční aplikace mikroslužeb [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) v současné době používá funkce poskytované [vyslancem](https://www.envoyproxy.io/) k implementaci brány rozhraní API namísto dříve odkazovaného [Ocelotu](https://github.com/ThreeMammals/Ocelot).</span><span class="sxs-lookup"><span data-stu-id="5a9e2-104">The reference microservice application [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) is currently using features provided by [Envoy](https://www.envoyproxy.io/) to implement the API Gateway instead of the earlier referenced [Ocelot](https://github.com/ThreeMammals/Ocelot).</span></span>
> <span data-ttu-id="5a9e2-105">Tuto volbu návrhu jsme provedli z důvodu integrované podpory protokolu WebSocket, kterou vyžaduje nová mezioborová komunikace gRPC implementovaná v eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="5a9e2-105">We made this design choice because of Envoy's built-in support for the WebSocket protocol, required by the new gRPC inter-service communications implemented in eShopOnContainers.</span></span>
> <span data-ttu-id="5a9e2-106">Tuto část jsme však v průvodci zachovái, takže můžete Ocelot považovat za jednoduchou, schopnou a lehkou bránu rozhraní API vhodnou pro scénáře produkčního prostředí.</span><span class="sxs-lookup"><span data-stu-id="5a9e2-106">However, we've retained this section in the guide so you can consider Ocelot as a simple, capable, and lightweight API Gateway suitable for production-grade scenarios.</span></span>

## <a name="architect-and-design-your-api-gateways"></a><span data-ttu-id="5a9e2-107">Navrhněte a navrhněte brány rozhraní API</span><span class="sxs-lookup"><span data-stu-id="5a9e2-107">Architect and design your API Gateways</span></span>

<span data-ttu-id="5a9e2-108">Následující diagram architektury ukazuje, jak byly brány rozhraní API implementovány pomocí Ocelotu v eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="5a9e2-108">The following architecture diagram shows how API Gateways were implemented with Ocelot in eShopOnContainers.</span></span>

![Diagram znázorňující architekturu eShopOnContainers.](./media/implement-api-gateways-with-ocelot/eshoponcontainers-architecture.png)

<span data-ttu-id="5a9e2-110">**Obrázek 6-28**.</span><span class="sxs-lookup"><span data-stu-id="5a9e2-110">**Figure 6-28**.</span></span> <span data-ttu-id="5a9e2-111">Architektura eShopOnContainers s bránami API</span><span class="sxs-lookup"><span data-stu-id="5a9e2-111">eShopOnContainers architecture with API Gateways</span></span>

<span data-ttu-id="5a9e2-112">Tento diagram ukazuje, jak se celá aplikace nasadí do jednoho hostitele Dockeru nebo vývojového počítače s "Docker pro Windows" nebo "Docker pro Mac".</span><span class="sxs-lookup"><span data-stu-id="5a9e2-112">That diagram shows how the whole application is deployed into a single Docker host or development PC with "Docker for Windows" or "Docker for Mac".</span></span> <span data-ttu-id="5a9e2-113">Nasazení do libovolného orchestrator by však podobné, ale všechny kontejnery v diagramu může být škálovat v orchestrator.</span><span class="sxs-lookup"><span data-stu-id="5a9e2-113">However, deploying into any orchestrator would be similar, but any container in the diagram could be scaled out in the orchestrator.</span></span>

<span data-ttu-id="5a9e2-114">Kromě toho by měly být prostředky infrastruktury, jako jsou databáze, mezipaměti a zprostředkovatele zpráv, převedeny z orchestrátoru a nasazeny do vysoce dostupných systémů pro infrastrukturu, jako je Azure SQL Database, Azure Cosmos DB, Azure Redis, Azure Service Bus, nebo jakékoli řešení clustering HA v místním prostředí.</span><span class="sxs-lookup"><span data-stu-id="5a9e2-114">In addition, the infrastructure assets such as databases, cache, and message brokers should be offloaded from the orchestrator and deployed into high available systems for infrastructure, like Azure SQL Database, Azure Cosmos DB, Azure Redis, Azure Service Bus, or any HA clustering solution on-premises.</span></span>

<span data-ttu-id="5a9e2-115">Jak si můžete také všimnout v diagramu, s několika brány rozhraní API umožňuje více vývojových týmů být autonomní (v tomto případě funkce marketingu vs. nákupní funkce) při vývoji a nasazování svých mikroslužeb a jejich vlastní související brány rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="5a9e2-115">As you can also notice in the diagram, having several API Gateways allows multiple development teams to be autonomous (in this case Marketing features vs. Shopping features) when developing and deploying their microservices plus their own related API Gateways.</span></span>

<span data-ttu-id="5a9e2-116">Pokud jste měli jednu monolitickou bránu rozhraní API, což by znamenalo jeden bod, který by měl být aktualizován několika vývojovými týmy, které by mohly spojit všechny mikroslužby s jednou částí aplikace.</span><span class="sxs-lookup"><span data-stu-id="5a9e2-116">If you had a single monolithic API Gateway that would mean a single point to be updated by several development teams, which could couple all the microservices with a single part of the application.</span></span>

<span data-ttu-id="5a9e2-117">Chystáte mnohem dále v návrhu, někdy jemně odstupňované brány rozhraní API může být také omezena na jednu obchodní mikroslužeb v závislosti na zvolené architektuře.</span><span class="sxs-lookup"><span data-stu-id="5a9e2-117">Going much further in the design, sometimes a fine-grained API Gateway can also be limited to a single business microservice depending on the chosen architecture.</span></span> <span data-ttu-id="5a9e2-118">S hranice brány rozhraní API diktované firmou nebo doménou vám pomůže získat lepší návrh.</span><span class="sxs-lookup"><span data-stu-id="5a9e2-118">Having the API Gateway's boundaries dictated by the business or domain will help you to get a better design.</span></span>

<span data-ttu-id="5a9e2-119">Například jemné rozlišovací schopnost ve vrstvě brány rozhraní API může být užitečné zejména pro pokročilejší aplikace složené ui, které jsou založeny na mikroslužeb, protože koncept jemně odstupňované brány rozhraní API je podobný službě složení rozhraní.</span><span class="sxs-lookup"><span data-stu-id="5a9e2-119">For instance, fine granularity in the API Gateway tier can be especially useful for more advanced composite UI applications that are based on microservices, because the concept of a fine-grained API Gateway is similar to a UI composition service.</span></span>

<span data-ttu-id="5a9e2-120">Ponoříme se do dalšípodrobnosti v předchozí části [Vytváření složené houfně založené na mikroslužeb](../architect-microservice-container-applications/microservice-based-composite-ui-shape-layout.md).</span><span class="sxs-lookup"><span data-stu-id="5a9e2-120">We delve into more details in the previous section [Creating composite UI based on microservices](../architect-microservice-container-applications/microservice-based-composite-ui-shape-layout.md).</span></span>

<span data-ttu-id="5a9e2-121">Jako klíčový stánek s jídlem, pro mnoho středně velkých a velkých aplikací, pomocí vlastní-postavený API Gateway produkt je obvykle dobrý přístup, ale ne jako jeden monolitický agregátor nebo unikátní centrální vlastní brána rozhraní API, pokud, že brána rozhraní API umožňuje více nezávislých konfigurační oblasti pro několik vývojových týmů, které vytvářejí autonomní mikroslužby.</span><span class="sxs-lookup"><span data-stu-id="5a9e2-121">As key takeaway, for many medium- and large-size applications, using a custom-built API Gateway product is usually a good approach, but not as a single monolithic aggregator or unique central custom API Gateway unless that API Gateway allows multiple independent configuration areas for the several development teams creating autonomous microservices.</span></span>

### <a name="sample-microservicescontainers-to-reroute-through-the-api-gateways"></a><span data-ttu-id="5a9e2-122">Ukázka mikroslužeb/kontejnerů pro přesměrování přes brány rozhraní API</span><span class="sxs-lookup"><span data-stu-id="5a9e2-122">Sample microservices/containers to reroute through the API Gateways</span></span>

<span data-ttu-id="5a9e2-123">Jako příklad eShopOnContainers má kolem šesti typů interních mikroslužeb, které mají být publikovány prostřednictvím brány rozhraní API, jak je znázorněno na následujícím obrázku.</span><span class="sxs-lookup"><span data-stu-id="5a9e2-123">As an example, eShopOnContainers has around six internal microservice-types that have to be published through the API Gateways, as shown in the following image.</span></span>

![Snímek obrazovky složky Služby zobrazující její podsložky](./media/implement-api-gateways-with-ocelot/eshoponcontainers-microservice-folders.png)

<span data-ttu-id="5a9e2-125">**Obrázek 6-29**.</span><span class="sxs-lookup"><span data-stu-id="5a9e2-125">**Figure 6-29**.</span></span> <span data-ttu-id="5a9e2-126">Složky mikroslužeb v řešení eShopOnContainers v sadě Visual Studio</span><span class="sxs-lookup"><span data-stu-id="5a9e2-126">Microservice folders in eShopOnContainers solution in Visual Studio</span></span>

<span data-ttu-id="5a9e2-127">O službě Identity je v návrhu ponechána mimo směrování brány rozhraní API, protože je to jediný průřezový problém v systému, ačkoli s Ocelotem je také možné jej zahrnout jako součást seznamů přesměrování.</span><span class="sxs-lookup"><span data-stu-id="5a9e2-127">About the Identity service, in the design it's left out of the API Gateway routing because it's the only cross-cutting concern in the system, although with Ocelot it's also possible to include it as part of the rerouting lists.</span></span>

<span data-ttu-id="5a9e2-128">Všechny tyto služby jsou aktuálně implementovány jako ASP.NET služby základního webového rozhraní API, jak můžete zjistit z kódu.</span><span class="sxs-lookup"><span data-stu-id="5a9e2-128">All those services are currently implemented as ASP.NET Core Web API services, as you can tell from the code.</span></span> <span data-ttu-id="5a9e2-129">Zaměřme se na jednu z mikroslužeb, jako je kód mikroslužeb katalogu.</span><span class="sxs-lookup"><span data-stu-id="5a9e2-129">Let's focus on one of the microservices like the Catalog microservice code.</span></span>

![Snímek obrazovky Průzkumníka řešení zobrazující obsah projektu Catalog.API](./media/implement-api-gateways-with-ocelot/catalog-api-microservice-folders.png)

<span data-ttu-id="5a9e2-131">**Obrázek 6-30**.</span><span class="sxs-lookup"><span data-stu-id="5a9e2-131">**Figure 6-30**.</span></span> <span data-ttu-id="5a9e2-132">Ukázková mikroslužba webového rozhraní API (katalogová mikroslužba)</span><span class="sxs-lookup"><span data-stu-id="5a9e2-132">Sample Web API microservice (Catalog microservice)</span></span>

<span data-ttu-id="5a9e2-133">Uvidíte, že mikroslužba katalogu je typický ASP.NET core web api projektu s několika řadiče a metody, jako je v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="5a9e2-133">You can see that the Catalog microservice is a typical ASP.NET Core Web API project with several controllers and methods like in the following code.</span></span>

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

<span data-ttu-id="5a9e2-134">Požadavek HTTP skončí spuštěním tohoto druhu kódu Jazyka C# s přístupem k databázi mikroslužeb a jakékoli další požadované akce.</span><span class="sxs-lookup"><span data-stu-id="5a9e2-134">The HTTP request will end up running that kind of C# code accessing the microservice database and any additional required action.</span></span>

<span data-ttu-id="5a9e2-135">Pokud jde o adresu URL mikroslužeb, když jsou kontejnery nasazeny ve vašem místním vývojovém počítači (místní hostitel Dockeru), kontejner každé mikroslužby má vždy interní port (obvykle port 80) zadaný v jeho dockerfile, jako v následujícím dockerfile:</span><span class="sxs-lookup"><span data-stu-id="5a9e2-135">Regarding the microservice URL, when the containers are deployed in your local development PC (local Docker host), each microservice's container has always an internal port (usually port 80) specified in its dockerfile, as in the following dockerfile:</span></span>

```Dockerfile
FROM mcr.microsoft.com/dotnet/core/aspnet:3.1 AS base
WORKDIR /app
EXPOSE 80
```

<span data-ttu-id="5a9e2-136">Port 80 zobrazený v kódu je interní v rámci hostitele Dockeru, takže ho klientské aplikace nemohou oslovit.</span><span class="sxs-lookup"><span data-stu-id="5a9e2-136">The port 80 shown in the code is internal within the Docker host, so it can't be reached by client apps.</span></span>

<span data-ttu-id="5a9e2-137">Klientské aplikace mají přístup pouze k externím portům `docker-compose`(pokud existuje) publikovaným při nasazování pomocí aplikace .</span><span class="sxs-lookup"><span data-stu-id="5a9e2-137">Client apps can access only the external ports (if any) published when deploying with `docker-compose`.</span></span>

<span data-ttu-id="5a9e2-138">Tyto externí porty by neměly být publikovány při nasazování do produkčního prostředí.</span><span class="sxs-lookup"><span data-stu-id="5a9e2-138">Those external ports shouldn't be published when deploying to a production environment.</span></span> <span data-ttu-id="5a9e2-139">To je přesně důvod, proč chcete použít bránu rozhraní API, abyste se vyhnuli přímé komunikaci mezi klientskými aplikacemi a mikroslužbami.</span><span class="sxs-lookup"><span data-stu-id="5a9e2-139">This is precisely why you want to use the API Gateway, to avoid the direct communication between the client apps and the microservices.</span></span>

<span data-ttu-id="5a9e2-140">Však při vývoji, chcete získat přístup k mikroslužeb/kontejnerpřímo a spusťte jej přes Swagger.</span><span class="sxs-lookup"><span data-stu-id="5a9e2-140">However, when developing, you want to access the microservice/container directly and run it through Swagger.</span></span> <span data-ttu-id="5a9e2-141">To je důvod, proč v eShopOnContainers externí porty jsou stále určeny i v případě, že nebudou použity brány rozhraní API nebo klientské aplikace.</span><span class="sxs-lookup"><span data-stu-id="5a9e2-141">That's why in eShopOnContainers, the external ports are still specified even when they won't be used by the API Gateway or the client apps.</span></span>

<span data-ttu-id="5a9e2-142">Tady je příklad souboru `docker-compose.override.yml` pro mikroslužbu katalogu:</span><span class="sxs-lookup"><span data-stu-id="5a9e2-142">Here's an example of the `docker-compose.override.yml` file for the Catalog microservice:</span></span>

```yml
catalog-api:
  environment:
    - ASPNETCORE_ENVIRONMENT=Development
    - ASPNETCORE_URLS=http://0.0.0.0:80
    - ConnectionString=YOUR_VALUE
    - ... Other Environment Variables
  ports:
    - "5101:80"   # Important: In a production environment you should remove the external port (5101) kept here for microservice debugging purposes.
                  # The API Gateway redirects and access through the internal port (80).
```

<span data-ttu-id="5a9e2-143">Můžete vidět, jak v konfiguraci docker-compose.override.yml vnitřní port pro kontejner katalogu je port 80, ale port pro externí přístup je 5101.</span><span class="sxs-lookup"><span data-stu-id="5a9e2-143">You can see how in the docker-compose.override.yml configuration the internal port for the Catalog container is port 80, but the port for external access is 5101.</span></span> <span data-ttu-id="5a9e2-144">Ale tento port by neměl být používán aplikací při použití brány rozhraní API, pouze k ladění, spuštění a testování pouze mikroslužeb katalogu.</span><span class="sxs-lookup"><span data-stu-id="5a9e2-144">But this port shouldn't be used by the application when using an API Gateway, only to debug, run, and test just the Catalog microservice.</span></span>

<span data-ttu-id="5a9e2-145">Normálně nebudete nasazovat s docker-compose do produkčního prostředí, protože správné produkční nasazení prostředí pro mikroslužby je orchestrátor jako Kubernetes nebo Service Fabric.</span><span class="sxs-lookup"><span data-stu-id="5a9e2-145">Normally, you won't be deploying with docker-compose into a production environment because the right production deployment environment for microservices is an orchestrator like Kubernetes or Service Fabric.</span></span> <span data-ttu-id="5a9e2-146">Při nasazování do těchto prostředí používáte různé konfigurační soubory, kde nebudete publikovat přímo žádný externí port pro mikroslužby, ale budete vždy používat reverzní proxy z brány rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="5a9e2-146">When deploying to those environments you use different configuration files where you won't publish directly any external port for the microservices but, you'll always use the reverse proxy from the API Gateway.</span></span>

<span data-ttu-id="5a9e2-147">Spusťte mikroslužbu katalogu v místním hostiteli Dockeru.</span><span class="sxs-lookup"><span data-stu-id="5a9e2-147">Run the catalog microservice in your local Docker host.</span></span> <span data-ttu-id="5a9e2-148">Buď spusťte úplné řešení eShopOnContainers z Visual Studia (spustí všechny služby v souborech docker-compose) nebo spusťte mikroslužbu katalogu `docker-compose.yml` s `docker-compose.override.yml` následujícím příkazem docker-compose v CMD nebo PowerShellu umístěném ve složce, kde jsou umístěny a.</span><span class="sxs-lookup"><span data-stu-id="5a9e2-148">Either run the full eShopOnContainers solution from Visual Studio (it runs all the services in the docker-compose files), or start the Catalog microservice with the following docker-compose command in CMD or PowerShell positioned at the folder where the `docker-compose.yml` and `docker-compose.override.yml` are placed.</span></span>

```console
docker-compose run --service-ports catalog-api
```

<span data-ttu-id="5a9e2-149">Tento příkaz spustí pouze kontejner služby rozhraní katalogu api plus závislosti, které jsou zadány v docker-compose.yml.</span><span class="sxs-lookup"><span data-stu-id="5a9e2-149">This command only runs the catalog-api service container plus dependencies that are specified in the docker-compose.yml.</span></span> <span data-ttu-id="5a9e2-150">V tomto případě kontejner sql serveru a Kontejner RabbitMQ.</span><span class="sxs-lookup"><span data-stu-id="5a9e2-150">In this case, the SQL Server container and RabbitMQ container.</span></span>

<span data-ttu-id="5a9e2-151">Potom můžete přímo přistupovat k mikroslužbě katalogu a vidět jeho metody prostřednictvím uživatelského rozhraní Swagger, které přistupuje přímo prostřednictvím tohoto "externího" portu, v tomto případě `http://localhost:5101/swagger`:</span><span class="sxs-lookup"><span data-stu-id="5a9e2-151">Then, you can directly access the Catalog microservice and see its methods through the Swagger UI accessing directly through that "external" port, in this case `http://localhost:5101/swagger`:</span></span>

![Snímek obrazovky uživatelského rozhraní Swagger zobrazující rozhraní API REST rozhraní Catalog.API ROZHRANÍ API](./media/implement-api-gateways-with-ocelot/test-catalog-microservice.png)

<span data-ttu-id="5a9e2-153">**Obrázek 6-31**.</span><span class="sxs-lookup"><span data-stu-id="5a9e2-153">**Figure 6-31**.</span></span> <span data-ttu-id="5a9e2-154">Testování mikroslužby katalogu s jeho uživatelskérozhraní Swagger</span><span class="sxs-lookup"><span data-stu-id="5a9e2-154">Testing the Catalog microservice with its Swagger UI</span></span>

<span data-ttu-id="5a9e2-155">V tomto okamžiku můžete nastavit zarážku v kódu Jazyka C# v sadě Visual Studio, otestovat mikroslužbu s `docker-compose down` metodami vystavenými v unovém jazyce Swagger a nakonec vyčistit vše pomocí příkazu.</span><span class="sxs-lookup"><span data-stu-id="5a9e2-155">At this point, you could set a breakpoint in C# code in Visual Studio, test the microservice with the methods exposed in Swagger UI, and finally clean-up everything with the `docker-compose down` command.</span></span>

<span data-ttu-id="5a9e2-156">Však komunikace přímého přístupu k mikroslužbě, v tomto případě prostřednictvím externího portu 5101, je přesně to, co chcete vyhnout ve vaší aplikaci.</span><span class="sxs-lookup"><span data-stu-id="5a9e2-156">However, direct-access communication to the microservice, in this case through the external port 5101, is precisely what you want to avoid in your application.</span></span> <span data-ttu-id="5a9e2-157">A můžete se tomu vyhnout nastavením další úrovně dereference brány rozhraní API (Ocelot, v tomto případě).</span><span class="sxs-lookup"><span data-stu-id="5a9e2-157">And you can avoid that by setting the additional level of indirection of the API Gateway (Ocelot, in this case).</span></span> <span data-ttu-id="5a9e2-158">Tímto způsobem klientská aplikace nebude mít přímý přístup k mikroslužeb.</span><span class="sxs-lookup"><span data-stu-id="5a9e2-158">That way, the client app won't directly access the microservice.</span></span>

## <a name="implementing-your-api-gateways-with-ocelot"></a><span data-ttu-id="5a9e2-159">Implementace brány rozhraní API s Ocelotem</span><span class="sxs-lookup"><span data-stu-id="5a9e2-159">Implementing your API Gateways with Ocelot</span></span>

<span data-ttu-id="5a9e2-160">Ocelot je v podstatě sada middlewares, které můžete použít v určitém pořadí.</span><span class="sxs-lookup"><span data-stu-id="5a9e2-160">Ocelot is basically a set of middlewares that you can apply in a specific order.</span></span>

<span data-ttu-id="5a9e2-161">Ocelot je určen pro práci pouze s ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="5a9e2-161">Ocelot is designed to work with ASP.NET Core only.</span></span> <span data-ttu-id="5a9e2-162">Nejnovější verze cílů `.NETCoreApp 3.1` balíčku a proto není vhodná pro aplikace rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="5a9e2-162">The latest version of the package targets `.NETCoreApp 3.1` and hence it is not suitable for .NET Framework applications.</span></span>

<span data-ttu-id="5a9e2-163">Nainstalujete Ocelot a jeho závislosti v projektu ASP.NET Core s [balíčkem NuGet společnosti Ocelot](https://www.nuget.org/packages/Ocelot/)z aplikace Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="5a9e2-163">You install Ocelot and its dependencies in your ASP.NET Core project with [Ocelot's NuGet package](https://www.nuget.org/packages/Ocelot/), from Visual Studio.</span></span>

```powershell
Install-Package Ocelot
```

<span data-ttu-id="5a9e2-164">V eShopOnContainers je implementace brány API jednoduchým ASP.NET projektu Core WebHost a middleware Ocelot zpracovává všechny funkce brány ROZHRANÍ API, jak je znázorněno na následujícím obrázku:</span><span class="sxs-lookup"><span data-stu-id="5a9e2-164">In eShopOnContainers, its API Gateway implementation is a simple ASP.NET Core WebHost project, and Ocelot’s middleware handles all the API Gateway features, as shown in the following image:</span></span>

![Snímek obrazovky Průzkumníka řešení zobrazující projekt brány rozhraní API Ocelot](./media/implement-api-gateways-with-ocelot/ocelotapigw-base-project.png)

<span data-ttu-id="5a9e2-166">**Obrázek 6-32**.</span><span class="sxs-lookup"><span data-stu-id="5a9e2-166">**Figure 6-32**.</span></span> <span data-ttu-id="5a9e2-167">Základní projekt OcelotApiGw v eShopOnContainers</span><span class="sxs-lookup"><span data-stu-id="5a9e2-167">The OcelotApiGw base project in eShopOnContainers</span></span>

<span data-ttu-id="5a9e2-168">Tento ASP.NET core webhost projekt je v `Program.cs` podstatě postaven se dvěma jednoduchými soubory: a `Startup.cs`.</span><span class="sxs-lookup"><span data-stu-id="5a9e2-168">This ASP.NET Core WebHost project is basically built with two simple files:  `Program.cs` and `Startup.cs`.</span></span>

<span data-ttu-id="5a9e2-169">Program.cs stačí vytvořit a nakonfigurovat typické ASP.NET Core BuildWebHost.</span><span class="sxs-lookup"><span data-stu-id="5a9e2-169">The Program.cs just needs to create and configure the typical ASP.NET Core BuildWebHost.</span></span>

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

<span data-ttu-id="5a9e2-170">Důležitým bodem zde pro Ocelot je `configuration.json` soubor, který musíte `AddJsonFile()` poskytnout stavitelprostřednictvím metody.</span><span class="sxs-lookup"><span data-stu-id="5a9e2-170">The important point here for Ocelot is the `configuration.json` file that you must provide to the builder through the `AddJsonFile()` method.</span></span> <span data-ttu-id="5a9e2-171">To `configuration.json` je místo, kde zadáte všechny brány rozhraní API ReRoutes, což znamená externí koncové body s konkrétní porty a korelované vnitřní koncové body, obvykle pomocí různých portů.</span><span class="sxs-lookup"><span data-stu-id="5a9e2-171">That `configuration.json` is where you specify all the API Gateway ReRoutes, meaning the external endpoints with specific ports and the correlated internal endpoints, usually using different ports.</span></span>

```json
{
    "ReRoutes": [],
    "GlobalConfiguration": {}
}
```

<span data-ttu-id="5a9e2-172">Konfigurace má dvě části.</span><span class="sxs-lookup"><span data-stu-id="5a9e2-172">There are two sections to the configuration.</span></span> <span data-ttu-id="5a9e2-173">Pole ReRoutes a GlobalConfiguration.</span><span class="sxs-lookup"><span data-stu-id="5a9e2-173">An array of ReRoutes and a GlobalConfiguration.</span></span> <span data-ttu-id="5a9e2-174">ReRoutes jsou objekty, které říkají Ocelot, jak zacházet s požadavkem upstream.</span><span class="sxs-lookup"><span data-stu-id="5a9e2-174">The ReRoutes are the objects that tell Ocelot how to treat an upstream request.</span></span> <span data-ttu-id="5a9e2-175">Globální konfigurace umožňuje přepsání nastavení specifických pro reroute.</span><span class="sxs-lookup"><span data-stu-id="5a9e2-175">The Global configuration allows overrides of ReRoute specific settings.</span></span> <span data-ttu-id="5a9e2-176">Je to užitečné, pokud nechcete spravovat velké množství nastavení specifických pro ReRoute.</span><span class="sxs-lookup"><span data-stu-id="5a9e2-176">It's useful if you don't want to manage lots of ReRoute specific settings.</span></span>

<span data-ttu-id="5a9e2-177">Tady je zjednodušený příklad [konfiguračního souboru ReRoute](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/ApiGateways/Web.Bff.Shopping/apigw/configuration.json) z jedné z bran rozhraní API z eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="5a9e2-177">Here's a simplified example of [ReRoute configuration file](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/ApiGateways/Web.Bff.Shopping/apigw/configuration.json) from one of the API Gateways from eShopOnContainers.</span></span>

```json
{
  "ReRoutes": [
    {
      "DownstreamPathTemplate": "/api/{version}/{everything}",
      "DownstreamScheme": "http",
      "DownstreamHostAndPorts": [
        {
          "Host": "catalog-api",
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
          "Host": "basket-api",
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

<span data-ttu-id="5a9e2-178">Hlavní funkcí brány rozhraní API Ocelot je převzetí příchozích požadavků HTTP a jejich předání na příjem dat služby, v současné době jako další požadavek HTTP.</span><span class="sxs-lookup"><span data-stu-id="5a9e2-178">The main functionality of an Ocelot API Gateway is to take incoming HTTP requests and forward them on to a downstream service, currently as another HTTP request.</span></span> <span data-ttu-id="5a9e2-179">Ocelot popisuje směrování jednoho požadavku do druhého jako ReRoute.</span><span class="sxs-lookup"><span data-stu-id="5a9e2-179">Ocelot's describes the routing of one request to another as a ReRoute.</span></span>

<span data-ttu-id="5a9e2-180">Například pojďme se zaměřit na jeden z ReRoutes v configuration.json shora, konfigurace pro mikroslužbu košíku.</span><span class="sxs-lookup"><span data-stu-id="5a9e2-180">For instance, let's focus on one of the ReRoutes in the configuration.json from above, the configuration for the Basket microservice.</span></span>

```json
{
      "DownstreamPathTemplate": "/api/{version}/{everything}",
      "DownstreamScheme": "http",
      "DownstreamHostAndPorts": [
        {
          "Host": "basket-api",
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

<span data-ttu-id="5a9e2-181">DownstreamPathTemplate, Scheme a DownstreamHostAndPorts provést adresu URL interní mikroslužby, že tento požadavek bude předán.</span><span class="sxs-lookup"><span data-stu-id="5a9e2-181">The DownstreamPathTemplate, Scheme, and DownstreamHostAndPorts make the internal microservice URL that this request will be forwarded to.</span></span>

<span data-ttu-id="5a9e2-182">Port je vnitřní port používaný službou.</span><span class="sxs-lookup"><span data-stu-id="5a9e2-182">The port is the internal port used by the service.</span></span> <span data-ttu-id="5a9e2-183">Při použití kontejnerů, port zadaný v jeho dockerfile.</span><span class="sxs-lookup"><span data-stu-id="5a9e2-183">When using containers, the port specified at its dockerfile.</span></span>

<span data-ttu-id="5a9e2-184">Jedná `Host` se o název služby, který závisí na překladu názvů služeb, který používáte.</span><span class="sxs-lookup"><span data-stu-id="5a9e2-184">The `Host` is a service name that depends on the service name resolution you are using.</span></span> <span data-ttu-id="5a9e2-185">Při použití docker-compose jsou názvy služeb poskytovány hostitelem Dockeru, který používá názvy služeb poskytované v souborech docker-compose.</span><span class="sxs-lookup"><span data-stu-id="5a9e2-185">When using docker-compose, the services names are provided by the Docker Host, which is using the service names provided in the docker-compose files.</span></span> <span data-ttu-id="5a9e2-186">Pokud používáte orchestrator jako Kubernetes nebo Service Fabric, tento název by měl být vyřešen překladem DNS nebo názvů poskytovaným každým orchestratorem.</span><span class="sxs-lookup"><span data-stu-id="5a9e2-186">If using an orchestrator like Kubernetes or Service Fabric, that name should be resolved by the DNS or name resolution provided by each orchestrator.</span></span>

<span data-ttu-id="5a9e2-187">DownstreamHostAndPorts je pole, které obsahuje hostitele a port všech podřízené služby, které chcete předat požadavky.</span><span class="sxs-lookup"><span data-stu-id="5a9e2-187">DownstreamHostAndPorts is an array that contains the host and port of any downstream services that you wish to forward requests to.</span></span> <span data-ttu-id="5a9e2-188">Obvykle to bude obsahovat pouze jednu položku, ale někdy budete chtít požadavky na vyrovnávání zatížení na vaše služby navazujícím vysílání a Ocelot umožňuje přidat více než jednu položku a pak vybrat vyrovnávání zatížení.</span><span class="sxs-lookup"><span data-stu-id="5a9e2-188">Usually this will just contain one entry but sometimes you might want to load balance requests to your downstream services and Ocelot lets you add more than one entry and then select a load balancer.</span></span> <span data-ttu-id="5a9e2-189">Ale pokud používáte Azure a jakýkoli orchestrátor, je pravděpodobně lepší nápad nazatížení rovnováhy s cloudovou a orchestrator infrastruktury.</span><span class="sxs-lookup"><span data-stu-id="5a9e2-189">But if using Azure and any orchestrator it is probably a better idea to load balance with the cloud and orchestrator infrastructure.</span></span>

<span data-ttu-id="5a9e2-190">UpstreamPathTemplate je adresa URL, kterou Ocelot použije k identifikaci šablony DownstreamPathTemplate, která má být pro daný požadavek od klienta používána.</span><span class="sxs-lookup"><span data-stu-id="5a9e2-190">The UpstreamPathTemplate is the URL that Ocelot will use to identify which DownstreamPathTemplate to use for a given request from the client.</span></span> <span data-ttu-id="5a9e2-191">Nakonec upstreamHttpMethod se používá tak Ocelot můžete rozlišovat mezi různými požadavky (GET, POST, PUT) na stejnou adresu URL.</span><span class="sxs-lookup"><span data-stu-id="5a9e2-191">Finally, the UpstreamHttpMethod is used so Ocelot can distinguish between different requests (GET, POST, PUT) to the same URL.</span></span>

<span data-ttu-id="5a9e2-192">V tomto okamžiku můžete mít jednu bránu Rozhraní API Ocelot (ASP.NET Core WebHost) pomocí jednoho nebo [více sloučených souborů configuration.json](https://ocelot.readthedocs.io/en/latest/features/configuration.html#merging-configuration-files) nebo můžete také uložit [konfiguraci v úložišti Consul KV](https://ocelot.readthedocs.io/en/latest/features/configuration.html#store-configuration-in-consul).</span><span class="sxs-lookup"><span data-stu-id="5a9e2-192">At this point, you could have a single Ocelot API Gateway (ASP.NET Core WebHost) using one or [multiple merged configuration.json files](https://ocelot.readthedocs.io/en/latest/features/configuration.html#merging-configuration-files) or you can also store the [configuration in a Consul KV store](https://ocelot.readthedocs.io/en/latest/features/configuration.html#store-configuration-in-consul).</span></span>

<span data-ttu-id="5a9e2-193">Ale jak je zavedeno v části architektury a návrhu, pokud opravdu chcete mít autonomní mikroslužeb, může být lepší rozdělit tuto jednu monolitickou bránu rozhraní API do více bran rozhraní API a/nebo BFF (Backend pro front-end).</span><span class="sxs-lookup"><span data-stu-id="5a9e2-193">But as introduced in the architecture and design sections, if you really want to have autonomous microservices, it might be better to split that single monolithic API Gateway into multiple API Gateways and/or BFF (Backend for Frontend).</span></span> <span data-ttu-id="5a9e2-194">Za tímto účelem se podívejme, jak implementovat tento přístup s kontejnery Dockeru.</span><span class="sxs-lookup"><span data-stu-id="5a9e2-194">For that purpose, let's see how to implement that approach with Docker containers.</span></span>

### <a name="using-a-single-docker-container-image-to-run-multiple-different-api-gateway--bff-container-types"></a><span data-ttu-id="5a9e2-195">Použití jedné image kontejneru Dockeru ke spuštění několika různých typů kontejnerů brány rozhraní API / BFF</span><span class="sxs-lookup"><span data-stu-id="5a9e2-195">Using a single Docker container image to run multiple different API Gateway / BFF container types</span></span>

<span data-ttu-id="5a9e2-196">V eShopOnContainers používáme jednu bitovou kopii kontejneru Dockeru s bránou rozhraní API Ocelot, ale pak za běhu vytvoříme různé služby/kontejnery pro každý typ brány ROZHRANÍ API/BFF tím, že poskytujeme jiný soubor configuration.json pomocí svazku dockeru pro přístup k jiné složce PC pro každou službu.</span><span class="sxs-lookup"><span data-stu-id="5a9e2-196">In eShopOnContainers, we're using a single Docker container image with the Ocelot API Gateway but then, at run time, we create different services/containers for each type of API-Gateway/BFF by providing a different configuration.json file, using a docker volume to access a different PC folder for each service.</span></span>

![Diagram jedné image Dockeru brány Ocelot pro všechny brány rozhraní API.](./media/implement-api-gateways-with-ocelot/reusing-single-ocelot-docker-image.png)

<span data-ttu-id="5a9e2-198">**Obrázek 6-33**.</span><span class="sxs-lookup"><span data-stu-id="5a9e2-198">**Figure 6-33**.</span></span> <span data-ttu-id="5a9e2-199">Opětovné použití jedné bitové kopie Ocelot Docker u více typů brány rozhraní API</span><span class="sxs-lookup"><span data-stu-id="5a9e2-199">Reusing a single Ocelot Docker image across multiple API Gateway types</span></span>

<span data-ttu-id="5a9e2-200">V eShopOnContainers je "Obecný Obrázek Docker u brány Rozhraní API" vytvořen s projektem s názvem OcelotApiGw a názvem obrázku "eshop/ocelotapigw", který je zadán v souboru docker-compose.yml.</span><span class="sxs-lookup"><span data-stu-id="5a9e2-200">In eShopOnContainers, the "Generic Ocelot API Gateway Docker Image" is created with the project named 'OcelotApiGw' and the image name "eshop/ocelotapigw" that is specified in the docker-compose.yml file.</span></span> <span data-ttu-id="5a9e2-201">Potom při nasazování do Dockeru budou čtyři kontejnery brány ROZHRANÍ API vytvořené ze stejné image Dockeru, jak je znázorněno na následujícím výňatku ze souboru docker-compose.yml.</span><span class="sxs-lookup"><span data-stu-id="5a9e2-201">Then, when deploying to Docker, there will be four API-Gateway containers created from that same Docker image, as shown in the following extract from the docker-compose.yml file.</span></span>

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

<span data-ttu-id="5a9e2-202">Navíc, jak můžete vidět v následujícím souboru docker-compose.override.yml, jediný rozdíl mezi těmito kontejnery brány rozhraní API je konfigurační soubor Ocelot, který se liší pro každý kontejner služby a je určen za běhu prostřednictvím Svazek Dockeru.</span><span class="sxs-lookup"><span data-stu-id="5a9e2-202">Additionally, as you can see in the following docker-compose.override.yml file, the only difference between those API Gateway containers is the Ocelot configuration file, which is different for each service container and it's specified at runtime through a Docker volume.</span></span>

```yml
mobileshoppingapigw:
  environment:
    - ASPNETCORE_ENVIRONMENT=Development
    - IdentityUrl=http://identity-api
  ports:
    - "5200:80"
  volumes:
    - ./src/ApiGateways/Mobile.Bff.Shopping/apigw:/app/configuration

mobilemarketingapigw:
  environment:
    - ASPNETCORE_ENVIRONMENT=Development
    - IdentityUrl=http://identity-api
  ports:
    - "5201:80"
  volumes:
    - ./src/ApiGateways/Mobile.Bff.Marketing/apigw:/app/configuration

webshoppingapigw:
  environment:
    - ASPNETCORE_ENVIRONMENT=Development
    - IdentityUrl=http://identity-api
  ports:
    - "5202:80"
  volumes:
    - ./src/ApiGateways/Web.Bff.Shopping/apigw:/app/configuration

webmarketingapigw:
  environment:
    - ASPNETCORE_ENVIRONMENT=Development
    - IdentityUrl=http://identity-api
  ports:
    - "5203:80"
  volumes:
    - ./src/ApiGateways/Web.Bff.Marketing/apigw:/app/configuration
```

<span data-ttu-id="5a9e2-203">Z důvodu předchozího kódu a jak je znázorněno v průzkumníku Sady Visual Studio níže, jediný soubor potřebný k definování každé konkrétní obchodní/BFF brány rozhraní API je pouze configuration.json soubor, protože čtyři brány rozhraní API jsou založeny na stejné image Dockeru.</span><span class="sxs-lookup"><span data-stu-id="5a9e2-203">Because of that previous code, and as shown in the Visual Studio Explorer below, the only file needed to define each specific business/BFF API Gateway is just a configuration.json file, because the four API Gateways are based on the same Docker image.</span></span>

![Snímek obrazovky zobrazující všechny brány rozhraní API se soubory configuration.json](./media/implement-api-gateways-with-ocelot/ocelot-configuration-files.png)

<span data-ttu-id="5a9e2-205">**Obrázek 6-34**.</span><span class="sxs-lookup"><span data-stu-id="5a9e2-205">**Figure 6-34**.</span></span> <span data-ttu-id="5a9e2-206">Jediný soubor potřebný k definování každé brány ROZHRANÍ API / BFF s Ocelotem je konfigurační soubor</span><span class="sxs-lookup"><span data-stu-id="5a9e2-206">The only file needed to define each API Gateway / BFF with Ocelot is a configuration file</span></span>

<span data-ttu-id="5a9e2-207">Rozdělením brány rozhraní API do více bran rozhraní API mohou různé vývojové týmy zaměřené na různé podmnožiny mikroslužeb spravovat své vlastní brány rozhraní API pomocí nezávislých konfiguračních souborů Ocelot.</span><span class="sxs-lookup"><span data-stu-id="5a9e2-207">By splitting the API Gateway into multiple API Gateways, different development teams focusing on different subsets of microservices can manage their own API Gateways by using independent Ocelot configuration files.</span></span> <span data-ttu-id="5a9e2-208">Navíc mohou současně znovu použít stejnou image Ocelot Docker.</span><span class="sxs-lookup"><span data-stu-id="5a9e2-208">Plus, at the same time they can reuse the same Ocelot Docker image.</span></span>

<span data-ttu-id="5a9e2-209">Nyní, pokud spustíte eShopOnContainers s bránami rozhraní API (zahrnuty ve výchozím nastavení ve VS při otevírání eShopOnContainers-ServicesAndWebApps.sln řešení, nebo pokud běží "docker-compose up"), budou provedeny následující ukázkové trasy.</span><span class="sxs-lookup"><span data-stu-id="5a9e2-209">Now, if you run eShopOnContainers with the API Gateways (included by default in VS when opening eShopOnContainers-ServicesAndWebApps.sln solution or if running "docker-compose up"), the following sample routes will be performed.</span></span>

<span data-ttu-id="5a9e2-210">Například při návštěvě upstream `http://localhost:5202/api/v1/c/catalog/items/2/` URL obsluhované webshoppingapigw API Gateway, dostanete stejný výsledek `http://catalog-api/api/v1/2` z interní downstream URL v rámci hostitele Dockeru, jako v následujícím prohlížeči.</span><span class="sxs-lookup"><span data-stu-id="5a9e2-210">For instance, when visiting the upstream URL `http://localhost:5202/api/v1/c/catalog/items/2/` served by the webshoppingapigw API Gateway, you get the same result from the internal Downstream URL `http://catalog-api/api/v1/2` within the Docker host, as in the following browser.</span></span>

![Snímek obrazovky s prohlížečem zobrazujícím odpověď procházející bránou rozhraní API](./media/implement-api-gateways-with-ocelot/access-microservice-through-url.png)

<span data-ttu-id="5a9e2-212">**Obrázek 6-35**.</span><span class="sxs-lookup"><span data-stu-id="5a9e2-212">**Figure 6-35**.</span></span> <span data-ttu-id="5a9e2-213">Přístup k mikroslužbě prostřednictvím adresy URL poskytované bránou rozhraní API</span><span class="sxs-lookup"><span data-stu-id="5a9e2-213">Accessing a microservice through a URL provided by the API Gateway</span></span>

<span data-ttu-id="5a9e2-214">Z důvodů testování nebo ladění, pokud jste chtěli přímý přístup ke kontejneru Katalog Docker (pouze ve vývojovém prostředí) bez průchodu bránou rozhraní API, protože 'catalog-api' je interní překlad DNS pro hostitele Dockeru (zjišťování služby zpracované názvy služeb docker-compose), jediný způsob, jak `http://localhost:5101/api/v1/Catalog/items/1` přímo přistupovat ke kontejneru, je prostřednictvím externího portu publikovaného v docker-compose.override.yml, který je k dispozici pouze pro vývojové testy, například v následujícím prohlížeči.</span><span class="sxs-lookup"><span data-stu-id="5a9e2-214">Because of testing or debugging reasons, if you wanted to directly access to the Catalog Docker container (only at the development environment) without passing through the API Gateway, since 'catalog-api' is a DNS resolution internal to the Docker host (service discovery handled by docker-compose service names), the only way to directly access the container is through the external port published in the docker-compose.override.yml, which is provided only for development tests, such as `http://localhost:5101/api/v1/Catalog/items/1` in the following browser.</span></span>

![Snímek obrazovky prohlížeče zobrazující přímou odpověď na soubor Catalog.api](./media/implement-api-gateways-with-ocelot/direct-access-microservice-testing.png)

<span data-ttu-id="5a9e2-216">**Obrázek 6-36**.</span><span class="sxs-lookup"><span data-stu-id="5a9e2-216">**Figure 6-36**.</span></span> <span data-ttu-id="5a9e2-217">Přímý přístup k mikroslužbě pro testovací účely</span><span class="sxs-lookup"><span data-stu-id="5a9e2-217">Direct access to a microservice for testing purposes</span></span>

<span data-ttu-id="5a9e2-218">Ale aplikace je nakonfigurovántak, aby přistupuje ke všem mikroslužeb prostřednictvím brány rozhraní API, ne i když přímý port "zkratky".</span><span class="sxs-lookup"><span data-stu-id="5a9e2-218">But the application is configured so it accesses all the microservices through the API Gateways, not though the direct port "shortcuts".</span></span>

### <a name="the-gateway-aggregation-pattern-in-eshoponcontainers"></a><span data-ttu-id="5a9e2-219">Vzor agregace brány v eShopOnContainers</span><span class="sxs-lookup"><span data-stu-id="5a9e2-219">The Gateway aggregation pattern in eShopOnContainers</span></span>

<span data-ttu-id="5a9e2-220">Jak bylo zavedeno dříve, flexibilní způsob implementace požadavků agregace je s vlastní služby, podle kódu.</span><span class="sxs-lookup"><span data-stu-id="5a9e2-220">As introduced previously, a flexible way to implement requests aggregation is with custom services, by code.</span></span> <span data-ttu-id="5a9e2-221">Můžete také implementovat agregaci požadavků pomocí [funkce Agregace požadavků v Ocelotu](https://ocelot.readthedocs.io/en/latest/features/requestaggregation.html#request-aggregation), ale nemusí být tak flexibilní, jak potřebujete.</span><span class="sxs-lookup"><span data-stu-id="5a9e2-221">You could also implement request aggregation with the [Request Aggregation feature in Ocelot](https://ocelot.readthedocs.io/en/latest/features/requestaggregation.html#request-aggregation), but it might not be as flexible as you need.</span></span> <span data-ttu-id="5a9e2-222">Proto je vybraný způsob implementace agregace v eShopOnContainers s explicitní ASP.NET služby Core Web API pro každý agregátor.</span><span class="sxs-lookup"><span data-stu-id="5a9e2-222">Therefore, the selected way to implement aggregation in eShopOnContainers is with an explicit ASP.NET Core Web API service for each aggregator.</span></span>

<span data-ttu-id="5a9e2-223">Podle tohoto přístupu je diagram složení brány rozhraní API ve skutečnosti o něco rozšířenější při zvažování služeb agregátoru, které nejsou zobrazeny ve zjednodušeném diagramu globální architektury, který byl zobrazen dříve.</span><span class="sxs-lookup"><span data-stu-id="5a9e2-223">According to that approach, the API Gateway composition diagram is in reality a bit more extended when considering the aggregator services that are not shown in the simplified global architecture diagram shown previously.</span></span>

<span data-ttu-id="5a9e2-224">V následujícím diagramu můžete také zobrazit, jak služby agregátoru pracují s jejich souvisejícíbrány rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="5a9e2-224">In the following diagram, you can also see how the aggregator services work with their related API Gateways.</span></span>

![Diagram architektury eShopOnContainers znázorňující agregátorové služby.](./media/implement-api-gateways-with-ocelot/eshoponcontainers-architecture-aggregator-services.png)

<span data-ttu-id="5a9e2-226">**Obrázek 6-37**.</span><span class="sxs-lookup"><span data-stu-id="5a9e2-226">**Figure 6-37**.</span></span> <span data-ttu-id="5a9e2-227">architektura eShopOnContainers s agregátorovými službami</span><span class="sxs-lookup"><span data-stu-id="5a9e2-227">eShopOnContainers architecture with aggregator services</span></span>

<span data-ttu-id="5a9e2-228">Dalším přiblížením v obchodní oblasti "Nakupování" na následujícím obrázku uvidíte, že chattiness mezi klientskými aplikacemi a mikroslužbami se snižuje při použití agregátorových služeb v gatewayrozhraní API.</span><span class="sxs-lookup"><span data-stu-id="5a9e2-228">Zooming in further, on the "Shopping" business area in the following image, you can see that chattiness between the client apps and the microservices is reduced when using the aggregator services in the API Gateways.</span></span>

![Diagram znázorňující přiblížení architektury eShopOnContainers.](./media/implement-api-gateways-with-ocelot/zoom-in-vision-aggregator-services.png)

<span data-ttu-id="5a9e2-230">**Obrázek 6-38**.</span><span class="sxs-lookup"><span data-stu-id="5a9e2-230">**Figure 6-38**.</span></span> <span data-ttu-id="5a9e2-231">Zvětšete vizi agregátorových služeb</span><span class="sxs-lookup"><span data-stu-id="5a9e2-231">Zoom in vision of the Aggregator services</span></span>

<span data-ttu-id="5a9e2-232">Můžete si všimnout, jak když diagram zobrazuje možné požadavky pocházející z brány rozhraní API může získat složité.</span><span class="sxs-lookup"><span data-stu-id="5a9e2-232">You can notice how when the diagram shows the possible requests coming from the API Gateways it can get complex.</span></span> <span data-ttu-id="5a9e2-233">I když můžete vidět, jak by se šipky v modré barvě zjednodušily, z pohledu klientských aplikací, při použití vzoru agregátoru snížením chattiness a latence v komunikaci, což v konečném důsledku výrazně zlepšuje uživatelské prostředí pro vzdálené aplikace ( mobilní a SPA), zejména.</span><span class="sxs-lookup"><span data-stu-id="5a9e2-233">Although you can see how the arrows in blue would be simplified, from a client apps perspective, when using the aggregator pattern by reducing chattiness and latency in the communication, ultimately significantly improving the user experience for the remote apps (mobile and SPA apps), especially.</span></span>

<span data-ttu-id="5a9e2-234">V případě obchodní oblasti "Marketing" a mikroslužeb se jedná o jednoduchý případ použití, takže nebylo nutné používat agregátory, ale v případě potřeby by to mohlo být také možné.</span><span class="sxs-lookup"><span data-stu-id="5a9e2-234">In the case of the "Marketing" business area and microservices, it is a simple use case so there was no need to use aggregators, but it could also be possible, if needed.</span></span>

### <a name="authentication-and-authorization-in-ocelot-api-gateways"></a><span data-ttu-id="5a9e2-235">Ověřování a autorizace v branách rozhraní API Ocelot</span><span class="sxs-lookup"><span data-stu-id="5a9e2-235">Authentication and authorization in Ocelot API Gateways</span></span>

<span data-ttu-id="5a9e2-236">V bráně rozhraní API Ocelot můžete sedět ověřovací služby, jako je například ASP.NET služby Core Web API pomocí [IdentityServer](https://identityserver.io/) poskytující ověřovací token, a to buď ven nebo uvnitř brány rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="5a9e2-236">In an Ocelot API Gateway you can sit the authentication service, such as an ASP.NET Core Web API service using [IdentityServer](https://identityserver.io/) providing the auth token, either out or inside the API Gateway.</span></span>

<span data-ttu-id="5a9e2-237">Vzhledem k tomu, že eShopOnContainers používá více bran rozhraní API s hranicemi založenými na BFF a obchodních oblastech, služba Identity/Auth je vynechána z bran rozhraní API, jak je zvýrazněno žlutě v následujícím diagramu.</span><span class="sxs-lookup"><span data-stu-id="5a9e2-237">Since eShopOnContainers is using multiple API Gateways with boundaries based on BFF and business areas, the Identity/Auth service is left out of the API Gateways, as highlighted in yellow in the following diagram.</span></span>

![Diagram znázorňující mikroslužbu Identity pod bránou rozhraní API.](./media/implement-api-gateways-with-ocelot/eshoponcontainers-identity-service-position.png)

<span data-ttu-id="5a9e2-239">**Obrázek 6-39**.</span><span class="sxs-lookup"><span data-stu-id="5a9e2-239">**Figure 6-39**.</span></span> <span data-ttu-id="5a9e2-240">Pozice služby Identity v eShopOnContainers</span><span class="sxs-lookup"><span data-stu-id="5a9e2-240">Position of the Identity service in eShopOnContainers</span></span>

<span data-ttu-id="5a9e2-241">Ocelot však také podporuje sedící mikroslužbu Identity/Auth v rámci hranice brány rozhraní API, jako v tomto jiném diagramu.</span><span class="sxs-lookup"><span data-stu-id="5a9e2-241">However, Ocelot also supports sitting the Identity/Auth microservice within the API Gateway boundary, as in this other diagram.</span></span>

![Diagram znázorňující ověřování v bráně rozhraní API Ocelot.](./media/implement-api-gateways-with-ocelot/ocelot-authentication.png)

<span data-ttu-id="5a9e2-243">**Obrázek 6-40**.</span><span class="sxs-lookup"><span data-stu-id="5a9e2-243">**Figure 6-40**.</span></span> <span data-ttu-id="5a9e2-244">Autentizace v Ocelotu</span><span class="sxs-lookup"><span data-stu-id="5a9e2-244">Authentication in Ocelot</span></span>

<span data-ttu-id="5a9e2-245">Jak ukazuje předchozí diagram, když je mikroslužba Identity pod bránou rozhraní API (AG): 1) AG požaduje auth token z mikroslužby identity, 2) Mikroslužba identity vrátí token AG, 3-4) AG požadavky z mikroslužeb pomocí tokenu ověření.</span><span class="sxs-lookup"><span data-stu-id="5a9e2-245">As the previous diagram shows, when the Identity microservice is beneath the API gateway (AG): 1) AG requests an auth token from identity microservice, 2) The identity microservice returns token to AG, 3-4) AG requests from microservices using the auth token.</span></span> <span data-ttu-id="5a9e2-246">Vzhledem k tomu, že aplikace eShopOnContainers rozdělila bránu rozhraní API na více bff (Backend pro front-end) a obchodní oblasti brány rozhraní API, další možností by bylo vytvořit další bránu rozhraní API pro průřezové obavy.</span><span class="sxs-lookup"><span data-stu-id="5a9e2-246">Because eShopOnContainers application has split the API Gateway into multiple BFF (Backend for Frontend) and business areas API Gateways, another option would have been to create an additional API Gateway for cross-cutting concerns.</span></span> <span data-ttu-id="5a9e2-247">Tato volba by byla spravedlivá ve složitější architektuře založené na mikroslužbách s více průřezovými obavami mikroslužeb.</span><span class="sxs-lookup"><span data-stu-id="5a9e2-247">That choice would be fair in a more complex microservice based architecture with multiple cross-cutting concerns microservices.</span></span> <span data-ttu-id="5a9e2-248">Vzhledem k tomu, že v eShopOnContainers existuje pouze jeden průřezový problém, bylo rozhodnuto, že bude pouze zpracovávat bezpečnostní službu z oblasti brány ROZHRANÍ API, pro jednoduchost.</span><span class="sxs-lookup"><span data-stu-id="5a9e2-248">Since there's only one cross-cutting concern in eShopOnContainers, it was decided to just handle the security service out of the API Gateway realm, for simplicity's sake.</span></span>

<span data-ttu-id="5a9e2-249">V každém případě pokud je aplikace zabezpečená na úrovni brány rozhraní API, ověřovací modul brány rozhraní API Ocelot je nejprve navštíven při pokusu o použití jakékoli zabezpečené mikroslužby.</span><span class="sxs-lookup"><span data-stu-id="5a9e2-249">In any case, if the app is secured at the API Gateway level, the authentication module of the Ocelot API Gateway is visited at first when trying to use any secured microservice.</span></span> <span data-ttu-id="5a9e2-250">To přesměruje požadavek HTTP na návštěvu identity nebo ověření mikroslužby získat přístupový token, takže můžete navštívit chráněné služby s access_token.</span><span class="sxs-lookup"><span data-stu-id="5a9e2-250">That redirects the HTTP request to visit the Identity or auth microservice to get the access token so you can visit the protected services with the access_token.</span></span>

<span data-ttu-id="5a9e2-251">Způsob zabezpečení s ověřováním libovolné služby na úrovni brány rozhraní API je nastavení authenticationProviderKey v souvisejícínastavení na configuration.json.</span><span class="sxs-lookup"><span data-stu-id="5a9e2-251">The way you secure with authentication any service at the API Gateway level is by setting the AuthenticationProviderKey in its related settings at the configuration.json.</span></span>

```json
    {
      "DownstreamPathTemplate": "/api/{version}/{everything}",
      "DownstreamScheme": "http",
      "DownstreamHostAndPorts": [
        {
          "Host": "basket-api",
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

<span data-ttu-id="5a9e2-252">Při spuštění Ocelot, se podíváme na ReRoutes AuthenticationOptions.AuthenticationProviderKey a zkontrolujte, zda je u daného klíče registrován poskytovatel ověřování.</span><span class="sxs-lookup"><span data-stu-id="5a9e2-252">When Ocelot runs, it will look at the ReRoutes AuthenticationOptions.AuthenticationProviderKey and check that there is an Authentication Provider registered with the given key.</span></span> <span data-ttu-id="5a9e2-253">Pokud není, pak Ocelot nezačne.</span><span class="sxs-lookup"><span data-stu-id="5a9e2-253">If there isn't, then Ocelot will not start up.</span></span> <span data-ttu-id="5a9e2-254">Pokud existuje, pak ReRoute bude používat tohoto zprostředkovatele při spuštění.</span><span class="sxs-lookup"><span data-stu-id="5a9e2-254">If there is, then the ReRoute will use that provider when it executes.</span></span>

<span data-ttu-id="5a9e2-255">Vzhledem k tomu, že Ocelot WebHost je nakonfigurován s `authenticationProviderKey = "IdentityApiKey"`, které budou vyžadovat ověření vždy, když tato služba má nějaké požadavky bez tokenu ověření.</span><span class="sxs-lookup"><span data-stu-id="5a9e2-255">Because the Ocelot WebHost is configured with the `authenticationProviderKey = "IdentityApiKey"`, that will require authentication whenever that service has any requests without any auth token.</span></span>

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

<span data-ttu-id="5a9e2-256">Potom je také nutné nastavit autorizaci s atributem [Authorize] na libovolném prostředku, ke kterým má být přistupovat jako mikroslužby, například v následujícím řadiči mikroslužeb košíku.</span><span class="sxs-lookup"><span data-stu-id="5a9e2-256">Then, you also need to set authorization with the [Authorize] attribute on any resource to be accessed like the microservices, such as in the following Basket microservice controller.</span></span>

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

<span data-ttu-id="5a9e2-257">ValidAudiences jako "košík" jsou korelovány s publikem `AddJwtBearer()` definované v každé mikroslužbě s na ConfigureServices() třídy Startup, například v kódu níže.</span><span class="sxs-lookup"><span data-stu-id="5a9e2-257">The ValidAudiences such as "basket" are correlated with the audience defined in each microservice with `AddJwtBearer()` at the ConfigureServices() of the Startup class, such as in the code below.</span></span>

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

<span data-ttu-id="5a9e2-258">Pokud se pokusíte o přístup k jakékoli zabezpečené mikroslužby, jako je `http://localhost:5202/api/v1/b/basket/1`mikroslužba košíku s reroute adresu URL na základě brány rozhraní API jako , pak dostanete 401 neoprávněné, pokud zadáte platný token.</span><span class="sxs-lookup"><span data-stu-id="5a9e2-258">If you try to access any secured microservice, like the Basket microservice with a ReRoute URL based on the API Gateway like `http://localhost:5202/api/v1/b/basket/1`, then you'll get a 401 Unauthorized unless you provide a valid token.</span></span> <span data-ttu-id="5a9e2-259">Na druhou stranu pokud je ověřena adresa URL ReRoute, Ocelot vyvolá jakékoli podřízené schéma, které je s ním spojeno (adresa URL interní mikroslužby).</span><span class="sxs-lookup"><span data-stu-id="5a9e2-259">On the other hand, if a ReRoute URL is authenticated, Ocelot will invoke whatever downstream scheme is associated with it (the internal microservice URL).</span></span>

<span data-ttu-id="5a9e2-260">**Autorizace na úrovni ReRoutes společnosti Ocelot.**</span><span class="sxs-lookup"><span data-stu-id="5a9e2-260">**Authorization at Ocelot's ReRoutes tier.**</span></span>  <span data-ttu-id="5a9e2-261">Ocelot podporuje autorizaci založenou na deklaracích identity vyhodnocenou po ověření.</span><span class="sxs-lookup"><span data-stu-id="5a9e2-261">Ocelot supports claims-based authorization evaluated after the authentication.</span></span> <span data-ttu-id="5a9e2-262">Autorizaci nastavíte na úrovni postupu přidáním následujících řádků do konfigurace ReRoute.</span><span class="sxs-lookup"><span data-stu-id="5a9e2-262">You set the authorization at a route level by adding the following lines to the ReRoute configuration.</span></span>

```json
"RouteClaimsRequirement": {
    "UserType": "employee"
}
```

<span data-ttu-id="5a9e2-263">V tomto příkladu při volání autorizace middleware Ocelot zjistí, zda uživatel má typ deklarace "UserType" v tokenu a pokud je hodnota této deklarace "zaměstnanec".</span><span class="sxs-lookup"><span data-stu-id="5a9e2-263">In that example, when the authorization middleware is called, Ocelot will find if the user has the claim type 'UserType' in the token and if the value of that claim is 'employee'.</span></span> <span data-ttu-id="5a9e2-264">Pokud tomu tak není, pak uživatel nebude autorizován a odpověď bude zakázána 403.</span><span class="sxs-lookup"><span data-stu-id="5a9e2-264">If it isn't, then the user will not be authorized and the response will be 403 forbidden.</span></span>

## <a name="using-kubernetes-ingress-plus-ocelot-api-gateways"></a><span data-ttu-id="5a9e2-265">Použití kubernetes ingress plus Ocelot API brány</span><span class="sxs-lookup"><span data-stu-id="5a9e2-265">Using Kubernetes Ingress plus Ocelot API Gateways</span></span>

<span data-ttu-id="5a9e2-266">Při použití Kubernetes (jako v clusteru služby Azure Kubernetes) obvykle sjednocujete všechny požadavky HTTP prostřednictvím [úrovně Kubernetes Ingress](https://kubernetes.io/docs/concepts/services-networking/ingress/) založené na *Nginx*.</span><span class="sxs-lookup"><span data-stu-id="5a9e2-266">When using Kubernetes (like in an Azure Kubernetes Service cluster), you usually unify all the HTTP requests through the [Kubernetes Ingress tier](https://kubernetes.io/docs/concepts/services-networking/ingress/) based on *Nginx*.</span></span>

<span data-ttu-id="5a9e2-267">V Kubernetes, pokud nepoužíváte žádný přístup příchozího přenosu dat, pak vaše služby a pody mají IP adresy pouze směrovatelné v síti clusteru.</span><span class="sxs-lookup"><span data-stu-id="5a9e2-267">In Kubernetes, if you don't use any ingress approach, then your services and pods have IPs only routable by the cluster network.</span></span>

<span data-ttu-id="5a9e2-268">Ale pokud používáte přístup příchozího přenosu dat, budete mít střední vrstvu mezi Internetem a vašimi službami (včetně vašich bran rozhraní API), která funguje jako reverzní proxy server.</span><span class="sxs-lookup"><span data-stu-id="5a9e2-268">But if you use an ingress approach, you'll have a middle tier between the Internet and your services (including your API Gateways), acting as a reverse proxy.</span></span>

<span data-ttu-id="5a9e2-269">Jako definice příchozí přenos dat je kolekce pravidel, která umožňují příchozí připojení k dosažení clusterových služeb.</span><span class="sxs-lookup"><span data-stu-id="5a9e2-269">As a definition, an Ingress is a collection of rules that allow inbound connections to reach the cluster services.</span></span> <span data-ttu-id="5a9e2-270">Příchozí přenos dat je obvykle nakonfigurován tak, aby poskytoval služby externě dosažitelné adresy URL, provoz vyvažování zatížení, ukončení SSL a další.</span><span class="sxs-lookup"><span data-stu-id="5a9e2-270">An ingress is usually configured to provide services externally reachable URLs, load balance traffic, SSL termination and more.</span></span> <span data-ttu-id="5a9e2-271">Uživatelé požadují příchozí přenos dat posting ingress prostředku na server rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="5a9e2-271">Users request ingress by POSTing the Ingress resource to the API server.</span></span>

<span data-ttu-id="5a9e2-272">V eShopOnContainers při vývoji místně a pomocí pouze váš vývojový počítač jako hostitele Dockeru, nepoužíváte žádné příchozí přenos dat, ale pouze více bran rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="5a9e2-272">In eShopOnContainers, when developing locally and using just your development machine as the Docker host, you are not using any ingress but only the multiple API Gateways.</span></span>

<span data-ttu-id="5a9e2-273">Však při cílení "produkční" prostředí založené na Kubernetes, eShopOnContainers používá příchozí přenos dat před brány rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="5a9e2-273">However, when targeting a "production" environment based on Kubernetes, eShopOnContainers is using an ingress in front of the API gateways.</span></span> <span data-ttu-id="5a9e2-274">Tímto způsobem klienti stále volat stejnou základní adresu URL, ale požadavky jsou směrovány do více bran rozhraní API nebo BFF.</span><span class="sxs-lookup"><span data-stu-id="5a9e2-274">That way, the clients still call the same base URL but the requests are routed to multiple API Gateways or BFF.</span></span>

<span data-ttu-id="5a9e2-275">Brány rozhraní API jsou front-endy nebo fasády, které vynořují pouze služby, ale ne webové aplikace, které jsou obvykle mimo jejich rozsah.</span><span class="sxs-lookup"><span data-stu-id="5a9e2-275">API Gateways are front-ends or façades surfacing only the services but not the web applications that are usually out of their scope.</span></span> <span data-ttu-id="5a9e2-276">Kromě toho brány rozhraní API může skrýt některé interní mikroslužeb.</span><span class="sxs-lookup"><span data-stu-id="5a9e2-276">In addition, the API Gateways might hide certain internal microservices.</span></span>

<span data-ttu-id="5a9e2-277">Příchozí přenos dat je však pouze přesměrování požadavků HTTP, ale ne snaží skrýt žádné mikroslužby nebo webové aplikace.</span><span class="sxs-lookup"><span data-stu-id="5a9e2-277">The ingress, however, is just redirecting HTTP requests but not trying to hide any microservice or web app.</span></span>

<span data-ttu-id="5a9e2-278">S ingress Nginx vrstvy v Kubernetes před webových aplikací plus několik Ocelot API brány / BFF je ideální architektura, jak je znázorněno na následujícím diagramu.</span><span class="sxs-lookup"><span data-stu-id="5a9e2-278">Having an ingress Nginx tier in Kubernetes in front of the web applications plus the several Ocelot API Gateways / BFF is the ideal architecture, as shown in the following diagram.</span></span>

![Diagram znázorňující, jak úroveň příchozího přenosu dat zapadá do prostředí AKS.](./media/implement-api-gateways-with-ocelot/eshoponcontainer-ingress-tier.png)

<span data-ttu-id="5a9e2-280">**Obrázek 6-41**.</span><span class="sxs-lookup"><span data-stu-id="5a9e2-280">**Figure 6-41**.</span></span> <span data-ttu-id="5a9e2-281">Ingress vrstva v eShopOnContainers při nasazení do Kubernetes</span><span class="sxs-lookup"><span data-stu-id="5a9e2-281">The ingress tier in eShopOnContainers when deployed into Kubernetes</span></span>

<span data-ttu-id="5a9e2-282">Příchozí přenos dat Kubernetes funguje jako reverzní proxy pro veškerý provoz do aplikace, včetně webových aplikací, které jsou obvykle mimo obor brány rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="5a9e2-282">A Kubernetes Ingress acts as a reverse proxy for all traffic to the app, including the web applications, that are usually out of the Api gateway scope.</span></span> <span data-ttu-id="5a9e2-283">Když nasadíte eShopOnContainers do Kubernetes, zpřístupní jen několik služeb nebo koncových bodů prostřednictvím _příchozího přenosu dat_, v podstatě následující seznam příponek na adresách URL:</span><span class="sxs-lookup"><span data-stu-id="5a9e2-283">When you deploy eShopOnContainers into Kubernetes, it exposes just a few services or endpoints via _ingress_, basically the following list of postfixes on the URLs:</span></span>

- <span data-ttu-id="5a9e2-284">`/`pro klientskou webovou aplikaci SPA</span><span class="sxs-lookup"><span data-stu-id="5a9e2-284">`/` for the client SPA web application</span></span>
- <span data-ttu-id="5a9e2-285">`/webmvc`pro klientskou webovou aplikaci MVC</span><span class="sxs-lookup"><span data-stu-id="5a9e2-285">`/webmvc` for the client MVC web application</span></span>
- <span data-ttu-id="5a9e2-286">`/webstatus`pro klientskou webovou aplikaci zobrazující stav/kontroly stavu</span><span class="sxs-lookup"><span data-stu-id="5a9e2-286">`/webstatus` for the client web app showing the status/healthchecks</span></span>
- <span data-ttu-id="5a9e2-287">`/webshoppingapigw`pro web BFF a nákupní obchodní procesy</span><span class="sxs-lookup"><span data-stu-id="5a9e2-287">`/webshoppingapigw` for the web BFF and shopping business processes</span></span>
- <span data-ttu-id="5a9e2-288">`/webmarketingapigw`pro web BFF a marketingové obchodní procesy</span><span class="sxs-lookup"><span data-stu-id="5a9e2-288">`/webmarketingapigw` for the web BFF and marketing business processes</span></span>
- <span data-ttu-id="5a9e2-289">`/mobileshoppingapigw`pro mobilní BFF a nákupní obchodní procesy</span><span class="sxs-lookup"><span data-stu-id="5a9e2-289">`/mobileshoppingapigw` for the mobile BFF and shopping business processes</span></span>
- <span data-ttu-id="5a9e2-290">`/mobilemarketingapigw`pro mobilní BFF a marketingové obchodní procesy</span><span class="sxs-lookup"><span data-stu-id="5a9e2-290">`/mobilemarketingapigw` for the mobile BFF and marketing business processes</span></span>

<span data-ttu-id="5a9e2-291">Při nasazování do Kubernetes, každý Ocelot API Gateway používá jiný soubor "configuration.json" pro každý _pod_ běží brány rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="5a9e2-291">When deploying to Kubernetes, each Ocelot API Gateway is using a different "configuration.json" file for each _pod_ running the API Gateways.</span></span> <span data-ttu-id="5a9e2-292">Tyto soubory "configuration.json" jsou poskytovány připojením (původně se skriptem deploy.ps1) svazku vytvořeného na základě _konfigurační mapy_ Kubernetes s názvem "ocelot".</span><span class="sxs-lookup"><span data-stu-id="5a9e2-292">Those "configuration.json" files are provided by mounting (originally with the deploy.ps1 script) a volume created based on a Kubernetes _config map_ named ‘ocelot'.</span></span> <span data-ttu-id="5a9e2-293">Každý kontejner připojí svůj související konfigurační `/app/configuration`soubor do složky kontejneru s názvem .</span><span class="sxs-lookup"><span data-stu-id="5a9e2-293">Each container mounts its related configuration file in the container's folder named `/app/configuration`.</span></span>

<span data-ttu-id="5a9e2-294">Ve zdrojových kódech eShopOnContainers lze původní soubory "configuration.json" `k8s/ocelot/` nalézt ve složce.</span><span class="sxs-lookup"><span data-stu-id="5a9e2-294">In the source code files of eShopOnContainers, the original "configuration.json" files can be found within the `k8s/ocelot/` folder.</span></span> <span data-ttu-id="5a9e2-295">Je tu jeden soubor pro každý BFF/APIGateway.</span><span class="sxs-lookup"><span data-stu-id="5a9e2-295">There's one file for each BFF/APIGateway.</span></span>

## <a name="additional-cross-cutting-features-in-an-ocelot-api-gateway"></a><span data-ttu-id="5a9e2-296">Další průřezové funkce v bráně API Ocelot</span><span class="sxs-lookup"><span data-stu-id="5a9e2-296">Additional cross-cutting features in an Ocelot API Gateway</span></span>

<span data-ttu-id="5a9e2-297">Existují další důležité funkce pro výzkum a použití, při použití Brány rozhraní API Ocelot, popsané v následujících odkazech.</span><span class="sxs-lookup"><span data-stu-id="5a9e2-297">There are other important features to research and use, when using an Ocelot API Gateway, described in the following links.</span></span>

- <span data-ttu-id="5a9e2-298">**Zjišťování služeb na straně klienta integrující Ocelot s konzulem nebo Eurekou** </span><span class="sxs-lookup"><span data-stu-id="5a9e2-298">**Service discovery in the client side integrating Ocelot with Consul or Eureka** </span></span>\
  <https://ocelot.readthedocs.io/en/latest/features/servicediscovery.html>

- <span data-ttu-id="5a9e2-299">**Ukládání do mezipaměti na úrovni brány rozhraní API** </span><span class="sxs-lookup"><span data-stu-id="5a9e2-299">**Caching at the API Gateway tier** </span></span>\
  <https://ocelot.readthedocs.io/en/latest/features/caching.html>

- <span data-ttu-id="5a9e2-300">**Protokolování na úrovni brány rozhraní API** </span><span class="sxs-lookup"><span data-stu-id="5a9e2-300">**Logging at the API Gateway tier** </span></span>\
  <https://ocelot.readthedocs.io/en/latest/features/logging.html>

- <span data-ttu-id="5a9e2-301">**Kvalita služeb (opakování a jističe) na úrovni brány ROZHRANÍ API** </span><span class="sxs-lookup"><span data-stu-id="5a9e2-301">**Quality of Service (Retries and Circuit breakers) at the API Gateway tier** </span></span>\
  <https://ocelot.readthedocs.io/en/latest/features/qualityofservice.html>

- <span data-ttu-id="5a9e2-302">**Omezení rychlosti** </span><span class="sxs-lookup"><span data-stu-id="5a9e2-302">**Rate limiting** </span></span>\
  [https://ocelot.readthedocs.io/en/latest/features/ratelimiting.html](https://ocelot.readthedocs.io/en/latest/features/ratelimiting.html )

> [!div class="step-by-step"]
> <span data-ttu-id="5a9e2-303">[Předchozí](background-tasks-with-ihostedservice.md)
> [další](../microservice-ddd-cqrs-patterns/index.md)</span><span class="sxs-lookup"><span data-stu-id="5a9e2-303">[Previous](background-tasks-with-ihostedservice.md)
[Next](../microservice-ddd-cqrs-patterns/index.md)</span></span>
