---
title: "Boji se složitost firmy v Mikroslužbu s DDD a CQRS vzorky"
description: "Architektura Mikroslužeb .NET pro aplikace .NET Kontejnerizované | Boji se složitost firmy v Mikroslužbu s DDD a CQRS vzorky"
keywords: "Docker, Mikroslužeb, ASP.NET, kontejneru"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: be2d8a2fd77d65b82574efde3b9922a1176ad2f2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="tackling-business-complexity-in-a-microservice-with-ddd-and-cqrs-patterns"></a><span data-ttu-id="ce81e-104">Boji se složitost firmy v Mikroslužbu s DDD a CQRS vzorky</span><span class="sxs-lookup"><span data-stu-id="ce81e-104">Tackling Business Complexity in a Microservice with DDD and CQRS Patterns</span></span>

<span data-ttu-id="ce81e-105">*Návrh modelu domény pro každou mikroslužbu nebo ohraničenou kontext, který se vztahuje k pochopení obchodní domény.*</span><span class="sxs-lookup"><span data-stu-id="ce81e-105">*Design a domain model for each microservice or Bounded Context that reflects understanding of the business domain.*</span></span>

<span data-ttu-id="ce81e-106">Tato část se zaměřuje na pokročilejší mikroslužeb, který implementujete, když potřebujete řešení komplexních subsystémy nebo mikroslužeb odvozené od znalosti odborníků domény s proměnlivých obchodní pravidla.</span><span class="sxs-lookup"><span data-stu-id="ce81e-106">This section focuses on more advanced microservices that you implement when you need to tackle complex subsystems, or microservices derived from the knowledge of domain experts with ever-changing business rules.</span></span> <span data-ttu-id="ce81e-107">Architektura vzory použít v této části jsou založené na základě domény návrhu (DDD) a přístupy k příkazu a dotaz odpovědnost oddělení (CQRS), jak ukazuje následující obrázek 9-1.</span><span class="sxs-lookup"><span data-stu-id="ce81e-107">The architecture patterns used in this section are based on domain-driven design (DDD) and Command and Query Responsibility Segregation (CQRS) approaches, as illustrated in Figure 9-1.</span></span>

![](./media/image1.png)

<span data-ttu-id="ce81e-108">**Obrázek 9-1**.</span><span class="sxs-lookup"><span data-stu-id="ce81e-108">**Figure 9-1**.</span></span> <span data-ttu-id="ce81e-109">Architektura externí mikroslužbu versus vzory interní architekturu pro každý mikroslužbu</span><span class="sxs-lookup"><span data-stu-id="ce81e-109">External microservice architecture versus internal architecture patterns for each microservice</span></span>

<span data-ttu-id="ce81e-110">Většina techniky pro data řízené mikroslužeb, jako je například implementaci služby webového rozhraní API ASP.NET Core nebo jak vystavit metadata Swagger s Swashbuckle, je však také pro pokročilejší mikroslužeb implementuje interně pomocí DDD vzory.</span><span class="sxs-lookup"><span data-stu-id="ce81e-110">However, most of the techniques for data driven microservices, such as how to implement an ASP.NET Core Web API service or how to expose Swagger metadata with Swashbuckle, are also applicable to the more advanced microservices implemented internally with DDD patterns.</span></span> <span data-ttu-id="ce81e-111">Tato část je rozšířením předchozích sekcí, protože většina postupy popsané dříve platí také zde nebo pro jakýkoli druh mikroslužby.</span><span class="sxs-lookup"><span data-stu-id="ce81e-111">This section is an extension of the previous sections, because most of the practices explained earlier also apply here or for any kind of microservice.</span></span>

<span data-ttu-id="ce81e-112">Tato část obsahuje podrobnosti nejprve zjednodušené CQRS vzory použitou v eShopOnContainers odkaz na aplikaci.</span><span class="sxs-lookup"><span data-stu-id="ce81e-112">This section first provides details on the simplified CQRS patterns used in the eShopOnContainers reference application.</span></span> <span data-ttu-id="ce81e-113">Později zobrazí se přehled DDD techniky, které vám umožní najít běžných vzorů, které můžete opakovaně použít ve svých aplikacích.</span><span class="sxs-lookup"><span data-stu-id="ce81e-113">Later, you will get an overview of the DDD techniques that enable you to find common patterns that you can reuse in your applications.</span></span>

