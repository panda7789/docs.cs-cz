---
title: Prozkoumat rozsahy dat pomocí indexů a rozsahů
description: V tomto pokročilém kurzu se naučíte prozkoumat data pomocí indexů a rozsahů, abyste prozkoumali řezy sekvenční sady dat.
ms.date: 04/19/2019
ms.custom: mvc
ms.openlocfilehash: 27f4b90f130345dd10517a5de78c759066afdf07
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70926642"
---
# <a name="indices-and-ranges"></a><span data-ttu-id="fcff3-103">Indexy a rozsahy</span><span class="sxs-lookup"><span data-stu-id="fcff3-103">Indices and ranges</span></span>

<span data-ttu-id="fcff3-104">Rozsahy a indexy poskytují stručnou syntaxi pro přístup k jednotlivým prvkům nebo rozsahům <xref:System.Array>v <xref:System.Span%601>, nebo <xref:System.ReadOnlySpan%601>.</span><span class="sxs-lookup"><span data-stu-id="fcff3-104">Ranges and indices provide a succinct syntax for accessing single elements or ranges in an <xref:System.Array>, <xref:System.Span%601>, or <xref:System.ReadOnlySpan%601>.</span></span> <span data-ttu-id="fcff3-105">Tyto funkce umožňují přesnější, jasnou syntaxi pro přístup k jednotlivým prvkům nebo rozsahům prvků v sekvenci.</span><span class="sxs-lookup"><span data-stu-id="fcff3-105">These features enable more concise, clear syntax to access single elements or ranges of elements in a sequence.</span></span>

<span data-ttu-id="fcff3-106">V tomto kurzu se naučíte:</span><span class="sxs-lookup"><span data-stu-id="fcff3-106">In this tutorial, you'll learn how to:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="fcff3-107">Použijte syntaxi pro rozsahy v sekvenci.</span><span class="sxs-lookup"><span data-stu-id="fcff3-107">Use the syntax for ranges in a sequence.</span></span>
> - <span data-ttu-id="fcff3-108">Pochopení rozhodnutí o návrhu pro začátek a konec každé sekvence.</span><span class="sxs-lookup"><span data-stu-id="fcff3-108">Understand the design decisions for the start and end of each sequence.</span></span>
> - <span data-ttu-id="fcff3-109">Naučte se <xref:System.Index> scénáře pro <xref:System.Range> typy a.</span><span class="sxs-lookup"><span data-stu-id="fcff3-109">Learn scenarios for the <xref:System.Index> and <xref:System.Range> types.</span></span>

## <a name="language-support-for-indices-and-ranges"></a><span data-ttu-id="fcff3-110">Podpora jazyků pro indexy a rozsahy</span><span class="sxs-lookup"><span data-stu-id="fcff3-110">Language support for indices and ranges</span></span>

<span data-ttu-id="fcff3-111">Tato podpora jazyků spoléhá na dva nové typy a dva nové operátory.</span><span class="sxs-lookup"><span data-stu-id="fcff3-111">This language support relies on two new types and two new operators.</span></span>

- <span data-ttu-id="fcff3-112"><xref:System.Index?displayProperty=nameWithType>představuje index do sekvence.</span><span class="sxs-lookup"><span data-stu-id="fcff3-112"><xref:System.Index?displayProperty=nameWithType> represents an index into a sequence.</span></span>
- <span data-ttu-id="fcff3-113">`^` Operátor, který určuje, že index je relativní ke konci sekvence.</span><span class="sxs-lookup"><span data-stu-id="fcff3-113">The `^` operator, which specifies that an index is relative to the end of a sequence.</span></span>
- <span data-ttu-id="fcff3-114"><xref:System.Range?displayProperty=nameWithType>představuje dílčí rozsah sekvence.</span><span class="sxs-lookup"><span data-stu-id="fcff3-114"><xref:System.Range?displayProperty=nameWithType> represents a sub range of a sequence.</span></span>
- <span data-ttu-id="fcff3-115">Operátor Range (`..`), který určuje začátek a konec rozsahu jako jeho operandy.</span><span class="sxs-lookup"><span data-stu-id="fcff3-115">The Range operator (`..`), which specifies the start and end of a range as its operands.</span></span>

