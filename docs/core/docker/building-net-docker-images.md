---
title: Vytváření Imagí Dockeru .NET Core
description: Principy imagí Dockeru a .NET Core
author: jralexander
ms.author: johalex
ms.date: 11/06/2017
ms.topic: tutorial
ms.custom: mvc
ms.openlocfilehash: e48a263334ebb93a5d281032336aeb4073d8467c
ms.sourcegitcommit: e8dc507cfdaad504fc9d4c83d28d24569dcef91c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/03/2018
ms.locfileid: "34827336"
---
# <a name="building-docker-images-for-net-core-applications"></a><span data-ttu-id="4d53a-103">Vytváření Imagí Dockeru pro aplikace .NET Core</span><span class="sxs-lookup"><span data-stu-id="4d53a-103">Building Docker Images for .NET Core Applications</span></span>

 <span data-ttu-id="4d53a-104">V tomto kurzu se zaměříme na tom, jak pomocí .NET Core v Dockeru.</span><span class="sxs-lookup"><span data-stu-id="4d53a-104">In this tutorial, We focus on how to use .NET Core on Docker.</span></span> <span data-ttu-id="4d53a-105">Nejprve podíváme na různé imagí Dockeru k dispozici a spravován společností Microsoft a případy použití.</span><span class="sxs-lookup"><span data-stu-id="4d53a-105">First, we explore the different Docker images offered and maintained by Microsoft, and use cases.</span></span> <span data-ttu-id="4d53a-106">Potom jsme zjistěte, jak sestavit a dockerizace aplikace ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="4d53a-106">We then learn how to build and dockerize an ASP.NET Core app.</span></span>

<span data-ttu-id="4d53a-107">V průběhu tohoto kurzu se dozvíte:</span><span class="sxs-lookup"><span data-stu-id="4d53a-107">During the course of this tutorial, you learn:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="4d53a-108">Další informace o imagích Dockeru rozhraní Microsoft .NET Core</span><span class="sxs-lookup"><span data-stu-id="4d53a-108">Learn about Microsoft .NET Core Docker images</span></span> 
> * <span data-ttu-id="4d53a-109">Získat ASP.NET Core ukázkovou aplikaci do Dockerize</span><span class="sxs-lookup"><span data-stu-id="4d53a-109">Get an ASP.NET Core sample app to Dockerize</span></span>
> * <span data-ttu-id="4d53a-110">Spuštění ukázkové aplikace ASP.NET místně</span><span class="sxs-lookup"><span data-stu-id="4d53a-110">Run the ASP.NET sample app locally</span></span>
> * <span data-ttu-id="4d53a-111">Sestavte a spusťte ukázku s prostředím Docker pro kontejnery Linuxu</span><span class="sxs-lookup"><span data-stu-id="4d53a-111">Build and run the sample with Docker for Linux containers</span></span>
> * <span data-ttu-id="4d53a-112">Sestavte a spusťte ukázku s kontejnery Docker pro Windows</span><span class="sxs-lookup"><span data-stu-id="4d53a-112">Build and run the sample with Docker for Windows containers</span></span>

## <a name="docker-image-optimizations"></a><span data-ttu-id="4d53a-113">Optimalizace Image dockeru</span><span class="sxs-lookup"><span data-stu-id="4d53a-113">Docker Image Optimizations</span></span>

<span data-ttu-id="4d53a-114">Při vytváření imagí Dockeru pro vývojáře, jsme se zaměřili na třech hlavních scénářích:</span><span class="sxs-lookup"><span data-stu-id="4d53a-114">When building Docker images for developers, we focused on three main scenarios:</span></span>

* <span data-ttu-id="4d53a-115">Obrázky používané pro vývoj aplikací .NET Core</span><span class="sxs-lookup"><span data-stu-id="4d53a-115">Images used to develop .NET Core apps</span></span>
* <span data-ttu-id="4d53a-116">Image sloužící k sestavení aplikace .NET Core</span><span class="sxs-lookup"><span data-stu-id="4d53a-116">Images used to build .NET Core apps</span></span>
* <span data-ttu-id="4d53a-117">Obrázky používané ke spouštění aplikací .NET Core</span><span class="sxs-lookup"><span data-stu-id="4d53a-117">Images used to run .NET Core apps</span></span>

<span data-ttu-id="4d53a-118">Proč tři Image?</span><span class="sxs-lookup"><span data-stu-id="4d53a-118">Why three images?</span></span>
<span data-ttu-id="4d53a-119">Při vývoji, vytváření a spouštění kontejnerizovaných aplikací, jsme mají různé priority.</span><span class="sxs-lookup"><span data-stu-id="4d53a-119">When developing, building, and running containerized applications, we have different priorities.</span></span>

* <span data-ttu-id="4d53a-120">**Vývoj:** prioritou se zaměřuje na rychle iterovat změny a možnost ladit změny.</span><span class="sxs-lookup"><span data-stu-id="4d53a-120">**Development:**  The priority focuses on quickly iterate changes, and the ability to debug the changes.</span></span> <span data-ttu-id="4d53a-121">Velikost bitové kopie není důležité, místo toho můžete provést změny kódu a rychle vidět?</span><span class="sxs-lookup"><span data-stu-id="4d53a-121">The size of the image isn't as important, rather can you make changes to your code and see them quickly?</span></span>

