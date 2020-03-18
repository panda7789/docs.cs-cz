---
title: Prozkoumejte rozsahy dat pomocí indexů a rozsahů
description: Tento pokročilý kurz vás naučí prozkoumat data pomocí indexů a rozsahů a prozkoumat řezy sekvenční datové sady.
ms.date: 03/11/2020
ms.technology: csharp-fundamentals
ms.custom: mvc
ms.openlocfilehash: 82aad968e2efc437c82a7c8250bcd108b60b09e1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79156491"
---
# <a name="indices-and-ranges"></a><span data-ttu-id="61c9e-103">Indexy a rozsahy</span><span class="sxs-lookup"><span data-stu-id="61c9e-103">Indices and ranges</span></span>

<span data-ttu-id="61c9e-104">Rozsahy a indexy poskytují stručnou syntaxi pro přístup k jednotlivým prvkům nebo rozsahům v sekvenci.</span><span class="sxs-lookup"><span data-stu-id="61c9e-104">Ranges and indices provide a succinct syntax for accessing single elements or ranges in a sequence.</span></span>

<span data-ttu-id="61c9e-105">V tomto kurzu se naučíte:</span><span class="sxs-lookup"><span data-stu-id="61c9e-105">In this tutorial, you'll learn how to:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="61c9e-106">Syntaxe pro oblasti v sekvenci použijte.</span><span class="sxs-lookup"><span data-stu-id="61c9e-106">Use the syntax for ranges in a sequence.</span></span>
> - <span data-ttu-id="61c9e-107">Seznamte se s rozhodnutími o návrhu pro začátek a konec každé sekvence.</span><span class="sxs-lookup"><span data-stu-id="61c9e-107">Understand the design decisions for the start and end of each sequence.</span></span>
> - <span data-ttu-id="61c9e-108">Seznamte se <xref:System.Index> <xref:System.Range> se scénáři pro a typy.</span><span class="sxs-lookup"><span data-stu-id="61c9e-108">Learn scenarios for the <xref:System.Index> and <xref:System.Range> types.</span></span>

## <a name="language-support-for-indices-and-ranges"></a><span data-ttu-id="61c9e-109">Jazyková podpora indexů a rozsahů</span><span class="sxs-lookup"><span data-stu-id="61c9e-109">Language support for indices and ranges</span></span>

<span data-ttu-id="61c9e-110">Tato jazyková podpora se opírá o dva nové typy a dva nové operátory:</span><span class="sxs-lookup"><span data-stu-id="61c9e-110">This language support relies on two new types and two new operators:</span></span>

- <span data-ttu-id="61c9e-111"><xref:System.Index?displayProperty=nameWithType>představuje index do sekvence.</span><span class="sxs-lookup"><span data-stu-id="61c9e-111"><xref:System.Index?displayProperty=nameWithType> represents an index into a sequence.</span></span>
- <span data-ttu-id="61c9e-112">Index z koncového operátoru `^`, který určuje, že index je relativní ke konci sekvence.</span><span class="sxs-lookup"><span data-stu-id="61c9e-112">The index from end operator `^`, which specifies that an index is relative to the end of a sequence.</span></span>
- <span data-ttu-id="61c9e-113"><xref:System.Range?displayProperty=nameWithType>představuje dílčí rozsah sekvence.</span><span class="sxs-lookup"><span data-stu-id="61c9e-113"><xref:System.Range?displayProperty=nameWithType> represents a sub range of a sequence.</span></span>
- <span data-ttu-id="61c9e-114">Operátor `..`rozsahu , který určuje začátek a konec rozsahu jako jeho operandy.</span><span class="sxs-lookup"><span data-stu-id="61c9e-114">The range operator `..`, which specifies the start and end of a range as its operands.</span></span>

