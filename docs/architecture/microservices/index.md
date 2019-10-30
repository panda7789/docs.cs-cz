---
title: Mikroslužby .NET. Architektura pro kontejnerizované aplikace .NET
description: Architektura mikroslužeb .NET pro kontejnerové aplikace .NET | Mikroslužby jsou modulární a nezávisle nasazujíelné služby. Kontejnery Docker (pro Linux a Windows) zjednodušují nasazení a testování tím, že propojí službu a její závislosti do jedné jednotky, která se pak spustí v izolovaném prostředí.
ms.date: 01/07/2019
ms.openlocfilehash: 7fa4935fe56ca873a5311812637964083e34170e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73089911"
---
# <a name="net-microservices-architecture-for-containerized-net-applications"></a><span data-ttu-id="3bccc-105">Mikroslužby .NET: architektura pro kontejnerové aplikace .NET</span><span class="sxs-lookup"><span data-stu-id="3bccc-105">.NET Microservices: Architecture for Containerized .NET Applications</span></span>

![Titulní kniha](./media/cover-small.png)

<span data-ttu-id="3bccc-107">**Edice 2.2** – aktualizace na ASP.NET Core 2,2</span><span class="sxs-lookup"><span data-stu-id="3bccc-107">**EDITION v2.2** - Updated to ASP.NET Core 2.2</span></span>

<span data-ttu-id="3bccc-108">Tato příručka je Úvod k vývoji aplikací založených na mikroslužbách a jejich správě pomocí kontejnerů.</span><span class="sxs-lookup"><span data-stu-id="3bccc-108">This guide is an introduction to developing microservices-based applications and managing them using containers.</span></span> <span data-ttu-id="3bccc-109">Popisuje přístupy k návrhu a implementaci architektury pomocí .NET Core a kontejnerů Docker.</span><span class="sxs-lookup"><span data-stu-id="3bccc-109">It discusses architectural design and implementation approaches using .NET Core and Docker containers.</span></span>

<span data-ttu-id="3bccc-110">Aby bylo snazší začít, příručka se zaměřuje na odkaz na kontejner a aplikaci založenou na mikroslužbách, kterou můžete prozkoumat.</span><span class="sxs-lookup"><span data-stu-id="3bccc-110">To make it easier to get started, the guide focuses on a reference containerized and microservice-based application that you can explore.</span></span> <span data-ttu-id="3bccc-111">Referenční aplikace je k dispozici v úložišti GitHub [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) .</span><span class="sxs-lookup"><span data-stu-id="3bccc-111">The reference application is available at the [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) GitHub repo.</span></span>

## <a name="action-links"></a><span data-ttu-id="3bccc-112">Odkazy na akce</span><span class="sxs-lookup"><span data-stu-id="3bccc-112">Action links</span></span>

