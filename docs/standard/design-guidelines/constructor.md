---
title: "Návrh – konstruktor"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- member design guidelines, constructors
- constructors, design guidelines
- instance constructors
- type constructors
- virtual members
- constructors, types
- default constructors
- static constructors
ms.assetid: b4496afe-5fa7-4bb0-85ca-70b0ef21e6fc
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a46bf111b76ef6d07fa99cc3b19684a0726b7062
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="constructor-design"></a><span data-ttu-id="845a5-102">Návrh – konstruktor</span><span class="sxs-lookup"><span data-stu-id="845a5-102">Constructor Design</span></span>
<span data-ttu-id="845a5-103">Existují dva druhy konstruktory: Zadejte konstruktory a konstruktory instancí.</span><span class="sxs-lookup"><span data-stu-id="845a5-103">There are two kinds of constructors: type constructors and instance constructors.</span></span>  
  
 <span data-ttu-id="845a5-104">Konstruktory typu statické a spustit modul CLR před použitím typu.</span><span class="sxs-lookup"><span data-stu-id="845a5-104">Type constructors are static and are run by the CLR before the type is used.</span></span> <span data-ttu-id="845a5-105">Konstruktory instancí spuštěny při vytvoření instance typu.</span><span class="sxs-lookup"><span data-stu-id="845a5-105">Instance constructors run when an instance of a type is created.</span></span>  
  
 <span data-ttu-id="845a5-106">Konstruktory typu nelze provést žádné parametry.</span><span class="sxs-lookup"><span data-stu-id="845a5-106">Type constructors cannot take any parameters.</span></span> <span data-ttu-id="845a5-107">Konstruktory instancí můžete.</span><span class="sxs-lookup"><span data-stu-id="845a5-107">Instance constructors can.</span></span> <span data-ttu-id="845a5-108">Konstruktory instancí, které nechcete provést žádné parametry se často nazývají výchozí konstruktory.</span><span class="sxs-lookup"><span data-stu-id="845a5-108">Instance constructors that don’t take any parameters are often called default constructors.</span></span>  
  
 <span data-ttu-id="845a5-109">Konstruktory jsou nejvíce přirozené způsob, jak vytvořit instance typu.</span><span class="sxs-lookup"><span data-stu-id="845a5-109">Constructors are the most natural way to create instances of a type.</span></span> <span data-ttu-id="845a5-110">Většina vývojářů bude hledat a pokuste se použít konstruktor před jejich zvažte alternativní způsoby vytváření instancí (například metody vytváření).</span><span class="sxs-lookup"><span data-stu-id="845a5-110">Most developers will search and try to use a constructor before they consider alternative ways of creating instances (such as factory methods).</span></span>  
  
 <span data-ttu-id="845a5-111">**✓ ZVAŽTE** poskytuje jednoduchý, v ideálním případě výchozí, konstruktory.</span><span class="sxs-lookup"><span data-stu-id="845a5-111">**✓ CONSIDER** providing simple, ideally default, constructors.</span></span>  
  
 <span data-ttu-id="845a5-112">Jednoduché konstruktor má velmi malý počet parametrů a všechny parametry jsou primitiv nebo výčty.</span><span class="sxs-lookup"><span data-stu-id="845a5-112">A simple constructor has a very small number of parameters, and all parameters are primitives or enums.</span></span> <span data-ttu-id="845a5-113">Tyto jednoduché konstruktory zvýšit použitelnost rozhraní.</span><span class="sxs-lookup"><span data-stu-id="845a5-113">Such simple constructors increase usability of the framework.</span></span>  
  
 <span data-ttu-id="845a5-114">**✓ ZVAŽTE** pomocí metody statické factory místo konstruktoru, pokud sémantiku požadovaná operace se nemapují přímo do vytváření nové instance, nebo pokud následující pokyny pro návrh konstruktor funguje nepřirozené.</span><span class="sxs-lookup"><span data-stu-id="845a5-114">**✓ CONSIDER** using a static factory method instead of a constructor if the semantics of the desired operation do not map directly to the construction of a new instance, or if following the constructor design guidelines feels unnatural.</span></span>  
  
 <span data-ttu-id="845a5-115">**PROVEĎTE ✓** použít konstruktor parametry jako zástupce pro nastavení hlavní vlastností.</span><span class="sxs-lookup"><span data-stu-id="845a5-115">**✓ DO** use constructor parameters as shortcuts for setting main properties.</span></span>  
  
 <span data-ttu-id="845a5-116">Měla by existovat žádný rozdíl ve smyslu sémantiky mezi pomocí prázdného konstruktoru následuje některé sady vlastností a pomocí konstruktoru více argumentů.</span><span class="sxs-lookup"><span data-stu-id="845a5-116">There should be no difference in semantics between using the empty constructor followed by some property sets and using a constructor with multiple arguments.</span></span>  
  
 <span data-ttu-id="845a5-117">**PROVEĎTE ✓** používají stejný název pro konstruktor parametry a vlastnosti, pokud se parametry konstruktor používají se jednoduše nastavit vlastnost.</span><span class="sxs-lookup"><span data-stu-id="845a5-117">**✓ DO** use the same name for constructor parameters and a property if the constructor parameters are used to simply set the property.</span></span>  
  
 <span data-ttu-id="845a5-118">Jediným rozdílem mezi tyto parametry a vlastnosti by měl být velká a malá písmena.</span><span class="sxs-lookup"><span data-stu-id="845a5-118">The only difference between such parameters and the properties should be casing.</span></span>  
  
 <span data-ttu-id="845a5-119">**PROVEĎTE ✓** minimálním úsilím v konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="845a5-119">**✓ DO** minimal work in the constructor.</span></span>  
  
 <span data-ttu-id="845a5-120">Konstruktory neměli dělat spoustu práce než zachycení parametry konstruktor.</span><span class="sxs-lookup"><span data-stu-id="845a5-120">Constructors should not do much work other than capture the constructor parameters.</span></span> <span data-ttu-id="845a5-121">Náklady na další zpracování by měl odloží až požadovaných.</span><span class="sxs-lookup"><span data-stu-id="845a5-121">The cost of any other processing should be delayed until required.</span></span>  
  
 <span data-ttu-id="845a5-122">**PROVEĎTE ✓** vyvolat výjimky z konstruktory instancí, podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="845a5-122">**✓ DO** throw exceptions from instance constructors, if appropriate.</span></span>  
  
 <span data-ttu-id="845a5-123">**PROVEĎTE ✓** explicitně deklarovat veřejný výchozí konstruktor ve třídách, pokud je potřeba takový konstruktor.</span><span class="sxs-lookup"><span data-stu-id="845a5-123">**✓ DO** explicitly declare the public default constructor in classes, if such a constructor is required.</span></span>  
  
 <span data-ttu-id="845a5-124">Pokud na typ není explicitně deklarovat všechny konstruktory, mnoha jazycích (například C#) automaticky přidá výchozí veřejný konstruktor.</span><span class="sxs-lookup"><span data-stu-id="845a5-124">If you don’t explicitly declare any constructors on a type, many languages (such as C#) will automatically add a public default constructor.</span></span> <span data-ttu-id="845a5-125">(Abstraktní třídy získat chráněný konstruktor.)</span><span class="sxs-lookup"><span data-stu-id="845a5-125">(Abstract classes get a protected constructor.)</span></span>  
  
 <span data-ttu-id="845a5-126">Přidání parametrizovaného konstruktor na třídu zabrání kompilátoru přidávání výchozí konstruktor.</span><span class="sxs-lookup"><span data-stu-id="845a5-126">Adding a parameterized constructor to a class prevents the compiler from adding the default constructor.</span></span> <span data-ttu-id="845a5-127">To často způsobuje náhodných nejnovější změny.</span><span class="sxs-lookup"><span data-stu-id="845a5-127">This often causes accidental breaking changes.</span></span>  
  
 <span data-ttu-id="845a5-128">**X nepoužívejte** explicitně na struktury definování výchozí konstruktory.</span><span class="sxs-lookup"><span data-stu-id="845a5-128">**X AVOID** explicitly defining default constructors on structs.</span></span>  
  
 <span data-ttu-id="845a5-129">Díky tomu pole vytvoření rychlejší, protože pokud není definován výchozí konstruktor, nemá ke spuštění na každý slot v poli.</span><span class="sxs-lookup"><span data-stu-id="845a5-129">This makes array creation faster, because if the default constructor is not defined, it does not have to be run on every slot in the array.</span></span> <span data-ttu-id="845a5-130">Všimněte si, že mnoho kompilátory, včetně C#, Nepovolit struktury tak, aby měl bezparametrové konstruktory z tohoto důvodu.</span><span class="sxs-lookup"><span data-stu-id="845a5-130">Note that many compilers, including C#, don’t allow structs to have parameterless constructors for this reason.</span></span>  
  
 <span data-ttu-id="845a5-131">**X nepoužívejte** volání virtuální členové objektu uvnitř jeho konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="845a5-131">**X AVOID** calling virtual members on an object inside its constructor.</span></span>  
  
 <span data-ttu-id="845a5-132">Volání metody člena virtuální způsobí, že nejodvozenějších přepsání, která se má volat, i když konstruktoru nejvíce odvozený typ dosud nebyla spuštěna plně.</span><span class="sxs-lookup"><span data-stu-id="845a5-132">Calling a virtual member will cause the most derived override to be called, even if the constructor of the most derived type has not been fully run yet.</span></span>  
  
### <a name="type-constructor-guidelines"></a><span data-ttu-id="845a5-133">Pokyny pro konstruktor typu</span><span class="sxs-lookup"><span data-stu-id="845a5-133">Type Constructor Guidelines</span></span>  
 <span data-ttu-id="845a5-134">**PROVEĎTE ✓** soukromá statické konstruktory.</span><span class="sxs-lookup"><span data-stu-id="845a5-134">**✓ DO** make static constructors private.</span></span>  
  
 <span data-ttu-id="845a5-135">Statický konstruktor, označované taky jako konstruktoru třídy, se používá k chybě při inicializaci typu.</span><span class="sxs-lookup"><span data-stu-id="845a5-135">A static constructor, also called a class constructor, is used to initialize a type.</span></span> <span data-ttu-id="845a5-136">Modul CLR volá statického konstruktoru dřív, než se vytvoří první instance typu nebo se nazývají všechny statické členy tohoto typu.</span><span class="sxs-lookup"><span data-stu-id="845a5-136">The CLR calls the static constructor before the first instance of the type is created or any static members on that type are called.</span></span> <span data-ttu-id="845a5-137">Uživatel nemá žádnou kontrolu nad kdy se nazývá statického konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="845a5-137">The user has no control over when the static constructor is called.</span></span> <span data-ttu-id="845a5-138">Statický konstruktor není privátní, může být volána kódu než modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="845a5-138">If a static constructor is not private, it can be called by code other than the CLR.</span></span> <span data-ttu-id="845a5-139">V závislosti na operací prováděných v konstruktoru to může způsobit neočekávané chování.</span><span class="sxs-lookup"><span data-stu-id="845a5-139">Depending on the operations performed in the constructor, this can cause unexpected behavior.</span></span> <span data-ttu-id="845a5-140">Kompilátor jazyka C# vynutí statické konstruktory důvěrné.</span><span class="sxs-lookup"><span data-stu-id="845a5-140">The C# compiler forces static constructors to be private.</span></span>  
  
 <span data-ttu-id="845a5-141">**X nesmí** generování výjimek ze statické konstruktory.</span><span class="sxs-lookup"><span data-stu-id="845a5-141">**X DO NOT** throw exceptions from static constructors.</span></span>  
  
 <span data-ttu-id="845a5-142">Pokud z konstruktoru typu je vyvolána výjimka, typ není v aktuální doméně aplikace.</span><span class="sxs-lookup"><span data-stu-id="845a5-142">If an exception is thrown from a type constructor, the type is not usable in the current application domain.</span></span>  
  
 <span data-ttu-id="845a5-143">**✓ ZVAŽTE** inicializace statického pole vloženě než explicitně pomocí statické konstruktory, protože modul runtime je schopen optimalizovat výkon typy, které nemají explicitně definovaných statického konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="845a5-143">**✓ CONSIDER** initializing static fields inline rather than explicitly using static constructors, because the runtime is able to optimize the performance of types that don’t have an explicitly defined static constructor.</span></span>  
  
 <span data-ttu-id="845a5-144">*Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*</span><span class="sxs-lookup"><span data-stu-id="845a5-144">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="845a5-145">*Provedení podle oprávnění Pearson Education, Inc. z [pokynů pro návrh Framework: konvence, Idioms a vzory pro jedno použití knihovny .NET, 2. vydání](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Abrams Brada publikovaná 22 Oct 2008 pomocí Designing Effective jako součást vývoj řady Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="845a5-145">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="845a5-146">Viz také</span><span class="sxs-lookup"><span data-stu-id="845a5-146">See Also</span></span>  
 [<span data-ttu-id="845a5-147">Člen pokynů pro návrh</span><span class="sxs-lookup"><span data-stu-id="845a5-147">Member Design Guidelines</span></span>](../../../docs/standard/design-guidelines/member.md)  
 [<span data-ttu-id="845a5-148">Pokyny pro návrh Framework</span><span class="sxs-lookup"><span data-stu-id="845a5-148">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
