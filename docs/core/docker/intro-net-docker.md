---
title: Úvod do rozhraní .NET a Docker
description: Principy Docker a .NET Core
author: jralexander
ms.author: johalex
ms.date: 11/06/2017
ms.topic: conceptual
ms.prod: dotnet-core
ms.technology: dotnet-docker
ms.devlang: dotnet
manager: wpickett
ms.custom: mvc
ms.workload:
- dotnetcore
ms.openlocfilehash: 3ceeead391c3e64db6849236a0f6821eb03abc3c
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
---
# <a name="introduction-to-net-and-docker"></a><span data-ttu-id="f1c87-103">Úvod do rozhraní .NET a Docker</span><span class="sxs-lookup"><span data-stu-id="f1c87-103">Introduction to .NET and Docker</span></span>

<span data-ttu-id="f1c87-104">Tento článek poskytuje úvod a koncepční základní informace o práci s .NET v nástroji Docker.</span><span class="sxs-lookup"><span data-stu-id="f1c87-104">This article provides an introduction and conceptual background to working with .NET on Docker.</span></span>

## <a name="docker-packaging-your-apps-to-deploy-and-run-anywhere"></a><span data-ttu-id="f1c87-105">Docker: Zabalení aplikace nasadit a spustit odkudkoli</span><span class="sxs-lookup"><span data-stu-id="f1c87-105">Docker: Packaging your apps to deploy and run anywhere</span></span>

