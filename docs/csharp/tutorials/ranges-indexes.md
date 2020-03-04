---
title: Prozkoumat rozsahy dat pomocí indexů a rozsahů
description: V tomto pokročilém kurzu se naučíte prozkoumat data pomocí indexů a rozsahů, abyste prozkoumali řezy sekvenční sady dat.
ms.date: 09/20/2019
ms.technology: csharp-fundamentals
ms.custom: mvc
ms.openlocfilehash: 5b6277763cfccfc75947f6fa0534964389b1dea3
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/03/2020
ms.locfileid: "78240038"
---
# <a name="indices-and-ranges"></a>Indexy a rozsahy

Rozsahy a indexy poskytují stručnou syntaxi pro přístup k jednotlivým prvkům nebo rozsahům v sekvenci.

V tomto kurzu se naučíte:

> [!div class="checklist"]
>
> - Použijte syntaxi pro rozsahy v sekvenci.
> - Pochopení rozhodnutí o návrhu pro začátek a konec každé sekvence.
> - Seznamte se s scénáři <xref:System.Index> a <xref:System.Range>ch typů.

## <a name="language-support-for-indices-and-ranges"></a>Podpora jazyků pro indexy a rozsahy

Tato podpora jazyků spoléhá na dva nové typy a dva nové operátory:

- <xref:System.Index?displayProperty=nameWithType> představuje index do sekvence.
- Index z operátoru end `^`, který určuje, že index je relativní ke konci sekvence.
- <xref:System.Range?displayProperty=nameWithType> představuje dílčí rozsah sekvence.
- Operátor rozsahu `..`, který určuje začátek a konec rozsahu jako jeho operandy.

Pojďme začít s pravidly pro indexy. Zvažte pole `sequence`. `0` index je stejný jako `sequence[0]`. `^0` index je stejný jako `sequence[sequence.Length]`. Všimněte si, že `sequence[^0]` vyvolá výjimku, stejně jako `sequence[sequence.Length]`. V případě libovolného čísla `n`index `^n` stejný jako `sequence[sequence.Length - n]`.

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

Poslední slovo můžete načíst pomocí indexu `^1`. Pod inicializaci přidejte následující kód:

[!code-csharp[LastIndex](~/samples/snippets/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_LastIndex)]

Rozsah Určuje *začátek* a *konec* rozsahu. Rozsahy jsou exkluzivní, což znamená, že *konec* není zahrnutý v rozsahu. Rozsah `[0..^0]` představuje celý rozsah, stejně jako `[0..sequence.Length]` představuje celý rozsah. 

Následující kód vytvoří dílčí rozsah s slovy "Rychlá", "hnědá" a "Fox". Zahrnuje `words[1]` prostřednictvím `words[3]`. Element `words[4]` není v rozsahu. Do stejné metody přidejte následující kód. Zkopírujte ho a vložte ho do dolní části okna interaktivní.

[!code-csharp[Range](~/samples/snippets/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_Range)]

Následující kód vytvoří dílčí rozsah s "opožděným" a "pes". Zahrnuje `words[^2]` a `words[^1]`. Koncový index `words[^0]` není zahrnutý. Přidejte také následující kód:

[!code-csharp[LastRange](~/samples/snippets/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_LastRange)]

V následujících příkladech jsou vytvořeny rozsahy, které jsou otevřeny pro začátek, konec nebo obojí:

[!code-csharp[PartialRange](~/samples/snippets/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_PartialRanges)]

Můžete také deklarovat rozsahy nebo indexy jako proměnné. Proměnná se pak dá použít uvnitř `[` a `]`ch znaků:

[!code-csharp[IndexRangeTypes](~/samples/snippets/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_RangeIndexTypes)]

Následující příklad znázorňuje mnoho z důvodů pro tyto volby. Pokud chcete vyzkoušet různé kombinace, upravte `x`, `y`a `z`. Při experimentování použijte hodnoty, kde je `x` menší než `y`a `y` je nižší než `z` pro platné kombinace. Do nové metody přidejte následující kód. Vyzkoušejte různé kombinace:

[!code-csharp[SemanticsExamples](~/samples/snippets/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_Semantics)]

## <a name="type-support-for-indices-and-ranges"></a>Podpora typů pro indexy a rozsahy

Indexy a rozsahy poskytují nejasnou, stručnou syntaxi pro přístup k jednomu prvku nebo dílčímu rozsahu prvků v sekvenci. Indexový výraz obvykle vrací typ prvků sekvence. Výraz rozsahu obvykle vrací stejný typ sekvence jako zdrojovou sekvenci.

Pokud typ poskytuje [indexer](../programming-guide/indexers/index.md) s parametrem <xref:System.Index> nebo <xref:System.Range>, explicitně podporuje indexy nebo rozsahy v uvedeném pořadí. Když typ poskytne indexer, který přebírá jeden <xref:System.Range> parametr, může se zvolit, že se má vrátit jiný typ sekvence, například <xref:System.Span%601?displayProperty=nameWithType>.

Typ je **vypočítán** , pokud má vlastnost s názvem `Length` nebo `Count` s přístupným mechanismem getter a návratovým typem `int`. Typ Count, který explicitně nepodporuje indexy nebo rozsahy, může pro ně poskytnout implicitní podporu. Další informace naleznete v části Podpora [implicitního indexu](~/_csharplang/proposals/csharp-8.0/ranges.md#implicit-index-support) a [Podpora implicitního rozsahu](~/_csharplang/proposals/csharp-8.0/ranges.md#implicit-range-support) v [poznámce k návrhu funkcí](~/_csharplang/proposals/csharp-8.0/ranges.md). Rozsahy, které používají implicitní rozsah, vracejí stejný typ sekvence jako zdrojová sekvence.

Například následující typy rozhraní .NET podporují jak indexy, tak rozsahy: <xref:System.Array>, <xref:System.String>, <xref:System.Span%601>a <xref:System.ReadOnlySpan%601>. <xref:System.Collections.Generic.List%601> podporuje indexy, ale nepodporuje rozsahy.

## <a name="scenarios-for-indices-and-ranges"></a>Scénáře pro indexy a rozsahy

Pokud chcete provést analýzu v podrozsahu celé sekvence, často použijete rozsahy a indexy. Nová syntaxe je jasná při čtení přesně z toho, co je dílčí rozsah zahrnutý. Místní funkce `MovingAverage` jako argument převezme <xref:System.Range>. Metoda pak při výpočtu minimálních, maximálních a průměrů vytvoří výčet pouze tohoto rozsahu. Vyzkoušejte následující kód v projektu:

[!code-csharp[MovingAverages](~/samples/snippets/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_MovingAverage)]

Dokončený kód si můžete stáhnout z úložiště [dotnet/Samples](https://github.com/dotnet/samples/tree/master/csharp/tutorials/RangesIndexes) .
