---
title: Přístupy k architektuře – aplikace bez serveru
description: Úvod do architektury architektury pro vytváření cloudových podnikových aplikací, od N-vrstvých architektur až po bez serveru.
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 74de96bef48f16ced4adf82855a740aa0afcdf1d
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/08/2019
ms.locfileid: "72522894"
---
# <a name="architecture-approaches"></a><span data-ttu-id="fbce6-103">Přístupy k architektuře</span><span class="sxs-lookup"><span data-stu-id="fbce6-103">Architecture approaches</span></span>

<span data-ttu-id="fbce6-104">Porozumění existujícím přístupům k architektům podnikových aplikací je vyjasnění role, kterou prohrála bez serveru.</span><span class="sxs-lookup"><span data-stu-id="fbce6-104">Understanding existing approaches to architecting enterprise apps helps clarify the role played by serverless.</span></span> <span data-ttu-id="fbce6-105">Existuje mnoho přístupů a vzorů, které se vyvinuly během desetiletí vývoje softwaru, a všechny mají své vlastní specialisty a nevýhody.</span><span class="sxs-lookup"><span data-stu-id="fbce6-105">There are many approaches and patterns that evolved over decades of software development, and all have their own pros and cons.</span></span> <span data-ttu-id="fbce6-106">V mnoha případech se může stát, že konečné řešení nezahrnuje rozhodování o jednom přístupu, ale může integrovat několik přístupů.</span><span class="sxs-lookup"><span data-stu-id="fbce6-106">In many cases, the ultimate solution may not involve deciding on a single approach but may integrate several approaches.</span></span> <span data-ttu-id="fbce6-107">Scénáře migrace často zahrnují přesun z jednoho přístupu architektury do druhého prostřednictvím hybridního přístupu.</span><span class="sxs-lookup"><span data-stu-id="fbce6-107">Migration scenarios often involve shifting from one architecture approach to another through a hybrid approach.</span></span>

<span data-ttu-id="fbce6-108">V této části najdete přehled logických i fyzických struktur pro podnikové aplikace.</span><span class="sxs-lookup"><span data-stu-id="fbce6-108">This chapter provides an overview of both logical and physical architecture patterns for enterprise applications.</span></span>

## <a name="architecture-patterns"></a><span data-ttu-id="fbce6-109">Vzory architektury</span><span class="sxs-lookup"><span data-stu-id="fbce6-109">Architecture patterns</span></span>

<span data-ttu-id="fbce6-110">Moderní obchodní aplikace se řídí různými modely architektury.</span><span class="sxs-lookup"><span data-stu-id="fbce6-110">Modern business applications follow a variety of architecture patterns.</span></span> <span data-ttu-id="fbce6-111">Tato část představuje průzkum běžných vzorů.</span><span class="sxs-lookup"><span data-stu-id="fbce6-111">This section represents a survey of common patterns.</span></span> <span data-ttu-id="fbce6-112">Zde uvedené příklady nejsou nutně všechny osvědčené postupy, ale ilustrují různé přístupy.</span><span class="sxs-lookup"><span data-stu-id="fbce6-112">The patterns listed here aren't necessarily all best practices, but illustrate different approaches.</span></span>

