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
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741734"
---
# <a name="constructor-design"></a><span data-ttu-id="aa6c8-102">Návrh konstruktoru</span><span class="sxs-lookup"><span data-stu-id="aa6c8-102">Constructor Design</span></span>

<span data-ttu-id="aa6c8-103">Existují dva druhy konstruktorů: konstruktory typů a konstruktory instancí.</span><span class="sxs-lookup"><span data-stu-id="aa6c8-103">There are two kinds of constructors: type constructors and instance constructors.</span></span>

<span data-ttu-id="aa6c8-104">Konstruktory typů jsou statické a jsou spuštěny modulem CLR před použitím typu.</span><span class="sxs-lookup"><span data-stu-id="aa6c8-104">Type constructors are static and are run by the CLR before the type is used.</span></span> <span data-ttu-id="aa6c8-105">Konstruktory instancí jsou spouštěny při vytvoření instance typu.</span><span class="sxs-lookup"><span data-stu-id="aa6c8-105">Instance constructors run when an instance of a type is created.</span></span>

<span data-ttu-id="aa6c8-106">Konstruktory typů nemůžou mít žádné parametry.</span><span class="sxs-lookup"><span data-stu-id="aa6c8-106">Type constructors cannot take any parameters.</span></span> <span data-ttu-id="aa6c8-107">Konstruktory instancí můžou.</span><span class="sxs-lookup"><span data-stu-id="aa6c8-107">Instance constructors can.</span></span> <span data-ttu-id="aa6c8-108">Konstruktory instancí, které nevyužívají žádné parametry, se často nazývají konstruktory bez parametrů.</span><span class="sxs-lookup"><span data-stu-id="aa6c8-108">Instance constructors that don’t take any parameters are often called parameterless constructors.</span></span>

<span data-ttu-id="aa6c8-109">Konstruktory představují nejpřirozený způsob, jak vytvořit instance typu.</span><span class="sxs-lookup"><span data-stu-id="aa6c8-109">Constructors are the most natural way to create instances of a type.</span></span> <span data-ttu-id="aa6c8-110">Většina vývojářů hledá a pokusí se použít konstruktor předtím, než uvažují alternativní způsoby vytváření instancí (například metody výroby).</span><span class="sxs-lookup"><span data-stu-id="aa6c8-110">Most developers will search and try to use a constructor before they consider alternative ways of creating instances (such as factory methods).</span></span>

<span data-ttu-id="aa6c8-111">✔️ Zvažte poskytování jednoduchých, ideálních, ideálních konstruktorů.</span><span class="sxs-lookup"><span data-stu-id="aa6c8-111">✔️ CONSIDER providing simple, ideally default, constructors.</span></span>

<span data-ttu-id="aa6c8-112">Jednoduchý konstruktor má velmi malý počet parametrů a všechny parametry jsou primitivní nebo výčty.</span><span class="sxs-lookup"><span data-stu-id="aa6c8-112">A simple constructor has a very small number of parameters, and all parameters are primitives or enums.</span></span> <span data-ttu-id="aa6c8-113">Takové jednoduché konstruktory zvyšují použitelnost rozhraní.</span><span class="sxs-lookup"><span data-stu-id="aa6c8-113">Such simple constructors increase usability of the framework.</span></span>

<span data-ttu-id="aa6c8-114">✔️ Zvažte použití statické metody Factory namísto konstruktoru, pokud sémantika požadované operace není mapována přímo na konstrukci nové instance, nebo pokud podle pokynů pro návrh konstruktoru nevidíte nepřirozeně.</span><span class="sxs-lookup"><span data-stu-id="aa6c8-114">✔️ CONSIDER using a static factory method instead of a constructor if the semantics of the desired operation do not map directly to the construction of a new instance, or if following the constructor design guidelines feels unnatural.</span></span>

<span data-ttu-id="aa6c8-115">✔️ použít parametry konstruktoru jako zkratky pro nastavení hlavních vlastností.</span><span class="sxs-lookup"><span data-stu-id="aa6c8-115">✔️ DO use constructor parameters as shortcuts for setting main properties.</span></span>

<span data-ttu-id="aa6c8-116">V sémantikě by neměl být žádný rozdíl mezi použitím prázdného konstruktoru následovanýho některými sadami vlastností a použitím konstruktoru s více argumenty.</span><span class="sxs-lookup"><span data-stu-id="aa6c8-116">There should be no difference in semantics between using the empty constructor followed by some property sets and using a constructor with multiple arguments.</span></span>

