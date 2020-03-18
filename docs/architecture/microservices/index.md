---
title: Mikroslužby .NET. Architektura pro kontejnerizované aplikace .NET
description: Architektura mikroslužeb .NET pro kontejnerizované aplikace .NET | Mikroslužeb jsou modulární a nezávisle nasaditelné služby. Kontejnery Dockeru (pro Linux a Windows) zjednodušují nasazení a testování sdružováním služby a jejích závislostí do jedné jednotky, která se pak spouštějí v izolovaném prostředí.
ms.date: 01/30/2020
ms.openlocfilehash: 1337fe56e78e03a85627737bd52a089fd946b842
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "77543531"
---
# <a name="net-microservices-architecture-for-containerized-net-applications"></a><span data-ttu-id="bdda3-105">.NET Microservices: Architektura pro kontejnerizované aplikace .NET</span><span class="sxs-lookup"><span data-stu-id="bdda3-105">.NET Microservices: Architecture for Containerized .NET Applications</span></span>

![Obálka knihy](./media/cover-small.png)

<span data-ttu-id="bdda3-107">**EDITION v3.1** - Aktualizováno na ASP.NET Jádro 3.1</span><span class="sxs-lookup"><span data-stu-id="bdda3-107">**EDITION v3.1** - Updated to ASP.NET Core 3.1</span></span>

<span data-ttu-id="bdda3-108">Tato příručka je úvodem do vývoje aplikací založených na mikroslužbách a jejich správě pomocí kontejnerů.</span><span class="sxs-lookup"><span data-stu-id="bdda3-108">This guide is an introduction to developing microservices-based applications and managing them using containers.</span></span> <span data-ttu-id="bdda3-109">Popisuje architektury návrhu a implementace přístupy pomocí .NET Core a Docker kontejnery.</span><span class="sxs-lookup"><span data-stu-id="bdda3-109">It discusses architectural design and implementation approaches using .NET Core and Docker containers.</span></span>

<span data-ttu-id="bdda3-110">Chcete-li usnadnit začít, průvodce se zaměřuje na odkaz kontejnerizované a mikroslužeb založené aplikace, které můžete prozkoumat.</span><span class="sxs-lookup"><span data-stu-id="bdda3-110">To make it easier to get started, the guide focuses on a reference containerized and microservice-based application that you can explore.</span></span> <span data-ttu-id="bdda3-111">Referenční aplikace je k dispozici na [repo eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) GitHub.</span><span class="sxs-lookup"><span data-stu-id="bdda3-111">The reference application is available at the [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) GitHub repo.</span></span>

## <a name="action-links"></a><span data-ttu-id="bdda3-112">Akční odkazy</span><span class="sxs-lookup"><span data-stu-id="bdda3-112">Action links</span></span>

