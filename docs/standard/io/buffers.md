---
title: Systémové.Vyrovnávací paměti - .NET
ms.date: 12/05/2019
ms.technology: dotnet-standard
helpviewer_keywords:
- buffers [.NET]
- I/O [.NET], buffers
author: rick-anderson
ms.author: riande
ms.openlocfilehash: d113def0182dc6a5bcea6c18b2d0e4b475946e31
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/21/2020
ms.locfileid: "81739620"
---
# <a name="work-with-buffers-in-net"></a>Práce s vyrovnávacími paměťmi v rozhraní .NET

Tento článek obsahuje přehled typů, které pomáhají číst data, která běží přes více vyrovnávacích pamětí. Používají se především k <xref:System.IO.Pipelines.PipeReader> podpoře objektů.

## <a name="ibufferwritert"></a>IBufferWriter\<T\>

<xref:System.Buffers.IBufferWriter%601?displayProperty=fullName>je smlouva pro synchronní zápis do vyrovnávací paměti. Na nejnižší úrovni rozhraní:

- Je základní a není těžké používat.
- Umožňuje přístup <xref:System.Memory%601> k <xref:System.Span%601>nebo . Nebo `Memory<T>` `Span<T>` může být zapsána do a `T` můžete určit, kolik položek bylo zapsáno.

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet)]

Předchozí metoda:

- Požaduje vyrovnávací paměť alespoň 5 bajtů `IBufferWriter<byte>` `GetSpan(5)`z using .
- Zapíše bajty pro řetězec ASCII "Hello" na vrácené `Span<byte>`.
- Volání <xref:System.Buffers.IBufferWriter%601> označující, kolik bajtů byly zapsány do vyrovnávací paměti.

Tato metoda zápisu `Memory<T>` / `Span<T>` používá vyrovnávací `IBufferWriter<T>`paměť poskytovanou . Alternativně metodu <xref:System.Buffers.BuffersExtensions.Write%2A> rozšíření lze zkopírovat existující vyrovnávací `IBufferWriter<T>`paměť do . `Write`dělá práci volání `GetSpan` / `Advance` podle potřeby, takže není třeba `Advance` volat po psaní:

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet2)]

<xref:System.Buffers.ArrayBufferWriter%601>je `IBufferWriter<T>` implementace, jejíž záložní úložiště je jedno souvislé pole.

### <a name="ibufferwriter-common-problems"></a>IBufferWriter běžné problémy

- `GetSpan`a `GetMemory` vrátit vyrovnávací paměť s alespoň požadované množství paměti. Nepředpokládejte přesné velikosti vyrovnávací paměti.
- Neexistuje žádná záruka, že po sobě jdoucí volání vrátí stejnou vyrovnávací paměť nebo vyrovnávací paměť stejné velikosti.
- Nová vyrovnávací paměť musí `Advance` být požadována po volání pokračovat v zápisu další data. Dříve získanou `Advance` vyrovnávací paměť nelze zapsat do po byla volána.

## <a name="readonlysequencet"></a>ReadOnlySequence\<T\>

![ReadOnlySequence zobrazující paměť v kanálu a pod touto sekvenční pozicí paměti jen pro čtení](media/buffers/ro-sequence.png)

<xref:System.Buffers.ReadOnlySequence%601>je struktura, která může představovat souvislou nebo nesousedící posloupnost . `T` Může být vyroben z:

1. Položka `T[]`.
1. Položka `ReadOnlyMemory<T>`.
1. Dvojice propojeného uzlu <xref:System.Buffers.ReadOnlySequenceSegment%601> seznamu a indexu představující počáteční a koncovou pozici sekvence.

Třetí zastoupení je nejzajímavější, protože má vliv na výkon `ReadOnlySequence<T>`na různé operace na :

|Reprezentace|Operace|Složitost|
---|---|---|
|`T[]`/`ReadOnlyMemory<T>`|`Length`|`O(1)`|
|`T[]`/`ReadOnlyMemory<T>`|`GetPosition(long)`|`O(1)`|
|`T[]`/`ReadOnlyMemory<T>`|`Slice(int, int)`|`O(1)`|
|`T[]`/`ReadOnlyMemory<T>`|`Slice(SequencePostion,  SequencePostion)`|`O(1)`|
|`ReadOnlySequenceSegment<T>`|`Length`|`O(1)`|
|`ReadOnlySequenceSegment<T>`|`GetPosition(long)`|`O(number of segments)`|
|`ReadOnlySequenceSegment<T>`|`Slice(int, int)`|`O(number of segments)`|
|`ReadOnlySequenceSegment<T>`|`Slice(SequencePostion, SequencePostion)`|`O(1)`|

