---
title: Úvod k .NET a Dockeru
description: Principy Dockeru a .NET Core
author: jralexander
ms.author: johalex
ms.date: 11/06/2017
ms.custom: mvc
ms.openlocfilehash: d578ec5a25dbb5de3c88386e212e68cf3b267749
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45970640"
---
# <a name="introduction-to-net-and-docker"></a><span data-ttu-id="b2272-103">Úvod k .NET a Dockeru</span><span class="sxs-lookup"><span data-stu-id="b2272-103">Introduction to .NET and Docker</span></span>

<span data-ttu-id="b2272-104">Tento článek poskytuje úvod a koncepční znalosti potřebné k práci s využitím .NET v Dockeru.</span><span class="sxs-lookup"><span data-stu-id="b2272-104">This article provides an introduction and conceptual background to working with .NET on Docker.</span></span>

## <a name="docker-packaging-your-apps-to-deploy-and-run-anywhere"></a><span data-ttu-id="b2272-105">Docker: Vytváření balíčků aplikací k nasazení a spouštění kdekoli</span><span class="sxs-lookup"><span data-stu-id="b2272-105">Docker: Packaging your apps to deploy and run anywhere</span></span>

<span data-ttu-id="b2272-106">[Docker](../../standard/microservices-architecture/container-docker-introduction/docker-defined.md) je otevřená platforma, která umožňuje vývojářům a správcům sestavení [image](https://docs.docker.com/glossary/?term=image), dodávat a spouštět distribuované aplikace v volně izolovaného prostředí volá [kontejneru](https://www.docker.com/what-container).</span><span class="sxs-lookup"><span data-stu-id="b2272-106">[Docker](../../standard/microservices-architecture/container-docker-introduction/docker-defined.md) is an open platform that enables developers and administrators to build [images](https://docs.docker.com/glossary/?term=image), ship, and run distributed applications in a loosely isolated environment called a [container](https://www.docker.com/what-container).</span></span> <span data-ttu-id="b2272-107">Tento přístup umožňuje správu životního cyklu aplikací efektivní mezi vývojovým, dotazů a odpovědí a produkční prostředí.</span><span class="sxs-lookup"><span data-stu-id="b2272-107">This approach enables efficient application lifecycle management between development, QA, and production environments.</span></span>
 
<span data-ttu-id="b2272-108">[Platforma Docker](https://docs.docker.com/engine/docker-overview/#the-docker-platform) používá [modul Docker](https://docs.docker.com/engine/docker-overview/#docker-engine) k rychlému sestavování a balíčky aplikací jako [imagí Dockeru](https://docs.docker.com/glossary/?term=image) vytvořené pomocí souborů, které jsou napsané v [souboru Dockerfile ](https://docs.docker.com/glossary/?term=Dockerfile) formát, který pak je nasadit a spustit [vrstvy kontejneru](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/#container-and-layers).</span><span class="sxs-lookup"><span data-stu-id="b2272-108">The [Docker platform](https://docs.docker.com/engine/docker-overview/#the-docker-platform) uses the [Docker Engine](https://docs.docker.com/engine/docker-overview/#docker-engine) to quickly build and package apps as [Docker images](https://docs.docker.com/glossary/?term=image) created using files written in the [Dockerfile](https://docs.docker.com/glossary/?term=Dockerfile) format that then is deployed and run in a [layered container](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/#container-and-layers).</span></span>

<span data-ttu-id="b2272-109">Můžete buď vytvořit svoje vlastní [Image na základě úrovní](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/#images-and-layers) jako soubory dockerfile nebo použijte existující z [registru](https://docs.docker.com/glossary/?term=registry), třeba [Docker Hubu](https://docs.docker.com/glossary/?term=Docker%20Hub).</span><span class="sxs-lookup"><span data-stu-id="b2272-109">You can either create your own [layered images](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/#images-and-layers) as dockerfiles or use existing ones from a [registry](https://docs.docker.com/glossary/?term=registry), like [Docker Hub](https://docs.docker.com/glossary/?term=Docker%20Hub).</span></span>

<span data-ttu-id="b2272-110">[Vztah mezi kontejnery Dockeru, obrázky a registry](../../standard/microservices-architecture/container-docker-introduction/docker-containers-images-registries.md) je důležitý koncept při [navrhování a sestavování kontejnerizovaných aplikací nebo mikroslužeb](../../standard/microservices-architecture/architect-microservice-container-applications/index.md).</span><span class="sxs-lookup"><span data-stu-id="b2272-110">The [relationship between Docker containers, images, and registries](../../standard/microservices-architecture/container-docker-introduction/docker-containers-images-registries.md) is an important concept when [architecting and building containerized applications or microservices](../../standard/microservices-architecture/architect-microservice-container-applications/index.md).</span></span> <span data-ttu-id="b2272-111">Tento postup značně zkracuje dobu mezi vývojem a nasazení.</span><span class="sxs-lookup"><span data-stu-id="b2272-111">This approach greatly shortens the time between development and deployment.</span></span>

### <a name="further-reading-and-watching"></a><span data-ttu-id="b2272-112">Další čtení (a sledování)</span><span class="sxs-lookup"><span data-stu-id="b2272-112">Further reading (and watching)</span></span>

* [<span data-ttu-id="b2272-113">Kontejnery založené na Windows: vývoj moderních aplikací s ovládacím prvkem na podnikové úrovni.</span><span class="sxs-lookup"><span data-stu-id="b2272-113">Windows-based containers: Modern app development with enterprise-grade control.</span></span>](https://www.youtube.com/watch?v=Ryx3o0rD5lY&feature=youtu.be)
* [<span data-ttu-id="b2272-114">Přehled dockeru</span><span class="sxs-lookup"><span data-stu-id="b2272-114">Docker overview</span></span>](https://docs.docker.com/engine/docker-overview/)
* [<span data-ttu-id="b2272-115">Soubor Docker na kontejnery Windows</span><span class="sxs-lookup"><span data-stu-id="b2272-115">Dockerfile on Windows Containers</span></span>](/virtualization/windowscontainers/manage-docker/manage-windows-dockerfile)
* [<span data-ttu-id="b2272-116">Osvědčené postupy pro psaní soubory Dockerfile</span><span class="sxs-lookup"><span data-stu-id="b2272-116">Best practices for writing Dockerfiles</span></span>](https://docs.docker.com/engine/userguide/eng-image/dockerfile_best-practices/)
* [<span data-ttu-id="b2272-117">Vytváření Imagí Dockeru pro aplikace .NET Core</span><span class="sxs-lookup"><span data-stu-id="b2272-117">Building Docker Images for .NET Core applications</span></span>](../docker/building-net-docker-images.md)


### <a name="getting-net-docker-images"></a><span data-ttu-id="b2272-118">Získat Image .NET Dockeru</span><span class="sxs-lookup"><span data-stu-id="b2272-118">Getting .NET Docker images</span></span>

<span data-ttu-id="b2272-119">Image Dockeru oficiální .NET jsou vytvořené a optimalizované od Microsoftu.</span><span class="sxs-lookup"><span data-stu-id="b2272-119">The Official .NET Docker images are created and optimized by Microsoft.</span></span> <span data-ttu-id="b2272-120">Jsou veřejně dostupné v Microsoft úložišť v Docker Hubu.</span><span class="sxs-lookup"><span data-stu-id="b2272-120">They are publicly available in the Microsoft repositories on Docker Hub.</span></span> <span data-ttu-id="b2272-121">Každé úložiště může obsahovat více bitových kopií, v závislosti na rozhraní .NET verze a verze operačního systému.</span><span class="sxs-lookup"><span data-stu-id="b2272-121">Each repository can contain multiple images, depending on .NET versions, and on OS versions.</span></span> <span data-ttu-id="b2272-122">Většina úložišť image poskytují rozsáhlé označování můžete vybrat konkrétní verzi rozhraní framework verze a operační systém (distribuce Linuxu nebo verze Windows).</span><span class="sxs-lookup"><span data-stu-id="b2272-122">Most image repos provide extensive tagging to help you select both a specific framework version and an OS (Linux distro or Windows version).</span></span>

## <a name="scenario-based-guidance"></a><span data-ttu-id="b2272-123">Pokyny na základě scénáře</span><span class="sxs-lookup"><span data-stu-id="b2272-123">Scenario based guidance</span></span>

<span data-ttu-id="b2272-124">Záměrem Microsoftu je pro úložiště .NET je detailní a zaměřují se úložiště, které představují konkrétní scénář nebo úlohy.</span><span class="sxs-lookup"><span data-stu-id="b2272-124">Microsoft’s intent for .NET repositories is to have granular and focused repos, which represent a specific scenario or workload.</span></span>

<span data-ttu-id="b2272-125">`microsoft/aspnetcore` Bitové kopie jsou optimalizované pro aplikace ASP.NET Core na Docker, kontejnery můžete začít rychleji.</span><span class="sxs-lookup"><span data-stu-id="b2272-125">The `microsoft/aspnetcore` images are optimized for ASP.NET Core apps on Docker, so containers can start faster.</span></span>

<span data-ttu-id="b2272-126">.NET Core imagí (`microsoft/dotnet`) jsou určené pro konzolové aplikace založené na .NET Core.</span><span class="sxs-lookup"><span data-stu-id="b2272-126">The .NET Core images (`microsoft/dotnet`) are intended for console apps based on .NET Core.</span></span> <span data-ttu-id="b2272-127">Třeba dávkové procesy, Azure WebJobs a další scénáře konzoly používali optimalizované bitové kopie .NET Core.</span><span class="sxs-lookup"><span data-stu-id="b2272-127">For example, batch processes, Azure WebJobs, and other console scenarios should use optimized .NET Core images.</span></span>

<span data-ttu-id="b2272-128">Nejobvyklejšími vodorovné scénář pro používání aplikací Dockeru a .NET je pro produkční nasazení a hostování.</span><span class="sxs-lookup"><span data-stu-id="b2272-128">The most obvious horizontal scenario for using Docker and .NET applications is for production deployment and hosting.</span></span> <span data-ttu-id="b2272-129">Ukázalo se, že je jenom jedním scénářem produkce a ostatní jsou rovnoměrně užitečné.</span><span class="sxs-lookup"><span data-stu-id="b2272-129">It turns out that production is just one scenario and the other ones are equally useful.</span></span> <span data-ttu-id="b2272-130">Tyto scénáře nejsou specifická pro .NET, ale mají používat pro většinu platforem pro vývojáře.</span><span class="sxs-lookup"><span data-stu-id="b2272-130">These scenarios are not specific to .NET, but should apply to most developer platforms.</span></span>

* <span data-ttu-id="b2272-131">**Nainstalujte překážek** – .NET si můžete vyzkoušet bez místní instalace.</span><span class="sxs-lookup"><span data-stu-id="b2272-131">**Low friction install** — You can try out .NET without a local install.</span></span> <span data-ttu-id="b2272-132">Stačí stáhněte image Dockeru s .NET v ní.</span><span class="sxs-lookup"><span data-stu-id="b2272-132">Just download a Docker image with .NET in it.</span></span>

* <span data-ttu-id="b2272-133">**Vývoj v kontejneru** – což vývojovém a produkčním prostředí podobné (předcházení problémů, jako jsou globální stav počítače pro vývojáře) konzistentní prostředí můžete vyvíjet.</span><span class="sxs-lookup"><span data-stu-id="b2272-133">**Develop in a container** — You can develop in a consistent environment, making development and production environments similar (avoiding issues like global state on developer machines).</span></span> <span data-ttu-id="b2272-134">Visual Studio Tools for Docker i umožňují spuštění kontejneru přímo ze sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b2272-134">Visual Studio Tools for Docker even enable you to start a container directly from Visual Studio.</span></span>

* <span data-ttu-id="b2272-135">**Testování v kontejneru** – můžete otestovat v kontejneru, snižuje chyby způsobené nesprávně nakonfigurované prostředí nebo jiné změny zůstat z poslední sady testů.</span><span class="sxs-lookup"><span data-stu-id="b2272-135">**Test in a container** — You can test in a container, reducing failures due to incorrectly configured environments or other changes left behind from the last test.</span></span>

* <span data-ttu-id="b2272-136">**Sestavení v kontejneru** – můžete vytvářet kód v kontejneru, takže není nutné správně nakonfigurovat sdílené sestavení počítače pro více prostředí, ale místo toho přesuňte do "BYOC" (přineste si vlastní kontejner) přístup.</span><span class="sxs-lookup"><span data-stu-id="b2272-136">**Build in a container** — You can build code in a container, avoiding the need to correctly configure shared build machines for multiple environments but instead move to a “BYOC” (bring your own container) approach.</span></span>

* <span data-ttu-id="b2272-137">**Nasazení ve všech prostředích** – nasazujete bitovou kopii prostřednictvím všech vašich prostředích.</span><span class="sxs-lookup"><span data-stu-id="b2272-137">**Deployment in all environments** — You can deploy an image through all of your environments.</span></span> <span data-ttu-id="b2272-138">Tento přístup snižuje chyby způsobené rozdíly konfigurací, obvykle změny chování bitové kopie pomocí externího konfigurace (například vložené proměnné).</span><span class="sxs-lookup"><span data-stu-id="b2272-138">This approach reduces failures due to configuration differences, typically changing the image behavior via external configuration (for example, injected environment variables).</span></span>

<span data-ttu-id="b2272-139">[Obecné pokyny](../../standard/microservices-architecture/net-core-net-framework-containers/general-guidance.md) pro rozhodování mezi .NET Core a .NET Framework pro vývoj kontejnerů Dockeru.</span><span class="sxs-lookup"><span data-stu-id="b2272-139">[General guidance](../../standard/microservices-architecture/net-core-net-framework-containers/general-guidance.md) for deciding between .NET Core and .NET Framework for Docker container development.</span></span>

### <a name="common-docker-development-scenarios"></a><span data-ttu-id="b2272-140">Běžné scénáře vývoje Dockeru</span><span class="sxs-lookup"><span data-stu-id="b2272-140">Common Docker development scenarios</span></span>

#### <a name="net-core"></a><span data-ttu-id="b2272-141">.NET Core</span><span class="sxs-lookup"><span data-stu-id="b2272-141">.NET Core</span></span>

<span data-ttu-id="b2272-142">**.NET core prostředky**</span><span class="sxs-lookup"><span data-stu-id="b2272-142">**.NET Core resources**</span></span>

 <span data-ttu-id="b2272-143">Vyberte si ukázky .NET Core, které odpovídají vaší scénáře, které vás zajímají.</span><span class="sxs-lookup"><span data-stu-id="b2272-143">Pick the .NET Core samples that fit your scenarios of interest.</span></span> <span data-ttu-id="b2272-144">Všechny ukázky pokyny popisují, jak cílit na Windows nebo linuxového Dockeru imagí z hostitele Windows, Linux nebo macOS.</span><span class="sxs-lookup"><span data-stu-id="b2272-144">All sample instructions describe how to target Windows or Linux Docker images from Windows, Linux, or macOS hosts.</span></span>

<span data-ttu-id="b2272-145">Ukázky použití .NET Core 2.0.</span><span class="sxs-lookup"><span data-stu-id="b2272-145">The samples use .NET Core 2.0.</span></span> <span data-ttu-id="b2272-146">Použití Docker [vícefázových sestavení](https://github.com/dotnet/announcements/issues/18) a [více architektury značky](https://github.com/dotnet/announcements/issues/14) spouštějte podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="b2272-146">They use Docker [multi-stage build](https://github.com/dotnet/announcements/issues/18) and [multi-arch tags](https://github.com/dotnet/announcements/issues/14) where appropriate.</span></span>

* [<span data-ttu-id="b2272-147">.NET core Image v Dockerhubu</span><span class="sxs-lookup"><span data-stu-id="b2272-147">.NET Core images on DockerHub</span></span>](https://hub.docker.com/r/microsoft/dotnet/)

* [<span data-ttu-id="b2272-148">Dockerizace aplikací .NET Core</span><span class="sxs-lookup"><span data-stu-id="b2272-148">Dockerize a .NET Core application</span></span>](https://docs.docker.com/engine/examples/dotnetcore/)

* <span data-ttu-id="b2272-149">V této ukázce .NET Core Docker jak [použít Docker ve vývojových procesech .NET Core](https://github.com/dotnet/dotnet-docker-samples/tree/master/dotnetapp-dev).</span><span class="sxs-lookup"><span data-stu-id="b2272-149">This .NET Core Docker sample demonstrates how to [use Docker in your .NET Core development process](https://github.com/dotnet/dotnet-docker-samples/tree/master/dotnetapp-dev).</span></span> <span data-ttu-id="b2272-150">Ukázka funguje s kontejnery Windows i Linux.</span><span class="sxs-lookup"><span data-stu-id="b2272-150">The sample works with both Linux and Windows containers.</span></span>

* <span data-ttu-id="b2272-151">V této aplikaci .NET Core Docker ukázce vzoru osvědčených postupů pro [vytváření imagí Dockeru pro aplikace .NET Core pro produkční prostředí.](https://github.com/dotnet/dotnet-docker-samples/tree/master/dotnetapp-prod)</span><span class="sxs-lookup"><span data-stu-id="b2272-151">This .NET Core Docker sample demonstrates a best practice pattern for [building Docker images for .NET Core apps for production.](https://github.com/dotnet/dotnet-docker-samples/tree/master/dotnetapp-prod)</span></span> <span data-ttu-id="b2272-152">Ukázka funguje s kontejnery Windows i Linux.</span><span class="sxs-lookup"><span data-stu-id="b2272-152">The sample works with both Linux and Windows containers.</span></span>

* <span data-ttu-id="b2272-153">To [.NET Core Docker ukázka](https://github.com/dotnet/dotnet-docker-samples/tree/master/dotnetapp-selfcontained) ukazuje vzor osvědčených postupů pro vytváření imagí Dockeru pro [samostatné aplikace .NET Core](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="b2272-153">This [.NET Core Docker sample](https://github.com/dotnet/dotnet-docker-samples/tree/master/dotnetapp-selfcontained) demonstrates a best practice pattern for building Docker images for [self-contained .NET Core applications](../deploying/index.md).</span></span> <span data-ttu-id="b2272-154">Použít nejmenší kontejneru produkční bez na výhodu plynoucí z [sdílení základní Image mezi kontejnery](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/).</span><span class="sxs-lookup"><span data-stu-id="b2272-154">Used for the smallest production container without a benefit from [sharing base images between containers](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/).</span></span> <span data-ttu-id="b2272-155">Však může sdílet nižších vrstvách Dockeru.</span><span class="sxs-lookup"><span data-stu-id="b2272-155">However, lower Docker layers could be shared.</span></span>

#### <a name="arm32--raspberry-pi"></a><span data-ttu-id="b2272-156">ARM32 / Raspberry Pi</span><span class="sxs-lookup"><span data-stu-id="b2272-156">ARM32 / Raspberry Pi</span></span>

* [<span data-ttu-id="b2272-157">Oznámení sestavení .NET core Runtime ARM32</span><span class="sxs-lookup"><span data-stu-id="b2272-157">.NET Core Runtime ARM32 builds announcement</span></span>](https://github.com/dotnet/announcements/issues/29)

* [<span data-ttu-id="b2272-158">ARM32 / Raspberry Pi .NET Core Image v Dockerhubu</span><span class="sxs-lookup"><span data-stu-id="b2272-158">ARM32 / Raspberry Pi .NET Core images on DockerHub</span></span>](https://hub.docker.com/r/microsoft/dotnet/)

* [<span data-ttu-id="b2272-159">ARM32 / Raspberry Pi .NET Core Docker ukázky na Githubu</span><span class="sxs-lookup"><span data-stu-id="b2272-159">ARM32 / Raspberry Pi .NET Core Docker Samples on GitHub</span></span>](https://github.com/dotnet/dotnet-docker-samples#arm32--raspberry-pi)

#### <a name="net-framework"></a><span data-ttu-id="b2272-160">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="b2272-160">.NET Framework</span></span>

* [<span data-ttu-id="b2272-161">Rozhraní .NET framework Image v Dockerhubu</span><span class="sxs-lookup"><span data-stu-id="b2272-161">.NET Framework images on DockerHub</span></span>](https://hub.docker.com/r/microsoft/dotnet-framework/)

<span data-ttu-id="b2272-162">Toto úložiště obsahuje ukázky, které demonstrují různé konfigurace Dockeru rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b2272-162">This repo contain samples that demonstrate various .NET Framework Docker configurations.</span></span> <span data-ttu-id="b2272-163">Tyto Image můžete použít jako základ pro vlastní Image Dockeru.</span><span class="sxs-lookup"><span data-stu-id="b2272-163">You can use these images as the basis of your own Docker images.</span></span>

<span data-ttu-id="b2272-164">**Rozhraní .NET framework 4.7**</span><span class="sxs-lookup"><span data-stu-id="b2272-164">**.NET Framework 4.7**</span></span>

<span data-ttu-id="b2272-165">[Dotnet-ukázkové rozhraní framework: 4.7](https://github.com/Microsoft/dotnet-framework-docker-samples/tree/master/dotnetapp-4.7) ukazuje základní "hello world" použití [rozhraní .NET Framework 4.7](../../framework/whats-new/index.md#v47).</span><span class="sxs-lookup"><span data-stu-id="b2272-165">The [dotnet-framework:4.7 sample](https://github.com/Microsoft/dotnet-framework-docker-samples/tree/master/dotnetapp-4.7) demonstrates basic "hello world" usage of the [.NET Framework 4.7](../../framework/whats-new/index.md#v47).</span></span> <span data-ttu-id="b2272-166">To se dozvíte, jak můžete sestavení a nasazení aplikace na přijímající [image dockeru pro .NET Framework 4.7](https://github.com/Microsoft/dotnet-framework-docker-samples/blob/master/dotnetapp-4.7/Dockerfile).</span><span class="sxs-lookup"><span data-stu-id="b2272-166">It shows you how you can build and deploy the app relying on the [.NET Framework 4.7 docker image](https://github.com/Microsoft/dotnet-framework-docker-samples/blob/master/dotnetapp-4.7/Dockerfile).</span></span>

<span data-ttu-id="b2272-167">**Rozhraní .NET framework 4.6.2**</span><span class="sxs-lookup"><span data-stu-id="b2272-167">**.NET Framework 4.6.2**</span></span>

<span data-ttu-id="b2272-168">[Dotnet-ukázkové rozhraní framework: 4.6.2](https://github.com/Microsoft/dotnet-framework-docker-samples/tree/master/dotnetapp-4.6.2) ukazuje základní "hello world" použití [rozhraní .NET Framework 4.6.2](../../framework/whats-new/index.md#v462).</span><span class="sxs-lookup"><span data-stu-id="b2272-168">The [dotnet-framework:4.6.2 sample](https://github.com/Microsoft/dotnet-framework-docker-samples/tree/master/dotnetapp-4.6.2) demonstrates basic "hello world" usage of the [.NET Framework 4.6.2](../../framework/whats-new/index.md#v462).</span></span> <span data-ttu-id="b2272-169">To se dozvíte, jak můžete sestavení a nasazení aplikace na přijímající [image dockeru rozhraní .NET Framework 4.6.2](https://github.com/Microsoft/dotnet-framework-docker-samples/blob/master/dotnetapp-4.6.2/Dockerfile).</span><span class="sxs-lookup"><span data-stu-id="b2272-169">It shows you how you can build and deploy the app relying on the [.NET Framework 4.6.2 docker image](https://github.com/Microsoft/dotnet-framework-docker-samples/blob/master/dotnetapp-4.6.2/Dockerfile).</span></span>

<span data-ttu-id="b2272-170">**Rozhraní .NET framework 3.5**</span><span class="sxs-lookup"><span data-stu-id="b2272-170">**.NET Framework 3.5**</span></span>

 <span data-ttu-id="b2272-171">[Dotnet-framework: 3.5 ukázka](https://github.com/Microsoft/dotnet-framework-docker-samples/tree/master/dotnetapp-3.5) ukazuje základní "hello world" použití [rozhraní .NET Framework 3.5](https://github.com/Microsoft/dotnet-framework-docker-samples/blob/master/dotnetapp-3.5/dotnetapp-3.5/Dockerfile).</span><span class="sxs-lookup"><span data-stu-id="b2272-171">The [dotnet-framework:3.5 sample](https://github.com/Microsoft/dotnet-framework-docker-samples/tree/master/dotnetapp-3.5) demonstrates basic "hello world" usage of [.NET Framework 3.5](https://github.com/Microsoft/dotnet-framework-docker-samples/blob/master/dotnetapp-3.5/dotnetapp-3.5/Dockerfile).</span></span> <span data-ttu-id="b2272-172">To se dozvíte, jak můžete sestavit a nasadit projekt spoléhat na rozhraní .NET Framework 3.5 v Dockeru.</span><span class="sxs-lookup"><span data-stu-id="b2272-172">It shows you how you can build and deploy a project relying on .NET Framework 3.5 in Docker.</span></span>

#### <a name="aspnet-core"></a><span data-ttu-id="b2272-173">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="b2272-173">ASP.NET Core</span></span>

* <span data-ttu-id="b2272-174">[Tato ukázka ASP.NET Core Docker](https://github.com/dotnet/dotnet-docker-samples/tree/master/aspnetapp) ukazuje vzoru osvědčených postupů pro vytváření imagí Dockeru pro ASP.NET Core aplikace pro produkční prostředí.</span><span class="sxs-lookup"><span data-stu-id="b2272-174">[This ASP.NET Core Docker sample](https://github.com/dotnet/dotnet-docker-samples/tree/master/aspnetapp) demonstrates a best practice pattern for building Docker images for ASP.NET Core apps for production.</span></span> <span data-ttu-id="b2272-175">Ukázka funguje s kontejnery Windows i Linux.</span><span class="sxs-lookup"><span data-stu-id="b2272-175">The sample works with both Linux and Windows containers.</span></span>

* [<span data-ttu-id="b2272-176">ASP.NET Core Image v Dockerhubu</span><span class="sxs-lookup"><span data-stu-id="b2272-176">ASP.NET Core images on DockerHub</span></span>](https://hub.docker.com/r/microsoft/aspnetcore-build/)

* [<span data-ttu-id="b2272-177">Imagí pro ASP.NET Core na Githubu</span><span class="sxs-lookup"><span data-stu-id="b2272-177">ASP.NET Core images on GitHub</span></span>](https://github.com/aspnet/aspnet-docker)

#### <a name="aspnet-framework"></a><span data-ttu-id="b2272-178">Rozhraní ASP.NET</span><span class="sxs-lookup"><span data-stu-id="b2272-178">ASP.NET Framework</span></span>

* [<span data-ttu-id="b2272-179">ASP.NET Framework Image v Dockerhubu</span><span class="sxs-lookup"><span data-stu-id="b2272-179">ASP.NET Framework images on DockerHub</span></span>](https://hub.docker.com/r/microsoft/aspnet/)

* [<span data-ttu-id="b2272-180">Aplikace webových formulářů ASP.NET v ukázce rozhraní .NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="b2272-180">ASP.NET Web Forms app on .NET Framework 4.6.2 sample</span></span>](https://github.com/Microsoft/dotnet-framework-docker-samples/tree/master/aspnetapp)

#### <a name="windows-communication-framework-wcf"></a><span data-ttu-id="b2272-181">Windows Communication Framework (WCF)</span><span class="sxs-lookup"><span data-stu-id="b2272-181">Windows Communication Framework (WCF)</span></span>

* [<span data-ttu-id="b2272-182">Windows Communication Framework (WCF) Image v Dockerhubu</span><span class="sxs-lookup"><span data-stu-id="b2272-182">Windows Communication Framework (WCF) images on DockerHub</span></span>](https://hub.docker.com/r/microsoft/wcf/)

* [<span data-ttu-id="b2272-183">Image Windows Communication Framework (WCF) na Githubu</span><span class="sxs-lookup"><span data-stu-id="b2272-183">Windows Communication Framework (WCF) images on GitHub</span></span>](https://github.com/microsoft/wcf-docker)

* [<span data-ttu-id="b2272-184">Ukázky Windows Communication Framework (WCF) Docker pomocí rozhraní .NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="b2272-184">Windows Communication Framework (WCF) Docker samples using .NET Framework 4.6.2</span></span>](https://github.com/Microsoft/wcf-docker-samples)

#### <a name="internet-information-server-iis"></a><span data-ttu-id="b2272-185">Internet Information Server (IIS)</span><span class="sxs-lookup"><span data-stu-id="b2272-185">Internet Information Server (IIS)</span></span>

* [<span data-ttu-id="b2272-186">Internet Information Server (IIS) Image v Dockerhubu</span><span class="sxs-lookup"><span data-stu-id="b2272-186">Internet Information Server (IIS) images on DockerHub</span></span>](https://hub.docker.com/r/microsoft/iis/)

* [<span data-ttu-id="b2272-187">Obrázky Internet Information Server (IIS) na Githubu</span><span class="sxs-lookup"><span data-stu-id="b2272-187">Internet Information Server (IIS) images on GitHub</span></span>](https://github.com/microsoft/iis-docker)

### <a name="interact-with-other-microsoft-stack-container-images"></a><span data-ttu-id="b2272-188">Pracovat s další Image kontejneru Microsoft zásobníku</span><span class="sxs-lookup"><span data-stu-id="b2272-188">Interact with other Microsoft stack container images</span></span>

#### <a name="microsoft-sql-server"></a><span data-ttu-id="b2272-189">Microsoft SQL Server</span><span class="sxs-lookup"><span data-stu-id="b2272-189">Microsoft SQL Server</span></span>

* [<span data-ttu-id="b2272-190">Spusťte Microsoft SQL Server pro Linux 2017 image kontejneru s Docker rychlý start</span><span class="sxs-lookup"><span data-stu-id="b2272-190">Run the Microsoft SQL Server for Linux 2017 container image with Docker Quickstart</span></span>](https://docs.microsoft.com/sql/linux/quickstart-install-connect-docker)

* [<span data-ttu-id="b2272-191">Microsoft SQL Server pro Linuxové Image v Dockerhubu</span><span class="sxs-lookup"><span data-stu-id="b2272-191">Microsoft SQL Server for Linux images on DockerHub</span></span>](https://hub.docker.com/r/microsoft/mssql-server-linux/)

* [<span data-ttu-id="b2272-192">Image Microsoft SQL Server Express Edition pro kontejnery Windows na Dockerhubu</span><span class="sxs-lookup"><span data-stu-id="b2272-192">Microsoft SQL Server Express Edition images for Windows Containers on DockerHub</span></span>](https://hub.docker.com/r/microsoft/mssql-server-windows-express/)

* [<span data-ttu-id="b2272-193">Image Microsoft SQL Server Developer Edition pro kontejnery Windows na Dockerhubu</span><span class="sxs-lookup"><span data-stu-id="b2272-193">Microsoft SQL Server Developer Edition images for Windows Containers on DockerHub</span></span>](https://hub.docker.com/r/microsoft/mssql-server-windows-developer/)

#### <a name="azure-devops-services-agent"></a><span data-ttu-id="b2272-194">Agent Azure DevOps služby</span><span class="sxs-lookup"><span data-stu-id="b2272-194">Azure DevOps Services agent</span></span>

* [<span data-ttu-id="b2272-195">Azure DevOps služby agenta Image v Dockerhubu</span><span class="sxs-lookup"><span data-stu-id="b2272-195">Azure DevOps Services agent images on DockerHub</span></span>](https://hub.docker.com/r/microsoft/vsts-agent/)

* [<span data-ttu-id="b2272-196">Azure DevOps služby agenta imagí na Githubu</span><span class="sxs-lookup"><span data-stu-id="b2272-196">Azure DevOps Services agent images on GitHub</span></span>](https://github.com/Microsoft/vsts-agent-docker)

#### <a name="operations-management-suite-oms-linux-agent"></a><span data-ttu-id="b2272-197">Operations Management Suite (OMS) linuxového agenta</span><span class="sxs-lookup"><span data-stu-id="b2272-197">Operations Management Suite (OMS) Linux agent</span></span>

* [<span data-ttu-id="b2272-198">Přehled Operations Management Suite (OMS) Linux agent</span><span class="sxs-lookup"><span data-stu-id="b2272-198">Operations Management Suite (OMS) Linux agent overview</span></span>](https://github.com/Microsoft/OMS-Agent-for-Linux/blob/master/docs/Docker-Instructions.md)

* [<span data-ttu-id="b2272-199">Operations Management Suite (OMS) Image v Dockerhubu</span><span class="sxs-lookup"><span data-stu-id="b2272-199">Operations Management Suite (OMS) images on DockerHub</span></span>](https://hub.docker.com/r/microsoft/oms/)

* [<span data-ttu-id="b2272-200">Operations Management Suite (OMS) Image na Githubu</span><span class="sxs-lookup"><span data-stu-id="b2272-200">Operations Management Suite (OMS) images on GitHub</span></span>](https://github.com/Microsoft/OMS-docker)

#### <a name="microsoft-azure-command-line-interface-cli"></a><span data-ttu-id="b2272-201">Rozhraní příkazového řádku Microsoft Azure (CLI)</span><span class="sxs-lookup"><span data-stu-id="b2272-201">Microsoft Azure Command Line Interface (CLI)</span></span>

* [<span data-ttu-id="b2272-202">Microsoft Azure rozhraní příkazového řádku (CLI) Image v Dockerhubu</span><span class="sxs-lookup"><span data-stu-id="b2272-202">Microsoft Azure Command Line Interface (CLI) images on DockerHub</span></span>](https://hub.docker.com/r/microsoft/azure-cli/) 

* [<span data-ttu-id="b2272-203">Image Microsoft rozhraní příkazového řádku (CLI) Azure na Githubu</span><span class="sxs-lookup"><span data-stu-id="b2272-203">Microsoft Azure Command-Line Interface (CLI) images on GitHub</span></span>](https://github.com/Azure/azure-cli#Docker)

> [!NOTE]
> <span data-ttu-id="b2272-204">Pokud nemáte předplatné Azure, [zaregistrujte se ještě dnes](https://azure.microsoft.com/free/?b=16.48) pro bezplatný účet 30 dní a získat 200 USD v kreditech Azure pro vyzkoušení jakékoli kombinace služeb Azure.</span><span class="sxs-lookup"><span data-stu-id="b2272-204">If you do not have an Azure subscription, [sign up today](https://azure.microsoft.com/free/?b=16.48) for a free 30-day account and get $200 in Azure Credits to try out any combination of Azure services.</span></span>

#### <a name="microsoft-azure-cosmos-db-emulator-windows-containers-only"></a><span data-ttu-id="b2272-205">Emulátor služby Microsoft Azure Cosmos DB (pouze kontejnery Windows)</span><span class="sxs-lookup"><span data-stu-id="b2272-205">Microsoft Azure Cosmos DB Emulator (Windows Containers only)</span></span>

* [<span data-ttu-id="b2272-206">Emulátor služby Microsoft Azure Cosmos DB Image v Dockerhubu</span><span class="sxs-lookup"><span data-stu-id="b2272-206">Microsoft Azure Cosmos DB Emulator images on DockerHub</span></span>](https://hub.docker.com/r/microsoft/azure-cosmosdb-emulator) 

* [<span data-ttu-id="b2272-207">Pro místní vývoj a testování používat emulátor služby Azure Cosmos DB</span><span class="sxs-lookup"><span data-stu-id="b2272-207">Use the Azure Cosmos DB Emulator for local development and testing</span></span>](/azure/cosmos-db/local-emulator#developing-with-the-emulator)

## <a name="exploring-the-rich-docker-development-ecosystem"></a><span data-ttu-id="b2272-208">Zkoumání pestrého ekosystému Dockeru vývoj</span><span class="sxs-lookup"><span data-stu-id="b2272-208">Exploring the rich Docker development ecosystem</span></span>

<span data-ttu-id="b2272-209">Teď, když jste se dozvěděli o platforma Docker a různé imagí Dockeru, dalším krokem je prozkoumat pestrého ekosystému Dockeru.</span><span class="sxs-lookup"><span data-stu-id="b2272-209">Now that you have learned about the Docker platform and different Docker images, the next step is to explore the rich Docker ecosystem.</span></span> <span data-ttu-id="b2272-210">Jak nástroje Microsoftu doplňují vývojových zobrazí následující odkazy.</span><span class="sxs-lookup"><span data-stu-id="b2272-210">The following links show you how the Microsoft tools complement container development.</span></span>

* [<span data-ttu-id="b2272-211">Společně pomocí .NET a Dockeru</span><span class="sxs-lookup"><span data-stu-id="b2272-211">Using .NET and Docker together</span></span>](https://blogs.msdn.microsoft.com/dotnet/2017/05/25/using-net-and-docker-together/)
* [<span data-ttu-id="b2272-212">Návrh a vývoj aplikací .NET více kontejnerů a založených na Mikroslužbách</span><span class="sxs-lookup"><span data-stu-id="b2272-212">Designing and Developing Multi-Container and Microservice-Based .NET Applications</span></span>](../../standard/microservices-architecture/multi-container-microservice-net-applications/index.md)
* [<span data-ttu-id="b2272-213">Rozšíření sady Visual Studio Code Dockeru</span><span class="sxs-lookup"><span data-stu-id="b2272-213">Visual Studio Code Docker extension</span></span>](https://code.visualstudio.com/docs/languages/dockerfile)
* [<span data-ttu-id="b2272-214">Zjistěte, jak používat Azure Service Fabric</span><span class="sxs-lookup"><span data-stu-id="b2272-214">Learn how to use Azure Service Fabric</span></span>](/azure/service-fabric/index)
* [<span data-ttu-id="b2272-215">Service Fabric získávání ukázka Začínáme</span><span class="sxs-lookup"><span data-stu-id="b2272-215">Service Fabric Getting Started Sample</span></span>](https://azure.microsoft.com/resources/samples/service-fabric-dotnet-getting-started/)
* [<span data-ttu-id="b2272-216">Výhody kontejnerů Windows</span><span class="sxs-lookup"><span data-stu-id="b2272-216">Benefits of Windows Containers</span></span>](/virtualization/windowscontainers/about/index#video-overview)
* [<span data-ttu-id="b2272-217">Práce s nástroji Dockeru pro Visual Studio</span><span class="sxs-lookup"><span data-stu-id="b2272-217">Working with Visual Studio Docker Tools</span></span>](/aspnet/core/host-and-deploy/docker/visual-studio-tools-for-docker)
* [<span data-ttu-id="b2272-218">Nasazování Imagí Dockeru ze služby Azure Container Registry do služby Azure Container Instances</span><span class="sxs-lookup"><span data-stu-id="b2272-218">Deploying Docker Images from the Azure Container Registry to Azure Container Instances</span></span>](https://blogs.msdn.microsoft.com/stevelasker/2017/07/28/deploying-docker-images-from-the-azure-container-registry-to-azure-container-instances/)
* [<span data-ttu-id="b2272-219">Ladění ve Visual Studiu Code</span><span class="sxs-lookup"><span data-stu-id="b2272-219">Debugging with Visual Studio Code</span></span>](https://code.visualstudio.com/docs/nodejs/debugging-recipes#_nodejs-typescript-docker-container)
* [<span data-ttu-id="b2272-220">Praktické ukázky sady Visual Studio pro Mac, kontejnery a kód bez serveru v cloudu</span><span class="sxs-lookup"><span data-stu-id="b2272-220">Getting hands on with Visual Studio for Mac, containers, and serverless code in the cloud</span></span>](https://blogs.msdn.microsoft.com/visualstudio/2017/08/31/hands-on-with-visual-studio-for-mac-containers-serverless-code-in-the-cloud/#comments)
* [<span data-ttu-id="b2272-221">Začínáme s Dockerem a sady Visual Studio pro Mac testovacího prostředí</span><span class="sxs-lookup"><span data-stu-id="b2272-221">Getting Started with Docker and Visual Studio for Mac Lab</span></span>](https://github.com/Microsoft/vs4mac-labs/tree/master/Docker/Getting-Started)

## <a name="next-steps"></a><span data-ttu-id="b2272-222">Další kroky</span><span class="sxs-lookup"><span data-stu-id="b2272-222">Next steps</span></span>

* [<span data-ttu-id="b2272-223">Základy Dockeru s .NET Core</span><span class="sxs-lookup"><span data-stu-id="b2272-223">Learn Docker Basics with .NET Core</span></span>](docker-basics-dotnet-core.md)
* [<span data-ttu-id="b2272-224">Vytváření Imagí Dockeru .NET Core</span><span class="sxs-lookup"><span data-stu-id="b2272-224">Building .NET Core Docker Images</span></span>](building-net-docker-images.md)
