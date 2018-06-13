---
title: Definování vaší aplikace s více kontejnerů pomocí docker-compose.yml
description: Architektura Mikroslužeb .NET pro aplikace .NET Kontejnerizované | Definování vaší aplikace s více kontejnerů pomocí docker-compose.yml
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/30/2017
ms.openlocfilehash: ded2e5399938be25005776963b0310b6a49d0353
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33592350"
---
# <a name="defining-your-multi-container-application-with-docker-composeyml"></a><span data-ttu-id="2c576-103">Definování vaší aplikace s více kontejnerů pomocí docker-compose.yml</span><span class="sxs-lookup"><span data-stu-id="2c576-103">Defining your multi-container application with docker-compose.yml</span></span> 

<span data-ttu-id="2c576-104">V této příručce [docker-compose.yml](https://docs.docker.com/compose/compose-file/) souboru byla zavedena v části [kroku 4. Definování vašim službám v docker-compose.yml při vytvoření aplikace s více kontejner Docker](#step4_define_svcs_in_docker_compose_yml).</span><span class="sxs-lookup"><span data-stu-id="2c576-104">In this guide, the [docker-compose.yml](https://docs.docker.com/compose/compose-file/) file was introduced in the section [Step 4. Define your services in docker-compose.yml when building a multi-container Docker application](#step4_define_svcs_in_docker_compose_yml).</span></span> <span data-ttu-id="2c576-105">Existují však další způsoby, jak používat docker-compose soubory, které je vhodné využít podrobněji.</span><span class="sxs-lookup"><span data-stu-id="2c576-105">However, there are additional ways to use the docker-compose files that are worth exploring in further detail.</span></span>

<span data-ttu-id="2c576-106">Můžete například explicitně popisují, jak chcete nasadit aplikace s více kontejneru v soubor docker-compose.yml.</span><span class="sxs-lookup"><span data-stu-id="2c576-106">For example, you can explicitly describe how you want to deploy your multi-container application in the docker-compose.yml file.</span></span> <span data-ttu-id="2c576-107">Volitelně můžete také popisují, jak budete k vytváření vlastních bitových kopií Docker.</span><span class="sxs-lookup"><span data-stu-id="2c576-107">Optionally, you can also describe how you are going to build your custom Docker images.</span></span> <span data-ttu-id="2c576-108">(Imagí Dockeru vlastní také se dají vytvářet pomocí rozhraní příkazového řádku Dockeru.)</span><span class="sxs-lookup"><span data-stu-id="2c576-108">(Custom Docker images can also be built with the Docker CLI.)</span></span>

<span data-ttu-id="2c576-109">V podstatě můžete definovat každý z kontejnerů, které chcete nasadit plus určité charakteristické vlastnosti pro každý kontejner nasazení.</span><span class="sxs-lookup"><span data-stu-id="2c576-109">Basically, you define each of the containers you want to deploy plus certain characteristics for each container deployment.</span></span> <span data-ttu-id="2c576-110">Až budete mít soubor popisu nasazení několika kontejnerů, můžete nasadit celé řešení v rámci jedné akce řízená [docker compose až](https://docs.docker.com/compose/overview/) příkaz rozhraní příkazového řádku, nebo můžete nasadit transparentně ze sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="2c576-110">Once you have a multi-container deployment description file, you can deploy the whole solution in a single action orchestrated by the [docker-compose up](https://docs.docker.com/compose/overview/) CLI command, or you can deploy it transparently from Visual Studio.</span></span> <span data-ttu-id="2c576-111">Jinak by budete muset použít rozhraní příkazového řádku Dockeru nasazení kontejneru podle kontejneru v několika krocích pomocí docker, spusťte příkaz z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="2c576-111">Otherwise, you would need to use the Docker CLI to deploy container-by-container in multiple steps by using the docker run command from the command line.</span></span> <span data-ttu-id="2c576-112">Každá služba definované v docker-compose.yml proto musíte zadat přesně jednu bitovou kopii nebo sestavení.</span><span class="sxs-lookup"><span data-stu-id="2c576-112">Therefore, each service defined in docker-compose.yml must specify exactly one image or build.</span></span> <span data-ttu-id="2c576-113">Další klíče jsou volitelné a je obdobou jejich docker spuštění příkazového řádku svými protějšky.</span><span class="sxs-lookup"><span data-stu-id="2c576-113">Other keys are optional, and are analogous to their docker run command-line counterparts.</span></span>

<span data-ttu-id="2c576-114">Následující kód YAML je definice možné globální ale jeden soubor docker-compose.yml pro ukázku eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="2c576-114">The following YAML code is the definition of a possible global but single docker-compose.yml file for the eShopOnContainers sample.</span></span> <span data-ttu-id="2c576-115">Toto není soubor skutečné docker-compose z eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="2c576-115">This is not the actual docker-compose file from eShopOnContainers.</span></span> <span data-ttu-id="2c576-116">Místo toho je jednodušší a konsolidované verze v jednom souboru, který není nejlepší způsob, jak pracovat s docker tvoří soubory, jak bude vysvětleno později.</span><span class="sxs-lookup"><span data-stu-id="2c576-116">Instead, it is a simplified and consolidated version in a single file, which is not the best way to work with docker-compose files, as will be explained later.</span></span>

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

<span data-ttu-id="2c576-117">Kořenový klíč v tomto souboru se služeb.</span><span class="sxs-lookup"><span data-stu-id="2c576-117">The root key in this file is services.</span></span> <span data-ttu-id="2c576-118">Pod tímto klíčem definujete služby, kterou chcete nasadit a spustit při spuštění docker compose příkaz nebo při nasazení ze sady Visual Studio pomocí tento soubor docker-compose.yml.</span><span class="sxs-lookup"><span data-stu-id="2c576-118">Under that key you define the services you want to deploy and run when you execute the docker-compose up command or when you deploy from Visual Studio by using this docker-compose.yml file.</span></span> <span data-ttu-id="2c576-119">V tomto případě soubor docker-compose.yml má více služeb definovat, jak je popsáno v následujícím seznamu.</span><span class="sxs-lookup"><span data-stu-id="2c576-119">In this case, the docker-compose.yml file has multiple services defined, as described in the following list.</span></span>

-   <span data-ttu-id="2c576-120">webmvc kontejneru, včetně aplikace ASP.NET MVC základní využívání mikroslužeb ze serverové C\#</span><span class="sxs-lookup"><span data-stu-id="2c576-120">webmvc Container including the ASP.NET Core MVC application consuming the microservices from server-side C\#</span></span>

-   <span data-ttu-id="2c576-121">CATALOG.API včetně mikroslužbu webového rozhraní API pro jádro ASP.NET katalog kontejner</span><span class="sxs-lookup"><span data-stu-id="2c576-121">catalog.api Container including the Catalog ASP.NET Core Web API microservice</span></span>

-   <span data-ttu-id="2c576-122">Ordering.API kontejneru, včetně mikroslužbu řazení rozhraní ASP.NET Web API Core</span><span class="sxs-lookup"><span data-stu-id="2c576-122">ordering.api Container including the Ordering ASP.NET Core Web API microservice</span></span>

-   <span data-ttu-id="2c576-123">SQL.data kontejneru systémem SQL Server pro Linux, která uchovává mikroslužeb databáze</span><span class="sxs-lookup"><span data-stu-id="2c576-123">sql.data Container running SQL Server for Linux, holding the microservices databases</span></span>

-   <span data-ttu-id="2c576-124">basket.API kontejner s mikroslužbu košík ASP.NET Core webového rozhraní API</span><span class="sxs-lookup"><span data-stu-id="2c576-124">basket.api Container with the Basket ASP.NET Core Web API microservice</span></span>

-   <span data-ttu-id="2c576-125">basket.data kontejneru službu REDIS cache s databázi košík jako mezipaměti REDIS</span><span class="sxs-lookup"><span data-stu-id="2c576-125">basket.data Container running the REDIS cache service, with the basket database as a REDIS cache</span></span>

### <a name="a-simple-web-service-api-container"></a><span data-ttu-id="2c576-126">Kontejner jednoduché rozhraní API webové služby</span><span class="sxs-lookup"><span data-stu-id="2c576-126">A simple Web Service API container</span></span>

<span data-ttu-id="2c576-127">Zaměřený na jediný kontejner, catalog.api kontejneru mikroslužbu má přehledné definice:</span><span class="sxs-lookup"><span data-stu-id="2c576-127">Focusing on a single container, the catalog.api container-microservice has a straightforward definition:</span></span>

```yml
  catalog.api:
    image: eshop/catalog.api
    environment:
      - ConnectionString=Server=catalog.data;Initial Catalog=CatalogData;User Id=sa;Password=your@password
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

<span data-ttu-id="2c576-128">Tato služba kontejnerizované má následující základní konfiguraci:</span><span class="sxs-lookup"><span data-stu-id="2c576-128">This containerized service has the following basic configuration:</span></span>

-   <span data-ttu-id="2c576-129">Je založena na bitovou kopii vlastní eshop/catalog.api.</span><span class="sxs-lookup"><span data-stu-id="2c576-129">It is based on the custom eshop/catalog.api image.</span></span> <span data-ttu-id="2c576-130">Pro saké na jednoduchost, neexistuje žádné sestavení: klíč nastavení v souboru.</span><span class="sxs-lookup"><span data-stu-id="2c576-130">For simplicity’s sake, there is no build: key setting in the file.</span></span> <span data-ttu-id="2c576-131">To znamená, že bitovou kopii musí mít byla dříve vytvořená (pomocí docker sestavení) nebo byly staženy (pomocí příkazu docker vyžádání obsahu) z jakékoli Docker registru.</span><span class="sxs-lookup"><span data-stu-id="2c576-131">This means that the image must have been previously built (with docker build) or have been downloaded (with the docker pull command) from any Docker registry.</span></span>

-   <span data-ttu-id="2c576-132">Definuje proměnnou prostředí s názvem připojovacího řetězce připojovacím řetězcem, který bude používat pro přístup k instanci systému SQL Server, který obsahuje datový model katalogu Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="2c576-132">It defines an environment variable named ConnectionString with the connection string to be used by Entity Framework to access the SQL Server instance that contains the catalog data model.</span></span> <span data-ttu-id="2c576-133">V takovém případě stejnému kontejneru systému SQL Server je podržíte více databází.</span><span class="sxs-lookup"><span data-stu-id="2c576-133">In this case, the same SQL Server container is holding multiple databases.</span></span> <span data-ttu-id="2c576-134">Proto musíte méně paměti v počítači pro vývoj pro Docker.</span><span class="sxs-lookup"><span data-stu-id="2c576-134">Therefore, you need less memory in your development machine for Docker.</span></span> <span data-ttu-id="2c576-135">Můžete však také nasadit jednoho kontejneru typu SQL Server pro každou databázi mikroslužby.</span><span class="sxs-lookup"><span data-stu-id="2c576-135">However, you could also deploy one SQL Server container for each microservice database.</span></span>

-   <span data-ttu-id="2c576-136">Název systému SQL Server je sql.data, což je stejný název používá pro kontejner, ve kterém běží instance systému SQL Server pro Linux.</span><span class="sxs-lookup"><span data-stu-id="2c576-136">The SQL Server name is sql.data, which is the same name used for the container that is running the SQL Server instance for Linux.</span></span> <span data-ttu-id="2c576-137">To je vhodné; bude možné použít tento překlad (interní Docker hostitele) bude vyřešen síťová adresa, takže není nutné znát interní IP adresu pro kontejnerů, které se připojujete z jiných kontejnerů.</span><span class="sxs-lookup"><span data-stu-id="2c576-137">This is convenient; being able to use this name resolution (internal to the Docker host) will resolve the network address so you don’t need to know the internal IP for the containers you are accessing from other containers.</span></span>

<span data-ttu-id="2c576-138">Protože připojovací řetězec je definované proměnné prostředí, můžete tuto proměnnou nastavit přes jiný mechanismus a v jinou dobu.</span><span class="sxs-lookup"><span data-stu-id="2c576-138">Because the connection string is defined by an environment variable, you could set that variable through a different mechanism and at a different time.</span></span> <span data-ttu-id="2c576-139">Například můžete nastavit různé připojovací řetězec při nasazení do produkčního prostředí v posledním hostitelů nebo proveďte z kanály CI/CD služby VSTS nebo upřednostňovaný DevOps systému.</span><span class="sxs-lookup"><span data-stu-id="2c576-139">For example, you could set a different connection string when deploying to production in the final hosts, or by doing it from your CI/CD pipelines in VSTS or your preferred DevOps system.</span></span>

-   <span data-ttu-id="2c576-140">Zpřístupňuje port 80 pro interní přístup ke službě catalog.api v rámci Docker hostitele.</span><span class="sxs-lookup"><span data-stu-id="2c576-140">It exposes port 80 for internal access to the catalog.api service within the Docker host.</span></span> <span data-ttu-id="2c576-141">Hostitel je aktuálně virtuálního počítače s Linuxem, protože je založena na bitovou kopii Docker pro Linux, ale může nakonfigurovat kontejner, aby místo toho spustit na bitovou kopii systému Windows.</span><span class="sxs-lookup"><span data-stu-id="2c576-141">The host is currently a Linux VM because it is based on a Docker image for Linux, but you could configure the container to run on a Windows image instead.</span></span>

-   <span data-ttu-id="2c576-142">Předává zveřejněné port 80 kontejneru na port 5101 na hostitelském počítači Docker (virtuálního počítače s Linuxem).</span><span class="sxs-lookup"><span data-stu-id="2c576-142">It forwards the exposed port 80 on the container to port 5101 on the Docker host machine (the Linux VM).</span></span>

-   <span data-ttu-id="2c576-143">Webové služby se odkazuje na službu sql.data (instance systému SQL Server pro databázi Linux spuštěné v kontejneru).</span><span class="sxs-lookup"><span data-stu-id="2c576-143">It links the web service to the sql.data service (the SQL Server instance for Linux database running in a container).</span></span> <span data-ttu-id="2c576-144">Pokud určíte tuto závislost, kontejneru catalog.api nespustí, dokud již bylo zahájeno sql.data kontejneru; To je důležité, protože catalog.api musí mít databázi systému SQL Server a spuštěna nejdřív.</span><span class="sxs-lookup"><span data-stu-id="2c576-144">When you specify this dependency, the catalog.api container will not start until the sql.data container has already started; this is important because catalog.api needs to have the SQL Server database up and running first.</span></span> <span data-ttu-id="2c576-145">Však tento druh kontejneru závislost není dost v mnoha případech, protože Docker kontroluje jenom na úrovni kontejneru.</span><span class="sxs-lookup"><span data-stu-id="2c576-145">However, this kind of container dependency is not enough in many cases, because Docker checks only at the container level.</span></span> <span data-ttu-id="2c576-146">Někdy služby (v tomto případu SQL serveru) stále možná není připravené, proto se doporučuje implementovat logiku opakovaných pokusů s exponenciálního omezení rychlosti v mikroslužeb vašeho klienta.</span><span class="sxs-lookup"><span data-stu-id="2c576-146">Sometimes the service (in this case SQL Server) might still not be ready, so it is advisable to implement retry logic with exponential backoff in your client microservices.</span></span> <span data-ttu-id="2c576-147">Tímto způsobem, pokud není připraven na krátkou dobu kontejner závislost aplikace zůstanou odolný.</span><span class="sxs-lookup"><span data-stu-id="2c576-147">That way, if a dependency container is not ready for a short time, the application will still be resilient.</span></span>

-   <span data-ttu-id="2c576-148">Je nakonfigurován pro povolení přístupu k externích serverů: nadbytečné\_hostitelů nastavení umožňuje přístup k externím serverům nebo počítače mimo hostitelů Docker (který je mimo výchozí virtuálních počítačů Linux, který je vývoj Docker hostitele), jako je například místní databáze SQL Instance serveru na váš vývojový počítač.</span><span class="sxs-lookup"><span data-stu-id="2c576-148">It is configured to allow access to external servers: the extra\_hosts setting allows you to access external servers or machines outside of the Docker host (that is, outside the default Linux VM which is a development Docker host), such as a local SQL Server instance on your development PC.</span></span>

<span data-ttu-id="2c576-149">Existují také další, pokročilejší docker-compose.yml nastavení, která se budeme zabývat v následujících částech.</span><span class="sxs-lookup"><span data-stu-id="2c576-149">There are also other, more advanced docker-compose.yml settings that we will discuss in the following sections.</span></span>

### <a name="using-docker-compose-files-to-target-multiple-environments"></a><span data-ttu-id="2c576-150">Pomocí docker tvoří pro prostředí s více soubory</span><span class="sxs-lookup"><span data-stu-id="2c576-150">Using docker-compose files to target multiple environments</span></span>

<span data-ttu-id="2c576-151">Soubory docker-compose.yml jsou definiční soubory a mohou být využívána více infrastruktury, které pochopit, že formát.</span><span class="sxs-lookup"><span data-stu-id="2c576-151">The docker-compose.yml files are definition files and can be used by multiple infrastructures that understand that format.</span></span> <span data-ttu-id="2c576-152">Nástroj nejjednodušší je docker-tvoří příkazu, ale jiné nástroje, jako orchestrators (například Docker Swarm) také chápou tento soubor.</span><span class="sxs-lookup"><span data-stu-id="2c576-152">The most straightforward tool is the docker-compose command, but other tools like orchestrators (for example, Docker Swarm) also understand that file.</span></span>

<span data-ttu-id="2c576-153">Proto pomocí docker compose příkaz můžete cílit na následující hlavní scénáře.</span><span class="sxs-lookup"><span data-stu-id="2c576-153">Therefore, by using the docker-compose command you can target the following main scenarios.</span></span>

#### <a name="development-environments"></a><span data-ttu-id="2c576-154">Vývojové prostředí</span><span class="sxs-lookup"><span data-stu-id="2c576-154">Development environments</span></span>

<span data-ttu-id="2c576-155">Při vývoji aplikací, je důležité, abyste mohli spustit aplikaci izolované vývojovém prostředí.</span><span class="sxs-lookup"><span data-stu-id="2c576-155">When you develop applications, it is important to be able to run an application in an isolated development environment.</span></span> <span data-ttu-id="2c576-156">Můžete použít docker compose rozhraní příkazového řádku příkaz k vytvoření tohoto prostředí nebo Visual Studio, který používá docker tvoří skrytě.</span><span class="sxs-lookup"><span data-stu-id="2c576-156">You can use the docker-compose CLI command to create that environment or use Visual Studio which uses docker-compose under the covers.</span></span>

<span data-ttu-id="2c576-157">Soubor docker-compose.yml umožňuje nakonfigurovat a zdokumentovat všechny aplikace služby závislosti (jiných služeb, mezipaměti, databáze, fronty, atd.).</span><span class="sxs-lookup"><span data-stu-id="2c576-157">The docker-compose.yml file allows you to configure and document all your application’s service dependencies (other services, cache, databases, queues, etc.).</span></span> <span data-ttu-id="2c576-158">Pomocí docker compose příkaz rozhraní příkazového řádku, můžete vytvořit a spustit jeden nebo více kontejnerů pro každá závislost jedním příkazem (docker tvoří nahoru).</span><span class="sxs-lookup"><span data-stu-id="2c576-158">Using the docker-compose CLI command, you can create and start one or more containers for each dependency with a single command (docker-compose up).</span></span>

<span data-ttu-id="2c576-159">Soubory docker-compose.yml jsou interpretovat pomocí modulu Docker konfigurační soubory, ale také fungovat jako soubory pohodlný dokumentaci o složení více kontejneru aplikace.</span><span class="sxs-lookup"><span data-stu-id="2c576-159">The docker-compose.yml files are configuration files interpreted by Docker engine but also serve as convenient documentation files about the composition of your multi-container application.</span></span>

#### <a name="testing-environments"></a><span data-ttu-id="2c576-160">Testovacích prostředích</span><span class="sxs-lookup"><span data-stu-id="2c576-160">Testing environments</span></span>

<span data-ttu-id="2c576-161">Důležitou součástí žádné průběžné nasazování (CD) nebo proces průběžnou integraci (CI) jsou testy částí a integrace testy.</span><span class="sxs-lookup"><span data-stu-id="2c576-161">An important part of any continuous deployment (CD) or continuous integration (CI) process are the unit tests and integration tests.</span></span> <span data-ttu-id="2c576-162">Tyto automatizované testy vyžadují izolovaném prostředí, nebude mít dopad uživatele nebo všechny ostatní změny v datech aplikace.</span><span class="sxs-lookup"><span data-stu-id="2c576-162">These automated tests require an isolated environment so they are not impacted by the users or any other change in the application’s data.</span></span>

<span data-ttu-id="2c576-163">Pomocí Docker Compose můžete vytvořit a zrušení izolované prostředí velmi snadno v několika příkazů z příkazového řádku nebo skripty, například následující příkazy:</span><span class="sxs-lookup"><span data-stu-id="2c576-163">With Docker Compose you can create and destroy that isolated environment very easily in a few commands from your command prompt or scripts, like the following commands:</span></span>

```
docker-compose up -d
./run_unit_tests
docker-compose down
```

#### <a name="production-deployments"></a><span data-ttu-id="2c576-164">Nasazení v produkčním prostředí</span><span class="sxs-lookup"><span data-stu-id="2c576-164">Production deployments</span></span>

<span data-ttu-id="2c576-165">Můžete taky vytvořit k nasazení na vzdálené modulu Docker.</span><span class="sxs-lookup"><span data-stu-id="2c576-165">You can also use Compose to deploy to a remote Docker Engine.</span></span> <span data-ttu-id="2c576-166">Obvyklý případ je nasadit do jedné instance Docker hostitele (jako jsou například produkční virtuálního počítače nebo serveru zřizovat s [počítač Docker](https://docs.docker.com/machine/overview/)).</span><span class="sxs-lookup"><span data-stu-id="2c576-166">A typical case is to deploy to a single Docker host instance (like a production VM or server provisioned with [Docker Machine](https://docs.docker.com/machine/overview/)).</span></span> <span data-ttu-id="2c576-167">Ale mohou být také celou [Docker Swarm](https://docs.docker.com/swarm/overview/) clusteru, protože clustery jsou kompatibilní s soubory docker-compose.yml.</span><span class="sxs-lookup"><span data-stu-id="2c576-167">But it could also be an entire [Docker Swarm](https://docs.docker.com/swarm/overview/) cluster, because clusters are also compatible with the docker-compose.yml files.</span></span>

<span data-ttu-id="2c576-168">Pokud používáte jiné orchestrator (Azure Service Fabric, Mesos DC/OS, Kubernetes atd.), vám může být nutné přidat nastavení konfigurace Instalační program a metadata stejně jako v nástroji docker-compose.yml, ale ve formátu vyžaduje další orchestrator.</span><span class="sxs-lookup"><span data-stu-id="2c576-168">If you are using any other orchestrator (Azure Service Fabric, Mesos DC/OS, Kubernetes, etc.), you might need to add setup and metadata configuration settings like those in docker-compose.yml, but in the format required by the other orchestrator.</span></span>

<span data-ttu-id="2c576-169">V každém případě docker compose je vhodné nástroje a metadata formát pro vývoj, testování a provozním pracovní postupy, i když pracovním postupu mohou lišit na orchestrator, kterou používáte.</span><span class="sxs-lookup"><span data-stu-id="2c576-169">In any case, docker-compose is a convenient tool and metadata format for development, testing and production workflows, although the production workflow might vary on the orchestrator you are using.</span></span>

### <a name="using-multiple-docker-compose-files-to-handle-several-environments"></a><span data-ttu-id="2c576-170">Pomocí několika docker tvoří soubory pro zpracování více prostředích</span><span class="sxs-lookup"><span data-stu-id="2c576-170">Using multiple docker-compose files to handle several environments</span></span>

<span data-ttu-id="2c576-171">Pokud je cílem různých prostředích, měli byste použít více tvoří soubory.</span><span class="sxs-lookup"><span data-stu-id="2c576-171">When targeting different environments, you should use multiple compose files.</span></span> <span data-ttu-id="2c576-172">To vám umožní vytvořit více variant konfigurace v závislosti na prostředí.</span><span class="sxs-lookup"><span data-stu-id="2c576-172">This lets you create multiple configuration variants depending on the environment.</span></span>

#### <a name="overriding-the-base-docker-compose-file"></a><span data-ttu-id="2c576-173">Přepsání soubor základní docker-compose</span><span class="sxs-lookup"><span data-stu-id="2c576-173">Overriding the base docker-compose file</span></span>

<span data-ttu-id="2c576-174">Můžete použít soubor docker-compose.yml jeden jako zjednodušenou příklady uvedené v předchozí části.</span><span class="sxs-lookup"><span data-stu-id="2c576-174">You could use a single docker-compose.yml file as in the simplified examples shown in previous sections.</span></span> <span data-ttu-id="2c576-175">Které však není doporučeno pro většinu aplikací.</span><span class="sxs-lookup"><span data-stu-id="2c576-175">However, that is not recommended for most applications.</span></span>

<span data-ttu-id="2c576-176">Ve výchozím nastavení přečte vytvářené ze dvou souborů, docker-compose.yml a soubor docker-compose.override.yml volitelné.</span><span class="sxs-lookup"><span data-stu-id="2c576-176">By default, Compose reads two files, a docker-compose.yml and an optional docker-compose.override.yml file.</span></span> <span data-ttu-id="2c576-177">Jak ukazuje obrázek 8-11, když pomocí sady Visual Studio a také povolení podpory Docker, Visual Studio vytvoří soubor docker-compose.ci.build,yml Další budete moci použít z položek konfigurace nebo CD kanálů, jako v služby VSTS.</span><span class="sxs-lookup"><span data-stu-id="2c576-177">As shown in Figure 8-11, when you are using Visual Studio and enabling Docker support, Visual Studio also creates an additional docker-compose.ci.build,yml file for you to use from your CI/CD pipelines like in VSTS.</span></span>

![](./media/image12.png)

<span data-ttu-id="2c576-178">**Obrázek 8-11**.</span><span class="sxs-lookup"><span data-stu-id="2c576-178">**Figure 8-11**.</span></span> <span data-ttu-id="2c576-179">soubory ve Visual Studio 2017 docker compose</span><span class="sxs-lookup"><span data-stu-id="2c576-179">docker-compose files in Visual Studio 2017</span></span>

<span data-ttu-id="2c576-180">Můžete upravit soubory docker-compose pomocí libovolného editoru, jako je Visual Studio Code nebo Sublime a spusťte aplikaci pomocí docker compose až příkaz.</span><span class="sxs-lookup"><span data-stu-id="2c576-180">You can edit the docker-compose files with any editor, like Visual Studio Code or Sublime, and run the application with the docker-compose up command.</span></span>

<span data-ttu-id="2c576-181">Podle konvence soubor docker-compose.yml obsahuje základní konfiguraci a další nastavení statické.</span><span class="sxs-lookup"><span data-stu-id="2c576-181">By convention, the docker-compose.yml file contains your base configuration and other static settings.</span></span> <span data-ttu-id="2c576-182">To znamená, že v závislosti na prostředí pro nasazení, které se zaměříte neměli měnit konfiguraci služby.</span><span class="sxs-lookup"><span data-stu-id="2c576-182">That means that the service configuration should not change depending on the deployment environment you are targeting.</span></span>

<span data-ttu-id="2c576-183">Soubor docker-compose.override.yml, jak naznačuje název obsahuje nastavení konfigurace, které potlačí základní konfigurace, jako je například konfigurace, která závisí na prostředí nasazení.</span><span class="sxs-lookup"><span data-stu-id="2c576-183">The docker-compose.override.yml file, as its name suggests, contains configuration settings that override the base configuration, such as configuration that depends on the deployment environment.</span></span> <span data-ttu-id="2c576-184">Také můžete mít víc přepsání souborů s různými názvy.</span><span class="sxs-lookup"><span data-stu-id="2c576-184">You can have multiple override files with different names also.</span></span> <span data-ttu-id="2c576-185">Soubory přepsání obvykle obsahují další informace potřebné pro aplikaci, ale konkrétní prostředí a nasazení.</span><span class="sxs-lookup"><span data-stu-id="2c576-185">The override files usually contain additional information needed by the application but specific to an environment or to a deployment.</span></span>

#### <a name="targeting-multiple-environments"></a><span data-ttu-id="2c576-186">Cílení na více prostředí</span><span class="sxs-lookup"><span data-stu-id="2c576-186">Targeting multiple environments</span></span>

<span data-ttu-id="2c576-187">Typické použití případ je při definování více tvoří soubory, můžete určit cílovou několika prostředích, jako výrobní, pracovní položky konfigurace nebo vývoj.</span><span class="sxs-lookup"><span data-stu-id="2c576-187">A typical use case is when you define multiple compose files so you can target multiple environments, like production, staging, CI, or development.</span></span> <span data-ttu-id="2c576-188">Pro podporu tyto rozdíly, je možné rozdělit konfiguraci psaní do více souborů, jak ukazuje obrázek 8-12.</span><span class="sxs-lookup"><span data-stu-id="2c576-188">To support these differences, you can split your Compose configuration into multiple files, as shown in Figure 8-12.</span></span>

![](./media/image13.png)

<span data-ttu-id="2c576-189">**Obrázek 8-12**.</span><span class="sxs-lookup"><span data-stu-id="2c576-189">**Figure 8-12**.</span></span> <span data-ttu-id="2c576-190">Více docker tvoří soubory potlačení hodnot v souboru základní docker-compose.yml</span><span class="sxs-lookup"><span data-stu-id="2c576-190">Multiple docker-compose files overriding values in the base docker-compose.yml file</span></span>

<span data-ttu-id="2c576-191">Začínat soubor základní docker-compose.yml.</span><span class="sxs-lookup"><span data-stu-id="2c576-191">You start with the base docker-compose.yml file.</span></span> <span data-ttu-id="2c576-192">Tento základní soubor musí obsahovat nastavení základní nebo statické konfigurace, která se nemění v závislosti na prostředí.</span><span class="sxs-lookup"><span data-stu-id="2c576-192">This base file has to contain the base or static configuration settings that do not change depending on the environment.</span></span> <span data-ttu-id="2c576-193">Například eShopOnContainers má následující soubor docker-compose.yml jako základního souboru.</span><span class="sxs-lookup"><span data-stu-id="2c576-193">For example, the eShopOnContainers has the following docker-compose.yml file as the base file.</span></span>

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

<span data-ttu-id="2c576-194">Z důvodu jiný cíl nasazení prostředí neměli měnit hodnoty v souboru základní docker-compose.yml.</span><span class="sxs-lookup"><span data-stu-id="2c576-194">The values in the base docker-compose.yml file should not change because of different target deployment environments.</span></span>

<span data-ttu-id="2c576-195">Pokud byste se zaměřit na definici služby webmvc, například najdete v tom, jak tyto informace je podobný bez ohledu na to, jaké prostředí může cílení.</span><span class="sxs-lookup"><span data-stu-id="2c576-195">If you focus on the webmvc service definition, for instance, you can see how that information is much the same no matter what environment you might be targeting.</span></span> <span data-ttu-id="2c576-196">Máte následující informace:</span><span class="sxs-lookup"><span data-stu-id="2c576-196">You have the following information:</span></span>

-   <span data-ttu-id="2c576-197">Název služby: webmvc.</span><span class="sxs-lookup"><span data-stu-id="2c576-197">The service name: webmvc.</span></span>

-   <span data-ttu-id="2c576-198">Vlastní image kontejneru: eshop/webmvc.</span><span class="sxs-lookup"><span data-stu-id="2c576-198">The container’s custom image: eshop/webmvc.</span></span>

-   <span data-ttu-id="2c576-199">Příkaz k vytvoření vlastních Docker bitovou kopii, která určuje, které soubor Docker používat.</span><span class="sxs-lookup"><span data-stu-id="2c576-199">The command to build the custom Docker image, indicating which Dockerfile to use.</span></span>

-   <span data-ttu-id="2c576-200">Závislosti na dalších službách, proto tento kontejner se nespustí, dokud spustili jiných kontejnerů závislostí.</span><span class="sxs-lookup"><span data-stu-id="2c576-200">Dependencies on other services, so this container does not start until the other dependency containers have started.</span></span>

<span data-ttu-id="2c576-201">Můžete mít další konfiguraci, ale důležité je, že v souboru základní docker-compose.yml jenom chcete nastavit informace, které je společná pro prostředí.</span><span class="sxs-lookup"><span data-stu-id="2c576-201">You can have additional configuration, but the important point is that in the base docker-compose.yml file, you just want to set the information that is common across environments.</span></span> <span data-ttu-id="2c576-202">Pak by měl v docker compose.override.yml nebo podobné soubory pro produkční nebo pracovní umístit konfigurace, které jsou specifické pro každé prostředí.</span><span class="sxs-lookup"><span data-stu-id="2c576-202">Then in the docker-compose.override.yml or similar files for production or staging, you should place configuration that is specific for each environment.</span></span>

<span data-ttu-id="2c576-203">Docker-compose.override.yml se obvykle používá pro vývojové prostředí, jako v následujícím příkladu z eShopOnContainers:</span><span class="sxs-lookup"><span data-stu-id="2c576-203">Usually, the docker-compose.override.yml is used for your development environment, as in the following example from eShopOnContainers:</span></span>

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

<span data-ttu-id="2c576-204">V tomto příkladu konfigurace přepisování vývoj vystavuje některé porty na hostitele, definuje proměnných prostředí pomocí adresy URL pro přesměrování a určuje připojovací řetězce pro vývojové prostředí.</span><span class="sxs-lookup"><span data-stu-id="2c576-204">In this example, the development override configuration exposes some ports to the host, defines environment variables with redirect URLs, and specifies connection strings for the development environment.</span></span> <span data-ttu-id="2c576-205">Tato nastavení jsou všechny jenom pro vývojové prostředí.</span><span class="sxs-lookup"><span data-stu-id="2c576-205">These settings are all just for the development environment.</span></span>

<span data-ttu-id="2c576-206">Při spuštění `docker-compose up` (nebo ji spustit ze sady Visual Studio), příkaz načte přepsání automaticky jako by se měla slučování oba soubory.</span><span class="sxs-lookup"><span data-stu-id="2c576-206">When you run `docker-compose up` (or launch it from Visual Studio), the command reads the overrides automatically as if it were merging both files.</span></span>

<span data-ttu-id="2c576-207">Předpokládejme, že chcete jiný soubor vytvářené pro produkční prostředí, s jinou konfiguraci hodnot, porty nebo připojovací řetězce.</span><span class="sxs-lookup"><span data-stu-id="2c576-207">Suppose that you want another Compose file for the production environment, with different configuration values, ports or connection strings.</span></span> <span data-ttu-id="2c576-208">Můžete vytvořit jiný soubor přepsat, jako je soubor s názvem `docker-compose.prod.yml` s různá nastavení a proměnných prostředí.</span><span class="sxs-lookup"><span data-stu-id="2c576-208">You can create another override file, like file named `docker-compose.prod.yml` with different settings and environment variables.</span></span>  <span data-ttu-id="2c576-209">Tento soubor může být uložená v různých úložiště Git nebo spravovat a zabezpečené na jiný tým.</span><span class="sxs-lookup"><span data-stu-id="2c576-209">That file might be stored in a different Git repo or managed and secured by a different team.</span></span>

#### <a name="how-to-deploy-with-a-specific-override-file"></a><span data-ttu-id="2c576-210">Nasazení s soubor specifické přepsání</span><span class="sxs-lookup"><span data-stu-id="2c576-210">How to deploy with a specific override file</span></span>

<span data-ttu-id="2c576-211">Pokud chcete použít víc souborů přepsání nebo k přepsání souboru s jiným názvem, můžete použít možnost -f pomocí docker compose příkaz a zadejte soubory.</span><span class="sxs-lookup"><span data-stu-id="2c576-211">To use multiple override files, or an override file with a different name, you can use the -f option with the docker-compose command and specify the files.</span></span> <span data-ttu-id="2c576-212">Napište sloučení souborů v pořadí, ve kterém jsou uvedené v příkazovém řádku.</span><span class="sxs-lookup"><span data-stu-id="2c576-212">Compose merges files in the order they are specified on the command line.</span></span> <span data-ttu-id="2c576-213">Následující příklad ukazuje, jak nasadit pomocí přepsání souborů.</span><span class="sxs-lookup"><span data-stu-id="2c576-213">The following example shows how to deploy with override files.</span></span>

```
docker-compose -f docker-compose.yml -f docker-compose.prod.yml up -d
```

#### <a name="using-environment-variables-in-docker-compose-files"></a><span data-ttu-id="2c576-214">Použití proměnných prostředí v docker nové soubory</span><span class="sxs-lookup"><span data-stu-id="2c576-214">Using environment variables in docker-compose files</span></span>

<span data-ttu-id="2c576-215">To bude vyhovovat, zejména v produkčním prostředí, abyste mohli získat informace o konfiguraci z proměnné prostředí, jako v předchozích příkladech můžeme ukázaly.</span><span class="sxs-lookup"><span data-stu-id="2c576-215">It is convenient, especially in production environments, to be able to get configuration information from environment variables, as we have shown in previous examples.</span></span> <span data-ttu-id="2c576-216">Referenční proměnné prostředí v souborech docker-compose pomocí syntaxe \${MY\_VAR}.</span><span class="sxs-lookup"><span data-stu-id="2c576-216">You reference an environment variable in your docker-compose files using the syntax \${MY\_VAR}.</span></span> <span data-ttu-id="2c576-217">Následující řádek ze souboru docker compose.prod.yml ukazuje, jak chcete-li hodnota proměnné prostředí.</span><span class="sxs-lookup"><span data-stu-id="2c576-217">The following line from a docker-compose.prod.yml file shows how to reference the value of an environment variable.</span></span>

```yml
IdentityUrl=http://${ESHOP_PROD_EXTERNAL_DNS_NAME_OR_IP}:5105
```

<span data-ttu-id="2c576-218">Proměnné prostředí jsou vytvořeny a inicializovány různými způsoby v závislosti na prostředí hostitele (Linux, Windows, cloudu clusteru, atd.).</span><span class="sxs-lookup"><span data-stu-id="2c576-218">Environment variables are created and initialized in different ways, depending on your host environment (Linux, Windows, Cloud cluster, etc.).</span></span> <span data-ttu-id="2c576-219">Pohodlnější přístup je však můžete použít soubor .env.</span><span class="sxs-lookup"><span data-stu-id="2c576-219">However, a convenient approach is to use an .env file.</span></span> <span data-ttu-id="2c576-220">Podpora souborů docker-compose deklarace proměnné prostředí v souboru .env výchozí.</span><span class="sxs-lookup"><span data-stu-id="2c576-220">The docker-compose files support declaring default environment variables in the .env file.</span></span> <span data-ttu-id="2c576-221">Tyto hodnoty pro proměnné prostředí jsou výchozí hodnoty.</span><span class="sxs-lookup"><span data-stu-id="2c576-221">These values for the environment variables are the default values.</span></span> <span data-ttu-id="2c576-222">Ale mohou být přepsány hodnoty, které může jste definovali v každé z vašich prostředích (hostitelský operační systém nebo proměnné prostředí z clusteru).</span><span class="sxs-lookup"><span data-stu-id="2c576-222">But they can be overridden by the values you might have defined in each of your environments (host OS or environment variables from your cluster).</span></span> <span data-ttu-id="2c576-223">Umístěte tento soubor .env ve složce, kde docker compose příkaz spuštěn z.</span><span class="sxs-lookup"><span data-stu-id="2c576-223">You place this .env file in the folder where the docker-compose command is executed from.</span></span>

<span data-ttu-id="2c576-224">Následující příklad ukazuje soubor .env jako [.env](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/.env) soubor eShopOnContainers aplikace.</span><span class="sxs-lookup"><span data-stu-id="2c576-224">The following example shows an .env file like the [.env](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/.env) file for the eShopOnContainers application.</span></span>

```
# .env file

ESHOP_EXTERNAL_DNS_NAME_OR_IP=localhost

ESHOP_PROD_EXTERNAL_DNS_NAME_OR_IP=10.121.122.92
```

<span data-ttu-id="2c576-225">Docker compose očekává každý řádek v souboru .env být ve formátu &lt;proměnná&gt;=&lt;hodnotu&gt;.</span><span class="sxs-lookup"><span data-stu-id="2c576-225">Docker-compose expects each line in an .env file to be in the format &lt;variable&gt;=&lt;value&gt;.</span></span>

<span data-ttu-id="2c576-226">Všimněte si, že s hodnotami nastavenými v běhové prostředí vždy přepsat hodnoty definované v souboru .env.</span><span class="sxs-lookup"><span data-stu-id="2c576-226">Note that the values set in the runtime environment always override the values defined inside the .env file.</span></span> <span data-ttu-id="2c576-227">Podobným způsobem hodnoty předány prostřednictvím argumenty příkazového řádku příkaz také přepsat výchozí hodnoty v souboru .env.</span><span class="sxs-lookup"><span data-stu-id="2c576-227">In a similar way, values passed via command-line command arguments also override the default values set in the .env file.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="2c576-228">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="2c576-228">Additional resources</span></span>

-   <span data-ttu-id="2c576-229">**Přehled Docker Compose**
    [*https://docs.docker.com/compose/overview/*](https://docs.docker.com/compose/overview/)</span><span class="sxs-lookup"><span data-stu-id="2c576-229">**Overview of Docker Compose**
[*https://docs.docker.com/compose/overview/*](https://docs.docker.com/compose/overview/)</span></span>

-   <span data-ttu-id="2c576-230">**Více souborů vytvářené**
    [*https://docs.docker.com/compose/extends/\#více tvoří soubory*](https://docs.docker.com/compose/extends/#multiple-compose-files)</span><span class="sxs-lookup"><span data-stu-id="2c576-230">**Multiple Compose files**
[*https://docs.docker.com/compose/extends/\#multiple-compose-files*](https://docs.docker.com/compose/extends/#multiple-compose-files)</span></span>

### <a name="building-optimized-aspnet-core-docker-images"></a><span data-ttu-id="2c576-231">Vytváření optimalizované imagí Dockeru jádro ASP.NET</span><span class="sxs-lookup"><span data-stu-id="2c576-231">Building optimized ASP.NET Core Docker images</span></span>

<span data-ttu-id="2c576-232">Pokud zkoumáte Docker a .NET Core na zdroje v síti Internet, zjistíte Dockerfiles, které ukazují zjednodušení vytváření obrazem Docker zkopírováním svůj zdroj do kontejneru.</span><span class="sxs-lookup"><span data-stu-id="2c576-232">If you are exploring Docker and .NET Core on sources on the Internet, you will find Dockerfiles that demonstrate the simplicity of building a Docker image by copying your source into a container.</span></span> <span data-ttu-id="2c576-233">Tyto příklady navrhnout pomocí jednoduchého konfigurace může mít bitovou kopii Docker s prostředím zabalit s aplikací.</span><span class="sxs-lookup"><span data-stu-id="2c576-233">These examples suggest that by using a simple configuration, you can have a Docker image with the environment packaged with your application.</span></span> <span data-ttu-id="2c576-234">Následující příklad ukazuje jednoduchý soubor Docker v této souvislosti.</span><span class="sxs-lookup"><span data-stu-id="2c576-234">The following example shows a simple Dockerfile in this vein.</span></span>

```
FROM microsoft/dotnet

WORKDIR /app

ENV ASPNETCORE_URLS http://+:80

EXPOSE 80

COPY . .

RUN dotnet restore

ENTRYPOINT ["dotnet", "run"]
```

<span data-ttu-id="2c576-235">Soubor Docker takto bude fungovat.</span><span class="sxs-lookup"><span data-stu-id="2c576-235">A Dockerfile like this will work.</span></span> <span data-ttu-id="2c576-236">Můžete však podstatně optimalizovat bitových kopií, zejména vaše produkční Image.</span><span class="sxs-lookup"><span data-stu-id="2c576-236">However, you can substantially optimize your images, especially your production images.</span></span>

<span data-ttu-id="2c576-237">V kontejneru a mikroslužeb modelu jsou neustále spouštění kontejnery.</span><span class="sxs-lookup"><span data-stu-id="2c576-237">In the container and microservices model, you are constantly starting containers.</span></span> <span data-ttu-id="2c576-238">Typické způsob používání kontejnerů nerestartuje kontejner režimu spánku, protože je kontejner na jedno použití.</span><span class="sxs-lookup"><span data-stu-id="2c576-238">The typical way of using containers does not restart a sleeping container, because the container is disposable.</span></span> <span data-ttu-id="2c576-239">Orchestrators (například Docker Swarm, Kubernetes, orchestrátoru DC/OS nebo Azure Service Fabric) jednoduše vytvořit nové instance třídy bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="2c576-239">Orchestrators (like Docker Swarm, Kubernetes, DCOS or Azure Service Fabric) simply create new instances of images.</span></span> <span data-ttu-id="2c576-240">To znamená, že potřebujete optimalizovat předkompilace aplikace, když je vytvořen, proces vytváření instancí bude rychlejší.</span><span class="sxs-lookup"><span data-stu-id="2c576-240">What this means is that you would need to optimize by precompiling the application when it is built so the instantiation process will be faster.</span></span> <span data-ttu-id="2c576-241">Když se spustí kontejneru, mělo by být připraven ke spuštění.</span><span class="sxs-lookup"><span data-stu-id="2c576-241">When the container is started, it should be ready to run.</span></span> <span data-ttu-id="2c576-242">Nesmí obnovit a kompilaci v době běhu, pomocí dotnet obnovení a dotnet vytváření příkazů z dotnet rozhraní příkazového řádku, jak můžete vidět v mnoha příspěvcích na blogu o .NET Core a Docker.</span><span class="sxs-lookup"><span data-stu-id="2c576-242">You should not restore and compile at run time, using dotnet restore and dotnet build commands from the dotnet CLI that, as you see in many blog posts about .NET Core and Docker.</span></span>

<span data-ttu-id="2c576-243">Tým služby rozhraní .NET byla provádění pracovní důležité, aby .NET Core a ASP.NET Core rozhraní optimalizovaný kontejner.</span><span class="sxs-lookup"><span data-stu-id="2c576-243">The .NET team has been doing important work to make .NET Core and ASP.NET Core a container-optimized framework.</span></span> <span data-ttu-id="2c576-244">.NET Core nejen je jednoduché rozhraní s malou paměťovou zátěž; týmu se zaměřuje na výkon při spouštění a vytváří některé optimalizované Docker Image, jako je třeba [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) bitové kopie k dispozici na [úložiště Docker Hub](https://hub.docker.com/r/microsoft/aspnetcore/), oproti běžné [ Microsoft/dotnet](https://hub.docker.com/r/microsoft/dotnet/) nebo [microsoft/nanoserver](https://github.com/dotnet/dotnet-docker/blob/master/1.0/nanoserver/runtime/Dockerfile) bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="2c576-244">Not only is .NET Core a lightweight framework with a small memory footprint; the team has focused on startup performance and produced some optimized Docker images, like the [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) image available at [Docker Hub](https://hub.docker.com/r/microsoft/aspnetcore/), in comparison to the regular [microsoft/dotnet](https://hub.docker.com/r/microsoft/dotnet/) or [microsoft/nanoserver](https://github.com/dotnet/dotnet-docker/blob/master/1.0/nanoserver/runtime/Dockerfile) images.</span></span> <span data-ttu-id="2c576-245">[Microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) image poskytuje automatické nastavení aspnetcore\_adres URL na port 80 a mezipaměti před ngend sestavení; obě nastavení mít za následek rychlejší spuštění.</span><span class="sxs-lookup"><span data-stu-id="2c576-245">The [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) image provides automatic setting of aspnetcore\_urls to port 80 and the pre-ngend cache of assemblies; both of these settings result in faster startup.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="2c576-246">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="2c576-246">Additional resources</span></span>

-   <span data-ttu-id="2c576-247">**Vytváření optimalizované Imagí Dockeru základní technologie ASP.NET**
    [*https://blogs.msdn.microsoft.com/stevelasker/2016/09/29/building-optimized-docker-images-with-asp-net-core/*](https://blogs.msdn.microsoft.com/stevelasker/2016/09/29/building-optimized-docker-images-with-asp-net-core/)</span><span class="sxs-lookup"><span data-stu-id="2c576-247">**Building Optimized Docker Images with ASP.NET Core**
[*https://blogs.msdn.microsoft.com/stevelasker/2016/09/29/building-optimized-docker-images-with-asp-net-core/*](https://blogs.msdn.microsoft.com/stevelasker/2016/09/29/building-optimized-docker-images-with-asp-net-core/)</span></span>

### <a name="building-the-application-from-a-build-ci-container"></a><span data-ttu-id="2c576-248">Vytvoření aplikace z kontejneru sestavení (CI)</span><span class="sxs-lookup"><span data-stu-id="2c576-248">Building the application from a build (CI) container</span></span>

<span data-ttu-id="2c576-249">Další výhodou Docker je, že můžete vytvořit aplikaci z předkonfigurovaných kontejneru, jak ukazuje obrázek 8-13 proto není nutné k vytvoření sestavení počítače nebo virtuálního počítače k sestavení aplikace.</span><span class="sxs-lookup"><span data-stu-id="2c576-249">Another benefit of Docker is that you can build your application from a preconfigured container, as shown in Figure 8-13, so you do not need to create a build machine or VM to build your application.</span></span> <span data-ttu-id="2c576-250">Můžete použít, nebo tento kontejner sestavení testů spuštěním na vývojovém počítači.</span><span class="sxs-lookup"><span data-stu-id="2c576-250">You can use or test that build container by running it at your development machine.</span></span> <span data-ttu-id="2c576-251">Ale co je ještě více zajímavé, které můžete použít stejný kontejner sestavení z vašeho kanálu CI (nepřetržité integrace).</span><span class="sxs-lookup"><span data-stu-id="2c576-251">But what is even more interesting is that you can use the same build container from your CI (Continuous Integration) pipeline.</span></span>

![](./media/image14.png)

<span data-ttu-id="2c576-252">**Obrázek 8-13**.</span><span class="sxs-lookup"><span data-stu-id="2c576-252">**Figure 8-13**.</span></span> <span data-ttu-id="2c576-253">Sestavení – kontejner docker kompilování vaší binární soubory rozhraní .NET</span><span class="sxs-lookup"><span data-stu-id="2c576-253">Docker build-container compiling your .NET binaries</span></span> 

<span data-ttu-id="2c576-254">V tomto scénáři poskytujeme [microsoft/aspnetcore sestavení](https://hub.docker.com/r/microsoft/aspnetcore-build/) bitovou kopii, kterou můžete použít pro zkompilování a vybuildování aplikace ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="2c576-254">For this scenario, we provide the [microsoft/aspnetcore-build](https://hub.docker.com/r/microsoft/aspnetcore-build/) image, which you can use to compile and build your ASP.NET Core apps.</span></span> <span data-ttu-id="2c576-255">V obrázku na základě se umístí výstup [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) bitovou kopii, kterou je obrázek optimalizované runtime, jako v předchozí části.</span><span class="sxs-lookup"><span data-stu-id="2c576-255">The output is placed in an image based on the [microsoft/aspnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) image, which is an optimized runtime image, as previously noted.</span></span>

<span data-ttu-id="2c576-256">Bitová kopie aspnetcore sestavení obsahuje všechno, co potřebujete, aby bylo možné kompilaci aplikace ASP.NET Core, včetně .NET Core, sady SDK technologie ASP.NET, npm, Bower, Gulp, atd.</span><span class="sxs-lookup"><span data-stu-id="2c576-256">The aspnetcore-build image contains everything you need in order to compile an ASP.NET Core application, including .NET Core, the ASP.NET SDK, npm, Bower, Gulp, etc.</span></span>

<span data-ttu-id="2c576-257">Potřebujeme tyto závislosti v čase vytvoření buildu.</span><span class="sxs-lookup"><span data-stu-id="2c576-257">We need these dependencies at build time.</span></span> <span data-ttu-id="2c576-258">Ale jsme nechcete, aby k provedení těchto aplikací za běhu, protože by byla bitovou kopii zbytečně velké.</span><span class="sxs-lookup"><span data-stu-id="2c576-258">But we do not want to carry these with the application at runtime, because it would make the image unnecessarily large.</span></span> <span data-ttu-id="2c576-259">V aplikaci eShopOnContainers, můžete vytvořit aplikaci z kontejneru právě spuštěním následující docker napište příkaz.</span><span class="sxs-lookup"><span data-stu-id="2c576-259">In the eShopOnContainers application, you can build the application from a container by just running the following docker-compose command.</span></span>

```
  docker-compose -f docker-compose.ci.build.yml up
```

<span data-ttu-id="2c576-260">Obrázek 8-14 ukazuje tento příkaz není spuštěn v příkazovém řádku.</span><span class="sxs-lookup"><span data-stu-id="2c576-260">Figure 8-14 shows this command running at the command line.</span></span>

![](./media/image15.png)

<span data-ttu-id="2c576-261">**Obrázek 8-14.**</span><span class="sxs-lookup"><span data-stu-id="2c576-261">**Figure 8-14.**</span></span> <span data-ttu-id="2c576-262">Vytváření aplikace .NET z kontejneru</span><span class="sxs-lookup"><span data-stu-id="2c576-262">Building your .NET application from a container</span></span>

<span data-ttu-id="2c576-263">Jak můžete vidět, je kontejner, který běží ci sestavení\_1 kontejneru.</span><span class="sxs-lookup"><span data-stu-id="2c576-263">As you can see, the container that is running is the ci-build\_1 container.</span></span> <span data-ttu-id="2c576-264">To je založené na bitovou kopii aspnetcore sestavení tak, aby můžete zkompilovat a sestavit celou aplikaci z tohoto kontejneru, místo z vašeho počítače.</span><span class="sxs-lookup"><span data-stu-id="2c576-264">This is based on the aspnetcore-build image so that it can compile and build your whole application from within that container instead of from your PC.</span></span> <span data-ttu-id="2c576-265">To znamená Proč ve skutečnosti je vytváření a kompilování .NET Core projekty v systému Linux, protože tento kontejner běží na hostiteli systému Linux Docker výchozí.</span><span class="sxs-lookup"><span data-stu-id="2c576-265">That is why in reality it is building and compiling the .NET Core projects in Linux—because that container is running on the default Docker Linux host.</span></span>

<span data-ttu-id="2c576-266">[Docker compose.ci.build.yml](https://github.com/dotnet/eShopOnContainers/blob/master/docker-compose.ci.build.yml) soubor pro této bitové kopie (součást eShopOnContainers) obsahuje následující kód.</span><span class="sxs-lookup"><span data-stu-id="2c576-266">The [docker-compose.ci.build.yml](https://github.com/dotnet/eShopOnContainers/blob/master/docker-compose.ci.build.yml) file for that image (part of eShopOnContainers) contains the following code.</span></span> <span data-ttu-id="2c576-267">Uvidíte, že začne kontejneru sestavení pomocí [microsoft/aspnetcore sestavení](https://hub.docker.com/r/microsoft/aspnetcore-build/) bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="2c576-267">You can see that it starts a build container using the [microsoft/aspnetcore-build](https://hub.docker.com/r/microsoft/aspnetcore-build/) image.</span></span>

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

* <span data-ttu-id="2c576-268">Počínaje **.NET Core 2.0**, `dotnet restore` příkaz provede automaticky při `dotnet publish` se spustí příkaz.</span><span class="sxs-lookup"><span data-stu-id="2c576-268">Starting with **.NET Core 2.0**, `dotnet restore` command executes automatically when the `dotnet publish` command is executed.</span></span>

<span data-ttu-id="2c576-269">Jakmile kontejneru sestavení spuštěná, spuštění obnovení dotnet .NET SDK a dotnet. publikování příkazy na všechny projekty v řešení pro kompilaci rozhraní .NET bits.</span><span class="sxs-lookup"><span data-stu-id="2c576-269">Once the build container is up and running, it runs the .NET SDK dotnet restore and dotnet publish commands against all the projects in the solution in order to compile the .NET bits.</span></span> <span data-ttu-id="2c576-270">V takovém případě eShopOnContainers obsahuje také SPA podle TypeScript a úhlová pro kód klienta, a proto ho také musí zkontrolovat závislosti jazyka JavaScript pomocí npm, ale tato akce není v relaci s .NET bits.</span><span class="sxs-lookup"><span data-stu-id="2c576-270">In this case, because eShopOnContainers also has an SPA based on TypeScript and Angular for the client code, it also needs to check JavaScript dependencies with npm, but that action is not related to the .NET bits.</span></span>

<span data-ttu-id="2c576-271">Dotnet publikování příkaz sestavení a publikuje kompilovaný výstup ve složce každý projekt na... Složka /obj/Docker/Publish, jak ukazuje obrázek 8 až 15.</span><span class="sxs-lookup"><span data-stu-id="2c576-271">The dotnet publish command builds and publishes the compiled output within each project’s folder to the ../obj/Docker/publish folder, as shown in Figure 8-15.</span></span>

![](./media/image16.png)

<span data-ttu-id="2c576-272">**Obrázek 8 až 15.**</span><span class="sxs-lookup"><span data-stu-id="2c576-272">**Figure 8-15.**</span></span> <span data-ttu-id="2c576-273">Příkaz Publikovat binární soubory, které jsou generované dotnet.</span><span class="sxs-lookup"><span data-stu-id="2c576-273">Binary files generated by the dotnet publish command</span></span>

#### <a name="creating-the-docker-images-from-the-cli"></a><span data-ttu-id="2c576-274">Vytvoření imagí Dockeru z rozhraní příkazového řádku</span><span class="sxs-lookup"><span data-stu-id="2c576-274">Creating the Docker images from the CLI</span></span>

<span data-ttu-id="2c576-275">Jakmile výstupu aplikace publikována do související složek (v rámci každého projektu), dalším krokem je ve skutečnosti vytvoření imagí Dockeru.</span><span class="sxs-lookup"><span data-stu-id="2c576-275">Once the application output is published to the related folders (within each project), the next step is to actually build the Docker images.</span></span> <span data-ttu-id="2c576-276">K tomuto účelu použijete docker-compose sestavení a docker tvoří příkazy, jak ukazuje obrázek 8-16.</span><span class="sxs-lookup"><span data-stu-id="2c576-276">To do this, you use the docker-compose build and docker-compose up commands, as shown in Figure 8-16.</span></span>

![](./media/image17.png)

<span data-ttu-id="2c576-277">**Obrázek 8-16.**</span><span class="sxs-lookup"><span data-stu-id="2c576-277">**Figure 8-16.**</span></span> <span data-ttu-id="2c576-278">Vytváření imagí Dockeru a spouštění kontejnerů.</span><span class="sxs-lookup"><span data-stu-id="2c576-278">Building Docker images and running the containers</span></span>

<span data-ttu-id="2c576-279">Obrázek 8-17 můžete zobrazit, jak docker-compose vytvářet příkaz spustí.</span><span class="sxs-lookup"><span data-stu-id="2c576-279">In Figure 8-17, you can see how the docker-compose build command runs.</span></span>

![](./media/image18.png)

<span data-ttu-id="2c576-280">**Obrázek 8-17**.</span><span class="sxs-lookup"><span data-stu-id="2c576-280">**Figure 8-17**.</span></span> <span data-ttu-id="2c576-281">Vytváření bitových kopií Docker pomocí docker-napište příkaz sestavení</span><span class="sxs-lookup"><span data-stu-id="2c576-281">Building the Docker images with the docker-compose build command</span></span>

<span data-ttu-id="2c576-282">Rozdíl mezi docker-compose sestavení a docker compose až příkazy je, že docker compose sestavení a spuštění bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="2c576-282">The difference between the docker-compose build and docker-compose up commands is that docker-compose up both builds and starts the images.</span></span>

<span data-ttu-id="2c576-283">Pokud používáte Visual Studio, jsou všechny tyto kroky provést v pozadí.</span><span class="sxs-lookup"><span data-stu-id="2c576-283">When you use Visual Studio, all these steps are performed under the covers.</span></span> <span data-ttu-id="2c576-284">Visual Studio zkompiluje aplikace .NET, vytvoří imagí Dockeru a nasadí do hostitelů Docker kontejnerů.</span><span class="sxs-lookup"><span data-stu-id="2c576-284">Visual Studio compiles your .NET application, creates the Docker images, and deploys the containers into the Docker host.</span></span> <span data-ttu-id="2c576-285">Visual Studio nabízí další funkce, jako možnost ladění kontejnerů spuštěna v Docker, přímo ze sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="2c576-285">Visual Studio offers additional features, like the ability to debug your containers running in Docker, directly from Visual Studio.</span></span>

<span data-ttu-id="2c576-286">Celkové takeway tady je, že budete moci sestavit aplikaci stejné svůj CI/CD kanál má sestavit způsobem ho – z kontejneru místo z místního počítače.</span><span class="sxs-lookup"><span data-stu-id="2c576-286">The overall takeway here is that you are able to build your application the same way your CI/CD pipeline should build it—from a container instead of from a local machine.</span></span> <span data-ttu-id="2c576-287">Po s bitové kopie vytvořené, pak stačí ke spuštění imagí Dockeru pomocí docker-tvoří až příkaz.</span><span class="sxs-lookup"><span data-stu-id="2c576-287">After having the images created, then you just need to run the Docker images using the docker-compose up command.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="2c576-288">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="2c576-288">Additional resources</span></span>

-   <span data-ttu-id="2c576-289">**Vytváření bits z kontejneru: nastavení řešení eShopOnContainers v prostředí Windows rozhraní příkazového řádku (dotnet příkazového řádku Dockeru a VS Code rozhraní příkazového řádku,)**
    [*https://github.com/dotnet/eShopOnContainers/wiki/03.-Setting-the-eShopOnContainers-solution-up-in-a-Windows-CLI-environment-(dotnet-CLI, - Docker - rozhraní příkazového řádku- a -VS-kódu)*](https://github.com/dotnet/eShopOnContainers/wiki/03.-Setting-the-eShopOnContainers-solution-up-in-a-Windows-CLI-environment-(dotnet-CLI,-Docker-CLI-and-VS-Code))</span><span class="sxs-lookup"><span data-stu-id="2c576-289">**Building bits from a container: Setting the eShopOnContainers solution up in a Windows CLI environment (dotnet CLI, Docker CLI and VS Code)**
[*https://github.com/dotnet/eShopOnContainers/wiki/03.-Setting-the-eShopOnContainers-solution-up-in-a-Windows-CLI-environment-(dotnet-CLI,-Docker-CLI-and-VS-Code)*](https://github.com/dotnet/eShopOnContainers/wiki/03.-Setting-the-eShopOnContainers-solution-up-in-a-Windows-CLI-environment-(dotnet-CLI,-Docker-CLI-and-VS-Code))</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="2c576-290">[Předchozí] (data řízené crud-microservice.md) [Další] (container.md databáze serveru)</span><span class="sxs-lookup"><span data-stu-id="2c576-290">[Previous] (data-driven-crud-microservice.md) [Next] (database-server-container.md)</span></span>
