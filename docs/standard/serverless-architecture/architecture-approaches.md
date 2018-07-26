---
title: Architektura přístupy – aplikace bez serveru
description: Úvod do architektury přístupů pro podnikové cloudové aplikace, z N-vrstvou architekturu v Azure k bez serveru.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: b080e029fb1214ebf4d2717902c3b6d4af06d254
ms.sourcegitcommit: 4c158beee818c408d45a9609bfc06f209a523e22
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/03/2018
ms.locfileid: "37404899"
---
# <a name="architecture-approaches"></a><span data-ttu-id="f1ffc-103">Přístupy k architektuře</span><span class="sxs-lookup"><span data-stu-id="f1ffc-103">Architecture approaches</span></span>

<span data-ttu-id="f1ffc-104">Principy existujících přístupů k navrhování firemních aplikací pomáhá vysvětlit roli hrají bez serveru.</span><span class="sxs-lookup"><span data-stu-id="f1ffc-104">Understanding existing approaches to architecting enterprise apps helps clarify the role played by serverless.</span></span> <span data-ttu-id="f1ffc-105">Existuje mnoho přístupů a vzory, které se za desítky let vývoje softwaru, a všechny mají své vlastní výhody a nevýhody.</span><span class="sxs-lookup"><span data-stu-id="f1ffc-105">There are many approaches and patterns that evolved over decades of software development, and all have their own pros and cons.</span></span> <span data-ttu-id="f1ffc-106">V mnoha případech ultimate řešení nemusí zahrnovat rozhodování o jeden přístup, ale může integrovat několik přístupů.</span><span class="sxs-lookup"><span data-stu-id="f1ffc-106">In many cases, the ultimate solution may not involve deciding on a single approach but may integrate several approaches.</span></span> <span data-ttu-id="f1ffc-107">Scénáře migrace často zahrnuje posun od jednoho architektura přístupu do jiné prostřednictvím s hybridním přístupem.</span><span class="sxs-lookup"><span data-stu-id="f1ffc-107">Migration scenarios often involve shifting from one architecture approach to another through a hybrid approach.</span></span>

<span data-ttu-id="f1ffc-108">Tato kapitola obsahuje přehled oba vzorky logické a fyzické architektura pro podnikové aplikace.</span><span class="sxs-lookup"><span data-stu-id="f1ffc-108">This chapter provides an overview of both logical and physical architecture patterns for enterprise applications.</span></span>

## <a name="architecture-patterns"></a><span data-ttu-id="f1ffc-109">Vzory architektury</span><span class="sxs-lookup"><span data-stu-id="f1ffc-109">Architecture patterns</span></span>

<span data-ttu-id="f1ffc-110">Moderní firemní aplikace podle různých vzory architektury.</span><span class="sxs-lookup"><span data-stu-id="f1ffc-110">Modern business applications follow a variety of architecture patterns.</span></span> <span data-ttu-id="f1ffc-111">Tato část představuje přehled běžných vzorů.</span><span class="sxs-lookup"><span data-stu-id="f1ffc-111">This section represents a survey of common patterns.</span></span> <span data-ttu-id="f1ffc-112">Tyto vzory se dají tady nejsou nutně všechny osvědčené postupy, ale ukazují různé přístupy.</span><span class="sxs-lookup"><span data-stu-id="f1ffc-112">The patterns listed here aren't necessarily all best practices, but illustrate different approaches.</span></span>

