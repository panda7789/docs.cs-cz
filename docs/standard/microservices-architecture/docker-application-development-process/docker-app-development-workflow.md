---
title: Pracovní postup vývoje aplikací Dockeru
description: Zjistěte podrobnosti pracovního postupu pro vývoj aplikací založených na Dockeru. Krok za krokem začít a získat některé podrobnosti pro optimalizaci soubory Dockerfile a končit zjednodušený pracovní postup k dispozici, když pomocí sady Visual Studio.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 01/07/2019
ms.openlocfilehash: a8016b2b55313cb6e1d84bfb2c50a62347858de9
ms.sourcegitcommit: 7156c0b9e4ce4ce5ecf48ce3d925403b638b680c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/26/2019
ms.locfileid: "58464356"
---
# <a name="development-workflow-for-docker-apps"></a><span data-ttu-id="3b358-104">Pracovní postup vývoje aplikací Dockeru</span><span class="sxs-lookup"><span data-stu-id="3b358-104">Development workflow for Docker apps</span></span>

<span data-ttu-id="3b358-105">Životním cyklu vývoje aplikací se spustí na počítači, jako vývojář, pokud kód aplikace s použitím upřednostňovaný jazyk a místně ji otestovat.</span><span class="sxs-lookup"><span data-stu-id="3b358-105">The application development life cycle starts at your computer, as a developer, where you code the application using your preferred language and test it locally.</span></span> <span data-ttu-id="3b358-106">S tímto pracovním postupem, bez ohledu na to, které jazyk, rozhraní a platformu zvolíte se vždy vývoj a testování kontejnery Dockeru ale uděláte místně.</span><span class="sxs-lookup"><span data-stu-id="3b358-106">With this workflow, no matter which language, framework, and platform you choose, you're always developing and testing Docker containers, but doing so locally.</span></span>

<span data-ttu-id="3b358-107">Každý kontejner (instance image Dockeru) zahrnuje následující součásti:</span><span class="sxs-lookup"><span data-stu-id="3b358-107">Each container (an instance of a Docker image) includes the following components:</span></span>

- <span data-ttu-id="3b358-108">Operačního systému výběru, například Linux distribuce, Windows Nano Server nebo jádra serveru systému Windows.</span><span class="sxs-lookup"><span data-stu-id="3b358-108">An operating system selection, for example, a Linux distribution, Windows Nano Server, or Windows Server Core.</span></span>

- <span data-ttu-id="3b358-109">Soubory přidat během vývoje, například zdrojový kód a aplikace binární soubory.</span><span class="sxs-lookup"><span data-stu-id="3b358-109">Files added during development, for example, source code and application binaries.</span></span>

- <span data-ttu-id="3b358-110">Informace o konfiguraci, jako je například nastavení prostředí a závislosti.</span><span class="sxs-lookup"><span data-stu-id="3b358-110">Configuration information, such as environment settings and dependencies.</span></span>

## <a name="workflow-for-developing-docker-container-based-applications"></a><span data-ttu-id="3b358-111">Pracovní postup pro vývoj aplikací založených na kontejnerech Dockeru</span><span class="sxs-lookup"><span data-stu-id="3b358-111">Workflow for developing Docker container-based applications</span></span>

<span data-ttu-id="3b358-112">Tato část popisuje *vnitřní smyčky* pracovní postup vývoje aplikací založených na kontejnerech Dockeru.</span><span class="sxs-lookup"><span data-stu-id="3b358-112">This section describes the *inner-loop* development workflow for Docker container-based applications.</span></span> <span data-ttu-id="3b358-113">Vnitřní smyčky pracovního postupu znamená, že není vzhledem k tomu širší DevOps pracovního postupu, který může obsahovat až po produkční nasazení a právě se zaměřuje na vývojové práce vykonané na počítači pro vývojáře.</span><span class="sxs-lookup"><span data-stu-id="3b358-113">The inner-loop workflow means it's not considering the broader DevOps workflow, that can include up to production deployment, and just focuses on the development work done on the developer's computer.</span></span> <span data-ttu-id="3b358-114">Počáteční kroky k nastavení prostředí nejsou zahrnuté, protože tyto kroky se provádějí jenom jednou.</span><span class="sxs-lookup"><span data-stu-id="3b358-114">The initial steps to set up the environment aren't included, since those steps are done only once.</span></span>

<span data-ttu-id="3b358-115">Aplikace se skládá z vlastní služby a další knihovny (závislosti).</span><span class="sxs-lookup"><span data-stu-id="3b358-115">An application is composed of your own services plus additional libraries (dependencies).</span></span> <span data-ttu-id="3b358-116">Níže jsou uvedeny základní kroky, které obvykle provést při sestavování aplikace Dockeru, jak je znázorněno na obrázku 5-1.</span><span class="sxs-lookup"><span data-stu-id="3b358-116">The following are the basic steps you usually take when building a Docker application, as illustrated in Figure 5-1.</span></span>

![<span data-ttu-id="3b358-117">Proces vývoje aplikací Dockeru: 1 - kód vaší aplikace, 2 - zápis souboru Dockerfile/s, 3 – vytváření imagí, které jsou definovány v souboru Dockerfile/s, 4 – (volitelné) psaní služby v souboru docker-compose.yml, 5, - spuštění kontejneru nebo docker-compose aplikace, 6 – testování aplikace nebo mikroslužeb, 7 – nahrání do úložiště a opakujte tento postup.</span><span class="sxs-lookup"><span data-stu-id="3b358-117">The development process for Docker apps: 1 - Code your App, 2 - Write Dockerfile/s, 3 - Create images defined at Dockerfile/s, 4 - (optional) Compose services in the docker-compose.yml file, 5 - Run container or docker-compose app, 6 - Test your app or microservices, 7 - Push to repo and repeat.</span></span> ](./media/image1.png)

<span data-ttu-id="3b358-118">**Obrázek 5-1.**</span><span class="sxs-lookup"><span data-stu-id="3b358-118">**Figure 5-1.**</span></span> <span data-ttu-id="3b358-119">Krok za krokem pracovního postupu pro vývoj Docker kontejnerizovaných aplikací</span><span class="sxs-lookup"><span data-stu-id="3b358-119">Step-by-step workflow for developing Docker containerized apps</span></span>

<span data-ttu-id="3b358-120">V této části je podrobně popsán tento celý proces a všemi hlavními kroky jsou vysvětleny se zaměříte na prostředí Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="3b358-120">In this section, this whole process is detailed and every major step is explained by focusing on a Visual Studio environment.</span></span>