Z důvodu této smíšené `ReadOnlySequence<T>` reprezentace zpřístupňuje indexy jako `SequencePosition` místo celé číslo. A `SequencePosition`:

- Je neprůhledná hodnota, která `ReadOnlySequence<T>` představuje index do kde pochází.
- Skládá se ze dvou částí, celé číslo a objekt. Co tyto dvě hodnoty představují, `ReadOnlySequence<T>`jsou vázány na implementaci .

### <a name="access-data"></a>Přístup k datům

Zpřístupňuje `ReadOnlySequence<T>` data jako výčtu `ReadOnlyMemory<T>`. Výčet každého segmentu lze provést pomocí základní foreach:

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet3)]

Předchozí metoda prohledává každý segment pro konkrétní bajt. Pokud potřebujete sledovat každý segment `SequencePosition`, <xref:System.Buffers.ReadOnlySequence%601.TryGet%2A?displayProperty=nameWithType> je vhodnější. Další ukázka změní předchozí kód `SequencePosition` vrátit místo celé číslo. Vrácení `SequencePosition` má tu výhodu, že umožňuje volajícímu vyhnout se druhé skenování získat data na konkrétní index.

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet4)]

Kombinace `SequencePosition` a `TryGet` působí jako čítač. Pole pozice je upraveno na začátku každé iterace `ReadOnlySequence<T>`tak, aby bylo začátkem každého segmentu v rámci .

Předchozí metoda existuje jako metoda rozšíření `ReadOnlySequence<T>`na . <xref:System.Buffers.BuffersExtensions.PositionOf%2A>lze použít ke zjednodušení předchozího kódu:

```csharp
SequencePosition? FindIndexOf(in ReadOnlySequence<byte> buffer, byte data) => buffer.PositionOf(data);
```

#### <a name="process-a-readonlysequencet"></a>Zpracování sekvence ReadOnlyT\<T\>

Zpracování `ReadOnlySequence<T>` může být náročné, protože data mohou být rozdělena mezi více segmentů v rámci sekvence. Pro dosažení nejlepšího výkonu rozdělte kód na dvě cesty:

- Rychlá cesta, která se zabývá případem jednoho segmentu.
- Pomalá cesta, která se zabývá rozdělením dat mezi segmenty.

Existuje několik přístupů, které lze použít ke zpracování dat ve vícesegmentových sekvencích:

- Použijte [`SequenceReader<T>`](#sequencereadert).
- Analyzovat datový segment podle segmentu, `SequencePosition` sledování a index v rámci segmentu analyzované. Tím se zabrání zbytečné přidělení, ale může být neefektivní, zejména pro malé vyrovnávací paměti.
- Zkopírujte `ReadOnlySequence<T>` souvislé pole a zacházejte s ním jako s jednou vyrovnávací pamětí:
  - Pokud `ReadOnlySequence<T>` je malá velikost, může být rozumné zkopírovat data do vyrovnávací paměti přidělené zásobníku pomocí operátoru [stackalloc.](../../csharp/language-reference/operators/stackalloc.md)
  - Zkopírujte `ReadOnlySequence<T>` do sdruženého pole pomocí <xref:System.Buffers.ArrayPool%601.Shared%2A?displayProperty=nameWithType>.
  - Použijte [`ReadOnlySequence<T>.ToArray()`](xref:System.Buffers.BuffersExtensions.ToArray%2A). To se nedoporučuje v horké cesty, protože `T[]` přiděluje nové na haldě.

Následující příklady ukazují některé běžné `ReadOnlySequence<byte>`případy pro zpracování :

##### <a name="process-binary-data"></a>Zpracovat binární data

Následující příklad analyzuje 4bajtovou délku velkého endianového celého čísla `ReadOnlySequence<byte>`od začátku .

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet5)]

[!INCLUDE [localized code comments](../../../includes/code-comments-loc.md)]

##### <a name="process-text-data"></a>Zpracování textových dat

Následující příklad:

- Najde první nový`\r\n`řádek ( `ReadOnlySequence<byte>` ) v a vrátí jej prostřednictvím out 'line' parametr.
- Ořízne tento `\r\n` řádek, s výjimkou vstupní vyrovnávací paměti.

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet6)]

##### <a name="empty-segments"></a>Prázdné segmenty

Je platný pro uložení prázdných segmentů uvnitř . `ReadOnlySequence<T>` Prázdné segmenty může dojít při výčtu segmentů explicitně:

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet7)]

Předchozí kód vytvoří `ReadOnlySequence<byte>` s prázdnými segmenty a ukazuje, jak tyto prázdné segmenty ovlivňují různá řešení API:

