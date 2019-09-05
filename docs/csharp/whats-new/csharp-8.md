---
title: Co je nového v C# 8,0 – C# příručka
description: Získejte přehled o nových funkcích dostupných v C# 8,0. Tento článek je aktuální s verzí Preview 5.
ms.date: 09/02/2019
ms.openlocfilehash: 7210f2e978f307b3ecef2eff272fea0d19025de6
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252904"
---
# <a name="whats-new-in-c-80"></a><span data-ttu-id="cc74f-104">Co je nového v C# 8,0</span><span class="sxs-lookup"><span data-stu-id="cc74f-104">What's new in C# 8.0</span></span>

<span data-ttu-id="cc74f-105">Existuje mnoho vylepšení C# jazyka, který můžete vyzkoušet již.</span><span class="sxs-lookup"><span data-stu-id="cc74f-105">There are many enhancements to the C# language that you can try out already.</span></span>

- [<span data-ttu-id="cc74f-106">Členové jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="cc74f-106">Readonly members</span></span>](#readonly-members)
- [<span data-ttu-id="cc74f-107">Výchozí členové rozhraní</span><span class="sxs-lookup"><span data-stu-id="cc74f-107">Default interface members</span></span>](#default-interface-members)
- <span data-ttu-id="cc74f-108">[Vylepšení porovnávání vzorů](#more-patterns-in-more-places):</span><span class="sxs-lookup"><span data-stu-id="cc74f-108">[Pattern matching enhancements](#more-patterns-in-more-places):</span></span>
  - [<span data-ttu-id="cc74f-109">Výrazy Switch</span><span class="sxs-lookup"><span data-stu-id="cc74f-109">Switch expressions</span></span>](#switch-expressions)
  - [<span data-ttu-id="cc74f-110">Vzory vlastností</span><span class="sxs-lookup"><span data-stu-id="cc74f-110">Property patterns</span></span>](#property-patterns)
  - [<span data-ttu-id="cc74f-111">Vzory řazené kolekce členů</span><span class="sxs-lookup"><span data-stu-id="cc74f-111">Tuple patterns</span></span>](#tuple-patterns)
  - [<span data-ttu-id="cc74f-112">Poziční vzory</span><span class="sxs-lookup"><span data-stu-id="cc74f-112">Positional patterns</span></span>](#positional-patterns)
- [<span data-ttu-id="cc74f-113">Používání deklarací</span><span class="sxs-lookup"><span data-stu-id="cc74f-113">Using declarations</span></span>](#using-declarations)
- [<span data-ttu-id="cc74f-114">Statické místní funkce</span><span class="sxs-lookup"><span data-stu-id="cc74f-114">Static local functions</span></span>](#static-local-functions)
- [<span data-ttu-id="cc74f-115">Struktury odkazů na jedno použití</span><span class="sxs-lookup"><span data-stu-id="cc74f-115">Disposable ref structs</span></span>](#disposable-ref-structs)
- [<span data-ttu-id="cc74f-116">Odkazové typy s možnou hodnotou null</span><span class="sxs-lookup"><span data-stu-id="cc74f-116">Nullable reference types</span></span>](#nullable-reference-types)
- [<span data-ttu-id="cc74f-117">Asynchronní proudy</span><span class="sxs-lookup"><span data-stu-id="cc74f-117">Asynchronous streams</span></span>](#asynchronous-streams)
- [<span data-ttu-id="cc74f-118">Indexy a rozsahy</span><span class="sxs-lookup"><span data-stu-id="cc74f-118">Indices and ranges</span></span>](#indices-and-ranges)
- [<span data-ttu-id="cc74f-119">Vylepšení interpolované doslovného řetězce</span><span class="sxs-lookup"><span data-stu-id="cc74f-119">Enhancement of interpolated verbatim strings</span></span>](#enhancement-of-interpolated-verbatim-strings)

> [!NOTE]
> <span data-ttu-id="cc74f-120">Tento článek byl naposledy aktualizován na C# verzi 8,0 Preview 5.</span><span class="sxs-lookup"><span data-stu-id="cc74f-120">This article was last updated for C# 8.0 preview 5.</span></span>

<span data-ttu-id="cc74f-121">Zbývající část tohoto článku stručně popisuje tyto funkce.</span><span class="sxs-lookup"><span data-stu-id="cc74f-121">The remainder of this article briefly describes these features.</span></span> <span data-ttu-id="cc74f-122">Kde jsou k dispozici podrobné články, jsou uvedeny odkazy na tyto kurzy a přehledy.</span><span class="sxs-lookup"><span data-stu-id="cc74f-122">Where in-depth articles are available, links to those tutorials and overviews are provided.</span></span> <span data-ttu-id="cc74f-123">Pomocí `dotnet try` globálního nástroje můžete prozkoumat tyto funkce ve vašem prostředí:</span><span class="sxs-lookup"><span data-stu-id="cc74f-123">You can explore these features in your environment using the `dotnet try` global tool:</span></span>

1. <span data-ttu-id="cc74f-124">Nainstalujte nástroj [dotnet-try](https://github.com/dotnet/try/blob/master/README.md#setup) Global.</span><span class="sxs-lookup"><span data-stu-id="cc74f-124">Install the [dotnet-try](https://github.com/dotnet/try/blob/master/README.md#setup) global tool.</span></span>
1. <span data-ttu-id="cc74f-125">Naklonujte úložiště [dotnet/try-Samples](https://github.com/dotnet/try-samples) .</span><span class="sxs-lookup"><span data-stu-id="cc74f-125">Clone the [dotnet/try-samples](https://github.com/dotnet/try-samples) repository.</span></span>
1. <span data-ttu-id="cc74f-126">Nastavte aktuální adresář do podadresáře *csharp8* pro úložiště *Try-Samples* .</span><span class="sxs-lookup"><span data-stu-id="cc74f-126">Set the current directory to the *csharp8* subdirectory for the *try-samples* repository.</span></span>
1. <span data-ttu-id="cc74f-127">Spusťte `dotnet try`.</span><span class="sxs-lookup"><span data-stu-id="cc74f-127">Run `dotnet try`.</span></span>

## <a name="readonly-members"></a><span data-ttu-id="cc74f-128">Členové jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="cc74f-128">Readonly members</span></span>

<span data-ttu-id="cc74f-129">Můžete použít `readonly` modifikátor na libovolný člen struktury.</span><span class="sxs-lookup"><span data-stu-id="cc74f-129">You can apply the `readonly` modifier to any member of a struct.</span></span> <span data-ttu-id="cc74f-130">Indikuje, že člen nemění stav.</span><span class="sxs-lookup"><span data-stu-id="cc74f-130">It indicates that the member does not modify state.</span></span> <span data-ttu-id="cc74f-131">Je lépe podrobnější než použití `readonly` modifikátoru `struct` na deklaraci.</span><span class="sxs-lookup"><span data-stu-id="cc74f-131">It's more granular than applying the `readonly` modifier to a `struct` declaration.</span></span>  <span data-ttu-id="cc74f-132">Vezměte v úvahu následující proměnlivou strukturu:</span><span class="sxs-lookup"><span data-stu-id="cc74f-132">Consider the following mutable struct:</span></span>

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

<span data-ttu-id="cc74f-133">Podobně jako u `ToString()` většiny struktur metoda nemění stav.</span><span class="sxs-lookup"><span data-stu-id="cc74f-133">Like most structs, the `ToString()` method does not modify state.</span></span> <span data-ttu-id="cc74f-134">Můžete určit, že přidáním `readonly` modifikátoru k `ToString()`deklaraci:</span><span class="sxs-lookup"><span data-stu-id="cc74f-134">You could indicate that by adding the `readonly` modifier to the declaration of `ToString()`:</span></span>

```csharp
public readonly override string ToString() =>
    $"({X}, {Y}) is {Distance} from the origin";
```

<span data-ttu-id="cc74f-135">Předchozí změna vygeneruje upozornění kompilátoru, protože `ToString` přistupuje k `Distance` vlastnosti, která není označena jako `readonly`:</span><span class="sxs-lookup"><span data-stu-id="cc74f-135">The preceding change generates a compiler warning, because `ToString` accesses the `Distance` property, which is not marked `readonly`:</span></span>

```console
warning CS8656: Call to non-readonly member 'Point.Distance.get' from a 'readonly' member results in an implicit copy of 'this'
```

<span data-ttu-id="cc74f-136">Kompilátor vás upozorní, když potřebuje vytvořit obrannou linií kopii.</span><span class="sxs-lookup"><span data-stu-id="cc74f-136">The compiler warns you when it needs to create a defensive copy.</span></span>  <span data-ttu-id="cc74f-137">Vlastnost nezmění stav, takže můžete toto upozornění opravit `readonly` přidáním modifikátoru k deklaraci: `Distance`</span><span class="sxs-lookup"><span data-stu-id="cc74f-137">The `Distance` property does not change state, so you can fix this warning by adding the `readonly` modifier to the declaration:</span></span>

```csharp
public readonly double Distance => Math.Sqrt(X * X + Y * Y);
```

<span data-ttu-id="cc74f-138">Všimněte si, `readonly` že modifikátor je nutný pro vlastnost, která je jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="cc74f-138">Notice that the `readonly` modifier is necessary on a read only property.</span></span> <span data-ttu-id="cc74f-139">Kompilátor nepředpokládá `get` , že přistupující objekty nemění stav. musíte deklarovat `readonly` explicitně.</span><span class="sxs-lookup"><span data-stu-id="cc74f-139">The compiler doesn't assume `get` accessors do not modify state; you must declare `readonly` explicitly.</span></span> <span data-ttu-id="cc74f-140">Kompilátor vynutilo pravidlo, které `readonly` členové nemění stav.</span><span class="sxs-lookup"><span data-stu-id="cc74f-140">The compiler does enforce the rule that `readonly` members do not modify state.</span></span> <span data-ttu-id="cc74f-141">Následující metoda nebude zkompilována, dokud neodeberete `readonly` modifikátor:</span><span class="sxs-lookup"><span data-stu-id="cc74f-141">The following method will not compile unless you remove the `readonly` modifier:</span></span>

```csharp
public readonly void Translate(int xOffset, int yOffset)
{
    X += xOffset;
    Y += yOffset;
}
```

<span data-ttu-id="cc74f-142">Tato funkce umožňuje určit záměr návrhu, aby ho kompilátor mohl vynutit a na základě tohoto záměru provádět optimalizace.</span><span class="sxs-lookup"><span data-stu-id="cc74f-142">This feature lets you specify your design intent so the compiler can enforce it, and make optimizations based on that intent.</span></span>

## <a name="default-interface-members"></a><span data-ttu-id="cc74f-143">Výchozí členové rozhraní</span><span class="sxs-lookup"><span data-stu-id="cc74f-143">Default interface members</span></span>

<span data-ttu-id="cc74f-144">Nyní můžete přidat členy do rozhraní a poskytnout implementaci pro tyto členy.</span><span class="sxs-lookup"><span data-stu-id="cc74f-144">You can now add members to interfaces and provide an implementation for those members.</span></span> <span data-ttu-id="cc74f-145">Tato funkce jazyka umožňuje autorům rozhraní API přidávat metody do rozhraní v pozdějších verzích bez narušení zdrojové nebo binární kompatibility se stávajícími implementacemi tohoto rozhraní.</span><span class="sxs-lookup"><span data-stu-id="cc74f-145">This language feature enables API authors to add methods to an interface in later versions without breaking source or binary compatibility with existing implementations of that interface.</span></span> <span data-ttu-id="cc74f-146">Stávající implementace *dědí* výchozí implementaci.</span><span class="sxs-lookup"><span data-stu-id="cc74f-146">Existing implementations *inherit* the default implementation.</span></span> <span data-ttu-id="cc74f-147">Tato funkce také umožňuje C# vzájemnou spolupráci s rozhraními API, která cílí na Android nebo SWIFT, což podporuje podobné funkce.</span><span class="sxs-lookup"><span data-stu-id="cc74f-147">This feature also enables C# to interoperate with APIs that target Android or Swift, which support similar features.</span></span> <span data-ttu-id="cc74f-148">Výchozí členové rozhraní také umožňují scénáře podobně jako funkce jazyka "vlastnosti".</span><span class="sxs-lookup"><span data-stu-id="cc74f-148">Default interface members also enable scenarios similar to a "traits" language feature.</span></span>

<span data-ttu-id="cc74f-149">Výchozí členové rozhraní mají vliv na mnoho scénářů a prvků jazyka.</span><span class="sxs-lookup"><span data-stu-id="cc74f-149">Default interface members affects many scenarios and language elements.</span></span> <span data-ttu-id="cc74f-150">Náš první kurz popisuje [aktualizaci rozhraní s výchozími implementacemi](../tutorials/default-interface-members-versions.md).</span><span class="sxs-lookup"><span data-stu-id="cc74f-150">Our first tutorial covers [updating an interface with default implementations](../tutorials/default-interface-members-versions.md).</span></span> <span data-ttu-id="cc74f-151">Další kurzy a referenční aktualizace jsou k disčase pro obecné vydání.</span><span class="sxs-lookup"><span data-stu-id="cc74f-151">Other tutorials and reference updates are coming in time for general release.</span></span>

## <a name="more-patterns-in-more-places"></a><span data-ttu-id="cc74f-152">Další vzory na více místech</span><span class="sxs-lookup"><span data-stu-id="cc74f-152">More patterns in more places</span></span>

<span data-ttu-id="cc74f-153">**Porovnávání vzorů** poskytuje nástrojům poskytování funkcionality závislé na tvaru v rámci souvisejících, ale různých druhů dat.</span><span class="sxs-lookup"><span data-stu-id="cc74f-153">**Pattern matching** gives tools to provide shape-dependent functionality across related but different kinds of data.</span></span> <span data-ttu-id="cc74f-154">C#7,0 představil Syntax pro vzory typů a konstantní vzorce pomocí [`is`](../language-reference/keywords/is.md) výrazu [`switch`](../language-reference/keywords/switch.md) a příkazu.</span><span class="sxs-lookup"><span data-stu-id="cc74f-154">C# 7.0 introduced syntax for type patterns and constant patterns by using the [`is`](../language-reference/keywords/is.md) expression and the [`switch`](../language-reference/keywords/switch.md) statement.</span></span> <span data-ttu-id="cc74f-155">Tyto funkce představovaly první nezávazné kroky směrem k podpoře programovacích paradigmat, ve kterých jsou data a funkce živě oddělené.</span><span class="sxs-lookup"><span data-stu-id="cc74f-155">These features represented the first tentative steps toward supporting programming paradigms where data and functionality live apart.</span></span> <span data-ttu-id="cc74f-156">Vzhledem k tomu, že se odvětví pohybuje k většímu mikroslužbám a dalším cloudovým architekturám, jsou potřeba jiné jazykové nástroje.</span><span class="sxs-lookup"><span data-stu-id="cc74f-156">As the industry moves toward more microservices and other cloud-based architectures, other language tools are needed.</span></span>

<span data-ttu-id="cc74f-157">C#8,0 rozšíří tento slovník, takže můžete použít více výrazů vzoru ve více místech kódu.</span><span class="sxs-lookup"><span data-stu-id="cc74f-157">C# 8.0 expands this vocabulary so you can use more pattern expressions in more places in your code.</span></span> <span data-ttu-id="cc74f-158">Tyto funkce zvažte, když jsou vaše data a funkce oddělené.</span><span class="sxs-lookup"><span data-stu-id="cc74f-158">Consider these features when your data and functionality are separate.</span></span> <span data-ttu-id="cc74f-159">Zvažte porovnávání vzorů, pokud jsou algoritmy závislé na jiném faktě, než je typ modulu runtime objektu.</span><span class="sxs-lookup"><span data-stu-id="cc74f-159">Consider pattern matching when your algorithms depend on a fact other than the runtime type of an object.</span></span> <span data-ttu-id="cc74f-160">Tyto techniky poskytují jiný způsob, jak vyjádřit návrhy.</span><span class="sxs-lookup"><span data-stu-id="cc74f-160">These techniques provide another way to express designs.</span></span>

<span data-ttu-id="cc74f-161">Kromě nových vzorů na nových místech C# 8,0 přidává **rekurzivní vzory**.</span><span class="sxs-lookup"><span data-stu-id="cc74f-161">In addition to new patterns in new places, C# 8.0 adds **recursive patterns**.</span></span> <span data-ttu-id="cc74f-162">Výsledek jakéhokoli výrazu vzoru je výraz.</span><span class="sxs-lookup"><span data-stu-id="cc74f-162">The result of any pattern expression is an expression.</span></span> <span data-ttu-id="cc74f-163">Rekurzivní vzorek je pouze výraz vzoru aplikovaný na výstup jiného výrazu vzoru.</span><span class="sxs-lookup"><span data-stu-id="cc74f-163">A recursive pattern is simply a pattern expression applied to the output of another pattern expression.</span></span>

### <a name="switch-expressions"></a><span data-ttu-id="cc74f-164">výrazy Switch</span><span class="sxs-lookup"><span data-stu-id="cc74f-164">switch expressions</span></span>

<span data-ttu-id="cc74f-165">Příkaz často v každém z jeho `case` bloků vytvoří hodnotu. [`switch`](../language-reference/keywords/switch.md)</span><span class="sxs-lookup"><span data-stu-id="cc74f-165">Often, a [`switch`](../language-reference/keywords/switch.md) statement produces a value in each of its `case` blocks.</span></span> <span data-ttu-id="cc74f-166">**Výrazy Switch** umožňují použít stručnější syntaxi výrazů.</span><span class="sxs-lookup"><span data-stu-id="cc74f-166">**Switch expressions** enable you to use more concise expression syntax.</span></span> <span data-ttu-id="cc74f-167">K dispozici jsou `case` méně `break` opakující se a klíčová slova a méně složené závorky.</span><span class="sxs-lookup"><span data-stu-id="cc74f-167">There are fewer repetitive `case` and `break` keywords, and fewer curly braces.</span></span>  <span data-ttu-id="cc74f-168">Podívejte se například na následující výčet, který obsahuje seznam barev duha:</span><span class="sxs-lookup"><span data-stu-id="cc74f-168">As an example, consider the following enum that lists the colors of the rainbow:</span></span>

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

<span data-ttu-id="cc74f-169">Pokud vaše aplikace definovala `RGBColor` typ, který je vytvořen z `R`rozhraní `G` , `B` a, mohli byste převést `Rainbow` hodnotu na její hodnoty RGB pomocí následující metody, která obsahuje výraz Switch:</span><span class="sxs-lookup"><span data-stu-id="cc74f-169">If your application defined an `RGBColor` type that is constructed from the `R`, `G` and `B` components, you could convert a `Rainbow` value to its RGB values using the following method containing a switch expression:</span></span>

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

<span data-ttu-id="cc74f-170">Tady je několik vylepšení syntaxe:</span><span class="sxs-lookup"><span data-stu-id="cc74f-170">There are several syntax improvements here:</span></span>

- <span data-ttu-id="cc74f-171">Proměnná se nachází před `switch` klíčovým slovem.</span><span class="sxs-lookup"><span data-stu-id="cc74f-171">The variable comes before the `switch` keyword.</span></span> <span data-ttu-id="cc74f-172">V jiném pořadí je vizuálně snadné odlišit výraz přepínače od příkazu switch.</span><span class="sxs-lookup"><span data-stu-id="cc74f-172">The different order makes it visually easy to distinguish the switch expression from the switch statement.</span></span>
- <span data-ttu-id="cc74f-173">Prvky `case` `=>`a `:` jsou nahrazeny.</span><span class="sxs-lookup"><span data-stu-id="cc74f-173">The `case` and `:` elements are replaced with `=>`.</span></span> <span data-ttu-id="cc74f-174">Je výstižnější a intuitivní.</span><span class="sxs-lookup"><span data-stu-id="cc74f-174">It's more concise and intuitive.</span></span>
- <span data-ttu-id="cc74f-175">Případ je nahrazen `_`zahozením. `default`</span><span class="sxs-lookup"><span data-stu-id="cc74f-175">The `default` case is replaced with a `_` discard.</span></span>
- <span data-ttu-id="cc74f-176">Tělo jsou výrazy, nikoli příkazy.</span><span class="sxs-lookup"><span data-stu-id="cc74f-176">The bodies are expressions, not statements.</span></span>

<span data-ttu-id="cc74f-177">Kontrast se stejným kódem pomocí příkazu Classic `switch` :</span><span class="sxs-lookup"><span data-stu-id="cc74f-177">Contrast that with the equivalent code using the classic `switch` statement:</span></span>

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

### <a name="property-patterns"></a><span data-ttu-id="cc74f-178">Vzory vlastností</span><span class="sxs-lookup"><span data-stu-id="cc74f-178">Property patterns</span></span>

<span data-ttu-id="cc74f-179">**Vzor vlastnosti** umožňuje porovnávat vlastnosti objektu, který je zkontrolován.</span><span class="sxs-lookup"><span data-stu-id="cc74f-179">The **property pattern** enables you to match on properties of the object examined.</span></span> <span data-ttu-id="cc74f-180">Vezměte v úvahu web elektronického obchodování, který musí počítat DPH na základě adresy kupujícího.</span><span class="sxs-lookup"><span data-stu-id="cc74f-180">Consider an eCommerce site that must compute sales tax based on the buyer's address.</span></span> <span data-ttu-id="cc74f-181">Toto výpočtu není základní zodpovědností `Address` třídy.</span><span class="sxs-lookup"><span data-stu-id="cc74f-181">That computation is not a core responsibility of an `Address` class.</span></span> <span data-ttu-id="cc74f-182">Změní se v průběhu času, nejspíš častěji než změny formátu adresy.</span><span class="sxs-lookup"><span data-stu-id="cc74f-182">It will change over time, likely more often than address format changes.</span></span> <span data-ttu-id="cc74f-183">Částka DPH závisí na `State` vlastnosti adresy.</span><span class="sxs-lookup"><span data-stu-id="cc74f-183">The amount of sales tax depends on the `State` property of the address.</span></span> <span data-ttu-id="cc74f-184">Následující metoda používá vzorek vlastností k výpočtu DPH z adresy a ceny:</span><span class="sxs-lookup"><span data-stu-id="cc74f-184">The following method uses the property pattern to compute the sales tax from the address and the price:</span></span>

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

<span data-ttu-id="cc74f-185">Porovnávání vzorů vytvoří stručnou syntaxi pro vyjádření tohoto algoritmu.</span><span class="sxs-lookup"><span data-stu-id="cc74f-185">Pattern matching creates a concise syntax for expressing this algorithm.</span></span>

### <a name="tuple-patterns"></a><span data-ttu-id="cc74f-186">Vzory řazené kolekce členů</span><span class="sxs-lookup"><span data-stu-id="cc74f-186">Tuple patterns</span></span>

<span data-ttu-id="cc74f-187">Některé algoritmy závisí na více vstupech.</span><span class="sxs-lookup"><span data-stu-id="cc74f-187">Some algorithms depend on multiple inputs.</span></span> <span data-ttu-id="cc74f-188">**Vzorce řazené kolekce členů** umožňují přepínat na základě více hodnot vyjádřených jako [řazené kolekce členů](../tuples.md).</span><span class="sxs-lookup"><span data-stu-id="cc74f-188">**Tuple patterns** allow you to switch based on multiple values expressed as a [tuple](../tuples.md).</span></span>  <span data-ttu-id="cc74f-189">Následující kód ukazuje výraz přepínače pro herní *rock, papír, nůžky*:</span><span class="sxs-lookup"><span data-stu-id="cc74f-189">The following code shows a switch expression for the game *rock, paper, scissors*:</span></span>

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

<span data-ttu-id="cc74f-190">Zprávy indikují vítěze.</span><span class="sxs-lookup"><span data-stu-id="cc74f-190">The messages indicate the winner.</span></span> <span data-ttu-id="cc74f-191">Případ zahození představuje tři kombinace pro vazby nebo jiné textové vstupy.</span><span class="sxs-lookup"><span data-stu-id="cc74f-191">The discard case represents the three combinations for ties, or other text inputs.</span></span>

### <a name="positional-patterns"></a><span data-ttu-id="cc74f-192">Poziční vzory</span><span class="sxs-lookup"><span data-stu-id="cc74f-192">Positional patterns</span></span>

<span data-ttu-id="cc74f-193">Některé typy obsahují `Deconstruct` metodu, která dekonstruuje své vlastnosti do diskrétních proměnných.</span><span class="sxs-lookup"><span data-stu-id="cc74f-193">Some types include a `Deconstruct` method that deconstructs its properties into discrete variables.</span></span> <span data-ttu-id="cc74f-194">Když je metoda přístupná, můžete použít **poziční vzory** pro kontrolu vlastností objektu a použít tyto vlastnosti pro vzor. `Deconstruct`</span><span class="sxs-lookup"><span data-stu-id="cc74f-194">When a `Deconstruct` method is accessible, you can use **positional patterns** to inspect properties of the object and use those properties for a pattern.</span></span>  <span data-ttu-id="cc74f-195">Vezměte v úvahu `Point` následující třídu, která `Deconstruct` obsahuje metodu pro vytvoření diskrétních `X` proměnných `Y`pro a:</span><span class="sxs-lookup"><span data-stu-id="cc74f-195">Consider the following `Point` class that includes a `Deconstruct` method to create discrete variables for `X` and `Y`:</span></span>

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

<span data-ttu-id="cc74f-196">Navíc zvažte následující výčet, který představuje různé pozice kvadrantu:</span><span class="sxs-lookup"><span data-stu-id="cc74f-196">Additionally, consider the following enum that represents various positions of a quadrant:</span></span>

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

<span data-ttu-id="cc74f-197">Následující metoda používá **poziční vzor** k extrakci hodnot `x` a `y`.</span><span class="sxs-lookup"><span data-stu-id="cc74f-197">The following method uses the **positional pattern** to extract the values of `x` and `y`.</span></span> <span data-ttu-id="cc74f-198">Pak pomocí `when` klauzule `Quadrant` určíte bod:</span><span class="sxs-lookup"><span data-stu-id="cc74f-198">Then, it uses a `when` clause to determine the `Quadrant` of the point:</span></span>

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

<span data-ttu-id="cc74f-199">Vzor zahození v předchozím přepínači odpovídá, `x` Pokud `y` buď nebo je 0, ale ne obojí.</span><span class="sxs-lookup"><span data-stu-id="cc74f-199">The discard pattern in the preceding switch matches when either `x` or `y` is 0, but not both.</span></span> <span data-ttu-id="cc74f-200">Výraz přepínače musí buď vytvořit hodnotu, nebo vyvolat výjimku.</span><span class="sxs-lookup"><span data-stu-id="cc74f-200">A switch expression must either produce a value or throw an exception.</span></span> <span data-ttu-id="cc74f-201">Pokud žádný z případů neodpovídá, výraz přepínače vyvolá výjimku.</span><span class="sxs-lookup"><span data-stu-id="cc74f-201">If none of the cases match, the switch expression throws an exception.</span></span> <span data-ttu-id="cc74f-202">Kompilátor vygeneruje upozornění, pokud nepokrýváte všechny možné případy ve výrazu přepínače.</span><span class="sxs-lookup"><span data-stu-id="cc74f-202">The compiler generates a warning for you if you do not cover all possible cases in your switch expression.</span></span>

<span data-ttu-id="cc74f-203">Techniky porovnávání vzorů můžete prozkoumat v tomto [pokročilém kurzu o porovnávání vzorů](../tutorials/pattern-matching.md).</span><span class="sxs-lookup"><span data-stu-id="cc74f-203">You can explore pattern matching techniques in this [advanced tutorial on pattern matching](../tutorials/pattern-matching.md).</span></span>

## <a name="using-declarations"></a><span data-ttu-id="cc74f-204">používání deklarací</span><span class="sxs-lookup"><span data-stu-id="cc74f-204">using declarations</span></span>

<span data-ttu-id="cc74f-205">**Deklarace using** je deklarace proměnné před `using` klíčovým slovem.</span><span class="sxs-lookup"><span data-stu-id="cc74f-205">A **using declaration** is a variable declaration preceded by the `using` keyword.</span></span> <span data-ttu-id="cc74f-206">Dává kompilátoru pokyn, že proměnná, která má být deklarována, by měla být uvolněna na konci ohraničujícího oboru.</span><span class="sxs-lookup"><span data-stu-id="cc74f-206">It tells the compiler that the variable being declared should be disposed at the end of the enclosing scope.</span></span> <span data-ttu-id="cc74f-207">Zvažte například následující kód, který zapisuje textový soubor:</span><span class="sxs-lookup"><span data-stu-id="cc74f-207">For example, consider the following code that writes a text file:</span></span>

```csharp
static void WriteLinesToFile(IEnumerable<string> lines)
{
    using var file = new System.IO.StreamWriter("WriteLines2.txt");
    foreach (string line in lines)
    {
        if (!line.Contains("Second"))
        {
            file.WriteLine(line);
        }
    }
// file is disposed here
}
```

<span data-ttu-id="cc74f-208">V předchozím příkladu je soubor zlikvidován při dosažení uzavírací závorky pro metodu.</span><span class="sxs-lookup"><span data-stu-id="cc74f-208">In the preceding example, the file is disposed when the closing brace for the method is reached.</span></span> <span data-ttu-id="cc74f-209">To je konec oboru, ve kterém `file` je deklarováno.</span><span class="sxs-lookup"><span data-stu-id="cc74f-209">That's the end of the scope in which `file` is declared.</span></span> <span data-ttu-id="cc74f-210">Předchozí kód je ekvivalentní následujícímu kódu, který používá [příkaz Classic using](../language-reference/keywords/using-statement.md):</span><span class="sxs-lookup"><span data-stu-id="cc74f-210">The preceding code is equivalent to the following code that uses the classic [using statement](../language-reference/keywords/using-statement.md):</span></span>

```csharp
static void WriteLinesToFile(IEnumerable<string> lines)
{
    using (var file = new System.IO.StreamWriter("WriteLines2.txt"))
    {
        foreach (string line in lines)
        {
            if (!line.Contains("Second"))
            {
                file.WriteLine(line);
            }
        }
    } // file is disposed here
}
```

<span data-ttu-id="cc74f-211">V předchozím příkladu je soubor zlikvidován při dosažení uzavírací závorky přidružené `using` k příkazu.</span><span class="sxs-lookup"><span data-stu-id="cc74f-211">In the preceding example, the file is disposed when the closing brace associated with the `using` statement is reached.</span></span>

<span data-ttu-id="cc74f-212">V obou případech kompilátor vygeneruje volání `Dispose()`.</span><span class="sxs-lookup"><span data-stu-id="cc74f-212">In both cases, the compiler generates the call to `Dispose()`.</span></span> <span data-ttu-id="cc74f-213">Kompilátor vygeneruje chybu, pokud výraz v `using` příkazu není jednorázově.</span><span class="sxs-lookup"><span data-stu-id="cc74f-213">The compiler generates an error if the expression in the `using` statement is not disposable.</span></span>

## <a name="static-local-functions"></a><span data-ttu-id="cc74f-214">Statické místní funkce</span><span class="sxs-lookup"><span data-stu-id="cc74f-214">Static local functions</span></span>

<span data-ttu-id="cc74f-215">Nyní můžete přidat `static` modifikátor k místním funkcím, aby se zajistilo, že lokální funkce nebude zachytit (odkaz) jakékoli proměnné z ohraničujícího oboru.</span><span class="sxs-lookup"><span data-stu-id="cc74f-215">You can now add the `static` modifier to local functions to ensure that local function doesn't capture (reference) any variables from the enclosing scope.</span></span> <span data-ttu-id="cc74f-216">Tím se vygeneruje `CS8421`"statická místní funkce nemůže obsahovat odkaz na \<proměnnou >."</span><span class="sxs-lookup"><span data-stu-id="cc74f-216">Doing so generates `CS8421`, "A static local function can't contain a reference to \<variable>."</span></span> 

<span data-ttu-id="cc74f-217">Vezměte v úvahu následující kód.</span><span class="sxs-lookup"><span data-stu-id="cc74f-217">Consider the following code.</span></span> <span data-ttu-id="cc74f-218">Místní funkce `LocalFunction` přistupuje k proměnné `y`deklarované v ohraničujícím oboru (metoda `M`).</span><span class="sxs-lookup"><span data-stu-id="cc74f-218">The local function `LocalFunction` accesses the variable `y`, declared in the enclosing scope (the method `M`).</span></span> <span data-ttu-id="cc74f-219">Proto nelze deklarovat s `static`modifikátorem: `LocalFunction`</span><span class="sxs-lookup"><span data-stu-id="cc74f-219">Therefore, `LocalFunction` can't be declared with the `static` modifier:</span></span>

```csharp
int M()
{
    int y;
    LocalFunction();
    return y;

    void LocalFunction() => y = 0;
}
```

<span data-ttu-id="cc74f-220">Následující kód obsahuje statickou místní funkci.</span><span class="sxs-lookup"><span data-stu-id="cc74f-220">The following code contains a static local function.</span></span> <span data-ttu-id="cc74f-221">Může být statický, protože nemá přístup k žádným proměnným v ohraničujícím oboru:</span><span class="sxs-lookup"><span data-stu-id="cc74f-221">It can be static because it doesn't access any variables in the enclosing scope:</span></span>

```csharp
int M()
{
    int y = 5;
    int x = 7;
    return Add(x, y);

    static int Add(int left, int right) => left + right;
}
```

## <a name="disposable-ref-structs"></a><span data-ttu-id="cc74f-222">Struktury odkazů na jedno použití</span><span class="sxs-lookup"><span data-stu-id="cc74f-222">Disposable ref structs</span></span>

<span data-ttu-id="cc74f-223">Deklarace s modifikátorem nesmí implementovat žádná rozhraní, a proto nemůže implementovat <xref:System.IDisposable>. `struct` `ref`</span><span class="sxs-lookup"><span data-stu-id="cc74f-223">A `struct` declared with the `ref` modifier may not implement any interfaces and so cannot implement <xref:System.IDisposable>.</span></span> <span data-ttu-id="cc74f-224">Proto aby `ref struct` bylo možné odstranit, musí mít přístupnou `void Dispose()` metodu.</span><span class="sxs-lookup"><span data-stu-id="cc74f-224">Therefore, to enable a `ref struct` to be disposed, it must have an accessible `void Dispose()` method.</span></span> <span data-ttu-id="cc74f-225">To platí i pro `readonly ref struct` deklarace.</span><span class="sxs-lookup"><span data-stu-id="cc74f-225">This also applies to `readonly ref struct` declarations.</span></span>

## <a name="nullable-reference-types"></a><span data-ttu-id="cc74f-226">Odkazové typy s možnou hodnotou null</span><span class="sxs-lookup"><span data-stu-id="cc74f-226">Nullable reference types</span></span>

<span data-ttu-id="cc74f-227">V kontextu anotace s možnou hodnotou null je jakákoli proměnná typu odkazu považována za **typ odkazu**, který není null.</span><span class="sxs-lookup"><span data-stu-id="cc74f-227">Inside a nullable annotation context, any variable of a reference type is considered to be a **nonnullable reference type**.</span></span> <span data-ttu-id="cc74f-228">Pokud chcete označit, že proměnná může mít hodnotu null, je nutné připojit název `?` typu k deklaraci proměnné jako **typ odkazu s možnou hodnotou null**.</span><span class="sxs-lookup"><span data-stu-id="cc74f-228">If you want to indicate that a variable may be null, you must append the type name with the `?` to declare the variable as a **nullable reference type**.</span></span>

<span data-ttu-id="cc74f-229">Pro nehodnotový odkazový typ kompilátor používá analýzu toků k zajištění, že lokální proměnné jsou inicializovány na hodnotu, která není null, je-li deklarována.</span><span class="sxs-lookup"><span data-stu-id="cc74f-229">For nonnullable reference types, the compiler uses flow analysis to ensure that local variables are initialized to a non-null value when declared.</span></span> <span data-ttu-id="cc74f-230">Pole musí být inicializována během konstrukce.</span><span class="sxs-lookup"><span data-stu-id="cc74f-230">Fields must be initialized during construction.</span></span> <span data-ttu-id="cc74f-231">Kompilátor vygeneruje upozornění, pokud proměnná není nastavena voláním žádné z dostupných konstruktorů nebo inicializátorem.</span><span class="sxs-lookup"><span data-stu-id="cc74f-231">The compiler generates a warning if the variable is not set by a call to any of the available constructors or by an initializer.</span></span> <span data-ttu-id="cc74f-232">Kromě toho nemůžete přiřadit typy odkazů, které mohou mít hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="cc74f-232">Furthermore, nonnullable reference types can't be assigned a value that could be null.</span></span>

<span data-ttu-id="cc74f-233">Typy odkazů s možnou hodnotou null nejsou kontrolovány, aby se zajistilo, že nejsou přiřazeny nebo inicializovány</span><span class="sxs-lookup"><span data-stu-id="cc74f-233">Nullable reference types aren't checked to ensure they aren't assigned or initialized to null.</span></span> <span data-ttu-id="cc74f-234">Kompilátor však používá analýzu toků k zajištění toho, aby byla jakákoli proměnná typu odkazu s možnou hodnotou null zkontrolována před tím, než bude k dispozici nebo přiřazena k neprázdnému typu odkazu.</span><span class="sxs-lookup"><span data-stu-id="cc74f-234">However, the compiler uses flow analysis to ensure that any variable of a nullable reference type is checked against null before it's accessed or assigned to a nonnullable reference type.</span></span>

<span data-ttu-id="cc74f-235">Další informace o této funkci najdete v přehledu [typů odkazů s možnou hodnotou null](../nullable-references.md).</span><span class="sxs-lookup"><span data-stu-id="cc74f-235">You can learn more about the feature in the overview of [nullable reference types](../nullable-references.md).</span></span> <span data-ttu-id="cc74f-236">Zkuste to sami v nové aplikaci v tomto [kurzu odkazové typy s možnou hodnotou null](../tutorials/nullable-reference-types.md).</span><span class="sxs-lookup"><span data-stu-id="cc74f-236">Try it yourself in a new application in this [nullable reference types tutorial](../tutorials/nullable-reference-types.md).</span></span> <span data-ttu-id="cc74f-237">Přečtěte si o krocích k migraci existujícího základu kódu, aby bylo možné používat v [migraci aplikace na použití typů odkazů s možnou hodnotou null v kurzu](../tutorials/upgrade-to-nullable-references.md).</span><span class="sxs-lookup"><span data-stu-id="cc74f-237">Learn about the steps to migrate an existing codebase to make use of nullable reference types in the [migrating an application to use nullable reference types tutorial](../tutorials/upgrade-to-nullable-references.md).</span></span>

## <a name="asynchronous-streams"></a><span data-ttu-id="cc74f-238">Asynchronní proudy</span><span class="sxs-lookup"><span data-stu-id="cc74f-238">Asynchronous streams</span></span>

<span data-ttu-id="cc74f-239">Počínaje C# 8,0 můžete proudy vytvářet a spotřebovávat asynchronně.</span><span class="sxs-lookup"><span data-stu-id="cc74f-239">Starting with C# 8.0, you can create and consume streams asynchronously.</span></span> <span data-ttu-id="cc74f-240">Metoda, která vrací asynchronní datový proud má tři vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="cc74f-240">A method that returns an asynchronous stream has three properties:</span></span>

1. <span data-ttu-id="cc74f-241">Je deklarována s `async` modifikátorem.</span><span class="sxs-lookup"><span data-stu-id="cc74f-241">It's declared with the `async` modifier.</span></span>
1. <span data-ttu-id="cc74f-242">Vrátí <xref:System.Collections.Generic.IAsyncEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="cc74f-242">It returns an <xref:System.Collections.Generic.IAsyncEnumerable%601>.</span></span>
1. <span data-ttu-id="cc74f-243">Metoda obsahuje `yield return` příkazy pro vrácení po sobě jdoucích prvků v asynchronním datovém proudu.</span><span class="sxs-lookup"><span data-stu-id="cc74f-243">The method contains `yield return` statements to return successive elements in the asynchronous stream.</span></span>

<span data-ttu-id="cc74f-244">Spotřebovávání asynchronního datového proudu vyžaduje, abyste `await` `foreach` před klíčovým slovem při vytváření výčtu prvků v datovém proudu přidali klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="cc74f-244">Consuming an asynchronous stream requires you to add the `await` keyword before the `foreach` keyword when you enumerate the elements of the stream.</span></span> <span data-ttu-id="cc74f-245">Přidání klíčového slova vyžaduje metodu, která vytvoří výčet asynchronního datového proudu, který má `async` být deklarován s modifikátorem a vrátí typ povolený pro `async` metodu. `await`</span><span class="sxs-lookup"><span data-stu-id="cc74f-245">Adding the `await` keyword requires the method that enumerates the asynchronous stream to be declared with the `async` modifier and to return a type allowed for an `async` method.</span></span> <span data-ttu-id="cc74f-246">Obvykle to znamená, že <xref:System.Threading.Tasks.Task> vrací <xref:System.Threading.Tasks.Task%601>nebo.</span><span class="sxs-lookup"><span data-stu-id="cc74f-246">Typically that means returning a <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="cc74f-247">Může to být <xref:System.Threading.Tasks.ValueTask> také nebo <xref:System.Threading.Tasks.ValueTask%601>.</span><span class="sxs-lookup"><span data-stu-id="cc74f-247">It can also be a <xref:System.Threading.Tasks.ValueTask> or <xref:System.Threading.Tasks.ValueTask%601>.</span></span> <span data-ttu-id="cc74f-248">Metoda může spotřebovávat a vytvořit asynchronní datový proud, což znamená, že by vrátilo <xref:System.Collections.Generic.IAsyncEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="cc74f-248">A method can both consume and produce an asynchronous stream, which means it would return an <xref:System.Collections.Generic.IAsyncEnumerable%601>.</span></span> <span data-ttu-id="cc74f-249">Následující kód vygeneruje sekvenci od 0 do 19, čekání 100 MS mezi vygenerováním každého čísla:</span><span class="sxs-lookup"><span data-stu-id="cc74f-249">The following code generates a sequence from 0 to 19, waiting 100 ms between generating each number:</span></span>

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

<span data-ttu-id="cc74f-250">Vyčíslení sekvence pomocí `await foreach` příkazu:</span><span class="sxs-lookup"><span data-stu-id="cc74f-250">You would enumerate the sequence using the `await foreach` statement:</span></span>

```csharp
await foreach (var number in GenerateSequence())
{
    Console.WriteLine(number);
}
```

<span data-ttu-id="cc74f-251">Asynchronní streamy si můžete vyzkoušet sami v našem kurzu [vytváření a využívání asynchronních datových proudů](../tutorials/generate-consume-asynchronous-stream.md).</span><span class="sxs-lookup"><span data-stu-id="cc74f-251">You can try asynchronous streams yourself in our tutorial on [creating and consuming async streams](../tutorials/generate-consume-asynchronous-stream.md).</span></span>

## <a name="indices-and-ranges"></a><span data-ttu-id="cc74f-252">Indexy a rozsahy</span><span class="sxs-lookup"><span data-stu-id="cc74f-252">Indices and ranges</span></span>

<span data-ttu-id="cc74f-253">Rozsahy a indexy poskytují stručnou syntaxi pro určení dílčích rozsahů v poli, <xref:System.Span%601>nebo. <xref:System.ReadOnlySpan%601></span><span class="sxs-lookup"><span data-stu-id="cc74f-253">Ranges and indices provide a succinct syntax for specifying subranges in an array, <xref:System.Span%601>, or <xref:System.ReadOnlySpan%601>.</span></span>

<span data-ttu-id="cc74f-254">Tato podpora jazyků spoléhá na dva nové typy a dva nové operátory:</span><span class="sxs-lookup"><span data-stu-id="cc74f-254">This language support relies on two new types, and two new operators:</span></span>

- <span data-ttu-id="cc74f-255"><xref:System.Index?displayProperty=nameWithType>představuje index do sekvence.</span><span class="sxs-lookup"><span data-stu-id="cc74f-255"><xref:System.Index?displayProperty=nameWithType> represents an index into a sequence.</span></span>
- <span data-ttu-id="cc74f-256">`^` Operátor, který určuje, že index je relativní ke konci sekvence.</span><span class="sxs-lookup"><span data-stu-id="cc74f-256">The `^` operator, which specifies that an index is relative to the end of the sequence.</span></span>
- <span data-ttu-id="cc74f-257"><xref:System.Range?displayProperty=nameWithType>představuje dílčí rozsah sekvence.</span><span class="sxs-lookup"><span data-stu-id="cc74f-257"><xref:System.Range?displayProperty=nameWithType> represents a sub range of a sequence.</span></span>
- <span data-ttu-id="cc74f-258">Operátor Range (`..`), který určuje začátek a konec rozsahu jako jeho operandy.</span><span class="sxs-lookup"><span data-stu-id="cc74f-258">The Range operator (`..`), which specifies the start and end of a range as its operands.</span></span>

<span data-ttu-id="cc74f-259">Pojďme začít s pravidly pro indexy.</span><span class="sxs-lookup"><span data-stu-id="cc74f-259">Let's start with the rules for indexes.</span></span> <span data-ttu-id="cc74f-260">Zvažte pole `sequence`.</span><span class="sxs-lookup"><span data-stu-id="cc74f-260">Consider an array `sequence`.</span></span> <span data-ttu-id="cc74f-261">Index je stejný jako `sequence[0]`. `0`</span><span class="sxs-lookup"><span data-stu-id="cc74f-261">The `0` index is the same as `sequence[0]`.</span></span> <span data-ttu-id="cc74f-262">Index je stejný jako `sequence[sequence.Length]`. `^0`</span><span class="sxs-lookup"><span data-stu-id="cc74f-262">The `^0` index is the same as `sequence[sequence.Length]`.</span></span> <span data-ttu-id="cc74f-263">Všimněte si `sequence[^0]` , že vyvolá výjimku, stejně jako `sequence[sequence.Length]` .</span><span class="sxs-lookup"><span data-stu-id="cc74f-263">Note that `sequence[^0]` does throw an exception, just as `sequence[sequence.Length]` does.</span></span> <span data-ttu-id="cc74f-264">Pro jakékoli číslo `n`je index `^n` stejný jako `sequence.Length - n`.</span><span class="sxs-lookup"><span data-stu-id="cc74f-264">For any number `n`, the index `^n` is the same as `sequence.Length - n`.</span></span>

<span data-ttu-id="cc74f-265">Rozsah Určuje *začátek* a *konec* rozsahu.</span><span class="sxs-lookup"><span data-stu-id="cc74f-265">A range specifies the *start* and *end* of a range.</span></span> <span data-ttu-id="cc74f-266">Začátek rozsahu je včetně, ale konec rozsahu je exkluzivní, což znamená, že *začátek* je zahrnut v rozsahu, ale *konec* není zahrnutý v rozsahu.</span><span class="sxs-lookup"><span data-stu-id="cc74f-266">The start of the range is inclusive, but the end of the range is exclusive, meaning the *start* is included in the range but the *end* is not included in the range.</span></span> <span data-ttu-id="cc74f-267">Rozsah `[0..^0]` představuje celý rozsah, stejně jako `[0..sequence.Length]` představuje celý rozsah.</span><span class="sxs-lookup"><span data-stu-id="cc74f-267">The range `[0..^0]` represents the entire range, just as `[0..sequence.Length]` represents the entire range.</span></span> 

<span data-ttu-id="cc74f-268">Pojďme se podívat na několik příkladů.</span><span class="sxs-lookup"><span data-stu-id="cc74f-268">Let's look at a few examples.</span></span> <span data-ttu-id="cc74f-269">Vezměte v úvahu následující pole s poznámkou s jeho indexem od začátku do konce:</span><span class="sxs-lookup"><span data-stu-id="cc74f-269">Consider the following array, annotated with its index from the start and from the end:</span></span>

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

<span data-ttu-id="cc74f-270">Poslední slovo můžete načíst s `^1` indexem:</span><span class="sxs-lookup"><span data-stu-id="cc74f-270">You can retrieve the last word with the `^1` index:</span></span>

```csharp
Console.WriteLine($"The last word is {words[^1]}");
// writes "dog"
```

<span data-ttu-id="cc74f-271">Následující kód vytvoří dílčí rozsah s slovy "Rychlá", "hnědá" a "Fox".</span><span class="sxs-lookup"><span data-stu-id="cc74f-271">The following code creates a subrange with the words "quick", "brown", and "fox".</span></span> <span data-ttu-id="cc74f-272">Zahrnuje `words[1]` .`words[3]`</span><span class="sxs-lookup"><span data-stu-id="cc74f-272">It includes `words[1]` through `words[3]`.</span></span> <span data-ttu-id="cc74f-273">Element `words[4]` není v rozsahu.</span><span class="sxs-lookup"><span data-stu-id="cc74f-273">The element `words[4]` is not in the range.</span></span>

```csharp
var quickBrownFox = words[1..4];
```

<span data-ttu-id="cc74f-274">Následující kód vytvoří dílčí rozsah s "opožděným" a "pes".</span><span class="sxs-lookup"><span data-stu-id="cc74f-274">The following code creates a subrange with "lazy" and "dog".</span></span> <span data-ttu-id="cc74f-275">Zahrnuje `words[^2]` a .`words[^1]`</span><span class="sxs-lookup"><span data-stu-id="cc74f-275">It includes `words[^2]` and `words[^1]`.</span></span> <span data-ttu-id="cc74f-276">Koncový index `words[^0]` není zahrnutý:</span><span class="sxs-lookup"><span data-stu-id="cc74f-276">The end index `words[^0]` is not included:</span></span>

```csharp
var lazyDog = words[^2..^0];
```

<span data-ttu-id="cc74f-277">V následujících příkladech jsou vytvořeny rozsahy, které jsou otevřeny pro začátek, konec nebo obojí:</span><span class="sxs-lookup"><span data-stu-id="cc74f-277">The following examples create ranges that are open ended for the start, end, or both:</span></span>

```csharp
var allWords = words[..]; // contains "The" through "dog".
var firstPhrase = words[..4]; // contains "The" through "fox"
var lastPhrase = words[6..]; // contains "the", "lazy" and "dog"
```

<span data-ttu-id="cc74f-278">Rozsahy můžete deklarovat také jako proměnné:</span><span class="sxs-lookup"><span data-stu-id="cc74f-278">You can also declare ranges as variables:</span></span>

```csharp
Range phrase = 1..4;
```

<span data-ttu-id="cc74f-279">Rozsah lze použít `[` v rámci znaků a `]` :</span><span class="sxs-lookup"><span data-stu-id="cc74f-279">The range can then be used inside the `[` and `]` characters:</span></span>

```csharp
var text = words[phrase];
```

<span data-ttu-id="cc74f-280">Můžete prozkoumat další informace o indexech a oblastech v kurzu týkající se [indexů a rozsahů](../tutorials/ranges-indexes.md).</span><span class="sxs-lookup"><span data-stu-id="cc74f-280">You can explore more about indices and ranges in the tutorial on [indices and ranges](../tutorials/ranges-indexes.md).</span></span>

## <a name="enhancement-of-interpolated-verbatim-strings"></a><span data-ttu-id="cc74f-281">Vylepšení interpolované doslovného řetězce</span><span class="sxs-lookup"><span data-stu-id="cc74f-281">Enhancement of interpolated verbatim strings</span></span>

<span data-ttu-id="cc74f-282">[](../language-reference/tokens/interpolated.md) `$@"..."` `@$"..."` Pořadí a `@`tokeny v interpolované doslovném řetězci mohou být libovolné: a jsou platné interpolované řetězce. `$`</span><span class="sxs-lookup"><span data-stu-id="cc74f-282">Order of the `$` and `@` tokens in [interpolated](../language-reference/tokens/interpolated.md) verbatim strings can be any: both `$@"..."` and `@$"..."` are valid interpolated verbatim strings.</span></span> <span data-ttu-id="cc74f-283">V dřívějších C# verzích `$` se token `@` musí vyskytovat před tokenem.</span><span class="sxs-lookup"><span data-stu-id="cc74f-283">In earlier C# versions, the `$` token must appear before the `@` token.</span></span>
