---
title: Sestavování aplikací ASP.NET Core nasazených jako kontejnery Linux do clusterů AKS/Kubernetes
description: Životní cyklus kontejnerizované aplikace Dockeru s platformou a nástroji Microsoft
ms.date: 08/06/2020
ms.openlocfilehash: 4b04e5d56c73918c665ad6e2825205870aac9606
ms.sourcegitcommit: ef50c99928183a0bba75e07b9f22895cd4c480f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/07/2020
ms.locfileid: "87916453"
---
# <a name="build-aspnet-core-applications-deployed-as-linux-containers-into-an-akskubernetes-orchestrator"></a><span data-ttu-id="7e4ca-103">Sestavování aplikací ASP.NET Core nasazených jako kontejnery Linux do nástroje AKS/Kubernetes Orchestrator</span><span class="sxs-lookup"><span data-stu-id="7e4ca-103">Build ASP.NET Core applications deployed as Linux containers into an AKS/Kubernetes orchestrator</span></span>

<span data-ttu-id="7e4ca-104">Azure Kubernetes Services (AKS) jsou spravované služby Kubernetes orchestrace v Azure, které zjednodušují nasazení a správu kontejnerů.</span><span class="sxs-lookup"><span data-stu-id="7e4ca-104">Azure Kubernetes Services (AKS) is Azure's managed Kubernetes orchestrations services that simplify container deployment and management.</span></span>

<span data-ttu-id="7e4ca-105">AKS hlavní funkce:</span><span class="sxs-lookup"><span data-stu-id="7e4ca-105">AKS main features are:</span></span>

- <span data-ttu-id="7e4ca-106">Rovina řízení hostovaná v Azure</span><span class="sxs-lookup"><span data-stu-id="7e4ca-106">An Azure-hosted control plane</span></span>
- <span data-ttu-id="7e4ca-107">Automatizované upgrady</span><span class="sxs-lookup"><span data-stu-id="7e4ca-107">Automated upgrades</span></span>
- <span data-ttu-id="7e4ca-108">Samoopravování</span><span class="sxs-lookup"><span data-stu-id="7e4ca-108">Self-healing</span></span>
- <span data-ttu-id="7e4ca-109">Uživatelsky konfigurovatelné škálování</span><span class="sxs-lookup"><span data-stu-id="7e4ca-109">User-configurable scaling</span></span>
- <span data-ttu-id="7e4ca-110">Jednodušší uživatelské prostředí pro vývojáře i pro operátory clusterů.</span><span class="sxs-lookup"><span data-stu-id="7e4ca-110">Simpler user experience for both developers and cluster operators.</span></span>

<span data-ttu-id="7e4ca-111">Následující příklady Prozkoumejte vytvoření aplikace ASP.NET Core 3,1, která běží na platformě Linux a nasadí do clusteru AKS v Azure, zatímco vývoj se provádí pomocí sady Visual Studio 2019.</span><span class="sxs-lookup"><span data-stu-id="7e4ca-111">The following examples explore the creation of an ASP.NET Core 3.1 application that runs on Linux and deploys to an AKS Cluster in Azure, while development is done using Visual Studio 2019.</span></span>

## <a name="creating-the-aspnet-core-project-using-visual-studio-2019"></a><span data-ttu-id="7e4ca-112">Vytvoření projektu ASP.NET Core pomocí sady Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="7e4ca-112">Creating the ASP.NET Core Project using Visual Studio 2019</span></span>

<span data-ttu-id="7e4ca-113">ASP.NET Core je vývojová platforma pro obecné účely udržovaná Microsoftem a komunitou .NET na GitHubu.</span><span class="sxs-lookup"><span data-stu-id="7e4ca-113">ASP.NET Core is a general-purpose development platform maintained by Microsoft and the .NET community on GitHub.</span></span> <span data-ttu-id="7e4ca-114">Je to podpora pro různé platformy, Windows, macOS a Linux a dá se použít v scénářích zařízení, Cloud a integrovaných a IoT.</span><span class="sxs-lookup"><span data-stu-id="7e4ca-114">It's cross-platform, supporting Windows, macOS and Linux, and can be used in device, cloud, and embedded/IoT scenarios.</span></span>

<span data-ttu-id="7e4ca-115">V tomto příkladu se používá několik jednoduchých projektů založených na šablonách sady Visual Studio, takže nepotřebujete mít spoustu dalších znalostí pro vytvoření ukázky.</span><span class="sxs-lookup"><span data-stu-id="7e4ca-115">This example uses a couple of simple projects based on Visual Studio templates, so you don't need much additional knowledge to create the sample.</span></span> <span data-ttu-id="7e4ca-116">Projekt je třeba vytvořit pomocí standardní šablony, která obsahuje všechny prvky pro spuštění malého projektu s REST API a webovou aplikací se stránkami Razor pomocí technologie ASP.NET Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="7e4ca-116">You only have to create the project using a standard template that includes all the elements to run a small project with a REST API and a Web App with Razor pages, using ASP.NET Core 3.1 technology.</span></span>

![Přidejte nové okno projektu v aplikaci Visual Studio a vyberte ASP.NET Core webové aplikace.](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/create-aspnet-core-application.png)

