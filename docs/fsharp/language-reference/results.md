---
title: 'Výsledky (F #)'
description: "Další informace o použití F #, způsobit' typ můžete napsat kód chyby proti chybám."
author: cartermp
ms.author: phcart
ms.date: 04/24/2017
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 35fd1d3b1590291e18aa28460cf5939606c21d3a
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
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

Jak můžete vidět, je poměrně snadné různé funkce ověřování řetězu společně, pokud mají všechny vrátit vynutíte `Result`.  Díky tomu se rozdělit funkcí jako je to na malé části, které jsou složení, je možné podle potřeby.  To má také přidané hodnoty *vynucování* použití [porovnávání vzorů](pattern-matching.md) na konci zaokrouhlit ověření, což na oplátku vynucuje vyšší stupeň správnost programu.

## <a name="see-also"></a>Viz také

[Rozlišovaná sjednocení](discriminated-unions.md)

[Porovnávání vzorů](pattern-matching.md)
