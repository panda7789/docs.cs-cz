---
title: "Vytváření bitových kopií Docker .NET Core"
description: "Seznámení s imagí Dockeru a .NET Core"
keywords: "Rozhraní .NET, rozhraní .NET core, Docker"
author: jralexander
ms.author: johalex
ms.date: 11/06/2017
ms.topic: tutorial
ms.prod: .net-core
ms.technology: dotnet-docker
ms.devlang: dotnet
ms.assetid: 03c28597-7e73-46d6-a9c3-f9cb55642739
ms.custom: mvc
manager: wpickett
ms.openlocfilehash: 3ec2d5a58b46e332de41b618f1c3fac663b29bee
ms.sourcegitcommit: 5fb6646b5ee3769ffb214e672041833ea4ceeb26
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/08/2017
---
# <a name="building-docker-images-for-net-core-applications"></a><span data-ttu-id="c5ac6-104">Vytváření Imagí Dockeru pro aplikace .NET Core</span><span class="sxs-lookup"><span data-stu-id="c5ac6-104">Building Docker Images for .NET Core Applications</span></span>

 <span data-ttu-id="c5ac6-105">V tomto kurzu zaměříme na použití .NET Core na Docker.</span><span class="sxs-lookup"><span data-stu-id="c5ac6-105">In this tutorial, We focus on how to use .NET Core on Docker.</span></span> <span data-ttu-id="c5ac6-106">Nejdřív jsme prozkoumejte různé imagí Dockeru nabízí a spravován společností Microsoft a případy použití.</span><span class="sxs-lookup"><span data-stu-id="c5ac6-106">First, we explore the different Docker images offered and maintained by Microsoft, and use cases.</span></span> <span data-ttu-id="c5ac6-107">Potom jsme zjistěte, jak vytvářet a dockerize aplikace ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="c5ac6-107">We then learn how to build and dockerize an ASP.NET Core app.</span></span>

<span data-ttu-id="c5ac6-108">V průběhu tohoto kurzu se seznámíte:</span><span class="sxs-lookup"><span data-stu-id="c5ac6-108">During the course of this tutorial, you learn:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="c5ac6-109">Další informace o rozhraní Microsoft .NET Core Docker obrázků</span><span class="sxs-lookup"><span data-stu-id="c5ac6-109">Learn about Microsoft .NET Core Docker images</span></span> 
> * <span data-ttu-id="c5ac6-110">Získat ukázkovou aplikaci k Dockerize ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="c5ac6-110">Get an ASP.NET Core sample app to Dockerize</span></span>
> * <span data-ttu-id="c5ac6-111">Místní spuštění ukázkové aplikace ASP.NET</span><span class="sxs-lookup"><span data-stu-id="c5ac6-111">Run the ASP.NET sample app locally</span></span>
> * <span data-ttu-id="c5ac6-112">Sestavení a spuštění vzorového Linux kontejnerů pomocí Docker</span><span class="sxs-lookup"><span data-stu-id="c5ac6-112">Build and run the sample with Docker for Linux containers</span></span>
> * <span data-ttu-id="c5ac6-113">Sestavení a spuštění vzorového s kontejnery Docker pro Windows</span><span class="sxs-lookup"><span data-stu-id="c5ac6-113">Build and run the sample with Docker for Windows containers</span></span>

## <a name="docker-image-optimizations"></a><span data-ttu-id="c5ac6-114">Optimalizace na obrázku docker</span><span class="sxs-lookup"><span data-stu-id="c5ac6-114">Docker Image Optimizations</span></span>

<span data-ttu-id="c5ac6-115">Při vytváření imagí Dockeru pro vývojáře, zaměřili jsme se na třech hlavních scénářích:</span><span class="sxs-lookup"><span data-stu-id="c5ac6-115">When building Docker images for developers, we focused on three main scenarios:</span></span>

* <span data-ttu-id="c5ac6-116">Obrázků použitých k vývoji aplikací .NET Core</span><span class="sxs-lookup"><span data-stu-id="c5ac6-116">Images used to develop .NET Core apps</span></span>
* <span data-ttu-id="c5ac6-117">Bitové kopie sloužící k vytvoření aplikace .NET Core</span><span class="sxs-lookup"><span data-stu-id="c5ac6-117">Images used to build .NET Core apps</span></span>
* <span data-ttu-id="c5ac6-118">Bitové kopie používá ke spouštění aplikací .NET Core</span><span class="sxs-lookup"><span data-stu-id="c5ac6-118">Images used to run .NET Core apps</span></span>

<span data-ttu-id="c5ac6-119">Proč tři Image?</span><span class="sxs-lookup"><span data-stu-id="c5ac6-119">Why three images?</span></span>
<span data-ttu-id="c5ac6-120">Při vyvíjení, vytváření a běh aplikací kontejnerizované, máme různých priorit.</span><span class="sxs-lookup"><span data-stu-id="c5ac6-120">When developing, building, and running containerized applications, we have different priorities.</span></span>

