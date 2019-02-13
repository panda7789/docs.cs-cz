---
title: Pracovní postup vývoje vnitřní smyčky pro aplikace Dockeru
description: Přečtěte si pracovní postup "vnitřní smyčky" pro vývoj aplikací Dockeru.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 11/23/2018
ms.openlocfilehash: 03eb4662e55551678105fa9ef25b42cc05c132a5
ms.sourcegitcommit: 30e2fe5cc4165aa6dde7218ec80a13def3255e98
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/13/2019
ms.locfileid: "56219085"
---
# <a name="inner-loop-development-workflow-for-docker-apps"></a><span data-ttu-id="a3370-103">Pracovní postup vývoje vnitřní smyčky pro aplikace Dockeru</span><span class="sxs-lookup"><span data-stu-id="a3370-103">Inner-loop development workflow for Docker apps</span></span>

<span data-ttu-id="a3370-104">Před aktivací pracovního postupu vnější smyčky pokrývající celý DevOps cyklu, to všechno začíná každý vývojář počítače, psaní kódu aplikace pomocí jejich preferované jazyky a platformy a jejím místním otestováním (obrázek 4 – 14).</span><span class="sxs-lookup"><span data-stu-id="a3370-104">Before triggering the outer-loop workflow spanning the entire DevOps cycle, it all begins on each developer's machine, coding the app itself, using their preferred languages or platforms, and testing it locally (Figure 4-14).</span></span> <span data-ttu-id="a3370-105">Ale v každém případě budete mít velmi důležitý bod v běžném, bez ohledu na to, jaký jazyk, rozhraní nebo platformy zvolíte.</span><span class="sxs-lookup"><span data-stu-id="a3370-105">But in every case, you will have a very important point in common, no matter what language, framework, or platforms you choose.</span></span> <span data-ttu-id="a3370-106">V tomto konkrétním pracovním postupu jsou vždy vývoj a testování kontejnery Dockeru, ale místně.</span><span class="sxs-lookup"><span data-stu-id="a3370-106">In this specific workflow, you are always developing and testing Docker containers, but locally.</span></span>

![](./media/image18.png)

<span data-ttu-id="a3370-107">Obrázek 4 – 14: Kontext vývoje vnitřní smyčky</span><span class="sxs-lookup"><span data-stu-id="a3370-107">Figure 4-14: Inner-loop development context</span></span>

<span data-ttu-id="a3370-108">Kontejner nebo instance image Dockeru, bude obsahovat tyto komponenty:</span><span class="sxs-lookup"><span data-stu-id="a3370-108">The container or instance of a Docker image will contain these components:</span></span>

-   <span data-ttu-id="a3370-109">Výběru operačního systému (například distribuci Linuxu nebo Windows)</span><span class="sxs-lookup"><span data-stu-id="a3370-109">An operating system selection (for example, a Linux distribution or Windows)</span></span>

-   <span data-ttu-id="a3370-110">Soubory přidané vývojář (třeba binární soubory aplikace)</span><span class="sxs-lookup"><span data-stu-id="a3370-110">Files added by the developer (for example, app binaries)</span></span>

-   <span data-ttu-id="a3370-111">Konfigurace (například nastavení prostředí a závislosti)</span><span class="sxs-lookup"><span data-stu-id="a3370-111">Configuration (for example, environment settings and dependencies)</span></span>

-   <span data-ttu-id="a3370-112">Pokyny pro jaké procesy spuštění pomocí Dockeru</span><span class="sxs-lookup"><span data-stu-id="a3370-112">Instructions for what processes to run by Docker</span></span>

<span data-ttu-id="a3370-113">Můžete nastavit pracovní postup vývoje vnitřní smyčky, s využitím Dockeru jako proces (popsané v další části).</span><span class="sxs-lookup"><span data-stu-id="a3370-113">You can set up the inner-loop development workflow that utilizes Docker as the process (described in the next section).</span></span> <span data-ttu-id="a3370-114">Vezměte v úvahu, že počáteční kroky k nastavení prostředí není zahrnuta, protože je potřeba udělat jenom jednou.</span><span class="sxs-lookup"><span data-stu-id="a3370-114">Take into account that the initial steps to set up the environment is not included, because you need to do that just once.</span></span>

## <a name="building-a-single-app-within-a-docker-container-using-visual-studio-code-and-docker-cli"></a><span data-ttu-id="a3370-115">Vytvoření jednoduché aplikace v kontejneru Dockeru pomocí Visual Studio Code a rozhraní příkazového řádku Dockeru</span><span class="sxs-lookup"><span data-stu-id="a3370-115">Building a single app within a Docker container using Visual Studio Code and Docker CLI</span></span>

<span data-ttu-id="a3370-116">Aplikace se skládá z vlastní služby a další knihovny (závislosti).</span><span class="sxs-lookup"><span data-stu-id="a3370-116">Apps are made up from your own services plus additional libraries (dependencies).</span></span>

<span data-ttu-id="a3370-117">Obrázek 4 – 15 ukazuje základní kroky, které je obvykle potřeba provádět při vytváření aplikace Dockeru, za nímž následuje podrobný popis jednotlivých kroků.</span><span class="sxs-lookup"><span data-stu-id="a3370-117">Figure 4-15 shows the basic steps that you usually need to carry out when building a Docker app, followed by detailed descriptions of each step.</span></span>

![](./media/image19.png)

<span data-ttu-id="a3370-118">Obrázek 4 – 15: Pracovní postup vysoké úrovně pro životní cyklus pro Docker kontejnerizovaných aplikací pomocí rozhraní příkazového řádku Dockeru</span><span class="sxs-lookup"><span data-stu-id="a3370-118">Figure 4-15: High-level workflow for the life cycle for Docker containerized applications using Docker CLI</span></span>

### <a name="step-1-start-coding-in-visual-studio-code-and-create-your-initial-appservice-baseline"></a><span data-ttu-id="a3370-119">Krok 1: Pusťte se do programování ve Visual Studio Code a vytvořit směrný plán počáteční aplikace nebo služby</span><span class="sxs-lookup"><span data-stu-id="a3370-119">Step 1: Start coding in Visual Studio Code and create your initial app/service baseline</span></span>

