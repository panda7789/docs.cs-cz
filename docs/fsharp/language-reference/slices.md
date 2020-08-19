---
title: Řezy
description: 'Naučte se, jak používat řezy pro existující datové typy F # a jak definovat vlastní řezy pro jiné datové typy.'
ms.date: 12/23/2019
ms.openlocfilehash: d3ddb2c247c36a85842f565f051372c5f2c9a9e9
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/18/2020
ms.locfileid: "88559008"
---
# <a name="slices"></a>Řezy

V jazyce F # je řez podmnožinou libovolného datového typu, který má `GetSlice` metodu v definici nebo v [rozšíření typu](type-extensions.md)v rámci oboru. Nejčastěji se používá u polí a seznamů F #. Tento článek vysvětluje, jak vzít řezy z existujících typů F # a jak definovat vlastní řezy.

Řezy se podobají [indexerům](./members/indexed-properties.md), ale místo toho, aby vydávaly jedinou hodnotu z podkladové datové struktury, poskytují více.

Jazyk F # v současné době má vnitřní podporu pro vytváření řezů řetězců, seznamů, polí a 2D polí.

## <a name="basic-slicing-with-f-lists-and-arrays"></a>Základní průřezy pomocí seznamů a polí F #

Nejběžnější typy dat, které jsou rozdělené, jsou seznamy a pole F #. Následující příklad ukazuje, jak to provést se seznamy:

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

Pole řezů je stejně jako v seznamech řezů:

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

## <a name="slicing-multidimensional-arrays"></a>Vytváření řezů multidimenzionálních polí

Jazyk f # podporuje multidimenzionální pole v knihovně F # Core. Stejně jako u jednorozměrného pole mohou být také užitečné řezy multidimenzionálních polí. Zavedení dalších dimenzí však vyžaduje mírně odlišnou syntaxi, takže můžete pořizovat řezy konkrétních řádků a sloupců.

Následující příklady ukazují, jak vytvořit řezy 2D pole:

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

Základní knihovna F # není aktuálně definována `GetSlice` pro 3D pole. Pokud chcete rozdělit 3D pole nebo jiná pole více dimenzí, definujte `GetSlice` člena sami.

## <a name="defining-slices-for-other-data-structures"></a>Definování řezů pro jiné datové struktury

Základní knihovna jazyka F # definuje řezy pro omezené sady typů. Pokud chcete definovat řezy pro více datových typů, můžete tak učinit buď v samotné definici typu, nebo v rozšíření typu.

Tady je příklad, jak můžete definovat řezy pro <xref:System.ArraySegment%601> třídu, aby bylo možné pohodlné manipulaci s daty:

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

Další příklad s použitím <xref:System.Span%601> <xref:System.ReadOnlySpan%601> typů a:

```fsharp
open System

type ReadOnlySpan<'T> with
    member sp.GetSlice(startIdx, endIdx) =
        let s = defaultArg startIdx 0
        let e = defaultArg endIdx sp.Length
        sp.Slice(s, e - s)

type Span<'T> with
    member sp.GetSlice(startIdx, endIdx) =
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

## <a name="built-in-f-slices-are-end-inclusive"></a>Předdefinované řezy F # jsou na konci (včetně).

Všechny vnitřní řezy v F # jsou na konci včetně. To znamená, že horní mez je obsažena v řezu. Pro daný řez s počáteční index `x` a koncovým indexem `y` bude výsledný řez obsahovat hodnotu *YTH* .

```fsharp
// Define a new list
let xs = [1 .. 10]

printfn "%A" xs.[2..5] // Includes the 5th index
```

## <a name="see-also"></a>Viz také

- [Indexované vlastnosti](./members/indexed-properties.md)
