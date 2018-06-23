---
title: Pracovní postup vývoje pro Docker aplikace
description: Architektura Mikroslužeb .NET pro aplikace .NET Kontejnerizované | Pracovní postup vývoje pro Docker aplikace
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/18/2017
ms.openlocfilehash: 2e29e88a104050230b7816da6793120d61de7bc6
ms.sourcegitcommit: c217b067985905cb21eafc5dd9a83568d7ff4e45
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/22/2018
ms.locfileid: "36314949"
---
# <a name="development-workflow-for-docker-apps"></a><span data-ttu-id="d64f9-103">Pracovní postup vývoje pro Docker aplikace</span><span class="sxs-lookup"><span data-stu-id="d64f9-103">Development workflow for Docker apps</span></span>

<span data-ttu-id="d64f9-104">Životního cyklu aplikace spustí na každý vývojář počítače, kde vývojář kódy aplikace pomocí jejich upřednostňovaný jazyk a testy ho místně.</span><span class="sxs-lookup"><span data-stu-id="d64f9-104">The application development lifecycle starts at each developer’s machine, where the developer codes the application using their preferred language and tests it locally.</span></span> <span data-ttu-id="d64f9-105">Bez ohledu na to, které jazyk, architektura a platforma vývojář vybere, se tento pracovní postup vývojář je vždy vývoj a testování Docker kontejnery, ale tak místně.</span><span class="sxs-lookup"><span data-stu-id="d64f9-105">No matter which language, framework, and platform the developer chooses, with this workflow, the developer is always developing and testing Docker containers, but doing so locally.</span></span>

<span data-ttu-id="d64f9-106">Každý kontejner (instance Docker Image) zahrnuje následující součásti:</span><span class="sxs-lookup"><span data-stu-id="d64f9-106">Each container (an instance of a Docker image) includes the following components:</span></span>

-   <span data-ttu-id="d64f9-107">Výběr operačního systému, (například distribuce systému Linux, Windows Nano Server nebo jádro systému Windows Server).</span><span class="sxs-lookup"><span data-stu-id="d64f9-107">An operating system selection (for example, a Linux distribution, Windows Nano Server, or Windows Server Core).</span></span>

-   <span data-ttu-id="d64f9-108">Soubory přidal developer (binární soubory aplikace, atd.).</span><span class="sxs-lookup"><span data-stu-id="d64f9-108">Files added by the developer (application binaries, etc.).</span></span>

-   <span data-ttu-id="d64f9-109">Informace o konfiguraci (nastavení prostředí a závislosti).</span><span class="sxs-lookup"><span data-stu-id="d64f9-109">Configuration information (environment settings and dependencies).</span></span>

## <a name="workflow-for-developing-docker-container-based-applications"></a><span data-ttu-id="d64f9-110">Pracovní postup pro vývoj aplikací na základě kontejner Docker</span><span class="sxs-lookup"><span data-stu-id="d64f9-110">Workflow for developing Docker container-based applications</span></span>

<span data-ttu-id="d64f9-111">Tato část popisuje *vnitřní smyčky* pracovní postup vývoje pro aplikace založené na kontejner Docker.</span><span class="sxs-lookup"><span data-stu-id="d64f9-111">This section describes the *inner-loop* development workflow for Docker container-based applications.</span></span> <span data-ttu-id="d64f9-112">Pracovní postup vnitřní smyčky znamená ji není přihlédnutím k širší DevOps pracovního postupu a právě se zaměřuje na vývoj pro práci na počítači pro vývojáře.</span><span class="sxs-lookup"><span data-stu-id="d64f9-112">The inner-loop workflow means it is not taking into account the broader DevOps workflow and just focuses on the development work done on the developer’s computer.</span></span> <span data-ttu-id="d64f9-113">Počáteční kroky pro nastavení prostředí nejsou zahrnuty, od těch, které se provádějí pouze jednou.</span><span class="sxs-lookup"><span data-stu-id="d64f9-113">The initial steps to set up the environment are not included, since those are done only once.</span></span>

<span data-ttu-id="d64f9-114">Aplikace se skládá z vlastní služby a další knihovny (závislosti).</span><span class="sxs-lookup"><span data-stu-id="d64f9-114">An application is composed of your own services plus additional libraries (dependencies).</span></span> <span data-ttu-id="d64f9-115">Následují základní kroky, které obvykle podniknout při vytvoření aplikace Docker, jak ukazuje následující obrázek 5-1.</span><span class="sxs-lookup"><span data-stu-id="d64f9-115">The following are the basic steps you usually take when building a Docker application, as illustrated in Figure 5-1.</span></span>

![](./media/image1.png)

<span data-ttu-id="d64f9-116">**Obrázek 5-1.**</span><span class="sxs-lookup"><span data-stu-id="d64f9-116">**Figure 5-1.**</span></span> <span data-ttu-id="d64f9-117">Krok za krokem pracovního postupu pro vývoj aplikací kontejnerizované Docker</span><span class="sxs-lookup"><span data-stu-id="d64f9-117">Step-by-step workflow for developing Docker containerized apps</span></span>

<span data-ttu-id="d64f9-118">V této příručce je podrobně popsán tento celý proces a každé hlavní fázi se vysvětluje zaměřené na prostředí sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d64f9-118">In this guide, this whole process is detailed and every major step is explained by focusing on a Visual Studio environment.</span></span>

<span data-ttu-id="d64f9-119">Pokud používáte přístup vývoj editor nebo rozhraní příkazového řádku (například Visual Studio Code a příkazového řádku Dockeru v systému macOS nebo Windows), je třeba vědět každý krok, obecně podrobněji, než pokud používáte Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d64f9-119">When you are using an editor/CLI development approach (for example, Visual Studio Code plus Docker CLI on macOS or Windows), you need to know every step, generally in more detail than if you are using Visual Studio.</span></span> <span data-ttu-id="d64f9-120">Další podrobnosti o práci v prostředí rozhraní příkazového řádku najdete v části elektronická kniha [životního cyklu aplikace Kontejnerizované Docker s Platforms Microsoft a nástrojů](http://aka.ms/dockerlifecycleebook/).</span><span class="sxs-lookup"><span data-stu-id="d64f9-120">For more details about working in a CLI environment, refer to the e-book [Containerized Docker Application lifecycle with Microsoft Platforms and Tools](http://aka.ms/dockerlifecycleebook/).</span></span>

<span data-ttu-id="d64f9-121">Pokud používáte Visual Studio 2015 nebo Visual Studio 2017, mnoho z těchto kroků jsou zpracovávány pro vás, což výrazně zvyšuje produktivitu.</span><span class="sxs-lookup"><span data-stu-id="d64f9-121">When you are using Visual Studio 2015 or Visual Studio 2017, many of those steps are handled for you, which dramatically improves your productivity.</span></span> <span data-ttu-id="d64f9-122">To platí hlavně pokud používáte Visual Studio 2017 a cílení na více kontejneru aplikace.</span><span class="sxs-lookup"><span data-stu-id="d64f9-122">This is especially true when you are using Visual Studio 2017 and targeting multi-container applications.</span></span> <span data-ttu-id="d64f9-123">Například s jediným klepnutím myši, přidá Visual Studio soubor Docker a docker-compose.yml soubor do vašich projektů s konfigurací pro vaši aplikaci.</span><span class="sxs-lookup"><span data-stu-id="d64f9-123">For instance, with just one mouse click, Visual Studio adds the Dockerfile and docker-compose.yml file to your projects with the configuration for your application.</span></span> <span data-ttu-id="d64f9-124">Při spuštění aplikace v sadě Visual Studio, bitovou kopii Docker sestavení a spuštění aplikace s více kontejnerů přímo v Docker; i umožňuje ladit několik kontejnerů najednou.</span><span class="sxs-lookup"><span data-stu-id="d64f9-124">When you run the application in Visual Studio, it builds the Docker image and runs the multi-container application directly in Docker; it even allows you to debug several containers at once.</span></span> <span data-ttu-id="d64f9-125">Tyto funkce budou zvýšení rychlosti vývoj.</span><span class="sxs-lookup"><span data-stu-id="d64f9-125">These features will boost your development speed.</span></span>

<span data-ttu-id="d64f9-126">Ale stejně, protože sada Visual Studio provádí tyto kroky automatické neznamená, že nepotřebujete vědět, co se děje v dole s Docker.</span><span class="sxs-lookup"><span data-stu-id="d64f9-126">However, just because Visual Studio makes those steps automatic does not mean that you do not need to know what is going on underneath with Docker.</span></span> <span data-ttu-id="d64f9-127">Proto v pokyny, který následuje, jsme podrobnosti každý krok.</span><span class="sxs-lookup"><span data-stu-id="d64f9-127">Therefore, in the guidance that follows, we detail every step.</span></span>

![](./media/image2.png)

## <a name="step-1-start-coding-and-create-your-initial-application-or-service-baseline"></a><span data-ttu-id="d64f9-128">Krok 1.</span><span class="sxs-lookup"><span data-stu-id="d64f9-128">Step 1.</span></span> <span data-ttu-id="d64f9-129">Psaní a vytvořit počáteční aplikace nebo služby směrného plánu</span><span class="sxs-lookup"><span data-stu-id="d64f9-129">Start coding and create your initial application or service baseline</span></span>

<span data-ttu-id="d64f9-130">Vývoj aplikace s Docker je podobným způsobem můžete vyvíjet aplikace bez Docker.</span><span class="sxs-lookup"><span data-stu-id="d64f9-130">Developing a Docker application is similar to the way you develop an application without Docker.</span></span> <span data-ttu-id="d64f9-131">Rozdíl je, že při vývoji pro Docker, jsou nasazení a testování aplikací nebo služeb spuštěných v rámci Docker kontejnerů ve vašem místním prostředí.</span><span class="sxs-lookup"><span data-stu-id="d64f9-131">The difference is that while developing for Docker, you are deploying and testing your application or services running within Docker containers in your local environment.</span></span> <span data-ttu-id="d64f9-132">Kontejner může být kontejner Linux nebo kontejneru systému Windows.</span><span class="sxs-lookup"><span data-stu-id="d64f9-132">The container can be either a Linux container or a Windows container.</span></span>

