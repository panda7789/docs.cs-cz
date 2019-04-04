---
title: Mikroslužby .NET. Architektura pro Kontejnerizované aplikace .NET
description: Architektura Mikroslužeb .NET pro Kontejnerizované aplikace .NET | Mikroslužby jsou modulární a umožňují nezávislé nasazení služby. Kontejnery dockeru (pro systémy Linux a Windows) zjednodušit nasazování a testování seskupí služby a jeho závislosti do jedné jednotky, které je potom spouštět v izolovaném prostředí.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 01/07/2019
ms.openlocfilehash: 9a544172e180bbd3ae5eb2281e73e36407ffc003
ms.sourcegitcommit: 7156c0b9e4ce4ce5ecf48ce3d925403b638b680c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/26/2019
ms.locfileid: "58463641"
---
# <a name="net-microservices-architecture-for-containerized-net-applications"></a><span data-ttu-id="eedac-105">Mikroslužby .NET: Architektura pro Kontejnerizované aplikace .NET</span><span class="sxs-lookup"><span data-stu-id="eedac-105">.NET Microservices: Architecture for Containerized .NET Applications</span></span>

![Titulní knihy](./media/cover-small.png)

<span data-ttu-id="eedac-107">**EDICE v2.2.00** – aktualizováno, aby ASP.NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="eedac-107">**EDITION v2.2.00** - Updated to ASP.NET Core 2.2</span></span>

<span data-ttu-id="eedac-108">Tato příručka slouží jako úvod k vývoji aplikací založených na mikroslužbách a správu kontejnerů.</span><span class="sxs-lookup"><span data-stu-id="eedac-108">This guide is an introduction to developing microservices-based applications and managing them using containers.</span></span> <span data-ttu-id="eedac-109">Tento článek popisuje kontrol architektonického návrhu a implementace přístupy pomocí .NET Core a kontejnery Dockeru.</span><span class="sxs-lookup"><span data-stu-id="eedac-109">It discusses architectural design and implementation approaches using .NET Core and Docker containers.</span></span> 

<span data-ttu-id="eedac-110">Aby bylo snazší, abyste mohli začít, průvodce se zaměřuje na odkaz kontejnerizovaných a aplikací založených na mikroslužbách, kterou můžete prozkoumat.</span><span class="sxs-lookup"><span data-stu-id="eedac-110">To make it easier to get started, the guide focuses on a reference containerized and microservice-based application that you can explore.</span></span> <span data-ttu-id="eedac-111">Referenční aplikace je k dispozici na [aplikaci eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) úložiště GitHub.</span><span class="sxs-lookup"><span data-stu-id="eedac-111">The reference application is available at the [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) GitHub repo.</span></span>

## <a name="action-links"></a><span data-ttu-id="eedac-112">Odkazy na akce</span><span class="sxs-lookup"><span data-stu-id="eedac-112">Action links</span></span>

