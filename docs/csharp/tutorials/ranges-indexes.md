---
title: Prozkoumejte rozsahy dat pomocí indexů a rozsahy
description: Tato pokročilé kurzu se naučíte zkoumat data pomocí indexy a oblastí k prozkoumání řezy sekvenční datových sad.
ms.date: 04/19/2019
ms.custom: mvc
ms.openlocfilehash: 64fae4581e265d4f70b8356d5c651b4fdaca3fe9
ms.sourcegitcommit: dd3b897feb5c4ac39732bb165848e37a344b0765
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/25/2019
ms.locfileid: "64431488"
---
# <a name="indices-and-ranges"></a><span data-ttu-id="ea863-103">Indexy a rozsahy</span><span class="sxs-lookup"><span data-stu-id="ea863-103">Indices and ranges</span></span>

<span data-ttu-id="ea863-104">Rozsahy a indexy poskytují stručné syntaxe pro přístup k jednotlivé prvky nebo oblasti <xref:System.Array>, <xref:System.Span%601>, nebo <xref:System.ReadOnlySpan%601>.</span><span class="sxs-lookup"><span data-stu-id="ea863-104">Ranges and indices provide a succinct syntax for accessing single elements or ranges in an <xref:System.Array>, <xref:System.Span%601>, or <xref:System.ReadOnlySpan%601>.</span></span> <span data-ttu-id="ea863-105">Tyto funkce umožňují přesnější, zrušte zaškrtnutí políčka syntaxi k přístupu k jednotlivé prvky nebo rozsah prvků v posloupnosti.</span><span class="sxs-lookup"><span data-stu-id="ea863-105">These features enable more concise, clear syntax to access single elements or ranges of elements in a sequence.</span></span>

<span data-ttu-id="ea863-106">V tomto kurzu se dozvíte jak:</span><span class="sxs-lookup"><span data-stu-id="ea863-106">In this tutorial, you'll learn how to:</span></span>

> [!div class="checklist"]
> * <span data-ttu-id="ea863-107">U rozsahů v pořadí použijte syntaxi.</span><span class="sxs-lookup"><span data-stu-id="ea863-107">Use the syntax for ranges in a sequence.</span></span>
> * <span data-ttu-id="ea863-108">Seznamte se s rozhodnutí o návrhu pro začátku a konce každého pořadí.</span><span class="sxs-lookup"><span data-stu-id="ea863-108">Understand the design decisions for the start and end of each sequence.</span></span>
> * <span data-ttu-id="ea863-109">Další scénáře pro <xref:System.Index> a <xref:System.Range> typy.</span><span class="sxs-lookup"><span data-stu-id="ea863-109">Learn scenarios for the <xref:System.Index> and <xref:System.Range> types.</span></span>

## <a name="language-support-for-indices-and-ranges"></a><span data-ttu-id="ea863-110">Podpora jazyků pro rozsahy a indexy</span><span class="sxs-lookup"><span data-stu-id="ea863-110">Language support for indices and ranges</span></span>

<span data-ttu-id="ea863-111">Můžete určit index **od konce** pomocí `^` znak před index.</span><span class="sxs-lookup"><span data-stu-id="ea863-111">You can specify an index **from the end** using the `^` character before the index.</span></span> <span data-ttu-id="ea863-112">Indexování od konce spustí z pravidla, která `0..^0` Určuje celou oblast.</span><span class="sxs-lookup"><span data-stu-id="ea863-112">Indexing from the end starts from the rule that `0..^0` specifies the entire range.</span></span> <span data-ttu-id="ea863-113">K výpisu obsahu celého pole začnete *na první prvek*a pokračovat, dokud se *místo za posledním prvkem*.</span><span class="sxs-lookup"><span data-stu-id="ea863-113">To enumerate an entire array, you start *at the first element*, and continue until you are *past the last element*.</span></span> <span data-ttu-id="ea863-114">Představte si, že chování `MoveNext` metodu na enumerátor: vrátí hodnotu false v případě úspěšného posledním prvkem výčtu.</span><span class="sxs-lookup"><span data-stu-id="ea863-114">Think of the behavior of the `MoveNext` method on an enumerator: it returns false when the enumeration passes the last element.</span></span> <span data-ttu-id="ea863-115">Index `^0` znamená "end" `array[array.Length]`, nebo index, který následuje po posledním prvku.</span><span class="sxs-lookup"><span data-stu-id="ea863-115">The index `^0` means "the end", `array[array.Length]`, or the index that follows the last element.</span></span> <span data-ttu-id="ea863-116">Jste obeznámeni s `array[2]` znamená elementu "2 od samého začátku".</span><span class="sxs-lookup"><span data-stu-id="ea863-116">You are familiar with `array[2]` meaning the element "2 from the start".</span></span> <span data-ttu-id="ea863-117">Nyní `array[^2]` znamená, že element "2 od konce".</span><span class="sxs-lookup"><span data-stu-id="ea863-117">Now, `array[^2]` means the element "2 from the end".</span></span> 

