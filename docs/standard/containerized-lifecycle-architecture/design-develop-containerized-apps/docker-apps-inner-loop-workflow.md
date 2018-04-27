---
title: Pracovní postup vývoje vnitřní smyčky pro Docker aplikace
description: Kontejnerizované Docker životního cyklu aplikací s Microsoft platforma a nástroje
ms.prod: .net
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 8ee1918091fe72e8606be6e7503ecd850084a4ba
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2018
---
# <a name="inner-loop-development-workflow-for-docker-apps"></a><span data-ttu-id="4f2ae-103">Pracovní postup vývoje vnitřní smyčky pro Docker aplikace</span><span class="sxs-lookup"><span data-stu-id="4f2ae-103">Inner-loop development workflow for Docker apps</span></span>

<span data-ttu-id="4f2ae-104">Před spuštěním pracovního postupu vnější smyčky pokrývání uzlů celý DevOps cyklus, vše začíná na každý vývojář počítače, kódování aplikace, pomocí jejich upřednostňované jazyky nebo platformy a místní testování (obrázek 4-14).</span><span class="sxs-lookup"><span data-stu-id="4f2ae-104">Before triggering the outer-loop workflow spanning the entire DevOps cycle, it all begins on each developer's machine, coding the app itself, using their preferred languages or platforms, and testing it locally (Figure 4-14).</span></span> <span data-ttu-id="4f2ae-105">Ale v každém případě je nutné bod velmi důležité společné, bez ohledu na to, jaké jazyk, framework nebo platformy zvolíte.</span><span class="sxs-lookup"><span data-stu-id="4f2ae-105">But in every case, you will have a very important point in common, no matter what language, framework, or platforms you choose.</span></span> <span data-ttu-id="4f2ae-106">V tomto pracovním postupu konkrétní jsou vždy vývoj a testování Docker kontejnery, ale místně.</span><span class="sxs-lookup"><span data-stu-id="4f2ae-106">In this specific workflow, you are always developing and testing Docker containers, but locally.</span></span>

![](./media/image18.png)

<span data-ttu-id="4f2ae-107">Obrázek 4 – 14: vnitřní smyčky vývoj kontextu</span><span class="sxs-lookup"><span data-stu-id="4f2ae-107">Figure 4-14: Inner-loop development context</span></span>

<span data-ttu-id="4f2ae-108">Kontejner nebo instance Docker Image bude obsahovat tyto komponenty:</span><span class="sxs-lookup"><span data-stu-id="4f2ae-108">The container or instance of a Docker image will contain these components:</span></span>

-   <span data-ttu-id="4f2ae-109">Výběru operačního systému (například distribuční Linux nebo Windows)</span><span class="sxs-lookup"><span data-stu-id="4f2ae-109">An operating system selection (for example, a Linux distribution or Windows)</span></span>

-   <span data-ttu-id="4f2ae-110">Soubory přidal developer (například binární soubory aplikace)</span><span class="sxs-lookup"><span data-stu-id="4f2ae-110">Files added by the developer (for example, app binaries)</span></span>

-   <span data-ttu-id="4f2ae-111">Konfigurace (například nastavení prostředí a závislosti)</span><span class="sxs-lookup"><span data-stu-id="4f2ae-111">Configuration (for example, environment settings and dependencies)</span></span>

-   <span data-ttu-id="4f2ae-112">Pokyny pro jaké procesy spuštění pomocí Docker</span><span class="sxs-lookup"><span data-stu-id="4f2ae-112">Instructions for what processes to run by Docker</span></span>

<span data-ttu-id="4f2ae-113">Můžete nastavit vnitřní smyčky vývoj pracovního postupu, který využívá Docker jako proces (popsané v další části).</span><span class="sxs-lookup"><span data-stu-id="4f2ae-113">You can set up the inner-loop development workflow that utilizes Docker as the process (described in the next section).</span></span> <span data-ttu-id="4f2ae-114">Vezměte v úvahu, že počáteční kroky pro nastavení prostředí není zahrnutý, protože je potřeba udělat jenom jednou.</span><span class="sxs-lookup"><span data-stu-id="4f2ae-114">Take into account that the initial steps to set up the environment is not included, because you need to do that just once.</span></span>

## <a name="building-a-single-app-within-a-docker-container-using-visual-studio-code-and-docker-cli"></a><span data-ttu-id="4f2ae-115">Vytvoření jednoduché aplikace v rámci kontejner Docker pomocí Visual Studio Code a příkazového řádku Dockeru</span><span class="sxs-lookup"><span data-stu-id="4f2ae-115">Building a single app within a Docker container using Visual Studio Code and Docker CLI</span></span>

<span data-ttu-id="4f2ae-116">Aplikace se skládá z vlastní služby a další knihovny (závislosti).</span><span class="sxs-lookup"><span data-stu-id="4f2ae-116">Apps are made up from your own services plus additional libraries (dependencies).</span></span>

<span data-ttu-id="4f2ae-117">Obrázek 4 – 15 ukazuje základní kroky, které je obvykle potřeba provádět při sestavování aplikaci pomocí Docker, za nímž následuje podrobný popis jednotlivých kroků.</span><span class="sxs-lookup"><span data-stu-id="4f2ae-117">Figure 4-15 shows the basic steps that you usually need to carry out when building a Docker app, followed by detailed descriptions of each step.</span></span>

![](./media/image19.png)

<span data-ttu-id="4f2ae-118">Obrázek 4 – 15: základní pracovní postup pro životní cyklus Docker kontejnerizované aplikace pomocí příkazového řádku Dockeru</span><span class="sxs-lookup"><span data-stu-id="4f2ae-118">Figure 4-15: High-level workflow for the life cycle for Docker containerized applications using Docker CLI</span></span>

### <a name="step-1-start-coding-in-visual-studio-code-and-create-your-initial-appservice-baseline"></a><span data-ttu-id="4f2ae-119">Krok 1: Začínáme kódovat v kódu Visual Studio a vytvořte standardní hodnoty počáteční aplikace/služby</span><span class="sxs-lookup"><span data-stu-id="4f2ae-119">Step 1: Start coding in Visual Studio Code and create your initial app/service baseline</span></span>

