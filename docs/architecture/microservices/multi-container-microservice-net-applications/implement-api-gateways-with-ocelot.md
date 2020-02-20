---
title: Implementace bran rozhraní API s Ocelotem
description: Naučte se implementovat brány API pomocí Ocelot a jak používat Ocelot v prostředí založeném na kontejnerech.
ms.date: 01/30/2020
ms.openlocfilehash: 0eb834829a418cfa1ccdf13c5fc8849f6855c4ba
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/20/2020
ms.locfileid: "77502419"
---
# <a name="implement-api-gateways-with-ocelot"></a><span data-ttu-id="8b07d-103">Implementace bran API pomocí Ocelot</span><span class="sxs-lookup"><span data-stu-id="8b07d-103">Implement API Gateways with Ocelot</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8b07d-104">Referenční [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) aplikace v současné době používá funkce poskytované [zástupné](https://www.envoyproxy.io/) k implementaci brány API namísto předchozího odkazovaného [Ocelot](https://github.com/ThreeMammals/Ocelot).</span><span class="sxs-lookup"><span data-stu-id="8b07d-104">The reference microservice application [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) is currently using features provided by [Envoy](https://www.envoyproxy.io/) to implement the API Gateway instead of the earlier referenced [Ocelot](https://github.com/ThreeMammals/Ocelot).</span></span>
> <span data-ttu-id="8b07d-105">Tuto možnost jsme zvolili kvůli integrované podpoře zástupné protokolu WebSocket, kterou vyžaduje nová komunikace mezi službami gRPC implementované v eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="8b07d-105">We made this design choice because of Envoy's built-in support for the WebSocket protocol, required by the new gRPC inter-service communications implemented in eShopOnContainers.</span></span>
> <span data-ttu-id="8b07d-106">Tento oddíl jsme ale v průvodci zachovali, takže můžete zvážit Ocelot jako jednoduchou, schopnou a zjednodušenou bránu API vhodnou pro scénáře produkčního prostředí.</span><span class="sxs-lookup"><span data-stu-id="8b07d-106">However, we've retained this section in the guide so you can consider Ocelot as a simple, capable, and lightweight API Gateway suitable for production-grade scenarios.</span></span>

## <a name="architect-and-design-your-api-gateways"></a><span data-ttu-id="8b07d-107">Architekt a návrh vašich bran rozhraní API</span><span class="sxs-lookup"><span data-stu-id="8b07d-107">Architect and design your API Gateways</span></span>

<span data-ttu-id="8b07d-108">Následující diagram architektury ukazuje, jak byly v eShopOnContainers implementovány brány rozhraní API pomocí Ocelot.</span><span class="sxs-lookup"><span data-stu-id="8b07d-108">The following architecture diagram shows how API Gateways were implemented with Ocelot in eShopOnContainers.</span></span>

![Diagram znázorňující architekturu eShopOnContainers](./media/implement-api-gateways-with-ocelot/eshoponcontainers-architecture.png)

<span data-ttu-id="8b07d-110">**Obrázek 6-28**.</span><span class="sxs-lookup"><span data-stu-id="8b07d-110">**Figure 6-28**.</span></span> <span data-ttu-id="8b07d-111">Architektura eShopOnContainers s bránami API</span><span class="sxs-lookup"><span data-stu-id="8b07d-111">eShopOnContainers architecture with API Gateways</span></span>

<span data-ttu-id="8b07d-112">Tento diagram znázorňuje, jak je celá aplikace nasazena do jednoho hostitele Docker nebo vývojového počítače s názvem "Docker for Windows" nebo "Docker for Mac".</span><span class="sxs-lookup"><span data-stu-id="8b07d-112">That diagram shows how the whole application is deployed into a single Docker host or development PC with "Docker for Windows" or "Docker for Mac".</span></span> <span data-ttu-id="8b07d-113">Nasazení nástroje na jakýkoli produkt Orchestrator však bude podobné, ale v nástroji Orchestrator lze škálovat libovolný kontejner v diagramu.</span><span class="sxs-lookup"><span data-stu-id="8b07d-113">However, deploying into any orchestrator would be similar, but any container in the diagram could be scaled out in the orchestrator.</span></span>

<span data-ttu-id="8b07d-114">Kromě toho by se měly prostředky infrastruktury, jako jsou databáze, mezipaměť a zprostředkovatelé zpráv, přesměrovat z produktu Orchestrator a nasazovat na vysoce dostupné systémy pro infrastrukturu, jako je Azure SQL Database, Azure Cosmos DB, Azure Redis, Azure Service Bus, nebo jakékoli řešení clusteringu s vysokou dostupností v místním prostředí.</span><span class="sxs-lookup"><span data-stu-id="8b07d-114">In addition, the infrastructure assets such as databases, cache, and message brokers should be offloaded from the orchestrator and deployed into high available systems for infrastructure, like Azure SQL Database, Azure Cosmos DB, Azure Redis, Azure Service Bus, or any HA clustering solution on-premises.</span></span>

<span data-ttu-id="8b07d-115">Vzhledem k tomu, že v diagramu můžete také všimnout, že několik bran rozhraní API umožňuje, aby více vývojových týmů bylo autonomní (v tomto případě marketingové funkce vs. nákupy) při vývoji a nasazování mikroslužeb a jejich vlastních souvisejících bran rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="8b07d-115">As you can also notice in the diagram, having several API Gateways allows multiple development teams to be autonomous (in this case Marketing features vs. Shopping features) when developing and deploying their microservices plus their own related API Gateways.</span></span>

<span data-ttu-id="8b07d-116">Pokud jste měli jedinou bránu rozhraní API monolitické, která by znamenala, že se jeden bod dá aktualizovat několika vývojovými týmy, může to pár všech mikroslužeb s jedinou částí aplikace.</span><span class="sxs-lookup"><span data-stu-id="8b07d-116">If you had a single monolithic API Gateway that would mean a single point to be updated by several development teams, which could couple all the microservices with a single part of the application.</span></span>

<span data-ttu-id="8b07d-117">V takovém případě je v podstatě ještě mnohem víc, ale jemně zrnitou bránu API můžete omezit na jednu jednotlivou obchodní mikroslužbu v závislosti na zvolené architektuře.</span><span class="sxs-lookup"><span data-stu-id="8b07d-117">Going much further in the design, sometimes a fine-grained API Gateway can also be limited to a single business microservice depending on the chosen architecture.</span></span> <span data-ttu-id="8b07d-118">Používání hranic brány API, které jsou vyřízeny firmou nebo doménou, vám pomůže dosáhnout lepšího návrhu.</span><span class="sxs-lookup"><span data-stu-id="8b07d-118">Having the API Gateway's boundaries dictated by the business or domain will help you to get a better design.</span></span>

<span data-ttu-id="8b07d-119">Například přesnější členitost v úrovni brány rozhraní API může být obzvláště užitečná pro pokročilejší aplikace složených uživatelského rozhraní, které jsou založené na mikroslužbách, protože koncept jemně odstupňované brány rozhraní API je podobný službě složení uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="8b07d-119">For instance, fine granularity in the API Gateway tier can be especially useful for more advanced composite UI applications that are based on microservices, because the concept of a fine-grained API Gateway is similar to a UI composition service.</span></span>

<span data-ttu-id="8b07d-120">V předchozí části se zobrazí další podrobnosti, které [vytváří složené uživatelské rozhraní založené na mikroslužbách](../architect-microservice-container-applications/microservice-based-composite-ui-shape-layout.md).</span><span class="sxs-lookup"><span data-stu-id="8b07d-120">We delve into more details in the previous section [Creating composite UI based on microservices](../architect-microservice-container-applications/microservice-based-composite-ui-shape-layout.md).</span></span>

<span data-ttu-id="8b07d-121">Jako Key poznatkem pro mnoho středních a velkých aplikací je použití předem vytvořeného produktu brány rozhraní API obvykle dobrým přístupem, ale ne jako s jedním monolitické Agregátorem nebo jedinečnou bránou rozhraní API, pokud tato brána API nepovoluje víc nezávislých. oblasti konfigurace pro několik vývojových týmů vytvářejících autonomní mikroslužby.</span><span class="sxs-lookup"><span data-stu-id="8b07d-121">As key takeaway, for many medium- and large-size applications, using a custom-built API Gateway product is usually a good approach, but not as a single monolithic aggregator or unique central custom API Gateway unless that API Gateway allows multiple independent configuration areas for the several development teams creating autonomous microservices.</span></span>

### <a name="sample-microservicescontainers-to-reroute-through-the-api-gateways"></a><span data-ttu-id="8b07d-122">Ukázkové mikroslužby/kontejnery pro přesměrování přes brány rozhraní API</span><span class="sxs-lookup"><span data-stu-id="8b07d-122">Sample microservices/containers to reroute through the API Gateways</span></span>

<span data-ttu-id="8b07d-123">Například eShopOnContainers má kolem šesti interních typů mikroslužeb, které je třeba publikovat prostřednictvím bran rozhraní API, jak je znázorněno na následujícím obrázku.</span><span class="sxs-lookup"><span data-stu-id="8b07d-123">As an example, eShopOnContainers has around six internal microservice-types that have to be published through the API Gateways, as shown in the following image.</span></span>

