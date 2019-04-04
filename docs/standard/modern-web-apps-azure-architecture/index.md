---
title: Navrhování moderních webových aplikací pomocí ASP.NET Core a Azure
description: Průvodce, který obsahuje pokyny k začátku do konce vytváření monolitické webových aplikací pomocí ASP.NET Core a Azure.
author: ardalis
ms.author: wiwagn
ms.date: 01/30/2019
ms.openlocfilehash: 27212045d9870c9f2fc15509d76f3e9b07d8657f
ms.sourcegitcommit: 0aca6c5d166d7961a1e354c248495645b97a1dc5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/30/2019
ms.locfileid: "58675832"
---
# <a name="architect-modern-web-applications-with-aspnet-core-and-azure"></a><span data-ttu-id="e2d6d-103">Navrhování moderních webových aplikací pomocí ASP.NET Core a Azure</span><span class="sxs-lookup"><span data-stu-id="e2d6d-103">Architect Modern Web Applications with ASP.NET Core and Azure</span></span>

![Titulní obrázek Průvodce architekt moderních webových aplikací.](./media/index/web-application-guide-cover-image.png)

<span data-ttu-id="e2d6d-105">PUBLIKOVAL(A)</span><span class="sxs-lookup"><span data-stu-id="e2d6d-105">PUBLISHED BY</span></span>

<span data-ttu-id="e2d6d-106">Microsoft Developer Division, .NET a Visual Studio produktových týmů</span><span class="sxs-lookup"><span data-stu-id="e2d6d-106">Microsoft Developer Division, .NET, and Visual Studio product teams</span></span>

<span data-ttu-id="e2d6d-107">A division of Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="e2d6d-107">A division of Microsoft Corporation</span></span>

<span data-ttu-id="e2d6d-108">One Microsoft Way</span><span class="sxs-lookup"><span data-stu-id="e2d6d-108">One Microsoft Way</span></span>

<span data-ttu-id="e2d6d-109">Redmond, Washington 98052-6399</span><span class="sxs-lookup"><span data-stu-id="e2d6d-109">Redmond, Washington 98052-6399</span></span>

<span data-ttu-id="e2d6d-110">Copyright © 2019 by Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="e2d6d-110">Copyright © 2019 by Microsoft Corporation</span></span>

<span data-ttu-id="e2d6d-111">Všechna práva vyhrazena.</span><span class="sxs-lookup"><span data-stu-id="e2d6d-111">All rights reserved.</span></span> <span data-ttu-id="e2d6d-112">Žádná část obsahu této knihy může reprodukovat nebo v libovolné formě nebo jakýmikoli prostředky bez písemného souhlasu vydavatele.</span><span class="sxs-lookup"><span data-stu-id="e2d6d-112">No part of the contents of this book may be reproduced or transmitted in any form or by any means without the written permission of the publisher.</span></span>

<span data-ttu-id="e2d6d-113">Tato kniha je k dispozici "jako-je" a vyjadřuje zobrazení autora a názory.</span><span class="sxs-lookup"><span data-stu-id="e2d6d-113">This book is provided “as-is” and expresses the author’s views and opinions.</span></span> <span data-ttu-id="e2d6d-114">Zobrazení, názory a informace v této knize, včetně adres URL a jiných odkazů na internetové weby, mohou změnit bez předchozího upozornění.</span><span class="sxs-lookup"><span data-stu-id="e2d6d-114">The views, opinions and information expressed in this book, including URL and other Internet website references, may change without notice.</span></span>

<span data-ttu-id="e2d6d-115">Některé zde uvedené příklady jsou k dispozici pouze pro ilustraci a jsou smyšlené.</span><span class="sxs-lookup"><span data-stu-id="e2d6d-115">Some examples depicted herein are provided for illustration only and are fictitious.</span></span> <span data-ttu-id="e2d6d-116">Žádný skutečný vztah nebo spojení ani je určena ji vyvozovat.</span><span class="sxs-lookup"><span data-stu-id="e2d6d-116">No real association or connection is intended or should be inferred.</span></span>

<span data-ttu-id="e2d6d-117">Microsoft a ochranné známky uvedený na https://www.microsoft.com na webové stránce "Ochranné známky" jsou obchodní známky společností skupiny Microsoft.</span><span class="sxs-lookup"><span data-stu-id="e2d6d-117">Microsoft and the trademarks listed at https://www.microsoft.com on the “Trademarks” webpage are trademarks of the Microsoft group of companies.</span></span>

<span data-ttu-id="e2d6d-118">Mac a macOS jsou ochranné známky společnosti Apple Inc.</span><span class="sxs-lookup"><span data-stu-id="e2d6d-118">Mac and macOS are trademarks of Apple Inc.</span></span>

