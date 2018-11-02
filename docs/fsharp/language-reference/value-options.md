---
title: 'Hodnota možnosti (F #)'
description: 'Další informace o typu hodnota možnosti F #, což je struktura verze typu možnosti.'
ms.date: 06/16/2018
ms.openlocfilehash: 978bd1713c16f7c050ccb097cb134973d10ef6f5
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/02/2018
ms.locfileid: "50185833"
---
# <a name="value-options"></a>Hodnota možnosti

Typ hodnoty možnosti v jazyce F # se používá při uložení těchto dvou okolností:

1. Scénář je vhodný pro [možnost F #](options.md).
2. Pomocí struktury zvyšuje výkon ve vašem scénáři.

Ne všechny scénáře náročné na výkon se "Vyřešeno" použití struktur. Je nutné zvážit další náklady na kopírování při jejich používání místo typy odkazů. Však velké programy F # obvykle vytvořit instanci mnoho doplňkové typy, které budou plout prostřednictvím horké cesty, protože struktury někdy může přinést lepší celkový výkon během životního cyklu aplikace.

## <a name="definition"></a>Definice

Možnost Hodnota je definována jako [rozlišovaná sjednocení na základě struktury](discriminated-unions.md#struct-discriminated-unions) , který je podobný typ odkazu možnost. Jeho definice můžete chápat takto:

```fsharp
[<StructuralEquality; StructuralComparison>]
[<Struct>]
type ValueOption<'T> =
    | ValueNone
    | ValueSome of 'T
```

Možnost hodnota odpovídá strukturální rovnost a porovnání. Hlavní rozdíl je, že kompilovaný název, název typu a velikosti písmen názvů ukazují, že se jedná o typ hodnoty.

## <a name="using-value-options"></a>Pomocí možnosti hodnoty

Stejně jako se používají hodnotu možnosti [možnosti](options.md). `ValueSome` slouží k označení, že hodnota je k dispozici, a `ValueNone` se používá, když hodnota není k dispozici:

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

Stejně jako u [možnosti](options.md), zásady vytváření názvů pro funkce, která vrátí `ValueOption` je prefix `try`.

## <a name="value-option-properties-and-methods"></a>Hodnota možnosti vlastnosti a metody

V tuto chvíli je jednu vlastnost s možností hodnota: `Value`. <xref:System.InvalidOperationException> Je vyvolána, pokud žádná hodnota není k dispozici, když se tato vlastnost vyvolá.

## <a name="value-option-functions"></a>Hodnota možnosti funkce

Aktuálně nejsou k dispozici jednu funkci modulu mez pro hodnotu možnosti, `defaultValueArg`:

```fsharp
val defaultValueArg : arg:'T voption -> defaultValue:'T -> 'T 
```

Stejně jako u `defaultArg` funkci `defaultValueArg` vrátí zdrojovou hodnotu danou hodnotu možnosti, pokud existuje; jinak vrátí zadanou výchozí hodnotu.

V tuto chvíli neexistují žádné další funkce vázané na modulu hodnotu možnosti.

## <a name="see-also"></a>Viz také:

- [Možnosti](options.md)
