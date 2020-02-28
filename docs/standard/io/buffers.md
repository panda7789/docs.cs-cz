---
title: System. buffers – .NET
ms.date: 12/05/2019
ms.technology: dotnet-standard
helpviewer_keywords:
- buffers [.NET]
- I/O [.NET], buffers
author: rick-anderson
ms.author: riande
ms.openlocfilehash: f939164cd56b2fb2feeeb171236b0e1171327e19
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2020
ms.locfileid: "78160115"
---
# <a name="work-with-buffers-in-net"></a>Práce s vyrovnávacími paměťmi v .NET

Tento článek poskytuje přehled typů, které pomůžou při čtení dat, která běží napříč více vyrovnávacími paměťmi. Používají se hlavně k podpoře <xref:System.IO.Pipelines.PipeReader> objektů.

## <a name="ibufferwritert"></a>IBufferWriter\<T\>

<xref:System.Buffers.IBufferWriter%601?displayProperty=fullName> je kontraktem synchronního zápisu do vyrovnávací paměti. Na nejnižší úrovni rozhraní:

- Je základní a není obtížné ho použít.
- Umožňuje přístup k <xref:System.Memory%601> nebo <xref:System.Span%601>. `Memory<T>` nebo `Span<T>` lze zapsat do a můžete určit, kolik `T` položek bylo zapsáno.

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet)]

Předchozí metoda:

- Vyžádá vyrovnávací paměť o velikosti alespoň 5 bajtů z `IBufferWriter<byte>` pomocí `GetSpan(5)`.
- Zapíše bajty pro řetězec ASCII "Hello" do vráceného `Span<byte>`.
- Volá <xref:System.Buffers.IBufferWriter%601> k určení, kolik bajtů bylo zapsáno do vyrovnávací paměti.

Tato metoda zápisu používá `Memory<T>`/`Span<T>` vyrovnávací paměti poskytované `IBufferWriter<T>`. Alternativně lze metodu rozšíření <xref:System.Buffers.BuffersExtensions.Write%2A> použít ke zkopírování existující vyrovnávací paměti do `IBufferWriter<T>`. `Write` provádí volání `GetSpan``Advance` /podle potřeby, takže není nutné volat `Advance` po zápisu:

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet2)]

<xref:System.Buffers.ArrayBufferWriter%601> je implementace `IBufferWriter<T>`, jehož záložní úložiště je jediné souvislé pole.

### <a name="ibufferwriter-common-problems"></a>IBufferWriter běžné problémy

- `GetSpan` a `GetMemory` vrátí vyrovnávací paměť s minimální požadovanou velikostí paměti. Neberete přesnou velikost vyrovnávací paměti.
- Není nijak zaručeno, že po sobě jdoucí volání budou vracet stejnou vyrovnávací paměť nebo vyrovnávací paměť se stejnou velikostí.
- Po volání `Advance` pro pokračování v zápisu dalších dat je nutné požádat o novou vyrovnávací paměť. Dříve získanou vyrovnávací paměť nelze zapsat do po volání `Advance`.

## <a name="readonlysequencet"></a>ReadOnlySequence\<T\>

![ReadOnlySequence zobrazování paměti v kanálu a pod tím, že je pozice paměti jen pro čtení.](media/buffers/ro-sequence.png)

<xref:System.Buffers.ReadOnlySequence%601> je struktura, která může představovat souvislou nebo nesouvislou sekvenci `T`. Dá se sestavit z:

1. Položka `T[]`.
1. Položka `ReadOnlyMemory<T>`.
1. Dvojice uzlů propojeného seznamu <xref:System.Buffers.ReadOnlySequenceSegment%601> a index představující počáteční a koncovou pozici sekvence.

Třetí reprezentace je nejzajímavější, protože má dopad na výkon různých operací na `ReadOnlySequence<T>`:

|Obrázek|Operace|Složitost|
---|---|---|
|`T[]`/`ReadOnlyMemory<T>`|`Length`|`O(1)`|
|`T[]`/`ReadOnlyMemory<T>`|`GetPosition(long)`|`O(1)`|
|`T[]`/`ReadOnlyMemory<T>`|`Slice(int, int)`|`O(1)`|
|`T[]`/`ReadOnlyMemory<T>`|`Slice(SequencePostion,  SequencePostion)`|`O(1)`|
|`ReadOnlySequenceSegment<T>`|`Length`|`O(1)`|
|`ReadOnlySequenceSegment<T>`|`GetPosition(long)`|`O(number of segments)`|
|`ReadOnlySequenceSegment<T>`|`Slice(int, int)`|`O(number of segments)`|
|`ReadOnlySequenceSegment<T>`|`Slice(SequencePostion, SequencePostion)`|`O(1)`|

