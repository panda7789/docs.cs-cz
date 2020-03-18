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
ms.openlocfilehash: 7ab795cd4c6e0ff5e1451c05987848c41bd69577
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400601"
---
# <a name="constructor-design"></a><span data-ttu-id="c4891-102">Návrh konstruktoru</span><span class="sxs-lookup"><span data-stu-id="c4891-102">Constructor Design</span></span>

<span data-ttu-id="c4891-103">Existují dva druhy konstruktorů: typ konstruktory a instance konstruktory.</span><span class="sxs-lookup"><span data-stu-id="c4891-103">There are two kinds of constructors: type constructors and instance constructors.</span></span>

<span data-ttu-id="c4891-104">Typ konstruktory jsou statické a jsou spuštěny CLR před použitím typu.</span><span class="sxs-lookup"><span data-stu-id="c4891-104">Type constructors are static and are run by the CLR before the type is used.</span></span> <span data-ttu-id="c4891-105">Konstruktory instancí jsou spuštěny při vytvoření instance typu.</span><span class="sxs-lookup"><span data-stu-id="c4891-105">Instance constructors run when an instance of a type is created.</span></span>

<span data-ttu-id="c4891-106">Typ konstruktory nemůže trvat žádné parametry.</span><span class="sxs-lookup"><span data-stu-id="c4891-106">Type constructors cannot take any parameters.</span></span> <span data-ttu-id="c4891-107">Instance konstruktory mohou.</span><span class="sxs-lookup"><span data-stu-id="c4891-107">Instance constructors can.</span></span> <span data-ttu-id="c4891-108">Instance konstruktory, které neberou žádné parametry se často nazývají konstruktory bez parametrů.</span><span class="sxs-lookup"><span data-stu-id="c4891-108">Instance constructors that don’t take any parameters are often called parameterless constructors.</span></span>

<span data-ttu-id="c4891-109">Konstruktory jsou nejpřirozenější způsob, jak vytvořit instance typu.</span><span class="sxs-lookup"><span data-stu-id="c4891-109">Constructors are the most natural way to create instances of a type.</span></span> <span data-ttu-id="c4891-110">Většina vývojářů bude hledat a pokusí se použít konstruktor před tím, než zváží alternativní způsoby vytváření instancí (například metody výroby).</span><span class="sxs-lookup"><span data-stu-id="c4891-110">Most developers will search and try to use a constructor before they consider alternative ways of creating instances (such as factory methods).</span></span>

<span data-ttu-id="c4891-111">✔️ zvažte poskytnutí jednoduchých, ideálně výchozích konstruktorů.</span><span class="sxs-lookup"><span data-stu-id="c4891-111">✔️ CONSIDER providing simple, ideally default, constructors.</span></span>

<span data-ttu-id="c4891-112">Jednoduchý konstruktor má velmi malý počet parametrů a všechny parametry jsou primitiva nebo výčty.</span><span class="sxs-lookup"><span data-stu-id="c4891-112">A simple constructor has a very small number of parameters, and all parameters are primitives or enums.</span></span> <span data-ttu-id="c4891-113">Takové jednoduché konstruktory zvyšují použitelnost rámce.</span><span class="sxs-lookup"><span data-stu-id="c4891-113">Such simple constructors increase usability of the framework.</span></span>

<span data-ttu-id="c4891-114">✔️ zvažte použití statické tovární metody namísto konstruktoru, pokud sémantiku požadované operace nemapují přímo na konstrukci nové instance, nebo pokud se následující pokyny pro návrh konstruktoru cítí nepřirozeně.</span><span class="sxs-lookup"><span data-stu-id="c4891-114">✔️ CONSIDER using a static factory method instead of a constructor if the semantics of the desired operation do not map directly to the construction of a new instance, or if following the constructor design guidelines feels unnatural.</span></span>

<span data-ttu-id="c4891-115">✔️ DO použít parametry konstruktoru jako zkratky pro nastavení hlavních vlastností.</span><span class="sxs-lookup"><span data-stu-id="c4891-115">✔️ DO use constructor parameters as shortcuts for setting main properties.</span></span>

<span data-ttu-id="c4891-116">By měl být žádný rozdíl v sémantice mezi pomocí prázdný konstruktor následuje některé sady vlastností a pomocí konstruktoru s více argumenty.</span><span class="sxs-lookup"><span data-stu-id="c4891-116">There should be no difference in semantics between using the empty constructor followed by some property sets and using a constructor with multiple arguments.</span></span>

