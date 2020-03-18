---
title: Zvládnutí firemní složitosti v mikroslužbě pomocí vzorů DDD a CQRS
description: Architektura mikroslužeb .NET pro kontejnerizované aplikace .NET | Pochopit, jak řešit složité obchodní scénáře použití DDD a CQRS vzory
ms.date: 10/08/2018
ms.openlocfilehash: 88b105b68307c8587f877bb9ddf370e143d8539b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73739827"
---
# <a name="tackle-business-complexity-in-a-microservice-with-ddd-and-cqrs-patterns"></a><span data-ttu-id="9dea5-103">Řešení obchodní složitosti v mikroslužbě se vzory DDD a CQRS</span><span class="sxs-lookup"><span data-stu-id="9dea5-103">Tackle Business Complexity in a Microservice with DDD and CQRS Patterns</span></span>

<span data-ttu-id="9dea5-104">*Navrhněte model domény pro každou mikroslužbu nebo ohraničený kontext, který odráží pochopení obchodní domény.*</span><span class="sxs-lookup"><span data-stu-id="9dea5-104">*Design a domain model for each microservice or Bounded Context that reflects understanding of the business domain.*</span></span>

<span data-ttu-id="9dea5-105">Tato část se zaměřuje na pokročilejší mikroslužeb, které implementujete, když potřebujete řešit složité subsystémy nebo mikroslužeb odvozené ze znalostí doménových odborníků s neustále se měnícími obchodními pravidly.</span><span class="sxs-lookup"><span data-stu-id="9dea5-105">This section focuses on more advanced microservices that you implement when you need to tackle complex subsystems, or microservices derived from the knowledge of domain experts with ever-changing business rules.</span></span> <span data-ttu-id="9dea5-106">Vzory architektury použité v této části jsou založeny na přístupech návrhu řízeného doménou (DDD) a segregátem odpovědnosti příkazů a dotazů (CQRS), jak je znázorněno na obrázku 7-1.</span><span class="sxs-lookup"><span data-stu-id="9dea5-106">The architecture patterns used in this section are based on domain-driven design (DDD) and Command and Query Responsibility Segregation (CQRS) approaches, as illustrated in Figure 7-1.</span></span>

:::image type="complex" source="./media/index/internal-versus-external-architecture.png" alt-text="Diagram porovnání externí a vnitřní vzory architektury.":::
<span data-ttu-id="9dea5-108">Rozdíl mezi externí architekturou: vzory mikroslužeb, brány rozhraní API, odolná komunikace, pub/sub atd.</span><span class="sxs-lookup"><span data-stu-id="9dea5-108">Difference between external architecture: microservice patterns, API gateways, resilient communications, pub/sub, etc., and internal architecture: data driven/CRUD, DDD patterns, dependency injection, multiple libraries, etc.</span></span>
:::image-end:::

<span data-ttu-id="9dea5-109">**Obrázek 7-1**.</span><span class="sxs-lookup"><span data-stu-id="9dea5-109">**Figure 7-1**.</span></span> <span data-ttu-id="9dea5-110">Externí architektura mikroslužeb versus vzory interní architektury pro každou mikroslužbu</span><span class="sxs-lookup"><span data-stu-id="9dea5-110">External microservice architecture versus internal architecture patterns for each microservice</span></span>

<span data-ttu-id="9dea5-111">Většina technik pro mikroslužby řízené daty, například jak implementovat službu ASP.NET core web api nebo jak vystavit metadata Swagger s Swashbuckle nebo NSwag, jsou také použitelné pro pokročilejší mikroslužby implementované interně s Vzory DDD.</span><span class="sxs-lookup"><span data-stu-id="9dea5-111">However, most of the techniques for data driven microservices, such as how to implement an ASP.NET Core Web API service or how to expose Swagger metadata with Swashbuckle or NSwag, are also applicable to the more advanced microservices implemented internally with DDD patterns.</span></span> <span data-ttu-id="9dea5-112">Tato část je rozšíření předchozí části, protože většina postupů vysvětlených dříve platí také zde nebo pro jakýkoli druh mikroslužeb.</span><span class="sxs-lookup"><span data-stu-id="9dea5-112">This section is an extension of the previous sections, because most of the practices explained earlier also apply here or for any kind of microservice.</span></span>

