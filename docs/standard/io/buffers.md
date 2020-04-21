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
# <a name="work-with-buffers-in-net"></a><span data-ttu-id="e79e4-102">Práce s vyrovnávacími paměťmi v rozhraní .NET</span><span class="sxs-lookup"><span data-stu-id="e79e4-102">Work with Buffers in .NET</span></span>

<span data-ttu-id="e79e4-103">Tento článek obsahuje přehled typů, které pomáhají číst data, která běží přes více vyrovnávacích pamětí.</span><span class="sxs-lookup"><span data-stu-id="e79e4-103">This article provides an overview of types that help read data that runs across multiple buffers.</span></span> <span data-ttu-id="e79e4-104">Používají se především k <xref:System.IO.Pipelines.PipeReader> podpoře objektů.</span><span class="sxs-lookup"><span data-stu-id="e79e4-104">They're primarily used to support <xref:System.IO.Pipelines.PipeReader> objects.</span></span>

## <a name="ibufferwritert"></a><span data-ttu-id="e79e4-105">IBufferWriter\<T\></span><span class="sxs-lookup"><span data-stu-id="e79e4-105">IBufferWriter\<T\></span></span>

<span data-ttu-id="e79e4-106"><xref:System.Buffers.IBufferWriter%601?displayProperty=fullName>je smlouva pro synchronní zápis do vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="e79e4-106"><xref:System.Buffers.IBufferWriter%601?displayProperty=fullName> is a contract for synchronous buffered writing.</span></span> <span data-ttu-id="e79e4-107">Na nejnižší úrovni rozhraní:</span><span class="sxs-lookup"><span data-stu-id="e79e4-107">At the lowest level, the interface:</span></span>

- <span data-ttu-id="e79e4-108">Je základní a není těžké používat.</span><span class="sxs-lookup"><span data-stu-id="e79e4-108">Is basic and not difficult to use.</span></span>
- <span data-ttu-id="e79e4-109">Umožňuje přístup <xref:System.Memory%601> k <xref:System.Span%601>nebo .</span><span class="sxs-lookup"><span data-stu-id="e79e4-109">Allows access to a <xref:System.Memory%601> or <xref:System.Span%601>.</span></span> <span data-ttu-id="e79e4-110">Nebo `Memory<T>` `Span<T>` může být zapsána do a `T` můžete určit, kolik položek bylo zapsáno.</span><span class="sxs-lookup"><span data-stu-id="e79e4-110">The `Memory<T>` or `Span<T>` can be written to and you can determine how many `T` items were written.</span></span>

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet)]

<span data-ttu-id="e79e4-111">Předchozí metoda:</span><span class="sxs-lookup"><span data-stu-id="e79e4-111">The preceding method:</span></span>

- <span data-ttu-id="e79e4-112">Požaduje vyrovnávací paměť alespoň 5 bajtů `IBufferWriter<byte>` `GetSpan(5)`z using .</span><span class="sxs-lookup"><span data-stu-id="e79e4-112">Requests a buffer of at least 5 bytes from the `IBufferWriter<byte>` using `GetSpan(5)`.</span></span>
- <span data-ttu-id="e79e4-113">Zapíše bajty pro řetězec ASCII "Hello" na vrácené `Span<byte>`.</span><span class="sxs-lookup"><span data-stu-id="e79e4-113">Writes bytes for the ASCII string "Hello" to the returned `Span<byte>`.</span></span>
- <span data-ttu-id="e79e4-114">Volání <xref:System.Buffers.IBufferWriter%601> označující, kolik bajtů byly zapsány do vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="e79e4-114">Calls  <xref:System.Buffers.IBufferWriter%601> to indicate how many bytes were written to the buffer.</span></span>

<span data-ttu-id="e79e4-115">Tato metoda zápisu `Memory<T>` / `Span<T>` používá vyrovnávací `IBufferWriter<T>`paměť poskytovanou .</span><span class="sxs-lookup"><span data-stu-id="e79e4-115">This method of writing uses the `Memory<T>`/`Span<T>` buffer provided by the `IBufferWriter<T>`.</span></span> <span data-ttu-id="e79e4-116">Alternativně metodu <xref:System.Buffers.BuffersExtensions.Write%2A> rozšíření lze zkopírovat existující vyrovnávací `IBufferWriter<T>`paměť do .</span><span class="sxs-lookup"><span data-stu-id="e79e4-116">Alternatively, the <xref:System.Buffers.BuffersExtensions.Write%2A> extension method can be used to copy an existing buffer to the `IBufferWriter<T>`.</span></span> <span data-ttu-id="e79e4-117">`Write`dělá práci volání `GetSpan` / `Advance` podle potřeby, takže není třeba `Advance` volat po psaní:</span><span class="sxs-lookup"><span data-stu-id="e79e4-117">`Write` does the work of calling `GetSpan`/`Advance` as appropriate, so there's no need to call `Advance` after writing:</span></span>

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet2)]

