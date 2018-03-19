---
title: "Architekti moderních webových aplikací pomocí ASP.NET Core a Azure"
description: "Architektury moderních webových aplikací pomocí ASP.NET Core a Azure | Úvod"
author: ardalis
ms.author: wiwagn
ms.date: 10/06/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 1140a18aba685f3415d7c599d1b76648bf9924e7
ms.sourcegitcommit: c3957fdb990060559d73cca44ab3e2c7b4d049c0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2018
---
# <a name="architect-modern-web-applications-with-aspnet-core-and-azure"></a><span data-ttu-id="fe57a-103">Architekti moderních webových aplikací pomocí ASP.NET Core a Azure</span><span class="sxs-lookup"><span data-stu-id="fe57a-103">Architect Modern Web Applications with ASP.NET Core and Azure</span></span>

![Obrázek titulní](./media/cover.jpg)


<span data-ttu-id="fe57a-105">.NET core a ASP.NET Core nabízí několik výhod oproti tradičním .NET – vývoj.</span><span class="sxs-lookup"><span data-stu-id="fe57a-105">.NET Core and ASP.NET Core offer several advantages over traditional .NET development.</span></span> <span data-ttu-id="fe57a-106">.NET Core byste měli použít pro serverové aplikace, pokud některé nebo všechny z následujících akcí, které jsou důležité pro úspěch vaší aplikace:</span><span class="sxs-lookup"><span data-stu-id="fe57a-106">You should use .NET Core for your server applications if some or all of the following are important to your application's success:</span></span>

-   <span data-ttu-id="fe57a-107">Podpora více platforem</span><span class="sxs-lookup"><span data-stu-id="fe57a-107">Cross-platform support</span></span>

-   <span data-ttu-id="fe57a-108">Použití mikroslužeb</span><span class="sxs-lookup"><span data-stu-id="fe57a-108">Use of microservices</span></span>

-   <span data-ttu-id="fe57a-109">Použití kontejnerů Docker</span><span class="sxs-lookup"><span data-stu-id="fe57a-109">Use of Docker containers</span></span>

-   <span data-ttu-id="fe57a-110">Vysoký výkon a škálovatelnost požadavky</span><span class="sxs-lookup"><span data-stu-id="fe57a-110">High performance and scalability requirements</span></span>

-   <span data-ttu-id="fe57a-111">Souběžně sdílená verze rozhraní .NET verze aplikace na stejném serveru</span><span class="sxs-lookup"><span data-stu-id="fe57a-111">Side-by-side versioning of .NET versions by application on the same server</span></span>

<span data-ttu-id="fe57a-112">Tradiční aplikace .NET může a proveďte podporu těchto požadavků, ale jsou optimalizované ASP.NET Core a .NET Core nabízí vylepšenou podporu pro výše uvedené scénáře.</span><span class="sxs-lookup"><span data-stu-id="fe57a-112">Traditional .NET applications can and do support these requirements, but ASP.NET Core and .NET Core have been optimized to offer improved support for the above scenarios.</span></span>

<span data-ttu-id="fe57a-113">Organizace více výběru pro hostování své webové aplikace v cloudu pomocí služby, jako je Microsoft Azure.</span><span class="sxs-lookup"><span data-stu-id="fe57a-113">More and more organizations are choosing to host their web applications in the cloud using services like Microsoft Azure.</span></span> <span data-ttu-id="fe57a-114">Měli byste zvážit hostování vaší aplikace v cloudu, pokud tady jsou důležité pro vaše aplikace nebo organizace:</span><span class="sxs-lookup"><span data-stu-id="fe57a-114">You should consider hosting your application in the cloud if the following are important to your application or organization:</span></span>

-   <span data-ttu-id="fe57a-115">Snížené investice do datového centra náklady (hardwaru, softwaru, místo, nástroje atd.)</span><span class="sxs-lookup"><span data-stu-id="fe57a-115">Reduced investment in data center costs (hardware, software, space, utilities, etc)</span></span>

-   <span data-ttu-id="fe57a-116">Flexibilní ceny (platím na základě využití, ne pro nečinnosti kapacity)</span><span class="sxs-lookup"><span data-stu-id="fe57a-116">Flexible pricing (pay based on usage, not for idle capacity)</span></span>