<span data-ttu-id="7e4ca-118">**Obrázek 4-35**.</span><span class="sxs-lookup"><span data-stu-id="7e4ca-118">**Figure 4-35**.</span></span> <span data-ttu-id="7e4ca-119">Vytvoření webové aplikace v ASP.NET Core v aplikaci Visual Studio 2019.</span><span class="sxs-lookup"><span data-stu-id="7e4ca-119">Creating an ASP.NET Core Web Application in Visual Studio 2019.</span></span>

<span data-ttu-id="7e4ca-120">Chcete-li vytvořit ukázkový projekt v aplikaci Visual Studio, vyberte **soubor**  >  **Nový**  >  **projekt**, vyberte typ **webového** projektu a poté šablonu **ASP.NET Core webové aplikace** .</span><span class="sxs-lookup"><span data-stu-id="7e4ca-120">To create the sample project in Visual Studio, select **File** > **New** > **Project**, select the **Web** project type and then the **ASP.NET Core Web Application** template.</span></span> <span data-ttu-id="7e4ca-121">Šablonu můžete vyhledat také v případě, že ji potřebujete.</span><span class="sxs-lookup"><span data-stu-id="7e4ca-121">You can also search for the template if you need it.</span></span>

<span data-ttu-id="7e4ca-122">Pak zadejte název a umístění aplikace, jak je znázorněno na následujícím obrázku.</span><span class="sxs-lookup"><span data-stu-id="7e4ca-122">Then enter the application name and location as shown in the next image.</span></span>

![Zadejte název projektu a jeho umístění.](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/enter-project-name-and-location.png)

<span data-ttu-id="7e4ca-124">**Obrázek 4-36**.</span><span class="sxs-lookup"><span data-stu-id="7e4ca-124">**Figure 4-36**.</span></span> <span data-ttu-id="7e4ca-125">Zadejte název projektu a umístění v aplikaci Visual Studio 2019.</span><span class="sxs-lookup"><span data-stu-id="7e4ca-125">Enter the project name and location in Visual Studio 2019.</span></span>

<span data-ttu-id="7e4ca-126">Ověřte, že jste vybrali ASP.NET Core 3,1 jako rozhraní.</span><span class="sxs-lookup"><span data-stu-id="7e4ca-126">Verify that you've selected ASP.NET Core 3.1 as the framework.</span></span> <span data-ttu-id="7e4ca-127">Rozhraní .NET Core 3,1 je součástí nejnovější verze sady Visual Studio 2019 a při instalaci sady Visual Studio je automaticky nainstalováno a nakonfigurováno.</span><span class="sxs-lookup"><span data-stu-id="7e4ca-127">.NET Core 3.1 is included in the latest release of Visual Studio 2019 and is automatically installed and configured for you when you install Visual Studio.</span></span>

![Dialog sady Visual Studio pro výběr typu ASP.NET Core webové aplikace s vybranou možností rozhraní API.](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/create-web-api-application.png)

<span data-ttu-id="7e4ca-129">**Obrázek 4-37**.</span><span class="sxs-lookup"><span data-stu-id="7e4ca-129">**Figure 4-37**.</span></span> <span data-ttu-id="7e4ca-130">Výběr typu projektu ASP.NET CORE 3,1 a webového rozhraní API</span><span class="sxs-lookup"><span data-stu-id="7e4ca-130">Selecting ASP.NET CORE 3.1 and Web API project type</span></span>

<span data-ttu-id="7e4ca-131">Podpora Docker není teď zapnutá, takže ji můžete zobrazit až po vytvoření projektu.</span><span class="sxs-lookup"><span data-stu-id="7e4ca-131">Notice Docker support is not enabled now, just to show it can be done after project creation.</span></span>

<span data-ttu-id="7e4ca-132">Pokud máte předchozí verzi rozhraní .NET Core, můžete si stáhnout a nainstalovat verzi 3,1 z <https://dotnet.microsoft.com/download> .</span><span class="sxs-lookup"><span data-stu-id="7e4ca-132">If you have any previous version of .NET Core, you can download and install the 3.1 version from <https://dotnet.microsoft.com/download>.</span></span>

<span data-ttu-id="7e4ca-133">Pokud se chcete podívat, jak se váš projekt stane ukotvovat, můžete teď přidat podporu Docker.</span><span class="sxs-lookup"><span data-stu-id="7e4ca-133">To show you can "Dockerize" your project at any time, you'll add Docker support now.</span></span> <span data-ttu-id="7e4ca-134">V Průzkumník řešení klikněte pravým tlačítkem myši na uzel projektu a v místní nabídce vyberte **Přidat**  >  **podporu Docker** .</span><span class="sxs-lookup"><span data-stu-id="7e4ca-134">So right-click on the project node in Solution Explorer and select **Add** > **Docker support** on the context menu.</span></span>

![Možnost místní nabídky pro přidání podpory Docker do existujícího projektu: klikněte pravým tlačítkem (v projektu) > přidat podporu > Docker.](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/add-docker-support-to-project.png)

<span data-ttu-id="7e4ca-136">**Obrázek 4-38**.</span><span class="sxs-lookup"><span data-stu-id="7e4ca-136">**Figure 4-38**.</span></span> <span data-ttu-id="7e4ca-137">Přidání podpory Docker do existujícího projektu</span><span class="sxs-lookup"><span data-stu-id="7e4ca-137">Adding Docker support to an existing project</span></span>

