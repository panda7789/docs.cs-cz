---
title: Návody a přehled technických začátků
description: Modernizace existujících aplikací .NET pomocí Azure Cloudu a kontejnerů Windows | Přehled návodů a technických začátků
ms.date: 04/28/2018
ms.openlocfilehash: 190b33c4307b09bab0543d481e66ac9328074a0d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "69660888"
---
# <a name="walkthroughs-and-technical-get-started-overview"></a><span data-ttu-id="c881f-103">Návody a přehled technických začátků</span><span class="sxs-lookup"><span data-stu-id="c881f-103">Walkthroughs and technical get started overview</span></span>

<span data-ttu-id="c881f-104">Chcete-li omezit velikost této e-knihy, další technická dokumentace a úplné návody byly k dispozici v úložišti GitHub.</span><span class="sxs-lookup"><span data-stu-id="c881f-104">To limit the size of this e-book, additional technical documentation and the full walkthroughs were made available in a GitHub repository.</span></span> <span data-ttu-id="c881f-105">Online série návodů, která je popsána v této kapitole, zahrnuje podrobné nastavení více prostředí, která jsou založená na kontejnerech Windows, a nasazení do Azure.</span><span class="sxs-lookup"><span data-stu-id="c881f-105">The online series of walkthroughs that is described in this chapter covers the step-by-step setup of the multiple environments that are based on Windows Containers, and deployment to Azure.</span></span>

<span data-ttu-id="c881f-106">V následujících částech je vysvětleno, o čem je každý návod, jeho cíle a vize na vysoké úrovni a poskytuje diagram úkolů, které jsou zapojeny.</span><span class="sxs-lookup"><span data-stu-id="c881f-106">The following sections explain what each walkthrough is about, its objectives and high-level vision, and provides a diagram of the tasks that are involved.</span></span> <span data-ttu-id="c881f-107">Návody můžete získat sami v *eShopmodernizing* apps GitHub <https://github.com/dotnet-architecture/eShopModernizing/wiki>repo wiki na .</span><span class="sxs-lookup"><span data-stu-id="c881f-107">You can get the walkthroughs themselves in the *eShopModernizing* apps GitHub repo wiki at <https://github.com/dotnet-architecture/eShopModernizing/wiki>.</span></span>

## <a name="technical-walkthrough-list"></a><span data-ttu-id="c881f-108">Technický seznam návodu</span><span class="sxs-lookup"><span data-stu-id="c881f-108">Technical walkthrough list</span></span>

<span data-ttu-id="c881f-109">Následující návody pro získání práce poskytují konzistentní a komplexní technické pokyny pro ukázkové aplikace, které můžete zvedat a přesouvat pomocí kontejnerů a pak se přesunout pomocí několika možností nasazení v Azure.</span><span class="sxs-lookup"><span data-stu-id="c881f-109">The following get-started walkthroughs provide consistent and comprehensive technical guidance for sample apps that you can lift and shift by using containers, and then move by using multiple deployment choices in Azure.</span></span>

<span data-ttu-id="c881f-110">Každý z následujících návodů používá nové ukázkové aplikace eShopLegacy a eShopModernizing, které jsou dostupné na GitHubu na adrese <https://github.com/dotnet-architecture/eShopModernizing>.</span><span class="sxs-lookup"><span data-stu-id="c881f-110">Each of the following walkthroughs uses the new sample eShopLegacy and eShopModernizing apps, which are available on GitHub at <https://github.com/dotnet-architecture/eShopModernizing>.</span></span>

- <span data-ttu-id="c881f-111">**Prohlídka starších aplikací eShopu (základní aplikace pro modernizaci)**</span><span class="sxs-lookup"><span data-stu-id="c881f-111">**Tour of eShop legacy apps (baseline apps to modernize)**</span></span>

- <span data-ttu-id="c881f-112">**Kontejnerujte stávající ASP.NET webové aplikace (WebForms & MVC) pomocí kontejnerů s Windows**</span><span class="sxs-lookup"><span data-stu-id="c881f-112">**Containerize your existing ASP.NET web apps (WebForms & MVC) with Windows Containers**</span></span>

- <span data-ttu-id="c881f-113">**Kontejnerujte stávající služby WCF (aplikace N-Tier) pomocí kontejnerů windows**</span><span class="sxs-lookup"><span data-stu-id="c881f-113">**Containerize your existing WCF services (N-Tier apps) with Windows Containers**</span></span>

- <span data-ttu-id="c881f-114">**Nasazení aplikace založené na kontejnerech Windows do virtuálních aplikací Azure**</span><span class="sxs-lookup"><span data-stu-id="c881f-114">**Deploy your Windows Containers-based app to Azure VMs**</span></span>

- <span data-ttu-id="c881f-115">**Nasazení aplikací založených na kontejnerech Windows do Kubernetes ve službě Azure Container Service**</span><span class="sxs-lookup"><span data-stu-id="c881f-115">**Deploy your Windows Containers-based apps to Kubernetes in Azure Container Service**</span></span>

## <a name="walkthrough-1-tour-of-eshop-legacy-apps"></a><span data-ttu-id="c881f-116">Návod 1: Prohlídka starších aplikací eShopu</span><span class="sxs-lookup"><span data-stu-id="c881f-116">Walkthrough 1: Tour of eShop legacy apps</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="c881f-117">Dostupnost technického návodu</span><span class="sxs-lookup"><span data-stu-id="c881f-117">Technical walkthrough availability</span></span>

<span data-ttu-id="c881f-118">Úplný technický návod je k dispozici v eShopModernizing GitHub repo wiki:</span><span class="sxs-lookup"><span data-stu-id="c881f-118">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki:</span></span>

