---
title: Mikroslužby .NET. Architektura pro Kontejnerizované aplikace .NET
description: Architektura Mikroslužeb .NET pro Kontejnerizované aplikace .NET | Mikroslužby jsou modulární a umožňují nezávislé nasazení služby. Kontejnery dockeru (pro systémy Linux a Windows) zjednodušit nasazování a testování seskupí služby a jeho závislosti do jedné jednotky, které je potom spouštět v izolovaném prostředí.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 06/06/2018
ms.openlocfilehash: 6b57f66068409ade24eecff636b9dd3f4084fd71
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43516148"
---
![](./media/cover.png)

# <a name="net-microservices-architecture-for-containerized-net-applications"></a><span data-ttu-id="283b2-105">Mikroslužby .NET.</span><span class="sxs-lookup"><span data-stu-id="283b2-105">.NET Microservices.</span></span> <span data-ttu-id="283b2-106">Architektura pro Kontejnerizované aplikace .NET</span><span class="sxs-lookup"><span data-stu-id="283b2-106">Architecture for Containerized .NET Applications</span></span>

<span data-ttu-id="283b2-107">Ke stažení je k dispozici na: <https://aka.ms/microservicesebook></span><span class="sxs-lookup"><span data-stu-id="283b2-107">DOWNLOAD available at: <https://aka.ms/microservicesebook></span></span>

<span data-ttu-id="283b2-108">PUBLIKOVAL(A)</span><span class="sxs-lookup"><span data-stu-id="283b2-108">PUBLISHED BY</span></span>

<span data-ttu-id="283b2-109">Microsoft Developer Division, .NET a Visual Studio produktových týmů</span><span class="sxs-lookup"><span data-stu-id="283b2-109">Microsoft Developer Division, .NET and Visual Studio product teams</span></span>

<span data-ttu-id="283b2-110">Divize Microsoft Corporation.</span><span class="sxs-lookup"><span data-stu-id="283b2-110">A division of Microsoft Corporation</span></span>

<span data-ttu-id="283b2-111">One Microsoft Way</span><span class="sxs-lookup"><span data-stu-id="283b2-111">One Microsoft Way</span></span>

<span data-ttu-id="283b2-112">Redmond, Washington 98052-6399</span><span class="sxs-lookup"><span data-stu-id="283b2-112">Redmond, Washington 98052-6399</span></span>

<span data-ttu-id="283b2-113">Copyright © 2018 Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="283b2-113">Copyright © 2018 by Microsoft Corporation</span></span>

<span data-ttu-id="283b2-114">Všechna práva vyhrazena.</span><span class="sxs-lookup"><span data-stu-id="283b2-114">All rights reserved.</span></span> <span data-ttu-id="283b2-115">Žádná část obsahu této knihy může reprodukovat nebo v libovolné formě nebo jakýmikoli prostředky bez písemného souhlasu vydavatele.</span><span class="sxs-lookup"><span data-stu-id="283b2-115">No part of the contents of this book may be reproduced or transmitted in any form or by any means without the written permission of the publisher.</span></span>

<span data-ttu-id="283b2-116">Tato kniha je k dispozici "jako-je" a vyjadřuje zobrazení autora a názory.</span><span class="sxs-lookup"><span data-stu-id="283b2-116">This book is provided “as-is” and expresses the author’s views and opinions.</span></span> <span data-ttu-id="283b2-117">Zobrazení, názory a informace v této knize, včetně adres URL a jiných odkazů na internetové weby, mohou změnit bez předchozího upozornění.</span><span class="sxs-lookup"><span data-stu-id="283b2-117">The views, opinions and information expressed in this book, including URL and other Internet website references, may change without notice.</span></span>

<span data-ttu-id="283b2-118">Některé zde uvedené příklady jsou k dispozici pouze pro ilustraci a jsou smyšlené.</span><span class="sxs-lookup"><span data-stu-id="283b2-118">Some examples depicted herein are provided for illustration only and are fictitious.</span></span> <span data-ttu-id="283b2-119">Žádný skutečný vztah nebo spojení ani je určena ji vyvozovat.</span><span class="sxs-lookup"><span data-stu-id="283b2-119">No real association or connection is intended or should be inferred.</span></span>

