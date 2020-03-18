---
title: Přístupy k architektuře – aplikace bez serveru
description: Úvod k přístupům architektury pro vytváření cloudových podnikových aplikací, od n-vrstvých architektur až po bezserverové.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 74de96bef48f16ced4adf82855a740aa0afcdf1d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "72522894"
---
# <a name="architecture-approaches"></a><span data-ttu-id="76b33-103">Přístupy k architektuře</span><span class="sxs-lookup"><span data-stu-id="76b33-103">Architecture approaches</span></span>

<span data-ttu-id="76b33-104">Principy stávajících přístupů k navrhování podnikových aplikací pomáhají objasnit roli, kterou hrají serverové služby.</span><span class="sxs-lookup"><span data-stu-id="76b33-104">Understanding existing approaches to architecting enterprise apps helps clarify the role played by serverless.</span></span> <span data-ttu-id="76b33-105">Existuje mnoho přístupů a vzorů, které se vyvíjely v průběhu desetiletí vývoje softwaru, a všechny mají své vlastní klady a zápory.</span><span class="sxs-lookup"><span data-stu-id="76b33-105">There are many approaches and patterns that evolved over decades of software development, and all have their own pros and cons.</span></span> <span data-ttu-id="76b33-106">V mnoha případech nemusí konečné řešení zahrnovat rozhodování o jednotném přístupu, ale může integrovat několik přístupů.</span><span class="sxs-lookup"><span data-stu-id="76b33-106">In many cases, the ultimate solution may not involve deciding on a single approach but may integrate several approaches.</span></span> <span data-ttu-id="76b33-107">Scénáře migrace často zahrnují přechod z jednoho přístupu architektury na jiný prostřednictvím hybridního přístupu.</span><span class="sxs-lookup"><span data-stu-id="76b33-107">Migration scenarios often involve shifting from one architecture approach to another through a hybrid approach.</span></span>

<span data-ttu-id="76b33-108">Tato kapitola obsahuje přehled logických i fyzických vzorů architektury pro podnikové aplikace.</span><span class="sxs-lookup"><span data-stu-id="76b33-108">This chapter provides an overview of both logical and physical architecture patterns for enterprise applications.</span></span>

## <a name="architecture-patterns"></a><span data-ttu-id="76b33-109">Vzory architektury</span><span class="sxs-lookup"><span data-stu-id="76b33-109">Architecture patterns</span></span>

<span data-ttu-id="76b33-110">Moderní obchodní aplikace se řídí různými vzory architektury.</span><span class="sxs-lookup"><span data-stu-id="76b33-110">Modern business applications follow a variety of architecture patterns.</span></span> <span data-ttu-id="76b33-111">Tato část představuje přehled běžných vzorů.</span><span class="sxs-lookup"><span data-stu-id="76b33-111">This section represents a survey of common patterns.</span></span> <span data-ttu-id="76b33-112">Vzory zde uvedené nejsou nutně všechny osvědčené postupy, ale ilustrují různé přístupy.</span><span class="sxs-lookup"><span data-stu-id="76b33-112">The patterns listed here aren't necessarily all best practices, but illustrate different approaches.</span></span>

