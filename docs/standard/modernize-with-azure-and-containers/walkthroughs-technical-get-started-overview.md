---
title: Návody a přehled technických začátků
description: Modernizace stávajících aplikací .NET pomocí cloudu Azure a kontejnery Windows | Návody a technický přehled Začínáme
ms.date: 04/28/2018
ms.openlocfilehash: 1ae6f3c1e739184356b97fa96e74bab402bf1d2a
ms.sourcegitcommit: 34593b4d0be779699d38a9949d6aec11561657ec
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/11/2019
ms.locfileid: "66832952"
---
# <a name="walkthroughs-and-technical-get-started-overview"></a><span data-ttu-id="c2284-103">Návody a přehled technických začátků</span><span class="sxs-lookup"><span data-stu-id="c2284-103">Walkthroughs and technical get started overview</span></span>

<span data-ttu-id="c2284-104">Omezení velikosti tuto elektronickou příručku, další technickou dokumentaci a úplné názorné postupy byly k dispozici v úložišti GitHub.</span><span class="sxs-lookup"><span data-stu-id="c2284-104">To limit the size of this e-book, additional technical documentation and the full walkthroughs were made available in a GitHub repository.</span></span> <span data-ttu-id="c2284-105">Online řada návodů, který je popsaný v této kapitole zahrnuje podrobné nastavení více prostředí, které jsou založeny na kontejnery Windows a nasazení do Azure.</span><span class="sxs-lookup"><span data-stu-id="c2284-105">The online series of walkthroughs that is described in this chapter covers the step-by-step setup of the multiple environments that are based on Windows Containers, and deployment to Azure.</span></span>

<span data-ttu-id="c2284-106">Následující části popisují, co každého návodu je o cílech a vysoké úrovně pro zpracování obrazu a poskytuje diagramu úloh, které jsou zahrnuty.</span><span class="sxs-lookup"><span data-stu-id="c2284-106">The following sections explain what each walkthrough is about, its objectives and high-level vision, and provides a diagram of the tasks that are involved.</span></span> <span data-ttu-id="c2284-107">Můžete získat návody sami v *eShopModernizing* wiki úložiště GitHub aplikace na <https://github.com/dotnet-architecture/eShopModernizing/wiki>.</span><span class="sxs-lookup"><span data-stu-id="c2284-107">You can get the walkthroughs themselves in the *eShopModernizing* apps GitHub repo wiki at <https://github.com/dotnet-architecture/eShopModernizing/wiki>.</span></span>

## <a name="technical-walkthrough-list"></a><span data-ttu-id="c2284-108">Seznam průvodcem produktem</span><span class="sxs-lookup"><span data-stu-id="c2284-108">Technical walkthrough list</span></span>

<span data-ttu-id="c2284-109">Následující návody pro get-started poskytují komplexní a konzistentní technické pokyny pro ukázkové aplikace, které můžete přenést a shift pomocí kontejnerů a přesuňte pomocí několika možností nasazení v Azure.</span><span class="sxs-lookup"><span data-stu-id="c2284-109">The following get-started walkthroughs provide consistent and comprehensive technical guidance for sample apps that you can lift and shift by using containers, and then move by using multiple deployment choices in Azure.</span></span>

<span data-ttu-id="c2284-110">Každá z následujících návodech používá nové ukázkové eShopLegacy a eShopModernizing aplikace, které jsou k dispozici na Githubu v <https://github.com/dotnet-architecture/eShopModernizing>.</span><span class="sxs-lookup"><span data-stu-id="c2284-110">Each of the following walkthroughs uses the new sample eShopLegacy and eShopModernizing apps, which are available on GitHub at <https://github.com/dotnet-architecture/eShopModernizing>.</span></span>

- <span data-ttu-id="c2284-111">**Prohlídka eShop starší verze aplikací (aplikace pro směrný plán pro modernizaci)**</span><span class="sxs-lookup"><span data-stu-id="c2284-111">**Tour of eShop legacy apps (baseline apps to modernize)**</span></span>

- <span data-ttu-id="c2284-112">**Kontejnerizace existující webových aplikací ASP.NET (WebForms & MVC) s kontejnery Windows**</span><span class="sxs-lookup"><span data-stu-id="c2284-112">**Containerize your existing ASP.NET web apps (WebForms & MVC) with Windows Containers**</span></span>

- <span data-ttu-id="c2284-113">**Kontejnerizovat stávající službu WCF (aplikace pro N-vrstvá) s kontejnery Windows**</span><span class="sxs-lookup"><span data-stu-id="c2284-113">**Containerize your existing WCF services (N-Tier apps) with Windows Containers**</span></span>

- <span data-ttu-id="c2284-114">**Nasazení aplikace založené na kontejnery Windows na virtuálních počítačích Azure**</span><span class="sxs-lookup"><span data-stu-id="c2284-114">**Deploy your Windows Containers-based app to Azure VMs**</span></span>

- <span data-ttu-id="c2284-115">**Nasazení aplikací na základě kontejnerů Windows v Kubernetes ve službě Azure Container Service**</span><span class="sxs-lookup"><span data-stu-id="c2284-115">**Deploy your Windows Containers-based apps to Kubernetes in Azure Container Service**</span></span>

## <a name="walkthrough-1-tour-of-eshop-legacy-apps"></a><span data-ttu-id="c2284-116">Návod 1: Prohlídka eShop starší verze aplikací</span><span class="sxs-lookup"><span data-stu-id="c2284-116">Walkthrough 1: Tour of eShop legacy apps</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="c2284-117">Dostupnost průvodcem produktem</span><span class="sxs-lookup"><span data-stu-id="c2284-117">Technical walkthrough availability</span></span>

<span data-ttu-id="c2284-118">Je k dispozici v wiki úložiště GitHub eShopModernizing plnou technickou názorný postup:</span><span class="sxs-lookup"><span data-stu-id="c2284-118">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki:</span></span>