* <span data-ttu-id="c5ac6-121">**Vývoj:** se zaměřuje priority na rychle iterovat změny a možnost ladění změny.</span><span class="sxs-lookup"><span data-stu-id="c5ac6-121">**Development:**  The priority focuses on quickly iterate changes, and the ability to debug the changes.</span></span> <span data-ttu-id="c5ac6-122">Velikost bitové kopie není jako důležité, místo můžete provádět změny kódu a rychle vidět?</span><span class="sxs-lookup"><span data-stu-id="c5ac6-122">The size of the image isn't as important, rather can you make changes to your code and see them quickly?</span></span>

* <span data-ttu-id="c5ac6-123">**Sestavení:** tato bitová kopie obsahuje vše potřebné ke kompilaci aplikace, která zahrnuje kompilátor a další závislosti za účelem optimalizace binární soubory.</span><span class="sxs-lookup"><span data-stu-id="c5ac6-123">**Build:** This image contains everything needed to compile your app, which includes the compiler and any other dependencies to optimize the binaries.</span></span>  <span data-ttu-id="c5ac6-124">Bitovou kopii sestavení použijete k vytvoření prostředků, které umístíte do bitové kopie produkční.</span><span class="sxs-lookup"><span data-stu-id="c5ac6-124">You use the build image to create the assets you place into a production image.</span></span> <span data-ttu-id="c5ac6-125">Sestavení image se použije pro nepřetržitou integraci, nebo v prostředí sestavení.</span><span class="sxs-lookup"><span data-stu-id="c5ac6-125">The build image would be used for continuous integration, or in a build environment.</span></span> <span data-ttu-id="c5ac6-126">Tento přístup umožňuje sestavení agenta pro zkompilování a vybuildování aplikace (s všechny požadované závislosti) v instanci sestavení bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="c5ac6-126">This approach allows a build agent to compile and build the application (with all the required dependencies) in a build image instance.</span></span> <span data-ttu-id="c5ac6-127">Agenta sestavení pouze musí vědět, jak spustit tento Docker image.</span><span class="sxs-lookup"><span data-stu-id="c5ac6-127">Your build agent only needs to know how to run this Docker image.</span></span>

* <span data-ttu-id="c5ac6-128">**Produkční:** rychlost můžete nasadit a spustit image?</span><span class="sxs-lookup"><span data-stu-id="c5ac6-128">**Production:** How fast you can deploy and start your image?</span></span> <span data-ttu-id="c5ac6-129">Tento image je malý, takže je optimalizován výkon sítě z registru Docker do hostitelů Docker.</span><span class="sxs-lookup"><span data-stu-id="c5ac6-129">This image is small so network performance from your Docker Registry to your Docker hosts is optimized.</span></span> <span data-ttu-id="c5ac6-130">Obsah je připraven ke spuštění povolení nejrychlejší čas z Docker spustit, aby se zpracování výsledků.</span><span class="sxs-lookup"><span data-stu-id="c5ac6-130">The contents are ready to run enabling the fastest time from Docker run to processing results.</span></span> <span data-ttu-id="c5ac6-131">Kompilace dynamický kód není potřeba mít ve Docker model.</span><span class="sxs-lookup"><span data-stu-id="c5ac6-131">Dynamic code compilation isn't needed in the Docker model.</span></span> <span data-ttu-id="c5ac6-132">Obsah, který můžete umístit na tomto obrázku bude omezeno na binární soubory a obsah potřebné ke spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="c5ac6-132">The content you place in this image would be limited to the binaries and content needed to run the application.</span></span>

    <span data-ttu-id="c5ac6-133">Například `dotnet publish` výstup obsahuje:</span><span class="sxs-lookup"><span data-stu-id="c5ac6-133">For example, the `dotnet publish` output contains:</span></span>

    * <span data-ttu-id="c5ac6-134">kompilované binární soubory</span><span class="sxs-lookup"><span data-stu-id="c5ac6-134">the compiled binaries</span></span>
    * <span data-ttu-id="c5ac6-135">soubory .js a .css</span><span class="sxs-lookup"><span data-stu-id="c5ac6-135">.js and .css files</span></span>


<span data-ttu-id="c5ac6-136">Z důvodu zahrnout `dotnet publish` výstupu příkazu v bitové kopii produkčního je zachování jeho ' velikost na minimum.</span><span class="sxs-lookup"><span data-stu-id="c5ac6-136">The reason to include the `dotnet publish` command output in your production image is to keep its' size to a minimum.</span></span>

<span data-ttu-id="c5ac6-137">Některé obrázky, .NET Core sdílet vrstvy mezi různé značky, stahuje nejnovější značky je relativně jednoduché proces.</span><span class="sxs-lookup"><span data-stu-id="c5ac6-137">Some .NET Core images share layers between different tags so downloading the latest tag is a relatively lightweight process.</span></span> <span data-ttu-id="c5ac6-138">Pokud již máte starší verze na počítači, sníží tato architektura místo na disku potřebné.</span><span class="sxs-lookup"><span data-stu-id="c5ac6-138">If you already have an older version on your machine, this architecture decreases the needed disk space.</span></span>

