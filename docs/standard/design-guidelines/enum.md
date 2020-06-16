---
title: Návrh výčtu
description: Návrh pro výčty, které jsou zvláštním druhem hodnotového typu. Jednoduché výčty uchovávají malé, uzavřené sady možností. Výčty označení podporují bitové operace s hodnotami výčtu.
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- type design guidelines, enumerations
- simple enumerations
- enumerations [.NET Framework], design guidelines
- class library design guidelines [.NET Framework], enumerations
- flags enumerations
ms.assetid: dd53c952-9d9a-4736-86ff-9540e815d545
ms.openlocfilehash: 40a9faf53dc8a03674cd59074244c15cd304bdd2
ms.sourcegitcommit: 5fd4696a3e5791b2a8c449ccffda87f2cc2d4894
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/15/2020
ms.locfileid: "84768534"
---
# <a name="enum-design"></a><span data-ttu-id="ba31f-105">Návrh výčtu</span><span class="sxs-lookup"><span data-stu-id="ba31f-105">Enum Design</span></span>

<span data-ttu-id="ba31f-106">Výčty jsou speciálním druhem hodnotového typu.</span><span class="sxs-lookup"><span data-stu-id="ba31f-106">Enums are a special kind of value type.</span></span> <span data-ttu-id="ba31f-107">Existují dva druhy výčtů: jednoduché výčty a výčty příznaku.</span><span class="sxs-lookup"><span data-stu-id="ba31f-107">There are two kinds of enums: simple enums and flag enums.</span></span>

<span data-ttu-id="ba31f-108">Jednoduché výčty reprezentují malé uzavřené sady možností.</span><span class="sxs-lookup"><span data-stu-id="ba31f-108">Simple enums represent small closed sets of choices.</span></span> <span data-ttu-id="ba31f-109">Běžným příkladem jednoduchého výčtu je sada barev.</span><span class="sxs-lookup"><span data-stu-id="ba31f-109">A common example of the simple enum is a set of colors.</span></span>

<span data-ttu-id="ba31f-110">Výčty příznaků jsou navržené tak, aby podporovaly bitové operace s hodnotami výčtu.</span><span class="sxs-lookup"><span data-stu-id="ba31f-110">Flag enums are designed to support bitwise operations on the enum values.</span></span> <span data-ttu-id="ba31f-111">Běžným příkladem výčtu příznaků je seznam možností.</span><span class="sxs-lookup"><span data-stu-id="ba31f-111">A common example of the flags enum is a list of options.</span></span>

<span data-ttu-id="ba31f-112">✔️ použít výčet pro silné typy parametrů, vlastnosti a návratové hodnoty, které reprezentují sady hodnot.</span><span class="sxs-lookup"><span data-stu-id="ba31f-112">✔️ DO use an enum to strongly type parameters, properties, and return values that represent sets of values.</span></span>

<span data-ttu-id="ba31f-113">✔️ preferovat pomocí výčtu místo statických konstant.</span><span class="sxs-lookup"><span data-stu-id="ba31f-113">✔️ DO favor using an enum instead of static constants.</span></span>

<span data-ttu-id="ba31f-114">❌Nepoužívejte výčet pro otevřené sady (například verzi operačního systému, názvy vašich přátel atd.).</span><span class="sxs-lookup"><span data-stu-id="ba31f-114">❌ DO NOT use an enum for open sets (such as the operating system version, names of your friends, etc.).</span></span>

<span data-ttu-id="ba31f-115">❌Neposkytněte hodnoty rezervovaných výčtů, které jsou určeny pro budoucí použití.</span><span class="sxs-lookup"><span data-stu-id="ba31f-115">❌ DO NOT provide reserved enum values that are intended for future use.</span></span>

