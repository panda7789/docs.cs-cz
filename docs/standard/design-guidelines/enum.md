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
ms.openlocfilehash: 544f617ca3a352814504125d7a61d70db5a81566
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33579246"
---
# <a name="enum-design"></a><span data-ttu-id="1006b-102">Návrh výčtu</span><span class="sxs-lookup"><span data-stu-id="1006b-102">Enum Design</span></span>
<span data-ttu-id="1006b-103">Výčty jsou zvláštní druh typ hodnoty.</span><span class="sxs-lookup"><span data-stu-id="1006b-103">Enums are a special kind of value type.</span></span> <span data-ttu-id="1006b-104">Existují dva druhy výčty: jednoduchý výčty a příznak výčty.</span><span class="sxs-lookup"><span data-stu-id="1006b-104">There are two kinds of enums: simple enums and flag enums.</span></span>  
  
 <span data-ttu-id="1006b-105">Jednoduché výčty představují malé uzavřené sady možností.</span><span class="sxs-lookup"><span data-stu-id="1006b-105">Simple enums represent small closed sets of choices.</span></span> <span data-ttu-id="1006b-106">Běžným příkladem je jednoduchý výčet je sada barev.</span><span class="sxs-lookup"><span data-stu-id="1006b-106">A common example of the simple enum is a set of colors.</span></span>  
  
 <span data-ttu-id="1006b-107">Příznak výčty jsou navrženy pro podporu bitové operace na hodnoty výčtu.</span><span class="sxs-lookup"><span data-stu-id="1006b-107">Flag enums are designed to support bitwise operations on the enum values.</span></span> <span data-ttu-id="1006b-108">Běžným příkladem je výčet příznaků je seznam možností.</span><span class="sxs-lookup"><span data-stu-id="1006b-108">A common example of the flags enum is a list of options.</span></span>  
  
 <span data-ttu-id="1006b-109">**✓ DO** pomocí výčet parametry, vlastnosti, silného typu a návratové hodnoty, které představují sadu hodnot.</span><span class="sxs-lookup"><span data-stu-id="1006b-109">**✓ DO** use an enum to strongly type parameters, properties, and return values that represent sets of values.</span></span>  
  
 <span data-ttu-id="1006b-110">**✓ DO** upřednostnit pomocí výčet místo statické konstanty.</span><span class="sxs-lookup"><span data-stu-id="1006b-110">**✓ DO** favor using an enum instead of static constants.</span></span>  
  
 <span data-ttu-id="1006b-111">**X DO NOT** používat výčet pro otevřené sady (například verzi operačního systému, názvy přátel, atd.).</span><span class="sxs-lookup"><span data-stu-id="1006b-111">**X DO NOT** use an enum for open sets (such as the operating system version, names of your friends, etc.).</span></span>  
  
 <span data-ttu-id="1006b-112">**X DO NOT** poskytují vyhrazené výčet hodnot, které jsou určené pro budoucí použití.</span><span class="sxs-lookup"><span data-stu-id="1006b-112">**X DO NOT** provide reserved enum values that are intended for future use.</span></span>  
  
 <span data-ttu-id="1006b-113">Vždy jednoduše přidáním hodnoty do existující výčtu v pozdější fázi.</span><span class="sxs-lookup"><span data-stu-id="1006b-113">You can always simply add values to the existing enum at a later stage.</span></span> <span data-ttu-id="1006b-114">V tématu [přidání hodnoty výčty](#add_value) Další informace o přidání hodnot do výčty.</span><span class="sxs-lookup"><span data-stu-id="1006b-114">See [Adding Values to Enums](#add_value) for more details on adding values to enums.</span></span> <span data-ttu-id="1006b-115">Vyhrazené hodnoty právě znečištění směrovány správu sadu skutečné hodnoty a vede k chyby uživatele.</span><span class="sxs-lookup"><span data-stu-id="1006b-115">Reserved values just pollute the set of real values and tend to lead to user errors.</span></span>  
  
 <span data-ttu-id="1006b-116">**X AVOID** veřejně vystavení výčty pomocí pouze jednu hodnotu.</span><span class="sxs-lookup"><span data-stu-id="1006b-116">**X AVOID** publicly exposing enums with only one value.</span></span>  
  
 <span data-ttu-id="1006b-117">Běžnou praxí pro zajištění budoucí rozšíření rozhraní API jazyka C je přidání vyhrazené parametrů do metoda signatur.</span><span class="sxs-lookup"><span data-stu-id="1006b-117">A common practice for ensuring future extensibility of C APIs is to add reserved parameters to method signatures.</span></span> <span data-ttu-id="1006b-118">Takové vyhrazené parametry může být vyjádřený jako výčty pomocí jednoho výchozí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="1006b-118">Such reserved parameters can be expressed as enums with a single default value.</span></span> <span data-ttu-id="1006b-119">To by neměl spravované rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="1006b-119">This should not be done in managed APIs.</span></span> <span data-ttu-id="1006b-120">Přetěžování metody umožňuje přidání parametrů v budoucích vezích se.</span><span class="sxs-lookup"><span data-stu-id="1006b-120">Method overloading allows adding parameters in future releases.</span></span>  
  
 <span data-ttu-id="1006b-121">**X DO NOT** zahrnout sentinel hodnoty výčty.</span><span class="sxs-lookup"><span data-stu-id="1006b-121">**X DO NOT** include sentinel values in enums.</span></span>  
  
 <span data-ttu-id="1006b-122">I když jsou někdy jsou užitečné pro vývojáře framework, sentinel hodnoty jsou pro uživatele Framework matoucí.</span><span class="sxs-lookup"><span data-stu-id="1006b-122">Although they are sometimes helpful to framework developers, sentinel values are confusing to users of the framework.</span></span> <span data-ttu-id="1006b-123">Používají se ke sledování stavu vrácení, jedna z hodnot výčtu spíše než ze sady reprezentována výčtového typu.</span><span class="sxs-lookup"><span data-stu-id="1006b-123">They are used to track the state of the enum rather than being one of the values from the set represented by the enum.</span></span>  
  
 <span data-ttu-id="1006b-124">**✓ DO** zadejte hodnotu nula na jednoduchý výčty.</span><span class="sxs-lookup"><span data-stu-id="1006b-124">**✓ DO** provide a value of zero on simple enums.</span></span>  
  
 <span data-ttu-id="1006b-125">Zvažte možnost volání hodnota něco podobného jako "None."</span><span class="sxs-lookup"><span data-stu-id="1006b-125">Consider calling the value something like "None."</span></span> <span data-ttu-id="1006b-126">Pokud tuto hodnotu není vhodná pro tento konkrétní výčet, je vhodné nejběžnější výchozí hodnota pro výčet přiřadit základní hodnota nula.</span><span class="sxs-lookup"><span data-stu-id="1006b-126">If such a value is not appropriate for this particular enum, the most common default value for the enum should be assigned the underlying value of zero.</span></span>  
  
 <span data-ttu-id="1006b-127">**✓ CONSIDER** pomocí <xref:System.Int32> (výchozí ve většině programovacích jazycích) jako nadřazený typ enum Pokud žádné z následujících:</span><span class="sxs-lookup"><span data-stu-id="1006b-127">**✓ CONSIDER** using <xref:System.Int32> (the default in most programming languages) as the underlying type of an enum unless any of the following is true:</span></span>  
  
-   <span data-ttu-id="1006b-128">Je výčet je výčet příznaků a máte víc než 32 příznaky, nebo se očekávají, že mají více v budoucnu.</span><span class="sxs-lookup"><span data-stu-id="1006b-128">The enum is a flags enum and you have more than 32 flags, or expect to have more in the future.</span></span>  
  
-   <span data-ttu-id="1006b-129">Základní typ musí být jiný než <xref:System.Int32> jednodušší funkční spolupráce s nespravovaným kódem očekává jinou velikost výčty.</span><span class="sxs-lookup"><span data-stu-id="1006b-129">The underlying type needs to be different than <xref:System.Int32> for easier interoperability with unmanaged code expecting different-size enums.</span></span>  
  
-   <span data-ttu-id="1006b-130">Menší podkladovým typem by způsobilo významné úspory v prostoru.</span><span class="sxs-lookup"><span data-stu-id="1006b-130">A smaller underlying type would result in substantial savings in space.</span></span> <span data-ttu-id="1006b-131">Pokud očekáváte výčtu, která má být použit především jako argument pro tok řízení, velikost způsobuje malé rozdíly.</span><span class="sxs-lookup"><span data-stu-id="1006b-131">If you expect the enum to be used mainly as an argument for flow of control, the size makes little difference.</span></span> <span data-ttu-id="1006b-132">Úspora velikosti může být důležité pokud:</span><span class="sxs-lookup"><span data-stu-id="1006b-132">The size savings might be significant if:</span></span>  
  
    -   <span data-ttu-id="1006b-133">Očekáváte výčtu, která má být použit jako pole v velmi často instancí struktura nebo třída.</span><span class="sxs-lookup"><span data-stu-id="1006b-133">You expect the enum to be used as a field in a very frequently instantiated structure or class.</span></span>  
  
    -   <span data-ttu-id="1006b-134">Očekáváte uživatelům vytvářet velké pole nebo kolekce výčet instancí.</span><span class="sxs-lookup"><span data-stu-id="1006b-134">You expect users to create large arrays or collections of the enum instances.</span></span>  
  
    -   <span data-ttu-id="1006b-135">Očekáváte velký počet instancí výčtu k serializaci.</span><span class="sxs-lookup"><span data-stu-id="1006b-135">You expect a large number of instances of the enum to be serialized.</span></span>  
  
 <span data-ttu-id="1006b-136">Pro použití v paměti, uvědomte si, že spravované objekty jsou vždy `DWORD`-zarovnán, proto musíte efektivně více výčty nebo jiné malé struktury v instanci do pack menší výčtu s aby rozdíl, protože velikost celkový instance je vždy má být zaokrouhlené nahoru `DWORD`.</span><span class="sxs-lookup"><span data-stu-id="1006b-136">For in-memory usage, be aware that managed objects are always `DWORD`-aligned, so you effectively need multiple enums or other small structures in an instance to pack a smaller enum with in order to make a difference, because the total instance size is always going to be rounded up to a `DWORD`.</span></span>  
  
 <span data-ttu-id="1006b-137">**✓ DO** název příznak výčty pomocí množném čísle podstatná jména či fráze podstatné jméno a jednoduchý výčty pomocí singulární podstatná jména či fráze podstatné jméno.</span><span class="sxs-lookup"><span data-stu-id="1006b-137">**✓ DO** name flag enums with plural nouns or noun phrases and simple enums with singular nouns or noun phrases.</span></span>  
  
 <span data-ttu-id="1006b-138">**X DO NOT** rozšířit <xref:System.Enum?displayProperty=nameWithType> přímo.</span><span class="sxs-lookup"><span data-stu-id="1006b-138">**X DO NOT** extend <xref:System.Enum?displayProperty=nameWithType> directly.</span></span>  
  
 <span data-ttu-id="1006b-139"><xref:System.Enum?displayProperty=nameWithType> je speciální typ používaný službou modulu CLR vytvořit uživateli definované výčty.</span><span class="sxs-lookup"><span data-stu-id="1006b-139"><xref:System.Enum?displayProperty=nameWithType> is a special type used by the CLR to create user-defined enumerations.</span></span> <span data-ttu-id="1006b-140">Většina programovacích jazyků zadejte programovací element, který umožňuje přístup k této funkce.</span><span class="sxs-lookup"><span data-stu-id="1006b-140">Most programming languages provide a programming element that gives you access to this functionality.</span></span> <span data-ttu-id="1006b-141">Například v jazyce C# `enum` – klíčové slovo se používá k definování výčet.</span><span class="sxs-lookup"><span data-stu-id="1006b-141">For example, in C# the `enum` keyword is used to define an enumeration.</span></span>  
  
<a name="design"></a>   
### <a name="designing-flag-enums"></a><span data-ttu-id="1006b-142">Návrh příznak výčty</span><span class="sxs-lookup"><span data-stu-id="1006b-142">Designing Flag Enums</span></span>  
 <span data-ttu-id="1006b-143">**✓ DO** použít <xref:System.FlagsAttribute?displayProperty=nameWithType> na příznak výčty.</span><span class="sxs-lookup"><span data-stu-id="1006b-143">**✓ DO** apply the <xref:System.FlagsAttribute?displayProperty=nameWithType> to flag enums.</span></span> <span data-ttu-id="1006b-144">Tento atribut nevztahují na jednoduchý výčty.</span><span class="sxs-lookup"><span data-stu-id="1006b-144">Do not apply this attribute to simple enums.</span></span>  
  
 <span data-ttu-id="1006b-145">**✓ DO** použít zajišťuje dva pro hodnoty výčtu příznak, mohou být volně kombinovány pomocí bitové operace OR.</span><span class="sxs-lookup"><span data-stu-id="1006b-145">**✓ DO** use powers of two for the flag enum values so they can be freely combined using the bitwise OR operation.</span></span>  
  
 <span data-ttu-id="1006b-146">**✓ CONSIDER** poskytování hodnot speciální výčtu pro běžně používá kombinace příznaků.</span><span class="sxs-lookup"><span data-stu-id="1006b-146">**✓ CONSIDER** providing special enum values for commonly used combinations of flags.</span></span>  
  
 <span data-ttu-id="1006b-147">Bitové operace jsou rozšířené koncept a nesmí být požadovány pro jednoduché úlohy.</span><span class="sxs-lookup"><span data-stu-id="1006b-147">Bitwise operations are an advanced concept and should not be required for simple tasks.</span></span> <span data-ttu-id="1006b-148"><xref:System.IO.FileAccess.ReadWrite> je příklad speciální hodnoty.</span><span class="sxs-lookup"><span data-stu-id="1006b-148"><xref:System.IO.FileAccess.ReadWrite> is an example of such a special value.</span></span>  
  
 <span data-ttu-id="1006b-149">**X AVOID** vytváření výčtů příznak, kde jsou neplatné určité kombinace hodnot.</span><span class="sxs-lookup"><span data-stu-id="1006b-149">**X AVOID** creating flag enums where certain combinations of values are invalid.</span></span>  
  
 <span data-ttu-id="1006b-150">**X AVOID** pomocí příznak hodnoty výčtu nula, pokud hodnota představuje "všechny příznaky jsou vymazány" a je správně podle další obecné zásady s názvem.</span><span class="sxs-lookup"><span data-stu-id="1006b-150">**X AVOID** using flag enum values of zero unless the value represents "all flags are cleared" and is named appropriately, as prescribed by the next guideline.</span></span>  
  
 <span data-ttu-id="1006b-151">**✓ DO** název nulové hodnoty příznak výčtů `None`.</span><span class="sxs-lookup"><span data-stu-id="1006b-151">**✓ DO** name the zero value of flag enums `None`.</span></span> <span data-ttu-id="1006b-152">Pro příkaz enum příznak musí hodnota vždy význam "všechny příznaky jsou vymazány."</span><span class="sxs-lookup"><span data-stu-id="1006b-152">For a flag enum, the value must always mean "all flags are cleared."</span></span>  
  
<a name="add_value"></a>   
### <a name="adding-value-to-enums"></a><span data-ttu-id="1006b-153">Přidáním hodnoty pro výčty</span><span class="sxs-lookup"><span data-stu-id="1006b-153">Adding Value to Enums</span></span>  
 <span data-ttu-id="1006b-154">Je velmi běžné ke zjištění, budete muset po jste již odeslali ho přidat hodnoty výčtu.</span><span class="sxs-lookup"><span data-stu-id="1006b-154">It is very common to discover that you need to add values to an enum after you have already shipped it.</span></span> <span data-ttu-id="1006b-155">Potenciální problémy s kompatibilitou aplikací Pokud nastane je vrácena hodnota nově přidané z existujícího rozhraní API, protože chybně napsané aplikace nemusí správně zpracovat novou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="1006b-155">There is a potential application compatibility problem when the newly added value is returned from an existing API, because poorly written applications might not handle the new value correctly.</span></span>  
  
 <span data-ttu-id="1006b-156">**✓ CONSIDER** přidání hodnot do výčty navzdory riziko malé kompatibility.</span><span class="sxs-lookup"><span data-stu-id="1006b-156">**✓ CONSIDER** adding values to enums, despite a small compatibility risk.</span></span>  
  
 <span data-ttu-id="1006b-157">Pokud máte reálná data o aplikace nekompatibility způsobené doplňky výčet, zvažte přidání nového rozhraní API, který vrací hodnoty novém i starém a přestat používat staré rozhraní API, které by měly pokračovat ve vrací pouze původní hodnoty.</span><span class="sxs-lookup"><span data-stu-id="1006b-157">If you have real data about application incompatibilities caused by additions to an enum, consider adding a new API that returns the new and old values, and deprecate the old API, which should continue returning just the old values.</span></span> <span data-ttu-id="1006b-158">Tím bude zajištěno, že zůstanou existující aplikace kompatibilní.</span><span class="sxs-lookup"><span data-stu-id="1006b-158">This will ensure that your existing applications remain compatible.</span></span>  
  
 <span data-ttu-id="1006b-159">*Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*</span><span class="sxs-lookup"><span data-stu-id="1006b-159">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="1006b-160">*Provedení podle oprávnění Pearson Education, Inc. z [pokynů pro návrh Framework: konvence, Idioms a vzory pro jedno použití knihovny .NET, 2. vydání](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Abrams Brada publikovaná 22 Oct 2008 pomocí Designing Effective jako součást vývoj řady Microsoft Windows.*</span><span class="sxs-lookup"><span data-stu-id="1006b-160">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1006b-161">Viz také</span><span class="sxs-lookup"><span data-stu-id="1006b-161">See Also</span></span>  
 [<span data-ttu-id="1006b-162">Pokyny k návrhu typu</span><span class="sxs-lookup"><span data-stu-id="1006b-162">Type Design Guidelines</span></span>](../../../docs/standard/design-guidelines/type.md)  
 [<span data-ttu-id="1006b-163">Pokyny k návrhu architektury</span><span class="sxs-lookup"><span data-stu-id="1006b-163">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)