![Snímek obrazovky se složkou služby zobrazující její podsložky](./media/implement-api-gateways-with-ocelot/eshoponcontainers-microservice-folders.png)

<span data-ttu-id="8b07d-125">**Obrázek 6-29**.</span><span class="sxs-lookup"><span data-stu-id="8b07d-125">**Figure 6-29**.</span></span> <span data-ttu-id="8b07d-126">Složky mikroslužeb v řešení eShopOnContainers v aplikaci Visual Studio</span><span class="sxs-lookup"><span data-stu-id="8b07d-126">Microservice folders in eShopOnContainers solution in Visual Studio</span></span>

<span data-ttu-id="8b07d-127">O službě identit, v návrhu, který je z hlediska směrování brány rozhraní API, je jediným problémem, který se týká pouze průřezů v systému, i když s Ocelot je také možné ho zahrnout jako součást seznamů opětovného směrování.</span><span class="sxs-lookup"><span data-stu-id="8b07d-127">About the Identity service, in the design it's left out of the API Gateway routing because it's the only cross-cutting concern in the system, although with Ocelot it's also possible to include it as part of the rerouting lists.</span></span>

<span data-ttu-id="8b07d-128">Všechny tyto služby se v současnosti implementují jako ASP.NET Core služby webového rozhraní API, jak je můžete říct od kódu.</span><span class="sxs-lookup"><span data-stu-id="8b07d-128">All those services are currently implemented as ASP.NET Core Web API services, as you can tell from the code.</span></span> <span data-ttu-id="8b07d-129">Pojďme se zaměřit na jednu z mikroslužeb, jako je kód mikroslužby katalogu.</span><span class="sxs-lookup"><span data-stu-id="8b07d-129">Let's focus on one of the microservices like the Catalog microservice code.</span></span>

![Snímek obrazovky Průzkumník řešení zobrazující obsah projektu Catalog. API](./media/implement-api-gateways-with-ocelot/catalog-api-microservice-folders.png)

<span data-ttu-id="8b07d-131">**Obrázek 6-30**.</span><span class="sxs-lookup"><span data-stu-id="8b07d-131">**Figure 6-30**.</span></span> <span data-ttu-id="8b07d-132">Ukázka mikroslužby webového rozhraní API (služba katalogu mikroslužeb)</span><span class="sxs-lookup"><span data-stu-id="8b07d-132">Sample Web API microservice (Catalog microservice)</span></span>

<span data-ttu-id="8b07d-133">Můžete vidět, že mikroslužba katalogu je typický ASP.NET Core projektu webového rozhraní API s několika řadiči a metodami, jako v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="8b07d-133">You can see that the Catalog microservice is a typical ASP.NET Core Web API project with several controllers and methods like in the following code.</span></span>

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

<span data-ttu-id="8b07d-134">Požadavek HTTP ukončí běh tohoto druhu C# kódu s přístupem k databázi mikroslužeb a všech dalších potřebných akcí.</span><span class="sxs-lookup"><span data-stu-id="8b07d-134">The HTTP request will end up running that kind of C# code accessing the microservice database and any additional required action.</span></span>

<span data-ttu-id="8b07d-135">V souvislosti s adresou URL mikroslužeb, když jsou kontejnery nasazeny na místním počítači pro vývoj (místní hostitel Docker), má každý kontejner mikroslužeb vždy interní port (obvykle port 80), který je uveden v souboru Dockerfile, jako v následujícím souboru Dockerfile:</span><span class="sxs-lookup"><span data-stu-id="8b07d-135">Regarding the microservice URL, when the containers are deployed in your local development PC (local Docker host), each microservice's container has always an internal port (usually port 80) specified in its dockerfile, as in the following dockerfile:</span></span>

```Dockerfile
FROM mcr.microsoft.com/dotnet/core/aspnet:3.1 AS base
WORKDIR /app
EXPOSE 80
```

<span data-ttu-id="8b07d-136">Port 80 zobrazený v kódu je interní v rámci hostitele Docker, takže není dostupný pro klientské aplikace.</span><span class="sxs-lookup"><span data-stu-id="8b07d-136">The port 80 shown in the code is internal within the Docker host, so it can't be reached by client apps.</span></span>

<span data-ttu-id="8b07d-137">Klientské aplikace mají přístup pouze k externím portům (pokud existuje), které jsou publikovány při nasazení pomocí `docker-compose`.</span><span class="sxs-lookup"><span data-stu-id="8b07d-137">Client apps can access only the external ports (if any) published when deploying with `docker-compose`.</span></span>

<span data-ttu-id="8b07d-138">Tyto externí porty by neměly být publikovány při nasazování do produkčního prostředí.</span><span class="sxs-lookup"><span data-stu-id="8b07d-138">Those external ports shouldn't be published when deploying to a production environment.</span></span> <span data-ttu-id="8b07d-139">To je přesně důvod, proč chcete používat bránu rozhraní API, abyste se vyhnuli přímé komunikaci mezi klientskými aplikacemi a mikroslužbami.</span><span class="sxs-lookup"><span data-stu-id="8b07d-139">This is precisely why you want to use the API Gateway, to avoid the direct communication between the client apps and the microservices.</span></span>

<span data-ttu-id="8b07d-140">Při vývoji ale chcete přímo získat přístup k mikroslužbám nebo kontejneru a spustit ho prostřednictvím Swagger.</span><span class="sxs-lookup"><span data-stu-id="8b07d-140">However, when developing, you want to access the microservice/container directly and run it through Swagger.</span></span> <span data-ttu-id="8b07d-141">To je důvod, proč v eShopOnContainers jsou externí porty stále zadané i v případě, že se nepoužívají v bráně API ani v klientských aplikacích.</span><span class="sxs-lookup"><span data-stu-id="8b07d-141">That's why in eShopOnContainers, the external ports are still specified even when they won't be used by the API Gateway or the client apps.</span></span>

<span data-ttu-id="8b07d-142">Tady je příklad souboru `docker-compose.override.yml` pro mikroslužbu katalogu:</span><span class="sxs-lookup"><span data-stu-id="8b07d-142">Here's an example of the `docker-compose.override.yml` file for the Catalog microservice:</span></span>

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

<span data-ttu-id="8b07d-143">Můžete zjistit, jak v konfiguraci Docker-Compose. override. yml je interním portem kontejneru katalogu port 80, ale port pro externí přístup je 5101.</span><span class="sxs-lookup"><span data-stu-id="8b07d-143">You can see how in the docker-compose.override.yml configuration the internal port for the Catalog container is port 80, but the port for external access is 5101.</span></span> <span data-ttu-id="8b07d-144">Tento port by ale neměl používat aplikace při použití brány API, jenom pro ladění, spouštění a testování jenom pro mikroslužby katalogu.</span><span class="sxs-lookup"><span data-stu-id="8b07d-144">But this port shouldn't be used by the application when using an API Gateway, only to debug, run, and test just the Catalog microservice.</span></span>

<span data-ttu-id="8b07d-145">Za normálních okolností nebudete nasazovat do provozního prostředí Docker – to znamená, že správné provozní prostředí nasazení pro mikroslužby je Orchestrator, jako je Kubernetes nebo Service Fabric.</span><span class="sxs-lookup"><span data-stu-id="8b07d-145">Normally, you won't be deploying with docker-compose into a production environment because the right production deployment environment for microservices is an orchestrator like Kubernetes or Service Fabric.</span></span> <span data-ttu-id="8b07d-146">Při nasazování do těchto prostředí budete používat jiné konfigurační soubory, kde nebudete publikovat přímo žádný externí port pro mikroslužby, ale reverzní proxy server budete vždycky používat z brány rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="8b07d-146">When deploying to those environments you use different configuration files where you won't publish directly any external port for the microservices but, you'll always use the reverse proxy from the API Gateway.</span></span>

<span data-ttu-id="8b07d-147">Spusťte službu mikroslužeb katalogu v místním hostiteli Docker.</span><span class="sxs-lookup"><span data-stu-id="8b07d-147">Run the catalog microservice in your local Docker host.</span></span> <span data-ttu-id="8b07d-148">Buď spusťte úplné řešení eShopOnContainers ze sady Visual Studio (spustí všechny služby v Docker – skládání souborů), nebo spusťte službu Catalog v katalogu pomocí následujícího příkazu Docker-skládání v prostředí CMD nebo PowerShell umístěného ve složce, kde jsou umístěny `docker-compose.yml` a `docker-compose.override.yml`.</span><span class="sxs-lookup"><span data-stu-id="8b07d-148">Either run the full eShopOnContainers solution from Visual Studio (it runs all the services in the docker-compose files), or start the Catalog microservice with the following docker-compose command in CMD or PowerShell positioned at the folder where the `docker-compose.yml` and `docker-compose.override.yml` are placed.</span></span>

```console
docker-compose run --service-ports catalog-api
```

<span data-ttu-id="8b07d-149">Tento příkaz spustí pouze závislosti kontejneru služby API Catalog plus, které jsou zadány v Docker-Compose. yml.</span><span class="sxs-lookup"><span data-stu-id="8b07d-149">This command only runs the catalog-api service container plus dependencies that are specified in the docker-compose.yml.</span></span> <span data-ttu-id="8b07d-150">V tomto případě kontejner SQL Server a kontejner RabbitMQ.</span><span class="sxs-lookup"><span data-stu-id="8b07d-150">In this case, the SQL Server container and RabbitMQ container.</span></span>

