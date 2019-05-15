---
title: Prozkoumejte rozsahy dat pomocí indexů a rozsahy
description: Tato pokročilé kurzu se naučíte zkoumat data pomocí indexy a oblastí k prozkoumání řezy sekvenční datových sad.
ms.date: 04/19/2019
ms.custom: mvc
ms.openlocfilehash: 118d3c9ccad98ec02195c2b5e26a2ca203990adf
ms.sourcegitcommit: 682c64df0322c7bda016f8bfea8954e9b31f1990
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/13/2019
ms.locfileid: "65557189"
---
# <a name="indices-and-ranges"></a>Indexy a rozsahy

Rozsahy a indexy poskytují stručné syntaxe pro přístup k jednotlivé prvky nebo oblasti <xref:System.Array>, <xref:System.Span%601>, nebo <xref:System.ReadOnlySpan%601>. Tyto funkce umožňují přesnější, zrušte zaškrtnutí políčka syntaxi k přístupu k jednotlivé prvky nebo rozsah prvků v posloupnosti.

V tomto kurzu se dozvíte jak:

> [!div class="checklist"]
> * U rozsahů v pořadí použijte syntaxi.
> * Seznamte se s rozhodnutí o návrhu pro začátku a konce každého pořadí.
> * Další scénáře pro <xref:System.Index> a <xref:System.Range> typy.

## <a name="language-support-for-indices-and-ranges"></a>Podpora jazyků pro rozsahy a indexy

Tato podpora jazyka spoléhá na dva nové typy a dvou nových operátorů.
- <xref:System.Index?displayProperty=nameWithType> představuje index na sekvenci.
- `^` Operátor, který určuje, že je index vzhledem ke konci sekvence.
- <xref:System.Range?displayProperty=nameWithType> představuje rozsah dílčí sekvenci.
- Operátor rozsahu (`..`), který určuje jeho operandy počáteční a koncová hodnota rozsahu.

Začněme s pravidly pro indexy. Vezměte v úvahu pole `sequence`. `0` Index je stejný jako `sequence[0]`. `^0` Index je stejný jako `sequence[sequence.Length]`. Všimněte si, že `sequence[^0]` vyvolá výjimku, stejně jako `sequence[sequence.Length]` nepodporuje. Pro libovolný počet `n`, index `^n` je stejný jako `sequence[sequence.Length - n]`.

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

Můžete načíst poslední slovo s `^1` indexu. Přidejte následující kód pod inicializace:

[!code-csharp[LastIndex](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_LastIndex)]

Určuje oblast *start* a *koncové* rozsahu. Rozsahy jsou výhradní, to znamená *end* není zahrnutý v rozsahu. Rozsah `[0..^0]` představuje celou oblast, stejně jako `[0..sequence.Length]` představuje celou oblast. 

Následující kód vytvoří podrozsahu s slova "rychlé", "brown" a "fox". Zahrnuje `words[1]` prostřednictvím `words[3]`. Element `words[4]` není v rozsahu. Přidejte následující kód k metodě stejné. Zkopírujte a vložte ji dole v interaktivním okně.

[!code-csharp[Range](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_Range)]

Následující kód vytvoří podrozsahu "opožděné" a "pes". Zahrnuje `words[^2]` a `words[^1]`. Koncová hodnota `words[^0]` není zahrnut. Přidejte následující kód:

[!code-csharp[LastRange](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_LastRange)]

Následující příklady vytváří rozsahy, které jsou otevřené skončila pro zahájení a ukončení:

[!code-csharp[PartialRange](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_PartialRanges)]

Rozsahy nebo indexy můžete také deklarovat jako proměnné. Proměnná je pak možné uvnitř `[` a `]` znaků:

[!code-csharp[IndexRangeTypes](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_RangeIndexTypes)]

Následující příklad ukazuje mnoho důvodů těchto možností. Upravit `x`, `y`, a `z` vyzkoušet různé kombinace. Když můžete experimentovat, použijte hodnoty, kde `x` je menší než `y`, a `y` je menší než `z` pro platné kombinace. Přidejte následující kód do nové metody. Zkuste použijte různé kombinace:

[!code-csharp[SemanticsExamples](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_Semantics)]

## <a name="scenarios-for-indices-and-ranges"></a>Scénáře pro rozsahy a indexy

Pokud chcete provádět některé analýzy podrozsahu celé sekvenci, budete používat často rozsahy a indexy. Nová syntaxe je jasnější v přesně je zahrnuta jaké podrozsahu pro čtení. Lokální funkce `MovingAverage` přijímá <xref:System.Range> jako svůj argument. Metoda pak vytvoří výčet právě tento rozsah při výpočtu min, max a průměr. Vyzkoušejte následující kód ve vašem projektu:

[!code-csharp[MovingAverages](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_MovingAverage)]

Můžete stáhnout Dokončený kód z [dotnet/samples](https://github.com/dotnet/samples/tree/master/csharp/tutorials/RangesIndexes) úložiště.
