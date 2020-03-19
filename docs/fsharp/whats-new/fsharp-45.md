---
title: Co je nového ve F# 4.5 - F# Guide
description: Získejte přehled o nových funkcích dostupných v f# 4.5.
ms.date: 11/27/2019
ms.openlocfilehash: 560e3dd941f79b76d3b864ba0f6560be154ebc1a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186138"
---
# <a name="whats-new-in-f-45"></a>Co je nového ve F# 4.5

F# 4.5 přidává více vylepšení jazyka F#. Mnohé z těchto funkcí byly sečteny, abyste mohli psát efektivní kód v F# a zároveň zajistit, že tento kód je bezpečný. To znamená přidání několika konceptů do jazyka a značné množství analýzy kompilátoru při použití těchto konstrukcí.

## <a name="get-started"></a>Začínáme

F# 4.5 je k dispozici ve všech distribucích .NET Core a nástrojích Visual Studio. [Můžete začít s F#](../get-started/index.md) a dozvíte se více.

## <a name="span-and-byref-like-structs"></a>Span a byref-jako struktury

Typ <xref:System.Span%601> zavedený v .NET Core umožňuje reprezentovat vyrovnávací paměti v paměti způsobem silného typu, který je nyní povolen v F# počínaje F# 4.5. Následující příklad ukazuje, jak můžete znovu použít <xref:System.Span%601> funkci pracující s různými reprezentacemi vyrovnávací paměti:

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

Důležitým aspektem je, že Span a další [byref-jako struktury](../language-reference/structures.md#byreflike-structs) mají velmi rigidní statické analýzy prováděné kompilátorem, které omezují jejich použití způsoby, které může být neočekávané. Toto je základní kompromis mezi výkon, expresivita a bezpečnost, která je zavedena v F# 4.5.

## <a name="revamped-byrefs"></a>Přepracované byrefs

Před F# 4.5 [Byrefs](../language-reference/byrefs.md) v F# byly nebezpečné a nezdravé pro mnoho aplikací. Problémy se zvukem kolem byrefs byly řešeny v F# 4.5 a byla také použita stejná statická analýza provedená pro span a byref-like struktury.

### <a name="inreft-and-outreft"></a>inref<'T> a předčí<'T>

Chcete-li reprezentovat pojem jen pro čtení, jen pro zápis a čtení a `inref<'T>`zápis `outref<'T>` spravované ukazatel, F# 4.5 zavádí , typy představují jen pro čtení a jen pro zápis ukazatele, v uvedeném pořadí. Každý z nich má jinou sémantiku. Nelze například zapisovat do : `inref<'T>`

```fsharp
let f (dt: inref<DateTime>) =
    dt <- DateTime.Now // ERROR - cannot write to an inref!
```

Ve výchozím nastavení odvození typu odvodí spravované ukazatele tak, `inref<'T>` aby byly v souladu s neměnnou povahou kódu F#, pokud již bylo něco deklarováno jako proměnlivé. Chcete-li něco zapisovat, budete muset `mutable` deklarovat typ jako před předáním jeho adresu funkci nebo členovi, který s ním manipuluje. Další informace naleznete v [tématu Byrefs](../language-reference/byrefs.md).

## <a name="readonly-structs"></a>Struktury jen pro čtení

Počínaje F# 4.5, můžete anotovat strukturu <xref:System.Runtime.CompilerServices.IsReadOnlyAttribute> s jako takové:

```fsharp
[<IsReadOnly; Struct>]
type S(count1: int, count2: int) =
    member x.Count1 = count1
    member x.Count2 = count2
```

To zakazuje deklarování proměnlivý člen v struktuře a vydává metadata, která umožňuje F# a C# považovat za jen pro čtení při spotřebovávat z sestavení. Další informace najdete v tématu [Struktury jen pro čtení](../language-reference/structures.md#readonly-structs).

## <a name="void-pointers"></a>Void ukazatele

Typ `voidptr` je přidán do F# 4.5, stejně jako následující funkce:

* `NativePtr.ofVoidPtr`převedení ukazatele void na nativní ukazatel int
* `NativePtr.toVoidPtr`převedení nativního ukazatele int na ukazatel void

To je užitečné při spolupráci s nativní komponenty, která využívá void ukazatele.

## <a name="the-match-keyword"></a>Klíčové slovo `match!`

Klíčové `match!` slovo vylepšuje porovnávání vzorů uvnitř výpočtového výrazu:

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

To umožňuje zkrátit kód, který často zahrnuje možnosti míchání (nebo jiné typy) s výpočetní výrazy, jako je například asynchronní. Chcete-li se dozvědět více, viz [zápas!](../language-reference/computation-expressions.md#match).

## <a name="relaxed-upcasting-requirements-in-array-list-and-sequence-expressions"></a>Uvolněné požadavky na upcasting ve výrazech pole, seznamu a sekvencí

Míchání typů, kde jeden může dědit z jiného uvnitř pole, seznam a sekvence výrazy tradičně `:>` vyžaduje, abyste upcast libovolný odvozený typ jeho nadřazený typ s nebo `upcast`. To je nyní uvolněná, prokázáno takto:

```fsharp
let x0 : obj list  = [ "a" ] // ok pre-F# 4.5
let x1 : obj list  = [ "a"; "b" ] // ok pre-F# 4.5
let x2 : obj list  = [ yield "a" :> obj ] // ok pre-F# 4.5

let x3 : obj list  = [ yield "a" ] // Now ok for F# 4.5, and can replace x2
```

## <a name="indentation-relaxation-for-array-and-list-expressions"></a>Uvolnění odsazení pro výrazy pole a seznamu

Před F# 4.5 je třeba nadměrně odsadit pole a seznam výrazů při předání jako argumenty volání metody. To již není nutné:

```fsharp
module NoExcessiveIndenting =
    System.Console.WriteLine(format="{0}", arg = [|
        "hello"
    |])
    System.Console.WriteLine([|
        "hello"
    |])
```
