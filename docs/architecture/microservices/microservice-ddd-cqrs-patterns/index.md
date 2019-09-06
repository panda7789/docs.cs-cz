---
title: Zvládnutí firemní složitosti v mikroslužbě pomocí vzorů DDD a CQRS
description: Architektura mikroslužeb .NET pro kontejnerové aplikace .NET | Pochopte, jak řešit složité obchodní scénáře, které používají vzory DDD a CQRS.
ms.date: 10/08/2018
ms.openlocfilehash: d311641e2ac73205c04c3f1147b54991585ce851
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "70295913"
---
# <a name="tackle-business-complexity-in-a-microservice-with-ddd-and-cqrs-patterns"></a><span data-ttu-id="83640-103">Řešení složitosti firmy v mikroslužbě pomocí vzorů DDD a CQRS</span><span class="sxs-lookup"><span data-stu-id="83640-103">Tackle Business Complexity in a Microservice with DDD and CQRS Patterns</span></span>

<span data-ttu-id="83640-104">*Navrhněte doménový model pro jednotlivé mikroslužby nebo s ohraničeným kontextem, který odráží porozumění obchodní doméně.*</span><span class="sxs-lookup"><span data-stu-id="83640-104">*Design a domain model for each microservice or Bounded Context that reflects understanding of the business domain.*</span></span>

<span data-ttu-id="83640-105">Tato část se zaměřuje na pokročilejší mikroslužby, které implementujete, když potřebujete vypořádat se se složitými subsystémy nebo mikroslužbami, které jsou odvozené od znalostí odborníků na domény s neustále se měnícími obchodními pravidly.</span><span class="sxs-lookup"><span data-stu-id="83640-105">This section focuses on more advanced microservices that you implement when you need to tackle complex subsystems, or microservices derived from the knowledge of domain experts with ever-changing business rules.</span></span> <span data-ttu-id="83640-106">Vzory architektury použité v této části jsou založené na CQRSch návrhech založených na doménách (DDD) a CQRS (Command and Query Responsibility Segregation) (), jak je znázorněno na obrázku 7-1.</span><span class="sxs-lookup"><span data-stu-id="83640-106">The architecture patterns used in this section are based on domain-driven design (DDD) and Command and Query Responsibility Segregation (CQRS) approaches, as illustrated in Figure 7-1.</span></span>

![Rozdíl mezi externí architekturou: vzory mikroslužeb, brány API, odolná komunikace, pub/sub atd. a interní architektura: řízené daty/CRUD, DDD vzory, vkládání závislostí, vícenásobné knihovny atd.](./media/image1.png)

<span data-ttu-id="83640-108">**Obrázek 7-1**.</span><span class="sxs-lookup"><span data-stu-id="83640-108">**Figure 7-1**.</span></span> <span data-ttu-id="83640-109">Externí architektura mikroslužeb oproti vnitřním schématům architektury pro jednotlivé mikroslužby</span><span class="sxs-lookup"><span data-stu-id="83640-109">External microservice architecture versus internal architecture patterns for each microservice</span></span>

<span data-ttu-id="83640-110">Většina technik pro mikroslužby řízené daty, jako je například implementace služby ASP.NET Core webového rozhraní API nebo zpřístupnění metadat Swagger pomocí swashbuckle nebo NSwag, se také vztahují na pokročilejší implementované mikroslužby s DDD vzory.</span><span class="sxs-lookup"><span data-stu-id="83640-110">However, most of the techniques for data driven microservices, such as how to implement an ASP.NET Core Web API service or how to expose Swagger metadata with Swashbuckle or NSwag, are also applicable to the more advanced microservices implemented internally with DDD patterns.</span></span> <span data-ttu-id="83640-111">Tato část je rozšířením předchozích sekcí, protože většina postupů, které jsme si vyznamenali dříve, platí i pro jakýkoliv druh mikroslužeb.</span><span class="sxs-lookup"><span data-stu-id="83640-111">This section is an extension of the previous sections, because most of the practices explained earlier also apply here or for any kind of microservice.</span></span>

