---
title: Architektur moderních webových aplikací s ASP.NET Core a Azure
description: Průvodce, který poskytuje komplexní pokyny pro vytváření monolitických webových aplikací pomocí ASP.NET Core a Azure.
author: ardalis
ms.author: wiwagn
ms.date: 12/4/2019
ms.openlocfilehash: c19e5e90cfb96463f744cfb064abe72ee5db2e9f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "77449322"
---
# <a name="architect-modern-web-applications-with-aspnet-core-and-azure"></a><span data-ttu-id="d04c3-103">Navrhování moderních webových aplikací pomocí ASP.NET Core a Azure</span><span class="sxs-lookup"><span data-stu-id="d04c3-103">Architect Modern Web Applications with ASP.NET Core and Azure</span></span>

![Obrázek obálky knihy průvodce Moderní webové aplikace Architekt.](./media/index/web-application-guide-cover-image.png)

<span data-ttu-id="d04c3-105">**EDITION v3.1** - Aktualizováno na ASP.NET Jádro 3.1</span><span class="sxs-lookup"><span data-stu-id="d04c3-105">**EDITION v3.1** - Updated to ASP.NET Core 3.1</span></span>

<span data-ttu-id="d04c3-106">PUBLIKOVAL(A)</span><span class="sxs-lookup"><span data-stu-id="d04c3-106">PUBLISHED BY</span></span>

<span data-ttu-id="d04c3-107">Produktové týmy Microsoft Developer Division, .NET a Visual Studio</span><span class="sxs-lookup"><span data-stu-id="d04c3-107">Microsoft Developer Division, .NET, and Visual Studio product teams</span></span>

<span data-ttu-id="d04c3-108">Divize společnosti Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="d04c3-108">A division of Microsoft Corporation</span></span>

<span data-ttu-id="d04c3-109">One Microsoft Way</span><span class="sxs-lookup"><span data-stu-id="d04c3-109">One Microsoft Way</span></span>

<span data-ttu-id="d04c3-110">Redmond, Washington 98052-6399</span><span class="sxs-lookup"><span data-stu-id="d04c3-110">Redmond, Washington 98052-6399</span></span>

<span data-ttu-id="d04c3-111">Autorská práva © 2020 společností Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="d04c3-111">Copyright © 2020 by Microsoft Corporation</span></span>

<span data-ttu-id="d04c3-112">Všechna práva vyhrazena.</span><span class="sxs-lookup"><span data-stu-id="d04c3-112">All rights reserved.</span></span> <span data-ttu-id="d04c3-113">Žádná část obsahu této knihy nesmí být reprodukována nebo přenášena v jakékoli formě nebo jakýmkoli způsobem bez písemného souhlasu vydavatele.</span><span class="sxs-lookup"><span data-stu-id="d04c3-113">No part of the contents of this book may be reproduced or transmitted in any form or by any means without the written permission of the publisher.</span></span>

<span data-ttu-id="d04c3-114">Tato kniha je poskytována "tak, jak je" a vyjadřuje názory a názory autora.</span><span class="sxs-lookup"><span data-stu-id="d04c3-114">This book is provided “as-is” and expresses the author’s views and opinions.</span></span> <span data-ttu-id="d04c3-115">Názory, názory a informace vyjádřené v této knize, včetně URL a dalších odkazů na internetové stránky, se mohou změnit bez předchozího upozornění.</span><span class="sxs-lookup"><span data-stu-id="d04c3-115">The views, opinions and information expressed in this book, including URL and other Internet website references, may change without notice.</span></span>

<span data-ttu-id="d04c3-116">Některé zde uvedené příklady slouží pouze k znázornění a jsou smyšlené.</span><span class="sxs-lookup"><span data-stu-id="d04c3-116">Some examples depicted herein are provided for illustration only and are fictitious.</span></span> <span data-ttu-id="d04c3-117">Neměli byste z nich vyvozovat žádné skutečné vztahy či spojení.</span><span class="sxs-lookup"><span data-stu-id="d04c3-117">No real association or connection is intended or should be inferred.</span></span>

<span data-ttu-id="d04c3-118">Společnost Microsoft a ochranné https://www.microsoft.com známky uvedené na webové stránce "Ochranné známky" jsou ochrannými známkami skupiny společností Microsoft.</span><span class="sxs-lookup"><span data-stu-id="d04c3-118">Microsoft and the trademarks listed at https://www.microsoft.com on the “Trademarks” webpage are trademarks of the Microsoft group of companies.</span></span>

<span data-ttu-id="d04c3-119">Mac a macOS jsou ochranné známky společnosti Apple Inc.</span><span class="sxs-lookup"><span data-stu-id="d04c3-119">Mac and macOS are trademarks of Apple Inc.</span></span>