<span data-ttu-id="8b07d-151">Pak můžete přímo získat přístup ke mikroslužbám katalogu a pomocí uživatelského rozhraní Swagger získat přístup k jeho metodám přímo prostřednictvím tohoto "externího" portu, v tomto případě `http://localhost:5101/swagger`:</span><span class="sxs-lookup"><span data-stu-id="8b07d-151">Then, you can directly access the Catalog microservice and see its methods through the Swagger UI accessing directly through that "external" port, in this case `http://localhost:5101/swagger`:</span></span>

![Snímek obrazovky uživatelského rozhraní Swagger zobrazující REST API katalogu. API](./media/implement-api-gateways-with-ocelot/test-catalog-microservice.png)

<span data-ttu-id="8b07d-153">**Obrázek 6-31**.</span><span class="sxs-lookup"><span data-stu-id="8b07d-153">**Figure 6-31**.</span></span> <span data-ttu-id="8b07d-154">Testování mikroslužby katalogu pomocí uživatelského rozhraní Swagger</span><span class="sxs-lookup"><span data-stu-id="8b07d-154">Testing the Catalog microservice with its Swagger UI</span></span>

<span data-ttu-id="8b07d-155">V tomto okamžiku můžete nastavit zarážku v C# kódu v sadě Visual Studio, testovat mikroslužbu pomocí metod vydaných v uživatelském rozhraní Swagger a nakonec vyčistit vše pomocí `docker-compose down` příkazu.</span><span class="sxs-lookup"><span data-stu-id="8b07d-155">At this point, you could set a breakpoint in C# code in Visual Studio, test the microservice with the methods exposed in Swagger UI, and finally clean-up everything with the `docker-compose down` command.</span></span>

<span data-ttu-id="8b07d-156">Komunikace s přímým přístupem k mikroslužbám ale v tomto případě přes externí port 5101 je přesně to, co chcete v aplikaci zabránit.</span><span class="sxs-lookup"><span data-stu-id="8b07d-156">However, direct-access communication to the microservice, in this case through the external port 5101, is precisely what you want to avoid in your application.</span></span> <span data-ttu-id="8b07d-157">A můžete se tomu vyhnout nastavením dodatečné úrovně dereference brány API (Ocelot, v tomto případě).</span><span class="sxs-lookup"><span data-stu-id="8b07d-157">And you can avoid that by setting the additional level of indirection of the API Gateway (Ocelot, in this case).</span></span> <span data-ttu-id="8b07d-158">Klientská aplikace tak nebude mít přímý přístup k mikroslužbám.</span><span class="sxs-lookup"><span data-stu-id="8b07d-158">That way, the client app won't directly access the microservice.</span></span>

## <a name="implementing-your-api-gateways-with-ocelot"></a><span data-ttu-id="8b07d-159">Implementace bran API pomocí Ocelot</span><span class="sxs-lookup"><span data-stu-id="8b07d-159">Implementing your API Gateways with Ocelot</span></span>

<span data-ttu-id="8b07d-160">Ocelot je v podstatě sada middlewarů, které můžete použít v určitém pořadí.</span><span class="sxs-lookup"><span data-stu-id="8b07d-160">Ocelot is basically a set of middlewares that you can apply in a specific order.</span></span>

<span data-ttu-id="8b07d-161">Ocelot je navržená tak, aby pracovala pouze s ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="8b07d-161">Ocelot is designed to work with ASP.NET Core only.</span></span> <span data-ttu-id="8b07d-162">Cílí na to `netstandard2.0`, takže se dá použít kdekoli .NET Standard 2,0, včetně běhového prostředí .NET Core 2,0 a .NET Framework 4.6.1 runtime a up.</span><span class="sxs-lookup"><span data-stu-id="8b07d-162">It targets `netstandard2.0` so it can be used anywhere .NET Standard 2.0 is supported, including .NET Core 2.0 runtime and .NET Framework 4.6.1 runtime and up.</span></span>