<span data-ttu-id="fcff3-116">Pojďme začít s pravidly pro indexy.</span><span class="sxs-lookup"><span data-stu-id="fcff3-116">Let's start with the rules for indices.</span></span> <span data-ttu-id="fcff3-117">Zvažte pole `sequence`.</span><span class="sxs-lookup"><span data-stu-id="fcff3-117">Consider an array `sequence`.</span></span> <span data-ttu-id="fcff3-118">Index je stejný jako `sequence[0]`. `0`</span><span class="sxs-lookup"><span data-stu-id="fcff3-118">The `0` index is the same as `sequence[0]`.</span></span> <span data-ttu-id="fcff3-119">Index je stejný jako `sequence[sequence.Length]`. `^0`</span><span class="sxs-lookup"><span data-stu-id="fcff3-119">The `^0` index is the same as `sequence[sequence.Length]`.</span></span> <span data-ttu-id="fcff3-120">Všimněte si `sequence[^0]` , že vyvolá výjimku, stejně jako `sequence[sequence.Length]` .</span><span class="sxs-lookup"><span data-stu-id="fcff3-120">Note that `sequence[^0]` does throw an exception, just as `sequence[sequence.Length]` does.</span></span> <span data-ttu-id="fcff3-121">Pro jakékoli číslo `n`je index `^n` stejný jako `sequence[sequence.Length - n]`.</span><span class="sxs-lookup"><span data-stu-id="fcff3-121">For any number `n`, the index `^n` is the same as `sequence[sequence.Length - n]`.</span></span>

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

<span data-ttu-id="fcff3-122">Poslední slovo můžete načíst s `^1` indexem.</span><span class="sxs-lookup"><span data-stu-id="fcff3-122">You can retrieve the last word with the `^1` index.</span></span> <span data-ttu-id="fcff3-123">Pod inicializaci přidejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="fcff3-123">Add the following code below the initialization:</span></span>

[!code-csharp[LastIndex](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_LastIndex)]

<span data-ttu-id="fcff3-124">Rozsah Určuje *začátek* a *konec* rozsahu.</span><span class="sxs-lookup"><span data-stu-id="fcff3-124">A range specifies the *start* and *end* of a range.</span></span> <span data-ttu-id="fcff3-125">Rozsahy jsou exkluzivní, což znamená, že *konec* není zahrnutý v rozsahu.</span><span class="sxs-lookup"><span data-stu-id="fcff3-125">Ranges are exclusive, meaning the *end* is not included in the range.</span></span> <span data-ttu-id="fcff3-126">Rozsah `[0..^0]` představuje celý rozsah, stejně jako `[0..sequence.Length]` představuje celý rozsah.</span><span class="sxs-lookup"><span data-stu-id="fcff3-126">The range `[0..^0]` represents the entire range, just as `[0..sequence.Length]` represents the entire range.</span></span> 

<span data-ttu-id="fcff3-127">Následující kód vytvoří dílčí rozsah s slovy "Rychlá", "hnědá" a "Fox".</span><span class="sxs-lookup"><span data-stu-id="fcff3-127">The following code creates a subrange with the words "quick", "brown", and "fox".</span></span> <span data-ttu-id="fcff3-128">Zahrnuje `words[1]` .`words[3]`</span><span class="sxs-lookup"><span data-stu-id="fcff3-128">It includes `words[1]` through `words[3]`.</span></span> <span data-ttu-id="fcff3-129">Element `words[4]` není v rozsahu.</span><span class="sxs-lookup"><span data-stu-id="fcff3-129">The element `words[4]` isn't in the range.</span></span> <span data-ttu-id="fcff3-130">Do stejné metody přidejte následující kód.</span><span class="sxs-lookup"><span data-stu-id="fcff3-130">Add the following code to the same method.</span></span> <span data-ttu-id="fcff3-131">Zkopírujte ho a vložte ho do dolní části okna interaktivní.</span><span class="sxs-lookup"><span data-stu-id="fcff3-131">Copy and paste it at the bottom of the interactive window.</span></span>

[!code-csharp[Range](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_Range)]

<span data-ttu-id="fcff3-132">Následující kód vytvoří dílčí rozsah s "opožděným" a "pes".</span><span class="sxs-lookup"><span data-stu-id="fcff3-132">The following code creates a subrange with "lazy" and "dog".</span></span> <span data-ttu-id="fcff3-133">Zahrnuje `words[^2]` a .`words[^1]`</span><span class="sxs-lookup"><span data-stu-id="fcff3-133">It includes `words[^2]` and `words[^1]`.</span></span> <span data-ttu-id="fcff3-134">Koncový index `words[^0]` není zahrnutý.</span><span class="sxs-lookup"><span data-stu-id="fcff3-134">The end index `words[^0]` isn't included.</span></span> <span data-ttu-id="fcff3-135">Přidejte také následující kód:</span><span class="sxs-lookup"><span data-stu-id="fcff3-135">Add the following code as well:</span></span>

