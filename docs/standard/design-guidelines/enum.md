---
title: Návrh výčtu
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- type design guidelines, enumerations
- simple enumerations
- enumerations [.NET Framework], design guidelines
- class library design guidelines [.NET Framework], enumerations
- flags enumerations
ms.assetid: dd53c952-9d9a-4736-86ff-9540e815d545
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9dea187b5f3911114e551d640e0bb0aa6fac1143
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44137210"
---
# <a name="enum-design"></a><span data-ttu-id="9f2be-102">Návrh výčtu</span><span class="sxs-lookup"><span data-stu-id="9f2be-102">Enum Design</span></span>
<span data-ttu-id="9f2be-103">Výčty jsou zvláštní druh typu hodnoty.</span><span class="sxs-lookup"><span data-stu-id="9f2be-103">Enums are a special kind of value type.</span></span> <span data-ttu-id="9f2be-104">Existují dva typy výčtů: jednoduchý, výčty a příznak výčty.</span><span class="sxs-lookup"><span data-stu-id="9f2be-104">There are two kinds of enums: simple enums and flag enums.</span></span>  
  
 <span data-ttu-id="9f2be-105">Jednoduché výčty představují malé uzavřených sad možností.</span><span class="sxs-lookup"><span data-stu-id="9f2be-105">Simple enums represent small closed sets of choices.</span></span> <span data-ttu-id="9f2be-106">Běžným příkladem jednoduché výčtu je sada barev.</span><span class="sxs-lookup"><span data-stu-id="9f2be-106">A common example of the simple enum is a set of colors.</span></span>  
  
 <span data-ttu-id="9f2be-107">Příznak výčty jsou navrženy pro podporu bitové operace s hodnotami výčtu.</span><span class="sxs-lookup"><span data-stu-id="9f2be-107">Flag enums are designed to support bitwise operations on the enum values.</span></span> <span data-ttu-id="9f2be-108">Běžným příkladem výčet příznaků je seznam možností.</span><span class="sxs-lookup"><span data-stu-id="9f2be-108">A common example of the flags enum is a list of options.</span></span>  
  
 <span data-ttu-id="9f2be-109">**✓ DO** pomocí výčet parametry, vlastnosti, silného typu a návratové hodnoty, které představují sadu hodnot.</span><span class="sxs-lookup"><span data-stu-id="9f2be-109">**✓ DO** use an enum to strongly type parameters, properties, and return values that represent sets of values.</span></span>  
  
 <span data-ttu-id="9f2be-110">**✓ DO** upřednostnit pomocí výčet místo statické konstanty.</span><span class="sxs-lookup"><span data-stu-id="9f2be-110">**✓ DO** favor using an enum instead of static constants.</span></span>  
  
 <span data-ttu-id="9f2be-111">**X DO NOT** používat výčet pro otevřené sady (například verzi operačního systému, názvy přátel, atd.).</span><span class="sxs-lookup"><span data-stu-id="9f2be-111">**X DO NOT** use an enum for open sets (such as the operating system version, names of your friends, etc.).</span></span>  
  
 <span data-ttu-id="9f2be-112">**X DO NOT** poskytují vyhrazené výčet hodnot, které jsou určené pro budoucí použití.</span><span class="sxs-lookup"><span data-stu-id="9f2be-112">**X DO NOT** provide reserved enum values that are intended for future use.</span></span>  
  
 <span data-ttu-id="9f2be-113">V pozdější fázi můžete vždy jednoduše přidejte hodnoty pro existující výčet.</span><span class="sxs-lookup"><span data-stu-id="9f2be-113">You can always simply add values to the existing enum at a later stage.</span></span> <span data-ttu-id="9f2be-114">Zobrazit [přidání hodnoty výčty](#add_value) podrobné informace o přidání hodnot do výčty.</span><span class="sxs-lookup"><span data-stu-id="9f2be-114">See [Adding Values to Enums](#add_value) for more details on adding values to enums.</span></span> <span data-ttu-id="9f2be-115">Vyhrazené hodnoty stačí znečištění směrovány správu sadu skutečných hodnot a vede k chybám uživatelů.</span><span class="sxs-lookup"><span data-stu-id="9f2be-115">Reserved values just pollute the set of real values and tend to lead to user errors.</span></span>  
  
 <span data-ttu-id="9f2be-116">**X AVOID** veřejně vystavení výčty pomocí pouze jednu hodnotu.</span><span class="sxs-lookup"><span data-stu-id="9f2be-116">**X AVOID** publicly exposing enums with only one value.</span></span>  
  
 <span data-ttu-id="9f2be-117">Běžnou praxí pro zajištění budoucí rozšíření rozhraní API jazyka C je přidání vyhrazené parametry podpisy metod.</span><span class="sxs-lookup"><span data-stu-id="9f2be-117">A common practice for ensuring future extensibility of C APIs is to add reserved parameters to method signatures.</span></span> <span data-ttu-id="9f2be-118">Tyto parametry vyhrazené může být vyjádřený jako výčty pomocí jedno výchozí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="9f2be-118">Such reserved parameters can be expressed as enums with a single default value.</span></span> <span data-ttu-id="9f2be-119">To by neměl být spravovaných rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="9f2be-119">This should not be done in managed APIs.</span></span> <span data-ttu-id="9f2be-120">Metoda přetížení umožňuje přidávání parametrů v budoucích vezích se.</span><span class="sxs-lookup"><span data-stu-id="9f2be-120">Method overloading allows adding parameters in future releases.</span></span>  
  
 <span data-ttu-id="9f2be-121">**X DO NOT** zahrnout sentinel hodnoty výčty.</span><span class="sxs-lookup"><span data-stu-id="9f2be-121">**X DO NOT** include sentinel values in enums.</span></span>  
  
 <span data-ttu-id="9f2be-122">I když jsou někdy užitečné pro vývojáře rozhraní framework, sentinel hodnoty jsou matoucí pro uživatele tohoto rozhraní.</span><span class="sxs-lookup"><span data-stu-id="9f2be-122">Although they are sometimes helpful to framework developers, sentinel values are confusing to users of the framework.</span></span> <span data-ttu-id="9f2be-123">Používají se ke sledování stavu je jedna z hodnot výčtu spíše než ze sady reprezentována výčtového typu.</span><span class="sxs-lookup"><span data-stu-id="9f2be-123">They are used to track the state of the enum rather than being one of the values from the set represented by the enum.</span></span>  
  
 <span data-ttu-id="9f2be-124">**✓ DO** zadejte hodnotu nula na jednoduchý výčty.</span><span class="sxs-lookup"><span data-stu-id="9f2be-124">**✓ DO** provide a value of zero on simple enums.</span></span>  
  
 <span data-ttu-id="9f2be-125">Zvažte možnost volání hodnotu něco jako "None".</span><span class="sxs-lookup"><span data-stu-id="9f2be-125">Consider calling the value something like "None."</span></span> <span data-ttu-id="9f2be-126">Pokud taková hodnota není vhodná pro tento konkrétní výčet, měla být přiřazena základní hodnotou nula nejběžnější výchozí hodnota pro výčet.</span><span class="sxs-lookup"><span data-stu-id="9f2be-126">If such a value is not appropriate for this particular enum, the most common default value for the enum should be assigned the underlying value of zero.</span></span>  
  
 <span data-ttu-id="9f2be-127">**✓ CONSIDER** pomocí <xref:System.Int32> (výchozí ve většině programovacích jazycích) jako nadřazený typ enum Pokud žádné z následujících:</span><span class="sxs-lookup"><span data-stu-id="9f2be-127">**✓ CONSIDER** using <xref:System.Int32> (the default in most programming languages) as the underlying type of an enum unless any of the following is true:</span></span>  
  
-   <span data-ttu-id="9f2be-128">Výčet je výčet příznaků a máte více než 32 příznaky, nebo chcete mít více v budoucnu.</span><span class="sxs-lookup"><span data-stu-id="9f2be-128">The enum is a flags enum and you have more than 32 flags, or expect to have more in the future.</span></span>  
  
-   <span data-ttu-id="9f2be-129">Základní typ musí být jiná než <xref:System.Int32> jednodušší spolupráce s nespravovaným kódem očekává jinou velikost výčty.</span><span class="sxs-lookup"><span data-stu-id="9f2be-129">The underlying type needs to be different than <xref:System.Int32> for easier interoperability with unmanaged code expecting different-size enums.</span></span>  
  
-   <span data-ttu-id="9f2be-130">Výsledkem by bylo menší základní typ značné úspory v prostoru.</span><span class="sxs-lookup"><span data-stu-id="9f2be-130">A smaller underlying type would result in substantial savings in space.</span></span> <span data-ttu-id="9f2be-131">Pokud očekáváte, že výčtu použije hlavně jako argument pro tok řízení, velikost provede malý rozdíl.</span><span class="sxs-lookup"><span data-stu-id="9f2be-131">If you expect the enum to be used mainly as an argument for flow of control, the size makes little difference.</span></span> <span data-ttu-id="9f2be-132">Úspora velikosti může být významné pokud:</span><span class="sxs-lookup"><span data-stu-id="9f2be-132">The size savings might be significant if:</span></span>  
  
    -   <span data-ttu-id="9f2be-133">Očekáváte, že se použije jako pole instance velmi často struktury nebo třídy výčtu.</span><span class="sxs-lookup"><span data-stu-id="9f2be-133">You expect the enum to be used as a field in a very frequently instantiated structure or class.</span></span>  
  
    -   <span data-ttu-id="9f2be-134">Očekáváte, že uživatelům vytvořit velké pole nebo kolekce výčet instancí.</span><span class="sxs-lookup"><span data-stu-id="9f2be-134">You expect users to create large arrays or collections of the enum instances.</span></span>  
  
    -   <span data-ttu-id="9f2be-135">Očekáváte velký počet instancí výčtového typu se musí serializovat.</span><span class="sxs-lookup"><span data-stu-id="9f2be-135">You expect a large number of instances of the enum to be serialized.</span></span>  
  
 <span data-ttu-id="9f2be-136">Pro použití v paměti, mějte na paměti, že spravované objekty budou vždy `DWORD`-zarovnané, tak efektivně potřebujete více výčty nebo jiných malých struktury v instanci se zabalit menší výčet s aby rozdíl, protože velikost celkový počet instancí je vždy má zaokrouhlí `DWORD`.</span><span class="sxs-lookup"><span data-stu-id="9f2be-136">For in-memory usage, be aware that managed objects are always `DWORD`-aligned, so you effectively need multiple enums or other small structures in an instance to pack a smaller enum with in order to make a difference, because the total instance size is always going to be rounded up to a `DWORD`.</span></span>  
  
 <span data-ttu-id="9f2be-137">**✓ DO** název příznak výčty pomocí množném čísle podstatná jména či fráze podstatné jméno a jednoduchý výčty pomocí singulární podstatná jména či fráze podstatné jméno.</span><span class="sxs-lookup"><span data-stu-id="9f2be-137">**✓ DO** name flag enums with plural nouns or noun phrases and simple enums with singular nouns or noun phrases.</span></span>  
  
 <span data-ttu-id="9f2be-138">**X DO NOT** rozšířit <xref:System.Enum?displayProperty=nameWithType> přímo.</span><span class="sxs-lookup"><span data-stu-id="9f2be-138">**X DO NOT** extend <xref:System.Enum?displayProperty=nameWithType> directly.</span></span>  
  
 <span data-ttu-id="9f2be-139"><xref:System.Enum?displayProperty=nameWithType> je speciální typ používá modul CLR k vytvoření uživatelem definované výčty.</span><span class="sxs-lookup"><span data-stu-id="9f2be-139"><xref:System.Enum?displayProperty=nameWithType> is a special type used by the CLR to create user-defined enumerations.</span></span> <span data-ttu-id="9f2be-140">Většina programovacích jazyků poskytují programový element, který poskytuje přístup k této funkci.</span><span class="sxs-lookup"><span data-stu-id="9f2be-140">Most programming languages provide a programming element that gives you access to this functionality.</span></span> <span data-ttu-id="9f2be-141">Například v jazyce C# `enum` – klíčové slovo se používá k definování výčtu.</span><span class="sxs-lookup"><span data-stu-id="9f2be-141">For example, in C# the `enum` keyword is used to define an enumeration.</span></span>  
  
<a name="design"></a>   
### <a name="designing-flag-enums"></a><span data-ttu-id="9f2be-142">Navrhování příznak výčty</span><span class="sxs-lookup"><span data-stu-id="9f2be-142">Designing Flag Enums</span></span>  
 <span data-ttu-id="9f2be-143">**✓ DO** použít <xref:System.FlagsAttribute?displayProperty=nameWithType> na příznak výčty.</span><span class="sxs-lookup"><span data-stu-id="9f2be-143">**✓ DO** apply the <xref:System.FlagsAttribute?displayProperty=nameWithType> to flag enums.</span></span> <span data-ttu-id="9f2be-144">Tento atribut nevztahují na jednoduché výčty.</span><span class="sxs-lookup"><span data-stu-id="9f2be-144">Do not apply this attribute to simple enums.</span></span>  
  
 <span data-ttu-id="9f2be-145">**✓ DO** použít zajišťuje dva pro hodnoty výčtu příznak, mohou být volně kombinovány pomocí bitové operace OR.</span><span class="sxs-lookup"><span data-stu-id="9f2be-145">**✓ DO** use powers of two for the flag enum values so they can be freely combined using the bitwise OR operation.</span></span>  
  
 <span data-ttu-id="9f2be-146">**✓ CONSIDER** poskytování hodnot speciální výčtu pro běžně používá kombinace příznaků.</span><span class="sxs-lookup"><span data-stu-id="9f2be-146">**✓ CONSIDER** providing special enum values for commonly used combinations of flags.</span></span>  
  
 <span data-ttu-id="9f2be-147">Bitové operace jsou rozšířené koncept a by neměla být zapotřebí pro jednoduché úlohy.</span><span class="sxs-lookup"><span data-stu-id="9f2be-147">Bitwise operations are an advanced concept and should not be required for simple tasks.</span></span> <span data-ttu-id="9f2be-148"><xref:System.IO.FileAccess.ReadWrite> je příkladem zvláštní hodnota.</span><span class="sxs-lookup"><span data-stu-id="9f2be-148"><xref:System.IO.FileAccess.ReadWrite> is an example of such a special value.</span></span>  
  
 <span data-ttu-id="9f2be-149">**X AVOID** vytváření výčtů příznak, kde jsou neplatné určité kombinace hodnot.</span><span class="sxs-lookup"><span data-stu-id="9f2be-149">**X AVOID** creating flag enums where certain combinations of values are invalid.</span></span>  
  
 <span data-ttu-id="9f2be-150">**X AVOID** pomocí příznak hodnoty výčtu nula, pokud hodnota představuje "všechny příznaky jsou vymazány" a je správně podle další obecné zásady s názvem.</span><span class="sxs-lookup"><span data-stu-id="9f2be-150">**X AVOID** using flag enum values of zero unless the value represents "all flags are cleared" and is named appropriately, as prescribed by the next guideline.</span></span>  
  
 <span data-ttu-id="9f2be-151">**✓ DO** název nulové hodnoty příznak výčtů `None`.</span><span class="sxs-lookup"><span data-stu-id="9f2be-151">**✓ DO** name the zero value of flag enums `None`.</span></span> <span data-ttu-id="9f2be-152">Příznak výčtu musí hodnota vždy znamená "všechny příznaky jsou vymazány."</span><span class="sxs-lookup"><span data-stu-id="9f2be-152">For a flag enum, the value must always mean "all flags are cleared."</span></span>  
  
<a name="add_value"></a>   
### <a name="adding-value-to-enums"></a><span data-ttu-id="9f2be-153">Přínos pro výčty</span><span class="sxs-lookup"><span data-stu-id="9f2be-153">Adding Value to Enums</span></span>  
 <span data-ttu-id="9f2be-154">Je velmi běžné ke zjištění, že budete muset přidat hodnoty výčtu, poté, co jste už už vydali.</span><span class="sxs-lookup"><span data-stu-id="9f2be-154">It is very common to discover that you need to add values to an enum after you have already shipped it.</span></span> <span data-ttu-id="9f2be-155">Je potenciální problémy s kompatibilitou aplikací po je nově přidaná hodnota vrácená z existujícího rozhraní API, protože špatně vytvořené aplikace nemusí správně zpracovávat nové hodnoty.</span><span class="sxs-lookup"><span data-stu-id="9f2be-155">There is a potential application compatibility problem when the newly added value is returned from an existing API, because poorly written applications might not handle the new value correctly.</span></span>  
  
 <span data-ttu-id="9f2be-156">**✓ CONSIDER** přidání hodnot do výčty navzdory riziko malé kompatibility.</span><span class="sxs-lookup"><span data-stu-id="9f2be-156">**✓ CONSIDER** adding values to enums, despite a small compatibility risk.</span></span>  
  
 <span data-ttu-id="9f2be-157">Pokud máte reálná data o nekompatibility aplikací způsobené dodatky na výčet, zvažte přidání nového rozhraní API, který vrací hodnoty novém i starém a vyřazení staré rozhraní API, které by měly pokračovat ve vrací pouze původní hodnoty.</span><span class="sxs-lookup"><span data-stu-id="9f2be-157">If you have real data about application incompatibilities caused by additions to an enum, consider adding a new API that returns the new and old values, and deprecate the old API, which should continue returning just the old values.</span></span> <span data-ttu-id="9f2be-158">Tím se zajistí, že zůstane svoje stávající aplikace kompatibilní.</span><span class="sxs-lookup"><span data-stu-id="9f2be-158">This will ensure that your existing applications remain compatible.</span></span>  
  
 <span data-ttu-id="9f2be-159">*Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*</span><span class="sxs-lookup"><span data-stu-id="9f2be-159">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="9f2be-160">*Přetištěno podle oprávnění Pearson vzdělávání, Inc. z [pokyny k návrhu architektury: konvence, Idiomy a vzory pro opakovaně použitelného knihovny .NET, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Brad Abrams publikované 22 Oct 2008, Designing Effective jako části této série Microsoft Windows Development.*</span><span class="sxs-lookup"><span data-stu-id="9f2be-160">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f2be-161">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9f2be-161">See also</span></span>

- [<span data-ttu-id="9f2be-162">Pokyny k návrhu typu</span><span class="sxs-lookup"><span data-stu-id="9f2be-162">Type Design Guidelines</span></span>](../../../docs/standard/design-guidelines/type.md)  
- [<span data-ttu-id="9f2be-163">Pokyny k návrhu architektury</span><span class="sxs-lookup"><span data-stu-id="9f2be-163">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
