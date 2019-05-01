---
title: Zvládnutí firemní složitosti v mikroslužbě pomocí vzorů DDD a CQRS
description: Architektura Mikroslužeb .NET pro Kontejnerizované aplikace .NET | Naučte se řešit komplexní obchodní scénáře použití vzorů DDD a CQRS
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/08/2018
ms.openlocfilehash: f17acd6765de96bf8cec28c4e212733822fa0b73
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62019760"
---
# <a name="tackle-business-complexity-in-a-microservice-with-ddd-and-cqrs-patterns"></a><span data-ttu-id="05d43-103">Řešit firemní složitosti v Mikroslužbě pomocí vzorů DDD a CQRS</span><span class="sxs-lookup"><span data-stu-id="05d43-103">Tackle Business Complexity in a Microservice with DDD and CQRS Patterns</span></span>

<span data-ttu-id="05d43-104">*Návrh modelem domény pro jednotlivé mikroslužby nebo ohraničená kontextu, který se zobrazuje přehled o obchodní domény.*</span><span class="sxs-lookup"><span data-stu-id="05d43-104">*Design a domain model for each microservice or Bounded Context that reflects understanding of the business domain.*</span></span>

<span data-ttu-id="05d43-105">Tato část se zaměřuje na pokročilejší mikroslužeb, které lze implementovat budete muset řešit komplexní subsystémy nebo mikroslužeb odvozené ze znalostí odborníky na domény s neustále se měnící obchodní pravidla.</span><span class="sxs-lookup"><span data-stu-id="05d43-105">This section focuses on more advanced microservices that you implement when you need to tackle complex subsystems, or microservices derived from the knowledge of domain experts with ever-changing business rules.</span></span> <span data-ttu-id="05d43-106">Tyto architektury vzory se dají použít v této části jsou založené na návrhu řízeného doménou (DDD) a přístupy k příkazu a model dělení zodpovědnosti dotazů (CQRS), jak je znázorněno na obrázku 7-1.</span><span class="sxs-lookup"><span data-stu-id="05d43-106">The architecture patterns used in this section are based on domain-driven design (DDD) and Command and Query Responsibility Segregation (CQRS) approaches, as illustrated in Figure 7-1.</span></span>

![Rozdíl mezi externí architektury: mikroslužeb vzory, brány rozhraní API, odolné komunikace, publikování a odběr, atd. a interní architekturu: data driven/CRUD vzorů DDD, vkládání závislostí, více knihoven, atd.](./media/image1.png)

<span data-ttu-id="05d43-108">**Obrázek 7 – 1**.</span><span class="sxs-lookup"><span data-stu-id="05d43-108">**Figure 7-1**.</span></span> <span data-ttu-id="05d43-109">Architekturu mikroslužeb externí a interní architekturu vzorů u jednotlivých mikroslužeb</span><span class="sxs-lookup"><span data-stu-id="05d43-109">External microservice architecture versus internal architecture patterns for each microservice</span></span>

<span data-ttu-id="05d43-110">Většina techniky pro mikroslužby, jako je například implementace služby webového rozhraní API ASP.NET Core nebo jak vystavit metadata Swagger s Swashbuckle nebo službou NSwag, na základě dat je však také lze použít na pokročilejší mikroslužeb implementována interně pomocí Vzorů DDD.</span><span class="sxs-lookup"><span data-stu-id="05d43-110">However, most of the techniques for data driven microservices, such as how to implement an ASP.NET Core Web API service or how to expose Swagger metadata with Swashbuckle or NSwag, are also applicable to the more advanced microservices implemented internally with DDD patterns.</span></span> <span data-ttu-id="05d43-111">Tato část je rozšířením v předchozích částech, protože většina údajů je vysvětleno výše platí také zde nebo pro jakýkoli druh mikroslužeb.</span><span class="sxs-lookup"><span data-stu-id="05d43-111">This section is an extension of the previous sections, because most of the practices explained earlier also apply here or for any kind of microservice.</span></span>