<span data-ttu-id="283b2-120">Microsoft a ochranné známky uvedený na http://www.microsoft.com na webové stránce "Ochranné známky" jsou obchodní známky společností skupiny Microsoft.</span><span class="sxs-lookup"><span data-stu-id="283b2-120">Microsoft and the trademarks listed at http://www.microsoft.com on the “Trademarks” webpage are trademarks of the Microsoft group of companies.</span></span>

<span data-ttu-id="283b2-121">Mac a macOS jsou ochranné známky společnosti Apple Inc.</span><span class="sxs-lookup"><span data-stu-id="283b2-121">Mac and macOS are trademarks of Apple Inc.</span></span>

<span data-ttu-id="283b2-122">Velryba logo Dockeru je registrovaná ochranná známka společnosti Docker, Inc. Použít oprávnění.</span><span class="sxs-lookup"><span data-stu-id="283b2-122">The Docker whale logo is a registered trademark of Docker, Inc. Used by permission.</span></span>

<span data-ttu-id="283b2-123">Všechny ostatní značky a loga jsou majetkem příslušných vlastníků.</span><span class="sxs-lookup"><span data-stu-id="283b2-123">All other marks and logos are property of their respective owners.</span></span>

<span data-ttu-id="283b2-124">Spoluautoři:</span><span class="sxs-lookup"><span data-stu-id="283b2-124">Co-Authors:</span></span>

> <span data-ttu-id="283b2-125">**De la Torre Cesarovi**, vyšší ODP., .NET produktový tým Microsoft Corp.</span><span class="sxs-lookup"><span data-stu-id="283b2-125">**Cesar de la Torre**, Sr. PM, .NET product team, Microsoft Corp.</span></span>
>
> <span data-ttu-id="283b2-126">**Bill Wagnera**, vyšší Obsahu pro vývojáře v jazyce C + E, Microsoft Corp.</span><span class="sxs-lookup"><span data-stu-id="283b2-126">**Bill Wagner**, Sr. Content Developer, C+E, Microsoft Corp.</span></span>
>
> <span data-ttu-id="283b2-127">**Mike Rousos**, hlavní softwarový inženýr, týmu DevDiv CAT, Microsoft</span><span class="sxs-lookup"><span data-stu-id="283b2-127">**Mike Rousos**, Principal Software Engineer, DevDiv CAT team, Microsoft</span></span>

<span data-ttu-id="283b2-128">Editory:</span><span class="sxs-lookup"><span data-stu-id="283b2-128">Editors:</span></span>

> <span data-ttu-id="283b2-129">**Mike Pope**</span><span class="sxs-lookup"><span data-stu-id="283b2-129">**Mike Pope**</span></span>
>
> <span data-ttu-id="283b2-130">**Steve Hoag**</span><span class="sxs-lookup"><span data-stu-id="283b2-130">**Steve Hoag**</span></span>

<span data-ttu-id="283b2-131">Účastníci a recenzenti:</span><span class="sxs-lookup"><span data-stu-id="283b2-131">Participants and reviewers:</span></span>

