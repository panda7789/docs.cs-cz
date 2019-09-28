---
title: Prozkoumat rozsahy dat pomocí indexů a rozsahů
description: V tomto pokročilém kurzu se naučíte prozkoumat data pomocí indexů a rozsahů, abyste prozkoumali řezy sekvenční sady dat.
ms.date: 09/20/2019
ms.custom: mvc
ms.openlocfilehash: a879601e1358f72e80983992a3cd96ba1fb06a38
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/27/2019
ms.locfileid: "71391965"
---
# <a name="indices-and-ranges"></a><span data-ttu-id="73907-103">Indexy a rozsahy</span><span class="sxs-lookup"><span data-stu-id="73907-103">Indices and ranges</span></span>

<span data-ttu-id="73907-104">Rozsahy a indexy poskytují stručnou syntaxi pro přístup k jednotlivým prvkům nebo rozsahům v sekvenci.</span><span class="sxs-lookup"><span data-stu-id="73907-104">Ranges and indices provide a succinct syntax for accessing single elements or ranges in a sequence.</span></span>

<span data-ttu-id="73907-105">V tomto kurzu se naučíte:</span><span class="sxs-lookup"><span data-stu-id="73907-105">In this tutorial, you'll learn how to:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="73907-106">Použijte syntaxi pro rozsahy v sekvenci.</span><span class="sxs-lookup"><span data-stu-id="73907-106">Use the syntax for ranges in a sequence.</span></span>
> - <span data-ttu-id="73907-107">Pochopení rozhodnutí o návrhu pro začátek a konec každé sekvence.</span><span class="sxs-lookup"><span data-stu-id="73907-107">Understand the design decisions for the start and end of each sequence.</span></span>
> - <span data-ttu-id="73907-108">Naučte se <xref:System.Index> scénáře pro <xref:System.Range> typy a.</span><span class="sxs-lookup"><span data-stu-id="73907-108">Learn scenarios for the <xref:System.Index> and <xref:System.Range> types.</span></span>

## <a name="language-support-for-indices-and-ranges"></a><span data-ttu-id="73907-109">Podpora jazyků pro indexy a rozsahy</span><span class="sxs-lookup"><span data-stu-id="73907-109">Language support for indices and ranges</span></span>

<span data-ttu-id="73907-110">Tato podpora jazyků spoléhá na dva nové typy a dva nové operátory:</span><span class="sxs-lookup"><span data-stu-id="73907-110">This language support relies on two new types and two new operators:</span></span>

- <span data-ttu-id="73907-111"><xref:System.Index?displayProperty=nameWithType>představuje index do sekvence.</span><span class="sxs-lookup"><span data-stu-id="73907-111"><xref:System.Index?displayProperty=nameWithType> represents an index into a sequence.</span></span>
- <span data-ttu-id="73907-112">Index z operátoru `^`end, který určuje, že index je relativní ke konci sekvence.</span><span class="sxs-lookup"><span data-stu-id="73907-112">The index from end operator `^`, which specifies that an index is relative to the end of a sequence.</span></span>
- <span data-ttu-id="73907-113"><xref:System.Range?displayProperty=nameWithType>představuje dílčí rozsah sekvence.</span><span class="sxs-lookup"><span data-stu-id="73907-113"><xref:System.Range?displayProperty=nameWithType> represents a sub range of a sequence.</span></span>
- <span data-ttu-id="73907-114">Operátor `..`rozsahu, který určuje začátek a konec rozsahu jako jeho operandy.</span><span class="sxs-lookup"><span data-stu-id="73907-114">The range operator `..`, which specifies the start and end of a range as its operands.</span></span>