<span data-ttu-id="83640-112">V této části najdete nejdřív podrobné informace o zjednodušených vzorech CQRS používaných v referenční aplikaci eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="83640-112">This section first provides details on the simplified CQRS patterns used in the eShopOnContainers reference application.</span></span> <span data-ttu-id="83640-113">Později získáte přehled technik DDD, které vám umožní najít běžné vzory, které můžete znovu použít ve svých aplikacích.</span><span class="sxs-lookup"><span data-stu-id="83640-113">Later, you will get an overview of the DDD techniques that enable you to find common patterns that you can reuse in your applications.</span></span>

<span data-ttu-id="83640-114">DDD je velké téma s bohatou sadou prostředků pro učení.</span><span class="sxs-lookup"><span data-stu-id="83640-114">DDD is a large topic with a rich set of resources for learning.</span></span> <span data-ttu-id="83640-115">Můžete začít s kniha, jako je [návrh založený na doméně](https://domainlanguage.com/ddd/) , pomocí Eric Evans a dalších materiálů od Vaughn Vernon, Jimmy Nilsson, Greg Younga, UDI Dahan, Jimmy Bogard a mnoha dalších expertů na DDD/CQRS.</span><span class="sxs-lookup"><span data-stu-id="83640-115">You can start with books like [Domain-Driven Design](https://domainlanguage.com/ddd/) by Eric Evans and additional materials from Vaughn Vernon, Jimmy Nilsson, Greg Young, Udi Dahan, Jimmy Bogard, and many other DDD/CQRS experts.</span></span> <span data-ttu-id="83640-116">Ale většina z nich se snaží zjistit, jak se v rámci konverzace, tabulování a modelování domén s odborníky v konkrétní obchodní doméně naučíte používat DDD techniky.</span><span class="sxs-lookup"><span data-stu-id="83640-116">But most of all you need to try to learn how to apply DDD techniques from the conversations, whiteboarding, and domain modeling sessions with the experts in your concrete business domain.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="83640-117">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="83640-117">Additional resources</span></span>

##### <a name="ddd-domain-driven-design"></a><span data-ttu-id="83640-118">DDD (návrh založený na doméně)</span><span class="sxs-lookup"><span data-stu-id="83640-118">DDD (Domain-Driven Design)</span></span>

- <span data-ttu-id="83640-119">**Eric Evans. Jazyk domény** </span><span class="sxs-lookup"><span data-stu-id="83640-119">**Eric Evans. Domain Language** </span></span>\
  <https://domainlanguage.com/>

- <span data-ttu-id="83640-120">**Martin Fowlera. Návrh založený na doméně** </span><span class="sxs-lookup"><span data-stu-id="83640-120">**Martin Fowler. Domain-Driven Design** </span></span>\
  <https://martinfowler.com/tags/domain%20driven%20design.html>

- <span data-ttu-id="83640-121">**Jimmy Bogard. Posílení vaší domény: Úvod** </span><span class="sxs-lookup"><span data-stu-id="83640-121">**Jimmy Bogard. Strengthening your domain: a primer** </span></span>\
  <https://lostechies.com/jimmybogard/2010/02/04/strengthening-your-domain-a-primer/>

##### <a name="ddd-books"></a><span data-ttu-id="83640-122">DDD knihy</span><span class="sxs-lookup"><span data-stu-id="83640-122">DDD books</span></span>

- <span data-ttu-id="83640-123">**Eric Evans. Návrh založený na doméně: Řešení složitosti na srdce softwaru** </span><span class="sxs-lookup"><span data-stu-id="83640-123">**Eric Evans. Domain-Driven Design: Tackling Complexity in the Heart of Software** </span></span>\
  <https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/>

- <span data-ttu-id="83640-124">**Eric Evans. Referenční informace k návrhu založenému na doméně: Souhrny definic a vzorů** </span><span class="sxs-lookup"><span data-stu-id="83640-124">**Eric Evans. Domain-Driven Design Reference: Definitions and Pattern Summaries** </span></span>\
  <https://www.amazon.com/Domain-Driven-Design-Reference-Definitions-2014-09-22/dp/B01N8YB4ZO/>

- <span data-ttu-id="83640-125">**Vaughn Vernon. Implementace návrhu založeného na doméně** </span><span class="sxs-lookup"><span data-stu-id="83640-125">**Vaughn Vernon. Implementing Domain-Driven Design** </span></span>\
  <https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/>

- <span data-ttu-id="83640-126">**Vaughn Vernon. Návrh založený na doméně byl stále přetrvává.**  </span><span class="sxs-lookup"><span data-stu-id="83640-126">**Vaughn Vernon. Domain-Driven Design Distilled** </span></span>\
  <https://www.amazon.com/Domain-Driven-Design-Distilled-Vaughn-Vernon/dp/0134434420/>

- <span data-ttu-id="83640-127">**Jimmy Nilsson. Použití návrhu a vzorů založených na doméně** </span><span class="sxs-lookup"><span data-stu-id="83640-127">**Jimmy Nilsson. Applying Domain-Driven Design and Patterns** </span></span>\
  <https://www.amazon.com/Applying-Domain-Driven-Design-Patterns-Examples/dp/0321268202/>

- <span data-ttu-id="83640-128">**Cesar de la Torre. N-vrstvý Průvodce architekturou orientovaný na doménu s .NET** </span><span class="sxs-lookup"><span data-stu-id="83640-128">**Cesar de la Torre. N-Layered Domain-Oriented Architecture Guide with .NET** </span></span>\
  <https://www.amazon.com/N-Layered-Domain-Oriented-Architecture-Guide-NET/dp/8493903612/>

- <span data-ttu-id="83640-129">**Abel Avram a Floyd Marinescu. Rychlé navrhování založené na doméně** </span><span class="sxs-lookup"><span data-stu-id="83640-129">**Abel Avram and Floyd Marinescu. Domain-Driven Design Quickly** </span></span>\
  <https://www.amazon.com/Domain-Driven-Design-Quickly-Abel-Avram/dp/1411609255/>

- <span data-ttu-id="83640-130">**Scott Millett, záměrné ladění – vzory, principy a postupy návrhu založeného na doméně** </span><span class="sxs-lookup"><span data-stu-id="83640-130">**Scott Millett, Nick Tune - Patterns, Principles, and Practices of Domain-Driven Design** </span></span>\
  <http://www.wrox.com/WileyCDA/WroxTitle/Patterns-Principles-and-Practices-of-Domain-Driven-Design.productCd-1118714709.html>

##### <a name="ddd-training"></a><span data-ttu-id="83640-131">DDD školení</span><span class="sxs-lookup"><span data-stu-id="83640-131">DDD training</span></span>

- <span data-ttu-id="83640-132">**Julie Lerman a Steve Smith. Základy návrhu založené na doméně** </span><span class="sxs-lookup"><span data-stu-id="83640-132">**Julie Lerman and Steve Smith. Domain-Driven Design Fundamentals** </span></span>\
  <https://bit.ly/PS-DDD>

>[!div class="step-by-step"]
><span data-ttu-id="83640-133">[Předchozí](../multi-container-microservice-net-applications/implement-api-gateways-with-ocelot.md)Další
>[](apply-simplified-microservice-cqrs-ddd-patterns.md)</span><span class="sxs-lookup"><span data-stu-id="83640-133">[Previous](../multi-container-microservice-net-applications/implement-api-gateways-with-ocelot.md)
[Next](apply-simplified-microservice-cqrs-ddd-patterns.md)</span></span>
