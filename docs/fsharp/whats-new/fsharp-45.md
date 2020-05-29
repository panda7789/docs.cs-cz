---
title: 'Co je nového v příručce F # 4,5-F #'
description: 'Získejte přehled o nových funkcích dostupných v F # 4,5.'
ms.date: 11/27/2019
ms.openlocfilehash: 2c978c66a4bf231398508cbc1cbb8839228ea8e9
ms.sourcegitcommit: 71b8f5a2108a0f1a4ef1d8d75c5b3e129ec5ca1e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/29/2020
ms.locfileid: "84202352"
---
# <a name="whats-new-in-f-45"></a>Co je nového v jazyce F # 4,5

Jazyk f # 4,5 přidává více vylepšení jazyka F #. Mnohé z těchto funkcí byly přidány dohromady, aby bylo možné psát efektivní kód v F # a zároveň zajistit bezpečnost tohoto kódu. To znamená, že přidání několika konceptů do jazyka a významného množství analýzy kompilátoru při použití těchto konstrukcí.

## <a name="get-started"></a>Začínáme

F # 4,5 je k dispozici ve všech distribucích .NET Core a nástrojích sady Visual Studio. Začněte [s F #](../get-started/index.md) a získejte další informace.

## <a name="span-and-byref-like-structs"></a>Struktury typu span a ByRef

<xref:System.Span%601>Typ zavedený v .NET Core umožňuje znázornit vyrovnávací paměti v paměti se silným typem, který je teď povolený v f # počínaje f # 4,5. Následující příklad ukazuje, jak lze znovu použít funkci, která pracuje <xref:System.Span%601> s různými reprezentacemi vyrovnávací paměti:

```fsharp
let safeSum (bytes: Span<byte>) =
    let mutable sum = 0
    for i in 0 .. bytes.Length - 1 do
        sum <- sum + int bytes.[i]
    sum

// managed memory
let arrayMemory = Array.zeroCreate<byte>(100)
let arraySpan = new Span<byte>(arrayMemory)

safeSum(arraySpan) |> printfn "res = %d"

// native memory
let nativeMemory = Marshal.AllocHGlobal(100);
let nativeSpan = new Span<byte>(nativeMemory.ToPointer(), 100)

safeSum(nativeSpan) |> printfn "res = %d"
Marshal.FreeHGlobal(nativeMemory)

// stack memory
let mem = NativePtr.stackalloc<byte>(100)
let mem2 = mem |> NativePtr.toVoidPtr
let stackSpan = Span<byte>(mem2, 100)

safeSum(stackSpan) |> printfn "res = %d"
```

Důležitým aspektem je, že rozsah a jiné [struktury typu ByRef](../language-reference/structures.md#byreflike-structs) mají velmi pevnou statickou analýzu provedenou kompilátorem, která omezuje jejich použití způsobem, který by mohl být neočekávaný. Jedná se o zásadní kompromisy mezi výkonem, expresivity a bezpečností, které jsou představeny v F # 4,5.

## <a name="revamped-byrefs"></a>Přepracované byrefs

Před F # 4,5 byly [byrefs](../language-reference/byrefs.md) v jazyce f # nebezpečné a nezvukové pro mnoho aplikací. V jazyce F # 4,5 byly vyřešeny problémy se zvukem ByRef a byla použita stejná statická analýza pro rozsah a strukturu typu ByRef.

### <a name="inreft-and-outreft"></a>inref< t> a outref< t>

Aby reprezentovala pojem spravovaného ukazatele jen pro čtení, jen pro zápis a čtení a zápis, F # 4,5 představuje `inref<'T>` `outref<'T>` typy, které reprezentují ukazatele jen pro čtení a jen pro zápis, v uvedeném pořadí. Každá z nich má různou sémantiku. Například nemůžete zapisovat do `inref<'T>` :

```fsharp
let f (dt: inref<DateTime>) =
    dt <- DateTime.Now // ERROR - cannot write to an inref!
```

Ve výchozím nastavení bude odvození typu odvodit spravované ukazatele jako `inref<'T>` v souladu s neproměnlivou povahou kódu F #, pokud něco již nebylo deklarováno jako mutable. Aby bylo možné zapisovat do libovolného textu, je nutné deklarovat typ jako `mutable` před předáním jeho adresy funkci nebo členu, který je s ním manipulován. Další informace najdete v tématu [byrefs](../language-reference/byrefs.md).

## <a name="readonly-structs"></a>Struktury jen pro čtení

Počínaje F # 4,5 můžete přidat do struktury poznámku <xref:System.Runtime.CompilerServices.IsReadOnlyAttribute> jako takovou:

```fsharp
[<IsReadOnly; Struct>]
type S(count1: int, count2: int) =
    member x.Count1 = count1
    member x.Count2 = count2
```

To vám neumožní deklarovat proměnlivého člena ve struktuře a emitovat metadata, která umožňují jazyku F # a C# zacházet jako ReadOnly při spotřebování ze sestavení. Další informace najdete v tématu [struktury jen pro čtení](../language-reference/structures.md#readonly-structs).

## <a name="void-pointers"></a>Ukazatele void

`voidptr`Typ je přidán do F # 4,5, jak jsou následující funkce:

* `NativePtr.ofVoidPtr`převod ukazatele void na nativní ukazatel int
* `NativePtr.toVoidPtr`převod nativního ukazatele int na ukazatel void

To je užitečné při spolupráci s nativní komponentou, která využívá ukazatele void.

## <a name="the-match-keyword"></a>Klíčové slovo `match!`

`match!`Klíčové slovo vylepšuje porovnávání vzorů v rámci výrazu výpočtu:

```fsharp
// Code that returns an asynchronous option
let checkBananaAsync (s: string) =
    async {
        if s = "banana" then
            return Some s
        else
            return None
    }

// Now you can use 'match!'
let funcWithString (s: string) =
    async {
        match! checkBananaAsync s with
        | Some bananaString -> printfn "It's banana!"
        | None -> printfn "%s" s
}
```

To umožňuje zkrátit kód, který často zahrnuje možnosti kombinování (nebo jiných typů) s výpočetními výrazy, jako je například Async. Další informace najdete v tématu věnovaném [shodě](../language-reference/computation-expressions.md#match).

## <a name="relaxed-upcasting-requirements-in-array-list-and-sequence-expressions"></a>Odlehčené požadavky na přetypování ve výrazech Array, list a Sequence

Kombinování typů, kde jedna může dědit z jiného objektu Array, list a Sequence Expressions, je tradičně nutné k přetypování odvozeného typu na svůj nadřazený typ pomocí `:>` nebo `upcast` . To je teď odlehčené, které ukazuje následující:

```fsharp
let x0 : obj list  = [ "a" ] // ok pre-F# 4.5
let x1 : obj list  = [ "a"; "b" ] // ok pre-F# 4.5
let x2 : obj list  = [ yield "a" :> obj ] // ok pre-F# 4.5

let x3 : obj list  = [ yield "a" ] // Now ok for F# 4.5, and can replace x2
```

## <a name="indentation-relaxation-for-array-and-list-expressions"></a>Zmírnění odrážek pro výrazy Array a list

Před F # 4,5 jste museli při předávání jako argumentů volání metody příliš odsazovat výrazy pole a seznamu. Už to není potřeba:

```fsharp
module NoExcessiveIndenting =
    System.Console.WriteLine(format="{0}", arg = [|
        "hello"
    |])
    System.Console.WriteLine([|
        "hello"
    |])
```
