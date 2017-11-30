---
title: "Rozhraní .NET Mikroslužeb. Architektura pro aplikace .NET Kontejnerizované"
description: "Architektura Mikroslužeb .NET pro aplikace .NET Kontejnerizované | Úvodní část"
keywords: "Docker, Mikroslužeb, ASP.NET, kontejneru"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: f869656be4c211c9b028f8ac574eb3bf2de139e2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
![](./media/cover.png)

# <a name="net-microservices-architecture-for-containerized-net-applications"></a><span data-ttu-id="7adc7-105">Rozhraní .NET Mikroslužeb.</span><span class="sxs-lookup"><span data-stu-id="7adc7-105">.NET Microservices.</span></span> <span data-ttu-id="7adc7-106">Architektura pro aplikace .NET Kontejnerizované</span><span class="sxs-lookup"><span data-stu-id="7adc7-106">Architecture for Containerized .NET Applications</span></span>

<span data-ttu-id="7adc7-107">STAŽENÍ, které jsou k dispozici na: <https://aka.ms/microservicesebook></span><span class="sxs-lookup"><span data-stu-id="7adc7-107">DOWNLOAD available at: <https://aka.ms/microservicesebook></span></span>

<span data-ttu-id="7adc7-108">PUBLIKOVÁNO</span><span class="sxs-lookup"><span data-stu-id="7adc7-108">PUBLISHED BY</span></span>

<span data-ttu-id="7adc7-109">Týmy pro produkt Microsoft Developer dělení, rozhraní .NET a Visual Studio</span><span class="sxs-lookup"><span data-stu-id="7adc7-109">Microsoft Developer Division, .NET and Visual Studio product teams</span></span>

<span data-ttu-id="7adc7-110">Dělení společnosti Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="7adc7-110">A division of Microsoft Corporation</span></span>

<span data-ttu-id="7adc7-111">One Microsoft Way</span><span class="sxs-lookup"><span data-stu-id="7adc7-111">One Microsoft Way</span></span>

<span data-ttu-id="7adc7-112">Redmond, Washington 98052-6399</span><span class="sxs-lookup"><span data-stu-id="7adc7-112">Redmond, Washington 98052-6399</span></span>

<span data-ttu-id="7adc7-113">Copyright © Microsoft Corporation 2017</span><span class="sxs-lookup"><span data-stu-id="7adc7-113">Copyright © 2017 by Microsoft Corporation</span></span>

<span data-ttu-id="7adc7-114">Všechna práva vyhrazena.</span><span class="sxs-lookup"><span data-stu-id="7adc7-114">All rights reserved.</span></span> <span data-ttu-id="7adc7-115">Žádná z částí obsah této příručky je možné reprodukovat nebo přenést v žádný formulář nebo žádnými prostředky bez předchozího písemného souhlasu vydavatele.</span><span class="sxs-lookup"><span data-stu-id="7adc7-115">No part of the contents of this book may be reproduced or transmitted in any form or by any means without the written permission of the publisher.</span></span>

<span data-ttu-id="7adc7-116">Tato kniha je k dispozici "jako-je" a vyjadřoval zobrazení a názory vytvářením obsahu.</span><span class="sxs-lookup"><span data-stu-id="7adc7-116">This book is provided “as-is” and expresses the author’s views and opinions.</span></span> <span data-ttu-id="7adc7-117">Zobrazení, názory a informace v této příručce, včetně adres URL a dalších odkazů na internetové weby, mohou změnit bez předchozího upozornění.</span><span class="sxs-lookup"><span data-stu-id="7adc7-117">The views, opinions and information expressed in this book, including URL and other Internet website references, may change without notice.</span></span>

<span data-ttu-id="7adc7-118">Některé příklady použité v ukázkách jsou jenom ilustrativní a smyšlené.</span><span class="sxs-lookup"><span data-stu-id="7adc7-118">Some examples depicted herein are provided for illustration only and are fictitious.</span></span> <span data-ttu-id="7adc7-119">Žádný skutečný vztah nebo připojení je určený nebo událostmi.</span><span class="sxs-lookup"><span data-stu-id="7adc7-119">No real association or connection is intended or should be inferred.</span></span>

