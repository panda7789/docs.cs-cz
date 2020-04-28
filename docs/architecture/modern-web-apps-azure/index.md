---
title: Navrhování moderních webových aplikací pomocí ASP.NET Core a Azure
description: Příručka, která poskytuje kompletní pokyny k vytváření monolitické webových aplikací pomocí ASP.NET Core a Azure.
author: ardalis
ms.author: wiwagn
ms.date: 12/4/2019
ms.openlocfilehash: 6ae5de0381c8796faee74abd40f688214ab13211
ms.sourcegitcommit: 5988e9a29cedb8757320817deda3c08c6f44a6aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2020
ms.locfileid: "82199960"
---
# <a name="architect-modern-web-applications-with-aspnet-core-and-azure"></a><span data-ttu-id="c9fcb-103">Navrhování moderních webových aplikací pomocí ASP.NET Core a Azure</span><span class="sxs-lookup"><span data-stu-id="c9fcb-103">Architect Modern Web Applications with ASP.NET Core and Azure</span></span>

![Titulní obrázek knihy Průvodce moderními webovými aplikacemi architektury](./media/index/web-application-guide-cover-image.png)

<span data-ttu-id="c9fcb-105">**Edice verze 3.1** – aktualizace na ASP.NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="c9fcb-105">**EDITION v3.1** - Updated to ASP.NET Core 3.1</span></span>

<span data-ttu-id="c9fcb-106">PUBLIKOVAL(A)</span><span class="sxs-lookup"><span data-stu-id="c9fcb-106">PUBLISHED BY</span></span>

<span data-ttu-id="c9fcb-107">Týmy produktů Microsoft Developer divize, .NET a Visual Studio</span><span class="sxs-lookup"><span data-stu-id="c9fcb-107">Microsoft Developer Division, .NET, and Visual Studio product teams</span></span>

<span data-ttu-id="c9fcb-108">Divize společnosti Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="c9fcb-108">A division of Microsoft Corporation</span></span>

<span data-ttu-id="c9fcb-109">One Microsoft Way</span><span class="sxs-lookup"><span data-stu-id="c9fcb-109">One Microsoft Way</span></span>

<span data-ttu-id="c9fcb-110">Redmond, Washington 98052-6399</span><span class="sxs-lookup"><span data-stu-id="c9fcb-110">Redmond, Washington 98052-6399</span></span>

<span data-ttu-id="c9fcb-111">Copyright © 2020 od společnosti Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="c9fcb-111">Copyright © 2020 by Microsoft Corporation</span></span>

<span data-ttu-id="c9fcb-112">Všechna práva vyhrazena.</span><span class="sxs-lookup"><span data-stu-id="c9fcb-112">All rights reserved.</span></span> <span data-ttu-id="c9fcb-113">Žádná část obsahu této knihy se nedá reprodukovat ani přenést v jakékoli formě nebo jakýmkoli způsobem bez písemného svolení vydavatele.</span><span class="sxs-lookup"><span data-stu-id="c9fcb-113">No part of the contents of this book may be reproduced or transmitted in any form or by any means without the written permission of the publisher.</span></span>

<span data-ttu-id="c9fcb-114">Tato kniha je k dispozici "tak jak jsou" a vyjadřuje zobrazení a stanoviska autora.</span><span class="sxs-lookup"><span data-stu-id="c9fcb-114">This book is provided "as-is" and expresses the author's views and opinions.</span></span> <span data-ttu-id="c9fcb-115">Zobrazení, názory a informace vyjádřené v této knize, včetně adres URL a dalších odkazů na internetové weby, se mohou změnit bez předchozího upozornění.</span><span class="sxs-lookup"><span data-stu-id="c9fcb-115">The views, opinions, and information expressed in this book, including URL and other Internet website references, may change without notice.</span></span>