<span data-ttu-id="aa6c8-117">✔️ použít stejný název pro parametry konstruktoru a vlastnost, pokud jsou parametry konstruktoru použity pro jednoduše nastavení vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="aa6c8-117">✔️ DO use the same name for constructor parameters and a property if the constructor parameters are used to simply set the property.</span></span>

<span data-ttu-id="aa6c8-118">Jediný rozdíl mezi takovými parametry a vlastnostmi musí být velká a malá písmena.</span><span class="sxs-lookup"><span data-stu-id="aa6c8-118">The only difference between such parameters and the properties should be casing.</span></span>

<span data-ttu-id="aa6c8-119">✔️ UDĚLAT v konstruktoru minimální práci.</span><span class="sxs-lookup"><span data-stu-id="aa6c8-119">✔️ DO minimal work in the constructor.</span></span>

<span data-ttu-id="aa6c8-120">Konstruktory by neměly dělat mnohem více práce než zachycení parametrů konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="aa6c8-120">Constructors should not do much work other than capture the constructor parameters.</span></span> <span data-ttu-id="aa6c8-121">Náklady na jakékoli jiné zpracování by měly být zpožděny, dokud není vyžadováno.</span><span class="sxs-lookup"><span data-stu-id="aa6c8-121">The cost of any other processing should be delayed until required.</span></span>

<span data-ttu-id="aa6c8-122">Pokud je to vhodné, ✔️ vyvolat výjimky z konstruktorů instance.</span><span class="sxs-lookup"><span data-stu-id="aa6c8-122">✔️ DO throw exceptions from instance constructors, if appropriate.</span></span>

<span data-ttu-id="aa6c8-123">✔️ explicitně deklarovat veřejný konstruktor bez parametrů ve třídách, pokud je takový konstruktor požadován.</span><span class="sxs-lookup"><span data-stu-id="aa6c8-123">✔️ DO explicitly declare the public parameterless constructor in classes, if such a constructor is required.</span></span>

