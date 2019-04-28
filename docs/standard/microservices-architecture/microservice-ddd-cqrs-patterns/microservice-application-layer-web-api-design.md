---
title: Návrh aplikační vrstvy a webového rozhraní API mikroslužby
description: Architektura Mikroslužeb .NET pro Kontejnerizované aplikace .NET | Stručný zmínka SOLID principů návrhu aplikační vrstvu.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/08/2018
ms.openlocfilehash: 9177ac9a79afaea01f0ec21b0a64bad5a94e9966
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61760893"
---
# <a name="design-the-microservice-application-layer-and-web-api"></a><span data-ttu-id="5cfe0-103">Návrh aplikační vrstvy mikroslužby a webové rozhraní API</span><span class="sxs-lookup"><span data-stu-id="5cfe0-103">Design the microservice application layer and Web API</span></span>

## <a name="use-solid-principles-and-dependency-injection"></a><span data-ttu-id="5cfe0-104">Použijte zásady PEVNÉ a injektáž závislostí</span><span class="sxs-lookup"><span data-stu-id="5cfe0-104">Use SOLID principles and Dependency Injection</span></span>

<span data-ttu-id="5cfe0-105">PLNÉ zásady jsou kritické technik, který se má použít v jakékoli moderní i klíčové podnikové aplikace, třeba vývoj mikroslužbě pomocí vzorů DDD.</span><span class="sxs-lookup"><span data-stu-id="5cfe0-105">SOLID principles are critical techniques to be used in any modern and mission-critical application, such as developing a microservice with DDD patterns.</span></span> <span data-ttu-id="5cfe0-106">PLNÉ je zkratka této skupiny pěti základními zásadami:</span><span class="sxs-lookup"><span data-stu-id="5cfe0-106">SOLID is an acronym that groups five fundamental principles:</span></span>

- <span data-ttu-id="5cfe0-107">Jednotné zásady odpovědnosti</span><span class="sxs-lookup"><span data-stu-id="5cfe0-107">Single Responsibility principle</span></span>

- <span data-ttu-id="5cfe0-108">Princip otevřený/uzavřený</span><span class="sxs-lookup"><span data-stu-id="5cfe0-108">Open/closed principle</span></span>

- <span data-ttu-id="5cfe0-109">Zásady Liskov nahrazení</span><span class="sxs-lookup"><span data-stu-id="5cfe0-109">Liskov substitution principle</span></span>

- <span data-ttu-id="5cfe0-110">Princip oddělení rozhraní</span><span class="sxs-lookup"><span data-stu-id="5cfe0-110">Interface Segregation principle</span></span>

- <span data-ttu-id="5cfe0-111">Princip inverzi závislostí</span><span class="sxs-lookup"><span data-stu-id="5cfe0-111">Dependency Inversion principle</span></span>

<span data-ttu-id="5cfe0-112">Více o způsob návrhu aplikace nebo interní vrstvy mikroslužby a oddělení závislosti mezi nimi je PLNÝ.</span><span class="sxs-lookup"><span data-stu-id="5cfe0-112">SOLID is more about how you design your application or microservice internal layers and about decoupling dependencies between them.</span></span> <span data-ttu-id="5cfe0-113">To není v relaci k doméně, ale technického návrhu vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="5cfe0-113">It is not related to the domain, but to the application’s technical design.</span></span> <span data-ttu-id="5cfe0-114">Principu poslední principu inverzi závislost umožňuje oddělit vrstvě infrastruktury od zbytku vrstvy, která umožňuje lépe samostatné implementace DDD vrstev.</span><span class="sxs-lookup"><span data-stu-id="5cfe0-114">The final principle, the Dependency Inversion principle, allows you to decouple the infrastructure layer from the rest of the layers, which allows a better decoupled implementation of the DDD layers.</span></span>

