---
title: Řezy
description: Naučte se, jak používat řezy F# pro existující datové typy a jak definovat vlastní řezy pro jiné datové typy.
ms.date: 12/23/2019
ms.openlocfilehash: 928005f2c63ffe099bb64e11ed29bb625e0a54c6
ms.sourcegitcommit: 19014f9c081ca2ff19652ca12503828db8239d48
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/04/2020
ms.locfileid: "76980376"
---
# <a name="slices"></a><span data-ttu-id="e91ca-103">Řezy</span><span class="sxs-lookup"><span data-stu-id="e91ca-103">Slices</span></span>

<span data-ttu-id="e91ca-104">V F#je řez podmnožinou libovolného datového typu, který má metodu `GetSlice` v definici nebo v [rozšíření typu](type-extensions.md)v rámci oboru.</span><span class="sxs-lookup"><span data-stu-id="e91ca-104">In F#, a slice is a subset of any data type that has a `GetSlice` method in its definition or in an in-scope [type extension](type-extensions.md).</span></span> <span data-ttu-id="e91ca-105">Nejčastěji se používá u F# polí a seznamů.</span><span class="sxs-lookup"><span data-stu-id="e91ca-105">It is most commonly used with F# arrays and lists.</span></span> <span data-ttu-id="e91ca-106">Tento článek vysvětluje, jak vzít řezy z existujících F# typů a jak definovat vlastní řezy.</span><span class="sxs-lookup"><span data-stu-id="e91ca-106">This article explains how to take slices from existing F# types and how to define your own slices.</span></span>

<span data-ttu-id="e91ca-107">Řezy se podobají [indexerům](./members/indexed-properties.md), ale místo toho, aby vydávaly jedinou hodnotu z podkladové datové struktury, poskytují více.</span><span class="sxs-lookup"><span data-stu-id="e91ca-107">Slices are similar to [indexers](./members/indexed-properties.md), but instead of yielding a single value from the underlying data structure, they yield multiple ones.</span></span>

<span data-ttu-id="e91ca-108">F#v současné době má vnitřní podporu pro vytváření řezů řetězců, seznamů, polí a 2D polí.</span><span class="sxs-lookup"><span data-stu-id="e91ca-108">F# currently has intrinsic support for slicing strings, lists, arrays, and 2D arrays.</span></span>

## <a name="basic-slicing-with-f-lists-and-arrays"></a><span data-ttu-id="e91ca-109">Základní řezy se F# seznamy a poli</span><span class="sxs-lookup"><span data-stu-id="e91ca-109">Basic slicing with F# lists and arrays</span></span>

<span data-ttu-id="e91ca-110">Nejběžnější typy dat, které jsou rozdělené, jsou F# seznamy a pole.</span><span class="sxs-lookup"><span data-stu-id="e91ca-110">The most common data types that are sliced are F# lists and arrays.</span></span> <span data-ttu-id="e91ca-111">Následující příklad ukazuje, jak to provést se seznamy:</span><span class="sxs-lookup"><span data-stu-id="e91ca-111">The following example demonstrates how to do this with lists:</span></span>

```fsharp
// Generate a list of 100 integers
let fullList = [ 1 .. 100 ]

// Create a slice from indices 1-5 (inclusive)
let smallSlice = fullList.[1..5]
printfn "Small slice: %A" smallSlice

// Create a slice from the beginning to index 5 (inclusive)
let unboundedBeginning = fullList.[..5]
printfn "Unbounded beginning slice: %A" unboundedBeginning

// Create a slice from an index to the end of the list
let unboundedEnd = fullList.[94..]
printfn "Unbounded end slice: %A" unboundedEnd
```

<span data-ttu-id="e91ca-112">Pole řezů je stejně jako v seznamech řezů:</span><span class="sxs-lookup"><span data-stu-id="e91ca-112">Slicing arrays is just like slicing lists:</span></span>

```fsharp
// Generate an array of 100 integers
let fullArray = [| 1 .. 100 |]

// Create a slice from indices 1-5 (inclusive)
let smallSlice = fullArray.[1..5]
printfn "Small slice: %A" smallSlice

// Create a slice from the beginning to index 5 (inclusive)
let unboundedBeginning = fullArray.[..5]
printfn "Unbounded beginning slice: %A" unboundedBeginning

// Create a slice from an index to the end of the list
let unboundedEnd = fullArray.[94..]
printfn "Unbounded end slice: %A" unboundedEnd
```

