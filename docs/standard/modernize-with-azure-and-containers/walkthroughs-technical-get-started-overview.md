---
title: "Postupy a technická získat Začínáme přehled"
description: "Modernizovat existující aplikace .NET s cloudu Azure a Windows kontejnery | postupy a technická získat Začínáme přehled"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/26/2017
ms.openlocfilehash: e78dd4a324ca9fc973f1aa0d8e6a9abe1341876c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="walkthroughs-and-technical-get-started-overview"></a><span data-ttu-id="37574-103">Postupy a technická získat Začínáme přehled</span><span class="sxs-lookup"><span data-stu-id="37574-103">Walkthroughs and technical get started overview</span></span> 

<span data-ttu-id="37574-104">Omezit velikost této e knihy, jsme provedli další technickou dokumentaci a úplné návody k dispozici v úložišti GitHub.</span><span class="sxs-lookup"><span data-stu-id="37574-104">To limit the size of this e-book, we've made additional technical documentation and the full walkthroughs available in a GitHub repo.</span></span> <span data-ttu-id="37574-105">Online řada návodů, která je popsána v tato kapitola obsahuje podrobné nastavení několika prostředí, které jsou založeny na Windows kontejnery a nasazení do Azure.</span><span class="sxs-lookup"><span data-stu-id="37574-105">The online series of walkthroughs that is described in this chapter covers the step-by-step setup of the multiple environments that are based on Windows Containers, and deployment to Azure.</span></span>