<span data-ttu-id="73907-115">Pojďme začít s pravidly pro indexy.</span><span class="sxs-lookup"><span data-stu-id="73907-115">Let's start with the rules for indices.</span></span> <span data-ttu-id="73907-116">Zvažte pole `sequence`.</span><span class="sxs-lookup"><span data-stu-id="73907-116">Consider an array `sequence`.</span></span> <span data-ttu-id="73907-117">Index je stejný jako `sequence[0]`. `0`</span><span class="sxs-lookup"><span data-stu-id="73907-117">The `0` index is the same as `sequence[0]`.</span></span> <span data-ttu-id="73907-118">Index je stejný jako `sequence[sequence.Length]`. `^0`</span><span class="sxs-lookup"><span data-stu-id="73907-118">The `^0` index is the same as `sequence[sequence.Length]`.</span></span> <span data-ttu-id="73907-119">Všimněte si `sequence[^0]` , že vyvolá výjimku, stejně jako `sequence[sequence.Length]` .</span><span class="sxs-lookup"><span data-stu-id="73907-119">Note that `sequence[^0]` does throw an exception, just as `sequence[sequence.Length]` does.</span></span> <span data-ttu-id="73907-120">Pro jakékoli číslo `n`je index `^n` stejný jako `sequence[sequence.Length - n]`.</span><span class="sxs-lookup"><span data-stu-id="73907-120">For any number `n`, the index `^n` is the same as `sequence[sequence.Length - n]`.</span></span>

