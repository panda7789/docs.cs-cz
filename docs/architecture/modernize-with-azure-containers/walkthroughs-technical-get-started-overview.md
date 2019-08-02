---
title: Návody a přehled technických začátků
description: Modernizovat stávající aplikace .NET pomocí cloudu Azure a kontejnerů Windows | Návody a přehled technických informací Začínáme
ms.date: 04/28/2018
ms.openlocfilehash: 81f7d9fbf596a23b83e2dc9251788b33a8817e16
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "68676883"
---
# <a name="walkthroughs-and-technical-get-started-overview"></a><span data-ttu-id="91060-103">Návody a přehled technických začátků</span><span class="sxs-lookup"><span data-stu-id="91060-103">Walkthroughs and technical get started overview</span></span>

<span data-ttu-id="91060-104">Pokud chcete omezit velikost této elektronické knihy, měla by být v úložišti GitHubu dostupná další technická dokumentace a kompletní návody.</span><span class="sxs-lookup"><span data-stu-id="91060-104">To limit the size of this e-book, additional technical documentation and the full walkthroughs were made available in a GitHub repository.</span></span> <span data-ttu-id="91060-105">Online série návodů popsaných v této kapitole obsahuje podrobné nastavení více prostředí, která jsou založená na kontejnerech Windows, a nasazení do Azure.</span><span class="sxs-lookup"><span data-stu-id="91060-105">The online series of walkthroughs that is described in this chapter covers the step-by-step setup of the multiple environments that are based on Windows Containers, and deployment to Azure.</span></span>

<span data-ttu-id="91060-106">V následujících částech se dozvíte, co se týká každého návodu, jeho cíle a špičkového výhledu a poskytuje diagram úloh, které jsou součástí.</span><span class="sxs-lookup"><span data-stu-id="91060-106">The following sections explain what each walkthrough is about, its objectives and high-level vision, and provides a diagram of the tasks that are involved.</span></span> <span data-ttu-id="91060-107">Návody můžete získat sami na wikiwebu úložiště GitHub pro aplikace *eShopModernizing* na adrese <https://github.com/dotnet-architecture/eShopModernizing/wiki>.</span><span class="sxs-lookup"><span data-stu-id="91060-107">You can get the walkthroughs themselves in the *eShopModernizing* apps GitHub repo wiki at <https://github.com/dotnet-architecture/eShopModernizing/wiki>.</span></span>

## <a name="technical-walkthrough-list"></a><span data-ttu-id="91060-108">Seznam technických postupů</span><span class="sxs-lookup"><span data-stu-id="91060-108">Technical walkthrough list</span></span>

<span data-ttu-id="91060-109">Následující návody Začínáme poskytují konzistentní a komplexní technické pokyny pro ukázkové aplikace, které můžete nasazovat a Shift pomocí kontejnerů, a pak je přesunout pomocí několika možností nasazení v Azure.</span><span class="sxs-lookup"><span data-stu-id="91060-109">The following get-started walkthroughs provide consistent and comprehensive technical guidance for sample apps that you can lift and shift by using containers, and then move by using multiple deployment choices in Azure.</span></span>

<span data-ttu-id="91060-110">Každý z následujících návodů používá nové ukázkové aplikace eShopLegacy a eShopModernizing, které jsou dostupné na GitHubu na adrese <https://github.com/dotnet-architecture/eShopModernizing>.</span><span class="sxs-lookup"><span data-stu-id="91060-110">Each of the following walkthroughs uses the new sample eShopLegacy and eShopModernizing apps, which are available on GitHub at <https://github.com/dotnet-architecture/eShopModernizing>.</span></span>

- <span data-ttu-id="91060-111">**Prohlídka aplikací eShop Legacy (základní aplikace do modernizovat)**</span><span class="sxs-lookup"><span data-stu-id="91060-111">**Tour of eShop legacy apps (baseline apps to modernize)**</span></span>

- <span data-ttu-id="91060-112">**Kontejnerizace své stávající webové aplikace ASP.NET (WebForms & MVC) pomocí kontejnerů Windows**</span><span class="sxs-lookup"><span data-stu-id="91060-112">**Containerize your existing ASP.NET web apps (WebForms & MVC) with Windows Containers**</span></span>

- <span data-ttu-id="91060-113">**Kontejnerizace své stávající služby WCF (N-vrstvých aplikací) pomocí kontejnerů Windows**</span><span class="sxs-lookup"><span data-stu-id="91060-113">**Containerize your existing WCF services (N-Tier apps) with Windows Containers**</span></span>

- <span data-ttu-id="91060-114">**Nasazení aplikace založené na kontejnerech Windows do virtuálních počítačů Azure**</span><span class="sxs-lookup"><span data-stu-id="91060-114">**Deploy your Windows Containers-based app to Azure VMs**</span></span>

- <span data-ttu-id="91060-115">**Nasaďte aplikace založené na kontejnerech Windows do Kubernetes v Azure Container Service**</span><span class="sxs-lookup"><span data-stu-id="91060-115">**Deploy your Windows Containers-based apps to Kubernetes in Azure Container Service**</span></span>

## <a name="walkthrough-1-tour-of-eshop-legacy-apps"></a><span data-ttu-id="91060-116">Návod 1: Prohlídka starších verzí aplikací eShop</span><span class="sxs-lookup"><span data-stu-id="91060-116">Walkthrough 1: Tour of eShop legacy apps</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="91060-117">Dostupnost technického návodu</span><span class="sxs-lookup"><span data-stu-id="91060-117">Technical walkthrough availability</span></span>

<span data-ttu-id="91060-118">Úplný technický návod je k dispozici na wikiwebu eShopModernizing GitHub:</span><span class="sxs-lookup"><span data-stu-id="91060-118">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki:</span></span>

