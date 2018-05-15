---
title: Postupy a technická získat Začínáme přehled
description: Modernizovat existující aplikace .NET s cloudu Azure a Windows kontejnery | Postupy a technická získat Začínáme přehled
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/28/2018
ms.openlocfilehash: 27de9d1c5475855a22f2d8a3518982605277f6d9
ms.sourcegitcommit: 88f251b08bf0718ce119f3d7302f514b74895038
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/10/2018
---
# <a name="walkthroughs-and-technical-get-started-overview"></a><span data-ttu-id="9e9fa-103">Postupy a technická získat Začínáme přehled</span><span class="sxs-lookup"><span data-stu-id="9e9fa-103">Walkthroughs and technical get started overview</span></span>

<span data-ttu-id="9e9fa-104">K omezení velikosti elektronická kniha, provedeny další technickou dokumentaci a úplné návody k dispozici v úložišti GitHub.</span><span class="sxs-lookup"><span data-stu-id="9e9fa-104">To limit the size of this e-book, additional technical documentation and the full walkthroughs were made available in a GitHub repository.</span></span> <span data-ttu-id="9e9fa-105">Online řada návodů, která je popsána v tato kapitola obsahuje podrobné nastavení několika prostředí, které jsou založeny na Windows kontejnery a nasazení do Azure.</span><span class="sxs-lookup"><span data-stu-id="9e9fa-105">The online series of walkthroughs that is described in this chapter covers the step-by-step setup of the multiple environments that are based on Windows Containers, and deployment to Azure.</span></span>