<span data-ttu-id="a3370-120">Způsob, jak vyvíjet aplikace je hodně podobné způsobu práce bez Dockeru.</span><span class="sxs-lookup"><span data-stu-id="a3370-120">The way you develop your application is pretty similar to the way you do it without Docker.</span></span> <span data-ttu-id="a3370-121">Rozdíl je, že při vývoji, máte nasazení a testování vaší aplikace nebo služby v rámci kontejnery Dockeru, které jsou umístěny v místním prostředí (např. virtuální počítač s Linuxem nebo Windows).</span><span class="sxs-lookup"><span data-stu-id="a3370-121">The difference is that while developing, you are deploying and testing your application or services running within Docker containers placed in your local environment (like a Linux VM or Windows).</span></span>

<span data-ttu-id="a3370-122">**Nastavení místního prostředí**</span><span class="sxs-lookup"><span data-stu-id="a3370-122">**Setting up your local environment**</span></span>

<span data-ttu-id="a3370-123">S nejnovější verzí Dockeru pro Mac a Windows je jednodušší než dříve k vývoji aplikací Dockeru a instalační program je jednoduché.</span><span class="sxs-lookup"><span data-stu-id="a3370-123">With the latest versions of Docker for Mac and Windows, it's easier than ever to develop Docker applications, and the setup is straightforward.</span></span>

