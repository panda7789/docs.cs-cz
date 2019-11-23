---
title: Pracovní postup vývoje vnitřní smyčky pro aplikace Dockeru
description: Seznamte se s pracovním postupem "vnitřní smyčka" pro vývoj aplikací Docker.
ms.date: 02/15/2019
ms.openlocfilehash: 5f534b23f5e0042e68343deb0c1e9e0ee2e64600
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394780"
---
# <a name="inner-loop-development-workflow-for-docker-apps"></a><span data-ttu-id="35c80-103">Pracovní postup vývoje vnitřní smyčky pro aplikace Dockeru</span><span class="sxs-lookup"><span data-stu-id="35c80-103">Inner-loop development workflow for Docker apps</span></span>

<span data-ttu-id="35c80-104">Předtím, než se aktivuje pracovní postup vnější smyčky zahrnující celý cyklus DevOps, začne vše v každém počítači vývojářů, bude se zakódovat vlastní aplikace, pomocí svých preferovaných jazyků nebo platforem a místně se testuje (obrázek 4-21).</span><span class="sxs-lookup"><span data-stu-id="35c80-104">Before triggering the outer-loop workflow spanning the entire DevOps cycle, it all begins on each developer's machine, coding the app itself, using their preferred languages or platforms, and testing it locally (Figure 4-21).</span></span> <span data-ttu-id="35c80-105">V každém případě ale budete mít důležitý obecný bod, bez ohledu na to, jaký jazyk, rozhraní nebo platformy si zvolíte.</span><span class="sxs-lookup"><span data-stu-id="35c80-105">But in every case, you'll have an important point in common, no matter what language, framework, or platforms you choose.</span></span> <span data-ttu-id="35c80-106">V tomto konkrétním pracovním postupu budete vždy vyvíjet a testovat kontejnery Docker, ale lokálně.</span><span class="sxs-lookup"><span data-stu-id="35c80-106">In this specific workflow, you're always developing and testing Docker containers, but locally.</span></span>

![Diagram znázorňující koncept prostředí pro vývoj vnitřních smyček.](./media/docker-apps-inner-loop-workflow/inner-loop-development-context.png)

<span data-ttu-id="35c80-108">**Obrázek 4-21**.</span><span class="sxs-lookup"><span data-stu-id="35c80-108">**Figure 4-21**.</span></span> <span data-ttu-id="35c80-109">Vývojový kontext pro vnitřní smyčku</span><span class="sxs-lookup"><span data-stu-id="35c80-109">Inner-loop development context</span></span>

<span data-ttu-id="35c80-110">Kontejner nebo instance image Docker bude obsahovat tyto komponenty:</span><span class="sxs-lookup"><span data-stu-id="35c80-110">The container or instance of a Docker image will contain these components:</span></span>

- <span data-ttu-id="35c80-111">Výběr operačního systému (například distribuce systému Linux nebo Windows)</span><span class="sxs-lookup"><span data-stu-id="35c80-111">An operating system selection (for example, a Linux distribution or Windows)</span></span>

- <span data-ttu-id="35c80-112">Soubory přidané vývojářem (například binární soubory aplikace)</span><span class="sxs-lookup"><span data-stu-id="35c80-112">Files added by the developer (for example, app binaries)</span></span>

- <span data-ttu-id="35c80-113">Konfigurace (například nastavení prostředí a závislosti)</span><span class="sxs-lookup"><span data-stu-id="35c80-113">Configuration (for example, environment settings and dependencies)</span></span>

- <span data-ttu-id="35c80-114">Pokyny pro procesy, které se mají spustit přes Docker</span><span class="sxs-lookup"><span data-stu-id="35c80-114">Instructions for what processes to run by Docker</span></span>

<span data-ttu-id="35c80-115">Můžete nastavit vývojový postup pro vnitřní smyčku, který využívá Docker jako proces (popsaný v následující části).</span><span class="sxs-lookup"><span data-stu-id="35c80-115">You can set up the inner-loop development workflow that utilizes Docker as the process (described in the next section).</span></span> <span data-ttu-id="35c80-116">Vezměte v úvahu, že nejsou zahrnuté počáteční kroky pro nastavení prostředí, protože ho stačí udělat jenom jednou.</span><span class="sxs-lookup"><span data-stu-id="35c80-116">Consider that the initial steps to set up the environment are not included, because you only need to do it once.</span></span>

## <a name="building-a-single-app-within-a-docker-container-using-visual-studio-code-and-docker-cli"></a><span data-ttu-id="35c80-117">Vytvoření jedné aplikace v kontejneru Docker pomocí Visual Studio Code a Docker CLI</span><span class="sxs-lookup"><span data-stu-id="35c80-117">Building a single app within a Docker container using Visual Studio Code and Docker CLI</span></span>

<span data-ttu-id="35c80-118">Aplikace se vytvářejí z vašich vlastních služeb a dalších knihoven (závislosti).</span><span class="sxs-lookup"><span data-stu-id="35c80-118">Apps are made up from your own services plus additional libraries (dependencies).</span></span>

<span data-ttu-id="35c80-119">Obrázek 4-22 ukazuje základní kroky, které obvykle potřebujete provést při sestavování aplikace Docker, po kterém následují podrobné popisy jednotlivých kroků.</span><span class="sxs-lookup"><span data-stu-id="35c80-119">Figure 4-22 shows the basic steps that you usually need to carry out when building a Docker app, followed by detailed descriptions of each step.</span></span>

![Diagram znázorňující sedm kroků, které je potřeba k vytvoření kontejnerové aplikace.](./media/docker-apps-inner-loop-workflow/life-cycle-containerized-apps-docker-cli.png)

<span data-ttu-id="35c80-121">**Obrázek 4-22**.</span><span class="sxs-lookup"><span data-stu-id="35c80-121">**Figure 4-22**.</span></span> <span data-ttu-id="35c80-122">Pracovní postup vysoké úrovně pro životní cyklus aplikací Docker s využitím Docker CLI</span><span class="sxs-lookup"><span data-stu-id="35c80-122">High-level workflow for the life cycle for Docker containerized applications using Docker CLI</span></span>