-   <span data-ttu-id="fe57a-117">Extrémně spolehlivosti</span><span class="sxs-lookup"><span data-stu-id="fe57a-117">Extreme reliability</span></span>

-   <span data-ttu-id="fe57a-118">Vylepšené aplikace mobility; snadno změnit kde a jak vaše aplikace je nasazená</span><span class="sxs-lookup"><span data-stu-id="fe57a-118">Improved app mobility; easily change where and how your app is deployed</span></span>

-   <span data-ttu-id="fe57a-119">Flexibilní kapacity; škálování směrem nahoru nebo dolů na základě skutečné požadavky</span><span class="sxs-lookup"><span data-stu-id="fe57a-119">Flexible capacity; scale up or down based on actual needs</span></span>

<span data-ttu-id="fe57a-120">Vytváření webových aplikací pomocí ASP.NET Core, hostované ve službě Microsoft Azure nabízí řadu výhod konkurenční přes tradiční alternativy.</span><span class="sxs-lookup"><span data-stu-id="fe57a-120">Building web applications with ASP.NET Core, hosted in Microsoft Azure, offers numerous competitive advantages over traditional alternatives.</span></span> <span data-ttu-id="fe57a-121">ASP.NET Core je optimalizovaná pro postupy vývoj moderních webových aplikací a na cloudový hosting scénáře.</span><span class="sxs-lookup"><span data-stu-id="fe57a-121">ASP.NET Core is optimized for modern web application development practices and cloud hosting scenarios.</span></span> <span data-ttu-id="fe57a-122">V tomto průvodci se dozvíte, jak do architektury aplikace ASP.NET Core nejlépe využít těchto funkcí.</span><span class="sxs-lookup"><span data-stu-id="fe57a-122">In this guide, you will learn how to architect your ASP.NET Core applications to best take advantage of these capabilities.</span></span>

## <a name="purpose"></a><span data-ttu-id="fe57a-123">Účel</span><span class="sxs-lookup"><span data-stu-id="fe57a-123">Purpose</span></span>

<span data-ttu-id="fe57a-124">Tato příručka obsahuje pokyny začátku do konce k vytváření monolitický webových aplikací pomocí ASP.NET Core a Azure.</span><span class="sxs-lookup"><span data-stu-id="fe57a-124">This guide provides end-to-end guidance on building monolithic web applications using ASP.NET Core and Azure.</span></span>

<span data-ttu-id="fe57a-125">Tato příručka je doplňkem k "*Architecting a vývoj Kontejnerizované a na základě Mikroslužbu aplikace pomocí rozhraní .NET*" která se zaměřuje další na Docker, Mikroslužeb a nasazení kontejnerů do firemní sítě hostitele aplikace.</span><span class="sxs-lookup"><span data-stu-id="fe57a-125">This guide is complementary to the "*Architecting and Developing Containerized and Microservice-based Applications with .NET*" which focuses more on Docker, Microservices, and Deployment of Containers to host enterprise applications.</span></span>

> ### <a name="architecting-and-developing-containerized-microservice-based-apps-in-net"></a><span data-ttu-id="fe57a-126">Architektury a vývoj Kontejnerizované Mikroslužbu na základě aplikací v rozhraní .NET</span><span class="sxs-lookup"><span data-stu-id="fe57a-126">Architecting and Developing Containerized Microservice Based Apps in .NET</span></span>
> - <span data-ttu-id="fe57a-127">**elektronická kniha**</span><span class="sxs-lookup"><span data-stu-id="fe57a-127">**e-book**</span></span>  
> <http://aka.ms/MicroservicesEbook>
> - <span data-ttu-id="fe57a-128">**Ukázkové aplikace**</span><span class="sxs-lookup"><span data-stu-id="fe57a-128">**Sample Application**</span></span>  
> <http://aka.ms/microservicesarchitecture>

## <a name="who-should-use-this-guide"></a><span data-ttu-id="fe57a-129">Tato příručka, kdo by měl používat</span><span class="sxs-lookup"><span data-stu-id="fe57a-129">Who should use this guide</span></span>