<span data-ttu-id="aa6c8-124">Pokud nedeklarujete explicitně žádné konstruktory typu, mnoho jazyků (například C#) bude automaticky přidávat veřejný konstruktor bez parametrů.</span><span class="sxs-lookup"><span data-stu-id="aa6c8-124">If you don’t explicitly declare any constructors on a type, many languages (such as C#) will automatically add a public parameterless constructor.</span></span> <span data-ttu-id="aa6c8-125">(Abstraktní třídy získávají chráněný konstruktor.)</span><span class="sxs-lookup"><span data-stu-id="aa6c8-125">(Abstract classes get a protected constructor.)</span></span>

<span data-ttu-id="aa6c8-126">Přidání parametrizovaného konstruktoru do třídy znemožní kompilátoru přidat konstruktor bez parametrů.</span><span class="sxs-lookup"><span data-stu-id="aa6c8-126">Adding a parameterized constructor to a class prevents the compiler from adding the parameterless constructor.</span></span> <span data-ttu-id="aa6c8-127">To často způsobí nechtěné změny.</span><span class="sxs-lookup"><span data-stu-id="aa6c8-127">This often causes accidental breaking changes.</span></span>

<span data-ttu-id="aa6c8-128">❌ se vyhnout explicitnímu definování konstruktorů bez parametrů u struktur.</span><span class="sxs-lookup"><span data-stu-id="aa6c8-128">❌ AVOID explicitly defining parameterless constructors on structs.</span></span>

<span data-ttu-id="aa6c8-129">Díky tomu je vytvoření pole rychlejší, protože pokud konstruktor bez parametrů není definován, nemusí být spuštěn na všech slotech v poli.</span><span class="sxs-lookup"><span data-stu-id="aa6c8-129">This makes array creation faster, because if the parameterless constructor is not defined, it does not have to be run on every slot in the array.</span></span> <span data-ttu-id="aa6c8-130">Všimněte si, že mnoho kompilátorů C#, včetně, neumožňuje strukturám mít z tohoto důvodu konstruktory bez parametrů.</span><span class="sxs-lookup"><span data-stu-id="aa6c8-130">Note that many compilers, including C#, don’t allow structs to have parameterless constructors for this reason.</span></span>

<span data-ttu-id="aa6c8-131">❌ Vyhněte se volání virtuálních členů u objektu uvnitř jeho konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="aa6c8-131">❌ AVOID calling virtual members on an object inside its constructor.</span></span>

<span data-ttu-id="aa6c8-132">Volání virtuálního členu způsobí volání nejvíce odvozeného přepsání, a to i v případě, že konstruktor nejvíce odvozeného typu nebyl dosud zcela spuštěn.</span><span class="sxs-lookup"><span data-stu-id="aa6c8-132">Calling a virtual member will cause the most derived override to be called, even if the constructor of the most derived type has not been fully run yet.</span></span>

## <a name="type-constructor-guidelines"></a><span data-ttu-id="aa6c8-133">Pokyny k konstruktoru typu</span><span class="sxs-lookup"><span data-stu-id="aa6c8-133">Type Constructor Guidelines</span></span>

<span data-ttu-id="aa6c8-134">✔️ UDĚLAT statické konstruktory jako soukromé.</span><span class="sxs-lookup"><span data-stu-id="aa6c8-134">✔️ DO make static constructors private.</span></span>

<span data-ttu-id="aa6c8-135">Pro inicializaci typu se používá statický konstruktor, označovaný také jako konstruktor třídy.</span><span class="sxs-lookup"><span data-stu-id="aa6c8-135">A static constructor, also called a class constructor, is used to initialize a type.</span></span> <span data-ttu-id="aa6c8-136">Modul CLR volá statický konstruktor před vytvořením první instance typu nebo se zavoláním všech statických členů tohoto typu.</span><span class="sxs-lookup"><span data-stu-id="aa6c8-136">The CLR calls the static constructor before the first instance of the type is created or any static members on that type are called.</span></span> <span data-ttu-id="aa6c8-137">Uživatel nemá žádné řízení při volání statického konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="aa6c8-137">The user has no control over when the static constructor is called.</span></span> <span data-ttu-id="aa6c8-138">Pokud statický konstruktor není privátní, může být volán jiným kódem než CLR.</span><span class="sxs-lookup"><span data-stu-id="aa6c8-138">If a static constructor is not private, it can be called by code other than the CLR.</span></span> <span data-ttu-id="aa6c8-139">V závislosti na operacích provedených v konstruktoru to může způsobit neočekávané chování.</span><span class="sxs-lookup"><span data-stu-id="aa6c8-139">Depending on the operations performed in the constructor, this can cause unexpected behavior.</span></span> <span data-ttu-id="aa6c8-140">C# Kompilátor vynutí, aby statické konstruktory byly privátní.</span><span class="sxs-lookup"><span data-stu-id="aa6c8-140">The C# compiler forces static constructors to be private.</span></span>

<span data-ttu-id="aa6c8-141">❌ nevyvolávat výjimky ze statických konstruktorů.</span><span class="sxs-lookup"><span data-stu-id="aa6c8-141">❌ DO NOT throw exceptions from static constructors.</span></span>

<span data-ttu-id="aa6c8-142">Je-li výjimka vyvolána z konstruktoru typu, nelze typ použít v aktuální doméně aplikace.</span><span class="sxs-lookup"><span data-stu-id="aa6c8-142">If an exception is thrown from a type constructor, the type is not usable in the current application domain.</span></span>

<span data-ttu-id="aa6c8-143">✔️ Zvažte inicializaci statických polí namísto explicitního použití statických konstruktorů, protože modul runtime může optimalizovat výkon typů, které nemají explicitně definovaný statický konstruktor.</span><span class="sxs-lookup"><span data-stu-id="aa6c8-143">✔️ CONSIDER initializing static fields inline rather than explicitly using static constructors, because the runtime is able to optimize the performance of types that don’t have an explicitly defined static constructor.</span></span>

<span data-ttu-id="aa6c8-144">*Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*</span><span class="sxs-lookup"><span data-stu-id="aa6c8-144">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

<span data-ttu-id="aa6c8-145">*Přetištěno oprávněním Pearsonova vzdělávání, Inc. z [pokynů pro návrh rozhraní: konvence, idiomy a vzory pro opakovaně použitelné knihovny .NET, druhá edice](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) od Krzysztof Cwalina a Brad Abrams, publikovaly 22. října 2008 Addison-Wesley Professional jako součást sady Microsoft Windows Development Series.*</span><span class="sxs-lookup"><span data-stu-id="aa6c8-145">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="aa6c8-146">Viz také</span><span class="sxs-lookup"><span data-stu-id="aa6c8-146">See also</span></span>

- [<span data-ttu-id="aa6c8-147">Pokyny k návrhu člena</span><span class="sxs-lookup"><span data-stu-id="aa6c8-147">Member Design Guidelines</span></span>](../../../docs/standard/design-guidelines/member.md)
- [<span data-ttu-id="aa6c8-148">Pokyny k návrhu architektury</span><span class="sxs-lookup"><span data-stu-id="aa6c8-148">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