<span data-ttu-id="a3370-124">**Další informace o** pokyny týkající se nastavení Dockeru pro Windows, přejděte na [ https://docs.docker.com/docker-for-windows/ ](https://docs.docker.com/docker-for-windows/).</span><span class="sxs-lookup"><span data-stu-id="a3370-124">**More info** For instructions on setting up Docker for Windows, go to [https://docs.docker.com/docker-for-windows/](https://docs.docker.com/docker-for-windows/).</span></span>

<span data-ttu-id="a3370-125">Pokyny k nastavení Dockeru pro Mac, přejděte na <https://docs.docker.com/docker-for-mac/>.</span><span class="sxs-lookup"><span data-stu-id="a3370-125">For instructions on setting up Docker for Mac, go to <https://docs.docker.com/docker-for-mac/>.</span></span>

<span data-ttu-id="a3370-126">Kromě toho budete potřebovat editor kódu tak, aby ve skutečnosti můžete vyvíjet aplikace pomocí rozhraní příkazového řádku Dockeru.</span><span class="sxs-lookup"><span data-stu-id="a3370-126">In addition, you'll need a code editor so that you can actually develop your application while using Docker CLI.</span></span>

<span data-ttu-id="a3370-127">Společnost Microsoft poskytuje Visual Studio Code, který je ve zjednodušeném editoru kódu, který se podporuje na Macu, Windows a Linux a nabízí technologii IntelliSense s [podporu mnoha jazyků](https://code.visualstudio.com/docs/languages/overview) (jazyk JavaScript, .NET, Go, Java, Ruby, Python a většinu Moderní jazyky), [ladění](https://code.visualstudio.com/Docs/editor/debugging), [integrace s úložištěm Git](https://code.visualstudio.com/Docs/editor/versioncontrol) a [rozšíření podpory](https://code.visualstudio.com/docs/extensions/overview).</span><span class="sxs-lookup"><span data-stu-id="a3370-127">Microsoft provides Visual Studio Code, which is a lightweight code editor that is supported on Mac, Windows, and Linux, and provides IntelliSense with [support for many languages](https://code.visualstudio.com/docs/languages/overview) (JavaScript, .NET, Go, Java, Ruby, Python, and most modern languages), [debugging](https://code.visualstudio.com/Docs/editor/debugging), [integration with Git](https://code.visualstudio.com/Docs/editor/versioncontrol) and [extensions support](https://code.visualstudio.com/docs/extensions/overview).</span></span> <span data-ttu-id="a3370-128">Tento editor se skvěle hodí pro vývojáře Mac a Linux.</span><span class="sxs-lookup"><span data-stu-id="a3370-128">This editor is a great fit for Mac and Linux developers.</span></span> <span data-ttu-id="a3370-129">Ve Windows také můžete použít celou aplikaci Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="a3370-129">In Windows, you also can use the full Visual Studio application.</span></span>

<span data-ttu-id="a3370-130">**Další informace o** pokyny k instalaci Visual Studio pro Windows, Mac nebo Linux, přejděte na <https://code.visualstudio.com/docs/setup/setup-overview/>.</span><span class="sxs-lookup"><span data-stu-id="a3370-130">**More info** For instructions on installing Visual Studio for Windows, Mac, or Linux, go to <https://code.visualstudio.com/docs/setup/setup-overview/>.</span></span>

<span data-ttu-id="a3370-131">Můžete pracovat pomocí rozhraní příkazového řádku Dockeru a napište svůj kód pomocí editoru kódu, ale pokud používáte Visual Studio Code, umožní snadno vytvořit soubor Dockerfile a soubory docker-compose.yml ve vašem pracovním prostoru.</span><span class="sxs-lookup"><span data-stu-id="a3370-131">You can work with Docker CLI and write your code using any code editor, but if you use Visual Studio Code, it makes it easy to author Dockerfile and docker-compose.yml files in your workspace.</span></span> <span data-ttu-id="a3370-132">Navíc můžete spouštět úlohy Visual Studio Code z integrovaného vývojového prostředí, který vás vyzve k skripty, které mohou běžet elaborované operací s použitím rozhraní příkazového řádku Dockeru pod.</span><span class="sxs-lookup"><span data-stu-id="a3370-132">Plus, you can run Visual Studio Code tasks from the IDE that will prompt scripts that can be running elaborated operations using Docker CLI underneath.</span></span>

<span data-ttu-id="a3370-133">Poskytuje rozšíření, které budete muset nainstalovat Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="a3370-133">Visual Studio Code is provided by an extension, which you'll need to install.</span></span> <span data-ttu-id="a3370-134">Chcete-li to provést, stiskněte kombinaci kláves Ctrl + Shift + P, zadejte **ext, přípona instalace**, a pak spusťte rozšíření: Instalace rozšíření příkazu zobrazíte seznam rozšíření Marketplace.</span><span class="sxs-lookup"><span data-stu-id="a3370-134">To do so, Press Ctrl+Shift+P, type **ext install**, and then run the Extensions: Install Extension command to bring up the Marketplace extension list.</span></span> <span data-ttu-id="a3370-135">Dále zadejte **docker** filtrování výsledků a potom vyberte soubor Dockerfile a Docker Compose souboru (yml) rozšíření podpory, jak je znázorněno v obrázek 4-16.</span><span class="sxs-lookup"><span data-stu-id="a3370-135">Next, type **docker** to filter the results, and then select the Dockerfile And Docker Compose File (yml) Support extension, as depicted in Figure 4-16.</span></span>

![](./media/image20.png)

<span data-ttu-id="a3370-136">Obrázek 4 – 16: Instaluje se rozšíření Dockeru v aplikaci Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="a3370-136">Figure 4-16: Installing the Docker Extension in Visual Studio Code</span></span>

### <a name="step-2-create-a-dockerfile-related-to-an-existing-image-plain-os-or-dev-environments-like-net-core-nodejs-and-ruby"></a><span data-ttu-id="a3370-137">Krok 2: Vytvoření souboru DockerFile související s existující image (plain operačního systému nebo vývoj prostředí, jako je .NET Core, Node.js a Ruby)</span><span class="sxs-lookup"><span data-stu-id="a3370-137">Step 2: Create a DockerFile related to an existing image (plain OS or dev environments like .NET Core, Node.js, and Ruby)</span></span>

<span data-ttu-id="a3370-138">Budete potřebovat soubor DockerFile na vlastní image má být sestaven a na kontejneru pro nasazení, proto pokud vaše aplikace se skládá z jedné vlastní službě, budete potřebovat jeden soubor DockerFile.</span><span class="sxs-lookup"><span data-stu-id="a3370-138">You will need a DockerFile per custom image to be built and per container to be deployed, therefore, if your app is made up of a single custom service, you will need a single DockerFile.</span></span> <span data-ttu-id="a3370-139">Ale pokud se vaše aplikace skládá z více služeb (stejně jako v architektuře mikroslužeb), budete potřebovat jeden soubor Dockerfile každou službu.</span><span class="sxs-lookup"><span data-stu-id="a3370-139">But, if your app is composed of multiple services (as in a microservices architecture), you'll need one Dockerfile per service.</span></span>

<span data-ttu-id="a3370-140">Soubor DockerFile je obvykle umístěn v kořenové složce aplikace nebo služby a obsahuje požadované příkazy tak, které Docker ví, jak nastavit a spustit aplikaci nebo službu.</span><span class="sxs-lookup"><span data-stu-id="a3370-140">The DockerFile is usually placed within the root folder of your app or service and contains the required commands so that Docker knows how to set up and run that app or service.</span></span> <span data-ttu-id="a3370-141">Můžete vytvořit váš soubor DockerFile a přidejte do projektu spolu s kódu (node.js, .NET Core, atd.), nebo pokud jsou pro vás nové prostředí, podívejte se na následující vrcholu.</span><span class="sxs-lookup"><span data-stu-id="a3370-141">You can create your DockerFile and add it to your project along with your code (node.js, .NET Core, etc.), or, if you are new to the environment, take a look at the following Tip.</span></span>

> [!TIP]
> <span data-ttu-id="a3370-142">Můžete použít nástroj příkazového řádku, který volá [yo docker](https://github.com/Microsoft/generator-docker), který vygeneruje uživatelské rozhraní soubory z projektu v jazyce, výběru a přidá požadované soubory konfigurace Dockeru.</span><span class="sxs-lookup"><span data-stu-id="a3370-142">You can use a command-line tool called [yo docker](https://github.com/Microsoft/generator-docker), which scaffolds files from your project in the language you choose and adds the required Docker configuration files.</span></span> <span data-ttu-id="a3370-143">V podstatě, abychom vývojářům Začínáme vytvoří odpovídající soubor DockerFile, docker-compose.yml a jiné přidružené skripty pro sestavení a spouští vaše kontejnery Dockeru.</span><span class="sxs-lookup"><span data-stu-id="a3370-143">Basically, to assist developers getting started, it creates the appropriate DockerFile, docker-compose.yml, and other associated scripts to build and run your Docker containers.</span></span> <span data-ttu-id="a3370-144">Tento generátor yeoman zobrazí výzvu na pár otázek, s výzvou hostitele vývoj pro vybraný jazyk a cílový kontejner.</span><span class="sxs-lookup"><span data-stu-id="a3370-144">This yeoman generator will prompt you with a few questions, asking your selected development language and destination container host.</span></span>

![Yo docker](./media/image21.png)

<span data-ttu-id="a3370-146">Například obrázek 4-17 ukazuje dvě snímky obrazovky z terminály ve Windows a na Macu, v obou případech se systémem yo docker, která bude generovat ukázkové kódové projekty (aktuálně .NET Core, go a Node.js jako seznam podporovaných jazyků) ještě nakonfigurováno pro práci na horní Dockeru.</span><span class="sxs-lookup"><span data-stu-id="a3370-146">For instance, Figure 4-17 shows two screenshots from the terminals in Windows and on a Mac, in both cases, running yo docker, which will generate the sample code projects (currently .NET Core, Golang, and Node.js as supported languages) already configured to work on top of Docker.</span></span>

![](./media/image22.PNG)  ![](./media/image23.png)

<span data-ttu-id="a3370-147">Obrázek 4 – 17: docker příkazu yo nástroje ve Windows (vlevo) a na Macu</span><span class="sxs-lookup"><span data-stu-id="a3370-147">Figure 4-17: yo docker command tool in Windows (left) and on a Mac</span></span>

<span data-ttu-id="a3370-148">Obrázek 4 – 18 představuje příklad použití yo docker až budete mít existující projekt .NET Core v místo, kde můžete být automaticky.</span><span class="sxs-lookup"><span data-stu-id="a3370-148">Figure 4-18 presents an example using yo docker after you have an existing .NET Core project in place to be scaffolded.</span></span>

![](./media/image24.PNG)

<span data-ttu-id="a3370-149">Obrázek 4 – 18: yo docker pomocí stávající .NET Core probíhá projekt</span><span class="sxs-lookup"><span data-stu-id="a3370-149">Figure 4-18: yo docker with an existing .NET Core project in place</span></span>

<span data-ttu-id="a3370-150">Ze souboru DockerFile zadejte co základní image Dockeru, který budete používat (například "FROM microsoft/dotnet:1.0.0-core").</span><span class="sxs-lookup"><span data-stu-id="a3370-150">From the DockerFile, you specify what base Docker image you'll be using (like using "FROM microsoft/dotnet:1.0.0-core").</span></span> <span data-ttu-id="a3370-151">Obvykle vytvoříte vlastní bitovou kopii nad základní image, který můžete získat z jakékoli oficiální úložiště [registru Docker Hub](https://hub.docker.com/) (stejně jako [bitovou kopii pro .NET Core](https://hub.docker.com/r/microsoft/dotnet/) nebo jeden [pro Node.js](https://hub.docker.com/_/node/)).</span><span class="sxs-lookup"><span data-stu-id="a3370-151">You usually will build your custom image on top of a base image that you can get from any official repository at the [Docker Hub registry](https://hub.docker.com/) (like an [image for .NET Core](https://hub.docker.com/r/microsoft/dotnet/) or one [for Node.js](https://hub.docker.com/_/node/)).</span></span>

<span data-ttu-id="a3370-152">***Možnost A: Použít existující oficiální image Dockeru***</span><span class="sxs-lookup"><span data-stu-id="a3370-152">***Option A: Use an existing official Docker image***</span></span>

<span data-ttu-id="a3370-153">Použití zásobníku jazyka oficiální úložiště s číslem verze zajistí, že stejné funkce jazyka jsou k dispozici na všech počítačích (včetně vývoje, testování a produkce).</span><span class="sxs-lookup"><span data-stu-id="a3370-153">Using an official repository of a language stack with a version number ensures that the same language features are available on all machines (including development, testing, and production).</span></span>

<span data-ttu-id="a3370-154">Následuje ukázkový soubor DockerFile pro .NET Core kontejneru:</span><span class="sxs-lookup"><span data-stu-id="a3370-154">Following is a sample DockerFile for a .NET Core container:</span></span>

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

<span data-ttu-id="a3370-155">V tomto případě používá verzi 1.0.1 oficiální image Dockeru ASP.NET Core pro Linux s názvem microsoft/aspnetcore:1.0.1.</span><span class="sxs-lookup"><span data-stu-id="a3370-155">In this case, it is using the version 1.0.1 of the official ASP.NET Core Docker image for Linux named microsoft/aspnetcore:1.0.1.</span></span> <span data-ttu-id="a3370-156">Pro další podrobnosti najdete [Image Dockeru ASP.NET Core stránky](https://hub.docker.com/r/microsoft/aspnetcore/) a [Image Dockeru .NET Core stránky](https://hub.docker.com/r/microsoft/dotnet/).</span><span class="sxs-lookup"><span data-stu-id="a3370-156">For further details, consult the [ASP.NET Core Docker Image page](https://hub.docker.com/r/microsoft/aspnetcore/) and the [.NET Core Docker Image page](https://hub.docker.com/r/microsoft/dotnet/).</span></span> <span data-ttu-id="a3370-157">Je také může použít jiné srovnatelné image jako uzel: 4-onbuild pro Node.js nebo mnoha jiných předem nakonfigurovaným imagím pro vývojářské jazyky, které jsou k dispozici v [Docker Hubu](https://hub.docker.com/explore/).</span><span class="sxs-lookup"><span data-stu-id="a3370-157">You also could be using another comparable image like node:4-onbuild for Node.js, or many other preconfigured images for development languages, which are available at [Docker Hub](https://hub.docker.com/explore/).</span></span>

<span data-ttu-id="a3370-158">V souboru DockerFile potřebujete také dáte pokyn, aby Docker nenaslouchá na portu TCP, který budete používat v době běhu (například port 80).</span><span class="sxs-lookup"><span data-stu-id="a3370-158">In the DockerFile, you also need to instruct Docker to listen to the TCP port that you will use at runtime (such as port 80).</span></span>

<span data-ttu-id="a3370-159">Existují další řádky konfigurace, které můžete přidat v souboru DockerFile v závislosti na jazyk a rozhraní, které používáte, takže Docker ví, jak spustit aplikaci.</span><span class="sxs-lookup"><span data-stu-id="a3370-159">There are other lines of configuration that you can add in the DockerFile depending on the language/framework you are using, so Docker knows how to run the app.</span></span> <span data-ttu-id="a3370-160">Pro instanci, potřebujete ENTRYPOINT uspokojování \["dotnet", "MyCustomMicroservice.dll"\] ke spuštění aplikace .NET Core, i když můžete mít více variant v závislosti na přístup k sestavení a spuštění služby.</span><span class="sxs-lookup"><span data-stu-id="a3370-160">For instance, you need the ENTRYPOINT line with \["dotnet", "MyCustomMicroservice.dll"\] to run a .NET Core app, although you can have multiple variants depending on the approach to build and run your service.</span></span> <span data-ttu-id="a3370-161">Pokud chcete sestavovat a spouštět aplikace .NET při použití sady SDK a rozhraní příkazového řádku dotnet, bylo by mírně liší.</span><span class="sxs-lookup"><span data-stu-id="a3370-161">If you're using the SDK and dotnet CLI to build and run the .NET app, it would be slightly different.</span></span> <span data-ttu-id="a3370-162">Dolní řádek je, že vstupní bod řádku plus další řádky budou lišit v závislosti na jazyk nebo platformu vybraných pro vaše aplikace.</span><span class="sxs-lookup"><span data-stu-id="a3370-162">The bottom line is that the ENTRYPOINT line plus additional lines will be different depending on the language/platform you choose for your application.</span></span>

<span data-ttu-id="a3370-163">**Další informace o** informace o vytváření imagí Dockeru pro aplikace .NET Core, přejděte na <https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images>.</span><span class="sxs-lookup"><span data-stu-id="a3370-163">**More info** For information about building Docker images for .NET Core applications, go to <https://docs.microsoft.com/dotnet/core/docker/building-net-docker-images>.</span></span>

<span data-ttu-id="a3370-164">Další informace o vytváření vlastních imagí, přejděte na [ https://docs.docker.com/engine/\ kurzy/dockerimages/](https://docs.docker.com/engine/tutorials/dockerimages/).</span><span class="sxs-lookup"><span data-stu-id="a3370-164">To learn more about building your own images, go to [https://docs.docker.com/engine/\ tutorials/dockerimages/](https://docs.docker.com/engine/tutorials/dockerimages/).</span></span>

<span data-ttu-id="a3370-165">**Úložiště s více platformami image**</span><span class="sxs-lookup"><span data-stu-id="a3370-165">**Multiplatform image repositories**</span></span>

<span data-ttu-id="a3370-166">Kontejnery Windows jsou více běžně se vyskytujícím, jednoho úložiště může obsahovat variant, platformy, jako jsou bitové kopie operačních systémů Linux a Windows.</span><span class="sxs-lookup"><span data-stu-id="a3370-166">As Windows containers become more prevalent, a single repository can contain platform variants, such as a Linux and Windows image.</span></span> <span data-ttu-id="a3370-167">Toto je nová funkce přicházející v Dockeru, který umožňuje dodavatelům použít jednoho úložiště pro různé platformy, například [microsoft/aspdotnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) úložiště, které je k dispozici na Dockerhubu registru.</span><span class="sxs-lookup"><span data-stu-id="a3370-167">This is a new feature coming in Docker that makes it possible for vendors to use a single repository to cover multiple platforms, such as [microsoft/aspdotnetcore](https://hub.docker.com/r/microsoft/aspnetcore/) repository, which is available at DockerHub registry.</span></span> <span data-ttu-id="a3370-168">Jako funkci přicházejí k životu, přebírání tuto bitovou kopii z hostitele Windows přetáhne Windows variant, zatímco přebírání stejný název image z hostitele platformy Linux přetáhne varianty Linuxu.</span><span class="sxs-lookup"><span data-stu-id="a3370-168">As the feature comes alive, pulling this image from a Windows host will pull the Windows variant, whereas pulling the same image name from a Linux host will pull the Linux variant.</span></span>

<span data-ttu-id="a3370-169">***Možnost B: Vytvoření zcela nové základní image***</span><span class="sxs-lookup"><span data-stu-id="a3370-169">***Option B: Create your base image from scratch***</span></span>

<span data-ttu-id="a3370-170">Můžete vytvořit vlastní základní image Dockeru od začátku, jak je popsáno v tomto [článku](https://docs.docker.com/engine/userguide/eng-image/baseimages/) od Dockeru.</span><span class="sxs-lookup"><span data-stu-id="a3370-170">You can create your own Docker base image from scratch as explained in this [article](https://docs.docker.com/engine/userguide/eng-image/baseimages/) from Docker.</span></span> <span data-ttu-id="a3370-171">Scénář, který je pravděpodobně není pro vás nejvhodnější, pokud právě začínáte s Dockerem, ale pokud chcete nastavit konkrétní bity základní image, můžete to provést.</span><span class="sxs-lookup"><span data-stu-id="a3370-171">This is a scenario that is probably not best for you if you are just starting with Docker, but if you want to set the specific bits of your own base image, you can do it.</span></span>

### <a name="step-3-create-your-custom-docker-images-embedding-your-service-in-it"></a><span data-ttu-id="a3370-172">Krok 3: Vytvoření vlastní Image Dockeru vložení služby</span><span class="sxs-lookup"><span data-stu-id="a3370-172">Step 3: Create your custom Docker images embedding your service in it</span></span>

<span data-ttu-id="a3370-173">U každé aplikace se skládá z vlastní služby budete muset vytvořit související image.</span><span class="sxs-lookup"><span data-stu-id="a3370-173">For each custom service that comprises your app, you'll need to create a related image.</span></span> <span data-ttu-id="a3370-174">Pokud vaše aplikace skládá z jedné služby nebo webové aplikace, budete potřebovat jenom jedné image.</span><span class="sxs-lookup"><span data-stu-id="a3370-174">If your app is made up of a single service or web app, you'll need just a single image.</span></span>

> [!NOTE]
> <span data-ttu-id="a3370-175">Když se vezme v úvahu "workflow pro DevOps vnější smyčky", Image se vytvoří pomocí automatizovaného procesu sestavení pokaždé, když nahrajete váš zdrojový kód do úložiště Git (průběžná integrace), obrázky budou vytvořeny v globálním prostředí z vaší zdrojový kód.</span><span class="sxs-lookup"><span data-stu-id="a3370-175">When taking into account the "outer-loop DevOps workflow," the images will be created by an automated build process whenever you push your source code to a Git repository (Continuous Integration) so the images will be created in that global environment from your source code.</span></span>

<span data-ttu-id="a3370-176">Ale předtím, než jsme zvažte, že přejdete na tuto trasu vnější smyčky, potřebujeme zajistit, že aplikace Dockeru ve skutečnosti funguje správně tak, aby jejich není push kód, který nemusí správně fungovat do systému správy zdrojového kódu (Git atd.).</span><span class="sxs-lookup"><span data-stu-id="a3370-176">But, before we consider going to that outer-loop route, we need to ensure that the Docker application is actually working properly so that they don't push code that might not work properly to the source control system (Git, etc.).</span></span>

<span data-ttu-id="a3370-177">Každý vývojář proto nejprve musí udělat celý proces vnitřní smyčky, místně ji otestovat a pokračovat ve vývoji, dokud chtějí push kompletní funkce nebo změňte na systém správy zdrojového kódu.</span><span class="sxs-lookup"><span data-stu-id="a3370-177">Therefore, each developer first needs to do the entire inner-loop process to test locally and continue developing until they want to push a complete feature or change to the source control system.</span></span>

<span data-ttu-id="a3370-178">Pro vytvoření image v místním prostředí a pomocí souboru DockerFile, můžete použít příkaz sestavení dockeru, jak je ukázáno v obrázek 4-19 (můžete také spustit docker-compose up – sestavení pro aplikace, které sestává z několika kontejnerů nebo služeb Team Foundation).</span><span class="sxs-lookup"><span data-stu-id="a3370-178">To create an image in your local environment and using the DockerFile, you can use the docker build command, as demonstrated in Figure 4-19 (you also can run docker-compose up --build for applications composed by several containers/services).</span></span>

![](./media/image25.png)

<span data-ttu-id="a3370-179">Obrázek 4 – 19: Spouštění sestavení dockeru</span><span class="sxs-lookup"><span data-stu-id="a3370-179">Figure 4-19: Running docker build</span></span>

<span data-ttu-id="a3370-180">Volitelně můžete místo přímo spouštět docker sestavení ze složky projektu, nejprve můžete vygenerovat nasaditelný složku s knihovnami .NET, třeba pomocí spuštění dotnet příkazu pro publikování a pak spusťte sestavení dockeru.</span><span class="sxs-lookup"><span data-stu-id="a3370-180">Optionally, instead of directly running docker build from the project's folder, you first can generate a deployable folder with the .NET libraries needed by using the run dotnet publish command, and then run docker build.</span></span>

<span data-ttu-id="a3370-181">V tomto příkladu, tím se vytvoří image Dockeru s název cesardl/netcore-webapi mikroslužeb – docker: first (: nejprve je značka, jako jsou konkrétní verzi).</span><span class="sxs-lookup"><span data-stu-id="a3370-181">In this example, this creates a Docker image with the name cesardl/netcore-webapi-microservice-docker:first (:first is a tag, like a specific version).</span></span> <span data-ttu-id="a3370-182">Je-li provést tento krok pro každou vlastní image, které je potřeba vytvořit složené aplikace Dockeru s několika kontejnery.</span><span class="sxs-lookup"><span data-stu-id="a3370-182">You can take this step for each custom image you need to create for your composed Docker application with several containers.</span></span>

<span data-ttu-id="a3370-183">Najdete existujících bitových kopií ve vašem místním úložišti (vývojovém počítači) s využitím dockeru příkaz bitové kopie, jak je znázorněno na obrázku 4-20.</span><span class="sxs-lookup"><span data-stu-id="a3370-183">You can find the existing images in your local repository (your development machine) by using the docker images command, as illustrated in Figure 4-20.</span></span>

![](./media/image26.png)

<span data-ttu-id="a3370-184">Obrázek 4-20: Zobrazení existujících obrázků s využitím Image dockeru</span><span class="sxs-lookup"><span data-stu-id="a3370-184">Figure 4-20: Viewing existing images using docker images</span></span>

### <a name="step-4-optional-define-your-services-in-docker-composeyml-when-building-a-composed-docker-app-with-multiple-services"></a><span data-ttu-id="a3370-185">Krok 4: (Volitelné) Definování vašich služeb v docker-compose.yml při vytváření složené aplikace Dockeru s více službami</span><span class="sxs-lookup"><span data-stu-id="a3370-185">Step 4: (Optional) Define your services in docker-compose.yml when building a composed Docker app with multiple services</span></span>

<span data-ttu-id="a3370-186">Pomocí souboru docker-compose.yml můžete definovat sadu souvisejících služeb umožňující nasadit ho jako aplikace skládá pomocí příkazů nasazení je vysvětleno v další části kroku.</span><span class="sxs-lookup"><span data-stu-id="a3370-186">With the docker-compose.yml file you can define a set of related services to be deployed as a composed application with the deployment commands explained in the next step section.</span></span>

<span data-ttu-id="a3370-187">Je potřeba vytvořit tento soubor do vašeho hlavního nebo kořenové složky řešení; do následujícího souboru docker-compose.yml to měl být podobný obsah:</span><span class="sxs-lookup"><span data-stu-id="a3370-187">You need to create that file in your main or root solution folder; it should have a similar content to the following docker-compose.yml file:</span></span>

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

<span data-ttu-id="a3370-188">V tomto konkrétním případě tento soubor definuje dvě služby: webové služby (vaše vlastní služba) a službu redis (Oblíbené mezipaměti služby).</span><span class="sxs-lookup"><span data-stu-id="a3370-188">In this particular case, this file defines two services: the web service (your custom service) and the redis service (a popular cache service).</span></span> <span data-ttu-id="a3370-189">Každá služba se nasadí jako kontejner, proto musíme pomocí konkrétní image Dockeru pro každý.</span><span class="sxs-lookup"><span data-stu-id="a3370-189">Each service will be deployed as a container, so we need to use a concrete Docker image for each.</span></span> <span data-ttu-id="a3370-190">Pro tento konkrétní webovou službu na obrázku potřebovat provést následující kroky:</span><span class="sxs-lookup"><span data-stu-id="a3370-190">For this particular web service, the image will need to do the following:</span></span>

-   <span data-ttu-id="a3370-191">Sestavení z soubor DockerFile v aktuálním adresáři</span><span class="sxs-lookup"><span data-stu-id="a3370-191">Build from the DockerFile in the current directory</span></span>

-   <span data-ttu-id="a3370-192">Dál vystavené port 80 v kontejneru na port 81 na hostitelském počítači</span><span class="sxs-lookup"><span data-stu-id="a3370-192">Forward the exposed port 80 on the container to port 81 on the host machine</span></span>

-   <span data-ttu-id="a3370-193">Připojení adresáře projektu v hostiteli /code v rámci kontejneru, takže budete moct změnit kód bez nutnosti znovu sestavovat image</span><span class="sxs-lookup"><span data-stu-id="a3370-193">Mount the project directory on the host to /code within the container, making it possible for you to modify the code without having to rebuild the image</span></span>

-   <span data-ttu-id="a3370-194">Odkaz webové služby ke službě redis</span><span class="sxs-lookup"><span data-stu-id="a3370-194">Link the web service to the redis service</span></span>

<span data-ttu-id="a3370-195">Použití služby redis [nejnovější veřejné redis image](https://hub.docker.com/_/redis/) získaných z registru Docker Hub.</span><span class="sxs-lookup"><span data-stu-id="a3370-195">The redis service uses the [latest public redis image](https://hub.docker.com/_/redis/) pulled from the Docker Hub registry.</span></span> <span data-ttu-id="a3370-196">[redis](https://redis.io/) je systém velmi populární mezipaměti pro aplikace na straně serveru.</span><span class="sxs-lookup"><span data-stu-id="a3370-196">[redis](https://redis.io/) is a very popular cache system for server-side applications.</span></span>

### <a name="step-5-build-and-run-your-docker-app"></a><span data-ttu-id="a3370-197">Krok 5: Sestavení a spuštění aplikace Dockeru</span><span class="sxs-lookup"><span data-stu-id="a3370-197">Step 5: Build and run your Docker app</span></span>

<span data-ttu-id="a3370-198">Pokud vaše aplikace má pouze jeden kontejner, stačí ji spustit nasazení na hostitele Docker (virtuální počítač nebo fyzický server).</span><span class="sxs-lookup"><span data-stu-id="a3370-198">If your app has only a single container, you just need to run it by deploying it to your Docker Host (VM or physical server).</span></span> <span data-ttu-id="a3370-199">Nicméně pokud vaše aplikace se skládá z několika služeb, budete muset *tvoří ji*také.</span><span class="sxs-lookup"><span data-stu-id="a3370-199">However, if your app is made up of multiple services, you need to *compose it*, too.</span></span> <span data-ttu-id="a3370-200">Podívejme se na různé možnosti.</span><span class="sxs-lookup"><span data-stu-id="a3370-200">Let's see the different options.</span></span>

<span data-ttu-id="a3370-201">***Možnost A: Spustit jedním kontejnerem nebo služby***</span><span class="sxs-lookup"><span data-stu-id="a3370-201">***Option A: Run a single container or service***</span></span>

<span data-ttu-id="a3370-202">Image Dockeru můžete spustit pomocí dockeru, spusťte příkaz, jak je znázorněno zde:</span><span class="sxs-lookup"><span data-stu-id="a3370-202">You can run the Docker image by using the docker run command, as shown here:</span></span>

```
docker run -t -d -p 80:5000
cesardl/netcore-webapi-microservice-docker:first
```

<span data-ttu-id="a3370-203">Všimněte si, že pro toto konkrétní nasazení jsme budete se přesměruje požadavky odeslané na portu 80 na interní port 5000.</span><span class="sxs-lookup"><span data-stu-id="a3370-203">Note that for this particular deployment, we'll be redirecting requests sent to port 80 to the internal port 5000.</span></span> <span data-ttu-id="a3370-204">Aplikace teď naslouchá na externím portu 80 na úrovni hostitele.</span><span class="sxs-lookup"><span data-stu-id="a3370-204">Now, the application is listening on the external port 80 at the host level.</span></span>

<span data-ttu-id="a3370-205">***Možnost B: Vytvářet a spouštět aplikace typu kontejner více***</span><span class="sxs-lookup"><span data-stu-id="a3370-205">***Option B: Compose and run a multiple-container application***</span></span>

<span data-ttu-id="a3370-206">Ve většině scénářů organizace aplikaci v Dockeru se skládá z více služeb.</span><span class="sxs-lookup"><span data-stu-id="a3370-206">In most enterprise scenarios, a Docker application will be composed of multiple services.</span></span> <span data-ttu-id="a3370-207">Pro tyto případy můžete spuštění příkazu docker-compose up (obrázek 4 – 21), které použije soubor docker-compose.yml, kterou může jste vytvořili dříve.</span><span class="sxs-lookup"><span data-stu-id="a3370-207">For these cases, you can run the command docker-compose up (Figure 4-21), which will use the docker-compose.yml file that you might have created previously.</span></span> <span data-ttu-id="a3370-208">Spustí tento příkaz nasadí složené aplikaci se všemi jeho související kontejnerů.</span><span class="sxs-lookup"><span data-stu-id="a3370-208">Running this command deploys a composed application with all of its related containers.</span></span>

![](./media/image27.png)

<span data-ttu-id="a3370-209">Obrázek 4 – 21: Výsledky spuštění příkazu "docker-compose up"</span><span class="sxs-lookup"><span data-stu-id="a3370-209">Figure 4-21: Results of running the "docker-compose up" command</span></span>

<span data-ttu-id="a3370-210">Po spuštění docker-compose up, budete nasazovat aplikace a její související kontejnerů do hostitele Dockeru, jak ukazuje obrázek 4 – 22 reprezentaci virtuálního počítače.</span><span class="sxs-lookup"><span data-stu-id="a3370-210">After you run docker-compose up, you deploy your application and its related container(s) into your Docker Host, as illustrated in Figure 4-22, in the VM representation.</span></span>

![](./media/image28.png)

<span data-ttu-id="a3370-211">Obrázek 4 – 22: Virtuální počítač s kontejnery Dockeru nasazené</span><span class="sxs-lookup"><span data-stu-id="a3370-211">Figure 4-22: VM with Docker containers deployed</span></span>

<span data-ttu-id="a3370-212">Poznámka: docker-compose up a docker, spusťte mohou být dostatečné k testování kontejnerů ve vašem vývojovém prostředí, ale pokud očekáváte pro práci s clustery Dockeru a orchestrátorů, jako je Docker Swarm, Mesosphere DC/OS nebo Kubernetes je nemusí použít na všech aby bylo možné vertikálně navýšit kapacitu.</span><span class="sxs-lookup"><span data-stu-id="a3370-212">Note docker-compose up and docker run might be enough for testing your containers in your development environment, but you might not use them at all if you are expecting to work with Docker clusters and orchestrators like Docker Swarm, Mesosphere DC/OS, or Kubernetes in order to be able to scale up.</span></span> <span data-ttu-id="a3370-213">Pokud používáte cluster jako [režim Docker Swarm](https://docs.docker.com/engine/swarm/) (k dispozici v Docker pro Windows a Mac od verze 1.12), musíte nasadit a testovat pomocí dalších příkazů, jako je služba docker vytvořit pro jednu službu nebo pokud jste nasazení aplikace skládá z několika kontejnerů pomocí docker compose svazku a docker nasazení myBundleFile, nasazením složené aplikace jako zásobník, jak je popsáno v článku [distribuované aplikace sady](https://blog.docker.com/2016/06/docker-app-bundle/) od Dockeru.</span><span class="sxs-lookup"><span data-stu-id="a3370-213">If you're using a cluster like [Docker Swarm mode](https://docs.docker.com/engine/swarm/) (available in Docker for Windows and Mac since version 1.12), you need to deploy and test with additional commands such as docker service create for single services, or when you're deploying an app composed of several containers, using docker compose bundle and docker deploy myBundleFile, by deploying the composed app as a stack, as explained in the article [Distributed Application Bundles](https://blog.docker.com/2016/06/docker-app-bundle/) from Docker.</span></span>

<span data-ttu-id="a3370-214">Pro [DC/OS](https://mesosphere.com/blog/2015/09/02/dcos-cli-command-line-tool-datacenter/) a [Kubernetes](https://kubernetes.io/docs/user-guide/deployments/#creating-a-deployment) použijete jiné nasazení příkazy a skripty, také.</span><span class="sxs-lookup"><span data-stu-id="a3370-214">For [DC/OS](https://mesosphere.com/blog/2015/09/02/dcos-cli-command-line-tool-datacenter/) and [Kubernetes](https://kubernetes.io/docs/user-guide/deployments/#creating-a-deployment) you would use different deployment commands and scripts, as well.</span></span>

### <a name="step-6-test-your-docker-application-locally-in-your-local-cd-vm"></a><span data-ttu-id="a3370-215">Krok 6: Otestujte aplikaci Docker (místně, v místní virtuální počítač CD)</span><span class="sxs-lookup"><span data-stu-id="a3370-215">Step 6: Test your Docker application (locally, in your local CD VM)</span></span>

<span data-ttu-id="a3370-216">Tento krok se liší v závislosti na tom, co vaše aplikace stojí.</span><span class="sxs-lookup"><span data-stu-id="a3370-216">This step will vary depending on what your app is doing.</span></span>

<span data-ttu-id="a3370-217">Ve velmi jednoduché rozhraní .NET Core webového rozhraní API "Hello World" nasadit jako jedním kontejnerem nebo služby by stačí pro přístup ke službě zadáním TCP port zadaný v souboru DockerFile.</span><span class="sxs-lookup"><span data-stu-id="a3370-217">In a very simple .NET Core Web API "Hello World" deployed as a single container or service, you'd just need to access the service by providing the TCP port specified in the DockerFile.</span></span>

<span data-ttu-id="a3370-218">Pokud localhost není zapnutý, přejděte k vaší službě zjistit IP adresu počítače pomocí tohoto příkazu:</span><span class="sxs-lookup"><span data-stu-id="a3370-218">If localhost is not turned on, to navigate to your service, find the IP address for the machine by using this command:</span></span>

<span data-ttu-id="a3370-219">docker-machine ip *svůj název kontejneru*</span><span class="sxs-lookup"><span data-stu-id="a3370-219">docker-machine ip *your-container-name*</span></span>

<span data-ttu-id="a3370-220">Na hostitele Docker spusťte prohlížeč a přejděte na web; vaše aplikace nebo služby spuštěné, měli byste vidět, jak je ukázáno v obrázek 4 – 23.</span><span class="sxs-lookup"><span data-stu-id="a3370-220">On the Docker host, open a browser and navigate to that site; you should see your app/service running, as demonstrated in Figure 4-23.</span></span>

![](./media/image29.png)

<span data-ttu-id="a3370-221">Obrázek 4 – 23: Testování aplikace místně s použitím místního hostitele Docker</span><span class="sxs-lookup"><span data-stu-id="a3370-221">Figure 4-23: Testing your Docker application locally using localhost</span></span>

<span data-ttu-id="a3370-222">Všimněte si, že používá port 80, ale interně byl přesměrován na portu 5000, protože to je, jak nasazení pomocí dockeru spustíte tak, jak je vysvětleno výše.</span><span class="sxs-lookup"><span data-stu-id="a3370-222">Note that it is using port 80, but internally it was being redirected to port 5000, because that's how it was deployed with docker run, as explained earlier.</span></span>

<span data-ttu-id="a3370-223">Můžete ho otestovat pomocí příkazu CURL z terminálu.</span><span class="sxs-lookup"><span data-stu-id="a3370-223">You can test this by using CURL from the terminal.</span></span> <span data-ttu-id="a3370-224">V instalaci Dockeru na Windows je výchozí IP 10.0.75.1, jak je znázorněno v obrázek 4 – 24.</span><span class="sxs-lookup"><span data-stu-id="a3370-224">In a Docker installation on Windows, the default IP is 10.0.75.1, as depicted in Figure 4-24.</span></span>

![](./media/image30.png)

<span data-ttu-id="a3370-225">Obrázek 4 – 24: Testování aplikace Docker místně pomocí CURL</span><span class="sxs-lookup"><span data-stu-id="a3370-225">Figure 4-24: Testing a Docker application locally by using CURL</span></span>

<span data-ttu-id="a3370-226">**Ladění kontejneru spuštěného v Dockeru**</span><span class="sxs-lookup"><span data-stu-id="a3370-226">**Debugging a container running on Docker**</span></span>

<span data-ttu-id="a3370-227">Visual Studio Code podporuje ladění Dockeru, pokud používáte Node.js a jiných platformách, jako je .NET Core kontejnery.</span><span class="sxs-lookup"><span data-stu-id="a3370-227">Visual Studio Code supports debugging Docker if you're using Node.js and other platforms like .NET Core containers.</span></span>

<span data-ttu-id="a3370-228">Můžete také ladit kontejnery .NET Core v Dockeru při používání sady Visual Studio, jak je popsáno v další části.</span><span class="sxs-lookup"><span data-stu-id="a3370-228">You also can debug .NET Core containers in Docker when using Visual Studio, as described in the next section.</span></span>

<span data-ttu-id="a3370-229">**Další informace:** Další informace o ladění kontejnerů Dockeru Node.js, přejděte na <https://blog.docker.com/2016/07/live-debugging-docker/> a [ https://blogs.msdn.microsoft.com/\ uživatele\_ed/2016/02/27 nebo Visual-Studio-Code-New-features-13-Big-Debugging-Updates-Rich-Object-hover-Conditional-breakpoints-node-js-mono-more/](https://blogs.msdn.microsoft.com/user_ed/2016/02/27/visual-studio-code-new-features-13-big-debugging-updates-rich-object-hover-conditional-breakpoints-node-js-mono-more/).</span><span class="sxs-lookup"><span data-stu-id="a3370-229">**More info:** To learn more about debugging Node.js Docker containers, go to <https://blog.docker.com/2016/07/live-debugging-docker/> and [https://blogs.msdn.microsoft.com/\ user\_ed/2016/02/27/visual-studio-code-new-features-13-big-debugging-updates-rich-object-hover-conditional-breakpoints-node-js-mono-more/](https://blogs.msdn.microsoft.com/user_ed/2016/02/27/visual-studio-code-new-features-13-big-debugging-updates-rich-object-hover-conditional-breakpoints-node-js-mono-more/).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="a3370-230">[Předchozí](docker-apps-development-environment.md)
>[další](visual-studio-tools-for-docker.md)</span><span class="sxs-lookup"><span data-stu-id="a3370-230">[Previous](docker-apps-development-environment.md)
[Next](visual-studio-tools-for-docker.md)</span></span>