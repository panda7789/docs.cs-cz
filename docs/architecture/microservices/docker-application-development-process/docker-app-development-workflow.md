---
title: Pracovní postup vývoje aplikací Dockeru
description: Pochopte podrobnosti pracovního postupu pro vývoj aplikací založených na Docker. Zahajte krok za krokem a získejte do některých podrobností, abyste mohli optimalizovat fázemi a skončit s zjednodušeným pracovním postupem, který je dostupný při používání sady Visual Studio.
ms.date: 01/07/2019
ms.openlocfilehash: 53675bf974069e9052d6d03b2743314af6f13cf9
ms.sourcegitcommit: feb42222f1430ca7b8115ae45e7a38fc4a1ba623
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/02/2020
ms.locfileid: "76965786"
---
# <a name="development-workflow-for-docker-apps"></a><span data-ttu-id="d505b-104">Pracovní postup vývoje aplikací Dockeru</span><span class="sxs-lookup"><span data-stu-id="d505b-104">Development workflow for Docker apps</span></span>

<span data-ttu-id="d505b-105">Životní cyklus vývoje aplikací začíná ve vašem počítači, jako vývojář, kde aplikaci nakódujete pomocí preferovaného jazyka a otestujete ji místně.</span><span class="sxs-lookup"><span data-stu-id="d505b-105">The application development life cycle starts at your computer, as a developer, where you code the application using your preferred language and test it locally.</span></span> <span data-ttu-id="d505b-106">V tomto pracovním postupu bez ohledu na to, jaký jazyk, architekturu a platformu zvolíte, budete vždycky vyvíjet a testovat kontejnery Docker, ale děláte je místně.</span><span class="sxs-lookup"><span data-stu-id="d505b-106">With this workflow, no matter which language, framework, and platform you choose, you're always developing and testing Docker containers, but doing so locally.</span></span>

<span data-ttu-id="d505b-107">Každý kontejner (instance image Docker) obsahuje následující komponenty:</span><span class="sxs-lookup"><span data-stu-id="d505b-107">Each container (an instance of a Docker image) includes the following components:</span></span>

- <span data-ttu-id="d505b-108">Výběr operačního systému, například distribuce systému Linux, Windows nano Server nebo jádro Windows serveru.</span><span class="sxs-lookup"><span data-stu-id="d505b-108">An operating system selection, for example, a Linux distribution, Windows Nano Server, or Windows Server Core.</span></span>

- <span data-ttu-id="d505b-109">Soubory přidané během vývoje, například zdrojový kód a binární soubory aplikace.</span><span class="sxs-lookup"><span data-stu-id="d505b-109">Files added during development, for example, source code and application binaries.</span></span>

- <span data-ttu-id="d505b-110">Konfigurační informace, například nastavení prostředí a závislosti.</span><span class="sxs-lookup"><span data-stu-id="d505b-110">Configuration information, such as environment settings and dependencies.</span></span>

## <a name="workflow-for-developing-docker-container-based-applications"></a><span data-ttu-id="d505b-111">Pracovní postup pro vývoj aplikací založených na kontejnerech Docker</span><span class="sxs-lookup"><span data-stu-id="d505b-111">Workflow for developing Docker container-based applications</span></span>

<span data-ttu-id="d505b-112">Tato část popisuje pracovní postup vývoje *vnitřních smyček* pro aplikace založené na kontejnerech Docker.</span><span class="sxs-lookup"><span data-stu-id="d505b-112">This section describes the *inner-loop* development workflow for Docker container-based applications.</span></span> <span data-ttu-id="d505b-113">Pracovní postup vnitřní smyčky znamená, že se nepovažuje za širší DevOps pracovní postup, který může zahrnovat až produkční nasazení, a zaměřuje se na vývojovou práci, která se provádí na počítači vývojáře.</span><span class="sxs-lookup"><span data-stu-id="d505b-113">The inner-loop workflow means it's not considering the broader DevOps workflow, which can include up to production deployment, and just focuses on the development work done on the developer's computer.</span></span> <span data-ttu-id="d505b-114">Úvodní kroky pro nastavení prostředí nejsou zahrnuté, protože se tyto kroky provádějí jenom jednou.</span><span class="sxs-lookup"><span data-stu-id="d505b-114">The initial steps to set up the environment aren't included, since those steps are done only once.</span></span>

<span data-ttu-id="d505b-115">Aplikace se skládá z vašich vlastních služeb a dalších knihoven (závislosti).</span><span class="sxs-lookup"><span data-stu-id="d505b-115">An application is composed of your own services plus additional libraries (dependencies).</span></span> <span data-ttu-id="d505b-116">Následují základní kroky, které obvykle provádíte při sestavování aplikace Docker, jak je znázorněno na obrázku 5-1.</span><span class="sxs-lookup"><span data-stu-id="d505b-116">The following are the basic steps you usually take when building a Docker application, as illustrated in Figure 5-1.</span></span>

:::image type="complex" source="./media/docker-app-development-workflow/life-cycle-containerized-apps-docker-cli.png" alt-text="Diagram znázorňující 7 kroků, které je potřeba k vytvoření kontejnerové aplikace.":::
<span data-ttu-id="d505b-118">Proces vývoje pro aplikace Docker: 1 – kódování vaší aplikace, 2-zápis souboru Dockerfile/s, 3-vytváření imagí definovaných na souboru Dockerfile/s, 4 – (volitelné) psaní služeb v souboru Docker-Compose. yml, 5 spuštění kontejneru nebo Docker – sestavování, 6-testování aplikace nebo mikroslužeb, 7-nabízení do úložiště a opakování.</span><span class="sxs-lookup"><span data-stu-id="d505b-118">The development process for Docker apps: 1 - Code your App, 2 - Write Dockerfile/s, 3 - Create images defined at Dockerfile/s, 4 - (optional) Compose services in the docker-compose.yml file, 5 - Run container or docker-compose app, 6 - Test your app or microservices, 7 - Push to repo and repeat.</span></span>
:::image-end:::

<span data-ttu-id="d505b-119">**Obrázek 5-1.**</span><span class="sxs-lookup"><span data-stu-id="d505b-119">**Figure 5-1.**</span></span> <span data-ttu-id="d505b-120">Podrobný pracovní postup pro vývoj aplikací s kontejnerem Docker</span><span class="sxs-lookup"><span data-stu-id="d505b-120">Step-by-step workflow for developing Docker containerized apps</span></span>

<span data-ttu-id="d505b-121">V této části je tento celý proces podrobný a každý hlavní krok je vysvětlen tak, že zaměříte na prostředí sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d505b-121">In this section, this whole process is detailed and every major step is explained by focusing on a Visual Studio environment.</span></span>

<span data-ttu-id="d505b-122">Pokud používáte přístup pro vývoj Editor/CLI (například Visual Studio Code plus Docker CLI v systému macOS nebo Windows), musíte znát každý krok, obecně více podrobností, než Pokud používáte Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d505b-122">When you're using an editor/CLI development approach (for example, Visual Studio Code plus Docker CLI on macOS or Windows), you need to know every step, generally in more detail than if you're using Visual Studio.</span></span> <span data-ttu-id="d505b-123">Další informace o práci v prostředí CLI najdete v části elektronický [životní cyklus aplikací Docker v kontejneru s platformami a nástroji Microsoftu](https://aka.ms/dockerlifecycleebook/).</span><span class="sxs-lookup"><span data-stu-id="d505b-123">For more information about working in a CLI environment, see the e-book [Containerized Docker Application lifecycle with Microsoft Platforms and Tools](https://aka.ms/dockerlifecycleebook/).</span></span>

<span data-ttu-id="d505b-124">Pokud používáte sadu Visual Studio 2017, mnohé z těchto kroků jsou zpracovávány za vás, což výrazně zvyšuje vaši produktivitu.</span><span class="sxs-lookup"><span data-stu-id="d505b-124">When you're using Visual Studio 2017, many of those steps are handled for you, which dramatically improves your productivity.</span></span> <span data-ttu-id="d505b-125">To platí hlavně v případě, že používáte Visual Studio 2017 a cílíte na aplikace s více kontejnery.</span><span class="sxs-lookup"><span data-stu-id="d505b-125">This is especially true when you're using Visual Studio 2017 and targeting multi-container applications.</span></span> <span data-ttu-id="d505b-126">Například když jediným kliknutím myši, Visual Studio přidá do vašich projektů soubor souboru Dockerfile a Docker-Compose. yml s konfigurací vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="d505b-126">For instance, with just one mouse click, Visual Studio adds the Dockerfile and docker-compose.yml file to your projects with the configuration for your application.</span></span> <span data-ttu-id="d505b-127">Při spuštění aplikace v aplikaci Visual Studio se vytvoří image Docker a aplikace s více kontejnery se spustí přímo v Docker; i když vám umožní ladit několik kontejnerů najednou.</span><span class="sxs-lookup"><span data-stu-id="d505b-127">When you run the application in Visual Studio, it builds the Docker image and runs the multi-container application directly in Docker; it even allows you to debug several containers at once.</span></span> <span data-ttu-id="d505b-128">Tyto funkce zvýší vaši rychlost vývoje.</span><span class="sxs-lookup"><span data-stu-id="d505b-128">These features will boost your development speed.</span></span>

<span data-ttu-id="d505b-129">Nicméně, protože Visual Studio neprovede tyto kroky automaticky, neznamená to, že nepotřebujete, abyste věděli, co se právě nachází pod nástrojem Docker.</span><span class="sxs-lookup"><span data-stu-id="d505b-129">However, just because Visual Studio makes those steps automatic doesn't mean that you don't need to know what's going on underneath with Docker.</span></span> <span data-ttu-id="d505b-130">Proto následující pokyny podrobně popisuje každý krok.</span><span class="sxs-lookup"><span data-stu-id="d505b-130">Therefore, the following guidance details every step.</span></span>

![Obrázek pro krok 1](./media/docker-app-development-workflow/step-1-code-your-app.png)

## <a name="step-1-start-coding-and-create-your-initial-application-or-service-baseline"></a><span data-ttu-id="d505b-132">Krok 1.</span><span class="sxs-lookup"><span data-stu-id="d505b-132">Step 1.</span></span> <span data-ttu-id="d505b-133">Spuštění kódování a vytvoření počátečního směrného plánu aplikace nebo služby</span><span class="sxs-lookup"><span data-stu-id="d505b-133">Start coding and create your initial application or service baseline</span></span>

<span data-ttu-id="d505b-134">Vývoj aplikace Docker je podobný jako při vývoji aplikace bez Docker.</span><span class="sxs-lookup"><span data-stu-id="d505b-134">Developing a Docker application is similar to the way you develop an application without Docker.</span></span> <span data-ttu-id="d505b-135">Rozdíl je v tom, že při vývoji pro Docker nasazujete a testujete svou aplikaci nebo služby běžící v kontejnerech Docker ve vašem místním prostředí (buď nastavení virtuálního počítače Linux pomocí Docker, nebo přímo Windows, pokud používáte kontejnery Windows).</span><span class="sxs-lookup"><span data-stu-id="d505b-135">The difference is that while developing for Docker, you're deploying and testing your application or services running within Docker containers in your local environment (either a Linux VM setup by Docker or directly Windows if using Windows Containers).</span></span>

### <a name="set-up-your-local-environment-with-visual-studio"></a><span data-ttu-id="d505b-136">Nastavení místního prostředí pomocí sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="d505b-136">Set up your local environment with Visual Studio</span></span>

