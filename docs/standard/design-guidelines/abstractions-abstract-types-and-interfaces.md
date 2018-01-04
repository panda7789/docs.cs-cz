---
title: "Abstrakce (abstraktní typy a rozhraní)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- interfaces [.NET Framework], abstract
- abstract interfaces [.NET Framework]
- abstract types [.NET Framework]
- types [.NET Framework], abstract
ms.assetid: 0a632bc7-9b03-44ee-8842-c82f88672a45
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 276c5883487d8fba47d7fb80060d4c947e0f6cd6
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="abstractions-abstract-types-and-interfaces"></a><span data-ttu-id="129c7-102">Abstrakce (abstraktní typy a rozhraní)</span><span class="sxs-lookup"><span data-stu-id="129c7-102">Abstractions (Abstract Types and Interfaces)</span></span>
<span data-ttu-id="129c7-103">Abstrakci je typ, který popisuje kontraktu, ale neposkytuje úplnou implementaci kontraktu.</span><span class="sxs-lookup"><span data-stu-id="129c7-103">An abstraction is a type that describes a contract but does not provide a full implementation of the contract.</span></span> <span data-ttu-id="129c7-104">Abstrakce jsou obvykle implementovány jako abstraktní třídy nebo rozhraní a začne s dobře definované sadě referenční dokumentaci k nástroji popisující požadované sémantika typy implementace kontraktu.</span><span class="sxs-lookup"><span data-stu-id="129c7-104">Abstractions are usually implemented as abstract classes or interfaces, and they come with a well-defined set of reference documentation describing the required semantics of the types implementing the contract.</span></span> <span data-ttu-id="129c7-105">Mezi nejdůležitější abstrakce v rozhraní .NET Framework patří <xref:System.IO.Stream>, <xref:System.Collections.Generic.IEnumerable%601>, a <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="129c7-105">Some of the most important abstractions in the .NET Framework include <xref:System.IO.Stream>, <xref:System.Collections.Generic.IEnumerable%601>, and <xref:System.Object>.</span></span>  
  
 <span data-ttu-id="129c7-106">Rozhraní můžete rozšířit pomocí implementace konkrétní typ, který podporuje kontrakt abstrakci a pomocí tohoto konkrétního typu framework rozhraní API náročné (pracující na) odběru.</span><span class="sxs-lookup"><span data-stu-id="129c7-106">You can extend frameworks by implementing a concrete type that supports the contract of an abstraction and using this concrete type with framework APIs consuming (operating on) the abstraction.</span></span>  
  
 <span data-ttu-id="129c7-107">Smysluplný a užitečné abstrakce, který se bude moct odolat test čas je velmi obtížné návrhu.</span><span class="sxs-lookup"><span data-stu-id="129c7-107">A meaningful and useful abstraction that is able to withstand the test of time is very difficult to design.</span></span> <span data-ttu-id="129c7-108">Potíže hlavní dochází správnou sadu žádné další a ne méně členů.</span><span class="sxs-lookup"><span data-stu-id="129c7-108">The main difficulty is getting the right set of members, no more and no fewer.</span></span> <span data-ttu-id="129c7-109">Pokud abstrakci má příliš mnoho členů, bude obtížné nebo dokonce možné implementovat.</span><span class="sxs-lookup"><span data-stu-id="129c7-109">If an abstraction has too many members, it becomes difficult or even impossible to implement.</span></span> <span data-ttu-id="129c7-110">Pokud má příliš málo členy pro funkci přislíbeném, stane nemá zajímavými způsoby.</span><span class="sxs-lookup"><span data-stu-id="129c7-110">If it has too few members for the promised functionality, it becomes useless in many interesting scenarios.</span></span>  
  
 <span data-ttu-id="129c7-111">Příliš mnoho abstrakce v rozhraní také negativně ovlivnit použitelnost rozhraní.</span><span class="sxs-lookup"><span data-stu-id="129c7-111">Too many abstractions in a framework also negatively affect usability of the framework.</span></span> <span data-ttu-id="129c7-112">Často je velmi obtížné porozumět abstrakci bez pochopení, jak zapadá do větší přehled o konkrétní implementace a rozhraní API pracující na odběru.</span><span class="sxs-lookup"><span data-stu-id="129c7-112">It is often quite difficult to understand an abstraction without understanding how it fits into the larger picture of the concrete implementations and the APIs operating on the abstraction.</span></span> <span data-ttu-id="129c7-113">Názvy abstrakce a jejich členové jsou také nutně abstraktní, často vede jako nesrozumitelné a unapproachable první neměňte širší kontextu jejich využití.</span><span class="sxs-lookup"><span data-stu-id="129c7-113">Also, names of abstractions and their members are necessarily abstract, which often makes them cryptic and unapproachable without first understanding the broader context of their usage.</span></span>  
  
 <span data-ttu-id="129c7-114">Abstrakce však poskytují velmi výkonné rozšíření, což často nemůže shodovat na rozšiřitelnost mechanismy.</span><span class="sxs-lookup"><span data-stu-id="129c7-114">However, abstractions provide extremely powerful extensibility that the other extensibility mechanisms cannot often match.</span></span> <span data-ttu-id="129c7-115">Jsou jádrem mnoho architektury vzory, třeba moduly plug-in inverzi řízení (IoC), kanálů a tak dále.</span><span class="sxs-lookup"><span data-stu-id="129c7-115">They are at the core of many architectural patterns, such as plug-ins, inversion of control (IoC), pipelines, and so on.</span></span> <span data-ttu-id="129c7-116">Jsou také velmi důležité pro testovatelnosti architektury.</span><span class="sxs-lookup"><span data-stu-id="129c7-116">They are also extremely important for testability of frameworks.</span></span> <span data-ttu-id="129c7-117">Dobrý abstrakce umožňují se zakázaným inzerováním out velkou závislosti pro účely testování jednotek.</span><span class="sxs-lookup"><span data-stu-id="129c7-117">Good abstractions make it possible to stub out heavy dependencies for the purpose of unit testing.</span></span> <span data-ttu-id="129c7-118">V souhrnu jsou zodpovědní za sought-after bohatost moderní architektury objektově orientované abstrakce.</span><span class="sxs-lookup"><span data-stu-id="129c7-118">In summary, abstractions are responsible for the sought-after richness of the modern object-oriented frameworks.</span></span>  
  
 <span data-ttu-id="129c7-119">**X nesmí** zadejte abstrakce, pokud jsou neotestovali ve vývoji několik rozhraní API využívání abstrakce a konkrétní implementace.</span><span class="sxs-lookup"><span data-stu-id="129c7-119">**X DO NOT** provide abstractions unless they are tested by developing several concrete implementations and APIs consuming the abstractions.</span></span>  
  
 <span data-ttu-id="129c7-120">**PROVEĎTE ✓** zvolit pečlivě abstraktní třídy a rozhraní při navrhování abstrakci.</span><span class="sxs-lookup"><span data-stu-id="129c7-120">**✓ DO** choose carefully between an abstract class and an interface when designing an abstraction.</span></span>  
  
 <span data-ttu-id="129c7-121">**✓ ZVAŽTE** poskytuje odkaz testy pro konkrétní implementace abstrakce.</span><span class="sxs-lookup"><span data-stu-id="129c7-121">**✓ CONSIDER** providing reference tests for concrete implementations of abstractions.</span></span> <span data-ttu-id="129c7-122">Tyto testy by měl povolit uživatelům otestovat, zda jejich implementace správně implementaci kontraktu.</span><span class="sxs-lookup"><span data-stu-id="129c7-122">Such tests should allow users to test whether their implementations correctly implement the contract.</span></span>  
  
 <span data-ttu-id="129c7-123">*Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*</span><span class="sxs-lookup"><span data-stu-id="129c7-123">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="129c7-124">*Provedení podle oprávnění Pearson Education, Inc. z [pokynů pro návrh Framework: konvence, Idioms a vzory pro jedno použití knihovny .NET, 2. vydání](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Abrams Brada publikovaná 22 Oct 2008 pomocí Designing Effective jako součást vývoj řady Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="129c7-124">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="129c7-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="129c7-125">See Also</span></span>  
 [<span data-ttu-id="129c7-126">Pokyny k návrhu architektury</span><span class="sxs-lookup"><span data-stu-id="129c7-126">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
 [<span data-ttu-id="129c7-127">Navrhování pro rozšiřitelnost</span><span class="sxs-lookup"><span data-stu-id="129c7-127">Designing for Extensibility</span></span>](../../../docs/standard/design-guidelines/designing-for-extensibility.md)
