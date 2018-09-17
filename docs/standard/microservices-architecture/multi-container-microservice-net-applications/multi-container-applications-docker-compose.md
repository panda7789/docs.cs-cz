---
title: Definování vícekontejnerové aplikace pomocí docker-compose.yml
description: Architektura Mikroslužeb .NET pro Kontejnerizované aplikace .NET | Definování vícekontejnerové aplikace pomocí docker-compose.yml
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/30/2017
ms.openlocfilehash: d1c4166129716ccbbc86855e38d631f493b82290
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45750255"
---
# <a name="defining-your-multi-container-application-with-docker-composeyml"></a><span data-ttu-id="ef266-103">Definování vícekontejnerové aplikace pomocí docker-compose.yml</span><span class="sxs-lookup"><span data-stu-id="ef266-103">Defining your multi-container application with docker-compose.yml</span></span> 

<span data-ttu-id="ef266-104">V této příručce [docker-compose.yml](https://docs.docker.com/compose/compose-file/) souboru byla zavedena v části [kroku 4. Definování vašich služeb v docker-compose.yml při sestavování aplikace více kontejnerů Dockeru](#step4_define_svcs_in_docker_compose_yml).</span><span class="sxs-lookup"><span data-stu-id="ef266-104">In this guide, the [docker-compose.yml](https://docs.docker.com/compose/compose-file/) file was introduced in the section [Step 4. Define your services in docker-compose.yml when building a multi-container Docker application](#step4_define_svcs_in_docker_compose_yml).</span></span> <span data-ttu-id="ef266-105">Existují však další způsoby, jak používat docker-compose soubory, které stojí za prozkoumání podrobněji.</span><span class="sxs-lookup"><span data-stu-id="ef266-105">However, there are additional ways to use the docker-compose files that are worth exploring in further detail.</span></span>

<span data-ttu-id="ef266-106">Například můžete výslovně popsat, jak chcete nasadit vícekontejnerové aplikace v souboru docker-compose.yml.</span><span class="sxs-lookup"><span data-stu-id="ef266-106">For example, you can explicitly describe how you want to deploy your multi-container application in the docker-compose.yml file.</span></span> <span data-ttu-id="ef266-107">Volitelně může také popisovat, jak chcete sestavit vlastní Image Dockeru.</span><span class="sxs-lookup"><span data-stu-id="ef266-107">Optionally, you can also describe how you are going to build your custom Docker images.</span></span> <span data-ttu-id="ef266-108">(Vlastní Image Dockeru se dají taky vytvářet pomocí rozhraní příkazového řádku Dockeru.)</span><span class="sxs-lookup"><span data-stu-id="ef266-108">(Custom Docker images can also be built with the Docker CLI.)</span></span>

<span data-ttu-id="ef266-109">V podstatě definování všech kontejnerů, které chcete nasadit, a navíc určité vlastnosti pro každý kontejner nasazení.</span><span class="sxs-lookup"><span data-stu-id="ef266-109">Basically, you define each of the containers you want to deploy plus certain characteristics for each container deployment.</span></span> <span data-ttu-id="ef266-110">Jakmile budete mít soubor s popisem nasazení více kontejnerů, můžete nasadit celé řešení v rámci jedné akce orchestrované systémem [docker-compose up](https://docs.docker.com/compose/overview/) příkazu rozhraní příkazového řádku, nebo ji můžete nasadit transparentně ze sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="ef266-110">Once you have a multi-container deployment description file, you can deploy the whole solution in a single action orchestrated by the [docker-compose up](https://docs.docker.com/compose/overview/) CLI command, or you can deploy it transparently from Visual Studio.</span></span> <span data-ttu-id="ef266-111">V opačném případě musíte použít rozhraní příkazového řádku Dockeru k nasazení kontejnerů pomocí kontejneru v několika krocích pomocí dockeru, spusťte příkaz z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="ef266-111">Otherwise, you would need to use the Docker CLI to deploy container-by-container in multiple steps by using the docker run command from the command line.</span></span> <span data-ttu-id="ef266-112">Jednotlivé služby definované v docker-compose.yml proto musíte zadat právě jednu image nebo sestavení.</span><span class="sxs-lookup"><span data-stu-id="ef266-112">Therefore, each service defined in docker-compose.yml must specify exactly one image or build.</span></span> <span data-ttu-id="ef266-113">Další klíče jsou volitelné a odpovídají jejich docker, spusťte příkazový řádek protějšky.</span><span class="sxs-lookup"><span data-stu-id="ef266-113">Other keys are optional, and are analogous to their docker run command-line counterparts.</span></span>

<span data-ttu-id="ef266-114">Následující kód YAML je definice je to možné globální, ale jeden soubor docker-compose.yml pro vzorovou aplikaci eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="ef266-114">The following YAML code is the definition of a possible global but single docker-compose.yml file for the eShopOnContainers sample.</span></span> <span data-ttu-id="ef266-115">Toto není skutečný docker-compose soubor v aplikaci eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="ef266-115">This is not the actual docker-compose file from eShopOnContainers.</span></span> <span data-ttu-id="ef266-116">Místo toho je zjednodušený a konsolidované verze jednoho souboru, který není nejlepší způsob, jak pracovat s souborů docker-compose, jak budou vysvětlena dále.</span><span class="sxs-lookup"><span data-stu-id="ef266-116">Instead, it is a simplified and consolidated version in a single file, which is not the best way to work with docker-compose files, as will be explained later.</span></span>

```yml
version: '2'

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

<span data-ttu-id="ef266-117">Kořenový klíč z tohoto souboru se služby.</span><span class="sxs-lookup"><span data-stu-id="ef266-117">The root key in this file is services.</span></span> <span data-ttu-id="ef266-118">Pod tímto klíčem definujete služby chcete nasadit a spustit při spouštění docker-compose up příkaz nebo při nasazení ze sady Visual Studio s použitím tohoto souboru docker-compose.yml.</span><span class="sxs-lookup"><span data-stu-id="ef266-118">Under that key you define the services you want to deploy and run when you execute the docker-compose up command or when you deploy from Visual Studio by using this docker-compose.yml file.</span></span> <span data-ttu-id="ef266-119">V tomto případě soubor docker-compose.yml má několik služeb, které jsou definovány, jak je popsáno v následujícím seznamu.</span><span class="sxs-lookup"><span data-stu-id="ef266-119">In this case, the docker-compose.yml file has multiple services defined, as described in the following list.</span></span>

-   <span data-ttu-id="ef266-120">webmvc kontejneru, včetně aplikací ASP.NET Core MVC využívání mikroslužeb from C na straně serveru\#</span><span class="sxs-lookup"><span data-stu-id="ef266-120">webmvc Container including the ASP.NET Core MVC application consuming the microservices from server-side C\#</span></span>

-   <span data-ttu-id="ef266-121">CATALOG.API kontejneru, včetně katalogu ASP.NET Core webového rozhraní API mikroslužby</span><span class="sxs-lookup"><span data-stu-id="ef266-121">catalog.api Container including the Catalog ASP.NET Core Web API microservice</span></span>

-   <span data-ttu-id="ef266-122">Ordering.API kontejneru, včetně řazení ASP.NET Core webového rozhraní API mikroslužby</span><span class="sxs-lookup"><span data-stu-id="ef266-122">ordering.api Container including the Ordering ASP.NET Core Web API microservice</span></span>

-   <span data-ttu-id="ef266-123">SQL.data kontejneru systémem SQL Server pro Linux, uchovávající databází mikroslužeb</span><span class="sxs-lookup"><span data-stu-id="ef266-123">sql.data Container running SQL Server for Linux, holding the microservices databases</span></span>

-   <span data-ttu-id="ef266-124">basket.API kontejneru s nákupní košík ASP.NET Core webového rozhraní API mikroslužby</span><span class="sxs-lookup"><span data-stu-id="ef266-124">basket.api Container with the Basket ASP.NET Core Web API microservice</span></span>

-   <span data-ttu-id="ef266-125">basket.data kontejneru Služba mezipaměti REDIS s databází nákupní košík jako mezipaměť REDIS</span><span class="sxs-lookup"><span data-stu-id="ef266-125">basket.data Container running the REDIS cache service, with the basket database as a REDIS cache</span></span>

### <a name="a-simple-web-service-api-container"></a><span data-ttu-id="ef266-126">Jednoduchý kontejner rozhraní API webové služby</span><span class="sxs-lookup"><span data-stu-id="ef266-126">A simple Web Service API container</span></span>

<span data-ttu-id="ef266-127">Se zaměříte na jediný kontejner, kontejner catalog.api-mikroslužeb má jednoduché definici:</span><span class="sxs-lookup"><span data-stu-id="ef266-127">Focusing on a single container, the catalog.api container-microservice has a straightforward definition:</span></span>

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

<span data-ttu-id="ef266-128">Tato kontejnerizovaná služba má následující základní konfigurace:</span><span class="sxs-lookup"><span data-stu-id="ef266-128">This containerized service has the following basic configuration:</span></span>

-   <span data-ttu-id="ef266-129">Je založena na imagi vlastní eshop/catalog.api.</span><span class="sxs-lookup"><span data-stu-id="ef266-129">It is based on the custom eshop/catalog.api image.</span></span> <span data-ttu-id="ef266-130">Pro jednoduchost saké neexistuje žádné sestavení: nastavení v souboru klíče.</span><span class="sxs-lookup"><span data-stu-id="ef266-130">For simplicity’s sake, there is no build: key setting in the file.</span></span> <span data-ttu-id="ef266-131">To znamená, že obrázek musí mít byla dříve vytvořena (pomocí sestavení dockeru) se stáhly (pomocí příkazu docker pull) z libovolného registru Dockeru.</span><span class="sxs-lookup"><span data-stu-id="ef266-131">This means that the image must have been previously built (with docker build) or have been downloaded (with the docker pull command) from any Docker registry.</span></span>

-   <span data-ttu-id="ef266-132">Definuje proměnnou prostředí s názvem připojovací řetězec připojovacím řetězcem Entity Framework používané pro přístup k instanci serveru SQL Server, který obsahuje datový model katalogu.</span><span class="sxs-lookup"><span data-stu-id="ef266-132">It defines an environment variable named ConnectionString with the connection string to be used by Entity Framework to access the SQL Server instance that contains the catalog data model.</span></span> <span data-ttu-id="ef266-133">V takovém případě stejného kontejneru systému SQL Server obsahuje více databází.</span><span class="sxs-lookup"><span data-stu-id="ef266-133">In this case, the same SQL Server container is holding multiple databases.</span></span> <span data-ttu-id="ef266-134">Proto je nutné méně paměti v počítači pro vývoj pro Docker.</span><span class="sxs-lookup"><span data-stu-id="ef266-134">Therefore, you need less memory in your development machine for Docker.</span></span> <span data-ttu-id="ef266-135">Můžete však také nasadit jeden kontejner systému SQL Server pro každou databázi mikroslužeb.</span><span class="sxs-lookup"><span data-stu-id="ef266-135">However, you could also deploy one SQL Server container for each microservice database.</span></span>

-   <span data-ttu-id="ef266-136">Název systému SQL Server je sql.data, které se stejným názvem, který pro kontejner, na kterém běží instance systému SQL Server pro Linux.</span><span class="sxs-lookup"><span data-stu-id="ef266-136">The SQL Server name is sql.data, which is the same name used for the container that is running the SQL Server instance for Linux.</span></span> <span data-ttu-id="ef266-137">Tato možnost je pohodlná; bude možné použít tento překlad (interní hostitele Dockeru) vyřeší síťovou adresu, takže není nutné znát interní IP adresa pro kontejnery, které spouštíte z jiných kontejnerů.</span><span class="sxs-lookup"><span data-stu-id="ef266-137">This is convenient; being able to use this name resolution (internal to the Docker host) will resolve the network address so you don’t need to know the internal IP for the containers you are accessing from other containers.</span></span>

<span data-ttu-id="ef266-138">Vzhledem k tomu, že připojovací řetězec je určené proměnnou prostředí, můžete tuto proměnnou nastavit prostřednictvím jiným způsobem a jiný čas.</span><span class="sxs-lookup"><span data-stu-id="ef266-138">Because the connection string is defined by an environment variable, you could set that variable through a different mechanism and at a different time.</span></span> <span data-ttu-id="ef266-139">Například můžete nastavit různé připojovací řetězec při nasazení do produkčního prostředí v posledním hostitele nebo provedením z vašich kanálů CI/CD v Azure DevOps služby nebo systému upřednostňované DevOps.</span><span class="sxs-lookup"><span data-stu-id="ef266-139">For example, you could set a different connection string when deploying to production in the final hosts, or by doing it from your CI/CD pipelines in Azure DevOps Services or your preferred DevOps system.</span></span>

-   <span data-ttu-id="ef266-140">Zpřístupňuje port 80 pro interní přístup ke službě catalog.api v rámci hostitele Dockeru.</span><span class="sxs-lookup"><span data-stu-id="ef266-140">It exposes port 80 for internal access to the catalog.api service within the Docker host.</span></span> <span data-ttu-id="ef266-141">Hostitel je aktuálně virtuálního počítače s Linuxem, protože je založen na image Dockeru pro Linux, ale můžete nakonfigurovat tak, kontejner pro spuštění v imagi Windows místo.</span><span class="sxs-lookup"><span data-stu-id="ef266-141">The host is currently a Linux VM because it is based on a Docker image for Linux, but you could configure the container to run on a Windows image instead.</span></span>

-   <span data-ttu-id="ef266-142">Předá vystavené port 80 v kontejneru na port 5101 hostitele Docker Machine (virtuálního počítače s Linuxem).</span><span class="sxs-lookup"><span data-stu-id="ef266-142">It forwards the exposed port 80 on the container to port 5101 on the Docker host machine (the Linux VM).</span></span>

-   <span data-ttu-id="ef266-143">Webové služby odkazuje ve službě sql.data (instance systému SQL Server pro Linux databáze spuštěné v kontejneru).</span><span class="sxs-lookup"><span data-stu-id="ef266-143">It links the web service to the sql.data service (the SQL Server instance for Linux database running in a container).</span></span> <span data-ttu-id="ef266-144">Pokud zadáte tuto závislost, kontejneru catalog.api nespustí, dokud již bylo zahájeno sql.data kontejneru; To je důležité, protože catalog.api musí být databáze serveru SQL Server a spuštěna nejprve.</span><span class="sxs-lookup"><span data-stu-id="ef266-144">When you specify this dependency, the catalog.api container will not start until the sql.data container has already started; this is important because catalog.api needs to have the SQL Server database up and running first.</span></span> <span data-ttu-id="ef266-145">Však tento druh závislosti kontejneru není dostatečně v mnoha případech, protože Docker zkontroluje pouze na úrovni kontejneru.</span><span class="sxs-lookup"><span data-stu-id="ef266-145">However, this kind of container dependency is not enough in many cases, because Docker checks only at the container level.</span></span> <span data-ttu-id="ef266-146">Někdy služby (v tomto případě systému SQL Server) nemusí nadále budete mít, proto se doporučuje implementovat logiku opakování pomocí exponenciálního omezení rychlosti mikroslužby klienta.</span><span class="sxs-lookup"><span data-stu-id="ef266-146">Sometimes the service (in this case SQL Server) might still not be ready, so it is advisable to implement retry logic with exponential backoff in your client microservices.</span></span> <span data-ttu-id="ef266-147">Tímto způsobem, pokud kontejner závislosti není připravený na krátkou dobu, aplikace bude nadále odolný.</span><span class="sxs-lookup"><span data-stu-id="ef266-147">That way, if a dependency container is not ready for a short time, the application will still be resilient.</span></span>

-   <span data-ttu-id="ef266-148">Je nakonfigurována pro povolení přístupu k externím serverům: nadbytečné\_hostitelů nastavení vám umožní přistupovat k externí servery nebo počítače mimo hostitele Docker (tedy mimo výchozí linuxového virtuálního počítače, který je vývoj Docker hostitele), jako je například místní databáze SQL Instance serveru na vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="ef266-148">It is configured to allow access to external servers: the extra\_hosts setting allows you to access external servers or machines outside of the Docker host (that is, outside the default Linux VM which is a development Docker host), such as a local SQL Server instance on your development PC.</span></span>

<span data-ttu-id="ef266-149">Existují také jiné, pokročilejší docker-compose.yml nastavení, které se budeme zabývat v dalších částech.</span><span class="sxs-lookup"><span data-stu-id="ef266-149">There are also other, more advanced docker-compose.yml settings that we will discuss in the following sections.</span></span>

### <a name="using-docker-compose-files-to-target-multiple-environments"></a><span data-ttu-id="ef266-150">Pomocí souborů docker-compose cílit na více prostředí</span><span class="sxs-lookup"><span data-stu-id="ef266-150">Using docker-compose files to target multiple environments</span></span>

<span data-ttu-id="ef266-151">Soubory docker-compose.yml jsou soubory definic a mohou být využívána více infrastruktury, které rozumí formátu.</span><span class="sxs-lookup"><span data-stu-id="ef266-151">The docker-compose.yml files are definition files and can be used by multiple infrastructures that understand that format.</span></span> <span data-ttu-id="ef266-152">Nástroj nejjednodušší je docker-compose příkazu, ale další nástroje, jako je srozuměni tento soubor s orchestrátory (například Docker Swarm).</span><span class="sxs-lookup"><span data-stu-id="ef266-152">The most straightforward tool is the docker-compose command, but other tools like orchestrators (for example, Docker Swarm) also understand that file.</span></span>

<span data-ttu-id="ef266-153">Proto se s použitím příkazu je možné cílit na následující hlavní scénáře docker-compose.</span><span class="sxs-lookup"><span data-stu-id="ef266-153">Therefore, by using the docker-compose command you can target the following main scenarios.</span></span>

#### <a name="development-environments"></a><span data-ttu-id="ef266-154">Vývojová prostředí</span><span class="sxs-lookup"><span data-stu-id="ef266-154">Development environments</span></span>

<span data-ttu-id="ef266-155">Při vývoji aplikací, je důležité, aby bylo možné spouštět aplikace v izolovaném vývojové prostředí.</span><span class="sxs-lookup"><span data-stu-id="ef266-155">When you develop applications, it is important to be able to run an application in an isolated development environment.</span></span> <span data-ttu-id="ef266-156">Můžete použít příkazu rozhraní příkazového řádku k vytvoření tohoto prostředí nebo pomocí sady Visual Studio, který používá docker-compose pod pokličkou docker-compose.</span><span class="sxs-lookup"><span data-stu-id="ef266-156">You can use the docker-compose CLI command to create that environment or use Visual Studio which uses docker-compose under the covers.</span></span>

<span data-ttu-id="ef266-157">Soubor docker-compose.yml umožňuje konfigurovat a dokumentovat závislosti služby všechny aplikace (jiné služby, mezipaměti, databáze, fronty atd.).</span><span class="sxs-lookup"><span data-stu-id="ef266-157">The docker-compose.yml file allows you to configure and document all your application’s service dependencies (other services, cache, databases, queues, etc.).</span></span> <span data-ttu-id="ef266-158">Použití docker-compose příkazu rozhraní příkazového řádku, můžete vytvořit a spustit jeden nebo více kontejnerů pro každý závislosti pomocí jediného příkazu (docker-compose up).</span><span class="sxs-lookup"><span data-stu-id="ef266-158">Using the docker-compose CLI command, you can create and start one or more containers for each dependency with a single command (docker-compose up).</span></span>

<span data-ttu-id="ef266-159">Soubory docker-compose.yml jsou konfigurační soubory interpretovat modul Docker, ale sloužit také jako soubory pohodlný dokumentace o složení vícekontejnerovou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="ef266-159">The docker-compose.yml files are configuration files interpreted by Docker engine but also serve as convenient documentation files about the composition of your multi-container application.</span></span>

#### <a name="testing-environments"></a><span data-ttu-id="ef266-160">Testovací prostředí</span><span class="sxs-lookup"><span data-stu-id="ef266-160">Testing environments</span></span>

<span data-ttu-id="ef266-161">Důležitou součástí procesu kontinuální integrace (CI) ani průběžného nasazování (CD) jsou testy jednotek a integrační testy.</span><span class="sxs-lookup"><span data-stu-id="ef266-161">An important part of any continuous deployment (CD) or continuous integration (CI) process are the unit tests and integration tests.</span></span> <span data-ttu-id="ef266-162">Tyto automatizované testy vyžadují izolovaného prostředí, takže nejsou ovlivněny uživatelů nebo jiné změny v datech vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="ef266-162">These automated tests require an isolated environment so they are not impacted by the users or any other change in the application’s data.</span></span>

<span data-ttu-id="ef266-163">Pomocí Docker Compose můžete vytvořit a odstranit izolované prostředí velmi snadno v několika příkazů z příkazového řádku nebo skripty, například následující příkazy:</span><span class="sxs-lookup"><span data-stu-id="ef266-163">With Docker Compose you can create and destroy that isolated environment very easily in a few commands from your command prompt or scripts, like the following commands:</span></span>

```
docker-compose up -d
./run_unit_tests
docker-compose down
```

#### <a name="production-deployments"></a><span data-ttu-id="ef266-164">Nasazení v produkčním prostředí</span><span class="sxs-lookup"><span data-stu-id="ef266-164">Production deployments</span></span>

<span data-ttu-id="ef266-165">Compose můžete použít také k nasazení na vzdálený modul Docker.</span><span class="sxs-lookup"><span data-stu-id="ef266-165">You can also use Compose to deploy to a remote Docker Engine.</span></span> <span data-ttu-id="ef266-166">Obvyklý případ je nasadit do jedné instance hostitele Docker (jako jsou produkční virtuální počítač nebo server opatřena [Docker Machine](https://docs.docker.com/machine/overview/)).</span><span class="sxs-lookup"><span data-stu-id="ef266-166">A typical case is to deploy to a single Docker host instance (like a production VM or server provisioned with [Docker Machine](https://docs.docker.com/machine/overview/)).</span></span> <span data-ttu-id="ef266-167">Ale mohou být také celý [Docker Swarm](https://docs.docker.com/swarm/overview/) clusteru, protože v clusterech, budou také kompatibilní se soubory docker-compose.yml.</span><span class="sxs-lookup"><span data-stu-id="ef266-167">But it could also be an entire [Docker Swarm](https://docs.docker.com/swarm/overview/) cluster, because clusters are also compatible with the docker-compose.yml files.</span></span>

<span data-ttu-id="ef266-168">Pokud používáte jiné orchestrator (Azure Service Fabric, Mesos DC/OS, Kubernetes, atd.), můžete potřebovat přidat instalační program a metadata nastavení konfigurace podobné těm v docker-compose.yml, ale ve formátu vyžaduje další nástroje orchestrator.</span><span class="sxs-lookup"><span data-stu-id="ef266-168">If you are using any other orchestrator (Azure Service Fabric, Mesos DC/OS, Kubernetes, etc.), you might need to add setup and metadata configuration settings like those in docker-compose.yml, but in the format required by the other orchestrator.</span></span>

<span data-ttu-id="ef266-169">V každém případě docker-compose je vhodné nástroje a metadata formát pro vývoj, testování a produkční pracovní postupy, i když pracovním postupu se může lišit na orchestrátoru, který používáte.</span><span class="sxs-lookup"><span data-stu-id="ef266-169">In any case, docker-compose is a convenient tool and metadata format for development, testing and production workflows, although the production workflow might vary on the orchestrator you are using.</span></span>

### <a name="using-multiple-docker-compose-files-to-handle-several-environments"></a><span data-ttu-id="ef266-170">Použití více souborů docker-compose pro zpracování několika prostředí</span><span class="sxs-lookup"><span data-stu-id="ef266-170">Using multiple docker-compose files to handle several environments</span></span>

<span data-ttu-id="ef266-171">Při cílení na jiné prostředí, byste měli použít více soubory compose.</span><span class="sxs-lookup"><span data-stu-id="ef266-171">When targeting different environments, you should use multiple compose files.</span></span> <span data-ttu-id="ef266-172">To vám umožní vytvořit několik variant konfigurace v závislosti na prostředí.</span><span class="sxs-lookup"><span data-stu-id="ef266-172">This lets you create multiple configuration variants depending on the environment.</span></span>

#### <a name="overriding-the-base-docker-compose-file"></a><span data-ttu-id="ef266-173">Přepsání souboru základní docker-compose</span><span class="sxs-lookup"><span data-stu-id="ef266-173">Overriding the base docker-compose file</span></span>

<span data-ttu-id="ef266-174">Můžete použít soubor jednoho docker-compose.yml jako zjednodušené příkladů uvedených v předchozí části.</span><span class="sxs-lookup"><span data-stu-id="ef266-174">You could use a single docker-compose.yml file as in the simplified examples shown in previous sections.</span></span> <span data-ttu-id="ef266-175">Který však není doporučeno pro většinu aplikací.</span><span class="sxs-lookup"><span data-stu-id="ef266-175">However, that is not recommended for most applications.</span></span>

<span data-ttu-id="ef266-176">Ve výchozím nastavení přečte vytvořit dva soubory, docker-compose.yml a docker-compose.override.yml volitelné soubor.</span><span class="sxs-lookup"><span data-stu-id="ef266-176">By default, Compose reads two files, a docker-compose.yml and an optional docker-compose.override.yml file.</span></span> <span data-ttu-id="ef266-177">Jak ukazuje obrázek 8-11, když pomocí sady Visual Studio a povolení podpory Dockeru, Visual Studio také vytvoří soubor docker-compose.ci.build,yml další pro použití z vašich kanálů CI/CD jako ve službách Azure DevOps.</span><span class="sxs-lookup"><span data-stu-id="ef266-177">As shown in Figure 8-11, when you are using Visual Studio and enabling Docker support, Visual Studio also creates an additional docker-compose.ci.build,yml file for you to use from your CI/CD pipelines like in Azure DevOps Services.</span></span>

![](./media/image12.png)

<span data-ttu-id="ef266-178">**Obrázek 8-11**.</span><span class="sxs-lookup"><span data-stu-id="ef266-178">**Figure 8-11**.</span></span> <span data-ttu-id="ef266-179">docker-compose soubory v sadě Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="ef266-179">docker-compose files in Visual Studio 2017</span></span>

<span data-ttu-id="ef266-180">Můžete upravit docker-compose soubory v libovolném editoru, jako je Visual Studio Code nebo Sublime a spusťte aplikaci docker-compose up příkazu.</span><span class="sxs-lookup"><span data-stu-id="ef266-180">You can edit the docker-compose files with any editor, like Visual Studio Code or Sublime, and run the application with the docker-compose up command.</span></span>

<span data-ttu-id="ef266-181">Podle konvence soubor docker-compose.yml obsahuje základní konfiguraci a další nastavení statické.</span><span class="sxs-lookup"><span data-stu-id="ef266-181">By convention, the docker-compose.yml file contains your base configuration and other static settings.</span></span> <span data-ttu-id="ef266-182">To znamená, že konfigurace služby by neměly měnit v závislosti na prostředí, na které cílíte.</span><span class="sxs-lookup"><span data-stu-id="ef266-182">That means that the service configuration should not change depending on the deployment environment you are targeting.</span></span>

<span data-ttu-id="ef266-183">Soubor docker-compose.override.yml jako její název napovídá, obsahuje konfigurační nastavení přepsat základní konfigurace, jako je například konfigurace, která závisí na prostředí nasazení.</span><span class="sxs-lookup"><span data-stu-id="ef266-183">The docker-compose.override.yml file, as its name suggests, contains configuration settings that override the base configuration, such as configuration that depends on the deployment environment.</span></span> <span data-ttu-id="ef266-184">Také můžete mít více přepsání souborů s různými názvy.</span><span class="sxs-lookup"><span data-stu-id="ef266-184">You can have multiple override files with different names also.</span></span> <span data-ttu-id="ef266-185">Přepsat soubory obvykle obsahují další informace potřebné pro aplikaci, ale konkrétní prostředí nebo nasazení.</span><span class="sxs-lookup"><span data-stu-id="ef266-185">The override files usually contain additional information needed by the application but specific to an environment or to a deployment.</span></span>

#### <a name="targeting-multiple-environments"></a><span data-ttu-id="ef266-186">Cílení na více prostředí</span><span class="sxs-lookup"><span data-stu-id="ef266-186">Targeting multiple environments</span></span>

<span data-ttu-id="ef266-187">Typický případ použití je při definování více compose soubory, je možné cílit na více prostředí, jako jsou výroba, Fázování importu, průběžná integrace a vývoje.</span><span class="sxs-lookup"><span data-stu-id="ef266-187">A typical use case is when you define multiple compose files so you can target multiple environments, like production, staging, CI, or development.</span></span> <span data-ttu-id="ef266-188">Pro podporu těchto rozdílů, můžete rozdělit konfiguraci psaní do více souborů, jak ukazuje obrázek 8 – 12.</span><span class="sxs-lookup"><span data-stu-id="ef266-188">To support these differences, you can split your Compose configuration into multiple files, as shown in Figure 8-12.</span></span>

![](./media/image13.png)

<span data-ttu-id="ef266-189">**Obrázek 8-12**.</span><span class="sxs-lookup"><span data-stu-id="ef266-189">**Figure 8-12**.</span></span> <span data-ttu-id="ef266-190">Několik souborů docker-compose přepsání hodnot v souboru docker-compose.yml základní</span><span class="sxs-lookup"><span data-stu-id="ef266-190">Multiple docker-compose files overriding values in the base docker-compose.yml file</span></span>

<span data-ttu-id="ef266-191">Začněte s soubor základní docker-compose.yml.</span><span class="sxs-lookup"><span data-stu-id="ef266-191">You start with the base docker-compose.yml file.</span></span> <span data-ttu-id="ef266-192">Tuto základní soubor musí obsahovat nastavení konfigurace základní nebo statické, které se nemění v závislosti na prostředí.</span><span class="sxs-lookup"><span data-stu-id="ef266-192">This base file has to contain the base or static configuration settings that do not change depending on the environment.</span></span> <span data-ttu-id="ef266-193">Například aplikaci eShopOnContainers má následující soubor docker-compose.yml jako základního souboru.</span><span class="sxs-lookup"><span data-stu-id="ef266-193">For example, the eShopOnContainers has the following docker-compose.yml file as the base file.</span></span>

```yml
#docker-compose.yml (Base)
version: '3'
services:
  basket.api:
    image: eshop/basket.api:${TAG:-latest}
    build:
      context: ./src/Services/Basket/Basket.API
      dockerfile: Dockerfile    
    depends_on:
      - basket.data
      - identity.api
      - rabbitmq

  catalog.api:
    image: eshop/catalog.api:${TAG:-latest}
    build:
      context: ./src/Services/Catalog/Catalog.API
      dockerfile: Dockerfile    
    depends_on:
      - sql.data
      - rabbitmq

  marketing.api:
    image: eshop/marketing.api:${TAG:-latest}
    build:
      context: ./src/Services/Marketing/Marketing.API
      dockerfile: Dockerfile    
    depends_on:
      - sql.data
      - nosql.data
      - identity.api
      - rabbitmq

  webmvc:
    image: eshop/webmvc:${TAG:-latest}
    build:
      context: ./src/Web/WebMVC
      dockerfile: Dockerfile    
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

<span data-ttu-id="ef266-194">Hodnoty v souboru základní docker-compose.yml by neměly měnit z důvodu různých cílových prostředí nasazení.</span><span class="sxs-lookup"><span data-stu-id="ef266-194">The values in the base docker-compose.yml file should not change because of different target deployment environments.</span></span>

<span data-ttu-id="ef266-195">Pokud vám soustředit se na definici služby webmvc, například uvidíte jak tyto informace je skoro stejné bez ohledu na to, co prostředí, které vám může cílí.</span><span class="sxs-lookup"><span data-stu-id="ef266-195">If you focus on the webmvc service definition, for instance, you can see how that information is much the same no matter what environment you might be targeting.</span></span> <span data-ttu-id="ef266-196">Máte následující informace:</span><span class="sxs-lookup"><span data-stu-id="ef266-196">You have the following information:</span></span>

-   <span data-ttu-id="ef266-197">Název služby: webmvc.</span><span class="sxs-lookup"><span data-stu-id="ef266-197">The service name: webmvc.</span></span>

-   <span data-ttu-id="ef266-198">Vlastní image kontejneru: eshop/webmvc.</span><span class="sxs-lookup"><span data-stu-id="ef266-198">The container’s custom image: eshop/webmvc.</span></span>

-   <span data-ttu-id="ef266-199">Příkaz k vytvoření vlastní image Dockeru, určující, které soubor Dockerfile používat.</span><span class="sxs-lookup"><span data-stu-id="ef266-199">The command to build the custom Docker image, indicating which Dockerfile to use.</span></span>

-   <span data-ttu-id="ef266-200">Závislosti na dalších službách, takže tento kontejner se nespustí, dokud jste spustili dalších kontejnerů závislostí.</span><span class="sxs-lookup"><span data-stu-id="ef266-200">Dependencies on other services, so this container does not start until the other dependency containers have started.</span></span>

<span data-ttu-id="ef266-201">Můžete mít další konfiguraci, ale důležité je, že v souboru docker-compose.yml základní jenom chcete nastavit informace, které jsou společné napříč prostředími.</span><span class="sxs-lookup"><span data-stu-id="ef266-201">You can have additional configuration, but the important point is that in the base docker-compose.yml file, you just want to set the information that is common across environments.</span></span> <span data-ttu-id="ef266-202">Potom v docker-compose.override.yml nebo podobné soubory provozního nebo testovacího měli umístit konfigurace, které jsou specifické pro každé prostředí.</span><span class="sxs-lookup"><span data-stu-id="ef266-202">Then in the docker-compose.override.yml or similar files for production or staging, you should place configuration that is specific for each environment.</span></span>

<span data-ttu-id="ef266-203">Docker-compose.override.yml se obvykle používá pro vaše vývojové prostředí, jako v následujícím příkladu v aplikaci eShopOnContainers:</span><span class="sxs-lookup"><span data-stu-id="ef266-203">Usually, the docker-compose.override.yml is used for your development environment, as in the following example from eShopOnContainers:</span></span>

```yml
#docker-compose.override.yml (Extended config for DEVELOPMENT env.)
version: '3'

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
      - PicBaseUrl=${ESHOP_AZURE_STORAGE_CATALOG_URL:-http://localhost:5101/api/v1/catalog/items/[0]/pic/}   
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
      - CatalogUrl=http://catalog.api
      - OrderingUrl=http://ordering.api
      - BasketUrl=http://basket.api
      - LocationsUrl=http://locations.api
      - IdentityUrl=http://10.0.75.1:5105
      - MarketingUrl=http://marketing.api                                                    
      - CatalogUrlHC=http://catalog.api/hc
      - OrderingUrlHC=http://ordering.api/hc
      - IdentityUrlHC=http://identity.api/hc     
      - BasketUrlHC=http://basket.api/hc
      - MarketingUrlHC=http://marketing.api/hc
      - PaymentUrlHC=http://payment.api/hc
      - UseCustomizationData=True
      - ApplicationInsights__InstrumentationKey=${INSTRUMENTATION_KEY}
      - OrchestratorType=${ORCHESTRATOR_TYPE}
      - UseLoadTest=${USE_LOADTEST:-False}
    ports:
      - "5100:80"
  sql.data:
    environment:
      - MSSQL_SA_PASSWORD=Pass@word
      - ACCEPT_EULA=Y
      - MSSQL_PID=Developer
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

<span data-ttu-id="ef266-204">V tomto příkladu konfigurace přepisování vývoj uvádí některé porty na hostitele, definuje proměnných prostředí pomocí adresy URL pro přesměrování a určuje připojovací řetězce pro vývojové prostředí.</span><span class="sxs-lookup"><span data-stu-id="ef266-204">In this example, the development override configuration exposes some ports to the host, defines environment variables with redirect URLs, and specifies connection strings for the development environment.</span></span> <span data-ttu-id="ef266-205">Tato nastavení jsou všechny jenom pro vývojové prostředí.</span><span class="sxs-lookup"><span data-stu-id="ef266-205">These settings are all just for the development environment.</span></span>

<span data-ttu-id="ef266-206">Při spuštění `docker-compose up` (nebo ji spustit ze sady Visual Studio), tento příkaz načte přepsání automaticky jako kdyby to byly sloučení oba soubory.</span><span class="sxs-lookup"><span data-stu-id="ef266-206">When you run `docker-compose up` (or launch it from Visual Studio), the command reads the overrides automatically as if it were merging both files.</span></span>

<span data-ttu-id="ef266-207">Předpokládejme, že má jiný soubor Compose pro produkční prostředí s jinou konfiguraci hodnoty, porty nebo připojovací řetězce.</span><span class="sxs-lookup"><span data-stu-id="ef266-207">Suppose that you want another Compose file for the production environment, with different configuration values, ports or connection strings.</span></span> <span data-ttu-id="ef266-208">Můžete vytvořit soubor přepsání, jako je soubor s názvem `docker-compose.prod.yml` s různými nastaveními a proměnných prostředí.</span><span class="sxs-lookup"><span data-stu-id="ef266-208">You can create another override file, like file named `docker-compose.prod.yml` with different settings and environment variables.</span></span>  <span data-ttu-id="ef266-209">Tento soubor může být uložená v různých úložiště Git nebo spravovat a zabezpečit jiný tým.</span><span class="sxs-lookup"><span data-stu-id="ef266-209">That file might be stored in a different Git repo or managed and secured by a different team.</span></span>

#### <a name="how-to-deploy-with-a-specific-override-file"></a><span data-ttu-id="ef266-210">Nasazení se souborem specifické přepsání</span><span class="sxs-lookup"><span data-stu-id="ef266-210">How to deploy with a specific override file</span></span>

<span data-ttu-id="ef266-211">Pokud chcete použít více souborů přepsání nebo přepsání souboru s jiným názvem, můžete použít možnost -f s příkazu docker-compose a zadejte soubory.</span><span class="sxs-lookup"><span data-stu-id="ef266-211">To use multiple override files, or an override file with a different name, you can use the -f option with the docker-compose command and specify the files.</span></span> <span data-ttu-id="ef266-212">Vytvoření souborů sloučení v pořadí, v jakém jsou uvedeny v příkazovém řádku.</span><span class="sxs-lookup"><span data-stu-id="ef266-212">Compose merges files in the order they are specified on the command line.</span></span> <span data-ttu-id="ef266-213">Následující příklad ukazuje, jak nasadit pomocí přepsání souborů.</span><span class="sxs-lookup"><span data-stu-id="ef266-213">The following example shows how to deploy with override files.</span></span>

```
docker-compose -f docker-compose.yml -f docker-compose.prod.yml up -d
```

#### <a name="using-environment-variables-in-docker-compose-files"></a><span data-ttu-id="ef266-214">Použití proměnných prostředí v souborů docker-compose</span><span class="sxs-lookup"><span data-stu-id="ef266-214">Using environment variables in docker-compose files</span></span>

<span data-ttu-id="ef266-215">Je vhodné, zejména v produkčním prostředí, abyste mohli získat informace o konfiguraci z proměnných prostředí, jak budeme mít je znázorněno v předchozích příkladech.</span><span class="sxs-lookup"><span data-stu-id="ef266-215">It is convenient, especially in production environments, to be able to get configuration information from environment variables, as we have shown in previous examples.</span></span> <span data-ttu-id="ef266-216">Odkaz na proměnnou prostředí v souborech docker-compose pomocí syntaxe \${MY\_VAR}.</span><span class="sxs-lookup"><span data-stu-id="ef266-216">You reference an environment variable in your docker-compose files using the syntax \${MY\_VAR}.</span></span> <span data-ttu-id="ef266-217">Následující řádek ze souboru dockeru compose.prod.yml ukazuje, jak odkazovat na hodnotu proměnné prostředí.</span><span class="sxs-lookup"><span data-stu-id="ef266-217">The following line from a docker-compose.prod.yml file shows how to reference the value of an environment variable.</span></span>

```yml
IdentityUrl=http://${ESHOP_PROD_EXTERNAL_DNS_NAME_OR_IP}:5105
```

<span data-ttu-id="ef266-218">Proměnné prostředí jsou vytvořeny a inicializovány různými způsoby v závislosti na hostitelské prostředí (Linux, Windows, Cloudový cluster atd.).</span><span class="sxs-lookup"><span data-stu-id="ef266-218">Environment variables are created and initialized in different ways, depending on your host environment (Linux, Windows, Cloud cluster, etc.).</span></span> <span data-ttu-id="ef266-219">Pohodlný přístup je však použití souboru .env.</span><span class="sxs-lookup"><span data-stu-id="ef266-219">However, a convenient approach is to use an .env file.</span></span> <span data-ttu-id="ef266-220">Podpora souborů docker-compose deklarování proměnných prostředí v souboru .env výchozí.</span><span class="sxs-lookup"><span data-stu-id="ef266-220">The docker-compose files support declaring default environment variables in the .env file.</span></span> <span data-ttu-id="ef266-221">Tyto hodnoty pro proměnné prostředí jsou výchozí hodnoty.</span><span class="sxs-lookup"><span data-stu-id="ef266-221">These values for the environment variables are the default values.</span></span> <span data-ttu-id="ef266-222">Ale může být přepsána hodnoty, které může jste definovali ve všech vašich prostředích (hostitelský operační systém nebo proměnné prostředí z clusteru).</span><span class="sxs-lookup"><span data-stu-id="ef266-222">But they can be overridden by the values you might have defined in each of your environments (host OS or environment variables from your cluster).</span></span> <span data-ttu-id="ef266-223">Umístění tohoto souboru .env ve složce kde docker-compose ze spuštění příkazu.</span><span class="sxs-lookup"><span data-stu-id="ef266-223">You place this .env file in the folder where the docker-compose command is executed from.</span></span>

<span data-ttu-id="ef266-224">Následující příklad ukazuje souboru .env stejně jako [.env](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/.env) soubor pro aplikaci eShopOnContainers aplikaci.</span><span class="sxs-lookup"><span data-stu-id="ef266-224">The following example shows an .env file like the [.env](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/.env) file for the eShopOnContainers application.</span></span>

```
# .env file

ESHOP_EXTERNAL_DNS_NAME_OR_IP=localhost

ESHOP_PROD_EXTERNAL_DNS_NAME_OR_IP=10.121.122.92
```

<span data-ttu-id="ef266-225">Docker-compose očekává, že každý řádek v souboru .env být ve formátu &lt;proměnnou&gt;=&lt;hodnota&gt;.</span><span class="sxs-lookup"><span data-stu-id="ef266-225">Docker-compose expects each line in an .env file to be in the format &lt;variable&gt;=&lt;value&gt;.</span></span>

<span data-ttu-id="ef266-226">Všimněte si, že hodnoty nastavené v běhovém prostředí vždy přepsat hodnoty definované v souboru .env.</span><span class="sxs-lookup"><span data-stu-id="ef266-226">Note that the values set in the runtime environment always override the values defined inside the .env file.</span></span> <span data-ttu-id="ef266-227">Podobným způsobem hodnoty předané prostřednictvím argumentů příkazového řádku příkaz také přepsat výchozí hodnoty nastavené v souboru .env.</span><span class="sxs-lookup"><span data-stu-id="ef266-227">In a similar way, values passed via command-line command arguments also override the default values set in the .env file.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="ef266-228">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="ef266-228">Additional resources</span></span>

-   <span data-ttu-id="ef266-229">**Přehled služby Docker Compose**
    [*https://docs.docker.com/compose/overview/*](https://docs.docker.com/compose/overview/)</span><span class="sxs-lookup"><span data-stu-id="ef266-229">**Overview of Docker Compose**
[*https://docs.docker.com/compose/overview/*](https://docs.docker.com/compose/overview/)</span></span>

-   <span data-ttu-id="ef266-230">**Více soubory Compose**
    [*https://docs.docker.com/compose/extends/\#multiple-compose-files*](https://docs.docker.com/compose/extends/#multiple-compose-files)</span><span class="sxs-lookup"><span data-stu-id="ef266-230">**Multiple Compose files**
[*https://docs.docker.com/compose/extends/\#multiple-compose-files*](https://docs.docker.com/compose/extends/#multiple-compose-files)</span></span>

### <a name="building-optimized-aspnet-core-docker-images"></a><span data-ttu-id="ef266-231">Vytváření optimalizované Image Dockeru ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="ef266-231">Building optimized ASP.NET Core Docker images</span></span>

<span data-ttu-id="ef266-232">Pokud zkoumáte Dockeru a .NET Core na zdroje v síti Internet, zjistíte soubory Dockerfile, které ukazují zjednodušení vytváření image Dockeru pomocí kopírování zdroje do kontejneru.</span><span class="sxs-lookup"><span data-stu-id="ef266-232">If you are exploring Docker and .NET Core on sources on the Internet, you will find Dockerfiles that demonstrate the simplicity of building a Docker image by copying your source into a container.</span></span> <span data-ttu-id="ef266-233">Tyto příklady navrhnout pomocí jednoduchou konfiguraci a může mít image Dockeru s prostředím zabalit s aplikací.</span><span class="sxs-lookup"><span data-stu-id="ef266-233">These examples suggest that by using a simple configuration, you can have a Docker image with the environment packaged with your application.</span></span> <span data-ttu-id="ef266-234">Následující příklad ukazuje jednoduchý soubor Dockerfile v této souvislosti.</span><span class="sxs-lookup"><span data-stu-id="ef266-234">The following example shows a simple Dockerfile in this vein.</span></span>

```
FROM microsoft/dotnet

WORKDIR /app

ENV ASPNETCORE_URLS http://+:80

EXPOSE 80

COPY . .

RUN dotnet restore

ENTRYPOINT ["dotnet", "run"]
```

<span data-ttu-id="ef266-235">Soubor Dockerfile takto bude fungovat.</span><span class="sxs-lookup"><span data-stu-id="ef266-235">A Dockerfile like this will work.</span></span> <span data-ttu-id="ef266-236">Je ale podstatně optimalizovat Image, zejména produkčních imagí.</span><span class="sxs-lookup"><span data-stu-id="ef266-236">However, you can substantially optimize your images, especially your production images.</span></span>

<span data-ttu-id="ef266-237">V modelu mikroslužeb a kontejnerů jsou neustále spouštění kontejnerů.</span><span class="sxs-lookup"><span data-stu-id="ef266-237">In the container and microservices model, you are constantly starting containers.</span></span> <span data-ttu-id="ef266-238">Typické způsob, jak pomocí kontejnerů nerestartuje spící kontejner, protože kontejneru je jedno použití.</span><span class="sxs-lookup"><span data-stu-id="ef266-238">The typical way of using containers does not restart a sleeping container, because the container is disposable.</span></span> <span data-ttu-id="ef266-239">Orchestrátory (jako je Docker Swarm, Kubernetes, DC/OS nebo Azure Service Fabric) jednoduše vytvořte nové instance z imagí.</span><span class="sxs-lookup"><span data-stu-id="ef266-239">Orchestrators (like Docker Swarm, Kubernetes, DCOS or Azure Service Fabric) simply create new instances of images.</span></span> <span data-ttu-id="ef266-240">To znamená, že potřebujete optimalizovat předkompilace aplikace, když je sestaven tak proces vytváření instancí bude rychlejší.</span><span class="sxs-lookup"><span data-stu-id="ef266-240">What this means is that you would need to optimize by precompiling the application when it is built so the instantiation process will be faster.</span></span> <span data-ttu-id="ef266-241">Při spuštění kontejneru musí být připraveny ke spuštění.</span><span class="sxs-lookup"><span data-stu-id="ef266-241">When the container is started, it should be ready to run.</span></span> <span data-ttu-id="ef266-242">Nesmí obnovit a kompilaci za běhu, dotnet restore a dotnet sestavovací příkazy z rozhraní příkazového řádku dotnet, jak vidíte v mnoha blogové příspěvky o .NET Core a Docker.</span><span class="sxs-lookup"><span data-stu-id="ef266-242">You should not restore and compile at run time, using dotnet restore and dotnet build commands from the dotnet CLI that, as you see in many blog posts about .NET Core and Docker.</span></span>

<span data-ttu-id="ef266-243">Tým .NET má způsobem důležitou práci provést optimalizovaný kontejner rozhraní .NET Core a ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="ef266-243">The .NET team has been doing important work to make .NET Core and ASP.NET Core a container-optimized framework.</span></span> <span data-ttu-id="ef266-244">Nejen .NET Core je jednoduché rozhraní s malé paměťové nároky; tým zaměřený na výkon při spouštění a vytváří některé optimalizované Image Dockeru, jako je třeba [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) bitové kopie, které jsou k dispozici na [Docker Hubu](https://hub.docker.com/r/microsoft/aspnetcore/), porovnání standardní [ Microsoft/dotnet](https://hub.docker.com/r/microsoft/dotnet/) nebo [microsoft/nanoserver](https://github.com/dotnet/dotnet-docker/blob/master/1.0/nanoserver/runtime/Dockerfile) bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="ef266-244">Not only is .NET Core a lightweight framework with a small memory footprint; the team has focused on startup performance and produced some optimized Docker images, like the [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) image available at [Docker Hub](https://hub.docker.com/r/microsoft/aspnetcore/), in comparison to the regular [microsoft/dotnet](https://hub.docker.com/r/microsoft/dotnet/) or [microsoft/nanoserver](https://github.com/dotnet/dotnet-docker/blob/master/1.0/nanoserver/runtime/Dockerfile) images.</span></span> <span data-ttu-id="ef266-245">[Microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) image poskytuje automatické nastavení aspnetcore\_adresy URL na port 80 a mezipaměti pre-ngend sestavení; obě nastavení za následek rychlejší spuštění.</span><span class="sxs-lookup"><span data-stu-id="ef266-245">The [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) image provides automatic setting of aspnetcore\_urls to port 80 and the pre-ngend cache of assemblies; both of these settings result in faster startup.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="ef266-246">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="ef266-246">Additional resources</span></span>

-   <span data-ttu-id="ef266-247">**Vytváření optimalizované Image Dockeru s ASP.NET Core**
    [*https://blogs.msdn.microsoft.com/stevelasker/2016/09/29/building-optimized-docker-images-with-asp-net-core/*](https://blogs.msdn.microsoft.com/stevelasker/2016/09/29/building-optimized-docker-images-with-asp-net-core/)</span><span class="sxs-lookup"><span data-stu-id="ef266-247">**Building Optimized Docker Images with ASP.NET Core**
[*https://blogs.msdn.microsoft.com/stevelasker/2016/09/29/building-optimized-docker-images-with-asp-net-core/*](https://blogs.msdn.microsoft.com/stevelasker/2016/09/29/building-optimized-docker-images-with-asp-net-core/)</span></span>

### <a name="building-the-application-from-a-build-ci-container"></a><span data-ttu-id="ef266-248">Vytvoření aplikace z kontejneru sestavení (CI)</span><span class="sxs-lookup"><span data-stu-id="ef266-248">Building the application from a build (CI) container</span></span>

<span data-ttu-id="ef266-249">Další výhodou Dockeru je, že můžete vytvářet aplikace z předkonfigurovaných kontejneru, jak je znázorněno v obrázek 8-13, takže není nutné k vytvoření sestavení počítače nebo virtuálního počítače pro sestavení aplikace.</span><span class="sxs-lookup"><span data-stu-id="ef266-249">Another benefit of Docker is that you can build your application from a preconfigured container, as shown in Figure 8-13, so you do not need to create a build machine or VM to build your application.</span></span> <span data-ttu-id="ef266-250">Můžete použít nebo otestování tohoto sestavení kontejneru spuštěním na vývojovém počítači.</span><span class="sxs-lookup"><span data-stu-id="ef266-250">You can use or test that build container by running it at your development machine.</span></span> <span data-ttu-id="ef266-251">Ale co je ještě zajímavější, které můžete použít stejný kontejner sestavení z vašeho kanálu CI (průběžná integrace).</span><span class="sxs-lookup"><span data-stu-id="ef266-251">But what is even more interesting is that you can use the same build container from your CI (Continuous Integration) pipeline.</span></span>

![](./media/image14.png)

<span data-ttu-id="ef266-252">**Obrázek 8-13**.</span><span class="sxs-lookup"><span data-stu-id="ef266-252">**Figure 8-13**.</span></span> <span data-ttu-id="ef266-253">Sestavení – kontejner docker kompilace .NET binární soubory</span><span class="sxs-lookup"><span data-stu-id="ef266-253">Docker build-container compiling your .NET binaries</span></span> 

<span data-ttu-id="ef266-254">V tomto scénáři zajišťuje [microsoft/aspnetcore-build](https://hub.docker.com/r/microsoft/aspnetcore-build/) image, kterou můžete použít ke kompilaci a vytváření aplikací ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="ef266-254">For this scenario, we provide the [microsoft/aspnetcore-build](https://hub.docker.com/r/microsoft/aspnetcore-build/) image, which you can use to compile and build your ASP.NET Core apps.</span></span> <span data-ttu-id="ef266-255">Výstup se umístí do image založenou na [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) bitovou kopii, která je obrázek optimalizovaný modul runtime, jako v předchozí části.</span><span class="sxs-lookup"><span data-stu-id="ef266-255">The output is placed in an image based on the [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) image, which is an optimized runtime image, as previously noted.</span></span>

<span data-ttu-id="ef266-256">Image aspnetcore-build obsahuje všechno, co potřebujete, aby bylo možné zkompilovat aplikaci ASP.NET Core, včetně .NET Core, sady SDK technologie ASP.NET, npm, Bower, Gulp, atd.</span><span class="sxs-lookup"><span data-stu-id="ef266-256">The aspnetcore-build image contains everything you need in order to compile an ASP.NET Core application, including .NET Core, the ASP.NET SDK, npm, Bower, Gulp, etc.</span></span>

<span data-ttu-id="ef266-257">Potřebujeme tyto závislosti v okamžiku sestavení.</span><span class="sxs-lookup"><span data-stu-id="ef266-257">We need these dependencies at build time.</span></span> <span data-ttu-id="ef266-258">Ale jsme nechcete, aby tyto aplikace provádět za běhu, protože by byla image zbytečně velký.</span><span class="sxs-lookup"><span data-stu-id="ef266-258">But we do not want to carry these with the application at runtime, because it would make the image unnecessarily large.</span></span> <span data-ttu-id="ef266-259">V aplikaci eShopOnContainers aplikaci, můžete vytvořit aplikaci z kontejneru jednoduše spuštěním tohoto příkazu docker-compose.</span><span class="sxs-lookup"><span data-stu-id="ef266-259">In the eShopOnContainers application, you can build the application from a container by just running the following docker-compose command.</span></span>

```
  docker-compose -f docker-compose.ci.build.yml up
```

<span data-ttu-id="ef266-260">Obrázek 8-14 ukazuje tento příkaz spouštění na příkazovém řádku.</span><span class="sxs-lookup"><span data-stu-id="ef266-260">Figure 8-14 shows this command running at the command line.</span></span>

![](./media/image15.png)

<span data-ttu-id="ef266-261">**Obrázek 8-14.**</span><span class="sxs-lookup"><span data-stu-id="ef266-261">**Figure 8-14.**</span></span> <span data-ttu-id="ef266-262">Vytvoření aplikace .NET v kontejneru</span><span class="sxs-lookup"><span data-stu-id="ef266-262">Building your .NET application from a container</span></span>

<span data-ttu-id="ef266-263">Jak vidíte, je kontejner, na kterém běží sestavení ci\_počet kontejnerů: 1.</span><span class="sxs-lookup"><span data-stu-id="ef266-263">As you can see, the container that is running is the ci-build\_1 container.</span></span> <span data-ttu-id="ef266-264">To je založené na image aspnetcore-build tak, aby jeho kompilace a sestavení celé aplikace z v rámci tohoto kontejneru, nikoli z vašeho počítače.</span><span class="sxs-lookup"><span data-stu-id="ef266-264">This is based on the aspnetcore-build image so that it can compile and build your whole application from within that container instead of from your PC.</span></span> <span data-ttu-id="ef266-265">To znamená Proč ve skutečnosti je sestavení a kompilace projektů .NET Core v systému Linux, protože tento kontejner běží na hostiteli systému Linux Docker výchozí.</span><span class="sxs-lookup"><span data-stu-id="ef266-265">That is why in reality it is building and compiling the .NET Core projects in Linux—because that container is running on the default Docker Linux host.</span></span>

<span data-ttu-id="ef266-266">[Docker-compose.ci.build.yml](https://github.com/dotnet/eShopOnContainers/blob/master/docker-compose.ci.build.yml) soubor pro tuto bitovou kopii (součást aplikaci eShopOnContainers) obsahuje následující kód.</span><span class="sxs-lookup"><span data-stu-id="ef266-266">The [docker-compose.ci.build.yml](https://github.com/dotnet/eShopOnContainers/blob/master/docker-compose.ci.build.yml) file for that image (part of eShopOnContainers) contains the following code.</span></span> <span data-ttu-id="ef266-267">Uvidíte, že začne sestavení kontejneru pomocí [microsoft/aspnetcore-build](https://hub.docker.com/r/microsoft/aspnetcore-build/) bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="ef266-267">You can see that it starts a build container using the [microsoft/aspnetcore-build](https://hub.docker.com/r/microsoft/aspnetcore-build/) image.</span></span>

```yml
version: '3'

services:

  ci-build:

    image: microsoft/aspnetcore-build:2.0

    volumes:
      - .:/src

    working_dir: /src

    command: /bin/bash -c "pushd ./src/Web/WebSPA && npm rebuild node-sass && popd && dotnet restore ./eShopOnContainers-ServicesAndWebApps.sln && dotnet publish ./eShopOnContainers-ServicesAndWebApps.sln -c Release -o ./obj/Docker/publish"

```

* <span data-ttu-id="ef266-268">Počínaje **.NET Core 2.0**, `dotnet restore` příkaz spustí automaticky při `dotnet publish` spuštění příkazu.</span><span class="sxs-lookup"><span data-stu-id="ef266-268">Starting with **.NET Core 2.0**, `dotnet restore` command executes automatically when the `dotnet publish` command is executed.</span></span>

<span data-ttu-id="ef266-269">Po sestavení kontejneru je v provozu, spouští příkaz dotnet restore sady .NET SDK a dotnet publikovat příkazy spouštěly pro všechny projekty v řešení mohli zkompilovat .NET bits.</span><span class="sxs-lookup"><span data-stu-id="ef266-269">Once the build container is up and running, it runs the .NET SDK dotnet restore and dotnet publish commands against all the projects in the solution in order to compile the .NET bits.</span></span> <span data-ttu-id="ef266-270">V takovém případě aplikaci eShopOnContainers také obsahuje SPA podle TypeScript a Angular pro klientský kód, a proto potřebuje také kontrolovat závislosti jazyka JavaScript pomocí npm, ale tato akce není v relaci s bity .NET.</span><span class="sxs-lookup"><span data-stu-id="ef266-270">In this case, because eShopOnContainers also has an SPA based on TypeScript and Angular for the client code, it also needs to check JavaScript dependencies with npm, but that action is not related to the .NET bits.</span></span>

<span data-ttu-id="ef266-271">Dotnet publikovat příkaz sestavení a publikuje kompilovaný výstup v rámci složky projektu, každý... Složka /obj/Docker/Publish, jak ukazuje obrázek 8 – 15.</span><span class="sxs-lookup"><span data-stu-id="ef266-271">The dotnet publish command builds and publishes the compiled output within each project’s folder to the ../obj/Docker/publish folder, as shown in Figure 8-15.</span></span>

![](./media/image16.png)

<span data-ttu-id="ef266-272">**Obrázek 8 – 15.**</span><span class="sxs-lookup"><span data-stu-id="ef266-272">**Figure 8-15.**</span></span> <span data-ttu-id="ef266-273">Binární soubory generované záznamem pro dotnet příkazu pro publikování</span><span class="sxs-lookup"><span data-stu-id="ef266-273">Binary files generated by the dotnet publish command</span></span>

#### <a name="creating-the-docker-images-from-the-cli"></a><span data-ttu-id="ef266-274">Vytvoření Image Dockeru z rozhraní příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="ef266-274">Creating the Docker images from the CLI</span></span>

<span data-ttu-id="ef266-275">Po publikování výstup aplikace do souvisejících složek (v rámci každého projektu), dalším krokem je ve skutečnosti sestavit Image Dockeru.</span><span class="sxs-lookup"><span data-stu-id="ef266-275">Once the application output is published to the related folders (within each project), the next step is to actually build the Docker images.</span></span> <span data-ttu-id="ef266-276">K tomuto účelu použijte docker-compose sestavení a docker-compose up příkazy, jak ukazuje obrázek 8 – 16.</span><span class="sxs-lookup"><span data-stu-id="ef266-276">To do this, you use the docker-compose build and docker-compose up commands, as shown in Figure 8-16.</span></span>

![](./media/image17.png)

<span data-ttu-id="ef266-277">**Obrázek 8 – 16.**</span><span class="sxs-lookup"><span data-stu-id="ef266-277">**Figure 8-16.**</span></span> <span data-ttu-id="ef266-278">Vytváření imagí Dockeru a spuštění kontejnerů</span><span class="sxs-lookup"><span data-stu-id="ef266-278">Building Docker images and running the containers</span></span>

<span data-ttu-id="ef266-279">Obrázek 8-17 můžete zobrazit, jak vytvářet docker-compose spuštění příkazu.</span><span class="sxs-lookup"><span data-stu-id="ef266-279">In Figure 8-17, you can see how the docker-compose build command runs.</span></span>

![](./media/image18.png)

<span data-ttu-id="ef266-280">**Obrázek 8-17**.</span><span class="sxs-lookup"><span data-stu-id="ef266-280">**Figure 8-17**.</span></span> <span data-ttu-id="ef266-281">Vytváření imagí Dockeru docker-compose příkaz sestavení</span><span class="sxs-lookup"><span data-stu-id="ef266-281">Building the Docker images with the docker-compose build command</span></span>

<span data-ttu-id="ef266-282">Rozdíl mezi docker-compose sestavení a docker-compose up příkazy je, že docker-compose up sestavení a spuštění imagí.</span><span class="sxs-lookup"><span data-stu-id="ef266-282">The difference between the docker-compose build and docker-compose up commands is that docker-compose up both builds and starts the images.</span></span>

<span data-ttu-id="ef266-283">Při použití sady Visual Studio jsou všechny tyto kroky provést na pozadí.</span><span class="sxs-lookup"><span data-stu-id="ef266-283">When you use Visual Studio, all these steps are performed under the covers.</span></span> <span data-ttu-id="ef266-284">Visual Studio zkompiluje aplikaci .NET, vytvoří Image Dockeru a umožňuje nasazení kontejnerů do hostitele Dockeru.</span><span class="sxs-lookup"><span data-stu-id="ef266-284">Visual Studio compiles your .NET application, creates the Docker images, and deploys the containers into the Docker host.</span></span> <span data-ttu-id="ef266-285">Visual Studio nabízí další funkce, jako je schopnost ladit vaše kontejnery spuštěné v Dockeru, přímo ze sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="ef266-285">Visual Studio offers additional features, like the ability to debug your containers running in Docker, directly from Visual Studio.</span></span>

<span data-ttu-id="ef266-286">Celkové takeway zde je, že se můžete k sestavení aplikace stejný způsobem by měl svůj kanál CI/CD sestavte ho – z kontejneru místo z místního počítače.</span><span class="sxs-lookup"><span data-stu-id="ef266-286">The overall takeway here is that you are able to build your application the same way your CI/CD pipeline should build it—from a container instead of from a local machine.</span></span> <span data-ttu-id="ef266-287">Po s obrázky vytvořené, pak stačí pro spuštění imagí Dockeru pomocí dockeru-compose up příkazu.</span><span class="sxs-lookup"><span data-stu-id="ef266-287">After having the images created, then you just need to run the Docker images using the docker-compose up command.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="ef266-288">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="ef266-288">Additional resources</span></span>

-   <span data-ttu-id="ef266-289">**Vytváření bitů z kontejneru: nastavení řešení aplikaci eShopOnContainers v prostředí Windows CLI (rozhraní příkazového řádku dotnet, rozhraní příkazového řádku Dockeru a VS Code)**
    [*https://github.com/dotnet/eShopOnContainers/wiki/03.-Setting-the-eShopOnContainers-solution-up-in-a-Windows-CLI-environment-(dotnet-CLI, - Docker – rozhraní příkazového řádku- a -VS-kódu)*](https://github.com/dotnet/eShopOnContainers/wiki/03.-Setting-the-eShopOnContainers-solution-up-in-a-Windows-CLI-environment-(dotnet-CLI,-Docker-CLI-and-VS-Code))</span><span class="sxs-lookup"><span data-stu-id="ef266-289">**Building bits from a container: Setting the eShopOnContainers solution up in a Windows CLI environment (dotnet CLI, Docker CLI and VS Code)**
[*https://github.com/dotnet/eShopOnContainers/wiki/03.-Setting-the-eShopOnContainers-solution-up-in-a-Windows-CLI-environment-(dotnet-CLI,-Docker-CLI-and-VS-Code)*](https://github.com/dotnet/eShopOnContainers/wiki/03.-Setting-the-eShopOnContainers-solution-up-in-a-Windows-CLI-environment-(dotnet-CLI,-Docker-CLI-and-VS-Code))</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="ef266-290">[Předchozí](data-driven-crud-microservice.md)
[další](database-server-container.md)</span><span class="sxs-lookup"><span data-stu-id="ef266-290">[Previous](data-driven-crud-microservice.md)
[Next](database-server-container.md)</span></span>
