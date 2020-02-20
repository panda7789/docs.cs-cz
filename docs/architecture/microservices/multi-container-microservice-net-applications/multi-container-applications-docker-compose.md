---
title: Definování vícekontejnerové aplikace pomocí docker-compose.yml
description: Jak určit složení mikroslužeb pro aplikaci s více kontejnery pomocí Docker-Compose. yml.
ms.date: 01/30/2020
ms.openlocfilehash: 86d6feda343df7f4b72374f93fc45b3246780cdf
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/20/2020
ms.locfileid: "77502455"
---
# <a name="defining-your-multi-container-application-with-docker-composeyml"></a><span data-ttu-id="63acd-103">Definování vícekontejnerové aplikace pomocí docker-compose.yml</span><span class="sxs-lookup"><span data-stu-id="63acd-103">Defining your multi-container application with docker-compose.yml</span></span>

<span data-ttu-id="63acd-104">V tomto průvodci byl soubor [Docker-Compose. yml](https://docs.docker.com/compose/compose-file/) představený v části [Krok 4. V Docker-Compose. yml definujte své služby při sestavování aplikace Docker pro více kontejnerů](../docker-application-development-process/docker-app-development-workflow.md#step-4-define-your-services-in-docker-composeyml-when-building-a-multi-container-docker-application).</span><span class="sxs-lookup"><span data-stu-id="63acd-104">In this guide, the [docker-compose.yml](https://docs.docker.com/compose/compose-file/) file was introduced in the section [Step 4. Define your services in docker-compose.yml when building a multi-container Docker application](../docker-application-development-process/docker-app-development-workflow.md#step-4-define-your-services-in-docker-composeyml-when-building-a-multi-container-docker-application).</span></span> <span data-ttu-id="63acd-105">Existují však další způsoby, jak použít soubory Docker – skládání, které jsou podrobněji prozkoumání.</span><span class="sxs-lookup"><span data-stu-id="63acd-105">However, there are additional ways to use the docker-compose files that are worth exploring in further detail.</span></span>

<span data-ttu-id="63acd-106">Můžete například explicitně popsat, jak chcete v souboru Docker-Compose. yml nasadit aplikaci s více kontejnery.</span><span class="sxs-lookup"><span data-stu-id="63acd-106">For example, you can explicitly describe how you want to deploy your multi-container application in the docker-compose.yml file.</span></span> <span data-ttu-id="63acd-107">Volitelně můžete také popsat, jak budete vytvářet vlastní image Docker.</span><span class="sxs-lookup"><span data-stu-id="63acd-107">Optionally, you can also describe how you are going to build your custom Docker images.</span></span> <span data-ttu-id="63acd-108">(Vlastní image Docker můžete také vytvořit pomocí Docker CLI.)</span><span class="sxs-lookup"><span data-stu-id="63acd-108">(Custom Docker images can also be built with the Docker CLI.)</span></span>

<span data-ttu-id="63acd-109">V podstatě definujete každý z kontejnerů, které chcete nasadit, a některé vlastnosti pro každé nasazení kontejneru.</span><span class="sxs-lookup"><span data-stu-id="63acd-109">Basically, you define each of the containers you want to deploy plus certain characteristics for each container deployment.</span></span> <span data-ttu-id="63acd-110">Jakmile budete mít soubor s popisem nasazení s více kontejnery, můžete nasadit celé řešení v rámci jedné akce Orchestrované příkazem [Docker-sestavit](https://docs.docker.com/compose/overview/) rozhraní příkazového řádku nebo ho můžete transparentně nasadit ze sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="63acd-110">Once you have a multi-container deployment description file, you can deploy the whole solution in a single action orchestrated by the [docker-compose up](https://docs.docker.com/compose/overview/) CLI command, or you can deploy it transparently from Visual Studio.</span></span> <span data-ttu-id="63acd-111">V opačném případě byste k nasazení kontejnerů do kontejneru do více kroků použili příkaz Docker CLI pomocí příkazu `docker run` z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="63acd-111">Otherwise, you would need to use the Docker CLI to deploy container-by-container in multiple steps by using the `docker run` command from the command line.</span></span> <span data-ttu-id="63acd-112">Proto každá služba definovaná v Docker-Compose. yml musí určovat přesně jeden obrázek nebo sestavení.</span><span class="sxs-lookup"><span data-stu-id="63acd-112">Therefore, each service defined in docker-compose.yml must specify exactly one image or build.</span></span> <span data-ttu-id="63acd-113">Další klíče jsou volitelné a jsou podobné jejich `docker run` protějškům příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="63acd-113">Other keys are optional, and are analogous to their `docker run` command-line counterparts.</span></span>

<span data-ttu-id="63acd-114">Následující kód YAML je definicí možného souboru Global, ale Single Docker-Compose. yml pro ukázku eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="63acd-114">The following YAML code is the definition of a possible global but single docker-compose.yml file for the eShopOnContainers sample.</span></span> <span data-ttu-id="63acd-115">Nejedná se o skutečný soubor Docker-skládání z eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="63acd-115">This is not the actual docker-compose file from eShopOnContainers.</span></span> <span data-ttu-id="63acd-116">Místo toho je tato zjednodušená a konsolidovaná verze v jednom souboru, což není nejlepším způsobem, jak pracovat se soubory Docker-pro vytváření, jak bude vysvětleno později.</span><span class="sxs-lookup"><span data-stu-id="63acd-116">Instead, it is a simplified and consolidated version in a single file, which is not the best way to work with docker-compose files, as will be explained later.</span></span>

```yml
version: '3.4'

services:
  webmvc:
    image: eshop/webmvc
    environment:
      - CatalogUrl=http://catalog-api
      - OrderingUrl=http://ordering-api
      - BasketUrl=http://basket-api
    ports:
      - "5100:80"
    depends_on:
      - catalog-api
      - ordering-api
      - basket-api

  catalog-api:
    image: eshop/catalog-api
    environment:
      - ConnectionString=Server=sqldata;Initial Catalog=CatalogData;User Id=sa;Password=your@password
    expose:
      - "80"
    ports:
      - "5101:80"
    #extra hosts can be used for standalone SQL Server or services at the dev PC
    extra_hosts:
      - "CESARDLSURFBOOK:10.0.75.1"
    depends_on:
      - sqldata

  ordering-api:
    image: eshop/ordering-api
    environment:
      - ConnectionString=Server=sqldata;Database=Services.OrderingDb;User Id=sa;Password=your@password
    ports:
      - "5102:80"
    #extra hosts can be used for standalone SQL Server or services at the dev PC
    extra_hosts:
      - "CESARDLSURFBOOK:10.0.75.1"
    depends_on:
      - sqldata

  basket-api:
    image: eshop/basket-api
    environment:
      - ConnectionString=sqldata
    ports:
      - "5103:80"
    depends_on:
      - sqldata

  sqldata:
    environment:
      - SA_PASSWORD=your@password
      - ACCEPT_EULA=Y
    ports:
      - "5434:1433"

  basketdata:
    image: redis
```

<span data-ttu-id="63acd-117">Kořenový klíč v tomto souboru je služby.</span><span class="sxs-lookup"><span data-stu-id="63acd-117">The root key in this file is services.</span></span> <span data-ttu-id="63acd-118">V tomto klíči definujete služby, které chcete nasadit a spustit při spuštění příkazu `docker-compose up`, nebo při nasazení ze sady Visual Studio pomocí tohoto souboru Docker-Compose. yml.</span><span class="sxs-lookup"><span data-stu-id="63acd-118">Under that key, you define the services you want to deploy and run when you execute the `docker-compose up` command or when you deploy from Visual Studio by using this docker-compose.yml file.</span></span> <span data-ttu-id="63acd-119">V tomto případě má soubor Docker-Compose. yml definováno více služeb, jak je popsáno v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="63acd-119">In this case, the docker-compose.yml file has multiple services defined, as described in the following table.</span></span>

| <span data-ttu-id="63acd-120">Název služby</span><span class="sxs-lookup"><span data-stu-id="63acd-120">Service name</span></span> | <span data-ttu-id="63acd-121">Popis</span><span class="sxs-lookup"><span data-stu-id="63acd-121">Description</span></span> |
|--------------|-------------|
| <span data-ttu-id="63acd-122">webmvc</span><span class="sxs-lookup"><span data-stu-id="63acd-122">webmvc</span></span>       | <span data-ttu-id="63acd-123">Kontejner včetně aplikace ASP.NET Core MVC využívající mikroslužby na straně serveru C\#</span><span class="sxs-lookup"><span data-stu-id="63acd-123">Container including the ASP.NET Core MVC application consuming the microservices from server-side C\#</span></span>|
| <span data-ttu-id="63acd-124">katalog – rozhraní API</span><span class="sxs-lookup"><span data-stu-id="63acd-124">catalog-api</span></span>  | <span data-ttu-id="63acd-125">Kontejner včetně služby Catalog ASP.NET Core mikroslužby webového rozhraní API</span><span class="sxs-lookup"><span data-stu-id="63acd-125">Container including the Catalog ASP.NET Core Web API microservice</span></span> |
| <span data-ttu-id="63acd-126">řazení – rozhraní API</span><span class="sxs-lookup"><span data-stu-id="63acd-126">ordering-api</span></span> | <span data-ttu-id="63acd-127">Kontejner, včetně pořadí ASP.NET Core mikroslužby webového rozhraní API</span><span class="sxs-lookup"><span data-stu-id="63acd-127">Container including the Ordering ASP.NET Core Web API microservice</span></span> |
| <span data-ttu-id="63acd-128">sqldata</span><span class="sxs-lookup"><span data-stu-id="63acd-128">sqldata</span></span>     | <span data-ttu-id="63acd-129">Kontejner se spuštěným SQL Server pro Linux, který uchovává databáze mikroslužeb.</span><span class="sxs-lookup"><span data-stu-id="63acd-129">Container running SQL Server for Linux, holding the microservices databases</span></span> |
| <span data-ttu-id="63acd-130">košík – rozhraní API</span><span class="sxs-lookup"><span data-stu-id="63acd-130">basket-api</span></span>   | <span data-ttu-id="63acd-131">Kontejner s ASP.NET Core mikroslužba webového rozhraní API pro koš</span><span class="sxs-lookup"><span data-stu-id="63acd-131">Container with the Basket ASP.NET Core Web API microservice</span></span> |
| <span data-ttu-id="63acd-132">basketdata</span><span class="sxs-lookup"><span data-stu-id="63acd-132">basketdata</span></span>  | <span data-ttu-id="63acd-133">Kontejner, ve kterém je spuštěná služba REDIS cache, s databází košíku jako REDIS cache</span><span class="sxs-lookup"><span data-stu-id="63acd-133">Container running the REDIS cache service, with the basket database as a REDIS cache</span></span> |

### <a name="a-simple-web-service-api-container"></a><span data-ttu-id="63acd-134">Jednoduchý kontejner rozhraní API pro webové služby</span><span class="sxs-lookup"><span data-stu-id="63acd-134">A simple Web Service API container</span></span>

<span data-ttu-id="63acd-135">Zaostření na jednom kontejneru, katalogu rozhraní API – mikroslužba má jasné definice:</span><span class="sxs-lookup"><span data-stu-id="63acd-135">Focusing on a single container, the catalog-api container-microservice has a straightforward definition:</span></span>

```yml
  catalog-api:
    image: eshop/catalog-api
    environment:
      - ConnectionString=Server=sqldata;Initial Catalog=CatalogData;User Id=sa;Password=your@password
    expose:
      - "80"
    ports:
      - "5101:80"
    #extra hosts can be used for standalone SQL Server or services at the dev PC
    extra_hosts:
      - "CESARDLSURFBOOK:10.0.75.1"
    depends_on:
      - sqldata
```

<span data-ttu-id="63acd-136">Tato služba kontejneru má následující základní konfiguraci:</span><span class="sxs-lookup"><span data-stu-id="63acd-136">This containerized service has the following basic configuration:</span></span>

- <span data-ttu-id="63acd-137">Je založen na vlastní imagi **eshop/Catalog-API** .</span><span class="sxs-lookup"><span data-stu-id="63acd-137">It is based on the custom **eshop/catalog-api** image.</span></span> <span data-ttu-id="63acd-138">V zájmu zjednodušení není v souboru žádné nastavení pro sestavení: klíče.</span><span class="sxs-lookup"><span data-stu-id="63acd-138">For simplicity’s sake, there is no build: key setting in the file.</span></span> <span data-ttu-id="63acd-139">To znamená, že bitová kopie musí být dřív sestavená (pomocí buildu Docker) nebo se stáhla (pomocí příkazu docker pull) z libovolného registru Docker.</span><span class="sxs-lookup"><span data-stu-id="63acd-139">This means that the image must have been previously built (with docker build) or have been downloaded (with the docker pull command) from any Docker registry.</span></span>

- <span data-ttu-id="63acd-140">Definuje proměnnou prostředí s názvem ConnectionString s připojovacím řetězcem, který má být použit Entity Framework pro přístup k instanci SQL Server, která obsahuje model dat katalogu.</span><span class="sxs-lookup"><span data-stu-id="63acd-140">It defines an environment variable named ConnectionString with the connection string to be used by Entity Framework to access the SQL Server instance that contains the catalog data model.</span></span> <span data-ttu-id="63acd-141">V takovém případě stejný kontejner SQL Server drží více databází.</span><span class="sxs-lookup"><span data-stu-id="63acd-141">In this case, the same SQL Server container is holding multiple databases.</span></span> <span data-ttu-id="63acd-142">Proto potřebujete na svém vývojovém počítači méně paměti pro Docker.</span><span class="sxs-lookup"><span data-stu-id="63acd-142">Therefore, you need less memory in your development machine for Docker.</span></span> <span data-ttu-id="63acd-143">Můžete ale také nasadit jeden kontejner SQL Server pro každou databázi mikroslužeb.</span><span class="sxs-lookup"><span data-stu-id="63acd-143">However, you could also deploy one SQL Server container for each microservice database.</span></span>

- <span data-ttu-id="63acd-144">Název SQL Server je **Sqldata**, což je stejný název, který se používá pro kontejner, na kterém je spuštěná instance SQL Server pro Linux.</span><span class="sxs-lookup"><span data-stu-id="63acd-144">The SQL Server name is **sqldata**, which is the same name used for the container that is running the SQL Server instance for Linux.</span></span> <span data-ttu-id="63acd-145">To je pohodlné; možnost použít toto rozlišení názvu (interní pro hostitele Docker) vyřeší síťovou adresu, takže nemusíte znát interní IP adresy pro kontejnery, které přistupujete z jiných kontejnerů.</span><span class="sxs-lookup"><span data-stu-id="63acd-145">This is convenient; being able to use this name resolution (internal to the Docker host) will resolve the network address so you don’t need to know the internal IP for the containers you are accessing from other containers.</span></span>

<span data-ttu-id="63acd-146">Vzhledem k tomu, že připojovací řetězec je definován proměnnou prostředí, můžete tuto proměnnou nastavit pomocí jiného mechanismu a v jinou dobu.</span><span class="sxs-lookup"><span data-stu-id="63acd-146">Because the connection string is defined by an environment variable, you could set that variable through a different mechanism and at a different time.</span></span> <span data-ttu-id="63acd-147">Můžete například nastavit jiný připojovací řetězec při nasazování do produkčního prostředí v konečných hostitelích nebo z vašich kanálů CI/CD v Azure DevOps Services nebo preferovaného systému DevOps.</span><span class="sxs-lookup"><span data-stu-id="63acd-147">For example, you could set a different connection string when deploying to production in the final hosts, or by doing it from your CI/CD pipelines in Azure DevOps Services or your preferred DevOps system.</span></span>

- <span data-ttu-id="63acd-148">Zpřístupňuje port 80 pro interní přístup ke službě **Catalog-API** v rámci hostitele Docker.</span><span class="sxs-lookup"><span data-stu-id="63acd-148">It exposes port 80 for internal access to the **catalog-api** service within the Docker host.</span></span> <span data-ttu-id="63acd-149">Hostitelem je aktuálně virtuální počítač se systémem Linux, protože je založen na imagi Docker pro Linux, ale můžete nastavit, aby se kontejner spouštěl v imagi Windows.</span><span class="sxs-lookup"><span data-stu-id="63acd-149">The host is currently a Linux VM because it is based on a Docker image for Linux, but you could configure the container to run on a Windows image instead.</span></span>

- <span data-ttu-id="63acd-150">Přepošle vystavený port 80 na kontejner na port 5101 na hostitelském počítači Docker (virtuální počítač Linux).</span><span class="sxs-lookup"><span data-stu-id="63acd-150">It forwards the exposed port 80 on the container to port 5101 on the Docker host machine (the Linux VM).</span></span>

- <span data-ttu-id="63acd-151">Odkazuje na webovou službu na službu **Sqldata** (instance SQL Server pro databázi Linux spuštěnou v kontejneru).</span><span class="sxs-lookup"><span data-stu-id="63acd-151">It links the web service to the **sqldata** service (the SQL Server instance for Linux database running in a container).</span></span> <span data-ttu-id="63acd-152">Když zadáte tuto závislost, kontejner API Catalog se nespustí, dokud se kontejner Sqldata už nespustil. To je důležité, protože Catalog-API vyžaduje, aby se nejdřív nastavila a běžela databáze SQL Server.</span><span class="sxs-lookup"><span data-stu-id="63acd-152">When you specify this dependency, the catalog-api container will not start until the sqldata container has already started; this is important because catalog-api needs to have the SQL Server database up and running first.</span></span> <span data-ttu-id="63acd-153">Tento druh závislosti kontejneru ale v mnoha případech není dostatečný, protože kontroly Docker jsou jenom na úrovni kontejneru.</span><span class="sxs-lookup"><span data-stu-id="63acd-153">However, this kind of container dependency is not enough in many cases, because Docker checks only at the container level.</span></span> <span data-ttu-id="63acd-154">Někdy může být služba (v tomto případě SQL Server) stále připravená, takže je vhodné implementovat logiku opakování pomocí exponenciálního omezení rychlostiu v klientských mikroslužbách.</span><span class="sxs-lookup"><span data-stu-id="63acd-154">Sometimes the service (in this case SQL Server) might still not be ready, so it is advisable to implement retry logic with exponential backoff in your client microservices.</span></span> <span data-ttu-id="63acd-155">To znamená, že pokud kontejner závislostí není připravený na krátkou dobu, bude aplikace stále odolná.</span><span class="sxs-lookup"><span data-stu-id="63acd-155">That way, if a dependency container is not ready for a short time, the application will still be resilient.</span></span>

- <span data-ttu-id="63acd-156">Je nakonfigurovaná tak, aby povolovala přístup k externím serverům: nastavení další\_hostitelů umožňuje přístup k externím serverům nebo počítačům mimo hostitele Docker (to znamená, že je mimo výchozí virtuální počítač Linux, který je hostitelem hostitele Docker), jako je například místní instance SQL Server na vašem vývojovém počítači.</span><span class="sxs-lookup"><span data-stu-id="63acd-156">It is configured to allow access to external servers: the extra\_hosts setting allows you to access external servers or machines outside of the Docker host (that is, outside the default Linux VM, which is a development Docker host), such as a local SQL Server instance on your development PC.</span></span>

<span data-ttu-id="63acd-157">K dispozici jsou také další pokročilejší `docker-compose.yml`á nastavení, která budeme projednávat v následujících částech.</span><span class="sxs-lookup"><span data-stu-id="63acd-157">There are also other, more advanced `docker-compose.yml` settings that we'll discuss in the following sections.</span></span>

### <a name="using-docker-compose-files-to-target-multiple-environments"></a><span data-ttu-id="63acd-158">Použití souborů Docker-skládání k sestavení více prostředí</span><span class="sxs-lookup"><span data-stu-id="63acd-158">Using docker-compose files to target multiple environments</span></span>

<span data-ttu-id="63acd-159">`docker-compose.*.yml` soubory jsou definiční soubory a mohou být používány více infrastrukturami, které tento formát porozuměl.</span><span class="sxs-lookup"><span data-stu-id="63acd-159">The `docker-compose.*.yml` files are definition files and can be used by multiple infrastructures that understand that format.</span></span> <span data-ttu-id="63acd-160">Nejpřímější nástroj je příkaz Docker-skládání.</span><span class="sxs-lookup"><span data-stu-id="63acd-160">The most straightforward tool is the docker-compose command.</span></span>

<span data-ttu-id="63acd-161">Proto pomocí příkazu Docker-skládání můžete cílit na následující hlavní scénáře.</span><span class="sxs-lookup"><span data-stu-id="63acd-161">Therefore, by using the docker-compose command you can target the following main scenarios.</span></span>

#### <a name="development-environments"></a><span data-ttu-id="63acd-162">Vývojová prostředí</span><span class="sxs-lookup"><span data-stu-id="63acd-162">Development environments</span></span>

<span data-ttu-id="63acd-163">Při vývoji aplikací je důležité, aby bylo možné spustit aplikaci v izolovaném vývojovém prostředí.</span><span class="sxs-lookup"><span data-stu-id="63acd-163">When you develop applications, it is important to be able to run an application in an isolated development environment.</span></span> <span data-ttu-id="63acd-164">K vytvoření prostředí nebo sady Visual Studio, které používá Docker-skládání v rámci pokrývání, můžete použít příkaz Docker-Create CLI.</span><span class="sxs-lookup"><span data-stu-id="63acd-164">You can use the docker-compose CLI command to create that environment or Visual Studio, which uses docker-compose under the covers.</span></span>

<span data-ttu-id="63acd-165">Soubor Docker-Compose. yml umožňuje konfigurovat a zdokumentovat všechny závislosti služby vaší aplikace (další služby, mezipaměť, databáze, fronty atd.).</span><span class="sxs-lookup"><span data-stu-id="63acd-165">The docker-compose.yml file allows you to configure and document all your application’s service dependencies (other services, cache, databases, queues, etc.).</span></span> <span data-ttu-id="63acd-166">Pomocí příkazu Docker-Create CLI můžete vytvořit a spustit jeden nebo více kontejnerů pro každou závislost jediným příkazem (Docker – sestavit).</span><span class="sxs-lookup"><span data-stu-id="63acd-166">Using the docker-compose CLI command, you can create and start one or more containers for each dependency with a single command (docker-compose up).</span></span>

<span data-ttu-id="63acd-167">Soubory Docker-Compose. yml jsou konfigurační soubory interpretované modulem Docker, ale také slouží jako praktické dokumentační soubory o složení aplikace s více kontejnery.</span><span class="sxs-lookup"><span data-stu-id="63acd-167">The docker-compose.yml files are configuration files interpreted by Docker engine but also serve as convenient documentation files about the composition of your multi-container application.</span></span>

#### <a name="testing-environments"></a><span data-ttu-id="63acd-168">Testovací prostředí</span><span class="sxs-lookup"><span data-stu-id="63acd-168">Testing environments</span></span>

<span data-ttu-id="63acd-169">Důležitou součástí jakéhokoli procesu průběžného nasazování (CD) nebo průběžná integrace (CI) jsou testy jednotek a integrační testy.</span><span class="sxs-lookup"><span data-stu-id="63acd-169">An important part of any continuous deployment (CD) or continuous integration (CI) process are the unit tests and integration tests.</span></span> <span data-ttu-id="63acd-170">Tyto automatizované testy vyžadují izolované prostředí, aby na ně neovlivnili uživatelé ani žádné jiné změny v datech aplikace.</span><span class="sxs-lookup"><span data-stu-id="63acd-170">These automated tests require an isolated environment so they are not impacted by the users or any other change in the application’s data.</span></span>

<span data-ttu-id="63acd-171">Pomocí Docker Compose můžete toto izolované prostředí snadno vytvořit a zničit v několika příkazech z příkazového řádku nebo skriptů, podobně jako v následujících příkazech:</span><span class="sxs-lookup"><span data-stu-id="63acd-171">With Docker Compose, you can create and destroy that isolated environment very easily in a few commands from your command prompt or scripts, like the following commands:</span></span>

```console
docker-compose -f docker-compose.yml -f docker-compose-test.override.yml up -d
./run_unit_tests
docker-compose -f docker-compose.yml -f docker-compose.test.override.yml down
```

#### <a name="production-deployments"></a><span data-ttu-id="63acd-172">Produkční nasazení</span><span class="sxs-lookup"><span data-stu-id="63acd-172">Production deployments</span></span>

<span data-ttu-id="63acd-173">K nasazení na vzdálený modul Docker můžete použít také nástroj vytvořit.</span><span class="sxs-lookup"><span data-stu-id="63acd-173">You can also use Compose to deploy to a remote Docker Engine.</span></span> <span data-ttu-id="63acd-174">Typickým případem je nasazení na jednu instanci hostitele Docker (jako produkční virtuální počítač nebo server zřízený pomocí [Docker Machine](https://docs.docker.com/machine/overview/)).</span><span class="sxs-lookup"><span data-stu-id="63acd-174">A typical case is to deploy to a single Docker host instance (like a production VM or server provisioned with [Docker Machine](https://docs.docker.com/machine/overview/)).</span></span>

<span data-ttu-id="63acd-175">Pokud používáte jakýkoli jiný produkt Orchestrator (Azure Service Fabric, Kubernetes atd.), může být nutné přidat nastavení konfigurace nastavení a metadat, například v Docker-Compose. yml, ale ve formátu požadovaném jiným nástrojem Orchestrator.</span><span class="sxs-lookup"><span data-stu-id="63acd-175">If you are using any other orchestrator (Azure Service Fabric, Kubernetes, etc.), you might need to add setup and metadata configuration settings like those in docker-compose.yml, but in the format required by the other orchestrator.</span></span>

<span data-ttu-id="63acd-176">V každém případě je Docker-napsat pohodlný nástroj a formát metadat pro pracovní postupy pro vývoj, testování a produkční prostředí, i když se produkční pracovní postup může lišit v rámci produktu Orchestrator, který používáte.</span><span class="sxs-lookup"><span data-stu-id="63acd-176">In any case, docker-compose is a convenient tool and metadata format for development, testing and production workflows, although the production workflow might vary on the orchestrator you are using.</span></span>

### <a name="using-multiple-docker-compose-files-to-handle-several-environments"></a><span data-ttu-id="63acd-177">Použití několika souborů Docker-skládání pro zpracování několika prostředí</span><span class="sxs-lookup"><span data-stu-id="63acd-177">Using multiple docker-compose files to handle several environments</span></span>

<span data-ttu-id="63acd-178">Při cílení na různá prostředí byste měli použít více souborů pro vytváření.</span><span class="sxs-lookup"><span data-stu-id="63acd-178">When targeting different environments, you should use multiple compose files.</span></span> <span data-ttu-id="63acd-179">To vám umožní vytvořit několik variant konfigurace v závislosti na prostředí.</span><span class="sxs-lookup"><span data-stu-id="63acd-179">This lets you create multiple configuration variants depending on the environment.</span></span>

#### <a name="overriding-the-base-docker-compose-file"></a><span data-ttu-id="63acd-180">Přepsání základního souboru Docker-skládání</span><span class="sxs-lookup"><span data-stu-id="63acd-180">Overriding the base docker-compose file</span></span>

<span data-ttu-id="63acd-181">Můžete použít jeden soubor Docker-Compose. yml jako v zjednodušených příkladech uvedených v předchozích částech.</span><span class="sxs-lookup"><span data-stu-id="63acd-181">You could use a single docker-compose.yml file as in the simplified examples shown in previous sections.</span></span> <span data-ttu-id="63acd-182">To však nedoporučujeme pro většinu aplikací.</span><span class="sxs-lookup"><span data-stu-id="63acd-182">However, that is not recommended for most applications.</span></span>

<span data-ttu-id="63acd-183">Ve výchozím nastavení čte čtení dva soubory, Docker-Compose. yml a nepovinný soubor Docker-Compose. override. yml.</span><span class="sxs-lookup"><span data-stu-id="63acd-183">By default, Compose reads two files, a docker-compose.yml and an optional docker-compose.override.yml file.</span></span> <span data-ttu-id="63acd-184">Jak je znázorněno na obrázku 6-11, pokud používáte aplikaci Visual Studio a povolíte podporu Docker, sada Visual Studio také vytvoří další soubor Docker-Compose. vs. Debug. g. yml pro ladění aplikace. můžete se podívat na tento soubor ve složce obj\\Docker\\ v hlavní složce řešení.</span><span class="sxs-lookup"><span data-stu-id="63acd-184">As shown in Figure 6-11, when you are using Visual Studio and enabling Docker support, Visual Studio also creates an additional docker-compose.vs.debug.g.yml file for debugging the application, you can take a look at this file in folder obj\\Docker\\ in the main solution folder.</span></span>

![Snímek obrazovky se soubory v projektu Docker pro sestavení.](./media/multi-container-applications-docker-compose/docker-compose-file-visual-studio.png)

<span data-ttu-id="63acd-186">**Obrázek 6-11**.</span><span class="sxs-lookup"><span data-stu-id="63acd-186">**Figure 6-11**.</span></span> <span data-ttu-id="63acd-187">soubory Docker – sestavení v aplikaci Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="63acd-187">docker-compose files in Visual Studio 2019</span></span>

<span data-ttu-id="63acd-188">**Docker – sestavení** struktury souborů projektu:</span><span class="sxs-lookup"><span data-stu-id="63acd-188">**docker-compose** project file structure:</span></span>

- <span data-ttu-id="63acd-189">*. dockerignore* – používá se k ignorování souborů</span><span class="sxs-lookup"><span data-stu-id="63acd-189">*.dockerignore* - used to ignore files</span></span>
- <span data-ttu-id="63acd-190">*Docker-Compose. yml* – slouží k vytváření mikroslužeb</span><span class="sxs-lookup"><span data-stu-id="63acd-190">*docker-compose.yml* - used to compose microservices</span></span>
- <span data-ttu-id="63acd-191">*Docker-Compose. override. yml* – používá se ke konfiguraci prostředí mikroslužeb.</span><span class="sxs-lookup"><span data-stu-id="63acd-191">*docker-compose.override.yml* - used to configure microservices environment</span></span>

<span data-ttu-id="63acd-192">Soubory Docker můžete upravit pomocí libovolného editoru, například Visual Studio Code nebo subvápna, a aplikaci spustit pomocí příkazu Docker-sestavit.</span><span class="sxs-lookup"><span data-stu-id="63acd-192">You can edit the docker-compose files with any editor, like Visual Studio Code or Sublime, and run the application with the docker-compose up command.</span></span>

<span data-ttu-id="63acd-193">Podle konvence obsahuje soubor Docker-Compose. yml základní konfiguraci a jiné statické nastavení.</span><span class="sxs-lookup"><span data-stu-id="63acd-193">By convention, the docker-compose.yml file contains your base configuration and other static settings.</span></span> <span data-ttu-id="63acd-194">To znamená, že se konfigurace služby nesmí měnit v závislosti na prostředí nasazení, které cílíte.</span><span class="sxs-lookup"><span data-stu-id="63acd-194">That means that the service configuration should not change depending on the deployment environment you are targeting.</span></span>

<span data-ttu-id="63acd-195">Soubor Docker-Compose. override. yml, jak je navržen názvem, obsahuje nastavení konfigurace, které přepíše základní konfiguraci, například konfiguraci, která závisí na prostředí nasazení.</span><span class="sxs-lookup"><span data-stu-id="63acd-195">The docker-compose.override.yml file, as its name suggests, contains configuration settings that override the base configuration, such as configuration that depends on the deployment environment.</span></span> <span data-ttu-id="63acd-196">Můžete mít také více souborů přepsání s různými názvy.</span><span class="sxs-lookup"><span data-stu-id="63acd-196">You can have multiple override files with different names also.</span></span> <span data-ttu-id="63acd-197">Soubory přepsání obvykle obsahují další informace, které aplikace potřebuje, ale specifické pro prostředí nebo nasazení.</span><span class="sxs-lookup"><span data-stu-id="63acd-197">The override files usually contain additional information needed by the application but specific to an environment or to a deployment.</span></span>

#### <a name="targeting-multiple-environments"></a><span data-ttu-id="63acd-198">Cílení na více prostředí</span><span class="sxs-lookup"><span data-stu-id="63acd-198">Targeting multiple environments</span></span>

<span data-ttu-id="63acd-199">Typický případ použití je při definování více souborů pro vytváření, aby bylo možné cílit na více prostředí, jako je výroba, příprava, CI nebo vývoj.</span><span class="sxs-lookup"><span data-stu-id="63acd-199">A typical use case is when you define multiple compose files so you can target multiple environments, like production, staging, CI, or development.</span></span> <span data-ttu-id="63acd-200">Pro podporu těchto rozdílů můžete svou konfiguraci vytváření rozdělit do několika souborů, jak je znázorněno na obrázku 6-12.</span><span class="sxs-lookup"><span data-stu-id="63acd-200">To support these differences, you can split your Compose configuration into multiple files, as shown in Figure 6-12.</span></span>

![Diagram tří souborů Docker-skládání nastavených na přepsání základního souboru](./media/multi-container-applications-docker-compose/multiple-docker-compose-files-override-base.png)

<span data-ttu-id="63acd-202">**Obrázek 6-12**.</span><span class="sxs-lookup"><span data-stu-id="63acd-202">**Figure 6-12**.</span></span> <span data-ttu-id="63acd-203">Více souborů Docker – skládáním hodnot do základního souboru Docker-Compose. yml</span><span class="sxs-lookup"><span data-stu-id="63acd-203">Multiple docker-compose files overriding values in the base docker-compose.yml file</span></span>

<span data-ttu-id="63acd-204">Můžete zkombinovat více souborů Docker-Compose\*. yml pro zpracování různých prostředí.</span><span class="sxs-lookup"><span data-stu-id="63acd-204">You can combine multiple docker-compose\*.yml files to handle different environments.</span></span> <span data-ttu-id="63acd-205">Začnete se základním souborem Docker-Compose. yml.</span><span class="sxs-lookup"><span data-stu-id="63acd-205">You start with the base docker-compose.yml file.</span></span> <span data-ttu-id="63acd-206">Tento základní soubor musí obsahovat základní nebo statické nastavení konfigurace, které se v závislosti na prostředí nemění.</span><span class="sxs-lookup"><span data-stu-id="63acd-206">This base file has to contain the base or static configuration settings that do not change depending on the environment.</span></span> <span data-ttu-id="63acd-207">Například eShopOnContainers má následující soubor Docker-Compose. yml (zjednodušený s menším počtem služeb) jako základní soubor.</span><span class="sxs-lookup"><span data-stu-id="63acd-207">For example, the eShopOnContainers has the following docker-compose.yml file (simplified with fewer services) as the base file.</span></span>

```yml
#docker-compose.yml (Base)
version: '3.4'
services:
  basket-api:
    image: eshop/basket-api:${TAG:-latest}
    build:
      context: .
      dockerfile: src/Services/Basket/Basket.API/Dockerfile
    depends_on:
      - basketdata
      - identity-api
      - rabbitmq

  catalog-api:
    image: eshop/catalog-api:${TAG:-latest}
    build:
      context: .
      dockerfile: src/Services/Catalog/Catalog.API/Dockerfile
    depends_on:
      - sqldata
      - rabbitmq

  marketing-api:
    image: eshop/marketing-api:${TAG:-latest}
    build:
      context: .
      dockerfile: src/Services/Marketing/Marketing.API/Dockerfile
    depends_on:
      - sqldata
      - nosqldata
      - identity-api
      - rabbitmq

  webmvc:
    image: eshop/webmvc:${TAG:-latest}
    build:
      context: .
      dockerfile: src/Web/WebMVC/Dockerfile
    depends_on:
      - catalog-api
      - ordering-api
      - identity-api
      - basket-api
      - marketing-api

  sqldata:
    image: mcr.microsoft.com/mssql/server:2017-latest

  nosqldata:
    image: mongo

  basketdata:
    image: redis

  rabbitmq:
    image: rabbitmq:3-management

```

<span data-ttu-id="63acd-208">Hodnoty v základním souboru Docker-Compose. yml by se neměly měnit z důvodu různých cílových prostředí nasazení.</span><span class="sxs-lookup"><span data-stu-id="63acd-208">The values in the base docker-compose.yml file should not change because of different target deployment environments.</span></span>

<span data-ttu-id="63acd-209">Pokud se zaměříte na definici služby webmvc, můžete například zjistit, jak jsou tyto informace mnohem stejné bez ohledu na to, na jaké prostředí budete chtít cílit.</span><span class="sxs-lookup"><span data-stu-id="63acd-209">If you focus on the webmvc service definition, for instance, you can see how that information is much the same no matter what environment you might be targeting.</span></span> <span data-ttu-id="63acd-210">Máte následující informace:</span><span class="sxs-lookup"><span data-stu-id="63acd-210">You have the following information:</span></span>

- <span data-ttu-id="63acd-211">Název služby: webmvc.</span><span class="sxs-lookup"><span data-stu-id="63acd-211">The service name: webmvc.</span></span>

- <span data-ttu-id="63acd-212">Vlastní image kontejneru: eshop/webmvc.</span><span class="sxs-lookup"><span data-stu-id="63acd-212">The container’s custom image: eshop/webmvc.</span></span>

- <span data-ttu-id="63acd-213">Příkaz pro sestavení vlastní image Docker, která určuje, který souboru Dockerfile se má použít.</span><span class="sxs-lookup"><span data-stu-id="63acd-213">The command to build the custom Docker image, indicating which Dockerfile to use.</span></span>

- <span data-ttu-id="63acd-214">Závislosti na jiných službách, takže tento kontejner se nespustí, dokud se nespustí ostatní kontejnery závislostí.</span><span class="sxs-lookup"><span data-stu-id="63acd-214">Dependencies on other services, so this container does not start until the other dependency containers have started.</span></span>

<span data-ttu-id="63acd-215">Můžete mít další konfiguraci, ale důležitým bodem je, že v základním souboru Docker-Compose. yml budete chtít jenom nastavit informace, které jsou v různých prostředích společné.</span><span class="sxs-lookup"><span data-stu-id="63acd-215">You can have additional configuration, but the important point is that in the base docker-compose.yml file, you just want to set the information that is common across environments.</span></span> <span data-ttu-id="63acd-216">Pak v Docker-Compose. override. yml nebo podobné soubory pro produkční prostředí nebo přípravu byste měli umístit konfiguraci, která je specifická pro každé prostředí.</span><span class="sxs-lookup"><span data-stu-id="63acd-216">Then in the docker-compose.override.yml or similar files for production or staging, you should place configuration that is specific for each environment.</span></span>

<span data-ttu-id="63acd-217">Obvykle se pro vývojové prostředí používá Docker-Compose. override. yml, jako v následujícím příkladu z eShopOnContainers:</span><span class="sxs-lookup"><span data-stu-id="63acd-217">Usually, the docker-compose.override.yml is used for your development environment, as in the following example from eShopOnContainers:</span></span>

```yml
#docker-compose.override.yml (Extended config for DEVELOPMENT env.)
version: '3.4'

services:
# Simplified number of services here:

  basket-api:
    environment:
      - ASPNETCORE_ENVIRONMENT=Development
      - ASPNETCORE_URLS=http://0.0.0.0:80
      - ConnectionString=${ESHOP_AZURE_REDIS_BASKET_DB:-basketdata}
      - identityUrl=http://identity-api
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

  catalog-api:
    environment:
      - ASPNETCORE_ENVIRONMENT=Development
      - ASPNETCORE_URLS=http://0.0.0.0:80
      - ConnectionString=${ESHOP_AZURE_CATALOG_DB:-Server=sqldata;Database=Microsoft.eShopOnContainers.Services.CatalogDb;User Id=sa;Password=Pass@word}
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

  marketing-api:
    environment:
      - ASPNETCORE_ENVIRONMENT=Development
      - ASPNETCORE_URLS=http://0.0.0.0:80
      - ConnectionString=${ESHOP_AZURE_MARKETING_DB:-Server=sqldata;Database=Microsoft.eShopOnContainers.Services.MarketingDb;User Id=sa;Password=Pass@word}
      - MongoConnectionString=${ESHOP_AZURE_COSMOSDB:-mongodb://nosqldata}
      - MongoDatabase=MarketingDb
      - EventBusConnection=${ESHOP_AZURE_SERVICE_BUS:-rabbitmq}
      - EventBusUserName=${ESHOP_SERVICE_BUS_USERNAME}
      - EventBusPassword=${ESHOP_SERVICE_BUS_PASSWORD}
      - identityUrl=http://identity-api
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
      - CatalogUrlHC=http://catalog-api/hc
      - OrderingUrlHC=http://ordering-api/hc
      - IdentityUrlHC=http://identity-api/hc
      - BasketUrlHC=http://basket-api/hc
      - MarketingUrlHC=http://marketing-api/hc
      - PaymentUrlHC=http://payment-api/hc
      - SignalrHubUrl=http://${ESHOP_EXTERNAL_DNS_NAME_OR_IP}:5202
      - UseCustomizationData=True
      - ApplicationInsights__InstrumentationKey=${INSTRUMENTATION_KEY}
      - OrchestratorType=${ORCHESTRATOR_TYPE}
      - UseLoadTest=${USE_LOADTEST:-False}
    ports:
      - "5100:80"
  sqldata:
    environment:
      - SA_PASSWORD=Pass@word
      - ACCEPT_EULA=Y
    ports:
      - "5433:1433"
  nosqldata:
    ports:
      - "27017:27017"
  basketdata:
    ports:
      - "6379:6379"
  rabbitmq:
    ports:
      - "15672:15672"
      - "5672:5672"

```

<span data-ttu-id="63acd-218">V tomto příkladu konfigurace přepsání vývoje zpřístupňuje některé porty hostiteli, definuje proměnné prostředí s adresami URL pro přesměrování a určuje připojovací řetězce pro vývojové prostředí.</span><span class="sxs-lookup"><span data-stu-id="63acd-218">In this example, the development override configuration exposes some ports to the host, defines environment variables with redirect URLs, and specifies connection strings for the development environment.</span></span> <span data-ttu-id="63acd-219">Tato nastavení jsou pouze pro vývojové prostředí.</span><span class="sxs-lookup"><span data-stu-id="63acd-219">These settings are all just for the development environment.</span></span>

<span data-ttu-id="63acd-220">Když spustíte `docker-compose up` (nebo ho spustíte ze sady Visual Studio), příkaz automaticky přečte přepsání, jako kdyby byly oba soubory sloučeny.</span><span class="sxs-lookup"><span data-stu-id="63acd-220">When you run `docker-compose up` (or launch it from Visual Studio), the command reads the overrides automatically as if it were merging both files.</span></span>

<span data-ttu-id="63acd-221">Předpokládejme, že budete chtít jiný soubor pro vytváření v produkčním prostředí s různými hodnotami konfigurace, porty nebo připojovacími řetězci.</span><span class="sxs-lookup"><span data-stu-id="63acd-221">Suppose that you want another Compose file for the production environment, with different configuration values, ports, or connection strings.</span></span> <span data-ttu-id="63acd-222">Můžete vytvořit další soubor přepsání, jako je například soubor s názvem `docker-compose.prod.yml` s různými nastaveními a proměnnými prostředí.</span><span class="sxs-lookup"><span data-stu-id="63acd-222">You can create another override file, like file named `docker-compose.prod.yml` with different settings and environment variables.</span></span> <span data-ttu-id="63acd-223">Tento soubor může být uložený v jiném úložišti Git nebo spravovaný a zabezpečený jiným týmem.</span><span class="sxs-lookup"><span data-stu-id="63acd-223">That file might be stored in a different Git repo or managed and secured by a different team.</span></span>

#### <a name="how-to-deploy-with-a-specific-override-file"></a><span data-ttu-id="63acd-224">Postup nasazení s konkrétním souborem přepsání</span><span class="sxs-lookup"><span data-stu-id="63acd-224">How to deploy with a specific override file</span></span>

<span data-ttu-id="63acd-225">Chcete-li použít více souborů přepsání nebo přepsat soubor s jiným názvem, můžete použít možnost-f s příkazem Docker-skládání a zadat soubory.</span><span class="sxs-lookup"><span data-stu-id="63acd-225">To use multiple override files, or an override file with a different name, you can use the -f option with the docker-compose command and specify the files.</span></span> <span data-ttu-id="63acd-226">Vytváření sloučí soubory v pořadí, v jakém jsou zadány na příkazovém řádku.</span><span class="sxs-lookup"><span data-stu-id="63acd-226">Compose merges files in the order they are specified on the command line.</span></span> <span data-ttu-id="63acd-227">Následující příklad ukazuje, jak nasadit soubory s přepsáním.</span><span class="sxs-lookup"><span data-stu-id="63acd-227">The following example shows how to deploy with override files.</span></span>

```console
docker-compose -f docker-compose.yml -f docker-compose.prod.yml up -d
```

#### <a name="using-environment-variables-in-docker-compose-files"></a><span data-ttu-id="63acd-228">Použití proměnných prostředí v Docker – skládání souborů</span><span class="sxs-lookup"><span data-stu-id="63acd-228">Using environment variables in docker-compose files</span></span>

<span data-ttu-id="63acd-229">V produkčních prostředích je to vhodné, zejména v produkčním prostředí, aby bylo možné získat informace o konfiguraci z proměnných prostředí, jak jsme ukázali v předchozích příkladech.</span><span class="sxs-lookup"><span data-stu-id="63acd-229">It is convenient, especially in production environments, to be able to get configuration information from environment variables, as we have shown in previous examples.</span></span> <span data-ttu-id="63acd-230">Na proměnnou prostředí v souborech Docker můžete odkazovat pomocí syntaxe $ {MY\_VAR}.</span><span class="sxs-lookup"><span data-stu-id="63acd-230">You can reference an environment variable in your docker-compose files using the syntax ${MY\_VAR}.</span></span> <span data-ttu-id="63acd-231">Následující řádek ze souboru Docker-Compose. prod. yml ukazuje, jak odkazovat na hodnotu proměnné prostředí.</span><span class="sxs-lookup"><span data-stu-id="63acd-231">The following line from a docker-compose.prod.yml file shows how to reference the value of an environment variable.</span></span>

```yml
IdentityUrl=http://${ESHOP_PROD_EXTERNAL_DNS_NAME_OR_IP}:5105
```

<span data-ttu-id="63acd-232">Proměnné prostředí jsou vytvářeny a inicializovány různými způsoby v závislosti na hostitelském prostředí (Linux, Windows, cloudovém clusteru atd.).</span><span class="sxs-lookup"><span data-stu-id="63acd-232">Environment variables are created and initialized in different ways, depending on your host environment (Linux, Windows, Cloud cluster, etc.).</span></span> <span data-ttu-id="63acd-233">Pohodlný přístup ale je použít soubor. env.</span><span class="sxs-lookup"><span data-stu-id="63acd-233">However, a convenient approach is to use an .env file.</span></span> <span data-ttu-id="63acd-234">Soubory Docker-skládání podporují deklaraci výchozích proměnných prostředí v souboru. env.</span><span class="sxs-lookup"><span data-stu-id="63acd-234">The docker-compose files support declaring default environment variables in the .env file.</span></span> <span data-ttu-id="63acd-235">Tyto hodnoty pro proměnné prostředí jsou výchozí hodnoty.</span><span class="sxs-lookup"><span data-stu-id="63acd-235">These values for the environment variables are the default values.</span></span> <span data-ttu-id="63acd-236">Ale můžou být přepsány hodnotami, které jste pravděpodobně definovali v každém z vašich prostředí (hostitelský operační systém nebo proměnné prostředí z vašeho clusteru).</span><span class="sxs-lookup"><span data-stu-id="63acd-236">But they can be overridden by the values you might have defined in each of your environments (host OS or environment variables from your cluster).</span></span> <span data-ttu-id="63acd-237">Tento soubor. env umístíte do složky, ve které je spuštěný příkaz Docker-skládání.</span><span class="sxs-lookup"><span data-stu-id="63acd-237">You place this .env file in the folder where the docker-compose command is executed from.</span></span>

<span data-ttu-id="63acd-238">Následující příklad ukazuje soubor. ENV, jako je soubor [. env](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/.env) pro aplikaci eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="63acd-238">The following example shows an .env file like the [.env](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/.env) file for the eShopOnContainers application.</span></span>

```sh
# .env file

ESHOP_EXTERNAL_DNS_NAME_OR_IP=localhost

ESHOP_PROD_EXTERNAL_DNS_NAME_OR_IP=10.121.122.92
```

<span data-ttu-id="63acd-239">Docker-Format očekává, že každý řádek v souboru. env bude ve formátu \<proměnná\>=\<Value\>.</span><span class="sxs-lookup"><span data-stu-id="63acd-239">Docker-compose expects each line in an .env file to be in the format \<variable\>=\<value\>.</span></span>

<span data-ttu-id="63acd-240">Hodnoty nastavené v běhovém prostředí vždy přepisují hodnoty definované v souboru. env.</span><span class="sxs-lookup"><span data-stu-id="63acd-240">The values set in the run-time environment always override the values defined inside the .env file.</span></span> <span data-ttu-id="63acd-241">Podobným způsobem hodnoty předané pomocí argumentů příkazového řádku přepisují také výchozí hodnoty nastavené v souboru. env.</span><span class="sxs-lookup"><span data-stu-id="63acd-241">In a similar way, values passed via command-line arguments also override the default values set in the .env file.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="63acd-242">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="63acd-242">Additional resources</span></span>

- <span data-ttu-id="63acd-243">**Přehled Docker Compose** </span><span class="sxs-lookup"><span data-stu-id="63acd-243">**Overview of Docker Compose** </span></span>\
    <https://docs.docker.com/compose/overview/>

- <span data-ttu-id="63acd-244">**Více souborů pro vytváření** </span><span class="sxs-lookup"><span data-stu-id="63acd-244">**Multiple Compose files** </span></span>\
    [https://docs.docker.com/compose/extends/\#multiple-compose-files](https://docs.docker.com/compose/extends/#multiple-compose-files)

### <a name="building-optimized-aspnet-core-docker-images"></a><span data-ttu-id="63acd-245">Vytváření optimalizovaných imagí ASP.NET Core Docker</span><span class="sxs-lookup"><span data-stu-id="63acd-245">Building optimized ASP.NET Core Docker images</span></span>

<span data-ttu-id="63acd-246">Pokud zkoumáte Docker a .NET Core na zdrojích na internetu, najdete fázemi, které demonstrují jednoduchost vytváření imagí Docker zkopírováním zdroje do kontejneru.</span><span class="sxs-lookup"><span data-stu-id="63acd-246">If you are exploring Docker and .NET Core on sources on the Internet, you will find Dockerfiles that demonstrate the simplicity of building a Docker image by copying your source into a container.</span></span> <span data-ttu-id="63acd-247">Tyto příklady naznačují, že pomocí jednoduché konfigurace můžete mít image Docker s prostředím zabaleným do aplikace.</span><span class="sxs-lookup"><span data-stu-id="63acd-247">These examples suggest that by using a simple configuration, you can have a Docker image with the environment packaged with your application.</span></span> <span data-ttu-id="63acd-248">Následující příklad ukazuje jednoduchý souboru Dockerfile v tomto podmnožině.</span><span class="sxs-lookup"><span data-stu-id="63acd-248">The following example shows a simple Dockerfile in this vein.</span></span>

```Dockerfile
FROM mcr.microsoft.com/dotnet/core/sdk:3.1
WORKDIR /app
ENV ASPNETCORE_URLS http://+:80
EXPOSE 80
COPY . .
RUN dotnet restore
ENTRYPOINT ["dotnet", "run"]
```

<span data-ttu-id="63acd-249">Souboru Dockerfile jako to bude fungovat.</span><span class="sxs-lookup"><span data-stu-id="63acd-249">A Dockerfile like this will work.</span></span> <span data-ttu-id="63acd-250">Vaše image ale můžete významně optimalizovat, zejména v produkčních bitových kopiích.</span><span class="sxs-lookup"><span data-stu-id="63acd-250">However, you can substantially optimize your images, especially your production images.</span></span>

<span data-ttu-id="63acd-251">V modelu kontejneru a mikroslužeb jsou stále spouštěny kontejnery.</span><span class="sxs-lookup"><span data-stu-id="63acd-251">In the container and microservices model, you are constantly starting containers.</span></span> <span data-ttu-id="63acd-252">Typický způsob použití kontejnerů nerestartuje kontejner v režimu spánku, protože kontejner je na jedno použití.</span><span class="sxs-lookup"><span data-stu-id="63acd-252">The typical way of using containers does not restart a sleeping container, because the container is disposable.</span></span> <span data-ttu-id="63acd-253">Orchestrace (jako Kubernetes a Azure Service Fabric) jednoduše vytvoří nové instance imagí.</span><span class="sxs-lookup"><span data-stu-id="63acd-253">Orchestrators (like Kubernetes and Azure Service Fabric) simply create new instances of images.</span></span> <span data-ttu-id="63acd-254">To znamená, že je nutné optimalizovat sestavením aplikace, když je sestavena, takže proces vytváření instancí bude rychlejší.</span><span class="sxs-lookup"><span data-stu-id="63acd-254">What this means is that you would need to optimize by precompiling the application when it is built so the instantiation process will be faster.</span></span> <span data-ttu-id="63acd-255">Po spuštění kontejneru by měl být připraven ke spuštění.</span><span class="sxs-lookup"><span data-stu-id="63acd-255">When the container is started, it should be ready to run.</span></span> <span data-ttu-id="63acd-256">Za běhu byste neměli obnovovat a kompilovat pomocí příkazů `dotnet restore` a `dotnet build` z příkazu dotnet CLI, který se zobrazí v mnoha blogových příspěvcích o .NET Core a Docker.</span><span class="sxs-lookup"><span data-stu-id="63acd-256">You should not restore and compile at run time, using `dotnet restore` and `dotnet build` commands from the dotnet CLI that, as you see in many blog posts about .NET Core and Docker.</span></span>

<span data-ttu-id="63acd-257">Tým .NET prováděl důležitou práci pro zajištění .NET Core a ASP.NET Core architektury optimalizované pro kontejnery.</span><span class="sxs-lookup"><span data-stu-id="63acd-257">The .NET team has been doing important work to make .NET Core and ASP.NET Core a container-optimized framework.</span></span> <span data-ttu-id="63acd-258">Jenom rozhraní .NET Core a odlehčené rozhraní s malými nároky na paměť; tým se zaměřuje na optimalizované image Docker pro tři hlavní scénáře a publikovaly je v registru Docker Hub v *dotnet/Core*, počínaje verzí 2,1:</span><span class="sxs-lookup"><span data-stu-id="63acd-258">Not only is .NET Core a lightweight framework with a small memory footprint; the team has focused on optimized Docker images for three main scenarios and published them in the Docker Hub registry at *dotnet/core*, beginning with version 2.1:</span></span>

1. <span data-ttu-id="63acd-259">**Vývoj**: kde priorita je schopnost rychle iterovat a ladit změny a kde je velikost sekundární.</span><span class="sxs-lookup"><span data-stu-id="63acd-259">**Development**: Where the priority is the ability to quickly iterate and debug changes, and where size is secondary.</span></span>

2. <span data-ttu-id="63acd-260">**Sestavení**: priorita kompiluje aplikaci a zahrnuje binární soubory a další závislosti pro optimalizaci binárních souborů.</span><span class="sxs-lookup"><span data-stu-id="63acd-260">**Build**: The priority is compiling the application and includes binaries and other dependencies to optimize binaries.</span></span>

3. <span data-ttu-id="63acd-261">**Produkční**: kde se zaměřuje na rychlé nasazení a spuštění kontejnerů, takže tyto image jsou omezené na binární soubory a obsah potřebný ke spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="63acd-261">**Production**: Where the focus is fast deploying and starting of containers, so these images are limited to the binaries and the content needed to run the application.</span></span>

<span data-ttu-id="63acd-262">Za tímto účelem tým .NET poskytuje čtyři základní varianty v [dotnet/Core](https://hub.docker.com/_/microsoft-dotnet-core/) (v Docker Hub):</span><span class="sxs-lookup"><span data-stu-id="63acd-262">To achieve this, the .NET team is providing four basic variants in [dotnet/core](https://hub.docker.com/_/microsoft-dotnet-core/) (at Docker Hub):</span></span>

1. <span data-ttu-id="63acd-263">**SDK**: pro scénáře vývoje a sestavování</span><span class="sxs-lookup"><span data-stu-id="63acd-263">**sdk**: for development and build scenarios</span></span>
1. <span data-ttu-id="63acd-264">**ASPNET**: pro produkční scénáře ASP.NET</span><span class="sxs-lookup"><span data-stu-id="63acd-264">**aspnet**: for ASP.NET production scenarios</span></span>
1. <span data-ttu-id="63acd-265">**runtime**: pro produkční scénáře .NET</span><span class="sxs-lookup"><span data-stu-id="63acd-265">**runtime**: for .NET production scenarios</span></span>
1. <span data-ttu-id="63acd-266">**runtime-DEPS**: pro produkční scénáře aplikací, které jsou [samostatně obsaženy](../../../core/deploying/index.md#publish-self-contained).</span><span class="sxs-lookup"><span data-stu-id="63acd-266">**runtime-deps**: for production scenarios of [self-contained applications](../../../core/deploying/index.md#publish-self-contained).</span></span>

<span data-ttu-id="63acd-267">V případě rychlejšího spuštění jsou bitové kopie za běhu také automaticky nastaveny\_adresy URL aspnetcore na port 80 a použít Ngen k vytvoření mezipaměti nativní bitové kopie sestavení.</span><span class="sxs-lookup"><span data-stu-id="63acd-267">For faster startup, runtime images also automatically set aspnetcore\_urls to port 80 and use Ngen to create a native image cache of assemblies.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="63acd-268">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="63acd-268">Additional resources</span></span>

- <span data-ttu-id="63acd-269">**Vytváření optimalizovaných imagí Docker pomocí ASP.NET Core**</span><span class="sxs-lookup"><span data-stu-id="63acd-269">**Building Optimized Docker Images with ASP.NET Core**</span></span>  
  <https://docs.microsoft.com/archive/blogs/stevelasker/building-optimized-docker-images-with-asp-net-core>

- <span data-ttu-id="63acd-270">**Vytváření imagí Dockeru pro aplikace .NET Core**</span><span class="sxs-lookup"><span data-stu-id="63acd-270">**Building Docker Images for .NET Core Applications**</span></span>  
  [https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images](/aspnet/core/host-and-deploy/docker/building-net-docker-images)

> [!div class="step-by-step"]
> <span data-ttu-id="63acd-271">[Předchozí](data-driven-crud-microservice.md)
> [Další](database-server-container.md)</span><span class="sxs-lookup"><span data-stu-id="63acd-271">[Previous](data-driven-crud-microservice.md)
[Next](database-server-container.md)</span></span>
