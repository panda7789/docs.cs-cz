---
title: 'Výsledky (F #)'
description: 'Zjistěte, jak pomocí F # "Výsledek" typ můžete napsat kód chyby proti chybám.'
ms.date: 04/24/2017
ms.openlocfilehash: a7ce2e1f6b8c6a32d99a2feaf9547c4b67b152b8
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43749246"
---
# <a name="results"></a>výsledky

Od verze F # 4.1, je `Result<'T,'TFailure>` typ, který můžete použít k zápisu chybové proti chybám kódu, který se může skládat.

## <a name="syntax"></a>Syntaxe

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

Všimněte si, že je typ výsledku [rozlišovaná sjednocení na základě struktury](discriminated-unions.md#struct-discriminated-unions), což je jiný, která byla zavedena v F # 4.1.  Strukturální rovnost sémantika tady.

`Result` Typ se obvykle používá v monadic zpracování chyb, které se často označuje jako [železniční objektově orientovaného programování](https://swlaschin.gitbooks.io/fsharpforfunandprofit/content/posts/recipe-part2.html) v rámci komunity F #.  Následující příklad jednoduchého dotazu ukazuje tento přístup.

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

Jak vidíte, je poměrně snadné pro zřetězení různé funkce ověřování, pokud vynutíte, aby všechna vrácení `Result`.  To vám umožňuje rozdělit funkce, jako jsou to na malé části, které jsou složení, podle potřeby je možné.  To má také přidanou hodnotou *vynucování* použití [porovnávání vzorů](pattern-matching.md) na konci kruhové ověřování, což na oplátku vynucuje vyšší stupeň správnosti programu.

## <a name="see-also"></a>Viz také:

- [Rozlišovaná sjednocení](discriminated-unions.md)
- [Porovnávání vzorů](pattern-matching.md)