[<span data-ttu-id="91060-119">názorné postupy pro eShopModernizing wiki</span><span class="sxs-lookup"><span data-stu-id="91060-119">eShopModernizing wiki walkthroughs</span></span>](https://github.com/dotnet-architecture/eShopModernizing/wiki)

### <a name="overview"></a><span data-ttu-id="91060-120">Přehled</span><span class="sxs-lookup"><span data-stu-id="91060-120">Overview</span></span>

<span data-ttu-id="91060-121">V tomto návodu můžete prozkoumat počáteční implementaci tří ukázkových starších verzí aplikací.</span><span class="sxs-lookup"><span data-stu-id="91060-121">In this walkthrough, you can explore the initial implementation of three sample legacy applications.</span></span> <span data-ttu-id="91060-122">První dvě ukázkové webové aplikace mají architekturu monolitické a vytvořily se pomocí klasického ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="91060-122">The first two sample web apps have a monolithic architecture, and were created by using classic ASP.NET.</span></span> <span data-ttu-id="91060-123">Jedna aplikace je založena na ASP.NET 4. x MVC; Druhá aplikace je založena na webových formulářích ASP.NET 4. x.</span><span class="sxs-lookup"><span data-stu-id="91060-123">One application is based on ASP.NET 4.x MVC; the second application is based on ASP.NET 4.x Web Forms.</span></span>
<span data-ttu-id="91060-124">Třetí aplikace je 3 vrstva, která se skládá z aplikace typu klient-server a služby [Windows Communication Foundation (WCF)](../../framework/wcf/whats-wcf.md) na straně serveru.</span><span class="sxs-lookup"><span data-stu-id="91060-124">The third app is a 3-Tier app composed by a client WinForms app and a server-side [Windows Communication Foundation (WCF)](../../framework/wcf/whats-wcf.md) service.</span></span>

<span data-ttu-id="91060-125">Všechny tyto aplikace jsou dostupné v [úložišti GitHub eShopModernizing](https://github.com/dotnet-architecture/eShopModernizing).</span><span class="sxs-lookup"><span data-stu-id="91060-125">All these applications are available at the [eShopModernizing GitHub repo](https://github.com/dotnet-architecture/eShopModernizing).</span></span>

### <a name="goals"></a><span data-ttu-id="91060-126">Cíle</span><span class="sxs-lookup"><span data-stu-id="91060-126">Goals</span></span>

<span data-ttu-id="91060-127">Hlavním cílem tohoto návodu je jednoduše seznámit se s těmito aplikacemi a s jejich kódem a konfigurací.</span><span class="sxs-lookup"><span data-stu-id="91060-127">The main goal of this walkthrough is simply to get familiar with these apps, and with their code and configuration.</span></span> <span data-ttu-id="91060-128">Aplikace můžete nakonfigurovat tak, aby vygenerovaly a používaly přípravou data bez použití databáze SQL pro účely testování.</span><span class="sxs-lookup"><span data-stu-id="91060-128">You can configure the apps so that they generate and use mock data, without using the SQL database, for testing purposes.</span></span> <span data-ttu-id="91060-129">Tato volitelná konfigurace je založena na injektáže závislosti v odděleném způsobu.</span><span class="sxs-lookup"><span data-stu-id="91060-129">This optional config is based on dependency injection, in a decoupled way.</span></span>

### <a name="scenario-1-aspnet-web-apps"></a><span data-ttu-id="91060-130">Scénář 1: Webové aplikace v ASP.NET</span><span class="sxs-lookup"><span data-stu-id="91060-130">Scenario 1: ASP.NET Web apps</span></span>

<span data-ttu-id="91060-131">Následující obrázek ukazuje jednoduchý scénář původní starší verze ASP.NET webových aplikací.</span><span class="sxs-lookup"><span data-stu-id="91060-131">The figure below shows the simple scenario of the original legacy ASP.NET web applications.</span></span>

![Scénář jednoduché architektury pro původní starší verze webových aplikací v ASP.NET](./media/image5-1.png)

<span data-ttu-id="91060-133">V perspektivě obchodní domény obě aplikace nabízejí stejné funkce správy katalogu.</span><span class="sxs-lookup"><span data-stu-id="91060-133">From a business domain perspective, both apps offer the same catalog management features.</span></span> <span data-ttu-id="91060-134">Členové týmu eShop Enterprise by tuto aplikaci mohli používat k zobrazení a úpravám katalogu produktů.</span><span class="sxs-lookup"><span data-stu-id="91060-134">Members of the eShop enterprise team would use the app to view and edit the product catalog.</span></span>

<span data-ttu-id="91060-135">Následující obrázek ukazuje úvodní snímky obrazovky aplikace.</span><span class="sxs-lookup"><span data-stu-id="91060-135">The next figure shows the initial app screenshots.</span></span>

![Aplikace webových formulářů ASP.NET MVC a ASP.NET (existující/starší technologie)](./media/image5-2.png)

<span data-ttu-id="91060-137">Závislosti v ASP.NET 4. x nebo starších verzích (pro MVC nebo pro webové formuláře) znamenají, že tyto aplikace nebudou běžet v .NET Core, pokud není kód plně přepsaný pomocí ASP.NET Core MVC.</span><span class="sxs-lookup"><span data-stu-id="91060-137">Dependencies in ASP.NET 4.x or earlier versions (either for MVC or for Web Forms) means that these applications won’t run on .NET Core unless the code is fully rewritten by using ASP.NET Core MVC.</span></span>

### <a name="scenario-2-wcf-service-and-winforms-client-app-3-tier-app"></a><span data-ttu-id="91060-138">Scénář 2: Klientská aplikace služby WCF a WinForms (aplikace na úrovni 3)</span><span class="sxs-lookup"><span data-stu-id="91060-138">Scenario 2: WCF service and WinForms client app (3-Tier app)</span></span>

<span data-ttu-id="91060-139">Následující obrázek ukazuje jednoduchý scénář původní starší verze aplikace 3 vrstvy.</span><span class="sxs-lookup"><span data-stu-id="91060-139">The figure below shows the simple scenario of the original 3-Tier legacy application.</span></span>

![Scénář jednoduché architektury původní starší verze aplikace na 3 vrstvě se službou WCF a klientskou aplikací WinForms](./media/image5-1.5.png)

### <a name="benefits"></a><span data-ttu-id="91060-141">Výhody</span><span class="sxs-lookup"><span data-stu-id="91060-141">Benefits</span></span>

<span data-ttu-id="91060-142">Výhody tohoto návodu jsou jednoduché: Stačí, abyste obeznámeni s kódem a počátečními aplikacemi.</span><span class="sxs-lookup"><span data-stu-id="91060-142">The benefits of this walkthrough are simple: Just get familiar with the code and initial apps.</span></span>

### <a name="next-steps"></a><span data-ttu-id="91060-143">Další kroky</span><span class="sxs-lookup"><span data-stu-id="91060-143">Next steps</span></span>

<span data-ttu-id="91060-144">Podrobnější zkoumání tohoto obsahu najdete na wikiwebu GitHub:</span><span class="sxs-lookup"><span data-stu-id="91060-144">Explore this content more in-depth on the GitHub wiki:</span></span>

- [<span data-ttu-id="91060-145">Projděte si základní aplikace ASP.NET MVC a webové formuláře "starší".</span><span class="sxs-lookup"><span data-stu-id="91060-145">Tour on the baseline ASP.NET MVC and Web Forms “legacy” apps</span></span>](https://github.com/dotnet-architecture/eShopModernizing/wiki/01.-Tour-on-the-ASP.NET-MVC-and-WebForms-apps-implementation-code)
- [<span data-ttu-id="91060-146">Prohlídku na základní úrovni služby WCF a WinForms (3 vrstvy) "starší" aplikace</span><span class="sxs-lookup"><span data-stu-id="91060-146">Tour on the baseline WCF service and WinForms (3-Tier) “legacy” app</span></span>](https://github.com/dotnet-architecture/eShopModernizing/wiki/21.-Tour-on-the-WCF-service-and-WinForms-apps)

## <a name="walkthrough-2-containerize-your-existing-net-applications-with-windows-containers"></a><span data-ttu-id="91060-147">Návod 2: Kontejnerizace své stávající aplikace .NET pomocí kontejnerů Windows</span><span class="sxs-lookup"><span data-stu-id="91060-147">Walkthrough 2: Containerize your existing .NET applications with Windows Containers</span></span>

### <a name="overview"></a><span data-ttu-id="91060-148">Přehled</span><span class="sxs-lookup"><span data-stu-id="91060-148">Overview</span></span>

<span data-ttu-id="91060-149">Pomocí kontejnerů Windows můžete zlepšit nasazení stávajících aplikací .NET, jako jsou ty, které jsou založené na MVC, webových formulářích nebo WCF, do produkčních, vývojových a testovacích prostředí.</span><span class="sxs-lookup"><span data-stu-id="91060-149">Use Windows Containers to improve deployment of existing .NET applications, like those based on MVC, Web Forms, or WCF, to production, development, and test environments.</span></span>

### <a name="goals"></a><span data-ttu-id="91060-150">Cíle</span><span class="sxs-lookup"><span data-stu-id="91060-150">Goals</span></span>

<span data-ttu-id="91060-151">Cílem tohoto návodu je zobrazit několik možností pro uzavření existující aplikace .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="91060-151">The goal of this walkthrough is to show you several options for containerizing an existing .NET Framework application.</span></span> <span data-ttu-id="91060-152">Můžete:</span><span class="sxs-lookup"><span data-stu-id="91060-152">You can:</span></span>

- <span data-ttu-id="91060-153">Kontejnerizace aplikaci pomocí [nástrojů sady Visual studio 2017 pro Docker](/aspnet/core/host-and-deploy/docker/visual-studio-tools-for-docker) (visual Studio 2017 nebo novější verze).</span><span class="sxs-lookup"><span data-stu-id="91060-153">Containerize your application by using [Visual Studio 2017 Tools for Docker](/aspnet/core/host-and-deploy/docker/visual-studio-tools-for-docker) (Visual Studio 2017 or later versions).</span></span>

- <span data-ttu-id="91060-154">Kontejnerizace aplikaci ručním přidáním [souboru Dockerfile](https://docs.docker.com/engine/reference/builder/)a pak pomocí [Docker CLI](https://docs.docker.com/engine/reference/commandline/cli/).</span><span class="sxs-lookup"><span data-stu-id="91060-154">Containerize your application by manually adding a [Dockerfile](https://docs.docker.com/engine/reference/builder/), and then using the [Docker CLI](https://docs.docker.com/engine/reference/commandline/cli/).</span></span>

- <span data-ttu-id="91060-155">Kontejnerizace aplikaci pomocí nástroje [Img2Docker](https://github.com/docker/communitytools-image2docker-win) (Open source nástroj z Docker).</span><span class="sxs-lookup"><span data-stu-id="91060-155">Containerize your application by using the [Img2Docker](https://github.com/docker/communitytools-image2docker-win) tool (an open-source tool from Docker).</span></span>

<span data-ttu-id="91060-156">Tento názorný postup se zaměřuje na nástroje sady Visual Studio 2017 pro přístup k Docker, ale ostatní dva přístupy jsou v souvislosti s používáním fázemi poměrně podobné.</span><span class="sxs-lookup"><span data-stu-id="91060-156">This walkthrough focuses on the Visual Studio 2017 Tools for Docker approach, but the other two approaches are fairly similar in regard to using Dockerfiles.</span></span>

### <a name="scenario-1-containerized-aspnet-web-apps"></a><span data-ttu-id="91060-157">Scénář 1: ASP.NET webové aplikace v kontejneru</span><span class="sxs-lookup"><span data-stu-id="91060-157">Scenario 1: Containerized ASP.NET web apps</span></span>

<span data-ttu-id="91060-158">Obrázek níže ukazuje scénář pro kontejnerové aplikace eShop starší verze webových aplikací.</span><span class="sxs-lookup"><span data-stu-id="91060-158">Figure below shows the scenario for containerized eShop legacy web apps applications.</span></span>

![Zjednodušený diagram architektury kontejnerových aplikací ASP.NET ve vývojovém prostředí](./media/image5-3.png)

### <a name="scenario-2-containerized-wcf-service"></a><span data-ttu-id="91060-160">Scénář 2: Kontejnerová služba WCF</span><span class="sxs-lookup"><span data-stu-id="91060-160">Scenario 2: Containerized WCF service</span></span>

<span data-ttu-id="91060-161">Obrázek níže ukazuje scénář pro aplikaci se třemi úrovněmi s kontejnerovou službou WCF.</span><span class="sxs-lookup"><span data-stu-id="91060-161">Figure below shows the scenario for a 3-Tier app with a containerized WCF service.</span></span>

![Zjednodušený diagram architektury kontejnerové služby WCF ve vývojovém prostředí](./media/image5-3.5.png)

### <a name="benefits"></a><span data-ttu-id="91060-163">Výhody</span><span class="sxs-lookup"><span data-stu-id="91060-163">Benefits</span></span>

<span data-ttu-id="91060-164">Existují výhody spuštění aplikace v monolitické v kontejneru.</span><span class="sxs-lookup"><span data-stu-id="91060-164">There are advantages to running your monolithic application in a container.</span></span> <span data-ttu-id="91060-165">Nejprve vytvoříte obrázek pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="91060-165">First, you create an image for the application.</span></span> <span data-ttu-id="91060-166">Od tohoto okamžiku se každé nasazení spouští ve stejném prostředí.</span><span class="sxs-lookup"><span data-stu-id="91060-166">From that point on, every deployment runs in the same environment.</span></span> <span data-ttu-id="91060-167">Každý kontejner používá stejnou verzi operačního systému, má nainstalovanou stejnou verzi závislostí, používá stejnou verzi rozhraní .NET Framework a je vytvořen pomocí stejného procesu.</span><span class="sxs-lookup"><span data-stu-id="91060-167">Every container uses the same OS version, has the same version of dependencies installed, uses the same .NET framework version, and is built by using the same process.</span></span> <span data-ttu-id="91060-168">V podstatě budete řídit závislosti aplikace pomocí Image Docker.</span><span class="sxs-lookup"><span data-stu-id="91060-168">Basically, you control the dependencies of your application by using a Docker image.</span></span> <span data-ttu-id="91060-169">Závislosti při nasazení kontejnerů cestují k aplikaci.</span><span class="sxs-lookup"><span data-stu-id="91060-169">The dependencies travel with the application when you deploy the containers.</span></span>

<span data-ttu-id="91060-170">Další výhodou je, že vývojáři můžou aplikaci spouštět v konzistentním prostředí, které poskytuje kontejnery Windows.</span><span class="sxs-lookup"><span data-stu-id="91060-170">An additional benefit is that developers can run the application in the consistent environment that's provided by Windows Containers.</span></span> <span data-ttu-id="91060-171">Problémy, které se objeví jenom s určitými verzemi, můžou být hned Spotted místo zpřístupnění v pracovním nebo produkčním prostředí.</span><span class="sxs-lookup"><span data-stu-id="91060-171">Issues that appear only with certain versions can be spotted immediately, instead of surfacing in a staging or production environment.</span></span> <span data-ttu-id="91060-172">Rozdíly ve vývojových prostředích, která používají členové vývojového týmu, se týkají méně, když aplikace běží v kontejnerech.</span><span class="sxs-lookup"><span data-stu-id="91060-172">Differences in development environments used by members of the development team matter less when applications run in containers.</span></span>

<span data-ttu-id="91060-173">Kontejnerové aplikace mají také plošší křivku škálování na více instancí.</span><span class="sxs-lookup"><span data-stu-id="91060-173">Containerized applications also have a flatter scale-out curve.</span></span> <span data-ttu-id="91060-174">Aplikace s využitím kontejnerů umožňují mít více instancí aplikací a služeb (na základě kontejnerů) ve VIRTUÁLNÍm počítači nebo fyzickém počítači v porovnání s běžnými nasazeními aplikací na počítač.</span><span class="sxs-lookup"><span data-stu-id="91060-174">Containerized apps enable you to have more application and service instances (based on containers) in a VM or physical machine compared to regular application deployments per machine.</span></span> <span data-ttu-id="91060-175">To se týká vyšší hustoty a menšího počtu požadovaných prostředků, zejména při použití orchestrací, jako je Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="91060-175">This translates to higher density and fewer required resources, especially when you use orchestrators like Kubernetes.</span></span>

<span data-ttu-id="91060-176">V ideálních situacích není nutné dělat žádné změny kódu aplikace (C\#).</span><span class="sxs-lookup"><span data-stu-id="91060-176">Containerization, in ideal situations, does not require making any changes to the application code (C\#).</span></span> <span data-ttu-id="91060-177">Ve většině scénářů potřebujete jenom soubory metadat nasazení Docker (fázemi a soubory Docker Compose).</span><span class="sxs-lookup"><span data-stu-id="91060-177">In most scenarios, you just need the Docker deployment metadata files (Dockerfiles and Docker Compose files).</span></span>

### <a name="next-steps"></a><span data-ttu-id="91060-178">Další postup</span><span class="sxs-lookup"><span data-stu-id="91060-178">Next steps</span></span>

<span data-ttu-id="91060-179">Podrobnější zkoumání tohoto obsahu najdete na wikiwebu GitHub:</span><span class="sxs-lookup"><span data-stu-id="91060-179">Explore this content more in-depth on the GitHub wiki:</span></span>

- [<span data-ttu-id="91060-180">Jak kontejnerizace .NET Framework webové aplikace pomocí kontejnerů Windows a Docker</span><span class="sxs-lookup"><span data-stu-id="91060-180">How to containerize the .NET Framework web apps with Windows Containers and Docker</span></span>](https://github.com/dotnet-architecture/eShopModernizing/wiki/02.-How-to-containerize-the-.NET-Framework-web-apps-with-Windows-Containers-and-Docker)
- [<span data-ttu-id="91060-181">Přidání podpory Docker do služby WCF</span><span class="sxs-lookup"><span data-stu-id="91060-181">Adding Docker Support to a WCF service</span></span>](https://github.com/dotnet-architecture/eShopModernizing/wiki/22.-Adding-Docker-Support)

## <a name="walkthrough-3-deploy-your-windows-containers-based-app-to-azure-vms"></a><span data-ttu-id="91060-182">Návod 3: Nasazení aplikace založené na kontejnerech Windows do virtuálních počítačů Azure</span><span class="sxs-lookup"><span data-stu-id="91060-182">Walkthrough 3: Deploy your Windows Containers-based app to Azure VMs</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="91060-183">Dostupnost technického návodu</span><span class="sxs-lookup"><span data-stu-id="91060-183">Technical walkthrough availability</span></span>

<span data-ttu-id="91060-184">Úplný technický návod je k dispozici na wikiwebu eShopModernizing GitHub:<https://github.com/dotnet-architecture/eShopModernizing/wiki/06.-Deploying-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD)></span><span class="sxs-lookup"><span data-stu-id="91060-184">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki: <https://github.com/dotnet-architecture/eShopModernizing/wiki/06.-Deploying-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD)></span></span>

### <a name="overview"></a><span data-ttu-id="91060-185">Přehled</span><span class="sxs-lookup"><span data-stu-id="91060-185">Overview</span></span>

<span data-ttu-id="91060-186">Nasazení na hostitele Docker na virtuálním počítači s Windows serverem 2016 (VM) v Azure umožňuje rychle nastavit vývojové a testovací a přípravná prostředí.</span><span class="sxs-lookup"><span data-stu-id="91060-186">Deploying to a Docker host on a Windows Server 2016 Virtual Machine (VM) in Azure lets you quickly set up development/test/staging environments.</span></span> <span data-ttu-id="91060-187">Poskytuje také běžné místo pro testery nebo obchodní uživatele k ověření aplikace.</span><span class="sxs-lookup"><span data-stu-id="91060-187">It also gives you a common place for testers or business users to validate the app.</span></span> <span data-ttu-id="91060-188">Virtuální počítače můžou být taky platná provozní prostředí infrastruktury jako služby (IaaS).</span><span class="sxs-lookup"><span data-stu-id="91060-188">VMs also can be valid Infrastructure as a Service (IaaS) production environments.</span></span>

### <a name="goals"></a><span data-ttu-id="91060-189">Cíle</span><span class="sxs-lookup"><span data-stu-id="91060-189">Goals</span></span>

<span data-ttu-id="91060-190">Cílem tohoto návodu je ukázat vám několik alternativ, které máte, když nasadíte kontejnery Windows do virtuálních počítačů Azure, které jsou založené na Windows serveru 2016 nebo novějších verzích.</span><span class="sxs-lookup"><span data-stu-id="91060-190">The goal of this walkthrough is to show you the multiple alternatives you have when you deploy Windows Containers to Azure VMs that are based on Windows Server 2016 or later versions.</span></span>

### <a name="scenarios"></a><span data-ttu-id="91060-191">Scénáře</span><span class="sxs-lookup"><span data-stu-id="91060-191">Scenarios</span></span>

<span data-ttu-id="91060-192">V tomto návodu se zabývá několik scénářů.</span><span class="sxs-lookup"><span data-stu-id="91060-192">Several scenarios are covered in this walkthrough.</span></span>

#### <a name="scenario-a-deploy-to-an-azure-vm-from-a-dev-pc-through-docker-engine-connection"></a><span data-ttu-id="91060-193">Scénář A: Nasazení na virtuální počítač Azure z vývojového počítače prostřednictvím připojení k Docker Engine</span><span class="sxs-lookup"><span data-stu-id="91060-193">Scenario A: Deploy to an Azure VM from a dev PC through Docker Engine connection</span></span>

![Nasazení na virtuální počítač Azure z vývojového počítače prostřednictvím připojení k dokovacímu modulu](./media/image5-4.png)

<span data-ttu-id="91060-195">**Obrázek 5-4.**</span><span class="sxs-lookup"><span data-stu-id="91060-195">**Figure 5-4.**</span></span> <span data-ttu-id="91060-196">Nasazení na virtuální počítač Azure z vývojového počítače prostřednictvím připojení k dokovacímu modulu</span><span class="sxs-lookup"><span data-stu-id="91060-196">Deploy to an Azure VM from a dev PC through a Docker Engine connection</span></span>

#### <a name="scenario-b-deploy-to-an-azure-vm-through-a-docker-registry"></a><span data-ttu-id="91060-197">Scénář B: Nasazení na virtuální počítač Azure prostřednictvím registru Docker</span><span class="sxs-lookup"><span data-stu-id="91060-197">Scenario B: Deploy to an Azure VM through a Docker Registry</span></span>

![Nasazení na virtuální počítač Azure prostřednictvím registru Docker](./media/image5-5.png)

<span data-ttu-id="91060-199">**Obrázek 5-5.**</span><span class="sxs-lookup"><span data-stu-id="91060-199">**Figure 5-5.**</span></span> <span data-ttu-id="91060-200">Nasazení na virtuální počítač Azure prostřednictvím registru Docker</span><span class="sxs-lookup"><span data-stu-id="91060-200">Deploy to an Azure VM through a Docker Registry</span></span>

#### <a name="scenario-c-deploy-to-an-azure-vm-from-cicd-pipelines-in-azure-devops-services"></a><span data-ttu-id="91060-201">Scénář C: Nasazení na virtuální počítač Azure z kanálů CI/CD v Azure DevOps Services</span><span class="sxs-lookup"><span data-stu-id="91060-201">Scenario C: Deploy to an Azure VM from CI/CD pipelines in Azure DevOps Services</span></span>

![Nasazení na virtuální počítač Azure z kanálů CI/CD v Azure DevOps Services](./media/image5-6.png)

<span data-ttu-id="91060-203">**Obrázek 5-6.**</span><span class="sxs-lookup"><span data-stu-id="91060-203">**Figure 5-6.**</span></span> <span data-ttu-id="91060-204">Nasazení na virtuální počítač Azure z kanálů CI/CD v Azure DevOps Services</span><span class="sxs-lookup"><span data-stu-id="91060-204">Deploy to an Azure VM from CI/CD pipelines in Azure DevOps Services</span></span>

### <a name="azure-vms-for-windows-containers"></a><span data-ttu-id="91060-205">Virtuální počítače Azure pro kontejnery Windows</span><span class="sxs-lookup"><span data-stu-id="91060-205">Azure VMs for Windows Containers</span></span>

<span data-ttu-id="91060-206">Virtuální počítače Azure pro kontejnery Windows jsou virtuální počítače založené na Windows serveru 2016, Windows 10 nebo novějších verzích s nastavením modulu Docker.</span><span class="sxs-lookup"><span data-stu-id="91060-206">Azure VMs for Windows Containers are VMs based on Windows Server 2016, Windows 10, or later versions, both with Docker Engine set up.</span></span> <span data-ttu-id="91060-207">Ve většině případů se Windows Server 2016 používá ve virtuálních počítačích Azure.</span><span class="sxs-lookup"><span data-stu-id="91060-207">In most cases, Windows Server 2016 is used in the Azure VMs.</span></span>

<span data-ttu-id="91060-208">Azure v současné době poskytuje virtuálnímu počítači s názvem **Windows Server 2016 s kontejnery**.</span><span class="sxs-lookup"><span data-stu-id="91060-208">Azure currently provides a VM named **Windows Server 2016 with Containers**.</span></span> <span data-ttu-id="91060-209">Tento virtuální počítač můžete použít k tomu, abyste si vyzkoušeli novou funkci kontejneru Windows serveru, a to buď s Windows serverem Core, nebo Windows nano serverem.</span><span class="sxs-lookup"><span data-stu-id="91060-209">You can use this VM to try the new Windows Server Container feature, with either Windows Server Core or Windows Nano Server.</span></span> <span data-ttu-id="91060-210">Nainstalují se image operačních systémů kontejnerů a pak je virtuální počítač připravený k použití s Docker.</span><span class="sxs-lookup"><span data-stu-id="91060-210">Container OS images are installed, and then the VM is ready to use with Docker.</span></span>

### <a name="benefits"></a><span data-ttu-id="91060-211">Výhody</span><span class="sxs-lookup"><span data-stu-id="91060-211">Benefits</span></span>

<span data-ttu-id="91060-212">I když se kontejnery Windows dají nasadit na místní virtuální počítače s Windows serverem 2016 při nasazení do Azure, získáte snadnější způsob, jak začít s připravenými virtuálními počítači kontejnerů Windows serveru.</span><span class="sxs-lookup"><span data-stu-id="91060-212">Although Windows Containers can be deployed to on-premises Windows Server 2016 VMs, when you deploy to Azure, you get an easier way to get started, with ready-to-use Windows Server Container VMs.</span></span> <span data-ttu-id="91060-213">Získáte také běžné online umístění, které je dostupné pro testery a automatickou škálovatelnost prostřednictvím Azure Virtual Machine Scale Sets.</span><span class="sxs-lookup"><span data-stu-id="91060-213">You also get a common online location that’s accessible to testers, and automatic scalability through Azure virtual machine scale sets.</span></span>

### <a name="next-steps"></a><span data-ttu-id="91060-214">Další kroky</span><span class="sxs-lookup"><span data-stu-id="91060-214">Next steps</span></span>

<span data-ttu-id="91060-215">Podrobnější zkoumání tohoto obsahu najdete na wikiwebu GitHub:</span><span class="sxs-lookup"><span data-stu-id="91060-215">Explore this content more in-depth on the GitHub wiki:</span></span>

<https://github.com/dotnet-architecture/eShopModernizing/wiki/06.-Deploying-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD)>

## <a name="walkthrough-4-deploy-your-windows-containers-based-apps-to-azure-container-instances-aci"></a><span data-ttu-id="91060-216">Návod 4: Nasazení aplikací založených na kontejnerech Windows do Azure Container Instances (ACI)</span><span class="sxs-lookup"><span data-stu-id="91060-216">Walkthrough 4: Deploy your Windows Containers-based apps to Azure Container Instances (ACI)</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="91060-217">Dostupnost technického návodu</span><span class="sxs-lookup"><span data-stu-id="91060-217">Technical walkthrough availability</span></span>

<span data-ttu-id="91060-218">Úplný technický návod je k dispozici na wikiwebu eShopModernizing GitHub:</span><span class="sxs-lookup"><span data-stu-id="91060-218">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki:</span></span>

<span data-ttu-id="91060-219">[Nasazení aplikací do ACI (Azure Container Instances)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances))</span><span class="sxs-lookup"><span data-stu-id="91060-219">[Deploying the Apps to ACI (Azure Container Instances)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances))</span></span>

### <a name="overview"></a><span data-ttu-id="91060-220">Přehled</span><span class="sxs-lookup"><span data-stu-id="91060-220">Overview</span></span>

<span data-ttu-id="91060-221">[Azure Container Instances (ACI)](https://docs.microsoft.com/azure/container-instances/) je nejrychlejší způsob, jak mít kontejnery pro vývoj/testování a přípravu, kde můžete nasazovat jednotlivé instance kontejnerů.</span><span class="sxs-lookup"><span data-stu-id="91060-221">[Azure Container Instances (ACI)](https://docs.microsoft.com/azure/container-instances/) is the quickest way to have a Containers dev/test/staging environment where you can deploy single instances of containers.</span></span>

### <a name="goals"></a><span data-ttu-id="91060-222">Cíle</span><span class="sxs-lookup"><span data-stu-id="91060-222">Goals</span></span>

<span data-ttu-id="91060-223">V tomto návodu se dozvíte o hlavních scénářích při nasazování kontejnerů Windows do Azure Container Instances (ACI) a o tom, jak můžete nasadit eShopModernizing aplikace do ACI.</span><span class="sxs-lookup"><span data-stu-id="91060-223">This walkthrough shows you the main scenarios when deploying Windows Containers to Azure Container Instances (ACI) and how you can deploy eShopModernizing Apps into ACI.</span></span>

### <a name="scenarios"></a><span data-ttu-id="91060-224">Scénáře</span><span class="sxs-lookup"><span data-stu-id="91060-224">Scenarios</span></span>

<span data-ttu-id="91060-225">Existují varianty, jak nasadit aplikace eShopModernizing do ACI, jako je nasazení pouze jedné nebo všech aplikací (aplikace MVC, aplikace WebForm nebo služba WCF).</span><span class="sxs-lookup"><span data-stu-id="91060-225">There can be variations about deploying the eShopModernizing apps into ACI such as deploying just one or all of the apps (MVC app, WebForms app or WCF service).</span></span> <span data-ttu-id="91060-226">V níže uvedeném scénáři vidíte aplikaci ASP.NET MVC a kontejner SQL Server, jak jsou nasazeny jako kontejnery do ACI (Azure Container Instances).</span><span class="sxs-lookup"><span data-stu-id="91060-226">In the following scenario shown below you can see the ASP.NET MVC app plus the SQL Server container both of them deployed as containers into ACI (Azure Container Instances).</span></span>

![Nasazení na ACI z vývojového prostředí](./media/image5-3.5.6.png)

### <a name="benefits"></a><span data-ttu-id="91060-228">Výhody</span><span class="sxs-lookup"><span data-stu-id="91060-228">Benefits</span></span>

<span data-ttu-id="91060-229">Azure Container Instances usnadňuje vytváření a správu kontejnerů Docker v Azure, aniž byste museli zřizovat virtuální počítače nebo přidělovat službu vyšší úrovně.</span><span class="sxs-lookup"><span data-stu-id="91060-229">Azure Container Instances makes it easy to create and manage Docker containers in Azure, without having to provision virtual machines or adopt a higher-level service.</span></span> <span data-ttu-id="91060-230">Pomocí ACI můžete přímo nasadit kontejner Windows v Azure a zveřejnit ho na internetu s plně kvalifikovaným názvem domény (FQDN) v řádu sekund (za předpokladu, že máte připravenou image kontejneru Windows v registru Docker, jako je Docker Hub nebo Azure Container. Registr).</span><span class="sxs-lookup"><span data-stu-id="91060-230">With ACI, you can directly deploy a Windows container in Azure and expose it to the internet with a fully qualified domain name (FQDN) in a matter of seconds (Provided that you have the Windows Container image ready in a Docker registry like Docker Hub or Azure Container Registry).</span></span>

### <a name="considerations"></a><span data-ttu-id="91060-231">Požadavky</span><span class="sxs-lookup"><span data-stu-id="91060-231">Considerations</span></span>

<span data-ttu-id="91060-232">Nasazení kontejnerů Windows s úplnými .NET Framework/ASP.NET nebo SQL Server do Azure Container Instances (ACI) není poměrně stejně rychlé jako nasazení na obvyklého hostitele Docker (jako Windows Server 2016 s kontejnery Windows), protože image Docker musí být stažení (z registru Docker) pokaždé a velikosti image kontejneru SQL (15,1 GB) a image kontejneru ASP.NET (13,9 GB) jsou výrazně velké, ale je mnohem levnější než udržování vlastního hostitele Docker (trvale online). Windows Server 2016 s virtuálními počítači kontejnerů Windows v Azure – nezmiňujte si celý Orchestrator jako Kubernetes v Azure (AKS), který je na druhé straně skvělým výběrem pro produkční nasazení.</span><span class="sxs-lookup"><span data-stu-id="91060-232">Deploying Windows Containers with either full .NET Framework / ASP.NET or SQL Server into Azure Container Instances (ACI) is not quite as fast as deploying to a regular Docker Host (like a Windows Server 2016 with Windows Containers) because the Docker image has to be downloaded (pulled from the Docker registry) every time and the sizes of the SQL container image (15.1 GB) and the ASP.NET container image (13.9 GB) are significantly large, however it is much cheaper than maintaining your own docker host (permanently on-line Windows Server 2016 with Windows Containers VM in Azure) not to mention a whole orchestrator like Kubernetes in Azure (AKS) which is, on the other hand, a great choice for production deployments.</span></span>

<span data-ttu-id="91060-233">Hlavním závěrem je použití Azure Container Instances velmi přesvědčivou možností pro scénáře vývoje a testování a pro kanály CI/CD.</span><span class="sxs-lookup"><span data-stu-id="91060-233">As main conclusion, using Azure Container Instances is a very compelling option for Dev/Test scenarios and for CI/CD pipelines.</span></span>

## <a name="next-steps"></a><span data-ttu-id="91060-234">Další postup</span><span class="sxs-lookup"><span data-stu-id="91060-234">Next steps</span></span>

<span data-ttu-id="91060-235">Podrobnější zkoumání tohoto obsahu najdete na wikiwebu GitHub:</span><span class="sxs-lookup"><span data-stu-id="91060-235">Explore this content more in-depth on the GitHub wiki:</span></span>

[https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances))

## <a name="walkthrough-5-deploy-your-windows-containers-based-apps-to-kubernetes-in-azure-container-service"></a><span data-ttu-id="91060-236">Návod 5: Nasaďte aplikace založené na kontejnerech Windows do Kubernetes v Azure Container Service</span><span class="sxs-lookup"><span data-stu-id="91060-236">Walkthrough 5: Deploy your Windows Containers-based apps to Kubernetes in Azure Container Service</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="91060-237">Dostupnost technického návodu</span><span class="sxs-lookup"><span data-stu-id="91060-237">Technical walkthrough availability</span></span>

<span data-ttu-id="91060-238">Úplný technický návod je k dispozici na wikiwebu eShopModernizing GitHub:</span><span class="sxs-lookup"><span data-stu-id="91060-238">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki:</span></span>

<https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-CI-CD)>

### <a name="overview"></a><span data-ttu-id="91060-239">Přehled</span><span class="sxs-lookup"><span data-stu-id="91060-239">Overview</span></span>

<span data-ttu-id="91060-240">Aplikace, která je založená na kontejnerech Windows, bude rychle potřebovat používání platforem, takže se ještě od virtuálních počítačů s IaaS přesouvá ještě dál.</span><span class="sxs-lookup"><span data-stu-id="91060-240">An application that's based on Windows Containers will quickly need to use platforms, moving even further away from IaaS VMs.</span></span> <span data-ttu-id="91060-241">To je nutné, aby bylo možné snadno dosáhnout vysoké škálovatelnosti a lepšího automatizované škálovatelnosti a významně zlepšovat automatizované nasazení a správu verzí.</span><span class="sxs-lookup"><span data-stu-id="91060-241">This is needed to easily achieve high scalability and better automated scalability, and for a significant improvement in automated deployments and versioning.</span></span> <span data-ttu-id="91060-242">Tyto cíle můžete dosáhnout pomocí nástroje Orchestrator [Kubernetes](https://kubernetes.io/), který je k dispozici ve [službě Azure Container Services](https://azure.microsoft.com/services/container-service/).</span><span class="sxs-lookup"><span data-stu-id="91060-242">You can achieve these goals by using the orchestrator [Kubernetes](https://kubernetes.io/), available in [Azure Container Services](https://azure.microsoft.com/services/container-service/).</span></span>

### <a name="goals"></a><span data-ttu-id="91060-243">Cíle</span><span class="sxs-lookup"><span data-stu-id="91060-243">Goals</span></span>

<span data-ttu-id="91060-244">Cílem tohoto návodu je zjistit, jak nasadit aplikaci založenou na kontejnerech Windows do Kubernetes (označované také jako *K8s*) v Azure Container Service.</span><span class="sxs-lookup"><span data-stu-id="91060-244">The goal of this walkthrough is to learn how to deploy a Windows Container–based application to Kubernetes (also called *K8s*) in Azure Container Service.</span></span> <span data-ttu-id="91060-245">Nasazení na Kubernetes od začátku je proces se dvěma kroky:</span><span class="sxs-lookup"><span data-stu-id="91060-245">Deploying to Kubernetes from scratch is a two-step process:</span></span>

1. <span data-ttu-id="91060-246">Nasaďte cluster Kubernetes do Azure Container Service.</span><span class="sxs-lookup"><span data-stu-id="91060-246">Deploy a Kubernetes cluster to Azure Container Service.</span></span>

2. <span data-ttu-id="91060-247">Nasaďte aplikaci a související prostředky do clusteru Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="91060-247">Deploy the application and related resources to the Kubernetes cluster.</span></span>

### <a name="scenarios"></a><span data-ttu-id="91060-248">Scénáře</span><span class="sxs-lookup"><span data-stu-id="91060-248">Scenarios</span></span>

#### <a name="scenario-a-deploy-directly-to-a-kubernetes-cluster-from-a-dev-environment"></a><span data-ttu-id="91060-249">Scénář A: Nasazení přímo do clusteru Kubernetes z vývojového prostředí</span><span class="sxs-lookup"><span data-stu-id="91060-249">Scenario A: Deploy directly to a Kubernetes cluster from a dev environment</span></span>

![Nasazení přímo do clusteru Kubernetes z vývojového prostředí](./media/image5-7.png)

<span data-ttu-id="91060-251">**Obrázek 5-7.**</span><span class="sxs-lookup"><span data-stu-id="91060-251">**Figure 5-7.**</span></span> <span data-ttu-id="91060-252">Nasazení přímo do clusteru Kubernetes z vývojového prostředí</span><span class="sxs-lookup"><span data-stu-id="91060-252">Deploy directly to a Kubernetes cluster from a development environment</span></span>

#### <a name="scenario-b-deploy-to-a-kubernetes-cluster-from-cicd-pipelines-in-azure-devops-services"></a><span data-ttu-id="91060-253">Scénář B: Nasazení do clusteru Kubernetes z kanálů CI/CD v Azure DevOps Services</span><span class="sxs-lookup"><span data-stu-id="91060-253">Scenario B: Deploy to a Kubernetes cluster from CI/CD pipelines in Azure DevOps Services</span></span>

![Nasazení do clusteru Kubernetes z kanálů CI/CD v Azure DevOps Services](./media/image5-8.png)

<span data-ttu-id="91060-255">**Obrázek 5-8.**</span><span class="sxs-lookup"><span data-stu-id="91060-255">**Figure 5-8.**</span></span> <span data-ttu-id="91060-256">Nasazení do clusteru Kubernetes z kanálů CI/CD v Azure DevOps Services</span><span class="sxs-lookup"><span data-stu-id="91060-256">Deploy to a Kubernetes cluster from CI/CD pipelines in Azure DevOps Services</span></span>

### <a name="benefits"></a><span data-ttu-id="91060-257">Výhody</span><span class="sxs-lookup"><span data-stu-id="91060-257">Benefits</span></span>

<span data-ttu-id="91060-258">Nasazení do clusteru v Kubernetes přináší spoustu výhod.</span><span class="sxs-lookup"><span data-stu-id="91060-258">There are many benefits to deploying to a cluster in Kubernetes.</span></span> <span data-ttu-id="91060-259">Největší výhodou je, že získáte prostředí připravené pro produkční prostředí, ve kterém můžete škálovat aplikaci na základě počtu instancí kontejnerů, které chcete použít (vnitřní škálovatelnost ve stávajících uzlech), a na základě počtu uzlů nebo virtuálních počítačů v clusteru ( globální škálovatelnost clusteru).</span><span class="sxs-lookup"><span data-stu-id="91060-259">The biggest benefit is that you get a production-ready environment in which you can scale out the application based on the number of container instances you want to use (inner-scalability in the existing nodes), and based on the number of nodes or VMs in the cluster (global scalability of the cluster).</span></span>

<span data-ttu-id="91060-260">Azure Container Service optimalizuje oblíbené open source nástroje a technologie specifické pro Azure.</span><span class="sxs-lookup"><span data-stu-id="91060-260">Azure Container Service optimizes popular open-source tools and technologies specifically for Azure.</span></span> <span data-ttu-id="91060-261">Získáte otevřené řešení, které nabízí přenositelnost, pro vaše kontejnery i pro konfiguraci aplikace.</span><span class="sxs-lookup"><span data-stu-id="91060-261">You get an open solution that offers portability, both for your containers and for your application configuration.</span></span> <span data-ttu-id="91060-262">Vyberte velikost, počet hostitelů a služba Orchestrator Tools – Container Service zpracovává všechno ostatní.</span><span class="sxs-lookup"><span data-stu-id="91060-262">You select the size, the number of hosts, and the orchestrator tools-Container Service handles everything else.</span></span>

<span data-ttu-id="91060-263">Díky Kubernetes můžou vývojáři sledovat fyzické a virtuální počítače a plánovat infrastrukturu zaměřenou na kontejner, která usnadňuje následující možnosti, mimo jiné:</span><span class="sxs-lookup"><span data-stu-id="91060-263">With Kubernetes, developers can progress from thinking about physical and virtual machines, to planning a container-centric infrastructure that facilitates the following capabilities, among others:</span></span>

- <span data-ttu-id="91060-264">Aplikace založené na více kontejnerech</span><span class="sxs-lookup"><span data-stu-id="91060-264">Applications based on multiple containers</span></span>

- <span data-ttu-id="91060-265">Replikace instancí kontejnerů a horizontálního automatického škálování</span><span class="sxs-lookup"><span data-stu-id="91060-265">Replicating container instances and horizontal autoscaling</span></span>

- <span data-ttu-id="91060-266">Pojmenování a zjišťování (například interní DNS)</span><span class="sxs-lookup"><span data-stu-id="91060-266">Naming and discovering (for example, internal DNS)</span></span>

- <span data-ttu-id="91060-267">Vyrovnávání zatížení</span><span class="sxs-lookup"><span data-stu-id="91060-267">Balancing loads</span></span>

- <span data-ttu-id="91060-268">Postupné aktualizace</span><span class="sxs-lookup"><span data-stu-id="91060-268">Rolling updates</span></span>

- <span data-ttu-id="91060-269">Distribuce tajných kódů</span><span class="sxs-lookup"><span data-stu-id="91060-269">Distributing secrets</span></span>

- <span data-ttu-id="91060-270">Kontroly stavu aplikace</span><span class="sxs-lookup"><span data-stu-id="91060-270">Application health checks</span></span>

## <a name="next-steps"></a><span data-ttu-id="91060-271">Další postup</span><span class="sxs-lookup"><span data-stu-id="91060-271">Next steps</span></span>

<span data-ttu-id="91060-272">Podrobnější zkoumání tohoto obsahu najdete na wikiwebu GitHub:<https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-CI-CD)></span><span class="sxs-lookup"><span data-stu-id="91060-272">Explore this content more in-depth on the GitHub wiki: <https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-CI-CD)></span></span>

## <a name="walkthrough-6-deploy-your-windows-containers-based-apps-to-azure-app-service-for-containers"></a><span data-ttu-id="91060-273">Návod 6: Nasaďte aplikace založené na kontejnerech Windows pro Azure App Service pro kontejnery.</span><span class="sxs-lookup"><span data-stu-id="91060-273">Walkthrough 6: Deploy your Windows Containers-based apps to Azure App Service for Containers</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="91060-274">Dostupnost technického návodu</span><span class="sxs-lookup"><span data-stu-id="91060-274">Technical walkthrough availability</span></span>

<span data-ttu-id="91060-275">Úplný technický návod je k dispozici na wikiwebu eShopModernizing GitHub:</span><span class="sxs-lookup"><span data-stu-id="91060-275">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki:</span></span>

<https://github.com/dotnet-architecture/eShopModernizing/wiki/Deploy-Windows-Container-to-Azure-App-Service>

### <a name="overview"></a><span data-ttu-id="91060-276">Přehled</span><span class="sxs-lookup"><span data-stu-id="91060-276">Overview</span></span>

<span data-ttu-id="91060-277">Jednoduchou kontejnerovou aplikaci pomocí kontejnerů Windows lze snadno nasadit do Azure App Service pro kontejnery.</span><span class="sxs-lookup"><span data-stu-id="91060-277">A simple containerized application using Windows Containers can easily be deployed to Azure App Service for Containers.</span></span> <span data-ttu-id="91060-278">Toto je doporučený postup pro většinu aplikací založených na kontejnerech Windows.</span><span class="sxs-lookup"><span data-stu-id="91060-278">This is the recommended approach for most Windows Container-based applications.</span></span>

### <a name="goals"></a><span data-ttu-id="91060-279">Cíle</span><span class="sxs-lookup"><span data-stu-id="91060-279">Goals</span></span>

<span data-ttu-id="91060-280">Cílem tohoto návodu je zjistit, jak nasadit aplikaci založenou na kontejnerech Windows pro Azure App Service pro kontejnery z registru (Docker Hub nebo Azure Container Registry).</span><span class="sxs-lookup"><span data-stu-id="91060-280">The goal of this walkthrough is to learn how to deploy a Windows Container–based application to Azure App Service for Containers from a registry (Docker Hub or Azure Container Registry).</span></span>

### <a name="scenario"></a><span data-ttu-id="91060-281">Scénář</span><span class="sxs-lookup"><span data-stu-id="91060-281">Scenario</span></span>

![Nasazení aplikace založené na kontejnerech Windows pro Azure App Service pro kontejnery](./media/image5-11.png)

### <a name="benefits"></a><span data-ttu-id="91060-283">Výhody</span><span class="sxs-lookup"><span data-stu-id="91060-283">Benefits</span></span>

<span data-ttu-id="91060-284">Nasazení do Azure App Service for Containers nabízí výhody kontejnerů spárovaných s výhodami PaaS Azure App Service.</span><span class="sxs-lookup"><span data-stu-id="91060-284">Deploying to Azure App Service for Containers offers the benefits of containers paired with the PaaS benefits of Azure App Service.</span></span> <span data-ttu-id="91060-285">Službu App Service je možné snadno škálovat vertikálně i vodorovně a je možné ji nakonfigurovat na automatické škálování tak, aby splňovala měnící se požadavky.</span><span class="sxs-lookup"><span data-stu-id="91060-285">The app service can easily be scaled both vertically and horizontally, and can be configured to autoscale to meet changing demands.</span></span> <span data-ttu-id="91060-286">Aktualizace se dají provádět s nulovými výpadky a konfigurace průběžného nasazování z registru se dá snadno nakonfigurovat taky.</span><span class="sxs-lookup"><span data-stu-id="91060-286">Updates can be performed with zero downtime and configuration of continuous deployment from a registry is easily configured as well.</span></span>

## <a name="next-steps"></a><span data-ttu-id="91060-287">Další kroky</span><span class="sxs-lookup"><span data-stu-id="91060-287">Next steps</span></span>

<span data-ttu-id="91060-288">Podrobnější zkoumání tohoto obsahu najdete na wikiwebu GitHub:<https://github.com/dotnet-architecture/eShopModernizing/wiki/Deploy-Windows-Container-to-Azure-App-Service></span><span class="sxs-lookup"><span data-stu-id="91060-288">Explore this content more in-depth on the GitHub wiki: <https://github.com/dotnet-architecture/eShopModernizing/wiki/Deploy-Windows-Container-to-Azure-App-Service></span></span>

> [!div class="step-by-step"]
> <span data-ttu-id="91060-289">[Předchozí](modernize-existing-apps-to-cloud-optimized/migrate-to-hybrid-cloud-scenarios.md)Další
> [](conclusions.md)</span><span class="sxs-lookup"><span data-stu-id="91060-289">[Previous](modernize-existing-apps-to-cloud-optimized/migrate-to-hybrid-cloud-scenarios.md)
[Next](conclusions.md)</span></span>
