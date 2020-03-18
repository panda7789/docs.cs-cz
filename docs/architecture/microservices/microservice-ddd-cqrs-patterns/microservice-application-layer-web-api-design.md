---
title: Návrh aplikační vrstvy a webového rozhraní API mikroslužby
description: Architektura mikroslužeb .NET pro kontejnerizované aplikace .NET | Stručná zmínka o principech SOLID pro návrh aplikační vrstvy.
ms.date: 10/08/2018
ms.openlocfilehash: 3c3b9f74e76e01deafa1f97de5d3250d57716014
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "70296738"
---
# <a name="design-the-microservice-application-layer-and-web-api"></a><span data-ttu-id="40668-103">Návrh aplikační vrstvy mikroslužeb a webového rozhraní API</span><span class="sxs-lookup"><span data-stu-id="40668-103">Design the microservice application layer and Web API</span></span>

## <a name="use-solid-principles-and-dependency-injection"></a><span data-ttu-id="40668-104">Použití principů SOLID a vkládání závislostí</span><span class="sxs-lookup"><span data-stu-id="40668-104">Use SOLID principles and Dependency Injection</span></span>

<span data-ttu-id="40668-105">Principy SOLID jsou kritické techniky, které mají být použity v jakékoli moderní a kritické aplikace, jako je například vývoj mikroslužeb se vzory DDD.</span><span class="sxs-lookup"><span data-stu-id="40668-105">SOLID principles are critical techniques to be used in any modern and mission-critical application, such as developing a microservice with DDD patterns.</span></span> <span data-ttu-id="40668-106">SOLID je zkratka, která seskupuje pět základních principů:</span><span class="sxs-lookup"><span data-stu-id="40668-106">SOLID is an acronym that groups five fundamental principles:</span></span>

- <span data-ttu-id="40668-107">Zásada jednotné odpovědnosti</span><span class="sxs-lookup"><span data-stu-id="40668-107">Single Responsibility principle</span></span>

- <span data-ttu-id="40668-108">Otevřený/uzavřený princip</span><span class="sxs-lookup"><span data-stu-id="40668-108">Open/closed principle</span></span>

- <span data-ttu-id="40668-109">Liskovův substituční princip</span><span class="sxs-lookup"><span data-stu-id="40668-109">Liskov substitution principle</span></span>

- <span data-ttu-id="40668-110">Princip segregace rozhraní</span><span class="sxs-lookup"><span data-stu-id="40668-110">Interface Segregation principle</span></span>

- <span data-ttu-id="40668-111">Princip inverze závislostí</span><span class="sxs-lookup"><span data-stu-id="40668-111">Dependency Inversion principle</span></span>

<span data-ttu-id="40668-112">SOLID je více o tom, jak navrhnout vnitřní vrstvy aplikace nebo mikroslužeb a o oddělení závislostí mezi nimi.</span><span class="sxs-lookup"><span data-stu-id="40668-112">SOLID is more about how you design your application or microservice internal layers and about decoupling dependencies between them.</span></span> <span data-ttu-id="40668-113">Nesouvisí s doménou, ale s technickým návrhem aplikace.</span><span class="sxs-lookup"><span data-stu-id="40668-113">It is not related to the domain, but to the application’s technical design.</span></span> <span data-ttu-id="40668-114">Konečný princip, princip inverze závislostí, umožňuje oddělit vrstvu infrastruktury od ostatních vrstev, což umožňuje lepší oddělenou implementaci vrstev DDD.</span><span class="sxs-lookup"><span data-stu-id="40668-114">The final principle, the Dependency Inversion principle, allows you to decouple the infrastructure layer from the rest of the layers, which allows a better decoupled implementation of the DDD layers.</span></span>

