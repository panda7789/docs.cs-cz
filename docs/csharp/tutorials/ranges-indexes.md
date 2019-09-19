---
title: Prozkoumat rozsahy dat pomocí indexů a rozsahů
description: V tomto pokročilém kurzu se naučíte prozkoumat data pomocí indexů a rozsahů, abyste prozkoumali řezy sekvenční sady dat.
ms.date: 04/19/2019
ms.custom: mvc
ms.openlocfilehash: d0eeadfff9732ced22e045536a88ed49cd98bbaa
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117840"
---
# <a name="indices-and-ranges"></a>Indexy a rozsahy

Rozsahy a indexy poskytují stručnou syntaxi pro přístup k jednotlivým prvkům nebo rozsahům <xref:System.Array>v <xref:System.String>, <xref:System.Span%601>, nebo <xref:System.ReadOnlySpan%601>. Tyto funkce umožňují přesnější, jasnou syntaxi pro přístup k jednotlivým prvkům nebo rozsahům prvků v sekvenci.

V tomto kurzu se naučíte:

> [!div class="checklist"]
>
> - Použijte syntaxi pro rozsahy v sekvenci.
> - Pochopení rozhodnutí o návrhu pro začátek a konec každé sekvence.
> - Naučte se <xref:System.Index> scénáře pro <xref:System.Range> typy a.

## <a name="language-support-for-indices-and-ranges"></a>Podpora jazyků pro indexy a rozsahy

Tato podpora jazyků spoléhá na dva nové typy a dva nové operátory:

- <xref:System.Index?displayProperty=nameWithType>představuje index do sekvence.
- Index z operátoru `^`end, který určuje, že index je relativní ke konci sekvence.
- <xref:System.Range?displayProperty=nameWithType>představuje dílčí rozsah sekvence.
- Operátor `..`rozsahu, který určuje začátek a konec rozsahu jako jeho operandy.

Pojďme začít s pravidly pro indexy. Zvažte pole `sequence`. Index je stejný jako `sequence[0]`. `0` Index je stejný jako `sequence[sequence.Length]`. `^0` Všimněte si `sequence[^0]` , že vyvolá výjimku, stejně jako `sequence[sequence.Length]` . Pro jakékoli číslo `n`je index `^n` stejný jako `sequence[sequence.Length - n]`.

```csharp-interactive
string[] words = new string[]
{
                // index from start    index from end
    "The",      // 0                   ^9
    "quick",    // 1                   ^8
    "brown",    // 2                   ^7
    "fox",      // 3                   ^6
    "jumped",   // 4                   ^5
    "over",     // 5                   ^4
    "the",      // 6                   ^3
    "lazy",     // 7                   ^2
    "dog"       // 8                   ^1
};              // 9 (or words.Length) ^0
```

Poslední slovo můžete načíst s `^1` indexem. Pod inicializaci přidejte následující kód:

[!code-csharp[LastIndex](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_LastIndex)]

Rozsah Určuje *začátek* a *konec* rozsahu. Rozsahy jsou exkluzivní, což znamená, že *konec* není zahrnutý v rozsahu. Rozsah `[0..^0]` představuje celý rozsah, stejně jako `[0..sequence.Length]` představuje celý rozsah. 

Následující kód vytvoří dílčí rozsah s slovy "Rychlá", "hnědá" a "Fox". Zahrnuje `words[1]` .`words[3]` Element `words[4]` není v rozsahu. Do stejné metody přidejte následující kód. Zkopírujte ho a vložte ho do dolní části okna interaktivní.

[!code-csharp[Range](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_Range)]

Následující kód vytvoří dílčí rozsah s "opožděným" a "pes". Zahrnuje `words[^2]` a .`words[^1]` Koncový index `words[^0]` není zahrnutý. Přidejte také následující kód:

[!code-csharp[LastRange](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_LastRange)]

V následujících příkladech jsou vytvořeny rozsahy, které jsou otevřeny pro začátek, konec nebo obojí:

[!code-csharp[PartialRange](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_PartialRanges)]

Můžete také deklarovat rozsahy nebo indexy jako proměnné. Proměnná se pak dá použít uvnitř `[` znaků a: `]`

[!code-csharp[IndexRangeTypes](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_RangeIndexTypes)]

Následující příklad znázorňuje mnoho z důvodů pro tyto volby. Upravte `x`, `y`a a`z` vyzkoušejte různé kombinace. Při experimentování `x` použijte hodnoty, kde je menší než `y`a `y` je menší než `z` pro platné kombinace. Do nové metody přidejte následující kód. Vyzkoušejte různé kombinace:

[!code-csharp[SemanticsExamples](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_Semantics)]

## <a name="scenarios-for-indices-and-ranges"></a>Scénáře pro indexy a rozsahy

Pokud chcete provést analýzu v podrozsahu celé sekvence, často použijete rozsahy a indexy. Nová syntaxe je jasná při čtení přesně z toho, co je dílčí rozsah zahrnutý. Místní funkce `MovingAverage` <xref:System.Range> přijímá jako svůj argument. Metoda pak při výpočtu minimálních, maximálních a průměrů vytvoří výčet pouze tohoto rozsahu. Vyzkoušejte následující kód v projektu:

[!code-csharp[MovingAverages](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_MovingAverage)]

Dokončený kód si můžete stáhnout z úložiště [dotnet/Samples](https://github.com/dotnet/samples/tree/master/csharp/tutorials/RangesIndexes) .