<span data-ttu-id="9e9fa-106">Následující části popisují, co každý návod o svých cílů a vysoké úrovně vize a poskytuje diagram úlohy, které se podílejí.</span><span class="sxs-lookup"><span data-stu-id="9e9fa-106">The following sections explain what each walkthrough is about, its objectives and high-level vision, and provides a diagram of the tasks that are involved.</span></span> <span data-ttu-id="9e9fa-107">Můžete získat sami názorné postupy v *eShopModernizing* wiki úložišti GitHub aplikace v [ https://github.com/dotnet-architecture/eShopModernizing/wiki ](https://github.com/dotnet-architecture/eShopModernizing/wiki).</span><span class="sxs-lookup"><span data-stu-id="9e9fa-107">You can get the walkthroughs themselves in the *eShopModernizing* apps GitHub repo wiki at [https://github.com/dotnet-architecture/eShopModernizing/wiki](https://github.com/dotnet-architecture/eShopModernizing/wiki).</span></span>

## <a name="technical-walkthrough-list"></a><span data-ttu-id="9e9fa-108">Seznamu technických návod</span><span class="sxs-lookup"><span data-stu-id="9e9fa-108">Technical walkthrough list</span></span>

<span data-ttu-id="9e9fa-109">Následující kurzy get-started poskytovat konzistentní a komplexní technické pokyny pro ukázkové aplikace, které se dají navýšení a posunutí pomocí kontejnery a potom přesunout tak, že pomocí více možností nasazení v Azure.</span><span class="sxs-lookup"><span data-stu-id="9e9fa-109">The following get-started walkthroughs provide consistent and comprehensive technical guidance for sample apps that you can lift and shift by using containers, and then move by using multiple deployment choices in Azure.</span></span>

<span data-ttu-id="9e9fa-110">Každá z následující kurzy používá nové ukázkových eShopLegacy a eShopModernizing aplikací, které jsou k dispozici na webu GitHub na [ https://github.com/dotnet-architecture/eShopModernizing ](https://github.com/dotnet-architecture/eShopModernizing).</span><span class="sxs-lookup"><span data-stu-id="9e9fa-110">Each of the following walkthroughs uses the new sample eShopLegacy and eShopModernizing apps, which are available on GitHub at [https://github.com/dotnet-architecture/eShopModernizing](https://github.com/dotnet-architecture/eShopModernizing).</span></span>

- <span data-ttu-id="9e9fa-111">**Prohlídka eShop starší verze aplikací (aplikace směrného plánu modernizovat)**</span><span class="sxs-lookup"><span data-stu-id="9e9fa-111">**Tour of eShop legacy apps (baseline apps to modernize)**</span></span>

- <span data-ttu-id="9e9fa-112">**Containerize existující webových aplikací ASP.NET (WebForms & MVC) s kontejnery Windows**</span><span class="sxs-lookup"><span data-stu-id="9e9fa-112">**Containerize your existing ASP.NET web apps (WebForms & MVC) with Windows Containers**</span></span>

- <span data-ttu-id="9e9fa-113">**Containerize stávající služby WCF (vícevrstvé aplikace) s kontejnery Windows**</span><span class="sxs-lookup"><span data-stu-id="9e9fa-113">**Containerize your existing WCF services (N-Tier apps) with Windows Containers**</span></span>

- <span data-ttu-id="9e9fa-114">**Nasazení aplikace systému Windows na základě kontejnery pro virtuální počítače Azure**</span><span class="sxs-lookup"><span data-stu-id="9e9fa-114">**Deploy your Windows Containers-based app to Azure VMs**</span></span>

- <span data-ttu-id="9e9fa-115">**Nasazení aplikace na základě kontejnery Windows do Kubernetes v Azure Container Service**</span><span class="sxs-lookup"><span data-stu-id="9e9fa-115">**Deploy your Windows Containers-based apps to Kubernetes in Azure Container Service**</span></span>

- <span data-ttu-id="9e9fa-116">**Nasazení aplikace na základě kontejnery Windows do Azure Service Fabric**</span><span class="sxs-lookup"><span data-stu-id="9e9fa-116">**Deploy your Windows Containers-based apps to Azure Service Fabric**</span></span>


## <a name="walkthrough-1-tour-of-eshop-legacy-apps"></a><span data-ttu-id="9e9fa-117">Návod 1: Prohlídka eShop starší verze aplikací</span><span class="sxs-lookup"><span data-stu-id="9e9fa-117">Walkthrough 1: Tour of eShop legacy apps</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="9e9fa-118">Technické návod dostupnosti</span><span class="sxs-lookup"><span data-stu-id="9e9fa-118">Technical walkthrough availability</span></span>

<span data-ttu-id="9e9fa-119">Úplné technické návod je k dispozici na stránkách wiki úložišti GitHub eShopModernizing:</span><span class="sxs-lookup"><span data-stu-id="9e9fa-119">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki:</span></span>

[<span data-ttu-id="9e9fa-120">návody eShopModernizing wiki</span><span class="sxs-lookup"><span data-stu-id="9e9fa-120">eShopModernizing wiki walkthroughs</span></span>](https://github.com/dotnet-architecture/eShopModernizing/wiki)


### <a name="overview"></a><span data-ttu-id="9e9fa-121">Přehled</span><span class="sxs-lookup"><span data-stu-id="9e9fa-121">Overview</span></span>

<span data-ttu-id="9e9fa-122">V tomto návodu můžete prozkoumat počáteční implementace tři ukázkové starší verze aplikace.</span><span class="sxs-lookup"><span data-stu-id="9e9fa-122">In this walkthrough, you can explore the initial implementation of three sample legacy applications.</span></span> <span data-ttu-id="9e9fa-123">První dva ukázkové webové aplikace mají monolitický architekturu a byly vytvořeny pomocí klasického ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="9e9fa-123">The first two sample web apps have a monolithic architecture, and were created by using classic ASP.NET.</span></span> <span data-ttu-id="9e9fa-124">Jeden aplikace je založena na technologii ASP.NET 4.x MVC; druhý aplikace je založena na webových formulářů ASP.NET 4.x.</span><span class="sxs-lookup"><span data-stu-id="9e9fa-124">One application is based on ASP.NET 4.x MVC; the second application is based on ASP.NET 4.x Web Forms.</span></span> <span data-ttu-id="9e9fa-125">Třetí aplikace je 3vrstvé aplikace skládá klientskou aplikaci pro WinForms a straně serveru [Windows Communication Foundation (WCF)](../../framework/wcf/whats-wcf.md) služby.</span><span class="sxs-lookup"><span data-stu-id="9e9fa-125">The third app is a 3-Tier app composed by a client WinForms app and a server-side [Windows Communication Foundation (WCF)](../../framework/wcf/whats-wcf.md) service.</span></span>

<span data-ttu-id="9e9fa-126">Všechny tyto aplikace jsou k dispozici na [úložiště GitHub eShopModernizing](https://github.com/dotnet-architecture/eShopModernizing).</span><span class="sxs-lookup"><span data-stu-id="9e9fa-126">All these applications are available at the [eShopModernizing GitHub repo](https://github.com/dotnet-architecture/eShopModernizing).</span></span>

### <a name="goals"></a><span data-ttu-id="9e9fa-127">Cíle</span><span class="sxs-lookup"><span data-stu-id="9e9fa-127">Goals</span></span>

<span data-ttu-id="9e9fa-128">Hlavním cílem tohoto návodu je jednoduše a seznamte se s těmito aplikacemi a s jejich kódu a konfigurace.</span><span class="sxs-lookup"><span data-stu-id="9e9fa-128">The main goal of this walkthrough is simply to get familiar with these apps, and with their code and configuration.</span></span> <span data-ttu-id="9e9fa-129">Aplikace můžete nakonfigurovat tak, aby se vygenerování a použití imitovaná data bez použití databáze SQL pro účely testování.</span><span class="sxs-lookup"><span data-stu-id="9e9fa-129">You can configure the apps so that they generate and use mock data, without using the SQL database, for testing purposes.</span></span> <span data-ttu-id="9e9fa-130">Toto volitelné konfigurace je založená na vkládání závislostí odpojeného způsobem.</span><span class="sxs-lookup"><span data-stu-id="9e9fa-130">This optional config is based on dependency injection, in a decoupled way.</span></span>

### <a name="scenario-1-aspnet-web-apps"></a><span data-ttu-id="9e9fa-131">Scénář 1: ASP.NET – webové aplikace</span><span class="sxs-lookup"><span data-stu-id="9e9fa-131">Scenario 1: ASP.NET Web apps</span></span>

<span data-ttu-id="9e9fa-132">Následující obrázek znázorňuje jednoduchý scénář původní starší verze webové aplikace ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="9e9fa-132">The figure below shows the simple scenario of the original legacy ASP.NET web applications.</span></span>

> ![Scénář jednoduchého architektura původní starší verze webových aplikací ASP.NET](./media/image5-1.png)
>

<span data-ttu-id="9e9fa-134">Z hlediska domény obchodní obě aplikace nabízejí katalogu stejné funkce pro správu.</span><span class="sxs-lookup"><span data-stu-id="9e9fa-134">From a business domain perspective, both apps offer the same catalog management features.</span></span> <span data-ttu-id="9e9fa-135">Členové týmu enterprise eShop využije aplikace k zobrazení a úpravy katalogu produktů.</span><span class="sxs-lookup"><span data-stu-id="9e9fa-135">Members of the eShop enterprise team would use the app to view and edit the product catalog.</span></span> 

<span data-ttu-id="9e9fa-136">Následující obrázek ukazuje na snímcích obrazovky počáteční aplikace.</span><span class="sxs-lookup"><span data-stu-id="9e9fa-136">The next figure shows the initial app screenshots.</span></span>

![Aplikace ASP.NET MVC a webových formulářů ASP.NET (technologie existující nebo starší)](./media/image5-2.png)

<span data-ttu-id="9e9fa-138">Závislosti v technologii ASP.NET 4.x nebo starší verze (buď pro MVC nebo webových formulářů) znamená, že tyto aplikace se na .NET Core nespustí, pokud kód je plně přepsaná pomocí ASP.NET MVC jádra.</span><span class="sxs-lookup"><span data-stu-id="9e9fa-138">Dependencies in ASP.NET 4.x or earlier versions (either for MVC or for Web Forms) means that these applications won’t run on .NET Core unless the code is fully rewritten by using ASP.NET Core MVC.</span></span> 

### <a name="scenario-2-wcf-service-and-winforms-client-app-3-tier-app"></a><span data-ttu-id="9e9fa-139">Scénář 2: Služby WCF a WinForms klienta aplikace (úroveň 3)</span><span class="sxs-lookup"><span data-stu-id="9e9fa-139">Scenario 2: WCF service and WinForms client app (3-Tier app)</span></span>

<span data-ttu-id="9e9fa-140">Následující obrázek znázorňuje jednoduchý scénář původní vrstvy 3 starší verzi aplikace.</span><span class="sxs-lookup"><span data-stu-id="9e9fa-140">The figure below shows the simple scenario of the original 3-Tier legacy application.</span></span>

> ![Scénář jednoduchého architektura původní starší verze 3vrstvé aplikace pomocí služby WCF a klientskou aplikaci WinForms](./media/image5-1.5.png)
>

### <a name="benefits"></a><span data-ttu-id="9e9fa-142">Výhody</span><span class="sxs-lookup"><span data-stu-id="9e9fa-142">Benefits</span></span>

<span data-ttu-id="9e9fa-143">Výhody tohoto návodu jsou jednoduché: právě Seznamte se s kódem a počáteční aplikace.</span><span class="sxs-lookup"><span data-stu-id="9e9fa-143">The benefits of this walkthrough are simple: Just get familiar with the code and initial apps.</span></span>

### <a name="next-steps"></a><span data-ttu-id="9e9fa-144">Další kroky</span><span class="sxs-lookup"><span data-stu-id="9e9fa-144">Next steps</span></span>

<span data-ttu-id="9e9fa-145">Prozkoumejte podrobnější tento obsah na stránkách wiki Githubu:</span><span class="sxs-lookup"><span data-stu-id="9e9fa-145">Explore this content more in-depth on the GitHub wiki:</span></span>

  - [<span data-ttu-id="9e9fa-146">Prohlídka na základě technologie ASP.NET MVC a webových formulářů "starší" aplikace</span><span class="sxs-lookup"><span data-stu-id="9e9fa-146">Tour on the baseline ASP.NET MVC and Web Forms “legacy” apps</span></span>](https://github.com/dotnet-architecture/eShopModernizing/wiki/01.-Tour-on-the-ASP.NET-MVC-and-WebForms-apps-implementation-code)
  - [<span data-ttu-id="9e9fa-147">Prohlídka na službu WCF směrného plánu a WinForms (3vrstvé) "starší" aplikace</span><span class="sxs-lookup"><span data-stu-id="9e9fa-147">Tour on the baseline WCF service and WinForms (3-Tier) “legacy” app</span></span>](https://github.com/dotnet-architecture/eShopModernizing/wiki/21.-Tour-on-the-WCF-service-and-WinForms-apps)


## <a name="walkthrough-2-containerize-your-existing-net-applications-with-windows-containers"></a><span data-ttu-id="9e9fa-148">Návod 2: Containerize existující aplikace .NET s kontejnery Windows</span><span class="sxs-lookup"><span data-stu-id="9e9fa-148">Walkthrough 2: Containerize your existing .NET applications with Windows Containers</span></span>

### <a name="overview"></a><span data-ttu-id="9e9fa-149">Přehled</span><span class="sxs-lookup"><span data-stu-id="9e9fa-149">Overview</span></span>

<span data-ttu-id="9e9fa-150">Použití Windows kontejnerů ke zlepšení nasazení existujících aplikací .NET, například algoritmů založených na rozhraní MVC a webových formulářů, WCF, výroby, vývoj a testovací prostředí.</span><span class="sxs-lookup"><span data-stu-id="9e9fa-150">Use Windows Containers to improve deployment of existing .NET applications, like those based on MVC, Web Forms, or WCF, to production, development, and test environments.</span></span>

### <a name="goals"></a><span data-ttu-id="9e9fa-151">Cíle</span><span class="sxs-lookup"><span data-stu-id="9e9fa-151">Goals</span></span>

<span data-ttu-id="9e9fa-152">Cílem tohoto návodu je tak, aby zobrazovalo několik možností pro containerizing stávající aplikace rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9e9fa-152">The goal of this walkthrough is to show you several options for containerizing an existing .NET Framework application.</span></span> <span data-ttu-id="9e9fa-153">Můžeš:</span><span class="sxs-lookup"><span data-stu-id="9e9fa-153">You can:</span></span>

- <span data-ttu-id="9e9fa-154">Containerize vaší aplikace pomocí [2017 nástroje sady Visual Studio pro Docker](/aspnet/core/host-and-deploy/docker/visual-studio-tools-for-docker) (Visual Studio 2017 nebo novější verze).</span><span class="sxs-lookup"><span data-stu-id="9e9fa-154">Containerize your application by using [Visual Studio 2017 Tools for Docker](/aspnet/core/host-and-deploy/docker/visual-studio-tools-for-docker) (Visual Studio 2017 or later versions).</span></span>

- <span data-ttu-id="9e9fa-155">Containerize aplikace tak, že ručně přidáte [soubor Docker](https://docs.docker.com/engine/reference/builder/)a potom pomocí [příkazového řádku Dockeru](https://docs.docker.com/engine/reference/commandline/cli/).</span><span class="sxs-lookup"><span data-stu-id="9e9fa-155">Containerize your application by manually adding a [Dockerfile](https://docs.docker.com/engine/reference/builder/), and then using the [Docker CLI](https://docs.docker.com/engine/reference/commandline/cli/).</span></span>

- <span data-ttu-id="9e9fa-156">Containerize vaší aplikace pomocí [Img2Docker](https://github.com/docker/communitytools-image2docker-win) (nástroj open-source z Docker).</span><span class="sxs-lookup"><span data-stu-id="9e9fa-156">Containerize your application by using the [Img2Docker](https://github.com/docker/communitytools-image2docker-win) tool (an open-source tool from Docker).</span></span>

<span data-ttu-id="9e9fa-157">Tento názorný postup se zaměřuje na Visual Studio Tools 2017 Docker přístup, ale jsou poměrně stejné z hlediska pomocí Dockerfiles tyto dva přístupy.</span><span class="sxs-lookup"><span data-stu-id="9e9fa-157">This walkthrough focuses on the Visual Studio 2017 Tools for Docker approach, but the other two approaches are fairly similar in regard to using Dockerfiles.</span></span>

### <a name="scenario-1-containerized-aspnet-web-apps"></a><span data-ttu-id="9e9fa-158">Scénář 1: Kontejnerizované ASP.NET webové aplikace</span><span class="sxs-lookup"><span data-stu-id="9e9fa-158">Scenario 1: Containerized ASP.NET web apps</span></span>

<span data-ttu-id="9e9fa-159">Následující obrázek znázorňuje tento scénář pro kontejnerizované eShop starší verze webové aplikace aplikace.</span><span class="sxs-lookup"><span data-stu-id="9e9fa-159">Figure below shows the scenario for containerized eShop legacy web apps applications.</span></span>

> ![Diagram zjednodušení architektury kontejnerové aplikace ASP.NET ve vývojovém prostředí](./media/image5-3.png)
>


### <a name="scenario-2-containerized-wcf-service"></a><span data-ttu-id="9e9fa-161">Scénář 2: Služby WCF Kontejnerizované</span><span class="sxs-lookup"><span data-stu-id="9e9fa-161">Scenario 2: Containerized WCF service</span></span>

<span data-ttu-id="9e9fa-162">Následující obrázek znázorňuje tento scénář pro 3vrstvé aplikace kontejnerizované službou WCF.</span><span class="sxs-lookup"><span data-stu-id="9e9fa-162">Figure below shows the scenario for a 3-Tier app with a containerized WCF service.</span></span> 

> ![Zjednodušená diagram architektury kontejnerové služby WCF ve vývojovém prostředí](./media/image5-3.5.png)
>

### <a name="benefits"></a><span data-ttu-id="9e9fa-164">Výhody</span><span class="sxs-lookup"><span data-stu-id="9e9fa-164">Benefits</span></span>

<span data-ttu-id="9e9fa-165">Existují výhody používání aplikace monolitický v kontejneru.</span><span class="sxs-lookup"><span data-stu-id="9e9fa-165">There are advantages to running your monolithic application in a container.</span></span> <span data-ttu-id="9e9fa-166">Nejprve je třeba vytvořit bitovou kopii pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="9e9fa-166">First, you create an image for the application.</span></span> <span data-ttu-id="9e9fa-167">Od tohoto okamžiku v každé nasazení běží ve stejném prostředí.</span><span class="sxs-lookup"><span data-stu-id="9e9fa-167">From that point on, every deployment runs in the same environment.</span></span> <span data-ttu-id="9e9fa-168">Každý kontejner používá stejnou verzi operačního systému, má stejnou verzi závislostí nainstalována, používá stejnou verzi rozhraní .NET framework a je vytvořen pomocí stejného procesu.</span><span class="sxs-lookup"><span data-stu-id="9e9fa-168">Every container uses the same OS version, has the same version of dependencies installed, uses the same .NET framework version, and is built by using the same process.</span></span> <span data-ttu-id="9e9fa-169">V podstatě řídit závislostí vaší aplikace pomocí Docker bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="9e9fa-169">Basically, you control the dependencies of your application by using a Docker image.</span></span> <span data-ttu-id="9e9fa-170">Závislosti cestují k aplikaci při nasazení kontejnerů.</span><span class="sxs-lookup"><span data-stu-id="9e9fa-170">The dependencies travel with the application when you deploy the containers.</span></span>

<span data-ttu-id="9e9fa-171">Další výhodou je, že vývojáři aplikaci můžete spustit v konzistentní prostředí, které poskytuje Windows kontejnery.</span><span class="sxs-lookup"><span data-stu-id="9e9fa-171">An additional benefit is that developers can run the application in the consistent environment that's provided by Windows Containers.</span></span> <span data-ttu-id="9e9fa-172">Problémy, které se zobrazují pouze u některých verzí můžete okamžitě, nanese místo zpřístupnění v pracovním nebo produkčním prostředí.</span><span class="sxs-lookup"><span data-stu-id="9e9fa-172">Issues that appear only with certain versions can be spotted immediately, instead of surfacing in a staging or production environment.</span></span> <span data-ttu-id="9e9fa-173">Rozdíly ve vývojovém prostředí používá členové týmu pro vývoj podstatné menší při spuštění aplikace v kontejnerech.</span><span class="sxs-lookup"><span data-stu-id="9e9fa-173">Differences in development environments used by members of the development team matter less when applications run in containers.</span></span>

<span data-ttu-id="9e9fa-174">Kontejnerizované aplikací mít také plošší křivky Škálováním na více systémů.</span><span class="sxs-lookup"><span data-stu-id="9e9fa-174">Containerized applications also have a flatter scale-out curve.</span></span> <span data-ttu-id="9e9fa-175">Kontejnerizované aplikací umožňují mít další aplikace a instance služby (podle kontejnery) v virtuálního počítače nebo fyzického počítače ve srovnání s nasazení regulární aplikací na počítač.</span><span class="sxs-lookup"><span data-stu-id="9e9fa-175">Containerized apps enable you to have more application and service instances (based on containers) in a VM or physical machine compared to regular application deployments per machine.</span></span> <span data-ttu-id="9e9fa-176">Výsledkem je vyšší hustotu a méně požadované prostředky, zejména v případě, že používáte orchestrators jako Kubernetes nebo Service Fabric.</span><span class="sxs-lookup"><span data-stu-id="9e9fa-176">This translates to higher density and fewer required resources, especially when you use orchestrators like Kubernetes or Service Fabric.</span></span>

<span data-ttu-id="9e9fa-177">Rozdělení do kontejnerů v situacích, ideální, není nutné provádět jakékoliv změny kódu aplikace (C\#).</span><span class="sxs-lookup"><span data-stu-id="9e9fa-177">Containerization, in ideal situations, does not require making any changes to the application code (C\#).</span></span> <span data-ttu-id="9e9fa-178">Ve většině scénářů bude třeba jen soubory metadat nasazení Docker (soubory Dockerfiles a Docker Compose).</span><span class="sxs-lookup"><span data-stu-id="9e9fa-178">In most scenarios, you just need the Docker deployment metadata files (Dockerfiles and Docker Compose files).</span></span>

### <a name="next-steps"></a><span data-ttu-id="9e9fa-179">Další kroky</span><span class="sxs-lookup"><span data-stu-id="9e9fa-179">Next steps</span></span>

<span data-ttu-id="9e9fa-180">Prozkoumejte podrobnější tento obsah na stránkách wiki Githubu:</span><span class="sxs-lookup"><span data-stu-id="9e9fa-180">Explore this content more in-depth on the GitHub wiki:</span></span>

  - [<span data-ttu-id="9e9fa-181">Postup containerize webové aplikace rozhraní .NET Framework s kontejnery Windows a Docker</span><span class="sxs-lookup"><span data-stu-id="9e9fa-181">How to containerize the .NET Framework web apps with Windows Containers and Docker</span></span>](https://github.com/dotnet-architecture/eShopModernizing/wiki/02.-How-to-containerize-the-.NET-Framework-web-apps-with-Windows-Containers-and-Docker)
  - [<span data-ttu-id="9e9fa-182">Přidání podpory Docker do služby WCF</span><span class="sxs-lookup"><span data-stu-id="9e9fa-182">Adding Docker Support to a WCF service</span></span>](https://github.com/dotnet-architecture/eShopModernizing/wiki/22.-Adding-Docker-Support)



## <a name="walkthrough-3-deploy-your-windows-containers-based-app-to-azure-vms"></a><span data-ttu-id="9e9fa-183">Návod 3: Nasazení aplikace systému Windows na základě kontejnery pro virtuální počítače Azure</span><span class="sxs-lookup"><span data-stu-id="9e9fa-183">Walkthrough 3: Deploy your Windows Containers-based app to Azure VMs</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="9e9fa-184">Technické návod dostupnosti</span><span class="sxs-lookup"><span data-stu-id="9e9fa-184">Technical walkthrough availability</span></span>

<span data-ttu-id="9e9fa-185">Úplné technické návod je k dispozici na stránkách wiki úložišti GitHub eShopModernizing: [https://github.com/dotnet-architecture/eShopModernizing/wiki/03.-How-to-deploy-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/03.-How-to-deploy-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD))</span><span class="sxs-lookup"><span data-stu-id="9e9fa-185">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki: [https://github.com/dotnet-architecture/eShopModernizing/wiki/03.-How-to-deploy-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/03.-How-to-deploy-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD))</span></span>

### <a name="overview"></a><span data-ttu-id="9e9fa-186">Přehled</span><span class="sxs-lookup"><span data-stu-id="9e9fa-186">Overview</span></span>

<span data-ttu-id="9e9fa-187">Nasazení do hostitelů Docker v Windows Server 2016 virtuálního počítače (VM) v Azure umožňuje rychle nastavit vývoj/testovací/přípravného prostředí.</span><span class="sxs-lookup"><span data-stu-id="9e9fa-187">Deploying to a Docker host on a Windows Server 2016 Virtual Machine (VM) in Azure lets you quickly set up development/test/staging environments.</span></span> <span data-ttu-id="9e9fa-188">Také poskytuje společné místo pro testery nebo podnikoví uživatelé k ověření aplikace.</span><span class="sxs-lookup"><span data-stu-id="9e9fa-188">It also gives you a common place for testers or business users to validate the app.</span></span> <span data-ttu-id="9e9fa-189">Virtuální počítače také může být platný že jako provozní prostředí služby (IaaS).</span><span class="sxs-lookup"><span data-stu-id="9e9fa-189">VMs also can be valid Infrastucture as a Service (IaaS) production environments.</span></span>

### <a name="goals"></a><span data-ttu-id="9e9fa-190">Cíle</span><span class="sxs-lookup"><span data-stu-id="9e9fa-190">Goals</span></span>

<span data-ttu-id="9e9fa-191">Cílem tohoto návodu je tak, aby zobrazovalo více alternativy, které máte, když nasadíte kontejnery Windows na virtuálních počítačích Azure, které jsou založené na systému Windows Server 2016 nebo novější verze.</span><span class="sxs-lookup"><span data-stu-id="9e9fa-191">The goal of this walkthrough is to show you the multiple alternatives you have when you deploy Windows Containers to Azure VMs that are based on Windows Server 2016 or later versions.</span></span>

### <a name="scenarios"></a><span data-ttu-id="9e9fa-192">Scénáře</span><span class="sxs-lookup"><span data-stu-id="9e9fa-192">Scenarios</span></span>

<span data-ttu-id="9e9fa-193">Několik scénáře jsou popsané v tomto návodu.</span><span class="sxs-lookup"><span data-stu-id="9e9fa-193">Several scenarios are covered in this walkthrough.</span></span>

#### <a name="scenario-a-deploy-to-an-azure-vm-from-a-dev-pc-through-docker-engine-connection"></a><span data-ttu-id="9e9fa-194">Scénář A: nasazení na virtuální počítač Azure ze dev počítače prostřednictvím připojení modulu Docker</span><span class="sxs-lookup"><span data-stu-id="9e9fa-194">Scenario A: Deploy to an Azure VM from a dev PC through Docker Engine connection</span></span>

![Nasazení na virtuální počítač Azure z vývojářů počítače prostřednictvím připojení k modulu Docker](./media/image5-4.png)

> <span data-ttu-id="9e9fa-196">**Obrázek 5 – 4.**</span><span class="sxs-lookup"><span data-stu-id="9e9fa-196">**Figure 5-4.**</span></span> <span data-ttu-id="9e9fa-197">Nasazení na virtuální počítač Azure z vývojářů počítače prostřednictvím připojení k modulu Docker</span><span class="sxs-lookup"><span data-stu-id="9e9fa-197">Deploy to an Azure VM from a dev PC through a Docker Engine connection</span></span>

#### <a name="scenario-b-deploy-to-an-azure-vm-through-a-docker-registry"></a><span data-ttu-id="9e9fa-198">Scénář B: nasazení na virtuální počítač Azure prostřednictvím registru Docker</span><span class="sxs-lookup"><span data-stu-id="9e9fa-198">Scenario B: Deploy to an Azure VM through a Docker Registry</span></span>

![Nasazení na virtuální počítač Azure prostřednictvím registru Docker](./media/image5-5.png)

> <span data-ttu-id="9e9fa-200">**Obrázek 5-5.**</span><span class="sxs-lookup"><span data-stu-id="9e9fa-200">**Figure 5-5.**</span></span> <span data-ttu-id="9e9fa-201">Nasazení na virtuální počítač Azure prostřednictvím registru Docker</span><span class="sxs-lookup"><span data-stu-id="9e9fa-201">Deploy to an Azure VM through a Docker Registry</span></span>

#### <a name="scenario-c-deploy-to-an-azure-vm-from-cicd-pipelines-in-visual-studio-team-services"></a><span data-ttu-id="9e9fa-202">Scénář C: nasazení na virtuální počítač Azure z položek konfigurace nebo CD kanály v sadě Visual Studio Team Services</span><span class="sxs-lookup"><span data-stu-id="9e9fa-202">Scenario C: Deploy to an Azure VM from CI/CD pipelines in Visual Studio Team Services</span></span>

![Nasazení z položek konfigurace nebo CD kanály v sadě Visual Studio Team Services na virtuální počítač Azure](./media/image5-6.png)

> <span data-ttu-id="9e9fa-204">**Obrázek 5 a 6.**</span><span class="sxs-lookup"><span data-stu-id="9e9fa-204">**Figure 5-6.**</span></span> <span data-ttu-id="9e9fa-205">Nasazení z položek konfigurace nebo CD kanály v sadě Visual Studio Team Services na virtuální počítač Azure</span><span class="sxs-lookup"><span data-stu-id="9e9fa-205">Deploy to an Azure VM from CI/CD pipelines in Visual Studio Team Services</span></span>

### <a name="azure-vms-for-windows-containers"></a><span data-ttu-id="9e9fa-206">Virtuální počítače Azure pro Windows kontejnery</span><span class="sxs-lookup"><span data-stu-id="9e9fa-206">Azure VMs for Windows Containers</span></span>

<span data-ttu-id="9e9fa-207">Azure kontejnery virtuálních počítačů pro Windows jsou virtuální počítače na základě systému Windows Server 2016, Windows 10 nebo novější verze, jak k modulu Docker nastavení.</span><span class="sxs-lookup"><span data-stu-id="9e9fa-207">Azure VMs for Windows Containers are VMs based on Windows Server 2016, Windows 10, or later versions, both with Docker Engine set up.</span></span> <span data-ttu-id="9e9fa-208">Ve většině případů se používá Windows Server 2016 ve virtuálních počítačích Azure.</span><span class="sxs-lookup"><span data-stu-id="9e9fa-208">In most cases, Windows Server 2016 is used in the Azure VMs.</span></span>

<span data-ttu-id="9e9fa-209">Virtuální počítač s názvem aktuálně poskytuje Azure **systému Windows Server 2016 s kontejnery**.</span><span class="sxs-lookup"><span data-stu-id="9e9fa-209">Azure currently provides a VM named **Windows Server 2016 with Containers**.</span></span> <span data-ttu-id="9e9fa-210">Můžete vyzkoušet nové funkce kontejneru systému Windows Server s Windows Server Core nebo Windows Nano Server můžete použít tento virtuální počítač.</span><span class="sxs-lookup"><span data-stu-id="9e9fa-210">You can use this VM to try the new Windows Server Container feature, with either Windows Server Core or Windows Nano Server.</span></span> <span data-ttu-id="9e9fa-211">Kontejner imagí operačního systému jsou nainstalované a je připravený k použití s Docker virtuálního počítače.</span><span class="sxs-lookup"><span data-stu-id="9e9fa-211">Container OS images are installed, and then the VM is ready to use with Docker.</span></span>

### <a name="benefits"></a><span data-ttu-id="9e9fa-212">Výhody</span><span class="sxs-lookup"><span data-stu-id="9e9fa-212">Benefits</span></span>

<span data-ttu-id="9e9fa-213">I když Windows kontejnery mohou být nasazeny do místní 2016 virtuálních počítačů Windows serveru, když nasadíte do Azure, můžete získat snadný způsob, jak začít pracovat s virtuálními počítači kontejneru připravené k použití Windows serveru.</span><span class="sxs-lookup"><span data-stu-id="9e9fa-213">Although Windows Containers can be deployed to on-premises Windows Server 2016 VMs, when you deploy to Azure, you get an easier way to get started, with ready-to-use Windows Server Container VMs.</span></span> <span data-ttu-id="9e9fa-214">Můžete také získat běžné online umístění, které je přístupné pro testery a automatické škálovatelnost prostřednictvím sady škálování virtuálního počítače Azure.</span><span class="sxs-lookup"><span data-stu-id="9e9fa-214">You also get a common online location that’s accessible to testers, and automatic scalability through Azure virtual machine scale sets.</span></span>

### <a name="next-steps"></a><span data-ttu-id="9e9fa-215">Další kroky</span><span class="sxs-lookup"><span data-stu-id="9e9fa-215">Next steps</span></span>

<span data-ttu-id="9e9fa-216">Prozkoumejte podrobnější tento obsah na stránkách wiki Githubu:</span><span class="sxs-lookup"><span data-stu-id="9e9fa-216">Explore this content more in-depth on the GitHub wiki:</span></span>

[https://github.com/dotnet-architecture/eShopModernizing/wiki/03.-How-to-deploy-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/03.-How-to-deploy-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD))

## <a name="walkthrough-4-deploy-your-windows-containers-based-apps-to-azure-container-instances-aci"></a><span data-ttu-id="9e9fa-217">Návod 4: Nasazení aplikace na základě kontejnery Windows do Azure kontejner instancí (ACI)</span><span class="sxs-lookup"><span data-stu-id="9e9fa-217">Walkthrough 4: Deploy your Windows Containers-based apps to Azure Container Instances (ACI)</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="9e9fa-218">Technické návod dostupnosti</span><span class="sxs-lookup"><span data-stu-id="9e9fa-218">Technical walkthrough availability</span></span>

<span data-ttu-id="9e9fa-219">Úplné technické návod je k dispozici na stránkách wiki úložišti GitHub eShopModernizing:</span><span class="sxs-lookup"><span data-stu-id="9e9fa-219">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki:</span></span>

<span data-ttu-id="9e9fa-220">[Nasazení aplikace do ACI (instance kontejner Azure)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances))</span><span class="sxs-lookup"><span data-stu-id="9e9fa-220">[Deploying the Apps to ACI (Azure Container Instances)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances))</span></span>

### <a name="overview"></a><span data-ttu-id="9e9fa-221">Přehled</span><span class="sxs-lookup"><span data-stu-id="9e9fa-221">Overview</span></span>

<span data-ttu-id="9e9fa-222">[Instance Azure kontejneru (ACI)](https://docs.microsoft.com/en-us/azure/container-instances/) je nejrychlejší způsob, jak mají dev/testovací/pracovní prostředí kontejnery, kde můžete nasadit jeden instancí kontejnerů.</span><span class="sxs-lookup"><span data-stu-id="9e9fa-222">[Azure Container Instances (ACI)](https://docs.microsoft.com/en-us/azure/container-instances/) is the quickest way to have a Containers dev/test/staging environment where you can deploy single instances of containers.</span></span>

### <a name="goals"></a><span data-ttu-id="9e9fa-223">Cíle</span><span class="sxs-lookup"><span data-stu-id="9e9fa-223">Goals</span></span>

<span data-ttu-id="9e9fa-224">Tento návod ukazuje základní scénáře při nasazování Windows kontejnery Azure kontejner instancí (ACI) a jak můžete nasadit aplikace eShopModernizing do ACI.</span><span class="sxs-lookup"><span data-stu-id="9e9fa-224">This walkthrough shows you the main scenarios when deploying Windows Containers to Azure Container Instances (ACI) and how you can deploy eShopModernizing Apps into ACI.</span></span>

### <a name="scenarios"></a><span data-ttu-id="9e9fa-225">Scénáře</span><span class="sxs-lookup"><span data-stu-id="9e9fa-225">Scenarios</span></span>

<span data-ttu-id="9e9fa-226">Může být variace o nasazování aplikací eShopModernizing do ACI jako je nasazení jenom jednoho nebo všech aplikací (aplikace MVC, WebForms aplikaci nebo službu WCF).</span><span class="sxs-lookup"><span data-stu-id="9e9fa-226">There can be variations about deploying the eShopModernizing apps into ACI such as deploying just one or all of the apps (MVC app, WebForms app or WCF service).</span></span> <span data-ttu-id="9e9fa-227">V následujícím scénáři znázorněném uvidíte aplikace ASP.NET MVC a kontejneru systému SQL Server oba dva nasazené jako kontejnery do ACI (instance kontejner Azure).</span><span class="sxs-lookup"><span data-stu-id="9e9fa-227">In the following scenario shown below you can see the ASP.NET MVC app plus the SQL Server container both of them deployed as containers into ACI (Azure Container Instances).</span></span>

![Nasazení na ACI z prostředí pro vývoj](./media/image5-3.5.6.png)

### <a name="benefits"></a><span data-ttu-id="9e9fa-229">Výhody</span><span class="sxs-lookup"><span data-stu-id="9e9fa-229">Benefits</span></span>

<span data-ttu-id="9e9fa-230">Azure instancí kontejnerů umožňuje snadno vytvářet a spravovat Docker kontejnerů v Azure, aniž by museli zřizovat virtuální počítače nebo přijmou vyšší úrovně služby.</span><span class="sxs-lookup"><span data-stu-id="9e9fa-230">Azure Container Instances makes it easy to create and manage Docker containers in Azure, without having to provision virtual machines or adopt a higher-level service.</span></span> <span data-ttu-id="9e9fa-231">S ACI můžete přímo nasazení kontejneru systému Windows v Azure a umístěte ji do internet s platný plně kvalifikovaný název domény (FQDN) v řádu sekund (za předpokladu, že máte připravené bitové kopie kontejneru systému Windows v registru Docker jako úložiště Docker Hub nebo kontejneru Azure Registr).</span><span class="sxs-lookup"><span data-stu-id="9e9fa-231">With ACI, you can directly deploy a Windows container in Azure and expose it to the internet with a fully qualified domain name (FQDN) in a matter of seconds (Provided that you have the Windows Container image ready in a Docker registry like Docker Hub or Azure Container Registry).</span></span>

### <a name="considerations"></a><span data-ttu-id="9e9fa-232">Důležité informace</span><span class="sxs-lookup"><span data-stu-id="9e9fa-232">Considerations</span></span>

<span data-ttu-id="9e9fa-233">Nasazení Windows kontejnery s buď úplné rozhraní .NET Framework / ASP.NET nebo SQL Server do Azure kontejner instancí (ACI) není dost tak rychlý jako nasazení na regulární Docker hostitele (např. Windows Server 2016 s kontejnery Windows), protože bitovou kopii Docker musí být Stáhnout (načtený z registru Docker) pokaždé, když a velikosti bitové kopie kontejneru SQL (15.1 GB) a bitovou kopii kontejneru ASP.NET (13.9 GB) jsou výrazně velký, ale je výrazně levnější než zachování vlastní hostitelů docker (trvale online Windows Server 2016 se virtuální počítač s Windows kontejnerů v Azure) není abychom zmínili celou orchestrator jako Kubernetes v Azure (AKS/ACS) nebo Azure Service Fabric, které jsou na druhé straně skvělé možnosti pro nasazení v produkčním prostředí.</span><span class="sxs-lookup"><span data-stu-id="9e9fa-233">Deploying Windows Containers with either full .NET Framework / ASP.NET or SQL Server into Azure Container Instances (ACI) is not quite as fast as deploying to a regular Docker Host (like a Windows Server 2016 with Windows Containers) because the Docker image has to be downloaded (pulled from the Docker registry) every time and the sizes of the SQL container image (15.1 GB) and the ASP.NET container image (13.9 GB) are significantly large, however it is much cheaper than maintaining your own docker host (permanently on-line Windows Server 2016 with Windows Containers VM in Azure) not to mention a whole orchestrator like Kubernetes in Azure (AKS/ACS) or Azure Service Fabric which are, on the other hand, great choices for production deployments.</span></span>

<span data-ttu-id="9e9fa-234">Jako hlavní uzavření pomocí Azure kontejner instancí je velmi poutavé možnost pro scénáře vývoje/testování a CI/CD kanály.</span><span class="sxs-lookup"><span data-stu-id="9e9fa-234">As main conclusion, using Azure Container Instances is a very compelling option for Dev/Test scenarios and for CI/CD pipelines.</span></span>

## <a name="next-steps"></a><span data-ttu-id="9e9fa-235">Další kroky</span><span class="sxs-lookup"><span data-stu-id="9e9fa-235">Next steps</span></span>

<span data-ttu-id="9e9fa-236">Prozkoumejte podrobnější tento obsah na stránkách wiki Githubu:</span><span class="sxs-lookup"><span data-stu-id="9e9fa-236">Explore this content more in-depth on the GitHub wiki:</span></span> 

[https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances)TBD)


## <a name="walkthrough-5-deploy-your-windows-containers-based-apps-to-kubernetes-in-azure-container-service"></a><span data-ttu-id="9e9fa-237">Návod 5: Nasazení aplikace na základě kontejnery Windows do Kubernetes v Azure Container Service</span><span class="sxs-lookup"><span data-stu-id="9e9fa-237">Walkthrough 5: Deploy your Windows Containers-based apps to Kubernetes in Azure Container Service</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="9e9fa-238">Technické návod dostupnosti</span><span class="sxs-lookup"><span data-stu-id="9e9fa-238">Technical walkthrough availability</span></span>

<span data-ttu-id="9e9fa-239">Úplné technické návod je k dispozici na stránkách wiki úložišti GitHub eShopModernizing:</span><span class="sxs-lookup"><span data-stu-id="9e9fa-239">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki:</span></span>

[https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-C-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-C-CD))

### <a name="overview"></a><span data-ttu-id="9e9fa-240">Přehled</span><span class="sxs-lookup"><span data-stu-id="9e9fa-240">Overview</span></span>

<span data-ttu-id="9e9fa-241">Aplikace, která je založena na systému Windows kontejnery rychle muset platformy, přesunutí i další počítače z virtuálních počítačů IaaS.</span><span class="sxs-lookup"><span data-stu-id="9e9fa-241">An application that's based on Windows Containers will quickly need to use platforms, moving even further away from IaaS VMs.</span></span> <span data-ttu-id="9e9fa-242">To je potřeba snadno dosáhnout vysoké škálovatelnost a lépe automatizované škálovatelnost a pro přináší značné vylepšení v automatizované nasazení a správa verzí.</span><span class="sxs-lookup"><span data-stu-id="9e9fa-242">This is needed to easily achieve high scalability and better automated scalability, and for a significant improvement in automated deployments and versioning.</span></span> <span data-ttu-id="9e9fa-243">Tyto cíle můžete dosáhnout pomocí orchestrator [Kubernetes](https://kubernetes.io/), k dispozici v [služby kontejneru Azure](https://azure.microsoft.com/services/container-service/).</span><span class="sxs-lookup"><span data-stu-id="9e9fa-243">You can achieve these goals by using the orchestrator [Kubernetes](https://kubernetes.io/), available in [Azure Container Services](https://azure.microsoft.com/services/container-service/).</span></span>

### <a name="goals"></a><span data-ttu-id="9e9fa-244">Cíle</span><span class="sxs-lookup"><span data-stu-id="9e9fa-244">Goals</span></span>

<span data-ttu-id="9e9fa-245">Cílem tohoto návodu je další informace o nasazení aplikace na základě kontejneru systému Windows k Kubernetes (také nazývané *K8s*) v Azure Container Service.</span><span class="sxs-lookup"><span data-stu-id="9e9fa-245">The goal of this walkthrough is to learn how to deploy a Windows Container–based application to Kubernetes (also called *K8s*) in Azure Container Service.</span></span> <span data-ttu-id="9e9fa-246">Nasazení do Kubernetes od začátku je dvoustupňový proces:</span><span class="sxs-lookup"><span data-stu-id="9e9fa-246">Deploying to Kubernetes from scratch is a two-step process:</span></span>

1.  <span data-ttu-id="9e9fa-247">Nasaďte Kubernetes clusteru Azure Container Service.</span><span class="sxs-lookup"><span data-stu-id="9e9fa-247">Deploy a Kubernetes cluster to Azure Container Service.</span></span>

2.  <span data-ttu-id="9e9fa-248">Nasazení aplikace a související prostředky do clusteru Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="9e9fa-248">Deploy the application and related resources to the Kubernetes cluster.</span></span>

### <a name="scenarios"></a><span data-ttu-id="9e9fa-249">Scénáře</span><span class="sxs-lookup"><span data-stu-id="9e9fa-249">Scenarios</span></span>

#### <a name="scenario-a-deploy-directly-to-a-kubernetes-cluster-from-a-dev-environment"></a><span data-ttu-id="9e9fa-250">Scénář A: nasadit přímo do clusteru s podporou Kubernetes z prostředí vývojářů</span><span class="sxs-lookup"><span data-stu-id="9e9fa-250">Scenario A: Deploy directly to a Kubernetes cluster from a dev environment</span></span>

![Nasazení přímo na clusteru s podporou Kubernetes z prostředí pro vývoj](./media/image5-7.png)

> <span data-ttu-id="9e9fa-252">**Obrázek 5 – 7.**</span><span class="sxs-lookup"><span data-stu-id="9e9fa-252">**Figure 5-7.**</span></span> <span data-ttu-id="9e9fa-253">Nasazení přímo na clusteru s podporou Kubernetes z prostředí pro vývoj</span><span class="sxs-lookup"><span data-stu-id="9e9fa-253">Deploy directly to a Kubernetes cluster from a development environment</span></span>

#### <a name="scenario-b-deploy-to-a-kubernetes-cluster-from-cicd-pipelines-in-team-services"></a><span data-ttu-id="9e9fa-254">Scénář B: nasadit do clusteru s podporou Kubernetes z položek konfigurace nebo CD kanálů v Team Services</span><span class="sxs-lookup"><span data-stu-id="9e9fa-254">Scenario B: Deploy to a Kubernetes cluster from CI/CD pipelines in Team Services</span></span>

![Nasazení do clusteru s podporou Kubernetes z položek konfigurace nebo CD kanály v Team Services](./media/image5-8.png)

> <span data-ttu-id="9e9fa-256">**Obrázek 5-8.**</span><span class="sxs-lookup"><span data-stu-id="9e9fa-256">**Figure 5-8.**</span></span> <span data-ttu-id="9e9fa-257">Nasazení do clusteru s podporou Kubernetes z položek konfigurace nebo CD kanály v Team Services</span><span class="sxs-lookup"><span data-stu-id="9e9fa-257">Deploy to a Kubernetes cluster from CI/CD pipelines in Team Services</span></span>

### <a name="benefits"></a><span data-ttu-id="9e9fa-258">Výhody</span><span class="sxs-lookup"><span data-stu-id="9e9fa-258">Benefits</span></span>

<span data-ttu-id="9e9fa-259">Existuje mnoho výhod nasazení do clusteru s podporou v Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="9e9fa-259">There are many benefits to deploying to a cluster in Kubernetes.</span></span> <span data-ttu-id="9e9fa-260">Největší výhodou je, že dostanete prostředí produkční prostředí, ve kterém můžete škálovat aplikace založené na počet instancí kontejneru, které chcete použít (vnitřní škálovatelnost v existujícím uzlům) a na základě počtu uzlů nebo virtuální počítače v clusteru ( Globální škálovatelnost clusteru).</span><span class="sxs-lookup"><span data-stu-id="9e9fa-260">The biggest benefit is that you get a production-ready environment in which you can scale out the application based on the number of container instances you want to use (inner-scalability in the existing nodes), and based on the number of nodes or VMs in the cluster (global scalability of the cluster).</span></span>

<span data-ttu-id="9e9fa-261">Azure Container Service optimalizuje oblíbených open-source nástrojů a technologií speciálně pro Azure.</span><span class="sxs-lookup"><span data-stu-id="9e9fa-261">Azure Container Service optimizes popular open-source tools and technologies specifically for Azure.</span></span> <span data-ttu-id="9e9fa-262">Získat otevřete řešení, která nabízí přenositelnost pro vaše kontejnery i pro konfiguraci aplikace.</span><span class="sxs-lookup"><span data-stu-id="9e9fa-262">You get an open solution that offers portability, both for your containers and for your application configuration.</span></span> <span data-ttu-id="9e9fa-263">Vyberte velikost, počtu hostitelů, a nástrojů orchestrator-kontejneru služby zpracovává nic jiného.</span><span class="sxs-lookup"><span data-stu-id="9e9fa-263">You select the size, the number of hosts, and the orchestrator tools-Container Service handles everything else.</span></span>

<span data-ttu-id="9e9fa-264">S Kubernetes mohou vývojáři průběhu od přemýšlení o fyzické a virtuální počítače k plánování zaměřené na kontejner infrastruktury, která usnadňuje následující funkce, mimo jiné:</span><span class="sxs-lookup"><span data-stu-id="9e9fa-264">With Kubernetes, developers can progress from thinking about physical and virtual machines, to planning a container-centric infrastructure that facilitates the following capabilities, among others:</span></span>

- <span data-ttu-id="9e9fa-265">Aplikace založené na několika kontejnerů</span><span class="sxs-lookup"><span data-stu-id="9e9fa-265">Applications based on multiple containers</span></span>

- <span data-ttu-id="9e9fa-266">Replikace instancí kontejnerů a vodorovné automatické škálování</span><span class="sxs-lookup"><span data-stu-id="9e9fa-266">Replicating container instances and horizontal autoscaling</span></span>

- <span data-ttu-id="9e9fa-267">Pojmenování a zjišťování (například interní DNS)</span><span class="sxs-lookup"><span data-stu-id="9e9fa-267">Naming and discovering (for example, internal DNS)</span></span>

- <span data-ttu-id="9e9fa-268">Vyrovnávání zatížení</span><span class="sxs-lookup"><span data-stu-id="9e9fa-268">Balancing loads</span></span>

- <span data-ttu-id="9e9fa-269">Vrácení aktualizace</span><span class="sxs-lookup"><span data-stu-id="9e9fa-269">Rolling updates</span></span>

- <span data-ttu-id="9e9fa-270">Distribuce tajné klíče</span><span class="sxs-lookup"><span data-stu-id="9e9fa-270">Distributing secrets</span></span>

- <span data-ttu-id="9e9fa-271">Kontroly stavu aplikace</span><span class="sxs-lookup"><span data-stu-id="9e9fa-271">Application health checks</span></span>

## <a name="next-steps"></a><span data-ttu-id="9e9fa-272">Další kroky</span><span class="sxs-lookup"><span data-stu-id="9e9fa-272">Next steps</span></span>

<span data-ttu-id="9e9fa-273">Prozkoumejte podrobnější tento obsah na stránkách wiki Githubu: [https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-C-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-C-CD))</span><span class="sxs-lookup"><span data-stu-id="9e9fa-273">Explore this content more in-depth on the GitHub wiki: [https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-C-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-C-CD))</span></span>

## <a name="walkthrough-6-deploy-your-windows-containers-based-apps-to-azure-service-fabric"></a><span data-ttu-id="9e9fa-274">Návod 6: Nasazení aplikace na základě kontejnery Windows do Azure Service Fabric</span><span class="sxs-lookup"><span data-stu-id="9e9fa-274">Walkthrough 6: Deploy your Windows Containers-based apps to Azure Service Fabric</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="9e9fa-275">Technické návod dostupnosti</span><span class="sxs-lookup"><span data-stu-id="9e9fa-275">Technical walkthrough availability</span></span>

<span data-ttu-id="9e9fa-276">Úplné technické návod je k dispozici na stránkách wiki úložišti GitHub eShopModernizing:</span><span class="sxs-lookup"><span data-stu-id="9e9fa-276">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki:</span></span>

[https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-How-to-deploy-your-Windows-Containers-based-apps-into-Azure-Service-Fabric-(Including-CI-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-How-to-deploy-your-Windows-Containers-based-apps-into-Azure-Service-Fabric-(Including-CI-CD))

### <a name="overview"></a><span data-ttu-id="9e9fa-277">Přehled</span><span class="sxs-lookup"><span data-stu-id="9e9fa-277">Overview</span></span>

<span data-ttu-id="9e9fa-278">Aplikace založené na Windows kontejnery rychle musí používat platforem, přesunutí i další počítače z virtuálních počítačů IaaS.</span><span class="sxs-lookup"><span data-stu-id="9e9fa-278">An application based on Windows Containers quickly needs to use platforms, moving even further away from IaaS VMs.</span></span> <span data-ttu-id="9e9fa-279">To je potřeba snadno dosáhnout vysoké škálovatelnost a lépe automatizované škálovatelnost a pro přináší značné vylepšení v automatizované nasazení a správa verzí.</span><span class="sxs-lookup"><span data-stu-id="9e9fa-279">This is needed to easily achieve high scalability and better automated scalability, and for a significant improvement in automated deployments and versioning.</span></span> <span data-ttu-id="9e9fa-280">Pomocí orchestrator Azure Service Fabric, která je k dispozici v cloudu Azure, ale také k dispozici pro použití v místě, nebo i v různých veřejného cloudu, můžete dosáhnout těchto cílů.</span><span class="sxs-lookup"><span data-stu-id="9e9fa-280">You can achieve these goals by using the orchestrator Azure Service Fabric, which is available in the Azure cloud, but also available to use on-premises, or even in a different public cloud.</span></span>

### <a name="goals"></a><span data-ttu-id="9e9fa-281">Cíle</span><span class="sxs-lookup"><span data-stu-id="9e9fa-281">Goals</span></span>

<span data-ttu-id="9e9fa-282">Cílem tohoto návodu je další informace o nasazení aplikace na základě kontejneru systému Windows do clusteru Service Fabric v Azure.</span><span class="sxs-lookup"><span data-stu-id="9e9fa-282">The goal of this walkthrough is to learn how to deploy a Windows Container–based application to a Service Fabric cluster in Azure.</span></span> <span data-ttu-id="9e9fa-283">Nasazení do Service Fabric od začátku je dvoustupňový proces:</span><span class="sxs-lookup"><span data-stu-id="9e9fa-283">Deploying to Service Fabric from scratch is a two-step process:</span></span>

1.  <span data-ttu-id="9e9fa-284">Cluster Service Fabric nasaďte do Azure (nebo do různých prostředí).</span><span class="sxs-lookup"><span data-stu-id="9e9fa-284">Deploy a Service Fabric cluster to Azure (or to a different environment).</span></span>

2.  <span data-ttu-id="9e9fa-285">Nasaďte aplikace a související prostředky do clusteru Service Fabric.</span><span class="sxs-lookup"><span data-stu-id="9e9fa-285">Deploy the application and related resources to the Service Fabric cluster.</span></span>

### <a name="scenarios"></a><span data-ttu-id="9e9fa-286">Scénáře</span><span class="sxs-lookup"><span data-stu-id="9e9fa-286">Scenarios</span></span>

#### <a name="scenario-a-deploy-directly-to-a-service-fabric-cluster-from-a-dev-environment"></a><span data-ttu-id="9e9fa-287">Scénář A: nasadit přímo na clusteru Service Fabric z prostředí vývojářů</span><span class="sxs-lookup"><span data-stu-id="9e9fa-287">Scenario A: Deploy directly to a Service Fabric cluster from a dev environment</span></span>

![Nasazení z prostředí pro vývoj přímo na clusteru Service Fabric](./media/image5-9.png)

> <span data-ttu-id="9e9fa-289">**Obrázek 5-9.**</span><span class="sxs-lookup"><span data-stu-id="9e9fa-289">**Figure 5-9.**</span></span> <span data-ttu-id="9e9fa-290">Nasazení z prostředí pro vývoj přímo na clusteru Service Fabric</span><span class="sxs-lookup"><span data-stu-id="9e9fa-290">Deploy directly to a Service Fabric cluster from a development environment</span></span>

### <a name="scenario-b-deploy-to-a-service-fabric-cluster-from-cicd-pipelines-in-team-services"></a><span data-ttu-id="9e9fa-291">Scénář B: nasadit do clusteru Service Fabric z položek konfigurace nebo CD kanálů v Team Services</span><span class="sxs-lookup"><span data-stu-id="9e9fa-291">Scenario B: Deploy to a Service Fabric cluster from CI/CD pipelines in Team Services</span></span>

![Nasazení na cluster Service Fabric z položek konfigurace nebo CD kanály v sadě Visual Studio Team Services](./media/image5-10.png)

> <span data-ttu-id="9e9fa-293">**Obrázek 5-10.**</span><span class="sxs-lookup"><span data-stu-id="9e9fa-293">**Figure 5-10.**</span></span> <span data-ttu-id="9e9fa-294">Nasazení na cluster Service Fabric z položek konfigurace nebo CD kanály v sadě Visual Studio Team Services</span><span class="sxs-lookup"><span data-stu-id="9e9fa-294">Deploy to a Service Fabric cluster from CI/CD pipelines in Visual Studio Team Services</span></span>

## <a name="benefits"></a><span data-ttu-id="9e9fa-295">Výhody</span><span class="sxs-lookup"><span data-stu-id="9e9fa-295">Benefits</span></span>

<span data-ttu-id="9e9fa-296">Výhody nasazení na cluster Service Fabric se podobá výhody použití Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="9e9fa-296">The benefits of deploying to a cluster in Service Fabric are similar to the benefits of using Kubernetes.</span></span> <span data-ttu-id="9e9fa-297">Jeden rozdíl, ale je, že Service Fabric je víc vyspělých produkčním prostředí pro aplikace systému Windows ve srovnání s Kubernetes, který je ve fázi beta verzi pro Windows kontejnery v Kubernetes verze 1.9 (2017 prosince).</span><span class="sxs-lookup"><span data-stu-id="9e9fa-297">One difference, though, is that Service Fabric is a more mature production environment for Windows applications compared to Kubernetes, which is in a beta phase for Windows Containers in Kubernetes version 1.9 (December 2017).</span></span> <span data-ttu-id="9e9fa-298">Kubernetes je víc vyspělých prostředí pro Linux.</span><span class="sxs-lookup"><span data-stu-id="9e9fa-298">Kubernetes is a more mature environment for Linux.</span></span>

<span data-ttu-id="9e9fa-299">Hlavní výhodou používání Azure Service Fabric je, že dostanete prostředí produkční prostředí, ve kterém můžete škálovat aplikace založené na počet instancí kontejneru, které chcete použít (vnitřní škálovatelnost v existujícím uzlům) a na základě počtu uzly nebo virtuální počítače v clusteru (globální škálovatelnost clusteru).</span><span class="sxs-lookup"><span data-stu-id="9e9fa-299">The main benefit of using Azure Service Fabric is that you get a production-ready environment in which you can scale out the application based on the number of container instances you want to use (inner-scalability in the existing nodes), and based on the number of nodes or VMs in the cluster (global scalability of the cluster).</span></span>

<span data-ttu-id="9e9fa-300">Azure Service Fabric nabízí přenositelnost pro vaše kontejnery i pro konfiguraci aplikace.</span><span class="sxs-lookup"><span data-stu-id="9e9fa-300">Azure Service Fabric offers portability both for your containers and for your application configuration.</span></span> <span data-ttu-id="9e9fa-301">Můžete mít Service Fabric cluster v Azure a nainstalujte ji na místě ve svém vlastním datovém centru.</span><span class="sxs-lookup"><span data-stu-id="9e9fa-301">You can have a Service Fabric cluster in Azure, or install it on-premises in your own datacenter.</span></span> <span data-ttu-id="9e9fa-302">Můžete nainstalovat i clusteru Service Fabric v jiném cloudu, jako je třeba [Amazon AWS](https://blogs.msdn.microsoft.com/azureservicefabric/2017/05/18/tutorial-how-to-create-a-service-fabric-standalone-cluster-with-aws-ec2-instances/).</span><span class="sxs-lookup"><span data-stu-id="9e9fa-302">You can even install a Service Fabric cluster in a different cloud, like [Amazon AWS](https://blogs.msdn.microsoft.com/azureservicefabric/2017/05/18/tutorial-how-to-create-a-service-fabric-standalone-cluster-with-aws-ec2-instances/).</span></span>

<span data-ttu-id="9e9fa-303">Pomocí Service Fabric mohou vývojáři průběhu od přemýšlení o fyzické a virtuální počítače k plánování zaměřené na kontejner infrastruktury, která usnadňuje následující funkce, mimo jiné:</span><span class="sxs-lookup"><span data-stu-id="9e9fa-303">With Service Fabric, developers can progress from thinking about physical and virtual machines to planning a container-centric infrastructure that facilitates the following capabilities, among others:</span></span>

- <span data-ttu-id="9e9fa-304">Aplikace založené na několika kontejnerů.</span><span class="sxs-lookup"><span data-stu-id="9e9fa-304">Applications based on multiple containers.</span></span>

- <span data-ttu-id="9e9fa-305">Replikace instancí kontejnerů a vodorovné automatické škálování.</span><span class="sxs-lookup"><span data-stu-id="9e9fa-305">Replicating container instances and horizontal autoscaling.</span></span>

- <span data-ttu-id="9e9fa-306">Pojmenování a zjišťování (například interní DNS).</span><span class="sxs-lookup"><span data-stu-id="9e9fa-306">Naming and discovering (for example, internal DNS).</span></span>

- <span data-ttu-id="9e9fa-307">Vyrovnávání zatížení.</span><span class="sxs-lookup"><span data-stu-id="9e9fa-307">Balancing loads.</span></span>

- <span data-ttu-id="9e9fa-308">Vrácení aktualizace.</span><span class="sxs-lookup"><span data-stu-id="9e9fa-308">Rolling updates.</span></span>

- <span data-ttu-id="9e9fa-309">Distribuce tajných klíčů.</span><span class="sxs-lookup"><span data-stu-id="9e9fa-309">Distributing secrets.</span></span>

- <span data-ttu-id="9e9fa-310">Kontroluje stav aplikací.</span><span class="sxs-lookup"><span data-stu-id="9e9fa-310">Application health checks.</span></span>

<span data-ttu-id="9e9fa-311">Následující funkce jsou výhradní v Service Fabric (ve srovnání s další orchestrators):</span><span class="sxs-lookup"><span data-stu-id="9e9fa-311">The following capabilities are exclusive in Service Fabric (compared to other orchestrators):</span></span>

- <span data-ttu-id="9e9fa-312">Funkce stavové služby prostřednictvím modelu aplikací spolehlivé služby.</span><span class="sxs-lookup"><span data-stu-id="9e9fa-312">Stateful services capability, through the Reliable Services application model.</span></span>

- <span data-ttu-id="9e9fa-313">Vzor aktéři prostřednictvím aplikačního modelu Reliable Actors.</span><span class="sxs-lookup"><span data-stu-id="9e9fa-313">Actors pattern, through the Reliable Actors application model.</span></span>

- <span data-ttu-id="9e9fa-314">Nasaďte úplné kost procesy, kromě kontejnery systému Windows nebo Linux.</span><span class="sxs-lookup"><span data-stu-id="9e9fa-314">Deploy bare-bone processes, in addition to Windows or Linux containers.</span></span>

- <span data-ttu-id="9e9fa-315">Rozšířené kumulativní aktualizace a kontroly stavu.</span><span class="sxs-lookup"><span data-stu-id="9e9fa-315">Advanced rolling updates and health checks.</span></span>

### <a name="next-steps"></a><span data-ttu-id="9e9fa-316">Další kroky</span><span class="sxs-lookup"><span data-stu-id="9e9fa-316">Next steps</span></span>

<span data-ttu-id="9e9fa-317">Prozkoumejte podrobnější tento obsah na stránkách wiki Githubu:</span><span class="sxs-lookup"><span data-stu-id="9e9fa-317">Explore this content more in-depth on the GitHub wiki:</span></span>

[https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-How-to-deploy-your-Windows-Containers-based-apps-into-Azure-Service-Fabric-(Including-CI-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-How-to-deploy-your-Windows-Containers-based-apps-into-Azure-Service-Fabric-(Including-CI-CD))

>[!div class="step-by-step"]
<span data-ttu-id="9e9fa-318">[Předchozí](lift-and-shift-existing-apps-devops/migrate-to-hybrid-cloud-scenarios.md)
[další](conclusions.md)</span><span class="sxs-lookup"><span data-stu-id="9e9fa-318">[Previous](lift-and-shift-existing-apps-devops/migrate-to-hybrid-cloud-scenarios.md)
[Next](conclusions.md)</span></span>