<span data-ttu-id="8b07d-163">Ocelot a jeho závislosti nainstalujete v projektu ASP.NET Core pomocí [balíčku NuGet ocelot](https://www.nuget.org/packages/Ocelot/)ze sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="8b07d-163">You install Ocelot and its dependencies in your ASP.NET Core project with [Ocelot's NuGet package](https://www.nuget.org/packages/Ocelot/), from Visual Studio.</span></span>

```powershell
Install-Package Ocelot
```

<span data-ttu-id="8b07d-164">V eShopOnContainers je jeho implementace brány API jednoduchý ASP.NET Core projekt webhosta a middleware Ocelot zpracovává všechny funkce brány API, jak je znázorněno na následujícím obrázku:</span><span class="sxs-lookup"><span data-stu-id="8b07d-164">In eShopOnContainers, its API Gateway implementation is a simple ASP.NET Core WebHost project, and Ocelot’s middleware handles all the API Gateway features, as shown in the following image:</span></span>

![Snímek obrazovky Průzkumník řešení zobrazující projekt brány API Ocelot](./media/implement-api-gateways-with-ocelot/ocelotapigw-base-project.png)

<span data-ttu-id="8b07d-166">**Obrázek 6-32**.</span><span class="sxs-lookup"><span data-stu-id="8b07d-166">**Figure 6-32**.</span></span> <span data-ttu-id="8b07d-167">Projekt OcelotApiGw Base v eShopOnContainers</span><span class="sxs-lookup"><span data-stu-id="8b07d-167">The OcelotApiGw base project in eShopOnContainers</span></span>

<span data-ttu-id="8b07d-168">Tento ASP.NET Core projekt webhost je vytvořen v podstatě pomocí dvou jednoduchých souborů: `Program.cs` a `Startup.cs`.</span><span class="sxs-lookup"><span data-stu-id="8b07d-168">This ASP.NET Core WebHost project is basically built with two simple files:  `Program.cs` and `Startup.cs`.</span></span>

<span data-ttu-id="8b07d-169">Program.cs potřebuje jenom vytvořit a nakonfigurovat typické ASP.NET Core BuildWebHost.</span><span class="sxs-lookup"><span data-stu-id="8b07d-169">The Program.cs just needs to create and configure the typical ASP.NET Core BuildWebHost.</span></span>

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

<span data-ttu-id="8b07d-170">Důležitým bodem pro Ocelot je soubor `configuration.json`, který musíte poskytnout tvůrci prostřednictvím metody `AddJsonFile()`.</span><span class="sxs-lookup"><span data-stu-id="8b07d-170">The important point here for Ocelot is the `configuration.json` file that you must provide to the builder through the `AddJsonFile()` method.</span></span> <span data-ttu-id="8b07d-171">V `configuration.json` je místo, kde zadáte všechny přesměrování brány API, což znamená, že externí koncové body s konkrétními porty a korelační interní koncové body jsou obvykle pomocí různých portů.</span><span class="sxs-lookup"><span data-stu-id="8b07d-171">That `configuration.json` is where you specify all the API Gateway ReRoutes, meaning the external endpoints with specific ports and the correlated internal endpoints, usually using different ports.</span></span>

```json
{
    "ReRoutes": [],
    "GlobalConfiguration": {}
}
```

<span data-ttu-id="8b07d-172">Existují dva oddíly konfigurace.</span><span class="sxs-lookup"><span data-stu-id="8b07d-172">There are two sections to the configuration.</span></span> <span data-ttu-id="8b07d-173">Pole přesměruje a GlobalConfiguration.</span><span class="sxs-lookup"><span data-stu-id="8b07d-173">An array of ReRoutes and a GlobalConfiguration.</span></span> <span data-ttu-id="8b07d-174">Přesměrování jsou objekty, které říká Ocelot, jak zacházet s nadřazeným požadavkem.</span><span class="sxs-lookup"><span data-stu-id="8b07d-174">The ReRoutes are the objects that tell Ocelot how to treat an upstream request.</span></span> <span data-ttu-id="8b07d-175">Globální konfigurace umožňuje přepisovat specifická nastavení pro přesměrování.</span><span class="sxs-lookup"><span data-stu-id="8b07d-175">The Global configuration allows overrides of ReRoute specific settings.</span></span> <span data-ttu-id="8b07d-176">To je užitečné, pokud nechcete spravovat spoustu nastavení konkrétního přesměrování.</span><span class="sxs-lookup"><span data-stu-id="8b07d-176">It's useful if you don't want to manage lots of ReRoute specific settings.</span></span>

<span data-ttu-id="8b07d-177">Tady je zjednodušený příklad, jak [přesměrovat konfigurační soubor](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/ApiGateways/Web.Bff.Shopping/apigw/configuration.json) z jedné z bran rozhraní API z eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="8b07d-177">Here's a simplified example of [ReRoute configuration file](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/ApiGateways/Web.Bff.Shopping/apigw/configuration.json) from one of the API Gateways from eShopOnContainers.</span></span>

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

<span data-ttu-id="8b07d-178">Hlavní funkcí brány Ocelot API je přijmout příchozí požadavky HTTP a přeslat je do služby pro příjem dat, a to v současné době jako jiný požadavek HTTP.</span><span class="sxs-lookup"><span data-stu-id="8b07d-178">The main functionality of an Ocelot API Gateway is to take incoming HTTP requests and forward them on to a downstream service, currently as another HTTP request.</span></span> <span data-ttu-id="8b07d-179">Ocelot popisuje směrování jednoho požadavku na jiný jako přesměrování.</span><span class="sxs-lookup"><span data-stu-id="8b07d-179">Ocelot's describes the routing of one request to another as a ReRoute.</span></span>

<span data-ttu-id="8b07d-180">Řekněme například, že se zaměříme na jednu z přesměrů v Configuration. JSON výše. konfigurace pro mikroslužbu koše.</span><span class="sxs-lookup"><span data-stu-id="8b07d-180">For instance, let's focus on one of the ReRoutes in the configuration.json from above, the configuration for the Basket microservice.</span></span>

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

<span data-ttu-id="8b07d-181">DownstreamPathTemplate, schéma a DownstreamHostAndPorts vytvoří interní adresu URL mikroslužby, na kterou se tato žádost přepošle.</span><span class="sxs-lookup"><span data-stu-id="8b07d-181">The DownstreamPathTemplate, Scheme, and DownstreamHostAndPorts make the internal microservice URL that this request will be forwarded to.</span></span>

<span data-ttu-id="8b07d-182">Port je interní port používaný službou.</span><span class="sxs-lookup"><span data-stu-id="8b07d-182">The port is the internal port used by the service.</span></span> <span data-ttu-id="8b07d-183">Při použití kontejnerů se port zadal na jeho souboru Dockerfile.</span><span class="sxs-lookup"><span data-stu-id="8b07d-183">When using containers, the port specified at its dockerfile.</span></span>

<span data-ttu-id="8b07d-184">`Host` je název služby, který závisí na překladu názvu služby, který používáte.</span><span class="sxs-lookup"><span data-stu-id="8b07d-184">The `Host` is a service name that depends on the service name resolution you are using.</span></span> <span data-ttu-id="8b07d-185">Při použití Docker-skládání jsou názvy služeb poskytovány hostitelem Docker, který používá názvy služeb, které jsou k dispozici v souborech Docker-pro vytváření.</span><span class="sxs-lookup"><span data-stu-id="8b07d-185">When using docker-compose, the services names are provided by the Docker Host, which is using the service names provided in the docker-compose files.</span></span> <span data-ttu-id="8b07d-186">Pokud používáte Orchestrator jako Kubernetes nebo Service Fabric, měl by tento název přeložit DNS nebo překlad IP adres, který poskytuje každý Orchestrator.</span><span class="sxs-lookup"><span data-stu-id="8b07d-186">If using an orchestrator like Kubernetes or Service Fabric, that name should be resolved by the DNS or name resolution provided by each orchestrator.</span></span>

<span data-ttu-id="8b07d-187">DownstreamHostAndPorts je pole, které obsahuje hostitele a port jakékoli služby pro příjem dat, na kterou chcete předávané požadavky.</span><span class="sxs-lookup"><span data-stu-id="8b07d-187">DownstreamHostAndPorts is an array that contains the host and port of any downstream services that you wish to forward requests to.</span></span> <span data-ttu-id="8b07d-188">Obvykle bude obsahovat pouze jednu položku, někdy ale můžete chtít vyrovnávat zatížení požadavků na služby pro příjem dat a Ocelot umožňuje přidat více než jednu položku a pak vybrat nástroj pro vyrovnávání zatížení.</span><span class="sxs-lookup"><span data-stu-id="8b07d-188">Usually this will just contain one entry but sometimes you might want to load balance requests to your downstream services and Ocelot lets you add more than one entry and then select a load balancer.</span></span> <span data-ttu-id="8b07d-189">Pokud ale používáte Azure a jakýkoli Orchestrator, je pravděpodobně lepší vyrovnávat zatížení s infrastrukturou Cloud a Orchestrator.</span><span class="sxs-lookup"><span data-stu-id="8b07d-189">But if using Azure and any orchestrator it is probably a better idea to load balance with the cloud and orchestrator infrastructure.</span></span>

<span data-ttu-id="8b07d-190">UpstreamPathTemplate je adresa URL, kterou Ocelot použije k identifikaci, které DownstreamPathTemplate se má použít pro daný požadavek od klienta.</span><span class="sxs-lookup"><span data-stu-id="8b07d-190">The UpstreamPathTemplate is the URL that Ocelot will use to identify which DownstreamPathTemplate to use for a given request from the client.</span></span> <span data-ttu-id="8b07d-191">Nakonec se použije UpstreamHttpMethod, aby Ocelot mohl rozlišovat různé požadavky (GET, POST, PUT) na stejnou adresu URL.</span><span class="sxs-lookup"><span data-stu-id="8b07d-191">Finally, the UpstreamHttpMethod is used so Ocelot can distinguish between different requests (GET, POST, PUT) to the same URL.</span></span>

<span data-ttu-id="8b07d-192">V tomto okamžiku můžete mít jedinou bránu Ocelot API (ASP.NET Core webhost) pomocí jednoho nebo [několika sloučených souborů Configuration. JSON](https://ocelot.readthedocs.io/en/latest/features/configuration.html#merging-configuration-files) nebo můžete konfiguraci uložit i [v úložišti Consul KV](https://ocelot.readthedocs.io/en/latest/features/configuration.html#store-configuration-in-consul).</span><span class="sxs-lookup"><span data-stu-id="8b07d-192">At this point, you could have a single Ocelot API Gateway (ASP.NET Core WebHost) using one or [multiple merged configuration.json files](https://ocelot.readthedocs.io/en/latest/features/configuration.html#merging-configuration-files) or you can also store the [configuration in a Consul KV store](https://ocelot.readthedocs.io/en/latest/features/configuration.html#store-configuration-in-consul).</span></span>

<span data-ttu-id="8b07d-193">Jak je zavedené v sekcích architektury a návrhu, pokud opravdu chcete mít autonomní mikroslužby, může být lepší rozdělit tuto bránu monolitické API na několik bran rozhraní API a/nebo BFF (back-end pro front-end).</span><span class="sxs-lookup"><span data-stu-id="8b07d-193">But as introduced in the architecture and design sections, if you really want to have autonomous microservices, it might be better to split that single monolithic API Gateway into multiple API Gateways and/or BFF (Backend for Frontend).</span></span> <span data-ttu-id="8b07d-194">Pro tento účel se podívejme, jak implementovat tento přístup k kontejnerům Docker.</span><span class="sxs-lookup"><span data-stu-id="8b07d-194">For that purpose, let's see how to implement that approach with Docker containers.</span></span>

### <a name="using-a-single-docker-container-image-to-run-multiple-different-api-gateway--bff-container-types"></a><span data-ttu-id="8b07d-195">Použití jediné image kontejneru Docker pro spuštění více různých typů kontejnerů brány API/BFF</span><span class="sxs-lookup"><span data-stu-id="8b07d-195">Using a single Docker container image to run multiple different API Gateway / BFF container types</span></span>

<span data-ttu-id="8b07d-196">V eShopOnContainers používáme jednu Image kontejneru Docker s bránou rozhraní Ocelot API, ale za běhu vytvoříme pro každý typ rozhraní API-Gateway/BFF různé služby a kontejnery, a to tak, že k přístupu na jinou složku na počítači pro každou službu použijete jiný soubor Configuration. JSON.</span><span class="sxs-lookup"><span data-stu-id="8b07d-196">In eShopOnContainers, we're using a single Docker container image with the Ocelot API Gateway but then, at run time, we create different services/containers for each type of API-Gateway/BFF by providing a different configuration.json file, using a docker volume to access a different PC folder for each service.</span></span>

![Diagram jedné image Docker Ocelot brány pro všechny brány API](./media/implement-api-gateways-with-ocelot/reusing-single-ocelot-docker-image.png)

<span data-ttu-id="8b07d-198">**Obrázek 6-33**.</span><span class="sxs-lookup"><span data-stu-id="8b07d-198">**Figure 6-33**.</span></span> <span data-ttu-id="8b07d-199">Opakované použití jedné image Docker Ocelot napříč více typy brány rozhraní API</span><span class="sxs-lookup"><span data-stu-id="8b07d-199">Reusing a single Ocelot Docker image across multiple API Gateway types</span></span>

<span data-ttu-id="8b07d-200">V eShopOnContainers se v projektu s názvem "OcelotApiGw" a s názvem Image "eshop/OcelotApiGw", který je uveden v souboru Docker-Compose. yml, vytvoří "Obecná image Docker brány API Ocelot".</span><span class="sxs-lookup"><span data-stu-id="8b07d-200">In eShopOnContainers, the "Generic Ocelot API Gateway Docker Image" is created with the project named 'OcelotApiGw' and the image name "eshop/ocelotapigw" that is specified in the docker-compose.yml file.</span></span> <span data-ttu-id="8b07d-201">Při nasazování do Docker se pak vytvoří čtyři kontejnery API-Gateway vytvořené z stejné image Docker, jak je znázorněno v následujícím extrakci ze souboru Docker-Compose. yml.</span><span class="sxs-lookup"><span data-stu-id="8b07d-201">Then, when deploying to Docker, there will be four API-Gateway containers created from that same Docker image, as shown in the following extract from the docker-compose.yml file.</span></span>

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

<span data-ttu-id="8b07d-202">Jak vidíte v následujícím souboru Docker-Compose. override. yml, jediným rozdílem mezi těmito kontejnery brány API je konfigurační soubor Ocelot, který se liší pro každý kontejner služby a je určen za běhu prostřednictvím Svazek Docker.</span><span class="sxs-lookup"><span data-stu-id="8b07d-202">Additionally, as you can see in the following docker-compose.override.yml file, the only difference between those API Gateway containers is the Ocelot configuration file, which is different for each service container and it's specified at runtime through a Docker volume.</span></span>

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

<span data-ttu-id="8b07d-203">Z důvodu tohoto předchozího kódu, jak je znázorněno v Průzkumníkovi aplikace Visual Studio níže, je jediným souborem potřebným k definování každé konkrétní brány rozhraní API pro obchodní/BFF jenom soubor Configuration. JSON, protože čtyři brány rozhraní API jsou založené na stejné imagi Docker.</span><span class="sxs-lookup"><span data-stu-id="8b07d-203">Because of that previous code, and as shown in the Visual Studio Explorer below, the only file needed to define each specific business/BFF API Gateway is just a configuration.json file, because the four API Gateways are based on the same Docker image.</span></span>

![Snímek obrazovky zobrazující všechny brány rozhraní API se soubory Configuration. JSON.](./media/implement-api-gateways-with-ocelot/ocelot-configuration-files.png)

<span data-ttu-id="8b07d-205">**Obrázek 6-34**.</span><span class="sxs-lookup"><span data-stu-id="8b07d-205">**Figure 6-34**.</span></span> <span data-ttu-id="8b07d-206">Jediným souborem potřebným k definování každého rozhraní API Gateway/BFF s Ocelot je konfigurační soubor.</span><span class="sxs-lookup"><span data-stu-id="8b07d-206">The only file needed to define each API Gateway / BFF with Ocelot is a configuration file</span></span>

<span data-ttu-id="8b07d-207">Díky rozdělení brány API na několik bran rozhraní API můžou různé vývojové týmy zaměřené na různé podmnožiny mikroslužeb spravovat svoje vlastní brány API pomocí nezávislých Ocelot konfiguračních souborů.</span><span class="sxs-lookup"><span data-stu-id="8b07d-207">By splitting the API Gateway into multiple API Gateways, different development teams focusing on different subsets of microservices can manage their own API Gateways by using independent Ocelot configuration files.</span></span> <span data-ttu-id="8b07d-208">Navíc zároveň můžou znovu použít stejnou image Docker Ocelot.</span><span class="sxs-lookup"><span data-stu-id="8b07d-208">Plus, at the same time they can reuse the same Ocelot Docker image.</span></span>

<span data-ttu-id="8b07d-209">Když teď spustíte eShopOnContainers s branami rozhraní API (standardně ve verzi VS při otevírání řešení eShopOnContainers-ServicesAndWebApps. sln nebo spuštěním příkazu "Docker-sestavit"), provedou se následující ukázkové trasy.</span><span class="sxs-lookup"><span data-stu-id="8b07d-209">Now, if you run eShopOnContainers with the API Gateways (included by default in VS when opening eShopOnContainers-ServicesAndWebApps.sln solution or if running "docker-compose up"), the following sample routes will be performed.</span></span>

<span data-ttu-id="8b07d-210">Když například navštívíte nadřazený URL `http://localhost:5202/api/v1/c/catalog/items/2/` obsluhované bránou webshoppingapigw API, získáte stejný výsledek z interní adresy URL pro příjem dat `http://catalog-api/api/v1/2` v rámci hostitele Docker, jako v následujícím prohlížeči.</span><span class="sxs-lookup"><span data-stu-id="8b07d-210">For instance, when visiting the upstream URL `http://localhost:5202/api/v1/c/catalog/items/2/` served by the webshoppingapigw API Gateway, you get the same result from the internal Downstream URL `http://catalog-api/api/v1/2` within the Docker host, as in the following browser.</span></span>

![Snímek obrazovky prohlížeče znázorňující odpověď procházející rozhraním API Gateway](./media/implement-api-gateways-with-ocelot/access-microservice-through-url.png)

<span data-ttu-id="8b07d-212">**Obrázek 6-35**.</span><span class="sxs-lookup"><span data-stu-id="8b07d-212">**Figure 6-35**.</span></span> <span data-ttu-id="8b07d-213">Přístup k mikroslužbám prostřednictvím adresy URL poskytované bránou API</span><span class="sxs-lookup"><span data-stu-id="8b07d-213">Accessing a microservice through a URL provided by the API Gateway</span></span>

<span data-ttu-id="8b07d-214">Z důvodu testování nebo ladění, pokud jste chtěli získat přímý přístup ke kontejneru Docker katalogu (pouze ve vývojovém prostředí) bez předávání bránou API, vzhledem k tomu, že "Catalog-API" je překlad DNS interního překladu na hostitele Docker (zjišťování služby, které zpracovávají názvy služeb Docker-), jediným způsobem, jak přímo přistupovat ke kontejneru, je externí port publikovaný v Docker-Compose. override. yml, který je k dispozici pouze pro vývojové testy, například `http://localhost:5101/api/v1/Catalog/items/1` v následujícím prohlížeči.</span><span class="sxs-lookup"><span data-stu-id="8b07d-214">Because of testing or debugging reasons, if you wanted to directly access to the Catalog Docker container (only at the development environment) without passing through the API Gateway, since 'catalog-api' is a DNS resolution internal to the Docker host (service discovery handled by docker-compose service names), the only way to directly access the container is through the external port published in the docker-compose.override.yml, which is provided only for development tests, such as `http://localhost:5101/api/v1/Catalog/items/1` in the following browser.</span></span>

![Snímek obrazovky prohlížeče ukazující přímou odpověď na katalog. API](./media/implement-api-gateways-with-ocelot/direct-access-microservice-testing.png)

<span data-ttu-id="8b07d-216">**Obrázek 6-36**.</span><span class="sxs-lookup"><span data-stu-id="8b07d-216">**Figure 6-36**.</span></span> <span data-ttu-id="8b07d-217">Přímý přístup k mikroslužbám pro účely testování</span><span class="sxs-lookup"><span data-stu-id="8b07d-217">Direct access to a microservice for testing purposes</span></span>

<span data-ttu-id="8b07d-218">Ale aplikace je nakonfigurovaná tak, aby přístupná ke všem mikroslužbám prostřednictvím bran rozhraní API, ne i přes "zkratky" s přímým portem ".</span><span class="sxs-lookup"><span data-stu-id="8b07d-218">But the application is configured so it accesses all the microservices through the API Gateways, not though the direct port "shortcuts".</span></span>

### <a name="the-gateway-aggregation-pattern-in-eshoponcontainers"></a><span data-ttu-id="8b07d-219">Model agregace brány v eShopOnContainers</span><span class="sxs-lookup"><span data-stu-id="8b07d-219">The Gateway aggregation pattern in eShopOnContainers</span></span>

<span data-ttu-id="8b07d-220">Jak jsme představili dřív, flexibilní způsob implementace agregace požadavků je s vlastními službami, podle kódu.</span><span class="sxs-lookup"><span data-stu-id="8b07d-220">As introduced previously, a flexible way to implement requests aggregation is with custom services, by code.</span></span> <span data-ttu-id="8b07d-221">Můžete také implementovat agregaci požadavků s [funkcí agregace požadavků v ocelot](https://ocelot.readthedocs.io/en/latest/features/requestaggregation.html#request-aggregation), ale nemusí být tak flexibilní, jak potřebujete.</span><span class="sxs-lookup"><span data-stu-id="8b07d-221">You could also implement request aggregation with the [Request Aggregation feature in Ocelot](https://ocelot.readthedocs.io/en/latest/features/requestaggregation.html#request-aggregation), but it might not be as flexible as you need.</span></span> <span data-ttu-id="8b07d-222">Proto je vybraný způsob implementace agregace v eShopOnContainers s explicitní ASP.NET Core služby webového rozhraní API pro každý agregátor.</span><span class="sxs-lookup"><span data-stu-id="8b07d-222">Therefore, the selected way to implement aggregation in eShopOnContainers is with an explicit ASP.NET Core Web API service for each aggregator.</span></span>

<span data-ttu-id="8b07d-223">V souladu s tímto přístupem je diagram kompozice brány API ve skutečnosti trochu rozšířený při zvažování agregátorových služeb, které se nezobrazuje v diagramu zjednodušené globální architektury.</span><span class="sxs-lookup"><span data-stu-id="8b07d-223">According to that approach, the API Gateway composition diagram is in reality a bit more extended when considering the aggregator services that are not shown in the simplified global architecture diagram shown previously.</span></span>

<span data-ttu-id="8b07d-224">V následujícím diagramu můžete také vidět, jak služby Agregátoru fungují s jejich souvisejícími bránami API.</span><span class="sxs-lookup"><span data-stu-id="8b07d-224">In the following diagram, you can also see how the aggregator services work with their related API Gateways.</span></span>

![Diagram architektury eShopOnContainers znázorňující služby Agregátoru](./media/implement-api-gateways-with-ocelot/eshoponcontainers-architecture-aggregator-services.png)

<span data-ttu-id="8b07d-226">**Obrázek 6-37**.</span><span class="sxs-lookup"><span data-stu-id="8b07d-226">**Figure 6-37**.</span></span> <span data-ttu-id="8b07d-227">Architektura eShopOnContainers s agregátor Services</span><span class="sxs-lookup"><span data-stu-id="8b07d-227">eShopOnContainers architecture with aggregator services</span></span>

<span data-ttu-id="8b07d-228">Další přiblížení: v obchodní oblasti "nakupování" na následujícím obrázku vidíte, že upovídanost mezi klientskými aplikacemi a mikroslužbami se při používání Agregátoru v bránách rozhraní API zkrátí.</span><span class="sxs-lookup"><span data-stu-id="8b07d-228">Zooming in further, on the "Shopping" business area in the following image, you can see that chattiness between the client apps and the microservices is reduced when using the aggregator services in the API Gateways.</span></span>

![Diagram znázorňující přiblížení architektury eShopOnContainers](./media/implement-api-gateways-with-ocelot/zoom-in-vision-aggregator-services.png)

<span data-ttu-id="8b07d-230">**Obrázek 6-38**.</span><span class="sxs-lookup"><span data-stu-id="8b07d-230">**Figure 6-38**.</span></span> <span data-ttu-id="8b07d-231">Přiblížení ve výhledu Agregátorových služeb</span><span class="sxs-lookup"><span data-stu-id="8b07d-231">Zoom in vision of the Aggregator services</span></span>

<span data-ttu-id="8b07d-232">Můžete si všimnout, jak se v diagramu zobrazují možné požadavky přicházející z bran rozhraní API, které může získat složitý přístup.</span><span class="sxs-lookup"><span data-stu-id="8b07d-232">You can notice how when the diagram shows the possible requests coming from the API Gateways it can get complex.</span></span> <span data-ttu-id="8b07d-233">I když vidíte, jak se budou šipky v modrém zjednodušeny, z perspektivy klientských aplikací při použití vzoru Agregátoru tím, že se omezí upovídanost a latence v komunikaci, a nakonec se tím významně zlepšuje uživatelské prostředí pro vzdálené aplikace ( mobilní a SPA aplikace), zejména.</span><span class="sxs-lookup"><span data-stu-id="8b07d-233">Although you can see how the arrows in blue would be simplified, from a client apps perspective, when using the aggregator pattern by reducing chattiness and latency in the communication, ultimately significantly improving the user experience for the remote apps (mobile and SPA apps), especially.</span></span>

<span data-ttu-id="8b07d-234">V případě obchodní oblasti a mikroslužeb "marketing" se jedná o jednoduchý případ použití, takže nemusíte používat agregátory, ale v případě potřeby to může být možné.</span><span class="sxs-lookup"><span data-stu-id="8b07d-234">In the case of the "Marketing" business area and microservices, it is a simple use case so there was no need to use aggregators, but it could also be possible, if needed.</span></span>

### <a name="authentication-and-authorization-in-ocelot-api-gateways"></a><span data-ttu-id="8b07d-235">Ověřování a autorizace v bránách rozhraní API Ocelot</span><span class="sxs-lookup"><span data-stu-id="8b07d-235">Authentication and authorization in Ocelot API Gateways</span></span>

<span data-ttu-id="8b07d-236">V bráně rozhraní Ocelot API můžete službu ověřování, jako je ASP.NET Core služby webového rozhraní API, nastavovat pomocí [IdentityServer](https://identityserver.io/) , který poskytuje ověřovací token, a to buď nebo uvnitř brány rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="8b07d-236">In an Ocelot API Gateway you can sit the authentication service, such as an ASP.NET Core Web API service using [IdentityServer](https://identityserver.io/) providing the auth token, either out or inside the API Gateway.</span></span>

<span data-ttu-id="8b07d-237">Vzhledem k tomu, že eShopOnContainers používá více bran rozhraní API s hranicemi založenými na BFF a obchodních oblastech, služba identity/auth nepochází z bran rozhraní API, jak je zvýrazněna žlutě v následujícím diagramu.</span><span class="sxs-lookup"><span data-stu-id="8b07d-237">Since eShopOnContainers is using multiple API Gateways with boundaries based on BFF and business areas, the Identity/Auth service is left out of the API Gateways, as highlighted in yellow in the following diagram.</span></span>

![Diagram znázorňující mikroslužbu identity pod bránou API](./media/implement-api-gateways-with-ocelot/eshoponcontainers-identity-service-position.png)

<span data-ttu-id="8b07d-239">**Obrázek 6-39**.</span><span class="sxs-lookup"><span data-stu-id="8b07d-239">**Figure 6-39**.</span></span> <span data-ttu-id="8b07d-240">Pozice služby identity v eShopOnContainers</span><span class="sxs-lookup"><span data-stu-id="8b07d-240">Position of the Identity service in eShopOnContainers</span></span>

<span data-ttu-id="8b07d-241">Ocelot však podporuje i podřízení identity/auth mikroslužby v rámci hranice brány rozhraní API, jako v tomto jiném diagramu.</span><span class="sxs-lookup"><span data-stu-id="8b07d-241">However, Ocelot also supports sitting the Identity/Auth microservice within the API Gateway boundary, as in this other diagram.</span></span>

![Diagram znázorňující ověřování v bráně Ocelot API](./media/implement-api-gateways-with-ocelot/ocelot-authentication.png)

<span data-ttu-id="8b07d-243">**Obrázek 6-40**.</span><span class="sxs-lookup"><span data-stu-id="8b07d-243">**Figure 6-40**.</span></span> <span data-ttu-id="8b07d-244">Ověřování v Ocelot</span><span class="sxs-lookup"><span data-stu-id="8b07d-244">Authentication in Ocelot</span></span>

<span data-ttu-id="8b07d-245">Jak ukazuje předchozí diagram, když je mikroslužba identity pod bránou API (AG): 1) AG vyžádá ověřovací token od mikroslužby identity, 2) mikroslužba identity vrátí token do AG, 3-4) žádosti AG z mikroslužeb pomocí ověřovacího tokenu.</span><span class="sxs-lookup"><span data-stu-id="8b07d-245">As the previous diagram shows, when the Identity microservice is beneath the API gateway (AG): 1) AG requests an auth token from identity microservice, 2) The identity microservice returns token to AG, 3-4) AG requests from microservices using the auth token.</span></span> <span data-ttu-id="8b07d-246">Vzhledem k tomu, že aplikace eShopOnContainers rozdělila bránu API na více BFF (back-end pro front-end) a brány rozhraní API obchodních oblastí, měla by být další možnost vytvoření další brány API pro různé průřezy.</span><span class="sxs-lookup"><span data-stu-id="8b07d-246">Because eShopOnContainers application has split the API Gateway into multiple BFF (Backend for Frontend) and business areas API Gateways, another option would have been to create an additional API Gateway for cross-cutting concerns.</span></span> <span data-ttu-id="8b07d-247">Tato volba by byla poctivá v komplexnější architektuře založené na mikroslužbách s více aspekty, které se na mikroslužby týkají.</span><span class="sxs-lookup"><span data-stu-id="8b07d-247">That choice would be fair in a more complex microservice based architecture with multiple cross-cutting concerns microservices.</span></span> <span data-ttu-id="8b07d-248">Vzhledem k tomu, že v eShopOnContainers existuje pouze jeden problém pro průřez, bylo rozhodnuto pouze zpracovat službu zabezpečení ze sféry brány rozhraní API, a to z důvodu zjednodušení.</span><span class="sxs-lookup"><span data-stu-id="8b07d-248">Since there's only one cross-cutting concern in eShopOnContainers, it was decided to just handle the security service out of the API Gateway realm, for simplicity's sake.</span></span>