<span data-ttu-id="e79e4-118"><xref:System.Buffers.ArrayBufferWriter%601>je `IBufferWriter<T>` implementace, jejíž záložní úložiště je jedno souvislé pole.</span><span class="sxs-lookup"><span data-stu-id="e79e4-118"><xref:System.Buffers.ArrayBufferWriter%601> is an implementation of `IBufferWriter<T>` whose backing store is a single contiguous array.</span></span>

### <a name="ibufferwriter-common-problems"></a><span data-ttu-id="e79e4-119">IBufferWriter běžné problémy</span><span class="sxs-lookup"><span data-stu-id="e79e4-119">IBufferWriter common problems</span></span>

- <span data-ttu-id="e79e4-120">`GetSpan`a `GetMemory` vrátit vyrovnávací paměť s alespoň požadované množství paměti.</span><span class="sxs-lookup"><span data-stu-id="e79e4-120">`GetSpan` and `GetMemory` return a buffer with at least the requested amount of memory.</span></span> <span data-ttu-id="e79e4-121">Nepředpokládejte přesné velikosti vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="e79e4-121">Don't assume exact buffer sizes.</span></span>
- <span data-ttu-id="e79e4-122">Neexistuje žádná záruka, že po sobě jdoucí volání vrátí stejnou vyrovnávací paměť nebo vyrovnávací paměť stejné velikosti.</span><span class="sxs-lookup"><span data-stu-id="e79e4-122">There's no guarantee that successive calls will return the same buffer or the same-sized buffer.</span></span>
- <span data-ttu-id="e79e4-123">Nová vyrovnávací paměť musí `Advance` být požadována po volání pokračovat v zápisu další data.</span><span class="sxs-lookup"><span data-stu-id="e79e4-123">A new buffer must be requested after calling `Advance` to continue writing more data.</span></span> <span data-ttu-id="e79e4-124">Dříve získanou `Advance` vyrovnávací paměť nelze zapsat do po byla volána.</span><span class="sxs-lookup"><span data-stu-id="e79e4-124">A previously acquired buffer cannot be written to after `Advance` has been called.</span></span>

## <a name="readonlysequencet"></a><span data-ttu-id="e79e4-125">ReadOnlySequence\<T\></span><span class="sxs-lookup"><span data-stu-id="e79e4-125">ReadOnlySequence\<T\></span></span>

![ReadOnlySequence zobrazující paměť v kanálu a pod touto sekvenční pozicí paměti jen pro čtení](media/buffers/ro-sequence.png)

<span data-ttu-id="e79e4-127"><xref:System.Buffers.ReadOnlySequence%601>je struktura, která může představovat souvislou nebo nesousedící posloupnost . `T`</span><span class="sxs-lookup"><span data-stu-id="e79e4-127"><xref:System.Buffers.ReadOnlySequence%601> is a struct that can represent a contiguous or noncontiguous sequence of `T`.</span></span> <span data-ttu-id="e79e4-128">Může být vyroben z:</span><span class="sxs-lookup"><span data-stu-id="e79e4-128">It can be constructed from:</span></span>

1. <span data-ttu-id="e79e4-129">Položka `T[]`.</span><span class="sxs-lookup"><span data-stu-id="e79e4-129">A `T[]`</span></span>
1. <span data-ttu-id="e79e4-130">Položka `ReadOnlyMemory<T>`.</span><span class="sxs-lookup"><span data-stu-id="e79e4-130">A `ReadOnlyMemory<T>`</span></span>
1. <span data-ttu-id="e79e4-131">Dvojice propojeného uzlu <xref:System.Buffers.ReadOnlySequenceSegment%601> seznamu a indexu představující počáteční a koncovou pozici sekvence.</span><span class="sxs-lookup"><span data-stu-id="e79e4-131">A pair of linked list node <xref:System.Buffers.ReadOnlySequenceSegment%601> and index to represent the start and end position of the sequence.</span></span>

<span data-ttu-id="e79e4-132">Třetí zastoupení je nejzajímavější, protože má vliv na výkon `ReadOnlySequence<T>`na různé operace na :</span><span class="sxs-lookup"><span data-stu-id="e79e4-132">The third representation is the most interesting one as it has performance implications on various operations on the `ReadOnlySequence<T>`:</span></span>