Z důvodu této smíšené reprezentace `ReadOnlySequence<T>` zpřístupňuje indexy jako `SequencePosition` namísto celého čísla. `SequencePosition`:

- Je neprůhledná hodnota, která představuje index do `ReadOnlySequence<T>`, kde pochází.
- Se skládá ze dvou částí typu Integer a Object. Které tyto dvě hodnoty představují, jsou svázány s implementací `ReadOnlySequence<T>`.

### <a name="access-data"></a>Přístup k datům

`ReadOnlySequence<T>` zpřístupňuje data jako vyčíslitelné `ReadOnlyMemory<T>`. Výčet jednotlivých segmentů lze provést pomocí základního příkazu foreach:

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet3)]

Předchozí metoda vyhledá každý segment konkrétního bajtu. Pokud potřebujete sledovat `SequencePosition`jednotlivých segmentů, <xref:System.Buffers.ReadOnlySequence%601.TryGet%2A?displayProperty=nameWithType> je vhodnější. Následující ukázka změní předchozí kód a vrátí `SequencePosition` namísto celého čísla. Vrácení `SequencePosition` má výhodu povolit volajícímu zabránit druhé kontrole, aby získal data na konkrétním indexu.

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet4)]

Kombinace `SequencePosition` a `TryGet` funguje jako enumerátor. Pole pozice je upraveno na začátku každé iterace, aby bylo možné začít každý segment v rámci `ReadOnlySequence<T>`.

Předchozí metoda existuje jako metoda rozšíření v `ReadOnlySequence<T>`. <xref:System.Buffers.BuffersExtensions.PositionOf%2A> lze použít pro zjednodušení předchozího kódu:

```csharp
SequencePosition? FindIndexOf(in ReadOnlySequence<byte> buffer, byte data) => buffer.PositionOf(data);
```

#### <a name="process-a-readonlysequencet"></a>Zpracování ReadOnlySequence\<T\>

Zpracování `ReadOnlySequence<T>` může být náročné, protože data mohou být rozdělena mezi několik segmentů v rámci sekvence. Nejlepšího výkonu dosáhnete rozdělením kódu do dvou cest:

- Rychlá cesta, která se zabývá jediným segmentem – případ.
- Pomalá cesta, která se zabývá rozdělením dat mezi segmenty.

Existuje několik přístupů, které lze použít ke zpracování dat ve více segmentech sekvence:

- Použijte [`SequenceReader<T>`](#sequencereadert).
- Analyzujte segment dat podle segmentů a udržujte si přehled o `SequencePosition` a indexu v rámci analyzovaného segmentu. Tím se zabrání zbytečnému přidělení, ale může být neefektivní, zejména pro malé vyrovnávací paměti.
- Zkopírujte `ReadOnlySequence<T>` do souvislého pole a považovat ho za jednu vyrovnávací paměť:
  - Pokud je velikost `ReadOnlySequence<T>` malá, může být vhodné kopírovat data do vyrovnávací paměti přidělené zásobníkem pomocí operátoru [stackalloc](../../csharp/language-reference/operators/stackalloc.md) .
  - Zkopírujte `ReadOnlySequence<T>` do pole ve fondu pomocí <xref:System.Buffers.ArrayPool%601.Shared%2A?displayProperty=nameWithType>.
  - Použijte [`ReadOnlySequence<T>.ToArray()`](xref:System.Buffers.BuffersExtensions.ToArray%2A). Nedoporučuje se v aktivních cestách, protože přiděluje nový `T[]` haldy.

Následující příklady ukazují některé běžné případy zpracování `ReadOnlySequence<byte>`:

##### <a name="process-binary-data"></a>Zpracovat binární data

Následující příklad analyzuje celé číslo o velikosti 4 bajtu big-endian od začátku `ReadOnlySequence<byte>`.

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet5)]

[!INCLUDE [localized code comments](../../../includes/code-comments-loc.md)]

##### <a name="process-text-data"></a>Zpracování textových dat

Následující příklad:

- Vyhledá první řádek nového řádku (`\r\n`) v `ReadOnlySequence<byte>` a vrátí ho pomocí parametru out ' line '.
- Ořízne tento řádek, kromě `\r\n` ze vstupní vyrovnávací paměti.

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet6)]

##### <a name="empty-segments"></a>Prázdné segmenty

Je platný pro ukládání prázdných segmentů do `ReadOnlySequence<T>`. Při explicitním vyčíslení segmentů může dojít k prázdným segmentům:

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet7)]

Předchozí kód vytvoří `ReadOnlySequence<byte>` s prázdnými segmenty a ukáže, jak tyto prázdné segmenty ovlivňují různá rozhraní API:

