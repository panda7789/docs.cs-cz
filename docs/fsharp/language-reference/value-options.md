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
# <a name="value-options"></a>Možnosti pro hodnoty

Hodnota možnosti typ v se F# používá v případě, že jsou uloženy následující dvě okolnosti:

1. Scénář je vhodný pro [ F# možnost](options.md).
2. Použití struktury poskytuje ve vašem scénáři výhodu výkonu.

Ne všechny scénáře citlivé na výkon jsou "vyřešené" pomocí struktur. Je nutné vzít v úvahu další náklady na kopírování při jejich použití namísto odkazových typů. Velké F# programy však obvykle vytvářejí mnoho volitelných typů, které jsou přenášeny prostřednictvím aktivních cest, a v takových případech mohou struktury často vracet lepší celkový výkon po celou dobu životnosti programu.

## <a name="definition"></a>Definice

Možnost hodnoty je definována jako [rozlišené sjednocení struktury](discriminated-unions.md#struct-discriminated-unions) , které se podobá typu možnosti odkazu. Její definice se dá představit tímto způsobem:

```fsharp
[<StructuralEquality; StructuralComparison>]
[<Struct>]
type ValueOption<'T> =
    | ValueNone
    | ValueSome of 'T
```

Hodnota možnosti odpovídá strukturální rovnosti a porovnávání. Hlavní rozdíl je v tom, že zkompilovaný název, název typu a názvy všech písmen označují, že se jedná o typ hodnoty.

## <a name="using-value-options"></a>Použití možností hodnot

Možnosti hodnoty se používají stejně jako [Možnosti](options.md). `ValueSome` slouží k označení toho, že hodnota je přítomna a `ValueNone` se používá, když hodnota není k dispozici:

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

Podobně jako u [možností](options.md)jsou zásady vytváření názvů pro funkci, která vrací `ValueOption`, předponou `try`.

## <a name="value-option-properties-and-methods"></a>Vlastnosti a metody možností hodnoty

V tuto chvíli existuje jedna vlastnost pro hodnoty možností: `Value`. <xref:System.InvalidOperationException> je vyvolána, pokud je při vyvolání této vlastnosti zobrazena žádná hodnota.

## <a name="value-option-functions"></a>Hodnoty možností funkcí

Modul `ValueOption` v FSharp. Core obsahuje ekvivalentní funkce modulu `Option`. Existuje několik rozdílů v názvu, například `defaultValueArg`:

```fsharp
val defaultValueArg : arg:'T voption -> defaultValue:'T -> 'T
```

To funguje stejně jako `defaultArg` v modulu `Option`, ale místo toho pracuje s možností hodnoty.

## <a name="see-also"></a>Viz také:

- [Možnosti](options.md)