## <a name="slicing-multidimensional-arrays"></a><span data-ttu-id="e91ca-113">Vytváření řezů multidimenzionálních polí</span><span class="sxs-lookup"><span data-stu-id="e91ca-113">Slicing multidimensional arrays</span></span>

<span data-ttu-id="e91ca-114">F#podporuje multidimenzionální pole v F# základní knihovně.</span><span class="sxs-lookup"><span data-stu-id="e91ca-114">F# supports multidimensional arrays in the F# core library.</span></span> <span data-ttu-id="e91ca-115">Stejně jako u jednorozměrného pole mohou být také užitečné řezy multidimenzionálních polí.</span><span class="sxs-lookup"><span data-stu-id="e91ca-115">As with one-dimensional arrays, slices of multidimensional arrays can also be useful.</span></span> <span data-ttu-id="e91ca-116">Zavedení dalších dimenzí však vyžaduje mírně odlišnou syntaxi, takže můžete pořizovat řezy konkrétních řádků a sloupců.</span><span class="sxs-lookup"><span data-stu-id="e91ca-116">However, the introduction of additional dimensions mandates a slightly different syntax so that you can take slices of specific rows and columns.</span></span>

<span data-ttu-id="e91ca-117">Následující příklady ukazují, jak vytvořit řezy 2D pole:</span><span class="sxs-lookup"><span data-stu-id="e91ca-117">The following examples demonstrate how to slice a 2D array:</span></span>

```fsharp
// Generate a 3x3 2D matrix
let A = array2D [[1;2;3];[4;5;6];[7;8;9]]
printfn "Full matrix:\n %A" A

// Take the first row
let row0 = A.[0,*]
printfn "Row 0: %A" row0

// Take the first column
let col0 = A.[*,0]
printfn "Column 0: %A" col0

// Take all rows but only two columns
let subA = A.[*,0..1]
printfn "%A" subA

// Take two rows and all columns
let subA' = A.[0..1,*]
printfn "%A" subA'

// Slice a 2x2 matrix out of the full 3x3 matrix
let twoByTwo = A.[0..1,0..1]
printfn "%A" twoByTwo
```

<span data-ttu-id="e91ca-118">F# Základní knihovna aktuálně nedefinuje `GetSlice` pro 3D pole.</span><span class="sxs-lookup"><span data-stu-id="e91ca-118">The F# core library does not currently define `GetSlice` for 3D arrays.</span></span> <span data-ttu-id="e91ca-119">Pokud chcete rozdělit 3D pole nebo jiná pole více dimenzí, definujte `GetSlice` člena sami.</span><span class="sxs-lookup"><span data-stu-id="e91ca-119">If you wish to slice 3D arrays or other arrays of more dimensions, define the `GetSlice` member yourself.</span></span>

## <a name="defining-slices-for-other-data-structures"></a><span data-ttu-id="e91ca-120">Definování řezů pro jiné datové struktury</span><span class="sxs-lookup"><span data-stu-id="e91ca-120">Defining slices for other data structures</span></span>

<span data-ttu-id="e91ca-121">F# Základní knihovna definuje řezy pro omezené sady typů.</span><span class="sxs-lookup"><span data-stu-id="e91ca-121">The F# core library defines slices for a limited set of types.</span></span> <span data-ttu-id="e91ca-122">Pokud chcete definovat řezy pro více datových typů, můžete tak učinit buď v samotné definici typu, nebo v rozšíření typu.</span><span class="sxs-lookup"><span data-stu-id="e91ca-122">If you wish to define slices for more data types, you can do so either in the type definition itself or in a type extension.</span></span>

<span data-ttu-id="e91ca-123">Tady je příklad, jak můžete definovat řezy pro třídu <xref:System.ArraySegment%601>, abyste umožnili pohodlné manipulaci s daty:</span><span class="sxs-lookup"><span data-stu-id="e91ca-123">For example, here's how you might define slices for the <xref:System.ArraySegment%601> class to allow for convenient data manipulation:</span></span>