<span data-ttu-id="fbce6-113">Další informace najdete v tématu [Průvodce architekturou aplikací Azure](https://docs.microsoft.com/azure/architecture/guide/).</span><span class="sxs-lookup"><span data-stu-id="fbce6-113">For more information, see [Azure application architecture guide](https://docs.microsoft.com/azure/architecture/guide/).</span></span>

## <a name="monoliths"></a><span data-ttu-id="fbce6-114">Monolitů</span><span class="sxs-lookup"><span data-stu-id="fbce6-114">Monoliths</span></span>

<span data-ttu-id="fbce6-115">Řada obchodních aplikací dodržuje vzor monolitu.</span><span class="sxs-lookup"><span data-stu-id="fbce6-115">Many business applications follow a monolith pattern.</span></span> <span data-ttu-id="fbce6-116">Starší verze aplikací jsou často implementovány jako monolitů.</span><span class="sxs-lookup"><span data-stu-id="fbce6-116">Legacy applications are often implemented as monoliths.</span></span> <span data-ttu-id="fbce6-117">Ve vzorci monolitu jsou všechny aspekty týkající se aplikace obsaženy v jednom nasazení.</span><span class="sxs-lookup"><span data-stu-id="fbce6-117">In the monolith pattern, all application concerns are contained in a single deployment.</span></span> <span data-ttu-id="fbce6-118">Vše od uživatelského rozhraní po volání databáze je zahrnuto ve stejném základu kódu.</span><span class="sxs-lookup"><span data-stu-id="fbce6-118">Everything from user interface to database calls is included in the same codebase.</span></span>

![Architektura monolitu](./media/monolith-architecture.png)

<span data-ttu-id="fbce6-120">Přístup k monolitu má několik výhod.</span><span class="sxs-lookup"><span data-stu-id="fbce6-120">There are several advantages to the monolith approach.</span></span> <span data-ttu-id="fbce6-121">Je často snadné stáhnout jeden základ kódu a začít pracovat.</span><span class="sxs-lookup"><span data-stu-id="fbce6-121">It's often easy to pull down a single code base and start working.</span></span> <span data-ttu-id="fbce6-122">Doba provozu může být menší a vytváření testovacích prostředí je stejně snadné jako poskytování nové kopie.</span><span class="sxs-lookup"><span data-stu-id="fbce6-122">Ramp up time may be less, and creating test environments is as simple as providing a new copy.</span></span> <span data-ttu-id="fbce6-123">Monolitu může být navržený tak, aby zahrnoval více komponent a aplikací.</span><span class="sxs-lookup"><span data-stu-id="fbce6-123">The monolith may be designed to include multiple components and applications.</span></span>

<span data-ttu-id="fbce6-124">Monolitu vzor bohužel má tendenci rozlomit se škálováním.</span><span class="sxs-lookup"><span data-stu-id="fbce6-124">Unfortunately, the monolith pattern tends to break down at scale.</span></span> <span data-ttu-id="fbce6-125">Mezi hlavní nevýhody přístupu monolitu patří:</span><span class="sxs-lookup"><span data-stu-id="fbce6-125">Major disadvantages of the monolith approach include:</span></span>

- <span data-ttu-id="fbce6-126">Obtížně fungovat paralelně ve stejném základu kódu.</span><span class="sxs-lookup"><span data-stu-id="fbce6-126">Difficult to work in parallel in the same code base.</span></span>
- <span data-ttu-id="fbce6-127">Jakékoli změny bez ohledu na to, jak triviální vyžaduje nasazení nové verze celé aplikace.</span><span class="sxs-lookup"><span data-stu-id="fbce6-127">Any change, no matter how trivial, requires deploying a new version of the entire application.</span></span>
- <span data-ttu-id="fbce6-128">Refaktoring může mít vliv na celou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="fbce6-128">Refactoring potentially impacts the entire application.</span></span>
- <span data-ttu-id="fbce6-129">Jediným řešením pro horizontální navýšení kapacity je často vytvoření více kopií monolitu náročných na prostředky.</span><span class="sxs-lookup"><span data-stu-id="fbce6-129">Often the only solution to scale is to create multiple, resource-intensive copies of the monolith.</span></span>
- <span data-ttu-id="fbce6-130">V případě, že se systémy rozbalí nebo ostatní systémy získávají, může být integrace obtížné.</span><span class="sxs-lookup"><span data-stu-id="fbce6-130">As systems expand or other systems are acquired, integration can be difficult.</span></span>
- <span data-ttu-id="fbce6-131">Testování může být obtížné kvůli nutnosti nakonfigurovat celou monolitu.</span><span class="sxs-lookup"><span data-stu-id="fbce6-131">It may be difficult to test due to the need to configure the entire monolith.</span></span>
- <span data-ttu-id="fbce6-132">Opětovné použití kódu je náročné a často jiné aplikace mají vlastní kopie kódu.</span><span class="sxs-lookup"><span data-stu-id="fbce6-132">Code reuse is challenging and often other apps end up having their own copies of code.</span></span>

<span data-ttu-id="fbce6-133">Mnohé firmy vypadají v cloudu jako příležitost k migraci aplikací monolitu a ve stejnou dobu refaktorování na více použitelných vzorů.</span><span class="sxs-lookup"><span data-stu-id="fbce6-133">Many businesses look to the cloud as an opportunity to migrate monolith applications and at the same time refactor them to more usable patterns.</span></span> <span data-ttu-id="fbce6-134">Je běžné rozdělit jednotlivé aplikace a komponenty, aby je bylo možné udržovat, nasadit a škálovat samostatně.</span><span class="sxs-lookup"><span data-stu-id="fbce6-134">It's common to break out the individual applications and components to allow them to be maintained, deployed, and scaled separately.</span></span>

## <a name="n-layer-applications"></a><span data-ttu-id="fbce6-135">N-vrstvé aplikace</span><span class="sxs-lookup"><span data-stu-id="fbce6-135">N-Layer applications</span></span>

<span data-ttu-id="fbce6-136">N-vrstvá aplikace oddíl aplikační logiky do specifických vrstev.</span><span class="sxs-lookup"><span data-stu-id="fbce6-136">N-layer application partition application logic into specific layers.</span></span> <span data-ttu-id="fbce6-137">Mezi nejběžnější vrstvy patří:</span><span class="sxs-lookup"><span data-stu-id="fbce6-137">The most common layers include:</span></span>

- <span data-ttu-id="fbce6-138">Uživatelské rozhraní</span><span class="sxs-lookup"><span data-stu-id="fbce6-138">User interface</span></span>
- <span data-ttu-id="fbce6-139">Obchodní logika</span><span class="sxs-lookup"><span data-stu-id="fbce6-139">Business logic</span></span>
- <span data-ttu-id="fbce6-140">Přístup k datům</span><span class="sxs-lookup"><span data-stu-id="fbce6-140">Data access</span></span>

<span data-ttu-id="fbce6-141">Další vrstvy můžou zahrnovat middleware, dávkové zpracování a rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="fbce6-141">Other layers may include middleware, batch processing, and API.</span></span> <span data-ttu-id="fbce6-142">Je důležité si uvědomit, že vrstvy jsou logické.</span><span class="sxs-lookup"><span data-stu-id="fbce6-142">It's important to note the layers are logical.</span></span> <span data-ttu-id="fbce6-143">I když se vyvíjí v izolaci, můžou se všechny nasadit na stejnou cílovou platformu.</span><span class="sxs-lookup"><span data-stu-id="fbce6-143">Although they're developed in isolation, they may all be deployed to the same target platform.</span></span>

![N-vrstvá architektura](./media/n-layer-architecture.png)

<span data-ttu-id="fbce6-145">K dispozici je několik výhod pro N-vrstvý přístup, včetně:</span><span class="sxs-lookup"><span data-stu-id="fbce6-145">There are several advantages to the N-Layer approach, including:</span></span>

- <span data-ttu-id="fbce6-146">Refaktoring je izolovaný s vrstvou.</span><span class="sxs-lookup"><span data-stu-id="fbce6-146">Refactoring is isolated to a layer.</span></span>
- <span data-ttu-id="fbce6-147">Týmy můžou nezávisle sestavovat, testovat, nasazovat a udržovat samostatné vrstvy.</span><span class="sxs-lookup"><span data-stu-id="fbce6-147">Teams can independently build, test, deploy, and maintain separate layers.</span></span>
- <span data-ttu-id="fbce6-148">Vrstvy lze odkládací, například datová vrstva může přistupovat k několika databázím, aniž by vyžadovaly změny ve vrstvě uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="fbce6-148">Layers can be swapped out, for example the data layer may access multiple databases without requiring changes to the UI layer.</span></span>

<span data-ttu-id="fbce6-149">Bez serveru se dá použít k implementaci jedné nebo víc vrstev.</span><span class="sxs-lookup"><span data-stu-id="fbce6-149">Serverless may be used to implement one or more layers.</span></span>

## <a name="microservices"></a><span data-ttu-id="fbce6-150">Mikroslužeb</span><span class="sxs-lookup"><span data-stu-id="fbce6-150">Microservices</span></span>

<span data-ttu-id="fbce6-151">Architektury **[mikroslužeb](https://docs.microsoft.com/azure/architecture/guide/architecture-styles/microservices)** obsahují běžné charakteristiky, které zahrnují:</span><span class="sxs-lookup"><span data-stu-id="fbce6-151">**[Microservices](https://docs.microsoft.com/azure/architecture/guide/architecture-styles/microservices)** architectures contain common characteristics that include:</span></span>

- <span data-ttu-id="fbce6-152">Aplikace se skládají z několika malých služeb.</span><span class="sxs-lookup"><span data-stu-id="fbce6-152">Applications are composed of several small services.</span></span>
- <span data-ttu-id="fbce6-153">Každá služba se spouští ve vlastním procesu.</span><span class="sxs-lookup"><span data-stu-id="fbce6-153">Each service runs in its own process.</span></span>
- <span data-ttu-id="fbce6-154">Služby jsou zarovnány k obchodním doménám.</span><span class="sxs-lookup"><span data-stu-id="fbce6-154">Services are aligned around business domains.</span></span>
- <span data-ttu-id="fbce6-155">Služby komunikují přes odlehčená rozhraní API, obvykle jako přenos pomocí protokolu HTTP.</span><span class="sxs-lookup"><span data-stu-id="fbce6-155">Services communicate over lightweight APIs, typically using HTTP as the transport.</span></span>
- <span data-ttu-id="fbce6-156">Služby je možné nasadit a upgradovat nezávisle.</span><span class="sxs-lookup"><span data-stu-id="fbce6-156">Services can be deployed and upgraded independently.</span></span>
- <span data-ttu-id="fbce6-157">Služby nejsou závislé na jednom úložišti dat.</span><span class="sxs-lookup"><span data-stu-id="fbce6-157">Services aren't dependent on a single data store.</span></span>
- <span data-ttu-id="fbce6-158">Systém je navržený s ohledem na selhání a aplikace může běžet i v případě, že některé služby selžou.</span><span class="sxs-lookup"><span data-stu-id="fbce6-158">The system is designed with failure in mind, and the app may still run even when certain services fail.</span></span>

<span data-ttu-id="fbce6-159">Mikroslužby nemusí být vzájemně exkluzivní pro jiné přístupy k architektuře.</span><span class="sxs-lookup"><span data-stu-id="fbce6-159">Microservices don't have to be mutually exclusive to other architecture approaches.</span></span> <span data-ttu-id="fbce6-160">N-vrstvá architektura může například používat mikroslužby pro střední vrstvu.</span><span class="sxs-lookup"><span data-stu-id="fbce6-160">For example, an N-Tier architecture may use microservices for the middle tier.</span></span> <span data-ttu-id="fbce6-161">Je také možné implementovat mikroslužby mnoha různými způsoby, od virtuálních adresářů hostitelů služby IIS až po kontejnery.</span><span class="sxs-lookup"><span data-stu-id="fbce6-161">It's also possible to implement microservices in a variety of ways, from virtual directories on IIS hosts to containers.</span></span> <span data-ttu-id="fbce6-162">Charakteristiky mikroslužeb je zvláště ideální pro implementace bez serveru.</span><span class="sxs-lookup"><span data-stu-id="fbce6-162">The characteristics of microservices make them especially ideal for serverless implementations.</span></span>

![Architektura mikroslužeb](./media/microservices-architecture.png)

<span data-ttu-id="fbce6-164">Mezi profesionály architektury mikroslužeb patří:</span><span class="sxs-lookup"><span data-stu-id="fbce6-164">The pros of microservices architectures include:</span></span>

- <span data-ttu-id="fbce6-165">Refaktoring se často izoluje u jediné služby.</span><span class="sxs-lookup"><span data-stu-id="fbce6-165">Refactoring is often isolated to a single service.</span></span>
- <span data-ttu-id="fbce6-166">Služby je možné upgradovat nezávisle na sobě.</span><span class="sxs-lookup"><span data-stu-id="fbce6-166">Services can be upgraded independently of each other.</span></span>
- <span data-ttu-id="fbce6-167">Odolnost a pružnost je možné vyladit podle požadavků jednotlivých služeb.</span><span class="sxs-lookup"><span data-stu-id="fbce6-167">Resiliency and elasticity can be tuned to the demands of individual services.</span></span>
- <span data-ttu-id="fbce6-168">Vývoj může nastat paralelně napříč různými týmy a platformami.</span><span class="sxs-lookup"><span data-stu-id="fbce6-168">Development can happen in parallel across disparate teams and platforms.</span></span>
- <span data-ttu-id="fbce6-169">Napsání komplexních testů pro izolované služby je snazší.</span><span class="sxs-lookup"><span data-stu-id="fbce6-169">It's easier to write comprehensive tests for isolated services.</span></span>

<span data-ttu-id="fbce6-170">Mikroslužby se dodávají s vlastními výzvami, včetně:</span><span class="sxs-lookup"><span data-stu-id="fbce6-170">Microservices come with their own challenges, including:</span></span>

- <span data-ttu-id="fbce6-171">Určete, jaké služby jsou k dispozici a jak je volat.</span><span class="sxs-lookup"><span data-stu-id="fbce6-171">Determining what services are available and how to call them.</span></span>
- <span data-ttu-id="fbce6-172">Správa životního cyklu služeb.</span><span class="sxs-lookup"><span data-stu-id="fbce6-172">Managing the lifecycle of services.</span></span>
- <span data-ttu-id="fbce6-173">Seznamte se s tím, jak se služby vzájemně vejdou do celkové aplikace.</span><span class="sxs-lookup"><span data-stu-id="fbce6-173">Understanding how services fit together in the overall application.</span></span>
- <span data-ttu-id="fbce6-174">Úplné systémové testování volání prováděných napříč různými službami.</span><span class="sxs-lookup"><span data-stu-id="fbce6-174">Full system testing of calls made across disparate services.</span></span>

<span data-ttu-id="fbce6-175">Nakonec existují řešení, která řeší všechny tyto výzvy, včetně klepnutí na výhody bez serveru, které jsou popsány později.</span><span class="sxs-lookup"><span data-stu-id="fbce6-175">Ultimately there are solutions to address all of these challenges, including tapping into the benefits of serverless that are discussed later.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="fbce6-176">[Předchozí](index.md)
>[Další](architecture-deployment-approaches.md)</span><span class="sxs-lookup"><span data-stu-id="fbce6-176">[Previous](index.md)
[Next](architecture-deployment-approaches.md)</span></span>