<span data-ttu-id="e2d6d-119">Velryba logo Dockeru je registrovaná ochranná známka společnosti Docker, Inc. Použít oprávnění.</span><span class="sxs-lookup"><span data-stu-id="e2d6d-119">The Docker whale logo is a registered trademark of Docker, Inc. Used by permission.</span></span>

<span data-ttu-id="e2d6d-120">Všechny ostatní značky a loga jsou majetkem příslušných vlastníků.</span><span class="sxs-lookup"><span data-stu-id="e2d6d-120">All other marks and logos are property of their respective owners.</span></span>

<span data-ttu-id="e2d6d-121">Autor:</span><span class="sxs-lookup"><span data-stu-id="e2d6d-121">Author:</span></span>

> <span data-ttu-id="e2d6d-122">**Steve "ardalis" Smith** - softwarový architekt a Trainer - [Ardalis.com](https://ardalis.com)</span><span class="sxs-lookup"><span data-stu-id="e2d6d-122">**Steve "ardalis" Smith** - Software Architect and Trainer - [Ardalis.com](https://ardalis.com)</span></span>

<span data-ttu-id="e2d6d-123">Editory:</span><span class="sxs-lookup"><span data-stu-id="e2d6d-123">Editors:</span></span>

> <span data-ttu-id="e2d6d-124">**Maira Wenzel**</span><span class="sxs-lookup"><span data-stu-id="e2d6d-124">**Maira Wenzel**</span></span>

## <a name="introduction"></a><span data-ttu-id="e2d6d-125">Úvod</span><span class="sxs-lookup"><span data-stu-id="e2d6d-125">Introduction</span></span>

<span data-ttu-id="e2d6d-126">.NET core a ASP.NET Core nabízí několik výhod oproti tradičním vývoj na platformě .NET.</span><span class="sxs-lookup"><span data-stu-id="e2d6d-126">.NET Core and ASP.NET Core offer several advantages over traditional .NET development.</span></span> <span data-ttu-id="e2d6d-127">Pokud některé nebo všechny z následujících akcí, které jsou důležité pro úspěch vaší aplikace byste měli používat .NET Core pro serverové aplikace:</span><span class="sxs-lookup"><span data-stu-id="e2d6d-127">You should use .NET Core for your server applications if some or all of the following are important to your application's success:</span></span>

- <span data-ttu-id="e2d6d-128">Podpora víc platforem.</span><span class="sxs-lookup"><span data-stu-id="e2d6d-128">Cross-platform support.</span></span>

- <span data-ttu-id="e2d6d-129">Používání mikroslužeb.</span><span class="sxs-lookup"><span data-stu-id="e2d6d-129">Use of microservices.</span></span>

- <span data-ttu-id="e2d6d-130">Použití kontejnerů Dockeru.</span><span class="sxs-lookup"><span data-stu-id="e2d6d-130">Use of Docker containers.</span></span>

- <span data-ttu-id="e2d6d-131">Vysoké požadavky na výkon a škálovatelnost.</span><span class="sxs-lookup"><span data-stu-id="e2d6d-131">High performance and scalability requirements.</span></span>

- <span data-ttu-id="e2d6d-132">Správa verzí vedle sebe verzí rozhraní .NET v aplikaci na stejném serveru.</span><span class="sxs-lookup"><span data-stu-id="e2d6d-132">Side-by-side versioning of .NET versions by application on the same server.</span></span>

<span data-ttu-id="e2d6d-133">Tradiční aplikace rozhraní .NET můžete a dělat podporují mnohé z těchto požadavků, ale v ASP.NET Core a .NET Core byly optimalizovány a nabídnout Vylepšená podpora pro výše zmíněné situace umožnili.</span><span class="sxs-lookup"><span data-stu-id="e2d6d-133">Traditional .NET applications can and do support many of these requirements, but ASP.NET Core and .NET Core have been optimized to offer improved support for the above scenarios.</span></span>

<span data-ttu-id="e2d6d-134">Více organizací volí k hostování webových aplikací v cloudu pomocí služeb, jako je Microsoft Azure.</span><span class="sxs-lookup"><span data-stu-id="e2d6d-134">More and more organizations are choosing to host their web applications in the cloud using services like Microsoft Azure.</span></span> <span data-ttu-id="e2d6d-135">Měli byste zvážit hostování vaší aplikace v cloudu, pokud tady jsou důležité pro vaše aplikace nebo organizace:</span><span class="sxs-lookup"><span data-stu-id="e2d6d-135">You should consider hosting your application in the cloud if the following are important to your application or organization:</span></span>

- <span data-ttu-id="e2d6d-136">Snížení investice do datového centra náklady (hardware, software, místa, nástroje, Správa serveru atd.)</span><span class="sxs-lookup"><span data-stu-id="e2d6d-136">Reduced investment in data center costs (hardware, software, space, utilities, server management, etc.)</span></span>

- <span data-ttu-id="e2d6d-137">Flexibilní ceny (placené podle používání, ne za nevyužitou kapacitu).</span><span class="sxs-lookup"><span data-stu-id="e2d6d-137">Flexible pricing (pay based on usage, not for idle capacity).</span></span>

- <span data-ttu-id="e2d6d-138">Extrémní spolehlivost.</span><span class="sxs-lookup"><span data-stu-id="e2d6d-138">Extreme reliability.</span></span>

- <span data-ttu-id="e2d6d-139">Vylepšené aplikace mobility; snadno změnit, kde a jak je aplikace nasazená.</span><span class="sxs-lookup"><span data-stu-id="e2d6d-139">Improved app mobility; easily change where and how your app is deployed.</span></span>

- <span data-ttu-id="e2d6d-140">Flexibilní kapacity; vertikálně navyšovat nebo snižovat podle skutečných potřeb.</span><span class="sxs-lookup"><span data-stu-id="e2d6d-140">Flexible capacity; scale up or down based on actual needs.</span></span>

<span data-ttu-id="e2d6d-141">Vytváření webových aplikací pomocí ASP.NET Core, hostované v Azure, nabízí mnoho konkurenční výhody oproti tradičním alternativy.</span><span class="sxs-lookup"><span data-stu-id="e2d6d-141">Building web applications with ASP.NET Core, hosted in Azure, offers many competitive advantages over traditional alternatives.</span></span> <span data-ttu-id="e2d6d-142">ASP.NET Core je optimalizovaná pro postupy vývoje moderních webových aplikací a cloudových scénářích hostování.</span><span class="sxs-lookup"><span data-stu-id="e2d6d-142">ASP.NET Core is optimized for modern web application development practices and cloud hosting scenarios.</span></span> <span data-ttu-id="e2d6d-143">V této příručce se dozvíte, jak navrhovat aplikace ASP.NET Core nejlíp využít tyto možnosti.</span><span class="sxs-lookup"><span data-stu-id="e2d6d-143">In this guide, you'll learn how to architect your ASP.NET Core applications to best take advantage of these capabilities.</span></span>

## <a name="purpose"></a><span data-ttu-id="e2d6d-144">Účel</span><span class="sxs-lookup"><span data-stu-id="e2d6d-144">Purpose</span></span>

<span data-ttu-id="e2d6d-145">Tato příručka obsahuje pokyny k začátku do konce vytváření *monolitické* webové aplikace pomocí ASP.NET Core a Azure.</span><span class="sxs-lookup"><span data-stu-id="e2d6d-145">This guide provides end-to-end guidance on building *monolithic* web applications using ASP.NET Core and Azure.</span></span> <span data-ttu-id="e2d6d-146">V tomto kontextu "monolitické" odkazuje na skutečnost, že jsou tyto aplikace nasadit jako celek, ne jako kolekci komunikující služeb a aplikací.</span><span class="sxs-lookup"><span data-stu-id="e2d6d-146">In this context, "monolithic" refers to the fact that these applications are deployed as a single unit, not as a collection of interacting services and applications.</span></span>

<span data-ttu-id="e2d6d-147">Tento průvodce je pouze doplnění ["_Mikroslužby .NET. Architektura pro Kontejnerizovaných aplikací .NET_"](../microservices-architecture/index.md) který se zaměřuje další on Docker, Mikroslužby a nasazení kontejnerů pro hostování podnikových aplikací.</span><span class="sxs-lookup"><span data-stu-id="e2d6d-147">This guide is complementary to the ["_.NET Microservices. Architecture for Containerized .NET Applications_"](../microservices-architecture/index.md) which focuses more on Docker, Microservices, and Deployment of Containers to host enterprise applications.</span></span>

### <a name="net-microservices-architecture-for-containerized-net-applications"></a><span data-ttu-id="e2d6d-148">Mikroslužby .NET.</span><span class="sxs-lookup"><span data-stu-id="e2d6d-148">.NET Microservices.</span></span> <span data-ttu-id="e2d6d-149">Architektura pro Kontejnerizované aplikace .NET</span><span class="sxs-lookup"><span data-stu-id="e2d6d-149">Architecture for Containerized .NET Applications</span></span>

- <span data-ttu-id="e2d6d-150">**(elektronická kniha)**</span><span class="sxs-lookup"><span data-stu-id="e2d6d-150">**e-book**</span></span>  
  <https://aka.ms/MicroservicesEbook>
- <span data-ttu-id="e2d6d-151">**Ukázkové aplikace**</span><span class="sxs-lookup"><span data-stu-id="e2d6d-151">**Sample Application**</span></span>  
  <https://aka.ms/microservicesarchitecture>

## <a name="who-should-use-this-guide"></a><span data-ttu-id="e2d6d-152">Kdo by měl používat tohoto průvodce</span><span class="sxs-lookup"><span data-stu-id="e2d6d-152">Who should use this guide</span></span>

<span data-ttu-id="e2d6d-153">Cílovou skupinu tohoto průvodce je především vývojáře, vedoucími vývoje a architektů, kteří mají zájem o vývoj moderních webových aplikací pomocí Microsoft technologie a služby v cloudu.</span><span class="sxs-lookup"><span data-stu-id="e2d6d-153">The audience for this guide is mainly developers, development leads, and architects who are interested in building modern web applications using Microsoft technologies and services in the cloud.</span></span>

<span data-ttu-id="e2d6d-154">Sekundární skupina jsou technické pracovníky s rozhodovací pravomocí, kteří jsou již známé technologie ASP.NET nebo v Azure a hledáte informace o tom, zda má smysl pro upgrade na technologie ASP.NET Core pro nové nebo existující projekty.</span><span class="sxs-lookup"><span data-stu-id="e2d6d-154">A secondary audience is technical decision makers who are already familiar ASP.NET or Azure and are looking for information on whether it makes sense to upgrade to ASP.NET Core for new or existing projects.</span></span>

## <a name="how-you-can-use-this-guide"></a><span data-ttu-id="e2d6d-155">Použití tohoto průvodce</span><span class="sxs-lookup"><span data-stu-id="e2d6d-155">How you can use this guide</span></span>

<span data-ttu-id="e2d6d-156">Tato příručka obsahuje byla zhušťovat do poměrně málo početnému dokumentu, který se zaměřuje na tvorbu webových aplikací s moderní technologie .NET a Windows Azure.</span><span class="sxs-lookup"><span data-stu-id="e2d6d-156">This guide has been condensed into a relatively small document that focuses on building web applications with modern .NET technologies and Windows Azure.</span></span> <span data-ttu-id="e2d6d-157">V důsledku toho může být číst v celém rozsahu na poskytují základní principy těchto aplikací a jejich technické aspekty.</span><span class="sxs-lookup"><span data-stu-id="e2d6d-157">As such, it can be read in its entirety to provide a foundation of understanding such applications and their technical considerations.</span></span> <span data-ttu-id="e2d6d-158">V průvodci, spolu s ukázkovou aplikaci, může sloužit také jako výchozí bod nebo odkaz.</span><span class="sxs-lookup"><span data-stu-id="e2d6d-158">The guide, along with its sample application, can also serve as a starting point or reference.</span></span> <span data-ttu-id="e2d6d-159">Použijte související ukázkové aplikace jako šablonu pro vaše vlastní aplikace, nebo můžete zobrazit, jak můžete organizovat součásti vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="e2d6d-159">Use the associated sample application as a template for your own applications, or to see how you might organize your application's component parts.</span></span> <span data-ttu-id="e2d6d-160">Při odkazovat zpět v Průvodci principy a pokrytí architektury a možnosti technologií a důležité informace o rozhodnutí při vážení tyto možnosti pro svoji vlastní aplikaci.</span><span class="sxs-lookup"><span data-stu-id="e2d6d-160">Refer back to the guide's principles and coverage of architecture and technology options and decision considerations when you're weighing these choices for your own application.</span></span>

<span data-ttu-id="e2d6d-161">Můžete dál v této příručce k vašemu týmu pomoct zajistit, aby tyto aspekty a příležitosti.</span><span class="sxs-lookup"><span data-stu-id="e2d6d-161">Feel free to forward this guide to your team to help ensure a common understanding of these considerations and opportunities.</span></span> <span data-ttu-id="e2d6d-162">S Vystoupením práce z společnou sadu terminologie a základní principy pomáhá zajistit konzistentní použití architektury vzory a postupy.</span><span class="sxs-lookup"><span data-stu-id="e2d6d-162">Having everybody working from a common set of terminology and underlying principles helps ensure consistent application of architectural patterns and practices.</span></span>

## <a name="references"></a><span data-ttu-id="e2d6d-163">Odkazy</span><span class="sxs-lookup"><span data-stu-id="e2d6d-163">References</span></span>

- <span data-ttu-id="e2d6d-164">**Volba mezi .NET Core a .NET Framework pro serverové aplikace**</span><span class="sxs-lookup"><span data-stu-id="e2d6d-164">**Choosing between .NET Core and .NET Framework for server apps**</span></span>  
  [https://docs.microsoft.com/dotnet/standard/choosing-core-framework-server](../choosing-core-framework-server.md)

>[!div class="step-by-step"]
>[<span data-ttu-id="e2d6d-165">Next</span><span class="sxs-lookup"><span data-stu-id="e2d6d-165">Next</span></span>](modern-web-applications-characteristics.md)