<span data-ttu-id="8b07d-249">V každém případě platí, že pokud je aplikace zabezpečená na úrovni brány rozhraní API, při pokusu o použití zabezpečené mikroslužby se nejdřív navštíví modul ověřování brány API Ocelot.</span><span class="sxs-lookup"><span data-stu-id="8b07d-249">In any case, if the app is secured at the API Gateway level, the authentication module of the Ocelot API Gateway is visited at first when trying to use any secured microservice.</span></span> <span data-ttu-id="8b07d-250">Tím přesměruje požadavek HTTP na návštěvu identity nebo auth mikroslužeb, aby získal přístupový token, takže můžete přejít k chráněným službám pomocí access_token.</span><span class="sxs-lookup"><span data-stu-id="8b07d-250">That redirects the HTTP request to visit the Identity or auth microservice to get the access token so you can visit the protected services with the access_token.</span></span>

<span data-ttu-id="8b07d-251">Způsob zabezpečení při ověřování jakékoli služby na úrovni brány rozhraní API je nastavením AuthenticationProviderKey v souvisejícím nastavení v Configuration. JSON.</span><span class="sxs-lookup"><span data-stu-id="8b07d-251">The way you secure with authentication any service at the API Gateway level is by setting the AuthenticationProviderKey in its related settings at the configuration.json.</span></span>

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