<span data-ttu-id="7adc7-120">Microsoft a ochranné známky uvedené http://www.microsoft.com na webové stránce "Ochranné známky" jsou obchodní známky společností skupiny Microsoft.</span><span class="sxs-lookup"><span data-stu-id="7adc7-120">Microsoft and the trademarks listed at http://www.microsoft.com on the “Trademarks” webpage are trademarks of the Microsoft group of companies.</span></span>

<span data-ttu-id="7adc7-121">Mac a systému macOS jsou ochranné známky společnosti Apple, Inc.</span><span class="sxs-lookup"><span data-stu-id="7adc7-121">Mac and macOS are trademarks of Apple Inc.</span></span>

<span data-ttu-id="7adc7-122">Logo velryba Docker je registrovaná ochranná známka společnosti Docker, Inc. Pomocí oprávnění.</span><span class="sxs-lookup"><span data-stu-id="7adc7-122">The Docker whale logo is a registered trademark of Docker, Inc. Used by permission.</span></span>

<span data-ttu-id="7adc7-123">Všechny ostatní značky a loga jsou vlastnictvím příslušných vlastníků.</span><span class="sxs-lookup"><span data-stu-id="7adc7-123">All other marks and logos are property of their respective owners.</span></span>

<span data-ttu-id="7adc7-124">Spoluautoři:</span><span class="sxs-lookup"><span data-stu-id="7adc7-124">Co-Authors:</span></span>

> <span data-ttu-id="7adc7-125">**Cesaru členka Torre**, Sr. PM, .NET produktový tým Microsoft Corp.</span><span class="sxs-lookup"><span data-stu-id="7adc7-125">**Cesar de la Torre**, Sr. PM, .NET product team, Microsoft Corp.</span></span>
>
> <span data-ttu-id="7adc7-126">**Faktury Wagnera**, Sr. Obsahu Developer, C + E, Microsoft Corp.</span><span class="sxs-lookup"><span data-stu-id="7adc7-126">**Bill Wagner**, Sr. Content Developer, C+E, Microsoft Corp.</span></span>
>
> <span data-ttu-id="7adc7-127">**Jan Rousos**, hlavní softwaru pracovníka, týmu DevDiv CAT, Microsoft</span><span class="sxs-lookup"><span data-stu-id="7adc7-127">**Mike Rousos**, Principal Software Engineer, DevDiv CAT team, Microsoft</span></span>

<span data-ttu-id="7adc7-128">Editory:</span><span class="sxs-lookup"><span data-stu-id="7adc7-128">Editors:</span></span>

> <span data-ttu-id="7adc7-129">**Jan Pope**</span><span class="sxs-lookup"><span data-stu-id="7adc7-129">**Mike Pope**</span></span>
>
> <span data-ttu-id="7adc7-130">**Steve Hoag**</span><span class="sxs-lookup"><span data-stu-id="7adc7-130">**Steve Hoag**</span></span>

<span data-ttu-id="7adc7-131">Účastníci a recenzenti:</span><span class="sxs-lookup"><span data-stu-id="7adc7-131">Participants and reviewers:</span></span>

