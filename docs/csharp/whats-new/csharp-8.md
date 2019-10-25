---
title: Co je nového v C# 8,0 – C# příručka
description: Získejte přehled o nových funkcích dostupných v C# 8,0.
ms.date: 09/20/2019
ms.openlocfilehash: 335ae37b20f752f4181a4d1828cb2a1f02c0fa9e
ms.sourcegitcommit: 9bd1c09128e012b6e34bdcbdf3576379f58f3137
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2019
ms.locfileid: "72798919"
---
# <a name="whats-new-in-c-80"></a><span data-ttu-id="17ec8-103">Co je nového v C# 8,0</span><span class="sxs-lookup"><span data-stu-id="17ec8-103">What's new in C# 8.0</span></span>

<span data-ttu-id="17ec8-104">C#8,0 přidává následující funkce a vylepšení C# jazyka:</span><span class="sxs-lookup"><span data-stu-id="17ec8-104">C# 8.0 adds the following features and enhancements to the C# language:</span></span>

- [<span data-ttu-id="17ec8-105">Členové jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="17ec8-105">Readonly members</span></span>](#readonly-members)
- [<span data-ttu-id="17ec8-106">Výchozí metody rozhraní</span><span class="sxs-lookup"><span data-stu-id="17ec8-106">Default interface methods</span></span>](#default-interface-methods)
- <span data-ttu-id="17ec8-107">[Vylepšení porovnávání vzorů](#more-patterns-in-more-places):</span><span class="sxs-lookup"><span data-stu-id="17ec8-107">[Pattern matching enhancements](#more-patterns-in-more-places):</span></span>
  - [<span data-ttu-id="17ec8-108">Výrazy Switch</span><span class="sxs-lookup"><span data-stu-id="17ec8-108">Switch expressions</span></span>](#switch-expressions)
  - [<span data-ttu-id="17ec8-109">Vzory vlastností</span><span class="sxs-lookup"><span data-stu-id="17ec8-109">Property patterns</span></span>](#property-patterns)
  - [<span data-ttu-id="17ec8-110">Vzory řazené kolekce členů</span><span class="sxs-lookup"><span data-stu-id="17ec8-110">Tuple patterns</span></span>](#tuple-patterns)
  - [<span data-ttu-id="17ec8-111">Poziční vzory</span><span class="sxs-lookup"><span data-stu-id="17ec8-111">Positional patterns</span></span>](#positional-patterns)
- [<span data-ttu-id="17ec8-112">Používání deklarací</span><span class="sxs-lookup"><span data-stu-id="17ec8-112">Using declarations</span></span>](#using-declarations)
- [<span data-ttu-id="17ec8-113">Statické místní funkce</span><span class="sxs-lookup"><span data-stu-id="17ec8-113">Static local functions</span></span>](#static-local-functions)
- [<span data-ttu-id="17ec8-114">Struktury odkazů na jedno použití</span><span class="sxs-lookup"><span data-stu-id="17ec8-114">Disposable ref structs</span></span>](#disposable-ref-structs)
- [<span data-ttu-id="17ec8-115">Odkazové typy s možnou hodnotou null</span><span class="sxs-lookup"><span data-stu-id="17ec8-115">Nullable reference types</span></span>](#nullable-reference-types)
- [<span data-ttu-id="17ec8-116">Asynchronní proudy</span><span class="sxs-lookup"><span data-stu-id="17ec8-116">Asynchronous streams</span></span>](#asynchronous-streams)
- [<span data-ttu-id="17ec8-117">Indexy a rozsahy</span><span class="sxs-lookup"><span data-stu-id="17ec8-117">Indices and ranges</span></span>](#indices-and-ranges)
- [<span data-ttu-id="17ec8-118">Přiřazení slučování s hodnotou null</span><span class="sxs-lookup"><span data-stu-id="17ec8-118">Null-coalescing assignment</span></span>](#null-coalescing-assignment)
- [<span data-ttu-id="17ec8-119">Nespravované konstruované typy</span><span class="sxs-lookup"><span data-stu-id="17ec8-119">Unmanaged constructed types</span></span>](#unmanaged-constructed-types)
- [<span data-ttu-id="17ec8-120">Stackalloc ve vnořených výrazech</span><span class="sxs-lookup"><span data-stu-id="17ec8-120">Stackalloc in nested expressions</span></span>](#stackalloc-in-nested-expressions)
- [<span data-ttu-id="17ec8-121">Vylepšení interpolované doslovného řetězce</span><span class="sxs-lookup"><span data-stu-id="17ec8-121">Enhancement of interpolated verbatim strings</span></span>](#enhancement-of-interpolated-verbatim-strings)

<span data-ttu-id="17ec8-122">Zbývající část tohoto článku stručně popisuje tyto funkce.</span><span class="sxs-lookup"><span data-stu-id="17ec8-122">The remainder of this article briefly describes these features.</span></span> <span data-ttu-id="17ec8-123">Kde jsou k dispozici podrobné články, jsou uvedeny odkazy na tyto kurzy a přehledy.</span><span class="sxs-lookup"><span data-stu-id="17ec8-123">Where in-depth articles are available, links to those tutorials and overviews are provided.</span></span> <span data-ttu-id="17ec8-124">Pomocí globálního nástroje `dotnet try` můžete prozkoumat tyto funkce ve vašem prostředí:</span><span class="sxs-lookup"><span data-stu-id="17ec8-124">You can explore these features in your environment using the `dotnet try` global tool:</span></span>

1. <span data-ttu-id="17ec8-125">Nainstalujte nástroj [dotnet-try](https://github.com/dotnet/try/blob/master/README.md#setup) Global.</span><span class="sxs-lookup"><span data-stu-id="17ec8-125">Install the [dotnet-try](https://github.com/dotnet/try/blob/master/README.md#setup) global tool.</span></span>
1. <span data-ttu-id="17ec8-126">Naklonujte úložiště [dotnet/try-Samples](https://github.com/dotnet/try-samples) .</span><span class="sxs-lookup"><span data-stu-id="17ec8-126">Clone the [dotnet/try-samples](https://github.com/dotnet/try-samples) repository.</span></span>
1. <span data-ttu-id="17ec8-127">Nastavte aktuální adresář do podadresáře *csharp8* pro úložiště *Try-Samples* .</span><span class="sxs-lookup"><span data-stu-id="17ec8-127">Set the current directory to the *csharp8* subdirectory for the *try-samples* repository.</span></span>
1. <span data-ttu-id="17ec8-128">Spusťte `dotnet try`.</span><span class="sxs-lookup"><span data-stu-id="17ec8-128">Run `dotnet try`.</span></span>

## <a name="readonly-members"></a><span data-ttu-id="17ec8-129">Členové jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="17ec8-129">Readonly members</span></span>

<span data-ttu-id="17ec8-130">Modifikátor `readonly` můžete použít pro libovolný člen struktury.</span><span class="sxs-lookup"><span data-stu-id="17ec8-130">You can apply the `readonly` modifier to any member of a struct.</span></span> <span data-ttu-id="17ec8-131">Indikuje, že člen nemění stav.</span><span class="sxs-lookup"><span data-stu-id="17ec8-131">It indicates that the member does not modify state.</span></span> <span data-ttu-id="17ec8-132">Je lépe podrobnější než použití modifikátoru `readonly` u deklarace `struct`.</span><span class="sxs-lookup"><span data-stu-id="17ec8-132">It's more granular than applying the `readonly` modifier to a `struct` declaration.</span></span>  <span data-ttu-id="17ec8-133">Vezměte v úvahu následující proměnlivou strukturu:</span><span class="sxs-lookup"><span data-stu-id="17ec8-133">Consider the following mutable struct:</span></span>

```csharp
public struct Point
{
    public double X { get; set; }
    public double Y { get; set; }
    public double Distance => Math.Sqrt(X * X + Y * Y);

    public override string ToString() =>
        $"({X}, {Y}) is {Distance} from the origin";
}
```

<span data-ttu-id="17ec8-134">Podobně jako u většiny struktur nemění metoda `ToString()` stav.</span><span class="sxs-lookup"><span data-stu-id="17ec8-134">Like most structs, the `ToString()` method does not modify state.</span></span> <span data-ttu-id="17ec8-135">Můžete určit, že přidáním modifikátoru `readonly` do deklarace `ToString()`:</span><span class="sxs-lookup"><span data-stu-id="17ec8-135">You could indicate that by adding the `readonly` modifier to the declaration of `ToString()`:</span></span>

```csharp
public readonly override string ToString() =>
    $"({X}, {Y}) is {Distance} from the origin";
```

<span data-ttu-id="17ec8-136">Předchozí změna vygeneruje upozornění kompilátoru, protože `ToString` přistupuje k vlastnosti `Distance`, která není označena `readonly`:</span><span class="sxs-lookup"><span data-stu-id="17ec8-136">The preceding change generates a compiler warning, because `ToString` accesses the `Distance` property, which is not marked `readonly`:</span></span>

```console
warning CS8656: Call to non-readonly member 'Point.Distance.get' from a 'readonly' member results in an implicit copy of 'this'
```

<span data-ttu-id="17ec8-137">Kompilátor vás upozorní, když potřebuje vytvořit obrannou linií kopii.</span><span class="sxs-lookup"><span data-stu-id="17ec8-137">The compiler warns you when it needs to create a defensive copy.</span></span>  <span data-ttu-id="17ec8-138">Vlastnost `Distance` nezmění stav, takže můžete toto upozornění opravit přidáním modifikátoru `readonly` k deklaraci:</span><span class="sxs-lookup"><span data-stu-id="17ec8-138">The `Distance` property does not change state, so you can fix this warning by adding the `readonly` modifier to the declaration:</span></span>

```csharp
public readonly double Distance => Math.Sqrt(X * X + Y * Y);
```

<span data-ttu-id="17ec8-139">Všimněte si, že modifikátor `readonly` je nezbytný pro vlastnost jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="17ec8-139">Notice that the `readonly` modifier is necessary on a read only property.</span></span> <span data-ttu-id="17ec8-140">Kompilátor nepředpokládá, že přístupové objekty `get` nemění stav; je nutné deklarovat `readonly` explicitně.</span><span class="sxs-lookup"><span data-stu-id="17ec8-140">The compiler doesn't assume `get` accessors do not modify state; you must declare `readonly` explicitly.</span></span> <span data-ttu-id="17ec8-141">Automaticky implementované vlastnosti představují výjimku. Kompilátor bude považovat všechny automaticky implementované metody getter jako jen pro čtení, takže zde není nutné přidávat modifikátor `readonly` do vlastností `X` a `Y`.</span><span class="sxs-lookup"><span data-stu-id="17ec8-141">Auto-implemented properties are an exception; the compiler will treat all auto-implemented getters as readonly, so here there is no need to add the `readonly` modifier to the `X` and `Y` properties.</span></span>

<span data-ttu-id="17ec8-142">Kompilátor vynutil pravidlo, které `readonly` členové nemění stav.</span><span class="sxs-lookup"><span data-stu-id="17ec8-142">The compiler does enforce the rule that `readonly` members do not modify state.</span></span> <span data-ttu-id="17ec8-143">Následující metoda nebude zkompilována, dokud neodeberete modifikátor `readonly`:</span><span class="sxs-lookup"><span data-stu-id="17ec8-143">The following method will not compile unless you remove the `readonly` modifier:</span></span>

```csharp
public readonly void Translate(int xOffset, int yOffset)
{
    X += xOffset;
    Y += yOffset;
}
```

<span data-ttu-id="17ec8-144">Tato funkce umožňuje určit záměr návrhu, aby ho kompilátor mohl vynutit a na základě tohoto záměru provádět optimalizace.</span><span class="sxs-lookup"><span data-stu-id="17ec8-144">This feature lets you specify your design intent so the compiler can enforce it, and make optimizations based on that intent.</span></span>

## <a name="default-interface-methods"></a><span data-ttu-id="17ec8-145">Výchozí metody rozhraní</span><span class="sxs-lookup"><span data-stu-id="17ec8-145">Default interface methods</span></span>

<span data-ttu-id="17ec8-146">Nyní můžete přidat členy do rozhraní a poskytnout implementaci pro tyto členy.</span><span class="sxs-lookup"><span data-stu-id="17ec8-146">You can now add members to interfaces and provide an implementation for those members.</span></span> <span data-ttu-id="17ec8-147">Tato funkce jazyka umožňuje autorům rozhraní API přidávat metody do rozhraní v pozdějších verzích bez narušení zdrojové nebo binární kompatibility se stávajícími implementacemi tohoto rozhraní.</span><span class="sxs-lookup"><span data-stu-id="17ec8-147">This language feature enables API authors to add methods to an interface in later versions without breaking source or binary compatibility with existing implementations of that interface.</span></span> <span data-ttu-id="17ec8-148">Stávající implementace *dědí* výchozí implementaci.</span><span class="sxs-lookup"><span data-stu-id="17ec8-148">Existing implementations *inherit* the default implementation.</span></span> <span data-ttu-id="17ec8-149">Tato funkce také umožňuje C# vzájemnou spolupráci s rozhraními API, která cílí na Android nebo SWIFT, což podporuje podobné funkce.</span><span class="sxs-lookup"><span data-stu-id="17ec8-149">This feature also enables C# to interoperate with APIs that target Android or Swift, which support similar features.</span></span> <span data-ttu-id="17ec8-150">Výchozí metody rozhraní také umožňují scénáře podobně jako funkce jazyka "vlastnosti".</span><span class="sxs-lookup"><span data-stu-id="17ec8-150">Default interface methods also enable scenarios similar to a "traits" language feature.</span></span>

<span data-ttu-id="17ec8-151">Výchozí metody rozhraní ovlivňují mnoho scénářů a prvků jazyka.</span><span class="sxs-lookup"><span data-stu-id="17ec8-151">Default interface methods affects many scenarios and language elements.</span></span> <span data-ttu-id="17ec8-152">Náš první kurz popisuje [aktualizaci rozhraní s výchozími implementacemi](../tutorials/default-interface-methods-versions.md).</span><span class="sxs-lookup"><span data-stu-id="17ec8-152">Our first tutorial covers [updating an interface with default implementations](../tutorials/default-interface-methods-versions.md).</span></span> <span data-ttu-id="17ec8-153">Další kurzy a referenční aktualizace jsou k disčase pro obecné vydání.</span><span class="sxs-lookup"><span data-stu-id="17ec8-153">Other tutorials and reference updates are coming in time for general release.</span></span>

## <a name="more-patterns-in-more-places"></a><span data-ttu-id="17ec8-154">Další vzory na více místech</span><span class="sxs-lookup"><span data-stu-id="17ec8-154">More patterns in more places</span></span>

<span data-ttu-id="17ec8-155">**Porovnávání vzorů** poskytuje nástrojům poskytování funkcionality závislé na tvaru v rámci souvisejících, ale různých druhů dat.</span><span class="sxs-lookup"><span data-stu-id="17ec8-155">**Pattern matching** gives tools to provide shape-dependent functionality across related but different kinds of data.</span></span> <span data-ttu-id="17ec8-156">C#7,0 představil Syntax pro vzory typů a konstantní vzorce pomocí výrazu [`is`](../language-reference/keywords/is.md) a příkazu [`switch`](../language-reference/keywords/switch.md) .</span><span class="sxs-lookup"><span data-stu-id="17ec8-156">C# 7.0 introduced syntax for type patterns and constant patterns by using the [`is`](../language-reference/keywords/is.md) expression and the [`switch`](../language-reference/keywords/switch.md) statement.</span></span> <span data-ttu-id="17ec8-157">Tyto funkce představovaly první nezávazné kroky směrem k podpoře programovacích paradigmat, ve kterých jsou data a funkce živě oddělené.</span><span class="sxs-lookup"><span data-stu-id="17ec8-157">These features represented the first tentative steps toward supporting programming paradigms where data and functionality live apart.</span></span> <span data-ttu-id="17ec8-158">Vzhledem k tomu, že se odvětví pohybuje k většímu mikroslužbám a dalším cloudovým architekturám, jsou potřeba jiné jazykové nástroje.</span><span class="sxs-lookup"><span data-stu-id="17ec8-158">As the industry moves toward more microservices and other cloud-based architectures, other language tools are needed.</span></span>

<span data-ttu-id="17ec8-159">C#8,0 rozšíří tento slovník, takže můžete použít více výrazů vzoru ve více místech kódu.</span><span class="sxs-lookup"><span data-stu-id="17ec8-159">C# 8.0 expands this vocabulary so you can use more pattern expressions in more places in your code.</span></span> <span data-ttu-id="17ec8-160">Tyto funkce zvažte, když jsou vaše data a funkce oddělené.</span><span class="sxs-lookup"><span data-stu-id="17ec8-160">Consider these features when your data and functionality are separate.</span></span> <span data-ttu-id="17ec8-161">Zvažte porovnávání vzorů, pokud jsou algoritmy závislé na jiném faktě, než je typ modulu runtime objektu.</span><span class="sxs-lookup"><span data-stu-id="17ec8-161">Consider pattern matching when your algorithms depend on a fact other than the runtime type of an object.</span></span> <span data-ttu-id="17ec8-162">Tyto techniky poskytují jiný způsob, jak vyjádřit návrhy.</span><span class="sxs-lookup"><span data-stu-id="17ec8-162">These techniques provide another way to express designs.</span></span>

<span data-ttu-id="17ec8-163">Kromě nových vzorů na nových místech C# 8,0 přidává **rekurzivní vzory**.</span><span class="sxs-lookup"><span data-stu-id="17ec8-163">In addition to new patterns in new places, C# 8.0 adds **recursive patterns**.</span></span> <span data-ttu-id="17ec8-164">Výsledek jakéhokoli výrazu vzoru je výraz.</span><span class="sxs-lookup"><span data-stu-id="17ec8-164">The result of any pattern expression is an expression.</span></span> <span data-ttu-id="17ec8-165">Rekurzivní vzorek je pouze výraz vzoru aplikovaný na výstup jiného výrazu vzoru.</span><span class="sxs-lookup"><span data-stu-id="17ec8-165">A recursive pattern is simply a pattern expression applied to the output of another pattern expression.</span></span>

### <a name="switch-expressions"></a><span data-ttu-id="17ec8-166">výrazy Switch</span><span class="sxs-lookup"><span data-stu-id="17ec8-166">Switch expressions</span></span>

<span data-ttu-id="17ec8-167">V každém z jeho bloků `case` se často příkaz [`switch`](../language-reference/keywords/switch.md) vytváří jako hodnota.</span><span class="sxs-lookup"><span data-stu-id="17ec8-167">Often, a [`switch`](../language-reference/keywords/switch.md) statement produces a value in each of its `case` blocks.</span></span> <span data-ttu-id="17ec8-168">**Výrazy Switch** umožňují použít stručnější syntaxi výrazů.</span><span class="sxs-lookup"><span data-stu-id="17ec8-168">**Switch expressions** enable you to use more concise expression syntax.</span></span> <span data-ttu-id="17ec8-169">K dispozici je méně opakujících se `case` a `break` klíčových slov a méně složených závorek.</span><span class="sxs-lookup"><span data-stu-id="17ec8-169">There are fewer repetitive `case` and `break` keywords, and fewer curly braces.</span></span>  <span data-ttu-id="17ec8-170">Podívejte se například na následující výčet, který obsahuje seznam barev duha:</span><span class="sxs-lookup"><span data-stu-id="17ec8-170">As an example, consider the following enum that lists the colors of the rainbow:</span></span>

```csharp
public enum Rainbow
{
    Red,
    Orange,
    Yellow,
    Green,
    Blue,
    Indigo,
    Violet
}
```

<span data-ttu-id="17ec8-171">Pokud vaše aplikace definovala typ `RGBColor`, který je vytvořen z komponent `R`, `G` a `B`, můžete převést hodnotu `Rainbow` na hodnoty RGB pomocí následující metody, která obsahuje výraz Switch:</span><span class="sxs-lookup"><span data-stu-id="17ec8-171">If your application defined an `RGBColor` type that is constructed from the `R`, `G` and `B` components, you could convert a `Rainbow` value to its RGB values using the following method containing a switch expression:</span></span>

```csharp
public static RGBColor FromRainbow(Rainbow colorBand) =>
    colorBand switch
    {
        Rainbow.Red    => new RGBColor(0xFF, 0x00, 0x00),
        Rainbow.Orange => new RGBColor(0xFF, 0x7F, 0x00),
        Rainbow.Yellow => new RGBColor(0xFF, 0xFF, 0x00),
        Rainbow.Green  => new RGBColor(0x00, 0xFF, 0x00),
        Rainbow.Blue   => new RGBColor(0x00, 0x00, 0xFF),
        Rainbow.Indigo => new RGBColor(0x4B, 0x00, 0x82),
        Rainbow.Violet => new RGBColor(0x94, 0x00, 0xD3),
        _              => throw new ArgumentException(message: "invalid enum value", paramName: nameof(colorBand)),
    };
```

<span data-ttu-id="17ec8-172">Tady je několik vylepšení syntaxe:</span><span class="sxs-lookup"><span data-stu-id="17ec8-172">There are several syntax improvements here:</span></span>

- <span data-ttu-id="17ec8-173">Proměnná se nachází před klíčovým slovem `switch`.</span><span class="sxs-lookup"><span data-stu-id="17ec8-173">The variable comes before the `switch` keyword.</span></span> <span data-ttu-id="17ec8-174">V jiném pořadí je vizuálně snadné odlišit výraz přepínače od příkazu switch.</span><span class="sxs-lookup"><span data-stu-id="17ec8-174">The different order makes it visually easy to distinguish the switch expression from the switch statement.</span></span>
- <span data-ttu-id="17ec8-175">Prvky `case` a `:` jsou nahrazeny `=>`.</span><span class="sxs-lookup"><span data-stu-id="17ec8-175">The `case` and `:` elements are replaced with `=>`.</span></span> <span data-ttu-id="17ec8-176">Je výstižnější a intuitivní.</span><span class="sxs-lookup"><span data-stu-id="17ec8-176">It's more concise and intuitive.</span></span>
- <span data-ttu-id="17ec8-177">`default` případ se nahradí `_` zahození.</span><span class="sxs-lookup"><span data-stu-id="17ec8-177">The `default` case is replaced with a `_` discard.</span></span>
- <span data-ttu-id="17ec8-178">Tělo jsou výrazy, nikoli příkazy.</span><span class="sxs-lookup"><span data-stu-id="17ec8-178">The bodies are expressions, not statements.</span></span>

<span data-ttu-id="17ec8-179">Kontrast s ekvivalentním kódem pomocí příkazu Classic `switch`:</span><span class="sxs-lookup"><span data-stu-id="17ec8-179">Contrast that with the equivalent code using the classic `switch` statement:</span></span>

```csharp
public static RGBColor FromRainbowClassic(Rainbow colorBand)
{
    switch (colorBand)
    {
        case Rainbow.Red:
            return new RGBColor(0xFF, 0x00, 0x00);
        case Rainbow.Orange:
            return new RGBColor(0xFF, 0x7F, 0x00);
        case Rainbow.Yellow:
            return new RGBColor(0xFF, 0xFF, 0x00);
        case Rainbow.Green:
            return new RGBColor(0x00, 0xFF, 0x00);
        case Rainbow.Blue:
            return new RGBColor(0x00, 0x00, 0xFF);
        case Rainbow.Indigo:
            return new RGBColor(0x4B, 0x00, 0x82);
        case Rainbow.Violet:
            return new RGBColor(0x94, 0x00, 0xD3);
        default:
            throw new ArgumentException(message: "invalid enum value", paramName: nameof(colorBand));
    };
}
```

### <a name="property-patterns"></a><span data-ttu-id="17ec8-180">Vzory vlastností</span><span class="sxs-lookup"><span data-stu-id="17ec8-180">Property patterns</span></span>

<span data-ttu-id="17ec8-181">**Vzor vlastnosti** umožňuje porovnávat vlastnosti objektu, který je zkontrolován.</span><span class="sxs-lookup"><span data-stu-id="17ec8-181">The **property pattern** enables you to match on properties of the object examined.</span></span> <span data-ttu-id="17ec8-182">Vezměte v úvahu web elektronického obchodování, který musí počítat DPH na základě adresy kupujícího.</span><span class="sxs-lookup"><span data-stu-id="17ec8-182">Consider an eCommerce site that must compute sales tax based on the buyer's address.</span></span> <span data-ttu-id="17ec8-183">Toto výpočtu není základní zodpovědností třídy `Address`.</span><span class="sxs-lookup"><span data-stu-id="17ec8-183">That computation is not a core responsibility of an `Address` class.</span></span> <span data-ttu-id="17ec8-184">Změní se v průběhu času, nejspíš častěji než změny formátu adresy.</span><span class="sxs-lookup"><span data-stu-id="17ec8-184">It will change over time, likely more often than address format changes.</span></span> <span data-ttu-id="17ec8-185">Objem DPH závisí na vlastnosti `State` adresy.</span><span class="sxs-lookup"><span data-stu-id="17ec8-185">The amount of sales tax depends on the `State` property of the address.</span></span> <span data-ttu-id="17ec8-186">Následující metoda používá vzorek vlastností k výpočtu DPH z adresy a ceny:</span><span class="sxs-lookup"><span data-stu-id="17ec8-186">The following method uses the property pattern to compute the sales tax from the address and the price:</span></span>

```csharp
public static decimal ComputeSalesTax(Address location, decimal salePrice) =>
    location switch
    {
        { State: "WA" } => salePrice * 0.06M,
        { State: "MN" } => salePrice * 0.75M,
        { State: "MI" } => salePrice * 0.05M,
        // other cases removed for brevity...
        _ => 0M
    };
```

<span data-ttu-id="17ec8-187">Porovnávání vzorů vytvoří stručnou syntaxi pro vyjádření tohoto algoritmu.</span><span class="sxs-lookup"><span data-stu-id="17ec8-187">Pattern matching creates a concise syntax for expressing this algorithm.</span></span>

### <a name="tuple-patterns"></a><span data-ttu-id="17ec8-188">Vzory řazené kolekce členů</span><span class="sxs-lookup"><span data-stu-id="17ec8-188">Tuple patterns</span></span>

<span data-ttu-id="17ec8-189">Některé algoritmy závisí na více vstupech.</span><span class="sxs-lookup"><span data-stu-id="17ec8-189">Some algorithms depend on multiple inputs.</span></span> <span data-ttu-id="17ec8-190">**Vzorce řazené kolekce členů** umožňují přepínat na základě více hodnot vyjádřených jako [řazené kolekce členů](../tuples.md).</span><span class="sxs-lookup"><span data-stu-id="17ec8-190">**Tuple patterns** allow you to switch based on multiple values expressed as a [tuple](../tuples.md).</span></span>  <span data-ttu-id="17ec8-191">Následující kód ukazuje výraz přepínače pro herní *rock, papír, nůžky*:</span><span class="sxs-lookup"><span data-stu-id="17ec8-191">The following code shows a switch expression for the game *rock, paper, scissors*:</span></span>

```csharp
public static string RockPaperScissors(string first, string second)
    => (first, second) switch
    {
        ("rock", "paper") => "rock is covered by paper. Paper wins.",
        ("rock", "scissors") => "rock breaks scissors. Rock wins.",
        ("paper", "rock") => "paper covers rock. Paper wins.",
        ("paper", "scissors") => "paper is cut by scissors. Scissors wins.",
        ("scissors", "rock") => "scissors is broken by rock. Rock wins.",
        ("scissors", "paper") => "scissors cuts paper. Scissors wins.",
        (_, _) => "tie"
    };
```

<span data-ttu-id="17ec8-192">Zprávy indikují vítěze.</span><span class="sxs-lookup"><span data-stu-id="17ec8-192">The messages indicate the winner.</span></span> <span data-ttu-id="17ec8-193">Případ zahození představuje tři kombinace pro vazby nebo jiné textové vstupy.</span><span class="sxs-lookup"><span data-stu-id="17ec8-193">The discard case represents the three combinations for ties, or other text inputs.</span></span>

### <a name="positional-patterns"></a><span data-ttu-id="17ec8-194">Poziční vzory</span><span class="sxs-lookup"><span data-stu-id="17ec8-194">Positional patterns</span></span>

<span data-ttu-id="17ec8-195">Některé typy zahrnují metodu `Deconstruct`, která dekonstruuje své vlastnosti do diskrétních proměnných.</span><span class="sxs-lookup"><span data-stu-id="17ec8-195">Some types include a `Deconstruct` method that deconstructs its properties into discrete variables.</span></span> <span data-ttu-id="17ec8-196">Pokud je k dispozici metoda `Deconstruct`, můžete použít **poziční vzory** pro kontrolu vlastností objektu a použít tyto vlastnosti pro vzor.</span><span class="sxs-lookup"><span data-stu-id="17ec8-196">When a `Deconstruct` method is accessible, you can use **positional patterns** to inspect properties of the object and use those properties for a pattern.</span></span>  <span data-ttu-id="17ec8-197">Vezměte v úvahu následující třídu `Point`, která obsahuje metodu `Deconstruct` pro vytváření diskrétních proměnných pro `X` a `Y`:</span><span class="sxs-lookup"><span data-stu-id="17ec8-197">Consider the following `Point` class that includes a `Deconstruct` method to create discrete variables for `X` and `Y`:</span></span>

```csharp
public class Point
{
    public int X { get; }
    public int Y { get; }

    public Point(int x, int y) => (X, Y) = (x, y);

    public void Deconstruct(out int x, out int y) =>
        (x, y) = (X, Y);
}
```

<span data-ttu-id="17ec8-198">Navíc zvažte následující výčet, který představuje různé pozice kvadrantu:</span><span class="sxs-lookup"><span data-stu-id="17ec8-198">Additionally, consider the following enum that represents various positions of a quadrant:</span></span>

```csharp
public enum Quadrant
{
    Unknown,
    Origin,
    One,
    Two,
    Three,
    Four,
    OnBorder
}
```

<span data-ttu-id="17ec8-199">Následující metoda používá **poziční vzorek** k extrakci hodnot `x` a `y`.</span><span class="sxs-lookup"><span data-stu-id="17ec8-199">The following method uses the **positional pattern** to extract the values of `x` and `y`.</span></span> <span data-ttu-id="17ec8-200">Pak pomocí klauzule `when` určíte `Quadrant` bodu:</span><span class="sxs-lookup"><span data-stu-id="17ec8-200">Then, it uses a `when` clause to determine the `Quadrant` of the point:</span></span>

```csharp
static Quadrant GetQuadrant(Point point) => point switch
{
    (0, 0) => Quadrant.Origin,
    var (x, y) when x > 0 && y > 0 => Quadrant.One,
    var (x, y) when x < 0 && y > 0 => Quadrant.Two,
    var (x, y) when x < 0 && y < 0 => Quadrant.Three,
    var (x, y) when x > 0 && y < 0 => Quadrant.Four,
    var (_, _) => Quadrant.OnBorder,
    _ => Quadrant.Unknown
};
```

<span data-ttu-id="17ec8-201">Vzor zahození v předchozím přepínači odpovídá, pokud buď `x` nebo `y` je 0, ale ne obojí.</span><span class="sxs-lookup"><span data-stu-id="17ec8-201">The discard pattern in the preceding switch matches when either `x` or `y` is 0, but not both.</span></span> <span data-ttu-id="17ec8-202">Výraz přepínače musí buď vytvořit hodnotu, nebo vyvolat výjimku.</span><span class="sxs-lookup"><span data-stu-id="17ec8-202">A switch expression must either produce a value or throw an exception.</span></span> <span data-ttu-id="17ec8-203">Pokud žádný z případů neodpovídá, výraz přepínače vyvolá výjimku.</span><span class="sxs-lookup"><span data-stu-id="17ec8-203">If none of the cases match, the switch expression throws an exception.</span></span> <span data-ttu-id="17ec8-204">Kompilátor vygeneruje upozornění, pokud nepokrýváte všechny možné případy ve výrazu přepínače.</span><span class="sxs-lookup"><span data-stu-id="17ec8-204">The compiler generates a warning for you if you do not cover all possible cases in your switch expression.</span></span>

<span data-ttu-id="17ec8-205">Techniky porovnávání vzorů můžete prozkoumat v tomto [pokročilém kurzu o porovnávání vzorů](../tutorials/pattern-matching.md).</span><span class="sxs-lookup"><span data-stu-id="17ec8-205">You can explore pattern matching techniques in this [advanced tutorial on pattern matching](../tutorials/pattern-matching.md).</span></span>

## <a name="using-declarations"></a><span data-ttu-id="17ec8-206">používání deklarací</span><span class="sxs-lookup"><span data-stu-id="17ec8-206">Using declarations</span></span>

<span data-ttu-id="17ec8-207">**Deklarace using** je deklarace proměnné před klíčovým slovem `using`.</span><span class="sxs-lookup"><span data-stu-id="17ec8-207">A **using declaration** is a variable declaration preceded by the `using` keyword.</span></span> <span data-ttu-id="17ec8-208">Dává kompilátoru pokyn, že proměnná, která má být deklarována, by měla být uvolněna na konci ohraničujícího oboru.</span><span class="sxs-lookup"><span data-stu-id="17ec8-208">It tells the compiler that the variable being declared should be disposed at the end of the enclosing scope.</span></span> <span data-ttu-id="17ec8-209">Zvažte například následující kód, který zapisuje textový soubor:</span><span class="sxs-lookup"><span data-stu-id="17ec8-209">For example, consider the following code that writes a text file:</span></span>

```csharp
static int WriteLinesToFile(IEnumerable<string> lines)
{
    using var file = new System.IO.StreamWriter("WriteLines2.txt");
    // Notice how we declare skippedLines after the using statement.
    int skippedLines = 0;
    foreach (string line in lines)
    {
        if (!line.Contains("Second"))
        {
            file.WriteLine(line);
        }
        else
        {
            skippedLines++;
        }
    }
    // Notice how skippedLines is in scope here.
    return skippedLines;
    // file is disposed here
}
```

<span data-ttu-id="17ec8-210">V předchozím příkladu je soubor zlikvidován při dosažení uzavírací závorky pro metodu.</span><span class="sxs-lookup"><span data-stu-id="17ec8-210">In the preceding example, the file is disposed when the closing brace for the method is reached.</span></span> <span data-ttu-id="17ec8-211">To je konec oboru, ve kterém je deklarováno `file`.</span><span class="sxs-lookup"><span data-stu-id="17ec8-211">That's the end of the scope in which `file` is declared.</span></span> <span data-ttu-id="17ec8-212">Předchozí kód je ekvivalentní následujícímu kódu, který používá [příkaz Classic using](../language-reference/keywords/using-statement.md):</span><span class="sxs-lookup"><span data-stu-id="17ec8-212">The preceding code is equivalent to the following code that uses the classic [using statement](../language-reference/keywords/using-statement.md):</span></span>

```csharp
static int WriteLinesToFile(IEnumerable<string> lines)
{
    // We must declare the variable outside of the using block
    // so that it is in scope to be returned.
    int skippedLines = 0;
    using (var file = new System.IO.StreamWriter("WriteLines2.txt"))
    {
        foreach (string line in lines)
        {
            if (!line.Contains("Second"))
            {
                file.WriteLine(line);
            }
            else
            {
                skippedLines++;
            }
        }
    } // file is disposed here
    return skippedLines;
}
```

<span data-ttu-id="17ec8-213">V předchozím příkladu je soubor uvolněn, pokud je dosažena pravá složená závorka přidružená k příkazu `using`.</span><span class="sxs-lookup"><span data-stu-id="17ec8-213">In the preceding example, the file is disposed when the closing brace associated with the `using` statement is reached.</span></span>

<span data-ttu-id="17ec8-214">V obou případech kompilátor vygeneruje volání `Dispose()`.</span><span class="sxs-lookup"><span data-stu-id="17ec8-214">In both cases, the compiler generates the call to `Dispose()`.</span></span> <span data-ttu-id="17ec8-215">Kompilátor vygeneruje chybu, pokud výraz v příkazu `using` není na jedno použití.</span><span class="sxs-lookup"><span data-stu-id="17ec8-215">The compiler generates an error if the expression in the `using` statement is not disposable.</span></span>

## <a name="static-local-functions"></a><span data-ttu-id="17ec8-216">Statické místní funkce</span><span class="sxs-lookup"><span data-stu-id="17ec8-216">Static local functions</span></span>

<span data-ttu-id="17ec8-217">Nyní můžete přidat modifikátor `static` do místních funkcí, aby se zajistilo, že lokální funkce nebude zachytit (odkaz) jakékoli proměnné z nadřazeného oboru.</span><span class="sxs-lookup"><span data-stu-id="17ec8-217">You can now add the `static` modifier to local functions to ensure that local function doesn't capture (reference) any variables from the enclosing scope.</span></span> <span data-ttu-id="17ec8-218">Tím se vygeneruje `CS8421`. statická místní funkce nemůže obsahovat odkaz na \<variable >.</span><span class="sxs-lookup"><span data-stu-id="17ec8-218">Doing so generates `CS8421`, "A static local function can't contain a reference to \<variable>."</span></span> 

<span data-ttu-id="17ec8-219">Vezměte v úvahu následující kód.</span><span class="sxs-lookup"><span data-stu-id="17ec8-219">Consider the following code.</span></span> <span data-ttu-id="17ec8-220">Místní funkce `LocalFunction` přistupuje k proměnné `y` deklarované v ohraničujícím oboru (metoda `M`).</span><span class="sxs-lookup"><span data-stu-id="17ec8-220">The local function `LocalFunction` accesses the variable `y`, declared in the enclosing scope (the method `M`).</span></span> <span data-ttu-id="17ec8-221">Proto `LocalFunction` nelze deklarovat pomocí modifikátoru `static`:</span><span class="sxs-lookup"><span data-stu-id="17ec8-221">Therefore, `LocalFunction` can't be declared with the `static` modifier:</span></span>

```csharp
int M()
{
    int y;
    LocalFunction();
    return y;

    void LocalFunction() => y = 0;
}
```

<span data-ttu-id="17ec8-222">Následující kód obsahuje statickou místní funkci.</span><span class="sxs-lookup"><span data-stu-id="17ec8-222">The following code contains a static local function.</span></span> <span data-ttu-id="17ec8-223">Může být statický, protože nemá přístup k žádným proměnným v ohraničujícím oboru:</span><span class="sxs-lookup"><span data-stu-id="17ec8-223">It can be static because it doesn't access any variables in the enclosing scope:</span></span>

```csharp
int M()
{
    int y = 5;
    int x = 7;
    return Add(x, y);

    static int Add(int left, int right) => left + right;
}
```

## <a name="disposable-ref-structs"></a><span data-ttu-id="17ec8-224">Struktury odkazů na jedno použití</span><span class="sxs-lookup"><span data-stu-id="17ec8-224">Disposable ref structs</span></span>

<span data-ttu-id="17ec8-225">@No__t_0 deklarovaný s modifikátorem `ref` nesmí implementovat žádná rozhraní a proto nemohou implementovat <xref:System.IDisposable>.</span><span class="sxs-lookup"><span data-stu-id="17ec8-225">A `struct` declared with the `ref` modifier may not implement any interfaces and so cannot implement <xref:System.IDisposable>.</span></span> <span data-ttu-id="17ec8-226">Proto aby bylo možné odstranit `ref struct`, musí mít přístupnou metodu `void Dispose()`.</span><span class="sxs-lookup"><span data-stu-id="17ec8-226">Therefore, to enable a `ref struct` to be disposed, it must have an accessible `void Dispose()` method.</span></span> <span data-ttu-id="17ec8-227">To platí také pro deklarace `readonly ref struct`.</span><span class="sxs-lookup"><span data-stu-id="17ec8-227">This also applies to `readonly ref struct` declarations.</span></span>

## <a name="nullable-reference-types"></a><span data-ttu-id="17ec8-228">Odkazové typy s možnou hodnotou null</span><span class="sxs-lookup"><span data-stu-id="17ec8-228">Nullable reference types</span></span>

<span data-ttu-id="17ec8-229">V kontextu anotace s možnou hodnotou null je jakákoli proměnná typu odkazu považována za **typ odkazu**, který není null.</span><span class="sxs-lookup"><span data-stu-id="17ec8-229">Inside a nullable annotation context, any variable of a reference type is considered to be a **nonnullable reference type**.</span></span> <span data-ttu-id="17ec8-230">Pokud chcete označit, že proměnná může mít hodnotu null, je nutné připojit název typu s `?` pro deklaraci proměnné jako **typ odkazu s možnou hodnotou null**.</span><span class="sxs-lookup"><span data-stu-id="17ec8-230">If you want to indicate that a variable may be null, you must append the type name with the `?` to declare the variable as a **nullable reference type**.</span></span>

<span data-ttu-id="17ec8-231">Pro nehodnotový odkazový typ kompilátor používá analýzu toků k zajištění, že lokální proměnné jsou inicializovány na hodnotu, která není null, je-li deklarována.</span><span class="sxs-lookup"><span data-stu-id="17ec8-231">For nonnullable reference types, the compiler uses flow analysis to ensure that local variables are initialized to a non-null value when declared.</span></span> <span data-ttu-id="17ec8-232">Pole musí být inicializována během konstrukce.</span><span class="sxs-lookup"><span data-stu-id="17ec8-232">Fields must be initialized during construction.</span></span> <span data-ttu-id="17ec8-233">Kompilátor vygeneruje upozornění, pokud proměnná není nastavena voláním žádné z dostupných konstruktorů nebo inicializátorem.</span><span class="sxs-lookup"><span data-stu-id="17ec8-233">The compiler generates a warning if the variable is not set by a call to any of the available constructors or by an initializer.</span></span> <span data-ttu-id="17ec8-234">Kromě toho nemůžete přiřadit typy odkazů, které mohou mít hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="17ec8-234">Furthermore, nonnullable reference types can't be assigned a value that could be null.</span></span>

<span data-ttu-id="17ec8-235">Typy odkazů s možnou hodnotou null nejsou kontrolovány, aby se zajistilo, že nejsou přiřazeny nebo inicializovány</span><span class="sxs-lookup"><span data-stu-id="17ec8-235">Nullable reference types aren't checked to ensure they aren't assigned or initialized to null.</span></span> <span data-ttu-id="17ec8-236">Kompilátor však používá analýzu toků k zajištění toho, aby byla jakákoli proměnná typu odkazu s možnou hodnotou null zkontrolována před tím, než bude k dispozici nebo přiřazena k neprázdnému typu odkazu.</span><span class="sxs-lookup"><span data-stu-id="17ec8-236">However, the compiler uses flow analysis to ensure that any variable of a nullable reference type is checked against null before it's accessed or assigned to a nonnullable reference type.</span></span>

<span data-ttu-id="17ec8-237">Další informace o této funkci najdete v přehledu [typů odkazů s možnou hodnotou null](../nullable-references.md).</span><span class="sxs-lookup"><span data-stu-id="17ec8-237">You can learn more about the feature in the overview of [nullable reference types](../nullable-references.md).</span></span> <span data-ttu-id="17ec8-238">Zkuste to sami v nové aplikaci v tomto [kurzu odkazové typy s možnou hodnotou null](../tutorials/nullable-reference-types.md).</span><span class="sxs-lookup"><span data-stu-id="17ec8-238">Try it yourself in a new application in this [nullable reference types tutorial](../tutorials/nullable-reference-types.md).</span></span> <span data-ttu-id="17ec8-239">Přečtěte si o krocích k migraci existujícího základu kódu, aby bylo možné používat v [migraci aplikace na použití typů odkazů s možnou hodnotou null v kurzu](../tutorials/upgrade-to-nullable-references.md).</span><span class="sxs-lookup"><span data-stu-id="17ec8-239">Learn about the steps to migrate an existing codebase to make use of nullable reference types in the [migrating an application to use nullable reference types tutorial](../tutorials/upgrade-to-nullable-references.md).</span></span>

## <a name="asynchronous-streams"></a><span data-ttu-id="17ec8-240">Asynchronní proudy</span><span class="sxs-lookup"><span data-stu-id="17ec8-240">Asynchronous streams</span></span>

<span data-ttu-id="17ec8-241">Počínaje C# 8,0 můžete proudy vytvářet a spotřebovávat asynchronně.</span><span class="sxs-lookup"><span data-stu-id="17ec8-241">Starting with C# 8.0, you can create and consume streams asynchronously.</span></span> <span data-ttu-id="17ec8-242">Metoda, která vrací asynchronní datový proud má tři vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="17ec8-242">A method that returns an asynchronous stream has three properties:</span></span>

1. <span data-ttu-id="17ec8-243">Je deklarována s modifikátorem `async`.</span><span class="sxs-lookup"><span data-stu-id="17ec8-243">It's declared with the `async` modifier.</span></span>
1. <span data-ttu-id="17ec8-244">Vrátí <xref:System.Collections.Generic.IAsyncEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="17ec8-244">It returns an <xref:System.Collections.Generic.IAsyncEnumerable%601>.</span></span>
1. <span data-ttu-id="17ec8-245">Metoda obsahuje příkazy `yield return` pro vrácení po sobě jdoucích prvků v asynchronním datovém proudu.</span><span class="sxs-lookup"><span data-stu-id="17ec8-245">The method contains `yield return` statements to return successive elements in the asynchronous stream.</span></span>

<span data-ttu-id="17ec8-246">Spotřebovávání asynchronního datového proudu vyžaduje, abyste před klíčovým slovem `foreach` přidali klíčové slovo `await` při vytváření výčtu prvků streamu.</span><span class="sxs-lookup"><span data-stu-id="17ec8-246">Consuming an asynchronous stream requires you to add the `await` keyword before the `foreach` keyword when you enumerate the elements of the stream.</span></span> <span data-ttu-id="17ec8-247">Přidání klíčového slova `await` vyžaduje metodu, která vytvoří výčet asynchronního datového proudu, který má být deklarován pomocí modifikátoru `async` a vrátí typ povolený pro metodu `async`.</span><span class="sxs-lookup"><span data-stu-id="17ec8-247">Adding the `await` keyword requires the method that enumerates the asynchronous stream to be declared with the `async` modifier and to return a type allowed for an `async` method.</span></span> <span data-ttu-id="17ec8-248">Obvykle to znamená vrácení <xref:System.Threading.Tasks.Task> nebo <xref:System.Threading.Tasks.Task%601>.</span><span class="sxs-lookup"><span data-stu-id="17ec8-248">Typically that means returning a <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="17ec8-249">Může to být také <xref:System.Threading.Tasks.ValueTask> nebo <xref:System.Threading.Tasks.ValueTask%601>.</span><span class="sxs-lookup"><span data-stu-id="17ec8-249">It can also be a <xref:System.Threading.Tasks.ValueTask> or <xref:System.Threading.Tasks.ValueTask%601>.</span></span> <span data-ttu-id="17ec8-250">Metoda může spotřebovávat a vytvořit asynchronní datový proud, což znamená, že by vrátilo <xref:System.Collections.Generic.IAsyncEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="17ec8-250">A method can both consume and produce an asynchronous stream, which means it would return an <xref:System.Collections.Generic.IAsyncEnumerable%601>.</span></span> <span data-ttu-id="17ec8-251">Následující kód vygeneruje sekvenci od 0 do 19, čekání 100 MS mezi vygenerováním každého čísla:</span><span class="sxs-lookup"><span data-stu-id="17ec8-251">The following code generates a sequence from 0 to 19, waiting 100 ms between generating each number:</span></span>

```csharp
public static async System.Collections.Generic.IAsyncEnumerable<int> GenerateSequence()
{
    for (int i = 0; i < 20; i++)
    {
        await Task.Delay(100);
        yield return i;
    }
}
```

<span data-ttu-id="17ec8-252">Vyčíslení sekvence pomocí příkazu `await foreach`:</span><span class="sxs-lookup"><span data-stu-id="17ec8-252">You would enumerate the sequence using the `await foreach` statement:</span></span>

```csharp
await foreach (var number in GenerateSequence())
{
    Console.WriteLine(number);
}
```

<span data-ttu-id="17ec8-253">Asynchronní streamy si můžete vyzkoušet sami v našem kurzu [vytváření a využívání asynchronních datových proudů](../tutorials/generate-consume-asynchronous-stream.md).</span><span class="sxs-lookup"><span data-stu-id="17ec8-253">You can try asynchronous streams yourself in our tutorial on [creating and consuming async streams](../tutorials/generate-consume-asynchronous-stream.md).</span></span>

## <a name="indices-and-ranges"></a><span data-ttu-id="17ec8-254">Indexy a rozsahy</span><span class="sxs-lookup"><span data-stu-id="17ec8-254">Indices and ranges</span></span>

<span data-ttu-id="17ec8-255">Indexy a rozsahy poskytují stručnou syntaxi pro přístup k jednotlivým prvkům nebo rozsahům v sekvenci.</span><span class="sxs-lookup"><span data-stu-id="17ec8-255">Indices and ranges provide a succinct syntax for accessing single elements or ranges in a sequence.</span></span>

<span data-ttu-id="17ec8-256">Tato podpora jazyků spoléhá na dva nové typy a dva nové operátory:</span><span class="sxs-lookup"><span data-stu-id="17ec8-256">This language support relies on two new types, and two new operators:</span></span>

- <span data-ttu-id="17ec8-257"><xref:System.Index?displayProperty=nameWithType> představuje index do sekvence.</span><span class="sxs-lookup"><span data-stu-id="17ec8-257"><xref:System.Index?displayProperty=nameWithType> represents an index into a sequence.</span></span>
- <span data-ttu-id="17ec8-258">Index z operátoru end `^`, který určuje, že index je relativní ke konci sekvence.</span><span class="sxs-lookup"><span data-stu-id="17ec8-258">The index from end operator `^`, which specifies that an index is relative to the end of the sequence.</span></span>
- <span data-ttu-id="17ec8-259"><xref:System.Range?displayProperty=nameWithType> představuje dílčí rozsah sekvence.</span><span class="sxs-lookup"><span data-stu-id="17ec8-259"><xref:System.Range?displayProperty=nameWithType> represents a sub range of a sequence.</span></span>
- <span data-ttu-id="17ec8-260">Operátor rozsahu `..`, který jako svůj operand Určuje začátek a konec rozsahu.</span><span class="sxs-lookup"><span data-stu-id="17ec8-260">The range operator `..`, which specifies the start and end of a range as its operands.</span></span>

<span data-ttu-id="17ec8-261">Pojďme začít s pravidly pro indexy.</span><span class="sxs-lookup"><span data-stu-id="17ec8-261">Let's start with the rules for indexes.</span></span> <span data-ttu-id="17ec8-262">Vezměte v úvahu pole `sequence`.</span><span class="sxs-lookup"><span data-stu-id="17ec8-262">Consider an array `sequence`.</span></span> <span data-ttu-id="17ec8-263">`0` index je stejný jako `sequence[0]`.</span><span class="sxs-lookup"><span data-stu-id="17ec8-263">The `0` index is the same as `sequence[0]`.</span></span> <span data-ttu-id="17ec8-264">`^0` index je stejný jako `sequence[sequence.Length]`.</span><span class="sxs-lookup"><span data-stu-id="17ec8-264">The `^0` index is the same as `sequence[sequence.Length]`.</span></span> <span data-ttu-id="17ec8-265">Všimněte si, že `sequence[^0]` vyvolá výjimku, stejně jako `sequence[sequence.Length]`.</span><span class="sxs-lookup"><span data-stu-id="17ec8-265">Note that `sequence[^0]` does throw an exception, just as `sequence[sequence.Length]` does.</span></span> <span data-ttu-id="17ec8-266">V případě libovolného čísla `n`index `^n` stejný jako `sequence.Length - n`.</span><span class="sxs-lookup"><span data-stu-id="17ec8-266">For any number `n`, the index `^n` is the same as `sequence.Length - n`.</span></span>

<span data-ttu-id="17ec8-267">Rozsah Určuje *začátek* a *konec* rozsahu.</span><span class="sxs-lookup"><span data-stu-id="17ec8-267">A range specifies the *start* and *end* of a range.</span></span> <span data-ttu-id="17ec8-268">Začátek rozsahu je včetně, ale konec rozsahu je exkluzivní, což znamená, že *začátek* je zahrnut v rozsahu, ale *konec* není zahrnutý v rozsahu.</span><span class="sxs-lookup"><span data-stu-id="17ec8-268">The start of the range is inclusive, but the end of the range is exclusive, meaning the *start* is included in the range but the *end* is not included in the range.</span></span> <span data-ttu-id="17ec8-269">Rozsah `[0..^0]` představuje celý rozsah, stejně jako `[0..sequence.Length]` představuje celý rozsah.</span><span class="sxs-lookup"><span data-stu-id="17ec8-269">The range `[0..^0]` represents the entire range, just as `[0..sequence.Length]` represents the entire range.</span></span>

<span data-ttu-id="17ec8-270">Pojďme se podívat na několik příkladů.</span><span class="sxs-lookup"><span data-stu-id="17ec8-270">Let's look at a few examples.</span></span> <span data-ttu-id="17ec8-271">Vezměte v úvahu následující pole s poznámkou s jeho indexem od začátku do konce:</span><span class="sxs-lookup"><span data-stu-id="17ec8-271">Consider the following array, annotated with its index from the start and from the end:</span></span>

```csharp
var words = new string[]
{
                // index from start    index from end
    "The",      // 0                   ^9
    "quick",    // 1                   ^8
    "brown",    // 2                   ^7
    "fox",      // 3                   ^6
    "jumped",   // 4                   ^5
    "over",     // 5                   ^4
    "the",      // 6                   ^3
    "lazy",     // 7                   ^2
    "dog"       // 8                   ^1
};              // 9 (or words.Length) ^0
```

<span data-ttu-id="17ec8-272">Poslední slovo můžete načíst pomocí `^1` indexu:</span><span class="sxs-lookup"><span data-stu-id="17ec8-272">You can retrieve the last word with the `^1` index:</span></span>

```csharp
Console.WriteLine($"The last word is {words[^1]}");
// writes "dog"
```

<span data-ttu-id="17ec8-273">Následující kód vytvoří dílčí rozsah s slovy "Rychlá", "hnědá" a "Fox".</span><span class="sxs-lookup"><span data-stu-id="17ec8-273">The following code creates a subrange with the words "quick", "brown", and "fox".</span></span> <span data-ttu-id="17ec8-274">Zahrnuje `words[1]` prostřednictvím `words[3]`.</span><span class="sxs-lookup"><span data-stu-id="17ec8-274">It includes `words[1]` through `words[3]`.</span></span> <span data-ttu-id="17ec8-275">Element `words[4]` není v rozsahu.</span><span class="sxs-lookup"><span data-stu-id="17ec8-275">The element `words[4]` is not in the range.</span></span>

```csharp
var quickBrownFox = words[1..4];
```

<span data-ttu-id="17ec8-276">Následující kód vytvoří dílčí rozsah s "opožděným" a "pes".</span><span class="sxs-lookup"><span data-stu-id="17ec8-276">The following code creates a subrange with "lazy" and "dog".</span></span> <span data-ttu-id="17ec8-277">Zahrnuje `words[^2]` a `words[^1]`.</span><span class="sxs-lookup"><span data-stu-id="17ec8-277">It includes `words[^2]` and `words[^1]`.</span></span> <span data-ttu-id="17ec8-278">Konec `words[^0]` indexu není zahrnutý:</span><span class="sxs-lookup"><span data-stu-id="17ec8-278">The end index `words[^0]` is not included:</span></span>

```csharp
var lazyDog = words[^2..^0];
```

<span data-ttu-id="17ec8-279">V následujících příkladech jsou vytvořeny rozsahy, které jsou otevřeny pro začátek, konec nebo obojí:</span><span class="sxs-lookup"><span data-stu-id="17ec8-279">The following examples create ranges that are open ended for the start, end, or both:</span></span>

```csharp
var allWords = words[..]; // contains "The" through "dog".
var firstPhrase = words[..4]; // contains "The" through "fox"
var lastPhrase = words[6..]; // contains "the", "lazy" and "dog"
```

<span data-ttu-id="17ec8-280">Rozsahy můžete deklarovat také jako proměnné:</span><span class="sxs-lookup"><span data-stu-id="17ec8-280">You can also declare ranges as variables:</span></span>

```csharp
Range phrase = 1..4;
```

<span data-ttu-id="17ec8-281">Rozsah se pak dá použít uvnitř `[` a `]`ch znaků:</span><span class="sxs-lookup"><span data-stu-id="17ec8-281">The range can then be used inside the `[` and `]` characters:</span></span>

```csharp
var text = words[phrase];
```

<span data-ttu-id="17ec8-282">Pouze pole podporují indexy a rozsahy.</span><span class="sxs-lookup"><span data-stu-id="17ec8-282">Not only arrays support indices and ranges.</span></span> <span data-ttu-id="17ec8-283">Můžete také použít indexy a rozsahy s [řetězci](../language-reference/builtin-types/reference-types.md#the-string-type), <xref:System.Span%601>nebo <xref:System.ReadOnlySpan%601>.</span><span class="sxs-lookup"><span data-stu-id="17ec8-283">You also can use indices and ranges with [string](../language-reference/builtin-types/reference-types.md#the-string-type), <xref:System.Span%601>, or <xref:System.ReadOnlySpan%601>.</span></span> <span data-ttu-id="17ec8-284">Další informace najdete v tématu [Podpora typů pro indexy a rozsahy](../tutorials/ranges-indexes.md#type-support-for-indices-and-ranges).</span><span class="sxs-lookup"><span data-stu-id="17ec8-284">For more information, see [Type support for indices and ranges](../tutorials/ranges-indexes.md#type-support-for-indices-and-ranges).</span></span>

<span data-ttu-id="17ec8-285">Můžete prozkoumat další informace o indexech a oblastech v kurzu týkající se [indexů a rozsahů](../tutorials/ranges-indexes.md).</span><span class="sxs-lookup"><span data-stu-id="17ec8-285">You can explore more about indices and ranges in the tutorial on [indices and ranges](../tutorials/ranges-indexes.md).</span></span>

## <a name="null-coalescing-assignment"></a><span data-ttu-id="17ec8-286">Přiřazení slučování s hodnotou null</span><span class="sxs-lookup"><span data-stu-id="17ec8-286">Null-coalescing assignment</span></span>

<span data-ttu-id="17ec8-287">C#8,0 zavádí operátor přiřazení s hodnotou null `??=`.</span><span class="sxs-lookup"><span data-stu-id="17ec8-287">C# 8.0 introduces the null-coalescing assignment operator `??=`.</span></span> <span data-ttu-id="17ec8-288">Operátor `??=` můžete použít k přiřazení hodnoty jeho pravého operandu k levému operandu pouze v případě, že je operand na levé straně vyhodnocen jako `null`.</span><span class="sxs-lookup"><span data-stu-id="17ec8-288">You can use the `??=` operator to assign the value of its right-hand operand to its left-hand operand only if the left-hand operand evaluates to `null`.</span></span>

```csharp
List<int> numbers = null;
int? i = null;

numbers ??= new List<int>();
numbers.Add(i ??= 17);
numbers.Add(i ??= 20);

Console.WriteLine(string.Join(" ", numbers));  // output: 17 17
Console.WriteLine(i);  // output: 17
```

<span data-ttu-id="17ec8-289">Další informace najdete v tématu [?? a?? =](../language-reference/operators/null-coalescing-operator.md) – článek o operátorech</span><span class="sxs-lookup"><span data-stu-id="17ec8-289">For more information, see the [?? and ??= operators](../language-reference/operators/null-coalescing-operator.md) article.</span></span>

## <a name="unmanaged-constructed-types"></a><span data-ttu-id="17ec8-290">Nespravované konstruované typy</span><span class="sxs-lookup"><span data-stu-id="17ec8-290">Unmanaged constructed types</span></span>

<span data-ttu-id="17ec8-291">V C# 7,3 a starších verzích konstruovaný typ (typ, který obsahuje alespoň jeden argument typu) nemůže být [nespravovaný typ](../language-reference/builtin-types/unmanaged-types.md).</span><span class="sxs-lookup"><span data-stu-id="17ec8-291">In C# 7.3 and earlier, a constructed type (a type that includes at least one type argument) cannot be an [unmanaged type](../language-reference/builtin-types/unmanaged-types.md).</span></span> <span data-ttu-id="17ec8-292">Počínaje C# 8,0, konstruovaný typ hodnoty je nespravovaný, pokud obsahuje pole pouze nespravovaných typů.</span><span class="sxs-lookup"><span data-stu-id="17ec8-292">Starting with C# 8.0, a constructed value type is unmanaged if it contains fields of unmanaged types only.</span></span>

<span data-ttu-id="17ec8-293">Například s ohledem na následující definice obecného typu `Coords<T>`:</span><span class="sxs-lookup"><span data-stu-id="17ec8-293">For example, given the following definition of the generic `Coords<T>` type:</span></span>

```csharp
public struct Coords<T>
{
    public T X;
    public T Y;
}
```

<span data-ttu-id="17ec8-294">typ `Coords<int>` je nespravovaný typ v C# 8,0 a novějším.</span><span class="sxs-lookup"><span data-stu-id="17ec8-294">the `Coords<int>` type is an unmanaged type in C# 8.0 and later.</span></span> <span data-ttu-id="17ec8-295">Podobně jako u jakéhokoli nespravovaného typu můžete vytvořit ukazatel na proměnnou tohoto typu nebo [přidělit blok paměti v zásobníku](../language-reference/operators/stackalloc.md) pro instance tohoto typu:</span><span class="sxs-lookup"><span data-stu-id="17ec8-295">Like for any unmanaged type, you can create a pointer to a variable of this type or [allocate a block of memory on the stack](../language-reference/operators/stackalloc.md) for instances of this type:</span></span>

```csharp
Span<Coords<int>> coordinates = stackalloc[]
{
    new Coords<int> { X = 0, Y = 0 },
    new Coords<int> { X = 0, Y = 3 },
    new Coords<int> { X = 4, Y = 0 }
};
```

<span data-ttu-id="17ec8-296">Další informace naleznete v tématu [nespravované typy](../language-reference/builtin-types/unmanaged-types.md).</span><span class="sxs-lookup"><span data-stu-id="17ec8-296">For more information, see [Unmanaged types](../language-reference/builtin-types/unmanaged-types.md).</span></span>

## <a name="stackalloc-in-nested-expressions"></a><span data-ttu-id="17ec8-297">stackalloc ve vnořených výrazech</span><span class="sxs-lookup"><span data-stu-id="17ec8-297">Stackalloc in nested expressions</span></span>

<span data-ttu-id="17ec8-298">Počínaje C# 8,0 platí, že pokud je výsledek [stackalloc](../language-reference/operators/stackalloc.md) výrazu<xref:System.Span%601?displayProperty=nameWithType>nebo<xref:System.ReadOnlySpan%601?displayProperty=nameWithType>typu, můžete použít výraz`stackalloc`v jiných výrazech:</span><span class="sxs-lookup"><span data-stu-id="17ec8-298">Starting with C# 8.0, if the result of a [stackalloc](../language-reference/operators/stackalloc.md) expression is of the <xref:System.Span%601?displayProperty=nameWithType> or <xref:System.ReadOnlySpan%601?displayProperty=nameWithType> type, you can use the `stackalloc` expression in other expressions:</span></span>

```csharp
Span<int> numbers = stackalloc[] { 1, 2, 3, 4, 5, 6 };
var ind = numbers.IndexOfAny(stackalloc[] { 2, 4, 6 ,8 });
Console.WriteLine(ind);  // output: 1
```

## <a name="enhancement-of-interpolated-verbatim-strings"></a><span data-ttu-id="17ec8-299">Vylepšení interpolované doslovného řetězce</span><span class="sxs-lookup"><span data-stu-id="17ec8-299">Enhancement of interpolated verbatim strings</span></span>

<span data-ttu-id="17ec8-300">Pořadí tokenů `$` a `@` v [interpolice](../language-reference/tokens/interpolated.md) doslovného řetězce může být libovolná: `$@"..."` i `@$"..."` jsou platné interpolované řetězce.</span><span class="sxs-lookup"><span data-stu-id="17ec8-300">Order of the `$` and `@` tokens in [interpolated](../language-reference/tokens/interpolated.md) verbatim strings can be any: both `$@"..."` and `@$"..."` are valid interpolated verbatim strings.</span></span> <span data-ttu-id="17ec8-301">V dřívějších C# verzích musí být token `$` uveden před tokenem `@`.</span><span class="sxs-lookup"><span data-stu-id="17ec8-301">In earlier C# versions, the `$` token must appear before the `@` token.</span></span>