> <span data-ttu-id="283b2-132">**Jeffrey Richter**, Partner softwaru Eng týmu Azure, Microsoft</span><span class="sxs-lookup"><span data-stu-id="283b2-132">**Jeffrey Richter**, Partner Software Eng, Azure team, Microsoft</span></span>
>
> <span data-ttu-id="283b2-133">**Jimmy Bogard**, hlavní architekt na Headspring</span><span class="sxs-lookup"><span data-stu-id="283b2-133">**Jimmy Bogard**, Chief Architect at Headspring</span></span>
>
> <span data-ttu-id="283b2-134">**UDI Dahan**, Zakladatel a generální ředitel, určitého softwaru</span><span class="sxs-lookup"><span data-stu-id="283b2-134">**Udi Dahan**, Founder & CEO, Particular Software</span></span>
>
> <span data-ttu-id="283b2-135">**Jimmy Nilsson**, Spoluzakladatel a generální Factor10</span><span class="sxs-lookup"><span data-stu-id="283b2-135">**Jimmy Nilsson**, Co-founder and CEO of Factor10</span></span>
>
> <span data-ttu-id="283b2-136">**Glenn Condron**, vyšší Programový manažer týmu ASP.NET</span><span class="sxs-lookup"><span data-stu-id="283b2-136">**Glenn Condron**, Sr. Program Manager, ASP.NET team</span></span>
>
> <span data-ttu-id="283b2-137">**Označit Fussell**, hlavní Projektový manažer zájemce, tým Azure Service Fabric, Microsoft</span><span class="sxs-lookup"><span data-stu-id="283b2-137">**Mark Fussell**, Principal PM Lead, Azure Service Fabric team, Microsoft</span></span>
>
> <span data-ttu-id="283b2-138">**Diego Vega**, PM zájemce, Entity Framework týmu, Microsoft</span><span class="sxs-lookup"><span data-stu-id="283b2-138">**Diego Vega**, PM Lead, Entity Framework team, Microsoft</span></span>
>
> <span data-ttu-id="283b2-139">**Jiří Dorrans**, vyšší Zabezpečení programový manažer</span><span class="sxs-lookup"><span data-stu-id="283b2-139">**Barry Dorrans**, Sr. Security Program Manager</span></span>
>
> <span data-ttu-id="283b2-140">**Rowan Miller**, vyšší Programový manažer Microsoftu</span><span class="sxs-lookup"><span data-stu-id="283b2-140">**Rowan Miller**, Sr. Program Manager, Microsoft</span></span>
>
> <span data-ttu-id="283b2-141">**Ankit Asthana**, hlavní manažer PM, týmu .NET, Microsoft</span><span class="sxs-lookup"><span data-stu-id="283b2-141">**Ankit Asthana**, Principal PM Manager, .NET team, Microsoft</span></span>
>
> <span data-ttu-id="283b2-142">**Scott Hunter**, Partner Director oddělení PM, týmu .NET, Microsoft</span><span class="sxs-lookup"><span data-stu-id="283b2-142">**Scott Hunter**, Partner Director PM, .NET team, Microsoft</span></span>
>
> <span data-ttu-id="283b2-143">**Dylan Reisenberger**, architekt a vedoucí vývoje v Polly</span><span class="sxs-lookup"><span data-stu-id="283b2-143">**Dylan Reisenberger**, Architect and Dev Lead at Polly</span></span>
>
> <span data-ttu-id="283b2-144">**Steve Smith**, Tvůrce softwaru & Trainer na ASPSmith Ltd.</span><span class="sxs-lookup"><span data-stu-id="283b2-144">**Steve Smith**, Software Craftsman & Trainer at ASPSmith Ltd.</span></span>
>
> <span data-ttu-id="283b2-145">**Ian Cooper**, kódování navrhovat jasnější na</span><span class="sxs-lookup"><span data-stu-id="283b2-145">**Ian Cooper**, Coding Architect at Brighter</span></span>
>
> <span data-ttu-id="283b2-146">**Unai Zorrilla**, architekt a vedoucí vývoje v Plain Concepts</span><span class="sxs-lookup"><span data-stu-id="283b2-146">**Unai Zorrilla**, Architect and Dev Lead at Plain Concepts</span></span>
>
> <span data-ttu-id="283b2-147">**Eduard Tomáši**, vedoucí vývoje v Plain Concepts</span><span class="sxs-lookup"><span data-stu-id="283b2-147">**Eduard Tomas**, Dev Lead at Plain Concepts</span></span>
>
> <span data-ttu-id="283b2-148">**Ramon Tomáši**, vývojář v Plain Concepts</span><span class="sxs-lookup"><span data-stu-id="283b2-148">**Ramon Tomas**, Developer at Plain Concepts</span></span>
>
> <span data-ttu-id="283b2-149">**David Sanz**, vývojář v Plain Concepts</span><span class="sxs-lookup"><span data-stu-id="283b2-149">**David Sanz**, Developer at Plain Concepts</span></span>
>
> <span data-ttu-id="283b2-150">**Javier Valero**, hlavní, provozní ředitel ve Grupo řešení</span><span class="sxs-lookup"><span data-stu-id="283b2-150">**Javier Valero**, Chief Operating Officer at Grupo Solutio</span></span>
>
> <span data-ttu-id="283b2-151">**Pierre proso**, vyšší Konzultant, Microsoft</span><span class="sxs-lookup"><span data-stu-id="283b2-151">**Pierre Millet**, Sr. Consultant, Microsoft</span></span>
>
> <span data-ttu-id="283b2-152">**Michael Friis**, správce produktu, Inc Dockeru</span><span class="sxs-lookup"><span data-stu-id="283b2-152">**Michael Friis**, Product Manager, Docker Inc</span></span>
>
> <span data-ttu-id="283b2-153">**Charles Lowell**, softwarový inženýr, týmu VS CAT, Microsoft</span><span class="sxs-lookup"><span data-stu-id="283b2-153">**Charles Lowell**, Software Engineer, VS CAT team, Microsoft</span></span>

