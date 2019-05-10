---
title: Prozkoumejte rozsahy dat pomocí indexů a rozsahy
description: Tato pokročilé kurzu se naučíte zkoumat data pomocí indexy a oblastí k prozkoumání řezy sekvenční datových sad.
ms.date: 04/19/2019
ms.custom: mvc
ms.openlocfilehash: 64fae4581e265d4f70b8356d5c651b4fdaca3fe9
ms.sourcegitcommit: dd3b897feb5c4ac39732bb165848e37a344b0765
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/25/2019
ms.locfileid: "64431488"
---
# <a name="indices-and-ranges"></a>Indexy a rozsahy

Rozsahy a indexy poskytují stručné syntaxe pro přístup k jednotlivé prvky nebo oblasti <xref:System.Array>, <xref:System.Span%601>, nebo <xref:System.ReadOnlySpan%601>. Tyto funkce umožňují přesnější, zrušte zaškrtnutí políčka syntaxi k přístupu k jednotlivé prvky nebo rozsah prvků v posloupnosti.

V tomto kurzu se dozvíte jak:

> [!div class="checklist"]
> * U rozsahů v pořadí použijte syntaxi.
> * Seznamte se s rozhodnutí o návrhu pro začátku a konce každého pořadí.
> * Další scénáře pro <xref:System.Index> a <xref:System.Range> typy.

## <a name="language-support-for-indices-and-ranges"></a>Podpora jazyků pro rozsahy a indexy

Můžete určit index **od konce** pomocí `^` znak před index. Indexování od konce spustí z pravidla, která `0..^0` Určuje celou oblast. K výpisu obsahu celého pole začnete *na první prvek*a pokračovat, dokud se *místo za posledním prvkem*. Představte si, že chování `MoveNext` metodu na enumerátor: vrátí hodnotu false v případě úspěšného posledním prvkem výčtu. Index `^0` znamená "end" `array[array.Length]`, nebo index, který následuje po posledním prvku. Jste obeznámeni s `array[2]` znamená elementu "2 od samého začátku". Nyní `array[^2]` znamená, že element "2 od konce". 

Můžete zadat **rozsah** s **operátor rozsahu**: `..`. Například `0..^0` určuje celý rozsah pole: 0 od začátku až do, s výjimkou 0 od konce. Jeden z operandů může používat "z start" nebo "end". Kromě toho může vynechat jeden z operandů. Výchozí hodnoty jsou `0` pro počáteční index a `^0` end indexu.

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

Pojem "od začátku" a "z"konec posiluje indexu každého prvku, a rozsahy adres jsou uvedeny bez konec rozsahu. "Start" celého pole je první prvek. "End" celého pole *minulosti* poslední prvek.

Můžete načíst poslední slovo s `^1` indexu. Přidejte následující kód pod inicializace:

[!code-csharp[LastIndex](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_LastIndex)]

Následující kód vytvoří podrozsahu s slova "rychlé", "brown" a "fox". Zahrnuje `words[1]` prostřednictvím `words[3]`. Element `words[4]` není v rozsahu. Přidejte následující kód k metodě stejné. Zkopírujte a vložte ji dole v interaktivním okně.

[!code-csharp[Range](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_Range)]

Následující kód vytvoří podrozsahu "opožděné" a "pes". Zahrnuje `words[^2]` a `words[^1]`. Koncová hodnota `words[^0]` není zahrnut. Přidejte následující kód:

[!code-csharp[LastRange](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_LastRange)]

Následující příklady vytváří rozsahy, které jsou otevřené skončila pro zahájení a ukončení:

[!code-csharp[PartialRange](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_PartialRanges)]

Rozsahy nebo indexy můžete také deklarovat jako proměnné. Proměnná je pak možné uvnitř `[` a `]` znaků:

[!code-csharp[IndexRangeTypes](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_RangeIndexTypes)]

Předchozí příklady ukazují dvě rozhodnutí o návrhu, které vyžadují další vysvětlení:

- Rozsahy jsou *exkluzivní*, tj. element v poslední index není v rozsahu.
- Index `^0` je *konci* kolekce, ne *poslední prvek* v kolekci.

Následující příklad ukazuje mnoho důvodů těchto možností. Upravit `x`, `y`, a `z` vyzkoušet různé kombinace. Když můžete experimentovat, použijte hodnoty, kde `x` je menší než `y`, a `y` je menší než `z` pro platné kombinace. Přidejte následující kód do nové metody. Zkuste použijte různé kombinace:

[!code-csharp[SemanticsExamples](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_Semantics)]

## <a name="scenarios-for-indices-and-ranges"></a>Scénáře pro rozsahy a indexy

Pokud chcete provádět některé analýzy podrozsahu celé sekvenci, budete používat často rozsahy a indexy. Nová syntaxe je jasnější v přesně je zahrnuta jaké podrozsahu pro čtení. Lokální funkce `MovingAverage` přijímá <xref:System.Range> jako svůj argument. Metoda pak vytvoří výčet právě tento rozsah při výpočtu min, max a průměr. Vyzkoušejte následující kód ve vašem projektu:

[!code-csharp[MovingAverages](~/samples/csharp/tutorials/RangesIndexes/IndicesAndRanges.cs#IndicesAndRanges_MovingAverage)]

Můžete stáhnout Dokončený kód z [dotnet/samples](https://github.com/dotnet/samples/tree/master/csharp/tutorials/RangesIndexes) úložiště.