<span data-ttu-id="c9fcb-116">Některé zde uvedené příklady slouží pouze k znázornění a jsou smyšlené.</span><span class="sxs-lookup"><span data-stu-id="c9fcb-116">Some examples depicted herein are provided for illustration only and are fictitious.</span></span> <span data-ttu-id="c9fcb-117">Neměli byste z nich vyvozovat žádné skutečné vztahy či spojení.</span><span class="sxs-lookup"><span data-stu-id="c9fcb-117">No real association or connection is intended or should be inferred.</span></span>

<span data-ttu-id="c9fcb-118">Microsoft a ochranné známky uvedené https://www.microsoft.com na webové stránce ochranné známky jsou ochranné známky skupiny společností Microsoft.</span><span class="sxs-lookup"><span data-stu-id="c9fcb-118">Microsoft and the trademarks listed at https://www.microsoft.com on the "Trademarks" webpage are trademarks of the Microsoft group of companies.</span></span>

<span data-ttu-id="c9fcb-119">Mac a macOS jsou ochranné známky společnosti Apple Inc.</span><span class="sxs-lookup"><span data-stu-id="c9fcb-119">Mac and macOS are trademarks of Apple Inc.</span></span>

<span data-ttu-id="c9fcb-120">Logo Docker Whale je registrovaná ochranná známka společnosti Docker, Inc., kterou používá oprávnění.</span><span class="sxs-lookup"><span data-stu-id="c9fcb-120">The Docker whale logo is a registered trademark of Docker, Inc. Used by permission.</span></span>

<span data-ttu-id="c9fcb-121">Všechny ostatní značky a loga jsou majetkem příslušných vlastníků.</span><span class="sxs-lookup"><span data-stu-id="c9fcb-121">All other marks and logos are property of their respective owners.</span></span>

<span data-ttu-id="c9fcb-122">Autor:</span><span class="sxs-lookup"><span data-stu-id="c9fcb-122">Author:</span></span>