|<span data-ttu-id="e79e4-133">Reprezentace</span><span class="sxs-lookup"><span data-stu-id="e79e4-133">Representation</span></span>|<span data-ttu-id="e79e4-134">Operace</span><span class="sxs-lookup"><span data-stu-id="e79e4-134">Operation</span></span>|<span data-ttu-id="e79e4-135">Složitost</span><span class="sxs-lookup"><span data-stu-id="e79e4-135">Complexity</span></span>|
---|---|---|
|`T[]`/`ReadOnlyMemory<T>`|`Length`|`O(1)`|
|`T[]`/`ReadOnlyMemory<T>`|`GetPosition(long)`|`O(1)`|
|`T[]`/`ReadOnlyMemory<T>`|`Slice(int, int)`|`O(1)`|
|`T[]`/`ReadOnlyMemory<T>`|`Slice(SequencePostion,  SequencePostion)`|`O(1)`|
|`ReadOnlySequenceSegment<T>`|`Length`|`O(1)`|
|`ReadOnlySequenceSegment<T>`|`GetPosition(long)`|`O(number of segments)`|
|`ReadOnlySequenceSegment<T>`|`Slice(int, int)`|`O(number of segments)`|
|`ReadOnlySequenceSegment<T>`|`Slice(SequencePostion, SequencePostion)`|`O(1)`|

<span data-ttu-id="e79e4-136">Z důvodu této smíšené `ReadOnlySequence<T>` reprezentace zpřístupňuje indexy jako `SequencePosition` místo celé číslo.</span><span class="sxs-lookup"><span data-stu-id="e79e4-136">Because of this mixed representation, the `ReadOnlySequence<T>` exposes indexes as `SequencePosition` instead of an integer.</span></span> <span data-ttu-id="e79e4-137">A `SequencePosition`:</span><span class="sxs-lookup"><span data-stu-id="e79e4-137">A `SequencePosition`:</span></span>

- <span data-ttu-id="e79e4-138">Je neprůhledná hodnota, která `ReadOnlySequence<T>` představuje index do kde pochází.</span><span class="sxs-lookup"><span data-stu-id="e79e4-138">Is an opaque value that represents an index into the `ReadOnlySequence<T>` where it originated.</span></span>
- <span data-ttu-id="e79e4-139">Skládá se ze dvou částí, celé číslo a objekt.</span><span class="sxs-lookup"><span data-stu-id="e79e4-139">Consists of two parts, an integer and an object.</span></span> <span data-ttu-id="e79e4-140">Co tyto dvě hodnoty představují, `ReadOnlySequence<T>`jsou vázány na implementaci .</span><span class="sxs-lookup"><span data-stu-id="e79e4-140">What these two values represent are tied to the implementation of `ReadOnlySequence<T>`.</span></span>

### <a name="access-data"></a><span data-ttu-id="e79e4-141">Přístup k datům</span><span class="sxs-lookup"><span data-stu-id="e79e4-141">Access data</span></span>

<span data-ttu-id="e79e4-142">Zpřístupňuje `ReadOnlySequence<T>` data jako výčtu `ReadOnlyMemory<T>`.</span><span class="sxs-lookup"><span data-stu-id="e79e4-142">The `ReadOnlySequence<T>` exposes data as an enumerable of `ReadOnlyMemory<T>`.</span></span> <span data-ttu-id="e79e4-143">Výčet každého segmentu lze provést pomocí základní foreach:</span><span class="sxs-lookup"><span data-stu-id="e79e4-143">Enumerating each of the segments can be done using a basic foreach:</span></span>

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet3)]

<span data-ttu-id="e79e4-144">Předchozí metoda prohledává každý segment pro konkrétní bajt.</span><span class="sxs-lookup"><span data-stu-id="e79e4-144">The preceding method searches each segment for a specific byte.</span></span> <span data-ttu-id="e79e4-145">Pokud potřebujete sledovat každý segment `SequencePosition`, <xref:System.Buffers.ReadOnlySequence%601.TryGet%2A?displayProperty=nameWithType> je vhodnější.</span><span class="sxs-lookup"><span data-stu-id="e79e4-145">If you need to keep track of each segment's `SequencePosition`, <xref:System.Buffers.ReadOnlySequence%601.TryGet%2A?displayProperty=nameWithType> is more appropriate.</span></span> <span data-ttu-id="e79e4-146">Další ukázka změní předchozí kód `SequencePosition` vrátit místo celé číslo.</span><span class="sxs-lookup"><span data-stu-id="e79e4-146">The next sample changes the preceding code to return a `SequencePosition` instead of an integer.</span></span> <span data-ttu-id="e79e4-147">Vrácení `SequencePosition` má tu výhodu, že umožňuje volajícímu vyhnout se druhé skenování získat data na konkrétní index.</span><span class="sxs-lookup"><span data-stu-id="e79e4-147">Returning a `SequencePosition` has the benefit of allowing the caller to avoid a second scan to get the data at a specific index.</span></span>

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet4)]