<span data-ttu-id="4f2ae-120">Způsob, jak vyvíjet aplikaci je poměrně podobným způsobem, které můžete provést bez Docker.</span><span class="sxs-lookup"><span data-stu-id="4f2ae-120">The way you develop your application is pretty similar to the way you do it without Docker.</span></span> <span data-ttu-id="4f2ae-121">Rozdíl je, že při vývoji, jsou nasazení a testování aplikací nebo služeb spuštěných v rámci Docker kontejnery umístěny ve vašem místním prostředí (třeba virtuální počítač s Linuxem nebo Windows).</span><span class="sxs-lookup"><span data-stu-id="4f2ae-121">The difference is that while developing, you are deploying and testing your application or services running within Docker containers placed in your local environment (like a Linux VM or Windows).</span></span>

<span data-ttu-id="4f2ae-122">**Nastavení místního prostředí**</span><span class="sxs-lookup"><span data-stu-id="4f2ae-122">**Setting up your local environment**</span></span>

<span data-ttu-id="4f2ae-123">Nejnovější verze Docker pro Mac a Windows je jednodušší než kdy k vývoji aplikací Docker a instalace je jednoduchá.</span><span class="sxs-lookup"><span data-stu-id="4f2ae-123">With the latest versions of Docker for Mac and Windows, it's easier than ever to develop Docker applications, and the setup is straightforward.</span></span>