### <a name="step-1-start-coding-in-visual-studio-code-and-create-your-initial-appservice-baseline"></a><span data-ttu-id="35c80-123">Krok 1: začátek kódování Visual Studio Code a vytvoření počátečního směrného plánu aplikace nebo služby</span><span class="sxs-lookup"><span data-stu-id="35c80-123">Step 1: Start coding in Visual Studio Code and create your initial app/service baseline</span></span>

<span data-ttu-id="35c80-124">Způsob vývoje aplikace je podobný způsobu, jakým jste to provedete bez Docker.</span><span class="sxs-lookup"><span data-stu-id="35c80-124">The way you develop your application is similar to the way you do it without Docker.</span></span> <span data-ttu-id="35c80-125">Rozdíl je v tom, že při vývoji nasazujete a testujete svou aplikaci nebo služby běžící v kontejnerech Docker umístěných ve vašem místním prostředí (jako je třeba virtuální počítač Linux nebo Windows).</span><span class="sxs-lookup"><span data-stu-id="35c80-125">The difference is that while developing, you're deploying and testing your application or services running within Docker containers placed in your local environment (like a Linux VM or Windows).</span></span>

<span data-ttu-id="35c80-126">**Nastavení místního prostředí**</span><span class="sxs-lookup"><span data-stu-id="35c80-126">**Setting up your local environment**</span></span>

<span data-ttu-id="35c80-127">S nejnovějšími verzemi Docker pro Mac a Windows je snazší než kdy dřív vyvíjet aplikace Docker a instalace je jednoduchá.</span><span class="sxs-lookup"><span data-stu-id="35c80-127">With the latest versions of Docker for Mac and Windows, it's easier than ever to develop Docker applications, and the setup is straightforward.</span></span>

> [!TIP]
> <span data-ttu-id="35c80-128">Pokyny, jak nastavit Docker for Windows, najdete v <https://docs.docker.com/docker-for-windows/>.</span><span class="sxs-lookup"><span data-stu-id="35c80-128">For instructions on setting up Docker for Windows, go to <https://docs.docker.com/docker-for-windows/>.</span></span>
>
><span data-ttu-id="35c80-129">Pokyny, jak nastavit Docker pro Mac, najdete v tématu <https://docs.docker.com/docker-for-mac/>.</span><span class="sxs-lookup"><span data-stu-id="35c80-129">For instructions on setting up Docker for Mac, go to <https://docs.docker.com/docker-for-mac/>.</span></span>

<span data-ttu-id="35c80-130">Kromě toho budete potřebovat Editor kódu, abyste mohli skutečně vyvíjet aplikace při použití Docker CLI.</span><span class="sxs-lookup"><span data-stu-id="35c80-130">In addition, you'll need a code editor so that you can actually develop your application while using Docker CLI.</span></span>

