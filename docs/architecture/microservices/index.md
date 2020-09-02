---
title: Mikroslužby .NET. Architektura pro kontejnerizované aplikace .NET
description: Architektura mikroslužeb .NET pro kontejnerové aplikace .NET | Mikroslužby jsou modulární a nezávisle nasazujíelné služby. Kontejnery Docker (pro Linux a Windows) zjednodušují nasazení a testování tím, že propojí službu a její závislosti do jedné jednotky, která se pak spustí v izolovaném prostředí.
ms.date: 09/02/2020
ms.openlocfilehash: aea5012fee102f388827d146043e69592e14f22b
ms.sourcegitcommit: b78018c850590dfc0348301e1748b779c28604cc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "89379132"
---
# <a name="net-microservices-architecture-for-containerized-net-applications"></a><span data-ttu-id="9192a-105">Mikroslužby .NET: Architektura pro kontejnerizované aplikace .NET</span><span class="sxs-lookup"><span data-stu-id="9192a-105">.NET Microservices: Architecture for Containerized .NET Applications</span></span>

![Titulní kniha](./media/cover-small.png)

<span data-ttu-id="9192a-107">**Edice v 3.1.2** – aktualizováno na ASP.NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="9192a-107">**EDITION v3.1.2** - Updated to ASP.NET Core 3.1</span></span>

<span data-ttu-id="9192a-108">Tato příručka je Úvod k vývoji aplikací založených na mikroslužbách a jejich správě pomocí kontejnerů.</span><span class="sxs-lookup"><span data-stu-id="9192a-108">This guide is an introduction to developing microservices-based applications and managing them using containers.</span></span> <span data-ttu-id="9192a-109">Popisuje přístupy k návrhu a implementaci architektury pomocí .NET Core a kontejnerů Docker.</span><span class="sxs-lookup"><span data-stu-id="9192a-109">It discusses architectural design and implementation approaches using .NET Core and Docker containers.</span></span>

<span data-ttu-id="9192a-110">Aby bylo snazší začít, příručka se zaměřuje na odkaz na kontejner a aplikaci založenou na mikroslužbách, kterou můžete prozkoumat.</span><span class="sxs-lookup"><span data-stu-id="9192a-110">To make it easier to get started, the guide focuses on a reference containerized and microservice-based application that you can explore.</span></span> <span data-ttu-id="9192a-111">Referenční aplikace je k dispozici v úložišti GitHub [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) .</span><span class="sxs-lookup"><span data-stu-id="9192a-111">The reference application is available at the [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) GitHub repo.</span></span>

## <a name="action-links"></a><span data-ttu-id="9192a-112">Odkazy na akce</span><span class="sxs-lookup"><span data-stu-id="9192a-112">Action links</span></span>