<span data-ttu-id="c4891-117">✔️ DO použít stejný název pro parametry konstruktoru a vlastnost, pokud parametry konstruktoru se používají k jednoduchému nastavení vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="c4891-117">✔️ DO use the same name for constructor parameters and a property if the constructor parameters are used to simply set the property.</span></span>

<span data-ttu-id="c4891-118">Jediným rozdílem mezi těmito parametry a vlastnostmi by měla být písmena.</span><span class="sxs-lookup"><span data-stu-id="c4891-118">The only difference between such parameters and the properties should be casing.</span></span>

<span data-ttu-id="c4891-119">✔️ provést minimální práci v konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="c4891-119">✔️ DO minimal work in the constructor.</span></span>

<span data-ttu-id="c4891-120">Konstruktory by neměly dělat mnoho práce než zachytit parametry konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="c4891-120">Constructors should not do much work other than capture the constructor parameters.</span></span> <span data-ttu-id="c4891-121">Náklady na jakékoli jiné zpracování by měly být zpožděny, dokud nebude vyžadováno.</span><span class="sxs-lookup"><span data-stu-id="c4891-121">The cost of any other processing should be delayed until required.</span></span>

<span data-ttu-id="c4891-122">✔️ DO vyvolat výjimky z konstruktorů instancí, pokud je to vhodné.</span><span class="sxs-lookup"><span data-stu-id="c4891-122">✔️ DO throw exceptions from instance constructors, if appropriate.</span></span>

<span data-ttu-id="c4891-123">✔️ DO explicitně deklarovat veřejné konstruktoru bez parametrů ve třídách, pokud je takový konstruktor požadován.</span><span class="sxs-lookup"><span data-stu-id="c4891-123">✔️ DO explicitly declare the public parameterless constructor in classes, if such a constructor is required.</span></span>