<span data-ttu-id="7e4ca-138">Pokud chcete dokončit přidávání podpory Docker, můžete zvolit Windows nebo Linux.</span><span class="sxs-lookup"><span data-stu-id="7e4ca-138">To complete adding Docker support, you can choose Windows or Linux.</span></span> <span data-ttu-id="7e4ca-139">V takovém případě vyberte **Linux**.</span><span class="sxs-lookup"><span data-stu-id="7e4ca-139">In this case, select **Linux**.</span></span>

![Dialog možností pro výběr cílového OS pro souboru Dockerfile.](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/select-linux-docker-support.png)

<span data-ttu-id="7e4ca-141">**Obrázek 4-39**.</span><span class="sxs-lookup"><span data-stu-id="7e4ca-141">**Figure 4-39**.</span></span> <span data-ttu-id="7e4ca-142">Výběr kontejnerů Linux.</span><span class="sxs-lookup"><span data-stu-id="7e4ca-142">Selecting Linux containers.</span></span>

<span data-ttu-id="7e4ca-143">V těchto jednoduchých krocích máte aplikaci ASP.NET Core 3,1 běžící v kontejneru Linux.</span><span class="sxs-lookup"><span data-stu-id="7e4ca-143">With these simple steps, you have your ASP.NET Core 3.1 application running on a Linux container.</span></span>

<span data-ttu-id="7e4ca-144">Podobným způsobem můžete také přidat velmi jednoduchý projekt **WebApp** (obrázek 4-40) pro využívání koncového bodu webového rozhraní API, i když zde podrobnosti nejsou popsané.</span><span class="sxs-lookup"><span data-stu-id="7e4ca-144">In a similar way, you can also add a very simple **WebApp** project (Figure 4-40) to consume the web API endpoint, although the details are not discussed here.</span></span>

<span data-ttu-id="7e4ca-145">Potom přidáte podporu nástroje Orchestrator pro projekt **WebApi** , jak je uvedeno dále, v imagi 4-40.</span><span class="sxs-lookup"><span data-stu-id="7e4ca-145">After that, you add orchestrator support for your **WebApi** project as shown next, in image 4-40.</span></span>

![Přidání podpory nástroje Orchestrator do projektu WebApi](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/add-orchestrator-support.png)

<span data-ttu-id="7e4ca-147">**Obrázek 4-40**.</span><span class="sxs-lookup"><span data-stu-id="7e4ca-147">**Figure 4-40**.</span></span> <span data-ttu-id="7e4ca-148">Do projektu *WebApi* se přidává podpora nástroje Orchestrator.</span><span class="sxs-lookup"><span data-stu-id="7e4ca-148">Adding orchestrator support to *WebApi* project.</span></span>

<span data-ttu-id="7e4ca-149">Když zvolíte `Docker Compose` možnost, která je pro místní vývoj vhodná, Visual Studio přidá do souboru Docker-Docker projekt, jak je znázorněno na obrázku 4-41.</span><span class="sxs-lookup"><span data-stu-id="7e4ca-149">When you choose the `Docker Compose` option, which is fine for local development, Visual Studio adds the docker-compose project, with the docker-compose files as shown in image 4-41.</span></span>

![Docker – sestavení přidané do řešení](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/docker-compose-project-in-visual-studio.png)

<span data-ttu-id="7e4ca-151">**Obrázek 4-41**.</span><span class="sxs-lookup"><span data-stu-id="7e4ca-151">**Figure 4-41**.</span></span> <span data-ttu-id="7e4ca-152">Do projektu *WebApi* se přidává podpora nástroje Orchestrator.</span><span class="sxs-lookup"><span data-stu-id="7e4ca-152">Adding orchestrator support to *WebApi* project.</span></span>

<span data-ttu-id="7e4ca-153">Počáteční přidané soubory jsou podobné těm:</span><span class="sxs-lookup"><span data-stu-id="7e4ca-153">The initial files added are similar to these ones:</span></span>

`docker-compose.yml`

```yml
version: "3.4"

services:
  webapi:
    image: ${DOCKER_REGISTRY-}webapi
    build:
      context: .
      dockerfile: WebApi/Dockerfile

  webapp:
    image: ${DOCKER_REGISTRY-}webapp
    build:
      context: .
      dockerfile: WebApp/Dockerfile
```

`docker-compose.override.yml`

```yml
version: "3.4"

services:
  webapi:
    environment:
      - ASPNETCORE_ENVIRONMENT=Development
      - ASPNETCORE_URLS=https://+:443;http://+:80
    ports:
      - "80"
      - "443"
    volumes:
      - ${APPDATA}/Microsoft/UserSecrets:/root/.microsoft/usersecrets:ro
      - ${APPDATA}/ASP.NET/Https:/root/.aspnet/https:ro
  webapp:
    environment:
      - ASPNETCORE_ENVIRONMENT=Development
      - ASPNETCORE_URLS=https://+:443;http://+:80
    ports:
      - "80"
      - "443"
    volumes:
      - ${APPDATA}/Microsoft/UserSecrets:/root/.microsoft/usersecrets:ro
      - ${APPDATA}/ASP.NET/Https:/root/.aspnet/https:ro
```