- `ReadOnlySequence<T>.Slice`s `SequencePosition` odkazem na prázdný segment tento segment zachová.
- `ReadOnlySequence<T>.Slice`s int přeskočí prázdné segmenty.
- Výčet `ReadOnlySequence<T>` výčet prázdné segmenty.

### <a name="potential-problems-with-readonlysequencet-and-sequenceposition"></a>Potenciální problémy s\<> A SequencePosition ReadOnlySequence T a SequencePosition

Existuje několik neobvyklých výsledků při `ReadOnlySequence<T>` / `SequencePosition` jednání s `ReadOnlySpan<T>` / `ReadOnlyMemory<T>` / `T[]` / `int`vs normální :

- `SequencePosition`je značka pozice pro `ReadOnlySequence<T>`konkrétní , nikoli absolutní pozici. Vzhledem k tomu, `ReadOnlySequence<T>`že je relativní k určité , `ReadOnlySequence<T>` nemá význam, pokud se používá mimo kde pochází.
- Aritmetika nelze provést `SequencePosition` bez . `ReadOnlySequence<T>` To znamená dělat `position++` základní `ReadOnlySequence<T>.GetPosition(position, 1)`věci, jako je napsáno .
- `GetPosition(long)`**nepodporuje** negativní indexy. To znamená, že je nemožné získat předposlední znak bez chůze všech segmentů.
- Dva `SequencePosition` nelze srovnávat, takže je obtížné:
  - Zjistěte, zda je jedna pozice větší nebo menší než jiná pozice.
  - Napište nějaké algoritmy analýzy.
- `ReadOnlySequence<T>`je větší než odkaz na objekt a pokud možno by měl být předán [dovnitř](../../csharp/language-reference/keywords/in-parameter-modifier.md) nebo [ref.](../../csharp/language-reference/keywords/ref.md) Předávání `ReadOnlySequence<T>` `in` nebo `ref` redukuje kopie [struktury](../../csharp/language-reference/builtin-types/struct.md).
- Prázdné segmenty:
  - Jsou platné `ReadOnlySequence<T>`v rámci .
  - Může se objevit při `ReadOnlySequence<T>.TryGet` iterace pomocí metody.
  - Může se objevit krájení `ReadOnlySequence<T>.Slice()` sekvence `SequencePosition` pomocí metody s objekty.

## <a name="sequencereadert"></a>Sekvenční čtečka\<T\>

<xref:System.Buffers.SequenceReader%601>:

- Je nový typ, který byl zaveden v .NET Core 3.0 zjednodušit zpracování `ReadOnlySequence<T>`.
- Sjednocuje rozdíly mezi `ReadOnlySequence<T>` jedním a `ReadOnlySequence<T>`více segmenty .
- Poskytuje pomocné položky pro`byte` čtení `char`binárních a textových dat ( a ), které mohou nebo nemusí být rozděleny mezi segmenty.

Existují integrované metody pro zpracování binárních i oddělených dat. Následující část ukazuje, jak vypadají stejné `SequenceReader<T>`metody s :

### <a name="access-data"></a>Přístup k datům

`SequenceReader<T>`má metody pro výčet dat `ReadOnlySequence<T>` uvnitř přímo. Následující kód je příkladem zpracování `ReadOnlySequence<byte>` `byte` a současně:

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet8)]

Zpřístupní `CurrentSpan` aktuální segmentu `Span`, který je podobný tomu, co bylo provedeno v metodě ručně.

### <a name="use-position"></a>Použít pozici

Následující kód je příkladem `FindIndexOf` implementace `SequenceReader<T>`pomocí :

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet9)]

### <a name="process-binary-data"></a>Zpracovat binární data

Následující příklad analyzuje 4bajtovou délku velkého endianového celého čísla `ReadOnlySequence<byte>`od začátku .

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet11)]

### <a name="process-text-data"></a>Zpracování textových dat

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet10)]

### <a name="sequencereadert-common-problems"></a>Sekvenční čtečka\<T\> běžné problémy

- Protože `SequenceReader<T>` je proměnlivá struktura, měla by být vždy předána [odkazem](../../csharp/language-reference/keywords/ref.md).
- `SequenceReader<T>`je [ref struct,](../../csharp/language-reference/builtin-types/struct.md#ref-struct) takže jej lze použít pouze v synchronních metodách a nemůže být uložen v polích. Další informace naleznete v [tématu Zápis bezpečné a efektivní kód jazyka C#](../../csharp/write-safe-efficient-code.md).
- `SequenceReader<T>`je optimalizován pro použití jako čtečka pouze pro předávání. `Rewind`je určen pro malé zálohy, které nelze `Read`řešit `Peek`s `IsNext` využitím jiných , a rozhraní API.
