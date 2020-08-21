---
title: Výsledky
description: 'Naučte se používat typ výsledek F #, který vám umožní napsat kód odolný proti chybám.'
ms.date: 08/13/2020
ms.openlocfilehash: d69e6ddc37bcf5cb5fc28644d59a11a822b83faa
ms.sourcegitcommit: c4a15c6c4ecbb8a46ad4e67d9b3ab9b8b031d849
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/20/2020
ms.locfileid: "88656915"
---
# <a name="results"></a><span data-ttu-id="a652c-103">Výsledky</span><span class="sxs-lookup"><span data-stu-id="a652c-103">Results</span></span>

<span data-ttu-id="a652c-104">`Result<'T,'TFailure>`Typ umožňuje napsat kód odolný proti chybám, který může být složen.</span><span class="sxs-lookup"><span data-stu-id="a652c-104">The `Result<'T,'TFailure>` type lets you write error-tolerant code that can be composed.</span></span>

## <a name="syntax"></a><span data-ttu-id="a652c-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="a652c-105">Syntax</span></span>

```fsharp
// The definition of Result in FSharp.Core
[<StructuralEquality; StructuralComparison>]
[<CompiledName("FSharpResult`2")>]
[<Struct>]
type Result<'T,'TError> =
    | Ok of ResultValue:'T
    | Error of ErrorValue:'TError
```

## <a name="remarks"></a><span data-ttu-id="a652c-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a652c-106">Remarks</span></span>

<span data-ttu-id="a652c-107">Prohlédněte si [`Result`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-resultmodule.html) modul pro integrovaný kombinátory pro `Result` .</span><span class="sxs-lookup"><span data-stu-id="a652c-107">See the [`Result`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-resultmodule.html) module for the built-in combinators for the `Result`.</span></span> <span data-ttu-id="a652c-108">textový.</span><span class="sxs-lookup"><span data-stu-id="a652c-108">type.</span></span>

<span data-ttu-id="a652c-109">Všimněte si, že typ výsledku je [struktura s rozlišeným sjednocením](discriminated-unions.md#struct-discriminated-unions).</span><span class="sxs-lookup"><span data-stu-id="a652c-109">Note that the result type is a [struct discriminated union](discriminated-unions.md#struct-discriminated-unions).</span></span> <span data-ttu-id="a652c-110">Tady se vztahují strukturální sémantiky rovnosti.</span><span class="sxs-lookup"><span data-stu-id="a652c-110">Structural equality semantics apply here.</span></span>

<span data-ttu-id="a652c-111">`Result`Typ se obvykle používá při zpracování chyb monadic, což se často označuje jako [železniční programování](https://swlaschin.gitbooks.io/fsharpforfunandprofit/content/posts/recipe-part2.html) v rámci komunity F #.</span><span class="sxs-lookup"><span data-stu-id="a652c-111">The `Result` type is typically used in monadic error-handling, which is often referred to as [Railway-oriented Programming](https://swlaschin.gitbooks.io/fsharpforfunandprofit/content/posts/recipe-part2.html) within the F# community.</span></span>  <span data-ttu-id="a652c-112">Tento přístup ukazuje následující triviální příklad.</span><span class="sxs-lookup"><span data-stu-id="a652c-112">The following trivial example demonstrates this approach.</span></span>

```fsharp
// Define a simple type which has fields that can be validated
type Request =
    { Name: string
      Email: string }

// Define some logic for what defines a valid name.
//
// Generates a Result which is an Ok if the name validates;
// otherwise, it generates a Result which is an Error.
let validateName req =
    match req.Name with
    | null -> Error "No name found."
    | "" -> Error "Name is empty."
    | "bananas" -> Error "Bananas is not a name."
    | _ -> Ok req

// Similarly, define some email validation logic.
let validateEmail req =
    match req.Email with
    | null -> Error "No email found."
    | "" -> Error "Email is empty."
    | s when s.EndsWith("bananas.com") -> Error "No email from bananas.com is allowed."
    | _ -> Ok req

let validateRequest reqResult =
    reqResult
    |> Result.bind validateName
    |> Result.bind validateEmail

let test() =
    // Now, create a Request and pattern match on the result.
    let req1 = { Name = "Phillip"; Email = "phillip@contoso.biz" }
    let res1 = validateRequest (Ok req1)
    match res1 with
    | Ok req -> printfn "My request was valid! Name: %s Email %s" req.Name req.Email
    | Error e -> printfn "Error: %s" e
    // Prints: "My request was valid!  Name: Phillip Email: phillip@consoto.biz"

    let req2 = { Name = "Phillip"; Email = "phillip@bananas.com" }
    let res2 = validateRequest (Ok req2)
    match res2 with
    | Ok req -> printfn "My request was valid! Name: %s Email %s" req.Name req.Email
    | Error e -> printfn "Error: %s" e
    // Prints: "Error: No email from bananas.com is allowed."

test()
```

<span data-ttu-id="a652c-113">Jak vidíte, je poměrně snadné zřetězit se k různým funkcím ověřování, pokud je vynutíte, aby vracely `Result` .</span><span class="sxs-lookup"><span data-stu-id="a652c-113">As you can see, it's quite easy to chain together various validation functions if you force them all to return a `Result`.</span></span>  <span data-ttu-id="a652c-114">To umožňuje přerušit funkčnost, jako je to v malých částech, které jsou sestavené tak, jak je potřebujete.</span><span class="sxs-lookup"><span data-stu-id="a652c-114">This lets you break up functionality like this into small pieces which are as composable as you need them to be.</span></span>  <span data-ttu-id="a652c-115">To má také přidanou hodnotu *vynucení* použití [porovnávání se vzorem](pattern-matching.md) na konci kulatého obhodnocení, které v nástroji vynucuje vyšší stupeň správnosti programu.</span><span class="sxs-lookup"><span data-stu-id="a652c-115">This also has the added value of *enforcing* the use of [pattern matching](pattern-matching.md) at the end of a round of validation, which in turns enforces a higher degree of program correctness.</span></span>

## <a name="see-also"></a><span data-ttu-id="a652c-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a652c-116">See also</span></span>

- [<span data-ttu-id="a652c-117">Rozlišovaná sjednocení</span><span class="sxs-lookup"><span data-stu-id="a652c-117">Discriminated Unions</span></span>](discriminated-unions.md)
- [<span data-ttu-id="a652c-118">Porovnávání vzorů</span><span class="sxs-lookup"><span data-stu-id="a652c-118">Pattern Matching</span></span>](pattern-matching.md)
