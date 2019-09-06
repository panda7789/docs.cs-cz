---
title: Návrh aplikační vrstvy a webového rozhraní API mikroslužby
description: Architektura mikroslužeb .NET pro kontejnerové aplikace .NET | Stručně zmíněné základní zásady pro návrh vrstvy aplikace.
ms.date: 10/08/2018
ms.openlocfilehash: 3c3b9f74e76e01deafa1f97de5d3250d57716014
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "70296738"
---
# <a name="design-the-microservice-application-layer-and-web-api"></a><span data-ttu-id="53352-103">Návrh aplikační vrstvy a webového rozhraní API mikroslužeb</span><span class="sxs-lookup"><span data-stu-id="53352-103">Design the microservice application layer and Web API</span></span>

## <a name="use-solid-principles-and-dependency-injection"></a><span data-ttu-id="53352-104">Použití pevných principů a injektáže závislostí</span><span class="sxs-lookup"><span data-stu-id="53352-104">Use SOLID principles and Dependency Injection</span></span>

<span data-ttu-id="53352-105">ZÁKLADNÍ zásady představují klíčové techniky pro použití v jakékoli moderní a klíčové aplikaci, jako je například vývoj mikroslužeb se vzory DDD.</span><span class="sxs-lookup"><span data-stu-id="53352-105">SOLID principles are critical techniques to be used in any modern and mission-critical application, such as developing a microservice with DDD patterns.</span></span> <span data-ttu-id="53352-106">SOLID je akronym, který seskupuje pět základních principů:</span><span class="sxs-lookup"><span data-stu-id="53352-106">SOLID is an acronym that groups five fundamental principles:</span></span>

- <span data-ttu-id="53352-107">Princip jedné zodpovědnosti</span><span class="sxs-lookup"><span data-stu-id="53352-107">Single Responsibility principle</span></span>

- <span data-ttu-id="53352-108">Princip otevření/uzavření</span><span class="sxs-lookup"><span data-stu-id="53352-108">Open/closed principle</span></span>

- <span data-ttu-id="53352-109">Liskov – princip nahrazení</span><span class="sxs-lookup"><span data-stu-id="53352-109">Liskov substitution principle</span></span>

- <span data-ttu-id="53352-110">Princip oddělení rozhraní</span><span class="sxs-lookup"><span data-stu-id="53352-110">Interface Segregation principle</span></span>

- <span data-ttu-id="53352-111">Princip inverze závislosti</span><span class="sxs-lookup"><span data-stu-id="53352-111">Dependency Inversion principle</span></span>

<span data-ttu-id="53352-112">SOLID je více informací o návrhu aplikace nebo vnitřních vrstev mikroslužeb a o vzájemných závislostech mezi nimi.</span><span class="sxs-lookup"><span data-stu-id="53352-112">SOLID is more about how you design your application or microservice internal layers and about decoupling dependencies between them.</span></span> <span data-ttu-id="53352-113">Nesouvisí s doménou, ale s technickým návrhem aplikace.</span><span class="sxs-lookup"><span data-stu-id="53352-113">It is not related to the domain, but to the application’s technical design.</span></span> <span data-ttu-id="53352-114">Konečný princip – princip inverze závislostí, umožňuje oddělit vrstvu infrastruktury od zbytku vrstev, což umožňuje lepší oddělit implementaci rozmístěných vrstev.</span><span class="sxs-lookup"><span data-stu-id="53352-114">The final principle, the Dependency Inversion principle, allows you to decouple the infrastructure layer from the rest of the layers, which allows a better decoupled implementation of the DDD layers.</span></span>

