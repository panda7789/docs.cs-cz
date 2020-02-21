---
title: Mikroslužby .NET. Architektura pro kontejnerizované aplikace .NET
description: Architektura mikroslužeb .NET pro kontejnerové aplikace .NET | Mikroslužby jsou modulární a nezávisle nasazujíelné služby. Kontejnery Docker (pro Linux a Windows) zjednodušují nasazení a testování tím, že propojí službu a její závislosti do jedné jednotky, která se pak spustí v izolovaném prostředí.
ms.date: 01/30/2020
ms.openlocfilehash: 1337fe56e78e03a85627737bd52a089fd946b842
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/21/2020
ms.locfileid: "77543531"
---
# <a name="net-microservices-architecture-for-containerized-net-applications"></a><span data-ttu-id="343c9-105">Mikroslužby .NET: architektura pro kontejnerové aplikace .NET</span><span class="sxs-lookup"><span data-stu-id="343c9-105">.NET Microservices: Architecture for Containerized .NET Applications</span></span>

![Titulní kniha](./media/cover-small.png)

<span data-ttu-id="343c9-107">**Edice verze 3.1** – aktualizace na ASP.NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="343c9-107">**EDITION v3.1** - Updated to ASP.NET Core 3.1</span></span>

<span data-ttu-id="343c9-108">Tato příručka je Úvod k vývoji aplikací založených na mikroslužbách a jejich správě pomocí kontejnerů.</span><span class="sxs-lookup"><span data-stu-id="343c9-108">This guide is an introduction to developing microservices-based applications and managing them using containers.</span></span> <span data-ttu-id="343c9-109">Popisuje přístupy k návrhu a implementaci architektury pomocí .NET Core a kontejnerů Docker.</span><span class="sxs-lookup"><span data-stu-id="343c9-109">It discusses architectural design and implementation approaches using .NET Core and Docker containers.</span></span>

<span data-ttu-id="343c9-110">Aby bylo snazší začít, příručka se zaměřuje na odkaz na kontejner a aplikaci založenou na mikroslužbách, kterou můžete prozkoumat.</span><span class="sxs-lookup"><span data-stu-id="343c9-110">To make it easier to get started, the guide focuses on a reference containerized and microservice-based application that you can explore.</span></span> <span data-ttu-id="343c9-111">Referenční aplikace je k dispozici v úložišti GitHub [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) .</span><span class="sxs-lookup"><span data-stu-id="343c9-111">The reference application is available at the [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) GitHub repo.</span></span>

## <a name="action-links"></a><span data-ttu-id="343c9-112">Odkazy na akce</span><span class="sxs-lookup"><span data-stu-id="343c9-112">Action links</span></span>