- `ReadOnlySequence<T>.Slice` s `SequencePosition` ukazujícím na prázdný segment, který zachovává tento segment.
- `ReadOnlySequence<T>.Slice` s int přeskočí na prázdné segmenty.
- Výčet `ReadOnlySequence<T>` vytvoří výčet prázdných segmentů.

### <a name="potential-problems-with-readonlysequencet-and-sequenceposition"></a>Potenciální problémy s ReadOnlySequence\<T > a SequencePosition

Při práci s `ReadOnlySequence<T>`/`SequencePosition` vs. normální `ReadOnlySpan<T>`/`ReadOnlyMemory<T>`/`T[]`/`int`má několik neobvyklých výsledků:

- `SequencePosition` je značka pozice pro konkrétní `ReadOnlySequence<T>`, nikoli absolutní pozici. Vzhledem k tomu, že je relativní ke konkrétní `ReadOnlySequence<T>`, nemá význam, pokud je použit mimo `ReadOnlySequence<T>`, kde pochází.
- Aritmetické operace nelze provést na `SequencePosition` bez `ReadOnlySequence<T>`. To znamená, že pro `ReadOnlySequence<T>.GetPosition(position, 1)`se napíše základní věci, jako je `position++`.
- `GetPosition(long)` nepodporuje **záporné** indexy. To znamená, že není možné získat druhý k poslednímu znaku bez procházení všech segmentů.
- Nelze porovnat dva `SequencePosition`, což ztěžuje:
  - Zjistěte, zda je jedna pozice větší nebo menší než jiná pozice.
  - Napište nějaké algoritmy analýzy.
- `ReadOnlySequence<T>` je větší než odkaz na objekt a měla by být předána [v](../../csharp/language-reference/keywords/in-parameter-modifier.md) nebo [ref](../../csharp/language-reference/keywords/ref.md) tam, kde je to možné. Předávání `ReadOnlySequence<T>` pomocí `in` nebo `ref` omezuje kopie [struktury](../../csharp/language-reference/builtin-types/struct.md).
- Prázdné segmenty:
  - Jsou platné v rámci `ReadOnlySequence<T>`.
  - Může se zobrazit při iteraci pomocí metody `ReadOnlySequence<T>.TryGet`.
  - Může se zobrazit v průřezu sekvence pomocí metody `ReadOnlySequence<T>.Slice()` s objekty `SequencePosition`.

## <a name="sequencereadert"></a>SequenceReader\<T\>

<xref:System.Buffers.SequenceReader%601>:

- Je nový typ, který byl představen v rozhraní .NET Core 3,0 pro zjednodušení zpracování `ReadOnlySequence<T>`.
- Sjednocuje rozdíly mezi jedním segmentem `ReadOnlySequence<T>` a více segmenty `ReadOnlySequence<T>`.
- Poskytuje nápovědu pro čtení binárních a textových dat (`byte` a `char`), která může nebo nemusí být rozdělená mezi segmenty.

Existují předdefinované metody pro práci se zpracováním binárních i oddělených dat. Následující část ukazuje, jak tyto stejné metody vypadají jako u `SequenceReader<T>`:

### <a name="access-data"></a>Přístup k datům

`SequenceReader<T>` obsahuje metody pro vytváření výčtu dat uvnitř `ReadOnlySequence<T>` přímo. Následující kód je příkladem zpracování `ReadOnlySequence<byte>` `byte` v daném čase:

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet8)]

`CurrentSpan` zpřístupňuje `Span`aktuálního segmentu, což se podobá tomu, co bylo provedeno v metodě ručně.

### <a name="use-position"></a>Použít pozici

Následující kód představuje ukázkovou implementaci `FindIndexOf` pomocí `SequenceReader<T>`:

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet9)]

### <a name="process-binary-data"></a>Zpracovat binární data

Následující příklad analyzuje celé číslo o velikosti 4 bajtu big-endian od začátku `ReadOnlySequence<byte>`.

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet11)]

### <a name="process-text-data"></a>Zpracování textových dat

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet10)]

### <a name="sequencereadert-common-problems"></a>SequenceReader\<T\> běžné problémy

- Protože je `SequenceReader<T>` proměnlivou strukturou, měla by být vždy předána [odkazem](../../csharp/language-reference/keywords/ref.md).
- `SequenceReader<T>` je [Struktura ref](../../csharp/language-reference/keywords/ref.md#ref-struct-types) , aby ji bylo možné použít pouze v synchronních metodách a nelze ji uložit do polí. Další informace najdete v tématu [Zápis bezpečného a C# efektivního kódu](../../csharp/write-safe-efficient-code.md).
- `SequenceReader<T>` je optimalizovaná pro použití jako čtecí modul jenom pro přeposílání. `Rewind` je určený pro malé zálohy, které se nedají řešit s využitím jiných rozhraní API `Read`, `Peek`a `IsNext`.
