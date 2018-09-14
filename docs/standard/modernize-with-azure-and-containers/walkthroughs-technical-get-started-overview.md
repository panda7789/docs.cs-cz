---
title: Návody a technický přehled Začínáme
description: Modernizace stávajících aplikací .NET pomocí cloudu Azure a kontejnery Windows | Návody a technický přehled Začínáme
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/28/2018
ms.openlocfilehash: 41fbeb3abc201ef03cf0c237a069e7687c98dd18
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/14/2018
ms.locfileid: "45594008"
---
# <a name="walkthroughs-and-technical-get-started-overview"></a><span data-ttu-id="6183a-103">Návody a technický přehled Začínáme</span><span class="sxs-lookup"><span data-stu-id="6183a-103">Walkthroughs and technical get started overview</span></span>

<span data-ttu-id="6183a-104">Omezení velikosti tuto elektronickou příručku, další technickou dokumentaci a úplné názorné postupy byly k dispozici v úložišti GitHub.</span><span class="sxs-lookup"><span data-stu-id="6183a-104">To limit the size of this e-book, additional technical documentation and the full walkthroughs were made available in a GitHub repository.</span></span> <span data-ttu-id="6183a-105">Online řada návodů, který je popsaný v této kapitole zahrnuje podrobné nastavení více prostředí, které jsou založeny na kontejnery Windows a nasazení do Azure.</span><span class="sxs-lookup"><span data-stu-id="6183a-105">The online series of walkthroughs that is described in this chapter covers the step-by-step setup of the multiple environments that are based on Windows Containers, and deployment to Azure.</span></span>

