---
title: "Architekti moderních webových aplikací pomocí ASP.NET Core a Azure"
description: "Architektury moderních webových aplikací pomocí ASP.NET Core a Azure | Úvod"
author: ardalis
ms.author: wiwagn
ms.date: 10/06/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.openlocfilehash: 93a74bb7ba537d3c7c0291f7903112dc470133a7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="architect-modern-web-applications-with-aspnet-core-and-azure"></a><span data-ttu-id="e5d7c-103">Architekti moderních webových aplikací pomocí ASP.NET Core a Azure</span><span class="sxs-lookup"><span data-stu-id="e5d7c-103">Architect Modern Web Applications with ASP.NET Core and Azure</span></span>

<span data-ttu-id="e5d7c-104">.NET core a ASP.NET Core nabízí několik výhod oproti tradičním .NET – vývoj.</span><span class="sxs-lookup"><span data-stu-id="e5d7c-104">.NET Core and ASP.NET Core offer several advantages over traditional .NET development.</span></span> <span data-ttu-id="e5d7c-105">.NET Core byste měli použít pro serverové aplikace, pokud některé nebo všechny z následujících akcí, které jsou důležité pro úspěch vaší aplikace:</span><span class="sxs-lookup"><span data-stu-id="e5d7c-105">You should use .NET Core for your server applications if some or all of the following are important to your application's success:</span></span>

-   <span data-ttu-id="e5d7c-106">Podpora více platforem</span><span class="sxs-lookup"><span data-stu-id="e5d7c-106">Cross-platform support</span></span>

-   <span data-ttu-id="e5d7c-107">Použití mikroslužeb</span><span class="sxs-lookup"><span data-stu-id="e5d7c-107">Use of microservices</span></span>

-   <span data-ttu-id="e5d7c-108">Použití kontejnerů Docker</span><span class="sxs-lookup"><span data-stu-id="e5d7c-108">Use of Docker containers</span></span>

-   <span data-ttu-id="e5d7c-109">Vysoký výkon a škálovatelnost požadavky</span><span class="sxs-lookup"><span data-stu-id="e5d7c-109">High performance and scalability requirements</span></span>

-   <span data-ttu-id="e5d7c-110">Souběžně sdílená verze rozhraní .NET verze aplikace na stejném serveru</span><span class="sxs-lookup"><span data-stu-id="e5d7c-110">Side-by-side versioning of .NET versions by application on the same server</span></span>

<span data-ttu-id="e5d7c-111">Tradiční aplikace .NET může a proveďte podporu těchto požadavků, ale jsou optimalizované ASP.NET Core a .NET Core nabízí vylepšenou podporu pro výše uvedené scénáře.</span><span class="sxs-lookup"><span data-stu-id="e5d7c-111">Traditional .NET applications can and do support these requirements, but ASP.NET Core and .NET Core have been optimized to offer improved support for the above scenarios.</span></span>

<span data-ttu-id="e5d7c-112">Organizace více výběru pro hostování své webové aplikace v cloudu pomocí služby, jako je Microsoft Azure.</span><span class="sxs-lookup"><span data-stu-id="e5d7c-112">More and more organizations are choosing to host their web applications in the cloud using services like Microsoft Azure.</span></span> <span data-ttu-id="e5d7c-113">Měli byste zvážit hostování vaší aplikace v cloudu, pokud tady jsou důležité pro vaše aplikace nebo organizace:</span><span class="sxs-lookup"><span data-stu-id="e5d7c-113">You should consider hosting your application in the cloud if the following are important to your application or organization:</span></span>

-   <span data-ttu-id="e5d7c-114">Snížené investice do datového centra náklady (hardwaru, softwaru, místo, nástroje atd.)</span><span class="sxs-lookup"><span data-stu-id="e5d7c-114">Reduced investment in data center costs (hardware, software, space, utilities, etc)</span></span>

-   <span data-ttu-id="e5d7c-115">Flexibilní ceny (platím na základě využití, ne pro nečinnosti kapacity)</span><span class="sxs-lookup"><span data-stu-id="e5d7c-115">Flexible pricing (pay based on usage, not for idle capacity)</span></span>

-   <span data-ttu-id="e5d7c-116">Extrémně spolehlivosti</span><span class="sxs-lookup"><span data-stu-id="e5d7c-116">Extreme reliability</span></span>