<span data-ttu-id="8b07d-252">Když se Ocelot spustí, bude se pohlížet na AuthenticationOptions. AuthenticationProviderKey a zkontroluje, jestli je u daného klíče zaregistrovaný zprostředkovatel ověřování.</span><span class="sxs-lookup"><span data-stu-id="8b07d-252">When Ocelot runs, it will look at the ReRoutes AuthenticationOptions.AuthenticationProviderKey and check that there is an Authentication Provider registered with the given key.</span></span> <span data-ttu-id="8b07d-253">Pokud ne, Ocelot se nespustí.</span><span class="sxs-lookup"><span data-stu-id="8b07d-253">If there isn't, then Ocelot will not start up.</span></span> <span data-ttu-id="8b07d-254">V takovém případě bude přesměrování používat tohoto poskytovatele při jeho spuštění.</span><span class="sxs-lookup"><span data-stu-id="8b07d-254">If there is, then the ReRoute will use that provider when it executes.</span></span>

<span data-ttu-id="8b07d-255">Protože je webhost Ocelot nakonfigurovaný pomocí `authenticationProviderKey = "IdentityApiKey"`, bude vyžadovat ověření vždy, když má služba nějaké požadavky bez tokenu ověřování.</span><span class="sxs-lookup"><span data-stu-id="8b07d-255">Because the Ocelot WebHost is configured with the `authenticationProviderKey = "IdentityApiKey"`, that will require authentication whenever that service has any requests without any auth token.</span></span>

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