- <span data-ttu-id="343c9-113">Tato elektronická kniha je také k dispozici ve formátu PDF (pouze v anglické verzi [).](https://aka.ms/microservicesebook)</span><span class="sxs-lookup"><span data-stu-id="343c9-113">This e-book is also available in a PDF format (English version only) [Download](https://aka.ms/microservicesebook)</span></span>

- <span data-ttu-id="343c9-114">Klonování/rozvětvení referenční aplikace [eShopOnContainers na GitHubu](https://github.com/dotnet-architecture/eShopOnContainers)</span><span class="sxs-lookup"><span data-stu-id="343c9-114">Clone/Fork the reference application [eShopOnContainers on GitHub](https://github.com/dotnet-architecture/eShopOnContainers)</span></span>

- <span data-ttu-id="343c9-115">Podívejte se na [úvodní video na Channel 9](https://aka.ms/microservices-video)</span><span class="sxs-lookup"><span data-stu-id="343c9-115">Watch the [introductory video on Channel 9](https://aka.ms/microservices-video)</span></span>

- <span data-ttu-id="343c9-116">Získejte hned informace o [architektuře mikroslužeb](https://aka.ms/MicroservicesArchitecture) .</span><span class="sxs-lookup"><span data-stu-id="343c9-116">Get to know the [Microservices Architecture](https://aka.ms/MicroservicesArchitecture) right away</span></span>

## <a name="introduction"></a><span data-ttu-id="343c9-117">Úvod</span><span class="sxs-lookup"><span data-stu-id="343c9-117">Introduction</span></span>

<span data-ttu-id="343c9-118">Podniky mají stále větší náklady na úspory nákladů, řešení problémů s nasazením a vylepšení DevOps a produkčních operací pomocí kontejnerů.</span><span class="sxs-lookup"><span data-stu-id="343c9-118">Enterprises are increasingly realizing cost savings, solving deployment problems, and improving DevOps and production operations by using containers.</span></span> <span data-ttu-id="343c9-119">Společnost Microsoft vydala inovace kontejnerů pro Windows a Linux tím, že vytváří produkty, jako je Azure Kubernetes Service a Azure Service Fabric, a spolupracuje s oborovými vedoucími, jako jsou Docker, Mesosphere a Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="343c9-119">Microsoft has been releasing container innovations for Windows and Linux by creating products like Azure Kubernetes Service and Azure Service Fabric, and by partnering with industry leaders like Docker, Mesosphere, and Kubernetes.</span></span> <span data-ttu-id="343c9-120">Tyto produkty poskytují řešení kontejnerů, která společnosti pomůžou sestavovat a nasazovat aplikace při rychlosti a škálování cloudu bez ohledu na to, jakou platformu nebo nástroje.</span><span class="sxs-lookup"><span data-stu-id="343c9-120">These products deliver container solutions that help companies build and deploy applications at cloud speed and scale, whatever their choice of platform or tools.</span></span>

<span data-ttu-id="343c9-121">Docker se stává jako de facto standard v odvětví kontejneru, který je podporovaný nejvýznamnějšími dodavateli v ekosystémech Windows a Linux.</span><span class="sxs-lookup"><span data-stu-id="343c9-121">Docker is becoming the de facto standard in the container industry, supported by the most significant vendors in the Windows and Linux ecosystems.</span></span> <span data-ttu-id="343c9-122">(Microsoft je jedním z hlavních dodavatelů cloudů, kteří podporují Docker.) V budoucnu se Docker bude pravděpodobně všudypřítomný do libovolného datacentra v cloudu nebo v místním prostředí.</span><span class="sxs-lookup"><span data-stu-id="343c9-122">(Microsoft is one of the main cloud vendors supporting Docker.) In the future, Docker will probably be ubiquitous in any datacenter in the cloud or on-premises.</span></span>

<span data-ttu-id="343c9-123">Kromě toho architektura [mikroslužeb](https://martinfowler.com/articles/microservices.html) se vychází jako důležitý přístup pro distribuované klíčové aplikace.</span><span class="sxs-lookup"><span data-stu-id="343c9-123">In addition, the [microservices](https://martinfowler.com/articles/microservices.html) architecture is emerging as an important approach for distributed mission-critical applications.</span></span> <span data-ttu-id="343c9-124">V architektuře založené na mikroslužbách je aplikace postavená na kolekci služeb, které se dají vyvíjet, testovat, nasazovat a samostatně nakládat s verzemi.</span><span class="sxs-lookup"><span data-stu-id="343c9-124">In a microservice-based architecture, the application is built on a collection of services that can be developed, tested, deployed, and versioned independently.</span></span>

## <a name="about-this-guide"></a><span data-ttu-id="343c9-125">O této příručce</span><span class="sxs-lookup"><span data-stu-id="343c9-125">About this guide</span></span>

<span data-ttu-id="343c9-126">Tato příručka je Úvod k vývoji aplikací založených na mikroslužbách a jejich správě pomocí kontejnerů.</span><span class="sxs-lookup"><span data-stu-id="343c9-126">This guide is an introduction to developing microservices-based applications and managing them using containers.</span></span> <span data-ttu-id="343c9-127">Popisuje přístupy k návrhu a implementaci architektury pomocí .NET Core a kontejnerů Docker.</span><span class="sxs-lookup"><span data-stu-id="343c9-127">It discusses architectural design and implementation approaches using .NET Core and Docker containers.</span></span> <span data-ttu-id="343c9-128">Aby bylo snazší začít s kontejnery a mikroslužbami, tato příručka se zaměřuje na odkaz na kontejner a aplikaci založenou na mikroslužbách, kterou můžete prozkoumat.</span><span class="sxs-lookup"><span data-stu-id="343c9-128">To make it easier to get started with containers and microservices, the guide focuses on a reference containerized and microservice-based application that you can explore.</span></span> <span data-ttu-id="343c9-129">Ukázková aplikace je k dispozici v úložišti GitHub [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) .</span><span class="sxs-lookup"><span data-stu-id="343c9-129">The sample application is available at the [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) GitHub repo.</span></span>

<span data-ttu-id="343c9-130">Tato příručka poskytuje pokyny pro základní vývoj a architekturu primárně na úrovni vývojového prostředí se zaměřením na dvě technologie: Docker a .NET Core.</span><span class="sxs-lookup"><span data-stu-id="343c9-130">This guide provides foundational development and architectural guidance primarily at a development environment level with a focus on two technologies: Docker and .NET Core.</span></span> <span data-ttu-id="343c9-131">Naším záměrem je přečíst si tuto příručku při zvažování návrhu vaší aplikace bez zaměření na infrastrukturu (Cloud nebo místní) vašeho provozního prostředí.</span><span class="sxs-lookup"><span data-stu-id="343c9-131">Our intention is that you read this guide when thinking about your application design without focusing on the infrastructure (cloud or on-premises) of your production environment.</span></span> <span data-ttu-id="343c9-132">Rozhodnutí o vaší infrastruktuře budete provádět později při vytváření aplikací připravených pro produkční prostředí.</span><span class="sxs-lookup"><span data-stu-id="343c9-132">You will make decisions about your infrastructure later, when you create your production-ready applications.</span></span> <span data-ttu-id="343c9-133">Proto je tato příručka zamýšlená jako infrastruktura nezávislá a další vývojové prostředí.</span><span class="sxs-lookup"><span data-stu-id="343c9-133">Therefore, this guide is intended to be infrastructure agnostic and more development-environment-centric.</span></span>

<span data-ttu-id="343c9-134">Po prostudování tohoto průvodce by vám v dalším kroku pomohlo zjistit mikroslužby připravené k výrobě na Microsoft Azure.</span><span class="sxs-lookup"><span data-stu-id="343c9-134">After you have studied this guide, your next step would be to learn about production-ready microservices on Microsoft Azure.</span></span>

## <a name="version"></a><span data-ttu-id="343c9-135">Verze</span><span class="sxs-lookup"><span data-stu-id="343c9-135">Version</span></span>

<span data-ttu-id="343c9-136">Tato příručka byla revidována tak, aby kryla verzi **.NET core 3,1** spolu s mnoha dalšími aktualizacemi, které se týkají stejných "Wave" technologií (tj. Azure a dalších technologií třetích stran), které se shodují v čase s verzí .net Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="343c9-136">This guide has been revised to cover **.NET Core 3.1** version along with many additional updates related to the same “wave” of technologies (that is, Azure and additional third-party technologies) coinciding in time with the .NET Core 3.1 release.</span></span> <span data-ttu-id="343c9-137">To je důvod, proč se verze knihy aktualizovala také na verzi **3,1**.</span><span class="sxs-lookup"><span data-stu-id="343c9-137">That’s why the book version has also been updated to version **3.1**.</span></span>

## <a name="what-this-guide-does-not-cover"></a><span data-ttu-id="343c9-138">Co tato příručka nepokrývá</span><span class="sxs-lookup"><span data-stu-id="343c9-138">What this guide does not cover</span></span>

<span data-ttu-id="343c9-139">Tato příručka se nezaměřuje na životní cyklus aplikací, DevOps, kanály CI/CD ani týmovou práci.</span><span class="sxs-lookup"><span data-stu-id="343c9-139">This guide does not focus on the application lifecycle, DevOps, CI/CD pipelines, or team work.</span></span> <span data-ttu-id="343c9-140">[Doplněný životní cyklus aplikace Docker v kontejneru s využitím platformy a nástrojů Microsoftu se](https://aka.ms/dockerlifecycleebook) zaměřuje na tento předmět.</span><span class="sxs-lookup"><span data-stu-id="343c9-140">The complementary guide [Containerized Docker Application Lifecycle with Microsoft Platform and Tools](https://aka.ms/dockerlifecycleebook) focuses on that subject.</span></span> <span data-ttu-id="343c9-141">Aktuální příručka také neposkytuje podrobnosti o implementaci infrastruktury Azure, jako jsou informace o konkrétních orchestrcích.</span><span class="sxs-lookup"><span data-stu-id="343c9-141">The current guide also does not provide implementation details on Azure infrastructure, such as information on specific orchestrators.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="343c9-142">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="343c9-142">Additional resources</span></span>

- <span data-ttu-id="343c9-143">**Kontejnerové životní cykly aplikace Docker s platformou a nástroji Microsoftu** (elektronická kniha ke stažení)</span><span class="sxs-lookup"><span data-stu-id="343c9-143">**Containerized Docker Application Lifecycle with Microsoft Platform and Tools** (downloadable e-book)</span></span>  
    <https://aka.ms/dockerlifecycleebook>

## <a name="who-should-use-this-guide"></a><span data-ttu-id="343c9-144">Kdo by měl používat tuto příručku</span><span class="sxs-lookup"><span data-stu-id="343c9-144">Who should use this guide</span></span>

<span data-ttu-id="343c9-145">Tuto příručku jsme napsali pro vývojáře a architekty řešení, kteří jsou noví pro vývoj aplikací založených na Docker a na architekturu založenou na mikroslužbách.</span><span class="sxs-lookup"><span data-stu-id="343c9-145">We wrote this guide for developers and solution architects who are new to Docker-based application development and to microservices-based architecture.</span></span> <span data-ttu-id="343c9-146">Tato příručka je určena pro vás, pokud se chcete dozvědět, jak architekt, navrhovat a implementovat aplikace pro zkušební použití pomocí vývojových technologií Microsoftu (se speciálním zaměřením na .NET Core) a s kontejnery Docker.</span><span class="sxs-lookup"><span data-stu-id="343c9-146">This guide is for you if you want to learn how to architect, design, and implement proof-of-concept applications with Microsoft development technologies (with special focus on .NET Core) and with Docker containers.</span></span>

<span data-ttu-id="343c9-147">Tento průvodce najdete také v případě, že jste Tvůrce technického rozhodnutí, jako je například podnikový architekt, který vyžaduje architekturu a technologický přehled, než se rozhodnete, jaký přístup vybrat pro nové a moderní distribuované aplikace.</span><span class="sxs-lookup"><span data-stu-id="343c9-147">You will also find this guide useful if you are a technical decision maker, such as an enterprise architect, who wants an architecture and technology overview before you decide on what approach to select for new and modern distributed applications.</span></span>

### <a name="how-to-use-this-guide"></a><span data-ttu-id="343c9-148">Jak používat tohoto průvodce</span><span class="sxs-lookup"><span data-stu-id="343c9-148">How to use this guide</span></span>

<span data-ttu-id="343c9-149">První část této příručky zavádí kontejnery Docker, popisuje, jak zvolit mezi .NET Core a .NET Framework jako vývojovou architekturou a poskytuje přehled mikroslužeb.</span><span class="sxs-lookup"><span data-stu-id="343c9-149">The first part of this guide introduces Docker containers, discusses how to choose between .NET Core and the .NET Framework as a development framework, and provides an overview of microservices.</span></span> <span data-ttu-id="343c9-150">Tento obsah je určen pro architekty a pracovníky technického rozhodování, kteří chtějí přehled, ale nemusí se soustředit na podrobnosti implementace kódu.</span><span class="sxs-lookup"><span data-stu-id="343c9-150">This content is for architects and technical decision makers who want an overview but don't need to focus on code implementation details.</span></span>

<span data-ttu-id="343c9-151">Druhá část příručky začíná [procesem vývoje pro aplikace založené na Docker](./docker-application-development-process/index.md) .</span><span class="sxs-lookup"><span data-stu-id="343c9-151">The second part of the guide starts with the [Development process for Docker based applications](./docker-application-development-process/index.md) section.</span></span> <span data-ttu-id="343c9-152">Zaměřuje se na vývoj a vzory mikroslužeb pro implementaci aplikací pomocí .NET Core a Docker.</span><span class="sxs-lookup"><span data-stu-id="343c9-152">It focuses on development and microservice patterns for implementing applications using .NET Core and Docker.</span></span> <span data-ttu-id="343c9-153">Tato část bude mít největší zájem na vývojáře a architekty, kteří se chtějí zaměřit na kód a podrobnosti o vzorech a implementaci.</span><span class="sxs-lookup"><span data-stu-id="343c9-153">This section will be of most interest to developers and architects who want to focus on code and on patterns and implementation details.</span></span>

## <a name="related-microservice-and-container-based-reference-application-eshoponcontainers"></a><span data-ttu-id="343c9-154">Související referenční aplikace založené na mikroslužbách a kontejneru: eShopOnContainers</span><span class="sxs-lookup"><span data-stu-id="343c9-154">Related microservice and container-based reference application: eShopOnContainers</span></span>

<span data-ttu-id="343c9-155">Aplikace eShopOnContainers je open source referenční aplikace pro .NET Core a mikroslužby, které jsou navržené tak, aby se nasadily pomocí kontejnerů Docker.</span><span class="sxs-lookup"><span data-stu-id="343c9-155">The eShopOnContainers application is an open-source reference app for .NET Core and microservices that is designed to be deployed using Docker containers.</span></span> <span data-ttu-id="343c9-156">Aplikace se skládá z několika subsystémů, včetně několika front-Store přední konců uživatelského rozhraní (aplikace webové MVC, webové zabezpečené ověřování a nativní mobilní aplikace).</span><span class="sxs-lookup"><span data-stu-id="343c9-156">The application consists of multiple subsystems, including several e-store UI front ends (a Web MVC app, a Web SPA, and a native mobile app).</span></span> <span data-ttu-id="343c9-157">Zahrnuje také back-endové mikroslužby a kontejnery pro všechny požadované operace na straně serveru.</span><span class="sxs-lookup"><span data-stu-id="343c9-157">It also includes the back-end microservices and containers for all required server-side operations.</span></span>

<span data-ttu-id="343c9-158">Účelem aplikace je předvedení struktur architektury.</span><span class="sxs-lookup"><span data-stu-id="343c9-158">The purpose of the application is to showcase architectural patterns.</span></span> <span data-ttu-id="343c9-159">Nejedná se **o šablonu připravenou pro produkční prostředí** pro spouštění reálných aplikací.</span><span class="sxs-lookup"><span data-stu-id="343c9-159">**IT IS NOT A PRODUCTION-READY TEMPLATE** to start real-world applications.</span></span> <span data-ttu-id="343c9-160">Ve skutečnosti je aplikace v trvalé verzi beta verze, protože se také používá k otestování nových potenciálně zajímavých technologií, které se zobrazují.</span><span class="sxs-lookup"><span data-stu-id="343c9-160">In fact, the application is in a permanent beta state, as it’s also used to test new potentially interesting technologies as they show up.</span></span>

## <a name="send-us-your-feedback"></a><span data-ttu-id="343c9-161">Pošlete nám svůj názor.</span><span class="sxs-lookup"><span data-stu-id="343c9-161">Send us your feedback!</span></span>

<span data-ttu-id="343c9-162">Tento průvodce jsme napsali a pomohli vám pochopit architekturu kontejnerových aplikací a mikroslužeb v .NET.</span><span class="sxs-lookup"><span data-stu-id="343c9-162">We wrote this guide to help you understand the architecture of containerized applications and microservices in .NET.</span></span> <span data-ttu-id="343c9-163">Bude vyvíjena příručka a související referenční aplikace, takže jsme Vítejte na vašem názoru.</span><span class="sxs-lookup"><span data-stu-id="343c9-163">The guide and related reference application will be evolving, so we welcome your feedback!</span></span> <span data-ttu-id="343c9-164">Pokud máte komentáře týkající se vylepšení této příručky, odešlete zpětnou vazbu na <https://aka.ms/ebookfeedback>.</span><span class="sxs-lookup"><span data-stu-id="343c9-164">If you have comments about how this guide can be improved, submit feedback at <https://aka.ms/ebookfeedback>.</span></span>

## <a name="credits"></a><span data-ttu-id="343c9-165">Kredity</span><span class="sxs-lookup"><span data-stu-id="343c9-165">Credits</span></span>

<span data-ttu-id="343c9-166">Spoluautoři:</span><span class="sxs-lookup"><span data-stu-id="343c9-166">Co-Authors:</span></span>

> <span data-ttu-id="343c9-167">**Cesar de la Torre**, SR. PM, produktový tým .NET, Microsoft Corp.</span><span class="sxs-lookup"><span data-stu-id="343c9-167">**Cesar de la Torre**, Sr. PM, .NET product team, Microsoft Corp.</span></span>
>
> <span data-ttu-id="343c9-168">**Bill Wagner**, SR. Content Developer, C + E, Microsoft Corp.</span><span class="sxs-lookup"><span data-stu-id="343c9-168">**Bill Wagner**, Sr. Content Developer, C+E, Microsoft Corp.</span></span>
>
> <span data-ttu-id="343c9-169">**Jan Rousos**, hlavní softwarový inženýr, DevDiv Cat tým, Microsoft</span><span class="sxs-lookup"><span data-stu-id="343c9-169">**Mike Rousos**, Principal Software Engineer, DevDiv CAT team, Microsoft</span></span>

<span data-ttu-id="343c9-170">Editory</span><span class="sxs-lookup"><span data-stu-id="343c9-170">Editors:</span></span>

> <span data-ttu-id="343c9-171">**Mike Pope**</span><span class="sxs-lookup"><span data-stu-id="343c9-171">**Mike Pope**</span></span>
>
> <span data-ttu-id="343c9-172">**Steve Hoag**</span><span class="sxs-lookup"><span data-stu-id="343c9-172">**Steve Hoag**</span></span>

<span data-ttu-id="343c9-173">Účastníci a kontroloři:</span><span class="sxs-lookup"><span data-stu-id="343c9-173">Participants and reviewers:</span></span>

> <span data-ttu-id="343c9-174">**Jeffrey Richter**, partnerský software eng, tým Azure, Microsoft</span><span class="sxs-lookup"><span data-stu-id="343c9-174">**Jeffrey Richter**, Partner Software Eng, Azure team, Microsoft</span></span>
>
> <span data-ttu-id="343c9-175">**Jimmy Bogard**, hlavní architekt na headspring</span><span class="sxs-lookup"><span data-stu-id="343c9-175">**Jimmy Bogard**, Chief Architect at Headspring</span></span>
>
> <span data-ttu-id="343c9-176">**UDI Dahan**, zakladatel & výkonný ředitel, konkrétní software</span><span class="sxs-lookup"><span data-stu-id="343c9-176">**Udi Dahan**, Founder & CEO, Particular Software</span></span>
>
> <span data-ttu-id="343c9-177">**Jimmy Nilsson**, zakladatel a generální ředitel pro Factor10</span><span class="sxs-lookup"><span data-stu-id="343c9-177">**Jimmy Nilsson**, Co-founder and CEO of Factor10</span></span>
>
> <span data-ttu-id="343c9-178">**Glenn Condron**, SR. Program Manager, ASP.NET tým</span><span class="sxs-lookup"><span data-stu-id="343c9-178">**Glenn Condron**, Sr. Program Manager, ASP.NET team</span></span>
>
> <span data-ttu-id="343c9-179">**Mark Fussell**, hlavní vedoucí pro odpoledne, Azure Service Fabric Team, Microsoft</span><span class="sxs-lookup"><span data-stu-id="343c9-179">**Mark Fussell**, Principal PM Lead, Azure Service Fabric team, Microsoft</span></span>
>
> <span data-ttu-id="343c9-180">**Diegu Vega**, vedoucí pracovník, Entity Framework tým, Microsoft</span><span class="sxs-lookup"><span data-stu-id="343c9-180">**Diego Vega**, PM Lead, Entity Framework team, Microsoft</span></span>
>
> <span data-ttu-id="343c9-181">**Barryho Dorrans**, správce programu SR. Security</span><span class="sxs-lookup"><span data-stu-id="343c9-181">**Barry Dorrans**, Sr. Security Program Manager</span></span>
>
> <span data-ttu-id="343c9-182">**Rowan Miller**, SR. Program Manager, Microsoft</span><span class="sxs-lookup"><span data-stu-id="343c9-182">**Rowan Miller**, Sr. Program Manager, Microsoft</span></span>
>
> <span data-ttu-id="343c9-183">**Ankit Asthana**, hlavní správce odpoledne, tým .NET, Microsoft</span><span class="sxs-lookup"><span data-stu-id="343c9-183">**Ankit Asthana**, Principal PM Manager, .NET team, Microsoft</span></span>
>
> <span data-ttu-id="343c9-184">**Scott Hunterem**, ředitel pro partnery, tým .NET, Microsoft</span><span class="sxs-lookup"><span data-stu-id="343c9-184">**Scott Hunter**, Partner Director PM, .NET team, Microsoft</span></span>
>
> <span data-ttu-id="343c9-185">**Nish Anil**, SR. Program Manager, .NET Team, Microsoft</span><span class="sxs-lookup"><span data-stu-id="343c9-185">**Nish Anil**, Sr. Program Manager, .NET team, Microsoft</span></span>
>
> <span data-ttu-id="343c9-186">**Dylan Reisenberger**, architekt a vývojářského vedoucího v Polly</span><span class="sxs-lookup"><span data-stu-id="343c9-186">**Dylan Reisenberger**, Architect and Dev Lead at Polly</span></span>
>
> <span data-ttu-id="343c9-187">**Steve "ardalis" Smith** -Software Architect a Trainer- [Ardalis.com](https://ardalis.com)</span><span class="sxs-lookup"><span data-stu-id="343c9-187">**Steve "ardalis" Smith** - Software Architect and Trainer - [Ardalis.com](https://ardalis.com)</span></span>
>
> <span data-ttu-id="343c9-188">**Ian Cooper**, architekt kódu na jasnější úrovni</span><span class="sxs-lookup"><span data-stu-id="343c9-188">**Ian Cooper**, Coding Architect at Brighter</span></span>
>
> <span data-ttu-id="343c9-189">**Unai Zorrilla**, architekt a vývojářské olovo v jednoduchých konceptech</span><span class="sxs-lookup"><span data-stu-id="343c9-189">**Unai Zorrilla**, Architect and Dev Lead at Plain Concepts</span></span>
>
> <span data-ttu-id="343c9-190">**Eduard Tomas**, vedoucí pro vývoj na jednoduchých konceptech</span><span class="sxs-lookup"><span data-stu-id="343c9-190">**Eduard Tomas**, Dev Lead at Plain Concepts</span></span>
>
> <span data-ttu-id="343c9-191">**Ramon Tomas**, Developer na jednoduchých konceptech</span><span class="sxs-lookup"><span data-stu-id="343c9-191">**Ramon Tomas**, Developer at Plain Concepts</span></span>
>
> <span data-ttu-id="343c9-192">**David Sanz**, Developer na jednoduchých konceptech</span><span class="sxs-lookup"><span data-stu-id="343c9-192">**David Sanz**, Developer at Plain Concepts</span></span>
>
> <span data-ttu-id="343c9-193">**Javier Valero**, vedoucí pracovník v Grupo solutio</span><span class="sxs-lookup"><span data-stu-id="343c9-193">**Javier Valero**, Chief Operating Officer at Grupo Solutio</span></span>
>
> <span data-ttu-id="343c9-194">**Pierre-Millet**, SR. konzultant, Microsoft</span><span class="sxs-lookup"><span data-stu-id="343c9-194">**Pierre Millet**, Sr. Consultant, Microsoft</span></span>
>
> <span data-ttu-id="343c9-195">**Michael Friis**, produktový manažer, Docker Inc</span><span class="sxs-lookup"><span data-stu-id="343c9-195">**Michael Friis**, Product Manager, Docker Inc</span></span>
>
> <span data-ttu-id="343c9-196">**Charles Lowell**, software inženýr, vs Cat tým, Microsoft</span><span class="sxs-lookup"><span data-stu-id="343c9-196">**Charles Lowell**, Software Engineer, VS CAT team, Microsoft</span></span>
>
> <span data-ttu-id="343c9-197">**Miguel Veloso**, inženýr pro vývoj softwaru v jednoduchých konceptech</span><span class="sxs-lookup"><span data-stu-id="343c9-197">**Miguel Veloso**, Software Development Engineer at Plain Concepts</span></span>

## <a name="copyright"></a><span data-ttu-id="343c9-198">Copyright</span><span class="sxs-lookup"><span data-stu-id="343c9-198">Copyright</span></span>

<span data-ttu-id="343c9-199">PUBLIKOVAL (A)</span><span class="sxs-lookup"><span data-stu-id="343c9-199">PUBLISHED BY</span></span>

<span data-ttu-id="343c9-200">Microsoft Developer divize, .NET a Visual Studio Product teams</span><span class="sxs-lookup"><span data-stu-id="343c9-200">Microsoft Developer Division, .NET and Visual Studio product teams</span></span>

<span data-ttu-id="343c9-201">Divize společnosti Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="343c9-201">A division of Microsoft Corporation</span></span>

<span data-ttu-id="343c9-202">Jeden způsob Microsoftu</span><span class="sxs-lookup"><span data-stu-id="343c9-202">One Microsoft Way</span></span>

<span data-ttu-id="343c9-203">Redmond, Washington 98052-6399</span><span class="sxs-lookup"><span data-stu-id="343c9-203">Redmond, Washington 98052-6399</span></span>

<span data-ttu-id="343c9-204">Copyright © 2020 od společnosti Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="343c9-204">Copyright © 2020 by Microsoft Corporation</span></span>

<span data-ttu-id="343c9-205">Všechna práva vyhrazena.</span><span class="sxs-lookup"><span data-stu-id="343c9-205">All rights reserved.</span></span> <span data-ttu-id="343c9-206">Žádná část obsahu této knihy se nedá reprodukovat ani přenést v jakékoli formě nebo jakýmkoli způsobem bez písemného svolení vydavatele.</span><span class="sxs-lookup"><span data-stu-id="343c9-206">No part of the contents of this book may be reproduced or transmitted in any form or by any means without the written permission of the publisher.</span></span>

<span data-ttu-id="343c9-207">Tato kniha je k dispozici "tak jak jsou" a vyjadřuje zobrazení a stanoviska autora.</span><span class="sxs-lookup"><span data-stu-id="343c9-207">This book is provided “as-is” and expresses the author’s views and opinions.</span></span> <span data-ttu-id="343c9-208">Zobrazení, názory a informace vyjádřené v této knize, včetně adres URL a dalších odkazů na internetové weby, se mohou změnit bez předchozího upozornění.</span><span class="sxs-lookup"><span data-stu-id="343c9-208">The views, opinions and information expressed in this book, including URL and other Internet website references, may change without notice.</span></span>

<span data-ttu-id="343c9-209">Některé příklady, které jsou zde uvedeny, jsou k dispozici pouze pro ilustraci a jsou smyšlené.</span><span class="sxs-lookup"><span data-stu-id="343c9-209">Some examples depicted herein are provided for illustration only and are fictitious.</span></span> <span data-ttu-id="343c9-210">Neexistuje žádné skutečné přidružení nebo připojení, které by mělo být odvozeno.</span><span class="sxs-lookup"><span data-stu-id="343c9-210">No real association or connection is intended or should be inferred.</span></span>

<span data-ttu-id="343c9-211">Microsoft a ochranné známky uvedené na adrese <https://www.microsoft.com> na webové stránce ochranné známky jsou ochranné známky skupiny společností Microsoft.</span><span class="sxs-lookup"><span data-stu-id="343c9-211">Microsoft and the trademarks listed at <https://www.microsoft.com> on the “Trademarks” webpage are trademarks of the Microsoft group of companies.</span></span>

<span data-ttu-id="343c9-212">Mac a macOS jsou ochranné známky společnosti Apple Inc.</span><span class="sxs-lookup"><span data-stu-id="343c9-212">Mac and macOS are trademarks of Apple Inc.</span></span>

<span data-ttu-id="343c9-213">Logo Docker Whale je registrovaná ochranná známka společnosti Docker, Inc., kterou používá oprávnění.</span><span class="sxs-lookup"><span data-stu-id="343c9-213">The Docker whale logo is a registered trademark of Docker, Inc. Used by permission.</span></span>

<span data-ttu-id="343c9-214">Všechny ostatní značky a loga jsou majetkem příslušných vlastníků.</span><span class="sxs-lookup"><span data-stu-id="343c9-214">All other marks and logos are property of their respective owners.</span></span>

>[!div class="step-by-step"]
>[<span data-ttu-id="343c9-215">Next</span><span class="sxs-lookup"><span data-stu-id="343c9-215">Next</span></span>](container-docker-introduction/index.md)