<span data-ttu-id="f1ffc-113">Další informace najdete v tématu [Průvodce architekturou aplikací Azure](https://docs.microsoft.com/azure/architecture/guide/).</span><span class="sxs-lookup"><span data-stu-id="f1ffc-113">For more information, see [Azure application architecture guide](https://docs.microsoft.com/azure/architecture/guide/).</span></span>

## <a name="monoliths"></a><span data-ttu-id="f1ffc-114">Monolitické</span><span class="sxs-lookup"><span data-stu-id="f1ffc-114">Monoliths</span></span>

<span data-ttu-id="f1ffc-115">Mnoho obchodních aplikací se řídí vzorem monolitu.</span><span class="sxs-lookup"><span data-stu-id="f1ffc-115">Many business applications follow a monolith pattern.</span></span> <span data-ttu-id="f1ffc-116">Starší aplikace, které jsou často implementovány jako monolitické.</span><span class="sxs-lookup"><span data-stu-id="f1ffc-116">Legacy applications are often implemented as monoliths.</span></span> <span data-ttu-id="f1ffc-117">Ve vzoru monolitu všechny aspekty aplikace jsou obsaženy v jednom nasazení.</span><span class="sxs-lookup"><span data-stu-id="f1ffc-117">In the monolith pattern, all application concerns are contained in a single deployment.</span></span> <span data-ttu-id="f1ffc-118">Všechno, co z uživatelského rozhraní pro volání databáze je součástí stejného základu kódu.</span><span class="sxs-lookup"><span data-stu-id="f1ffc-118">Everything from user interface to database calls is included in the same codebase.</span></span>

![Architektura monolitu](./media/monolith-architecture.png)

<span data-ttu-id="f1ffc-120">Existuje několik výhod přístupu monolitu.</span><span class="sxs-lookup"><span data-stu-id="f1ffc-120">There are several advantages to the monolith approach.</span></span> <span data-ttu-id="f1ffc-121">Často je snadné stáhne z jediného základu kódu a začít pracovat.</span><span class="sxs-lookup"><span data-stu-id="f1ffc-121">It's often easy to pull down a single code base and start working.</span></span> <span data-ttu-id="f1ffc-122">Doba přípravy může být menší, a vytvoření testovací prostředí je stejně jednoduché jako novou kopii.</span><span class="sxs-lookup"><span data-stu-id="f1ffc-122">Ramp up time may be less, and creating test environments is as simple as providing a new copy.</span></span> <span data-ttu-id="f1ffc-123">Monolitu může být navržena pro zahrnutí více komponent a aplikací.</span><span class="sxs-lookup"><span data-stu-id="f1ffc-123">The monolith may be designed to include multiple components and applications.</span></span>

<span data-ttu-id="f1ffc-124">Bohužel se obvykle vzor monolitu rozdělit ve velkém měřítku.</span><span class="sxs-lookup"><span data-stu-id="f1ffc-124">Unfortunately, the monolith pattern tends to break down at scale.</span></span> <span data-ttu-id="f1ffc-125">Hlavní nevýhody monolitu přístupu patří:</span><span class="sxs-lookup"><span data-stu-id="f1ffc-125">Major disadvantages of the monolith approach include:</span></span>

* <span data-ttu-id="f1ffc-126">Obtížně pracovat souběžně ve stejném základu kódu.</span><span class="sxs-lookup"><span data-stu-id="f1ffc-126">Difficult to work in parallel in the same code base.</span></span>
* <span data-ttu-id="f1ffc-127">Všechny změny, bez ohledu na to, jak jednoduché, vyžaduje nasazení nové verze celé aplikace.</span><span class="sxs-lookup"><span data-stu-id="f1ffc-127">Any change, no matter how trivial, requires deploying a new version of the entire application.</span></span>
* <span data-ttu-id="f1ffc-128">Refaktoring potenciálně ovlivňuje celou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="f1ffc-128">Refactoring potentially impacts the entire application.</span></span>
* <span data-ttu-id="f1ffc-129">Často pouze řešení škálování, je vytvořit víc kopií náročná monolitu.</span><span class="sxs-lookup"><span data-stu-id="f1ffc-129">Often the only solution to scale is to create multiple, resource-intensive copies of the monolith.</span></span>
* <span data-ttu-id="f1ffc-130">Jak rozbalit systémy nebo jinými systémy pořízené, integrace může být obtížné.</span><span class="sxs-lookup"><span data-stu-id="f1ffc-130">As systems expand or other systems are acquired, integration can be difficult.</span></span>
* <span data-ttu-id="f1ffc-131">Může být obtížné testu kvůli nutnosti konfigurace celý monolitu.</span><span class="sxs-lookup"><span data-stu-id="f1ffc-131">It may be difficult to test due to the need to configure the entire monolith.</span></span>
* <span data-ttu-id="f1ffc-132">Opakované využívání kódu je náročné a často další aplikace skončit s vlastní kopie kódu.</span><span class="sxs-lookup"><span data-stu-id="f1ffc-132">Code reuse is challenging and often other apps end up having their own copies of code.</span></span>

<span data-ttu-id="f1ffc-133">Řada podniků pohlížet jako příležitost k migraci monolitu aplikací a současně refaktorace na další použitelné modely do cloudu.</span><span class="sxs-lookup"><span data-stu-id="f1ffc-133">Many businesses look to the cloud as an opportunity to migrate monolith applications and at the same time refactor them to more usable patterns.</span></span> <span data-ttu-id="f1ffc-134">Je běžné rozdělit jednotlivých aplikací a součástí, aby se mohly být udržovány, nasadit a škálovat samostatně.</span><span class="sxs-lookup"><span data-stu-id="f1ffc-134">It's common to break out the individual applications and components to allow them to be maintained, deployed, and scaled separately.</span></span>

## <a name="n-layer-applications"></a><span data-ttu-id="f1ffc-135">Aplikací vrstvy N</span><span class="sxs-lookup"><span data-stu-id="f1ffc-135">N-Layer applications</span></span>

<span data-ttu-id="f1ffc-136">Aplikací vrstvy N oddílu aplikace logiky do konkrétní vrstvy.</span><span class="sxs-lookup"><span data-stu-id="f1ffc-136">N-layer application partition application logic into specific layers.</span></span> <span data-ttu-id="f1ffc-137">Nejběžnější vrstvy patří:</span><span class="sxs-lookup"><span data-stu-id="f1ffc-137">The most common layers include:</span></span>

* <span data-ttu-id="f1ffc-138">Uživatelské rozhraní</span><span class="sxs-lookup"><span data-stu-id="f1ffc-138">User interface</span></span>
* <span data-ttu-id="f1ffc-139">Obchodní logika</span><span class="sxs-lookup"><span data-stu-id="f1ffc-139">Business logic</span></span>
* <span data-ttu-id="f1ffc-140">Přístup k datům</span><span class="sxs-lookup"><span data-stu-id="f1ffc-140">Data access</span></span>

<span data-ttu-id="f1ffc-141">Middleware, dávkové zpracování a rozhraní API může obsahovat další vrstvy.</span><span class="sxs-lookup"><span data-stu-id="f1ffc-141">Other layers may include middleware, batch processing, and API.</span></span> <span data-ttu-id="f1ffc-142">Je důležité si uvědomit, že jsou logické vrstvy.</span><span class="sxs-lookup"><span data-stu-id="f1ffc-142">It's important to note the layers are logical.</span></span> <span data-ttu-id="f1ffc-143">I když jsou už vyvinuté v izolaci, jsou všechny jde nasadit do stejné cílové platformy.</span><span class="sxs-lookup"><span data-stu-id="f1ffc-143">Although they're developed in isolation, they may all be deployed to the same target platform.</span></span>

![N-vrstev architektury](./media/n-layer-architecture.png)

<span data-ttu-id="f1ffc-145">Má několik výhod pro N-vrstvu přístupu, včetně:</span><span class="sxs-lookup"><span data-stu-id="f1ffc-145">There are several advantages to the N-Layer approach, including:</span></span>

* <span data-ttu-id="f1ffc-146">Refaktoring je izolovaná na vrstvu.</span><span class="sxs-lookup"><span data-stu-id="f1ffc-146">Refactoring is isolated to a layer.</span></span>
* <span data-ttu-id="f1ffc-147">Týmy mohou nezávisle na sobě vytvořit, otestovat, nasadit a udržovat samostatné vrstvy.</span><span class="sxs-lookup"><span data-stu-id="f1ffc-147">Teams can independently build, test, deploy, and maintain separate layers.</span></span>
* <span data-ttu-id="f1ffc-148">Vrstvy můžete být automaticky, například datová vrstva může přistupovat k více databází bez nutnosti provádět změny vrstvě uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="f1ffc-148">Layers can be swapped out, for example the data layer may access multiple databases without requiring changes to the UI layer.</span></span>

<span data-ttu-id="f1ffc-149">Bez serveru slouží k implementaci jednu nebo více vrstev.</span><span class="sxs-lookup"><span data-stu-id="f1ffc-149">Serverless may be used to implement one or more layers.</span></span>

## <a name="microservices"></a><span data-ttu-id="f1ffc-150">Mikroslužby</span><span class="sxs-lookup"><span data-stu-id="f1ffc-150">Microservices</span></span>

<span data-ttu-id="f1ffc-151">**[Mikroslužby](https://docs.microsoft.com/azure/architecture/guide/architecture-styles/microservices)**  architektury obsahovat běžné vlastnosti, které zahrnují:</span><span class="sxs-lookup"><span data-stu-id="f1ffc-151">**[Microservices](https://docs.microsoft.com/azure/architecture/guide/architecture-styles/microservices)** architectures contain common characteristics that include:</span></span>

* <span data-ttu-id="f1ffc-152">Aplikace se skládají z několika malých služeb.</span><span class="sxs-lookup"><span data-stu-id="f1ffc-152">Applications are composed of several small services.</span></span>
* <span data-ttu-id="f1ffc-153">Každá služba se spouští ve svém vlastním procesu.</span><span class="sxs-lookup"><span data-stu-id="f1ffc-153">Each service runs in its own process.</span></span>
* <span data-ttu-id="f1ffc-154">Služby jsou zarovnány kolem obchodní domény.</span><span class="sxs-lookup"><span data-stu-id="f1ffc-154">Services are aligned around business domains.</span></span>
* <span data-ttu-id="f1ffc-155">Služby komunikují přes jednoduché rozhraní API, obvykle přenos pomocí protokolu HTTP.</span><span class="sxs-lookup"><span data-stu-id="f1ffc-155">Services communicate over lightweight APIs, typically using HTTP as the transport.</span></span>
* <span data-ttu-id="f1ffc-156">Služby je možné nasadit a upgraduje samostatně.</span><span class="sxs-lookup"><span data-stu-id="f1ffc-156">Services can be deployed and upgraded independently.</span></span>
* <span data-ttu-id="f1ffc-157">Služby nejsou závislé na jednom datovém úložišti.</span><span class="sxs-lookup"><span data-stu-id="f1ffc-157">Services aren't dependent on a single data store.</span></span>
* <span data-ttu-id="f1ffc-158">Systém je navržená s chybou v úvahu a aplikace může běžet i v případě selhání některých služeb.</span><span class="sxs-lookup"><span data-stu-id="f1ffc-158">The system is designed with failure in mind, and the app may still run even when certain services fail.</span></span>

<span data-ttu-id="f1ffc-159">Mikroslužby nemusí být vzájemné další přístupy k architektuře.</span><span class="sxs-lookup"><span data-stu-id="f1ffc-159">Microservices don't have to be mutual to other architecture approaches.</span></span> <span data-ttu-id="f1ffc-160">Například může použít N-vrstvou architekturu mikroslužeb pro střední vrstvy.</span><span class="sxs-lookup"><span data-stu-id="f1ffc-160">For example, an N-Tier architecture may use microservices for the middle tier.</span></span> <span data-ttu-id="f1ffc-161">Také je možné implementovat mikroslužby v celou řadu způsobů, z adresáře v hostitelích služby IIS do kontejnerů.</span><span class="sxs-lookup"><span data-stu-id="f1ffc-161">It's also possible to implement microservices in a variety of ways, from virtual directories on IIS hosts to containers.</span></span> <span data-ttu-id="f1ffc-162">Zkontrolujte charakteristiky mikroslužeb je zvláště ideální pro implementace bez serveru.</span><span class="sxs-lookup"><span data-stu-id="f1ffc-162">The characteristics of microservices make them especially ideal for serverless implementations.</span></span>

![Architektura Mikroslužeb](./media/microservices-architecture.png)

<span data-ttu-id="f1ffc-164">Profesionálové mikroslužeb patří:</span><span class="sxs-lookup"><span data-stu-id="f1ffc-164">The pros of microservices architectures include:</span></span>

* <span data-ttu-id="f1ffc-165">Refaktoring často je izolovaná na jednu službu.</span><span class="sxs-lookup"><span data-stu-id="f1ffc-165">Refactoring is often isolated to a single service.</span></span>
* <span data-ttu-id="f1ffc-166">Služby je možné upgradovat nezávisle na sobě.</span><span class="sxs-lookup"><span data-stu-id="f1ffc-166">Services can be upgraded independently of each other.</span></span>
* <span data-ttu-id="f1ffc-167">Odolnost proti chybám a elasticitu můžete ladit pro požadavky jednotlivých služeb.</span><span class="sxs-lookup"><span data-stu-id="f1ffc-167">Resiliency and elasticity can be tuned to the demands of individual services.</span></span>
* <span data-ttu-id="f1ffc-168">Vývoj, může dojít paralelně napříč různými týmy a platformami.</span><span class="sxs-lookup"><span data-stu-id="f1ffc-168">Development can happen in parallel across disparate teams and platforms.</span></span>
* <span data-ttu-id="f1ffc-169">Je snazší psát komplexní testy pro izolované služby.</span><span class="sxs-lookup"><span data-stu-id="f1ffc-169">It's easier to write comprehensive tests for isolated services.</span></span>

<span data-ttu-id="f1ffc-170">Mikroslužby jsou součástí vlastní výzvy, včetně:</span><span class="sxs-lookup"><span data-stu-id="f1ffc-170">Microservices come with their own challenges, including:</span></span>

* <span data-ttu-id="f1ffc-171">Určení, jaké služby jsou k dispozici a jak je volat.</span><span class="sxs-lookup"><span data-stu-id="f1ffc-171">Determining what services are available and how to call them.</span></span>
* <span data-ttu-id="f1ffc-172">Správa životního cyklu služeb.</span><span class="sxs-lookup"><span data-stu-id="f1ffc-172">Managing the lifecycle of services.</span></span>
* <span data-ttu-id="f1ffc-173">Ke zjištění, jak služby navzájem propojené, v celkové aplikace.</span><span class="sxs-lookup"><span data-stu-id="f1ffc-173">Understanding how services fit together in the overall application.</span></span>
* <span data-ttu-id="f1ffc-174">Úplnou testování volání napříč různými službami.</span><span class="sxs-lookup"><span data-stu-id="f1ffc-174">Full system testing of calls made across disparate services.</span></span>

<span data-ttu-id="f1ffc-175">Nakonec jsou všechny tyto výzvy, včetně proniknutí do výhod prostředí bez serveru, které jsou uvedeny dále vícebodových řešení.</span><span class="sxs-lookup"><span data-stu-id="f1ffc-175">Ultimately there are solutions to address all of these challenges, including tapping into the benefits of serverless that are discussed later.</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="f1ffc-176">[Předchozí](index.md)
[další](architecture-deployment-approaches.md)</span><span class="sxs-lookup"><span data-stu-id="f1ffc-176">[Previous](index.md)
[Next](architecture-deployment-approaches.md)</span></span>
