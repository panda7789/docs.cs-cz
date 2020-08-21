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
# <a name="results"></a>Výsledky

`Result<'T,'TFailure>`Typ umožňuje napsat kód odolný proti chybám, který může být složen.

## <a name="syntax"></a>Syntax

```fsharp
// The definition of Result in FSharp.Core
[<StructuralEquality; StructuralComparison>]
[<CompiledName("FSharpResult`2")>]
[<Struct>]
type Result<'T,'TError> =
    | Ok of ResultValue:'T
    | Error of ErrorValue:'TError
```

## <a name="remarks"></a>Poznámky

Prohlédněte si [`Result`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-resultmodule.html) modul pro integrovaný kombinátory pro `Result` . textový.

Všimněte si, že typ výsledku je [struktura s rozlišeným sjednocením](discriminated-unions.md#struct-discriminated-unions). Tady se vztahují strukturální sémantiky rovnosti.

`Result`Typ se obvykle používá při zpracování chyb monadic, což se často označuje jako [železniční programování](https://swlaschin.gitbooks.io/fsharpforfunandprofit/content/posts/recipe-part2.html) v rámci komunity F #.  Tento přístup ukazuje následující triviální příklad.

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

Jak vidíte, je poměrně snadné zřetězit se k různým funkcím ověřování, pokud je vynutíte, aby vracely `Result` .  To umožňuje přerušit funkčnost, jako je to v malých částech, které jsou sestavené tak, jak je potřebujete.  To má také přidanou hodnotu *vynucení* použití [porovnávání se vzorem](pattern-matching.md) na konci kulatého obhodnocení, které v nástroji vynucuje vyšší stupeň správnosti programu.

## <a name="see-also"></a>Viz také:

- [Rozlišovaná sjednocení](discriminated-unions.md)
- [Porovnávání vzorů](pattern-matching.md)