<span data-ttu-id="c5ac6-139">Když se více aplikací používat běžné bitové kopie na stejném počítači, paměti jsou sdílena mezi běžné bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="c5ac6-139">When multiple applications use common images on the same machine, memory is shared between the common images.</span></span> <span data-ttu-id="c5ac6-140">Image se musí shodovat s ke sdílení.</span><span class="sxs-lookup"><span data-stu-id="c5ac6-140">The images must be the same to be shared.</span></span>

## <a name="docker-image-variations"></a><span data-ttu-id="c5ac6-141">Variace docker bitové kopie</span><span class="sxs-lookup"><span data-stu-id="c5ac6-141">Docker image variations</span></span>

<span data-ttu-id="c5ac6-142">K dosažení výše uvedené cíle, poskytujeme variant bitové kopie v rámci [ `microsoft/dotnet` ](https://hub.docker.com/r/microsoft/dotnet/).</span><span class="sxs-lookup"><span data-stu-id="c5ac6-142">To achieve the goals above, we provide image variants under [`microsoft/dotnet`](https://hub.docker.com/r/microsoft/dotnet/).</span></span>

* <span data-ttu-id="c5ac6-143">`microsoft/dotnet:<version>-sdk`(`microsoft/dotnet:2.0.0-sdk`) Tato bitová kopie obsahuje .NET Core SDK, která zahrnuje .NET Core a nástroje příkazového řádku (CLI).</span><span class="sxs-lookup"><span data-stu-id="c5ac6-143">`microsoft/dotnet:<version>-sdk`(`microsoft/dotnet:2.0.0-sdk`) This image contains the .NET Core SDK, which includes the .NET Core and Command Line Tools (CLI).</span></span> <span data-ttu-id="c5ac6-144">Tuto bitovou kopii se mapuje **vývoj scénář**.</span><span class="sxs-lookup"><span data-stu-id="c5ac6-144">This image maps to the **development scenario**.</span></span> <span data-ttu-id="c5ac6-145">Můžete použít tuto bitovou kopii pro místní vývoj, ladění a testování částí.</span><span class="sxs-lookup"><span data-stu-id="c5ac6-145">You use this image for local development, debugging, and unit testing.</span></span> <span data-ttu-id="c5ac6-146">Tuto bitovou kopii lze také použít pro vaše **sestavení** scénáře.</span><span class="sxs-lookup"><span data-stu-id="c5ac6-146">This image can also be used for your **build** scenarios.</span></span> <span data-ttu-id="c5ac6-147">Pomocí `microsoft/dotnet:sdk` vždy obsahuje nejnovější verzi.</span><span class="sxs-lookup"><span data-stu-id="c5ac6-147">Using `microsoft/dotnet:sdk` always gives you the latest version.</span></span>

> [!TIP]
> <span data-ttu-id="c5ac6-148">Pokud si nejste jistí o vašim potřebám, kterou chcete použít `microsoft/dotnet:<version>-sdk` bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="c5ac6-148">If you are unsure about your needs, you want to use the `microsoft/dotnet:<version>-sdk` image.</span></span> <span data-ttu-id="c5ac6-149">Jako "de facto" bitovou kopii, je určený pro použití jako throw tokeny kontejneru (připojit zdrojový kód a spusťte kontejner a spusťte aplikaci) a jako základní bitovou kopii k vytvoření jiných obrázků z.</span><span class="sxs-lookup"><span data-stu-id="c5ac6-149">As the "de facto" image, it's designed to be used as a throw away container (mount your source code and start the container to start your app), and as the base image to build other images from.</span></span>

* <span data-ttu-id="c5ac6-150">`microsoft/dotnet:<version>-runtime`: Tento image obsahuje .NET Core (runtime a knihovny) a je optimalizovaná pro spouštění aplikací .NET Core **produkční**.</span><span class="sxs-lookup"><span data-stu-id="c5ac6-150">`microsoft/dotnet:<version>-runtime`: This image contains the .NET Core (runtime and libraries) and is optimized for running .NET Core apps in **production**.</span></span>

## <a name="alternative-images"></a><span data-ttu-id="c5ac6-151">Alternativní bitové kopie</span><span class="sxs-lookup"><span data-stu-id="c5ac6-151">Alternative images</span></span>

<span data-ttu-id="c5ac6-152">Kromě optimalizované scénářů vývoj, sestavení a produkční poskytujeme další bitové kopie:</span><span class="sxs-lookup"><span data-stu-id="c5ac6-152">In addition to the optimized scenarios of development, build and production, we provide additional images:</span></span>

* <span data-ttu-id="c5ac6-153">`microsoft/dotnet:<version>-runtime-deps`: **Runtime deps** bitová kopie obsahuje operační systém s všechny nativní závislosti vyžaduje .NET Core.</span><span class="sxs-lookup"><span data-stu-id="c5ac6-153">`microsoft/dotnet:<version>-runtime-deps`: The **runtime-deps** image contains the operating system with all of the native dependencies needed by .NET Core.</span></span> <span data-ttu-id="c5ac6-154">Tento image je pro [nezávislý aplikace](https://docs.microsoft.com/dotnet/core/deploying/index).</span><span class="sxs-lookup"><span data-stu-id="c5ac6-154">This image is for [self-contained applications](https://docs.microsoft.com/dotnet/core/deploying/index).</span></span>

<span data-ttu-id="c5ac6-155">Nejnovější verze jednotlivých variant:</span><span class="sxs-lookup"><span data-stu-id="c5ac6-155">Latest versions of each variant:</span></span>

* <span data-ttu-id="c5ac6-156">`microsoft/dotnet`nebo `microsoft/dotnet:latest` (alias pro bitovou kopii sady SDK)</span><span class="sxs-lookup"><span data-stu-id="c5ac6-156">`microsoft/dotnet` or `microsoft/dotnet:latest` (alias for the SDK image)</span></span>
* `microsoft/dotnet:sdk`
* `microsoft/dotnet:runtime`
* `microsoft/dotnet:runtime-deps`

## <a name="samples-to-explore"></a><span data-ttu-id="c5ac6-157">Ukázky a prozkoumejte</span><span class="sxs-lookup"><span data-stu-id="c5ac6-157">Samples to explore</span></span>

* <span data-ttu-id="c5ac6-158">[Tato ukázka ASP.NET Core Docker](https://github.com/dotnet/dotnet-docker-samples/tree/master/aspnetapp) ukazuje osvědčených postupů vzor pro vytváření imagí Dockeru pro ASP.NET Core aplikace pro produkční prostředí.</span><span class="sxs-lookup"><span data-stu-id="c5ac6-158">[This ASP.NET Core Docker sample](https://github.com/dotnet/dotnet-docker-samples/tree/master/aspnetapp) demonstrates a best practice pattern for building Docker images for ASP.NET Core apps for production.</span></span> <span data-ttu-id="c5ac6-159">Ukázka funguje s kontejnery Linux a Windows.</span><span class="sxs-lookup"><span data-stu-id="c5ac6-159">The sample works with both Linux and Windows containers.</span></span>

* <span data-ttu-id="c5ac6-160">Tento příklad .NET Core Docker znázorňuje osvědčených postupů vzor [vytváření imagí Dockeru pro aplikace .NET Core pro produkční prostředí.](https://github.com/dotnet/dotnet-docker-samples/tree/master/dotnetapp-prod)</span><span class="sxs-lookup"><span data-stu-id="c5ac6-160">This .NET Core Docker sample demonstrates a best practice pattern for [building Docker images for .NET Core apps for production.](https://github.com/dotnet/dotnet-docker-samples/tree/master/dotnetapp-prod)</span></span>

## <a name="your-first-aspnet-core-docker-app"></a><span data-ttu-id="c5ac6-161">První aplikace ASP.NET Core Docker</span><span class="sxs-lookup"><span data-stu-id="c5ac6-161">Your first ASP.NET Core Docker app</span></span>

<span data-ttu-id="c5ac6-162">V tomto kurzu umožňuje použití ukázkové aplikace ASP.NET Core Docker pro aplikaci, kterou chceme dockerize.</span><span class="sxs-lookup"><span data-stu-id="c5ac6-162">For this tutorial, lets use an ASP.NET Core Docker sample application for the app we want to dockerize.</span></span> <span data-ttu-id="c5ac6-163">Tato ukázková aplikace ASP.NET Core Docker představuje nejlepší postup vzor pro vytváření imagí Dockeru pro ASP.NET Core aplikace pro produkční prostředí.</span><span class="sxs-lookup"><span data-stu-id="c5ac6-163">This ASP.NET Core Docker sample application demonstrates a best practice pattern for building Docker images for ASP.NET Core apps for production.</span></span> <span data-ttu-id="c5ac6-164">Ukázka funguje s kontejnery Linux a Windows.</span><span class="sxs-lookup"><span data-stu-id="c5ac6-164">The sample works with both Linux and Windows containers.</span></span>

<span data-ttu-id="c5ac6-165">Ukázkový soubor Docker vytvoří image Docker aplikace ASP.NET Core na základě technologie ASP.NET Core Runtime Docker základní bitovou kopii.</span><span class="sxs-lookup"><span data-stu-id="c5ac6-165">The sample Dockerfile creates an ASP.NET Core application Docker image based off of the ASP.NET Core Runtime Docker base image.</span></span>

<span data-ttu-id="c5ac6-166">Použije [Docker více fáze sestavení funkce](https://docs.docker.com/engine/userguide/eng-image/multistage-build/) na:</span><span class="sxs-lookup"><span data-stu-id="c5ac6-166">It uses the [Docker multi-stage build feature](https://docs.docker.com/engine/userguide/eng-image/multistage-build/) to:</span></span>

* <span data-ttu-id="c5ac6-167">sestavit ukázku v kontejneru na základě **větší** základní image ASP.NET Core sestavení Docker</span><span class="sxs-lookup"><span data-stu-id="c5ac6-167">build the sample in a container based on the **larger** ASP.NET Core Build Docker base image</span></span> 
* <span data-ttu-id="c5ac6-168">zkopíruje do Docker image na základě výsledku poslední sestavení **menší** základní image ASP.NET Core Docker Runtime</span><span class="sxs-lookup"><span data-stu-id="c5ac6-168">copies the final build result into a Docker image based on the **smaller** ASP.NET Core Docker Runtime base image</span></span>

> [!Note]
> <span data-ttu-id="c5ac6-169">Sestavení bitová kopie obsahuje požadované nástroje k vytváření aplikací při bitovou kopii runtime neexistuje.</span><span class="sxs-lookup"><span data-stu-id="c5ac6-169">The build image contains required tools to build applications while the runtime image does not.</span></span>

### <a name="prerequisites"></a><span data-ttu-id="c5ac6-170">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c5ac6-170">Prerequisites</span></span>

<span data-ttu-id="c5ac6-171">Sestavení a spuštění, nainstalujte následující položky:</span><span class="sxs-lookup"><span data-stu-id="c5ac6-171">To build and run, install the following items:</span></span>

#### <a name="net-core-20-sdk"></a><span data-ttu-id="c5ac6-172">Základní rozhraní .NET 2.0 SDK</span><span class="sxs-lookup"><span data-stu-id="c5ac6-172">.NET Core 2.0 SDK</span></span>

* <span data-ttu-id="c5ac6-173">Nainstalujte [.NET Core SDK 2.0](https://www.microsoft.com/net/core).</span><span class="sxs-lookup"><span data-stu-id="c5ac6-173">Install [.NET Core SDK 2.0](https://www.microsoft.com/net/core).</span></span>

* <span data-ttu-id="c5ac6-174">Pokud jste to ještě neudělali, nainstalujte editor vaše oblíbené kódu.</span><span class="sxs-lookup"><span data-stu-id="c5ac6-174">Install your favorite code editor, if you haven't already.</span></span>

> [!TIP]
> <span data-ttu-id="c5ac6-175">Je potřeba nainstalovat editor kódu?</span><span class="sxs-lookup"><span data-stu-id="c5ac6-175">Need to install a code editor?</span></span> <span data-ttu-id="c5ac6-176">Zkuste [sady Visual Studio](https://visualstudio.com/downloads)!</span><span class="sxs-lookup"><span data-stu-id="c5ac6-176">Try [Visual Studio](https://visualstudio.com/downloads)!</span></span>

#### <a name="installing-docker-client"></a><span data-ttu-id="c5ac6-177">Instalace klienta Docker</span><span class="sxs-lookup"><span data-stu-id="c5ac6-177">Installing Docker Client</span></span>

<span data-ttu-id="c5ac6-178">Nainstalujte [Docker 17.06](https://docs.docker.com/release-notes/docker-ce/) nebo novější Docker klienta.</span><span class="sxs-lookup"><span data-stu-id="c5ac6-178">Install [Docker 17.06](https://docs.docker.com/release-notes/docker-ce/) or later of the Docker client.</span></span>

<span data-ttu-id="c5ac6-179">Klient Docker může být nainstalován v:</span><span class="sxs-lookup"><span data-stu-id="c5ac6-179">The Docker client can be installed in:</span></span>

* <span data-ttu-id="c5ac6-180">Distribuce systému Linux</span><span class="sxs-lookup"><span data-stu-id="c5ac6-180">Linux distributions</span></span>

   * [<span data-ttu-id="c5ac6-181">CentOS</span><span class="sxs-lookup"><span data-stu-id="c5ac6-181">CentOS</span></span>](https://www.docker.com/docker-centos-distribution)

   * [<span data-ttu-id="c5ac6-182">Debian</span><span class="sxs-lookup"><span data-stu-id="c5ac6-182">Debian</span></span>](https://www.docker.com/docker-debian)

   * [<span data-ttu-id="c5ac6-183">Fedora</span><span class="sxs-lookup"><span data-stu-id="c5ac6-183">Fedora</span></span>](https://www.docker.com/docker-fedora)

   * [<span data-ttu-id="c5ac6-184">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="c5ac6-184">Ubuntu</span></span>](https://www.docker.com/docker-ubuntu)

* [<span data-ttu-id="c5ac6-185">systému macOS</span><span class="sxs-lookup"><span data-stu-id="c5ac6-185">macOS</span></span>](https://docs.docker.com/docker-for-mac/)

* <span data-ttu-id="c5ac6-186">[Windows](https://docs.docker.com/docker-for-windows/).</span><span class="sxs-lookup"><span data-stu-id="c5ac6-186">[Windows](https://docs.docker.com/docker-for-windows/).</span></span>

#### <a name="installing-git-for-sample-repository"></a><span data-ttu-id="c5ac6-187">Instalace Gitu pro ukázkové úložiště</span><span class="sxs-lookup"><span data-stu-id="c5ac6-187">Installing Git for sample repository</span></span>

* <span data-ttu-id="c5ac6-188">Nainstalujte [git](https://git-scm.com/download) Pokud chcete klonovat úložiště.</span><span class="sxs-lookup"><span data-stu-id="c5ac6-188">Install [git](https://git-scm.com/download) if you wish to clone the repository.</span></span>

### <a name="getting-the-sample-application"></a><span data-ttu-id="c5ac6-189">Získávání ukázkové aplikace</span><span class="sxs-lookup"><span data-stu-id="c5ac6-189">Getting the sample application</span></span>

<span data-ttu-id="c5ac6-190">Nejjednodušší způsob, jak získat ukázce je klonováním [ukázky úložiště](https://github.com/dotnet/dotnet-docker-samples) s gitem, pomocí následujících pokynů:</span><span class="sxs-lookup"><span data-stu-id="c5ac6-190">The easiest way to get the sample is by cloning the [samples repository](https://github.com/dotnet/dotnet-docker-samples) with git, using the following instructions:</span></span> 

```console
git clone https://github.com/dotnet/dotnet-docker-samples/
```

<span data-ttu-id="c5ac6-191">Můžete také stáhnout úložiště (je malý) jako zip z ukázky úložiště .NET Core Docker.</span><span class="sxs-lookup"><span data-stu-id="c5ac6-191">You can also download the repository (it is small) as a zip from the .NET Core Docker samples repository.</span></span>

### <a name="run-the-aspnet-app-locally"></a><span data-ttu-id="c5ac6-192">Místní spuštění aplikace ASP.NET</span><span class="sxs-lookup"><span data-stu-id="c5ac6-192">Run the ASP.NET app locally</span></span>

<span data-ttu-id="c5ac6-193">Jako referenční bod před jsme containerize aplikace, nejprve spustíte aplikaci místně.</span><span class="sxs-lookup"><span data-stu-id="c5ac6-193">For a reference point, before we containerize the application, first run the application locally.</span></span>

<span data-ttu-id="c5ac6-194">Můžete sestavit a spustit aplikaci místně s .NET Core SDK 2.0 pomocí následujících příkazů (pokyny předpokládají kořenovém adresáři úložiště):</span><span class="sxs-lookup"><span data-stu-id="c5ac6-194">You can build and run the application locally with the .NET Core 2.0 SDK using the following commands (The instructions assume the root of the repository):</span></span>

```console
cd aspnetapp
dotnet run
```

<span data-ttu-id="c5ac6-195">Po spuštění aplikace, navštivte **http://localhost: 5000** ve webovém prohlížeči.</span><span class="sxs-lookup"><span data-stu-id="c5ac6-195">After the application starts, visit **http://localhost:5000** in your web browser.</span></span>

### <a name="build-and-run-the-sample-with-docker-for-linux-containers"></a><span data-ttu-id="c5ac6-196">Sestavení a spuštění vzorového Linux kontejnerů pomocí Docker</span><span class="sxs-lookup"><span data-stu-id="c5ac6-196">Build and run the sample with Docker for Linux containers</span></span>

<span data-ttu-id="c5ac6-197">Můžete sestavit a spustit ukázku v Docker použití kontejnerů Linux pomocí následujících příkazů (pokyny předpokládají kořenovém adresáři úložiště):</span><span class="sxs-lookup"><span data-stu-id="c5ac6-197">You can build and run the sample in Docker using Linux containers using the following commands (The instructions assume the root of the repository):</span></span>

```console
cd aspnetapp
docker build -t aspnetapp .
docker run -it --rm -p 5000:80 --name aspnetcore_sample aspnetapp
```

> [!Note] <span data-ttu-id="c5ac6-198">`docker run` '-P' argument port 5000 na místním počítači na port 80 v kontejneru mapy (formulář mapování portů `host:container`).</span><span class="sxs-lookup"><span data-stu-id="c5ac6-198">The `docker run` '-p' argument maps port 5000 on your local machine to port 80 in the container (the port mapping form is `host:container`).</span></span> <span data-ttu-id="c5ac6-199">Další informace najdete v tématu [docker spustit](https://docs.docker.com/engine/reference/commandline/exec/) odkazu na parametry příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="c5ac6-199">For more information, see the [docker run](https://docs.docker.com/engine/reference/commandline/exec/) reference on command-line parameters.</span></span>

<span data-ttu-id="c5ac6-200">Po spuštění aplikace, navštivte **http://localhost: 5000** ve webovém prohlížeči.</span><span class="sxs-lookup"><span data-stu-id="c5ac6-200">After the application starts, visit **http://localhost:5000** in your web browser.</span></span>

### <a name="build-and-run-the-sample-with-docker-for-windows-containers"></a><span data-ttu-id="c5ac6-201">Sestavení a spuštění vzorového s kontejnery Docker pro Windows</span><span class="sxs-lookup"><span data-stu-id="c5ac6-201">Build and run the sample with Docker for Windows containers</span></span>

<span data-ttu-id="c5ac6-202">Můžete sestavit a spustit ukázku v Docker použití Windows kontejnerů pomocí následujících příkazů (pokyny předpokládají kořenovém adresáři úložiště):</span><span class="sxs-lookup"><span data-stu-id="c5ac6-202">You can build and run the sample in Docker using Windows containers using the following commands (The instructions assume the root of the repository):</span></span>

```console
cd aspnetapp
docker build -t aspnetapp .
docker run -it --rm --name aspnetcore_sample aspnetapp
```

> [!IMPORTANT]
> <span data-ttu-id="c5ac6-203">Je nutné na Přejít **kontejneru IP adresu** (na rozdíl od http://localhost) v prohlížeči přímo při použití Windows kontejnerů.</span><span class="sxs-lookup"><span data-stu-id="c5ac6-203">You must navigate to the **container IP address** (as opposed to http://localhost) in your browser directly when using Windows containers.</span></span> <span data-ttu-id="c5ac6-204">Můžete získat IP adresu vašeho kontejneru pomocí následujících kroků:</span><span class="sxs-lookup"><span data-stu-id="c5ac6-204">You can get the IP address of your container with the following steps:</span></span>

* <span data-ttu-id="c5ac6-205">Otevřete jiného příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="c5ac6-205">Open up another command prompt.</span></span>
* <span data-ttu-id="c5ac6-206">Spustit `docker ps` zobrazíte spuštěných kontejnerů.</span><span class="sxs-lookup"><span data-stu-id="c5ac6-206">Run `docker ps` to see your running containers.</span></span> <span data-ttu-id="c5ac6-207">Kontejner "aspnetcore_sample" by měla existovat.</span><span class="sxs-lookup"><span data-stu-id="c5ac6-207">The "aspnetcore_sample" container should be there.</span></span>
* <span data-ttu-id="c5ac6-208">Run `docker exec aspnetcore_sample ipconfig`.</span><span class="sxs-lookup"><span data-stu-id="c5ac6-208">Run `docker exec aspnetcore_sample ipconfig`.</span></span>
* <span data-ttu-id="c5ac6-209">IP adresa kontejneru zkopírujte a vložte do prohlížeče (například 172.29.245.43).</span><span class="sxs-lookup"><span data-stu-id="c5ac6-209">Copy the container IP address and paste into your browser (for example, 172.29.245.43).</span></span>

> [!Note]
> <span data-ttu-id="c5ac6-210">Docker exec podporuje identifikační kontejnery s názvem nebo hodnoty hash.</span><span class="sxs-lookup"><span data-stu-id="c5ac6-210">Docker exec supports identifying containers with name or hash.</span></span> <span data-ttu-id="c5ac6-211">V našem příkladu se používá název (aspnetcore_sample).</span><span class="sxs-lookup"><span data-stu-id="c5ac6-211">The name (aspnetcore_sample) is used in our example.</span></span>

<span data-ttu-id="c5ac6-212">Podívejte se na následující příklad toho, jak získat IP adresu spuštěné kontejneru systému Windows.</span><span class="sxs-lookup"><span data-stu-id="c5ac6-212">See the following example of how to get the IP address of a running Windows container.</span></span>

```console
docker exec aspnetcore_sample ipconfig

Windows IP Configuration

Ethernet adapter Ethernet:

   Connection-specific DNS Suffix  . : contoso.com
   Link-local IPv6 Address . . . . . : fe80::1967:6598:124:cfa3%4
   IPv4 Address. . . . . . . . . . . : 172.29.245.43
   Subnet Mask . . . . . . . . . . . : 255.255.240.0
   Default Gateway . . . . . . . . . : 172.29.240.1
```

> [!Note]
> <span data-ttu-id="c5ac6-213">Docker exec spustí nový příkaz v běžící kontejneru.</span><span class="sxs-lookup"><span data-stu-id="c5ac6-213">Docker exec runs a new command in a running container.</span></span> <span data-ttu-id="c5ac6-214">Další informace najdete v tématu [docker exec odkaz](https://docs.docker.com/engine/reference/commandline/exec/) na parametry příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="c5ac6-214">For more information, see the [docker exec reference](https://docs.docker.com/engine/reference/commandline/exec/) on command-line parameters.</span></span>

<span data-ttu-id="c5ac6-215">Může vytvářet aplikace, která je připravená k nasazení do produkčního prostředí místně pomocí [dotnet publikování](../tools/dotnet-publish.md) příkaz.</span><span class="sxs-lookup"><span data-stu-id="c5ac6-215">You can produce an application that is ready to deploy to production locally using the [dotnet publish](../tools/dotnet-publish.md) command.</span></span>

```console
dotnet publish -c release -o published
```

> [!Note]
> <span data-ttu-id="c5ac6-216">-C argument verze sestavení aplikace v režimu vydání (výchozí hodnota je režim ladění).</span><span class="sxs-lookup"><span data-stu-id="c5ac6-216">The -c release argument builds the application in release mode (the default is debug mode).</span></span> <span data-ttu-id="c5ac6-217">Další informace najdete v tématu [dotnet. Spusťte odkaz](../tools/dotnet-run.md) na parametry příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="c5ac6-217">For more information, see the [dotnet run reference](../tools/dotnet-run.md) on command-line parameters.</span></span>

<span data-ttu-id="c5ac6-218">Spuštění aplikace na **Windows** pomocí následujícího příkazu.</span><span class="sxs-lookup"><span data-stu-id="c5ac6-218">You can run the application on **Windows** using the following command.</span></span>

```console
dotnet published\aspnetapp.dll
```

<span data-ttu-id="c5ac6-219">Spuštění aplikace na **Linux** nebo **systému macOS** pomocí následujícího příkazu.</span><span class="sxs-lookup"><span data-stu-id="c5ac6-219">You can run the application on **Linux** or **macOS** using the following command.</span></span>

```bash
dotnet published/aspnetapp.dll
```

### <a name="docker-images-used-in-this-sample"></a><span data-ttu-id="c5ac6-220">Docker obrázků použitých v této ukázce</span><span class="sxs-lookup"><span data-stu-id="c5ac6-220">Docker Images used in this sample</span></span>

<span data-ttu-id="c5ac6-221">V této ukázce se používají na následujících obrázcích Docker</span><span class="sxs-lookup"><span data-stu-id="c5ac6-221">The following Docker images are used in this sample</span></span>

* `microsoft/aspnetcore-build:2.0`
* `microsoft/aspnetcore:2.0`

<span data-ttu-id="c5ac6-222">Blahopřejeme!</span><span class="sxs-lookup"><span data-stu-id="c5ac6-222">Congratulations!</span></span> <span data-ttu-id="c5ac6-223">máte právě:</span><span class="sxs-lookup"><span data-stu-id="c5ac6-223">you have just:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="c5ac6-224">Naučili o imagí Dockeru základní rozhraní Microsoft .NET</span><span class="sxs-lookup"><span data-stu-id="c5ac6-224">Learned about Microsoft .NET Core Docker images</span></span>
> * <span data-ttu-id="c5ac6-225">Tu ASP.NET Core ukázkové aplikaci Dockerize</span><span class="sxs-lookup"><span data-stu-id="c5ac6-225">Got an ASP.NET Core sample app to Dockerize</span></span>
> * <span data-ttu-id="c5ac6-226">Byla spuštěna místně ukázková aplikace ASP.NET</span><span class="sxs-lookup"><span data-stu-id="c5ac6-226">Ran the ASP.NET sample app locally</span></span>
> * <span data-ttu-id="c5ac6-227">Vytvořené a spustil ukázku pomocí Docker pro Linux kontejnery</span><span class="sxs-lookup"><span data-stu-id="c5ac6-227">Built and ran the sample with Docker for Linux containers</span></span>
> * <span data-ttu-id="c5ac6-228">Vytvořené a spustil vzorku s kontejnery Docker pro Windows</span><span class="sxs-lookup"><span data-stu-id="c5ac6-228">Built and ran the sample with Docker for Windows containers</span></span>


<span data-ttu-id="c5ac6-229">**Další kroky**</span><span class="sxs-lookup"><span data-stu-id="c5ac6-229">**Next Steps**</span></span>

<span data-ttu-id="c5ac6-230">Zde jsou některé další kroky, které můžete provést:</span><span class="sxs-lookup"><span data-stu-id="c5ac6-230">Here are some next steps you can take:</span></span>

* [<span data-ttu-id="c5ac6-231">Práce s nástroji Visual Studio Docker</span><span class="sxs-lookup"><span data-stu-id="c5ac6-231">Working with Visual Studio Docker Tools</span></span>](https://docs.microsoft.com/aspnet/core/publishing/visual-studio-tools-for-docker)
* [<span data-ttu-id="c5ac6-232">Nasazení bitových kopií Docker z registru kontejner Azure do Azure kontejner instancí</span><span class="sxs-lookup"><span data-stu-id="c5ac6-232">Deploying Docker Images from the Azure Container Registry to Azure Container Instances</span></span>](https://blogs.msdn.microsoft.com/stevelasker/2017/07/28/deploying-docker-images-from-the-azure-container-registry-to-azure-container-instances/)
* [<span data-ttu-id="c5ac6-233">Ladění pomocí kódu v sadě Visual Studio</span><span class="sxs-lookup"><span data-stu-id="c5ac6-233">Debugging with Visual Studio Code</span></span>](https://code.visualstudio.com/docs/nodejs/debugging-recipes#_nodejs-typescript-docker-container) 
* [<span data-ttu-id="c5ac6-234">Načítání rukou pomocí sady Visual Studio pro Mac, kontejnery a bez serveru kódu v cloudu</span><span class="sxs-lookup"><span data-stu-id="c5ac6-234">Getting hands on with Visual Studio for Mac, containers, and serverless code in the cloud</span></span>](https://blogs.msdn.microsoft.com/visualstudio/2017/08/31/hands-on-with-visual-studio-for-mac-containers-serverless-code-in-the-cloud/#comments)
* [<span data-ttu-id="c5ac6-235">Začínáme s Docker a Visual Studio pro Mac testovacího prostředí</span><span class="sxs-lookup"><span data-stu-id="c5ac6-235">Getting Started with Docker and Visual Studio for Mac Lab</span></span>](https://github.com/Microsoft/vs4mac-labs/tree/master/Docker/Getting-Started)

> [!Note]
> <span data-ttu-id="c5ac6-236">Pokud nemáte předplatné Azure, [Přihlaste se ještě dnes](https://azure.microsoft.com/free/?b=16.48) bezplatný účet 30 dnů a 200 USD get v kredity Azure můžete vyzkoušet na libovolnou kombinaci služby Azure.</span><span class="sxs-lookup"><span data-stu-id="c5ac6-236">If you do not have an Azure subscription, [sign up today](https://azure.microsoft.com/free/?b=16.48) for a free 30-day account and get $200 in Azure Credits to try out any combination of Azure services.</span></span>