<span data-ttu-id="05d43-112">V této části nejprve poskytuje podrobné informace o jednodušší vzorů CQRS používaných v aplikaci eShopOnContainers odkaz na aplikaci.</span><span class="sxs-lookup"><span data-stu-id="05d43-112">This section first provides details on the simplified CQRS patterns used in the eShopOnContainers reference application.</span></span> <span data-ttu-id="05d43-113">Později získáte přehled o DDD techniky, které vám umožní najít běžné vzory, které můžete znovu použít ve svých aplikacích.</span><span class="sxs-lookup"><span data-stu-id="05d43-113">Later, you will get an overview of the DDD techniques that enable you to find common patterns that you can reuse in your applications.</span></span>

<span data-ttu-id="05d43-114">DDD je velké téma s širokou škálu materiálů.</span><span class="sxs-lookup"><span data-stu-id="05d43-114">DDD is a large topic with a rich set of resources for learning.</span></span> <span data-ttu-id="05d43-115">Můžete začít s knihy stejně jako [Domain-Driven Design](https://domainlanguage.com/ddd/) Eric Evans a další materiály od Vaughn Vernon Jimmy Nilsson, Grega Younga, Udi Dahan, Jimmy Bogard a mnoha dalšími experty DDD a CQRS.</span><span class="sxs-lookup"><span data-stu-id="05d43-115">You can start with books like [Domain-Driven Design](https://domainlanguage.com/ddd/) by Eric Evans and additional materials from Vaughn Vernon, Jimmy Nilsson, Greg Young, Udi Dahan, Jimmy Bogard, and many other DDD/CQRS experts.</span></span> <span data-ttu-id="05d43-116">Ale většinu z vás všechny nutné pokusí zjistěte, jak použít DDD techniky z konverzace, využití tabulí a modelování semináře s odborníky ve vaší doméně konkrétní obchodní domény.</span><span class="sxs-lookup"><span data-stu-id="05d43-116">But most of all you need to try to learn how to apply DDD techniques from the conversations, whiteboarding, and domain modeling sessions with the experts in your concrete business domain.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="05d43-117">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="05d43-117">Additional resources</span></span>

##### <a name="ddd-domain-driven-design"></a><span data-ttu-id="05d43-118">DDD (návrhem řízeným doménou)</span><span class="sxs-lookup"><span data-stu-id="05d43-118">DDD (Domain-Driven Design)</span></span>

- <span data-ttu-id="05d43-119">**Eric Evans. Jazyk domény** \\</span><span class="sxs-lookup"><span data-stu-id="05d43-119">**Eric Evans. Domain Language** \\</span></span>
  <https://domainlanguage.com/>

- <span data-ttu-id="05d43-120">**Martina Fowlera. Domain-Driven Design** \\</span><span class="sxs-lookup"><span data-stu-id="05d43-120">**Martin Fowler. Domain-Driven Design** \\</span></span>
  <https://martinfowler.com/tags/domain%20driven%20design.html>

- <span data-ttu-id="05d43-121">**Jimmy Bogard. Posílení vaší domény: Základy** \\</span><span class="sxs-lookup"><span data-stu-id="05d43-121">**Jimmy Bogard. Strengthening your domain: a primer** \\</span></span>
  <https://lostechies.com/jimmybogard/2010/02/04/strengthening-your-domain-a-primer/>

##### <a name="ddd-books"></a><span data-ttu-id="05d43-122">DDD knihy</span><span class="sxs-lookup"><span data-stu-id="05d43-122">DDD books</span></span>

- <span data-ttu-id="05d43-123">**Eric Evans. Návrhy řízené doménou: Použití složitosti srdce softwaru** \\</span><span class="sxs-lookup"><span data-stu-id="05d43-123">**Eric Evans. Domain-Driven Design: Tackling Complexity in the Heart of Software** \\</span></span>
  <https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/>

- <span data-ttu-id="05d43-124">**Eric Evans. Reference pro návrhy řízené doménou. Definice a souhrny vzor** \\</span><span class="sxs-lookup"><span data-stu-id="05d43-124">**Eric Evans. Domain-Driven Design Reference: Definitions and Pattern Summaries** \\</span></span>
  <https://www.amazon.com/Domain-Driven-Design-Reference-Definitions-2014-09-22/dp/B01N8YB4ZO/>

- <span data-ttu-id="05d43-125">**Vaughn Vernon. Implementace návrhu řízeného doménou** \\</span><span class="sxs-lookup"><span data-stu-id="05d43-125">**Vaughn Vernon. Implementing Domain-Driven Design** \\</span></span>
  <https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/>

- <span data-ttu-id="05d43-126">**Vaughn Vernon. Destilované návrhem řízeným doménou** \\</span><span class="sxs-lookup"><span data-stu-id="05d43-126">**Vaughn Vernon. Domain-Driven Design Distilled** \\</span></span>
  <https://www.amazon.com/Domain-Driven-Design-Distilled-Vaughn-Vernon/dp/0134434420/>

- <span data-ttu-id="05d43-127">**Jimmy Nilsson. Použití návrhu řízeného doménou a vzory** \\</span><span class="sxs-lookup"><span data-stu-id="05d43-127">**Jimmy Nilsson. Applying Domain-Driven Design and Patterns** \\</span></span>
  <https://www.amazon.com/Applying-Domain-Driven-Design-Patterns-Examples/dp/0321268202/>

- <span data-ttu-id="05d43-128">**De la Torre Cesarovi. Průvodce N vrstvami architektura orientovaná na doméně s využitím .NET** \\</span><span class="sxs-lookup"><span data-stu-id="05d43-128">**Cesar de la Torre. N-Layered Domain-Oriented Architecture Guide with .NET** \\</span></span>
  <https://www.amazon.com/N-Layered-Domain-Oriented-Architecture-Guide-NET/dp/8493903612/>

- <span data-ttu-id="05d43-129">**Abel Avram a Floyd Marinescu. Řízené doménou návrh rychle** \\</span><span class="sxs-lookup"><span data-stu-id="05d43-129">**Abel Avram and Floyd Marinescu. Domain-Driven Design Quickly** \\</span></span>
  <https://www.amazon.com/Domain-Driven-Design-Quickly-Abel-Avram/dp/1411609255/>

- <span data-ttu-id="05d43-130">**Scott Millett, Nick ladění – vzory, zásady a postupy při návrhu řízeného doménou** \\</span><span class="sxs-lookup"><span data-stu-id="05d43-130">**Scott Millett, Nick Tune - Patterns, Principles, and Practices of Domain-Driven Design** \\</span></span>
  <http://www.wrox.com/WileyCDA/WroxTitle/Patterns-Principles-and-Practices-of-Domain-Driven-Design.productCd-1118714709.html>

##### <a name="ddd-training"></a><span data-ttu-id="05d43-131">DDD školení</span><span class="sxs-lookup"><span data-stu-id="05d43-131">DDD training</span></span>

- <span data-ttu-id="05d43-132">**Julie Lerman a Steve Smith. Základy návrhu řízeného doménou** \\</span><span class="sxs-lookup"><span data-stu-id="05d43-132">**Julie Lerman and Steve Smith. Domain-Driven Design Fundamentals** \\</span></span>
  <https://bit.ly/PS-DDD>

>[!div class="step-by-step"]
><span data-ttu-id="05d43-133">[Předchozí](../multi-container-microservice-net-applications/implement-api-gateways-with-ocelot.md)
>[další](apply-simplified-microservice-cqrs-ddd-patterns.md)</span><span class="sxs-lookup"><span data-stu-id="05d43-133">[Previous](../multi-container-microservice-net-applications/implement-api-gateways-with-ocelot.md)
[Next](apply-simplified-microservice-cqrs-ddd-patterns.md)</span></span>