> <span data-ttu-id="c9fcb-123">**Steve "ardalis" Smith** -Software Architect a Trainer- [Ardalis.com](https://ardalis.com)</span><span class="sxs-lookup"><span data-stu-id="c9fcb-123">**Steve "ardalis" Smith** - Software Architect and Trainer - [Ardalis.com](https://ardalis.com)</span></span>

<span data-ttu-id="c9fcb-124">Editory</span><span class="sxs-lookup"><span data-stu-id="c9fcb-124">Editors:</span></span>

> <span data-ttu-id="c9fcb-125">**Maira Wenzel**</span><span class="sxs-lookup"><span data-stu-id="c9fcb-125">**Maira Wenzel**</span></span>

## <a name="introduction"></a><span data-ttu-id="c9fcb-126">Úvod</span><span class="sxs-lookup"><span data-stu-id="c9fcb-126">Introduction</span></span>

<span data-ttu-id="c9fcb-127">.NET Core a ASP.NET Core nabízí několik výhod oproti tradičnímu vývoji pro .NET.</span><span class="sxs-lookup"><span data-stu-id="c9fcb-127">.NET Core and ASP.NET Core offer several advantages over traditional .NET development.</span></span> <span data-ttu-id="c9fcb-128">Pro své serverové aplikace byste měli použít .NET Core, pokud jsou některé nebo všechny následující důležité pro úspěch vaší aplikace:</span><span class="sxs-lookup"><span data-stu-id="c9fcb-128">You should use .NET Core for your server applications if some or all of the following are important to your application's success:</span></span>

- <span data-ttu-id="c9fcb-129">Podpora pro různé platformy.</span><span class="sxs-lookup"><span data-stu-id="c9fcb-129">Cross-platform support.</span></span>

- <span data-ttu-id="c9fcb-130">Použití mikroslužeb.</span><span class="sxs-lookup"><span data-stu-id="c9fcb-130">Use of microservices.</span></span>

- <span data-ttu-id="c9fcb-131">Použití kontejnerů Docker.</span><span class="sxs-lookup"><span data-stu-id="c9fcb-131">Use of Docker containers.</span></span>

- <span data-ttu-id="c9fcb-132">Vysoký výkon a požadavky na škálovatelnost.</span><span class="sxs-lookup"><span data-stu-id="c9fcb-132">High performance and scalability requirements.</span></span>

- <span data-ttu-id="c9fcb-133">Souběžná Správa verzí rozhraní .NET podle aplikace na stejném serveru.</span><span class="sxs-lookup"><span data-stu-id="c9fcb-133">Side-by-side versioning of .NET versions by application on the same server.</span></span>

<span data-ttu-id="c9fcb-134">Tradiční aplikace .NET můžou a podporují mnoho těchto požadavků, ale ASP.NET Core a .NET Core jsou optimalizované tak, aby nabízely vylepšenou podporu pro výše uvedené scénáře.</span><span class="sxs-lookup"><span data-stu-id="c9fcb-134">Traditional .NET applications can and do support many of these requirements, but ASP.NET Core and .NET Core have been optimized to offer improved support for the above scenarios.</span></span>

<span data-ttu-id="c9fcb-135">Další a více organizací se volí pro hostování webových aplikací v cloudu pomocí služeb, jako je Microsoft Azure.</span><span class="sxs-lookup"><span data-stu-id="c9fcb-135">More and more organizations are choosing to host their web applications in the cloud using services like Microsoft Azure.</span></span> <span data-ttu-id="c9fcb-136">Měli byste zvážit hostování aplikace v cloudu, pokud jsou pro vaši aplikaci nebo organizaci důležité následující:</span><span class="sxs-lookup"><span data-stu-id="c9fcb-136">You should consider hosting your application in the cloud if the following are important to your application or organization:</span></span>

- <span data-ttu-id="c9fcb-137">Snížená investice do nákladů datového centra (hardware, software, prostor, nástroje, Správa serveru atd.)</span><span class="sxs-lookup"><span data-stu-id="c9fcb-137">Reduced investment in data center costs (hardware, software, space, utilities, server management, etc.)</span></span>

- <span data-ttu-id="c9fcb-138">Flexibilní ceny (placené na základě využití, ne pro nečinné kapacity).</span><span class="sxs-lookup"><span data-stu-id="c9fcb-138">Flexible pricing (pay based on usage, not for idle capacity).</span></span>

- <span data-ttu-id="c9fcb-139">Extrémní spolehlivost.</span><span class="sxs-lookup"><span data-stu-id="c9fcb-139">Extreme reliability.</span></span>

- <span data-ttu-id="c9fcb-140">Vylepšená mobilita aplikací; Snadná změna místa a způsobu nasazení aplikace</span><span class="sxs-lookup"><span data-stu-id="c9fcb-140">Improved app mobility; easily change where and how your app is deployed.</span></span>

- <span data-ttu-id="c9fcb-141">Flexibilní kapacita; horizontální navýšení nebo snížení kapacity podle skutečných potřeb</span><span class="sxs-lookup"><span data-stu-id="c9fcb-141">Flexible capacity; scale up or down based on actual needs.</span></span>

<span data-ttu-id="c9fcb-142">Vytváření webových aplikací pomocí ASP.NET Core hostovaných v Azure nabízí řadu konkurenčních výhod oproti tradičním alternativám.</span><span class="sxs-lookup"><span data-stu-id="c9fcb-142">Building web applications with ASP.NET Core, hosted in Azure, offers many competitive advantages over traditional alternatives.</span></span> <span data-ttu-id="c9fcb-143">ASP.NET Core je optimalizovaná pro moderní postupy pro vývoj webových aplikací a hostování cloudu.</span><span class="sxs-lookup"><span data-stu-id="c9fcb-143">ASP.NET Core is optimized for modern web application development practices and cloud hosting scenarios.</span></span> <span data-ttu-id="c9fcb-144">V této příručce se dozvíte, jak navrhovat aplikace ASP.NET Core, abyste mohli nejlépe využít tyto možnosti.</span><span class="sxs-lookup"><span data-stu-id="c9fcb-144">In this guide, you'll learn how to architect your ASP.NET Core applications to best take advantage of these capabilities.</span></span>

## <a name="purpose"></a><span data-ttu-id="c9fcb-145">Účel</span><span class="sxs-lookup"><span data-stu-id="c9fcb-145">Purpose</span></span>

<span data-ttu-id="c9fcb-146">Tato příručka poskytuje kompletní pokyny k vytváření *monolitické* webových aplikací pomocí ASP.NET Core a Azure.</span><span class="sxs-lookup"><span data-stu-id="c9fcb-146">This guide provides end-to-end guidance on building *monolithic* web applications using ASP.NET Core and Azure.</span></span> <span data-ttu-id="c9fcb-147">V tomto kontextu odkazuje "monolitické" na skutečnost, že tyto aplikace jsou nasazeny jako jediná jednotka, nikoli jako kolekce interaktivních služeb a aplikací.</span><span class="sxs-lookup"><span data-stu-id="c9fcb-147">In this context, "monolithic" refers to the fact that these applications are deployed as a single unit, not as a collection of interacting services and applications.</span></span>

<span data-ttu-id="c9fcb-148">Tato příručka je doplňkem ["_mikroslužby .NET". Architektura pro kontejnerové aplikace .NET_](../microservices/index.md), která se zaměřuje na Další informace o Docker, mikroslužbách a nasazení kontejnerů pro hostování podnikových aplikací.</span><span class="sxs-lookup"><span data-stu-id="c9fcb-148">This guide is complementary to ["_.NET Microservices. Architecture for Containerized .NET Applications_"](../microservices/index.md), which focuses more on Docker, microservices, and deployment of containers to host enterprise applications.</span></span>

### <a name="net-microservices-architecture-for-containerized-net-applications"></a><span data-ttu-id="c9fcb-149">Mikroslužby .NET.</span><span class="sxs-lookup"><span data-stu-id="c9fcb-149">.NET Microservices.</span></span> <span data-ttu-id="c9fcb-150">Architektura pro kontejnerizované aplikace .NET</span><span class="sxs-lookup"><span data-stu-id="c9fcb-150">Architecture for Containerized .NET Applications</span></span>

- <span data-ttu-id="c9fcb-151">**Elektronická kniha**</span><span class="sxs-lookup"><span data-stu-id="c9fcb-151">**e-book**</span></span>  
  <https://aka.ms/MicroservicesEbook>
- <span data-ttu-id="c9fcb-152">**Ukázková aplikace**</span><span class="sxs-lookup"><span data-stu-id="c9fcb-152">**Sample Application**</span></span>  
  <https://aka.ms/microservicesarchitecture>

## <a name="who-should-use-this-guide"></a><span data-ttu-id="c9fcb-153">Kdo by měl používat tuto příručku</span><span class="sxs-lookup"><span data-stu-id="c9fcb-153">Who should use this guide</span></span>

<span data-ttu-id="c9fcb-154">Cílová skupina pro tento průvodce je hlavně vývojářům, vedoucím vývoje a architektům, kteří mají zájem o vytváření moderních webových aplikací s využitím technologií a služeb Microsoftu v cloudu.</span><span class="sxs-lookup"><span data-stu-id="c9fcb-154">The audience for this guide is mainly developers, development leads, and architects who are interested in building modern web applications using Microsoft technologies and services in the cloud.</span></span>

<span data-ttu-id="c9fcb-155">Sekundární cílová skupina je technickým autorem rozhodnutí, kteří už znají ASP.NET nebo Azure a hledají informace o tom, jestli má smysl upgradovat na ASP.NET Core pro nové nebo existující projekty.</span><span class="sxs-lookup"><span data-stu-id="c9fcb-155">A secondary audience is technical decision makers who are already familiar ASP.NET or Azure and are looking for information on whether it makes sense to upgrade to ASP.NET Core for new or existing projects.</span></span>

## <a name="how-you-can-use-this-guide"></a><span data-ttu-id="c9fcb-156">Jak můžete použít tuto příručku</span><span class="sxs-lookup"><span data-stu-id="c9fcb-156">How you can use this guide</span></span>

<span data-ttu-id="c9fcb-157">Tato příručka je zhuštěná do relativně malého dokumentu, který se zaměřuje na sestavování webových aplikací s využitím moderních technologií .NET a Azure.</span><span class="sxs-lookup"><span data-stu-id="c9fcb-157">This guide has been condensed into a relatively small document that focuses on building web applications with modern .NET technologies and Azure.</span></span> <span data-ttu-id="c9fcb-158">V takovém případě je lze přečíst v celém rozsahu a poskytnout základ pro porozumění takovým aplikacím a jejich technickým hlediskům.</span><span class="sxs-lookup"><span data-stu-id="c9fcb-158">As such, it can be read in its entirety to provide a foundation of understanding such applications and their technical considerations.</span></span> <span data-ttu-id="c9fcb-159">Průvodce společně s jeho ukázkovou aplikací může sloužit také jako výchozí bod nebo odkaz.</span><span class="sxs-lookup"><span data-stu-id="c9fcb-159">The guide, along with its sample application, can also serve as a starting point or reference.</span></span> <span data-ttu-id="c9fcb-160">Použijte přidruženou ukázkovou aplikaci jako šablonu pro vlastní aplikace nebo k zobrazení, jak můžete uspořádat součásti komponenty aplikace.</span><span class="sxs-lookup"><span data-stu-id="c9fcb-160">Use the associated sample application as a template for your own applications, or to see how you might organize your application's component parts.</span></span> <span data-ttu-id="c9fcb-161">Přečtěte si téma zásady a pokrytí možností architektury a technologie a rozhodnutí o rozhodování, pokud chcete zvážit, jaké možnosti máte k dispozici pro vlastní aplikaci.</span><span class="sxs-lookup"><span data-stu-id="c9fcb-161">Refer back to the guide's principles and coverage of architecture and technology options and decision considerations when you're weighing these choices for your own application.</span></span>

<span data-ttu-id="c9fcb-162">Nebojte se této příručky s vaším týmem, abyste se ujistili, že se tyto otázky a příležitosti budou porozumět běžným způsobem.</span><span class="sxs-lookup"><span data-stu-id="c9fcb-162">Feel free to forward this guide to your team to help ensure a common understanding of these considerations and opportunities.</span></span> <span data-ttu-id="c9fcb-163">Díky tomu, že všichni pracují se společnou sadou terminologie a základními principy, pomáhají zajistit konzistentní používání vzorů a postupů architektury.</span><span class="sxs-lookup"><span data-stu-id="c9fcb-163">Having everybody working from a common set of terminology and underlying principles helps ensure consistent application of architectural patterns and practices.</span></span>

## <a name="references"></a><span data-ttu-id="c9fcb-164">Odkazy</span><span class="sxs-lookup"><span data-stu-id="c9fcb-164">References</span></span>

- <span data-ttu-id="c9fcb-165">**Volba mezi .NET Core a .NET Framework pro serverové aplikace**</span><span class="sxs-lookup"><span data-stu-id="c9fcb-165">**Choosing between .NET Core and .NET Framework for server apps**</span></span>  
  [https://docs.microsoft.com/dotnet/standard/choosing-core-framework-server](../../standard/choosing-core-framework-server.md)

>[!div class="step-by-step"]
>[<span data-ttu-id="c9fcb-166">Další</span><span class="sxs-lookup"><span data-stu-id="c9fcb-166">Next</span></span>](modern-web-applications-characteristics.md)