<span data-ttu-id="8b07d-256">Pak musíte také nastavit autorizaci pomocí atributu [Authorization] u libovolného prostředku, ke kterému se mají přicházet jako mikroslužby, například v následujícím koši mikrořadiče pro registraci.</span><span class="sxs-lookup"><span data-stu-id="8b07d-256">Then, you also need to set authorization with the [Authorize] attribute on any resource to be accessed like the microservices, such as in the following Basket microservice controller.</span></span>

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

<span data-ttu-id="8b07d-257">ValidAudiences jako "Koš" se koreluje s cílovou skupinou definovanou v každé mikroslužbě s `AddJwtBearer()` na ConfigureServices () třídy po spuštění, jako je například v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="8b07d-257">The ValidAudiences such as "basket" are correlated with the audience defined in each microservice with `AddJwtBearer()` at the ConfigureServices() of the Startup class, such as in the code below.</span></span>

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

<span data-ttu-id="8b07d-258">Pokud se pokusíte o přístup k zabezpečené mikroslužbě, jako je třeba mikroslužba košíku s adresou URL pro přesměrování na základě brány rozhraní API, jako je `http://localhost:5202/api/v1/b/basket/1`, získáte 401 neautorizovaný, pokud nezadáte platný token.</span><span class="sxs-lookup"><span data-stu-id="8b07d-258">If you try to access any secured microservice, like the Basket microservice with a ReRoute URL based on the API Gateway like `http://localhost:5202/api/v1/b/basket/1`, then you'll get a 401 Unauthorized unless you provide a valid token.</span></span> <span data-ttu-id="8b07d-259">Na druhé straně platí, že pokud se ověří adresa URL pro přesměrování, Ocelot vyvolá, že k ní je přidruženo jakékoli mezisystémové schéma (interní adresa URL mikroslužeb).</span><span class="sxs-lookup"><span data-stu-id="8b07d-259">On the other hand, if a ReRoute URL is authenticated, Ocelot will invoke whatever downstream scheme is associated with it (the internal microservice URL).</span></span>

<span data-ttu-id="8b07d-260">**Autorizace na úrovni přesměrování v Ocelot.**</span><span class="sxs-lookup"><span data-stu-id="8b07d-260">**Authorization at Ocelot's ReRoutes tier.**</span></span>  <span data-ttu-id="8b07d-261">Ocelot podporuje ověřování na základě deklarace identity vyhodnocené po ověření.</span><span class="sxs-lookup"><span data-stu-id="8b07d-261">Ocelot supports claims-based authorization evaluated after the authentication.</span></span> <span data-ttu-id="8b07d-262">Autorizaci nastavíte na úrovni trasy přidáním následujících řádků do konfigurace přesměrování.</span><span class="sxs-lookup"><span data-stu-id="8b07d-262">You set the authorization at a route level by adding the following lines to the ReRoute configuration.</span></span>

```json
"RouteClaimsRequirement": {
    "UserType": "employee"
}
```

<span data-ttu-id="8b07d-263">V tomto příkladu, když se volá middleware autorizace, Ocelot zjistí, jestli má uživatel v tokenu typ s deklarací UserType, a pokud je hodnota této deklarace identity Employee.</span><span class="sxs-lookup"><span data-stu-id="8b07d-263">In that example, when the authorization middleware is called, Ocelot will find if the user has the claim type 'UserType' in the token and if the value of that claim is 'employee'.</span></span> <span data-ttu-id="8b07d-264">Pokud ne, uživatel nebude autorizovaný a odpověď bude 403 zakázaná.</span><span class="sxs-lookup"><span data-stu-id="8b07d-264">If it isn't, then the user will not be authorized and the response will be 403 forbidden.</span></span>

## <a name="using-kubernetes-ingress-plus-ocelot-api-gateways"></a><span data-ttu-id="8b07d-265">Použití Kubernetes a Ocelot API Gateway</span><span class="sxs-lookup"><span data-stu-id="8b07d-265">Using Kubernetes Ingress plus Ocelot API Gateways</span></span>

