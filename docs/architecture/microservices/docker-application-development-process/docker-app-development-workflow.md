---
title: Pracovní postup vývoje aplikací Dockeru
description: Seznamte se s podrobnostmi pracovního postupu pro vývoj aplikací založených na Dockeru. Začněte krok za krokem a získejte do některých podrobností pro optimalizaci dockerfiles a zakončujte zjednodušeným pracovním postupem, který je k dispozici při použití sady Visual Studio.
ms.date: 01/30/2020
ms.openlocfilehash: 2f380c840e186c345f9222aa6b0cf1097a74874e
ms.sourcegitcommit: c91110ef6ee3fedb591f3d628dc17739c4a7071e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/15/2020
ms.locfileid: "81389200"
---
# <a name="development-workflow-for-docker-apps"></a><span data-ttu-id="995de-104">Pracovní postup vývoje aplikací Dockeru</span><span class="sxs-lookup"><span data-stu-id="995de-104">Development workflow for Docker apps</span></span>

<span data-ttu-id="995de-105">Životní cyklus vývoje aplikace začíná u vašeho počítače jako vývojář, kde aplikaci kódujete pomocí upřednostňovaného jazyka a testujete ji místně.</span><span class="sxs-lookup"><span data-stu-id="995de-105">The application development life cycle starts at your computer, as a developer, where you code the application using your preferred language and test it locally.</span></span> <span data-ttu-id="995de-106">S tímto pracovním postupem, bez ohledu na to, jaký jazyk, architekturu a platformu zvolíte, vždy vyvíjíte a testujete kontejnery Dockeru, ale děláte to místně.</span><span class="sxs-lookup"><span data-stu-id="995de-106">With this workflow, no matter which language, framework, and platform you choose, you're always developing and testing Docker containers, but doing so locally.</span></span>

<span data-ttu-id="995de-107">Každý kontejner (instance image Dockeru) obsahuje následující součásti:</span><span class="sxs-lookup"><span data-stu-id="995de-107">Each container (an instance of a Docker image) includes the following components:</span></span>

- <span data-ttu-id="995de-108">Výběr operačního systému, například linuxová distribuce, Windows Nano Server nebo Windows Server Core.</span><span class="sxs-lookup"><span data-stu-id="995de-108">An operating system selection, for example, a Linux distribution, Windows Nano Server, or Windows Server Core.</span></span>

- <span data-ttu-id="995de-109">Soubory přidané během vývoje, například zdrojový kód a binární soubory aplikace.</span><span class="sxs-lookup"><span data-stu-id="995de-109">Files added during development, for example, source code and application binaries.</span></span>

- <span data-ttu-id="995de-110">Informace o konfiguraci, jako je například nastavení prostředí a závislosti.</span><span class="sxs-lookup"><span data-stu-id="995de-110">Configuration information, such as environment settings and dependencies.</span></span>

## <a name="workflow-for-developing-docker-container-based-applications"></a><span data-ttu-id="995de-111">Pracovní postup pro vývoj aplikací založených na kontejnerech Dockeru</span><span class="sxs-lookup"><span data-stu-id="995de-111">Workflow for developing Docker container-based applications</span></span>

<span data-ttu-id="995de-112">Tato část popisuje pracovní postup vývoje *vnitřní smyčky* pro aplikace založené na kontejnerech Dockeru.</span><span class="sxs-lookup"><span data-stu-id="995de-112">This section describes the *inner-loop* development workflow for Docker container-based applications.</span></span> <span data-ttu-id="995de-113">Pracovní postup vnitřní smyčky znamená, že nezvažuje širší pracovní postup DevOps, který může zahrnovat až do produkčního nasazení, a zaměřuje se pouze na vývojovou práci provedenou v počítači vývojáře.</span><span class="sxs-lookup"><span data-stu-id="995de-113">The inner-loop workflow means it's not considering the broader DevOps workflow, which can include up to production deployment, and just focuses on the development work done on the developer's computer.</span></span> <span data-ttu-id="995de-114">Počáteční kroky k nastavení prostředí nejsou zahrnuty, protože tyto kroky se provádí pouze jednou.</span><span class="sxs-lookup"><span data-stu-id="995de-114">The initial steps to set up the environment aren't included, since those steps are done only once.</span></span>

<span data-ttu-id="995de-115">Aplikace se skládá z vlastních služeb a další knihovny (závislosti).</span><span class="sxs-lookup"><span data-stu-id="995de-115">An application is composed of your own services plus additional libraries (dependencies).</span></span> <span data-ttu-id="995de-116">Následují základní kroky, které obvykle provedete při vytváření aplikace Dockeru, jak je znázorněno na obrázku 5-1.</span><span class="sxs-lookup"><span data-stu-id="995de-116">The following are the basic steps you usually take when building a Docker application, as illustrated in Figure 5-1.</span></span>

:::image type="complex" source="./media/docker-app-development-workflow/life-cycle-containerized-apps-docker-cli.png" alt-text="Diagram znázorňující 7 kroků potřebných k vytvoření kontejnerizované aplikace.":::
<span data-ttu-id="995de-118">Proces vývoje pro aplikace Docker: 1 - Kód vaší aplikace, 2 - Zápis Dockerfile/s, 3 - Vytvoření bitových kopií definovaných na Dockerfile/s, 4 - (volitelné) Compose služby v docker-compose.yml souboru, 5 - Spustit kontejner nebo docker-compose aplikace, 6 - Test aplikace nebo mikroslužeb, 7 - Push to repo a opakovat.</span><span class="sxs-lookup"><span data-stu-id="995de-118">The development process for Docker apps: 1 - Code your App, 2 - Write Dockerfile/s, 3 - Create images defined at Dockerfile/s, 4 - (optional) Compose services in the docker-compose.yml file, 5 - Run container or docker-compose app, 6 - Test your app or microservices, 7 - Push to repo and repeat.</span></span>
:::image-end:::

<span data-ttu-id="995de-119">**Obrázek 5-1.**</span><span class="sxs-lookup"><span data-stu-id="995de-119">**Figure 5-1.**</span></span> <span data-ttu-id="995de-120">Podrobný pracovní postup pro vývoj kontejnerizovaných aplikací Dockeru</span><span class="sxs-lookup"><span data-stu-id="995de-120">Step-by-step workflow for developing Docker containerized apps</span></span>

<span data-ttu-id="995de-121">V této části je celý tento proces podrobně popsán a každý důležitý krok je vysvětlen zaměřením na prostředí sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="995de-121">In this section, this whole process is detailed and every major step is explained by focusing on a Visual Studio environment.</span></span>