> <span data-ttu-id="7adc7-132">**Jana Ritcher**, Eng softwaru partnera, tým Azure, Microsoft</span><span class="sxs-lookup"><span data-stu-id="7adc7-132">**Jeffrey Ritcher**, Partner Software Eng, Azure team, Microsoft</span></span>
>
> <span data-ttu-id="7adc7-133">**Jimmy Bogard**, hlavní architekt v Headspring</span><span class="sxs-lookup"><span data-stu-id="7adc7-133">**Jimmy Bogard**, Chief Architect at Headspring</span></span>
>
> <span data-ttu-id="7adc7-134">**UDI Dahan**, zakladatele & CEO, určitého softwaru</span><span class="sxs-lookup"><span data-stu-id="7adc7-134">**Udi Dahan**, Founder & CEO, Particular Software</span></span>
>
> <span data-ttu-id="7adc7-135">**Jimmy Nilsson**, společné zakladatele a CEO Factor10</span><span class="sxs-lookup"><span data-stu-id="7adc7-135">**Jimmy Nilsson**, Co-founder and CEO of Factor10</span></span>
>
> <span data-ttu-id="7adc7-136">**Glenn Condron**, Sr. Manažer programu ASP.NET team</span><span class="sxs-lookup"><span data-stu-id="7adc7-136">**Glenn Condron**, Sr. Program Manager, ASP.NET team</span></span>
>
> <span data-ttu-id="7adc7-137">**Označit Fussell**, hlavní PM realizace, tým Azure Service Fabric, Microsoft</span><span class="sxs-lookup"><span data-stu-id="7adc7-137">**Mark Fussell**, Principal PM Lead, Azure Service Fabric team, Microsoft</span></span>
>
> <span data-ttu-id="7adc7-138">**Diego Vega**, PM realizace, rozhraní Entity Framework tým Microsoft</span><span class="sxs-lookup"><span data-stu-id="7adc7-138">**Diego Vega**, PM Lead, Entity Framework team, Microsoft</span></span>
>
> <span data-ttu-id="7adc7-139">**Jiří Dorrans**, Sr. Program Správce zabezpečení</span><span class="sxs-lookup"><span data-stu-id="7adc7-139">**Barry Dorrans**, Sr. Security Program Manager</span></span>
>
> <span data-ttu-id="7adc7-140">**Rowan Lukeš**, Sr. Manažer programu Microsoft</span><span class="sxs-lookup"><span data-stu-id="7adc7-140">**Rowan Miller**, Sr. Program Manager, Microsoft</span></span>
>
> <span data-ttu-id="7adc7-141">**Ankit Asthana**, hlavní manažer PM, .NET tým Microsoft</span><span class="sxs-lookup"><span data-stu-id="7adc7-141">**Ankit Asthana**, Principal PM Manager, .NET team, Microsoft</span></span>
>
> <span data-ttu-id="7adc7-142">**Scott Hunter**, ředitel partnera PM, .NET tým Microsoft</span><span class="sxs-lookup"><span data-stu-id="7adc7-142">**Scott Hunter**, Partner Director PM, .NET team, Microsoft</span></span>
>
> <span data-ttu-id="7adc7-143">**Dylan Reisenberger**, architekty a vývojáře realizace v Polly</span><span class="sxs-lookup"><span data-stu-id="7adc7-143">**Dylan Reisenberger**, Architect and Dev Lead at Polly</span></span>
>
> <span data-ttu-id="7adc7-144">**Steve Smith**, Craftsman softwaru & Trainer ve ASPSmith Ltd.</span><span class="sxs-lookup"><span data-stu-id="7adc7-144">**Steve Smith**, Software Craftsman & Trainer at ASPSmith Ltd.</span></span>
>
> <span data-ttu-id="7adc7-145">**Ian Cooper**, kódování architektury v jasnější</span><span class="sxs-lookup"><span data-stu-id="7adc7-145">**Ian Cooper**, Coding Architect at Brighter</span></span>
>
> <span data-ttu-id="7adc7-146">**Unai Zorrilla**, architekty a vývojáře realizace na prostý koncepty</span><span class="sxs-lookup"><span data-stu-id="7adc7-146">**Unai Zorrilla**, Architect and Dev Lead at Plain Concepts</span></span>
>
> <span data-ttu-id="7adc7-147">**Eduard Tomáši**, Dev realizace na prostý koncepty</span><span class="sxs-lookup"><span data-stu-id="7adc7-147">**Eduard Tomas**, Dev Lead at Plain Concepts</span></span>
>
> <span data-ttu-id="7adc7-148">**Tomáši Ramon**, Developer na prostý koncepty</span><span class="sxs-lookup"><span data-stu-id="7adc7-148">**Ramon Tomas**, Developer at Plain Concepts</span></span>
>
> <span data-ttu-id="7adc7-149">**David Sanz**, Developer na prostý koncepty</span><span class="sxs-lookup"><span data-stu-id="7adc7-149">**David Sanz**, Developer at Plain Concepts</span></span>
>
> <span data-ttu-id="7adc7-150">**Javier Valero**, ředitel operační vedoucím v Grupo řešení</span><span class="sxs-lookup"><span data-stu-id="7adc7-150">**Javier Valero**, Chief Operating Officer at Grupo Solutio</span></span>
>
> <span data-ttu-id="7adc7-151">**Proso Pierre**, Sr. Poradce, Microsoft</span><span class="sxs-lookup"><span data-stu-id="7adc7-151">**Pierre Millet**, Sr. Consultant, Microsoft</span></span>
>
> <span data-ttu-id="7adc7-152">**Michael Friis**, správce produktu, Inc Docker</span><span class="sxs-lookup"><span data-stu-id="7adc7-152">**Michael Friis**, Product Manager, Docker Inc</span></span>
>
> <span data-ttu-id="7adc7-153">**Charlese Lowell**, softwaru pracovníka, týmu VS CAT, Microsoft</span><span class="sxs-lookup"><span data-stu-id="7adc7-153">**Charles Lowell**, Software Engineer, VS CAT team, Microsoft</span></span>