### <a name="set-up-your-local-environment-with-visual-studio"></a><span data-ttu-id="d64f9-133">Nastavení místního prostředí pomocí sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="d64f9-133">Set up your local environment with Visual Studio</span></span>

<span data-ttu-id="d64f9-134">Pokud chcete začít, zajistěte, aby byla [Docker Community Edition (CE)](https://www.docker.com/community-edition) pro Windows nainstalované, jak je popsáno v následujících pokynech:</span><span class="sxs-lookup"><span data-stu-id="d64f9-134">To begin, make sure you have [Docker Community Edition (CE)](https://www.docker.com/community-edition) for Windows installed, as explained in the following instructions:</span></span>

[<span data-ttu-id="d64f9-135">Začínáme s Docker CE pro Windows</span><span class="sxs-lookup"><span data-stu-id="d64f9-135">Get started with Docker CE for Windows</span></span>](https://docs.docker.com/docker-for-windows/)

<span data-ttu-id="d64f9-136">Kromě toho je nutné nainstalovat Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="d64f9-136">In addition, you will need Visual Studio 2017 installed.</span></span> <span data-ttu-id="d64f9-137">Je to upřednostňovaný přes Visual Studio 2015 s nástroji Visual Studio Tools pro Docker add-in, proto Visual Studio 2017 má pokročilejší podporu pro Docker, jako je podpora pro ladění kontejnerů.</span><span class="sxs-lookup"><span data-stu-id="d64f9-137">This is preferred over Visual Studio 2015 with the Visual Studio Tools for Docker add-in, because Visual Studio 2017 has more advanced support for Docker, like support for debugging containers.</span></span> <span data-ttu-id="d64f9-138">Visual Studio 2017 zahrnuje nástroje pro Docker, pokud jste vybrali **.NET Core a Docker** zatížení během instalace, jak je znázorněno na obrázku 5-2.</span><span class="sxs-lookup"><span data-stu-id="d64f9-138">Visual Studio 2017 includes the tooling for Docker if you selected the **.NET Core and Docker** workload during installation, as shown in Figure 5-2.</span></span>

![](./media/image3.png)

<span data-ttu-id="d64f9-139">**Obrázek 5-2**.</span><span class="sxs-lookup"><span data-stu-id="d64f9-139">**Figure 5-2**.</span></span> <span data-ttu-id="d64f9-140">Výběr **.NET Core a Docker** zatížení během instalace Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="d64f9-140">Selecting the **.NET Core and Docker** workload during Visual Studio 2017 setup</span></span>

<span data-ttu-id="d64f9-141">Kódování svoji aplikaci v prostý .NET (obvykle v .NET Core, pokud máte v úmyslu použít kontejnery) můžete spustit i před povolením Docker v aplikaci a nasazení a testování v Docker.</span><span class="sxs-lookup"><span data-stu-id="d64f9-141">You can start coding your application in plain .NET (usually in .NET Core if you are planning to use containers) even before enabling Docker in your application and deploying and testing in Docker.</span></span> <span data-ttu-id="d64f9-142">Doporučujeme však spustit pracující na Docker co nejdříve vzhledem k tomu, který bude reálného prostředí a problémy s můžete zjistit co nejdříve.</span><span class="sxs-lookup"><span data-stu-id="d64f9-142">However, it is recommended that you start working on Docker as soon as possible, because that will be the real environment and any issues can be discovered as soon as possible.</span></span> <span data-ttu-id="d64f9-143">To je podporováno, protože Visual Studio usnadňuje tak pracovat s Docker, téměř funguje transparentní – nejlepší příklad při ladění aplikace s více kontejner ze sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d64f9-143">This is encouraged because Visual Studio makes it so easy to work with Docker that it almost feels transparent—the best example when debugging multi-container applications from Visual Studio.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="d64f9-144">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="d64f9-144">Additional resources</span></span>

-   <span data-ttu-id="d64f9-145">**Začínáme s Docker CE pro Windows**
    [*https://docs.docker.com/docker-for-windows/*](https://docs.docker.com/docker-for-windows/)</span><span class="sxs-lookup"><span data-stu-id="d64f9-145">**Get started with Docker CE for Windows**
[*https://docs.docker.com/docker-for-windows/*](https://docs.docker.com/docker-for-windows/)</span></span>

-   <span data-ttu-id="d64f9-146">**Visual Studio 2017**
    [*https://visualstudio.microsoft.com/downloads/*](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)</span><span class="sxs-lookup"><span data-stu-id="d64f9-146">**Visual Studio 2017**
[*https://visualstudio.microsoft.com/downloads/*](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)</span></span>

![](./media/image4.png)

## <a name="step-2-create-a-dockerfile-related-to-an-existing-net-base-image"></a><span data-ttu-id="d64f9-147">Krok 2.</span><span class="sxs-lookup"><span data-stu-id="d64f9-147">Step 2.</span></span> <span data-ttu-id="d64f9-148">Vytvořit soubor Docker související s existující základní image rozhraní .NET</span><span class="sxs-lookup"><span data-stu-id="d64f9-148">Create a Dockerfile related to an existing .NET base image</span></span>

<span data-ttu-id="d64f9-149">Je třeba soubor Docker pro každý vlastní image, kterou chcete vytvořit; soubor Docker pro každý kontejner k nasazení, musíte taky jestli nasadit automaticky ze sady Visual Studio nebo ručně pomocí rozhraní příkazového řádku Dockeru (docker spustit a docker-tvoří příkazů).</span><span class="sxs-lookup"><span data-stu-id="d64f9-149">You need a Dockerfile for each custom image you want to build; you also need a Dockerfile for each container to be deployed, whether you deploy automatically from Visual Studio or manually using the Docker CLI (docker run and docker-compose commands).</span></span> <span data-ttu-id="d64f9-150">Pokud vaše aplikace obsahuje jeden vlastní službu, je třeba jeden soubor Docker.</span><span class="sxs-lookup"><span data-stu-id="d64f9-150">If your application contains a single custom service, you need a single Dockerfile.</span></span> <span data-ttu-id="d64f9-151">Pokud vaše aplikace obsahuje více služeb (jako architektura mikroslužeb), je třeba jeden soubor Docker pro každou službu.</span><span class="sxs-lookup"><span data-stu-id="d64f9-151">If your application contains multiple services (as in a microservices architecture), you need one Dockerfile for each service.</span></span>

<span data-ttu-id="d64f9-152">Soubor Docker je umístěn v kořenové složce aplikace nebo služby.</span><span class="sxs-lookup"><span data-stu-id="d64f9-152">The Dockerfile is placed in the root folder of your application or service.</span></span> <span data-ttu-id="d64f9-153">Obsahuje příkazy, které informují Docker, jak nastavit a spustit aplikaci nebo službě v kontejneru.</span><span class="sxs-lookup"><span data-stu-id="d64f9-153">It contains the commands that tell Docker how to set up and run your application or service in a container.</span></span> <span data-ttu-id="d64f9-154">Můžete ručně vytvořit soubor Docker v kódu a přidejte do projektu spolu s .NET závislosti.</span><span class="sxs-lookup"><span data-stu-id="d64f9-154">You can manually create a Dockerfile in code and add it to your project along with your .NET dependencies.</span></span>

<span data-ttu-id="d64f9-155">Visual Studio a jeho nástroje pro Docker tato úloha vyžaduje pouze pomocí několika kliknutí myší.</span><span class="sxs-lookup"><span data-stu-id="d64f9-155">With Visual Studio and its tools for Docker, this task requires only a few mouse clicks.</span></span> <span data-ttu-id="d64f9-156">Když vytvoříte nový projekt ve Visual Studio 2017, je možnost s názvem **podporu povolit kontejneru (Docker)**, jak ukazuje obrázek 5-3.</span><span class="sxs-lookup"><span data-stu-id="d64f9-156">When you create a new project in Visual Studio 2017, there is an option named **Enable Container (Docker) Support**, as shown in Figure 5-3.</span></span>

![](./media/image5.png)

<span data-ttu-id="d64f9-157">**Obrázek 5-3**.</span><span class="sxs-lookup"><span data-stu-id="d64f9-157">**Figure 5-3**.</span></span> <span data-ttu-id="d64f9-158">Povolení podpory Docker při vytvoření nového projektu ve Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="d64f9-158">Enabling Docker Support when creating a new project in Visual Studio 2017</span></span>

<span data-ttu-id="d64f9-159">Můžete také povolit podporu Docker na nový nebo existující projekt tak, že kliknete pravým tlačítkem na soubor projektu v sadě Visual Studio a vyberete možnost **Docker přidat projekt podporovat**, jak je znázorněno na obrázku 5-4.</span><span class="sxs-lookup"><span data-stu-id="d64f9-159">You can also enable Docker support on a new or existing project by right-clicking your project file in Visual Studio and selecting the option **Add-Docker Project Support**, as shown in Figure 5-4.</span></span>

![](./media/image6.png)

<span data-ttu-id="d64f9-160">**Obrázek 5-4**.</span><span class="sxs-lookup"><span data-stu-id="d64f9-160">**Figure 5-4**.</span></span> <span data-ttu-id="d64f9-161">Povolení podpory Docker v existující projekt Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="d64f9-161">Enabling Docker support in an existing Visual Studio 2017 project</span></span>

<span data-ttu-id="d64f9-162">Tato akce na projektu (například webové aplikace ASP.NET nebo služby webového rozhraní API) přidá soubor Docker do projektu s požadovanou konfigurací.</span><span class="sxs-lookup"><span data-stu-id="d64f9-162">This action on a project (like an ASP.NET Web application or Web API service) adds a Dockerfile to the project with the required configuration.</span></span> <span data-ttu-id="d64f9-163">Také přidá soubor docker-compose.yml pro celé řešení.</span><span class="sxs-lookup"><span data-stu-id="d64f9-163">It also adds a docker-compose.yml file for the whole solution.</span></span> <span data-ttu-id="d64f9-164">V následujících částech se popisují jsme informace, které jde do každé z těchto souborů.</span><span class="sxs-lookup"><span data-stu-id="d64f9-164">In the following sections, we describe the information that goes into each of those files.</span></span> <span data-ttu-id="d64f9-165">Visual Studio může tento pracovní to pro vás, ale je užitečné zjistit, co do soubor Docker.</span><span class="sxs-lookup"><span data-stu-id="d64f9-165">Visual Studio can do this work for you, but it is useful to understand what goes into a Dockerfile.</span></span>

### <a name="option-a-creating-a-project-using-an-existing-official-net-docker-image"></a><span data-ttu-id="d64f9-166">Možnost A: vytvoření projektu pomocí stávající image oficiální Docker rozhraní .NET</span><span class="sxs-lookup"><span data-stu-id="d64f9-166">Option A: Creating a project using an existing official .NET Docker image</span></span>

<span data-ttu-id="d64f9-167">Obvykle sestavení vlastní image pro váš kontejner nad základní image můžete získat z oficiálního úložiště na [úložiště Docker Hub](https://hub.docker.com/) registru.</span><span class="sxs-lookup"><span data-stu-id="d64f9-167">You usually build a custom image for your container on top of a base image you can get from an official repository at the [Docker Hub](https://hub.docker.com/) registry.</span></span> <span data-ttu-id="d64f9-168">Přesněji, se stane v pozadí, když povolíte podporu Docker v sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d64f9-168">That is precisely what happens under the covers when you enable Docker support in Visual Studio.</span></span> <span data-ttu-id="d64f9-169">Váš soubor Docker bude používat stávající aspnetcore image.</span><span class="sxs-lookup"><span data-stu-id="d64f9-169">Your Dockerfile will use an existing aspnetcore image.</span></span>

<span data-ttu-id="d64f9-170">Dříve jsme vysvětlit, které imagí Dockeru a úložiště můžete použít, v závislosti na framework a rozhodli jste se verze operačního systému.</span><span class="sxs-lookup"><span data-stu-id="d64f9-170">Earlier we explained which Docker images and repos you can use, depending on the framework and OS you have chosen.</span></span> <span data-ttu-id="d64f9-171">Například pokud chcete použít ASP.NET Core (Linux nebo Windows), obrázek, který má používat je společnosti microsoft nebo aspnetcore:2.0.</span><span class="sxs-lookup"><span data-stu-id="d64f9-171">For instance, if you want to use ASP.NET Core (Linux or Windows), the image to use is microsoft/aspnetcore:2.0.</span></span> <span data-ttu-id="d64f9-172">Proto stačí zadat jaké základní image Docker budete používat pro vaše kontejneru.</span><span class="sxs-lookup"><span data-stu-id="d64f9-172">Therefore, you just need to specify what base Docker image you will use for your container.</span></span> <span data-ttu-id="d64f9-173">To uděláte tak, že přidáte od společnosti microsoft nebo aspnetcore:2.0 pro váš soubor Docker.</span><span class="sxs-lookup"><span data-stu-id="d64f9-173">You do that by adding FROM microsoft/aspnetcore:2.0 to your Dockerfile.</span></span> <span data-ttu-id="d64f9-174">Tím se automaticky provede Visual Studio, ale pokud jste aktualizaci verze, můžete aktualizovat tuto hodnotu.</span><span class="sxs-lookup"><span data-stu-id="d64f9-174">This will be automatically performed by Visual Studio, but if you were to update the version, you update this value.</span></span>

<span data-ttu-id="d64f9-175">Použití oficiální úložiště bitové kopie .NET z úložiště Docker Hub s číslem verze zajišťuje, že jsou k dispozici na všech počítačích (včetně vývoj, testování a produkci) stejné funkce jazyka.</span><span class="sxs-lookup"><span data-stu-id="d64f9-175">Using an official .NET image repository from Docker Hub with a version number ensures that the same language features are available on all machines (including development, testing, and production).</span></span>

<span data-ttu-id="d64f9-176">Následující příklad ukazuje ukázkový soubor Docker pro kontejner ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="d64f9-176">The following example shows a sample Dockerfile for an ASP.NET Core container.</span></span>

```Dockerfile
FROM microsoft/aspnetcore:2.0
  
ARG source
  
WORKDIR /app
  
EXPOSE 80
  
COPY ${source:-obj/Docker/publish} .
  
ENTRYPOINT ["dotnet", " MySingleContainerWebApp.dll "]
```

<span data-ttu-id="d64f9-177">V tomto případě kontejner je založen na verzi 2.0 oficiální ASP.NET Core Docker bitovou kopii (více architektura pro Linux a Windows).</span><span class="sxs-lookup"><span data-stu-id="d64f9-177">In this case, the container is based on version 2.0 of the official ASP.NET Core Docker image (multi-arch for Linux and Windows).</span></span> <span data-ttu-id="d64f9-178">Toto je nastavení `FROM microsoft/aspnetcore:2.0`.</span><span class="sxs-lookup"><span data-stu-id="d64f9-178">This is the setting `FROM microsoft/aspnetcore:2.0`.</span></span> <span data-ttu-id="d64f9-179">(Další podrobnosti o této základní bitovou kopii, najdete v článku [ASP.NET Core Docker Image](https://hub.docker.com/r/microsoft/aspnetcore/) stránky a [.NET Core Docker Image](https://hub.docker.com/r/microsoft/dotnet/) stránky.) V soubor Docker musíte také vyzvat Docker naslouchat na portu TCP, které budete používat v době běhu (v tomto případě port 80 a jak je nakonfigurováno nastavení ZVEŘEJNĚTE).</span><span class="sxs-lookup"><span data-stu-id="d64f9-179">(For further details about this base image, see the [ASP.NET Core Docker Image](https://hub.docker.com/r/microsoft/aspnetcore/) page and the [.NET Core Docker Image](https://hub.docker.com/r/microsoft/dotnet/) page.) In the Dockerfile, you also need to instruct Docker to listen on the TCP port you will use at runtime (in this case, port 80, as configured with the EXPOSE setting).</span></span>

<span data-ttu-id="d64f9-180">Můžete zadat další konfiguraci nastavení v soubor Docker, v závislosti na jazyk a framework, který používáte.</span><span class="sxs-lookup"><span data-stu-id="d64f9-180">You can specify additional configuration settings in the Dockerfile, depending on the language and framework you are using.</span></span> <span data-ttu-id="d64f9-181">Například ENTRYPOINT řádek s \["dotnet", "MySingleContainerWebApp.dll"\] informuje Docker ke spuštění aplikace .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d64f9-181">For instance, the ENTRYPOINT line with \["dotnet", "MySingleContainerWebApp.dll"\] tells Docker to run a .NET Core application.</span></span> <span data-ttu-id="d64f9-182">Pokud používáte sady SDK a rozhraní .NET Core příkazového řádku (dotnet rozhraní příkazového řádku) sestavení a spuštění aplikace .NET, toto nastavení by lišit.</span><span class="sxs-lookup"><span data-stu-id="d64f9-182">If you are using the SDK and the .NET Core CLI (dotnet CLI) to build and run the .NET application, this setting would be different.</span></span> <span data-ttu-id="d64f9-183">Dolní řádek je, že řádku vstupní bod a další nastavení, bude lišit v závislosti na jazyk a platformy, které zvolíte pro vaši aplikaci.</span><span class="sxs-lookup"><span data-stu-id="d64f9-183">The bottom line is that the ENTRYPOINT line and other settings will be different depending on the language and platform you choose for your application.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="d64f9-184">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="d64f9-184">Additional resources</span></span>

-   <span data-ttu-id="d64f9-185">**Vytváření Imagí Dockeru pro aplikace .NET Core**
    [*https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images*](../../../core/docker/building-net-docker-images.md)</span><span class="sxs-lookup"><span data-stu-id="d64f9-185">**Building Docker Images for .NET Core Applications**
[*https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images*](../../../core/docker/building-net-docker-images.md)</span></span>

-   <span data-ttu-id="d64f9-186">**Sestavení vlastní image**.</span><span class="sxs-lookup"><span data-stu-id="d64f9-186">**Build your own image**.</span></span> <span data-ttu-id="d64f9-187">V oficiální dokumentaci Docker.</span><span class="sxs-lookup"><span data-stu-id="d64f9-187">In the official Docker documentation.</span></span>
    [*https://docs.docker.com/engine/tutorials/dockerimages/*](https://docs.docker.com/engine/tutorials/dockerimages/)

### <a name="using-multi-arch-image-repositories"></a><span data-ttu-id="d64f9-188">Použití více architektury image úložiště</span><span class="sxs-lookup"><span data-stu-id="d64f9-188">Using multi-arch image repositories</span></span>

<span data-ttu-id="d64f9-189">Jednoho úložiště může obsahovat variant platformy, jako je například bitovou kopii systému Linux a bitové kopie systému Windows.</span><span class="sxs-lookup"><span data-stu-id="d64f9-189">A single repo can contain platform variants, such as a Linux image and a Windows image.</span></span> <span data-ttu-id="d64f9-190">Tato funkce umožňuje dodavatelům jako Microsoft (creators základní image) k vytvoření jedné úložiště tak, aby pokrývalo více platforem (který je Linux a Windows).</span><span class="sxs-lookup"><span data-stu-id="d64f9-190">This feature allows vendors like Microsoft (base image creators) to create a single repo to cover multiple platforms (that is Linux and Windows).</span></span> <span data-ttu-id="d64f9-191">Například [microsoft/dotnet](https://hub.docker.com/r/microsoft/aspnetcore/) úložiště dostupné v registru úložiště Docker Hub poskytuje podporu pro Linux a Windows Nano Server za použití stejného názvu úložišti.</span><span class="sxs-lookup"><span data-stu-id="d64f9-191">For example, the [microsoft/dotnet](https://hub.docker.com/r/microsoft/aspnetcore/) repository available in the Docker Hub registry provides support for Linux and Windows Nano Server by using the same repo name.</span></span>

<span data-ttu-id="d64f9-192">Pokud zadáte značku, cílení na platformu, která je explicitní jako v následujících případech:</span><span class="sxs-lookup"><span data-stu-id="d64f9-192">If you specify a tag, targeting a platform that is explicit like in the following cases:</span></span>

-   <span data-ttu-id="d64f9-193">**microsoft/aspnetcore:2.0.0-jessie**</span><span class="sxs-lookup"><span data-stu-id="d64f9-193">**microsoft/aspnetcore:2.0.0-jessie**</span></span>

        .NET Core 2.0 runtime-only on Linux 

-   <span data-ttu-id="d64f9-194">**microsoft/aspnetcore:2.0.0-nanoserver**</span><span class="sxs-lookup"><span data-stu-id="d64f9-194">**microsoft/aspnetcore:2.0.0-nanoserver**</span></span>

        .NET Core 2.0 runtime-only on Windows Nano Server

<span data-ttu-id="d64f9-195">Ale a to je nového od mid 2017, pokud zadáte stejný název bitové kopie, i se stejnou značkou, nových více architektury bitových kopií (například obrázek aspnetcore, která podporuje více architektura) bude používat verzi systému Linux nebo Windows v závislosti na Docker hostitelský operační systém, který nasazujete , jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="d64f9-195">But, and this is new since mid-2017, if you specify the same image name, even with the same tag, the new multi-arch images (like the aspnetcore image which supports multi-arch) will use the Linux or Windows version depending on the Docker host OS you are deploying, as shown in the following example:</span></span>

-   <span data-ttu-id="d64f9-196">**microsoft/aspnetcore:2.0**</span><span class="sxs-lookup"><span data-stu-id="d64f9-196">**microsoft/aspnetcore:2.0**</span></span>

        Multi-arch: .NET Core 2.0 runtime-only on Linux or Windows Nano Server depending on the Docker host OS

<span data-ttu-id="d64f9-197">Tímto způsobem, když načítat bitovou kopii z hostitele Windows, bude ji stáhněte Windows variant a stahování stejný název bitové kopie z hostitele platformy Linux načte Linux variant.</span><span class="sxs-lookup"><span data-stu-id="d64f9-197">This way, when you pull an image from a Windows host, it will pull the Windows variant, and pulling the same image name from a Linux host will pull the Linux variant.</span></span>

### <a name="option-b-creating-your-base-image-from-scratch"></a><span data-ttu-id="d64f9-198">Možnost B: vytvoření základní bitové kopie od začátku</span><span class="sxs-lookup"><span data-stu-id="d64f9-198">Option B: Creating your base image from scratch</span></span>

<span data-ttu-id="d64f9-199">Můžete vytvořit vlastní základní image Docker od začátku.</span><span class="sxs-lookup"><span data-stu-id="d64f9-199">You can create your own Docker base image from scratch.</span></span> <span data-ttu-id="d64f9-200">Tento scénář se nedoporučuje pro někoho, kdo je počínaje Docker, ale pokud chcete nastavit konkrétní bity základní bitové kopie, můžete tak učinit.</span><span class="sxs-lookup"><span data-stu-id="d64f9-200">This scenario is not recommended for someone who is starting with Docker, but if you want to set the specific bits of your own base image, you can do so.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="d64f9-201">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="d64f9-201">Additional resources</span></span>

-   <span data-ttu-id="d64f9-202">**Více architektury .NET Core image**.</span><span class="sxs-lookup"><span data-stu-id="d64f9-202">**Multi-arch .NET Core images**.</span></span>
<span data-ttu-id="d64f9-203">https://github.com/dotnet/announcements/issues/14</span><span class="sxs-lookup"><span data-stu-id="d64f9-203">https://github.com/dotnet/announcements/issues/14</span></span> 
-   <span data-ttu-id="d64f9-204">**Vytvořte základní image**.</span><span class="sxs-lookup"><span data-stu-id="d64f9-204">**Create a base image**.</span></span> <span data-ttu-id="d64f9-205">Oficiální dokumentaci Docker.</span><span class="sxs-lookup"><span data-stu-id="d64f9-205">Official Docker documentation.</span></span>
    [*https://docs.docker.com/engine/userguide/eng-image/baseimages/*](https://docs.docker.com/engine/userguide/eng-image/baseimages/)

![](./media/image7.png)

## <a name="step-3-create-your-custom-docker-images-and-embed-your-application-or-service-in-them"></a><span data-ttu-id="d64f9-206">Krok 3.</span><span class="sxs-lookup"><span data-stu-id="d64f9-206">Step 3.</span></span> <span data-ttu-id="d64f9-207">Vytvoření vlastních imagí Dockeru a vložit vaše aplikace nebo služba</span><span class="sxs-lookup"><span data-stu-id="d64f9-207">Create your custom Docker images and embed your application or service in them</span></span>

<span data-ttu-id="d64f9-208">U každé služby v aplikaci musíte vytvořit související bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="d64f9-208">For each service in your application, you need to create a related image.</span></span> <span data-ttu-id="d64f9-209">Pokud vaše aplikace se skládá z jedné služby nebo webovou aplikaci, bude třeba jen jedné image.</span><span class="sxs-lookup"><span data-stu-id="d64f9-209">If your application is made up of a single service or web application, you just need a single image.</span></span>

<span data-ttu-id="d64f9-210">Všimněte si, že imagí Dockeru jsou pro vás vytvořen automaticky v sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d64f9-210">Note that the Docker images are built automatically for you in Visual Studio.</span></span> <span data-ttu-id="d64f9-211">Následující kroky jsou pouze potřebné pro pracovní postup editor nebo rozhraní příkazového řádku a vysvětlení pro přehlednost o co se stane pod.</span><span class="sxs-lookup"><span data-stu-id="d64f9-211">The following steps are only needed for the editor/CLI workflow and explained for clarity about what happens underneath.</span></span>

<span data-ttu-id="d64f9-212">Jako vývojáře, musíte pro vývoj a testování místně, dokud nabízené dokončené funkci nebo změňte systému správy zdrojů (například na Githubu).</span><span class="sxs-lookup"><span data-stu-id="d64f9-212">You, as developer, need to develop and test locally until you push a completed feature or change to your source control system (for example, to GitHub).</span></span> <span data-ttu-id="d64f9-213">To znamená, že potřebujete k vytvoření imagí Dockeru a k nasazení kontejnerů do místního hostitele Docker (Windows nebo virtuálního počítače s Linuxem) a spustit, testování a ladění pro tyto místní kontejnery.</span><span class="sxs-lookup"><span data-stu-id="d64f9-213">This means that you need to create the Docker images and deploy containers to a local Docker host (Windows or Linux VM) and run, test, and debug against those local containers.</span></span>

<span data-ttu-id="d64f9-214">Pokud chcete vytvořit vlastní image ve vašem místním prostředí pomocí příkazového řádku Dockeru a váš soubor Docker, můžete použít příkaz sestavení docker, jako obrázek 5-5.</span><span class="sxs-lookup"><span data-stu-id="d64f9-214">To create a custom image in your local environment by using Docker CLI and your Dockerfile, you can use the docker build command, as in Figure 5-5.</span></span>

![](./media/image8.png)

<span data-ttu-id="d64f9-215">**Obrázek 5-5**.</span><span class="sxs-lookup"><span data-stu-id="d64f9-215">**Figure 5-5**.</span></span> <span data-ttu-id="d64f9-216">Vytvoření vlastní image Docker</span><span class="sxs-lookup"><span data-stu-id="d64f9-216">Creating a custom Docker image</span></span>

<span data-ttu-id="d64f9-217">Volitelně můžete místo přímo spouštět docker sestavení ze složky projektu, můžete nejdřív generovat nasadit složka se požadované knihovny .NET a binární soubory spuštěním dotnet publikování a pak použít příkaz docker sestavení.</span><span class="sxs-lookup"><span data-stu-id="d64f9-217">Optionally, instead of directly running docker build from the project folder, you can first generate a deployable folder with the required .NET libraries and binaries by running dotnet publish, and then use the docker build command.</span></span>

<span data-ttu-id="d64f9-218">Tím se vytvoří bitovou kopii Docker s název cesardl/netcore-webapi mikroslužbu-docker: první.</span><span class="sxs-lookup"><span data-stu-id="d64f9-218">This will create a Docker image with the name cesardl/netcore-webapi-microservice-docker:first.</span></span> <span data-ttu-id="d64f9-219">V takovém případě: nejdřív se značku představující na konkrétní verzi.</span><span class="sxs-lookup"><span data-stu-id="d64f9-219">In this case, :first is a tag representing a specific version.</span></span> <span data-ttu-id="d64f9-220">Tento krok můžete opakovat pro každý vlastní image, které potřebujete k vytvoření aplikace skládá Docker.</span><span class="sxs-lookup"><span data-stu-id="d64f9-220">You can repeat this step for each custom image you need to create for your composed Docker application.</span></span>

<span data-ttu-id="d64f9-221">Pokud existuje žádost několika kontejnerů (to znamená, že je aplikace s více kontejnerů), můžete použít také docker compose nahoru – příkaz sestavení pro sestavení všechny související bitové kopie pomocí jednoho příkazu na základě metadat v související soubory docker-compose.yml.</span><span class="sxs-lookup"><span data-stu-id="d64f9-221">When an application is made of multiple containers (that is, it is a multi-container application), you can also use the docker-compose up --build command to build all the related images with a single command by using the metadata exposed in the related docker-compose.yml files.</span></span>

<span data-ttu-id="d64f9-222">Image můžete najít existující v místním úložišti pomocí docker příkaz bitové kopie, jak je znázorněno v obrázku 5 a 6.</span><span class="sxs-lookup"><span data-stu-id="d64f9-222">You can find the existing images in your local repository by using the docker images command, as shown in Figure 5-6.</span></span>

![](./media/image9.png)

<span data-ttu-id="d64f9-223">**Obrázek 5 a 6.**</span><span class="sxs-lookup"><span data-stu-id="d64f9-223">**Figure 5-6.**</span></span> <span data-ttu-id="d64f9-224">Zobrazení existujících bitových kopií, pomocí příkazu docker bitové kopie</span><span class="sxs-lookup"><span data-stu-id="d64f9-224">Viewing existing images using the docker images command</span></span>

### <a name="creating-docker-images-with-visual-studio"></a><span data-ttu-id="d64f9-225">Vytvoření imagí Dockeru pomocí sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="d64f9-225">Creating Docker images with Visual Studio</span></span>

<span data-ttu-id="d64f9-226">Pokud používáte Visual Studio k vytvoření projektu s podporou Docker, nevytvoříte explicitně bitovou kopii.</span><span class="sxs-lookup"><span data-stu-id="d64f9-226">When you are using Visual Studio to create a project with Docker support, you do not explicitly create an image.</span></span> <span data-ttu-id="d64f9-227">Místo toho se pro vás vytvoří bitovou kopii, při stisknutím klávesy F5 a spusťte dockerized aplikace nebo služby.</span><span class="sxs-lookup"><span data-stu-id="d64f9-227">Instead, the image is created for you when you press F5 and run the dockerized application or service.</span></span> <span data-ttu-id="d64f9-228">Tento krok je automatické v sadě Visual Studio a nebude se zobrazovat dojít, ale je důležité vědět, co se děje v dole.</span><span class="sxs-lookup"><span data-stu-id="d64f9-228">This step is automatic in Visual Studio, and you will not see it happen, but it is important that you know what is going on underneath.</span></span>

![](./media/image10.png)

## <a name="step-4-define-your-services-in-docker-composeyml-when-building-a-multi-container-docker-application"></a><span data-ttu-id="d64f9-229">Krok 4.</span><span class="sxs-lookup"><span data-stu-id="d64f9-229">Step 4.</span></span> <span data-ttu-id="d64f9-230">Definování vašim službám v docker-compose.yml při vytvoření aplikace s více kontejner Docker</span><span class="sxs-lookup"><span data-stu-id="d64f9-230">Define your services in docker-compose.yml when building a multi-container Docker application</span></span>

<span data-ttu-id="d64f9-231">[Docker-compose.yml](https://docs.docker.com/compose/compose-file/) souboru umožňuje definovat sadu související služby pro nasazení jako složený aplikace pomocí příkazů pro nasazení.</span><span class="sxs-lookup"><span data-stu-id="d64f9-231">The [docker-compose.yml](https://docs.docker.com/compose/compose-file/) file lets you define a set of related services to be deployed as a composed application with deployment commands.</span></span>

<span data-ttu-id="d64f9-232">Pokud chcete použít soubor docker-compose.yml, budete muset vytvořit soubor ve vaší hlavní nebo kořenové složky řešení, s obsahem, které jsou podobné jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="d64f9-232">To use a docker-compose.yml file, you need to create the file in your main or root solution folder, with content similar to that in the following example:</span></span>

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

<span data-ttu-id="d64f9-233">Všimněte si, že tento soubor docker-compose.yml je zjednodušená sloučené verze.</span><span class="sxs-lookup"><span data-stu-id="d64f9-233">Note that this docker-compose.yml file is a simplified and merged version.</span></span> <span data-ttu-id="d64f9-234">Obsahuje statický konfigurační data pro každý kontejner (jako je třeba název vlastní image), která se vztahuje vždy plus informace o konfiguraci, které může závisí na prostředí pro nasazení, jako je připojovací řetězec.</span><span class="sxs-lookup"><span data-stu-id="d64f9-234">It contains static configuration data for each container (like the name of the custom image), which always applies, plus configuration information that might depend on the deployment environment, like the connection string.</span></span> <span data-ttu-id="d64f9-235">V pozdějších částech se dozvíte, jak můžete rozdělit konfigurace docker-compose.yml do několika docker compose soubory a přepisujících hodnot v závislosti na typu prostředí a provádění (ladění nebo verze).</span><span class="sxs-lookup"><span data-stu-id="d64f9-235">In later sections, you will learn how you can split the docker-compose.yml configuration into multiple docker-compose files and override values depending on the environment and execution type (debug or release).</span></span>

<span data-ttu-id="d64f9-236">Příklad soubor docker-compose.yml definuje pět služby: službu webmvc (webová aplikace), dva mikroslužeb (catalog.api a ordering.api) a jeden datový zdroj kontejneru sql.data, založené na systému SQL Server pro Linux spuštěný jako kontejner.</span><span class="sxs-lookup"><span data-stu-id="d64f9-236">The docker-compose.yml file example defines five services: the webmvc service (a web application), two microservices (catalog.api and ordering.api), and one data source container, sql.data, based on SQL Server for Linux running as a container.</span></span> <span data-ttu-id="d64f9-237">Každá služba je nasazený jako kontejner, a bitovou kopii Docker se vyžaduje pro každou.</span><span class="sxs-lookup"><span data-stu-id="d64f9-237">Each service is deployed as a container, so a Docker image is required for each.</span></span>

<span data-ttu-id="d64f9-238">Soubor docker-compose.yml určuje pouze kontejnery, které jsou používány, ale jejich jednotlivě konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="d64f9-238">The docker-compose.yml file specifies not only what containers are being used, but how they are individually configured.</span></span> <span data-ttu-id="d64f9-239">Například webmvc kontejneru definice v souboru .yml:</span><span class="sxs-lookup"><span data-stu-id="d64f9-239">For instance, the webmvc container definition in the .yml file:</span></span>

-   <span data-ttu-id="d64f9-240">Pomocí předdefinovaných eshop / webové: nejnovější bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="d64f9-240">Uses a pre-built eshop/web:latest image.</span></span> <span data-ttu-id="d64f9-241">Však můžete také nakonfigurovat obrázek, který má být sestaven jako součást docker compose spuštění s další konfigurací podle sestavení: v souboru docker-compose.</span><span class="sxs-lookup"><span data-stu-id="d64f9-241">However, you could also configure the image to be built as part of the docker-compose execution with an additional configuration based on a build: section in the docker-compose file.</span></span>

-   <span data-ttu-id="d64f9-242">Inicializuje dvou proměnných prostředí (adresa URL katalogu a OrderingUrl).</span><span class="sxs-lookup"><span data-stu-id="d64f9-242">Initializes two environment variables (CatalogUrl and OrderingUrl).</span></span>

-   <span data-ttu-id="d64f9-243">Předává zveřejněné port 80 kontejneru na externím portu 80 na hostitelském počítači.</span><span class="sxs-lookup"><span data-stu-id="d64f9-243">Forwards the exposed port 80 on the container to the external port 80 on the host machine.</span></span>

-   <span data-ttu-id="d64f9-244">Odkazy na katalogu a řazení služby s webovou aplikaci závisí\_na nastavení.</span><span class="sxs-lookup"><span data-stu-id="d64f9-244">Links the web app to the catalog and ordering service with the depends\_on setting.</span></span> <span data-ttu-id="d64f9-245">To způsobí, že služba Počkejte, dokud jsou tyto služby spuštěny.</span><span class="sxs-lookup"><span data-stu-id="d64f9-245">This causes the service to wait until those services are started.</span></span>

<span data-ttu-id="d64f9-246">Soubor docker-compose.yml v další části jsme se pokroku při nabídneme postupy pro implementaci mikroslužeb a více kontejneru aplikace.</span><span class="sxs-lookup"><span data-stu-id="d64f9-246">We will revisit the docker-compose.yml file in a later section when we cover how to implement microservices and multi-container apps.</span></span>

### <a name="working-with-docker-composeyml-in-visual-studio-2017"></a><span data-ttu-id="d64f9-247">Práce s docker-compose.yml v Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="d64f9-247">Working with docker-compose.yml in Visual Studio 2017</span></span>

<span data-ttu-id="d64f9-248">Když přidáte podporu Docker řešení do projektu služby v řešení sady Visual Studio, jak je znázorněno na obrázku 5 – 7, Visual Studio přidá soubor Docker do projektu a přidá oddíl služby (projekt) ve vašem řešení se soubory docker-compose.yml.</span><span class="sxs-lookup"><span data-stu-id="d64f9-248">When you add Docker solution support to a service project in a Visual Studio solution, as shown in Figure 5-7, Visual Studio adds a Dockerfile to your project, and it adds a service section (project) in your solution with the docker-compose.yml files.</span></span> <span data-ttu-id="d64f9-249">Je snadný způsob, jak spustit sestavování řešení více kontejneru.</span><span class="sxs-lookup"><span data-stu-id="d64f9-249">It is an easy way to start composing your multiple-container solution.</span></span> <span data-ttu-id="d64f9-250">Můžete otevřít soubory docker-compose.yml a provede jejich aktualizaci s další funkce.</span><span class="sxs-lookup"><span data-stu-id="d64f9-250">You can then open the docker-compose.yml files and update them with additional features.</span></span>

![](./media/image6.png)

<span data-ttu-id="d64f9-251">**Obrázek 5 – 7**.</span><span class="sxs-lookup"><span data-stu-id="d64f9-251">**Figure 5-7**.</span></span> <span data-ttu-id="d64f9-252">Přidání podpory Docker v aplikaci Visual Studio 2017 kliknutím pravým tlačítkem na projekt ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="d64f9-252">Adding Docker support in Visual Studio 2017 by right-clicking an ASP.NET Core project</span></span>

<span data-ttu-id="d64f9-253">Přidání podpory Docker v sadě Visual Studio pouze přidá soubor Docker do projektu, ale přidá informace o konfiguraci několik globální docker-compose.yml souborů, které jsou nastaveny na úrovni řešení.</span><span class="sxs-lookup"><span data-stu-id="d64f9-253">Adding Docker support in Visual Studio not only adds the Dockerfile to your project, but adds the configuration information to several global docker-compose.yml files that are set at the solution level.</span></span>

<span data-ttu-id="d64f9-254">Po přidání podpory Docker do řešení v sadě Visual Studio, zobrazí se také nový uzel (v souboru projektu docker compose.dcproj) v Průzkumníku řešení, která obsahuje soubory přidané docker-compose.yml, jak je znázorněno v obrázku 5 až 8.</span><span class="sxs-lookup"><span data-stu-id="d64f9-254">After you add Docker support to your solution in Visual Studio, you will also see a new node (in the docker-compose.dcproj project file) in Solution Explorer that contains the added docker-compose.yml files, as shown in Figure 5-8.</span></span>

![](./media/image11.PNG)

<span data-ttu-id="d64f9-255">**Obrázek 5 až 8**.</span><span class="sxs-lookup"><span data-stu-id="d64f9-255">**Figure 5-8**.</span></span> <span data-ttu-id="d64f9-256">**Docker compose** uzel stromu přidán do Průzkumníka řešení 2017 Visual Studio</span><span class="sxs-lookup"><span data-stu-id="d64f9-256">The **docker-compose** tree node added in Visual Studio 2017 Solution Explorer</span></span>

<span data-ttu-id="d64f9-257">Můžete nasadit aplikace s více kontejnerů pomocí docker-compose.yml jednoho souboru pomocí docker compose až příkaz.</span><span class="sxs-lookup"><span data-stu-id="d64f9-257">You could deploy a multi-container application with a single docker-compose.yml file by using the docker-compose up command.</span></span> <span data-ttu-id="d64f9-258">Však sady Visual Studio přidá skupiny, můžete přepsat hodnoty v závislosti na prostředí (vývoj a produkční) a provádění typu (vydání a ladění).</span><span class="sxs-lookup"><span data-stu-id="d64f9-258">However, Visual Studio adds a group of them so you can override values depending on the environment (development versus production) and execution type (release versus debug).</span></span> <span data-ttu-id="d64f9-259">Tato funkce bude vysvětlené v pozdějších částech.</span><span class="sxs-lookup"><span data-stu-id="d64f9-259">This capability will be explained in later sections.</span></span>

![](./media/image12.png)

## <a name="step-5-build-and-run-your-docker-application"></a><span data-ttu-id="d64f9-260">Krok 5.</span><span class="sxs-lookup"><span data-stu-id="d64f9-260">Step 5.</span></span> <span data-ttu-id="d64f9-261">Sestavení a spuštění aplikace Docker</span><span class="sxs-lookup"><span data-stu-id="d64f9-261">Build and run your Docker application</span></span>

<span data-ttu-id="d64f9-262">Pokud vaše aplikace má pouze jediný kontejner, můžete ho spustit publikovat na vašem hostiteli Docker (virtuálního počítače nebo fyzického serveru).</span><span class="sxs-lookup"><span data-stu-id="d64f9-262">If your application only has a single container, you can run it by deploying it to your Docker host (VM or physical server).</span></span> <span data-ttu-id="d64f9-263">Ale pokud vaše aplikace obsahuje více služeb, můžete nasadit jako složený aplikace, buď pomocí jednoduchého příkazu rozhraní příkazového řádku (docker tvoří nahoru), nebo pomocí sady Visual Studio, které budou používat tento příkaz v pozadí.</span><span class="sxs-lookup"><span data-stu-id="d64f9-263">However, if your application contains multiple services, you can deploy it as a composed application, either using a single CLI command (docker-compose up), or with Visual Studio, which will use that command under the covers.</span></span> <span data-ttu-id="d64f9-264">Podívejme se na různé možnosti.</span><span class="sxs-lookup"><span data-stu-id="d64f9-264">Let’s look at the different options.</span></span>

### <a name="option-a-running-a-single-container-with-docker-cli"></a><span data-ttu-id="d64f9-265">Možnost A: spuštěna pomocí příkazového řádku Dockeru kontejner jedním</span><span class="sxs-lookup"><span data-stu-id="d64f9-265">Option A: Running a single-container with Docker CLI</span></span>

<span data-ttu-id="d64f9-266">Můžete spustit kontejner Docker pomocí docker, spusťte příkaz, stejně jako obrázek 5 – 9:</span><span class="sxs-lookup"><span data-stu-id="d64f9-266">You can run a Docker container using the docker run command, as in Figure 5-9:</span></span>

```console
  docker run -t -d -p 80:5000 cesardl/netcore-webapi-microservice-docker:first
```

![](./media/image13.png)

<span data-ttu-id="d64f9-267">**Obrázek 5-9**.</span><span class="sxs-lookup"><span data-stu-id="d64f9-267">**Figure 5-9**.</span></span> <span data-ttu-id="d64f9-268">Spuštění kontejner Docker pomocí docker, spusťte příkaz</span><span class="sxs-lookup"><span data-stu-id="d64f9-268">Running a Docker container using the docker run command</span></span>

<span data-ttu-id="d64f9-269">V takovém případě příkaz váže interní port 5000 kontejneru na port 80 hostitelský počítač.</span><span class="sxs-lookup"><span data-stu-id="d64f9-269">In this case, the command binds the internal port 5000 of the container to port 80 of the host machine.</span></span> <span data-ttu-id="d64f9-270">To znamená, že je Hostitel naslouchá na portu 80 a předávání na port 5000 na kontejneru.</span><span class="sxs-lookup"><span data-stu-id="d64f9-270">This means that the host is listening on port 80 and forwarding to port 5000 on the container.</span></span>

### <a name="option-b-running-a-multi-container-application"></a><span data-ttu-id="d64f9-271">Možnost B: spuštěna aplikace typu kontejner s více</span><span class="sxs-lookup"><span data-stu-id="d64f9-271">Option B: Running a multi-container application</span></span>

<span data-ttu-id="d64f9-272">Ve většině scénářů organizace Docker aplikace se skládá z více služeb, což znamená, že budete muset spustit aplikaci více kontejneru, jak je znázorněno v obrázku 5-10.</span><span class="sxs-lookup"><span data-stu-id="d64f9-272">In most enterprise scenarios, a Docker application will be composed of multiple services, which means you need to run a multi-container application, as shown in Figure 5-10.</span></span>

![](./media/image14.png)

<span data-ttu-id="d64f9-273">**Obrázek 5-10**.</span><span class="sxs-lookup"><span data-stu-id="d64f9-273">**Figure 5-10**.</span></span> <span data-ttu-id="d64f9-274">Virtuální počítač s kontejnery Docker nasazení</span><span class="sxs-lookup"><span data-stu-id="d64f9-274">VM with Docker containers deployed</span></span>

#### <a name="running-a-multi-container-application-with-the-docker-cli"></a><span data-ttu-id="d64f9-275">Spuštění aplikace s více kontejnerů pomocí rozhraní příkazového řádku Dockeru</span><span class="sxs-lookup"><span data-stu-id="d64f9-275">Running a multi-container application with the Docker CLI</span></span>

<span data-ttu-id="d64f9-276">Ke spuštění aplikace s více kontejnerů pomocí rozhraní příkazového řádku Dockeru, můžete spustit docker-tvoří až příkaz.</span><span class="sxs-lookup"><span data-stu-id="d64f9-276">To run a multi-container application with the Docker CLI, you can run the docker-compose up command.</span></span> <span data-ttu-id="d64f9-277">Tento soubor docker-compose.yml používá příkaz, abyste měli na úrovni řešení pro nasazení aplikace s více kontejnerů.</span><span class="sxs-lookup"><span data-stu-id="d64f9-277">This command uses the docker-compose.yml file that you have at the solution level to deploy a multi-container application.</span></span> <span data-ttu-id="d64f9-278">Obrázek 5-11 zobrazuje výsledky, když spustíte příkaz z adresáře hlavní projekt, který obsahuje soubor docker-compose.yml.</span><span class="sxs-lookup"><span data-stu-id="d64f9-278">Figure 5-11 shows the results when running the command from your main project directory, which contains the docker-compose.yml file.</span></span>

![](./media/image15.png)

<span data-ttu-id="d64f9-279">**Obrázek 5-11**.</span><span class="sxs-lookup"><span data-stu-id="d64f9-279">**Figure 5-11**.</span></span> <span data-ttu-id="d64f9-280">Příklad výsledků při spuštění docker compose až příkaz</span><span class="sxs-lookup"><span data-stu-id="d64f9-280">Example results when running the docker-compose up command</span></span>

<span data-ttu-id="d64f9-281">Po docker-tvoří spuštění příkazu, aplikace a související kontejnerů jsou nasazeny do Docker hostiteli, jak je ukázáno v reprezentace virtuálních počítačů v obrázku 5-10.</span><span class="sxs-lookup"><span data-stu-id="d64f9-281">After the docker-compose up command runs, the application and its related containers are deployed into your Docker host, as illustrated in the VM representation in Figure 5-10.</span></span>

#### <a name="running-and-debugging-a-multi-container-application-with-visual-studio"></a><span data-ttu-id="d64f9-282">Spuštění a ladění aplikace s více kontejnerů pomocí sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="d64f9-282">Running and debugging a multi-container application with Visual Studio</span></span> 

<span data-ttu-id="d64f9-283">Spuštěna aplikace typu kontejner s více pomocí Visual Studio 2017 nelze získat jednodušší.</span><span class="sxs-lookup"><span data-stu-id="d64f9-283">Running a multi-container application using Visual Studio 2017 cannot get simpler.</span></span> <span data-ttu-id="d64f9-284">Nelze spustit jenom aplikace s více kontejnerů, ale budete moci nastavení zarážek regulární ladění všechny kontejnery přímo ze sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d64f9-284">You can not only run the multi-container application, but you are able to debug all its containers directly from Visual Studio by setting regular breakpoints.</span></span>

<span data-ttu-id="d64f9-285">Jak je uvedeno před pokaždé, když přidáte podporu řešení Docker na projekt v rámci řešení, tento projekt je nakonfigurovaný v souboru globální docker-compose.yml (řešení úrovni), který umožňuje spustit nebo ladění celé řešení najednou.</span><span class="sxs-lookup"><span data-stu-id="d64f9-285">As mentioned before, each time you add Docker solution support to a project within a solution, that project is configured in the global (solution-level) docker-compose.yml file, which lets you run or debug the whole solution at once.</span></span> <span data-ttu-id="d64f9-286">Visual Studio spustit jeden kontejner pro každý projekt, který má povolenou podporou řešení Docker a provedení všech kroků interní pro vás (dotnet publikovat, sestavení docker atd.).</span><span class="sxs-lookup"><span data-stu-id="d64f9-286">Visual Studio will start one container for each project that has Docker solution support enabled, and perform all the internal steps for you (dotnet publish, docker build, etc.).</span></span>

<span data-ttu-id="d64f9-287">Je nutné zdůraznit, jak ukazuje obrázek 5-12, v aplikaci Visual Studio 2017 se další **Docker** příkazu pro reakce na stisknutí klávesy F5.</span><span class="sxs-lookup"><span data-stu-id="d64f9-287">The important point here is that, as shown in Figure 5-12, in Visual Studio 2017 there is an additional **Docker** command for the F5 key action.</span></span> <span data-ttu-id="d64f9-288">Tato možnost umožňuje spustit nebo ladění aplikace s více kontejneru spuštěním všechny kontejnery, které jsou definovány v souborech docker-compose.yml na úrovni řešení.</span><span class="sxs-lookup"><span data-stu-id="d64f9-288">This option lets you run or debug a multi-container application by running all the containers that are defined in the docker-compose.yml files at the solution level.</span></span> <span data-ttu-id="d64f9-289">Možnost ladění řešení více kontejneru znamená, že můžete nastavit zarážky několik, každé zarážky v na jiný projekt (kontejner) a při ladění ze sady Visual Studio přestanete na zarážkách definované v různých projektů a systémem jiných kontejnerů.</span><span class="sxs-lookup"><span data-stu-id="d64f9-289">The ability to debug multiple-container solutions means that you can set several breakpoints, each breakpoint in a different project (container), and while debugging from Visual Studio you will stop at breakpoints defined in different projects and running on different containers.</span></span>

![](./media/image16.png)

<span data-ttu-id="d64f9-290">**Obrázek 5-12**.</span><span class="sxs-lookup"><span data-stu-id="d64f9-290">**Figure 5-12**.</span></span> <span data-ttu-id="d64f9-291">Spouštění aplikací využívajících službu kontejneru v Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="d64f9-291">Running multi-container apps in Visual Studio 2017</span></span>

### <a name="additional-resources"></a><span data-ttu-id="d64f9-292">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="d64f9-292">Additional resources</span></span>

-   <span data-ttu-id="d64f9-293">**Nasaďte kontejner ASP.NET vzdáleného hostitele Docker**
    [*https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker*](https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker)</span><span class="sxs-lookup"><span data-stu-id="d64f9-293">**Deploy an ASP.NET container to a remote Docker host**
[*https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker*](https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker)</span></span>

### <a name="a-note-about-testing-and-deploying-with-orchestrators"></a><span data-ttu-id="d64f9-294">Poznámka o testování a nasazení s orchestrators</span><span class="sxs-lookup"><span data-stu-id="d64f9-294">A note about testing and deploying with orchestrators</span></span>

<span data-ttu-id="d64f9-295">Docker compose nahoru a docker spustit příkazy (nebo spuštění a ladění kontejnerů v sadě Visual Studio) jsou pro testování kontejnery ve vašem vývojovém prostředí.</span><span class="sxs-lookup"><span data-stu-id="d64f9-295">The docker-compose up and docker run commands (or running and debugging the containers in Visual Studio) are adequate for testing containers in your development environment.</span></span> <span data-ttu-id="d64f9-296">Ale pokud cílíte na Docker clustery a orchestrators jako Docker Swarm, Mesosphere DC/OS nebo Kubernetes byste neměli používat tento přístup.</span><span class="sxs-lookup"><span data-stu-id="d64f9-296">But you should not use this approach if you are targeting Docker clusters and orchestrators like Docker Swarm, Mesosphere DC/OS, or Kubernetes.</span></span> <span data-ttu-id="d64f9-297">Pokud používáte cluster jako [Docker Swarm režimu](https://docs.docker.com/engine/swarm/) (k dispozici v CE Docker pro systém Windows a Mac od verze 1.12), musíte nasadit a otestovat s další příkazy, jako je [vytvoření služby docker](https://docs.docker.com/engine/reference/commandline/service_create/) pro jeden služby.</span><span class="sxs-lookup"><span data-stu-id="d64f9-297">If you are using a cluster like [Docker Swarm mode](https://docs.docker.com/engine/swarm/) (available in Docker CE for Windows and Mac since version 1.12), you need to deploy and test with additional commands like [docker service create](https://docs.docker.com/engine/reference/commandline/service_create/) for single services.</span></span> <span data-ttu-id="d64f9-298">Pokud nasazujete aplikace skládá z několika kontejnerů, můžete použít [docker compose sady](https://docs.docker.com/compose/reference/bundle/) a [docker nasazení myBundleFile](https://docs.docker.com/engine/reference/commandline/deploy/) se nasazení skládá aplikace jako *zásobníku*.</span><span class="sxs-lookup"><span data-stu-id="d64f9-298">If you are deploying an application composed of several containers, you use [docker compose bundle](https://docs.docker.com/compose/reference/bundle/) and [docker deploy myBundleFile](https://docs.docker.com/engine/reference/commandline/deploy/) to deploy the composed application as a *stack*.</span></span> <span data-ttu-id="d64f9-299">Další informace naleznete v příspěvku blogu [představení experimentální distribuované aplikace sady](https://blog.docker.com/2016/06/docker-app-bundle/) v dokumentaci k nástroji Docker.</span><span class="sxs-lookup"><span data-stu-id="d64f9-299">For more information, see the blog post [Introducing Experimental Distributed Application Bundles](https://blog.docker.com/2016/06/docker-app-bundle/) in the Docker documentation.</span></span> <span data-ttu-id="d64f9-300">na webu Docker.</span><span class="sxs-lookup"><span data-stu-id="d64f9-300">on the Docker site.</span></span>

<span data-ttu-id="d64f9-301">Pro [DC/OS](https://mesosphere.com/blog/2015/09/02/dcos-cli-command-line-tool-datacenter/) a [Kubernetes](http://kubernetes.io/docs/user-guide/deployments/) použijete jiné nasazení příkazy a skripty také.</span><span class="sxs-lookup"><span data-stu-id="d64f9-301">For [DC/OS](https://mesosphere.com/blog/2015/09/02/dcos-cli-command-line-tool-datacenter/) and [Kubernetes](http://kubernetes.io/docs/user-guide/deployments/) you would use different deployment commands and scripts as well.</span></span>

![](./media/image17.png)

## <a name="step-6-test-your-docker-application-using-your-local-docker-host"></a><span data-ttu-id="d64f9-302">Krok 6.</span><span class="sxs-lookup"><span data-stu-id="d64f9-302">Step 6.</span></span> <span data-ttu-id="d64f9-303">Testování aplikace Docker pomocí vašeho místního hostitele Docker</span><span class="sxs-lookup"><span data-stu-id="d64f9-303">Test your Docker application using your local Docker host</span></span>

<span data-ttu-id="d64f9-304">Tento krok se bude lišit v závislosti na tom, co je to vaše aplikace.</span><span class="sxs-lookup"><span data-stu-id="d64f9-304">This step will vary depending on what your application is doing.</span></span> <span data-ttu-id="d64f9-305">Ve jednoduché rozhraní .NET Core webové aplikaci, která je nasazena jako jediný kontejner nebo služby mají přístup ke službě otevřením prohlížeče na hostiteli Docker a přejdete na tuto lokalitu, jak je znázorněno v obrázek 5 – 13.</span><span class="sxs-lookup"><span data-stu-id="d64f9-305">In a simple .NET Core Web application that is deployed as a single container or service, you can access the service by opening a browser on the Docker host and navigating to that site as shown in Figure 5-13.</span></span> <span data-ttu-id="d64f9-306">(Pokud se konfigurace v soubor Docker mapuje kontejneru na port hostitele, který je jakoukoli jinou hodnotu než 80, zahrnují port hostitele v adrese URL.)</span><span class="sxs-lookup"><span data-stu-id="d64f9-306">(If the configuration in the Dockerfile maps the container to a port on the host that is anything other than 80, include the host port in the URL.)</span></span>

![](./media/image18.png)

<span data-ttu-id="d64f9-307">**Obrázek 5 – 13**.</span><span class="sxs-lookup"><span data-stu-id="d64f9-307">**Figure 5-13**.</span></span> <span data-ttu-id="d64f9-308">Příklad testování Docker aplikace místně pomocí místního hostitele</span><span class="sxs-lookup"><span data-stu-id="d64f9-308">Example of testing your Docker application locally using localhost</span></span>

<span data-ttu-id="d64f9-309">Pokud localhost neukazuje na Docker hostitele IP (ve výchozím nastavení se při použití Docker CE by měl), přejděte na služby, použijte IP adresu vašeho počítače síťové karty.</span><span class="sxs-lookup"><span data-stu-id="d64f9-309">If localhost is not pointing to the Docker host IP (by default, when using Docker CE, it should), to navigate to your service, use the IP address of your machine’s network card.</span></span>

<span data-ttu-id="d64f9-310">Všimněte si, že tuto adresu URL v prohlížeči používá port 80 například konkrétním kontejneru, který je právě popsané.</span><span class="sxs-lookup"><span data-stu-id="d64f9-310">Note that this URL in the browser uses port 80 for the particular container example being discussed.</span></span> <span data-ttu-id="d64f9-311">Však interně žádosti se protože přesměrováni na port 5000, který byl, jak byl zaveden pomocí docker, spusťte příkaz, jak je popsáno v předchozím kroku.</span><span class="sxs-lookup"><span data-stu-id="d64f9-311">However, internally the requests are being redirected to port 5000, because that was how it was deployed with the docker run command, as explained in a previous step.</span></span>

<span data-ttu-id="d64f9-312">Také můžete testovat aplikaci pomocí curl z terminálu, jak je znázorněno v obrázku 5-14.</span><span class="sxs-lookup"><span data-stu-id="d64f9-312">You can also test the application using curl from the terminal, as shown in Figure 5-14.</span></span> <span data-ttu-id="d64f9-313">V rámci Docker instalace v systému Windows je výchozí Docker hostitele IP vždy 10.0.75.1 kromě skutečná adresa IP počítače.</span><span class="sxs-lookup"><span data-stu-id="d64f9-313">In a Docker installation on Windows, the default Docker Host IP is always 10.0.75.1 in addition to your machine’s actual IP address.</span></span>

![](./media/image19.png)

<span data-ttu-id="d64f9-314">**Obrázek 5-14**.</span><span class="sxs-lookup"><span data-stu-id="d64f9-314">**Figure 5-14**.</span></span> <span data-ttu-id="d64f9-315">Příklad testování Docker aplikace místně pomocí curl</span><span class="sxs-lookup"><span data-stu-id="d64f9-315">Example of testing your Docker application locally using curl</span></span>

### <a name="testing-and-debugging-containers-with-visual-studio-2017"></a><span data-ttu-id="d64f9-316">Testování a ladění kontejnery s Visual Studio 2017</span><span class="sxs-lookup"><span data-stu-id="d64f9-316">Testing and debugging containers with Visual Studio 2017</span></span>

<span data-ttu-id="d64f9-317">Při spuštění a ladění kontejnery s Visual Studio 2017, můžete ladit aplikace .NET mnohem stejným způsobem jako při spuštění bez kontejnery.</span><span class="sxs-lookup"><span data-stu-id="d64f9-317">When running and debugging the containers with Visual Studio 2017, you can debug the .NET application in much the same way as you would when running without containers.</span></span>

### <a name="testing-and-debugging-without-visual-studio"></a><span data-ttu-id="d64f9-318">Testování a ladění bez sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="d64f9-318">Testing and debugging without Visual Studio</span></span>

<span data-ttu-id="d64f9-319">Pokud vyvíjíte pomocí editoru/CLI přístup, je obtížnější ladění kontejnerů a budete chtít ladění pomocí generování trasování.</span><span class="sxs-lookup"><span data-stu-id="d64f9-319">If you are developing using the editor/CLI approach, debugging containers is more difficult and you will want to debug by generating traces.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="d64f9-320">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="d64f9-320">Additional resources</span></span>

-   <span data-ttu-id="d64f9-321">**Ladění aplikací v místním kontejner Docker**
    [*https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh*](https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh)</span><span class="sxs-lookup"><span data-stu-id="d64f9-321">**Debugging apps in a local Docker container**
[*https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh*](https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh)</span></span>

-   <span data-ttu-id="d64f9-322">**Steve Lasker. Vytvoření, ladění, nasazení aplikací ASP.NET Core pomocí Docker.**</span><span class="sxs-lookup"><span data-stu-id="d64f9-322">**Steve Lasker. Build, Debug, Deploy ASP.NET Core Apps with Docker.**</span></span> <span data-ttu-id="d64f9-323">Video.</span><span class="sxs-lookup"><span data-stu-id="d64f9-323">Video.</span></span>
    [*https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T115*](https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T115)

## <a name="simplified-workflow-when-developing-containers-with-visual-studio"></a><span data-ttu-id="d64f9-324">Zjednodušená pracovního postupu při vývoji kontejnery pomocí sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="d64f9-324">Simplified workflow when developing containers with Visual Studio</span></span>

<span data-ttu-id="d64f9-325">Efektivně pracovní postup, když pomocí sady Visual Studio je mnohem jednodušší než když použijete metodu editor nebo rozhraní příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="d64f9-325">Effectively, the workflow when using Visual Studio is a lot simpler than if you use the editor/CLI approach.</span></span> <span data-ttu-id="d64f9-326">Většina kroky podle Docker související s soubor Docker a docker-compose.yml soubory jsou skrytý nebo zjednodušené Visual Studio, jak je znázorněno v obrázku 5-15.</span><span class="sxs-lookup"><span data-stu-id="d64f9-326">Most of the steps required by Docker related to the Dockerfile and docker-compose.yml files are hidden or simplified by Visual Studio, as shown in Figure 5-15.</span></span>

![](./media/image20.png)

<span data-ttu-id="d64f9-327">**Obrázek 5-15**.</span><span class="sxs-lookup"><span data-stu-id="d64f9-327">**Figure 5-15**.</span></span> <span data-ttu-id="d64f9-328">Zjednodušené pracovní postup, když vývoj pomocí sady Visual Studio</span><span class="sxs-lookup"><span data-stu-id="d64f9-328">Simplified workflow when developing with Visual Studio</span></span>

<span data-ttu-id="d64f9-329">Kromě toho budete muset provést krok 2 (Přidání podpory Docker do vašich projektů) pouze jednou.</span><span class="sxs-lookup"><span data-stu-id="d64f9-329">In addition, you need to perform step 2 (adding Docker support to your projects) just once.</span></span> <span data-ttu-id="d64f9-330">Proto je podobná obvyklé vývojářských úloh pracovního postupu, při použití rozhraní .NET pro další vývoj.</span><span class="sxs-lookup"><span data-stu-id="d64f9-330">Therefore, the workflow is similar to your usual development tasks when using .NET for any other development.</span></span> <span data-ttu-id="d64f9-331">Je třeba vědět, co se děje skrytě (proces vytváření bitové kopie, jaké základní bitové kopie, kterou používáte, nasazení kontejnerů, atd.) a v některých případech, že budete také muset upravit soubor soubor Docker nebo docker-compose.yml k přizpůsobení chování.</span><span class="sxs-lookup"><span data-stu-id="d64f9-331">You need to know what is going on under the covers (the image build process, what base images you are using, deployment of containers, etc.) and sometimes you will also need to edit the Dockerfile or docker-compose.yml file to customize behaviors.</span></span> <span data-ttu-id="d64f9-332">Ale většinu práce je výrazně jednodušší pomocí sady Visual Studio, což je mnohem vyšší produktivitu.</span><span class="sxs-lookup"><span data-stu-id="d64f9-332">But most of the work is greatly simplified by using Visual Studio, making you a lot more productive.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="d64f9-333">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="d64f9-333">Additional resources</span></span>

-   <span data-ttu-id="d64f9-334">**Steve Lasker. .NET – vývoj docker s Visual Studio 2017**
    [*https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T111*](https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T111)</span><span class="sxs-lookup"><span data-stu-id="d64f9-334">**Steve Lasker. .NET Docker Development with Visual Studio 2017**
[*https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T111*](https://channel9.msdn.com/Events/Visual-Studio/Visual-Studio-2017-Launch/T111)</span></span>

-   <span data-ttu-id="d64f9-335">**Jeffrey T. Fritz. Uveďte základní aplikace .NET v kontejneru s nové nástroje Docker pro sadu Visual Studio**
    [*https://blogs.msdn.microsoft.com/webdev/2016/11/16/new-docker-tools-for-visual-studio/*](https://blogs.msdn.microsoft.com/webdev/2016/11/16/new-docker-tools-for-visual-studio/)</span><span class="sxs-lookup"><span data-stu-id="d64f9-335">**Jeffrey T. Fritz. Put a .NET Core App in a Container with the new Docker Tools for Visual Studio**
[*https://blogs.msdn.microsoft.com/webdev/2016/11/16/new-docker-tools-for-visual-studio/*](https://blogs.msdn.microsoft.com/webdev/2016/11/16/new-docker-tools-for-visual-studio/)</span></span>

## <a name="using-powershell-commands-in-a-dockerfile-to-set-up-windows-containers"></a><span data-ttu-id="d64f9-336">Nastavení Windows kontejnery pomocí příkazů prostředí PowerShell v soubor Docker</span><span class="sxs-lookup"><span data-stu-id="d64f9-336">Using PowerShell commands in a Dockerfile to set up Windows Containers</span></span> 

<span data-ttu-id="d64f9-337">[Kontejnery Windows](https://msdn.microsoft.com/en-us/virtualization/windowscontainers/about/about_overview) vám umožní převést existující aplikace Windows imagí Dockeru a nasadit je stejné nástroje jako zbytek ekosystému Docker.</span><span class="sxs-lookup"><span data-stu-id="d64f9-337">[Windows Containers](https://msdn.microsoft.com/en-us/virtualization/windowscontainers/about/about_overview) allow you to convert your existing Windows applications into Docker images and deploy them with the same tools as the rest of the Docker ecosystem.</span></span> <span data-ttu-id="d64f9-338">Pokud chcete používat Windows kontejnery, spusťte příkazy prostředí PowerShell v soubor Docker, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="d64f9-338">To use Windows Containers, you run PowerShell commands in the Dockerfile, as shown in the following example:</span></span>

```Dockerfile
FROM microsoft/windowsservercore
  
LABEL Description="IIS" Vendor="Microsoft" Version="10"
  
RUN powershell -Command Add-WindowsFeature Web-Server
  
CMD [ "ping", "localhost", "-t" ]
```

<span data-ttu-id="d64f9-339">V takovém případě jsme používáte základní bitovou kopii systému Windows Server Core (FROM nastavení) a instalace služby IIS pomocí příkazu prostředí PowerShell (nastavení spuštění).</span><span class="sxs-lookup"><span data-stu-id="d64f9-339">In this case, we are using a Windows Server Core base image (the FROM setting) and installing IIS with a PowerShell command (the RUN setting).</span></span> <span data-ttu-id="d64f9-340">Podobným způsobem můžete také použít příkazy prostředí PowerShell pro nastavení dalších komponent, jako je ASP.NET 4.x, .NET 4.6 nebo jiný software pro Windows.</span><span class="sxs-lookup"><span data-stu-id="d64f9-340">In a similar way, you could also use PowerShell commands to set up additional components like ASP.NET 4.x, .NET 4.6, or any other Windows software.</span></span> <span data-ttu-id="d64f9-341">Například následující příkaz v soubor Docker Nastaví technologii ASP.NET 4.5:</span><span class="sxs-lookup"><span data-stu-id="d64f9-341">For example, the following command in a Dockerfile sets up ASP.NET 4.5:</span></span>

```Dockerfile
RUN powershell add-windowsfeature web-asp-net45
```

### <a name="additional-resources"></a><span data-ttu-id="d64f9-342">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="d64f9-342">Additional resources</span></span>

-   <span data-ttu-id="d64f9-343">**aspnet-docker/Dockerfile.**</span><span class="sxs-lookup"><span data-stu-id="d64f9-343">**aspnet-docker/Dockerfile.**</span></span> <span data-ttu-id="d64f9-344">Příklady příkazů prostředí Powershell pro spouštění z dockerfiles zahrnout funkce systému Windows.</span><span class="sxs-lookup"><span data-stu-id="d64f9-344">Example Powershell commands to run from dockerfiles to include Windows features.</span></span>
    [*https://github.com/Microsoft/aspnet-docker/blob/master/4.6.2/Dockerfile*](https://github.com/Microsoft/aspnet-docker/blob/master/4.6.2/Dockerfile)

>[!div class="step-by-step"]
<span data-ttu-id="d64f9-345">[Předchozí] (index.md) [Další] (.. / net-core-single-containers-linux-windows-server-hosts/index.md)</span><span class="sxs-lookup"><span data-stu-id="d64f9-345">[Previous] (index.md) [Next] (../net-core-single-containers-linux-windows-server-hosts/index.md)</span></span>