- <span data-ttu-id="bdda3-113">Tato e-kniha je také k dispozici ve formátu PDF (pouze anglická verze) [Ke stažení](https://aka.ms/microservicesebook)</span><span class="sxs-lookup"><span data-stu-id="bdda3-113">This e-book is also available in a PDF format (English version only) [Download](https://aka.ms/microservicesebook)</span></span>

- <span data-ttu-id="bdda3-114">Klonovat/rozvintí referenční aplikace [eShopOnContainers na GitHubu](https://github.com/dotnet-architecture/eShopOnContainers)</span><span class="sxs-lookup"><span data-stu-id="bdda3-114">Clone/Fork the reference application [eShopOnContainers on GitHub](https://github.com/dotnet-architecture/eShopOnContainers)</span></span>

- <span data-ttu-id="bdda3-115">Podívejte se na [úvodní video na kanálu 9](https://aka.ms/microservices-video)</span><span class="sxs-lookup"><span data-stu-id="bdda3-115">Watch the [introductory video on Channel 9](https://aka.ms/microservices-video)</span></span>

- <span data-ttu-id="bdda3-116">Seznamte se s [architekturou mikroslužeb](https://aka.ms/MicroservicesArchitecture) ihned</span><span class="sxs-lookup"><span data-stu-id="bdda3-116">Get to know the [Microservices Architecture](https://aka.ms/MicroservicesArchitecture) right away</span></span>

## <a name="introduction"></a><span data-ttu-id="bdda3-117">Úvod</span><span class="sxs-lookup"><span data-stu-id="bdda3-117">Introduction</span></span>

<span data-ttu-id="bdda3-118">Podniky stále více realizuje úspory nákladů, řeší problémy s nasazením a vylepšují devops a výrobní operace pomocí kontejnerů.</span><span class="sxs-lookup"><span data-stu-id="bdda3-118">Enterprises are increasingly realizing cost savings, solving deployment problems, and improving DevOps and production operations by using containers.</span></span> <span data-ttu-id="bdda3-119">Microsoft vydává inovace kontejnerů pro Windows a Linux tím, že vytváří produkty, jako je Azure Kubernetes Service a Azure Service Fabric, a spolupracuje s vedoucími pracovníky v oboru, jako jsou Docker, Mesosphere a Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="bdda3-119">Microsoft has been releasing container innovations for Windows and Linux by creating products like Azure Kubernetes Service and Azure Service Fabric, and by partnering with industry leaders like Docker, Mesosphere, and Kubernetes.</span></span> <span data-ttu-id="bdda3-120">Tyto produkty poskytují kontejnerová řešení, která pomáhají společnostem vytvářet a nasazovat aplikace rychlostí a škálovatrychlostí cloudu, bez ohledu na jejich výběr platformy nebo nástrojů.</span><span class="sxs-lookup"><span data-stu-id="bdda3-120">These products deliver container solutions that help companies build and deploy applications at cloud speed and scale, whatever their choice of platform or tools.</span></span>

<span data-ttu-id="bdda3-121">Docker se stává de facto standardem v kontejnerovém průmyslu, podporovaný nejvýznamnějšími dodavateli v ekosystémech Windows a Linux.</span><span class="sxs-lookup"><span data-stu-id="bdda3-121">Docker is becoming the de facto standard in the container industry, supported by the most significant vendors in the Windows and Linux ecosystems.</span></span> <span data-ttu-id="bdda3-122">(Microsoft je jedním z hlavních dodavatelů cloudu podporující docker.) V budoucnu bude Docker pravděpodobně všudypřítomný v libovolném datovém centru v cloudu nebo v místním prostředí.</span><span class="sxs-lookup"><span data-stu-id="bdda3-122">(Microsoft is one of the main cloud vendors supporting Docker.) In the future, Docker will probably be ubiquitous in any datacenter in the cloud or on-premises.</span></span>

<span data-ttu-id="bdda3-123">Kromě toho architektura [mikroslužeb](https://martinfowler.com/articles/microservices.html) se objevuje jako důležitý přístup pro distribuované důležité aplikace.</span><span class="sxs-lookup"><span data-stu-id="bdda3-123">In addition, the [microservices](https://martinfowler.com/articles/microservices.html) architecture is emerging as an important approach for distributed mission-critical applications.</span></span> <span data-ttu-id="bdda3-124">V architektuře založené na mikroslužbách je aplikace postavena na kolekci služeb, které lze vyvíjet, testovat, nasazovat a vyvíjet nezávisle.</span><span class="sxs-lookup"><span data-stu-id="bdda3-124">In a microservice-based architecture, the application is built on a collection of services that can be developed, tested, deployed, and versioned independently.</span></span>

## <a name="about-this-guide"></a><span data-ttu-id="bdda3-125">O této příručce</span><span class="sxs-lookup"><span data-stu-id="bdda3-125">About this guide</span></span>

<span data-ttu-id="bdda3-126">Tato příručka je úvodem do vývoje aplikací založených na mikroslužbách a jejich správě pomocí kontejnerů.</span><span class="sxs-lookup"><span data-stu-id="bdda3-126">This guide is an introduction to developing microservices-based applications and managing them using containers.</span></span> <span data-ttu-id="bdda3-127">Popisuje architektury návrhu a implementace přístupy pomocí .NET Core a Docker kontejnery.</span><span class="sxs-lookup"><span data-stu-id="bdda3-127">It discusses architectural design and implementation approaches using .NET Core and Docker containers.</span></span> <span data-ttu-id="bdda3-128">Chcete-li usnadnit začít s kontejnery a mikroslužeb, průvodce se zaměřuje na odkaz kontejnerizované a mikroslužeb založené aplikace, které můžete prozkoumat.</span><span class="sxs-lookup"><span data-stu-id="bdda3-128">To make it easier to get started with containers and microservices, the guide focuses on a reference containerized and microservice-based application that you can explore.</span></span> <span data-ttu-id="bdda3-129">Ukázková aplikace je k dispozici v úložišti [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) GitHub.</span><span class="sxs-lookup"><span data-stu-id="bdda3-129">The sample application is available at the [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) GitHub repo.</span></span>

<span data-ttu-id="bdda3-130">Tato příručka poskytuje základní vývoj a architektonické pokyny především na úrovni vývojového prostředí se zaměřením na dvě technologie: Docker a .NET Core.</span><span class="sxs-lookup"><span data-stu-id="bdda3-130">This guide provides foundational development and architectural guidance primarily at a development environment level with a focus on two technologies: Docker and .NET Core.</span></span> <span data-ttu-id="bdda3-131">Naším záměrem je, abyste si přečetli tuto příručku při přemýšlení o návrhu aplikace, aniž byste se zaměřili na infrastrukturu (cloud nebo místní) vašeho produkčního prostředí.</span><span class="sxs-lookup"><span data-stu-id="bdda3-131">Our intention is that you read this guide when thinking about your application design without focusing on the infrastructure (cloud or on-premises) of your production environment.</span></span> <span data-ttu-id="bdda3-132">O vaší infrastruktuře se budete rozhodovat později, až vytvoříte aplikace připravené pro produkční prostředí.</span><span class="sxs-lookup"><span data-stu-id="bdda3-132">You will make decisions about your infrastructure later, when you create your production-ready applications.</span></span> <span data-ttu-id="bdda3-133">Proto tato příručka je určena k infrastruktury agnostik a více na vývoj prostředí.</span><span class="sxs-lookup"><span data-stu-id="bdda3-133">Therefore, this guide is intended to be infrastructure agnostic and more development-environment-centric.</span></span>

<span data-ttu-id="bdda3-134">Po prostudování této příručky by dalším krokem bylo získat informace o mikroslužbách připravených pro produkční prostředí v Microsoft Azure.</span><span class="sxs-lookup"><span data-stu-id="bdda3-134">After you have studied this guide, your next step would be to learn about production-ready microservices on Microsoft Azure.</span></span>

## <a name="version"></a><span data-ttu-id="bdda3-135">Version</span><span class="sxs-lookup"><span data-stu-id="bdda3-135">Version</span></span>

<span data-ttu-id="bdda3-136">Tato příručka byla revidována tak, aby pokrývala verzi **.NET Core 3.1** spolu s mnoha dalšími aktualizacemi souvisejícími se stejnou "vlnou" technologií (tj. Azure a dalšími technologiemi třetích stran), které se časově mění s verzí .NET Core 3.1.</span><span class="sxs-lookup"><span data-stu-id="bdda3-136">This guide has been revised to cover **.NET Core 3.1** version along with many additional updates related to the same “wave” of technologies (that is, Azure and additional third-party technologies) coinciding in time with the .NET Core 3.1 release.</span></span> <span data-ttu-id="bdda3-137">To je důvod, proč kniha verze byla také aktualizována na verzi **3.1**.</span><span class="sxs-lookup"><span data-stu-id="bdda3-137">That’s why the book version has also been updated to version **3.1**.</span></span>

## <a name="what-this-guide-does-not-cover"></a><span data-ttu-id="bdda3-138">Co tato příručka nezahrnuje</span><span class="sxs-lookup"><span data-stu-id="bdda3-138">What this guide does not cover</span></span>

<span data-ttu-id="bdda3-139">Tato příručka se nezaměřuje na životní cyklus aplikace, devops, ci/cd kanály nebo týmovou práci.</span><span class="sxs-lookup"><span data-stu-id="bdda3-139">This guide does not focus on the application lifecycle, DevOps, CI/CD pipelines, or team work.</span></span> <span data-ttu-id="bdda3-140">Na toto téma se zaměřuje doplňková příručka [Containerized Docker Application Lifecycle s platformou Microsoft Platform and Tools.](https://aka.ms/dockerlifecycleebook)</span><span class="sxs-lookup"><span data-stu-id="bdda3-140">The complementary guide [Containerized Docker Application Lifecycle with Microsoft Platform and Tools](https://aka.ms/dockerlifecycleebook) focuses on that subject.</span></span> <span data-ttu-id="bdda3-141">Aktuální průvodce také neposkytuje podrobnosti implementace infrastruktury Azure, jako jsou informace o konkrétních orchestrátorech.</span><span class="sxs-lookup"><span data-stu-id="bdda3-141">The current guide also does not provide implementation details on Azure infrastructure, such as information on specific orchestrators.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="bdda3-142">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="bdda3-142">Additional resources</span></span>

- <span data-ttu-id="bdda3-143">**Kontejnerizovaný životní cyklus aplikací Dockeru s platformou Microsoft Platform and Tools** (e-kniha ke stažení)</span><span class="sxs-lookup"><span data-stu-id="bdda3-143">**Containerized Docker Application Lifecycle with Microsoft Platform and Tools** (downloadable e-book)</span></span>  
    <https://aka.ms/dockerlifecycleebook>

## <a name="who-should-use-this-guide"></a><span data-ttu-id="bdda3-144">Kdo by měl používat tuto příručku</span><span class="sxs-lookup"><span data-stu-id="bdda3-144">Who should use this guide</span></span>

<span data-ttu-id="bdda3-145">Napsali jsme tuto příručku pro vývojáře a architekty řešení, kteří jsou noví ve vývoji aplikací založených na Dockeru a na architektuře založené na mikroslužbách.</span><span class="sxs-lookup"><span data-stu-id="bdda3-145">We wrote this guide for developers and solution architects who are new to Docker-based application development and to microservices-based architecture.</span></span> <span data-ttu-id="bdda3-146">Tato příručka je pro vás, pokud se chcete dozvědět, jak architekt, návrh a implementaci proof-of-concept aplikací s vývojovými technologiemi Microsoftu (se zvláštním zaměřením na .NET Core) a s kontejnery Dockeru.</span><span class="sxs-lookup"><span data-stu-id="bdda3-146">This guide is for you if you want to learn how to architect, design, and implement proof-of-concept applications with Microsoft development technologies (with special focus on .NET Core) and with Docker containers.</span></span>

<span data-ttu-id="bdda3-147">Tuto příručku také považujete za užitečnou, pokud jste technický rozhodovací orgán, například podnikový architekt, který chce přehled architektury a technologie, než se rozhodnete, jaký přístup vybrat pro nové a moderní distribuované aplikace.</span><span class="sxs-lookup"><span data-stu-id="bdda3-147">You will also find this guide useful if you are a technical decision maker, such as an enterprise architect, who wants an architecture and technology overview before you decide on what approach to select for new and modern distributed applications.</span></span>

### <a name="how-to-use-this-guide"></a><span data-ttu-id="bdda3-148">Jak používat tohoto průvodce</span><span class="sxs-lookup"><span data-stu-id="bdda3-148">How to use this guide</span></span>

<span data-ttu-id="bdda3-149">První část této příručky zavádí kontejnery Dockeru, popisuje, jak si vybrat mezi .NET Core a rozhraní .NET Framework jako vývojové rozhraní a poskytuje přehled mikroslužeb.</span><span class="sxs-lookup"><span data-stu-id="bdda3-149">The first part of this guide introduces Docker containers, discusses how to choose between .NET Core and the .NET Framework as a development framework, and provides an overview of microservices.</span></span> <span data-ttu-id="bdda3-150">Tento obsah je určen architektům a technickým rozhodovacím orgánům, kteří chtějí přehled, ale nemusí se zaměřovat na podrobnosti implementace kódu.</span><span class="sxs-lookup"><span data-stu-id="bdda3-150">This content is for architects and technical decision makers who want an overview but don't need to focus on code implementation details.</span></span>

<span data-ttu-id="bdda3-151">Druhá část průvodce začíná [procesem vývoje pro aplikace založené na Dockeru.](./docker-application-development-process/index.md)</span><span class="sxs-lookup"><span data-stu-id="bdda3-151">The second part of the guide starts with the [Development process for Docker based applications](./docker-application-development-process/index.md) section.</span></span> <span data-ttu-id="bdda3-152">Zaměřuje se na vývoj a mikroslužby vzory pro implementaci aplikací pomocí .NET Core a Docker.</span><span class="sxs-lookup"><span data-stu-id="bdda3-152">It focuses on development and microservice patterns for implementing applications using .NET Core and Docker.</span></span> <span data-ttu-id="bdda3-153">Tato část bude nejvíce zajímat vývojáře a architekty, kteří se chtějí zaměřit na kód a na vzory a podrobnosti implementace.</span><span class="sxs-lookup"><span data-stu-id="bdda3-153">This section will be of most interest to developers and architects who want to focus on code and on patterns and implementation details.</span></span>

## <a name="related-microservice-and-container-based-reference-application-eshoponcontainers"></a><span data-ttu-id="bdda3-154">Související referenční aplikace mikroslužeb a kontejnerů: eShopOnContainers</span><span class="sxs-lookup"><span data-stu-id="bdda3-154">Related microservice and container-based reference application: eShopOnContainers</span></span>

<span data-ttu-id="bdda3-155">Aplikace eShopOnContainers je referenční aplikace s otevřeným zdrojovým kódem pro .NET Core a mikroslužby, která je určena k nasazení pomocí kontejnerů Dockeru.</span><span class="sxs-lookup"><span data-stu-id="bdda3-155">The eShopOnContainers application is an open-source reference app for .NET Core and microservices that is designed to be deployed using Docker containers.</span></span> <span data-ttu-id="bdda3-156">Aplikace se skládá z více subsystémů, včetně několika front-endů uživatelského nastavení e-store (webová aplikace MVC, Web SPA a nativní mobilní aplikace).</span><span class="sxs-lookup"><span data-stu-id="bdda3-156">The application consists of multiple subsystems, including several e-store UI front ends (a Web MVC app, a Web SPA, and a native mobile app).</span></span> <span data-ttu-id="bdda3-157">Obsahuje také back-endové mikroslužby a kontejnery pro všechny požadované operace na straně serveru.</span><span class="sxs-lookup"><span data-stu-id="bdda3-157">It also includes the back-end microservices and containers for all required server-side operations.</span></span>

<span data-ttu-id="bdda3-158">Účelem aplikace je předvést architektonické vzory.</span><span class="sxs-lookup"><span data-stu-id="bdda3-158">The purpose of the application is to showcase architectural patterns.</span></span> <span data-ttu-id="bdda3-159">**Není to šablona připravená na výrobu** pro spuštění reálných aplikací.</span><span class="sxs-lookup"><span data-stu-id="bdda3-159">**IT IS NOT A PRODUCTION-READY TEMPLATE** to start real-world applications.</span></span> <span data-ttu-id="bdda3-160">Ve skutečnosti je aplikace v trvalém stavu beta, protože se také používá k testování nových potenciálně zajímavých technologií, jak se objevují.</span><span class="sxs-lookup"><span data-stu-id="bdda3-160">In fact, the application is in a permanent beta state, as it’s also used to test new potentially interesting technologies as they show up.</span></span>

## <a name="send-us-your-feedback"></a><span data-ttu-id="bdda3-161">Pošlete nám svůj názor!</span><span class="sxs-lookup"><span data-stu-id="bdda3-161">Send us your feedback!</span></span>

<span data-ttu-id="bdda3-162">Napsali jsme tuto příručku, která vám pomůže pochopit architekturu kontejnerizovaných aplikací a mikroslužeb v rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="bdda3-162">We wrote this guide to help you understand the architecture of containerized applications and microservices in .NET.</span></span> <span data-ttu-id="bdda3-163">Průvodce a související referenční aplikace se bude vyvíjet, takže uvítáme vaši zpětnou vazbu!</span><span class="sxs-lookup"><span data-stu-id="bdda3-163">The guide and related reference application will be evolving, so we welcome your feedback!</span></span> <span data-ttu-id="bdda3-164">Pokud máte připomínky k tomu, jak lze <https://aka.ms/ebookfeedback>tuto příručku zlepšit, odešlete zpětnou vazbu na adrese .</span><span class="sxs-lookup"><span data-stu-id="bdda3-164">If you have comments about how this guide can be improved, submit feedback at <https://aka.ms/ebookfeedback>.</span></span>

## <a name="credits"></a><span data-ttu-id="bdda3-165">Kredity</span><span class="sxs-lookup"><span data-stu-id="bdda3-165">Credits</span></span>

<span data-ttu-id="bdda3-166">Spoluautoři:</span><span class="sxs-lookup"><span data-stu-id="bdda3-166">Co-Authors:</span></span>

> <span data-ttu-id="bdda3-167">**Cesar de la Torre**, Sr. PM, produktový tým .NET, Microsoft Corp.</span><span class="sxs-lookup"><span data-stu-id="bdda3-167">**Cesar de la Torre**, Sr. PM, .NET product team, Microsoft Corp.</span></span>
>
> <span data-ttu-id="bdda3-168">**Bill Wagner**, sr. Content Developer, C + E, Microsoft Corp.</span><span class="sxs-lookup"><span data-stu-id="bdda3-168">**Bill Wagner**, Sr. Content Developer, C+E, Microsoft Corp.</span></span>
>
> <span data-ttu-id="bdda3-169">**Mike Rousos**, hlavní softwarový inženýr, DevDiv CAT tým, Microsoft</span><span class="sxs-lookup"><span data-stu-id="bdda3-169">**Mike Rousos**, Principal Software Engineer, DevDiv CAT team, Microsoft</span></span>

<span data-ttu-id="bdda3-170">Editory:</span><span class="sxs-lookup"><span data-stu-id="bdda3-170">Editors:</span></span>

> <span data-ttu-id="bdda3-171">**Mike Papež**</span><span class="sxs-lookup"><span data-stu-id="bdda3-171">**Mike Pope**</span></span>
>
> <span data-ttu-id="bdda3-172">**Steva Hoaga**</span><span class="sxs-lookup"><span data-stu-id="bdda3-172">**Steve Hoag**</span></span>

<span data-ttu-id="bdda3-173">Účastníci a recenzenti:</span><span class="sxs-lookup"><span data-stu-id="bdda3-173">Participants and reviewers:</span></span>

> <span data-ttu-id="bdda3-174">**Jeffrey Richter**, Partner Software Eng, Tým Azure, Microsoft</span><span class="sxs-lookup"><span data-stu-id="bdda3-174">**Jeffrey Richter**, Partner Software Eng, Azure team, Microsoft</span></span>
>
> <span data-ttu-id="bdda3-175">**Jimmy Bogard**, hlavní architekt ve společnosti Headspring</span><span class="sxs-lookup"><span data-stu-id="bdda3-175">**Jimmy Bogard**, Chief Architect at Headspring</span></span>
>
> <span data-ttu-id="bdda3-176">**Udi Dahan**, zakladatel & generální ředitel, Konkrétní software</span><span class="sxs-lookup"><span data-stu-id="bdda3-176">**Udi Dahan**, Founder & CEO, Particular Software</span></span>
>
> <span data-ttu-id="bdda3-177">**Jimmy Nilsson**, spoluzakladatel a generální ředitel společnosti Factor10</span><span class="sxs-lookup"><span data-stu-id="bdda3-177">**Jimmy Nilsson**, Co-founder and CEO of Factor10</span></span>
>
> <span data-ttu-id="bdda3-178">**Glenn Condron**, sr. programový manažer, ASP.NET tým</span><span class="sxs-lookup"><span data-stu-id="bdda3-178">**Glenn Condron**, Sr. Program Manager, ASP.NET team</span></span>
>
> <span data-ttu-id="bdda3-179">**Mark Fussell**, hlavní vedoucí pm, tým Azure Service Fabric, Microsoft</span><span class="sxs-lookup"><span data-stu-id="bdda3-179">**Mark Fussell**, Principal PM Lead, Azure Service Fabric team, Microsoft</span></span>
>
> <span data-ttu-id="bdda3-180">**Diego Vega**, PM Lead, Entity Framework tým, Microsoft</span><span class="sxs-lookup"><span data-stu-id="bdda3-180">**Diego Vega**, PM Lead, Entity Framework team, Microsoft</span></span>
>
> <span data-ttu-id="bdda3-181">**Barry Dorrans**, vedoucí bezpečnostního programu</span><span class="sxs-lookup"><span data-stu-id="bdda3-181">**Barry Dorrans**, Sr. Security Program Manager</span></span>
>
> <span data-ttu-id="bdda3-182">**Rowan Miller**, Sr. Program Manager, Microsoft</span><span class="sxs-lookup"><span data-stu-id="bdda3-182">**Rowan Miller**, Sr. Program Manager, Microsoft</span></span>
>
> <span data-ttu-id="bdda3-183">**Ankit Asthana**, hlavní pm manažer, .NET tým, Microsoft</span><span class="sxs-lookup"><span data-stu-id="bdda3-183">**Ankit Asthana**, Principal PM Manager, .NET team, Microsoft</span></span>
>
> <span data-ttu-id="bdda3-184">**Scott Hunter**, partnerský ředitel PM, .NET tým, Microsoft</span><span class="sxs-lookup"><span data-stu-id="bdda3-184">**Scott Hunter**, Partner Director PM, .NET team, Microsoft</span></span>
>
> <span data-ttu-id="bdda3-185">**Nish Anil**, Sr. Program Manager, .NET tým, Microsoft</span><span class="sxs-lookup"><span data-stu-id="bdda3-185">**Nish Anil**, Sr. Program Manager, .NET team, Microsoft</span></span>
>
> <span data-ttu-id="bdda3-186">**Dylan Reisenberger**, architekt a dev olovo v Polly</span><span class="sxs-lookup"><span data-stu-id="bdda3-186">**Dylan Reisenberger**, Architect and Dev Lead at Polly</span></span>
>
> <span data-ttu-id="bdda3-187">**Steve "ardalis" Smith** - softwarový architekt a trenér - [Ardalis.com](https://ardalis.com)</span><span class="sxs-lookup"><span data-stu-id="bdda3-187">**Steve "ardalis" Smith** - Software Architect and Trainer - [Ardalis.com](https://ardalis.com)</span></span>
>
> <span data-ttu-id="bdda3-188">**Ian Cooper**, Coding Architect ve společnosti Brighter</span><span class="sxs-lookup"><span data-stu-id="bdda3-188">**Ian Cooper**, Coding Architect at Brighter</span></span>
>
> <span data-ttu-id="bdda3-189">**Unai Zorrilla**, architekt a dev olovo ve společnosti Plain Concepts</span><span class="sxs-lookup"><span data-stu-id="bdda3-189">**Unai Zorrilla**, Architect and Dev Lead at Plain Concepts</span></span>
>
> <span data-ttu-id="bdda3-190">**Eduard Tomas**, Dev Lead ve společnosti Plain Concepts</span><span class="sxs-lookup"><span data-stu-id="bdda3-190">**Eduard Tomas**, Dev Lead at Plain Concepts</span></span>
>
> <span data-ttu-id="bdda3-191">**Ramon Tomas**, Developer ve společnosti Plain Concepts</span><span class="sxs-lookup"><span data-stu-id="bdda3-191">**Ramon Tomas**, Developer at Plain Concepts</span></span>
>
> <span data-ttu-id="bdda3-192">**David Sanz**, Developer ve společnosti Plain Concepts</span><span class="sxs-lookup"><span data-stu-id="bdda3-192">**David Sanz**, Developer at Plain Concepts</span></span>
>
> <span data-ttu-id="bdda3-193">**Javier Valero**, provozní ředitel společnosti Grupo Solutio</span><span class="sxs-lookup"><span data-stu-id="bdda3-193">**Javier Valero**, Chief Operating Officer at Grupo Solutio</span></span>
>
> <span data-ttu-id="bdda3-194">**Pierre Millet**, senior konzultant, Microsoft</span><span class="sxs-lookup"><span data-stu-id="bdda3-194">**Pierre Millet**, Sr. Consultant, Microsoft</span></span>
>
> <span data-ttu-id="bdda3-195">**Michael Friis**, produktový manažer, Docker Inc</span><span class="sxs-lookup"><span data-stu-id="bdda3-195">**Michael Friis**, Product Manager, Docker Inc</span></span>
>
> <span data-ttu-id="bdda3-196">**Charles Lowell**, softwarový inženýr, Tým VS CAT, Microsoft</span><span class="sxs-lookup"><span data-stu-id="bdda3-196">**Charles Lowell**, Software Engineer, VS CAT team, Microsoft</span></span>
>
> <span data-ttu-id="bdda3-197">**Miguel Veloso**, software development engineer ve společnosti Plain Concepts</span><span class="sxs-lookup"><span data-stu-id="bdda3-197">**Miguel Veloso**, Software Development Engineer at Plain Concepts</span></span>

## <a name="copyright"></a><span data-ttu-id="bdda3-198">Copyright</span><span class="sxs-lookup"><span data-stu-id="bdda3-198">Copyright</span></span>

<span data-ttu-id="bdda3-199">PUBLIKOVAL(A)</span><span class="sxs-lookup"><span data-stu-id="bdda3-199">PUBLISHED BY</span></span>

<span data-ttu-id="bdda3-200">Produktové týmy Microsoft Developer Division, .NET a Visual Studio</span><span class="sxs-lookup"><span data-stu-id="bdda3-200">Microsoft Developer Division, .NET and Visual Studio product teams</span></span>

<span data-ttu-id="bdda3-201">Divize společnosti Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="bdda3-201">A division of Microsoft Corporation</span></span>

<span data-ttu-id="bdda3-202">One Microsoft Way</span><span class="sxs-lookup"><span data-stu-id="bdda3-202">One Microsoft Way</span></span>

<span data-ttu-id="bdda3-203">Redmond, Washington 98052-6399</span><span class="sxs-lookup"><span data-stu-id="bdda3-203">Redmond, Washington 98052-6399</span></span>

<span data-ttu-id="bdda3-204">Autorská práva © 2020 společností Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="bdda3-204">Copyright © 2020 by Microsoft Corporation</span></span>

<span data-ttu-id="bdda3-205">Všechna práva vyhrazena.</span><span class="sxs-lookup"><span data-stu-id="bdda3-205">All rights reserved.</span></span> <span data-ttu-id="bdda3-206">Žádná část obsahu této knihy nesmí být reprodukována nebo přenášena v jakékoli formě nebo jakýmkoli způsobem bez písemného souhlasu vydavatele.</span><span class="sxs-lookup"><span data-stu-id="bdda3-206">No part of the contents of this book may be reproduced or transmitted in any form or by any means without the written permission of the publisher.</span></span>

<span data-ttu-id="bdda3-207">Tato kniha je poskytována "tak, jak je" a vyjadřuje názory a názory autora.</span><span class="sxs-lookup"><span data-stu-id="bdda3-207">This book is provided “as-is” and expresses the author’s views and opinions.</span></span> <span data-ttu-id="bdda3-208">Názory, názory a informace vyjádřené v této knize, včetně URL a dalších odkazů na internetové stránky, se mohou změnit bez předchozího upozornění.</span><span class="sxs-lookup"><span data-stu-id="bdda3-208">The views, opinions and information expressed in this book, including URL and other Internet website references, may change without notice.</span></span>

<span data-ttu-id="bdda3-209">Některé zde uvedené příklady slouží pouze k znázornění a jsou smyšlené.</span><span class="sxs-lookup"><span data-stu-id="bdda3-209">Some examples depicted herein are provided for illustration only and are fictitious.</span></span> <span data-ttu-id="bdda3-210">Neměli byste z nich vyvozovat žádné skutečné vztahy či spojení.</span><span class="sxs-lookup"><span data-stu-id="bdda3-210">No real association or connection is intended or should be inferred.</span></span>

<span data-ttu-id="bdda3-211">Společnost Microsoft a ochranné <https://www.microsoft.com> známky uvedené na webové stránce "Ochranné známky" jsou ochrannými známkami skupiny společností Microsoft.</span><span class="sxs-lookup"><span data-stu-id="bdda3-211">Microsoft and the trademarks listed at <https://www.microsoft.com> on the “Trademarks” webpage are trademarks of the Microsoft group of companies.</span></span>

<span data-ttu-id="bdda3-212">Mac a macOS jsou ochranné známky společnosti Apple Inc.</span><span class="sxs-lookup"><span data-stu-id="bdda3-212">Mac and macOS are trademarks of Apple Inc.</span></span>

<span data-ttu-id="bdda3-213">Logo velryby Docker je registrovaná ochranná známka společnosti Docker, Inc. Používá se svolením.</span><span class="sxs-lookup"><span data-stu-id="bdda3-213">The Docker whale logo is a registered trademark of Docker, Inc. Used by permission.</span></span>

<span data-ttu-id="bdda3-214">Všechny ostatní značky a loga jsou majetkem příslušných vlastníků.</span><span class="sxs-lookup"><span data-stu-id="bdda3-214">All other marks and logos are property of their respective owners.</span></span>

>[!div class="step-by-step"]
>[<span data-ttu-id="bdda3-215">Další</span><span class="sxs-lookup"><span data-stu-id="bdda3-215">Next</span></span>](container-docker-introduction/index.md)