<span data-ttu-id="ce81e-114">DDD je velké téma s bohatou sadu prostředků pro učení.</span><span class="sxs-lookup"><span data-stu-id="ce81e-114">DDD is a large topic with a rich set of resources for learning.</span></span> <span data-ttu-id="ce81e-115">Můžete spustit pomocí books jako [Domain-Driven návrhu](https://domainlanguage.com/ddd/) zařízení Erica Evans a další materiály z Vaughn Vernon, Jimmy Nilsson, Gregu Young, Udi Dahan, Jimmy Bogard a mnoho dalších DDD nebo CQRS odborníky.</span><span class="sxs-lookup"><span data-stu-id="ce81e-115">You can start with books like [Domain-Driven Design](https://domainlanguage.com/ddd/) by Eric Evans and additional materials from Vaughn Vernon, Jimmy Nilsson, Greg Young, Udi Dahan, Jimmy Bogard, and many other DDD/CQRS experts.</span></span> <span data-ttu-id="ce81e-116">Ale většina vše, co je potřeba k vyzkoušení se dozvíte, jak použít techniky DDD z konverzace, whiteboarding a modelování relace s odborníky ve vaší doméně konkrétní obchodní domény.</span><span class="sxs-lookup"><span data-stu-id="ce81e-116">But most of all you need to try to learn how to apply DDD techniques from the conversations, whiteboarding, and domain modeling sessions with the experts in your concrete business domain.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="ce81e-117">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="ce81e-117">Additional resources</span></span>

##### <a name="ddd-domain-driven-design"></a><span data-ttu-id="ce81e-118">DDD (návrh řízené domény)</span><span class="sxs-lookup"><span data-stu-id="ce81e-118">DDD (Domain-Driven Design)</span></span>

-   <span data-ttu-id="ce81e-119">**Zařízení Evans Erica. Jazyk domény**
    [*http://domainlanguage.com/*](http://domainlanguage.com/)</span><span class="sxs-lookup"><span data-stu-id="ce81e-119">**Eric Evans. Domain Language**
[*http://domainlanguage.com/*](http://domainlanguage.com/)</span></span>

-   <span data-ttu-id="ce81e-120">**Martin Fowler. Domény řízené návrhu**
    [*http://martinfowler.com/tags/domain%20driven%20design.html*](http://martinfowler.com/tags/domain%20driven%20design.html)</span><span class="sxs-lookup"><span data-stu-id="ce81e-120">**Martin Fowler. Domain-Driven Design**
[*http://martinfowler.com/tags/domain%20driven%20design.html*](http://martinfowler.com/tags/domain%20driven%20design.html)</span></span>

-   <span data-ttu-id="ce81e-121">**Jimmy Bogard. Posílení doménu: Základy**
    [*https://lostechies.com/jimmybogard/2010/02/04/strengthening-your-domain-a-primer/*](https://lostechies.com/jimmybogard/2010/02/04/strengthening-your-domain-a-primer/)</span><span class="sxs-lookup"><span data-stu-id="ce81e-121">**Jimmy Bogard. Strengthening your domain: a primer**
[*https://lostechies.com/jimmybogard/2010/02/04/strengthening-your-domain-a-primer/*](https://lostechies.com/jimmybogard/2010/02/04/strengthening-your-domain-a-primer/)</span></span>

##### <a name="ddd-books"></a><span data-ttu-id="ce81e-122">DDD knihy</span><span class="sxs-lookup"><span data-stu-id="ce81e-122">DDD books</span></span>

-   <span data-ttu-id="ce81e-123">**Zařízení Evans Erica. Řízené domény návrhu: Boji se složitostí při vysílat softwaru**
    [*https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/*](https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/)</span><span class="sxs-lookup"><span data-stu-id="ce81e-123">**Eric Evans. Domain-Driven Design: Tackling Complexity in the Heart of Software**
[*https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/*](https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/)</span></span>

-   <span data-ttu-id="ce81e-124">**Zařízení Evans Erica. Odkaz na základě domény návrhu: Definice a souhrny vzor**
    [*https://www.amazon.com/Domain-Driven-Design-Reference-Definitions-2014-09-22/dp/B01N8YB4ZO/*](https://www.amazon.com/Domain-Driven-Design-Reference-Definitions-2014-09-22/dp/B01N8YB4ZO/)</span><span class="sxs-lookup"><span data-stu-id="ce81e-124">**Eric Evans. Domain-Driven Design Reference: Definitions and Pattern Summaries**
[*https://www.amazon.com/Domain-Driven-Design-Reference-Definitions-2014-09-22/dp/B01N8YB4ZO/*](https://www.amazon.com/Domain-Driven-Design-Reference-Definitions-2014-09-22/dp/B01N8YB4ZO/)</span></span>

-   <span data-ttu-id="ce81e-125">**Vaughn Vernon. Implementace návrhu řízené domény**
    [*https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/*](https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/)</span><span class="sxs-lookup"><span data-stu-id="ce81e-125">**Vaughn Vernon. Implementing Domain-Driven Design**
[*https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/*](https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/)</span></span>

-   <span data-ttu-id="ce81e-126">**Vaughn Vernon. Domény řízené návrhu destilovaná**
    [*https://www.amazon.com/Domain-Driven-Design-Distilled-Vaughn-Vernon/dp/0134434420/*](https://www.amazon.com/Domain-Driven-Design-Distilled-Vaughn-Vernon/dp/0134434420/)</span><span class="sxs-lookup"><span data-stu-id="ce81e-126">**Vaughn Vernon. Domain-Driven Design Distilled**
[*https://www.amazon.com/Domain-Driven-Design-Distilled-Vaughn-Vernon/dp/0134434420/*](https://www.amazon.com/Domain-Driven-Design-Distilled-Vaughn-Vernon/dp/0134434420/)</span></span>

-   <span data-ttu-id="ce81e-127">**Jimmy Nilsson. Použití řízené domény návrhu a vzory**
    [*https://www.amazon.com/Applying-Domain-Driven-Design-Patterns-Examples/dp/0321268202/*](https://www.amazon.com/Applying-Domain-Driven-Design-Patterns-Examples/dp/0321268202/)</span><span class="sxs-lookup"><span data-stu-id="ce81e-127">**Jimmy Nilsson. Applying Domain-Driven Design and Patterns**
[*https://www.amazon.com/Applying-Domain-Driven-Design-Patterns-Examples/dp/0321268202/*](https://www.amazon.com/Applying-Domain-Driven-Design-Patterns-Examples/dp/0321268202/)</span></span>

-   <span data-ttu-id="ce81e-128">**Cesaru členka Torre. Průvodce vrstvený N architektura orientovaná na doméně s .NET**
    [*https://www.amazon.com/N-Layered-Domain-Oriented-Architecture-Guide-NET/dp/8493903612/*](https://www.amazon.com/N-Layered-Domain-Oriented-Architecture-Guide-NET/dp/8493903612/)</span><span class="sxs-lookup"><span data-stu-id="ce81e-128">**Cesar de la Torre. N-Layered Domain-Oriented Architecture Guide with .NET**
[*https://www.amazon.com/N-Layered-Domain-Oriented-Architecture-Guide-NET/dp/8493903612/*](https://www.amazon.com/N-Layered-Domain-Oriented-Architecture-Guide-NET/dp/8493903612/)</span></span>

-   <span data-ttu-id="ce81e-129">**Opisek Avram a Floyd Marinescu. Domény řízené návrhu rychle**
    [*https://www.amazon.com/Domain-Driven-Design-Quickly-Abel-Avram/dp/1411609255/*](https://www.amazon.com/Domain-Driven-Design-Quickly-Abel-Avram/dp/1411609255/)</span><span class="sxs-lookup"><span data-stu-id="ce81e-129">**Abel Avram and Floyd Marinescu. Domain-Driven Design Quickly**
[*https://www.amazon.com/Domain-Driven-Design-Quickly-Abel-Avram/dp/1411609255/*](https://www.amazon.com/Domain-Driven-Design-Quickly-Abel-Avram/dp/1411609255/)</span></span>

<span data-ttu-id="ce81e-130">DDD školení</span><span class="sxs-lookup"><span data-stu-id="ce81e-130">DDD training</span></span>

-   <span data-ttu-id="ce81e-131">**Julie Lerman a Steve Smith. Základy návrhu řízené domény**
    [*http://bit.ly/PS-DDD*](http://bit.ly/PS-DDD)</span><span class="sxs-lookup"><span data-stu-id="ce81e-131">**Julie Lerman and Steve Smith. Domain-Driven Design Fundamentals**
[*http://bit.ly/PS-DDD*](http://bit.ly/PS-DDD)</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="ce81e-132">[Předchozí] (.. / multi-container-microservice-net-applications/test-aspnet-core-services-web-apps.md) [Další] (apply-simplified-microservice-cqrs-ddd-patterns.md)</span><span class="sxs-lookup"><span data-stu-id="ce81e-132">[Previous] (../multi-container-microservice-net-applications/test-aspnet-core-services-web-apps.md) [Next] (apply-simplified-microservice-cqrs-ddd-patterns.md)</span></span>
