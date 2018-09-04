---
title: Pracovní postup vývoje aplikací Dockeru
description: Architektura Mikroslužeb .NET pro Kontejnerizované aplikace .NET | Pracovní postup vývoje aplikací Dockeru
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/18/2017
ms.openlocfilehash: b7115530c44321dc2a10be3996c14429591b611f
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43553391"
---
# <a name="development-workflow-for-docker-apps"></a><span data-ttu-id="a1899-103">Pracovní postup vývoje aplikací Dockeru</span><span class="sxs-lookup"><span data-stu-id="a1899-103">Development workflow for Docker apps</span></span>

<span data-ttu-id="a1899-104">Životní cyklus vývoje aplikací začíná každý vývojář počítače, ve kterém vývojář kódy aplikace pomocí jejich upřednostňovaný jazyk a testy místně.</span><span class="sxs-lookup"><span data-stu-id="a1899-104">The application development lifecycle starts at each developer’s machine, where the developer codes the application using their preferred language and tests it locally.</span></span> <span data-ttu-id="a1899-105">Bez ohledu na to, které jazyk, rozhraní a platformě vývojář rozhodne pro tento pracovní postup vývojář je vždy vývoj a testování kontejnery Dockeru, ale uděláte místně.</span><span class="sxs-lookup"><span data-stu-id="a1899-105">No matter which language, framework, and platform the developer chooses, with this workflow, the developer is always developing and testing Docker containers, but doing so locally.</span></span>

<span data-ttu-id="a1899-106">Každý kontejner (instance image Dockeru) zahrnuje následující součásti:</span><span class="sxs-lookup"><span data-stu-id="a1899-106">Each container (an instance of a Docker image) includes the following components:</span></span>

-   <span data-ttu-id="a1899-107">Výběr operačního systému, (například Linuxová distribuce vytvořená, Windows Nano serveru nebo Windows Server Core).</span><span class="sxs-lookup"><span data-stu-id="a1899-107">An operating system selection (for example, a Linux distribution, Windows Nano Server, or Windows Server Core).</span></span>

-   <span data-ttu-id="a1899-108">Soubory přidané vývojář (binární soubory aplikace atd.).</span><span class="sxs-lookup"><span data-stu-id="a1899-108">Files added by the developer (application binaries, etc.).</span></span>

-   <span data-ttu-id="a1899-109">Informace o konfiguraci (nastavení prostředí a závislosti).</span><span class="sxs-lookup"><span data-stu-id="a1899-109">Configuration information (environment settings and dependencies).</span></span>

## <a name="workflow-for-developing-docker-container-based-applications"></a><span data-ttu-id="a1899-110">Pracovní postup pro vývoj aplikací založených na kontejnerech Dockeru</span><span class="sxs-lookup"><span data-stu-id="a1899-110">Workflow for developing Docker container-based applications</span></span>

<span data-ttu-id="a1899-111">Tato část popisuje *vnitřní smyčky* pracovní postup vývoje aplikací založených na kontejnerech Dockeru.</span><span class="sxs-lookup"><span data-stu-id="a1899-111">This section describes the *inner-loop* development workflow for Docker container-based applications.</span></span> <span data-ttu-id="a1899-112">Vnitřní smyčky pracovního postupu znamená, že se zohledněním širší pracovních postupů DevOps a právě se zaměřuje na vývojové práce vykonané na počítači pro vývojáře.</span><span class="sxs-lookup"><span data-stu-id="a1899-112">The inner-loop workflow means it is not taking into account the broader DevOps workflow and just focuses on the development work done on the developer’s computer.</span></span> <span data-ttu-id="a1899-113">Počáteční kroky k nastavení prostředí nejsou zahrnuty, protože ty se provede jen jednou.</span><span class="sxs-lookup"><span data-stu-id="a1899-113">The initial steps to set up the environment are not included, since those are done only once.</span></span>

<span data-ttu-id="a1899-114">Aplikace se skládá z vlastní služby a další knihovny (závislosti).</span><span class="sxs-lookup"><span data-stu-id="a1899-114">An application is composed of your own services plus additional libraries (dependencies).</span></span> <span data-ttu-id="a1899-115">Níže jsou uvedeny základní kroky, které obvykle provést při sestavování aplikace Dockeru, jak je znázorněno na obrázku 5-1.</span><span class="sxs-lookup"><span data-stu-id="a1899-115">The following are the basic steps you usually take when building a Docker application, as illustrated in Figure 5-1.</span></span>

![](./media/image1.png)

<span data-ttu-id="a1899-116">**Obrázek 5-1.**</span><span class="sxs-lookup"><span data-stu-id="a1899-116">**Figure 5-1.**</span></span> <span data-ttu-id="a1899-117">Krok za krokem pracovního postupu pro vývoj Docker kontejnerizovaných aplikací</span><span class="sxs-lookup"><span data-stu-id="a1899-117">Step-by-step workflow for developing Docker containerized apps</span></span>

<span data-ttu-id="a1899-118">V této příručce je podrobně popsán tento celý proces a všemi hlavními kroky jsou vysvětleny se zaměříte na prostředí Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="a1899-118">In this guide, this whole process is detailed and every major step is explained by focusing on a Visual Studio environment.</span></span>

