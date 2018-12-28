---
title: Přehled Image dockeru
description: Další informace o použití publikovaných imagí Dockeru .NET Core z registru Dockeru. Také se dozvíte, jak o přijetí změn imagí a vytvoření vlastních imagí.
ms.date: 11/06/2017
ms.topic: tutorial
ms.custom: mvc, seodec18
ms.openlocfilehash: dd8c6c500dc2177768e6cba0c1e303950e20d4f3
ms.sourcegitcommit: 3d0c29b878f00caec288dfecb3a5c959de5aa629
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/20/2018
ms.locfileid: "53656034"
---
# <a name="learn-about-docker-images-for-net-core"></a><span data-ttu-id="f9e4c-104">Další informace o imagích Dockeru pro .NET Core</span><span class="sxs-lookup"><span data-stu-id="f9e4c-104">Learn about Docker images for .NET Core</span></span>

<span data-ttu-id="f9e4c-105">V tomto kurzu se zaměříme na tom, jak pomocí .NET Core v Dockeru.</span><span class="sxs-lookup"><span data-stu-id="f9e4c-105">In this tutorial, We focus on how to use .NET Core on Docker.</span></span> <span data-ttu-id="f9e4c-106">Nejprve podíváme na různé imagí Dockeru k dispozici a spravován společností Microsoft a případy použití.</span><span class="sxs-lookup"><span data-stu-id="f9e4c-106">First, we explore the different Docker images offered and maintained by Microsoft, and use cases.</span></span> <span data-ttu-id="f9e4c-107">Potom jsme zjistěte, jak sestavit a dockerizace aplikace ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="f9e4c-107">We then learn how to build and dockerize an ASP.NET Core app.</span></span>

<span data-ttu-id="f9e4c-108">V průběhu tohoto kurzu se dozvíte:</span><span class="sxs-lookup"><span data-stu-id="f9e4c-108">During the course of this tutorial, you learn:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="f9e4c-109">Další informace o imagích Dockeru rozhraní Microsoft .NET Core</span><span class="sxs-lookup"><span data-stu-id="f9e4c-109">Learn about Microsoft .NET Core Docker images</span></span> 
> * <span data-ttu-id="f9e4c-110">Získat ASP.NET Core ukázkovou aplikaci do Dockerize</span><span class="sxs-lookup"><span data-stu-id="f9e4c-110">Get an ASP.NET Core sample app to Dockerize</span></span>
> * <span data-ttu-id="f9e4c-111">Spuštění ukázkové aplikace ASP.NET místně</span><span class="sxs-lookup"><span data-stu-id="f9e4c-111">Run the ASP.NET sample app locally</span></span>
> * <span data-ttu-id="f9e4c-112">Sestavte a spusťte ukázku s prostředím Docker pro kontejnery Linuxu</span><span class="sxs-lookup"><span data-stu-id="f9e4c-112">Build and run the sample with Docker for Linux containers</span></span>
> * <span data-ttu-id="f9e4c-113">Sestavte a spusťte ukázku s kontejnery Docker pro Windows</span><span class="sxs-lookup"><span data-stu-id="f9e4c-113">Build and run the sample with Docker for Windows containers</span></span>

## <a name="docker-image-optimizations"></a><span data-ttu-id="f9e4c-114">Optimalizace Image dockeru</span><span class="sxs-lookup"><span data-stu-id="f9e4c-114">Docker Image Optimizations</span></span>

<span data-ttu-id="f9e4c-115">Při vytváření imagí Dockeru pro vývojáře, jsme se zaměřili na třech hlavních scénářích:</span><span class="sxs-lookup"><span data-stu-id="f9e4c-115">When building Docker images for developers, we focused on three main scenarios:</span></span>

* <span data-ttu-id="f9e4c-116">Obrázky používané pro vývoj aplikací .NET Core</span><span class="sxs-lookup"><span data-stu-id="f9e4c-116">Images used to develop .NET Core apps</span></span>
* <span data-ttu-id="f9e4c-117">Image sloužící k sestavení aplikace .NET Core</span><span class="sxs-lookup"><span data-stu-id="f9e4c-117">Images used to build .NET Core apps</span></span>
* <span data-ttu-id="f9e4c-118">Obrázky používané ke spouštění aplikací .NET Core</span><span class="sxs-lookup"><span data-stu-id="f9e4c-118">Images used to run .NET Core apps</span></span>

<span data-ttu-id="f9e4c-119">Proč tři Image?</span><span class="sxs-lookup"><span data-stu-id="f9e4c-119">Why three images?</span></span>
<span data-ttu-id="f9e4c-120">Při vývoji, vytváření a spouštění kontejnerizovaných aplikací, jsme mají různé priority.</span><span class="sxs-lookup"><span data-stu-id="f9e4c-120">When developing, building, and running containerized applications, we have different priorities.</span></span>

* <span data-ttu-id="f9e4c-121">**Vývoj aplikací:**  Priorita se zaměřuje na rychle iterovat změny a možnost ladit změny.</span><span class="sxs-lookup"><span data-stu-id="f9e4c-121">**Development:**  The priority focuses on quickly iterate changes, and the ability to debug the changes.</span></span> <span data-ttu-id="f9e4c-122">Velikost bitové kopie není důležité, místo toho můžete provést změny kódu a rychle vidět?</span><span class="sxs-lookup"><span data-stu-id="f9e4c-122">The size of the image isn't as important, rather can you make changes to your code and see them quickly?</span></span>

