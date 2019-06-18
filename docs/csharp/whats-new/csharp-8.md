---
title: Co je nového v C# 8.0 – C# Průvodce
description: Získejte přehled o nových funkcí dostupných v C# 8.0. V tomto článku je aktuální verze Preview 5.
ms.date: 02/12/2019
ms.openlocfilehash: 99056c9cd330c0c3ae6c63239989a2e9e9dc496c
ms.sourcegitcommit: 5e05f983e63d5bbd8c0b246d02c6e4f23d2fc1db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/17/2019
ms.locfileid: "67151982"
---
# <a name="whats-new-in-c-80"></a><span data-ttu-id="6c3b2-104">Co je nového v C# 8.0</span><span class="sxs-lookup"><span data-stu-id="6c3b2-104">What's new in C# 8.0</span></span>

<span data-ttu-id="6c3b2-105">Existuje mnoho vylepšení C# jazyk, který můžete vyzkoušet již.</span><span class="sxs-lookup"><span data-stu-id="6c3b2-105">There are many enhancements to the C# language that you can try out already.</span></span> 

- [<span data-ttu-id="6c3b2-106">Členy jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="6c3b2-106">Readonly members</span></span>](#readonly-members)
- [<span data-ttu-id="6c3b2-107">Výchozí členy rozhraní</span><span class="sxs-lookup"><span data-stu-id="6c3b2-107">Default interface members</span></span>](#default-interface-members)
- <span data-ttu-id="6c3b2-108">[Porovnávání vzorů vylepšení](#more-patterns-in-more-places):</span><span class="sxs-lookup"><span data-stu-id="6c3b2-108">[Pattern matching enhancements](#more-patterns-in-more-places):</span></span>
  * [<span data-ttu-id="6c3b2-109">Přepnout výrazy</span><span class="sxs-lookup"><span data-stu-id="6c3b2-109">Switch expressions</span></span>](#switch-expressions)
  * [<span data-ttu-id="6c3b2-110">Vlastnost vzory</span><span class="sxs-lookup"><span data-stu-id="6c3b2-110">Property patterns</span></span>](#property-patterns)
  * [<span data-ttu-id="6c3b2-111">Vzory řazené kolekce členů</span><span class="sxs-lookup"><span data-stu-id="6c3b2-111">Tuple patterns</span></span>](#tuple-patterns)
  * [<span data-ttu-id="6c3b2-112">Poziční vzory</span><span class="sxs-lookup"><span data-stu-id="6c3b2-112">Positional patterns</span></span>](#positional-patterns)
- [<span data-ttu-id="6c3b2-113">Pomocí deklarace</span><span class="sxs-lookup"><span data-stu-id="6c3b2-113">Using declarations</span></span>](#using-declarations)
- [<span data-ttu-id="6c3b2-114">Statická lokální funkce</span><span class="sxs-lookup"><span data-stu-id="6c3b2-114">Static local functions</span></span>](#static-local-functions)
- [<span data-ttu-id="6c3b2-115">Struktury ref uvolnitelné</span><span class="sxs-lookup"><span data-stu-id="6c3b2-115">Disposable ref structs</span></span>](#disposable-ref-structs)
- [<span data-ttu-id="6c3b2-116">Odkazové typy s možnou hodnotou null</span><span class="sxs-lookup"><span data-stu-id="6c3b2-116">Nullable reference types</span></span>](#nullable-reference-types)
- [<span data-ttu-id="6c3b2-117">Asynchronní datové proudy</span><span class="sxs-lookup"><span data-stu-id="6c3b2-117">Asynchronous streams</span></span>](#asynchronous-streams)
- [<span data-ttu-id="6c3b2-118">Indexy a rozsahy</span><span class="sxs-lookup"><span data-stu-id="6c3b2-118">Indices and ranges</span></span>](#indices-and-ranges)

> [!NOTE]
> <span data-ttu-id="6c3b2-119">Tento článek byl naposledy aktualizován pro C# 8.0 ve verzi preview 5.</span><span class="sxs-lookup"><span data-stu-id="6c3b2-119">This article was last updated for C# 8.0 preview 5.</span></span>

<span data-ttu-id="6c3b2-120">Zbývající část tohoto článku stručně popisuje tyto funkce.</span><span class="sxs-lookup"><span data-stu-id="6c3b2-120">The remainder of this article briefly describes these features.</span></span> <span data-ttu-id="6c3b2-121">Pokud podrobné články jsou k dispozici, jsou k dispozici odkazy na tyto kurzy a přehledy.</span><span class="sxs-lookup"><span data-stu-id="6c3b2-121">Where in-depth articles are available, links to those tutorials and overviews are provided.</span></span>

## <a name="readonly-members"></a><span data-ttu-id="6c3b2-122">Členy jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="6c3b2-122">Readonly members</span></span>

<span data-ttu-id="6c3b2-123">Můžete použít `readonly` modifikátor k libovolnému členovi struktury.</span><span class="sxs-lookup"><span data-stu-id="6c3b2-123">You can apply the `readonly` modifier to any member of a struct.</span></span> <span data-ttu-id="6c3b2-124">Znamená to, že člen neprovede žádné změny stavu.</span><span class="sxs-lookup"><span data-stu-id="6c3b2-124">It indicates that the member does not modify state.</span></span> <span data-ttu-id="6c3b2-125">Je podrobnější než použití `readonly` modifikátor `struct` deklarace.</span><span class="sxs-lookup"><span data-stu-id="6c3b2-125">It's more granular than applying the `readonly` modifier to a `struct` declaration.</span></span>  <span data-ttu-id="6c3b2-126">Vezměte v úvahu následující proměnlivé struktury:</span><span class="sxs-lookup"><span data-stu-id="6c3b2-126">Consider the following mutable struct:</span></span>

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

<span data-ttu-id="6c3b2-127">Většina struktury, jako jsou `ToString()` metoda neprovede žádné změny stavu.</span><span class="sxs-lookup"><span data-stu-id="6c3b2-127">Like most structs, the `ToString()` method does not modify state.</span></span> <span data-ttu-id="6c3b2-128">Který může znamenat tak, že přidáte `readonly` modifikátoru deklarace `ToString()`:</span><span class="sxs-lookup"><span data-stu-id="6c3b2-128">You could indicate that by adding the `readonly` modifier to the declaration of `ToString()`:</span></span>

```csharp
public readonly override string ToString() =>
    $"({X}, {Y}) is {Distance} from the origin";
```

<span data-ttu-id="6c3b2-129">Předchozí změny generuje upozornění kompilátoru, protože `ToString` přistupuje `Distance` vlastnost, která není označena `readonly`:</span><span class="sxs-lookup"><span data-stu-id="6c3b2-129">The preceding change generates a compiler warning, because `ToString` accesses the `Distance` property, which is not marked `readonly`:</span></span>

```console
warning CS8656: Call to non-readonly member 'Point.Distance.get' from a 'readonly' member results in an implicit copy of 'this'
```

<span data-ttu-id="6c3b2-130">Kompilátor vás upozorní, když je potřeba vytvořit obranná kopie.</span><span class="sxs-lookup"><span data-stu-id="6c3b2-130">The compiler warns you when it needs to create a defensive copy.</span></span>  <span data-ttu-id="6c3b2-131">`Distance` Vlastnost nedojde ke změně stavu, takže toto upozornění můžete vyřešit tak, že přidáte `readonly` modifikátoru deklarace:</span><span class="sxs-lookup"><span data-stu-id="6c3b2-131">The `Distance` property does not change state, so you can fix this warning by adding the `readonly` modifier to the declaration:</span></span>

```csharp
public readonly double Distance => Math.Sqrt(X * X + Y * Y);
```

<span data-ttu-id="6c3b2-132">Všimněte si, že `readonly` Modifikátor je nezbytné na vlastnost jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="6c3b2-132">Notice that the `readonly` modifier is necessary on a read only property.</span></span> <span data-ttu-id="6c3b2-133">Kompilátor nepředpokládá `get` přistupující objekty neprovádějte žádné změny stavu, je třeba deklarovat `readonly` explicitně.</span><span class="sxs-lookup"><span data-stu-id="6c3b2-133">The compiler doesn't assume `get` accessors do not modify state; you must declare `readonly` explicitly.</span></span> <span data-ttu-id="6c3b2-134">Kompilátor vynucuje pravidla, která `readonly` členy neprovádějte žádné změny stavu.</span><span class="sxs-lookup"><span data-stu-id="6c3b2-134">The compiler does enforce the rule that `readonly` members do not modify state.</span></span> <span data-ttu-id="6c3b2-135">Následující metoda nebude kompilovat, dokud neodeberete `readonly` modifikátor:</span><span class="sxs-lookup"><span data-stu-id="6c3b2-135">The following method will not compile unless you remove the `readonly` modifier:</span></span>

```csharp
public readonly void Translate(int xOffset, int yOffset)
{
    X += xOffset;
    Y += yOffset;
}
```

<span data-ttu-id="6c3b2-136">Tato funkce vám umožní zadat máte v úmyslu návrhu tak, aby kompilátor může vynutit a ujistěte se, optimalizace podle tohoto záměru.</span><span class="sxs-lookup"><span data-stu-id="6c3b2-136">This feature lets you specify your design intent so the compiler can enforce it, and make optimizations based on that intent.</span></span>

## <a name="default-interface-members"></a><span data-ttu-id="6c3b2-137">Výchozí členy rozhraní</span><span class="sxs-lookup"><span data-stu-id="6c3b2-137">Default interface members</span></span>

<span data-ttu-id="6c3b2-138">Teď můžete přidat členy do rozhraní a poskytnout implementaci pro ty členy.</span><span class="sxs-lookup"><span data-stu-id="6c3b2-138">You can now add members to interfaces and provide an implementation for those members.</span></span> <span data-ttu-id="6c3b2-139">Této funkci jazyka umožňuje autorům rozhraní API přidat metody do rozhraní v pozdějších verzích bez narušení zdroje nebo binární kompatibilitu s existující implementace rozhraní.</span><span class="sxs-lookup"><span data-stu-id="6c3b2-139">This language feature enables API authors to add methods to an interface in later versions without breaking source or binary compatibility with existing implementations of that interface.</span></span> <span data-ttu-id="6c3b2-140">Existujících implementací *dědit* výchozí implementaci.</span><span class="sxs-lookup"><span data-stu-id="6c3b2-140">Existing implementations *inherit* the default implementation.</span></span> <span data-ttu-id="6c3b2-141">Tato funkce také umožňuje C# pro spolupráci s rozhraní API, která cílí na Android nebo Swift, které podporují podobné funkce.</span><span class="sxs-lookup"><span data-stu-id="6c3b2-141">This feature also enables C# to interoperate with APIs that target Android or Swift, which support similar features.</span></span> <span data-ttu-id="6c3b2-142">Výchozí členy rozhraní také povolit scénáře podobné funkci jazyka "vlastnosti".</span><span class="sxs-lookup"><span data-stu-id="6c3b2-142">Default interface members also enable scenarios similar to a "traits" language feature.</span></span>

<span data-ttu-id="6c3b2-143">Výchozí členy rozhraní ovlivňuje mnoho scénářů a prvky jazyka.</span><span class="sxs-lookup"><span data-stu-id="6c3b2-143">Default interface members affects many scenarios and language elements.</span></span> <span data-ttu-id="6c3b2-144">Naše první kurz se zabývá [aktualizace pomocí výchozí implementace rozhraní](../tutorials/default-interface-members-versions.md).</span><span class="sxs-lookup"><span data-stu-id="6c3b2-144">Our first tutorial covers [updating an interface with default implementations](../tutorials/default-interface-members-versions.md).</span></span> <span data-ttu-id="6c3b2-145">Další kurzy a referenční aktualizace se chystají v čase pro obecné verze.</span><span class="sxs-lookup"><span data-stu-id="6c3b2-145">Other tutorials and reference updates are coming in time for general release.</span></span>

## <a name="more-patterns-in-more-places"></a><span data-ttu-id="6c3b2-146">Další vzory na více místech</span><span class="sxs-lookup"><span data-stu-id="6c3b2-146">More patterns in more places</span></span>

<span data-ttu-id="6c3b2-147">**Porovnávání vzorů** poskytuje nástroje k zajištění funkce závislé na tvar v souvisejících, ale různé druhy dat.</span><span class="sxs-lookup"><span data-stu-id="6c3b2-147">**Pattern matching** gives tools to provide shape-dependent functionality across related but different kinds of data.</span></span> <span data-ttu-id="6c3b2-148">C#7.0 vytvořit pomocí syntaxe pro typ vzory a konstantní vzory [ `is` ](../language-reference/keywords/is.md) výraz a [ `switch` ](../language-reference/keywords/switch.md) příkazu.</span><span class="sxs-lookup"><span data-stu-id="6c3b2-148">C# 7.0 introduced syntax for type patterns and constant patterns by using the [`is`](../language-reference/keywords/is.md) expression and the [`switch`](../language-reference/keywords/switch.md) statement.</span></span> <span data-ttu-id="6c3b2-149">Tyto funkce jsou reprezentovány první nezávazně postup směrem k podpoře programovací modely, kde data a funkce live od sebe.</span><span class="sxs-lookup"><span data-stu-id="6c3b2-149">These features represented the first tentative steps toward supporting programming paradigms where data and functionality live apart.</span></span> <span data-ttu-id="6c3b2-150">Jak se v oboru blíží další mikroslužby a další cloudové architektury, jsou potřeba další nástroje jazyka.</span><span class="sxs-lookup"><span data-stu-id="6c3b2-150">As the industry moves toward more microservices and other cloud-based architectures, other language tools are needed.</span></span>

<span data-ttu-id="6c3b2-151">C#8.0 rozšiřuje tento slovník tak další vzorek výrazy můžete použít na více místech ve vašem kódu.</span><span class="sxs-lookup"><span data-stu-id="6c3b2-151">C# 8.0 expands this vocabulary so you can use more pattern expressions in more places in your code.</span></span> <span data-ttu-id="6c3b2-152">Pokud vaše data a funkce jsou oddělené vezměte v úvahu tyto funkce.</span><span class="sxs-lookup"><span data-stu-id="6c3b2-152">Consider these features when your data and functionality are separate.</span></span> <span data-ttu-id="6c3b2-153">Vezměte v úvahu porovnávání vzorů při algoritmy závisí na skutečnost než objekt typu modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="6c3b2-153">Consider pattern matching when your algorithms depend on a fact other than the runtime type of an object.</span></span> <span data-ttu-id="6c3b2-154">Tyto postupy zadejte jiný způsob, jak vyjádřit návrhy.</span><span class="sxs-lookup"><span data-stu-id="6c3b2-154">These techniques provide another way to express designs.</span></span>

<span data-ttu-id="6c3b2-155">Kromě nové vzory v nových místech C# 8.0 přidá **rekurzivní vzory**.</span><span class="sxs-lookup"><span data-stu-id="6c3b2-155">In addition to new patterns in new places, C# 8.0 adds **recursive patterns**.</span></span> <span data-ttu-id="6c3b2-156">Výsledek výrazu jakékoli vzor je výraz.</span><span class="sxs-lookup"><span data-stu-id="6c3b2-156">The result of any pattern expression is an expression.</span></span> <span data-ttu-id="6c3b2-157">Rekurzivní vzor je jednoduše vzor výraz použitý pro výstup jiný výraz vzoru.</span><span class="sxs-lookup"><span data-stu-id="6c3b2-157">A recursive pattern is simply a pattern expression applied to the output of another pattern expression.</span></span>

### <a name="switch-expressions"></a><span data-ttu-id="6c3b2-158">Přepnout výrazy</span><span class="sxs-lookup"><span data-stu-id="6c3b2-158">switch expressions</span></span>

<span data-ttu-id="6c3b2-159">Často [ `switch` ](../language-reference/keywords/switch.md) příkaz vytvoří hodnotu ve všech jeho `case` bloky.</span><span class="sxs-lookup"><span data-stu-id="6c3b2-159">Often, a [`switch`](../language-reference/keywords/switch.md) statement produces a value in each of its `case` blocks.</span></span> <span data-ttu-id="6c3b2-160">**Přepnout výrazy** vám umožní používat stručnější syntaxi výrazu.</span><span class="sxs-lookup"><span data-stu-id="6c3b2-160">**Switch expressions** enable you to use more concise expression syntax.</span></span> <span data-ttu-id="6c3b2-161">Existují méně opakované `case` a `break` klíčová slova a méně složených závorek.</span><span class="sxs-lookup"><span data-stu-id="6c3b2-161">There are fewer repetitive `case` and `break` keywords, and fewer curly braces.</span></span>  <span data-ttu-id="6c3b2-162">Jako příklad vezměte v úvahu následující výčtového typu, který obsahuje seznam barvy rainbow:</span><span class="sxs-lookup"><span data-stu-id="6c3b2-162">As an example, consider the following enum that lists the colors of the rainbow:</span></span>

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

<span data-ttu-id="6c3b2-163">Pokud vaše aplikace definované `RGBColor` typ, který je vytvořen z `R`, `G` a `B` součásti, můžete převést `Rainbow` hodnotu na jeho hodnoty RGB pomocí následující metody, který obsahuje výraz přepínače:</span><span class="sxs-lookup"><span data-stu-id="6c3b2-163">If your application defined an `RGBColor` type that is constructed from the `R`, `G` and `B` components, you could convert a `Rainbow` value to its RGB values using the following method containing a switch expression:</span></span>

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

<span data-ttu-id="6c3b2-164">Existuje několik vylepšení syntaxe tady:</span><span class="sxs-lookup"><span data-stu-id="6c3b2-164">There are several syntax improvements here:</span></span>

- <span data-ttu-id="6c3b2-165">Proměnná byla zaslána před `switch` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="6c3b2-165">The variable comes before the `switch` keyword.</span></span> <span data-ttu-id="6c3b2-166">Jiné pořadí vizuálně usnadňuje rozlišit výraz přepínače z příkazu switch.</span><span class="sxs-lookup"><span data-stu-id="6c3b2-166">The different order makes it visually easy to distinguish the switch expression from the switch statement.</span></span>
- <span data-ttu-id="6c3b2-167">`case` a `:` prvky jsou nahrazeny `=>`.</span><span class="sxs-lookup"><span data-stu-id="6c3b2-167">The `case` and `:` elements are replaced with `=>`.</span></span> <span data-ttu-id="6c3b2-168">Je stručnějším a intuitivní.</span><span class="sxs-lookup"><span data-stu-id="6c3b2-168">It's more concise and intuitive.</span></span>
- <span data-ttu-id="6c3b2-169">`default` Případ je nahrazen `_` zahodit.</span><span class="sxs-lookup"><span data-stu-id="6c3b2-169">The `default` case is replaced with a `_` discard.</span></span>
- <span data-ttu-id="6c3b2-170">Subjekty jsou výrazy, nikoli příkazy.</span><span class="sxs-lookup"><span data-stu-id="6c3b2-170">The bodies are expressions, not statements.</span></span>

<span data-ttu-id="6c3b2-171">Oproti, který odpovídá kódu pomocí klasického `switch` – příkaz:</span><span class="sxs-lookup"><span data-stu-id="6c3b2-171">Contrast that with the equivalent code using the classic `switch` statement:</span></span>

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

### <a name="property-patterns"></a><span data-ttu-id="6c3b2-172">Vlastnost vzory</span><span class="sxs-lookup"><span data-stu-id="6c3b2-172">Property patterns</span></span>

<span data-ttu-id="6c3b2-173">**Vlastnost vzor** umožňuje tak, aby odpovídala na vlastnosti objektu prověřit.</span><span class="sxs-lookup"><span data-stu-id="6c3b2-173">The **property pattern** enables you to match on properties of the object examined.</span></span> <span data-ttu-id="6c3b2-174">Vezměte v úvahu elektronického obchodování webu, který musí vypočítat na základě adresy odběratele DPH.</span><span class="sxs-lookup"><span data-stu-id="6c3b2-174">Consider an eCommerce site that must compute sales tax based on the buyer's address.</span></span> <span data-ttu-id="6c3b2-175">Výpočet není základní působnosti `Address` třídy.</span><span class="sxs-lookup"><span data-stu-id="6c3b2-175">That computation is not a core responsibility of an `Address` class.</span></span> <span data-ttu-id="6c3b2-176">Se změní v čase, pravděpodobně častěji než změny formátu adresy.</span><span class="sxs-lookup"><span data-stu-id="6c3b2-176">It will change over time, likely more often than address format changes.</span></span> <span data-ttu-id="6c3b2-177">Množství DPH závisí `State` vlastnost adresy.</span><span class="sxs-lookup"><span data-stu-id="6c3b2-177">The amount of sales tax depends on the `State` property of the address.</span></span> <span data-ttu-id="6c3b2-178">Následující metoda používá vzor pro vlastnost pro výpočet DPH z adresy a cena:</span><span class="sxs-lookup"><span data-stu-id="6c3b2-178">The following method uses the property pattern to compute the sales tax from the address and the price:</span></span>

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

<span data-ttu-id="6c3b2-179">Porovnávání vzorů vytvoří stručnější syntaxe pro vyjádření tento algoritmus.</span><span class="sxs-lookup"><span data-stu-id="6c3b2-179">Pattern matching creates a concise syntax for expressing this algorithm.</span></span>

### <a name="tuple-patterns"></a><span data-ttu-id="6c3b2-180">Vzory řazené kolekce členů</span><span class="sxs-lookup"><span data-stu-id="6c3b2-180">Tuple patterns</span></span>

<span data-ttu-id="6c3b2-181">Některé algoritmy závisí na více vstupů.</span><span class="sxs-lookup"><span data-stu-id="6c3b2-181">Some algorithms depend on multiple inputs.</span></span> <span data-ttu-id="6c3b2-182">**Vzory řazené kolekce členů** bylo možné přepnout na základě více hodnot, vyjádřené jako [řazené kolekce členů](../tuples.md).</span><span class="sxs-lookup"><span data-stu-id="6c3b2-182">**Tuple patterns** allow you to switch based on multiple values expressed as a [tuple](../tuples.md).</span></span>  <span data-ttu-id="6c3b2-183">Následující kód ukazuje výraz přepínače hry *rock, dokument, nůžek*:</span><span class="sxs-lookup"><span data-stu-id="6c3b2-183">The following code shows a switch expression for the game *rock, paper, scissors*:</span></span>

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

<span data-ttu-id="6c3b2-184">Zprávy určit vítěze.</span><span class="sxs-lookup"><span data-stu-id="6c3b2-184">The messages indicate the winner.</span></span> <span data-ttu-id="6c3b2-185">Případ zahození představuje tři kombinace pro vazby nebo další textovými vstupy.</span><span class="sxs-lookup"><span data-stu-id="6c3b2-185">The discard case represents the three combinations for ties, or other text inputs.</span></span>

### <a name="positional-patterns"></a><span data-ttu-id="6c3b2-186">Poziční vzory</span><span class="sxs-lookup"><span data-stu-id="6c3b2-186">Positional patterns</span></span>

<span data-ttu-id="6c3b2-187">Některé typy zahrnují `Deconstruct` metodu, která do proměnných diskrétního deconstructs její vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="6c3b2-187">Some types include a `Deconstruct` method that deconstructs its properties into discrete variables.</span></span> <span data-ttu-id="6c3b2-188">Když `Deconstruct` metoda je přístupná, můžete použít **poziční vzory** ke kontrole vlastností objektu a použijte tyto vlastnosti pro vzor.</span><span class="sxs-lookup"><span data-stu-id="6c3b2-188">When a `Deconstruct` method is accessible, you can use **positional patterns** to inspect properties of the object and use those properties for a pattern.</span></span>  <span data-ttu-id="6c3b2-189">Vezměte v úvahu následující `Point` třídu, která zahrnuje `Deconstruct` metodu pro vytvoření proměnné diskrétního pro `X` a `Y`:</span><span class="sxs-lookup"><span data-stu-id="6c3b2-189">Consider the following `Point` class that includes a `Deconstruct` method to create discrete variables for `X` and `Y`:</span></span>

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

<span data-ttu-id="6c3b2-190">Kromě toho zvažte následující výčtového typu, který představuje různé pozic kvadrantu:</span><span class="sxs-lookup"><span data-stu-id="6c3b2-190">Additionally, consider the following enum that represents various positions of a quadrant:</span></span>

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

<span data-ttu-id="6c3b2-191">Používá následující metodu **poziční vzor** k extrakci hodnot z `x` a `y`.</span><span class="sxs-lookup"><span data-stu-id="6c3b2-191">The following method uses the **positional pattern** to extract the values of `x` and `y`.</span></span> <span data-ttu-id="6c3b2-192">Potom použije `when` klauzule určit `Quadrant` bodu:</span><span class="sxs-lookup"><span data-stu-id="6c3b2-192">Then, it uses a `when` clause to determine the `Quadrant` of the point:</span></span>

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

<span data-ttu-id="6c3b2-193">Vzor zrušení v předchozím přepínače odpovídá při buď `x` nebo `y` je 0, ale ne obojí.</span><span class="sxs-lookup"><span data-stu-id="6c3b2-193">The discard pattern in the preceding switch matches when either `x` or `y` is 0, but not both.</span></span> <span data-ttu-id="6c3b2-194">Výraz přepínače musíte vytvořit hodnotu nebo vyvolat výjimku.</span><span class="sxs-lookup"><span data-stu-id="6c3b2-194">A switch expression must either produce a value or throw an exception.</span></span> <span data-ttu-id="6c3b2-195">Výraz přepínače vyvolá výjimku, pokud neodpovídá žádná případů.</span><span class="sxs-lookup"><span data-stu-id="6c3b2-195">If none of the cases match, the switch expression throws an exception.</span></span> <span data-ttu-id="6c3b2-196">Kompilátor vygeneruje upozornění za vás, pokud jste ve výrazu přepínače nepokrývají všechny možné případy.</span><span class="sxs-lookup"><span data-stu-id="6c3b2-196">The compiler generates a warning for you if you do not cover all possible cases in your switch expression.</span></span>

<span data-ttu-id="6c3b2-197">Můžete prozkoumat porovnávání vzorů postupy v tomto [Upřesnit kurz o porovnávání vzorů](../tutorials/pattern-matching.md).</span><span class="sxs-lookup"><span data-stu-id="6c3b2-197">You can explore pattern matching techniques in this [advanced tutorial on pattern matching](../tutorials/pattern-matching.md).</span></span>

## <a name="using-declarations"></a><span data-ttu-id="6c3b2-198">Pomocí deklarace</span><span class="sxs-lookup"><span data-stu-id="6c3b2-198">using declarations</span></span>

<span data-ttu-id="6c3b2-199">A **using – deklarace** deklaraci proměnné předchází `using` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="6c3b2-199">A **using declaration** is a variable declaration preceded by the `using` keyword.</span></span> <span data-ttu-id="6c3b2-200">To sděluje kompilátoru, že by mělo být uvolněno deklarované proměnné na konci nadřazeném oboru.</span><span class="sxs-lookup"><span data-stu-id="6c3b2-200">It tells the compiler that the variable being declared should be disposed at the end of the enclosing scope.</span></span> <span data-ttu-id="6c3b2-201">Zvažte například následující kód, který zapisuje do textového souboru:</span><span class="sxs-lookup"><span data-stu-id="6c3b2-201">For example, consider the following code that writes a text file:</span></span>

```csharp
static void WriteLinesToFile(IEnumerable<string> lines)
{
    using var file = new System.IO.StreamWriter("WriteLines2.txt");
    foreach (string line in lines)
    {
        // If the line doesn't contain the word 'Second', write the line to the file.
        if (!line.Contains("Second"))
        {
            file.WriteLine(line);
        }
    }
// file is disposed here
}
```

<span data-ttu-id="6c3b2-202">V předchozím příkladu je soubor odstraněn po dosažení pravou složenou závorku v případě metody.</span><span class="sxs-lookup"><span data-stu-id="6c3b2-202">In the preceding example, the file is disposed when the closing brace for the method is reached.</span></span> <span data-ttu-id="6c3b2-203">Který je koncem objektu oboru, ve kterém `file` je deklarována.</span><span class="sxs-lookup"><span data-stu-id="6c3b2-203">That's the end of the scope in which `file` is declared.</span></span> <span data-ttu-id="6c3b2-204">Předchozí kód je ekvivalentní následujícímu kódu pomocí klasického [příkazy using](../language-reference/keywords/using-statement.md) – příkaz:</span><span class="sxs-lookup"><span data-stu-id="6c3b2-204">The preceding code is equivalent to the following code using the classic [using statements](../language-reference/keywords/using-statement.md) statement:</span></span>

```csharp
static void WriteLinesToFile(IEnumerable<string> lines)
{
    using (var file = new System.IO.StreamWriter("WriteLines2.txt"))
    {
        foreach (string line in lines)
        {
            // If the line doesn't contain the word 'Second', write the line to the file.
            if (!line.Contains("Second"))
            {
                file.WriteLine(line);
            }
        }
    } // file is disposed here
}
```

<span data-ttu-id="6c3b2-205">V předchozím příkladu je soubor uvolněno při přidružené pravou složenou závorku `using` je dosažen příkaz.</span><span class="sxs-lookup"><span data-stu-id="6c3b2-205">In the preceding example, the file is disposed when the closing brace associated with the `using` statement is reached.</span></span>

<span data-ttu-id="6c3b2-206">V obou případech platí, kompilátor vygeneruje volání `Dispose()`.</span><span class="sxs-lookup"><span data-stu-id="6c3b2-206">In both cases, the compiler generates the call to `Dispose()`.</span></span> <span data-ttu-id="6c3b2-207">Kompilátor vygeneruje chybu, pokud výraz v pomocí příkazu není na jedno použití.</span><span class="sxs-lookup"><span data-stu-id="6c3b2-207">The compiler generates an error if the expression in the using statement is not disposable.</span></span>

## <a name="static-local-functions"></a><span data-ttu-id="6c3b2-208">Statická lokální funkce</span><span class="sxs-lookup"><span data-stu-id="6c3b2-208">Static local functions</span></span>

<span data-ttu-id="6c3b2-209">Teď můžete přidávat `static` modifikátor lokální funkce zajistit, že místní funkce nezachytí (referenční dokumentace) všechny proměnné v ohraničujícím oboru.</span><span class="sxs-lookup"><span data-stu-id="6c3b2-209">You can now add the `static` modifier to local functions to ensure that local function doesn't capture (reference) any variables from the enclosing scope.</span></span> <span data-ttu-id="6c3b2-210">Tím se vygeneruje `CS8421`, "statické lokální funkce nesmí obsahovat odkaz na \<proměnná >."</span><span class="sxs-lookup"><span data-stu-id="6c3b2-210">Doing so generates `CS8421`, "A static local function can't contain a reference to \<variable>."</span></span> 

<span data-ttu-id="6c3b2-211">Uvažujme následující kód.</span><span class="sxs-lookup"><span data-stu-id="6c3b2-211">Consider the following code.</span></span> <span data-ttu-id="6c3b2-212">Lokální funkce `LocalFunction` přistupuje k proměnné `y`, které jsou deklarovány v ohraničujícím oboru (metoda `M`).</span><span class="sxs-lookup"><span data-stu-id="6c3b2-212">The local function `LocalFunction` accesses the variable `y`, declared in the enclosing scope (the method `M`).</span></span> <span data-ttu-id="6c3b2-213">Proto `LocalFunction` se nedá deklarovat pomocí `static` modifikátor:</span><span class="sxs-lookup"><span data-stu-id="6c3b2-213">Therefore, `LocalFunction` can't be declared with the `static` modifier:</span></span>

```csharp
int M()
{
    int y;
    LocalFunction();
    return y;

    void LocalFunction() => y = 0;
}
```

<span data-ttu-id="6c3b2-214">Následující kód obsahuje statické lokální funkce.</span><span class="sxs-lookup"><span data-stu-id="6c3b2-214">The following code contains a static local function.</span></span> <span data-ttu-id="6c3b2-215">Může být statická, protože nemá přístup k žádné proměnné v ohraničujícím oboru:</span><span class="sxs-lookup"><span data-stu-id="6c3b2-215">It can be static because it doesn't access any variables in the enclosing scope:</span></span>

```csharp
int M()
{
    int y = 5;
    int x = 7;
    return Add(x, y);

    static int Add(int left, int right) => left + right;
}
```

## <a name="disposable-ref-structs"></a><span data-ttu-id="6c3b2-216">Struktury ref uvolnitelné</span><span class="sxs-lookup"><span data-stu-id="6c3b2-216">Disposable ref structs</span></span>

<span data-ttu-id="6c3b2-217">A `struct` deklarované s `ref` modifikátor nemusí implementovat jakékoli rozhraní a proto nemůže implementovat <xref:System.IDisposable>.</span><span class="sxs-lookup"><span data-stu-id="6c3b2-217">A `struct` declared with the `ref` modifier may not implement any interfaces and so cannot implement <xref:System.IDisposable>.</span></span> <span data-ttu-id="6c3b2-218">Proto aby `ref struct` odstraněn, musí mít k dispozici přístup `void Dispose()` metoda.</span><span class="sxs-lookup"><span data-stu-id="6c3b2-218">Therefore, to enable a `ref struct` to be disposed, it must have an accessible `void Dispose()` method.</span></span> <span data-ttu-id="6c3b2-219">To platí i pro `readonly ref struct` deklarace.</span><span class="sxs-lookup"><span data-stu-id="6c3b2-219">This also applies to `readonly ref struct` declarations.</span></span>

## <a name="nullable-reference-types"></a><span data-ttu-id="6c3b2-220">Odkazové typy s možnou hodnotou null</span><span class="sxs-lookup"><span data-stu-id="6c3b2-220">Nullable reference types</span></span>

<span data-ttu-id="6c3b2-221">V kontextu poznámky s možnou hodnotou Null, všechny proměnné typu odkazu se považuje za **nonnullable odkazový typ**.</span><span class="sxs-lookup"><span data-stu-id="6c3b2-221">Inside a nullable annotation context, any variable of a reference type is considered to be a **nonnullable reference type**.</span></span> <span data-ttu-id="6c3b2-222">Pokud chcete určit, že proměnná může mít hodnotu null, musí připojit k názvu typu `?` deklarovat jako proměnnou **typ s možnou hodnotou Null odkazu**.</span><span class="sxs-lookup"><span data-stu-id="6c3b2-222">If you want to indicate that a variable may be null, you must append the type name with the `?` to declare the variable as a **nullable reference type**.</span></span>

<span data-ttu-id="6c3b2-223">Pro typy odkazů nemá kompilátor používá k zajištění, že místní proměnné jsou inicializovány na hodnotu než null při deklaraci analýzy toku.</span><span class="sxs-lookup"><span data-stu-id="6c3b2-223">For nonnullable reference types, the compiler uses flow analysis to ensure that local variables are initialized to a non-null value when declared.</span></span> <span data-ttu-id="6c3b2-224">Pole musí být inicializován během konstrukce.</span><span class="sxs-lookup"><span data-stu-id="6c3b2-224">Fields must be initialized during construction.</span></span> <span data-ttu-id="6c3b2-225">Kompilátor generuje upozornění, pokud proměnná není nastavená voláním kterýkoli z konstruktorů k dispozici nebo inicializátor.</span><span class="sxs-lookup"><span data-stu-id="6c3b2-225">The compiler generates a warning if the variable is not set by a call to any of the available constructors or by an initializer.</span></span> <span data-ttu-id="6c3b2-226">Kromě toho nemá odkazové typy nelze přiřadit hodnotu, která může mít hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="6c3b2-226">Furthermore, nonnullable reference types can't be assigned a value that could be null.</span></span>

<span data-ttu-id="6c3b2-227">Typy odkazů s možnou hodnotou Null nejsou kontrola nejsou přiřazen nebo inicializován na hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="6c3b2-227">Nullable reference types aren't checked to ensure they aren't assigned or initialized to null.</span></span> <span data-ttu-id="6c3b2-228">Však kompilátor používá k zajištění, že všechny proměnné typu odkazu s možnou hodnotou null je porovnány s hodnotou null, předtím, než má získat přístup nebo přiřazený k typu odkazu nonnullable analýzy toku.</span><span class="sxs-lookup"><span data-stu-id="6c3b2-228">However, the compiler uses flow analysis to ensure that any variable of a nullable reference type is checked against null before it's accessed or assigned to a nonnullable reference type.</span></span>

<span data-ttu-id="6c3b2-229">Další informace o funkci v přehledu [typy s možnou hodnotou Null odkazů](../nullable-references.md).</span><span class="sxs-lookup"><span data-stu-id="6c3b2-229">You can learn more about the feature in the overview of [nullable reference types](../nullable-references.md).</span></span> <span data-ttu-id="6c3b2-230">Vyzkoušejte si to sami v nové aplikaci v tomto [kurzu typy s možnou hodnotou Null reference](../tutorials/nullable-reference-types.md).</span><span class="sxs-lookup"><span data-stu-id="6c3b2-230">Try it yourself in a new application in this [nullable reference types tutorial](../tutorials/nullable-reference-types.md).</span></span> <span data-ttu-id="6c3b2-231">Seznamte se s kroky při migraci z existujícího základu kódu, aby použití typů s povolenou hodnotou Null odkazu v [migrace aplikace pro použití s možnou hodnotou NULL referenční typy kurzu](../tutorials/upgrade-to-nullable-references.md).</span><span class="sxs-lookup"><span data-stu-id="6c3b2-231">Learn about the steps to migrate an existing codebase to make use of nullable reference types in the [migrating an application to use nullable reference types tutorial](../tutorials/upgrade-to-nullable-references.md).</span></span>

## <a name="asynchronous-streams"></a><span data-ttu-id="6c3b2-232">Asynchronní datové proudy</span><span class="sxs-lookup"><span data-stu-id="6c3b2-232">Asynchronous streams</span></span>

<span data-ttu-id="6c3b2-233">Počínaje C# 8.0, lze vytvářet a využívat datové proudy asynchronně.</span><span class="sxs-lookup"><span data-stu-id="6c3b2-233">Starting with C# 8.0, you can create and consume streams asynchronously.</span></span> <span data-ttu-id="6c3b2-234">Metodu vracející asynchronní datový proud má tři vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="6c3b2-234">A method that returns an asynchronous stream has three properties:</span></span>

1. <span data-ttu-id="6c3b2-235">Je deklarována s `async` modifikátor.</span><span class="sxs-lookup"><span data-stu-id="6c3b2-235">It's declared with the `async` modifier.</span></span>
1. <span data-ttu-id="6c3b2-236">Vrátí <xref:System.Collections.Generic.IAsyncEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="6c3b2-236">It returns an <xref:System.Collections.Generic.IAsyncEnumerable%601>.</span></span>
1. <span data-ttu-id="6c3b2-237">Metoda obsahuje `yield return` příkazy vrátit po sobě jdoucí prvky v asynchronního datového proudu.</span><span class="sxs-lookup"><span data-stu-id="6c3b2-237">The method contains `yield return` statements to return successive elements in the asynchronous stream.</span></span>

<span data-ttu-id="6c3b2-238">Použití asynchronního datového proudu je potřeba přidat `await` – klíčové slovo před `foreach` – klíčové slovo při výčtu prvky datového proudu.</span><span class="sxs-lookup"><span data-stu-id="6c3b2-238">Consuming an asynchronous stream requires you to add the `await` keyword before the `foreach` keyword when you enumerate the elements of the stream.</span></span> <span data-ttu-id="6c3b2-239">Přidání `await` – klíčové slovo vyžaduje metodu, která vytvoří výčet asynchronního datového proudu deklarován s `async` modifikátor a návratový typ povolené pro `async` metoda.</span><span class="sxs-lookup"><span data-stu-id="6c3b2-239">Adding the `await` keyword requires the method that enumerates the asynchronous stream to be declared with the `async` modifier and to return a type allowed for an `async` method.</span></span> <span data-ttu-id="6c3b2-240">Obvykle to znamená, že vrácení <xref:System.Threading.Tasks.Task> nebo <xref:System.Threading.Tasks.Task%601>.</span><span class="sxs-lookup"><span data-stu-id="6c3b2-240">Typically that means returning a <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="6c3b2-241">Může být <xref:System.Threading.Tasks.ValueTask> nebo <xref:System.Threading.Tasks.ValueTask%601>.</span><span class="sxs-lookup"><span data-stu-id="6c3b2-241">It can also be a <xref:System.Threading.Tasks.ValueTask> or <xref:System.Threading.Tasks.ValueTask%601>.</span></span> <span data-ttu-id="6c3b2-242">Metoda může současně využívají a produkují asynchronní datový proud, což znamená, že by měla vrátit <xref:System.Collections.Generic.IAsyncEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="6c3b2-242">A method can both consume and produce an asynchronous stream, which means it would return an <xref:System.Collections.Generic.IAsyncEnumerable%601>.</span></span> <span data-ttu-id="6c3b2-243">Následující kód generuje sekvenci od 0 do 19 čekání na 100 ms mezi generování každé číslo:</span><span class="sxs-lookup"><span data-stu-id="6c3b2-243">The following code generates a sequence from 0 to 19, waiting 100 ms between generating each number:</span></span>

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

<span data-ttu-id="6c3b2-244">By výčet pomocí pořadí `await foreach` – příkaz:</span><span class="sxs-lookup"><span data-stu-id="6c3b2-244">You would enumerate the sequence using the `await foreach` statement:</span></span>

```csharp
await foreach (var number in GenerateSequence())
{
    Console.WriteLine(number);
}
```

<span data-ttu-id="6c3b2-245">Můžete zkusit asynchronními datovými proudy sami v našem kurzu [vytváření a používání asynchronních streamů](../tutorials/generate-consume-asynchronous-stream.md).</span><span class="sxs-lookup"><span data-stu-id="6c3b2-245">You can try asynchronous streams yourself in our tutorial on [creating and consuming async streams](../tutorials/generate-consume-asynchronous-stream.md).</span></span>

## <a name="indices-and-ranges"></a><span data-ttu-id="6c3b2-246">Indexy a rozsahy</span><span class="sxs-lookup"><span data-stu-id="6c3b2-246">Indices and ranges</span></span>

<span data-ttu-id="6c3b2-247">Rozsahy a indexy poskytují stručné syntaxe pro zadání podrozsahů v poli, <xref:System.Span%601>, nebo <xref:System.ReadOnlySpan%601>.</span><span class="sxs-lookup"><span data-stu-id="6c3b2-247">Ranges and indices provide a succinct syntax for specifying subranges in an array, <xref:System.Span%601>, or <xref:System.ReadOnlySpan%601>.</span></span>

<span data-ttu-id="6c3b2-248">Tato podpora jazyka spoléhá na dva nové typy a dvou nových operátorů.</span><span class="sxs-lookup"><span data-stu-id="6c3b2-248">This language support relies on two new types, and two new operators.</span></span>
- <span data-ttu-id="6c3b2-249"><xref:System.Index?displayProperty=nameWithType> představuje index na sekvenci.</span><span class="sxs-lookup"><span data-stu-id="6c3b2-249"><xref:System.Index?displayProperty=nameWithType> represents an index into a sequence.</span></span>
- <span data-ttu-id="6c3b2-250">`^` Operátor, který určuje, že je index vzhledem ke konci sekvence.</span><span class="sxs-lookup"><span data-stu-id="6c3b2-250">The `^` operator, which specifies that an index is relative to the end of the sequence.</span></span>
- <span data-ttu-id="6c3b2-251"><xref:System.Range?displayProperty=nameWithType> představuje rozsah dílčí sekvenci.</span><span class="sxs-lookup"><span data-stu-id="6c3b2-251"><xref:System.Range?displayProperty=nameWithType> represents a sub range of a sequence.</span></span>
- <span data-ttu-id="6c3b2-252">Operátor rozsahu (`..`), který určuje začátek a konec rozsahu, jako je operandy.</span><span class="sxs-lookup"><span data-stu-id="6c3b2-252">The Range operator (`..`), which specifies the start and end of a range as is operands.</span></span>

<span data-ttu-id="6c3b2-253">Začněme s pravidly pro indexy.</span><span class="sxs-lookup"><span data-stu-id="6c3b2-253">Let's start with the rules for indexes.</span></span> <span data-ttu-id="6c3b2-254">Vezměte v úvahu pole `sequence`.</span><span class="sxs-lookup"><span data-stu-id="6c3b2-254">Consider an array `sequence`.</span></span> <span data-ttu-id="6c3b2-255">`0` Index je stejný jako `sequence[0]`.</span><span class="sxs-lookup"><span data-stu-id="6c3b2-255">The `0` index is the same as `sequence[0]`.</span></span> <span data-ttu-id="6c3b2-256">`^0` Index je stejný jako `sequence[sequence.Length]`.</span><span class="sxs-lookup"><span data-stu-id="6c3b2-256">The `^0` index is the same as `sequence[sequence.Length]`.</span></span> <span data-ttu-id="6c3b2-257">Všimněte si, že `sequence[^0]` vyvolá výjimku, stejně jako `sequence[sequence.Length]` nepodporuje.</span><span class="sxs-lookup"><span data-stu-id="6c3b2-257">Note that `sequence[^0]` does throw an exception, just as `sequence[sequence.Length]` does.</span></span> <span data-ttu-id="6c3b2-258">Pro libovolný počet `n`, index `^n` je stejný jako `sequence.Length - n`.</span><span class="sxs-lookup"><span data-stu-id="6c3b2-258">For any number `n`, the index `^n` is the same as `sequence.Length - n`.</span></span>

<span data-ttu-id="6c3b2-259">Určuje oblast *start* a *koncové* rozsahu.</span><span class="sxs-lookup"><span data-stu-id="6c3b2-259">A range specifies the *start* and *end* of a range.</span></span> <span data-ttu-id="6c3b2-260">Začátek rozsahu je také zahrnuto, ale je exkluzivní, což znamená konec rozsahu *start* je součástí rozsahu ale *end* není zahrnutý v rozsahu.</span><span class="sxs-lookup"><span data-stu-id="6c3b2-260">The start of the range is inclusive, but the end of the range is exclusive, meaning the *start* is included in the range but the *end* is not included in the range.</span></span> <span data-ttu-id="6c3b2-261">Rozsah `[0..^0]` představuje celou oblast, stejně jako `[0..sequence.Length]` představuje celou oblast.</span><span class="sxs-lookup"><span data-stu-id="6c3b2-261">The range `[0..^0]` represents the entire range, just as `[0..sequence.Length]` represents the entire range.</span></span> 

<span data-ttu-id="6c3b2-262">Podívejme se na několik příkladů.</span><span class="sxs-lookup"><span data-stu-id="6c3b2-262">Let's look at a few examples.</span></span> <span data-ttu-id="6c3b2-263">Vezměte v úvahu následující pole označena s jeho index od samého začátku a konci:</span><span class="sxs-lookup"><span data-stu-id="6c3b2-263">Consider the following array, annotated with its index from the start and from the end:</span></span>

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

<span data-ttu-id="6c3b2-264">Můžete načíst poslední slovo s `^1` indexu:</span><span class="sxs-lookup"><span data-stu-id="6c3b2-264">You can retrieve the last word with the `^1` index:</span></span>

```csharp
Console.WriteLine($"The last word is {words[^1]}");
// writes "dog"
```

<span data-ttu-id="6c3b2-265">Následující kód vytvoří podrozsahu s slova "rychlé", "brown" a "fox".</span><span class="sxs-lookup"><span data-stu-id="6c3b2-265">The following code creates a subrange with the words "quick", "brown", and "fox".</span></span> <span data-ttu-id="6c3b2-266">Zahrnuje `words[1]` prostřednictvím `words[3]`.</span><span class="sxs-lookup"><span data-stu-id="6c3b2-266">It includes `words[1]` through `words[3]`.</span></span> <span data-ttu-id="6c3b2-267">Element `words[4]` není v rozsahu.</span><span class="sxs-lookup"><span data-stu-id="6c3b2-267">The element `words[4]` is not in the range.</span></span>

```csharp
var quickBrownFox = words[1..4];
```

<span data-ttu-id="6c3b2-268">Následující kód vytvoří podrozsahu "opožděné" a "pes".</span><span class="sxs-lookup"><span data-stu-id="6c3b2-268">The following code creates a subrange with "lazy" and "dog".</span></span> <span data-ttu-id="6c3b2-269">Zahrnuje `words[^2]` a `words[^1]`.</span><span class="sxs-lookup"><span data-stu-id="6c3b2-269">It includes `words[^2]` and `words[^1]`.</span></span> <span data-ttu-id="6c3b2-270">Koncová hodnota `words[^0]` nezahrnuje:</span><span class="sxs-lookup"><span data-stu-id="6c3b2-270">The end index `words[^0]` is not included:</span></span>

```csharp
var lazyDog = words[^2..^0];
```

<span data-ttu-id="6c3b2-271">Následující příklady vytváří rozsahy, které jsou otevřené skončila pro zahájení a ukončení:</span><span class="sxs-lookup"><span data-stu-id="6c3b2-271">The following examples create ranges that are open ended for the start, end, or both:</span></span>

```csharp
var allWords = words[..]; // contains "The" through "dog".
var firstPhrase = words[..4]; // contains "The" through "fox"
var lastPhrase = words[6..]; // contains "the, "lazy" and "dog"
```

<span data-ttu-id="6c3b2-272">Rozsahy můžete také deklarovat jako proměnné:</span><span class="sxs-lookup"><span data-stu-id="6c3b2-272">You can also declare ranges as variables:</span></span>

```csharp
Range phrase = 1..4;
```

<span data-ttu-id="6c3b2-273">Rozsah je pak možné uvnitř `[` a `]` znaků:</span><span class="sxs-lookup"><span data-stu-id="6c3b2-273">The range can then be used inside the `[` and `]` characters:</span></span>

```csharp
var text = words[phrase];
```

<span data-ttu-id="6c3b2-274">Další informace o indexy a rozsahy můžete prozkoumat v tomto kurzu na [indexy a rozsahy adres](../tutorials/ranges-indexes.md).</span><span class="sxs-lookup"><span data-stu-id="6c3b2-274">You can explore more about indices and ranges in the tutorial on [indices and ranges](../tutorials/ranges-indexes.md).</span></span>