<span data-ttu-id="c4891-124">Pokud explicitně nedeklarujete žádné konstruktory na typu, mnoho jazyků (například C#) automaticky přidá veřejný konstruktor bez parametrů.</span><span class="sxs-lookup"><span data-stu-id="c4891-124">If you don’t explicitly declare any constructors on a type, many languages (such as C#) will automatically add a public parameterless constructor.</span></span> <span data-ttu-id="c4891-125">(Abstraktní třídy získat chráněný konstruktor.)</span><span class="sxs-lookup"><span data-stu-id="c4891-125">(Abstract classes get a protected constructor.)</span></span>

<span data-ttu-id="c4891-126">Přidání parametrizovaného konstruktoru do třídy zabrání kompilátoru v přidání konstruktoru bez parametrů.</span><span class="sxs-lookup"><span data-stu-id="c4891-126">Adding a parameterized constructor to a class prevents the compiler from adding the parameterless constructor.</span></span> <span data-ttu-id="c4891-127">To často způsobuje náhodné změny porušení.</span><span class="sxs-lookup"><span data-stu-id="c4891-127">This often causes accidental breaking changes.</span></span>

<span data-ttu-id="c4891-128">❌Vyhněte se explicitně definovat konstruktory bez parametrů na strukturách.</span><span class="sxs-lookup"><span data-stu-id="c4891-128">❌ AVOID explicitly defining parameterless constructors on structs.</span></span>

<span data-ttu-id="c4891-129">To zrychluje vytváření pole, protože pokud není definován konstruktor bez parametrů, nemusí být spuštěn na každém slotu v poli.</span><span class="sxs-lookup"><span data-stu-id="c4891-129">This makes array creation faster, because if the parameterless constructor is not defined, it does not have to be run on every slot in the array.</span></span> <span data-ttu-id="c4891-130">Všimněte si, že mnoho kompilátorů, včetně C#, neumožňují struktury mít konstruktory bez parametrů z tohoto důvodu.</span><span class="sxs-lookup"><span data-stu-id="c4891-130">Note that many compilers, including C#, don’t allow structs to have parameterless constructors for this reason.</span></span>

<span data-ttu-id="c4891-131">❌Vyhněte se volání virtuálních členů na objekt uvnitř jeho konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="c4891-131">❌ AVOID calling virtual members on an object inside its constructor.</span></span>

<span data-ttu-id="c4891-132">Volání virtuálního člena způsobí, že nejvíce odvozené přepsání bude voláno, i když konstruktor nejvíce odvozeného typu ještě nebyl plně spuštěn.</span><span class="sxs-lookup"><span data-stu-id="c4891-132">Calling a virtual member will cause the most derived override to be called, even if the constructor of the most derived type has not been fully run yet.</span></span>

## <a name="type-constructor-guidelines"></a><span data-ttu-id="c4891-133">Pokyny konstruktoru typu</span><span class="sxs-lookup"><span data-stu-id="c4891-133">Type Constructor Guidelines</span></span>

<span data-ttu-id="c4891-134">✔️ do, aby statické konstruktory soukromé.</span><span class="sxs-lookup"><span data-stu-id="c4891-134">✔️ DO make static constructors private.</span></span>

<span data-ttu-id="c4891-135">Statický konstruktor, nazývaný také konstruktor třídy, se používá k inicializaci typu.</span><span class="sxs-lookup"><span data-stu-id="c4891-135">A static constructor, also called a class constructor, is used to initialize a type.</span></span> <span data-ttu-id="c4891-136">CLR volá statický konstruktor před vytvořením první instance typu nebo jsou volány všechny statické členy tohoto typu.</span><span class="sxs-lookup"><span data-stu-id="c4891-136">The CLR calls the static constructor before the first instance of the type is created or any static members on that type are called.</span></span> <span data-ttu-id="c4891-137">Uživatel nemá žádnou kontrolu nad při volání statického konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="c4891-137">The user has no control over when the static constructor is called.</span></span> <span data-ttu-id="c4891-138">Pokud statický konstruktor není soukromý, může být volán jiným kódem než CLR.</span><span class="sxs-lookup"><span data-stu-id="c4891-138">If a static constructor is not private, it can be called by code other than the CLR.</span></span> <span data-ttu-id="c4891-139">V závislosti na operacích prováděných v konstruktoru to může způsobit neočekávané chování.</span><span class="sxs-lookup"><span data-stu-id="c4891-139">Depending on the operations performed in the constructor, this can cause unexpected behavior.</span></span> <span data-ttu-id="c4891-140">Kompilátor Jazyka C# vynutí, aby statické konstruktory byly soukromé.</span><span class="sxs-lookup"><span data-stu-id="c4891-140">The C# compiler forces static constructors to be private.</span></span>

<span data-ttu-id="c4891-141">❌NEVYVOLÁVAT výjimky ze statických konstruktorů.</span><span class="sxs-lookup"><span data-stu-id="c4891-141">❌ DO NOT throw exceptions from static constructors.</span></span>

<span data-ttu-id="c4891-142">Pokud je vyvolána výjimka z konstruktoru typu, typ není použitelný v aktuální doméně aplikace.</span><span class="sxs-lookup"><span data-stu-id="c4891-142">If an exception is thrown from a type constructor, the type is not usable in the current application domain.</span></span>

<span data-ttu-id="c4891-143">✔️ zvážit inicializaci statických polí vřadit spíše než explicitně pomocí statických konstruktorů, protože runtime je schopen optimalizovat výkon typů, které nemají explicitně definovaný statický konstruktor.</span><span class="sxs-lookup"><span data-stu-id="c4891-143">✔️ CONSIDER initializing static fields inline rather than explicitly using static constructors, because the runtime is able to optimize the performance of types that don’t have an explicitly defined static constructor.</span></span>

<span data-ttu-id="c4891-144">*Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*</span><span class="sxs-lookup"><span data-stu-id="c4891-144">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

<span data-ttu-id="c4891-145">*Přetištěno se svolením Pearson Education, Inc. z [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span><span class="sxs-lookup"><span data-stu-id="c4891-145">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="c4891-146">Viz také</span><span class="sxs-lookup"><span data-stu-id="c4891-146">See also</span></span>

- [<span data-ttu-id="c4891-147">Pokyny k návrhu člena</span><span class="sxs-lookup"><span data-stu-id="c4891-147">Member Design Guidelines</span></span>](../../../docs/standard/design-guidelines/member.md)
- [<span data-ttu-id="c4891-148">Pokyny k návrhu architektury</span><span class="sxs-lookup"><span data-stu-id="c4891-148">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