<span data-ttu-id="9dea5-113">Tato část nejprve obsahuje podrobnosti o zjednodušené CQRS vzory používané v eShopOnContainers referenční aplikace.</span><span class="sxs-lookup"><span data-stu-id="9dea5-113">This section first provides details on the simplified CQRS patterns used in the eShopOnContainers reference application.</span></span> <span data-ttu-id="9dea5-114">Později získáte přehled o technikách DDD, které vám umožní najít běžné vzory, které můžete znovu použít ve svých aplikacích.</span><span class="sxs-lookup"><span data-stu-id="9dea5-114">Later, you will get an overview of the DDD techniques that enable you to find common patterns that you can reuse in your applications.</span></span>

<span data-ttu-id="9dea5-115">DDD je velké téma s bohatou sadou zdrojů pro učení.</span><span class="sxs-lookup"><span data-stu-id="9dea5-115">DDD is a large topic with a rich set of resources for learning.</span></span> <span data-ttu-id="9dea5-116">Můžete začít s knihami, jako [je doména-Driven Design](https://domainlanguage.com/ddd/) Eric Evans a další materiály od Vaughn Vernon, Jimmy Nilsson, Greg Young, Udi Dahan, Jimmy Bogard, a mnoho dalších Odborníků DDD / CQRS.</span><span class="sxs-lookup"><span data-stu-id="9dea5-116">You can start with books like [Domain-Driven Design](https://domainlanguage.com/ddd/) by Eric Evans and additional materials from Vaughn Vernon, Jimmy Nilsson, Greg Young, Udi Dahan, Jimmy Bogard, and many other DDD/CQRS experts.</span></span> <span data-ttu-id="9dea5-117">Ale ze všeho nejvíc se musíte pokusit naučit, jak aplikovat Techniky DDD z rozhovorů, whiteboarding, a doména modelování zasedání s odborníky ve vaší konkrétní obchodní oblasti.</span><span class="sxs-lookup"><span data-stu-id="9dea5-117">But most of all you need to try to learn how to apply DDD techniques from the conversations, whiteboarding, and domain modeling sessions with the experts in your concrete business domain.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="9dea5-118">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="9dea5-118">Additional resources</span></span>

##### <a name="ddd-domain-driven-design"></a><span data-ttu-id="9dea5-119">DDD (návrh řízený doménou)</span><span class="sxs-lookup"><span data-stu-id="9dea5-119">DDD (Domain-Driven Design)</span></span>

- <span data-ttu-id="9dea5-120">**Eric Evans. Jazyk domény** </span><span class="sxs-lookup"><span data-stu-id="9dea5-120">**Eric Evans. Domain Language** </span></span>\
  <https://domainlanguage.com/>

- <span data-ttu-id="9dea5-121">**Martin Fowler. Návrh řízený doménou** </span><span class="sxs-lookup"><span data-stu-id="9dea5-121">**Martin Fowler. Domain-Driven Design** </span></span>\
  <https://martinfowler.com/tags/domain%20driven%20design.html>

- <span data-ttu-id="9dea5-122">**Jimmyho Bogarda. Posílení vaší domény: základní nátěr** </span><span class="sxs-lookup"><span data-stu-id="9dea5-122">**Jimmy Bogard. Strengthening your domain: a primer** </span></span>\
  <https://lostechies.com/jimmybogard/2010/02/04/strengthening-your-domain-a-primer/>

##### <a name="ddd-books"></a><span data-ttu-id="9dea5-123">DDD knihy</span><span class="sxs-lookup"><span data-stu-id="9dea5-123">DDD books</span></span>

- <span data-ttu-id="9dea5-124">**Eric Evans. Návrh řízený doménou: Řešení složitosti v srdci softwaru** </span><span class="sxs-lookup"><span data-stu-id="9dea5-124">**Eric Evans. Domain-Driven Design: Tackling Complexity in the Heart of Software** </span></span>\
  <https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/>

- <span data-ttu-id="9dea5-125">**Eric Evans. Odkaz na návrh založený na doméně: Definice a souhrny vzorů** </span><span class="sxs-lookup"><span data-stu-id="9dea5-125">**Eric Evans. Domain-Driven Design Reference: Definitions and Pattern Summaries** </span></span>\
  <https://www.amazon.com/Domain-Driven-Design-Reference-Definitions-2014-09-22/dp/B01N8YB4ZO/>

- <span data-ttu-id="9dea5-126">**Vaughn Vernon, to je můj zástupce. Implementace návrhu řízeného doménou** </span><span class="sxs-lookup"><span data-stu-id="9dea5-126">**Vaughn Vernon. Implementing Domain-Driven Design** </span></span>\
  <https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/>

- <span data-ttu-id="9dea5-127">**Vaughn Vernon, to je můj zástupce. Destilovaný návrh řízený doménou** </span><span class="sxs-lookup"><span data-stu-id="9dea5-127">**Vaughn Vernon. Domain-Driven Design Distilled** </span></span>\
  <https://www.amazon.com/Domain-Driven-Design-Distilled-Vaughn-Vernon/dp/0134434420/>

- <span data-ttu-id="9dea5-128">**Jimmy Nilsson. Použití návrhu a vzorů řízených doménou** </span><span class="sxs-lookup"><span data-stu-id="9dea5-128">**Jimmy Nilsson. Applying Domain-Driven Design and Patterns** </span></span>\
  <https://www.amazon.com/Applying-Domain-Driven-Design-Patterns-Examples/dp/0321268202/>

- <span data-ttu-id="9dea5-129">**Cesar de la Torre. N-vrstvené architektura orientované na doménu s rozhraním .NET** </span><span class="sxs-lookup"><span data-stu-id="9dea5-129">**Cesar de la Torre. N-Layered Domain-Oriented Architecture Guide with .NET** </span></span>\
  <https://www.amazon.com/N-Layered-Domain-Oriented-Architecture-Guide-NET/dp/8493903612/>

- <span data-ttu-id="9dea5-130">**Abel Avram a Floyd Marinescu. Návrh řízený doménou rychle** </span><span class="sxs-lookup"><span data-stu-id="9dea5-130">**Abel Avram and Floyd Marinescu. Domain-Driven Design Quickly** </span></span>\
  <https://www.amazon.com/Domain-Driven-Design-Quickly-Abel-Avram/dp/1411609255/>

- <span data-ttu-id="9dea5-131">**Scott Millett, Nick Tune - vzory, principy a postupy návrhu řízeného doménou** </span><span class="sxs-lookup"><span data-stu-id="9dea5-131">**Scott Millett, Nick Tune - Patterns, Principles, and Practices of Domain-Driven Design** </span></span>\
  <http://www.wrox.com/WileyCDA/WroxTitle/Patterns-Principles-and-Practices-of-Domain-Driven-Design.productCd-1118714709.html>

##### <a name="ddd-training"></a><span data-ttu-id="9dea5-132">Školení DDD</span><span class="sxs-lookup"><span data-stu-id="9dea5-132">DDD training</span></span>

- <span data-ttu-id="9dea5-133">**Julie Lermanová a Steve Smith. Základy návrhu řízeného doménou** </span><span class="sxs-lookup"><span data-stu-id="9dea5-133">**Julie Lerman and Steve Smith. Domain-Driven Design Fundamentals** </span></span>\
  <https://bit.ly/PS-DDD>

>[!div class="step-by-step"]
><span data-ttu-id="9dea5-134">[Předchozí](../multi-container-microservice-net-applications/implement-api-gateways-with-ocelot.md)
>[další](apply-simplified-microservice-cqrs-ddd-patterns.md)</span><span class="sxs-lookup"><span data-stu-id="9dea5-134">[Previous](../multi-container-microservice-net-applications/implement-api-gateways-with-ocelot.md)
[Next](apply-simplified-microservice-cqrs-ddd-patterns.md)</span></span>
