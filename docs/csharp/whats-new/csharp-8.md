---
title: Co je nového v C# 8.0 - C# Guide
description: Získejte přehled o nových funkcích dostupných v c# 8.0.
ms.date: 09/20/2019
ms.openlocfilehash: 0013f621268e2a4f1b916b226d83d18c68445ed1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399677"
---
# <a name="whats-new-in-c-80"></a><span data-ttu-id="4f809-103">Co je nového v C# 8.0</span><span class="sxs-lookup"><span data-stu-id="4f809-103">What's new in C# 8.0</span></span>

<span data-ttu-id="4f809-104">C# 8.0 přidává do jazyka C# následující funkce a vylepšení:</span><span class="sxs-lookup"><span data-stu-id="4f809-104">C# 8.0 adds the following features and enhancements to the C# language:</span></span>

- [<span data-ttu-id="4f809-105">Členové pouze pro čtení</span><span class="sxs-lookup"><span data-stu-id="4f809-105">Readonly members</span></span>](#readonly-members)
- [<span data-ttu-id="4f809-106">Výchozí metody rozhraní</span><span class="sxs-lookup"><span data-stu-id="4f809-106">Default interface methods</span></span>](#default-interface-methods)
- <span data-ttu-id="4f809-107">[Vylepšení porovnávání vzorů](#more-patterns-in-more-places):</span><span class="sxs-lookup"><span data-stu-id="4f809-107">[Pattern matching enhancements](#more-patterns-in-more-places):</span></span>
  - [<span data-ttu-id="4f809-108">Přepnutí výrazů</span><span class="sxs-lookup"><span data-stu-id="4f809-108">Switch expressions</span></span>](#switch-expressions)
  - [<span data-ttu-id="4f809-109">Vzory vlastností</span><span class="sxs-lookup"><span data-stu-id="4f809-109">Property patterns</span></span>](#property-patterns)
  - [<span data-ttu-id="4f809-110">Řazené kolekce členů</span><span class="sxs-lookup"><span data-stu-id="4f809-110">Tuple patterns</span></span>](#tuple-patterns)
  - [<span data-ttu-id="4f809-111">Poziční vzory</span><span class="sxs-lookup"><span data-stu-id="4f809-111">Positional patterns</span></span>](#positional-patterns)
- [<span data-ttu-id="4f809-112">Použití deklarací</span><span class="sxs-lookup"><span data-stu-id="4f809-112">Using declarations</span></span>](#using-declarations)
- [<span data-ttu-id="4f809-113">Statické místní funkce</span><span class="sxs-lookup"><span data-stu-id="4f809-113">Static local functions</span></span>](#static-local-functions)
- [<span data-ttu-id="4f809-114">Jednorázové ref struktury</span><span class="sxs-lookup"><span data-stu-id="4f809-114">Disposable ref structs</span></span>](#disposable-ref-structs)
- [<span data-ttu-id="4f809-115">Odkazové typy s možnou hodnotou null</span><span class="sxs-lookup"><span data-stu-id="4f809-115">Nullable reference types</span></span>](#nullable-reference-types)
- [<span data-ttu-id="4f809-116">Asynchronní datové proudy</span><span class="sxs-lookup"><span data-stu-id="4f809-116">Asynchronous streams</span></span>](#asynchronous-streams)
- [<span data-ttu-id="4f809-117">Indexy a rozsahy</span><span class="sxs-lookup"><span data-stu-id="4f809-117">Indices and ranges</span></span>](#indices-and-ranges)
- [<span data-ttu-id="4f809-118">Přiřazení null-coalescing</span><span class="sxs-lookup"><span data-stu-id="4f809-118">Null-coalescing assignment</span></span>](#null-coalescing-assignment)
- [<span data-ttu-id="4f809-119">Nespravované konstruované typy</span><span class="sxs-lookup"><span data-stu-id="4f809-119">Unmanaged constructed types</span></span>](#unmanaged-constructed-types)
- [<span data-ttu-id="4f809-120">Stackalloc ve vnořených výrazech</span><span class="sxs-lookup"><span data-stu-id="4f809-120">Stackalloc in nested expressions</span></span>](#stackalloc-in-nested-expressions)
- [<span data-ttu-id="4f809-121">Vylepšení interpolovaných doslovných řetězců</span><span class="sxs-lookup"><span data-stu-id="4f809-121">Enhancement of interpolated verbatim strings</span></span>](#enhancement-of-interpolated-verbatim-strings)

<span data-ttu-id="4f809-122">C# 8.0 je podporován na **rozhraních .NET Core 3.x** a **.NET Standard 2.1**.</span><span class="sxs-lookup"><span data-stu-id="4f809-122">C# 8.0 is supported on **.NET Core 3.x** and **.NET Standard 2.1**.</span></span> <span data-ttu-id="4f809-123">Další informace naleznete v [tématu C# language versioning](../language-reference/configure-language-version.md).</span><span class="sxs-lookup"><span data-stu-id="4f809-123">For more information, see [C# language versioning](../language-reference/configure-language-version.md).</span></span>

<span data-ttu-id="4f809-124">Zbývající část tohoto článku stručně popisuje tyto funkce.</span><span class="sxs-lookup"><span data-stu-id="4f809-124">The remainder of this article briefly describes these features.</span></span> <span data-ttu-id="4f809-125">Pokud jsou k dispozici podrobné články, jsou k dispozici odkazy na tyto kurzy a přehledy.</span><span class="sxs-lookup"><span data-stu-id="4f809-125">Where in-depth articles are available, links to those tutorials and overviews are provided.</span></span> <span data-ttu-id="4f809-126">Tyto funkce můžete prozkoumat ve `dotnet try` vašem prostředí pomocí globálního nástroje:</span><span class="sxs-lookup"><span data-stu-id="4f809-126">You can explore these features in your environment using the `dotnet try` global tool:</span></span>

1. <span data-ttu-id="4f809-127">Nainstalujte globální nástroj [dotnet-try.](https://github.com/dotnet/try/blob/master/README.md#setup)</span><span class="sxs-lookup"><span data-stu-id="4f809-127">Install the [dotnet-try](https://github.com/dotnet/try/blob/master/README.md#setup) global tool.</span></span>
1. <span data-ttu-id="4f809-128">Klonovat úložiště [dotnet/try-samples.](https://github.com/dotnet/try-samples)</span><span class="sxs-lookup"><span data-stu-id="4f809-128">Clone the [dotnet/try-samples](https://github.com/dotnet/try-samples) repository.</span></span>
1. <span data-ttu-id="4f809-129">Nastavte aktuální adresář do podadresáře *csharp8* pro úložiště *try-samples.*</span><span class="sxs-lookup"><span data-stu-id="4f809-129">Set the current directory to the *csharp8* subdirectory for the *try-samples* repository.</span></span>
1. <span data-ttu-id="4f809-130">Spusťte `dotnet try`.</span><span class="sxs-lookup"><span data-stu-id="4f809-130">Run `dotnet try`.</span></span>

## <a name="readonly-members"></a><span data-ttu-id="4f809-131">Členové pouze pro čtení</span><span class="sxs-lookup"><span data-stu-id="4f809-131">Readonly members</span></span>

<span data-ttu-id="4f809-132">`readonly` Modifikátor můžete použít na členy struktury.</span><span class="sxs-lookup"><span data-stu-id="4f809-132">You can apply the `readonly` modifier to members of a struct.</span></span> <span data-ttu-id="4f809-133">Označuje, že člen nemění stav.</span><span class="sxs-lookup"><span data-stu-id="4f809-133">It indicates that the member doesn't modify state.</span></span> <span data-ttu-id="4f809-134">Je podrobnější než použití `readonly` modifikátoru `struct` na deklaraci.</span><span class="sxs-lookup"><span data-stu-id="4f809-134">It's more granular than applying the `readonly` modifier to a `struct` declaration.</span></span>  <span data-ttu-id="4f809-135">Zvažte následující proměnlivou strukturu:</span><span class="sxs-lookup"><span data-stu-id="4f809-135">Consider the following mutable struct:</span></span>

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

<span data-ttu-id="4f809-136">Stejně jako většina `ToString()` struktur, metoda nemění stav.</span><span class="sxs-lookup"><span data-stu-id="4f809-136">Like most structs, the `ToString()` method doesn't modify state.</span></span> <span data-ttu-id="4f809-137">Můžete to označit přidáním modifikátoru `readonly` do deklarace `ToString()`:</span><span class="sxs-lookup"><span data-stu-id="4f809-137">You could indicate that by adding the `readonly` modifier to the declaration of `ToString()`:</span></span>

```csharp
public readonly override string ToString() =>
    $"({X}, {Y}) is {Distance} from the origin";
```

<span data-ttu-id="4f809-138">Předchozí změna generuje upozornění kompilátoru, `ToString` protože `Distance` přistupuje `readonly`k vlastnosti, která není označena :</span><span class="sxs-lookup"><span data-stu-id="4f809-138">The preceding change generates a compiler warning, because `ToString` accesses the `Distance` property, which isn't marked `readonly`:</span></span>

```console
warning CS8656: Call to non-readonly member 'Point.Distance.get' from a 'readonly' member results in an implicit copy of 'this'
```

<span data-ttu-id="4f809-139">Kompilátor vás upozorní, když potřebuje vytvořit obrannou kopii.</span><span class="sxs-lookup"><span data-stu-id="4f809-139">The compiler warns you when it needs to create a defensive copy.</span></span>  <span data-ttu-id="4f809-140">Vlastnost `Distance` nezmění stav, takže můžete opravit toto upozornění `readonly` přidáním modifikátor u deklarace:</span><span class="sxs-lookup"><span data-stu-id="4f809-140">The `Distance` property doesn't change state, so you can fix this warning by adding the `readonly` modifier to the declaration:</span></span>

```csharp
public readonly double Distance => Math.Sqrt(X * X + Y * Y);
```

<span data-ttu-id="4f809-141">Všimněte `readonly` si, že modifikátor je nezbytné pro vlastnost jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="4f809-141">Notice that the `readonly` modifier is necessary on a read-only property.</span></span> <span data-ttu-id="4f809-142">Kompilátor nepředpokládá, `get` že přístupové objektů nemění stav; musíte deklarovat `readonly` explicitně.</span><span class="sxs-lookup"><span data-stu-id="4f809-142">The compiler doesn't assume `get` accessors don't modify state; you must declare `readonly` explicitly.</span></span> <span data-ttu-id="4f809-143">Automaticky implementované vlastnosti jsou výjimkou; kompilátor bude považovat všechny automaticky implementované gettery za jen pro čtení, takže zde není nutné přidávat `readonly` modifikátor do vlastností `X` a. `Y`</span><span class="sxs-lookup"><span data-stu-id="4f809-143">Auto-implemented properties are an exception; the compiler will treat all auto-implemented getters as readonly, so here there's no need to add the `readonly` modifier to the `X` and `Y` properties.</span></span>

<span data-ttu-id="4f809-144">Kompilátor vynucuje pravidlo, že `readonly` členové nemění stav.</span><span class="sxs-lookup"><span data-stu-id="4f809-144">The compiler does enforce the rule that `readonly` members don't modify state.</span></span> <span data-ttu-id="4f809-145">Následující metoda nebude kompilovat, `readonly` pokud odebrat modifikátor:</span><span class="sxs-lookup"><span data-stu-id="4f809-145">The following method won't compile unless you remove the `readonly` modifier:</span></span>

```csharp
public readonly void Translate(int xOffset, int yOffset)
{
    X += xOffset;
    Y += yOffset;
}
```

<span data-ttu-id="4f809-146">Tato funkce umožňuje určit záměr návrhu, aby ho kompilátor mohl vynutit, a provést optimalizace na základě tohoto záměru.</span><span class="sxs-lookup"><span data-stu-id="4f809-146">This feature lets you specify your design intent so the compiler can enforce it, and make optimizations based on that intent.</span></span> <span data-ttu-id="4f809-147">Další informace o členech readonly se [`readonly`](../language-reference/keywords/readonly.md#readonly-member-examples)dozvíte v článku s odkazy na jazyk na .</span><span class="sxs-lookup"><span data-stu-id="4f809-147">You can learn more about readonly members in the language reference article on [`readonly`](../language-reference/keywords/readonly.md#readonly-member-examples).</span></span>

## <a name="default-interface-methods"></a><span data-ttu-id="4f809-148">Výchozí metody rozhraní</span><span class="sxs-lookup"><span data-stu-id="4f809-148">Default interface methods</span></span>

<span data-ttu-id="4f809-149">Nyní můžete přidat členy do rozhraní a poskytnout implementaci pro tyto členy.</span><span class="sxs-lookup"><span data-stu-id="4f809-149">You can now add members to interfaces and provide an implementation for those members.</span></span> <span data-ttu-id="4f809-150">Tato jazyková funkce umožňuje autorům rozhraní API přidávat metody do rozhraní v novějších verzích bez přerušení zdrojové nebo binární kompatibility s existujícími implementacemi tohoto rozhraní.</span><span class="sxs-lookup"><span data-stu-id="4f809-150">This language feature enables API authors to add methods to an interface in later versions without breaking source or binary compatibility with existing implementations of that interface.</span></span> <span data-ttu-id="4f809-151">Existující implementace *dědí* výchozí implementaci.</span><span class="sxs-lookup"><span data-stu-id="4f809-151">Existing implementations *inherit* the default implementation.</span></span> <span data-ttu-id="4f809-152">Tato funkce také umožňuje C# spolupracovat s api, která cílí na Android nebo Swift, které podporují podobné funkce.</span><span class="sxs-lookup"><span data-stu-id="4f809-152">This feature also enables C# to interoperate with APIs that target Android or Swift, which support similar features.</span></span> <span data-ttu-id="4f809-153">Výchozí metody rozhraní také umožňují scénáře podobné funkci jazyka "vlastnosti".</span><span class="sxs-lookup"><span data-stu-id="4f809-153">Default interface methods also enable scenarios similar to a "traits" language feature.</span></span>

<span data-ttu-id="4f809-154">Výchozí metody rozhraní ovlivňují mnoho scénářů a prvků jazyka.</span><span class="sxs-lookup"><span data-stu-id="4f809-154">Default interface methods affects many scenarios and language elements.</span></span> <span data-ttu-id="4f809-155">Náš první výukový program se zabývá [aktualizací rozhraní s výchozími implementacemi](../tutorials/default-interface-methods-versions.md).</span><span class="sxs-lookup"><span data-stu-id="4f809-155">Our first tutorial covers [updating an interface with default implementations](../tutorials/default-interface-methods-versions.md).</span></span> <span data-ttu-id="4f809-156">Další výukové programy a referenční aktualizace přicházejí včas pro obecné vydání.</span><span class="sxs-lookup"><span data-stu-id="4f809-156">Other tutorials and reference updates are coming in time for general release.</span></span>

## <a name="more-patterns-in-more-places"></a><span data-ttu-id="4f809-157">Více vzorů na více místech</span><span class="sxs-lookup"><span data-stu-id="4f809-157">More patterns in more places</span></span>

<span data-ttu-id="4f809-158">**Porovnávání vzorů** poskytuje nástroje pro poskytování funkcí závislých na tvarech napříč souvisejícími, ale různými druhy dat.</span><span class="sxs-lookup"><span data-stu-id="4f809-158">**Pattern matching** gives tools to provide shape-dependent functionality across related but different kinds of data.</span></span> <span data-ttu-id="4f809-159">C# 7.0 zavedlsyntaxi pro vzory typu a [`is`](../language-reference/keywords/is.md) konstantní vzorky pomocí výrazu a příkazu. [`switch`](../language-reference/keywords/switch.md)</span><span class="sxs-lookup"><span data-stu-id="4f809-159">C# 7.0 introduced syntax for type patterns and constant patterns by using the [`is`](../language-reference/keywords/is.md) expression and the [`switch`](../language-reference/keywords/switch.md) statement.</span></span> <span data-ttu-id="4f809-160">Tyto funkce představovaly první předběžné kroky směrem k podpoře programovacích paradigmat, kde data a funkce žijí odděleně.</span><span class="sxs-lookup"><span data-stu-id="4f809-160">These features represented the first tentative steps toward supporting programming paradigms where data and functionality live apart.</span></span> <span data-ttu-id="4f809-161">Vzhledem k tomu, že se odvětví posune směrem k více mikroslužbám a dalším cloudovým architekturám, jsou potřeba další jazykové nástroje.</span><span class="sxs-lookup"><span data-stu-id="4f809-161">As the industry moves toward more microservices and other cloud-based architectures, other language tools are needed.</span></span>

<span data-ttu-id="4f809-162">C# 8.0 rozšiřuje tento slovník, takže můžete použít více vzor výrazy na více místech v kódu.</span><span class="sxs-lookup"><span data-stu-id="4f809-162">C# 8.0 expands this vocabulary so you can use more pattern expressions in more places in your code.</span></span> <span data-ttu-id="4f809-163">Zvažte tyto funkce, když jsou vaše data a funkce oddělené.</span><span class="sxs-lookup"><span data-stu-id="4f809-163">Consider these features when your data and functionality are separate.</span></span> <span data-ttu-id="4f809-164">Zvažte porovnávání vzorů, když vaše algoritmy závisí na skutečnosti, než je typ runtime objektu.</span><span class="sxs-lookup"><span data-stu-id="4f809-164">Consider pattern matching when your algorithms depend on a fact other than the runtime type of an object.</span></span> <span data-ttu-id="4f809-165">Tyto techniky poskytují další způsob, jak vyjádřit návrhy.</span><span class="sxs-lookup"><span data-stu-id="4f809-165">These techniques provide another way to express designs.</span></span>

<span data-ttu-id="4f809-166">Kromě nových vzorů na nových místech c# 8.0 přidává **rekurzivní vzory**.</span><span class="sxs-lookup"><span data-stu-id="4f809-166">In addition to new patterns in new places, C# 8.0 adds **recursive patterns**.</span></span> <span data-ttu-id="4f809-167">Výsledkem libovolného výrazu vzoru je výraz.</span><span class="sxs-lookup"><span data-stu-id="4f809-167">The result of any pattern expression is an expression.</span></span> <span data-ttu-id="4f809-168">Rekurzivní vzorek je jednoduše výraz vzorku aplikovaný na výstup jiného výrazu vzorku.</span><span class="sxs-lookup"><span data-stu-id="4f809-168">A recursive pattern is simply a pattern expression applied to the output of another pattern expression.</span></span>

### <a name="switch-expressions"></a><span data-ttu-id="4f809-169">Přepnutí výrazů</span><span class="sxs-lookup"><span data-stu-id="4f809-169">Switch expressions</span></span>

<span data-ttu-id="4f809-170">Často příkaz [`switch`](../language-reference/keywords/switch.md) vytvoří hodnotu v každém `case` z jeho bloků.</span><span class="sxs-lookup"><span data-stu-id="4f809-170">Often, a [`switch`](../language-reference/keywords/switch.md) statement produces a value in each of its `case` blocks.</span></span> <span data-ttu-id="4f809-171">**Přepínací výrazy** umožňují používat stručnější syntaxi výrazů.</span><span class="sxs-lookup"><span data-stu-id="4f809-171">**Switch expressions** enable you to use more concise expression syntax.</span></span> <span data-ttu-id="4f809-172">Existuje méně opakujících se `case` `break` a klíčových slov a méně složených závorek.</span><span class="sxs-lookup"><span data-stu-id="4f809-172">There are fewer repetitive `case` and `break` keywords, and fewer curly braces.</span></span>  <span data-ttu-id="4f809-173">Jako příklad zvažte následující výčet, který uvádí barvy duhy:</span><span class="sxs-lookup"><span data-stu-id="4f809-173">As an example, consider the following enum that lists the colors of the rainbow:</span></span>

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

<span data-ttu-id="4f809-174">Pokud `RGBColor` aplikace definovala `R`typ, který je `G` `B` vytvořen z , a `Rainbow` komponenty, můžete převést hodnotu na jeho hodnoty RGB pomocí následující metody obsahující výraz přepínače:</span><span class="sxs-lookup"><span data-stu-id="4f809-174">If your application defined an `RGBColor` type that is constructed from the `R`, `G` and `B` components, you could convert a `Rainbow` value to its RGB values using the following method containing a switch expression:</span></span>

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

<span data-ttu-id="4f809-175">Existuje zde několik vylepšení syntaxe:</span><span class="sxs-lookup"><span data-stu-id="4f809-175">There are several syntax improvements here:</span></span>

- <span data-ttu-id="4f809-176">Proměnná předchází klíčovému slovu. `switch`</span><span class="sxs-lookup"><span data-stu-id="4f809-176">The variable comes before the `switch` keyword.</span></span> <span data-ttu-id="4f809-177">Různé pořadí umožňuje vizuálně snadno odlišit výraz přepínače od příkazu switch.</span><span class="sxs-lookup"><span data-stu-id="4f809-177">The different order makes it visually easy to distinguish the switch expression from the switch statement.</span></span>
- <span data-ttu-id="4f809-178">`case` Prvky `:` a jsou `=>`nahrazeny písmenem .</span><span class="sxs-lookup"><span data-stu-id="4f809-178">The `case` and `:` elements are replaced with `=>`.</span></span> <span data-ttu-id="4f809-179">Je to stručnější a intuitivnější.</span><span class="sxs-lookup"><span data-stu-id="4f809-179">It's more concise and intuitive.</span></span>
- <span data-ttu-id="4f809-180">Pouzdro `default` je nahrazeno `_` výmětem.</span><span class="sxs-lookup"><span data-stu-id="4f809-180">The `default` case is replaced with a `_` discard.</span></span>
- <span data-ttu-id="4f809-181">Těla jsou výrazy, ne příkazy.</span><span class="sxs-lookup"><span data-stu-id="4f809-181">The bodies are expressions, not statements.</span></span>

<span data-ttu-id="4f809-182">Kontrast, že s ekvivalentní `switch` kód pomocí klasické hopříkaz:</span><span class="sxs-lookup"><span data-stu-id="4f809-182">Contrast that with the equivalent code using the classic `switch` statement:</span></span>

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

### <a name="property-patterns"></a><span data-ttu-id="4f809-183">Vzory vlastností</span><span class="sxs-lookup"><span data-stu-id="4f809-183">Property patterns</span></span>

<span data-ttu-id="4f809-184">**Vzor vlastnosti** umožňuje shodovat s vlastnostmi zkoumaného objektu.</span><span class="sxs-lookup"><span data-stu-id="4f809-184">The **property pattern** enables you to match on properties of the object examined.</span></span> <span data-ttu-id="4f809-185">Zvažte web elektronického obchodu, který musí vypočítat DPH na základě adresy kupujícího.</span><span class="sxs-lookup"><span data-stu-id="4f809-185">Consider an eCommerce site that must compute sales tax based on the buyer's address.</span></span> <span data-ttu-id="4f809-186">Tento výpočt není hlavní odpovědností `Address` třídy.</span><span class="sxs-lookup"><span data-stu-id="4f809-186">That computation isn't a core responsibility of an `Address` class.</span></span> <span data-ttu-id="4f809-187">To se bude měnit v průběhu času, pravděpodobně častěji než změny formátu adresy.</span><span class="sxs-lookup"><span data-stu-id="4f809-187">It will change over time, likely more often than address format changes.</span></span> <span data-ttu-id="4f809-188">Částka DPH závisí na `State` vlastnosti adresy.</span><span class="sxs-lookup"><span data-stu-id="4f809-188">The amount of sales tax depends on the `State` property of the address.</span></span> <span data-ttu-id="4f809-189">Následující metoda používá vlastnost vzor pro výpočet DPH z adresy a ceny:</span><span class="sxs-lookup"><span data-stu-id="4f809-189">The following method uses the property pattern to compute the sales tax from the address and the price:</span></span>

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

<span data-ttu-id="4f809-190">Porovnávání vzorů vytvoří stručnou syntaxi pro vyjádření tohoto algoritmu.</span><span class="sxs-lookup"><span data-stu-id="4f809-190">Pattern matching creates a concise syntax for expressing this algorithm.</span></span>

### <a name="tuple-patterns"></a><span data-ttu-id="4f809-191">Řazené kolekce členů</span><span class="sxs-lookup"><span data-stu-id="4f809-191">Tuple patterns</span></span>

<span data-ttu-id="4f809-192">Některé algoritmy závisí na více vstupech.</span><span class="sxs-lookup"><span data-stu-id="4f809-192">Some algorithms depend on multiple inputs.</span></span> <span data-ttu-id="4f809-193">**Vzorky n-tice** umožňují přepínat na základě více hodnot vyjádřených jako [řazená kolekce členů](../tuples.md).</span><span class="sxs-lookup"><span data-stu-id="4f809-193">**Tuple patterns** allow you to switch based on multiple values expressed as a [tuple](../tuples.md).</span></span>  <span data-ttu-id="4f809-194">Následující kód ukazuje výraz přepínače pro hru *rock, papír, nůžky*:</span><span class="sxs-lookup"><span data-stu-id="4f809-194">The following code shows a switch expression for the game *rock, paper, scissors*:</span></span>

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

<span data-ttu-id="4f809-195">Zprávy označují vítěze.</span><span class="sxs-lookup"><span data-stu-id="4f809-195">The messages indicate the winner.</span></span> <span data-ttu-id="4f809-196">Zahození případu představuje tři kombinace pro vazby nebo jiné textové vstupy.</span><span class="sxs-lookup"><span data-stu-id="4f809-196">The discard case represents the three combinations for ties, or other text inputs.</span></span>

### <a name="positional-patterns"></a><span data-ttu-id="4f809-197">Poziční vzory</span><span class="sxs-lookup"><span data-stu-id="4f809-197">Positional patterns</span></span>

<span data-ttu-id="4f809-198">Některé typy `Deconstruct` zahrnují metodu, která dekonstruuje jeho vlastnosti do diskrétní proměnné.</span><span class="sxs-lookup"><span data-stu-id="4f809-198">Some types include a `Deconstruct` method that deconstructs its properties into discrete variables.</span></span> <span data-ttu-id="4f809-199">Pokud `Deconstruct` je metoda přístupná, můžete použít **poziční vzorky** ke kontrole vlastností objektu a použít tyto vlastnosti pro vzorek.</span><span class="sxs-lookup"><span data-stu-id="4f809-199">When a `Deconstruct` method is accessible, you can use **positional patterns** to inspect properties of the object and use those properties for a pattern.</span></span>  <span data-ttu-id="4f809-200">Zvažte `Point` následující třídu, která obsahuje metodu `Deconstruct` `X` pro `Y`vytvoření diskrétních proměnných pro a:</span><span class="sxs-lookup"><span data-stu-id="4f809-200">Consider the following `Point` class that includes a `Deconstruct` method to create discrete variables for `X` and `Y`:</span></span>

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

<span data-ttu-id="4f809-201">Kromě toho zvažte následující výčt, který představuje různé pozice kvadrantu:</span><span class="sxs-lookup"><span data-stu-id="4f809-201">Additionally, consider the following enum that represents various positions of a quadrant:</span></span>

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

<span data-ttu-id="4f809-202">Následující metoda používá **poziční vzor** `x` extrahovat hodnoty a `y`.</span><span class="sxs-lookup"><span data-stu-id="4f809-202">The following method uses the **positional pattern** to extract the values of `x` and `y`.</span></span> <span data-ttu-id="4f809-203">Potom používá klauzuli `when` k `Quadrant` určení bodu:</span><span class="sxs-lookup"><span data-stu-id="4f809-203">Then, it uses a `when` clause to determine the `Quadrant` of the point:</span></span>

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

<span data-ttu-id="4f809-204">Vzorek zahození v předchozím přepínači odpovídá, když buď `x` nebo `y` je 0, ale ne obojí.</span><span class="sxs-lookup"><span data-stu-id="4f809-204">The discard pattern in the preceding switch matches when either `x` or `y` is 0, but not both.</span></span> <span data-ttu-id="4f809-205">Výraz přepínače musí buď vytvořit hodnotu nebo vyvolat výjimku.</span><span class="sxs-lookup"><span data-stu-id="4f809-205">A switch expression must either produce a value or throw an exception.</span></span> <span data-ttu-id="4f809-206">Pokud žádný z případů shodují, výraz přepínač vyvolá výjimku.</span><span class="sxs-lookup"><span data-stu-id="4f809-206">If none of the cases match, the switch expression throws an exception.</span></span> <span data-ttu-id="4f809-207">Kompilátor vygeneruje upozornění pro vás, pokud nechcete pokrýt všechny možné případy ve výrazu přepínač.</span><span class="sxs-lookup"><span data-stu-id="4f809-207">The compiler generates a warning for you if you don't cover all possible cases in your switch expression.</span></span>

<span data-ttu-id="4f809-208">Můžete prozkoumat techniky porovnávání vzorů v tomto [pokročilém kurzu o porovnávání vzorů](../tutorials/pattern-matching.md).</span><span class="sxs-lookup"><span data-stu-id="4f809-208">You can explore pattern matching techniques in this [advanced tutorial on pattern matching](../tutorials/pattern-matching.md).</span></span>

## <a name="using-declarations"></a><span data-ttu-id="4f809-209">Použití deklarací</span><span class="sxs-lookup"><span data-stu-id="4f809-209">Using declarations</span></span>

<span data-ttu-id="4f809-210">Deklarace **using** je deklarace proměnné, které předchází `using` klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="4f809-210">A **using declaration** is a variable declaration preceded by the `using` keyword.</span></span> <span data-ttu-id="4f809-211">Říká kompilátoru, že proměnná deklarovaná by měla být uvolněna na konci ohraničujícího oboru.</span><span class="sxs-lookup"><span data-stu-id="4f809-211">It tells the compiler that the variable being declared should be disposed at the end of the enclosing scope.</span></span> <span data-ttu-id="4f809-212">Zvažte například následující kód, který zapisuje textový soubor:</span><span class="sxs-lookup"><span data-stu-id="4f809-212">For example, consider the following code that writes a text file:</span></span>

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

<span data-ttu-id="4f809-213">V předchozím příkladu je soubor uvolněn při dosažení uzavírací složená závorka pro metodu.</span><span class="sxs-lookup"><span data-stu-id="4f809-213">In the preceding example, the file is disposed when the closing brace for the method is reached.</span></span> <span data-ttu-id="4f809-214">To je konec oboru, ve `file` kterém je deklarována.</span><span class="sxs-lookup"><span data-stu-id="4f809-214">That's the end of the scope in which `file` is declared.</span></span> <span data-ttu-id="4f809-215">Předchozí kód je ekvivalentní následující kód, který používá klasický [using příkaz](../language-reference/keywords/using-statement.md):</span><span class="sxs-lookup"><span data-stu-id="4f809-215">The preceding code is equivalent to the following code that uses the classic [using statement](../language-reference/keywords/using-statement.md):</span></span>

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

<span data-ttu-id="4f809-216">V předchozím příkladu je soubor uvolněn při dosažení uzavírací složená závorka přidružená k příkazu. `using`</span><span class="sxs-lookup"><span data-stu-id="4f809-216">In the preceding example, the file is disposed when the closing brace associated with the `using` statement is reached.</span></span>

<span data-ttu-id="4f809-217">V obou případech kompilátor generuje `Dispose()`volání .</span><span class="sxs-lookup"><span data-stu-id="4f809-217">In both cases, the compiler generates the call to `Dispose()`.</span></span> <span data-ttu-id="4f809-218">Kompilátor generuje chybu, pokud výraz `using` v příkazu není na jedno použití.</span><span class="sxs-lookup"><span data-stu-id="4f809-218">The compiler generates an error if the expression in the `using` statement isn't disposable.</span></span>

## <a name="static-local-functions"></a><span data-ttu-id="4f809-219">Statické místní funkce</span><span class="sxs-lookup"><span data-stu-id="4f809-219">Static local functions</span></span>

<span data-ttu-id="4f809-220">Nyní můžete přidat `static` modifikátor do místních funkcí, abyste zajistili, že místní funkce nezachytí (neodkazuje) žádné proměnné z ohraničujícího oboru.</span><span class="sxs-lookup"><span data-stu-id="4f809-220">You can now add the `static` modifier to local functions to ensure that local function doesn't capture (reference) any variables from the enclosing scope.</span></span> <span data-ttu-id="4f809-221">Tím se `CS8421`vygeneruje , "Statické místní funkce \<nemůže obsahovat odkaz na proměnné>."</span><span class="sxs-lookup"><span data-stu-id="4f809-221">Doing so generates `CS8421`, "A static local function can't contain a reference to \<variable>."</span></span>

<span data-ttu-id="4f809-222">Zvažte následující kód.</span><span class="sxs-lookup"><span data-stu-id="4f809-222">Consider the following code.</span></span> <span data-ttu-id="4f809-223">Místní funkce `LocalFunction` přistupuje k proměnné `y`, deklarované v ohraničující mašká (metoda). `M`</span><span class="sxs-lookup"><span data-stu-id="4f809-223">The local function `LocalFunction` accesses the variable `y`, declared in the enclosing scope (the method `M`).</span></span> <span data-ttu-id="4f809-224">`LocalFunction` Proto nelze deklarovat `static` pomocí modifikátoru:</span><span class="sxs-lookup"><span data-stu-id="4f809-224">Therefore, `LocalFunction` can't be declared with the `static` modifier:</span></span>

```csharp
int M()
{
    int y;
    LocalFunction();
    return y;

    void LocalFunction() => y = 0;
}
```

<span data-ttu-id="4f809-225">Následující kód obsahuje statickou místní funkci.</span><span class="sxs-lookup"><span data-stu-id="4f809-225">The following code contains a static local function.</span></span> <span data-ttu-id="4f809-226">Může být statický, protože nemá přístup k žádné proměnné v ohraničujícím oboru:</span><span class="sxs-lookup"><span data-stu-id="4f809-226">It can be static because it doesn't access any variables in the enclosing scope:</span></span>

```csharp
int M()
{
    int y = 5;
    int x = 7;
    return Add(x, y);

    static int Add(int left, int right) => left + right;
}
```

## <a name="disposable-ref-structs"></a><span data-ttu-id="4f809-227">Jednorázové ref struktury</span><span class="sxs-lookup"><span data-stu-id="4f809-227">Disposable ref structs</span></span>

<span data-ttu-id="4f809-228">`struct` Deklarované `ref` s modifikátorem nemusí implementovat <xref:System.IDisposable>žádná rozhraní, a proto nelze implementovat .</span><span class="sxs-lookup"><span data-stu-id="4f809-228">A `struct` declared with the `ref` modifier may not implement any interfaces and so can't implement <xref:System.IDisposable>.</span></span> <span data-ttu-id="4f809-229">Proto povolit `ref struct` likvidaci, musí mít přístupnou `void Dispose()` metodu.</span><span class="sxs-lookup"><span data-stu-id="4f809-229">Therefore, to enable a `ref struct` to be disposed, it must have an accessible `void Dispose()` method.</span></span> <span data-ttu-id="4f809-230">Tato funkce platí `readonly ref struct` také pro deklarace.</span><span class="sxs-lookup"><span data-stu-id="4f809-230">This feature also applies to `readonly ref struct` declarations.</span></span>

## <a name="nullable-reference-types"></a><span data-ttu-id="4f809-231">Odkazové typy s možnou hodnotou null</span><span class="sxs-lookup"><span data-stu-id="4f809-231">Nullable reference types</span></span>

<span data-ttu-id="4f809-232">Uvnitř kontextu poznámky s možnou hodnotou null je jakákoli proměnná typu odkazu považována za **nenulný typ odkazu**.</span><span class="sxs-lookup"><span data-stu-id="4f809-232">Inside a nullable annotation context, any variable of a reference type is considered to be a **nonnullable reference type**.</span></span> <span data-ttu-id="4f809-233">Pokud chcete označit, že proměnná může být null, je `?` nutné připojit název typu s deklarovat proměnnou jako **typ odkazu s možnou hodnotou null**.</span><span class="sxs-lookup"><span data-stu-id="4f809-233">If you want to indicate that a variable may be null, you must append the type name with the `?` to declare the variable as a **nullable reference type**.</span></span>

<span data-ttu-id="4f809-234">Pro neplatné typy odkazů kompilátor používá analýzu toku k zajištění, že místní proměnné jsou inicializovány na hodnotu bez nuly při deklarování.</span><span class="sxs-lookup"><span data-stu-id="4f809-234">For nonnullable reference types, the compiler uses flow analysis to ensure that local variables are initialized to a non-null value when declared.</span></span> <span data-ttu-id="4f809-235">Pole musí být během výstavby inicializována.</span><span class="sxs-lookup"><span data-stu-id="4f809-235">Fields must be initialized during construction.</span></span> <span data-ttu-id="4f809-236">Kompilátor generuje upozornění, pokud proměnná není nastavena voláním některého z dostupných konstruktorů nebo inicializátorem.</span><span class="sxs-lookup"><span data-stu-id="4f809-236">The compiler generates a warning if the variable isn't set by a call to any of the available constructors or by an initializer.</span></span> <span data-ttu-id="4f809-237">Kromě toho nelze zrušitelné typy odkazů nelze přiřadit hodnotu, která může být null.</span><span class="sxs-lookup"><span data-stu-id="4f809-237">Furthermore, nonnullable reference types can't be assigned a value that could be null.</span></span>

<span data-ttu-id="4f809-238">Typy odkazů s možnou hodnotou Null nejsou kontrolovány, aby bylo zajištěno, že nejsou přiřazeny nebo inicializovány na hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="4f809-238">Nullable reference types aren't checked to ensure they aren't assigned or initialized to null.</span></span> <span data-ttu-id="4f809-239">Kompilátor však používá analýzu toku k zajištění, že všechny proměnné typu odkazu s možnou hodnotou null je zkontrolována proti hodnotě null před tím, než je přístupná nebo přiřazena k neplatnému typu odkazu.</span><span class="sxs-lookup"><span data-stu-id="4f809-239">However, the compiler uses flow analysis to ensure that any variable of a nullable reference type is checked against null before it's accessed or assigned to a nonnullable reference type.</span></span>

<span data-ttu-id="4f809-240">Další informace o této funkci naleznete v přehledu [typů odkazů s možnou hodnotou null](../nullable-references.md).</span><span class="sxs-lookup"><span data-stu-id="4f809-240">You can learn more about the feature in the overview of [nullable reference types](../nullable-references.md).</span></span> <span data-ttu-id="4f809-241">Vyzkoušejte si to sami v nové aplikaci v tomto [kurzu s nulovatelnými typy odkazů](../tutorials/nullable-reference-types.md).</span><span class="sxs-lookup"><span data-stu-id="4f809-241">Try it yourself in a new application in this [nullable reference types tutorial](../tutorials/nullable-reference-types.md).</span></span> <span data-ttu-id="4f809-242">Informace o krocích migrace existujícího základu kódu pro použití typů odkazů s možnou hodnotou null v [kurzu migrace aplikace k použití typů odkazů s možnou hodnotou null](../tutorials/upgrade-to-nullable-references.md).</span><span class="sxs-lookup"><span data-stu-id="4f809-242">Learn about the steps to migrate an existing codebase to make use of nullable reference types in the [migrating an application to use nullable reference types tutorial](../tutorials/upgrade-to-nullable-references.md).</span></span>

## <a name="asynchronous-streams"></a><span data-ttu-id="4f809-243">Asynchronní datové proudy</span><span class="sxs-lookup"><span data-stu-id="4f809-243">Asynchronous streams</span></span>

<span data-ttu-id="4f809-244">Počínaje C# 8.0, můžete vytvořit a využívat datové proudy asynchronně.</span><span class="sxs-lookup"><span data-stu-id="4f809-244">Starting with C# 8.0, you can create and consume streams asynchronously.</span></span> <span data-ttu-id="4f809-245">Metoda, která vrací asynchronní datový proud, má tři vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="4f809-245">A method that returns an asynchronous stream has three properties:</span></span>

1. <span data-ttu-id="4f809-246">Je to deklarováno modifikátorem. `async`</span><span class="sxs-lookup"><span data-stu-id="4f809-246">It's declared with the `async` modifier.</span></span>
1. <span data-ttu-id="4f809-247">Vrátí . <xref:System.Collections.Generic.IAsyncEnumerable%601></span><span class="sxs-lookup"><span data-stu-id="4f809-247">It returns an <xref:System.Collections.Generic.IAsyncEnumerable%601>.</span></span>
1. <span data-ttu-id="4f809-248">Metoda obsahuje `yield return` příkazy vrátit po sobě jdoucích prvků v asynchronní datový proud.</span><span class="sxs-lookup"><span data-stu-id="4f809-248">The method contains `yield return` statements to return successive elements in the asynchronous stream.</span></span>

<span data-ttu-id="4f809-249">Náročné asynchronní datový proud vyžaduje, `await` abyste přidat `foreach` klíčové slovo před klíčové slovo při výčet prvků datového proudu.</span><span class="sxs-lookup"><span data-stu-id="4f809-249">Consuming an asynchronous stream requires you to add the `await` keyword before the `foreach` keyword when you enumerate the elements of the stream.</span></span> <span data-ttu-id="4f809-250">Přidání `await` klíčového slova vyžaduje metodu, která vyjmenovává asynchronní datový proud, který má být deklarován pomocí `async` modifikátoru, a vrátí typ povolený pro metodu. `async`</span><span class="sxs-lookup"><span data-stu-id="4f809-250">Adding the `await` keyword requires the method that enumerates the asynchronous stream to be declared with the `async` modifier and to return a type allowed for an `async` method.</span></span> <span data-ttu-id="4f809-251">Obvykle to znamená vrácení <xref:System.Threading.Tasks.Task> <xref:System.Threading.Tasks.Task%601>nebo .</span><span class="sxs-lookup"><span data-stu-id="4f809-251">Typically that means returning a <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="4f809-252">To může být <xref:System.Threading.Tasks.ValueTask> <xref:System.Threading.Tasks.ValueTask%601>také nebo .</span><span class="sxs-lookup"><span data-stu-id="4f809-252">It can also be a <xref:System.Threading.Tasks.ValueTask> or <xref:System.Threading.Tasks.ValueTask%601>.</span></span> <span data-ttu-id="4f809-253">Metoda může spotřebovávat a vytvářet asynchronní datový <xref:System.Collections.Generic.IAsyncEnumerable%601>proud, což znamená, že vrátí .</span><span class="sxs-lookup"><span data-stu-id="4f809-253">A method can both consume and produce an asynchronous stream, which means it would return an <xref:System.Collections.Generic.IAsyncEnumerable%601>.</span></span> <span data-ttu-id="4f809-254">Následující kód generuje sekvenci od 0 do 19, čekání 100 ms mezi generování každé číslo:</span><span class="sxs-lookup"><span data-stu-id="4f809-254">The following code generates a sequence from 0 to 19, waiting 100 ms between generating each number:</span></span>

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

<span data-ttu-id="4f809-255">Byste výčet sekvence pomocí příkazu: `await foreach`</span><span class="sxs-lookup"><span data-stu-id="4f809-255">You would enumerate the sequence using the `await foreach` statement:</span></span>

```csharp
await foreach (var number in GenerateSequence())
{
    Console.WriteLine(number);
}
```

<span data-ttu-id="4f809-256">Můžete zkusit asynchronní proudy sami v našem kurzu o [vytváření a využívání asynchronních proudů](../tutorials/generate-consume-asynchronous-stream.md).</span><span class="sxs-lookup"><span data-stu-id="4f809-256">You can try asynchronous streams yourself in our tutorial on [creating and consuming async streams](../tutorials/generate-consume-asynchronous-stream.md).</span></span> <span data-ttu-id="4f809-257">Ve výchozím nastavení jsou prvky datového proudu zpracovány v zachyceném kontextu.</span><span class="sxs-lookup"><span data-stu-id="4f809-257">By default, stream elements are processed in the captured context.</span></span> <span data-ttu-id="4f809-258">Pokud chcete zakázat zachycení kontextu, použijte <xref:System.Threading.Tasks.TaskAsyncEnumerableExtensions.ConfigureAwait%2A?displayProperty=nameWithType> metodu rozšíření.</span><span class="sxs-lookup"><span data-stu-id="4f809-258">If you want to disable capturing of the context, use the <xref:System.Threading.Tasks.TaskAsyncEnumerableExtensions.ConfigureAwait%2A?displayProperty=nameWithType> extension method.</span></span> <span data-ttu-id="4f809-259">Další informace o kontextech synchronizace a zachycení aktuálního kontextu naleznete v článku o [využití asynchronního vzoru založeného na úlohách](../../standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="4f809-259">For more information about synchronization contexts and capturing the current context, see the article on [consuming the Task-based asynchronous pattern](../../standard/asynchronous-programming-patterns/consuming-the-task-based-asynchronous-pattern.md).</span></span>

## <a name="indices-and-ranges"></a><span data-ttu-id="4f809-260">Indexy a rozsahy</span><span class="sxs-lookup"><span data-stu-id="4f809-260">Indices and ranges</span></span>

<span data-ttu-id="4f809-261">Indexy a rozsahy poskytují stručnou syntaxi pro přístup k jednotlivým prvkům nebo rozsahům v sekvenci.</span><span class="sxs-lookup"><span data-stu-id="4f809-261">Indices and ranges provide a succinct syntax for accessing single elements or ranges in a sequence.</span></span>

<span data-ttu-id="4f809-262">Tato jazyková podpora závisí na dvou nových typech a dvou nových operátorech:</span><span class="sxs-lookup"><span data-stu-id="4f809-262">This language support relies on two new types, and two new operators:</span></span>

- <span data-ttu-id="4f809-263"><xref:System.Index?displayProperty=nameWithType>představuje index do sekvence.</span><span class="sxs-lookup"><span data-stu-id="4f809-263"><xref:System.Index?displayProperty=nameWithType> represents an index into a sequence.</span></span>
- <span data-ttu-id="4f809-264">Index z koncového operátoru `^`, který určuje, že index je relativní ke konci sekvence.</span><span class="sxs-lookup"><span data-stu-id="4f809-264">The index from end operator `^`, which specifies that an index is relative to the end of the sequence.</span></span>
- <span data-ttu-id="4f809-265"><xref:System.Range?displayProperty=nameWithType>představuje dílčí rozsah sekvence.</span><span class="sxs-lookup"><span data-stu-id="4f809-265"><xref:System.Range?displayProperty=nameWithType> represents a sub range of a sequence.</span></span>
- <span data-ttu-id="4f809-266">Operátor `..`rozsahu , který určuje začátek a konec rozsahu jako jeho operandy.</span><span class="sxs-lookup"><span data-stu-id="4f809-266">The range operator `..`, which specifies the start and end of a range as its operands.</span></span>

<span data-ttu-id="4f809-267">Začněme s pravidly pro indexy.</span><span class="sxs-lookup"><span data-stu-id="4f809-267">Let's start with the rules for indexes.</span></span> <span data-ttu-id="4f809-268">Zvažte `sequence`pole .</span><span class="sxs-lookup"><span data-stu-id="4f809-268">Consider an array `sequence`.</span></span> <span data-ttu-id="4f809-269">Index `0` je stejný `sequence[0]`jako .</span><span class="sxs-lookup"><span data-stu-id="4f809-269">The `0` index is the same as `sequence[0]`.</span></span> <span data-ttu-id="4f809-270">Index `^0` je stejný `sequence[sequence.Length]`jako .</span><span class="sxs-lookup"><span data-stu-id="4f809-270">The `^0` index is the same as `sequence[sequence.Length]`.</span></span> <span data-ttu-id="4f809-271">Všimněte `sequence[^0]` si, že se `sequence[sequence.Length]` vyvolat výjimku, stejně jako dělá.</span><span class="sxs-lookup"><span data-stu-id="4f809-271">Note that `sequence[^0]` does throw an exception, just as `sequence[sequence.Length]` does.</span></span> <span data-ttu-id="4f809-272">Pro libovolné `n`číslo `^n` je index `sequence.Length - n`stejný jako .</span><span class="sxs-lookup"><span data-stu-id="4f809-272">For any number `n`, the index `^n` is the same as `sequence.Length - n`.</span></span>

<span data-ttu-id="4f809-273">Rozsah určuje *začátek* *a* konec rozsahu.</span><span class="sxs-lookup"><span data-stu-id="4f809-273">A range specifies the *start* and *end* of a range.</span></span> <span data-ttu-id="4f809-274">Začátek rozsahu je včetně, ale konec rozsahu je exkluzivní, což znamená, že *začátek* je součástí rozsahu, ale *konec* není součástí rozsahu.</span><span class="sxs-lookup"><span data-stu-id="4f809-274">The start of the range is inclusive, but the end of the range is exclusive, meaning the *start* is included in the range but the *end* isn't included in the range.</span></span> <span data-ttu-id="4f809-275">Rozsah `[0..^0]` představuje celý rozsah, `[0..sequence.Length]` stejně jako představuje celý rozsah.</span><span class="sxs-lookup"><span data-stu-id="4f809-275">The range `[0..^0]` represents the entire range, just as `[0..sequence.Length]` represents the entire range.</span></span>

<span data-ttu-id="4f809-276">Podívejme se na několik příkladů.</span><span class="sxs-lookup"><span data-stu-id="4f809-276">Let's look at a few examples.</span></span> <span data-ttu-id="4f809-277">Zvažte následující pole s poznámkami s jeho indexem od začátku a od konce:</span><span class="sxs-lookup"><span data-stu-id="4f809-277">Consider the following array, annotated with its index from the start and from the end:</span></span>

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

<span data-ttu-id="4f809-278">Můžete načíst poslední slovo `^1` s indexem:</span><span class="sxs-lookup"><span data-stu-id="4f809-278">You can retrieve the last word with the `^1` index:</span></span>

```csharp
Console.WriteLine($"The last word is {words[^1]}");
// writes "dog"
```

<span data-ttu-id="4f809-279">Následující kód vytvoří podrozsah se slovy "quick", "brown" a "fox".</span><span class="sxs-lookup"><span data-stu-id="4f809-279">The following code creates a subrange with the words "quick", "brown", and "fox".</span></span> <span data-ttu-id="4f809-280">To `words[1]` zahrnuje `words[3]`prostřednictvím .</span><span class="sxs-lookup"><span data-stu-id="4f809-280">It includes `words[1]` through `words[3]`.</span></span> <span data-ttu-id="4f809-281">Prvek `words[4]` není v rozsahu.</span><span class="sxs-lookup"><span data-stu-id="4f809-281">The element `words[4]` isn't in the range.</span></span>

```csharp
var quickBrownFox = words[1..4];
```

<span data-ttu-id="4f809-282">Následující kód vytvoří podrozsah s "líný" a "pes".</span><span class="sxs-lookup"><span data-stu-id="4f809-282">The following code creates a subrange with "lazy" and "dog".</span></span> <span data-ttu-id="4f809-283">To `words[^2]` zahrnuje `words[^1]`a .</span><span class="sxs-lookup"><span data-stu-id="4f809-283">It includes `words[^2]` and `words[^1]`.</span></span> <span data-ttu-id="4f809-284">Koncový index `words[^0]` není zahrnut:</span><span class="sxs-lookup"><span data-stu-id="4f809-284">The end index `words[^0]` isn't included:</span></span>

```csharp
var lazyDog = words[^2..^0];
```

<span data-ttu-id="4f809-285">Následující příklady vytvářejí oblasti, které jsou otevřené pro začátek, konec nebo obojí:</span><span class="sxs-lookup"><span data-stu-id="4f809-285">The following examples create ranges that are open ended for the start, end, or both:</span></span>

```csharp
var allWords = words[..]; // contains "The" through "dog".
var firstPhrase = words[..4]; // contains "The" through "fox"
var lastPhrase = words[6..]; // contains "the", "lazy" and "dog"
```

<span data-ttu-id="4f809-286">Rozsahy můžete také deklarovat jako proměnné:</span><span class="sxs-lookup"><span data-stu-id="4f809-286">You can also declare ranges as variables:</span></span>

```csharp
Range phrase = 1..4;
```

<span data-ttu-id="4f809-287">Rozsah pak lze použít `[` uvnitř `]` znaky a:</span><span class="sxs-lookup"><span data-stu-id="4f809-287">The range can then be used inside the `[` and `]` characters:</span></span>

```csharp
var text = words[phrase];
```

<span data-ttu-id="4f809-288">Nejen pole podporují indexy a rozsahy.</span><span class="sxs-lookup"><span data-stu-id="4f809-288">Not only arrays support indices and ranges.</span></span> <span data-ttu-id="4f809-289">Můžete také použít indexy a rozsahy <xref:System.Span%601>s <xref:System.ReadOnlySpan%601> [řetězcem](../language-reference/builtin-types/reference-types.md#the-string-type), nebo .</span><span class="sxs-lookup"><span data-stu-id="4f809-289">You also can use indices and ranges with [string](../language-reference/builtin-types/reference-types.md#the-string-type), <xref:System.Span%601>, or <xref:System.ReadOnlySpan%601>.</span></span> <span data-ttu-id="4f809-290">Další informace naleznete [v tématu Typ podpory pro indexy a rozsahy](../tutorials/ranges-indexes.md#type-support-for-indices-and-ranges).</span><span class="sxs-lookup"><span data-stu-id="4f809-290">For more information, see [Type support for indices and ranges](../tutorials/ranges-indexes.md#type-support-for-indices-and-ranges).</span></span>

<span data-ttu-id="4f809-291">Další informace o indexech a rozsahech můžete prozkoumat v kurzu o [indexech a rozsahech](../tutorials/ranges-indexes.md).</span><span class="sxs-lookup"><span data-stu-id="4f809-291">You can explore more about indices and ranges in the tutorial on [indices and ranges](../tutorials/ranges-indexes.md).</span></span>

## <a name="null-coalescing-assignment"></a><span data-ttu-id="4f809-292">Přiřazení null-coalescing</span><span class="sxs-lookup"><span data-stu-id="4f809-292">Null-coalescing assignment</span></span>

<span data-ttu-id="4f809-293">C# 8.0 zavádí operátor `??=`přiřazení null-coalescing .</span><span class="sxs-lookup"><span data-stu-id="4f809-293">C# 8.0 introduces the null-coalescing assignment operator `??=`.</span></span> <span data-ttu-id="4f809-294">`??=` Operátor můžete použít k přiřazení hodnoty jeho pravostranného operandu jeho levostranné operandu pouze `null`v případě, že se levá operand vyhodnotí na .</span><span class="sxs-lookup"><span data-stu-id="4f809-294">You can use the `??=` operator to assign the value of its right-hand operand to its left-hand operand only if the left-hand operand evaluates to `null`.</span></span>

```csharp
List<int> numbers = null;
int? i = null;

numbers ??= new List<int>();
numbers.Add(i ??= 17);
numbers.Add(i ??= 20);

Console.WriteLine(string.Join(" ", numbers));  // output: 17 17
Console.WriteLine(i);  // output: 17
```

<span data-ttu-id="4f809-295">Pro více informací, viz [?? a ?? = článek operátorů.](../language-reference/operators/null-coalescing-operator.md)</span><span class="sxs-lookup"><span data-stu-id="4f809-295">For more information, see the [?? and ??= operators](../language-reference/operators/null-coalescing-operator.md) article.</span></span>

## <a name="unmanaged-constructed-types"></a><span data-ttu-id="4f809-296">Nespravované konstruované typy</span><span class="sxs-lookup"><span data-stu-id="4f809-296">Unmanaged constructed types</span></span>

<span data-ttu-id="4f809-297">V C# 7.3 a starší, konstruované typu (typ, který obsahuje alespoň jeden argument typu) nemůže být [nespravovaný typ](../language-reference/builtin-types/unmanaged-types.md).</span><span class="sxs-lookup"><span data-stu-id="4f809-297">In C# 7.3 and earlier, a constructed type (a type that includes at least one type argument) can't be an [unmanaged type](../language-reference/builtin-types/unmanaged-types.md).</span></span> <span data-ttu-id="4f809-298">Počínaje C# 8.0, početný typ hodnoty je nespravovaný, pokud obsahuje pouze pole nespravovaných typů.</span><span class="sxs-lookup"><span data-stu-id="4f809-298">Starting with C# 8.0, a constructed value type is unmanaged if it contains fields of unmanaged types only.</span></span>

<span data-ttu-id="4f809-299">Například s ohledem na následující `Coords<T>` definici obecného typu:</span><span class="sxs-lookup"><span data-stu-id="4f809-299">For example, given the following definition of the generic `Coords<T>` type:</span></span>

```csharp
public struct Coords<T>
{
    public T X;
    public T Y;
}
```

<span data-ttu-id="4f809-300">`Coords<int>` typ je nespravovaný typ v C# 8.0 a novější.</span><span class="sxs-lookup"><span data-stu-id="4f809-300">the `Coords<int>` type is an unmanaged type in C# 8.0 and later.</span></span> <span data-ttu-id="4f809-301">Stejně jako u všech nespravovaných typů můžete vytvořit ukazatel na proměnnou tohoto typu nebo [přidělit blok paměti v zásobníku](../language-reference/operators/stackalloc.md) pro instance tohoto typu:</span><span class="sxs-lookup"><span data-stu-id="4f809-301">Like for any unmanaged type, you can create a pointer to a variable of this type or [allocate a block of memory on the stack](../language-reference/operators/stackalloc.md) for instances of this type:</span></span>

```csharp
Span<Coords<int>> coordinates = stackalloc[]
{
    new Coords<int> { X = 0, Y = 0 },
    new Coords<int> { X = 0, Y = 3 },
    new Coords<int> { X = 4, Y = 0 }
};
```

<span data-ttu-id="4f809-302">Další informace naleznete v tématu [Unmanaged types](../language-reference/builtin-types/unmanaged-types.md).</span><span class="sxs-lookup"><span data-stu-id="4f809-302">For more information, see [Unmanaged types](../language-reference/builtin-types/unmanaged-types.md).</span></span>

## <a name="stackalloc-in-nested-expressions"></a><span data-ttu-id="4f809-303">Stackalloc ve vnořených výrazech</span><span class="sxs-lookup"><span data-stu-id="4f809-303">Stackalloc in nested expressions</span></span>

<span data-ttu-id="4f809-304">Počínaje C# 8.0, pokud je výsledek výrazu [stackalloc](../language-reference/operators/stackalloc.md) typu <xref:System.Span%601?displayProperty=nameWithType> nebo, <xref:System.ReadOnlySpan%601?displayProperty=nameWithType> můžete použít `stackalloc` výraz v jiných výrazech:</span><span class="sxs-lookup"><span data-stu-id="4f809-304">Starting with C# 8.0, if the result of a [stackalloc](../language-reference/operators/stackalloc.md) expression is of the <xref:System.Span%601?displayProperty=nameWithType> or <xref:System.ReadOnlySpan%601?displayProperty=nameWithType> type, you can use the `stackalloc` expression in other expressions:</span></span>

```csharp
Span<int> numbers = stackalloc[] { 1, 2, 3, 4, 5, 6 };
var ind = numbers.IndexOfAny(stackalloc[] { 2, 4, 6 ,8 });
Console.WriteLine(ind);  // output: 1
```

## <a name="enhancement-of-interpolated-verbatim-strings"></a><span data-ttu-id="4f809-305">Vylepšení interpolovaných doslovných řetězců</span><span class="sxs-lookup"><span data-stu-id="4f809-305">Enhancement of interpolated verbatim strings</span></span>

<span data-ttu-id="4f809-306">Pořadí `$` a `@` tokeny v [interpolovaných](../language-reference/tokens/interpolated.md) doslovných řetězců může `$@"..."` být `@$"..."` libovolné: oba a jsou platné interpolované doslovné řetězce.</span><span class="sxs-lookup"><span data-stu-id="4f809-306">Order of the `$` and `@` tokens in [interpolated](../language-reference/tokens/interpolated.md) verbatim strings can be any: both `$@"..."` and `@$"..."` are valid interpolated verbatim strings.</span></span> <span data-ttu-id="4f809-307">V dřívějších verzích `$` jazyka C# `@` token musí zobrazit před token.</span><span class="sxs-lookup"><span data-stu-id="4f809-307">In earlier C# versions, the `$` token must appear before the `@` token.</span></span>