## <a name="introduction"></a><span data-ttu-id="283b2-154">Úvod</span><span class="sxs-lookup"><span data-stu-id="283b2-154">Introduction</span></span>

<span data-ttu-id="283b2-155">Podniky jsou stále porozumění úspory nákladů, řešení problémů s nasazením a zlepšení operace DevOps a produkčním prostředí pomocí kontejnerů.</span><span class="sxs-lookup"><span data-stu-id="283b2-155">Enterprises are increasingly realizing cost savings, solving deployment problems, and improving DevOps and production operations by using containers.</span></span> <span data-ttu-id="283b2-156">Microsoft má byla uvolnění inovace kontejner pro Windows a Linux tak, že vytvoříte produkty, jako je Azure Container Service a Azure Service Fabric a díky partnerství s vedoucím postavením, jako je Docker, Mesosphere a Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="283b2-156">Microsoft has been releasing container innovations for Windows and Linux by creating products like Azure Container Service and Azure Service Fabric, and by partnering with industry leaders like Docker, Mesosphere, and Kubernetes.</span></span> <span data-ttu-id="283b2-157">Tyto produkty poskytovat kontejneru řešení, která pomáhají společnostem sestavovat a nasazovat aplikace v cloudu rychlost a škálování, kterou si sami vyberou platformy nebo nástroje.</span><span class="sxs-lookup"><span data-stu-id="283b2-157">These products deliver container solutions that help companies build and deploy applications at cloud speed and scale, whatever their choice of platform or tools.</span></span>

<span data-ttu-id="283b2-158">Docker je stále de facto standardem v odvětví kontejneru, podporovány jsou nejdůležitější dodavatelé v ekosystémů Windows a Linux.</span><span class="sxs-lookup"><span data-stu-id="283b2-158">Docker is becoming the de facto standard in the container industry, supported by the most significant vendors in the Windows and Linux ecosystems.</span></span> <span data-ttu-id="283b2-159">(Microsoft je hlavní cloudových vendorů, podporu Dockeru.) V budoucích verzích Dockeru bude pravděpodobně všudypřítomná v libovolné datacentrum do cloudu nebo lokálně.</span><span class="sxs-lookup"><span data-stu-id="283b2-159">(Microsoft is one of the main cloud vendors supporting Docker.) In the future, Docker will probably be ubiquitous in any datacenter in the cloud or on-premises.</span></span>