<span data-ttu-id="e79e4-148">Kombinace `SequencePosition` a `TryGet` působí jako čítač.</span><span class="sxs-lookup"><span data-stu-id="e79e4-148">The combination of `SequencePosition` and `TryGet` acts like an enumerator.</span></span> <span data-ttu-id="e79e4-149">Pole pozice je upraveno na začátku každé iterace `ReadOnlySequence<T>`tak, aby bylo začátkem každého segmentu v rámci .</span><span class="sxs-lookup"><span data-stu-id="e79e4-149">The position field is modified at the start of each iteration to be start of each segment within the `ReadOnlySequence<T>`.</span></span>

<span data-ttu-id="e79e4-150">Předchozí metoda existuje jako metoda rozšíření `ReadOnlySequence<T>`na .</span><span class="sxs-lookup"><span data-stu-id="e79e4-150">The preceding method exists as an extension method on `ReadOnlySequence<T>`.</span></span> <span data-ttu-id="e79e4-151"><xref:System.Buffers.BuffersExtensions.PositionOf%2A>lze použít ke zjednodušení předchozího kódu:</span><span class="sxs-lookup"><span data-stu-id="e79e4-151"><xref:System.Buffers.BuffersExtensions.PositionOf%2A> can be used to simplify the preceding code:</span></span>

```csharp
SequencePosition? FindIndexOf(in ReadOnlySequence<byte> buffer, byte data) => buffer.PositionOf(data);
```

#### <a name="process-a-readonlysequencet"></a><span data-ttu-id="e79e4-152">Zpracování sekvence ReadOnlyT\<T\></span><span class="sxs-lookup"><span data-stu-id="e79e4-152">Process a ReadOnlySequence\<T\></span></span>

<span data-ttu-id="e79e4-153">Zpracování `ReadOnlySequence<T>` může být náročné, protože data mohou být rozdělena mezi více segmentů v rámci sekvence.</span><span class="sxs-lookup"><span data-stu-id="e79e4-153">Processing a `ReadOnlySequence<T>` can be challenging since data may be split across multiple segments within the sequence.</span></span> <span data-ttu-id="e79e4-154">Pro dosažení nejlepšího výkonu rozdělte kód na dvě cesty:</span><span class="sxs-lookup"><span data-stu-id="e79e4-154">For the best performance, split code into two paths:</span></span>

- <span data-ttu-id="e79e4-155">Rychlá cesta, která se zabývá případem jednoho segmentu.</span><span class="sxs-lookup"><span data-stu-id="e79e4-155">A fast path that deals with the single segment case.</span></span>
- <span data-ttu-id="e79e4-156">Pomalá cesta, která se zabývá rozdělením dat mezi segmenty.</span><span class="sxs-lookup"><span data-stu-id="e79e4-156">A slow path that deals with the data split across segments.</span></span>

<span data-ttu-id="e79e4-157">Existuje několik přístupů, které lze použít ke zpracování dat ve vícesegmentových sekvencích:</span><span class="sxs-lookup"><span data-stu-id="e79e4-157">There are a few approaches that can be used to process data in multi-segmented sequences:</span></span>