<span data-ttu-id="ea863-118">Můžete zadat **rozsah** s **operátor rozsahu**: `..`.</span><span class="sxs-lookup"><span data-stu-id="ea863-118">You can specify a **range** with the **range operator**: `..`.</span></span> <span data-ttu-id="ea863-119">Například `0..^0` určuje celý rozsah pole: 0 od začátku až do, s výjimkou 0 od konce.</span><span class="sxs-lookup"><span data-stu-id="ea863-119">For example, `0..^0` specifies the entire range of the array: 0 from the start up to, but not including 0 from the end.</span></span> <span data-ttu-id="ea863-120">Jeden z operandů může používat "z start" nebo "end".</span><span class="sxs-lookup"><span data-stu-id="ea863-120">Either operand may use "from the start" or "from the end".</span></span> <span data-ttu-id="ea863-121">Kromě toho může vynechat jeden z operandů.</span><span class="sxs-lookup"><span data-stu-id="ea863-121">Furthermore, either operand may be omitted.</span></span> <span data-ttu-id="ea863-122">Výchozí hodnoty jsou `0` pro počáteční index a `^0` end indexu.</span><span class="sxs-lookup"><span data-stu-id="ea863-122">The defaults are `0` for the start index, and `^0` for the end index.</span></span>

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

<span data-ttu-id="ea863-123">Pojem "od začátku" a "z"konec posiluje indexu každého prvku, a rozsahy adres jsou uvedeny bez konec rozsahu.</span><span class="sxs-lookup"><span data-stu-id="ea863-123">The index of each element reinforces the concept of "from the start", and "from the end", and that ranges are exclusive of the end of the range.</span></span> <span data-ttu-id="ea863-124">"Start" celého pole je první prvek.</span><span class="sxs-lookup"><span data-stu-id="ea863-124">The "start" of the entire array is the first element.</span></span> <span data-ttu-id="ea863-125">"End" celého pole *minulosti* poslední prvek.</span><span class="sxs-lookup"><span data-stu-id="ea863-125">The "end" of the entire array is *past* the last element.</span></span>

<span data-ttu-id="ea863-126">Můžete načíst poslední slovo s `^1` indexu.</span><span class="sxs-lookup"><span data-stu-id="ea863-126">You can retrieve the last word with the `^1` index.</span></span> <span data-ttu-id="ea863-127">Přidejte následující kód pod inicializace:</span><span class="sxs-lookup"><span data-stu-id="ea863-127">Add the following code below the initialization:</span></span>

[!code-csharp[LastIndex](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_LastIndex)]

<span data-ttu-id="ea863-128">Následující kód vytvoří podrozsahu s slova "rychlé", "brown" a "fox".</span><span class="sxs-lookup"><span data-stu-id="ea863-128">The following code creates a subrange with the words "quick", "brown", and "fox".</span></span> <span data-ttu-id="ea863-129">Zahrnuje `words[1]` prostřednictvím `words[3]`.</span><span class="sxs-lookup"><span data-stu-id="ea863-129">It includes `words[1]` through `words[3]`.</span></span> <span data-ttu-id="ea863-130">Element `words[4]` není v rozsahu.</span><span class="sxs-lookup"><span data-stu-id="ea863-130">The element `words[4]` isn't in the range.</span></span> <span data-ttu-id="ea863-131">Přidejte následující kód k metodě stejné.</span><span class="sxs-lookup"><span data-stu-id="ea863-131">Add the following code to the same method.</span></span> <span data-ttu-id="ea863-132">Zkopírujte a vložte ji dole v interaktivním okně.</span><span class="sxs-lookup"><span data-stu-id="ea863-132">Copy and paste it at the bottom of the interactive window.</span></span>

[!code-csharp[Range](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_Range)]

<span data-ttu-id="ea863-133">Následující kód vytvoří podrozsahu "opožděné" a "pes".</span><span class="sxs-lookup"><span data-stu-id="ea863-133">The following code creates a subrange with "lazy" and "dog".</span></span> <span data-ttu-id="ea863-134">Zahrnuje `words[^2]` a `words[^1]`.</span><span class="sxs-lookup"><span data-stu-id="ea863-134">It includes `words[^2]` and `words[^1]`.</span></span> <span data-ttu-id="ea863-135">Koncová hodnota `words[^0]` není zahrnut.</span><span class="sxs-lookup"><span data-stu-id="ea863-135">The end index `words[^0]` isn't included.</span></span> <span data-ttu-id="ea863-136">Přidejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="ea863-136">Add the following code as well:</span></span>

[!code-csharp[LastRange](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_LastRange)]

<span data-ttu-id="ea863-137">Následující příklady vytváří rozsahy, které jsou otevřené skončila pro zahájení a ukončení:</span><span class="sxs-lookup"><span data-stu-id="ea863-137">The following examples create ranges that are open ended for the start, end, or both:</span></span>

