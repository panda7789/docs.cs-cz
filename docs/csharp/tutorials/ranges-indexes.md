---
title: Prozkoumejte rozsahy dat pomocí indexů a rozsahy
description: Tato pokročilé kurzu se naučíte zkoumat data pomocí indexy a oblastí k prozkoumání řezy sekvenční datových sad.
ms.date: 04/19/2019
ms.custom: mvc
ms.openlocfilehash: 118d3c9ccad98ec02195c2b5e26a2ca203990adf
ms.sourcegitcommit: 682c64df0322c7bda016f8bfea8954e9b31f1990
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/13/2019
ms.locfileid: "65557189"
---
# <a name="indices-and-ranges"></a><span data-ttu-id="edc5d-103">Indexy a rozsahy</span><span class="sxs-lookup"><span data-stu-id="edc5d-103">Indices and ranges</span></span>

<span data-ttu-id="edc5d-104">Rozsahy a indexy poskytují stručné syntaxe pro přístup k jednotlivé prvky nebo oblasti <xref:System.Array>, <xref:System.Span%601>, nebo <xref:System.ReadOnlySpan%601>.</span><span class="sxs-lookup"><span data-stu-id="edc5d-104">Ranges and indices provide a succinct syntax for accessing single elements or ranges in an <xref:System.Array>, <xref:System.Span%601>, or <xref:System.ReadOnlySpan%601>.</span></span> <span data-ttu-id="edc5d-105">Tyto funkce umožňují přesnější, zrušte zaškrtnutí políčka syntaxi k přístupu k jednotlivé prvky nebo rozsah prvků v posloupnosti.</span><span class="sxs-lookup"><span data-stu-id="edc5d-105">These features enable more concise, clear syntax to access single elements or ranges of elements in a sequence.</span></span>

<span data-ttu-id="edc5d-106">V tomto kurzu se dozvíte jak:</span><span class="sxs-lookup"><span data-stu-id="edc5d-106">In this tutorial, you'll learn how to:</span></span>

> [!div class="checklist"]
> * <span data-ttu-id="edc5d-107">U rozsahů v pořadí použijte syntaxi.</span><span class="sxs-lookup"><span data-stu-id="edc5d-107">Use the syntax for ranges in a sequence.</span></span>
> * <span data-ttu-id="edc5d-108">Seznamte se s rozhodnutí o návrhu pro začátku a konce každého pořadí.</span><span class="sxs-lookup"><span data-stu-id="edc5d-108">Understand the design decisions for the start and end of each sequence.</span></span>
> * <span data-ttu-id="edc5d-109">Další scénáře pro <xref:System.Index> a <xref:System.Range> typy.</span><span class="sxs-lookup"><span data-stu-id="edc5d-109">Learn scenarios for the <xref:System.Index> and <xref:System.Range> types.</span></span>

## <a name="language-support-for-indices-and-ranges"></a><span data-ttu-id="edc5d-110">Podpora jazyků pro rozsahy a indexy</span><span class="sxs-lookup"><span data-stu-id="edc5d-110">Language support for indices and ranges</span></span>

<span data-ttu-id="edc5d-111">Tato podpora jazyka spoléhá na dva nové typy a dvou nových operátorů.</span><span class="sxs-lookup"><span data-stu-id="edc5d-111">This language support relies on two new types and two new operators.</span></span>
- <span data-ttu-id="edc5d-112"><xref:System.Index?displayProperty=nameWithType> představuje index na sekvenci.</span><span class="sxs-lookup"><span data-stu-id="edc5d-112"><xref:System.Index?displayProperty=nameWithType> represents an index into a sequence.</span></span>
- <span data-ttu-id="edc5d-113">`^` Operátor, který určuje, že je index vzhledem ke konci sekvence.</span><span class="sxs-lookup"><span data-stu-id="edc5d-113">The `^` operator, which specifies that an index is relative to the end of a sequence.</span></span>
- <span data-ttu-id="edc5d-114"><xref:System.Range?displayProperty=nameWithType> představuje rozsah dílčí sekvenci.</span><span class="sxs-lookup"><span data-stu-id="edc5d-114"><xref:System.Range?displayProperty=nameWithType> represents a sub range of a sequence.</span></span>
- <span data-ttu-id="edc5d-115">Operátor rozsahu (`..`), který určuje jeho operandy počáteční a koncová hodnota rozsahu.</span><span class="sxs-lookup"><span data-stu-id="edc5d-115">The Range operator (`..`), which specifies the start and end of a range as its operands.</span></span>