- <span data-ttu-id="e79e4-158">Použijte [`SequenceReader<T>`](#sequencereadert).</span><span class="sxs-lookup"><span data-stu-id="e79e4-158">Use the [`SequenceReader<T>`](#sequencereadert).</span></span>
- <span data-ttu-id="e79e4-159">Analyzovat datový segment podle segmentu, `SequencePosition` sledování a index v rámci segmentu analyzované.</span><span class="sxs-lookup"><span data-stu-id="e79e4-159">Parse data segment by segment, keeping track of the `SequencePosition` and index within the segment parsed.</span></span> <span data-ttu-id="e79e4-160">Tím se zabrání zbytečné přidělení, ale může být neefektivní, zejména pro malé vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="e79e4-160">This avoids unnecessary allocations but may be inefficient, especially for small buffers.</span></span>
- <span data-ttu-id="e79e4-161">Zkopírujte `ReadOnlySequence<T>` souvislé pole a zacházejte s ním jako s jednou vyrovnávací pamětí:</span><span class="sxs-lookup"><span data-stu-id="e79e4-161">Copy the `ReadOnlySequence<T>` to a contiguous array and treat it like a single buffer:</span></span>
  - <span data-ttu-id="e79e4-162">Pokud `ReadOnlySequence<T>` je malá velikost, může být rozumné zkopírovat data do vyrovnávací paměti přidělené zásobníku pomocí operátoru [stackalloc.](../../csharp/language-reference/operators/stackalloc.md)</span><span class="sxs-lookup"><span data-stu-id="e79e4-162">If the size of the `ReadOnlySequence<T>` is small, it may be reasonable to copy the data into a stack-allocated buffer using the [stackalloc](../../csharp/language-reference/operators/stackalloc.md) operator.</span></span>
  - <span data-ttu-id="e79e4-163">Zkopírujte `ReadOnlySequence<T>` do sdruženého pole pomocí <xref:System.Buffers.ArrayPool%601.Shared%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e79e4-163">Copy the `ReadOnlySequence<T>` into a pooled array using <xref:System.Buffers.ArrayPool%601.Shared%2A?displayProperty=nameWithType>.</span></span>
  - <span data-ttu-id="e79e4-164">Použijte [`ReadOnlySequence<T>.ToArray()`](xref:System.Buffers.BuffersExtensions.ToArray%2A).</span><span class="sxs-lookup"><span data-stu-id="e79e4-164">Use [`ReadOnlySequence<T>.ToArray()`](xref:System.Buffers.BuffersExtensions.ToArray%2A).</span></span> <span data-ttu-id="e79e4-165">To se nedoporučuje v horké cesty, protože `T[]` přiděluje nové na haldě.</span><span class="sxs-lookup"><span data-stu-id="e79e4-165">This isn't recommended in hot paths as it allocates a new `T[]` on the heap.</span></span>

<span data-ttu-id="e79e4-166">Následující příklady ukazují některé běžné `ReadOnlySequence<byte>`případy pro zpracování :</span><span class="sxs-lookup"><span data-stu-id="e79e4-166">The following examples demonstrate some common cases for processing `ReadOnlySequence<byte>`:</span></span>

##### <a name="process-binary-data"></a><span data-ttu-id="e79e4-167">Zpracovat binární data</span><span class="sxs-lookup"><span data-stu-id="e79e4-167">Process binary data</span></span>

<span data-ttu-id="e79e4-168">Následující příklad analyzuje 4bajtovou délku velkého endianového celého čísla `ReadOnlySequence<byte>`od začátku .</span><span class="sxs-lookup"><span data-stu-id="e79e4-168">The following example parses a 4-byte big-endian integer length from the start of the `ReadOnlySequence<byte>`.</span></span>

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet5)]

[!INCLUDE [localized code comments](../../../includes/code-comments-loc.md)]

##### <a name="process-text-data"></a><span data-ttu-id="e79e4-169">Zpracování textových dat</span><span class="sxs-lookup"><span data-stu-id="e79e4-169">Process text data</span></span>

<span data-ttu-id="e79e4-170">Následující příklad:</span><span class="sxs-lookup"><span data-stu-id="e79e4-170">The following example:</span></span>

- <span data-ttu-id="e79e4-171">Najde první nový`\r\n`řádek ( `ReadOnlySequence<byte>` ) v a vrátí jej prostřednictvím out 'line' parametr.</span><span class="sxs-lookup"><span data-stu-id="e79e4-171">Finds the first newline (`\r\n`) in the `ReadOnlySequence<byte>` and returns it via the out 'line' parameter.</span></span>
- <span data-ttu-id="e79e4-172">Ořízne tento `\r\n` řádek, s výjimkou vstupní vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="e79e4-172">Trims that line, excluding the `\r\n` from the input buffer.</span></span>

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet6)]

##### <a name="empty-segments"></a><span data-ttu-id="e79e4-173">Prázdné segmenty</span><span class="sxs-lookup"><span data-stu-id="e79e4-173">Empty segments</span></span>

<span data-ttu-id="e79e4-174">Je platný pro uložení prázdných segmentů uvnitř . `ReadOnlySequence<T>`</span><span class="sxs-lookup"><span data-stu-id="e79e4-174">It's valid to store empty segments inside of a `ReadOnlySequence<T>`.</span></span> <span data-ttu-id="e79e4-175">Prázdné segmenty může dojít při výčtu segmentů explicitně:</span><span class="sxs-lookup"><span data-stu-id="e79e4-175">Empty segments may occur while enumerating segments explicitly:</span></span>

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet7)]