<span data-ttu-id="f1c87-106">[Docker](../../standard/microservices-architecture/container-docker-introduction/docker-defined.md) je otevřená platforma, která umožňuje vývojáři a správci sestavení [bitové kopie](https://docs.docker.com/glossary/?term=image), odeslání a spustit distribuované aplikace v prostředí volně izolované názvem [kontejneru](https://www.docker.com/what-container).</span><span class="sxs-lookup"><span data-stu-id="f1c87-106">[Docker](../../standard/microservices-architecture/container-docker-introduction/docker-defined.md) is an open platform that enables developers and administrators to build [images](https://docs.docker.com/glossary/?term=image), ship, and run distributed applications in a loosely isolated environment called a [container](https://www.docker.com/what-container).</span></span> <span data-ttu-id="f1c87-107">Tento přístup umožňuje správu životního cyklu aplikací efektivní mezi vývoj, QA a provozní prostředí.</span><span class="sxs-lookup"><span data-stu-id="f1c87-107">This approach enables efficient application lifecycle management between development, QA, and production environments.</span></span>
 
<span data-ttu-id="f1c87-108">[Docker platformy](https://docs.docker.com/engine/docker-overview/#the-docker-platform) používá [modulu Docker](https://docs.docker.com/engine/docker-overview/#docker-engine) rychle vytvářet a balíček aplikace jako [imagí Dockeru](https://docs.docker.com/glossary/?term=image) vytvořený soubory, které jsou napsané v [soubor Docker ](https://docs.docker.com/glossary/?term=Dockerfile) formátu, který pak je nasadit a spustit [vrstvený kontejneru](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/#container-and-layers).</span><span class="sxs-lookup"><span data-stu-id="f1c87-108">The [Docker platform](https://docs.docker.com/engine/docker-overview/#the-docker-platform) uses the [Docker Engine](https://docs.docker.com/engine/docker-overview/#docker-engine) to quickly build and package apps as [Docker images](https://docs.docker.com/glossary/?term=image) created using files written in the [Dockerfile](https://docs.docker.com/glossary/?term=Dockerfile) format that then is deployed and run in a [layered container](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/#container-and-layers).</span></span>

<span data-ttu-id="f1c87-109">Můžete buď vytvořit vlastní [na základě bitové kopie](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/#images-and-layers) jako dockerfiles nebo použijte existující z [registru](https://docs.docker.com/glossary/?term=registry), například [úložiště Docker Hub](https://docs.docker.com/glossary/?term=Docker%20Hub).</span><span class="sxs-lookup"><span data-stu-id="f1c87-109">You can either create your own [layered images](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/#images-and-layers) as dockerfiles or use existing ones from a [registry](https://docs.docker.com/glossary/?term=registry), like [Docker Hub](https://docs.docker.com/glossary/?term=Docker%20Hub).</span></span>

<span data-ttu-id="f1c87-110">[Vztah mezi Docker kontejnery, Image a registrech](../../standard/microservices-architecture/container-docker-introduction/docker-containers-images-registries.md) je důležité koncept při [architektury a sestavování kontejnerové aplikace nebo mikroslužeb](../../standard/microservices-architecture/architect-microservice-container-applications/index.md).</span><span class="sxs-lookup"><span data-stu-id="f1c87-110">The [relationship between Docker containers, images, and registries](../../standard/microservices-architecture/container-docker-introduction/docker-containers-images-registries.md) is an important concept when [architecting and building containerized applications or microservices](../../standard/microservices-architecture/architect-microservice-container-applications/index.md).</span></span> <span data-ttu-id="f1c87-111">Tento přístup výrazně zkracuje doba mezi vývoj a nasazení.</span><span class="sxs-lookup"><span data-stu-id="f1c87-111">This approach greatly shortens the time between development and deployment.</span></span>

### <a name="further-reading-and-watching"></a><span data-ttu-id="f1c87-112">Další čtení (a sledování)</span><span class="sxs-lookup"><span data-stu-id="f1c87-112">Further reading (and watching)</span></span>

* [<span data-ttu-id="f1c87-113">Kontejnery založené na systému Windows: vývoj moderních aplikací pomocí řízení podnikové úrovni.</span><span class="sxs-lookup"><span data-stu-id="f1c87-113">Windows-based containers: Modern app development with enterprise-grade control.</span></span>](https://www.youtube.com/watch?v=Ryx3o0rD5lY&feature=youtu.be)
* [<span data-ttu-id="f1c87-114">Přehled docker</span><span class="sxs-lookup"><span data-stu-id="f1c87-114">Docker overview</span></span>](https://docs.docker.com/engine/docker-overview/)
* [<span data-ttu-id="f1c87-115">Soubor Docker kontejnerům Windows</span><span class="sxs-lookup"><span data-stu-id="f1c87-115">Dockerfile on Windows Containers</span></span>](/virtualization/windowscontainers/manage-docker/manage-windows-dockerfile)
* [<span data-ttu-id="f1c87-116">Osvědčené postupy pro psaní Dockerfiles</span><span class="sxs-lookup"><span data-stu-id="f1c87-116">Best practices for writing Dockerfiles</span></span>](https://docs.docker.com/engine/userguide/eng-image/dockerfile_best-practices/)
* [<span data-ttu-id="f1c87-117">Vytváření Imagí Dockeru pro aplikace .NET Core</span><span class="sxs-lookup"><span data-stu-id="f1c87-117">Building Docker Images for .NET Core applications</span></span>](../docker/building-net-docker-images.md)


### <a name="getting-net-docker-images"></a><span data-ttu-id="f1c87-118">Získávání imagí Dockeru rozhraní .NET</span><span class="sxs-lookup"><span data-stu-id="f1c87-118">Getting .NET Docker images</span></span>

<span data-ttu-id="f1c87-119">Oficiální Docker .NET bitové kopie se vytváří a optimalizované společností Microsoft.</span><span class="sxs-lookup"><span data-stu-id="f1c87-119">The Official .NET Docker images are created and optimized by Microsoft.</span></span> <span data-ttu-id="f1c87-120">Jsou veřejně dostupné v Microsoft úložiště na úložiště Docker Hub.</span><span class="sxs-lookup"><span data-stu-id="f1c87-120">They are publicly available in the Microsoft repositories on Docker Hub.</span></span> <span data-ttu-id="f1c87-121">Každý úložiště může obsahovat více bitových kopií, v závislosti na rozhraní .NET verze a na verze operačního systému.</span><span class="sxs-lookup"><span data-stu-id="f1c87-121">Each repository can contain multiple images, depending on .NET versions, and on OS versions.</span></span> <span data-ttu-id="f1c87-122">Většina úložiště image poskytují rozsáhlé označení vám pomohou vybrat konkrétní framework verze a operační systém (verze Windows nebo Linux distro).</span><span class="sxs-lookup"><span data-stu-id="f1c87-122">Most image repos provide extensive tagging to help you select both a specific framework version and an OS (Linux distro or Windows version).</span></span>

## <a name="scenario-based-guidance"></a><span data-ttu-id="f1c87-123">Scénář na základě pokyny</span><span class="sxs-lookup"><span data-stu-id="f1c87-123">Scenario based guidance</span></span>

<span data-ttu-id="f1c87-124">Záměr společnosti Microsoft pro rozhraní .NET úložiště je získat podrobné a zaměřují se úložiště, které představují konkrétní scénář nebo zatížení.</span><span class="sxs-lookup"><span data-stu-id="f1c87-124">Microsoft’s intent for .NET repositories is to have granular and focused repos, which represent a specific scenario or workload.</span></span>

<span data-ttu-id="f1c87-125">`microsoft/aspnetcore` Bitové kopie jsou optimalizované pro aplikace ASP.NET Core na Docker, takže kontejnery můžete spustit rychlejší.</span><span class="sxs-lookup"><span data-stu-id="f1c87-125">The `microsoft/aspnetcore` images are optimized for ASP.NET Core apps on Docker, so containers can start faster.</span></span>

<span data-ttu-id="f1c87-126">Obrázky .NET Core (`microsoft/dotnet`) jsou určené pro konzolu aplikace založené na .NET Core.</span><span class="sxs-lookup"><span data-stu-id="f1c87-126">The .NET Core images (`microsoft/dotnet`) are intended for console apps based on .NET Core.</span></span> <span data-ttu-id="f1c87-127">Například procesy batch, Azure WebJobs a scénáře konzoly by měl používat optimalizované Image .NET Core.</span><span class="sxs-lookup"><span data-stu-id="f1c87-127">For example, batch processes, Azure WebJobs, and other console scenarios should use optimized .NET Core images.</span></span>

<span data-ttu-id="f1c87-128">Nejobvyklejší vodorovné scénář pro použití aplikací Docker a .NET je pro produkční nasazení a hostování.</span><span class="sxs-lookup"><span data-stu-id="f1c87-128">The most obvious horizontal scenario for using Docker and .NET applications is for production deployment and hosting.</span></span> <span data-ttu-id="f1c87-129">Ukazuje se, že produkční je jenom jedním scénářem, a další ty, které jsou rovnoměrně užitečné.</span><span class="sxs-lookup"><span data-stu-id="f1c87-129">It turns out that production is just one scenario and the other ones are equally useful.</span></span> <span data-ttu-id="f1c87-130">Tyto scénáře nejsou specifické pro rozhraní .NET, ale měli použít pro většině platforem developer.</span><span class="sxs-lookup"><span data-stu-id="f1c87-130">These scenarios are not specific to .NET, but should apply to most developer platforms.</span></span>

* <span data-ttu-id="f1c87-131">**Nainstalujte nízkým třením** – .NET můžete vyzkoušet bez místní instalace.</span><span class="sxs-lookup"><span data-stu-id="f1c87-131">**Low friction install** — You can try out .NET without a local install.</span></span> <span data-ttu-id="f1c87-132">Stáhněte pouze bitovou kopii Docker s .NET v ní.</span><span class="sxs-lookup"><span data-stu-id="f1c87-132">Just download a Docker image with .NET in it.</span></span>

* <span data-ttu-id="f1c87-133">**Vývoj v kontejneru** – můžete vyvíjet v prostředí konzistentní provedení vývoj a produkční prostředí podobné (zabraňující problémy jako globální stav na počítačích vývojářů).</span><span class="sxs-lookup"><span data-stu-id="f1c87-133">**Develop in a container** — You can develop in a consistent environment, making development and production environments similar (avoiding issues like global state on developer machines).</span></span> <span data-ttu-id="f1c87-134">Nástroje sady Visual Studio pro Docker i umožňují spusťte kontejner přímo ze sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="f1c87-134">Visual Studio Tools for Docker even enable you to start a container directly from Visual Studio.</span></span>

* <span data-ttu-id="f1c87-135">**Testování v kontejneru** – můžete otestovat v kontejneru, snižuje chyby způsobené nesprávnou konfigurací prostředí nebo jiné změny zanechat z poslední test.</span><span class="sxs-lookup"><span data-stu-id="f1c87-135">**Test in a container** — You can test in a container, reducing failures due to incorrectly configured environments or other changes left behind from the last test.</span></span>

* <span data-ttu-id="f1c87-136">**Sestavení v kontejneru** – můžete vytvořit kód v kontejneru, takže není nutné správně nakonfigurovat počítačů sdílené sestavení pro prostředí s více, ale místo toho přesunout do "BYOC" (přineste si vlastní kontejner) přístup.</span><span class="sxs-lookup"><span data-stu-id="f1c87-136">**Build in a container** — You can build code in a container, avoiding the need to correctly configure shared build machines for multiple environments but instead move to a “BYOC” (bring your own container) approach.</span></span>

* <span data-ttu-id="f1c87-137">**Nasazení ve všech prostředích** – můžete nasadit bitovou prochází všechna prostředí.</span><span class="sxs-lookup"><span data-stu-id="f1c87-137">**Deployment in all environments** — You can deploy an image through all of your environments.</span></span> <span data-ttu-id="f1c87-138">Tento přístup snižuje chyby způsobené konfigurace rozdílů, obvykle změny chování bitovou kopii prostřednictvím externí konfigurace (například vloženého prostředí proměnné).</span><span class="sxs-lookup"><span data-stu-id="f1c87-138">This approach reduces failures due to configuration differences, typically changing the image behavior via external configuration (for example, injected environment variables).</span></span>

<span data-ttu-id="f1c87-139">[Obecné pokyny](../../standard/microservices-architecture/net-core-net-framework-containers/general-guidance.md) rozhodování mezi .NET Core a rozhraní .NET Framework pro vývoj kontejner Docker.</span><span class="sxs-lookup"><span data-stu-id="f1c87-139">[General guidance](../../standard/microservices-architecture/net-core-net-framework-containers/general-guidance.md) for deciding between .NET Core and .NET Framework for Docker container development.</span></span>

### <a name="common-docker-development-scenarios"></a><span data-ttu-id="f1c87-140">Běžné scénáře vývoj Docker</span><span class="sxs-lookup"><span data-stu-id="f1c87-140">Common Docker development scenarios</span></span>

#### <a name="net-core"></a><span data-ttu-id="f1c87-141">.NET Core</span><span class="sxs-lookup"><span data-stu-id="f1c87-141">.NET Core</span></span>

<span data-ttu-id="f1c87-142">**.NET core prostředky**</span><span class="sxs-lookup"><span data-stu-id="f1c87-142">**.NET Core resources**</span></span>

 <span data-ttu-id="f1c87-143">Vyberte ukázky .NET Core splňující vaše scénáře, které vás zajímají.</span><span class="sxs-lookup"><span data-stu-id="f1c87-143">Pick the .NET Core samples that fit your scenarios of interest.</span></span> <span data-ttu-id="f1c87-144">Všechny ukázkové pokyny popisují, jak cílových bitových kopií systému Windows nebo Linux Docker ze systému Windows, Linux nebo systému macOS hostitelů.</span><span class="sxs-lookup"><span data-stu-id="f1c87-144">All sample instructions describe how to target Windows or Linux Docker images from Windows, Linux, or macOS hosts.</span></span>

<span data-ttu-id="f1c87-145">Ukázky použití .NET Core 2.0.</span><span class="sxs-lookup"><span data-stu-id="f1c87-145">The samples use .NET Core 2.0.</span></span> <span data-ttu-id="f1c87-146">Používají Docker [více fáze sestavení](https://github.com/dotnet/announcements/issues/18) a [více architektury značky](https://github.com/dotnet/announcements/issues/14) podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="f1c87-146">They use Docker [multi-stage build](https://github.com/dotnet/announcements/issues/18) and [multi-arch tags](https://github.com/dotnet/announcements/issues/14) where appropriate.</span></span>

* [<span data-ttu-id="f1c87-147">.NET core Image na DockerHub</span><span class="sxs-lookup"><span data-stu-id="f1c87-147">.NET Core images on DockerHub</span></span>](https://hub.docker.com/r/microsoft/dotnet/)

* [<span data-ttu-id="f1c87-148">Dockerize aplikace .NET Core</span><span class="sxs-lookup"><span data-stu-id="f1c87-148">Dockerize a .NET Core application</span></span>](https://docs.docker.com/engine/examples/dotnetcore/)

* <span data-ttu-id="f1c87-149">Tento příklad .NET Core Docker znázorňuje postup [pomocí Docker ve vývojových procesech .NET Core](https://github.com/dotnet/dotnet-docker-samples/tree/master/dotnetapp-dev).</span><span class="sxs-lookup"><span data-stu-id="f1c87-149">This .NET Core Docker sample demonstrates how to [use Docker in your .NET Core development process](https://github.com/dotnet/dotnet-docker-samples/tree/master/dotnetapp-dev).</span></span> <span data-ttu-id="f1c87-150">Ukázka funguje s kontejnery Linux a Windows.</span><span class="sxs-lookup"><span data-stu-id="f1c87-150">The sample works with both Linux and Windows containers.</span></span>

* <span data-ttu-id="f1c87-151">Tento příklad .NET Core Docker znázorňuje osvědčených postupů vzor [vytváření imagí Dockeru pro aplikace .NET Core pro produkční prostředí.](https://github.com/dotnet/dotnet-docker-samples/tree/master/dotnetapp-prod)</span><span class="sxs-lookup"><span data-stu-id="f1c87-151">This .NET Core Docker sample demonstrates a best practice pattern for [building Docker images for .NET Core apps for production.](https://github.com/dotnet/dotnet-docker-samples/tree/master/dotnetapp-prod)</span></span> <span data-ttu-id="f1c87-152">Ukázka funguje s kontejnery Linux a Windows.</span><span class="sxs-lookup"><span data-stu-id="f1c87-152">The sample works with both Linux and Windows containers.</span></span>

* <span data-ttu-id="f1c87-153">To [ukázka .NET Core Docker](https://github.com/dotnet/dotnet-docker-samples/tree/master/dotnetapp-selfcontained) ukazuje osvědčených postupů vzor pro vytváření imagí Dockeru pro [nezávislý aplikace .NET Core](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="f1c87-153">This [.NET Core Docker sample](https://github.com/dotnet/dotnet-docker-samples/tree/master/dotnetapp-selfcontained) demonstrates a best practice pattern for building Docker images for [self-contained .NET Core applications](../deploying/index.md).</span></span> <span data-ttu-id="f1c87-154">Použít pro kontejner nejmenší provozní bez výhody z [sdílení základní Image mezi kontejnery](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/).</span><span class="sxs-lookup"><span data-stu-id="f1c87-154">Used for the smallest production container without a benefit from [sharing base images between containers](https://docs.docker.com/engine/userguide/storagedriver/imagesandcontainers/).</span></span> <span data-ttu-id="f1c87-155">Nižších vrstvách Docker však může sdílet.</span><span class="sxs-lookup"><span data-stu-id="f1c87-155">However, lower Docker layers could be shared.</span></span>

#### <a name="arm32--raspberry-pi"></a><span data-ttu-id="f1c87-156">ARM32 / malin pí</span><span class="sxs-lookup"><span data-stu-id="f1c87-156">ARM32 / Raspberry Pi</span></span>

* [<span data-ttu-id="f1c87-157">.NET core Runtime ARM32 sestavení oznámení</span><span class="sxs-lookup"><span data-stu-id="f1c87-157">.NET Core Runtime ARM32 builds announcement</span></span>](https://github.com/dotnet/announcements/issues/29)

* [<span data-ttu-id="f1c87-158">ARM32 / malin platformy .NET Core bitové kopie na DockerHub</span><span class="sxs-lookup"><span data-stu-id="f1c87-158">ARM32 / Raspberry Pi .NET Core images on DockerHub</span></span>](https://hub.docker.com/r/microsoft/dotnet/)

* [<span data-ttu-id="f1c87-159">ARM32 / Malinová platformy .NET Core Docker ukázky na Githubu</span><span class="sxs-lookup"><span data-stu-id="f1c87-159">ARM32 / Raspberry Pi .NET Core Docker Samples on GitHub</span></span>](https://github.com/dotnet/dotnet-docker-samples#arm32--raspberry-pi)

#### <a name="net-framework"></a><span data-ttu-id="f1c87-160">.NET Framework</span><span class="sxs-lookup"><span data-stu-id="f1c87-160">.NET Framework</span></span>

* [<span data-ttu-id="f1c87-161">Rozhraní .NET framework Image na DockerHub</span><span class="sxs-lookup"><span data-stu-id="f1c87-161">.NET Framework images on DockerHub</span></span>](https://hub.docker.com/r/microsoft/dotnet-framework/)

<span data-ttu-id="f1c87-162">Toto úložiště obsahovat ukázky, která ukazují různých konfiguracích Docker rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f1c87-162">This repo contain samples that demonstrate various .NET Framework Docker configurations.</span></span> <span data-ttu-id="f1c87-163">Tyto Image můžete použít jako základ imagí Dockeru.</span><span class="sxs-lookup"><span data-stu-id="f1c87-163">You can use these images as the basis of your own Docker images.</span></span>

<span data-ttu-id="f1c87-164">**Rozhraní .NET framework 4.7**</span><span class="sxs-lookup"><span data-stu-id="f1c87-164">**.NET Framework 4.7**</span></span>

<span data-ttu-id="f1c87-165">[Dotnet – ukázka framework: 4.7](https://github.com/Microsoft/dotnet-framework-docker-samples/tree/master/dotnetapp-4.7) ukazuje základní "text hello world" použití [4.7 rozhraní .NET Framework](../../framework/whats-new/index.md#v47).</span><span class="sxs-lookup"><span data-stu-id="f1c87-165">The [dotnet-framework:4.7 sample](https://github.com/Microsoft/dotnet-framework-docker-samples/tree/master/dotnetapp-4.7) demonstrates basic "hello world" usage of the [.NET Framework 4.7](../../framework/whats-new/index.md#v47).</span></span> <span data-ttu-id="f1c87-166">Ho se dozvíte, jak můžete sestavit a nasazení aplikace spoléhat na [rozhraní .NET Framework 4.7 docker image](https://github.com/Microsoft/dotnet-framework-docker-samples/blob/master/dotnetapp-4.7/Dockerfile).</span><span class="sxs-lookup"><span data-stu-id="f1c87-166">It shows you how you can build and deploy the app relying on the [.NET Framework 4.7 docker image](https://github.com/Microsoft/dotnet-framework-docker-samples/blob/master/dotnetapp-4.7/Dockerfile).</span></span>

<span data-ttu-id="f1c87-167">**Rozhraní .NET framework 4.6.2**</span><span class="sxs-lookup"><span data-stu-id="f1c87-167">**.NET Framework 4.6.2**</span></span>

<span data-ttu-id="f1c87-168">[Dotnet – ukázka framework: 4.6.2](https://github.com/Microsoft/dotnet-framework-docker-samples/tree/master/dotnetapp-4.6.2) ukazuje základní "text hello world" použití [rozhraní .NET Framework 4.6.2](../../framework/whats-new/index.md#v462).</span><span class="sxs-lookup"><span data-stu-id="f1c87-168">The [dotnet-framework:4.6.2 sample](https://github.com/Microsoft/dotnet-framework-docker-samples/tree/master/dotnetapp-4.6.2) demonstrates basic "hello world" usage of the [.NET Framework 4.6.2](../../framework/whats-new/index.md#v462).</span></span> <span data-ttu-id="f1c87-169">Ho se dozvíte, jak můžete sestavit a nasazení aplikace spoléhat na [rozhraní .NET Framework 4.6.2 docker image](https://github.com/Microsoft/dotnet-framework-docker-samples/blob/master/dotnetapp-4.6.2/Dockerfile).</span><span class="sxs-lookup"><span data-stu-id="f1c87-169">It shows you how you can build and deploy the app relying on the [.NET Framework 4.6.2 docker image](https://github.com/Microsoft/dotnet-framework-docker-samples/blob/master/dotnetapp-4.6.2/Dockerfile).</span></span>

<span data-ttu-id="f1c87-170">**Rozhraní .NET framework 3.5**</span><span class="sxs-lookup"><span data-stu-id="f1c87-170">**.NET Framework 3.5**</span></span>

 <span data-ttu-id="f1c87-171">[Dotnet – ukázka framework: 3.5](https://github.com/Microsoft/dotnet-framework-docker-samples/tree/master/dotnetapp-3.5) ukazuje základní "text hello world" použití [rozhraní .NET Framework 3.5](https://github.com/Microsoft/dotnet-framework-docker-samples/blob/master/dotnetapp-3.5/dotnetapp-3.5/Dockerfile).</span><span class="sxs-lookup"><span data-stu-id="f1c87-171">The [dotnet-framework:3.5 sample](https://github.com/Microsoft/dotnet-framework-docker-samples/tree/master/dotnetapp-3.5) demonstrates basic "hello world" usage of [.NET Framework 3.5](https://github.com/Microsoft/dotnet-framework-docker-samples/blob/master/dotnetapp-3.5/dotnetapp-3.5/Dockerfile).</span></span> <span data-ttu-id="f1c87-172">Ho ukazuje, jak můžete sestavit a nasazení projektu spoléhat na rozhraní .NET Framework 3.5 v Docker.</span><span class="sxs-lookup"><span data-stu-id="f1c87-172">It shows you how you can build and deploy a project relying on .NET Framework 3.5 in Docker.</span></span>

#### <a name="aspnet-core"></a><span data-ttu-id="f1c87-173">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="f1c87-173">ASP.NET Core</span></span>

* <span data-ttu-id="f1c87-174">[Tato ukázka ASP.NET Core Docker](https://github.com/dotnet/dotnet-docker-samples/tree/master/aspnetapp) ukazuje osvědčených postupů vzor pro vytváření imagí Dockeru pro ASP.NET Core aplikace pro produkční prostředí.</span><span class="sxs-lookup"><span data-stu-id="f1c87-174">[This ASP.NET Core Docker sample](https://github.com/dotnet/dotnet-docker-samples/tree/master/aspnetapp) demonstrates a best practice pattern for building Docker images for ASP.NET Core apps for production.</span></span> <span data-ttu-id="f1c87-175">Ukázka funguje s kontejnery Linux a Windows.</span><span class="sxs-lookup"><span data-stu-id="f1c87-175">The sample works with both Linux and Windows containers.</span></span>

* [<span data-ttu-id="f1c87-176">ASP.NET Core Image na DockerHub</span><span class="sxs-lookup"><span data-stu-id="f1c87-176">ASP.NET Core images on DockerHub</span></span>](https://hub.docker.com/r/microsoft/aspnetcore-build/)

* [<span data-ttu-id="f1c87-177">ASP.NET Core bitové kopie na Githubu</span><span class="sxs-lookup"><span data-stu-id="f1c87-177">ASP.NET Core images on GitHub</span></span>](https://github.com/aspnet/aspnet-docker)

#### <a name="aspnet-framework"></a><span data-ttu-id="f1c87-178">Rozhraní ASP.NET</span><span class="sxs-lookup"><span data-stu-id="f1c87-178">ASP.NET Framework</span></span>

* [<span data-ttu-id="f1c87-179">Rozhraní ASP.NET Image na DockerHub</span><span class="sxs-lookup"><span data-stu-id="f1c87-179">ASP.NET Framework images on DockerHub</span></span>](https://hub.docker.com/r/microsoft/aspnet/)

* [<span data-ttu-id="f1c87-180">Aplikace webových formulářů ASP.NET na rozhraní .NET Framework 4.6.2 vzorku</span><span class="sxs-lookup"><span data-stu-id="f1c87-180">ASP.NET Web Forms app on .NET Framework 4.6.2 sample</span></span>](https://github.com/Microsoft/dotnet-framework-docker-samples/tree/master/aspnetapp)

#### <a name="windows-communication-framework-wcf"></a><span data-ttu-id="f1c87-181">Windows Communication Framework (WCF)</span><span class="sxs-lookup"><span data-stu-id="f1c87-181">Windows Communication Framework (WCF)</span></span>

* [<span data-ttu-id="f1c87-182">Image Windows Communication Framework (WCF) na DockerHub</span><span class="sxs-lookup"><span data-stu-id="f1c87-182">Windows Communication Framework (WCF) images on DockerHub</span></span>](https://hub.docker.com/r/microsoft/wcf/)

* [<span data-ttu-id="f1c87-183">Bitové kopie služby Windows Communication Framework (WCF) na Githubu</span><span class="sxs-lookup"><span data-stu-id="f1c87-183">Windows Communication Framework (WCF) images on GitHub</span></span>](https://github.com/microsoft/wcf-docker)

* [<span data-ttu-id="f1c87-184">Ukázky Windows Communication Framework (WCF) Docker pomocí rozhraní .NET Full Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="f1c87-184">Windows Communication Framework (WCF) Docker samples using .NET Full Framework 4.6.2</span></span>](https://github.com/Microsoft/wcf-docker-samples)

#### <a name="internet-information-server-iis"></a><span data-ttu-id="f1c87-185">Internet Information Server (IIS)</span><span class="sxs-lookup"><span data-stu-id="f1c87-185">Internet Information Server (IIS)</span></span>

* [<span data-ttu-id="f1c87-186">Image Internet Information Server (IIS) na DockerHub</span><span class="sxs-lookup"><span data-stu-id="f1c87-186">Internet Information Server (IIS) images on DockerHub</span></span>](https://hub.docker.com/r/microsoft/iis/)

* [<span data-ttu-id="f1c87-187">Obrázky Internet Information Server (IIS) na Githubu</span><span class="sxs-lookup"><span data-stu-id="f1c87-187">Internet Information Server (IIS) images on GitHub</span></span>](https://github.com/microsoft/iis-docker)

### <a name="interact-with-other-microsoft-stack-container-images"></a><span data-ttu-id="f1c87-188">Komunikovat s jiných Microsoft zásobníku kontejneru obrázků</span><span class="sxs-lookup"><span data-stu-id="f1c87-188">Interact with other Microsoft stack container images</span></span>

#### <a name="microsoft-sql-server"></a><span data-ttu-id="f1c87-189">Microsoft SQL Server</span><span class="sxs-lookup"><span data-stu-id="f1c87-189">Microsoft SQL Server</span></span>

* [<span data-ttu-id="f1c87-190">Spusťte Microsoft SQL Server pro Linux 2017 kontejneru image s Docker rychlý start</span><span class="sxs-lookup"><span data-stu-id="f1c87-190">Run the Microsoft SQL Server for Linux 2017 container image with Docker Quickstart</span></span>](https://docs.microsoft.com/sql/linux/quickstart-install-connect-docker)

* [<span data-ttu-id="f1c87-191">Microsoft SQL Server pro Linux bitové kopie na DockerHub</span><span class="sxs-lookup"><span data-stu-id="f1c87-191">Microsoft SQL Server for Linux images on DockerHub</span></span>](https://hub.docker.com/r/microsoft/mssql-server-linux/)

* [<span data-ttu-id="f1c87-192">Microsoft SQL Server Express Edition bitových kopií pro Windows kontejnerů v DockerHub</span><span class="sxs-lookup"><span data-stu-id="f1c87-192">Microsoft SQL Server Express Edition images for Windows Containers on DockerHub</span></span>](https://hub.docker.com/r/microsoft/mssql-server-windows-express/)

* [<span data-ttu-id="f1c87-193">Microsoft SQL Server Developer Edition bitových kopií pro Windows kontejnerů v DockerHub</span><span class="sxs-lookup"><span data-stu-id="f1c87-193">Microsoft SQL Server Developer Edition images for Windows Containers on DockerHub</span></span>](https://hub.docker.com/r/microsoft/mssql-server-windows-developer/)

#### <a name="visual-studio-team-services-vsts-agent"></a><span data-ttu-id="f1c87-194">Visual Studio Team Services (služby VSTS) agenta</span><span class="sxs-lookup"><span data-stu-id="f1c87-194">Visual Studio Team Services (VSTS) agent</span></span>

* [<span data-ttu-id="f1c87-195">Visual Studio Team Services (služby VSTS) agenta Image na DockerHub</span><span class="sxs-lookup"><span data-stu-id="f1c87-195">Visual Studio Team Services (VSTS) agent images on DockerHub</span></span>](https://hub.docker.com/r/microsoft/vsts-agent/)

* [<span data-ttu-id="f1c87-196">Visual Studio Team Services (služby VSTS) agenta obrázků na Githubu</span><span class="sxs-lookup"><span data-stu-id="f1c87-196">Visual Studio Team Services (VSTS) agent images on GitHub</span></span>](https://github.com/Microsoft/vsts-agent-docker)

#### <a name="operations-management-suite-oms-linux-agent"></a><span data-ttu-id="f1c87-197">Agent nástroje Operations Management Suite (OMS) Linux</span><span class="sxs-lookup"><span data-stu-id="f1c87-197">Operations Management Suite (OMS) Linux agent</span></span>

* [<span data-ttu-id="f1c87-198">Přehled agenta Operations Management Suite (OMS) Linux</span><span class="sxs-lookup"><span data-stu-id="f1c87-198">Operations Management Suite (OMS) Linux agent overview</span></span>](https://github.com/Microsoft/OMS-Agent-for-Linux/blob/master/docs/Docker-Instructions.md)

* [<span data-ttu-id="f1c87-199">Operations Management Suite (OMS) Image na DockerHub</span><span class="sxs-lookup"><span data-stu-id="f1c87-199">Operations Management Suite (OMS) images on DockerHub</span></span>](https://hub.docker.com/r/microsoft/oms/)

* [<span data-ttu-id="f1c87-200">Obrázky Operations Management Suite (OMS) na Githubu</span><span class="sxs-lookup"><span data-stu-id="f1c87-200">Operations Management Suite (OMS) images on GitHub</span></span>](https://github.com/Microsoft/OMS-docker)

#### <a name="microsoft-azure-command-line-interface-cli"></a><span data-ttu-id="f1c87-201">Rozhraní příkazového řádku Microsoft Azure (CLI)</span><span class="sxs-lookup"><span data-stu-id="f1c87-201">Microsoft Azure Command Line Interface (CLI)</span></span>

* [<span data-ttu-id="f1c87-202">Microsoft Azure rozhraní příkazového řádku (CLI) Image na DockerHub</span><span class="sxs-lookup"><span data-stu-id="f1c87-202">Microsoft Azure Command Line Interface (CLI) images on DockerHub</span></span>](https://hub.docker.com/r/microsoft/azure-cli/) 

* [<span data-ttu-id="f1c87-203">Microsoft Azure rozhraní příkazového řádku (CLI) bitové kopie na Githubu</span><span class="sxs-lookup"><span data-stu-id="f1c87-203">Microsoft Azure Command-Line Interface (CLI) images on GitHub</span></span>](https://github.com/Azure/azure-cli#Docker)

> [!NOTE]
> <span data-ttu-id="f1c87-204">Pokud nemáte předplatné Azure, [Přihlaste se ještě dnes](https://azure.microsoft.com/free/?b=16.48) bezplatný účet 30 dnů a 200 USD get v kredity Azure můžete vyzkoušet na libovolnou kombinaci služby Azure.</span><span class="sxs-lookup"><span data-stu-id="f1c87-204">If you do not have an Azure subscription, [sign up today](https://azure.microsoft.com/free/?b=16.48) for a free 30-day account and get $200 in Azure Credits to try out any combination of Azure services.</span></span>

#### <a name="microsoft-azure-cosmos-db-emulator-windows-containers-only"></a><span data-ttu-id="f1c87-205">Emulátor systému Cosmos DB Microsoft Azure (pouze Windows kontejnery)</span><span class="sxs-lookup"><span data-stu-id="f1c87-205">Microsoft Azure Cosmos DB Emulator (Windows Containers only)</span></span>

* [<span data-ttu-id="f1c87-206">Microsoft Azure Cosmos DB emulátoru Image na DockerHub</span><span class="sxs-lookup"><span data-stu-id="f1c87-206">Microsoft Azure Cosmos DB Emulator images on DockerHub</span></span>](https://hub.docker.com/r/microsoft/azure-cosmosdb-emulator) 

* [<span data-ttu-id="f1c87-207">Použití emulátoru DB Cosmos Azure pro místní vývoj a testování</span><span class="sxs-lookup"><span data-stu-id="f1c87-207">Use the Azure Cosmos DB Emulator for local development and testing</span></span>](/azure/cosmos-db/local-emulator#developing-with-the-emulator)

## <a name="exploring-the-rich-docker-development-ecosystem"></a><span data-ttu-id="f1c87-208">Zkoumání bohatý ekosystém vývoj Docker</span><span class="sxs-lookup"><span data-stu-id="f1c87-208">Exploring the rich Docker development ecosystem</span></span>

<span data-ttu-id="f1c87-209">Teď, když jste se naučili o Docker platformy a jiné imagí Dockeru, dalším krokem je prozkoumat bohatý ekosystém Docker.</span><span class="sxs-lookup"><span data-stu-id="f1c87-209">Now that you have learned about the Docker platform and different Docker images, the next step is to explore the rich Docker ecosystem.</span></span> <span data-ttu-id="f1c87-210">Následující odkazy vám ukážou, jak nástroje Microsoft doplňují vývoj kontejneru.</span><span class="sxs-lookup"><span data-stu-id="f1c87-210">The following links show you how the Microsoft tools complement container development.</span></span>

* [<span data-ttu-id="f1c87-211">Společně pomocí rozhraní .NET a Docker</span><span class="sxs-lookup"><span data-stu-id="f1c87-211">Using .NET and Docker together</span></span>](https://blogs.msdn.microsoft.com/dotnet/2017/05/25/using-net-and-docker-together/)
* [<span data-ttu-id="f1c87-212">Návrh a vývoj aplikace s více kontejneru a na základě Mikroslužbu .NET</span><span class="sxs-lookup"><span data-stu-id="f1c87-212">Designing and Developing Multi-Container and Microservice-Based .NET Applications</span></span>](../../standard/microservices-architecture/multi-container-microservice-net-applications/index.md)
* [<span data-ttu-id="f1c87-213">Rozšíření sady Visual Studio Code Docker</span><span class="sxs-lookup"><span data-stu-id="f1c87-213">Visual Studio Code Docker extension</span></span>](https://code.visualstudio.com/docs/languages/dockerfile)
* [<span data-ttu-id="f1c87-214">Naučte se používat Azure Service Fabric</span><span class="sxs-lookup"><span data-stu-id="f1c87-214">Learn how to use Azure Service Fabric</span></span>](/azure/service-fabric/index)
* [<span data-ttu-id="f1c87-215">Ukázka spuštění získávání Service Fabric</span><span class="sxs-lookup"><span data-stu-id="f1c87-215">Service Fabric Getting Started Sample</span></span>](https://azure.microsoft.com/resources/samples/service-fabric-dotnet-getting-started/)
* [<span data-ttu-id="f1c87-216">Výhody Windows kontejnery</span><span class="sxs-lookup"><span data-stu-id="f1c87-216">Benefits of Windows Containers</span></span>](/virtualization/windowscontainers/about/index#video-overview)
* [<span data-ttu-id="f1c87-217">Práce s nástroji Visual Studio Docker</span><span class="sxs-lookup"><span data-stu-id="f1c87-217">Working with Visual Studio Docker Tools</span></span>](/aspnet/core/host-and-deploy/docker/visual-studio-tools-for-docker)
* [<span data-ttu-id="f1c87-218">Nasazení bitových kopií Docker z registru kontejner Azure do Azure kontejner instancí</span><span class="sxs-lookup"><span data-stu-id="f1c87-218">Deploying Docker Images from the Azure Container Registry to Azure Container Instances</span></span>](https://blogs.msdn.microsoft.com/stevelasker/2017/07/28/deploying-docker-images-from-the-azure-container-registry-to-azure-container-instances/)
* [<span data-ttu-id="f1c87-219">Ladění pomocí kódu v sadě Visual Studio</span><span class="sxs-lookup"><span data-stu-id="f1c87-219">Debugging with Visual Studio Code</span></span>](https://code.visualstudio.com/docs/nodejs/debugging-recipes#_nodejs-typescript-docker-container)
* [<span data-ttu-id="f1c87-220">Načítání rukou pomocí sady Visual Studio pro Mac, kontejnery a bez serveru kódu v cloudu</span><span class="sxs-lookup"><span data-stu-id="f1c87-220">Getting hands on with Visual Studio for Mac, containers, and serverless code in the cloud</span></span>](https://blogs.msdn.microsoft.com/visualstudio/2017/08/31/hands-on-with-visual-studio-for-mac-containers-serverless-code-in-the-cloud/#comments)
* [<span data-ttu-id="f1c87-221">Začínáme s Docker a Visual Studio pro Mac testovacího prostředí</span><span class="sxs-lookup"><span data-stu-id="f1c87-221">Getting Started with Docker and Visual Studio for Mac Lab</span></span>](https://github.com/Microsoft/vs4mac-labs/tree/master/Docker/Getting-Started)

## <a name="next-steps"></a><span data-ttu-id="f1c87-222">Další kroky</span><span class="sxs-lookup"><span data-stu-id="f1c87-222">Next steps</span></span>

* [<span data-ttu-id="f1c87-223">Základy Dockeru s .NET Core</span><span class="sxs-lookup"><span data-stu-id="f1c87-223">Learn Docker Basics with .NET Core</span></span>](docker-basics-dotnet-core.md)
* [<span data-ttu-id="f1c87-224">Vytváření bitových kopií Docker .NET Core</span><span class="sxs-lookup"><span data-stu-id="f1c87-224">Building .NET Core Docker Images</span></span>](building-net-docker-images.md)
