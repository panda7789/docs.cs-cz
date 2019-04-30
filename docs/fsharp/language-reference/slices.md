---
title: Kolekce obsahuje nějaké řezy (F#)
description: Další informace o tom, jak používat kolekce obsahuje nějaké řezy existujících F# datových typů a tom, jak definovat vlastní kolekce obsahuje nějaké řezy pro jiné datové typy.
ms.date: 01/22/2019
ms.openlocfilehash: 1d8bb029ad18c8853ab58888959967ed279fb368
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61925984"
---
# <a name="slices"></a><span data-ttu-id="2b65a-103">Kolekce obsahuje nějaké řezy</span><span class="sxs-lookup"><span data-stu-id="2b65a-103">Slices</span></span>

<span data-ttu-id="2b65a-104">V F#, řez je podmnožinou datového typu.</span><span class="sxs-lookup"><span data-stu-id="2b65a-104">In F#, a slice is a subset of a data type.</span></span> <span data-ttu-id="2b65a-105">Aby bylo možné provést určitý řez od datového typu, musíte buď definovat datový typ `GetSlice` metoda nebo v [zadejte příponu](type-extensions.md) , který je v oboru.</span><span class="sxs-lookup"><span data-stu-id="2b65a-105">To be able to take a slice from a data type, the data type must either define a `GetSlice` method or in a [type extension](type-extensions.md) that is in scope.</span></span> <span data-ttu-id="2b65a-106">Tento článek vysvětluje, jak využít řezy z existujících F# typy a tom, jak definovat vlastní.</span><span class="sxs-lookup"><span data-stu-id="2b65a-106">This article explains how to take slices from existing F# types and how to define your own.</span></span>

<span data-ttu-id="2b65a-107">Kolekce obsahuje nějaké řezy jsou podobné [indexery](members/indexed-properties.md), ale místo získávání jedinou hodnotu z podkladová datová struktura, poskytují několik snímků.</span><span class="sxs-lookup"><span data-stu-id="2b65a-107">Slices are similar to [indexers](members/indexed-properties.md), but instead of yielding a single value from the underlying data structure, they yield multiple ones.</span></span>

<span data-ttu-id="2b65a-108">F#nyní má hlavní vnitřní podporu pro dělení řetězců, seznamů, polí a 2D pole.</span><span class="sxs-lookup"><span data-stu-id="2b65a-108">F# currently has intrinsic support for slicing strings, lists, arrays, and 2D arrays.</span></span>

## <a name="basic-slicing-with-f-lists-and-arrays"></a><span data-ttu-id="2b65a-109">Základní dělení s F# seznamy a pole</span><span class="sxs-lookup"><span data-stu-id="2b65a-109">Basic slicing with F# lists and arrays</span></span>

<span data-ttu-id="2b65a-110">Nejčastěji používané datové typy, které jsou rozděleny jsou F# seznamy a pole.</span><span class="sxs-lookup"><span data-stu-id="2b65a-110">The most common data types that are sliced are F# lists and arrays.</span></span> <span data-ttu-id="2b65a-111">Následující příklad ukazuje, jak to udělat pomocí seznamů:</span><span class="sxs-lookup"><span data-stu-id="2b65a-111">The following example demonstrates how to do this with lists:</span></span>

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

<span data-ttu-id="2b65a-112">Řezání pole je stejné jako při vytváření řezů seznamy:</span><span class="sxs-lookup"><span data-stu-id="2b65a-112">Slicing arrays is just like slicing lists:</span></span>

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

## <a name="slicing-multidimensional-arrays"></a><span data-ttu-id="2b65a-113">Dělení vícerozměrná pole</span><span class="sxs-lookup"><span data-stu-id="2b65a-113">Slicing multidimensional arrays</span></span>

<span data-ttu-id="2b65a-114">F#podporuje vícerozměrná pole v F# základní knihovny.</span><span class="sxs-lookup"><span data-stu-id="2b65a-114">F# supports multidimensional arrays in the F# core library.</span></span> <span data-ttu-id="2b65a-115">Stejně jako u jednorozměrné pole, řezy vícerozměrná pole lze také užitečné.</span><span class="sxs-lookup"><span data-stu-id="2b65a-115">As with one-dimensional arrays, slices of multidimensional arrays can also be useful.</span></span> <span data-ttu-id="2b65a-116">Ale zavedení další dimenze zmocňuje mírně odlišnou syntaxi tak, aby si můžete řezy konkrétní řádků a sloupců.</span><span class="sxs-lookup"><span data-stu-id="2b65a-116">However, the introduction of additional dimensions mandates a slightly different syntax so that you can take slices of specific rows and columns.</span></span>

<span data-ttu-id="2b65a-117">Následující příklady ukazují, jak rozdělit 2D pole:</span><span class="sxs-lookup"><span data-stu-id="2b65a-117">The following examples demonstrate how to slice a 2D array:</span></span>

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

<span data-ttu-id="2b65a-118">F# Základní knihovna nedefinuje `GetSlice`pro 3D pole.</span><span class="sxs-lookup"><span data-stu-id="2b65a-118">The F# core library does not define `GetSlice`for 3D arrays.</span></span> <span data-ttu-id="2b65a-119">Pokud budete chtít rozdělit ty nebo jiných polí více dimenzí, je nutné definovat `GetSlice` člen sami.</span><span class="sxs-lookup"><span data-stu-id="2b65a-119">If you wish to slice those or other arrays of more dimensions, you must define the `GetSlice` member yourself.</span></span>

## <a name="defining-slices-for-other-data-structures"></a><span data-ttu-id="2b65a-120">Definování kolekce obsahuje nějaké řezy pro další datové struktury</span><span class="sxs-lookup"><span data-stu-id="2b65a-120">Defining slices for other data structures</span></span>

<span data-ttu-id="2b65a-121">F# Základní knihovna definuje řezy pro omezenou sadu typů.</span><span class="sxs-lookup"><span data-stu-id="2b65a-121">The F# core library defines slices for a limited set of types.</span></span> <span data-ttu-id="2b65a-122">Pokud chcete definovat řezy pro další typy dat, lze provést v definici typu, samotné nebo v rozšíření typu.</span><span class="sxs-lookup"><span data-stu-id="2b65a-122">If you wish to define slices for more data types, you can do so either in the type definition itself or in a type extension.</span></span>

<span data-ttu-id="2b65a-123">Například tady je způsob můžete třeba definovat ve výsečích <xref:System.ArraySegment%601> třídu, která umožňuje pro manipulaci s daty vhodné:</span><span class="sxs-lookup"><span data-stu-id="2b65a-123">For example, here's how you might define slices for the <xref:System.ArraySegment%601> class to allow for convenient data manipulation:</span></span>

```fsharp
open System

type ArraySegment<'TItem> with
    member segment.GetSlice(?start, ?finish) =
        let start = defaultArg start 0
        let finish = defaultArg finish segment.Count
        ArraySegment(segment.Array, segment.Offset + start, finish - start)

let arr = ArraySegment [| 1 .. 10 |]
let slice = arr.[2..5] //[ 3; 4; 5]
```

### <a name="use-inlining-to-avoid-boxing-if-it-is-necessary"></a><span data-ttu-id="2b65a-124">Pomocí vkládání, pokud je nutné, aby zabalení</span><span class="sxs-lookup"><span data-stu-id="2b65a-124">Use inlining to avoid boxing if it is necessary</span></span>

<span data-ttu-id="2b65a-125">Pokud definujete řezy pro typ, který je ve skutečnosti struktura, doporučujeme vám `inline` `GetSlice` člen.</span><span class="sxs-lookup"><span data-stu-id="2b65a-125">If you are defining slices for a type that is actually a struct, we recommend that you `inline` the `GetSlice` member.</span></span> <span data-ttu-id="2b65a-126">F# Kompilátor optimalizuje okamžitě volitelné argumenty, jak se vyhnout libovolná přidělení haldy jako výsledek dělení.</span><span class="sxs-lookup"><span data-stu-id="2b65a-126">The F# compiler optimizes away the optional arguments, avoiding any heap allocations as a result of slicing.</span></span> <span data-ttu-id="2b65a-127">To je obzvláště důležité pro dělení konstrukce, jako <xref:System.Span%601> , který se nedá přidělit v haldě.</span><span class="sxs-lookup"><span data-stu-id="2b65a-127">This is critically important for slicing constructs such as <xref:System.Span%601> that cannot be allocated on the heap.</span></span>

```fsharp
open System

type Span<'T> with
    // Note the 'inline' in the member definition
    member inline sp.GetSlice(startIdx, endIdx) =
        let s = defaultArg startIdx 0
        let e = defaultArg endIdx sp.Length
        sp.Slice(s, e)

let printSpan (sp: Span<int>) =
    let arr = sp.ToArray()
    printfn "%A" arr

let sp = [| 1; 2; 3; 4; 5 |].AsSpan()
printSpan sp.[0..] // [|1; 2; 3; 4; 5|]
printSpan sp.[..5] // [|1; 2; 3; 4; 5|]
printSpan sp.[0..3] // [|1; 2; 3|]
printSpan sp.[1..2] // |2; 3|]
```

## <a name="see-also"></a><span data-ttu-id="2b65a-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2b65a-128">See also</span></span>

- [<span data-ttu-id="2b65a-129">Indexované vlastnosti</span><span class="sxs-lookup"><span data-stu-id="2b65a-129">Indexed properties</span></span>](members/indexed-properties.md)