<span data-ttu-id="7e4ca-154">Pokud chcete, aby aplikace běžela s Docker Compose stačí provést několik vylepšení`docker-compose.override.yml`</span><span class="sxs-lookup"><span data-stu-id="7e4ca-154">To have you app running with Docker Compose you just have to make a few tweaks to `docker-compose.override.yml`</span></span>

```yml
services:
  webapi:
    #...
    ports:
      - "51080:80"
      - "51443:443"
    #...
  webapp:
    environment:
      #...
      - WebApiBaseAddress=http://webapi
    ports:
      - "50080:80"
      - "50443:443"
    #...
```

<span data-ttu-id="7e4ca-155">Nyní můžete spustit aplikaci pomocí klávesy **F5** nebo pomocí tlačítka **Přehrát** nebo **stisknutím klávesy CTRL + F5** vybrat projekt Docker – sestavení, jak je znázorněno na obrázku 4-42.</span><span class="sxs-lookup"><span data-stu-id="7e4ca-155">Now you can run your application with **F5** key, or by using the **Play** button, or the **Ctrl+F5** key, selecting the docker-compose project, as shown in image 4-42.</span></span>

![Spuštění aplikace Docker – sestavení projektu se sadou Visual Studio](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/running-docker-compose-with-visual-studio.png)

<span data-ttu-id="7e4ca-157">**Obrázek 4-42**.</span><span class="sxs-lookup"><span data-stu-id="7e4ca-157">**Figure 4-42**.</span></span> <span data-ttu-id="7e4ca-158">Do projektu *WebApi* se přidává podpora nástroje Orchestrator.</span><span class="sxs-lookup"><span data-stu-id="7e4ca-158">Adding orchestrator support to *WebApi* project.</span></span>

<span data-ttu-id="7e4ca-159">Při spuštění aplikace Docker-tváře, která je vysvětlena, získáte:</span><span class="sxs-lookup"><span data-stu-id="7e4ca-159">When running the docker-compose application as explained, you get:</span></span>

1. <span data-ttu-id="7e4ca-160">Obrázky sestavené a kontejnery vytvořené podle souboru Docker – pro sestavení.</span><span class="sxs-lookup"><span data-stu-id="7e4ca-160">The images built and containers created as per the docker-compose file.</span></span>
2. <span data-ttu-id="7e4ca-161">Prohlížeč je otevřen v adrese konfigurované v dialogovém okně vlastnosti `docker-compose` projektu.</span><span class="sxs-lookup"><span data-stu-id="7e4ca-161">The browser open in the address configured in the "Properties" dialog for the `docker-compose` project.</span></span>
3. <span data-ttu-id="7e4ca-162">Okno **kontejneru** otevřené (v aplikaci Visual Studio 2019 verze 16,4 a novější).</span><span class="sxs-lookup"><span data-stu-id="7e4ca-162">The **Container** window open (in Visual Studio 2019 version 16.4 and later).</span></span>
4. <span data-ttu-id="7e4ca-163">Podpora ladicího programu pro všechny projekty v řešení, jak je znázorněno na následujících obrázcích.</span><span class="sxs-lookup"><span data-stu-id="7e4ca-163">Debugger support for all projects in the solution, as shown in the following images.</span></span>

<span data-ttu-id="7e4ca-164">Otevřený prohlížeč:</span><span class="sxs-lookup"><span data-stu-id="7e4ca-164">Browser opened:</span></span>

![Zobrazení prohlížeče s webovou aplikací spuštěnou](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/browser-opened.png)

<span data-ttu-id="7e4ca-166">**Obrázek 4-43**.</span><span class="sxs-lookup"><span data-stu-id="7e4ca-166">**Figure 4-43**.</span></span> <span data-ttu-id="7e4ca-167">Okno prohlížeče s aplikací spuštěnou na více kontejnerech.</span><span class="sxs-lookup"><span data-stu-id="7e4ca-167">Browser window with an application running on multiple containers.</span></span>

<span data-ttu-id="7e4ca-168">Okno kontejnery:</span><span class="sxs-lookup"><span data-stu-id="7e4ca-168">Containers window:</span></span>

![Okno kontejnerů sady Visual Studio](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/visual-studio-containers-window.png)

<span data-ttu-id="7e4ca-170">**Obrázek 4-44**.</span><span class="sxs-lookup"><span data-stu-id="7e4ca-170">**Figure 4-44**.</span></span> <span data-ttu-id="7e4ca-171">Okno kontejnerů sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="7e4ca-171">Visual Studio "Containers" window</span></span>

<span data-ttu-id="7e4ca-172">Okno **kontejnery** umožňuje zobrazit spuštěné kontejnery, procházet dostupné image, zobrazovat proměnné prostředí, protokoly a mapování portů, kontrolovat systém souborů, připojit ladicí program nebo otevřít okno terminálu v prostředí kontejneru.</span><span class="sxs-lookup"><span data-stu-id="7e4ca-172">The **Containers** window lets you view running containers, browse available images, view environment variables, logs, and port mappings, inspect the filesystem, attach a debugger, or open a terminal window inside the container environment.</span></span>

