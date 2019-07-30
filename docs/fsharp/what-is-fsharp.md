---
title: Co je F#
description: Přečtěte si, F# co je programovací jazyk a F# jaké je programování. Přečtěte si o bohatých datových typech, funkcích a o tom, jak se vejdou dohromady.
ms.date: 08/03/2018
ms.openlocfilehash: 0c576fe49fadebd68e4fc9d2b20ea8f0cb991af5
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630460"
---
# <a name="what-is-f"></a><span data-ttu-id="01f19-104">Co je F\#</span><span class="sxs-lookup"><span data-stu-id="01f19-104">What is F\#</span></span>

<span data-ttu-id="01f19-105">F#je funkční programovací jazyk, který usnadňuje psaní správného a udržovatelného kódu.</span><span class="sxs-lookup"><span data-stu-id="01f19-105">F# is a functional programming language that makes it easy to write correct and maintainable code.</span></span>

<span data-ttu-id="01f19-106">F#programování primárně zahrnuje definování typů a funkcí, které jsou odvozeny a zobecněny automaticky.</span><span class="sxs-lookup"><span data-stu-id="01f19-106">F# programming primarily involves defining types and functions that are type-inferred and generalized automatically.</span></span> <span data-ttu-id="01f19-107">Díky tomu může být zaostření v doméně problému a manipulaci s daty namísto podrobností programování.</span><span class="sxs-lookup"><span data-stu-id="01f19-107">This allows your focus to remain on the problem domain and manipulating its data, rather than the details of programming.</span></span>

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

<span data-ttu-id="01f19-108">F#obsahuje mnoho funkcí, včetně:</span><span class="sxs-lookup"><span data-stu-id="01f19-108">F# has numerous features, including:</span></span>

* <span data-ttu-id="01f19-109">Prostá syntaxe</span><span class="sxs-lookup"><span data-stu-id="01f19-109">Lightweight syntax</span></span>
* <span data-ttu-id="01f19-110">Neměnné ve výchozím nastavení</span><span class="sxs-lookup"><span data-stu-id="01f19-110">Immutable by default</span></span>
* <span data-ttu-id="01f19-111">Odvození typu a Automatická generalizace</span><span class="sxs-lookup"><span data-stu-id="01f19-111">Type inference and automatic generalization</span></span>
* <span data-ttu-id="01f19-112">Funkce první třídy</span><span class="sxs-lookup"><span data-stu-id="01f19-112">First-class functions</span></span>
* <span data-ttu-id="01f19-113">Výkonné datové typy</span><span class="sxs-lookup"><span data-stu-id="01f19-113">Powerful data types</span></span>
* <span data-ttu-id="01f19-114">Porovnávání vzorů</span><span class="sxs-lookup"><span data-stu-id="01f19-114">Pattern matching</span></span>
* <span data-ttu-id="01f19-115">Asynchronní programování</span><span class="sxs-lookup"><span data-stu-id="01f19-115">Async programming</span></span>