[<span data-ttu-id="c2284-119">návody eShopModernizing wiki</span><span class="sxs-lookup"><span data-stu-id="c2284-119">eShopModernizing wiki walkthroughs</span></span>](https://github.com/dotnet-architecture/eShopModernizing/wiki)

### <a name="overview"></a><span data-ttu-id="c2284-120">Přehled</span><span class="sxs-lookup"><span data-stu-id="c2284-120">Overview</span></span>

<span data-ttu-id="c2284-121">V tomto podrobném návodu můžete prozkoumat počáteční implementace tři ukázkové starší verze aplikace.</span><span class="sxs-lookup"><span data-stu-id="c2284-121">In this walkthrough, you can explore the initial implementation of three sample legacy applications.</span></span> <span data-ttu-id="c2284-122">První dva ukázkové webové aplikace mají monolitické architektury a byly vytvořeny pomocí klasického rozhraní ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="c2284-122">The first two sample web apps have a monolithic architecture, and were created by using classic ASP.NET.</span></span> <span data-ttu-id="c2284-123">Jedna aplikace je založena na technologii ASP.NET 4.x MVC; Druhá aplikace je založena na webových formulářů ASP.NET 4.x.</span><span class="sxs-lookup"><span data-stu-id="c2284-123">One application is based on ASP.NET 4.x MVC; the second application is based on ASP.NET 4.x Web Forms.</span></span>
<span data-ttu-id="c2284-124">Třetí aplikace je 3vrstvé aplikace skládající se tak, že klientská aplikace WinForms a na straně serveru [Windows Communication Foundation (WCF)](../../framework/wcf/whats-wcf.md) služby.</span><span class="sxs-lookup"><span data-stu-id="c2284-124">The third app is a 3-Tier app composed by a client WinForms app and a server-side [Windows Communication Foundation (WCF)](../../framework/wcf/whats-wcf.md) service.</span></span>

<span data-ttu-id="c2284-125">Všechny tyto aplikace jsou k dispozici na [úložiště GitHub eShopModernizing](https://github.com/dotnet-architecture/eShopModernizing).</span><span class="sxs-lookup"><span data-stu-id="c2284-125">All these applications are available at the [eShopModernizing GitHub repo](https://github.com/dotnet-architecture/eShopModernizing).</span></span>

### <a name="goals"></a><span data-ttu-id="c2284-126">Cíle</span><span class="sxs-lookup"><span data-stu-id="c2284-126">Goals</span></span>

<span data-ttu-id="c2284-127">Hlavním cílem tohoto návodu je jednoduše a seznamte se s těmito aplikacemi a s jejich kódu a konfigurace.</span><span class="sxs-lookup"><span data-stu-id="c2284-127">The main goal of this walkthrough is simply to get familiar with these apps, and with their code and configuration.</span></span> <span data-ttu-id="c2284-128">Aplikace můžete nakonfigurovat tak, aby generovat a používat mock data bez použití databáze SQL pro účely testování.</span><span class="sxs-lookup"><span data-stu-id="c2284-128">You can configure the apps so that they generate and use mock data, without using the SQL database, for testing purposes.</span></span> <span data-ttu-id="c2284-129">Tato volitelná konfigurace je založen na vkládání závislostí oddělující způsobem.</span><span class="sxs-lookup"><span data-stu-id="c2284-129">This optional config is based on dependency injection, in a decoupled way.</span></span>

### <a name="scenario-1-aspnet-web-apps"></a><span data-ttu-id="c2284-130">Scénář 1: Webových aplikací ASP.NET</span><span class="sxs-lookup"><span data-stu-id="c2284-130">Scenario 1: ASP.NET Web apps</span></span>

<span data-ttu-id="c2284-131">Následující obrázek znázorňuje jednoduchý scénář původní starší verze webových aplikací ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="c2284-131">The figure below shows the simple scenario of the original legacy ASP.NET web applications.</span></span>

![Jednoduchá architektura scénář původní starší verze webových aplikací ASP.NET](./media/image5-1.png)

<span data-ttu-id="c2284-133">Z hlediska domény firmy obě aplikace nabízejí katalogu stejné funkce pro správu.</span><span class="sxs-lookup"><span data-stu-id="c2284-133">From a business domain perspective, both apps offer the same catalog management features.</span></span> <span data-ttu-id="c2284-134">Členové týmu enterprise eShop využije aplikace k zobrazení a úprava katalog produktů.</span><span class="sxs-lookup"><span data-stu-id="c2284-134">Members of the eShop enterprise team would use the app to view and edit the product catalog.</span></span>

<span data-ttu-id="c2284-135">Následující obrázek ukazuje na snímcích obrazovky počáteční aplikace.</span><span class="sxs-lookup"><span data-stu-id="c2284-135">The next figure shows the initial app screenshots.</span></span>

![Aplikace ASP.NET MVC a ASP.NET Web Forms (technologie existující/starší verze)](./media/image5-2.png)

<span data-ttu-id="c2284-137">Závislosti v technologii ASP.NET 4.x a předchozími verzemi (buď pro MVC nebo pro webové formuláře) znamená, že se tyto aplikace nespustí v rozhraní .NET Core, pokud kód je úplně přepsán pomocí ASP.NET Core MVC.</span><span class="sxs-lookup"><span data-stu-id="c2284-137">Dependencies in ASP.NET 4.x or earlier versions (either for MVC or for Web Forms) means that these applications won’t run on .NET Core unless the code is fully rewritten by using ASP.NET Core MVC.</span></span>

### <a name="scenario-2-wcf-service-and-winforms-client-app-3-tier-app"></a><span data-ttu-id="c2284-138">Scénář 2: Aplikace WinForms klienta (3vrstvé aplikace) a služby WCF</span><span class="sxs-lookup"><span data-stu-id="c2284-138">Scenario 2: WCF service and WinForms client app (3-Tier app)</span></span>

<span data-ttu-id="c2284-139">Následující obrázek znázorňuje jednoduchý scénář původní 3vrstvá starší verze aplikace.</span><span class="sxs-lookup"><span data-stu-id="c2284-139">The figure below shows the simple scenario of the original 3-Tier legacy application.</span></span>

![Jednoduchá architektura scénář být vybavené klientskou aplikací WinForms a původní starší verze 3vrstvé aplikace se službou WCF](./media/image5-1.5.png)

### <a name="benefits"></a><span data-ttu-id="c2284-141">Výhody</span><span class="sxs-lookup"><span data-stu-id="c2284-141">Benefits</span></span>

<span data-ttu-id="c2284-142">Výhody tohoto názorného postupu jsou jednoduché: Získejte zkušenosti s kódem a počáteční aplikace.</span><span class="sxs-lookup"><span data-stu-id="c2284-142">The benefits of this walkthrough are simple: Just get familiar with the code and initial apps.</span></span>

### <a name="next-steps"></a><span data-ttu-id="c2284-143">Další kroky</span><span class="sxs-lookup"><span data-stu-id="c2284-143">Next steps</span></span>

<span data-ttu-id="c2284-144">Tento obsah podrobnější zkoumání na Wiki úložiště GitHub:</span><span class="sxs-lookup"><span data-stu-id="c2284-144">Explore this content more in-depth on the GitHub wiki:</span></span>

- [<span data-ttu-id="c2284-145">Prohlídka na základní technologie ASP.NET MVC a aplikace webových formulářů "starší"</span><span class="sxs-lookup"><span data-stu-id="c2284-145">Tour on the baseline ASP.NET MVC and Web Forms “legacy” apps</span></span>](https://github.com/dotnet-architecture/eShopModernizing/wiki/01.-Tour-on-the-ASP.NET-MVC-and-WebForms-apps-implementation-code)
- [<span data-ttu-id="c2284-146">Prohlídka na aplikace WinForms v "starší" (3 vrstvy) a služby WCF směrného plánu</span><span class="sxs-lookup"><span data-stu-id="c2284-146">Tour on the baseline WCF service and WinForms (3-Tier) “legacy” app</span></span>](https://github.com/dotnet-architecture/eShopModernizing/wiki/21.-Tour-on-the-WCF-service-and-WinForms-apps)

## <a name="walkthrough-2-containerize-your-existing-net-applications-with-windows-containers"></a><span data-ttu-id="c2284-147">Návod 2: Kontejnerizace existující aplikace .NET s kontejnery Windows</span><span class="sxs-lookup"><span data-stu-id="c2284-147">Walkthrough 2: Containerize your existing .NET applications with Windows Containers</span></span>

### <a name="overview"></a><span data-ttu-id="c2284-148">Přehled</span><span class="sxs-lookup"><span data-stu-id="c2284-148">Overview</span></span>

<span data-ttu-id="c2284-149">Kontejnery Windows použijte ke zlepšení nasazení existujících aplikací .NET, jako jsou systémy založené na MVC, webových formulářů nebo WCF, do produkčního prostředí, vývojová a testovací prostředí.</span><span class="sxs-lookup"><span data-stu-id="c2284-149">Use Windows Containers to improve deployment of existing .NET applications, like those based on MVC, Web Forms, or WCF, to production, development, and test environments.</span></span>

### <a name="goals"></a><span data-ttu-id="c2284-150">Cíle</span><span class="sxs-lookup"><span data-stu-id="c2284-150">Goals</span></span>

<span data-ttu-id="c2284-151">Cílem tohoto návodu je zobrazit několik možností pro uzavření do kontejneru existující aplikaci .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c2284-151">The goal of this walkthrough is to show you several options for containerizing an existing .NET Framework application.</span></span> <span data-ttu-id="c2284-152">Můžete:</span><span class="sxs-lookup"><span data-stu-id="c2284-152">You can:</span></span>

- <span data-ttu-id="c2284-153">Kontejnerizujte své aplikace pomocí [Visual Studio 2017 Tools for Docker](/aspnet/core/host-and-deploy/docker/visual-studio-tools-for-docker) (Visual Studio 2017 nebo novější verze).</span><span class="sxs-lookup"><span data-stu-id="c2284-153">Containerize your application by using [Visual Studio 2017 Tools for Docker](/aspnet/core/host-and-deploy/docker/visual-studio-tools-for-docker) (Visual Studio 2017 or later versions).</span></span>

- <span data-ttu-id="c2284-154">Kontejnerizujte své aplikace tak, že ručně přidáte [soubor Dockerfile](https://docs.docker.com/engine/reference/builder/)a následným použitím [rozhraní příkazového řádku Dockeru](https://docs.docker.com/engine/reference/commandline/cli/).</span><span class="sxs-lookup"><span data-stu-id="c2284-154">Containerize your application by manually adding a [Dockerfile](https://docs.docker.com/engine/reference/builder/), and then using the [Docker CLI](https://docs.docker.com/engine/reference/commandline/cli/).</span></span>

- <span data-ttu-id="c2284-155">Kontejnerizujte své aplikace pomocí [Img2Docker](https://github.com/docker/communitytools-image2docker-win) nástroje (nástroj open source od Dockeru).</span><span class="sxs-lookup"><span data-stu-id="c2284-155">Containerize your application by using the [Img2Docker](https://github.com/docker/communitytools-image2docker-win) tool (an open-source tool from Docker).</span></span>

<span data-ttu-id="c2284-156">Tento návod se zaměřuje na Visual Studio 2017 Tools for Docker přístup, ale ostatní dva přístupy jsou podobné ve vztahu pomocí soubory Dockerfile.</span><span class="sxs-lookup"><span data-stu-id="c2284-156">This walkthrough focuses on the Visual Studio 2017 Tools for Docker approach, but the other two approaches are fairly similar in regard to using Dockerfiles.</span></span>

### <a name="scenario-1-containerized-aspnet-web-apps"></a><span data-ttu-id="c2284-157">Scénář 1: Kontejnerizované webové aplikace ASP.NET</span><span class="sxs-lookup"><span data-stu-id="c2284-157">Scenario 1: Containerized ASP.NET web apps</span></span>

<span data-ttu-id="c2284-158">Následující obrázek znázorňuje scénář pro kontejnerizované eShop starší verze webové aplikace aplikace.</span><span class="sxs-lookup"><span data-stu-id="c2284-158">Figure below shows the scenario for containerized eShop legacy web apps applications.</span></span>

![Diagram architektury zjednodušené kontejnerizovaných aplikací technologie ASP.NET ve vývojovém prostředí](./media/image5-3.png)

### <a name="scenario-2-containerized-wcf-service"></a><span data-ttu-id="c2284-160">Scénář 2: Kontejnerizovaná služba WCF</span><span class="sxs-lookup"><span data-stu-id="c2284-160">Scenario 2: Containerized WCF service</span></span>

<span data-ttu-id="c2284-161">Následující obrázek znázorňuje scénář 3vrstvé aplikace s kontejnerizovaná služba WCF.</span><span class="sxs-lookup"><span data-stu-id="c2284-161">Figure below shows the scenario for a 3-Tier app with a containerized WCF service.</span></span>

![Zjednodušená diagram architektury kontejnerizované služby WCF ve vývojovém prostředí](./media/image5-3.5.png)

### <a name="benefits"></a><span data-ttu-id="c2284-163">Výhody</span><span class="sxs-lookup"><span data-stu-id="c2284-163">Benefits</span></span>

<span data-ttu-id="c2284-164">Existují výhody používání monolitické aplikace v kontejneru.</span><span class="sxs-lookup"><span data-stu-id="c2284-164">There are advantages to running your monolithic application in a container.</span></span> <span data-ttu-id="c2284-165">Nejprve vytvořte image pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="c2284-165">First, you create an image for the application.</span></span> <span data-ttu-id="c2284-166">Od tohoto okamžiku v každé nasazení běží ve stejném prostředí.</span><span class="sxs-lookup"><span data-stu-id="c2284-166">From that point on, every deployment runs in the same environment.</span></span> <span data-ttu-id="c2284-167">Každý kontejner používá stejnou verzi operačního systému, má stejnou verzi závislosti nainstalované, používá stejnou verzi rozhraní .NET framework a je vytvořena pomocí stejného procesu.</span><span class="sxs-lookup"><span data-stu-id="c2284-167">Every container uses the same OS version, has the same version of dependencies installed, uses the same .NET framework version, and is built by using the same process.</span></span> <span data-ttu-id="c2284-168">V podstatě řízení závislostí vaší aplikace pomocí image Dockeru.</span><span class="sxs-lookup"><span data-stu-id="c2284-168">Basically, you control the dependencies of your application by using a Docker image.</span></span> <span data-ttu-id="c2284-169">Závislosti cestují s aplikací při nasazování kontejnerů.</span><span class="sxs-lookup"><span data-stu-id="c2284-169">The dependencies travel with the application when you deploy the containers.</span></span>

<span data-ttu-id="c2284-170">Další výhodou je, že vývojáři spuštěním aplikace v prostředí konzistentní vzhledem k aplikacím, které poskytuje kontejnery Windows.</span><span class="sxs-lookup"><span data-stu-id="c2284-170">An additional benefit is that developers can run the application in the consistent environment that's provided by Windows Containers.</span></span> <span data-ttu-id="c2284-171">Problémy, které se zobrazují pouze u některých verzí můžete okamžitě, nanese místo zpřístupnění v přípravném nebo produkčním prostředí.</span><span class="sxs-lookup"><span data-stu-id="c2284-171">Issues that appear only with certain versions can be spotted immediately, instead of surfacing in a staging or production environment.</span></span> <span data-ttu-id="c2284-172">Rozdíly ve vývojovém prostředí, které používají členové vývojového týmu méně důležitá, když aplikace běží v kontejnerech.</span><span class="sxs-lookup"><span data-stu-id="c2284-172">Differences in development environments used by members of the development team matter less when applications run in containers.</span></span>

<span data-ttu-id="c2284-173">Kontejnerizované aplikace také mít plošší křivky horizontální navýšení kapacity.</span><span class="sxs-lookup"><span data-stu-id="c2284-173">Containerized applications also have a flatter scale-out curve.</span></span> <span data-ttu-id="c2284-174">Kontejnerizovaných aplikací umožňují další aplikace a instance služby (podle kontejnerů) virtuálního počítače nebo fyzického počítače, ve srovnání s nasazení aplikace pravidelně na počítač.</span><span class="sxs-lookup"><span data-stu-id="c2284-174">Containerized apps enable you to have more application and service instances (based on containers) in a VM or physical machine compared to regular application deployments per machine.</span></span> <span data-ttu-id="c2284-175">Výsledkem je vyšší hustota a méně požadované prostředky, zejména v případě, že používáte orchestrátorů, jako je Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="c2284-175">This translates to higher density and fewer required resources, especially when you use orchestrators like Kubernetes.</span></span>

<span data-ttu-id="c2284-176">Kontejnerizace v situacích, ideální, nevyžaduje změny kódu aplikace (C\#).</span><span class="sxs-lookup"><span data-stu-id="c2284-176">Containerization, in ideal situations, does not require making any changes to the application code (C\#).</span></span> <span data-ttu-id="c2284-177">Ve většině případů stačí Docker nasazení metadat souborů (soubory Dockerfile a Docker Compose soubory).</span><span class="sxs-lookup"><span data-stu-id="c2284-177">In most scenarios, you just need the Docker deployment metadata files (Dockerfiles and Docker Compose files).</span></span>

### <a name="next-steps"></a><span data-ttu-id="c2284-178">Další kroky</span><span class="sxs-lookup"><span data-stu-id="c2284-178">Next steps</span></span>

<span data-ttu-id="c2284-179">Tento obsah podrobnější zkoumání na Wiki úložiště GitHub:</span><span class="sxs-lookup"><span data-stu-id="c2284-179">Explore this content more in-depth on the GitHub wiki:</span></span>

- [<span data-ttu-id="c2284-180">Jak kontejnerizovat aplikace webového rozhraní .NET Framework s kontejnery Windows a Dockeru</span><span class="sxs-lookup"><span data-stu-id="c2284-180">How to containerize the .NET Framework web apps with Windows Containers and Docker</span></span>](https://github.com/dotnet-architecture/eShopModernizing/wiki/02.-How-to-containerize-the-.NET-Framework-web-apps-with-Windows-Containers-and-Docker)
- [<span data-ttu-id="c2284-181">Přidání podpory Dockeru do služby WCF</span><span class="sxs-lookup"><span data-stu-id="c2284-181">Adding Docker Support to a WCF service</span></span>](https://github.com/dotnet-architecture/eShopModernizing/wiki/22.-Adding-Docker-Support)

## <a name="walkthrough-3-deploy-your-windows-containers-based-app-to-azure-vms"></a><span data-ttu-id="c2284-182">Návod 3: Nasazení aplikace založené na kontejnery Windows na virtuálních počítačích Azure</span><span class="sxs-lookup"><span data-stu-id="c2284-182">Walkthrough 3: Deploy your Windows Containers-based app to Azure VMs</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="c2284-183">Dostupnost průvodcem produktem</span><span class="sxs-lookup"><span data-stu-id="c2284-183">Technical walkthrough availability</span></span>

<span data-ttu-id="c2284-184">Je k dispozici v wiki úložiště GitHub eShopModernizing plnou technickou názorný postup: <https://github.com/dotnet-architecture/eShopModernizing/wiki/06.-Deploying-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD)></span><span class="sxs-lookup"><span data-stu-id="c2284-184">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki: <https://github.com/dotnet-architecture/eShopModernizing/wiki/06.-Deploying-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD)></span></span>

### <a name="overview"></a><span data-ttu-id="c2284-185">Přehled</span><span class="sxs-lookup"><span data-stu-id="c2284-185">Overview</span></span>

<span data-ttu-id="c2284-186">Nasazení na hostitele Docker na Windows serveru 2016 virtuálního počítače (počítače) v Azure umožňuje rychle nastavit vývojové/testovací/přípravných prostředí.</span><span class="sxs-lookup"><span data-stu-id="c2284-186">Deploying to a Docker host on a Windows Server 2016 Virtual Machine (VM) in Azure lets you quickly set up development/test/staging environments.</span></span> <span data-ttu-id="c2284-187">Také poskytuje společné místo pro testery nebo firemním uživatelům ověřovat aplikace.</span><span class="sxs-lookup"><span data-stu-id="c2284-187">It also gives you a common place for testers or business users to validate the app.</span></span> <span data-ttu-id="c2284-188">Virtuální počítač také může být platný infrastruktury jako služby (IaaS) produkční prostředí.</span><span class="sxs-lookup"><span data-stu-id="c2284-188">VMs also can be valid Infrastructure as a Service (IaaS) production environments.</span></span>

### <a name="goals"></a><span data-ttu-id="c2284-189">Cíle</span><span class="sxs-lookup"><span data-stu-id="c2284-189">Goals</span></span>

<span data-ttu-id="c2284-190">Cílem tohoto návodu je zobrazit více alternativy, které jste při nasazování kontejnerů Windows na virtuální počítače Azure, které jsou založené na Windows Server 2016 nebo novější verze.</span><span class="sxs-lookup"><span data-stu-id="c2284-190">The goal of this walkthrough is to show you the multiple alternatives you have when you deploy Windows Containers to Azure VMs that are based on Windows Server 2016 or later versions.</span></span>

### <a name="scenarios"></a><span data-ttu-id="c2284-191">Scénáře</span><span class="sxs-lookup"><span data-stu-id="c2284-191">Scenarios</span></span>

<span data-ttu-id="c2284-192">Několik scénáře jsou popsané v tomto názorném postupu.</span><span class="sxs-lookup"><span data-stu-id="c2284-192">Several scenarios are covered in this walkthrough.</span></span>

#### <a name="scenario-a-deploy-to-an-azure-vm-from-a-dev-pc-through-docker-engine-connection"></a><span data-ttu-id="c2284-193">Scénář A: Nasazení na Virtuálním počítači Azure z vývojář počítače přes připojení modul Docker</span><span class="sxs-lookup"><span data-stu-id="c2284-193">Scenario A: Deploy to an Azure VM from a dev PC through Docker Engine connection</span></span>

![Nasazení na Virtuálním počítači Azure z vývojář PC prostřednictvím připojení k modulu Docker](./media/image5-4.png)

<span data-ttu-id="c2284-195">**Obrázek 5 – 4.**</span><span class="sxs-lookup"><span data-stu-id="c2284-195">**Figure 5-4.**</span></span> <span data-ttu-id="c2284-196">Nasazení na Virtuálním počítači Azure z vývojář PC prostřednictvím připojení k modulu Docker</span><span class="sxs-lookup"><span data-stu-id="c2284-196">Deploy to an Azure VM from a dev PC through a Docker Engine connection</span></span>

#### <a name="scenario-b-deploy-to-an-azure-vm-through-a-docker-registry"></a><span data-ttu-id="c2284-197">Scénář B: Nasazení do virtuálního počítače Azure pomocí registru Dockeru</span><span class="sxs-lookup"><span data-stu-id="c2284-197">Scenario B: Deploy to an Azure VM through a Docker Registry</span></span>

![Nasazení do virtuálního počítače Azure pomocí registru Dockeru](./media/image5-5.png)

<span data-ttu-id="c2284-199">**Obrázek 5 – 5.**</span><span class="sxs-lookup"><span data-stu-id="c2284-199">**Figure 5-5.**</span></span> <span data-ttu-id="c2284-200">Nasazení do virtuálního počítače Azure pomocí registru Dockeru</span><span class="sxs-lookup"><span data-stu-id="c2284-200">Deploy to an Azure VM through a Docker Registry</span></span>

#### <a name="scenario-c-deploy-to-an-azure-vm-from-cicd-pipelines-in-azure-devops-services"></a><span data-ttu-id="c2284-201">Scénář C: Nasazení na Virtuálním počítači Azure z kanálů CI/CD ve službách Azure DevOps</span><span class="sxs-lookup"><span data-stu-id="c2284-201">Scenario C: Deploy to an Azure VM from CI/CD pipelines in Azure DevOps Services</span></span>

![Nasazení na Virtuálním počítači Azure z kanálů CI/CD ve službách Azure DevOps](./media/image5-6.png)

<span data-ttu-id="c2284-203">**Obrázek 5 a 6.**</span><span class="sxs-lookup"><span data-stu-id="c2284-203">**Figure 5-6.**</span></span> <span data-ttu-id="c2284-204">Nasazení na Virtuálním počítači Azure z kanálů CI/CD ve službách Azure DevOps</span><span class="sxs-lookup"><span data-stu-id="c2284-204">Deploy to an Azure VM from CI/CD pipelines in Azure DevOps Services</span></span>

### <a name="azure-vms-for-windows-containers"></a><span data-ttu-id="c2284-205">Virtuální počítače Azure pro kontejnery Windows</span><span class="sxs-lookup"><span data-stu-id="c2284-205">Azure VMs for Windows Containers</span></span>

<span data-ttu-id="c2284-206">Virtuální počítače pro Windows kontejnery služby Azure jsou virtuálních počítačů založených na Windows serveru 2016, Windows 10 nebo novější verze, s modul Docker nastavení.</span><span class="sxs-lookup"><span data-stu-id="c2284-206">Azure VMs for Windows Containers are VMs based on Windows Server 2016, Windows 10, or later versions, both with Docker Engine set up.</span></span> <span data-ttu-id="c2284-207">Ve většině případů se používá Windows Server 2016 ve virtuálních počítačích Azure.</span><span class="sxs-lookup"><span data-stu-id="c2284-207">In most cases, Windows Server 2016 is used in the Azure VMs.</span></span>

<span data-ttu-id="c2284-208">Azure v současné době poskytuje virtuální počítač s názvem **Windows serveru 2016 s kontejnery**.</span><span class="sxs-lookup"><span data-stu-id="c2284-208">Azure currently provides a VM named **Windows Server 2016 with Containers**.</span></span> <span data-ttu-id="c2284-209">Tento virtuální počítač můžete vyzkoušet nové funkce kontejneru Windows serveru s Windows Server Core nebo Windows Nano Server.</span><span class="sxs-lookup"><span data-stu-id="c2284-209">You can use this VM to try the new Windows Server Container feature, with either Windows Server Core or Windows Nano Server.</span></span> <span data-ttu-id="c2284-210">Kontejnerové Image operačního systému jsou nainstalovány a pak je virtuální počítač připravený k použití s Dockerem.</span><span class="sxs-lookup"><span data-stu-id="c2284-210">Container OS images are installed, and then the VM is ready to use with Docker.</span></span>

### <a name="benefits"></a><span data-ttu-id="c2284-211">Výhody</span><span class="sxs-lookup"><span data-stu-id="c2284-211">Benefits</span></span>

<span data-ttu-id="c2284-212">I když se dají nasadit kontejnery Windows pro místní Windows Server 2016 virtuální počítače, při nasazování do Azure, budete mít snadný způsob, jak začít s virtuálními počítači kontejneru připravené k použití Windows serveru.</span><span class="sxs-lookup"><span data-stu-id="c2284-212">Although Windows Containers can be deployed to on-premises Windows Server 2016 VMs, when you deploy to Azure, you get an easier way to get started, with ready-to-use Windows Server Container VMs.</span></span> <span data-ttu-id="c2284-213">Získáte také běžné online umístění, která je přístupná pro testery a automatické škálovatelnosti pomocí škálovací sady virtuálních počítačů Azure.</span><span class="sxs-lookup"><span data-stu-id="c2284-213">You also get a common online location that’s accessible to testers, and automatic scalability through Azure virtual machine scale sets.</span></span>

### <a name="next-steps"></a><span data-ttu-id="c2284-214">Další kroky</span><span class="sxs-lookup"><span data-stu-id="c2284-214">Next steps</span></span>

<span data-ttu-id="c2284-215">Tento obsah podrobnější zkoumání na Wiki úložiště GitHub:</span><span class="sxs-lookup"><span data-stu-id="c2284-215">Explore this content more in-depth on the GitHub wiki:</span></span>

<https://github.com/dotnet-architecture/eShopModernizing/wiki/06.-Deploying-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD)>

## <a name="walkthrough-4-deploy-your-windows-containers-based-apps-to-azure-container-instances-aci"></a><span data-ttu-id="c2284-216">Návod 4: Nasazovat aplikace založené na kontejnery Windows do služby Azure Container Instances (ACI)</span><span class="sxs-lookup"><span data-stu-id="c2284-216">Walkthrough 4: Deploy your Windows Containers-based apps to Azure Container Instances (ACI)</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="c2284-217">Dostupnost průvodcem produktem</span><span class="sxs-lookup"><span data-stu-id="c2284-217">Technical walkthrough availability</span></span>

<span data-ttu-id="c2284-218">Je k dispozici v wiki úložiště GitHub eShopModernizing plnou technickou názorný postup:</span><span class="sxs-lookup"><span data-stu-id="c2284-218">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki:</span></span>

<span data-ttu-id="c2284-219">[Nasazení aplikace do služby ACI (Azure Container Instances)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances))</span><span class="sxs-lookup"><span data-stu-id="c2284-219">[Deploying the Apps to ACI (Azure Container Instances)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances))</span></span>

### <a name="overview"></a><span data-ttu-id="c2284-220">Přehled</span><span class="sxs-lookup"><span data-stu-id="c2284-220">Overview</span></span>

<span data-ttu-id="c2284-221">[Azure Container Instances (ACI)](https://docs.microsoft.com/azure/container-instances/) je nejrychlejší způsob, jak prostředí dev/test/přípravy kontejnerů, kde můžete nasadit jeden instancí kontejnerů.</span><span class="sxs-lookup"><span data-stu-id="c2284-221">[Azure Container Instances (ACI)](https://docs.microsoft.com/azure/container-instances/) is the quickest way to have a Containers dev/test/staging environment where you can deploy single instances of containers.</span></span>

### <a name="goals"></a><span data-ttu-id="c2284-222">Cíle</span><span class="sxs-lookup"><span data-stu-id="c2284-222">Goals</span></span>

<span data-ttu-id="c2284-223">Tento návod ukazuje základní scénáře při nasazování kontejnerů Windows do Azure Container Instances (ACI) a jak můžete nasadit aplikace eShopModernizing do ACI.</span><span class="sxs-lookup"><span data-stu-id="c2284-223">This walkthrough shows you the main scenarios when deploying Windows Containers to Azure Container Instances (ACI) and how you can deploy eShopModernizing Apps into ACI.</span></span>

### <a name="scenarios"></a><span data-ttu-id="c2284-224">Scénáře</span><span class="sxs-lookup"><span data-stu-id="c2284-224">Scenarios</span></span>

<span data-ttu-id="c2284-225">Může existovat variace o nasazení aplikací eShopModernizing do ACI, jako je nasazení jenom v jednom nebo všechny aplikace (aplikace MVC, webových formulářů aplikaci nebo službu WCF).</span><span class="sxs-lookup"><span data-stu-id="c2284-225">There can be variations about deploying the eShopModernizing apps into ACI such as deploying just one or all of the apps (MVC app, WebForms app or WCF service).</span></span> <span data-ttu-id="c2284-226">V následujícím scénáři je uvedeno níže můžete vidět aplikaci ASP.NET MVC a kontejner SQL serveru, jejich nasazení jako kontejnery do ACI (Azure Container Instances).</span><span class="sxs-lookup"><span data-stu-id="c2284-226">In the following scenario shown below you can see the ASP.NET MVC app plus the SQL Server container both of them deployed as containers into ACI (Azure Container Instances).</span></span>

![Nasazení do služby ACI z vývojového prostředí](./media/image5-3.5.6.png)

### <a name="benefits"></a><span data-ttu-id="c2284-228">Výhody</span><span class="sxs-lookup"><span data-stu-id="c2284-228">Benefits</span></span>

<span data-ttu-id="c2284-229">Služba Azure Container Instances usnadňuje vytváření a správu kontejnerů Dockeru v Azure, aniž byste museli zřizovat virtuální počítače nebo používat službu.</span><span class="sxs-lookup"><span data-stu-id="c2284-229">Azure Container Instances makes it easy to create and manage Docker containers in Azure, without having to provision virtual machines or adopt a higher-level service.</span></span> <span data-ttu-id="c2284-230">Pomocí ACI můžete přímo nasadit kontejner Windows ve službě Azure a zveřejníte ho na Internetu s použitím plně kvalifikovaného názvu domény (FQDN) v řádu sekund (za předpokladu, že budete mít připravený kontejner Windows image v registru Dockeru jako Docker Hubu nebo služby Azure Container Registru).</span><span class="sxs-lookup"><span data-stu-id="c2284-230">With ACI, you can directly deploy a Windows container in Azure and expose it to the internet with a fully qualified domain name (FQDN) in a matter of seconds (Provided that you have the Windows Container image ready in a Docker registry like Docker Hub or Azure Container Registry).</span></span>

### <a name="considerations"></a><span data-ttu-id="c2284-231">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c2284-231">Considerations</span></span>

<span data-ttu-id="c2284-232">Nasazování kontejnerů Windows s buď úplné rozhraní .NET Framework / technologie ASP.NET nebo SQL serveru do Azure Container Instances (ACI) není úplně tak rychlý jako při nasazování na regulární hostitele Docker (např. Windows Server 2016 s kontejnery Windows), protože image Dockeru, musí být stažení (načtený z registru Dockeru) pokaždé, když a i když je mnohem levnější než udržování vašeho vlastního hostitele docker (trvale online jsou výrazně velké velikosti image kontejneru SQL (15.1 GB) a image kontejneru ASP.NET (13.9 GB) Windows Server 2016 s virtuálním Počítačem kontejnery Windows v Azure) nemluvě celý orchestrator, jako je Kubernetes v Azure (AKS), který je na druhé straně skvělou volbou pro nasazení v produkčním prostředí.</span><span class="sxs-lookup"><span data-stu-id="c2284-232">Deploying Windows Containers with either full .NET Framework / ASP.NET or SQL Server into Azure Container Instances (ACI) is not quite as fast as deploying to a regular Docker Host (like a Windows Server 2016 with Windows Containers) because the Docker image has to be downloaded (pulled from the Docker registry) every time and the sizes of the SQL container image (15.1 GB) and the ASP.NET container image (13.9 GB) are significantly large, however it is much cheaper than maintaining your own docker host (permanently on-line Windows Server 2016 with Windows Containers VM in Azure) not to mention a whole orchestrator like Kubernetes in Azure (AKS) which is, on the other hand, a great choice for production deployments.</span></span>

<span data-ttu-id="c2284-233">Jako hlavní uzavření pomocí služby Azure Container Instances je velice přesvědčivý argument možnost pro scénáře vývoje/testování a pro kanály CI/CD.</span><span class="sxs-lookup"><span data-stu-id="c2284-233">As main conclusion, using Azure Container Instances is a very compelling option for Dev/Test scenarios and for CI/CD pipelines.</span></span>

## <a name="next-steps"></a><span data-ttu-id="c2284-234">Další kroky</span><span class="sxs-lookup"><span data-stu-id="c2284-234">Next steps</span></span>

<span data-ttu-id="c2284-235">Tento obsah podrobnější zkoumání na Wiki úložiště GitHub:</span><span class="sxs-lookup"><span data-stu-id="c2284-235">Explore this content more in-depth on the GitHub wiki:</span></span>

[https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances))

## <a name="walkthrough-5-deploy-your-windows-containers-based-apps-to-kubernetes-in-azure-container-service"></a><span data-ttu-id="c2284-236">Návod 5: Nasazení aplikací na základě kontejnerů Windows v Kubernetes ve službě Azure Container Service</span><span class="sxs-lookup"><span data-stu-id="c2284-236">Walkthrough 5: Deploy your Windows Containers-based apps to Kubernetes in Azure Container Service</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="c2284-237">Dostupnost průvodcem produktem</span><span class="sxs-lookup"><span data-stu-id="c2284-237">Technical walkthrough availability</span></span>

<span data-ttu-id="c2284-238">Je k dispozici v wiki úložiště GitHub eShopModernizing plnou technickou názorný postup:</span><span class="sxs-lookup"><span data-stu-id="c2284-238">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki:</span></span>

<https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-CI-CD)>

### <a name="overview"></a><span data-ttu-id="c2284-239">Přehled</span><span class="sxs-lookup"><span data-stu-id="c2284-239">Overview</span></span>

<span data-ttu-id="c2284-240">Aplikace, která je založena na kontejnery Windows rychle muset použít platformy, přesunutí ještě více pryč z virtuálních počítačů IaaS.</span><span class="sxs-lookup"><span data-stu-id="c2284-240">An application that's based on Windows Containers will quickly need to use platforms, moving even further away from IaaS VMs.</span></span> <span data-ttu-id="c2284-241">To je potřeba provést snadno dosáhnout vysoké škálovatelnosti a lépe automatizované škálovatelnost a přináší značné vylepšení v automatické nasazení a správy verzí.</span><span class="sxs-lookup"><span data-stu-id="c2284-241">This is needed to easily achieve high scalability and better automated scalability, and for a significant improvement in automated deployments and versioning.</span></span> <span data-ttu-id="c2284-242">Tyto cíle lze dosáhnout pomocí orchestrátoru [Kubernetes](https://kubernetes.io/), která je dostupná v [služby Azure Container Service](https://azure.microsoft.com/services/container-service/).</span><span class="sxs-lookup"><span data-stu-id="c2284-242">You can achieve these goals by using the orchestrator [Kubernetes](https://kubernetes.io/), available in [Azure Container Services](https://azure.microsoft.com/services/container-service/).</span></span>

### <a name="goals"></a><span data-ttu-id="c2284-243">Cíle</span><span class="sxs-lookup"><span data-stu-id="c2284-243">Goals</span></span>

<span data-ttu-id="c2284-244">Cílem tohoto návodu je naučit se nasazovat aplikace založené na Windows kontejnerů Kubernetes (také nazývané *K8s*) ve službě Azure Container Service.</span><span class="sxs-lookup"><span data-stu-id="c2284-244">The goal of this walkthrough is to learn how to deploy a Windows Container–based application to Kubernetes (also called *K8s*) in Azure Container Service.</span></span> <span data-ttu-id="c2284-245">Nasazování do Kubernetes úplně od začátku je dvoustupňový proces:</span><span class="sxs-lookup"><span data-stu-id="c2284-245">Deploying to Kubernetes from scratch is a two-step process:</span></span>

1. <span data-ttu-id="c2284-246">Nasazení clusteru Kubernetes do služby Azure Container Service.</span><span class="sxs-lookup"><span data-stu-id="c2284-246">Deploy a Kubernetes cluster to Azure Container Service.</span></span>

2. <span data-ttu-id="c2284-247">Nasazení aplikace a související prostředky do clusteru Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="c2284-247">Deploy the application and related resources to the Kubernetes cluster.</span></span>

### <a name="scenarios"></a><span data-ttu-id="c2284-248">Scénáře</span><span class="sxs-lookup"><span data-stu-id="c2284-248">Scenarios</span></span>

#### <a name="scenario-a-deploy-directly-to-a-kubernetes-cluster-from-a-dev-environment"></a><span data-ttu-id="c2284-249">Scénář A: Nasadit do clusteru Kubernetes z vývojového prostředí</span><span class="sxs-lookup"><span data-stu-id="c2284-249">Scenario A: Deploy directly to a Kubernetes cluster from a dev environment</span></span>

![Nasadit do clusteru Kubernetes z vývojového prostředí](./media/image5-7.png)

<span data-ttu-id="c2284-251">**Obrázek 5 – 7.**</span><span class="sxs-lookup"><span data-stu-id="c2284-251">**Figure 5-7.**</span></span> <span data-ttu-id="c2284-252">Nasadit do clusteru Kubernetes z vývojového prostředí</span><span class="sxs-lookup"><span data-stu-id="c2284-252">Deploy directly to a Kubernetes cluster from a development environment</span></span>

#### <a name="scenario-b-deploy-to-a-kubernetes-cluster-from-cicd-pipelines-in-azure-devops-services"></a><span data-ttu-id="c2284-253">Scénář B: Nasazení do clusteru Kubernetes z kanálů CI/CD ve službách Azure DevOps</span><span class="sxs-lookup"><span data-stu-id="c2284-253">Scenario B: Deploy to a Kubernetes cluster from CI/CD pipelines in Azure DevOps Services</span></span>

![Nasazení do clusteru Kubernetes z kanálů CI/CD ve službách Azure DevOps](./media/image5-8.png)

<span data-ttu-id="c2284-255">**Obrázek 5 až 8.**</span><span class="sxs-lookup"><span data-stu-id="c2284-255">**Figure 5-8.**</span></span> <span data-ttu-id="c2284-256">Nasazení do clusteru Kubernetes z kanálů CI/CD ve službách Azure DevOps</span><span class="sxs-lookup"><span data-stu-id="c2284-256">Deploy to a Kubernetes cluster from CI/CD pipelines in Azure DevOps Services</span></span>

### <a name="benefits"></a><span data-ttu-id="c2284-257">Výhody</span><span class="sxs-lookup"><span data-stu-id="c2284-257">Benefits</span></span>

<span data-ttu-id="c2284-258">Existuje mnoho výhod pro nasazení do clusteru v Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="c2284-258">There are many benefits to deploying to a cluster in Kubernetes.</span></span> <span data-ttu-id="c2284-259">Největší výhodou je, že dostanete prostředí připravené pro produkční prostředí, ve kterém můžete aplikace založená na počet instancí kontejneru chcete použít (vnitřní škálovatelnost v existujících uzlů) a na základě počtu virtuálních počítačů nebo uzly v clusteru (horizontálně navýšit Globální škálovatelnost clusteru).</span><span class="sxs-lookup"><span data-stu-id="c2284-259">The biggest benefit is that you get a production-ready environment in which you can scale out the application based on the number of container instances you want to use (inner-scalability in the existing nodes), and based on the number of nodes or VMs in the cluster (global scalability of the cluster).</span></span>

<span data-ttu-id="c2284-260">Služba Azure Container Service optimalizuje oblíbených opensourcových nástrojů a technologií konkrétně pro Azure.</span><span class="sxs-lookup"><span data-stu-id="c2284-260">Azure Container Service optimizes popular open-source tools and technologies specifically for Azure.</span></span> <span data-ttu-id="c2284-261">Získáte otevřené řešení, které nabízí přenositelnost pro vaše kontejnery i Konfigurace aplikací.</span><span class="sxs-lookup"><span data-stu-id="c2284-261">You get an open solution that offers portability, both for your containers and for your application configuration.</span></span> <span data-ttu-id="c2284-262">Vyberete velikost, počet hostitelů, a nástroje orchestrator – kontejner služby postará o všechno ostatní.</span><span class="sxs-lookup"><span data-stu-id="c2284-262">You select the size, the number of hosts, and the orchestrator tools-Container Service handles everything else.</span></span>

<span data-ttu-id="c2284-263">S využitím Kubernetes můžete průběh vývojáře od přemýšlení o fyzické a virtuální počítače, k plánování zaměřené na kontejner infrastruktury, která usnadňuje následující funkce, mimo jiné:</span><span class="sxs-lookup"><span data-stu-id="c2284-263">With Kubernetes, developers can progress from thinking about physical and virtual machines, to planning a container-centric infrastructure that facilitates the following capabilities, among others:</span></span>

- <span data-ttu-id="c2284-264">Aplikace založené na několika kontejnerů</span><span class="sxs-lookup"><span data-stu-id="c2284-264">Applications based on multiple containers</span></span>

- <span data-ttu-id="c2284-265">Replikace container instances a automatické horizontální škálování</span><span class="sxs-lookup"><span data-stu-id="c2284-265">Replicating container instances and horizontal autoscaling</span></span>

- <span data-ttu-id="c2284-266">Pojmenování a zjišťování (například interní DNS)</span><span class="sxs-lookup"><span data-stu-id="c2284-266">Naming and discovering (for example, internal DNS)</span></span>

- <span data-ttu-id="c2284-267">Vyrovnávání zatížení</span><span class="sxs-lookup"><span data-stu-id="c2284-267">Balancing loads</span></span>

- <span data-ttu-id="c2284-268">Aktualizace se zajištěním provozu</span><span class="sxs-lookup"><span data-stu-id="c2284-268">Rolling updates</span></span>

- <span data-ttu-id="c2284-269">Distribuce tajných kódů</span><span class="sxs-lookup"><span data-stu-id="c2284-269">Distributing secrets</span></span>

- <span data-ttu-id="c2284-270">Kontroly stavu aplikace</span><span class="sxs-lookup"><span data-stu-id="c2284-270">Application health checks</span></span>

## <a name="next-steps"></a><span data-ttu-id="c2284-271">Další kroky</span><span class="sxs-lookup"><span data-stu-id="c2284-271">Next steps</span></span>

<span data-ttu-id="c2284-272">Tento obsah podrobnější zkoumání na Wiki úložiště GitHub: <https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-CI-CD)></span><span class="sxs-lookup"><span data-stu-id="c2284-272">Explore this content more in-depth on the GitHub wiki: <https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-CI-CD)></span></span>

## <a name="walkthrough-6-deploy-your-windows-containers-based-apps-to-azure-app-service-for-containers"></a><span data-ttu-id="c2284-273">Návod 6: Nasazení aplikace založené na kontejnery Windows do Azure App Service pro kontejnery</span><span class="sxs-lookup"><span data-stu-id="c2284-273">Walkthrough 6: Deploy your Windows Containers-based apps to Azure App Service for Containers</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="c2284-274">Dostupnost průvodcem produktem</span><span class="sxs-lookup"><span data-stu-id="c2284-274">Technical walkthrough availability</span></span>

<span data-ttu-id="c2284-275">Je k dispozici v wiki úložiště GitHub eShopModernizing plnou technickou názorný postup:</span><span class="sxs-lookup"><span data-stu-id="c2284-275">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki:</span></span>

<https://github.com/dotnet-architecture/eShopModernizing/wiki/Deploy-Windows-Container-to-Azure-App-Service>

### <a name="overview"></a><span data-ttu-id="c2284-276">Přehled</span><span class="sxs-lookup"><span data-stu-id="c2284-276">Overview</span></span>

<span data-ttu-id="c2284-277">Jednoduché kontejnerizované aplikace pomocí kontejnerů Windows je možné snadno nasadit do služby Azure App Service pro kontejnery.</span><span class="sxs-lookup"><span data-stu-id="c2284-277">A simple containerized application using Windows Containers can easily be deployed to Azure App Service for Containers.</span></span> <span data-ttu-id="c2284-278">Toto je doporučený postup pro většinu aplikací založených na kontejnerech Windows.</span><span class="sxs-lookup"><span data-stu-id="c2284-278">This is the recommended approach for most Windows Container-based applications.</span></span>

### <a name="goals"></a><span data-ttu-id="c2284-279">Cíle</span><span class="sxs-lookup"><span data-stu-id="c2284-279">Goals</span></span>

<span data-ttu-id="c2284-280">Cílem tohoto návodu je naučit se nasazovat aplikace založené na kontejneru Windows do Azure App Service pro kontejnery z registru (Docker Hubu nebo služby Azure Container Registry).</span><span class="sxs-lookup"><span data-stu-id="c2284-280">The goal of this walkthrough is to learn how to deploy a Windows Container–based application to Azure App Service for Containers from a registry (Docker Hub or Azure Container Registry).</span></span>

### <a name="scenario"></a><span data-ttu-id="c2284-281">Scénář</span><span class="sxs-lookup"><span data-stu-id="c2284-281">Scenario</span></span>

![Nasazení aplikace založené na kontejnerech Windows do Azure App Service pro kontejnery](./media/image5-11.png)

### <a name="benefits"></a><span data-ttu-id="c2284-283">Výhody</span><span class="sxs-lookup"><span data-stu-id="c2284-283">Benefits</span></span>

<span data-ttu-id="c2284-284">Nasazení do služby Azure App Service pro kontejnery nabízí výhody kontejnerů spárovat s výhodami Azure App Service nabízí PaaS.</span><span class="sxs-lookup"><span data-stu-id="c2284-284">Deploying to Azure App Service for Containers offers the benefits of containers paired with the PaaS benefits of Azure App Service.</span></span> <span data-ttu-id="c2284-285">Služby app service je možné snadno škálovat vertikální i horizontální a dá se k automatickému škálování s cílem splnit měnící požadavky.</span><span class="sxs-lookup"><span data-stu-id="c2284-285">The app service can easily be scaled both vertically and horizontally, and can be configured to autoscale to meet changing demands.</span></span> <span data-ttu-id="c2284-286">Aktualizací je možné provést s nulovými výpadky a konfiguraci průběžného nasazování z registru se snadno konfigurovat také.</span><span class="sxs-lookup"><span data-stu-id="c2284-286">Updates can be performed with zero downtime and configuration of continuous deployment from a registry is easily configured as well.</span></span>

## <a name="next-steps"></a><span data-ttu-id="c2284-287">Další kroky</span><span class="sxs-lookup"><span data-stu-id="c2284-287">Next steps</span></span>

<span data-ttu-id="c2284-288">Tento obsah podrobnější zkoumání na Wiki úložiště GitHub: <https://github.com/dotnet-architecture/eShopModernizing/wiki/Deploy-Windows-Container-to-Azure-App-Service></span><span class="sxs-lookup"><span data-stu-id="c2284-288">Explore this content more in-depth on the GitHub wiki: <https://github.com/dotnet-architecture/eShopModernizing/wiki/Deploy-Windows-Container-to-Azure-App-Service></span></span>

> [!div class="step-by-step"]
> <span data-ttu-id="c2284-289">[Předchozí](lift-and-shift-existing-apps-devops/migrate-to-hybrid-cloud-scenarios.md)
> [další](conclusions.md)</span><span class="sxs-lookup"><span data-stu-id="c2284-289">[Previous](lift-and-shift-existing-apps-devops/migrate-to-hybrid-cloud-scenarios.md)
[Next](conclusions.md)</span></span>