```fsharp
open System

type ArraySegment<'TItem> with
    member segment.GetSlice(start, finish) =
        let start = defaultArg start 0
        let finish = defaultArg finish segment.Count
        ArraySegment(segment.Array, segment.Offset + start, finish - start)

let arr = ArraySegment [| 1 .. 10 |]
let slice = arr.[2..5] //[ 3; 4; 5]
```

### <a name="use-inlining-to-avoid-boxing-if-it-is-necessary"></a><span data-ttu-id="e91ca-124">Použít vkládání k zamezení zabalení, pokud je to nezbytné</span><span class="sxs-lookup"><span data-stu-id="e91ca-124">Use inlining to avoid boxing if it is necessary</span></span>

<span data-ttu-id="e91ca-125">Pokud definujete řezy pro typ, který je ve skutečnosti strukturou, doporučujeme, abyste `inline` `GetSlice` člen.</span><span class="sxs-lookup"><span data-stu-id="e91ca-125">If you are defining slices for a type that is actually a struct, we recommend that you `inline` the `GetSlice` member.</span></span> <span data-ttu-id="e91ca-126">F# Kompilátor optimalizuje volitelné argumenty a vyloučí případné přidělení haldy jako výsledek vytváření řezů.</span><span class="sxs-lookup"><span data-stu-id="e91ca-126">The F# compiler optimizes away the optional arguments, avoiding any heap allocations as a result of slicing.</span></span> <span data-ttu-id="e91ca-127">To je důležité pro vytváření řezů, jako je například <xref:System.Span%601>, které nelze přidělit haldě.</span><span class="sxs-lookup"><span data-stu-id="e91ca-127">This is critically important for slicing constructs such as <xref:System.Span%601> that cannot be allocated on the heap.</span></span>

```fsharp
open System

type ReadOnlySpan<'T> with
    // Note the 'inline' in the member definition
    member inline sp.GetSlice(startIdx, endIdx) =
        let s = defaultArg startIdx 0
        let e = defaultArg endIdx sp.Length
        sp.Slice(s, e - s)

type Span<'T> with
    // Note the 'inline' in the member definition
    member inline sp.GetSlice(startIdx, endIdx) =
        let s = defaultArg startIdx 0
        let e = defaultArg endIdx sp.Length
        sp.Slice(s, e - s)

let printSpan (sp: Span<int>) =
    let arr = sp.ToArray()
    printfn "%A" arr

let sp = [| 1; 2; 3; 4; 5 |].AsSpan()
printSpan sp.[0..] // [|1; 2; 3; 4; 5|]
printSpan sp.[..5] // [|1; 2; 3; 4; 5|]
printSpan sp.[0..3] // [|1; 2; 3|]
printSpan sp.[1..3] // |2; 3|]
```

## <a name="built-in-f-slices-are-end-inclusive"></a><span data-ttu-id="e91ca-128">Předdefinované řezy jsou F# na konci včetně.</span><span class="sxs-lookup"><span data-stu-id="e91ca-128">Built-in F# slices are end-inclusive</span></span>

<span data-ttu-id="e91ca-129">Všechny vnitřní řezy v F# nástroji jsou na konci včetně. To znamená, že horní mez je obsažena v řezu.</span><span class="sxs-lookup"><span data-stu-id="e91ca-129">All intrinsic slices in F# are end-inclusive; that is, the upper bound is included in the slice.</span></span> <span data-ttu-id="e91ca-130">V daném řezu pomocí počátečního `x` indexu a ukončení `y`indexu bude výsledný řez obsahovat hodnotu *YTH* .</span><span class="sxs-lookup"><span data-stu-id="e91ca-130">For a given slice with starting index `x` and ending index `y`, the resulting slice will include the *yth* value.</span></span>

```fsharp
// Define a new list
let xs = [1 .. 10]

printfn "%A" xs.[2..5] // Includes the 5th index
```

## <a name="see-also"></a><span data-ttu-id="e91ca-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e91ca-131">See also</span></span>

- [<span data-ttu-id="e91ca-132">Indexované vlastnosti</span><span class="sxs-lookup"><span data-stu-id="e91ca-132">Indexed properties</span></span>](./members/indexed-properties.md)