<span data-ttu-id="283b2-160">Kromě toho [mikroslužeb](https://martinfowler.com/articles/microservices.html) architektura je nově vznikající jako důležité přístup pro distribuované klíčové aplikace.</span><span class="sxs-lookup"><span data-stu-id="283b2-160">In addition, the [microservices](https://martinfowler.com/articles/microservices.html) architecture is emerging as an important approach for distributed mission-critical applications.</span></span> <span data-ttu-id="283b2-161">V architektuře s využitím mikroslužeb je aplikace sestavená u kolekce služeb, které mohou být vytvořeny, otestovat, nasazené a systémovou správou verzí nezávisle na sobě.</span><span class="sxs-lookup"><span data-stu-id="283b2-161">In a microservice-based architecture, the application is built on a collection of services that can be developed, tested, deployed, and versioned independently.</span></span>

## <a name="about-this-guide"></a><span data-ttu-id="283b2-162">Informace o této příručce</span><span class="sxs-lookup"><span data-stu-id="283b2-162">About this guide</span></span>

<span data-ttu-id="283b2-163">Tato příručka slouží jako úvod k vývoji aplikací založených na mikroslužbách a správu kontejnerů.</span><span class="sxs-lookup"><span data-stu-id="283b2-163">This guide is an introduction to developing microservices-based applications and managing them using containers.</span></span> <span data-ttu-id="283b2-164">Tento článek popisuje kontrol architektonického návrhu a implementace přístupy pomocí .NET Core a kontejnery Dockeru.</span><span class="sxs-lookup"><span data-stu-id="283b2-164">It discusses architectural design and implementation approaches using .NET Core and Docker containers.</span></span> <span data-ttu-id="283b2-165">Aby bylo snazší začít pracovat s kontejnery a mikroslužby, průvodce se zaměřuje na odkaz kontejnerizovaných a aplikací založených na mikroslužbách, kterou můžete prozkoumat.</span><span class="sxs-lookup"><span data-stu-id="283b2-165">To make it easier to get started with containers and microservices, the guide focuses on a reference containerized and microservice-based application that you can explore.</span></span> <span data-ttu-id="283b2-166">Ukázková aplikace je k dispozici na [aplikaci eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) úložiště GitHub.</span><span class="sxs-lookup"><span data-stu-id="283b2-166">The sample application is available at the [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) GitHub repo.</span></span>

<span data-ttu-id="283b2-167">Tato příručka obsahuje základní vývoj a doprovodné materiály k architektuře primárně na úrovni prostředí vývoj se zaměřením na technologie: Docker a .NET Core.</span><span class="sxs-lookup"><span data-stu-id="283b2-167">This guide provides foundational development and architectural guidance primarily at a development environment level with a focus on two technologies: Docker and .NET Core.</span></span> <span data-ttu-id="283b2-168">Naším úmyslem je, že si přečtete tuto příručku při posuzování návrhu aplikace, nemusíte se soustředit na infrastrukturu (v cloudu nebo místních) vašeho produkčního prostředí.</span><span class="sxs-lookup"><span data-stu-id="283b2-168">Our intention is that you read this guide when thinking about your application design without focusing on the infrastructure (cloud or on-premises) of your production environment.</span></span> <span data-ttu-id="283b2-169">Bude rozhodnutí o infrastruktuře později, při vytváření aplikace připravené pro produkční prostředí.</span><span class="sxs-lookup"><span data-stu-id="283b2-169">You will make decisions about your infrastructure later, when you create your production-ready applications.</span></span> <span data-ttu-id="283b2-170">Proto tato příručka je určena být nezávislá a více vývojové prostředí – zaměřené na infrastrukturu.</span><span class="sxs-lookup"><span data-stu-id="283b2-170">Therefore, this guide is intended to be infrastructure agnostic and more development-environment-centric.</span></span>

<span data-ttu-id="283b2-171">Po zkoumali této příručce, bude dalším krokem je další informace o mikroslužbách připravené pro produkční prostředí v Microsoft Azure.</span><span class="sxs-lookup"><span data-stu-id="283b2-171">After you have studied this guide, your next step would be to learn about production-ready microservices on Microsoft Azure.</span></span>

## <a name="what-this-guide-does-not-cover"></a><span data-ttu-id="283b2-172">Co tato příručka nepopisuje</span><span class="sxs-lookup"><span data-stu-id="283b2-172">What this guide does not cover</span></span>

<span data-ttu-id="283b2-173">Tato příručka se nezaměřuje na životního cyklu aplikací, vývoj a provoz kanálů CI/CD nebo tým pracovat.</span><span class="sxs-lookup"><span data-stu-id="283b2-173">This guide does not focus on the application lifecycle, DevOps, CI/CD pipelines, or team work.</span></span> <span data-ttu-id="283b2-174">Doplňkové průvodce [Kontejnerizovaných životní cyklus aplikace Dockeru s platformou a nástroji Microsoft](https://aka.ms/dockerlifecycleebook) se zaměřuje na tohoto subjektu.</span><span class="sxs-lookup"><span data-stu-id="283b2-174">The complementary guide [Containerized Docker Application Lifecycle with Microsoft Platform and Tools](https://aka.ms/dockerlifecycleebook) focuses on that subject.</span></span> <span data-ttu-id="283b2-175">Aktuální Průvodce také neposkytuje podrobné informace o implementaci na infrastrukturu Azure, jako je například informace o konkrétní orchestrátorů.</span><span class="sxs-lookup"><span data-stu-id="283b2-175">The current guide also does not provide implementation details on Azure infrastructure, such as information on specific orchestrators.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="283b2-176">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="283b2-176">Additional resources</span></span>

-   <span data-ttu-id="283b2-177">**Životní cyklus aplikace Dockeru s platformou a nástroji Microsoft kontejnerizovaných** (ke stažení e kniha) [*https://aka.ms/dockerlifecycleebook*](https://aka.ms/dockerlifecycleebook)</span><span class="sxs-lookup"><span data-stu-id="283b2-177">**Containerized Docker Application Lifecycle with Microsoft Platform and Tools** (downloadable e-book) [*https://aka.ms/dockerlifecycleebook*](https://aka.ms/dockerlifecycleebook)</span></span>

## <a name="who-should-use-this-guide"></a><span data-ttu-id="283b2-178">Kdo by měl používat tohoto průvodce</span><span class="sxs-lookup"><span data-stu-id="283b2-178">Who should use this guide</span></span>

<span data-ttu-id="283b2-179">Jsme napsali Tato příručka pro vývojáře a architekty řešení, kteří jsou nové pro vývoj aplikací založených na Dockeru a architektura založená na mikroslužbách.</span><span class="sxs-lookup"><span data-stu-id="283b2-179">We wrote this guide for developers and solution architects who are new to Docker-based application development and to microservices-based architecture.</span></span> <span data-ttu-id="283b2-180">Tento průvodce je pro, pokud chcete získat informace tom, jak navrhovat, navrhování a implementace aplikací testování konceptu s vývojovým technologiím Microsoftu (se zvláštním zaměřením na .NET Core) a s kontejnery Dockeru.</span><span class="sxs-lookup"><span data-stu-id="283b2-180">This guide is for you if you want to learn how to architect, design, and implement proof-of-concept applications with Microsoft development technologies (with special focus on .NET Core) and with Docker containers.</span></span>

<span data-ttu-id="283b2-181">Také zjistíte Tato příručka užitečné, pokud jste technický pracovník s rozhodovací pravomocí, jako je například podnikový architekt, kdo chce, aby se architektura a přehledu technologie před rozhodnout, na jaké přístup k výběru pro nové a moderní distribuované aplikace.</span><span class="sxs-lookup"><span data-stu-id="283b2-181">You will also find this guide useful if you are a technical decision maker, such as an enterprise architect, who wants an architecture and technology overview before you decide on what approach to select for new and modern distributed applications.</span></span>

### <a name="how-to-use-this-guide"></a><span data-ttu-id="283b2-182">Jak používat tohoto průvodce</span><span class="sxs-lookup"><span data-stu-id="283b2-182">How to use this guide</span></span>

<span data-ttu-id="283b2-183">První části této příručky zavádí kontejnery Dockeru, popisuje, jak si vybrat mezi .NET Core a .NET Framework jako rozhraní pro vývoj a najdete zde přehled mikroslužeb.</span><span class="sxs-lookup"><span data-stu-id="283b2-183">The first part of this guide introduces Docker containers, discusses how to choose between .NET Core and the .NET Framework as a development framework, and provides an overview of microservices.</span></span> <span data-ttu-id="283b2-184">Tento obsah je pro architekty a technické rozhodovací pravomocí, kteří chtějí přehled, ale nemusíte zaměřit se na podrobnosti implementace kódu.</span><span class="sxs-lookup"><span data-stu-id="283b2-184">This content is for architects and technical decision makers who want an overview but who do not need to focus on code implementation details.</span></span>

<span data-ttu-id="283b2-185">Začíná druhé části v průvodci [aplikací založených na proces vývoje pro Docker](#ch_dev_process_for_docker_based_apps) oddílu.</span><span class="sxs-lookup"><span data-stu-id="283b2-185">The second part of the guide starts with the [Development process for Docker based applications](#ch_dev_process_for_docker_based_apps) section.</span></span> <span data-ttu-id="283b2-186">Zaměřuje se na vývoj a mikroslužeb vzory pro provádění aplikací pomocí .NET Core a Docker.</span><span class="sxs-lookup"><span data-stu-id="283b2-186">It focuses on development and microservice patterns for implementing applications using .NET Core and Docker.</span></span> <span data-ttu-id="283b2-187">Tato část bude mít největší zájem vývojářům a architektům, kteří chtějí soustředit se na kód a vzorců a podrobnosti implementace.</span><span class="sxs-lookup"><span data-stu-id="283b2-187">This section will be of most interest to developers and architects who want to focus on code and on patterns and implementation details.</span></span>

## <a name="related-microservice-and-container-based-reference-application-eshoponcontainers"></a><span data-ttu-id="283b2-188">Související mikroslužby a aplikace založené na kontejnerech odkaz: aplikaci eShopOnContainers</span><span class="sxs-lookup"><span data-stu-id="283b2-188">Related microservice and container-based reference application: eShopOnContainers</span></span>

<span data-ttu-id="283b2-189">Aplikaci eShopOnContainers aplikace je odkaz na aplikaci pro .NET Core a mikroslužeb, která slouží k nasazení kontejnerů Dockeru.</span><span class="sxs-lookup"><span data-stu-id="283b2-189">The eShopOnContainers application is a reference app for .NET Core and microservices that is designed to be deployed using Docker containers.</span></span> <span data-ttu-id="283b2-190">Aplikace se skládá z více subsystémů, včetně několik e-store uživatelského rozhraní front-endů (Web app a nativní mobilní aplikace).</span><span class="sxs-lookup"><span data-stu-id="283b2-190">The application consists of multiple subsystems, including several e-store UI front ends (a Web app and a native mobile app).</span></span> <span data-ttu-id="283b2-191">Zahrnuje také back-end mikroslužeb a kontejnerů pro všechny požadované operace na straně serveru.</span><span class="sxs-lookup"><span data-stu-id="283b2-191">It also includes the back-end microservices and containers for all required server-side operations.</span></span>

<span data-ttu-id="283b2-192">Tento mikroslužby a aplikace založené na kontejnerech zdrojový kód je open source a je k dispozici na [aplikaci eShopOnContainers](https://aka.ms/MicroservicesArchitecture) úložiště GitHub.</span><span class="sxs-lookup"><span data-stu-id="283b2-192">This microservice and container-based application source code is open source and available at the [eShopOnContainers](https://aka.ms/MicroservicesArchitecture) GitHub repo.</span></span>

## <a name="send-us-your-feedback"></a><span data-ttu-id="283b2-193">Pošlete nám svůj názor!</span><span class="sxs-lookup"><span data-stu-id="283b2-193">Send us your feedback!</span></span>

<span data-ttu-id="283b2-194">Jsme napsali této příručce, které vám pomůžou porozumět architektuře mikroslužeb v rozhraní .NET a kontejnerizovaných aplikací.</span><span class="sxs-lookup"><span data-stu-id="283b2-194">We wrote this guide to help you understand the architecture of containerized applications and microservices in .NET.</span></span> <span data-ttu-id="283b2-195">Průvodce a související referenční aplikace bude se vyvíjí, takže vaše připomínky budou vítány!</span><span class="sxs-lookup"><span data-stu-id="283b2-195">The guide and related reference application will be evolving, so we welcome your feedback!</span></span> <span data-ttu-id="283b2-196">Pokud máte připomínky jak se tento průvodce může zlepšit, odešlete jim:</span><span class="sxs-lookup"><span data-stu-id="283b2-196">If you have comments about how this guide can be improved, please send them to:</span></span>

[dotnet-architecture-ebooks-feedback@service.microsoft.com](mailto:dotnet-architecture-ebooks-feedback@service.microsoft.com)

>[!div class="step-by-step"]
[<span data-ttu-id="283b2-197">Next</span><span class="sxs-lookup"><span data-stu-id="283b2-197">Next</span></span>](container-docker-introduction/index.md)