<span data-ttu-id="61c9e-115">Začněme s pravidly pro indexy.</span><span class="sxs-lookup"><span data-stu-id="61c9e-115">Let's start with the rules for indices.</span></span> <span data-ttu-id="61c9e-116">Zvažte `sequence`pole .</span><span class="sxs-lookup"><span data-stu-id="61c9e-116">Consider an array `sequence`.</span></span> <span data-ttu-id="61c9e-117">Index `0` je stejný `sequence[0]`jako .</span><span class="sxs-lookup"><span data-stu-id="61c9e-117">The `0` index is the same as `sequence[0]`.</span></span> <span data-ttu-id="61c9e-118">Index `^0` je stejný `sequence[sequence.Length]`jako .</span><span class="sxs-lookup"><span data-stu-id="61c9e-118">The `^0` index is the same as `sequence[sequence.Length]`.</span></span> <span data-ttu-id="61c9e-119">Výraz `sequence[^0]` vyvolat výjimku, stejně jako `sequence[sequence.Length]` dělá.</span><span class="sxs-lookup"><span data-stu-id="61c9e-119">The expression `sequence[^0]` does throw an exception, just as `sequence[sequence.Length]` does.</span></span> <span data-ttu-id="61c9e-120">Pro libovolné `n`číslo `^n` je index `sequence[sequence.Length - n]`stejný jako .</span><span class="sxs-lookup"><span data-stu-id="61c9e-120">For any number `n`, the index `^n` is the same as `sequence[sequence.Length - n]`.</span></span>