## <a name="introduction"></a><span data-ttu-id="7adc7-154">Úvod</span><span class="sxs-lookup"><span data-stu-id="7adc7-154">Introduction</span></span>

<span data-ttu-id="7adc7-155">Podniky jsou stále porozumění úsporu nákladů, řešení problémů s nasazením a zvýšení operace DevOps a produkční pomocí kontejnerů.</span><span class="sxs-lookup"><span data-stu-id="7adc7-155">Enterprises are increasingly realizing cost savings, solving deployment problems, and improving DevOps and production operations by using containers.</span></span> <span data-ttu-id="7adc7-156">Microsoft má byla vydává inovace kontejner pro systém Windows a Linux tak, že vytvoříte produkty, jako je Azure Container Service a Azure Service Fabric a prostřednictvím partnerských vedoucími jako Docker, Mesosphere a Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="7adc7-156">Microsoft has been releasing container innovations for Windows and Linux by creating products like Azure Container Service and Azure Service Fabric, and by partnering with industry leaders like Docker, Mesosphere, and Kubernetes.</span></span> <span data-ttu-id="7adc7-157">Tyto produkty dodat kontejneru řešení, které pomáhají společnosti sestavení a nasazení aplikací v cloudu rychlost a škálování, ať si sami vyberou platformy nebo nástrojů.</span><span class="sxs-lookup"><span data-stu-id="7adc7-157">These products deliver container solutions that help companies build and deploy applications at cloud speed and scale, whatever their choice of platform or tools.</span></span>

<span data-ttu-id="7adc7-158">Docker se stává stále de facto standardem v kontejneru odvětví, jsou nejdůležitější dodavatelé v systému Windows a Linux ekosystémů nepodporuje.</span><span class="sxs-lookup"><span data-stu-id="7adc7-158">Docker is becoming the de facto standard in the container industry, supported by the most significant vendors in the Windows and Linux ecosystems.</span></span> <span data-ttu-id="7adc7-159">(Microsoft je jeden z dodavatelů hlavní cloudu podpora Docker.) V budoucnu Docker bude pravděpodobně všudypřítomný do všech datových center v cloudu nebo místně.</span><span class="sxs-lookup"><span data-stu-id="7adc7-159">(Microsoft is one of the main cloud vendors supporting Docker.) In the future, Docker will probably be ubiquitous in any datacenter in the cloud or on-premises.</span></span>

