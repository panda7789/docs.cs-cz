---
title: 'Výsledky (F #)'
description: "Další informace o použití F #, způsobit' typ můžete napsat kód chyby proti chybám."
ms.date: 04/24/2017
ms.openlocfilehash: 432e420ba7c2005caa46250dde82c2c67c9d3ae3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33563005"
---
# <a name="results"></a><span data-ttu-id="d8258-103">Výsledky</span><span class="sxs-lookup"><span data-stu-id="d8258-103">Results</span></span>

<span data-ttu-id="d8258-104">Od verze 4.1 F #, je `Result<'T,'TFailure>` typ, který můžete použít k zápisu-chybám kódu, který může být složené.</span><span class="sxs-lookup"><span data-stu-id="d8258-104">Starting with F# 4.1, there is a `Result<'T,'TFailure>` type which you can use for writing error-tolerant code which can be composed.</span></span>

## <a name="syntax"></a><span data-ttu-id="d8258-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d8258-105">Syntax</span></span>

```fsharp
// The definition of Result in FSharp.Core
[<StructuralEquality; StructuralComparison>]
[<CompiledName("FSharpResult`2")>]
[<Struct>]
type Result<'T,'TError> = 
    | Ok of ResultValue:'T 
    | Error of ErrorValue:'TError
```

## <a name="remarks"></a><span data-ttu-id="d8258-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d8258-106">Remarks</span></span>

<span data-ttu-id="d8258-107">Všimněte si, že je typ výsledku [struktura rozlišované sjednocení](discriminated-unions.md#struct-discriminated-unions), což je jiné funkce, zavedená v F # 4.1.</span><span class="sxs-lookup"><span data-stu-id="d8258-107">Note that the result type is a [struct discriminated union](discriminated-unions.md#struct-discriminated-unions), which is another feature introduced in F# 4.1.</span></span>  <span data-ttu-id="d8258-108">Strukturální rovnosti sémantiku použita zde.</span><span class="sxs-lookup"><span data-stu-id="d8258-108">Structural equality semantics apply here.</span></span>

<span data-ttu-id="d8258-109">`Result` Typ se obvykle používá v monadic zpracování chyb, které se často označuje jako [železniční orientované programování](https://swlaschin.gitbooks.io/fsharpforfunandprofit/content/posts/recipe-part2.html) v rámci komunity F #.</span><span class="sxs-lookup"><span data-stu-id="d8258-109">The `Result` type is typically used in monadic error-handling, which is often referred to as [Railway-oriented Programming](https://swlaschin.gitbooks.io/fsharpforfunandprofit/content/posts/recipe-part2.html) within the F# community.</span></span>  <span data-ttu-id="d8258-110">Následující příklad trivial ukazuje tento přístup.</span><span class="sxs-lookup"><span data-stu-id="d8258-110">The following trivial example demonstrates this approach.</span></span>

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

<span data-ttu-id="d8258-111">Jak můžete vidět, je poměrně snadné různé funkce ověřování řetězu společně, pokud mají všechny vrátit vynutíte `Result`.</span><span class="sxs-lookup"><span data-stu-id="d8258-111">As you can see, it's quite easy to chain together various validation functions if you force them all to return a `Result`.</span></span>  <span data-ttu-id="d8258-112">Díky tomu se rozdělit funkcí jako je to na malé části, které jsou složení, je možné podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="d8258-112">This lets you break up functionality like this into small pieces which are as composable as you need them to be.</span></span>  <span data-ttu-id="d8258-113">To má také přidané hodnoty *vynucování* použití [porovnávání vzorů](pattern-matching.md) na konci zaokrouhlit ověření, což na oplátku vynucuje vyšší stupeň správnost programu.</span><span class="sxs-lookup"><span data-stu-id="d8258-113">This also has the added value of *enforcing* the use of [pattern matching](pattern-matching.md) at the end of a round of validation, which in turns enforces a higher degree of program correctness.</span></span>

## <a name="see-also"></a><span data-ttu-id="d8258-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="d8258-114">See Also</span></span>

[<span data-ttu-id="d8258-115">Rozlišovaná sjednocení</span><span class="sxs-lookup"><span data-stu-id="d8258-115">Discriminated Unions</span></span>](discriminated-unions.md)

[<span data-ttu-id="d8258-116">Porovnávání vzorů</span><span class="sxs-lookup"><span data-stu-id="d8258-116">Pattern Matching</span></span>](pattern-matching.md)