-   <span data-ttu-id="e5d7c-117">Vylepšené aplikace mobility; snadno změnit kde a jak vaše aplikace je nasazená</span><span class="sxs-lookup"><span data-stu-id="e5d7c-117">Improved app mobility; easily change where and how your app is deployed</span></span>

-   <span data-ttu-id="e5d7c-118">Flexibilní kapacity; škálování směrem nahoru nebo dolů na základě skutečné požadavky</span><span class="sxs-lookup"><span data-stu-id="e5d7c-118">Flexible capacity; scale up or down based on actual needs</span></span>

<span data-ttu-id="e5d7c-119">Vytváření webových aplikací pomocí ASP.NET Core, hostované ve službě Microsoft Azure nabízí řadu výhod konkurenční přes tradiční alternativy.</span><span class="sxs-lookup"><span data-stu-id="e5d7c-119">Building web applications with ASP.NET Core, hosted in Microsoft Azure, offers numerous competitive advantages over traditional alternatives.</span></span> <span data-ttu-id="e5d7c-120">ASP.NET Core je optimalizovaná pro postupy vývoj moderních webových aplikací a na cloudový hosting scénáře.</span><span class="sxs-lookup"><span data-stu-id="e5d7c-120">ASP.NET Core is optimized for modern web application development practices and cloud hosting scenarios.</span></span> <span data-ttu-id="e5d7c-121">V tomto průvodci se dozvíte, jak do architektury aplikace ASP.NET Core nejlépe využít těchto funkcí.</span><span class="sxs-lookup"><span data-stu-id="e5d7c-121">In this guide, you will learn how to architect your ASP.NET Core applications to best take advantage of these capabilities.</span></span>

## <a name="purpose"></a><span data-ttu-id="e5d7c-122">Účel</span><span class="sxs-lookup"><span data-stu-id="e5d7c-122">Purpose</span></span>

<span data-ttu-id="e5d7c-123">Tato příručka obsahuje pokyny začátku do konce k vytváření monolitický webových aplikací pomocí ASP.NET Core a Azure.</span><span class="sxs-lookup"><span data-stu-id="e5d7c-123">This guide provides end-to-end guidance on building monolithic web applications using ASP.NET Core and Azure.</span></span>

<span data-ttu-id="e5d7c-124">Tato příručka je doplňkem k "*Architecting a vývoj Kontejnerizované a na základě Mikroslužbu aplikace pomocí rozhraní .NET*" která se zaměřuje další na Docker, Mikroslužeb a nasazení kontejnerů do firemní sítě hostitele aplikace.</span><span class="sxs-lookup"><span data-stu-id="e5d7c-124">This guide is complementary to the "*Architecting and Developing Containerized and Microservice-based Applications with .NET*" which focuses more on Docker, Microservices, and Deployment of Containers to host enterprise applications.</span></span>

> ### <a name="architecting-and-developing-containerized-microservice-based-apps-in-net"></a><span data-ttu-id="e5d7c-125">Architektury a vývoj Kontejnerizované Mikroslužbu na základě aplikací v rozhraní .NET</span><span class="sxs-lookup"><span data-stu-id="e5d7c-125">Architecting and Developing Containerized Microservice Based Apps in .NET</span></span>
> - <span data-ttu-id="e5d7c-126">**elektronická kniha**</span><span class="sxs-lookup"><span data-stu-id="e5d7c-126">**e-book**</span></span>  
> <span data-ttu-id="e5d7c-127"><http://aka.MS/MicroservicesEbook></span><span class="sxs-lookup"><span data-stu-id="e5d7c-127"><http://aka.ms/MicroservicesEbook></span></span>
> - <span data-ttu-id="e5d7c-128">**Ukázkové aplikace**</span><span class="sxs-lookup"><span data-stu-id="e5d7c-128">**Sample Application**</span></span>  
> <span data-ttu-id="e5d7c-129"><http://aka.MS/microservicesarchitecture></span><span class="sxs-lookup"><span data-stu-id="e5d7c-129"><http://aka.ms/microservicesarchitecture></span></span>

## <a name="who-should-use-this-guide"></a><span data-ttu-id="e5d7c-130">Tato příručka, kdo by měl používat</span><span class="sxs-lookup"><span data-stu-id="e5d7c-130">Who should use this guide</span></span>

<span data-ttu-id="e5d7c-131">Cílovou skupinu tohoto průvodce je především vývojáře, zájemců vývoj a architektům, kteří mají zájem o vytváření moderních webových aplikací pomocí Microsoft technologií a služeb v cloudu.</span><span class="sxs-lookup"><span data-stu-id="e5d7c-131">The audience for this guide is mainly developers, development leads, and architects who are interested in building modern web applications using Microsoft technologies and services in the cloud.</span></span>

