---
title: Pracovní postup vývoje vnitřní smyčky pro aplikace Dockeru
description: Přečtěte si o pracovním postupu pro vývoj vnitřních smyček pro aplikace Docker.
ms.date: 08/06/2020
ms.openlocfilehash: bf837ab53fff2b53cf141b2e621d484cff9b6889
ms.sourcegitcommit: ef50c99928183a0bba75e07b9f22895cd4c480f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/07/2020
ms.locfileid: "87916183"
---
# <a name="inner-loop-development-workflow-for-docker-apps"></a><span data-ttu-id="2dc23-103">Pracovní postup vývoje vnitřní smyčky pro aplikace Dockeru</span><span class="sxs-lookup"><span data-stu-id="2dc23-103">Inner-loop development workflow for Docker apps</span></span>

<span data-ttu-id="2dc23-104">Předtím, než se aktivuje pracovní postup vnější smyčky zahrnující celý cyklus DevOps, začne vše v každém počítači vývojářů, bude se zakódovat vlastní aplikace, pomocí svých preferovaných jazyků nebo platforem a místně se testuje (obrázek 4-21).</span><span class="sxs-lookup"><span data-stu-id="2dc23-104">Before triggering the outer-loop workflow spanning the entire DevOps cycle, it all begins on each developer's machine, coding the app itself, using their preferred languages or platforms, and testing it locally (Figure 4-21).</span></span> <span data-ttu-id="2dc23-105">V každém případě ale budete mít důležitý obecný bod, bez ohledu na to, jaký jazyk, rozhraní nebo platformy si zvolíte.</span><span class="sxs-lookup"><span data-stu-id="2dc23-105">But in every case, you'll have an important point in common, no matter what language, framework, or platforms you choose.</span></span> <span data-ttu-id="2dc23-106">V tomto konkrétním pracovním postupu budete vždy vyvíjet a testovat kontejnery Docker v jiných prostředích, ale lokálně.</span><span class="sxs-lookup"><span data-stu-id="2dc23-106">In this specific workflow, you're always developing and testing Docker containers in no other environments, but locally.</span></span>

![Diagram znázorňující koncept prostředí pro vývoj vnitřních smyček.](./media/docker-apps-inner-loop-workflow/inner-loop-development-context.png)

<span data-ttu-id="2dc23-108">**Obrázek 4-21**.</span><span class="sxs-lookup"><span data-stu-id="2dc23-108">**Figure 4-21**.</span></span> <span data-ttu-id="2dc23-109">Vývojový kontext pro vnitřní smyčku</span><span class="sxs-lookup"><span data-stu-id="2dc23-109">Inner-loop development context</span></span>

<span data-ttu-id="2dc23-110">Kontejner nebo instance image Docker bude obsahovat tyto komponenty:</span><span class="sxs-lookup"><span data-stu-id="2dc23-110">The container or instance of a Docker image will contain these components:</span></span>

- <span data-ttu-id="2dc23-111">Výběr operačního systému (například distribuce systému Linux nebo Windows)</span><span class="sxs-lookup"><span data-stu-id="2dc23-111">An operating system selection (for example, a Linux distribution or Windows)</span></span>

- <span data-ttu-id="2dc23-112">Soubory přidané vývojářem (například binární soubory aplikace)</span><span class="sxs-lookup"><span data-stu-id="2dc23-112">Files added by the developer (for example, app binaries)</span></span>

- <span data-ttu-id="2dc23-113">Konfigurace (například nastavení prostředí a závislosti)</span><span class="sxs-lookup"><span data-stu-id="2dc23-113">Configuration (for example, environment settings and dependencies)</span></span>

- <span data-ttu-id="2dc23-114">Pokyny pro procesy, které se mají spustit přes Docker</span><span class="sxs-lookup"><span data-stu-id="2dc23-114">Instructions for what processes to run by Docker</span></span>

<span data-ttu-id="2dc23-115">Můžete nastavit vývojový postup pro vnitřní smyčku, který využívá Docker jako proces (popsaný v následující části).</span><span class="sxs-lookup"><span data-stu-id="2dc23-115">You can set up the inner-loop development workflow that utilizes Docker as the process (described in the next section).</span></span> <span data-ttu-id="2dc23-116">Vezměte v úvahu, že nejsou zahrnuté počáteční kroky pro nastavení prostředí, protože ho stačí udělat jenom jednou.</span><span class="sxs-lookup"><span data-stu-id="2dc23-116">Consider that the initial steps to set up the environment are not included, because you only need to do it once.</span></span>

## <a name="building-a-single-app-within-a-docker-container-using-visual-studio-code-and-docker-cli"></a><span data-ttu-id="2dc23-117">Vytvoření jedné aplikace v kontejneru Docker pomocí Visual Studio Code a Docker CLI</span><span class="sxs-lookup"><span data-stu-id="2dc23-117">Building a single app within a Docker container using Visual Studio Code and Docker CLI</span></span>

<span data-ttu-id="2dc23-118">Aplikace se vytvářejí z vašich vlastních služeb a dalších knihoven (závislosti).</span><span class="sxs-lookup"><span data-stu-id="2dc23-118">Apps are made up from your own services plus additional libraries (dependencies).</span></span>

<span data-ttu-id="2dc23-119">Obrázek 4-22 ukazuje základní kroky, které obvykle potřebujete provést při sestavování aplikace Docker, po kterém následují podrobné popisy jednotlivých kroků.</span><span class="sxs-lookup"><span data-stu-id="2dc23-119">Figure 4-22 shows the basic steps that you usually need to carry out when building a Docker app, followed by detailed descriptions of each step.</span></span>

![Diagram znázorňující sedm kroků, které je potřeba k vytvoření kontejnerové aplikace.](./media/docker-apps-inner-loop-workflow/life-cycle-containerized-apps-docker-cli.png)

<span data-ttu-id="2dc23-121">**Obrázek 4-22**.</span><span class="sxs-lookup"><span data-stu-id="2dc23-121">**Figure 4-22**.</span></span> <span data-ttu-id="2dc23-122">Pracovní postup vysoké úrovně pro životní cyklus aplikací Docker s využitím Docker CLI</span><span class="sxs-lookup"><span data-stu-id="2dc23-122">High-level workflow for the life cycle for Docker containerized applications using Docker CLI</span></span>

### <a name="step-1-start-coding-in-visual-studio-code-and-create-your-initial-appservice-baseline"></a><span data-ttu-id="2dc23-123">Krok 1: začátek kódování Visual Studio Code a vytvoření počátečního směrného plánu aplikace nebo služby</span><span class="sxs-lookup"><span data-stu-id="2dc23-123">Step 1: Start coding in Visual Studio Code and create your initial app/service baseline</span></span>