<span data-ttu-id="53352-115">Vkládání závislostí (DI) je jeden způsob, jak implementovat princip inverze závislostí.</span><span class="sxs-lookup"><span data-stu-id="53352-115">Dependency Injection (DI) is one way to implement the Dependency Inversion principle.</span></span> <span data-ttu-id="53352-116">Je to způsob, jak dosáhnout volného spojení mezi objekty a jejich závislostmi.</span><span class="sxs-lookup"><span data-stu-id="53352-116">It is a technique for achieving loose coupling between objects and their dependencies.</span></span> <span data-ttu-id="53352-117">Namísto přímého vytváření instancí spolupracovníků nebo použití statických odkazů (to znamená použití New...) objekty, které třída potřebuje k provedení svých akcí, jsou poskytovány třídě (nebo "vložené do") třídy.</span><span class="sxs-lookup"><span data-stu-id="53352-117">Rather than directly instantiating collaborators, or using static references (that is, using new…), the objects that a class needs in order to perform its actions are provided to (or "injected into") the class.</span></span> <span data-ttu-id="53352-118">Nejčastěji třídy budou deklarovat své závislosti prostřednictvím jejich konstruktoru, což jim umožní dodržovat princip explicitní závislosti.</span><span class="sxs-lookup"><span data-stu-id="53352-118">Most often, classes will declare their dependencies via their constructor, allowing them to follow the Explicit Dependencies principle.</span></span> <span data-ttu-id="53352-119">Vkládání závislostí je obvykle založeno na konkrétních kontejnerech inverze ovládacích prvků (IoC).</span><span class="sxs-lookup"><span data-stu-id="53352-119">Dependency Injection is usually based on specific Inversion of Control (IoC) containers.</span></span> <span data-ttu-id="53352-120">ASP.NET Core poskytuje jednoduchý integrovaný kontejner IoC, ale můžete použít i oblíbený IoC kontejner, jako je Autofac nebo Ninject.</span><span class="sxs-lookup"><span data-stu-id="53352-120">ASP.NET Core provides a simple built-in IoC container, but you can also use your favorite IoC container, like Autofac or Ninject.</span></span>

<span data-ttu-id="53352-121">Podle plných principů budou vaše třídy pravděpodobně přirozeně malé, dobře náročné a snadno testované.</span><span class="sxs-lookup"><span data-stu-id="53352-121">By following the SOLID principles, your classes will tend naturally to be small, well-factored, and easily tested.</span></span> <span data-ttu-id="53352-122">Ale jak zjistíte, jestli se do tříd vkládají příliš mnoho závislostí?</span><span class="sxs-lookup"><span data-stu-id="53352-122">But how can you know if too many dependencies are being injected into your classes?</span></span> <span data-ttu-id="53352-123">Použijete-li parametr DI prostřednictvím konstruktoru, bude snadné ho detekovat pouze v případě, že se díváte na počet parametrů vašeho konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="53352-123">If you use DI through the constructor, it will be easy to detect that by just looking at the number of parameters for your constructor.</span></span> <span data-ttu-id="53352-124">Pokud existuje příliš mnoho závislostí, obvykle se jedná o znaménko ( [zápach kódu](https://deviq.com/code-smells/)), že se vaše třída pokouší provést příliš mnoho a je pravděpodobně porušena jedna zásada zodpovědnosti.</span><span class="sxs-lookup"><span data-stu-id="53352-124">If there are too many dependencies, this is generally a sign (a [code smell](https://deviq.com/code-smells/)) that your class is trying to do too much, and is probably violating the Single Responsibility principle.</span></span>

<span data-ttu-id="53352-125">Mělo by to mít další průvodce, aby se podrobně kryl.</span><span class="sxs-lookup"><span data-stu-id="53352-125">It would take another guide to cover SOLID in detail.</span></span> <span data-ttu-id="53352-126">Proto tato příručka vyžaduje, abyste měli jenom minimální znalosti těchto témat.</span><span class="sxs-lookup"><span data-stu-id="53352-126">Therefore, this guide requires you to have only a minimum knowledge of these topics.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="53352-127">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="53352-127">Additional resources</span></span>

- <span data-ttu-id="53352-128">**SOLID Základní principy OOP** </span><span class="sxs-lookup"><span data-stu-id="53352-128">**SOLID: Fundamental OOP Principles** </span></span>\
  <https://deviq.com/solid/>

- <span data-ttu-id="53352-129">**Inverze řídicích kontejnerů a vzor vložení závislostí** </span><span class="sxs-lookup"><span data-stu-id="53352-129">**Inversion of Control Containers and the Dependency Injection pattern** </span></span>\
  <https://martinfowler.com/articles/injection.html>

- <span data-ttu-id="53352-130">**Steve Smith. Nové je připevnit** </span><span class="sxs-lookup"><span data-stu-id="53352-130">**Steve Smith. New is Glue** </span></span>\
  <https://ardalis.com/new-is-glue>

> [!div class="step-by-step"]
> <span data-ttu-id="53352-131">[Předchozí](nosql-database-persistence-infrastructure.md)Další
> [](microservice-application-layer-implementation-web-api.md)</span><span class="sxs-lookup"><span data-stu-id="53352-131">[Previous](nosql-database-persistence-infrastructure.md)
[Next](microservice-application-layer-implementation-web-api.md)</span></span>
