---
title: Pracovní postup vývoje vnitřní smyčky pro aplikace Dockeru
description: Naučte se pracovní postup "vnitřní smyčka" pro vývoj aplikací Dockeru.
ms.date: 02/15/2019
ms.openlocfilehash: bce047bd5ba75f9ef652a294ff6a15656fc5ac34
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/21/2020
ms.locfileid: "81738410"
---
# <a name="inner-loop-development-workflow-for-docker-apps"></a><span data-ttu-id="5e874-103">Pracovní postup vývoje vnitřní smyčky pro aplikace Dockeru</span><span class="sxs-lookup"><span data-stu-id="5e874-103">Inner-loop development workflow for Docker apps</span></span>

<span data-ttu-id="5e874-104">Před aktivací vnější smyčky pracovního postupu zahrnující celý cyklus DevOps, to vše začíná na počítači každého vývojáře, kódování samotné aplikace, pomocí jejich preferované jazyky nebo platformy a testování místně (Obrázek 4-21).</span><span class="sxs-lookup"><span data-stu-id="5e874-104">Before triggering the outer-loop workflow spanning the entire DevOps cycle, it all begins on each developer's machine, coding the app itself, using their preferred languages or platforms, and testing it locally (Figure 4-21).</span></span> <span data-ttu-id="5e874-105">Ale v každém případě budete mít důležitý společný bod, bez ohledu na to, jaký jazyk, rámec nebo platformy si vyberete.</span><span class="sxs-lookup"><span data-stu-id="5e874-105">But in every case, you'll have an important point in common, no matter what language, framework, or platforms you choose.</span></span> <span data-ttu-id="5e874-106">V tomto konkrétním pracovním postupu vždy vyvíjíte a testujete kontejnery Dockeru, ale místně.</span><span class="sxs-lookup"><span data-stu-id="5e874-106">In this specific workflow, you're always developing and testing Docker containers, but locally.</span></span>

![Diagram znázorňující koncept vývojového prostředí vnitřní smyčky.](./media/docker-apps-inner-loop-workflow/inner-loop-development-context.png)

<span data-ttu-id="5e874-108">**Obrázek 4-21**.</span><span class="sxs-lookup"><span data-stu-id="5e874-108">**Figure 4-21**.</span></span> <span data-ttu-id="5e874-109">Kontext vývoje vnitřní smyčky</span><span class="sxs-lookup"><span data-stu-id="5e874-109">Inner-loop development context</span></span>

<span data-ttu-id="5e874-110">Kontejner nebo instance image Dockeru bude obsahovat tyto součásti:</span><span class="sxs-lookup"><span data-stu-id="5e874-110">The container or instance of a Docker image will contain these components:</span></span>

- <span data-ttu-id="5e874-111">Výběr operačního systému (například linuxová distribuce nebo Windows)</span><span class="sxs-lookup"><span data-stu-id="5e874-111">An operating system selection (for example, a Linux distribution or Windows)</span></span>

- <span data-ttu-id="5e874-112">Soubory přidané vývojářem (například binární soubory aplikací)</span><span class="sxs-lookup"><span data-stu-id="5e874-112">Files added by the developer (for example, app binaries)</span></span>

- <span data-ttu-id="5e874-113">Konfigurace (například nastavení prostředí a závislosti)</span><span class="sxs-lookup"><span data-stu-id="5e874-113">Configuration (for example, environment settings and dependencies)</span></span>

- <span data-ttu-id="5e874-114">Pokyny pro to, jaké procesy má Docker spouštět</span><span class="sxs-lookup"><span data-stu-id="5e874-114">Instructions for what processes to run by Docker</span></span>

<span data-ttu-id="5e874-115">Můžete nastavit pracovní postup vývoje vnitřní smyčky, který využívá Docker jako proces (popsané v další části).</span><span class="sxs-lookup"><span data-stu-id="5e874-115">You can set up the inner-loop development workflow that utilizes Docker as the process (described in the next section).</span></span> <span data-ttu-id="5e874-116">Zvažte, že počáteční kroky k nastavení prostředí nejsou zahrnuty, protože stačí to udělat jednou.</span><span class="sxs-lookup"><span data-stu-id="5e874-116">Consider that the initial steps to set up the environment are not included, because you only need to do it once.</span></span>

## <a name="building-a-single-app-within-a-docker-container-using-visual-studio-code-and-docker-cli"></a><span data-ttu-id="5e874-117">Vytváření jedné aplikace v kontejneru Dockeru pomocí kódu Visual Studio a cli Dockeru</span><span class="sxs-lookup"><span data-stu-id="5e874-117">Building a single app within a Docker container using Visual Studio Code and Docker CLI</span></span>

<span data-ttu-id="5e874-118">Aplikace se shodnou z vašich vlastních služeb a dalších knihoven (závislostí).</span><span class="sxs-lookup"><span data-stu-id="5e874-118">Apps are made up from your own services plus additional libraries (dependencies).</span></span>

<span data-ttu-id="5e874-119">Obrázek 4-22 ukazuje základní kroky, které obvykle potřebujete provést při vytváření aplikace Dockeru, následované podrobnými popisy každého kroku.</span><span class="sxs-lookup"><span data-stu-id="5e874-119">Figure 4-22 shows the basic steps that you usually need to carry out when building a Docker app, followed by detailed descriptions of each step.</span></span>

![Diagram znázorňující sedm kroků potřebných k vytvoření kontejnerizované aplikace.](./media/docker-apps-inner-loop-workflow/life-cycle-containerized-apps-docker-cli.png)

<span data-ttu-id="5e874-121">**Obrázek 4-22**.</span><span class="sxs-lookup"><span data-stu-id="5e874-121">**Figure 4-22**.</span></span> <span data-ttu-id="5e874-122">Pracovní postup na vysoké úrovni pro životní cyklus kontejnerizovaných aplikací Dockeru pomocí cli Dockeru</span><span class="sxs-lookup"><span data-stu-id="5e874-122">High-level workflow for the life cycle for Docker containerized applications using Docker CLI</span></span>