```csharp
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

<span data-ttu-id="61c9e-121">Můžete načíst poslední slovo `^1` s indexem.</span><span class="sxs-lookup"><span data-stu-id="61c9e-121">You can retrieve the last word with the `^1` index.</span></span> <span data-ttu-id="61c9e-122">Pod inicializaci přidejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="61c9e-122">Add the following code below the initialization:</span></span>

[!code-csharp[LastIndex](~/samples/snippets/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_LastIndex)]

<span data-ttu-id="61c9e-123">Rozsah určuje *začátek* *a* konec rozsahu.</span><span class="sxs-lookup"><span data-stu-id="61c9e-123">A range specifies the *start* and *end* of a range.</span></span> <span data-ttu-id="61c9e-124">Rozsahy jsou exkluzivní, což znamená, že *konec* není součástí rozsahu.</span><span class="sxs-lookup"><span data-stu-id="61c9e-124">Ranges are exclusive, meaning the *end* isn't included in the range.</span></span> <span data-ttu-id="61c9e-125">Rozsah `[0..^0]` představuje celý rozsah, `[0..sequence.Length]` stejně jako představuje celý rozsah.</span><span class="sxs-lookup"><span data-stu-id="61c9e-125">The range `[0..^0]` represents the entire range, just as `[0..sequence.Length]` represents the entire range.</span></span>

<span data-ttu-id="61c9e-126">Následující kód vytvoří podrozsah se slovy "quick", "brown" a "fox".</span><span class="sxs-lookup"><span data-stu-id="61c9e-126">The following code creates a subrange with the words "quick", "brown", and "fox".</span></span> <span data-ttu-id="61c9e-127">To `words[1]` zahrnuje `words[3]`prostřednictvím .</span><span class="sxs-lookup"><span data-stu-id="61c9e-127">It includes `words[1]` through `words[3]`.</span></span> <span data-ttu-id="61c9e-128">Prvek `words[4]` není v rozsahu.</span><span class="sxs-lookup"><span data-stu-id="61c9e-128">The element `words[4]` isn't in the range.</span></span> <span data-ttu-id="61c9e-129">Přidejte následující kód ke stejné metodě.</span><span class="sxs-lookup"><span data-stu-id="61c9e-129">Add the following code to the same method.</span></span> <span data-ttu-id="61c9e-130">Zkopírujte a vložte jej do dolní části interaktivního okna.</span><span class="sxs-lookup"><span data-stu-id="61c9e-130">Copy and paste it at the bottom of the interactive window.</span></span>

[!code-csharp[Range](~/samples/snippets/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_Range)]

<span data-ttu-id="61c9e-131">Následující kód vytvoří podrozsah s "líný" a "pes".</span><span class="sxs-lookup"><span data-stu-id="61c9e-131">The following code creates a subrange with "lazy" and "dog".</span></span> <span data-ttu-id="61c9e-132">To `words[^2]` zahrnuje `words[^1]`a .</span><span class="sxs-lookup"><span data-stu-id="61c9e-132">It includes `words[^2]` and `words[^1]`.</span></span> <span data-ttu-id="61c9e-133">Koncový index `words[^0]` není zahrnut.</span><span class="sxs-lookup"><span data-stu-id="61c9e-133">The end index `words[^0]` isn't included.</span></span> <span data-ttu-id="61c9e-134">Přidejte také následující kód:</span><span class="sxs-lookup"><span data-stu-id="61c9e-134">Add the following code as well:</span></span>

[!code-csharp[LastRange](~/samples/snippets/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_LastRange)]

<span data-ttu-id="61c9e-135">Následující příklady vytvářejí oblasti, které jsou otevřené pro začátek, konec nebo obojí:</span><span class="sxs-lookup"><span data-stu-id="61c9e-135">The following examples create ranges that are open ended for the start, end, or both:</span></span>

[!code-csharp[PartialRange](~/samples/snippets/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_PartialRanges)]

<span data-ttu-id="61c9e-136">Rozsahy nebo indexy můžete také deklarovat jako proměnné.</span><span class="sxs-lookup"><span data-stu-id="61c9e-136">You can also declare ranges or indices as variables.</span></span> <span data-ttu-id="61c9e-137">Proměnnou lze pak použít `[` `]` uvnitř znaků a:</span><span class="sxs-lookup"><span data-stu-id="61c9e-137">The variable can then be used inside the `[` and `]` characters:</span></span>

[!code-csharp[IndexRangeTypes](~/samples/snippets/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_RangeIndexTypes)]

<span data-ttu-id="61c9e-138">Následující příklad ukazuje mnoho důvodů pro tyto volby.</span><span class="sxs-lookup"><span data-stu-id="61c9e-138">The following sample shows many of the reasons for those choices.</span></span> <span data-ttu-id="61c9e-139">`x`Upravte `y`, `z` a vyzkoušejte různé kombinace.</span><span class="sxs-lookup"><span data-stu-id="61c9e-139">Modify `x`, `y`, and `z` to try different combinations.</span></span> <span data-ttu-id="61c9e-140">Při experimentování použijte `x` hodnoty, `y`kde `y` je menší `z` než , a je menší než pro platné kombinace.</span><span class="sxs-lookup"><span data-stu-id="61c9e-140">When you experiment, use values where `x` is less than `y`, and `y` is less than `z` for valid combinations.</span></span> <span data-ttu-id="61c9e-141">Přidejte následující kód do nové metody.</span><span class="sxs-lookup"><span data-stu-id="61c9e-141">Add the following code in a new method.</span></span> <span data-ttu-id="61c9e-142">Vyzkoušejte různé kombinace:</span><span class="sxs-lookup"><span data-stu-id="61c9e-142">Try different combinations:</span></span>

[!code-csharp[SemanticsExamples](~/samples/snippets/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_Semantics)]

## <a name="type-support-for-indices-and-ranges"></a><span data-ttu-id="61c9e-143">Podpora typů pro indexy a rozsahy</span><span class="sxs-lookup"><span data-stu-id="61c9e-143">Type support for indices and ranges</span></span>

<span data-ttu-id="61c9e-144">Indexy a rozsahy poskytují jasnou, stručnou syntaxi pro přístup k jednomu prvku nebo podoblasti prvků v sekvenci.</span><span class="sxs-lookup"><span data-stu-id="61c9e-144">Indexes and ranges provide clear, concise syntax to access a single element or a subrange of elements in a sequence.</span></span> <span data-ttu-id="61c9e-145">Výraz indexu obvykle vrací typ prvků sekvence.</span><span class="sxs-lookup"><span data-stu-id="61c9e-145">An index expression typically returns the type of the elements of a sequence.</span></span> <span data-ttu-id="61c9e-146">Výraz rozsahu obvykle vrací stejný typ sekvence jako zdrojová sekvence.</span><span class="sxs-lookup"><span data-stu-id="61c9e-146">A range expression typically returns the same sequence type as the source sequence.</span></span>

<span data-ttu-id="61c9e-147">Libovolný typ, který poskytuje [indexeru](../programming-guide/indexers/index.md) s parametrem <xref:System.Index> nebo <xref:System.Range> explicitně podporuje indexy nebo rozsahy.</span><span class="sxs-lookup"><span data-stu-id="61c9e-147">Any type that provides an [indexer](../programming-guide/indexers/index.md) with an <xref:System.Index> or <xref:System.Range> parameter explicitly supports indices or ranges respectively.</span></span> <span data-ttu-id="61c9e-148">Indexer, který přebírá <xref:System.Range> jeden parametr může vrátit jiný <xref:System.Span%601?displayProperty=nameWithType>typ sekvence, například .</span><span class="sxs-lookup"><span data-stu-id="61c9e-148">An indexer that takes a single <xref:System.Range> parameter may return a different sequence type, such as <xref:System.Span%601?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="61c9e-149">Typ je **možné počítat,** pokud `Length` má `Count` vlastnost s názvem nebo s `int`přístupným getter a návratový typ .</span><span class="sxs-lookup"><span data-stu-id="61c9e-149">A type is **countable** if it has a property named `Length` or `Count` with an accessible getter and a return type of `int`.</span></span> <span data-ttu-id="61c9e-150">Počítatelný typ, který explicitně nepodporuje indexy nebo rozsahy, může poskytnout implicitní podporu pro ně.</span><span class="sxs-lookup"><span data-stu-id="61c9e-150">A countable type that doesn't explicitly support indices or ranges may provide an implicit support for them.</span></span> <span data-ttu-id="61c9e-151">Další informace naleznete v části [implicitní index podpory](~/_csharplang/proposals/csharp-8.0/ranges.md#implicit-index-support) a [implicitní rozsah podpory](~/_csharplang/proposals/csharp-8.0/ranges.md#implicit-range-support) poznámky [návrhu funkce](~/_csharplang/proposals/csharp-8.0/ranges.md).</span><span class="sxs-lookup"><span data-stu-id="61c9e-151">For more information, see the [Implicit Index support](~/_csharplang/proposals/csharp-8.0/ranges.md#implicit-index-support) and [Implicit Range support](~/_csharplang/proposals/csharp-8.0/ranges.md#implicit-range-support) sections of the [feature proposal note](~/_csharplang/proposals/csharp-8.0/ranges.md).</span></span> <span data-ttu-id="61c9e-152">Rozsahy používající implicitní podporu rozsahu vrátí stejný typ sekvence jako zdrojová sekvence.</span><span class="sxs-lookup"><span data-stu-id="61c9e-152">Ranges using implicit range support return the same sequence type as the source sequence.</span></span>

<span data-ttu-id="61c9e-153">Například následující typy .NET podporují indexy i <xref:System.String>rozsahy: , <xref:System.Span%601>a <xref:System.ReadOnlySpan%601>.</span><span class="sxs-lookup"><span data-stu-id="61c9e-153">For example, the following .NET types support both indices and ranges: <xref:System.String>, <xref:System.Span%601>, and <xref:System.ReadOnlySpan%601>.</span></span> <span data-ttu-id="61c9e-154">Podporuje <xref:System.Collections.Generic.List%601> indexy, ale nepodporuje rozsahy.</span><span class="sxs-lookup"><span data-stu-id="61c9e-154">The <xref:System.Collections.Generic.List%601> supports indices but doesn't support ranges.</span></span>

<span data-ttu-id="61c9e-155"><xref:System.Array>má více nuancí chování.</span><span class="sxs-lookup"><span data-stu-id="61c9e-155"><xref:System.Array> has more nuanced behavior.</span></span> <span data-ttu-id="61c9e-156">Pole s jednou dimenzí podporují indexy i rozsahy.</span><span class="sxs-lookup"><span data-stu-id="61c9e-156">Single dimension arrays support both indices and ranges.</span></span> <span data-ttu-id="61c9e-157">Vícerozměrná pole ne.</span><span class="sxs-lookup"><span data-stu-id="61c9e-157">Multi-dimensional arrays don't.</span></span> <span data-ttu-id="61c9e-158">Indexer pro vícerozměrné pole má více parametrů, nikoli jeden parametr.</span><span class="sxs-lookup"><span data-stu-id="61c9e-158">The indexer for a multi-dimensional array has multiple parameters, not a single parameter.</span></span> <span data-ttu-id="61c9e-159">Zubatá pole, označovaná také jako pole polí, podporují rozsahy i indexery.</span><span class="sxs-lookup"><span data-stu-id="61c9e-159">Jagged arrays, also referred to as an array of arrays, support both ranges and indexers.</span></span> <span data-ttu-id="61c9e-160">Následující příklad ukazuje, jak iterat obdélníkové podsekce zubaté pole.</span><span class="sxs-lookup"><span data-stu-id="61c9e-160">The following example shows how to iterate a rectangular subsection of a jagged array.</span></span> <span data-ttu-id="61c9e-161">Itetuje řez uprostřed, s výjimkou prvního a posledního tří řádků a prvnía poslední dva sloupce z každého vybraného řádku:</span><span class="sxs-lookup"><span data-stu-id="61c9e-161">It iterates the section in the center, excluding the first and last three rows, and the first and last two columns from each selected row:</span></span>

[!code-csharp[JaggedArrays](~/samples/snippets/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_JaggedArrays)]

## <a name="scenarios-for-indices-and-ranges"></a><span data-ttu-id="61c9e-162">Scénáře pro indexy a rozsahy</span><span class="sxs-lookup"><span data-stu-id="61c9e-162">Scenarios for indices and ranges</span></span>

<span data-ttu-id="61c9e-163">Často budete používat rozsahy a indexy, pokud chcete analyzovat podrozsah větší sekvence.</span><span class="sxs-lookup"><span data-stu-id="61c9e-163">You'll often use ranges and indices when you want to analyze a subrange of a larger sequence.</span></span> <span data-ttu-id="61c9e-164">Nová syntaxe je jasnější při čtení přesně to, co podrozsah se jedná.</span><span class="sxs-lookup"><span data-stu-id="61c9e-164">The new syntax is clearer in reading exactly what subrange is involved.</span></span> <span data-ttu-id="61c9e-165">Místní funkce `MovingAverage` bere <xref:System.Range> jako jeho argument.</span><span class="sxs-lookup"><span data-stu-id="61c9e-165">The local function `MovingAverage` takes a <xref:System.Range> as its argument.</span></span> <span data-ttu-id="61c9e-166">Metoda pak vyjmenovává právě tento rozsah při výpočtu min, max a průměr.</span><span class="sxs-lookup"><span data-stu-id="61c9e-166">The method then enumerates just that range when calculating the min, max, and average.</span></span> <span data-ttu-id="61c9e-167">Zkuste v projektu následující kód:</span><span class="sxs-lookup"><span data-stu-id="61c9e-167">Try the following code in your project:</span></span>

[!code-csharp[MovingAverages](~/samples/snippets/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_MovingAverage)]