<span data-ttu-id="7e4ca-173">Jak vidíte, integrace mezi Visual Studio 2019 a Docker je zcela zaměřená na produktivitu vývojářů.</span><span class="sxs-lookup"><span data-stu-id="7e4ca-173">As you can see, the integration between Visual Studio 2019 and Docker is completely oriented to the developer's productivity.</span></span>

<span data-ttu-id="7e4ca-174">Pomocí příkazu je samozřejmě můžete také zobrazit seznam imagí `docker images` .</span><span class="sxs-lookup"><span data-stu-id="7e4ca-174">Of course, you can also list the images using the `docker images` command.</span></span> <span data-ttu-id="7e4ca-175">Měli byste vidět `webapi` image a `webapp` s `dev` značkami vytvořenými automatickým nasazením našeho projektu pomocí sady Visual Studio 2019.</span><span class="sxs-lookup"><span data-stu-id="7e4ca-175">You should see the `webapi` and `webapp` images with the `dev` tags created by the automatic deployment of our project with Visual Studio 2019.</span></span>

```console
docker images
```

![Výstup konzoly z příkazu Docker images zobrazuje seznam s: úložiště, značka, ID obrázku, Vytvořeno (datum) a velikost.](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/docker-images-command.png)

<span data-ttu-id="7e4ca-177">**Obrázek 4-45**.</span><span class="sxs-lookup"><span data-stu-id="7e4ca-177">**Figure 4-45**.</span></span> <span data-ttu-id="7e4ca-178">Zobrazení imagí Docker</span><span class="sxs-lookup"><span data-stu-id="7e4ca-178">View of Docker images</span></span>

## <a name="register-the-solution-in-an-azure-container-registry-acr"></a><span data-ttu-id="7e4ca-179">Registrace řešení v Azure Container Registry (ACR)</span><span class="sxs-lookup"><span data-stu-id="7e4ca-179">Register the Solution in an Azure Container Registry (ACR)</span></span>

