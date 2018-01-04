---
title: "Navrhování mikroslužbu aplikační vrstvu a webového rozhraní API"
description: "Architektura Mikroslužeb .NET pro aplikace .NET Kontejnerizované | Navrhování mikroslužbu aplikační vrstvu a webového rozhraní API"
keywords: "Docker, Mikroslužeb, ASP.NET, kontejneru"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 12/12/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: c166e0286d0769e24a6361037eb6c4694fb821ae
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="designing-the-microservice-application-layer-and-web-api"></a><span data-ttu-id="57501-104">Navrhování mikroslužbu aplikační vrstvu a webového rozhraní API</span><span class="sxs-lookup"><span data-stu-id="57501-104">Designing the microservice application layer and Web API</span></span>

## <a name="using-solid-principles-and-dependency-injection"></a><span data-ttu-id="57501-105">Pomocí plnou principy a vkládání závislostí</span><span class="sxs-lookup"><span data-stu-id="57501-105">Using SOLID principles and Dependency Injection</span></span>

<span data-ttu-id="57501-106">PLNOU zásady jsou kritické techniky, který se má použít v jakékoli moderní a kritické aplikace, třeba vývoj mikroslužbu DDD vzory.</span><span class="sxs-lookup"><span data-stu-id="57501-106">SOLID principles are critical techniques to be used in any modern and mission-critical application, such as developing a microservice with DDD patterns.</span></span> <span data-ttu-id="57501-107">PLNOU je zkratka z této skupiny pět základních zásad:</span><span class="sxs-lookup"><span data-stu-id="57501-107">SOLID is an acronym that groups five fundamental principles:</span></span>

-   <span data-ttu-id="57501-108">Jeden zásady odpovědnosti</span><span class="sxs-lookup"><span data-stu-id="57501-108">Single Responsibility principle</span></span>

-   <span data-ttu-id="57501-109">Princip otevřený nebo zavřený</span><span class="sxs-lookup"><span data-stu-id="57501-109">Open/closed principle</span></span>

-   <span data-ttu-id="57501-110">Zásady Liskov nahrazení</span><span class="sxs-lookup"><span data-stu-id="57501-110">Liskov substitution principle</span></span>

-   <span data-ttu-id="57501-111">Princip inverzi oddělení</span><span class="sxs-lookup"><span data-stu-id="57501-111">Inversion Segregation principle</span></span>

-   <span data-ttu-id="57501-112">Princip inverzi závislostí</span><span class="sxs-lookup"><span data-stu-id="57501-112">Dependency Inversion principle</span></span>

<span data-ttu-id="57501-113">UCELENÝ se více o při navrhování vaší aplikace nebo interní vrstvami mikroslužbu a oddělení závislosti mezi nimi.</span><span class="sxs-lookup"><span data-stu-id="57501-113">SOLID is more about how you design your application or microservice internal layers and about decoupling dependencies between them.</span></span> <span data-ttu-id="57501-114">Nesouvisí se k doméně, ale technického návrhu aplikace.</span><span class="sxs-lookup"><span data-stu-id="57501-114">It is not related to the domain, but to the application’s technical design.</span></span> <span data-ttu-id="57501-115">Poslední Princip Princip závislostí inverzi (DI) umožňuje oddělit vrstvě infrastruktury od zbytku vrstvy, která umožňuje lépe odpojeného implementace DDD vrstev.</span><span class="sxs-lookup"><span data-stu-id="57501-115">The final principle, the Dependency Inversion (DI) principle, allows you to decouple the infrastructure layer from the rest of the layers, which allows a better decoupled implementation of the DDD layers.</span></span>

<span data-ttu-id="57501-116">DI je jedním ze způsobů k provedení zásady inverzi závislostí.</span><span class="sxs-lookup"><span data-stu-id="57501-116">DI is one way to implement the Dependency Inversion principle.</span></span> <span data-ttu-id="57501-117">Jde o techniku k dosažení volné párování mezi objekty a jejich závislosti.</span><span class="sxs-lookup"><span data-stu-id="57501-117">It is a technique for achieving loose coupling between objects and their dependencies.</span></span> <span data-ttu-id="57501-118">Ne přímo vytváření instancí spolupracovníci, nebo pomocí statické odkazy, jsou objekty, které potřebuje třídy za účelem provádění akcí poskytované (nebo "vloženy do") třída.</span><span class="sxs-lookup"><span data-stu-id="57501-118">Rather than directly instantiating collaborators, or using static references, the objects that a class needs in order to perform its actions are provided to (or "injected into") the class.</span></span> <span data-ttu-id="57501-119">Třídy bude nejčastěji deklarovat závislé prostřednictvím jejich konstruktoru, což jim umožní sledovat zásadu explicitní závislosti.</span><span class="sxs-lookup"><span data-stu-id="57501-119">Most often, classes will declare their dependencies via their constructor, allowing them to follow the Explicit Dependencies principle.</span></span> <span data-ttu-id="57501-120">DI většinou podle konkrétní kontejnery v inverzi z ovládacích prvků (IoC).</span><span class="sxs-lookup"><span data-stu-id="57501-120">DI is usually based on specific Inversion of Control (IoC) containers.</span></span> <span data-ttu-id="57501-121">ASP.NET Core poskytuje jednoduché předdefinované kontejner IoC, ale můžete použít také vaše oblíbené kontejner IoC jako Autofac nebo Ninject.</span><span class="sxs-lookup"><span data-stu-id="57501-121">ASP.NET Core provides a simple built-in IoC container, but you can also use your favorite IoC container, like Autofac or Ninject.</span></span>

