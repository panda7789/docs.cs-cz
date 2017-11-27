---
title: "Výsledky (F #)"
description: "Další informace o použití F #, způsobit' typ můžete napsat kód chyby proti chybám."
keywords: "Visual f #, f #, funkční programování"
author: cartermp
ms.author: phcart
ms.date: 04/24/2017
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: a15b5cf1-9055-4481-918c-4c8a051b5829
ms.openlocfilehash: 26478ccfbf88d43c0b194e77d9aacc313515283f
ms.sourcegitcommit: 8d14e8c1b15009330c9880f8523686158924e1a4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/14/2017
---
# <a name="results"></a><span data-ttu-id="3879a-104">Výsledky</span><span class="sxs-lookup"><span data-stu-id="3879a-104">Results</span></span>

<span data-ttu-id="3879a-105">Od verze 4.1 F #, je `Result<'T,'TFailure>` typ, který můžete použít k zápisu-chybám kódu, který může být složené.</span><span class="sxs-lookup"><span data-stu-id="3879a-105">Starting with F# 4.1, there is a `Result<'T,'TFailure>` type which you can use for writing error-tolerant code which can be composed.</span></span>

## <a name="syntax"></a><span data-ttu-id="3879a-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3879a-106">Syntax</span></span>

```fsharp
// The definition of Result in FSharp.Core
[<StructuralEquality; StructuralComparison>]
[<CompiledName("FSharpResult`2")>]
[<Struct>]
type Result<'T,'TError> = 
    | Ok of ResultValue:'T 
    | Error of ErrorValue:'TError
```

## <a name="remarks"></a><span data-ttu-id="3879a-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3879a-107">Remarks</span></span>

<span data-ttu-id="3879a-108">Všimněte si, že je typ výsledku [struktura rozlišované sjednocení](discriminated-unions.md#struct-discriminated-unions), což je jiné funkce, zavedená v F # 4.1.</span><span class="sxs-lookup"><span data-stu-id="3879a-108">Note that the result type is a [struct discriminated union](discriminated-unions.md#struct-discriminated-unions), which is another feature introduced in F# 4.1.</span></span>  <span data-ttu-id="3879a-109">Strukturální rovnosti sémantiku použita zde.</span><span class="sxs-lookup"><span data-stu-id="3879a-109">Structural equality semantics apply here.</span></span>

<span data-ttu-id="3879a-110">`Result` Typ se obvykle používá v monadic zpracování chyb, které se často označuje jako [železniční orientované programování](https://swlaschin.gitbooks.io/fsharpforfunandprofit/content/posts/recipe-part2.html) v rámci komunity F #.</span><span class="sxs-lookup"><span data-stu-id="3879a-110">The `Result` type is typically used in monadic error-handling, which is often referred to as [Railway-oriented Programming](https://swlaschin.gitbooks.io/fsharpforfunandprofit/content/posts/recipe-part2.html) within the F# community.</span></span>  <span data-ttu-id="3879a-111">Následující příklad trivial ukazuje tento přístup.</span><span class="sxs-lookup"><span data-stu-id="3879a-111">The following trivial example demonstrates this approach.</span></span>

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
    | String.Empty -> Error "Name is empty."
    | "bananas" -> Error "Bananas is not a name."
    | _ -> Ok req

// Similarly, define some email validation logic.
let validateEmail req =
    match req.Email with
    | null -> Error "No email found."
    | String.Empty -> Error "Email is empty."
    | s when s.EndsWith("bananas.com") -> Error "No email from bananas.com is allowed."
    | _ -> OK req

let validateRequest reqResult =
    reqResult 
    |> Result.bind validateName
    |> Result.bind validateEmail

let test() = 
    // Now, create a Request and pattern match on the result.
    let req1 = { Name = "Phillip"; Email = "phillip@contoso.biz" }
    let res1 = validateRequest (OK req1)
    match res1 with
    | Ok req -> printfn "My request was valid! Name: %s Email %s" req1.Name req1.Email
    | Error e -> printfn "Error: %s" e
    // Prints " "My request was valid!  Name: Phillip Email: phillip@consoto.biz"

    let req2 = { Name = "Phillip"; Email = "phillip@bananas.com" }
    let res2 = validateRequest (OK req2)
    match res2 with
    | Ok req -> printfn "My request was valid! Name: %s Email %s" req1.Name req1.Email
    | Error e -> printfn "Error: %s" e
    // Prints: "Error: No email from bananas.com is allowed."

test()
```

<span data-ttu-id="3879a-112">Jak můžete vidět, je poměrně snadné různé funkce ověřování řetězu společně, pokud mají všechny vrátit vynutíte `Result`.</span><span class="sxs-lookup"><span data-stu-id="3879a-112">As you can see, it's quite easy to chain together various validation functions if you force them all to return a `Result`.</span></span>  <span data-ttu-id="3879a-113">Díky tomu se rozdělit funkcí jako je to na malé části, které jsou složení, je možné podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="3879a-113">This lets you break up functionality like this into small pieces which are as composable as you need them to be.</span></span>  <span data-ttu-id="3879a-114">To má také přidané hodnoty *vynucování* použití [porovnávání vzorů](pattern-matching.md) na konci zaokrouhlit ověření, což na oplátku vynucuje vyšší stupeň správnost programu.</span><span class="sxs-lookup"><span data-stu-id="3879a-114">This also has the added value of *enforcing* the use of [pattern matching](pattern-matching.md) at the end of a round of validation, which in turns enforces a higher degree of program correctness.</span></span>

## <a name="see-also"></a><span data-ttu-id="3879a-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="3879a-115">See Also</span></span>

[<span data-ttu-id="3879a-116">Rozlišovaná sjednocení</span><span class="sxs-lookup"><span data-stu-id="3879a-116">Discriminated Unions</span></span>](discriminated-unions.md)

[<span data-ttu-id="3879a-117">Shoda vzoru</span><span class="sxs-lookup"><span data-stu-id="3879a-117">Pattern Matching</span></span>](pattern-matching.md)