<span data-ttu-id="e5d7c-132">Sekundární cílové skupiny je technické vedoucím pracovníkům, kteří jsou již obeznámeni ASP.NET nebo Azure a hledáte informace o tom, jestli má smysl pro upgrade na ASP.NET Core pro nové nebo existující projekty.</span><span class="sxs-lookup"><span data-stu-id="e5d7c-132">A secondary audience is technical decision makers who are already familiar ASP.NET and/or Azure and are looking for information on whether it makes sense to upgrade to ASP.NET Core for new or existing projects.</span></span>

## <a name="how-you-can-use-this-guide"></a><span data-ttu-id="e5d7c-133">Použití této příručce</span><span class="sxs-lookup"><span data-stu-id="e5d7c-133">How you can use this guide</span></span>

<span data-ttu-id="e5d7c-134">Tato příručka obsahuje byla vyjádřit těmito poměrně malý dokument, který se zaměřuje na tvorbu webových aplikací s moderním technologie .NET a systému Windows Azure.</span><span class="sxs-lookup"><span data-stu-id="e5d7c-134">This guide has been condensed into a relatively small document that focuses on building web applications with modern .NET technologies and Windows Azure.</span></span> <span data-ttu-id="e5d7c-135">Jako takový ho můžete přečíst v celé jeho šíři poskytnout základní principy tyto aplikace a jejich technické aspekty.</span><span class="sxs-lookup"><span data-stu-id="e5d7c-135">As such, it can be read in its entirety to provide a foundation of understanding such applications and their technical considerations.</span></span> <span data-ttu-id="e5d7c-136">V průvodci, společně s ukázkovou aplikaci, může taky sloužit jako výchozí bod nebo odkaz.</span><span class="sxs-lookup"><span data-stu-id="e5d7c-136">The guide, along with its sample application, can also serve as a starting point or reference.</span></span> <span data-ttu-id="e5d7c-137">Pomocí aplikace přidružené sample jako šablona pro vaše vlastní aplikace nebo zjistit, jak můžete organizovat součásti vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="e5d7c-137">Use the associated sample application as a template for your own applications, or to see how you might organize your application's component parts.</span></span> <span data-ttu-id="e5d7c-138">Při odkazovat zpět v Průvodci principy a pokrytí architektura a možnosti technologií a rozhodnutí vážení tyto možnosti pro vlastní aplikaci.</span><span class="sxs-lookup"><span data-stu-id="e5d7c-138">Refer back to the guide's principles and coverage of architecture and technology options and decision considerations when weighing these choices for your own application.</span></span>

<span data-ttu-id="e5d7c-139">Nebojte se, že předávání této příručce si s týmem k zajištění výklad tyto požadavky a možnosti.</span><span class="sxs-lookup"><span data-stu-id="e5d7c-139">Feel free to forward this guide to your team to help ensure a common understanding of these considerations and opportunities.</span></span> <span data-ttu-id="e5d7c-140">Má každý uživatel práce z společnou sadu terminologie a základních zásad vám pomůže zajistit konzistentní použití architektury vzory a postupy.</span><span class="sxs-lookup"><span data-stu-id="e5d7c-140">Having everybody working from a common set of terminology and underlying principles will help ensure consistent application of architectural patterns and practices.</span></span>

## <a name="references"></a><span data-ttu-id="e5d7c-141">Odkazy</span><span class="sxs-lookup"><span data-stu-id="e5d7c-141">References</span></span>
- <span data-ttu-id="e5d7c-142">**Volba mezi .NET Core a rozhraní .NET Framework pro server aplikace**</span><span class="sxs-lookup"><span data-stu-id="e5d7c-142">**Choosing between .NET Core and .NET Framework for server apps**</span></span>  
<span data-ttu-id="e5d7c-143"><https://docs.microsoft.com/DotNet/articles/Standard/Choosing-Core-Framework-server></span><span class="sxs-lookup"><span data-stu-id="e5d7c-143"><https://docs.microsoft.com/dotnet/articles/standard/choosing-core-framework-server></span></span>

>[!div class="step-by-step"]
<span data-ttu-id="e5d7c-144">[Další] (moderních web aplikace characteristics.md)</span><span class="sxs-lookup"><span data-stu-id="e5d7c-144">[Next] (modern-web-applications-characteristics.md)</span></span>