[!code-csharp[LastRange](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_LastRange)]

<span data-ttu-id="fcff3-136">V následujících příkladech jsou vytvořeny rozsahy, které jsou otevřeny pro začátek, konec nebo obojí:</span><span class="sxs-lookup"><span data-stu-id="fcff3-136">The following examples create ranges that are open ended for the start, end, or both:</span></span>

[!code-csharp[PartialRange](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_PartialRanges)]

<span data-ttu-id="fcff3-137">Můžete také deklarovat rozsahy nebo indexy jako proměnné.</span><span class="sxs-lookup"><span data-stu-id="fcff3-137">You can also declare ranges or indices as variables.</span></span> <span data-ttu-id="fcff3-138">Proměnná se pak dá použít uvnitř `[` znaků a: `]`</span><span class="sxs-lookup"><span data-stu-id="fcff3-138">The variable can then be used inside the `[` and `]` characters:</span></span>

[!code-csharp[IndexRangeTypes](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_RangeIndexTypes)]

<span data-ttu-id="fcff3-139">Následující příklad znázorňuje mnoho z důvodů pro tyto volby.</span><span class="sxs-lookup"><span data-stu-id="fcff3-139">The following sample shows many of the reasons for those choices.</span></span> <span data-ttu-id="fcff3-140">Upravte `x`, `y`a a`z` vyzkoušejte různé kombinace.</span><span class="sxs-lookup"><span data-stu-id="fcff3-140">Modify `x`, `y`, and `z` to try different combinations.</span></span> <span data-ttu-id="fcff3-141">Při experimentování `x` použijte hodnoty, kde je menší než `y`a `y` je menší než `z` pro platné kombinace.</span><span class="sxs-lookup"><span data-stu-id="fcff3-141">When you experiment, use values where `x` is less than `y`, and `y` is less than `z` for valid combinations.</span></span> <span data-ttu-id="fcff3-142">Do nové metody přidejte následující kód.</span><span class="sxs-lookup"><span data-stu-id="fcff3-142">Add the following code in a new method.</span></span> <span data-ttu-id="fcff3-143">Vyzkoušejte různé kombinace:</span><span class="sxs-lookup"><span data-stu-id="fcff3-143">Try different combinations:</span></span>

[!code-csharp[SemanticsExamples](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_Semantics)]

## <a name="scenarios-for-indices-and-ranges"></a><span data-ttu-id="fcff3-144">Scénáře pro indexy a rozsahy</span><span class="sxs-lookup"><span data-stu-id="fcff3-144">Scenarios for Indices and Ranges</span></span>

<span data-ttu-id="fcff3-145">Pokud chcete provést analýzu v podrozsahu celé sekvence, často použijete rozsahy a indexy.</span><span class="sxs-lookup"><span data-stu-id="fcff3-145">You'll often use ranges and indices when you want to perform some analysis on subrange of an entire sequence.</span></span> <span data-ttu-id="fcff3-146">Nová syntaxe je jasná při čtení přesně z toho, co je dílčí rozsah zahrnutý.</span><span class="sxs-lookup"><span data-stu-id="fcff3-146">The new syntax is clearer in reading exactly what subrange is involved.</span></span> <span data-ttu-id="fcff3-147">Místní funkce `MovingAverage` <xref:System.Range> přijímá jako svůj argument.</span><span class="sxs-lookup"><span data-stu-id="fcff3-147">The local function `MovingAverage` takes a <xref:System.Range> as its argument.</span></span> <span data-ttu-id="fcff3-148">Metoda pak při výpočtu minimálních, maximálních a průměrů vytvoří výčet pouze tohoto rozsahu.</span><span class="sxs-lookup"><span data-stu-id="fcff3-148">The method then enumerates just that range when calculating the min, max, and average.</span></span> <span data-ttu-id="fcff3-149">Vyzkoušejte následující kód v projektu:</span><span class="sxs-lookup"><span data-stu-id="fcff3-149">Try the following code in your project:</span></span>

[!code-csharp[MovingAverages](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_MovingAverage)]

<span data-ttu-id="fcff3-150">Dokončený kód si můžete stáhnout z úložiště [dotnet/Samples](https://github.com/dotnet/samples/tree/master/csharp/tutorials/RangesIndexes) .</span><span class="sxs-lookup"><span data-stu-id="fcff3-150">You can download the completed code from the [dotnet/samples](https://github.com/dotnet/samples/tree/master/csharp/tutorials/RangesIndexes) repository.</span></span>