<span data-ttu-id="6183a-106">Následující části popisují, co každého návodu je o cílech a vysoké úrovně pro zpracování obrazu a poskytuje diagramu úloh, které jsou zahrnuty.</span><span class="sxs-lookup"><span data-stu-id="6183a-106">The following sections explain what each walkthrough is about, its objectives and high-level vision, and provides a diagram of the tasks that are involved.</span></span> <span data-ttu-id="6183a-107">Můžete získat návody sami v *eShopModernizing* wiki úložiště GitHub aplikace na [ https://github.com/dotnet-architecture/eShopModernizing/wiki ](https://github.com/dotnet-architecture/eShopModernizing/wiki).</span><span class="sxs-lookup"><span data-stu-id="6183a-107">You can get the walkthroughs themselves in the *eShopModernizing* apps GitHub repo wiki at [https://github.com/dotnet-architecture/eShopModernizing/wiki](https://github.com/dotnet-architecture/eShopModernizing/wiki).</span></span>

## <a name="technical-walkthrough-list"></a><span data-ttu-id="6183a-108">Seznam průvodcem produktem</span><span class="sxs-lookup"><span data-stu-id="6183a-108">Technical walkthrough list</span></span>

<span data-ttu-id="6183a-109">Následující návody pro get-started poskytují komplexní a konzistentní technické pokyny pro ukázkové aplikace, které můžete přenést a shift pomocí kontejnerů a přesuňte pomocí několika možností nasazení v Azure.</span><span class="sxs-lookup"><span data-stu-id="6183a-109">The following get-started walkthroughs provide consistent and comprehensive technical guidance for sample apps that you can lift and shift by using containers, and then move by using multiple deployment choices in Azure.</span></span>

<span data-ttu-id="6183a-110">Každá z následujících návodech používá nové ukázkové eShopLegacy a eShopModernizing aplikace, které jsou k dispozici na Githubu v [ https://github.com/dotnet-architecture/eShopModernizing ](https://github.com/dotnet-architecture/eShopModernizing).</span><span class="sxs-lookup"><span data-stu-id="6183a-110">Each of the following walkthroughs uses the new sample eShopLegacy and eShopModernizing apps, which are available on GitHub at [https://github.com/dotnet-architecture/eShopModernizing](https://github.com/dotnet-architecture/eShopModernizing).</span></span>

- <span data-ttu-id="6183a-111">**Prohlídka eShop starší verze aplikací (aplikace pro směrný plán pro modernizaci)**</span><span class="sxs-lookup"><span data-stu-id="6183a-111">**Tour of eShop legacy apps (baseline apps to modernize)**</span></span>

- <span data-ttu-id="6183a-112">**Kontejnerizace existující webových aplikací ASP.NET (WebForms & MVC) s kontejnery Windows**</span><span class="sxs-lookup"><span data-stu-id="6183a-112">**Containerize your existing ASP.NET web apps (WebForms & MVC) with Windows Containers**</span></span>

- <span data-ttu-id="6183a-113">**Kontejnerizovat stávající službu WCF (aplikace pro N-vrstvá) s kontejnery Windows**</span><span class="sxs-lookup"><span data-stu-id="6183a-113">**Containerize your existing WCF services (N-Tier apps) with Windows Containers**</span></span>

- <span data-ttu-id="6183a-114">**Nasazení aplikace založené na kontejnery Windows na virtuálních počítačích Azure**</span><span class="sxs-lookup"><span data-stu-id="6183a-114">**Deploy your Windows Containers-based app to Azure VMs**</span></span>

- <span data-ttu-id="6183a-115">**Nasazení aplikací na základě kontejnerů Windows v Kubernetes ve službě Azure Container Service**</span><span class="sxs-lookup"><span data-stu-id="6183a-115">**Deploy your Windows Containers-based apps to Kubernetes in Azure Container Service**</span></span>

- <span data-ttu-id="6183a-116">**Nasazení aplikace založené na kontejnery Windows do Azure Service Fabric**</span><span class="sxs-lookup"><span data-stu-id="6183a-116">**Deploy your Windows Containers-based apps to Azure Service Fabric**</span></span>


## <a name="walkthrough-1-tour-of-eshop-legacy-apps"></a><span data-ttu-id="6183a-117">Návod 1: Prohlídka eShop starší verze aplikací</span><span class="sxs-lookup"><span data-stu-id="6183a-117">Walkthrough 1: Tour of eShop legacy apps</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="6183a-118">Dostupnost průvodcem produktem</span><span class="sxs-lookup"><span data-stu-id="6183a-118">Technical walkthrough availability</span></span>

<span data-ttu-id="6183a-119">Je k dispozici v wiki úložiště GitHub eShopModernizing plnou technickou názorný postup:</span><span class="sxs-lookup"><span data-stu-id="6183a-119">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki:</span></span>

[<span data-ttu-id="6183a-120">návody eShopModernizing wiki</span><span class="sxs-lookup"><span data-stu-id="6183a-120">eShopModernizing wiki walkthroughs</span></span>](https://github.com/dotnet-architecture/eShopModernizing/wiki)


### <a name="overview"></a><span data-ttu-id="6183a-121">Přehled</span><span class="sxs-lookup"><span data-stu-id="6183a-121">Overview</span></span>

<span data-ttu-id="6183a-122">V tomto podrobném návodu můžete prozkoumat počáteční implementace tři ukázkové starší verze aplikace.</span><span class="sxs-lookup"><span data-stu-id="6183a-122">In this walkthrough, you can explore the initial implementation of three sample legacy applications.</span></span> <span data-ttu-id="6183a-123">První dva ukázkové webové aplikace mají monolitické architektury a byly vytvořeny pomocí klasického rozhraní ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="6183a-123">The first two sample web apps have a monolithic architecture, and were created by using classic ASP.NET.</span></span> <span data-ttu-id="6183a-124">Jedna aplikace je založena na technologii ASP.NET 4.x MVC; Druhá aplikace je založena na webových formulářů ASP.NET 4.x.</span><span class="sxs-lookup"><span data-stu-id="6183a-124">One application is based on ASP.NET 4.x MVC; the second application is based on ASP.NET 4.x Web Forms.</span></span> <span data-ttu-id="6183a-125">Třetí aplikace je 3vrstvé aplikace skládající se tak, že klientská aplikace WinForms a na straně serveru [Windows Communication Foundation (WCF)](../../framework/wcf/whats-wcf.md) služby.</span><span class="sxs-lookup"><span data-stu-id="6183a-125">The third app is a 3-Tier app composed by a client WinForms app and a server-side [Windows Communication Foundation (WCF)](../../framework/wcf/whats-wcf.md) service.</span></span>

<span data-ttu-id="6183a-126">Všechny tyto aplikace jsou k dispozici na [úložiště GitHub eShopModernizing](https://github.com/dotnet-architecture/eShopModernizing).</span><span class="sxs-lookup"><span data-stu-id="6183a-126">All these applications are available at the [eShopModernizing GitHub repo](https://github.com/dotnet-architecture/eShopModernizing).</span></span>

### <a name="goals"></a><span data-ttu-id="6183a-127">Cíle</span><span class="sxs-lookup"><span data-stu-id="6183a-127">Goals</span></span>

<span data-ttu-id="6183a-128">Hlavním cílem tohoto návodu je jednoduše a seznamte se s těmito aplikacemi a s jejich kódu a konfigurace.</span><span class="sxs-lookup"><span data-stu-id="6183a-128">The main goal of this walkthrough is simply to get familiar with these apps, and with their code and configuration.</span></span> <span data-ttu-id="6183a-129">Aplikace můžete nakonfigurovat tak, aby generovat a používat mock data bez použití databáze SQL pro účely testování.</span><span class="sxs-lookup"><span data-stu-id="6183a-129">You can configure the apps so that they generate and use mock data, without using the SQL database, for testing purposes.</span></span> <span data-ttu-id="6183a-130">Tato volitelná konfigurace je založen na vkládání závislostí oddělující způsobem.</span><span class="sxs-lookup"><span data-stu-id="6183a-130">This optional config is based on dependency injection, in a decoupled way.</span></span>

### <a name="scenario-1-aspnet-web-apps"></a><span data-ttu-id="6183a-131">Scénář 1: Webových aplikací ASP.NET</span><span class="sxs-lookup"><span data-stu-id="6183a-131">Scenario 1: ASP.NET Web apps</span></span>

<span data-ttu-id="6183a-132">Následující obrázek znázorňuje jednoduchý scénář původní starší verze webových aplikací ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="6183a-132">The figure below shows the simple scenario of the original legacy ASP.NET web applications.</span></span>

> ![Jednoduchá architektura scénář původní starší verze webových aplikací ASP.NET](./media/image5-1.png)
>

<span data-ttu-id="6183a-134">Z hlediska domény firmy obě aplikace nabízejí katalogu stejné funkce pro správu.</span><span class="sxs-lookup"><span data-stu-id="6183a-134">From a business domain perspective, both apps offer the same catalog management features.</span></span> <span data-ttu-id="6183a-135">Členové týmu enterprise eShop využije aplikace k zobrazení a úprava katalog produktů.</span><span class="sxs-lookup"><span data-stu-id="6183a-135">Members of the eShop enterprise team would use the app to view and edit the product catalog.</span></span> 

<span data-ttu-id="6183a-136">Následující obrázek ukazuje na snímcích obrazovky počáteční aplikace.</span><span class="sxs-lookup"><span data-stu-id="6183a-136">The next figure shows the initial app screenshots.</span></span>

![Aplikace ASP.NET MVC a ASP.NET Web Forms (technologie existující/starší verze)](./media/image5-2.png)

<span data-ttu-id="6183a-138">Závislosti v technologii ASP.NET 4.x a předchozími verzemi (buď pro MVC nebo pro webové formuláře) znamená, že se tyto aplikace nespustí v rozhraní .NET Core, pokud kód je úplně přepsán pomocí ASP.NET Core MVC.</span><span class="sxs-lookup"><span data-stu-id="6183a-138">Dependencies in ASP.NET 4.x or earlier versions (either for MVC or for Web Forms) means that these applications won’t run on .NET Core unless the code is fully rewritten by using ASP.NET Core MVC.</span></span> 

### <a name="scenario-2-wcf-service-and-winforms-client-app-3-tier-app"></a><span data-ttu-id="6183a-139">Scénář 2: Službu WCF a WinForms klientské aplikace (3vrstvé aplikace)</span><span class="sxs-lookup"><span data-stu-id="6183a-139">Scenario 2: WCF service and WinForms client app (3-Tier app)</span></span>

<span data-ttu-id="6183a-140">Následující obrázek znázorňuje jednoduchý scénář původní 3vrstvá starší verze aplikace.</span><span class="sxs-lookup"><span data-stu-id="6183a-140">The figure below shows the simple scenario of the original 3-Tier legacy application.</span></span>

> ![Jednoduchá architektura scénář být vybavené klientskou aplikací WinForms a původní starší verze 3vrstvé aplikace se službou WCF](./media/image5-1.5.png)
>

### <a name="benefits"></a><span data-ttu-id="6183a-142">Výhody</span><span class="sxs-lookup"><span data-stu-id="6183a-142">Benefits</span></span>

<span data-ttu-id="6183a-143">Výhody tohoto názorného postupu jsou jednoduché: stačí Seznamte se s kódem a počáteční aplikace.</span><span class="sxs-lookup"><span data-stu-id="6183a-143">The benefits of this walkthrough are simple: Just get familiar with the code and initial apps.</span></span>

### <a name="next-steps"></a><span data-ttu-id="6183a-144">Další kroky</span><span class="sxs-lookup"><span data-stu-id="6183a-144">Next steps</span></span>

<span data-ttu-id="6183a-145">Tento obsah podrobnější zkoumání na Wiki úložiště GitHub:</span><span class="sxs-lookup"><span data-stu-id="6183a-145">Explore this content more in-depth on the GitHub wiki:</span></span>

  - [<span data-ttu-id="6183a-146">Prohlídka na základní technologie ASP.NET MVC a aplikace webových formulářů "starší"</span><span class="sxs-lookup"><span data-stu-id="6183a-146">Tour on the baseline ASP.NET MVC and Web Forms “legacy” apps</span></span>](https://github.com/dotnet-architecture/eShopModernizing/wiki/01.-Tour-on-the-ASP.NET-MVC-and-WebForms-apps-implementation-code)
  - [<span data-ttu-id="6183a-147">Prohlídka na aplikace WinForms v "starší" (3 vrstvy) a služby WCF směrného plánu</span><span class="sxs-lookup"><span data-stu-id="6183a-147">Tour on the baseline WCF service and WinForms (3-Tier) “legacy” app</span></span>](https://github.com/dotnet-architecture/eShopModernizing/wiki/21.-Tour-on-the-WCF-service-and-WinForms-apps)


## <a name="walkthrough-2-containerize-your-existing-net-applications-with-windows-containers"></a><span data-ttu-id="6183a-148">Návod 2: Kontejnerizace existující aplikace .NET s kontejnery Windows</span><span class="sxs-lookup"><span data-stu-id="6183a-148">Walkthrough 2: Containerize your existing .NET applications with Windows Containers</span></span>

### <a name="overview"></a><span data-ttu-id="6183a-149">Přehled</span><span class="sxs-lookup"><span data-stu-id="6183a-149">Overview</span></span>

<span data-ttu-id="6183a-150">Kontejnery Windows použijte ke zlepšení nasazení existujících aplikací .NET, jako jsou systémy založené na MVC, webových formulářů nebo WCF, do produkčního prostředí, vývojová a testovací prostředí.</span><span class="sxs-lookup"><span data-stu-id="6183a-150">Use Windows Containers to improve deployment of existing .NET applications, like those based on MVC, Web Forms, or WCF, to production, development, and test environments.</span></span>

### <a name="goals"></a><span data-ttu-id="6183a-151">Cíle</span><span class="sxs-lookup"><span data-stu-id="6183a-151">Goals</span></span>

<span data-ttu-id="6183a-152">Cílem tohoto návodu je zobrazit několik možností pro uzavření do kontejneru existující aplikaci .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="6183a-152">The goal of this walkthrough is to show you several options for containerizing an existing .NET Framework application.</span></span> <span data-ttu-id="6183a-153">Můžeš:</span><span class="sxs-lookup"><span data-stu-id="6183a-153">You can:</span></span>

- <span data-ttu-id="6183a-154">Kontejnerizujte své aplikace pomocí [Visual Studio 2017 Tools for Docker](/aspnet/core/host-and-deploy/docker/visual-studio-tools-for-docker) (Visual Studio 2017 nebo novější verze).</span><span class="sxs-lookup"><span data-stu-id="6183a-154">Containerize your application by using [Visual Studio 2017 Tools for Docker](/aspnet/core/host-and-deploy/docker/visual-studio-tools-for-docker) (Visual Studio 2017 or later versions).</span></span>

- <span data-ttu-id="6183a-155">Kontejnerizujte své aplikace tak, že ručně přidáte [soubor Dockerfile](https://docs.docker.com/engine/reference/builder/)a následným použitím [rozhraní příkazového řádku Dockeru](https://docs.docker.com/engine/reference/commandline/cli/).</span><span class="sxs-lookup"><span data-stu-id="6183a-155">Containerize your application by manually adding a [Dockerfile](https://docs.docker.com/engine/reference/builder/), and then using the [Docker CLI](https://docs.docker.com/engine/reference/commandline/cli/).</span></span>

- <span data-ttu-id="6183a-156">Kontejnerizujte své aplikace pomocí [Img2Docker](https://github.com/docker/communitytools-image2docker-win) nástroje (nástroj open source od Dockeru).</span><span class="sxs-lookup"><span data-stu-id="6183a-156">Containerize your application by using the [Img2Docker](https://github.com/docker/communitytools-image2docker-win) tool (an open-source tool from Docker).</span></span>

<span data-ttu-id="6183a-157">Tento návod se zaměřuje na Visual Studio 2017 Tools for Docker přístup, ale ostatní dva přístupy jsou podobné ve vztahu pomocí soubory Dockerfile.</span><span class="sxs-lookup"><span data-stu-id="6183a-157">This walkthrough focuses on the Visual Studio 2017 Tools for Docker approach, but the other two approaches are fairly similar in regard to using Dockerfiles.</span></span>

### <a name="scenario-1-containerized-aspnet-web-apps"></a><span data-ttu-id="6183a-158">Scénář 1: ASP.NET Kontejnerizovaných webových aplikací</span><span class="sxs-lookup"><span data-stu-id="6183a-158">Scenario 1: Containerized ASP.NET web apps</span></span>

<span data-ttu-id="6183a-159">Následující obrázek znázorňuje scénář pro kontejnerizované eShop starší verze webové aplikace aplikace.</span><span class="sxs-lookup"><span data-stu-id="6183a-159">Figure below shows the scenario for containerized eShop legacy web apps applications.</span></span>

> ![Diagram architektury zjednodušené kontejnerizovaných aplikací technologie ASP.NET ve vývojovém prostředí](./media/image5-3.png)
>


### <a name="scenario-2-containerized-wcf-service"></a><span data-ttu-id="6183a-161">Scénář 2: Služba kontejnerizovaná WCF</span><span class="sxs-lookup"><span data-stu-id="6183a-161">Scenario 2: Containerized WCF service</span></span>

<span data-ttu-id="6183a-162">Následující obrázek znázorňuje scénář 3vrstvé aplikace s kontejnerizovaná služba WCF.</span><span class="sxs-lookup"><span data-stu-id="6183a-162">Figure below shows the scenario for a 3-Tier app with a containerized WCF service.</span></span> 

> ![Zjednodušená diagram architektury kontejnerizované služby WCF ve vývojovém prostředí](./media/image5-3.5.png)
>

### <a name="benefits"></a><span data-ttu-id="6183a-164">Výhody</span><span class="sxs-lookup"><span data-stu-id="6183a-164">Benefits</span></span>

<span data-ttu-id="6183a-165">Existují výhody používání monolitické aplikace v kontejneru.</span><span class="sxs-lookup"><span data-stu-id="6183a-165">There are advantages to running your monolithic application in a container.</span></span> <span data-ttu-id="6183a-166">Nejprve vytvořte image pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="6183a-166">First, you create an image for the application.</span></span> <span data-ttu-id="6183a-167">Od tohoto okamžiku v každé nasazení běží ve stejném prostředí.</span><span class="sxs-lookup"><span data-stu-id="6183a-167">From that point on, every deployment runs in the same environment.</span></span> <span data-ttu-id="6183a-168">Každý kontejner používá stejnou verzi operačního systému, má stejnou verzi závislosti nainstalované, používá stejnou verzi rozhraní .NET framework a je vytvořena pomocí stejného procesu.</span><span class="sxs-lookup"><span data-stu-id="6183a-168">Every container uses the same OS version, has the same version of dependencies installed, uses the same .NET framework version, and is built by using the same process.</span></span> <span data-ttu-id="6183a-169">V podstatě řízení závislostí vaší aplikace pomocí image Dockeru.</span><span class="sxs-lookup"><span data-stu-id="6183a-169">Basically, you control the dependencies of your application by using a Docker image.</span></span> <span data-ttu-id="6183a-170">Závislosti cestují s aplikací při nasazování kontejnerů.</span><span class="sxs-lookup"><span data-stu-id="6183a-170">The dependencies travel with the application when you deploy the containers.</span></span>

<span data-ttu-id="6183a-171">Další výhodou je, že vývojáři spuštěním aplikace v prostředí konzistentní vzhledem k aplikacím, které poskytuje kontejnery Windows.</span><span class="sxs-lookup"><span data-stu-id="6183a-171">An additional benefit is that developers can run the application in the consistent environment that's provided by Windows Containers.</span></span> <span data-ttu-id="6183a-172">Problémy, které se zobrazují pouze u některých verzí můžete okamžitě, nanese místo zpřístupnění v přípravném nebo produkčním prostředí.</span><span class="sxs-lookup"><span data-stu-id="6183a-172">Issues that appear only with certain versions can be spotted immediately, instead of surfacing in a staging or production environment.</span></span> <span data-ttu-id="6183a-173">Rozdíly ve vývojovém prostředí, které používají členové vývojového týmu méně důležitá, když aplikace běží v kontejnerech.</span><span class="sxs-lookup"><span data-stu-id="6183a-173">Differences in development environments used by members of the development team matter less when applications run in containers.</span></span>

<span data-ttu-id="6183a-174">Kontejnerizované aplikace také mít plošší křivky horizontální navýšení kapacity.</span><span class="sxs-lookup"><span data-stu-id="6183a-174">Containerized applications also have a flatter scale-out curve.</span></span> <span data-ttu-id="6183a-175">Kontejnerizovaných aplikací umožňují další aplikace a instance služby (podle kontejnerů) virtuálního počítače nebo fyzického počítače, ve srovnání s nasazení aplikace pravidelně na počítač.</span><span class="sxs-lookup"><span data-stu-id="6183a-175">Containerized apps enable you to have more application and service instances (based on containers) in a VM or physical machine compared to regular application deployments per machine.</span></span> <span data-ttu-id="6183a-176">Výsledkem je vyšší hustota a méně požadované prostředky, zejména v případě, že používáte orchestrátorů, jako je Kubernetes nebo Service Fabric.</span><span class="sxs-lookup"><span data-stu-id="6183a-176">This translates to higher density and fewer required resources, especially when you use orchestrators like Kubernetes or Service Fabric.</span></span>

<span data-ttu-id="6183a-177">Kontejnerizace v situacích, ideální, nevyžaduje změny kódu aplikace (C\#).</span><span class="sxs-lookup"><span data-stu-id="6183a-177">Containerization, in ideal situations, does not require making any changes to the application code (C\#).</span></span> <span data-ttu-id="6183a-178">Ve většině případů stačí Docker nasazení metadat souborů (soubory Dockerfile a Docker Compose soubory).</span><span class="sxs-lookup"><span data-stu-id="6183a-178">In most scenarios, you just need the Docker deployment metadata files (Dockerfiles and Docker Compose files).</span></span>

### <a name="next-steps"></a><span data-ttu-id="6183a-179">Další kroky</span><span class="sxs-lookup"><span data-stu-id="6183a-179">Next steps</span></span>

<span data-ttu-id="6183a-180">Tento obsah podrobnější zkoumání na Wiki úložiště GitHub:</span><span class="sxs-lookup"><span data-stu-id="6183a-180">Explore this content more in-depth on the GitHub wiki:</span></span>

  - [<span data-ttu-id="6183a-181">Jak kontejnerizovat aplikace webového rozhraní .NET Framework s kontejnery Windows a Dockeru</span><span class="sxs-lookup"><span data-stu-id="6183a-181">How to containerize the .NET Framework web apps with Windows Containers and Docker</span></span>](https://github.com/dotnet-architecture/eShopModernizing/wiki/02.-How-to-containerize-the-.NET-Framework-web-apps-with-Windows-Containers-and-Docker)
  - [<span data-ttu-id="6183a-182">Přidání podpory Dockeru do služby WCF</span><span class="sxs-lookup"><span data-stu-id="6183a-182">Adding Docker Support to a WCF service</span></span>](https://github.com/dotnet-architecture/eShopModernizing/wiki/22.-Adding-Docker-Support)



## <a name="walkthrough-3-deploy-your-windows-containers-based-app-to-azure-vms"></a><span data-ttu-id="6183a-183">Návod 3: Nasazení aplikace založené na kontejnery Windows na virtuálních počítačích Azure</span><span class="sxs-lookup"><span data-stu-id="6183a-183">Walkthrough 3: Deploy your Windows Containers-based app to Azure VMs</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="6183a-184">Dostupnost průvodcem produktem</span><span class="sxs-lookup"><span data-stu-id="6183a-184">Technical walkthrough availability</span></span>

<span data-ttu-id="6183a-185">Je k dispozici v wiki úložiště GitHub eShopModernizing plnou technickou názorný postup: [https://github.com/dotnet-architecture/eShopModernizing/wiki/03.-How-to-deploy-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/03.-How-to-deploy-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD))</span><span class="sxs-lookup"><span data-stu-id="6183a-185">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki: [https://github.com/dotnet-architecture/eShopModernizing/wiki/03.-How-to-deploy-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/03.-How-to-deploy-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD))</span></span>

### <a name="overview"></a><span data-ttu-id="6183a-186">Přehled</span><span class="sxs-lookup"><span data-stu-id="6183a-186">Overview</span></span>

<span data-ttu-id="6183a-187">Nasazení na hostitele Docker na Windows serveru 2016 virtuálního počítače (počítače) v Azure umožňuje rychle nastavit vývojové/testovací/přípravných prostředí.</span><span class="sxs-lookup"><span data-stu-id="6183a-187">Deploying to a Docker host on a Windows Server 2016 Virtual Machine (VM) in Azure lets you quickly set up development/test/staging environments.</span></span> <span data-ttu-id="6183a-188">Také poskytuje společné místo pro testery nebo firemním uživatelům ověřovat aplikace.</span><span class="sxs-lookup"><span data-stu-id="6183a-188">It also gives you a common place for testers or business users to validate the app.</span></span> <span data-ttu-id="6183a-189">Virtuální počítač také může být platný cenu jako služba (IaaS) produkční prostředí.</span><span class="sxs-lookup"><span data-stu-id="6183a-189">VMs also can be valid Infrastucture as a Service (IaaS) production environments.</span></span>

### <a name="goals"></a><span data-ttu-id="6183a-190">Cíle</span><span class="sxs-lookup"><span data-stu-id="6183a-190">Goals</span></span>

<span data-ttu-id="6183a-191">Cílem tohoto návodu je zobrazit více alternativy, které jste při nasazování kontejnerů Windows na virtuální počítače Azure, které jsou založené na Windows Server 2016 nebo novější verze.</span><span class="sxs-lookup"><span data-stu-id="6183a-191">The goal of this walkthrough is to show you the multiple alternatives you have when you deploy Windows Containers to Azure VMs that are based on Windows Server 2016 or later versions.</span></span>

### <a name="scenarios"></a><span data-ttu-id="6183a-192">Scénáře</span><span class="sxs-lookup"><span data-stu-id="6183a-192">Scenarios</span></span>

<span data-ttu-id="6183a-193">Několik scénáře jsou popsané v tomto názorném postupu.</span><span class="sxs-lookup"><span data-stu-id="6183a-193">Several scenarios are covered in this walkthrough.</span></span>

#### <a name="scenario-a-deploy-to-an-azure-vm-from-a-dev-pc-through-docker-engine-connection"></a><span data-ttu-id="6183a-194">Scénář A: nasazení na Virtuálním počítači Azure z vývojář počítače přes připojení modul Docker</span><span class="sxs-lookup"><span data-stu-id="6183a-194">Scenario A: Deploy to an Azure VM from a dev PC through Docker Engine connection</span></span>

![Nasazení na Virtuálním počítači Azure z vývojář PC prostřednictvím připojení k modulu Docker](./media/image5-4.png)

> <span data-ttu-id="6183a-196">**Obrázek 5 – 4.**</span><span class="sxs-lookup"><span data-stu-id="6183a-196">**Figure 5-4.**</span></span> <span data-ttu-id="6183a-197">Nasazení na Virtuálním počítači Azure z vývojář PC prostřednictvím připojení k modulu Docker</span><span class="sxs-lookup"><span data-stu-id="6183a-197">Deploy to an Azure VM from a dev PC through a Docker Engine connection</span></span>

#### <a name="scenario-b-deploy-to-an-azure-vm-through-a-docker-registry"></a><span data-ttu-id="6183a-198">Scénář B: nasazení na Virtuálním počítači Azure pomocí registru Dockeru</span><span class="sxs-lookup"><span data-stu-id="6183a-198">Scenario B: Deploy to an Azure VM through a Docker Registry</span></span>

![Nasazení do virtuálního počítače Azure pomocí registru Dockeru](./media/image5-5.png)

> <span data-ttu-id="6183a-200">**Obrázek 5 – 5.**</span><span class="sxs-lookup"><span data-stu-id="6183a-200">**Figure 5-5.**</span></span> <span data-ttu-id="6183a-201">Nasazení do virtuálního počítače Azure pomocí registru Dockeru</span><span class="sxs-lookup"><span data-stu-id="6183a-201">Deploy to an Azure VM through a Docker Registry</span></span>

#### <a name="scenario-c-deploy-to-an-azure-vm-from-cicd-pipelines-in-azure-devops-services"></a><span data-ttu-id="6183a-202">Scénář C: nasazení na Virtuálním počítači Azure z kanálů CI/CD ve službách Azure DevOps</span><span class="sxs-lookup"><span data-stu-id="6183a-202">Scenario C: Deploy to an Azure VM from CI/CD pipelines in Azure DevOps Services</span></span>

![Nasazení na Virtuálním počítači Azure z kanálů CI/CD ve službách Azure DevOps](./media/image5-6.png)

> <span data-ttu-id="6183a-204">**Obrázek 5 a 6.**</span><span class="sxs-lookup"><span data-stu-id="6183a-204">**Figure 5-6.**</span></span> <span data-ttu-id="6183a-205">Nasazení na Virtuálním počítači Azure z kanálů CI/CD ve službách Azure DevOps</span><span class="sxs-lookup"><span data-stu-id="6183a-205">Deploy to an Azure VM from CI/CD pipelines in Azure DevOps Services</span></span>

### <a name="azure-vms-for-windows-containers"></a><span data-ttu-id="6183a-206">Virtuální počítače Azure pro kontejnery Windows</span><span class="sxs-lookup"><span data-stu-id="6183a-206">Azure VMs for Windows Containers</span></span>

<span data-ttu-id="6183a-207">Virtuální počítače pro Windows kontejnery služby Azure jsou virtuálních počítačů založených na Windows serveru 2016, Windows 10 nebo novější verze, s modul Docker nastavení.</span><span class="sxs-lookup"><span data-stu-id="6183a-207">Azure VMs for Windows Containers are VMs based on Windows Server 2016, Windows 10, or later versions, both with Docker Engine set up.</span></span> <span data-ttu-id="6183a-208">Ve většině případů se používá Windows Server 2016 ve virtuálních počítačích Azure.</span><span class="sxs-lookup"><span data-stu-id="6183a-208">In most cases, Windows Server 2016 is used in the Azure VMs.</span></span>

<span data-ttu-id="6183a-209">Azure v současné době poskytuje virtuální počítač s názvem **Windows serveru 2016 s kontejnery**.</span><span class="sxs-lookup"><span data-stu-id="6183a-209">Azure currently provides a VM named **Windows Server 2016 with Containers**.</span></span> <span data-ttu-id="6183a-210">Tento virtuální počítač můžete vyzkoušet nové funkce kontejneru Windows serveru s Windows Server Core nebo Windows Nano Server.</span><span class="sxs-lookup"><span data-stu-id="6183a-210">You can use this VM to try the new Windows Server Container feature, with either Windows Server Core or Windows Nano Server.</span></span> <span data-ttu-id="6183a-211">Kontejnerové Image operačního systému jsou nainstalovány a pak je virtuální počítač připravený k použití s Dockerem.</span><span class="sxs-lookup"><span data-stu-id="6183a-211">Container OS images are installed, and then the VM is ready to use with Docker.</span></span>

### <a name="benefits"></a><span data-ttu-id="6183a-212">Výhody</span><span class="sxs-lookup"><span data-stu-id="6183a-212">Benefits</span></span>

<span data-ttu-id="6183a-213">I když se dají nasadit kontejnery Windows pro místní Windows Server 2016 virtuální počítače, při nasazování do Azure, budete mít snadný způsob, jak začít s virtuálními počítači kontejneru připravené k použití Windows serveru.</span><span class="sxs-lookup"><span data-stu-id="6183a-213">Although Windows Containers can be deployed to on-premises Windows Server 2016 VMs, when you deploy to Azure, you get an easier way to get started, with ready-to-use Windows Server Container VMs.</span></span> <span data-ttu-id="6183a-214">Získáte také běžné online umístění, která je přístupná pro testery a automatické škálovatelnosti pomocí škálovací sady virtuálních počítačů Azure.</span><span class="sxs-lookup"><span data-stu-id="6183a-214">You also get a common online location that’s accessible to testers, and automatic scalability through Azure virtual machine scale sets.</span></span>

### <a name="next-steps"></a><span data-ttu-id="6183a-215">Další kroky</span><span class="sxs-lookup"><span data-stu-id="6183a-215">Next steps</span></span>

<span data-ttu-id="6183a-216">Tento obsah podrobnější zkoumání na Wiki úložiště GitHub:</span><span class="sxs-lookup"><span data-stu-id="6183a-216">Explore this content more in-depth on the GitHub wiki:</span></span>

[https://github.com/dotnet-architecture/eShopModernizing/wiki/03.-How-to-deploy-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/03.-How-to-deploy-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD))

## <a name="walkthrough-4-deploy-your-windows-containers-based-apps-to-azure-container-instances-aci"></a><span data-ttu-id="6183a-217">Návod 4: Nasazení aplikace založené na kontejnery Windows do služby Azure Container Instances (ACI)</span><span class="sxs-lookup"><span data-stu-id="6183a-217">Walkthrough 4: Deploy your Windows Containers-based apps to Azure Container Instances (ACI)</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="6183a-218">Dostupnost průvodcem produktem</span><span class="sxs-lookup"><span data-stu-id="6183a-218">Technical walkthrough availability</span></span>

<span data-ttu-id="6183a-219">Je k dispozici v wiki úložiště GitHub eShopModernizing plnou technickou názorný postup:</span><span class="sxs-lookup"><span data-stu-id="6183a-219">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki:</span></span>

<span data-ttu-id="6183a-220">[Nasazení aplikace do služby ACI (Azure Container Instances)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances))</span><span class="sxs-lookup"><span data-stu-id="6183a-220">[Deploying the Apps to ACI (Azure Container Instances)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances))</span></span>

### <a name="overview"></a><span data-ttu-id="6183a-221">Přehled</span><span class="sxs-lookup"><span data-stu-id="6183a-221">Overview</span></span>

<span data-ttu-id="6183a-222">[Azure Container Instances (ACI)](https://docs.microsoft.com/en-us/azure/container-instances/) je nejrychlejší způsob, jak prostředí dev/test/přípravy kontejnerů, kde můžete nasadit jeden instancí kontejnerů.</span><span class="sxs-lookup"><span data-stu-id="6183a-222">[Azure Container Instances (ACI)](https://docs.microsoft.com/en-us/azure/container-instances/) is the quickest way to have a Containers dev/test/staging environment where you can deploy single instances of containers.</span></span>

### <a name="goals"></a><span data-ttu-id="6183a-223">Cíle</span><span class="sxs-lookup"><span data-stu-id="6183a-223">Goals</span></span>

<span data-ttu-id="6183a-224">Tento návod ukazuje základní scénáře při nasazování kontejnerů Windows do Azure Container Instances (ACI) a jak můžete nasadit aplikace eShopModernizing do ACI.</span><span class="sxs-lookup"><span data-stu-id="6183a-224">This walkthrough shows you the main scenarios when deploying Windows Containers to Azure Container Instances (ACI) and how you can deploy eShopModernizing Apps into ACI.</span></span>

### <a name="scenarios"></a><span data-ttu-id="6183a-225">Scénáře</span><span class="sxs-lookup"><span data-stu-id="6183a-225">Scenarios</span></span>

<span data-ttu-id="6183a-226">Může existovat variace o nasazení aplikací eShopModernizing do ACI, jako je nasazení jenom v jednom nebo všechny aplikace (aplikace MVC, webových formulářů aplikaci nebo službu WCF).</span><span class="sxs-lookup"><span data-stu-id="6183a-226">There can be variations about deploying the eShopModernizing apps into ACI such as deploying just one or all of the apps (MVC app, WebForms app or WCF service).</span></span> <span data-ttu-id="6183a-227">V následujícím scénáři je uvedeno níže můžete vidět aplikaci ASP.NET MVC a kontejner SQL serveru, jejich nasazení jako kontejnery do ACI (Azure Container Instances).</span><span class="sxs-lookup"><span data-stu-id="6183a-227">In the following scenario shown below you can see the ASP.NET MVC app plus the SQL Server container both of them deployed as containers into ACI (Azure Container Instances).</span></span>

![Nasazení do služby ACI z vývojového prostředí](./media/image5-3.5.6.png)

### <a name="benefits"></a><span data-ttu-id="6183a-229">Výhody</span><span class="sxs-lookup"><span data-stu-id="6183a-229">Benefits</span></span>

<span data-ttu-id="6183a-230">Služba Azure Container Instances usnadňuje vytváření a správu kontejnerů Dockeru v Azure, aniž byste museli zřizovat virtuální počítače nebo používat službu.</span><span class="sxs-lookup"><span data-stu-id="6183a-230">Azure Container Instances makes it easy to create and manage Docker containers in Azure, without having to provision virtual machines or adopt a higher-level service.</span></span> <span data-ttu-id="6183a-231">Pomocí ACI můžete přímo nasadit kontejner Windows ve službě Azure a zveřejníte ho na Internetu s použitím plně kvalifikovaného názvu domény (FQDN) v řádu sekund (za předpokladu, že budete mít připravený kontejner Windows image v registru Dockeru jako Docker Hubu nebo služby Azure Container Registru).</span><span class="sxs-lookup"><span data-stu-id="6183a-231">With ACI, you can directly deploy a Windows container in Azure and expose it to the internet with a fully qualified domain name (FQDN) in a matter of seconds (Provided that you have the Windows Container image ready in a Docker registry like Docker Hub or Azure Container Registry).</span></span>

### <a name="considerations"></a><span data-ttu-id="6183a-232">Důležité informace</span><span class="sxs-lookup"><span data-stu-id="6183a-232">Considerations</span></span>

<span data-ttu-id="6183a-233">Nasazování kontejnerů Windows s buď úplné rozhraní .NET Framework / technologie ASP.NET nebo SQL serveru do Azure Container Instances (ACI) není úplně tak rychlý jako při nasazování na regulární hostitele Docker (např. Windows Server 2016 s kontejnery Windows), protože image Dockeru, musí být stažení (načtený z registru Dockeru) pokaždé, když a i když je mnohem levnější než udržování vašeho vlastního hostitele docker (trvale online jsou výrazně velké velikosti image kontejneru SQL (15.1 GB) a image kontejneru ASP.NET (13.9 GB) Windows Server 2016 s virtuálním Počítačem kontejnery Windows v Azure) nemluvě celý orchestrator, jako je Kubernetes v Azure (/ služby AKS ACS) nebo Azure Service Fabric, které jsou na druhé straně skvělou možností pro nasazení v produkčním prostředí.</span><span class="sxs-lookup"><span data-stu-id="6183a-233">Deploying Windows Containers with either full .NET Framework / ASP.NET or SQL Server into Azure Container Instances (ACI) is not quite as fast as deploying to a regular Docker Host (like a Windows Server 2016 with Windows Containers) because the Docker image has to be downloaded (pulled from the Docker registry) every time and the sizes of the SQL container image (15.1 GB) and the ASP.NET container image (13.9 GB) are significantly large, however it is much cheaper than maintaining your own docker host (permanently on-line Windows Server 2016 with Windows Containers VM in Azure) not to mention a whole orchestrator like Kubernetes in Azure (AKS/ACS) or Azure Service Fabric which are, on the other hand, great choices for production deployments.</span></span>

<span data-ttu-id="6183a-234">Jako hlavní uzavření pomocí služby Azure Container Instances je velice přesvědčivý argument možnost pro scénáře vývoje/testování a pro kanály CI/CD.</span><span class="sxs-lookup"><span data-stu-id="6183a-234">As main conclusion, using Azure Container Instances is a very compelling option for Dev/Test scenarios and for CI/CD pipelines.</span></span>

## <a name="next-steps"></a><span data-ttu-id="6183a-235">Další kroky</span><span class="sxs-lookup"><span data-stu-id="6183a-235">Next steps</span></span>

<span data-ttu-id="6183a-236">Tento obsah podrobnější zkoumání na Wiki úložiště GitHub:</span><span class="sxs-lookup"><span data-stu-id="6183a-236">Explore this content more in-depth on the GitHub wiki:</span></span> 

[https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances)TBD)


## <a name="walkthrough-5-deploy-your-windows-containers-based-apps-to-kubernetes-in-azure-container-service"></a><span data-ttu-id="6183a-237">Návod 5: Nasazení aplikací na základě kontejnerů Windows v Kubernetes ve službě Azure Container Service</span><span class="sxs-lookup"><span data-stu-id="6183a-237">Walkthrough 5: Deploy your Windows Containers-based apps to Kubernetes in Azure Container Service</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="6183a-238">Dostupnost průvodcem produktem</span><span class="sxs-lookup"><span data-stu-id="6183a-238">Technical walkthrough availability</span></span>

<span data-ttu-id="6183a-239">Je k dispozici v wiki úložiště GitHub eShopModernizing plnou technickou názorný postup:</span><span class="sxs-lookup"><span data-stu-id="6183a-239">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki:</span></span>

[https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-C-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-C-CD))

### <a name="overview"></a><span data-ttu-id="6183a-240">Přehled</span><span class="sxs-lookup"><span data-stu-id="6183a-240">Overview</span></span>

<span data-ttu-id="6183a-241">Aplikace, která je založena na kontejnery Windows rychle muset použít platformy, přesunutí ještě více pryč z virtuálních počítačů IaaS.</span><span class="sxs-lookup"><span data-stu-id="6183a-241">An application that's based on Windows Containers will quickly need to use platforms, moving even further away from IaaS VMs.</span></span> <span data-ttu-id="6183a-242">To je potřeba provést snadno dosáhnout vysoké škálovatelnosti a lépe automatizované škálovatelnost a přináší značné vylepšení v automatické nasazení a správy verzí.</span><span class="sxs-lookup"><span data-stu-id="6183a-242">This is needed to easily achieve high scalability and better automated scalability, and for a significant improvement in automated deployments and versioning.</span></span> <span data-ttu-id="6183a-243">Tyto cíle lze dosáhnout pomocí orchestrátoru [Kubernetes](https://kubernetes.io/), která je dostupná v [služby Azure Container Service](https://azure.microsoft.com/services/container-service/).</span><span class="sxs-lookup"><span data-stu-id="6183a-243">You can achieve these goals by using the orchestrator [Kubernetes](https://kubernetes.io/), available in [Azure Container Services](https://azure.microsoft.com/services/container-service/).</span></span>

### <a name="goals"></a><span data-ttu-id="6183a-244">Cíle</span><span class="sxs-lookup"><span data-stu-id="6183a-244">Goals</span></span>

<span data-ttu-id="6183a-245">Cílem tohoto návodu je naučit se nasazovat aplikace založené na Windows kontejnerů Kubernetes (také nazývané *K8s*) ve službě Azure Container Service.</span><span class="sxs-lookup"><span data-stu-id="6183a-245">The goal of this walkthrough is to learn how to deploy a Windows Container–based application to Kubernetes (also called *K8s*) in Azure Container Service.</span></span> <span data-ttu-id="6183a-246">Nasazování do Kubernetes úplně od začátku je dvoustupňový proces:</span><span class="sxs-lookup"><span data-stu-id="6183a-246">Deploying to Kubernetes from scratch is a two-step process:</span></span>

1.  <span data-ttu-id="6183a-247">Nasazení clusteru Kubernetes do služby Azure Container Service.</span><span class="sxs-lookup"><span data-stu-id="6183a-247">Deploy a Kubernetes cluster to Azure Container Service.</span></span>

2.  <span data-ttu-id="6183a-248">Nasazení aplikace a související prostředky do clusteru Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="6183a-248">Deploy the application and related resources to the Kubernetes cluster.</span></span>

### <a name="scenarios"></a><span data-ttu-id="6183a-249">Scénáře</span><span class="sxs-lookup"><span data-stu-id="6183a-249">Scenarios</span></span>

#### <a name="scenario-a-deploy-directly-to-a-kubernetes-cluster-from-a-dev-environment"></a><span data-ttu-id="6183a-250">Scénář A: nasadit přímo do clusteru Kubernetes z vývojového prostředí</span><span class="sxs-lookup"><span data-stu-id="6183a-250">Scenario A: Deploy directly to a Kubernetes cluster from a dev environment</span></span>

![Nasadit do clusteru Kubernetes z vývojového prostředí](./media/image5-7.png)

> <span data-ttu-id="6183a-252">**Obrázek 5 – 7.**</span><span class="sxs-lookup"><span data-stu-id="6183a-252">**Figure 5-7.**</span></span> <span data-ttu-id="6183a-253">Nasadit do clusteru Kubernetes z vývojového prostředí</span><span class="sxs-lookup"><span data-stu-id="6183a-253">Deploy directly to a Kubernetes cluster from a development environment</span></span>

#### <a name="scenario-b-deploy-to-a-kubernetes-cluster-from-cicd-pipelines-in-azure-devops-services"></a><span data-ttu-id="6183a-254">Scénář B: nasazení do clusteru Kubernetes z CI/CD kanálů služby Azure DevOps</span><span class="sxs-lookup"><span data-stu-id="6183a-254">Scenario B: Deploy to a Kubernetes cluster from CI/CD pipelines in Azure DevOps Services</span></span>

![Nasazení do clusteru Kubernetes z kanálů CI/CD ve službách Azure DevOps](./media/image5-8.png)

> <span data-ttu-id="6183a-256">**Obrázek 5 až 8.**</span><span class="sxs-lookup"><span data-stu-id="6183a-256">**Figure 5-8.**</span></span> <span data-ttu-id="6183a-257">Nasazení do clusteru Kubernetes z kanálů CI/CD ve službách Azure DevOps</span><span class="sxs-lookup"><span data-stu-id="6183a-257">Deploy to a Kubernetes cluster from CI/CD pipelines in Azure DevOps Services</span></span>

### <a name="benefits"></a><span data-ttu-id="6183a-258">Výhody</span><span class="sxs-lookup"><span data-stu-id="6183a-258">Benefits</span></span>

<span data-ttu-id="6183a-259">Existuje mnoho výhod pro nasazení do clusteru v Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="6183a-259">There are many benefits to deploying to a cluster in Kubernetes.</span></span> <span data-ttu-id="6183a-260">Největší výhodou je, že dostanete prostředí připravené pro produkční prostředí, ve kterém můžete aplikace založená na počet instancí kontejneru chcete použít (vnitřní škálovatelnost v existujících uzlů) a na základě počtu virtuálních počítačů nebo uzly v clusteru (horizontálně navýšit Globální škálovatelnost clusteru).</span><span class="sxs-lookup"><span data-stu-id="6183a-260">The biggest benefit is that you get a production-ready environment in which you can scale out the application based on the number of container instances you want to use (inner-scalability in the existing nodes), and based on the number of nodes or VMs in the cluster (global scalability of the cluster).</span></span>

<span data-ttu-id="6183a-261">Služba Azure Container Service optimalizuje oblíbených opensourcových nástrojů a technologií konkrétně pro Azure.</span><span class="sxs-lookup"><span data-stu-id="6183a-261">Azure Container Service optimizes popular open-source tools and technologies specifically for Azure.</span></span> <span data-ttu-id="6183a-262">Získáte otevřené řešení, které nabízí přenositelnost pro vaše kontejnery i Konfigurace aplikací.</span><span class="sxs-lookup"><span data-stu-id="6183a-262">You get an open solution that offers portability, both for your containers and for your application configuration.</span></span> <span data-ttu-id="6183a-263">Vyberete velikost, počet hostitelů, a nástroje orchestrator – kontejner služby postará o všechno ostatní.</span><span class="sxs-lookup"><span data-stu-id="6183a-263">You select the size, the number of hosts, and the orchestrator tools-Container Service handles everything else.</span></span>

<span data-ttu-id="6183a-264">S využitím Kubernetes můžete průběh vývojáře od přemýšlení o fyzické a virtuální počítače, k plánování zaměřené na kontejner infrastruktury, která usnadňuje následující funkce, mimo jiné:</span><span class="sxs-lookup"><span data-stu-id="6183a-264">With Kubernetes, developers can progress from thinking about physical and virtual machines, to planning a container-centric infrastructure that facilitates the following capabilities, among others:</span></span>

- <span data-ttu-id="6183a-265">Aplikace založené na několika kontejnerů</span><span class="sxs-lookup"><span data-stu-id="6183a-265">Applications based on multiple containers</span></span>

- <span data-ttu-id="6183a-266">Replikace container instances a automatické horizontální škálování</span><span class="sxs-lookup"><span data-stu-id="6183a-266">Replicating container instances and horizontal autoscaling</span></span>

- <span data-ttu-id="6183a-267">Pojmenování a zjišťování (například interní DNS)</span><span class="sxs-lookup"><span data-stu-id="6183a-267">Naming and discovering (for example, internal DNS)</span></span>

- <span data-ttu-id="6183a-268">Vyrovnávání zatížení</span><span class="sxs-lookup"><span data-stu-id="6183a-268">Balancing loads</span></span>

- <span data-ttu-id="6183a-269">Aktualizace se zajištěním provozu</span><span class="sxs-lookup"><span data-stu-id="6183a-269">Rolling updates</span></span>

- <span data-ttu-id="6183a-270">Distribuce tajných kódů</span><span class="sxs-lookup"><span data-stu-id="6183a-270">Distributing secrets</span></span>

- <span data-ttu-id="6183a-271">Kontroly stavu aplikace</span><span class="sxs-lookup"><span data-stu-id="6183a-271">Application health checks</span></span>

## <a name="next-steps"></a><span data-ttu-id="6183a-272">Další kroky</span><span class="sxs-lookup"><span data-stu-id="6183a-272">Next steps</span></span>

<span data-ttu-id="6183a-273">Tento obsah podrobnější zkoumání na Wiki úložiště GitHub: [https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-C-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-C-CD))</span><span class="sxs-lookup"><span data-stu-id="6183a-273">Explore this content more in-depth on the GitHub wiki: [https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-C-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-C-CD))</span></span>

## <a name="walkthrough-6-deploy-your-windows-containers-based-apps-to-azure-service-fabric"></a><span data-ttu-id="6183a-274">Návod 6: Nasazení aplikace založené na kontejnery Windows do Azure Service Fabric</span><span class="sxs-lookup"><span data-stu-id="6183a-274">Walkthrough 6: Deploy your Windows Containers-based apps to Azure Service Fabric</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="6183a-275">Dostupnost průvodcem produktem</span><span class="sxs-lookup"><span data-stu-id="6183a-275">Technical walkthrough availability</span></span>

<span data-ttu-id="6183a-276">Je k dispozici v wiki úložiště GitHub eShopModernizing plnou technickou názorný postup:</span><span class="sxs-lookup"><span data-stu-id="6183a-276">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki:</span></span>

[https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-How-to-deploy-your-Windows-Containers-based-apps-into-Azure-Service-Fabric-(Including-CI-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-How-to-deploy-your-Windows-Containers-based-apps-into-Azure-Service-Fabric-(Including-CI-CD))

### <a name="overview"></a><span data-ttu-id="6183a-277">Přehled</span><span class="sxs-lookup"><span data-stu-id="6183a-277">Overview</span></span>

<span data-ttu-id="6183a-278">Aplikace založené na kontejnery Windows rychle musí používat platformy, přesunutí ještě více pryč z virtuálních počítačů IaaS.</span><span class="sxs-lookup"><span data-stu-id="6183a-278">An application based on Windows Containers quickly needs to use platforms, moving even further away from IaaS VMs.</span></span> <span data-ttu-id="6183a-279">To je potřeba provést snadno dosáhnout vysoké škálovatelnosti a lépe automatizované škálovatelnost a přináší značné vylepšení v automatické nasazení a správy verzí.</span><span class="sxs-lookup"><span data-stu-id="6183a-279">This is needed to easily achieve high scalability and better automated scalability, and for a significant improvement in automated deployments and versioning.</span></span> <span data-ttu-id="6183a-280">Pomocí Azure Service Fabric, která je k dispozici v cloudu Azure, ale také k dispozici pro použití v místním, orchestrator nebo dokonce i v různých veřejného cloudu, můžete dosáhnout těchto cílů.</span><span class="sxs-lookup"><span data-stu-id="6183a-280">You can achieve these goals by using the orchestrator Azure Service Fabric, which is available in the Azure cloud, but also available to use on-premises, or even in a different public cloud.</span></span>

### <a name="goals"></a><span data-ttu-id="6183a-281">Cíle</span><span class="sxs-lookup"><span data-stu-id="6183a-281">Goals</span></span>

<span data-ttu-id="6183a-282">Cílem tohoto návodu je naučit se nasazovat aplikace založené na Windows kontejnerů do clusteru Service Fabric v Azure.</span><span class="sxs-lookup"><span data-stu-id="6183a-282">The goal of this walkthrough is to learn how to deploy a Windows Container–based application to a Service Fabric cluster in Azure.</span></span> <span data-ttu-id="6183a-283">Nasazení do Service Fabric úplně od začátku je dvoustupňový proces:</span><span class="sxs-lookup"><span data-stu-id="6183a-283">Deploying to Service Fabric from scratch is a two-step process:</span></span>

1.  <span data-ttu-id="6183a-284">Nasazení clusteru Service Fabric do Azure (nebo do jiného prostředí).</span><span class="sxs-lookup"><span data-stu-id="6183a-284">Deploy a Service Fabric cluster to Azure (or to a different environment).</span></span>

2.  <span data-ttu-id="6183a-285">Nasazení aplikace a související prostředky do clusteru Service Fabric.</span><span class="sxs-lookup"><span data-stu-id="6183a-285">Deploy the application and related resources to the Service Fabric cluster.</span></span>

### <a name="scenarios"></a><span data-ttu-id="6183a-286">Scénáře</span><span class="sxs-lookup"><span data-stu-id="6183a-286">Scenarios</span></span>

#### <a name="scenario-a-deploy-directly-to-a-service-fabric-cluster-from-a-dev-environment"></a><span data-ttu-id="6183a-287">Scénář A: nasadit přímo do clusteru Service Fabric z vývojového prostředí</span><span class="sxs-lookup"><span data-stu-id="6183a-287">Scenario A: Deploy directly to a Service Fabric cluster from a dev environment</span></span>

![Nasadit do clusteru Service Fabric z vývojového prostředí](./media/image5-9.png)

> <span data-ttu-id="6183a-289">**Obrázek 5 až 9.**</span><span class="sxs-lookup"><span data-stu-id="6183a-289">**Figure 5-9.**</span></span> <span data-ttu-id="6183a-290">Nasadit do clusteru Service Fabric z vývojového prostředí</span><span class="sxs-lookup"><span data-stu-id="6183a-290">Deploy directly to a Service Fabric cluster from a development environment</span></span>

### <a name="scenario-b-deploy-to-a-service-fabric-cluster-from-cicd-pipelines-in-azure-devops-services"></a><span data-ttu-id="6183a-291">Scénář B: nasazení do clusteru Service Fabric z CI/CD kanálů služby Azure DevOps</span><span class="sxs-lookup"><span data-stu-id="6183a-291">Scenario B: Deploy to a Service Fabric cluster from CI/CD pipelines in Azure DevOps Services</span></span>

![Nasazení do clusteru Service Fabric z kanálů CI/CD ve službách Azure DevOps](./media/image5-10.png)

> <span data-ttu-id="6183a-293">**Obrázek 5 – 10.**</span><span class="sxs-lookup"><span data-stu-id="6183a-293">**Figure 5-10.**</span></span> <span data-ttu-id="6183a-294">Nasazení do clusteru Service Fabric z kanálů CI/CD ve službách Azure DevOps</span><span class="sxs-lookup"><span data-stu-id="6183a-294">Deploy to a Service Fabric cluster from CI/CD pipelines in Azure DevOps Services</span></span>

## <a name="benefits"></a><span data-ttu-id="6183a-295">Výhody</span><span class="sxs-lookup"><span data-stu-id="6183a-295">Benefits</span></span>

<span data-ttu-id="6183a-296">Výhody nasazení do clusteru v Service Fabric jsou podobné výhody používání Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="6183a-296">The benefits of deploying to a cluster in Service Fabric are similar to the benefits of using Kubernetes.</span></span> <span data-ttu-id="6183a-297">Jedním z rozdílů, ale je, že Service Fabric je vyspělejší produkčním prostředí pro aplikace Windows ve srovnání s Kubernetes, který je ve fázi beta pro kontejnery Windows v Kubernetes verze 1.9 (prosinec 2017).</span><span class="sxs-lookup"><span data-stu-id="6183a-297">One difference, though, is that Service Fabric is a more mature production environment for Windows applications compared to Kubernetes, which is in a beta phase for Windows Containers in Kubernetes version 1.9 (December 2017).</span></span> <span data-ttu-id="6183a-298">Kubernetes je vyspělejší prostředí pro Linux.</span><span class="sxs-lookup"><span data-stu-id="6183a-298">Kubernetes is a more mature environment for Linux.</span></span>

<span data-ttu-id="6183a-299">Hlavní výhodou použití Azure Service Fabric je, že dostanete prostředí připravené pro produkční prostředí, ve kterém můžete škálovat aplikace založená na počet instancí kontejneru chcete použít (vnitřní škálovatelnost v existujících uzlů) a podle počtu uzly nebo virtuální počítače v clusteru (globální škálovatelnost clusteru).</span><span class="sxs-lookup"><span data-stu-id="6183a-299">The main benefit of using Azure Service Fabric is that you get a production-ready environment in which you can scale out the application based on the number of container instances you want to use (inner-scalability in the existing nodes), and based on the number of nodes or VMs in the cluster (global scalability of the cluster).</span></span>

<span data-ttu-id="6183a-300">Azure Service Fabric nabízí přenositelnost pro vaše kontejnery i Konfigurace aplikací.</span><span class="sxs-lookup"><span data-stu-id="6183a-300">Azure Service Fabric offers portability both for your containers and for your application configuration.</span></span> <span data-ttu-id="6183a-301">Můžete použít Service Fabric cluster v Azure, nebo ji nainstalovat lokálně ve vašem vlastním datovém centru.</span><span class="sxs-lookup"><span data-stu-id="6183a-301">You can have a Service Fabric cluster in Azure, or install it on-premises in your own datacenter.</span></span> <span data-ttu-id="6183a-302">Můžete nainstalovat i cluster Service Fabric v jiný cloud, jako je třeba [Amazon AWS](https://blogs.msdn.microsoft.com/azureservicefabric/2017/05/18/tutorial-how-to-create-a-service-fabric-standalone-cluster-with-aws-ec2-instances/).</span><span class="sxs-lookup"><span data-stu-id="6183a-302">You can even install a Service Fabric cluster in a different cloud, like [Amazon AWS](https://blogs.msdn.microsoft.com/azureservicefabric/2017/05/18/tutorial-how-to-create-a-service-fabric-standalone-cluster-with-aws-ec2-instances/).</span></span>

<span data-ttu-id="6183a-303">S využitím Service Fabric můžete průběh vývojáře od přemýšlení o fyzické a virtuální počítače k plánování zaměřené na kontejner infrastruktury, která usnadňuje následující funkce, mimo jiné:</span><span class="sxs-lookup"><span data-stu-id="6183a-303">With Service Fabric, developers can progress from thinking about physical and virtual machines to planning a container-centric infrastructure that facilitates the following capabilities, among others:</span></span>

- <span data-ttu-id="6183a-304">Aplikace založené na několik kontejnerů.</span><span class="sxs-lookup"><span data-stu-id="6183a-304">Applications based on multiple containers.</span></span>

- <span data-ttu-id="6183a-305">Replikace container instances a automatické horizontální škálování.</span><span class="sxs-lookup"><span data-stu-id="6183a-305">Replicating container instances and horizontal autoscaling.</span></span>

- <span data-ttu-id="6183a-306">Pojmenování a zjišťování (například interní DNS).</span><span class="sxs-lookup"><span data-stu-id="6183a-306">Naming and discovering (for example, internal DNS).</span></span>

- <span data-ttu-id="6183a-307">Vyrovnávání zatížení.</span><span class="sxs-lookup"><span data-stu-id="6183a-307">Balancing loads.</span></span>

- <span data-ttu-id="6183a-308">Aktualizace se zajištěním provozu.</span><span class="sxs-lookup"><span data-stu-id="6183a-308">Rolling updates.</span></span>

- <span data-ttu-id="6183a-309">Distribuce tajných kódů.</span><span class="sxs-lookup"><span data-stu-id="6183a-309">Distributing secrets.</span></span>

- <span data-ttu-id="6183a-310">Kontroluje se stav aplikace.</span><span class="sxs-lookup"><span data-stu-id="6183a-310">Application health checks.</span></span>

<span data-ttu-id="6183a-311">Tyto možnosti jsou výhradně v Service Fabric (ve srovnání se jiných orchestrátorů):</span><span class="sxs-lookup"><span data-stu-id="6183a-311">The following capabilities are exclusive in Service Fabric (compared to other orchestrators):</span></span>

- <span data-ttu-id="6183a-312">Funkce stavové služby, prostřednictvím aplikačního modelu Reliable Services.</span><span class="sxs-lookup"><span data-stu-id="6183a-312">Stateful services capability, through the Reliable Services application model.</span></span>

- <span data-ttu-id="6183a-313">Model objektů actor, prostřednictvím aplikačního modelu Reliable Actors.</span><span class="sxs-lookup"><span data-stu-id="6183a-313">Actors pattern, through the Reliable Actors application model.</span></span>

- <span data-ttu-id="6183a-314">Nasazení úplné kost procesy, kromě kontejnery Windows nebo Linux.</span><span class="sxs-lookup"><span data-stu-id="6183a-314">Deploy bare-bone processes, in addition to Windows or Linux containers.</span></span>

- <span data-ttu-id="6183a-315">Pokročilé kumulativní aktualizace a kontroly stavu.</span><span class="sxs-lookup"><span data-stu-id="6183a-315">Advanced rolling updates and health checks.</span></span>

### <a name="next-steps"></a><span data-ttu-id="6183a-316">Další kroky</span><span class="sxs-lookup"><span data-stu-id="6183a-316">Next steps</span></span>

<span data-ttu-id="6183a-317">Tento obsah podrobnější zkoumání na Wiki úložiště GitHub:</span><span class="sxs-lookup"><span data-stu-id="6183a-317">Explore this content more in-depth on the GitHub wiki:</span></span>

[https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-How-to-deploy-your-Windows-Containers-based-apps-into-Azure-Service-Fabric-(Including-CI-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-How-to-deploy-your-Windows-Containers-based-apps-into-Azure-Service-Fabric-(Including-CI-CD))

>[!div class="step-by-step"]
<span data-ttu-id="6183a-318">[Předchozí](lift-and-shift-existing-apps-devops/migrate-to-hybrid-cloud-scenarios.md)
[další](conclusions.md)</span><span class="sxs-lookup"><span data-stu-id="6183a-318">[Previous](lift-and-shift-existing-apps-devops/migrate-to-hybrid-cloud-scenarios.md)
[Next](conclusions.md)</span></span>
