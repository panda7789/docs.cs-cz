---
title: Architekt moderních webových aplikací pomocí ASP.NET Core a Azure
description: Příručka, která poskytuje kompletní pokyny k vytváření monolitické webových aplikací pomocí ASP.NET Core a Azure.
author: ardalis
ms.author: wiwagn
ms.date: 01/30/2019
ms.openlocfilehash: 739dd607aaa45f73e777a30c6495e329236fee17
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "70296290"
---
# <a name="architect-modern-web-applications-with-aspnet-core-and-azure"></a><span data-ttu-id="2ec68-103">Architekt moderních webových aplikací pomocí ASP.NET Core a Azure</span><span class="sxs-lookup"><span data-stu-id="2ec68-103">Architect Modern Web Applications with ASP.NET Core and Azure</span></span>

![Titulní obrázek Průvodce moderními webovými aplikacemi v architektech](./media/index/web-application-guide-cover-image.png)

<span data-ttu-id="2ec68-105">PUBLIKOVAL (A)</span><span class="sxs-lookup"><span data-stu-id="2ec68-105">PUBLISHED BY</span></span>

<span data-ttu-id="2ec68-106">Týmy produktů Microsoft Developer divize, .NET a Visual Studio</span><span class="sxs-lookup"><span data-stu-id="2ec68-106">Microsoft Developer Division, .NET, and Visual Studio product teams</span></span>

<span data-ttu-id="2ec68-107">Divize společnosti Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="2ec68-107">A division of Microsoft Corporation</span></span>

<span data-ttu-id="2ec68-108">Jeden způsob Microsoftu</span><span class="sxs-lookup"><span data-stu-id="2ec68-108">One Microsoft Way</span></span>

<span data-ttu-id="2ec68-109">Redmond, Washington 98052-6399</span><span class="sxs-lookup"><span data-stu-id="2ec68-109">Redmond, Washington 98052-6399</span></span>

<span data-ttu-id="2ec68-110">Copyright © 2019 by Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="2ec68-110">Copyright © 2019 by Microsoft Corporation</span></span>

<span data-ttu-id="2ec68-111">Všechna práva vyhrazena.</span><span class="sxs-lookup"><span data-stu-id="2ec68-111">All rights reserved.</span></span> <span data-ttu-id="2ec68-112">Žádná část obsahu této knihy se nedá reprodukovat ani přenést v jakékoli formě nebo jakýmkoli způsobem bez písemného svolení vydavatele.</span><span class="sxs-lookup"><span data-stu-id="2ec68-112">No part of the contents of this book may be reproduced or transmitted in any form or by any means without the written permission of the publisher.</span></span>

<span data-ttu-id="2ec68-113">Tato kniha je k dispozici "tak jak jsou" a vyjadřuje zobrazení a stanoviska autora.</span><span class="sxs-lookup"><span data-stu-id="2ec68-113">This book is provided “as-is” and expresses the author’s views and opinions.</span></span> <span data-ttu-id="2ec68-114">Zobrazení, názory a informace vyjádřené v této knize, včetně adres URL a dalších odkazů na internetové weby, se mohou změnit bez předchozího upozornění.</span><span class="sxs-lookup"><span data-stu-id="2ec68-114">The views, opinions and information expressed in this book, including URL and other Internet website references, may change without notice.</span></span>

<span data-ttu-id="2ec68-115">Některé příklady, které jsou zde uvedeny, jsou k dispozici pouze pro ilustraci a jsou smyšlené.</span><span class="sxs-lookup"><span data-stu-id="2ec68-115">Some examples depicted herein are provided for illustration only and are fictitious.</span></span> <span data-ttu-id="2ec68-116">Neexistuje žádné skutečné přidružení nebo připojení, které by mělo být odvozeno.</span><span class="sxs-lookup"><span data-stu-id="2ec68-116">No real association or connection is intended or should be inferred.</span></span>

<span data-ttu-id="2ec68-117">Microsoft a ochranné známky uvedené https://www.microsoft.com na webové stránce ochranné známky jsou ochranné známky skupiny společností Microsoft.</span><span class="sxs-lookup"><span data-stu-id="2ec68-117">Microsoft and the trademarks listed at https://www.microsoft.com on the “Trademarks” webpage are trademarks of the Microsoft group of companies.</span></span>

<span data-ttu-id="2ec68-118">Mac a macOS jsou ochranné známky společnosti Apple Inc.</span><span class="sxs-lookup"><span data-stu-id="2ec68-118">Mac and macOS are trademarks of Apple Inc.</span></span>

