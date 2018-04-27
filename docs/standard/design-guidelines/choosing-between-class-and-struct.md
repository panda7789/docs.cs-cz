---
title: Volba mezi třídy a struktury
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- class library design guidelines [.NET Framework], structures
- class library design guidelines [.NET Framework], classes
- structures [.NET Framework], vs. classes
- classes [.NET Framework], design guidelines
- type design guidelines, structures
- structures [.NET Framework], design guidelines
- classes [.NET Framework], vs. structures
- type design guidelines, classes
ms.assetid: f8b8ec9b-0ba7-4dea-aadf-a93395cd804f
caps.latest.revision: 11
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: d7b7a0b290b97966894b9fa7d3b5597e68037cb0
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2018
---
# <a name="choosing-between-class-and-struct"></a><span data-ttu-id="7c6e1-102">Volba mezi třídy a struktury</span><span class="sxs-lookup"><span data-stu-id="7c6e1-102">Choosing Between Class and Struct</span></span>
<span data-ttu-id="7c6e1-103">Jeden základní rozhodnutí o návrhu, které každý framework Návrhář otočená je ohledně návrhu typu třídy (typu odkazu.) nebo jako struktury (typ hodnoty).</span><span class="sxs-lookup"><span data-stu-id="7c6e1-103">One of the basic design decisions every framework designer faces is whether to design a type as a class (a reference type) or as a struct (a value type).</span></span> <span data-ttu-id="7c6e1-104">Dobrou znalost jazyka rozdíly v chování odkazové typy a typy hodnot je velmi důležité při vytvoření tato volba.</span><span class="sxs-lookup"><span data-stu-id="7c6e1-104">Good understanding of the differences in the behavior of reference types and value types is crucial in making this choice.</span></span>  
  
 <span data-ttu-id="7c6e1-105">První nesouhlasí odkazové typy a typy hodnot, které jsme zvažovat je, že odkazové typy jsou přidělené v haldě a uklizeny, zatímco typy hodnot, které jsou přiděleny buď v zásobníku nebo vložené v obsahující typy a kdy navrácena zásobníku unwinds nebo při jejich obsahující typ získá navrácena.</span><span class="sxs-lookup"><span data-stu-id="7c6e1-105">The first difference between reference types and value types we will consider is that reference types are allocated on the heap and garbage-collected, whereas value types are allocated either on the stack or inline in containing types and deallocated when the stack unwinds or when their containing type gets deallocated.</span></span> <span data-ttu-id="7c6e1-106">Přidělování a navrácení typů hodnot, proto jsou v obecné levnějších než přidělování a navrácení odkazové typy.</span><span class="sxs-lookup"><span data-stu-id="7c6e1-106">Therefore, allocations and deallocations of value types are in general cheaper than allocations and deallocations of reference types.</span></span>  
  
 <span data-ttu-id="7c6e1-107">V dalším kroku pole odkaz, který typy jsou přidělené se na řádku, což znamená pole, které jsou elementy jenom odkazy k instancím typu odkazu, který je umístěný v haldě.</span><span class="sxs-lookup"><span data-stu-id="7c6e1-107">Next, arrays of reference types are allocated out-of-line, meaning the array elements are just references to instances of the reference type residing on the heap.</span></span> <span data-ttu-id="7c6e1-108">Hodnota typu pole jsou přiděleny vložené, což znamená, že elementy pole jsou instance skutečný typ hodnoty.</span><span class="sxs-lookup"><span data-stu-id="7c6e1-108">Value type arrays are allocated inline, meaning that the array elements are the actual instances of the value type.</span></span> <span data-ttu-id="7c6e1-109">Přidělování a navrácení hodnota typu pole jsou proto výrazně levnější než přidělování a navrácení odkaz na typ pole.</span><span class="sxs-lookup"><span data-stu-id="7c6e1-109">Therefore, allocations and deallocations of value type arrays are much cheaper than allocations and deallocations of reference type arrays.</span></span> <span data-ttu-id="7c6e1-110">Kromě toho ve většině případů hodnota typu pole vykazovat mnohem lepší polohu odkazu.</span><span class="sxs-lookup"><span data-stu-id="7c6e1-110">In addition, in a majority of cases value type arrays exhibit much better locality of reference.</span></span>  
  
 <span data-ttu-id="7c6e1-111">Další rozdíl se týká využití paměti.</span><span class="sxs-lookup"><span data-stu-id="7c6e1-111">The next difference is related to memory usage.</span></span> <span data-ttu-id="7c6e1-112">Typy hodnot získat do pole, když přetypovat na typ odkazu nebo jednomu z rozhraní, která implementují.</span><span class="sxs-lookup"><span data-stu-id="7c6e1-112">Value types get boxed when cast to a reference type or one of the interfaces they implement.</span></span> <span data-ttu-id="7c6e1-113">Získají nezabalený při převést zpět na typ hodnoty.</span><span class="sxs-lookup"><span data-stu-id="7c6e1-113">They get unboxed when cast back to the value type.</span></span> <span data-ttu-id="7c6e1-114">Protože polí jsou objekty, které mají při přidělování v haldě a uvolňování paměti, příliš mnoho zabalení a rozbalení může mít negativní dopad na haldě, bude systém uvolňování a nakonec i výkon aplikace.</span><span class="sxs-lookup"><span data-stu-id="7c6e1-114">Because boxes are objects that are allocated on the heap and are garbage-collected, too much boxing and unboxing can have a negative impact on the heap, the garbage collector, and ultimately the performance of the application.</span></span>  <span data-ttu-id="7c6e1-115">Naproti tomu žádný takový zabalení nastane jako odkazové typy jsou přetypování.</span><span class="sxs-lookup"><span data-stu-id="7c6e1-115">In contrast, no such boxing occurs as reference types are cast.</span></span>  
  
 <span data-ttu-id="7c6e1-116">Odkaz na typ přiřazení zkopírujte odkaz, zatímco hodnota typu přiřazení zkopírujte celou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="7c6e1-116">Next, reference type assignments copy the reference, whereas value type assignments copy the entire value.</span></span> <span data-ttu-id="7c6e1-117">Přiřazení velké referenční typy jsou proto levnějších než přiřazení typů velkých hodnot.</span><span class="sxs-lookup"><span data-stu-id="7c6e1-117">Therefore, assignments of large reference types are cheaper than assignments of large value types.</span></span>  
  
 <span data-ttu-id="7c6e1-118">Nakonec odkazové typy jsou předávány odkazem, zatímco typů hodnot se předávají podle hodnoty.</span><span class="sxs-lookup"><span data-stu-id="7c6e1-118">Finally, reference types are passed by reference, whereas value types are passed by value.</span></span> <span data-ttu-id="7c6e1-119">Změny instance typu odkaz ovlivní všechny odkazy na instanci.</span><span class="sxs-lookup"><span data-stu-id="7c6e1-119">Changes to an instance of a reference type affect all references pointing to the instance.</span></span> <span data-ttu-id="7c6e1-120">Instance typu hodnota se zkopírují, pokud je předaná hodnota.</span><span class="sxs-lookup"><span data-stu-id="7c6e1-120">Value type instances are copied when they are passed by value.</span></span> <span data-ttu-id="7c6e1-121">Při změně instanci typu hodnoty samozřejmě neovlivňuje žádné jeho kopie.</span><span class="sxs-lookup"><span data-stu-id="7c6e1-121">When an instance of a value type is changed, it of course does not affect any of its copies.</span></span> <span data-ttu-id="7c6e1-122">Protože kopie nejsou explicitně vytvořený uživatelem, ale implicitně vytvářejí, když se předávají argumentů nebo návratové hodnoty jsou vráceny, může být matoucí pro mnoho uživatelů typy hodnot, které mohou být změněny.</span><span class="sxs-lookup"><span data-stu-id="7c6e1-122">Because the copies are not created explicitly by the user but are implicitly created when arguments are passed or return values are returned, value types that can be changed can be confusing to many users.</span></span> <span data-ttu-id="7c6e1-123">Typy hodnot, proto by měl být neměnitelný.</span><span class="sxs-lookup"><span data-stu-id="7c6e1-123">Therefore, value types should be immutable.</span></span>  
  
 <span data-ttu-id="7c6e1-124">Existuje pravidlo musí být většinu typů v rámci třídy.</span><span class="sxs-lookup"><span data-stu-id="7c6e1-124">As a rule of thumb, the majority of types in a framework should be classes.</span></span> <span data-ttu-id="7c6e1-125">Existují však některé situace, ve kterých charakteristiky typ hodnoty Ujistěte se, je vhodnější použít struktury.</span><span class="sxs-lookup"><span data-stu-id="7c6e1-125">There are, however, some situations in which the characteristics of a value type make it more appropriate to use structs.</span></span>  
  
 <span data-ttu-id="7c6e1-126">**✓ ZVAŽTE** definice struktury místo třídu, pokud instance typu jsou malé a běžně krátkodobou nebo jsou běžně součástí jiné objekty.</span><span class="sxs-lookup"><span data-stu-id="7c6e1-126">**✓ CONSIDER** defining a struct instead of a class if instances of the type are small and commonly short-lived or are commonly embedded in other objects.</span></span>  
  
 <span data-ttu-id="7c6e1-127">**X nepoužívejte** definice struktury, pokud má tento typ všechny následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="7c6e1-127">**X AVOID** defining a struct unless the type has all of the following characteristics:</span></span>  
  
