---
title: Pracovní postup vývoje vnitřní smyčky pro aplikace Dockeru
description: Přečtěte si pracovní postup "vnitřní smyčky" pro vývoj aplikací Dockeru.
ms.date: 02/15/2019
ms.openlocfilehash: ce573546f61b98c2f93e998203497fa949e9efe8
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2019
ms.locfileid: "65644863"
---
# <a name="inner-loop-development-workflow-for-docker-apps"></a><span data-ttu-id="68527-103">Pracovní postup vývoje vnitřní smyčky pro aplikace Dockeru</span><span class="sxs-lookup"><span data-stu-id="68527-103">Inner-loop development workflow for Docker apps</span></span>

<span data-ttu-id="68527-104">Před aktivací pracovního postupu vnější smyčky pokrývající celý DevOps cyklu, to všechno začíná každý vývojář počítače, psaní kódu aplikace pomocí jejich preferované jazyky a platformy a jejím místním otestováním (obrázek 4 – 21).</span><span class="sxs-lookup"><span data-stu-id="68527-104">Before triggering the outer-loop workflow spanning the entire DevOps cycle, it all begins on each developer's machine, coding the app itself, using their preferred languages or platforms, and testing it locally (Figure 4-21).</span></span> <span data-ttu-id="68527-105">Ale v každém případě budete mít o důležitý fakt v běžných bez ohledu na to, jaký jazyk, rozhraní nebo platformy zvolíte.</span><span class="sxs-lookup"><span data-stu-id="68527-105">But in every case, you'll have an important point in common, no matter what language, framework, or platforms you choose.</span></span> <span data-ttu-id="68527-106">V tomto konkrétním pracovním postupu vždy vývoji a testování kontejnery Dockeru, ale místně.</span><span class="sxs-lookup"><span data-stu-id="68527-106">In this specific workflow, you're always developing and testing Docker containers, but locally.</span></span>

![Krok 1 – kód/spuštění/ladění](./media/image18.png)

<span data-ttu-id="68527-108">**Obrázek 4 – 21**.</span><span class="sxs-lookup"><span data-stu-id="68527-108">**Figure 4-21**.</span></span> <span data-ttu-id="68527-109">Kontext vývoje vnitřní smyčky</span><span class="sxs-lookup"><span data-stu-id="68527-109">Inner-loop development context</span></span>

<span data-ttu-id="68527-110">Kontejner nebo instance image Dockeru, bude obsahovat tyto komponenty:</span><span class="sxs-lookup"><span data-stu-id="68527-110">The container or instance of a Docker image will contain these components:</span></span>

- <span data-ttu-id="68527-111">Výběru operačního systému (například distribuci Linuxu nebo Windows)</span><span class="sxs-lookup"><span data-stu-id="68527-111">An operating system selection (for example, a Linux distribution or Windows)</span></span>

- <span data-ttu-id="68527-112">Soubory přidané vývojář (třeba binární soubory aplikace)</span><span class="sxs-lookup"><span data-stu-id="68527-112">Files added by the developer (for example, app binaries)</span></span>

- <span data-ttu-id="68527-113">Konfigurace (například nastavení prostředí a závislosti)</span><span class="sxs-lookup"><span data-stu-id="68527-113">Configuration (for example, environment settings and dependencies)</span></span>

- <span data-ttu-id="68527-114">Pokyny pro jaké procesy spuštění pomocí Dockeru</span><span class="sxs-lookup"><span data-stu-id="68527-114">Instructions for what processes to run by Docker</span></span>

<span data-ttu-id="68527-115">Můžete nastavit pracovní postup vývoje vnitřní smyčky, s využitím Dockeru jako proces (popsané v další části).</span><span class="sxs-lookup"><span data-stu-id="68527-115">You can set up the inner-loop development workflow that utilizes Docker as the process (described in the next section).</span></span> <span data-ttu-id="68527-116">Vezměte v úvahu, že počáteční kroky k nastavení prostředí nejsou zahrnuty, protože je potřeba jenom jednou.</span><span class="sxs-lookup"><span data-stu-id="68527-116">Consider that the initial steps to set up the environment are not included, because you only need to do it once.</span></span>

## <a name="building-a-single-app-within-a-docker-container-using-visual-studio-code-and-docker-cli"></a><span data-ttu-id="68527-117">Vytvoření jednoduché aplikace v kontejneru Dockeru pomocí Visual Studio Code a rozhraní příkazového řádku Dockeru</span><span class="sxs-lookup"><span data-stu-id="68527-117">Building a single app within a Docker container using Visual Studio Code and Docker CLI</span></span>

<span data-ttu-id="68527-118">Aplikace se skládá z vlastní služby a další knihovny (závislosti).</span><span class="sxs-lookup"><span data-stu-id="68527-118">Apps are made up from your own services plus additional libraries (dependencies).</span></span>

<span data-ttu-id="68527-119">Obrázek 4 – 22 uvedeny základní kroky, které je obvykle potřeba provádět při vytváření aplikace Dockeru, za nímž následuje podrobný popis jednotlivých kroků.</span><span class="sxs-lookup"><span data-stu-id="68527-119">Figure 4-22 shows the basic steps that you usually need to carry out when building a Docker app, followed by detailed descriptions of each step.</span></span>

![Přehled pracovního postupu: Krok 1 – kód, krok 2 – zapisovat soubory Dockerfile, krok 3 – vytváření imagí, které jsou definovány soubory Dockerfile, krok 4 – definovat souborem docker-compose krok 5: spuštění kontejnerů služby nebo aplikace skládá, krok 6 – Test aplikace, krok 7 – doručit na začátku vnější smyčky (kanálů CI/CD) ani pokračovat de veloping.](./media/image19.png)

<span data-ttu-id="68527-121">**Obrázek 4 – 22**.</span><span class="sxs-lookup"><span data-stu-id="68527-121">**Figure 4-22**.</span></span> <span data-ttu-id="68527-122">Pracovní postup vysoké úrovně pro životní cyklus pro Docker kontejnerizovaných aplikací pomocí rozhraní příkazového řádku Dockeru</span><span class="sxs-lookup"><span data-stu-id="68527-122">High-level workflow for the life cycle for Docker containerized applications using Docker CLI</span></span>