<span data-ttu-id="d04c3-120">Logo velryby Docker je registrovaná ochranná známka společnosti Docker, Inc. Používá se svolením.</span><span class="sxs-lookup"><span data-stu-id="d04c3-120">The Docker whale logo is a registered trademark of Docker, Inc. Used by permission.</span></span>

<span data-ttu-id="d04c3-121">Všechny ostatní značky a loga jsou majetkem příslušných vlastníků.</span><span class="sxs-lookup"><span data-stu-id="d04c3-121">All other marks and logos are property of their respective owners.</span></span>

<span data-ttu-id="d04c3-122">Autor:</span><span class="sxs-lookup"><span data-stu-id="d04c3-122">Author:</span></span>

> <span data-ttu-id="d04c3-123">**Steve "ardalis" Smith** - softwarový architekt a trenér - [Ardalis.com](https://ardalis.com)</span><span class="sxs-lookup"><span data-stu-id="d04c3-123">**Steve "ardalis" Smith** - Software Architect and Trainer - [Ardalis.com](https://ardalis.com)</span></span>

<span data-ttu-id="d04c3-124">Editory:</span><span class="sxs-lookup"><span data-stu-id="d04c3-124">Editors:</span></span>

> <span data-ttu-id="d04c3-125">**Maira Wenzel**</span><span class="sxs-lookup"><span data-stu-id="d04c3-125">**Maira Wenzel**</span></span>

## <a name="introduction"></a><span data-ttu-id="d04c3-126">Úvod</span><span class="sxs-lookup"><span data-stu-id="d04c3-126">Introduction</span></span>

<span data-ttu-id="d04c3-127">.NET Core a ASP.NET Core nabízejí několik výhod oproti tradičnímu vývoji .NET.</span><span class="sxs-lookup"><span data-stu-id="d04c3-127">.NET Core and ASP.NET Core offer several advantages over traditional .NET development.</span></span> <span data-ttu-id="d04c3-128">Jádro .NET pro serverové aplikace byste měli použít, pokud jsou pro úspěch vaší aplikace důležité některé nebo všechny následující:</span><span class="sxs-lookup"><span data-stu-id="d04c3-128">You should use .NET Core for your server applications if some or all of the following are important to your application's success:</span></span>

- <span data-ttu-id="d04c3-129">Podpora napříč platformami.</span><span class="sxs-lookup"><span data-stu-id="d04c3-129">Cross-platform support.</span></span>

- <span data-ttu-id="d04c3-130">Použití mikroslužeb.</span><span class="sxs-lookup"><span data-stu-id="d04c3-130">Use of microservices.</span></span>

- <span data-ttu-id="d04c3-131">Použití kontejnerů Dockeru.</span><span class="sxs-lookup"><span data-stu-id="d04c3-131">Use of Docker containers.</span></span>

- <span data-ttu-id="d04c3-132">Vysoké požadavky na výkon a škálovatelnost.</span><span class="sxs-lookup"><span data-stu-id="d04c3-132">High performance and scalability requirements.</span></span>

- <span data-ttu-id="d04c3-133">Souběžná správa verzí verzí rozhraní .NET aplikací na stejném serveru.</span><span class="sxs-lookup"><span data-stu-id="d04c3-133">Side-by-side versioning of .NET versions by application on the same server.</span></span>

<span data-ttu-id="d04c3-134">Tradiční aplikace .NET mohou a podporují mnoho z těchto požadavků, ale ASP.NET Core a .NET Core byly optimalizovány tak, aby nabízely vylepšenou podporu pro výše uvedené scénáře.</span><span class="sxs-lookup"><span data-stu-id="d04c3-134">Traditional .NET applications can and do support many of these requirements, but ASP.NET Core and .NET Core have been optimized to offer improved support for the above scenarios.</span></span>

<span data-ttu-id="d04c3-135">Stále více organizací se rozhodlo hostovat své webové aplikace v cloudu pomocí služeb, jako je Microsoft Azure.</span><span class="sxs-lookup"><span data-stu-id="d04c3-135">More and more organizations are choosing to host their web applications in the cloud using services like Microsoft Azure.</span></span> <span data-ttu-id="d04c3-136">Měli byste zvážit hostování aplikace v cloudu, pokud jsou pro vaši aplikaci nebo organizaci důležité následující:</span><span class="sxs-lookup"><span data-stu-id="d04c3-136">You should consider hosting your application in the cloud if the following are important to your application or organization:</span></span>

- <span data-ttu-id="d04c3-137">Snížení investic do nákladů datových center (hardware, software, prostor, nástroje, správa serverů atd.)</span><span class="sxs-lookup"><span data-stu-id="d04c3-137">Reduced investment in data center costs (hardware, software, space, utilities, server management, etc.)</span></span>

- <span data-ttu-id="d04c3-138">Flexibilní ceny (platí na základě využití, ne pro nevyužitou kapacitu).</span><span class="sxs-lookup"><span data-stu-id="d04c3-138">Flexible pricing (pay based on usage, not for idle capacity).</span></span>

- <span data-ttu-id="d04c3-139">Extrémní spolehlivost.</span><span class="sxs-lookup"><span data-stu-id="d04c3-139">Extreme reliability.</span></span>

- <span data-ttu-id="d04c3-140">Vylepšená mobilita aplikací; snadno změnit, kde a jak je vaše aplikace nasazena.</span><span class="sxs-lookup"><span data-stu-id="d04c3-140">Improved app mobility; easily change where and how your app is deployed.</span></span>

- <span data-ttu-id="d04c3-141">Flexibilní kapacita; stupnice nahoru nebo dolů na základě skutečných potřeb.</span><span class="sxs-lookup"><span data-stu-id="d04c3-141">Flexible capacity; scale up or down based on actual needs.</span></span>

<span data-ttu-id="d04c3-142">Vytváření webových aplikací s ASP.NET Core, hostované v Azure, nabízí mnoho konkurenčních výhod oproti tradičním alternativám.</span><span class="sxs-lookup"><span data-stu-id="d04c3-142">Building web applications with ASP.NET Core, hosted in Azure, offers many competitive advantages over traditional alternatives.</span></span> <span data-ttu-id="d04c3-143">ASP.NET Core je optimalizovaný pro moderní postupy vývoje webových aplikací a scénáře cloudového hostování.</span><span class="sxs-lookup"><span data-stu-id="d04c3-143">ASP.NET Core is optimized for modern web application development practices and cloud hosting scenarios.</span></span> <span data-ttu-id="d04c3-144">V této příručce se dozvíte, jak navrhovat ASP.NET základní aplikace, abyste tyto možnosti co nejlépe využili.</span><span class="sxs-lookup"><span data-stu-id="d04c3-144">In this guide, you'll learn how to architect your ASP.NET Core applications to best take advantage of these capabilities.</span></span>

## <a name="purpose"></a><span data-ttu-id="d04c3-145">Účel</span><span class="sxs-lookup"><span data-stu-id="d04c3-145">Purpose</span></span>

<span data-ttu-id="d04c3-146">Tato příručka poskytuje komplexní pokyny pro vytváření *monolitických* webových aplikací pomocí ASP.NET Core a Azure.</span><span class="sxs-lookup"><span data-stu-id="d04c3-146">This guide provides end-to-end guidance on building *monolithic* web applications using ASP.NET Core and Azure.</span></span> <span data-ttu-id="d04c3-147">V tomto kontextu "monolitické" odkazuje na skutečnost, že tyto aplikace jsou nasazeny jako jeden celek, nikoli jako kolekce vzájemně propojených služeb a aplikací.</span><span class="sxs-lookup"><span data-stu-id="d04c3-147">In this context, "monolithic" refers to the fact that these applications are deployed as a single unit, not as a collection of interacting services and applications.</span></span>

<span data-ttu-id="d04c3-148">Tato příručka je doplňkem ["_.NET Microservices. Architektura pro kontejnerizované aplikace .NET_,](../microservices/index.md) která se více zaměřuje na Docker, Mikroslužby a nasazení kontejnerů pro hostování podnikových aplikací.</span><span class="sxs-lookup"><span data-stu-id="d04c3-148">This guide is complementary to the ["_.NET Microservices. Architecture for Containerized .NET Applications_"](../microservices/index.md) which focuses more on Docker, Microservices, and Deployment of Containers to host enterprise applications.</span></span>

### <a name="net-microservices-architecture-for-containerized-net-applications"></a><span data-ttu-id="d04c3-149">Mikroslužby .NET.</span><span class="sxs-lookup"><span data-stu-id="d04c3-149">.NET Microservices.</span></span> <span data-ttu-id="d04c3-150">Architektura pro kontejnerizované aplikace .NET</span><span class="sxs-lookup"><span data-stu-id="d04c3-150">Architecture for Containerized .NET Applications</span></span>

- <span data-ttu-id="d04c3-151">**e-kniha**</span><span class="sxs-lookup"><span data-stu-id="d04c3-151">**e-book**</span></span>  
  <https://aka.ms/MicroservicesEbook>
- <span data-ttu-id="d04c3-152">**Ukázková aplikace**</span><span class="sxs-lookup"><span data-stu-id="d04c3-152">**Sample Application**</span></span>  
  <https://aka.ms/microservicesarchitecture>

## <a name="who-should-use-this-guide"></a><span data-ttu-id="d04c3-153">Kdo by měl používat tuto příručku</span><span class="sxs-lookup"><span data-stu-id="d04c3-153">Who should use this guide</span></span>

<span data-ttu-id="d04c3-154">Cílovou skupinou pro tuto příručku jsou především vývojáři, vedoucí vývoje a architekti, kteří se zajímají o vytváření moderních webových aplikací pomocí technologií a služeb společnosti Microsoft v cloudu.</span><span class="sxs-lookup"><span data-stu-id="d04c3-154">The audience for this guide is mainly developers, development leads, and architects who are interested in building modern web applications using Microsoft technologies and services in the cloud.</span></span>

<span data-ttu-id="d04c3-155">Sekundární okruh uživatelů je technická rozhodovací skupina, která už zná ASP.NET nebo Azure a hledají informace o tom, jestli má smysl upgradovat na ASP.NET Core pro nové nebo stávající projekty.</span><span class="sxs-lookup"><span data-stu-id="d04c3-155">A secondary audience is technical decision makers who are already familiar ASP.NET or Azure and are looking for information on whether it makes sense to upgrade to ASP.NET Core for new or existing projects.</span></span>

## <a name="how-you-can-use-this-guide"></a><span data-ttu-id="d04c3-156">Jak můžete tuto příručku používat</span><span class="sxs-lookup"><span data-stu-id="d04c3-156">How you can use this guide</span></span>

<span data-ttu-id="d04c3-157">Tato příručka byla zhuštěna do relativně malého dokumentu, který se zaměřuje na vytváření webových aplikací s moderními technologiemi .NET a Windows Azure.</span><span class="sxs-lookup"><span data-stu-id="d04c3-157">This guide has been condensed into a relatively small document that focuses on building web applications with modern .NET technologies and Windows Azure.</span></span> <span data-ttu-id="d04c3-158">Jako takový, to může být chápána v plném rozsahu poskytnout základ pro pochopení těchto aplikací a jejich technické aspekty.</span><span class="sxs-lookup"><span data-stu-id="d04c3-158">As such, it can be read in its entirety to provide a foundation of understanding such applications and their technical considerations.</span></span> <span data-ttu-id="d04c3-159">Průvodce, spolu s jeho ukázkovou aplikací, může také sloužit jako výchozí bod nebo odkaz.</span><span class="sxs-lookup"><span data-stu-id="d04c3-159">The guide, along with its sample application, can also serve as a starting point or reference.</span></span> <span data-ttu-id="d04c3-160">Použijte přidruženou ukázkovou aplikaci jako šablonu pro vlastní aplikace nebo se podívejte, jak můžete uspořádat součásti aplikace.</span><span class="sxs-lookup"><span data-stu-id="d04c3-160">Use the associated sample application as a template for your own applications, or to see how you might organize your application's component parts.</span></span> <span data-ttu-id="d04c3-161">Při zvažování těchto možností pro vlastní aplikaci se vraťte k principům průvodce a pokrytí možností architektury a technologií a k úvahám o rozhodování.</span><span class="sxs-lookup"><span data-stu-id="d04c3-161">Refer back to the guide's principles and coverage of architecture and technology options and decision considerations when you're weighing these choices for your own application.</span></span>

<span data-ttu-id="d04c3-162">Neváhejte a předat tuto příručku svému týmu, abyste zajistili společné porozumění těmto úvahám a příležitostem.</span><span class="sxs-lookup"><span data-stu-id="d04c3-162">Feel free to forward this guide to your team to help ensure a common understanding of these considerations and opportunities.</span></span> <span data-ttu-id="d04c3-163">To, že všichni pracují ze společného souboru terminologie a základních principů, pomáhá zajistit konzistentní uplatňování architektonických vzorů a postupů.</span><span class="sxs-lookup"><span data-stu-id="d04c3-163">Having everybody working from a common set of terminology and underlying principles helps ensure consistent application of architectural patterns and practices.</span></span>

## <a name="references"></a><span data-ttu-id="d04c3-164">Odkazy</span><span class="sxs-lookup"><span data-stu-id="d04c3-164">References</span></span>

- <span data-ttu-id="d04c3-165">**Volba mezi .NET Core a .NET Framework pro serverové aplikace**</span><span class="sxs-lookup"><span data-stu-id="d04c3-165">**Choosing between .NET Core and .NET Framework for server apps**</span></span>  
  [https://docs.microsoft.com/dotnet/standard/choosing-core-framework-server](../../standard/choosing-core-framework-server.md)

>[!div class="step-by-step"]
>[<span data-ttu-id="d04c3-166">Další</span><span class="sxs-lookup"><span data-stu-id="d04c3-166">Next</span></span>](modern-web-applications-characteristics.md)
