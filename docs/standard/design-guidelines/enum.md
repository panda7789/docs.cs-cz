---
title: Návrh výčtu
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- type design guidelines, enumerations
- simple enumerations
- enumerations [.NET Framework], design guidelines
- class library design guidelines [.NET Framework], enumerations
- flags enumerations
ms.assetid: dd53c952-9d9a-4736-86ff-9540e815d545
ms.openlocfilehash: 130e9b4e7f8d7076d1dc3f21f51dc07a68799bbe
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709449"
---
# <a name="enum-design"></a><span data-ttu-id="71d2e-102">Návrh výčtu</span><span class="sxs-lookup"><span data-stu-id="71d2e-102">Enum Design</span></span>

<span data-ttu-id="71d2e-103">Výčty jsou speciálním druhem hodnotového typu.</span><span class="sxs-lookup"><span data-stu-id="71d2e-103">Enums are a special kind of value type.</span></span> <span data-ttu-id="71d2e-104">Existují dva druhy výčtů: jednoduché výčty a výčty příznaku.</span><span class="sxs-lookup"><span data-stu-id="71d2e-104">There are two kinds of enums: simple enums and flag enums.</span></span>

<span data-ttu-id="71d2e-105">Jednoduché výčty reprezentují malé uzavřené sady možností.</span><span class="sxs-lookup"><span data-stu-id="71d2e-105">Simple enums represent small closed sets of choices.</span></span> <span data-ttu-id="71d2e-106">Běžným příkladem jednoduchého výčtu je sada barev.</span><span class="sxs-lookup"><span data-stu-id="71d2e-106">A common example of the simple enum is a set of colors.</span></span>

<span data-ttu-id="71d2e-107">Výčty příznaků jsou navržené tak, aby podporovaly bitové operace s hodnotami výčtu.</span><span class="sxs-lookup"><span data-stu-id="71d2e-107">Flag enums are designed to support bitwise operations on the enum values.</span></span> <span data-ttu-id="71d2e-108">Běžným příkladem výčtu příznaků je seznam možností.</span><span class="sxs-lookup"><span data-stu-id="71d2e-108">A common example of the flags enum is a list of options.</span></span>

<span data-ttu-id="71d2e-109">**✓ DO** pomocí výčet parametry, vlastnosti, silného typu a návratové hodnoty, které představují sadu hodnot.</span><span class="sxs-lookup"><span data-stu-id="71d2e-109">**✓ DO** use an enum to strongly type parameters, properties, and return values that represent sets of values.</span></span>

<span data-ttu-id="71d2e-110">**✓ DO** upřednostnit pomocí výčet místo statické konstanty.</span><span class="sxs-lookup"><span data-stu-id="71d2e-110">**✓ DO** favor using an enum instead of static constants.</span></span>

<span data-ttu-id="71d2e-111">**X DO NOT** používat výčet pro otevřené sady (například verzi operačního systému, názvy přátel, atd.).</span><span class="sxs-lookup"><span data-stu-id="71d2e-111">**X DO NOT** use an enum for open sets (such as the operating system version, names of your friends, etc.).</span></span>

<span data-ttu-id="71d2e-112">**X DO NOT** poskytují vyhrazené výčet hodnot, které jsou určené pro budoucí použití.</span><span class="sxs-lookup"><span data-stu-id="71d2e-112">**X DO NOT** provide reserved enum values that are intended for future use.</span></span>