<span data-ttu-id="e79e4-176">Předchozí kód vytvoří `ReadOnlySequence<byte>` s prázdnými segmenty a ukazuje, jak tyto prázdné segmenty ovlivňují různá řešení API:</span><span class="sxs-lookup"><span data-stu-id="e79e4-176">The preceding code creates a `ReadOnlySequence<byte>` with empty segments and shows how those empty segments affect the various APIs:</span></span>

- <span data-ttu-id="e79e4-177">`ReadOnlySequence<T>.Slice`s `SequencePosition` odkazem na prázdný segment tento segment zachová.</span><span class="sxs-lookup"><span data-stu-id="e79e4-177">`ReadOnlySequence<T>.Slice` with a `SequencePosition` pointing to an empty segment preserves that segment.</span></span>
- <span data-ttu-id="e79e4-178">`ReadOnlySequence<T>.Slice`s int přeskočí prázdné segmenty.</span><span class="sxs-lookup"><span data-stu-id="e79e4-178">`ReadOnlySequence<T>.Slice` with an int skips over the empty segments.</span></span>
- <span data-ttu-id="e79e4-179">Výčet `ReadOnlySequence<T>` výčet prázdné segmenty.</span><span class="sxs-lookup"><span data-stu-id="e79e4-179">Enumerating the `ReadOnlySequence<T>` enumerates the empty segments.</span></span>

### <a name="potential-problems-with-readonlysequencet-and-sequenceposition"></a><span data-ttu-id="e79e4-180">Potenciální problémy s\<> A SequencePosition ReadOnlySequence T a SequencePosition</span><span class="sxs-lookup"><span data-stu-id="e79e4-180">Potential problems with ReadOnlySequence\<T> and SequencePosition</span></span>

<span data-ttu-id="e79e4-181">Existuje několik neobvyklých výsledků při `ReadOnlySequence<T>` / `SequencePosition` jednání s `ReadOnlySpan<T>` / `ReadOnlyMemory<T>` / `T[]` / `int`vs normální :</span><span class="sxs-lookup"><span data-stu-id="e79e4-181">There are several unusual outcomes when dealing with a `ReadOnlySequence<T>`/`SequencePosition` vs. a normal `ReadOnlySpan<T>`/`ReadOnlyMemory<T>`/`T[]`/`int`:</span></span>

- <span data-ttu-id="e79e4-182">`SequencePosition`je značka pozice pro `ReadOnlySequence<T>`konkrétní , nikoli absolutní pozici.</span><span class="sxs-lookup"><span data-stu-id="e79e4-182">`SequencePosition` is a position marker for a specific `ReadOnlySequence<T>`, not an absolute position.</span></span> <span data-ttu-id="e79e4-183">Vzhledem k tomu, `ReadOnlySequence<T>`že je relativní k určité , `ReadOnlySequence<T>` nemá význam, pokud se používá mimo kde pochází.</span><span class="sxs-lookup"><span data-stu-id="e79e4-183">Because it's relative to a specific `ReadOnlySequence<T>`, it doesn't have meaning if used outside of the `ReadOnlySequence<T>` where it originated.</span></span>
- <span data-ttu-id="e79e4-184">Aritmetika nelze provést `SequencePosition` bez . `ReadOnlySequence<T>`</span><span class="sxs-lookup"><span data-stu-id="e79e4-184">Arithmetic can't be performed on `SequencePosition` without the `ReadOnlySequence<T>`.</span></span> <span data-ttu-id="e79e4-185">To znamená dělat `position++` základní `ReadOnlySequence<T>.GetPosition(position, 1)`věci, jako je napsáno .</span><span class="sxs-lookup"><span data-stu-id="e79e4-185">That means doing basic things like `position++` is written `ReadOnlySequence<T>.GetPosition(position, 1)`.</span></span>
- <span data-ttu-id="e79e4-186">`GetPosition(long)`**nepodporuje** negativní indexy.</span><span class="sxs-lookup"><span data-stu-id="e79e4-186">`GetPosition(long)` does **not** support negative indexes.</span></span> <span data-ttu-id="e79e4-187">To znamená, že je nemožné získat předposlední znak bez chůze všech segmentů.</span><span class="sxs-lookup"><span data-stu-id="e79e4-187">That means it's impossible to get the second to last character without walking all segments.</span></span>
- <span data-ttu-id="e79e4-188">Dva `SequencePosition` nelze srovnávat, takže je obtížné:</span><span class="sxs-lookup"><span data-stu-id="e79e4-188">Two `SequencePosition` can't be compared, making it difficult to:</span></span>
  - <span data-ttu-id="e79e4-189">Zjistěte, zda je jedna pozice větší nebo menší než jiná pozice.</span><span class="sxs-lookup"><span data-stu-id="e79e4-189">Know if one position is greater than or less than another position.</span></span>
  - <span data-ttu-id="e79e4-190">Napište nějaké algoritmy analýzy.</span><span class="sxs-lookup"><span data-stu-id="e79e4-190">Write some parsing algorithms.</span></span>