<span data-ttu-id="a1899-119">Při použití metodiky vývoj editoru a rozhraní příkazového řádku (například Visual Studio Code a rozhraní příkazového řádku Dockeru v systému macOS nebo Windows), musíte znát každý krok, obecně podrobnější než při použití sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="a1899-119">When you are using an editor/CLI development approach (for example, Visual Studio Code plus Docker CLI on macOS or Windows), you need to know every step, generally in more detail than if you are using Visual Studio.</span></span> <span data-ttu-id="a1899-120">Podrobné informace o práci v prostředí rozhraní příkazového řádku najdete v elektronické příručce [životního cyklu Kontejnerizovaných aplikací Dockeru pomocí nástrojů a Microsoft Platforms](https://aka.ms/dockerlifecycleebook/).</span><span class="sxs-lookup"><span data-stu-id="a1899-120">For more details about working in a CLI environment, refer to the e-book [Containerized Docker Application lifecycle with Microsoft Platforms and Tools](https://aka.ms/dockerlifecycleebook/).</span></span>

<span data-ttu-id="a1899-121">Pokud používáte Visual Studio 2015 nebo Visual Studio 2017, mnoho z těchto kroků se postará služba za vás, což výrazně zvyšuje vaši produktivitu.</span><span class="sxs-lookup"><span data-stu-id="a1899-121">When you are using Visual Studio 2015 or Visual Studio 2017, many of those steps are handled for you, which dramatically improves your productivity.</span></span> <span data-ttu-id="a1899-122">To platí zejména při používání sady Visual Studio 2017 a cílení vícekontejnerových aplikací.</span><span class="sxs-lookup"><span data-stu-id="a1899-122">This is especially true when you are using Visual Studio 2017 and targeting multi-container applications.</span></span> <span data-ttu-id="a1899-123">Například s jediným klepnutím myši, Visual Studio přidá soubor Dockerfile a docker-compose.yml do vašich projektů s konfigurací pro vaši aplikaci.</span><span class="sxs-lookup"><span data-stu-id="a1899-123">For instance, with just one mouse click, Visual Studio adds the Dockerfile and docker-compose.yml file to your projects with the configuration for your application.</span></span> <span data-ttu-id="a1899-124">Při spuštění aplikace v sadě Visual Studio sestaví image Dockeru a spustí vícekontejnerová aplikace přímo v Dockeru; dokonce i umožňuje ladit několik kontejnerů najednou.</span><span class="sxs-lookup"><span data-stu-id="a1899-124">When you run the application in Visual Studio, it builds the Docker image and runs the multi-container application directly in Docker; it even allows you to debug several containers at once.</span></span> <span data-ttu-id="a1899-125">Tyto funkce budou zvýšit rychlost vývoje.</span><span class="sxs-lookup"><span data-stu-id="a1899-125">These features will boost your development speed.</span></span>

<span data-ttu-id="a1899-126">Ale to, že sada Visual Studio provádí tyto kroky automatického neznamená, že nepotřebujete vědět, co se děje v pod tím s Dockerem.</span><span class="sxs-lookup"><span data-stu-id="a1899-126">However, just because Visual Studio makes those steps automatic does not mean that you do not need to know what is going on underneath with Docker.</span></span> <span data-ttu-id="a1899-127">Proto v dokumentu, který následuje, můžeme podrobně každý krok.</span><span class="sxs-lookup"><span data-stu-id="a1899-127">Therefore, in the guidance that follows, we detail every step.</span></span>

![](./media/image2.png)

## <a name="step-1-start-coding-and-create-your-initial-application-or-service-baseline"></a><span data-ttu-id="a1899-128">Krok 1.</span><span class="sxs-lookup"><span data-stu-id="a1899-128">Step 1.</span></span> <span data-ttu-id="a1899-129">Psaní kódu a vytvořte počáteční aplikace nebo služba směrného plánu</span><span class="sxs-lookup"><span data-stu-id="a1899-129">Start coding and create your initial application or service baseline</span></span>

<span data-ttu-id="a1899-130">Vývoj aplikací Dockeru je podobným způsobem, jakým vyvíjíte aplikaci bez Dockeru.</span><span class="sxs-lookup"><span data-stu-id="a1899-130">Developing a Docker application is similar to the way you develop an application without Docker.</span></span> <span data-ttu-id="a1899-131">Rozdíl je, že při vývoji pro Docker, máte nasazení a testování vaší aplikace nebo služby v rámci kontejnerů Docker v místním prostředí.</span><span class="sxs-lookup"><span data-stu-id="a1899-131">The difference is that while developing for Docker, you are deploying and testing your application or services running within Docker containers in your local environment.</span></span> <span data-ttu-id="a1899-132">Kontejner může být kontejneru Linuxu nebo kontejner Windows.</span><span class="sxs-lookup"><span data-stu-id="a1899-132">The container can be either a Linux container or a Windows container.</span></span>

### <a name="set-up-your-local-environment-with-visual-studio"></a><span data-ttu-id="a1899-133">Nastavit místní prostředí pomocí sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="a1899-133">Set up your local environment with Visual Studio</span></span>

<span data-ttu-id="a1899-134">Pokud chcete začít, ujistěte se, že máte [Docker Community Edition (CE)](https://www.docker.com/community-edition) pro Windows nainstalované, jak je popsáno v následujících pokynech:</span><span class="sxs-lookup"><span data-stu-id="a1899-134">To begin, make sure you have [Docker Community Edition (CE)](https://www.docker.com/community-edition) for Windows installed, as explained in the following instructions:</span></span>

[<span data-ttu-id="a1899-135">Začínáme s Docker CE pro Windows</span><span class="sxs-lookup"><span data-stu-id="a1899-135">Get started with Docker CE for Windows</span></span>](https://docs.docker.com/docker-for-windows/)

<span data-ttu-id="a1899-136">Kromě toho budete potřebovat nainstalovanou sadu Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="a1899-136">In addition, you will need Visual Studio 2017 installed.</span></span> <span data-ttu-id="a1899-137">To je upřednostňována před Visual Studio 2015 se sadou Visual Studio Tools for Docker – doplněk, protože Visual Studio 2017 obsahuje další pokročilé podpora pro Docker, jako je podpora pro ladění kontejnerů.</span><span class="sxs-lookup"><span data-stu-id="a1899-137">This is preferred over Visual Studio 2015 with the Visual Studio Tools for Docker add-in, because Visual Studio 2017 has more advanced support for Docker, like support for debugging containers.</span></span> <span data-ttu-id="a1899-138">Visual Studio 2017 obsahuje nástroje pro Docker, pokud jste vybrali **.NET Core a Docker** úloh během instalace, jak je znázorněno v obrázku 5-2.</span><span class="sxs-lookup"><span data-stu-id="a1899-138">Visual Studio 2017 includes the tooling for Docker if you selected the **.NET Core and Docker** workload during installation, as shown in Figure 5-2.</span></span>

![](./media/image3.png)

<span data-ttu-id="a1899-139">**Obrázek 5-2**.</span><span class="sxs-lookup"><span data-stu-id="a1899-139">**Figure 5-2**.</span></span> <span data-ttu-id="a1899-140">Výběr **.NET Core a Docker** úloh během instalace sady Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="a1899-140">Selecting the **.NET Core and Docker** workload during Visual Studio 2017 setup</span></span>

<span data-ttu-id="a1899-141">Můžete začít kódování aplikace v .NET prostý (obvykle v .NET Core, pokud máte v úmyslu používat kontejnery) ještě před povolením Docker ve vaší aplikaci a o nasazení a testování v Dockeru.</span><span class="sxs-lookup"><span data-stu-id="a1899-141">You can start coding your application in plain .NET (usually in .NET Core if you are planning to use containers) even before enabling Docker in your application and deploying and testing in Docker.</span></span> <span data-ttu-id="a1899-142">Doporučujeme však začít pracovat na Docker co nejdříve, protože, které se stanou skutečnou prostředí a můžete co nejdříve zjistit všechny problémy.</span><span class="sxs-lookup"><span data-stu-id="a1899-142">However, it is recommended that you start working on Docker as soon as possible, because that will be the real environment and any issues can be discovered as soon as possible.</span></span> <span data-ttu-id="a1899-143">To je podporováno, protože Visual Studio usnadňuje tak práci s Dockerem, téměř je transparentní, představte si třeba při ladění vícekontejnerových aplikací ze sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="a1899-143">This is encouraged because Visual Studio makes it so easy to work with Docker that it almost feels transparent—the best example when debugging multi-container applications from Visual Studio.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="a1899-144">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="a1899-144">Additional resources</span></span>

-   <span data-ttu-id="a1899-145">**Začínáme s Docker CE pro Windows**
    [*https://docs.docker.com/docker-for-windows/*](https://docs.docker.com/docker-for-windows/)</span><span class="sxs-lookup"><span data-stu-id="a1899-145">**Get started with Docker CE for Windows**
[*https://docs.docker.com/docker-for-windows/*](https://docs.docker.com/docker-for-windows/)</span></span>

-   <span data-ttu-id="a1899-146">**Visual Studio 2017**
    [*https://visualstudio.microsoft.com/downloads/*](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)</span><span class="sxs-lookup"><span data-stu-id="a1899-146">**Visual Studio 2017**
[*https://visualstudio.microsoft.com/downloads/*](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)</span></span>

![](./media/image4.png)

## <a name="step-2-create-a-dockerfile-related-to-an-existing-net-base-image"></a><span data-ttu-id="a1899-147">Krok 2.</span><span class="sxs-lookup"><span data-stu-id="a1899-147">Step 2.</span></span> <span data-ttu-id="a1899-148">Vytvoření souboru Dockerfile související s existující základní image .NET</span><span class="sxs-lookup"><span data-stu-id="a1899-148">Create a Dockerfile related to an existing .NET base image</span></span>

<span data-ttu-id="a1899-149">Budete potřebovat soubor Dockerfile pro každý vlastní image, kterou chcete sestavit. soubor Dockerfile pro každý kontejner má být nasazen, musíte také, jestli nasadit automaticky ze sady Visual Studio nebo ručně pomocí rozhraní příkazového řádku Dockeru (spuštění docker a docker-compose příkazů).</span><span class="sxs-lookup"><span data-stu-id="a1899-149">You need a Dockerfile for each custom image you want to build; you also need a Dockerfile for each container to be deployed, whether you deploy automatically from Visual Studio or manually using the Docker CLI (docker run and docker-compose commands).</span></span> <span data-ttu-id="a1899-150">Pokud vaše aplikace obsahuje jeden vlastní službu, potřebujete jeden soubor Dockerfile.</span><span class="sxs-lookup"><span data-stu-id="a1899-150">If your application contains a single custom service, you need a single Dockerfile.</span></span> <span data-ttu-id="a1899-151">Pokud vaše aplikace obsahuje více služeb (stejně jako v architektuře mikroslužeb), budete potřebovat jeden soubor Dockerfile pro každou službu.</span><span class="sxs-lookup"><span data-stu-id="a1899-151">If your application contains multiple services (as in a microservices architecture), you need one Dockerfile for each service.</span></span>

<span data-ttu-id="a1899-152">Soubor Dockerfile je umístěn v kořenové složce aplikace nebo služby.</span><span class="sxs-lookup"><span data-stu-id="a1899-152">The Dockerfile is placed in the root folder of your application or service.</span></span> <span data-ttu-id="a1899-153">Obsahuje příkazy, které informace tom, jak nastavit a spustit vaše aplikace nebo služby v kontejneru Dockeru.</span><span class="sxs-lookup"><span data-stu-id="a1899-153">It contains the commands that tell Docker how to set up and run your application or service in a container.</span></span> <span data-ttu-id="a1899-154">Můžete ručně vytvořit soubor Dockerfile v kódu a přidejte do projektu spolu s .NET závislosti.</span><span class="sxs-lookup"><span data-stu-id="a1899-154">You can manually create a Dockerfile in code and add it to your project along with your .NET dependencies.</span></span>

<span data-ttu-id="a1899-155">Pomocí sady Visual Studio a jeho nástrojů Dockeru tato úloha vyžaduje jenom několik kliknutí myší.</span><span class="sxs-lookup"><span data-stu-id="a1899-155">With Visual Studio and its tools for Docker, this task requires only a few mouse clicks.</span></span> <span data-ttu-id="a1899-156">Při vytváření nového projektu v sadě Visual Studio 2017 je k dispozici možnost s názvem **podpora povolit kontejnerů (Dockeru)**, jak je znázorněno v obrázek 5-3.</span><span class="sxs-lookup"><span data-stu-id="a1899-156">When you create a new project in Visual Studio 2017, there is an option named **Enable Container (Docker) Support**, as shown in Figure 5-3.</span></span>

![](./media/image5.png)

<span data-ttu-id="a1899-157">**Obrázek 5 – 3**.</span><span class="sxs-lookup"><span data-stu-id="a1899-157">**Figure 5-3**.</span></span> <span data-ttu-id="a1899-158">Povolení podpory Dockeru, při vytváření nového projektu v sadě Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="a1899-158">Enabling Docker Support when creating a new project in Visual Studio 2017</span></span>

<span data-ttu-id="a1899-159">Můžete také povolit podporu Dockeru na nového nebo existujícího projektu tak, že pravým tlačítkem myši na soubor projektu v sadě Visual Studio a výběrem možnosti **Docker přidat projekt podporovat**, jak je znázorněno v obrázek 5 – 4.</span><span class="sxs-lookup"><span data-stu-id="a1899-159">You can also enable Docker support on a new or existing project by right-clicking your project file in Visual Studio and selecting the option **Add-Docker Project Support**, as shown in Figure 5-4.</span></span>

![](./media/image6.png)

<span data-ttu-id="a1899-160">**Obrázek 5 – 4**.</span><span class="sxs-lookup"><span data-stu-id="a1899-160">**Figure 5-4**.</span></span> <span data-ttu-id="a1899-161">Povolení podpory Dockeru v existujícím projektu Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="a1899-161">Enabling Docker support in an existing Visual Studio 2017 project</span></span>

<span data-ttu-id="a1899-162">Tato akce na projektu (například webové aplikace ASP.NET nebo webové rozhraní API služby) přidá do projektu s požadovanou konfigurací souboru Dockerfile.</span><span class="sxs-lookup"><span data-stu-id="a1899-162">This action on a project (like an ASP.NET Web application or Web API service) adds a Dockerfile to the project with the required configuration.</span></span> <span data-ttu-id="a1899-163">Také přidá soubor docker-compose.yml pro celé řešení.</span><span class="sxs-lookup"><span data-stu-id="a1899-163">It also adds a docker-compose.yml file for the whole solution.</span></span> <span data-ttu-id="a1899-164">V následujících částech popisujeme informace, které přejde do každé z těchto souborů.</span><span class="sxs-lookup"><span data-stu-id="a1899-164">In the following sections, we describe the information that goes into each of those files.</span></span> <span data-ttu-id="a1899-165">Visual Studio může provést tuto práci za vás, ale je užitečné k pochopení, co je potřeba k souboru Dockerfile.</span><span class="sxs-lookup"><span data-stu-id="a1899-165">Visual Studio can do this work for you, but it is useful to understand what goes into a Dockerfile.</span></span>

### <a name="option-a-creating-a-project-using-an-existing-official-net-docker-image"></a><span data-ttu-id="a1899-166">Odpověď: možnost Vytvoření projektu pomocí existující oficiální image .NET Dockeru</span><span class="sxs-lookup"><span data-stu-id="a1899-166">Option A: Creating a project using an existing official .NET Docker image</span></span>

<span data-ttu-id="a1899-167">Obvykle vytvoříte vlastní image kontejneru nad základní image, můžete získat z oficiální úložiště na [Docker Hubu](https://hub.docker.com/) registru.</span><span class="sxs-lookup"><span data-stu-id="a1899-167">You usually build a custom image for your container on top of a base image you can get from an official repository at the [Docker Hub](https://hub.docker.com/) registry.</span></span> <span data-ttu-id="a1899-168">To je přesně co se stane na pozadí, když povolíte podporu Dockeru v sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="a1899-168">That is precisely what happens under the covers when you enable Docker support in Visual Studio.</span></span> <span data-ttu-id="a1899-169">Váš soubor Dockerfile použije existující image aspnetcore.</span><span class="sxs-lookup"><span data-stu-id="a1899-169">Your Dockerfile will use an existing aspnetcore image.</span></span>

<span data-ttu-id="a1899-170">Dříve jsme vysvětlit, které Image Dockeru a úložiště můžete použít, v závislosti na rozhraní framework a rozhodli jste se operační systém.</span><span class="sxs-lookup"><span data-stu-id="a1899-170">Earlier we explained which Docker images and repos you can use, depending on the framework and OS you have chosen.</span></span> <span data-ttu-id="a1899-171">Například pokud chcete používat ASP.NET Core (s Linuxem nebo Windows), obrázku je microsoft / aspnetcore:2.0.</span><span class="sxs-lookup"><span data-stu-id="a1899-171">For instance, if you want to use ASP.NET Core (Linux or Windows), the image to use is microsoft/aspnetcore:2.0.</span></span> <span data-ttu-id="a1899-172">Proto stačí zadat jaké základní image Dockeru, který budete používat pro váš kontejner.</span><span class="sxs-lookup"><span data-stu-id="a1899-172">Therefore, you just need to specify what base Docker image you will use for your container.</span></span> <span data-ttu-id="a1899-173">Můžete to udělat tak, že přidáte od Microsoftu nebo aspnetcore:2.0 na vašem souboru Dockerfile.</span><span class="sxs-lookup"><span data-stu-id="a1899-173">You do that by adding FROM microsoft/aspnetcore:2.0 to your Dockerfile.</span></span> <span data-ttu-id="a1899-174">To se automaticky provede pomocí sady Visual Studio, ale pokud byste chtěli aktualizovat verzi, aktualizujte tuto hodnotu.</span><span class="sxs-lookup"><span data-stu-id="a1899-174">This will be automatically performed by Visual Studio, but if you were to update the version, you update this value.</span></span>

<span data-ttu-id="a1899-175">Použití oficiální úložiště .NET image z Docker Hubu s číslem verze zajistí, že stejné funkce jazyka jsou k dispozici na všech počítačích (včetně vývoje, testování a produkce).</span><span class="sxs-lookup"><span data-stu-id="a1899-175">Using an official .NET image repository from Docker Hub with a version number ensures that the same language features are available on all machines (including development, testing, and production).</span></span>

<span data-ttu-id="a1899-176">Následující příklad ukazuje ukázkový soubor Dockerfile pro kontejner služby ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="a1899-176">The following example shows a sample Dockerfile for an ASP.NET Core container.</span></span>

```Dockerfile
FROM microsoft/aspnetcore:2.0
  
ARG source
  
WORKDIR /app
  
EXPOSE 80
  
COPY ${source:-obj/Docker/publish} .
  
ENTRYPOINT ["dotnet", " MySingleContainerWebApp.dll "]
```

<span data-ttu-id="a1899-177">V tomto případě kontejner je založená na verzi 2.0 oficiální Image Dockeru ASP.NET Core (více arch pro systémy Linux a Windows).</span><span class="sxs-lookup"><span data-stu-id="a1899-177">In this case, the container is based on version 2.0 of the official ASP.NET Core Docker image (multi-arch for Linux and Windows).</span></span> <span data-ttu-id="a1899-178">Toto je nastavení `FROM microsoft/aspnetcore:2.0`.</span><span class="sxs-lookup"><span data-stu-id="a1899-178">This is the setting `FROM microsoft/aspnetcore:2.0`.</span></span> <span data-ttu-id="a1899-179">(Další podrobnosti o této základní image, najdete v článku [Image Dockeru ASP.NET Core](https://hub.docker.com/r/microsoft/aspnetcore/) stránky a [Image Dockeru .NET Core](https://hub.docker.com/r/microsoft/dotnet/) stránky.) V souboru Dockerfile potřebujete také dáte pokyn, aby Docker pro naslouchání na portu TCP, které se použijí v době běhu (v tomto případě portem 80, nakonfigurované s nastavením VYSTAVENÍ).</span><span class="sxs-lookup"><span data-stu-id="a1899-179">(For further details about this base image, see the [ASP.NET Core Docker Image](https://hub.docker.com/r/microsoft/aspnetcore/) page and the [.NET Core Docker Image](https://hub.docker.com/r/microsoft/dotnet/) page.) In the Dockerfile, you also need to instruct Docker to listen on the TCP port you will use at runtime (in this case, port 80, as configured with the EXPOSE setting).</span></span>

<span data-ttu-id="a1899-180">Můžete zadat další nastavení konfigurace v souboru Dockerfile, v závislosti na jazyk a rozhraní, které používáte.</span><span class="sxs-lookup"><span data-stu-id="a1899-180">You can specify additional configuration settings in the Dockerfile, depending on the language and framework you are using.</span></span> <span data-ttu-id="a1899-181">Například řádek ENTRYPOINT s \["dotnet", "MySingleContainerWebApp.dll"\] říká Dockeru spustit aplikaci .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a1899-181">For instance, the ENTRYPOINT line with \["dotnet", "MySingleContainerWebApp.dll"\] tells Docker to run a .NET Core application.</span></span> <span data-ttu-id="a1899-182">Pokud používáte sadu SDK a rozhraní .NET Core CLI (rozhraní příkazového řádku dotnet) k sestavení a spuštění aplikace .NET, toto nastavení bude jiný.</span><span class="sxs-lookup"><span data-stu-id="a1899-182">If you are using the SDK and the .NET Core CLI (dotnet CLI) to build and run the .NET application, this setting would be different.</span></span> <span data-ttu-id="a1899-183">Dolní řádek je, že řádku vstupního bodu a další nastavení budou lišit v závislosti na jazyku a platformě, kterou zvolíte pro vaši aplikaci.</span><span class="sxs-lookup"><span data-stu-id="a1899-183">The bottom line is that the ENTRYPOINT line and other settings will be different depending on the language and platform you choose for your application.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="a1899-184">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="a1899-184">Additional resources</span></span>

-   <span data-ttu-id="a1899-185">**Vytváření Imagí Dockeru pro aplikace .NET Core**
    [*https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images*](../../../core/docker/building-net-docker-images.md)</span><span class="sxs-lookup"><span data-stu-id="a1899-185">**Building Docker Images for .NET Core Applications**
[*https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images*](../../../core/docker/building-net-docker-images.md)</span></span>

-   <span data-ttu-id="a1899-186">**Vytvoření vlastní image**.</span><span class="sxs-lookup"><span data-stu-id="a1899-186">**Build your own image**.</span></span> <span data-ttu-id="a1899-187">V oficiální dokumentaci k Dockeru.</span><span class="sxs-lookup"><span data-stu-id="a1899-187">In the official Docker documentation.</span></span>
    [*https://docs.docker.com/engine/tutorials/dockerimages/*](https://docs.docker.com/engine/tutorials/dockerimages/)

### <a name="using-multi-arch-image-repositories"></a><span data-ttu-id="a1899-188">Pomocí více architektury image úložišť</span><span class="sxs-lookup"><span data-stu-id="a1899-188">Using multi-arch image repositories</span></span>

<span data-ttu-id="a1899-189">Jediné úložiště může obsahovat variant, platformy, jako jsou image Linuxu a Windows image.</span><span class="sxs-lookup"><span data-stu-id="a1899-189">A single repo can contain platform variants, such as a Linux image and a Windows image.</span></span> <span data-ttu-id="a1899-190">Tato funkce umožňuje dodavatelé, jako je Microsoft (creators základní image) k vytvoření jednoho úložiště pro víc platforem (to znamená operačních systémů Linux a Windows).</span><span class="sxs-lookup"><span data-stu-id="a1899-190">This feature allows vendors like Microsoft (base image creators) to create a single repo to cover multiple platforms (that is Linux and Windows).</span></span> <span data-ttu-id="a1899-191">Například [microsoft/dotnet](https://hub.docker.com/r/microsoft/aspnetcore/) úložiště k dispozici v registru Docker Hub poskytuje podporu pro systémy Linux a Windows Nano Server pomocí stejného názvu úložiště.</span><span class="sxs-lookup"><span data-stu-id="a1899-191">For example, the [microsoft/dotnet](https://hub.docker.com/r/microsoft/aspnetcore/) repository available in the Docker Hub registry provides support for Linux and Windows Nano Server by using the same repo name.</span></span>

<span data-ttu-id="a1899-192">Je-li zadat značky, cílení na platformu, která je explicitní jako v následujících případech:</span><span class="sxs-lookup"><span data-stu-id="a1899-192">If you specify a tag, targeting a platform that is explicit like in the following cases:</span></span>

-   <span data-ttu-id="a1899-193">**microsoft/aspnetcore:2.0.0-jessie**</span><span class="sxs-lookup"><span data-stu-id="a1899-193">**microsoft/aspnetcore:2.0.0-jessie**</span></span>

        .NET Core 2.0 runtime-only on Linux 

-   <span data-ttu-id="a1899-194">**microsoft/aspnetcore:2.0.0-nanoserver**</span><span class="sxs-lookup"><span data-stu-id="a1899-194">**microsoft/aspnetcore:2.0.0-nanoserver**</span></span>

        .NET Core 2.0 runtime-only on Windows Nano Server

<span data-ttu-id="a1899-195">Ale a toto je nový od poloviny 2017, pokud zadáte stejný název image, i se stejnou značkou, nových imagí více architektury (např. image aspnetcore, která podporuje více arch) budou používat verzi systému Linux nebo Windows v závislosti na nasazujete hostitele Docker operačního systému , jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="a1899-195">But, and this is new since mid-2017, if you specify the same image name, even with the same tag, the new multi-arch images (like the aspnetcore image which supports multi-arch) will use the Linux or Windows version depending on the Docker host OS you are deploying, as shown in the following example:</span></span>

-   <span data-ttu-id="a1899-196">**microsoft/aspnetcore:2.0**</span><span class="sxs-lookup"><span data-stu-id="a1899-196">**microsoft/aspnetcore:2.0**</span></span>

        Multi-arch: .NET Core 2.0 runtime-only on Linux or Windows Nano Server depending on the Docker host OS

<span data-ttu-id="a1899-197">Tímto způsobem, když si stáhnete obrázek z hostitele Windows, je přetáhne Windows variant a přebírání z hostitele platformy Linux stejný název image přetáhne varianty Linuxu.</span><span class="sxs-lookup"><span data-stu-id="a1899-197">This way, when you pull an image from a Windows host, it will pull the Windows variant, and pulling the same image name from a Linux host will pull the Linux variant.</span></span>

### <a name="option-b-creating-your-base-image-from-scratch"></a><span data-ttu-id="a1899-198">Možnost B: vytvoříte základní image od začátku</span><span class="sxs-lookup"><span data-stu-id="a1899-198">Option B: Creating your base image from scratch</span></span>

<span data-ttu-id="a1899-199">Vlastní základní image Dockeru můžete vytvořit úplně od začátku.</span><span class="sxs-lookup"><span data-stu-id="a1899-199">You can create your own Docker base image from scratch.</span></span> <span data-ttu-id="a1899-200">Tento scénář se nedoporučuje pro uživatele, který se spouští s Dockerem, ale pokud chcete nastavit konkrétní bity základní image, můžete tak učinit.</span><span class="sxs-lookup"><span data-stu-id="a1899-200">This scenario is not recommended for someone who is starting with Docker, but if you want to set the specific bits of your own base image, you can do so.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="a1899-201">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="a1899-201">Additional resources</span></span>

-   <span data-ttu-id="a1899-202">**Více architektury .NET Core imagí**.</span><span class="sxs-lookup"><span data-stu-id="a1899-202">**Multi-arch .NET Core images**.</span></span>
<span data-ttu-id="a1899-203">https://github.com/dotnet/announcements/issues/14</span><span class="sxs-lookup"><span data-stu-id="a1899-203">https://github.com/dotnet/announcements/issues/14</span></span> 
-   <span data-ttu-id="a1899-204">**Vytvoření základní image**.</span><span class="sxs-lookup"><span data-stu-id="a1899-204">**Create a base image**.</span></span> <span data-ttu-id="a1899-205">Oficiální dokumentace k Dockeru.</span><span class="sxs-lookup"><span data-stu-id="a1899-205">Official Docker documentation.</span></span>
    [*https://docs.docker.com/engine/userguide/eng-image/baseimages/*](https://docs.docker.com/engine/userguide/eng-image/baseimages/)

![](./media/image7.png)

## <a name="step-3-create-your-custom-docker-images-and-embed-your-application-or-service-in-them"></a><span data-ttu-id="a1899-206">Krok 3.</span><span class="sxs-lookup"><span data-stu-id="a1899-206">Step 3.</span></span> <span data-ttu-id="a1899-207">Vytvoření vlastní Image Dockeru a vložit vaše aplikace nebo služba</span><span class="sxs-lookup"><span data-stu-id="a1899-207">Create your custom Docker images and embed your application or service in them</span></span>

<span data-ttu-id="a1899-208">Pro každou službu v aplikaci budete muset vytvořit související image.</span><span class="sxs-lookup"><span data-stu-id="a1899-208">For each service in your application, you need to create a related image.</span></span> <span data-ttu-id="a1899-209">Pokud vaše aplikace se skládá z jedné služby nebo webové aplikace, potřebujete jenom jedné image.</span><span class="sxs-lookup"><span data-stu-id="a1899-209">If your application is made up of a single service or web application, you just need a single image.</span></span>

<span data-ttu-id="a1899-210">Všimněte si, že Image Dockeru se vytváří automaticky za vás v sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="a1899-210">Note that the Docker images are built automatically for you in Visual Studio.</span></span> <span data-ttu-id="a1899-211">Následující kroky jsou jenom potřebné pro pracovní postup editoru a rozhraní příkazového řádku a vysvětlení pro přehlednost o co se stane pod.</span><span class="sxs-lookup"><span data-stu-id="a1899-211">The following steps are only needed for the editor/CLI workflow and explained for clarity about what happens underneath.</span></span>

<span data-ttu-id="a1899-212">Jako vývojář, potřebujete pro vývoj a testování místně, než přejdete dokončené funkce nebo změňte na systému správy zdrojů (například na Githubu).</span><span class="sxs-lookup"><span data-stu-id="a1899-212">You, as developer, need to develop and test locally until you push a completed feature or change to your source control system (for example, to GitHub).</span></span> <span data-ttu-id="a1899-213">To znamená, že budete muset vytvoření imagí Dockeru a nasazení kontejnerů do místního hostitele Docker (Windows nebo linuxového virtuálního počítače) a spuštění, testování a ladění pro tyto místní kontejnery.</span><span class="sxs-lookup"><span data-stu-id="a1899-213">This means that you need to create the Docker images and deploy containers to a local Docker host (Windows or Linux VM) and run, test, and debug against those local containers.</span></span>

<span data-ttu-id="a1899-214">Vytvoření vlastní image v místním prostředí pomocí rozhraní příkazového řádku Dockeru a vašem souboru Dockerfile, můžete použít příkaz sestavení dockeru, jako obrázek 5 – 5.</span><span class="sxs-lookup"><span data-stu-id="a1899-214">To create a custom image in your local environment by using Docker CLI and your Dockerfile, you can use the docker build command, as in Figure 5-5.</span></span>

![](./media/image8.png)

<span data-ttu-id="a1899-215">**Obrázek 5 až 5**.</span><span class="sxs-lookup"><span data-stu-id="a1899-215">**Figure 5-5**.</span></span> <span data-ttu-id="a1899-216">Vytvoření vlastní image Dockeru</span><span class="sxs-lookup"><span data-stu-id="a1899-216">Creating a custom Docker image</span></span>

<span data-ttu-id="a1899-217">Volitelně můžete místo přímo spouštět sestavení dockeru ze složky projektu, můžete nejdřív vygenerovat nasaditelný složka se požadované knihovny .NET a binární soubory spuštěním dotnet publikovat a použijte příkaz sestavení dockeru.</span><span class="sxs-lookup"><span data-stu-id="a1899-217">Optionally, instead of directly running docker build from the project folder, you can first generate a deployable folder with the required .NET libraries and binaries by running dotnet publish, and then use the docker build command.</span></span>

<span data-ttu-id="a1899-218">Tím se vytvoří image Dockeru s název cesardl/netcore-webapi mikroslužeb – docker: první.</span><span class="sxs-lookup"><span data-stu-id="a1899-218">This will create a Docker image with the name cesardl/netcore-webapi-microservice-docker:first.</span></span> <span data-ttu-id="a1899-219">V takovém případě: nejprve je klíčové slovo představující konkrétní verzi.</span><span class="sxs-lookup"><span data-stu-id="a1899-219">In this case, :first is a tag representing a specific version.</span></span> <span data-ttu-id="a1899-220">Tento krok můžete opakovat pro každý vlastní image, které potřebujete k vytvoření aplikace skládá Dockeru.</span><span class="sxs-lookup"><span data-stu-id="a1899-220">You can repeat this step for each custom image you need to create for your composed Docker application.</span></span>

<span data-ttu-id="a1899-221">Když aplikaci tvoří několik kontejnerů (to znamená, že je vícekontejnerová aplikace), můžete použít také docker-compose up - příkaz sestavení k sestavení všechny obrázky související s jediným příkazem s využitím metadat v související soubory docker-compose.yml.</span><span class="sxs-lookup"><span data-stu-id="a1899-221">When an application is made of multiple containers (that is, it is a multi-container application), you can also use the docker-compose up --build command to build all the related images with a single command by using the metadata exposed in the related docker-compose.yml files.</span></span>

<span data-ttu-id="a1899-222">Najdete existujících bitových kopií ve vašem místním úložišti s využitím dockeru příkaz bitové kopie, jak je znázorněno v obrázek 5 a 6.</span><span class="sxs-lookup"><span data-stu-id="a1899-222">You can find the existing images in your local repository by using the docker images command, as shown in Figure 5-6.</span></span>

![](./media/image9.png)

<span data-ttu-id="a1899-223">**Obrázek 5 a 6.**</span><span class="sxs-lookup"><span data-stu-id="a1899-223">**Figure 5-6.**</span></span> <span data-ttu-id="a1899-224">Zobrazení existujících imagí pomocí příkazu Image dockeru</span><span class="sxs-lookup"><span data-stu-id="a1899-224">Viewing existing images using the docker images command</span></span>

### <a name="creating-docker-images-with-visual-studio"></a><span data-ttu-id="a1899-225">Vytváření imagí Dockeru pomocí sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="a1899-225">Creating Docker images with Visual Studio</span></span>

<span data-ttu-id="a1899-226">Při použití sady Visual Studio k vytvoření projektu s podporou Dockeru, nevytvoříte explicitně bitovou kopii.</span><span class="sxs-lookup"><span data-stu-id="a1899-226">When you are using Visual Studio to create a project with Docker support, you do not explicitly create an image.</span></span> <span data-ttu-id="a1899-227">Místo toho image se vytvoří za vás při stisknutí klávesy F5 a spusťte dockerized aplikaci nebo službě.</span><span class="sxs-lookup"><span data-stu-id="a1899-227">Instead, the image is created for you when you press F5 and run the dockerized application or service.</span></span> <span data-ttu-id="a1899-228">Tento krok je automatické v sadě Visual Studio a to uděláme nezobrazí, ale je důležité vědět, co se děje v pod tím.</span><span class="sxs-lookup"><span data-stu-id="a1899-228">This step is automatic in Visual Studio, and you will not see it happen, but it is important that you know what is going on underneath.</span></span>

![](./media/image10.png)

## <a name="step-4-define-your-services-in-docker-composeyml-when-building-a-multi-container-docker-application"></a><span data-ttu-id="a1899-229">Krok 4.</span><span class="sxs-lookup"><span data-stu-id="a1899-229">Step 4.</span></span> <span data-ttu-id="a1899-230">Definování vašich služeb v docker-compose.yml při sestavování aplikace Dockeru</span><span class="sxs-lookup"><span data-stu-id="a1899-230">Define your services in docker-compose.yml when building a multi-container Docker application</span></span>

<span data-ttu-id="a1899-231">[Docker-compose.yml](https://docs.docker.com/compose/compose-file/) souboru umožňuje definovat sadu souvisejících služeb umožňující nasadit ho jako aplikace skládá pomocí příkazů nasazení.</span><span class="sxs-lookup"><span data-stu-id="a1899-231">The [docker-compose.yml](https://docs.docker.com/compose/compose-file/) file lets you define a set of related services to be deployed as a composed application with deployment commands.</span></span>

<span data-ttu-id="a1899-232">Pokud chcete použít soubor docker-compose.yml, je potřeba vytvořit soubor ve vaší hlavní nebo kořenové složky řešení, s obsahem podobné jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="a1899-232">To use a docker-compose.yml file, you need to create the file in your main or root solution folder, with content similar to that in the following example:</span></span>

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

<span data-ttu-id="a1899-233">Všimněte si, že tento soubor docker-compose.yml je zjednodušený a sloučené verze.</span><span class="sxs-lookup"><span data-stu-id="a1899-233">Note that this docker-compose.yml file is a simplified and merged version.</span></span> <span data-ttu-id="a1899-234">Obsahuje statické konfigurační data pro každý kontejner (např. název vlastní image), která se vždy vztahuje, a navíc informace o konfiguraci, která může záviset na prostředí pro nasazení, jako je připojovací řetězec.</span><span class="sxs-lookup"><span data-stu-id="a1899-234">It contains static configuration data for each container (like the name of the custom image), which always applies, plus configuration information that might depend on the deployment environment, like the connection string.</span></span> <span data-ttu-id="a1899-235">V dalších částech se dozvíte, jak můžete rozdělit do několika konfiguraci docker-compose.yml docker-compose soubory a hodnot v závislosti na prostředí a spuštění typu (ladění nebo vydání).</span><span class="sxs-lookup"><span data-stu-id="a1899-235">In later sections, you will learn how you can split the docker-compose.yml configuration into multiple docker-compose files and override values depending on the environment and execution type (debug or release).</span></span>

<span data-ttu-id="a1899-236">Příklad souboru docker-compose.yml definuje čtyři služby: webmvc service (webová aplikace), dva mikroslužby (catalog.api a ordering.api) a jeden datový zdroj kontejnery sql.data, založené na systému SQL Server pro Linux spuštěný jako kontejner.</span><span class="sxs-lookup"><span data-stu-id="a1899-236">The docker-compose.yml file example defines four services: the webmvc service (a web application), two microservices (catalog.api and ordering.api), and one data source container, sql.data, based on SQL Server for Linux running as a container.</span></span> <span data-ttu-id="a1899-237">Každá služba se nasadí jako kontejner, takže image Dockeru je povinné pro každý.</span><span class="sxs-lookup"><span data-stu-id="a1899-237">Each service is deployed as a container, so a Docker image is required for each.</span></span>

<span data-ttu-id="a1899-238">Soubor docker-compose.yml určuje nejen jaké kontejnery jsou používány, ale jejich jednotlivě konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="a1899-238">The docker-compose.yml file specifies not only what containers are being used, but how they are individually configured.</span></span> <span data-ttu-id="a1899-239">Například webmvc definice kontejneru ve soubor .yml:</span><span class="sxs-lookup"><span data-stu-id="a1899-239">For instance, the webmvc container definition in the .yml file:</span></span>

-   <span data-ttu-id="a1899-240">Pomocí předem sestavených eshop / webové: nejnovější verzi image.</span><span class="sxs-lookup"><span data-stu-id="a1899-240">Uses a pre-built eshop/web:latest image.</span></span> <span data-ttu-id="a1899-241">Ale můžete také nakonfigurovat na obrázku má být sestaven jako součást docker-compose spuštění další konfigurace podle sestavení: oddíl v souboru docker-compose.</span><span class="sxs-lookup"><span data-stu-id="a1899-241">However, you could also configure the image to be built as part of the docker-compose execution with an additional configuration based on a build: section in the docker-compose file.</span></span>

-   <span data-ttu-id="a1899-242">Inicializuje dvou proměnných prostředí (adresa URL katalogu a OrderingUrl).</span><span class="sxs-lookup"><span data-stu-id="a1899-242">Initializes two environment variables (CatalogUrl and OrderingUrl).</span></span>

-   <span data-ttu-id="a1899-243">Předává vystavené port 80 v kontejneru pro externí port 80 na hostitelském počítači.</span><span class="sxs-lookup"><span data-stu-id="a1899-243">Forwards the exposed port 80 on the container to the external port 80 on the host machine.</span></span>

-   <span data-ttu-id="a1899-244">Odkazy webové aplikace v katalogu a řazení služby s závisí\_na nastavení.</span><span class="sxs-lookup"><span data-stu-id="a1899-244">Links the web app to the catalog and ordering service with the depends\_on setting.</span></span> <span data-ttu-id="a1899-245">To způsobí, že služba Počkejte, dokud tyto služby jsou spuštěny.</span><span class="sxs-lookup"><span data-stu-id="a1899-245">This causes the service to wait until those services are started.</span></span>

<span data-ttu-id="a1899-246">Soubor docker-compose.yml v další části jsme se opakování při popisujeme k implementaci mikroslužeb a vícekontejnerových aplikací.</span><span class="sxs-lookup"><span data-stu-id="a1899-246">We will revisit the docker-compose.yml file in a later section when we cover how to implement microservices and multi-container apps.</span></span>

### <a name="working-with-docker-composeyml-in-visual-studio-2017"></a><span data-ttu-id="a1899-247">Práce s docker-compose.yml v sadě Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="a1899-247">Working with docker-compose.yml in Visual Studio 2017</span></span>

<span data-ttu-id="a1899-248">Když přidáte podporu Dockeru řešení do projektu služby v řešení sady Visual Studio, jak je znázorněno v obrázek 5 – 7, Visual Studio do vašeho projektu přidá soubor Dockerfile a přidá oddíl služby (projekt) v rámci vašeho řešení se soubory docker-compose.yml.</span><span class="sxs-lookup"><span data-stu-id="a1899-248">When you add Docker solution support to a service project in a Visual Studio solution, as shown in Figure 5-7, Visual Studio adds a Dockerfile to your project, and it adds a service section (project) in your solution with the docker-compose.yml files.</span></span> <span data-ttu-id="a1899-249">Je snadný způsob, jak spustit sestavování vašich řešení více kontejnerů.</span><span class="sxs-lookup"><span data-stu-id="a1899-249">It is an easy way to start composing your multiple-container solution.</span></span> <span data-ttu-id="a1899-250">Pak můžete otevřít soubory docker-compose.yml a aktualizovat o další funkce.</span><span class="sxs-lookup"><span data-stu-id="a1899-250">You can then open the docker-compose.yml files and update them with additional features.</span></span>

![](./media/image6.png)

<span data-ttu-id="a1899-251">**Obrázek 5 – 7**.</span><span class="sxs-lookup"><span data-stu-id="a1899-251">**Figure 5-7**.</span></span> <span data-ttu-id="a1899-252">Přidání podpory Dockeru kliknutím pravým tlačítkem myši projekt ASP.NET Core v sadě Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="a1899-252">Adding Docker support in Visual Studio 2017 by right-clicking an ASP.NET Core project</span></span>

<span data-ttu-id="a1899-253">Přidání podpory Dockeru v sadě Visual Studio pouze do vašeho projektu přidá soubor Dockerfile, ale přidá informace o konfiguraci na několik souborů docker-compose.yml globální, které jsou nastaveny na úrovni řešení.</span><span class="sxs-lookup"><span data-stu-id="a1899-253">Adding Docker support in Visual Studio not only adds the Dockerfile to your project, but adds the configuration information to several global docker-compose.yml files that are set at the solution level.</span></span>

<span data-ttu-id="a1899-254">Po přidání podpory Dockeru do svého řešení v sadě Visual Studio, zobrazí se také nový uzel (v souboru projektu dockeru compose.dcproj) v Průzkumníku řešení, která obsahuje soubory přidané docker-compose.yml, jak je znázorněno v obrázek 5 až 8.</span><span class="sxs-lookup"><span data-stu-id="a1899-254">After you add Docker support to your solution in Visual Studio, you will also see a new node (in the docker-compose.dcproj project file) in Solution Explorer that contains the added docker-compose.yml files, as shown in Figure 5-8.</span></span>

![](./media/image11.PNG)

<span data-ttu-id="a1899-255">**Obrázek 5 až 8**.</span><span class="sxs-lookup"><span data-stu-id="a1899-255">**Figure 5-8**.</span></span> <span data-ttu-id="a1899-256">**Docker-compose** uzel stromu přidá v okně Průzkumník řešení Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="a1899-256">The **docker-compose** tree node added in Visual Studio 2017 Solution Explorer</span></span>

<span data-ttu-id="a1899-257">Můžete nasadit vícekontejnerové aplikace pomocí docker-compose.yml jeden soubor s použitím docker-compose up příkazu.</span><span class="sxs-lookup"><span data-stu-id="a1899-257">You could deploy a multi-container application with a single docker-compose.yml file by using the docker-compose up command.</span></span> <span data-ttu-id="a1899-258">Ale sady Visual Studio přidá skupinu z nich, mohou přepsat hodnoty v závislosti na prostředí (vývojové oproti produkčním prostředí) a spuštění typu (vydání a ladění).</span><span class="sxs-lookup"><span data-stu-id="a1899-258">However, Visual Studio adds a group of them so you can override values depending on the environment (development versus production) and execution type (release versus debug).</span></span> <span data-ttu-id="a1899-259">Tato funkce bude je popsáno v předchozích částech.</span><span class="sxs-lookup"><span data-stu-id="a1899-259">This capability will be explained in later sections.</span></span>

![](./media/image12.png)

## <a name="step-5-build-and-run-your-docker-application"></a><span data-ttu-id="a1899-260">Krok 5.</span><span class="sxs-lookup"><span data-stu-id="a1899-260">Step 5.</span></span> <span data-ttu-id="a1899-261">Sestavte a spusťte aplikaci v Dockeru</span><span class="sxs-lookup"><span data-stu-id="a1899-261">Build and run your Docker application</span></span>

<span data-ttu-id="a1899-262">Pokud vaše aplikace má pouze jeden kontejner, můžete ji spustit po nasazení na hostitele Docker (virtuální počítač nebo fyzický server).</span><span class="sxs-lookup"><span data-stu-id="a1899-262">If your application only has a single container, you can run it by deploying it to your Docker host (VM or physical server).</span></span> <span data-ttu-id="a1899-263">Nicméně pokud vaše aplikace obsahuje několik služeb, můžete nasadit ho jako aplikace skládá buď pomocí jediného příkazu rozhraní příkazového řádku (docker-compose up), nebo pomocí sady Visual Studio, které budou používat tento příkaz na pozadí.</span><span class="sxs-lookup"><span data-stu-id="a1899-263">However, if your application contains multiple services, you can deploy it as a composed application, either using a single CLI command (docker-compose up), or with Visual Studio, which will use that command under the covers.</span></span> <span data-ttu-id="a1899-264">Podívejme se na různé možnosti.</span><span class="sxs-lookup"><span data-stu-id="a1899-264">Let’s look at the different options.</span></span>

### <a name="option-a-running-a-single-container-with-docker-cli"></a><span data-ttu-id="a1899-265">Možnost A: spuštěný jeden kontejner pomocí rozhraní příkazového řádku Dockeru</span><span class="sxs-lookup"><span data-stu-id="a1899-265">Option A: Running a single-container with Docker CLI</span></span>

<span data-ttu-id="a1899-266">Můžete spustit kontejner Docker s využitím dockeru, spusťte příkaz jako obrázek 5 až 9:</span><span class="sxs-lookup"><span data-stu-id="a1899-266">You can run a Docker container using the docker run command, as in Figure 5-9:</span></span>

```console
  docker run -t -d -p 80:5000 cesardl/netcore-webapi-microservice-docker:first
```

![](./media/image13.png)

<span data-ttu-id="a1899-267">**Obrázek 5 až 9**.</span><span class="sxs-lookup"><span data-stu-id="a1899-267">**Figure 5-9**.</span></span> <span data-ttu-id="a1899-268">Spuštěný kontejner Docker s využitím dockeru, spusťte příkaz</span><span class="sxs-lookup"><span data-stu-id="a1899-268">Running a Docker container using the docker run command</span></span>

<span data-ttu-id="a1899-269">Příkaz v tomto případě váže interní port 5000 z kontejneru na port 80 hostitelském počítači.</span><span class="sxs-lookup"><span data-stu-id="a1899-269">In this case, the command binds the internal port 5000 of the container to port 80 of the host machine.</span></span> <span data-ttu-id="a1899-270">To znamená, že hostitel naslouchá na portu 80 a předává na portu 5000 v kontejneru.</span><span class="sxs-lookup"><span data-stu-id="a1899-270">This means that the host is listening on port 80 and forwarding to port 5000 on the container.</span></span>

### <a name="option-b-running-a-multi-container-application"></a><span data-ttu-id="a1899-271">Možnost B: systémem vícekontejnerová aplikace</span><span class="sxs-lookup"><span data-stu-id="a1899-271">Option B: Running a multi-container application</span></span>

<span data-ttu-id="a1899-272">Ve většině scénářů organizace aplikaci v Dockeru se skládá z více služeb, což znamená, že budete muset spustit vícekontejnerové aplikace, jak je znázorněno v obrázek 5 až 10.</span><span class="sxs-lookup"><span data-stu-id="a1899-272">In most enterprise scenarios, a Docker application will be composed of multiple services, which means you need to run a multi-container application, as shown in Figure 5-10.</span></span>

![](./media/image14.png)

<span data-ttu-id="a1899-273">**Obrázek 5 až 10**.</span><span class="sxs-lookup"><span data-stu-id="a1899-273">**Figure 5-10**.</span></span> <span data-ttu-id="a1899-274">Virtuální počítač s kontejnery Dockeru nasazené</span><span class="sxs-lookup"><span data-stu-id="a1899-274">VM with Docker containers deployed</span></span>

#### <a name="running-a-multi-container-application-with-the-docker-cli"></a><span data-ttu-id="a1899-275">Spuštění vícekontejnerové aplikace pomocí rozhraní příkazového řádku Dockeru</span><span class="sxs-lookup"><span data-stu-id="a1899-275">Running a multi-container application with the Docker CLI</span></span>

<span data-ttu-id="a1899-276">Ke spuštění vícekontejnerové aplikace pomocí rozhraní příkazového řádku Dockeru, můžete spustit docker-compose up příkazu.</span><span class="sxs-lookup"><span data-stu-id="a1899-276">To run a multi-container application with the Docker CLI, you can run the docker-compose up command.</span></span> <span data-ttu-id="a1899-277">Tento soubor používá docker-compose.yml příkaz, abyste měli na úrovni řešení nasazení vícekontejnerových aplikací.</span><span class="sxs-lookup"><span data-stu-id="a1899-277">This command uses the docker-compose.yml file that you have at the solution level to deploy a multi-container application.</span></span> <span data-ttu-id="a1899-278">Obrázek 5 – 11 můžete vidět výsledky při spuštění příkazu z adresáře hlavního projektu, který obsahuje soubor docker-compose.yml.</span><span class="sxs-lookup"><span data-stu-id="a1899-278">Figure 5-11 shows the results when running the command from your main project directory, which contains the docker-compose.yml file.</span></span>

![](./media/image15.png)

<span data-ttu-id="a1899-279">**Obrázek 5 – 11**.</span><span class="sxs-lookup"><span data-stu-id="a1899-279">**Figure 5-11**.</span></span> <span data-ttu-id="a1899-280">Příklad výsledků při spuštění docker-compose up příkaz</span><span class="sxs-lookup"><span data-stu-id="a1899-280">Example results when running the docker-compose up command</span></span>

<span data-ttu-id="a1899-281">Po docker-compose up spuštění příkazu, aplikace a její související kontejnery se nasazují do hostitele Dockeru, jak je znázorněno v reprezentaci virtuálního počítače v obrázek 5 – 10.</span><span class="sxs-lookup"><span data-stu-id="a1899-281">After the docker-compose up command runs, the application and its related containers are deployed into your Docker host, as illustrated in the VM representation in Figure 5-10.</span></span>

#### <a name="running-and-debugging-a-multi-container-application-with-visual-studio"></a><span data-ttu-id="a1899-282">Spouštění a ladění vícekontejnerové aplikace pomocí sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="a1899-282">Running and debugging a multi-container application with Visual Studio</span></span> 

<span data-ttu-id="a1899-283">Nelze získat jednodušší systémem vícekontejnerové aplikace pomocí sady Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="a1899-283">Running a multi-container application using Visual Studio 2017 cannot get simpler.</span></span> <span data-ttu-id="a1899-284">Nelze spustit pouze vícekontejnerové aplikace, ale budete moci ladit jejím kontejnerům přímo ze sady Visual Studio tak, že nastavíte pravidelné zarážky.</span><span class="sxs-lookup"><span data-stu-id="a1899-284">You can not only run the multi-container application, but you are able to debug all its containers directly from Visual Studio by setting regular breakpoints.</span></span>

<span data-ttu-id="a1899-285">Jak už bylo zmíněno dříve, pokaždé, když přidáte řešení podpory Dockeru do projektu v rámci řešení, že projekt je nakonfigurovaný v souboru globální docker-compose.yml (na úrovni řešení), která umožňuje spustit nebo ladit celé řešení najednou.</span><span class="sxs-lookup"><span data-stu-id="a1899-285">As mentioned before, each time you add Docker solution support to a project within a solution, that project is configured in the global (solution-level) docker-compose.yml file, which lets you run or debug the whole solution at once.</span></span> <span data-ttu-id="a1899-286">Visual Studio spustit jeden kontejner pro každý projekt, který podporuje Docker řešení povolené a provedení všech kroků interní za vás (dotnet publikovat, sestavení dockeru atd.).</span><span class="sxs-lookup"><span data-stu-id="a1899-286">Visual Studio will start one container for each project that has Docker solution support enabled, and perform all the internal steps for you (dotnet publish, docker build, etc.).</span></span>

<span data-ttu-id="a1899-287">Důležitý bod je, že, jak je znázorněno v obrázek 5 – 12, v sadě Visual Studio 2017 Další **Docker** příkaz pro akci klíčové F5.</span><span class="sxs-lookup"><span data-stu-id="a1899-287">The important point here is that, as shown in Figure 5-12, in Visual Studio 2017 there is an additional **Docker** command for the F5 key action.</span></span> <span data-ttu-id="a1899-288">Tato možnost umožňuje spustit nebo ladit vícekontejnerová aplikace spuštěním všechny kontejnery, které jsou definovány v souboru docker-compose.yml na úrovni řešení.</span><span class="sxs-lookup"><span data-stu-id="a1899-288">This option lets you run or debug a multi-container application by running all the containers that are defined in the docker-compose.yml files at the solution level.</span></span> <span data-ttu-id="a1899-289">Možnost ladit více kontejnerů řešení znamená, že můžete nastavit několik zarážky, každé zarážky v jiném projektu (kontejner) a při ladění ze sady Visual Studio se zastaví na zarážkách definovány v různých projektech a běží na různé kontejnery.</span><span class="sxs-lookup"><span data-stu-id="a1899-289">The ability to debug multiple-container solutions means that you can set several breakpoints, each breakpoint in a different project (container), and while debugging from Visual Studio you will stop at breakpoints defined in different projects and running on different containers.</span></span>

![](./media/image16.png)

<span data-ttu-id="a1899-290">**Obrázek 5 – 12**.</span><span class="sxs-lookup"><span data-stu-id="a1899-290">**Figure 5-12**.</span></span> <span data-ttu-id="a1899-291">Spouštění vícekontejnerových aplikací v sadě Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="a1899-291">Running multi-container apps in Visual Studio 2017</span></span>

### <a name="additional-resources"></a><span data-ttu-id="a1899-292">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="a1899-292">Additional resources</span></span>

-   <span data-ttu-id="a1899-293">**Nasazení kontejneru ASP.NET na vzdáleného hostitele Docker**
    [*https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker*](https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker)</span><span class="sxs-lookup"><span data-stu-id="a1899-293">**Deploy an ASP.NET container to a remote Docker host**
[*https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker*](https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker)</span></span>

### <a name="a-note-about-testing-and-deploying-with-orchestrators"></a><span data-ttu-id="a1899-294">Poznámka k testování a nasazení s orchestrátory</span><span class="sxs-lookup"><span data-stu-id="a1899-294">A note about testing and deploying with orchestrators</span></span>

<span data-ttu-id="a1899-295">Docker-compose up a příkazy dockeru spustit (nebo spouštění a ladění kontejnerů v sadě Visual Studio) jsou dostatečné pro testování kontejnerů ve vašem vývojovém prostředí.</span><span class="sxs-lookup"><span data-stu-id="a1899-295">The docker-compose up and docker run commands (or running and debugging the containers in Visual Studio) are adequate for testing containers in your development environment.</span></span> <span data-ttu-id="a1899-296">Ale tento přístup byste neměli používat, pokud cílíte na clustery Dockeru a orchestrátorů, jako je Docker Swarm, Mesosphere DC/OS nebo Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="a1899-296">But you should not use this approach if you are targeting Docker clusters and orchestrators like Docker Swarm, Mesosphere DC/OS, or Kubernetes.</span></span> <span data-ttu-id="a1899-297">Pokud používáte cluster jako [režim Docker Swarm](https://docs.docker.com/engine/swarm/) (k dispozici v Docker CE pro Windows a Mac od verze 1.12), musíte nasadit a testovat pomocí dalších příkazů, jako jsou [vytvoření služby docker](https://docs.docker.com/engine/reference/commandline/service_create/) pro jednotné služby.</span><span class="sxs-lookup"><span data-stu-id="a1899-297">If you are using a cluster like [Docker Swarm mode](https://docs.docker.com/engine/swarm/) (available in Docker CE for Windows and Mac since version 1.12), you need to deploy and test with additional commands like [docker service create](https://docs.docker.com/engine/reference/commandline/service_create/) for single services.</span></span> <span data-ttu-id="a1899-298">Pokud nasazujete aplikace skládá z několika kontejnerů, můžete použít [docker compose sady](https://docs.docker.com/compose/reference/bundle/) a [docker nasazení myBundleFile](https://docs.docker.com/engine/reference/commandline/deploy/) se nasazení skládá aplikace jako *zásobníku*.</span><span class="sxs-lookup"><span data-stu-id="a1899-298">If you are deploying an application composed of several containers, you use [docker compose bundle](https://docs.docker.com/compose/reference/bundle/) and [docker deploy myBundleFile](https://docs.docker.com/engine/reference/commandline/deploy/) to deploy the composed application as a *stack*.</span></span> <span data-ttu-id="a1899-299">Další informace naleznete v příspěvku blogu [Představujeme experimentální distribuované aplikace sady](https://blog.docker.com/2016/06/docker-app-bundle/) v dokumentaci k Dockeru.</span><span class="sxs-lookup"><span data-stu-id="a1899-299">For more information, see the blog post [Introducing Experimental Distributed Application Bundles](https://blog.docker.com/2016/06/docker-app-bundle/) in the Docker documentation.</span></span> <span data-ttu-id="a1899-300">na serveru Docker.</span><span class="sxs-lookup"><span data-stu-id="a1899-300">on the Docker site.</span></span>

<span data-ttu-id="a1899-301">Pro [DC/OS](https://mesosphere.com/blog/2015/09/02/dcos-cli-command-line-tool-datacenter/) a [Kubernetes](http://kubernetes.io/docs/user-guide/deployments/) použijete jiné nasazení příkazy a skripty také.</span><span class="sxs-lookup"><span data-stu-id="a1899-301">For [DC/OS](https://mesosphere.com/blog/2015/09/02/dcos-cli-command-line-tool-datacenter/) and [Kubernetes](http://kubernetes.io/docs/user-guide/deployments/) you would use different deployment commands and scripts as well.</span></span>

![](./media/image17.png)

## <a name="step-6-test-your-docker-application-using-your-local-docker-host"></a><span data-ttu-id="a1899-302">Krok 6.</span><span class="sxs-lookup"><span data-stu-id="a1899-302">Step 6.</span></span> <span data-ttu-id="a1899-303">Otestujte aplikaci Dockeru pomocí místního hostitele Docker</span><span class="sxs-lookup"><span data-stu-id="a1899-303">Test your Docker application using your local Docker host</span></span>

<span data-ttu-id="a1899-304">Tento krok se liší v závislosti na tom, co aplikace dělá.</span><span class="sxs-lookup"><span data-stu-id="a1899-304">This step will vary depending on what your application is doing.</span></span> <span data-ttu-id="a1899-305">V jednoduchou aplikaci webového rozhraní .NET Core, který je nasazen jako jedním kontejnerem nebo služby můžete přístup ke službě otevřením prohlížeče na hostitele Dockeru a přechodu k této lokalitě, jak je znázorněno v obrázek 5-13.</span><span class="sxs-lookup"><span data-stu-id="a1899-305">In a simple .NET Core Web application that is deployed as a single container or service, you can access the service by opening a browser on the Docker host and navigating to that site as shown in Figure 5-13.</span></span> <span data-ttu-id="a1899-306">(Pokud se konfigurace v souboru Dockerfile mapuje kontejneru na port na hostiteli není nic jiného než 80, zahrnovat port hostitele v adrese URL.)</span><span class="sxs-lookup"><span data-stu-id="a1899-306">(If the configuration in the Dockerfile maps the container to a port on the host that is anything other than 80, include the host port in the URL.)</span></span>

![](./media/image18.png)

<span data-ttu-id="a1899-307">**Obrázek 5-13**.</span><span class="sxs-lookup"><span data-stu-id="a1899-307">**Figure 5-13**.</span></span> <span data-ttu-id="a1899-308">Příklad testování vašich aplikací Dockeru s místním prostředí s využitím místního hostitele</span><span class="sxs-lookup"><span data-stu-id="a1899-308">Example of testing your Docker application locally using localhost</span></span>

<span data-ttu-id="a1899-309">Pokud localhost neukazuje na Dockeru IP adresa hostitele (ve výchozím nastavení se při použití Docker CE by měl), přejděte k vaší službě, můžete IP adresu síťové karty v počítači.</span><span class="sxs-lookup"><span data-stu-id="a1899-309">If localhost is not pointing to the Docker host IP (by default, when using Docker CE, it should), to navigate to your service, use the IP address of your machine’s network card.</span></span>

<span data-ttu-id="a1899-310">Všimněte si, že tato adresa URL v prohlížeči používá port 80, třeba konkrétní kontejner diskutovány.</span><span class="sxs-lookup"><span data-stu-id="a1899-310">Note that this URL in the browser uses port 80 for the particular container example being discussed.</span></span> <span data-ttu-id="a1899-311">Ale interně požadavky přesměrováni na portu 5000, protože bylo jak nasazení s prostředím docker, spusťte příkaz, jak je popsáno v předchozím kroku.</span><span class="sxs-lookup"><span data-stu-id="a1899-311">However, internally the requests are being redirected to port 5000, because that was how it was deployed with the docker run command, as explained in a previous step.</span></span>

<span data-ttu-id="a1899-312">Můžete také test aplikace pomocí curl z terminálu, jak je znázorněno v obrázek 5-14.</span><span class="sxs-lookup"><span data-stu-id="a1899-312">You can also test the application using curl from the terminal, as shown in Figure 5-14.</span></span> <span data-ttu-id="a1899-313">V instalaci Dockeru na Windows IP adresa hostitele Docker výchozí hodnota je vždy 10.0.75.1 kromě vlastní IP adresu vašeho počítače.</span><span class="sxs-lookup"><span data-stu-id="a1899-313">In a Docker installation on Windows, the default Docker Host IP is always 10.0.75.1 in addition to your machine’s actual IP address.</span></span>

![](./media/image19.png)

<span data-ttu-id="a1899-314">**Obrázek 5-14**.</span><span class="sxs-lookup"><span data-stu-id="a1899-314">**Figure 5-14**.</span></span> <span data-ttu-id="a1899-315">Příklad testování vašich aplikací Dockeru s místně pomocí curl</span><span class="sxs-lookup"><span data-stu-id="a1899-315">Example of testing your Docker application locally using curl</span></span>

### <a name="testing-and-debugging-containers-with-visual-studio-2017"></a><span data-ttu-id="a1899-316">Testování a ladění kontejnerů pomocí sady Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="a1899-316">Testing and debugging containers with Visual Studio 2017</span></span>

<span data-ttu-id="a1899-317">Při spouštění a ladění kontejnerů pomocí sady Visual Studio 2017, můžete ladit aplikaci .NET v podstatě stejným způsobem jako při spuštění bez kontejnery.</span><span class="sxs-lookup"><span data-stu-id="a1899-317">When running and debugging the containers with Visual Studio 2017, you can debug the .NET application in much the same way as you would when running without containers.</span></span>

### <a name="testing-and-debugging-without-visual-studio"></a><span data-ttu-id="a1899-318">Testování a ladění bez sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="a1899-318">Testing and debugging without Visual Studio</span></span>

<span data-ttu-id="a1899-319">Pokud vyvíjíte pomocí editoru/CLI přístup, je obtížnější ladění kontejnerů a budete chtít ladit vygenerováním trasování.</span><span class="sxs-lookup"><span data-stu-id="a1899-319">If you are developing using the editor/CLI approach, debugging containers is more difficult and you will want to debug by generating traces.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="a1899-320">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="a1899-320">Additional resources</span></span>

-   <span data-ttu-id="a1899-321">**Ladění aplikací v místním kontejneru Dockeru**
    [*https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh*](https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh)</span><span class="sxs-lookup"><span data-stu-id="a1899-321">**Debugging apps in a local Docker container**
[*https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh*](https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh)</span></span>

-   <span data-ttu-id="a1899-322">**Steve Lasker. Sestavení, ladění, nasazení aplikace ASP.NET Core s Dockerem.**</span><span class="sxs-lookup"><span data-stu-id="a1899-322">**Steve Lasker. Build, Debug, Deploy ASP.NET Core Apps with Docker.**</span></span> <span data-ttu-id="a1899-323">Video.</span><span class="sxs-lookup"><span data-stu-id="a1899-323">Video.</span></span>
    [*https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T115*](https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T115)

## <a name="simplified-workflow-when-developing-containers-with-visual-studio"></a><span data-ttu-id="a1899-324">Zjednodušené pracovní postupy při vývoji kontejnery pomocí sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="a1899-324">Simplified workflow when developing containers with Visual Studio</span></span>

<span data-ttu-id="a1899-325">Efektivně pracovní postup při používání sady Visual Studio je mnohem jednodušší než při použití editoru/CLI přístup.</span><span class="sxs-lookup"><span data-stu-id="a1899-325">Effectively, the workflow when using Visual Studio is a lot simpler than if you use the editor/CLI approach.</span></span> <span data-ttu-id="a1899-326">Většina kroků vyžadují Docker související s soubor Dockerfile a soubory docker-compose.yml jsou skryta nebo zjednodušená sada Visual Studio, jak je znázorněno v obrázek 5 – 15.</span><span class="sxs-lookup"><span data-stu-id="a1899-326">Most of the steps required by Docker related to the Dockerfile and docker-compose.yml files are hidden or simplified by Visual Studio, as shown in Figure 5-15.</span></span>

![](./media/image20.png)

<span data-ttu-id="a1899-327">**Obrázek 5 – 15**.</span><span class="sxs-lookup"><span data-stu-id="a1899-327">**Figure 5-15**.</span></span> <span data-ttu-id="a1899-328">Zjednodušené pracovní postupy při vývoji pomocí sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="a1899-328">Simplified workflow when developing with Visual Studio</span></span>

<span data-ttu-id="a1899-329">Kromě toho budete muset provést krok 2 (Přidání podpory Dockeru do vašich projektů) pouze jednou.</span><span class="sxs-lookup"><span data-stu-id="a1899-329">In addition, you need to perform step 2 (adding Docker support to your projects) just once.</span></span> <span data-ttu-id="a1899-330">Proto je podobný běžné vývojářské úlohy pracovního postupu, při použití rozhraní .NET pro další vývoj.</span><span class="sxs-lookup"><span data-stu-id="a1899-330">Therefore, the workflow is similar to your usual development tasks when using .NET for any other development.</span></span> <span data-ttu-id="a1899-331">Je potřeba vědět, co se děje na pozadí (procesu sestavení, jaké základní Image, kterou používáte, nasazení kontejnerů, atd.) a v některých případech bude také nutné upravit soubor Dockerfile nebo docker-compose.yml k přizpůsobení chování.</span><span class="sxs-lookup"><span data-stu-id="a1899-331">You need to know what is going on under the covers (the image build process, what base images you are using, deployment of containers, etc.) and sometimes you will also need to edit the Dockerfile or docker-compose.yml file to customize behaviors.</span></span> <span data-ttu-id="a1899-332">Ale většinu práce výrazně zjednodušuje použití sady Visual Studio, což je mnohem vyšší produktivitu.</span><span class="sxs-lookup"><span data-stu-id="a1899-332">But most of the work is greatly simplified by using Visual Studio, making you a lot more productive.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="a1899-333">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="a1899-333">Additional resources</span></span>

-   <span data-ttu-id="a1899-334">**Steve Lasker. Vývoj na platformě .NET dockeru pomocí sady Visual Studio 2017**
    [*https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T111*](https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T111)</span><span class="sxs-lookup"><span data-stu-id="a1899-334">**Steve Lasker. .NET Docker Development with Visual Studio 2017**
[*https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T111*](https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T111)</span></span>

-   <span data-ttu-id="a1899-335">**Jeffrey T. Fritz. Vložte aplikace .NET Core v kontejneru pomocí nového nástroje Dockeru pro Visual Studio**
    [*https://blogs.msdn.microsoft.com/webdev/2016/11/16/new-docker-tools-for-visual-studio/*](https://blogs.msdn.microsoft.com/webdev/2016/11/16/new-docker-tools-for-visual-studio/)</span><span class="sxs-lookup"><span data-stu-id="a1899-335">**Jeffrey T. Fritz. Put a .NET Core App in a Container with the new Docker Tools for Visual Studio**
[*https://blogs.msdn.microsoft.com/webdev/2016/11/16/new-docker-tools-for-visual-studio/*](https://blogs.msdn.microsoft.com/webdev/2016/11/16/new-docker-tools-for-visual-studio/)</span></span>

## <a name="using-powershell-commands-in-a-dockerfile-to-set-up-windows-containers"></a><span data-ttu-id="a1899-336">Pomocí příkazů prostředí PowerShell v souboru Dockerfile k nastavení kontejnery Windows</span><span class="sxs-lookup"><span data-stu-id="a1899-336">Using PowerShell commands in a Dockerfile to set up Windows Containers</span></span> 

<span data-ttu-id="a1899-337">[Kontejnery Windows](https://msdn.microsoft.com/en-us/virtualization/windowscontainers/about/about_overview) umožňují převést svoje stávající aplikace pro Windows do Image Dockeru a nasadit je pomocí stejných nástrojů jako ostatní ekosystému Dockeru.</span><span class="sxs-lookup"><span data-stu-id="a1899-337">[Windows Containers](https://msdn.microsoft.com/en-us/virtualization/windowscontainers/about/about_overview) allow you to convert your existing Windows applications into Docker images and deploy them with the same tools as the rest of the Docker ecosystem.</span></span> <span data-ttu-id="a1899-338">Pokud chcete používat kontejnery Windows, spusťte příkazy Powershellu v souboru Dockerfile, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="a1899-338">To use Windows Containers, you run PowerShell commands in the Dockerfile, as shown in the following example:</span></span>

```Dockerfile
FROM microsoft/windowsservercore
  
LABEL Description="IIS" Vendor="Microsoft" Version="10"
  
RUN powershell -Command Add-WindowsFeature Web-Server
  
CMD [ "ping", "localhost", "-t" ]
```

<span data-ttu-id="a1899-339">V tomto případě jsme se pomocí základní image jádra serveru systému Windows (od nastavení) a instalace služby IIS pomocí příkazu prostředí PowerShell (nastavení spuštění).</span><span class="sxs-lookup"><span data-stu-id="a1899-339">In this case, we are using a Windows Server Core base image (the FROM setting) and installing IIS with a PowerShell command (the RUN setting).</span></span> <span data-ttu-id="a1899-340">Podobným způsobem můžete také použít příkazy prostředí PowerShell nastavit další komponenty, jako je ASP.NET 4.x, .NET 4.6 nebo jiný software pro Windows.</span><span class="sxs-lookup"><span data-stu-id="a1899-340">In a similar way, you could also use PowerShell commands to set up additional components like ASP.NET 4.x, .NET 4.6, or any other Windows software.</span></span> <span data-ttu-id="a1899-341">Například následující příkaz v souboru Dockerfile Nastaví technologii ASP.NET 4.5:</span><span class="sxs-lookup"><span data-stu-id="a1899-341">For example, the following command in a Dockerfile sets up ASP.NET 4.5:</span></span>

```Dockerfile
RUN powershell add-windowsfeature web-asp-net45
```

### <a name="additional-resources"></a><span data-ttu-id="a1899-342">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="a1899-342">Additional resources</span></span>

-   <span data-ttu-id="a1899-343">**aspnet-docker/Dockerfile.**</span><span class="sxs-lookup"><span data-stu-id="a1899-343">**aspnet-docker/Dockerfile.**</span></span> <span data-ttu-id="a1899-344">Příklady příkazů Powershellu spouštět z soubory dockerfile začlenit funkce Windows.</span><span class="sxs-lookup"><span data-stu-id="a1899-344">Example Powershell commands to run from dockerfiles to include Windows features.</span></span>
    [*https://github.com/Microsoft/aspnet-docker/blob/master/4.6.2/Dockerfile*](https://github.com/Microsoft/aspnet-docker/blob/master/4.6.2/Dockerfile)

>[!div class="step-by-step"]
<span data-ttu-id="a1899-345">[Předchozí](index.md)
[další](../net-core-single-containers-linux-windows-server-hosts/index.md)</span><span class="sxs-lookup"><span data-stu-id="a1899-345">[Previous](index.md)
[Next](../net-core-single-containers-linux-windows-server-hosts/index.md)</span></span>