- <span data-ttu-id="3bccc-113">Stáhnout tuto elektronickou knihu ve zvoleném formátu (pouze anglické verze): | [PDF](https://aka.ms/microservicesebook) | [MOBI](https://dotnet.microsoft.com/download/thank-you/microservices-architecture-ebook-mobi) | [EPUB](https://dotnet.microsoft.com/download/thank-you/microservices-architecture-ebook-epub) |</span><span class="sxs-lookup"><span data-stu-id="3bccc-113">Download this e-book in your format of choice (English version only): | [PDF](https://aka.ms/microservicesebook) | [MOBI](https://dotnet.microsoft.com/download/thank-you/microservices-architecture-ebook-mobi) | [EPUB](https://dotnet.microsoft.com/download/thank-you/microservices-architecture-ebook-epub) |</span></span>

- <span data-ttu-id="3bccc-114">Klonování/rozvětvení referenční aplikace [eShopOnContainers na GitHubu](https://github.com/dotnet-architecture/eShopOnContainers)</span><span class="sxs-lookup"><span data-stu-id="3bccc-114">Clone/Fork the reference application [eShopOnContainers on GitHub](https://github.com/dotnet-architecture/eShopOnContainers)</span></span>

- <span data-ttu-id="3bccc-115">Podívejte se na [úvodní video na Channel 9](https://aka.ms/microservices-video)</span><span class="sxs-lookup"><span data-stu-id="3bccc-115">Watch the [introductory video on Channel 9](https://aka.ms/microservices-video)</span></span>

- <span data-ttu-id="3bccc-116">Získejte hned informace o [architektuře mikroslužeb](https://aka.ms/MicroservicesArchitecture) .</span><span class="sxs-lookup"><span data-stu-id="3bccc-116">Get to know the [Microservices Architecture](https://aka.ms/MicroservicesArchitecture) right away</span></span>

## <a name="introduction"></a><span data-ttu-id="3bccc-117">Úvod</span><span class="sxs-lookup"><span data-stu-id="3bccc-117">Introduction</span></span>

<span data-ttu-id="3bccc-118">Podniky mají stále větší náklady na úspory nákladů, řešení problémů s nasazením a vylepšení DevOps a produkčních operací pomocí kontejnerů.</span><span class="sxs-lookup"><span data-stu-id="3bccc-118">Enterprises are increasingly realizing cost savings, solving deployment problems, and improving DevOps and production operations by using containers.</span></span> <span data-ttu-id="3bccc-119">Společnost Microsoft vydala inovace kontejnerů pro Windows a Linux tím, že vytváří produkty, jako je Azure Kubernetes Service a Azure Service Fabric, a spolupracuje s oborovými vedoucími, jako jsou Docker, Mesosphere a Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="3bccc-119">Microsoft has been releasing container innovations for Windows and Linux by creating products like Azure Kubernetes Service and Azure Service Fabric, and by partnering with industry leaders like Docker, Mesosphere, and Kubernetes.</span></span> <span data-ttu-id="3bccc-120">Tyto produkty poskytují řešení kontejnerů, která společnosti pomůžou sestavovat a nasazovat aplikace při rychlosti a škálování cloudu bez ohledu na to, jakou platformu nebo nástroje.</span><span class="sxs-lookup"><span data-stu-id="3bccc-120">These products deliver container solutions that help companies build and deploy applications at cloud speed and scale, whatever their choice of platform or tools.</span></span>

<span data-ttu-id="3bccc-121">Docker se stává jako de facto standard v odvětví kontejneru, který je podporovaný nejvýznamnějšími dodavateli v ekosystémech Windows a Linux.</span><span class="sxs-lookup"><span data-stu-id="3bccc-121">Docker is becoming the de facto standard in the container industry, supported by the most significant vendors in the Windows and Linux ecosystems.</span></span> <span data-ttu-id="3bccc-122">(Microsoft je jedním z hlavních dodavatelů cloudů, kteří podporují Docker.) V budoucnu se Docker bude pravděpodobně všudypřítomný do libovolného datacentra v cloudu nebo v místním prostředí.</span><span class="sxs-lookup"><span data-stu-id="3bccc-122">(Microsoft is one of the main cloud vendors supporting Docker.) In the future, Docker will probably be ubiquitous in any datacenter in the cloud or on-premises.</span></span>

<span data-ttu-id="3bccc-123">Kromě toho architektura [mikroslužeb](https://martinfowler.com/articles/microservices.html) se vychází jako důležitý přístup pro distribuované klíčové aplikace.</span><span class="sxs-lookup"><span data-stu-id="3bccc-123">In addition, the [microservices](https://martinfowler.com/articles/microservices.html) architecture is emerging as an important approach for distributed mission-critical applications.</span></span> <span data-ttu-id="3bccc-124">V architektuře založené na mikroslužbách je aplikace postavená na kolekci služeb, které se dají vyvíjet, testovat, nasazovat a samostatně nakládat s verzemi.</span><span class="sxs-lookup"><span data-stu-id="3bccc-124">In a microservice-based architecture, the application is built on a collection of services that can be developed, tested, deployed, and versioned independently.</span></span>

## <a name="about-this-guide"></a><span data-ttu-id="3bccc-125">O této příručce</span><span class="sxs-lookup"><span data-stu-id="3bccc-125">About this guide</span></span>

<span data-ttu-id="3bccc-126">Tato příručka je Úvod k vývoji aplikací založených na mikroslužbách a jejich správě pomocí kontejnerů.</span><span class="sxs-lookup"><span data-stu-id="3bccc-126">This guide is an introduction to developing microservices-based applications and managing them using containers.</span></span> <span data-ttu-id="3bccc-127">Popisuje přístupy k návrhu a implementaci architektury pomocí .NET Core a kontejnerů Docker.</span><span class="sxs-lookup"><span data-stu-id="3bccc-127">It discusses architectural design and implementation approaches using .NET Core and Docker containers.</span></span> <span data-ttu-id="3bccc-128">Aby bylo snazší začít s kontejnery a mikroslužbami, tato příručka se zaměřuje na odkaz na kontejner a aplikaci založenou na mikroslužbách, kterou můžete prozkoumat.</span><span class="sxs-lookup"><span data-stu-id="3bccc-128">To make it easier to get started with containers and microservices, the guide focuses on a reference containerized and microservice-based application that you can explore.</span></span> <span data-ttu-id="3bccc-129">Ukázková aplikace je k dispozici v úložišti GitHub [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) .</span><span class="sxs-lookup"><span data-stu-id="3bccc-129">The sample application is available at the [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) GitHub repo.</span></span>

<span data-ttu-id="3bccc-130">Tato příručka poskytuje pokyny pro základní vývoj a architekturu primárně na úrovni vývojového prostředí se zaměřením na dvě technologie: Docker a .NET Core.</span><span class="sxs-lookup"><span data-stu-id="3bccc-130">This guide provides foundational development and architectural guidance primarily at a development environment level with a focus on two technologies: Docker and .NET Core.</span></span> <span data-ttu-id="3bccc-131">Naším záměrem je přečíst si tuto příručku při zvažování návrhu vaší aplikace bez zaměření na infrastrukturu (Cloud nebo místní) vašeho provozního prostředí.</span><span class="sxs-lookup"><span data-stu-id="3bccc-131">Our intention is that you read this guide when thinking about your application design without focusing on the infrastructure (cloud or on-premises) of your production environment.</span></span> <span data-ttu-id="3bccc-132">Rozhodnutí o vaší infrastruktuře budete provádět později při vytváření aplikací připravených pro produkční prostředí.</span><span class="sxs-lookup"><span data-stu-id="3bccc-132">You will make decisions about your infrastructure later, when you create your production-ready applications.</span></span> <span data-ttu-id="3bccc-133">Proto je tato příručka zamýšlená jako infrastruktura nezávislá a další vývojové prostředí.</span><span class="sxs-lookup"><span data-stu-id="3bccc-133">Therefore, this guide is intended to be infrastructure agnostic and more development-environment-centric.</span></span>

<span data-ttu-id="3bccc-134">Po prostudování tohoto průvodce by vám v dalším kroku pomohlo zjistit mikroslužby připravené k výrobě na Microsoft Azure.</span><span class="sxs-lookup"><span data-stu-id="3bccc-134">After you have studied this guide, your next step would be to learn about production-ready microservices on Microsoft Azure.</span></span>

## <a name="version"></a><span data-ttu-id="3bccc-135">Version</span><span class="sxs-lookup"><span data-stu-id="3bccc-135">Version</span></span>

<span data-ttu-id="3bccc-136">Tato příručka byla revidována tak, aby kryla verzi **.NET Core 2,2** a řadu dalších aktualizací, které se vztahují ke stejným "Wave" technologií (tj.</span><span class="sxs-lookup"><span data-stu-id="3bccc-136">This guide has been revised to cover **.NET Core 2.2** version plus many additional updates related to the same “wave” of technologies (that is.</span></span> <span data-ttu-id="3bccc-137">Azure a další technologie jiných výrobců se shodují v čase s .NET Core 2,2.</span><span class="sxs-lookup"><span data-stu-id="3bccc-137">Azure and additional 3rd party technologies) coinciding in time with .NET Core 2.2.</span></span> <span data-ttu-id="3bccc-138">To je důvod, proč se verze knihy aktualizovala také na verzi **2,2**.</span><span class="sxs-lookup"><span data-stu-id="3bccc-138">That’s why the book version has also been updated to version **2.2**.</span></span>

## <a name="what-this-guide-does-not-cover"></a><span data-ttu-id="3bccc-139">Co tato příručka nepokrývá</span><span class="sxs-lookup"><span data-stu-id="3bccc-139">What this guide does not cover</span></span>

<span data-ttu-id="3bccc-140">Tato příručka se nezaměřuje na životní cyklus aplikací, DevOps, kanály CI/CD ani týmovou práci.</span><span class="sxs-lookup"><span data-stu-id="3bccc-140">This guide does not focus on the application lifecycle, DevOps, CI/CD pipelines, or team work.</span></span> <span data-ttu-id="3bccc-141">[Doplněný životní cyklus aplikace Docker v kontejneru s využitím platformy a nástrojů Microsoftu se](https://aka.ms/dockerlifecycleebook) zaměřuje na tento předmět.</span><span class="sxs-lookup"><span data-stu-id="3bccc-141">The complementary guide [Containerized Docker Application Lifecycle with Microsoft Platform and Tools](https://aka.ms/dockerlifecycleebook) focuses on that subject.</span></span> <span data-ttu-id="3bccc-142">Aktuální příručka také neposkytuje podrobnosti o implementaci infrastruktury Azure, jako jsou informace o konkrétních orchestrcích.</span><span class="sxs-lookup"><span data-stu-id="3bccc-142">The current guide also does not provide implementation details on Azure infrastructure, such as information on specific orchestrators.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="3bccc-143">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="3bccc-143">Additional resources</span></span>

- <span data-ttu-id="3bccc-144">**Kontejnerové životní cykly aplikace Docker s platformou a nástroji Microsoftu** (elektronická kniha ke stažení)</span><span class="sxs-lookup"><span data-stu-id="3bccc-144">**Containerized Docker Application Lifecycle with Microsoft Platform and Tools** (downloadable e-book)</span></span>  
    <https://aka.ms/dockerlifecycleebook>

## <a name="who-should-use-this-guide"></a><span data-ttu-id="3bccc-145">Kdo by měl používat tuto příručku</span><span class="sxs-lookup"><span data-stu-id="3bccc-145">Who should use this guide</span></span>

<span data-ttu-id="3bccc-146">Tuto příručku jsme napsali pro vývojáře a architekty řešení, kteří jsou noví pro vývoj aplikací založených na Docker a na architekturu založenou na mikroslužbách.</span><span class="sxs-lookup"><span data-stu-id="3bccc-146">We wrote this guide for developers and solution architects who are new to Docker-based application development and to microservices-based architecture.</span></span> <span data-ttu-id="3bccc-147">Tato příručka je určena pro vás, pokud se chcete dozvědět, jak architekt, navrhovat a implementovat aplikace pro zkušební použití pomocí vývojových technologií Microsoftu (se speciálním zaměřením na .NET Core) a s kontejnery Docker.</span><span class="sxs-lookup"><span data-stu-id="3bccc-147">This guide is for you if you want to learn how to architect, design, and implement proof-of-concept applications with Microsoft development technologies (with special focus on .NET Core) and with Docker containers.</span></span>

<span data-ttu-id="3bccc-148">Tento průvodce najdete také v případě, že jste Tvůrce technického rozhodnutí, jako je například podnikový architekt, který vyžaduje architekturu a technologický přehled, než se rozhodnete, jaký přístup vybrat pro nové a moderní distribuované aplikace.</span><span class="sxs-lookup"><span data-stu-id="3bccc-148">You will also find this guide useful if you are a technical decision maker, such as an enterprise architect, who wants an architecture and technology overview before you decide on what approach to select for new and modern distributed applications.</span></span>

### <a name="how-to-use-this-guide"></a><span data-ttu-id="3bccc-149">Jak používat tohoto průvodce</span><span class="sxs-lookup"><span data-stu-id="3bccc-149">How to use this guide</span></span>

<span data-ttu-id="3bccc-150">První část této příručky zavádí kontejnery Docker, popisuje, jak zvolit mezi .NET Core a .NET Framework jako vývojovou architekturou a poskytuje přehled mikroslužeb.</span><span class="sxs-lookup"><span data-stu-id="3bccc-150">The first part of this guide introduces Docker containers, discusses how to choose between .NET Core and the .NET Framework as a development framework, and provides an overview of microservices.</span></span> <span data-ttu-id="3bccc-151">Tento obsah je určen pro architekty a pracovníky technického rozhodování, kteří chtějí přehled, ale nemusí se soustředit na podrobnosti implementace kódu.</span><span class="sxs-lookup"><span data-stu-id="3bccc-151">This content is for architects and technical decision makers who want an overview but don't need to focus on code implementation details.</span></span>

<span data-ttu-id="3bccc-152">Druhá část příručky začíná [procesem vývoje pro aplikace založené na Docker](./docker-application-development-process/index.md) .</span><span class="sxs-lookup"><span data-stu-id="3bccc-152">The second part of the guide starts with the [Development process for Docker based applications](./docker-application-development-process/index.md) section.</span></span> <span data-ttu-id="3bccc-153">Zaměřuje se na vývoj a vzory mikroslužeb pro implementaci aplikací pomocí .NET Core a Docker.</span><span class="sxs-lookup"><span data-stu-id="3bccc-153">It focuses on development and microservice patterns for implementing applications using .NET Core and Docker.</span></span> <span data-ttu-id="3bccc-154">Tato část bude mít největší zájem na vývojáře a architekty, kteří se chtějí zaměřit na kód a podrobnosti o vzorech a implementaci.</span><span class="sxs-lookup"><span data-stu-id="3bccc-154">This section will be of most interest to developers and architects who want to focus on code and on patterns and implementation details.</span></span>

## <a name="related-microservice-and-container-based-reference-application-eshoponcontainers"></a><span data-ttu-id="3bccc-155">Související referenční aplikace založené na mikroslužbách a kontejneru: eShopOnContainers</span><span class="sxs-lookup"><span data-stu-id="3bccc-155">Related microservice and container-based reference application: eShopOnContainers</span></span>

<span data-ttu-id="3bccc-156">Aplikace eShopOnContainers je open source referenční aplikace pro .NET Core a mikroslužby, které jsou navržené tak, aby se nasadily pomocí kontejnerů Docker.</span><span class="sxs-lookup"><span data-stu-id="3bccc-156">The eShopOnContainers application is an open-source reference app for .NET Core and microservices that is designed to be deployed using Docker containers.</span></span> <span data-ttu-id="3bccc-157">Aplikace se skládá z několika subsystémů, včetně několika front-Store přední konců uživatelského rozhraní (aplikace webové MVC, webové zabezpečené ověřování a nativní mobilní aplikace).</span><span class="sxs-lookup"><span data-stu-id="3bccc-157">The application consists of multiple subsystems, including several e-store UI front ends (a Web MVC app, a Web SPA, and a native mobile app).</span></span> <span data-ttu-id="3bccc-158">Zahrnuje také back-endové mikroslužby a kontejnery pro všechny požadované operace na straně serveru.</span><span class="sxs-lookup"><span data-stu-id="3bccc-158">It also includes the back-end microservices and containers for all required server-side operations.</span></span>

<span data-ttu-id="3bccc-159">Účelem aplikace je předvedení struktur architektury.</span><span class="sxs-lookup"><span data-stu-id="3bccc-159">The purpose of the application is to showcase architectural patterns.</span></span> <span data-ttu-id="3bccc-160">Nejedná se **o šablonu připravenou pro produkční prostředí** pro spouštění reálných aplikací.</span><span class="sxs-lookup"><span data-stu-id="3bccc-160">**IT IS NOT A PRODUCTION-READY TEMPLATE** to start real-world applications.</span></span> <span data-ttu-id="3bccc-161">Ve skutečnosti je aplikace v trvalé verzi beta verze, protože se také používá k otestování nových potenciálně zajímavých technologií, které se zobrazují.</span><span class="sxs-lookup"><span data-stu-id="3bccc-161">In fact, the application is in a permanent beta state, as it’s also used to test new potentially interesting technologies as they show up.</span></span>

## <a name="send-us-your-feedback"></a><span data-ttu-id="3bccc-162">Pošlete nám svůj názor.</span><span class="sxs-lookup"><span data-stu-id="3bccc-162">Send us your feedback!</span></span>

<span data-ttu-id="3bccc-163">Tento průvodce jsme napsali a pomohli vám pochopit architekturu kontejnerových aplikací a mikroslužeb v .NET.</span><span class="sxs-lookup"><span data-stu-id="3bccc-163">We wrote this guide to help you understand the architecture of containerized applications and microservices in .NET.</span></span> <span data-ttu-id="3bccc-164">Bude vyvíjena příručka a související referenční aplikace, takže jsme Vítejte na vašem názoru.</span><span class="sxs-lookup"><span data-stu-id="3bccc-164">The guide and related reference application will be evolving, so we welcome your feedback!</span></span> <span data-ttu-id="3bccc-165">Pokud máte komentáře týkající se toho, jak se dá tato příručka zlepšit, pošlete prosím jim tyto informace:</span><span class="sxs-lookup"><span data-stu-id="3bccc-165">If you have comments about how this guide can be improved, please send them to:</span></span>

[dotnet-architecture-ebooks-feedback@service.microsoft.com](mailto:dotnet-architecture-ebooks-feedback@service.microsoft.com)

## <a name="credits"></a><span data-ttu-id="3bccc-166">dobropis</span><span class="sxs-lookup"><span data-stu-id="3bccc-166">Credits</span></span>

<span data-ttu-id="3bccc-167">Spoluautoři:</span><span class="sxs-lookup"><span data-stu-id="3bccc-167">Co-Authors:</span></span>

> <span data-ttu-id="3bccc-168">**Cesar de la Torre**, SR. PM, produktový tým .NET, Microsoft Corp.</span><span class="sxs-lookup"><span data-stu-id="3bccc-168">**Cesar de la Torre**, Sr. PM, .NET product team, Microsoft Corp.</span></span>
>
> <span data-ttu-id="3bccc-169">**Bill Wagner**, SR. Content Developer, C + E, Microsoft Corp.</span><span class="sxs-lookup"><span data-stu-id="3bccc-169">**Bill Wagner**, Sr. Content Developer, C+E, Microsoft Corp.</span></span>
>
> <span data-ttu-id="3bccc-170">**Jan Rousos**, hlavní softwarový inženýr, DevDiv Cat tým, Microsoft</span><span class="sxs-lookup"><span data-stu-id="3bccc-170">**Mike Rousos**, Principal Software Engineer, DevDiv CAT team, Microsoft</span></span>

<span data-ttu-id="3bccc-171">Editory</span><span class="sxs-lookup"><span data-stu-id="3bccc-171">Editors:</span></span>

> <span data-ttu-id="3bccc-172">**Mike Pope**</span><span class="sxs-lookup"><span data-stu-id="3bccc-172">**Mike Pope**</span></span>
>
> <span data-ttu-id="3bccc-173">**Steve Hoag**</span><span class="sxs-lookup"><span data-stu-id="3bccc-173">**Steve Hoag**</span></span>

<span data-ttu-id="3bccc-174">Účastníci a kontroloři:</span><span class="sxs-lookup"><span data-stu-id="3bccc-174">Participants and reviewers:</span></span>

> <span data-ttu-id="3bccc-175">**Jeffrey Richter**, partnerský software eng, tým Azure, Microsoft</span><span class="sxs-lookup"><span data-stu-id="3bccc-175">**Jeffrey Richter**, Partner Software Eng, Azure team, Microsoft</span></span>
>
> <span data-ttu-id="3bccc-176">**Jimmy Bogard**, hlavní architekt na headspring</span><span class="sxs-lookup"><span data-stu-id="3bccc-176">**Jimmy Bogard**, Chief Architect at Headspring</span></span>
>
> <span data-ttu-id="3bccc-177">**UDI Dahan**, zakladatel & výkonný ředitel, konkrétní software</span><span class="sxs-lookup"><span data-stu-id="3bccc-177">**Udi Dahan**, Founder & CEO, Particular Software</span></span>
>
> <span data-ttu-id="3bccc-178">**Jimmy Nilsson**, zakladatel a generální ředitel pro Factor10</span><span class="sxs-lookup"><span data-stu-id="3bccc-178">**Jimmy Nilsson**, Co-founder and CEO of Factor10</span></span>
>
> <span data-ttu-id="3bccc-179">**Glenn Condron**, SR. Program Manager, ASP.NET tým</span><span class="sxs-lookup"><span data-stu-id="3bccc-179">**Glenn Condron**, Sr. Program Manager, ASP.NET team</span></span>
>
> <span data-ttu-id="3bccc-180">**Mark Fussell**, hlavní vedoucí pro odpoledne, Azure Service Fabric Team, Microsoft</span><span class="sxs-lookup"><span data-stu-id="3bccc-180">**Mark Fussell**, Principal PM Lead, Azure Service Fabric team, Microsoft</span></span>
>
> <span data-ttu-id="3bccc-181">**Diegu Vega**, vedoucí pracovník, Entity Framework tým, Microsoft</span><span class="sxs-lookup"><span data-stu-id="3bccc-181">**Diego Vega**, PM Lead, Entity Framework team, Microsoft</span></span>
>
> <span data-ttu-id="3bccc-182">**Barryho Dorrans**, správce programu SR. Security</span><span class="sxs-lookup"><span data-stu-id="3bccc-182">**Barry Dorrans**, Sr. Security Program Manager</span></span>
>
> <span data-ttu-id="3bccc-183">**Rowan Miller**, SR. Program Manager, Microsoft</span><span class="sxs-lookup"><span data-stu-id="3bccc-183">**Rowan Miller**, Sr. Program Manager, Microsoft</span></span>
>
> <span data-ttu-id="3bccc-184">**Ankit Asthana**, hlavní správce odpoledne, tým .NET, Microsoft</span><span class="sxs-lookup"><span data-stu-id="3bccc-184">**Ankit Asthana**, Principal PM Manager, .NET team, Microsoft</span></span>
>
> <span data-ttu-id="3bccc-185">**Scott Hunterem**, ředitel pro partnery, tým .NET, Microsoft</span><span class="sxs-lookup"><span data-stu-id="3bccc-185">**Scott Hunter**, Partner Director PM, .NET team, Microsoft</span></span>
>
> <span data-ttu-id="3bccc-186">**Nish Anil**, SR. Program Manager, .NET Team, Microsoft</span><span class="sxs-lookup"><span data-stu-id="3bccc-186">**Nish Anil**, Sr. Program Manager, .NET team, Microsoft</span></span>
>
> <span data-ttu-id="3bccc-187">**Dylan Reisenberger**, architekt a vývojářského vedoucího v Polly</span><span class="sxs-lookup"><span data-stu-id="3bccc-187">**Dylan Reisenberger**, Architect and Dev Lead at Polly</span></span>
>
> <span data-ttu-id="3bccc-188">**Steve "ardalis" Smith** -Software Architect a Trainer- [Ardalis.com](https://ardalis.com)</span><span class="sxs-lookup"><span data-stu-id="3bccc-188">**Steve "ardalis" Smith** - Software Architect and Trainer - [Ardalis.com](https://ardalis.com)</span></span>
>
> <span data-ttu-id="3bccc-189">**Ian Cooper**, architekt kódu na jasnější úrovni</span><span class="sxs-lookup"><span data-stu-id="3bccc-189">**Ian Cooper**, Coding Architect at Brighter</span></span>
>
> <span data-ttu-id="3bccc-190">**Unai Zorrilla**, architekt a vývojářské olovo v jednoduchých konceptech</span><span class="sxs-lookup"><span data-stu-id="3bccc-190">**Unai Zorrilla**, Architect and Dev Lead at Plain Concepts</span></span>
>
> <span data-ttu-id="3bccc-191">**Eduard Tomas**, vedoucí pro vývoj na jednoduchých konceptech</span><span class="sxs-lookup"><span data-stu-id="3bccc-191">**Eduard Tomas**, Dev Lead at Plain Concepts</span></span>
>
> <span data-ttu-id="3bccc-192">**Ramon Tomas**, Developer na jednoduchých konceptech</span><span class="sxs-lookup"><span data-stu-id="3bccc-192">**Ramon Tomas**, Developer at Plain Concepts</span></span>
>
> <span data-ttu-id="3bccc-193">**David Sanz**, Developer na jednoduchých konceptech</span><span class="sxs-lookup"><span data-stu-id="3bccc-193">**David Sanz**, Developer at Plain Concepts</span></span>
>
> <span data-ttu-id="3bccc-194">**Javier Valero**, vedoucí pracovník v Grupo solutio</span><span class="sxs-lookup"><span data-stu-id="3bccc-194">**Javier Valero**, Chief Operating Officer at Grupo Solutio</span></span>
>
> <span data-ttu-id="3bccc-195">**Pierre-Millet**, SR. konzultant, Microsoft</span><span class="sxs-lookup"><span data-stu-id="3bccc-195">**Pierre Millet**, Sr. Consultant, Microsoft</span></span>
>
> <span data-ttu-id="3bccc-196">**Michael Friis**, produktový manažer, Docker Inc</span><span class="sxs-lookup"><span data-stu-id="3bccc-196">**Michael Friis**, Product Manager, Docker Inc</span></span>
>
> <span data-ttu-id="3bccc-197">**Charles Lowell**, software inženýr, vs Cat tým, Microsoft</span><span class="sxs-lookup"><span data-stu-id="3bccc-197">**Charles Lowell**, Software Engineer, VS CAT team, Microsoft</span></span>
>
> <span data-ttu-id="3bccc-198">**Miguel Veloso**, SR. konzultant při Turing výzvě</span><span class="sxs-lookup"><span data-stu-id="3bccc-198">**Miguel Veloso**, Sr. Consultant at Turing Challenge</span></span>

## <a name="copyright"></a><span data-ttu-id="3bccc-199">Úprava</span><span class="sxs-lookup"><span data-stu-id="3bccc-199">Copyright</span></span>

<span data-ttu-id="3bccc-200">STAŽENÍ k dispozici na adrese: <https://aka.ms/microservicesebook></span><span class="sxs-lookup"><span data-stu-id="3bccc-200">DOWNLOAD available at: <https://aka.ms/microservicesebook></span></span>

<span data-ttu-id="3bccc-201">PUBLIKOVAL (A)</span><span class="sxs-lookup"><span data-stu-id="3bccc-201">PUBLISHED BY</span></span>

<span data-ttu-id="3bccc-202">Microsoft Developer divize, .NET a Visual Studio Product teams</span><span class="sxs-lookup"><span data-stu-id="3bccc-202">Microsoft Developer Division, .NET and Visual Studio product teams</span></span>

<span data-ttu-id="3bccc-203">Divize společnosti Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="3bccc-203">A division of Microsoft Corporation</span></span>

<span data-ttu-id="3bccc-204">Jeden způsob Microsoftu</span><span class="sxs-lookup"><span data-stu-id="3bccc-204">One Microsoft Way</span></span>

<span data-ttu-id="3bccc-205">Redmond, Washington 98052-6399</span><span class="sxs-lookup"><span data-stu-id="3bccc-205">Redmond, Washington 98052-6399</span></span>

<span data-ttu-id="3bccc-206">Copyright © 2019 od společnosti Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="3bccc-206">Copyright © 2019 by Microsoft Corporation</span></span>

<span data-ttu-id="3bccc-207">Všechna práva vyhrazena.</span><span class="sxs-lookup"><span data-stu-id="3bccc-207">All rights reserved.</span></span> <span data-ttu-id="3bccc-208">Žádná část obsahu této knihy se nedá reprodukovat ani přenést v jakékoli formě nebo jakýmkoli způsobem bez písemného svolení vydavatele.</span><span class="sxs-lookup"><span data-stu-id="3bccc-208">No part of the contents of this book may be reproduced or transmitted in any form or by any means without the written permission of the publisher.</span></span>

<span data-ttu-id="3bccc-209">Tato kniha je k dispozici "tak jak jsou" a vyjadřuje zobrazení a stanoviska autora.</span><span class="sxs-lookup"><span data-stu-id="3bccc-209">This book is provided “as-is” and expresses the author’s views and opinions.</span></span> <span data-ttu-id="3bccc-210">Zobrazení, názory a informace vyjádřené v této knize, včetně adres URL a dalších odkazů na internetové weby, se mohou změnit bez předchozího upozornění.</span><span class="sxs-lookup"><span data-stu-id="3bccc-210">The views, opinions and information expressed in this book, including URL and other Internet website references, may change without notice.</span></span>

<span data-ttu-id="3bccc-211">Některé příklady, které jsou zde uvedeny, jsou k dispozici pouze pro ilustraci a jsou smyšlené.</span><span class="sxs-lookup"><span data-stu-id="3bccc-211">Some examples depicted herein are provided for illustration only and are fictitious.</span></span> <span data-ttu-id="3bccc-212">Neexistuje žádné skutečné přidružení nebo připojení, které by mělo být odvozeno.</span><span class="sxs-lookup"><span data-stu-id="3bccc-212">No real association or connection is intended or should be inferred.</span></span>

<span data-ttu-id="3bccc-213">Microsoft a ochranné známky uvedené na adrese <https://www.microsoft.com> na webové stránce ochranné známky jsou ochranné známky skupiny společností Microsoft.</span><span class="sxs-lookup"><span data-stu-id="3bccc-213">Microsoft and the trademarks listed at <https://www.microsoft.com> on the “Trademarks” webpage are trademarks of the Microsoft group of companies.</span></span>

<span data-ttu-id="3bccc-214">Mac a macOS jsou ochranné známky společnosti Apple Inc.</span><span class="sxs-lookup"><span data-stu-id="3bccc-214">Mac and macOS are trademarks of Apple Inc.</span></span>

<span data-ttu-id="3bccc-215">Logo Docker Whale je registrovaná ochranná známka společnosti Docker, Inc., kterou používá oprávnění.</span><span class="sxs-lookup"><span data-stu-id="3bccc-215">The Docker whale logo is a registered trademark of Docker, Inc. Used by permission.</span></span>

<span data-ttu-id="3bccc-216">Všechny ostatní značky a loga jsou majetkem příslušných vlastníků.</span><span class="sxs-lookup"><span data-stu-id="3bccc-216">All other marks and logos are property of their respective owners.</span></span>

>[!div class="step-by-step"]
>[<span data-ttu-id="3bccc-217">Next</span><span class="sxs-lookup"><span data-stu-id="3bccc-217">Next</span></span>](container-docker-introduction/index.md)
