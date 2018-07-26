---
title: Zvládnutí firemní složitosti v Mikroslužbě pomocí vzorů DDD a CQRS
description: Architektura Mikroslužeb .NET pro Kontejnerizované aplikace .NET | Zvládnutí firemní složitosti v Mikroslužbě pomocí vzorů DDD a CQRS
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 06/06/2018
ms.openlocfilehash: bc8ff6262436af6eb49a4ef8635d502e80b74b5a
ms.sourcegitcommit: 59b51cd7c95c75be85bd6ef715e9ef8c85720bac
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/06/2018
ms.locfileid: "37874384"
---
# <a name="tackling-business-complexity-in-a-microservice-with-ddd-and-cqrs-patterns"></a><span data-ttu-id="e7635-103">Zvládnutí firemní složitosti v Mikroslužbě pomocí vzorů DDD a CQRS</span><span class="sxs-lookup"><span data-stu-id="e7635-103">Tackling Business Complexity in a Microservice with DDD and CQRS Patterns</span></span>

<span data-ttu-id="e7635-104">*Návrh modelem domény pro jednotlivé mikroslužby nebo ohraničená kontextu, který se zobrazuje přehled o obchodní domény.*</span><span class="sxs-lookup"><span data-stu-id="e7635-104">*Design a domain model for each microservice or Bounded Context that reflects understanding of the business domain.*</span></span>

<span data-ttu-id="e7635-105">Tato část se zaměřuje na pokročilejší mikroslužeb, které lze implementovat budete muset řešit komplexní subsystémy nebo mikroslužeb odvozené ze znalostí odborníky na domény s neustále se měnící obchodní pravidla.</span><span class="sxs-lookup"><span data-stu-id="e7635-105">This section focuses on more advanced microservices that you implement when you need to tackle complex subsystems, or microservices derived from the knowledge of domain experts with ever-changing business rules.</span></span> <span data-ttu-id="e7635-106">Tyto architektury vzory se dají použít v této části jsou založené na návrhu řízeného doménou (DDD) a přístupy k příkazu a model dělení zodpovědnosti dotazů (CQRS), jak je znázorněno na obrázku 9-1.</span><span class="sxs-lookup"><span data-stu-id="e7635-106">The architecture patterns used in this section are based on domain-driven design (DDD) and Command and Query Responsibility Segregation (CQRS) approaches, as illustrated in Figure 9-1.</span></span>

![](./media/image1.png)

<span data-ttu-id="e7635-107">**Obrázek 9-1**.</span><span class="sxs-lookup"><span data-stu-id="e7635-107">**Figure 9-1**.</span></span> <span data-ttu-id="e7635-108">Architekturu mikroslužeb externí a interní architekturu vzorů u jednotlivých mikroslužeb</span><span class="sxs-lookup"><span data-stu-id="e7635-108">External microservice architecture versus internal architecture patterns for each microservice</span></span>

<span data-ttu-id="e7635-109">Většina techniky pro mikroslužby, jako je například implementace služby webového rozhraní API ASP.NET Core nebo jak vystavit metadata Swagger službou Swashbuckle, na základě dat je však také lze použít na pokročilejší mikroslužeb implementována interně pomocí DDD vzory.</span><span class="sxs-lookup"><span data-stu-id="e7635-109">However, most of the techniques for data driven microservices, such as how to implement an ASP.NET Core Web API service or how to expose Swagger metadata with Swashbuckle, are also applicable to the more advanced microservices implemented internally with DDD patterns.</span></span> <span data-ttu-id="e7635-110">Tato část je rozšířením v předchozích částech, protože většina údajů je vysvětleno výše platí také zde nebo pro jakýkoli druh mikroslužeb.</span><span class="sxs-lookup"><span data-stu-id="e7635-110">This section is an extension of the previous sections, because most of the practices explained earlier also apply here or for any kind of microservice.</span></span>

<span data-ttu-id="e7635-111">V této části nejprve poskytuje podrobné informace o jednodušší vzorů CQRS používaných v aplikaci eShopOnContainers odkaz na aplikaci.</span><span class="sxs-lookup"><span data-stu-id="e7635-111">This section first provides details on the simplified CQRS patterns used in the eShopOnContainers reference application.</span></span> <span data-ttu-id="e7635-112">Později získáte přehled o DDD techniky, které vám umožní najít běžné vzory, které můžete znovu použít ve svých aplikacích.</span><span class="sxs-lookup"><span data-stu-id="e7635-112">Later, you will get an overview of the DDD techniques that enable you to find common patterns that you can reuse in your applications.</span></span>

