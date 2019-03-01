---
title: Co jeF#
description: Další informace o tom, co F# programovací jazyk je a co F# programování je stejná jako. Další informace o bohaté datové typy, funkce a jak jsou zapadají.
ms.date: 08/03/2018
ms.openlocfilehash: ea82147e4e6d3c980fb224eeafd805c7ed53f8f2
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56966955"
---
# <a name="what-is-f"></a><span data-ttu-id="4073d-104">Co je F\#</span><span class="sxs-lookup"><span data-stu-id="4073d-104">What is F\#</span></span>

<span data-ttu-id="4073d-105">F#je funkcionální programovací jazyk, který usnadňuje zápis správné a udržovatelný kód.</span><span class="sxs-lookup"><span data-stu-id="4073d-105">F# is a functional programming language that makes it easy to write correct and maintainable code.</span></span>

<span data-ttu-id="4073d-106">F#programování primárně potřeba definovat typy a funkce, které se odvodit typ a automaticky zobecněný.</span><span class="sxs-lookup"><span data-stu-id="4073d-106">F# programming primarily involves defining types and functions that are type-inferred and generalized automatically.</span></span> <span data-ttu-id="4073d-107">Díky tomu váš výběr zůstat na domény a manipulace s nimi svoje data, spíše než o programování.</span><span class="sxs-lookup"><span data-stu-id="4073d-107">This allows your focus to remain on the problem domain and manipulating its data, rather than the details of programming.</span></span>

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

<span data-ttu-id="4073d-108">F#má řadu funkcí, včetně:</span><span class="sxs-lookup"><span data-stu-id="4073d-108">F# has numerous features, including:</span></span>

* <span data-ttu-id="4073d-109">Prostá syntaxe</span><span class="sxs-lookup"><span data-stu-id="4073d-109">Lightweight syntax</span></span>
* <span data-ttu-id="4073d-110">Neměnné ve výchozím nastavení</span><span class="sxs-lookup"><span data-stu-id="4073d-110">Immutable by default</span></span>
* <span data-ttu-id="4073d-111">Odvození typu proměnné a Automatická generalizace</span><span class="sxs-lookup"><span data-stu-id="4073d-111">Type inference and automatic generalization</span></span>
* <span data-ttu-id="4073d-112">Funkce první třídy</span><span class="sxs-lookup"><span data-stu-id="4073d-112">First-class functions</span></span>
* <span data-ttu-id="4073d-113">Výkonné datové typy</span><span class="sxs-lookup"><span data-stu-id="4073d-113">Powerful data types</span></span>
* <span data-ttu-id="4073d-114">Porovnávání vzorů</span><span class="sxs-lookup"><span data-stu-id="4073d-114">Pattern matching</span></span>
* <span data-ttu-id="4073d-115">Asynchronní programování</span><span class="sxs-lookup"><span data-stu-id="4073d-115">Async programming</span></span>

<span data-ttu-id="4073d-116">Úplná sada funkcí jsou dokumentovány v článku [ F# referenční informace k jazyku](language-reference/index.md).</span><span class="sxs-lookup"><span data-stu-id="4073d-116">A full set of features are documented in the [F# language reference](language-reference/index.md).</span></span>

## <a name="rich-data-types"></a><span data-ttu-id="4073d-117">Bohaté datové typy</span><span class="sxs-lookup"><span data-stu-id="4073d-117">Rich data types</span></span>

<span data-ttu-id="4073d-118">Datové typy, jako [záznamy](language-reference/records.md) a [Rozlišované sjednocení](language-reference/discriminated-unions.md) umožňují představují komplexní data a domén.</span><span class="sxs-lookup"><span data-stu-id="4073d-118">Data types such as [Records](language-reference/records.md) and [Discriminated Unions](language-reference/discriminated-unions.md) let you represent complex data and domains.</span></span>

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

<span data-ttu-id="4073d-119">F#záznamy a rozlišovaná sjednocení jsou nenulové, neměnné a srovnatelné ve výchozím nastavení, díky kterým jsou velmi snadné použití.</span><span class="sxs-lookup"><span data-stu-id="4073d-119">F# records and discriminated unions are non-null, immutable, and comparable by default, making them very easy to use.</span></span>

## <a name="enforced-correctness-with-functions-and-pattern-matching"></a><span data-ttu-id="4073d-120">Vynucené správnosti s funkcemi a porovnávání vzorů</span><span class="sxs-lookup"><span data-stu-id="4073d-120">Enforced correctness with functions and pattern matching</span></span>

<span data-ttu-id="4073d-121">F#funkce jsou snadno deklarovat a výkonné v praxi.</span><span class="sxs-lookup"><span data-stu-id="4073d-121">F# functions are easy to declare and powerful in practice.</span></span> <span data-ttu-id="4073d-122">V kombinaci s [porovnávání vzorů](language-reference/pattern-matching.md), umožňují definovat chování, jehož správnosti je vynucena kompilátorem.</span><span class="sxs-lookup"><span data-stu-id="4073d-122">When combined with [pattern matching](language-reference/pattern-matching.md), they allow you to define behavior whose correctness is enforced by the compiler.</span></span>

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

<span data-ttu-id="4073d-123">F#funkce jsou také první třídy, což znamená, mohou být předány jako parametry a vrácená z dalších funkcí.</span><span class="sxs-lookup"><span data-stu-id="4073d-123">F# functions are also first-class, meaning they can be passed as parameters and returned from other functions.</span></span>

## <a name="functions-to-define-operations-on-objects"></a><span data-ttu-id="4073d-124">Funkce k definování operací s objekty</span><span class="sxs-lookup"><span data-stu-id="4073d-124">Functions to define operations on objects</span></span>

<span data-ttu-id="4073d-125">F#obsahuje plnou podporu pro objekty, které jsou užitečné datové typy, pokud chcete kombinovat data a funkce.</span><span class="sxs-lookup"><span data-stu-id="4073d-125">F# has full support for objects, which are useful data types when you need to blend data and functionality.</span></span> <span data-ttu-id="4073d-126">F#funkce se používají k práci s objekty.</span><span class="sxs-lookup"><span data-stu-id="4073d-126">F# functions are used to manipulate objects.</span></span>

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

<span data-ttu-id="4073d-127">Místo psaní kódu, který je objektově orientované, v F#, budete často psát kód, který zpracovává objekty jako jiný typ dat pro funkce pro manipulaci s.</span><span class="sxs-lookup"><span data-stu-id="4073d-127">Rather than writing code that is object-oriented, in F#, you will often write code that treats objects as another data type for functions to manipulate.</span></span> <span data-ttu-id="4073d-128">Funkce, jako [obecných rozhraní](language-reference/interfaces.md), [výrazy objektu](language-reference/object-expressions.md)a rozumné využití [členy](language-reference/members/index.md) jsou běžné ve větší F# programy.</span><span class="sxs-lookup"><span data-stu-id="4073d-128">Features such as [generic interfaces](language-reference/interfaces.md), [object expressions](language-reference/object-expressions.md), and judicious use of [members](language-reference/members/index.md) are common in larger F# programs.</span></span>

## <a name="next-steps"></a><span data-ttu-id="4073d-129">Další kroky</span><span class="sxs-lookup"><span data-stu-id="4073d-129">Next steps</span></span>

<span data-ttu-id="4073d-130">Další informace o s větším počtem F# funkcí, podívejte se [ F# Tour](tour.md).</span><span class="sxs-lookup"><span data-stu-id="4073d-130">To learn more about a larger set of F# features, check out the [F# Tour](tour.md).</span></span>