### <a name="step-1-start-coding-in-visual-studio-code-and-create-your-initial-appservice-baseline"></a><span data-ttu-id="68527-123">Krok 1: Pusťte se do programování ve Visual Studio Code a vytvořit směrný plán počáteční aplikace nebo služby</span><span class="sxs-lookup"><span data-stu-id="68527-123">Step 1: Start coding in Visual Studio Code and create your initial app/service baseline</span></span>

<span data-ttu-id="68527-124">Způsob, jak vyvíjet aplikace je podobný způsobu práce bez Dockeru.</span><span class="sxs-lookup"><span data-stu-id="68527-124">The way you develop your application is similar to the way you do it without Docker.</span></span> <span data-ttu-id="68527-125">Rozdíl je, že při vývoji, jste nasazení a testování vaší aplikace nebo služby v rámci kontejnery Dockeru, které jsou umístěny v místním prostředí (např. virtuální počítač s Linuxem nebo Windows).</span><span class="sxs-lookup"><span data-stu-id="68527-125">The difference is that while developing, you're deploying and testing your application or services running within Docker containers placed in your local environment (like a Linux VM or Windows).</span></span>

<span data-ttu-id="68527-126">**Nastavení místního prostředí**</span><span class="sxs-lookup"><span data-stu-id="68527-126">**Setting up your local environment**</span></span>

<span data-ttu-id="68527-127">S nejnovější verzí Dockeru pro Mac a Windows je jednodušší než dříve k vývoji aplikací Dockeru a instalační program je jednoduché.</span><span class="sxs-lookup"><span data-stu-id="68527-127">With the latest versions of Docker for Mac and Windows, it's easier than ever to develop Docker applications, and the setup is straightforward.</span></span>

> [! INFORMACE O]
>
> <span data-ttu-id="68527-129">Pokyny k nastavení Dockeru pro Windows, přejděte na <https://docs.docker.com/docker-for-windows/>.</span><span class="sxs-lookup"><span data-stu-id="68527-129">For instructions on setting up Docker for Windows, go to <https://docs.docker.com/docker-for-windows/>.</span></span>
>
><span data-ttu-id="68527-130">Pokyny k nastavení Dockeru pro Mac, přejděte na <https://docs.docker.com/docker-for-mac/>.</span><span class="sxs-lookup"><span data-stu-id="68527-130">For instructions on setting up Docker for Mac, go to <https://docs.docker.com/docker-for-mac/>.</span></span>

<span data-ttu-id="68527-131">Kromě toho budete potřebovat editor kódu tak, aby ve skutečnosti můžete vyvíjet aplikace pomocí rozhraní příkazového řádku Dockeru.</span><span class="sxs-lookup"><span data-stu-id="68527-131">In addition, you'll need a code editor so that you can actually develop your application while using Docker CLI.</span></span>