<span data-ttu-id="7adc7-160">Kromě toho [mikroslužeb](https://martinfowler.com/articles/microservices.html) architektura je rozvíjející jako důležité přístup pro distribuované kritických aplikací.</span><span class="sxs-lookup"><span data-stu-id="7adc7-160">In addition, the [microservices](https://martinfowler.com/articles/microservices.html) architecture is emerging as an important approach for distributed mission-critical applications.</span></span> <span data-ttu-id="7adc7-161">V architektuře na základě mikroslužbu aplikace je založený na kolekce služeb, které mohou být vytvořeny, otestovat, nasazené a verzí nezávisle.</span><span class="sxs-lookup"><span data-stu-id="7adc7-161">In a microservice-based architecture, the application is built on a collection of services that can be developed, tested, deployed, and versioned independently.</span></span>

## <a name="about-this-guide"></a><span data-ttu-id="7adc7-162">Informace o této příručce</span><span class="sxs-lookup"><span data-stu-id="7adc7-162">About this guide</span></span>

<span data-ttu-id="7adc7-163">Tato příručka je Úvod k vývoji aplikace založené na mikroslužeb a jejich správě použití kontejnerů.</span><span class="sxs-lookup"><span data-stu-id="7adc7-163">This guide is an introduction to developing microservices-based applications and managing them using containers.</span></span> <span data-ttu-id="7adc7-164">Popisuje architektury návrhu a implementace blíží použití .NET Core a Docker kontejnerů.</span><span class="sxs-lookup"><span data-stu-id="7adc7-164">It discusses architectural design and implementation approaches using .NET Core and Docker containers.</span></span> <span data-ttu-id="7adc7-165">Aby bylo snazší začít pracovat s kontejnery a mikroslužeb, se v Průvodci zaměřuje na odkaz kontejnerizované a na základě mikroslužbu aplikace, kterou můžete prozkoumat.</span><span class="sxs-lookup"><span data-stu-id="7adc7-165">To make it easier to get started with containers and microservices, the guide focuses on a reference containerized and microservice-based application that you can explore.</span></span> <span data-ttu-id="7adc7-166">Ukázkové aplikace je k dispozici na [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) úložiště GitHub.</span><span class="sxs-lookup"><span data-stu-id="7adc7-166">The sample application is available at the [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) GitHub repo.</span></span>

<span data-ttu-id="7adc7-167">Tato příručka poskytuje základní vývoj a architektury pokyny především na úrovni vývoj prostředí se zaměřením na dvě technologie: Docker a .NET Core.</span><span class="sxs-lookup"><span data-stu-id="7adc7-167">This guide provides foundational development and architectural guidance primarily at a development environment level with a focus on two technologies: Docker and .NET Core.</span></span> <span data-ttu-id="7adc7-168">Naším úmyslem je čtení této příručky, pokud přemýšlíte o návrhu aplikace bez zaměřené na infrastrukturu (cloudové nebo místní) vašeho produkčního prostředí.</span><span class="sxs-lookup"><span data-stu-id="7adc7-168">Our intention is that you read this guide when thinking about your application design without focusing on the infrastructure (cloud or on-premises) of your production environment.</span></span> <span data-ttu-id="7adc7-169">Bude rozhodnutí o infrastruktuře později, při vytváření aplikace produkční prostředí.</span><span class="sxs-lookup"><span data-stu-id="7adc7-169">You will make decisions about your infrastructure later, when you create your production-ready applications.</span></span> <span data-ttu-id="7adc7-170">Proto tato příručka je určená jako infrastruktury lhostejné a více vývoj prostředí-na střed.</span><span class="sxs-lookup"><span data-stu-id="7adc7-170">Therefore, this guide is intended to be infrastructure agnostic and more development-environment-centric.</span></span>

<span data-ttu-id="7adc7-171">Po zkoumali této příručce, dalším krokem bude další informace o mikroslužeb produkční prostředí v Microsoft Azure.</span><span class="sxs-lookup"><span data-stu-id="7adc7-171">After you have studied this guide, your next step would be to learn about production-ready microservices on Microsoft Azure.</span></span>

## <a name="what-this-guide-does-not-cover"></a><span data-ttu-id="7adc7-172">Co tato příručka nepopisuje</span><span class="sxs-lookup"><span data-stu-id="7adc7-172">What this guide does not cover</span></span>

<span data-ttu-id="7adc7-173">Tato příručka není soustředit na životním cyklu aplikací DevOps, CI/CD kanály, nebo tým spolupracovat.</span><span class="sxs-lookup"><span data-stu-id="7adc7-173">This guide does not focus on the application lifecycle, DevOps, CI/CD pipelines, or team work.</span></span> <span data-ttu-id="7adc7-174">Průvodci doplňkové [Kontejnerizované Docker cyklu aplikací s Microsoft platforma a nástroje](https://aka.ms/dockerlifecycleebook) se zaměřuje na tomto subjektu.</span><span class="sxs-lookup"><span data-stu-id="7adc7-174">The complementary guide [Containerized Docker Application Lifecycle with Microsoft Platform and Tools](https://aka.ms/dockerlifecycleebook) focuses on that subject.</span></span> <span data-ttu-id="7adc7-175">Aktuální Průvodce také neposkytuje informace o implementaci na infrastrukturu Azure, jako je například informace o konkrétní orchestrators.</span><span class="sxs-lookup"><span data-stu-id="7adc7-175">The current guide also does not provide implementation details on Azure infrastructure, such as information on specific orchestrators.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="7adc7-176">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="7adc7-176">Additional resources</span></span>

-   <span data-ttu-id="7adc7-177">**Kontejnerizované Docker životního cyklu aplikací s Microsoft platforma a nástroje** (ke stažení elektronická kniha) [ *https://aka.ms/dockerlifecycleebook*](https://aka.ms/dockerlifecycleebook)</span><span class="sxs-lookup"><span data-stu-id="7adc7-177">**Containerized Docker Application Lifecycle with Microsoft Platform and Tools** (downloadable e-book) [*https://aka.ms/dockerlifecycleebook*](https://aka.ms/dockerlifecycleebook)</span></span>

## <a name="who-should-use-this-guide"></a><span data-ttu-id="7adc7-178">Tato příručka, kdo by měl používat</span><span class="sxs-lookup"><span data-stu-id="7adc7-178">Who should use this guide</span></span>

<span data-ttu-id="7adc7-179">Napsali jsme Tato příručka pro vývojáře a řešení architektům, kteří jsou nové pro vývoj aplikací na základě Docker a architektura založená na mikroslužeb.</span><span class="sxs-lookup"><span data-stu-id="7adc7-179">We wrote this guide for developers and solution architects who are new to Docker-based application development and to microservices-based architecture.</span></span> <span data-ttu-id="7adc7-180">Tato příručka je pro další informace o architektury, chcete-li navrhování a implementaci testování konceptu aplikací pomocí technologie Microsoft vývoje (s speciální aktivní .NET Core) a s Docker kontejnery.</span><span class="sxs-lookup"><span data-stu-id="7adc7-180">This guide is for you if you want to learn how to architect, design, and implement proof-of-concept applications with Microsoft development technologies (with special focus on .NET Core) and with Docker containers.</span></span>

<span data-ttu-id="7adc7-181">Je také k dispozici tato příručka užitečné, pokud jsou technické rozhodovací pravomocí, jako je například architekti enterprise, kdo chce architekturu a Přehled technologie předtím, než se rozhodnete, na jaký způsob vyberte pro nový a moderní distribuované aplikace.</span><span class="sxs-lookup"><span data-stu-id="7adc7-181">You will also find this guide useful if you are a technical decision maker, such as an enterprise architect, who wants an architecture and technology overview before you decide on what approach to select for new and modern distributed applications.</span></span>

### <a name="how-to-use-this-guide"></a><span data-ttu-id="7adc7-182">Jak používat tato příručka</span><span class="sxs-lookup"><span data-stu-id="7adc7-182">How to use this guide</span></span>

<span data-ttu-id="7adc7-183">První část tohoto průvodce uvádí Docker kontejnery, popisuje, jak si vybrat mezi .NET Core a rozhraní .NET Framework jako rozhraní pro vývoj a poskytuje přehled mikroslužeb.</span><span class="sxs-lookup"><span data-stu-id="7adc7-183">The first part of this guide introduces Docker containers, discusses how to choose between .NET Core and the .NET Framework as a development framework, and provides an overview of microservices.</span></span> <span data-ttu-id="7adc7-184">Tento obsah je pro architekty a technické vedoucím pracovníkům, kteří chtějí přehled ale nemusíte zaměřit se na podrobnosti implementace kódu.</span><span class="sxs-lookup"><span data-stu-id="7adc7-184">This content is for architects and technical decision makers who want an overview but who do not need to focus on code implementation details.</span></span>

<span data-ttu-id="7adc7-185">Druhá část průvodce začíná [procesu vývoje pro Docker aplikace založené na](#ch_dev_process_for_docker_based_apps) oddílu.</span><span class="sxs-lookup"><span data-stu-id="7adc7-185">The second part of the guide starts with the [Development process for Docker based applications](#ch_dev_process_for_docker_based_apps) section.</span></span> <span data-ttu-id="7adc7-186">Zaměřuje se na vývoj a mikroslužbu vzory pro implementaci aplikace s použitím .NET Core a Docker.</span><span class="sxs-lookup"><span data-stu-id="7adc7-186">It focuses on development and microservice patterns for implementing applications using .NET Core and Docker.</span></span> <span data-ttu-id="7adc7-187">Tato část bude většina zajímavé pro vývojáře a architektům, kteří chtějí zaměřit se na kód a na vzory a podrobnosti implementace.</span><span class="sxs-lookup"><span data-stu-id="7adc7-187">This section will be of most interest to developers and architects who want to focus on code and on patterns and implementation details.</span></span>

## <a name="related-microservice-and-container-based-reference-application-eshoponcontainers"></a><span data-ttu-id="7adc7-188">Související s mikroslužbu a aplikace na základě kontejneru odkaz: eShopOnContainers</span><span class="sxs-lookup"><span data-stu-id="7adc7-188">Related microservice and container-based reference application: eShopOnContainers</span></span>

<span data-ttu-id="7adc7-189">Aplikace eShopOnContainers je odkaz na aplikaci pro .NET Core a mikroslužeb, který slouží k nasazení pomocí Docker kontejnery.</span><span class="sxs-lookup"><span data-stu-id="7adc7-189">The eShopOnContainers application is a reference app for .NET Core and microservices that is designed to be deployed using Docker containers.</span></span> <span data-ttu-id="7adc7-190">Aplikace se skládá z několika subsystémy, včetně několik e úložiště uživatelského rozhraní front-end (webové aplikace a nativní mobilní aplikace).</span><span class="sxs-lookup"><span data-stu-id="7adc7-190">The application consists of multiple subsystems, including several e-store UI front ends (a Web app and a native mobile app).</span></span> <span data-ttu-id="7adc7-191">Zahrnuje taky mikroslužeb back-end a kontejnery pro všechny požadované operace na straně serveru.</span><span class="sxs-lookup"><span data-stu-id="7adc7-191">It also includes the back-end microservices and containers for all required server-side operations.</span></span>

<span data-ttu-id="7adc7-192">Tento mikroslužbu a aplikace založené na kontejneru zdrojový kód je open source a je k dispozici [eShopOnContainers](http://aka.ms/MicroservicesArchitecture) úložiště GitHub.</span><span class="sxs-lookup"><span data-stu-id="7adc7-192">This microservice and container-based application source code is open source and available at the [eShopOnContainers](http://aka.ms/MicroservicesArchitecture) GitHub repo.</span></span>

## <a name="send-us-your-feedback"></a><span data-ttu-id="7adc7-193">Pošlete nám svůj názor!</span><span class="sxs-lookup"><span data-stu-id="7adc7-193">Send us your feedback!</span></span>

<span data-ttu-id="7adc7-194">Napsali jsme tento průvodce vám pomůže pochopit architektura kontejnerizované aplikací a mikroslužeb v rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="7adc7-194">We wrote this guide to help you understand the architecture of containerized applications and microservices in .NET.</span></span> <span data-ttu-id="7adc7-195">Průvodce a související referenční aplikace bude mít vyvíjejí, tak Uvítáme vaše názory!</span><span class="sxs-lookup"><span data-stu-id="7adc7-195">The guide and related reference application will be evolving, so we welcome your feedback!</span></span> <span data-ttu-id="7adc7-196">Pokud máte komentáře o tom, jak je možné zlepšit této příručce, pošlete prosím, aby:</span><span class="sxs-lookup"><span data-stu-id="7adc7-196">If you have comments about how this guide can be improved, please send them to:</span></span>

[dotnet-architecture-ebooks-feedback@service.microsoft.com](mailto:dotnet-architecture-ebooks-feedback@service.microsoft.com)

>[!div class="step-by-step"]
<span data-ttu-id="7adc7-197">[Další] (kontejner docker Úvod/index.md)</span><span class="sxs-lookup"><span data-stu-id="7adc7-197">[Next] (container-docker-introduction/index.md)</span></span>