- <span data-ttu-id="e79e4-191">`ReadOnlySequence<T>`je větší než odkaz na objekt a pokud možno by měl být předán [dovnitř](../../csharp/language-reference/keywords/in-parameter-modifier.md) nebo [ref.](../../csharp/language-reference/keywords/ref.md)</span><span class="sxs-lookup"><span data-stu-id="e79e4-191">`ReadOnlySequence<T>` is bigger than an object reference and should be passed by [in](../../csharp/language-reference/keywords/in-parameter-modifier.md) or [ref](../../csharp/language-reference/keywords/ref.md) where possible.</span></span> <span data-ttu-id="e79e4-192">Předávání `ReadOnlySequence<T>` `in` nebo `ref` redukuje kopie [struktury](../../csharp/language-reference/builtin-types/struct.md).</span><span class="sxs-lookup"><span data-stu-id="e79e4-192">Passing `ReadOnlySequence<T>` by `in` or `ref` reduces copies of the [struct](../../csharp/language-reference/builtin-types/struct.md).</span></span>
- <span data-ttu-id="e79e4-193">Prázdné segmenty:</span><span class="sxs-lookup"><span data-stu-id="e79e4-193">Empty segments:</span></span>
  - <span data-ttu-id="e79e4-194">Jsou platné `ReadOnlySequence<T>`v rámci .</span><span class="sxs-lookup"><span data-stu-id="e79e4-194">Are valid within a `ReadOnlySequence<T>`.</span></span>
  - <span data-ttu-id="e79e4-195">Může se objevit při `ReadOnlySequence<T>.TryGet` iterace pomocí metody.</span><span class="sxs-lookup"><span data-stu-id="e79e4-195">Can appear when iterating using the `ReadOnlySequence<T>.TryGet` method.</span></span>
  - <span data-ttu-id="e79e4-196">Může se objevit krájení `ReadOnlySequence<T>.Slice()` sekvence `SequencePosition` pomocí metody s objekty.</span><span class="sxs-lookup"><span data-stu-id="e79e4-196">Can appear slicing the sequence using the `ReadOnlySequence<T>.Slice()` method with `SequencePosition` objects.</span></span>

## <a name="sequencereadert"></a><span data-ttu-id="e79e4-197">Sekvenční čtečka\<T\></span><span class="sxs-lookup"><span data-stu-id="e79e4-197">SequenceReader\<T\></span></span>

<span data-ttu-id="e79e4-198"><xref:System.Buffers.SequenceReader%601>:</span><span class="sxs-lookup"><span data-stu-id="e79e4-198"><xref:System.Buffers.SequenceReader%601>:</span></span>

- <span data-ttu-id="e79e4-199">Je nový typ, který byl zaveden v .NET Core 3.0 zjednodušit zpracování `ReadOnlySequence<T>`.</span><span class="sxs-lookup"><span data-stu-id="e79e4-199">Is a new type that was introduced in .NET Core 3.0 to simplify the processing of a `ReadOnlySequence<T>`.</span></span>
- <span data-ttu-id="e79e4-200">Sjednocuje rozdíly mezi `ReadOnlySequence<T>` jedním a `ReadOnlySequence<T>`více segmenty .</span><span class="sxs-lookup"><span data-stu-id="e79e4-200">Unifies the differences between a single segment `ReadOnlySequence<T>` and multi-segment `ReadOnlySequence<T>`.</span></span>
- <span data-ttu-id="e79e4-201">Poskytuje pomocné položky pro`byte` čtení `char`binárních a textových dat ( a ), které mohou nebo nemusí být rozděleny mezi segmenty.</span><span class="sxs-lookup"><span data-stu-id="e79e4-201">Provides helpers for reading binary and text data (`byte` and `char`) that may or may not be split across segments.</span></span>

<span data-ttu-id="e79e4-202">Existují integrované metody pro zpracování binárních i oddělených dat.</span><span class="sxs-lookup"><span data-stu-id="e79e4-202">There are built-in methods for dealing with processing both binary and delimited data.</span></span> <span data-ttu-id="e79e4-203">Následující část ukazuje, jak vypadají stejné `SequenceReader<T>`metody s :</span><span class="sxs-lookup"><span data-stu-id="e79e4-203">The following section demonstrates what those same methods look like with the `SequenceReader<T>`:</span></span>

