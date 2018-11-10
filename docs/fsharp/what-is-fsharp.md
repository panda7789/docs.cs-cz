---
title: Co je F#
description: Další informace o jaké F# programovací jazyk je a co programování v jazyce F# je jako. Další informace o bohaté datové typy, funkce a jak jsou zapadají.
ms.date: 08/03/2018
ms.openlocfilehash: 193747f380c61a387ed79ecca6abbcd90ee74376
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/02/2018
ms.locfileid: "43863293"
---
# <a name="what-is-f"></a>Co je F# #

F# je funkcionální programovací jazyk, který usnadňuje zápis správné a udržovatelný kód.

Programování v jazyce F# primárně potřeba definovat typy a funkce, které se odvodit typ a automaticky zobecněný. Díky tomu váš výběr zůstat na domény a manipulace s nimi svoje data, spíše než o programování.

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

F# obsahuje mnoho funkcí, včetně:

* Prostá syntaxe
* Neměnné ve výchozím nastavení
* Odvození typu proměnné a Automatická generalizace
* Funkce první třídy
* Výkonné datové typy
* Porovnávání vzorů
* Asynchronní programování

Úplná sada funkcí jsou dokumentovány v článku [referenční dokumentace jazyka F#](language-reference/index.md).

## <a name="rich-data-types"></a>Bohaté datové typy

Datové typy, jako [záznamy](language-reference/records.md) a [Rozlišované sjednocení](language-reference/discriminated-unions.md) umožňují představují komplexní data a domén.

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

F# záznamy a rozlišovaná sjednocení jsou nenulové, neměnné a srovnatelné ve výchozím nastavení, díky kterým jsou velmi snadné použití.

## <a name="enforced-correctness-with-functions-and-pattern-matching"></a>Vynucené správnosti s funkcemi a porovnávání vzorů

Funkce F# jsou snadno k deklaraci a výkonné v praxi. V kombinaci s [porovnávání vzorů](language-reference/pattern-matching.md), umožňují definovat chování, jehož správnosti je vynucena kompilátorem.

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

Funkce F# jsou také první třídy, což znamená, mohou být předány jako parametry a vrácená z dalších funkcí.

## <a name="functions-to-define-operations-on-objects"></a>Funkce k definování operací s objekty

F# obsahuje plnou podporu pro objekty, které jsou užitečné datové typy, pokud chcete kombinovat data a funkce. Funkce F# se používají k práci s objekty.

```fsharp
type Set<[<EqualityConditionOn>] ‘T when ‘T: comparison>(elements: seq<'T>) =
    member s.IsEmpty = // Implementation elided
    member s.Contains (value) =// Implementation elided
    member s.Add (value) = // Implementation elided
    // ...
    // Further Implementation elided
    // ...
    interface IEnumerable<‘T>
    interface IReadOnlyCollection<‘T>

[<RequireQualifiedAccess>]
module Set =
    let isEmpty (set: Set<'T>) = set.IsEmpty

    let contains element (set: Set<'T>) = set.Contains(element)

    let add value (set: Set<'T>) = set.Add(value)
```

Místo psaní kódu, který je objektově orientované, v jazyce F#, budete často psát kód, že zpracuje objekty jako jiný typ dat pro funkce pro manipulaci s. Funkce, jako [obecných rozhraní](language-reference/interfaces.md), [výrazy objektu](language-reference/object-expressions.md)a rozumné využití [členy](language-reference/members/index.md) jsou běžné ve větších programů F#.

## <a name="next-steps"></a>Další kroky

Další informace o větší sadu funkcí F#, podívejte se [F# Tour](tour.md).