<span data-ttu-id="edc5d-116">Začněme s pravidly pro indexy.</span><span class="sxs-lookup"><span data-stu-id="edc5d-116">Let's start with the rules for indices.</span></span> <span data-ttu-id="edc5d-117">Vezměte v úvahu pole `sequence`.</span><span class="sxs-lookup"><span data-stu-id="edc5d-117">Consider an array `sequence`.</span></span> <span data-ttu-id="edc5d-118">`0` Index je stejný jako `sequence[0]`.</span><span class="sxs-lookup"><span data-stu-id="edc5d-118">The `0` index is the same as `sequence[0]`.</span></span> <span data-ttu-id="edc5d-119">`^0` Index je stejný jako `sequence[sequence.Length]`.</span><span class="sxs-lookup"><span data-stu-id="edc5d-119">The `^0` index is the same as `sequence[sequence.Length]`.</span></span> <span data-ttu-id="edc5d-120">Všimněte si, že `sequence[^0]` vyvolá výjimku, stejně jako `sequence[sequence.Length]` nepodporuje.</span><span class="sxs-lookup"><span data-stu-id="edc5d-120">Note that `sequence[^0]` does throw an exception, just as `sequence[sequence.Length]` does.</span></span> <span data-ttu-id="edc5d-121">Pro libovolný počet `n`, index `^n` je stejný jako `sequence[sequence.Length - n]`.</span><span class="sxs-lookup"><span data-stu-id="edc5d-121">For any number `n`, the index `^n` is the same as `sequence[sequence.Length - n]`.</span></span>

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

<span data-ttu-id="edc5d-122">Můžete načíst poslední slovo s `^1` indexu.</span><span class="sxs-lookup"><span data-stu-id="edc5d-122">You can retrieve the last word with the `^1` index.</span></span> <span data-ttu-id="edc5d-123">Přidejte následující kód pod inicializace:</span><span class="sxs-lookup"><span data-stu-id="edc5d-123">Add the following code below the initialization:</span></span>

[!code-csharp[LastIndex](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_LastIndex)]

<span data-ttu-id="edc5d-124">Určuje oblast *start* a *koncové* rozsahu.</span><span class="sxs-lookup"><span data-stu-id="edc5d-124">A range specifies the *start* and *end* of a range.</span></span> <span data-ttu-id="edc5d-125">Rozsahy jsou výhradní, to znamená *end* není zahrnutý v rozsahu.</span><span class="sxs-lookup"><span data-stu-id="edc5d-125">Ranges are exclusive, meaning the *end* is not included in the range.</span></span> <span data-ttu-id="edc5d-126">Rozsah `[0..^0]` představuje celou oblast, stejně jako `[0..sequence.Length]` představuje celou oblast.</span><span class="sxs-lookup"><span data-stu-id="edc5d-126">The range `[0..^0]` represents the entire range, just as `[0..sequence.Length]` represents the entire range.</span></span> 

<span data-ttu-id="edc5d-127">Následující kód vytvoří podrozsahu s slova "rychlé", "brown" a "fox".</span><span class="sxs-lookup"><span data-stu-id="edc5d-127">The following code creates a subrange with the words "quick", "brown", and "fox".</span></span> <span data-ttu-id="edc5d-128">Zahrnuje `words[1]` prostřednictvím `words[3]`.</span><span class="sxs-lookup"><span data-stu-id="edc5d-128">It includes `words[1]` through `words[3]`.</span></span> <span data-ttu-id="edc5d-129">Element `words[4]` není v rozsahu.</span><span class="sxs-lookup"><span data-stu-id="edc5d-129">The element `words[4]` isn't in the range.</span></span> <span data-ttu-id="edc5d-130">Přidejte následující kód k metodě stejné.</span><span class="sxs-lookup"><span data-stu-id="edc5d-130">Add the following code to the same method.</span></span> <span data-ttu-id="edc5d-131">Zkopírujte a vložte ji dole v interaktivním okně.</span><span class="sxs-lookup"><span data-stu-id="edc5d-131">Copy and paste it at the bottom of the interactive window.</span></span>

[!code-csharp[Range](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_Range)]

<span data-ttu-id="edc5d-132">Následující kód vytvoří podrozsahu "opožděné" a "pes".</span><span class="sxs-lookup"><span data-stu-id="edc5d-132">The following code creates a subrange with "lazy" and "dog".</span></span> <span data-ttu-id="edc5d-133">Zahrnuje `words[^2]` a `words[^1]`.</span><span class="sxs-lookup"><span data-stu-id="edc5d-133">It includes `words[^2]` and `words[^1]`.</span></span> <span data-ttu-id="edc5d-134">Koncová hodnota `words[^0]` není zahrnut.</span><span class="sxs-lookup"><span data-stu-id="edc5d-134">The end index `words[^0]` isn't included.</span></span> <span data-ttu-id="edc5d-135">Přidejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="edc5d-135">Add the following code as well:</span></span>