<span data-ttu-id="5cfe0-115">Dependency Injection (DI) je jedním ze způsobů implementace principu závislost inverzi.</span><span class="sxs-lookup"><span data-stu-id="5cfe0-115">Dependency Injection (DI) is one way to implement the Dependency Inversion principle.</span></span> <span data-ttu-id="5cfe0-116">Jde o techniku pro dosažení volné párování mezi objekty a jejich závislosti.</span><span class="sxs-lookup"><span data-stu-id="5cfe0-116">It is a technique for achieving loose coupling between objects and their dependencies.</span></span> <span data-ttu-id="5cfe0-117">Místo přímo vytvoření instance spolupracovníci, nebo pomocí statických odkazů (které je, pomocí nové...), jsou objekty, které třída potřebuje, aby jeho činnostem poskytnuté (nebo "vloženy do") třídy.</span><span class="sxs-lookup"><span data-stu-id="5cfe0-117">Rather than directly instantiating collaborators, or using static references (that is, using new…), the objects that a class needs in order to perform its actions are provided to (or "injected into") the class.</span></span> <span data-ttu-id="5cfe0-118">Nejčastěji se třídy deklarují svoje závislosti přes jejich konstruktoru, což jim umožní postupovat podle principu explicitní závislosti.</span><span class="sxs-lookup"><span data-stu-id="5cfe0-118">Most often, classes will declare their dependencies via their constructor, allowing them to follow the Explicit Dependencies principle.</span></span> <span data-ttu-id="5cfe0-119">Injektáž závislostí je obvykle založena na konkrétní kontejnery řízení IOC (Inversion).</span><span class="sxs-lookup"><span data-stu-id="5cfe0-119">Dependency Injection is usually based on specific Inversion of Control (IoC) containers.</span></span> <span data-ttu-id="5cfe0-120">ASP.NET Core nabízí jednoduchý kontejner IoC integrované, ale můžete použít také oblíbené kontejner IoC, třeba Autofac nebo Ninject.</span><span class="sxs-lookup"><span data-stu-id="5cfe0-120">ASP.NET Core provides a simple built-in IoC container, but you can also use your favorite IoC container, like Autofac or Ninject.</span></span>

<span data-ttu-id="5cfe0-121">Pomocí následujících SOLID zásady, tříd bodech přirozeně malé, skvěle a snadno otestované.</span><span class="sxs-lookup"><span data-stu-id="5cfe0-121">By following the SOLID principles, your classes will tend naturally to be small, well-factored, and easily tested.</span></span> <span data-ttu-id="5cfe0-122">Ale jak můžete víte, pokud příliš velký počet závislostí se vloží do vašich tříd?</span><span class="sxs-lookup"><span data-stu-id="5cfe0-122">But how can you know if too many dependencies are being injected into your classes?</span></span> <span data-ttu-id="5cfe0-123">Pokud používáte DI pomocí konstruktoru, bude snadno zjistit, který jen pohlédnutím na počet parametrů pro váš konstruktor.</span><span class="sxs-lookup"><span data-stu-id="5cfe0-123">If you use DI through the constructor, it will be easy to detect that by just looking at the number of parameters for your constructor.</span></span> <span data-ttu-id="5cfe0-124">Pokud je příliš velký počet závislostí, je obvykle znak ( [kódu pach](https://deviq.com/code-smells/)), že se snaží docílit příliš mnoho vaší třídy a pravděpodobně porušuje Princip jednotnou zodpovědnost.</span><span class="sxs-lookup"><span data-stu-id="5cfe0-124">If there are too many dependencies, this is generally a sign (a [code smell](https://deviq.com/code-smells/)) that your class is trying to do too much, and is probably violating the Single Responsibility principle.</span></span>

<span data-ttu-id="5cfe0-125">By to obnášelo jiného průvodce k podrobně zahrnovat PLNÝ.</span><span class="sxs-lookup"><span data-stu-id="5cfe0-125">It would take another guide to cover SOLID in detail.</span></span> <span data-ttu-id="5cfe0-126">Proto tato příručka vyžaduje, abyste nemají pouze minimální informace o těchto tématech.</span><span class="sxs-lookup"><span data-stu-id="5cfe0-126">Therefore, this guide requires you to have only a minimum knowledge of these topics.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="5cfe0-127">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="5cfe0-127">Additional resources</span></span>

- <span data-ttu-id="5cfe0-128">**PLNÁ: Základní OOP zásady** \\</span><span class="sxs-lookup"><span data-stu-id="5cfe0-128">**SOLID: Fundamental OOP Principles** \\</span></span>
  <https://deviq.com/solid/>

- <span data-ttu-id="5cfe0-129">**Inverze – kontejnery ovládacích prvků a vzor injektáž závislostí** \\</span><span class="sxs-lookup"><span data-stu-id="5cfe0-129">**Inversion of Control Containers and the Dependency Injection pattern** \\</span></span>
  <https://martinfowler.com/articles/injection.html>

- <span data-ttu-id="5cfe0-130">**Steve Smith. Je nový spojovací** \\</span><span class="sxs-lookup"><span data-stu-id="5cfe0-130">**Steve Smith. New is Glue** \\</span></span>
  <https://ardalis.com/new-is-glue>

> [!div class="step-by-step"]
> <span data-ttu-id="5cfe0-131">[Předchozí](nosql-database-persistence-infrastructure.md)
> [další](microservice-application-layer-implementation-web-api.md)</span><span class="sxs-lookup"><span data-stu-id="5cfe0-131">[Previous](nosql-database-persistence-infrastructure.md)
[Next](microservice-application-layer-implementation-web-api.md)</span></span>