<span data-ttu-id="e7635-113">DDD je velké téma s širokou škálu materiálů.</span><span class="sxs-lookup"><span data-stu-id="e7635-113">DDD is a large topic with a rich set of resources for learning.</span></span> <span data-ttu-id="e7635-114">Můžete začít s knihy stejně jako [Domain-Driven Design](https://domainlanguage.com/ddd/) Eric Evans a další materiály od Vaughn Vernon Jimmy Nilsson, Grega Younga, Udi Dahan, Jimmy Bogard a mnoha dalšími experty DDD a CQRS.</span><span class="sxs-lookup"><span data-stu-id="e7635-114">You can start with books like [Domain-Driven Design](https://domainlanguage.com/ddd/) by Eric Evans and additional materials from Vaughn Vernon, Jimmy Nilsson, Greg Young, Udi Dahan, Jimmy Bogard, and many other DDD/CQRS experts.</span></span> <span data-ttu-id="e7635-115">Ale většinu z vás všechny nutné pokusí zjistěte, jak použít DDD techniky z konverzace, využití tabulí a modelování semináře s odborníky ve vaší doméně konkrétní obchodní domény.</span><span class="sxs-lookup"><span data-stu-id="e7635-115">But most of all you need to try to learn how to apply DDD techniques from the conversations, whiteboarding, and domain modeling sessions with the experts in your concrete business domain.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="e7635-116">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="e7635-116">Additional resources</span></span>

##### <a name="ddd-domain-driven-design"></a><span data-ttu-id="e7635-117">DDD (návrhem řízeným doménou)</span><span class="sxs-lookup"><span data-stu-id="e7635-117">DDD (Domain-Driven Design)</span></span>

-   <span data-ttu-id="e7635-118">**Eric Evans. Jazyk domény**
    [*https://domainlanguage.com/*](https://domainlanguage.com/)</span><span class="sxs-lookup"><span data-stu-id="e7635-118">**Eric Evans. Domain Language**
[*https://domainlanguage.com/*](https://domainlanguage.com/)</span></span>

-   <span data-ttu-id="e7635-119">**Martina Fowlera. Návrhy řízené doménou**
    [*https://martinfowler.com/tags/domain%20driven%20design.html*](https://martinfowler.com/tags/domain%20driven%20design.html)</span><span class="sxs-lookup"><span data-stu-id="e7635-119">**Martin Fowler. Domain-Driven Design**
[*https://martinfowler.com/tags/domain%20driven%20design.html*](https://martinfowler.com/tags/domain%20driven%20design.html)</span></span>

-   <span data-ttu-id="e7635-120">**Jimmy Bogard. Posílení vaší domény: Základy**
    [*https://lostechies.com/jimmybogard/2010/02/04/strengthening-your-domain-a-primer/*](https://lostechies.com/jimmybogard/2010/02/04/strengthening-your-domain-a-primer/)</span><span class="sxs-lookup"><span data-stu-id="e7635-120">**Jimmy Bogard. Strengthening your domain: a primer**
[*https://lostechies.com/jimmybogard/2010/02/04/strengthening-your-domain-a-primer/*](https://lostechies.com/jimmybogard/2010/02/04/strengthening-your-domain-a-primer/)</span></span>

##### <a name="ddd-books"></a><span data-ttu-id="e7635-121">DDD knihy</span><span class="sxs-lookup"><span data-stu-id="e7635-121">DDD books</span></span>

-   <span data-ttu-id="e7635-122">**Eric Evans. Návrhy řízené doménou: Použití složitosti srdce softwaru**
    [*https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/*](https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/)</span><span class="sxs-lookup"><span data-stu-id="e7635-122">**Eric Evans. Domain-Driven Design: Tackling Complexity in the Heart of Software**
[*https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/*](https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/)</span></span>

-   <span data-ttu-id="e7635-123">**Eric Evans. Návrhu řízeného doménou – referenční informace: Definice a souhrny vzor**
    [*https://www.amazon.com/Domain-Driven-Design-Reference-Definitions-2014-09-22/dp/B01N8YB4ZO/*](https://www.amazon.com/Domain-Driven-Design-Reference-Definitions-2014-09-22/dp/B01N8YB4ZO/)</span><span class="sxs-lookup"><span data-stu-id="e7635-123">**Eric Evans. Domain-Driven Design Reference: Definitions and Pattern Summaries**
[*https://www.amazon.com/Domain-Driven-Design-Reference-Definitions-2014-09-22/dp/B01N8YB4ZO/*](https://www.amazon.com/Domain-Driven-Design-Reference-Definitions-2014-09-22/dp/B01N8YB4ZO/)</span></span>

-   <span data-ttu-id="e7635-124">**Vaughn Vernon. Implementace návrhu řízeného doménou**
    [*https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/*](https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/)</span><span class="sxs-lookup"><span data-stu-id="e7635-124">**Vaughn Vernon. Implementing Domain-Driven Design**
[*https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/*](https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/)</span></span>

-   <span data-ttu-id="e7635-125">**Vaughn Vernon. Destilované návrhem řízeným doménou**
    [*https://www.amazon.com/Domain-Driven-Design-Distilled-Vaughn-Vernon/dp/0134434420/*](https://www.amazon.com/Domain-Driven-Design-Distilled-Vaughn-Vernon/dp/0134434420/)</span><span class="sxs-lookup"><span data-stu-id="e7635-125">**Vaughn Vernon. Domain-Driven Design Distilled**
[*https://www.amazon.com/Domain-Driven-Design-Distilled-Vaughn-Vernon/dp/0134434420/*](https://www.amazon.com/Domain-Driven-Design-Distilled-Vaughn-Vernon/dp/0134434420/)</span></span>

-   <span data-ttu-id="e7635-126">**Jimmy Nilsson. Použití návrhu řízeného doménou a vzory**
    [*https://www.amazon.com/Applying-Domain-Driven-Design-Patterns-Examples/dp/0321268202/*](https://www.amazon.com/Applying-Domain-Driven-Design-Patterns-Examples/dp/0321268202/)</span><span class="sxs-lookup"><span data-stu-id="e7635-126">**Jimmy Nilsson. Applying Domain-Driven Design and Patterns**
[*https://www.amazon.com/Applying-Domain-Driven-Design-Patterns-Examples/dp/0321268202/*](https://www.amazon.com/Applying-Domain-Driven-Design-Patterns-Examples/dp/0321268202/)</span></span>

-   <span data-ttu-id="e7635-127">**De la Torre Cesarovi. Průvodce N vrstvami architektura orientovaná na doméně s využitím .NET**
    [*https://www.amazon.com/N-Layered-Domain-Oriented-Architecture-Guide-NET/dp/8493903612/*](https://www.amazon.com/N-Layered-Domain-Oriented-Architecture-Guide-NET/dp/8493903612/)</span><span class="sxs-lookup"><span data-stu-id="e7635-127">**Cesar de la Torre. N-Layered Domain-Oriented Architecture Guide with .NET**
[*https://www.amazon.com/N-Layered-Domain-Oriented-Architecture-Guide-NET/dp/8493903612/*](https://www.amazon.com/N-Layered-Domain-Oriented-Architecture-Guide-NET/dp/8493903612/)</span></span>

-   <span data-ttu-id="e7635-128">**Abel Avram a Floyd Marinescu. Řízené doménou návrh rychle**
    [*https://www.amazon.com/Domain-Driven-Design-Quickly-Abel-Avram/dp/1411609255/*](https://www.amazon.com/Domain-Driven-Design-Quickly-Abel-Avram/dp/1411609255/)</span><span class="sxs-lookup"><span data-stu-id="e7635-128">**Abel Avram and Floyd Marinescu. Domain-Driven Design Quickly**
[*https://www.amazon.com/Domain-Driven-Design-Quickly-Abel-Avram/dp/1411609255/*](https://www.amazon.com/Domain-Driven-Design-Quickly-Abel-Avram/dp/1411609255/)</span></span>

<span data-ttu-id="e7635-129">DDD školení</span><span class="sxs-lookup"><span data-stu-id="e7635-129">DDD training</span></span>

-   <span data-ttu-id="e7635-130">**Julie Lerman a Steve Smith. Základy návrhu řízeného doménou**
    [*http://bit.ly/PS-DDD*](http://bit.ly/PS-DDD)</span><span class="sxs-lookup"><span data-stu-id="e7635-130">**Julie Lerman and Steve Smith. Domain-Driven Design Fundamentals**
[*http://bit.ly/PS-DDD*](http://bit.ly/PS-DDD)</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="e7635-131">[Předchozí](../multi-container-microservice-net-applications/implement-api-gateways-with-ocelot.md)
[další](apply-simplified-microservice-cqrs-ddd-patterns.md)</span><span class="sxs-lookup"><span data-stu-id="e7635-131">[Previous](../multi-container-microservice-net-applications/implement-api-gateways-with-ocelot.md)
[Next](apply-simplified-microservice-cqrs-ddd-patterns.md)</span></span>