* <span data-ttu-id="f9e4c-123">**Sestavení:** Tato image obsahuje vše potřebné pro kompilaci aplikace, které zahrnují kompilátor a další závislosti optimalizovat binární soubory.</span><span class="sxs-lookup"><span data-stu-id="f9e4c-123">**Build:** This image contains everything needed to compile your app, which includes the compiler and any other dependencies to optimize the binaries.</span></span>  <span data-ttu-id="f9e4c-124">Sestavení image použijete k vytvoření majetek, který umístíte do produkčního prostředí image.</span><span class="sxs-lookup"><span data-stu-id="f9e4c-124">You use the build image to create the assets you place into a production image.</span></span> <span data-ttu-id="f9e4c-125">Sestavení image se použije pro průběžnou integraci, nebo v prostředí sestavení.</span><span class="sxs-lookup"><span data-stu-id="f9e4c-125">The build image would be used for continuous integration, or in a build environment.</span></span> <span data-ttu-id="f9e4c-126">Tento přístup umožňuje agenta sestavení pro zkompilování a vybuildování aplikace (s všechny požadované závislosti) v instanci bitové kopie sestavení.</span><span class="sxs-lookup"><span data-stu-id="f9e4c-126">This approach allows a build agent to compile and build the application (with all the required dependencies) in a build image instance.</span></span> <span data-ttu-id="f9e4c-127">Agenta sestavení stačí vědět, jak ke spuštění této image Dockeru.</span><span class="sxs-lookup"><span data-stu-id="f9e4c-127">Your build agent only needs to know how to run this Docker image.</span></span>

* <span data-ttu-id="f9e4c-128">**Produkční:** Jak rychle můžete nasadit a spustit image?</span><span class="sxs-lookup"><span data-stu-id="f9e4c-128">**Production:** How fast you can deploy and start your image?</span></span> <span data-ttu-id="f9e4c-129">Tato image je malé, takže je optimalizován výkon sítě z registru Dockeru do Docker hostitelů.</span><span class="sxs-lookup"><span data-stu-id="f9e4c-129">This image is small so network performance from your Docker Registry to your Docker hosts is optimized.</span></span> <span data-ttu-id="f9e4c-130">Obsah je připraven ke spuštění povolení nejrychlejší doba od Dockeru, spusťte na zpracování výsledků.</span><span class="sxs-lookup"><span data-stu-id="f9e4c-130">The contents are ready to run enabling the fastest time from Docker run to processing results.</span></span> <span data-ttu-id="f9e4c-131">Dynamický kód kompilace, není nutná v modelu Dockeru.</span><span class="sxs-lookup"><span data-stu-id="f9e4c-131">Dynamic code compilation isn't needed in the Docker model.</span></span> <span data-ttu-id="f9e4c-132">Obsah, který umístíte do této bitové kopie omezeny na binární soubory a obsah potřebný ke spuštění aplikace.</span><span class="sxs-lookup"><span data-stu-id="f9e4c-132">The content you place in this image would be limited to the binaries and content needed to run the application.</span></span>

    <span data-ttu-id="f9e4c-133">Například `dotnet publish` výstup obsahuje:</span><span class="sxs-lookup"><span data-stu-id="f9e4c-133">For example, the `dotnet publish` output contains:</span></span>

    * <span data-ttu-id="f9e4c-134">kompilované binární soubory</span><span class="sxs-lookup"><span data-stu-id="f9e4c-134">the compiled binaries</span></span>
    * <span data-ttu-id="f9e4c-135">soubory JS a CSS</span><span class="sxs-lookup"><span data-stu-id="f9e4c-135">.js and .css files</span></span>


<span data-ttu-id="f9e4c-136">Z důvodu chcete zahrnout `dotnet publish` výstupu příkazu v bitové kopii produkčního prostředí o jeho velikost na minimum.</span><span class="sxs-lookup"><span data-stu-id="f9e4c-136">The reason to include the `dotnet publish` command output in your production image is to keep its size to a minimum.</span></span>

<span data-ttu-id="f9e4c-137">Některé obrázky .NET Core sdílení vrstev mezi různých klíčových slov, takže stahování nejnovějších značka je poměrně jednoduchý proces.</span><span class="sxs-lookup"><span data-stu-id="f9e4c-137">Some .NET Core images share layers between different tags so downloading the latest tag is a relatively lightweight process.</span></span> <span data-ttu-id="f9e4c-138">Pokud už máte starší verzi na svém počítači, tato architektura zmenšuje místo na disku potřebné.</span><span class="sxs-lookup"><span data-stu-id="f9e4c-138">If you already have an older version on your machine, this architecture decreases the needed disk space.</span></span>

<span data-ttu-id="f9e4c-139">Při obvyklých imagí používat více aplikací ve stejném počítači, je paměť sdílená mezi obvyklých imagí.</span><span class="sxs-lookup"><span data-stu-id="f9e4c-139">When multiple applications use common images on the same machine, memory is shared between the common images.</span></span> <span data-ttu-id="f9e4c-140">Image se musí shodovat s ke sdílení.</span><span class="sxs-lookup"><span data-stu-id="f9e4c-140">The images must be the same to be shared.</span></span>

## <a name="docker-image-variations"></a><span data-ttu-id="f9e4c-141">Variace image dockeru</span><span class="sxs-lookup"><span data-stu-id="f9e4c-141">Docker image variations</span></span>