<span data-ttu-id="7e4ca-180">Obrázky můžete nahrát do [Azure Container Registry (ACR)](https://azure.microsoft.com/services/container-registry/), ale můžete také použít Docker Hub nebo jakýkoli jiný registr, aby bylo možné image nasadit do clusteru AKS z tohoto registru.</span><span class="sxs-lookup"><span data-stu-id="7e4ca-180">You can upload the images to the [Azure Container Registry (ACR)](https://azure.microsoft.com/services/container-registry/), but you could also use Docker Hub or any other registry, so the images can be deployed to the AKS cluster from that registry.</span></span>

### <a name="create-an-acr-instance"></a><span data-ttu-id="7e4ca-181">Vytvoření instance ACR</span><span class="sxs-lookup"><span data-stu-id="7e4ca-181">Create an ACR instance</span></span>

<span data-ttu-id="7e4ca-182">Z příkazu **AZ CLI**spusťte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="7e4ca-182">Run the following command from the **az cli**:</span></span>

```powershell
az acr create --name exploredocker --resource-group explore-docker-aks-rg --sku basic --admin-enabled
```

### <a name="create-the-image-in-release-mode"></a><span data-ttu-id="7e4ca-183">Vytvoření image v režimu vydání</span><span class="sxs-lookup"><span data-stu-id="7e4ca-183">Create the image in Release mode</span></span>

<span data-ttu-id="7e4ca-184">Bitovou kopii teď vytvoříte v režimu **vydání** (připravené pro produkční prostředí) tak, že změníte **verzi**, jak je znázorněno na obrázku 4-46, a spustíte aplikaci stejným způsobem jako předtím.</span><span class="sxs-lookup"><span data-stu-id="7e4ca-184">You'll now create the image in **Release** mode (ready for production) by changing to **Release**, as shown in Figure 4-46, and running the application as you did before.</span></span>

![Možnost panelu nástrojů v sadě VS k sestavení v režimu vydání.](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/select-release-mode.png)

<span data-ttu-id="7e4ca-186">**Obrázek 4-46**.</span><span class="sxs-lookup"><span data-stu-id="7e4ca-186">**Figure 4-46**.</span></span> <span data-ttu-id="7e4ca-187">Výběr režimu vydání</span><span class="sxs-lookup"><span data-stu-id="7e4ca-187">Selecting Release Mode</span></span>

<span data-ttu-id="7e4ca-188">Pokud `docker images` příkaz spustíte, zobrazí se oba vytvořené bitové kopie, jeden pro `debug` (**vývoj**) a druhý pro `release` (**nejnovější**) režim.</span><span class="sxs-lookup"><span data-stu-id="7e4ca-188">If you execute the `docker images` command, you'll see both images created, one for `debug` (**dev**) and the other for `release` (**latest**) mode.</span></span>

### <a name="create-a-new-tag-for-the-image"></a><span data-ttu-id="7e4ca-189">Vytvořit novou značku pro obrázek</span><span class="sxs-lookup"><span data-stu-id="7e4ca-189">Create a new Tag for the Image</span></span>

<span data-ttu-id="7e4ca-190">Každá image kontejneru musí být označena `loginServer` názvem registru.</span><span class="sxs-lookup"><span data-stu-id="7e4ca-190">Each container image needs to be tagged with the `loginServer` name of the registry.</span></span> <span data-ttu-id="7e4ca-191">Tato značka se používá pro směrování při nahrávání imagí kontejneru do registru imagí.</span><span class="sxs-lookup"><span data-stu-id="7e4ca-191">This tag is used for routing when pushing container images to an image registry.</span></span>

<span data-ttu-id="7e4ca-192">Název můžete zobrazit `loginServer` z Azure Portal a přebírat informace z Azure Container Registry</span><span class="sxs-lookup"><span data-stu-id="7e4ca-192">You can view the `loginServer` name from the Azure portal, taking the information from the Azure Container Registry</span></span>

![V prohlížeči se zobrazí název služby Azure Container Registry v pravém horním rohu.](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/loginServer-name.png)

<span data-ttu-id="7e4ca-194">**Obrázek 4-47**.</span><span class="sxs-lookup"><span data-stu-id="7e4ca-194">**Figure 4-47**.</span></span> <span data-ttu-id="7e4ca-195">Zobrazení názvu registru</span><span class="sxs-lookup"><span data-stu-id="7e4ca-195">View of the name of the Registry</span></span>

<span data-ttu-id="7e4ca-196">Nebo spuštěním následujícího příkazu:</span><span class="sxs-lookup"><span data-stu-id="7e4ca-196">Or by running the following command:</span></span>

```console
az acr list --resource-group <resource-group-name> --query "[].{acrLoginServer:loginServer}" --output table
```

![Výstup konzoly z výše uvedeného příkazu](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/az-cli-loginServer-name.png)

<span data-ttu-id="7e4ca-198">**Obrázek 4-48**.</span><span class="sxs-lookup"><span data-stu-id="7e4ca-198">**Figure 4-48**.</span></span> <span data-ttu-id="7e4ca-199">Získání názvu registru pomocí **AZ CLI**</span><span class="sxs-lookup"><span data-stu-id="7e4ca-199">Get the name of the registry using **az cli**</span></span>

<span data-ttu-id="7e4ca-200">V obou případech získáte název.</span><span class="sxs-lookup"><span data-stu-id="7e4ca-200">In both cases, you'll obtain the name.</span></span> <span data-ttu-id="7e4ca-201">V našem příkladu `exploredocker.azurecr.io` .</span><span class="sxs-lookup"><span data-stu-id="7e4ca-201">In our example, `exploredocker.azurecr.io`.</span></span>

<span data-ttu-id="7e4ca-202">Nyní můžete označit Image pomocí nejnovější bitové kopie (obrázek verze) a příkazu:</span><span class="sxs-lookup"><span data-stu-id="7e4ca-202">Now you can tag the image, taking the latest image (the Release image), with the command:</span></span>

```console
docker tag <image-name>:latest <login-server-name>/<image-name>:v1
```

<span data-ttu-id="7e4ca-203">Po spuštění příkazu vypište `docker tag` obrázky pomocí `docker images` příkazu a měli byste vidět obrázek s novou značkou.</span><span class="sxs-lookup"><span data-stu-id="7e4ca-203">After running the `docker tag` command, list the images with the `docker images` command, and you should see the image with the new tag.</span></span>

![Výstup konzoly z příkazu Docker images](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/tagged-docker-images-list.png)

<span data-ttu-id="7e4ca-205">**Obrázek 4-49**.</span><span class="sxs-lookup"><span data-stu-id="7e4ca-205">**Figure 4-49**.</span></span> <span data-ttu-id="7e4ca-206">Zobrazení tagovaných obrázků</span><span class="sxs-lookup"><span data-stu-id="7e4ca-206">View of tagged images</span></span>

### <a name="push-the-image-into-the-azure-acr"></a><span data-ttu-id="7e4ca-207">Vložení image do Azure ACR</span><span class="sxs-lookup"><span data-stu-id="7e4ca-207">Push the image into the Azure ACR</span></span>

<span data-ttu-id="7e4ca-208">Přihlášení k Azure Container Registry</span><span class="sxs-lookup"><span data-stu-id="7e4ca-208">Log in to the Azure Container Registry</span></span>

```console
az acr login --name exploredocker
```

<span data-ttu-id="7e4ca-209">Nahrajte image do Azure ACR pomocí následujícího příkazu:</span><span class="sxs-lookup"><span data-stu-id="7e4ca-209">Push the image into the Azure ACR, using the following command:</span></span>

```console
docker push <login-server-name>/<image-name>:v1
```

<span data-ttu-id="7e4ca-210">Tento příkaz při nahrávání imagí trvá, ale v procesu vám poskytne zpětnou vazbu.</span><span class="sxs-lookup"><span data-stu-id="7e4ca-210">This command takes a while uploading the images but gives you feedback in the process.</span></span> <span data-ttu-id="7e4ca-211">Na následujícím obrázku vidíte výstup z jedné image dokončeno a další probíhá.</span><span class="sxs-lookup"><span data-stu-id="7e4ca-211">In the following image you can see the output from one image completed and another in progress.</span></span>

![Výstup konzoly z příkazu Docker push](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/uploading-docker-images-complete.png)

<span data-ttu-id="7e4ca-213">**Obrázek 4-50**.</span><span class="sxs-lookup"><span data-stu-id="7e4ca-213">**Figure 4-50**.</span></span> <span data-ttu-id="7e4ca-214">Výstup konzoly z příkazu push</span><span class="sxs-lookup"><span data-stu-id="7e4ca-214">Console output from the push command.</span></span>

<span data-ttu-id="7e4ca-215">K nasazení aplikace pro více kontejnerů do clusteru AKS potřebujete některé `.yaml` soubory manifestu, které mají většinu vlastností ze `docker-compose.yml` `docker-compose.override.yml` souborů a.</span><span class="sxs-lookup"><span data-stu-id="7e4ca-215">To deploy your multi-container app into your AKS cluster you need some manifest `.yaml` files that have, most of the properties taken from the `docker-compose.yml` and `docker-compose.override.yml` files.</span></span>

#### `deploy-webapi.yml`

```yml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: webapi
  labels:
    app: weather-forecast
spec:
  replicas: 1
  selector:
    matchLabels:
      service: webapi
  template:
    metadata:
      labels:
        app: weather-forecast
        service: webapi
    spec:
      containers:
        - name: webapi
          image: exploredocker.azurecr.io/webapi:v1
          imagePullPolicy: IfNotPresent
          ports:
            - containerPort: 80
              protocol: TCP
          env:
            - name: ASPNETCORE_URLS
              value: http://+:80
---
apiVersion: v1
kind: Service
metadata:
  name: webapi
  labels:
    app: weather-forecast
    service: webapi
spec:
  ports:
    - port: 80
      targetPort: 80
      protocol: TCP
  selector:
    service: webapi
```

#### `deploy-webapp.yml`

```yml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: webapp
  labels:
    app: weather-forecast
spec:
  replicas: 1
  selector:
    matchLabels:
      service: webapp
  template:
    metadata:
      labels:
        app: weather-forecast
        service: webapp
    spec:
      containers:
        - name: webapp
          image: exploredocker.azurecr.io/webapp:v1
          imagePullPolicy: IfNotPresent
          ports:
            - containerPort: 80
              protocol: TCP
          env:
            - name: ASPNETCORE_URLS
              value: http://+:80
            - name: WebApiBaseAddress
              value: http://webapi
---
apiVersion: v1
kind: Service
metadata:
  name: webapp
  labels:
    app: weather-forecast
    service: webapp
spec:
  type: LoadBalancer
  ports:
    - port: 80
      targetPort: 80
      protocol: TCP
  selector:
    service: webapp
```

> [!NOTE]
> <span data-ttu-id="7e4ca-216">Předchozí `.yml` soubory povolují pouze `HTTP` porty pomocí `ASPNETCORE_URLS` parametru, aby nedocházelo k problémům s chybějícím certifikátem v ukázkové aplikaci.</span><span class="sxs-lookup"><span data-stu-id="7e4ca-216">The previous `.yml` files only enable the `HTTP` ports, using the `ASPNETCORE_URLS` parameter, to avoid issues with the missing certificate in the sample app.</span></span>

> [!TIP]
> <span data-ttu-id="7e4ca-217">V této příručce najdete informace o tom, jak vytvořit cluster AKS pro tuto ukázku v oddílu [**nasazení do služby Azure Kubernetes Service (AKS)**](deploy-azure-kubernetes-service.md) .</span><span class="sxs-lookup"><span data-stu-id="7e4ca-217">You can see how to create the AKS Cluster for this sample in section [**Deploy to Azure Kubernetes Service (AKS)**](deploy-azure-kubernetes-service.md) on this guide.</span></span>

<span data-ttu-id="7e4ca-218">Teď jste skoro připraveni nasadit pomocí **kubectl**, ale nejdřív musíte získat přihlašovací údaje z clusteru AKS pomocí tohoto příkazu:</span><span class="sxs-lookup"><span data-stu-id="7e4ca-218">Now you're almost ready to deploy using **kubectl**, but first you must get the credentials from the AKS Cluster with this command:</span></span>

```console
az aks get-credentials --resource-group explore-docker-aks-rg --name explore-docker-aks
```

![Výstup z konzoly z výše uvedeného příkazu: "prozkoumává-Docker-AKS" jako aktuální kontext v C:\Users\Miguel.kube\config](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/getting-aks-credentials.png)

<span data-ttu-id="7e4ca-220">**Obrázek 4-51**.</span><span class="sxs-lookup"><span data-stu-id="7e4ca-220">**Figure 4-51**.</span></span> <span data-ttu-id="7e4ca-221">Získávání přihlašovacích údajů z AKS do prostředí kubectl</span><span class="sxs-lookup"><span data-stu-id="7e4ca-221">Getting credentials from AKS into the kubectl environment.</span></span>

<span data-ttu-id="7e4ca-222">Musíte taky dovolit, aby cluster AKS vyčetl image z ACR pomocí tohoto příkazu:</span><span class="sxs-lookup"><span data-stu-id="7e4ca-222">You also have to allow the AKS cluster to pull images from the ACR, using this command:</span></span>

```console
az aks update --name explore-docker-aks --resource-group explore-docker-aks-rg --attach-acr exploredocker
```

<span data-ttu-id="7e4ca-223">Dokončení předchozího příkazu může trvat několik minut.</span><span class="sxs-lookup"><span data-stu-id="7e4ca-223">The previous command might take a couple of minutes to complete.</span></span> <span data-ttu-id="7e4ca-224">Pak pomocí `kubectl apply` příkazu spusťte nasazení a pak `kubectl get all` Získejte seznam objektů clusteru.</span><span class="sxs-lookup"><span data-stu-id="7e4ca-224">Then, use the `kubectl apply` command to launch the deployments, and then `kubectl get all` get list the cluster objects.</span></span>

```console
kubectl apply -f deploy-webapi.yml
kubectl apply -f deploy-webapp.yml

kubectl get all
```

![Výstup z konzoly z výše uvedených příkazů: nasazení byla aplikována.](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/kubectl-apply-command.png)

<span data-ttu-id="7e4ca-227">**Obrázek 4-52**.</span><span class="sxs-lookup"><span data-stu-id="7e4ca-227">**Figure 4-52**.</span></span> <span data-ttu-id="7e4ca-228">Nasazení do Kubernetes</span><span class="sxs-lookup"><span data-stu-id="7e4ca-228">Deployment to Kubernetes</span></span>

<span data-ttu-id="7e4ca-229">Budete muset chvíli počkat, dokud nástroj pro vyrovnávání zatížení nezíská externí IP adresu, zkontroluje se `kubectl get services` a pak by aplikace měla být k dispozici na adrese, jak je znázorněno na následujícím obrázku:</span><span class="sxs-lookup"><span data-stu-id="7e4ca-229">You'll have to wait a while until the load balancer gets the external IP, checking with `kubectl get services`, and then the application should be available at that address, as shown in the next image:</span></span>

![Zobrazení prohlížeče aplikace nasazené do AKS](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/aks-deployed-application.png)

<span data-ttu-id="7e4ca-231">**Obrázek 4-53**.</span><span class="sxs-lookup"><span data-stu-id="7e4ca-231">**Figure 4-53**.</span></span> <span data-ttu-id="7e4ca-232">Nasazení do Kubernetes</span><span class="sxs-lookup"><span data-stu-id="7e4ca-232">Deployment to Kubernetes</span></span>

<span data-ttu-id="7e4ca-233">Po dokončení nasazení můžete k [webovému uživatelskému rozhraní Kubernetes](https://kubernetes.io/docs/tasks/access-application-cluster/web-ui-dashboard/) přistupovat pomocí místního proxy serveru pomocí tunelu SSH.</span><span class="sxs-lookup"><span data-stu-id="7e4ca-233">When the deployment completes, you can access the [Kubernetes Web UI](https://kubernetes.io/docs/tasks/access-application-cluster/web-ui-dashboard/) with a local proxy, using an ssh tunnel.</span></span>

<span data-ttu-id="7e4ca-234">Nejprve musíte vytvořit ClusterRoleBinding pomocí následujícího příkazu:</span><span class="sxs-lookup"><span data-stu-id="7e4ca-234">First you must create a ClusterRoleBinding with the following command:</span></span>

```console
kubectl create clusterrolebinding kubernetes-dashboard --clusterrole=cluster-admin --serviceaccount=kube-system:kubernetes-dashboard
```

<span data-ttu-id="7e4ca-235">A potom tento příkaz spustí proxy:</span><span class="sxs-lookup"><span data-stu-id="7e4ca-235">And then this command to start the proxy:</span></span>

```console
az aks browse --resource-group exploredocker-aks-rg --name explore-docker-aks
```

<span data-ttu-id="7e4ca-236">Mělo by se otevřít okno prohlížeče `http://127.0.0.1:8001` s podobným zobrazením:</span><span class="sxs-lookup"><span data-stu-id="7e4ca-236">A browser window should open at `http://127.0.0.1:8001` with a view similar to this one:</span></span>

![Zobrazení prohlížeče řídicího panelu Kubernetes zobrazující nasazení, lusky, sady replik a služby.](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/kubernetes-cluster-information.png)

<span data-ttu-id="7e4ca-238">**Obrázek 4-54**.</span><span class="sxs-lookup"><span data-stu-id="7e4ca-238">**Figure 4-54**.</span></span> <span data-ttu-id="7e4ca-239">Zobrazit informace o clusteru Kubernetes</span><span class="sxs-lookup"><span data-stu-id="7e4ca-239">View Kubernetes cluster information</span></span>

<span data-ttu-id="7e4ca-240">Nyní máte aplikaci ASP.NET Core, která běží v kontejnerech Linux a nasazená do clusteru AKS v Azure.</span><span class="sxs-lookup"><span data-stu-id="7e4ca-240">Now you have your ASP.NET Core application, running in Linux containers, and deployed to an AKS cluster on Azure.</span></span>

> [!NOTE]
> <span data-ttu-id="7e4ca-241">Další informace o nasazení pomocí Kubernetes najdete v tématech:<https://kubernetes.io/docs/reference/kubectl/cheatsheet/></span><span class="sxs-lookup"><span data-stu-id="7e4ca-241">For more information on deployment with Kubernetes see: <https://kubernetes.io/docs/reference/kubectl/cheatsheet/></span></span>

> [!div class="step-by-step"]
> <span data-ttu-id="7e4ca-242">[Předchozí](set-up-windows-containers-with-powershell.md) 
>  [Další](../docker-devops-workflow/index.md)</span><span class="sxs-lookup"><span data-stu-id="7e4ca-242">[Previous](set-up-windows-containers-with-powershell.md)
[Next](../docker-devops-workflow/index.md)</span></span>