<span data-ttu-id="71d2e-113">V pozdější fázi můžete kdykoli jednoduše přidat hodnoty do stávajícího výčtu.</span><span class="sxs-lookup"><span data-stu-id="71d2e-113">You can always simply add values to the existing enum at a later stage.</span></span> <span data-ttu-id="71d2e-114">Další podrobnosti o přidávání hodnot do výčtů naleznete v tématu [Přidání hodnot do výčtů](#add_value) .</span><span class="sxs-lookup"><span data-stu-id="71d2e-114">See [Adding Values to Enums](#add_value) for more details on adding values to enums.</span></span> <span data-ttu-id="71d2e-115">Rezervované hodnoty jenom zneznečišťující sadu skutečných hodnot a mají za následek chyby uživatelů.</span><span class="sxs-lookup"><span data-stu-id="71d2e-115">Reserved values just pollute the set of real values and tend to lead to user errors.</span></span>

<span data-ttu-id="71d2e-116">**X AVOID** veřejně vystavení výčty pomocí pouze jednu hodnotu.</span><span class="sxs-lookup"><span data-stu-id="71d2e-116">**X AVOID** publicly exposing enums with only one value.</span></span>

<span data-ttu-id="71d2e-117">Běžný postup pro zajištění budoucí rozšiřitelnosti rozhraní API jazyka C je přidání rezervovaných parametrů k podpisům metod.</span><span class="sxs-lookup"><span data-stu-id="71d2e-117">A common practice for ensuring future extensibility of C APIs is to add reserved parameters to method signatures.</span></span> <span data-ttu-id="71d2e-118">Tyto vyhrazené parametry lze vyjádřit jako výčty s jednou výchozí hodnotou.</span><span class="sxs-lookup"><span data-stu-id="71d2e-118">Such reserved parameters can be expressed as enums with a single default value.</span></span> <span data-ttu-id="71d2e-119">To by nemělo být provedeno ve spravovaných rozhraních API.</span><span class="sxs-lookup"><span data-stu-id="71d2e-119">This should not be done in managed APIs.</span></span> <span data-ttu-id="71d2e-120">Přetížení metody umožňuje přidávání parametrů v budoucích verzích.</span><span class="sxs-lookup"><span data-stu-id="71d2e-120">Method overloading allows adding parameters in future releases.</span></span>

<span data-ttu-id="71d2e-121">**X DO NOT** zahrnout sentinel hodnoty výčty.</span><span class="sxs-lookup"><span data-stu-id="71d2e-121">**X DO NOT** include sentinel values in enums.</span></span>

<span data-ttu-id="71d2e-122">I když jsou někdy užitečné pro vývojáře architektury, hodnoty Sentinel jsou pro uživatele rozhraní matoucí.</span><span class="sxs-lookup"><span data-stu-id="71d2e-122">Although they are sometimes helpful to framework developers, sentinel values are confusing to users of the framework.</span></span> <span data-ttu-id="71d2e-123">Používají se ke sledování stavu výčtu, nikoli k jedné z hodnot ze sady reprezentované výčtem.</span><span class="sxs-lookup"><span data-stu-id="71d2e-123">They are used to track the state of the enum rather than being one of the values from the set represented by the enum.</span></span>

<span data-ttu-id="71d2e-124">**✓ DO** zadejte hodnotu nula na jednoduchý výčty.</span><span class="sxs-lookup"><span data-stu-id="71d2e-124">**✓ DO** provide a value of zero on simple enums.</span></span>

<span data-ttu-id="71d2e-125">Zvažte volání hodnoty jako "none".</span><span class="sxs-lookup"><span data-stu-id="71d2e-125">Consider calling the value something like "None."</span></span> <span data-ttu-id="71d2e-126">Pokud taková hodnota není vhodná pro tento konkrétní výčet, měla by být většině běžných výchozích hodnot výčtu přiřazena základní hodnota nula.</span><span class="sxs-lookup"><span data-stu-id="71d2e-126">If such a value is not appropriate for this particular enum, the most common default value for the enum should be assigned the underlying value of zero.</span></span>

<span data-ttu-id="71d2e-127">**✓ CONSIDER** pomocí <xref:System.Int32> (výchozí ve většině programovacích jazycích) jako nadřazený typ enum Pokud žádné z následujících:</span><span class="sxs-lookup"><span data-stu-id="71d2e-127">**✓ CONSIDER** using <xref:System.Int32> (the default in most programming languages) as the underlying type of an enum unless any of the following is true:</span></span>

- <span data-ttu-id="71d2e-128">Výčtový typ je výčet příznaků a máte více než 32 příznaků nebo v budoucnu očekávat větší hodnotu.</span><span class="sxs-lookup"><span data-stu-id="71d2e-128">The enum is a flags enum and you have more than 32 flags, or expect to have more in the future.</span></span>

- <span data-ttu-id="71d2e-129">Podkladový typ musí být jiný než <xref:System.Int32> pro snazší interoperabilitu s nespravovaným kódem očekává v různých velikostech výčty.</span><span class="sxs-lookup"><span data-stu-id="71d2e-129">The underlying type needs to be different than <xref:System.Int32> for easier interoperability with unmanaged code expecting different-size enums.</span></span>

- <span data-ttu-id="71d2e-130">Menší nadřízený typ by způsobil značnou úsporu místa.</span><span class="sxs-lookup"><span data-stu-id="71d2e-130">A smaller underlying type would result in substantial savings in space.</span></span> <span data-ttu-id="71d2e-131">Pokud očekáváte, že se má výčet použít hlavně jako argument pro tok řízení, velikost bude mít malý rozdíl.</span><span class="sxs-lookup"><span data-stu-id="71d2e-131">If you expect the enum to be used mainly as an argument for flow of control, the size makes little difference.</span></span> <span data-ttu-id="71d2e-132">Úspora velikosti může být významná v těchto případech:</span><span class="sxs-lookup"><span data-stu-id="71d2e-132">The size savings might be significant if:</span></span>

  - <span data-ttu-id="71d2e-133">Očekáváte, že se výčet použije jako pole ve velmi často se instanci struktury nebo třídy.</span><span class="sxs-lookup"><span data-stu-id="71d2e-133">You expect the enum to be used as a field in a very frequently instantiated structure or class.</span></span>

  - <span data-ttu-id="71d2e-134">Očekáváte, že uživatelé budou vytvářet velká pole nebo kolekce instancí výčtu.</span><span class="sxs-lookup"><span data-stu-id="71d2e-134">You expect users to create large arrays or collections of the enum instances.</span></span>

  - <span data-ttu-id="71d2e-135">Očekáváte, že se má serializovat velký počet instancí výčtu.</span><span class="sxs-lookup"><span data-stu-id="71d2e-135">You expect a large number of instances of the enum to be serialized.</span></span>

<span data-ttu-id="71d2e-136">V případě využití v paměti si uvědomte, že spravované objekty jsou vždycky `DWORD`zarovnané, takže v instanci efektivně potřebujete víc výčtů nebo jiných malých struktur, aby bylo možné vytvořit rozdíl, protože celková velikost instance se vždycky zaokrouhluje na `DWORD`.</span><span class="sxs-lookup"><span data-stu-id="71d2e-136">For in-memory usage, be aware that managed objects are always `DWORD`-aligned, so you effectively need multiple enums or other small structures in an instance to pack a smaller enum with in order to make a difference, because the total instance size is always going to be rounded up to a `DWORD`.</span></span>

<span data-ttu-id="71d2e-137">**✓ DO** název příznak výčty pomocí množném čísle podstatná jména či fráze podstatné jméno a jednoduchý výčty pomocí singulární podstatná jména či fráze podstatné jméno.</span><span class="sxs-lookup"><span data-stu-id="71d2e-137">**✓ DO** name flag enums with plural nouns or noun phrases and simple enums with singular nouns or noun phrases.</span></span>

<span data-ttu-id="71d2e-138">**X DO NOT** rozšířit <xref:System.Enum?displayProperty=nameWithType> přímo.</span><span class="sxs-lookup"><span data-stu-id="71d2e-138">**X DO NOT** extend <xref:System.Enum?displayProperty=nameWithType> directly.</span></span>

<span data-ttu-id="71d2e-139"><xref:System.Enum?displayProperty=nameWithType> je speciální typ používaný modulem CLR k vytváření výčtů definovaných uživatelem.</span><span class="sxs-lookup"><span data-stu-id="71d2e-139"><xref:System.Enum?displayProperty=nameWithType> is a special type used by the CLR to create user-defined enumerations.</span></span> <span data-ttu-id="71d2e-140">Většina programovacích jazyků poskytuje programovací prvek, který vám dává přístup k této funkci.</span><span class="sxs-lookup"><span data-stu-id="71d2e-140">Most programming languages provide a programming element that gives you access to this functionality.</span></span> <span data-ttu-id="71d2e-141">Například v C# klíčovém slově `enum` slouží k definování výčtu.</span><span class="sxs-lookup"><span data-stu-id="71d2e-141">For example, in C# the `enum` keyword is used to define an enumeration.</span></span>

<a name="design"></a>

### <a name="designing-flag-enums"></a><span data-ttu-id="71d2e-142">Navrhování výčtů příznaků</span><span class="sxs-lookup"><span data-stu-id="71d2e-142">Designing Flag Enums</span></span>

<span data-ttu-id="71d2e-143">**✓ DO** použít <xref:System.FlagsAttribute?displayProperty=nameWithType> na příznak výčty.</span><span class="sxs-lookup"><span data-stu-id="71d2e-143">**✓ DO** apply the <xref:System.FlagsAttribute?displayProperty=nameWithType> to flag enums.</span></span> <span data-ttu-id="71d2e-144">Nepoužívejte tento atribut pro jednoduché výčty.</span><span class="sxs-lookup"><span data-stu-id="71d2e-144">Do not apply this attribute to simple enums.</span></span>

<span data-ttu-id="71d2e-145">**✓ DO** použít zajišťuje dva pro hodnoty výčtu příznak, mohou být volně kombinovány pomocí bitové operace OR.</span><span class="sxs-lookup"><span data-stu-id="71d2e-145">**✓ DO** use powers of two for the flag enum values so they can be freely combined using the bitwise OR operation.</span></span>

<span data-ttu-id="71d2e-146">**✓ CONSIDER** poskytování hodnot speciální výčtu pro běžně používá kombinace příznaků.</span><span class="sxs-lookup"><span data-stu-id="71d2e-146">**✓ CONSIDER** providing special enum values for commonly used combinations of flags.</span></span>

<span data-ttu-id="71d2e-147">Bitové operace jsou pokročilým konceptem a neměly by se vyžadovat pro jednoduché úlohy.</span><span class="sxs-lookup"><span data-stu-id="71d2e-147">Bitwise operations are an advanced concept and should not be required for simple tasks.</span></span> <span data-ttu-id="71d2e-148"><xref:System.IO.FileAccess.ReadWrite> je příkladem takové speciální hodnoty.</span><span class="sxs-lookup"><span data-stu-id="71d2e-148"><xref:System.IO.FileAccess.ReadWrite> is an example of such a special value.</span></span>

<span data-ttu-id="71d2e-149">**X AVOID** vytváření výčtů příznak, kde jsou neplatné určité kombinace hodnot.</span><span class="sxs-lookup"><span data-stu-id="71d2e-149">**X AVOID** creating flag enums where certain combinations of values are invalid.</span></span>

<span data-ttu-id="71d2e-150">**X AVOID** pomocí příznak hodnoty výčtu nula, pokud hodnota představuje "všechny příznaky jsou vymazány" a je správně podle další obecné zásady s názvem.</span><span class="sxs-lookup"><span data-stu-id="71d2e-150">**X AVOID** using flag enum values of zero unless the value represents "all flags are cleared" and is named appropriately, as prescribed by the next guideline.</span></span>

<span data-ttu-id="71d2e-151">**✓ DO** název nulové hodnoty příznak výčtů `None`.</span><span class="sxs-lookup"><span data-stu-id="71d2e-151">**✓ DO** name the zero value of flag enums `None`.</span></span> <span data-ttu-id="71d2e-152">U výčtu příznaků hodnota musí vždy znamenat "všechny příznaky jsou vymazány".</span><span class="sxs-lookup"><span data-stu-id="71d2e-152">For a flag enum, the value must always mean "all flags are cleared."</span></span>

<a name="add_value"></a>

### <a name="adding-value-to-enums"></a><span data-ttu-id="71d2e-153">Přidání hodnoty do výčtů</span><span class="sxs-lookup"><span data-stu-id="71d2e-153">Adding Value to Enums</span></span>

<span data-ttu-id="71d2e-154">Je velmi běžné zjistit, že je třeba přidat hodnoty do výčtu po jeho odeslání.</span><span class="sxs-lookup"><span data-stu-id="71d2e-154">It is very common to discover that you need to add values to an enum after you have already shipped it.</span></span> <span data-ttu-id="71d2e-155">Při vrácení nově přidané hodnoty z existujícího rozhraní API dojde k potenciálnímu problému s kompatibilitou aplikací, protože špatně zapsané aplikace nemusí správně zpracovat novou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="71d2e-155">There is a potential application compatibility problem when the newly added value is returned from an existing API, because poorly written applications might not handle the new value correctly.</span></span>

<span data-ttu-id="71d2e-156">**✓ CONSIDER** přidání hodnot do výčty navzdory riziko malé kompatibility.</span><span class="sxs-lookup"><span data-stu-id="71d2e-156">**✓ CONSIDER** adding values to enums, despite a small compatibility risk.</span></span>

<span data-ttu-id="71d2e-157">Pokud máte skutečná data týkající se nekompatibility aplikací způsobená přídavky výčtu, zvažte přidání nového rozhraní API, které vrátí nové a staré hodnoty, a vyřadí staré rozhraní API, které by mělo pokračovat v vracení pouze starých hodnot.</span><span class="sxs-lookup"><span data-stu-id="71d2e-157">If you have real data about application incompatibilities caused by additions to an enum, consider adding a new API that returns the new and old values, and deprecate the old API, which should continue returning just the old values.</span></span> <span data-ttu-id="71d2e-158">Tím zajistíte, že vaše existující aplikace budou kompatibilní.</span><span class="sxs-lookup"><span data-stu-id="71d2e-158">This will ensure that your existing applications remain compatible.</span></span>

<span data-ttu-id="71d2e-159">*Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*</span><span class="sxs-lookup"><span data-stu-id="71d2e-159">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

<span data-ttu-id="71d2e-160">*Přetištěno oprávněním Pearsonova vzdělávání, Inc. z [pokynů pro návrh rozhraní: konvence, idiomy a vzory pro opakovaně použitelné knihovny .NET, druhá edice](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) od Krzysztof Cwalina a Brad Abrams, publikovaly 22. října 2008 Addison-Wesley Professional jako součást sady Microsoft Windows Development Series.*</span><span class="sxs-lookup"><span data-stu-id="71d2e-160">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="71d2e-161">Viz také:</span><span class="sxs-lookup"><span data-stu-id="71d2e-161">See also</span></span>

- [<span data-ttu-id="71d2e-162">Pokyny k návrhu typu</span><span class="sxs-lookup"><span data-stu-id="71d2e-162">Type Design Guidelines</span></span>](../../../docs/standard/design-guidelines/type.md)
- [<span data-ttu-id="71d2e-163">Pokyny k návrhu architektury</span><span class="sxs-lookup"><span data-stu-id="71d2e-163">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