### <a name="step-1-start-coding-in-visual-studio-code-and-create-your-initial-appservice-baseline"></a><span data-ttu-id="5e874-123">Krok 1: Začněte kódovat v kódu Visual Studia a vytvořte počáteční směrný plán aplikace nebo služby</span><span class="sxs-lookup"><span data-stu-id="5e874-123">Step 1: Start coding in Visual Studio Code and create your initial app/service baseline</span></span>

<span data-ttu-id="5e874-124">Způsob, jakým vyvíjíte aplikaci, je podobný způsobu, jakým to děláte bez Dockeru.</span><span class="sxs-lookup"><span data-stu-id="5e874-124">The way you develop your application is similar to the way you do it without Docker.</span></span> <span data-ttu-id="5e874-125">Rozdíl je v tom, že při vývoji nasazujete a testujete aplikaci nebo služby spuštěné v kontejnerech Dockeru umístěných v místním prostředí (jako je virtuální počítač s Linuxem nebo Windows).</span><span class="sxs-lookup"><span data-stu-id="5e874-125">The difference is that while developing, you're deploying and testing your application or services running within Docker containers placed in your local environment (like a Linux VM or Windows).</span></span>

<span data-ttu-id="5e874-126">**Nastavení místního prostředí**</span><span class="sxs-lookup"><span data-stu-id="5e874-126">**Setting up your local environment**</span></span>

<span data-ttu-id="5e874-127">S nejnovějšími verzemi Dockeru pro Mac a Windows je vývoj aplikací Dockeru jednodušší než kdy dřív a nastavení je jednoduché.</span><span class="sxs-lookup"><span data-stu-id="5e874-127">With the latest versions of Docker for Mac and Windows, it's easier than ever to develop Docker applications, and the setup is straightforward.</span></span>

> [!TIP]
> <span data-ttu-id="5e874-128">Pokyny k nastavení Dockeru pro <https://docs.docker.com/docker-for-windows/>Windows najdete v .</span><span class="sxs-lookup"><span data-stu-id="5e874-128">For instructions on setting up Docker for Windows, go to <https://docs.docker.com/docker-for-windows/>.</span></span>
>
><span data-ttu-id="5e874-129">Pokyny k nastavení Dockeru pro <https://docs.docker.com/docker-for-mac/>Mac najdete v .</span><span class="sxs-lookup"><span data-stu-id="5e874-129">For instructions on setting up Docker for Mac, go to <https://docs.docker.com/docker-for-mac/>.</span></span>

<span data-ttu-id="5e874-130">Kromě toho budete potřebovat editor kódu, takže můžete skutečně rozvíjet aplikaci při použití rozhraní se kdispozici jako rozhraní se kšak dockeru.</span><span class="sxs-lookup"><span data-stu-id="5e874-130">In addition, you'll need a code editor so that you can actually develop your application while using Docker CLI.</span></span>

