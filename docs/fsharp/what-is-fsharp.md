---
title: Co je F#
description: Přečtěte si, F# co je programovací jazyk a F# jaké je programování. Přečtěte si o bohatých datových typech, funkcích a o tom, jak se vejdou dohromady.
ms.date: 08/03/2018
ms.openlocfilehash: 3cba509f59a8e81e1a0264de7451e9d80304d768
ms.sourcegitcommit: 8b8dd14dde727026fd0b6ead1ec1df2e9d747a48
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/27/2019
ms.locfileid: "71332737"
---
# <a name="what-is-f"></a>Co je F\#

F#je funkční programovací jazyk, který usnadňuje psaní správného a udržovatelného kódu.

F#programování primárně zahrnuje definování typů a funkcí, které jsou odvozeny a zobecněny automaticky. Díky tomu může být zaostření v doméně problému a manipulaci s daty namísto podrobností programování.

```fsharp
open System // Gets access to functionality in System namespace.

// Defines a function that takes a name and produces a greeting.
let getGreeting name =
    sprintf "Hello, %s! Isn't F# great?" name

[<EntryPoint>]
let main args =
    // Defines a list of names
    let names = [ "Don"; "Julia"; "Xi" ]

    // Prints a greeting for each name!
    names
    |> List.map getGreeting
    |> List.iter (fun greeting -> printfn "%s" greeting)

    0
```

F#obsahuje mnoho funkcí, včetně:

* Prostá syntaxe
* Neměnné ve výchozím nastavení
* Odvození typu a Automatická generalizace
* Funkce první třídy
* Výkonné datové typy
* Porovnávání vzorů
* Asynchronní programování

V [ F# referenční příručce k jazyku](./language-reference/index.md)jsou popsány úplné sady funkcí.

## <a name="rich-data-types"></a>Formátované datové typy

Datové typy, jako jsou [záznamy](./language-reference/records.md) a [rozlišené sjednocení](./language-reference/discriminated-unions.md) , umožňují reprezentovat složitá data a domény.

```fsharp
// Group data with Records
type SuccessfulWithdrawal = {
    Amount: decimal
    Balance: decimal
}

type FailedWithdrawal = {
    Amount: decimal
    Balance: decimal
    IsOverdraft: bool
}

// Use discriminated unions to represent data of 1 or more forms
type WithdrawalResult =
    | Success of SuccessfulWithdrawal
    | InsufficientFunds of FailedWithdrawal
    | CardExpired of System.DateTime
    | UndisclosedFailure
```

F#záznamy a rozlišené sjednocení jsou ve výchozím nastavení nenulové, neměnné a srovnatelné, takže je velmi snadné je používat.

## <a name="enforced-correctness-with-functions-and-pattern-matching"></a>Vynutila správnost pomocí funkcí a porovnávání vzorů.

F#funkce jsou v praxi snadno deklarované a výkonné. V kombinaci se [porovnáváním vzorů](./language-reference/pattern-matching.md)umožňuje definovat chování, jehož správnost je vynutila kompilátorem.

```fsharp
// Returns a WithdrawalResult
let withdrawMoney amount = // Implementation elided

let handleWithdrawal amount =
    let w = withdrawMoney amount

    // The F# compiler enforces accounting for each case!
    match w with
    | Success s -> printfn "Successfully withdrew %f" s.Amount
    | InsufficientFunds f -> printfn "Failed: balance is %f" f.Balance
    | CardExpired d -> printfn "Failed: card expired on %O" d
    | UndisclosedFailure -> printfn "Failed: unknown :("
```

F#funkce jsou také první třídy, což znamená, že mohou být předány jako parametry a vráceny z jiných funkcí.

## <a name="functions-to-define-operations-on-objects"></a>Funkce pro definování operací s objekty

F#má plnou podporu pro objekty, které jsou užitečné datové typy, pokud potřebujete Blend data a funkce. F#funkce se používají k manipulaci s objekty.

```fsharp
type Set<'T when 'T: comparison>(elements: seq<'T>) =
    member s.IsEmpty = // Implementation elided
    member s.Contains (value) =// Implementation elided
    member s.Add (value) = // Implementation elided
    // ...
    // Further Implementation elided
    // ...
    interface IEnumerable<‘T>
    interface IReadOnlyCollection<‘T>

module Set =
    let isEmpty (set: Set<'T>) = set.IsEmpty

    let contains element (set: Set<'T>) = set.Contains(element)

    let add value (set: Set<'T>) = set.Add(value)
```

Místo psaní kódu, který je objektově orientovaný, v F#nástroji budete často psát kód, který bude zpracovávat objekty jako jiný datový typ pro zpracování funkcí. Funkce, jako jsou [Obecná rozhraní](./language-reference/interfaces.md), [výrazy objektů](./language-reference/object-expressions.md)a rozumné použití [členů](./language-reference/members/index.md) , jsou běžné ve větších F# programech.

## <a name="next-steps"></a>Další kroky

Pokud se chcete dozvědět víc o větší sadě F# funkcí, podívejte se na [ F# prohlídku](tour.md).