* <span data-ttu-id="4d53a-122">**Sestavení:** tento obrázek obsahuje vše potřebné pro kompilaci aplikace, které zahrnují kompilátor a další závislosti optimalizovat binární soubory.</span><span class="sxs-lookup"><span data-stu-id="4d53a-122">**Build:** This image contains everything needed to compile your app, which includes the compiler and any other dependencies to optimize the binaries.</span></span>  <span data-ttu-id="4d53a-123">Sestavení image použijete k vytvoření majetek, který umístíte do produkčního prostředí image.</span><span class="sxs-lookup"><span data-stu-id="4d53a-123">You use the build image to create the assets you place into a production image.</span></span> <span data-ttu-id="4d53a-124">Sestavení image se použije pro průběžnou integraci, nebo v prostředí sestavení.</span><span class="sxs-lookup"><span data-stu-id="4d53a-124">The build image would be used for continuous integration, or in a build environment.</span></span> <span data-ttu-id="4d53a-125">Tento přístup umožňuje agenta sestavení pro zkompilování a vybuildování aplikace (s všechny požadované závislosti) v instanci bitové kopie sestavení.</span><span class="sxs-lookup"><span data-stu-id="4d53a-125">This approach allows a build agent to compile and build the application (with all the required dependencies) in a build image instance.</span></span> <span data-ttu-id="4d53a-126">Agenta sestavení stačí vědět, jak ke spuštění této image Dockeru.</span><span class="sxs-lookup"><span data-stu-id="4d53a-126">Your build agent only needs to know how to run this Docker image.</span></span>

* <span data-ttu-id="4d53a-127">**Produkční:** jak rychle můžete nasadit a spustit image?</span><span class="sxs-lookup"><span data-stu-id="4d53a-127">**Production:** How fast you can deploy and start your image?</span></span> <span data-ttu-id="4d53a-128">Tato image je malé, takže je optimalizován výkon sítě z registru Dockeru do Docker hostitelů.</span><span class="sxs-lookup"><span data-stu-id="4d53a-128">This image is small so network performance from your Docker Registry to your Docker hosts is optimized.</span></span> <span data-ttu-id="4d53a-129">Obsah je připraven ke spuštění povolení nejrychlejší doba od Dockeru, spusťte na zpracování výsledků.</span><span class="sxs-lookup"><span data-stu-id="4d53a-129">The contents are ready to run enabling the fastest time from Docker run to processing results.</span></span> <span data-ttu-id="4d53a-130">Dynamický kód kompilace, není nutná v modelu Dockeru.</span><span class="sxs-lookup"><span data-stu-id="4d53a-130">Dynamic code compilation isn't needed in the Docker model.</span></span> <span data-ttu-id="4d53a-131">Obsah, který umístíte do této bitové kopie omezeny na binární soubory a obsah potřebný ke spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="4d53a-131">The content you place in this image would be limited to the binaries and content needed to run the application.</span></span>

    <span data-ttu-id="4d53a-132">Například `dotnet publish` výstup obsahuje:</span><span class="sxs-lookup"><span data-stu-id="4d53a-132">For example, the `dotnet publish` output contains:</span></span>

    * <span data-ttu-id="4d53a-133">kompilované binární soubory</span><span class="sxs-lookup"><span data-stu-id="4d53a-133">the compiled binaries</span></span>
    * <span data-ttu-id="4d53a-134">soubory JS a CSS</span><span class="sxs-lookup"><span data-stu-id="4d53a-134">.js and .css files</span></span>


<span data-ttu-id="4d53a-135">Z důvodu chcete zahrnout `dotnet publish` výstupu příkazu v bitové kopii produkčního prostředí o jeho velikost na minimum.</span><span class="sxs-lookup"><span data-stu-id="4d53a-135">The reason to include the `dotnet publish` command output in your production image is to keep its size to a minimum.</span></span>

<span data-ttu-id="4d53a-136">Některé obrázky .NET Core sdílení vrstev mezi různých klíčových slov, takže stahování nejnovějších značka je poměrně jednoduchý proces.</span><span class="sxs-lookup"><span data-stu-id="4d53a-136">Some .NET Core images share layers between different tags so downloading the latest tag is a relatively lightweight process.</span></span> <span data-ttu-id="4d53a-137">Pokud už máte starší verzi na svém počítači, tato architektura zmenšuje místo na disku potřebné.</span><span class="sxs-lookup"><span data-stu-id="4d53a-137">If you already have an older version on your machine, this architecture decreases the needed disk space.</span></span>

<span data-ttu-id="4d53a-138">Při obvyklých imagí používat více aplikací ve stejném počítači, je paměť sdílená mezi obvyklých imagí.</span><span class="sxs-lookup"><span data-stu-id="4d53a-138">When multiple applications use common images on the same machine, memory is shared between the common images.</span></span> <span data-ttu-id="4d53a-139">Image se musí shodovat s ke sdílení.</span><span class="sxs-lookup"><span data-stu-id="4d53a-139">The images must be the same to be shared.</span></span>

## <a name="docker-image-variations"></a><span data-ttu-id="4d53a-140">Variace image dockeru</span><span class="sxs-lookup"><span data-stu-id="4d53a-140">Docker image variations</span></span>