[<span data-ttu-id="c881f-119">eShopModernizing wiki návody</span><span class="sxs-lookup"><span data-stu-id="c881f-119">eShopModernizing wiki walkthroughs</span></span>](https://github.com/dotnet-architecture/eShopModernizing/wiki)

### <a name="overview"></a><span data-ttu-id="c881f-120">Přehled</span><span class="sxs-lookup"><span data-stu-id="c881f-120">Overview</span></span>

<span data-ttu-id="c881f-121">V tomto návodu můžete prozkoumat počáteční implementaci tří ukázkových starších aplikací.</span><span class="sxs-lookup"><span data-stu-id="c881f-121">In this walkthrough, you can explore the initial implementation of three sample legacy applications.</span></span> <span data-ttu-id="c881f-122">První dvě ukázkové webové aplikace mají monolitickou architekturu a byly vytvořeny pomocí klasické ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="c881f-122">The first two sample web apps have a monolithic architecture, and were created by using classic ASP.NET.</span></span> <span data-ttu-id="c881f-123">Jedna aplikace je založena na ASP.NET 4.x MVC; druhá aplikace je založena na ASP.NET 4.x Web Forms.</span><span class="sxs-lookup"><span data-stu-id="c881f-123">One application is based on ASP.NET 4.x MVC; the second application is based on ASP.NET 4.x Web Forms.</span></span>
<span data-ttu-id="c881f-124">Třetí aplikace je 3vrstvá aplikace složená z klientské aplikace WinForms a služby [WCF (Windows Communication Foundation)](../../framework/wcf/whats-wcf.md) na straně serveru.</span><span class="sxs-lookup"><span data-stu-id="c881f-124">The third app is a 3-Tier app composed by a client WinForms app and a server-side [Windows Communication Foundation (WCF)](../../framework/wcf/whats-wcf.md) service.</span></span>

<span data-ttu-id="c881f-125">Všechny tyto aplikace jsou k dispozici v [eShopmodernizing GitHub repo](https://github.com/dotnet-architecture/eShopModernizing).</span><span class="sxs-lookup"><span data-stu-id="c881f-125">All these applications are available at the [eShopModernizing GitHub repo](https://github.com/dotnet-architecture/eShopModernizing).</span></span>

### <a name="goals"></a><span data-ttu-id="c881f-126">Cíle</span><span class="sxs-lookup"><span data-stu-id="c881f-126">Goals</span></span>

<span data-ttu-id="c881f-127">Hlavním cílem tohoto návodu je jednoduše seznámit se s těmito aplikacemi a s jejich kódem a konfigurací.</span><span class="sxs-lookup"><span data-stu-id="c881f-127">The main goal of this walkthrough is simply to get familiar with these apps, and with their code and configuration.</span></span> <span data-ttu-id="c881f-128">Aplikace můžete nakonfigurovat tak, aby generovaly a používaly falešná data bez použití databáze SQL pro účely testování.</span><span class="sxs-lookup"><span data-stu-id="c881f-128">You can configure the apps so that they generate and use mock data, without using the SQL database, for testing purposes.</span></span> <span data-ttu-id="c881f-129">Tato volitelná konfigurace je založena na vkládání závislostí, a to odděleným způsobem.</span><span class="sxs-lookup"><span data-stu-id="c881f-129">This optional config is based on dependency injection, in a decoupled way.</span></span>

### <a name="scenario-1-aspnet-web-apps"></a><span data-ttu-id="c881f-130">Scénář 1: ASP.NET webových aplikací</span><span class="sxs-lookup"><span data-stu-id="c881f-130">Scenario 1: ASP.NET Web apps</span></span>

<span data-ttu-id="c881f-131">Na obrázku níže je uveden jednoduchý scénář původní starší ASP.NET webových aplikací.</span><span class="sxs-lookup"><span data-stu-id="c881f-131">The figure below shows the simple scenario of the original legacy ASP.NET web applications.</span></span>

![Jednoduchý scénář architektury původních starších ASP.NET webových aplikací](./media/image5-1.png)

<span data-ttu-id="c881f-133">Z pohledu obchodní domény nabízejí obě aplikace stejné funkce správy katalogu.</span><span class="sxs-lookup"><span data-stu-id="c881f-133">From a business domain perspective, both apps offer the same catalog management features.</span></span> <span data-ttu-id="c881f-134">Členové podnikového týmu eShopu by aplikaci používali k zobrazení a úpravám katalogu produktů.</span><span class="sxs-lookup"><span data-stu-id="c881f-134">Members of the eShop enterprise team would use the app to view and edit the product catalog.</span></span>

<span data-ttu-id="c881f-135">Následující obrázek znázorňuje úvodní snímky obrazovky aplikace.</span><span class="sxs-lookup"><span data-stu-id="c881f-135">The next figure shows the initial app screenshots.</span></span>

![ASP.NET aplikace MVC a ASP.NET webových formulářů (stávající/starší technologie)](./media/image5-2.png)

<span data-ttu-id="c881f-137">Závislosti v ASP.NET verze4.x nebo starší (buď pro MVC nebo pro webové formuláře) znamená, že tyto aplikace nebudou spuštěny na .NET Core, pokud není kód plně přepsán pomocí ASP.NET Core MVC.</span><span class="sxs-lookup"><span data-stu-id="c881f-137">Dependencies in ASP.NET 4.x or earlier versions (either for MVC or for Web Forms) means that these applications won’t run on .NET Core unless the code is fully rewritten by using ASP.NET Core MVC.</span></span>

### <a name="scenario-2-wcf-service-and-winforms-client-app-3-tier-app"></a><span data-ttu-id="c881f-138">Scénář 2: Služba WCF a klientská aplikace WinForms (třívrstvá aplikace)</span><span class="sxs-lookup"><span data-stu-id="c881f-138">Scenario 2: WCF service and WinForms client app (3-Tier app)</span></span>

<span data-ttu-id="c881f-139">Na obrázku níže je uveden jednoduchý scénář původní verze 3 vrstvé aplikace.</span><span class="sxs-lookup"><span data-stu-id="c881f-139">The figure below shows the simple scenario of the original 3-Tier legacy application.</span></span>

![Jednoduchý scénář architektury původní původní třívrstvé aplikace se službou WCF a klientskou aplikací WinForms](./media/image5-1.5.png)

### <a name="benefits"></a><span data-ttu-id="c881f-141">Výhody</span><span class="sxs-lookup"><span data-stu-id="c881f-141">Benefits</span></span>

<span data-ttu-id="c881f-142">Výhody tohoto návodu jsou jednoduché: Stačí se seznámit s kódem a počátečními aplikacemi.</span><span class="sxs-lookup"><span data-stu-id="c881f-142">The benefits of this walkthrough are simple: Just get familiar with the code and initial apps.</span></span>

### <a name="next-steps"></a><span data-ttu-id="c881f-143">Další kroky</span><span class="sxs-lookup"><span data-stu-id="c881f-143">Next steps</span></span>

<span data-ttu-id="c881f-144">Prozkoumejte tento obsah podrobněji na wiki GitHubu:</span><span class="sxs-lookup"><span data-stu-id="c881f-144">Explore this content more in-depth on the GitHub wiki:</span></span>

- [<span data-ttu-id="c881f-145">Prohlídka základních ASP.NET "starších" aplikací MVC a webových formulářů</span><span class="sxs-lookup"><span data-stu-id="c881f-145">Tour on the baseline ASP.NET MVC and Web Forms “legacy” apps</span></span>](https://github.com/dotnet-architecture/eShopModernizing/wiki/01.-Tour-on-the-ASP.NET-MVC-and-WebForms-apps-implementation-code)
- [<span data-ttu-id="c881f-146">Prohlídka základní služby WCF a "starší) aplikace WinForms (3-Tier)</span><span class="sxs-lookup"><span data-stu-id="c881f-146">Tour on the baseline WCF service and WinForms (3-Tier) “legacy” app</span></span>](https://github.com/dotnet-architecture/eShopModernizing/wiki/21.-Tour-on-the-WCF-service-and-WinForms-apps)

## <a name="walkthrough-2-containerize-your-existing-net-applications-with-windows-containers"></a><span data-ttu-id="c881f-147">Návod 2: Kontejnerizaci stávajících aplikací .NET pomocí kontejnerů windows</span><span class="sxs-lookup"><span data-stu-id="c881f-147">Walkthrough 2: Containerize your existing .NET applications with Windows Containers</span></span>

### <a name="overview"></a><span data-ttu-id="c881f-148">Přehled</span><span class="sxs-lookup"><span data-stu-id="c881f-148">Overview</span></span>

<span data-ttu-id="c881f-149">Kontejnery systému Windows slouží ke zlepšení nasazení existujících aplikací .NET, jako jsou aplikace založené na MVC, webových formulářích nebo WCF, do produkčního, vývojového a testovacího prostředí.</span><span class="sxs-lookup"><span data-stu-id="c881f-149">Use Windows Containers to improve deployment of existing .NET applications, like those based on MVC, Web Forms, or WCF, to production, development, and test environments.</span></span>

### <a name="goals"></a><span data-ttu-id="c881f-150">Cíle</span><span class="sxs-lookup"><span data-stu-id="c881f-150">Goals</span></span>

<span data-ttu-id="c881f-151">Cílem tohoto návodu je zobrazit několik možností pro kontejnerizaci existující aplikace rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c881f-151">The goal of this walkthrough is to show you several options for containerizing an existing .NET Framework application.</span></span> <span data-ttu-id="c881f-152">Můžete:</span><span class="sxs-lookup"><span data-stu-id="c881f-152">You can:</span></span>

- <span data-ttu-id="c881f-153">Kontejnerize aplikace pomocí [Visual Studio 2017 Nástroje pro Docker](/aspnet/core/host-and-deploy/docker/visual-studio-tools-for-docker) (Visual Studio 2017 nebo novější verze).</span><span class="sxs-lookup"><span data-stu-id="c881f-153">Containerize your application by using [Visual Studio 2017 Tools for Docker](/aspnet/core/host-and-deploy/docker/visual-studio-tools-for-docker) (Visual Studio 2017 or later versions).</span></span>

- <span data-ttu-id="c881f-154">Kontejnerize aplikace ručním přidáním [Dockerfile](https://docs.docker.com/engine/reference/builder/)a potom pomocí [Docker CLI](https://docs.docker.com/engine/reference/commandline/cli/).</span><span class="sxs-lookup"><span data-stu-id="c881f-154">Containerize your application by manually adding a [Dockerfile](https://docs.docker.com/engine/reference/builder/), and then using the [Docker CLI](https://docs.docker.com/engine/reference/commandline/cli/).</span></span>

- <span data-ttu-id="c881f-155">Kontejnerize aplikace pomocí nástroje [Img2Docker](https://github.com/docker/communitytools-image2docker-win) (open source nástroj z Dockeru).</span><span class="sxs-lookup"><span data-stu-id="c881f-155">Containerize your application by using the [Img2Docker](https://github.com/docker/communitytools-image2docker-win) tool (an open-source tool from Docker).</span></span>

<span data-ttu-id="c881f-156">Tento návod se zaměřuje na visual studio 2017 nástroje pro přístup Docker, ale další dva přístupy jsou poměrně podobné s ohledem na použití Dockerfiles.</span><span class="sxs-lookup"><span data-stu-id="c881f-156">This walkthrough focuses on the Visual Studio 2017 Tools for Docker approach, but the other two approaches are fairly similar in regard to using Dockerfiles.</span></span>

### <a name="scenario-1-containerized-aspnet-web-apps"></a><span data-ttu-id="c881f-157">Scénář 1: Kontejnerizované ASP.NET webových aplikací</span><span class="sxs-lookup"><span data-stu-id="c881f-157">Scenario 1: Containerized ASP.NET web apps</span></span>

<span data-ttu-id="c881f-158">Obrázek níže ukazuje scénář pro kontejnerizované aplikace eShop starších webových aplikací.</span><span class="sxs-lookup"><span data-stu-id="c881f-158">Figure below shows the scenario for containerized eShop legacy web apps applications.</span></span>

![Zjednodušený diagram architektury kontejnerizovaných ASP.NET aplikací ve vývojovém prostředí](./media/image5-3.png)

### <a name="scenario-2-containerized-wcf-service"></a><span data-ttu-id="c881f-160">Scénář 2: Kontejnerizovaná služba WCF</span><span class="sxs-lookup"><span data-stu-id="c881f-160">Scenario 2: Containerized WCF service</span></span>

<span data-ttu-id="c881f-161">Obrázek níže ukazuje scénář pro 3vrstvé aplikace s kontejnerizované WCF služby.</span><span class="sxs-lookup"><span data-stu-id="c881f-161">Figure below shows the scenario for a 3-Tier app with a containerized WCF service.</span></span>

![Diagram zjednodušené architektury kontejnerizované služby WCF ve vývojovém prostředí](./media/image5-3.5.png)

### <a name="benefits"></a><span data-ttu-id="c881f-163">Výhody</span><span class="sxs-lookup"><span data-stu-id="c881f-163">Benefits</span></span>

<span data-ttu-id="c881f-164">Spuštění monolitické aplikace v kontejneru má své výhody.</span><span class="sxs-lookup"><span data-stu-id="c881f-164">There are advantages to running your monolithic application in a container.</span></span> <span data-ttu-id="c881f-165">Nejprve vytvoříte bitovou kopii pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="c881f-165">First, you create an image for the application.</span></span> <span data-ttu-id="c881f-166">Od tohoto okamžiku je každé nasazení spuštěno ve stejném prostředí.</span><span class="sxs-lookup"><span data-stu-id="c881f-166">From that point on, every deployment runs in the same environment.</span></span> <span data-ttu-id="c881f-167">Každý kontejner používá stejnou verzi operačního systému, má nainstalovanou stejnou verzi závislostí, používá stejnou verzi rozhraní .NET framework a je sestaven pomocí stejného procesu.</span><span class="sxs-lookup"><span data-stu-id="c881f-167">Every container uses the same OS version, has the same version of dependencies installed, uses the same .NET framework version, and is built by using the same process.</span></span> <span data-ttu-id="c881f-168">V podstatě můžete řídit závislosti vaší aplikace pomocí image Dockeru.</span><span class="sxs-lookup"><span data-stu-id="c881f-168">Basically, you control the dependencies of your application by using a Docker image.</span></span> <span data-ttu-id="c881f-169">Závislosti cestovat s aplikací při nasazení kontejnerů.</span><span class="sxs-lookup"><span data-stu-id="c881f-169">The dependencies travel with the application when you deploy the containers.</span></span>

<span data-ttu-id="c881f-170">Další výhodou je, že vývojáři můžete spustit aplikaci v konzistentním prostředí, které je k dispozici kontejnery systému Windows.</span><span class="sxs-lookup"><span data-stu-id="c881f-170">An additional benefit is that developers can run the application in the consistent environment that's provided by Windows Containers.</span></span> <span data-ttu-id="c881f-171">Problémy, které se zobrazují pouze u určitých verzí, mohou být zveřejnky okamžitě, namísto vynoření v pracovní nebo produkční prostředí.</span><span class="sxs-lookup"><span data-stu-id="c881f-171">Issues that appear only with certain versions can be spotted immediately, instead of surfacing in a staging or production environment.</span></span> <span data-ttu-id="c881f-172">Rozdíly ve vývojových prostředích používaných členy vývojového týmu záleží méně, když aplikace spustit v kontejnerech.</span><span class="sxs-lookup"><span data-stu-id="c881f-172">Differences in development environments used by members of the development team matter less when applications run in containers.</span></span>

<span data-ttu-id="c881f-173">Kontejnerizované aplikace mají také plošší křivku škálování.</span><span class="sxs-lookup"><span data-stu-id="c881f-173">Containerized applications also have a flatter scale-out curve.</span></span> <span data-ttu-id="c881f-174">Kontejnerizované aplikace umožňují mít více instancí aplikací a služeb (založených na kontejnerech) ve virtuálním počítači nebo fyzickém počítači ve srovnání s běžnými nasazeními aplikací na počítač.</span><span class="sxs-lookup"><span data-stu-id="c881f-174">Containerized apps enable you to have more application and service instances (based on containers) in a VM or physical machine compared to regular application deployments per machine.</span></span> <span data-ttu-id="c881f-175">To znamená vyšší hustotu a méně požadovaných prostředků, zejména při použití orchestrátorů, jako je Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="c881f-175">This translates to higher density and fewer required resources, especially when you use orchestrators like Kubernetes.</span></span>

<span data-ttu-id="c881f-176">Kontejnerizace v ideálních situacích nevyžaduje provedení jakýchkoli změn\#v kódu aplikace (C).</span><span class="sxs-lookup"><span data-stu-id="c881f-176">Containerization, in ideal situations, does not require making any changes to the application code (C\#).</span></span> <span data-ttu-id="c881f-177">Ve většině scénářů potřebujete pouze soubory metadat nasazení Dockeru (Dockerfiles a Docker Compose files).</span><span class="sxs-lookup"><span data-stu-id="c881f-177">In most scenarios, you just need the Docker deployment metadata files (Dockerfiles and Docker Compose files).</span></span>

### <a name="next-steps"></a><span data-ttu-id="c881f-178">Další kroky</span><span class="sxs-lookup"><span data-stu-id="c881f-178">Next steps</span></span>

<span data-ttu-id="c881f-179">Prozkoumejte tento obsah podrobněji na wiki GitHubu:</span><span class="sxs-lookup"><span data-stu-id="c881f-179">Explore this content more in-depth on the GitHub wiki:</span></span>

- [<span data-ttu-id="c881f-180">Jak kontejnerizovat webové aplikace rozhraní .NET Framework pomocí kontejnerů windows a Dockeru</span><span class="sxs-lookup"><span data-stu-id="c881f-180">How to containerize the .NET Framework web apps with Windows Containers and Docker</span></span>](https://github.com/dotnet-architecture/eShopModernizing/wiki/02.-How-to-containerize-the-.NET-Framework-web-apps-with-Windows-Containers-and-Docker)
- [<span data-ttu-id="c881f-181">Přidání podpory Dockeru ke službě WCF</span><span class="sxs-lookup"><span data-stu-id="c881f-181">Adding Docker Support to a WCF service</span></span>](https://github.com/dotnet-architecture/eShopModernizing/wiki/22.-Adding-Docker-Support)

## <a name="walkthrough-3-deploy-your-windows-containers-based-app-to-azure-vms"></a><span data-ttu-id="c881f-182">Návod 3: Nasazení aplikace založené na kontejnerech Windows do virtuálních aplikací Azure</span><span class="sxs-lookup"><span data-stu-id="c881f-182">Walkthrough 3: Deploy your Windows Containers-based app to Azure VMs</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="c881f-183">Dostupnost technického návodu</span><span class="sxs-lookup"><span data-stu-id="c881f-183">Technical walkthrough availability</span></span>

<span data-ttu-id="c881f-184">Úplný technický návod je k dispozici v eShopModernizing GitHub repo wiki:<https://github.com/dotnet-architecture/eShopModernizing/wiki/06.-Deploying-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD)></span><span class="sxs-lookup"><span data-stu-id="c881f-184">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki: <https://github.com/dotnet-architecture/eShopModernizing/wiki/06.-Deploying-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD)></span></span>

### <a name="overview"></a><span data-ttu-id="c881f-185">Přehled</span><span class="sxs-lookup"><span data-stu-id="c881f-185">Overview</span></span>

<span data-ttu-id="c881f-186">Nasazení do hostitele Dockeru na virtuálním počítači (VM) Windows Serveru 2016 v Azure vám umožní rychle nastavit vývojová/testovací/pracovní prostředí.</span><span class="sxs-lookup"><span data-stu-id="c881f-186">Deploying to a Docker host on a Windows Server 2016 Virtual Machine (VM) in Azure lets you quickly set up development/test/staging environments.</span></span> <span data-ttu-id="c881f-187">Poskytuje také společné místo pro testery nebo firemní uživatele k ověření aplikace.</span><span class="sxs-lookup"><span data-stu-id="c881f-187">It also gives you a common place for testers or business users to validate the app.</span></span> <span data-ttu-id="c881f-188">Virtuální virtuální servery mohou být také platné infrastruktury jako služby (IaaS) produkční prostředí.</span><span class="sxs-lookup"><span data-stu-id="c881f-188">VMs also can be valid Infrastructure as a Service (IaaS) production environments.</span></span>

### <a name="goals"></a><span data-ttu-id="c881f-189">Cíle</span><span class="sxs-lookup"><span data-stu-id="c881f-189">Goals</span></span>

<span data-ttu-id="c881f-190">Cílem tohoto návodu je zobrazit více alternativ, které máte při nasazování kontejnerů Windows do virtuálních aplikací Azure, které jsou založené na windows serverových nebo novějších verzích.</span><span class="sxs-lookup"><span data-stu-id="c881f-190">The goal of this walkthrough is to show you the multiple alternatives you have when you deploy Windows Containers to Azure VMs that are based on Windows Server 2016 or later versions.</span></span>

### <a name="scenarios"></a><span data-ttu-id="c881f-191">Scénáře</span><span class="sxs-lookup"><span data-stu-id="c881f-191">Scenarios</span></span>

<span data-ttu-id="c881f-192">V tomto návodu je popsáno několik scénářů.</span><span class="sxs-lookup"><span data-stu-id="c881f-192">Several scenarios are covered in this walkthrough.</span></span>

#### <a name="scenario-a-deploy-to-an-azure-vm-from-a-dev-pc-through-docker-engine-connection"></a><span data-ttu-id="c881f-193">Scénář A: Nasazení na virtuální počítač Azure z počítače pro dev prostřednictvím připojení Docker Engine</span><span class="sxs-lookup"><span data-stu-id="c881f-193">Scenario A: Deploy to an Azure VM from a dev PC through Docker Engine connection</span></span>

![Nasazení na virtuální počítač Azure z počítače pro dev pc přes připojení Docker Engine](./media/image5-4.png)

<span data-ttu-id="c881f-195">**Obrázek 5-4.**</span><span class="sxs-lookup"><span data-stu-id="c881f-195">**Figure 5-4.**</span></span> <span data-ttu-id="c881f-196">Nasazení na virtuální počítač Azure z počítače pro dev pc přes připojení Docker Engine</span><span class="sxs-lookup"><span data-stu-id="c881f-196">Deploy to an Azure VM from a dev PC through a Docker Engine connection</span></span>

#### <a name="scenario-b-deploy-to-an-azure-vm-through-a-docker-registry"></a><span data-ttu-id="c881f-197">Scénář B: Nasazení na virtuální počítač Azure prostřednictvím registru Dockeru</span><span class="sxs-lookup"><span data-stu-id="c881f-197">Scenario B: Deploy to an Azure VM through a Docker Registry</span></span>

![Nasazení na virtuální počítač Azure prostřednictvím registru Dockeru](./media/image5-5.png)

<span data-ttu-id="c881f-199">**Obrázek 5-5.**</span><span class="sxs-lookup"><span data-stu-id="c881f-199">**Figure 5-5.**</span></span> <span data-ttu-id="c881f-200">Nasazení na virtuální počítač Azure prostřednictvím registru Dockeru</span><span class="sxs-lookup"><span data-stu-id="c881f-200">Deploy to an Azure VM through a Docker Registry</span></span>

#### <a name="scenario-c-deploy-to-an-azure-vm-from-cicd-pipelines-in-azure-devops-services"></a><span data-ttu-id="c881f-201">Scénář C: Nasazení na virtuální počítač Azure z kanálů CI/CD ve službách Azure DevOps Services</span><span class="sxs-lookup"><span data-stu-id="c881f-201">Scenario C: Deploy to an Azure VM from CI/CD pipelines in Azure DevOps Services</span></span>

![Nasazení do virtuálního počítače Azure z kanálů CI/CD ve službách Azure DevOps Services](./media/image5-6.png)

<span data-ttu-id="c881f-203">**Obrázek 5-6.**</span><span class="sxs-lookup"><span data-stu-id="c881f-203">**Figure 5-6.**</span></span> <span data-ttu-id="c881f-204">Nasazení do virtuálního počítače Azure z kanálů CI/CD ve službách Azure DevOps Services</span><span class="sxs-lookup"><span data-stu-id="c881f-204">Deploy to an Azure VM from CI/CD pipelines in Azure DevOps Services</span></span>

### <a name="azure-vms-for-windows-containers"></a><span data-ttu-id="c881f-205">Virtuální počítače Azure pro kontejnery s Windows</span><span class="sxs-lookup"><span data-stu-id="c881f-205">Azure VMs for Windows Containers</span></span>

<span data-ttu-id="c881f-206">Virtuální počítače Azure pro kontejnery s Windows jsou virtuální počítače založené na Windows Serveru 2016, Windows 10 nebo novějších verzích, obojí s nastaveným Docker Engine.</span><span class="sxs-lookup"><span data-stu-id="c881f-206">Azure VMs for Windows Containers are VMs based on Windows Server 2016, Windows 10, or later versions, both with Docker Engine set up.</span></span> <span data-ttu-id="c881f-207">Ve většině případů se Windows Server 2016 používá ve virtuálních počítačích Azure.</span><span class="sxs-lookup"><span data-stu-id="c881f-207">In most cases, Windows Server 2016 is used in the Azure VMs.</span></span>

<span data-ttu-id="c881f-208">Azure aktuálně poskytuje virtuální počítač s názvem **Windows Server 2016 s kontejnery**.</span><span class="sxs-lookup"><span data-stu-id="c881f-208">Azure currently provides a VM named **Windows Server 2016 with Containers**.</span></span> <span data-ttu-id="c881f-209">Pomocí tohoto virtuálního virtuálního serveru můžete vyzkoušet novou funkci Kontejner windows serveru, a to buď s Windows Server Core, nebo Windows Nano Server.</span><span class="sxs-lookup"><span data-stu-id="c881f-209">You can use this VM to try the new Windows Server Container feature, with either Windows Server Core or Windows Nano Server.</span></span> <span data-ttu-id="c881f-210">Image operačního systému kontejneru jsou nainstalované a pak virtuální hovirtuální ms je připraven k použití s Dockeru.</span><span class="sxs-lookup"><span data-stu-id="c881f-210">Container OS images are installed, and then the VM is ready to use with Docker.</span></span>

### <a name="benefits"></a><span data-ttu-id="c881f-211">Výhody</span><span class="sxs-lookup"><span data-stu-id="c881f-211">Benefits</span></span>

<span data-ttu-id="c881f-212">I když kontejnery Windows lze nasadit na místní virtuální počítače Windows Server 2016, při nasazení do Azure, získáte jednodušší způsob, jak začít, s ready-to-use Windows Server Kontejner virtuálnípočítače.</span><span class="sxs-lookup"><span data-stu-id="c881f-212">Although Windows Containers can be deployed to on-premises Windows Server 2016 VMs, when you deploy to Azure, you get an easier way to get started, with ready-to-use Windows Server Container VMs.</span></span> <span data-ttu-id="c881f-213">Získáte také společné online umístění, které je přístupné testerům, a automatickou škálovatelnost prostřednictvím škálovacích sad virtuálních strojů Azure.</span><span class="sxs-lookup"><span data-stu-id="c881f-213">You also get a common online location that’s accessible to testers, and automatic scalability through Azure virtual machine scale sets.</span></span>

### <a name="next-steps"></a><span data-ttu-id="c881f-214">Další kroky</span><span class="sxs-lookup"><span data-stu-id="c881f-214">Next steps</span></span>

<span data-ttu-id="c881f-215">Prozkoumejte tento obsah podrobněji na wiki GitHubu:</span><span class="sxs-lookup"><span data-stu-id="c881f-215">Explore this content more in-depth on the GitHub wiki:</span></span>

<https://github.com/dotnet-architecture/eShopModernizing/wiki/06.-Deploying-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD)>

## <a name="walkthrough-4-deploy-your-windows-containers-based-apps-to-azure-container-instances-aci"></a><span data-ttu-id="c881f-216">Návod 4: Nasazení aplikací založených na kontejnerech Windows do instancí kontejnerů Azure (ACI)</span><span class="sxs-lookup"><span data-stu-id="c881f-216">Walkthrough 4: Deploy your Windows Containers-based apps to Azure Container Instances (ACI)</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="c881f-217">Dostupnost technického návodu</span><span class="sxs-lookup"><span data-stu-id="c881f-217">Technical walkthrough availability</span></span>

<span data-ttu-id="c881f-218">Úplný technický návod je k dispozici v eShopModernizing GitHub repo wiki:</span><span class="sxs-lookup"><span data-stu-id="c881f-218">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki:</span></span>

<span data-ttu-id="c881f-219">[Nasazení aplikací do ACI (instance kontejnerů Azure)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances))</span><span class="sxs-lookup"><span data-stu-id="c881f-219">[Deploying the Apps to ACI (Azure Container Instances)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances))</span></span>

### <a name="overview"></a><span data-ttu-id="c881f-220">Přehled</span><span class="sxs-lookup"><span data-stu-id="c881f-220">Overview</span></span>

<span data-ttu-id="c881f-221">[Azure Container Instances (ACI)](https://docs.microsoft.com/azure/container-instances/) je nejrychlejší způsob, jak mít kontejnery dev/test/pracovní prostředí, kde můžete nasadit jednotlivé instance kontejnerů.</span><span class="sxs-lookup"><span data-stu-id="c881f-221">[Azure Container Instances (ACI)](https://docs.microsoft.com/azure/container-instances/) is the quickest way to have a Containers dev/test/staging environment where you can deploy single instances of containers.</span></span>

### <a name="goals"></a><span data-ttu-id="c881f-222">Cíle</span><span class="sxs-lookup"><span data-stu-id="c881f-222">Goals</span></span>

<span data-ttu-id="c881f-223">Tento návod ukazuje hlavní scénáře při nasazování kontejnerů Windows do azure kontejnerů instance (ACI) a jak můžete nasadit eShopModernizing Apps do ACI.</span><span class="sxs-lookup"><span data-stu-id="c881f-223">This walkthrough shows you the main scenarios when deploying Windows Containers to Azure Container Instances (ACI) and how you can deploy eShopModernizing Apps into ACI.</span></span>

### <a name="scenarios"></a><span data-ttu-id="c881f-224">Scénáře</span><span class="sxs-lookup"><span data-stu-id="c881f-224">Scenarios</span></span>

<span data-ttu-id="c881f-225">K dispozici mohou být různé informace o nasazení aplikací eShopModernizing do ACI, jako je nasazení pouze jedné nebo všech aplikací (aplikace MVC, aplikace WebForms nebo služba WCF).</span><span class="sxs-lookup"><span data-stu-id="c881f-225">There can be variations about deploying the eShopModernizing apps into ACI such as deploying just one or all of the apps (MVC app, WebForms app or WCF service).</span></span> <span data-ttu-id="c881f-226">V následujícím scénáři je uvedeno níže uvidíte ASP.NET mvc aplikace plus kontejner SQL Server oba nasazené jako kontejnery do ACI (Azure Container Instances).</span><span class="sxs-lookup"><span data-stu-id="c881f-226">In the following scenario shown below you can see the ASP.NET MVC app plus the SQL Server container both of them deployed as containers into ACI (Azure Container Instances).</span></span>

![Nasazení do ACI z vývojového prostředí](./media/image5-3.5.6.png)

### <a name="benefits"></a><span data-ttu-id="c881f-228">Výhody</span><span class="sxs-lookup"><span data-stu-id="c881f-228">Benefits</span></span>

<span data-ttu-id="c881f-229">Služba Azure Container Instances usnadňuje vytváření a správu kontejnerů Dockeru v Azure, aniž byste museli zřizovat virtuální počítače nebo používat službu vyšší úrovně.</span><span class="sxs-lookup"><span data-stu-id="c881f-229">Azure Container Instances makes it easy to create and manage Docker containers in Azure, without having to provision virtual machines or adopt a higher-level service.</span></span> <span data-ttu-id="c881f-230">S ACI můžete přímo nasadit kontejner Windows v Azure a vystavit ho na internet s plně kvalifikovaným názvem domény (FQDN) během několika sekund (za předpokladu, že máte image kontejneru Windows připravenv registru Dockeru, jako je Docker Hub nebo Azure Container registru).</span><span class="sxs-lookup"><span data-stu-id="c881f-230">With ACI, you can directly deploy a Windows container in Azure and expose it to the internet with a fully qualified domain name (FQDN) in a matter of seconds (Provided that you have the Windows Container image ready in a Docker registry like Docker Hub or Azure Container Registry).</span></span>

### <a name="considerations"></a><span data-ttu-id="c881f-231">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c881f-231">Considerations</span></span>

<span data-ttu-id="c881f-232">Nasazení kontejnerů Windows s úplnou rozhraním .NET Framework / ASP.NET nebo SQL Server do instancí kontejnerů Azure (ACI) není tak rychlé jako nasazení na běžném hostiteli Dockeru (jako je Windows Server 2016 s kontejnery Windows), protože bitová kopie Dockeru se musí stáhnout (vytáhnout z registru Dockeru) pokaždé a velikosti bitové kopie kontejneru SQL (15,1 GB) a image kontejneru ASP.NET (13,9 GB) jsou výrazně velké, nicméně je to mnohem levnější než udržování vlastního hostitele dockeru (trvale on-line Windows Server 2016 s virtuálním počítačem s windows containers v Azure) nemluvě o celém orchestrátoru, jako je Kubernetes v Azure (AKS), což je na druhou stranu skvělá volba pro produkční nasazení.</span><span class="sxs-lookup"><span data-stu-id="c881f-232">Deploying Windows Containers with either full .NET Framework / ASP.NET or SQL Server into Azure Container Instances (ACI) is not quite as fast as deploying to a regular Docker Host (like a Windows Server 2016 with Windows Containers) because the Docker image has to be downloaded (pulled from the Docker registry) every time and the sizes of the SQL container image (15.1 GB) and the ASP.NET container image (13.9 GB) are significantly large, however it is much cheaper than maintaining your own docker host (permanently on-line Windows Server 2016 with Windows Containers VM in Azure) not to mention a whole orchestrator like Kubernetes in Azure (AKS) which is, on the other hand, a great choice for production deployments.</span></span>

<span data-ttu-id="c881f-233">Jako hlavní závěr pomocí Azure Container Instances je velmi přesvědčivá možnost pro scénáře pro vývoj a testování a pro kanály CI/CD.</span><span class="sxs-lookup"><span data-stu-id="c881f-233">As main conclusion, using Azure Container Instances is a very compelling option for Dev/Test scenarios and for CI/CD pipelines.</span></span>

## <a name="next-steps"></a><span data-ttu-id="c881f-234">Další kroky</span><span class="sxs-lookup"><span data-stu-id="c881f-234">Next steps</span></span>

<span data-ttu-id="c881f-235">Prozkoumejte tento obsah podrobněji na wiki GitHubu:</span><span class="sxs-lookup"><span data-stu-id="c881f-235">Explore this content more in-depth on the GitHub wiki:</span></span>

[https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-Deploying-the-Apps-to-ACI-(Azure-Container-Instances))

## <a name="walkthrough-5-deploy-your-windows-containers-based-apps-to-kubernetes-in-azure-container-service"></a><span data-ttu-id="c881f-236">Návod 5: Nasazení aplikací založených na kontejnerech Windows do Kubernetes ve službě Azure Container Service</span><span class="sxs-lookup"><span data-stu-id="c881f-236">Walkthrough 5: Deploy your Windows Containers-based apps to Kubernetes in Azure Container Service</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="c881f-237">Dostupnost technického návodu</span><span class="sxs-lookup"><span data-stu-id="c881f-237">Technical walkthrough availability</span></span>

<span data-ttu-id="c881f-238">Úplný technický návod je k dispozici v eShopModernizing GitHub repo wiki:</span><span class="sxs-lookup"><span data-stu-id="c881f-238">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki:</span></span>

<https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-CI-CD)>

### <a name="overview"></a><span data-ttu-id="c881f-239">Přehled</span><span class="sxs-lookup"><span data-stu-id="c881f-239">Overview</span></span>

<span data-ttu-id="c881f-240">Aplikace založená na kontejnerech Windows bude rychle muset používat platformy a posune se ještě dál od virtuálních aplikací IaaS.</span><span class="sxs-lookup"><span data-stu-id="c881f-240">An application that's based on Windows Containers will quickly need to use platforms, moving even further away from IaaS VMs.</span></span> <span data-ttu-id="c881f-241">To je potřeba ke snadnému dosažení vysoké škálovatelnosti a lepší automatizované škálovatelnosti a k významnému zlepšení v automatizovaných nasazeních a správě verzí.</span><span class="sxs-lookup"><span data-stu-id="c881f-241">This is needed to easily achieve high scalability and better automated scalability, and for a significant improvement in automated deployments and versioning.</span></span> <span data-ttu-id="c881f-242">Těchto cílů můžete dosáhnout pomocí orchestrátoru [Kubernetes](https://kubernetes.io/), který je k dispozici ve [službě Azure Container Services](https://azure.microsoft.com/services/container-service/).</span><span class="sxs-lookup"><span data-stu-id="c881f-242">You can achieve these goals by using the orchestrator [Kubernetes](https://kubernetes.io/), available in [Azure Container Services](https://azure.microsoft.com/services/container-service/).</span></span>

### <a name="goals"></a><span data-ttu-id="c881f-243">Cíle</span><span class="sxs-lookup"><span data-stu-id="c881f-243">Goals</span></span>

<span data-ttu-id="c881f-244">Cílem tohoto návodu je naučit se nasadit aplikaci založenou na kontejneru Windows do Kubernetes (označované také jako *K8s)* ve službě Azure Container Service.</span><span class="sxs-lookup"><span data-stu-id="c881f-244">The goal of this walkthrough is to learn how to deploy a Windows Container–based application to Kubernetes (also called *K8s*) in Azure Container Service.</span></span> <span data-ttu-id="c881f-245">Nasazení do Kubernetes od nuly je dvoustupňový proces:</span><span class="sxs-lookup"><span data-stu-id="c881f-245">Deploying to Kubernetes from scratch is a two-step process:</span></span>

1. <span data-ttu-id="c881f-246">Nasazení clusteru Kubernetes do služby Azure Container Service.</span><span class="sxs-lookup"><span data-stu-id="c881f-246">Deploy a Kubernetes cluster to Azure Container Service.</span></span>

2. <span data-ttu-id="c881f-247">Nasazení aplikace a souvisejících prostředků do clusteru Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="c881f-247">Deploy the application and related resources to the Kubernetes cluster.</span></span>

### <a name="scenarios"></a><span data-ttu-id="c881f-248">Scénáře</span><span class="sxs-lookup"><span data-stu-id="c881f-248">Scenarios</span></span>

#### <a name="scenario-a-deploy-directly-to-a-kubernetes-cluster-from-a-dev-environment"></a><span data-ttu-id="c881f-249">Scénář A: Nasazení přímo do clusteru Kubernetes z dev prostředí</span><span class="sxs-lookup"><span data-stu-id="c881f-249">Scenario A: Deploy directly to a Kubernetes cluster from a dev environment</span></span>

![Nasazení přímo do clusteru Kubernetes z vývojového prostředí](./media/image5-7.png)

<span data-ttu-id="c881f-251">**Obrázek 5-7.**</span><span class="sxs-lookup"><span data-stu-id="c881f-251">**Figure 5-7.**</span></span> <span data-ttu-id="c881f-252">Nasazení přímo do clusteru Kubernetes z vývojového prostředí</span><span class="sxs-lookup"><span data-stu-id="c881f-252">Deploy directly to a Kubernetes cluster from a development environment</span></span>

#### <a name="scenario-b-deploy-to-a-kubernetes-cluster-from-cicd-pipelines-in-azure-devops-services"></a><span data-ttu-id="c881f-253">Scénář B: Nasazení do clusteru Kubernetes z kanálů CI/CD ve službách Azure DevOps Services</span><span class="sxs-lookup"><span data-stu-id="c881f-253">Scenario B: Deploy to a Kubernetes cluster from CI/CD pipelines in Azure DevOps Services</span></span>

![Nasazení do clusteru Kubernetes z kanálů CI/CD ve službách Azure DevOps Services](./media/image5-8.png)

<span data-ttu-id="c881f-255">**Obrázek 5-8.**</span><span class="sxs-lookup"><span data-stu-id="c881f-255">**Figure 5-8.**</span></span> <span data-ttu-id="c881f-256">Nasazení do clusteru Kubernetes z kanálů CI/CD ve službách Azure DevOps Services</span><span class="sxs-lookup"><span data-stu-id="c881f-256">Deploy to a Kubernetes cluster from CI/CD pipelines in Azure DevOps Services</span></span>

### <a name="benefits"></a><span data-ttu-id="c881f-257">Výhody</span><span class="sxs-lookup"><span data-stu-id="c881f-257">Benefits</span></span>

<span data-ttu-id="c881f-258">Nasazení do clusteru v Kubernetes má mnoho výhod.</span><span class="sxs-lookup"><span data-stu-id="c881f-258">There are many benefits to deploying to a cluster in Kubernetes.</span></span> <span data-ttu-id="c881f-259">Největší výhodou je, že získáte prostředí připravené k produkčnímu prostředí, ve kterém můžete škálovat aplikaci na základě počtu instancí kontejneru, které chcete použít (vnitřní škálovatelnost v existujících uzlech), a na základě počtu uzlů nebo virtuálních počítačů v clusteru ( globální škálovatelnost clusteru).</span><span class="sxs-lookup"><span data-stu-id="c881f-259">The biggest benefit is that you get a production-ready environment in which you can scale out the application based on the number of container instances you want to use (inner-scalability in the existing nodes), and based on the number of nodes or VMs in the cluster (global scalability of the cluster).</span></span>

<span data-ttu-id="c881f-260">Azure Container Service optimalizuje oblíbené open source nástroje a technologie speciálně pro Azure.</span><span class="sxs-lookup"><span data-stu-id="c881f-260">Azure Container Service optimizes popular open-source tools and technologies specifically for Azure.</span></span> <span data-ttu-id="c881f-261">Získáte otevřené řešení, které nabízí přenositelnost, a to jak pro vaše kontejnery a pro konfiguraci aplikace.</span><span class="sxs-lookup"><span data-stu-id="c881f-261">You get an open solution that offers portability, both for your containers and for your application configuration.</span></span> <span data-ttu-id="c881f-262">Vyberete velikost, počet hostitelů a orchestrator nástroje kontejnerové služby zpracovává vše ostatní.</span><span class="sxs-lookup"><span data-stu-id="c881f-262">You select the size, the number of hosts, and the orchestrator tools-Container Service handles everything else.</span></span>

<span data-ttu-id="c881f-263">S Kubernetes mohou vývojáři postupovat od přemýšlení o fyzických a virtuálních počítačích až po plánování infrastruktury zaměřené na kontejnery, která mimo jiné usnadňuje následující funkce:</span><span class="sxs-lookup"><span data-stu-id="c881f-263">With Kubernetes, developers can progress from thinking about physical and virtual machines, to planning a container-centric infrastructure that facilitates the following capabilities, among others:</span></span>

- <span data-ttu-id="c881f-264">Aplikace založené na více kontejnerech</span><span class="sxs-lookup"><span data-stu-id="c881f-264">Applications based on multiple containers</span></span>

- <span data-ttu-id="c881f-265">Replikace instancí kontejneru a horizontální automatické škálování</span><span class="sxs-lookup"><span data-stu-id="c881f-265">Replicating container instances and horizontal autoscaling</span></span>

- <span data-ttu-id="c881f-266">Pojmenování a zjišťování (například interní DNS)</span><span class="sxs-lookup"><span data-stu-id="c881f-266">Naming and discovering (for example, internal DNS)</span></span>

- <span data-ttu-id="c881f-267">Vyvažovací zatížení</span><span class="sxs-lookup"><span data-stu-id="c881f-267">Balancing loads</span></span>

- <span data-ttu-id="c881f-268">Postupné aktualizace</span><span class="sxs-lookup"><span data-stu-id="c881f-268">Rolling updates</span></span>

- <span data-ttu-id="c881f-269">Distribuce tajných kódů</span><span class="sxs-lookup"><span data-stu-id="c881f-269">Distributing secrets</span></span>

- <span data-ttu-id="c881f-270">Kontroly stavu aplikace</span><span class="sxs-lookup"><span data-stu-id="c881f-270">Application health checks</span></span>

## <a name="next-steps"></a><span data-ttu-id="c881f-271">Další kroky</span><span class="sxs-lookup"><span data-stu-id="c881f-271">Next steps</span></span>

<span data-ttu-id="c881f-272">Prozkoumejte tento obsah podrobněji na wiki GitHubu:<https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-CI-CD)></span><span class="sxs-lookup"><span data-stu-id="c881f-272">Explore this content more in-depth on the GitHub wiki: <https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-CI-CD)></span></span>

## <a name="walkthrough-6-deploy-your-windows-containers-based-apps-to-azure-app-service-for-containers"></a><span data-ttu-id="c881f-273">Návod 6: Nasazení aplikací založených na kontejnerech Windows do služby Azure App Service for Containers</span><span class="sxs-lookup"><span data-stu-id="c881f-273">Walkthrough 6: Deploy your Windows Containers-based apps to Azure App Service for Containers</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="c881f-274">Dostupnost technického návodu</span><span class="sxs-lookup"><span data-stu-id="c881f-274">Technical walkthrough availability</span></span>

<span data-ttu-id="c881f-275">Úplný technický návod je k dispozici v eShopModernizing GitHub repo wiki:</span><span class="sxs-lookup"><span data-stu-id="c881f-275">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki:</span></span>

<https://github.com/dotnet-architecture/eShopModernizing/wiki/Deploy-Windows-Container-to-Azure-App-Service>

### <a name="overview"></a><span data-ttu-id="c881f-276">Přehled</span><span class="sxs-lookup"><span data-stu-id="c881f-276">Overview</span></span>

<span data-ttu-id="c881f-277">Jednoduchou kontejnerizovanou aplikaci pomocí kontejnerů Windows lze snadno nasadit do služby Azure App Service for Containers.</span><span class="sxs-lookup"><span data-stu-id="c881f-277">A simple containerized application using Windows Containers can easily be deployed to Azure App Service for Containers.</span></span> <span data-ttu-id="c881f-278">Toto je doporučený přístup pro většinu aplikací založených na kontejneru systému Windows.</span><span class="sxs-lookup"><span data-stu-id="c881f-278">This is the recommended approach for most Windows Container-based applications.</span></span>

### <a name="goals"></a><span data-ttu-id="c881f-279">Cíle</span><span class="sxs-lookup"><span data-stu-id="c881f-279">Goals</span></span>

<span data-ttu-id="c881f-280">Cílem tohoto návodu je zjistit, jak nasadit aplikaci založenou na kontejnerech Windows do služby Azure App Service for Containers z registru (Docker Hub nebo Azure Container Registry).</span><span class="sxs-lookup"><span data-stu-id="c881f-280">The goal of this walkthrough is to learn how to deploy a Windows Container–based application to Azure App Service for Containers from a registry (Docker Hub or Azure Container Registry).</span></span>

### <a name="scenario"></a><span data-ttu-id="c881f-281">Scénář</span><span class="sxs-lookup"><span data-stu-id="c881f-281">Scenario</span></span>

![Nasazení aplikace založené na kontejnerech Windows do služby Azure App Service pro kontejnery](./media/image5-11.png)

### <a name="benefits"></a><span data-ttu-id="c881f-283">Výhody</span><span class="sxs-lookup"><span data-stu-id="c881f-283">Benefits</span></span>

<span data-ttu-id="c881f-284">Nasazení do služby Azure App Service for Containers nabízí výhody kontejnerů spárovaných s výhodami služby PaaS služby Azure App Service.</span><span class="sxs-lookup"><span data-stu-id="c881f-284">Deploying to Azure App Service for Containers offers the benefits of containers paired with the PaaS benefits of Azure App Service.</span></span> <span data-ttu-id="c881f-285">App service lze snadno škálovat vertikálně i horizontálně a lze ji nakonfigurovat tak, aby automaticky škálovala tak, aby splňovala měnící se požadavky.</span><span class="sxs-lookup"><span data-stu-id="c881f-285">The app service can easily be scaled both vertically and horizontally, and can be configured to autoscale to meet changing demands.</span></span> <span data-ttu-id="c881f-286">Aktualizace lze provádět s nulovými prostoji a konfigurace průběžného nasazení z registru je také snadno konfigurovat.</span><span class="sxs-lookup"><span data-stu-id="c881f-286">Updates can be performed with zero downtime and configuration of continuous deployment from a registry is easily configured as well.</span></span>

## <a name="next-steps"></a><span data-ttu-id="c881f-287">Další kroky</span><span class="sxs-lookup"><span data-stu-id="c881f-287">Next steps</span></span>

<span data-ttu-id="c881f-288">Prozkoumejte tento obsah podrobněji na wiki GitHubu:<https://github.com/dotnet-architecture/eShopModernizing/wiki/Deploy-Windows-Container-to-Azure-App-Service></span><span class="sxs-lookup"><span data-stu-id="c881f-288">Explore this content more in-depth on the GitHub wiki: <https://github.com/dotnet-architecture/eShopModernizing/wiki/Deploy-Windows-Container-to-Azure-App-Service></span></span>

> [!div class="step-by-step"]
> <span data-ttu-id="c881f-289">[Předchozí](modernize-existing-apps-to-cloud-optimized/migrate-to-hybrid-cloud-scenarios.md)
> [další](conclusions.md)</span><span class="sxs-lookup"><span data-stu-id="c881f-289">[Previous](modernize-existing-apps-to-cloud-optimized/migrate-to-hybrid-cloud-scenarios.md)
[Next](conclusions.md)</span></span> <!-- Next Chapter -->
