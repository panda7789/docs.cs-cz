---
title: Hodnota možnosti
description: Další informace o F# možnost Hodnota typu, který je struktura verzi typu možnosti.
ms.date: 02/06/2019
ms.openlocfilehash: e1036c83189c853b3704d94ca245e4818acc98c1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61982576"
---
# <a name="value-options"></a><span data-ttu-id="7f7df-103">Hodnota možnosti</span><span class="sxs-lookup"><span data-stu-id="7f7df-103">Value Options</span></span>

<span data-ttu-id="7f7df-104">Typ hodnoty možnosti v F# se používá při uložení těchto dvou okolností:</span><span class="sxs-lookup"><span data-stu-id="7f7df-104">The Value Option type in F# is used when the following two circumstances hold:</span></span>

1. <span data-ttu-id="7f7df-105">Scénář je vhodný pro [ F# možnost](options.md).</span><span class="sxs-lookup"><span data-stu-id="7f7df-105">A scenario is appropriate for an [F# Option](options.md).</span></span>
2. <span data-ttu-id="7f7df-106">Pomocí struktury zvyšuje výkon ve vašem scénáři.</span><span class="sxs-lookup"><span data-stu-id="7f7df-106">Using a struct provides a performance benefit in your scenario.</span></span>

<span data-ttu-id="7f7df-107">Ne všechny scénáře náročné na výkon se "Vyřešeno" použití struktur.</span><span class="sxs-lookup"><span data-stu-id="7f7df-107">Not all performance-sensitive scenarios are "solved" by using structs.</span></span> <span data-ttu-id="7f7df-108">Je nutné zvážit další náklady na kopírování při jejich používání místo typy odkazů.</span><span class="sxs-lookup"><span data-stu-id="7f7df-108">You must consider the additional cost of copying when using them instead of reference types.</span></span> <span data-ttu-id="7f7df-109">Však velké F# programy běžně vytváření instancí mnoho doplňkové typy, které budou plout prostřednictvím horké cesty a v takovém případě může často struktury přinést lepší celkový výkon během životního cyklu aplikace.</span><span class="sxs-lookup"><span data-stu-id="7f7df-109">However, large F# programs commonly instantiate many optional types that flow through hot paths, and in such cases, structs can often yield better overall performance over the lifetime of a program.</span></span>

## <a name="definition"></a><span data-ttu-id="7f7df-110">Definice</span><span class="sxs-lookup"><span data-stu-id="7f7df-110">Definition</span></span>

<span data-ttu-id="7f7df-111">Možnost Hodnota je definována jako [rozlišovaná sjednocení na základě struktury](discriminated-unions.md#struct-discriminated-unions) , který je podobný typ odkazu možnost.</span><span class="sxs-lookup"><span data-stu-id="7f7df-111">Value Option is defined as a [struct discriminated union](discriminated-unions.md#struct-discriminated-unions) that is similar to the reference option type.</span></span> <span data-ttu-id="7f7df-112">Jeho definice můžete chápat takto:</span><span class="sxs-lookup"><span data-stu-id="7f7df-112">Its definition can be thought of this way:</span></span>

```fsharp
[<StructuralEquality; StructuralComparison>]
[<Struct>]
type ValueOption<'T> =
    | ValueNone
    | ValueSome of 'T
```

<span data-ttu-id="7f7df-113">Možnost hodnota odpovídá strukturální rovnost a porovnání.</span><span class="sxs-lookup"><span data-stu-id="7f7df-113">Value Option conforms to structural equality and comparison.</span></span> <span data-ttu-id="7f7df-114">Hlavní rozdíl je, že kompilovaný název, název typu a velikosti písmen názvů ukazují, že se jedná o typ hodnoty.</span><span class="sxs-lookup"><span data-stu-id="7f7df-114">The main difference is that the compiled name, type name, and case names all indicate that it is a value type.</span></span>

## <a name="using-value-options"></a><span data-ttu-id="7f7df-115">Pomocí možnosti hodnoty</span><span class="sxs-lookup"><span data-stu-id="7f7df-115">Using Value Options</span></span>

<span data-ttu-id="7f7df-116">Stejně jako se používají hodnotu možnosti [možnosti](options.md).</span><span class="sxs-lookup"><span data-stu-id="7f7df-116">Value Options are used just like [Options](options.md).</span></span> <span data-ttu-id="7f7df-117">`ValueSome` slouží k označení, že hodnota je k dispozici, a `ValueNone` se používá, když hodnota není k dispozici:</span><span class="sxs-lookup"><span data-stu-id="7f7df-117">`ValueSome` is used to indicate that a value is present, and `ValueNone` is used when a value is not present:</span></span>

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

<span data-ttu-id="7f7df-118">Stejně jako u [možnosti](options.md), zásady vytváření názvů pro funkce, která vrátí `ValueOption` je prefix `try`.</span><span class="sxs-lookup"><span data-stu-id="7f7df-118">As with [Options](options.md), the naming convention for a function that returns `ValueOption` is to prefix it with `try`.</span></span>

## <a name="value-option-properties-and-methods"></a><span data-ttu-id="7f7df-119">Hodnota možnosti vlastnosti a metody</span><span class="sxs-lookup"><span data-stu-id="7f7df-119">Value Option properties and methods</span></span>

<span data-ttu-id="7f7df-120">V tuto chvíli je jednu vlastnost s možností hodnota: `Value`.</span><span class="sxs-lookup"><span data-stu-id="7f7df-120">There is one property for Value Options at this time: `Value`.</span></span> <span data-ttu-id="7f7df-121"><xref:System.InvalidOperationException> Je vyvolána, pokud žádná hodnota není k dispozici, když se tato vlastnost vyvolá.</span><span class="sxs-lookup"><span data-stu-id="7f7df-121">An <xref:System.InvalidOperationException> is raised if no value is present when this property is invoked.</span></span>

## <a name="value-option-functions"></a><span data-ttu-id="7f7df-122">Hodnota možnosti funkce</span><span class="sxs-lookup"><span data-stu-id="7f7df-122">Value Option functions</span></span>

<span data-ttu-id="7f7df-123">Aktuálně nejsou k dispozici jednu funkci modulu mez pro hodnotu možnosti, `defaultValueArg`:</span><span class="sxs-lookup"><span data-stu-id="7f7df-123">There is currently one module-bound function for Value Options, `defaultValueArg`:</span></span>

```fsharp
val defaultValueArg : arg:'T voption -> defaultValue:'T -> 'T 
```

<span data-ttu-id="7f7df-124">Stejně jako u `defaultArg` funkci `defaultValueArg` vrátí zdrojovou hodnotu danou hodnotu možnosti, pokud existuje; jinak vrátí zadanou výchozí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="7f7df-124">As with the `defaultArg` function, `defaultValueArg` returns the underlying value of the given Value Option if it exists; otherwise, it returns the specified default value.</span></span>

<span data-ttu-id="7f7df-125">V tuto chvíli neexistují žádné další funkce vázané na modulu hodnotu možnosti.</span><span class="sxs-lookup"><span data-stu-id="7f7df-125">At this time, there are no other module-bound functions for Value Options.</span></span>

## <a name="see-also"></a><span data-ttu-id="7f7df-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7f7df-126">See also</span></span>

- [<span data-ttu-id="7f7df-127">Možnosti</span><span class="sxs-lookup"><span data-stu-id="7f7df-127">Options</span></span>](options.md)
