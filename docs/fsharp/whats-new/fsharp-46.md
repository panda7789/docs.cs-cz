---
title: Co je nového v F# 4,6 – F# příručka
description: Získejte přehled o nových funkcích dostupných v F# 4,6.
ms.date: 11/27/2019
ms.openlocfilehash: 81d3e988d044cb16f8ec079118fd0ede2dabc587
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/28/2019
ms.locfileid: "74644080"
---
# <a name="whats-new-in-f-46"></a><span data-ttu-id="89b92-103">Co je nového v F# 4,6</span><span class="sxs-lookup"><span data-stu-id="89b92-103">What's new in F# 4.6</span></span>

<span data-ttu-id="89b92-104">F#4,6 přidává k F# jazyku více vylepšení.</span><span class="sxs-lookup"><span data-stu-id="89b92-104">F# 4.6 adds multiple improvements to the F# language.</span></span>

## <a name="get-started"></a><span data-ttu-id="89b92-105">Začínáme</span><span class="sxs-lookup"><span data-stu-id="89b92-105">Get started</span></span>

<span data-ttu-id="89b92-106">F#4,6 je k dispozici ve všech distribucích .NET Core a nástrojích sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="89b92-106">F# 4.6 is available in all .NET Core distributions and Visual Studio tooling.</span></span> <span data-ttu-id="89b92-107">Začněte [s F# ](../get-started/index.md) a získejte další informace.</span><span class="sxs-lookup"><span data-stu-id="89b92-107">[Get started with F#](../get-started/index.md) to learn more.</span></span>

## <a name="anonymous-records"></a><span data-ttu-id="89b92-108">Anonymní záznamy</span><span class="sxs-lookup"><span data-stu-id="89b92-108">Anonymous records</span></span>

<span data-ttu-id="89b92-109">[Anonymní záznamy](../language-reference/anonymous-records.md) jsou nový F# typ zavedený v F# 4,6.</span><span class="sxs-lookup"><span data-stu-id="89b92-109">[Anonymous records](../language-reference/anonymous-records.md) are a new kind of F# type introduced in F# 4.6.</span></span> <span data-ttu-id="89b92-110">Jsou jednoduché agregované pojmenované hodnoty, které není nutné deklarovat před použitím.</span><span class="sxs-lookup"><span data-stu-id="89b92-110">They are simple aggregates of named values that don't need to be declared before use.</span></span> <span data-ttu-id="89b92-111">Můžete je deklarovat buď jako struktury, nebo na typy odkazů.</span><span class="sxs-lookup"><span data-stu-id="89b92-111">You can declare them as either structs or reference types.</span></span> <span data-ttu-id="89b92-112">Ve výchozím nastavení se jedná o typy odkazů.</span><span class="sxs-lookup"><span data-stu-id="89b92-112">They're reference types by default.</span></span>

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

<span data-ttu-id="89b92-113">Mohou být také deklarovány jako struktury pro případy, kdy chcete seskupit typy hodnot a fungují ve scénářích, které jsou závislé na výkonu:</span><span class="sxs-lookup"><span data-stu-id="89b92-113">They can also be declared as structs for when you want to group value types and are operating in performance-sensitive scenarios:</span></span>

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

<span data-ttu-id="89b92-114">Jsou poměrně výkonné a dají se použít v mnoha scénářích.</span><span class="sxs-lookup"><span data-stu-id="89b92-114">They're quite powerful and can be used in numerous scenarios.</span></span> <span data-ttu-id="89b92-115">Další informace najdete v [anonymních záznamech](../language-reference/anonymous-records.md).</span><span class="sxs-lookup"><span data-stu-id="89b92-115">Learn more at [Anonymous records](../language-reference/anonymous-records.md).</span></span>

## <a name="valueoption-functions"></a><span data-ttu-id="89b92-116">Funkce ValueOption</span><span class="sxs-lookup"><span data-stu-id="89b92-116">ValueOption functions</span></span>

<span data-ttu-id="89b92-117">Typ ValueOption přidaný v F# 4,5 teď má "paritu funkcí vázaných na modul" s typem možnosti.</span><span class="sxs-lookup"><span data-stu-id="89b92-117">The ValueOption type added in F# 4.5 now has "module-bound function parity" with the Option type.</span></span> <span data-ttu-id="89b92-118">Mezi příklady běžně používaných příkladů patří:</span><span class="sxs-lookup"><span data-stu-id="89b92-118">Some of the more commonly-used examples are as follows:</span></span>

```fsharp
// Multiply a value option by 2 if it has  value
let xOpt = ValueSome 99
let result = xOpt |> ValueOption.map (fun v -> v * 2)

// Reverse a string if it exists
let strOpt = ValueSome "Mirror image"
let reverse (str: string) =
    match str with
    | null
    | "" -> None
    | s ->
        str.ToCharArray()
        |> Array.rev
        |> string
        |> Some

let reversedString = strOpt |> Option.bind reverse
```

<span data-ttu-id="89b92-119">To umožňuje používat ValueOption stejně jako možnost ve scénářích, kde se s typem hodnoty zvyšuje výkon.</span><span class="sxs-lookup"><span data-stu-id="89b92-119">This allows for ValueOption to be used just like Option in scenarios where having a value type improves performance.</span></span>