```csharp-interactive
string[] words = new string[]
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

<span data-ttu-id="73907-121">Poslední slovo můžete načíst s `^1` indexem.</span><span class="sxs-lookup"><span data-stu-id="73907-121">You can retrieve the last word with the `^1` index.</span></span> <span data-ttu-id="73907-122">Pod inicializaci přidejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="73907-122">Add the following code below the initialization:</span></span>

[!code-csharp[LastIndex](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_LastIndex)]

<span data-ttu-id="73907-123">Rozsah Určuje *začátek* a *konec* rozsahu.</span><span class="sxs-lookup"><span data-stu-id="73907-123">A range specifies the *start* and *end* of a range.</span></span> <span data-ttu-id="73907-124">Rozsahy jsou exkluzivní, což znamená, že *konec* není zahrnutý v rozsahu.</span><span class="sxs-lookup"><span data-stu-id="73907-124">Ranges are exclusive, meaning the *end* is not included in the range.</span></span> <span data-ttu-id="73907-125">Rozsah `[0..^0]` představuje celý rozsah, stejně jako `[0..sequence.Length]` představuje celý rozsah.</span><span class="sxs-lookup"><span data-stu-id="73907-125">The range `[0..^0]` represents the entire range, just as `[0..sequence.Length]` represents the entire range.</span></span> 

<span data-ttu-id="73907-126">Následující kód vytvoří dílčí rozsah s slovy "Rychlá", "hnědá" a "Fox".</span><span class="sxs-lookup"><span data-stu-id="73907-126">The following code creates a subrange with the words "quick", "brown", and "fox".</span></span> <span data-ttu-id="73907-127">Zahrnuje `words[1]` .`words[3]`</span><span class="sxs-lookup"><span data-stu-id="73907-127">It includes `words[1]` through `words[3]`.</span></span> <span data-ttu-id="73907-128">Element `words[4]` není v rozsahu.</span><span class="sxs-lookup"><span data-stu-id="73907-128">The element `words[4]` isn't in the range.</span></span> <span data-ttu-id="73907-129">Do stejné metody přidejte následující kód.</span><span class="sxs-lookup"><span data-stu-id="73907-129">Add the following code to the same method.</span></span> <span data-ttu-id="73907-130">Zkopírujte ho a vložte ho do dolní části okna interaktivní.</span><span class="sxs-lookup"><span data-stu-id="73907-130">Copy and paste it at the bottom of the interactive window.</span></span>

[!code-csharp[Range](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_Range)]

<span data-ttu-id="73907-131">Následující kód vytvoří dílčí rozsah s "opožděným" a "pes".</span><span class="sxs-lookup"><span data-stu-id="73907-131">The following code creates a subrange with "lazy" and "dog".</span></span> <span data-ttu-id="73907-132">Zahrnuje `words[^2]` a .`words[^1]`</span><span class="sxs-lookup"><span data-stu-id="73907-132">It includes `words[^2]` and `words[^1]`.</span></span> <span data-ttu-id="73907-133">Koncový index `words[^0]` není zahrnutý.</span><span class="sxs-lookup"><span data-stu-id="73907-133">The end index `words[^0]` isn't included.</span></span> <span data-ttu-id="73907-134">Přidejte také následující kód:</span><span class="sxs-lookup"><span data-stu-id="73907-134">Add the following code as well:</span></span>

[!code-csharp[LastRange](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_LastRange)]

<span data-ttu-id="73907-135">V následujících příkladech jsou vytvořeny rozsahy, které jsou otevřeny pro začátek, konec nebo obojí:</span><span class="sxs-lookup"><span data-stu-id="73907-135">The following examples create ranges that are open ended for the start, end, or both:</span></span>

[!code-csharp[PartialRange](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_PartialRanges)]

<span data-ttu-id="73907-136">Můžete také deklarovat rozsahy nebo indexy jako proměnné.</span><span class="sxs-lookup"><span data-stu-id="73907-136">You can also declare ranges or indices as variables.</span></span> <span data-ttu-id="73907-137">Proměnná se pak dá použít uvnitř `[` znaků a: `]`</span><span class="sxs-lookup"><span data-stu-id="73907-137">The variable can then be used inside the `[` and `]` characters:</span></span>

[!code-csharp[IndexRangeTypes](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_RangeIndexTypes)]

<span data-ttu-id="73907-138">Následující příklad znázorňuje mnoho z důvodů pro tyto volby.</span><span class="sxs-lookup"><span data-stu-id="73907-138">The following sample shows many of the reasons for those choices.</span></span> <span data-ttu-id="73907-139">Upravte `x`, `y`a a`z` vyzkoušejte různé kombinace.</span><span class="sxs-lookup"><span data-stu-id="73907-139">Modify `x`, `y`, and `z` to try different combinations.</span></span> <span data-ttu-id="73907-140">Při experimentování `x` použijte hodnoty, kde je menší než `y`a `y` je menší než `z` pro platné kombinace.</span><span class="sxs-lookup"><span data-stu-id="73907-140">When you experiment, use values where `x` is less than `y`, and `y` is less than `z` for valid combinations.</span></span> <span data-ttu-id="73907-141">Do nové metody přidejte následující kód.</span><span class="sxs-lookup"><span data-stu-id="73907-141">Add the following code in a new method.</span></span> <span data-ttu-id="73907-142">Vyzkoušejte různé kombinace:</span><span class="sxs-lookup"><span data-stu-id="73907-142">Try different combinations:</span></span>

[!code-csharp[SemanticsExamples](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_Semantics)]

## <a name="type-support-for-indices-and-ranges"></a><span data-ttu-id="73907-143">Podpora typů pro indexy a rozsahy</span><span class="sxs-lookup"><span data-stu-id="73907-143">Type support for indices and ranges</span></span>

<span data-ttu-id="73907-144">Pokud typ poskytuje [indexer](../programming-guide/indexers/index.md) s parametrem <xref:System.Index> nebo <xref:System.Range>, explicitně podporuje indexy nebo rozsahy v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="73907-144">If a type provides an [indexer](../programming-guide/indexers/index.md) with an <xref:System.Index> or <xref:System.Range> parameter, it explicitly supports indices or ranges respectively.</span></span>

<span data-ttu-id="73907-145">Typ je **vypočítán** , pokud má vlastnost s názvem `Length` nebo `Count` s přístupným mechanismem getter a návratovým typem `int`.</span><span class="sxs-lookup"><span data-stu-id="73907-145">A type is **countable** if it has a property named `Length` or `Count` with an accessible getter and a return type of `int`.</span></span> <span data-ttu-id="73907-146">Typ Count, který explicitně nepodporuje indexy nebo rozsahy, může pro ně poskytnout implicitní podporu.</span><span class="sxs-lookup"><span data-stu-id="73907-146">A countable type that doesn't explicitly support indices or ranges may provide an implicit support for them.</span></span> <span data-ttu-id="73907-147">Další informace naleznete v části Podpora [implicitního indexu](~/_csharplang/proposals/csharp-8.0/ranges.md#implicit-index-support) a [Podpora implicitního rozsahu](~/_csharplang/proposals/csharp-8.0/ranges.md#implicit-range-support) v [poznámce k návrhu funkcí](~/_csharplang/proposals/csharp-8.0/ranges.md).</span><span class="sxs-lookup"><span data-stu-id="73907-147">For more information, see the [Implicit Index support](~/_csharplang/proposals/csharp-8.0/ranges.md#implicit-index-support) and [Implicit Range support](~/_csharplang/proposals/csharp-8.0/ranges.md#implicit-range-support) sections of the [feature proposal note](~/_csharplang/proposals/csharp-8.0/ranges.md).</span></span>

<span data-ttu-id="73907-148">Například následující typy rozhraní .NET podporují jak indexy, tak rozsahy: <xref:System.Array>, <xref:System.String>, <xref:System.Span%601> a <xref:System.ReadOnlySpan%601>.</span><span class="sxs-lookup"><span data-stu-id="73907-148">For example, the following .NET types support both indices and ranges: <xref:System.Array>, <xref:System.String>, <xref:System.Span%601>, and <xref:System.ReadOnlySpan%601>.</span></span> <span data-ttu-id="73907-149">@No__t-0 podporuje indexy, ale nepodporuje rozsahy.</span><span class="sxs-lookup"><span data-stu-id="73907-149">The <xref:System.Collections.Generic.List%601> supports indices but doesn't support ranges.</span></span>

## <a name="scenarios-for-indices-and-ranges"></a><span data-ttu-id="73907-150">Scénáře pro indexy a rozsahy</span><span class="sxs-lookup"><span data-stu-id="73907-150">Scenarios for indices and ranges</span></span>

<span data-ttu-id="73907-151">Pokud chcete provést analýzu v podrozsahu celé sekvence, často použijete rozsahy a indexy.</span><span class="sxs-lookup"><span data-stu-id="73907-151">You'll often use ranges and indices when you want to perform some analysis on subrange of an entire sequence.</span></span> <span data-ttu-id="73907-152">Nová syntaxe je jasná při čtení přesně z toho, co je dílčí rozsah zahrnutý.</span><span class="sxs-lookup"><span data-stu-id="73907-152">The new syntax is clearer in reading exactly what subrange is involved.</span></span> <span data-ttu-id="73907-153">Místní funkce `MovingAverage` <xref:System.Range> přijímá jako svůj argument.</span><span class="sxs-lookup"><span data-stu-id="73907-153">The local function `MovingAverage` takes a <xref:System.Range> as its argument.</span></span> <span data-ttu-id="73907-154">Metoda pak při výpočtu minimálních, maximálních a průměrů vytvoří výčet pouze tohoto rozsahu.</span><span class="sxs-lookup"><span data-stu-id="73907-154">The method then enumerates just that range when calculating the min, max, and average.</span></span> <span data-ttu-id="73907-155">Vyzkoušejte následující kód v projektu:</span><span class="sxs-lookup"><span data-stu-id="73907-155">Try the following code in your project:</span></span>

[!code-csharp[MovingAverages](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_MovingAverage)]

<span data-ttu-id="73907-156">Dokončený kód si můžete stáhnout z úložiště [dotnet/Samples](https://github.com/dotnet/samples/tree/master/csharp/tutorials/RangesIndexes) .</span><span class="sxs-lookup"><span data-stu-id="73907-156">You can download the completed code from the [dotnet/samples](https://github.com/dotnet/samples/tree/master/csharp/tutorials/RangesIndexes) repository.</span></span>