<span data-ttu-id="40668-115">Vkládání závislostí (DI) je jedním ze způsobů, jak implementovat princip inverze závislostí.</span><span class="sxs-lookup"><span data-stu-id="40668-115">Dependency Injection (DI) is one way to implement the Dependency Inversion principle.</span></span> <span data-ttu-id="40668-116">Jedná se o techniku pro dosažení volné párování mezi objekty a jejich závislosti.</span><span class="sxs-lookup"><span data-stu-id="40668-116">It is a technique for achieving loose coupling between objects and their dependencies.</span></span> <span data-ttu-id="40668-117">Spíše než přímo vytváření konkretizovat spolupracovníky nebo pomocí statických odkazů (to znamená pomocí new...), objekty, které třída potřebuje k provedení své akce jsou k dispozici (nebo "vstřikuje do" třídy.</span><span class="sxs-lookup"><span data-stu-id="40668-117">Rather than directly instantiating collaborators, or using static references (that is, using new…), the objects that a class needs in order to perform its actions are provided to (or "injected into") the class.</span></span> <span data-ttu-id="40668-118">Nejčastěji třídy deklarují své závislosti prostřednictvím svého konstruktoru, což jim umožňuje dodržovat zásadu explicitní závislosti.</span><span class="sxs-lookup"><span data-stu-id="40668-118">Most often, classes will declare their dependencies via their constructor, allowing them to follow the Explicit Dependencies principle.</span></span> <span data-ttu-id="40668-119">Vkládání závislostí je obvykle založena na konkrétní inverze řídicí (IoC) kontejnery.</span><span class="sxs-lookup"><span data-stu-id="40668-119">Dependency Injection is usually based on specific Inversion of Control (IoC) containers.</span></span> <span data-ttu-id="40668-120">ASP.NET Core poskytuje jednoduchý vestavěný kontejner IoC, ale můžete také použít svůj oblíbený kontejner IoC, jako je Autofac nebo Ninject.</span><span class="sxs-lookup"><span data-stu-id="40668-120">ASP.NET Core provides a simple built-in IoC container, but you can also use your favorite IoC container, like Autofac or Ninject.</span></span>

<span data-ttu-id="40668-121">Dodržováním zásad SOLID budou vaše třídy přirozeně malé, dobře zapracované a snadno testovatelné.</span><span class="sxs-lookup"><span data-stu-id="40668-121">By following the SOLID principles, your classes will tend naturally to be small, well-factored, and easily tested.</span></span> <span data-ttu-id="40668-122">Ale jak můžete vědět, zda příliš mnoho závislostí jsou vstřikovány do vašich tříd?</span><span class="sxs-lookup"><span data-stu-id="40668-122">But how can you know if too many dependencies are being injected into your classes?</span></span> <span data-ttu-id="40668-123">Pokud používáte DI prostřednictvím konstruktoru, bude snadné zjistit, že pouhým pohledem na počet parametrů pro konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="40668-123">If you use DI through the constructor, it will be easy to detect that by just looking at the number of parameters for your constructor.</span></span> <span data-ttu-id="40668-124">Pokud existuje příliš mnoho závislostí, je to obecně znaménko [(zápach kódu),](https://deviq.com/code-smells/)že vaše třída se snaží udělat příliš mnoho a pravděpodobně porušuje zásadu jedné odpovědnosti.</span><span class="sxs-lookup"><span data-stu-id="40668-124">If there are too many dependencies, this is generally a sign (a [code smell](https://deviq.com/code-smells/)) that your class is trying to do too much, and is probably violating the Single Responsibility principle.</span></span>

<span data-ttu-id="40668-125">To by trvalo další průvodce na pokrytí SOLID v detailu.</span><span class="sxs-lookup"><span data-stu-id="40668-125">It would take another guide to cover SOLID in detail.</span></span> <span data-ttu-id="40668-126">Proto tato příručka vyžaduje, abyste měli pouze minimální znalosti o těchto tématech.</span><span class="sxs-lookup"><span data-stu-id="40668-126">Therefore, this guide requires you to have only a minimum knowledge of these topics.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="40668-127">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="40668-127">Additional resources</span></span>

- <span data-ttu-id="40668-128">**SOLID: Základní principy OOP** </span><span class="sxs-lookup"><span data-stu-id="40668-128">**SOLID: Fundamental OOP Principles** </span></span>\
  <https://deviq.com/solid/>

- <span data-ttu-id="40668-129">**Inverze řídicích kontejnerů a vzor vkládání závislostí** </span><span class="sxs-lookup"><span data-stu-id="40668-129">**Inversion of Control Containers and the Dependency Injection pattern** </span></span>\
  <https://martinfowler.com/articles/injection.html>

- <span data-ttu-id="40668-130">**Steva Smithe. Novinou je lepidlo** </span><span class="sxs-lookup"><span data-stu-id="40668-130">**Steve Smith. New is Glue** </span></span>\
  <https://ardalis.com/new-is-glue>

> [!div class="step-by-step"]
> <span data-ttu-id="40668-131">[Předchozí](nosql-database-persistence-infrastructure.md)
> [další](microservice-application-layer-implementation-web-api.md)</span><span class="sxs-lookup"><span data-stu-id="40668-131">[Previous](nosql-database-persistence-infrastructure.md)
[Next](microservice-application-layer-implementation-web-api.md)</span></span>
