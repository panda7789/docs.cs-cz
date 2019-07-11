---
title: Návrh konstruktoru
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- member design guidelines, constructors
- constructors, design guidelines
- instance constructors
- type constructors
- virtual members
- constructors, types
- parameterless constructors
- static constructors
ms.assetid: b4496afe-5fa7-4bb0-85ca-70b0ef21e6fc
author: KrzysztofCwalina
ms.openlocfilehash: 074aa391b71257584a01171e95da7472354cdc2c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67746773"
---
# <a name="constructor-design"></a><span data-ttu-id="8ac96-102">Návrh konstruktoru</span><span class="sxs-lookup"><span data-stu-id="8ac96-102">Constructor Design</span></span>
<span data-ttu-id="8ac96-103">Existují dva typy konstruktorů: Zadejte konstruktory a konstruktory instancí.</span><span class="sxs-lookup"><span data-stu-id="8ac96-103">There are two kinds of constructors: type constructors and instance constructors.</span></span>  
  
 <span data-ttu-id="8ac96-104">Konstruktory typu jsou statické a jsou provozované CLR předtím, než se typ používá.</span><span class="sxs-lookup"><span data-stu-id="8ac96-104">Type constructors are static and are run by the CLR before the type is used.</span></span> <span data-ttu-id="8ac96-105">Konstruktory instancí spustí, když je vytvořena instance typu.</span><span class="sxs-lookup"><span data-stu-id="8ac96-105">Instance constructors run when an instance of a type is created.</span></span>  
  
 <span data-ttu-id="8ac96-106">Konstruktory typu nelze provést žádné parametry.</span><span class="sxs-lookup"><span data-stu-id="8ac96-106">Type constructors cannot take any parameters.</span></span> <span data-ttu-id="8ac96-107">Konstruktory instancí může.</span><span class="sxs-lookup"><span data-stu-id="8ac96-107">Instance constructors can.</span></span> <span data-ttu-id="8ac96-108">Konstruktory instancí, které nechcete provést žádné parametry jsou často nazývány konstruktory bez parametrů.</span><span class="sxs-lookup"><span data-stu-id="8ac96-108">Instance constructors that don’t take any parameters are often called parameterless constructors.</span></span>  
  
 <span data-ttu-id="8ac96-109">Konstruktory jsou nejvíce přirozený způsob, jak vytvořit instance typu.</span><span class="sxs-lookup"><span data-stu-id="8ac96-109">Constructors are the most natural way to create instances of a type.</span></span> <span data-ttu-id="8ac96-110">Většina vývojářů hledání, který se pokusí použít konstruktor před považují za alternativní způsoby vytváření instancí (například metody pro vytváření objektů).</span><span class="sxs-lookup"><span data-stu-id="8ac96-110">Most developers will search and try to use a constructor before they consider alternative ways of creating instances (such as factory methods).</span></span>  
  
 <span data-ttu-id="8ac96-111">**✓ CONSIDER** poskytuje jednoduchý, v ideálním případě výchozí, konstruktory.</span><span class="sxs-lookup"><span data-stu-id="8ac96-111">**✓ CONSIDER** providing simple, ideally default, constructors.</span></span>  
  
 <span data-ttu-id="8ac96-112">Jednoduché konstruktor má velmi malý počet parametrů a všechny parametry jsou primitivních elementů nebo výčty.</span><span class="sxs-lookup"><span data-stu-id="8ac96-112">A simple constructor has a very small number of parameters, and all parameters are primitives or enums.</span></span> <span data-ttu-id="8ac96-113">Tyto jednoduché konstruktory zlepšit tak použitelnost rozhraní Framework.</span><span class="sxs-lookup"><span data-stu-id="8ac96-113">Such simple constructors increase usability of the framework.</span></span>  
  
 <span data-ttu-id="8ac96-114">**✓ CONSIDER** pomocí metody statické factory místo konstruktoru, pokud sémantiku požadovaná operace se nemapují přímo do vytváření nové instance, nebo pokud následující pokyny pro návrh konstruktor funguje nepřirozené.</span><span class="sxs-lookup"><span data-stu-id="8ac96-114">**✓ CONSIDER** using a static factory method instead of a constructor if the semantics of the desired operation do not map directly to the construction of a new instance, or if following the constructor design guidelines feels unnatural.</span></span>  
  
 <span data-ttu-id="8ac96-115">**✓ DO** použít konstruktor parametry jako zástupce pro nastavení hlavní vlastností.</span><span class="sxs-lookup"><span data-stu-id="8ac96-115">**✓ DO** use constructor parameters as shortcuts for setting main properties.</span></span>  
  
 <span data-ttu-id="8ac96-116">Měla by existovat žádné rozdíly v sémantice mezi pomocí prázdného konstruktoru, za nímž následuje některé vlastnosti sady a pomocí více argumentů konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="8ac96-116">There should be no difference in semantics between using the empty constructor followed by some property sets and using a constructor with multiple arguments.</span></span>  
  
 <span data-ttu-id="8ac96-117">**✓ DO** používají stejný název pro konstruktor parametry a vlastnosti, pokud se parametry konstruktor používají se jednoduše nastavit vlastnost.</span><span class="sxs-lookup"><span data-stu-id="8ac96-117">**✓ DO** use the same name for constructor parameters and a property if the constructor parameters are used to simply set the property.</span></span>  
  
 <span data-ttu-id="8ac96-118">Jediným rozdílem mezi tyto parametry a vlastnosti by měla být malá a velká písmena.</span><span class="sxs-lookup"><span data-stu-id="8ac96-118">The only difference between such parameters and the properties should be casing.</span></span>  
  
 <span data-ttu-id="8ac96-119">**✓ DO** minimálním úsilím v konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="8ac96-119">**✓ DO** minimal work in the constructor.</span></span>  
  
 <span data-ttu-id="8ac96-120">Konstruktory by neměla provést mnoho práce než zachytávání parametry konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="8ac96-120">Constructors should not do much work other than capture the constructor parameters.</span></span> <span data-ttu-id="8ac96-121">Náklady na libovolné jiné zpracování zpoždění, dokud se vyžaduje.</span><span class="sxs-lookup"><span data-stu-id="8ac96-121">The cost of any other processing should be delayed until required.</span></span>  
  
 <span data-ttu-id="8ac96-122">**✓ DO** vyvolat výjimky z konstruktory instancí, podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="8ac96-122">**✓ DO** throw exceptions from instance constructors, if appropriate.</span></span>  
  
 <span data-ttu-id="8ac96-123">**PROVEĎTE ✓** explicitně deklarovat konstruktor public bez parametrů ve třídách, pokud takový konstruktor je povinný.</span><span class="sxs-lookup"><span data-stu-id="8ac96-123">**✓ DO** explicitly declare the public parameterless constructor in classes, if such a constructor is required.</span></span>  
  
 <span data-ttu-id="8ac96-124">Pokud není deklarujete explicitně žádné konstruktory typu, řadu jiných jazyků (jako například C#) automaticky přidá veřejný konstruktor bez parametrů.</span><span class="sxs-lookup"><span data-stu-id="8ac96-124">If you don’t explicitly declare any constructors on a type, many languages (such as C#) will automatically add a public parameterless constructor.</span></span> <span data-ttu-id="8ac96-125">(Abstraktní třídy získat chráněný konstruktor.)</span><span class="sxs-lookup"><span data-stu-id="8ac96-125">(Abstract classes get a protected constructor.)</span></span>  
  
 <span data-ttu-id="8ac96-126">Přidávání do parametrizovaného konstruktoru třídy zabrání přidání konstruktor bez parametrů kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="8ac96-126">Adding a parameterized constructor to a class prevents the compiler from adding the parameterless constructor.</span></span> <span data-ttu-id="8ac96-127">Často způsobuje náhodného nejnovější změny.</span><span class="sxs-lookup"><span data-stu-id="8ac96-127">This often causes accidental breaking changes.</span></span>  
  
 <span data-ttu-id="8ac96-128">**X nepoužívejte** na struktury explicitně definovat konstruktory bez parametrů.</span><span class="sxs-lookup"><span data-stu-id="8ac96-128">**X AVOID** explicitly defining parameterless constructors on structs.</span></span>  
  
 <span data-ttu-id="8ac96-129">To umožňuje vytvoření pole rychleji, protože pokud není definován konstruktor bez parametrů, nemá pro spuštění na každé pozici pole.</span><span class="sxs-lookup"><span data-stu-id="8ac96-129">This makes array creation faster, because if the parameterless constructor is not defined, it does not have to be run on every slot in the array.</span></span> <span data-ttu-id="8ac96-130">Všimněte si, že mnoho kompilátorů, včetně C#, Nepovolit struktury z tohoto důvodu mít konstruktor bez parametrů.</span><span class="sxs-lookup"><span data-stu-id="8ac96-130">Note that many compilers, including C#, don’t allow structs to have parameterless constructors for this reason.</span></span>  
  
 <span data-ttu-id="8ac96-131">**X AVOID** volání virtuální členové objektu uvnitř jeho konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="8ac96-131">**X AVOID** calling virtual members on an object inside its constructor.</span></span>  
  
 <span data-ttu-id="8ac96-132">Volání virtuální člen způsobí nejodvozenějšího přepsání volat, i v případě, že nejvíc odvozený typ konstruktoru dosud nebyla spuštěna plně.</span><span class="sxs-lookup"><span data-stu-id="8ac96-132">Calling a virtual member will cause the most derived override to be called, even if the constructor of the most derived type has not been fully run yet.</span></span>  
  
### <a name="type-constructor-guidelines"></a><span data-ttu-id="8ac96-133">Pokyny pro konstruktor typu</span><span class="sxs-lookup"><span data-stu-id="8ac96-133">Type Constructor Guidelines</span></span>  
 <span data-ttu-id="8ac96-134">**✓ DO** soukromá statické konstruktory.</span><span class="sxs-lookup"><span data-stu-id="8ac96-134">**✓ DO** make static constructors private.</span></span>  
  
 <span data-ttu-id="8ac96-135">Statický konstruktor, také volat konstruktor třídy slouží k inicializaci typu.</span><span class="sxs-lookup"><span data-stu-id="8ac96-135">A static constructor, also called a class constructor, is used to initialize a type.</span></span> <span data-ttu-id="8ac96-136">CLR volá statický konstruktor před první instance typu je vytvořen nebo jakékoli statické členy tohoto typu jsou volány.</span><span class="sxs-lookup"><span data-stu-id="8ac96-136">The CLR calls the static constructor before the first instance of the type is created or any static members on that type are called.</span></span> <span data-ttu-id="8ac96-137">Uživatel nemá žádnou kontrolu nad tím, kdy je volána statický konstruktor.</span><span class="sxs-lookup"><span data-stu-id="8ac96-137">The user has no control over when the static constructor is called.</span></span> <span data-ttu-id="8ac96-138">Pokud statický konstruktor není soukromý, může být volán kód než CLR.</span><span class="sxs-lookup"><span data-stu-id="8ac96-138">If a static constructor is not private, it can be called by code other than the CLR.</span></span> <span data-ttu-id="8ac96-139">V závislosti na operací provedených v konstruktoru to může způsobit neočekávané chování.</span><span class="sxs-lookup"><span data-stu-id="8ac96-139">Depending on the operations performed in the constructor, this can cause unexpected behavior.</span></span> <span data-ttu-id="8ac96-140">Kompilátor jazyka C# vynutí statické konstruktory mají být privátní.</span><span class="sxs-lookup"><span data-stu-id="8ac96-140">The C# compiler forces static constructors to be private.</span></span>  
  
 <span data-ttu-id="8ac96-141">**X DO NOT** generování výjimek ze statické konstruktory.</span><span class="sxs-lookup"><span data-stu-id="8ac96-141">**X DO NOT** throw exceptions from static constructors.</span></span>  
  
 <span data-ttu-id="8ac96-142">Pokud je vyvolána výjimka v konstruktoru typu, typ není v aktuální doméně aplikace.</span><span class="sxs-lookup"><span data-stu-id="8ac96-142">If an exception is thrown from a type constructor, the type is not usable in the current application domain.</span></span>  
  
 <span data-ttu-id="8ac96-143">**✓ CONSIDER** inicializace statického pole vloženě než explicitně pomocí statické konstruktory, protože modul runtime je schopen optimalizovat výkon typy, které nemají explicitně definovaných statického konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="8ac96-143">**✓ CONSIDER** initializing static fields inline rather than explicitly using static constructors, because the runtime is able to optimize the performance of types that don’t have an explicitly defined static constructor.</span></span>  
  
 <span data-ttu-id="8ac96-144">*Portions © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*</span><span class="sxs-lookup"><span data-stu-id="8ac96-144">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="8ac96-145">*Přetištěno podle oprávnění Pearson vzdělávání, Inc. z [pokyny k návrhu architektury: Konvence, Idiomy a vzory pro opakovaně použitelného knihovny .NET, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Brad Abrams publikován 22 Oct 2008, Designing Effective části této série Microsoft Windows Development.*</span><span class="sxs-lookup"><span data-stu-id="8ac96-145">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ac96-146">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8ac96-146">See also</span></span>

- [<span data-ttu-id="8ac96-147">Pokyny k návrhu člena</span><span class="sxs-lookup"><span data-stu-id="8ac96-147">Member Design Guidelines</span></span>](../../../docs/standard/design-guidelines/member.md)
- [<span data-ttu-id="8ac96-148">Pokyny k návrhu architektury</span><span class="sxs-lookup"><span data-stu-id="8ac96-148">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
