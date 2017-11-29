---
title: "Úvod do rozhraní .NET a Docker"
description: Principy Docker a .NET Core
keywords: "Rozhraní .NET, rozhraní .NET core, Docker"
author: jralexander
ms.author: johalex
ms.date: 11/06/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-docker
ms.devlang: dotnet
ms.assetid: 03c28597-7e73-46d6-a9c3-f9cb55642739
manager: wpickett
ms.custom: mvc
ms.openlocfilehash: 1c9ce7a008c86d1c245ce8b7d616e05fcb3d4bbc
ms.sourcegitcommit: a53799f81351ad9afb3007cd68846ce6aeeb10cb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/15/2017
---
# <a name="introduction-to-net-and-docker"></a><span data-ttu-id="2c5bc-104">Úvod do rozhraní .NET a Docker</span><span class="sxs-lookup"><span data-stu-id="2c5bc-104">Introduction to .NET and Docker</span></span>

 <span data-ttu-id="2c5bc-105">Tento článek poskytuje úvod a koncepční základní informace o práci s .NET v nástroji Docker.</span><span class="sxs-lookup"><span data-stu-id="2c5bc-105">This article provides an introduction and conceptual background to working with .NET on Docker.</span></span> 

## <a name="docker-packaging-your-apps-to-deploy-and-run-anywhere"></a><span data-ttu-id="2c5bc-106">Docker: Zabalení aplikace nasadit a spustit odkudkoli</span><span class="sxs-lookup"><span data-stu-id="2c5bc-106">Docker: Packaging your apps to deploy and run anywhere</span></span>