<span data-ttu-id="68527-132">Společnost Microsoft poskytuje Visual Studio Code, který je ve zjednodušeném editoru kódu, který se podporuje na Macu, Windows a Linux a nabízí technologii IntelliSense s [podporu mnoha jazyků](https://code.visualstudio.com/docs/languages/overview) (jazyk JavaScript, .NET, Go, Java, Ruby, Python a většinu Moderní jazyky), [ladění](https://code.visualstudio.com/Docs/editor/debugging), [integrace s úložištěm Git](https://code.visualstudio.com/Docs/editor/versioncontrol) a [rozšíření podpory](https://code.visualstudio.com/docs/extensions/overview).</span><span class="sxs-lookup"><span data-stu-id="68527-132">Microsoft provides Visual Studio Code, which is a lightweight code editor that's supported on Mac, Windows, and Linux, and provides IntelliSense with [support for many languages](https://code.visualstudio.com/docs/languages/overview) (JavaScript, .NET, Go, Java, Ruby, Python, and most modern languages), [debugging](https://code.visualstudio.com/Docs/editor/debugging), [integration with Git](https://code.visualstudio.com/Docs/editor/versioncontrol) and [extensions support](https://code.visualstudio.com/docs/extensions/overview).</span></span> <span data-ttu-id="68527-133">Tento editor se skvěle hodí pro vývojáře Mac a Linux.</span><span class="sxs-lookup"><span data-stu-id="68527-133">This editor is a great fit for Mac and Linux developers.</span></span> <span data-ttu-id="68527-134">Ve Windows také můžete použít celou aplikaci Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="68527-134">In Windows, you also can use the full Visual Studio application.</span></span>

> [! INFORMACE O]
>
> <span data-ttu-id="68527-136">Pokyny k instalaci Visual Studio Code pro Windows, Mac nebo Linux, přejděte na <https://code.visualstudio.com/docs/setup/setup-overview/>.</span><span class="sxs-lookup"><span data-stu-id="68527-136">For instructions on installing Visual Studio Code for Windows, Mac, or Linux, go to <https://code.visualstudio.com/docs/setup/setup-overview/>.</span></span>
>
> <span data-ttu-id="68527-137">Pokyny k nastavení Dockeru pro Mac, přejděte na <https://docs.docker.com/docker-for-mac/>.</span><span class="sxs-lookup"><span data-stu-id="68527-137">For instructions on setting up Docker for Mac, go to <https://docs.docker.com/docker-for-mac/>.</span></span>

<span data-ttu-id="68527-138">Můžete pracovat pomocí rozhraní příkazového řádku Dockeru a napište svůj kód pomocí editoru kódu, ale pomocí Visual Studio Code se rozšíření Docker umožňuje snadno autorovi `Dockerfile` a `docker-compose.yml` soubory ve vašem pracovním prostoru.</span><span class="sxs-lookup"><span data-stu-id="68527-138">You can work with Docker CLI and write your code using any code editor, but using Visual Studio Code with the Docker extension makes it easy to author `Dockerfile` and `docker-compose.yml` files in your workspace.</span></span> <span data-ttu-id="68527-139">Na Visual Studio IDE kód ke spuštění příkazů Docker pomocí rozhraní příkazového řádku Dockeru pod můžete spouštět úlohy a skripty.</span><span class="sxs-lookup"><span data-stu-id="68527-139">You can also run tasks and scripts from the Visual Studio Code IDE to execute Docker commands using the Docker CLI underneath.</span></span>

<span data-ttu-id="68527-140">Rozšíření Docker pro VS Code poskytuje následující funkce:</span><span class="sxs-lookup"><span data-stu-id="68527-140">The Docker extension for VS Code provides the following features:</span></span>

- <span data-ttu-id="68527-141">Automatické `Dockerfile` a `docker-compose.yml` generování souborů</span><span class="sxs-lookup"><span data-stu-id="68527-141">Automatic `Dockerfile` and `docker-compose.yml` file generation</span></span>

- <span data-ttu-id="68527-142">Syntaxe zvýrazňování a při najetí myší tipy pro `docker-compose.yml` a `Dockerfile` soubory</span><span class="sxs-lookup"><span data-stu-id="68527-142">Syntax highlighting and hover tips for `docker-compose.yml` and `Dockerfile` files</span></span>

- <span data-ttu-id="68527-143">Technologie IntelliSense (dokončování) pro `Dockerfile` a `docker-compose.yml` soubory</span><span class="sxs-lookup"><span data-stu-id="68527-143">IntelliSense (completions) for `Dockerfile` and `docker-compose.yml` files</span></span>

- <span data-ttu-id="68527-144">Linting (chyby a upozornění) pro `Dockerfile` soubory</span><span class="sxs-lookup"><span data-stu-id="68527-144">Linting (errors and warnings) for `Dockerfile` files</span></span>

- <span data-ttu-id="68527-145">Příkaz integrace palety (F1) pro nejčastěji používané příkazy Dockeru</span><span class="sxs-lookup"><span data-stu-id="68527-145">Command Palette (F1) integration for the most common Docker commands</span></span>

- <span data-ttu-id="68527-146">Integrace Průzkumníka správy Imagí a kontejnery</span><span class="sxs-lookup"><span data-stu-id="68527-146">Explorer integration for managing Images and Containers</span></span>

- <span data-ttu-id="68527-147">Nasadit Image v Dockerhubu a Azure Container registry do služby Azure App Service</span><span class="sxs-lookup"><span data-stu-id="68527-147">Deploy images from DockerHub and Azure Container Registries to Azure App Service</span></span>

<span data-ttu-id="68527-148">Chcete-li nainstalovat rozšíření Docker, stiskněte klávesy Ctrl + Shift + P, zadejte `ext install`, a potom spusťte instalaci rozšíření příkazu zobrazíte seznam rozšíření Marketplace.</span><span class="sxs-lookup"><span data-stu-id="68527-148">To install the Docker extension, press Ctrl+Shift+P, type `ext install`, and then run the Install Extension command to bring up the Marketplace extension list.</span></span> <span data-ttu-id="68527-149">Dále zadejte **docker** k filtrování výsledků a pak vyberte rozšíření podpory Dockeru, jak je znázorněno v obrázek 4 – 23.</span><span class="sxs-lookup"><span data-stu-id="68527-149">Next, type **docker** to filter the results, and then select the Docker Support extension, as depicted in Figure 4-23.</span></span>

![Přehled rozšíření Dockeru pro VS Code.](./media/image20.png)

<span data-ttu-id="68527-151">**Obrázek 4 – 23**.</span><span class="sxs-lookup"><span data-stu-id="68527-151">**Figure 4-23**.</span></span> <span data-ttu-id="68527-152">Instaluje se rozšíření Dockeru v aplikaci Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="68527-152">Installing the Docker Extension in Visual Studio Code</span></span>

### <a name="step-2-create-a-dockerfile-related-to-an-existing-image-plain-os-or-dev-environments-like-net-core-nodejs-and-ruby"></a><span data-ttu-id="68527-153">Krok 2: Vytvoření souboru DockerFile související s existující image (plain operačního systému nebo vývoj prostředí, jako je .NET Core, Node.js a Ruby)</span><span class="sxs-lookup"><span data-stu-id="68527-153">Step 2: Create a DockerFile related to an existing image (plain OS or dev environments like .NET Core, Node.js, and Ruby)</span></span>

<span data-ttu-id="68527-154">Budete potřebovat `DockerFile` na vlastní image má být sestaven a na kontejneru pro nasazení.</span><span class="sxs-lookup"><span data-stu-id="68527-154">You'll need a `DockerFile` per custom image to be built and per container to be deployed.</span></span> <span data-ttu-id="68527-155">Pokud vaše aplikace se skládá z jedné vlastní službě, budete potřebovat jeden `DockerFile`.</span><span class="sxs-lookup"><span data-stu-id="68527-155">If your app is made up of a single custom service, you'll need a single `DockerFile`.</span></span> <span data-ttu-id="68527-156">Ale pokud se vaše aplikace skládá z více služeb (stejně jako v architektuře mikroslužeb), budete potřebovat `Dockerfile` každou službu.</span><span class="sxs-lookup"><span data-stu-id="68527-156">But if your app is composed of multiple services (as in a microservices architecture), you'll need one `Dockerfile` per service.</span></span>

<span data-ttu-id="68527-157">`DockerFile` Je obvykle umístěn v kořenové složce aplikace nebo služby a obsahuje požadované příkazy tak, které Docker ví, jak nastavit a spustit aplikaci nebo službu.</span><span class="sxs-lookup"><span data-stu-id="68527-157">The `DockerFile` is commonly placed in the root folder of your app or service and contains the required commands so that Docker knows how to set up and run that app or service.</span></span> <span data-ttu-id="68527-158">Můžete vytvořit vaše `DockerFile` a přidejte ho do svého projektu spolu s kódu (node.js, .NET Core, atd.), nebo pokud jste nové prostředí, podívejte se na následující vrcholu.</span><span class="sxs-lookup"><span data-stu-id="68527-158">You can create your `DockerFile` and add it to your project along with your code (node.js, .NET Core, etc.), or, if you're new to the environment, take a look at the following Tip.</span></span>

> [!TIP]
>
> <span data-ttu-id="68527-159">Můžete použít rozšíření Docker a provede vás při použití `Dockerfile` a `docker-compose.yml` soubory související s kontejnery Dockeru.</span><span class="sxs-lookup"><span data-stu-id="68527-159">You can use the Docker extension to guide you when using the `Dockerfile` and `docker-compose.yml` files related to your Docker containers.</span></span> <span data-ttu-id="68527-160">Nakonec pravděpodobně napíšete tyto typy souborů bez tento nástroj, ale je dobrým výchozím bodem, který urychlí vaše křivka se použití rozšíření Docker.</span><span class="sxs-lookup"><span data-stu-id="68527-160">Eventually, you'll probably write these kinds of files without this tool, but using the Docker extension is a good starting point that will accelerate your learning curve.</span></span>

<span data-ttu-id="68527-161">Obrázek 4 – 24 můžete zobrazit, jak docker-compose se přidá soubor s použitím rozšíření Dockeru pro VS Code.</span><span class="sxs-lookup"><span data-stu-id="68527-161">In Figure 4-24, you can see how a docker-compose file is added by using the Docker Extension for VS Code.</span></span>

![Zobrazení konzoly rozšíření Dockeru pro VS Code.](./media/image24.png)

<span data-ttu-id="68527-163">**Obrázek 4 – 24**.</span><span class="sxs-lookup"><span data-stu-id="68527-163">**Figure 4-24**.</span></span> <span data-ttu-id="68527-164">Přidat pomocí souborů dockeru **Docker přidat soubory do příkazu pracovního prostoru**</span><span class="sxs-lookup"><span data-stu-id="68527-164">Docker files added using the **Add Docker files to Workspace command**</span></span>

<span data-ttu-id="68527-165">Když přidáte soubor DockerFile, zadejte co základní image Dockeru, který budete používat (například `FROM mcr.microsoft.com/dotnet/core/aspnet`).</span><span class="sxs-lookup"><span data-stu-id="68527-165">When you add a DockerFile, you specify what base Docker image you’ll be using (like using `FROM mcr.microsoft.com/dotnet/core/aspnet`).</span></span> <span data-ttu-id="68527-166">Obvykle vytvoříte vlastní bitovou kopii nad základní image, kterou můžete získat z jakékoli oficiální úložiště [registru Docker Hub](https://hub.docker.com/) (stejně jako [bitovou kopii pro .NET Core](https://hub.docker.com/_/microsoft-dotnet-core/) nebo [pro Node.js](https://hub.docker.com/_/node/)).</span><span class="sxs-lookup"><span data-stu-id="68527-166">You'll usually build your custom image on top of a base image that you get from any official repository at the [Docker Hub registry](https://hub.docker.com/) (like an [image for .NET Core](https://hub.docker.com/_/microsoft-dotnet-core/) or the one [for Node.js](https://hub.docker.com/_/node/)).</span></span>

<span data-ttu-id="68527-167">***Použít existující oficiální image Dockeru***</span><span class="sxs-lookup"><span data-stu-id="68527-167">***Use an existing official Docker image***</span></span>

<span data-ttu-id="68527-168">Použití zásobníku jazyka oficiální úložiště s číslem verze zajistí, že stejné funkce jazyka jsou k dispozici na všech počítačích (včetně vývoje, testování a produkce).</span><span class="sxs-lookup"><span data-stu-id="68527-168">Using an official repository of a language stack with a version number ensures that the same language features are available on all machines (including development, testing, and production).</span></span>

<span data-ttu-id="68527-169">Následuje ukázkový soubor DockerFile pro .NET Core kontejneru:</span><span class="sxs-lookup"><span data-stu-id="68527-169">The following is a sample DockerFile for a .NET Core container:</span></span>

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

<span data-ttu-id="68527-170">V tomto případě bitovou kopii podle verze 2.2 oficiální image Dockeru ASP.NET Core (více arch pro systémy Linux a Windows), podle řádku `FROM mcr.microsoft.com/dotnet/core/aspnet:2.2`.</span><span class="sxs-lookup"><span data-stu-id="68527-170">In this case, the image is based on version 2.2 of the official ASP.NET Core Docker image (multi-arch for Linux and Windows), as per the line `FROM mcr.microsoft.com/dotnet/core/aspnet:2.2`.</span></span> <span data-ttu-id="68527-171">(Další informace o tomto tématu najdete v článku [Image Dockeru ASP.NET Core](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) stránky a [Image Dockeru .NET Core](https://hub.docker.com/_/microsoft-dotnet-core/) stránky).</span><span class="sxs-lookup"><span data-stu-id="68527-171">(For more information about this topic, see the [ASP.NET Core Docker Image](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) page and the [.NET Core Docker Image](https://hub.docker.com/_/microsoft-dotnet-core/) page).</span></span>

<span data-ttu-id="68527-172">V souboru DockerFile se dá taky nastavit Docker nenaslouchá na portu TCP, který budete používat v době běhu (například port 80).</span><span class="sxs-lookup"><span data-stu-id="68527-172">In the DockerFile, you can also instruct Docker to listen to the TCP port that you'll use at runtime (such as port 80).</span></span>

<span data-ttu-id="68527-173">Můžete zadat další nastavení konfigurace v souboru Dockerfile, v závislosti na jazyk a rozhraní, které používáte.</span><span class="sxs-lookup"><span data-stu-id="68527-173">You can specify additional configuration settings in the Dockerfile, depending on the language and framework you're using.</span></span> <span data-ttu-id="68527-174">Například `ENTRYPOINT` čára s `["dotnet", "MySingleContainerWebApp.dll"]` říká Dockeru spustit aplikaci .NET Core.</span><span class="sxs-lookup"><span data-stu-id="68527-174">For instance, the `ENTRYPOINT` line with `["dotnet", "MySingleContainerWebApp.dll"]` tells Docker to run a .NET Core application.</span></span> <span data-ttu-id="68527-175">Pokud používáte sadu SDK a rozhraní příkazového řádku .NET Core (`dotnet CLI`) k sestavení a spuštění aplikace .NET, toto nastavení bude odlišná.</span><span class="sxs-lookup"><span data-stu-id="68527-175">If you're using the SDK and the .NET Core CLI (`dotnet CLI`) to build and run the .NET application, this setting would be different.</span></span> <span data-ttu-id="68527-176">Klíčovým bodem tedy je, že vstupní bod řádku a další nastavení závisí na jazyk a platformu, kterou zvolíte pro vaši aplikaci.</span><span class="sxs-lookup"><span data-stu-id="68527-176">The key point here is that the ENTRYPOINT line and other settings depend on the language and platform you choose for your application.</span></span>

> [! INFORMACE O]
>
> <span data-ttu-id="68527-178">Další informace o vytváření imagí Dockeru pro aplikace .NET Core, přejděte na <https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images>.</span><span class="sxs-lookup"><span data-stu-id="68527-178">For more information about building Docker images for .NET Core applications, go to <https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images>.</span></span>
>
> <span data-ttu-id="68527-179">Další informace o vytváření vlastních imagí, přejděte na <https://docs.docker.com/engine/tutorials/dockerimages/>.</span><span class="sxs-lookup"><span data-stu-id="68527-179">To learn more about building your own images, go to <https://docs.docker.com/engine/tutorials/dockerimages/>.</span></span>

<span data-ttu-id="68527-180">**Použití úložiště image více architektury**</span><span class="sxs-lookup"><span data-stu-id="68527-180">**Use multi-arch image repositories**</span></span>

<span data-ttu-id="68527-181">Název jedné image do úložiště může obsahovat variant, platformy, jako jsou image Linuxu a Windows image.</span><span class="sxs-lookup"><span data-stu-id="68527-181">A single image name in a repo can contain platform variants, such as a Linux image and a Windows image.</span></span> <span data-ttu-id="68527-182">Tato funkce umožňuje dodavatelé, jako je Microsoft (creators základní image) k vytvoření jednoho úložiště pro víc platforem (to znamená, Linux a Windows).</span><span class="sxs-lookup"><span data-stu-id="68527-182">This feature allows vendors like Microsoft (base image creators) to create a single repo to cover multiple platforms (that is, Linux and Windows).</span></span> <span data-ttu-id="68527-183">Například [dotnet/core/aspnet](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) úložiště k dispozici v registru Docker Hub poskytuje podporu pro systémy Linux a Windows Nano Server pomocí stejného názvu image.</span><span class="sxs-lookup"><span data-stu-id="68527-183">For example, the [dotnet/core/aspnet](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) repository available in the Docker Hub registry provides support for Linux and Windows Nano Server by using the same image name.</span></span>

<span data-ttu-id="68527-184">Souhrnné informace [dotnet/core/aspnet](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) image z hostitele Windows si vyžádá Windows variant, zatímco přebírání stejný název image z hostitele platformy Linux si vyžádá varianty Linuxu.</span><span class="sxs-lookup"><span data-stu-id="68527-184">Pulling the [dotnet/core/aspnet](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) image from a Windows host pulls the Windows variant, whereas pulling the same image name from a Linux host pulls the Linux variant.</span></span>

<span data-ttu-id="68527-185">***Vytvoření zcela nové základní image***</span><span class="sxs-lookup"><span data-stu-id="68527-185">***Create your base image from scratch***</span></span>

<span data-ttu-id="68527-186">Můžete vytvořit vlastní základní image Dockeru od začátku, jak je popsáno v tomto [článku](https://docs.docker.com/engine/userguide/eng-image/baseimages/) od Dockeru.</span><span class="sxs-lookup"><span data-stu-id="68527-186">You can create your own Docker base image from scratch as explained in this [article](https://docs.docker.com/engine/userguide/eng-image/baseimages/) from Docker.</span></span> <span data-ttu-id="68527-187">Tento scénář není pravděpodobně pro vás nejvýhodnější Pokud začínáte s Dockerem, ale pokud chcete nastavit konkrétní bity základní image, můžete to provést.</span><span class="sxs-lookup"><span data-stu-id="68527-187">This scenario is probably not the best for you if you're just starting with Docker, but if you want to set the specific bits of your own base image, you can do it.</span></span>

### <a name="step-3-create-your-custom-docker-images-embedding-your-service-in-it"></a><span data-ttu-id="68527-188">Krok 3: Vytvoření vlastní Image Dockeru vložení služby</span><span class="sxs-lookup"><span data-stu-id="68527-188">Step 3: Create your custom Docker images embedding your service in it</span></span>

<span data-ttu-id="68527-189">U každé aplikace se skládá z vlastní služby budete muset vytvořit související image.</span><span class="sxs-lookup"><span data-stu-id="68527-189">For each custom service that comprises your app, you'll need to create a related image.</span></span> <span data-ttu-id="68527-190">Pokud vaše aplikace skládá z jedné služby nebo webové aplikace, budete potřebovat jenom jedné image.</span><span class="sxs-lookup"><span data-stu-id="68527-190">If your app is made up of a single service or web app, you'll need just a single image.</span></span>

> [!NOTE]
>
> <span data-ttu-id="68527-191">Když se vezme v úvahu "workflow pro DevOps vnější smyčky", obrázky, bude vytvořen pomocí automatizovaného procesu sestavení pokaždé, když vložíte změny zdrojového kódu do úložiště Git (Nepřetržitá integrace), takže Image se vytvoří v globálním prostředí z vaší zdrojový kód.</span><span class="sxs-lookup"><span data-stu-id="68527-191">When taking into account the "outer-loop DevOps workflow", the images will be created by an automated build process whenever you push your source code to a Git repository (Continuous Integration), so the images will be created in that global environment from your source code.</span></span>
>
> <span data-ttu-id="68527-192">Ale předtím, než jsme zvažte, že přejdete na tuto trasu vnější smyčky, potřebujeme zajistit, že aplikace Dockeru ve skutečnosti funguje správně tak, aby jejich není push kód, který nemusí správně fungovat do systému správy zdrojového kódu (Git atd.).</span><span class="sxs-lookup"><span data-stu-id="68527-192">But before we consider going to that outer-loop route, we need to ensure that the Docker application is actually working properly so that they don't push code that might not work properly to the source control system (Git, etc.).</span></span>
>
> <span data-ttu-id="68527-193">Každý vývojář proto nejprve musí udělat celý proces vnitřní smyčky, místně ji otestovat a pokračovat ve vývoji, dokud chtějí push kompletní funkce nebo změňte na systém správy zdrojového kódu.</span><span class="sxs-lookup"><span data-stu-id="68527-193">Therefore, each developer first needs to do the entire inner-loop process to test locally and continue developing until they want to push a complete feature or change to the source control system.</span></span>

<span data-ttu-id="68527-194">Pro vytvoření image v místním prostředí a pomocí souboru DockerFile, můžete použít příkaz sestavení dockeru, jak je ukázáno v obrázek 4 – 25 (můžete také spustit `docker-compose up --build` pro aplikace, které sestává z několika kontejnerů nebo služeb Team Foundation).</span><span class="sxs-lookup"><span data-stu-id="68527-194">To create an image in your local environment and using the DockerFile, you can use the docker build command, as demonstrated in Figure 4-25 (you also can run `docker-compose up --build` for applications composed by several containers/services).</span></span>

![Výstup na konzole docker-compose sestavení, zobrazuje průběh stahování imagí.](./media/image25.png)

<span data-ttu-id="68527-196">**Obrázek 4 – 25**.</span><span class="sxs-lookup"><span data-stu-id="68527-196">**Figure 4-25**.</span></span> <span data-ttu-id="68527-197">Spouštění sestavení dockeru</span><span class="sxs-lookup"><span data-stu-id="68527-197">Running docker build</span></span>

<span data-ttu-id="68527-198">Volitelně můžete místo přímo spouštět `docker build` ze složky projektu, nejprve můžete vygenerovat nasaditelný složku s knihovnami .NET potřebuje používat spuštění `dotnet publish` příkaz a poté spusťte `docker build`.</span><span class="sxs-lookup"><span data-stu-id="68527-198">Optionally, instead of directly running `docker build` from the project folder, you first can generate a deployable folder with the .NET libraries needed by using the run `dotnet publish` command, and then run `docker build`.</span></span>

<span data-ttu-id="68527-199">Tento příklad vytvoří image Dockeru s názvem `cesardl/netcore-webapi-microservice-docker:first` (`:first` jsou klíčová slova, jako jsou konkrétní verzi).</span><span class="sxs-lookup"><span data-stu-id="68527-199">This example creates a Docker image with the name `cesardl/netcore-webapi-microservice-docker:first` (`:first` is a tag, like a specific version).</span></span> <span data-ttu-id="68527-200">Je-li provést tento krok pro každou vlastní image, které je potřeba vytvořit složené aplikace Dockeru s několika kontejnery.</span><span class="sxs-lookup"><span data-stu-id="68527-200">You can take this step for each custom image you need to create for your composed Docker application with several containers.</span></span>

<span data-ttu-id="68527-201">Najdete existujících bitových kopií ve vašem místním úložišti (vývojovém počítači) s využitím dockeru příkaz bitové kopie, jak je znázorněno v obrázek 4 – 26.</span><span class="sxs-lookup"><span data-stu-id="68527-201">You can find the existing images in your local repository (your development machine) by using the docker images command, as illustrated in Figure 4-26.</span></span>

![Výstup z příkazu imagí dockeru, zobrazení existujících imagí konzoly.](./media/image26.png)

<span data-ttu-id="68527-203">**Obrázek 4 – 26**.</span><span class="sxs-lookup"><span data-stu-id="68527-203">**Figure 4-26**.</span></span> <span data-ttu-id="68527-204">Zobrazení existujících obrázků s využitím Image dockeru</span><span class="sxs-lookup"><span data-stu-id="68527-204">Viewing existing images using docker images</span></span>

### <a name="step-4-define-your-services-in-docker-composeyml-when-building-a-composed-docker-app-with-multiple-services"></a><span data-ttu-id="68527-205">Krok 4: Definování vašich služeb v docker-compose.yml při vytváření složené aplikace Dockeru s více službami</span><span class="sxs-lookup"><span data-stu-id="68527-205">Step 4: Define your services in docker-compose.yml when building a composed Docker app with multiple services</span></span>

<span data-ttu-id="68527-206">S `docker-compose.yml` soubor, můžete definovat sadu souvisejících služeb umožňující nasadit ho jako aplikace skládá pomocí příkazů nasazení je vysvětleno v další části kroku.</span><span class="sxs-lookup"><span data-stu-id="68527-206">With the `docker-compose.yml` file, you can define a set of related services to be deployed as a composed application with the deployment commands explained in the next step section.</span></span>

<span data-ttu-id="68527-207">Vytvoření tohoto souboru ve vaší hlavní nebo kořenové složky řešení; měl by mít podobný zobrazená v tomto obsahu `docker-compose.yml` souboru:</span><span class="sxs-lookup"><span data-stu-id="68527-207">Create that file in your main or root solution folder; it should have content similar to that shown in this `docker-compose.yml` file:</span></span>

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

<span data-ttu-id="68527-208">V tomto konkrétním případě tento soubor definuje dvě služby: webové služby (vaše vlastní služba) a službu redis (Oblíbené mezipaměti služby).</span><span class="sxs-lookup"><span data-stu-id="68527-208">In this particular case, this file defines two services: the web service (your custom service) and the redis service (a popular cache service).</span></span> <span data-ttu-id="68527-209">Každá služba se nasadí jako kontejner, proto musíme pomocí konkrétní image Dockeru pro každý.</span><span class="sxs-lookup"><span data-stu-id="68527-209">Each service will be deployed as a container, so we need to use a concrete Docker image for each.</span></span> <span data-ttu-id="68527-210">Pro tento konkrétní webovou službu na obrázku potřebovat provést následující kroky:</span><span class="sxs-lookup"><span data-stu-id="68527-210">For this particular web service, the image will need to do the following:</span></span>

- <span data-ttu-id="68527-211">Sestavení z soubor DockerFile v aktuálním adresáři</span><span class="sxs-lookup"><span data-stu-id="68527-211">Build from the DockerFile in the current directory</span></span>

- <span data-ttu-id="68527-212">Dál vystavené port 80 v kontejneru na port 81 na hostitelském počítači</span><span class="sxs-lookup"><span data-stu-id="68527-212">Forward the exposed port 80 on the container to port 81 on the host machine</span></span>

- <span data-ttu-id="68527-213">Připojení adresáře projektu v hostiteli /code v rámci kontejneru, takže budete moct změnit kód bez nutnosti znovu sestavovat image</span><span class="sxs-lookup"><span data-stu-id="68527-213">Mount the project directory on the host to /code within the container, making it possible for you to modify the code without having to rebuild the image</span></span>

- <span data-ttu-id="68527-214">Odkaz webové služby ke službě redis</span><span class="sxs-lookup"><span data-stu-id="68527-214">Link the web service to the redis service</span></span>

<span data-ttu-id="68527-215">Použití služby redis [nejnovější veřejné redis image](https://hub.docker.com/_/redis/) získaných z registru Docker Hub.</span><span class="sxs-lookup"><span data-stu-id="68527-215">The redis service uses the [latest public redis image](https://hub.docker.com/_/redis/) pulled from the Docker Hub registry.</span></span> <span data-ttu-id="68527-216">[redis](https://redis.io/) je systém Oblíbené mezipaměti pro aplikace na straně serveru.</span><span class="sxs-lookup"><span data-stu-id="68527-216">[redis](https://redis.io/) is a popular cache system for server-side applications.</span></span>

### <a name="step-5-build-and-run-your-docker-app"></a><span data-ttu-id="68527-217">Krok 5: Sestavení a spuštění aplikace Dockeru</span><span class="sxs-lookup"><span data-stu-id="68527-217">Step 5: Build and run your Docker app</span></span>

<span data-ttu-id="68527-218">Pokud vaše aplikace má pouze jeden kontejner, stačí ji spustit nasazení na hostitele Docker (virtuální počítač nebo fyzický server).</span><span class="sxs-lookup"><span data-stu-id="68527-218">If your app has only a single container, you just need to run it by deploying it to your Docker Host (VM or physical server).</span></span> <span data-ttu-id="68527-219">Nicméně pokud vaše aplikace se skládá z několika služeb, budete muset *tvoří ji*také.</span><span class="sxs-lookup"><span data-stu-id="68527-219">However, if your app is made up of multiple services, you need to *compose it*, too.</span></span> <span data-ttu-id="68527-220">Podívejme se na různé možnosti.</span><span class="sxs-lookup"><span data-stu-id="68527-220">Let's see the different options.</span></span>

<span data-ttu-id="68527-221">***Možnost A: Spustit jedním kontejnerem nebo služby***</span><span class="sxs-lookup"><span data-stu-id="68527-221">***Option A: Run a single container or service***</span></span>

<span data-ttu-id="68527-222">Image Dockeru můžete spustit pomocí dockeru, spusťte příkaz, jak je znázorněno zde:</span><span class="sxs-lookup"><span data-stu-id="68527-222">You can run the Docker image by using the docker run command, as shown here:</span></span>

```console
docker run -t -d -p 80:5000 cesardl/netcore-webapi-microservice-docker:first
```

<span data-ttu-id="68527-223">Pro toto konkrétní nasazení jsme budete přesměruje požadavky odeslané na portu 80 na interní port 5000.</span><span class="sxs-lookup"><span data-stu-id="68527-223">For this particular deployment, we'll be redirecting requests sent to port 80 to the internal port 5000.</span></span> <span data-ttu-id="68527-224">Aplikace je teď naslouchá na externím portu 80 na úrovni hostitele.</span><span class="sxs-lookup"><span data-stu-id="68527-224">Now the application is listening on the external port 80 at the host level.</span></span>

<span data-ttu-id="68527-225">***Možnost B: Vytvářet a spouštět aplikace typu kontejner více***</span><span class="sxs-lookup"><span data-stu-id="68527-225">***Option B: Compose and run a multiple-container application***</span></span>

<span data-ttu-id="68527-226">Ve většině scénářů organizace aplikaci v Dockeru se skládá z více služeb.</span><span class="sxs-lookup"><span data-stu-id="68527-226">In most enterprise scenarios, a Docker application will be composed of multiple services.</span></span> <span data-ttu-id="68527-227">Pro tyto případy můžete spustit `docker-compose up` příkazu (obrázek 4 – 27), který použije soubor docker-compose.yml, kterou může jste vytvořili dříve.</span><span class="sxs-lookup"><span data-stu-id="68527-227">For these cases, you can run the `docker-compose up` command (Figure 4-27), which will use the docker-compose.yml file that you might have created previously.</span></span> <span data-ttu-id="68527-228">Spustí tento příkaz nasadí složené aplikaci se všemi jeho související kontejnerů.</span><span class="sxs-lookup"><span data-stu-id="68527-228">Running this command deploys a composed application with all of its related containers.</span></span>

![Výstup z konzoly docker-compose up příkazu.](./media/image27.png)

<span data-ttu-id="68527-230">**Obrázek 4 – 27**.</span><span class="sxs-lookup"><span data-stu-id="68527-230">**Figure 4-27**.</span></span> <span data-ttu-id="68527-231">Výsledky spuštění příkazu "docker-compose up"</span><span class="sxs-lookup"><span data-stu-id="68527-231">Results of running the "docker-compose up" command</span></span>

<span data-ttu-id="68527-232">Po spuštění `docker-compose up`, budete nasazovat aplikace a její související kontejnerů do hostitele Dockeru, jak je znázorněno v obrázek 4 – 28, v reprezentaci virtuálního počítače.</span><span class="sxs-lookup"><span data-stu-id="68527-232">After you run `docker-compose up`, you deploy your application and its related container(s) into your Docker Host, as illustrated in Figure 4-28, in the VM representation.</span></span>

![Virtuální počítač spuštěný vícekontejnerových aplikací.](./media/image28.png)

<span data-ttu-id="68527-234">**Obrázek 4 – 28**.</span><span class="sxs-lookup"><span data-stu-id="68527-234">**Figure 4-28**.</span></span> <span data-ttu-id="68527-235">Virtuální počítač s kontejnery Dockeru nasazené</span><span class="sxs-lookup"><span data-stu-id="68527-235">VM with Docker containers deployed</span></span>

### <a name="step-6-test-your-docker-application-locally-in-your-local-cd-vm"></a><span data-ttu-id="68527-236">Krok 6: Otestujte aplikaci Docker (místně, v místní virtuální počítač CD)</span><span class="sxs-lookup"><span data-stu-id="68527-236">Step 6: Test your Docker application (locally, in your local CD VM)</span></span>

<span data-ttu-id="68527-237">Tento krok se liší v závislosti na tom, co vaše aplikace stojí.</span><span class="sxs-lookup"><span data-stu-id="68527-237">This step will vary depending on what your app is doing.</span></span>

<span data-ttu-id="68527-238">V jednoduchých .NET Core webového rozhraní API "Hello World" nasadit jako jedním kontejnerem nebo služby by stačí pro přístup ke službě zadáním TCP port zadaný v souboru DockerFile.</span><span class="sxs-lookup"><span data-stu-id="68527-238">In a simple .NET Core Web API "Hello World" deployed as a single container or service, you'd just need to access the service by providing the TCP port specified in the DockerFile.</span></span>

<span data-ttu-id="68527-239">Pokud localhost není zapnutý, přejděte k vaší službě zjistit IP adresu počítače pomocí tohoto příkazu:</span><span class="sxs-lookup"><span data-stu-id="68527-239">If localhost is not turned on, to navigate to your service, find the IP address for the machine by using this command:</span></span>

```console
docker-machine {IP} {YOUR-CONTAINER-NAME}
```

<span data-ttu-id="68527-240">Na hostitele Docker spusťte prohlížeč a přejděte na web; vaše aplikace nebo služby spuštěné, měli byste vidět, jak je ukázáno v obrázek 4 – 29.</span><span class="sxs-lookup"><span data-stu-id="68527-240">On the Docker host, open a browser and navigate to that site; you should see your app/service running, as demonstrated in Figure 4-29.</span></span>

![Zobrazit v prohlížeči neodpověděla localhost/API/hodnoty.](./media/image29.png)

<span data-ttu-id="68527-242">**Obrázek 4 – 29**.</span><span class="sxs-lookup"><span data-stu-id="68527-242">**Figure 4-29**.</span></span> <span data-ttu-id="68527-243">Testování aplikace místně s použitím místního hostitele Docker</span><span class="sxs-lookup"><span data-stu-id="68527-243">Testing your Docker application locally using localhost</span></span>

<span data-ttu-id="68527-244">Všimněte si, že používá port 80, ale interně se přesměruje na port 5000, protože to je, jak byla nasazena s `docker run`, jak je vysvětleno výše.</span><span class="sxs-lookup"><span data-stu-id="68527-244">Note that it's using port 80, but internally it's being redirected to port 5000, because that's how it was deployed with `docker run`, as explained earlier.</span></span>

<span data-ttu-id="68527-245">Můžete ho otestovat pomocí příkazu CURL z terminálu.</span><span class="sxs-lookup"><span data-stu-id="68527-245">You can test this by using CURL from the terminal.</span></span> <span data-ttu-id="68527-246">V instalaci Dockeru na Windows je výchozí IP 10.0.75.1, jak je znázorněno v obrázek 4-30.</span><span class="sxs-lookup"><span data-stu-id="68527-246">In a Docker installation on Windows, the default IP is 10.0.75.1, as depicted in Figure 4-30.</span></span>

![Získávání výstupu konzoly http://10.0.75.1/API/values pomocí curl](./media/image30.png)

<span data-ttu-id="68527-248">**Obrázek 4-30**.</span><span class="sxs-lookup"><span data-stu-id="68527-248">**Figure 4-30**.</span></span> <span data-ttu-id="68527-249">Testování aplikace Docker místně pomocí CURL</span><span class="sxs-lookup"><span data-stu-id="68527-249">Testing a Docker application locally by using CURL</span></span>

<span data-ttu-id="68527-250">**Ladění kontejneru spuštěného v Dockeru**</span><span class="sxs-lookup"><span data-stu-id="68527-250">**Debugging a container running on Docker**</span></span>

<span data-ttu-id="68527-251">Visual Studio Code podporuje ladění Dockeru, pokud používáte Node.js a jiných platformách, jako je .NET Core kontejnery.</span><span class="sxs-lookup"><span data-stu-id="68527-251">Visual Studio Code supports debugging Docker if you're using Node.js and other platforms like .NET Core containers.</span></span>

<span data-ttu-id="68527-252">Můžete také ladit kontejnery .NET Core nebo .NET Framework v Dockeru při použití Visual Studio pro Windows nebo Mac, jak je popsáno v další části.</span><span class="sxs-lookup"><span data-stu-id="68527-252">You also can debug .NET Core or .NET Framework containers in Docker when using Visual Studio for Windows or Mac, as described in the next section.</span></span>

> [! INFORMACE O]
>
> <span data-ttu-id="68527-254">Další informace o ladění kontejnerů Dockeru Node.js, přejděte na <https://blog.docker.com/2016/07/live-debugging-docker/> a <https://blogs.msdn.microsoft.com/user_ed/2016/02/27/visual-studio-code-new-features-13-big-debugging-updates-rich-object-hover-conditional-breakpoints-node-js-mono-more/>.</span><span class="sxs-lookup"><span data-stu-id="68527-254">To learn more about debugging Node.js Docker containers, go to <https://blog.docker.com/2016/07/live-debugging-docker/> and <https://blogs.msdn.microsoft.com/user_ed/2016/02/27/visual-studio-code-new-features-13-big-debugging-updates-rich-object-hover-conditional-breakpoints-node-js-mono-more/>.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="68527-255">[Předchozí](docker-apps-development-environment.md)
>[další](visual-studio-tools-for-docker.md)</span><span class="sxs-lookup"><span data-stu-id="68527-255">[Previous](docker-apps-development-environment.md)
[Next](visual-studio-tools-for-docker.md)</span></span>
