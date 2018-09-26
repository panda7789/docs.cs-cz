---
title: Pracovní postup vývoje aplikací Dockeru
description: Architektura Mikroslužeb .NET pro Kontejnerizované aplikace .NET | Pracovní postup vývoje aplikací Dockeru
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/05/2018
ms.openlocfilehash: 16e539af2ab503bddbd958ae4b60662b5923b1f1
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2018
ms.locfileid: "47088916"
---
# <a name="development-workflow-for-docker-apps"></a><span data-ttu-id="0d595-103">Pracovní postup vývoje aplikací Dockeru</span><span class="sxs-lookup"><span data-stu-id="0d595-103">Development workflow for Docker apps</span></span>

<span data-ttu-id="0d595-104">Životním cyklu vývoje aplikací začíná každý vývojář počítače, ve kterém vývojář kódy aplikace pomocí jejich upřednostňovaný jazyk a testy místně.</span><span class="sxs-lookup"><span data-stu-id="0d595-104">The application development life cycle starts at each developer’s machine, where the developer codes the application using their preferred language and tests it locally.</span></span> <span data-ttu-id="0d595-105">Bez ohledu na to, které jazyk, rozhraní a platformě vývojář rozhodne pro tento pracovní postup vývojář je vždy vývoj a testování kontejnery Dockeru, ale uděláte místně.</span><span class="sxs-lookup"><span data-stu-id="0d595-105">No matter which language, framework, and platform the developer chooses, with this workflow, the developer is always developing and testing Docker containers, but doing so locally.</span></span>

<span data-ttu-id="0d595-106">Každý kontejner (instance image Dockeru) zahrnuje následující součásti:</span><span class="sxs-lookup"><span data-stu-id="0d595-106">Each container (an instance of a Docker image) includes the following components:</span></span>

- <span data-ttu-id="0d595-107">Výběr operačního systému, (například Linuxová distribuce vytvořená, Windows Nano serveru nebo Windows Server Core).</span><span class="sxs-lookup"><span data-stu-id="0d595-107">An operating system selection (for example, a Linux distribution, Windows Nano Server, or Windows Server Core).</span></span>

- <span data-ttu-id="0d595-108">Soubory přidané vývojář (binární soubory aplikace atd.).</span><span class="sxs-lookup"><span data-stu-id="0d595-108">Files added by the developer (application binaries, etc.).</span></span>

- <span data-ttu-id="0d595-109">Informace o konfiguraci (nastavení prostředí a závislosti).</span><span class="sxs-lookup"><span data-stu-id="0d595-109">Configuration information (environment settings and dependencies).</span></span>

## <a name="workflow-for-developing-docker-container-based-applications"></a><span data-ttu-id="0d595-110">Pracovní postup pro vývoj aplikací založených na kontejnerech Dockeru</span><span class="sxs-lookup"><span data-stu-id="0d595-110">Workflow for developing Docker container-based applications</span></span>

<span data-ttu-id="0d595-111">Tato část popisuje *vnitřní smyčky* pracovní postup vývoje aplikací založených na kontejnerech Dockeru.</span><span class="sxs-lookup"><span data-stu-id="0d595-111">This section describes the *inner-loop* development workflow for Docker container-based applications.</span></span> <span data-ttu-id="0d595-112">Vnitřní smyčky pracovního postupu znamená, že se zohledněním širší pracovních postupů DevOps a právě se zaměřuje na vývojové práce vykonané na počítači pro vývojáře.</span><span class="sxs-lookup"><span data-stu-id="0d595-112">The inner-loop workflow means it is not taking into account the broader DevOps workflow and just focuses on the development work done on the developer’s computer.</span></span> <span data-ttu-id="0d595-113">Počáteční kroky k nastavení prostředí nejsou zahrnuty, protože ty se provede jen jednou.</span><span class="sxs-lookup"><span data-stu-id="0d595-113">The initial steps to set up the environment are not included, since those are done only once.</span></span>

<span data-ttu-id="0d595-114">Aplikace se skládá z vlastní služby a další knihovny (závislosti).</span><span class="sxs-lookup"><span data-stu-id="0d595-114">An application is composed of your own services plus additional libraries (dependencies).</span></span> <span data-ttu-id="0d595-115">Níže jsou uvedeny základní kroky, které obvykle provést při sestavování aplikace Dockeru, jak je znázorněno na obrázku 5-1.</span><span class="sxs-lookup"><span data-stu-id="0d595-115">The following are the basic steps you usually take when building a Docker application, as illustrated in Figure 5-1.</span></span>

![Krok za krokem pracovního postupu pro vývoj obrázek kontejnerizované aplikace Dockeru](./media/image1.png)

<span data-ttu-id="0d595-117">**Obrázek 5-1.**</span><span class="sxs-lookup"><span data-stu-id="0d595-117">**Figure 5-1.**</span></span> <span data-ttu-id="0d595-118">Krok za krokem pracovního postupu pro vývoj Docker kontejnerizovaných aplikací</span><span class="sxs-lookup"><span data-stu-id="0d595-118">Step-by-step workflow for developing Docker containerized apps</span></span>

<span data-ttu-id="0d595-119">V této příručce je podrobně popsán tento celý proces a všemi hlavními kroky jsou vysvětleny se zaměříte na prostředí Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="0d595-119">In this guide, this whole process is detailed and every major step is explained by focusing on a Visual Studio environment.</span></span>

