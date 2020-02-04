---
title: Co je nového v F# 4,6 – F# příručka
description: Získejte přehled o nových funkcích dostupných v F# 4,6.
ms.date: 11/27/2019
ms.openlocfilehash: 620c1edd8ea212fee306a02d5844b6b322808251
ms.sourcegitcommit: 19014f9c081ca2ff19652ca12503828db8239d48
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/04/2020
ms.locfileid: "76980389"
---
# <a name="whats-new-in-f-46"></a>Co je nového v F# 4,6

F#4,6 přidává k F# jazyku více vylepšení.

## <a name="get-started"></a>Začínáme

F#4,6 je k dispozici ve všech distribucích .NET Core a nástrojích sady Visual Studio. Začněte [s F# ](../get-started/index.md) a získejte další informace.

## <a name="anonymous-records"></a>Anonymní záznamy

[Anonymní záznamy](../language-reference/anonymous-records.md) jsou nový F# typ zavedený v F# 4,6. Jsou jednoduché agregované pojmenované hodnoty, které není nutné deklarovat před použitím. Můžete je deklarovat buď jako struktury, nebo na typy odkazů. Ve výchozím nastavení se jedná o typy odkazů.

```fsharp
open System

let getCircleStats radius =
    let d = radius * 2.0
    let a = Math.PI * (radius ** 2.0)
    let c = 2.0 * Math.PI * radius

    {| Diameter = d; Area = a; Circumference = c |}

let r = 2.0
let stats = getCircleStats r
printfn "Circle with radius: %f has diameter %f, area %f, and circumference %f"
    r stats.Diameter stats.Area stats.Circumference
```

Mohou být také deklarovány jako struktury pro případy, kdy chcete seskupit typy hodnot a fungují ve scénářích, které jsou závislé na výkonu:

```fsharp
open System

let getCircleStats radius =
    let d = radius * 2.0
    let a = Math.PI * (radius ** 2.0)
    let c = 2.0 * Math.PI * radius

    struct {| Diameter = d; Area = a; Circumference = c |}

let r = 2.0
let stats = getCircleStats r
printfn "Circle with radius: %f has diameter %f, area %f, and circumference %f"
    r stats.Diameter stats.Area stats.Circumference
```

Jsou poměrně výkonné a dají se použít v mnoha scénářích. Další informace najdete v [anonymních záznamech](../language-reference/anonymous-records.md).

## <a name="valueoption-functions"></a>Funkce ValueOption

Typ ValueOption přidaný v F# 4,5 teď má "paritu funkcí vázaných na modul" s typem možnosti. Mezi příklady běžně používaných příkladů patří:

```fsharp
// Multiply a value option by 2 if it has  value
let xOpt = ValueSome 99
let result = xOpt |> ValueOption.map (fun v -> v * 2)

// Reverse a string if it exists
let strOpt = ValueSome "Mirror image"
let reverse (str: string) =
    match str with
    | null
    | "" -> ValueNone
    | s ->
        str.ToCharArray()
        |> Array.rev
        |> string
        |> ValueSome

let reversedString = strOpt |> ValueOption.bind reverse
```

To umožňuje používat ValueOption stejně jako možnost ve scénářích, kde se s typem hodnoty zvyšuje výkon.