<span data-ttu-id="2ec68-119">Logo Docker Whale je registrovaná ochranná známka společnosti Docker, Inc. Používá se oprávněním.</span><span class="sxs-lookup"><span data-stu-id="2ec68-119">The Docker whale logo is a registered trademark of Docker, Inc. Used by permission.</span></span>

<span data-ttu-id="2ec68-120">Všechny ostatní značky a loga jsou majetkem příslušných vlastníků.</span><span class="sxs-lookup"><span data-stu-id="2ec68-120">All other marks and logos are property of their respective owners.</span></span>

<span data-ttu-id="2ec68-121">Autorizova</span><span class="sxs-lookup"><span data-stu-id="2ec68-121">Author:</span></span>

> <span data-ttu-id="2ec68-122">**Steve "ardalis" Smith** -Software Architect a Trainer- [Ardalis.com](https://ardalis.com)</span><span class="sxs-lookup"><span data-stu-id="2ec68-122">**Steve "ardalis" Smith** - Software Architect and Trainer - [Ardalis.com](https://ardalis.com)</span></span>

<span data-ttu-id="2ec68-123">Editory</span><span class="sxs-lookup"><span data-stu-id="2ec68-123">Editors:</span></span>

> <span data-ttu-id="2ec68-124">**Maira Wenzel**</span><span class="sxs-lookup"><span data-stu-id="2ec68-124">**Maira Wenzel**</span></span>

## <a name="introduction"></a><span data-ttu-id="2ec68-125">Úvod</span><span class="sxs-lookup"><span data-stu-id="2ec68-125">Introduction</span></span>

<span data-ttu-id="2ec68-126">.NET Core a ASP.NET Core nabízí několik výhod oproti tradičnímu vývoji pro .NET.</span><span class="sxs-lookup"><span data-stu-id="2ec68-126">.NET Core and ASP.NET Core offer several advantages over traditional .NET development.</span></span> <span data-ttu-id="2ec68-127">Pro své serverové aplikace byste měli použít .NET Core, pokud jsou některé nebo všechny následující důležité pro úspěch vaší aplikace:</span><span class="sxs-lookup"><span data-stu-id="2ec68-127">You should use .NET Core for your server applications if some or all of the following are important to your application's success:</span></span>

- <span data-ttu-id="2ec68-128">Podpora pro různé platformy.</span><span class="sxs-lookup"><span data-stu-id="2ec68-128">Cross-platform support.</span></span>

- <span data-ttu-id="2ec68-129">Použití mikroslužeb.</span><span class="sxs-lookup"><span data-stu-id="2ec68-129">Use of microservices.</span></span>

- <span data-ttu-id="2ec68-130">Použití kontejnerů Docker.</span><span class="sxs-lookup"><span data-stu-id="2ec68-130">Use of Docker containers.</span></span>

- <span data-ttu-id="2ec68-131">Vysoký výkon a požadavky na škálovatelnost.</span><span class="sxs-lookup"><span data-stu-id="2ec68-131">High performance and scalability requirements.</span></span>

- <span data-ttu-id="2ec68-132">Souběžná Správa verzí rozhraní .NET podle aplikace na stejném serveru.</span><span class="sxs-lookup"><span data-stu-id="2ec68-132">Side-by-side versioning of .NET versions by application on the same server.</span></span>

<span data-ttu-id="2ec68-133">Tradiční aplikace .NET můžou a podporují mnoho těchto požadavků, ale ASP.NET Core a .NET Core jsou optimalizované tak, aby nabízely vylepšenou podporu pro výše uvedené scénáře.</span><span class="sxs-lookup"><span data-stu-id="2ec68-133">Traditional .NET applications can and do support many of these requirements, but ASP.NET Core and .NET Core have been optimized to offer improved support for the above scenarios.</span></span>

<span data-ttu-id="2ec68-134">Další a více organizací se volí pro hostování webových aplikací v cloudu pomocí služeb, jako je Microsoft Azure.</span><span class="sxs-lookup"><span data-stu-id="2ec68-134">More and more organizations are choosing to host their web applications in the cloud using services like Microsoft Azure.</span></span> <span data-ttu-id="2ec68-135">Měli byste zvážit hostování aplikace v cloudu, pokud jsou pro vaši aplikaci nebo organizaci důležité následující:</span><span class="sxs-lookup"><span data-stu-id="2ec68-135">You should consider hosting your application in the cloud if the following are important to your application or organization:</span></span>

- <span data-ttu-id="2ec68-136">Snížená investice do nákladů datového centra (hardware, software, prostor, nástroje, Správa serveru atd.)</span><span class="sxs-lookup"><span data-stu-id="2ec68-136">Reduced investment in data center costs (hardware, software, space, utilities, server management, etc.)</span></span>

- <span data-ttu-id="2ec68-137">Flexibilní ceny (placené na základě využití, ne pro nečinné kapacity).</span><span class="sxs-lookup"><span data-stu-id="2ec68-137">Flexible pricing (pay based on usage, not for idle capacity).</span></span>

- <span data-ttu-id="2ec68-138">Extrémní spolehlivost.</span><span class="sxs-lookup"><span data-stu-id="2ec68-138">Extreme reliability.</span></span>

- <span data-ttu-id="2ec68-139">Vylepšená mobilita aplikací; Snadná změna místa a způsobu nasazení aplikace</span><span class="sxs-lookup"><span data-stu-id="2ec68-139">Improved app mobility; easily change where and how your app is deployed.</span></span>

- <span data-ttu-id="2ec68-140">Flexibilní kapacita; horizontální navýšení nebo snížení kapacity podle skutečných potřeb</span><span class="sxs-lookup"><span data-stu-id="2ec68-140">Flexible capacity; scale up or down based on actual needs.</span></span>

<span data-ttu-id="2ec68-141">Vytváření webových aplikací pomocí ASP.NET Core hostovaných v Azure nabízí řadu konkurenčních výhod oproti tradičním alternativám.</span><span class="sxs-lookup"><span data-stu-id="2ec68-141">Building web applications with ASP.NET Core, hosted in Azure, offers many competitive advantages over traditional alternatives.</span></span> <span data-ttu-id="2ec68-142">ASP.NET Core je optimalizovaná pro moderní postupy pro vývoj webových aplikací a hostování cloudu.</span><span class="sxs-lookup"><span data-stu-id="2ec68-142">ASP.NET Core is optimized for modern web application development practices and cloud hosting scenarios.</span></span> <span data-ttu-id="2ec68-143">V této příručce se dozvíte, jak navrhovat aplikace ASP.NET Core, abyste mohli nejlépe využít tyto možnosti.</span><span class="sxs-lookup"><span data-stu-id="2ec68-143">In this guide, you'll learn how to architect your ASP.NET Core applications to best take advantage of these capabilities.</span></span>

## <a name="purpose"></a><span data-ttu-id="2ec68-144">Účel</span><span class="sxs-lookup"><span data-stu-id="2ec68-144">Purpose</span></span>

<span data-ttu-id="2ec68-145">Tato příručka poskytuje kompletní pokyny k vytváření *monolitické* webových aplikací pomocí ASP.NET Core a Azure.</span><span class="sxs-lookup"><span data-stu-id="2ec68-145">This guide provides end-to-end guidance on building *monolithic* web applications using ASP.NET Core and Azure.</span></span> <span data-ttu-id="2ec68-146">V tomto kontextu odkazuje "monolitické" na skutečnost, že tyto aplikace jsou nasazeny jako jediná jednotka, nikoli jako kolekce interaktivních služeb a aplikací.</span><span class="sxs-lookup"><span data-stu-id="2ec68-146">In this context, "monolithic" refers to the fact that these applications are deployed as a single unit, not as a collection of interacting services and applications.</span></span>

<span data-ttu-id="2ec68-147">Tato příručka je doplňkem k ["_mikroslužbám .NET". Architektura pro kontejnerové aplikace_](../microservices/index.md) .NET, která se zaměřuje na Další informace o Docker, mikroslužbách a nasazení kontejnerů pro hostování podnikových aplikací.</span><span class="sxs-lookup"><span data-stu-id="2ec68-147">This guide is complementary to the ["_.NET Microservices. Architecture for Containerized .NET Applications_"](../microservices/index.md) which focuses more on Docker, Microservices, and Deployment of Containers to host enterprise applications.</span></span>

### <a name="net-microservices-architecture-for-containerized-net-applications"></a><span data-ttu-id="2ec68-148">Mikroslužby .NET.</span><span class="sxs-lookup"><span data-stu-id="2ec68-148">.NET Microservices.</span></span> <span data-ttu-id="2ec68-149">Architektura pro kontejnerizované aplikace .NET</span><span class="sxs-lookup"><span data-stu-id="2ec68-149">Architecture for Containerized .NET Applications</span></span>

- <span data-ttu-id="2ec68-150">**Elektronická kniha**</span><span class="sxs-lookup"><span data-stu-id="2ec68-150">**e-book**</span></span>  
  <https://aka.ms/MicroservicesEbook>
- <span data-ttu-id="2ec68-151">**Ukázková aplikace**</span><span class="sxs-lookup"><span data-stu-id="2ec68-151">**Sample Application**</span></span>  
  <https://aka.ms/microservicesarchitecture>

## <a name="who-should-use-this-guide"></a><span data-ttu-id="2ec68-152">Kdo by měl používat tuto příručku</span><span class="sxs-lookup"><span data-stu-id="2ec68-152">Who should use this guide</span></span>

<span data-ttu-id="2ec68-153">Cílová skupina pro tento průvodce je hlavně vývojářům, vedoucím vývoje a architektům, kteří mají zájem o vytváření moderních webových aplikací s využitím technologií a služeb Microsoftu v cloudu.</span><span class="sxs-lookup"><span data-stu-id="2ec68-153">The audience for this guide is mainly developers, development leads, and architects who are interested in building modern web applications using Microsoft technologies and services in the cloud.</span></span>

<span data-ttu-id="2ec68-154">Sekundární cílová skupina je technickým autorem rozhodnutí, kteří už znají ASP.NET nebo Azure a hledají informace o tom, jestli má smysl upgradovat na ASP.NET Core pro nové nebo existující projekty.</span><span class="sxs-lookup"><span data-stu-id="2ec68-154">A secondary audience is technical decision makers who are already familiar ASP.NET or Azure and are looking for information on whether it makes sense to upgrade to ASP.NET Core for new or existing projects.</span></span>

## <a name="how-you-can-use-this-guide"></a><span data-ttu-id="2ec68-155">Jak můžete použít tuto příručku</span><span class="sxs-lookup"><span data-stu-id="2ec68-155">How you can use this guide</span></span>

<span data-ttu-id="2ec68-156">Tato příručka je zhuštěná do relativně malého dokumentu, který se zaměřuje na sestavování webových aplikací s využitím moderních technologií .NET a Windows Azure.</span><span class="sxs-lookup"><span data-stu-id="2ec68-156">This guide has been condensed into a relatively small document that focuses on building web applications with modern .NET technologies and Windows Azure.</span></span> <span data-ttu-id="2ec68-157">V takovém případě je lze přečíst v celém rozsahu a poskytnout základ pro porozumění takovým aplikacím a jejich technickým hlediskům.</span><span class="sxs-lookup"><span data-stu-id="2ec68-157">As such, it can be read in its entirety to provide a foundation of understanding such applications and their technical considerations.</span></span> <span data-ttu-id="2ec68-158">Průvodce společně s jeho ukázkovou aplikací může sloužit také jako výchozí bod nebo odkaz.</span><span class="sxs-lookup"><span data-stu-id="2ec68-158">The guide, along with its sample application, can also serve as a starting point or reference.</span></span> <span data-ttu-id="2ec68-159">Použijte přidruženou ukázkovou aplikaci jako šablonu pro vlastní aplikace nebo k zobrazení, jak můžete uspořádat součásti komponenty aplikace.</span><span class="sxs-lookup"><span data-stu-id="2ec68-159">Use the associated sample application as a template for your own applications, or to see how you might organize your application's component parts.</span></span> <span data-ttu-id="2ec68-160">Přečtěte si téma zásady a pokrytí možností architektury a technologie a rozhodnutí o rozhodování, pokud chcete zvážit, jaké možnosti máte k dispozici pro vlastní aplikaci.</span><span class="sxs-lookup"><span data-stu-id="2ec68-160">Refer back to the guide's principles and coverage of architecture and technology options and decision considerations when you're weighing these choices for your own application.</span></span>

<span data-ttu-id="2ec68-161">Nebojte se této příručky s vaším týmem, abyste se ujistili, že se tyto otázky a příležitosti budou porozumět běžným způsobem.</span><span class="sxs-lookup"><span data-stu-id="2ec68-161">Feel free to forward this guide to your team to help ensure a common understanding of these considerations and opportunities.</span></span> <span data-ttu-id="2ec68-162">Díky tomu, že všichni pracují se společnou sadou terminologie a základními principy, pomáhají zajistit konzistentní používání vzorů a postupů architektury.</span><span class="sxs-lookup"><span data-stu-id="2ec68-162">Having everybody working from a common set of terminology and underlying principles helps ensure consistent application of architectural patterns and practices.</span></span>

## <a name="references"></a><span data-ttu-id="2ec68-163">Odkazy</span><span class="sxs-lookup"><span data-stu-id="2ec68-163">References</span></span>

- <span data-ttu-id="2ec68-164">**Volba mezi .NET Core a .NET Framework pro serverové aplikace**</span><span class="sxs-lookup"><span data-stu-id="2ec68-164">**Choosing between .NET Core and .NET Framework for server apps**</span></span>  
  [https://docs.microsoft.com/dotnet/standard/choosing-core-framework-server](../../standard/choosing-core-framework-server.md)

>[!div class="step-by-step"]
>[<span data-ttu-id="2ec68-165">Next</span><span class="sxs-lookup"><span data-stu-id="2ec68-165">Next</span></span>](modern-web-applications-characteristics.md)