<span data-ttu-id="995de-122">Pokud používáte přístup k vývoji editoru a rozhraní CLI (například Visual Studio Code plus Docker CLI v macOS nebo Windows), musíte znát každý krok, obecně podrobněji, než když používáte Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="995de-122">When you're using an editor/CLI development approach (for example, Visual Studio Code plus Docker CLI on macOS or Windows), you need to know every step, generally in more detail than if you're using Visual Studio.</span></span> <span data-ttu-id="995de-123">Další informace o práci v prostředí rozhraní pro nastavení rozhraní se křidýlku najdete v tématu životní [cyklus aplikací Containerized Docker u e-knihy Containerized Docker Application s platformami a nástroji microsoftu](https://aka.ms/dockerlifecycleebook/).</span><span class="sxs-lookup"><span data-stu-id="995de-123">For more information about working in a CLI environment, see the e-book [Containerized Docker Application lifecycle with Microsoft Platforms and Tools](https://aka.ms/dockerlifecycleebook/).</span></span>

<span data-ttu-id="995de-124">Když používáte Visual Studio 2019, mnoho z těchto kroků jsou zpracovány za vás, což výrazně zvyšuje vaši produktivitu.</span><span class="sxs-lookup"><span data-stu-id="995de-124">When you're using Visual Studio 2019, many of those steps are handled for you, which dramatically improves your productivity.</span></span> <span data-ttu-id="995de-125">To platí zejména v případě, že používáte Visual Studio 2019 a cílení na aplikace s více kontejnery.</span><span class="sxs-lookup"><span data-stu-id="995de-125">This is especially true when you're using Visual Studio 2019 and targeting multi-container applications.</span></span> <span data-ttu-id="995de-126">Například s jedním kliknutím myši, Visual `Dockerfile` `docker-compose.yml` Studio přidá a soubor do vašich projektů s konfigurací pro vaši aplikaci.</span><span class="sxs-lookup"><span data-stu-id="995de-126">For instance, with just one mouse click, Visual Studio adds the `Dockerfile` and `docker-compose.yml` file to your projects with the configuration for your application.</span></span> <span data-ttu-id="995de-127">Když spustíte aplikaci v sadě Visual Studio, vytvoří image Dockeru a spustí aplikaci s více kontejnery přímo v Dockeru; dokonce umožňuje ladit několik kontejnerů najednou.</span><span class="sxs-lookup"><span data-stu-id="995de-127">When you run the application in Visual Studio, it builds the Docker image and runs the multi-container application directly in Docker; it even allows you to debug several containers at once.</span></span> <span data-ttu-id="995de-128">Tyto funkce zvýší rychlost vašeho vývoje.</span><span class="sxs-lookup"><span data-stu-id="995de-128">These features will boost your development speed.</span></span>

<span data-ttu-id="995de-129">Ale jen proto, že Visual Studio dělá tyto kroky automatické neznamená, že nepotřebujete vědět, co se děje pod docker.</span><span class="sxs-lookup"><span data-stu-id="995de-129">However, just because Visual Studio makes those steps automatic doesn't mean that you don't need to know what's going on underneath with Docker.</span></span> <span data-ttu-id="995de-130">Proto následující pokyny podrobnosti každý krok.</span><span class="sxs-lookup"><span data-stu-id="995de-130">Therefore, the following guidance details every step.</span></span>

![Obrázek kroku 1.](./media/docker-app-development-workflow/step-1-code-your-app.png)

## <a name="step-1-start-coding-and-create-your-initial-application-or-service-baseline"></a><span data-ttu-id="995de-132">Krok 1.</span><span class="sxs-lookup"><span data-stu-id="995de-132">Step 1.</span></span> <span data-ttu-id="995de-133">Spuštění kódování a vytvoření počátečního směrného plánu aplikace nebo služby</span><span class="sxs-lookup"><span data-stu-id="995de-133">Start coding and create your initial application or service baseline</span></span>

<span data-ttu-id="995de-134">Vývoj aplikace Dockeru je podobný způsobu vývoje aplikace bez Dockeru.</span><span class="sxs-lookup"><span data-stu-id="995de-134">Developing a Docker application is similar to the way you develop an application without Docker.</span></span> <span data-ttu-id="995de-135">Rozdíl je v tom, že při vývoji pro Docker nasazujete a testujete aplikace nebo služby spuštěné v kontejnerech Dockeru ve vašem místním prostředí (buď nastavení virtuálního počítače s Linuxem dockerem, nebo přímo Windows, pokud používáte kontejnery Windows).</span><span class="sxs-lookup"><span data-stu-id="995de-135">The difference is that while developing for Docker, you're deploying and testing your application or services running within Docker containers in your local environment (either a Linux VM setup by Docker or directly Windows if using Windows Containers).</span></span>

### <a name="set-up-your-local-environment-with-visual-studio"></a><span data-ttu-id="995de-136">Nastavení místního prostředí pomocí sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="995de-136">Set up your local environment with Visual Studio</span></span>

<span data-ttu-id="995de-137">Chcete-li začít, ujistěte se, že máte nainstalovanou [dockerovou verzi Community Edition (CE)](https://docs.docker.com/docker-for-windows/) pro systém Windows, jak je vysvětleno v následujících pokynech:</span><span class="sxs-lookup"><span data-stu-id="995de-137">To begin, make sure you have [Docker Community Edition (CE)](https://docs.docker.com/docker-for-windows/) for Windows installed, as explained in the following instructions:</span></span>

[<span data-ttu-id="995de-138">Začínáme s Dockerem CE pro Windows</span><span class="sxs-lookup"><span data-stu-id="995de-138">Get started with Docker CE for Windows</span></span>](https://docs.docker.com/docker-for-windows/)

<span data-ttu-id="995de-139">Kromě toho potřebujete Visual Studio 2019 verze 16.4 nebo novější, s nainstalovanou **úlohou pro vývoj napříč platformami .NET Core,** jak je znázorněno na obrázku 5-2.</span><span class="sxs-lookup"><span data-stu-id="995de-139">In addition, you need Visual Studio 2019 version 16.4 or later, with the **.NET Core cross-platform development** workload installed, as shown in Figure 5-2.</span></span>

![Snímek obrazovky s výběrem vývoje napříč platformami .NET Core](./media/docker-app-development-workflow/dotnet-core-cross-platform-development.png)

<span data-ttu-id="995de-141">**Obrázek 5-2**.</span><span class="sxs-lookup"><span data-stu-id="995de-141">**Figure 5-2**.</span></span> <span data-ttu-id="995de-142">Výběr **úlohy vývoje napříč platformami .NET Core** během instalace Visual Studia 2019</span><span class="sxs-lookup"><span data-stu-id="995de-142">Selecting the **.NET Core cross-platform development** workload during Visual Studio 2019 setup</span></span>

<span data-ttu-id="995de-143">Můžete začít kódovat aplikaci ve formátu plain .NET (obvykle v .NET Core, pokud plánujete používat kontejnery) ještě před povolením Dockeru ve vaší aplikaci a nasazením a testováním v Dockeru.</span><span class="sxs-lookup"><span data-stu-id="995de-143">You can start coding your application in plain .NET (usually in .NET Core if you're planning to use containers) even before enabling Docker in your application and deploying and testing in Docker.</span></span> <span data-ttu-id="995de-144">Doporučujeme však začít pracovat na Dockeru co nejdříve, protože to bude skutečné prostředí a všechny problémy mohou být zjištěny co nejdříve.</span><span class="sxs-lookup"><span data-stu-id="995de-144">However, it is recommended that you start working on Docker as soon as possible, because that will be the real environment and any issues can be discovered as soon as possible.</span></span> <span data-ttu-id="995de-145">To je doporučeno, protože Visual Studio umožňuje tak snadno pracovat s Dockeru, že se téměř cítí transparentní – nejlepší příklad při ladění aplikací s více kontejnery z Visual Studia.</span><span class="sxs-lookup"><span data-stu-id="995de-145">This is encouraged because Visual Studio makes it so easy to work with Docker that it almost feels transparent—the best example when debugging multi-container applications from Visual Studio.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="995de-146">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="995de-146">Additional resources</span></span>

- <span data-ttu-id="995de-147">**Začínáme s Dockerem CE pro Windows** </span><span class="sxs-lookup"><span data-stu-id="995de-147">**Get started with Docker CE for Windows** </span></span>\
  <https://docs.docker.com/docker-for-windows/>

- <span data-ttu-id="995de-148">**Visual Studio 2019** </span><span class="sxs-lookup"><span data-stu-id="995de-148">**Visual Studio 2019** </span></span>\
  [https://visualstudio.microsoft.com/downloads/](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)

![Obrázek kroku 2.](./media/docker-app-development-workflow/step-2-write-dockerfile.png)

## <a name="step-2-create-a-dockerfile-related-to-an-existing-net-base-image"></a><span data-ttu-id="995de-150">Krok 2.</span><span class="sxs-lookup"><span data-stu-id="995de-150">Step 2.</span></span> <span data-ttu-id="995de-151">Vytvoření souboru Dockerfile souvisejícího s existující základní bitovou bitovou kopii rozhraní .NET</span><span class="sxs-lookup"><span data-stu-id="995de-151">Create a Dockerfile related to an existing .NET base image</span></span>

<span data-ttu-id="995de-152">Potřebujete Dockerfile pro každou vlastní image, kterou chcete vytvořit; potřebujete také Dockerfile pro každý kontejner, který má být nasazen, ať už se nasadíte automaticky z Visual Studia nebo ručně pomocí Cli Dockeru (docker run a docker-compose příkazy).</span><span class="sxs-lookup"><span data-stu-id="995de-152">You need a Dockerfile for each custom image you want to build; you also need a Dockerfile for each container to be deployed, whether you deploy automatically from Visual Studio or manually using the Docker CLI (docker run and docker-compose commands).</span></span> <span data-ttu-id="995de-153">Pokud vaše aplikace obsahuje jednu vlastní službu, budete potřebovat jeden Dockerfile.</span><span class="sxs-lookup"><span data-stu-id="995de-153">If your application contains a single custom service, you need a single Dockerfile.</span></span> <span data-ttu-id="995de-154">Pokud vaše aplikace obsahuje více služeb (jako v architektuře mikroslužeb), budete potřebovat jeden Dockerfile pro každou službu.</span><span class="sxs-lookup"><span data-stu-id="995de-154">If your application contains multiple services (as in a microservices architecture), you need one Dockerfile for each service.</span></span>

<span data-ttu-id="995de-155">Soubor Dockerfile je umístěn v kořenové složce aplikace nebo služby.</span><span class="sxs-lookup"><span data-stu-id="995de-155">The Dockerfile is placed in the root folder of your application or service.</span></span> <span data-ttu-id="995de-156">Obsahuje příkazy, které říkají Dockeru, jak nastavit a spustit aplikaci nebo službu v kontejneru.</span><span class="sxs-lookup"><span data-stu-id="995de-156">It contains the commands that tell Docker how to set up and run your application or service in a container.</span></span> <span data-ttu-id="995de-157">Můžete ručně vytvořit Dockerfile v kódu a přidat jej do projektu spolu s vaše .NET závislosti.</span><span class="sxs-lookup"><span data-stu-id="995de-157">You can manually create a Dockerfile in code and add it to your project along with your .NET dependencies.</span></span>

<span data-ttu-id="995de-158">S Visual Studio a jeho nástroje pro Docker, tato úloha vyžaduje pouze několik kliknutí myší.</span><span class="sxs-lookup"><span data-stu-id="995de-158">With Visual Studio and its tools for Docker, this task requires only a few mouse clicks.</span></span> <span data-ttu-id="995de-159">Když vytvoříte nový projekt v Sadě Visual Studio 2019, je k dispozici možnost s názvem **Povolit podporu Dockeru**, jak je znázorněno na obrázku 5-3.</span><span class="sxs-lookup"><span data-stu-id="995de-159">When you create a new project in Visual Studio 2019, there's an option named **Enable Docker Support**, as shown in Figure 5-3.</span></span>

![Snímek obrazovky s zaškrtnutím políčka Povolit podporu Dockeru](./media/docker-app-development-workflow/enable-docker-support-check-box.png)

<span data-ttu-id="995de-161">**Obrázek 5-3**.</span><span class="sxs-lookup"><span data-stu-id="995de-161">**Figure 5-3**.</span></span> <span data-ttu-id="995de-162">Povolení podpory Dockeru při vytváření nového projektu ASP.NET Core ve Visual Studiu 2019</span><span class="sxs-lookup"><span data-stu-id="995de-162">Enabling Docker Support when creating a new ASP.NET Core project in Visual Studio 2019</span></span>

<span data-ttu-id="995de-163">Podporu Dockeru můžete povolit také u existujícího projektu webové aplikace ASP.NET Core tak, že kliknete pravým tlačítkem myši na projekt v **Průzkumníku řešení** a vyberete **přidat** > **podporu Dockeru...**, jak je znázorněno na obrázku 5-4.</span><span class="sxs-lookup"><span data-stu-id="995de-163">You can also enable Docker support on an existing ASP.NET Core web app project by right-clicking the project in **Solution Explorer** and selecting **Add** > **Docker Support...**, as shown in Figure 5-4.</span></span>

![Snímek obrazovky s možností Podpora Dockeru v nabídce Přidat](./media/docker-app-development-workflow/add-docker-support-option.png)

<span data-ttu-id="995de-165">**Obrázek 5-4**.</span><span class="sxs-lookup"><span data-stu-id="995de-165">**Figure 5-4**.</span></span> <span data-ttu-id="995de-166">Povolení podpory Dockeru v existujícím projektu Visual Studia 2019</span><span class="sxs-lookup"><span data-stu-id="995de-166">Enabling Docker support in an existing Visual Studio 2019 project</span></span>

<span data-ttu-id="995de-167">Tato akce přidá *Dockerfile* do projektu s požadovanou konfiguraci a je k dispozici pouze na ASP.NET základní projekty.</span><span class="sxs-lookup"><span data-stu-id="995de-167">This action adds a *Dockerfile* to the project with the required configuration, and is only available on ASP.NET Core projects.</span></span>

<span data-ttu-id="995de-168">Podobně visual studio můžete také přidat `docker-compose.yml` soubor pro celé řešení s možností **Přidat > podpora kontejneru Orchestrator...**. V kroku 4 tuto možnost podrobněji prozkoumáme.</span><span class="sxs-lookup"><span data-stu-id="995de-168">In a similar fashion, Visual Studio can also add a `docker-compose.yml` file for the whole solution with the option **Add > Container Orchestrator Support...**. In step 4, we'll explore this option in greater detail.</span></span>

### <a name="using-an-existing-official-net-docker-image"></a><span data-ttu-id="995de-169">Použití existující oficiální bitové kopie .NET Docker</span><span class="sxs-lookup"><span data-stu-id="995de-169">Using an existing official .NET Docker image</span></span>

<span data-ttu-id="995de-170">Obvykle vytvoříte vlastní image pro váš kontejner nad základní image, kterou získáte z oficiálního úložiště, jako je registr [Docker Hub.](https://hub.docker.com/)</span><span class="sxs-lookup"><span data-stu-id="995de-170">You usually build a custom image for your container on top of a base image you get from an official repository like the [Docker Hub](https://hub.docker.com/) registry.</span></span> <span data-ttu-id="995de-171">To je přesně to, co se stane pod kryty, když povolíte podporu Dockeru v sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="995de-171">That is precisely what happens under the covers when you enable Docker support in Visual Studio.</span></span> <span data-ttu-id="995de-172">Soubor Dockerfile bude `dotnet/core/aspnet` používat existující image.</span><span class="sxs-lookup"><span data-stu-id="995de-172">Your Dockerfile will use an existing `dotnet/core/aspnet` image.</span></span>

<span data-ttu-id="995de-173">Dříve jsme vysvětlili, které image dockeru a repo můžete použít, v závislosti na rámci a operačního rozhraní, které jste si vybrali.</span><span class="sxs-lookup"><span data-stu-id="995de-173">Earlier we explained which Docker images and repos you can use, depending on the framework and OS you have chosen.</span></span> <span data-ttu-id="995de-174">Například, pokud chcete použít ASP.NET Core (Linux nebo Windows), bitová kopie, která má být používána, je `mcr.microsoft.com/dotnet/core/aspnet:3.1`.</span><span class="sxs-lookup"><span data-stu-id="995de-174">For instance, if you want to use ASP.NET Core (Linux or Windows), the image to use is `mcr.microsoft.com/dotnet/core/aspnet:3.1`.</span></span> <span data-ttu-id="995de-175">Proto stačí zadat, jakou základní image Dockeru budete používat pro kontejner.</span><span class="sxs-lookup"><span data-stu-id="995de-175">Therefore, you just need to specify what base Docker image you will use for your container.</span></span> <span data-ttu-id="995de-176">Můžete to provést `FROM mcr.microsoft.com/dotnet/core/aspnet:3.1` přidáním do souboru Dockerfile.</span><span class="sxs-lookup"><span data-stu-id="995de-176">You do that by adding `FROM mcr.microsoft.com/dotnet/core/aspnet:3.1` to your Dockerfile.</span></span> <span data-ttu-id="995de-177">To bude automaticky provedeno visual studio, ale pokud byste měli aktualizovat verzi, aktualizovat tuto hodnotu.</span><span class="sxs-lookup"><span data-stu-id="995de-177">This will be automatically performed by Visual Studio, but if you were to update the version, you update this value.</span></span>

<span data-ttu-id="995de-178">Použití oficiálního úložiště bitových údajů .NET z Docker Hubu s číslem verze zajišťuje, že stejné funkce jazyka jsou k dispozici na všech počítačích (včetně vývoje, testování a výroby).</span><span class="sxs-lookup"><span data-stu-id="995de-178">Using an official .NET image repository from Docker Hub with a version number ensures that the same language features are available on all machines (including development, testing, and production).</span></span>

<span data-ttu-id="995de-179">Následující příklad ukazuje ukázkový soubor Dockerfile pro kontejner ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="995de-179">The following example shows a sample Dockerfile for an ASP.NET Core container.</span></span>

```Dockerfile
FROM mcr.microsoft.com/dotnet/core/aspnet:3.1
ARG source
WORKDIR /app
EXPOSE 80
COPY ${source:-obj/Docker/publish} .
ENTRYPOINT ["dotnet", " MySingleContainerWebApp.dll "]
```

<span data-ttu-id="995de-180">V tomto případě je obraz založen na verzi 3.1 oficiálního ASP.NET image Core Docker (multi-arch pro Linux a Windows).</span><span class="sxs-lookup"><span data-stu-id="995de-180">In this case, the image is based on version 3.1 of the official ASP.NET Core Docker image (multi-arch for Linux and Windows).</span></span> <span data-ttu-id="995de-181">Toto je `FROM mcr.microsoft.com/dotnet/core/aspnet:3.1`nastavení .</span><span class="sxs-lookup"><span data-stu-id="995de-181">This is the setting `FROM mcr.microsoft.com/dotnet/core/aspnet:3.1`.</span></span> <span data-ttu-id="995de-182">(Další informace o této základní bitové kopii naleznete na stránce [.NET Core Docker Image.)](https://hub.docker.com/_/microsoft-dotnet-core/) V Dockerfile, musíte také pokyn Docker poslouchat na portu TCP, který budete používat za běhu (v tomto případě port 80, jak je nakonfigurován s nastavením EXPOSE).</span><span class="sxs-lookup"><span data-stu-id="995de-182">(For more information about this base image, see the [.NET Core Docker Image](https://hub.docker.com/_/microsoft-dotnet-core/) page.) In the Dockerfile, you also need to instruct Docker to listen on the TCP port you will use at runtime (in this case, port 80, as configured with the EXPOSE setting).</span></span>

<span data-ttu-id="995de-183">Můžete zadat další nastavení konfigurace v Dockerfile, v závislosti na jazyku a rozhraní, které používáte.</span><span class="sxs-lookup"><span data-stu-id="995de-183">You can specify additional configuration settings in the Dockerfile, depending on the language and framework you're using.</span></span> <span data-ttu-id="995de-184">Například řádek ENTRYPOINT `["dotnet", "MySingleContainerWebApp.dll"]` s říká Docker spustit aplikaci .NET Core.</span><span class="sxs-lookup"><span data-stu-id="995de-184">For instance, the ENTRYPOINT line with `["dotnet", "MySingleContainerWebApp.dll"]` tells Docker to run a .NET Core application.</span></span> <span data-ttu-id="995de-185">Pokud používáte sadu SDK a rozhraní .NET Core CLI (dotnet CLI) k sestavení a spuštění aplikace .NET, bude toto nastavení jiné.</span><span class="sxs-lookup"><span data-stu-id="995de-185">If you're using the SDK and the .NET Core CLI (dotnet CLI) to build and run the .NET application, this setting would be different.</span></span> <span data-ttu-id="995de-186">Pointa je, že entrypoint řádek a další nastavení se bude lišit v závislosti na jazyku a platformě, kterou zvolíte pro vaši aplikaci.</span><span class="sxs-lookup"><span data-stu-id="995de-186">The bottom line is that the ENTRYPOINT line and other settings will be different depending on the language and platform you choose for your application.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="995de-187">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="995de-187">Additional resources</span></span>

- <span data-ttu-id="995de-188">**Vytváření imitace Dockeru pro základní aplikace .NET** </span><span class="sxs-lookup"><span data-stu-id="995de-188">**Building Docker Images for .NET Core Applications** </span></span>\
  [https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images](/aspnet/core/host-and-deploy/docker/building-net-docker-images)

- <span data-ttu-id="995de-189">**Vytvořte si vlastní image**.</span><span class="sxs-lookup"><span data-stu-id="995de-189">**Build your own image**.</span></span> <span data-ttu-id="995de-190">V oficiální dokumentaci dockeru.</span><span class="sxs-lookup"><span data-stu-id="995de-190">In the official Docker documentation.</span></span>\
  <https://docs.docker.com/engine/tutorials/dockerimages/>

- <span data-ttu-id="995de-191">**Udržování aktuálního stavu s bitovými kopiemi kontejnerů .NET** </span><span class="sxs-lookup"><span data-stu-id="995de-191">**Staying up-to-date with .NET Container Images** </span></span>\
  <https://devblogs.microsoft.com/dotnet/staying-up-to-date-with-net-container-images/>

- <span data-ttu-id="995de-192">**Použití rozhraní .NET a dockeru společně – aktualizace DockerConu 2018** </span><span class="sxs-lookup"><span data-stu-id="995de-192">**Using .NET and Docker Together - DockerCon 2018 Update** </span></span>\
  <https://devblogs.microsoft.com/dotnet/using-net-and-docker-together-dockercon-2018-update/>

### <a name="using-multi-arch-image-repositories"></a><span data-ttu-id="995de-193">Použití víceobloukových obrazových úložišť</span><span class="sxs-lookup"><span data-stu-id="995de-193">Using multi-arch image repositories</span></span>

<span data-ttu-id="995de-194">Jediné repo může obsahovat varianty platformy, jako je například bitová kopie Linuxu a bitová kopie systému Windows.</span><span class="sxs-lookup"><span data-stu-id="995de-194">A single repo can contain platform variants, such as a Linux image and a Windows image.</span></span> <span data-ttu-id="995de-195">Tato funkce umožňuje dodavatelům, jako je Microsoft (tvůrci základních obrázků), vytvořit jeden repo, který by pokrýval více platforem (tedy Linux a Windows).</span><span class="sxs-lookup"><span data-stu-id="995de-195">This feature allows vendors like Microsoft (base image creators) to create a single repo to cover multiple platforms (that is Linux and Windows).</span></span> <span data-ttu-id="995de-196">Například úložiště [dotnet/core,](https://hub.docker.com/_/microsoft-dotnet-core/) které je k dispozici v registru Docker Hub, poskytuje podporu pro Linux a Windows Nano Server pomocí stejného názvu úložiště.</span><span class="sxs-lookup"><span data-stu-id="995de-196">For example, the [dotnet/core](https://hub.docker.com/_/microsoft-dotnet-core/) repository available in the Docker Hub registry provides support for Linux and Windows Nano Server by using the same repo name.</span></span>

<span data-ttu-id="995de-197">Pokud zadáte značku, cílení na platformu, která je explicitní jako v následujících případech:</span><span class="sxs-lookup"><span data-stu-id="995de-197">If you specify a tag, targeting a platform that is explicit like in the following cases:</span></span>

- `mcr.microsoft.com/dotnet/core/aspnet:3.1-buster-slim` \
  <span data-ttu-id="995de-198">Cíle: .NET Core 3.1 runtime-only na Linuxu</span><span class="sxs-lookup"><span data-stu-id="995de-198">Targets: .NET Core 3.1 runtime-only on Linux</span></span>

- `mcr.microsoft.com/dotnet/core/aspnet:3.1-nanoserver-1909` \
  <span data-ttu-id="995de-199">Cíle: Pouze runtime .NET Core 3.1 na Windows Nano Server</span><span class="sxs-lookup"><span data-stu-id="995de-199">Targets: .NET Core 3.1 runtime-only on Windows Nano Server</span></span>

<span data-ttu-id="995de-200">Pokud však zadáte stejný název obrázku, a to i se stejnou `aspnet` značkou, budou víceobloukové obrazy (jako obrázek) používat verzi Linuxu nebo Windows v závislosti na hostitelském operačním systému Dockeru, který nasazujete, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="995de-200">But, if you specify the same image name, even with the same tag, the multi-arch images (like the `aspnet` image) will use the Linux or Windows version depending on the Docker host OS you're deploying, as shown in the following example:</span></span>

- `mcr.microsoft.com/dotnet/core/aspnet:3.1` \
  <span data-ttu-id="995de-201">Multi-arch: .NET Core 3.1 runtime-only na Linuxu nebo Windows Nano Server v závislosti na dockeru hostitelského operačního systému</span><span class="sxs-lookup"><span data-stu-id="995de-201">Multi-arch: .NET Core 3.1 runtime-only on Linux or Windows Nano Server depending on the Docker host OS</span></span>

<span data-ttu-id="995de-202">Tímto způsobem, když vytáhnete obrázek z hostitele systému Windows, vytáhne variantu systému Windows a vytažení stejného názvu obrázku z hostitele Linuxu vytáhne variantu Linuxu.</span><span class="sxs-lookup"><span data-stu-id="995de-202">This way, when you pull an image from a Windows host, it will pull the Windows variant, and pulling the same image name from a Linux host will pull the Linux variant.</span></span>

### <a name="multi-stage-builds-in-dockerfile"></a><span data-ttu-id="995de-203">Vícestupňové sestavení v Dockerfile</span><span class="sxs-lookup"><span data-stu-id="995de-203">Multi-stage builds in Dockerfile</span></span>

<span data-ttu-id="995de-204">Dockerfile je podobný dávkový skript.</span><span class="sxs-lookup"><span data-stu-id="995de-204">The Dockerfile is similar to a batch script.</span></span> <span data-ttu-id="995de-205">Podobně jako byste museli nastavit počítač z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="995de-205">Similar to what you would do if you had to set up the machine from the command line.</span></span>

<span data-ttu-id="995de-206">Začíná se základním obrazem, který nastavuje počáteční kontext, je to jako spouštěcí souborový systém, který sedí nad hostitelským osem.</span><span class="sxs-lookup"><span data-stu-id="995de-206">It starts with a base image that sets up the initial context, it's like the startup filesystem, that sits on top of the host OS.</span></span> <span data-ttu-id="995de-207">Není to Operační os, ale můžete si myslet, že jako "" OS uvnitř kontejneru.</span><span class="sxs-lookup"><span data-stu-id="995de-207">It's not an OS, but you can think of it like "the" OS inside the container.</span></span>

<span data-ttu-id="995de-208">Spuštění každého příkazového řádku vytvoří novou vrstvu v souborovém systému se změnami z předchozího, takže v kombinaci vytvoří výsledný souborový systém.</span><span class="sxs-lookup"><span data-stu-id="995de-208">The execution of every command line creates a new layer on the filesystem with the changes from the previous one, so that, when combined, produce the resulting filesystem.</span></span>

<span data-ttu-id="995de-209">Vzhledem k tomu, že každá nová vrstva "spočívá" nad předchozí a výsledná velikost obrázku se zvyšuje s každým příkazem, obrázky mohou být velmi velké, pokud musí zahrnovat například sdk potřebnou k vytvoření a publikování aplikace.</span><span class="sxs-lookup"><span data-stu-id="995de-209">Since every new layer "rests" on top of the previous one and the resulting image size increases with every command, images can get very large if they have to include, for example, the SDK needed to build and publish an application.</span></span>

<span data-ttu-id="995de-210">To je místo, kde multi-fáze staví dostat do pozemku (od Docker 17,05 a vyšší), aby se jejich kouzlo.</span><span class="sxs-lookup"><span data-stu-id="995de-210">This is where multi-stage builds get into the plot (from Docker 17.05 and higher) to do their magic.</span></span>

<span data-ttu-id="995de-211">Základní myšlenkou je, že proces provádění dockerových souborů můžete oddělit ve fázích, kde fáze je počáteční obrázek následovaný jedním nebo více příkazy a poslední fáze určuje konečnou velikost obrázku.</span><span class="sxs-lookup"><span data-stu-id="995de-211">The core idea is that you can separate the Dockerfile execution process in stages, where a stage is an initial image followed by one or more commands, and the last stage determines the final image size.</span></span>

<span data-ttu-id="995de-212">Stručně řečeno, vícestupňové sestavení umožňují rozdělení tvorby v různých "fázích" a pak sestavit konečný obraz s pouze příslušné adresáře z mezilehlých fází.</span><span class="sxs-lookup"><span data-stu-id="995de-212">In short, multi-stage builds allow splitting the creation in different "phases" and then assemble the final image taking only the relevant directories from the intermediate stages.</span></span> <span data-ttu-id="995de-213">Obecná strategie použití této funkce je:</span><span class="sxs-lookup"><span data-stu-id="995de-213">The general strategy to use this feature is:</span></span>

1. <span data-ttu-id="995de-214">Použijte základní bitovou kopii sady SDK (nezáleží na tom, jak velký), se vším, co je potřeba k sestavení a publikování aplikace do složky a pak</span><span class="sxs-lookup"><span data-stu-id="995de-214">Use a base SDK image (doesn't matter how large), with everything needed to build and publish the application to a folder and then</span></span>

2. <span data-ttu-id="995de-215">Použijte základní, malý obrázek pouze za běhu a zkopírujte složku publikování z předchozí fáze k vytvoření malého konečného obrázku.</span><span class="sxs-lookup"><span data-stu-id="995de-215">Use a base, small, runtime-only image and copy the publishing folder from the previous stage to produce a small final image.</span></span>

<span data-ttu-id="995de-216">Pravděpodobně nejlepší způsob, jak pochopit vícestupňový prochází Dockerfile podrobně, řádek po řádku, takže začněme s počáteční Dockerfile vytvořené Visual Studio při přidávání podpory Docker u projektu a dostane se do některé optimalizace později.</span><span class="sxs-lookup"><span data-stu-id="995de-216">Probably the best way to understand multi-stage is going through a Dockerfile in detail, line by line, so let's begin with the initial Dockerfile created by Visual Studio when adding Docker support to a project and will get into some optimizations later.</span></span>

<span data-ttu-id="995de-217">Počáteční Dockerfile může vypadat nějak takto:</span><span class="sxs-lookup"><span data-stu-id="995de-217">The initial Dockerfile might look something like this:</span></span>

```Dockerfile
 1  FROM mcr.microsoft.com/dotnet/core/aspnet:3.1 AS base
 2  WORKDIR /app
 3  EXPOSE 80
 4
 5  FROM mcr.microsoft.com/dotnet/core/sdk:3.1 AS build
 6  WORKDIR /src
 7  COPY src/Services/Catalog/Catalog.API/Catalog.API.csproj …
 8  COPY src/BuildingBlocks/HealthChecks/src/Microsoft.AspNetCore.HealthChecks …
 9  COPY src/BuildingBlocks/HealthChecks/src/Microsoft.Extensions.HealthChecks …
10  COPY src/BuildingBlocks/EventBus/IntegrationEventLogEF/ …
11  COPY src/BuildingBlocks/EventBus/EventBus/EventBus.csproj …
12  COPY src/BuildingBlocks/EventBus/EventBusRabbitMQ/EventBusRabbitMQ.csproj …
13  COPY src/BuildingBlocks/EventBus/EventBusServiceBus/EventBusServiceBus.csproj …
14  COPY src/BuildingBlocks/WebHostCustomization/WebHost.Customization …
15  COPY src/BuildingBlocks/HealthChecks/src/Microsoft.Extensions …
16  COPY src/BuildingBlocks/HealthChecks/src/Microsoft.Extensions …
17  RUN dotnet restore src/Services/Catalog/Catalog.API/Catalog.API.csproj
18  COPY . .
19  WORKDIR /src/src/Services/Catalog/Catalog.API
20  RUN dotnet build Catalog.API.csproj -c Release -o /app
21
22  FROM build AS publish
23  RUN dotnet publish Catalog.API.csproj -c Release -o /app
24
25  FROM base AS final
26  WORKDIR /app
27  COPY --from=publish /app .
28  ENTRYPOINT ["dotnet", "Catalog.API.dll"]
```

<span data-ttu-id="995de-218">A toto jsou detaily, řádek po řádku:</span><span class="sxs-lookup"><span data-stu-id="995de-218">And these are the details, line by line:</span></span>

- <span data-ttu-id="995de-219">**#1 čáry:** Začněte fázi se základním obrázkem pouze "malý" runtime, nazvěme ji **základnou** pro referenci.</span><span class="sxs-lookup"><span data-stu-id="995de-219">**Line #1:** Begin a stage with a "small" runtime-only base image, call it **base** for reference.</span></span>

- <span data-ttu-id="995de-220">**Linka #2:** Vytvořte adresář **/app** v obraze.</span><span class="sxs-lookup"><span data-stu-id="995de-220">**Line #2:** Create the **/app** directory in the image.</span></span>

- <span data-ttu-id="995de-221">**#3 čáry:** Vystavit port **80**.</span><span class="sxs-lookup"><span data-stu-id="995de-221">**Line #3:** Expose port **80**.</span></span>

- <span data-ttu-id="995de-222">**Linka #5:** Začněte novou fázi s "velkým" obrazem pro vytváření/publikování.</span><span class="sxs-lookup"><span data-stu-id="995de-222">**Line #5:** Begin a new stage with the "large" image for building/publishing.</span></span> <span data-ttu-id="995de-223">Nazvěme to **stavět** pro referenci.</span><span class="sxs-lookup"><span data-stu-id="995de-223">Call it **build** for reference.</span></span>

- <span data-ttu-id="995de-224">**Linka #6:** Vytvořte adresář **/src** v obraze.</span><span class="sxs-lookup"><span data-stu-id="995de-224">**Line #6:** Create directory **/src** in the image.</span></span>

- <span data-ttu-id="995de-225">**Linka #7:** Až do řádku 16 zkopírujte odkazované soubory projektu **.csproj,** abyste mohli později obnovit balíčky.</span><span class="sxs-lookup"><span data-stu-id="995de-225">**Line #7:** Up to line 16, copy referenced **.csproj** project files to be able to restore packages later.</span></span>

- <span data-ttu-id="995de-226">**Linka #17:** Obnovení balíčků pro projekt **Catalog.API** a odkazované projekty.</span><span class="sxs-lookup"><span data-stu-id="995de-226">**Line #17:** Restore packages for the **Catalog.API** project and the referenced projects.</span></span>

- <span data-ttu-id="995de-227">**Linka #18:** Zkopírujte **všechny adresářové stromy řešení** (s výjimkou souborů/adresářů zahrnutých v souboru **.dockerignore)** do adresáře **/src** v bitové kopii.</span><span class="sxs-lookup"><span data-stu-id="995de-227">**Line #18:** Copy **all directory tree for the solution** (except the files/directories included in the **.dockerignore** file) to the **/src** directory in the image.</span></span>

- <span data-ttu-id="995de-228">**Linka #19:** Změňte aktuální složku na projekt **Catalog.API.**</span><span class="sxs-lookup"><span data-stu-id="995de-228">**Line #19:** Change the current folder to the **Catalog.API** project.</span></span>

- <span data-ttu-id="995de-229">**#20 čáry:** Vytvořte projekt (a další závislosti projektu) a výstup do adresáře **/app** v bitové kopii.</span><span class="sxs-lookup"><span data-stu-id="995de-229">**Line #20:** Build the project (and other project dependencies) and output to the **/app** directory in the image.</span></span>

- <span data-ttu-id="995de-230">**Linka #22:** Začněte novou fázi pokračovat z sestavení.</span><span class="sxs-lookup"><span data-stu-id="995de-230">**Line #22:** Begin a new stage continuing from the build.</span></span> <span data-ttu-id="995de-231">Nazvěme to **publikovat** pro referenci.</span><span class="sxs-lookup"><span data-stu-id="995de-231">Call it **publish** for reference.</span></span>

- <span data-ttu-id="995de-232">**Linka #23:** Publikujte projekt (a závislosti) a výstup do adresáře **/app** v bitové kopii.</span><span class="sxs-lookup"><span data-stu-id="995de-232">**Line #23:** Publish the project (and dependencies) and output to the **/app** directory in the image.</span></span>

- <span data-ttu-id="995de-233">**#25 čáry:** Začněte novou etapu, která pokračuje od **základny,** a nazvěme ji **konečnou**.</span><span class="sxs-lookup"><span data-stu-id="995de-233">**Line #25:** Begin a new stage continuing from **base** and call it **final**.</span></span>

- <span data-ttu-id="995de-234">**Linka #26:** Změňte aktuální adresář na **/app**.</span><span class="sxs-lookup"><span data-stu-id="995de-234">**Line #26:** Change the current directory to **/app**.</span></span>

- <span data-ttu-id="995de-235">**Linka #27:** Zkopírujte adresář **/app** z **publikování** fáze do aktuálního adresáře.</span><span class="sxs-lookup"><span data-stu-id="995de-235">**Line #27:** Copy the **/app** directory from stage **publish** to the current directory.</span></span>

- <span data-ttu-id="995de-236">**Linka #28:** Definujte příkaz, který chcete spustit při spuštění kontejneru.</span><span class="sxs-lookup"><span data-stu-id="995de-236">**Line #28:** Define the command to run when the container is started.</span></span>

<span data-ttu-id="995de-237">Nyní pojďme prozkoumat některé optimalizace ke zlepšení výkonu celého procesu, který v případě eShopOnContainers znamená asi 22 minut nebo více k vytvoření kompletního řešení v kontejnerech Linuxu.</span><span class="sxs-lookup"><span data-stu-id="995de-237">Now let's explore some optimizations to improve the whole process performance that, in the case of eShopOnContainers, means about 22 minutes or more to build the complete solution in Linux containers.</span></span>

<span data-ttu-id="995de-238">Budete využívat funkce mezipaměti vrstev Dockeru, což je poměrně jednoduché: pokud jsou základní obraz a příkazy stejné jako některé dříve provedené, můžete použít výslednou vrstvu bez nutnosti provádění příkazů, což šetří nějaký čas.</span><span class="sxs-lookup"><span data-stu-id="995de-238">You'll take advantage of Docker's layer cache feature, which is quite simple: if the base image and the commands are the same as some previously executed, it can just use the resulting layer without the need to execute the commands, thus saving some time.</span></span>

<span data-ttu-id="995de-239">Takže se zaměřme na fázi **sestavení,** řádky 5-6 jsou většinou stejné, ale řádky 7-17 se liší pro každou službu z eShopOnContainers, takže musí provést pokaždé, když jste změnili řádky 7-16 na:</span><span class="sxs-lookup"><span data-stu-id="995de-239">So, let's focus on the **build** stage, lines 5-6 are mostly the same, but lines 7-17 are different for every service from eShopOnContainers, so they have to execute every single time, however if you changed lines 7-16 to:</span></span>

```Dockerfile
COPY . .
```

<span data-ttu-id="995de-240">Pak by to bylo stejné pro každou službu, to by zkopírovat celé řešení a vytvoří větší vrstvu, ale:</span><span class="sxs-lookup"><span data-stu-id="995de-240">Then it would be just the same for every service, it would copy the whole solution and would create a larger layer but:</span></span>

1. <span data-ttu-id="995de-241">Proces kopírování by byl proveden pouze poprvé (a při opětovném sestavení, pokud dojde ke změně souboru) a použil by mezipaměť pro všechny ostatní služby a</span><span class="sxs-lookup"><span data-stu-id="995de-241">The copy process would only be executed the first time (and when rebuilding if a file is changed) and would use the cache for all other services and</span></span>

2. <span data-ttu-id="995de-242">Vzhledem k tomu, že větší obraz se vyskytuje v mezilehlé fázi, nemá vliv na konečnou velikost obrazu.</span><span class="sxs-lookup"><span data-stu-id="995de-242">Since the larger image occurs in an intermediate stage it, doesn't affect the final image size.</span></span>

<span data-ttu-id="995de-243">Další významná optimalizace zahrnuje `restore` příkaz spuštěný v řádku 17, který se také liší pro každou službu eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="995de-243">The next significant optimization involves the `restore` command executed in line 17, which is also different for every service of eShopOnContainers.</span></span> <span data-ttu-id="995de-244">Pokud tento řádek změníte na pouze:</span><span class="sxs-lookup"><span data-stu-id="995de-244">If you change that line to just:</span></span>

```Dockerfile
RUN dotnet restore
```

<span data-ttu-id="995de-245">To by obnovit balíčky pro celé řešení, ale pak znovu, to by to jen jednou, místo 15 krát se současnou strategií.</span><span class="sxs-lookup"><span data-stu-id="995de-245">It would restore the packages for the whole solution, but then again, it would do it just once, instead of the 15 times with the current strategy.</span></span>

<span data-ttu-id="995de-246">Však `dotnet restore` pouze spustí, pokud je jeden projekt nebo soubor řešení ve složce, takže dosažení tohoto je trochu složitější a způsob, jak ji vyřešit, aniž by se do příliš mnoho detailů, je toto:</span><span class="sxs-lookup"><span data-stu-id="995de-246">However, `dotnet restore` only runs if there's a single project or solution file in the folder, so achieving this is a bit more complicated and the way to solve it, without getting into too many details, is this:</span></span>

1. <span data-ttu-id="995de-247">Do **.dockerignore**přidejte následující řádky :</span><span class="sxs-lookup"><span data-stu-id="995de-247">Add the following lines to **.dockerignore**:</span></span>

   - <span data-ttu-id="995de-248">`*.sln`, chcete-li ignorovat všechny soubory řešení ve stromu hlavních složek</span><span class="sxs-lookup"><span data-stu-id="995de-248">`*.sln`, to ignore all solution files in the main folder tree</span></span>

   - <span data-ttu-id="995de-249">`!eShopOnContainers-ServicesAndWebApps.sln`, aby zahrnoval pouze tento soubor řešení.</span><span class="sxs-lookup"><span data-stu-id="995de-249">`!eShopOnContainers-ServicesAndWebApps.sln`, to include only this solution file.</span></span>

2. <span data-ttu-id="995de-250">`/ignoreprojectextensions:.dcproj` Zahrňte `dotnet restore`argument do aplikace , takže také ignoruje projekt docker-compose a obnoví pouze balíčky pro řešení eShopOnContainers-ServicesAndWebApps.</span><span class="sxs-lookup"><span data-stu-id="995de-250">Include the `/ignoreprojectextensions:.dcproj` argument to `dotnet restore`, so it also ignores the docker-compose project and only restores the packages for the eShopOnContainers-ServicesAndWebApps solution.</span></span>

<span data-ttu-id="995de-251">Pro konečnou optimalizaci se prostě stane, že řádek 20 je redundantní, protože řádek 23 také vytváří aplikaci a přichází v podstatě hned po řádku 20, takže jde další časově náročný příkaz.</span><span class="sxs-lookup"><span data-stu-id="995de-251">For the final optimization, it just happens that line 20 is redundant, as line 23 also builds the application and comes, in essence, right after line 20, so there goes another time-consuming command.</span></span>

<span data-ttu-id="995de-252">Výsledný soubor je pak:</span><span class="sxs-lookup"><span data-stu-id="995de-252">The resulting file is then:</span></span>

```Dockerfile
 1  FROM mcr.microsoft.com/dotnet/core/aspnet:3.1 AS base
 2  WORKDIR /app
 3  EXPOSE 80
 4
 5  FROM mcr.microsoft.com/dotnet/core/sdk:3.1 AS publish
 6  WORKDIR /src
 7  COPY . .
 8  RUN dotnet restore /ignoreprojectextensions:.dcproj
 9  WORKDIR /src/src/Services/Catalog/Catalog.API
10  RUN dotnet publish Catalog.API.csproj -c Release -o /app
11
12  FROM base AS final
13  WORKDIR /app
14  COPY --from=publish /app
15  ENTRYPOINT ["dotnet", "Catalog.API.dll"]
```

### <a name="creating-your-base-image-from-scratch"></a><span data-ttu-id="995de-253">Vytvoření základního obrázku od začátku</span><span class="sxs-lookup"><span data-stu-id="995de-253">Creating your base image from scratch</span></span>

<span data-ttu-id="995de-254">Můžete vytvořit vlastní základní image Dockeru od začátku.</span><span class="sxs-lookup"><span data-stu-id="995de-254">You can create your own Docker base image from scratch.</span></span> <span data-ttu-id="995de-255">Tento scénář se nedoporučuje pro někoho, kdo začíná s Docker, ale pokud chcete nastavit konkrétní bity vlastní základní image, můžete tak učinit.</span><span class="sxs-lookup"><span data-stu-id="995de-255">This scenario is not recommended for someone who is starting with Docker, but if you want to set the specific bits of your own base image, you can do so.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="995de-256">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="995de-256">Additional resources</span></span>

- <span data-ttu-id="995de-257">**Víceobloukové obrázky .NET Core**.</span><span class="sxs-lookup"><span data-stu-id="995de-257">**Multi-arch .NET Core images**.</span></span>\
  <https://github.com/dotnet/announcements/issues/14>

- <span data-ttu-id="995de-258">**Vytvořte základní bitovou kopii**.</span><span class="sxs-lookup"><span data-stu-id="995de-258">**Create a base image**.</span></span> <span data-ttu-id="995de-259">Oficiální dokumentace dockeru.</span><span class="sxs-lookup"><span data-stu-id="995de-259">Official Docker documentation.</span></span>\
  <https://docs.docker.com/develop/develop-images/baseimages/>

![Obrázek kroku 3.](./media/docker-app-development-workflow/step-3-create-dockerfile-defined-images.png)

## <a name="step-3-create-your-custom-docker-images-and-embed-your-application-or-service-in-them"></a><span data-ttu-id="995de-261">Krok 3.</span><span class="sxs-lookup"><span data-stu-id="995de-261">Step 3.</span></span> <span data-ttu-id="995de-262">Vytvořte si vlastní image Dockeru a vložte do nich aplikaci nebo službu.</span><span class="sxs-lookup"><span data-stu-id="995de-262">Create your custom Docker images and embed your application or service in them</span></span>

<span data-ttu-id="995de-263">Pro každou službu v aplikaci je třeba vytvořit související bitovou kopii.</span><span class="sxs-lookup"><span data-stu-id="995de-263">For each service in your application, you need to create a related image.</span></span> <span data-ttu-id="995de-264">Pokud je vaše aplikace tvořena jedinou službou nebo webovou aplikací, potřebujete pouze jeden obrázek.</span><span class="sxs-lookup"><span data-stu-id="995de-264">If your application is made up of a single service or web application, you just need a single image.</span></span>

<span data-ttu-id="995de-265">Všimněte si, že image Dockeru jsou vytvořeny automaticky pro vás v sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="995de-265">Note that the Docker images are built automatically for you in Visual Studio.</span></span> <span data-ttu-id="995de-266">Následující kroky jsou potřebné pouze pro pracovní postup editoru/rozhraní příkazového příkazu a vysvětleno pro přehlednost o tom, co se děje pod ním.</span><span class="sxs-lookup"><span data-stu-id="995de-266">The following steps are only needed for the editor/CLI workflow and explained for clarity about what happens underneath.</span></span>

<span data-ttu-id="995de-267">Vy, jako vývojář, je třeba vyvíjet a testovat místně, dokud push dokončené funkce nebo změnit systém správy zdrojového kódu (například na GitHub).</span><span class="sxs-lookup"><span data-stu-id="995de-267">You, as a developer, need to develop and test locally until you push a completed feature or change to your source control system (for example, to GitHub).</span></span> <span data-ttu-id="995de-268">To znamená, že je potřeba vytvořit image Dockeru a nasadit kontejnery do místního hostitele Dockeru (Windows nebo virtuální počítač SNI) a spustit, testovat a ladit proti těmto místním kontejnerům.</span><span class="sxs-lookup"><span data-stu-id="995de-268">This means that you need to create the Docker images and deploy containers to a local Docker host (Windows or Linux VM) and run, test, and debug against those local containers.</span></span>

<span data-ttu-id="995de-269">Chcete-li vytvořit vlastní image v místním prostředí pomocí Docker CLI a dockerfile, můžete použít příkaz sestavení dockeru, jako na obrázku 5-5.</span><span class="sxs-lookup"><span data-stu-id="995de-269">To create a custom image in your local environment by using Docker CLI and your Dockerfile, you can use the docker build command, as in Figure 5-5.</span></span>

![Snímek obrazovky zobrazující výstup konzoly příkazu docker build.](./media/docker-app-development-workflow/run-docker-build-command.png)

<span data-ttu-id="995de-271">**Obrázek 5-5**.</span><span class="sxs-lookup"><span data-stu-id="995de-271">**Figure 5-5**.</span></span> <span data-ttu-id="995de-272">Vytvoření vlastní image Dockeru</span><span class="sxs-lookup"><span data-stu-id="995de-272">Creating a custom Docker image</span></span>

<span data-ttu-id="995de-273">Volitelně můžete namísto přímého spuštění sestavení dockeru ze složky projektu nejprve vygenerovat nasaditelnou složku s požadovanými knihovnami a binárními soubory .NET spuštěním `dotnet publish`a potom použít `docker build` příkaz.</span><span class="sxs-lookup"><span data-stu-id="995de-273">Optionally, instead of directly running docker build from the project folder, you can first generate a deployable folder with the required .NET libraries and binaries by running `dotnet publish`, and then use the `docker build` command.</span></span>

<span data-ttu-id="995de-274">Tím vytvoříte image Dockeru `cesardl/netcore-webapi-microservice-docker:first`s názvem .</span><span class="sxs-lookup"><span data-stu-id="995de-274">This will create a Docker image with the name `cesardl/netcore-webapi-microservice-docker:first`.</span></span> <span data-ttu-id="995de-275">V tomto případě : first je značka představující konkrétní verzi.</span><span class="sxs-lookup"><span data-stu-id="995de-275">In this case, :first is a tag representing a specific version.</span></span> <span data-ttu-id="995de-276">Tento krok můžete zopakovat pro každou vlastní bitovou kopii, kterou potřebujete vytvořit pro komponovanou aplikaci Docker.</span><span class="sxs-lookup"><span data-stu-id="995de-276">You can repeat this step for each custom image you need to create for your composed Docker application.</span></span>

<span data-ttu-id="995de-277">Pokud je aplikace vyrobena z více kontejnerů (to znamená, že se `docker-compose up --build` jedná o aplikaci s více kontejnery), můžete také použít příkaz k vytvoření všech souvisejících bitových kopií pomocí jediného příkazu pomocí metadat vystavených v souvisejících souborech docker-compose.yml.</span><span class="sxs-lookup"><span data-stu-id="995de-277">When an application is made of multiple containers (that is, it is a multi-container application), you can also use the `docker-compose up --build` command to build all the related images with a single command by using the metadata exposed in the related docker-compose.yml files.</span></span>

<span data-ttu-id="995de-278">Existující obrázky můžete najít v místním úložišti pomocí příkazu imkdocker, jak je znázorněno na obrázku 5-6.</span><span class="sxs-lookup"><span data-stu-id="995de-278">You can find the existing images in your local repository by using the docker images command, as shown in Figure 5-6.</span></span>

![Konzolový výstup z iobrazů řídicího místa s existujícími obrazy.](./media/docker-app-development-workflow/view-existing-images-with-docker-images.png)

<span data-ttu-id="995de-280">**Obrázek 5-6.**</span><span class="sxs-lookup"><span data-stu-id="995de-280">**Figure 5-6.**</span></span> <span data-ttu-id="995de-281">Zobrazení existujících obrazů pomocí příkazu docker images</span><span class="sxs-lookup"><span data-stu-id="995de-281">Viewing existing images using the docker images command</span></span>

### <a name="creating-docker-images-with-visual-studio"></a><span data-ttu-id="995de-282">Vytváření imitací Dockeru pomocí Sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="995de-282">Creating Docker images with Visual Studio</span></span>

<span data-ttu-id="995de-283">Při použití Visual Studio k vytvoření projektu s podporou Dockeru, není explicitně vytvořit image.</span><span class="sxs-lookup"><span data-stu-id="995de-283">When you use Visual Studio to create a project with Docker support, you don't explicitly create an image.</span></span> <span data-ttu-id="995de-284">Místo toho je obrázek vytvořen pro vás, když stisknete **Klávesu F5** (nebo **Ctrl-F5)** pro spuštění dockerized aplikace nebo služby.</span><span class="sxs-lookup"><span data-stu-id="995de-284">Instead, the image is created for you when you press **F5** (or **Ctrl-F5**) to run the dockerized application or service.</span></span> <span data-ttu-id="995de-285">Tento krok je v sadě Visual Studio automatický a neuvidíte, že k tomu dojde, ale je důležité, abyste věděli, co se děje pod ním.</span><span class="sxs-lookup"><span data-stu-id="995de-285">This step is automatic in Visual Studio and you won't see it happen, but it's important that you know what's going on underneath.</span></span>

![Obrázek volitelného kroku 4.](./media/docker-app-development-workflow/step-4-define-services-docker-compose-yml.png)

## <a name="step-4-define-your-services-in-docker-composeyml-when-building-a-multi-container-docker-application"></a><span data-ttu-id="995de-287">Krok 4.</span><span class="sxs-lookup"><span data-stu-id="995de-287">Step 4.</span></span> <span data-ttu-id="995de-288">Definujte své služby v docker-compose.yml při vytváření aplikace Docker u více kontejnerů</span><span class="sxs-lookup"><span data-stu-id="995de-288">Define your services in docker-compose.yml when building a multi-container Docker application</span></span>

<span data-ttu-id="995de-289">Soubor [docker-compose.yml](https://docs.docker.com/compose/compose-file/) umožňuje definovat sadu souvisejících služeb, které mají být nasazeny jako komponovaná aplikace s příkazy nasazení.</span><span class="sxs-lookup"><span data-stu-id="995de-289">The [docker-compose.yml](https://docs.docker.com/compose/compose-file/) file lets you define a set of related services to be deployed as a composed application with deployment commands.</span></span> <span data-ttu-id="995de-290">Také konfiguruje jeho vztahy závislostí a konfigurace za běhu.</span><span class="sxs-lookup"><span data-stu-id="995de-290">It also configures its dependency relations and run-time configuration.</span></span>

<span data-ttu-id="995de-291">Chcete-li použít soubor docker-compose.yml, musíte vytvořit soubor v hlavní nebo kořenové složce řešení s obsahem podobným obsahu v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="995de-291">To use a docker-compose.yml file, you need to create the file in your main or root solution folder, with content similar to that in the following example:</span></span>

```yml
version: '3.4'

services:

  webmvc:
    image: eshop/web
    environment:
      - CatalogUrl=http://catalog-api
      - OrderingUrl=http://ordering-api
    ports:
      - "80:80"
    depends_on:
      - catalog-api
      - ordering-api

  catalog-api:
    image: eshop/catalog-api
    environment:
      - ConnectionString=Server=sqldata;Port=1433;Database=CatalogDB;…
    ports:
      - "81:80"
    depends_on:
      - sqldata

  ordering-api:
    image: eshop/ordering-api
    environment:
      - ConnectionString=Server=sqldata;Database=OrderingDb;…
    ports:
      - "82:80"
    extra_hosts:
      - "CESARDLBOOKVHD:10.0.75.1"
    depends_on:
      - sqldata

  sqldata:
    image: mssql-server-linux:latest
    environment:
      - SA_PASSWORD=Pass@word
      - ACCEPT_EULA=Y
    ports:
      - "5433:1433"
```

<span data-ttu-id="995de-292">Tento soubor docker-compose.yml je zjednodušená a sloučená verze.</span><span class="sxs-lookup"><span data-stu-id="995de-292">This docker-compose.yml file is a simplified and merged version.</span></span> <span data-ttu-id="995de-293">Obsahuje statická konfigurační data pro každý kontejner (například název vlastní bitové kopie), která je vždy vyžadována, a informace o konfiguraci, které mohou záviset na prostředí nasazení, jako je připojovací řetězec.</span><span class="sxs-lookup"><span data-stu-id="995de-293">It contains static configuration data for each container (like the name of the custom image), which is always required, and configuration information that might depend on the deployment environment, like the connection string.</span></span> <span data-ttu-id="995de-294">V dalších částech se dozvíte, jak rozdělit konfiguraci docker-compose.yml do více souborů docker-compose a přepsat hodnoty v závislosti na prostředí a typu spuštění (ladění nebo vydání).</span><span class="sxs-lookup"><span data-stu-id="995de-294">In later sections, you will learn how to split the docker-compose.yml configuration into multiple docker-compose files and override values depending on the environment and execution type (debug or release).</span></span>

<span data-ttu-id="995de-295">Příklad souboru docker-compose.yml definuje čtyři `webmvc` služby: službu (webovou `basket-api`aplikaci), dvě `sqldata`mikroslužby (`ordering-api` a ) a jeden kontejner zdroje dat , založený na SQL Serveru pro Linux běžícím jako kontejner.</span><span class="sxs-lookup"><span data-stu-id="995de-295">The docker-compose.yml file example defines four services: the `webmvc` service (a web application), two microservices (`ordering-api` and `basket-api`), and one data source container, `sqldata`, based on SQL Server for Linux running as a container.</span></span> <span data-ttu-id="995de-296">Každá služba bude nasazena jako kontejner, takže image Dockeru je vyžadována pro každou.</span><span class="sxs-lookup"><span data-stu-id="995de-296">Each service will be deployed as a container, so a Docker image is required for each.</span></span>

<span data-ttu-id="995de-297">Soubor docker-compose.yml určuje nejen to, jaké kontejnery se používají, ale jak jsou individuálně konfigurovány.</span><span class="sxs-lookup"><span data-stu-id="995de-297">The docker-compose.yml file specifies not only what containers are being used, but how they are individually configured.</span></span> <span data-ttu-id="995de-298">Například definice `webmvc` kontejneru v souboru YML:</span><span class="sxs-lookup"><span data-stu-id="995de-298">For instance, the `webmvc` container definition in the .yml file:</span></span>

- <span data-ttu-id="995de-299">Používá předem sestavenou `eshop/web:latest` bitovou kopii.</span><span class="sxs-lookup"><span data-stu-id="995de-299">Uses a pre-built `eshop/web:latest` image.</span></span> <span data-ttu-id="995de-300">Můžete však také nakonfigurovat bitovou kopii, která má být vytvořena jako součást spuštění docker-compose s další konfigurací založenou na sestavení: části v souboru docker-compose.</span><span class="sxs-lookup"><span data-stu-id="995de-300">However, you could also configure the image to be built as part of the docker-compose execution with an additional configuration based on a build: section in the docker-compose file.</span></span>

- <span data-ttu-id="995de-301">Inicializuje dvě proměnné prostředí (CatalogUrl a OrderingUrl).</span><span class="sxs-lookup"><span data-stu-id="995de-301">Initializes two environment variables (CatalogUrl and OrderingUrl).</span></span>

- <span data-ttu-id="995de-302">Předá exponovaný port 80 na kontejneru na externí port 80 na hostitelském počítači.</span><span class="sxs-lookup"><span data-stu-id="995de-302">Forwards the exposed port 80 on the container to the external port 80 on the host machine.</span></span>

- <span data-ttu-id="995de-303">Propojí webovou aplikaci s katalogem a objednávkovou službou s nastavením depends_on.</span><span class="sxs-lookup"><span data-stu-id="995de-303">Links the web app to the catalog and ordering service with the depends_on setting.</span></span> <span data-ttu-id="995de-304">To způsobí, že služba čekat, dokud tyto služby jsou spuštěny.</span><span class="sxs-lookup"><span data-stu-id="995de-304">This causes the service to wait until those services are started.</span></span>

<span data-ttu-id="995de-305">Znovu navštívíme soubor docker-compose.yml v pozdější části, když se podíváme, jak implementovat mikroslužeb a aplikace s více kontejnery.</span><span class="sxs-lookup"><span data-stu-id="995de-305">We will revisit the docker-compose.yml file in a later section when we cover how to implement microservices and multi-container apps.</span></span>

### <a name="working-with-docker-composeyml-in-visual-studio-2019"></a><span data-ttu-id="995de-306">Práce s docker-compose.yml ve Visual Studiu 2019</span><span class="sxs-lookup"><span data-stu-id="995de-306">Working with docker-compose.yml in Visual Studio 2019</span></span>

<span data-ttu-id="995de-307">Kromě přidání Dockerfile do projektu, jak jsme již zmínili, Visual Studio 2017 (od verze 15.8 na) můžete přidat orchestrator podporu pro Docker Compose do řešení.</span><span class="sxs-lookup"><span data-stu-id="995de-307">Besides adding a Dockerfile to a project, as we mentioned before, Visual Studio 2017 (from version 15.8 on) can add orchestrator support for Docker Compose to a solution.</span></span>

<span data-ttu-id="995de-308">Když přidáte podporu orchestrator kontejneru, jak je znázorněno na obrázku 5-7, poprvé, Visual Studio vytvoří Dockerfile pro `docker-compose*.yml` projekt a vytvoří nový projekt (část služby) ve vašem řešení s několika globálnísoubory a potom přidá projekt do těchto souborů.</span><span class="sxs-lookup"><span data-stu-id="995de-308">When you add container orchestrator support, as shown in Figure 5-7, for the first time, Visual Studio creates the Dockerfile for the project and creates a new (service section) project in your solution with several global `docker-compose*.yml` files, and then adds the project to those files.</span></span> <span data-ttu-id="995de-309">Potom můžete otevřít soubory docker-compose.yml a aktualizovat je dalšími funkcemi.</span><span class="sxs-lookup"><span data-stu-id="995de-309">You can then open the docker-compose.yml files and update them with additional features.</span></span>

<span data-ttu-id="995de-310">Tento formulář operace je třeba zopakovat každý projekt, který chcete zahrnout do souboru docker-compose.yml.</span><span class="sxs-lookup"><span data-stu-id="995de-310">You have to repeat this operation form every project you want to include in the docker-compose.yml file.</span></span>

<span data-ttu-id="995de-311">V době psaní tohoto článku Visual Studio podporuje **Docker Compose** a **Kubernetes/Helm** orchestrátory.</span><span class="sxs-lookup"><span data-stu-id="995de-311">At the time of this writing, Visual Studio supports **Docker Compose** and **Kubernetes/Helm** orchestrators.</span></span>

![Snímek obrazovky zobrazující možnost Podpora orchestrátoru kontejneru v kontextové nabídce projektu](./media/docker-app-development-workflow/add-container-orchestrator-support-option.png)

<span data-ttu-id="995de-313">**Obrázek 5-7**.</span><span class="sxs-lookup"><span data-stu-id="995de-313">**Figure 5-7**.</span></span> <span data-ttu-id="995de-314">Přidání podpory Dockeru ve Visual Studiu 2019 kliknutím pravým tlačítkem myši na ASP.NET základní projekt</span><span class="sxs-lookup"><span data-stu-id="995de-314">Adding Docker support in Visual Studio 2019 by right-clicking an ASP.NET Core project</span></span>

<span data-ttu-id="995de-315">Po přidání podpory orchestrator do vašeho řešení v sadě Visual Studio, `docker-compose.dcproj` uvidíte také nový uzel (v souboru projektu) v Průzkumníku řešení, který obsahuje přidané soubory docker-compose.yml, jak je znázorněno na obrázku 5-8.</span><span class="sxs-lookup"><span data-stu-id="995de-315">After you add orchestrator support to your solution in Visual Studio, you will also see a new node (in the `docker-compose.dcproj` project file) in Solution Explorer that contains the added docker-compose.yml files, as shown in Figure 5-8.</span></span>

![Snímek obrazovky uzlu docker-compose v Průzkumníku řešení](./media/docker-app-development-workflow/docker-compose-tree-node.png)

<span data-ttu-id="995de-317">**Obrázek 5-8**.</span><span class="sxs-lookup"><span data-stu-id="995de-317">**Figure 5-8**.</span></span> <span data-ttu-id="995de-318">Uzel stromu **docker-compose** přidaný v Průzkumníku řešení Visual Studia 2019</span><span class="sxs-lookup"><span data-stu-id="995de-318">The **docker-compose** tree node added in Visual Studio 2019 Solution Explorer</span></span>

<span data-ttu-id="995de-319">Pomocí příkazu můžete nasadit aplikaci s více kontejnery pomocí jednoho `docker-compose up` souboru docker-compose.yml.</span><span class="sxs-lookup"><span data-stu-id="995de-319">You could deploy a multi-container application with a single docker-compose.yml file by using the `docker-compose up` command.</span></span> <span data-ttu-id="995de-320">Visual Studio však přidá skupinu z nich, takže můžete přepsat hodnoty v závislosti na prostředí (vývoj nebo výroba) a typ spuštění (uvolnění nebo ladění).</span><span class="sxs-lookup"><span data-stu-id="995de-320">However, Visual Studio adds a group of them so you can override values depending on the environment (development or production) and execution type (release or debug).</span></span> <span data-ttu-id="995de-321">Tato funkce bude vysvětlena v dalších částech.</span><span class="sxs-lookup"><span data-stu-id="995de-321">This capability will be explained in later sections.</span></span>

![Obrázek kroku 5.](./media/docker-app-development-workflow/step-5-run-containers-compose-app.png)

## <a name="step-5-build-and-run-your-docker-application"></a><span data-ttu-id="995de-323">Krok 5.</span><span class="sxs-lookup"><span data-stu-id="995de-323">Step 5.</span></span> <span data-ttu-id="995de-324">Sestavení a spuštění aplikace Dockeru</span><span class="sxs-lookup"><span data-stu-id="995de-324">Build and run your Docker application</span></span>

<span data-ttu-id="995de-325">Pokud vaše aplikace má jenom jeden kontejner, můžete jej spustit nasazením do hostitele Dockeru (virtuální počítač nebo fyzický server).</span><span class="sxs-lookup"><span data-stu-id="995de-325">If your application only has a single container, you can run it by deploying it to your Docker host (VM or physical server).</span></span> <span data-ttu-id="995de-326">Pokud však vaše aplikace obsahuje více služeb, můžete ji nasadit jako složenou aplikaci, a to buď pomocí jediného příkazu příkazu příkazu příkazu příkazu cli (`docker-compose up)`nebo s aplikací Visual Studio, která bude tento příkaz používat pod kryty.</span><span class="sxs-lookup"><span data-stu-id="995de-326">However, if your application contains multiple services, you can deploy it as a composed application, either using a single CLI command (`docker-compose up)`, or with Visual Studio, which will use that command under the covers.</span></span> <span data-ttu-id="995de-327">Podívejme se na různé možnosti.</span><span class="sxs-lookup"><span data-stu-id="995de-327">Let's look at the different options.</span></span>

### <a name="option-a-running-a-single-container-application"></a><span data-ttu-id="995de-328">Možnost A: Spuštění aplikace s jedním kontejnerem</span><span class="sxs-lookup"><span data-stu-id="995de-328">Option A: Running a single-container application</span></span>

#### <a name="using-docker-cli"></a><span data-ttu-id="995de-329">Použití cli Dockeru</span><span class="sxs-lookup"><span data-stu-id="995de-329">Using Docker CLI</span></span>

<span data-ttu-id="995de-330">Kontejner Dockeru můžete spustit `docker run` pomocí příkazu, jak je znázorněno na obrázku 5-9:</span><span class="sxs-lookup"><span data-stu-id="995de-330">You can run a Docker container using the `docker run` command, as shown in Figure 5-9:</span></span>

```console
docker run -t -d -p 80:5000 cesardl/netcore-webapi-microservice-docker:first
```

<span data-ttu-id="995de-331">Výše uvedený příkaz vytvoří novou instanci kontejneru ze zadané bitové kopie při každém spuštění.</span><span class="sxs-lookup"><span data-stu-id="995de-331">The above command will create a new container instance from the specified image, every time it's run.</span></span> <span data-ttu-id="995de-332">Parametr můžete `--name` použít k poskytnutí názvu kontejneru `docker start {name}` a potom použít (nebo použít ID kontejneru nebo automatický název) ke spuštění existující instance kontejneru.</span><span class="sxs-lookup"><span data-stu-id="995de-332">You can use the `--name` parameter to give a name to the container and then use `docker start {name}` (or use the container ID or automatic name) to run an existing container instance.</span></span>

![Snímek obrazovky se spuštěním kontejneru Dockeru pomocí příkazu docker run.](./media/docker-app-development-workflow/use-docker-run-command.png)

<span data-ttu-id="995de-334">**Obrázek 5-9**.</span><span class="sxs-lookup"><span data-stu-id="995de-334">**Figure 5-9**.</span></span> <span data-ttu-id="995de-335">Spuštění kontejneru Dockeru pomocí příkazu docker run</span><span class="sxs-lookup"><span data-stu-id="995de-335">Running a Docker container using the docker run command</span></span>

<span data-ttu-id="995de-336">V tomto případě příkaz váže vnitřní port 5000 kontejneru na port 80 hostitelského počítače.</span><span class="sxs-lookup"><span data-stu-id="995de-336">In this case, the command binds the internal port 5000 of the container to port 80 of the host machine.</span></span> <span data-ttu-id="995de-337">To znamená, že hostitel naslouchá na portu 80 a přeposílá na port 5000 v kontejneru.</span><span class="sxs-lookup"><span data-stu-id="995de-337">This means that the host is listening on port 80 and forwarding to port 5000 on the container.</span></span>

<span data-ttu-id="995de-338">Zobrazená hodnota hash je ID kontejneru a je mu `--name` také přiřazen náhodný čitelný název, pokud není použita možnost.</span><span class="sxs-lookup"><span data-stu-id="995de-338">The hash shown is the container ID and it’s also assigned a random readable name if the `--name` option is not used.</span></span>

#### <a name="using-visual-studio"></a><span data-ttu-id="995de-339">Pomocí sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="995de-339">Using Visual Studio</span></span>

<span data-ttu-id="995de-340">Pokud jste nepřidali podporu orchestrator kontejneru, můžete také spustit jeden kontejner aplikace v sadě Visual Studio stisknutím **Ctrl-F5** a můžete také použít **F5** k ladění aplikace v rámci kontejneru.</span><span class="sxs-lookup"><span data-stu-id="995de-340">If you haven't added container orchestrator support, you can also run a single container app in Visual Studio by pressing **Ctrl-F5** and you can also use **F5** to debug the application within the container.</span></span> <span data-ttu-id="995de-341">Kontejner běží místně pomocí docker spustit.</span><span class="sxs-lookup"><span data-stu-id="995de-341">The container runs locally using docker run.</span></span>

### <a name="option-b-running-a-multi-container-application"></a><span data-ttu-id="995de-342">Možnost B: Spuštění aplikace s více kontejnery</span><span class="sxs-lookup"><span data-stu-id="995de-342">Option B: Running a multi-container application</span></span>

<span data-ttu-id="995de-343">Ve většině podnikových scénářů aplikace Dockeru se bude skládat z více služeb, což znamená, že je třeba spustit aplikaci s více kontejnery, jak je znázorněno na obrázku 5-10.</span><span class="sxs-lookup"><span data-stu-id="995de-343">In most enterprise scenarios, a Docker application will be composed of multiple services, which means you need to run a multi-container application, as shown in Figure 5-10.</span></span>

![Virtuální virtuální byl v ovesu s několika kontejnery Dockeru](./media/docker-app-development-workflow/vm-with-docker-containers-deployed.png)

<span data-ttu-id="995de-345">**Obrázek 5-10**.</span><span class="sxs-lookup"><span data-stu-id="995de-345">**Figure 5-10**.</span></span> <span data-ttu-id="995de-346">Virtuální virtuální ms s nasazenými kontejnery Dockeru</span><span class="sxs-lookup"><span data-stu-id="995de-346">VM with Docker containers deployed</span></span>

#### <a name="using-docker-cli"></a><span data-ttu-id="995de-347">Použití cli Dockeru</span><span class="sxs-lookup"><span data-stu-id="995de-347">Using Docker CLI</span></span>

<span data-ttu-id="995de-348">Chcete-li spustit aplikaci s více kontejnery `docker-compose up` s příkazem příkazu Dockeru, použijte příkaz.</span><span class="sxs-lookup"><span data-stu-id="995de-348">To run a multi-container application with the Docker CLI, you use the `docker-compose up` command.</span></span> <span data-ttu-id="995de-349">Tento příkaz používá soubor **docker-compose.yml,** který máte na úrovni řešení k nasazení aplikace s více kontejnery.</span><span class="sxs-lookup"><span data-stu-id="995de-349">This command uses the **docker-compose.yml** file that you have at the solution level to deploy a multi-container application.</span></span> <span data-ttu-id="995de-350">Obrázek 5-11 ukazuje výsledky při spuštění příkazu z hlavního adresáře řešení, který obsahuje soubor docker-compose.yml.</span><span class="sxs-lookup"><span data-stu-id="995de-350">Figure 5-11 shows the results when running the command from your main solution directory, which contains the docker-compose.yml file.</span></span>

![Zobrazení obrazovky při spuštění příkazu docker-compose up](./media/docker-app-development-workflow/results-docker-compose-up.png)

<span data-ttu-id="995de-352">**Obrázek 5-11**.</span><span class="sxs-lookup"><span data-stu-id="995de-352">**Figure 5-11**.</span></span> <span data-ttu-id="995de-353">Příklad výsledků při spuštění příkazu docker-compose up</span><span class="sxs-lookup"><span data-stu-id="995de-353">Example results when running the docker-compose up command</span></span>

<span data-ttu-id="995de-354">Po spuštění příkazu docker-compose up se aplikace a související kontejnery nasadí do hostitele Dockeru, jak je znázorněno na obrázku 5-10.</span><span class="sxs-lookup"><span data-stu-id="995de-354">After the docker-compose up command runs, the application and its related containers are deployed into your Docker host, as depicted in Figure 5-10.</span></span>

#### <a name="using-visual-studio"></a><span data-ttu-id="995de-355">Pomocí sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="995de-355">Using Visual Studio</span></span>

<span data-ttu-id="995de-356">Spuštění aplikace s více kontejnery pomocí Visual Studia 2019 nemůže být jednodušší.</span><span class="sxs-lookup"><span data-stu-id="995de-356">Running a multi-container application using Visual Studio 2019 can't get any simpler.</span></span> <span data-ttu-id="995de-357">Stačí stisknout **Ctrl-F5** spustit nebo **F5** ladit, jako obvykle, nastavení **docker-compose** projektu jako spuštění projektu.</span><span class="sxs-lookup"><span data-stu-id="995de-357">You just press **Ctrl-F5** to run or **F5** to debug, as usual, setting up the **docker-compose** project as the startup project.</span></span>  <span data-ttu-id="995de-358">Visual Studio zpracovává všechny potřebné nastavení, takže můžete vytvořit zarážky jako obvykle a ladit, co se nakonec stane nezávislými procesy spuštěnými na "vzdálených serverech", s ladicím programem, který je již připojen, stejně jako to.</span><span class="sxs-lookup"><span data-stu-id="995de-358">Visual Studio handles all needed setup, so you can create breakpoints as usual and debug what finally become independent processes running in "remote servers", with the debugger already attached, just like that.</span></span>

<span data-ttu-id="995de-359">Jak již bylo zmíněno dříve, pokaždé, když přidáte podporu řešení Docker u projektu v rámci řešení, tento projekt je nakonfigurován v globálním (řešení úrovni) docker-compose.yml souboru, který umožňuje spustit nebo ladit celé řešení najednou.</span><span class="sxs-lookup"><span data-stu-id="995de-359">As mentioned before, each time you add Docker solution support to a project within a solution, that project is configured in the global (solution-level) docker-compose.yml file, which lets you run or debug the whole solution at once.</span></span> <span data-ttu-id="995de-360">Visual Studio spustí jeden kontejner pro každý projekt, který má povolenou podporu řešení Dockeru a provede všechny interní kroky za vás (dotnet publish, docker build atd.).</span><span class="sxs-lookup"><span data-stu-id="995de-360">Visual Studio will start one container for each project that has Docker solution support enabled, and perform all the internal steps for you (dotnet publish, docker build, etc.).</span></span>

<span data-ttu-id="995de-361">Pokud se chcete podívat na všechny dřiny, podívejte se na soubor:</span><span class="sxs-lookup"><span data-stu-id="995de-361">If you want to take a peek at all the drudgery, take a look at the file:</span></span>

`{root solution folder}\obj\Docker\docker-compose.vs.debug.g.yml`

<span data-ttu-id="995de-362">Důležitým bodem je, jak je znázorněno na obrázku 5-12, v Sadě Visual Studio 2019 je další příkaz **Docker** u akce klíče F5.</span><span class="sxs-lookup"><span data-stu-id="995de-362">The important point here is that, as shown in Figure 5-12, in Visual Studio 2019 there is an additional **Docker** command for the F5 key action.</span></span> <span data-ttu-id="995de-363">Tato možnost umožňuje spustit nebo ladit aplikaci s více kontejnery spuštěním všech kontejnerů, které jsou definovány v souborech docker-compose.yml na úrovni řešení.</span><span class="sxs-lookup"><span data-stu-id="995de-363">This option lets you run or debug a multi-container application by running all the containers that are defined in the docker-compose.yml files at the solution level.</span></span> <span data-ttu-id="995de-364">Možnost ladit řešení s více kontejnery znamená, že můžete nastavit několik zarážek, každý zarážka v jiném projektu (kontejner) a při ladění z Visual Studio se zastaví na zarážky definované v různých projektech a běží na různých kontejnerech.</span><span class="sxs-lookup"><span data-stu-id="995de-364">The ability to debug multiple-container solutions means that you can set several breakpoints, each breakpoint in a different project (container), and while debugging from Visual Studio you will stop at breakpoints defined in different projects and running on different containers.</span></span>

![Snímek obrazovky panelu nástrojů ladění se spuštěným projektem docker-compose](./media/docker-app-development-workflow/debug-toolbar-docker-compose-project.png)

<span data-ttu-id="995de-366">**Obrázek 5-12**.</span><span class="sxs-lookup"><span data-stu-id="995de-366">**Figure 5-12**.</span></span> <span data-ttu-id="995de-367">Spouštění aplikací s více kontejnery ve Visual Studiu 2019</span><span class="sxs-lookup"><span data-stu-id="995de-367">Running multi-container apps in Visual Studio 2019</span></span>

### <a name="additional-resources"></a><span data-ttu-id="995de-368">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="995de-368">Additional resources</span></span>

- <span data-ttu-id="995de-369">**Nasazení kontejneru ASP.NET vzdálenému hostiteli Dockeru** </span><span class="sxs-lookup"><span data-stu-id="995de-369">**Deploy an ASP.NET container to a remote Docker host** </span></span>\
  <https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker>

### <a name="a-note-about-testing-and-deploying-with-orchestrators"></a><span data-ttu-id="995de-370">Poznámka o testování a nasazování s orchestrátory</span><span class="sxs-lookup"><span data-stu-id="995de-370">A note about testing and deploying with orchestrators</span></span>

<span data-ttu-id="995de-371">Příkazy pro spuštění dockeru a dockeru (nebo spuštění a ladění kontejnerů v sadě Visual Studio) jsou vhodné pro testování kontejnerů ve vývojovém prostředí.</span><span class="sxs-lookup"><span data-stu-id="995de-371">The docker-compose up and docker run commands (or running and debugging the containers in Visual Studio) are adequate for testing containers in your development environment.</span></span> <span data-ttu-id="995de-372">Ale neměli byste používat tento přístup pro nasazení v produkčním prostředí, kde byste měli cílit orchestrátory jako [Kubernetes](https://kubernetes.io/) nebo [Service Fabric](https://azure.microsoft.com/services/service-fabric/).</span><span class="sxs-lookup"><span data-stu-id="995de-372">But you should not use this approach for production deployments, where you should target orchestrators like [Kubernetes](https://kubernetes.io/) or [Service Fabric](https://azure.microsoft.com/services/service-fabric/).</span></span> <span data-ttu-id="995de-373">Pokud používáte Kubernetes, budete muset použít [pody](https://kubernetes.io/docs/concepts/workloads/pods/pod/) uspořádat kontejnery a [služby](https://kubernetes.io/docs/concepts/services-networking/service/) pro jejich připojení k síti.</span><span class="sxs-lookup"><span data-stu-id="995de-373">If you're using Kubernetes, you have to use [pods](https://kubernetes.io/docs/concepts/workloads/pods/pod/) to organize containers and [services](https://kubernetes.io/docs/concepts/services-networking/service/) to network them.</span></span> <span data-ttu-id="995de-374">Nasazení [můžete](https://kubernetes.io/docs/concepts/workloads/controllers/deployment/) také použít k uspořádání vytváření a úprav podu.</span><span class="sxs-lookup"><span data-stu-id="995de-374">You also use [deployments](https://kubernetes.io/docs/concepts/workloads/controllers/deployment/) to organize pod creation and modification.</span></span>

![Obrázek kroku 6.](./media/docker-app-development-workflow/step-6-test-app-microservices.png)

## <a name="step-6-test-your-docker-application-using-your-local-docker-host"></a><span data-ttu-id="995de-376">Krok 6.</span><span class="sxs-lookup"><span data-stu-id="995de-376">Step 6.</span></span> <span data-ttu-id="995de-377">Testování aplikace Dockeru pomocí místního hostitele Dockeru</span><span class="sxs-lookup"><span data-stu-id="995de-377">Test your Docker application using your local Docker host</span></span>

<span data-ttu-id="995de-378">Tento krok se bude lišit v závislosti na tom, co vaše aplikace dělá.</span><span class="sxs-lookup"><span data-stu-id="995de-378">This step will vary depending on what your application is doing.</span></span> <span data-ttu-id="995de-379">V jednoduché webové aplikaci .NET Core, která je nasazena jako jeden kontejner nebo služba, můžete ke službě přistupovat otevřením prohlížeče na hostiteli Dockeru a přechodem na tento web, jak je znázorněno na obrázku 5-13.</span><span class="sxs-lookup"><span data-stu-id="995de-379">In a simple .NET Core Web application that is deployed as a single container or service, you can access the service by opening a browser on the Docker host and navigating to that site, as shown in Figure 5-13.</span></span> <span data-ttu-id="995de-380">(Pokud konfigurace v Souboru Dockerfile mapuje kontejner na port na hostiteli, který je něco jiného než 80, zahrňte port hostitele v adrese URL.)</span><span class="sxs-lookup"><span data-stu-id="995de-380">(If the configuration in the Dockerfile maps the container to a port on the host that is anything other than 80, include the host port in the URL.)</span></span>

![Snímek obrazovky s odpovědí z localhost/API/values.](./media/docker-app-development-workflow/test-docker-app-locally-localhost.png)

<span data-ttu-id="995de-382">**Obrázek 5-13**.</span><span class="sxs-lookup"><span data-stu-id="995de-382">**Figure 5-13**.</span></span> <span data-ttu-id="995de-383">Příklad testování aplikace Docker místně pomocí localhost</span><span class="sxs-lookup"><span data-stu-id="995de-383">Example of testing your Docker application locally using localhost</span></span>

<span data-ttu-id="995de-384">Pokud localhost neukazuje na IP hostitele Dockeru (ve výchozím nastavení, při použití Docker CE, by měl), chcete-li přejít na vaši službu, použijte IP adresu síťové karty vašeho počítače.</span><span class="sxs-lookup"><span data-stu-id="995de-384">If localhost is not pointing to the Docker host IP (by default, when using Docker CE, it should), to navigate to your service, use the IP address of your machine's network card.</span></span>

<span data-ttu-id="995de-385">Všimněte si, že tato adresa URL v prohlížeči používá port 80 pro konkrétní příklad kontejneru, který je popsán.</span><span class="sxs-lookup"><span data-stu-id="995de-385">Note that this URL in the browser uses port 80 for the particular container example being discussed.</span></span> <span data-ttu-id="995de-386">Však interně požadavky jsou přesměrovány na port 5000, protože to bylo, jak byl nasazen s příkazem docker spustit, jak je vysvětleno v předchozím kroku.</span><span class="sxs-lookup"><span data-stu-id="995de-386">However, internally the requests are being redirected to port 5000, because that was how it was deployed with the docker run command, as explained in a previous step.</span></span>

<span data-ttu-id="995de-387">Aplikaci můžete také otestovat pomocí zvlnění z terminálu, jak je znázorněno na obrázku 5-14.</span><span class="sxs-lookup"><span data-stu-id="995de-387">You can also test the application using curl from the terminal, as shown in Figure 5-14.</span></span> <span data-ttu-id="995de-388">V instalaci Dockeru v systému Windows je výchozí IP hostitele Dockeru vždy 10.0.75.1 kromě skutečné IP adresy vašeho počítače.</span><span class="sxs-lookup"><span data-stu-id="995de-388">In a Docker installation on Windows, the default Docker Host IP is always 10.0.75.1 in addition to your machine's actual IP address.</span></span>

![Konzolový výstup http://10.0.75.1/API/values od získání s curl.](./media/docker-app-development-workflow/test-docker-app-locally-curl.png)

<span data-ttu-id="995de-390">**Obrázek 5-14**.</span><span class="sxs-lookup"><span data-stu-id="995de-390">**Figure 5-14**.</span></span> <span data-ttu-id="995de-391">Příklad testování aplikace Docker místně pomocí curl</span><span class="sxs-lookup"><span data-stu-id="995de-391">Example of testing your Docker application locally using curl</span></span>

### <a name="testing-and-debugging-containers-with-visual-studio-2019"></a><span data-ttu-id="995de-392">Testování a ladění kontejnerů pomocí Visual Studia 2019</span><span class="sxs-lookup"><span data-stu-id="995de-392">Testing and debugging containers with Visual Studio 2019</span></span>

<span data-ttu-id="995de-393">Při spuštění a ladění kontejnerů s Visual Studio 2019, můžete ladit .NET aplikace v podstatě stejným způsobem jako při spuštění bez kontejnerů.</span><span class="sxs-lookup"><span data-stu-id="995de-393">When running and debugging the containers with Visual Studio 2019, you can debug the .NET application in much the same way as you would when running without containers.</span></span>

### <a name="testing-and-debugging-without-visual-studio"></a><span data-ttu-id="995de-394">Testování a ladění bez sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="995de-394">Testing and debugging without Visual Studio</span></span>

<span data-ttu-id="995de-395">Pokud vyvíjíte pomocí editor/CLI přístup, ladění kontejnerů je obtížnější a budete pravděpodobně chtít ladit generováním trasování.</span><span class="sxs-lookup"><span data-stu-id="995de-395">If you're developing using the editor/CLI approach, debugging containers is more difficult and you'll probably want to debug by generating traces.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="995de-396">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="995de-396">Additional resources</span></span>

- <span data-ttu-id="995de-397">**Ladění aplikací v místním kontejneru Dockeru** </span><span class="sxs-lookup"><span data-stu-id="995de-397">**Debugging apps in a local Docker container** </span></span>\
  [https://docs.microsoft.com/visualstudio/containers/edit-and-refresh](/visualstudio/containers/edit-and-refresh)

- <span data-ttu-id="995de-398">**Steva Laskera. Sestavení, ladění, nasazení ASP.NET základních aplikací pomocí Dockeru.**</span><span class="sxs-lookup"><span data-stu-id="995de-398">**Steve Lasker. Build, Debug, Deploy ASP.NET Core Apps with Docker.**</span></span> <span data-ttu-id="995de-399">Video.</span><span class="sxs-lookup"><span data-stu-id="995de-399">Video.</span></span> \
  <https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T115>

## <a name="simplified-workflow-when-developing-containers-with-visual-studio"></a><span data-ttu-id="995de-400">Zjednodušený pracovní postup při vývoji kontejnerů pomocí sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="995de-400">Simplified workflow when developing containers with Visual Studio</span></span>

<span data-ttu-id="995de-401">Efektivně pracovní postup při použití sady Visual Studio je mnohem jednodušší, než pokud použijete přístup editor/CLI.</span><span class="sxs-lookup"><span data-stu-id="995de-401">Effectively, the workflow when using Visual Studio is a lot simpler than if you use the editor/CLI approach.</span></span> <span data-ttu-id="995de-402">Většina kroků požadovaných Dockersouvisející s Dockerfile a docker-compose.yml soubory jsou skryté nebo zjednodušené Visual Studio, jak je znázorněno na obrázku 5-15.</span><span class="sxs-lookup"><span data-stu-id="995de-402">Most of the steps required by Docker related to the Dockerfile and docker-compose.yml files are hidden or simplified by Visual Studio, as shown in Figure 5-15.</span></span>

:::image type="complex" source="./media/docker-app-development-workflow/simplified-life-cycle-containerized-apps-docker-cli.png" alt-text="Diagram znázorňující pět zjednodušených kroků, které je třeba k vytvoření aplikace.":::
<span data-ttu-id="995de-404">Proces vývoje pro aplikace Docker: 1 - Kód vaší aplikace, 2 - Zápis Dockerfile/s, 3 - Vytvoření bitových kopií definovaných na Dockerfile/s, 4 - (volitelné) Compose služby v docker-compose.yml souboru, 5 - Spustit kontejner nebo docker-compose aplikace, 6 - Test aplikace nebo mikroslužeb, 7 - Push to repo a opakovat.</span><span class="sxs-lookup"><span data-stu-id="995de-404">The development process for Docker apps: 1 - Code your App, 2 - Write Dockerfile/s, 3 - Create images defined at Dockerfile/s, 4 - (optional) Compose services in the docker-compose.yml file, 5 - Run container or docker-compose app, 6 - Test your app or microservices, 7 - Push to repo and repeat.</span></span>
:::image-end:::

<span data-ttu-id="995de-405">**Obrázek 5-15**.</span><span class="sxs-lookup"><span data-stu-id="995de-405">**Figure 5-15**.</span></span> <span data-ttu-id="995de-406">Zjednodušený pracovní postup při vývoji pomocí sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="995de-406">Simplified workflow when developing with Visual Studio</span></span>

<span data-ttu-id="995de-407">Kromě toho je třeba provést krok 2 (přidání podpory Dockeru do vašich projektů) pouze jednou.</span><span class="sxs-lookup"><span data-stu-id="995de-407">In addition, you need to perform step 2 (adding Docker support to your projects) just once.</span></span> <span data-ttu-id="995de-408">Proto pracovní postup je podobný běžné vývojové úkoly při použití rozhraní .NET pro jakýkoli jiný vývoj.</span><span class="sxs-lookup"><span data-stu-id="995de-408">Therefore, the workflow is similar to your usual development tasks when using .NET for any other development.</span></span> <span data-ttu-id="995de-409">Musíte vědět, co se děje pod kryty (proces sestavení image, jaké základní image používáte, nasazení kontejnerů atd.) a někdy budete také muset upravit soubor Dockerfile nebo docker-compose.yml pro přizpůsobení chování.</span><span class="sxs-lookup"><span data-stu-id="995de-409">You need to know what is going on under the covers (the image build process, what base images you're using, deployment of containers, etc.) and sometimes you will also need to edit the Dockerfile or docker-compose.yml file to customize behaviors.</span></span> <span data-ttu-id="995de-410">Ale většina práce je velmi zjednodušena pomocí sady Visual Studio, takže budete mnohem produktivnější.</span><span class="sxs-lookup"><span data-stu-id="995de-410">But most of the work is greatly simplified by using Visual Studio, making you a lot more productive.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="995de-411">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="995de-411">Additional resources</span></span>

- <span data-ttu-id="995de-412">**Steva Laskera. Vývoj dockeru .NET s Visual Studio (2017)** </span><span class="sxs-lookup"><span data-stu-id="995de-412">**Steve Lasker. .NET Docker Development with Visual Studio (2017)** </span></span>\
  <https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T111>

## <a name="using-powershell-commands-in-a-dockerfile-to-set-up-windows-containers"></a><span data-ttu-id="995de-413">Nastavení kontejnerů Windows pomocí powershellových příkazů v souboru Dockerfile</span><span class="sxs-lookup"><span data-stu-id="995de-413">Using PowerShell commands in a Dockerfile to set up Windows Containers</span></span>

<span data-ttu-id="995de-414">[Kontejnery Windows](https://docs.microsoft.com/virtualization/windowscontainers/about/index) umožňují převést existující aplikace Systému Windows na inaimages Dockeru a nasadit je pomocí stejných nástrojů jako zbytek ekosystému Dockeru.</span><span class="sxs-lookup"><span data-stu-id="995de-414">[Windows Containers](https://docs.microsoft.com/virtualization/windowscontainers/about/index) allow you to convert your existing Windows applications into Docker images and deploy them with the same tools as the rest of the Docker ecosystem.</span></span> <span data-ttu-id="995de-415">Chcete-li použít kontejnery systému Windows, spouštět příkazy prostředí PowerShell v souboru Dockerfile, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="995de-415">To use Windows Containers, you run PowerShell commands in the Dockerfile, as shown in the following example:</span></span>

```Dockerfile
FROM mcr.microsoft.com/windows/servercore
LABEL Description="IIS" Vendor="Microsoft" Version="10"
RUN powershell -Command Add-WindowsFeature Web-Server
CMD [ "ping", "localhost", "-t" ]
```

<span data-ttu-id="995de-416">V tomto případě používáme základní bitovou kopii jádra systému Windows Server (nastavení FROM) a instalujeme službu IIS pomocí příkazu Prostředí PowerShell (nastavení RUN).</span><span class="sxs-lookup"><span data-stu-id="995de-416">In this case, we are using a Windows Server Core base image (the FROM setting) and installing IIS with a PowerShell command (the RUN setting).</span></span> <span data-ttu-id="995de-417">Podobným způsobem můžete také použít příkazy prostředí PowerShell k nastavení dalších součástí, jako je ASP.NET 4.x, .NET 4.6 nebo jakýkoli jiný software windows.</span><span class="sxs-lookup"><span data-stu-id="995de-417">In a similar way, you could also use PowerShell commands to set up additional components like ASP.NET 4.x, .NET 4.6, or any other Windows software.</span></span> <span data-ttu-id="995de-418">Například následující příkaz v souboru Dockerfile nastaví ASP.NET 4.5:</span><span class="sxs-lookup"><span data-stu-id="995de-418">For example, the following command in a Dockerfile sets up ASP.NET 4.5:</span></span>

```Dockerfile
RUN powershell add-windowsfeature web-asp-net45
```

### <a name="additional-resources"></a><span data-ttu-id="995de-419">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="995de-419">Additional resources</span></span>

- <span data-ttu-id="995de-420">**aspnet-docker/Dockerfile.**</span><span class="sxs-lookup"><span data-stu-id="995de-420">**aspnet-docker/Dockerfile.**</span></span> <span data-ttu-id="995de-421">Příklad příkazů prostředí PowerShell pro spuštění ze souborů dockerfiles za účelem zahrnutí funkcí systému Windows.</span><span class="sxs-lookup"><span data-stu-id="995de-421">Example PowerShell commands to run from dockerfiles to include Windows features.</span></span>\
  <https://github.com/Microsoft/aspnet-docker/blob/master/4.7.1-windowsservercore-ltsc2016/runtime/Dockerfile>

>[!div class="step-by-step"]
><span data-ttu-id="995de-422">[Předchozí](index.md)
>[další](../multi-container-microservice-net-applications/index.md)</span><span class="sxs-lookup"><span data-stu-id="995de-422">[Previous](index.md)
[Next](../multi-container-microservice-net-applications/index.md)</span></span>
