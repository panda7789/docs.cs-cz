---
title: Kolekce obsahuje nějaké řezy (F#)
description: Další informace o tom, jak používat kolekce obsahuje nějaké řezy existujících F# datových typů a tom, jak definovat vlastní kolekce obsahuje nějaké řezy pro jiné datové typy.
ms.date: 01/22/2019
ms.openlocfilehash: 60b57d4eea40bb26dc43d8255dd933b63ac6303c
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56970103"
---
# <a name="slices"></a>Kolekce obsahuje nějaké řezy

V F#, řez je podmnožinou datového typu. Aby bylo možné provést určitý řez od datového typu, musíte buď definovat datový typ `GetSlice` metoda nebo v [zadejte příponu](type-extensions.md) , který je v oboru. Tento článek vysvětluje, jak využít řezy z existujících F# typy a tom, jak definovat vlastní.

Kolekce obsahuje nějaké řezy jsou podobné [indexery](members/indexed-properties.md), ale místo získávání jedinou hodnotu z podkladová datová struktura, poskytují několik snímků.

F#nyní má hlavní vnitřní podporu pro dělení řetězců, seznamů, polí a 2D pole.

## <a name="basic-slicing-with-f-lists-and-arrays"></a>Základní dělení s F# seznamy a pole

Nejčastěji používané datové typy, které jsou rozděleny jsou F# seznamy a pole. Následující příklad ukazuje, jak to udělat pomocí seznamů:

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

Řezání pole je stejné jako při vytváření řezů seznamy:

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

## <a name="slicing-multidimensional-arrays"></a>Dělení vícerozměrná pole

F#podporuje vícerozměrná pole v F# základní knihovny. Stejně jako u jednorozměrné pole, řezy vícerozměrná pole lze také užitečné. Ale zavedení další dimenze zmocňuje mírně odlišnou syntaxi tak, aby si můžete řezy konkrétní řádků a sloupců.

Následující příklady ukazují, jak rozdělit 2D pole:

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
printfn "%A" twobyTwo
```

F# Základní knihovna nedefinuje `GetSlice`pro 3D pole. Pokud budete chtít rozdělit ty nebo jiných polí více dimenzí, je nutné definovat `GetSlice` člen sami.

## <a name="defining-slices-for-other-data-structures"></a>Definování kolekce obsahuje nějaké řezy pro další datové struktury

F# Základní knihovna definuje řezy pro omezenou sadu typů. Pokud chcete definovat řezy pro další typy dat, lze provést v definici typu, samotné nebo v rozšíření typu.

Například tady je způsob můžete třeba definovat ve výsečích <xref:System.ArraySegment%601> třídu, která umožňuje pro manipulaci s daty vhodné:

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

### <a name="use-inlining-to-avoid-boxing-if-it-is-necessary"></a>Pomocí vkládání, pokud je nutné, aby zabalení

Pokud definujete řezy pro typ, který je ve skutečnosti struktura, doporučujeme vám `inline` `GetSlice` člen. F# Kompilátor optimalizuje okamžitě volitelné argumenty, jak se vyhnout libovolná přidělení haldy jako výsledek dělení. To je obzvláště důležité pro dělení konstrukce, jako <xref:System.Span%601> , který se nedá přidělit v haldě.

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

## <a name="see-also"></a>Viz také:

- [Indexované vlastnosti](members/indexed-properties.md)