<span data-ttu-id="3b358-121">Pokud používáte metodiky vývoj editoru a rozhraní příkazového řádku (například Visual Studio Code a rozhraní příkazového řádku Dockeru v systému macOS nebo Windows), musíte znát každý krok, obecně podrobněji, než pokud používáte Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="3b358-121">When you're using an editor/CLI development approach (for example, Visual Studio Code plus Docker CLI on macOS or Windows), you need to know every step, generally in more detail than if you're using Visual Studio.</span></span> <span data-ttu-id="3b358-122">Další informace o práci v prostředí rozhraní příkazového řádku, najdete v e kniha [životního cyklu Kontejnerizovaných aplikací Dockeru pomocí nástrojů a Microsoft Platforms](https://aka.ms/dockerlifecycleebook/).</span><span class="sxs-lookup"><span data-stu-id="3b358-122">For more information about working in a CLI environment, see the e-book [Containerized Docker Application lifecycle with Microsoft Platforms and Tools](https://aka.ms/dockerlifecycleebook/).</span></span>

<span data-ttu-id="3b358-123">Pokud používáte Visual Studio 2017, mnoho z těchto kroků se postará služba za vás, což výrazně zvyšuje vaši produktivitu.</span><span class="sxs-lookup"><span data-stu-id="3b358-123">When you're using Visual Studio 2017, many of those steps are handled for you, which dramatically improves your productivity.</span></span> <span data-ttu-id="3b358-124">To platí zejména při používání sady Visual Studio 2017 a cílení vícekontejnerových aplikací.</span><span class="sxs-lookup"><span data-stu-id="3b358-124">This is especially true when you're using Visual Studio 2017 and targeting multi-container applications.</span></span> <span data-ttu-id="3b358-125">Například s jediným klepnutím myši, Visual Studio přidá soubor Dockerfile a docker-compose.yml do vašich projektů s konfigurací pro vaši aplikaci.</span><span class="sxs-lookup"><span data-stu-id="3b358-125">For instance, with just one mouse click, Visual Studio adds the Dockerfile and docker-compose.yml file to your projects with the configuration for your application.</span></span> <span data-ttu-id="3b358-126">Při spuštění aplikace v sadě Visual Studio sestaví image Dockeru a spustí vícekontejnerová aplikace přímo v Dockeru; dokonce i umožňuje ladit několik kontejnerů najednou.</span><span class="sxs-lookup"><span data-stu-id="3b358-126">When you run the application in Visual Studio, it builds the Docker image and runs the multi-container application directly in Docker; it even allows you to debug several containers at once.</span></span> <span data-ttu-id="3b358-127">Tyto funkce budou zvýšit rychlost vývoje.</span><span class="sxs-lookup"><span data-stu-id="3b358-127">These features will boost your development speed.</span></span>

<span data-ttu-id="3b358-128">Ale to, že sada Visual Studio provádí tyto kroky automatického neznamená, že nepotřebujete vědět, co se děje v pod tím s Dockerem.</span><span class="sxs-lookup"><span data-stu-id="3b358-128">However, just because Visual Studio makes those steps automatic doesn't mean that you don't need to know what's going on underneath with Docker.</span></span> <span data-ttu-id="3b358-129">Proto následující pokyny obsahuje podrobnosti o každém kroku.</span><span class="sxs-lookup"><span data-stu-id="3b358-129">Therefore, the following guidance details every step.</span></span>

![1 - kódu vaší aplikace](./media/image2.png)

## <a name="step-1-start-coding-and-create-your-initial-application-or-service-baseline"></a><span data-ttu-id="3b358-131">Krok 1.</span><span class="sxs-lookup"><span data-stu-id="3b358-131">Step 1.</span></span> <span data-ttu-id="3b358-132">Psaní kódu a vytvořte počáteční aplikace nebo služba směrného plánu</span><span class="sxs-lookup"><span data-stu-id="3b358-132">Start coding and create your initial application or service baseline</span></span>

<span data-ttu-id="3b358-133">Vývoj aplikací Dockeru je podobným způsobem, jakým vyvíjíte aplikaci bez Dockeru.</span><span class="sxs-lookup"><span data-stu-id="3b358-133">Developing a Docker application is similar to the way you develop an application without Docker.</span></span> <span data-ttu-id="3b358-134">Rozdíl je, že při vývoji pro Docker, jste nasazení a testování vaší aplikace nebo služby v rámci kontejnerů Docker v místním prostředí buď (nastavení virtuálního počítače s Linuxem pomocí Dockeru), nebo přímo Windows při použití kontejnerů Windows.</span><span class="sxs-lookup"><span data-stu-id="3b358-134">The difference is that while developing for Docker, you're deploying and testing your application or services running within Docker containers in your local environment (either a Linux VM setup by Docker or directly Windows if using Windows Containers).</span></span>

### <a name="set-up-your-local-environment-with-visual-studio"></a><span data-ttu-id="3b358-135">Nastavit místní prostředí pomocí sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="3b358-135">Set up your local environment with Visual Studio</span></span>

<span data-ttu-id="3b358-136">Pokud chcete začít, ujistěte se, že máte [Docker Community Edition (CE)](https://docs.docker.com/docker-for-windows/) pro Windows nainstalované, jak je popsáno v následujících pokynech:</span><span class="sxs-lookup"><span data-stu-id="3b358-136">To begin, make sure you have [Docker Community Edition (CE)](https://docs.docker.com/docker-for-windows/) for Windows installed, as explained in the following instructions:</span></span>

[<span data-ttu-id="3b358-137">Začínáme s Docker CE pro Windows</span><span class="sxs-lookup"><span data-stu-id="3b358-137">Get started with Docker CE for Windows</span></span>](https://docs.docker.com/docker-for-windows/)

<span data-ttu-id="3b358-138">Kromě toho je třeba Visual Studio 2017 verze 15.7 nebo novější, se **vývoj pro různé platformy .NET Core** úlohy, které jsou nainstalovány, jak je znázorněno v obrázku 5-2.</span><span class="sxs-lookup"><span data-stu-id="3b358-138">In addition, you need Visual Studio 2017 version 15.7 or later, with the **.NET Core cross-platform development** workload installed, as shown in Figure 5-2.</span></span>

![.NET core vývoj multiplatformních aplikací úloh výběru během instalace sady Visual Studio.](./media/image3.png)

<span data-ttu-id="3b358-140">**Obrázek 5-2**.</span><span class="sxs-lookup"><span data-stu-id="3b358-140">**Figure 5-2**.</span></span> <span data-ttu-id="3b358-141">Výběr **vývoj pro různé platformy .NET Core** úloh během instalace sady Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="3b358-141">Selecting the **.NET Core cross-platform development** workload during Visual Studio 2017 setup</span></span>

<span data-ttu-id="3b358-142">Spuštění aplikace v .NET prostý (obvykle v případě, že používání kontejnerů .NET Core) kódování ještě před povolením Docker ve vaší aplikaci a o nasazení a testování v Dockeru.</span><span class="sxs-lookup"><span data-stu-id="3b358-142">You can start coding your application in plain .NET (usually in .NET Core if you're planning to use containers) even before enabling Docker in your application and deploying and testing in Docker.</span></span> <span data-ttu-id="3b358-143">Doporučujeme však začít pracovat na Docker co nejdříve, protože, které se stanou skutečnou prostředí a můžete co nejdříve zjistit všechny problémy.</span><span class="sxs-lookup"><span data-stu-id="3b358-143">However, it is recommended that you start working on Docker as soon as possible, because that will be the real environment and any issues can be discovered as soon as possible.</span></span> <span data-ttu-id="3b358-144">To je podporováno, protože Visual Studio usnadňuje tak práci s Dockerem, téměř je transparentní, představte si třeba při ladění vícekontejnerových aplikací ze sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="3b358-144">This is encouraged because Visual Studio makes it so easy to work with Docker that it almost feels transparent—the best example when debugging multi-container applications from Visual Studio.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="3b358-145">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="3b358-145">Additional resources</span></span>

- <span data-ttu-id="3b358-146">**Začínáme s Docker CE pro Windows** \\</span><span class="sxs-lookup"><span data-stu-id="3b358-146">**Get started with Docker CE for Windows** \\</span></span>
  [https://docs.docker.com/docker-for-windows/](https://docs.docker.com/docker-for-windows/)

- <span data-ttu-id="3b358-147">**Visual Studio 2017** \\</span><span class="sxs-lookup"><span data-stu-id="3b358-147">**Visual Studio 2017** \\</span></span>
  [https://visualstudio.microsoft.com/downloads/](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)

![2 - zapisovat soubory Dockerfile](./media/image4.png)

## <a name="step-2-create-a-dockerfile-related-to-an-existing-net-base-image"></a><span data-ttu-id="3b358-149">Krok 2.</span><span class="sxs-lookup"><span data-stu-id="3b358-149">Step 2.</span></span> <span data-ttu-id="3b358-150">Vytvoření souboru Dockerfile související s existující základní image .NET</span><span class="sxs-lookup"><span data-stu-id="3b358-150">Create a Dockerfile related to an existing .NET base image</span></span>

<span data-ttu-id="3b358-151">Budete potřebovat soubor Dockerfile pro každý vlastní image, kterou chcete sestavit. soubor Dockerfile pro každý kontejner má být nasazen, musíte také, jestli nasadit automaticky ze sady Visual Studio nebo ručně pomocí rozhraní příkazového řádku Dockeru (spuštění docker a docker-compose příkazů).</span><span class="sxs-lookup"><span data-stu-id="3b358-151">You need a Dockerfile for each custom image you want to build; you also need a Dockerfile for each container to be deployed, whether you deploy automatically from Visual Studio or manually using the Docker CLI (docker run and docker-compose commands).</span></span> <span data-ttu-id="3b358-152">Pokud vaše aplikace obsahuje jeden vlastní službu, potřebujete jeden soubor Dockerfile.</span><span class="sxs-lookup"><span data-stu-id="3b358-152">If your application contains a single custom service, you need a single Dockerfile.</span></span> <span data-ttu-id="3b358-153">Pokud vaše aplikace obsahuje více služeb (stejně jako v architektuře mikroslužeb), budete potřebovat jeden soubor Dockerfile pro každou službu.</span><span class="sxs-lookup"><span data-stu-id="3b358-153">If your application contains multiple services (as in a microservices architecture), you need one Dockerfile for each service.</span></span>

<span data-ttu-id="3b358-154">Soubor Dockerfile je umístěn v kořenové složce aplikace nebo služby.</span><span class="sxs-lookup"><span data-stu-id="3b358-154">The Dockerfile is placed in the root folder of your application or service.</span></span> <span data-ttu-id="3b358-155">Obsahuje příkazy, které informace tom, jak nastavit a spustit vaše aplikace nebo služby v kontejneru Dockeru.</span><span class="sxs-lookup"><span data-stu-id="3b358-155">It contains the commands that tell Docker how to set up and run your application or service in a container.</span></span> <span data-ttu-id="3b358-156">Můžete ručně vytvořit soubor Dockerfile v kódu a přidejte do projektu spolu s .NET závislosti.</span><span class="sxs-lookup"><span data-stu-id="3b358-156">You can manually create a Dockerfile in code and add it to your project along with your .NET dependencies.</span></span>

<span data-ttu-id="3b358-157">Pomocí sady Visual Studio a jeho nástrojů Dockeru tato úloha vyžaduje jenom několik kliknutí myší.</span><span class="sxs-lookup"><span data-stu-id="3b358-157">With Visual Studio and its tools for Docker, this task requires only a few mouse clicks.</span></span> <span data-ttu-id="3b358-158">Při vytváření nového projektu v sadě Visual Studio 2017 je k dispozici možnost s názvem **podpora povolit kontejnerů (Dockeru)**, jak je znázorněno v obrázek 5-3.</span><span class="sxs-lookup"><span data-stu-id="3b358-158">When you create a new project in Visual Studio 2017, there's an option named **Enable Container (Docker) Support**, as shown in Figure 5-3.</span></span>

![Povolit podporu Dockeru políčko při vytváření nového projektu ASP.NET Core v sadě Visual Studio 2017](./media/image5.png)

<span data-ttu-id="3b358-160">**Obrázek 5 – 3**.</span><span class="sxs-lookup"><span data-stu-id="3b358-160">**Figure 5-3**.</span></span> <span data-ttu-id="3b358-161">Povolení podpory Dockeru, při vytváření nového projektu ASP.NET Core v sadě Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="3b358-161">Enabling Docker Support when creating a new ASP.NET Core project in Visual Studio 2017</span></span>

<span data-ttu-id="3b358-162">Můžete také povolit podporu Dockeru na existující projekt webové aplikace ASP.NET Core kliknutím pravým tlačítkem myši na projekt v **Průzkumníka řešení** a vyberete **přidat** > **podporu Dockeru** , jak je znázorněno v obrázek 5 – 4.</span><span class="sxs-lookup"><span data-stu-id="3b358-162">You can also enable Docker support on an existing ASP.NET Core web app project by right-clicking the project in **Solution Explorer** and selecting **Add** > **Docker Support**, as shown in Figure 5-4.</span></span>

![Přidat možnost nabídky podpory Dockeru v sadě Visual Studio](./media/image6.png)

<span data-ttu-id="3b358-164">**Obrázek 5 – 4**.</span><span class="sxs-lookup"><span data-stu-id="3b358-164">**Figure 5-4**.</span></span> <span data-ttu-id="3b358-165">Povolení podpory Dockeru v existujícím projektu Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="3b358-165">Enabling Docker support in an existing Visual Studio 2017 project</span></span>

<span data-ttu-id="3b358-166">Tato akce přidá *soubor Dockerfile* do projektu s požadovanou konfigurací a je dostupná pouze na projekty ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="3b358-166">This action adds a *Dockerfile* to the project with the required configuration, and is only available on ASP.NET Core projects.</span></span>

<span data-ttu-id="3b358-167">Podobným způsobem můžete sady Visual Studio také přidat soubor docker-compose.yml pro celé řešení s možností **Přidat > Podpora Orchestrátoru kontejnerů**.</span><span class="sxs-lookup"><span data-stu-id="3b358-167">In a similar fashion, Visual Studio can also add a docker-compose.yml file for the whole solution with the option **Add > Container Orchestrator Support**.</span></span> <span data-ttu-id="3b358-168">V kroku 4 se podíváme podrobněji tuto možnost.</span><span class="sxs-lookup"><span data-stu-id="3b358-168">In step 4, we'll explore this option in greater detail.</span></span>

### <a name="using-an-existing-official-net-docker-image"></a><span data-ttu-id="3b358-169">Použití existující oficiální image .NET Dockeru</span><span class="sxs-lookup"><span data-stu-id="3b358-169">Using an existing official .NET Docker image</span></span>

<span data-ttu-id="3b358-170">Obvykle vytvoříte vlastní image kontejneru nad základní image, můžete získat z oficiální úložiště, třeba [Docker Hubu](https://hub.docker.com/) registru.</span><span class="sxs-lookup"><span data-stu-id="3b358-170">You usually build a custom image for your container on top of a base image you get from an official repository like the [Docker Hub](https://hub.docker.com/) registry.</span></span> <span data-ttu-id="3b358-171">To je přesně co se stane na pozadí, když povolíte podporu Dockeru v sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="3b358-171">That is precisely what happens under the covers when you enable Docker support in Visual Studio.</span></span> <span data-ttu-id="3b358-172">Váš soubor Dockerfile použije existující `aspnetcore` bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="3b358-172">Your Dockerfile will use an existing `aspnetcore` image.</span></span>

<span data-ttu-id="3b358-173">Dříve jsme vysvětlit, které Image Dockeru a úložiště můžete použít, v závislosti na rozhraní framework a rozhodli jste se operační systém.</span><span class="sxs-lookup"><span data-stu-id="3b358-173">Earlier we explained which Docker images and repos you can use, depending on the framework and OS you have chosen.</span></span> <span data-ttu-id="3b358-174">Například pokud chcete používat ASP.NET Core (s Linuxem nebo Windows), obrázku je `microsoft/dotnet:2.2-aspnetcore-runtime`.</span><span class="sxs-lookup"><span data-stu-id="3b358-174">For instance, if you want to use ASP.NET Core (Linux or Windows), the image to use is `microsoft/dotnet:2.2-aspnetcore-runtime`.</span></span> <span data-ttu-id="3b358-175">Proto stačí zadat jaké základní image Dockeru, který budete používat pro váš kontejner.</span><span class="sxs-lookup"><span data-stu-id="3b358-175">Therefore, you just need to specify what base Docker image you will use for your container.</span></span> <span data-ttu-id="3b358-176">Můžete to udělat tak, že přidáte `FROM microsoft/dotnet:2.2-aspnetcore-runtime` na vašem souboru Dockerfile.</span><span class="sxs-lookup"><span data-stu-id="3b358-176">You do that by adding `FROM microsoft/dotnet:2.2-aspnetcore-runtime` to your Dockerfile.</span></span> <span data-ttu-id="3b358-177">To se automaticky provede pomocí sady Visual Studio, ale pokud byste chtěli aktualizovat verzi, aktualizujte tuto hodnotu.</span><span class="sxs-lookup"><span data-stu-id="3b358-177">This will be automatically performed by Visual Studio, but if you were to update the version, you update this value.</span></span>

<span data-ttu-id="3b358-178">Použití oficiální úložiště .NET image z Docker Hubu s číslem verze zajistí, že stejné funkce jazyka jsou k dispozici na všech počítačích (včetně vývoje, testování a produkce).</span><span class="sxs-lookup"><span data-stu-id="3b358-178">Using an official .NET image repository from Docker Hub with a version number ensures that the same language features are available on all machines (including development, testing, and production).</span></span>

<span data-ttu-id="3b358-179">Následující příklad ukazuje ukázkový soubor Dockerfile pro kontejner služby ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="3b358-179">The following example shows a sample Dockerfile for an ASP.NET Core container.</span></span>

```Dockerfile
FROM microsoft/dotnet:2.2-aspnetcore-runtime
ARG source
WORKDIR /app
EXPOSE 80
COPY ${source:-obj/Docker/publish} .
ENTRYPOINT ["dotnet", " MySingleContainerWebApp.dll "]
```

<span data-ttu-id="3b358-180">V tomto případě bitovou kopii podle verze 2.2 oficiální image Dockeru ASP.NET Core (více arch pro systémy Linux a Windows).</span><span class="sxs-lookup"><span data-stu-id="3b358-180">In this case, the image is based on version 2.2 of the official ASP.NET Core Docker image (multi-arch for Linux and Windows).</span></span> <span data-ttu-id="3b358-181">Toto je nastavení `FROM microsoft/dotnet:2.2-aspnetcore-runtime`.</span><span class="sxs-lookup"><span data-stu-id="3b358-181">This is the setting `FROM microsoft/dotnet:2.2-aspnetcore-runtime`.</span></span> <span data-ttu-id="3b358-182">(Další informace o této základní image, najdete v článku [Image Dockeru .NET Core](https://hub.docker.com/r/microsoft/dotnet/) stránky.) V souboru Dockerfile potřebujete také dáte pokyn, aby Docker pro naslouchání na portu TCP, které se použijí v době běhu (v tomto případě portem 80, nakonfigurované s nastavením VYSTAVENÍ).</span><span class="sxs-lookup"><span data-stu-id="3b358-182">(For more information about this base image, see the [.NET Core Docker Image](https://hub.docker.com/r/microsoft/dotnet/) page.) In the Dockerfile, you also need to instruct Docker to listen on the TCP port you will use at runtime (in this case, port 80, as configured with the EXPOSE setting).</span></span>

<span data-ttu-id="3b358-183">Můžete zadat další nastavení konfigurace v souboru Dockerfile, v závislosti na jazyk a rozhraní, které používáte.</span><span class="sxs-lookup"><span data-stu-id="3b358-183">You can specify additional configuration settings in the Dockerfile, depending on the language and framework you're using.</span></span> <span data-ttu-id="3b358-184">Například řádek ENTRYPOINT s `["dotnet", "MySingleContainerWebApp.dll"]` říká Dockeru spustit aplikaci .NET Core.</span><span class="sxs-lookup"><span data-stu-id="3b358-184">For instance, the ENTRYPOINT line with `["dotnet", "MySingleContainerWebApp.dll"]` tells Docker to run a .NET Core application.</span></span> <span data-ttu-id="3b358-185">Pokud používáte sadu SDK a rozhraní .NET Core CLI (rozhraní příkazového řádku dotnet) k sestavení a spuštění aplikace .NET, toto nastavení bude jiný.</span><span class="sxs-lookup"><span data-stu-id="3b358-185">If you're using the SDK and the .NET Core CLI (dotnet CLI) to build and run the .NET application, this setting would be different.</span></span> <span data-ttu-id="3b358-186">Dolní řádek je, že řádku vstupního bodu a další nastavení budou lišit v závislosti na jazyku a platformě, kterou zvolíte pro vaši aplikaci.</span><span class="sxs-lookup"><span data-stu-id="3b358-186">The bottom line is that the ENTRYPOINT line and other settings will be different depending on the language and platform you choose for your application.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="3b358-187">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="3b358-187">Additional resources</span></span>

- <span data-ttu-id="3b358-188">**Vytváření Imagí Dockeru pro aplikace .NET Core** \\</span><span class="sxs-lookup"><span data-stu-id="3b358-188">**Building Docker Images for .NET Core Applications** \\</span></span>
  [https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images](../../../core/docker/building-net-docker-images.md)

- <span data-ttu-id="3b358-189">**Vytvoření vlastní image**.</span><span class="sxs-lookup"><span data-stu-id="3b358-189">**Build your own image**.</span></span> <span data-ttu-id="3b358-190">V oficiální dokumentaci k Dockeru. \\</span><span class="sxs-lookup"><span data-stu-id="3b358-190">In the official Docker documentation.\\</span></span>
  [https://docs.docker.com/engine/tutorials/dockerimages/](https://docs.docker.com/engine/tutorials/dockerimages/)

- <span data-ttu-id="3b358-191">**Udržování aktuálnosti s Imagí kontejnerů v rozhraní .NET** \\</span><span class="sxs-lookup"><span data-stu-id="3b358-191">**Staying up-to-date with .NET Container Images** \\</span></span>
  <https://devblogs.microsoft.com/dotnet/staying-up-to-date-with-net-container-images/>

- <span data-ttu-id="3b358-192">**Pomocí .NET a Dockeru společně - DockerCon 2018 Update** \\</span><span class="sxs-lookup"><span data-stu-id="3b358-192">**Using .NET and Docker Together - DockerCon 2018 Update** \\</span></span>
  <https://devblogs.microsoft.com/dotnet/using-net-and-docker-together-dockercon-2018-update/>

### <a name="using-multi-arch-image-repositories"></a><span data-ttu-id="3b358-193">Pomocí více architektury image úložišť</span><span class="sxs-lookup"><span data-stu-id="3b358-193">Using multi-arch image repositories</span></span>

<span data-ttu-id="3b358-194">Jediné úložiště může obsahovat variant, platformy, jako jsou image Linuxu a Windows image.</span><span class="sxs-lookup"><span data-stu-id="3b358-194">A single repo can contain platform variants, such as a Linux image and a Windows image.</span></span> <span data-ttu-id="3b358-195">Tato funkce umožňuje dodavatelé, jako je Microsoft (creators základní image) k vytvoření jednoho úložiště pro víc platforem (to znamená operačních systémů Linux a Windows).</span><span class="sxs-lookup"><span data-stu-id="3b358-195">This feature allows vendors like Microsoft (base image creators) to create a single repo to cover multiple platforms (that is Linux and Windows).</span></span> <span data-ttu-id="3b358-196">Například [microsoft/dotnet](https://hub.docker.com/r/microsoft/dotnet/) úložiště k dispozici v registru Docker Hub poskytuje podporu pro systémy Linux a Windows Nano Server pomocí stejného názvu úložiště.</span><span class="sxs-lookup"><span data-stu-id="3b358-196">For example, the [microsoft/dotnet](https://hub.docker.com/r/microsoft/dotnet/) repository available in the Docker Hub registry provides support for Linux and Windows Nano Server by using the same repo name.</span></span>

<span data-ttu-id="3b358-197">Je-li zadat značky, cílení na platformu, která je explicitní jako v následujících případech:</span><span class="sxs-lookup"><span data-stu-id="3b358-197">If you specify a tag, targeting a platform that is explicit like in the following cases:</span></span>

- `microsoft/dotnet:2.2-aspnetcore-runtime-stretch-slim` \
  <span data-ttu-id="3b358-198">Cíle: .NET Core 2.2 pouze modul runtime v Linuxu</span><span class="sxs-lookup"><span data-stu-id="3b358-198">Targets: .NET Core 2.2 runtime-only on Linux</span></span>

- `microsoft/dotnet:2.2-aspnetcore-runtime-nanoserver-1809` \
  <span data-ttu-id="3b358-199">Cíle: .NET Core 2.2 pouze modul runtime Windows Nano server</span><span class="sxs-lookup"><span data-stu-id="3b358-199">Targets: .NET Core 2.2 runtime-only on Windows Nano Server</span></span>

<span data-ttu-id="3b358-200">Ale pokud zadáte stejný název image, i se stejnou značkou, více architektury obrázky (jako `aspnetcore` image) používat verzi systému Linux nebo Windows v závislosti na operačním systému hostitele Docker, že nasazujete, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="3b358-200">But, if you specify the same image name, even with the same tag, the multi-arch images (like the `aspnetcore` image) will use the Linux or Windows version depending on the Docker host OS you're deploying, as shown in the following example:</span></span>

- `microsoft/dotnet:2.2-aspnetcore-runtime` \
  <span data-ttu-id="3b358-201">Více arch: .NET Core 2.2 runtime jen v systému Linux nebo Windows Nano serveru v závislosti na operačním systému hostitele Docker</span><span class="sxs-lookup"><span data-stu-id="3b358-201">Multi-arch: .NET Core 2.2 runtime-only on Linux or Windows Nano Server depending on the Docker host OS</span></span>

<span data-ttu-id="3b358-202">Tímto způsobem, když si stáhnete obrázek z hostitele Windows, je přetáhne Windows variant a přebírání z hostitele platformy Linux stejný název image přetáhne varianty Linuxu.</span><span class="sxs-lookup"><span data-stu-id="3b358-202">This way, when you pull an image from a Windows host, it will pull the Windows variant, and pulling the same image name from a Linux host will pull the Linux variant.</span></span>

### <a name="multi-stage-builds-in-dockerfile"></a><span data-ttu-id="3b358-203">Vícefázových sestavení v souboru Dockerfile</span><span class="sxs-lookup"><span data-stu-id="3b358-203">Multi-stage builds in Dockerfile</span></span>

<span data-ttu-id="3b358-204">Soubor Dockerfile je podobný dávkový skript.</span><span class="sxs-lookup"><span data-stu-id="3b358-204">The Dockerfile is similar to a batch script.</span></span> <span data-ttu-id="3b358-205">Podobně jako co děláte, pokud jste museli nainstalovat počítač z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="3b358-205">Similar to what you would do if you had to set up the machine from the command line.</span></span>

<span data-ttu-id="3b358-206">Začíná základní image, který nastaví kolekci počáteční kontextu, je stejně jako při spuštění systému souborů, který je umístěný na hostitelském operačním systému.</span><span class="sxs-lookup"><span data-stu-id="3b358-206">It starts with a base image that sets up the initial context, it's like the startup filesystem, that sits on top of the host OS.</span></span> <span data-ttu-id="3b358-207">Není operační systém, ale můžete si představit Pokud jako "the" OS uvnitř kontejneru.</span><span class="sxs-lookup"><span data-stu-id="3b358-207">It's not an OS, but you can think of if like "the" OS inside the container.</span></span>

<span data-ttu-id="3b358-208">Spuštění každou příkazového řádku vytvoří novou vrstvu v systému souborů se změnami z předchozí, tak, aby v kombinaci, vytvářejí výsledný systému souborů.</span><span class="sxs-lookup"><span data-stu-id="3b358-208">The execution of every command line creates a new layer on the filesystem with the changes from the previous one, so that, when combined, produce the resulting filesystem.</span></span>

<span data-ttu-id="3b358-209">Protože každé nové vrstvě "ponechá" nad předchozí a výsledné velikost bitové kopie se zvyšuje s každý příkaz, bitové kopie mohou být velmi rozsáhlé, že pokud se mají zahrnout, například sady SDK potřebných k vytváření a publikování aplikace.</span><span class="sxs-lookup"><span data-stu-id="3b358-209">Since every new layer "rests" on top of the previous one and the resulting image size increases with every command, images can get very large if they have to include, for example, the SDK needed to build and publish an application.</span></span>

<span data-ttu-id="3b358-210">Je to, kde získat vícefázových sestavení do diagramů (od Dockeru 17.05 a vyšší) provedete jejich magic.</span><span class="sxs-lookup"><span data-stu-id="3b358-210">This is where multi-stage builds get into the plot (from Docker 17.05 and higher) to do their magic.</span></span>

<span data-ttu-id="3b358-211">Cílem core je, že můžete oddělit proces spuštění souboru Dockerfile ve fázích, kde fázi je počáteční obrázek za nímž následuje jedna nebo více příkazů, a poslední fáze Určuje velikost finální bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="3b358-211">The core idea is that you can separate the Dockerfile execution process in stages, where a stage is an initial image followed by one or more commands, and the last stage determines the final image size.</span></span>

<span data-ttu-id="3b358-212">Stručně řečeno vícefázových sestavení povolit rozdělení vytvoření v jiné "fáze" a pak sestavit finální image trvá pouze relevantní adresářů z dílčích etap.</span><span class="sxs-lookup"><span data-stu-id="3b358-212">In short, multi-stage builds allow splitting the creation in different "phases" and then assemble the final image taking only the relevant directories from the intermediate stages.</span></span> <span data-ttu-id="3b358-213">Obecná strategie pro použití této funkce je:</span><span class="sxs-lookup"><span data-stu-id="3b358-213">The general strategy to use this feature is:</span></span>

1. <span data-ttu-id="3b358-214">Pomocí základní image SDK (nebude vadit, jak velké), se vším potřebným k sestavení a publikování aplikace do složky a potom</span><span class="sxs-lookup"><span data-stu-id="3b358-214">Use a base SDK image (doesn't matter how large), with everything needed to build and publish the application to a folder and then</span></span>

2. <span data-ttu-id="3b358-215">Použít bitovou kopii základní, malé, pouze modul runtime a zkopírujte složky pro publikování z předchozí fáze k vytvoření malé konečném obrazu.</span><span class="sxs-lookup"><span data-stu-id="3b358-215">Use a base, small, runtime-only image and copy the publishing folder from the previous stage to produce a small final image.</span></span>

<span data-ttu-id="3b358-216">Pravděpodobně nejlepší způsob, jak porozumět vícefázové prochází souboru Dockerfile podrobně, řádek po řádku, můžeme začít s počáteční soubor Dockerfile vytvořených pomocí Visual Studia při přidání Dockeru k projektu a později se dostat do některé optimalizace.</span><span class="sxs-lookup"><span data-stu-id="3b358-216">Probably the best way to understand multi-stage is going through a Dockerfile in detail, line by line, so let's begin with the initial Dockerfile created by Visual Studio when adding Docker support to a project and will get into some optimizations later.</span></span>

<span data-ttu-id="3b358-217">Počáteční souboru Docker může vypadat přibližně takto:</span><span class="sxs-lookup"><span data-stu-id="3b358-217">The initial Dockerfile might look something like this:</span></span>

```Dockerfile
 1  FROM microsoft/dotnet:2.2-aspnetcore-runtime AS base
 2  WORKDIR /app
 3  EXPOSE 80
 4
 5  FROM microsoft/dotnet:2.2-sdk AS build
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
20  RUN dotnet build Catalog.API.csproj -c Release -0 /app
21
22  FROM build AS publish
23  RUN dotnet publish Catalog.API.csproj -c Release -0 /app
24
25  FROM base AS final
26  WORKDIR /app
27  COPY --from=publish /app
28  ENTRYPOINT ["dotnet", "Catalog.API.dll"]
```

<span data-ttu-id="3b358-218">A jedná se o řádek po řádku:</span><span class="sxs-lookup"><span data-stu-id="3b358-218">And these are the details, line by line:</span></span>

1.  <span data-ttu-id="3b358-219">Začít fáze "malé" pouze modul runtime základní Image, pojmenujte ji **základní** pro referenci.</span><span class="sxs-lookup"><span data-stu-id="3b358-219">Begin a stage with a "small" runtime-only base image, call it **base** for reference.</span></span>
2.  <span data-ttu-id="3b358-220">Vytvoření **/app** adresáře v bitové kopii.</span><span class="sxs-lookup"><span data-stu-id="3b358-220">Create **/app** directory in the image.</span></span>
3.  <span data-ttu-id="3b358-221">Zveřejnit port **80**.</span><span class="sxs-lookup"><span data-stu-id="3b358-221">Expose port **80**.</span></span>
<!-- skip -->
5.  <span data-ttu-id="3b358-222">Volání begin nové fáze "velký" Image pro vytváření a publikování **sestavení** pro referenci.</span><span class="sxs-lookup"><span data-stu-id="3b358-222">Begin a new stage with "large" image for building/publishing, call it **build** for reference.</span></span>
6.  <span data-ttu-id="3b358-223">Vytvořit adresář **/src** na obrázku.</span><span class="sxs-lookup"><span data-stu-id="3b358-223">Create directory **/src** in the image.</span></span>
7.  <span data-ttu-id="3b358-224">Až po řádek 16 kopírovat odkazované projekty **.csproj** soubory, abyste mohli později obnovit balíčky.</span><span class="sxs-lookup"><span data-stu-id="3b358-224">Up to line 16, copy referenced projects **.csproj** files, to be able to restore packages later.</span></span>
<!-- skip -->
17. <span data-ttu-id="3b358-225">Obnovení balíčků pro **Catalog.API** projektu a odkazované projekty.</span><span class="sxs-lookup"><span data-stu-id="3b358-225">Restore packages for the **Catalog.API** project and the referenced projects.</span></span>
18. <span data-ttu-id="3b358-226">Kopírování **strom volání adresář pro řešení** (s výjimkou součástí soubory a adresáře **.dockerignore** souboru) z k **/src** adresáře v bitové kopii.</span><span class="sxs-lookup"><span data-stu-id="3b358-226">Copy **all directory tree for the solution** (except the files/directories included in the **.dockerignore** file) from to the **/src** directory in the image.</span></span>
19. <span data-ttu-id="3b358-227">Změna aktuální složku na **Catalog.API** projektu.</span><span class="sxs-lookup"><span data-stu-id="3b358-227">Change current folder to **Catalog.API** project.</span></span>
20. <span data-ttu-id="3b358-228">Sestavení projektu (a další závislosti projektu) a výstup do **/app** adresáře v bitové kopii.</span><span class="sxs-lookup"><span data-stu-id="3b358-228">Build project (and other project dependencies) and output to **/app** directory in the image.</span></span>
<!-- skip -->
22. <span data-ttu-id="3b358-229">Začít nový fázi budete pokračovat z buildu, pojmenujte ji **publikovat** pro referenci.</span><span class="sxs-lookup"><span data-stu-id="3b358-229">Begin a new stage continuing from build, call it **publish** for reference.</span></span>
23. <span data-ttu-id="3b358-230">Publikování projektu (a závislostí) a výstup do **/app** adresáře v bitové kopii.</span><span class="sxs-lookup"><span data-stu-id="3b358-230">Publish project (and dependencies) and output to **/app** directory in the image.</span></span>
<!-- skip -->
25. <span data-ttu-id="3b358-231">Začít nový fázi pokračováním z **základní** a volejte jej **konečný**</span><span class="sxs-lookup"><span data-stu-id="3b358-231">Begin a new stage continuing from **base** and call it **final**</span></span>
26. <span data-ttu-id="3b358-232">Změňte aktuální adresář na **/app**</span><span class="sxs-lookup"><span data-stu-id="3b358-232">Change current directory to **/app**</span></span>
27. <span data-ttu-id="3b358-233">Kopírovat **/app** z fáze **publikovat** do aktuálního adresáře</span><span class="sxs-lookup"><span data-stu-id="3b358-233">Copy the **/app** directory from stage **publish** to the current directory</span></span>
28. <span data-ttu-id="3b358-234">Definování příkazu ke spuštění při spuštění kontejneru.</span><span class="sxs-lookup"><span data-stu-id="3b358-234">Define the command to run when the container is started.</span></span>

<span data-ttu-id="3b358-235">Nyní Pojďme prozkoumat některé optimalizace pro zlepšení výkonu celého procesu, v případě aplikaci eShopOnContainers, to znamená asi 22 minut nebo déle vytvářet kompletní řešení v kontejnery Linuxu.</span><span class="sxs-lookup"><span data-stu-id="3b358-235">Now let's explore some optimizations to improve the whole process performance that, in the case of eShopOnContainers, means about 22 minutes or more to build the complete solution in Linux containers.</span></span>

<span data-ttu-id="3b358-236">Budete využívat Docker vrstva mezipaměti funkci, která je poměrně jednoduchý: Pokud základní image a příkazy jsou stejné jako některé dříve spuštěn, může použít pouze výsledné vrstvy bez nutnosti provádět příkazy, a ušetřit tak nějakou dobu.</span><span class="sxs-lookup"><span data-stu-id="3b358-236">You'll take advantage of Docker's layer cache feature, which is quite simple: if the base image and the commands are the same as some previously executed, it can just use the resulting layer without the need to execute the commands, thus saving some time.</span></span>

<span data-ttu-id="3b358-237">Tedy zaměřme se na **sestavení** řádky 5 až 6 jsou většinou stejné fázi, ale řádky 7-17 se liší pro každou službu v aplikaci eShopOnContainers, tak mají k provedení pokaždé, když jeden, ale pokud jste změnili řádky 7 – 16:</span><span class="sxs-lookup"><span data-stu-id="3b358-237">So, let's focus on the **build** stage, lines 5-6 are mostly the same, but lines 7-17 are different for every service from eShopOnContainers, so they have to execute every single time, however if you changed lines 7-16 to:</span></span>

```
COPY . .
```

<span data-ttu-id="3b358-238">Pak budou platit stejně pro každou službu budou zkopírovány celé řešení a vytvořila větší vrstvy, ale:</span><span class="sxs-lookup"><span data-stu-id="3b358-238">Then it would be just the same for every service, it would copy the whole solution and would create a larger layer but:</span></span>

1) <span data-ttu-id="3b358-239">Proces kopírování by být provedeny pouze první (a při opětovném sestavování při změně souboru) a bude používat mezipaměť pro všechny ostatní služby a</span><span class="sxs-lookup"><span data-stu-id="3b358-239">The copy process would only be executed the first time (and when rebuilding if a file is changed) and would use the cache for all other services and</span></span>

2) <span data-ttu-id="3b358-240">Protože větší obrázek k ve stadiu zprostředkující ho, nemá vliv na velikost finální bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="3b358-240">Since the larger image occurs in an intermediate stage it, doesn't affect the final image size.</span></span>

<span data-ttu-id="3b358-241">Zahrnuje další významné optimalizace `restore` příkaz proveden v řádku 17, které se také pro každou službu aplikaci eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="3b358-241">The next significant optimization involves the `restore` command executed in line 17, which is also different for every service of eShopOnContainers.</span></span> <span data-ttu-id="3b358-242">Pokud změníte tento řádek jenom:</span><span class="sxs-lookup"><span data-stu-id="3b358-242">If you change that line to just:</span></span>

```console
RUN dotnet restore
```

<span data-ttu-id="3b358-243">To by obnovení balíčků pro celé řešení, ale pak znovu ji by udělat jenom jednou, namísto 15 časy s aktuální strategie.</span><span class="sxs-lookup"><span data-stu-id="3b358-243">It would restore the packages for the whole solution, but then again, it would do it just once, instead of the 15 times with the current strategy.</span></span>

<span data-ttu-id="3b358-244">Ale `dotnet restore` spuštěna pouze pokud je jeden projekt nebo soubor řešení ve složce, takže dosažení tohoto cíle je o něco složitější a způsob, jak vyřešit, aniž do příliš mnoho podrobností, je to:</span><span class="sxs-lookup"><span data-stu-id="3b358-244">However, `dotnet restore` only runs if there's a single project or solution file in the folder, so achieving this is a bit more complicated and the way to solve it, without getting into too many details, is this:</span></span>

1) <span data-ttu-id="3b358-245">Přidejte následující řádky do **.dockerignore**:</span><span class="sxs-lookup"><span data-stu-id="3b358-245">Add the following lines to **.dockerignore**:</span></span>

   - <span data-ttu-id="3b358-246">`*.sln`, chcete-li ignorovat všechny soubory řešení ve stromové struktuře složek hlavní</span><span class="sxs-lookup"><span data-stu-id="3b358-246">`*.sln`, to ignore all solution files in the main folder tree</span></span>

   - <span data-ttu-id="3b358-247">`!eShopOnContainers-ServicesAndWebApps.sln`, chcete-li zahrnout pouze tento soubor řešení.</span><span class="sxs-lookup"><span data-stu-id="3b358-247">`!eShopOnContainers-ServicesAndWebApps.sln`, to include only this solution file.</span></span>

2) <span data-ttu-id="3b358-248">Zahrnout `/ignoreprojectextensions:.dcproj` argument `dotnet restore`, tak také ignoruje docker-compose projektu a obnoví pouze zadané balíčky pro aplikaci eShopOnContainers ServicesAndWebApps řešení.</span><span class="sxs-lookup"><span data-stu-id="3b358-248">Include the `/ignoreprojectextensions:.dcproj` argument to `dotnet restore`, so it also ignores the docker-compose project and only restores the packages for the eShopOnContainers-ServicesAndWebApps solution.</span></span>

<span data-ttu-id="3b358-249">Poslední optimalizace prostě se to děje, že řádek 20 je redundantní, jako řádku 23 také sestavení aplikace a dodává, v podstatě hned po řádku 20, takže existuje přejde jiného příkazu časově náročné.</span><span class="sxs-lookup"><span data-stu-id="3b358-249">For the final optimization, it just happens that line 20 is redundant, as line 23 also builds the application and comes, in essence, right after line 20, so there goes another time-consuming command.</span></span>

<span data-ttu-id="3b358-250">Výsledný soubor bude:</span><span class="sxs-lookup"><span data-stu-id="3b358-250">The resulting file is then:</span></span>

```Dockerfile
 1  FROM microsoft/dotnet:2.2-aspnetcore-runtime AS base
 2  WORKDIR /app
 3  EXPOSE 80
 4
 5  FROM microsoft/dotnet:2.2-sdk AS publish
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

### <a name="creating-your-base-image-from-scratch"></a><span data-ttu-id="3b358-251">Vytvoření základní image od začátku</span><span class="sxs-lookup"><span data-stu-id="3b358-251">Creating your base image from scratch</span></span>

<span data-ttu-id="3b358-252">Vlastní základní image Dockeru můžete vytvořit úplně od začátku.</span><span class="sxs-lookup"><span data-stu-id="3b358-252">You can create your own Docker base image from scratch.</span></span> <span data-ttu-id="3b358-253">Tento scénář se nedoporučuje pro uživatele, který se spouští s Dockerem, ale pokud chcete nastavit konkrétní bity základní image, můžete tak učinit.</span><span class="sxs-lookup"><span data-stu-id="3b358-253">This scenario is not recommended for someone who is starting with Docker, but if you want to set the specific bits of your own base image, you can do so.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="3b358-254">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="3b358-254">Additional resources</span></span>

- <span data-ttu-id="3b358-255">**Více architektury .NET Core imagí**. \\</span><span class="sxs-lookup"><span data-stu-id="3b358-255">**Multi-arch .NET Core images**.\\</span></span>
  [https://github.com/dotnet/announcements/issues/14](https://github.com/dotnet/announcements/issues/14)

- <span data-ttu-id="3b358-256">**Vytvoření základní image**.</span><span class="sxs-lookup"><span data-stu-id="3b358-256">**Create a base image**.</span></span> <span data-ttu-id="3b358-257">Oficiální dokumentace k Dockeru. \\</span><span class="sxs-lookup"><span data-stu-id="3b358-257">Official Docker documentation.\\</span></span>
  [https://docs.docker.com/engine/userguide/eng-image/baseimages/](https://docs.docker.com/engine/userguide/eng-image/baseimages/)

![3. vytvoření imagí, které jsou definované na soubory Dockerfile](./media/image7.png)

## <a name="step-3-create-your-custom-docker-images-and-embed-your-application-or-service-in-them"></a><span data-ttu-id="3b358-259">Krok 3.</span><span class="sxs-lookup"><span data-stu-id="3b358-259">Step 3.</span></span> <span data-ttu-id="3b358-260">Vytvoření vlastní Image Dockeru a vložit vaše aplikace nebo služba</span><span class="sxs-lookup"><span data-stu-id="3b358-260">Create your custom Docker images and embed your application or service in them</span></span>

<span data-ttu-id="3b358-261">Pro každou službu v aplikaci budete muset vytvořit související image.</span><span class="sxs-lookup"><span data-stu-id="3b358-261">For each service in your application, you need to create a related image.</span></span> <span data-ttu-id="3b358-262">Pokud vaše aplikace se skládá z jedné služby nebo webové aplikace, potřebujete jenom jedné image.</span><span class="sxs-lookup"><span data-stu-id="3b358-262">If your application is made up of a single service or web application, you just need a single image.</span></span>

<span data-ttu-id="3b358-263">Všimněte si, že Image Dockeru se vytváří automaticky za vás v sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="3b358-263">Note that the Docker images are built automatically for you in Visual Studio.</span></span> <span data-ttu-id="3b358-264">Následující kroky jsou jenom potřebné pro pracovní postup editoru a rozhraní příkazového řádku a vysvětlení pro přehlednost o co se stane pod.</span><span class="sxs-lookup"><span data-stu-id="3b358-264">The following steps are only needed for the editor/CLI workflow and explained for clarity about what happens underneath.</span></span>

<span data-ttu-id="3b358-265">Jako vývojář, potřebujete pro vývoj a testování místně, než přejdete dokončené funkce nebo změňte na systému správy zdrojů (například na Githubu).</span><span class="sxs-lookup"><span data-stu-id="3b358-265">You, as developer, need to develop and test locally until you push a completed feature or change to your source control system (for example, to GitHub).</span></span> <span data-ttu-id="3b358-266">To znamená, že budete muset vytvoření imagí Dockeru a nasazení kontejnerů do místního hostitele Docker (Windows nebo linuxového virtuálního počítače) a spuštění, testování a ladění pro tyto místní kontejnery.</span><span class="sxs-lookup"><span data-stu-id="3b358-266">This means that you need to create the Docker images and deploy containers to a local Docker host (Windows or Linux VM) and run, test, and debug against those local containers.</span></span>

<span data-ttu-id="3b358-267">Vytvoření vlastní image v místním prostředí pomocí rozhraní příkazového řádku Dockeru a vašem souboru Dockerfile, můžete použít příkaz sestavení dockeru, jako obrázek 5 – 5.</span><span class="sxs-lookup"><span data-stu-id="3b358-267">To create a custom image in your local environment by using Docker CLI and your Dockerfile, you can use the docker build command, as in Figure 5-5.</span></span>

![Obrazovka průběhu sestavování image Dockeru](./media/image8.png)

<span data-ttu-id="3b358-269">**Obrázek 5 až 5**.</span><span class="sxs-lookup"><span data-stu-id="3b358-269">**Figure 5-5**.</span></span> <span data-ttu-id="3b358-270">Vytvoření vlastní image Dockeru</span><span class="sxs-lookup"><span data-stu-id="3b358-270">Creating a custom Docker image</span></span>

<span data-ttu-id="3b358-271">Volitelně můžete místo přímo spouštět sestavení dockeru ze složky projektu, můžete nejdřív vygenerovat nasaditelný složka se požadované knihovny .NET a binární soubory spuštěním `dotnet publish`a pak použít `docker build` příkazu.</span><span class="sxs-lookup"><span data-stu-id="3b358-271">Optionally, instead of directly running docker build from the project folder, you can first generate a deployable folder with the required .NET libraries and binaries by running `dotnet publish`, and then use the `docker build` command.</span></span>

<span data-ttu-id="3b358-272">Tím se vytvoří image Dockeru s názvem `cesardl/netcore-webapi-microservice-docker:first`.</span><span class="sxs-lookup"><span data-stu-id="3b358-272">This will create a Docker image with the name `cesardl/netcore-webapi-microservice-docker:first`.</span></span> <span data-ttu-id="3b358-273">V takovém případě: nejprve je klíčové slovo představující konkrétní verzi.</span><span class="sxs-lookup"><span data-stu-id="3b358-273">In this case, :first is a tag representing a specific version.</span></span> <span data-ttu-id="3b358-274">Tento krok můžete opakovat pro každý vlastní image, které potřebujete k vytvoření aplikace skládá Dockeru.</span><span class="sxs-lookup"><span data-stu-id="3b358-274">You can repeat this step for each custom image you need to create for your composed Docker application.</span></span>

<span data-ttu-id="3b358-275">Když aplikaci tvoří několik kontejnerů (to znamená, že je vícekontejnerová aplikace), můžete použít také `docker-compose up --build` příkazu sestavte všechny obrázky související s jediným příkazem s využitím metadat v souboru docker-compose.yml související .</span><span class="sxs-lookup"><span data-stu-id="3b358-275">When an application is made of multiple containers (that is, it is a multi-container application), you can also use the `docker-compose up --build` command to build all the related images with a single command by using the metadata exposed in the related docker-compose.yml files.</span></span>

<span data-ttu-id="3b358-276">Najdete existujících bitových kopií ve vašem místním úložišti s využitím dockeru příkaz bitové kopie, jak je znázorněno v obrázek 5 a 6.</span><span class="sxs-lookup"><span data-stu-id="3b358-276">You can find the existing images in your local repository by using the docker images command, as shown in Figure 5-6.</span></span>

![Zobrazení imagí výpis z příkazu Image dockeru](./media/image9.png)

<span data-ttu-id="3b358-278">**Obrázek 5 a 6.**</span><span class="sxs-lookup"><span data-stu-id="3b358-278">**Figure 5-6.**</span></span> <span data-ttu-id="3b358-279">Zobrazení existujících imagí pomocí příkazu Image dockeru</span><span class="sxs-lookup"><span data-stu-id="3b358-279">Viewing existing images using the docker images command</span></span>

### <a name="creating-docker-images-with-visual-studio"></a><span data-ttu-id="3b358-280">Vytváření imagí Dockeru pomocí sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="3b358-280">Creating Docker images with Visual Studio</span></span>

<span data-ttu-id="3b358-281">Při vytvoření projektu s podporou Dockeru pomocí sady Visual Studio, není explicitně vytvořit bitovou kopii.</span><span class="sxs-lookup"><span data-stu-id="3b358-281">When you use Visual Studio to create a project with Docker support, you don't explicitly create an image.</span></span> <span data-ttu-id="3b358-282">Místo toho na obrázku je vytvořen po stisknutí klávesy **F5** (nebo **Ctrl-F5**) pro spuštění dockerized aplikace nebo služby.</span><span class="sxs-lookup"><span data-stu-id="3b358-282">Instead, the image is created for you when you press **F5** (or **Ctrl-F5**) to run the dockerized application or service.</span></span> <span data-ttu-id="3b358-283">Tento krok je automatické v sadě Visual Studio a neuvidíte to uděláme, ale je důležité vědět, co se děje v pod tím.</span><span class="sxs-lookup"><span data-stu-id="3b358-283">This step is automatic in Visual Studio and you won't see it happen, but it's important that you know what's going on underneath.</span></span>

![4 – (volitelné) psaní služby v souboru docker-compose.yml](./media/image10.png)

## <a name="step-4-define-your-services-in-docker-composeyml-when-building-a-multi-container-docker-application"></a><span data-ttu-id="3b358-285">Krok 4.</span><span class="sxs-lookup"><span data-stu-id="3b358-285">Step 4.</span></span> <span data-ttu-id="3b358-286">Definování vašich služeb v docker-compose.yml při sestavování aplikace Dockeru</span><span class="sxs-lookup"><span data-stu-id="3b358-286">Define your services in docker-compose.yml when building a multi-container Docker application</span></span>

<span data-ttu-id="3b358-287">[Docker-compose.yml](https://docs.docker.com/compose/compose-file/) souboru umožňuje definovat sadu souvisejících služeb umožňující nasadit ho jako aplikace skládá pomocí příkazů nasazení.</span><span class="sxs-lookup"><span data-stu-id="3b358-287">The [docker-compose.yml](https://docs.docker.com/compose/compose-file/) file lets you define a set of related services to be deployed as a composed application with deployment commands.</span></span> <span data-ttu-id="3b358-288">Nakonfiguruje taky její vztahy závislostí a konfiguraci za běhu.</span><span class="sxs-lookup"><span data-stu-id="3b358-288">It also configures its dependency relations and run-time configuration.</span></span>

<span data-ttu-id="3b358-289">Pokud chcete použít soubor docker-compose.yml, je potřeba vytvořit soubor ve vaší hlavní nebo kořenové složky řešení, s obsahem podobné jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="3b358-289">To use a docker-compose.yml file, you need to create the file in your main or root solution folder, with content similar to that in the following example:</span></span>

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

<span data-ttu-id="3b358-290">Tento soubor docker-compose.yml je zjednodušený a sloučené verze.</span><span class="sxs-lookup"><span data-stu-id="3b358-290">This docker-compose.yml file is a simplified and merged version.</span></span> <span data-ttu-id="3b358-291">Obsahuje statické konfigurační data pro každý kontejner (např. název vlastní image), které je vždycky potřeba a konfigurační informace, které může záviset na prostředí pro nasazení, jako je připojovací řetězec.</span><span class="sxs-lookup"><span data-stu-id="3b358-291">It contains static configuration data for each container (like the name of the custom image), which is always required, and configuration information that might depend on the deployment environment, like the connection string.</span></span> <span data-ttu-id="3b358-292">V dalších částech se dozvíte, jak k rozdělení docker-compose.yml konfigurace do několika docker-compose soubory a hodnot v závislosti na prostředí a spuštění typu (ladění nebo vydání).</span><span class="sxs-lookup"><span data-stu-id="3b358-292">In later sections, you will learn how to split the docker-compose.yml configuration into multiple docker-compose files and override values depending on the environment and execution type (debug or release).</span></span>

<span data-ttu-id="3b358-293">Příklad souboru docker-compose.yml definuje čtyři služby: `webmvc` service (webová aplikace), dva mikroslužby (`ordering.api` a `basket.api`) a jedním datovým zdrojového kontejneru `sql.data`založená na systému SQL Server pro Linux spuštěný jako kontejner.</span><span class="sxs-lookup"><span data-stu-id="3b358-293">The docker-compose.yml file example defines four services: the `webmvc` service (a web application), two microservices (`ordering.api` and `basket.api`), and one data source container, `sql.data`, based on SQL Server for Linux running as a container.</span></span> <span data-ttu-id="3b358-294">Každá služba se nasadí jako kontejner, takže image Dockeru je povinné pro každý.</span><span class="sxs-lookup"><span data-stu-id="3b358-294">Each service will be deployed as a container, so a Docker image is required for each.</span></span>

<span data-ttu-id="3b358-295">Soubor docker-compose.yml určuje nejen jaké kontejnery jsou používány, ale jejich jednotlivě konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="3b358-295">The docker-compose.yml file specifies not only what containers are being used, but how they are individually configured.</span></span> <span data-ttu-id="3b358-296">Například `webmvc` definice kontejneru ve soubor .yml:</span><span class="sxs-lookup"><span data-stu-id="3b358-296">For instance, the `webmvc` container definition in the .yml file:</span></span>

- <span data-ttu-id="3b358-297">Používá předem připravené `eshop/web:latest` bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="3b358-297">Uses a pre-built `eshop/web:latest` image.</span></span> <span data-ttu-id="3b358-298">Ale můžete také nakonfigurovat na obrázku má být sestaven jako součást docker-compose spuštění další konfigurace podle sestavení: oddíl v souboru docker-compose.</span><span class="sxs-lookup"><span data-stu-id="3b358-298">However, you could also configure the image to be built as part of the docker-compose execution with an additional configuration based on a build: section in the docker-compose file.</span></span>

- <span data-ttu-id="3b358-299">Inicializuje dvou proměnných prostředí (adresa URL katalogu a OrderingUrl).</span><span class="sxs-lookup"><span data-stu-id="3b358-299">Initializes two environment variables (CatalogUrl and OrderingUrl).</span></span>

- <span data-ttu-id="3b358-300">Předává vystavené port 80 v kontejneru pro externí port 80 na hostitelském počítači.</span><span class="sxs-lookup"><span data-stu-id="3b358-300">Forwards the exposed port 80 on the container to the external port 80 on the host machine.</span></span>

- <span data-ttu-id="3b358-301">Odkazy webové aplikace v katalogu a řazení služby s nastavením depends_on.</span><span class="sxs-lookup"><span data-stu-id="3b358-301">Links the web app to the catalog and ordering service with the depends_on setting.</span></span> <span data-ttu-id="3b358-302">To způsobí, že služba Počkejte, dokud tyto služby jsou spuštěny.</span><span class="sxs-lookup"><span data-stu-id="3b358-302">This causes the service to wait until those services are started.</span></span>

<span data-ttu-id="3b358-303">Soubor docker-compose.yml v další části jsme se opakování při popisujeme k implementaci mikroslužeb a vícekontejnerových aplikací.</span><span class="sxs-lookup"><span data-stu-id="3b358-303">We will revisit the docker-compose.yml file in a later section when we cover how to implement microservices and multi-container apps.</span></span>

### <a name="working-with-docker-composeyml-in-visual-studio-2017"></a><span data-ttu-id="3b358-304">Práce s docker-compose.yml v sadě Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="3b358-304">Working with docker-compose.yml in Visual Studio 2017</span></span>

<span data-ttu-id="3b358-305">Kromě souboru Dockerfile přidat do projektu, jak už jsme zmínili dřív, a sady Visual Studio 2017 (od 15.8 na) můžete přidat podporu orchestrátoru Docker Compose do řešení.</span><span class="sxs-lookup"><span data-stu-id="3b358-305">Besides adding a Dockerfile to a project, as we mentioned before, Visual Studio 2017 (from 15.8 on) can add orchestrator support for Docker Compose to a solution.</span></span>

<span data-ttu-id="3b358-306">Když přidat podporu orchestrátoru kontejnerů, jak ukazuje obrázek 5 – 7 pro první spuštění sady Visual Studio vytvoří soubor Dockerfile pro projekt a vytvoří nový projekt (oddíl služby) ve vašem řešení s několika globálních `docker-compose*.yml` soubory a pak přidá projekt na tyto soubory.</span><span class="sxs-lookup"><span data-stu-id="3b358-306">When you add container orchestrator support, as shown in Figure 5-7, for the first time, Visual Studio creates the Dockerfile for the project and creates a new (service section) project in your solution with several global `docker-compose*.yml` files, and then adds the project to those files.</span></span> <span data-ttu-id="3b358-307">Pak můžete otevřít soubory docker-compose.yml a aktualizovat o další funkce.</span><span class="sxs-lookup"><span data-stu-id="3b358-307">You can then open the docker-compose.yml files and update them with additional features.</span></span>

<span data-ttu-id="3b358-308">Budete muset opakovat tento formulář operace každý projekt, který chcete zahrnout do souboru docker-compose.yml.</span><span class="sxs-lookup"><span data-stu-id="3b358-308">You have to repeat this operation form every project you want to include in the docker-compose.yml file.</span></span>

<span data-ttu-id="3b358-309">V době psaní tohoto návodu Visual Studio podporuje Docker Compose a Service Fabric, orchestrátorů.</span><span class="sxs-lookup"><span data-stu-id="3b358-309">At the time of this writing, Visual Studio supports Docker Compose and Service Fabric orchestrators.</span></span>

![Možnost místní nabídky do projektu aplikace ASP.NET Core přidat podporu orchestrátoru](./media/image21.png)

<span data-ttu-id="3b358-311">**Obrázek 5 – 7**.</span><span class="sxs-lookup"><span data-stu-id="3b358-311">**Figure 5-7**.</span></span> <span data-ttu-id="3b358-312">Přidání podpory Dockeru kliknutím pravým tlačítkem myši projekt ASP.NET Core v sadě Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="3b358-312">Adding Docker support in Visual Studio 2017 by right-clicking an ASP.NET Core project</span></span>

<span data-ttu-id="3b358-313">Po přidání podpory nástroje orchestrator do svého řešení v sadě Visual Studio se zobrazí nový uzel (v `docker-compose.dcproj` souboru projektu) v Průzkumníku řešení, která obsahuje soubory přidané docker-compose.yml, jak je znázorněno v obrázek 5 až 8.</span><span class="sxs-lookup"><span data-stu-id="3b358-313">After you add orchestrator support to your solution in Visual Studio, you will also see a new node (in the `docker-compose.dcproj` project file) in Solution Explorer that contains the added docker-compose.yml files, as shown in Figure 5-8.</span></span>

![docker-compose uzlu v Průzkumníkovi řešení](./media/image11.png)

<span data-ttu-id="3b358-315">**Obrázek 5 až 8**.</span><span class="sxs-lookup"><span data-stu-id="3b358-315">**Figure 5-8**.</span></span> <span data-ttu-id="3b358-316">**Docker-compose** uzel stromu přidá v okně Průzkumník řešení Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="3b358-316">The **docker-compose** tree node added in Visual Studio 2017 Solution Explorer</span></span>

<span data-ttu-id="3b358-317">Můžete nasadit vícekontejnerové aplikace pomocí docker-compose.yml jeden soubor s použitím `docker-compose up` příkazu.</span><span class="sxs-lookup"><span data-stu-id="3b358-317">You could deploy a multi-container application with a single docker-compose.yml file by using the `docker-compose up` command.</span></span> <span data-ttu-id="3b358-318">Visual Studio, ale přidá skupinu z nich tak mohou přepsat hodnoty v závislosti na prostředí (vývojové nebo produkční prostředí) a typu spuštění (vydání nebo ladícího).</span><span class="sxs-lookup"><span data-stu-id="3b358-318">However, Visual Studio adds a group of them so you can override values depending on the environment (development or production) and execution type (release or debug).</span></span> <span data-ttu-id="3b358-319">Tato funkce bude je popsáno v předchozích částech.</span><span class="sxs-lookup"><span data-stu-id="3b358-319">This capability will be explained in later sections.</span></span>

![5 – spouštění kontejnerů nebo vytvořit aplikaci](./media/image12.png)

## <a name="step-5-build-and-run-your-docker-application"></a><span data-ttu-id="3b358-321">Krok 5.</span><span class="sxs-lookup"><span data-stu-id="3b358-321">Step 5.</span></span> <span data-ttu-id="3b358-322">Sestavte a spusťte aplikaci v Dockeru</span><span class="sxs-lookup"><span data-stu-id="3b358-322">Build and run your Docker application</span></span>

<span data-ttu-id="3b358-323">Pokud vaše aplikace má pouze jeden kontejner, můžete ji spustit po nasazení na hostitele Docker (virtuální počítač nebo fyzický server).</span><span class="sxs-lookup"><span data-stu-id="3b358-323">If your application only has a single container, you can run it by deploying it to your Docker host (VM or physical server).</span></span> <span data-ttu-id="3b358-324">Nicméně pokud vaše aplikace obsahuje několik služeb, můžete nasadit ho jako aplikace skládá buď pomocí jediného příkazu rozhraní příkazového řádku (docker-compose up), nebo pomocí sady Visual Studio, které budou používat tento příkaz na pozadí.</span><span class="sxs-lookup"><span data-stu-id="3b358-324">However, if your application contains multiple services, you can deploy it as a composed application, either using a single CLI command (docker-compose up), or with Visual Studio, which will use that command under the covers.</span></span> <span data-ttu-id="3b358-325">Podívejme se na různé možnosti.</span><span class="sxs-lookup"><span data-stu-id="3b358-325">Let's look at the different options.</span></span>

### <a name="option-a-running-a-single-container-application"></a><span data-ttu-id="3b358-326">Možnost A: Spuštění aplikace jeden kontejner</span><span class="sxs-lookup"><span data-stu-id="3b358-326">Option A: Running a single-container application</span></span>

#### <a name="using-docker-cli"></a><span data-ttu-id="3b358-327">Pomocí rozhraní příkazového řádku Dockeru</span><span class="sxs-lookup"><span data-stu-id="3b358-327">Using Docker CLI</span></span>

<span data-ttu-id="3b358-328">Můžete spustit pomocí kontejneru Dockeru `docker run` příkaz, jak je znázorněno v obrázek 5 až 9:</span><span class="sxs-lookup"><span data-stu-id="3b358-328">You can run a Docker container using the `docker run` command, as shown in Figure 5-9:</span></span>

```console
  docker run -t -d -p 80:5000 cesardl/netcore-webapi-microservice-docker:first
```

<span data-ttu-id="3b358-329">Výše uvedený příkaz vytvoří novou instanci kontejneru ze zadané bitové kopie, pokaždé, když je spuštěn.</span><span class="sxs-lookup"><span data-stu-id="3b358-329">The above command will create a new container instance from the specified image, every time it's run.</span></span> <span data-ttu-id="3b358-330">Můžete použít `--name` parametr zadejte název kontejneru a pak použijte `docker start {name}` (nebo použijte id kontejneru a název automatického) ke spuštění existující instanci kontejneru.</span><span class="sxs-lookup"><span data-stu-id="3b358-330">You can use the `--name` parameter to give a name to the container and then use `docker start {name}` (or use the container id or automatic name) to run an existing container instance.</span></span>

![Zobrazení při spuštění kontejneru Dockeru pomocí dockeru, spusťte příkaz](./media/image13.png)

<span data-ttu-id="3b358-332">**Obrázek 5 až 9**.</span><span class="sxs-lookup"><span data-stu-id="3b358-332">**Figure 5-9**.</span></span> <span data-ttu-id="3b358-333">Spuštěný kontejner Docker s využitím dockeru, spusťte příkaz</span><span class="sxs-lookup"><span data-stu-id="3b358-333">Running a Docker container using the docker run command</span></span>

<span data-ttu-id="3b358-334">Příkaz v tomto případě váže interní port 5000 z kontejneru na port 80 hostitelském počítači.</span><span class="sxs-lookup"><span data-stu-id="3b358-334">In this case, the command binds the internal port 5000 of the container to port 80 of the host machine.</span></span> <span data-ttu-id="3b358-335">To znamená, že hostitel naslouchá na portu 80 a předává na portu 5000 v kontejneru.</span><span class="sxs-lookup"><span data-stu-id="3b358-335">This means that the host is listening on port 80 and forwarding to port 5000 on the container.</span></span>

<span data-ttu-id="3b358-336">Hodnota hash uvedené je id kontejneru a jí také přiřazena náhodné čitelný název Pokud `--name` není použita možnost.</span><span class="sxs-lookup"><span data-stu-id="3b358-336">The hash shown is the container id and it’s also assigned a random readable name if the `--name` option is not used.</span></span>

#### <a name="using-visual-studio"></a><span data-ttu-id="3b358-337">Pomocí sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="3b358-337">Using Visual Studio</span></span>

<span data-ttu-id="3b358-338">Pokud jste nepřidali podporu orchestrátoru kontejnerů, můžete použít také aplikaci s jedním kontejnerem v sadě Visual Studio stisknutím klávesy **Ctrl-F5** a můžete také použít **F5** pro ladění aplikace v kontejneru.</span><span class="sxs-lookup"><span data-stu-id="3b358-338">If you haven't added container orchestrator support, you can also run a single container app in Visual Studio by pressing **Ctrl-F5** and you can also use **F5** to debug the application within the container.</span></span> <span data-ttu-id="3b358-339">Kontejner spustí v místním prostředí s využitím dockeru, spusťte.</span><span class="sxs-lookup"><span data-stu-id="3b358-339">The container runs locally using docker run.</span></span>

### <a name="option-b-running-a-multi-container-application"></a><span data-ttu-id="3b358-340">Možnost B: Spuštění aplikace</span><span class="sxs-lookup"><span data-stu-id="3b358-340">Option B: Running a multi-container application</span></span>

<span data-ttu-id="3b358-341">Ve většině scénářů organizace aplikaci v Dockeru se skládá z více služeb, což znamená, že budete muset spustit vícekontejnerové aplikace, jak je znázorněno v obrázek 5 až 10.</span><span class="sxs-lookup"><span data-stu-id="3b358-341">In most enterprise scenarios, a Docker application will be composed of multiple services, which means you need to run a multi-container application, as shown in Figure 5-10.</span></span>

![Virtuální počítač s několika kontejnery Dockeru](./media/image14.png)

<span data-ttu-id="3b358-343">**Obrázek 5 až 10**.</span><span class="sxs-lookup"><span data-stu-id="3b358-343">**Figure 5-10**.</span></span> <span data-ttu-id="3b358-344">Virtuální počítač s kontejnery Dockeru nasazené</span><span class="sxs-lookup"><span data-stu-id="3b358-344">VM with Docker containers deployed</span></span>

#### <a name="using-docker-cli"></a><span data-ttu-id="3b358-345">Pomocí rozhraní příkazového řádku Dockeru</span><span class="sxs-lookup"><span data-stu-id="3b358-345">Using Docker CLI</span></span>

<span data-ttu-id="3b358-346">Ke spuštění vícekontejnerové aplikace pomocí rozhraní příkazového řádku Dockeru, můžete použít `docker-compose up` příkazu.</span><span class="sxs-lookup"><span data-stu-id="3b358-346">To run a multi-container application with the Docker CLI, you use the `docker-compose up` command.</span></span> <span data-ttu-id="3b358-347">Tento příkaz používá **docker-compose.yml** souboru, abyste měli na úrovni řešení nasazení vícekontejnerových aplikací.</span><span class="sxs-lookup"><span data-stu-id="3b358-347">This command uses the **docker-compose.yml** file that you have at the solution level to deploy a multi-container application.</span></span> <span data-ttu-id="3b358-348">Obrázek 5 – 11 můžete vidět výsledky při spuštění příkazu z adresáře hlavní řešení, která obsahuje soubor docker-compose.yml.</span><span class="sxs-lookup"><span data-stu-id="3b358-348">Figure 5-11 shows the results when running the command from your main solution directory, which contains the docker-compose.yml file.</span></span>

![Obrazovky zobrazení při spuštění docker-compose up příkaz](./media/image15.png)

<span data-ttu-id="3b358-350">**Obrázek 5 – 11**.</span><span class="sxs-lookup"><span data-stu-id="3b358-350">**Figure 5-11**.</span></span> <span data-ttu-id="3b358-351">Příklad výsledků při spuštění docker-compose up příkaz</span><span class="sxs-lookup"><span data-stu-id="3b358-351">Example results when running the docker-compose up command</span></span>

<span data-ttu-id="3b358-352">Po docker-compose up spuštění příkazu, aplikace a její související kontejnery se nasazují do hostitele Dockeru, jak je znázorněno v obrázek 5 – 10.</span><span class="sxs-lookup"><span data-stu-id="3b358-352">After the docker-compose up command runs, the application and its related containers are deployed into your Docker host, as depicted in Figure 5-10.</span></span>

#### <a name="using-visual-studio"></a><span data-ttu-id="3b358-353">Pomocí sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="3b358-353">Using Visual Studio</span></span>

<span data-ttu-id="3b358-354">Spuštění vícekontejnerové aplikace pomocí sady Visual Studio 2017 nejde získat žádná jednodušší.</span><span class="sxs-lookup"><span data-stu-id="3b358-354">Running a multi-container application using Visual Studio 2017 can't get any simpler.</span></span> <span data-ttu-id="3b358-355">Stačí stisknout **Ctrl-F5** ke spuštění nebo **F5** ladění, jako obvykle, nastavení **docker-compose** projekt jako spouštěný projekt.</span><span class="sxs-lookup"><span data-stu-id="3b358-355">You just press **Ctrl-F5** to run or **F5** to debug, as usual, setting up the **docker-compose** project as the startup project.</span></span>  <span data-ttu-id="3b358-356">Visual Studio zpracovává všechny potřebné instalační program, tak můžete vytvořit obvyklým zarážky a ladit co nakonec stanou nezávislé procesů spuštěných ve "vzdálené servery", stejně jako je například.</span><span class="sxs-lookup"><span data-stu-id="3b358-356">Visual Studio handles all needed setup, so you can create breakpoints as usual and debug what finally become independent processes running in "remote servers", just like that.</span></span>

<span data-ttu-id="3b358-357">Jak už bylo zmíněno dříve, pokaždé, když přidáte řešení podpory Dockeru do projektu v rámci řešení, že projekt je nakonfigurovaný v souboru globální docker-compose.yml (na úrovni řešení), která umožňuje spustit nebo ladit celé řešení najednou.</span><span class="sxs-lookup"><span data-stu-id="3b358-357">As mentioned before, each time you add Docker solution support to a project within a solution, that project is configured in the global (solution-level) docker-compose.yml file, which lets you run or debug the whole solution at once.</span></span> <span data-ttu-id="3b358-358">Visual Studio spustit jeden kontejner pro každý projekt, který podporuje Docker řešení povolené a provedení všech kroků interní za vás (dotnet publikovat, sestavení dockeru atd.).</span><span class="sxs-lookup"><span data-stu-id="3b358-358">Visual Studio will start one container for each project that has Docker solution support enabled, and perform all the internal steps for you (dotnet publish, docker build, etc.).</span></span>

<span data-ttu-id="3b358-359">Pokud chcete provést náhled vůbec drudgery, podívejte se na soubor:</span><span class="sxs-lookup"><span data-stu-id="3b358-359">If you want to take a peek at all the drudgery, take a look at the file:</span></span>

`{root solution folder}\obj\Docker\docker-compose.vs.debug.g.yml`

<span data-ttu-id="3b358-360">Důležitý bod je, že, jak je znázorněno v obrázek 5 – 12, v sadě Visual Studio 2017 Další **Docker** příkaz pro akci klíčové F5.</span><span class="sxs-lookup"><span data-stu-id="3b358-360">The important point here is that, as shown in Figure 5-12, in Visual Studio 2017 there is an additional **Docker** command for the F5 key action.</span></span> <span data-ttu-id="3b358-361">Tato možnost umožňuje spustit nebo ladit vícekontejnerová aplikace spuštěním všechny kontejnery, které jsou definovány v souboru docker-compose.yml na úrovni řešení.</span><span class="sxs-lookup"><span data-stu-id="3b358-361">This option lets you run or debug a multi-container application by running all the containers that are defined in the docker-compose.yml files at the solution level.</span></span> <span data-ttu-id="3b358-362">Možnost ladit více kontejnerů řešení znamená, že můžete nastavit několik zarážky, každé zarážky v jiném projektu (kontejner) a při ladění ze sady Visual Studio se zastaví na zarážkách definovány v různých projektech a běží na různé kontejnery.</span><span class="sxs-lookup"><span data-stu-id="3b358-362">The ability to debug multiple-container solutions means that you can set several breakpoints, each breakpoint in a different project (container), and while debugging from Visual Studio you will stop at breakpoints defined in different projects and running on different containers.</span></span>

![Visual Studio ladění nástrojů spuštění docker-compose projektu](./media/image16.png)

<span data-ttu-id="3b358-364">**Obrázek 5 – 12**.</span><span class="sxs-lookup"><span data-stu-id="3b358-364">**Figure 5-12**.</span></span> <span data-ttu-id="3b358-365">Spouštění vícekontejnerových aplikací v sadě Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="3b358-365">Running multi-container apps in Visual Studio 2017</span></span>

### <a name="additional-resources"></a><span data-ttu-id="3b358-366">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="3b358-366">Additional resources</span></span>

- <span data-ttu-id="3b358-367">**Nasazení kontejneru ASP.NET na vzdáleného hostitele Docker** \\</span><span class="sxs-lookup"><span data-stu-id="3b358-367">**Deploy an ASP.NET container to a remote Docker host** \\</span></span>
  [https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker](https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker)

### <a name="a-note-about-testing-and-deploying-with-orchestrators"></a><span data-ttu-id="3b358-368">Poznámka k testování a nasazení s orchestrátory</span><span class="sxs-lookup"><span data-stu-id="3b358-368">A note about testing and deploying with orchestrators</span></span>

<span data-ttu-id="3b358-369">Docker-compose up a příkazy dockeru spustit (nebo spouštění a ladění kontejnerů v sadě Visual Studio) jsou dostatečné pro testování kontejnerů ve vašem vývojovém prostředí.</span><span class="sxs-lookup"><span data-stu-id="3b358-369">The docker-compose up and docker run commands (or running and debugging the containers in Visual Studio) are adequate for testing containers in your development environment.</span></span> <span data-ttu-id="3b358-370">Ale tento přístup byste neměli používat v produkčních prostředích, kde je orchestrátorů, jako je cílem [Kubernetes](https://kubernetes.io/) nebo [Service Fabric](https://azure.microsoft.com/services/service-fabric/).</span><span class="sxs-lookup"><span data-stu-id="3b358-370">But you should not use this approach for production deployments, where you should target orchestrators like [Kubernetes](https://kubernetes.io/) or [Service Fabric](https://azure.microsoft.com/services/service-fabric/).</span></span> <span data-ttu-id="3b358-371">Pokud používáte Kubernetes je nutné použít [podů](https://kubernetes.io/docs/concepts/workloads/pods/pod/) k uspořádání kontejnery a [služby](https://kubernetes.io/docs/concepts/services-networking/service/) k síti je.</span><span class="sxs-lookup"><span data-stu-id="3b358-371">If you're using Kubernetes you have to use [pods](https://kubernetes.io/docs/concepts/workloads/pods/pod/) to organize containers and [services](https://kubernetes.io/docs/concepts/services-networking/service/) to network them.</span></span> <span data-ttu-id="3b358-372">Můžete také použít [nasazení](https://kubernetes.io/docs/concepts/workloads/controllers/deployment/) k uspořádání pod vytváření a úpravy.</span><span class="sxs-lookup"><span data-stu-id="3b358-372">You also use [deployments](https://kubernetes.io/docs/concepts/workloads/controllers/deployment/) to organize pod creation and modification.</span></span>

![6 – testování aplikace nebo mikroslužeb](./media/image17.png)

## <a name="step-6-test-your-docker-application-using-your-local-docker-host"></a><span data-ttu-id="3b358-374">Krok 6.</span><span class="sxs-lookup"><span data-stu-id="3b358-374">Step 6.</span></span> <span data-ttu-id="3b358-375">Otestujte aplikaci Dockeru pomocí místního hostitele Docker</span><span class="sxs-lookup"><span data-stu-id="3b358-375">Test your Docker application using your local Docker host</span></span>

<span data-ttu-id="3b358-376">Tento krok se liší v závislosti na tom, co aplikace dělá.</span><span class="sxs-lookup"><span data-stu-id="3b358-376">This step will vary depending on what your application is doing.</span></span> <span data-ttu-id="3b358-377">V jednoduchou aplikaci webového rozhraní .NET Core, který je nasazen jako jedním kontejnerem nebo služby můžete přístup ke službě otevřením prohlížeče na hostitele Dockeru a přejdete na tomto webu, jak je znázorněno v obrázek 5-13.</span><span class="sxs-lookup"><span data-stu-id="3b358-377">In a simple .NET Core Web application that is deployed as a single container or service, you can access the service by opening a browser on the Docker host and navigating to that site, as shown in Figure 5-13.</span></span> <span data-ttu-id="3b358-378">(Pokud se konfigurace v souboru Dockerfile mapuje kontejneru na port na hostiteli není nic jiného než 80, zahrnovat port hostitele v adrese URL.)</span><span class="sxs-lookup"><span data-stu-id="3b358-378">(If the configuration in the Dockerfile maps the container to a port on the host that is anything other than 80, include the host port in the URL.)</span></span>

![Zobrazit v prohlížeči reakce na koncový bod rozhraní API](./media/image18.png)

<span data-ttu-id="3b358-380">**Obrázek 5-13**.</span><span class="sxs-lookup"><span data-stu-id="3b358-380">**Figure 5-13**.</span></span> <span data-ttu-id="3b358-381">Příklad testování vašich aplikací Dockeru s místním prostředí s využitím místního hostitele</span><span class="sxs-lookup"><span data-stu-id="3b358-381">Example of testing your Docker application locally using localhost</span></span>

<span data-ttu-id="3b358-382">Pokud localhost neukazuje na Dockeru IP adresa hostitele (ve výchozím nastavení se při použití Docker CE by měl), přejděte k vaší službě, můžete IP adresu síťové karty v počítači.</span><span class="sxs-lookup"><span data-stu-id="3b358-382">If localhost is not pointing to the Docker host IP (by default, when using Docker CE, it should), to navigate to your service, use the IP address of your machine's network card.</span></span>

<span data-ttu-id="3b358-383">Všimněte si, že tato adresa URL v prohlížeči používá port 80, třeba konkrétní kontejner diskutovány.</span><span class="sxs-lookup"><span data-stu-id="3b358-383">Note that this URL in the browser uses port 80 for the particular container example being discussed.</span></span> <span data-ttu-id="3b358-384">Ale interně požadavky přesměrováni na portu 5000, protože bylo jak nasazení s prostředím docker, spusťte příkaz, jak je popsáno v předchozím kroku.</span><span class="sxs-lookup"><span data-stu-id="3b358-384">However, internally the requests are being redirected to port 5000, because that was how it was deployed with the docker run command, as explained in a previous step.</span></span>

<span data-ttu-id="3b358-385">Můžete také test aplikace pomocí curl z terminálu, jak je znázorněno v obrázek 5-14.</span><span class="sxs-lookup"><span data-stu-id="3b358-385">You can also test the application using curl from the terminal, as shown in Figure 5-14.</span></span> <span data-ttu-id="3b358-386">V instalaci Dockeru na Windows IP adresa hostitele Docker výchozí hodnota je vždy 10.0.75.1 kromě vlastní IP adresu vašeho počítače.</span><span class="sxs-lookup"><span data-stu-id="3b358-386">In a Docker installation on Windows, the default Docker Host IP is always 10.0.75.1 in addition to your machine's actual IP address.</span></span>

![Zobrazení reakce na koncový bod rozhraní API pomocí curl](./media/image19.png)

<span data-ttu-id="3b358-388">**Obrázek 5-14**.</span><span class="sxs-lookup"><span data-stu-id="3b358-388">**Figure 5-14**.</span></span> <span data-ttu-id="3b358-389">Příklad testování vašich aplikací Dockeru s místně pomocí curl</span><span class="sxs-lookup"><span data-stu-id="3b358-389">Example of testing your Docker application locally using curl</span></span>

### <a name="testing-and-debugging-containers-with-visual-studio-2017"></a><span data-ttu-id="3b358-390">Testování a ladění kontejnerů pomocí sady Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="3b358-390">Testing and debugging containers with Visual Studio 2017</span></span>

<span data-ttu-id="3b358-391">Při spouštění a ladění kontejnerů pomocí sady Visual Studio 2017, můžete ladit aplikaci .NET v podstatě stejným způsobem jako při spuštění bez kontejnery.</span><span class="sxs-lookup"><span data-stu-id="3b358-391">When running and debugging the containers with Visual Studio 2017, you can debug the .NET application in much the same way as you would when running without containers.</span></span>

### <a name="testing-and-debugging-without-visual-studio"></a><span data-ttu-id="3b358-392">Testování a ladění bez sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="3b358-392">Testing and debugging without Visual Studio</span></span>

<span data-ttu-id="3b358-393">Pokud vyvíjíte pomocí editoru/CLI přístup, ladění kontejnerů je obtížnější a budete chtít ladit vygenerováním trasování.</span><span class="sxs-lookup"><span data-stu-id="3b358-393">If you're developing using the editor/CLI approach, debugging containers is more difficult and you will want to debug by generating traces.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="3b358-394">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="3b358-394">Additional resources</span></span>

- <span data-ttu-id="3b358-395">**Ladění aplikací v místním kontejneru Dockeru** \\</span><span class="sxs-lookup"><span data-stu-id="3b358-395">**Debugging apps in a local Docker container** \\</span></span>
  [https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh](https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh)

- <span data-ttu-id="3b358-396">**Steve Lasker. Sestavení, ladění, nasazení aplikace ASP.NET Core s Dockerem.**</span><span class="sxs-lookup"><span data-stu-id="3b358-396">**Steve Lasker. Build, Debug, Deploy ASP.NET Core Apps with Docker.**</span></span> <span data-ttu-id="3b358-397">Video.</span><span class="sxs-lookup"><span data-stu-id="3b358-397">Video.</span></span> \
  [https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T115](https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T115)

## <a name="simplified-workflow-when-developing-containers-with-visual-studio"></a><span data-ttu-id="3b358-398">Zjednodušené pracovní postupy při vývoji kontejnery pomocí sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="3b358-398">Simplified workflow when developing containers with Visual Studio</span></span>

<span data-ttu-id="3b358-399">Efektivně pracovní postup při používání sady Visual Studio je mnohem jednodušší než při použití editoru/CLI přístup.</span><span class="sxs-lookup"><span data-stu-id="3b358-399">Effectively, the workflow when using Visual Studio is a lot simpler than if you use the editor/CLI approach.</span></span> <span data-ttu-id="3b358-400">Většina kroků vyžadují Docker související s soubor Dockerfile a soubory docker-compose.yml jsou skryta nebo zjednodušená sada Visual Studio, jak je znázorněno v obrázek 5 – 15.</span><span class="sxs-lookup"><span data-stu-id="3b358-400">Most of the steps required by Docker related to the Dockerfile and docker-compose.yml files are hidden or simplified by Visual Studio, as shown in Figure 5-15.</span></span>

![Zjednodušená pracovního postupu vývoje kontejneru pomocí sady Visual Studio: 1 - kódu vaší aplikace, 2 - podporu Dockeru přidat do projektů (jen jednou), 3 – spuštění kontejneru nebo docker-compose aplikace, 4 – testování aplikace nebo mikroslužeb, 5 – nahrání do úložiště a opakujte tento postup.](./media/image20.png)

<span data-ttu-id="3b358-402">**Obrázek 5 – 15**.</span><span class="sxs-lookup"><span data-stu-id="3b358-402">**Figure 5-15**.</span></span> <span data-ttu-id="3b358-403">Zjednodušené pracovní postupy při vývoji pomocí sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="3b358-403">Simplified workflow when developing with Visual Studio</span></span>

<span data-ttu-id="3b358-404">Kromě toho budete muset provést krok 2 (Přidání podpory Dockeru do vašich projektů) pouze jednou.</span><span class="sxs-lookup"><span data-stu-id="3b358-404">In addition, you need to perform step 2 (adding Docker support to your projects) just once.</span></span> <span data-ttu-id="3b358-405">Proto je podobný běžné vývojářské úlohy pracovního postupu, při použití rozhraní .NET pro další vývoj.</span><span class="sxs-lookup"><span data-stu-id="3b358-405">Therefore, the workflow is similar to your usual development tasks when using .NET for any other development.</span></span> <span data-ttu-id="3b358-406">Je potřeba vědět, co se děje na pozadí (procesu sestavení, jaké základní Image, kterou používáte, nasazení kontejnerů, atd.) a v některých případech bude také nutné upravit soubor Dockerfile nebo docker-compose.yml k přizpůsobení chování.</span><span class="sxs-lookup"><span data-stu-id="3b358-406">You need to know what is going on under the covers (the image build process, what base images you're using, deployment of containers, etc.) and sometimes you will also need to edit the Dockerfile or docker-compose.yml file to customize behaviors.</span></span> <span data-ttu-id="3b358-407">Ale většinu práce výrazně zjednodušuje použití sady Visual Studio, což je mnohem vyšší produktivitu.</span><span class="sxs-lookup"><span data-stu-id="3b358-407">But most of the work is greatly simplified by using Visual Studio, making you a lot more productive.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="3b358-408">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="3b358-408">Additional resources</span></span>

- <span data-ttu-id="3b358-409">**Steve Lasker. Vývoj na platformě .NET dockeru pomocí sady Visual Studio 2017** \\</span><span class="sxs-lookup"><span data-stu-id="3b358-409">**Steve Lasker. .NET Docker Development with Visual Studio 2017** \\</span></span>
  [https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T111](https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T111)

## <a name="using-powershell-commands-in-a-dockerfile-to-set-up-windows-containers"></a><span data-ttu-id="3b358-410">Pomocí příkazů prostředí PowerShell v souboru Dockerfile k nastavení kontejnery Windows</span><span class="sxs-lookup"><span data-stu-id="3b358-410">Using PowerShell commands in a Dockerfile to set up Windows Containers</span></span> 

<span data-ttu-id="3b358-411">[Kontejnery Windows](https://docs.microsoft.com/virtualization/windowscontainers/about/index) umožňují převést svoje stávající aplikace pro Windows do Image Dockeru a nasadit je pomocí stejných nástrojů jako ostatní ekosystému Dockeru.</span><span class="sxs-lookup"><span data-stu-id="3b358-411">[Windows Containers](https://docs.microsoft.com/virtualization/windowscontainers/about/index) allow you to convert your existing Windows applications into Docker images and deploy them with the same tools as the rest of the Docker ecosystem.</span></span> <span data-ttu-id="3b358-412">Pokud chcete používat kontejnery Windows, spusťte příkazy Powershellu v souboru Dockerfile, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="3b358-412">To use Windows Containers, you run PowerShell commands in the Dockerfile, as shown in the following example:</span></span>

```Dockerfile
FROM microsoft/windowsservercore
LABEL Description="IIS" Vendor="Microsoft" Version="10"
RUN powershell -Command Add-WindowsFeature Web-Server
CMD [ "ping", "localhost", "-t" ]
```

<span data-ttu-id="3b358-413">V tomto případě jsme se pomocí základní image jádra serveru systému Windows (od nastavení) a instalace služby IIS pomocí příkazu prostředí PowerShell (nastavení spuštění).</span><span class="sxs-lookup"><span data-stu-id="3b358-413">In this case, we are using a Windows Server Core base image (the FROM setting) and installing IIS with a PowerShell command (the RUN setting).</span></span> <span data-ttu-id="3b358-414">Podobným způsobem můžete také použít příkazy prostředí PowerShell nastavit další komponenty, jako je ASP.NET 4.x, .NET 4.6 nebo jiný software pro Windows.</span><span class="sxs-lookup"><span data-stu-id="3b358-414">In a similar way, you could also use PowerShell commands to set up additional components like ASP.NET 4.x, .NET 4.6, or any other Windows software.</span></span> <span data-ttu-id="3b358-415">Například následující příkaz v souboru Dockerfile Nastaví technologii ASP.NET 4.5:</span><span class="sxs-lookup"><span data-stu-id="3b358-415">For example, the following command in a Dockerfile sets up ASP.NET 4.5:</span></span>

```Dockerfile
RUN powershell add-windowsfeature web-asp-net45
```

### <a name="additional-resources"></a><span data-ttu-id="3b358-416">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="3b358-416">Additional resources</span></span>

- <span data-ttu-id="3b358-417">**aspnet-docker/Dockerfile.**</span><span class="sxs-lookup"><span data-stu-id="3b358-417">**aspnet-docker/Dockerfile.**</span></span> <span data-ttu-id="3b358-418">Příklady příkazů Powershellu spouštět z soubory dockerfile začlenit funkce Windows. \\</span><span class="sxs-lookup"><span data-stu-id="3b358-418">Example PowerShell commands to run from dockerfiles to include Windows features.\\</span></span>
  [https://github.com/Microsoft/aspnet-docker/blob/master/4.7.1-windowsservercore-ltsc2016/runtime/Dockerfile](https://github.com/Microsoft/aspnet-docker/blob/master/4.7.1-windowsservercore-ltsc2016/runtime/Dockerfile)

>[!div class="step-by-step"]
><span data-ttu-id="3b358-419">[Předchozí](index.md)
>[další](../multi-container-microservice-net-applications/index.md)</span><span class="sxs-lookup"><span data-stu-id="3b358-419">[Previous](index.md)
[Next](../multi-container-microservice-net-applications/index.md)</span></span>