<span data-ttu-id="4d53a-141">K dosažení cílů výše, poskytujeme varianty image v rámci [ `microsoft/dotnet` ](https://hub.docker.com/r/microsoft/dotnet/).</span><span class="sxs-lookup"><span data-stu-id="4d53a-141">To achieve the goals above, we provide image variants under [`microsoft/dotnet`](https://hub.docker.com/r/microsoft/dotnet/).</span></span>

* <span data-ttu-id="4d53a-142">`microsoft/dotnet:<version>-sdk`(`microsoft/dotnet:2.1-sdk`) Tento obrázek obsahuje sady .NET Core SDK, která zahrnuje .NET Core a nástroje příkazového řádku (CLI).</span><span class="sxs-lookup"><span data-stu-id="4d53a-142">`microsoft/dotnet:<version>-sdk`(`microsoft/dotnet:2.1-sdk`) This image contains the .NET Core SDK, which includes the .NET Core and Command Line Tools (CLI).</span></span> <span data-ttu-id="4d53a-143">Tento obrázek mapuje **scénář vývoje**.</span><span class="sxs-lookup"><span data-stu-id="4d53a-143">This image maps to the **development scenario**.</span></span> <span data-ttu-id="4d53a-144">Použít tuto bitovou kopii pro místní vývoj, ladění a testování částí.</span><span class="sxs-lookup"><span data-stu-id="4d53a-144">You use this image for local development, debugging, and unit testing.</span></span> <span data-ttu-id="4d53a-145">Tato image je také možné pro vaši **sestavení** scénáře.</span><span class="sxs-lookup"><span data-stu-id="4d53a-145">This image can also be used for your **build** scenarios.</span></span> <span data-ttu-id="4d53a-146">Pomocí `microsoft/dotnet:sdk` vždy obsahuje nejnovější verzi.</span><span class="sxs-lookup"><span data-stu-id="4d53a-146">Using `microsoft/dotnet:sdk` always gives you the latest version.</span></span>

> [!TIP]
> <span data-ttu-id="4d53a-147">Pokud si nejste jistí o vašim potřebám, kterou chcete použít `microsoft/dotnet:<version>-sdk` bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="4d53a-147">If you are unsure about your needs, you want to use the `microsoft/dotnet:<version>-sdk` image.</span></span> <span data-ttu-id="4d53a-148">Jako "de facto stane" image, je určený pro použití jako throw tokeny kontejneru (připojit svůj zdrojový kód a spustit kontejner pro spuštění vaší aplikace) a jako základní image k vytvoření další Image z.</span><span class="sxs-lookup"><span data-stu-id="4d53a-148">As the "de facto" image, it's designed to be used as a throw away container (mount your source code and start the container to start your app), and as the base image to build other images from.</span></span>

* <span data-ttu-id="4d53a-149">`microsoft/dotnet:<version>-runtime`: Tento obrázek obsahuje .NET Core (prostředí runtime a knihovny) a je optimalizovaná pro spouštění aplikací .NET Core **produkční**.</span><span class="sxs-lookup"><span data-stu-id="4d53a-149">`microsoft/dotnet:<version>-runtime`: This image contains the .NET Core (runtime and libraries) and is optimized for running .NET Core apps in **production**.</span></span>

## <a name="alternative-images"></a><span data-ttu-id="4d53a-150">Alternativní imagí</span><span class="sxs-lookup"><span data-stu-id="4d53a-150">Alternative images</span></span>

<span data-ttu-id="4d53a-151">Kromě optimalizované scénáře vývoje, sestavení a produkčním prostředí Nabízíme další Image:</span><span class="sxs-lookup"><span data-stu-id="4d53a-151">In addition to the optimized scenarios of development, build and production, we provide additional images:</span></span>

* <span data-ttu-id="4d53a-152">`microsoft/dotnet:<version>-runtime-deps`: **Runtime deps** bitová kopie obsahuje operační systém se všemi nativní závislosti vyžadované .NET Core.</span><span class="sxs-lookup"><span data-stu-id="4d53a-152">`microsoft/dotnet:<version>-runtime-deps`: The **runtime-deps** image contains the operating system with all of the native dependencies needed by .NET Core.</span></span> <span data-ttu-id="4d53a-153">Tento obrázek pochází pro [samostatná aplikace](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="4d53a-153">This image is for [self-contained applications](../deploying/index.md).</span></span>

<span data-ttu-id="4d53a-154">Nejnovější verze každého typu variant:</span><span class="sxs-lookup"><span data-stu-id="4d53a-154">Latest versions of each variant:</span></span>

* <span data-ttu-id="4d53a-155">`microsoft/dotnet` nebo `microsoft/dotnet:latest` (alias pro bitovou kopii sady SDK)</span><span class="sxs-lookup"><span data-stu-id="4d53a-155">`microsoft/dotnet` or `microsoft/dotnet:latest` (alias for the SDK image)</span></span>
* `microsoft/dotnet:sdk`
* `microsoft/dotnet:runtime`
* `microsoft/dotnet:runtime-deps`

## <a name="samples-to-explore"></a><span data-ttu-id="4d53a-156">Prozkoumejte ukázky</span><span class="sxs-lookup"><span data-stu-id="4d53a-156">Samples to explore</span></span>

* <span data-ttu-id="4d53a-157">[Tato ukázka ASP.NET Core Docker](https://github.com/dotnet/dotnet-docker/tree/master/samples/aspnetapp) ukazuje vzoru osvědčených postupů pro vytváření imagí Dockeru pro ASP.NET Core aplikace pro produkční prostředí.</span><span class="sxs-lookup"><span data-stu-id="4d53a-157">[This ASP.NET Core Docker sample](https://github.com/dotnet/dotnet-docker/tree/master/samples/aspnetapp) demonstrates a best practice pattern for building Docker images for ASP.NET Core apps for production.</span></span> <span data-ttu-id="4d53a-158">Ukázka funguje s kontejnery Windows i Linux.</span><span class="sxs-lookup"><span data-stu-id="4d53a-158">The sample works with both Linux and Windows containers.</span></span>

* <span data-ttu-id="4d53a-159">V této aplikaci .NET Core Docker ukázce vzoru osvědčených postupů pro [vytváření imagí Dockeru pro aplikace .NET Core pro produkční prostředí.](https://github.com/dotnet/dotnet-docker/tree/master/samples/dotnetapp)</span><span class="sxs-lookup"><span data-stu-id="4d53a-159">This .NET Core Docker sample demonstrates a best practice pattern for [building Docker images for .NET Core apps for production.](https://github.com/dotnet/dotnet-docker/tree/master/samples/dotnetapp)</span></span>

## <a name="forward-the-request-scheme-and-original-ip-address"></a><span data-ttu-id="4d53a-160">Schéma požadavku a původní IP adresa</span><span class="sxs-lookup"><span data-stu-id="4d53a-160">Forward the request scheme and original IP address</span></span>

<span data-ttu-id="4d53a-161">Proxy servery, nástroje pro vyrovnávání zatížení a jiných síťových zařízení často skryl informace o požadavku předtím, než dosáhne kontejnerizovanou aplikaci:</span><span class="sxs-lookup"><span data-stu-id="4d53a-161">Proxy servers, load balancers, and other network appliances often obscure information about a request before it reaches the containerized app:</span></span>

* <span data-ttu-id="4d53a-162">Pokud požadavky HTTPS jsou směrovány přes proxy server pomocí protokolu HTTP, původní schéma (HTTPS) ztratí a musí předávat v hlavičce.</span><span class="sxs-lookup"><span data-stu-id="4d53a-162">When HTTPS requests are proxied over HTTP, the original scheme (HTTPS) is lost and must be forwarded in a header.</span></span>
* <span data-ttu-id="4d53a-163">Protože aplikace obdrží žádost z proxy serveru a není true zdroj na Internetu nebo podnikové sítě, musí v hlavičce předané původní IP adresa klienta.</span><span class="sxs-lookup"><span data-stu-id="4d53a-163">Because an app receives a request from the proxy and not its true source on the Internet or corporate network, the original client IP address must also be forwarded in a header.</span></span>

<span data-ttu-id="4d53a-164">Tyto informace mohou být důležité pro zpracování žádostí, například v přesměrování ověřování, generování odkazů, hodnocení zásad a informace o zeměpisné poloze klienta.</span><span class="sxs-lookup"><span data-stu-id="4d53a-164">This information may be important in request processing, for example in redirects, authentication, link generation, policy evaluation, and client geolocation.</span></span>

<span data-ttu-id="4d53a-165">Přeposílat schéma a původní IP adresy pro kontejnerizované aplikace ASP.NET Core, používají předané Middleware záhlaví.</span><span class="sxs-lookup"><span data-stu-id="4d53a-165">To forward the scheme and original IP address to a containerized ASP.NET Core app, use Forwarded Headers Middleware.</span></span> <span data-ttu-id="4d53a-166">Další informace najdete v tématu [konfigurace ASP.NET Core práci se servery proxy a nástroje pro vyrovnávání zatížení](/aspnet/core/host-and-deploy/proxy-load-balancer).</span><span class="sxs-lookup"><span data-stu-id="4d53a-166">For more information, see [Configure ASP.NET Core to work with proxy servers and load balancers](/aspnet/core/host-and-deploy/proxy-load-balancer).</span></span>

## <a name="your-first-aspnet-core-docker-app"></a><span data-ttu-id="4d53a-167">Vaše první aplikace ASP.NET Core Dockeru</span><span class="sxs-lookup"><span data-stu-id="4d53a-167">Your first ASP.NET Core Docker app</span></span>

<span data-ttu-id="4d53a-168">Pro účely tohoto kurzu umožňuje aplikaci, kterou chceme dockerizace pomocí ukázkové aplikace ASP.NET Core Dockeru.</span><span class="sxs-lookup"><span data-stu-id="4d53a-168">For this tutorial, lets use an ASP.NET Core Docker sample application for the app we want to dockerize.</span></span> <span data-ttu-id="4d53a-169">Tato ukázková aplikace ASP.NET Core Docker ukazuje vzoru osvědčených postupů pro vytváření imagí Dockeru pro ASP.NET Core aplikace pro produkční prostředí.</span><span class="sxs-lookup"><span data-stu-id="4d53a-169">This ASP.NET Core Docker sample application demonstrates a best practice pattern for building Docker images for ASP.NET Core apps for production.</span></span> <span data-ttu-id="4d53a-170">Ukázka funguje s kontejnery Windows i Linux.</span><span class="sxs-lookup"><span data-stu-id="4d53a-170">The sample works with both Linux and Windows containers.</span></span>

<span data-ttu-id="4d53a-171">Soubor Dockerfile vzorovým kódem se vytvoří image Dockeru aplikace ASP.NET Core na základě základní image Dockeru modulu Runtime ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="4d53a-171">The sample Dockerfile creates an ASP.NET Core application Docker image based off of the ASP.NET Core Runtime Docker base image.</span></span>

<span data-ttu-id="4d53a-172">Používá [Docker vícefázových sestavení funkce](https://docs.docker.com/engine/userguide/eng-image/multistage-build/) na:</span><span class="sxs-lookup"><span data-stu-id="4d53a-172">It uses the [Docker multi-stage build feature](https://docs.docker.com/engine/userguide/eng-image/multistage-build/) to:</span></span>

* <span data-ttu-id="4d53a-173">sestavit ukázku v kontejneru na základě **větší** základní image Dockeru sestavení ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="4d53a-173">build the sample in a container based on the **larger** ASP.NET Core Build Docker base image</span></span> 
* <span data-ttu-id="4d53a-174">zkopíruje výsledek poslední sestavení do image Dockeru na základě **menší** základní imagi modulu Runtime ASP.NET Core Dockeru</span><span class="sxs-lookup"><span data-stu-id="4d53a-174">copies the final build result into a Docker image based on the **smaller** ASP.NET Core Docker Runtime base image</span></span>

> [!NOTE]
> <span data-ttu-id="4d53a-175">Sestavení image obsahuje potřebné nástroje pro vytváření aplikací, ale nikoli bitové kopie modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="4d53a-175">The build image contains required tools to build applications while the runtime image does not.</span></span>

### <a name="prerequisites"></a><span data-ttu-id="4d53a-176">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4d53a-176">Prerequisites</span></span>

<span data-ttu-id="4d53a-177">Sestavte a spusťte, nainstalujte následující položky:</span><span class="sxs-lookup"><span data-stu-id="4d53a-177">To build and run, install the following items:</span></span>

#### <a name="net-core-21-sdk"></a><span data-ttu-id="4d53a-178">.NET core 2.1 SDK</span><span class="sxs-lookup"><span data-stu-id="4d53a-178">.NET Core 2.1 SDK</span></span>

* <span data-ttu-id="4d53a-179">Nainstalujte [.NET Core SDK 2.1](https://www.microsoft.com/net/core).</span><span class="sxs-lookup"><span data-stu-id="4d53a-179">Install [.NET Core SDK 2.1](https://www.microsoft.com/net/core).</span></span>

* <span data-ttu-id="4d53a-180">Pokud jste tak dosud neučinili, nainstalujte váš oblíbený editor kódu.</span><span class="sxs-lookup"><span data-stu-id="4d53a-180">Install your favorite code editor, if you haven't already.</span></span>

> [!TIP]
> <span data-ttu-id="4d53a-181">Je potřeba nainstalovat editor kódu?</span><span class="sxs-lookup"><span data-stu-id="4d53a-181">Need to install a code editor?</span></span> <span data-ttu-id="4d53a-182">Zkuste [sady Visual Studio](https://visualstudio.com/downloads)!</span><span class="sxs-lookup"><span data-stu-id="4d53a-182">Try [Visual Studio](https://visualstudio.com/downloads)!</span></span>

#### <a name="installing-docker-client"></a><span data-ttu-id="4d53a-183">Instalace klienta Dockeru</span><span class="sxs-lookup"><span data-stu-id="4d53a-183">Installing Docker Client</span></span>

<span data-ttu-id="4d53a-184">Nainstalujte [Docker 18.03](https://docs.docker.com/release-notes/docker-ce/) nebo novější klienta Dockeru.</span><span class="sxs-lookup"><span data-stu-id="4d53a-184">Install [Docker 18.03](https://docs.docker.com/release-notes/docker-ce/) or later of the Docker client.</span></span>

<span data-ttu-id="4d53a-185">Klienta Dockeru se dá nainstalovat ve:</span><span class="sxs-lookup"><span data-stu-id="4d53a-185">The Docker client can be installed in:</span></span>

* <span data-ttu-id="4d53a-186">Linuxové distribuce</span><span class="sxs-lookup"><span data-stu-id="4d53a-186">Linux distributions</span></span>

   * [<span data-ttu-id="4d53a-187">CentOS</span><span class="sxs-lookup"><span data-stu-id="4d53a-187">CentOS</span></span>](https://www.docker.com/docker-centos-distribution)

   * [<span data-ttu-id="4d53a-188">Debian</span><span class="sxs-lookup"><span data-stu-id="4d53a-188">Debian</span></span>](https://www.docker.com/docker-debian)

   * [<span data-ttu-id="4d53a-189">Fedora</span><span class="sxs-lookup"><span data-stu-id="4d53a-189">Fedora</span></span>](https://www.docker.com/docker-fedora)

   * [<span data-ttu-id="4d53a-190">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="4d53a-190">Ubuntu</span></span>](https://www.docker.com/docker-ubuntu)

* [<span data-ttu-id="4d53a-191">macOS</span><span class="sxs-lookup"><span data-stu-id="4d53a-191">macOS</span></span>](https://docs.docker.com/docker-for-mac/)

* <span data-ttu-id="4d53a-192">[Windows](https://docs.docker.com/docker-for-windows/).</span><span class="sxs-lookup"><span data-stu-id="4d53a-192">[Windows](https://docs.docker.com/docker-for-windows/).</span></span>

#### <a name="installing-git-for-sample-repository"></a><span data-ttu-id="4d53a-193">Instalace Gitu pro ukázkové úložiště</span><span class="sxs-lookup"><span data-stu-id="4d53a-193">Installing Git for sample repository</span></span>

* <span data-ttu-id="4d53a-194">Nainstalujte [git](https://git-scm.com/download) Pokud budete chtít naklonujte úložiště.</span><span class="sxs-lookup"><span data-stu-id="4d53a-194">Install [git](https://git-scm.com/download) if you wish to clone the repository.</span></span>

### <a name="getting-the-sample-application"></a><span data-ttu-id="4d53a-195">Načítání ukázkové aplikace</span><span class="sxs-lookup"><span data-stu-id="4d53a-195">Getting the sample application</span></span>

<span data-ttu-id="4d53a-196">Nejjednodušší způsob, jak získat ukázky je to klonováním [úložiště .NET Core Dockeru](https://github.com/dotnet/dotnet-docker) s úložištěm git, pomocí následujících pokynů:</span><span class="sxs-lookup"><span data-stu-id="4d53a-196">The easiest way to get the sample is by cloning the [.NET Core Docker repository](https://github.com/dotnet/dotnet-docker) with git, using the following instructions:</span></span> 

```console
git clone https://github.com/dotnet/dotnet-docker
```

<span data-ttu-id="4d53a-197">Úložiště (je malé) můžete také stáhnout jako soubor zip z úložiště .NET Core Docker.</span><span class="sxs-lookup"><span data-stu-id="4d53a-197">You can also download the repository (it is small) as a zip from the .NET Core Docker repository.</span></span>

### <a name="run-the-aspnet-app-locally"></a><span data-ttu-id="4d53a-198">Místní spuštění aplikace ASP.NET</span><span class="sxs-lookup"><span data-stu-id="4d53a-198">Run the ASP.NET app locally</span></span>

<span data-ttu-id="4d53a-199">Pro referenční bod než jsme kontejnerizace aplikace, nejprve spusťte aplikaci místně.</span><span class="sxs-lookup"><span data-stu-id="4d53a-199">For a reference point, before we containerize the application, first run the application locally.</span></span>

<span data-ttu-id="4d53a-200">Můžete sestavit a spustit aplikaci místně pomocí sady SDK .NET Core 2.1 pomocí následujících příkazů (pokyny předpokládají kořenovém adresáři úložiště):</span><span class="sxs-lookup"><span data-stu-id="4d53a-200">You can build and run the application locally with the .NET Core 2.1 SDK using the following commands (The instructions assume the root of the repository):</span></span>

```console
cd dotnet-docker
cd samples
cd aspnetapp // solution scope where the dockerfile is located
cd aspnetapp // project scope

dotnet run
```

<span data-ttu-id="4d53a-201">Po spuštění aplikace, navštivte **http://localhost:5000** ve webovém prohlížeči.</span><span class="sxs-lookup"><span data-stu-id="4d53a-201">After the application starts, visit **http://localhost:5000** in your web browser.</span></span>

### <a name="build-and-run-the-sample-with-docker-for-linux-containers"></a><span data-ttu-id="4d53a-202">Sestavte a spusťte ukázku s prostředím Docker pro kontejnery Linuxu</span><span class="sxs-lookup"><span data-stu-id="4d53a-202">Build and run the sample with Docker for Linux containers</span></span>

<span data-ttu-id="4d53a-203">Můžete sestavit a spustit ukázku v Dockeru pomocí kontejnerů Linuxu pomocí následujících příkazů (pokyny předpokládají kořenovém adresáři úložiště):</span><span class="sxs-lookup"><span data-stu-id="4d53a-203">You can build and run the sample in Docker using Linux containers using the following commands (The instructions assume the root of the repository):</span></span>

```console
cd dotnet-docker
cd samples
cd aspnetapp // solution scope where the dockerfile is located

docker build -t aspnetapp .
docker run -it --rm -p 5000:80 --name aspnetcore_sample aspnetapp
```

> [!NOTE]
> <span data-ttu-id="4d53a-204">`docker run` "-P" argument portu 5000 na místním počítači na port 80 v kontejneru mapy (formulář mapování portů je `host:container`).</span><span class="sxs-lookup"><span data-stu-id="4d53a-204">The `docker run` '-p' argument maps port 5000 on your local machine to port 80 in the container (the port mapping form is `host:container`).</span></span> <span data-ttu-id="4d53a-205">Další informace najdete v tématu [dockeru spustit](https://docs.docker.com/engine/reference/commandline/exec/) odkaz na parametry příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="4d53a-205">For more information, see the [docker run](https://docs.docker.com/engine/reference/commandline/exec/) reference on command-line parameters.</span></span>

<span data-ttu-id="4d53a-206">Po spuštění aplikace, navštivte **http://localhost:5000** ve webovém prohlížeči.</span><span class="sxs-lookup"><span data-stu-id="4d53a-206">After the application starts, visit **http://localhost:5000** in your web browser.</span></span>

### <a name="build-and-run-the-sample-with-docker-for-windows-containers"></a><span data-ttu-id="4d53a-207">Sestavte a spusťte ukázku s kontejnery Docker pro Windows</span><span class="sxs-lookup"><span data-stu-id="4d53a-207">Build and run the sample with Docker for Windows containers</span></span>

<span data-ttu-id="4d53a-208">Můžete sestavit a spustit ukázku v Dockeru pomocí kontejnerů Windows pomocí následujících příkazů (pokyny předpokládají kořenovém adresáři úložiště):</span><span class="sxs-lookup"><span data-stu-id="4d53a-208">You can build and run the sample in Docker using Windows containers using the following commands (The instructions assume the root of the repository):</span></span>

```console
cd dotnet-docker
cd samples
cd aspnetapp // solution scope where the dockerfile is located

docker build -t aspnetapp .
docker run -it --rm --name aspnetcore_sample aspnetapp
```

> [!IMPORTANT]
> <span data-ttu-id="4d53a-209">Je nutné na Přejít **IP adresu kontejneru** (nikoli http://localhost) v prohlížeči přímo při používání kontejnerů Windows.</span><span class="sxs-lookup"><span data-stu-id="4d53a-209">You must navigate to the **container IP address** (as opposed to http://localhost) in your browser directly when using Windows containers.</span></span> <span data-ttu-id="4d53a-210">Můžete získat IP adresu vašeho kontejneru pomocí následujících kroků:</span><span class="sxs-lookup"><span data-stu-id="4d53a-210">You can get the IP address of your container with the following steps:</span></span>

* <span data-ttu-id="4d53a-211">Otevřete jiného příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="4d53a-211">Open up another command prompt.</span></span>
* <span data-ttu-id="4d53a-212">Spustit `docker ps` zobrazte spuštěné kontejnery.</span><span class="sxs-lookup"><span data-stu-id="4d53a-212">Run `docker ps` to see your running containers.</span></span> <span data-ttu-id="4d53a-213">Kontejner "aspnetcore_sample" by měl být existuje.</span><span class="sxs-lookup"><span data-stu-id="4d53a-213">The "aspnetcore_sample" container should be there.</span></span>
* <span data-ttu-id="4d53a-214">Spustit `docker exec aspnetcore_sample ipconfig`.</span><span class="sxs-lookup"><span data-stu-id="4d53a-214">Run `docker exec aspnetcore_sample ipconfig`.</span></span>
* <span data-ttu-id="4d53a-215">Zkopírujte IP adresu kontejneru a vložte do prohlížeče (například 172.29.245.43).</span><span class="sxs-lookup"><span data-stu-id="4d53a-215">Copy the container IP address and paste into your browser (for example, 172.29.245.43).</span></span>

> [!NOTE]
> <span data-ttu-id="4d53a-216">Docker exec podporuje identifikační kontejnery s názvem nebo hodnoty hash.</span><span class="sxs-lookup"><span data-stu-id="4d53a-216">Docker exec supports identifying containers with name or hash.</span></span> <span data-ttu-id="4d53a-217">Název (aspnetcore_sample) se používá v našem příkladu.</span><span class="sxs-lookup"><span data-stu-id="4d53a-217">The name (aspnetcore_sample) is used in our example.</span></span>

<span data-ttu-id="4d53a-218">Podívejte se na následující příklad toho, jak získat IP adresu spuštěný kontejner Windows.</span><span class="sxs-lookup"><span data-stu-id="4d53a-218">See the following example of how to get the IP address of a running Windows container.</span></span>

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

> [!NOTE]
> <span data-ttu-id="4d53a-219">Nový příkaz exec dockeru běží v spuštěný kontejner.</span><span class="sxs-lookup"><span data-stu-id="4d53a-219">Docker exec runs a new command in a running container.</span></span> <span data-ttu-id="4d53a-220">Další informace najdete v tématu [docker exec odkaz](https://docs.docker.com/engine/reference/commandline/exec/) na parametry příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="4d53a-220">For more information, see the [docker exec reference](https://docs.docker.com/engine/reference/commandline/exec/) on command-line parameters.</span></span>

<span data-ttu-id="4d53a-221">Můžete vytvářet aplikace, která je připravená k nasazení do produkčního prostředí místně s použitím [dotnet publikovat](../tools/dotnet-publish.md) příkazu.</span><span class="sxs-lookup"><span data-stu-id="4d53a-221">You can produce an application that is ready to deploy to production locally using the [dotnet publish](../tools/dotnet-publish.md) command.</span></span>

```console
dotnet publish -c Release -o published
```

> [!NOTE]
> <span data-ttu-id="4d53a-222">- C verze argument sestavení aplikace v režimu vydání (výchozí hodnota je režim ladění).</span><span class="sxs-lookup"><span data-stu-id="4d53a-222">The -c Release argument builds the application in release mode (the default is debug mode).</span></span> <span data-ttu-id="4d53a-223">Další informace najdete v tématu [dotnet spusťte odkaz](../tools/dotnet-run.md) na parametry příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="4d53a-223">For more information, see the [dotnet run reference](../tools/dotnet-run.md) on command-line parameters.</span></span>

<span data-ttu-id="4d53a-224">Aplikaci můžete spustit na **Windows** pomocí následujícího příkazu.</span><span class="sxs-lookup"><span data-stu-id="4d53a-224">You can run the application on **Windows** using the following command.</span></span>

```console
dotnet published\aspnetapp.dll
```

<span data-ttu-id="4d53a-225">Aplikaci můžete spustit na **Linux** nebo **macOS** pomocí následujícího příkazu.</span><span class="sxs-lookup"><span data-stu-id="4d53a-225">You can run the application on **Linux** or **macOS** using the following command.</span></span>

```bash
dotnet published/aspnetapp.dll
```

### <a name="docker-images-used-in-this-sample"></a><span data-ttu-id="4d53a-226">Používané v tomto příkladu Imagí dockeru</span><span class="sxs-lookup"><span data-stu-id="4d53a-226">Docker Images used in this sample</span></span>

<span data-ttu-id="4d53a-227">Následující Image Dockeru se používají v této ukázce souboru dockerfile.</span><span class="sxs-lookup"><span data-stu-id="4d53a-227">The following Docker images are used in this sample's dockerfile.</span></span>

* `microsoft/dotnet:2.1-sdk`
* `microsoft/dotnet:2.1-aspnetcore-runtime`

<span data-ttu-id="4d53a-228">Blahopřejeme!</span><span class="sxs-lookup"><span data-stu-id="4d53a-228">Congratulations!</span></span> <span data-ttu-id="4d53a-229">máte jen:</span><span class="sxs-lookup"><span data-stu-id="4d53a-229">you have just:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="4d53a-230">Dozvěděli jste se o imagích Dockeru rozhraní Microsoft .NET Core</span><span class="sxs-lookup"><span data-stu-id="4d53a-230">Learned about Microsoft .NET Core Docker images</span></span>
> * <span data-ttu-id="4d53a-231">Ukázkovou aplikaci do Dockerize je teď v ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="4d53a-231">Got an ASP.NET Core sample app to Dockerize</span></span>
> * <span data-ttu-id="4d53a-232">Spuštění ukázkové aplikace ASP.NET místně</span><span class="sxs-lookup"><span data-stu-id="4d53a-232">Ran the ASP.NET sample app locally</span></span>
> * <span data-ttu-id="4d53a-233">Vytvořené a spustili ukázku s prostředím Docker pro kontejnery Linuxu</span><span class="sxs-lookup"><span data-stu-id="4d53a-233">Built and ran the sample with Docker for Linux containers</span></span>
> * <span data-ttu-id="4d53a-234">Vytvořené a spustili ukázku s kontejnery Docker pro Windows</span><span class="sxs-lookup"><span data-stu-id="4d53a-234">Built and ran the sample with Docker for Windows containers</span></span>

<span data-ttu-id="4d53a-235">**Další kroky**</span><span class="sxs-lookup"><span data-stu-id="4d53a-235">**Next Steps**</span></span>

<span data-ttu-id="4d53a-236">Tady jsou některé další kroky, které si můžete:</span><span class="sxs-lookup"><span data-stu-id="4d53a-236">Here are some next steps you can take:</span></span>

* [<span data-ttu-id="4d53a-237">Práce s nástroji Dockeru pro Visual Studio</span><span class="sxs-lookup"><span data-stu-id="4d53a-237">Working with Visual Studio Docker Tools</span></span>](https://docs.microsoft.com/aspnet/core/publishing/visual-studio-tools-for-docker)
* [<span data-ttu-id="4d53a-238">Nasazování Imagí Dockeru ze služby Azure Container Registry do služby Azure Container Instances</span><span class="sxs-lookup"><span data-stu-id="4d53a-238">Deploying Docker Images from the Azure Container Registry to Azure Container Instances</span></span>](https://blogs.msdn.microsoft.com/stevelasker/2017/07/28/deploying-docker-images-from-the-azure-container-registry-to-azure-container-instances/)
* [<span data-ttu-id="4d53a-239">Ladění ve Visual Studiu Code</span><span class="sxs-lookup"><span data-stu-id="4d53a-239">Debugging with Visual Studio Code</span></span>](https://code.visualstudio.com/docs/nodejs/debugging-recipes#_nodejs-typescript-docker-container) 
* [<span data-ttu-id="4d53a-240">Praktické ukázky sady Visual Studio pro Mac, kontejnery a kód bez serveru v cloudu</span><span class="sxs-lookup"><span data-stu-id="4d53a-240">Getting hands on with Visual Studio for Mac, containers, and serverless code in the cloud</span></span>](https://blogs.msdn.microsoft.com/visualstudio/2017/08/31/hands-on-with-visual-studio-for-mac-containers-serverless-code-in-the-cloud/#comments)
* [<span data-ttu-id="4d53a-241">Začínáme s Dockerem a sady Visual Studio pro Mac testovacího prostředí</span><span class="sxs-lookup"><span data-stu-id="4d53a-241">Getting Started with Docker and Visual Studio for Mac Lab</span></span>](https://github.com/Microsoft/vs4mac-labs/tree/master/Docker/Getting-Started)

> [!NOTE]
> <span data-ttu-id="4d53a-242">Pokud nemáte předplatné Azure, [zaregistrujte se ještě dnes](https://azure.microsoft.com/free/?b=16.48) pro bezplatný účet 30 dní a získat 200 USD v kreditech Azure pro vyzkoušení jakékoli kombinace služeb Azure.</span><span class="sxs-lookup"><span data-stu-id="4d53a-242">If you do not have an Azure subscription, [sign up today](https://azure.microsoft.com/free/?b=16.48) for a free 30-day account and get $200 in Azure Credits to try out any combination of Azure services.</span></span>
