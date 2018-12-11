---
title: Definování vícekontejnerové aplikace pomocí docker-compose.yml
description: Architektura Mikroslužeb .NET pro Kontejnerizované aplikace .NET | Jak určit složení mikroslužeb pro vícekontejnerových aplikací pomocí docker-compose.yml.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/02/2018
ms.openlocfilehash: dc9149cb1a17e3af66abd995fd2a2196109e0e05
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53145251"
---
# <a name="defining-your-multi-container-application-with-docker-composeyml"></a><span data-ttu-id="4cf94-103">Definování vícekontejnerové aplikace pomocí docker-compose.yml</span><span class="sxs-lookup"><span data-stu-id="4cf94-103">Defining your multi-container application with docker-compose.yml</span></span> 

<span data-ttu-id="4cf94-104">V této příručce [docker-compose.yml](https://docs.docker.com/compose/compose-file/) souboru byla zavedena v části [kroku 4. Definování vašich služeb v docker-compose.yml při sestavování aplikace více kontejnerů Dockeru](../docker-application-development-process/docker-app-development-workflow.md#step-4-define-your-services-in-docker-composeyml-when-building-a-multi-container-docker-application).</span><span class="sxs-lookup"><span data-stu-id="4cf94-104">In this guide, the [docker-compose.yml](https://docs.docker.com/compose/compose-file/) file was introduced in the section [Step 4. Define your services in docker-compose.yml when building a multi-container Docker application](../docker-application-development-process/docker-app-development-workflow.md#step-4-define-your-services-in-docker-composeyml-when-building-a-multi-container-docker-application).</span></span> <span data-ttu-id="4cf94-105">Existují však další způsoby, jak používat docker-compose soubory, které stojí za prozkoumání podrobněji.</span><span class="sxs-lookup"><span data-stu-id="4cf94-105">However, there are additional ways to use the docker-compose files that are worth exploring in further detail.</span></span>

<span data-ttu-id="4cf94-106">Například můžete výslovně popsat, jak chcete nasadit vícekontejnerové aplikace v souboru docker-compose.yml.</span><span class="sxs-lookup"><span data-stu-id="4cf94-106">For example, you can explicitly describe how you want to deploy your multi-container application in the docker-compose.yml file.</span></span> <span data-ttu-id="4cf94-107">Volitelně může také popisovat, jak chcete sestavit vlastní Image Dockeru.</span><span class="sxs-lookup"><span data-stu-id="4cf94-107">Optionally, you can also describe how you are going to build your custom Docker images.</span></span> <span data-ttu-id="4cf94-108">(Vlastní Image Dockeru se dají taky vytvářet pomocí rozhraní příkazového řádku Dockeru.)</span><span class="sxs-lookup"><span data-stu-id="4cf94-108">(Custom Docker images can also be built with the Docker CLI.)</span></span>

<span data-ttu-id="4cf94-109">V podstatě definování všech kontejnerů, které chcete nasadit, a navíc určité vlastnosti pro každý kontejner nasazení.</span><span class="sxs-lookup"><span data-stu-id="4cf94-109">Basically, you define each of the containers you want to deploy plus certain characteristics for each container deployment.</span></span> <span data-ttu-id="4cf94-110">Jakmile budete mít soubor s popisem nasazení více kontejnerů, můžete nasadit celé řešení v rámci jedné akce orchestrované systémem [docker-compose up](https://docs.docker.com/compose/overview/) příkazu rozhraní příkazového řádku, nebo ji můžete nasadit transparentně ze sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="4cf94-110">Once you have a multi-container deployment description file, you can deploy the whole solution in a single action orchestrated by the [docker-compose up](https://docs.docker.com/compose/overview/) CLI command, or you can deploy it transparently from Visual Studio.</span></span> <span data-ttu-id="4cf94-111">V opačném případě je třeba použít k nasazení kontejnerů pomocí kontejneru v několika krocích pomocí rozhraní příkazového řádku Dockeru `docker run` příkazu z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="4cf94-111">Otherwise, you would need to use the Docker CLI to deploy container-by-container in multiple steps by using the `docker run` command from the command line.</span></span> <span data-ttu-id="4cf94-112">Jednotlivé služby definované v docker-compose.yml proto musíte zadat právě jednu image nebo sestavení.</span><span class="sxs-lookup"><span data-stu-id="4cf94-112">Therefore, each service defined in docker-compose.yml must specify exactly one image or build.</span></span> <span data-ttu-id="4cf94-113">Další klíče jsou volitelné a odpovídají jejich `docker run` příkazového řádku protějšky.</span><span class="sxs-lookup"><span data-stu-id="4cf94-113">Other keys are optional, and are analogous to their `docker run` command-line counterparts.</span></span>

<span data-ttu-id="4cf94-114">Následující kód YAML je definice je to možné globální, ale jeden soubor docker-compose.yml pro vzorovou aplikaci eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="4cf94-114">The following YAML code is the definition of a possible global but single docker-compose.yml file for the eShopOnContainers sample.</span></span> <span data-ttu-id="4cf94-115">Toto není skutečný docker-compose soubor v aplikaci eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="4cf94-115">This is not the actual docker-compose file from eShopOnContainers.</span></span> <span data-ttu-id="4cf94-116">Místo toho je zjednodušený a konsolidované verze jednoho souboru, který není nejlepší způsob, jak pracovat s souborů docker-compose, jak budou vysvětlena dále.</span><span class="sxs-lookup"><span data-stu-id="4cf94-116">Instead, it is a simplified and consolidated version in a single file, which is not the best way to work with docker-compose files, as will be explained later.</span></span>

```yml
version: '3.4'

services:
  webmvc:
    image: eshop/webmvc
    environment:
      - CatalogUrl=http://catalog.api
      - OrderingUrl=http://ordering.api
      - BasketUrl=http://basket.api
    ports:
      - "5100:80"
    depends_on:
      - catalog.api
      - ordering.api
      - basket.api

  catalog.api:
    image: eshop/catalog.api
    environment:
      - ConnectionString=Server=sql.data;Initial Catalog=CatalogData;User Id=sa;Password=your@password
    expose:
      - "80"
    ports:
      - "5101:80"
    #extra hosts can be used for standalone SQL Server or services at the dev PC
    extra_hosts:
      - "CESARDLSURFBOOK:10.0.75.1"
    depends_on:
      - sql.data

  ordering.api:
    image: eshop/ordering.api
    environment:
      - ConnectionString=Server=sql.data;Database=Services.OrderingDb;User Id=sa;Password=your@password
    ports:
      - "5102:80"
    #extra hosts can be used for standalone SQL Server or services at the dev PC
    extra_hosts:
      - "CESARDLSURFBOOK:10.0.75.1"
    depends_on:
      - sql.data

  basket.api:
    image: eshop/basket.api
    environment:
      - ConnectionString=sql.data
    ports:
      - "5103:80"
    depends_on:
      - sql.data

  sql.data:
    environment:
      - SA_PASSWORD=your@password
      - ACCEPT_EULA=Y
    ports:
      - "5434:1433"

  basket.data:
    image: redis
```

<span data-ttu-id="4cf94-117">Kořenový klíč z tohoto souboru se služby.</span><span class="sxs-lookup"><span data-stu-id="4cf94-117">The root key in this file is services.</span></span> <span data-ttu-id="4cf94-118">Pod tímto klíčem definujete služby chcete nasadit a spustit při spouštění `docker-compose up` příkaz nebo při nasazení ze sady Visual Studio s použitím tohoto souboru docker-compose.yml.</span><span class="sxs-lookup"><span data-stu-id="4cf94-118">Under that key you define the services you want to deploy and run when you execute the `docker-compose up` command or when you deploy from Visual Studio by using this docker-compose.yml file.</span></span> <span data-ttu-id="4cf94-119">V tomto případě soubor docker-compose.yml má několik služeb, které jsou definovány, jak je popsáno v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="4cf94-119">In this case, the docker-compose.yml file has multiple services defined, as described in the following table.</span></span>

| <span data-ttu-id="4cf94-120">Název služby</span><span class="sxs-lookup"><span data-stu-id="4cf94-120">Service name</span></span> | <span data-ttu-id="4cf94-121">Popis</span><span class="sxs-lookup"><span data-stu-id="4cf94-121">Description</span></span> |
|--------------|-------------|
| <span data-ttu-id="4cf94-122">webmvc</span><span class="sxs-lookup"><span data-stu-id="4cf94-122">webmvc</span></span>       | <span data-ttu-id="4cf94-123">Kontejneru, včetně aplikací ASP.NET Core MVC využívání mikroslužeb from C na straně serveru\#</span><span class="sxs-lookup"><span data-stu-id="4cf94-123">Container including the ASP.NET Core MVC application consuming the microservices from server-side C\#</span></span>|
| <span data-ttu-id="4cf94-124">CATALOG.API</span><span class="sxs-lookup"><span data-stu-id="4cf94-124">catalog.api</span></span>  | <span data-ttu-id="4cf94-125">Kontejner včetně katalogu ASP.NET Core webového rozhraní API mikroslužby</span><span class="sxs-lookup"><span data-stu-id="4cf94-125">Container including the Catalog ASP.NET Core Web API microservice</span></span> |
| <span data-ttu-id="4cf94-126">Ordering.API</span><span class="sxs-lookup"><span data-stu-id="4cf94-126">ordering.api</span></span> | <span data-ttu-id="4cf94-127">Kontejner včetně řazení ASP.NET Core webového rozhraní API mikroslužby</span><span class="sxs-lookup"><span data-stu-id="4cf94-127">Container including the Ordering ASP.NET Core Web API microservice</span></span> |
| <span data-ttu-id="4cf94-128">SQL.data</span><span class="sxs-lookup"><span data-stu-id="4cf94-128">sql.data</span></span>     | <span data-ttu-id="4cf94-129">Kontejner systémem SQL Server pro Linux, uchovávající databází mikroslužeb</span><span class="sxs-lookup"><span data-stu-id="4cf94-129">Container running SQL Server for Linux, holding the microservices databases</span></span> |
| <span data-ttu-id="4cf94-130">basket.API</span><span class="sxs-lookup"><span data-stu-id="4cf94-130">basket.api</span></span>   | <span data-ttu-id="4cf94-131">Kontejner s nákupní košík ASP.NET Core webového rozhraní API mikroslužby</span><span class="sxs-lookup"><span data-stu-id="4cf94-131">Container with the Basket ASP.NET Core Web API microservice</span></span> |
| <span data-ttu-id="4cf94-132">basket.data</span><span class="sxs-lookup"><span data-stu-id="4cf94-132">basket.data</span></span>  | <span data-ttu-id="4cf94-133">Spuštění REDIS kontejneru služby cache service, s databází nákupní košík jako mezipaměť REDIS</span><span class="sxs-lookup"><span data-stu-id="4cf94-133">Container running the REDIS cache service, with the basket database as a REDIS cache</span></span> |

### <a name="a-simple-web-service-api-container"></a><span data-ttu-id="4cf94-134">Jednoduchý kontejner rozhraní API webové služby</span><span class="sxs-lookup"><span data-stu-id="4cf94-134">A simple Web Service API container</span></span>

<span data-ttu-id="4cf94-135">Se zaměříte na jediný kontejner, kontejner catalog.api-mikroslužeb má jednoduché definici:</span><span class="sxs-lookup"><span data-stu-id="4cf94-135">Focusing on a single container, the catalog.api container-microservice has a straightforward definition:</span></span>

```yml
  catalog.api:
    image: eshop/catalog.api
    environment:
      - ConnectionString=Server=sql.data;Initial Catalog=CatalogData;User Id=sa;Password=your@password
    expose:
      - "80"
    ports:
      - "5101:80"
    #extra hosts can be used for standalone SQL Server or services at the dev PC
    extra_hosts:
      - "CESARDLSURFBOOK:10.0.75.1"
    depends_on:
      - sql.data
```

<span data-ttu-id="4cf94-136">Tato kontejnerizovaná služba má následující základní konfigurace:</span><span class="sxs-lookup"><span data-stu-id="4cf94-136">This containerized service has the following basic configuration:</span></span>

-   <span data-ttu-id="4cf94-137">Je založena na imagi vlastní eshop/catalog.api.</span><span class="sxs-lookup"><span data-stu-id="4cf94-137">It is based on the custom eshop/catalog.api image.</span></span> <span data-ttu-id="4cf94-138">Pro jednoduchost saké neexistuje žádné sestavení: nastavení v souboru klíče.</span><span class="sxs-lookup"><span data-stu-id="4cf94-138">For simplicity’s sake, there is no build: key setting in the file.</span></span> <span data-ttu-id="4cf94-139">To znamená, že obrázek musí mít byla dříve vytvořena (pomocí sestavení dockeru) se stáhly (pomocí příkazu docker pull) z libovolného registru Dockeru.</span><span class="sxs-lookup"><span data-stu-id="4cf94-139">This means that the image must have been previously built (with docker build) or have been downloaded (with the docker pull command) from any Docker registry.</span></span>

-   <span data-ttu-id="4cf94-140">Definuje proměnnou prostředí s názvem připojovací řetězec připojovacím řetězcem Entity Framework používané pro přístup k instanci serveru SQL Server, který obsahuje datový model katalogu.</span><span class="sxs-lookup"><span data-stu-id="4cf94-140">It defines an environment variable named ConnectionString with the connection string to be used by Entity Framework to access the SQL Server instance that contains the catalog data model.</span></span> <span data-ttu-id="4cf94-141">V takovém případě stejného kontejneru systému SQL Server obsahuje více databází.</span><span class="sxs-lookup"><span data-stu-id="4cf94-141">In this case, the same SQL Server container is holding multiple databases.</span></span> <span data-ttu-id="4cf94-142">Proto je nutné méně paměti v počítači pro vývoj pro Docker.</span><span class="sxs-lookup"><span data-stu-id="4cf94-142">Therefore, you need less memory in your development machine for Docker.</span></span> <span data-ttu-id="4cf94-143">Můžete však také nasadit jeden kontejner systému SQL Server pro každou databázi mikroslužeb.</span><span class="sxs-lookup"><span data-stu-id="4cf94-143">However, you could also deploy one SQL Server container for each microservice database.</span></span>

-   <span data-ttu-id="4cf94-144">Název systému SQL Server je sql.data, které se stejným názvem, který pro kontejner, na kterém běží instance systému SQL Server pro Linux.</span><span class="sxs-lookup"><span data-stu-id="4cf94-144">The SQL Server name is sql.data, which is the same name used for the container that is running the SQL Server instance for Linux.</span></span> <span data-ttu-id="4cf94-145">Tato možnost je pohodlná; bude možné použít tento překlad (interní hostitele Dockeru) vyřeší síťovou adresu, takže není nutné znát interní IP adresa pro kontejnery, které spouštíte z jiných kontejnerů.</span><span class="sxs-lookup"><span data-stu-id="4cf94-145">This is convenient; being able to use this name resolution (internal to the Docker host) will resolve the network address so you don’t need to know the internal IP for the containers you are accessing from other containers.</span></span>

<span data-ttu-id="4cf94-146">Vzhledem k tomu, že připojovací řetězec je určené proměnnou prostředí, můžete tuto proměnnou nastavit prostřednictvím jiným způsobem a jiný čas.</span><span class="sxs-lookup"><span data-stu-id="4cf94-146">Because the connection string is defined by an environment variable, you could set that variable through a different mechanism and at a different time.</span></span> <span data-ttu-id="4cf94-147">Například můžete nastavit různé připojovací řetězec při nasazení do produkčního prostředí v posledním hostitele nebo provedením z vašich kanálů CI/CD v Azure DevOps služby nebo systému upřednostňované DevOps.</span><span class="sxs-lookup"><span data-stu-id="4cf94-147">For example, you could set a different connection string when deploying to production in the final hosts, or by doing it from your CI/CD pipelines in Azure DevOps Services or your preferred DevOps system.</span></span>

-   <span data-ttu-id="4cf94-148">Zpřístupňuje port 80 pro interní přístup ke službě catalog.api v rámci hostitele Dockeru.</span><span class="sxs-lookup"><span data-stu-id="4cf94-148">It exposes port 80 for internal access to the catalog.api service within the Docker host.</span></span> <span data-ttu-id="4cf94-149">Hostitel je aktuálně virtuálního počítače s Linuxem, protože je založen na image Dockeru pro Linux, ale můžete nakonfigurovat tak, kontejner pro spuštění v imagi Windows místo.</span><span class="sxs-lookup"><span data-stu-id="4cf94-149">The host is currently a Linux VM because it is based on a Docker image for Linux, but you could configure the container to run on a Windows image instead.</span></span>

-   <span data-ttu-id="4cf94-150">Předá vystavené port 80 v kontejneru na port 5101 hostitele Docker Machine (virtuálního počítače s Linuxem).</span><span class="sxs-lookup"><span data-stu-id="4cf94-150">It forwards the exposed port 80 on the container to port 5101 on the Docker host machine (the Linux VM).</span></span>

-   <span data-ttu-id="4cf94-151">Webové služby odkazuje ve službě sql.data (instance systému SQL Server pro Linux databáze spuštěné v kontejneru).</span><span class="sxs-lookup"><span data-stu-id="4cf94-151">It links the web service to the sql.data service (the SQL Server instance for Linux database running in a container).</span></span> <span data-ttu-id="4cf94-152">Pokud zadáte tuto závislost, kontejneru catalog.api nespustí, dokud již bylo zahájeno sql.data kontejneru; To je důležité, protože catalog.api musí být databáze serveru SQL Server a spuštěna nejprve.</span><span class="sxs-lookup"><span data-stu-id="4cf94-152">When you specify this dependency, the catalog.api container will not start until the sql.data container has already started; this is important because catalog.api needs to have the SQL Server database up and running first.</span></span> <span data-ttu-id="4cf94-153">Však tento druh závislosti kontejneru není dostatečně v mnoha případech, protože Docker zkontroluje pouze na úrovni kontejneru.</span><span class="sxs-lookup"><span data-stu-id="4cf94-153">However, this kind of container dependency is not enough in many cases, because Docker checks only at the container level.</span></span> <span data-ttu-id="4cf94-154">Někdy služby (v tomto případě systému SQL Server) nemusí nadále budete mít, proto se doporučuje implementovat logiku opakování pomocí exponenciálního omezení rychlosti mikroslužby klienta.</span><span class="sxs-lookup"><span data-stu-id="4cf94-154">Sometimes the service (in this case SQL Server) might still not be ready, so it is advisable to implement retry logic with exponential backoff in your client microservices.</span></span> <span data-ttu-id="4cf94-155">Tímto způsobem, pokud kontejner závislosti není připravený na krátkou dobu, aplikace bude nadále odolný.</span><span class="sxs-lookup"><span data-stu-id="4cf94-155">That way, if a dependency container is not ready for a short time, the application will still be resilient.</span></span>

-   <span data-ttu-id="4cf94-156">Je nakonfigurována pro povolení přístupu k externím serverům: nadbytečné\_hostitelů nastavení vám umožní přistupovat k externí servery nebo počítače mimo hostitele Docker (tedy mimo výchozí linuxového virtuálního počítače, který je vývoj Docker hostitele), jako je například místní databáze SQL Instance serveru na vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="4cf94-156">It is configured to allow access to external servers: the extra\_hosts setting allows you to access external servers or machines outside of the Docker host (that is, outside the default Linux VM which is a development Docker host), such as a local SQL Server instance on your development PC.</span></span>

<span data-ttu-id="4cf94-157">Existují také jiné, pokročilejší docker-compose.yml nastavení, které se budeme zabývat v dalších částech.</span><span class="sxs-lookup"><span data-stu-id="4cf94-157">There are also other, more advanced docker-compose.yml settings that we will discuss in the following sections.</span></span>

### <a name="using-docker-compose-files-to-target-multiple-environments"></a><span data-ttu-id="4cf94-158">Pomocí souborů docker-compose cílit na více prostředí</span><span class="sxs-lookup"><span data-stu-id="4cf94-158">Using docker-compose files to target multiple environments</span></span>

<span data-ttu-id="4cf94-159">Soubory docker-compose.yml jsou soubory definic a mohou být využívána více infrastruktury, které rozumí formátu.</span><span class="sxs-lookup"><span data-stu-id="4cf94-159">The docker-compose.yml files are definition files and can be used by multiple infrastructures that understand that format.</span></span> <span data-ttu-id="4cf94-160">Nástroj nejjednodušší je příkazu docker-compose.</span><span class="sxs-lookup"><span data-stu-id="4cf94-160">The most straightforward tool is the docker-compose command.</span></span>

<span data-ttu-id="4cf94-161">Proto se s použitím příkazu je možné cílit na následující hlavní scénáře docker-compose.</span><span class="sxs-lookup"><span data-stu-id="4cf94-161">Therefore, by using the docker-compose command you can target the following main scenarios.</span></span>

#### <a name="development-environments"></a><span data-ttu-id="4cf94-162">Vývojová prostředí</span><span class="sxs-lookup"><span data-stu-id="4cf94-162">Development environments</span></span>

<span data-ttu-id="4cf94-163">Při vývoji aplikací, je důležité, aby bylo možné spouštět aplikace v izolovaném vývojové prostředí.</span><span class="sxs-lookup"><span data-stu-id="4cf94-163">When you develop applications, it is important to be able to run an application in an isolated development environment.</span></span> <span data-ttu-id="4cf94-164">Můžete použít příkazu rozhraní příkazového řádku k vytvoření tohoto prostředí nebo pomocí sady Visual Studio, který používá docker-compose pod pokličkou docker-compose.</span><span class="sxs-lookup"><span data-stu-id="4cf94-164">You can use the docker-compose CLI command to create that environment or use Visual Studio which uses docker-compose under the covers.</span></span>

<span data-ttu-id="4cf94-165">Soubor docker-compose.yml umožňuje konfigurovat a dokumentovat závislosti služby všechny aplikace (jiné služby, mezipaměti, databáze, fronty atd.).</span><span class="sxs-lookup"><span data-stu-id="4cf94-165">The docker-compose.yml file allows you to configure and document all your application’s service dependencies (other services, cache, databases, queues, etc.).</span></span> <span data-ttu-id="4cf94-166">Použití docker-compose příkazu rozhraní příkazového řádku, můžete vytvořit a spustit jeden nebo více kontejnerů pro každý závislosti pomocí jediného příkazu (docker-compose up).</span><span class="sxs-lookup"><span data-stu-id="4cf94-166">Using the docker-compose CLI command, you can create and start one or more containers for each dependency with a single command (docker-compose up).</span></span>

<span data-ttu-id="4cf94-167">Soubory docker-compose.yml jsou konfigurační soubory interpretovat modul Docker, ale sloužit také jako soubory pohodlný dokumentace o složení vícekontejnerovou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="4cf94-167">The docker-compose.yml files are configuration files interpreted by Docker engine but also serve as convenient documentation files about the composition of your multi-container application.</span></span>

#### <a name="testing-environments"></a><span data-ttu-id="4cf94-168">Testovací prostředí</span><span class="sxs-lookup"><span data-stu-id="4cf94-168">Testing environments</span></span>

<span data-ttu-id="4cf94-169">Důležitou součástí procesu kontinuální integrace (CI) ani průběžného nasazování (CD) jsou testy jednotek a integrační testy.</span><span class="sxs-lookup"><span data-stu-id="4cf94-169">An important part of any continuous deployment (CD) or continuous integration (CI) process are the unit tests and integration tests.</span></span> <span data-ttu-id="4cf94-170">Tyto automatizované testy vyžadují izolovaného prostředí, takže nejsou ovlivněny uživatelů nebo jiné změny v datech vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="4cf94-170">These automated tests require an isolated environment so they are not impacted by the users or any other change in the application’s data.</span></span>

<span data-ttu-id="4cf94-171">Pomocí Docker Compose můžete vytvořit a odstranit izolované prostředí velmi snadno v několika příkazů z příkazového řádku nebo skripty, například následující příkazy:</span><span class="sxs-lookup"><span data-stu-id="4cf94-171">With Docker Compose you can create and destroy that isolated environment very easily in a few commands from your command prompt or scripts, like the following commands:</span></span>

```
docker-compose -f docker-compose.yml -f docker-compose-test.override.yml up -d
./run_unit_tests
docker-compose -f docker-compose.yml -f docker-compose.test.override.yml down
```

#### <a name="production-deployments"></a><span data-ttu-id="4cf94-172">Nasazení v produkčním prostředí</span><span class="sxs-lookup"><span data-stu-id="4cf94-172">Production deployments</span></span>

<span data-ttu-id="4cf94-173">Compose můžete použít také k nasazení na vzdálený modul Docker.</span><span class="sxs-lookup"><span data-stu-id="4cf94-173">You can also use Compose to deploy to a remote Docker Engine.</span></span> <span data-ttu-id="4cf94-174">Obvyklý případ je nasadit do jedné instance hostitele Docker (jako jsou produkční virtuální počítač nebo server opatřena [Docker Machine](https://docs.docker.com/machine/overview/)).</span><span class="sxs-lookup"><span data-stu-id="4cf94-174">A typical case is to deploy to a single Docker host instance (like a production VM or server provisioned with [Docker Machine](https://docs.docker.com/machine/overview/)).</span></span>

<span data-ttu-id="4cf94-175">Pokud používáte jiné orchestrator (Azure Service Fabric, Kubernetes, atd.), můžete potřebovat přidat instalační program a metadata nastavení konfigurace podobné těm v docker-compose.yml, ale ve formátu vyžaduje další nástroje orchestrator.</span><span class="sxs-lookup"><span data-stu-id="4cf94-175">If you are using any other orchestrator (Azure Service Fabric, Kubernetes, etc.), you might need to add setup and metadata configuration settings like those in docker-compose.yml, but in the format required by the other orchestrator.</span></span>

<span data-ttu-id="4cf94-176">V každém případě docker-compose je vhodné nástroje a metadata formát pro vývoj, testování a produkční pracovní postupy, i když pracovním postupu se může lišit na orchestrátoru, který používáte.</span><span class="sxs-lookup"><span data-stu-id="4cf94-176">In any case, docker-compose is a convenient tool and metadata format for development, testing and production workflows, although the production workflow might vary on the orchestrator you are using.</span></span>

### <a name="using-multiple-docker-compose-files-to-handle-several-environments"></a><span data-ttu-id="4cf94-177">Použití více souborů docker-compose pro zpracování několika prostředí</span><span class="sxs-lookup"><span data-stu-id="4cf94-177">Using multiple docker-compose files to handle several environments</span></span>

<span data-ttu-id="4cf94-178">Při cílení na jiné prostředí, byste měli použít více soubory compose.</span><span class="sxs-lookup"><span data-stu-id="4cf94-178">When targeting different environments, you should use multiple compose files.</span></span> <span data-ttu-id="4cf94-179">To vám umožní vytvořit několik variant konfigurace v závislosti na prostředí.</span><span class="sxs-lookup"><span data-stu-id="4cf94-179">This lets you create multiple configuration variants depending on the environment.</span></span>

#### <a name="overriding-the-base-docker-compose-file"></a><span data-ttu-id="4cf94-180">Přepsání souboru základní docker-compose</span><span class="sxs-lookup"><span data-stu-id="4cf94-180">Overriding the base docker-compose file</span></span>

<span data-ttu-id="4cf94-181">Můžete použít soubor jednoho docker-compose.yml jako zjednodušené příkladů uvedených v předchozí části.</span><span class="sxs-lookup"><span data-stu-id="4cf94-181">You could use a single docker-compose.yml file as in the simplified examples shown in previous sections.</span></span> <span data-ttu-id="4cf94-182">Který však není doporučeno pro většinu aplikací.</span><span class="sxs-lookup"><span data-stu-id="4cf94-182">However, that is not recommended for most applications.</span></span>

<span data-ttu-id="4cf94-183">Ve výchozím nastavení přečte vytvořit dva soubory, docker-compose.yml a docker-compose.override.yml volitelné soubor.</span><span class="sxs-lookup"><span data-stu-id="4cf94-183">By default, Compose reads two files, a docker-compose.yml and an optional docker-compose.override.yml file.</span></span> <span data-ttu-id="4cf94-184">Jak je znázorněno v obrázek 6 – 11, když používáte aplikaci Visual Studio a povolení podpory Dockeru, Visual Studio také vytvoří soubor docker-compose.vs.debug.g.yml další ladění aplikace, si můžete prohlédnout tohoto souboru ve složce obj.\\Dockeru \\ ve složce hlavní řešení.</span><span class="sxs-lookup"><span data-stu-id="4cf94-184">As shown in Figure 6-11, when you are using Visual Studio and enabling Docker support, Visual Studio also creates an additional docker-compose.vs.debug.g.yml file for debugging the application, you can take a look at this file in folder obj\\Docker\\ in the main solution folder.</span></span>

![docker-compose strukturu souboru projektu: .dockerignore ignorovat soubory. docker-compose.yml, k vytváření mikroslužeb; docker-compose.override.yml ke konfiguraci prostředí mikroslužeb.](./media/image12.png)

<span data-ttu-id="4cf94-186">**Obrázek 6 – 11**.</span><span class="sxs-lookup"><span data-stu-id="4cf94-186">**Figure 6-11**.</span></span> <span data-ttu-id="4cf94-187">docker-compose soubory v sadě Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="4cf94-187">docker-compose files in Visual Studio 2017</span></span>

<span data-ttu-id="4cf94-188">Můžete upravit docker-compose soubory v libovolném editoru, jako je Visual Studio Code nebo Sublime a spusťte aplikaci docker-compose up příkazu.</span><span class="sxs-lookup"><span data-stu-id="4cf94-188">You can edit the docker-compose files with any editor, like Visual Studio Code or Sublime, and run the application with the docker-compose up command.</span></span>

<span data-ttu-id="4cf94-189">Podle konvence soubor docker-compose.yml obsahuje základní konfiguraci a další nastavení statické.</span><span class="sxs-lookup"><span data-stu-id="4cf94-189">By convention, the docker-compose.yml file contains your base configuration and other static settings.</span></span> <span data-ttu-id="4cf94-190">To znamená, že konfigurace služby by neměly měnit v závislosti na prostředí, na které cílíte.</span><span class="sxs-lookup"><span data-stu-id="4cf94-190">That means that the service configuration should not change depending on the deployment environment you are targeting.</span></span>

<span data-ttu-id="4cf94-191">Soubor docker-compose.override.yml jako její název napovídá, obsahuje konfigurační nastavení přepsat základní konfigurace, jako je například konfigurace, která závisí na prostředí nasazení.</span><span class="sxs-lookup"><span data-stu-id="4cf94-191">The docker-compose.override.yml file, as its name suggests, contains configuration settings that override the base configuration, such as configuration that depends on the deployment environment.</span></span> <span data-ttu-id="4cf94-192">Také můžete mít více přepsání souborů s různými názvy.</span><span class="sxs-lookup"><span data-stu-id="4cf94-192">You can have multiple override files with different names also.</span></span> <span data-ttu-id="4cf94-193">Přepsat soubory obvykle obsahují další informace potřebné pro aplikaci, ale konkrétní prostředí nebo nasazení.</span><span class="sxs-lookup"><span data-stu-id="4cf94-193">The override files usually contain additional information needed by the application but specific to an environment or to a deployment.</span></span>

#### <a name="targeting-multiple-environments"></a><span data-ttu-id="4cf94-194">Cílení na více prostředí</span><span class="sxs-lookup"><span data-stu-id="4cf94-194">Targeting multiple environments</span></span>

<span data-ttu-id="4cf94-195">Typický případ použití je při definování více compose soubory, je možné cílit na více prostředí, jako jsou výroba, Fázování importu, průběžná integrace a vývoje.</span><span class="sxs-lookup"><span data-stu-id="4cf94-195">A typical use case is when you define multiple compose files so you can target multiple environments, like production, staging, CI, or development.</span></span> <span data-ttu-id="4cf94-196">Pro podporu těchto rozdílů, můžete rozdělit konfiguraci psaní do více souborů, jak je znázorněno v obrázek 6-12.</span><span class="sxs-lookup"><span data-stu-id="4cf94-196">To support these differences, you can split your Compose configuration into multiple files, as shown in Figure 6-12.</span></span>

![Můžete kombinovat několik souborů docker-compose\*.fml pro zpracování různých prostředí.](./media/image13.png)

<span data-ttu-id="4cf94-198">**Obrázek 6-12**.</span><span class="sxs-lookup"><span data-stu-id="4cf94-198">**Figure 6-12**.</span></span> <span data-ttu-id="4cf94-199">Několik souborů docker-compose přepsání hodnot v souboru docker-compose.yml základní</span><span class="sxs-lookup"><span data-stu-id="4cf94-199">Multiple docker-compose files overriding values in the base docker-compose.yml file</span></span>

<span data-ttu-id="4cf94-200">Začněte s soubor základní docker-compose.yml.</span><span class="sxs-lookup"><span data-stu-id="4cf94-200">You start with the base docker-compose.yml file.</span></span> <span data-ttu-id="4cf94-201">Tuto základní soubor musí obsahovat nastavení konfigurace základní nebo statické, které se nemění v závislosti na prostředí.</span><span class="sxs-lookup"><span data-stu-id="4cf94-201">This base file has to contain the base or static configuration settings that do not change depending on the environment.</span></span> <span data-ttu-id="4cf94-202">Například aplikaci eShopOnContainers má následující soubor docker-compose.yml (zjednodušená méně službami) jako základního souboru.</span><span class="sxs-lookup"><span data-stu-id="4cf94-202">For example, the eShopOnContainers has the following docker-compose.yml file (simplified with less services) as the base file.</span></span>

```yml
#docker-compose.yml (Base)
version: '3.4'
services:
  basket.api:
    image: eshop/basket.api:${TAG:-latest}
    build:
      context: .
      dockerfile: src/Services/Basket/Basket.API/Dockerfile    
    depends_on:
      - basket.data
      - identity.api
      - rabbitmq

  catalog.api:
    image: eshop/catalog.api:${TAG:-latest}
    build:
      context: .
      dockerfile: src/Services/Catalog/Catalog.API/Dockerfile    
    depends_on:
      - sql.data
      - rabbitmq

  marketing.api:
    image: eshop/marketing.api:${TAG:-latest}
    build:
      context: .
      dockerfile: src/Services/Marketing/Marketing.API/Dockerfile    
    depends_on:
      - sql.data
      - nosql.data
      - identity.api
      - rabbitmq

  webmvc:
    image: eshop/webmvc:${TAG:-latest}
    build:
      context: .
      dockerfile: src/Web/WebMVC/Dockerfile    
    depends_on:
      - catalog.api
      - ordering.api
      - identity.api
      - basket.api
      - marketing.api

  sql.data:
    image: microsoft/mssql-server-linux:2017-latest

  nosql.data:
    image: mongo

  basket.data:
    image: redis
      
  rabbitmq:
    image: rabbitmq:3-management

```

<span data-ttu-id="4cf94-203">Hodnoty v souboru základní docker-compose.yml by neměly měnit z důvodu různých cílových prostředí nasazení.</span><span class="sxs-lookup"><span data-stu-id="4cf94-203">The values in the base docker-compose.yml file should not change because of different target deployment environments.</span></span>

<span data-ttu-id="4cf94-204">Pokud vám soustředit se na definici služby webmvc, například uvidíte jak tyto informace je skoro stejné bez ohledu na to, co prostředí, které vám může cílí.</span><span class="sxs-lookup"><span data-stu-id="4cf94-204">If you focus on the webmvc service definition, for instance, you can see how that information is much the same no matter what environment you might be targeting.</span></span> <span data-ttu-id="4cf94-205">Máte následující informace:</span><span class="sxs-lookup"><span data-stu-id="4cf94-205">You have the following information:</span></span>

-   <span data-ttu-id="4cf94-206">Název služby: webmvc.</span><span class="sxs-lookup"><span data-stu-id="4cf94-206">The service name: webmvc.</span></span>

-   <span data-ttu-id="4cf94-207">Vlastní image kontejneru: eshop/webmvc.</span><span class="sxs-lookup"><span data-stu-id="4cf94-207">The container’s custom image: eshop/webmvc.</span></span>

-   <span data-ttu-id="4cf94-208">Příkaz k vytvoření vlastní image Dockeru, určující, které soubor Dockerfile používat.</span><span class="sxs-lookup"><span data-stu-id="4cf94-208">The command to build the custom Docker image, indicating which Dockerfile to use.</span></span>

-   <span data-ttu-id="4cf94-209">Závislosti na dalších službách, takže tento kontejner se nespustí, dokud jste spustili dalších kontejnerů závislostí.</span><span class="sxs-lookup"><span data-stu-id="4cf94-209">Dependencies on other services, so this container does not start until the other dependency containers have started.</span></span>

<span data-ttu-id="4cf94-210">Můžete mít další konfiguraci, ale důležité je, že v souboru docker-compose.yml základní jenom chcete nastavit informace, které jsou společné napříč prostředími.</span><span class="sxs-lookup"><span data-stu-id="4cf94-210">You can have additional configuration, but the important point is that in the base docker-compose.yml file, you just want to set the information that is common across environments.</span></span> <span data-ttu-id="4cf94-211">Potom v docker-compose.override.yml nebo podobné soubory provozního nebo testovacího měli umístit konfigurace, které jsou specifické pro každé prostředí.</span><span class="sxs-lookup"><span data-stu-id="4cf94-211">Then in the docker-compose.override.yml or similar files for production or staging, you should place configuration that is specific for each environment.</span></span>

<span data-ttu-id="4cf94-212">Docker-compose.override.yml se obvykle používá pro vaše vývojové prostředí, jako v následujícím příkladu v aplikaci eShopOnContainers:</span><span class="sxs-lookup"><span data-stu-id="4cf94-212">Usually, the docker-compose.override.yml is used for your development environment, as in the following example from eShopOnContainers:</span></span>

```yml
#docker-compose.override.yml (Extended config for DEVELOPMENT env.)
version: '3.4'

services: 
# Simplified number of services here: 
      
  basket.api:
    environment:
      - ASPNETCORE_ENVIRONMENT=Development
      - ASPNETCORE_URLS=http://0.0.0.0:80
      - ConnectionString=${ESHOP_AZURE_REDIS_BASKET_DB:-basket.data}
      - identityUrl=http://identity.api              
      - IdentityUrlExternal=http://${ESHOP_EXTERNAL_DNS_NAME_OR_IP}:5105
      - EventBusConnection=${ESHOP_AZURE_SERVICE_BUS:-rabbitmq}
      - EventBusUserName=${ESHOP_SERVICE_BUS_USERNAME}
      - EventBusPassword=${ESHOP_SERVICE_BUS_PASSWORD}      
      - AzureServiceBusEnabled=False
      - ApplicationInsights__InstrumentationKey=${INSTRUMENTATION_KEY}
      - OrchestratorType=${ORCHESTRATOR_TYPE}
      - UseLoadTest=${USE_LOADTEST:-False}

    ports:
      - "5103:80"

  catalog.api:
    environment:
      - ASPNETCORE_ENVIRONMENT=Development
      - ASPNETCORE_URLS=http://0.0.0.0:80
      - ConnectionString=${ESHOP_AZURE_CATALOG_DB:-Server=sql.data;Database=Microsoft.eShopOnContainers.Services.CatalogDb;User Id=sa;Password=Pass@word}
      - PicBaseUrl=${ESHOP_AZURE_STORAGE_CATALOG_URL:-http://localhost:5202/api/v1/catalog/items/[0]/pic/}   
      - EventBusConnection=${ESHOP_AZURE_SERVICE_BUS:-rabbitmq}
      - EventBusUserName=${ESHOP_SERVICE_BUS_USERNAME}
      - EventBusPassword=${ESHOP_SERVICE_BUS_PASSWORD}         
      - AzureStorageAccountName=${ESHOP_AZURE_STORAGE_CATALOG_NAME}
      - AzureStorageAccountKey=${ESHOP_AZURE_STORAGE_CATALOG_KEY}
      - UseCustomizationData=True
      - AzureServiceBusEnabled=False
      - AzureStorageEnabled=False
      - ApplicationInsights__InstrumentationKey=${INSTRUMENTATION_KEY}
      - OrchestratorType=${ORCHESTRATOR_TYPE}
    ports:
      - "5101:80"

  marketing.api:
    environment:
      - ASPNETCORE_ENVIRONMENT=Development
      - ASPNETCORE_URLS=http://0.0.0.0:80
      - ConnectionString=${ESHOP_AZURE_MARKETING_DB:-Server=sql.data;Database=Microsoft.eShopOnContainers.Services.MarketingDb;User Id=sa;Password=Pass@word}
      - MongoConnectionString=${ESHOP_AZURE_COSMOSDB:-mongodb://nosql.data}
      - MongoDatabase=MarketingDb
      - EventBusConnection=${ESHOP_AZURE_SERVICE_BUS:-rabbitmq}
      - EventBusUserName=${ESHOP_SERVICE_BUS_USERNAME}
      - EventBusPassword=${ESHOP_SERVICE_BUS_PASSWORD}          
      - identityUrl=http://identity.api              
      - IdentityUrlExternal=http://${ESHOP_EXTERNAL_DNS_NAME_OR_IP}:5105
      - CampaignDetailFunctionUri=${ESHOP_AZUREFUNC_CAMPAIGN_DETAILS_URI}
      - PicBaseUrl=${ESHOP_AZURE_STORAGE_MARKETING_URL:-http://localhost:5110/api/v1/campaigns/[0]/pic/}
      - AzureStorageAccountName=${ESHOP_AZURE_STORAGE_MARKETING_NAME}
      - AzureStorageAccountKey=${ESHOP_AZURE_STORAGE_MARKETING_KEY}
      - AzureServiceBusEnabled=False
      - AzureStorageEnabled=False
      - ApplicationInsights__InstrumentationKey=${INSTRUMENTATION_KEY}
      - OrchestratorType=${ORCHESTRATOR_TYPE}
      - UseLoadTest=${USE_LOADTEST:-False}
    ports:
      - "5110:80"

  webmvc:
    environment:
      - ASPNETCORE_ENVIRONMENT=Development
      - ASPNETCORE_URLS=http://0.0.0.0:80
      - PurchaseUrl=http://webshoppingapigw
      - IdentityUrl=http://10.0.75.1:5105
      - MarketingUrl=http://webmarketingapigw
      - CatalogUrlHC=http://catalog.api/hc
      - OrderingUrlHC=http://ordering.api/hc
      - IdentityUrlHC=http://identity.api/hc
      - BasketUrlHC=http://basket.api/hc
      - MarketingUrlHC=http://marketing.api/hc
      - PaymentUrlHC=http://payment.api/hc
      - SignalrHubUrl=http://${ESHOP_EXTERNAL_DNS_NAME_OR_IP}:5202
      - UseCustomizationData=True
      - ApplicationInsights__InstrumentationKey=${INSTRUMENTATION_KEY}
      - OrchestratorType=${ORCHESTRATOR_TYPE}
      - UseLoadTest=${USE_LOADTEST:-False}
    ports:
      - "5100:80"
  sql.data:
    environment:
      - SA_PASSWORD=Pass@word
      - ACCEPT_EULA=Y
    ports:
      - "5433:1433"
  nosql.data:
    ports:
      - "27017:27017"
  basket.data:
    ports:
      - "6379:6379"      
  rabbitmq:
    ports:
      - "15672:15672"
      - "5672:5672"

```

<span data-ttu-id="4cf94-213">V tomto příkladu konfigurace přepisování vývoj uvádí některé porty na hostitele, definuje proměnných prostředí pomocí adresy URL pro přesměrování a určuje připojovací řetězce pro vývojové prostředí.</span><span class="sxs-lookup"><span data-stu-id="4cf94-213">In this example, the development override configuration exposes some ports to the host, defines environment variables with redirect URLs, and specifies connection strings for the development environment.</span></span> <span data-ttu-id="4cf94-214">Tato nastavení jsou všechny jenom pro vývojové prostředí.</span><span class="sxs-lookup"><span data-stu-id="4cf94-214">These settings are all just for the development environment.</span></span>

<span data-ttu-id="4cf94-215">Při spuštění `docker-compose up` (nebo ji spustit ze sady Visual Studio), tento příkaz načte přepsání automaticky jako kdyby to byly sloučení oba soubory.</span><span class="sxs-lookup"><span data-stu-id="4cf94-215">When you run `docker-compose up` (or launch it from Visual Studio), the command reads the overrides automatically as if it were merging both files.</span></span>

<span data-ttu-id="4cf94-216">Předpokládejme, že má jiný soubor Compose pro produkční prostředí s jinou konfiguraci hodnoty, porty nebo připojovací řetězce.</span><span class="sxs-lookup"><span data-stu-id="4cf94-216">Suppose that you want another Compose file for the production environment, with different configuration values, ports or connection strings.</span></span> <span data-ttu-id="4cf94-217">Můžete vytvořit soubor přepsání, jako je soubor s názvem `docker-compose.prod.yml` s různými nastaveními a proměnných prostředí.</span><span class="sxs-lookup"><span data-stu-id="4cf94-217">You can create another override file, like file named `docker-compose.prod.yml` with different settings and environment variables.</span></span>  <span data-ttu-id="4cf94-218">Tento soubor může být uložená v různých úložiště Git nebo spravovat a zabezpečit jiný tým.</span><span class="sxs-lookup"><span data-stu-id="4cf94-218">That file might be stored in a different Git repo or managed and secured by a different team.</span></span>

#### <a name="how-to-deploy-with-a-specific-override-file"></a><span data-ttu-id="4cf94-219">Nasazení se souborem specifické přepsání</span><span class="sxs-lookup"><span data-stu-id="4cf94-219">How to deploy with a specific override file</span></span>

<span data-ttu-id="4cf94-220">Pokud chcete použít více souborů přepsání nebo přepsání souboru s jiným názvem, můžete použít možnost -f s příkazu docker-compose a zadejte soubory.</span><span class="sxs-lookup"><span data-stu-id="4cf94-220">To use multiple override files, or an override file with a different name, you can use the -f option with the docker-compose command and specify the files.</span></span> <span data-ttu-id="4cf94-221">Vytvoření souborů sloučení v pořadí, v jakém jsou uvedeny v příkazovém řádku.</span><span class="sxs-lookup"><span data-stu-id="4cf94-221">Compose merges files in the order they are specified on the command line.</span></span> <span data-ttu-id="4cf94-222">Následující příklad ukazuje, jak nasadit pomocí přepsání souborů.</span><span class="sxs-lookup"><span data-stu-id="4cf94-222">The following example shows how to deploy with override files.</span></span>

```
docker-compose -f docker-compose.yml -f docker-compose.prod.yml up -d
```

#### <a name="using-environment-variables-in-docker-compose-files"></a><span data-ttu-id="4cf94-223">Použití proměnných prostředí v souborů docker-compose</span><span class="sxs-lookup"><span data-stu-id="4cf94-223">Using environment variables in docker-compose files</span></span>

<span data-ttu-id="4cf94-224">Je vhodné, zejména v produkčním prostředí, abyste mohli získat informace o konfiguraci z proměnných prostředí, jak budeme mít je znázorněno v předchozích příkladech.</span><span class="sxs-lookup"><span data-stu-id="4cf94-224">It is convenient, especially in production environments, to be able to get configuration information from environment variables, as we have shown in previous examples.</span></span> <span data-ttu-id="4cf94-225">Proměnné prostředí odkazovat ve vašich souborech docker-compose pomocí syntaxe ${MY\_VAR}.</span><span class="sxs-lookup"><span data-stu-id="4cf94-225">You can reference an environment variable in your docker-compose files using the syntax ${MY\_VAR}.</span></span> <span data-ttu-id="4cf94-226">Následující řádek ze souboru dockeru compose.prod.yml ukazuje, jak odkazovat na hodnotu proměnné prostředí.</span><span class="sxs-lookup"><span data-stu-id="4cf94-226">The following line from a docker-compose.prod.yml file shows how to reference the value of an environment variable.</span></span>

```yml
IdentityUrl=http://${ESHOP_PROD_EXTERNAL_DNS_NAME_OR_IP}:5105
```

<span data-ttu-id="4cf94-227">Proměnné prostředí jsou vytvořeny a inicializovány různými způsoby v závislosti na hostitelské prostředí (Linux, Windows, Cloudový cluster atd.).</span><span class="sxs-lookup"><span data-stu-id="4cf94-227">Environment variables are created and initialized in different ways, depending on your host environment (Linux, Windows, Cloud cluster, etc.).</span></span> <span data-ttu-id="4cf94-228">Pohodlný přístup je však použití souboru .env.</span><span class="sxs-lookup"><span data-stu-id="4cf94-228">However, a convenient approach is to use an .env file.</span></span> <span data-ttu-id="4cf94-229">Podpora souborů docker-compose deklarování proměnných prostředí v souboru .env výchozí.</span><span class="sxs-lookup"><span data-stu-id="4cf94-229">The docker-compose files support declaring default environment variables in the .env file.</span></span> <span data-ttu-id="4cf94-230">Tyto hodnoty pro proměnné prostředí jsou výchozí hodnoty.</span><span class="sxs-lookup"><span data-stu-id="4cf94-230">These values for the environment variables are the default values.</span></span> <span data-ttu-id="4cf94-231">Ale může být přepsána hodnoty, které může jste definovali ve všech vašich prostředích (hostitelský operační systém nebo proměnné prostředí z clusteru).</span><span class="sxs-lookup"><span data-stu-id="4cf94-231">But they can be overridden by the values you might have defined in each of your environments (host OS or environment variables from your cluster).</span></span> <span data-ttu-id="4cf94-232">Umístění tohoto souboru .env ve složce kde docker-compose ze spuštění příkazu.</span><span class="sxs-lookup"><span data-stu-id="4cf94-232">You place this .env file in the folder where the docker-compose command is executed from.</span></span>

<span data-ttu-id="4cf94-233">Následující příklad ukazuje souboru .env stejně jako [.env](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/.env) soubor pro aplikaci eShopOnContainers aplikaci.</span><span class="sxs-lookup"><span data-stu-id="4cf94-233">The following example shows an .env file like the [.env](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/.env) file for the eShopOnContainers application.</span></span>

```
# .env file

ESHOP_EXTERNAL_DNS_NAME_OR_IP=localhost

ESHOP_PROD_EXTERNAL_DNS_NAME_OR_IP=10.121.122.92
```

<span data-ttu-id="4cf94-234">Docker-compose očekává, že každý řádek v souboru .env být ve formátu \<proměnnou\>=\<hodnota\>.</span><span class="sxs-lookup"><span data-stu-id="4cf94-234">Docker-compose expects each line in an .env file to be in the format \<variable\>=\<value\>.</span></span>

<span data-ttu-id="4cf94-235">Všimněte si, že hodnoty nastavené v běhovém prostředí vždy přepsat hodnoty definované v souboru .env.</span><span class="sxs-lookup"><span data-stu-id="4cf94-235">Note that the values set in the runtime environment always override the values defined inside the .env file.</span></span> <span data-ttu-id="4cf94-236">Podobným způsobem hodnoty předané prostřednictvím argumentů příkazového řádku příkaz také přepsat výchozí hodnoty nastavené v souboru .env.</span><span class="sxs-lookup"><span data-stu-id="4cf94-236">In a similar way, values passed via command-line command arguments also override the default values set in the .env file.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="4cf94-237">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="4cf94-237">Additional resources</span></span>

-   <span data-ttu-id="4cf94-238">**Přehled služby Docker Compose**</span><span class="sxs-lookup"><span data-stu-id="4cf94-238">**Overview of Docker Compose**</span></span> <br/>
    [*https://docs.docker.com/compose/overview/*](https://docs.docker.com/compose/overview/)

-   <span data-ttu-id="4cf94-239">**Více soubory Compose**</span><span class="sxs-lookup"><span data-stu-id="4cf94-239">**Multiple Compose files**</span></span> <br/>
    [*https://docs.docker.com/compose/extends/\#multiple-compose-files*](https://docs.docker.com/compose/extends/#multiple-compose-files)

### <a name="building-optimized-aspnet-core-docker-images"></a><span data-ttu-id="4cf94-240">Vytváření optimalizované Image Dockeru ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="4cf94-240">Building optimized ASP.NET Core Docker images</span></span>

<span data-ttu-id="4cf94-241">Pokud zkoumáte Dockeru a .NET Core na zdroje v síti Internet, zjistíte soubory Dockerfile, které ukazují zjednodušení vytváření image Dockeru pomocí kopírování zdroje do kontejneru.</span><span class="sxs-lookup"><span data-stu-id="4cf94-241">If you are exploring Docker and .NET Core on sources on the Internet, you will find Dockerfiles that demonstrate the simplicity of building a Docker image by copying your source into a container.</span></span> <span data-ttu-id="4cf94-242">Tyto příklady navrhnout pomocí jednoduchou konfiguraci a může mít image Dockeru s prostředím zabalit s aplikací.</span><span class="sxs-lookup"><span data-stu-id="4cf94-242">These examples suggest that by using a simple configuration, you can have a Docker image with the environment packaged with your application.</span></span> <span data-ttu-id="4cf94-243">Následující příklad ukazuje jednoduchý soubor Dockerfile v této souvislosti.</span><span class="sxs-lookup"><span data-stu-id="4cf94-243">The following example shows a simple Dockerfile in this vein.</span></span>

```
FROM microsoft/dotnet
WORKDIR /app
ENV ASPNETCORE_URLS http://+:80
EXPOSE 80
COPY . .
RUN dotnet restore
ENTRYPOINT ["dotnet", "run"]
```

<span data-ttu-id="4cf94-244">Soubor Dockerfile takto bude fungovat.</span><span class="sxs-lookup"><span data-stu-id="4cf94-244">A Dockerfile like this will work.</span></span> <span data-ttu-id="4cf94-245">Je ale podstatně optimalizovat Image, zejména produkčních imagí.</span><span class="sxs-lookup"><span data-stu-id="4cf94-245">However, you can substantially optimize your images, especially your production images.</span></span>

<span data-ttu-id="4cf94-246">V modelu mikroslužeb a kontejnerů jsou neustále spouštění kontejnerů.</span><span class="sxs-lookup"><span data-stu-id="4cf94-246">In the container and microservices model, you are constantly starting containers.</span></span> <span data-ttu-id="4cf94-247">Typické způsob, jak pomocí kontejnerů nerestartuje spící kontejner, protože kontejneru je jedno použití.</span><span class="sxs-lookup"><span data-stu-id="4cf94-247">The typical way of using containers does not restart a sleeping container, because the container is disposable.</span></span> <span data-ttu-id="4cf94-248">Orchestrátory (jako je Kubernetes a Azure Service Fabric) jednoduše vytvořte nové instance z imagí.</span><span class="sxs-lookup"><span data-stu-id="4cf94-248">Orchestrators (like Kubernetes and Azure Service Fabric) simply create new instances of images.</span></span> <span data-ttu-id="4cf94-249">To znamená, že potřebujete optimalizovat předkompilace aplikace, když je sestaven tak proces vytváření instancí bude rychlejší.</span><span class="sxs-lookup"><span data-stu-id="4cf94-249">What this means is that you would need to optimize by precompiling the application when it is built so the instantiation process will be faster.</span></span> <span data-ttu-id="4cf94-250">Při spuštění kontejneru musí být připraveny ke spuštění.</span><span class="sxs-lookup"><span data-stu-id="4cf94-250">When the container is started, it should be ready to run.</span></span> <span data-ttu-id="4cf94-251">Nesmí obnovit a kompilaci za běhu použití `dotnet restore` a `dotnet build` příkazy z rozhraní příkazového řádku dotnet to, jak vidíte v mnoha blogové příspěvky o .NET Core a Docker.</span><span class="sxs-lookup"><span data-stu-id="4cf94-251">You should not restore and compile at run time, using `dotnet restore` and `dotnet build` commands from the dotnet CLI that, as you see in many blog posts about .NET Core and Docker.</span></span>

<span data-ttu-id="4cf94-252">Tým .NET má způsobem důležitou práci provést optimalizovaný kontejner rozhraní .NET Core a ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="4cf94-252">The .NET team has been doing important work to make .NET Core and ASP.NET Core a container-optimized framework.</span></span> <span data-ttu-id="4cf94-253">Nejen .NET Core je jednoduché rozhraní s malé paměťové nároky; tým zaměřený na optimalizované Image Dockeru pro tři hlavní scénáře a publikované v registru Docker Hub v <span class="underline">microsoft/dotnet</span>, začínající s verzí 2.1:</span><span class="sxs-lookup"><span data-stu-id="4cf94-253">Not only is .NET Core a lightweight framework with a small memory footprint; the team has focused on optimized Docker images for three main scenarios and published them in the Docker Hub registry at <span class="underline">microsoft/dotnet</span>, beginning with version 2.1:</span></span>

1.  <span data-ttu-id="4cf94-254">**Vývoj**: Pokud priorita je schopnost rychle interate a ladění změnám a velikosti je sekundární.</span><span class="sxs-lookup"><span data-stu-id="4cf94-254">**Development**: Where the priority is the ability to quickly interate and debug changes and size is secondary.</span></span>

2.  <span data-ttu-id="4cf94-255">**Sestavení**: Priorita je při kompilaci aplikace a obsahuje binární soubory a další závislosti optimalizovat binární soubory.</span><span class="sxs-lookup"><span data-stu-id="4cf94-255">**Build**: The priority is compiling the application and includes binaries and other dependencies to optimize binaries.</span></span>

3.  <span data-ttu-id="4cf94-256">**Produkční**: Pokud je fokus rychlé nasazení a spouštění kontejnerů, takže tyto Image jsou omezené na binární soubory a obsahu nedded ke spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="4cf94-256">**Production**: Where the focus is fast deploying and starting of containers, so these images are limited to the binaries and the content nedded to run the application.</span></span>

<span data-ttu-id="4cf94-257">Za tím účelem týmu .NET nabízí tři základní varianty v [microsoft/dotnet](https://hub.docker.com/r/microsoft/dotnet/) (v Docker Hubu):</span><span class="sxs-lookup"><span data-stu-id="4cf94-257">To achieve this, the .NET team is providing three basic variants in [microsoft/dotnet](https://hub.docker.com/r/microsoft/dotnet/) (at Docker Hub):</span></span>

1.  <span data-ttu-id="4cf94-258">**Sada SDK**: pro scénáře vývoje a sestavení.</span><span class="sxs-lookup"><span data-stu-id="4cf94-258">**sdk**: for the development and build scenarios.</span></span>
2.  <span data-ttu-id="4cf94-259">**modul runtime**: pro produkční scénář a</span><span class="sxs-lookup"><span data-stu-id="4cf94-259">**runtime**: for the production scenario and</span></span>
3.  <span data-ttu-id="4cf94-260">**modul runtime deps**: pro produkční scénáře [samostatná aplikace](https://docs.microsoft.com/dotnet/core/deploying/index#self-contained-deployments-scd).</span><span class="sxs-lookup"><span data-stu-id="4cf94-260">**runtime-deps**: for the production scenario of [self-contained applications](https://docs.microsoft.com/dotnet/core/deploying/index#self-contained-deployments-scd).</span></span>

<span data-ttu-id="4cf94-261">Modul runtime imagí taky poskytuje automatické nastavení aspnetcore\_adresy URL na port 80 a pre-ngend mezipaměti sestavení, které vám pomůžou získat rychlejší spuštění.</span><span class="sxs-lookup"><span data-stu-id="4cf94-261">Runtime images also provides automatic setting of aspnetcore\_urls to port 80 and the pre-ngend cache of assemblies; to help in getting faster startup.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="4cf94-262">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="4cf94-262">Additional resources</span></span>

-   <span data-ttu-id="4cf94-263">**Vytváření optimalizované Image Dockeru s ASP.NET Core**</span><span class="sxs-lookup"><span data-stu-id="4cf94-263">**Building Optimized Docker Images with ASP.NET Core**</span></span> <br/>
    [*https://blogs.msdn.microsoft.com/stevelasker/2016/09/29/building-optimized-docker-images-with-asp-net-core/*](https://blogs.msdn.microsoft.com/stevelasker/2016/09/29/building-optimized-docker-images-with-asp-net-core/)

-   <span data-ttu-id="4cf94-264">**Vytváření imagí Dockeru pro aplikace .NET Core**</span><span class="sxs-lookup"><span data-stu-id="4cf94-264">**Building Docker Images for .NET Core Applications**</span></span> <br/>
    [*https://docs.microsoft.com/en-us/dotnet/core/docker/building-net-docker-images*](https://docs.microsoft.com/en-us/dotnet/core/docker/building-net-docker-images)

>[!div class="step-by-step"]
><span data-ttu-id="4cf94-265">[Předchozí](data-driven-crud-microservice.md)
>[další](database-server-container.md)</span><span class="sxs-lookup"><span data-stu-id="4cf94-265">[Previous](data-driven-crud-microservice.md)
[Next](database-server-container.md)</span></span>