[!code-csharp[PartialRange](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_PartialRanges)]

<span data-ttu-id="ea863-138">Rozsahy nebo indexy můžete také deklarovat jako proměnné.</span><span class="sxs-lookup"><span data-stu-id="ea863-138">You can also declare ranges or indices as variables.</span></span> <span data-ttu-id="ea863-139">Proměnná je pak možné uvnitř `[` a `]` znaků:</span><span class="sxs-lookup"><span data-stu-id="ea863-139">The variable can then be used inside the `[` and `]` characters:</span></span>

[!code-csharp[IndexRangeTypes](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_RangeIndexTypes)]

<span data-ttu-id="ea863-140">Předchozí příklady ukazují dvě rozhodnutí o návrhu, které vyžadují další vysvětlení:</span><span class="sxs-lookup"><span data-stu-id="ea863-140">The previous examples show two design decisions that require more explanation:</span></span>

- <span data-ttu-id="ea863-141">Rozsahy jsou *exkluzivní*, tj. element v poslední index není v rozsahu.</span><span class="sxs-lookup"><span data-stu-id="ea863-141">Ranges are *exclusive*, meaning the element at the last index isn't in the range.</span></span>
- <span data-ttu-id="ea863-142">Index `^0` je *konci* kolekce, ne *poslední prvek* v kolekci.</span><span class="sxs-lookup"><span data-stu-id="ea863-142">The index `^0` is *the end* of the collection, not *the last element* in the collection.</span></span>

<span data-ttu-id="ea863-143">Následující příklad ukazuje mnoho důvodů těchto možností.</span><span class="sxs-lookup"><span data-stu-id="ea863-143">The following sample shows many of the reasons for those choices.</span></span> <span data-ttu-id="ea863-144">Upravit `x`, `y`, a `z` vyzkoušet různé kombinace.</span><span class="sxs-lookup"><span data-stu-id="ea863-144">Modify `x`, `y`, and `z` to try different combinations.</span></span> <span data-ttu-id="ea863-145">Když můžete experimentovat, použijte hodnoty, kde `x` je menší než `y`, a `y` je menší než `z` pro platné kombinace.</span><span class="sxs-lookup"><span data-stu-id="ea863-145">When you experiment, use values where `x` is less than `y`, and `y` is less than `z` for valid combinations.</span></span> <span data-ttu-id="ea863-146">Přidejte následující kód do nové metody.</span><span class="sxs-lookup"><span data-stu-id="ea863-146">Add the following code in a new method.</span></span> <span data-ttu-id="ea863-147">Zkuste použijte různé kombinace:</span><span class="sxs-lookup"><span data-stu-id="ea863-147">Try different combinations:</span></span>

[!code-csharp[SemanticsExamples](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_Semantics)]

## <a name="scenarios-for-indices-and-ranges"></a><span data-ttu-id="ea863-148">Scénáře pro rozsahy a indexy</span><span class="sxs-lookup"><span data-stu-id="ea863-148">Scenarios for Indices and Ranges</span></span>

<span data-ttu-id="ea863-149">Pokud chcete provádět některé analýzy podrozsahu celé sekvenci, budete používat často rozsahy a indexy.</span><span class="sxs-lookup"><span data-stu-id="ea863-149">You'll often use ranges and indices when you want to perform some analysis on subrange of an entire sequence.</span></span> <span data-ttu-id="ea863-150">Nová syntaxe je jasnější v přesně je zahrnuta jaké podrozsahu pro čtení.</span><span class="sxs-lookup"><span data-stu-id="ea863-150">The new syntax is clearer in reading exactly what subrange is involved.</span></span> <span data-ttu-id="ea863-151">Lokální funkce `MovingAverage` přijímá <xref:System.Range> jako svůj argument.</span><span class="sxs-lookup"><span data-stu-id="ea863-151">The local function `MovingAverage` takes a <xref:System.Range> as its argument.</span></span> <span data-ttu-id="ea863-152">Metoda pak vytvoří výčet právě tento rozsah při výpočtu min, max a průměr.</span><span class="sxs-lookup"><span data-stu-id="ea863-152">The method then enumerates just that range when calculating the min, max, and average.</span></span> <span data-ttu-id="ea863-153">Vyzkoušejte následující kód ve vašem projektu:</span><span class="sxs-lookup"><span data-stu-id="ea863-153">Try the following code in your project:</span></span>

[!code-csharp[MovingAverages](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_MovingAverage)]

<span data-ttu-id="ea863-154">Můžete stáhnout Dokončený kód z [dotnet/samples](https://github.com/dotnet/samples/tree/master/csharp/tutorials/RangesIndexes) úložiště.</span><span class="sxs-lookup"><span data-stu-id="ea863-154">You can download the completed code from the [dotnet/samples](https://github.com/dotnet/samples/tree/master/csharp/tutorials/RangesIndexes) repository.</span></span>
