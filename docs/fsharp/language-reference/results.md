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
# <a name="results"></a>Výsledky

Od verze 4.1 F #, je `Result<'T,'TFailure>` typ, který můžete použít k zápisu-chybám kódu, který může být složené.

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

Všimněte si, že je typ výsledku [struktura rozlišované sjednocení](discriminated-unions.md#struct-discriminated-unions), což je jiné funkce, zavedená v F # 4.1.  Strukturální rovnosti sémantiku použita zde.

`Result` Typ se obvykle používá v monadic zpracování chyb, které se často označuje jako [železniční orientované programování](https://swlaschin.gitbooks.io/fsharpforfunandprofit/content/posts/recipe-part2.html) v rámci komunity F #.  Následující příklad trivial ukazuje tento přístup.

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

Jak můžete vidět, je poměrně snadné různé funkce ověřování řetězu společně, pokud mají všechny vrátit vynutíte `Result`.  Díky tomu se rozdělit funkcí jako je to na malé části, které jsou složení, je možné podle potřeby.  To má také přidané hodnoty *vynucování* použití [porovnávání vzorů](pattern-matching.md) na konci zaokrouhlit ověření, což na oplátku vynucuje vyšší stupeň správnost programu.

## <a name="see-also"></a>Viz také

[Rozlišovaná sjednocení](discriminated-unions.md)

[Shoda vzoru](pattern-matching.md)