- <span data-ttu-id="9192a-113">Tato elektronická kniha je také k dispozici ve formátu PDF (pouze v anglické verzi [).](https://aka.ms/microservicesebook)</span><span class="sxs-lookup"><span data-stu-id="9192a-113">This e-book is also available in a PDF format (English version only) [Download](https://aka.ms/microservicesebook)</span></span>

- <span data-ttu-id="9192a-114">Klonování/rozvětvení referenční aplikace [eShopOnContainers na GitHubu](https://github.com/dotnet-architecture/eShopOnContainers)</span><span class="sxs-lookup"><span data-stu-id="9192a-114">Clone/Fork the reference application [eShopOnContainers on GitHub](https://github.com/dotnet-architecture/eShopOnContainers)</span></span>

- <span data-ttu-id="9192a-115">Podívejte se na [úvodní video na Channel 9](https://aka.ms/microservices-video)</span><span class="sxs-lookup"><span data-stu-id="9192a-115">Watch the [introductory video on Channel 9](https://aka.ms/microservices-video)</span></span>

- <span data-ttu-id="9192a-116">Získejte hned informace o [architektuře mikroslužeb](https://aka.ms/MicroservicesArchitecture) .</span><span class="sxs-lookup"><span data-stu-id="9192a-116">Get to know the [Microservices Architecture](https://aka.ms/MicroservicesArchitecture) right away</span></span>

## <a name="introduction"></a><span data-ttu-id="9192a-117">Úvod</span><span class="sxs-lookup"><span data-stu-id="9192a-117">Introduction</span></span>

<span data-ttu-id="9192a-118">Podniky mají stále větší náklady na úspory nákladů, řešení problémů s nasazením a vylepšení DevOps a produkčních operací pomocí kontejnerů.</span><span class="sxs-lookup"><span data-stu-id="9192a-118">Enterprises are increasingly realizing cost savings, solving deployment problems, and improving DevOps and production operations by using containers.</span></span> <span data-ttu-id="9192a-119">Společnost Microsoft vydala inovace kontejnerů pro Windows a Linux tím, že vytváří produkty, jako je Azure Kubernetes Service a Azure Service Fabric, a spolupracuje s oborovými vedoucími, jako jsou Docker, Mesosphere a Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="9192a-119">Microsoft has been releasing container innovations for Windows and Linux by creating products like Azure Kubernetes Service and Azure Service Fabric, and by partnering with industry leaders like Docker, Mesosphere, and Kubernetes.</span></span> <span data-ttu-id="9192a-120">Tyto produkty poskytují řešení kontejnerů, která společnosti pomůžou sestavovat a nasazovat aplikace při rychlosti a škálování cloudu bez ohledu na to, jakou platformu nebo nástroje.</span><span class="sxs-lookup"><span data-stu-id="9192a-120">These products deliver container solutions that help companies build and deploy applications at cloud speed and scale, whatever their choice of platform or tools.</span></span>

<span data-ttu-id="9192a-121">Docker se stává jako de facto standard v odvětví kontejneru, který je podporovaný nejvýznamnějšími dodavateli v ekosystémech Windows a Linux.</span><span class="sxs-lookup"><span data-stu-id="9192a-121">Docker is becoming the de facto standard in the container industry, supported by the most significant vendors in the Windows and Linux ecosystems.</span></span> <span data-ttu-id="9192a-122">(Microsoft je jedním z hlavních dodavatelů cloudů, kteří podporují Docker.) V budoucnu se Docker bude pravděpodobně všudypřítomný do libovolného datacentra v cloudu nebo v místním prostředí.</span><span class="sxs-lookup"><span data-stu-id="9192a-122">(Microsoft is one of the main cloud vendors supporting Docker.) In the future, Docker will probably be ubiquitous in any datacenter in the cloud or on-premises.</span></span>

<span data-ttu-id="9192a-123">Kromě toho architektura [mikroslužeb](https://martinfowler.com/articles/microservices.html) se vychází jako důležitý přístup pro distribuované klíčové aplikace.</span><span class="sxs-lookup"><span data-stu-id="9192a-123">In addition, the [microservices](https://martinfowler.com/articles/microservices.html) architecture is emerging as an important approach for distributed mission-critical applications.</span></span> <span data-ttu-id="9192a-124">V architektuře založené na mikroslužbách je aplikace postavená na kolekci služeb, které se dají vyvíjet, testovat, nasazovat a samostatně nakládat s verzemi.</span><span class="sxs-lookup"><span data-stu-id="9192a-124">In a microservice-based architecture, the application is built on a collection of services that can be developed, tested, deployed, and versioned independently.</span></span>

## <a name="about-this-guide"></a><span data-ttu-id="9192a-125">O této příručce</span><span class="sxs-lookup"><span data-stu-id="9192a-125">About this guide</span></span>

<span data-ttu-id="9192a-126">Tato příručka je Úvod k vývoji aplikací založených na mikroslužbách a jejich správě pomocí kontejnerů.</span><span class="sxs-lookup"><span data-stu-id="9192a-126">This guide is an introduction to developing microservices-based applications and managing them using containers.</span></span> <span data-ttu-id="9192a-127">Popisuje přístupy k návrhu a implementaci architektury pomocí .NET Core a kontejnerů Docker.</span><span class="sxs-lookup"><span data-stu-id="9192a-127">It discusses architectural design and implementation approaches using .NET Core and Docker containers.</span></span> <span data-ttu-id="9192a-128">Aby bylo snazší začít s kontejnery a mikroslužbami, tato příručka se zaměřuje na odkaz na kontejner a aplikaci založenou na mikroslužbách, kterou můžete prozkoumat.</span><span class="sxs-lookup"><span data-stu-id="9192a-128">To make it easier to get started with containers and microservices, the guide focuses on a reference containerized and microservice-based application that you can explore.</span></span> <span data-ttu-id="9192a-129">Ukázková aplikace je k dispozici v úložišti GitHub [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) .</span><span class="sxs-lookup"><span data-stu-id="9192a-129">The sample application is available at the [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) GitHub repo.</span></span>

<span data-ttu-id="9192a-130">Tato příručka poskytuje pokyny pro základní vývoj a architekturu primárně na úrovni vývojového prostředí se zaměřením na dvě technologie: Docker a .NET Core.</span><span class="sxs-lookup"><span data-stu-id="9192a-130">This guide provides foundational development and architectural guidance primarily at a development environment level with a focus on two technologies: Docker and .NET Core.</span></span> <span data-ttu-id="9192a-131">Naším záměrem je přečíst si tuto příručku při zvažování návrhu vaší aplikace bez zaměření na infrastrukturu (Cloud nebo místní) vašeho provozního prostředí.</span><span class="sxs-lookup"><span data-stu-id="9192a-131">Our intention is that you read this guide when thinking about your application design without focusing on the infrastructure (cloud or on-premises) of your production environment.</span></span> <span data-ttu-id="9192a-132">Rozhodnutí o vaší infrastruktuře budete provádět později při vytváření aplikací připravených pro produkční prostředí.</span><span class="sxs-lookup"><span data-stu-id="9192a-132">You will make decisions about your infrastructure later, when you create your production-ready applications.</span></span> <span data-ttu-id="9192a-133">Proto je tato příručka zamýšlená jako infrastruktura nezávislá a další vývojové prostředí.</span><span class="sxs-lookup"><span data-stu-id="9192a-133">Therefore, this guide is intended to be infrastructure agnostic and more development-environment-centric.</span></span>

<span data-ttu-id="9192a-134">Po prostudování tohoto průvodce by vám v dalším kroku pomohlo zjistit mikroslužby připravené k výrobě na Microsoft Azure.</span><span class="sxs-lookup"><span data-stu-id="9192a-134">After you have studied this guide, your next step would be to learn about production-ready microservices on Microsoft Azure.</span></span>

## <a name="version"></a><span data-ttu-id="9192a-135">Verze</span><span class="sxs-lookup"><span data-stu-id="9192a-135">Version</span></span>

<span data-ttu-id="9192a-136">Tato příručka byla revidována tak, aby kryla verzi **.NET core 3,1** spolu s mnoha dalšími aktualizacemi, které se týkají stejných "Wave" technologií (tj. Azure a dalších technologií třetích stran), které se shodují v čase s verzí .net Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="9192a-136">This guide has been revised to cover **.NET Core 3.1** version along with many additional updates related to the same “wave” of technologies (that is, Azure and additional third-party technologies) coinciding in time with the .NET Core 3.1 release.</span></span> <span data-ttu-id="9192a-137">To je důvod, proč se verze knihy aktualizovala také na verzi **3,1**.</span><span class="sxs-lookup"><span data-stu-id="9192a-137">That’s why the book version has also been updated to version **3.1**.</span></span>

## <a name="what-this-guide-does-not-cover"></a><span data-ttu-id="9192a-138">Co tato příručka nepokrývá</span><span class="sxs-lookup"><span data-stu-id="9192a-138">What this guide does not cover</span></span>

<span data-ttu-id="9192a-139">Tato příručka se nezaměřuje na životní cyklus aplikací, DevOps, kanály CI/CD ani týmovou práci.</span><span class="sxs-lookup"><span data-stu-id="9192a-139">This guide does not focus on the application lifecycle, DevOps, CI/CD pipelines, or team work.</span></span> <span data-ttu-id="9192a-140">[Doplněný životní cyklus aplikace Docker v kontejneru s využitím platformy a nástrojů Microsoftu se](https://aka.ms/dockerlifecycleebook) zaměřuje na tento předmět.</span><span class="sxs-lookup"><span data-stu-id="9192a-140">The complementary guide [Containerized Docker Application Lifecycle with Microsoft Platform and Tools](https://aka.ms/dockerlifecycleebook) focuses on that subject.</span></span> <span data-ttu-id="9192a-141">Aktuální příručka také neposkytuje podrobnosti o implementaci infrastruktury Azure, jako jsou informace o konkrétních orchestrcích.</span><span class="sxs-lookup"><span data-stu-id="9192a-141">The current guide also does not provide implementation details on Azure infrastructure, such as information on specific orchestrators.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="9192a-142">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="9192a-142">Additional resources</span></span>

- <span data-ttu-id="9192a-143">**Kontejnerové životní cykly aplikace Docker s platformou a nástroji Microsoftu** (elektronická kniha ke stažení)</span><span class="sxs-lookup"><span data-stu-id="9192a-143">**Containerized Docker Application Lifecycle with Microsoft Platform and Tools** (downloadable e-book)</span></span>  
    <https://aka.ms/dockerlifecycleebook>

## <a name="who-should-use-this-guide"></a><span data-ttu-id="9192a-144">Kdo by měl používat tuto příručku</span><span class="sxs-lookup"><span data-stu-id="9192a-144">Who should use this guide</span></span>

<span data-ttu-id="9192a-145">Tuto příručku jsme napsali pro vývojáře a architekty řešení, kteří jsou noví pro vývoj aplikací založených na Docker a na architekturu založenou na mikroslužbách.</span><span class="sxs-lookup"><span data-stu-id="9192a-145">We wrote this guide for developers and solution architects who are new to Docker-based application development and to microservices-based architecture.</span></span> <span data-ttu-id="9192a-146">Tato příručka je určena pro vás, pokud se chcete dozvědět, jak architekt, navrhovat a implementovat aplikace pro zkušební použití pomocí vývojových technologií Microsoftu (se speciálním zaměřením na .NET Core) a s kontejnery Docker.</span><span class="sxs-lookup"><span data-stu-id="9192a-146">This guide is for you if you want to learn how to architect, design, and implement proof-of-concept applications with Microsoft development technologies (with special focus on .NET Core) and with Docker containers.</span></span>

<span data-ttu-id="9192a-147">Tento průvodce najdete také v případě, že jste Tvůrce technického rozhodnutí, jako je například podnikový architekt, který vyžaduje architekturu a technologický přehled, než se rozhodnete, jaký přístup vybrat pro nové a moderní distribuované aplikace.</span><span class="sxs-lookup"><span data-stu-id="9192a-147">You will also find this guide useful if you are a technical decision maker, such as an enterprise architect, who wants an architecture and technology overview before you decide on what approach to select for new and modern distributed applications.</span></span>

### <a name="how-to-use-this-guide"></a><span data-ttu-id="9192a-148">Jak používat tohoto průvodce</span><span class="sxs-lookup"><span data-stu-id="9192a-148">How to use this guide</span></span>

<span data-ttu-id="9192a-149">První část této příručky zavádí kontejnery Docker, popisuje, jak zvolit mezi .NET Core a .NET Framework jako vývojovou architekturou a poskytuje přehled mikroslužeb.</span><span class="sxs-lookup"><span data-stu-id="9192a-149">The first part of this guide introduces Docker containers, discusses how to choose between .NET Core and the .NET Framework as a development framework, and provides an overview of microservices.</span></span> <span data-ttu-id="9192a-150">Tento obsah je určen pro architekty a pracovníky technického rozhodování, kteří chtějí přehled, ale nemusí se soustředit na podrobnosti implementace kódu.</span><span class="sxs-lookup"><span data-stu-id="9192a-150">This content is for architects and technical decision makers who want an overview but don't need to focus on code implementation details.</span></span>

<span data-ttu-id="9192a-151">Druhá část příručky začíná [procesem vývoje pro aplikace založené na Docker](./docker-application-development-process/index.md) .</span><span class="sxs-lookup"><span data-stu-id="9192a-151">The second part of the guide starts with the [Development process for Docker based applications](./docker-application-development-process/index.md) section.</span></span> <span data-ttu-id="9192a-152">Zaměřuje se na vývojové a mikroslužby pro implementaci aplikací pomocí .NET Core a Docker.</span><span class="sxs-lookup"><span data-stu-id="9192a-152">It focuses on the development and microservice patterns for implementing applications using .NET Core and Docker.</span></span> <span data-ttu-id="9192a-153">Tato část bude mít největší zájem na vývojáře a architekty, kteří se chtějí zaměřit na kód a podrobnosti o vzorech a implementaci.</span><span class="sxs-lookup"><span data-stu-id="9192a-153">This section will be of most interest to developers and architects who want to focus on code and on patterns and implementation details.</span></span>

## <a name="related-microservice-and-container-based-reference-application-eshoponcontainers"></a><span data-ttu-id="9192a-154">Související referenční aplikace založené na mikroslužbách a kontejneru: eShopOnContainers</span><span class="sxs-lookup"><span data-stu-id="9192a-154">Related microservice and container-based reference application: eShopOnContainers</span></span>

<span data-ttu-id="9192a-155">Aplikace eShopOnContainers je open source referenční aplikace pro .NET Core a mikroslužby, které jsou navržené tak, aby se nasadily pomocí kontejnerů Docker.</span><span class="sxs-lookup"><span data-stu-id="9192a-155">The eShopOnContainers application is an open-source reference app for .NET Core and microservices that is designed to be deployed using Docker containers.</span></span> <span data-ttu-id="9192a-156">Aplikace se skládá z několika subsystémů, včetně několika front-Store uživatelského rozhraní (aplikace webové MVC, webové zabezpečené ověřování a nativní mobilní aplikace).</span><span class="sxs-lookup"><span data-stu-id="9192a-156">The application consists of multiple subsystems, including several e-store UI front-ends (a Web MVC app, a Web SPA, and a native mobile app).</span></span> <span data-ttu-id="9192a-157">Zahrnuje také back-endové mikroslužby a kontejnery pro všechny požadované operace na straně serveru.</span><span class="sxs-lookup"><span data-stu-id="9192a-157">It also includes the back-end microservices and containers for all required server-side operations.</span></span>

<span data-ttu-id="9192a-158">Účelem aplikace je předvedení struktur architektury.</span><span class="sxs-lookup"><span data-stu-id="9192a-158">The purpose of the application is to showcase architectural patterns.</span></span> <span data-ttu-id="9192a-159">Nejedná se **o šablonu připravenou pro produkční prostředí** pro spouštění reálných aplikací.</span><span class="sxs-lookup"><span data-stu-id="9192a-159">**IT IS NOT A PRODUCTION-READY TEMPLATE** to start real-world applications.</span></span> <span data-ttu-id="9192a-160">Ve skutečnosti je aplikace v trvalé verzi beta verze, protože se také používá k otestování nových potenciálně zajímavých technologií, které se zobrazují.</span><span class="sxs-lookup"><span data-stu-id="9192a-160">In fact, the application is in a permanent beta state, as it's also used to test new potentially interesting technologies as they show up.</span></span>

## <a name="send-us-your-feedback"></a><span data-ttu-id="9192a-161">Vyjádřete svůj názor.</span><span class="sxs-lookup"><span data-stu-id="9192a-161">Send us your feedback!</span></span>

<span data-ttu-id="9192a-162">Tento průvodce jsme napsali a pomohli vám pochopit architekturu kontejnerových aplikací a mikroslužeb v .NET.</span><span class="sxs-lookup"><span data-stu-id="9192a-162">We wrote this guide to help you understand the architecture of containerized applications and microservices in .NET.</span></span> <span data-ttu-id="9192a-163">Bude vyvíjena příručka a související referenční aplikace, takže jsme Vítejte na vašem názoru.</span><span class="sxs-lookup"><span data-stu-id="9192a-163">The guide and related reference application will be evolving, so we welcome your feedback!</span></span> <span data-ttu-id="9192a-164">Pokud máte komentáře o tom, jak tento průvodce můžete zlepšit, pošlete nám svůj názor na <https://aka.ms/ebookfeedback> .</span><span class="sxs-lookup"><span data-stu-id="9192a-164">If you have comments about how this guide can be improved, submit feedback at <https://aka.ms/ebookfeedback>.</span></span>

## <a name="credits"></a><span data-ttu-id="9192a-165">Kredity</span><span class="sxs-lookup"><span data-stu-id="9192a-165">Credits</span></span>

<span data-ttu-id="9192a-166">Spoluautoři:</span><span class="sxs-lookup"><span data-stu-id="9192a-166">Co-Authors:</span></span>

> <span data-ttu-id="9192a-167">**Cesar de la Torre**, SR. PM, produktový tým .NET, Microsoft Corp.</span><span class="sxs-lookup"><span data-stu-id="9192a-167">**Cesar de la Torre**, Sr. PM, .NET product team, Microsoft Corp.</span></span>
>
> <span data-ttu-id="9192a-168">**Bill Wagner**, SR. Content Developer, C + E, Microsoft Corp.</span><span class="sxs-lookup"><span data-stu-id="9192a-168">**Bill Wagner**, Sr. Content Developer, C+E, Microsoft Corp.</span></span>
>
> <span data-ttu-id="9192a-169">**Jan Rousos**, hlavní softwarový inženýr, DevDiv Cat tým, Microsoft</span><span class="sxs-lookup"><span data-stu-id="9192a-169">**Mike Rousos**, Principal Software Engineer, DevDiv CAT team, Microsoft</span></span>

<span data-ttu-id="9192a-170">Editory</span><span class="sxs-lookup"><span data-stu-id="9192a-170">Editors:</span></span>

> <span data-ttu-id="9192a-171">**Mike Pope**</span><span class="sxs-lookup"><span data-stu-id="9192a-171">**Mike Pope**</span></span>
>
> <span data-ttu-id="9192a-172">**Steve Hoag**</span><span class="sxs-lookup"><span data-stu-id="9192a-172">**Steve Hoag**</span></span>

<span data-ttu-id="9192a-173">Účastníci a kontroloři:</span><span class="sxs-lookup"><span data-stu-id="9192a-173">Participants and reviewers:</span></span>

> <span data-ttu-id="9192a-174">**Jeffrey Richter**, partnerský software eng, tým Azure, Microsoft</span><span class="sxs-lookup"><span data-stu-id="9192a-174">**Jeffrey Richter**, Partner Software Eng, Azure team, Microsoft</span></span>
>
> <span data-ttu-id="9192a-175">**Jimmy Bogard**, hlavní architekt na headspring</span><span class="sxs-lookup"><span data-stu-id="9192a-175">**Jimmy Bogard**, Chief Architect at Headspring</span></span>
>
> <span data-ttu-id="9192a-176">**UDI Dahan**, zakladatel & výkonný ředitel, konkrétní software</span><span class="sxs-lookup"><span data-stu-id="9192a-176">**Udi Dahan**, Founder & CEO, Particular Software</span></span>
>
> <span data-ttu-id="9192a-177">**Jimmy Nilsson**, zakladatel a generální ředitel pro Factor10</span><span class="sxs-lookup"><span data-stu-id="9192a-177">**Jimmy Nilsson**, Co-founder and CEO of Factor10</span></span>
>
> <span data-ttu-id="9192a-178">**Glenn Condron**, SR. Program Manager, ASP.NET tým</span><span class="sxs-lookup"><span data-stu-id="9192a-178">**Glenn Condron**, Sr. Program Manager, ASP.NET team</span></span>
>
> <span data-ttu-id="9192a-179">**Mark Fussell**, hlavní vedoucí pro odpoledne, Azure Service Fabric Team, Microsoft</span><span class="sxs-lookup"><span data-stu-id="9192a-179">**Mark Fussell**, Principal PM Lead, Azure Service Fabric team, Microsoft</span></span>
>
> <span data-ttu-id="9192a-180">**Diegu Vega**, vedoucí pracovník, Entity Framework tým, Microsoft</span><span class="sxs-lookup"><span data-stu-id="9192a-180">**Diego Vega**, PM Lead, Entity Framework team, Microsoft</span></span>
>
> <span data-ttu-id="9192a-181">**Barryho Dorrans**, správce programu SR. Security</span><span class="sxs-lookup"><span data-stu-id="9192a-181">**Barry Dorrans**, Sr. Security Program Manager</span></span>
>
> <span data-ttu-id="9192a-182">**Rowan Miller**, SR. Program Manager, Microsoft</span><span class="sxs-lookup"><span data-stu-id="9192a-182">**Rowan Miller**, Sr. Program Manager, Microsoft</span></span>
>
> <span data-ttu-id="9192a-183">**Ankit Asthana**, hlavní správce odpoledne, tým .NET, Microsoft</span><span class="sxs-lookup"><span data-stu-id="9192a-183">**Ankit Asthana**, Principal PM Manager, .NET team, Microsoft</span></span>
>
> <span data-ttu-id="9192a-184">**Scott Hunterem**, ředitel pro partnery, tým .NET, Microsoft</span><span class="sxs-lookup"><span data-stu-id="9192a-184">**Scott Hunter**, Partner Director PM, .NET team, Microsoft</span></span>
>
> <span data-ttu-id="9192a-185">**Nish Anil**, SR. Program Manager, .NET Team, Microsoft</span><span class="sxs-lookup"><span data-stu-id="9192a-185">**Nish Anil**, Sr. Program Manager, .NET team, Microsoft</span></span>
>
> <span data-ttu-id="9192a-186">**Dylan Reisenberger**, architekt a vývojářského vedoucího v Polly</span><span class="sxs-lookup"><span data-stu-id="9192a-186">**Dylan Reisenberger**, Architect and Dev Lead at Polly</span></span>
>
> <span data-ttu-id="9192a-187">**Steve "ardalis" Smith** -Software Architect a Trainer- [Ardalis.com](https://ardalis.com)</span><span class="sxs-lookup"><span data-stu-id="9192a-187">**Steve "ardalis" Smith** - Software Architect and Trainer - [Ardalis.com](https://ardalis.com)</span></span>
>
> <span data-ttu-id="9192a-188">**Ian Cooper**, architekt kódu na jasnější úrovni</span><span class="sxs-lookup"><span data-stu-id="9192a-188">**Ian Cooper**, Coding Architect at Brighter</span></span>
>
> <span data-ttu-id="9192a-189">**Unai Zorrilla**, architekt a vývojářské olovo v jednoduchých konceptech</span><span class="sxs-lookup"><span data-stu-id="9192a-189">**Unai Zorrilla**, Architect and Dev Lead at Plain Concepts</span></span>
>
> <span data-ttu-id="9192a-190">**Eduard Tomas**, vedoucí pro vývoj na jednoduchých konceptech</span><span class="sxs-lookup"><span data-stu-id="9192a-190">**Eduard Tomas**, Dev Lead at Plain Concepts</span></span>
>
> <span data-ttu-id="9192a-191">**Ramon Tomas**, Developer na jednoduchých konceptech</span><span class="sxs-lookup"><span data-stu-id="9192a-191">**Ramon Tomas**, Developer at Plain Concepts</span></span>
>
> <span data-ttu-id="9192a-192">**David Sanz**, Developer na jednoduchých konceptech</span><span class="sxs-lookup"><span data-stu-id="9192a-192">**David Sanz**, Developer at Plain Concepts</span></span>
>
> <span data-ttu-id="9192a-193">**Javier Valero**, vedoucí pracovník v Grupo solutio</span><span class="sxs-lookup"><span data-stu-id="9192a-193">**Javier Valero**, Chief Operating Officer at Grupo Solutio</span></span>
>
> <span data-ttu-id="9192a-194">**Pierre-Millet**, SR. konzultant, Microsoft</span><span class="sxs-lookup"><span data-stu-id="9192a-194">**Pierre Millet**, Sr. Consultant, Microsoft</span></span>
>
> <span data-ttu-id="9192a-195">**Michael Friis**, produktový manažer, Docker Inc</span><span class="sxs-lookup"><span data-stu-id="9192a-195">**Michael Friis**, Product Manager, Docker Inc</span></span>
>
> <span data-ttu-id="9192a-196">**Charles Lowell**, software inženýr, vs Cat tým, Microsoft</span><span class="sxs-lookup"><span data-stu-id="9192a-196">**Charles Lowell**, Software Engineer, VS CAT team, Microsoft</span></span>
>
> <span data-ttu-id="9192a-197">**Miguel Veloso**, inženýr pro vývoj softwaru v jednoduchých konceptech</span><span class="sxs-lookup"><span data-stu-id="9192a-197">**Miguel Veloso**, Software Development Engineer at Plain Concepts</span></span>
>
> <span data-ttu-id="9192a-198">**Sumit Ghosh**, hlavní konzultant na Neudesic</span><span class="sxs-lookup"><span data-stu-id="9192a-198">**Sumit Ghosh**, Principal Consultant at Neudesic</span></span>

## <a name="copyright"></a><span data-ttu-id="9192a-199">Copyright</span><span class="sxs-lookup"><span data-stu-id="9192a-199">Copyright</span></span>

<span data-ttu-id="9192a-200">PUBLIKOVAL(A)</span><span class="sxs-lookup"><span data-stu-id="9192a-200">PUBLISHED BY</span></span>

<span data-ttu-id="9192a-201">Microsoft Developer divize, .NET a Visual Studio Product teams</span><span class="sxs-lookup"><span data-stu-id="9192a-201">Microsoft Developer Division, .NET and Visual Studio product teams</span></span>

<span data-ttu-id="9192a-202">Divize společnosti Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="9192a-202">A division of Microsoft Corporation</span></span>

<span data-ttu-id="9192a-203">One Microsoft Way</span><span class="sxs-lookup"><span data-stu-id="9192a-203">One Microsoft Way</span></span>

<span data-ttu-id="9192a-204">Redmond, Washington 98052-6399</span><span class="sxs-lookup"><span data-stu-id="9192a-204">Redmond, Washington 98052-6399</span></span>

<span data-ttu-id="9192a-205">Copyright © 2020 od společnosti Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="9192a-205">Copyright © 2020 by Microsoft Corporation</span></span>

<span data-ttu-id="9192a-206">All rights reserved.</span><span class="sxs-lookup"><span data-stu-id="9192a-206">All rights reserved.</span></span> <span data-ttu-id="9192a-207">Žádná část obsahu této knihy se nedá reprodukovat ani přenést v jakékoli formě nebo jakýmkoli způsobem bez písemného svolení vydavatele.</span><span class="sxs-lookup"><span data-stu-id="9192a-207">No part of the contents of this book may be reproduced or transmitted in any form or by any means without the written permission of the publisher.</span></span>

<span data-ttu-id="9192a-208">Tato kniha je k dispozici "tak jak jsou" a vyjadřuje zobrazení a stanoviska autora.</span><span class="sxs-lookup"><span data-stu-id="9192a-208">This book is provided "as-is" and expresses the author's views and opinions.</span></span> <span data-ttu-id="9192a-209">Zobrazení, názory a informace vyjádřené v této knize, včetně adres URL a dalších odkazů na internetové weby, se mohou změnit bez předchozího upozornění.</span><span class="sxs-lookup"><span data-stu-id="9192a-209">The views, opinions and information expressed in this book, including URL and other Internet website references, may change without notice.</span></span>

<span data-ttu-id="9192a-210">Některé zde uvedené příklady slouží pouze k znázornění a jsou smyšlené.</span><span class="sxs-lookup"><span data-stu-id="9192a-210">Some examples depicted herein are provided for illustration only and are fictitious.</span></span> <span data-ttu-id="9192a-211">Neměli byste z nich vyvozovat žádné skutečné vztahy či spojení.</span><span class="sxs-lookup"><span data-stu-id="9192a-211">No real association or connection is intended or should be inferred.</span></span>

<span data-ttu-id="9192a-212">Microsoft a ochranné známky uvedené na <https://www.microsoft.com> webové stránce ochranné známky jsou ochranné známky skupiny společností Microsoft.</span><span class="sxs-lookup"><span data-stu-id="9192a-212">Microsoft and the trademarks listed at <https://www.microsoft.com> on the "Trademarks" webpage are trademarks of the Microsoft group of companies.</span></span>

<span data-ttu-id="9192a-213">Mac a macOS jsou ochranné známky společnosti Apple Inc.</span><span class="sxs-lookup"><span data-stu-id="9192a-213">Mac and macOS are trademarks of Apple Inc.</span></span>

<span data-ttu-id="9192a-214">Logo Docker Whale je registrovaná ochranná známka společnosti Docker, Inc., kterou používá oprávnění.</span><span class="sxs-lookup"><span data-stu-id="9192a-214">The Docker whale logo is a registered trademark of Docker, Inc. Used by permission.</span></span>

<span data-ttu-id="9192a-215">Všechny ostatní značky a loga jsou majetkem příslušných vlastníků.</span><span class="sxs-lookup"><span data-stu-id="9192a-215">All other marks and logos are property of their respective owners.</span></span>

>[!div class="step-by-step"]
>[<span data-ttu-id="9192a-216">Další</span><span class="sxs-lookup"><span data-stu-id="9192a-216">Next</span></span>](container-docker-introduction/index.md)