<span data-ttu-id="01f19-116">V [ F# referenční příručce](./language-reference/index.md)k jazyku jsou popsány úplné sady funkcí.</span><span class="sxs-lookup"><span data-stu-id="01f19-116">A full set of features are documented in the [F# language reference](./language-reference/index.md).</span></span>

## <a name="rich-data-types"></a><span data-ttu-id="01f19-117">Formátované datové typy</span><span class="sxs-lookup"><span data-stu-id="01f19-117">Rich data types</span></span>

<span data-ttu-id="01f19-118">Datové typy, jako jsou [záznamy](./language-reference/records.md) a [rozlišené sjednocení](./language-reference/discriminated-unions.md) , umožňují reprezentovat složitá data a domény.</span><span class="sxs-lookup"><span data-stu-id="01f19-118">Data types such as [Records](./language-reference/records.md) and [Discriminated Unions](./language-reference/discriminated-unions.md) let you represent complex data and domains.</span></span>

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

<span data-ttu-id="01f19-119">F#záznamy a rozlišené sjednocení jsou ve výchozím nastavení nenulové, neměnné a srovnatelné, takže je velmi snadné je používat.</span><span class="sxs-lookup"><span data-stu-id="01f19-119">F# records and discriminated unions are non-null, immutable, and comparable by default, making them very easy to use.</span></span>

## <a name="enforced-correctness-with-functions-and-pattern-matching"></a><span data-ttu-id="01f19-120">Vynutila správnost pomocí funkcí a porovnávání vzorů.</span><span class="sxs-lookup"><span data-stu-id="01f19-120">Enforced correctness with functions and pattern matching</span></span>

<span data-ttu-id="01f19-121">F#funkce jsou v praxi snadno deklarované a výkonné.</span><span class="sxs-lookup"><span data-stu-id="01f19-121">F# functions are easy to declare and powerful in practice.</span></span> <span data-ttu-id="01f19-122">V kombinaci se [porovnáváním vzorů](./language-reference/pattern-matching.md)umožňuje definovat chování, jehož správnost je vynutila kompilátorem.</span><span class="sxs-lookup"><span data-stu-id="01f19-122">When combined with [pattern matching](./language-reference/pattern-matching.md), they allow you to define behavior whose correctness is enforced by the compiler.</span></span>

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

<span data-ttu-id="01f19-123">F#funkce jsou také první třídy, což znamená, že mohou být předány jako parametry a vráceny z jiných funkcí.</span><span class="sxs-lookup"><span data-stu-id="01f19-123">F# functions are also first-class, meaning they can be passed as parameters and returned from other functions.</span></span>

## <a name="functions-to-define-operations-on-objects"></a><span data-ttu-id="01f19-124">Funkce pro definování operací s objekty</span><span class="sxs-lookup"><span data-stu-id="01f19-124">Functions to define operations on objects</span></span>

<span data-ttu-id="01f19-125">F#má plnou podporu pro objekty, které jsou užitečné datové typy, pokud potřebujete Blend data a funkce.</span><span class="sxs-lookup"><span data-stu-id="01f19-125">F# has full support for objects, which are useful data types when you need to blend data and functionality.</span></span> <span data-ttu-id="01f19-126">F#funkce se používají k manipulaci s objekty.</span><span class="sxs-lookup"><span data-stu-id="01f19-126">F# functions are used to manipulate objects.</span></span>

```fsharp
type Set<[<EqualityConditionOn>] 'T when 'T: comparison>(elements: seq<'T>) =
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

<span data-ttu-id="01f19-127">Místo psaní kódu, který je objektově orientovaný, v F#nástroji budete často psát kód, který bude zpracovávat objekty jako jiný datový typ pro zpracování funkcí.</span><span class="sxs-lookup"><span data-stu-id="01f19-127">Rather than writing code that is object-oriented, in F#, you will often write code that treats objects as another data type for functions to manipulate.</span></span> <span data-ttu-id="01f19-128">Funkce, jako jsou [Obecná rozhraní](./language-reference/interfaces.md), [výrazy objektů](./language-reference/object-expressions.md)a rozumné použití [členů](./language-reference/members/index.md) , jsou běžné ve větších F# programech.</span><span class="sxs-lookup"><span data-stu-id="01f19-128">Features such as [generic interfaces](./language-reference/interfaces.md), [object expressions](./language-reference/object-expressions.md), and judicious use of [members](./language-reference/members/index.md) are common in larger F# programs.</span></span>

## <a name="next-steps"></a><span data-ttu-id="01f19-129">Další postup</span><span class="sxs-lookup"><span data-stu-id="01f19-129">Next steps</span></span>

<span data-ttu-id="01f19-130">Pokud se chcete dozvědět víc o větší sadě F# funkcí, podívejte se na [ F# prohlídku](tour.md).</span><span class="sxs-lookup"><span data-stu-id="01f19-130">To learn more about a larger set of F# features, check out the [F# Tour](tour.md).</span></span>