<span data-ttu-id="d505b-137">Pokud chcete začít, ujistěte se, že máte nainstalovánu [verzi Docker Community Edition (CE)](https://docs.docker.com/docker-for-windows/) pro Windows, jak je vysvětleno v následujících pokynech:</span><span class="sxs-lookup"><span data-stu-id="d505b-137">To begin, make sure you have [Docker Community Edition (CE)](https://docs.docker.com/docker-for-windows/) for Windows installed, as explained in the following instructions:</span></span>

[<span data-ttu-id="d505b-138">Začínáme s Docker CE for Windows</span><span class="sxs-lookup"><span data-stu-id="d505b-138">Get started with Docker CE for Windows</span></span>](https://docs.docker.com/docker-for-windows/)

<span data-ttu-id="d505b-139">Kromě toho potřebujete Visual Studio 2017 verze 15,7 nebo novější s nainstalovanou úlohou **vývoje .NET Core pro různé platformy** , jak je znázorněno na obrázku 5-2.</span><span class="sxs-lookup"><span data-stu-id="d505b-139">In addition, you need Visual Studio 2017 version 15.7 or later, with the **.NET Core cross-platform development** workload installed, as shown in Figure 5-2.</span></span>

![Snímek obrazovky s výběrem pro vývoj pro různé platformy .NET Core](./media/docker-app-development-workflow/dotnet-core-cross-platform-development.png)

<span data-ttu-id="d505b-141">**Obrázek 5-2**.</span><span class="sxs-lookup"><span data-stu-id="d505b-141">**Figure 5-2**.</span></span> <span data-ttu-id="d505b-142">Výběr úlohy **vývoje .NET Core pro různé platformy** během instalace sady Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="d505b-142">Selecting the **.NET Core cross-platform development** workload during Visual Studio 2017 setup</span></span>

<span data-ttu-id="d505b-143">Můžete spustit kódování aplikace v jednoduchém rozhraní .NET (obvykle v .NET Core, pokud plánujete používat kontejnery) dokonce ještě před povolením Docker ve vaší aplikaci a nasazením a testováním v Docker.</span><span class="sxs-lookup"><span data-stu-id="d505b-143">You can start coding your application in plain .NET (usually in .NET Core if you're planning to use containers) even before enabling Docker in your application and deploying and testing in Docker.</span></span> <span data-ttu-id="d505b-144">Doporučuje se ale co nejdříve začít pracovat na Docker, protože to bude reálné prostředí a jakékoli problémy, které je možné zjistit co nejdříve.</span><span class="sxs-lookup"><span data-stu-id="d505b-144">However, it is recommended that you start working on Docker as soon as possible, because that will be the real environment and any issues can be discovered as soon as possible.</span></span> <span data-ttu-id="d505b-145">To je doporučováno, protože Visual Studio usnadňuje práci s Docker, který je skoro průhledný, což je nejlepší příklad při ladění aplikací s více kontejnery ze sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d505b-145">This is encouraged because Visual Studio makes it so easy to work with Docker that it almost feels transparent—the best example when debugging multi-container applications from Visual Studio.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="d505b-146">Další materiály a zdroje informací</span><span class="sxs-lookup"><span data-stu-id="d505b-146">Additional resources</span></span>

- <span data-ttu-id="d505b-147">**Začínáme s Docker CE for Windows** </span><span class="sxs-lookup"><span data-stu-id="d505b-147">**Get started with Docker CE for Windows** </span></span>\
  <https://docs.docker.com/docker-for-windows/>

- <span data-ttu-id="d505b-148">**Visual Studio 2017** </span><span class="sxs-lookup"><span data-stu-id="d505b-148">**Visual Studio 2017** </span></span>\
  [https://visualstudio.microsoft.com/downloads/](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017)

![Obrázek pro krok 2.](./media/docker-app-development-workflow/step-2-write-dockerfile.png)

## <a name="step-2-create-a-dockerfile-related-to-an-existing-net-base-image"></a><span data-ttu-id="d505b-150">Krok 2.</span><span class="sxs-lookup"><span data-stu-id="d505b-150">Step 2.</span></span> <span data-ttu-id="d505b-151">Vytvoření souboru Dockerfile souvisejícího s existující imagí .NET Base</span><span class="sxs-lookup"><span data-stu-id="d505b-151">Create a Dockerfile related to an existing .NET base image</span></span>

<span data-ttu-id="d505b-152">Pro každou vlastní image, kterou chcete sestavit, potřebujete souboru Dockerfile; také potřebujete souboru Dockerfile pro každý kontejner, který chcete nasadit, bez ohledu na to, jestli nasazujete automaticky ze sady Visual Studio, nebo ručně pomocí příkazů Docker CLI (příkazy Docker Run a Docker-skládání).</span><span class="sxs-lookup"><span data-stu-id="d505b-152">You need a Dockerfile for each custom image you want to build; you also need a Dockerfile for each container to be deployed, whether you deploy automatically from Visual Studio or manually using the Docker CLI (docker run and docker-compose commands).</span></span> <span data-ttu-id="d505b-153">Pokud vaše aplikace obsahuje jednu vlastní službu, budete potřebovat jeden souboru Dockerfile.</span><span class="sxs-lookup"><span data-stu-id="d505b-153">If your application contains a single custom service, you need a single Dockerfile.</span></span> <span data-ttu-id="d505b-154">Pokud vaše aplikace obsahuje více služeb (jako v architektuře mikroslužeb), budete pro každou službu potřebovat jeden souboru Dockerfile.</span><span class="sxs-lookup"><span data-stu-id="d505b-154">If your application contains multiple services (as in a microservices architecture), you need one Dockerfile for each service.</span></span>

<span data-ttu-id="d505b-155">Souboru Dockerfile je umístěn v kořenové složce aplikace nebo služby.</span><span class="sxs-lookup"><span data-stu-id="d505b-155">The Dockerfile is placed in the root folder of your application or service.</span></span> <span data-ttu-id="d505b-156">Obsahuje příkazy, které informují Docker, jak nastavit a spustit vaši aplikaci nebo službu v kontejneru.</span><span class="sxs-lookup"><span data-stu-id="d505b-156">It contains the commands that tell Docker how to set up and run your application or service in a container.</span></span> <span data-ttu-id="d505b-157">Můžete ručně vytvořit souboru Dockerfile v kódu a přidat ho do svého projektu společně s vašimi závislostmi .NET.</span><span class="sxs-lookup"><span data-stu-id="d505b-157">You can manually create a Dockerfile in code and add it to your project along with your .NET dependencies.</span></span>

<span data-ttu-id="d505b-158">Pomocí sady Visual Studio a jejích nástrojů pro Docker Tato úloha vyžaduje jenom několik kliknutí myší.</span><span class="sxs-lookup"><span data-stu-id="d505b-158">With Visual Studio and its tools for Docker, this task requires only a few mouse clicks.</span></span> <span data-ttu-id="d505b-159">Při vytváření nového projektu v aplikaci Visual Studio 2017 existuje možnost s názvem **Povolit podporu kontejneru (Docker)** , jak je znázorněno na obrázku 5-3.</span><span class="sxs-lookup"><span data-stu-id="d505b-159">When you create a new project in Visual Studio 2017, there's an option named **Enable Container (Docker) Support**, as shown in Figure 5-3.</span></span>

![Snímek obrazovky, který ukazuje zaškrtávací políčko Povolit podporu Docker.](./media/docker-app-development-workflow/enable-docker-support-check-box.png)

<span data-ttu-id="d505b-161">**Obrázek 5-3**.</span><span class="sxs-lookup"><span data-stu-id="d505b-161">**Figure 5-3**.</span></span> <span data-ttu-id="d505b-162">Povolení podpory Docker při vytváření nového projektu ASP.NET Core v aplikaci Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="d505b-162">Enabling Docker Support when creating a new ASP.NET Core project in Visual Studio 2017</span></span>

<span data-ttu-id="d505b-163">Podporu Docker můžete povolit také pro existující projekt ASP.NET Core webové aplikace tak, že pravým tlačítkem myši kliknete na projekt v **Průzkumník řešení** a vyberete **Přidat** > **podporu Docker**, jak je znázorněno na obrázku 5-4.</span><span class="sxs-lookup"><span data-stu-id="d505b-163">You can also enable Docker support on an existing ASP.NET Core web app project by right-clicking the project in **Solution Explorer** and selecting **Add** > **Docker Support**, as shown in Figure 5-4.</span></span>

![Snímek obrazovky s možností podpora Docker v nabídce Přidat](./media/docker-app-development-workflow/add-docker-support-option.png)

<span data-ttu-id="d505b-165">**Obrázek 5-4**.</span><span class="sxs-lookup"><span data-stu-id="d505b-165">**Figure 5-4**.</span></span> <span data-ttu-id="d505b-166">Povolení podpory Docker v existujícím projektu sady Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="d505b-166">Enabling Docker support in an existing Visual Studio 2017 project</span></span>

<span data-ttu-id="d505b-167">Tato akce přidá do projektu *souboru Dockerfile* s požadovanou konfigurací a je k dispozici pouze pro ASP.NET Core projekty.</span><span class="sxs-lookup"><span data-stu-id="d505b-167">This action adds a *Dockerfile* to the project with the required configuration, and is only available on ASP.NET Core projects.</span></span>

<span data-ttu-id="d505b-168">Podobným způsobem může Visual Studio také přidat soubor Docker-Compose. yml pro celé řešení s možností **přidat > kontejner Orchestrator support**.</span><span class="sxs-lookup"><span data-stu-id="d505b-168">In a similar fashion, Visual Studio can also add a docker-compose.yml file for the whole solution with the option **Add > Container Orchestrator Support**.</span></span> <span data-ttu-id="d505b-169">V kroku 4 si tuto možnost podrobněji prozkoumáme.</span><span class="sxs-lookup"><span data-stu-id="d505b-169">In step 4, we'll explore this option in greater detail.</span></span>

### <a name="using-an-existing-official-net-docker-image"></a><span data-ttu-id="d505b-170">Použití stávající oficiální image rozhraní .NET Docker</span><span class="sxs-lookup"><span data-stu-id="d505b-170">Using an existing official .NET Docker image</span></span>

<span data-ttu-id="d505b-171">Obvykle vytvoříte vlastní image pro kontejner nad základní imagí, kterou získáte z oficiálního úložiště, jako je registr [Docker Hub](https://hub.docker.com/) .</span><span class="sxs-lookup"><span data-stu-id="d505b-171">You usually build a custom image for your container on top of a base image you get from an official repository like the [Docker Hub](https://hub.docker.com/) registry.</span></span> <span data-ttu-id="d505b-172">To je přesně to, co se stane v rámci pokrývání, když povolíte podporu Docker v aplikaci Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d505b-172">That is precisely what happens under the covers when you enable Docker support in Visual Studio.</span></span> <span data-ttu-id="d505b-173">Vaše souboru Dockerfile bude používat existující image `aspnetcore`.</span><span class="sxs-lookup"><span data-stu-id="d505b-173">Your Dockerfile will use an existing `aspnetcore` image.</span></span>

<span data-ttu-id="d505b-174">Dříve jsme zjistili, které image a úložiště Docker můžete použít v závislosti na zvoleném rozhraní a operačním systému.</span><span class="sxs-lookup"><span data-stu-id="d505b-174">Earlier we explained which Docker images and repos you can use, depending on the framework and OS you have chosen.</span></span> <span data-ttu-id="d505b-175">Například pokud chcete použít ASP.NET Core (Linux nebo Windows), obrázek, který se má použít, je `mcr.microsoft.com/dotnet/core/aspnet:2.2`.</span><span class="sxs-lookup"><span data-stu-id="d505b-175">For instance, if you want to use ASP.NET Core (Linux or Windows), the image to use is `mcr.microsoft.com/dotnet/core/aspnet:2.2`.</span></span> <span data-ttu-id="d505b-176">Proto stačí určit, jakou základní image Docker budete pro svůj kontejner používat.</span><span class="sxs-lookup"><span data-stu-id="d505b-176">Therefore, you just need to specify what base Docker image you will use for your container.</span></span> <span data-ttu-id="d505b-177">Uděláte to tak, že do souboru Dockerfile přidáte `FROM mcr.microsoft.com/dotnet/core/aspnet:2.2`.</span><span class="sxs-lookup"><span data-stu-id="d505b-177">You do that by adding `FROM mcr.microsoft.com/dotnet/core/aspnet:2.2` to your Dockerfile.</span></span> <span data-ttu-id="d505b-178">To se automaticky provede v aplikaci Visual Studio, ale pokud byste chtěli verzi aktualizovat, aktualizujete tuto hodnotu.</span><span class="sxs-lookup"><span data-stu-id="d505b-178">This will be automatically performed by Visual Studio, but if you were to update the version, you update this value.</span></span>

<span data-ttu-id="d505b-179">Použití oficiálního úložiště imagí .NET z dokovacího centra s číslem verze zajišťuje, aby byly na všech počítačích dostupné stejné funkce jazyka (včetně vývoje, testování a produkčního prostředí).</span><span class="sxs-lookup"><span data-stu-id="d505b-179">Using an official .NET image repository from Docker Hub with a version number ensures that the same language features are available on all machines (including development, testing, and production).</span></span>

<span data-ttu-id="d505b-180">Následující příklad ukazuje vzorový souboru Dockerfile pro kontejner ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="d505b-180">The following example shows a sample Dockerfile for an ASP.NET Core container.</span></span>

```Dockerfile
FROM mcr.microsoft.com/dotnet/core/aspnet:2.2
ARG source
WORKDIR /app
EXPOSE 80
COPY ${source:-obj/Docker/publish} .
ENTRYPOINT ["dotnet", " MySingleContainerWebApp.dll "]
```

<span data-ttu-id="d505b-181">V tomto případě je image založená na verzi 2,2 oficiální image ASP.NET Core Docker (více imagí pro Linux a Windows).</span><span class="sxs-lookup"><span data-stu-id="d505b-181">In this case, the image is based on version 2.2 of the official ASP.NET Core Docker image (multi-arch for Linux and Windows).</span></span> <span data-ttu-id="d505b-182">Toto je nastavení `FROM mcr.microsoft.com/dotnet/core/aspnet:2.2`.</span><span class="sxs-lookup"><span data-stu-id="d505b-182">This is the setting `FROM mcr.microsoft.com/dotnet/core/aspnet:2.2`.</span></span> <span data-ttu-id="d505b-183">(Další informace o této základní imagi najdete na stránce s [obrázkem Docker .NET Core](https://hub.docker.com/_/microsoft-dotnet-core/) .) V souboru Dockerfile musíte také dát Docker pokyn, aby naslouchal na portu TCP, který budete používat při běhu (v tomto případě port 80, jak je nakonfigurovaný s nastavením zpřístupnit).</span><span class="sxs-lookup"><span data-stu-id="d505b-183">(For more information about this base image, see the [.NET Core Docker Image](https://hub.docker.com/_/microsoft-dotnet-core/) page.) In the Dockerfile, you also need to instruct Docker to listen on the TCP port you will use at runtime (in this case, port 80, as configured with the EXPOSE setting).</span></span>

<span data-ttu-id="d505b-184">V souboru Dockerfile můžete určit další nastavení konfigurace v závislosti na jazyku a rozhraní, které používáte.</span><span class="sxs-lookup"><span data-stu-id="d505b-184">You can specify additional configuration settings in the Dockerfile, depending on the language and framework you're using.</span></span> <span data-ttu-id="d505b-185">Například řádek ENTRYPOINT s `["dotnet", "MySingleContainerWebApp.dll"]` instruuje Docker ke spuštění aplikace .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d505b-185">For instance, the ENTRYPOINT line with `["dotnet", "MySingleContainerWebApp.dll"]` tells Docker to run a .NET Core application.</span></span> <span data-ttu-id="d505b-186">Pokud k sestavení a spuštění aplikace .NET používáte sadu SDK a .NET Core CLI (dotnet CLI), toto nastavení se liší.</span><span class="sxs-lookup"><span data-stu-id="d505b-186">If you're using the SDK and the .NET Core CLI (dotnet CLI) to build and run the .NET application, this setting would be different.</span></span> <span data-ttu-id="d505b-187">Dolním řádkem je, že se řádek ENTRYPOINT a další nastavení liší v závislosti na jazyku a platformě, kterou zvolíte pro vaši aplikaci.</span><span class="sxs-lookup"><span data-stu-id="d505b-187">The bottom line is that the ENTRYPOINT line and other settings will be different depending on the language and platform you choose for your application.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="d505b-188">Další materiály a zdroje informací</span><span class="sxs-lookup"><span data-stu-id="d505b-188">Additional resources</span></span>

- <span data-ttu-id="d505b-189">**Vytváření imagí Docker pro aplikace .NET Core** </span><span class="sxs-lookup"><span data-stu-id="d505b-189">**Building Docker Images for .NET Core Applications** </span></span>\
  [https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images](/aspnet/core/host-and-deploy/docker/building-net-docker-images)

- <span data-ttu-id="d505b-190">**Sestavte si vlastní image**.</span><span class="sxs-lookup"><span data-stu-id="d505b-190">**Build your own image**.</span></span> <span data-ttu-id="d505b-191">V oficiální dokumentaci k Docker. </span><span class="sxs-lookup"><span data-stu-id="d505b-191">In the official Docker documentation.</span></span>\
  <https://docs.docker.com/engine/tutorials/dockerimages/>

- <span data-ttu-id="d505b-192">**Udržování aktuálnosti imagí kontejnerů .net** </span><span class="sxs-lookup"><span data-stu-id="d505b-192">**Staying up-to-date with .NET Container Images** </span></span>\
  <https://devblogs.microsoft.com/dotnet/staying-up-to-date-with-net-container-images/>

- <span data-ttu-id="d505b-193">**Použití rozhraní .NET a Docker společně – DockerCon 2018 Update** </span><span class="sxs-lookup"><span data-stu-id="d505b-193">**Using .NET and Docker Together - DockerCon 2018 Update** </span></span>\
  <https://devblogs.microsoft.com/dotnet/using-net-and-docker-together-dockercon-2018-update/>

### <a name="using-multi-arch-image-repositories"></a><span data-ttu-id="d505b-194">Použití úložišť imagí s více archy</span><span class="sxs-lookup"><span data-stu-id="d505b-194">Using multi-arch image repositories</span></span>

<span data-ttu-id="d505b-195">Jedno úložiště může obsahovat varianty platformy, jako je například bitová kopie systému Linux a bitová kopie systému Windows.</span><span class="sxs-lookup"><span data-stu-id="d505b-195">A single repo can contain platform variants, such as a Linux image and a Windows image.</span></span> <span data-ttu-id="d505b-196">Tato funkce umožňuje dodavatelům, jako je Microsoft (základní tvůrci obrázků), vytvořit jedno úložiště pro pokrytí více platforem (které jsou Linux a Windows).</span><span class="sxs-lookup"><span data-stu-id="d505b-196">This feature allows vendors like Microsoft (base image creators) to create a single repo to cover multiple platforms (that is Linux and Windows).</span></span> <span data-ttu-id="d505b-197">Například úložiště [dotnet/Core](https://hub.docker.com/_/microsoft-dotnet-core/) dostupné v registru Docker Hub poskytuje podporu pro systémy Linux a Windows nano Server pomocí stejného názvu úložiště.</span><span class="sxs-lookup"><span data-stu-id="d505b-197">For example, the [dotnet/core](https://hub.docker.com/_/microsoft-dotnet-core/) repository available in the Docker Hub registry provides support for Linux and Windows Nano Server by using the same repo name.</span></span>

<span data-ttu-id="d505b-198">Pokud zadáte značku, cílící na platformu, která je explicitní, podobně jako v následujících případech:</span><span class="sxs-lookup"><span data-stu-id="d505b-198">If you specify a tag, targeting a platform that is explicit like in the following cases:</span></span>

- `microsoft/dotnet:2.2-aspnetcore-runtime-stretch-slim` \
  <span data-ttu-id="d505b-199">Cíle: modul runtime .NET Core 2,2 – pouze v systému Linux</span><span class="sxs-lookup"><span data-stu-id="d505b-199">Targets: .NET Core 2.2 runtime-only on Linux</span></span>

- `microsoft/dotnet:2.2-aspnetcore-runtime-nanoserver-1809` \
  <span data-ttu-id="d505b-200">Cíle: modul runtime .NET Core 2,2 – pouze v systému Windows nano Server</span><span class="sxs-lookup"><span data-stu-id="d505b-200">Targets: .NET Core 2.2 runtime-only on Windows Nano Server</span></span>

<span data-ttu-id="d505b-201">Pokud ale zadáte stejný název bitové kopie, a to i se stejnou značkou, používají se pro více imagí (jako je `aspnetcore` image) verze systému Linux nebo Windows, a to v závislosti na operačním systému hostitele Docker, který nasazujete, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="d505b-201">But, if you specify the same image name, even with the same tag, the multi-arch images (like the `aspnetcore` image) will use the Linux or Windows version depending on the Docker host OS you're deploying, as shown in the following example:</span></span>

- `microsoft/dotnet:2.2-aspnetcore-runtime` \
  <span data-ttu-id="d505b-202">Vícenásobný arch: rozhraní .NET Core 2,2 runtime – pouze v systémech Linux nebo Windows nano Server v závislosti na hostitelském operačním systému Docker</span><span class="sxs-lookup"><span data-stu-id="d505b-202">Multi-arch: .NET Core 2.2 runtime-only on Linux or Windows Nano Server depending on the Docker host OS</span></span>

<span data-ttu-id="d505b-203">Tímto způsobem načteme variantu systému Windows, když nasadíte image z hostitele Windows, vyžádá si variantu Windows a vyžádá si stejný název image z hostitele Linux.</span><span class="sxs-lookup"><span data-stu-id="d505b-203">This way, when you pull an image from a Windows host, it will pull the Windows variant, and pulling the same image name from a Linux host will pull the Linux variant.</span></span>

### <a name="multi-stage-builds-in-dockerfile"></a><span data-ttu-id="d505b-204">Sestavení s více fázemi v souboru Dockerfile</span><span class="sxs-lookup"><span data-stu-id="d505b-204">Multi-stage builds in Dockerfile</span></span>

<span data-ttu-id="d505b-205">Souboru Dockerfile je podobný dávkovému skriptu.</span><span class="sxs-lookup"><span data-stu-id="d505b-205">The Dockerfile is similar to a batch script.</span></span> <span data-ttu-id="d505b-206">Podobně jako v případě, že jste museli nastavit počítač z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="d505b-206">Similar to what you would do if you had to set up the machine from the command line.</span></span>

<span data-ttu-id="d505b-207">Začíná základní imagí, která nastavuje počáteční kontext, jako spouštěcí systém souborů, který je umístěný na hostitelském operačním systému.</span><span class="sxs-lookup"><span data-stu-id="d505b-207">It starts with a base image that sets up the initial context, it's like the startup filesystem, that sits on top of the host OS.</span></span> <span data-ttu-id="d505b-208">Nejedná se o operační systém, ale můžete si ho představit jako "operační systém uvnitř kontejneru".</span><span class="sxs-lookup"><span data-stu-id="d505b-208">It's not an OS, but you can think of it like "the" OS inside the container.</span></span>

<span data-ttu-id="d505b-209">Spuštění každého příkazového řádku vytvoří v systému souborů novou vrstvu se změnami z předchozí verze, takže v případě kombinace vyprodukuje výsledný systém souborů.</span><span class="sxs-lookup"><span data-stu-id="d505b-209">The execution of every command line creates a new layer on the filesystem with the changes from the previous one, so that, when combined, produce the resulting filesystem.</span></span>

<span data-ttu-id="d505b-210">Vzhledem k tomu, že všechny nové vrstvy "jsou" na začátku a výslednou velikost obrazu se zvětšují s každým příkazem, obrázky můžou být velmi velké, pokud je potřeba je zahrnout, například sada SDK potřebná k sestavení a publikování aplikace.</span><span class="sxs-lookup"><span data-stu-id="d505b-210">Since every new layer "rests" on top of the previous one and the resulting image size increases with every command, images can get very large if they have to include, for example, the SDK needed to build and publish an application.</span></span>

<span data-ttu-id="d505b-211">Toto je místo, kde se sestavení s více fázemi dostanou do grafu (od Docker 17,05 a vyšší), aby se dosáhlo svého Magic.</span><span class="sxs-lookup"><span data-stu-id="d505b-211">This is where multi-stage builds get into the plot (from Docker 17.05 and higher) to do their magic.</span></span>

<span data-ttu-id="d505b-212">Základní nápad je, že můžete oddělit proces spuštění souboru Dockerfile ve fázích, kde fáze je počáteční obrázek následovaný jedním nebo více příkazy a poslední fáze určuje konečnou velikost obrázku.</span><span class="sxs-lookup"><span data-stu-id="d505b-212">The core idea is that you can separate the Dockerfile execution process in stages, where a stage is an initial image followed by one or more commands, and the last stage determines the final image size.</span></span>

<span data-ttu-id="d505b-213">V krátkém buildu s více fázemi umožňuje rozdělit vytváření v různých fázích a potom sestavit konečný obraz, který převezme pouze relevantní adresáře z mezilehlé fáze.</span><span class="sxs-lookup"><span data-stu-id="d505b-213">In short, multi-stage builds allow splitting the creation in different "phases" and then assemble the final image taking only the relevant directories from the intermediate stages.</span></span> <span data-ttu-id="d505b-214">Obecnou strategií pro použití této funkce je:</span><span class="sxs-lookup"><span data-stu-id="d505b-214">The general strategy to use this feature is:</span></span>

1. <span data-ttu-id="d505b-215">Použijte základní image sady SDK (nezáleží na tom, jak velká) se všemi potřebnými k sestavování a publikování aplikace do složky a potom</span><span class="sxs-lookup"><span data-stu-id="d505b-215">Use a base SDK image (doesn't matter how large), with everything needed to build and publish the application to a folder and then</span></span>

2. <span data-ttu-id="d505b-216">Použijte základní bitovou kopii pouze za běhu a zkopírujte složku pro publikování z předchozí fáze, aby se vytvořila nízká finální bitová kopie.</span><span class="sxs-lookup"><span data-stu-id="d505b-216">Use a base, small, runtime-only image and copy the publishing folder from the previous stage to produce a small final image.</span></span>

<span data-ttu-id="d505b-217">Nejlepším způsobem, jak porozumět více fázím, je souboru Dockerfile detailně, řádek po řádku, takže pojďme začít s počátečními souboru Dockerfile vytvořenými sadou Visual Studio při přidání podpory Docker do projektu a později se dostanete k optimalizaci.</span><span class="sxs-lookup"><span data-stu-id="d505b-217">Probably the best way to understand multi-stage is going through a Dockerfile in detail, line by line, so let's begin with the initial Dockerfile created by Visual Studio when adding Docker support to a project and will get into some optimizations later.</span></span>

<span data-ttu-id="d505b-218">Počáteční souboru Dockerfile by měl vypadat nějak takto:</span><span class="sxs-lookup"><span data-stu-id="d505b-218">The initial Dockerfile might look something like this:</span></span>

```Dockerfile
 1  FROM mcr.microsoft.com/dotnet/core/aspnet:2.2 AS base
 2  WORKDIR /app
 3  EXPOSE 80
 4
 5  FROM mcr.microsoft.com/dotnet/core/sdk:2.2 AS build
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

<span data-ttu-id="d505b-219">A jsou to podrobnosti, řádek po řádku:</span><span class="sxs-lookup"><span data-stu-id="d505b-219">And these are the details, line by line:</span></span>

- <span data-ttu-id="d505b-220">**#1 řádku:** Zahajte fázi s "malým" pouze modulem runtime základní image, zavolejte **základ** pro referenci.</span><span class="sxs-lookup"><span data-stu-id="d505b-220">**Line #1:** Begin a stage with a "small" runtime-only base image, call it **base** for reference.</span></span>

- <span data-ttu-id="d505b-221">**#2 řádku:** Vytvořte v imagi adresář **/App** .</span><span class="sxs-lookup"><span data-stu-id="d505b-221">**Line #2:** Create the **/app** directory in the image.</span></span>

- <span data-ttu-id="d505b-222">**#3 řádku:** Vystavte port **80**.</span><span class="sxs-lookup"><span data-stu-id="d505b-222">**Line #3:** Expose port **80**.</span></span>

- <span data-ttu-id="d505b-223">**#5 řádku:** Zahajte novou fázi s imagí "Velká" pro vytváření a publikování.</span><span class="sxs-lookup"><span data-stu-id="d505b-223">**Line #5:** Begin a new stage with the "large" image for building/publishing.</span></span> <span data-ttu-id="d505b-224">Pro referenci zavolejte **sestavení** IT.</span><span class="sxs-lookup"><span data-stu-id="d505b-224">Call it **build** for reference.</span></span>

- <span data-ttu-id="d505b-225">**#6 řádku:** Vytvořte v imagi adresář **/Src** .</span><span class="sxs-lookup"><span data-stu-id="d505b-225">**Line #6:** Create directory **/src** in the image.</span></span>

- <span data-ttu-id="d505b-226">**#7 řádku:** Až na řádek 16, zkopírujte odkazované soubory projektu **. csproj** , abyste mohli balíčky později obnovit.</span><span class="sxs-lookup"><span data-stu-id="d505b-226">**Line #7:** Up to line 16, copy referenced **.csproj** project files to be able to restore packages later.</span></span>

- <span data-ttu-id="d505b-227">**#17 řádku:** Obnovte balíčky pro projekt **Catalog. API** a odkazované projekty.</span><span class="sxs-lookup"><span data-stu-id="d505b-227">**Line #17:** Restore packages for the **Catalog.API** project and the referenced projects.</span></span>

- <span data-ttu-id="d505b-228">**#18 řádku:** Zkopírujte **všechny adresářové stromové struktury pro řešení** (kromě souborů/adresářů obsažených v souboru **. dockerignore** ) do adresáře **/Src** v imagi.</span><span class="sxs-lookup"><span data-stu-id="d505b-228">**Line #18:** Copy **all directory tree for the solution** (except the files/directories included in the **.dockerignore** file) to the **/src** directory in the image.</span></span>

- <span data-ttu-id="d505b-229">**#19 řádku:** Změňte aktuální složku na projekt **Catalog. API** .</span><span class="sxs-lookup"><span data-stu-id="d505b-229">**Line #19:** Change the current folder to the **Catalog.API** project.</span></span>

- <span data-ttu-id="d505b-230">**#20 řádku:** Sestavte projekt (a další závislosti projektu) a výstup do adresáře **/App** v imagi.</span><span class="sxs-lookup"><span data-stu-id="d505b-230">**Line #20:** Build the project (and other project dependencies) and output to the **/app** directory in the image.</span></span>

- <span data-ttu-id="d505b-231">**#22 řádku:** Zahajte pokračování nové fáze ze sestavení.</span><span class="sxs-lookup"><span data-stu-id="d505b-231">**Line #22:** Begin a new stage continuing from the build.</span></span> <span data-ttu-id="d505b-232">Pro referenci zavolejte **publikování** .</span><span class="sxs-lookup"><span data-stu-id="d505b-232">Call it **publish** for reference.</span></span>

- <span data-ttu-id="d505b-233">**#23 řádku:** Publikujte projekt (a závislosti) a výstup do adresáře **/App** v imagi.</span><span class="sxs-lookup"><span data-stu-id="d505b-233">**Line #23:** Publish the project (and dependencies) and output to the **/app** directory in the image.</span></span>

- <span data-ttu-id="d505b-234">**#25 řádku:** Začněte novou fázi od **základu** a zavolejte ji **finální**.</span><span class="sxs-lookup"><span data-stu-id="d505b-234">**Line #25:** Begin a new stage continuing from **base** and call it **final**.</span></span>

- <span data-ttu-id="d505b-235">**#26 řádku:** Změňte aktuální adresář na **/App**.</span><span class="sxs-lookup"><span data-stu-id="d505b-235">**Line #26:** Change the current directory to **/app**.</span></span>

- <span data-ttu-id="d505b-236">**#27 řádku:** Zkopírujte adresář **/App** z fáze **publikovat** do aktuálního adresáře.</span><span class="sxs-lookup"><span data-stu-id="d505b-236">**Line #27:** Copy the **/app** directory from stage **publish** to the current directory.</span></span>

- <span data-ttu-id="d505b-237">**#28 řádku:** Zadejte příkaz, který se má spustit při spuštění kontejneru.</span><span class="sxs-lookup"><span data-stu-id="d505b-237">**Line #28:** Define the command to run when the container is started.</span></span>

<span data-ttu-id="d505b-238">Nyní se podívejme na několik optimalizací, které vám pomůžou zlepšit výkon celého procesu, který v případě eShopOnContainers znamená přibližně 22 minut nebo více pro sestavení kompletního řešení v kontejnerech Linux.</span><span class="sxs-lookup"><span data-stu-id="d505b-238">Now let's explore some optimizations to improve the whole process performance that, in the case of eShopOnContainers, means about 22 minutes or more to build the complete solution in Linux containers.</span></span>

<span data-ttu-id="d505b-239">Budete využívat výhod funkce mezipaměti Docker, která je poměrně jednoduchá: Pokud je základní image a příkazy stejné jako u dříve spuštěných, může ji použít jenom výslednou vrstvu bez nutnosti spouštět příkazy, takže se ušetří nějaký čas.</span><span class="sxs-lookup"><span data-stu-id="d505b-239">You'll take advantage of Docker's layer cache feature, which is quite simple: if the base image and the commands are the same as some previously executed, it can just use the resulting layer without the need to execute the commands, thus saving some time.</span></span>

<span data-ttu-id="d505b-240">Proto se zaměřte na fázi **sestavení** , řádky 5-6 jsou většinou stejné, ale řádky 7-17 jsou pro každou službu z eShopOnContainers odlišné, takže je nutné je spustit vždy, když jste změnili řádky 7-16 na:</span><span class="sxs-lookup"><span data-stu-id="d505b-240">So, let's focus on the **build** stage, lines 5-6 are mostly the same, but lines 7-17 are different for every service from eShopOnContainers, so they have to execute every single time, however if you changed lines 7-16 to:</span></span>

```Dockerfile
COPY . .
```

<span data-ttu-id="d505b-241">Pak by byl stejný jako u každé služby, mohl by zkopírovat celé řešení a vytvořit větší vrstvu, ale:</span><span class="sxs-lookup"><span data-stu-id="d505b-241">Then it would be just the same for every service, it would copy the whole solution and would create a larger layer but:</span></span>

1. <span data-ttu-id="d505b-242">Proces kopírování se spustí jenom poprvé (a když se znovu sestaví při změně souboru) a použije mezipaměť pro všechny ostatní služby.</span><span class="sxs-lookup"><span data-stu-id="d505b-242">The copy process would only be executed the first time (and when rebuilding if a file is changed) and would use the cache for all other services and</span></span>

2. <span data-ttu-id="d505b-243">Vzhledem k tomu, že větší obrázek probíhá v mezilehlé fázi, nemá vliv na konečnou velikost obrázku.</span><span class="sxs-lookup"><span data-stu-id="d505b-243">Since the larger image occurs in an intermediate stage it, doesn't affect the final image size.</span></span>

<span data-ttu-id="d505b-244">Další významná optimalizace zahrnuje příkaz `restore` provedený na řádku 17, který je také pro každou službu eShopOnContainers odlišný.</span><span class="sxs-lookup"><span data-stu-id="d505b-244">The next significant optimization involves the `restore` command executed in line 17, which is also different for every service of eShopOnContainers.</span></span> <span data-ttu-id="d505b-245">Pokud tento řádek změníte jenom na:</span><span class="sxs-lookup"><span data-stu-id="d505b-245">If you change that line to just:</span></span>

```Dockerfile
RUN dotnet restore
```

<span data-ttu-id="d505b-246">To by obnovilo balíčky pro celé řešení, ale pak to udělá znovu jenom jednou, a to v rámci aktuální strategie za 15 krát.</span><span class="sxs-lookup"><span data-stu-id="d505b-246">It would restore the packages for the whole solution, but then again, it would do it just once, instead of the 15 times with the current strategy.</span></span>

<span data-ttu-id="d505b-247">`dotnet restore` se ale spustí jenom v případě, že je ve složce jeden soubor projektu nebo řešení, takže je to trochu složitější a způsob, jak ho vyřešit, aniž by bylo možné získat příliš mnoho podrobností:</span><span class="sxs-lookup"><span data-stu-id="d505b-247">However, `dotnet restore` only runs if there's a single project or solution file in the folder, so achieving this is a bit more complicated and the way to solve it, without getting into too many details, is this:</span></span>

1. <span data-ttu-id="d505b-248">Přidejte následující řádky do **. dockerignore**:</span><span class="sxs-lookup"><span data-stu-id="d505b-248">Add the following lines to **.dockerignore**:</span></span>

   - <span data-ttu-id="d505b-249">`*.sln`pro ignorování všech souborů řešení ve stromu hlavní složky</span><span class="sxs-lookup"><span data-stu-id="d505b-249">`*.sln`, to ignore all solution files in the main folder tree</span></span>

   - <span data-ttu-id="d505b-250">`!eShopOnContainers-ServicesAndWebApps.sln`, chcete-li zahrnout pouze tento soubor řešení.</span><span class="sxs-lookup"><span data-stu-id="d505b-250">`!eShopOnContainers-ServicesAndWebApps.sln`, to include only this solution file.</span></span>

2. <span data-ttu-id="d505b-251">Do `dotnet restore`zahrňte argument `/ignoreprojectextensions:.dcproj`, takže se taky ignoruje projekt Docker-Resolution a obnoví se jenom balíčky pro řešení eShopOnContainers-ServicesAndWebApps.</span><span class="sxs-lookup"><span data-stu-id="d505b-251">Include the `/ignoreprojectextensions:.dcproj` argument to `dotnet restore`, so it also ignores the docker-compose project and only restores the packages for the eShopOnContainers-ServicesAndWebApps solution.</span></span>

<span data-ttu-id="d505b-252">Pro konečnou optimalizaci se k tomu dochází pouze v případě, že řádek 20 je redundantní, protože řádek 23 také sestaví aplikaci a v podstatě je hned po řádku 20, takže existuje další časově náročný příkaz.</span><span class="sxs-lookup"><span data-stu-id="d505b-252">For the final optimization, it just happens that line 20 is redundant, as line 23 also builds the application and comes, in essence, right after line 20, so there goes another time-consuming command.</span></span>

<span data-ttu-id="d505b-253">Výsledný soubor je pak:</span><span class="sxs-lookup"><span data-stu-id="d505b-253">The resulting file is then:</span></span>

```Dockerfile
 1  FROM mcr.microsoft.com/dotnet/core/aspnet:2.2 AS base
 2  WORKDIR /app
 3  EXPOSE 80
 4
 5  FROM mcr.microsoft.com/dotnet/core/sdk:2.2 AS publish
 6  WORKDIR /src
 7  COPY . .
 8  RUN dotnet restore /ignoreprojectextensions:.dcproj
 9  WORKDIR /src/src/Services/Catalog/Catalog.API
10  RUN dotnet publish Catalog.API.csproj -c Release -0 /app
11
12  FROM base AS final
13  WORKDIR /app
14  COPY --from=publish /app
15  ENTRYPOINT ["dotnet", "Catalog.API.dll"]
```

### <a name="creating-your-base-image-from-scratch"></a><span data-ttu-id="d505b-254">Vytváření základní Image od začátku</span><span class="sxs-lookup"><span data-stu-id="d505b-254">Creating your base image from scratch</span></span>

<span data-ttu-id="d505b-255">Můžete vytvořit vlastní základní image Docker od začátku.</span><span class="sxs-lookup"><span data-stu-id="d505b-255">You can create your own Docker base image from scratch.</span></span> <span data-ttu-id="d505b-256">Tento scénář se nedoporučuje pro někoho, kdo začíná s Docker, ale pokud chcete nastavit konkrétní bity vlastní základní image, můžete to udělat.</span><span class="sxs-lookup"><span data-stu-id="d505b-256">This scenario is not recommended for someone who is starting with Docker, but if you want to set the specific bits of your own base image, you can do so.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="d505b-257">Další materiály a zdroje informací</span><span class="sxs-lookup"><span data-stu-id="d505b-257">Additional resources</span></span>

- <span data-ttu-id="d505b-258">**Vícevrstvé image .NET Core**. </span><span class="sxs-lookup"><span data-stu-id="d505b-258">**Multi-arch .NET Core images**.</span></span>\
  <https://github.com/dotnet/announcements/issues/14>

- <span data-ttu-id="d505b-259">**Vytvoří základní image**.</span><span class="sxs-lookup"><span data-stu-id="d505b-259">**Create a base image**.</span></span> <span data-ttu-id="d505b-260">Oficiální dokumentace k Docker. </span><span class="sxs-lookup"><span data-stu-id="d505b-260">Official Docker documentation.</span></span>\
  <https://docs.docker.com/develop/develop-images/baseimages/>

![Obrázek pro krok 3](./media/docker-app-development-workflow/step-3-create-dockerfile-defined-images.png)

## <a name="step-3-create-your-custom-docker-images-and-embed-your-application-or-service-in-them"></a><span data-ttu-id="d505b-262">Krok 3:</span><span class="sxs-lookup"><span data-stu-id="d505b-262">Step 3.</span></span> <span data-ttu-id="d505b-263">Vytvořte vlastní image Docker a vložte do nich svou aplikaci nebo službu.</span><span class="sxs-lookup"><span data-stu-id="d505b-263">Create your custom Docker images and embed your application or service in them</span></span>

<span data-ttu-id="d505b-264">Pro každou službu ve vaší aplikaci je potřeba vytvořit související image.</span><span class="sxs-lookup"><span data-stu-id="d505b-264">For each service in your application, you need to create a related image.</span></span> <span data-ttu-id="d505b-265">Pokud se vaše aplikace skládá z jediné služby nebo webové aplikace, stačí pouze jeden obrázek.</span><span class="sxs-lookup"><span data-stu-id="d505b-265">If your application is made up of a single service or web application, you just need a single image.</span></span>

<span data-ttu-id="d505b-266">Všimněte si, že image Docker jsou sestaveny automaticky pro vás v aplikaci Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d505b-266">Note that the Docker images are built automatically for you in Visual Studio.</span></span> <span data-ttu-id="d505b-267">Následující postup je nutný jenom pro pracovní postup Editor/CLI a vysvětluje, co se děje pod.</span><span class="sxs-lookup"><span data-stu-id="d505b-267">The following steps are only needed for the editor/CLI workflow and explained for clarity about what happens underneath.</span></span>

<span data-ttu-id="d505b-268">Jako vývojář budete potřebovat místní vývoj a testování, dokud nenainstalujete dokončenou funkci nebo nezměníte systém správy zdrojového kódu (například na GitHub).</span><span class="sxs-lookup"><span data-stu-id="d505b-268">You, as a developer, need to develop and test locally until you push a completed feature or change to your source control system (for example, to GitHub).</span></span> <span data-ttu-id="d505b-269">To znamená, že potřebujete vytvořit image Docker a nasazovat kontejnery na místního hostitele Docker (virtuální počítač se systémem Windows nebo Linux) a spouštět, testovat a ladit tyto místní kontejnery.</span><span class="sxs-lookup"><span data-stu-id="d505b-269">This means that you need to create the Docker images and deploy containers to a local Docker host (Windows or Linux VM) and run, test, and debug against those local containers.</span></span>

<span data-ttu-id="d505b-270">Pokud chcete vytvořit vlastní image v místním prostředí pomocí rozhraní Docker CLI a svého souboru Dockerfile, můžete použít příkaz Docker Build, jak je znázorněno na obrázku 5-5.</span><span class="sxs-lookup"><span data-stu-id="d505b-270">To create a custom image in your local environment by using Docker CLI and your Dockerfile, you can use the docker build command, as in Figure 5-5.</span></span>

![Snímek obrazovky znázorňující výstup konzoly příkazu Docker Build](./media/docker-app-development-workflow/run-docker-build-command.png)

<span data-ttu-id="d505b-272">**Obrázek 5-5**.</span><span class="sxs-lookup"><span data-stu-id="d505b-272">**Figure 5-5**.</span></span> <span data-ttu-id="d505b-273">Vytvoření vlastní image Docker</span><span class="sxs-lookup"><span data-stu-id="d505b-273">Creating a custom Docker image</span></span>

<span data-ttu-id="d505b-274">Místo toho, aby bylo možné přímo spustit sestavení Docker ze složky projektu, můžete nejprve vygenerovat složku nasaditelné pomocí požadovaných knihoven a binárních souborů .NET spuštěním `dotnet publish`a potom použít příkaz `docker build`.</span><span class="sxs-lookup"><span data-stu-id="d505b-274">Optionally, instead of directly running docker build from the project folder, you can first generate a deployable folder with the required .NET libraries and binaries by running `dotnet publish`, and then use the `docker build` command.</span></span>

<span data-ttu-id="d505b-275">Tím se vytvoří obrázek Docker s názvem `cesardl/netcore-webapi-microservice-docker:first`.</span><span class="sxs-lookup"><span data-stu-id="d505b-275">This will create a Docker image with the name `cesardl/netcore-webapi-microservice-docker:first`.</span></span> <span data-ttu-id="d505b-276">V tomto případě: první je značka reprezentující konkrétní verzi.</span><span class="sxs-lookup"><span data-stu-id="d505b-276">In this case, :first is a tag representing a specific version.</span></span> <span data-ttu-id="d505b-277">Tento krok můžete opakovat pro každou vlastní bitovou kopii, kterou potřebujete vytvořit pro svoji sestavenou aplikaci Docker.</span><span class="sxs-lookup"><span data-stu-id="d505b-277">You can repeat this step for each custom image you need to create for your composed Docker application.</span></span>

<span data-ttu-id="d505b-278">Pokud je aplikace vytvořena více kontejnerů (tj. jde o vícevláknovou aplikaci), můžete také použít příkaz `docker-compose up --build` k sestavení všech souvisejících imagí s jediným příkazem pomocí metadat zveřejněných v souvisejících souborech Docker-Compose. yml.</span><span class="sxs-lookup"><span data-stu-id="d505b-278">When an application is made of multiple containers (that is, it is a multi-container application), you can also use the `docker-compose up --build` command to build all the related images with a single command by using the metadata exposed in the related docker-compose.yml files.</span></span>

<span data-ttu-id="d505b-279">Existující image můžete najít v místním úložišti pomocí příkazu Docker images, jak je znázorněno na obrázku 5-6.</span><span class="sxs-lookup"><span data-stu-id="d505b-279">You can find the existing images in your local repository by using the docker images command, as shown in Figure 5-6.</span></span>

![Výstup z konzoly z příkazu Docker images zobrazující existující image](./media/docker-app-development-workflow/view-existing-images-with-docker-images.png)

<span data-ttu-id="d505b-281">**Obrázek 5-6.**</span><span class="sxs-lookup"><span data-stu-id="d505b-281">**Figure 5-6.**</span></span> <span data-ttu-id="d505b-282">Zobrazení existujících imagí pomocí příkazu Docker images</span><span class="sxs-lookup"><span data-stu-id="d505b-282">Viewing existing images using the docker images command</span></span>

### <a name="creating-docker-images-with-visual-studio"></a><span data-ttu-id="d505b-283">Vytváření imagí Docker pomocí sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="d505b-283">Creating Docker images with Visual Studio</span></span>

<span data-ttu-id="d505b-284">Když použijete Visual Studio k vytvoření projektu s podporou Docker, nevytvoříte explicitně image.</span><span class="sxs-lookup"><span data-stu-id="d505b-284">When you use Visual Studio to create a project with Docker support, you don't explicitly create an image.</span></span> <span data-ttu-id="d505b-285">Místo toho se obrázek vytvoří, když stisknete klávesu **F5** (nebo **CTRL-F5**) a spustíte aplikaci dockerized nebo službu.</span><span class="sxs-lookup"><span data-stu-id="d505b-285">Instead, the image is created for you when you press **F5** (or **Ctrl-F5**) to run the dockerized application or service.</span></span> <span data-ttu-id="d505b-286">Tento krok je automaticky v aplikaci Visual Studio a neuvidíte, že k tomu dochází, ale je důležité, abyste věděli, co se děje pod.</span><span class="sxs-lookup"><span data-stu-id="d505b-286">This step is automatic in Visual Studio and you won't see it happen, but it's important that you know what's going on underneath.</span></span>

![Obrázek pro volitelný krok 4](./media/docker-app-development-workflow/step-4-define-services-docker-compose-yml.png)

## <a name="step-4-define-your-services-in-docker-composeyml-when-building-a-multi-container-docker-application"></a><span data-ttu-id="d505b-288">Krok 4.</span><span class="sxs-lookup"><span data-stu-id="d505b-288">Step 4.</span></span> <span data-ttu-id="d505b-289">Definování služeb v Docker-Compose. yml při sestavování aplikace Docker s více kontejnery</span><span class="sxs-lookup"><span data-stu-id="d505b-289">Define your services in docker-compose.yml when building a multi-container Docker application</span></span>

<span data-ttu-id="d505b-290">Soubor [Docker-Compose. yml](https://docs.docker.com/compose/compose-file/) umožňuje definovat sadu souvisejících služeb, které mají být nasazeny jako složená aplikace s příkazy pro nasazení.</span><span class="sxs-lookup"><span data-stu-id="d505b-290">The [docker-compose.yml](https://docs.docker.com/compose/compose-file/) file lets you define a set of related services to be deployed as a composed application with deployment commands.</span></span> <span data-ttu-id="d505b-291">Také nakonfiguruje vztahy závislosti a konfiguraci runtime.</span><span class="sxs-lookup"><span data-stu-id="d505b-291">It also configures its dependency relations and run-time configuration.</span></span>

<span data-ttu-id="d505b-292">Chcete-li použít soubor Docker-Compose. yml, je třeba vytvořit soubor ve složce hlavního nebo kořenového řešení s obsahem podobným v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="d505b-292">To use a docker-compose.yml file, you need to create the file in your main or root solution folder, with content similar to that in the following example:</span></span>

```yml
version: '3.4'

services:

  webmvc:
    image: eshop/web
    environment:
      - CatalogUrl=http://catalog.api
      - OrderingUrl=http://ordering.api
    ports:
      - "80:80"
    depends_on:
      - catalog.api
      - ordering.api

  catalog.api:
    image: eshop/catalog.api
    environment:
      - ConnectionString=Server=sql.data;Port=1433;Database=CatalogDB;…
    ports:
      - "81:80"
    depends_on:
      - sql.data

  ordering.api:
    image: eshop/ordering.api
    environment:
      - ConnectionString=Server=sql.data;Database=OrderingDb;…
    ports:
      - "82:80"
    extra_hosts:
      - "CESARDLBOOKVHD:10.0.75.1"
    depends_on:
      - sql.data

  sql.data:
    image: mssql-server-linux:latest
    environment:
      - SA_PASSWORD=Pass@word
      - ACCEPT_EULA=Y
    ports:
      - "5433:1433"
```

<span data-ttu-id="d505b-293">Tento soubor Docker-Compose. yml je zjednodušená a Sloučená verze.</span><span class="sxs-lookup"><span data-stu-id="d505b-293">This docker-compose.yml file is a simplified and merged version.</span></span> <span data-ttu-id="d505b-294">Obsahuje statická konfigurační data pro každý kontejner (jako je název vlastní image), který je vždy vyžadován, a informace o konfiguraci, které mohou být závislé na prostředí nasazení, jako je například připojovací řetězec.</span><span class="sxs-lookup"><span data-stu-id="d505b-294">It contains static configuration data for each container (like the name of the custom image), which is always required, and configuration information that might depend on the deployment environment, like the connection string.</span></span> <span data-ttu-id="d505b-295">V dalších částech se dozvíte, jak rozdělit konfiguraci Docker-Compose. yml do více souborů Docker – pro vytváření souborů a přepis hodnot v závislosti na prostředí a typu spuštění (ladění nebo vydání).</span><span class="sxs-lookup"><span data-stu-id="d505b-295">In later sections, you will learn how to split the docker-compose.yml configuration into multiple docker-compose files and override values depending on the environment and execution type (debug or release).</span></span>

<span data-ttu-id="d505b-296">Příklad souboru Docker-Compose. yml definuje čtyři služby: služba `webmvc` (webová aplikace), dvě mikroslužby (`ordering.api` a `basket.api`) a jeden kontejner zdrojů dat `sql.data`, na základě SQL Server pro Linux běžící jako kontejner.</span><span class="sxs-lookup"><span data-stu-id="d505b-296">The docker-compose.yml file example defines four services: the `webmvc` service (a web application), two microservices (`ordering.api` and `basket.api`), and one data source container, `sql.data`, based on SQL Server for Linux running as a container.</span></span> <span data-ttu-id="d505b-297">Každá služba bude nasazena jako kontejner, takže se pro každý z nich vyžaduje image Docker.</span><span class="sxs-lookup"><span data-stu-id="d505b-297">Each service will be deployed as a container, so a Docker image is required for each.</span></span>

<span data-ttu-id="d505b-298">Soubor Docker-Compose. yml určuje nejen to, jaké kontejnery jsou používány, ale jak jsou konfigurovány samostatně.</span><span class="sxs-lookup"><span data-stu-id="d505b-298">The docker-compose.yml file specifies not only what containers are being used, but how they are individually configured.</span></span> <span data-ttu-id="d505b-299">Například definice kontejneru `webmvc` v souboru. yml:</span><span class="sxs-lookup"><span data-stu-id="d505b-299">For instance, the `webmvc` container definition in the .yml file:</span></span>

- <span data-ttu-id="d505b-300">Používá předem sestavenou bitovou kopii `eshop/web:latest`.</span><span class="sxs-lookup"><span data-stu-id="d505b-300">Uses a pre-built `eshop/web:latest` image.</span></span> <span data-ttu-id="d505b-301">Můžete ale také nakonfigurovat, aby se image vytvořila jako součást spuštění v Docker – pomocí dodatečné konfigurace založené na sestavení: oddíl v souboru Docker-skládání.</span><span class="sxs-lookup"><span data-stu-id="d505b-301">However, you could also configure the image to be built as part of the docker-compose execution with an additional configuration based on a build: section in the docker-compose file.</span></span>

- <span data-ttu-id="d505b-302">Inicializuje dvě proměnné prostředí (CatalogUrl a OrderingUrl).</span><span class="sxs-lookup"><span data-stu-id="d505b-302">Initializes two environment variables (CatalogUrl and OrderingUrl).</span></span>

- <span data-ttu-id="d505b-303">Přepošle vystavený port 80 na kontejner na externí port 80 na hostitelském počítači.</span><span class="sxs-lookup"><span data-stu-id="d505b-303">Forwards the exposed port 80 on the container to the external port 80 on the host machine.</span></span>

- <span data-ttu-id="d505b-304">Propojí webovou aplikaci s katalogem a službou řazení s nastavením depends_on.</span><span class="sxs-lookup"><span data-stu-id="d505b-304">Links the web app to the catalog and ordering service with the depends_on setting.</span></span> <span data-ttu-id="d505b-305">Tím dojde k tomu, že služba počká, až budou tyto služby spuštěné.</span><span class="sxs-lookup"><span data-stu-id="d505b-305">This causes the service to wait until those services are started.</span></span>

<span data-ttu-id="d505b-306">Až budeme pokrývat, jak implementovat mikroslužby a aplikace pro více kontejnerů, provedeme znovu soubor Docker-Compose. yml v pozdější části.</span><span class="sxs-lookup"><span data-stu-id="d505b-306">We will revisit the docker-compose.yml file in a later section when we cover how to implement microservices and multi-container apps.</span></span>

### <a name="working-with-docker-composeyml-in-visual-studio-2017"></a><span data-ttu-id="d505b-307">Práce s Docker-Compose. yml v aplikaci Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="d505b-307">Working with docker-compose.yml in Visual Studio 2017</span></span>

<span data-ttu-id="d505b-308">Kromě přidání souboru Dockerfile do projektu, jak je uvedeno dříve, může Visual Studio 2017 (ze verze 15,8 on) přidat do řešení podporu nástroje Orchestrator pro Docker Compose.</span><span class="sxs-lookup"><span data-stu-id="d505b-308">Besides adding a Dockerfile to a project, as we mentioned before, Visual Studio 2017 (from version 15.8 on) can add orchestrator support for Docker Compose to a solution.</span></span>

<span data-ttu-id="d505b-309">Když přidáte podporu nástroje Orchestrator pro kontejner, jak je znázorněno na obrázku 5-7, Visual Studio vytvoří souboru Dockerfile pro projekt a vytvoří nový projekt (oddíl služby) ve vašem řešení s několika globálními `docker-compose*.yml` soubory a potom do těchto souborů přidá projekt.</span><span class="sxs-lookup"><span data-stu-id="d505b-309">When you add container orchestrator support, as shown in Figure 5-7, for the first time, Visual Studio creates the Dockerfile for the project and creates a new (service section) project in your solution with several global `docker-compose*.yml` files, and then adds the project to those files.</span></span> <span data-ttu-id="d505b-310">Pak můžete otevřít soubory Docker-Compose. yml a aktualizovat je pomocí dalších funkcí.</span><span class="sxs-lookup"><span data-stu-id="d505b-310">You can then open the docker-compose.yml files and update them with additional features.</span></span>

<span data-ttu-id="d505b-311">Tuto operaci je nutné opakovat v každém projektu, který chcete zahrnout do souboru Docker-Compose. yml.</span><span class="sxs-lookup"><span data-stu-id="d505b-311">You have to repeat this operation form every project you want to include in the docker-compose.yml file.</span></span>

<span data-ttu-id="d505b-312">V době psaní tohoto zápisu aplikace Visual Studio podporuje orchestraci Docker Compose a Service Fabric.</span><span class="sxs-lookup"><span data-stu-id="d505b-312">At the time of this writing, Visual Studio supports Docker Compose and Service Fabric orchestrators.</span></span>

![Snímek obrazovky s možností podpora pro produkt Orchestrator pro kontejner v místní nabídce projektu](./media/docker-app-development-workflow/add-container-orchestrator-support-option.png)

<span data-ttu-id="d505b-314">**Obrázek 5-7**.</span><span class="sxs-lookup"><span data-stu-id="d505b-314">**Figure 5-7**.</span></span> <span data-ttu-id="d505b-315">Přidání podpory Docker do sady Visual Studio 2017 tak, že kliknete pravým tlačítkem na projekt ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="d505b-315">Adding Docker support in Visual Studio 2017 by right-clicking an ASP.NET Core project</span></span>

<span data-ttu-id="d505b-316">Po přidání podpory nástroje Orchestrator do řešení v aplikaci Visual Studio se také zobrazí nový uzel (v souboru `docker-compose.dcproj` projektu) v Průzkumník řešení, který obsahuje přidané soubory Docker-Compose. yml, jak je znázorněno na obrázku 5-8.</span><span class="sxs-lookup"><span data-stu-id="d505b-316">After you add orchestrator support to your solution in Visual Studio, you will also see a new node (in the `docker-compose.dcproj` project file) in Solution Explorer that contains the added docker-compose.yml files, as shown in Figure 5-8.</span></span>

![Snímek obrazovky s uzlem Docker-psací v Průzkumník řešení.](./media/docker-app-development-workflow/docker-compose-tree-node.png)

<span data-ttu-id="d505b-318">**Obrázek 5-8**.</span><span class="sxs-lookup"><span data-stu-id="d505b-318">**Figure 5-8**.</span></span> <span data-ttu-id="d505b-319">Uzel stromu **Docker-psacího** uzlu přidaný do sady Visual Studio 2017 Průzkumník řešení</span><span class="sxs-lookup"><span data-stu-id="d505b-319">The **docker-compose** tree node added in Visual Studio 2017 Solution Explorer</span></span>

<span data-ttu-id="d505b-320">Pomocí příkazu `docker-compose up` můžete nasadit aplikaci s více kontejnery s jedním souborem Docker-Compose. yml.</span><span class="sxs-lookup"><span data-stu-id="d505b-320">You could deploy a multi-container application with a single docker-compose.yml file by using the `docker-compose up` command.</span></span> <span data-ttu-id="d505b-321">Visual Studio však přidá skupinu, takže můžete přepsat hodnoty v závislosti na prostředí (vývoj nebo produkce) a typu spuštění (vydání nebo ladění).</span><span class="sxs-lookup"><span data-stu-id="d505b-321">However, Visual Studio adds a group of them so you can override values depending on the environment (development or production) and execution type (release or debug).</span></span> <span data-ttu-id="d505b-322">Tato funkce bude vysvětlena v dalších částech.</span><span class="sxs-lookup"><span data-stu-id="d505b-322">This capability will be explained in later sections.</span></span>

![Obrázek pro krok 5](./media/docker-app-development-workflow/step-5-run-containers-compose-app.png)

## <a name="step-5-build-and-run-your-docker-application"></a><span data-ttu-id="d505b-324">Krok 5.</span><span class="sxs-lookup"><span data-stu-id="d505b-324">Step 5.</span></span> <span data-ttu-id="d505b-325">Sestavení a spuštění aplikace Docker</span><span class="sxs-lookup"><span data-stu-id="d505b-325">Build and run your Docker application</span></span>

<span data-ttu-id="d505b-326">Pokud má vaše aplikace jenom jeden kontejner, můžete ho spustit nasazením na hostitele Docker (virtuální počítač nebo fyzický server).</span><span class="sxs-lookup"><span data-stu-id="d505b-326">If your application only has a single container, you can run it by deploying it to your Docker host (VM or physical server).</span></span> <span data-ttu-id="d505b-327">Pokud však vaše aplikace obsahuje více služeb, můžete ji nasadit jako složenou aplikaci, a to buď pomocí jednoho příkazu CLI (Docker-sestavit), nebo pomocí sady Visual Studio, která bude tento příkaz používat v rámci pokrývání.</span><span class="sxs-lookup"><span data-stu-id="d505b-327">However, if your application contains multiple services, you can deploy it as a composed application, either using a single CLI command (docker-compose up), or with Visual Studio, which will use that command under the covers.</span></span> <span data-ttu-id="d505b-328">Pojďme se podívat na různé možnosti.</span><span class="sxs-lookup"><span data-stu-id="d505b-328">Let's look at the different options.</span></span>

### <a name="option-a-running-a-single-container-application"></a><span data-ttu-id="d505b-329">Možnost A: spuštění aplikace s jedním kontejnerem</span><span class="sxs-lookup"><span data-stu-id="d505b-329">Option A: Running a single-container application</span></span>

#### <a name="using-docker-cli"></a><span data-ttu-id="d505b-330">Použití rozhraní Docker CLI</span><span class="sxs-lookup"><span data-stu-id="d505b-330">Using Docker CLI</span></span>

<span data-ttu-id="d505b-331">Kontejner Docker můžete spustit pomocí příkazu `docker run`, jak je znázorněno na obrázku 5-9:</span><span class="sxs-lookup"><span data-stu-id="d505b-331">You can run a Docker container using the `docker run` command, as shown in Figure 5-9:</span></span>

```console
docker run -t -d -p 80:5000 cesardl/netcore-webapi-microservice-docker:first
```

<span data-ttu-id="d505b-332">Výše uvedený příkaz vytvoří novou instanci kontejneru ze zadané image pokaždé, když se spustí.</span><span class="sxs-lookup"><span data-stu-id="d505b-332">The above command will create a new container instance from the specified image, every time it's run.</span></span> <span data-ttu-id="d505b-333">Pomocí parametru `--name` můžete předat kontejneru název a potom pomocí `docker start {name}` (nebo pomocí ID kontejneru nebo automatického názvu) spustit existující instanci kontejneru.</span><span class="sxs-lookup"><span data-stu-id="d505b-333">You can use the `--name` parameter to give a name to the container and then use `docker start {name}` (or use the container ID or automatic name) to run an existing container instance.</span></span>

![Snímek obrazovky s kontejnerem Docker pomocí příkazu Docker run](./media/docker-app-development-workflow/use-docker-run-command.png)

<span data-ttu-id="d505b-335">**Obrázek 5-9**.</span><span class="sxs-lookup"><span data-stu-id="d505b-335">**Figure 5-9**.</span></span> <span data-ttu-id="d505b-336">Spuštění kontejneru Docker pomocí příkazu Docker run</span><span class="sxs-lookup"><span data-stu-id="d505b-336">Running a Docker container using the docker run command</span></span>

<span data-ttu-id="d505b-337">V takovém případě příkaz váže interní port 5000 kontejneru na port 80 hostitelského počítače.</span><span class="sxs-lookup"><span data-stu-id="d505b-337">In this case, the command binds the internal port 5000 of the container to port 80 of the host machine.</span></span> <span data-ttu-id="d505b-338">To znamená, že hostitel naslouchá na portu 80 a přesměrovává na port 5000 na kontejneru.</span><span class="sxs-lookup"><span data-stu-id="d505b-338">This means that the host is listening on port 80 and forwarding to port 5000 on the container.</span></span>

<span data-ttu-id="d505b-339">Zobrazená hodnota hash je ID kontejneru a je mu přiřazen také náhodný čitelný název, pokud není použita možnost `--name`.</span><span class="sxs-lookup"><span data-stu-id="d505b-339">The hash shown is the container ID and it’s also assigned a random readable name if the `--name` option is not used.</span></span>

#### <a name="using-visual-studio"></a><span data-ttu-id="d505b-340">Pomocí sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="d505b-340">Using Visual Studio</span></span>

<span data-ttu-id="d505b-341">Pokud jste nepřidali podporu nástroje Orchestrator pro kontejner, můžete také spustit jednu aplikaci kontejneru v sadě Visual Studio stisknutím **kombinace kláves CTRL + F5** a můžete také pomocí **F5** ladit aplikaci v rámci kontejneru.</span><span class="sxs-lookup"><span data-stu-id="d505b-341">If you haven't added container orchestrator support, you can also run a single container app in Visual Studio by pressing **Ctrl-F5** and you can also use **F5** to debug the application within the container.</span></span> <span data-ttu-id="d505b-342">Kontejner se spouští místně pomocí Docker run.</span><span class="sxs-lookup"><span data-stu-id="d505b-342">The container runs locally using docker run.</span></span>

### <a name="option-b-running-a-multi-container-application"></a><span data-ttu-id="d505b-343">Možnost B: spuštění aplikace s více kontejnery</span><span class="sxs-lookup"><span data-stu-id="d505b-343">Option B: Running a multi-container application</span></span>

<span data-ttu-id="d505b-344">Ve většině podnikových scénářů se aplikace Docker skládá z několika služeb, což znamená, že je nutné spustit aplikaci s více kontejnery, jak je znázorněno na obrázku 5-10.</span><span class="sxs-lookup"><span data-stu-id="d505b-344">In most enterprise scenarios, a Docker application will be composed of multiple services, which means you need to run a multi-container application, as shown in Figure 5-10.</span></span>

![Virtuální počítač s několika kontejnery Docker](./media/docker-app-development-workflow/vm-with-docker-containers-deployed.png)

<span data-ttu-id="d505b-346">**Obrázek 5-10**.</span><span class="sxs-lookup"><span data-stu-id="d505b-346">**Figure 5-10**.</span></span> <span data-ttu-id="d505b-347">Virtuální počítač s nasazenými kontejnery Docker</span><span class="sxs-lookup"><span data-stu-id="d505b-347">VM with Docker containers deployed</span></span>

#### <a name="using-docker-cli"></a><span data-ttu-id="d505b-348">Použití rozhraní Docker CLI</span><span class="sxs-lookup"><span data-stu-id="d505b-348">Using Docker CLI</span></span>

<span data-ttu-id="d505b-349">Chcete-li spustit aplikaci s více kontejnery pomocí Docker CLI, použijte příkaz `docker-compose up`.</span><span class="sxs-lookup"><span data-stu-id="d505b-349">To run a multi-container application with the Docker CLI, you use the `docker-compose up` command.</span></span> <span data-ttu-id="d505b-350">Tento příkaz používá soubor **Docker-Compose. yml** , který máte na úrovni řešení k nasazení aplikace s více kontejnery.</span><span class="sxs-lookup"><span data-stu-id="d505b-350">This command uses the **docker-compose.yml** file that you have at the solution level to deploy a multi-container application.</span></span> <span data-ttu-id="d505b-351">Obrázek 5-11 zobrazuje výsledky při spuštění příkazu z hlavního adresáře řešení, který obsahuje soubor Docker-Compose. yml.</span><span class="sxs-lookup"><span data-stu-id="d505b-351">Figure 5-11 shows the results when running the command from your main solution directory, which contains the docker-compose.yml file.</span></span>

![Zobrazení obrazovky při spuštění příkazu Docker – vytvořit](./media/docker-app-development-workflow/results-docker-compose-up.png)

<span data-ttu-id="d505b-353">**Obrázek 5-11**.</span><span class="sxs-lookup"><span data-stu-id="d505b-353">**Figure 5-11**.</span></span> <span data-ttu-id="d505b-354">Příklady výsledků při spuštění příkazu Docker-sestavit</span><span class="sxs-lookup"><span data-stu-id="d505b-354">Example results when running the docker-compose up command</span></span>

<span data-ttu-id="d505b-355">Po spuštění příkazu Docker-sestavit je aplikace a její související kontejnery nasazeny do hostitele Docker, jak je znázorněno na obrázku 5-10.</span><span class="sxs-lookup"><span data-stu-id="d505b-355">After the docker-compose up command runs, the application and its related containers are deployed into your Docker host, as depicted in Figure 5-10.</span></span>

#### <a name="using-visual-studio"></a><span data-ttu-id="d505b-356">Pomocí sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="d505b-356">Using Visual Studio</span></span>

<span data-ttu-id="d505b-357">Spuštění aplikace s více kontejnery pomocí sady Visual Studio 2017 nemůže získat jednodušší.</span><span class="sxs-lookup"><span data-stu-id="d505b-357">Running a multi-container application using Visual Studio 2017 can't get any simpler.</span></span> <span data-ttu-id="d505b-358">Stačí stisknout **kombinaci kláves CTRL + F5** ke spuštění nebo **F5** pro ladění, jako obvykle, nastavení projektu **Docker-sestavit** jako spouštěného projektu.</span><span class="sxs-lookup"><span data-stu-id="d505b-358">You just press **Ctrl-F5** to run or **F5** to debug, as usual, setting up the **docker-compose** project as the startup project.</span></span>  <span data-ttu-id="d505b-359">Visual Studio zpracuje všechna potřebná nastavení, takže můžete vytvořit zarážky jako obvykle a ladit tak, co se stane samostatnými procesy běžícími na vzdálených serverech stejným způsobem.</span><span class="sxs-lookup"><span data-stu-id="d505b-359">Visual Studio handles all needed setup, so you can create breakpoints as usual and debug what finally become independent processes running in "remote servers", just like that.</span></span>

<span data-ttu-id="d505b-360">Jak bylo zmíněno dříve, pokaždé, když přidáte podporu řešení Docker do projektu v rámci řešení, je tento projekt konfigurován v souboru Global (Solution-Level) Docker-Compose. yml, který umožňuje spustit nebo ladit celé řešení najednou.</span><span class="sxs-lookup"><span data-stu-id="d505b-360">As mentioned before, each time you add Docker solution support to a project within a solution, that project is configured in the global (solution-level) docker-compose.yml file, which lets you run or debug the whole solution at once.</span></span> <span data-ttu-id="d505b-361">Visual Studio spustí jeden kontejner pro každý projekt, který má povolenou podporu řešení Docker, a provede všechny interní kroky (dotnet publish, Docker Build atd.).</span><span class="sxs-lookup"><span data-stu-id="d505b-361">Visual Studio will start one container for each project that has Docker solution support enabled, and perform all the internal steps for you (dotnet publish, docker build, etc.).</span></span>

<span data-ttu-id="d505b-362">Pokud si chcete prohlédnout všechny drudgery, podívejte se na soubor:</span><span class="sxs-lookup"><span data-stu-id="d505b-362">If you want to take a peek at all the drudgery, take a look at the file:</span></span>

`{root solution folder}\obj\Docker\docker-compose.vs.debug.g.yml`

<span data-ttu-id="d505b-363">Důležitým bodem je, jak je znázorněno na obrázku 5-12, v aplikaci Visual Studio 2017 je k dispozici další příkaz **Docker** pro akci klávesy F5.</span><span class="sxs-lookup"><span data-stu-id="d505b-363">The important point here is that, as shown in Figure 5-12, in Visual Studio 2017 there is an additional **Docker** command for the F5 key action.</span></span> <span data-ttu-id="d505b-364">Tato možnost umožňuje spustit nebo ladit aplikaci s více kontejnery spuštěním všech kontejnerů, které jsou definovány v souborech Docker-Compose. yml na úrovni řešení.</span><span class="sxs-lookup"><span data-stu-id="d505b-364">This option lets you run or debug a multi-container application by running all the containers that are defined in the docker-compose.yml files at the solution level.</span></span> <span data-ttu-id="d505b-365">Možnost ladit řešení s více kontejnery znamená, že můžete nastavit několik zarážek, každou zarážku v jiném projektu (kontejneru) a při ladění ze sady Visual Studio se zastavíte na zarážekch definovaných v různých projektech a v systému různé kontejnery.</span><span class="sxs-lookup"><span data-stu-id="d505b-365">The ability to debug multiple-container solutions means that you can set several breakpoints, each breakpoint in a different project (container), and while debugging from Visual Studio you will stop at breakpoints defined in different projects and running on different containers.</span></span>

![Snímek obrazovky s panelem ladění, na kterém je spuštěný projekt Docker-sestavit](./media/docker-app-development-workflow/debug-toolbar-docker-compose-project.png)

<span data-ttu-id="d505b-367">**Obrázek 5-12**.</span><span class="sxs-lookup"><span data-stu-id="d505b-367">**Figure 5-12**.</span></span> <span data-ttu-id="d505b-368">Spouštění aplikací s více kontejnery v aplikaci Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="d505b-368">Running multi-container apps in Visual Studio 2017</span></span>

### <a name="additional-resources"></a><span data-ttu-id="d505b-369">Další materiály a zdroje informací</span><span class="sxs-lookup"><span data-stu-id="d505b-369">Additional resources</span></span>

- <span data-ttu-id="d505b-370">**Nasazení kontejneru ASP.NET na hostitele vzdáleného docker** </span><span class="sxs-lookup"><span data-stu-id="d505b-370">**Deploy an ASP.NET container to a remote Docker host** </span></span>\
  <https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker>

### <a name="a-note-about-testing-and-deploying-with-orchestrators"></a><span data-ttu-id="d505b-371">Poznámka k testování a nasazení s orchestrací</span><span class="sxs-lookup"><span data-stu-id="d505b-371">A note about testing and deploying with orchestrators</span></span>

<span data-ttu-id="d505b-372">Příkazy Docker-sestavit a Docker spouštějí (nebo spouštějí a ladí kontejnery v aplikaci Visual Studio) jsou vhodné pro testování kontejnerů ve vašem vývojovém prostředí.</span><span class="sxs-lookup"><span data-stu-id="d505b-372">The docker-compose up and docker run commands (or running and debugging the containers in Visual Studio) are adequate for testing containers in your development environment.</span></span> <span data-ttu-id="d505b-373">Tento přístup ale byste neměli používat pro produkční nasazení, kde byste měli cílit na orchestraci, jako je [Kubernetes](https://kubernetes.io/) nebo [Service Fabric](https://azure.microsoft.com/services/service-fabric/).</span><span class="sxs-lookup"><span data-stu-id="d505b-373">But you should not use this approach for production deployments, where you should target orchestrators like [Kubernetes](https://kubernetes.io/) or [Service Fabric](https://azure.microsoft.com/services/service-fabric/).</span></span> <span data-ttu-id="d505b-374">Pokud používáte Kubernetes, musíte k uspořádání kontejnerů a [služeb](https://kubernetes.io/docs/concepts/services-networking/service/) do sítě použít [lusky](https://kubernetes.io/docs/concepts/workloads/pods/pod/) .</span><span class="sxs-lookup"><span data-stu-id="d505b-374">If you're using Kubernetes, you have to use [pods](https://kubernetes.io/docs/concepts/workloads/pods/pod/) to organize containers and [services](https://kubernetes.io/docs/concepts/services-networking/service/) to network them.</span></span> <span data-ttu-id="d505b-375">K uspořádání a úpravám pod můžete také použít [nasazení](https://kubernetes.io/docs/concepts/workloads/controllers/deployment/) .</span><span class="sxs-lookup"><span data-stu-id="d505b-375">You also use [deployments](https://kubernetes.io/docs/concepts/workloads/controllers/deployment/) to organize pod creation and modification.</span></span>

![Obrázek pro krok 6.](./media/docker-app-development-workflow/step-6-test-app-microservices.png)

## <a name="step-6-test-your-docker-application-using-your-local-docker-host"></a><span data-ttu-id="d505b-377">Krok 6.</span><span class="sxs-lookup"><span data-stu-id="d505b-377">Step 6.</span></span> <span data-ttu-id="d505b-378">Otestování aplikace Docker pomocí místního hostitele Docker</span><span class="sxs-lookup"><span data-stu-id="d505b-378">Test your Docker application using your local Docker host</span></span>

<span data-ttu-id="d505b-379">Tento krok se bude lišit v závislosti na tom, co vaše aplikace dělá.</span><span class="sxs-lookup"><span data-stu-id="d505b-379">This step will vary depending on what your application is doing.</span></span> <span data-ttu-id="d505b-380">V jednoduché webové aplikaci .NET Core, která je nasazena jako jediný kontejner nebo služba, můžete ke službě přistupovat otevřením prohlížeče na hostiteli Docker a přechodem na tuto lokalitu, jak je znázorněno na obrázku 5-13.</span><span class="sxs-lookup"><span data-stu-id="d505b-380">In a simple .NET Core Web application that is deployed as a single container or service, you can access the service by opening a browser on the Docker host and navigating to that site, as shown in Figure 5-13.</span></span> <span data-ttu-id="d505b-381">(Pokud konfigurace v souboru Dockerfile mapuje kontejner na port na hostiteli, který je cokoli jiného než 80, zahrňte do adresy URL port hostitele.)</span><span class="sxs-lookup"><span data-stu-id="d505b-381">(If the configuration in the Dockerfile maps the container to a port on the host that is anything other than 80, include the host port in the URL.)</span></span>

![Snímek obrazovky odpovědi z místního hostitele/rozhraní API/hodnot](./media/docker-app-development-workflow/test-docker-app-locally-localhost.png)

<span data-ttu-id="d505b-383">**Obrázek 5-13**.</span><span class="sxs-lookup"><span data-stu-id="d505b-383">**Figure 5-13**.</span></span> <span data-ttu-id="d505b-384">Příklad testování aplikace Docker místně pomocí místního hostitele</span><span class="sxs-lookup"><span data-stu-id="d505b-384">Example of testing your Docker application locally using localhost</span></span>

<span data-ttu-id="d505b-385">Pokud localhost neukazuje na IP adresu hostitele Docker (ve výchozím nastavení při použití Docker CE, měla by) přejít na vaši službu a použít IP adresu síťové karty vašeho počítače.</span><span class="sxs-lookup"><span data-stu-id="d505b-385">If localhost is not pointing to the Docker host IP (by default, when using Docker CE, it should), to navigate to your service, use the IP address of your machine's network card.</span></span>

<span data-ttu-id="d505b-386">Všimněte si, že tato adresa URL v prohlížeči používá port 80 pro konkrétní popsanou ukázku kontejneru.</span><span class="sxs-lookup"><span data-stu-id="d505b-386">Note that this URL in the browser uses port 80 for the particular container example being discussed.</span></span> <span data-ttu-id="d505b-387">Interní požadavky se ale přesměrují na port 5000, protože to bylo, jak bylo nasazeno pomocí příkazu Docker Run, jak je vysvětleno v předchozím kroku.</span><span class="sxs-lookup"><span data-stu-id="d505b-387">However, internally the requests are being redirected to port 5000, because that was how it was deployed with the docker run command, as explained in a previous step.</span></span>

<span data-ttu-id="d505b-388">Aplikaci můžete také otestovat pomocí oblého terminálu, jak je znázorněno na obrázku 5-14.</span><span class="sxs-lookup"><span data-stu-id="d505b-388">You can also test the application using curl from the terminal, as shown in Figure 5-14.</span></span> <span data-ttu-id="d505b-389">V instalaci Docker ve Windows je výchozí IP adresa hostitele Docker vždycky 10.0.75.1a kromě skutečné IP adresy vašeho počítače.</span><span class="sxs-lookup"><span data-stu-id="d505b-389">In a Docker installation on Windows, the default Docker Host IP is always 10.0.75.1 in addition to your machine's actual IP address.</span></span>

![Výstup na konzole z části získání http://10.0.75.1/API/values pomocí oblé.](./media/docker-app-development-workflow/test-docker-app-locally-curl.png)

<span data-ttu-id="d505b-391">**Obrázek 5-14**.</span><span class="sxs-lookup"><span data-stu-id="d505b-391">**Figure 5-14**.</span></span> <span data-ttu-id="d505b-392">Příklad testování aplikace Docker v místním prostředí pomocí formátu kudrlinkou</span><span class="sxs-lookup"><span data-stu-id="d505b-392">Example of testing your Docker application locally using curl</span></span>

### <a name="testing-and-debugging-containers-with-visual-studio-2017"></a><span data-ttu-id="d505b-393">Testování a ladění kontejnerů pomocí sady Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="d505b-393">Testing and debugging containers with Visual Studio 2017</span></span>

<span data-ttu-id="d505b-394">Při spuštění a ladění kontejnerů pomocí sady Visual Studio 2017 můžete ladit aplikaci .NET podobným způsobem jako při spuštění bez kontejnerů.</span><span class="sxs-lookup"><span data-stu-id="d505b-394">When running and debugging the containers with Visual Studio 2017, you can debug the .NET application in much the same way as you would when running without containers.</span></span>

### <a name="testing-and-debugging-without-visual-studio"></a><span data-ttu-id="d505b-395">Testování a ladění bez sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="d505b-395">Testing and debugging without Visual Studio</span></span>

<span data-ttu-id="d505b-396">Pokud vyvíjíte pomocí přístupu Editor/CLI, kontejnery ladění jsou obtížnější a vy budete chtít ladit vygenerováním trasování.</span><span class="sxs-lookup"><span data-stu-id="d505b-396">If you're developing using the editor/CLI approach, debugging containers is more difficult and you will want to debug by generating traces.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="d505b-397">Další materiály a zdroje informací</span><span class="sxs-lookup"><span data-stu-id="d505b-397">Additional resources</span></span>

- <span data-ttu-id="d505b-398">**Ladění aplikací v místním kontejneru docker** </span><span class="sxs-lookup"><span data-stu-id="d505b-398">**Debugging apps in a local Docker container** </span></span>\
  [https://docs.microsoft.com/visualstudio/containers/edit-and-refresh](/visualstudio/containers/edit-and-refresh)

- <span data-ttu-id="d505b-399">**Steve Lasker. Sestavování, ladění, nasazení ASP.NET Core aplikací pomocí Docker.**</span><span class="sxs-lookup"><span data-stu-id="d505b-399">**Steve Lasker. Build, Debug, Deploy ASP.NET Core Apps with Docker.**</span></span> <span data-ttu-id="d505b-400">Obrazový.</span><span class="sxs-lookup"><span data-stu-id="d505b-400">Video.</span></span> \
  <https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T115>

## <a name="simplified-workflow-when-developing-containers-with-visual-studio"></a><span data-ttu-id="d505b-401">Zjednodušený pracovní postup při vývoji kontejnerů pomocí sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="d505b-401">Simplified workflow when developing containers with Visual Studio</span></span>

<span data-ttu-id="d505b-402">Pracovní postup při použití sady Visual Studio je efektivně mnohem jednodušší než při použití přístupu Editor/CLI.</span><span class="sxs-lookup"><span data-stu-id="d505b-402">Effectively, the workflow when using Visual Studio is a lot simpler than if you use the editor/CLI approach.</span></span> <span data-ttu-id="d505b-403">Většina kroků požadovaných v Docker související se soubory souboru Dockerfile a Docker-Compose. yml jsou v aplikaci Visual Studio skryté nebo zjednodušené, jak je znázorněno na obrázku 5-15.</span><span class="sxs-lookup"><span data-stu-id="d505b-403">Most of the steps required by Docker related to the Dockerfile and docker-compose.yml files are hidden or simplified by Visual Studio, as shown in Figure 5-15.</span></span>

:::image type="complex" source="./media/docker-app-development-workflow/simplified-life-cycle-containerized-apps-docker-cli.png" alt-text="Diagram znázorňující pět zjednodušených kroků potřebných k vytvoření aplikace.":::
<span data-ttu-id="d505b-405">Proces vývoje pro aplikace Docker: 1 – kódování vaší aplikace, 2-zápis souboru Dockerfile/s, 3-vytváření imagí definovaných na souboru Dockerfile/s, 4 – (volitelné) psaní služeb v souboru Docker-Compose. yml, 5 spuštění kontejneru nebo Docker – sestavování, 6-testování aplikace nebo mikroslužeb, 7-nabízení do úložiště a opakování.</span><span class="sxs-lookup"><span data-stu-id="d505b-405">The development process for Docker apps: 1 - Code your App, 2 - Write Dockerfile/s, 3 - Create images defined at Dockerfile/s, 4 - (optional) Compose services in the docker-compose.yml file, 5 - Run container or docker-compose app, 6 - Test your app or microservices, 7 - Push to repo and repeat.</span></span>
:::image-end:::

<span data-ttu-id="d505b-406">**Obrázek 5-15**.</span><span class="sxs-lookup"><span data-stu-id="d505b-406">**Figure 5-15**.</span></span> <span data-ttu-id="d505b-407">Zjednodušený pracovní postup při vývoji se sadou Visual Studio</span><span class="sxs-lookup"><span data-stu-id="d505b-407">Simplified workflow when developing with Visual Studio</span></span>

<span data-ttu-id="d505b-408">Kromě toho je nutné provést krok 2 (přidání podpory Docker do vašich projektů) pouze jednou.</span><span class="sxs-lookup"><span data-stu-id="d505b-408">In addition, you need to perform step 2 (adding Docker support to your projects) just once.</span></span> <span data-ttu-id="d505b-409">Proto je pracovní postup podobný obvyklým vývojářským úlohám při použití rozhraní .NET pro jakýkoliv jiný vývoj.</span><span class="sxs-lookup"><span data-stu-id="d505b-409">Therefore, the workflow is similar to your usual development tasks when using .NET for any other development.</span></span> <span data-ttu-id="d505b-410">Potřebujete zjistit, co se týká pokrývání (proces sestavení obrazu, jaké základní image používáte, nasazení kontejnerů atd.), a někdy budete také muset upravit soubor souboru Dockerfile nebo Docker-Compose. yml, abyste mohli chování přizpůsobit.</span><span class="sxs-lookup"><span data-stu-id="d505b-410">You need to know what is going on under the covers (the image build process, what base images you're using, deployment of containers, etc.) and sometimes you will also need to edit the Dockerfile or docker-compose.yml file to customize behaviors.</span></span> <span data-ttu-id="d505b-411">Ale většina práce je výrazně zjednodušená pomocí sady Visual Studio, což vám umožní mnohem větší produktivitu.</span><span class="sxs-lookup"><span data-stu-id="d505b-411">But most of the work is greatly simplified by using Visual Studio, making you a lot more productive.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="d505b-412">Další materiály a zdroje informací</span><span class="sxs-lookup"><span data-stu-id="d505b-412">Additional resources</span></span>

- <span data-ttu-id="d505b-413">**Steve Lasker. .NET Docker – vývoj s využitím sady Visual Studio 2017** </span><span class="sxs-lookup"><span data-stu-id="d505b-413">**Steve Lasker. .NET Docker Development with Visual Studio 2017** </span></span>\
  <https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T111>

## <a name="using-powershell-commands-in-a-dockerfile-to-set-up-windows-containers"></a><span data-ttu-id="d505b-414">Použití příkazů PowerShellu v souboru Dockerfile k nastavení kontejnerů Windows</span><span class="sxs-lookup"><span data-stu-id="d505b-414">Using PowerShell commands in a Dockerfile to set up Windows Containers</span></span>

<span data-ttu-id="d505b-415">[Kontejnery Windows](https://docs.microsoft.com/virtualization/windowscontainers/about/index) umožňují převést existující aplikace pro Windows na Image Docker a nasadit je pomocí stejných nástrojů jako zbytek ekosystému Docker.</span><span class="sxs-lookup"><span data-stu-id="d505b-415">[Windows Containers](https://docs.microsoft.com/virtualization/windowscontainers/about/index) allow you to convert your existing Windows applications into Docker images and deploy them with the same tools as the rest of the Docker ecosystem.</span></span> <span data-ttu-id="d505b-416">Chcete-li použít kontejnery Windows, spusťte příkazy prostředí PowerShell v souboru Dockerfile, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="d505b-416">To use Windows Containers, you run PowerShell commands in the Dockerfile, as shown in the following example:</span></span>

```Dockerfile
FROM microsoft/windowsservercore
LABEL Description="IIS" Vendor="Microsoft" Version="10"
RUN powershell -Command Add-WindowsFeature Web-Server
CMD [ "ping", "localhost", "-t" ]
```

<span data-ttu-id="d505b-417">V tomto případě používáme základní bitovou kopii Windows serveru (nastavení z) a instalujete službu IIS pomocí příkazu PowerShellu (nastavení spuštění).</span><span class="sxs-lookup"><span data-stu-id="d505b-417">In this case, we are using a Windows Server Core base image (the FROM setting) and installing IIS with a PowerShell command (the RUN setting).</span></span> <span data-ttu-id="d505b-418">Podobným způsobem můžete také použít příkazy PowerShellu k nastavení dalších komponent, jako jsou ASP.NET 4. x, .NET 4,6 nebo jakýkoli jiný software pro Windows.</span><span class="sxs-lookup"><span data-stu-id="d505b-418">In a similar way, you could also use PowerShell commands to set up additional components like ASP.NET 4.x, .NET 4.6, or any other Windows software.</span></span> <span data-ttu-id="d505b-419">Například následující příkaz v souboru Dockerfile nastaví ASP.NET 4,5:</span><span class="sxs-lookup"><span data-stu-id="d505b-419">For example, the following command in a Dockerfile sets up ASP.NET 4.5:</span></span>

```Dockerfile
RUN powershell add-windowsfeature web-asp-net45
```

### <a name="additional-resources"></a><span data-ttu-id="d505b-420">Další materiály a zdroje informací</span><span class="sxs-lookup"><span data-stu-id="d505b-420">Additional resources</span></span>

- <span data-ttu-id="d505b-421">**aspnet-docker/Dockerfile.**</span><span class="sxs-lookup"><span data-stu-id="d505b-421">**aspnet-docker/Dockerfile.**</span></span> <span data-ttu-id="d505b-422">Příklady příkazů PowerShellu, které se mají spustit z fázemi a zahrnutí funkcí Windows. </span><span class="sxs-lookup"><span data-stu-id="d505b-422">Example PowerShell commands to run from dockerfiles to include Windows features.</span></span>\
  <https://github.com/Microsoft/aspnet-docker/blob/master/4.7.1-windowsservercore-ltsc2016/runtime/Dockerfile>

>[!div class="step-by-step"]
><span data-ttu-id="d505b-423">[Předchozí](index.md)
>[Další](../multi-container-microservice-net-applications/index.md)</span><span class="sxs-lookup"><span data-stu-id="d505b-423">[Previous](index.md)
[Next](../multi-container-microservice-net-applications/index.md)</span></span>