<span data-ttu-id="37574-106">Následující části popisují, co každý postup je o její cíle, jeho vysoké úrovně vize- a poskytuje diagram úlohy, které se podílejí.</span><span class="sxs-lookup"><span data-stu-id="37574-106">The following sections explain what each walkthrough is about-its objectives, its high-level vision-and provides a diagram of the tasks that are involved.</span></span> <span data-ttu-id="37574-107">Můžete získat sami názorné postupy v *eShopModernizing* wiki úložišti GitHub aplikace v [https://github.com/dotnet-architecture/eShopModernizing/wiki](https://github.com/dotnet-architecture/eShopModernizing/wiki).</span><span class="sxs-lookup"><span data-stu-id="37574-107">You can get the walkthroughs themselves in the *eShopModernizing* apps GitHub repo wiki at [https://github.com/dotnet-architecture/eShopModernizing/wiki](https://github.com/dotnet-architecture/eShopModernizing/wiki).</span></span>

# <a name="technical-walkthrough-list"></a><span data-ttu-id="37574-108">Seznamu technických návod</span><span class="sxs-lookup"><span data-stu-id="37574-108">Technical walkthrough list</span></span>

<span data-ttu-id="37574-109">Následující kurzy get-started poskytovat konzistentní a komplexní technické pokyny pro ukázkové aplikace, které se dají navýšení a posunutí pomocí kontejnery a potom přesunout tak, že pomocí více možností nasazení v Azure.</span><span class="sxs-lookup"><span data-stu-id="37574-109">The following get-started walkthroughs provide consistent and comprehensive technical guidance for sample apps that you can lift and shift by using containers, and then move by using multiple deployment choices in Azure.</span></span>

<span data-ttu-id="37574-110">Každá z následující kurzy používá nové ukázkových eShopLegacy a eShopModernizing aplikací, které jsou k dispozici na webu GitHub na [https://github.com/dotnet-architecture/eShopModernizing](https://github.com/dotnet-architecture/eShopModernizing).</span><span class="sxs-lookup"><span data-stu-id="37574-110">Each of the following walkthroughs uses the new sample eShopLegacy and eShopModernizing apps, which are available on GitHub at [https://github.com/dotnet-architecture/eShopModernizing](https://github.com/dotnet-architecture/eShopModernizing).</span></span>

-   <span data-ttu-id="37574-111">**Prohlídka eShop starší verze aplikací**</span><span class="sxs-lookup"><span data-stu-id="37574-111">**Tour of eShop legacy apps**</span></span>

-   <span data-ttu-id="37574-112">**Containerize existující aplikace .NET s kontejnery Windows**</span><span class="sxs-lookup"><span data-stu-id="37574-112">**Containerize your existing .NET applications with Windows Containers**</span></span>

-   <span data-ttu-id="37574-113">**Nasazení aplikace systému Windows na základě kontejnery pro virtuální počítače Azure**</span><span class="sxs-lookup"><span data-stu-id="37574-113">**Deploy your Windows Containers-based app to Azure VMs**</span></span>

-   <span data-ttu-id="37574-114">**Nasazení aplikace na základě kontejnery Windows do Kubernetes v Azure Container Service**</span><span class="sxs-lookup"><span data-stu-id="37574-114">**Deploy your Windows Containers-based apps to Kubernetes in Azure Container Service**</span></span>

-   <span data-ttu-id="37574-115">**Nasazení aplikace na základě kontejnery Windows do Azure Service Fabric**</span><span class="sxs-lookup"><span data-stu-id="37574-115">**Deploy your Windows Containers-based apps to Azure Service Fabric**</span></span>

## <a name="walkthrough-1-tour-of-eshop-legacy-apps"></a><span data-ttu-id="37574-116">Návod 1: Prohlídka eShop starší verze aplikací</span><span class="sxs-lookup"><span data-stu-id="37574-116">Walkthrough 1: Tour of eShop legacy apps</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="37574-117">Technické návod dostupnosti</span><span class="sxs-lookup"><span data-stu-id="37574-117">Technical walkthrough availability</span></span>

<span data-ttu-id="37574-118">Úplné technické návod je k dispozici na stránkách wiki úložišti GitHub eShopModernizing:</span><span class="sxs-lookup"><span data-stu-id="37574-118">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki:</span></span>

[<span data-ttu-id="37574-119">https://github.com/DotNet-Architecture/eShopModernizing/Wiki/01.-Tour-on-eShopModernizing-Apps-Implementation-Code</span><span class="sxs-lookup"><span data-stu-id="37574-119">https://github.com/dotnet-architecture/eShopModernizing/wiki/01.-Tour-on-eShopModernizing-apps-implementation-code</span></span>](https://github.com/dotnet-architecture/eShopModernizing/wiki/01.-Tour-on-eShopModernizing-apps-implementation-code)

### <a name="overview"></a><span data-ttu-id="37574-120">Přehled</span><span class="sxs-lookup"><span data-stu-id="37574-120">Overview</span></span>

<span data-ttu-id="37574-121">V tomto návodu můžete prozkoumat počáteční implementace dva ukázkové starší verze aplikace.</span><span class="sxs-lookup"><span data-stu-id="37574-121">In this walkthrough, you can explore the initial implementation of two sample legacy applications.</span></span> <span data-ttu-id="37574-122">Obě ukázkových aplikací mít monolitický architektura a byly vytvořeny pomocí klasického ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="37574-122">Both sample apps have a monolithic architecture, and were created by using classic ASP.NET.</span></span> <span data-ttu-id="37574-123">Jeden aplikace je založena na technologii ASP.NET 4.x MVC; druhý aplikace je založena na webových formulářů ASP.NET 4.x.</span><span class="sxs-lookup"><span data-stu-id="37574-123">One application is based on ASP.NET 4.x MVC; the second application is based on ASP.NET 4.x Web Forms.</span></span> <span data-ttu-id="37574-124">Obě aplikace jsou v [úložiště GitHub eShopModernizing](https://github.com/dotnet-architecture/eShopModernizing).</span><span class="sxs-lookup"><span data-stu-id="37574-124">Both applications are in the [eShopModernizing GitHub repo](https://github.com/dotnet-architecture/eShopModernizing).</span></span>

<span data-ttu-id="37574-125">Můžete containerize obě ukázkové aplikace, podobným způsobem můžete containerize klasický [Windows Communication Foundation](https://docs.microsoft.com/dotnet/framework/wcf/whats-wcf) aplikace (WCF), který se má používat jako desktopová aplikace.</span><span class="sxs-lookup"><span data-stu-id="37574-125">You can containerize both sample apps, similar to the way you can containerize a classic [Windows Communication Foundation](https://docs.microsoft.com/dotnet/framework/wcf/whats-wcf) (WCF) application to be consumed as a desktop application.</span></span> <span data-ttu-id="37574-126">Příklad, naleznete v části [eShopModernizingWCFWinForms](https://github.com/dotnet-architecture/eShopModernizingWCFWinForms).</span><span class="sxs-lookup"><span data-stu-id="37574-126">For an example, see [eShopModernizingWCFWinForms](https://github.com/dotnet-architecture/eShopModernizingWCFWinForms).</span></span>

### <a name="goals"></a><span data-ttu-id="37574-127">Cíle</span><span class="sxs-lookup"><span data-stu-id="37574-127">Goals</span></span>

<span data-ttu-id="37574-128">Hlavním cílem tohoto návodu je jednoduše a seznamte se s těmito aplikacemi a s jejich kódu a konfigurace.</span><span class="sxs-lookup"><span data-stu-id="37574-128">The main goal of this walkthrough is simply to get familiar with these apps, and with their code and configuration.</span></span> <span data-ttu-id="37574-129">Aplikace můžete nakonfigurovat tak, aby se vygenerování a použití imitovaná data bez použití databáze SQL pro účely testování.</span><span class="sxs-lookup"><span data-stu-id="37574-129">You can configure the apps so that they generate and use mock data, without using the SQL database, for testing purposes.</span></span> <span data-ttu-id="37574-130">Toto volitelné konfigurace je založená na vkládání závislostí odpojeného způsobem.</span><span class="sxs-lookup"><span data-stu-id="37574-130">This optional config is based on dependency injection, in a decoupled way.</span></span>

### <a name="scenario"></a><span data-ttu-id="37574-131">Scénář</span><span class="sxs-lookup"><span data-stu-id="37574-131">Scenario</span></span>

<span data-ttu-id="37574-132">Obrázek 5-1 znázorňuje jednoduchý scénář původní starší verze aplikací.</span><span class="sxs-lookup"><span data-stu-id="37574-132">Figure 5-1 shows the simple scenario of the original legacy applications.</span></span>

> ![Scénář jednoduchého architektura původní starší verze aplikací](./media/image5-1.png)
>
> <span data-ttu-id="37574-134">**Obrázek 5-1.**</span><span class="sxs-lookup"><span data-stu-id="37574-134">**Figure 5-1.**</span></span> <span data-ttu-id="37574-135">Scénář jednoduchého architektura původní starší verze aplikací</span><span class="sxs-lookup"><span data-stu-id="37574-135">Simple architecture scenario of the original legacy applications</span></span>

<span data-ttu-id="37574-136">Z hlediska domény obchodní obě aplikace nabízejí katalogu stejné funkce pro správu.</span><span class="sxs-lookup"><span data-stu-id="37574-136">From a business domain perspective, both apps offer the same catalog management features.</span></span> <span data-ttu-id="37574-137">Členové týmu enterprise eShop využije aplikace k zobrazení a úpravy katalogu produktů.</span><span class="sxs-lookup"><span data-stu-id="37574-137">Members of the eShop enterprise team would use the app to view and edit the product catalog.</span></span> <span data-ttu-id="37574-138">Obrázek 5-2 je znázorněný na snímcích obrazovky počáteční aplikace.</span><span class="sxs-lookup"><span data-stu-id="37574-138">Figure 5-2 shows the initial app screenshots.</span></span>

![Aplikace ASP.NET MVC a webových formulářů ASP.NET (technologie existující nebo starší)](./media/image5-2.png)

> <span data-ttu-id="37574-140">**Obrázek 5-2.**</span><span class="sxs-lookup"><span data-stu-id="37574-140">**Figure 5-2.**</span></span> <span data-ttu-id="37574-141">Aplikace ASP.NET MVC a webových formulářů ASP.NET (technologie existující nebo starší)</span><span class="sxs-lookup"><span data-stu-id="37574-141">ASP.NET MVC and ASP.NET Web Forms applications (existing/legacy technologies)</span></span>

<span data-ttu-id="37574-142">Toto jsou webové aplikace, které se používají k procházení a upravit položky katalogu.</span><span class="sxs-lookup"><span data-stu-id="37574-142">These are web applications that are used to browse and modify catalog entries.</span></span> <span data-ttu-id="37574-143">Fakt, že obě aplikace poskytovat stejné funkce obchodní/funkční je jednoduše pro účely porovnání.</span><span class="sxs-lookup"><span data-stu-id="37574-143">The fact that both apps deliver the same business/functional features is simply for comparison purposes.</span></span> <span data-ttu-id="37574-144">Můžete zobrazit podobný proces modernizace pro aplikace, které byly vytvořeny pomocí architektury ASP.NET MVC a webových formulářů ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="37574-144">You can see a similar modernization process for apps that were created by using the ASP.NET MVC and ASP.NET Web Forms frameworks.</span></span>

<span data-ttu-id="37574-145">Závislosti v technologii ASP.NET 4.x nebo starší verze (buď pro MVC nebo webových formulářů) znamená, že tyto aplikace se na .NET Core nespustí, pokud kód je plně přepsaná pomocí ASP.NET MVC jádra.</span><span class="sxs-lookup"><span data-stu-id="37574-145">Dependencies in ASP.NET 4.x or earlier versions (either for MVC or for Web Forms) means that these applications won't run on .NET Core unless the code is fully rewritten by using ASP.NET Core MVC.</span></span> <span data-ttu-id="37574-146">Tento příklad ukazuje bodu, pokud nechcete, aby přepracování nebo přepisovat kód, můžete containerize existující aplikace a nadále používat stejné technologie .NET a má stejný kód.</span><span class="sxs-lookup"><span data-stu-id="37574-146">This demonstrates the point that if you don't want to re-architect or rewrite code, you can containerize existing applications, and still use the same .NET technologies and the same code.</span></span> <span data-ttu-id="37574-147">Uvidíte, jak můžete spouštět aplikace, jako jsou ty do kontejnerů bez uložení změn do starší verze kódu.</span><span class="sxs-lookup"><span data-stu-id="37574-147">You can see how you can run applications like these in containers, without any changes to legacy code.</span></span>

### <a name="benefits"></a><span data-ttu-id="37574-148">Výhody</span><span class="sxs-lookup"><span data-stu-id="37574-148">Benefits</span></span>

<span data-ttu-id="37574-149">Výhody tohoto návodu jsou jednoduché: právě Seznamte se s konfigurací kód a aplikace založené na vkládání závislostí.</span><span class="sxs-lookup"><span data-stu-id="37574-149">The benefits of this walkthrough are simple: Just get familiar with the code and application configuration, based on dependency injection.</span></span> <span data-ttu-id="37574-150">Potom můžete experimentovat s tímto přístupem při containerize a nasazení do několika prostředí v budoucnu.</span><span class="sxs-lookup"><span data-stu-id="37574-150">Then, you can experiment with this approach when you containerize and deploy to multiple environments in the future.</span></span>

### <a name="next-steps"></a><span data-ttu-id="37574-151">Další kroky</span><span class="sxs-lookup"><span data-stu-id="37574-151">Next steps</span></span>

<span data-ttu-id="37574-152">Prozkoumejte podrobnější tento obsah na stránkách wiki Githubu:</span><span class="sxs-lookup"><span data-stu-id="37574-152">Explore this content more in-depth on the GitHub wiki:</span></span>

[<span data-ttu-id="37574-153">https://github.com/DotNet-Architecture/eShopModernizing/Wiki/01.-Tour-on-eShopModernizing-Apps-Implementation-Code</span><span class="sxs-lookup"><span data-stu-id="37574-153">https://github.com/dotnet-architecture/eShopModernizing/wiki/01.-Tour-on-eShopModernizing-apps-implementation-code</span></span>](https://github.com/dotnet-architecture/eShopModernizing/wiki/01.-Tour-on-eShopModernizing-apps-implementation-code)

## <a name="walkthrough-2-containerize-your-existing-net-applications-with-windows-containers"></a><span data-ttu-id="37574-154">Návod 2: Containerize existující aplikace .NET s kontejnery Windows</span><span class="sxs-lookup"><span data-stu-id="37574-154">Walkthrough 2: Containerize your existing .NET applications with Windows Containers</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="37574-155">Technické návod dostupnosti</span><span class="sxs-lookup"><span data-stu-id="37574-155">Technical walkthrough availability</span></span>

<span data-ttu-id="37574-156">Úplné technické návod je k dispozici na stránkách wiki úložišti GitHub eShopModernizing:</span><span class="sxs-lookup"><span data-stu-id="37574-156">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki:</span></span>

[<span data-ttu-id="37574-157">https://github.com/DotNet-Architecture/eShopModernizing/Wiki/02.-How-to-containerized-the-.NET-Framework-Web-Apps-with-Windows-Containers-and-Docker</span><span class="sxs-lookup"><span data-stu-id="37574-157">https://github.com/dotnet-architecture/eShopModernizing/wiki/02.-How-to-containerized-the-.NET-Framework-web-apps-with-Windows-Containers-and-Docker</span></span>](https://https://github.com/dotnet-architecture/eShopModernizing/wiki/02.-How-to-containerized-the-.NET-Framework-web-apps-with-Windows-Containers-and-DockerTBD)

### <a name="overview"></a><span data-ttu-id="37574-158">Přehled</span><span class="sxs-lookup"><span data-stu-id="37574-158">Overview</span></span>

<span data-ttu-id="37574-159">Použití Windows kontejnerů ke zlepšení nasazení existujících aplikací .NET, například algoritmů založených na rozhraní MVC a webových formulářů, WCF, výroby, vývoj a testovací prostředí.</span><span class="sxs-lookup"><span data-stu-id="37574-159">Use Windows Containers to improve deployment of existing .NET applications, like those based on MVC, Web Forms, or WCF, to production, development, and test environments.</span></span>

### <a name="goals"></a><span data-ttu-id="37574-160">Cíle</span><span class="sxs-lookup"><span data-stu-id="37574-160">Goals</span></span>

<span data-ttu-id="37574-161">Cílem tohoto návodu je tak, aby zobrazovalo několik možností pro containerizing stávající aplikace rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="37574-161">The goal of this walkthrough is to show you several options for containerizing an existing .NET Framework application.</span></span> <span data-ttu-id="37574-162">Můžeš:</span><span class="sxs-lookup"><span data-stu-id="37574-162">You can:</span></span>

-   <span data-ttu-id="37574-163">Containerize vaší aplikace pomocí [2017 nástroje sady Visual Studio pro Docker](https://docs.microsoft.com/dotnet/core/docker/visual-studio-tools-for-docker) (Visual Studio 2017 nebo novější verze).</span><span class="sxs-lookup"><span data-stu-id="37574-163">Containerize your application by using [Visual Studio 2017 Tools for Docker](https://docs.microsoft.com/dotnet/core/docker/visual-studio-tools-for-docker) (Visual Studio 2017 or later versions).</span></span>

-   <span data-ttu-id="37574-164">Containerize aplikace tak, že ručně přidáte [soubor Docker](https://docs.docker.com/engine/reference/builder/)a potom pomocí [příkazového řádku Dockeru](https://docs.docker.com/engine/reference/commandline/cli/).</span><span class="sxs-lookup"><span data-stu-id="37574-164">Containerize your application by manually adding a [Dockerfile](https://docs.docker.com/engine/reference/builder/), and then using the [Docker CLI](https://docs.docker.com/engine/reference/commandline/cli/).</span></span>

-   <span data-ttu-id="37574-165">Containerize vaší aplikace pomocí [Img2Docker](https://github.com/docker/communitytools-image2docker-win) (nástroj open-source z Docker).</span><span class="sxs-lookup"><span data-stu-id="37574-165">Containerize your application by using the [Img2Docker](https://github.com/docker/communitytools-image2docker-win) tool (an open-source tool from Docker).</span></span>

<span data-ttu-id="37574-166">Tento názorný postup se zaměřuje na Visual Studio Tools 2017 Docker přístup, ale jsou tyto dva přístupy dost podobné namapoval pomocí Dockerfiles.</span><span class="sxs-lookup"><span data-stu-id="37574-166">This walkthrough focuses on the Visual Studio 2017 Tools for Docker approach, but the other two approaches are fairly similar in regards to using Dockerfiles.</span></span>

### <a name="scenario"></a><span data-ttu-id="37574-167">Scénář</span><span class="sxs-lookup"><span data-stu-id="37574-167">Scenario</span></span>

<span data-ttu-id="37574-168">Obrázek 5-3 ukazuje tento scénář pro kontejnerizované eShop starší verze aplikací.</span><span class="sxs-lookup"><span data-stu-id="37574-168">Figure 5-3 shows the scenario for containerized eShop legacy applications.</span></span>

> ![Diagram architektury zjednodušené kontejnerizované aplikací ve vývojovém prostředí](./media/image5-3.png)
>
> <span data-ttu-id="37574-170">**Obrázek 5-3.**</span><span class="sxs-lookup"><span data-stu-id="37574-170">**Figure 5-3.**</span></span> <span data-ttu-id="37574-171">Diagram architektury zjednodušené kontejnerizované aplikací ve vývojovém prostředí</span><span class="sxs-lookup"><span data-stu-id="37574-171">Simplified architecture diagram of containerized applications in a development environment</span></span>

### <a name="benefits"></a><span data-ttu-id="37574-172">Výhody</span><span class="sxs-lookup"><span data-stu-id="37574-172">Benefits</span></span>

<span data-ttu-id="37574-173">Existují výhody používání aplikace monolitický v kontejneru.</span><span class="sxs-lookup"><span data-stu-id="37574-173">There are advantages to running your monolithic application in a container.</span></span> <span data-ttu-id="37574-174">Nejprve je třeba vytvořit bitovou kopii pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="37574-174">First, you create an image for the application.</span></span> <span data-ttu-id="37574-175">Od tohoto okamžiku v každé nasazení běží ve stejném prostředí.</span><span class="sxs-lookup"><span data-stu-id="37574-175">From that point on, every deployment runs in the same environment.</span></span> <span data-ttu-id="37574-176">Každý kontejner používá stejnou verzi operačního systému, má stejnou verzi závislostí nainstalována, používá stejnou verzi rozhraní .NET framework a je vytvořen pomocí stejného procesu.</span><span class="sxs-lookup"><span data-stu-id="37574-176">Every container uses the same OS version, has the same version of dependencies installed, uses the same .NET framework version, and is built by using the same process.</span></span> <span data-ttu-id="37574-177">V podstatě řídit závislostí vaší aplikace pomocí Docker bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="37574-177">Basically, you control the dependencies of your application by using a Docker image.</span></span> <span data-ttu-id="37574-178">Závislosti cestují k aplikaci při nasazení kontejnerů.</span><span class="sxs-lookup"><span data-stu-id="37574-178">The dependencies travel with the application when you deploy the containers.</span></span>

<span data-ttu-id="37574-179">Další výhodou je, že vývojáři aplikaci můžete spustit v konzistentní prostředí, které poskytuje Windows kontejnery.</span><span class="sxs-lookup"><span data-stu-id="37574-179">An additional benefit is that developers can run the application in the consistent environment that's provided by Windows Containers.</span></span> <span data-ttu-id="37574-180">Problémy, které se zobrazují pouze u některých verzí můžete okamžitě, nanese místo zpřístupnění v pracovním nebo produkčním prostředí.</span><span class="sxs-lookup"><span data-stu-id="37574-180">Issues that appear only with certain versions can be spotted immediately, instead of surfacing in a staging or production environment.</span></span> <span data-ttu-id="37574-181">Rozdíly ve vývojovém prostředí používá členové týmu pro vývoj podstatné menší při spuštění aplikace v kontejnerech.</span><span class="sxs-lookup"><span data-stu-id="37574-181">Differences in development environments used by members of the development team matter less when applications run in containers.</span></span>

<span data-ttu-id="37574-182">Kontejnerizované aplikací mít také plošší křivky Škálováním na více systémů.</span><span class="sxs-lookup"><span data-stu-id="37574-182">Containerized applications also have a flatter scale-out curve.</span></span> <span data-ttu-id="37574-183">Kontejnerizované aplikací umožňují mít další aplikace a instance služby (podle kontejnery) v virtuálního počítače nebo fyzického počítače ve srovnání s nasazení regulární aplikací na počítač.</span><span class="sxs-lookup"><span data-stu-id="37574-183">Containerized apps enable you to have more application and service instances (based on containers) in a VM or physical machine compared to regular application deployments per machine.</span></span> <span data-ttu-id="37574-184">Výsledkem je vyšší hustotu a méně požadované prostředky, zejména v případě, že používáte orchestrators jako Kubernetes nebo Service Fabric.</span><span class="sxs-lookup"><span data-stu-id="37574-184">This translates to higher density and fewer required resources, especially when you use orchestrators like Kubernetes or Service Fabric.</span></span>

<span data-ttu-id="37574-185">Rozdělení do kontejnerů v situacích, ideální, není nutné provádět jakékoliv změny kódu aplikace (C\#).</span><span class="sxs-lookup"><span data-stu-id="37574-185">Containerization, in ideal situations, does not require making any changes to the application code (C\#).</span></span> <span data-ttu-id="37574-186">Ve většině scénářů bude třeba jen soubory metadat nasazení Docker (soubory Dockerfiles a Docker Compose).</span><span class="sxs-lookup"><span data-stu-id="37574-186">In most scenarios, you just need the Docker deployment metadata files (Dockerfiles and Docker Compose files).</span></span>

### <a name="next-steps"></a><span data-ttu-id="37574-187">Další kroky</span><span class="sxs-lookup"><span data-stu-id="37574-187">Next steps</span></span>

<span data-ttu-id="37574-188">Prozkoumat podrobnější tento obsah na stránkách wiki Githubu: [https://https://github.com/dotnet-architecture/eShopModernizing/wiki/02.-How-to-containerized-the-.NET-Framework-web-apps-with-Windows-Containers-and-Docker](https://https://github.com/dotnet-architecture/eShopModernizing/wiki/02.-How-to-containerized-the-.NET-Framework-web-apps-with-Windows-Containers-and-Docker)</span><span class="sxs-lookup"><span data-stu-id="37574-188">Explore this content more in-depth on the GitHub wiki: [https://https://github.com/dotnet-architecture/eShopModernizing/wiki/02.-How-to-containerized-the-.NET-Framework-web-apps-with-Windows-Containers-and-Docker](https://https://github.com/dotnet-architecture/eShopModernizing/wiki/02.-How-to-containerized-the-.NET-Framework-web-apps-with-Windows-Containers-and-Docker)</span></span>

## <a name="walkthrough-3-deploy-your-windows-containers-based-app-to-azure-vms"></a><span data-ttu-id="37574-189">Návod 3: Nasazení aplikace systému Windows na základě kontejnery pro virtuální počítače Azure</span><span class="sxs-lookup"><span data-stu-id="37574-189">Walkthrough 3: Deploy your Windows Containers-based app to Azure VMs</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="37574-190">Technické návod dostupnosti</span><span class="sxs-lookup"><span data-stu-id="37574-190">Technical walkthrough availability</span></span>

<span data-ttu-id="37574-191">Úplné technické návod je k dispozici na stránkách wiki úložišti GitHub eShopModernizing:</span><span class="sxs-lookup"><span data-stu-id="37574-191">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki:</span></span>

<span data-ttu-id="37574-192">[https://github.com/DotNet-Architecture/eShopModernizing/Wiki/03.-How-to-deploy-Your-Windows-Containers-Based-App-INTO-Azure-VMs-(Including-ci-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/03.-How-to-deploy-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD))</span><span class="sxs-lookup"><span data-stu-id="37574-192">[https://github.com/dotnet-architecture/eShopModernizing/wiki/03.-How-to-deploy-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/03.-How-to-deploy-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD))</span></span>

### <a name="overview"></a><span data-ttu-id="37574-193">Přehled</span><span class="sxs-lookup"><span data-stu-id="37574-193">Overview</span></span>

<span data-ttu-id="37574-194">Nasazení na Docker hostitele na virtuální počítač Windows serveru 2016 v Azure umožňuje rychle nastavit dev/testovací/přípravného prostředí.</span><span class="sxs-lookup"><span data-stu-id="37574-194">Deploying to a Docker host on a Windows Server 2016 VM in Azure lets you quickly set up dev/test/staging environments.</span></span> <span data-ttu-id="37574-195">Také poskytuje společné místo pro testery nebo podnikoví uživatelé k ověření aplikace.</span><span class="sxs-lookup"><span data-stu-id="37574-195">It also gives you a common place for testers or business users to validate the app.</span></span> <span data-ttu-id="37574-196">Virtuální počítače mohou být také platný IaaS provozní prostředí.</span><span class="sxs-lookup"><span data-stu-id="37574-196">VMs also can be valid IaaS production environments.</span></span>

### <a name="goals"></a><span data-ttu-id="37574-197">Cíle</span><span class="sxs-lookup"><span data-stu-id="37574-197">Goals</span></span>

<span data-ttu-id="37574-198">Cílem tohoto návodu je tak, aby zobrazovalo více alternativy, které máte, když nasadíte kontejnery Windows na virtuálních počítačích Azure, které jsou založené na systému Windows Server 2016 nebo novější verze.</span><span class="sxs-lookup"><span data-stu-id="37574-198">The goal of this walkthrough is to show you the multiple alternatives you have when you deploy Windows Containers to Azure VMs that are based on Windows Server 2016 or later versions.</span></span>

### <a name="scenarios"></a><span data-ttu-id="37574-199">Scénáře</span><span class="sxs-lookup"><span data-stu-id="37574-199">Scenarios</span></span>

<span data-ttu-id="37574-200">Několik scénáře jsou popsané v tomto návodu.</span><span class="sxs-lookup"><span data-stu-id="37574-200">Several scenarios are covered in this walkthrough.</span></span>

#### <a name="scenario-a-deploy-to-an-azure-vm-from-a-dev-pc-through-docker-engine-connection"></a><span data-ttu-id="37574-201">Scénář A: nasazení na virtuální počítač Azure ze dev počítače prostřednictvím připojení modulu Docker</span><span class="sxs-lookup"><span data-stu-id="37574-201">Scenario A: Deploy to an Azure VM from a dev PC through Docker Engine connection</span></span>

![Nasazení na virtuální počítač Azure z vývojářů počítače prostřednictvím připojení k modulu Docker](./media/image5-4.png)

> <span data-ttu-id="37574-203">**Obrázek 5 – 4.**</span><span class="sxs-lookup"><span data-stu-id="37574-203">**Figure 5-4.**</span></span> <span data-ttu-id="37574-204">Nasazení na virtuální počítač Azure z vývojářů počítače prostřednictvím připojení k modulu Docker</span><span class="sxs-lookup"><span data-stu-id="37574-204">Deploy to an Azure VM from a dev PC through a Docker Engine connection</span></span>

#### <a name="scenario-b-deploy-to-an-azure-vm-through-a-docker-registry"></a><span data-ttu-id="37574-205">Scénář B: nasazení na virtuální počítač Azure prostřednictvím registru Docker</span><span class="sxs-lookup"><span data-stu-id="37574-205">Scenario B: Deploy to an Azure VM through a Docker Registry</span></span>

![Nasazení na virtuální počítač Azure prostřednictvím registru Docker](./media/image5-5.png)

> <span data-ttu-id="37574-207">**Obrázek 5-5.**</span><span class="sxs-lookup"><span data-stu-id="37574-207">**Figure 5-5.**</span></span> <span data-ttu-id="37574-208">Nasazení na virtuální počítač Azure prostřednictvím registru Docker</span><span class="sxs-lookup"><span data-stu-id="37574-208">Deploy to an Azure VM through a Docker Registry</span></span>

#### <a name="scenario-c-deploy-to-an-azure-vm-from-cicd-pipelines-in-visual-studio-team-services"></a><span data-ttu-id="37574-209">Scénář C: nasazení na virtuální počítač Azure z položek konfigurace nebo CD kanály v sadě Visual Studio Team Services</span><span class="sxs-lookup"><span data-stu-id="37574-209">Scenario C: Deploy to an Azure VM from CI/CD pipelines in Visual Studio Team Services</span></span>

![Nasazení z položek konfigurace nebo CD kanály v sadě Visual Studio Team Services na virtuální počítač Azure](./media/image5-6.png)

> <span data-ttu-id="37574-211">**Obrázek 5 a 6.**</span><span class="sxs-lookup"><span data-stu-id="37574-211">**Figure 5-6.**</span></span> <span data-ttu-id="37574-212">Nasazení z položek konfigurace nebo CD kanály v sadě Visual Studio Team Services na virtuální počítač Azure</span><span class="sxs-lookup"><span data-stu-id="37574-212">Deploy to an Azure VM from CI/CD pipelines in Visual Studio Team Services</span></span>

### <a name="azure-vms-for-windows-containers"></a><span data-ttu-id="37574-213">Virtuální počítače Azure pro Windows kontejnery</span><span class="sxs-lookup"><span data-stu-id="37574-213">Azure VMs for Windows Containers</span></span>

<span data-ttu-id="37574-214">Azure kontejnery virtuálních počítačů pro Windows jsou jednoduše virtuálních počítačů, které jsou založené na systému Windows Server 2016, Windows 10 nebo novější verze, jak k modulu Docker nastavit.</span><span class="sxs-lookup"><span data-stu-id="37574-214">Azure VMs for Windows Containers are simply VMs that are based on Windows Server 2016, Windows 10, or later versions, both with Docker Engine set up.</span></span> <span data-ttu-id="37574-215">Ve většině případů bude používat systém Windows Server 2016 ve virtuálních počítačích Azure.</span><span class="sxs-lookup"><span data-stu-id="37574-215">In most cases, you will use Windows Server 2016 in the Azure VMs.</span></span>

<span data-ttu-id="37574-216">Virtuální počítač s názvem aktuálně poskytuje Azure **systému Windows Server 2016 s kontejnery**.</span><span class="sxs-lookup"><span data-stu-id="37574-216">Azure currently provides a VM named **Windows Server 2016 with Containers**.</span></span> <span data-ttu-id="37574-217">Můžete vyzkoušet nové funkce kontejneru systému Windows Server s Windows Server Core nebo Windows Nano Server můžete použít tento virtuální počítač.</span><span class="sxs-lookup"><span data-stu-id="37574-217">You can use this VM to try the new Windows Server Container feature, with either Windows Server Core or Windows Nano Server.</span></span> <span data-ttu-id="37574-218">Kontejner imagí operačního systému jsou nainstalované a je připravený k použití s Docker virtuálního počítače.</span><span class="sxs-lookup"><span data-stu-id="37574-218">Container OS images are installed, and then the VM is ready to use with Docker.</span></span>

### <a name="benefits"></a><span data-ttu-id="37574-219">Výhody</span><span class="sxs-lookup"><span data-stu-id="37574-219">Benefits</span></span>

<span data-ttu-id="37574-220">I když Windows kontejnery mohou být nasazeny do místní 2016 virtuálních počítačů Windows serveru, když nasadíte do Azure, můžete získat snadný způsob, jak začít pracovat s virtuálními počítači kontejneru připravené k použití Windows serveru.</span><span class="sxs-lookup"><span data-stu-id="37574-220">Although Windows Containers can be deployed to on-premises Windows Server 2016 VMs, when you deploy to Azure, you get an easier way to get started, with ready-to-use Windows Server Container VMs.</span></span> <span data-ttu-id="37574-221">Můžete také získat běžné online umístění, které je přístupné pro testery a automatické škálovatelnost prostřednictvím sady škálování virtuálního počítače Azure.</span><span class="sxs-lookup"><span data-stu-id="37574-221">You also get a common online location that’s accessible to testers, and automatic scalability through Azure VM scale sets.</span></span>

### <a name="next-steps"></a><span data-ttu-id="37574-222">Další kroky</span><span class="sxs-lookup"><span data-stu-id="37574-222">Next steps</span></span>

<span data-ttu-id="37574-223">Prozkoumejte podrobnější tento obsah na stránkách wiki Githubu:</span><span class="sxs-lookup"><span data-stu-id="37574-223">Explore this content more in-depth on the GitHub wiki:</span></span>

<span data-ttu-id="37574-224">[https://github.com/DotNet-Architecture/eShopModernizing/Wiki/03.-How-to-deploy-Your-Windows-Containers-Based-App-INTO-Azure-VMs-(Including-ci-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/03.-How-to-deploy-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD))</span><span class="sxs-lookup"><span data-stu-id="37574-224">[https://github.com/dotnet-architecture/eShopModernizing/wiki/03.-How-to-deploy-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/03.-How-to-deploy-your-Windows-Containers-based-app-into-Azure-VMs-(Including-CI-CD))</span></span>

## <a name="walkthrough-4-deploy-your-windows-containers-based-apps-to-kubernetes-in-azure-container-service"></a><span data-ttu-id="37574-225">Návod 4: Nasazení aplikace na základě kontejnery Windows do Kubernetes v Azure Container Service</span><span class="sxs-lookup"><span data-stu-id="37574-225">Walkthrough 4: Deploy your Windows Containers-based apps to Kubernetes in Azure Container Service</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="37574-226">Technické návod dostupnosti</span><span class="sxs-lookup"><span data-stu-id="37574-226">Technical walkthrough availability</span></span>

<span data-ttu-id="37574-227">Úplné technické návod je k dispozici na stránkách wiki úložišti GitHub eShopModernizing:</span><span class="sxs-lookup"><span data-stu-id="37574-227">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki:</span></span>

<span data-ttu-id="37574-228">[https://github.com/DotNet-Architecture/eShopModernizing/Wiki/04.-How-to-deploy-Your-Windows-Containers-Based-Apps-INTO-Kubernetes-in-Azure-Container-Service-(Including-C-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-C-CD))</span><span class="sxs-lookup"><span data-stu-id="37574-228">[https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-C-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-C-CD))</span></span>

### <a name="overview"></a><span data-ttu-id="37574-229">Přehled</span><span class="sxs-lookup"><span data-stu-id="37574-229">Overview</span></span>

<span data-ttu-id="37574-230">Aplikace, která je založena na systému Windows kontejnery rychle muset platformy, přesunutí i další počítače z virtuálních počítačů IaaS.</span><span class="sxs-lookup"><span data-stu-id="37574-230">An application that's based on Windows Containers will quickly need to use platforms, moving even further away from IaaS VMs.</span></span> <span data-ttu-id="37574-231">To je potřeba snadno dosáhnout vysoké škálovatelnost a lépe automatizované škálovatelnost a pro přináší značné vylepšení v automatizované nasazení a správa verzí.</span><span class="sxs-lookup"><span data-stu-id="37574-231">This is needed to easily achieve high scalability and better automated scalability, and for a significant improvement in automated deployments and versioning.</span></span> <span data-ttu-id="37574-232">Tyto cíle můžete dosáhnout pomocí orchestrator [Kubernetes](https://kubernetes.io/), k dispozici v [služby kontejneru Azure](https://azure.microsoft.com/services/container-service/).</span><span class="sxs-lookup"><span data-stu-id="37574-232">You can achieve these goals by using the orchestrator [Kubernetes](https://kubernetes.io/), available in [Azure Container Services](https://azure.microsoft.com/services/container-service/).</span></span>

### <a name="goals"></a><span data-ttu-id="37574-233">Cíle</span><span class="sxs-lookup"><span data-stu-id="37574-233">Goals</span></span>

<span data-ttu-id="37574-234">Cílem tohoto návodu je další informace o nasazení aplikace na základě kontejneru systému Windows k Kubernetes (také nazývané *K8s*) v Azure Container Service.</span><span class="sxs-lookup"><span data-stu-id="37574-234">The goal of this walkthrough is to learn how to deploy a Windows Container–based application to Kubernetes (also called *K8s*) in Azure Container Service.</span></span> <span data-ttu-id="37574-235">Nasazení do Kubernetes od začátku je dvoustupňový proces:</span><span class="sxs-lookup"><span data-stu-id="37574-235">Deploying to Kubernetes from scratch is a two-step process:</span></span>

1.  <span data-ttu-id="37574-236">Nasaďte Kubernetes clusteru Azure Container Service.</span><span class="sxs-lookup"><span data-stu-id="37574-236">Deploy a Kubernetes cluster to Azure Container Service.</span></span>

2.  <span data-ttu-id="37574-237">Nasazení aplikace a související prostředky do clusteru Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="37574-237">Deploy the application and related resources to the Kubernetes cluster.</span></span>

### <a name="scenarios"></a><span data-ttu-id="37574-238">Scénáře</span><span class="sxs-lookup"><span data-stu-id="37574-238">Scenarios</span></span>

#### <a name="scenario-a-deploy-directly-to-a-kubernetes-cluster-from-a-dev-environment"></a><span data-ttu-id="37574-239">Scénář A: nasadit přímo do clusteru s podporou Kubernetes z prostředí vývojářů</span><span class="sxs-lookup"><span data-stu-id="37574-239">Scenario A: Deploy directly to a Kubernetes cluster from a dev environment</span></span>

![Nasazení přímo na clusteru s podporou Kubernetes z prostředí pro vývoj](./media/image5-7.png)

> <span data-ttu-id="37574-241">**Obrázek 5 – 7.**</span><span class="sxs-lookup"><span data-stu-id="37574-241">**Figure 5-7.**</span></span> <span data-ttu-id="37574-242">Nasazení přímo na clusteru s podporou Kubernetes z prostředí pro vývoj</span><span class="sxs-lookup"><span data-stu-id="37574-242">Deploy directly to a Kubernetes cluster from a development environment</span></span>

#### <a name="scenario-b-deploy-to-a-kubernetes-cluster-from-cicd-pipelines-in-team-services"></a><span data-ttu-id="37574-243">Scénář B: nasadit do clusteru s podporou Kubernetes z položek konfigurace nebo CD kanálů v Team Services</span><span class="sxs-lookup"><span data-stu-id="37574-243">Scenario B: Deploy to a Kubernetes cluster from CI/CD pipelines in Team Services</span></span>

![Nasazení do clusteru s podporou Kubernetes z položek konfigurace nebo CD kanály v Team Services](./media/image5-8.png)

> <span data-ttu-id="37574-245">**Obrázek 5-8.**</span><span class="sxs-lookup"><span data-stu-id="37574-245">**Figure 5-8.**</span></span> <span data-ttu-id="37574-246">Nasazení do clusteru s podporou Kubernetes z položek konfigurace nebo CD kanály v Team Services</span><span class="sxs-lookup"><span data-stu-id="37574-246">Deploy to a Kubernetes cluster from CI/CD pipelines in Team Services</span></span>

### <a name="benefits"></a><span data-ttu-id="37574-247">Výhody</span><span class="sxs-lookup"><span data-stu-id="37574-247">Benefits</span></span>

<span data-ttu-id="37574-248">Existuje mnoho výhod nasazení do clusteru s podporou v Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="37574-248">There are many benefits to deploying to a cluster in Kubernetes.</span></span> <span data-ttu-id="37574-249">Největší výhodou je, že dostanete prostředí produkční prostředí, ve kterém můžete můžete škálování aplikace založené na počet instancí kontejneru, které chcete použít (vnitřní škálovatelnost v existujícím uzlům) a na základě počtu uzlů nebo virtuální počítače v clusteru ( Globální škálovatelnost clusteru).</span><span class="sxs-lookup"><span data-stu-id="37574-249">The biggest benefit is that you get a production-ready environment in which you can scale-out the application based on the number of container instances you want to use (inner-scalability in the existing nodes), and based on the number of nodes or VMs in the cluster (global scalability of the cluster).</span></span>

<span data-ttu-id="37574-250">Azure Container Service optimalizuje oblíbených open-source nástrojů a technologií speciálně pro Azure.</span><span class="sxs-lookup"><span data-stu-id="37574-250">Azure Container Service optimizes popular open-source tools and technologies specifically for Azure.</span></span> <span data-ttu-id="37574-251">Získat otevřete řešení, která nabízí přenositelnost pro vaše kontejnery i pro konfiguraci aplikace.</span><span class="sxs-lookup"><span data-stu-id="37574-251">You get an open solution that offers portability, both for your containers and for your application configuration.</span></span> <span data-ttu-id="37574-252">Vyberte velikost, počtu hostitelů, a nástrojů orchestrator-kontejneru služby zpracovává nic jiného.</span><span class="sxs-lookup"><span data-stu-id="37574-252">You select the size, the number of hosts, and the orchestrator tools-Container Service handles everything else.</span></span>

<span data-ttu-id="37574-253">S Kubernetes mohou vývojáři průběhu od přemýšlení o fyzické a virtuální počítače k plánování zaměřené na kontejner infrastruktury, která usnadňuje následující funkce, mimo jiné:</span><span class="sxs-lookup"><span data-stu-id="37574-253">With Kubernetes, developers can progress from thinking about physical and virtual machines, to planning a container-centric infrastructure that facilitates the following capabilities, among others:</span></span>

-   <span data-ttu-id="37574-254">Aplikace založené na několika kontejnerů</span><span class="sxs-lookup"><span data-stu-id="37574-254">Applications based on multiple containers</span></span>

-   <span data-ttu-id="37574-255">Replikace instancí kontejnerů a vodorovné automatické škálování</span><span class="sxs-lookup"><span data-stu-id="37574-255">Replicating container instances and horizontal autoscaling</span></span>

-   <span data-ttu-id="37574-256">Pojmenování a zjišťování (například interní DNS)</span><span class="sxs-lookup"><span data-stu-id="37574-256">Naming and discovering (for example, internal DNS)</span></span>

-   <span data-ttu-id="37574-257">Vyrovnávání zatížení</span><span class="sxs-lookup"><span data-stu-id="37574-257">Balancing loads</span></span>

-   <span data-ttu-id="37574-258">Vrácení aktualizace</span><span class="sxs-lookup"><span data-stu-id="37574-258">Rolling updates</span></span>

-   <span data-ttu-id="37574-259">Distribuce tajné klíče</span><span class="sxs-lookup"><span data-stu-id="37574-259">Distributing secrets</span></span>

-   <span data-ttu-id="37574-260">Kontroly stavu aplikace</span><span class="sxs-lookup"><span data-stu-id="37574-260">Application health checks</span></span>

## <a name="next-steps"></a><span data-ttu-id="37574-261">Další kroky</span><span class="sxs-lookup"><span data-stu-id="37574-261">Next steps</span></span>

<span data-ttu-id="37574-262">Prozkoumat podrobnější tento obsah na stránkách wiki Githubu: [https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-() Including-C-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-C-CD))</span><span class="sxs-lookup"><span data-stu-id="37574-262">Explore this content more in-depth on the GitHub wiki: [https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-C-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-C-CD))</span></span>

## <a name="walkthrough-5-deploy-your-windows-containers-based-apps-to-azure-service-fabric"></a><span data-ttu-id="37574-263">Návod 5: Nasazení aplikace na základě kontejnery Windows do Azure Service Fabric</span><span class="sxs-lookup"><span data-stu-id="37574-263">Walkthrough 5: Deploy your Windows Containers-based apps to Azure Service Fabric</span></span>

### <a name="technical-walkthrough-availability"></a><span data-ttu-id="37574-264">Technické návod dostupnosti</span><span class="sxs-lookup"><span data-stu-id="37574-264">Technical walkthrough availability</span></span>

<span data-ttu-id="37574-265">Úplné technické návod je k dispozici na stránkách wiki úložišti GitHub eShopModernizing:</span><span class="sxs-lookup"><span data-stu-id="37574-265">The full technical walkthrough is available in the eShopModernizing GitHub repo wiki:</span></span>

<span data-ttu-id="37574-266">[https://github.com/DotNet-Architecture/eShopModernizing/Wiki/05.-How-to-deploy-Your-Windows-Containers-Based-Apps-INTO-Azure-Service-Fabric-(Including-ci-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-How-to-deploy-your-Windows-Containers-based-apps-into-Azure-Service-Fabric-(Including-CI-CD))</span><span class="sxs-lookup"><span data-stu-id="37574-266">[https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-How-to-deploy-your-Windows-Containers-based-apps-into-Azure-Service-Fabric-(Including-CI-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-How-to-deploy-your-Windows-Containers-based-apps-into-Azure-Service-Fabric-(Including-CI-CD))</span></span>

### <a name="overview"></a><span data-ttu-id="37574-267">Přehled</span><span class="sxs-lookup"><span data-stu-id="37574-267">Overview</span></span>

<span data-ttu-id="37574-268">Aplikace, která je založena na systému Windows kontejnery rychle muset platformy, přesunutí i další počítače z virtuálních počítačů IaaS.</span><span class="sxs-lookup"><span data-stu-id="37574-268">An application that's based on Windows Containers will quickly need to use platforms, moving even further away from IaaS VMs.</span></span> <span data-ttu-id="37574-269">To je potřeba snadno dosáhnout vysoké škálovatelnost a lépe automatizované škálovatelnost a pro přináší značné vylepšení v automatizované nasazení a správa verzí.</span><span class="sxs-lookup"><span data-stu-id="37574-269">This is needed to easily achieve high scalability and better automated scalability, and for a significant improvement in automated deployments and versioning.</span></span> <span data-ttu-id="37574-270">Pomocí orchestrator Azure Service Fabric, která je k dispozici v cloudu Azure, ale také k dispozici pro použití v místě, nebo i v různých veřejného cloudu, můžete dosáhnout těchto cílů.</span><span class="sxs-lookup"><span data-stu-id="37574-270">You can achieve these goals by using the orchestrator Azure Service Fabric, which is available in the Azure cloud, but also available to use on-premises, or even in a different public cloud.</span></span>

### <a name="goals"></a><span data-ttu-id="37574-271">Cíle</span><span class="sxs-lookup"><span data-stu-id="37574-271">Goals</span></span>

<span data-ttu-id="37574-272">Cílem tohoto návodu je další informace o nasazení aplikace na základě kontejneru systému Windows do clusteru Service Fabric v Azure.</span><span class="sxs-lookup"><span data-stu-id="37574-272">The goal of this walkthrough is to learn how to deploy a Windows Container–based application to a Service Fabric cluster in Azure.</span></span> <span data-ttu-id="37574-273">Nasazení do Service Fabric od začátku je dvoustupňový proces:</span><span class="sxs-lookup"><span data-stu-id="37574-273">Deploying to Service Fabric from scratch is a two-step process:</span></span>

1.  <span data-ttu-id="37574-274">Cluster Service Fabric nasaďte do Azure (nebo do různých prostředí).</span><span class="sxs-lookup"><span data-stu-id="37574-274">Deploy a Service Fabric cluster to Azure (or to a different environment).</span></span>

2.  <span data-ttu-id="37574-275">Nasaďte aplikace a související prostředky do clusteru Service Fabric.</span><span class="sxs-lookup"><span data-stu-id="37574-275">Deploy the application and related resources to the Service Fabric cluster.</span></span>

### <a name="scenarios"></a><span data-ttu-id="37574-276">Scénáře</span><span class="sxs-lookup"><span data-stu-id="37574-276">Scenarios</span></span>

#### <a name="scenario-a-deploy-directly-to-a-service-fabric-cluster-from-a-dev-environment"></a><span data-ttu-id="37574-277">Scénář A: nasadit přímo na clusteru Service Fabric z prostředí vývojářů</span><span class="sxs-lookup"><span data-stu-id="37574-277">Scenario A: Deploy directly to a Service Fabric cluster from a dev environment</span></span>

![Nasazení z prostředí pro vývoj přímo na clusteru Service Fabric](./media/image5-9.png)

> <span data-ttu-id="37574-279">**Obrázek 5-9.**</span><span class="sxs-lookup"><span data-stu-id="37574-279">**Figure 5-9.**</span></span> <span data-ttu-id="37574-280">Nasazení z prostředí pro vývoj přímo na clusteru Service Fabric</span><span class="sxs-lookup"><span data-stu-id="37574-280">Deploy directly to a Service Fabric cluster from a development environment</span></span>

### <a name="scenario-b-deploy-to-a-service-fabric-cluster-from-cicd-pipelines-in-team-services"></a><span data-ttu-id="37574-281">Scénář B: nasadit do clusteru Service Fabric z položek konfigurace nebo CD kanálů v Team Services</span><span class="sxs-lookup"><span data-stu-id="37574-281">Scenario B: Deploy to a Service Fabric cluster from CI/CD pipelines in Team Services</span></span>

![Nasazení na cluster Service Fabric z položek konfigurace nebo CD kanály v sadě Visual Studio Team Services](./media/image5-10.png)

> <span data-ttu-id="37574-283">**Obrázek 5-10.**</span><span class="sxs-lookup"><span data-stu-id="37574-283">**Figure 5-10.**</span></span> <span data-ttu-id="37574-284">Nasazení na cluster Service Fabric z položek konfigurace nebo CD kanály v sadě Visual Studio Team Services</span><span class="sxs-lookup"><span data-stu-id="37574-284">Deploy to a Service Fabric cluster from CI/CD pipelines in Visual Studio Team Services</span></span>

## <a name="benefits"></a><span data-ttu-id="37574-285">Výhody</span><span class="sxs-lookup"><span data-stu-id="37574-285">Benefits</span></span>

<span data-ttu-id="37574-286">Výhody nasazení na cluster Service Fabric se podobá výhody použití Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="37574-286">The benefits of deploying to a cluster in Service Fabric are similar to the benefits of using Kubernetes.</span></span> <span data-ttu-id="37574-287">Jeden rozdíl, ale je, že Service Fabric je velmi vyspělá produkčním prostředí pro aplikace systému Windows ve srovnání s Kubernetes, která byla ve verzi preview pro kontejnery Windows dokud již v rané fázi spadají 2017.</span><span class="sxs-lookup"><span data-stu-id="37574-287">One difference, though, is that Service Fabric is a very mature production environment for Windows applications compared to Kubernetes, which was in preview for Windows Containers until early fall of 2017.</span></span> <span data-ttu-id="37574-288">(Kubernetes je víc vyspělých prostředí pro Linux).</span><span class="sxs-lookup"><span data-stu-id="37574-288">(Kubernetes is a more mature environment for Linux).</span></span> 

<span data-ttu-id="37574-289">Hlavní výhodou používání Azure Service Fabric je, že dostanete prostředí produkční prostředí, ve kterém můžete můžete škálování aplikace založené na počet instancí kontejneru, které chcete použít (vnitřní škálovatelnost v existujícím uzlům) a na základě počtu uzly nebo virtuální počítače v clusteru (globální škálovatelnost clusteru).</span><span class="sxs-lookup"><span data-stu-id="37574-289">The main benefit of using Azure Service Fabric is that you get a production-ready environment in which you can scale-out the application based on the number of container instances you want to use (inner-scalability in the existing nodes), and based on the number of nodes or VMs in the cluster (global scalability of the cluster).</span></span>

<span data-ttu-id="37574-290">Azure Service Fabric nabízí přenositelnost pro vaše kontejnery i pro konfiguraci aplikace.</span><span class="sxs-lookup"><span data-stu-id="37574-290">Azure Service Fabric offers portability both for your containers and for your application configuration.</span></span> <span data-ttu-id="37574-291">Můžete mít Service Fabric cluster v Azure a nainstalujte ji na místě ve svém vlastním datovém centru.</span><span class="sxs-lookup"><span data-stu-id="37574-291">You can have a Service Fabric cluster in Azure, or install it on-premises in your own datacenter.</span></span> <span data-ttu-id="37574-292">Můžete nainstalovat i clusteru Service Fabric v jiném cloudu, jako je třeba [Amazon AWS](https://blogs.msdn.microsoft.com/azureservicefabric/2017/05/18/tutorial-how-to-create-a-service-fabric-standalone-cluster-with-aws-ec2-instances/).</span><span class="sxs-lookup"><span data-stu-id="37574-292">You can even install a Service Fabric cluster in a different cloud, like [Amazon AWS](https://blogs.msdn.microsoft.com/azureservicefabric/2017/05/18/tutorial-how-to-create-a-service-fabric-standalone-cluster-with-aws-ec2-instances/).</span></span>

<span data-ttu-id="37574-293">Pomocí Service Fabric mohou vývojáři průběhu od přemýšlení o fyzické a virtuální počítače k plánování zaměřené na kontejner infrastruktury, která usnadňuje následující funkce, mimo jiné:</span><span class="sxs-lookup"><span data-stu-id="37574-293">With Service Fabric, developers can progress from thinking about physical and virtual machines to planning a container-centric infrastructure that facilitates the following capabilities, among others:</span></span>

-   <span data-ttu-id="37574-294">Aplikace založené na několika kontejnerů.</span><span class="sxs-lookup"><span data-stu-id="37574-294">Applications based on multiple containers.</span></span>

-   <span data-ttu-id="37574-295">Replikace instancí kontejnerů a vodorovné automatické škálování.</span><span class="sxs-lookup"><span data-stu-id="37574-295">Replicating container instances and horizontal autoscaling.</span></span>

-   <span data-ttu-id="37574-296">Pojmenování a zjišťování (například interní DNS).</span><span class="sxs-lookup"><span data-stu-id="37574-296">Naming and discovering (for example, internal DNS).</span></span>

-   <span data-ttu-id="37574-297">Vyrovnávání zatížení.</span><span class="sxs-lookup"><span data-stu-id="37574-297">Balancing loads.</span></span>

-   <span data-ttu-id="37574-298">Vrácení aktualizace.</span><span class="sxs-lookup"><span data-stu-id="37574-298">Rolling updates.</span></span>

-   <span data-ttu-id="37574-299">Distribuce tajných klíčů.</span><span class="sxs-lookup"><span data-stu-id="37574-299">Distributing secrets.</span></span>

-   <span data-ttu-id="37574-300">Kontroluje stav aplikací.</span><span class="sxs-lookup"><span data-stu-id="37574-300">Application health checks.</span></span>

<span data-ttu-id="37574-301">Následující funkce jsou výhradní v Service Fabric (ve srovnání s další orchestrators):</span><span class="sxs-lookup"><span data-stu-id="37574-301">The following capabilities are exclusive in Service Fabric (compared to other orchestrators):</span></span>

-   <span data-ttu-id="37574-302">Funkce stavové služby prostřednictvím modelu aplikací spolehlivé služby.</span><span class="sxs-lookup"><span data-stu-id="37574-302">Stateful services capability, through the Reliable Services application model.</span></span>

-   <span data-ttu-id="37574-303">Vzor aktéři prostřednictvím aplikačního modelu Reliable Actors.</span><span class="sxs-lookup"><span data-stu-id="37574-303">Actors pattern, through the Reliable Actors application model.</span></span>

-   <span data-ttu-id="37574-304">Nasaďte úplné kost procesy, kromě kontejnery systému Windows nebo Linux.</span><span class="sxs-lookup"><span data-stu-id="37574-304">Deploy bare-bone processes, in addition to Windows or Linux containers.</span></span>

-   <span data-ttu-id="37574-305">Rozšířené kumulativní aktualizace a kontroly stavu.</span><span class="sxs-lookup"><span data-stu-id="37574-305">Advanced rolling updates and health checks.</span></span>

### <a name="next-steps"></a><span data-ttu-id="37574-306">Další kroky</span><span class="sxs-lookup"><span data-stu-id="37574-306">Next steps</span></span>

<span data-ttu-id="37574-307">Prozkoumejte podrobnější tento obsah na stránkách wiki Githubu:</span><span class="sxs-lookup"><span data-stu-id="37574-307">Explore this content more in-depth on the GitHub wiki:</span></span>

<span data-ttu-id="37574-308">[https://github.com/DotNet-Architecture/eShopModernizing/Wiki/05.-How-to-deploy-Your-Windows-Containers-Based-Apps-INTO-Azure-Service-Fabric-(Including-ci-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-How-to-deploy-your-Windows-Containers-based-apps-into-Azure-Service-Fabric-(Including-CI-CD))</span><span class="sxs-lookup"><span data-stu-id="37574-308">[https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-How-to-deploy-your-Windows-Containers-based-apps-into-Azure-Service-Fabric-(Including-CI-CD)](https://github.com/dotnet-architecture/eShopModernizing/wiki/05.-How-to-deploy-your-Windows-Containers-based-apps-into-Azure-Service-Fabric-(Including-CI-CD))</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="37574-309">[Předchozí](lift-and-shift-existing-apps-devops/migrate-to-hybrid-cloud-scenarios.md)
[další](conclusions.md)</span><span class="sxs-lookup"><span data-stu-id="37574-309">[Previous](lift-and-shift-existing-apps-devops/migrate-to-hybrid-cloud-scenarios.md)
[Next](conclusions.md)</span></span>