<span data-ttu-id="2dc23-124">Způsob vývoje aplikace je podobný způsobu, jakým jste to provedete bez Docker.</span><span class="sxs-lookup"><span data-stu-id="2dc23-124">The way you develop your application is similar to the way you do it without Docker.</span></span> <span data-ttu-id="2dc23-125">Rozdíl je v tom, že při vývoji nasazujete a testujete svou aplikaci nebo služby běžící v kontejnerech Docker umístěných ve vašem místním prostředí (jako je třeba virtuální počítač Linux nebo Windows).</span><span class="sxs-lookup"><span data-stu-id="2dc23-125">The difference is that while developing, you're deploying and testing your application or services running within Docker containers placed in your local environment (like a Linux VM or Windows).</span></span>

<span data-ttu-id="2dc23-126">**Nastavení místního prostředí**</span><span class="sxs-lookup"><span data-stu-id="2dc23-126">**Setting up your local environment**</span></span>

<span data-ttu-id="2dc23-127">S nejnovějšími verzemi Docker desktopu pro Mac a Windows je snazší než kdy dřív vyvíjet aplikace Docker a instalace je jednoduchá.</span><span class="sxs-lookup"><span data-stu-id="2dc23-127">With the latest versions of Docker Desktop for Mac and Windows, it's easier than ever to develop Docker applications, and the setup is straightforward.</span></span>

> [!TIP]
> <span data-ttu-id="2dc23-128">Pokyny k nastavení Docker desktopu pro Windows najdete v tématu <https://docs.docker.com/docker-for-windows/> .</span><span class="sxs-lookup"><span data-stu-id="2dc23-128">For instructions on setting up Docker Desktop for Windows, go to <https://docs.docker.com/docker-for-windows/>.</span></span>
>
> <span data-ttu-id="2dc23-129">Pokyny, jak nastavit Docker Desktop pro Mac, najdete v tématu <https://docs.docker.com/docker-for-mac/> .</span><span class="sxs-lookup"><span data-stu-id="2dc23-129">For instructions on setting up Docker Desktop for Mac, go to <https://docs.docker.com/docker-for-mac/>.</span></span>

<span data-ttu-id="2dc23-130">Kromě toho budete potřebovat Editor kódu, abyste mohli skutečně vyvíjet aplikace při použití Docker CLI.</span><span class="sxs-lookup"><span data-stu-id="2dc23-130">In addition, you'll need a code editor so that you can actually develop your application while using Docker CLI.</span></span>