### <a name="access-data"></a><span data-ttu-id="e79e4-204">Přístup k datům</span><span class="sxs-lookup"><span data-stu-id="e79e4-204">Access data</span></span>

<span data-ttu-id="e79e4-205">`SequenceReader<T>`má metody pro výčet dat `ReadOnlySequence<T>` uvnitř přímo.</span><span class="sxs-lookup"><span data-stu-id="e79e4-205">`SequenceReader<T>` has methods for enumerating data inside of the `ReadOnlySequence<T>` directly.</span></span> <span data-ttu-id="e79e4-206">Následující kód je příkladem zpracování `ReadOnlySequence<byte>` `byte` a současně:</span><span class="sxs-lookup"><span data-stu-id="e79e4-206">The following code is an example of processing a `ReadOnlySequence<byte>` a `byte` at a time:</span></span>

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet8)]

<span data-ttu-id="e79e4-207">Zpřístupní `CurrentSpan` aktuální segmentu `Span`, který je podobný tomu, co bylo provedeno v metodě ručně.</span><span class="sxs-lookup"><span data-stu-id="e79e4-207">The `CurrentSpan` exposes the current segment's `Span`, which is similar to what was done in the method manually.</span></span>

### <a name="use-position"></a><span data-ttu-id="e79e4-208">Použít pozici</span><span class="sxs-lookup"><span data-stu-id="e79e4-208">Use position</span></span>

<span data-ttu-id="e79e4-209">Následující kód je příkladem `FindIndexOf` implementace `SequenceReader<T>`pomocí :</span><span class="sxs-lookup"><span data-stu-id="e79e4-209">The following code is an example implementation of `FindIndexOf` using the `SequenceReader<T>`:</span></span>

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet9)]

### <a name="process-binary-data"></a><span data-ttu-id="e79e4-210">Zpracovat binární data</span><span class="sxs-lookup"><span data-stu-id="e79e4-210">Process binary data</span></span>

<span data-ttu-id="e79e4-211">Následující příklad analyzuje 4bajtovou délku velkého endianového celého čísla `ReadOnlySequence<byte>`od začátku .</span><span class="sxs-lookup"><span data-stu-id="e79e4-211">The following example parses a 4-byte big-endian integer length from the start of the `ReadOnlySequence<byte>`.</span></span>

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet11)]

### <a name="process-text-data"></a><span data-ttu-id="e79e4-212">Zpracování textových dat</span><span class="sxs-lookup"><span data-stu-id="e79e4-212">Process text data</span></span>

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet10)]

### <a name="sequencereadert-common-problems"></a><span data-ttu-id="e79e4-213">Sekvenční čtečka\<T\> běžné problémy</span><span class="sxs-lookup"><span data-stu-id="e79e4-213">SequenceReader\<T\> common problems</span></span>

- <span data-ttu-id="e79e4-214">Protože `SequenceReader<T>` je proměnlivá struktura, měla by být vždy předána [odkazem](../../csharp/language-reference/keywords/ref.md).</span><span class="sxs-lookup"><span data-stu-id="e79e4-214">Because `SequenceReader<T>` is a mutable struct, it should always be passed by [reference](../../csharp/language-reference/keywords/ref.md).</span></span>
- <span data-ttu-id="e79e4-215">`SequenceReader<T>`je [ref struct,](../../csharp/language-reference/builtin-types/struct.md#ref-struct) takže jej lze použít pouze v synchronních metodách a nemůže být uložen v polích.</span><span class="sxs-lookup"><span data-stu-id="e79e4-215">`SequenceReader<T>` is a [ref struct](../../csharp/language-reference/builtin-types/struct.md#ref-struct) so it can only be used in synchronous methods and can't be stored in fields.</span></span> <span data-ttu-id="e79e4-216">Další informace naleznete v [tématu Zápis bezpečné a efektivní kód jazyka C#](../../csharp/write-safe-efficient-code.md).</span><span class="sxs-lookup"><span data-stu-id="e79e4-216">For more information, see [Write safe and efficient C# code](../../csharp/write-safe-efficient-code.md).</span></span>
- <span data-ttu-id="e79e4-217">`SequenceReader<T>`je optimalizován pro použití jako čtečka pouze pro předávání.</span><span class="sxs-lookup"><span data-stu-id="e79e4-217">`SequenceReader<T>` is optimized for use as a forward-only reader.</span></span> <span data-ttu-id="e79e4-218">`Rewind`je určen pro malé zálohy, které nelze `Read`řešit `Peek`s `IsNext` využitím jiných , a rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="e79e4-218">`Rewind` is intended for small backups that can't be addressed utilizing other `Read`, `Peek`, and `IsNext` APIs.</span></span>