[!code-csharp[LastRange](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_LastRange)]

<span data-ttu-id="edc5d-136">Následující příklady vytváří rozsahy, které jsou otevřené skončila pro zahájení a ukončení:</span><span class="sxs-lookup"><span data-stu-id="edc5d-136">The following examples create ranges that are open ended for the start, end, or both:</span></span>

[!code-csharp[PartialRange](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_PartialRanges)]

<span data-ttu-id="edc5d-137">Rozsahy nebo indexy můžete také deklarovat jako proměnné.</span><span class="sxs-lookup"><span data-stu-id="edc5d-137">You can also declare ranges or indices as variables.</span></span> <span data-ttu-id="edc5d-138">Proměnná je pak možné uvnitř `[` a `]` znaků:</span><span class="sxs-lookup"><span data-stu-id="edc5d-138">The variable can then be used inside the `[` and `]` characters:</span></span>

[!code-csharp[IndexRangeTypes](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_RangeIndexTypes)]

<span data-ttu-id="edc5d-139">Následující příklad ukazuje mnoho důvodů těchto možností.</span><span class="sxs-lookup"><span data-stu-id="edc5d-139">The following sample shows many of the reasons for those choices.</span></span> <span data-ttu-id="edc5d-140">Upravit `x`, `y`, a `z` vyzkoušet různé kombinace.</span><span class="sxs-lookup"><span data-stu-id="edc5d-140">Modify `x`, `y`, and `z` to try different combinations.</span></span> <span data-ttu-id="edc5d-141">Když můžete experimentovat, použijte hodnoty, kde `x` je menší než `y`, a `y` je menší než `z` pro platné kombinace.</span><span class="sxs-lookup"><span data-stu-id="edc5d-141">When you experiment, use values where `x` is less than `y`, and `y` is less than `z` for valid combinations.</span></span> <span data-ttu-id="edc5d-142">Přidejte následující kód do nové metody.</span><span class="sxs-lookup"><span data-stu-id="edc5d-142">Add the following code in a new method.</span></span> <span data-ttu-id="edc5d-143">Zkuste použijte různé kombinace:</span><span class="sxs-lookup"><span data-stu-id="edc5d-143">Try different combinations:</span></span>

[!code-csharp[SemanticsExamples](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_Semantics)]

## <a name="scenarios-for-indices-and-ranges"></a><span data-ttu-id="edc5d-144">Scénáře pro rozsahy a indexy</span><span class="sxs-lookup"><span data-stu-id="edc5d-144">Scenarios for Indices and Ranges</span></span>

<span data-ttu-id="edc5d-145">Pokud chcete provádět některé analýzy podrozsahu celé sekvenci, budete používat často rozsahy a indexy.</span><span class="sxs-lookup"><span data-stu-id="edc5d-145">You'll often use ranges and indices when you want to perform some analysis on subrange of an entire sequence.</span></span> <span data-ttu-id="edc5d-146">Nová syntaxe je jasnější v přesně je zahrnuta jaké podrozsahu pro čtení.</span><span class="sxs-lookup"><span data-stu-id="edc5d-146">The new syntax is clearer in reading exactly what subrange is involved.</span></span> <span data-ttu-id="edc5d-147">Lokální funkce `MovingAverage` přijímá <xref:System.Range> jako svůj argument.</span><span class="sxs-lookup"><span data-stu-id="edc5d-147">The local function `MovingAverage` takes a <xref:System.Range> as its argument.</span></span> <span data-ttu-id="edc5d-148">Metoda pak vytvoří výčet právě tento rozsah při výpočtu min, max a průměr.</span><span class="sxs-lookup"><span data-stu-id="edc5d-148">The method then enumerates just that range when calculating the min, max, and average.</span></span> <span data-ttu-id="edc5d-149">Vyzkoušejte následující kód ve vašem projektu:</span><span class="sxs-lookup"><span data-stu-id="edc5d-149">Try the following code in your project:</span></span>

[!code-csharp[MovingAverages](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_MovingAverage)]

<span data-ttu-id="edc5d-150">Můžete stáhnout Dokončený kód z [dotnet/samples](https://github.com/dotnet/samples/tree/master/csharp/tutorials/RangesIndexes) úložiště.</span><span class="sxs-lookup"><span data-stu-id="edc5d-150">You can download the completed code from the [dotnet/samples](https://github.com/dotnet/samples/tree/master/csharp/tutorials/RangesIndexes) repository.</span></span>
