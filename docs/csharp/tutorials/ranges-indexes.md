---
title: Prozkoumejte rozsahy dat pomocí indexů a rozsahů
description: Tento pokročilý kurz vás naučí prozkoumat data pomocí indexů a rozsahů a prozkoumat řezy sekvenční datové sady.
ms.date: 03/11/2020
ms.technology: csharp-fundamentals
ms.custom: mvc
ms.openlocfilehash: 82aad968e2efc437c82a7c8250bcd108b60b09e1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79156491"
---
# <a name="indices-and-ranges"></a>Indexy a rozsahy

Rozsahy a indexy poskytují stručnou syntaxi pro přístup k jednotlivým prvkům nebo rozsahům v sekvenci.

V tomto kurzu se naučíte:

> [!div class="checklist"]
>
> - Syntaxe pro oblasti v sekvenci použijte.
> - Seznamte se s rozhodnutími o návrhu pro začátek a konec každé sekvence.
> - Seznamte se <xref:System.Index> <xref:System.Range> se scénáři pro a typy.

## <a name="language-support-for-indices-and-ranges"></a>Jazyková podpora indexů a rozsahů

Tato jazyková podpora se opírá o dva nové typy a dva nové operátory:

- <xref:System.Index?displayProperty=nameWithType>představuje index do sekvence.
- Index z koncového operátoru `^`, který určuje, že index je relativní ke konci sekvence.
- <xref:System.Range?displayProperty=nameWithType>představuje dílčí rozsah sekvence.
- Operátor `..`rozsahu , který určuje začátek a konec rozsahu jako jeho operandy.

Začněme s pravidly pro indexy. Zvažte `sequence`pole . Index `0` je stejný `sequence[0]`jako . Index `^0` je stejný `sequence[sequence.Length]`jako . Výraz `sequence[^0]` vyvolat výjimku, stejně jako `sequence[sequence.Length]` dělá. Pro libovolné `n`číslo `^n` je index `sequence[sequence.Length - n]`stejný jako .

```csharp
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

Můžete načíst poslední slovo `^1` s indexem. Pod inicializaci přidejte následující kód:

[!code-csharp[LastIndex](~/samples/snippets/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_LastIndex)]

Rozsah určuje *začátek* *a* konec rozsahu. Rozsahy jsou exkluzivní, což znamená, že *konec* není součástí rozsahu. Rozsah `[0..^0]` představuje celý rozsah, `[0..sequence.Length]` stejně jako představuje celý rozsah.

Následující kód vytvoří podrozsah se slovy "quick", "brown" a "fox". To `words[1]` zahrnuje `words[3]`prostřednictvím . Prvek `words[4]` není v rozsahu. Přidejte následující kód ke stejné metodě. Zkopírujte a vložte jej do dolní části interaktivního okna.

[!code-csharp[Range](~/samples/snippets/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_Range)]

Následující kód vytvoří podrozsah s "líný" a "pes". To `words[^2]` zahrnuje `words[^1]`a . Koncový index `words[^0]` není zahrnut. Přidejte také následující kód:

[!code-csharp[LastRange](~/samples/snippets/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_LastRange)]

Následující příklady vytvářejí oblasti, které jsou otevřené pro začátek, konec nebo obojí:

[!code-csharp[PartialRange](~/samples/snippets/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_PartialRanges)]

Rozsahy nebo indexy můžete také deklarovat jako proměnné. Proměnnou lze pak použít `[` `]` uvnitř znaků a:

[!code-csharp[IndexRangeTypes](~/samples/snippets/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_RangeIndexTypes)]

Následující příklad ukazuje mnoho důvodů pro tyto volby. `x`Upravte `y`, `z` a vyzkoušejte různé kombinace. Při experimentování použijte `x` hodnoty, `y`kde `y` je menší `z` než , a je menší než pro platné kombinace. Přidejte následující kód do nové metody. Vyzkoušejte různé kombinace:

[!code-csharp[SemanticsExamples](~/samples/snippets/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_Semantics)]

## <a name="type-support-for-indices-and-ranges"></a>Podpora typů pro indexy a rozsahy

Indexy a rozsahy poskytují jasnou, stručnou syntaxi pro přístup k jednomu prvku nebo podoblasti prvků v sekvenci. Výraz indexu obvykle vrací typ prvků sekvence. Výraz rozsahu obvykle vrací stejný typ sekvence jako zdrojová sekvence.

Libovolný typ, který poskytuje [indexeru](../programming-guide/indexers/index.md) s parametrem <xref:System.Index> nebo <xref:System.Range> explicitně podporuje indexy nebo rozsahy. Indexer, který přebírá <xref:System.Range> jeden parametr může vrátit jiný <xref:System.Span%601?displayProperty=nameWithType>typ sekvence, například .

Typ je **možné počítat,** pokud `Length` má `Count` vlastnost s názvem nebo s `int`přístupným getter a návratový typ . Počítatelný typ, který explicitně nepodporuje indexy nebo rozsahy, může poskytnout implicitní podporu pro ně. Další informace naleznete v části [implicitní index podpory](~/_csharplang/proposals/csharp-8.0/ranges.md#implicit-index-support) a [implicitní rozsah podpory](~/_csharplang/proposals/csharp-8.0/ranges.md#implicit-range-support) poznámky [návrhu funkce](~/_csharplang/proposals/csharp-8.0/ranges.md). Rozsahy používající implicitní podporu rozsahu vrátí stejný typ sekvence jako zdrojová sekvence.

Například následující typy .NET podporují indexy i <xref:System.String>rozsahy: , <xref:System.Span%601>a <xref:System.ReadOnlySpan%601>. Podporuje <xref:System.Collections.Generic.List%601> indexy, ale nepodporuje rozsahy.

<xref:System.Array>má více nuancí chování. Pole s jednou dimenzí podporují indexy i rozsahy. Vícerozměrná pole ne. Indexer pro vícerozměrné pole má více parametrů, nikoli jeden parametr. Zubatá pole, označovaná také jako pole polí, podporují rozsahy i indexery. Následující příklad ukazuje, jak iterat obdélníkové podsekce zubaté pole. Itetuje řez uprostřed, s výjimkou prvního a posledního tří řádků a prvnía poslední dva sloupce z každého vybraného řádku:

[!code-csharp[JaggedArrays](~/samples/snippets/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_JaggedArrays)]

## <a name="scenarios-for-indices-and-ranges"></a>Scénáře pro indexy a rozsahy

Často budete používat rozsahy a indexy, pokud chcete analyzovat podrozsah větší sekvence. Nová syntaxe je jasnější při čtení přesně to, co podrozsah se jedná. Místní funkce `MovingAverage` bere <xref:System.Range> jako jeho argument. Metoda pak vyjmenovává právě tento rozsah při výpočtu min, max a průměr. Zkuste v projektu následující kód:

[!code-csharp[MovingAverages](~/samples/snippets/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_MovingAverage)]