<span data-ttu-id="ba31f-116">V pozdější fázi můžete kdykoli jednoduše přidat hodnoty do stávajícího výčtu.</span><span class="sxs-lookup"><span data-stu-id="ba31f-116">You can always simply add values to the existing enum at a later stage.</span></span> <span data-ttu-id="ba31f-117">Další podrobnosti o přidávání hodnot do výčtů naleznete v tématu [Přidání hodnot do výčtů](#add_value) .</span><span class="sxs-lookup"><span data-stu-id="ba31f-117">See [Adding Values to Enums](#add_value) for more details on adding values to enums.</span></span> <span data-ttu-id="ba31f-118">Rezervované hodnoty jenom zneznečišťující sadu skutečných hodnot a mají za následek chyby uživatelů.</span><span class="sxs-lookup"><span data-stu-id="ba31f-118">Reserved values just pollute the set of real values and tend to lead to user errors.</span></span>

<span data-ttu-id="ba31f-119">❌Vyhněte se veřejně vystavování výčtů pouze s jednou hodnotou.</span><span class="sxs-lookup"><span data-stu-id="ba31f-119">❌ AVOID publicly exposing enums with only one value.</span></span>

<span data-ttu-id="ba31f-120">Běžný postup pro zajištění budoucí rozšiřitelnosti rozhraní API jazyka C je přidání rezervovaných parametrů k podpisům metod.</span><span class="sxs-lookup"><span data-stu-id="ba31f-120">A common practice for ensuring future extensibility of C APIs is to add reserved parameters to method signatures.</span></span> <span data-ttu-id="ba31f-121">Tyto vyhrazené parametry lze vyjádřit jako výčty s jednou výchozí hodnotou.</span><span class="sxs-lookup"><span data-stu-id="ba31f-121">Such reserved parameters can be expressed as enums with a single default value.</span></span> <span data-ttu-id="ba31f-122">To by nemělo být provedeno ve spravovaných rozhraních API.</span><span class="sxs-lookup"><span data-stu-id="ba31f-122">This should not be done in managed APIs.</span></span> <span data-ttu-id="ba31f-123">Přetížení metody umožňuje přidávání parametrů v budoucích verzích.</span><span class="sxs-lookup"><span data-stu-id="ba31f-123">Method overloading allows adding parameters in future releases.</span></span>

<span data-ttu-id="ba31f-124">❌Nezahrnujte hodnoty Sentinel do výčtů.</span><span class="sxs-lookup"><span data-stu-id="ba31f-124">❌ DO NOT include sentinel values in enums.</span></span>

<span data-ttu-id="ba31f-125">I když jsou někdy užitečné pro vývojáře architektury, hodnoty Sentinel jsou pro uživatele rozhraní matoucí.</span><span class="sxs-lookup"><span data-stu-id="ba31f-125">Although they are sometimes helpful to framework developers, sentinel values are confusing to users of the framework.</span></span> <span data-ttu-id="ba31f-126">Používají se ke sledování stavu výčtu, nikoli k jedné z hodnot ze sady reprezentované výčtem.</span><span class="sxs-lookup"><span data-stu-id="ba31f-126">They are used to track the state of the enum rather than being one of the values from the set represented by the enum.</span></span>

<span data-ttu-id="ba31f-127">✔️ pro jednoduché výčty zadejte hodnotu nula.</span><span class="sxs-lookup"><span data-stu-id="ba31f-127">✔️ DO provide a value of zero on simple enums.</span></span>

<span data-ttu-id="ba31f-128">Zvažte volání hodnoty jako "none".</span><span class="sxs-lookup"><span data-stu-id="ba31f-128">Consider calling the value something like "None."</span></span> <span data-ttu-id="ba31f-129">Pokud taková hodnota není vhodná pro tento konkrétní výčet, měla by být většině běžných výchozích hodnot výčtu přiřazena základní hodnota nula.</span><span class="sxs-lookup"><span data-stu-id="ba31f-129">If such a value is not appropriate for this particular enum, the most common default value for the enum should be assigned the underlying value of zero.</span></span>

<span data-ttu-id="ba31f-130">✔️ Zvažte použití <xref:System.Int32> (výchozí ve většině programovacích jazyků) jako podkladový typ výčtu, pokud není splněna některá z následujících podmínek:</span><span class="sxs-lookup"><span data-stu-id="ba31f-130">✔️ CONSIDER using <xref:System.Int32> (the default in most programming languages) as the underlying type of an enum unless any of the following is true:</span></span>

- <span data-ttu-id="ba31f-131">Výčtový typ je výčet příznaků a máte více než 32 příznaků nebo v budoucnu očekávat větší hodnotu.</span><span class="sxs-lookup"><span data-stu-id="ba31f-131">The enum is a flags enum and you have more than 32 flags, or expect to have more in the future.</span></span>

- <span data-ttu-id="ba31f-132">Podkladový typ musí být jiný než <xref:System.Int32> pro snazší interoperabilitu s nespravovaným kódem, který očekává různé velikosti výčtů.</span><span class="sxs-lookup"><span data-stu-id="ba31f-132">The underlying type needs to be different than <xref:System.Int32> for easier interoperability with unmanaged code expecting different-size enums.</span></span>

- <span data-ttu-id="ba31f-133">Menší nadřízený typ by způsobil značnou úsporu místa.</span><span class="sxs-lookup"><span data-stu-id="ba31f-133">A smaller underlying type would result in substantial savings in space.</span></span> <span data-ttu-id="ba31f-134">Pokud očekáváte, že se má výčet použít hlavně jako argument pro tok řízení, velikost bude mít malý rozdíl.</span><span class="sxs-lookup"><span data-stu-id="ba31f-134">If you expect the enum to be used mainly as an argument for flow of control, the size makes little difference.</span></span> <span data-ttu-id="ba31f-135">Úspora velikosti může být významná v těchto případech:</span><span class="sxs-lookup"><span data-stu-id="ba31f-135">The size savings might be significant if:</span></span>

  - <span data-ttu-id="ba31f-136">Očekáváte, že se výčet použije jako pole ve velmi často se instanci struktury nebo třídy.</span><span class="sxs-lookup"><span data-stu-id="ba31f-136">You expect the enum to be used as a field in a very frequently instantiated structure or class.</span></span>

  - <span data-ttu-id="ba31f-137">Očekáváte, že uživatelé budou vytvářet velká pole nebo kolekce instancí výčtu.</span><span class="sxs-lookup"><span data-stu-id="ba31f-137">You expect users to create large arrays or collections of the enum instances.</span></span>

  - <span data-ttu-id="ba31f-138">Očekáváte, že se má serializovat velký počet instancí výčtu.</span><span class="sxs-lookup"><span data-stu-id="ba31f-138">You expect a large number of instances of the enum to be serialized.</span></span>

<span data-ttu-id="ba31f-139">V případě využití paměti je třeba si uvědomit, že jsou spravované objekty vždycky `DWORD` zarovnané, takže budete v instanci efektivně potřebovat více výčtů nebo jiných malých struktur, aby bylo možné provést rozdíl, protože celková velikost instance se vždycky zaokrouhluje na `DWORD` .</span><span class="sxs-lookup"><span data-stu-id="ba31f-139">For in-memory usage, be aware that managed objects are always `DWORD`-aligned, so you effectively need multiple enums or other small structures in an instance to pack a smaller enum with in order to make a difference, because the total instance size is always going to be rounded up to a `DWORD`.</span></span>

<span data-ttu-id="ba31f-140">✔️ DO názvů označovat výčty s podstatnými jmény v množném číslech nebo frázemi podstatných jmen a jednoduchými výčty s podstatnými jmény a větami</span><span class="sxs-lookup"><span data-stu-id="ba31f-140">✔️ DO name flag enums with plural nouns or noun phrases and simple enums with singular nouns or noun phrases.</span></span>

<span data-ttu-id="ba31f-141">❌Nešíří se <xref:System.Enum?displayProperty=nameWithType> přímo.</span><span class="sxs-lookup"><span data-stu-id="ba31f-141">❌ DO NOT extend <xref:System.Enum?displayProperty=nameWithType> directly.</span></span>

<span data-ttu-id="ba31f-142"><xref:System.Enum?displayProperty=nameWithType>je speciální typ používaný modulem CLR k vytváření výčtů definovaných uživatelem.</span><span class="sxs-lookup"><span data-stu-id="ba31f-142"><xref:System.Enum?displayProperty=nameWithType> is a special type used by the CLR to create user-defined enumerations.</span></span> <span data-ttu-id="ba31f-143">Většina programovacích jazyků poskytuje programovací prvek, který vám dává přístup k této funkci.</span><span class="sxs-lookup"><span data-stu-id="ba31f-143">Most programming languages provide a programming element that gives you access to this functionality.</span></span> <span data-ttu-id="ba31f-144">Například v jazyce C# se `enum` klíčové slovo používá k definování výčtu.</span><span class="sxs-lookup"><span data-stu-id="ba31f-144">For example, in C# the `enum` keyword is used to define an enumeration.</span></span>

<a name="design"></a>

### <a name="designing-flag-enums"></a><span data-ttu-id="ba31f-145">Navrhování výčtů příznaků</span><span class="sxs-lookup"><span data-stu-id="ba31f-145">Designing Flag Enums</span></span>

<span data-ttu-id="ba31f-146">✔️ použít <xref:System.FlagsAttribute?displayProperty=nameWithType> pro označení výčty.</span><span class="sxs-lookup"><span data-stu-id="ba31f-146">✔️ DO apply the <xref:System.FlagsAttribute?displayProperty=nameWithType> to flag enums.</span></span> <span data-ttu-id="ba31f-147">Nepoužívejte tento atribut pro jednoduché výčty.</span><span class="sxs-lookup"><span data-stu-id="ba31f-147">Do not apply this attribute to simple enums.</span></span>

<span data-ttu-id="ba31f-148">✔️ pro hodnoty výčtu příznaků použít mocniny dvou, aby bylo možné volně kombinovat pomocí bitové operace OR.</span><span class="sxs-lookup"><span data-stu-id="ba31f-148">✔️ DO use powers of two for the flag enum values so they can be freely combined using the bitwise OR operation.</span></span>

<span data-ttu-id="ba31f-149">✔️ Zvažte poskytování speciálních hodnot výčtu pro běžně používané kombinace příznaků.</span><span class="sxs-lookup"><span data-stu-id="ba31f-149">✔️ CONSIDER providing special enum values for commonly used combinations of flags.</span></span>

<span data-ttu-id="ba31f-150">Bitové operace jsou pokročilým konceptem a neměly by se vyžadovat pro jednoduché úlohy.</span><span class="sxs-lookup"><span data-stu-id="ba31f-150">Bitwise operations are an advanced concept and should not be required for simple tasks.</span></span> <span data-ttu-id="ba31f-151"><xref:System.IO.FileAccess.ReadWrite>je příkladem takové speciální hodnoty.</span><span class="sxs-lookup"><span data-stu-id="ba31f-151"><xref:System.IO.FileAccess.ReadWrite> is an example of such a special value.</span></span>

<span data-ttu-id="ba31f-152">❌Vyhněte se vytváření výčtů příznaků, kde jsou určité kombinace hodnot neplatné.</span><span class="sxs-lookup"><span data-stu-id="ba31f-152">❌ AVOID creating flag enums where certain combinations of values are invalid.</span></span>

<span data-ttu-id="ba31f-153">❌Vyhněte se použití hodnot výčtu příznak nula, pokud hodnota nepředstavuje "všechny příznaky jsou vymazány" a je pojmenována správně, jak je předepsáno v další části.</span><span class="sxs-lookup"><span data-stu-id="ba31f-153">❌ AVOID using flag enum values of zero unless the value represents "all flags are cleared" and is named appropriately, as prescribed by the next guideline.</span></span>

<span data-ttu-id="ba31f-154">✔️ pojmenovat nulovou hodnotu výčtů příznaků `None` .</span><span class="sxs-lookup"><span data-stu-id="ba31f-154">✔️ DO name the zero value of flag enums `None`.</span></span> <span data-ttu-id="ba31f-155">U výčtu příznaků hodnota musí vždy znamenat "všechny příznaky jsou vymazány".</span><span class="sxs-lookup"><span data-stu-id="ba31f-155">For a flag enum, the value must always mean "all flags are cleared."</span></span>

<a name="add_value"></a>

### <a name="adding-value-to-enums"></a><span data-ttu-id="ba31f-156">Přidání hodnoty do výčtů</span><span class="sxs-lookup"><span data-stu-id="ba31f-156">Adding Value to Enums</span></span>

<span data-ttu-id="ba31f-157">Je velmi běžné zjistit, že je třeba přidat hodnoty do výčtu po jeho odeslání.</span><span class="sxs-lookup"><span data-stu-id="ba31f-157">It is very common to discover that you need to add values to an enum after you have already shipped it.</span></span> <span data-ttu-id="ba31f-158">Při vrácení nově přidané hodnoty z existujícího rozhraní API dojde k potenciálnímu problému s kompatibilitou aplikací, protože špatně zapsané aplikace nemusí správně zpracovat novou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="ba31f-158">There is a potential application compatibility problem when the newly added value is returned from an existing API, because poorly written applications might not handle the new value correctly.</span></span>

<span data-ttu-id="ba31f-159">✔️ Zvažte přidání hodnot do výčtů bez ohledu na malé riziko kompatibility.</span><span class="sxs-lookup"><span data-stu-id="ba31f-159">✔️ CONSIDER adding values to enums, despite a small compatibility risk.</span></span>

<span data-ttu-id="ba31f-160">Pokud máte skutečná data týkající se nekompatibility aplikací způsobená přídavky výčtu, zvažte přidání nového rozhraní API, které vrátí nové a staré hodnoty, a vyřadí staré rozhraní API, které by mělo pokračovat v vracení pouze starých hodnot.</span><span class="sxs-lookup"><span data-stu-id="ba31f-160">If you have real data about application incompatibilities caused by additions to an enum, consider adding a new API that returns the new and old values, and deprecate the old API, which should continue returning just the old values.</span></span> <span data-ttu-id="ba31f-161">Tím zajistíte, že vaše existující aplikace budou kompatibilní.</span><span class="sxs-lookup"><span data-stu-id="ba31f-161">This will ensure that your existing applications remain compatible.</span></span>

<span data-ttu-id="ba31f-162">*Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*</span><span class="sxs-lookup"><span data-stu-id="ba31f-162">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

<span data-ttu-id="ba31f-163">*Přetištěno oprávněním Pearsonova vzdělávání, Inc. z [pokynů pro návrh rozhraní: konvence, idiomy a vzory pro opakovaně použitelné knihovny .NET, druhá edice](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) od Krzysztof Cwalina a Brad Abrams, publikovaly 22. října 2008 Addison-Wesley Professional jako součást sady Microsoft Windows Development Series.*</span><span class="sxs-lookup"><span data-stu-id="ba31f-163">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="ba31f-164">Viz také</span><span class="sxs-lookup"><span data-stu-id="ba31f-164">See also</span></span>

- [<span data-ttu-id="ba31f-165">Pokyny pro návrh typů</span><span class="sxs-lookup"><span data-stu-id="ba31f-165">Type Design Guidelines</span></span>](type.md)
- [<span data-ttu-id="ba31f-166">Pokyny k návrhu architektury</span><span class="sxs-lookup"><span data-stu-id="ba31f-166">Framework Design Guidelines</span></span>](index.md)