-   <span data-ttu-id="7c6e1-128">Logicky reprezentuje jednu hodnotu, podobně jako primitivní typy (`int`, `double`atd.).</span><span class="sxs-lookup"><span data-stu-id="7c6e1-128">It logically represents a single value, similar to primitive types (`int`, `double`, etc.).</span></span>  
  
-   <span data-ttu-id="7c6e1-129">Ho má velikost instance v části 16 bajtů.</span><span class="sxs-lookup"><span data-stu-id="7c6e1-129">It has an instance size under 16 bytes.</span></span>  
  
-   <span data-ttu-id="7c6e1-130">Se nedá změnit.</span><span class="sxs-lookup"><span data-stu-id="7c6e1-130">It is immutable.</span></span>  
  
-   <span data-ttu-id="7c6e1-131">Nebude mít často zabaleny.</span><span class="sxs-lookup"><span data-stu-id="7c6e1-131">It will not have to be boxed frequently.</span></span>  
  
 <span data-ttu-id="7c6e1-132">Ve všech ostatních případech byste měli definovat vaše typy jako třídy.</span><span class="sxs-lookup"><span data-stu-id="7c6e1-132">In all other cases, you should define your types as classes.</span></span>  
  
 <span data-ttu-id="7c6e1-133">*Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*</span><span class="sxs-lookup"><span data-stu-id="7c6e1-133">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="7c6e1-134">*Provedení podle oprávnění Pearson Education, Inc. z [pokynů pro návrh Framework: konvence, Idioms a vzory pro jedno použití knihovny .NET, 2. vydání](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Abrams Brada publikovaná 22 Oct 2008 pomocí Designing Effective jako součást vývoj řady Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="7c6e1-134">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c6e1-135">Viz také</span><span class="sxs-lookup"><span data-stu-id="7c6e1-135">See Also</span></span>  
 [<span data-ttu-id="7c6e1-136">Pokyny k návrhu typu</span><span class="sxs-lookup"><span data-stu-id="7c6e1-136">Type Design Guidelines</span></span>](../../../docs/standard/design-guidelines/type.md)  
 [<span data-ttu-id="7c6e1-137">Pokyny k návrhu architektury</span><span class="sxs-lookup"><span data-stu-id="7c6e1-137">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