<span data-ttu-id="f9e4c-142">K dosažení cílů výše, poskytujeme varianty image v rámci [ `microsoft/dotnet` ](https://hub.docker.com/r/microsoft/dotnet/).</span><span class="sxs-lookup"><span data-stu-id="f9e4c-142">To achieve the goals above, we provide image variants under [`microsoft/dotnet`](https://hub.docker.com/r/microsoft/dotnet/).</span></span>

* <span data-ttu-id="f9e4c-143">`microsoft/dotnet:<version>-sdk`(`microsoft/dotnet:2.1-sdk`) Tento obrázek obsahuje sady .NET Core SDK, která zahrnuje .NET Core a nástroje příkazového řádku (CLI).</span><span class="sxs-lookup"><span data-stu-id="f9e4c-143">`microsoft/dotnet:<version>-sdk`(`microsoft/dotnet:2.1-sdk`) This image contains the .NET Core SDK, which includes the .NET Core and Command Line Tools (CLI).</span></span> <span data-ttu-id="f9e4c-144">Tento obrázek mapuje **scénář vývoje**.</span><span class="sxs-lookup"><span data-stu-id="f9e4c-144">This image maps to the **development scenario**.</span></span> <span data-ttu-id="f9e4c-145">Použít tuto bitovou kopii pro místní vývoj, ladění a testování částí.</span><span class="sxs-lookup"><span data-stu-id="f9e4c-145">You use this image for local development, debugging, and unit testing.</span></span> <span data-ttu-id="f9e4c-146">Tato image je také možné pro vaši **sestavení** scénáře.</span><span class="sxs-lookup"><span data-stu-id="f9e4c-146">This image can also be used for your **build** scenarios.</span></span> <span data-ttu-id="f9e4c-147">Pomocí `microsoft/dotnet:sdk` vždy obsahuje nejnovější verzi.</span><span class="sxs-lookup"><span data-stu-id="f9e4c-147">Using `microsoft/dotnet:sdk` always gives you the latest version.</span></span>

> [!TIP]
> <span data-ttu-id="f9e4c-148">Pokud si nejste jistí o vašim potřebám, kterou chcete použít `microsoft/dotnet:<version>-sdk` bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="f9e4c-148">If you are unsure about your needs, you want to use the `microsoft/dotnet:<version>-sdk` image.</span></span> <span data-ttu-id="f9e4c-149">Jako "de facto stane" image, je určený pro použití jako throw tokeny kontejneru (připojit svůj zdrojový kód a spustit kontejner pro spuštění vaší aplikace) a jako základní image k vytvoření další Image z.</span><span class="sxs-lookup"><span data-stu-id="f9e4c-149">As the "de facto" image, it's designed to be used as a throw away container (mount your source code and start the container to start your app), and as the base image to build other images from.</span></span>

* <span data-ttu-id="f9e4c-150">`microsoft/dotnet:<version>-runtime`: Tato image obsahuje .NET Core (prostředí runtime a knihovny) a je optimalizovaná pro spouštění aplikací .NET Core **produkční**.</span><span class="sxs-lookup"><span data-stu-id="f9e4c-150">`microsoft/dotnet:<version>-runtime`: This image contains the .NET Core (runtime and libraries) and is optimized for running .NET Core apps in **production**.</span></span>

## <a name="alternative-images"></a><span data-ttu-id="f9e4c-151">Alternativní imagí</span><span class="sxs-lookup"><span data-stu-id="f9e4c-151">Alternative images</span></span>

<span data-ttu-id="f9e4c-152">Kromě optimalizované scénáře vývoje, sestavení a produkčním prostředí Nabízíme další Image:</span><span class="sxs-lookup"><span data-stu-id="f9e4c-152">In addition to the optimized scenarios of development, build and production, we provide additional images:</span></span>

* <span data-ttu-id="f9e4c-153">`microsoft/dotnet:<version>-runtime-deps`: **Runtime deps** bitová kopie obsahuje operační systém se všemi nativní závislosti vyžadované .NET Core.</span><span class="sxs-lookup"><span data-stu-id="f9e4c-153">`microsoft/dotnet:<version>-runtime-deps`: The **runtime-deps** image contains the operating system with all of the native dependencies needed by .NET Core.</span></span> <span data-ttu-id="f9e4c-154">Tento obrázek pochází pro [samostatná aplikace](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="f9e4c-154">This image is for [self-contained applications](../deploying/index.md).</span></span>

<span data-ttu-id="f9e4c-155">Nejnovější verze každého typu variant:</span><span class="sxs-lookup"><span data-stu-id="f9e4c-155">Latest versions of each variant:</span></span>

* <span data-ttu-id="f9e4c-156">`microsoft/dotnet` nebo `microsoft/dotnet:latest` (alias pro bitovou kopii sady SDK)</span><span class="sxs-lookup"><span data-stu-id="f9e4c-156">`microsoft/dotnet` or `microsoft/dotnet:latest` (alias for the SDK image)</span></span>
* `microsoft/dotnet:sdk`
* `microsoft/dotnet:runtime`
* `microsoft/dotnet:runtime-deps`

## <a name="samples-to-explore"></a><span data-ttu-id="f9e4c-157">Prozkoumejte ukázky</span><span class="sxs-lookup"><span data-stu-id="f9e4c-157">Samples to explore</span></span>

* <span data-ttu-id="f9e4c-158">[Tato ukázka ASP.NET Core Docker](https://github.com/dotnet/dotnet-docker/tree/master/samples/aspnetapp) ukazuje vzoru osvědčených postupů pro vytváření imagí Dockeru pro ASP.NET Core aplikace pro produkční prostředí.</span><span class="sxs-lookup"><span data-stu-id="f9e4c-158">[This ASP.NET Core Docker sample](https://github.com/dotnet/dotnet-docker/tree/master/samples/aspnetapp) demonstrates a best practice pattern for building Docker images for ASP.NET Core apps for production.</span></span> <span data-ttu-id="f9e4c-159">Ukázka funguje s kontejnery Windows i Linux.</span><span class="sxs-lookup"><span data-stu-id="f9e4c-159">The sample works with both Linux and Windows containers.</span></span>

* <span data-ttu-id="f9e4c-160">V této aplikaci .NET Core Docker ukázce vzoru osvědčených postupů pro [vytváření imagí Dockeru pro aplikace .NET Core pro produkční prostředí.](https://github.com/dotnet/dotnet-docker/tree/master/samples/dotnetapp)</span><span class="sxs-lookup"><span data-stu-id="f9e4c-160">This .NET Core Docker sample demonstrates a best practice pattern for [building Docker images for .NET Core apps for production.](https://github.com/dotnet/dotnet-docker/tree/master/samples/dotnetapp)</span></span>

## <a name="forward-the-request-scheme-and-original-ip-address"></a><span data-ttu-id="f9e4c-161">Schéma požadavku a původní IP adresa</span><span class="sxs-lookup"><span data-stu-id="f9e4c-161">Forward the request scheme and original IP address</span></span>

<span data-ttu-id="f9e4c-162">Proxy servery, nástroje pro vyrovnávání zatížení a jiných síťových zařízení často skryl informace o požadavku předtím, než dosáhne kontejnerizovanou aplikaci:</span><span class="sxs-lookup"><span data-stu-id="f9e4c-162">Proxy servers, load balancers, and other network appliances often obscure information about a request before it reaches the containerized app:</span></span>

* <span data-ttu-id="f9e4c-163">Pokud požadavky HTTPS jsou směrovány přes proxy server pomocí protokolu HTTP, původní schéma (HTTPS) ztratí a musí předávat v hlavičce.</span><span class="sxs-lookup"><span data-stu-id="f9e4c-163">When HTTPS requests are proxied over HTTP, the original scheme (HTTPS) is lost and must be forwarded in a header.</span></span>
* <span data-ttu-id="f9e4c-164">Protože aplikace obdrží žádost z proxy serveru a není true zdroj na Internetu nebo podnikové sítě, musí v hlavičce předané původní IP adresa klienta.</span><span class="sxs-lookup"><span data-stu-id="f9e4c-164">Because an app receives a request from the proxy and not its true source on the Internet or corporate network, the original client IP address must also be forwarded in a header.</span></span>

<span data-ttu-id="f9e4c-165">Tyto informace mohou být důležité pro zpracování žádostí, například v přesměrování ověřování, generování odkazů, hodnocení zásad a informace o zeměpisné poloze klienta.</span><span class="sxs-lookup"><span data-stu-id="f9e4c-165">This information may be important in request processing, for example in redirects, authentication, link generation, policy evaluation, and client geolocation.</span></span>

<span data-ttu-id="f9e4c-166">Přeposílat schéma a původní IP adresy pro kontejnerizované aplikace ASP.NET Core, používají předané Middleware záhlaví.</span><span class="sxs-lookup"><span data-stu-id="f9e4c-166">To forward the scheme and original IP address to a containerized ASP.NET Core app, use Forwarded Headers Middleware.</span></span> <span data-ttu-id="f9e4c-167">Další informace najdete v tématu [konfigurace ASP.NET Core práci se servery proxy a nástroje pro vyrovnávání zatížení](/aspnet/core/host-and-deploy/proxy-load-balancer).</span><span class="sxs-lookup"><span data-stu-id="f9e4c-167">For more information, see [Configure ASP.NET Core to work with proxy servers and load balancers](/aspnet/core/host-and-deploy/proxy-load-balancer).</span></span>

## <a name="your-first-aspnet-core-docker-app"></a><span data-ttu-id="f9e4c-168">Vaše první aplikace ASP.NET Core Dockeru</span><span class="sxs-lookup"><span data-stu-id="f9e4c-168">Your first ASP.NET Core Docker app</span></span>

<span data-ttu-id="f9e4c-169">Pro účely tohoto kurzu umožňuje aplikaci, kterou chceme dockerizace pomocí ukázkové aplikace ASP.NET Core Dockeru.</span><span class="sxs-lookup"><span data-stu-id="f9e4c-169">For this tutorial, lets use an ASP.NET Core Docker sample application for the app we want to dockerize.</span></span> <span data-ttu-id="f9e4c-170">Tato ukázková aplikace ASP.NET Core Docker ukazuje vzoru osvědčených postupů pro vytváření imagí Dockeru pro ASP.NET Core aplikace pro produkční prostředí.</span><span class="sxs-lookup"><span data-stu-id="f9e4c-170">This ASP.NET Core Docker sample application demonstrates a best practice pattern for building Docker images for ASP.NET Core apps for production.</span></span> <span data-ttu-id="f9e4c-171">Ukázka funguje s kontejnery Windows i Linux.</span><span class="sxs-lookup"><span data-stu-id="f9e4c-171">The sample works with both Linux and Windows containers.</span></span>

<span data-ttu-id="f9e4c-172">Soubor Dockerfile vzorovým kódem se vytvoří image Dockeru aplikace ASP.NET Core na základě základní image Dockeru modulu Runtime ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="f9e4c-172">The sample Dockerfile creates an ASP.NET Core application Docker image based off of the ASP.NET Core Runtime Docker base image.</span></span>

<span data-ttu-id="f9e4c-173">Používá [Docker vícefázových sestavení funkce](https://docs.docker.com/engine/userguide/eng-image/multistage-build/) na:</span><span class="sxs-lookup"><span data-stu-id="f9e4c-173">It uses the [Docker multi-stage build feature](https://docs.docker.com/engine/userguide/eng-image/multistage-build/) to:</span></span>

* <span data-ttu-id="f9e4c-174">sestavit ukázku v kontejneru na základě **větší** základní image Dockeru sestavení ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="f9e4c-174">build the sample in a container based on the **larger** ASP.NET Core Build Docker base image</span></span> 
* <span data-ttu-id="f9e4c-175">zkopíruje výsledek poslední sestavení do image Dockeru na základě **menší** základní imagi modulu Runtime ASP.NET Core Dockeru</span><span class="sxs-lookup"><span data-stu-id="f9e4c-175">copies the final build result into a Docker image based on the **smaller** ASP.NET Core Docker Runtime base image</span></span>

> [!NOTE]
> <span data-ttu-id="f9e4c-176">Sestavení image obsahuje potřebné nástroje pro vytváření aplikací, ale nikoli bitové kopie modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="f9e4c-176">The build image contains required tools to build applications while the runtime image does not.</span></span>

### <a name="prerequisites"></a><span data-ttu-id="f9e4c-177">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f9e4c-177">Prerequisites</span></span>

<span data-ttu-id="f9e4c-178">Sestavte a spusťte, nainstalujte následující položky:</span><span class="sxs-lookup"><span data-stu-id="f9e4c-178">To build and run, install the following items:</span></span>

#### <a name="net-core-21-sdk"></a><span data-ttu-id="f9e4c-179">.NET core 2.1 SDK</span><span class="sxs-lookup"><span data-stu-id="f9e4c-179">.NET Core 2.1 SDK</span></span>

* <span data-ttu-id="f9e4c-180">Nainstalujte [.NET Core 2.1 SDK](https://www.microsoft.com/net/core).</span><span class="sxs-lookup"><span data-stu-id="f9e4c-180">Install [.NET Core 2.1 SDK](https://www.microsoft.com/net/core).</span></span>

* <span data-ttu-id="f9e4c-181">Pokud jste tak dosud neučinili, nainstalujte váš oblíbený editor kódu.</span><span class="sxs-lookup"><span data-stu-id="f9e4c-181">Install your favorite code editor, if you haven't already.</span></span>

> [!TIP]
> <span data-ttu-id="f9e4c-182">Je potřeba nainstalovat editor kódu?</span><span class="sxs-lookup"><span data-stu-id="f9e4c-182">Need to install a code editor?</span></span> <span data-ttu-id="f9e4c-183">Zkuste [sady Visual Studio](https://visualstudio.com/downloads)!</span><span class="sxs-lookup"><span data-stu-id="f9e4c-183">Try [Visual Studio](https://visualstudio.com/downloads)!</span></span>

#### <a name="installing-docker-client"></a><span data-ttu-id="f9e4c-184">Instalace klienta Dockeru</span><span class="sxs-lookup"><span data-stu-id="f9e4c-184">Installing Docker Client</span></span>

<span data-ttu-id="f9e4c-185">Nainstalujte [Docker 18.03](https://docs.docker.com/release-notes/docker-ce/) nebo novější klienta Dockeru.</span><span class="sxs-lookup"><span data-stu-id="f9e4c-185">Install [Docker 18.03](https://docs.docker.com/release-notes/docker-ce/) or later of the Docker client.</span></span>

<span data-ttu-id="f9e4c-186">Klienta Dockeru se dá nainstalovat ve:</span><span class="sxs-lookup"><span data-stu-id="f9e4c-186">The Docker client can be installed in:</span></span>

* <span data-ttu-id="f9e4c-187">Linuxové distribuce</span><span class="sxs-lookup"><span data-stu-id="f9e4c-187">Linux distributions</span></span>

   * [<span data-ttu-id="f9e4c-188">CentOS</span><span class="sxs-lookup"><span data-stu-id="f9e4c-188">CentOS</span></span>](https://docs.docker.com/install/linux/docker-ce/centos/)

   * [<span data-ttu-id="f9e4c-189">Debian</span><span class="sxs-lookup"><span data-stu-id="f9e4c-189">Debian</span></span>](https://docs.docker.com/install/linux/docker-ce/debian/)

   * [<span data-ttu-id="f9e4c-190">Fedora</span><span class="sxs-lookup"><span data-stu-id="f9e4c-190">Fedora</span></span>](https://docs.docker.com/install/linux/docker-ce/fedora/)

   * [<span data-ttu-id="f9e4c-191">Ubuntu</span><span class="sxs-lookup"><span data-stu-id="f9e4c-191">Ubuntu</span></span>](https://docs.docker.com/install/linux/docker-ce/ubuntu/)

* [<span data-ttu-id="f9e4c-192">macOS</span><span class="sxs-lookup"><span data-stu-id="f9e4c-192">macOS</span></span>](https://docs.docker.com/docker-for-mac/install/)

* <span data-ttu-id="f9e4c-193">[Windows](https://docs.docker.com/docker-for-windows/install/).</span><span class="sxs-lookup"><span data-stu-id="f9e4c-193">[Windows](https://docs.docker.com/docker-for-windows/install/).</span></span>

#### <a name="installing-git-for-sample-repository"></a><span data-ttu-id="f9e4c-194">Instalace Gitu pro ukázkové úložiště</span><span class="sxs-lookup"><span data-stu-id="f9e4c-194">Installing Git for sample repository</span></span>

* <span data-ttu-id="f9e4c-195">Nainstalujte [git](https://git-scm.com/download) Pokud budete chtít naklonujte úložiště.</span><span class="sxs-lookup"><span data-stu-id="f9e4c-195">Install [git](https://git-scm.com/download) if you wish to clone the repository.</span></span>

### <a name="getting-the-sample-application"></a><span data-ttu-id="f9e4c-196">Načítání ukázkové aplikace</span><span class="sxs-lookup"><span data-stu-id="f9e4c-196">Getting the sample application</span></span>

<span data-ttu-id="f9e4c-197">Nejjednodušší způsob, jak získat ukázky je to klonováním [úložiště .NET Core Dockeru](https://github.com/dotnet/dotnet-docker) s úložištěm git, pomocí následujících pokynů:</span><span class="sxs-lookup"><span data-stu-id="f9e4c-197">The easiest way to get the sample is by cloning the [.NET Core Docker repository](https://github.com/dotnet/dotnet-docker) with git, using the following instructions:</span></span> 

```console
git clone https://github.com/dotnet/dotnet-docker
```

<span data-ttu-id="f9e4c-198">Úložiště (je malé) můžete také stáhnout jako soubor zip z úložiště .NET Core Docker.</span><span class="sxs-lookup"><span data-stu-id="f9e4c-198">You can also download the repository (it is small) as a zip from the .NET Core Docker repository.</span></span>

### <a name="run-the-aspnet-app-locally"></a><span data-ttu-id="f9e4c-199">Místní spuštění aplikace ASP.NET</span><span class="sxs-lookup"><span data-stu-id="f9e4c-199">Run the ASP.NET app locally</span></span>

<span data-ttu-id="f9e4c-200">Pro referenční bod než jsme kontejnerizace aplikace, nejprve spusťte aplikaci místně.</span><span class="sxs-lookup"><span data-stu-id="f9e4c-200">For a reference point, before we containerize the application, first run the application locally.</span></span>

<span data-ttu-id="f9e4c-201">Můžete sestavit a spustit aplikaci místně pomocí sady SDK .NET Core 2.1 pomocí následujících příkazů (pokyny předpokládají kořenovém adresáři úložiště):</span><span class="sxs-lookup"><span data-stu-id="f9e4c-201">You can build and run the application locally with the .NET Core 2.1 SDK using the following commands (The instructions assume the root of the repository):</span></span>

```console
cd dotnet-docker
cd samples
cd aspnetapp // solution scope where the dockerfile is located
cd aspnetapp // project scope

dotnet run
```

<span data-ttu-id="f9e4c-202">Po spuštění aplikace, navštivte **http://localhost:5000** ve webovém prohlížeči.</span><span class="sxs-lookup"><span data-stu-id="f9e4c-202">After the application starts, visit **http://localhost:5000** in your web browser.</span></span>

### <a name="build-and-run-the-sample-with-docker-for-linux-containers"></a><span data-ttu-id="f9e4c-203">Sestavte a spusťte ukázku s prostředím Docker pro kontejnery Linuxu</span><span class="sxs-lookup"><span data-stu-id="f9e4c-203">Build and run the sample with Docker for Linux containers</span></span>

<span data-ttu-id="f9e4c-204">Můžete sestavit a spustit ukázku v Dockeru pomocí kontejnerů Linuxu pomocí následujících příkazů (pokyny předpokládají kořenovém adresáři úložiště):</span><span class="sxs-lookup"><span data-stu-id="f9e4c-204">You can build and run the sample in Docker using Linux containers using the following commands (The instructions assume the root of the repository):</span></span>

```console
cd dotnet-docker
cd samples
cd aspnetapp // solution scope where the dockerfile is located

docker build -t aspnetapp .
docker run -it --rm -p 5000:80 --name aspnetcore_sample aspnetapp
```

> [!NOTE]
> <span data-ttu-id="f9e4c-205">`docker run` "-P" argument portu 5000 na místním počítači na port 80 v kontejneru mapy (formulář mapování portů je `host:container`).</span><span class="sxs-lookup"><span data-stu-id="f9e4c-205">The `docker run` '-p' argument maps port 5000 on your local machine to port 80 in the container (the port mapping form is `host:container`).</span></span> <span data-ttu-id="f9e4c-206">Další informace najdete v tématu [dockeru spustit](https://docs.docker.com/engine/reference/commandline/exec/) odkaz na parametry příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="f9e4c-206">For more information, see the [docker run](https://docs.docker.com/engine/reference/commandline/exec/) reference on command-line parameters.</span></span>

<span data-ttu-id="f9e4c-207">Po spuštění aplikace, navštivte **http://localhost:5000** ve webovém prohlížeči.</span><span class="sxs-lookup"><span data-stu-id="f9e4c-207">After the application starts, visit **http://localhost:5000** in your web browser.</span></span>

### <a name="build-and-run-the-sample-with-docker-for-windows-containers"></a><span data-ttu-id="f9e4c-208">Sestavte a spusťte ukázku s kontejnery Docker pro Windows</span><span class="sxs-lookup"><span data-stu-id="f9e4c-208">Build and run the sample with Docker for Windows containers</span></span>

<span data-ttu-id="f9e4c-209">Můžete sestavit a spustit ukázku v Dockeru pomocí kontejnerů Windows pomocí následujících příkazů (pokyny předpokládají kořenovém adresáři úložiště):</span><span class="sxs-lookup"><span data-stu-id="f9e4c-209">You can build and run the sample in Docker using Windows containers using the following commands (The instructions assume the root of the repository):</span></span>

```console
cd dotnet-docker
cd samples
cd aspnetapp // solution scope where the dockerfile is located

docker build -t aspnetapp .
docker run -it --rm --name aspnetcore_sample aspnetapp
```

> [!IMPORTANT]
> <span data-ttu-id="f9e4c-210">Je nutné na Přejít **IP adresu kontejneru** (nikoli `http://localhost`) ve svém prohlížeči přímo při používání kontejnerů Windows.</span><span class="sxs-lookup"><span data-stu-id="f9e4c-210">You must navigate to the **container IP address** (as opposed to `http://localhost`) in your browser directly when using Windows containers.</span></span> <span data-ttu-id="f9e4c-211">Můžete získat IP adresu vašeho kontejneru pomocí následujících kroků:</span><span class="sxs-lookup"><span data-stu-id="f9e4c-211">You can get the IP address of your container with the following steps:</span></span>

* <span data-ttu-id="f9e4c-212">Otevřete jiného příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="f9e4c-212">Open up another command prompt.</span></span>
* <span data-ttu-id="f9e4c-213">Spustit `docker ps` zobrazte spuštěné kontejnery.</span><span class="sxs-lookup"><span data-stu-id="f9e4c-213">Run `docker ps` to see your running containers.</span></span> <span data-ttu-id="f9e4c-214">Kontejner "aspnetcore_sample" by měl být existuje.</span><span class="sxs-lookup"><span data-stu-id="f9e4c-214">The "aspnetcore_sample" container should be there.</span></span>
* <span data-ttu-id="f9e4c-215">Spusťte `docker exec aspnetcore_sample ipconfig`.</span><span class="sxs-lookup"><span data-stu-id="f9e4c-215">Run `docker exec aspnetcore_sample ipconfig`.</span></span>
* <span data-ttu-id="f9e4c-216">Zkopírujte IP adresu kontejneru a vložte do prohlížeče (například 172.29.245.43).</span><span class="sxs-lookup"><span data-stu-id="f9e4c-216">Copy the container IP address and paste into your browser (for example, 172.29.245.43).</span></span>

> [!NOTE]
> <span data-ttu-id="f9e4c-217">Docker exec podporuje identifikační kontejnery s názvem nebo hodnoty hash.</span><span class="sxs-lookup"><span data-stu-id="f9e4c-217">Docker exec supports identifying containers with name or hash.</span></span> <span data-ttu-id="f9e4c-218">Název (aspnetcore_sample) se používá v našem příkladu.</span><span class="sxs-lookup"><span data-stu-id="f9e4c-218">The name (aspnetcore_sample) is used in our example.</span></span>

<span data-ttu-id="f9e4c-219">Podívejte se na následující příklad toho, jak získat IP adresu spuštěný kontejner Windows.</span><span class="sxs-lookup"><span data-stu-id="f9e4c-219">See the following example of how to get the IP address of a running Windows container.</span></span>

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
> <span data-ttu-id="f9e4c-220">Nový příkaz exec dockeru běží v spuštěný kontejner.</span><span class="sxs-lookup"><span data-stu-id="f9e4c-220">Docker exec runs a new command in a running container.</span></span> <span data-ttu-id="f9e4c-221">Další informace najdete v tématu [docker exec odkaz](https://docs.docker.com/engine/reference/commandline/exec/) na parametry příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="f9e4c-221">For more information, see the [docker exec reference](https://docs.docker.com/engine/reference/commandline/exec/) on command-line parameters.</span></span>

<span data-ttu-id="f9e4c-222">Můžete vytvářet aplikace, která je připravená k nasazení do produkčního prostředí místně s použitím [dotnet publikovat](../tools/dotnet-publish.md) příkazu.</span><span class="sxs-lookup"><span data-stu-id="f9e4c-222">You can produce an application that is ready to deploy to production locally using the [dotnet publish](../tools/dotnet-publish.md) command.</span></span>

```console
dotnet publish -c Release -o published
```

> [!NOTE]
> <span data-ttu-id="f9e4c-223">- C verze argument sestavení aplikace v režimu vydání (výchozí hodnota je režim ladění).</span><span class="sxs-lookup"><span data-stu-id="f9e4c-223">The -c Release argument builds the application in release mode (the default is debug mode).</span></span> <span data-ttu-id="f9e4c-224">Další informace najdete v tématu [dotnet spusťte odkaz](../tools/dotnet-run.md) na parametry příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="f9e4c-224">For more information, see the [dotnet run reference](../tools/dotnet-run.md) on command-line parameters.</span></span>

<span data-ttu-id="f9e4c-225">Aplikaci můžete spustit na **Windows** pomocí následujícího příkazu.</span><span class="sxs-lookup"><span data-stu-id="f9e4c-225">You can run the application on **Windows** using the following command.</span></span>

```console
dotnet published\aspnetapp.dll
```

<span data-ttu-id="f9e4c-226">Aplikaci můžete spustit na **Linux** nebo **macOS** pomocí následujícího příkazu.</span><span class="sxs-lookup"><span data-stu-id="f9e4c-226">You can run the application on **Linux** or **macOS** using the following command.</span></span>

```bash
dotnet published/aspnetapp.dll
```

### <a name="docker-images-used-in-this-sample"></a><span data-ttu-id="f9e4c-227">Používané v tomto příkladu Imagí dockeru</span><span class="sxs-lookup"><span data-stu-id="f9e4c-227">Docker Images used in this sample</span></span>

<span data-ttu-id="f9e4c-228">Následující Image Dockeru se používají v této ukázce souboru dockerfile.</span><span class="sxs-lookup"><span data-stu-id="f9e4c-228">The following Docker images are used in this sample's dockerfile.</span></span>

* `microsoft/dotnet:2.1-sdk`
* `microsoft/dotnet:2.1-aspnetcore-runtime`

<span data-ttu-id="f9e4c-229">Blahopřejeme!</span><span class="sxs-lookup"><span data-stu-id="f9e4c-229">Congratulations!</span></span> <span data-ttu-id="f9e4c-230">máte jen:</span><span class="sxs-lookup"><span data-stu-id="f9e4c-230">you have just:</span></span>
> [!div class="checklist"]
> * <span data-ttu-id="f9e4c-231">Dozvěděli jste se o imagích Dockeru rozhraní Microsoft .NET Core</span><span class="sxs-lookup"><span data-stu-id="f9e4c-231">Learned about Microsoft .NET Core Docker images</span></span>
> * <span data-ttu-id="f9e4c-232">Ukázkovou aplikaci do Dockerize je teď v ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="f9e4c-232">Got an ASP.NET Core sample app to Dockerize</span></span>
> * <span data-ttu-id="f9e4c-233">Spuštění ukázkové aplikace ASP.NET místně</span><span class="sxs-lookup"><span data-stu-id="f9e4c-233">Ran the ASP.NET sample app locally</span></span>
> * <span data-ttu-id="f9e4c-234">Vytvořené a spustili ukázku s prostředím Docker pro kontejnery Linuxu</span><span class="sxs-lookup"><span data-stu-id="f9e4c-234">Built and ran the sample with Docker for Linux containers</span></span>
> * <span data-ttu-id="f9e4c-235">Vytvořené a spustili ukázku s kontejnery Docker pro Windows</span><span class="sxs-lookup"><span data-stu-id="f9e4c-235">Built and ran the sample with Docker for Windows containers</span></span>

<span data-ttu-id="f9e4c-236">**Další kroky**</span><span class="sxs-lookup"><span data-stu-id="f9e4c-236">**Next Steps**</span></span>

<span data-ttu-id="f9e4c-237">Tady jsou některé další kroky, které si můžete:</span><span class="sxs-lookup"><span data-stu-id="f9e4c-237">Here are some next steps you can take:</span></span>

* [<span data-ttu-id="f9e4c-238">Práce s nástroji Dockeru pro Visual Studio</span><span class="sxs-lookup"><span data-stu-id="f9e4c-238">Working with Visual Studio Docker Tools</span></span>](https://docs.microsoft.com/aspnet/core/publishing/visual-studio-tools-for-docker)
* [<span data-ttu-id="f9e4c-239">Nasazování Imagí Dockeru ze služby Azure Container Registry do služby Azure Container Instances</span><span class="sxs-lookup"><span data-stu-id="f9e4c-239">Deploying Docker Images from the Azure Container Registry to Azure Container Instances</span></span>](https://blogs.msdn.microsoft.com/stevelasker/2017/07/28/deploying-docker-images-from-the-azure-container-registry-to-azure-container-instances/)
* [<span data-ttu-id="f9e4c-240">Ladění ve Visual Studiu Code</span><span class="sxs-lookup"><span data-stu-id="f9e4c-240">Debugging with Visual Studio Code</span></span>](https://code.visualstudio.com/docs/nodejs/debugging-recipes#_nodejs-typescript-docker-container) 
* [<span data-ttu-id="f9e4c-241">Praktické ukázky sady Visual Studio pro Mac, kontejnery a kód bez serveru v cloudu</span><span class="sxs-lookup"><span data-stu-id="f9e4c-241">Getting hands on with Visual Studio for Mac, containers, and serverless code in the cloud</span></span>](https://blogs.msdn.microsoft.com/visualstudio/2017/08/31/hands-on-with-visual-studio-for-mac-containers-serverless-code-in-the-cloud/#comments)
* [<span data-ttu-id="f9e4c-242">Začínáme s Dockerem a sady Visual Studio pro Mac testovacího prostředí</span><span class="sxs-lookup"><span data-stu-id="f9e4c-242">Getting Started with Docker and Visual Studio for Mac Lab</span></span>](https://github.com/Microsoft/vs4mac-labs/tree/master/Docker/Getting-Started)

> [!NOTE]
> <span data-ttu-id="f9e4c-243">Pokud nemáte předplatné Azure, [zaregistrujte se ještě dnes](https://azure.microsoft.com/free/?b=16.48) pro bezplatný účet 30 dní a získat 200 USD v kreditech Azure pro vyzkoušení jakékoli kombinace služeb Azure.</span><span class="sxs-lookup"><span data-stu-id="f9e4c-243">If you do not have an Azure subscription, [sign up today](https://azure.microsoft.com/free/?b=16.48) for a free 30-day account and get $200 in Azure Credits to try out any combination of Azure services.</span></span>