<span data-ttu-id="5e874-131">Microsoft poskytuje Visual Studio Code, což je lehký editor kódu, který je podporován v systémech Windows, Linux a macOS a poskytuje intelliSense [podporu pro mnoho jazyků](https://code.visualstudio.com/docs/languages/overview) (JavaScript, .NET, Go, Java, Ruby, Python a většina moderních jazyků), [ladění](https://code.visualstudio.com/Docs/editor/debugging), integrace [s Git](https://code.visualstudio.com/Docs/editor/versioncontrol) a podpora [rozšíření](https://code.visualstudio.com/docs/extensions/overview).</span><span class="sxs-lookup"><span data-stu-id="5e874-131">Microsoft provides Visual Studio Code, which is a lightweight code editor that's supported on Windows, Linux, and macOS, and provides IntelliSense with [support for many languages](https://code.visualstudio.com/docs/languages/overview) (JavaScript, .NET, Go, Java, Ruby, Python, and most modern languages), [debugging](https://code.visualstudio.com/Docs/editor/debugging), [integration with Git](https://code.visualstudio.com/Docs/editor/versioncontrol) and [extensions support](https://code.visualstudio.com/docs/extensions/overview).</span></span> <span data-ttu-id="5e874-132">Tento editor je skvělý pro vývojáře macOS a Linux.</span><span class="sxs-lookup"><span data-stu-id="5e874-132">This editor is a great fit for macOS and Linux developers.</span></span> <span data-ttu-id="5e874-133">V systému Windows můžete také použít Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="5e874-133">In Windows, you can also use Visual Studio.</span></span>

> [!TIP]
> <span data-ttu-id="5e874-134">Pokyny k instalaci kódu Sady Visual Studio pro Windows, <https://code.visualstudio.com/docs/setup/setup-overview/>Linux nebo macOS najdete na .</span><span class="sxs-lookup"><span data-stu-id="5e874-134">For instructions on installing Visual Studio Code for Windows, Linux, or macOS, go to <https://code.visualstudio.com/docs/setup/setup-overview/>.</span></span>
>
> <span data-ttu-id="5e874-135">Pokyny k nastavení Dockeru pro <https://docs.docker.com/docker-for-mac/>Mac najdete v .</span><span class="sxs-lookup"><span data-stu-id="5e874-135">For instructions on setting up Docker for Mac, go to <https://docs.docker.com/docker-for-mac/>.</span></span>

<span data-ttu-id="5e874-136">Můžete pracovat s Rozhraním řízení chování dockeru a psát kód pomocí libovolného editoru `Dockerfile` kódu, ale pomocí kódu Visual Studio s rozšířením Dockeru usnadňuje vytváření souborů a `docker-compose.yml` soubory ve vašem pracovním prostoru.</span><span class="sxs-lookup"><span data-stu-id="5e874-136">You can work with Docker CLI and write your code using any code editor, but using Visual Studio Code with the Docker extension makes it easy to author `Dockerfile` and `docker-compose.yml` files in your workspace.</span></span> <span data-ttu-id="5e874-137">Můžete také spustit úlohy a skripty z IDE kódu Visual Studio ke spuštění příkazů Dockeru pomocí cli Dockeru pod ním.</span><span class="sxs-lookup"><span data-stu-id="5e874-137">You can also run tasks and scripts from the Visual Studio Code IDE to execute Docker commands using the Docker CLI underneath.</span></span>

<span data-ttu-id="5e874-138">Rozšíření Dockeru pro Kód VS poskytuje následující funkce:</span><span class="sxs-lookup"><span data-stu-id="5e874-138">The Docker extension for VS Code provides the following features:</span></span>

- <span data-ttu-id="5e874-139">Automatické `Dockerfile` `docker-compose.yml` generování souborů</span><span class="sxs-lookup"><span data-stu-id="5e874-139">Automatic `Dockerfile` and `docker-compose.yml` file generation</span></span>

- <span data-ttu-id="5e874-140">Tipy pro zvýraznění syntaxe a najetí na jev `docker-compose.yml` a `Dockerfile` soubory</span><span class="sxs-lookup"><span data-stu-id="5e874-140">Syntax highlighting and hover tips for `docker-compose.yml` and `Dockerfile` files</span></span>

- <span data-ttu-id="5e874-141">Technologie IntelliSense (dokončení) a `Dockerfile` `docker-compose.yml` souborů</span><span class="sxs-lookup"><span data-stu-id="5e874-141">IntelliSense (completions) for `Dockerfile` and `docker-compose.yml` files</span></span>

- <span data-ttu-id="5e874-142">Linting (chyby a `Dockerfile` upozornění) pro soubory</span><span class="sxs-lookup"><span data-stu-id="5e874-142">Linting (errors and warnings) for `Dockerfile` files</span></span>

- <span data-ttu-id="5e874-143">Integrace palety příkazů (F1) pro nejběžnější příkazy Dockeru</span><span class="sxs-lookup"><span data-stu-id="5e874-143">Command Palette (F1) integration for the most common Docker commands</span></span>

- <span data-ttu-id="5e874-144">Integrace Průzkumníka pro správu obrázků a kontejnerů</span><span class="sxs-lookup"><span data-stu-id="5e874-144">Explorer integration for managing Images and Containers</span></span>

- <span data-ttu-id="5e874-145">Nasazení ibi z DockerHubu a registrů kontejnerů Azure do azure app služby</span><span class="sxs-lookup"><span data-stu-id="5e874-145">Deploy images from DockerHub and Azure Container Registries to Azure App Service</span></span>

<span data-ttu-id="5e874-146">Pokud chcete nainstalovat rozšíření Dockeru, stiskněte `ext install`Ctrl+Shift+P, zadejte a spusťte příkaz Instalovat rozšíření, abyste zoátrali seznam rozšíření Marketplace.</span><span class="sxs-lookup"><span data-stu-id="5e874-146">To install the Docker extension, press Ctrl+Shift+P, type `ext install`, and then run the Install Extension command to bring up the Marketplace extension list.</span></span> <span data-ttu-id="5e874-147">Dále zadejte **docker** pro filtrování výsledků a pak vyberte rozšíření podpory Dockeru, jak je znázorněno na obrázku 4-23.</span><span class="sxs-lookup"><span data-stu-id="5e874-147">Next, type **docker** to filter the results, and then select the Docker Support extension, as depicted in Figure 4-23.</span></span>

![Zobrazení rozšíření Docker pro Kód VS.](./media/docker-apps-inner-loop-workflow/install-docker-extension-vs-code.png)

<span data-ttu-id="5e874-149">**Obrázek 4-23**.</span><span class="sxs-lookup"><span data-stu-id="5e874-149">**Figure 4-23**.</span></span> <span data-ttu-id="5e874-150">Instalace rozšíření Dockeru v kódu Visual Studia</span><span class="sxs-lookup"><span data-stu-id="5e874-150">Installing the Docker Extension in Visual Studio Code</span></span>

### <a name="step-2-create-a-dockerfile-related-to-an-existing-image-plain-os-or-dev-environments-like-net-core-nodejs-and-ruby"></a><span data-ttu-id="5e874-151">Krok 2: Vytvoření souboru DockerFile souvisejícího s existující bitovou kopii (prostředí prostého operačního systému nebo dev, jako je .NET Core, Node.js a Ruby)</span><span class="sxs-lookup"><span data-stu-id="5e874-151">Step 2: Create a DockerFile related to an existing image (plain OS or dev environments like .NET Core, Node.js, and Ruby)</span></span>

<span data-ttu-id="5e874-152">Budete potřebovat `DockerFile` vlastní image, která má být sestavena a na kontejner, který chcete nasadit.</span><span class="sxs-lookup"><span data-stu-id="5e874-152">You'll need a `DockerFile` per custom image to be built and per container to be deployed.</span></span> <span data-ttu-id="5e874-153">Pokud je vaše aplikace tvořena jedinou vlastní službou, budete potřebovat jednu `DockerFile`.</span><span class="sxs-lookup"><span data-stu-id="5e874-153">If your app is made up of a single custom service, you'll need a single `DockerFile`.</span></span> <span data-ttu-id="5e874-154">Ale pokud se vaše aplikace skládá z více služeb (jako v `Dockerfile` architektuře mikroslužeb), budete potřebovat jednu na službu.</span><span class="sxs-lookup"><span data-stu-id="5e874-154">But if your app is composed of multiple services (as in a microservices architecture), you'll need one `Dockerfile` per service.</span></span>

<span data-ttu-id="5e874-155">Obvykle `DockerFile` se umisťuje do kořenové složky vaší aplikace nebo služby a obsahuje požadované příkazy, aby Docker věděl, jak tuto aplikaci nebo službu nastavit a spustit.</span><span class="sxs-lookup"><span data-stu-id="5e874-155">The `DockerFile` is commonly placed in the root folder of your app or service and contains the required commands so that Docker knows how to set up and run that app or service.</span></span> <span data-ttu-id="5e874-156">Můžete vytvořit `DockerFile` a přidat do projektu spolu s kódem (node.js, .NET Core, atd.), nebo pokud jste v prostředí noví, podívejte se na následující tip.</span><span class="sxs-lookup"><span data-stu-id="5e874-156">You can create your `DockerFile` and add it to your project along with your code (node.js, .NET Core, etc.), or, if you're new to the environment, take a look at the following Tip.</span></span>

> [!TIP]
> <span data-ttu-id="5e874-157">Můžete použít rozšíření Docker u vás `Dockerfile` při `docker-compose.yml` použití a soubory související s kontejnery Dockeru.</span><span class="sxs-lookup"><span data-stu-id="5e874-157">You can use the Docker extension to guide you when using the `Dockerfile` and `docker-compose.yml` files related to your Docker containers.</span></span> <span data-ttu-id="5e874-158">Nakonec budete pravděpodobně psát tyto druhy souborů bez tohoto nástroje, ale pomocí rozšíření Docker je dobrým výchozím bodem, který urychlí křivku učení.</span><span class="sxs-lookup"><span data-stu-id="5e874-158">Eventually, you'll probably write these kinds of files without this tool, but using the Docker extension is a good starting point that will accelerate your learning curve.</span></span>

<span data-ttu-id="5e874-159">Na obrázku 4-24 můžete vidět, jak se přidá soubor docker-compose pomocí rozšíření Dockeru pro kód VS.</span><span class="sxs-lookup"><span data-stu-id="5e874-159">In Figure 4-24, you can see how a docker-compose file is added by using the Docker Extension for VS Code.</span></span>

![Zobrazení konzoly rozšíření Dockeru pro Kód VS.](./media/docker-apps-inner-loop-workflow/add-docker-files-to-workspace-command.png)

<span data-ttu-id="5e874-161">**Obrázek 4-24**.</span><span class="sxs-lookup"><span data-stu-id="5e874-161">**Figure 4-24**.</span></span> <span data-ttu-id="5e874-162">Soubory Dockeru přidané pomocí **příkazu Přidat soubory Dockeru do pracovního prostoru**</span><span class="sxs-lookup"><span data-stu-id="5e874-162">Docker files added using the **Add Docker files to Workspace command**</span></span>

<span data-ttu-id="5e874-163">Když přidáte DockerFile, určíte, jakou základní image Dockeru `FROM mcr.microsoft.com/dotnet/core/aspnet`budete používat (například pomocí ).</span><span class="sxs-lookup"><span data-stu-id="5e874-163">When you add a DockerFile, you specify what base Docker image you'll be using (like using `FROM mcr.microsoft.com/dotnet/core/aspnet`).</span></span> <span data-ttu-id="5e874-164">Obvykle vytvoříte vlastní bitovou kopii nad základní bitovou kopii, kterou získáte z libovolného oficiálního úložiště v [registru Docker Hub](https://hub.docker.com/) (jako je [obrázek pro .NET Core](https://hub.docker.com/_/microsoft-dotnet-core/) nebo obrázek pro [Node.js).](https://hub.docker.com/_/node/)</span><span class="sxs-lookup"><span data-stu-id="5e874-164">You'll usually build your custom image on top of a base image that you get from any official repository at the [Docker Hub registry](https://hub.docker.com/) (like an [image for .NET Core](https://hub.docker.com/_/microsoft-dotnet-core/) or the one [for Node.js](https://hub.docker.com/_/node/)).</span></span>

<span data-ttu-id="5e874-165">***Použití existujícího oficiálního obrázku Dockeru***</span><span class="sxs-lookup"><span data-stu-id="5e874-165">***Use an existing official Docker image***</span></span>

<span data-ttu-id="5e874-166">Pomocí oficiálníúložiště zásobníku jazyka s číslem verze zajišťuje, že stejné funkce jazyka jsou k dispozici na všech počítačích (včetně vývoje, testování a výroby).</span><span class="sxs-lookup"><span data-stu-id="5e874-166">Using an official repository of a language stack with a version number ensures that the same language features are available on all machines (including development, testing, and production).</span></span>

<span data-ttu-id="5e874-167">Následuje ukázkový soubor DockerFile pro kontejner .NET Core:</span><span class="sxs-lookup"><span data-stu-id="5e874-167">The following is a sample DockerFile for a .NET Core container:</span></span>

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

<span data-ttu-id="5e874-168">V tomto případě je obraz založen na verzi 2.2 oficiálního ASP.NET Image Core Docker (multi-arch pro Linux a Windows), podle řádku `FROM mcr.microsoft.com/dotnet/core/aspnet:2.2`.</span><span class="sxs-lookup"><span data-stu-id="5e874-168">In this case, the image is based on version 2.2 of the official ASP.NET Core Docker image (multi-arch for Linux and Windows), as per the line `FROM mcr.microsoft.com/dotnet/core/aspnet:2.2`.</span></span> <span data-ttu-id="5e874-169">(Další informace o tomto tématu najdete na stránce [ASP.NET core dockerimage](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) a na stránce [.NET Core Docker Image).](https://hub.docker.com/_/microsoft-dotnet-core/)</span><span class="sxs-lookup"><span data-stu-id="5e874-169">(For more information about this topic, see the [ASP.NET Core Docker Image](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) page and the [.NET Core Docker Image](https://hub.docker.com/_/microsoft-dotnet-core/) page).</span></span>

<span data-ttu-id="5e874-170">V DockerFile můžete také pokyn Docker poslouchat tcp port, který budete používat za běhu (například port 80).</span><span class="sxs-lookup"><span data-stu-id="5e874-170">In the DockerFile, you can also instruct Docker to listen to the TCP port that you'll use at runtime (such as port 80).</span></span>

<span data-ttu-id="5e874-171">Můžete zadat další nastavení konfigurace v Dockerfile, v závislosti na jazyku a rozhraní, které používáte.</span><span class="sxs-lookup"><span data-stu-id="5e874-171">You can specify additional configuration settings in the Dockerfile, depending on the language and framework you're using.</span></span> <span data-ttu-id="5e874-172">Například `ENTRYPOINT` řádek s `["dotnet", "MySingleContainerWebApp.dll"]` říká Docker spustit aplikaci .NET Core.</span><span class="sxs-lookup"><span data-stu-id="5e874-172">For instance, the `ENTRYPOINT` line with `["dotnet", "MySingleContainerWebApp.dll"]` tells Docker to run a .NET Core application.</span></span> <span data-ttu-id="5e874-173">Pokud k sestavení a spuštění aplikace .NET používáte`dotnet CLI`sadu SDK a rozhraní .NET Core CLI ( ), bude toto nastavení jiné.</span><span class="sxs-lookup"><span data-stu-id="5e874-173">If you're using the SDK and the .NET Core CLI (`dotnet CLI`) to build and run the .NET application, this setting would be different.</span></span> <span data-ttu-id="5e874-174">Klíčovým bodem je, že řádek ENTRYPOINT a další nastavení závisí na jazyku a platformě, kterou zvolíte pro vaši aplikaci.</span><span class="sxs-lookup"><span data-stu-id="5e874-174">The key point here is that the ENTRYPOINT line and other settings depend on the language and platform you choose for your application.</span></span>

> [!TIP]
> <span data-ttu-id="5e874-175">Další informace o vytváření iniciál Dockeru pro aplikace .NET Core najdete v . <https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images></span><span class="sxs-lookup"><span data-stu-id="5e874-175">For more information about building Docker images for .NET Core applications, go to <https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images>.</span></span>
>
> <span data-ttu-id="5e874-176">Další informace o vytváření vlastních <https://docs.docker.com/engine/tutorials/dockerimages/>obrázků naleznete v najdete v aplikaci .</span><span class="sxs-lookup"><span data-stu-id="5e874-176">To learn more about building your own images, go to <https://docs.docker.com/engine/tutorials/dockerimages/>.</span></span>

<span data-ttu-id="5e874-177">**Použití víceobloukových úložišť obrázků**</span><span class="sxs-lookup"><span data-stu-id="5e874-177">**Use multi-arch image repositories**</span></span>

<span data-ttu-id="5e874-178">Název jedné bitové kopie v repo může obsahovat varianty platformy, jako je například bitová kopie Linuxu a bitová kopie systému Windows.</span><span class="sxs-lookup"><span data-stu-id="5e874-178">A single image name in a repo can contain platform variants, such as a Linux image and a Windows image.</span></span> <span data-ttu-id="5e874-179">Tato funkce umožňuje dodavatelům, jako je Microsoft (tvůrci základních obrázků), vytvořit jeden repo, který by pokrýval více platforem (tedy Linux a Windows).</span><span class="sxs-lookup"><span data-stu-id="5e874-179">This feature allows vendors like Microsoft (base image creators) to create a single repo to cover multiple platforms (that is, Linux and Windows).</span></span> <span data-ttu-id="5e874-180">Například úložiště [dotnet/core/aspnet,](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) které je k dispozici v registru Docker Hub, poskytuje podporu pro Linux a Windows Nano Server pomocí stejného názvu bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="5e874-180">For example, the [dotnet/core/aspnet](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) repository available in the Docker Hub registry provides support for Linux and Windows Nano Server by using the same image name.</span></span>

<span data-ttu-id="5e874-181">Vytažením bitové kopie [dotnet/core/aspnet](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) z hostitele systému Windows se vyžádá varianta systému Windows, zatímco vytažení stejného názvu bitové kopie z hostitele Linuxu vytáhne variantu Linuxu.</span><span class="sxs-lookup"><span data-stu-id="5e874-181">Pulling the [dotnet/core/aspnet](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) image from a Windows host pulls the Windows variant, whereas pulling the same image name from a Linux host pulls the Linux variant.</span></span>

<span data-ttu-id="5e874-182">***Vytvoření základního obrázku od začátku***</span><span class="sxs-lookup"><span data-stu-id="5e874-182">***Create your base image from scratch***</span></span>

<span data-ttu-id="5e874-183">Můžete vytvořit vlastní základní image Dockeru od začátku, jak je vysvětleno v tomto [článku](https://docs.docker.com/engine/userguide/eng-image/baseimages/) z Dockeru.</span><span class="sxs-lookup"><span data-stu-id="5e874-183">You can create your own Docker base image from scratch as explained in this [article](https://docs.docker.com/engine/userguide/eng-image/baseimages/) from Docker.</span></span> <span data-ttu-id="5e874-184">Tento scénář pravděpodobně není nejlepší pro vás, pokud jste právě začínás Docker, ale pokud chcete nastavit konkrétní bity vlastní základní image, můžete to udělat.</span><span class="sxs-lookup"><span data-stu-id="5e874-184">This scenario is probably not the best for you if you're just starting with Docker, but if you want to set the specific bits of your own base image, you can do it.</span></span>

### <a name="step-3-create-your-custom-docker-images-embedding-your-service-in-it"></a><span data-ttu-id="5e874-185">Krok 3: Vytvoření vlastních ireček Dockeru, které do ní vloží vaši službu</span><span class="sxs-lookup"><span data-stu-id="5e874-185">Step 3: Create your custom Docker images embedding your service in it</span></span>

<span data-ttu-id="5e874-186">Pro každou vlastní službu, která obsahuje vaši aplikaci, budete muset vytvořit související obrázek.</span><span class="sxs-lookup"><span data-stu-id="5e874-186">For each custom service that comprises your app, you'll need to create a related image.</span></span> <span data-ttu-id="5e874-187">Pokud se vaše aplikace skládá z jedné služby nebo webové aplikace, budete potřebovat jen jeden obrázek.</span><span class="sxs-lookup"><span data-stu-id="5e874-187">If your app is made up of a single service or web app, you'll need just a single image.</span></span>

> [!NOTE]
> <span data-ttu-id="5e874-188">Vezmeme-li v úvahu "vnější smyčka DevOps workflow", budou obrázky vytvořeny automatizovaným procesem sestavení při každém nabízení zdrojového kódu do úložiště Git (průběžná integrace), takže obrázky budou vytvořeny v tomto globálním prostředí z vašeho zdrojového kódu.</span><span class="sxs-lookup"><span data-stu-id="5e874-188">When taking into account the "outer-loop DevOps workflow", the images will be created by an automated build process whenever you push your source code to a Git repository (Continuous Integration), so the images will be created in that global environment from your source code.</span></span>
>
> <span data-ttu-id="5e874-189">Ale předtím, než budeme uvažovat o tom, že vnější smyčka trasy, musíme zajistit, že aplikace Docker je skutečně funguje správně tak, aby nebyly push kód, který nemusí fungovat správně do systému správy zdrojového kódu (Git, atd.).</span><span class="sxs-lookup"><span data-stu-id="5e874-189">But before we consider going to that outer-loop route, we need to ensure that the Docker application is actually working properly so that they don't push code that might not work properly to the source control system (Git, etc.).</span></span>
>
> <span data-ttu-id="5e874-190">Proto každý vývojář nejprve musí provést celý proces vnitřní smyčky k testování místně a pokračovat ve vývoji, dokud chtějí push kompletní funkce nebo změnit systém správy zdrojového kódu.</span><span class="sxs-lookup"><span data-stu-id="5e874-190">Therefore, each developer first needs to do the entire inner-loop process to test locally and continue developing until they want to push a complete feature or change to the source control system.</span></span>

<span data-ttu-id="5e874-191">Chcete-li vytvořit image v místním prostředí a pomocí DockerFile, můžete použít příkaz sestavení dockeru, jak `docker-compose up --build` je znázorněno na obrázku 4-25 (můžete také spustit pro aplikace složené z několika kontejnerů/služeb).</span><span class="sxs-lookup"><span data-stu-id="5e874-191">To create an image in your local environment and using the DockerFile, you can use the docker build command, as demonstrated in Figure 4-25 (you can also run `docker-compose up --build` for applications composed by several containers/services).</span></span>

![Snímek obrazovky zobrazující výstup konzoly příkazu docker build.](./media/docker-apps-inner-loop-workflow/run-docker-build-command.png)

<span data-ttu-id="5e874-193">**Obrázek 4-25**.</span><span class="sxs-lookup"><span data-stu-id="5e874-193">**Figure 4-25**.</span></span> <span data-ttu-id="5e874-194">Spuštění sestavení dockeru</span><span class="sxs-lookup"><span data-stu-id="5e874-194">Running docker build</span></span>

<span data-ttu-id="5e874-195">Volitelně můžete namísto `docker build` přímého spuštění ze složky projektu nejprve vygenerovat nasaditelnou `dotnet publish` složku s `docker build`knihovnami .NET potřebnými pomocí příkazu run a poté spustit .</span><span class="sxs-lookup"><span data-stu-id="5e874-195">Optionally, instead of directly running `docker build` from the project folder, you first can generate a deployable folder with the .NET libraries needed by using the run `dotnet publish` command, and then run `docker build`.</span></span>

<span data-ttu-id="5e874-196">Tento příklad vytvoří image Dockeru s názvem `cesardl/netcore-webapi-microservice-docker:first` (`:first` je značka, jako konkrétní verze).</span><span class="sxs-lookup"><span data-stu-id="5e874-196">This example creates a Docker image with the name `cesardl/netcore-webapi-microservice-docker:first` (`:first` is a tag, like a specific version).</span></span> <span data-ttu-id="5e874-197">Tento krok můžete provést pro každou vlastní bitovou kopii, kterou potřebujete vytvořit pro komponoci aplikace Docker s několika kontejnery.</span><span class="sxs-lookup"><span data-stu-id="5e874-197">You can take this step for each custom image you need to create for your composed Docker application with several containers.</span></span>

<span data-ttu-id="5e874-198">Existující obrázky najdete v místním úložišti (vývojovém počítači) pomocí příkazu ilustračních zařízení, jak je znázorněno na obrázku 4-26.</span><span class="sxs-lookup"><span data-stu-id="5e874-198">You can find the existing images in your local repository (your development machine) by using the docker images command, as illustrated in Figure 4-26.</span></span>

![Konzolový výstup z iobrazů řídicího místa s existujícími obrazy.](./media/docker-apps-inner-loop-workflow/view-existing-images-with-docker-images.png)

<span data-ttu-id="5e874-200">**Obrázek 4-26**.</span><span class="sxs-lookup"><span data-stu-id="5e874-200">**Figure 4-26**.</span></span> <span data-ttu-id="5e874-201">Zobrazení existujících obrazů pomocí imitací dockeru</span><span class="sxs-lookup"><span data-stu-id="5e874-201">Viewing existing images using docker images</span></span>

### <a name="step-4-define-your-services-in-docker-composeyml-when-building-a-composed-docker-app-with-multiple-services"></a><span data-ttu-id="5e874-202">Krok 4: Definování služeb v docker-compose.yml při vytváření složené aplikace Docker u více služeb</span><span class="sxs-lookup"><span data-stu-id="5e874-202">Step 4: Define your services in docker-compose.yml when building a composed Docker app with multiple services</span></span>

<span data-ttu-id="5e874-203">Pomocí `docker-compose.yml` souboru můžete definovat sadu souvisejících služeb, které mají být nasazeny jako komponovaná aplikace s příkazy nasazení vysvětlenými v části dalšího kroku.</span><span class="sxs-lookup"><span data-stu-id="5e874-203">With the `docker-compose.yml` file, you can define a set of related services to be deployed as a composed application with the deployment commands explained in the next step section.</span></span>

<span data-ttu-id="5e874-204">Vytvořte tento soubor v hlavní nebo kořenové složce řešení; měl by mít podobný obsah, `docker-compose.yml` který je uveden v tomto souboru:</span><span class="sxs-lookup"><span data-stu-id="5e874-204">Create that file in your main or root solution folder; it should have content similar to that shown in this `docker-compose.yml` file:</span></span>

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

<span data-ttu-id="5e874-205">V tomto konkrétním případě tento soubor definuje dvě služby: webovou službu (vlastní službu) a službu redis (oblíbenou službu mezipaměti).</span><span class="sxs-lookup"><span data-stu-id="5e874-205">In this particular case, this file defines two services: the web service (your custom service) and the redis service (a popular cache service).</span></span> <span data-ttu-id="5e874-206">Každá služba bude nasazena jako kontejner, takže pro každou z nich musíme použít konkrétní image Dockeru.</span><span class="sxs-lookup"><span data-stu-id="5e874-206">Each service will be deployed as a container, so we need to use a concrete Docker image for each.</span></span> <span data-ttu-id="5e874-207">Pro tuto konkrétní webovou službu bude nutné obrázek provést následující kroky:</span><span class="sxs-lookup"><span data-stu-id="5e874-207">For this particular web service, the image will need to do the following:</span></span>

- <span data-ttu-id="5e874-208">Sestavení z DockerFile v aktuálním adresáři</span><span class="sxs-lookup"><span data-stu-id="5e874-208">Build from the DockerFile in the current directory</span></span>

- <span data-ttu-id="5e874-209">Přepošlete exponovaný port 80 na kontejner u portu 81 na hostitelském počítači</span><span class="sxs-lookup"><span data-stu-id="5e874-209">Forward the exposed port 80 on the container to port 81 on the host machine</span></span>

- <span data-ttu-id="5e874-210">Připojení adresáře projektu na hostiteli do /code v kontejneru, takže můžete upravit kód bez nutnosti znovu sestavit bitovou kopii</span><span class="sxs-lookup"><span data-stu-id="5e874-210">Mount the project directory on the host to /code within the container, making it possible for you to modify the code without having to rebuild the image</span></span>

- <span data-ttu-id="5e874-211">Propojení webové služby se službou redis</span><span class="sxs-lookup"><span data-stu-id="5e874-211">Link the web service to the redis service</span></span>

<span data-ttu-id="5e874-212">Služba redis používá [nejnovější veřejnou image redis](https://hub.docker.com/_/redis/) z registru Docker Hub.</span><span class="sxs-lookup"><span data-stu-id="5e874-212">The redis service uses the [latest public redis image](https://hub.docker.com/_/redis/) pulled from the Docker Hub registry.</span></span> <span data-ttu-id="5e874-213">[redis](https://redis.io/) je populární cache systém pro aplikace na straně serveru.</span><span class="sxs-lookup"><span data-stu-id="5e874-213">[redis](https://redis.io/) is a popular cache system for server-side applications.</span></span>

### <a name="step-5-build-and-run-your-docker-app"></a><span data-ttu-id="5e874-214">Krok 5: Vytvoření a spuštění aplikace Docker</span><span class="sxs-lookup"><span data-stu-id="5e874-214">Step 5: Build and run your Docker app</span></span>

<span data-ttu-id="5e874-215">Pokud vaše aplikace má jenom jeden kontejner, stačí ho spustit nasazením do hostitele Dockeru (virtuálnípočítač nebo fyzický server).</span><span class="sxs-lookup"><span data-stu-id="5e874-215">If your app has only a single container, you just need to run it by deploying it to your Docker Host (VM or physical server).</span></span> <span data-ttu-id="5e874-216">Pokud je však vaše aplikace tvořena více službami, musíte *ji také sestavit*.</span><span class="sxs-lookup"><span data-stu-id="5e874-216">However, if your app is made up of multiple services, you need to *compose it*, too.</span></span> <span data-ttu-id="5e874-217">Podívejme se na různé možnosti.</span><span class="sxs-lookup"><span data-stu-id="5e874-217">Let's see the different options.</span></span>

<span data-ttu-id="5e874-218">***Možnost A: Spuštění jednoho kontejneru nebo služby***</span><span class="sxs-lookup"><span data-stu-id="5e874-218">***Option A: Run a single container or service***</span></span>

<span data-ttu-id="5e874-219">Image Dockeru můžete spustit pomocí příkazu docker run, jak je znázorněno zde:</span><span class="sxs-lookup"><span data-stu-id="5e874-219">You can run the Docker image by using the docker run command, as shown here:</span></span>

```console
docker run -t -d -p 80:5000 cesardl/netcore-webapi-microservice-docker:first
```

<span data-ttu-id="5e874-220">Pro toto konkrétní nasazení přesměrujeme požadavky odeslané na port 80 na interní port 5000.</span><span class="sxs-lookup"><span data-stu-id="5e874-220">For this particular deployment, we'll be redirecting requests sent to port 80 to the internal port 5000.</span></span> <span data-ttu-id="5e874-221">Nyní aplikace naslouchá na externím portu 80 na úrovni hostitele.</span><span class="sxs-lookup"><span data-stu-id="5e874-221">Now the application is listening on the external port 80 at the host level.</span></span>

<span data-ttu-id="5e874-222">***Možnost B: Vytvoření a spuštění aplikace s více kontejnery***</span><span class="sxs-lookup"><span data-stu-id="5e874-222">***Option B: Compose and run a multiple-container application***</span></span>

<span data-ttu-id="5e874-223">Ve většině podnikových scénářů aplikace Dockeru se bude skládat z více služeb.</span><span class="sxs-lookup"><span data-stu-id="5e874-223">In most enterprise scenarios, a Docker application will be composed of multiple services.</span></span> <span data-ttu-id="5e874-224">V těchto případech můžete `docker-compose up` spustit příkaz (obrázek 4-27), který bude používat soubor docker-compose.yml, který jste vytvořili dříve.</span><span class="sxs-lookup"><span data-stu-id="5e874-224">For these cases, you can run the `docker-compose up` command (Figure 4-27), which will use the docker-compose.yml file that you might have created previously.</span></span> <span data-ttu-id="5e874-225">Spuštění tohoto příkazu nasadí složenou aplikaci se všemi souvisejícími kontejnery.</span><span class="sxs-lookup"><span data-stu-id="5e874-225">Running this command deploys a composed application with all of its related containers.</span></span>

![Výstup konzoly z příkazu docker-compose up.](./media/docker-apps-inner-loop-workflow/results-docker-compose-up.png)

<span data-ttu-id="5e874-227">**Obrázek 4-27**.</span><span class="sxs-lookup"><span data-stu-id="5e874-227">**Figure 4-27**.</span></span> <span data-ttu-id="5e874-228">Výsledky spuštění příkazu "docker-compose up"</span><span class="sxs-lookup"><span data-stu-id="5e874-228">Results of running the "docker-compose up" command</span></span>

<span data-ttu-id="5e874-229">Po spuštění `docker-compose up`nasadíte aplikaci a související kontejnery do hostitele Dockeru, jak je znázorněno na obrázku 4-28, v reprezentaci virtuálního počítače.</span><span class="sxs-lookup"><span data-stu-id="5e874-229">After you run `docker-compose up`, you deploy your application and its related container(s) into your Docker Host, as illustrated in Figure 4-28, in the VM representation.</span></span>

![Virtuální montovny se spouštějí aplikace s více kontejnery.](./media/docker-apps-inner-loop-workflow/vm-with-docker-containers-deployed.png)

<span data-ttu-id="5e874-231">**Obrázek 4-28**.</span><span class="sxs-lookup"><span data-stu-id="5e874-231">**Figure 4-28**.</span></span> <span data-ttu-id="5e874-232">Virtuální virtuální ms s nasazenými kontejnery Dockeru</span><span class="sxs-lookup"><span data-stu-id="5e874-232">VM with Docker containers deployed</span></span>

### <a name="step-6-test-your-docker-application-locally-in-your-local-cd-vm"></a><span data-ttu-id="5e874-233">Krok 6: Otestujte aplikaci Dockeru (místně, v místním virtuálním počítači CD)</span><span class="sxs-lookup"><span data-stu-id="5e874-233">Step 6: Test your Docker application (locally, in your local CD VM)</span></span>

<span data-ttu-id="5e874-234">Tento krok se bude lišit v závislosti na tom, co vaše aplikace dělá.</span><span class="sxs-lookup"><span data-stu-id="5e874-234">This step will vary depending on what your app is doing.</span></span>

<span data-ttu-id="5e874-235">V jednoduchém webovém rozhraní .NET Core Web API "Hello World" nasazeném jako jeden kontejner nebo služba byste měli získat přístup ke službě poskytnutím portu TCP určeného v souboru DockerFile.</span><span class="sxs-lookup"><span data-stu-id="5e874-235">In a simple .NET Core Web API "Hello World" deployed as a single container or service, you'd just need to access the service by providing the TCP port specified in the DockerFile.</span></span>

<span data-ttu-id="5e874-236">Pokud localhost není zapnuta, chcete-li přejít na službu, vyhledejte IP adresu pro počítač pomocí tohoto příkazu:</span><span class="sxs-lookup"><span data-stu-id="5e874-236">If localhost is not turned on, to navigate to your service, find the IP address for the machine by using this command:</span></span>

```console
docker-machine {IP} {YOUR-CONTAINER-NAME}
```

<span data-ttu-id="5e874-237">Na hostiteli Dockeru otevřete prohlížeč a přejděte na tento web. měli byste vidět vaše aplikace / služba běží, jak je znázorněno na obrázku 4-29.</span><span class="sxs-lookup"><span data-stu-id="5e874-237">On the Docker host, open a browser and navigate to that site; you should see your app/service running, as demonstrated in Figure 4-29.</span></span>

![Zobrazení prohlížeče odpovědi z localhost/API/values.](./media/docker-apps-inner-loop-workflow/test-docker-app-locally-localhost.png)

<span data-ttu-id="5e874-239">**Obrázek 4-29**.</span><span class="sxs-lookup"><span data-stu-id="5e874-239">**Figure 4-29**.</span></span> <span data-ttu-id="5e874-240">Testování aplikace Docker místně pomocí localhost</span><span class="sxs-lookup"><span data-stu-id="5e874-240">Testing your Docker application locally using localhost</span></span>

<span data-ttu-id="5e874-241">Všimněte si, že používá port 80, ale interně je přesměrován na port 5000, `docker run`protože tak to bylo nasazeno s , jak bylo vysvětleno dříve.</span><span class="sxs-lookup"><span data-stu-id="5e874-241">Note that it's using port 80, but internally it's being redirected to port 5000, because that's how it was deployed with `docker run`, as explained earlier.</span></span>

<span data-ttu-id="5e874-242">Můžete to vyzkoušet pomocí CURL z terminálu.</span><span class="sxs-lookup"><span data-stu-id="5e874-242">You can test this by using CURL from the terminal.</span></span> <span data-ttu-id="5e874-243">V instalaci Dockeru v systému Windows je výchozí ADRESA IP 10.0.75.1, jak je znázorněno na obrázku 4-30.</span><span class="sxs-lookup"><span data-stu-id="5e874-243">In a Docker installation on Windows, the default IP is 10.0.75.1, as depicted in Figure 4-30.</span></span>

![Konzolový výstup http://10.0.75.1/API/values od získání s curl](./media/docker-apps-inner-loop-workflow/test-docker-app-locally-curl.png)

<span data-ttu-id="5e874-245">**Obrázek 4-30**.</span><span class="sxs-lookup"><span data-stu-id="5e874-245">**Figure 4-30**.</span></span> <span data-ttu-id="5e874-246">Testování aplikace Docker místně pomocí CURL</span><span class="sxs-lookup"><span data-stu-id="5e874-246">Testing a Docker application locally by using CURL</span></span>

<span data-ttu-id="5e874-247">**Ladění kontejneru spuštěného v Dockeru**</span><span class="sxs-lookup"><span data-stu-id="5e874-247">**Debugging a container running on Docker**</span></span>

<span data-ttu-id="5e874-248">Visual Studio Code podporuje ladění Dockeru, pokud používáte Node.js a další platformy, jako jsou kontejnery .NET Core.</span><span class="sxs-lookup"><span data-stu-id="5e874-248">Visual Studio Code supports debugging Docker if you're using Node.js and other platforms like .NET Core containers.</span></span>

<span data-ttu-id="5e874-249">Při použití Visual Studia pro Windows nebo Mac můžete také ladit kontejnery .NET Core nebo .NET Framework v Dockeru, jak je popsáno v další části.</span><span class="sxs-lookup"><span data-stu-id="5e874-249">You can also debug .NET Core or .NET Framework containers in Docker when using Visual Studio for Windows or Mac, as described in the next section.</span></span>

> [!TIP]
> <span data-ttu-id="5e874-250">Další informace o ladění kontejnerů Node.js <https://blog.docker.com/2016/07/live-debugging-docker/> Dockeru naleznete v tématu a <https://docs.microsoft.com/archive/blogs/user_ed/visual-studio-code-new-features-13-big-debugging-updates-rich-object-hover-conditional-breakpoints-node-js-mono-more>.</span><span class="sxs-lookup"><span data-stu-id="5e874-250">To learn more about debugging Node.js Docker containers, see <https://blog.docker.com/2016/07/live-debugging-docker/> and <https://docs.microsoft.com/archive/blogs/user_ed/visual-studio-code-new-features-13-big-debugging-updates-rich-object-hover-conditional-breakpoints-node-js-mono-more>.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="5e874-251">[Předchozí](docker-apps-development-environment.md)
>[další](visual-studio-tools-for-docker.md)</span><span class="sxs-lookup"><span data-stu-id="5e874-251">[Previous](docker-apps-development-environment.md)
[Next](visual-studio-tools-for-docker.md)</span></span>