<span data-ttu-id="fe57a-130">Cílovou skupinu tohoto průvodce je především vývojáře, zájemců vývoj a architektům, kteří mají zájem o vytváření moderních webových aplikací pomocí Microsoft technologií a služeb v cloudu.</span><span class="sxs-lookup"><span data-stu-id="fe57a-130">The audience for this guide is mainly developers, development leads, and architects who are interested in building modern web applications using Microsoft technologies and services in the cloud.</span></span>

<span data-ttu-id="fe57a-131">Sekundární cílové skupiny je technické vedoucím pracovníkům, kteří jsou již obeznámeni ASP.NET nebo Azure a hledáte informace o tom, jestli má smysl pro upgrade na ASP.NET Core pro nové nebo existující projekty.</span><span class="sxs-lookup"><span data-stu-id="fe57a-131">A secondary audience is technical decision makers who are already familiar ASP.NET and/or Azure and are looking for information on whether it makes sense to upgrade to ASP.NET Core for new or existing projects.</span></span>

## <a name="how-you-can-use-this-guide"></a><span data-ttu-id="fe57a-132">Použití této příručce</span><span class="sxs-lookup"><span data-stu-id="fe57a-132">How you can use this guide</span></span>

<span data-ttu-id="fe57a-133">Tato příručka obsahuje byla vyjádřit těmito poměrně malý dokument, který se zaměřuje na tvorbu webových aplikací s moderním technologie .NET a systému Windows Azure.</span><span class="sxs-lookup"><span data-stu-id="fe57a-133">This guide has been condensed into a relatively small document that focuses on building web applications with modern .NET technologies and Windows Azure.</span></span> <span data-ttu-id="fe57a-134">Jako takový ho můžete přečíst v celé jeho šíři poskytnout základní principy tyto aplikace a jejich technické aspekty.</span><span class="sxs-lookup"><span data-stu-id="fe57a-134">As such, it can be read in its entirety to provide a foundation of understanding such applications and their technical considerations.</span></span> <span data-ttu-id="fe57a-135">V průvodci, společně s ukázkovou aplikaci, může taky sloužit jako výchozí bod nebo odkaz.</span><span class="sxs-lookup"><span data-stu-id="fe57a-135">The guide, along with its sample application, can also serve as a starting point or reference.</span></span> <span data-ttu-id="fe57a-136">Pomocí aplikace přidružené sample jako šablona pro vaše vlastní aplikace nebo zjistit, jak můžete organizovat součásti vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="fe57a-136">Use the associated sample application as a template for your own applications, or to see how you might organize your application's component parts.</span></span> <span data-ttu-id="fe57a-137">Při odkazovat zpět v Průvodci principy a pokrytí architektura a možnosti technologií a rozhodnutí vážení tyto možnosti pro vlastní aplikaci.</span><span class="sxs-lookup"><span data-stu-id="fe57a-137">Refer back to the guide's principles and coverage of architecture and technology options and decision considerations when weighing these choices for your own application.</span></span>

<span data-ttu-id="fe57a-138">Nebojte se, že předávání této příručce si s týmem k zajištění výklad tyto požadavky a možnosti.</span><span class="sxs-lookup"><span data-stu-id="fe57a-138">Feel free to forward this guide to your team to help ensure a common understanding of these considerations and opportunities.</span></span> <span data-ttu-id="fe57a-139">Má každý uživatel práce z společnou sadu terminologie a základních zásad vám pomůže zajistit konzistentní použití architektury vzory a postupy.</span><span class="sxs-lookup"><span data-stu-id="fe57a-139">Having everybody working from a common set of terminology and underlying principles will help ensure consistent application of architectural patterns and practices.</span></span>

## <a name="references"></a><span data-ttu-id="fe57a-140">Odkazy</span><span class="sxs-lookup"><span data-stu-id="fe57a-140">References</span></span>
- <span data-ttu-id="fe57a-141">**Volba mezi .NET Core a .NET Framework pro serverové aplikace**</span><span class="sxs-lookup"><span data-stu-id="fe57a-141">**Choosing between .NET Core and .NET Framework for server apps**</span></span>  
<https://docs.microsoft.com/dotnet/standard/choosing-core-framework-server>

>[!div class="step-by-step"]
<span data-ttu-id="fe57a-142">[Další] (modern-web-applications-characteristics.md)</span><span class="sxs-lookup"><span data-stu-id="fe57a-142">[Next] (modern-web-applications-characteristics.md)</span></span>
