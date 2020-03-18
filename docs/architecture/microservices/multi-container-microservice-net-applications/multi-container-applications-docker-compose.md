---
title: Definování vícekontejnerové aplikace pomocí docker-compose.yml
description: Jak určit složení mikroslužeb pro vícekontejnerovou aplikaci s docker-compose.yml.
ms.date: 01/30/2020
ms.openlocfilehash: 86d6feda343df7f4b72374f93fc45b3246780cdf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "77502455"
---
# <a name="defining-your-multi-container-application-with-docker-composeyml"></a><span data-ttu-id="42fb5-103">Definování vícekontejnerové aplikace pomocí docker-compose.yml</span><span class="sxs-lookup"><span data-stu-id="42fb5-103">Defining your multi-container application with docker-compose.yml</span></span>

<span data-ttu-id="42fb5-104">V této příručce byl soubor [docker-compose.yml](https://docs.docker.com/compose/compose-file/) představen v části [Krok 4. Definujte své služby v docker-compose.yml při vytváření aplikace Docker u více kontejnerů](../docker-application-development-process/docker-app-development-workflow.md#step-4-define-your-services-in-docker-composeyml-when-building-a-multi-container-docker-application).</span><span class="sxs-lookup"><span data-stu-id="42fb5-104">In this guide, the [docker-compose.yml](https://docs.docker.com/compose/compose-file/) file was introduced in the section [Step 4. Define your services in docker-compose.yml when building a multi-container Docker application](../docker-application-development-process/docker-app-development-workflow.md#step-4-define-your-services-in-docker-composeyml-when-building-a-multi-container-docker-application).</span></span> <span data-ttu-id="42fb5-105">Existují však další způsoby, jak použít soubory docker-compose, které stojí za prozkoumání podrobněji.</span><span class="sxs-lookup"><span data-stu-id="42fb5-105">However, there are additional ways to use the docker-compose files that are worth exploring in further detail.</span></span>

<span data-ttu-id="42fb5-106">Můžete například explicitně popsat, jak chcete nasadit aplikaci s více kontejnery v souboru docker-compose.yml.</span><span class="sxs-lookup"><span data-stu-id="42fb5-106">For example, you can explicitly describe how you want to deploy your multi-container application in the docker-compose.yml file.</span></span> <span data-ttu-id="42fb5-107">Volitelně můžete také popsat, jak budete vytvářet vlastní image Dockeru.</span><span class="sxs-lookup"><span data-stu-id="42fb5-107">Optionally, you can also describe how you are going to build your custom Docker images.</span></span> <span data-ttu-id="42fb5-108">(Vlastní inabité image Dockeru lze také sestavit pomocí cli Dockeru.)</span><span class="sxs-lookup"><span data-stu-id="42fb5-108">(Custom Docker images can also be built with the Docker CLI.)</span></span>

<span data-ttu-id="42fb5-109">V podstatě definujete každý z kontejnerů, které chcete nasadit, plus určité charakteristiky pro každé nasazení kontejneru.</span><span class="sxs-lookup"><span data-stu-id="42fb5-109">Basically, you define each of the containers you want to deploy plus certain characteristics for each container deployment.</span></span> <span data-ttu-id="42fb5-110">Jakmile máte soubor s popisem nasazení s více kontejnery, můžete nasadit celé řešení v jedné akci řízené příkazem příkazu příkazu příkazu příkazu příkazu příkazu příkazu příkazu příkazu příkazu příkazu příkazu příkazu příkazu cli [v dockeru](https://docs.docker.com/compose/overview/) nebo jej můžete nasadit transparentně z visual studia.</span><span class="sxs-lookup"><span data-stu-id="42fb5-110">Once you have a multi-container deployment description file, you can deploy the whole solution in a single action orchestrated by the [docker-compose up](https://docs.docker.com/compose/overview/) CLI command, or you can deploy it transparently from Visual Studio.</span></span> <span data-ttu-id="42fb5-111">V opačném případě budete muset použít Docker CLI k nasazení kontejneru `docker run` po kontejneru ve více krocích pomocí příkazu z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="42fb5-111">Otherwise, you would need to use the Docker CLI to deploy container-by-container in multiple steps by using the `docker run` command from the command line.</span></span> <span data-ttu-id="42fb5-112">Proto každá služba definovaná v docker-compose.yml musí zadat přesně jednu bitovou kopii nebo sestavení.</span><span class="sxs-lookup"><span data-stu-id="42fb5-112">Therefore, each service defined in docker-compose.yml must specify exactly one image or build.</span></span> <span data-ttu-id="42fb5-113">Ostatní klíče jsou volitelné a jsou `docker run` podobné jejich protějšky příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="42fb5-113">Other keys are optional, and are analogous to their `docker run` command-line counterparts.</span></span>

<span data-ttu-id="42fb5-114">Následující kód YAML je definice možného globálního, ale jediného souboru docker-compose.yml pro ukázku eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="42fb5-114">The following YAML code is the definition of a possible global but single docker-compose.yml file for the eShopOnContainers sample.</span></span> <span data-ttu-id="42fb5-115">Toto není skutečný docker-compose soubor z eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="42fb5-115">This is not the actual docker-compose file from eShopOnContainers.</span></span> <span data-ttu-id="42fb5-116">Místo toho se jedná o zjednodušenou a konsolidovanou verzi v jednom souboru, což není nejlepší způsob práce se soubory docker-compose, jak bude vysvětleno později.</span><span class="sxs-lookup"><span data-stu-id="42fb5-116">Instead, it is a simplified and consolidated version in a single file, which is not the best way to work with docker-compose files, as will be explained later.</span></span>

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

<span data-ttu-id="42fb5-117">Kořenový klíč v tomto souboru jsou služby.</span><span class="sxs-lookup"><span data-stu-id="42fb5-117">The root key in this file is services.</span></span> <span data-ttu-id="42fb5-118">Pod tímto klíčem definujete služby, které chcete `docker-compose up` nasadit a spustit při spuštění příkazu nebo při nasazení z Visual Studia pomocí tohoto souboru docker-compose.yml.</span><span class="sxs-lookup"><span data-stu-id="42fb5-118">Under that key, you define the services you want to deploy and run when you execute the `docker-compose up` command or when you deploy from Visual Studio by using this docker-compose.yml file.</span></span> <span data-ttu-id="42fb5-119">V tomto případě má soubor docker-compose.yml více definovaných služeb, jak je popsáno v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="42fb5-119">In this case, the docker-compose.yml file has multiple services defined, as described in the following table.</span></span>

| <span data-ttu-id="42fb5-120">Název služby</span><span class="sxs-lookup"><span data-stu-id="42fb5-120">Service name</span></span> | <span data-ttu-id="42fb5-121">Popis</span><span class="sxs-lookup"><span data-stu-id="42fb5-121">Description</span></span> |
|--------------|-------------|
| <span data-ttu-id="42fb5-122">webmvc</span><span class="sxs-lookup"><span data-stu-id="42fb5-122">webmvc</span></span>       | <span data-ttu-id="42fb5-123">Kontejner včetně aplikace ASP.NET Core MVC, která spotřebovává mikroslužby z C na straně serveru\#</span><span class="sxs-lookup"><span data-stu-id="42fb5-123">Container including the ASP.NET Core MVC application consuming the microservices from server-side C\#</span></span>|
| <span data-ttu-id="42fb5-124">katalog-api</span><span class="sxs-lookup"><span data-stu-id="42fb5-124">catalog-api</span></span>  | <span data-ttu-id="42fb5-125">Kontejner včetně mikroslužby katalogového ASP.NET základního webového rozhraní API</span><span class="sxs-lookup"><span data-stu-id="42fb5-125">Container including the Catalog ASP.NET Core Web API microservice</span></span> |
| <span data-ttu-id="42fb5-126">objednání-api</span><span class="sxs-lookup"><span data-stu-id="42fb5-126">ordering-api</span></span> | <span data-ttu-id="42fb5-127">Kontejner včetně řazení ASP.NET základní webové rozhraní API mikroslužby</span><span class="sxs-lookup"><span data-stu-id="42fb5-127">Container including the Ordering ASP.NET Core Web API microservice</span></span> |
| <span data-ttu-id="42fb5-128">sqldata</span><span class="sxs-lookup"><span data-stu-id="42fb5-128">sqldata</span></span>     | <span data-ttu-id="42fb5-129">Kontejner se systémem SQL Server pro Linux, který drží databáze mikroslužeb</span><span class="sxs-lookup"><span data-stu-id="42fb5-129">Container running SQL Server for Linux, holding the microservices databases</span></span> |
| <span data-ttu-id="42fb5-130">koš-api</span><span class="sxs-lookup"><span data-stu-id="42fb5-130">basket-api</span></span>   | <span data-ttu-id="42fb5-131">Kontejner s mikroslužbou basket ASP.NET Core Web API</span><span class="sxs-lookup"><span data-stu-id="42fb5-131">Container with the Basket ASP.NET Core Web API microservice</span></span> |
| <span data-ttu-id="42fb5-132">data košíku</span><span class="sxs-lookup"><span data-stu-id="42fb5-132">basketdata</span></span>  | <span data-ttu-id="42fb5-133">Kontejner se spuštěnou službou mezipaměti REDIS s databází košíku jako mezipamětí REDIS</span><span class="sxs-lookup"><span data-stu-id="42fb5-133">Container running the REDIS cache service, with the basket database as a REDIS cache</span></span> |

### <a name="a-simple-web-service-api-container"></a><span data-ttu-id="42fb5-134">Jednoduchý kontejner rozhraní API webové služby</span><span class="sxs-lookup"><span data-stu-id="42fb5-134">A simple Web Service API container</span></span>

<span data-ttu-id="42fb5-135">Zaměření na jeden kontejner, kontejner rozhraní API katalogu mikroslužby má přímočarou definici:</span><span class="sxs-lookup"><span data-stu-id="42fb5-135">Focusing on a single container, the catalog-api container-microservice has a straightforward definition:</span></span>

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

<span data-ttu-id="42fb5-136">Tato kontejnerizovaná služba má následující základní konfiguraci:</span><span class="sxs-lookup"><span data-stu-id="42fb5-136">This containerized service has the following basic configuration:</span></span>

- <span data-ttu-id="42fb5-137">Je založen na vlastní **image eshopu / katalog-api.**</span><span class="sxs-lookup"><span data-stu-id="42fb5-137">It is based on the custom **eshop/catalog-api** image.</span></span> <span data-ttu-id="42fb5-138">Z důvodu jednoduchosti neexistuje žádné sestavení: nastavení klíče v souboru.</span><span class="sxs-lookup"><span data-stu-id="42fb5-138">For simplicity’s sake, there is no build: key setting in the file.</span></span> <span data-ttu-id="42fb5-139">To znamená, že image musí být dříve sestaveny (s docker sestavení) nebo byly staženy (s příkazem docker pull) z libovolného registru Docker.</span><span class="sxs-lookup"><span data-stu-id="42fb5-139">This means that the image must have been previously built (with docker build) or have been downloaded (with the docker pull command) from any Docker registry.</span></span>

- <span data-ttu-id="42fb5-140">Definuje proměnnou prostředí s názvem ConnectionString s připojovacím řetězcem, který má být použit rozhraním Entity Framework pro přístup k instanci serveru SQL Server, která obsahuje datový model katalogu.</span><span class="sxs-lookup"><span data-stu-id="42fb5-140">It defines an environment variable named ConnectionString with the connection string to be used by Entity Framework to access the SQL Server instance that contains the catalog data model.</span></span> <span data-ttu-id="42fb5-141">V tomto případě stejný kontejner SQL Server obsahuje více databází.</span><span class="sxs-lookup"><span data-stu-id="42fb5-141">In this case, the same SQL Server container is holding multiple databases.</span></span> <span data-ttu-id="42fb5-142">Proto potřebujete méně paměti ve vývojovém počítači pro Docker.</span><span class="sxs-lookup"><span data-stu-id="42fb5-142">Therefore, you need less memory in your development machine for Docker.</span></span> <span data-ttu-id="42fb5-143">Můžete však také nasadit jeden kontejner serveru SQL Server pro každou databázi mikroslužeb.</span><span class="sxs-lookup"><span data-stu-id="42fb5-143">However, you could also deploy one SQL Server container for each microservice database.</span></span>

- <span data-ttu-id="42fb5-144">Název serveru SQL Server je **sqldata**, což je stejný název použitý pro kontejner, ve kterém je spuštěna instance SERVERU SQL Server pro Linux.</span><span class="sxs-lookup"><span data-stu-id="42fb5-144">The SQL Server name is **sqldata**, which is the same name used for the container that is running the SQL Server instance for Linux.</span></span> <span data-ttu-id="42fb5-145">To je výhodné; možnost používat tento překlad názvů (interní pro hostitele Dockeru) vyřeší síťovou adresu, takže nepotřebujete znát interní IP adresu pro kontejnery, ke které přistupujete z jiných kontejnerů.</span><span class="sxs-lookup"><span data-stu-id="42fb5-145">This is convenient; being able to use this name resolution (internal to the Docker host) will resolve the network address so you don’t need to know the internal IP for the containers you are accessing from other containers.</span></span>

<span data-ttu-id="42fb5-146">Vzhledem k tomu, že připojovací řetězec je definován proměnnou prostředí, můžete tuto proměnnou nastavit prostřednictvím jiného mechanismu a v jiném čase.</span><span class="sxs-lookup"><span data-stu-id="42fb5-146">Because the connection string is defined by an environment variable, you could set that variable through a different mechanism and at a different time.</span></span> <span data-ttu-id="42fb5-147">Můžete například nastavit jiný připojovací řetězec při nasazování do produkčního prostředí v konečných hostitelích nebo tím, že to uděláte z vašich kanálů CI/CD ve službě Azure DevOps Services nebo ve vámi upřednostňovaném systému DevOps.</span><span class="sxs-lookup"><span data-stu-id="42fb5-147">For example, you could set a different connection string when deploying to production in the final hosts, or by doing it from your CI/CD pipelines in Azure DevOps Services or your preferred DevOps system.</span></span>

- <span data-ttu-id="42fb5-148">Zpřístupňuje port 80 pro interní přístup ke službě **rozhraní API katalogu** v rámci hostitele Dockeru.</span><span class="sxs-lookup"><span data-stu-id="42fb5-148">It exposes port 80 for internal access to the **catalog-api** service within the Docker host.</span></span> <span data-ttu-id="42fb5-149">Hostitel je aktuálně virtuální počítač s Linuxem, protože je založen na image Dockeru pro Linux, ale místo toho můžete nakonfigurovat kontejner pro spuštění na bitové kopii systému Windows.</span><span class="sxs-lookup"><span data-stu-id="42fb5-149">The host is currently a Linux VM because it is based on a Docker image for Linux, but you could configure the container to run on a Windows image instead.</span></span>

- <span data-ttu-id="42fb5-150">Předá exponovaný port 80 na kontejneru na port 5101 na hostitelském počítači Dockeru (virtuální počítač SIF).</span><span class="sxs-lookup"><span data-stu-id="42fb5-150">It forwards the exposed port 80 on the container to port 5101 on the Docker host machine (the Linux VM).</span></span>

- <span data-ttu-id="42fb5-151">Propojuje webovou službu se službou **sqldata** (instance SQL Serveru pro databázi Linuxu spuštěnou v kontejneru).</span><span class="sxs-lookup"><span data-stu-id="42fb5-151">It links the web service to the **sqldata** service (the SQL Server instance for Linux database running in a container).</span></span> <span data-ttu-id="42fb5-152">Když zadáte tuto závislost, kontejner rozhraní API katalogu se nespustí, dokud již není spuštěn kontejner sqldata; To je důležité, protože rozhraní API katalogu musí mít nejprve zprovozněnou databázi serveru SQL Server.</span><span class="sxs-lookup"><span data-stu-id="42fb5-152">When you specify this dependency, the catalog-api container will not start until the sqldata container has already started; this is important because catalog-api needs to have the SQL Server database up and running first.</span></span> <span data-ttu-id="42fb5-153">Tento druh závislosti kontejneru však není dost v mnoha případech, protože Docker kontroluje pouze na úrovni kontejneru.</span><span class="sxs-lookup"><span data-stu-id="42fb5-153">However, this kind of container dependency is not enough in many cases, because Docker checks only at the container level.</span></span> <span data-ttu-id="42fb5-154">Někdy služba (v tomto případě SQL Server) stále není připraven, takže je vhodné implementovat logiku opakování s exponenciální backoff ve vašem mikroslužeb klienta.</span><span class="sxs-lookup"><span data-stu-id="42fb5-154">Sometimes the service (in this case SQL Server) might still not be ready, so it is advisable to implement retry logic with exponential backoff in your client microservices.</span></span> <span data-ttu-id="42fb5-155">Tímto způsobem, pokud kontejner závislostí není připraven na krátkou dobu, aplikace bude stále odolné.</span><span class="sxs-lookup"><span data-stu-id="42fb5-155">That way, if a dependency container is not ready for a short time, the application will still be resilient.</span></span>

- <span data-ttu-id="42fb5-156">Je nakonfigurován tak, aby umožňoval\_přístup k externím serverům: nastavení dalších hostitelů umožňuje přístup k externím serverům nebo počítačům mimo hostitele Dockeru (tj. mimo výchozí virtuální počítač s Linuxem, což je vývojový hostitel Dockeru), například místní instance SERVERU SQL Server ve vývojovém počítači.</span><span class="sxs-lookup"><span data-stu-id="42fb5-156">It is configured to allow access to external servers: the extra\_hosts setting allows you to access external servers or machines outside of the Docker host (that is, outside the default Linux VM, which is a development Docker host), such as a local SQL Server instance on your development PC.</span></span>

<span data-ttu-id="42fb5-157">Existují také další, pokročilejší `docker-compose.yml` nastavení, které budeme diskutovat v následujících částech.</span><span class="sxs-lookup"><span data-stu-id="42fb5-157">There are also other, more advanced `docker-compose.yml` settings that we'll discuss in the following sections.</span></span>

### <a name="using-docker-compose-files-to-target-multiple-environments"></a><span data-ttu-id="42fb5-158">Použití souborů docker-compose k cílení na více prostředí</span><span class="sxs-lookup"><span data-stu-id="42fb5-158">Using docker-compose files to target multiple environments</span></span>

<span data-ttu-id="42fb5-159">Soubory `docker-compose.*.yml` jsou definiční soubory a mohou být použity více infrastruktur, které chápou tento formát.</span><span class="sxs-lookup"><span data-stu-id="42fb5-159">The `docker-compose.*.yml` files are definition files and can be used by multiple infrastructures that understand that format.</span></span> <span data-ttu-id="42fb5-160">Nejjednodušší nástroj je docker-compose příkaz.</span><span class="sxs-lookup"><span data-stu-id="42fb5-160">The most straightforward tool is the docker-compose command.</span></span>

<span data-ttu-id="42fb5-161">Proto pomocí příkazu docker-compose můžete cílit na následující hlavní scénáře.</span><span class="sxs-lookup"><span data-stu-id="42fb5-161">Therefore, by using the docker-compose command you can target the following main scenarios.</span></span>

#### <a name="development-environments"></a><span data-ttu-id="42fb5-162">Vývojová prostředí</span><span class="sxs-lookup"><span data-stu-id="42fb5-162">Development environments</span></span>

<span data-ttu-id="42fb5-163">Při vývoji aplikací je důležité, aby bylo možné spustit aplikaci v izolovaném vývojovém prostředí.</span><span class="sxs-lookup"><span data-stu-id="42fb5-163">When you develop applications, it is important to be able to run an application in an isolated development environment.</span></span> <span data-ttu-id="42fb5-164">Příkaz příkazu příkazu příkazu příkazu příkazu příkazu příkazu příkazu příkazu příkazu příkazu příkazu cli v dockeru můžete použít k vytvoření tohoto prostředí nebo sady Visual Studio, která používá docker-compose pod kryty.</span><span class="sxs-lookup"><span data-stu-id="42fb5-164">You can use the docker-compose CLI command to create that environment or Visual Studio, which uses docker-compose under the covers.</span></span>

<span data-ttu-id="42fb5-165">Soubor docker-compose.yml umožňuje konfigurovat a dokumentovat všechny závislosti služeb vaší aplikace (jiné služby, mezipaměť, databáze, fronty atd.).</span><span class="sxs-lookup"><span data-stu-id="42fb5-165">The docker-compose.yml file allows you to configure and document all your application’s service dependencies (other services, cache, databases, queues, etc.).</span></span> <span data-ttu-id="42fb5-166">Pomocí příkazu cli docker-compose můžete vytvořit a spustit jeden nebo více kontejnerů pro každou závislost pomocí jediného příkazu (docker-compose up).</span><span class="sxs-lookup"><span data-stu-id="42fb5-166">Using the docker-compose CLI command, you can create and start one or more containers for each dependency with a single command (docker-compose up).</span></span>

<span data-ttu-id="42fb5-167">Soubory docker-compose.yml jsou konfigurační soubory interpretované modulem Docker, ale také slouží jako pohodlné soubory dokumentace o složení aplikace s více kontejnery.</span><span class="sxs-lookup"><span data-stu-id="42fb5-167">The docker-compose.yml files are configuration files interpreted by Docker engine but also serve as convenient documentation files about the composition of your multi-container application.</span></span>

#### <a name="testing-environments"></a><span data-ttu-id="42fb5-168">Testovací prostředí</span><span class="sxs-lookup"><span data-stu-id="42fb5-168">Testing environments</span></span>

<span data-ttu-id="42fb5-169">Důležitou součástí procesu průběžného nasazení (CD) nebo průběžné integrace (CI) jsou testy částí a integrační testy.</span><span class="sxs-lookup"><span data-stu-id="42fb5-169">An important part of any continuous deployment (CD) or continuous integration (CI) process are the unit tests and integration tests.</span></span> <span data-ttu-id="42fb5-170">Tyto automatizované testy vyžadují izolované prostředí, takže nejsou ovlivněny uživateli nebo žádné jiné změny v datech aplikace.</span><span class="sxs-lookup"><span data-stu-id="42fb5-170">These automated tests require an isolated environment so they are not impacted by the users or any other change in the application’s data.</span></span>

<span data-ttu-id="42fb5-171">S Docker Compose můžete vytvořit a zničit toto izolované prostředí velmi snadno v několika příkazech z příkazového řádku nebo skriptů, jako jsou následující příkazy:</span><span class="sxs-lookup"><span data-stu-id="42fb5-171">With Docker Compose, you can create and destroy that isolated environment very easily in a few commands from your command prompt or scripts, like the following commands:</span></span>

```console
docker-compose -f docker-compose.yml -f docker-compose-test.override.yml up -d
./run_unit_tests
docker-compose -f docker-compose.yml -f docker-compose.test.override.yml down
```

#### <a name="production-deployments"></a><span data-ttu-id="42fb5-172">Produkční nasazení</span><span class="sxs-lookup"><span data-stu-id="42fb5-172">Production deployments</span></span>

<span data-ttu-id="42fb5-173">Compose můžete také použít k nasazení do vzdáleného modulu Docker Engine.</span><span class="sxs-lookup"><span data-stu-id="42fb5-173">You can also use Compose to deploy to a remote Docker Engine.</span></span> <span data-ttu-id="42fb5-174">Typickým případem je nasazení do jedné instance hostitele Dockeru (jako je produkční virtuální počítač nebo server zřízený pomocí [Počítače dockeru).](https://docs.docker.com/machine/overview/)</span><span class="sxs-lookup"><span data-stu-id="42fb5-174">A typical case is to deploy to a single Docker host instance (like a production VM or server provisioned with [Docker Machine](https://docs.docker.com/machine/overview/)).</span></span>

<span data-ttu-id="42fb5-175">Pokud používáte jiný orchestrator (Azure Service Fabric, Kubernetes atd.), budete muset přidat nastavení nastavení a nastavení konfigurace metadat, jako jsou v docker-compose.yml, ale ve formátu vyžadovaném jiným orchestrator.</span><span class="sxs-lookup"><span data-stu-id="42fb5-175">If you are using any other orchestrator (Azure Service Fabric, Kubernetes, etc.), you might need to add setup and metadata configuration settings like those in docker-compose.yml, but in the format required by the other orchestrator.</span></span>

<span data-ttu-id="42fb5-176">V každém případě docker-compose je pohodlný nástroj a formát metadat pro vývoj, testování a produkční pracovní postupy, i když pracovní postup výroby se může lišit na orchestrátoru, který používáte.</span><span class="sxs-lookup"><span data-stu-id="42fb5-176">In any case, docker-compose is a convenient tool and metadata format for development, testing and production workflows, although the production workflow might vary on the orchestrator you are using.</span></span>

### <a name="using-multiple-docker-compose-files-to-handle-several-environments"></a><span data-ttu-id="42fb5-177">Použití více souborů docker-compose pro zpracování několika prostředí</span><span class="sxs-lookup"><span data-stu-id="42fb5-177">Using multiple docker-compose files to handle several environments</span></span>

<span data-ttu-id="42fb5-178">Při cílení na různá prostředí byste měli použít více souborů pro skládání.</span><span class="sxs-lookup"><span data-stu-id="42fb5-178">When targeting different environments, you should use multiple compose files.</span></span> <span data-ttu-id="42fb5-179">To umožňuje vytvořit více variant konfigurace v závislosti na prostředí.</span><span class="sxs-lookup"><span data-stu-id="42fb5-179">This lets you create multiple configuration variants depending on the environment.</span></span>

#### <a name="overriding-the-base-docker-compose-file"></a><span data-ttu-id="42fb5-180">Přepsání základního souboru docker-compose</span><span class="sxs-lookup"><span data-stu-id="42fb5-180">Overriding the base docker-compose file</span></span>

<span data-ttu-id="42fb5-181">Můžete použít jeden soubor docker-compose.yml jako ve zjednodušených příkladech uvedených v předchozích částech.</span><span class="sxs-lookup"><span data-stu-id="42fb5-181">You could use a single docker-compose.yml file as in the simplified examples shown in previous sections.</span></span> <span data-ttu-id="42fb5-182">To se však nedoporučuje pro většinu aplikací.</span><span class="sxs-lookup"><span data-stu-id="42fb5-182">However, that is not recommended for most applications.</span></span>

<span data-ttu-id="42fb5-183">Ve výchozím nastavení compose čte dva soubory, docker-compose.yml a volitelný docker-compose.override.yml soubor.</span><span class="sxs-lookup"><span data-stu-id="42fb5-183">By default, Compose reads two files, a docker-compose.yml and an optional docker-compose.override.yml file.</span></span> <span data-ttu-id="42fb5-184">Jak je znázorněno na obrázku 6-11, když používáte Visual Studio a povolení podpory Dockeru, Visual Studio také vytvoří další soubor docker-compose.vs.debug.g.yml pro ladění aplikace, můžete se podívat na tento soubor ve složce obj\\Docker\\ v hlavní složce řešení.</span><span class="sxs-lookup"><span data-stu-id="42fb5-184">As shown in Figure 6-11, when you are using Visual Studio and enabling Docker support, Visual Studio also creates an additional docker-compose.vs.debug.g.yml file for debugging the application, you can take a look at this file in folder obj\\Docker\\ in the main solution folder.</span></span>

![Snímek obrazovky se soubory v projektu vytvoření dockeru](./media/multi-container-applications-docker-compose/docker-compose-file-visual-studio.png)

<span data-ttu-id="42fb5-186">**Obrázek 6-11**.</span><span class="sxs-lookup"><span data-stu-id="42fb5-186">**Figure 6-11**.</span></span> <span data-ttu-id="42fb5-187">soubory z docker-compose ve Visual Studiu 2019</span><span class="sxs-lookup"><span data-stu-id="42fb5-187">docker-compose files in Visual Studio 2019</span></span>

<span data-ttu-id="42fb5-188">**docker-compose** struktura souboru projektu:</span><span class="sxs-lookup"><span data-stu-id="42fb5-188">**docker-compose** project file structure:</span></span>

- <span data-ttu-id="42fb5-189">*.dockerignore* - používá se k ignorování souborů</span><span class="sxs-lookup"><span data-stu-id="42fb5-189">*.dockerignore* - used to ignore files</span></span>
- <span data-ttu-id="42fb5-190">*docker-compose.yml* - používá se k komponovat mikroslužby</span><span class="sxs-lookup"><span data-stu-id="42fb5-190">*docker-compose.yml* - used to compose microservices</span></span>
- <span data-ttu-id="42fb5-191">*docker-compose.override.yml* - slouží ke konfiguraci prostředí mikroslužeb</span><span class="sxs-lookup"><span data-stu-id="42fb5-191">*docker-compose.override.yml* - used to configure microservices environment</span></span>

<span data-ttu-id="42fb5-192">Můžete upravit docker-compose soubory s libovolným editorem, jako je Visual Studio Code nebo Sublime, a spustit aplikaci pomocí příkazu docker-compose up.</span><span class="sxs-lookup"><span data-stu-id="42fb5-192">You can edit the docker-compose files with any editor, like Visual Studio Code or Sublime, and run the application with the docker-compose up command.</span></span>

<span data-ttu-id="42fb5-193">Podle konvence obsahuje soubor docker-compose.yml základní konfiguraci a další statická nastavení.</span><span class="sxs-lookup"><span data-stu-id="42fb5-193">By convention, the docker-compose.yml file contains your base configuration and other static settings.</span></span> <span data-ttu-id="42fb5-194">To znamená, že konfigurace služby by se neměla měnit v závislosti na prostředí nasazení, na které cílíte.</span><span class="sxs-lookup"><span data-stu-id="42fb5-194">That means that the service configuration should not change depending on the deployment environment you are targeting.</span></span>

<span data-ttu-id="42fb5-195">Soubor docker-compose.override.yml, jak naznačuje jeho název, obsahuje nastavení konfigurace, která přepíší základní konfiguraci, například konfiguraci, která závisí na prostředí nasazení.</span><span class="sxs-lookup"><span data-stu-id="42fb5-195">The docker-compose.override.yml file, as its name suggests, contains configuration settings that override the base configuration, such as configuration that depends on the deployment environment.</span></span> <span data-ttu-id="42fb5-196">Můžete mít také více přepsání souborů s různými názvy.</span><span class="sxs-lookup"><span data-stu-id="42fb5-196">You can have multiple override files with different names also.</span></span> <span data-ttu-id="42fb5-197">Přepsat soubory obvykle obsahují další informace, které aplikace potřebuje, ale specifické pro prostředí nebo nasazení.</span><span class="sxs-lookup"><span data-stu-id="42fb5-197">The override files usually contain additional information needed by the application but specific to an environment or to a deployment.</span></span>

#### <a name="targeting-multiple-environments"></a><span data-ttu-id="42fb5-198">Cílení na více prostředí</span><span class="sxs-lookup"><span data-stu-id="42fb5-198">Targeting multiple environments</span></span>

<span data-ttu-id="42fb5-199">Typický případ použití je při definování více compose souborů, takže můžete cílit na více prostředí, jako je výroba, pracovní, CI nebo vývoj.</span><span class="sxs-lookup"><span data-stu-id="42fb5-199">A typical use case is when you define multiple compose files so you can target multiple environments, like production, staging, CI, or development.</span></span> <span data-ttu-id="42fb5-200">Chcete-li tyto rozdíly podpořit, můžete vytvořit konfiguraci compose do více souborů, jak je znázorněno na obrázku 6-12.</span><span class="sxs-lookup"><span data-stu-id="42fb5-200">To support these differences, you can split your Compose configuration into multiple files, as shown in Figure 6-12.</span></span>

![Diagram tří souborů docker-compose nastavených na přepsání základního souboru.](./media/multi-container-applications-docker-compose/multiple-docker-compose-files-override-base.png)

<span data-ttu-id="42fb5-202">**Obrázek 6-12**.</span><span class="sxs-lookup"><span data-stu-id="42fb5-202">**Figure 6-12**.</span></span> <span data-ttu-id="42fb5-203">Více souborů docker-compose přepsání hodnot v základním souboru docker-compose.yml</span><span class="sxs-lookup"><span data-stu-id="42fb5-203">Multiple docker-compose files overriding values in the base docker-compose.yml file</span></span>

<span data-ttu-id="42fb5-204">Můžete kombinovat více docker-compose\*.yml soubory pro zpracování různých prostředí.</span><span class="sxs-lookup"><span data-stu-id="42fb5-204">You can combine multiple docker-compose\*.yml files to handle different environments.</span></span> <span data-ttu-id="42fb5-205">Začínáte se základním souborem docker-compose.yml.</span><span class="sxs-lookup"><span data-stu-id="42fb5-205">You start with the base docker-compose.yml file.</span></span> <span data-ttu-id="42fb5-206">Tento základní soubor musí obsahovat základní nebo statické nastavení konfigurace, které se nemění v závislosti na prostředí.</span><span class="sxs-lookup"><span data-stu-id="42fb5-206">This base file has to contain the base or static configuration settings that do not change depending on the environment.</span></span> <span data-ttu-id="42fb5-207">Například eShopOnContainers má následující docker-compose.yml soubor (zjednodušené s menším počtem služeb) jako základní soubor.</span><span class="sxs-lookup"><span data-stu-id="42fb5-207">For example, the eShopOnContainers has the following docker-compose.yml file (simplified with fewer services) as the base file.</span></span>

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

<span data-ttu-id="42fb5-208">Hodnoty v základním souboru docker-compose.yml by se neměly měnit z důvodu různých cílových prostředí nasazení.</span><span class="sxs-lookup"><span data-stu-id="42fb5-208">The values in the base docker-compose.yml file should not change because of different target deployment environments.</span></span>

<span data-ttu-id="42fb5-209">Pokud se například zaměříte na definici služby webmvc, můžete vidět, jak jsou tyto informace téměř stejné bez ohledu na to, na jaké prostředí se můžete zaměřit.</span><span class="sxs-lookup"><span data-stu-id="42fb5-209">If you focus on the webmvc service definition, for instance, you can see how that information is much the same no matter what environment you might be targeting.</span></span> <span data-ttu-id="42fb5-210">Máte následující informace:</span><span class="sxs-lookup"><span data-stu-id="42fb5-210">You have the following information:</span></span>

- <span data-ttu-id="42fb5-211">Název služby: webmvc.</span><span class="sxs-lookup"><span data-stu-id="42fb5-211">The service name: webmvc.</span></span>

- <span data-ttu-id="42fb5-212">Vlastní image kontejneru: eshop / webmvc.</span><span class="sxs-lookup"><span data-stu-id="42fb5-212">The container’s custom image: eshop/webmvc.</span></span>

- <span data-ttu-id="42fb5-213">Příkaz k vytvoření vlastní image Dockeru označující, který dockerfile použít.</span><span class="sxs-lookup"><span data-stu-id="42fb5-213">The command to build the custom Docker image, indicating which Dockerfile to use.</span></span>

- <span data-ttu-id="42fb5-214">Závislosti na jiných službách, takže tento kontejner nelze spustit, dokud ostatní kontejnery závislostí byly spuštěny.</span><span class="sxs-lookup"><span data-stu-id="42fb5-214">Dependencies on other services, so this container does not start until the other dependency containers have started.</span></span>

<span data-ttu-id="42fb5-215">Můžete mít další konfiguraci, ale důležité je, že v základním souboru docker-compose.yml chcete nastavit informace, které jsou běžné v různých prostředích.</span><span class="sxs-lookup"><span data-stu-id="42fb5-215">You can have additional configuration, but the important point is that in the base docker-compose.yml file, you just want to set the information that is common across environments.</span></span> <span data-ttu-id="42fb5-216">Potom v docker-compose.override.yml nebo podobné soubory pro produkční nebo pracovní, měli byste umístit konfiguraci, která je specifická pro každé prostředí.</span><span class="sxs-lookup"><span data-stu-id="42fb5-216">Then in the docker-compose.override.yml or similar files for production or staging, you should place configuration that is specific for each environment.</span></span>

<span data-ttu-id="42fb5-217">Docker-compose.override.yml se obvykle používá pro vývojové prostředí, jako v následujícím příkladu z eShopOnContainers:</span><span class="sxs-lookup"><span data-stu-id="42fb5-217">Usually, the docker-compose.override.yml is used for your development environment, as in the following example from eShopOnContainers:</span></span>

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

<span data-ttu-id="42fb5-218">V tomto příkladu konfigurace přepsání vývoje zpřístupňuje některé porty hostiteli, definuje proměnné prostředí s adresami URL přesměrování a určuje připojovací řetězce pro vývojové prostředí.</span><span class="sxs-lookup"><span data-stu-id="42fb5-218">In this example, the development override configuration exposes some ports to the host, defines environment variables with redirect URLs, and specifies connection strings for the development environment.</span></span> <span data-ttu-id="42fb5-219">Tato nastavení jsou pouze pro vývojové prostředí.</span><span class="sxs-lookup"><span data-stu-id="42fb5-219">These settings are all just for the development environment.</span></span>

<span data-ttu-id="42fb5-220">Při spuštění `docker-compose up` (nebo spuštění z visual studia), příkaz přečte přepsání automaticky, jako by byly sloučení obou souborů.</span><span class="sxs-lookup"><span data-stu-id="42fb5-220">When you run `docker-compose up` (or launch it from Visual Studio), the command reads the overrides automatically as if it were merging both files.</span></span>

<span data-ttu-id="42fb5-221">Předpokládejme, že chcete jiný soubor Compose pro produkční prostředí s různými konfiguračními hodnotami, porty nebo připojovacími řetězci.</span><span class="sxs-lookup"><span data-stu-id="42fb5-221">Suppose that you want another Compose file for the production environment, with different configuration values, ports, or connection strings.</span></span> <span data-ttu-id="42fb5-222">Můžete vytvořit jiný soubor přepsání, například soubor pojmenovaný `docker-compose.prod.yml` s různými nastaveními a proměnnými prostředí.</span><span class="sxs-lookup"><span data-stu-id="42fb5-222">You can create another override file, like file named `docker-compose.prod.yml` with different settings and environment variables.</span></span> <span data-ttu-id="42fb5-223">Tento soubor může být uložen v jiném úložišti Git nebo spravován a zabezpečen jiným týmem.</span><span class="sxs-lookup"><span data-stu-id="42fb5-223">That file might be stored in a different Git repo or managed and secured by a different team.</span></span>

#### <a name="how-to-deploy-with-a-specific-override-file"></a><span data-ttu-id="42fb5-224">Jak nasadit s určitým přepsat soubor</span><span class="sxs-lookup"><span data-stu-id="42fb5-224">How to deploy with a specific override file</span></span>

<span data-ttu-id="42fb5-225">Chcete-li použít více přepsání souborů nebo přepsat soubor s jiným názvem, můžete použít -f možnost s příkazem docker-compose a určit soubory.</span><span class="sxs-lookup"><span data-stu-id="42fb5-225">To use multiple override files, or an override file with a different name, you can use the -f option with the docker-compose command and specify the files.</span></span> <span data-ttu-id="42fb5-226">Vytvoří slučovací soubory v pořadí, v jakém jsou určeny na příkazovém řádku.</span><span class="sxs-lookup"><span data-stu-id="42fb5-226">Compose merges files in the order they are specified on the command line.</span></span> <span data-ttu-id="42fb5-227">Následující příklad ukazuje, jak nasadit s přepsat soubory.</span><span class="sxs-lookup"><span data-stu-id="42fb5-227">The following example shows how to deploy with override files.</span></span>

```console
docker-compose -f docker-compose.yml -f docker-compose.prod.yml up -d
```

#### <a name="using-environment-variables-in-docker-compose-files"></a><span data-ttu-id="42fb5-228">Použití proměnných prostředí v souborech docker-compose</span><span class="sxs-lookup"><span data-stu-id="42fb5-228">Using environment variables in docker-compose files</span></span>

<span data-ttu-id="42fb5-229">Je vhodné, zejména v produkčním prostředí, aby bylo možné získat informace o konfiguraci z proměnných prostředí, jak jsme ukázali v předchozích příkladech.</span><span class="sxs-lookup"><span data-stu-id="42fb5-229">It is convenient, especially in production environments, to be able to get configuration information from environment variables, as we have shown in previous examples.</span></span> <span data-ttu-id="42fb5-230">Proměnnou prostředí můžete odkazovat na soubor y docker-compose pomocí syntaxe ${MY\_VAR}.</span><span class="sxs-lookup"><span data-stu-id="42fb5-230">You can reference an environment variable in your docker-compose files using the syntax ${MY\_VAR}.</span></span> <span data-ttu-id="42fb5-231">Následující řádek ze souboru docker-compose.prod.yml ukazuje, jak odkazovat na hodnotu proměnné prostředí.</span><span class="sxs-lookup"><span data-stu-id="42fb5-231">The following line from a docker-compose.prod.yml file shows how to reference the value of an environment variable.</span></span>

```yml
IdentityUrl=http://${ESHOP_PROD_EXTERNAL_DNS_NAME_OR_IP}:5105
```

<span data-ttu-id="42fb5-232">Proměnné prostředí jsou vytvářeny a inicializovány různými způsoby v závislosti na hostitelském prostředí (Linux, Windows, cloudový cluster atd.).</span><span class="sxs-lookup"><span data-stu-id="42fb5-232">Environment variables are created and initialized in different ways, depending on your host environment (Linux, Windows, Cloud cluster, etc.).</span></span> <span data-ttu-id="42fb5-233">Pohodlným přístupem je však použití souboru ENV.</span><span class="sxs-lookup"><span data-stu-id="42fb5-233">However, a convenient approach is to use an .env file.</span></span> <span data-ttu-id="42fb5-234">Soubory docker-compose podporují deklarování výchozích proměnných prostředí v souboru ENV.</span><span class="sxs-lookup"><span data-stu-id="42fb5-234">The docker-compose files support declaring default environment variables in the .env file.</span></span> <span data-ttu-id="42fb5-235">Tyto hodnoty pro proměnné prostředí jsou výchozí hodnoty.</span><span class="sxs-lookup"><span data-stu-id="42fb5-235">These values for the environment variables are the default values.</span></span> <span data-ttu-id="42fb5-236">Ale mohou být přepsány hodnotami, které jste definovali v každém z vašich prostředí (hostitelského operačního systému nebo proměnných prostředí z clusteru).</span><span class="sxs-lookup"><span data-stu-id="42fb5-236">But they can be overridden by the values you might have defined in each of your environments (host OS or environment variables from your cluster).</span></span> <span data-ttu-id="42fb5-237">Tento soubor ENV umístíte do složky, ze které je příkaz docker-compose proveden.</span><span class="sxs-lookup"><span data-stu-id="42fb5-237">You place this .env file in the folder where the docker-compose command is executed from.</span></span>

<span data-ttu-id="42fb5-238">Následující příklad ukazuje soubor ENV, jako je soubor [ENV](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/.env) pro aplikaci eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="42fb5-238">The following example shows an .env file like the [.env](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/.env) file for the eShopOnContainers application.</span></span>

```sh
# .env file

ESHOP_EXTERNAL_DNS_NAME_OR_IP=localhost

ESHOP_PROD_EXTERNAL_DNS_NAME_OR_IP=10.121.122.92
```

<span data-ttu-id="42fb5-239">Docker-compose očekává, že každý řádek v souboru \<ENV bude v hodnotě\>=\<\>proměnné formátu .</span><span class="sxs-lookup"><span data-stu-id="42fb5-239">Docker-compose expects each line in an .env file to be in the format \<variable\>=\<value\>.</span></span>

<span data-ttu-id="42fb5-240">Hodnoty nastavené v prostředí za běhu vždy přepíší hodnoty definované uvnitř souboru ENV.</span><span class="sxs-lookup"><span data-stu-id="42fb5-240">The values set in the run-time environment always override the values defined inside the .env file.</span></span> <span data-ttu-id="42fb5-241">Podobným způsobem hodnoty předané prostřednictvím argumentů příkazového řádku také přepíší výchozí hodnoty nastavené v souboru ENV.</span><span class="sxs-lookup"><span data-stu-id="42fb5-241">In a similar way, values passed via command-line arguments also override the default values set in the .env file.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="42fb5-242">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="42fb5-242">Additional resources</span></span>

- <span data-ttu-id="42fb5-243">**Přehled dockerového komponu** </span><span class="sxs-lookup"><span data-stu-id="42fb5-243">**Overview of Docker Compose** </span></span>\
    <https://docs.docker.com/compose/overview/>

- <span data-ttu-id="42fb5-244">**Více compose souborů** </span><span class="sxs-lookup"><span data-stu-id="42fb5-244">**Multiple Compose files** </span></span>\
    [https://docs.docker.com/compose/extends/\#multiple-compose-files](https://docs.docker.com/compose/extends/#multiple-compose-files)

### <a name="building-optimized-aspnet-core-docker-images"></a><span data-ttu-id="42fb5-245">Vytváření optimalizovaných ASP.NET image Core Dockeru</span><span class="sxs-lookup"><span data-stu-id="42fb5-245">Building optimized ASP.NET Core Docker images</span></span>

<span data-ttu-id="42fb5-246">Pokud zkoumáte Docker a .NET Core na zdroje na Internetu, najdete Dockerfiles, které ukazují jednoduchost vytváření image Docker u kopírování zdroje do kontejneru.</span><span class="sxs-lookup"><span data-stu-id="42fb5-246">If you are exploring Docker and .NET Core on sources on the Internet, you will find Dockerfiles that demonstrate the simplicity of building a Docker image by copying your source into a container.</span></span> <span data-ttu-id="42fb5-247">Tyto příklady naznačují, že pomocí jednoduché konfigurace můžete mít image Dockeru s prostředím zabaleným s vaší aplikací.</span><span class="sxs-lookup"><span data-stu-id="42fb5-247">These examples suggest that by using a simple configuration, you can have a Docker image with the environment packaged with your application.</span></span> <span data-ttu-id="42fb5-248">Následující příklad ukazuje jednoduchý Dockerfile v této žíře.</span><span class="sxs-lookup"><span data-stu-id="42fb5-248">The following example shows a simple Dockerfile in this vein.</span></span>

```Dockerfile
FROM mcr.microsoft.com/dotnet/core/sdk:3.1
WORKDIR /app
ENV ASPNETCORE_URLS http://+:80
EXPOSE 80
COPY . .
RUN dotnet restore
ENTRYPOINT ["dotnet", "run"]
```

<span data-ttu-id="42fb5-249">Dockerfile jako je tento bude fungovat.</span><span class="sxs-lookup"><span data-stu-id="42fb5-249">A Dockerfile like this will work.</span></span> <span data-ttu-id="42fb5-250">Můžete však podstatně optimalizovat obrázky, zejména produkční obrázky.</span><span class="sxs-lookup"><span data-stu-id="42fb5-250">However, you can substantially optimize your images, especially your production images.</span></span>

<span data-ttu-id="42fb5-251">V kontejneru a mikroslužeb modelu neustále spouštíkontejnery.</span><span class="sxs-lookup"><span data-stu-id="42fb5-251">In the container and microservices model, you are constantly starting containers.</span></span> <span data-ttu-id="42fb5-252">Typický způsob použití kontejnerů nerestartuje kontejner spánku, protože kontejner je na jedno použití.</span><span class="sxs-lookup"><span data-stu-id="42fb5-252">The typical way of using containers does not restart a sleeping container, because the container is disposable.</span></span> <span data-ttu-id="42fb5-253">Orchestratory (jako Kubernetes a Azure Service Fabric) jednoduše vytvořit nové instance ibi.</span><span class="sxs-lookup"><span data-stu-id="42fb5-253">Orchestrators (like Kubernetes and Azure Service Fabric) simply create new instances of images.</span></span> <span data-ttu-id="42fb5-254">To znamená, že budete muset optimalizovat předkompilací aplikace, když je sestavena, takže proces vytváření instancí bude rychlejší.</span><span class="sxs-lookup"><span data-stu-id="42fb5-254">What this means is that you would need to optimize by precompiling the application when it is built so the instantiation process will be faster.</span></span> <span data-ttu-id="42fb5-255">Při spuštění kontejneru by měl být připraven ke spuštění.</span><span class="sxs-lookup"><span data-stu-id="42fb5-255">When the container is started, it should be ready to run.</span></span> <span data-ttu-id="42fb5-256">Neměli byste obnovovat a kompilovat za běhu, pomocí `dotnet restore` a `dotnet build` příkazy z dotnet CLI, které, jak vidíte v mnoha blogu o .NET Core a Docker.</span><span class="sxs-lookup"><span data-stu-id="42fb5-256">You should not restore and compile at run time, using `dotnet restore` and `dotnet build` commands from the dotnet CLI that, as you see in many blog posts about .NET Core and Docker.</span></span>

<span data-ttu-id="42fb5-257">Tým .NET odvádí důležitou práci, aby vytvořil rozhraní .NET Core a ASP.NET Core jako rámec optimalizovaný pro kontejner.</span><span class="sxs-lookup"><span data-stu-id="42fb5-257">The .NET team has been doing important work to make .NET Core and ASP.NET Core a container-optimized framework.</span></span> <span data-ttu-id="42fb5-258">Nejen, že je .NET Core lehký rámec s malou paměťovou stopu; tým se zaměřil na optimalizované image Dockeru pro tři hlavní scénáře a publikoval je v registru Docker Hub u *dotnet/core*, počínaje verzí 2.1:</span><span class="sxs-lookup"><span data-stu-id="42fb5-258">Not only is .NET Core a lightweight framework with a small memory footprint; the team has focused on optimized Docker images for three main scenarios and published them in the Docker Hub registry at *dotnet/core*, beginning with version 2.1:</span></span>

1. <span data-ttu-id="42fb5-259">**Vývoj**: Kde je prioritou schopnost rychle iterate a ladění změn a kde velikost je sekundární.</span><span class="sxs-lookup"><span data-stu-id="42fb5-259">**Development**: Where the priority is the ability to quickly iterate and debug changes, and where size is secondary.</span></span>

2. <span data-ttu-id="42fb5-260">**Sestavení**: Prioritou je kompilace aplikace a zahrnuje binární soubory a další závislosti pro optimalizaci binárních souborů.</span><span class="sxs-lookup"><span data-stu-id="42fb5-260">**Build**: The priority is compiling the application and includes binaries and other dependencies to optimize binaries.</span></span>

3. <span data-ttu-id="42fb5-261">**Výroba**: Kde je fokus rychlé nasazení a spuštění kontejnerů, takže tyto obrázky jsou omezeny na binární soubory a obsah potřebný ke spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="42fb5-261">**Production**: Where the focus is fast deploying and starting of containers, so these images are limited to the binaries and the content needed to run the application.</span></span>

<span data-ttu-id="42fb5-262">K dosažení tohoto cíle poskytuje tým .NET čtyři základní varianty v [dotnet/core](https://hub.docker.com/_/microsoft-dotnet-core/) (v Docker Hubu):</span><span class="sxs-lookup"><span data-stu-id="42fb5-262">To achieve this, the .NET team is providing four basic variants in [dotnet/core](https://hub.docker.com/_/microsoft-dotnet-core/) (at Docker Hub):</span></span>

1. <span data-ttu-id="42fb5-263">**sdk**: pro vývoj a sestavení scénářů</span><span class="sxs-lookup"><span data-stu-id="42fb5-263">**sdk**: for development and build scenarios</span></span>
1. <span data-ttu-id="42fb5-264">**aspnet**: pro ASP.NET produkční scénáře</span><span class="sxs-lookup"><span data-stu-id="42fb5-264">**aspnet**: for ASP.NET production scenarios</span></span>
1. <span data-ttu-id="42fb5-265">**runtime**: pro produkční scénáře rozhraní .NET</span><span class="sxs-lookup"><span data-stu-id="42fb5-265">**runtime**: for .NET production scenarios</span></span>
1. <span data-ttu-id="42fb5-266">**runtime-deps**: pro produkční scénáře [samostatných aplikací](../../../core/deploying/index.md#publish-self-contained).</span><span class="sxs-lookup"><span data-stu-id="42fb5-266">**runtime-deps**: for production scenarios of [self-contained applications](../../../core/deploying/index.md#publish-self-contained).</span></span>

<span data-ttu-id="42fb5-267">Pro rychlejší spuštění, runtime obrázky také\_automaticky nastavit aspnetcore adresy URL na port 80 a použít Ngen vytvořit nativní image cache sestavení.</span><span class="sxs-lookup"><span data-stu-id="42fb5-267">For faster startup, runtime images also automatically set aspnetcore\_urls to port 80 and use Ngen to create a native image cache of assemblies.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="42fb5-268">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="42fb5-268">Additional resources</span></span>

- <span data-ttu-id="42fb5-269">**Vytváření optimalizovaných imitovaných imitacích Dockeru s ASP.NET jádrem**</span><span class="sxs-lookup"><span data-stu-id="42fb5-269">**Building Optimized Docker Images with ASP.NET Core**</span></span>  
  <https://docs.microsoft.com/archive/blogs/stevelasker/building-optimized-docker-images-with-asp-net-core>

- <span data-ttu-id="42fb5-270">**Vytváření imagí Dockeru pro aplikace .NET Core**</span><span class="sxs-lookup"><span data-stu-id="42fb5-270">**Building Docker Images for .NET Core Applications**</span></span>  
  [https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images](/aspnet/core/host-and-deploy/docker/building-net-docker-images)

> [!div class="step-by-step"]
> <span data-ttu-id="42fb5-271">[Předchozí](data-driven-crud-microservice.md)
> [další](database-server-container.md)</span><span class="sxs-lookup"><span data-stu-id="42fb5-271">[Previous](data-driven-crud-microservice.md)
[Next](database-server-container.md)</span></span>