<span data-ttu-id="8b07d-266">Při použití Kubernetes (jako v clusteru služby Azure Kubernetes) obvykle sjednotete všechny požadavky HTTP prostřednictvím [vrstvy Kubernetes](https://kubernetes.io/docs/concepts/services-networking/ingress/) příchozího přenosu dat založené na *Nginx*.</span><span class="sxs-lookup"><span data-stu-id="8b07d-266">When using Kubernetes (like in an Azure Kubernetes Service cluster), you usually unify all the HTTP requests through the [Kubernetes Ingress tier](https://kubernetes.io/docs/concepts/services-networking/ingress/) based on *Nginx*.</span></span>

<span data-ttu-id="8b07d-267">Pokud v Kubernetes nepoužíváte žádný přístup k příchozímu přístupu, pak vaše služby a lusky mají IP adresy směrovatelné jenom na síť s clustery.</span><span class="sxs-lookup"><span data-stu-id="8b07d-267">In Kubernetes, if you don't use any ingress approach, then your services and pods have IPs only routable by the cluster network.</span></span>

<span data-ttu-id="8b07d-268">Pokud ale použijete přístup příchozího přenosu dat, budete mít střední vrstvu mezi Internetem a vašimi službami (včetně vašich bran rozhraní API), které fungují jako reverzní proxy server.</span><span class="sxs-lookup"><span data-stu-id="8b07d-268">But if you use an ingress approach, you'll have a middle tier between the Internet and your services (including your API Gateways), acting as a reverse proxy.</span></span>

<span data-ttu-id="8b07d-269">V rámci definice příchozího přenosu dat je kolekce pravidel, která povolují příchozí připojení k dosažení clusterových služeb.</span><span class="sxs-lookup"><span data-stu-id="8b07d-269">As a definition, an Ingress is a collection of rules that allow inbound connections to reach the cluster services.</span></span> <span data-ttu-id="8b07d-270">Příchozí přenos dat je obvykle nakonfigurovaný tak, aby poskytoval služby externě dosažitelným adresám URL, provozu vyrovnávání zatížení, ukončení protokolu SSL a dalším.</span><span class="sxs-lookup"><span data-stu-id="8b07d-270">An ingress is usually configured to provide services externally reachable URLs, load balance traffic, SSL termination and more.</span></span> <span data-ttu-id="8b07d-271">Uživatelé požadují příchozí odesílání prostředků příchozího přenosu dat na Server API.</span><span class="sxs-lookup"><span data-stu-id="8b07d-271">Users request ingress by POSTing the Ingress resource to the API server.</span></span>

<span data-ttu-id="8b07d-272">V eShopOnContainers při vývoji místně a jenom pomocí vývojového počítače jako hostitele Docker nepoužíváte žádné příchozí přenosy, ale jenom několik bran rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="8b07d-272">In eShopOnContainers, when developing locally and using just your development machine as the Docker host, you are not using any ingress but only the multiple API Gateways.</span></span>

<span data-ttu-id="8b07d-273">Pokud ale zacílíte na prostředí "produkční" prostředí založené na Kubernetes, eShopOnContainers za brány rozhraní API používá příchozí přenos dat.</span><span class="sxs-lookup"><span data-stu-id="8b07d-273">However, when targeting a "production" environment based on Kubernetes, eShopOnContainers is using an ingress in front of the API gateways.</span></span> <span data-ttu-id="8b07d-274">Klienti tak budou stále volat stejnou základní adresu URL, ale požadavky jsou směrovány na více bran rozhraní API nebo BFF.</span><span class="sxs-lookup"><span data-stu-id="8b07d-274">That way, the clients still call the same base URL but the requests are routed to multiple API Gateways or BFF.</span></span>

<span data-ttu-id="8b07d-275">Brány rozhraní API jsou front-endy nebo fasády zpřístupnění jenom služby, ale ne webové aplikace, které jsou obvykle mimo svůj rozsah.</span><span class="sxs-lookup"><span data-stu-id="8b07d-275">API Gateways are front-ends or façades surfacing only the services but not the web applications that are usually out of their scope.</span></span> <span data-ttu-id="8b07d-276">Brány rozhraní API navíc můžou některé interní mikroslužby skrýt.</span><span class="sxs-lookup"><span data-stu-id="8b07d-276">In addition, the API Gateways might hide certain internal microservices.</span></span>

<span data-ttu-id="8b07d-277">Příchozí přenos dat se ale právě přesměrovává na požadavky HTTP, ale nepokouší se skrýt žádnou mikroslužbu nebo webovou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="8b07d-277">The ingress, however, is just redirecting HTTP requests but not trying to hide any microservice or web app.</span></span>

<span data-ttu-id="8b07d-278">Mít v Kubernetes před webovými aplikacemi úroveň příchozího Nginxu a několik bran Ocelot API/BFF je ideální architekturou, jak je znázorněno v následujícím diagramu.</span><span class="sxs-lookup"><span data-stu-id="8b07d-278">Having an ingress Nginx tier in Kubernetes in front of the web applications plus the several Ocelot API Gateways / BFF is the ideal architecture, as shown in the following diagram.</span></span>

![Diagram znázorňující, jak úroveň příchozího připadá do prostředí AKS.](./media/implement-api-gateways-with-ocelot/eshoponcontainer-ingress-tier.png)

<span data-ttu-id="8b07d-280">**Obrázek 6-41**.</span><span class="sxs-lookup"><span data-stu-id="8b07d-280">**Figure 6-41**.</span></span> <span data-ttu-id="8b07d-281">Úroveň příchozího přenosu v eShopOnContainers při nasazení do Kubernetes</span><span class="sxs-lookup"><span data-stu-id="8b07d-281">The ingress tier in eShopOnContainers when deployed into Kubernetes</span></span>

<span data-ttu-id="8b07d-282">Kubernetes příchozí připojení funguje jako reverzní proxy server pro veškerý provoz do aplikace, včetně webových aplikací, které jsou obvykle mimo rozsah brány rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="8b07d-282">A Kubernetes Ingress acts as a reverse proxy for all traffic to the app, including the web applications, that are usually out of the Api gateway scope.</span></span> <span data-ttu-id="8b07d-283">Když nasadíte eShopOnContainers do Kubernetes, zveřejňuje se v podstatě jenom pár služeb nebo koncových _bodů, a_to v podstatě následující seznam přípon v adresách URL:</span><span class="sxs-lookup"><span data-stu-id="8b07d-283">When you deploy eShopOnContainers into Kubernetes, it exposes just a few services or endpoints via _ingress_, basically the following list of postfixes on the URLs:</span></span>

- <span data-ttu-id="8b07d-284">`/` webové aplikace SPA klienta</span><span class="sxs-lookup"><span data-stu-id="8b07d-284">`/` for the client SPA web application</span></span>
- <span data-ttu-id="8b07d-285">`/webmvc` webové aplikace MVC klienta</span><span class="sxs-lookup"><span data-stu-id="8b07d-285">`/webmvc` for the client MVC web application</span></span>
- <span data-ttu-id="8b07d-286">`/webstatus` pro webovou aplikaci klienta zobrazující stav/healthchecks</span><span class="sxs-lookup"><span data-stu-id="8b07d-286">`/webstatus` for the client web app showing the status/healthchecks</span></span>
- <span data-ttu-id="8b07d-287">`/webshoppingapigw` pro webové BFF a nákupní obchodní procesy</span><span class="sxs-lookup"><span data-stu-id="8b07d-287">`/webshoppingapigw` for the web BFF and shopping business processes</span></span>
- <span data-ttu-id="8b07d-288">`/webmarketingapigw` pro webové BFF a marketingové obchodní procesy</span><span class="sxs-lookup"><span data-stu-id="8b07d-288">`/webmarketingapigw` for the web BFF and marketing business processes</span></span>
- <span data-ttu-id="8b07d-289">`/mobileshoppingapigw` pro mobilní procesy BFF a nákup obchodních procesů</span><span class="sxs-lookup"><span data-stu-id="8b07d-289">`/mobileshoppingapigw` for the mobile BFF and shopping business processes</span></span>
- <span data-ttu-id="8b07d-290">`/mobilemarketingapigw` pro obchodní procesy Mobile BFF a marketing</span><span class="sxs-lookup"><span data-stu-id="8b07d-290">`/mobilemarketingapigw` for the mobile BFF and marketing business processes</span></span>

<span data-ttu-id="8b07d-291">Při nasazování do Kubernetes každá brána API Ocelot používá jiný soubor Configuration. JSON pro každý _pod_ spuštěným bránou rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="8b07d-291">When deploying to Kubernetes, each Ocelot API Gateway is using a different "configuration.json" file for each _pod_ running the API Gateways.</span></span> <span data-ttu-id="8b07d-292">Tyto soubory "Configuration. JSON" jsou k dispozici připojením (původně pomocí skriptu Deploy. ps1) vytvořeného svazku založeného na _mapě konfigurace_ Kubernetes s názvem Ocelot.</span><span class="sxs-lookup"><span data-stu-id="8b07d-292">Those "configuration.json" files are provided by mounting (originally with the deploy.ps1 script) a volume created based on a Kubernetes _config map_ named ‘ocelot'.</span></span> <span data-ttu-id="8b07d-293">Každý kontejner připojí svůj související konfigurační soubor do složky kontejneru s názvem `/app/configuration`.</span><span class="sxs-lookup"><span data-stu-id="8b07d-293">Each container mounts its related configuration file in the container's folder named `/app/configuration`.</span></span>

<span data-ttu-id="8b07d-294">V souborech zdrojového kódu eShopOnContainers lze původní soubory "Configuration. JSON" najít v rámci `k8s/ocelot/` složky.</span><span class="sxs-lookup"><span data-stu-id="8b07d-294">In the source code files of eShopOnContainers, the original "configuration.json" files can be found within the `k8s/ocelot/` folder.</span></span> <span data-ttu-id="8b07d-295">Pro každou BFF/APIGateway existuje jeden soubor.</span><span class="sxs-lookup"><span data-stu-id="8b07d-295">There's one file for each BFF/APIGateway.</span></span>

## <a name="additional-cross-cutting-features-in-an-ocelot-api-gateway"></a><span data-ttu-id="8b07d-296">Další funkce pro křížové vyjmutí v bráně API Ocelot</span><span class="sxs-lookup"><span data-stu-id="8b07d-296">Additional cross-cutting features in an Ocelot API Gateway</span></span>

<span data-ttu-id="8b07d-297">Při použití brány Ocelot API jsou k dispozici další důležité funkce, které je potřeba prozkoumat a použít.</span><span class="sxs-lookup"><span data-stu-id="8b07d-297">There are other important features to research and use, when using an Ocelot API Gateway, described in the following links.</span></span>

- <span data-ttu-id="8b07d-298">**Zjišťování služby na straně klienta integrace Ocelot s Consul nebo Eureka** </span><span class="sxs-lookup"><span data-stu-id="8b07d-298">**Service discovery in the client side integrating Ocelot with Consul or Eureka** </span></span>\
  <https://ocelot.readthedocs.io/en/latest/features/servicediscovery.html>

- <span data-ttu-id="8b07d-299">**Ukládání do mezipaměti na úrovni brány API** </span><span class="sxs-lookup"><span data-stu-id="8b07d-299">**Caching at the API Gateway tier** </span></span>\
  <https://ocelot.readthedocs.io/en/latest/features/caching.html>

- <span data-ttu-id="8b07d-300">**Protokolování na úrovni brány API** </span><span class="sxs-lookup"><span data-stu-id="8b07d-300">**Logging at the API Gateway tier** </span></span>\
  <https://ocelot.readthedocs.io/en/latest/features/logging.html>

- <span data-ttu-id="8b07d-301">**Kvalita služby (opakování a přerušení okruhů) na úrovni brány rozhraní API** </span><span class="sxs-lookup"><span data-stu-id="8b07d-301">**Quality of Service (Retries and Circuit breakers) at the API Gateway tier** </span></span>\
  <https://ocelot.readthedocs.io/en/latest/features/qualityofservice.html>

- <span data-ttu-id="8b07d-302">**Omezení rychlosti** </span><span class="sxs-lookup"><span data-stu-id="8b07d-302">**Rate limiting** </span></span>\
  [https://ocelot.readthedocs.io/en/latest/features/ratelimiting.html](https://ocelot.readthedocs.io/en/latest/features/ratelimiting.html )

> [!div class="step-by-step"]
> <span data-ttu-id="8b07d-303">[Předchozí](background-tasks-with-ihostedservice.md)
> [Další](../microservice-ddd-cqrs-patterns/index.md)</span><span class="sxs-lookup"><span data-stu-id="8b07d-303">[Previous](background-tasks-with-ihostedservice.md)
[Next](../microservice-ddd-cqrs-patterns/index.md)</span></span>