<span data-ttu-id="2c5bc-107">[Docker](https://docs.microsoft.com/dotnet/standard/microservices-architecture/container-docker-introduction/docker-defined) je otevřená platforma, která umožňuje vývojáři a správci sestavení [bitové kopie](https://docs.docker.com/glossary/?term=image), odeslání a spustit distribuované aplikace v prostředí volně izolované názvem [kontejneru](https://www.docker.com/what-container).</span><span class="sxs-lookup"><span data-stu-id="2c5bc-107">[Docker](https://docs.microsoft.com/dotnet/standard/microservices-architecture/container-docker-introduction/docker-defined) is an open platform that enables developers and administrators to build [images](https://docs.docker.com/glossary/?term=image), ship, and run distributed applications in a loosely isolated environment called a [container](https://www.docker.com/what-container).</span></span> <span data-ttu-id="2c5bc-108">Tento přístup umožňuje správu životního cyklu aplikací efektivní mezi vývoj, QA a provozní prostředí.</span><span class="sxs-lookup"><span data-stu-id="2c5bc-108">This approach enables efficient application lifecycle management between development, QA, and production environments.</span></span>
 
<span data-ttu-id="2c5bc-109">[Docker platformy](https://docs.docker.com/engine/docker-overview/#the-docker-platform) používá [modulu Docker](https://docs.docker.com/engine/docker-overview/#docker-engine) rychle vytvářet a balíček aplikace jako [imagí Dockeru](https://docs.docker.com/glossary/?term=image) vytvořený soubory, které jsou napsané v [soubor Docker ](https://docs.docker.com/glossary/?term=Dockerfile) formátu, který pak je nasadit a spustit [vrstvený kontejneru](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/#container-and-layers).</span><span class="sxs-lookup"><span data-stu-id="2c5bc-109">The [Docker platform](https://docs.docker.com/engine/docker-overview/#the-docker-platform) uses the [Docker Engine](https://docs.docker.com/engine/docker-overview/#docker-engine) to quickly build and package apps as [Docker images](https://docs.docker.com/glossary/?term=image) created using files written in the [Dockerfile](https://docs.docker.com/glossary/?term=Dockerfile) format that then is deployed and run in a [layered container](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/#container-and-layers).</span></span>

<span data-ttu-id="2c5bc-110">Můžete buď vytvořit vlastní [na základě bitové kopie](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/#images-and-layers) jako dockerfiles nebo použijte existující z [registru](https://docs.docker.com/glossary/?term=registry), například [úložiště Docker Hub](https://docs.docker.com/glossary/?term=Docker%20Hub).</span><span class="sxs-lookup"><span data-stu-id="2c5bc-110">You can either create your own [layered images](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/#images-and-layers) as dockerfiles or use existing ones from a [registry](https://docs.docker.com/glossary/?term=registry), like [Docker Hub](https://docs.docker.com/glossary/?term=Docker%20Hub).</span></span>

<span data-ttu-id="2c5bc-111">[Vztah mezi Docker kontejnery, Image a registrech](https://docs.microsoft.com/dotnet/standard/microservices-architecture/container-docker-introduction/docker-containers-images-registries) je důležité koncept při [architektury a sestavování kontejnerové aplikace nebo mikroslužeb](https://docs.microsoft.com/dotnet/standard/microservices-architecture/architect-microservice-container-applications/).</span><span class="sxs-lookup"><span data-stu-id="2c5bc-111">The [relationship between Docker containers, images, and registries](https://docs.microsoft.com/dotnet/standard/microservices-architecture/container-docker-introduction/docker-containers-images-registries) is an important concept when [architecting and building containerized applications or microservices](https://docs.microsoft.com/dotnet/standard/microservices-architecture/architect-microservice-container-applications/).</span></span> <span data-ttu-id="2c5bc-112">Tento přístup výrazně zkracuje doba mezi vývoj a nasazení.</span><span class="sxs-lookup"><span data-stu-id="2c5bc-112">This approach greatly shortens the time between development and deployment.</span></span>

### <a name="further-reading-and-watching"></a><span data-ttu-id="2c5bc-113">Další čtení (a sledování)</span><span class="sxs-lookup"><span data-stu-id="2c5bc-113">Further reading (and watching)</span></span>

* [<span data-ttu-id="2c5bc-114">Kontejnery založené na systému Windows: vývoj moderních aplikací pomocí řízení podnikové úrovni.</span><span class="sxs-lookup"><span data-stu-id="2c5bc-114">Windows-based containers: Modern app development with enterprise-grade control.</span></span>](https://www.youtube.com/watch?v=Ryx3o0rD5lY&feature=youtu.be)
* [<span data-ttu-id="2c5bc-115">Přehled docker</span><span class="sxs-lookup"><span data-stu-id="2c5bc-115">Docker overview</span></span>](https://docs.docker.com/engine/docker-overview/)
* [<span data-ttu-id="2c5bc-116">Soubor Docker kontejnerům Windows</span><span class="sxs-lookup"><span data-stu-id="2c5bc-116">Dockerfile on Windows Containers</span></span>](https://docs.microsoft.com/virtualization/windowscontainers/manage-docker/manage-windows-dockerfile)
* [<span data-ttu-id="2c5bc-117">Osvědčené postupy pro psaní Dockerfiles</span><span class="sxs-lookup"><span data-stu-id="2c5bc-117">Best practices for writing Dockerfiles</span></span>](https://docs.docker.com/engine/userguide/eng-image/dockerfile_best-practices/)
* [<span data-ttu-id="2c5bc-118">Vytváření Imagí Dockeru pro aplikace .NET Core</span><span class="sxs-lookup"><span data-stu-id="2c5bc-118">Building Docker Images for .NET Core applications</span></span>](../docker/building-net-docker-images.md)


### <a name="getting-net-docker-images"></a><span data-ttu-id="2c5bc-119">Získávání Imagí Dockeru rozhraní .NET</span><span class="sxs-lookup"><span data-stu-id="2c5bc-119">Getting .NET Docker Images</span></span>

<span data-ttu-id="2c5bc-120">Oficiální Docker .NET bitové kopie se vytváří a optimalizované společností Microsoft.</span><span class="sxs-lookup"><span data-stu-id="2c5bc-120">The Official .NET Docker images are created and optimized by Microsoft.</span></span> <span data-ttu-id="2c5bc-121">Jsou veřejně dostupné v Microsoft úložiště na úložiště Docker Hub.</span><span class="sxs-lookup"><span data-stu-id="2c5bc-121">They are publicly available in the Microsoft repositories on Docker Hub.</span></span> <span data-ttu-id="2c5bc-122">Každý úložiště může obsahovat více bitových kopií, v závislosti na rozhraní .NET verze a na verze operačního systému.</span><span class="sxs-lookup"><span data-stu-id="2c5bc-122">Each repository can contain multiple images, depending on .NET versions, and on OS versions.</span></span> <span data-ttu-id="2c5bc-123">Většina úložiště image poskytují rozsáhlé označení vám pomohou vybrat konkrétní framework verze a operační systém (verze Windows nebo Linux distro).</span><span class="sxs-lookup"><span data-stu-id="2c5bc-123">Most image repos provide extensive tagging to help you select both a specific framework version and an OS (Linux distro or Windows version).</span></span>

## <a name="scenario-based-guidance"></a><span data-ttu-id="2c5bc-124">Scénář na základě pokyny</span><span class="sxs-lookup"><span data-stu-id="2c5bc-124">Scenario Based Guidance</span></span>

<span data-ttu-id="2c5bc-125">Záměr společnosti Microsoft pro rozhraní .NET úložiště je získat podrobné a zaměřují se úložiště, které představují konkrétní scénář nebo zatížení.</span><span class="sxs-lookup"><span data-stu-id="2c5bc-125">Microsoft’s intent for .NET repositories is to have granular and focused repos, which represent a specific scenario or workload.</span></span>

<span data-ttu-id="2c5bc-126">`microsoft/aspnetcore` Bitové kopie jsou optimalizované pro aplikace ASP.NET Core na Docker, takže kontejnery můžete spustit rychlejší.</span><span class="sxs-lookup"><span data-stu-id="2c5bc-126">The `microsoft/aspnetcore` images are optimized for ASP.NET Core apps on Docker, so containers can start faster.</span></span>

<span data-ttu-id="2c5bc-127">Obrázky .NET Core (`microsoft/dotnet`) jsou určené pro konzolu aplikace založené na .NET Core.</span><span class="sxs-lookup"><span data-stu-id="2c5bc-127">The .NET Core images (`microsoft/dotnet`) are intended for console apps based on .NET Core.</span></span> <span data-ttu-id="2c5bc-128">Například procesy batch, Azure WebJobs a scénáře konzoly by měl používat optimalizované Image .NET Core.</span><span class="sxs-lookup"><span data-stu-id="2c5bc-128">For example, batch processes, Azure WebJobs, and other console scenarios should use optimized .NET Core images.</span></span>

<span data-ttu-id="2c5bc-129">Nejobvyklejší vodorovné scénář pro použití aplikací Docker a .NET je pro produkční nasazení a hostování.</span><span class="sxs-lookup"><span data-stu-id="2c5bc-129">The most obvious horizontal scenario for using Docker and .NET applications is for production deployment and hosting.</span></span> <span data-ttu-id="2c5bc-130">Ukazuje se, že produkční je jenom jedním scénářem, a další ty, které jsou rovnoměrně užitečné.</span><span class="sxs-lookup"><span data-stu-id="2c5bc-130">It turns out that production is just one scenario and the other ones are equally useful.</span></span> <span data-ttu-id="2c5bc-131">Tyto scénáře nejsou specifické pro rozhraní .NET, ale měli použít pro většině platforem developer.</span><span class="sxs-lookup"><span data-stu-id="2c5bc-131">These scenarios are not specific to .NET, but should apply to most developer platforms.</span></span>

* <span data-ttu-id="2c5bc-132">**Nainstalujte nízkým třením** – .NET můžete vyzkoušet bez místní instalace.</span><span class="sxs-lookup"><span data-stu-id="2c5bc-132">**Low friction install** — You can try out .NET without a local install.</span></span> <span data-ttu-id="2c5bc-133">Stáhněte pouze bitovou kopii Docker s .NET v ní.</span><span class="sxs-lookup"><span data-stu-id="2c5bc-133">Just download a Docker image with .NET in it.</span></span>

* <span data-ttu-id="2c5bc-134">**Vývoj v kontejneru** – můžete vyvíjet v prostředí konzistentní provedení vývoj a produkční prostředí podobné (zabraňující problémy jako globální stav na počítačích vývojářů).</span><span class="sxs-lookup"><span data-stu-id="2c5bc-134">**Develop in a container** — You can develop in a consistent environment, making development and production environments similar (avoiding issues like global state on developer machines).</span></span> <span data-ttu-id="2c5bc-135">Nástroje sady Visual Studio pro Docker i umožňují spusťte kontejner přímo ze sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="2c5bc-135">Visual Studio Tools for Docker even enable you to start a container directly from Visual Studio.</span></span>

* <span data-ttu-id="2c5bc-136">**Testování v kontejneru** – můžete otestovat v kontejneru, snižuje chyby způsobené nesprávnou konfigurací prostředí nebo jiné změny zanechat z poslední test.</span><span class="sxs-lookup"><span data-stu-id="2c5bc-136">**Test in a container** — You can test in a container, reducing failures due to incorrectly configured environments or other changes left behind from the last test.</span></span>

* <span data-ttu-id="2c5bc-137">**Sestavení v kontejneru** – můžete vytvořit kód v kontejneru, takže není nutné správně nakonfigurovat počítačů sdílené sestavení pro prostředí s více, ale místo toho přesunout do "BYOC" (přineste si vlastní kontejner) přístup.</span><span class="sxs-lookup"><span data-stu-id="2c5bc-137">**Build in a container** — You can build code in a container, avoiding the need to correctly configure shared build machines for multiple environments but instead move to a “BYOC” (bring your own container) approach.</span></span>

* <span data-ttu-id="2c5bc-138">**Nasazení ve všech prostředích** – můžete nasadit bitovou prochází všechna prostředí.</span><span class="sxs-lookup"><span data-stu-id="2c5bc-138">**Deployment in all environments** — You can deploy an image through all of your environments.</span></span> <span data-ttu-id="2c5bc-139">Tento přístup snižuje chyby způsobené konfigurace rozdílů, obvykle změny chování bitovou kopii prostřednictvím externí konfigurace (například vloženého prostředí proměnné).</span><span class="sxs-lookup"><span data-stu-id="2c5bc-139">This approach reduces failures due to configuration differences, typically changing the image behavior via external configuration (for example, injected environment variables).</span></span>

<span data-ttu-id="2c5bc-140">[Obecné pokyny](https://docs.microsoft.com/dotnet/standard/microservices-architecture/net-core-net-framework-containers/general-guidance) rozhodování mezi .NET Core a rozhraní .NET Framework pro vývoj kontejner Docker.</span><span class="sxs-lookup"><span data-stu-id="2c5bc-140">[General guidance](https://docs.microsoft.com/dotnet/standard/microservices-architecture/net-core-net-framework-containers/general-guidance) for deciding between .NET Core and .NET Framework for Docker container development.</span></span>

### <a name="common-docker-development-scenarios"></a><span data-ttu-id="2c5bc-141">Běžné scénáře vývoj Docker</span><span class="sxs-lookup"><span data-stu-id="2c5bc-141">Common Docker development scenarios</span></span>

#### <a name="net-core"></a><span data-ttu-id="2c5bc-142">.NET Core</span><span class="sxs-lookup"><span data-stu-id="2c5bc-142">.NET Core</span></span>

<span data-ttu-id="2c5bc-143">**.NET core prostředky**</span><span class="sxs-lookup"><span data-stu-id="2c5bc-143">**.NET Core resources**</span></span>

 <span data-ttu-id="2c5bc-144">Vyberte ukázky .NET Core splňující vaše scénáře, které vás zajímají.</span><span class="sxs-lookup"><span data-stu-id="2c5bc-144">Pick the .NET Core samples that fit your scenarios of interest.</span></span> <span data-ttu-id="2c5bc-145">Všechny ukázkové pokyny popisují, jak cílových bitových kopií systému Windows nebo Linux Docker ze systému Windows, Linux nebo systému macOS hostitelů.</span><span class="sxs-lookup"><span data-stu-id="2c5bc-145">All sample instructions describe how to target Windows or Linux Docker images from Windows, Linux, or macOS hosts.</span></span>

<span data-ttu-id="2c5bc-146">Ukázky použití .NET Core 2.0.</span><span class="sxs-lookup"><span data-stu-id="2c5bc-146">The samples use .NET Core 2.0.</span></span> <span data-ttu-id="2c5bc-147">Používají Docker [více fáze sestavení](https://github.com/dotnet/announcements/issues/18) a [více architektury značky](https://github.com/dotnet/announcements/issues/14) podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="2c5bc-147">They use Docker [multi-stage build](https://github.com/dotnet/announcements/issues/18) and [multi-arch tags](https://github.com/dotnet/announcements/issues/14) where appropriate.</span></span>

* [<span data-ttu-id="2c5bc-148">.NET core Image na DockerHub</span><span class="sxs-lookup"><span data-stu-id="2c5bc-148">.NET Core images on DockerHub</span></span>](https://hub.docker.com/r/microsoft/dotnet/)

* [<span data-ttu-id="2c5bc-149">Dockerize aplikace .NET Core</span><span class="sxs-lookup"><span data-stu-id="2c5bc-149">Dockerize a .NET Core application</span></span>](https://docs.docker.com/engine/examples/dotnetcore/)

* <span data-ttu-id="2c5bc-150">Tento příklad .NET Core Docker znázorňuje postup [pomocí Docker ve vývojových procesech .NET Core](https://github.com/dotnet/dotnet-docker-samples/tree/master/dotnetapp-dev).</span><span class="sxs-lookup"><span data-stu-id="2c5bc-150">This .NET Core Docker sample demonstrates how to [use Docker in your .NET Core development process](https://github.com/dotnet/dotnet-docker-samples/tree/master/dotnetapp-dev).</span></span> <span data-ttu-id="2c5bc-151">Ukázka funguje s kontejnery Linux a Windows.</span><span class="sxs-lookup"><span data-stu-id="2c5bc-151">The sample works with both Linux and Windows containers.</span></span>

* <span data-ttu-id="2c5bc-152">Tento příklad .NET Core Docker znázorňuje osvědčených postupů vzor [vytváření imagí Dockeru pro aplikace .NET Core pro produkční prostředí.](https://github.com/dotnet/dotnet-docker-samples/tree/master/dotnetapp-prod)</span><span class="sxs-lookup"><span data-stu-id="2c5bc-152">This .NET Core Docker sample demonstrates a best practice pattern for [building Docker images for .NET Core apps for production.](https://github.com/dotnet/dotnet-docker-samples/tree/master/dotnetapp-prod)</span></span> <span data-ttu-id="2c5bc-153">Ukázka funguje s kontejnery Linux a Windows.</span><span class="sxs-lookup"><span data-stu-id="2c5bc-153">The sample works with both Linux and Windows containers.</span></span>

* <span data-ttu-id="2c5bc-154">To [ukázka .NET Core Docker](https://github.com/dotnet/dotnet-docker-samples/tree/master/dotnetapp-selfcontained) ukazuje osvědčených postupů vzor pro vytváření imagí Dockeru pro [nezávislý aplikace .NET Core](https://docs.microsoft.com/dotnet/core/deploying/).</span><span class="sxs-lookup"><span data-stu-id="2c5bc-154">This [.NET Core Docker sample](https://github.com/dotnet/dotnet-docker-samples/tree/master/dotnetapp-selfcontained) demonstrates a best practice pattern for building Docker images for [self-contained .NET Core applications](https://docs.microsoft.com/dotnet/core/deploying/).</span></span> <span data-ttu-id="2c5bc-155">Použít pro kontejner nejmenší provozní bez výhody z [sdílení základní Image mezi kontejnery](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/).</span><span class="sxs-lookup"><span data-stu-id="2c5bc-155">Used for the smallest production container without a benefit from [sharing base images between containers](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/).</span></span> <span data-ttu-id="2c5bc-156">Nižších vrstvách Docker však může sdílet.</span><span class="sxs-lookup"><span data-stu-id="2c5bc-156">However, lower Docker layers could be shared.</span></span>

#### <a name="arm32--raspberry-pi"></a><span data-ttu-id="2c5bc-157">ARM32 / malin pí</span><span class="sxs-lookup"><span data-stu-id="2c5bc-157">ARM32 / Raspberry Pi</span></span>

* [<span data-ttu-id="2c5bc-158">.NET core Runtime ARM32 sestavení oznámení</span><span class="sxs-lookup"><span data-stu-id="2c5bc-158">.NET Core Runtime ARM32 builds announcement</span></span>](https://github.com/dotnet/announcements/issues/29)

* [<span data-ttu-id="2c5bc-159">ARM32 / malin platformy .NET Core bitové kopie na DockerHub</span><span class="sxs-lookup"><span data-stu-id="2c5bc-159">ARM32 / Raspberry Pi .NET Core images on DockerHub</span></span>](https://hub.docker.com/r/microsoft/dotnet/)

* [<span data-ttu-id="2c5bc-160">ARM32 / Malinová platformy .NET Core Docker ukázky na Githubu</span><span class="sxs-lookup"><span data-stu-id="2c5bc-160">ARM32 / Raspberry Pi .NET Core Docker Samples on GitHub</span></span>](https://github.com/dotnet/dotnet-docker-samples#arm32--raspberry-pi)

#### <a name="net-framework"></a><span data-ttu-id="2c5bc-161">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="2c5bc-161">.NET Framework</span></span>

* <span data-ttu-id="2c5bc-162">[Rozhraní .NET framework Image na DockerHub](https://hub.docker.com/r/microsoft/dotnet-framework/) tohoto úložiště obsahovat ukázky, která ukazují různých konfiguracích Docker rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="2c5bc-162">[.NET Framework images on DockerHub](https://hub.docker.com/r/microsoft/dotnet-framework/) This repo contain samples that demonstrate various .NET Framework Docker configurations.</span></span> <span data-ttu-id="2c5bc-163">Tyto Image můžete použít jako základ imagí Dockeru.</span><span class="sxs-lookup"><span data-stu-id="2c5bc-163">You can use these images as the basis of your own Docker images.</span></span>

<span data-ttu-id="2c5bc-164">**Rozhraní .NET framework 4.7**</span><span class="sxs-lookup"><span data-stu-id="2c5bc-164">**.NET Framework 4.7**</span></span>

<span data-ttu-id="2c5bc-165">[ [Dotnet – ukázka framework: 4.7](https://github.com/Microsoft/dotnet-framework-docker-samples/tree/master/dotnetapp-4.7) ukazuje základní "text hello world" použití [4.7 rozhraní .NET Framework](https://docs.microsoft.com/dotnet/framework/whats-new/index#introducing-the-net-framework-47).</span><span class="sxs-lookup"><span data-stu-id="2c5bc-165">[The [dotnet-framework:4.7 sample](https://github.com/Microsoft/dotnet-framework-docker-samples/tree/master/dotnetapp-4.7) demonstrates basic "hello world" usage of the [.NET Framework 4.7](https://docs.microsoft.com/dotnet/framework/whats-new/index#introducing-the-net-framework-47).</span></span> <span data-ttu-id="2c5bc-166">Ho se dozvíte, jak můžete sestavit a nasazení aplikace spoléhat na [rozhraní .NET Framework 4.7 docker image](https://github.com/Microsoft/dotnet-framework-docker/blob/master/4.7/Dockerfile).</span><span class="sxs-lookup"><span data-stu-id="2c5bc-166">It shows you how you can build and deploy the app relying on the [.NET Framework 4.7 docker image](https://github.com/Microsoft/dotnet-framework-docker/blob/master/4.7/Dockerfile).</span></span>

<span data-ttu-id="2c5bc-167">**Rozhraní .NET framework 4.6.2**</span><span class="sxs-lookup"><span data-stu-id="2c5bc-167">**.NET Framework 4.6.2**</span></span>

<span data-ttu-id="2c5bc-168">[Dotnet – ukázka framework: 4.6.2](https://github.com/Microsoft/dotnet-framework-docker-samples/tree/master/dotnetapp-4.6.2) ukazuje základní "text hello world" použití [rozhraní .NET Framework 4.6.2](https://docs.microsoft.com/dotnet/framework/whats-new/index#whats-new-in-the-net-framework-462).</span><span class="sxs-lookup"><span data-stu-id="2c5bc-168">The [dotnet-framework:4.6.2 sample](https://github.com/Microsoft/dotnet-framework-docker-samples/tree/master/dotnetapp-4.6.2) demonstrates basic "hello world" usage of the [.NET Framework 4.6.2](https://docs.microsoft.com/dotnet/framework/whats-new/index#whats-new-in-the-net-framework-462).</span></span> <span data-ttu-id="2c5bc-169">Ho se dozvíte, jak můžete sestavit a nasazení aplikace spoléhat na [rozhraní .NET Framework 4.6.2 docker image](https://github.com/Microsoft/dotnet-framework-docker/tree/master/4.6.2).</span><span class="sxs-lookup"><span data-stu-id="2c5bc-169">It shows you how you can build and deploy the app relying on the [.NET Framework 4.6.2 docker image](https://github.com/Microsoft/dotnet-framework-docker/tree/master/4.6.2).</span></span>

<span data-ttu-id="2c5bc-170">**Rozhraní .NET framework 3.5**</span><span class="sxs-lookup"><span data-stu-id="2c5bc-170">**.NET Framework 3.5**</span></span>

 <span data-ttu-id="2c5bc-171">[Dotnet – ukázka framework: 3.5](https://github.com/Microsoft/dotnet-framework-docker-samples/tree/master/dotnetapp-3.5) ukazuje základní "text hello world" použití [rozhraní .NET Framework 3.5](https://github.com/Microsoft/dotnet-framework-docker/tree/master/3.5).</span><span class="sxs-lookup"><span data-stu-id="2c5bc-171">The [dotnet-framework:3.5 sample](https://github.com/Microsoft/dotnet-framework-docker-samples/tree/master/dotnetapp-3.5) demonstrates basic "hello world" usage of [.NET Framework 3.5](https://github.com/Microsoft/dotnet-framework-docker/tree/master/3.5).</span></span> <span data-ttu-id="2c5bc-172">Ho ukazuje, jak můžete sestavit a nasazení projektu spoléhat na rozhraní .NET Framework 3.5 v Docker.</span><span class="sxs-lookup"><span data-stu-id="2c5bc-172">It shows you how you can build and deploy a project relying on .NET Framework 3.5 in Docker.</span></span>

#### <a name="aspnet-core"></a><span data-ttu-id="2c5bc-173">Jádro ASP.NET</span><span class="sxs-lookup"><span data-stu-id="2c5bc-173">ASP.NET Core</span></span>

* <span data-ttu-id="2c5bc-174">[Tato ukázka ASP.NET Core Docker](https://github.com/dotnet/dotnet-docker-samples/tree/master/aspnetapp) ukazuje osvědčených postupů vzor pro vytváření imagí Dockeru pro ASP.NET Core aplikace pro produkční prostředí.</span><span class="sxs-lookup"><span data-stu-id="2c5bc-174">[This ASP.NET Core Docker sample](https://github.com/dotnet/dotnet-docker-samples/tree/master/aspnetapp) demonstrates a best practice pattern for building Docker images for ASP.NET Core apps for production.</span></span> <span data-ttu-id="2c5bc-175">Ukázka funguje s kontejnery Linux a Windows.</span><span class="sxs-lookup"><span data-stu-id="2c5bc-175">The sample works with both Linux and Windows containers.</span></span>

* [<span data-ttu-id="2c5bc-176">ASP.NET Core Image na DockerHub</span><span class="sxs-lookup"><span data-stu-id="2c5bc-176">ASP.NET Core images on DockerHub</span></span>](https://hub.docker.com/r/microsoft/aspnetcore-build/)

* [<span data-ttu-id="2c5bc-177">ASP.NET Core bitové kopie na Githubu</span><span class="sxs-lookup"><span data-stu-id="2c5bc-177">ASP.NET Core images on GitHub</span></span>](https://github.com/aspnet/aspnet-docker)

#### <a name="aspnet-framework"></a><span data-ttu-id="2c5bc-178">Rozhraní ASP.NET</span><span class="sxs-lookup"><span data-stu-id="2c5bc-178">ASP.NET Framework</span></span> 

* [<span data-ttu-id="2c5bc-179">Rozhraní ASP.NET Image na DockerHub</span><span class="sxs-lookup"><span data-stu-id="2c5bc-179">ASP.NET Framework images on DockerHub</span></span>](https://hub.docker.com/r/microsoft/aspnet/)

* [<span data-ttu-id="2c5bc-180">Aplikace webových formulářů ASP.NET na rozhraní .NET Framework 4.6.2 vzorku</span><span class="sxs-lookup"><span data-stu-id="2c5bc-180">ASP.NET Web Forms app on .NET Framework 4.6.2 sample</span></span>](https://github.com/Microsoft/dotnet-framework-docker-samples/tree/master/aspnetapp)

#### <a name="windows-communication-framework-wcf"></a><span data-ttu-id="2c5bc-181">Windows Communication Framework (WCF)</span><span class="sxs-lookup"><span data-stu-id="2c5bc-181">Windows Communication Framework (WCF)</span></span>

* [<span data-ttu-id="2c5bc-182">Image Windows Communication Framework (WCF) na DockerHub</span><span class="sxs-lookup"><span data-stu-id="2c5bc-182">Windows Communication Framework (WCF) images on DockerHub</span></span>](https://hub.docker.com/r/microsoft/wcf/)

* [<span data-ttu-id="2c5bc-183">Bitové kopie služby Windows Communication Framework (WCF) na Githubu</span><span class="sxs-lookup"><span data-stu-id="2c5bc-183">Windows Communication Framework (WCF) images on GitHub</span></span>](https://github.com/microsoft/iis-docker)

* [<span data-ttu-id="2c5bc-184">Ukázky Windows Communication Framework (WCF) Docker pomocí rozhraní .NET Full Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="2c5bc-184">Windows Communication Framework (WCF) Docker samples using .NET Full Framework 4.6.2</span></span>](https://github.com/Microsoft/wcf-docker-samples)

#### <a name="internet-information-server-iis"></a><span data-ttu-id="2c5bc-185">Internet Information Server (IIS)</span><span class="sxs-lookup"><span data-stu-id="2c5bc-185">Internet Information Server (IIS)</span></span>

* [<span data-ttu-id="2c5bc-186">Image Internet Information Server (IIS) na DockerHub</span><span class="sxs-lookup"><span data-stu-id="2c5bc-186">Internet Information Server (IIS) images on DockerHub</span></span>](https://hub.docker.com/r/microsoft/iis/)

* [<span data-ttu-id="2c5bc-187">Obrázky Internet Information Server (IIS) na Githubu</span><span class="sxs-lookup"><span data-stu-id="2c5bc-187">Internet Information Server (IIS) images on GitHub</span></span>](https://github.com/microsoft/wcf-docker)

### <a name="interact-with-other-microsoft-stack-container-images"></a><span data-ttu-id="2c5bc-188">Komunikovat s jiných Microsoft zásobníku kontejneru obrázků</span><span class="sxs-lookup"><span data-stu-id="2c5bc-188">Interact with other Microsoft stack container images</span></span>

#### <a name="microsoft-sql-server"></a><span data-ttu-id="2c5bc-189">Microsoft SQL Server</span><span class="sxs-lookup"><span data-stu-id="2c5bc-189">Microsoft SQL Server</span></span>

* [<span data-ttu-id="2c5bc-190">Spusťte Microsoft SQL Server pro Linux 2017 kontejneru image s Docker rychlý start</span><span class="sxs-lookup"><span data-stu-id="2c5bc-190">Run the Microsoft SQL Server for Linux 2017 container image with Docker Quickstart</span></span>](https://docs.microsoft.com/sql/linux/quickstart-install-connect-docker)

* [<span data-ttu-id="2c5bc-191">Microsoft SQL Server pro Linux bitové kopie na DockerHub</span><span class="sxs-lookup"><span data-stu-id="2c5bc-191">Microsoft SQL Server for Linux images on DockerHub</span></span>](https://hub.docker.com/r/microsoft/mssql-server-windows/)

* [<span data-ttu-id="2c5bc-192">Microsoft SQL serveru pro Windows kontejnery Image na DockerHub</span><span class="sxs-lookup"><span data-stu-id="2c5bc-192">Microsoft SQL Server for Windows Containers images on DockerHub</span></span>](https://hub.docker.com/r/microsoft/mssql-server-windows/)

* [<span data-ttu-id="2c5bc-193">Microsoft SQL Server Express Edition bitových kopií pro Windows kontejnerů v DockerHub</span><span class="sxs-lookup"><span data-stu-id="2c5bc-193">Microsoft SQL Server Express Edition images for Windows Containers on DockerHub</span></span>](https://hub.docker.com/r/microsoft/mssql-server-windows-express/)

* [<span data-ttu-id="2c5bc-194">Microsoft SQL Server Developer Edition bitových kopií pro Windows kontejnerů v DockerHub</span><span class="sxs-lookup"><span data-stu-id="2c5bc-194">Microsoft SQL Server Developer Edition images for Windows Containers on DockerHub</span></span>](https://hub.docker.com/r/microsoft/mssql-server-windows-developer/)

#### <a name="visual-studio-team-services-vsts-agent"></a><span data-ttu-id="2c5bc-195">Visual Studio Team Services (služby VSTS) agenta</span><span class="sxs-lookup"><span data-stu-id="2c5bc-195">Visual Studio Team Services (VSTS) agent</span></span>

* [<span data-ttu-id="2c5bc-196">Visual Studio Team Services (služby VSTS) agenta Image na DockerHub</span><span class="sxs-lookup"><span data-stu-id="2c5bc-196">Visual Studio Team Services (VSTS) agent images on DockerHub</span></span>](https://hub.docker.com/r/microsoft/vsts-agent/)

* [<span data-ttu-id="2c5bc-197">Visual Studio Team Services (služby VSTS) agenta obrázků na Githubu</span><span class="sxs-lookup"><span data-stu-id="2c5bc-197">Visual Studio Team Services (VSTS) agent images on GitHub</span></span>](https://github.com/Microsoft/vsts-agent-docker)

#### <a name="operations-management-suite-oms-linux-agent"></a><span data-ttu-id="2c5bc-198">Agent nástroje Operations Management Suite (OMS) Linux</span><span class="sxs-lookup"><span data-stu-id="2c5bc-198">Operations Management Suite (OMS) Linux agent</span></span>

* [<span data-ttu-id="2c5bc-199">Přehled agenta Operations Management Suite (OMS) Linux</span><span class="sxs-lookup"><span data-stu-id="2c5bc-199">Operations Management Suite (OMS) Linux agent overview</span></span>](https://github.com/Microsoft/OMS-Agent-for-Linux/blob/master/docs/Docker-Instructions.md#overview)

* [<span data-ttu-id="2c5bc-200">Operations Management Suite (OMS) Image na DockerHub</span><span class="sxs-lookup"><span data-stu-id="2c5bc-200">Operations Management Suite (OMS) images on DockerHub</span></span>](https://hub.docker.com/r/microsoft/vsts-agent/) 

* [<span data-ttu-id="2c5bc-201">Obrázky Operations Management Suite (OMS) na Githubu</span><span class="sxs-lookup"><span data-stu-id="2c5bc-201">Operations Management Suite (OMS) images on GitHub</span></span>](https://github.com/Microsoft/OMS-docker)

#### <a name="microsoft-azure-command-line-interface-cli"></a><span data-ttu-id="2c5bc-202">Rozhraní příkazového řádku Microsoft Azure (CLI)</span><span class="sxs-lookup"><span data-stu-id="2c5bc-202">Microsoft Azure Command Line Interface (CLI)</span></span>

* [<span data-ttu-id="2c5bc-203">Microsoft Azure rozhraní příkazového řádku (CLI) Image na DockerHub</span><span class="sxs-lookup"><span data-stu-id="2c5bc-203">Microsoft Azure Command Line Interface (CLI) images on DockerHub</span></span>](Docker image for Microsoft Azure Command Line Interface) 

* [<span data-ttu-id="2c5bc-204">Microsoft Azure rozhraní příkazového řádku (CLI) bitové kopie na Githubu</span><span class="sxs-lookup"><span data-stu-id="2c5bc-204">Microsoft Azure Command Line Interface (CLI) images on GitHub</span></span>](https://github.com/Microsoft/OMS-docker)

> [!Note]
> <span data-ttu-id="2c5bc-205">Pokud nemáte předplatné Azure, [Přihlaste se ještě dnes](https://azure.microsoft.com/free/?b=16.48) bezplatný účet 30 dnů a 200 USD get v kredity Azure můžete vyzkoušet na libovolnou kombinaci služby Azure.</span><span class="sxs-lookup"><span data-stu-id="2c5bc-205">If you do not have an Azure subscription, [sign up today](https://azure.microsoft.com/free/?b=16.48) for a free 30-day account and get $200 in Azure Credits to try out any combination of Azure services.</span></span>
>

#### <a name="microsoft-azure-cosmos-db-emulator-windows-containers-only"></a><span data-ttu-id="2c5bc-206">Emulátor systému Cosmos DB Microsoft Azure (pouze Windows kontejnery)</span><span class="sxs-lookup"><span data-stu-id="2c5bc-206">Microsoft Azure Cosmos DB Emulator (Windows Containers only)</span></span>

* [<span data-ttu-id="2c5bc-207">Microsoft Azure Cosmos DB emulátoru Image na DockerHub</span><span class="sxs-lookup"><span data-stu-id="2c5bc-207">Microsoft Azure Cosmos DB Emulator images on DockerHub</span></span>](https://hub.docker.com/r/microsoft/azure-cosmosdb-emulator) 

* [<span data-ttu-id="2c5bc-208">Použití emulátoru DB Cosmos Azure pro místní vývoj a testování</span><span class="sxs-lookup"><span data-stu-id="2c5bc-208">Use the Azure Cosmos DB Emulator for local development and testing</span></span>](https://docs.microsoft.com/azure/cosmos-db/local-emulator#developing-with-the-emulator)

## <a name="exploring-the-rich-docker-development-ecosystem"></a><span data-ttu-id="2c5bc-209">Zkoumání bohatý ekosystém vývoj Docker</span><span class="sxs-lookup"><span data-stu-id="2c5bc-209">Exploring the rich Docker development ecosystem</span></span>

<span data-ttu-id="2c5bc-210">Teď, když jste se naučili o Docker platformy a jiné imagí Dockeru, dalším krokem je prozkoumat bohatý ekosystém Docker.</span><span class="sxs-lookup"><span data-stu-id="2c5bc-210">Now that you have learned about the Docker platform and different Docker images, the next step is to explore the rich Docker ecosystem.</span></span> <span data-ttu-id="2c5bc-211">Následující odkazy vám ukážou, jak nástroje Microsoft doplňují vývoj kontejneru.</span><span class="sxs-lookup"><span data-stu-id="2c5bc-211">The following links show you how the Microsoft tools complement container development.</span></span>

* [<span data-ttu-id="2c5bc-212">Společně pomocí rozhraní .NET a Docker</span><span class="sxs-lookup"><span data-stu-id="2c5bc-212">Using .NET and Docker together</span></span>](https://blogs.msdn.microsoft.com/dotnet/2017/05/25/using-net-and-docker-together/) 
* [<span data-ttu-id="2c5bc-213">Návrh a vývoj aplikace s více kontejneru a na základě Mikroslužbu .NET</span><span class="sxs-lookup"><span data-stu-id="2c5bc-213">Designing and Developing Multi-Container and Microservice-Based .NET Applications</span></span>](../standard/microservices-architecture/multi-container-microservice-net-applications)
* [<span data-ttu-id="2c5bc-214">Rozšíření sady Visual Studio Code Docker</span><span class="sxs-lookup"><span data-stu-id="2c5bc-214">Visual Studio Code Docker extension</span></span>](https://code.visualstudio.com/docs/languages/dockerfile) 
* [<span data-ttu-id="2c5bc-215">Naučte se používat Azure Service Fabric</span><span class="sxs-lookup"><span data-stu-id="2c5bc-215">Learn how to use Azure Service Fabric</span></span>](https://docs.microsoft.com/azure/service-fabric/) 
* [<span data-ttu-id="2c5bc-216">Ukázka spuštění získávání Service Fabric</span><span class="sxs-lookup"><span data-stu-id="2c5bc-216">Service Fabric Getting Started Sample</span></span>](https://azure.microsoft.com/resources/samples/service-fabric-dotnet-getting-started/)
* [<span data-ttu-id="2c5bc-217">Výhody Windows kontejnery</span><span class="sxs-lookup"><span data-stu-id="2c5bc-217">Benefits of Windows Containers</span></span>](https://docs.microsoft.com/virtualization/windowscontainers/about/index#video-overview)
* [<span data-ttu-id="2c5bc-218">Práce s nástroji Visual Studio Docker</span><span class="sxs-lookup"><span data-stu-id="2c5bc-218">Working with Visual Studio Docker Tools</span></span>](https://docs.microsoft.com/aspnet/core/publishing/visual-studio-tools-for-docker)
* [<span data-ttu-id="2c5bc-219">Nasazení bitových kopií Docker z registru kontejner Azure do Azure kontejner instancí</span><span class="sxs-lookup"><span data-stu-id="2c5bc-219">Deploying Docker Images from the Azure Container Registry to Azure Container Instances</span></span>](https://blogs.msdn.microsoft.com/stevelasker/2017/07/28/deploying-docker-images-from-the-azure-container-registry-to-azure-container-instances/)
* [<span data-ttu-id="2c5bc-220">Ladění pomocí kódu v sadě Visual Studio</span><span class="sxs-lookup"><span data-stu-id="2c5bc-220">Debugging with Visual Studio Code</span></span>](https://code.visualstudio.com/docs/nodejs/debugging-recipes#_nodejs-typescript-docker-container) 
* [<span data-ttu-id="2c5bc-221">Načítání rukou pomocí sady Visual Studio pro Mac, kontejnery a bez serveru kódu v cloudu</span><span class="sxs-lookup"><span data-stu-id="2c5bc-221">Getting hands on with Visual Studio for Mac, containers, and serverless code in the cloud</span></span>](https://blogs.msdn.microsoft.com/visualstudio/2017/08/31/hands-on-with-visual-studio-for-mac-containers-serverless-code-in-the-cloud/#comments)
* [<span data-ttu-id="2c5bc-222">Začínáme s Docker a Visual Studio pro Mac testovacího prostředí</span><span class="sxs-lookup"><span data-stu-id="2c5bc-222">Getting Started with Docker and Visual Studio for Mac Lab</span></span>](https://github.com/Microsoft/vs4mac-labs/tree/master/Docker/Getting-Started)

## <a name="next-steps"></a><span data-ttu-id="2c5bc-223">Další kroky</span><span class="sxs-lookup"><span data-stu-id="2c5bc-223">Next Steps</span></span>

* [<span data-ttu-id="2c5bc-224">Další základní informace o Docker s .NET Core</span><span class="sxs-lookup"><span data-stu-id="2c5bc-224">Learn Docker Basics with .NET Core</span></span>](../docker/docker-basics-dotnet-core.md)
* [<span data-ttu-id="2c5bc-225">Vytváření bitových kopií Docker .NET Core</span><span class="sxs-lookup"><span data-stu-id="2c5bc-225">Building .NET Core Docker Images</span></span>](../docker/building-net-docker-images)