<span data-ttu-id="2dc23-131">Společnost Microsoft poskytuje Visual Studio Code, což je zjednodušený Editor kódu, který je podporován v systémech Windows, Linux a macOS a poskytuje technologii IntelliSense s [podporou pro řadu jazyků](https://code.visualstudio.com/docs/languages/overview) (JavaScript, .NET, jít, Java, Ruby, Python a většina moderních jazyků), [ladění](https://code.visualstudio.com/Docs/editor/debugging), [integrace s podporou Gitu](https://code.visualstudio.com/Docs/editor/versioncontrol) a [rozšíření](https://code.visualstudio.com/docs/extensions/overview).</span><span class="sxs-lookup"><span data-stu-id="2dc23-131">Microsoft provides Visual Studio Code, which is a lightweight code editor that's supported on Windows, Linux, and macOS, and provides IntelliSense with [support for many languages](https://code.visualstudio.com/docs/languages/overview) (JavaScript, .NET, Go, Java, Ruby, Python, and most modern languages), [debugging](https://code.visualstudio.com/Docs/editor/debugging), [integration with Git](https://code.visualstudio.com/Docs/editor/versioncontrol) and [extensions support](https://code.visualstudio.com/docs/extensions/overview).</span></span> <span data-ttu-id="2dc23-132">Tento editor je vhodný pro vývojáře v macOS a Linux.</span><span class="sxs-lookup"><span data-stu-id="2dc23-132">This editor is a great fit for macOS and Linux developers.</span></span> <span data-ttu-id="2dc23-133">V systému Windows můžete použít také aplikaci Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="2dc23-133">In Windows, you also can use Visual Studio.</span></span>

> [!TIP]
> <span data-ttu-id="2dc23-134">Pokyny, jak nainstalovat Visual Studio Code pro Windows, Linux nebo macOS, najdete v tématu <https://code.visualstudio.com/docs/setup/setup-overview/> .</span><span class="sxs-lookup"><span data-stu-id="2dc23-134">For instructions on installing Visual Studio Code for Windows, Linux, or macOS, go to <https://code.visualstudio.com/docs/setup/setup-overview/>.</span></span>
>
> <span data-ttu-id="2dc23-135">Pokyny, jak nastavit Docker pro Mac, najdete v tématu <https://docs.docker.com/docker-for-mac/> .</span><span class="sxs-lookup"><span data-stu-id="2dc23-135">For instructions on setting up Docker for Mac, go to <https://docs.docker.com/docker-for-mac/>.</span></span>

<span data-ttu-id="2dc23-136">Můžete pracovat s Docker CLI a napsat svůj kód pomocí editoru kódu, ale použití Visual Studio Code s rozšířením Docker usnadňuje tvorbu `Dockerfile` a vytváření `docker-compose.yml` souborů v pracovním prostoru.</span><span class="sxs-lookup"><span data-stu-id="2dc23-136">You can work with Docker CLI and write your code using any code editor, but using Visual Studio Code with the Docker extension makes it easy to author `Dockerfile` and `docker-compose.yml` files in your workspace.</span></span> <span data-ttu-id="2dc23-137">Můžete také spouštět úlohy a skripty z Visual Studio Code integrované vývojové prostředí (IDE) a spustit příkazy Docker pomocí příkazu Docker CLI pod.</span><span class="sxs-lookup"><span data-stu-id="2dc23-137">You can also run tasks and scripts from the Visual Studio Code IDE to execute Docker commands using the Docker CLI underneath.</span></span>

<span data-ttu-id="2dc23-138">Rozšíření Docker pro VS Code poskytuje následující funkce:</span><span class="sxs-lookup"><span data-stu-id="2dc23-138">The Docker extension for VS Code provides the following features:</span></span>

- <span data-ttu-id="2dc23-139">Automatické `Dockerfile` `docker-compose.yml` generování souborů a souborů</span><span class="sxs-lookup"><span data-stu-id="2dc23-139">Automatic `Dockerfile` and `docker-compose.yml` file generation</span></span>

- <span data-ttu-id="2dc23-140">Zvýrazňování syntaxe a tipy k najetí myší pro `docker-compose.yml` `Dockerfile` soubory a</span><span class="sxs-lookup"><span data-stu-id="2dc23-140">Syntax highlighting and hover tips for `docker-compose.yml` and `Dockerfile` files</span></span>

- <span data-ttu-id="2dc23-141">IntelliSense (dokončování) pro `Dockerfile` `docker-compose.yml` soubory a</span><span class="sxs-lookup"><span data-stu-id="2dc23-141">IntelliSense (completions) for `Dockerfile` and `docker-compose.yml` files</span></span>

- <span data-ttu-id="2dc23-142">Linting (chyby a upozornění) pro `Dockerfile` soubory</span><span class="sxs-lookup"><span data-stu-id="2dc23-142">Linting (errors and warnings) for `Dockerfile` files</span></span>

- <span data-ttu-id="2dc23-143">Integrace palet příkazů (F1) pro nejběžnější příkazy Docker</span><span class="sxs-lookup"><span data-stu-id="2dc23-143">Command Palette (F1) integration for the most common Docker commands</span></span>

- <span data-ttu-id="2dc23-144">Integrace Průzkumníka pro správu imagí a kontejnerů</span><span class="sxs-lookup"><span data-stu-id="2dc23-144">Explorer integration for managing Images and Containers</span></span>

- <span data-ttu-id="2dc23-145">Nasazení imagí z Dockerhubu a kontejnerů Azure Container Registry do Azure App Service</span><span class="sxs-lookup"><span data-stu-id="2dc23-145">Deploy images from DockerHub and Azure Container Registries to Azure App Service</span></span>

<span data-ttu-id="2dc23-146">Chcete-li nainstalovat rozšíření Docker, stiskněte klávesy CTRL + SHIFT + P, zadejte `ext install` a poté spusťte příkaz Install Extension a zobrazte seznam rozšíření Marketplace.</span><span class="sxs-lookup"><span data-stu-id="2dc23-146">To install the Docker extension, press Ctrl+Shift+P, type `ext install`, and then run the Install Extension command to bring up the Marketplace extension list.</span></span> <span data-ttu-id="2dc23-147">Potom zadejte **Docker** pro filtrování výsledků a pak vyberte rozšíření podpora Docker, jak je znázorněno na obrázku 4-23.</span><span class="sxs-lookup"><span data-stu-id="2dc23-147">Next, type **docker** to filter the results, and then select the Docker Support extension, as depicted in Figure 4-23.</span></span>

![Zobrazení rozšíření Docker pro VS Code.](media/docker-apps-inner-loop-workflow/install-docker-extension-vs-code.png)

<span data-ttu-id="2dc23-149">**Obrázek 4-23**.</span><span class="sxs-lookup"><span data-stu-id="2dc23-149">**Figure 4-23**.</span></span> <span data-ttu-id="2dc23-150">Instalace rozšíření Docker v Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="2dc23-150">Installing the Docker Extension in Visual Studio Code</span></span>

### <a name="step-2-create-a-dockerfile-related-to-an-existing-image-plain-os-or-dev-environments-like-net-core-nodejs-and-ruby"></a><span data-ttu-id="2dc23-151">Krok 2: vytvoření souboru Dockerfile souvisejícího s existující imagí (prostého operačního systému nebo vývojového prostředí, jako je .NET Core, Node.js a Ruby)</span><span class="sxs-lookup"><span data-stu-id="2dc23-151">Step 2: Create a DockerFile related to an existing image (plain OS or dev environments like .NET Core, Node.js, and Ruby)</span></span>

<span data-ttu-id="2dc23-152">Budete potřebovat `DockerFile` vlastní image, která se má sestavit a na kontejner, který se má nasadit.</span><span class="sxs-lookup"><span data-stu-id="2dc23-152">You'll need a `DockerFile` per custom image to be built and per container to be deployed.</span></span> <span data-ttu-id="2dc23-153">Pokud se vaše aplikace skládá z jedné vlastní služby, budete potřebovat jednu `DockerFile` .</span><span class="sxs-lookup"><span data-stu-id="2dc23-153">If your app is made up of single custom service, you'll need a single `DockerFile`.</span></span> <span data-ttu-id="2dc23-154">Pokud se ale vaše aplikace skládá z několika služeb (jako v architektuře mikroslužeb), budete ji potřebovat `Dockerfile` pro každou službu.</span><span class="sxs-lookup"><span data-stu-id="2dc23-154">But if your app is composed of multiple services (as in a microservices architecture), you'll need one `Dockerfile` per service.</span></span>

<span data-ttu-id="2dc23-155">`DockerFile`Obvykle se nachází v kořenové složce vaší aplikace nebo služby a obsahuje požadované příkazy, aby Docker věděl, jak nastavit a spustit tuto aplikaci nebo službu.</span><span class="sxs-lookup"><span data-stu-id="2dc23-155">The `DockerFile` is commonly placed in the root folder of your app or service and contains the required commands so that Docker knows how to set up and run that app or service.</span></span> <span data-ttu-id="2dc23-156">Můžete vytvořit `DockerFile` a přidat ho do projektu společně s vaším kódem (node.js, .NET Core atd.), nebo pokud s prostředím začínáte, podívejte se na následující tip.</span><span class="sxs-lookup"><span data-stu-id="2dc23-156">You can create your `DockerFile` and add it to your project along with your code (node.js, .NET Core, etc.), or, if you're new to the environment, take a look at the following Tip.</span></span>

> [!TIP]
> <span data-ttu-id="2dc23-157">Můžete použít rozšíření Docker, které vás provede při použití `Dockerfile` `docker-compose.yml` souborů a souvisejících s kontejnery Docker.</span><span class="sxs-lookup"><span data-stu-id="2dc23-157">You can use the Docker extension to guide you when using the `Dockerfile` and `docker-compose.yml` files related to your Docker containers.</span></span> <span data-ttu-id="2dc23-158">Nakonec budete pravděpodobně zapisovat tyto typy souborů bez tohoto nástroje, ale používání rozšíření Docker je dobrým výchozím bodem, který zrychlí výukovou křivku.</span><span class="sxs-lookup"><span data-stu-id="2dc23-158">Eventually, you'll probably write these kinds of files without this tool, but using the Docker extension is a good starting point that will accelerate your learning curve.</span></span>

<span data-ttu-id="2dc23-159">Na obrázku 4-24 se můžete podívat na postup přidání souborů Docker do projektu pomocí rozšíření Docker pro VS Code:</span><span class="sxs-lookup"><span data-stu-id="2dc23-159">In Figure 4-24, you can see the steps to add the docker files to a project by using the Docker Extension for VS Code:</span></span>

1. <span data-ttu-id="2dc23-160">Otevřete paletu příkazů, zadejte "**Docker**" a vyberte**Přidat soubory Docker do pracovního prostoru**.</span><span class="sxs-lookup"><span data-stu-id="2dc23-160">Open the command palette, type "**docker**" and select "**Add Docker Files to Workspace**".</span></span>
2. <span data-ttu-id="2dc23-161">Vybrat aplikační platformu (ASP.NET Core)</span><span class="sxs-lookup"><span data-stu-id="2dc23-161">Select Application Platform (ASP.NET Core)</span></span>
3. <span data-ttu-id="2dc23-162">Vybrat operační systém (Linux)</span><span class="sxs-lookup"><span data-stu-id="2dc23-162">Select Operating System (Linux)</span></span>
4. <span data-ttu-id="2dc23-163">Zahrnout volitelné Docker Compose soubory</span><span class="sxs-lookup"><span data-stu-id="2dc23-163">Include optional Docker Compose files</span></span>
5. <span data-ttu-id="2dc23-164">Zadejte porty k publikování (80, 443).</span><span class="sxs-lookup"><span data-stu-id="2dc23-164">Enter ports to publish (80, 443)</span></span>
6. <span data-ttu-id="2dc23-165">Výběr projektu</span><span class="sxs-lookup"><span data-stu-id="2dc23-165">Select the project</span></span>

![Postup přidání souborů Docker s rozšířením Docker](media/docker-apps-inner-loop-workflow/add-docker-files-to-workspace-command.png)

<span data-ttu-id="2dc23-167">**Obrázek 4-24**.</span><span class="sxs-lookup"><span data-stu-id="2dc23-167">**Figure 4-24**.</span></span> <span data-ttu-id="2dc23-168">Soubory Docker přidané pomocí příkazu **Přidat soubory Docker do pracovního prostoru**</span><span class="sxs-lookup"><span data-stu-id="2dc23-168">Docker files added using the **Add Docker files to Workspace** command</span></span>

<span data-ttu-id="2dc23-169">Když přidáte souboru Dockerfile, určíte, jakou základní image Docker budete používat (například pomocí `FROM mcr.microsoft.com/dotnet/core/aspnet` ).</span><span class="sxs-lookup"><span data-stu-id="2dc23-169">When you add a DockerFile, you specify what base Docker image you'll be using (like using `FROM mcr.microsoft.com/dotnet/core/aspnet`).</span></span> <span data-ttu-id="2dc23-170">Obvykle sestavíte vlastní image na základní imagi, kterou získáte z oficiálního úložiště v [registru Docker Hub](https://hub.docker.com/) (jako je [image pro .NET Core](https://hub.docker.com/_/microsoft-dotnet-core/) nebo ta [pro Node.js](https://hub.docker.com/_/node/)).</span><span class="sxs-lookup"><span data-stu-id="2dc23-170">You'll usually build your custom image on top of a base image that you get from any official repository at the [Docker Hub registry](https://hub.docker.com/) (like an [image for .NET Core](https://hub.docker.com/_/microsoft-dotnet-core/) or the one [for Node.js](https://hub.docker.com/_/node/)).</span></span>

> [!TIP]
> <span data-ttu-id="2dc23-171">Tento postup budete muset opakovat pro každý projekt ve vaší aplikaci.</span><span class="sxs-lookup"><span data-stu-id="2dc23-171">You'll have to repeat this procedure for every project in your application.</span></span> <span data-ttu-id="2dc23-172">Rozšíření však vyzve k přepsání vygenerovaného souboru Docker-rekládací soubor po prvním spuštění.</span><span class="sxs-lookup"><span data-stu-id="2dc23-172">However, the extension will ask to overwrite the generated docker-compose file after the first time.</span></span> <span data-ttu-id="2dc23-173">Měli byste odpovědět na Nepřepisovat, takže rozšíření vytvoří samostatné soubory Docker-skládání, které pak můžete sloučit před spuštěním Docker-skládání.</span><span class="sxs-lookup"><span data-stu-id="2dc23-173">You should reply to not overwrite it, so the extension creates separate docker-compose files, that you can then merge by hand, prior to running docker-compose.</span></span>

<span data-ttu-id="2dc23-174">**_Použití stávající oficiální image Docker_**</span><span class="sxs-lookup"><span data-stu-id="2dc23-174">**_Use an existing official Docker image_**</span></span>

<span data-ttu-id="2dc23-175">Použití oficiálního úložiště jazykové sady s číslem verze zajišťuje, aby byly stejné funkce jazyka dostupné na všech počítačích (včetně vývoje, testování a produkčního prostředí).</span><span class="sxs-lookup"><span data-stu-id="2dc23-175">Using an official repository of a language stack with a version number ensures that the same language features are available on all machines (including development, testing, and production).</span></span>

<span data-ttu-id="2dc23-176">Následuje ukázkový souboru Dockerfile pro kontejner .NET Core:</span><span class="sxs-lookup"><span data-stu-id="2dc23-176">The following is a sample DockerFile for a .NET Core container:</span></span>

```Dockerfile
FROM mcr.microsoft.com/dotnet/core/aspnet:3.1 AS base
WORKDIR /app
EXPOSE 80
EXPOSE 443

FROM mcr.microsoft.com/dotnet/core/sdk:3.1 AS build
WORKDIR /src
COPY ["src/WebApi/WebApi.csproj", "src/WebApi/"]
RUN dotnet restore "src/WebApi/WebApi.csproj"
COPY . .
WORKDIR "/src/src/WebApi"
RUN dotnet build "WebApi.csproj" -c Release -o /app/build

FROM build AS publish
RUN dotnet publish "WebApi.csproj" -c Release -o /app/publish

FROM base AS final
WORKDIR /app
COPY --from=publish /app/publish .
ENTRYPOINT ["dotnet", "WebApi.dll"]
```

<span data-ttu-id="2dc23-177">V tomto případě je bitová kopie založená na verzi 3,1 oficiální image s ASP.NET Core Docker (více imagí pro Linux a Windows), jak je uvedeno na řádku `FROM mcr.microsoft.com/dotnet/core/aspnet:3.1` .</span><span class="sxs-lookup"><span data-stu-id="2dc23-177">In this case, the image is based on version 3.1 of the official ASP.NET Core Docker image (multi-arch for Linux and Windows), as per the line `FROM mcr.microsoft.com/dotnet/core/aspnet:3.1`.</span></span> <span data-ttu-id="2dc23-178">(Další informace o tomto tématu najdete na stránce [ASP.NET Core Docker image](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) a na stránce s [obrázkem rozhraní Docker .NET Core](https://hub.docker.com/_/microsoft-dotnet-core/) ).</span><span class="sxs-lookup"><span data-stu-id="2dc23-178">(For more information about this topic, see the [ASP.NET Core Docker Image](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) page and the [.NET Core Docker Image](https://hub.docker.com/_/microsoft-dotnet-core/) page).</span></span>

<span data-ttu-id="2dc23-179">V souboru Dockerfile můžete také dát Docker pokyn k naslouchání portu TCP, který budete používat za běhu (například port 80 nebo 443).</span><span class="sxs-lookup"><span data-stu-id="2dc23-179">In the DockerFile, you can also instruct Docker to listen to the TCP port that you'll use at runtime (such as port 80 or 443).</span></span>

<span data-ttu-id="2dc23-180">V souboru Dockerfile můžete určit další nastavení konfigurace v závislosti na jazyku a rozhraní, které používáte.</span><span class="sxs-lookup"><span data-stu-id="2dc23-180">You can specify additional configuration settings in the Dockerfile, depending on the language and framework you're using.</span></span> <span data-ttu-id="2dc23-181">Například `ENTRYPOINT` řádek s `["dotnet", "WebMvcApplication.dll"]` informacemi Docker pro spuštění aplikace .NET Core.</span><span class="sxs-lookup"><span data-stu-id="2dc23-181">For instance, the `ENTRYPOINT` line with `["dotnet", "WebMvcApplication.dll"]` tells Docker to run a .NET Core application.</span></span> <span data-ttu-id="2dc23-182">Pokud používáte sadu SDK a .NET Core CLI ( `dotnet CLI` ) k sestavování a spouštění aplikace .NET, toto nastavení by se lišilo.</span><span class="sxs-lookup"><span data-stu-id="2dc23-182">If you're using the SDK and the .NET Core CLI (`dotnet CLI`) to build and run the .NET application, this setting would be different.</span></span> <span data-ttu-id="2dc23-183">Klíčovým bodem a dalšími nastaveními závisí na jazyku a platformě, kterou zvolíte pro vaši aplikaci.</span><span class="sxs-lookup"><span data-stu-id="2dc23-183">The key point here is that the ENTRYPOINT line and other settings depend on the language and platform you choose for your application.</span></span>

> [!TIP]
> <span data-ttu-id="2dc23-184">Další informace o vytváření imagí Docker pro aplikace .NET Core naleznete v <https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images> .</span><span class="sxs-lookup"><span data-stu-id="2dc23-184">For more information about building Docker images for .NET Core applications, go to <https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images>.</span></span>
>
> <span data-ttu-id="2dc23-185">Další informace o vytváření vlastních imagí najdete na webu <https://docs.docker.com/engine/tutorials/dockerimages/> .</span><span class="sxs-lookup"><span data-stu-id="2dc23-185">To learn more about building your own images, go to <https://docs.docker.com/engine/tutorials/dockerimages/>.</span></span>

<span data-ttu-id="2dc23-186">**Použití úložišť imagí s více archy**</span><span class="sxs-lookup"><span data-stu-id="2dc23-186">**Use multi-arch image repositories**</span></span>

<span data-ttu-id="2dc23-187">Jeden název bitové kopie v úložišti může obsahovat varianty platformy, jako je například bitová kopie systému Linux a bitová kopie systému Windows.</span><span class="sxs-lookup"><span data-stu-id="2dc23-187">A single image name in a repo can contain platform variants, such as a Linux image and a Windows image.</span></span> <span data-ttu-id="2dc23-188">Tato funkce umožňuje dodavatelům, jako je Microsoft (základní tvůrci obrázků), vytvořit jedno úložiště pro pokrytí více platforem (tj. Linux a Windows).</span><span class="sxs-lookup"><span data-stu-id="2dc23-188">This feature allows vendors like Microsoft (base image creators) to create a single repo to cover multiple platforms (that is, Linux and Windows).</span></span> <span data-ttu-id="2dc23-189">Například úložiště [dotnet/Core/ASPNET](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) dostupné v registru Docker Hub poskytuje podporu pro systémy Linux a Windows nano Server pomocí stejného názvu image.</span><span class="sxs-lookup"><span data-stu-id="2dc23-189">For example, the [dotnet/core/aspnet](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) repository available in the Docker Hub registry provides support for Linux and Windows Nano Server by using the same image name.</span></span>

<span data-ttu-id="2dc23-190">Načtení image [dotnet/Core/ASPNET](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) z hostitele Windows vyžádá si variantu Windows, zatímco při vyřazování stejného názvu bitové kopie z hostitele se systémem Linux se zažádá o variantu systému Linux.</span><span class="sxs-lookup"><span data-stu-id="2dc23-190">Pulling the [dotnet/core/aspnet](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) image from a Windows host pulls the Windows variant, whereas pulling the same image name from a Linux host pulls the Linux variant.</span></span>

<span data-ttu-id="2dc23-191">**_Vytvoření základní Image od začátku_**</span><span class="sxs-lookup"><span data-stu-id="2dc23-191">**_Create your base image from scratch_**</span></span>

<span data-ttu-id="2dc23-192">Můžete vytvořit vlastní základní image Docker od začátku, jak je vysvětleno v tomto [článku](https://docs.docker.com/engine/userguide/eng-image/baseimages/) z Docker.</span><span class="sxs-lookup"><span data-stu-id="2dc23-192">You can create your own Docker base image from scratch as explained in this [article](https://docs.docker.com/engine/userguide/eng-image/baseimages/) from Docker.</span></span> <span data-ttu-id="2dc23-193">Tento scénář je pravděpodobně nevhodný pro vás, pokud právě začínáte s Docker, ale pokud chcete nastavit konkrétní bity vlastní základní image, můžete to provést.</span><span class="sxs-lookup"><span data-stu-id="2dc23-193">This scenario is probably not the best for you if you're just starting with Docker, but if you want to set the specific bits of your own base image, you can do it.</span></span>

### <a name="step-3-create-your-custom-docker-images-embedding-your-service-in-it"></a><span data-ttu-id="2dc23-194">Krok 3: vytvořte vlastní image Docker, ve kterých se služba vkládá.</span><span class="sxs-lookup"><span data-stu-id="2dc23-194">Step 3: Create your custom Docker images embedding your service in it</span></span>

<span data-ttu-id="2dc23-195">Pro každou vlastní službu, která se skládá z vaší aplikace, budete muset vytvořit související image.</span><span class="sxs-lookup"><span data-stu-id="2dc23-195">For each custom service that comprises your app, you'll need to create a related image.</span></span> <span data-ttu-id="2dc23-196">Pokud se vaše aplikace skládá z jediné služby nebo webové aplikace, budete potřebovat jenom jednu Image.</span><span class="sxs-lookup"><span data-stu-id="2dc23-196">If your app is made up of a single service or web app, you'll need just a single image.</span></span>

> [!NOTE]
> <span data-ttu-id="2dc23-197">Když vezmete v úvahu "DevOps pracovní postup vnějšího cyklu", image se vytvoří pomocí automatizovaného procesu sestavení pokaždé, když nahrajete zdrojový kód do úložiště Git (průběžná integrace), takže se image vytvoří v globálním prostředí ze zdrojového kódu.</span><span class="sxs-lookup"><span data-stu-id="2dc23-197">When taking into account the "outer-loop DevOps workflow", the images will be created by an automated build process whenever you push your source code to a Git repository (Continuous Integration), so the images will be created in that global environment from your source code.</span></span>
>
> <span data-ttu-id="2dc23-198">Před tím, než se podíváte na tuto trasu vnější smyčky, je nutné zajistit, aby aplikace Docker správně fungovala, aby nenabízela kód, který nemusí správně fungovat pro systém správy zdrojového kódu (Git atd.).</span><span class="sxs-lookup"><span data-stu-id="2dc23-198">But before you consider going to that outer-loop route, you need to ensure that the Docker application is actually working properly so that they don't push code that might not work properly to the source control system (Git, etc.).</span></span>
>
> <span data-ttu-id="2dc23-199">Proto každý vývojář nejprve potřebuje provést celý proces vnitřní smyčky pro místní testování a pokračovat ve vývoji, dokud nechce doručovat kompletní funkci nebo přepnout do systému správy zdrojového kódu.</span><span class="sxs-lookup"><span data-stu-id="2dc23-199">Therefore, each developer first needs to do the entire inner-loop process to test locally and continue developing until they want to push a complete feature or change to the source control system.</span></span>

<span data-ttu-id="2dc23-200">Pokud chcete vytvořit image v místním prostředí a používat souboru Dockerfile, můžete použít příkaz Docker Build, jak je znázorněno na obrázku 4-25, protože tento obrázek již pro vás vypadá a sestavuje image pro všechny služby v aplikaci pomocí jednoduchého příkazu.</span><span class="sxs-lookup"><span data-stu-id="2dc23-200">To create an image in your local environment and using the DockerFile, you can use the docker build command, as shown in Figure 4-25, because it already tags the image for you and builds the images for all services in the application with a simple command.</span></span>

![Snímek obrazovky s výstupem konzoly příkazu Docker-skládání buildu](media/docker-apps-inner-loop-workflow/run-docker-build-command.png)

<span data-ttu-id="2dc23-202">**Obrázek 4-25**.</span><span class="sxs-lookup"><span data-stu-id="2dc23-202">**Figure 4-25**.</span></span> <span data-ttu-id="2dc23-203">Spouští se sestavení Docker.</span><span class="sxs-lookup"><span data-stu-id="2dc23-203">Running docker build</span></span>

<span data-ttu-id="2dc23-204">Místo toho, aby bylo možné přímo spustit `docker build` ze složky projektu, můžete nejprve vygenerovat nasazovatelné složky s knihovnami .NET potřebné pomocí příkazu Run `dotnet publish` a potom spustit `docker build` .</span><span class="sxs-lookup"><span data-stu-id="2dc23-204">Optionally, instead of directly running `docker build` from the project folder, you first can generate a deployable folder with the .NET libraries needed by using the run `dotnet publish` command, and then run `docker build`.</span></span>

<span data-ttu-id="2dc23-205">Tento příklad vytvoří image Docker s názvem `explore-docker-vscode/webapi:latest` ( `:latest` je značka, jako je například specifická verze).</span><span class="sxs-lookup"><span data-stu-id="2dc23-205">This example creates a Docker image with the name `explore-docker-vscode/webapi:latest` (`:latest` is a tag, like a specific version).</span></span> <span data-ttu-id="2dc23-206">Tento krok můžete provést pro každou vlastní bitovou kopii, kterou potřebujete vytvořit pro svoji sestavenou aplikaci Docker s několika kontejnery.</span><span class="sxs-lookup"><span data-stu-id="2dc23-206">You can take this step for each custom image you need to create for your composed Docker application with several containers.</span></span> <span data-ttu-id="2dc23-207">V další části se ale dozvíme, že to je snazší pomocí `docker-compose` .</span><span class="sxs-lookup"><span data-stu-id="2dc23-207">However, we'll see in the next section that it's easier to do this using `docker-compose`.</span></span>

<span data-ttu-id="2dc23-208">Existující image můžete najít v místním úložišti (ve vývojovém počítači) pomocí `docker images` příkazu, jak je znázorněno na obrázku 4-26.</span><span class="sxs-lookup"><span data-stu-id="2dc23-208">You can find the existing images in your local repository (your development machine) by using the `docker images` command, as illustrated in Figure 4-26.</span></span>

![Výstup z konzoly z příkazu Docker images zobrazující existující image](media/docker-apps-inner-loop-workflow/view-existing-images-with-docker-images.png)

<span data-ttu-id="2dc23-210">**Obrázek 4-26**.</span><span class="sxs-lookup"><span data-stu-id="2dc23-210">**Figure 4-26**.</span></span> <span data-ttu-id="2dc23-211">Zobrazení existujících imagí pomocí imagí Docker</span><span class="sxs-lookup"><span data-stu-id="2dc23-211">Viewing existing images using docker images</span></span>

### <a name="step-4-define-your-services-in-docker-composeyml-when-building-a-composed-docker-app-with-multiple-services"></a><span data-ttu-id="2dc23-212">Krok 4: definování služeb v Docker-Compose. yml při sestavování složené aplikace Docker s více službami</span><span class="sxs-lookup"><span data-stu-id="2dc23-212">Step 4: Define your services in docker-compose.yml when building a composed Docker app with multiple services</span></span>

<span data-ttu-id="2dc23-213">Pomocí tohoto `docker-compose.yml` souboru můžete definovat sadu souvisejících služeb, které mají být nasazeny jako složená aplikace, a příkazy nasazení popsané v části Další krok.</span><span class="sxs-lookup"><span data-stu-id="2dc23-213">With the `docker-compose.yml` file, you can define a set of related services to be deployed as a composed application with the deployment commands explained in the next step section.</span></span>

<span data-ttu-id="2dc23-214">Vytvořte tento soubor ve složce Main nebo root Solution. měl by mít podobný obsah, jako je zobrazený v tomto `docker-compose.yml` souboru:</span><span class="sxs-lookup"><span data-stu-id="2dc23-214">Create that file in your main or root solution folder; it should have content similar to that shown in this `docker-compose.yml` file:</span></span>

```yml
version: "3.4"

services:
  webapi:
    image: webapi
    build:
      context: .
      dockerfile: src/WebApi/Dockerfile
    ports:
      - 51080:80
    depends_on:
      - redis
    environment:
      - ASPNETCORE_ENVIRONMENT=Development
      - ASPNETCORE_URLS=http://+:80

  webapp:
    image: webapp
    build:
      context: .
      dockerfile: src/WebApp/Dockerfile
    ports:
      - 50080:80
    environment:
      - ASPNETCORE_ENVIRONMENT=Development
      - ASPNETCORE_URLS=http://+:80
      - WebApiBaseAddress=http://webapi

  redis:
    image: redis
```

<span data-ttu-id="2dc23-215">V tomto konkrétním případě tento soubor definuje tři služby: službu webového rozhraní API (vlastní služba), webovou aplikaci a službu Redis (oblíbená služba mezipaměti).</span><span class="sxs-lookup"><span data-stu-id="2dc23-215">In this particular case, this file defines three services: the web API service (your custom service), a web application, and the Redis service (a popular cache service).</span></span> <span data-ttu-id="2dc23-216">Každá služba bude nasazena jako kontejner, takže pro každou z nich potřebujete použít konkrétní image Docker.</span><span class="sxs-lookup"><span data-stu-id="2dc23-216">Each service will be deployed as a container, so you need to use a concrete Docker image for each.</span></span> <span data-ttu-id="2dc23-217">Pro tuto konkrétní aplikaci:</span><span class="sxs-lookup"><span data-stu-id="2dc23-217">For this particular application:</span></span>

- <span data-ttu-id="2dc23-218">Služba webového rozhraní API je sestavena z souboru Dockerfile v `src/WebApi/Dockerfile` adresáři.</span><span class="sxs-lookup"><span data-stu-id="2dc23-218">The web API service is built from the DockerFile in the `src/WebApi/Dockerfile` directory.</span></span>

- <span data-ttu-id="2dc23-219">Port hostitele 51080 se přepošle na vystavený port 80 na `webapi` kontejneru.</span><span class="sxs-lookup"><span data-stu-id="2dc23-219">The host port 51080 is forwarded to the exposed port 80 on the `webapi` container.</span></span>

- <span data-ttu-id="2dc23-220">Služba webového rozhraní API závisí na službě Redis.</span><span class="sxs-lookup"><span data-stu-id="2dc23-220">The web API service depends on the Redis service</span></span>

- <span data-ttu-id="2dc23-221">Webová aplikace přistupuje ke službě webového rozhraní API pomocí interní adresy: `http://webapi` .</span><span class="sxs-lookup"><span data-stu-id="2dc23-221">The web application accesses the web API service using the internal address: `http://webapi`.</span></span>

- <span data-ttu-id="2dc23-222">Služba Redis používá [nejnovější veřejnou image Redis](https://hub.docker.com/_/redis/) získanou z registru Docker Hub.</span><span class="sxs-lookup"><span data-stu-id="2dc23-222">The Redis service uses the [latest public redis image](https://hub.docker.com/_/redis/) pulled from the Docker Hub registry.</span></span> <span data-ttu-id="2dc23-223">[Redis](https://redis.io/) je oblíbený systém mezipaměti pro aplikace na straně serveru.</span><span class="sxs-lookup"><span data-stu-id="2dc23-223">[Redis](https://redis.io/) is a popular cache system for server-side applications.</span></span>

### <a name="step-5-build-and-run-your-docker-app"></a><span data-ttu-id="2dc23-224">Krok 5: sestavení a spuštění aplikace Docker</span><span class="sxs-lookup"><span data-stu-id="2dc23-224">Step 5: Build and run your Docker app</span></span>

<span data-ttu-id="2dc23-225">Pokud má vaše aplikace jenom jeden kontejner, stačí ho spustit nasazením na hostitele Docker (virtuální počítač nebo fyzický server).</span><span class="sxs-lookup"><span data-stu-id="2dc23-225">If your app has only a single container, you just need to run it by deploying it to your Docker Host (VM or physical server).</span></span> <span data-ttu-id="2dc23-226">Pokud je ale vaše aplikace tvořená více službami, je nutné _ji vytvořit_také.</span><span class="sxs-lookup"><span data-stu-id="2dc23-226">However, if your app is made up of multiple services, you need to _compose it_, too.</span></span> <span data-ttu-id="2dc23-227">Pojďme se podívat na různé možnosti.</span><span class="sxs-lookup"><span data-stu-id="2dc23-227">Let's see the different options.</span></span>

<span data-ttu-id="2dc23-228">**_Možnost A: spuštění jednoho kontejneru nebo služby_**</span><span class="sxs-lookup"><span data-stu-id="2dc23-228">**_Option A: Run a single container or service_**</span></span>

<span data-ttu-id="2dc23-229">Bitovou kopii Docker můžete spustit pomocí příkazu Docker Run, jak je znázorněno zde:</span><span class="sxs-lookup"><span data-stu-id="2dc23-229">You can run the Docker image by using the docker run command, as shown here:</span></span>

```console
docker run -t -d -p 50080:80 explore-docker-vscode/webapp:latest
```

<span data-ttu-id="2dc23-230">U tohoto konkrétního nasazení budeme přesměrování požadavků odeslaných na port 50080 na hostiteli do interního portu 80.</span><span class="sxs-lookup"><span data-stu-id="2dc23-230">For this particular deployment, we'll be redirecting requests sent to port 50080 on the host to the internal port 80.</span></span>

<span data-ttu-id="2dc23-231">**_Možnost B: vytvoření a spuštění aplikace s více kontejnery_**</span><span class="sxs-lookup"><span data-stu-id="2dc23-231">**_Option B: Compose and run a multiple-container application_**</span></span>

<span data-ttu-id="2dc23-232">Ve většině podnikových scénářů se aplikace Docker skládá z několika služeb.</span><span class="sxs-lookup"><span data-stu-id="2dc23-232">In most enterprise scenarios, a Docker application will be composed of multiple services.</span></span> <span data-ttu-id="2dc23-233">V těchto případech můžete spustit `docker-compose up` příkaz (obrázek 4-27), který bude používat soubor Docker-Compose. yml, který jste vytvořili dříve.</span><span class="sxs-lookup"><span data-stu-id="2dc23-233">For these cases, you can run the `docker-compose up` command (Figure 4-27), which will use the docker-compose.yml file that you created previously.</span></span> <span data-ttu-id="2dc23-234">Spuštění tohoto příkazu vytvoří všechny vlastní image a nasadí složenou aplikaci se všemi souvisejícími kontejnery.</span><span class="sxs-lookup"><span data-stu-id="2dc23-234">Running this command builds all custom images and deploys the composed application with all of its related containers.</span></span>

![Výstup konzoly z příkazu Docker-sestavit.](media/docker-apps-inner-loop-workflow/results-docker-compose-up.png)

<span data-ttu-id="2dc23-236">**Obrázek 4-27**.</span><span class="sxs-lookup"><span data-stu-id="2dc23-236">**Figure 4-27**.</span></span> <span data-ttu-id="2dc23-237">Výsledky spuštění příkazu Docker-sestavit</span><span class="sxs-lookup"><span data-stu-id="2dc23-237">Results of running the "docker-compose up" command</span></span>

<span data-ttu-id="2dc23-238">Po spuštění `docker-compose up` aplikace nasadíte aplikaci a její související kontejnery do hostitele Docker, jak je znázorněno na obrázku 4-28, ve formě reprezentace virtuálního počítače.</span><span class="sxs-lookup"><span data-stu-id="2dc23-238">After you run `docker-compose up`, you deploy your application and its related container(s) into your Docker Host, as illustrated in Figure 4-28, in the VM representation.</span></span>

![Virtuální počítač spouštějící aplikace s více kontejnery.](./media/docker-apps-inner-loop-workflow/vm-with-docker-containers-deployed.png)

<span data-ttu-id="2dc23-240">**Obrázek 4-28**.</span><span class="sxs-lookup"><span data-stu-id="2dc23-240">**Figure 4-28**.</span></span> <span data-ttu-id="2dc23-241">Virtuální počítač s nasazenými kontejnery Docker</span><span class="sxs-lookup"><span data-stu-id="2dc23-241">VM with Docker containers deployed</span></span>

### <a name="step-6-test-your-docker-application-locally-in-your-local-cd-vm"></a><span data-ttu-id="2dc23-242">Krok 6: testování aplikace Docker (místně, na místním VIRTUÁLNÍm počítači CD)</span><span class="sxs-lookup"><span data-stu-id="2dc23-242">Step 6: Test your Docker application (locally, in your local CD VM)</span></span>

<span data-ttu-id="2dc23-243">Tento krok se bude lišit v závislosti na tom, co vaše aplikace dělá.</span><span class="sxs-lookup"><span data-stu-id="2dc23-243">This step will vary depending on what your app is doing.</span></span>

<span data-ttu-id="2dc23-244">V jednoduchém webovém rozhraní API .NET Core "Hello World" nasazené jako jediný kontejner nebo služba budete potřebovat přístup ke službě pouze zadáním portu TCP určeného v souboru Dockerfile.</span><span class="sxs-lookup"><span data-stu-id="2dc23-244">In a simple .NET Core Web API "Hello World" deployed as a single container or service, you'd just need to access the service by providing the TCP port specified in the DockerFile.</span></span>

<span data-ttu-id="2dc23-245">V hostiteli Docker otevřete prohlížeč a přejděte k této lokalitě. měla by se zobrazit vaše aplikace nebo služba, jak je znázorněno na obrázku 4-29.</span><span class="sxs-lookup"><span data-stu-id="2dc23-245">On the Docker host, open a browser and navigate to that site; you should see your app/service running, as demonstrated in Figure 4-29.</span></span>

![Zobrazení prohlížeče odpovědi z místního hostitele/rozhraní API/hodnot.](media/docker-apps-inner-loop-workflow/test-docker-app-locally-localhost.png)

<span data-ttu-id="2dc23-247">**Obrázek 4-29**.</span><span class="sxs-lookup"><span data-stu-id="2dc23-247">**Figure 4-29**.</span></span> <span data-ttu-id="2dc23-248">Místní testování aplikace Docker pomocí prohlížeče</span><span class="sxs-lookup"><span data-stu-id="2dc23-248">Testing your Docker application locally by using the browser</span></span>

<span data-ttu-id="2dc23-249">Všimněte si, že používá port 50080, ale interně se přesměruje na port 80, protože to je to, jak bylo nasazeno v `docker compose` , jak bylo vysvětleno výše.</span><span class="sxs-lookup"><span data-stu-id="2dc23-249">Note that it's using port 50080, but internally it's being redirected to port 80, because that's how it was deployed with `docker compose`, as explained earlier.</span></span>

<span data-ttu-id="2dc23-250">Tuto možnost můžete otestovat pomocí prohlížeče pomocí OBLÉho z terminálu, jak je znázorněno na obrázku 4-30.</span><span class="sxs-lookup"><span data-stu-id="2dc23-250">You can test this by using the browser using CURL from the terminal, as depicted in Figure 4-30.</span></span>

![Výsledek ze složené aplikace získaný zhttp://localhost:51080/WeatherForecast](media/docker-apps-inner-loop-workflow/test-docker-app-locally-curl.png)

<span data-ttu-id="2dc23-252">**Obrázek 4-30**.</span><span class="sxs-lookup"><span data-stu-id="2dc23-252">**Figure 4-30**.</span></span> <span data-ttu-id="2dc23-253">Místní testování aplikace Docker pomocí OBLÉ</span><span class="sxs-lookup"><span data-stu-id="2dc23-253">Testing a Docker application locally by using CURL</span></span>

<span data-ttu-id="2dc23-254">**Ladění kontejneru spuštěného v Docker**</span><span class="sxs-lookup"><span data-stu-id="2dc23-254">**Debugging a container running on Docker**</span></span>

<span data-ttu-id="2dc23-255">Pokud používáte Node.js a jiné platformy, jako jsou kontejnery .NET Core, Visual Studio Code podporuje ladění Docker.</span><span class="sxs-lookup"><span data-stu-id="2dc23-255">Visual Studio Code supports debugging Docker if you're using Node.js and other platforms like .NET Core containers.</span></span>

<span data-ttu-id="2dc23-256">Při použití sady Visual Studio pro Windows nebo Mac můžete v Docker ladit také kontejnery .NET Core nebo .NET Framework, jak je popsáno v následující části.</span><span class="sxs-lookup"><span data-stu-id="2dc23-256">You also can debug .NET Core or .NET Framework containers in Docker when using Visual Studio for Windows or Mac, as described in the next section.</span></span>

> [!TIP]
> <span data-ttu-id="2dc23-257">Další informace o ladění Node.js kontejnerů Docker naleznete v tématu <https://blog.docker.com/2016/07/live-debugging-docker/> a <https://docs.microsoft.com/archive/blogs/user_ed/visual-studio-code-new-features-13-big-debugging-updates-rich-object-hover-conditional-breakpoints-node-js-mono-more> .</span><span class="sxs-lookup"><span data-stu-id="2dc23-257">To learn more about debugging Node.js Docker containers, see <https://blog.docker.com/2016/07/live-debugging-docker/> and <https://docs.microsoft.com/archive/blogs/user_ed/visual-studio-code-new-features-13-big-debugging-updates-rich-object-hover-conditional-breakpoints-node-js-mono-more>.</span></span>

> [!div class="step-by-step"]
> <span data-ttu-id="2dc23-258">[Předchozí](docker-apps-development-environment.md) 
>  [Další](visual-studio-tools-for-docker.md)</span><span class="sxs-lookup"><span data-stu-id="2dc23-258">[Previous](docker-apps-development-environment.md)
[Next](visual-studio-tools-for-docker.md)</span></span>