* <span data-ttu-id="eedac-113">Stáhněte si tuto e-kniha ve formát vašeho výběru: | [PDF](https://aka.ms/microservicesebook) | [MOBI](https://www.microsoft.com/net/download/thank-you/microservices-architecture-ebook-mobi) | [EPUB](https://www.microsoft.com/net/download/thank-you/microservices-architecture-ebook-epub) |</span><span class="sxs-lookup"><span data-stu-id="eedac-113">Download this eBook in your format of choice: | [PDF](https://aka.ms/microservicesebook) | [MOBI](https://www.microsoft.com/net/download/thank-you/microservices-architecture-ebook-mobi) | [EPUB](https://www.microsoft.com/net/download/thank-you/microservices-architecture-ebook-epub) |</span></span>

* <span data-ttu-id="eedac-114">Klon/Forku referenční aplikace [aplikaci eShopOnContainers na Githubu](https://github.com/dotnet-architecture/eShopOnContainers)</span><span class="sxs-lookup"><span data-stu-id="eedac-114">Clone/Fork the reference application [eShopOnContainers on GitHub](https://github.com/dotnet-architecture/eShopOnContainers)</span></span>
 
* <span data-ttu-id="eedac-115">Podívejte [úvodní video na Channel 9](https://aka.ms/microservices-video)</span><span class="sxs-lookup"><span data-stu-id="eedac-115">Watch the [introductory video on Channel 9](https://aka.ms/microservices-video)</span></span>

* <span data-ttu-id="eedac-116">Seznamte se [architektury Mikroslužeb](https://aka.ms/MicroservicesArchitecture) hned</span><span class="sxs-lookup"><span data-stu-id="eedac-116">Get to know the [Microservices Architecture](https://aka.ms/MicroservicesArchitecture) right away</span></span>

## <a name="introduction"></a><span data-ttu-id="eedac-117">Úvod</span><span class="sxs-lookup"><span data-stu-id="eedac-117">Introduction</span></span>

<span data-ttu-id="eedac-118">Podniky jsou stále porozumění úspory nákladů, řešení problémů s nasazením a zlepšení operace DevOps a produkčním prostředí pomocí kontejnerů.</span><span class="sxs-lookup"><span data-stu-id="eedac-118">Enterprises are increasingly realizing cost savings, solving deployment problems, and improving DevOps and production operations by using containers.</span></span> <span data-ttu-id="eedac-119">Microsoft má byla uvolnění inovace kontejner pro Windows a Linux tak, že vytvoříte produkty, jako je Azure Container Service a Azure Service Fabric a díky partnerství s vedoucím postavením, jako je Docker, Mesosphere a Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="eedac-119">Microsoft has been releasing container innovations for Windows and Linux by creating products like Azure Container Service and Azure Service Fabric, and by partnering with industry leaders like Docker, Mesosphere, and Kubernetes.</span></span> <span data-ttu-id="eedac-120">Tyto produkty poskytovat kontejneru řešení, která pomáhají společnostem sestavovat a nasazovat aplikace v cloudu rychlost a škálování, kterou si sami vyberou platformy nebo nástroje.</span><span class="sxs-lookup"><span data-stu-id="eedac-120">These products deliver container solutions that help companies build and deploy applications at cloud speed and scale, whatever their choice of platform or tools.</span></span>

<span data-ttu-id="eedac-121">Docker je stále de facto standardem v odvětví kontejneru, podporovány jsou nejdůležitější dodavatelé v ekosystémů Windows a Linux.</span><span class="sxs-lookup"><span data-stu-id="eedac-121">Docker is becoming the de facto standard in the container industry, supported by the most significant vendors in the Windows and Linux ecosystems.</span></span> <span data-ttu-id="eedac-122">(Microsoft je hlavní cloudových vendorů, podporu Dockeru.) V budoucích verzích Dockeru bude pravděpodobně všudypřítomná v libovolné datacentrum do cloudu nebo lokálně.</span><span class="sxs-lookup"><span data-stu-id="eedac-122">(Microsoft is one of the main cloud vendors supporting Docker.) In the future, Docker will probably be ubiquitous in any datacenter in the cloud or on-premises.</span></span>

<span data-ttu-id="eedac-123">Kromě toho [mikroslužeb](https://martinfowler.com/articles/microservices.html) architektura je nově vznikající jako důležité přístup pro distribuované klíčové aplikace.</span><span class="sxs-lookup"><span data-stu-id="eedac-123">In addition, the [microservices](https://martinfowler.com/articles/microservices.html) architecture is emerging as an important approach for distributed mission-critical applications.</span></span> <span data-ttu-id="eedac-124">V architektuře s využitím mikroslužeb je aplikace sestavená u kolekce služeb, které mohou být vytvořeny, otestovat, nasazené a systémovou správou verzí nezávisle na sobě.</span><span class="sxs-lookup"><span data-stu-id="eedac-124">In a microservice-based architecture, the application is built on a collection of services that can be developed, tested, deployed, and versioned independently.</span></span>

## <a name="about-this-guide"></a><span data-ttu-id="eedac-125">Informace o této příručce</span><span class="sxs-lookup"><span data-stu-id="eedac-125">About this guide</span></span>

<span data-ttu-id="eedac-126">Tato příručka slouží jako úvod k vývoji aplikací založených na mikroslužbách a správu kontejnerů.</span><span class="sxs-lookup"><span data-stu-id="eedac-126">This guide is an introduction to developing microservices-based applications and managing them using containers.</span></span> <span data-ttu-id="eedac-127">Tento článek popisuje kontrol architektonického návrhu a implementace přístupy pomocí .NET Core a kontejnery Dockeru.</span><span class="sxs-lookup"><span data-stu-id="eedac-127">It discusses architectural design and implementation approaches using .NET Core and Docker containers.</span></span> <span data-ttu-id="eedac-128">Aby bylo snazší začít pracovat s kontejnery a mikroslužby, průvodce se zaměřuje na odkaz kontejnerizovaných a aplikací založených na mikroslužbách, kterou můžete prozkoumat.</span><span class="sxs-lookup"><span data-stu-id="eedac-128">To make it easier to get started with containers and microservices, the guide focuses on a reference containerized and microservice-based application that you can explore.</span></span> <span data-ttu-id="eedac-129">Ukázková aplikace je k dispozici na [aplikaci eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) úložiště GitHub.</span><span class="sxs-lookup"><span data-stu-id="eedac-129">The sample application is available at the [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) GitHub repo.</span></span>

<span data-ttu-id="eedac-130">Tato příručka obsahuje základní vývoj a doprovodné materiály k architektuře primárně na úrovni prostředí vývoj se zaměřením na technologie: .NET Core a docker.</span><span class="sxs-lookup"><span data-stu-id="eedac-130">This guide provides foundational development and architectural guidance primarily at a development environment level with a focus on two technologies: Docker and .NET Core.</span></span> <span data-ttu-id="eedac-131">Naším úmyslem je, že si přečtete tuto příručku při posuzování návrhu aplikace, nemusíte se soustředit na infrastrukturu (v cloudu nebo místních) vašeho produkčního prostředí.</span><span class="sxs-lookup"><span data-stu-id="eedac-131">Our intention is that you read this guide when thinking about your application design without focusing on the infrastructure (cloud or on-premises) of your production environment.</span></span> <span data-ttu-id="eedac-132">Bude rozhodnutí o infrastruktuře později, při vytváření aplikace připravené pro produkční prostředí.</span><span class="sxs-lookup"><span data-stu-id="eedac-132">You will make decisions about your infrastructure later, when you create your production-ready applications.</span></span> <span data-ttu-id="eedac-133">Proto tato příručka je určena být nezávislá a více vývojové prostředí – zaměřené na infrastrukturu.</span><span class="sxs-lookup"><span data-stu-id="eedac-133">Therefore, this guide is intended to be infrastructure agnostic and more development-environment-centric.</span></span>

<span data-ttu-id="eedac-134">Po zkoumali této příručce, bude dalším krokem je další informace o mikroslužbách připravené pro produkční prostředí v Microsoft Azure.</span><span class="sxs-lookup"><span data-stu-id="eedac-134">After you have studied this guide, your next step would be to learn about production-ready microservices on Microsoft Azure.</span></span>

## <a name="version"></a><span data-ttu-id="eedac-135">Version</span><span class="sxs-lookup"><span data-stu-id="eedac-135">Version</span></span>

<span data-ttu-id="eedac-136">Tento průvodce byl změněn na pokrytí **.NET Core 2.2** verze a mnoho dalších aktualizace související s stejné "wave" technologií (tj.</span><span class="sxs-lookup"><span data-stu-id="eedac-136">This guide has been revised to cover **.NET Core 2.2** version plus many additional updates related to the same “wave” of technologies (that is.</span></span> <span data-ttu-id="eedac-137">Azure a další 3. stran technologie) okamžiku v čase s nástroji .NET Core 2.2.</span><span class="sxs-lookup"><span data-stu-id="eedac-137">Azure and additional 3rd party technologies) coinciding in time with .NET Core 2.2.</span></span> <span data-ttu-id="eedac-138">To je důvod, proč verze knihy se také aktualizovala na verzi **2.2**.</span><span class="sxs-lookup"><span data-stu-id="eedac-138">That’s why the book version has also been updated to version **2.2**.</span></span> 

## <a name="what-this-guide-does-not-cover"></a><span data-ttu-id="eedac-139">Co tato příručka nepopisuje</span><span class="sxs-lookup"><span data-stu-id="eedac-139">What this guide does not cover</span></span>

<span data-ttu-id="eedac-140">Tato příručka se nezaměřuje na životního cyklu aplikací, vývoj a provoz kanálů CI/CD nebo tým pracovat.</span><span class="sxs-lookup"><span data-stu-id="eedac-140">This guide does not focus on the application lifecycle, DevOps, CI/CD pipelines, or team work.</span></span> <span data-ttu-id="eedac-141">Doplňkové průvodce [Kontejnerizovaných životní cyklus aplikace Dockeru s platformou a nástroji Microsoft](https://aka.ms/dockerlifecycleebook) se zaměřuje na tohoto subjektu.</span><span class="sxs-lookup"><span data-stu-id="eedac-141">The complementary guide [Containerized Docker Application Lifecycle with Microsoft Platform and Tools](https://aka.ms/dockerlifecycleebook) focuses on that subject.</span></span> <span data-ttu-id="eedac-142">Aktuální Průvodce také neposkytuje podrobné informace o implementaci na infrastrukturu Azure, jako je například informace o konkrétní orchestrátorů.</span><span class="sxs-lookup"><span data-stu-id="eedac-142">The current guide also does not provide implementation details on Azure infrastructure, such as information on specific orchestrators.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="eedac-143">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="eedac-143">Additional resources</span></span>

-   <span data-ttu-id="eedac-144">**Životní cyklus aplikace Dockeru s platformou a nástroji Microsoft kontejnerizovaných** (ke stažení e kniha)</span><span class="sxs-lookup"><span data-stu-id="eedac-144">**Containerized Docker Application Lifecycle with Microsoft Platform and Tools** (downloadable e-book)</span></span>  
    [https://aka.ms/dockerlifecycleebook](https://aka.ms/dockerlifecycleebook)

## <a name="who-should-use-this-guide"></a><span data-ttu-id="eedac-145">Kdo by měl používat tohoto průvodce</span><span class="sxs-lookup"><span data-stu-id="eedac-145">Who should use this guide</span></span>

<span data-ttu-id="eedac-146">Jsme napsali Tato příručka pro vývojáře a architekty řešení, kteří jsou nové pro vývoj aplikací založených na Dockeru a architektura založená na mikroslužbách.</span><span class="sxs-lookup"><span data-stu-id="eedac-146">We wrote this guide for developers and solution architects who are new to Docker-based application development and to microservices-based architecture.</span></span> <span data-ttu-id="eedac-147">Tento průvodce je pro, pokud chcete získat informace tom, jak navrhovat, navrhování a implementace aplikací testování konceptu s vývojovým technologiím Microsoftu (se zvláštním zaměřením na .NET Core) a s kontejnery Dockeru.</span><span class="sxs-lookup"><span data-stu-id="eedac-147">This guide is for you if you want to learn how to architect, design, and implement proof-of-concept applications with Microsoft development technologies (with special focus on .NET Core) and with Docker containers.</span></span>

<span data-ttu-id="eedac-148">Také zjistíte Tato příručka užitečné, pokud jste technický pracovník s rozhodovací pravomocí, jako je například podnikový architekt, kdo chce, aby se architektura a přehledu technologie před rozhodnout, na jaké přístup k výběru pro nové a moderní distribuované aplikace.</span><span class="sxs-lookup"><span data-stu-id="eedac-148">You will also find this guide useful if you are a technical decision maker, such as an enterprise architect, who wants an architecture and technology overview before you decide on what approach to select for new and modern distributed applications.</span></span>

### <a name="how-to-use-this-guide"></a><span data-ttu-id="eedac-149">Jak používat tohoto průvodce</span><span class="sxs-lookup"><span data-stu-id="eedac-149">How to use this guide</span></span>

<span data-ttu-id="eedac-150">První části této příručky zavádí kontejnery Dockeru, popisuje, jak si vybrat mezi .NET Core a .NET Framework jako rozhraní pro vývoj a najdete zde přehled mikroslužeb.</span><span class="sxs-lookup"><span data-stu-id="eedac-150">The first part of this guide introduces Docker containers, discusses how to choose between .NET Core and the .NET Framework as a development framework, and provides an overview of microservices.</span></span> <span data-ttu-id="eedac-151">Tento obsah je pro architekty a technické pracovníky s rozhodovací pravomocí, kteří mají přehled, ale není potřeba zaměřit se na podrobnosti implementace kódu.</span><span class="sxs-lookup"><span data-stu-id="eedac-151">This content is for architects and technical decision makers who want an overview but don't need to focus on code implementation details.</span></span>

<span data-ttu-id="eedac-152">Začíná druhé části v průvodci [aplikací založených na proces vývoje pro Docker](./docker-application-development-process/index.md) oddílu.</span><span class="sxs-lookup"><span data-stu-id="eedac-152">The second part of the guide starts with the [Development process for Docker based applications](./docker-application-development-process/index.md) section.</span></span> <span data-ttu-id="eedac-153">Zaměřuje se na vývoj a mikroslužeb vzory pro provádění aplikací pomocí .NET Core a Docker.</span><span class="sxs-lookup"><span data-stu-id="eedac-153">It focuses on development and microservice patterns for implementing applications using .NET Core and Docker.</span></span> <span data-ttu-id="eedac-154">Tato část bude mít největší zájem vývojářům a architektům, kteří chtějí soustředit se na kód a vzorců a podrobnosti implementace.</span><span class="sxs-lookup"><span data-stu-id="eedac-154">This section will be of most interest to developers and architects who want to focus on code and on patterns and implementation details.</span></span>

## <a name="related-microservice-and-container-based-reference-application-eshoponcontainers"></a><span data-ttu-id="eedac-155">Související mikroslužby a aplikace založené na kontejnerech odkaz: aplikaci eShopOnContainers</span><span class="sxs-lookup"><span data-stu-id="eedac-155">Related microservice and container-based reference application: eShopOnContainers</span></span>

<span data-ttu-id="eedac-156">Aplikaci eShopOnContainers aplikace je odkaz na open source aplikace pro .NET Core a mikroslužeb, která slouží k nasazení kontejnerů Dockeru.</span><span class="sxs-lookup"><span data-stu-id="eedac-156">The eShopOnContainers application is an open-source reference app for .NET Core and microservices that is designed to be deployed using Docker containers.</span></span> <span data-ttu-id="eedac-157">Aplikace se skládá z více subsystémů, včetně několik e-store uživatelského rozhraní front-endů (aplikace Web MVC, SPA webové a nativní mobilní aplikace).</span><span class="sxs-lookup"><span data-stu-id="eedac-157">The application consists of multiple subsystems, including several e-store UI front ends (a Web MVC app, a Web SPA, and a native mobile app).</span></span> <span data-ttu-id="eedac-158">Zahrnuje také back-end mikroslužeb a kontejnerů pro všechny požadované operace na straně serveru.</span><span class="sxs-lookup"><span data-stu-id="eedac-158">It also includes the back-end microservices and containers for all required server-side operations.</span></span> 

<span data-ttu-id="eedac-159">Účelem aplikace je k prezentaci vzorech architektury.</span><span class="sxs-lookup"><span data-stu-id="eedac-159">The purpose of the application is to showcase architectural patterns.</span></span> <span data-ttu-id="eedac-160">**IT není připravené pro produkční prostředí ŠABLONU** ke spouštění skutečných aplikací.</span><span class="sxs-lookup"><span data-stu-id="eedac-160">**IT IS NOT A PRODUCTION-READY TEMPLATE** to start real-world applications.</span></span> <span data-ttu-id="eedac-161">Aplikace ve skutečnosti je ve stavu trvalé beta, jak se také používá k testování nových potenciálně zajímavý technologií, jako zobrazí.</span><span class="sxs-lookup"><span data-stu-id="eedac-161">In fact, the application is in a permanent beta state, as it’s also used to test new potentially interesting technologies as they show up.</span></span>

## <a name="send-us-your-feedback"></a><span data-ttu-id="eedac-162">Pošlete nám svůj názor!</span><span class="sxs-lookup"><span data-stu-id="eedac-162">Send us your feedback!</span></span>

<span data-ttu-id="eedac-163">Jsme napsali této příručce, které vám pomůžou porozumět architektuře mikroslužeb v rozhraní .NET a kontejnerizovaných aplikací.</span><span class="sxs-lookup"><span data-stu-id="eedac-163">We wrote this guide to help you understand the architecture of containerized applications and microservices in .NET.</span></span> <span data-ttu-id="eedac-164">Průvodce a související referenční aplikace bude se vyvíjí, takže vaše připomínky budou vítány!</span><span class="sxs-lookup"><span data-stu-id="eedac-164">The guide and related reference application will be evolving, so we welcome your feedback!</span></span> <span data-ttu-id="eedac-165">Pokud máte připomínky jak se tento průvodce může zlepšit, odešlete jim:</span><span class="sxs-lookup"><span data-stu-id="eedac-165">If you have comments about how this guide can be improved, please send them to:</span></span>

[dotnet-architecture-ebooks-feedback@service.microsoft.com](mailto:dotnet-architecture-ebooks-feedback@service.microsoft.com)

## <a name="credits"></a><span data-ttu-id="eedac-166">Závěrečné titulky</span><span class="sxs-lookup"><span data-stu-id="eedac-166">Credits</span></span>

<span data-ttu-id="eedac-167">Spoluautoři:</span><span class="sxs-lookup"><span data-stu-id="eedac-167">Co-Authors:</span></span>

> <span data-ttu-id="eedac-168">**De la Torre Cesarovi**, Senior PM, .NET produktový tým Microsoft Corp.</span><span class="sxs-lookup"><span data-stu-id="eedac-168">**Cesar de la Torre**, Sr. PM, .NET product team, Microsoft Corp.</span></span>
>
> <span data-ttu-id="eedac-169">**Bill Wagnera**, Senior obsahu pro vývojáře, C + E, Microsoft Corp.</span><span class="sxs-lookup"><span data-stu-id="eedac-169">**Bill Wagner**, Sr. Content Developer, C+E, Microsoft Corp.</span></span>
>
> <span data-ttu-id="eedac-170">**Mike Rousos**, hlavní softwarový inženýr, týmu DevDiv CAT, Microsoft</span><span class="sxs-lookup"><span data-stu-id="eedac-170">**Mike Rousos**, Principal Software Engineer, DevDiv CAT team, Microsoft</span></span>

<span data-ttu-id="eedac-171">Editory:</span><span class="sxs-lookup"><span data-stu-id="eedac-171">Editors:</span></span>

> <span data-ttu-id="eedac-172">**Mike Pope**</span><span class="sxs-lookup"><span data-stu-id="eedac-172">**Mike Pope**</span></span>
>
> <span data-ttu-id="eedac-173">**Steve Hoag**</span><span class="sxs-lookup"><span data-stu-id="eedac-173">**Steve Hoag**</span></span>

<span data-ttu-id="eedac-174">Účastníci a recenzenti:</span><span class="sxs-lookup"><span data-stu-id="eedac-174">Participants and reviewers:</span></span>

> <span data-ttu-id="eedac-175">**Jeffrey Richter**, Partner softwaru Eng týmu Azure, Microsoft</span><span class="sxs-lookup"><span data-stu-id="eedac-175">**Jeffrey Richter**, Partner Software Eng, Azure team, Microsoft</span></span>
>
> <span data-ttu-id="eedac-176">**Jimmy Bogard**, hlavní architekt na Headspring</span><span class="sxs-lookup"><span data-stu-id="eedac-176">**Jimmy Bogard**, Chief Architect at Headspring</span></span>
>
> <span data-ttu-id="eedac-177">**UDI Dahan**, Zakladatel a generální ředitel, určitého softwaru</span><span class="sxs-lookup"><span data-stu-id="eedac-177">**Udi Dahan**, Founder & CEO, Particular Software</span></span>
>
> <span data-ttu-id="eedac-178">**Jimmy Nilsson**, Spoluzakladatel a generální Factor10</span><span class="sxs-lookup"><span data-stu-id="eedac-178">**Jimmy Nilsson**, Co-founder and CEO of Factor10</span></span>
>
> <span data-ttu-id="eedac-179">**Glenn Condron**, Senior Program Manager tým ASP.NET</span><span class="sxs-lookup"><span data-stu-id="eedac-179">**Glenn Condron**, Sr. Program Manager, ASP.NET team</span></span>
>
> <span data-ttu-id="eedac-180">**Označit Fussell**, hlavní Projektový manažer zájemce, tým Azure Service Fabric, Microsoft</span><span class="sxs-lookup"><span data-stu-id="eedac-180">**Mark Fussell**, Principal PM Lead, Azure Service Fabric team, Microsoft</span></span>
>
> <span data-ttu-id="eedac-181">**Diego Vega**, PM zájemce, Entity Framework týmu, Microsoft</span><span class="sxs-lookup"><span data-stu-id="eedac-181">**Diego Vega**, PM Lead, Entity Framework team, Microsoft</span></span>
>
> <span data-ttu-id="eedac-182">**Jiří Dorrans**, hlavní manažer programu zabezpečení</span><span class="sxs-lookup"><span data-stu-id="eedac-182">**Barry Dorrans**, Sr. Security Program Manager</span></span>
>
> <span data-ttu-id="eedac-183">**Rowan Miller**, Senior Program Manager, Microsoft</span><span class="sxs-lookup"><span data-stu-id="eedac-183">**Rowan Miller**, Sr. Program Manager, Microsoft</span></span>
>
> <span data-ttu-id="eedac-184">**Ankit Asthana**, hlavní manažer PM, týmu .NET, Microsoft</span><span class="sxs-lookup"><span data-stu-id="eedac-184">**Ankit Asthana**, Principal PM Manager, .NET team, Microsoft</span></span>
>
> <span data-ttu-id="eedac-185">**Scott Hunter**, Partner Director oddělení PM, týmu .NET, Microsoft</span><span class="sxs-lookup"><span data-stu-id="eedac-185">**Scott Hunter**, Partner Director PM, .NET team, Microsoft</span></span>
>
> <span data-ttu-id="eedac-186">**Dokončení Anil**, hlavní programový manažer týmu .NET, Microsoft</span><span class="sxs-lookup"><span data-stu-id="eedac-186">**Nish Anil**, Sr. Program Manager, .NET team, Microsoft</span></span>
>
> <span data-ttu-id="eedac-187">**Dylan Reisenberger**, architekt a vedoucí vývoje v Polly</span><span class="sxs-lookup"><span data-stu-id="eedac-187">**Dylan Reisenberger**, Architect and Dev Lead at Polly</span></span>
>
> <span data-ttu-id="eedac-188">**Steve Smith**, Tvůrce softwaru & Trainer na ASPSmith Ltd.</span><span class="sxs-lookup"><span data-stu-id="eedac-188">**Steve Smith**, Software Craftsman & Trainer at ASPSmith Ltd.</span></span>
>
> <span data-ttu-id="eedac-189">**Ian Cooper**, kódování navrhovat jasnější na</span><span class="sxs-lookup"><span data-stu-id="eedac-189">**Ian Cooper**, Coding Architect at Brighter</span></span>
>
> <span data-ttu-id="eedac-190">**Unai Zorrilla**, architekt a vedoucí vývoje v Plain Concepts</span><span class="sxs-lookup"><span data-stu-id="eedac-190">**Unai Zorrilla**, Architect and Dev Lead at Plain Concepts</span></span>
>
> <span data-ttu-id="eedac-191">**Eduard Tomáši**, vedoucí vývoje v Plain Concepts</span><span class="sxs-lookup"><span data-stu-id="eedac-191">**Eduard Tomas**, Dev Lead at Plain Concepts</span></span>
>
> <span data-ttu-id="eedac-192">**Ramon Tomáši**, vývojář v Plain Concepts</span><span class="sxs-lookup"><span data-stu-id="eedac-192">**Ramon Tomas**, Developer at Plain Concepts</span></span>
>
> <span data-ttu-id="eedac-193">**David Sanz**, vývojář v Plain Concepts</span><span class="sxs-lookup"><span data-stu-id="eedac-193">**David Sanz**, Developer at Plain Concepts</span></span>
>
> <span data-ttu-id="eedac-194">**Javier Valero**, hlavní, provozní ředitel ve Grupo řešení</span><span class="sxs-lookup"><span data-stu-id="eedac-194">**Javier Valero**, Chief Operating Officer at Grupo Solutio</span></span>
>
> <span data-ttu-id="eedac-195">**Pierre Millet**, Sr. Consultant, Microsoft</span><span class="sxs-lookup"><span data-stu-id="eedac-195">**Pierre Millet**, Sr. Consultant, Microsoft</span></span>
>
> <span data-ttu-id="eedac-196">**Michael Friis**, správce produktu, Inc Dockeru</span><span class="sxs-lookup"><span data-stu-id="eedac-196">**Michael Friis**, Product Manager, Docker Inc</span></span>
>
> <span data-ttu-id="eedac-197">**Charles Lowell**, softwarový inženýr, týmu VS CAT, Microsoft</span><span class="sxs-lookup"><span data-stu-id="eedac-197">**Charles Lowell**, Software Engineer, VS CAT team, Microsoft</span></span>
>
> <span data-ttu-id="eedac-198">**Miguel Veloso**, Senior konzultant na Turing výzvy</span><span class="sxs-lookup"><span data-stu-id="eedac-198">**Miguel Veloso**, Sr. Consultant at Turing Challenge</span></span>

## <a name="copyright"></a><span data-ttu-id="eedac-199">Copyright</span><span class="sxs-lookup"><span data-stu-id="eedac-199">Copyright</span></span>

<span data-ttu-id="eedac-200">Ke stažení je k dispozici na: <https://aka.ms/microservicesebook></span><span class="sxs-lookup"><span data-stu-id="eedac-200">DOWNLOAD available at: <https://aka.ms/microservicesebook></span></span>

<span data-ttu-id="eedac-201">PUBLIKOVAL(A)</span><span class="sxs-lookup"><span data-stu-id="eedac-201">PUBLISHED BY</span></span>

<span data-ttu-id="eedac-202">Microsoft Developer Division, .NET a Visual Studio produktových týmů</span><span class="sxs-lookup"><span data-stu-id="eedac-202">Microsoft Developer Division, .NET and Visual Studio product teams</span></span>

<span data-ttu-id="eedac-203">A division of Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="eedac-203">A division of Microsoft Corporation</span></span>

<span data-ttu-id="eedac-204">One Microsoft Way</span><span class="sxs-lookup"><span data-stu-id="eedac-204">One Microsoft Way</span></span>

<span data-ttu-id="eedac-205">Redmond, Washington 98052-6399</span><span class="sxs-lookup"><span data-stu-id="eedac-205">Redmond, Washington 98052-6399</span></span>

<span data-ttu-id="eedac-206">Copyright © 2018 by Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="eedac-206">Copyright © 2018 by Microsoft Corporation</span></span>

<span data-ttu-id="eedac-207">Všechna práva vyhrazena.</span><span class="sxs-lookup"><span data-stu-id="eedac-207">All rights reserved.</span></span> <span data-ttu-id="eedac-208">Žádná část obsahu této knihy může reprodukovat nebo v libovolné formě nebo jakýmikoli prostředky bez písemného souhlasu vydavatele.</span><span class="sxs-lookup"><span data-stu-id="eedac-208">No part of the contents of this book may be reproduced or transmitted in any form or by any means without the written permission of the publisher.</span></span>

<span data-ttu-id="eedac-209">Tato kniha je k dispozici "jako-je" a vyjadřuje zobrazení autora a názory.</span><span class="sxs-lookup"><span data-stu-id="eedac-209">This book is provided “as-is” and expresses the author’s views and opinions.</span></span> <span data-ttu-id="eedac-210">Zobrazení, názory a informace v této knize, včetně adres URL a jiných odkazů na internetové weby, mohou změnit bez předchozího upozornění.</span><span class="sxs-lookup"><span data-stu-id="eedac-210">The views, opinions and information expressed in this book, including URL and other Internet website references, may change without notice.</span></span>

<span data-ttu-id="eedac-211">Některé zde uvedené příklady jsou k dispozici pouze pro ilustraci a jsou smyšlené.</span><span class="sxs-lookup"><span data-stu-id="eedac-211">Some examples depicted herein are provided for illustration only and are fictitious.</span></span> <span data-ttu-id="eedac-212">Žádný skutečný vztah nebo spojení ani je určena ji vyvozovat.</span><span class="sxs-lookup"><span data-stu-id="eedac-212">No real association or connection is intended or should be inferred.</span></span>

<span data-ttu-id="eedac-213">Microsoft a ochranné známky uvedený na <https://www.microsoft.com> na webové stránce "Ochranné známky" jsou obchodní známky společností skupiny Microsoft.</span><span class="sxs-lookup"><span data-stu-id="eedac-213">Microsoft and the trademarks listed at <https://www.microsoft.com> on the “Trademarks” webpage are trademarks of the Microsoft group of companies.</span></span>

<span data-ttu-id="eedac-214">Mac a macOS jsou ochranné známky společnosti Apple Inc.</span><span class="sxs-lookup"><span data-stu-id="eedac-214">Mac and macOS are trademarks of Apple Inc.</span></span>

<span data-ttu-id="eedac-215">Velryba logo Dockeru je registrovaná ochranná známka společnosti Docker, Inc. Použít oprávnění.</span><span class="sxs-lookup"><span data-stu-id="eedac-215">The Docker whale logo is a registered trademark of Docker, Inc. Used by permission.</span></span>

<span data-ttu-id="eedac-216">Všechny ostatní značky a loga jsou majetkem příslušných vlastníků.</span><span class="sxs-lookup"><span data-stu-id="eedac-216">All other marks and logos are property of their respective owners.</span></span>

>[!div class="step-by-step"]
>[<span data-ttu-id="eedac-217">Next</span><span class="sxs-lookup"><span data-stu-id="eedac-217">Next</span></span>](container-docker-introduction/index.md)