<span data-ttu-id="57501-122">Pomocí následujících plnou zásady, vaše třídy bude jsou obvykle přirozeně malé, dobře započítané a snadno otestované.</span><span class="sxs-lookup"><span data-stu-id="57501-122">By following the SOLID principles, your classes will tend naturally to be small, well-factored, and easily tested.</span></span> <span data-ttu-id="57501-123">Ale jak můžete vy víte, pokud jsou probíhá příliš velký počet závislostí vloženy do vaší třídy?</span><span class="sxs-lookup"><span data-stu-id="57501-123">But how can you know if too many dependencies are being injected into your classes?</span></span> <span data-ttu-id="57501-124">Pokud používáte DI pomocí konstruktoru, bude možné snadno zjistit, prohlížením právě počet parametrů pro vaše konstruktor.</span><span class="sxs-lookup"><span data-stu-id="57501-124">If you use DI through the constructor, it will be easy to detect that by just looking at the number of parameters for your constructor.</span></span> <span data-ttu-id="57501-125">Pokud jsou moc velký počet závislostí, je obvykle znaménkem ( [code pach](http://deviq.com/code-smells/)), se pokouší o provedení příliš mnoho třídě a pravděpodobně porušuje zásady jeden odpovědnosti.</span><span class="sxs-lookup"><span data-stu-id="57501-125">If there are too many dependencies, this is generally a sign (a [code smell](http://deviq.com/code-smells/)) that your class is trying to do too much, and is probably violating the Single Responsibility principle.</span></span>

<span data-ttu-id="57501-126">To bude trvat jiný průvodce tak, aby pokrývalo UCELENÝ podrobně.</span><span class="sxs-lookup"><span data-stu-id="57501-126">It would take another guide to cover SOLID in detail.</span></span> <span data-ttu-id="57501-127">Tato příručka proto vyžaduje, abyste mají pouze minimální znalosti o těchto tématech.</span><span class="sxs-lookup"><span data-stu-id="57501-127">Therefore, this guide requires you to have only a minimum knowledge of these topics.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="57501-128">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="57501-128">Additional resources</span></span>

-   <span data-ttu-id="57501-129">**UCELENÝ: Principy základní mimoprocesová aplikace VOLÁNA**
    [*http://deviq.com/solid/*](http://deviq.com/solid/%20)</span><span class="sxs-lookup"><span data-stu-id="57501-129">**SOLID: Fundamental OOP Principles**
[*http://deviq.com/solid/*](http://deviq.com/solid/%20)</span></span>

-   <span data-ttu-id="57501-130">**Inverze – kontejnery ovládacích prvků a vkládání závislostí vzor**
    [*https://martinfowler.com/articles/injection.html*](https://martinfowler.com/articles/injection.html)</span><span class="sxs-lookup"><span data-stu-id="57501-130">**Inversion of Control Containers and the Dependency Injection pattern**
[*https://martinfowler.com/articles/injection.html*](https://martinfowler.com/articles/injection.html)</span></span>

-   <span data-ttu-id="57501-131">**Steve Smith. Nové je pojidlem**
    [*http://ardalis.com/new-is-glue*](http://ardalis.com/new-is-glue)</span><span class="sxs-lookup"><span data-stu-id="57501-131">**Steve Smith. New is Glue**
[*http://ardalis.com/new-is-glue*](http://ardalis.com/new-is-glue)</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="57501-132">[Předchozí] (nosql-database trvalost infrastructure.md) [Další] (microservice-application-layer-implementation-web-api.md)</span><span class="sxs-lookup"><span data-stu-id="57501-132">[Previous] (nosql-database-persistence-infrastructure.md) [Next] (microservice-application-layer-implementation-web-api.md)</span></span>