<span data-ttu-id="4f2ae-124">**Další informace o** pokyny k nastavení Docker pro systém Windows, přejděte na [ https://docs.docker.com/docker-for-windows/ ](https://docs.docker.com/docker-for-windows/).</span><span class="sxs-lookup"><span data-stu-id="4f2ae-124">**More info** For instructions on setting up Docker for Windows, go to [https://docs.docker.com/docker-for-windows/](https://docs.docker.com/docker-for-windows/).</span></span>

<span data-ttu-id="4f2ae-125">Pokyny k nastavení Docker pro Mac, přejděte na <https://docs.docker.com/docker-for-mac/>.</span><span class="sxs-lookup"><span data-stu-id="4f2ae-125">For instructions on setting up Docker for Mac, go to <https://docs.docker.com/docker-for-mac/>.</span></span>

<span data-ttu-id="4f2ae-126">Kromě toho budete potřebovat editor kódu, takže ve skutečnosti můžete vyvíjet aplikace pomocí příkazového řádku Dockeru.</span><span class="sxs-lookup"><span data-stu-id="4f2ae-126">In addition, you'll need a code editor so that you can actually develop your application while using Docker CLI.</span></span>

<span data-ttu-id="4f2ae-127">Společnost Microsoft poskytuje Visual Studio Code, což je editor lehký kód, který je podporován v Mac, Windows a Linux a poskytuje technologii IntelliSense, s [podporu mnoha jazyků](https://code.visualstudio.com/docs/languages/overview) (JavaScript, .NET, přejděte, Java, Ruby, Pythonu a většina moderních jazyků), [ladění](https://code.visualstudio.com/Docs/editor/debugging), [integrace s Gitem](https://code.visualstudio.com/Docs/editor/versioncontrol) a [rozšíření podpory](https://code.visualstudio.com/docs/extensions/overview).</span><span class="sxs-lookup"><span data-stu-id="4f2ae-127">Microsoft provides Visual Studio Code, which is a lightweight code editor that is supported on Mac, Windows, and Linux, and provides IntelliSense with [support for many languages](https://code.visualstudio.com/docs/languages/overview) (JavaScript, .NET, Go, Java, Ruby, Python, and most modern languages), [debugging](https://code.visualstudio.com/Docs/editor/debugging), [integration with Git](https://code.visualstudio.com/Docs/editor/versioncontrol) and [extensions support](https://code.visualstudio.com/docs/extensions/overview).</span></span> <span data-ttu-id="4f2ae-128">Tohoto editoru je skvělým přizpůsobit pro vývojáře, Mac a Linux.</span><span class="sxs-lookup"><span data-stu-id="4f2ae-128">This editor is a great fit for Mac and Linux developers.</span></span> <span data-ttu-id="4f2ae-129">V systému Windows také můžete použít celou aplikaci Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="4f2ae-129">In Windows, you also can use the full Visual Studio application.</span></span>

<span data-ttu-id="4f2ae-130">**Další informace o** pokyny k instalaci Visual Studio pro Windows, Mac nebo Linux, přejděte na [ http://code.visualstudio.com/docs/setup/setup-overview/https://docs.docker.com/docker-for-mac/ ](http://code.visualstudio.com/docs/setup/setup-overview/https:/docs.docker.com/docker-for-mac/).</span><span class="sxs-lookup"><span data-stu-id="4f2ae-130">**More info** For instructions on installing Visual Studio for Windows, Mac, or Linux, go to [http://code.visualstudio.com/docs/setup/setup-overview/https://docs.docker.com/docker-for-mac/](http://code.visualstudio.com/docs/setup/setup-overview/https:/docs.docker.com/docker-for-mac/).</span></span>

<span data-ttu-id="4f2ae-131">Můžete pracovat s příkazového řádku Dockeru a zadejte kód, pomocí libovolného editoru kódu, ale pokud používáte Visual Studio Code, umožňuje se snadno vytvořit soubor Docker a docker-compose.yml soubory v pracovním prostoru.</span><span class="sxs-lookup"><span data-stu-id="4f2ae-131">You can work with Docker CLI and write your code using any code editor, but if you use Visual Studio Code, it makes it easy to author Dockerfile and docker-compose.yml files in your workspace.</span></span> <span data-ttu-id="4f2ae-132">Plus můžete spustit v prostředí IDE, který zobrazí výzvu skripty, které můžou být spuštění propracována operace pomocí příkazového řádku Dockeru pod Visual Studio Code úlohy.</span><span class="sxs-lookup"><span data-stu-id="4f2ae-132">Plus, you can run Visual Studio Code tasks from the IDE that will prompt scripts that can be running elaborated operations using Docker CLI underneath.</span></span>

<span data-ttu-id="4f2ae-133">Visual Studio Code zajišťuje rozšíření, které budete muset nainstalovat.</span><span class="sxs-lookup"><span data-stu-id="4f2ae-133">Visual Studio Code is provided by an extension, which you'll need to install.</span></span> <span data-ttu-id="4f2ae-134">Uděláte to tak, stiskněte Ctrl + Shift + P, zadejte **ext nainstalovat**, a poté spusťte rozšíření: příkazu pro instalaci rozšíření se zprovoznit seznam rozšíření Marketplace.</span><span class="sxs-lookup"><span data-stu-id="4f2ae-134">To do so, Press Ctrl+Shift+P, type **ext install**, and then run the Extensions: Install Extension command to bring up the Marketplace extension list.</span></span> <span data-ttu-id="4f2ae-135">Potom zadejte **docker** filtrovat výsledky a potom vyberte soubor Docker a Docker Compose soubor (yml) podporu rozšíření, jak je to znázorněno na obrázku 4-16.</span><span class="sxs-lookup"><span data-stu-id="4f2ae-135">Next, type **docker** to filter the results, and then select the Dockerfile And Docker Compose File (yml) Support extension, as depicted in Figure 4-16.</span></span>

![](./media/image20.png)

<span data-ttu-id="4f2ae-136">Obrázek 4-16: Instalace rozšíření Docker v sadě Visual Studio kódu</span><span class="sxs-lookup"><span data-stu-id="4f2ae-136">Figure 4-16: Installing the Docker Extension in Visual Studio Code</span></span>

### <a name="step-2-create-a-dockerfile-related-to-an-existing-image-plain-os-or-dev-environments-like-net-core-nodejs-and-ruby"></a><span data-ttu-id="4f2ae-137">Krok 2: Vytvořte soubor Docker související s stávající image (prostý operačního systému nebo dev prostředí jako .NET Core, Node.js a Ruby)</span><span class="sxs-lookup"><span data-stu-id="4f2ae-137">Step 2: Create a DockerFile related to an existing image (plain OS or dev environments like .NET Core, Node.js, and Ruby)</span></span>

<span data-ttu-id="4f2ae-138">Budete potřebovat soubor Docker jednotlivých vlastní image má být sestaven a kontejner pro nasazení, proto, pokud vaše aplikace se skládá z jedné vlastní služba, budete potřebovat jeden soubor Docker.</span><span class="sxs-lookup"><span data-stu-id="4f2ae-138">You will need a DockerFile per custom image to be built and per container to be deployed, therefore, if your app is made up of a single custom service, you will need a single DockerFile.</span></span> <span data-ttu-id="4f2ae-139">Ale pokud vaše aplikace se skládá z několika služeb (jako architektura mikroslužeb), budete potřebovat jeden soubor Docker pro službu.</span><span class="sxs-lookup"><span data-stu-id="4f2ae-139">But, if your app is composed of multiple services (as in a microservices architecture), you'll need one Dockerfile per service.</span></span>

<span data-ttu-id="4f2ae-140">Soubor Docker je obvykle umístit do kořenové složky vaší aplikace nebo služby a obsahuje požadované příkazy, aby věděl, že Docker může nastavit a spuštění této aplikace nebo služby.</span><span class="sxs-lookup"><span data-stu-id="4f2ae-140">The DockerFile is usually placed within the root folder of your app or service and contains the required commands so that Docker knows how to set up and run that app or service.</span></span> <span data-ttu-id="4f2ae-141">Můžete vytvořit váš soubor Docker a přidejte do projektu spolu se váš kód (node.js, .NET Core, atd.), nebo, pokud začínáte do prostředí, podívejte se na následující špičky.</span><span class="sxs-lookup"><span data-stu-id="4f2ae-141">You can create your DockerFile and add it to your project along with your code (node.js, .NET Core, etc.), or, if you are new to the environment, take a look at the following Tip.</span></span>

> [!TIP]
> <span data-ttu-id="4f2ae-142">Můžete použít nástroj příkazového řádku názvem [yo docker](https://github.com/Microsoft/generator-docker), který scaffold soubory z projektu v jazyce, vyberte a přidá požadované Docker konfigurační soubory.</span><span class="sxs-lookup"><span data-stu-id="4f2ae-142">You can use a command-line tool called [yo docker](https://github.com/Microsoft/generator-docker), which scaffolds files from your project in the language you choose and adds the required Docker configuration files.</span></span> <span data-ttu-id="4f2ae-143">V podstatě, pomáhá vývojářům Začínáme, vytvoří odpovídající soubor Docker, docker-compose.yml a další související skripty sestavení a spuštění Docker kontejnerů.</span><span class="sxs-lookup"><span data-stu-id="4f2ae-143">Basically, to assist developers getting started, it creates the appropriate DockerFile, docker-compose.yml, and other associated scripts to build and run your Docker containers.</span></span> <span data-ttu-id="4f2ae-144">Tento generátor yeoman zobrazí výzvu pomocí pár otázek, s dotazem, váš hostitel vývoj pro vybraný jazyk a cílový kontejner.</span><span class="sxs-lookup"><span data-stu-id="4f2ae-144">This yeoman generator will prompt you with a few questions, asking your selected development language and destination container host.</span></span>

![Yo docker](./media/image21.png)

<span data-ttu-id="4f2ae-146">Například obrázek 4-17 ukazuje dva snímky obrazovky z terminály v systému Windows a na spuštěném na počítači Mac., v obou případech je docker, což způsobí vygenerování ukázkový kód projektů (aktuálně .NET Core, Golang a Node.js jako podporované jazyky) již byla konfigurována pro práci začátek Docker.</span><span class="sxs-lookup"><span data-stu-id="4f2ae-146">For instance, Figure 4-17 shows two screenshots from the terminals in Windows and on a Mac, in both cases, running yo docker, which will generate the sample code projects (currently .NET Core, Golang, and Node.js as supported languages) already configured to work on top of Docker.</span></span>

![](./media/image22.PNG)  ![](./media/image23.png)

<span data-ttu-id="4f2ae-147">Obrázek 4 – 17: yo docker příkaz nástroj v systému Windows (vlevo) a na Macu</span><span class="sxs-lookup"><span data-stu-id="4f2ae-147">Figure 4-17: yo docker command tool in Windows (left) and on a Mac</span></span>

<span data-ttu-id="4f2ae-148">Obrázek 4 až 18 představuje příklad pomocí yo docker po existujícího projektu .NET Core zavedené se vygeneroval.</span><span class="sxs-lookup"><span data-stu-id="4f2ae-148">Figure 4-18 presents an example using yo docker after you have an existing .NET Core project in place to be scaffolded.</span></span>

![](./media/image24.PNG)

<span data-ttu-id="4f2ae-149">Obrázek 4 – 18: yo docker s existující .NET Core projektu na místě</span><span class="sxs-lookup"><span data-stu-id="4f2ae-149">Figure 4-18: yo docker with an existing .NET Core project in place</span></span>

<span data-ttu-id="4f2ae-150">Z soubor Docker zadejte co základní Docker image, které budete používat (např. pomocí "od microsoft/dotnet:1.0.0-core").</span><span class="sxs-lookup"><span data-stu-id="4f2ae-150">From the DockerFile, you specify what base Docker image you'll be using (like using "FROM microsoft/dotnet:1.0.0-core").</span></span> <span data-ttu-id="4f2ae-151">Obvykle bude vytvářet vlastní bitovou kopii na základní bitovou kopii, kterou můžete získat z jakékoli oficiální úložiště na [úložiště Docker Hub registru](https://hub.docker.com/) (jako je [bitovou kopii pro .NET Core](https://hub.docker.com/r/microsoft/dotnet/) nebo jednu [pro Node.js](https://hub.docker.com/_/node/)).</span><span class="sxs-lookup"><span data-stu-id="4f2ae-151">You usually will build your custom image on top of a base image that you can get from any official repository at the [Docker Hub registry](https://hub.docker.com/) (like an [image for .NET Core](https://hub.docker.com/r/microsoft/dotnet/) or one [for Node.js](https://hub.docker.com/_/node/)).</span></span>

<span data-ttu-id="4f2ae-152">***Možnost A: použití existující bitovou kopii oficiální Docker***</span><span class="sxs-lookup"><span data-stu-id="4f2ae-152">***Option A: Use an existing official Docker image***</span></span>

<span data-ttu-id="4f2ae-153">Použití zásobníku jazyk oficiální úložiště s číslem verze zajistí k dispozici na všech počítačích (včetně vývoj, testování a produkci) stejné funkce jazyka.</span><span class="sxs-lookup"><span data-stu-id="4f2ae-153">Using an official repository of a language stack with a version number ensures that the same language features are available on all machines (including development, testing, and production).</span></span>

<span data-ttu-id="4f2ae-154">Toto je ukázkový soubor Docker pro .NET Core kontejner:</span><span class="sxs-lookup"><span data-stu-id="4f2ae-154">Following is a sample DockerFile for a .NET Core container:</span></span>

```
# Base Docker image to use
FROM microsoft/aspnetcore:1.0.1\

# Set the Working Directory and files to be copied to the image
ARG source
WORKDIR /app
COPY ${source:-bin/Release/PublishOutput} .

# Configure the listening port to 80 (Internal/Secured port within Docker host)
EXPOSE 80

# Application entry point
ENTRYPOINT ["dotnet", "MyCustomMicroservice.dll"]
```

<span data-ttu-id="4f2ae-155">V takovém případě používá verzi 1.0.1 bitovou kopii oficiální Docker jádro ASP.NET pro Linux s názvem microsoft/aspnetcore:1.0.1.</span><span class="sxs-lookup"><span data-stu-id="4f2ae-155">In this case, it is using the version 1.0.1 of the official ASP.NET Core Docker image for Linux named microsoft/aspnetcore:1.0.1.</span></span> <span data-ttu-id="4f2ae-156">Další podrobnosti naleznete [stránky ASP.NET Core Docker Image](https://hub.docker.com/r/microsoft/aspnetcore/) a [.NET Core Docker bitové](https://hub.docker.com/r/microsoft/dotnet/).</span><span class="sxs-lookup"><span data-stu-id="4f2ae-156">For further details, consult the [ASP.NET Core Docker Image page](https://hub.docker.com/r/microsoft/aspnetcore/) and the [.NET Core Docker Image page](https://hub.docker.com/r/microsoft/dotnet/).</span></span> <span data-ttu-id="4f2ae-157">Můžete také může používat jiné porovnatelný z hlediska image jako uzel: 4-onbuild pro Node.js nebo mnoha jiných předkonfigurované obrázků pro programovacích jazyků, které jsou k dispozici v [úložiště Docker Hub](https://hub.docker.com/explore/).</span><span class="sxs-lookup"><span data-stu-id="4f2ae-157">You also could be using another comparable image like node:4-onbuild for Node.js, or many other preconfigured images for development languages, which are available at [Docker Hub](https://hub.docker.com/explore/).</span></span>

<span data-ttu-id="4f2ae-158">V soubor Docker musíte také vyzvat Docker pro naslouchání na portu TCP, který budete používat v době běhu (například port 80).</span><span class="sxs-lookup"><span data-stu-id="4f2ae-158">In the DockerFile, you also need to instruct Docker to listen to the TCP port that you will use at runtime (such as port 80).</span></span>

<span data-ttu-id="4f2ae-159">Existují další řádky konfigurace, které můžete přidat na soubor Docker v závislosti na jazyk nebo rozhraní, které používáte, takže Docker umí spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="4f2ae-159">There are other lines of configuration that you can add in the DockerFile depending on the language/framework you are using, so Docker knows how to run the app.</span></span> <span data-ttu-id="4f2ae-160">Například musíte ENTRYPOINT řádek s \["dotnet", "MyCustomMicroservice.dll"\] ke spuštění aplikace .NET Core, i když můžete mít více variant v závislosti na přístup k sestavení a spuštění služby.</span><span class="sxs-lookup"><span data-stu-id="4f2ae-160">For instance, you need the ENTRYPOINT line with \["dotnet", "MyCustomMicroservice.dll"\] to run a .NET Core app, although you can have multiple variants depending on the approach to build and run your service.</span></span> <span data-ttu-id="4f2ae-161">Pokud používáte sadu SDK, dotnet rozhraní příkazového řádku k vytvoření a spuštění aplikace .NET, je mírně lišit.</span><span class="sxs-lookup"><span data-stu-id="4f2ae-161">If you're using the SDK and dotnet CLI to build and run the .NET app, it would be slightly different.</span></span> <span data-ttu-id="4f2ae-162">Dolní řádek je, že ENTRYPOINT řádku plus další řádky se budou lišit v závislosti na jazyk nebo platformy, které zvolíte pro vaši aplikaci.</span><span class="sxs-lookup"><span data-stu-id="4f2ae-162">The bottom line is that the ENTRYPOINT line plus additional lines will be different depending on the language/platform you choose for your application.</span></span>

<span data-ttu-id="4f2ae-163">**Další informace o** informace o vytváření imagí Dockeru pro aplikace .NET Core, přejděte na <https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images>.</span><span class="sxs-lookup"><span data-stu-id="4f2ae-163">**More info** For information about building Docker images for .NET Core applications, go to <https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images>.</span></span>

<span data-ttu-id="4f2ae-164">Další informace o vytváření vlastních bitových kopií, přejděte na [ https://docs.docker.com/engine/\kurzy/dockerimages/](https://docs.docker.com/engine/tutorials/dockerimages/).</span><span class="sxs-lookup"><span data-stu-id="4f2ae-164">To learn more about building your own images, go to [https://docs.docker.com/engine/\ tutorials/dockerimages/](https://docs.docker.com/engine/tutorials/dockerimages/).</span></span>

<span data-ttu-id="4f2ae-165">**Úložiště s více platformami bitové kopie**</span><span class="sxs-lookup"><span data-stu-id="4f2ae-165">**Multiplatform image repositories**</span></span>

<span data-ttu-id="4f2ae-166">Jako kontejnery Windows začnou více běžně se vyskytujícím, jednoho úložiště může obsahovat variant platformu, například image, Linux a Windows.</span><span class="sxs-lookup"><span data-stu-id="4f2ae-166">As Windows containers become more prevalent, a single repository can contain platform variants, such as a Linux and Windows image.</span></span> <span data-ttu-id="4f2ae-167">Toto je nová funkce brzo Docker, která umožňuje dodavatelům použít jednom úložišti pro více platforem, jako například [microsoft/aspdotnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) úložiště, které je k dispozici v registru DockerHub.</span><span class="sxs-lookup"><span data-stu-id="4f2ae-167">This is a new feature coming in Docker that makes it possible for vendors to use a single repository to cover multiple platforms, such as [microsoft/aspdotnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) repository, which is available at DockerHub registry.</span></span> <span data-ttu-id="4f2ae-168">Jako funkci dodává zachování připojení, stahování této bitové kopie z hostitele Windows načte Windows variant, zatímco stahování stejný název bitové kopie z hostitele platformy Linux načte Linux variant.</span><span class="sxs-lookup"><span data-stu-id="4f2ae-168">As the feature comes alive, pulling this image from a Windows host will pull the Windows variant, whereas pulling the same image name from a Linux host will pull the Linux variant.</span></span>

<span data-ttu-id="4f2ae-169">***Možnost B: vytvořit základní bitové kopie od začátku***</span><span class="sxs-lookup"><span data-stu-id="4f2ae-169">***Option B: Create your base image from scratch***</span></span>

<span data-ttu-id="4f2ae-170">Můžete vytvořit vlastní základní image Docker od začátku, jak je popsáno v tomto [článku](https://docs.docker.com/engine/userguide/eng-image/baseimages/) z Docker.</span><span class="sxs-lookup"><span data-stu-id="4f2ae-170">You can create your own Docker base image from scratch as explained in this [article](https://docs.docker.com/engine/userguide/eng-image/baseimages/) from Docker.</span></span> <span data-ttu-id="4f2ae-171">Toto je scénáře, který je pravděpodobně není pro vás nejvhodnější, pokud právě začínáte s Docker, ale pokud chcete nastavit konkrétní bity základní bitové kopie, můžete to provést.</span><span class="sxs-lookup"><span data-stu-id="4f2ae-171">This is a scenario that is probably not best for you if you are just starting with Docker, but if you want to set the specific bits of your own base image, you can do it.</span></span>

### <a name="step-3-create-your-custom-docker-images-embedding-your-service-in-it"></a><span data-ttu-id="4f2ae-172">Krok 3: Vytvoření vlastních imagí Dockeru vložení služby v ní</span><span class="sxs-lookup"><span data-stu-id="4f2ae-172">Step 3: Create your custom Docker images embedding your service in it</span></span>

<span data-ttu-id="4f2ae-173">Pro každý vlastní službu, která se skládá z vaší aplikace budete muset vytvořit související image.</span><span class="sxs-lookup"><span data-stu-id="4f2ae-173">For each custom service that comprises your app, you'll need to create a related image.</span></span> <span data-ttu-id="4f2ae-174">Pokud vaše aplikace se skládá z jedné služby nebo webové aplikace, budete potřebovat pouze jeden obrázek.</span><span class="sxs-lookup"><span data-stu-id="4f2ae-174">If your app is made up of a single service or web app, you'll need just a single image.</span></span>

> [!NOTE]
> <span data-ttu-id="4f2ae-175">Když se vezme v úvahu "DevOps workflow Vnější smyčka", bitové kopie bude vytvořena procesem automatizované sestavení vždy, když push zdrojový kód do úložiště Git (průběžnou integraci), bitové kopie budou vytvořeny v globální prostředí z vaší zdrojový kód.</span><span class="sxs-lookup"><span data-stu-id="4f2ae-175">When taking into account the "outer-loop DevOps workflow," the images will be created by an automated build process whenever you push your source code to a Git repository (Continuous Integration) so the images will be created in that global environment from your source code.</span></span>

<span data-ttu-id="4f2ae-176">Ale předtím, než jsme zvažte má pro danou trasu vnější smyčky, potřebujeme zajistit, že aplikace Docker skutečně funguje správně, aby se nemáte push kód, který nemusí fungovat správně do správy zdrojového kódu (Git, atd.).</span><span class="sxs-lookup"><span data-stu-id="4f2ae-176">But, before we consider going to that outer-loop route, we need to ensure that the Docker application is actually working properly so that they don't push code that might not work properly to the source control system (Git, etc.).</span></span>

<span data-ttu-id="4f2ae-177">Proto každý vývojář nejdřív je potřeba udělat celý proces vnitřní smyčky pro testování místně a pokračovat ve vývoji, dokud chtějí push dokončení funkce nebo změňte správy zdrojového kódu.</span><span class="sxs-lookup"><span data-stu-id="4f2ae-177">Therefore, each developer first needs to do the entire inner-loop process to test locally and continue developing until they want to push a complete feature or change to the source control system.</span></span>

<span data-ttu-id="4f2ae-178">K vytvoření image ve vašem místním prostředí a pomocí soubor Docker, můžete příkaz sestavení docker, jak je předvedeno v obrázek 4-19 (také můžete spustit docker compose nahoru – sestavení pro aplikace, které sestává z několika kontejnerů nebo služeb).</span><span class="sxs-lookup"><span data-stu-id="4f2ae-178">To create an image in your local environment and using the DockerFile, you can use the docker build command, as demonstrated in Figure 4-19 (you also can run docker-compose up --build for applications composed by several containers/services).</span></span>

![](./media/image25.png)

<span data-ttu-id="4f2ae-179">Obrázek 4 – 19: spuštění docker sestavení</span><span class="sxs-lookup"><span data-stu-id="4f2ae-179">Figure 4-19: Running docker build</span></span>

<span data-ttu-id="4f2ae-180">Volitelně můžete místo přímo spouštět docker sestavení ze složky projektu, nejprve můžete vygenerovat nasadit složku s knihovnami .NET potřeby pomocí spuštění dotnet publikování příkaz, a poté spusťte docker sestavení.</span><span class="sxs-lookup"><span data-stu-id="4f2ae-180">Optionally, instead of directly running docker build from the project's folder, you first can generate a deployable folder with the .NET libraries needed by using the run dotnet publish command, and then run docker build.</span></span>

<span data-ttu-id="4f2ae-181">V tomto příkladu to vytvoří bitovou kopii Docker se název cesardl/netcore-webapi mikroslužbu-docker: první (: nejdřív se značky, například na konkrétní verzi).</span><span class="sxs-lookup"><span data-stu-id="4f2ae-181">In this example, this creates a Docker image with the name cesardl/netcore-webapi-microservice-docker:first (:first is a tag, like a specific version).</span></span> <span data-ttu-id="4f2ae-182">Tento krok pro každý vlastní image, které potřebujete k vytvoření aplikace skládá Docker s několika kontejnerů může trvat.</span><span class="sxs-lookup"><span data-stu-id="4f2ae-182">You can take this step for each custom image you need to create for your composed Docker application with several containers.</span></span>

<span data-ttu-id="4f2ae-183">Image můžete najít existující do místního úložiště (vývojovém počítači) pomocí docker příkaz bitové kopie, jak ukazuje obrázek 4-20.</span><span class="sxs-lookup"><span data-stu-id="4f2ae-183">You can find the existing images in your local repository (your development machine) by using the docker images command, as illustrated in Figure 4-20.</span></span>

![](./media/image26.png)

<span data-ttu-id="4f2ae-184">Obrázek 4-20: zobrazení existujících bitových kopií pomocí docker obrázků</span><span class="sxs-lookup"><span data-stu-id="4f2ae-184">Figure 4-20: Viewing existing images using docker images</span></span>

### <a name="step-4-optional-define-your-services-in-docker-composeyml-when-building-a-composed-docker-app-with-multiple-services"></a><span data-ttu-id="4f2ae-185">Krok 4: Definování (volitelné) vašim službám v docker-compose.yml při sestavování složený aplikace Docker s více službami</span><span class="sxs-lookup"><span data-stu-id="4f2ae-185">Step 4: (Optional) Define your services in docker-compose.yml when building a composed Docker app with multiple services</span></span>

<span data-ttu-id="4f2ae-186">Pomocí soubor docker-compose.yml můžete definovat sadu související služby pro nasazení jako složený aplikace pomocí příkazů nasazení popsané v další části kroku.</span><span class="sxs-lookup"><span data-stu-id="4f2ae-186">With the docker-compose.yml file you can define a set of related services to be deployed as a composed application with the deployment commands explained in the next step section.</span></span>

<span data-ttu-id="4f2ae-187">Je potřeba vytvořit tento soubor do vaší hlavní nebo kořenové složky řešení; Podobně jako obsah musí mít pro následující soubor docker-compose.yml:</span><span class="sxs-lookup"><span data-stu-id="4f2ae-187">You need to create that file in your main or root solution folder; it should have a similar content to the following docker-compose.yml file:</span></span>

```yml
version: '2'
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

<span data-ttu-id="4f2ae-188">V tomto konkrétním případě tento soubor definuje dvě služby: webové služby (služby vlastní) a službu redis (služba oblíbených mezipaměti).</span><span class="sxs-lookup"><span data-stu-id="4f2ae-188">In this particular case, this file defines two services: the web service (your custom service) and the redis service (a popular cache service).</span></span> <span data-ttu-id="4f2ae-189">Každá služba budou nasazeny jako kontejner, takže je potřeba použít konkrétní Docker bitovou kopii pro každý.</span><span class="sxs-lookup"><span data-stu-id="4f2ae-189">Each service will be deployed as a container, so we need to use a concrete Docker image for each.</span></span> <span data-ttu-id="4f2ae-190">Pro tuto konkrétní webovou službu bude nutné bitovou kopii postupujte takto:</span><span class="sxs-lookup"><span data-stu-id="4f2ae-190">For this particular web service, the image will need to do the following:</span></span>

-   <span data-ttu-id="4f2ae-191">Sestavení z soubor Docker v aktuálním adresáři</span><span class="sxs-lookup"><span data-stu-id="4f2ae-191">Build from the DockerFile in the current directory</span></span>

-   <span data-ttu-id="4f2ae-192">Předávání zveřejněné port 80 kontejneru na port 81 na hostitelském počítači</span><span class="sxs-lookup"><span data-stu-id="4f2ae-192">Forward the exposed port 80 on the container to port 81 on the host machine</span></span>

-   <span data-ttu-id="4f2ae-193">Připojení adresáře projektu na hostiteli, aby /code v rámci kontejneru, která umožňuje upravit kód bez nutnosti znovu vytvořit bitovou kopii</span><span class="sxs-lookup"><span data-stu-id="4f2ae-193">Mount the project directory on the host to /code within the container, making it possible for you to modify the code without having to rebuild the image</span></span>

-   <span data-ttu-id="4f2ae-194">Webová služba propojit službu redis</span><span class="sxs-lookup"><span data-stu-id="4f2ae-194">Link the web service to the redis service</span></span>

<span data-ttu-id="4f2ae-195">Používá službu redis [nejnovější bitové kopie veřejného redis](https://hub.docker.com/_/redis/) načtený z registru úložiště Docker Hub.</span><span class="sxs-lookup"><span data-stu-id="4f2ae-195">The redis service uses the [latest public redis image](https://hub.docker.com/_/redis/) pulled from the Docker Hub registry.</span></span> <span data-ttu-id="4f2ae-196">[redis](https://redis.io/) je systém velmi oblíbených mezipaměti pro serverové aplikace.</span><span class="sxs-lookup"><span data-stu-id="4f2ae-196">[redis](https://redis.io/) is a very popular cache system for server-side applications.</span></span>

### <a name="step-5-build-and-run-your-docker-app"></a><span data-ttu-id="4f2ae-197">Krok 5: Vytvoření a spuštění aplikace Docker</span><span class="sxs-lookup"><span data-stu-id="4f2ae-197">Step 5: Build and run your Docker app</span></span>

<span data-ttu-id="4f2ae-198">Pokud vaše aplikace obsahuje pouze jediný kontejner, stačí spustit publikovat na vašem hostiteli Docker (virtuálního počítače nebo fyzického serveru).</span><span class="sxs-lookup"><span data-stu-id="4f2ae-198">If your app has only a single container, you just need to run it by deploying it to your Docker Host (VM or physical server).</span></span> <span data-ttu-id="4f2ae-199">Ale pokud vaše aplikace se skládá z několika služeb, budete muset *tvoří ho*, příliš.</span><span class="sxs-lookup"><span data-stu-id="4f2ae-199">However, if your app is made up of multiple services, you need to *compose it*, too.</span></span> <span data-ttu-id="4f2ae-200">Podíváme se na různé možnosti.</span><span class="sxs-lookup"><span data-stu-id="4f2ae-200">Let's see the different options.</span></span>

<span data-ttu-id="4f2ae-201">***Možnost A: jediný kontejner nebo služby***</span><span class="sxs-lookup"><span data-stu-id="4f2ae-201">***Option A: Run a single container or service***</span></span>

<span data-ttu-id="4f2ae-202">Bitovou kopii Docker můžete spustit pomocí docker, spusťte příkaz, jak je vidět tady:</span><span class="sxs-lookup"><span data-stu-id="4f2ae-202">You can run the Docker image by using the docker run command, as shown here:</span></span>

```
docker run -t -d -p 80:5000
cesardl/netcore-webapi-microservice-docker:first
```

<span data-ttu-id="4f2ae-203">Všimněte si, že pro toto konkrétní nasazení, jsme budete přesměrovávat žádosti poslané na port 80 k interní port 5000.</span><span class="sxs-lookup"><span data-stu-id="4f2ae-203">Note that for this particular deployment, we'll be redirecting requests sent to port 80 to the internal port 5000.</span></span> <span data-ttu-id="4f2ae-204">Aplikace je nyní naslouchá na externím portu 80 na úrovni hostitele.</span><span class="sxs-lookup"><span data-stu-id="4f2ae-204">Now, the application is listening on the external port 80 at the host level.</span></span>

<span data-ttu-id="4f2ae-205">***Možnost B: vytvářené a spusťte aplikaci více kontejneru***</span><span class="sxs-lookup"><span data-stu-id="4f2ae-205">***Option B: Compose and run a multiple-container application***</span></span>

<span data-ttu-id="4f2ae-206">Ve většině scénářů organizace Docker aplikace se skládá z několika služeb.</span><span class="sxs-lookup"><span data-stu-id="4f2ae-206">In most enterprise scenarios, a Docker application will be composed of multiple services.</span></span> <span data-ttu-id="4f2ae-207">Pro tyto případy, můžete spustit příkaz docker compose nahoru (obrázek 4 – 21), který bude použit soubor docker-compose.yml, kterou může jste vytvořili dříve.</span><span class="sxs-lookup"><span data-stu-id="4f2ae-207">For these cases, you can run the command docker-compose up (Figure 4-21), which will use the docker-compose.yml file that you might have created previously.</span></span> <span data-ttu-id="4f2ae-208">Spuštění tohoto příkazu nasadí složený aplikaci se všemi jeho související kontejnerů.</span><span class="sxs-lookup"><span data-stu-id="4f2ae-208">Running this command deploys a composed application with all of its related containers.</span></span>

![](./media/image27.png)

<span data-ttu-id="4f2ae-209">Obrázek 4 – 21: výsledky spuštěním příkazu "docker-compose nahoru"</span><span class="sxs-lookup"><span data-stu-id="4f2ae-209">Figure 4-21: Results of running the "docker-compose up" command</span></span>

<span data-ttu-id="4f2ae-210">Po spuštění docker-vytvořit zálohu, nasazení aplikace a její související kontejnery do Docker hostiteli, jak ukazuje obrázek 4 – 22 reprezentace virtuálních počítačů.</span><span class="sxs-lookup"><span data-stu-id="4f2ae-210">After you run docker-compose up, you deploy your application and its related container(s) into your Docker Host, as illustrated in Figure 4-22, in the VM representation.</span></span>

![](./media/image28.png)

<span data-ttu-id="4f2ae-211">Obrázek 4 – 22: virtuálních počítačů s kontejnery Docker nasazení</span><span class="sxs-lookup"><span data-stu-id="4f2ae-211">Figure 4-22: VM with Docker containers deployed</span></span>

<span data-ttu-id="4f2ae-212">Poznámka: docker tvoří nahoru a docker spustit mohou být dostatečné pro testování kontejnerů ve vašem vývojovém prostředí, ale pokud očekáváte pro práci s clustery Docker a orchestrators jako Docker Swarm, Mesosphere DC/OS nebo Kubernetes je nemusí použít na všech aby bylo možné škálovat.</span><span class="sxs-lookup"><span data-stu-id="4f2ae-212">Note docker-compose up and docker run might be enough for testing your containers in your development environment, but you might not use them at all if you are expecting to work with Docker clusters and orchestrators like Docker Swarm, Mesosphere DC/OS, or Kubernetes in order to be able to scale up.</span></span> <span data-ttu-id="4f2ae-213">Pokud používáte cluster jako [Docker Swarm režimu](https://docs.docker.com/engine/swarm/) (k dispozici v Docker pro systém Windows a Mac od verze 1.12), musíte nasadit a otestovat s další příkazy, jako je služba docker vytvořit pro jednu službu nebo pokud jste nasazení aplikace skládá z několika kontejnerů pomocí docker compose sady a docker nasazení myBundleFile, nasazením aplikace komponovaná jako zásobník, jak je popsáno v článku [distribuované aplikace sady](https://blog.docker.com/2016/06/docker-app-bundle/) z Docker.</span><span class="sxs-lookup"><span data-stu-id="4f2ae-213">If you're using a cluster like [Docker Swarm mode](https://docs.docker.com/engine/swarm/) (available in Docker for Windows and Mac since version 1.12), you need to deploy and test with additional commands such as docker service create for single services, or when you're deploying an app composed of several containers, using docker compose bundle and docker deploy myBundleFile, by deploying the composed app as a stack, as explained in the article [Distributed Application Bundles](https://blog.docker.com/2016/06/docker-app-bundle/) from Docker.</span></span>

<span data-ttu-id="4f2ae-214">Pro [DC/OS](https://mesosphere.com/blog/2015/09/02/dcos-cli-command-line-tool-datacenter/) a [Kubernetes](http://kubernetes.io/docs/user-guide/deployments/#creating-a-deployment) použijete jiné nasazení příkazy a skripty, také.</span><span class="sxs-lookup"><span data-stu-id="4f2ae-214">For [DC/OS](https://mesosphere.com/blog/2015/09/02/dcos-cli-command-line-tool-datacenter/) and [Kubernetes](http://kubernetes.io/docs/user-guide/deployments/#creating-a-deployment) you would use different deployment commands and scripts, as well.</span></span>

### <a name="step-6-test-your-docker-application-locally-in-your-local-cd-vm"></a><span data-ttu-id="4f2ae-215">Krok 6: Testování vaší aplikace Docker (místně, v místní virtuální počítač CD)</span><span class="sxs-lookup"><span data-stu-id="4f2ae-215">Step 6: Test your Docker application (locally, in your local CD VM)</span></span>

<span data-ttu-id="4f2ae-216">Tento krok se bude lišit v závislosti na tom, co je to vaše aplikace.</span><span class="sxs-lookup"><span data-stu-id="4f2ae-216">This step will vary depending on what your app is doing.</span></span>

<span data-ttu-id="4f2ae-217">Ve velmi jednoduché rozhraní .NET Core webového rozhraní API "Hello, World" nasazené jako jediný kontejner nebo služby by stačí pro přístup ke službě tím, že poskytuje TCP port zadaný v soubor Docker.</span><span class="sxs-lookup"><span data-stu-id="4f2ae-217">In a very simple .NET Core Web API "Hello World" deployed as a single container or service, you'd just need to access the service by providing the TCP port specified in the DockerFile.</span></span>

<span data-ttu-id="4f2ae-218">Pokud localhost není zapnutá, přejděte na službě, najít IP adresu pro počítač pomocí tohoto příkazu:</span><span class="sxs-lookup"><span data-stu-id="4f2ae-218">If localhost is not turned on, to navigate to your service, find the IP address for the machine by using this command:</span></span>

<span data-ttu-id="4f2ae-219">počítač docker ip *si název kontejneru*</span><span class="sxs-lookup"><span data-stu-id="4f2ae-219">docker-machine ip *your-container-name*</span></span>

<span data-ttu-id="4f2ae-220">Na hostiteli Docker otevřete prohlížeč a přejděte do této lokality; měli byste vidět vaší aplikace nebo služba spuštěna, jak je předvedeno v obrázek 4 – 23.</span><span class="sxs-lookup"><span data-stu-id="4f2ae-220">On the Docker host, open a browser and navigate to that site; you should see your app/service running, as demonstrated in Figure 4-23.</span></span>

![](./media/image29.png)

<span data-ttu-id="4f2ae-221">Obrázek 4 – 23: testování Docker aplikace místně pomocí místního hostitele</span><span class="sxs-lookup"><span data-stu-id="4f2ae-221">Figure 4-23: Testing your Docker application locally using localhost</span></span>

<span data-ttu-id="4f2ae-222">Všimněte si, že používá port 80, ale interně byl přesměrován na port 5000, protože se jedná o tom, jak byl zaveden pomocí docker spustit, jak je popsáno výše.</span><span class="sxs-lookup"><span data-stu-id="4f2ae-222">Note that it is using port 80, but internally it was being redirected to port 5000, because that's how it was deployed with docker run, as explained earlier.</span></span>

<span data-ttu-id="4f2ae-223">Toto můžete otestovat pomocí CURL z terminálu.</span><span class="sxs-lookup"><span data-stu-id="4f2ae-223">You can test this by using CURL from the terminal.</span></span> <span data-ttu-id="4f2ae-224">V rámci Docker instalace v systému Windows je výchozí IP 10.0.75.1, jak je znázorněno v obrázek 4 – 24.</span><span class="sxs-lookup"><span data-stu-id="4f2ae-224">In a Docker installation on Windows, the default IP is 10.0.75.1, as depicted in Figure 4-24.</span></span>

![](./media/image30.png)

<span data-ttu-id="4f2ae-225">Obrázek 4 – 24: testování aplikace Docker místně pomocí CURL</span><span class="sxs-lookup"><span data-stu-id="4f2ae-225">Figure 4-24: Testing a Docker application locally by using CURL</span></span>

<span data-ttu-id="4f2ae-226">**Ladění kontejner Docker systémem**</span><span class="sxs-lookup"><span data-stu-id="4f2ae-226">**Debugging a container running on Docker**</span></span>

<span data-ttu-id="4f2ae-227">Visual Studio Code podporuje ladění Docker, pokud používáte Node.js a jiných platformách, jako kontejnery .NET Core.</span><span class="sxs-lookup"><span data-stu-id="4f2ae-227">Visual Studio Code supports debugging Docker if you're using Node.js and other platforms like .NET Core containers.</span></span>

<span data-ttu-id="4f2ae-228">Také můžete ladit .NET Core kontejnery v Docker když pomocí sady Visual Studio, jak je popsáno v následující části.</span><span class="sxs-lookup"><span data-stu-id="4f2ae-228">You also can debug .NET Core containers in Docker when using Visual Studio, as described in the next section.</span></span>

<span data-ttu-id="4f2ae-229">**Další informace:** Další informace o ladění kontejnerů Node.js Docker, přejděte na <https://blog.docker.com/2016/07/live-debugging-docker/> a [ https://blogs.msdn.microsoft.com/\ uživatele\_ed/2016/02/27 / Visual-Studio-Code-New-features-13-Big-Debugging-Updates-Rich-Object-hover-Conditional-breakpoints-node-js-mono-more/](https://blogs.msdn.microsoft.com/user_ed/2016/02/27/visual-studio-code-new-features-13-big-debugging-updates-rich-object-hover-conditional-breakpoints-node-js-mono-more/).</span><span class="sxs-lookup"><span data-stu-id="4f2ae-229">**More info:** To learn more about debugging Node.js Docker containers, go to <https://blog.docker.com/2016/07/live-debugging-docker/> and [https://blogs.msdn.microsoft.com/\ user\_ed/2016/02/27/visual-studio-code-new-features-13-big-debugging-updates-rich-object-hover-conditional-breakpoints-node-js-mono-more/](https://blogs.msdn.microsoft.com/user_ed/2016/02/27/visual-studio-code-new-features-13-big-debugging-updates-rich-object-hover-conditional-breakpoints-node-js-mono-more/).</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="4f2ae-230">[Předchozí] (docker aplikace development-environment.md) [Další] (visual-studio nástroje pro docker.md)</span><span class="sxs-lookup"><span data-stu-id="4f2ae-230">[Previous] (docker-apps-development-environment.md) [Next] (visual-studio-tools-for-docker.md)</span></span>