<span data-ttu-id="76b33-113">Další informace najdete v [tématu Architektura aplikací Azure průvodce](https://docs.microsoft.com/azure/architecture/guide/).</span><span class="sxs-lookup"><span data-stu-id="76b33-113">For more information, see [Azure application architecture guide](https://docs.microsoft.com/azure/architecture/guide/).</span></span>

## <a name="monoliths"></a><span data-ttu-id="76b33-114">Monolity</span><span class="sxs-lookup"><span data-stu-id="76b33-114">Monoliths</span></span>

<span data-ttu-id="76b33-115">Mnoho obchodních aplikací se řídí vzorem monolitu.</span><span class="sxs-lookup"><span data-stu-id="76b33-115">Many business applications follow a monolith pattern.</span></span> <span data-ttu-id="76b33-116">Starší aplikace jsou často implementovány jako monolity.</span><span class="sxs-lookup"><span data-stu-id="76b33-116">Legacy applications are often implemented as monoliths.</span></span> <span data-ttu-id="76b33-117">Ve vzoru monolitu jsou všechny obavy aplikace obsaženy v jednom nasazení.</span><span class="sxs-lookup"><span data-stu-id="76b33-117">In the monolith pattern, all application concerns are contained in a single deployment.</span></span> <span data-ttu-id="76b33-118">Vše od uživatelského rozhraní až po volání databáze je součástí stejného základu kódu.</span><span class="sxs-lookup"><span data-stu-id="76b33-118">Everything from user interface to database calls is included in the same codebase.</span></span>

![Monolitová architektura](./media/monolith-architecture.png)

<span data-ttu-id="76b33-120">Přístup monolitu má několik výhod.</span><span class="sxs-lookup"><span data-stu-id="76b33-120">There are several advantages to the monolith approach.</span></span> <span data-ttu-id="76b33-121">Často je snadné stáhnout jeden základ kódu a začít pracovat.</span><span class="sxs-lookup"><span data-stu-id="76b33-121">It's often easy to pull down a single code base and start working.</span></span> <span data-ttu-id="76b33-122">Doba rozjetí může být kratší a vytváření testovacích prostředí je stejně jednoduché jako poskytnutí nové kopie.</span><span class="sxs-lookup"><span data-stu-id="76b33-122">Ramp up time may be less, and creating test environments is as simple as providing a new copy.</span></span> <span data-ttu-id="76b33-123">Monolit může být navržen tak, aby zahrnoval více součástí a aplikací.</span><span class="sxs-lookup"><span data-stu-id="76b33-123">The monolith may be designed to include multiple components and applications.</span></span>

<span data-ttu-id="76b33-124">Bohužel, monolit vzor má tendenci se rozkládat ve velkém měřítku.</span><span class="sxs-lookup"><span data-stu-id="76b33-124">Unfortunately, the monolith pattern tends to break down at scale.</span></span> <span data-ttu-id="76b33-125">Mezi hlavní nevýhody monolitového přístupu patří:</span><span class="sxs-lookup"><span data-stu-id="76b33-125">Major disadvantages of the monolith approach include:</span></span>

- <span data-ttu-id="76b33-126">Obtížné pracovat paralelně ve stejném základu kódu.</span><span class="sxs-lookup"><span data-stu-id="76b33-126">Difficult to work in parallel in the same code base.</span></span>
- <span data-ttu-id="76b33-127">Každá změna, bez ohledu na to, jak triviální, vyžaduje nasazení nové verze celé aplikace.</span><span class="sxs-lookup"><span data-stu-id="76b33-127">Any change, no matter how trivial, requires deploying a new version of the entire application.</span></span>
- <span data-ttu-id="76b33-128">Refaktoring potenciálně ovlivňuje celou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="76b33-128">Refactoring potentially impacts the entire application.</span></span>
- <span data-ttu-id="76b33-129">Často jediným řešením škálování je vytvořit více kopií monolitu náročné na prostředky.</span><span class="sxs-lookup"><span data-stu-id="76b33-129">Often the only solution to scale is to create multiple, resource-intensive copies of the monolith.</span></span>
- <span data-ttu-id="76b33-130">Jak se systémy rozšiřují nebo získávají jiné systémy, integrace může být obtížná.</span><span class="sxs-lookup"><span data-stu-id="76b33-130">As systems expand or other systems are acquired, integration can be difficult.</span></span>
- <span data-ttu-id="76b33-131">Může být obtížné testovat z důvodu nutnosti konfigurovat celý monolit.</span><span class="sxs-lookup"><span data-stu-id="76b33-131">It may be difficult to test due to the need to configure the entire monolith.</span></span>
- <span data-ttu-id="76b33-132">Opakované použití kódu je náročné a často jiné aplikace skončí s vlastní kopie kódu.</span><span class="sxs-lookup"><span data-stu-id="76b33-132">Code reuse is challenging and often other apps end up having their own copies of code.</span></span>

<span data-ttu-id="76b33-133">Mnoho firem se na cloud dívá jako na příležitost k migraci monolitových aplikací a zároveň je refaktorovat na použitelnější vzory.</span><span class="sxs-lookup"><span data-stu-id="76b33-133">Many businesses look to the cloud as an opportunity to migrate monolith applications and at the same time refactor them to more usable patterns.</span></span> <span data-ttu-id="76b33-134">Je běžné prolomit jednotlivé aplikace a součásti, aby mohly být udržovány, nasazovány a škálovány samostatně.</span><span class="sxs-lookup"><span data-stu-id="76b33-134">It's common to break out the individual applications and components to allow them to be maintained, deployed, and scaled separately.</span></span>

## <a name="n-layer-applications"></a><span data-ttu-id="76b33-135">N-vrstvé aplikace</span><span class="sxs-lookup"><span data-stu-id="76b33-135">N-Layer applications</span></span>

<span data-ttu-id="76b33-136">Aplikační logika oddílu n vrstvy do konkrétních vrstev.</span><span class="sxs-lookup"><span data-stu-id="76b33-136">N-layer application partition application logic into specific layers.</span></span> <span data-ttu-id="76b33-137">Mezi nejběžnější vrstvy patří:</span><span class="sxs-lookup"><span data-stu-id="76b33-137">The most common layers include:</span></span>

- <span data-ttu-id="76b33-138">Uživatelské rozhraní</span><span class="sxs-lookup"><span data-stu-id="76b33-138">User interface</span></span>
- <span data-ttu-id="76b33-139">Obchodní logika</span><span class="sxs-lookup"><span data-stu-id="76b33-139">Business logic</span></span>
- <span data-ttu-id="76b33-140">Přístup k datům</span><span class="sxs-lookup"><span data-stu-id="76b33-140">Data access</span></span>

<span data-ttu-id="76b33-141">Ostatní vrstvy mohou zahrnovat middleware, dávkové zpracování a rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="76b33-141">Other layers may include middleware, batch processing, and API.</span></span> <span data-ttu-id="76b33-142">Je důležité si uvědomit, že vrstvy jsou logické.</span><span class="sxs-lookup"><span data-stu-id="76b33-142">It's important to note the layers are logical.</span></span> <span data-ttu-id="76b33-143">I když jsou vyvinuty izolovaně, mohou být všechny nasazeny na stejnou cílovou platformu.</span><span class="sxs-lookup"><span data-stu-id="76b33-143">Although they're developed in isolation, they may all be deployed to the same target platform.</span></span>

![Architektura N-Layer](./media/n-layer-architecture.png)

<span data-ttu-id="76b33-145">Přístup N-Layer má několik výhod, včetně:</span><span class="sxs-lookup"><span data-stu-id="76b33-145">There are several advantages to the N-Layer approach, including:</span></span>

- <span data-ttu-id="76b33-146">Refaktoring je izolován do vrstvy.</span><span class="sxs-lookup"><span data-stu-id="76b33-146">Refactoring is isolated to a layer.</span></span>
- <span data-ttu-id="76b33-147">Týmy mohou nezávisle vytvářet, testovat, nasazovat a udržovat samostatné vrstvy.</span><span class="sxs-lookup"><span data-stu-id="76b33-147">Teams can independently build, test, deploy, and maintain separate layers.</span></span>
- <span data-ttu-id="76b33-148">Vrstvy lze vyměnit, například datová vrstva může přistupovat k více databázím bez nutnosti změn vrstvy uj.</span><span class="sxs-lookup"><span data-stu-id="76b33-148">Layers can be swapped out, for example the data layer may access multiple databases without requiring changes to the UI layer.</span></span>

<span data-ttu-id="76b33-149">Bez serveru lze použít k implementaci jedné nebo více vrstev.</span><span class="sxs-lookup"><span data-stu-id="76b33-149">Serverless may be used to implement one or more layers.</span></span>

## <a name="microservices"></a><span data-ttu-id="76b33-150">Mikroslužby</span><span class="sxs-lookup"><span data-stu-id="76b33-150">Microservices</span></span>

<span data-ttu-id="76b33-151">**[Architektury mikroslužeb](https://docs.microsoft.com/azure/architecture/guide/architecture-styles/microservices)** obsahují společné charakteristiky, které zahrnují:</span><span class="sxs-lookup"><span data-stu-id="76b33-151">**[Microservices](https://docs.microsoft.com/azure/architecture/guide/architecture-styles/microservices)** architectures contain common characteristics that include:</span></span>

- <span data-ttu-id="76b33-152">Aplikace se skládají z několika malých služeb.</span><span class="sxs-lookup"><span data-stu-id="76b33-152">Applications are composed of several small services.</span></span>
- <span data-ttu-id="76b33-153">Každá služba běží ve svém vlastním procesu.</span><span class="sxs-lookup"><span data-stu-id="76b33-153">Each service runs in its own process.</span></span>
- <span data-ttu-id="76b33-154">Služby jsou zarovnány kolem obchodních domén.</span><span class="sxs-lookup"><span data-stu-id="76b33-154">Services are aligned around business domains.</span></span>
- <span data-ttu-id="76b33-155">Služby komunikovat přes zjednodušené api, obvykle pomocí protokolu HTTP jako přenos.</span><span class="sxs-lookup"><span data-stu-id="76b33-155">Services communicate over lightweight APIs, typically using HTTP as the transport.</span></span>
- <span data-ttu-id="76b33-156">Služby lze nasadit a upgradovat nezávisle.</span><span class="sxs-lookup"><span data-stu-id="76b33-156">Services can be deployed and upgraded independently.</span></span>
- <span data-ttu-id="76b33-157">Služby nejsou závislé na jednom úložišti dat.</span><span class="sxs-lookup"><span data-stu-id="76b33-157">Services aren't dependent on a single data store.</span></span>
- <span data-ttu-id="76b33-158">Systém je navržen s ohledem na selhání a aplikace může stále běžet i v případě, že některé služby selžou.</span><span class="sxs-lookup"><span data-stu-id="76b33-158">The system is designed with failure in mind, and the app may still run even when certain services fail.</span></span>

<span data-ttu-id="76b33-159">Mikroslužeb nemusí vzájemně vylučovat jiné architektury přístupy.</span><span class="sxs-lookup"><span data-stu-id="76b33-159">Microservices don't have to be mutually exclusive to other architecture approaches.</span></span> <span data-ttu-id="76b33-160">Například n-vrstvé architektury můžete použít mikroslužeb pro střední vrstvy.</span><span class="sxs-lookup"><span data-stu-id="76b33-160">For example, an N-Tier architecture may use microservices for the middle tier.</span></span> <span data-ttu-id="76b33-161">Je také možné implementovat mikroslužeb různými způsoby, od virtuálních adresářů na hostitelích služby IIS až po kontejnery.</span><span class="sxs-lookup"><span data-stu-id="76b33-161">It's also possible to implement microservices in a variety of ways, from virtual directories on IIS hosts to containers.</span></span> <span data-ttu-id="76b33-162">Vlastnosti mikroslužeb, aby byly obzvláště ideální pro implementace bez serveru.</span><span class="sxs-lookup"><span data-stu-id="76b33-162">The characteristics of microservices make them especially ideal for serverless implementations.</span></span>

![Architektura mikroslužeb](./media/microservices-architecture.png)

<span data-ttu-id="76b33-164">Mezi profesionály architektury mikroslužeb patří:</span><span class="sxs-lookup"><span data-stu-id="76b33-164">The pros of microservices architectures include:</span></span>

- <span data-ttu-id="76b33-165">Refaktoring je často izolován do jedné služby.</span><span class="sxs-lookup"><span data-stu-id="76b33-165">Refactoring is often isolated to a single service.</span></span>
- <span data-ttu-id="76b33-166">Služby lze upgradovat nezávisle na sobě.</span><span class="sxs-lookup"><span data-stu-id="76b33-166">Services can be upgraded independently of each other.</span></span>
- <span data-ttu-id="76b33-167">Odolnost a pružnost lze vyladit podle požadavků jednotlivých služeb.</span><span class="sxs-lookup"><span data-stu-id="76b33-167">Resiliency and elasticity can be tuned to the demands of individual services.</span></span>
- <span data-ttu-id="76b33-168">Vývoj může probíhat souběžně napříč různorodými týmy a platformami.</span><span class="sxs-lookup"><span data-stu-id="76b33-168">Development can happen in parallel across disparate teams and platforms.</span></span>
- <span data-ttu-id="76b33-169">Je jednodušší psát komplexní testy pro izolované služby.</span><span class="sxs-lookup"><span data-stu-id="76b33-169">It's easier to write comprehensive tests for isolated services.</span></span>

<span data-ttu-id="76b33-170">Mikroslužby přicházejí s vlastními výzvami, včetně:</span><span class="sxs-lookup"><span data-stu-id="76b33-170">Microservices come with their own challenges, including:</span></span>

- <span data-ttu-id="76b33-171">Určení, jaké služby jsou k dispozici a jak je nazývat.</span><span class="sxs-lookup"><span data-stu-id="76b33-171">Determining what services are available and how to call them.</span></span>
- <span data-ttu-id="76b33-172">Správa životního cyklu služeb.</span><span class="sxs-lookup"><span data-stu-id="76b33-172">Managing the lifecycle of services.</span></span>
- <span data-ttu-id="76b33-173">Pochopení toho, jak služby zapadají do celkové aplikace.</span><span class="sxs-lookup"><span data-stu-id="76b33-173">Understanding how services fit together in the overall application.</span></span>
- <span data-ttu-id="76b33-174">Úplné testování systému volání uskutečněných napříč různorodými službami.</span><span class="sxs-lookup"><span data-stu-id="76b33-174">Full system testing of calls made across disparate services.</span></span>

<span data-ttu-id="76b33-175">Nakonec existují řešení pro řešení všech těchto problémů, včetně využití výhod bez serveru, které jsou popsány později.</span><span class="sxs-lookup"><span data-stu-id="76b33-175">Ultimately there are solutions to address all of these challenges, including tapping into the benefits of serverless that are discussed later.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="76b33-176">[Předchozí](index.md)
>[další](architecture-deployment-approaches.md)</span><span class="sxs-lookup"><span data-stu-id="76b33-176">[Previous](index.md)
[Next](architecture-deployment-approaches.md)</span></span>