<span data-ttu-id="0d595-120">Při použití metodiky vývoj editoru a rozhraní příkazového řádku (například Visual Studio Code a rozhraní příkazového řádku Dockeru v systému macOS nebo Windows), musíte znát každý krok, obecně podrobnější než při použití sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="0d595-120">When you are using an editor/CLI development approach (for example, Visual Studio Code plus Docker CLI on macOS or Windows), you need to know every step, generally in more detail than if you are using Visual Studio.</span></span> <span data-ttu-id="0d595-121">Další informace o práci v prostředí rozhraní příkazového řádku, najdete v e kniha [životního cyklu Kontejnerizovaných aplikací Dockeru pomocí nástrojů a Microsoft Platforms](http://aka.ms/dockerlifecycleebook/).</span><span class="sxs-lookup"><span data-stu-id="0d595-121">For more information about working in a CLI environment, see the e-book [Containerized Docker Application lifecycle with Microsoft Platforms and Tools](http://aka.ms/dockerlifecycleebook/).</span></span>

<span data-ttu-id="0d595-122">Při používání sady Visual Studio, mnoho z těchto kroků se postará služba za vás, což výrazně zvyšuje vaši produktivitu.</span><span class="sxs-lookup"><span data-stu-id="0d595-122">When you're using Visual Studio, many of those steps are handled for you, which dramatically improves your productivity.</span></span> <span data-ttu-id="0d595-123">To platí zejména při používání sady Visual Studio 2017 a cílení vícekontejnerových aplikací.</span><span class="sxs-lookup"><span data-stu-id="0d595-123">This is especially true when you are using Visual Studio 2017 and targeting multi-container applications.</span></span> <span data-ttu-id="0d595-124">Například s jediným klepnutím myši, sada Visual Studio přidá *soubor Dockerfile* a *docker-compose.yml* souborů pro projekty s konfigurací pro vaši aplikaci.</span><span class="sxs-lookup"><span data-stu-id="0d595-124">For instance, with just one mouse click, Visual Studio adds the *Dockerfile* and *docker-compose.yml* files to your projects with the configuration for your application.</span></span> <span data-ttu-id="0d595-125">Při spuštění aplikace v sadě Visual Studio vytvoří image Dockeru a spustí vícekontejnerová aplikace přímo v Dockeru.</span><span class="sxs-lookup"><span data-stu-id="0d595-125">When you run the application in Visual Studio, it builds the Docker image and runs the multi-container application directly in Docker.</span></span> <span data-ttu-id="0d595-126">Dokonce i umožňuje ladit několik kontejnerů najednou.</span><span class="sxs-lookup"><span data-stu-id="0d595-126">It even allows you to debug several containers at once.</span></span> <span data-ttu-id="0d595-127">Tyto funkce zvýšit rychlost vývoje.</span><span class="sxs-lookup"><span data-stu-id="0d595-127">These features boost your development speed.</span></span>

<span data-ttu-id="0d595-128">V dokumentu, který následuje vám vysvětlíme, co se děje "pod pokličkou" s Dockerem.</span><span class="sxs-lookup"><span data-stu-id="0d595-128">In the guidance that follows, we explain what's happening "under the covers" with Docker.</span></span>

![Krok 1 – kód aplikace grafiky](./media/image2.png)

## <a name="step-1-start-coding-and-create-your-initial-application-or-service-baseline"></a><span data-ttu-id="0d595-130">Krok 1.</span><span class="sxs-lookup"><span data-stu-id="0d595-130">Step 1.</span></span> <span data-ttu-id="0d595-131">Psaní kódu a vytvořte počáteční aplikace nebo služba směrného plánu</span><span class="sxs-lookup"><span data-stu-id="0d595-131">Start coding and create your initial application or service baseline</span></span>

<span data-ttu-id="0d595-132">Vývoj aplikací Dockeru je podobným způsobem, jakým vyvíjíte aplikaci bez Dockeru.</span><span class="sxs-lookup"><span data-stu-id="0d595-132">Developing a Docker application is similar to the way you develop an application without Docker.</span></span> <span data-ttu-id="0d595-133">Rozdíl je, že při vývoji pro Docker, máte nasazení a testování vaší aplikace nebo služby v rámci kontejnerů Docker v místním prostředí.</span><span class="sxs-lookup"><span data-stu-id="0d595-133">The difference is that while developing for Docker, you are deploying and testing your application or services running within Docker containers in your local environment.</span></span> <span data-ttu-id="0d595-134">Kontejner může být kontejneru Linuxu nebo kontejner Windows.</span><span class="sxs-lookup"><span data-stu-id="0d595-134">The container can be either a Linux container or a Windows container.</span></span>

### <a name="set-up-your-local-environment-with-visual-studio"></a><span data-ttu-id="0d595-135">Nastavit místní prostředí pomocí sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="0d595-135">Set up your local environment with Visual Studio</span></span>

<span data-ttu-id="0d595-136">Pokud chcete začít, ujistěte se, že máte [Docker Community Edition (CE)](https://www.docker.com/community-edition) pro Windows nainstalované, jak je popsáno v následujících pokynech:</span><span class="sxs-lookup"><span data-stu-id="0d595-136">To begin, make sure you have [Docker Community Edition (CE)](https://www.docker.com/community-edition) for Windows installed, as explained in the following instructions:</span></span>

[<span data-ttu-id="0d595-137">Začínáme s Docker CE pro Windows</span><span class="sxs-lookup"><span data-stu-id="0d595-137">Get started with Docker CE for Windows</span></span>](https://docs.docker.com/docker-for-windows/)

<span data-ttu-id="0d595-138">Kromě toho je třeba Visual Studio 2017 se sadou **vývoj pro různé platformy .NET Core** úlohy, které jsou nainstalovány, jak je znázorněno v obrázku 5-2.</span><span class="sxs-lookup"><span data-stu-id="0d595-138">In addition, you need Visual Studio 2017 with the **.NET Core cross-platform development** workload installed, as shown in Figure 5-2.</span></span>

![](./media/image3.png)

<span data-ttu-id="0d595-139">**Obrázek 5-2**.</span><span class="sxs-lookup"><span data-stu-id="0d595-139">**Figure 5-2**.</span></span> <span data-ttu-id="0d595-140">Výběr **.NET Core a Docker** úloh během instalace sady Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="0d595-140">Selecting the **.NET Core and Docker** workload during Visual Studio 2017 setup</span></span>

<span data-ttu-id="0d595-141">Můžete začít kódování aplikace v .NET prostý (obvykle v .NET Core, pokud máte v úmyslu používat kontejnery) ještě před povolením Docker ve vaší aplikaci a o nasazení a testování v Dockeru.</span><span class="sxs-lookup"><span data-stu-id="0d595-141">You can start coding your application in plain .NET (usually in .NET Core if you are planning to use containers) even before enabling Docker in your application and deploying and testing in Docker.</span></span> <span data-ttu-id="0d595-142">Doporučujeme však začít pracovat na Docker co nejdříve, protože, které se stanou skutečnou prostředí a můžete co nejdříve zjistit všechny problémy.</span><span class="sxs-lookup"><span data-stu-id="0d595-142">However, it is recommended that you start working on Docker as soon as possible, because that will be the real environment and any issues can be discovered as soon as possible.</span></span> <span data-ttu-id="0d595-143">To je podporováno, protože Visual Studio usnadňuje tak práci s Dockerem, téměř je transparentní, představte si třeba při ladění vícekontejnerových aplikací ze sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="0d595-143">This is encouraged because Visual Studio makes it so easy to work with Docker that it almost feels transparent — the best example when debugging multi-container applications from Visual Studio.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="0d595-144">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="0d595-144">Additional resources</span></span>

- <span data-ttu-id="0d595-145">**Začínáme s Docker CE pro Windows**</span><span class="sxs-lookup"><span data-stu-id="0d595-145">**Get started with Docker CE for Windows**</span></span>

   [*https://docs.docker.com/docker-for-windows/*](https://docs.docker.com/docker-for-windows/)

- <span data-ttu-id="0d595-146">**Visual Studio 2017**</span><span class="sxs-lookup"><span data-stu-id="0d595-146">**Visual Studio 2017**</span></span>

   [*https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs*](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)

![Krok 2: zápis soubory Dockerfile grafiky](./media/image4.png)

## <a name="step-2-create-a-dockerfile-related-to-an-existing-net-base-image"></a><span data-ttu-id="0d595-148">Krok 2.</span><span class="sxs-lookup"><span data-stu-id="0d595-148">Step 2.</span></span> <span data-ttu-id="0d595-149">Vytvoření souboru Dockerfile související s existující základní image .NET</span><span class="sxs-lookup"><span data-stu-id="0d595-149">Create a Dockerfile related to an existing .NET base image</span></span>

<span data-ttu-id="0d595-150">Budete potřebovat soubor Dockerfile pro každý vlastní image, kterou chcete sestavit. soubor Dockerfile pro každý kontejner má být nasazen, musíte také, jestli nasadit automaticky ze sady Visual Studio nebo ručně pomocí rozhraní příkazového řádku Dockeru (spuštění docker a docker-compose příkazů).</span><span class="sxs-lookup"><span data-stu-id="0d595-150">You need a Dockerfile for each custom image you want to build; you also need a Dockerfile for each container to be deployed, whether you deploy automatically from Visual Studio or manually using the Docker CLI (docker run and docker-compose commands).</span></span> <span data-ttu-id="0d595-151">Pokud vaše aplikace obsahuje jeden vlastní službu, potřebujete jeden soubor Dockerfile.</span><span class="sxs-lookup"><span data-stu-id="0d595-151">If your application contains a single custom service, you need a single Dockerfile.</span></span> <span data-ttu-id="0d595-152">Pokud vaše aplikace obsahuje více služeb (stejně jako v architektuře mikroslužeb), budete potřebovat jeden soubor Dockerfile pro každou službu.</span><span class="sxs-lookup"><span data-stu-id="0d595-152">If your application contains multiple services (as in a microservices architecture), you need one Dockerfile for each service.</span></span>

<span data-ttu-id="0d595-153">Soubor Dockerfile je umístěn v kořenové složce aplikace nebo služby.</span><span class="sxs-lookup"><span data-stu-id="0d595-153">The Dockerfile is placed in the root folder of your application or service.</span></span> <span data-ttu-id="0d595-154">Obsahuje příkazy, které informace tom, jak nastavit a spustit vaše aplikace nebo služby v kontejneru Dockeru.</span><span class="sxs-lookup"><span data-stu-id="0d595-154">It contains the commands that tell Docker how to set up and run your application or service in a container.</span></span> <span data-ttu-id="0d595-155">Můžete ručně vytvořit soubor Dockerfile v kódu a přidejte do projektu spolu s .NET závislosti.</span><span class="sxs-lookup"><span data-stu-id="0d595-155">You can manually create a Dockerfile in code and add it to your project along with your .NET dependencies.</span></span>

<span data-ttu-id="0d595-156">Pomocí Visual Studio Tools for Docker tato úloha vyžaduje jenom několik kliknutí myší.</span><span class="sxs-lookup"><span data-stu-id="0d595-156">With Visual Studio Tools for Docker, this task requires only a few mouse clicks.</span></span> <span data-ttu-id="0d595-157">Při vytváření nového projektu v sadě Visual Studio 2017 je k dispozici možnost s názvem **povolit podporu Dockeru**, jak je znázorněno v obrázek 5-3.</span><span class="sxs-lookup"><span data-stu-id="0d595-157">When you create a new project in Visual Studio 2017, there's an option named **Enable Docker Support**, as shown in Figure 5-3.</span></span>

![Povolení podpory Dockeru, při vytváření nového projektu v sadě Visual Studio 2017](./media/image5.png)

<span data-ttu-id="0d595-159">**Obrázek 5 – 3**.</span><span class="sxs-lookup"><span data-stu-id="0d595-159">**Figure 5-3**.</span></span> <span data-ttu-id="0d595-160">Povolení podpory Dockeru, při vytváření nového projektu v sadě Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="0d595-160">Enabling Docker Support when creating a new project in Visual Studio 2017</span></span>

<span data-ttu-id="0d595-161">Můžete také povolit podporu Dockeru na existující projekt webové aplikace .NET Core kliknutím pravým tlačítkem myši na projekt v **Průzkumníka řešení** a vyberete **přidat** > **podporu Dockeru** , jak je znázorněno v obrázek 5 – 4.</span><span class="sxs-lookup"><span data-stu-id="0d595-161">You can also enable Docker support on an existing .NET Core web app project by right-clicking the project in **Solution Explorer** and selecting **Add** > **Docker Support**, as shown in Figure 5-4.</span></span>

![Přidat možnost nabídky podpory Dockeru v sadě Visual Studio](./media/add-docker-support.png)

<span data-ttu-id="0d595-163">**Obrázek 5 – 4**.</span><span class="sxs-lookup"><span data-stu-id="0d595-163">**Figure 5-4**.</span></span> <span data-ttu-id="0d595-164">Povolení podpory Dockeru v existujícím projektu Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="0d595-164">Enabling Docker support in an existing Visual Studio 2017 project</span></span>

<span data-ttu-id="0d595-165">Tato akce přidá *soubor Dockerfile* do projektu s požadovanou konfigurací a je dostupný jenom u projektů webové aplikace .NET Core.</span><span class="sxs-lookup"><span data-stu-id="0d595-165">This action adds a *Dockerfile* to the project with the required configuration, and is only available on .NET Core web app projects.</span></span>

<span data-ttu-id="0d595-166">Chcete-li přidat *docker-compose.yml* souboru pro celé řešení, klikněte pravým tlačítkem na projekt v **Průzkumníka řešení** a vyberte **přidat**  >   **Podpora Orchestrátoru kontejnerů**, jak je znázorněno v obrázek 5 – 5.</span><span class="sxs-lookup"><span data-stu-id="0d595-166">To add a *docker-compose.yml* file for the whole solution, right-click on the project in **Solution Explorer** and select **Add** > **Container Orchestrator Support**, as shown in Figure 5-5.</span></span>

![Přidat možnost nabídky podpory produktu orchestrator kontejnerů v sadě Visual Studio](./media/add-container-orchestrator-support.png)

<span data-ttu-id="0d595-168">**Obrázek 5 až 5**.</span><span class="sxs-lookup"><span data-stu-id="0d595-168">**Figure 5-5**.</span></span> <span data-ttu-id="0d595-169">Přidat podporu orchestrátoru kontejnerů do existujícího projektu v sadě Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="0d595-169">Adding container orchestrator support to an existing project in Visual Studio 2017.</span></span>

<span data-ttu-id="0d595-170">V následujících částech popisujeme informace, které přejde do každé z těchto souborů.</span><span class="sxs-lookup"><span data-stu-id="0d595-170">In the following sections, we describe the information that goes into each of those files.</span></span> <span data-ttu-id="0d595-171">Visual Studio může provést tuto práci za vás, ale je užitečné k pochopení, co je potřeba k souboru Dockerfile.</span><span class="sxs-lookup"><span data-stu-id="0d595-171">Visual Studio can do this work for you, but it is useful to understand what goes into a Dockerfile.</span></span>

### <a name="option-a-creating-a-project-using-an-existing-official-net-docker-image"></a><span data-ttu-id="0d595-172">Odpověď: možnost Vytvoření projektu pomocí existující oficiální image .NET Dockeru</span><span class="sxs-lookup"><span data-stu-id="0d595-172">Option A: Creating a project using an existing official .NET Docker image</span></span>

<span data-ttu-id="0d595-173">Obvykle vytvoříte vlastní image kontejneru nad základní image, můžete získat z oficiální úložiště na [Docker Hubu](https://hub.docker.com/) registru.</span><span class="sxs-lookup"><span data-stu-id="0d595-173">You usually build a custom image for your container on top of a base image you can get from an official repository at the [Docker Hub](https://hub.docker.com/) registry.</span></span> <span data-ttu-id="0d595-174">To je přesně co se stane na pozadí, když povolíte podporu Dockeru v sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="0d595-174">That is precisely what happens under the covers when you enable Docker support in Visual Studio.</span></span> <span data-ttu-id="0d595-175">Soubor Dockerfile použije existující image aspnetcore.</span><span class="sxs-lookup"><span data-stu-id="0d595-175">The Dockerfile uses an existing aspnetcore image.</span></span>

<span data-ttu-id="0d595-176">Dříve jsme vysvětlit, které Image Dockeru a úložiště můžete použít, v závislosti na rozhraní framework a rozhodli jste se operační systém.</span><span class="sxs-lookup"><span data-stu-id="0d595-176">Earlier we explained which Docker images and repos you can use, depending on the framework and OS you have chosen.</span></span> <span data-ttu-id="0d595-177">Například pokud chcete používat ASP.NET Core (s Linuxem nebo Windows), obrázku je microsoft / aspnetcore:2.0.</span><span class="sxs-lookup"><span data-stu-id="0d595-177">For instance, if you want to use ASP.NET Core (Linux or Windows), the image to use is microsoft/aspnetcore:2.0.</span></span> <span data-ttu-id="0d595-178">Proto stačí zadat jaké základní image Dockeru, který budete používat pro váš kontejner.</span><span class="sxs-lookup"><span data-stu-id="0d595-178">Therefore, you just need to specify what base Docker image you will use for your container.</span></span> <span data-ttu-id="0d595-179">Můžete to udělat tak, že přidáte od Microsoftu nebo aspnetcore:2.0 na vašem souboru Dockerfile.</span><span class="sxs-lookup"><span data-stu-id="0d595-179">You do that by adding FROM microsoft/aspnetcore:2.0 to your Dockerfile.</span></span> <span data-ttu-id="0d595-180">To se provádí automaticky pomocí sady Visual Studio, ale pokud byste chtěli aktualizovat verzi, aktualizujte tuto hodnotu.</span><span class="sxs-lookup"><span data-stu-id="0d595-180">This is automatically performed by Visual Studio, but if you were to update the version, you update this value.</span></span>

<span data-ttu-id="0d595-181">Použití oficiální úložiště .NET image z Docker Hubu s číslem verze zajistí, že stejné funkce jazyka jsou k dispozici na všech počítačích (včetně vývoje, testování a produkce).</span><span class="sxs-lookup"><span data-stu-id="0d595-181">Using an official .NET image repository from Docker Hub with a version number ensures that the same language features are available on all machines (including development, testing, and production).</span></span>

<span data-ttu-id="0d595-182">Následující příklad ukazuje ukázkový soubor Dockerfile pro kontejner služby ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="0d595-182">The following example shows a sample Dockerfile for an ASP.NET Core container.</span></span>

```Dockerfile
FROM microsoft/aspnetcore:2.0

ARG source

WORKDIR /app

EXPOSE 80

COPY ${source:-obj/Docker/publish} .

ENTRYPOINT ["dotnet", " MySingleContainerWebApp.dll "]
```

<span data-ttu-id="0d595-183">V tomto případě kontejner je založená na verzi 2.0 oficiální Image Dockeru ASP.NET Core (více arch pro systémy Linux a Windows).</span><span class="sxs-lookup"><span data-stu-id="0d595-183">In this case, the container is based on version 2.0 of the official ASP.NET Core Docker image (multi-arch for Linux and Windows).</span></span> <span data-ttu-id="0d595-184">Toto je nastavení `FROM microsoft/aspnetcore:2.0`.</span><span class="sxs-lookup"><span data-stu-id="0d595-184">This is the setting `FROM microsoft/aspnetcore:2.0`.</span></span> <span data-ttu-id="0d595-185">(Další informace o této základní image, najdete v článku [Image Dockeru ASP.NET Core](https://hub.docker.com/r/microsoft/aspnetcore/) stránky a [Image Dockeru .NET Core](https://hub.docker.com/r/microsoft/dotnet/) stránky.) V souboru Dockerfile potřebujete také dáte pokyn, aby Docker pro naslouchání na portu TCP, které se použijí v době běhu (v tomto případě portem 80, nakonfigurované s nastavením VYSTAVENÍ).</span><span class="sxs-lookup"><span data-stu-id="0d595-185">(For more information about this base image, see the [ASP.NET Core Docker Image](https://hub.docker.com/r/microsoft/aspnetcore/) page and the [.NET Core Docker Image](https://hub.docker.com/r/microsoft/dotnet/) page.) In the Dockerfile, you also need to instruct Docker to listen on the TCP port you will use at runtime (in this case, port 80, as configured with the EXPOSE setting).</span></span>

<span data-ttu-id="0d595-186">Můžete zadat další nastavení konfigurace v souboru Dockerfile, v závislosti na jazyk a rozhraní, které používáte.</span><span class="sxs-lookup"><span data-stu-id="0d595-186">You can specify additional configuration settings in the Dockerfile, depending on the language and framework you are using.</span></span> <span data-ttu-id="0d595-187">Například řádek ENTRYPOINT s \["dotnet", "MySingleContainerWebApp.dll"\] říká Dockeru spustit aplikaci .NET Core.</span><span class="sxs-lookup"><span data-stu-id="0d595-187">For instance, the ENTRYPOINT line with \["dotnet", "MySingleContainerWebApp.dll"\] tells Docker to run a .NET Core application.</span></span> <span data-ttu-id="0d595-188">Pokud používáte sadu SDK a rozhraní .NET Core CLI (rozhraní příkazového řádku dotnet) k sestavení a spuštění aplikace .NET, toto nastavení bude jiný.</span><span class="sxs-lookup"><span data-stu-id="0d595-188">If you are using the SDK and the .NET Core CLI (dotnet CLI) to build and run the .NET application, this setting would be different.</span></span> <span data-ttu-id="0d595-189">Dolní řádek je, že řádku vstupního bodu a další nastavení budou lišit v závislosti na jazyku a platformě, kterou zvolíte pro vaši aplikaci.</span><span class="sxs-lookup"><span data-stu-id="0d595-189">The bottom line is that the ENTRYPOINT line and other settings will be different depending on the language and platform you choose for your application.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="0d595-190">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="0d595-190">Additional resources</span></span>

- <span data-ttu-id="0d595-191">**Vytváření imagí Dockeru pro aplikace .NET Core**</span><span class="sxs-lookup"><span data-stu-id="0d595-191">**Building Docker Images for .NET Core Applications**</span></span>

   [*https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images*](../../../core/docker/building-net-docker-images.md)

- <span data-ttu-id="0d595-192">**Vytvoření vlastní image**.</span><span class="sxs-lookup"><span data-stu-id="0d595-192">**Build your own image**.</span></span> <span data-ttu-id="0d595-193">V oficiální dokumentaci k Dockeru.</span><span class="sxs-lookup"><span data-stu-id="0d595-193">In the official Docker documentation.</span></span>

   [*https://docs.docker.com/engine/tutorials/dockerimages/*](https://docs.docker.com/engine/tutorials/dockerimages/)

### <a name="using-multi-arch-image-repositories"></a><span data-ttu-id="0d595-194">Pomocí více architektury image úložišť</span><span class="sxs-lookup"><span data-stu-id="0d595-194">Using multi-arch image repositories</span></span>

<span data-ttu-id="0d595-195">Jediné úložiště může obsahovat variant, platformy, jako jsou image Linuxu a Windows image.</span><span class="sxs-lookup"><span data-stu-id="0d595-195">A single repo can contain platform variants, such as a Linux image and a Windows image.</span></span> <span data-ttu-id="0d595-196">Tato funkce umožňuje dodavatelé, jako je Microsoft (creators základní image) k vytvoření jednoho úložiště pro víc platforem (to znamená operačních systémů Linux a Windows).</span><span class="sxs-lookup"><span data-stu-id="0d595-196">This feature allows vendors like Microsoft (base image creators) to create a single repo to cover multiple platforms (that is Linux and Windows).</span></span> <span data-ttu-id="0d595-197">Například [microsoft/dotnet](https://hub.docker.com/r/microsoft/aspnetcore/) úložiště k dispozici v registru Docker Hub poskytuje podporu pro systémy Linux a Windows Nano Server pomocí stejného názvu úložiště.</span><span class="sxs-lookup"><span data-stu-id="0d595-197">For example, the [microsoft/dotnet](https://hub.docker.com/r/microsoft/aspnetcore/) repository available in the Docker Hub registry provides support for Linux and Windows Nano Server by using the same repo name.</span></span>

<span data-ttu-id="0d595-198">Je-li zadat značky, cílení na platformu, která je explicitní jako v následujících případech:</span><span class="sxs-lookup"><span data-stu-id="0d595-198">If you specify a tag, targeting a platform that is explicit like in the following cases:</span></span>

- <span data-ttu-id="0d595-199">**microsoft/aspnetcore:2.0.0-jessie**</span><span class="sxs-lookup"><span data-stu-id="0d595-199">**microsoft/aspnetcore:2.0.0-jessie**</span></span>

        .NET Core 2.0 runtime-only on Linux

- <span data-ttu-id="0d595-200">**microsoft/aspnetcore:2.0.0-nanoserver**</span><span class="sxs-lookup"><span data-stu-id="0d595-200">**microsoft/aspnetcore:2.0.0-nanoserver**</span></span>

        .NET Core 2.0 runtime-only on Windows Nano Server

<span data-ttu-id="0d595-201">Ale a toto je nový od poloviny 2017, pokud zadáte stejný název image, i se stejnou značkou, nových imagí více architektury (např. image aspnetcore, která podporuje více arch) budou používat verzi systému Linux nebo Windows v závislosti na nasazujete hostitele Docker operačního systému , jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="0d595-201">But, and this is new since mid-2017, if you specify the same image name, even with the same tag, the new multi-arch images (like the aspnetcore image, which supports multi-arch) will use the Linux or Windows version depending on the Docker host OS you are deploying, as shown in the following example:</span></span>

- <span data-ttu-id="0d595-202">**microsoft/aspnetcore:2.0**</span><span class="sxs-lookup"><span data-stu-id="0d595-202">**microsoft/aspnetcore:2.0**</span></span>

        Multi-arch: .NET Core 2.0 runtime-only on Linux or Windows Nano Server depending on the Docker host OS

<span data-ttu-id="0d595-203">Tímto způsobem, když si stáhnete obrázek z hostitele Windows, je přetáhne Windows variant a přebírání z hostitele platformy Linux stejný název image přetáhne varianty Linuxu.</span><span class="sxs-lookup"><span data-stu-id="0d595-203">This way, when you pull an image from a Windows host, it will pull the Windows variant, and pulling the same image name from a Linux host will pull the Linux variant.</span></span>

### <a name="option-b-creating-your-base-image-from-scratch"></a><span data-ttu-id="0d595-204">Možnost B: vytvoříte základní image od začátku</span><span class="sxs-lookup"><span data-stu-id="0d595-204">Option B: Creating your base image from scratch</span></span>

<span data-ttu-id="0d595-205">Vlastní základní image Dockeru můžete vytvořit úplně od začátku.</span><span class="sxs-lookup"><span data-stu-id="0d595-205">You can create your own Docker base image from scratch.</span></span> <span data-ttu-id="0d595-206">Tento scénář se nedoporučuje pro uživatele, který se spouští s Dockerem, ale pokud chcete nastavit konkrétní bity základní image, můžete tak učinit.</span><span class="sxs-lookup"><span data-stu-id="0d595-206">This scenario is not recommended for someone who is starting with Docker, but if you want to set the specific bits of your own base image, you can do so.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="0d595-207">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="0d595-207">Additional resources</span></span>

- <span data-ttu-id="0d595-208">**Více architektury .NET Core imagí**.</span><span class="sxs-lookup"><span data-stu-id="0d595-208">**Multi-arch .NET Core images**.</span></span>

   https://github.com/dotnet/announcements/issues/14

- <span data-ttu-id="0d595-209">**Vytvoření základní image**.</span><span class="sxs-lookup"><span data-stu-id="0d595-209">**Create a base image**.</span></span> <span data-ttu-id="0d595-210">Oficiální dokumentace k Dockeru.</span><span class="sxs-lookup"><span data-stu-id="0d595-210">Official Docker documentation.</span></span>

   [*https://docs.docker.com/engine/userguide/eng-image/baseimages/*](https://docs.docker.com/engine/userguide/eng-image/baseimages/)

![Krok 3: vytvoření bitové kopie grafiky](./media/image7.png)

## <a name="step-3-create-your-custom-docker-images-and-embed-your-application-or-service-in-them"></a><span data-ttu-id="0d595-212">Krok 3.</span><span class="sxs-lookup"><span data-stu-id="0d595-212">Step 3.</span></span> <span data-ttu-id="0d595-213">Vytvoření vlastní Image Dockeru a vložit vaše aplikace nebo služba</span><span class="sxs-lookup"><span data-stu-id="0d595-213">Create your custom Docker images and embed your application or service in them</span></span>

<span data-ttu-id="0d595-214">Pro každou službu v aplikaci budete muset vytvořit související image.</span><span class="sxs-lookup"><span data-stu-id="0d595-214">For each service in your application, you need to create a related image.</span></span> <span data-ttu-id="0d595-215">Pokud vaše aplikace se skládá z jedné služby nebo webové aplikace, potřebujete jenom jedné image.</span><span class="sxs-lookup"><span data-stu-id="0d595-215">If your application is made up of a single service or web application, you just need a single image.</span></span>

<span data-ttu-id="0d595-216">Image Dockeru se vytváří automaticky za vás v sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="0d595-216">The Docker images are built automatically for you in Visual Studio.</span></span> <span data-ttu-id="0d595-217">Následující kroky jsou jenom potřebné pro pracovní postup editoru a rozhraní příkazového řádku a vysvětlení pro přehlednost o co se stane pod.</span><span class="sxs-lookup"><span data-stu-id="0d595-217">The following steps are only needed for the editor/CLI workflow and explained for clarity about what happens underneath.</span></span>

<span data-ttu-id="0d595-218">Jako vývojář, potřebujete pro vývoj a testování místně, než přejdete dokončené funkce nebo změňte na systému správy zdrojů (například na Githubu).</span><span class="sxs-lookup"><span data-stu-id="0d595-218">You, as developer, need to develop and test locally until you push a completed feature or change to your source control system (for example, to GitHub).</span></span> <span data-ttu-id="0d595-219">To znamená, že budete muset vytvoření imagí Dockeru a nasazení kontejnerů do místního hostitele Docker (Windows nebo linuxového virtuálního počítače) a spuštění, testování a ladění pro tyto místní kontejnery.</span><span class="sxs-lookup"><span data-stu-id="0d595-219">This means that you need to create the Docker images and deploy containers to a local Docker host (Windows or Linux VM) and run, test, and debug against those local containers.</span></span>

<span data-ttu-id="0d595-220">Vytvoření vlastní image v místním prostředí pomocí rozhraní příkazového řádku Dockeru a vašem souboru Dockerfile, můžete použít příkaz sestavení dockeru, jako obrázek 5 – 5.</span><span class="sxs-lookup"><span data-stu-id="0d595-220">To create a custom image in your local environment by using Docker CLI and your Dockerfile, you can use the docker build command, as in Figure 5-5.</span></span>

![Vytvoření vlastní image Dockeru](./media/image8.png)

<span data-ttu-id="0d595-222">**Obrázek 5 až 5**.</span><span class="sxs-lookup"><span data-stu-id="0d595-222">**Figure 5-5**.</span></span> <span data-ttu-id="0d595-223">Vytvoření vlastní image Dockeru</span><span class="sxs-lookup"><span data-stu-id="0d595-223">Creating a custom Docker image</span></span>

<span data-ttu-id="0d595-224">Volitelně můžete místo přímo spouštět sestavení dockeru ze složky projektu, můžete nejdřív vygenerovat nasaditelný složka se požadované knihovny .NET a binární soubory spuštěním dotnet publikovat a použijte příkaz sestavení dockeru.</span><span class="sxs-lookup"><span data-stu-id="0d595-224">Optionally, instead of directly running docker build from the project folder, you can first generate a deployable folder with the required .NET libraries and binaries by running dotnet publish, and then use the docker build command.</span></span>

<span data-ttu-id="0d595-225">Tím se vytvoří image Dockeru s názvem **cesardl/netcore-webapi mikroslužeb – docker: první**.</span><span class="sxs-lookup"><span data-stu-id="0d595-225">This will create a Docker image with the name **cesardl/netcore-webapi-microservice-docker:first**.</span></span> <span data-ttu-id="0d595-226">V takovém případě: nejprve je klíčové slovo představující konkrétní verzi.</span><span class="sxs-lookup"><span data-stu-id="0d595-226">In this case, :first is a tag representing a specific version.</span></span> <span data-ttu-id="0d595-227">Tento krok můžete opakovat pro každý vlastní image, které potřebujete k vytvoření aplikace skládá Dockeru.</span><span class="sxs-lookup"><span data-stu-id="0d595-227">You can repeat this step for each custom image you need to create for your composed Docker application.</span></span>

<span data-ttu-id="0d595-228">Když aplikaci tvoří několik kontejnerů (to znamená, že je vícekontejnerová aplikace), můžete použít také docker-compose up - příkaz sestavení k sestavení všechny obrázky související s jediným příkazem s využitím metadat v související soubory docker-compose.yml.</span><span class="sxs-lookup"><span data-stu-id="0d595-228">When an application is made of multiple containers (that is, it is a multi-container application), you can also use the docker-compose up --build command to build all the related images with a single command by using the metadata exposed in the related docker-compose.yml files.</span></span>

<span data-ttu-id="0d595-229">Najdete existujících bitových kopií ve vašem místním úložišti s využitím dockeru příkaz bitové kopie, jak je znázorněno v obrázek 5 a 6.</span><span class="sxs-lookup"><span data-stu-id="0d595-229">You can find the existing images in your local repository by using the docker images command, as shown in Figure 5-6.</span></span>

![Zobrazení existujících imagí pomocí příkazu Image dockeru](./media/image9.png)

<span data-ttu-id="0d595-231">**Obrázek 5 a 6.**</span><span class="sxs-lookup"><span data-stu-id="0d595-231">**Figure 5-6.**</span></span> <span data-ttu-id="0d595-232">Zobrazení existujících imagí pomocí příkazu Image dockeru</span><span class="sxs-lookup"><span data-stu-id="0d595-232">Viewing existing images using the docker images command</span></span>

### <a name="creating-docker-images-with-visual-studio"></a><span data-ttu-id="0d595-233">Vytváření imagí Dockeru pomocí sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="0d595-233">Creating Docker images with Visual Studio</span></span>

<span data-ttu-id="0d595-234">Při vytvoření projektu s podporou Dockeru pomocí sady Visual Studio, není explicitně vytvořit bitovou kopii.</span><span class="sxs-lookup"><span data-stu-id="0d595-234">When you use Visual Studio to create a project with Docker support, you don't explicitly create an image.</span></span> <span data-ttu-id="0d595-235">Místo toho na obrázku je vytvořen po stisknutí klávesy **F5** pro spuštění dockerized aplikace nebo služby.</span><span class="sxs-lookup"><span data-stu-id="0d595-235">Instead, the image is created for you when you press **F5** to run the dockerized application or service.</span></span> <span data-ttu-id="0d595-236">Tento krok je automatické v sadě Visual Studio a neuvidíte to uděláme, ale je důležité vědět, co se děje v pod tím.</span><span class="sxs-lookup"><span data-stu-id="0d595-236">This step is automatic in Visual Studio and you won't see it happen, but it's important that you know what's going on underneath.</span></span>

![Krok 4: definování grafiku služby](./media/image10.png)

## <a name="step-4-define-your-services-in-docker-composeyml-when-building-a-multi-container-docker-application"></a><span data-ttu-id="0d595-238">Krok 4.</span><span class="sxs-lookup"><span data-stu-id="0d595-238">Step 4.</span></span> <span data-ttu-id="0d595-239">Definování vašich služeb v docker-compose.yml při sestavování aplikace Dockeru</span><span class="sxs-lookup"><span data-stu-id="0d595-239">Define your services in docker-compose.yml when building a multi-container Docker application</span></span>

<span data-ttu-id="0d595-240">[Docker-compose.yml](https://docs.docker.com/compose/compose-file/) souboru umožňuje definovat sadu souvisejících služeb umožňující nasadit ho jako aplikace skládá pomocí příkazů nasazení.</span><span class="sxs-lookup"><span data-stu-id="0d595-240">The [docker-compose.yml](https://docs.docker.com/compose/compose-file/) file lets you define a set of related services to be deployed as a composed application with deployment commands.</span></span>

<span data-ttu-id="0d595-241">Pokud chcete použít soubor docker-compose.yml, je potřeba vytvořit soubor ve vaší hlavní nebo kořenové složky řešení, s obsahem podobné jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="0d595-241">To use a docker-compose.yml file, you need to create the file in your main or root solution folder, with content similar to that in the following example:</span></span>

```yml
version: '3'

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
      - ConnectionString=Server=sql.data;Database=CatalogDB;…
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

<span data-ttu-id="0d595-242">Tento soubor docker-compose.yml je zjednodušený a sloučené verze.</span><span class="sxs-lookup"><span data-stu-id="0d595-242">This docker-compose.yml file is a simplified and merged version.</span></span> <span data-ttu-id="0d595-243">Obsahuje statické konfigurační data pro každý kontejner (např. název vlastní image), která se vždy vztahuje, a navíc informace o konfiguraci, která může záviset na prostředí pro nasazení, jako je připojovací řetězec.</span><span class="sxs-lookup"><span data-stu-id="0d595-243">It contains static configuration data for each container (like the name of the custom image), which always applies, plus configuration information that might depend on the deployment environment, like the connection string.</span></span> <span data-ttu-id="0d595-244">V dalších částech se dozvíte, jak můžete rozdělit do několika konfiguraci docker-compose.yml docker-compose soubory a hodnot v závislosti na prostředí a spuštění typu (ladění nebo vydání).</span><span class="sxs-lookup"><span data-stu-id="0d595-244">In later sections, you will learn how you can split the docker-compose.yml configuration into multiple docker-compose files and override values depending on the environment and execution type (debug or release).</span></span>

<span data-ttu-id="0d595-245">Příklad souboru docker-compose.yml definuje čtyři služby: webmvc service (webová aplikace), dva mikroslužby (catalog.api a ordering.api) a jeden datový zdroj kontejnery sql.data, založené na systému SQL Server pro Linux spuštěný jako kontejner.</span><span class="sxs-lookup"><span data-stu-id="0d595-245">The docker-compose.yml file example defines four services: the webmvc service (a web application), two microservices (catalog.api and ordering.api), and one data source container, sql.data, based on SQL Server for Linux running as a container.</span></span> <span data-ttu-id="0d595-246">Každá služba se nasadí jako kontejner, takže image Dockeru je povinné pro každý.</span><span class="sxs-lookup"><span data-stu-id="0d595-246">Each service is deployed as a container, so a Docker image is required for each.</span></span>

<span data-ttu-id="0d595-247">Soubor docker-compose.yml určuje nejen jaké kontejnery jsou používány, ale jejich jednotlivě konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="0d595-247">The docker-compose.yml file specifies not only what containers are being used, but how they are individually configured.</span></span> <span data-ttu-id="0d595-248">Například webmvc definice kontejneru ve soubor .yml:</span><span class="sxs-lookup"><span data-stu-id="0d595-248">For instance, the webmvc container definition in the .yml file:</span></span>

- <span data-ttu-id="0d595-249">Pomocí předem sestavených eshop / webové: nejnovější verzi image.</span><span class="sxs-lookup"><span data-stu-id="0d595-249">Uses a pre-built eshop/web:latest image.</span></span> <span data-ttu-id="0d595-250">Ale můžete také nakonfigurovat na obrázku má být sestaven jako součást docker-compose spuštění další konfigurace podle sestavení: oddíl v souboru docker-compose.</span><span class="sxs-lookup"><span data-stu-id="0d595-250">However, you could also configure the image to be built as part of the docker-compose execution with an additional configuration based on a build: section in the docker-compose file.</span></span>

- <span data-ttu-id="0d595-251">Inicializuje dvou proměnných prostředí (adresa URL katalogu a OrderingUrl).</span><span class="sxs-lookup"><span data-stu-id="0d595-251">Initializes two environment variables (CatalogUrl and OrderingUrl).</span></span>

- <span data-ttu-id="0d595-252">Předává vystavené port 80 v kontejneru pro externí port 80 na hostitelském počítači.</span><span class="sxs-lookup"><span data-stu-id="0d595-252">Forwards the exposed port 80 on the container to the external port 80 on the host machine.</span></span>

- <span data-ttu-id="0d595-253">Odkazy webové aplikace v katalogu a řazení služby s závisí\_na nastavení.</span><span class="sxs-lookup"><span data-stu-id="0d595-253">Links the web app to the catalog and ordering service with the depends\_on setting.</span></span> <span data-ttu-id="0d595-254">To způsobí, že služba Počkejte, dokud tyto služby jsou spuštěny.</span><span class="sxs-lookup"><span data-stu-id="0d595-254">This causes the service to wait until those services are started.</span></span>

<span data-ttu-id="0d595-255">Soubor docker-compose.yml v další části jsme se opakování při popisujeme k implementaci mikroslužeb a vícekontejnerových aplikací.</span><span class="sxs-lookup"><span data-stu-id="0d595-255">We will revisit the docker-compose.yml file in a later section when we cover how to implement microservices and multi-container apps.</span></span>

### <a name="working-with-docker-composeyml-in-visual-studio-2017"></a><span data-ttu-id="0d595-256">Práce s docker-compose.yml v sadě Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="0d595-256">Working with docker-compose.yml in Visual Studio 2017</span></span>

<span data-ttu-id="0d595-257">Když přidáte podporu orchestrátoru kontejnerů do projektu webové aplikace, jak je znázorněno v obrázek 5 – 7, Visual Studio přidá do řešení, které obsahuje soubor docker-compose.yml oddíl služby (projekt).</span><span class="sxs-lookup"><span data-stu-id="0d595-257">When you add container orchestrator support to a web app project, as shown in Figure 5-7, Visual Studio adds a service section (project) to the solution that contains a docker-compose.yml file.</span></span> <span data-ttu-id="0d595-258">Toto je snadný způsob, jak spustit sestavování řešení více kontejnerů.</span><span class="sxs-lookup"><span data-stu-id="0d595-258">This is an easy way to start composing a multiple-container solution.</span></span>

![Přidání položky nabídky podpory produktu orchestrator kontejnerů v sadě Visual Studio](./media/add-container-orchestrator-support.png)

<span data-ttu-id="0d595-260">**Obrázek 5 – 7**.</span><span class="sxs-lookup"><span data-stu-id="0d595-260">**Figure 5-7**.</span></span> <span data-ttu-id="0d595-261">Přidání podpory Dockeru kliknutím pravým tlačítkem myši projekt ASP.NET Core v sadě Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="0d595-261">Adding Docker support in Visual Studio 2017 by right-clicking an ASP.NET Core project</span></span>

<span data-ttu-id="0d595-262">Soubor Dockerfile přidat podporu orchestrátoru kontejnerů přidá do vašeho projektu, (pokud ještě neexistuje).</span><span class="sxs-lookup"><span data-stu-id="0d595-262">Adding container orchestrator support adds the Dockerfile to your project (if it doesn't already exist).</span></span> <span data-ttu-id="0d595-263">Přidá také informace o konfiguraci do souboru docker-compose.yml globální na úrovni řešení.</span><span class="sxs-lookup"><span data-stu-id="0d595-263">It also adds configuration information to a global docker-compose.yml file at the solution level.</span></span> <span data-ttu-id="0d595-264">Zobrazí se nový uzel projektu ( *docker compose.dcproj* souboru projektu) v **Průzkumníku řešení** , která obsahuje soubor docker-compose.yml, jak je znázorněno v obrázek 5 až 8.</span><span class="sxs-lookup"><span data-stu-id="0d595-264">You'll see a new project node (the *docker-compose.dcproj* project file) in **Solution Explorer** that contains the docker-compose.yml file, as shown in Figure 5-8.</span></span>

![docker-compose uzlu v Průzkumníkovi řešení](./media/docker-compose-files.png)

<span data-ttu-id="0d595-266">**Obrázek 5 až 8**.</span><span class="sxs-lookup"><span data-stu-id="0d595-266">**Figure 5-8**.</span></span> <span data-ttu-id="0d595-267">**Docker-compose** uzel stromu přidá v okně Průzkumník řešení Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="0d595-267">The **docker-compose** tree node added in Visual Studio 2017 Solution Explorer</span></span>

<span data-ttu-id="0d595-268">Můžete otevřít soubor docker-compose.yml a aktualizovat ho s dalšími funkcemi.</span><span class="sxs-lookup"><span data-stu-id="0d595-268">You can then open the docker-compose.yml file and update it with additional features.</span></span>

<span data-ttu-id="0d595-269">Vícekontejnerové aplikace pomocí docker-compose.yml jednoho souboru můžete nasadit pomocí `docker-compose up` příkazu.</span><span class="sxs-lookup"><span data-stu-id="0d595-269">You can deploy a multi-container application with a single docker-compose.yml file by using the `docker-compose up` command.</span></span>

![Krok 5: obrázek spuštění aplikace](./media/image12.png)

## <a name="step-5-build-and-run-your-docker-application"></a><span data-ttu-id="0d595-271">Krok 5.</span><span class="sxs-lookup"><span data-stu-id="0d595-271">Step 5.</span></span> <span data-ttu-id="0d595-272">Sestavte a spusťte aplikaci v Dockeru</span><span class="sxs-lookup"><span data-stu-id="0d595-272">Build and run your Docker application</span></span>

<span data-ttu-id="0d595-273">Pokud vaše aplikace má pouze jeden kontejner, můžete ji spustit po nasazení na hostitele Docker (virtuální počítač nebo fyzický server).</span><span class="sxs-lookup"><span data-stu-id="0d595-273">If your application only has a single container, you can run it by deploying it to your Docker host (VM or physical server).</span></span> <span data-ttu-id="0d595-274">Nicméně pokud vaše aplikace obsahuje několik služeb, můžete nasadit ho jako aplikace skládá buď pomocí jediného příkazu rozhraní příkazového řádku (docker-compose up), nebo pomocí sady Visual Studio, které budou používat tento příkaz na pozadí.</span><span class="sxs-lookup"><span data-stu-id="0d595-274">However, if your application contains multiple services, you can deploy it as a composed application, either using a single CLI command (docker-compose up), or with Visual Studio, which will use that command under the covers.</span></span> <span data-ttu-id="0d595-275">Podívejme se na různé možnosti.</span><span class="sxs-lookup"><span data-stu-id="0d595-275">Let’s look at the different options.</span></span>

### <a name="option-a-run-a-single-container-app"></a><span data-ttu-id="0d595-276">Možnost odpověď: Spusťte aplikaci jeden kontejner</span><span class="sxs-lookup"><span data-stu-id="0d595-276">Option A: Run a single-container app</span></span>

#### <a name="docker-cli"></a><span data-ttu-id="0d595-277">Rozhraní příkazového řádku dockeru</span><span class="sxs-lookup"><span data-stu-id="0d595-277">Docker CLI</span></span>

<span data-ttu-id="0d595-278">Můžete spustit kontejner Docker s využitím dockeru, spusťte příkaz jako obrázek 5 až 9:</span><span class="sxs-lookup"><span data-stu-id="0d595-278">You can run a Docker container using the docker run command, as in Figure 5-9:</span></span>

```console
  docker run -t -d -p 80:5000 cesardl/netcore-webapi-microservice-docker:first
```

![Spuštěný kontejner Docker s využitím dockeru, spusťte příkaz](./media/image13.png)

<span data-ttu-id="0d595-280">**Obrázek 5 až 9**.</span><span class="sxs-lookup"><span data-stu-id="0d595-280">**Figure 5-9**.</span></span> <span data-ttu-id="0d595-281">Spuštěný kontejner Docker s využitím dockeru, spusťte příkaz</span><span class="sxs-lookup"><span data-stu-id="0d595-281">Running a Docker container using the docker run command</span></span>

<span data-ttu-id="0d595-282">Příkaz v tomto případě váže interní port 5000 z kontejneru na port 80 hostitelském počítači.</span><span class="sxs-lookup"><span data-stu-id="0d595-282">In this case, the command binds the internal port 5000 of the container to port 80 of the host machine.</span></span> <span data-ttu-id="0d595-283">To znamená, že hostitel naslouchá na portu 80 a předává na portu 5000 v kontejneru.</span><span class="sxs-lookup"><span data-stu-id="0d595-283">This means that the host is listening on port 80 and forwarding to port 5000 on the container.</span></span>

#### <a name="visual-studio"></a><span data-ttu-id="0d595-284">Visual Studio</span><span class="sxs-lookup"><span data-stu-id="0d595-284">Visual Studio</span></span>

<span data-ttu-id="0d595-285">Pokud jste nepřidali podporu orchestrátoru kontejnerů, můžete použít také aplikaci s jedním kontejnerem v sadě Visual Studio stisknutím klávesy **F5**.</span><span class="sxs-lookup"><span data-stu-id="0d595-285">If you haven't added container orchestrator support, you can also run a single container app in Visual Studio by pressing **F5**.</span></span> <span data-ttu-id="0d595-286">Kontejner spustí v místním prostředí s využitím dockeru, spusťte.</span><span class="sxs-lookup"><span data-stu-id="0d595-286">The container runs locally using docker run.</span></span>

### <a name="option-b-run-a-multi-container-app"></a><span data-ttu-id="0d595-287">Možnost B: spuštění aplikace s více kontejnerů</span><span class="sxs-lookup"><span data-stu-id="0d595-287">Option B: Run a multi-container app</span></span>

<span data-ttu-id="0d595-288">Ve většině scénářů organizace aplikaci v Dockeru se skládá z více služeb, což znamená, že budete muset spustit vícekontejnerové aplikace, jak je znázorněno v obrázek 5 až 10.</span><span class="sxs-lookup"><span data-stu-id="0d595-288">In most enterprise scenarios, a Docker application will be composed of multiple services, which means you need to run a multi-container application, as shown in Figure 5-10.</span></span>

![Obrázek znázorňující pomocí kontejnerů Dockeru nasazených virtuálních počítačů](./media/image14.png)

<span data-ttu-id="0d595-290">**Obrázek 5 až 10**.</span><span class="sxs-lookup"><span data-stu-id="0d595-290">**Figure 5-10**.</span></span> <span data-ttu-id="0d595-291">Virtuální počítač s kontejnery Dockeru nasazené</span><span class="sxs-lookup"><span data-stu-id="0d595-291">VM with Docker containers deployed</span></span>

#### <a name="docker-cli"></a><span data-ttu-id="0d595-292">Rozhraní příkazového řádku dockeru</span><span class="sxs-lookup"><span data-stu-id="0d595-292">Docker CLI</span></span>

<span data-ttu-id="0d595-293">Ke spuštění vícekontejnerové aplikace pomocí rozhraní příkazového řádku Dockeru, můžete spustit docker-compose up příkazu.</span><span class="sxs-lookup"><span data-stu-id="0d595-293">To run a multi-container application with the Docker CLI, you can run the docker-compose up command.</span></span> <span data-ttu-id="0d595-294">Tento soubor používá docker-compose.yml příkaz, abyste měli na úrovni řešení nasazení vícekontejnerových aplikací.</span><span class="sxs-lookup"><span data-stu-id="0d595-294">This command uses the docker-compose.yml file that you have at the solution level to deploy a multi-container application.</span></span> <span data-ttu-id="0d595-295">Obrázek 5 – 11 můžete vidět výsledky při spuštění příkazu z adresáře hlavního projektu, který obsahuje soubor docker-compose.yml.</span><span class="sxs-lookup"><span data-stu-id="0d595-295">Figure 5-11 shows the results when running the command from your main project directory, which contains the docker-compose.yml file.</span></span>

![Příklad výsledků při spuštění docker-compose up příkaz](./media/image15.png)

<span data-ttu-id="0d595-297">**Obrázek 5 – 11**.</span><span class="sxs-lookup"><span data-stu-id="0d595-297">**Figure 5-11**.</span></span> <span data-ttu-id="0d595-298">Příklad výsledků při spuštění docker-compose up příkaz</span><span class="sxs-lookup"><span data-stu-id="0d595-298">Example results when running the docker-compose up command</span></span>

<span data-ttu-id="0d595-299">Po docker-compose up spuštění příkazu, aplikace a její související kontejnery se nasazují do hostitele Dockeru.</span><span class="sxs-lookup"><span data-stu-id="0d595-299">After the docker-compose up command runs, the application and its related containers are deployed into your Docker host.</span></span>

#### <a name="visual-studio"></a><span data-ttu-id="0d595-300">Visual Studio</span><span class="sxs-lookup"><span data-stu-id="0d595-300">Visual Studio</span></span>

<span data-ttu-id="0d595-301">Zprovoznění vícekontejnerové aplikace pomocí sady Visual Studio 2017 je jednoduché.</span><span class="sxs-lookup"><span data-stu-id="0d595-301">Running a multi-container application using Visual Studio 2017 is simple.</span></span> <span data-ttu-id="0d595-302">Pouze spustit vícekontejnerové aplikace, ale budete moci ladit jejím kontejnerům přímo ze sady Visual Studio můžete nastavovat zarážky regulárních.</span><span class="sxs-lookup"><span data-stu-id="0d595-302">Not only can you run the multi-container application, but you're able to debug all its containers directly from Visual Studio by setting regular breakpoints.</span></span>

<span data-ttu-id="0d595-303">Jak už bylo zmíněno dříve, pokaždé, když přidat podporu orchestrátoru kontejnerů do projektu v rámci řešení, že projekt je nakonfigurovaný v souboru globální docker-compose.yml (na úrovni řešení), která umožňuje spustit nebo ladit celé řešení najednou.</span><span class="sxs-lookup"><span data-stu-id="0d595-303">As mentioned before, each time you add container orchestrator support to a project within a solution, that project is configured in the global (solution-level) docker-compose.yml file, which lets you run or debug the whole solution at once.</span></span> <span data-ttu-id="0d595-304">Spustí jeden kontejner pro každý projekt, který podporuje Docker řešení povolené a provedení všech kroků interní za vás Visual Studio (dotnet publikovat, sestavení dockeru atd.).</span><span class="sxs-lookup"><span data-stu-id="0d595-304">Visual Studio will start one container for each project that has Docker solution support enabled and perform all the internal steps for you (dotnet publish, docker build, etc.).</span></span>

<span data-ttu-id="0d595-305">Důležitý bod je, že, jak je znázorněno v obrázek 5 – 12, v sadě Visual Studio 2017 Další **Docker** příkazu **F5** klíče akce.</span><span class="sxs-lookup"><span data-stu-id="0d595-305">The important point here is that, as shown in Figure 5-12, in Visual Studio 2017 there's an additional **Docker** command for the **F5** key action.</span></span> <span data-ttu-id="0d595-306">Tato možnost umožňuje spustit nebo ladit vícekontejnerová aplikace spuštěním všechny kontejnery, které jsou definovány v souboru docker-compose.yml na úrovni řešení.</span><span class="sxs-lookup"><span data-stu-id="0d595-306">This option lets you run or debug a multi-container application by running all the containers that are defined in the docker-compose.yml files at the solution level.</span></span> <span data-ttu-id="0d595-307">Možnost ladit více kontejnerů řešení znamená, že můžete nastavit několik zarážky, každé zarážky v jiném projektu (kontejner) a při ladění ze sady Visual Studio se zastaví na zarážkách definovány v různých projektech a běží na různé kontejnery.</span><span class="sxs-lookup"><span data-stu-id="0d595-307">The ability to debug multiple-container solutions means that you can set several breakpoints, each breakpoint in a different project (container), and while debugging from Visual Studio you will stop at breakpoints defined in different projects and running on different containers.</span></span>

![Spouštění vícekontejnerových aplikací v sadě Visual Studio 2017](./media/image16.png)

<span data-ttu-id="0d595-309">**Obrázek 5 – 12**.</span><span class="sxs-lookup"><span data-stu-id="0d595-309">**Figure 5-12**.</span></span> <span data-ttu-id="0d595-310">Spouštění vícekontejnerových aplikací v sadě Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="0d595-310">Running multi-container apps in Visual Studio 2017</span></span>

### <a name="additional-resources"></a><span data-ttu-id="0d595-311">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="0d595-311">Additional resources</span></span>

-  <span data-ttu-id="0d595-312">**Nasazení kontejneru ASP.NET na vzdáleného hostitele Docker**</span><span class="sxs-lookup"><span data-stu-id="0d595-312">**Deploy an ASP.NET container to a remote Docker host**</span></span>

   [*https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker*](https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker)

### <a name="a-note-about-testing-and-deploying-with-orchestrators"></a><span data-ttu-id="0d595-313">Poznámka k testování a nasazení s orchestrátory</span><span class="sxs-lookup"><span data-stu-id="0d595-313">A note about testing and deploying with orchestrators</span></span>

<span data-ttu-id="0d595-314">Docker-compose up a příkazy dockeru spustit (nebo spouštění a ladění kontejnerů v sadě Visual Studio) jsou dostatečné pro testování kontejnerů ve vašem vývojovém prostředí.</span><span class="sxs-lookup"><span data-stu-id="0d595-314">The docker-compose up and docker run commands (or running and debugging the containers in Visual Studio) are adequate for testing containers in your development environment.</span></span> <span data-ttu-id="0d595-315">Ale tento přístup byste neměli používat, pokud cílíte na clustery Dockeru a orchestrátorů, jako je Docker Swarm, Mesosphere DC/OS nebo Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="0d595-315">But you should not use this approach if you are targeting Docker clusters and orchestrators like Docker Swarm, Mesosphere DC/OS, or Kubernetes.</span></span> <span data-ttu-id="0d595-316">Pokud používáte cluster jako [režim Docker Swarm](https://docs.docker.com/engine/swarm/) (k dispozici v Docker CE pro Windows a Mac od verze 1.12), musíte nasadit a testovat pomocí dalších příkazů, jako jsou [vytvoření služby docker](https://docs.docker.com/engine/reference/commandline/service_create/) pro jednotné služby.</span><span class="sxs-lookup"><span data-stu-id="0d595-316">If you are using a cluster like [Docker Swarm mode](https://docs.docker.com/engine/swarm/) (available in Docker CE for Windows and Mac since version 1.12), you need to deploy and test with additional commands like [docker service create](https://docs.docker.com/engine/reference/commandline/service_create/) for single services.</span></span> <span data-ttu-id="0d595-317">Pokud nasazujete aplikace skládá z několika kontejnerů, můžete použít [docker compose sady](https://docs.docker.com/compose/reference/bundle/) a [docker nasazení myBundleFile](https://docs.docker.com/engine/reference/commandline/deploy/) se nasazení skládá aplikace jako *zásobníku*.</span><span class="sxs-lookup"><span data-stu-id="0d595-317">If you are deploying an application composed of several containers, you use [docker compose bundle](https://docs.docker.com/compose/reference/bundle/) and [docker deploy myBundleFile](https://docs.docker.com/engine/reference/commandline/deploy/) to deploy the composed application as a *stack*.</span></span> <span data-ttu-id="0d595-318">Další informace naleznete v příspěvku blogu [Představujeme experimentální distribuované aplikace sady](https://blog.docker.com/2016/06/docker-app-bundle/) v dokumentaci k Dockeru.</span><span class="sxs-lookup"><span data-stu-id="0d595-318">For more information, see the blog post [Introducing Experimental Distributed Application Bundles](https://blog.docker.com/2016/06/docker-app-bundle/) in the Docker documentation.</span></span> <span data-ttu-id="0d595-319">na serveru Docker.</span><span class="sxs-lookup"><span data-stu-id="0d595-319">on the Docker site.</span></span>

<span data-ttu-id="0d595-320">Pro [DC/OS](https://mesosphere.com/blog/2015/09/02/dcos-cli-command-line-tool-datacenter/) a [Kubernetes](http://kubernetes.io/docs/user-guide/deployments/) použijete jiné nasazení příkazy a skripty také.</span><span class="sxs-lookup"><span data-stu-id="0d595-320">For [DC/OS](https://mesosphere.com/blog/2015/09/02/dcos-cli-command-line-tool-datacenter/) and [Kubernetes](http://kubernetes.io/docs/user-guide/deployments/) you would use different deployment commands and scripts as well.</span></span>

![Krok 6 grafiky](./media/image17.png)

## <a name="step-6-test-your-docker-application-using-your-local-docker-host"></a><span data-ttu-id="0d595-322">Krok 6.</span><span class="sxs-lookup"><span data-stu-id="0d595-322">Step 6.</span></span> <span data-ttu-id="0d595-323">Otestujte aplikaci Dockeru pomocí místního hostitele Docker</span><span class="sxs-lookup"><span data-stu-id="0d595-323">Test your Docker application using your local Docker host</span></span>

<span data-ttu-id="0d595-324">Tento krok se liší v závislosti na tom, co aplikace dělá.</span><span class="sxs-lookup"><span data-stu-id="0d595-324">This step will vary depending on what your application is doing.</span></span> <span data-ttu-id="0d595-325">V jednoduchou aplikaci webového rozhraní .NET Core, který je nasazen jako jedním kontejnerem nebo služby můžete přístup ke službě otevřením prohlížeče na hostitele Dockeru a přejdete na tomto webu, jak je znázorněno v obrázek 5-13.</span><span class="sxs-lookup"><span data-stu-id="0d595-325">In a simple .NET Core Web application that is deployed as a single container or service, you can access the service by opening a browser on the Docker host and navigating to that site, as shown in Figure 5-13.</span></span> <span data-ttu-id="0d595-326">(Pokud se konfigurace v souboru Dockerfile mapuje kontejneru na port na hostiteli není nic jiného než 80, zahrnovat port hostitele v adrese URL.)</span><span class="sxs-lookup"><span data-stu-id="0d595-326">(If the configuration in the Dockerfile maps the container to a port on the host that is anything other than 80, include the host port in the URL.)</span></span>

![Příklad testování vašich aplikací Dockeru s místním prostředí s využitím místního hostitele](./media/image18.png)

<span data-ttu-id="0d595-328">**Obrázek 5-13**.</span><span class="sxs-lookup"><span data-stu-id="0d595-328">**Figure 5-13**.</span></span> <span data-ttu-id="0d595-329">Příklad testování vašich aplikací Dockeru s místním prostředí s využitím místního hostitele</span><span class="sxs-lookup"><span data-stu-id="0d595-329">Example of testing your Docker application locally using localhost</span></span>

<span data-ttu-id="0d595-330">Pokud localhost neukazuje na Dockeru IP adresa hostitele (ve výchozím nastavení se při použití Docker CE by měl), přejděte k vaší službě, můžete IP adresu síťové karty v počítači.</span><span class="sxs-lookup"><span data-stu-id="0d595-330">If localhost is not pointing to the Docker host IP (by default, when using Docker CE, it should), to navigate to your service, use the IP address of your machine’s network card.</span></span>

<span data-ttu-id="0d595-331">Tuto adresu URL v prohlížeči používá port 80, třeba konkrétní kontejner diskutovány.</span><span class="sxs-lookup"><span data-stu-id="0d595-331">This URL in the browser uses port 80 for the particular container example being discussed.</span></span> <span data-ttu-id="0d595-332">Ale interně požadavky přesměrováni na portu 5000, protože bylo jak nasazení s prostředím docker, spusťte příkaz, jak je popsáno v předchozím kroku.</span><span class="sxs-lookup"><span data-stu-id="0d595-332">However, internally the requests are being redirected to port 5000, because that was how it was deployed with the docker run command, as explained in a previous step.</span></span>

<span data-ttu-id="0d595-333">Můžete také test aplikace pomocí curl z terminálu, jak je znázorněno v obrázek 5-14.</span><span class="sxs-lookup"><span data-stu-id="0d595-333">You can also test the application using curl from the terminal, as shown in Figure 5-14.</span></span> <span data-ttu-id="0d595-334">V instalaci Dockeru na Windows IP adresa hostitele Docker výchozí hodnota je vždy 10.0.75.1 kromě vlastní IP adresu vašeho počítače.</span><span class="sxs-lookup"><span data-stu-id="0d595-334">In a Docker installation on Windows, the default Docker Host IP is always 10.0.75.1 in addition to your machine’s actual IP address.</span></span>

![Příklad testování vašich aplikací Dockeru s místně pomocí curl](./media/image19.png)

<span data-ttu-id="0d595-336">**Obrázek 5-14**.</span><span class="sxs-lookup"><span data-stu-id="0d595-336">**Figure 5-14**.</span></span> <span data-ttu-id="0d595-337">Příklad testování vašich aplikací Dockeru s místně pomocí curl</span><span class="sxs-lookup"><span data-stu-id="0d595-337">Example of testing your Docker application locally using curl</span></span>

### <a name="testing-and-debugging-containers-with-visual-studio-2017"></a><span data-ttu-id="0d595-338">Testování a ladění kontejnerů pomocí sady Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="0d595-338">Testing and debugging containers with Visual Studio 2017</span></span>

<span data-ttu-id="0d595-339">Při spouštění a ladění kontejnerů pomocí sady Visual Studio 2017, můžete ladit aplikaci .NET v podstatě stejným způsobem jako při spuštění bez kontejnery.</span><span class="sxs-lookup"><span data-stu-id="0d595-339">When running and debugging the containers with Visual Studio 2017, you can debug the .NET application in much the same way as you would when running without containers.</span></span>

### <a name="testing-and-debugging-without-visual-studio"></a><span data-ttu-id="0d595-340">Testování a ladění bez sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="0d595-340">Testing and debugging without Visual Studio</span></span>

<span data-ttu-id="0d595-341">Pokud vyvíjíte pomocí editoru/CLI přístup, je obtížnější ladění kontejnerů a budete chtít ladit vygenerováním trasování.</span><span class="sxs-lookup"><span data-stu-id="0d595-341">If you are developing using the editor/CLI approach, debugging containers is more difficult and you will want to debug by generating traces.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="0d595-342">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="0d595-342">Additional resources</span></span>

- <span data-ttu-id="0d595-343">**Ladění aplikací v místním kontejneru Dockeru**</span><span class="sxs-lookup"><span data-stu-id="0d595-343">**Debugging apps in a local Docker container**</span></span>

   [*https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh*](https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh)

- <span data-ttu-id="0d595-344">**Steve Lasker. Sestavení, ladění, nasazení aplikace ASP.NET Core s Dockerem.**</span><span class="sxs-lookup"><span data-stu-id="0d595-344">**Steve Lasker. Build, Debug, Deploy ASP.NET Core Apps with Docker.**</span></span> <span data-ttu-id="0d595-345">Video.</span><span class="sxs-lookup"><span data-stu-id="0d595-345">Video.</span></span>

   [*https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T115*](https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T115)

## <a name="simplified-workflow-when-developing-containers-with-visual-studio"></a><span data-ttu-id="0d595-346">Zjednodušené pracovní postupy při vývoji kontejnery pomocí sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="0d595-346">Simplified workflow when developing containers with Visual Studio</span></span>

<span data-ttu-id="0d595-347">Efektivně pracovní postup při používání sady Visual Studio je mnohem jednodušší než při použití editoru/CLI přístup.</span><span class="sxs-lookup"><span data-stu-id="0d595-347">Effectively, the workflow when using Visual Studio is a lot simpler than if you use the editor/CLI approach.</span></span> <span data-ttu-id="0d595-348">Většina kroků vyžadují Docker související s soubor Dockerfile a soubory docker-compose.yml jsou skryta nebo zjednodušená sada Visual Studio, jak je znázorněno v obrázek 5 – 15.</span><span class="sxs-lookup"><span data-stu-id="0d595-348">Most of the steps required by Docker related to the Dockerfile and docker-compose.yml files are hidden or simplified by Visual Studio, as shown in Figure 5-15.</span></span>

![Zjednodušené pracovní postupy při vývoji pomocí sady Visual Studio](./media/image20.png)

<span data-ttu-id="0d595-350">**Obrázek 5 – 15**.</span><span class="sxs-lookup"><span data-stu-id="0d595-350">**Figure 5-15**.</span></span> <span data-ttu-id="0d595-351">Zjednodušené pracovní postupy při vývoji pomocí sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="0d595-351">Simplified workflow when developing with Visual Studio</span></span>

<span data-ttu-id="0d595-352">Kromě toho budete muset provést krok 2 (Přidání podpory Dockeru do vašich projektů) pouze jednou.</span><span class="sxs-lookup"><span data-stu-id="0d595-352">In addition, you need to perform step 2 (adding Docker support to your projects) just once.</span></span> <span data-ttu-id="0d595-353">Proto je podobný běžné vývojářské úlohy pracovního postupu, při použití rozhraní .NET pro další vývoj.</span><span class="sxs-lookup"><span data-stu-id="0d595-353">Therefore, the workflow is similar to your usual development tasks when using .NET for any other development.</span></span> <span data-ttu-id="0d595-354">Je potřeba vědět, co se děje na pozadí (procesu sestavení, jaké základní Image, kterou používáte, nasazení kontejnerů, atd.) a v některých případech bude také nutné upravit soubor Dockerfile nebo docker-compose.yml k přizpůsobení chování.</span><span class="sxs-lookup"><span data-stu-id="0d595-354">You need to know what is going on under the covers (the image build process, what base images you are using, deployment of containers, etc.) and sometimes you will also need to edit the Dockerfile or docker-compose.yml file to customize behaviors.</span></span> <span data-ttu-id="0d595-355">Ale většinu práce výrazně zjednodušuje použití sady Visual Studio, což je mnohem vyšší produktivitu.</span><span class="sxs-lookup"><span data-stu-id="0d595-355">But most of the work is greatly simplified by using Visual Studio, making you a lot more productive.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="0d595-356">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="0d595-356">Additional resources</span></span>

- <span data-ttu-id="0d595-357">**Steve Lasker. Vývoj na platformě .NET dockeru pomocí sady Visual Studio 2017**</span><span class="sxs-lookup"><span data-stu-id="0d595-357">**Steve Lasker. .NET Docker Development with Visual Studio 2017**</span></span>

   [*https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T111*](https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T111)

- <span data-ttu-id="0d595-358">**Jeffrey T. Fritz. Vložte aplikace .NET Core v kontejneru pomocí nového nástroje Dockeru pro Visual Studio**</span><span class="sxs-lookup"><span data-stu-id="0d595-358">**Jeffrey T. Fritz. Put a .NET Core App in a Container with the new Docker Tools for Visual Studio**</span></span>

   [*https://blogs.msdn.microsoft.com/webdev/2016/11/16/new-docker-tools-for-visual-studio/*](https://blogs.msdn.microsoft.com/webdev/2016/11/16/new-docker-tools-for-visual-studio/)

## <a name="using-powershell-commands-in-a-dockerfile-to-set-up-windows-containers"></a><span data-ttu-id="0d595-359">Pomocí příkazů prostředí PowerShell v souboru Dockerfile k nastavení kontejnery Windows</span><span class="sxs-lookup"><span data-stu-id="0d595-359">Using PowerShell commands in a Dockerfile to set up Windows Containers</span></span>

<span data-ttu-id="0d595-360">[Kontejnery Windows](/virtualization/windowscontainers/about/index) umožňují převést svoje stávající aplikace pro Windows do Image Dockeru a nasadit je pomocí stejných nástrojů jako ostatní ekosystému Dockeru.</span><span class="sxs-lookup"><span data-stu-id="0d595-360">[Windows Containers](/virtualization/windowscontainers/about/index) allow you to convert your existing Windows applications into Docker images and deploy them with the same tools as the rest of the Docker ecosystem.</span></span> <span data-ttu-id="0d595-361">Pokud chcete používat kontejnery Windows, spusťte příkazy Powershellu v souboru Dockerfile, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="0d595-361">To use Windows Containers, you run PowerShell commands in the Dockerfile, as shown in the following example:</span></span>

```Dockerfile
FROM microsoft/windowsservercore

LABEL Description="IIS" Vendor="Microsoft" Version="10"

RUN powershell -Command Add-WindowsFeature Web-Server

CMD [ "ping", "localhost", "-t" ]
```

<span data-ttu-id="0d595-362">V tomto případě jsme se pomocí základní image jádra serveru systému Windows (od nastavení) a instalace služby IIS pomocí příkazu prostředí PowerShell (nastavení spuštění).</span><span class="sxs-lookup"><span data-stu-id="0d595-362">In this case, we are using a Windows Server Core base image (the FROM setting) and installing IIS with a PowerShell command (the RUN setting).</span></span> <span data-ttu-id="0d595-363">Podobným způsobem můžete také použít příkazy prostředí PowerShell nastavit další komponenty, jako je ASP.NET 4.x, .NET 4.6 nebo jiný software pro Windows.</span><span class="sxs-lookup"><span data-stu-id="0d595-363">In a similar way, you could also use PowerShell commands to set up additional components like ASP.NET 4.x, .NET 4.6, or any other Windows software.</span></span> <span data-ttu-id="0d595-364">Například následující příkaz v souboru Dockerfile Nastaví technologii ASP.NET 4.5:</span><span class="sxs-lookup"><span data-stu-id="0d595-364">For example, the following command in a Dockerfile sets up ASP.NET 4.5:</span></span>

```Dockerfile
RUN powershell add-windowsfeature web-asp-net45
```

### <a name="additional-resources"></a><span data-ttu-id="0d595-365">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="0d595-365">Additional resources</span></span>

- <span data-ttu-id="0d595-366">**aspnet-docker/Dockerfile.**</span><span class="sxs-lookup"><span data-stu-id="0d595-366">**aspnet-docker/Dockerfile.**</span></span> <span data-ttu-id="0d595-367">Příklady příkazů Powershellu spouštět z soubory dockerfile začlenit funkce Windows.</span><span class="sxs-lookup"><span data-stu-id="0d595-367">Example Powershell commands to run from dockerfiles to include Windows features.</span></span>

   [*https://github.com/Microsoft/aspnet-docker/blob/master/4.6.2/Dockerfile*](https://github.com/Microsoft/aspnet-docker/blob/master/4.6.2/Dockerfile)

>[!div class="step-by-step"]
<span data-ttu-id="0d595-368">[Předchozí](index.md)
[další](../net-core-single-containers-linux-windows-server-hosts/index.md)</span><span class="sxs-lookup"><span data-stu-id="0d595-368">[Previous](index.md)
[Next](../net-core-single-containers-linux-windows-server-hosts/index.md)</span></span>