<span data-ttu-id="35c80-131">Společnost Microsoft poskytuje Visual Studio Code, což je zjednodušený Editor kódu, který je podporován v systémech Windows, Linux a macOS a poskytuje technologii IntelliSense s [podporou pro řadu jazyků](https://code.visualstudio.com/docs/languages/overview) (JavaScript, .NET, jít, Java, Ruby, Python a většina moderních jazyků), [ladění](https://code.visualstudio.com/Docs/editor/debugging), [integrace s podporou Gitu](https://code.visualstudio.com/Docs/editor/versioncontrol) a [rozšíření](https://code.visualstudio.com/docs/extensions/overview).</span><span class="sxs-lookup"><span data-stu-id="35c80-131">Microsoft provides Visual Studio Code, which is a lightweight code editor that's supported on Windows, Linux, and macOS, and provides IntelliSense with [support for many languages](https://code.visualstudio.com/docs/languages/overview) (JavaScript, .NET, Go, Java, Ruby, Python, and most modern languages), [debugging](https://code.visualstudio.com/Docs/editor/debugging), [integration with Git](https://code.visualstudio.com/Docs/editor/versioncontrol) and [extensions support](https://code.visualstudio.com/docs/extensions/overview).</span></span> <span data-ttu-id="35c80-132">Tento editor je vhodný pro vývojáře v macOS a Linux.</span><span class="sxs-lookup"><span data-stu-id="35c80-132">This editor is a great fit for macOS and Linux developers.</span></span> <span data-ttu-id="35c80-133">V systému Windows můžete použít také aplikaci Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="35c80-133">In Windows, you also can use Visual Studio.</span></span>

> [!TIP]
> <span data-ttu-id="35c80-134">Pokyny k instalaci Visual Studio Code pro Windows, Linux nebo macOS najdete v článku <https://code.visualstudio.com/docs/setup/setup-overview/>.</span><span class="sxs-lookup"><span data-stu-id="35c80-134">For instructions on installing Visual Studio Code for Windows, Linux, or macOS, go to <https://code.visualstudio.com/docs/setup/setup-overview/>.</span></span>
>
> <span data-ttu-id="35c80-135">Pokyny, jak nastavit Docker pro Mac, najdete v tématu <https://docs.docker.com/docker-for-mac/>.</span><span class="sxs-lookup"><span data-stu-id="35c80-135">For instructions on setting up Docker for Mac, go to <https://docs.docker.com/docker-for-mac/>.</span></span>

<span data-ttu-id="35c80-136">Můžete pracovat s Docker CLI a napsat kód pomocí editoru kódu, ale použití Visual Studio Code s rozšířením Docker usnadňuje tvorbu `Dockerfile` a `docker-compose.yml` souborů v pracovním prostoru.</span><span class="sxs-lookup"><span data-stu-id="35c80-136">You can work with Docker CLI and write your code using any code editor, but using Visual Studio Code with the Docker extension makes it easy to author `Dockerfile` and `docker-compose.yml` files in your workspace.</span></span> <span data-ttu-id="35c80-137">Můžete také spouštět úlohy a skripty z Visual Studio Code integrované vývojové prostředí (IDE) a spustit příkazy Docker pomocí příkazu Docker CLI pod.</span><span class="sxs-lookup"><span data-stu-id="35c80-137">You can also run tasks and scripts from the Visual Studio Code IDE to execute Docker commands using the Docker CLI underneath.</span></span>

<span data-ttu-id="35c80-138">Rozšíření Docker pro VS Code poskytuje následující funkce:</span><span class="sxs-lookup"><span data-stu-id="35c80-138">The Docker extension for VS Code provides the following features:</span></span>

- <span data-ttu-id="35c80-139">Automatické generování `Dockerfile` a `docker-compose.yml` souborů</span><span class="sxs-lookup"><span data-stu-id="35c80-139">Automatic `Dockerfile` and `docker-compose.yml` file generation</span></span>

- <span data-ttu-id="35c80-140">Zvýrazňování syntaxe a tipy k najetí myší pro soubory `docker-compose.yml` a `Dockerfile`</span><span class="sxs-lookup"><span data-stu-id="35c80-140">Syntax highlighting and hover tips for `docker-compose.yml` and `Dockerfile` files</span></span>

- <span data-ttu-id="35c80-141">IntelliSense (dokončování) pro soubory `Dockerfile` a `docker-compose.yml`</span><span class="sxs-lookup"><span data-stu-id="35c80-141">IntelliSense (completions) for `Dockerfile` and `docker-compose.yml` files</span></span>

- <span data-ttu-id="35c80-142">Linting (chyby a upozornění) pro soubory `Dockerfile`</span><span class="sxs-lookup"><span data-stu-id="35c80-142">Linting (errors and warnings) for `Dockerfile` files</span></span>

- <span data-ttu-id="35c80-143">Integrace palet příkazů (F1) pro nejběžnější příkazy Docker</span><span class="sxs-lookup"><span data-stu-id="35c80-143">Command Palette (F1) integration for the most common Docker commands</span></span>

- <span data-ttu-id="35c80-144">Integrace Průzkumníka pro správu imagí a kontejnerů</span><span class="sxs-lookup"><span data-stu-id="35c80-144">Explorer integration for managing Images and Containers</span></span>

- <span data-ttu-id="35c80-145">Nasazení imagí z Dockerhubu a kontejnerů Azure Container Registry do Azure App Service</span><span class="sxs-lookup"><span data-stu-id="35c80-145">Deploy images from DockerHub and Azure Container Registries to Azure App Service</span></span>

<span data-ttu-id="35c80-146">Pokud chcete nainstalovat rozšíření Docker, stiskněte kombinaci kláves CTRL + SHIFT + P, zadejte `ext install`a pak spuštěním příkazu instalovat rozšíření zobrazte seznam rozšíření Marketplace.</span><span class="sxs-lookup"><span data-stu-id="35c80-146">To install the Docker extension, press Ctrl+Shift+P, type `ext install`, and then run the Install Extension command to bring up the Marketplace extension list.</span></span> <span data-ttu-id="35c80-147">Potom zadejte **Docker** pro filtrování výsledků a pak vyberte rozšíření podpora Docker, jak je znázorněno na obrázku 4-23.</span><span class="sxs-lookup"><span data-stu-id="35c80-147">Next, type **docker** to filter the results, and then select the Docker Support extension, as depicted in Figure 4-23.</span></span>

![Zobrazení rozšíření Docker pro VS Code.](./media/docker-apps-inner-loop-workflow/install-docker-extension-vs-code.png)

<span data-ttu-id="35c80-149">**Obrázek 4-23**.</span><span class="sxs-lookup"><span data-stu-id="35c80-149">**Figure 4-23**.</span></span> <span data-ttu-id="35c80-150">Instalace rozšíření Docker v Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="35c80-150">Installing the Docker Extension in Visual Studio Code</span></span>

### <a name="step-2-create-a-dockerfile-related-to-an-existing-image-plain-os-or-dev-environments-like-net-core-nodejs-and-ruby"></a><span data-ttu-id="35c80-151">Krok 2: vytvoření souboru Dockerfile souvisejícího s existující imagí (prostého operačního systému nebo vývojového prostředí, jako je .NET Core, Node. js a Ruby)</span><span class="sxs-lookup"><span data-stu-id="35c80-151">Step 2: Create a DockerFile related to an existing image (plain OS or dev environments like .NET Core, Node.js, and Ruby)</span></span>

<span data-ttu-id="35c80-152">Budete potřebovat `DockerFile` pro vlastní image, která se má sestavit a na kontejner, který se má nasadit.</span><span class="sxs-lookup"><span data-stu-id="35c80-152">You'll need a `DockerFile` per custom image to be built and per container to be deployed.</span></span> <span data-ttu-id="35c80-153">Pokud se vaše aplikace skládá z jedné vlastní služby, budete potřebovat jednu `DockerFile`.</span><span class="sxs-lookup"><span data-stu-id="35c80-153">If your app is made up of a single custom service, you'll need a single `DockerFile`.</span></span> <span data-ttu-id="35c80-154">Pokud se ale vaše aplikace skládá z několika služeb (jako v architektuře mikroslužeb), budete potřebovat jednu `Dockerfile` na službu.</span><span class="sxs-lookup"><span data-stu-id="35c80-154">But if your app is composed of multiple services (as in a microservices architecture), you'll need one `Dockerfile` per service.</span></span>

<span data-ttu-id="35c80-155">`DockerFile` se běžně umísťují do kořenové složky vaší aplikace nebo služby a obsahuje požadované příkazy, aby Docker věděl, jak tuto aplikaci nebo službu spustit.</span><span class="sxs-lookup"><span data-stu-id="35c80-155">The `DockerFile` is commonly placed in the root folder of your app or service and contains the required commands so that Docker knows how to set up and run that app or service.</span></span> <span data-ttu-id="35c80-156">Můžete vytvořit své `DockerFile` a přidat je do projektu společně s vaším kódem (Node. js, .NET Core atd.), nebo pokud s prostředím začínáte, podívejte se na následující tip.</span><span class="sxs-lookup"><span data-stu-id="35c80-156">You can create your `DockerFile` and add it to your project along with your code (node.js, .NET Core, etc.), or, if you're new to the environment, take a look at the following Tip.</span></span>

> [!TIP]
> <span data-ttu-id="35c80-157">Pomocí rozšíření Docker můžete postupovat při použití `Dockerfile` a `docker-compose.yml` souborů souvisejících s kontejnery Docker.</span><span class="sxs-lookup"><span data-stu-id="35c80-157">You can use the Docker extension to guide you when using the `Dockerfile` and `docker-compose.yml` files related to your Docker containers.</span></span> <span data-ttu-id="35c80-158">Nakonec budete pravděpodobně zapisovat tyto typy souborů bez tohoto nástroje, ale používání rozšíření Docker je dobrým výchozím bodem, který zrychlí výukovou křivku.</span><span class="sxs-lookup"><span data-stu-id="35c80-158">Eventually, you'll probably write these kinds of files without this tool, but using the Docker extension is a good starting point that will accelerate your learning curve.</span></span>

<span data-ttu-id="35c80-159">Na obrázku 4-24 se můžete podívat, jak se přidávají soubor Docker-skládání pomocí rozšíření Docker pro VS Code.</span><span class="sxs-lookup"><span data-stu-id="35c80-159">In Figure 4-24, you can see how a docker-compose file is added by using the Docker Extension for VS Code.</span></span>

![Zobrazení konzoly rozšíření Docker pro VS Code.](./media/docker-apps-inner-loop-workflow/add-docker-files-to-workspace-command.png)

<span data-ttu-id="35c80-161">**Obrázek 4-24**.</span><span class="sxs-lookup"><span data-stu-id="35c80-161">**Figure 4-24**.</span></span> <span data-ttu-id="35c80-162">Soubory Docker přidané pomocí **příkazu přidat soubory Docker do pracovního prostoru**</span><span class="sxs-lookup"><span data-stu-id="35c80-162">Docker files added using the **Add Docker files to Workspace command**</span></span>

<span data-ttu-id="35c80-163">Když přidáte souboru Dockerfile, určíte, jakou základní image Docker budete používat (například pomocí `FROM mcr.microsoft.com/dotnet/core/aspnet`).</span><span class="sxs-lookup"><span data-stu-id="35c80-163">When you add a DockerFile, you specify what base Docker image you’ll be using (like using `FROM mcr.microsoft.com/dotnet/core/aspnet`).</span></span> <span data-ttu-id="35c80-164">Obvykle sestavíte vlastní image na základní imagi, kterou získáte z oficiálního úložiště v [registru Docker Hub](https://hub.docker.com/) (jako je [image pro .NET Core](https://hub.docker.com/_/microsoft-dotnet-core/) nebo [pro Node. js](https://hub.docker.com/_/node/)).</span><span class="sxs-lookup"><span data-stu-id="35c80-164">You'll usually build your custom image on top of a base image that you get from any official repository at the [Docker Hub registry](https://hub.docker.com/) (like an [image for .NET Core](https://hub.docker.com/_/microsoft-dotnet-core/) or the one [for Node.js](https://hub.docker.com/_/node/)).</span></span>

<span data-ttu-id="35c80-165">***Použití stávající oficiální image Docker***</span><span class="sxs-lookup"><span data-stu-id="35c80-165">***Use an existing official Docker image***</span></span>

<span data-ttu-id="35c80-166">Použití oficiálního úložiště jazykové sady s číslem verze zajišťuje, aby byly stejné funkce jazyka dostupné na všech počítačích (včetně vývoje, testování a produkčního prostředí).</span><span class="sxs-lookup"><span data-stu-id="35c80-166">Using an official repository of a language stack with a version number ensures that the same language features are available on all machines (including development, testing, and production).</span></span>

<span data-ttu-id="35c80-167">Následuje ukázkový souboru Dockerfile pro kontejner .NET Core:</span><span class="sxs-lookup"><span data-stu-id="35c80-167">The following is a sample DockerFile for a .NET Core container:</span></span>

```Dockerfile
# Base Docker image to use  
FROM mcr.microsoft.com/dotnet/core/aspnet:2.2
  
# Set the Working Directory and files to be copied to the image  
ARG source  
WORKDIR /app  
COPY ${source:-bin/Release/PublishOutput} .  
  
# Configure the listening port to 80 (Internal/Secured port within Docker host)  
EXPOSE 80  
  
# Application entry point  
ENTRYPOINT ["dotnet", "MyCustomMicroservice.dll"]
```

<span data-ttu-id="35c80-168">V tomto případě je bitová kopie založená na verzi 2,2 oficiální bitové kopie ASP.NET Core Docker (pro Linux a Windows), jak na řádku `FROM mcr.microsoft.com/dotnet/core/aspnet:2.2`.</span><span class="sxs-lookup"><span data-stu-id="35c80-168">In this case, the image is based on version 2.2 of the official ASP.NET Core Docker image (multi-arch for Linux and Windows), as per the line `FROM mcr.microsoft.com/dotnet/core/aspnet:2.2`.</span></span> <span data-ttu-id="35c80-169">(Další informace o tomto tématu najdete na stránce [ASP.NET Core Docker image](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) a na stránce s [obrázkem rozhraní Docker .NET Core](https://hub.docker.com/_/microsoft-dotnet-core/) ).</span><span class="sxs-lookup"><span data-stu-id="35c80-169">(For more information about this topic, see the [ASP.NET Core Docker Image](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) page and the [.NET Core Docker Image](https://hub.docker.com/_/microsoft-dotnet-core/) page).</span></span>

<span data-ttu-id="35c80-170">V souboru Dockerfile můžete také dát Docker pokyn k naslouchání portu TCP, který budete používat za běhu (například port 80).</span><span class="sxs-lookup"><span data-stu-id="35c80-170">In the DockerFile, you can also instruct Docker to listen to the TCP port that you'll use at runtime (such as port 80).</span></span>

<span data-ttu-id="35c80-171">V souboru Dockerfile můžete určit další nastavení konfigurace v závislosti na jazyku a rozhraní, které používáte.</span><span class="sxs-lookup"><span data-stu-id="35c80-171">You can specify additional configuration settings in the Dockerfile, depending on the language and framework you're using.</span></span> <span data-ttu-id="35c80-172">Například `ENTRYPOINT` řádek s `["dotnet", "MySingleContainerWebApp.dll"]` instruuje Docker na spuštění aplikace .NET Core.</span><span class="sxs-lookup"><span data-stu-id="35c80-172">For instance, the `ENTRYPOINT` line with `["dotnet", "MySingleContainerWebApp.dll"]` tells Docker to run a .NET Core application.</span></span> <span data-ttu-id="35c80-173">Pokud používáte sadu SDK a .NET Core CLI (`dotnet CLI`) k sestavování a spouštění aplikace .NET, toto nastavení by se lišilo.</span><span class="sxs-lookup"><span data-stu-id="35c80-173">If you're using the SDK and the .NET Core CLI (`dotnet CLI`) to build and run the .NET application, this setting would be different.</span></span> <span data-ttu-id="35c80-174">Klíčovým bodem a dalšími nastaveními závisí na jazyku a platformě, kterou zvolíte pro vaši aplikaci.</span><span class="sxs-lookup"><span data-stu-id="35c80-174">The key point here is that the ENTRYPOINT line and other settings depend on the language and platform you choose for your application.</span></span>

> [!TIP]
> <span data-ttu-id="35c80-175">Další informace o vytváření imagí Docker pro aplikace .NET Core najdete v <https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images>.</span><span class="sxs-lookup"><span data-stu-id="35c80-175">For more information about building Docker images for .NET Core applications, go to <https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images>.</span></span>
>
> <span data-ttu-id="35c80-176">Pokud se chcete dozvědět víc o vytváření vlastních imagí, navštivte <https://docs.docker.com/engine/tutorials/dockerimages/>.</span><span class="sxs-lookup"><span data-stu-id="35c80-176">To learn more about building your own images, go to <https://docs.docker.com/engine/tutorials/dockerimages/>.</span></span>

<span data-ttu-id="35c80-177">**Použití úložišť imagí s více archy**</span><span class="sxs-lookup"><span data-stu-id="35c80-177">**Use multi-arch image repositories**</span></span>

<span data-ttu-id="35c80-178">Jeden název bitové kopie v úložišti může obsahovat varianty platformy, jako je například bitová kopie systému Linux a bitová kopie systému Windows.</span><span class="sxs-lookup"><span data-stu-id="35c80-178">A single image name in a repo can contain platform variants, such as a Linux image and a Windows image.</span></span> <span data-ttu-id="35c80-179">Tato funkce umožňuje dodavatelům, jako je Microsoft (základní tvůrci obrázků), vytvořit jedno úložiště pro pokrytí více platforem (tj. Linux a Windows).</span><span class="sxs-lookup"><span data-stu-id="35c80-179">This feature allows vendors like Microsoft (base image creators) to create a single repo to cover multiple platforms (that is, Linux and Windows).</span></span> <span data-ttu-id="35c80-180">Například úložiště [dotnet/Core/ASPNET](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) dostupné v registru Docker Hub poskytuje podporu pro systémy Linux a Windows nano Server pomocí stejného názvu image.</span><span class="sxs-lookup"><span data-stu-id="35c80-180">For example, the [dotnet/core/aspnet](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) repository available in the Docker Hub registry provides support for Linux and Windows Nano Server by using the same image name.</span></span>

<span data-ttu-id="35c80-181">Načtení image [dotnet/Core/ASPNET](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) z hostitele Windows vyžádá si variantu Windows, zatímco při vyřazování stejného názvu bitové kopie z hostitele se systémem Linux se zažádá o variantu systému Linux.</span><span class="sxs-lookup"><span data-stu-id="35c80-181">Pulling the [dotnet/core/aspnet](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) image from a Windows host pulls the Windows variant, whereas pulling the same image name from a Linux host pulls the Linux variant.</span></span>

<span data-ttu-id="35c80-182">***Vytvoření základní Image od začátku***</span><span class="sxs-lookup"><span data-stu-id="35c80-182">***Create your base image from scratch***</span></span>

<span data-ttu-id="35c80-183">Můžete vytvořit vlastní základní image Docker od začátku, jak je vysvětleno v tomto [článku](https://docs.docker.com/engine/userguide/eng-image/baseimages/) z Docker.</span><span class="sxs-lookup"><span data-stu-id="35c80-183">You can create your own Docker base image from scratch as explained in this [article](https://docs.docker.com/engine/userguide/eng-image/baseimages/) from Docker.</span></span> <span data-ttu-id="35c80-184">Tento scénář je pravděpodobně nevhodný pro vás, pokud právě začínáte s Docker, ale pokud chcete nastavit konkrétní bity vlastní základní image, můžete to provést.</span><span class="sxs-lookup"><span data-stu-id="35c80-184">This scenario is probably not the best for you if you're just starting with Docker, but if you want to set the specific bits of your own base image, you can do it.</span></span>

### <a name="step-3-create-your-custom-docker-images-embedding-your-service-in-it"></a><span data-ttu-id="35c80-185">Krok 3: vytvořte vlastní image Docker, ve kterých se služba vkládá.</span><span class="sxs-lookup"><span data-stu-id="35c80-185">Step 3: Create your custom Docker images embedding your service in it</span></span>

<span data-ttu-id="35c80-186">Pro každou vlastní službu, která se skládá z vaší aplikace, budete muset vytvořit související image.</span><span class="sxs-lookup"><span data-stu-id="35c80-186">For each custom service that comprises your app, you'll need to create a related image.</span></span> <span data-ttu-id="35c80-187">Pokud se vaše aplikace skládá z jediné služby nebo webové aplikace, budete potřebovat jenom jednu Image.</span><span class="sxs-lookup"><span data-stu-id="35c80-187">If your app is made up of a single service or web app, you'll need just a single image.</span></span>

> [!NOTE]
> <span data-ttu-id="35c80-188">Když vezmete v úvahu "DevOps pracovní postup vnějšího cyklu", image se vytvoří pomocí automatizovaného procesu sestavení pokaždé, když nahrajete zdrojový kód do úložiště Git (průběžná integrace), takže se image vytvoří v globálním prostředí z vašich zdrojový kód.</span><span class="sxs-lookup"><span data-stu-id="35c80-188">When taking into account the "outer-loop DevOps workflow", the images will be created by an automated build process whenever you push your source code to a Git repository (Continuous Integration), so the images will be created in that global environment from your source code.</span></span>
>
> <span data-ttu-id="35c80-189">Ale předtím, než se podíváme na tuto trasu vnější smyčky, musíme zajistit správné fungování aplikace Docker, aby nedošlo k tomu, že neobsahují kód, který nemusí správně fungovat v systému správy zdrojového kódu (Git atd.).</span><span class="sxs-lookup"><span data-stu-id="35c80-189">But before we consider going to that outer-loop route, we need to ensure that the Docker application is actually working properly so that they don't push code that might not work properly to the source control system (Git, etc.).</span></span>
>
> <span data-ttu-id="35c80-190">Proto každý vývojář nejprve potřebuje provést celý proces vnitřní smyčky pro místní testování a pokračovat ve vývoji, dokud nechce doručovat kompletní funkci nebo přepnout do systému správy zdrojového kódu.</span><span class="sxs-lookup"><span data-stu-id="35c80-190">Therefore, each developer first needs to do the entire inner-loop process to test locally and continue developing until they want to push a complete feature or change to the source control system.</span></span>

<span data-ttu-id="35c80-191">Pokud chcete vytvořit image v místním prostředí a používat souboru Dockerfile, můžete použít příkaz Docker Build, jak je znázorněno na obrázku 4-25 (můžete také spustit `docker-compose up --build` pro aplikace složené z několika kontejnerů/služeb).</span><span class="sxs-lookup"><span data-stu-id="35c80-191">To create an image in your local environment and using the DockerFile, you can use the docker build command, as demonstrated in Figure 4-25 (you also can run `docker-compose up --build` for applications composed by several containers/services).</span></span>

![Snímek obrazovky znázorňující výstup konzoly příkazu Docker Build](./media/docker-apps-inner-loop-workflow/run-docker-build-command.png)

<span data-ttu-id="35c80-193">**Obrázek 4-25**.</span><span class="sxs-lookup"><span data-stu-id="35c80-193">**Figure 4-25**.</span></span> <span data-ttu-id="35c80-194">Spouští se sestavení Docker.</span><span class="sxs-lookup"><span data-stu-id="35c80-194">Running docker build</span></span>

<span data-ttu-id="35c80-195">V případě potřeby můžete místo přímého spuštění `docker build` ze složky projektu vygenerovat nasazovatelné složky s knihovnami .NET potřebné pomocí příkazu Run `dotnet publish` a pak spustit `docker build`.</span><span class="sxs-lookup"><span data-stu-id="35c80-195">Optionally, instead of directly running `docker build` from the project folder, you first can generate a deployable folder with the .NET libraries needed by using the run `dotnet publish` command, and then run `docker build`.</span></span>

<span data-ttu-id="35c80-196">Tento příklad vytvoří bitovou kopii Docker s názvem `cesardl/netcore-webapi-microservice-docker:first` (`:first` je značka, jako je například specifická verze).</span><span class="sxs-lookup"><span data-stu-id="35c80-196">This example creates a Docker image with the name `cesardl/netcore-webapi-microservice-docker:first` (`:first` is a tag, like a specific version).</span></span> <span data-ttu-id="35c80-197">Tento krok můžete provést pro každou vlastní bitovou kopii, kterou potřebujete vytvořit pro svoji sestavenou aplikaci Docker s několika kontejnery.</span><span class="sxs-lookup"><span data-stu-id="35c80-197">You can take this step for each custom image you need to create for your composed Docker application with several containers.</span></span>

<span data-ttu-id="35c80-198">Existující image můžete najít v místním úložišti (ve vývojovém počítači) pomocí příkazu Docker images, jak je znázorněno na obrázku 4-26.</span><span class="sxs-lookup"><span data-stu-id="35c80-198">You can find the existing images in your local repository (your development machine) by using the docker images command, as illustrated in Figure 4-26.</span></span>

![Výstup z konzoly z příkazu Docker images zobrazující existující image](./media/docker-apps-inner-loop-workflow/view-existing-images-with-docker-images.png)

<span data-ttu-id="35c80-200">**Obrázek 4-26**.</span><span class="sxs-lookup"><span data-stu-id="35c80-200">**Figure 4-26**.</span></span> <span data-ttu-id="35c80-201">Zobrazení existujících imagí pomocí imagí Docker</span><span class="sxs-lookup"><span data-stu-id="35c80-201">Viewing existing images using docker images</span></span>

### <a name="step-4-define-your-services-in-docker-composeyml-when-building-a-composed-docker-app-with-multiple-services"></a><span data-ttu-id="35c80-202">Krok 4: definování služeb v Docker-Compose. yml při sestavování složené aplikace Docker s více službami</span><span class="sxs-lookup"><span data-stu-id="35c80-202">Step 4: Define your services in docker-compose.yml when building a composed Docker app with multiple services</span></span>

<span data-ttu-id="35c80-203">Pomocí souboru `docker-compose.yml` můžete definovat sadu souvisejících služeb, které mají být nasazeny jako složená aplikace, a příkazy nasazení popsané v části Další krok.</span><span class="sxs-lookup"><span data-stu-id="35c80-203">With the `docker-compose.yml` file, you can define a set of related services to be deployed as a composed application with the deployment commands explained in the next step section.</span></span>

<span data-ttu-id="35c80-204">Vytvořte tento soubor ve složce Main nebo root Solution. měl by mít podobný obsah, jako je zobrazený v tomto souboru `docker-compose.yml`:</span><span class="sxs-lookup"><span data-stu-id="35c80-204">Create that file in your main or root solution folder; it should have content similar to that shown in this `docker-compose.yml` file:</span></span>

```yml
version: '3.4'
services:
  web:
    build: .
    ports:
     - "81:80"
    volumes:
     - .:/code
    depends_on:
     - redis
  redis:
    image: redis
```

<span data-ttu-id="35c80-205">V tomto konkrétním případě tento soubor definuje dvě služby: webovou službu (vlastní služba) a službu Redis (oblíbená služba mezipaměti).</span><span class="sxs-lookup"><span data-stu-id="35c80-205">In this particular case, this file defines two services: the web service (your custom service) and the redis service (a popular cache service).</span></span> <span data-ttu-id="35c80-206">Každá služba bude nasazena jako kontejner, takže musíme pro každou z nich použít konkrétní image Docker.</span><span class="sxs-lookup"><span data-stu-id="35c80-206">Each service will be deployed as a container, so we need to use a concrete Docker image for each.</span></span> <span data-ttu-id="35c80-207">Pro tuto konkrétní webovou službu bude bitová kopie potřebovat následující:</span><span class="sxs-lookup"><span data-stu-id="35c80-207">For this particular web service, the image will need to do the following:</span></span>

- <span data-ttu-id="35c80-208">Sestavte z souboru Dockerfile v aktuálním adresáři</span><span class="sxs-lookup"><span data-stu-id="35c80-208">Build from the DockerFile in the current directory</span></span>

- <span data-ttu-id="35c80-209">Předejte vystavený port 80 na kontejner na port 81 na hostitelském počítači.</span><span class="sxs-lookup"><span data-stu-id="35c80-209">Forward the exposed port 80 on the container to port 81 on the host machine</span></span>

- <span data-ttu-id="35c80-210">Připojte adresář projektu na hostiteli, aby se/Code v rámci kontejneru, což vám umožní upravit kód bez nutnosti opětovného sestavení image.</span><span class="sxs-lookup"><span data-stu-id="35c80-210">Mount the project directory on the host to /code within the container, making it possible for you to modify the code without having to rebuild the image</span></span>

- <span data-ttu-id="35c80-211">Propojení webové služby se službou Redis</span><span class="sxs-lookup"><span data-stu-id="35c80-211">Link the web service to the redis service</span></span>

<span data-ttu-id="35c80-212">Služba Redis používá [nejnovější veřejnou image Redis](https://hub.docker.com/_/redis/) získanou z registru Docker Hub.</span><span class="sxs-lookup"><span data-stu-id="35c80-212">The redis service uses the [latest public redis image](https://hub.docker.com/_/redis/) pulled from the Docker Hub registry.</span></span> <span data-ttu-id="35c80-213">[Redis](https://redis.io/) je oblíbený systém mezipaměti pro aplikace na straně serveru.</span><span class="sxs-lookup"><span data-stu-id="35c80-213">[redis](https://redis.io/) is a popular cache system for server-side applications.</span></span>

### <a name="step-5-build-and-run-your-docker-app"></a><span data-ttu-id="35c80-214">Krok 5: sestavení a spuštění aplikace Docker</span><span class="sxs-lookup"><span data-stu-id="35c80-214">Step 5: Build and run your Docker app</span></span>

<span data-ttu-id="35c80-215">Pokud má vaše aplikace jenom jeden kontejner, stačí ho spustit nasazením na hostitele Docker (virtuální počítač nebo fyzický server).</span><span class="sxs-lookup"><span data-stu-id="35c80-215">If your app has only a single container, you just need to run it by deploying it to your Docker Host (VM or physical server).</span></span> <span data-ttu-id="35c80-216">Pokud je ale vaše aplikace tvořená více službami, je nutné *ji vytvořit*také.</span><span class="sxs-lookup"><span data-stu-id="35c80-216">However, if your app is made up of multiple services, you need to *compose it*, too.</span></span> <span data-ttu-id="35c80-217">Pojďme se podívat na různé možnosti.</span><span class="sxs-lookup"><span data-stu-id="35c80-217">Let's see the different options.</span></span>

<span data-ttu-id="35c80-218">***Možnost A: spuštění jednoho kontejneru nebo služby***</span><span class="sxs-lookup"><span data-stu-id="35c80-218">***Option A: Run a single container or service***</span></span>

<span data-ttu-id="35c80-219">Bitovou kopii Docker můžete spustit pomocí příkazu Docker Run, jak je znázorněno zde:</span><span class="sxs-lookup"><span data-stu-id="35c80-219">You can run the Docker image by using the docker run command, as shown here:</span></span>

```console
docker run -t -d -p 80:5000 cesardl/netcore-webapi-microservice-docker:first
```

<span data-ttu-id="35c80-220">U tohoto konkrétního nasazení budeme přesměrování požadavků odeslaných na port 80 na interní port 5000.</span><span class="sxs-lookup"><span data-stu-id="35c80-220">For this particular deployment, we'll be redirecting requests sent to port 80 to the internal port 5000.</span></span> <span data-ttu-id="35c80-221">Aplikace nyní naslouchá na externím portu 80 na úrovni hostitele.</span><span class="sxs-lookup"><span data-stu-id="35c80-221">Now the application is listening on the external port 80 at the host level.</span></span>

<span data-ttu-id="35c80-222">***Možnost B: vytvoření a spuštění aplikace s více kontejnery***</span><span class="sxs-lookup"><span data-stu-id="35c80-222">***Option B: Compose and run a multiple-container application***</span></span>

<span data-ttu-id="35c80-223">Ve většině podnikových scénářů se aplikace Docker skládá z několika služeb.</span><span class="sxs-lookup"><span data-stu-id="35c80-223">In most enterprise scenarios, a Docker application will be composed of multiple services.</span></span> <span data-ttu-id="35c80-224">V těchto případech můžete spustit příkaz `docker-compose up` (obrázek 4-27), který bude používat soubor Docker-Compose. yml, který jste mohli dříve vytvořit.</span><span class="sxs-lookup"><span data-stu-id="35c80-224">For these cases, you can run the `docker-compose up` command (Figure 4-27), which will use the docker-compose.yml file that you might have created previously.</span></span> <span data-ttu-id="35c80-225">Spuštěním tohoto příkazu nasadíte složenou aplikaci se všemi souvisejícími kontejnery.</span><span class="sxs-lookup"><span data-stu-id="35c80-225">Running this command deploys a composed application with all of its related containers.</span></span>

![Výstup konzoly z příkazu Docker-sestavit.](./media/docker-apps-inner-loop-workflow/results-docker-compose-up.png)

<span data-ttu-id="35c80-227">**Obrázek 4-27**.</span><span class="sxs-lookup"><span data-stu-id="35c80-227">**Figure 4-27**.</span></span> <span data-ttu-id="35c80-228">Výsledky spuštění příkazu Docker-sestavit</span><span class="sxs-lookup"><span data-stu-id="35c80-228">Results of running the "docker-compose up" command</span></span>

<span data-ttu-id="35c80-229">Po spuštění `docker-compose up`nasadíte aplikaci a její související kontejnery do hostitele Docker, jak je znázorněno na obrázku 4-28 ve formě reprezentace virtuálního počítače.</span><span class="sxs-lookup"><span data-stu-id="35c80-229">After you run `docker-compose up`, you deploy your application and its related container(s) into your Docker Host, as illustrated in Figure 4-28, in the VM representation.</span></span>

![Virtuální počítač spouštějící aplikace s více kontejnery.](./media/docker-apps-inner-loop-workflow/vm-with-docker-containers-deployed.png)

<span data-ttu-id="35c80-231">**Obrázek 4-28**.</span><span class="sxs-lookup"><span data-stu-id="35c80-231">**Figure 4-28**.</span></span> <span data-ttu-id="35c80-232">Virtuální počítač s nasazenými kontejnery Docker</span><span class="sxs-lookup"><span data-stu-id="35c80-232">VM with Docker containers deployed</span></span>

### <a name="step-6-test-your-docker-application-locally-in-your-local-cd-vm"></a><span data-ttu-id="35c80-233">Krok 6: testování aplikace Docker (místně, na místním VIRTUÁLNÍm počítači CD)</span><span class="sxs-lookup"><span data-stu-id="35c80-233">Step 6: Test your Docker application (locally, in your local CD VM)</span></span>

<span data-ttu-id="35c80-234">Tento krok se bude lišit v závislosti na tom, co vaše aplikace dělá.</span><span class="sxs-lookup"><span data-stu-id="35c80-234">This step will vary depending on what your app is doing.</span></span>

<span data-ttu-id="35c80-235">V jednoduchém webovém rozhraní API .NET Core "Hello World" nasazené jako jediný kontejner nebo služba budete potřebovat přístup ke službě pouze zadáním portu TCP určeného v souboru Dockerfile.</span><span class="sxs-lookup"><span data-stu-id="35c80-235">In a simple .NET Core Web API "Hello World" deployed as a single container or service, you'd just need to access the service by providing the TCP port specified in the DockerFile.</span></span>

<span data-ttu-id="35c80-236">Pokud není místní počítač zapnutý, přejděte k vaší službě a vyhledejte IP adresu počítače pomocí tohoto příkazu:</span><span class="sxs-lookup"><span data-stu-id="35c80-236">If localhost is not turned on, to navigate to your service, find the IP address for the machine by using this command:</span></span>

```console
docker-machine {IP} {YOUR-CONTAINER-NAME}
```

<span data-ttu-id="35c80-237">V hostiteli Docker otevřete prohlížeč a přejděte k této lokalitě. měla by se zobrazit vaše aplikace nebo služba, jak je znázorněno na obrázku 4-29.</span><span class="sxs-lookup"><span data-stu-id="35c80-237">On the Docker host, open a browser and navigate to that site; you should see your app/service running, as demonstrated in Figure 4-29.</span></span>

![Zobrazení prohlížeče odpovědi z místního hostitele/rozhraní API/hodnot.](./media/docker-apps-inner-loop-workflow/test-docker-app-locally-localhost.png)

<span data-ttu-id="35c80-239">**Obrázek 4-29**.</span><span class="sxs-lookup"><span data-stu-id="35c80-239">**Figure 4-29**.</span></span> <span data-ttu-id="35c80-240">Místní testování aplikace Docker pomocí místního hostitele</span><span class="sxs-lookup"><span data-stu-id="35c80-240">Testing your Docker application locally using localhost</span></span>

<span data-ttu-id="35c80-241">Všimněte si, že používá port 80, ale interně se přesměruje na port 5000, protože to je jak bylo nasazeno v `docker run`, jak bylo vysvětleno výše.</span><span class="sxs-lookup"><span data-stu-id="35c80-241">Note that it's using port 80, but internally it's being redirected to port 5000, because that's how it was deployed with `docker run`, as explained earlier.</span></span>

<span data-ttu-id="35c80-242">Tuto možnost můžete otestovat pomocí OBLÉ z terminálu.</span><span class="sxs-lookup"><span data-stu-id="35c80-242">You can test this by using CURL from the terminal.</span></span> <span data-ttu-id="35c80-243">V instalaci Docker ve Windows je výchozí IP adresa 10.0.75.1, jak je znázorněno na obrázku 4-30.</span><span class="sxs-lookup"><span data-stu-id="35c80-243">In a Docker installation on Windows, the default IP is 10.0.75.1, as depicted in Figure 4-30.</span></span>

![Výstup na konzole z části získání http://10.0.75.1/API/values s kudrlinkou](./media/docker-apps-inner-loop-workflow/test-docker-app-locally-curl.png)

<span data-ttu-id="35c80-245">**Obrázek 4-30**.</span><span class="sxs-lookup"><span data-stu-id="35c80-245">**Figure 4-30**.</span></span> <span data-ttu-id="35c80-246">Místní testování aplikace Docker pomocí OBLÉ</span><span class="sxs-lookup"><span data-stu-id="35c80-246">Testing a Docker application locally by using CURL</span></span>

<span data-ttu-id="35c80-247">**Ladění kontejneru spuštěného v Docker**</span><span class="sxs-lookup"><span data-stu-id="35c80-247">**Debugging a container running on Docker**</span></span>

<span data-ttu-id="35c80-248">Visual Studio Code podporuje ladění Docker, pokud používáte Node. js a jiné platformy, jako jsou kontejnery .NET Core.</span><span class="sxs-lookup"><span data-stu-id="35c80-248">Visual Studio Code supports debugging Docker if you're using Node.js and other platforms like .NET Core containers.</span></span>

<span data-ttu-id="35c80-249">Při použití sady Visual Studio pro Windows nebo Mac můžete v Docker ladit také kontejnery .NET Core nebo .NET Framework, jak je popsáno v následující části.</span><span class="sxs-lookup"><span data-stu-id="35c80-249">You also can debug .NET Core or .NET Framework containers in Docker when using Visual Studio for Windows or Mac, as described in the next section.</span></span>

> [!TIP]
> <span data-ttu-id="35c80-250">Další informace o ladění kontejnerů Docker Node. js naleznete v tématu <https://blog.docker.com/2016/07/live-debugging-docker/> a <https://blogs.msdn.microsoft.com/user_ed/2016/02/27/visual-studio-code-new-features-13-big-debugging-updates-rich-object-hover-conditional-breakpoints-node-js-mono-more/>.</span><span class="sxs-lookup"><span data-stu-id="35c80-250">To learn more about debugging Node.js Docker containers, see <https://blog.docker.com/2016/07/live-debugging-docker/> and <https://blogs.msdn.microsoft.com/user_ed/2016/02/27/visual-studio-code-new-features-13-big-debugging-updates-rich-object-hover-conditional-breakpoints-node-js-mono-more/>.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="35c80-251">[Předchozí](docker-apps-development-environment.md)
>[Další](visual-studio-tools-for-docker.md)</span><span class="sxs-lookup"><span data-stu-id="35c80-251">[Previous](docker-apps-development-environment.md)
[Next](visual-studio-tools-for-docker.md)</span></span>
