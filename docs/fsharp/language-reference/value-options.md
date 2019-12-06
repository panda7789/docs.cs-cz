---
title: Možnosti pro hodnoty
description: Přečtěte si F# o typu možnosti hodnoty, což je verze struktury typu možnosti.
ms.date: 12/04/2019
ms.openlocfilehash: 0e9882ab4acdf2757705ef6022516d3572d87ef2
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/05/2019
ms.locfileid: "74837113"
---
# <a name="value-options"></a><span data-ttu-id="ece75-103">Možnosti pro hodnoty</span><span class="sxs-lookup"><span data-stu-id="ece75-103">Value Options</span></span>

<span data-ttu-id="ece75-104">Hodnota možnosti typ v se F# používá v případě, že jsou uloženy následující dvě okolnosti:</span><span class="sxs-lookup"><span data-stu-id="ece75-104">The Value Option type in F# is used when the following two circumstances hold:</span></span>

1. <span data-ttu-id="ece75-105">Scénář je vhodný pro [ F# možnost](options.md).</span><span class="sxs-lookup"><span data-stu-id="ece75-105">A scenario is appropriate for an [F# Option](options.md).</span></span>
2. <span data-ttu-id="ece75-106">Použití struktury poskytuje ve vašem scénáři výhodu výkonu.</span><span class="sxs-lookup"><span data-stu-id="ece75-106">Using a struct provides a performance benefit in your scenario.</span></span>

<span data-ttu-id="ece75-107">Ne všechny scénáře citlivé na výkon jsou "vyřešené" pomocí struktur.</span><span class="sxs-lookup"><span data-stu-id="ece75-107">Not all performance-sensitive scenarios are "solved" by using structs.</span></span> <span data-ttu-id="ece75-108">Je nutné vzít v úvahu další náklady na kopírování při jejich použití namísto odkazových typů.</span><span class="sxs-lookup"><span data-stu-id="ece75-108">You must consider the additional cost of copying when using them instead of reference types.</span></span> <span data-ttu-id="ece75-109">Velké F# programy však obvykle vytvářejí mnoho volitelných typů, které jsou přenášeny prostřednictvím aktivních cest, a v takových případech mohou struktury často vracet lepší celkový výkon po celou dobu životnosti programu.</span><span class="sxs-lookup"><span data-stu-id="ece75-109">However, large F# programs commonly instantiate many optional types that flow through hot paths, and in such cases, structs can often yield better overall performance over the lifetime of a program.</span></span>

## <a name="definition"></a><span data-ttu-id="ece75-110">Definice</span><span class="sxs-lookup"><span data-stu-id="ece75-110">Definition</span></span>

<span data-ttu-id="ece75-111">Možnost hodnoty je definována jako [rozlišené sjednocení struktury](discriminated-unions.md#struct-discriminated-unions) , které se podobá typu možnosti odkazu.</span><span class="sxs-lookup"><span data-stu-id="ece75-111">Value Option is defined as a [struct discriminated union](discriminated-unions.md#struct-discriminated-unions) that is similar to the reference option type.</span></span> <span data-ttu-id="ece75-112">Její definice se dá představit tímto způsobem:</span><span class="sxs-lookup"><span data-stu-id="ece75-112">Its definition can be thought of this way:</span></span>

```fsharp
[<StructuralEquality; StructuralComparison>]
[<Struct>]
type ValueOption<'T> =
    | ValueNone
    | ValueSome of 'T
```

<span data-ttu-id="ece75-113">Hodnota možnosti odpovídá strukturální rovnosti a porovnávání.</span><span class="sxs-lookup"><span data-stu-id="ece75-113">Value Option conforms to structural equality and comparison.</span></span> <span data-ttu-id="ece75-114">Hlavní rozdíl je v tom, že zkompilovaný název, název typu a názvy všech písmen označují, že se jedná o typ hodnoty.</span><span class="sxs-lookup"><span data-stu-id="ece75-114">The main difference is that the compiled name, type name, and case names all indicate that it is a value type.</span></span>

## <a name="using-value-options"></a><span data-ttu-id="ece75-115">Použití možností hodnot</span><span class="sxs-lookup"><span data-stu-id="ece75-115">Using Value Options</span></span>

<span data-ttu-id="ece75-116">Možnosti hodnoty se používají stejně jako [Možnosti](options.md).</span><span class="sxs-lookup"><span data-stu-id="ece75-116">Value Options are used just like [Options](options.md).</span></span> <span data-ttu-id="ece75-117">`ValueSome` slouží k označení toho, že hodnota je přítomna a `ValueNone` se používá, když hodnota není k dispozici:</span><span class="sxs-lookup"><span data-stu-id="ece75-117">`ValueSome` is used to indicate that a value is present, and `ValueNone` is used when a value is not present:</span></span>

```fsharp
let tryParseDateTime (s: string) =
    match System.DateTime.TryParse(s) with
    | (true, dt) -> ValueSome dt
    | (false, _) -> ValueNone

let possibleDateString1 = "1990-12-25"
let possibleDateString2 = "This is not a date"

let result1 = tryParseDateTime possibleDateString1
let result2 = tryParseDateTime possibleDateString2

match (result1, result2) with
| ValueSome d1, ValueSome d2 -> printfn "Both are dates!"
| ValueSome d1, ValueNone -> printfn "Only the first is a date!"
| ValueNone, ValueSome d2 -> printfn "Only the second is a date!"
| ValueNone, ValueNone -> printfn "None of them are dates!"
```

<span data-ttu-id="ece75-118">Podobně jako u [možností](options.md)jsou zásady vytváření názvů pro funkci, která vrací `ValueOption`, předponou `try`.</span><span class="sxs-lookup"><span data-stu-id="ece75-118">As with [Options](options.md), the naming convention for a function that returns `ValueOption` is to prefix it with `try`.</span></span>

## <a name="value-option-properties-and-methods"></a><span data-ttu-id="ece75-119">Vlastnosti a metody možností hodnoty</span><span class="sxs-lookup"><span data-stu-id="ece75-119">Value Option properties and methods</span></span>

<span data-ttu-id="ece75-120">V tuto chvíli existuje jedna vlastnost pro hodnoty možností: `Value`.</span><span class="sxs-lookup"><span data-stu-id="ece75-120">There is one property for Value Options at this time: `Value`.</span></span> <span data-ttu-id="ece75-121"><xref:System.InvalidOperationException> je vyvolána, pokud je při vyvolání této vlastnosti zobrazena žádná hodnota.</span><span class="sxs-lookup"><span data-stu-id="ece75-121">An <xref:System.InvalidOperationException> is raised if no value is present when this property is invoked.</span></span>

## <a name="value-option-functions"></a><span data-ttu-id="ece75-122">Hodnoty možností funkcí</span><span class="sxs-lookup"><span data-stu-id="ece75-122">Value Option functions</span></span>

<span data-ttu-id="ece75-123">Modul `ValueOption` v FSharp. Core obsahuje ekvivalentní funkce modulu `Option`.</span><span class="sxs-lookup"><span data-stu-id="ece75-123">The `ValueOption` module in FSharp.Core contains equivalent functionality to the `Option` module.</span></span> <span data-ttu-id="ece75-124">Existuje několik rozdílů v názvu, například `defaultValueArg`:</span><span class="sxs-lookup"><span data-stu-id="ece75-124">There are a few differences in name, such as `defaultValueArg`:</span></span>

```fsharp
val defaultValueArg : arg:'T voption -> defaultValue:'T -> 'T
```

<span data-ttu-id="ece75-125">To funguje stejně jako `defaultArg` v modulu `Option`, ale místo toho pracuje s možností hodnoty.</span><span class="sxs-lookup"><span data-stu-id="ece75-125">This acts just like `defaultArg` in the `Option` module, but operates on a Value Option instead.</span></span>

## <a name="see-also"></a><span data-ttu-id="ece75-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ece75-126">See also</span></span>

- [<span data-ttu-id="ece75-127">Možnosti</span><span class="sxs-lookup"><span data-stu-id="ece75-127">Options</span></span>](options.md)
