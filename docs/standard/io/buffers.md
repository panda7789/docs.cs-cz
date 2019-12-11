---
title: System. buffers – .NET
ms.date: 12/05/2019
ms.technology: dotnet-standard
helpviewer_keywords:
- buffers [.NET]
- I/O [.NET], buffers
author: rick-anderson
ms.author: riande
ms.openlocfilehash: e42f165bfedec3b1fa54615ee7e2a2028f40aadb
ms.sourcegitcommit: 42ed59871db1f29a32b3d8e7abeb20e6eceeda7c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2019
ms.locfileid: "74960493"
---
# <a name="work-with-buffers-in-net"></a><span data-ttu-id="055e7-102">Práce s vyrovnávacími paměťmi v .NET</span><span class="sxs-lookup"><span data-stu-id="055e7-102">Work with Buffers in .NET</span></span>

<span data-ttu-id="055e7-103">Tento článek poskytuje přehled typů, které pomůžou při čtení dat, která běží napříč více vyrovnávacími paměťmi.</span><span class="sxs-lookup"><span data-stu-id="055e7-103">This article provides an overview of types that help read data that runs across multiple buffers.</span></span> <span data-ttu-id="055e7-104">Používají se hlavně k podpoře <xref:System.IO.Pipelines.PipeReader> objektů.</span><span class="sxs-lookup"><span data-stu-id="055e7-104">They're primarily used to support <xref:System.IO.Pipelines.PipeReader> objects.</span></span>

## <a name="ibufferwritert"></a><span data-ttu-id="055e7-105">IBufferWriter\<T\></span><span class="sxs-lookup"><span data-stu-id="055e7-105">IBufferWriter\<T\></span></span>

<span data-ttu-id="055e7-106"><xref:System.Buffers.IBufferWriter%601?displayProperty=fullName> je kontraktem synchronního zápisu do vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="055e7-106"><xref:System.Buffers.IBufferWriter%601?displayProperty=fullName> is a contract for synchronous buffered writing.</span></span> <span data-ttu-id="055e7-107">Na nejnižší úrovni rozhraní:</span><span class="sxs-lookup"><span data-stu-id="055e7-107">At the lowest level, the interface:</span></span>

- <span data-ttu-id="055e7-108">Je základní a není obtížné ho použít.</span><span class="sxs-lookup"><span data-stu-id="055e7-108">Is basic and not difficult to use.</span></span>
- <span data-ttu-id="055e7-109">Umožňuje přístup k <xref:System.Memory%601> nebo <xref:System.Span%601>.</span><span class="sxs-lookup"><span data-stu-id="055e7-109">Allows access to a <xref:System.Memory%601> or <xref:System.Span%601>.</span></span> <span data-ttu-id="055e7-110">`Memory<T>` nebo `Span<T>` lze zapsat do a můžete určit, kolik `T` položek bylo zapsáno.</span><span class="sxs-lookup"><span data-stu-id="055e7-110">The `Memory<T>` or `Span<T>` can be written to and you can determine how many `T` items were written.</span></span>

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet)]

<span data-ttu-id="055e7-111">Předchozí metoda:</span><span class="sxs-lookup"><span data-stu-id="055e7-111">The preceding method:</span></span>

- <span data-ttu-id="055e7-112">Vyžádá vyrovnávací paměť o velikosti alespoň 5 bajtů z `IBufferWriter<byte>` pomocí `GetSpan(5)`.</span><span class="sxs-lookup"><span data-stu-id="055e7-112">Requests a buffer of at least 5 bytes from the `IBufferWriter<byte>` using `GetSpan(5)`.</span></span>
- <span data-ttu-id="055e7-113">Zapíše bajty pro řetězec ASCII "Hello" do vráceného `Span<byte>`.</span><span class="sxs-lookup"><span data-stu-id="055e7-113">Writes bytes for the ASCII string "Hello" to the returned `Span<byte>`.</span></span>
- <span data-ttu-id="055e7-114">Volá <xref:System.Buffers.IBufferWriter%601> k určení, kolik bajtů bylo zapsáno do vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="055e7-114">Calls  <xref:System.Buffers.IBufferWriter%601> to indicate how many bytes were written to the buffer.</span></span>

<span data-ttu-id="055e7-115">Tato metoda zápisu používá `Memory<T>`/`Span<T>` vyrovnávací paměti poskytované `IBufferWriter<T>`.</span><span class="sxs-lookup"><span data-stu-id="055e7-115">This method of writing uses the `Memory<T>`/`Span<T>` buffer provided by the `IBufferWriter<T>`.</span></span> <span data-ttu-id="055e7-116">Alternativně lze metodu rozšíření <xref:System.Buffers.BuffersExtensions.Write%2A> použít ke zkopírování existující vyrovnávací paměti do `IBufferWriter<T>`.</span><span class="sxs-lookup"><span data-stu-id="055e7-116">Alternatively, the <xref:System.Buffers.BuffersExtensions.Write%2A> extension method can be used to copy an existing buffer to the `IBufferWriter<T>`.</span></span> <span data-ttu-id="055e7-117">`Write` provádí volání `GetSpan``Advance` /podle potřeby, takže není nutné volat `Advance` po zápisu:</span><span class="sxs-lookup"><span data-stu-id="055e7-117">`Write` does the work of calling `GetSpan`/`Advance` as appropriate, so there's no need to call `Advance` after writing:</span></span>

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet2)]

<span data-ttu-id="055e7-118"><xref:System.Buffers.ArrayBufferWriter%601> je implementace `IBufferWriter<T>`, jehož záložní úložiště je jediné souvislé pole.</span><span class="sxs-lookup"><span data-stu-id="055e7-118"><xref:System.Buffers.ArrayBufferWriter%601> is an implementation of `IBufferWriter<T>` whose backing store is a single contiguous array.</span></span>

### <a name="ibufferwriter-common-problems"></a><span data-ttu-id="055e7-119">IBufferWriter běžné problémy</span><span class="sxs-lookup"><span data-stu-id="055e7-119">IBufferWriter common problems</span></span>

- <span data-ttu-id="055e7-120">`GetSpan` a `GetMemory` vrátí vyrovnávací paměť s minimální požadovanou velikostí paměti.</span><span class="sxs-lookup"><span data-stu-id="055e7-120">`GetSpan` and `GetMemory` return a buffer with at least the requested amount of memory.</span></span> <span data-ttu-id="055e7-121">Neberete přesnou velikost vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="055e7-121">Don't assume exact buffer sizes.</span></span>
- <span data-ttu-id="055e7-122">Není nijak zaručeno, že po sobě jdoucí volání budou vracet stejnou vyrovnávací paměť nebo vyrovnávací paměť se stejnou velikostí.</span><span class="sxs-lookup"><span data-stu-id="055e7-122">There's no guarantee that successive calls will return the same buffer or the same-sized buffer.</span></span>
- <span data-ttu-id="055e7-123">Po volání `Advance` pro pokračování v zápisu dalších dat je nutné požádat o novou vyrovnávací paměť.</span><span class="sxs-lookup"><span data-stu-id="055e7-123">A new buffer must be requested after calling `Advance` to continue writing more data.</span></span> <span data-ttu-id="055e7-124">Dříve získanou vyrovnávací paměť nelze zapsat do po volání `Advance`.</span><span class="sxs-lookup"><span data-stu-id="055e7-124">A previously acquired buffer cannot be written to after `Advance` has been called.</span></span>

## <a name="readonlysequencet"></a><span data-ttu-id="055e7-125">ReadOnlySequence\<T\></span><span class="sxs-lookup"><span data-stu-id="055e7-125">ReadOnlySequence\<T\></span></span>

![ReadOnlySequence zobrazování paměti v kanálu a pod tím, že je pozice paměti jen pro čtení.](media/buffers/ro-sequence.png)

<span data-ttu-id="055e7-127"><xref:System.Buffers.ReadOnlySequence%601> je struktura, která může představovat souvislou nebo nesouvislou sekvenci `T`.</span><span class="sxs-lookup"><span data-stu-id="055e7-127"><xref:System.Buffers.ReadOnlySequence%601> is a struct that can represent a contiguous or noncontiguous sequence of `T`.</span></span> <span data-ttu-id="055e7-128">Dá se sestavit z:</span><span class="sxs-lookup"><span data-stu-id="055e7-128">It can be constructed from:</span></span>

1. <span data-ttu-id="055e7-129">A `T[]`</span><span class="sxs-lookup"><span data-stu-id="055e7-129">A `T[]`</span></span>
1. <span data-ttu-id="055e7-130">A `ReadOnlyMemory<T>`</span><span class="sxs-lookup"><span data-stu-id="055e7-130">A `ReadOnlyMemory<T>`</span></span>
1. <span data-ttu-id="055e7-131">Dvojice uzlů propojeného seznamu <xref:System.Buffers.ReadOnlySequenceSegment%601> a index představující počáteční a koncovou pozici sekvence.</span><span class="sxs-lookup"><span data-stu-id="055e7-131">A pair of linked list node <xref:System.Buffers.ReadOnlySequenceSegment%601> and index to represent the start and end position of the sequence.</span></span>

<span data-ttu-id="055e7-132">Třetí reprezentace je nejzajímavější, protože má dopad na výkon různých operací na `ReadOnlySequence<T>`:</span><span class="sxs-lookup"><span data-stu-id="055e7-132">The third representation is the most interesting one as it has performance implications on various operations on the `ReadOnlySequence<T>`:</span></span>

|<span data-ttu-id="055e7-133">Reprezentace</span><span class="sxs-lookup"><span data-stu-id="055e7-133">Representation</span></span>|<span data-ttu-id="055e7-134">Operace</span><span class="sxs-lookup"><span data-stu-id="055e7-134">Operation</span></span>|<span data-ttu-id="055e7-135">Složitost</span><span class="sxs-lookup"><span data-stu-id="055e7-135">Complexity</span></span>|
---|---|---|
|`T[]`/`ReadOnlyMemory<T>`|`Length`|`O(1)`|
|`T[]`/`ReadOnlyMemory<T>`|`GetPosition(long)`|`O(1)`|
|`T[]`/`ReadOnlyMemory<T>`|`Slice(int, int)`|`O(1)`|
|`T[]`/`ReadOnlyMemory<T>`|`Slice(SequencePostion,  SequencePostion)`|`O(1)`|
|`ReadOnlySequenceSegment<T>`|`Length`|`O(1)`|
|`ReadOnlySequenceSegment<T>`|`GetPosition(long)`|`O(number of segments)`|
|`ReadOnlySequenceSegment<T>`|`Slice(int, int)`|`O(number of segments)`|
|`ReadOnlySequenceSegment<T>`|`Slice(SequencePostion, SequencePostion)`|`O(1)`|

<span data-ttu-id="055e7-136">Z důvodu této smíšené reprezentace `ReadOnlySequence<T>` zpřístupňuje indexy jako `SequencePosition` namísto celého čísla.</span><span class="sxs-lookup"><span data-stu-id="055e7-136">Because of this mixed representation, the `ReadOnlySequence<T>` exposes indexes as `SequencePosition` instead of an integer.</span></span> <span data-ttu-id="055e7-137">`SequencePosition`:</span><span class="sxs-lookup"><span data-stu-id="055e7-137">A `SequencePosition`:</span></span>

- <span data-ttu-id="055e7-138">Je neprůhledná hodnota, která představuje index do `ReadOnlySequence<T>`, kde pochází.</span><span class="sxs-lookup"><span data-stu-id="055e7-138">Is an opaque value that represents an index into the `ReadOnlySequence<T>` where it originated.</span></span>
- <span data-ttu-id="055e7-139">Se skládá ze dvou částí typu Integer a Object.</span><span class="sxs-lookup"><span data-stu-id="055e7-139">Consists of two parts, an integer and an object.</span></span> <span data-ttu-id="055e7-140">Které tyto dvě hodnoty představují, jsou svázány s implementací `ReadOnlySequence<T>`.</span><span class="sxs-lookup"><span data-stu-id="055e7-140">What these two values represent are tied to the implementation of `ReadOnlySequence<T>`.</span></span>

### <a name="access-data"></a><span data-ttu-id="055e7-141">Přístup k datům</span><span class="sxs-lookup"><span data-stu-id="055e7-141">Access data</span></span>

<span data-ttu-id="055e7-142">`ReadOnlySequence<T>` zpřístupňuje data jako vyčíslitelné `ReadOnlyMemory<T>`.</span><span class="sxs-lookup"><span data-stu-id="055e7-142">The `ReadOnlySequence<T>` exposes data as an enumerable of `ReadOnlyMemory<T>`.</span></span> <span data-ttu-id="055e7-143">Výčet jednotlivých segmentů lze provést pomocí základního příkazu foreach:</span><span class="sxs-lookup"><span data-stu-id="055e7-143">Enumerating each of the segments can be done using a basic foreach:</span></span>

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet3)]

<span data-ttu-id="055e7-144">Předchozí metoda vyhledá každý segment konkrétního bajtu.</span><span class="sxs-lookup"><span data-stu-id="055e7-144">The preceding method searches each segment for a specific byte.</span></span> <span data-ttu-id="055e7-145">Pokud potřebujete sledovat `SequencePosition`jednotlivých segmentů, <xref:System.Buffers.ReadOnlySequence%601.TryGet%2A?displayProperty=nameWithType> je vhodnější.</span><span class="sxs-lookup"><span data-stu-id="055e7-145">If you need to keep track of each segment's `SequencePosition`, <xref:System.Buffers.ReadOnlySequence%601.TryGet%2A?displayProperty=nameWithType> is more appropriate.</span></span> <span data-ttu-id="055e7-146">Následující ukázka změní předchozí kód a vrátí `SequencePosition` namísto celého čísla.</span><span class="sxs-lookup"><span data-stu-id="055e7-146">The next sample changes the preceding code to return a `SequencePosition` instead of an integer.</span></span> <span data-ttu-id="055e7-147">Vrácení `SequencePosition` má výhodu povolit volajícímu zabránit druhé kontrole, aby získal data na konkrétním indexu.</span><span class="sxs-lookup"><span data-stu-id="055e7-147">Returning a `SequencePosition` has the benefit of allowing the caller to avoid a second scan to get the data at a specific index.</span></span>

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet4)]

<span data-ttu-id="055e7-148">Kombinace `SequencePosition` a `TryGet` funguje jako enumerátor.</span><span class="sxs-lookup"><span data-stu-id="055e7-148">The combination of `SequencePosition` and `TryGet` acts like an enumerator.</span></span> <span data-ttu-id="055e7-149">Pole pozice je upraveno na začátku každé iterace, aby bylo možné začít každý segment v rámci `ReadOnlySequence<T>`.</span><span class="sxs-lookup"><span data-stu-id="055e7-149">The position field is modified at the start of each iteration to be start of each segment within the `ReadOnlySequence<T>`.</span></span>

<span data-ttu-id="055e7-150">Předchozí metoda existuje jako metoda rozšíření v `ReadOnlySequence<T>`.</span><span class="sxs-lookup"><span data-stu-id="055e7-150">The preceding method exists as an extension method on `ReadOnlySequence<T>`.</span></span> <span data-ttu-id="055e7-151"><xref:System.Buffers.BuffersExtensions.PositionOf%2A> lze použít pro zjednodušení předchozího kódu:</span><span class="sxs-lookup"><span data-stu-id="055e7-151"><xref:System.Buffers.BuffersExtensions.PositionOf%2A> can be used to simplify the preceding code:</span></span>

```csharp
SequencePosition? FindIndexOf(in ReadOnlySequence<byte> buffer, byte data) => buffer.PositionOf(data);
```

#### <a name="process-a-readonlysequencet"></a><span data-ttu-id="055e7-152">Zpracování ReadOnlySequence\<T\></span><span class="sxs-lookup"><span data-stu-id="055e7-152">Process a ReadOnlySequence\<T\></span></span>

<span data-ttu-id="055e7-153">Zpracování `ReadOnlySequence<T>` může být náročné, protože data mohou být rozdělena mezi několik segmentů v rámci sekvence.</span><span class="sxs-lookup"><span data-stu-id="055e7-153">Processing a `ReadOnlySequence<T>` can be challenging since data may be split across multiple segments within the sequence.</span></span> <span data-ttu-id="055e7-154">Nejlepšího výkonu dosáhnete rozdělením kódu do dvou cest:</span><span class="sxs-lookup"><span data-stu-id="055e7-154">For the best performance, split code into two paths:</span></span>

- <span data-ttu-id="055e7-155">Rychlá cesta, která se zabývá jediným segmentem – případ.</span><span class="sxs-lookup"><span data-stu-id="055e7-155">A fast path that deals with the single segment case.</span></span>
- <span data-ttu-id="055e7-156">Pomalá cesta, která se zabývá rozdělením dat mezi segmenty.</span><span class="sxs-lookup"><span data-stu-id="055e7-156">A slow path that deals with the data split across segments.</span></span>

<span data-ttu-id="055e7-157">Existuje několik přístupů, které lze použít ke zpracování dat ve více segmentech sekvence:</span><span class="sxs-lookup"><span data-stu-id="055e7-157">There are a few approaches that can be used to process data in multi-segmented sequences:</span></span>

- <span data-ttu-id="055e7-158">Použijte [`SequenceReader<T>`](#sequencereadert).</span><span class="sxs-lookup"><span data-stu-id="055e7-158">Use the [`SequenceReader<T>`](#sequencereadert).</span></span>
- <span data-ttu-id="055e7-159">Analyzujte segment dat podle segmentů a udržujte si přehled o `SequencePosition` a indexu v rámci analyzovaného segmentu.</span><span class="sxs-lookup"><span data-stu-id="055e7-159">Parse data segment by segment, keeping track of the `SequencePosition` and index within the segment parsed.</span></span> <span data-ttu-id="055e7-160">Tím se zabrání zbytečnému přidělení, ale může být neefektivní, zejména pro malé vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="055e7-160">This avoids unnecessary allocations but may be inefficient, especially for small buffers.</span></span>
- <span data-ttu-id="055e7-161">Zkopírujte `ReadOnlySequence<T>` do souvislého pole a považovat ho za jednu vyrovnávací paměť:</span><span class="sxs-lookup"><span data-stu-id="055e7-161">Copy the `ReadOnlySequence<T>` to a contiguous array and treat it like a single buffer:</span></span>
  - <span data-ttu-id="055e7-162">Pokud je velikost `ReadOnlySequence<T>` malá, může být vhodné kopírovat data do vyrovnávací paměti přidělené zásobníkem pomocí operátoru [stackalloc](../../csharp/language-reference/operators/stackalloc.md) .</span><span class="sxs-lookup"><span data-stu-id="055e7-162">If the size of the `ReadOnlySequence<T>` is small, it may be reasonable to copy the data into a stack-allocated buffer using the [stackalloc](../../csharp/language-reference/operators/stackalloc.md) operator.</span></span>
  - <span data-ttu-id="055e7-163">Zkopírujte `ReadOnlySequence<T>` do pole ve fondu pomocí <xref:System.Buffers.ArrayPool%601.Shared%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="055e7-163">Copy the `ReadOnlySequence<T>` into a pooled array using <xref:System.Buffers.ArrayPool%601.Shared%2A?displayProperty=nameWithType>.</span></span>
  - <span data-ttu-id="055e7-164">Použití [ `ReadOnlySequence<T>.ToArray()` ](xref:System.Buffers.BuffersExtensions.ToArray%2A).</span><span class="sxs-lookup"><span data-stu-id="055e7-164">Use [`ReadOnlySequence<T>.ToArray()`](xref:System.Buffers.BuffersExtensions.ToArray%2A).</span></span> <span data-ttu-id="055e7-165">Nedoporučuje se v aktivních cestách, protože přiděluje nový `T[]` haldy.</span><span class="sxs-lookup"><span data-stu-id="055e7-165">This isn't recommended in hot paths as it allocates a new `T[]` on the heap.</span></span>

<span data-ttu-id="055e7-166">Následující příklady ukazují některé běžné případy zpracování `ReadOnlySequence<byte>`:</span><span class="sxs-lookup"><span data-stu-id="055e7-166">The following examples demonstrate some common cases for processing `ReadOnlySequence<byte>`:</span></span>

##### <a name="process-binary-data"></a><span data-ttu-id="055e7-167">Zpracovat binární data</span><span class="sxs-lookup"><span data-stu-id="055e7-167">Process binary data</span></span>

<span data-ttu-id="055e7-168">Následující příklad analyzuje celé číslo o velikosti 4 bajtu big-endian od začátku `ReadOnlySequence<byte>`.</span><span class="sxs-lookup"><span data-stu-id="055e7-168">The following example parses a 4-byte big-endian integer length from the start of the `ReadOnlySequence<byte>`.</span></span>

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet5)]

##### <a name="process-text-data"></a><span data-ttu-id="055e7-169">Zpracování textových dat</span><span class="sxs-lookup"><span data-stu-id="055e7-169">Process text data</span></span>

<span data-ttu-id="055e7-170">Následující příklad:</span><span class="sxs-lookup"><span data-stu-id="055e7-170">The following example:</span></span>

- <span data-ttu-id="055e7-171">Vyhledá první řádek nového řádku (`\r\n`) v `ReadOnlySequence<byte>` a vrátí ho pomocí parametru out ' line '.</span><span class="sxs-lookup"><span data-stu-id="055e7-171">Finds the first newline (`\r\n`) in the `ReadOnlySequence<byte>` and returns it via the out 'line' parameter.</span></span>
- <span data-ttu-id="055e7-172">Ořízne tento řádek, kromě `\r\n` ze vstupní vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="055e7-172">Trims that line, excluding the `\r\n` from the input buffer.</span></span>

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet6)]

##### <a name="empty-segments"></a><span data-ttu-id="055e7-173">Prázdné segmenty</span><span class="sxs-lookup"><span data-stu-id="055e7-173">Empty segments</span></span>

<span data-ttu-id="055e7-174">Je platný pro ukládání prázdných segmentů do `ReadOnlySequence<T>`.</span><span class="sxs-lookup"><span data-stu-id="055e7-174">It's valid to store empty segments inside of a `ReadOnlySequence<T>`.</span></span> <span data-ttu-id="055e7-175">Při explicitním vyčíslení segmentů může dojít k prázdným segmentům:</span><span class="sxs-lookup"><span data-stu-id="055e7-175">Empty segments may occur while enumerating segments explicitly:</span></span>

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet7)]

<span data-ttu-id="055e7-176">Předchozí kód vytvoří `ReadOnlySequence<byte>` s prázdnými segmenty a ukáže, jak tyto prázdné segmenty ovlivňují různá rozhraní API:</span><span class="sxs-lookup"><span data-stu-id="055e7-176">The preceding code creates a `ReadOnlySequence<byte>` with empty segments and shows how those empty segments affect the various APIs:</span></span>

- <span data-ttu-id="055e7-177">`ReadOnlySequence<T>.Slice` s `SequencePosition` ukazujícím na prázdný segment, který zachovává tento segment.</span><span class="sxs-lookup"><span data-stu-id="055e7-177">`ReadOnlySequence<T>.Slice` with a `SequencePosition` pointing to an empty segment preserves that segment.</span></span>
- <span data-ttu-id="055e7-178">`ReadOnlySequence<T>.Slice` s int přeskočí na prázdné segmenty.</span><span class="sxs-lookup"><span data-stu-id="055e7-178">`ReadOnlySequence<T>.Slice` with an int skips over the empty segments.</span></span>
- <span data-ttu-id="055e7-179">Výčet `ReadOnlySequence<T>` vytvoří výčet prázdných segmentů.</span><span class="sxs-lookup"><span data-stu-id="055e7-179">Enumerating the `ReadOnlySequence<T>` enumerates the empty segments.</span></span>

### <a name="potential-problems-with-readonlysequencet-and-sequenceposition"></a><span data-ttu-id="055e7-180">Potenciální problémy s ReadOnlySequence\<T > a SequencePosition</span><span class="sxs-lookup"><span data-stu-id="055e7-180">Potential problems with ReadOnlySequence\<T> and SequencePosition</span></span>

<span data-ttu-id="055e7-181">Při práci s `ReadOnlySequence<T>`/`SequencePosition` vs. normální `ReadOnlySpan<T>`/`ReadOnlyMemory<T>`/`T[]`/`int`má několik neobvyklých výsledků:</span><span class="sxs-lookup"><span data-stu-id="055e7-181">There are several unusual outcomes when dealing with a `ReadOnlySequence<T>`/`SequencePosition` vs. a normal `ReadOnlySpan<T>`/`ReadOnlyMemory<T>`/`T[]`/`int`:</span></span>

- <span data-ttu-id="055e7-182">`SequencePosition` je značka pozice pro konkrétní `ReadOnlySequence<T>`, nikoli absolutní pozici.</span><span class="sxs-lookup"><span data-stu-id="055e7-182">`SequencePosition` is a position marker for a specific `ReadOnlySequence<T>`, not an absolute position.</span></span> <span data-ttu-id="055e7-183">Vzhledem k tomu, že je relativní ke konkrétní `ReadOnlySequence<T>`, nemá význam, pokud je použit mimo `ReadOnlySequence<T>`, kde pochází.</span><span class="sxs-lookup"><span data-stu-id="055e7-183">Because it's relative to a specific `ReadOnlySequence<T>`, it doesn't have meaning if used outside of the `ReadOnlySequence<T>` where it originated.</span></span>
- <span data-ttu-id="055e7-184">Aritmetické operace nelze provést na `SequencePosition` bez `ReadOnlySequence<T>`.</span><span class="sxs-lookup"><span data-stu-id="055e7-184">Arithmetic can't be performed on `SequencePosition` without the `ReadOnlySequence<T>`.</span></span> <span data-ttu-id="055e7-185">To znamená, že pro `ReadOnlySequence<T>.GetPosition(position, 1)`se napíše základní věci, jako je `position++`.</span><span class="sxs-lookup"><span data-stu-id="055e7-185">That means doing basic things like `position++` is written `ReadOnlySequence<T>.GetPosition(position, 1)`.</span></span>
- <span data-ttu-id="055e7-186">`GetPosition(long)` nepodporuje **záporné** indexy.</span><span class="sxs-lookup"><span data-stu-id="055e7-186">`GetPosition(long)` does **not** support negative indexes.</span></span> <span data-ttu-id="055e7-187">To znamená, že není možné získat druhý k poslednímu znaku bez procházení všech segmentů.</span><span class="sxs-lookup"><span data-stu-id="055e7-187">That means it's impossible to get the second to last character without walking all segments.</span></span>
- <span data-ttu-id="055e7-188">Nelze porovnat dva `SequencePosition`, což ztěžuje:</span><span class="sxs-lookup"><span data-stu-id="055e7-188">Two `SequencePosition` can't be compared, making it difficult to:</span></span>
  - <span data-ttu-id="055e7-189">Zjistěte, zda je jedna pozice větší nebo menší než jiná pozice.</span><span class="sxs-lookup"><span data-stu-id="055e7-189">Know if one position is greater than or less than another position.</span></span>
  - <span data-ttu-id="055e7-190">Napište nějaké algoritmy analýzy.</span><span class="sxs-lookup"><span data-stu-id="055e7-190">Write some parsing algorithms.</span></span>
- <span data-ttu-id="055e7-191">`ReadOnlySequence<T>` je větší než odkaz na objekt a měla by být předána [v](../../csharp/language-reference/keywords/in-parameter-modifier.md) nebo [ref](../../csharp/language-reference/keywords/ref.md) tam, kde je to možné.</span><span class="sxs-lookup"><span data-stu-id="055e7-191">`ReadOnlySequence<T>` is bigger than an object reference and should be passed by [in](../../csharp/language-reference/keywords/in-parameter-modifier.md) or [ref](../../csharp/language-reference/keywords/ref.md) where possible.</span></span> <span data-ttu-id="055e7-192">Předávání `ReadOnlySequence<T>` pomocí `in` nebo `ref` omezuje kopie [struktury](../../csharp/language-reference/keywords/struct.md).</span><span class="sxs-lookup"><span data-stu-id="055e7-192">Passing `ReadOnlySequence<T>` by `in` or `ref` reduces copies of the [struct](../../csharp/language-reference/keywords/struct.md).</span></span>
- <span data-ttu-id="055e7-193">Prázdné segmenty:</span><span class="sxs-lookup"><span data-stu-id="055e7-193">Empty segments:</span></span>
  - <span data-ttu-id="055e7-194">Jsou platné v rámci `ReadOnlySequence<T>`.</span><span class="sxs-lookup"><span data-stu-id="055e7-194">Are valid within a `ReadOnlySequence<T>`.</span></span>
  - <span data-ttu-id="055e7-195">Může se zobrazit při iteraci pomocí metody `ReadOnlySequence<T>.TryGet`.</span><span class="sxs-lookup"><span data-stu-id="055e7-195">Can appear when iterating using the `ReadOnlySequence<T>.TryGet` method.</span></span>
  - <span data-ttu-id="055e7-196">Může se zobrazit v průřezu sekvence pomocí metody `ReadOnlySequence<T>.Slice()` s objekty `SequencePosition`.</span><span class="sxs-lookup"><span data-stu-id="055e7-196">Can appear slicing the sequence using the `ReadOnlySequence<T>.Slice()` method with `SequencePosition` objects.</span></span>

## <a name="sequencereadert"></a><span data-ttu-id="055e7-197">SequenceReader\<T\></span><span class="sxs-lookup"><span data-stu-id="055e7-197">SequenceReader\<T\></span></span>

<span data-ttu-id="055e7-198"><xref:System.Buffers.SequenceReader%601>:</span><span class="sxs-lookup"><span data-stu-id="055e7-198"><xref:System.Buffers.SequenceReader%601>:</span></span>

- <span data-ttu-id="055e7-199">Je nový typ, který byl představen v rozhraní .NET Core 3,0 pro zjednodušení zpracování `ReadOnlySequence<T>`.</span><span class="sxs-lookup"><span data-stu-id="055e7-199">Is a new type that was introduced in .NET Core 3.0 to simplify the processing of a `ReadOnlySequence<T>`.</span></span>
- <span data-ttu-id="055e7-200">Sjednocuje rozdíly mezi jedním segmentem `ReadOnlySequence<T>` a více segmenty `ReadOnlySequence<T>`.</span><span class="sxs-lookup"><span data-stu-id="055e7-200">Unifies the differences between a single segment `ReadOnlySequence<T>` and multi-segment `ReadOnlySequence<T>`.</span></span>
- <span data-ttu-id="055e7-201">Poskytuje nápovědu pro čtení binárních a textových dat (`byte` a `char`), která může nebo nemusí být rozdělená mezi segmenty.</span><span class="sxs-lookup"><span data-stu-id="055e7-201">Provides helpers for reading binary and text data (`byte` and `char`) that may or may not be split across segments.</span></span>

<span data-ttu-id="055e7-202">Existují předdefinované metody pro práci se zpracováním binárních i oddělených dat.</span><span class="sxs-lookup"><span data-stu-id="055e7-202">There are built-in methods for dealing with processing both binary and delimited data.</span></span> <span data-ttu-id="055e7-203">Následující část ukazuje, jak tyto stejné metody vypadají jako u `SequenceReader<T>`:</span><span class="sxs-lookup"><span data-stu-id="055e7-203">The following section demonstrates what those same methods look like with the `SequenceReader<T>`:</span></span>

### <a name="access-data"></a><span data-ttu-id="055e7-204">Přístup k datům</span><span class="sxs-lookup"><span data-stu-id="055e7-204">Access data</span></span>

<span data-ttu-id="055e7-205">`SequenceReader<T>` obsahuje metody pro vytváření výčtu dat uvnitř `ReadOnlySequence<T>` přímo.</span><span class="sxs-lookup"><span data-stu-id="055e7-205">`SequenceReader<T>` has methods for enumerating data inside of the `ReadOnlySequence<T>` directly.</span></span> <span data-ttu-id="055e7-206">Následující kód je příkladem zpracování `ReadOnlySequence<byte>` `byte` v daném čase:</span><span class="sxs-lookup"><span data-stu-id="055e7-206">The following code is an example of processing a `ReadOnlySequence<byte>` a `byte` at a time:</span></span>

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet8)]

<span data-ttu-id="055e7-207">`CurrentSpan` zpřístupňuje `Span`aktuálního segmentu, což se podobá tomu, co bylo provedeno v metodě ručně.</span><span class="sxs-lookup"><span data-stu-id="055e7-207">The `CurrentSpan` exposes the current segment's `Span`, which is similar to what was done in the method manually.</span></span>

### <a name="use-position"></a><span data-ttu-id="055e7-208">Použít pozici</span><span class="sxs-lookup"><span data-stu-id="055e7-208">Use position</span></span>

<span data-ttu-id="055e7-209">Následující kód představuje ukázkovou implementaci `FindIndexOf` pomocí `SequenceReader<T>`:</span><span class="sxs-lookup"><span data-stu-id="055e7-209">The following code is an example implementation of `FindIndexOf` using the `SequenceReader<T>`:</span></span>

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet9)]

### <a name="process-binary-data"></a><span data-ttu-id="055e7-210">Zpracovat binární data</span><span class="sxs-lookup"><span data-stu-id="055e7-210">Process binary data</span></span>

<span data-ttu-id="055e7-211">Následující příklad analyzuje celé číslo o velikosti 4 bajtu big-endian od začátku `ReadOnlySequence<byte>`.</span><span class="sxs-lookup"><span data-stu-id="055e7-211">The following example parses a 4-byte big-endian integer length from the start of the `ReadOnlySequence<byte>`.</span></span>

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet11)]

### <a name="process-text-data"></a><span data-ttu-id="055e7-212">Zpracování textových dat</span><span class="sxs-lookup"><span data-stu-id="055e7-212">Process text data</span></span>

[!code-csharp[](~/samples/snippets/csharp/buffers/MyClass.cs?name=snippet10)]

### <a name="sequencereadert-common-problems"></a><span data-ttu-id="055e7-213">SequenceReader\<T\> běžné problémy</span><span class="sxs-lookup"><span data-stu-id="055e7-213">SequenceReader\<T\> common problems</span></span>

- <span data-ttu-id="055e7-214">Protože je `SequenceReader<T>` proměnlivou strukturou, měla by být vždy předána [odkazem](../../csharp/language-reference/keywords/ref.md).</span><span class="sxs-lookup"><span data-stu-id="055e7-214">Because `SequenceReader<T>` is a mutable struct, it should always be passed by [reference](../../csharp/language-reference/keywords/ref.md).</span></span>
- <span data-ttu-id="055e7-215">`SequenceReader<T>` je [Struktura ref](../../csharp/language-reference/keywords/ref.md#ref-struct-types) , aby ji bylo možné použít pouze v synchronních metodách a nelze ji uložit do polí.</span><span class="sxs-lookup"><span data-stu-id="055e7-215">`SequenceReader<T>` is a [ref struct](../../csharp/language-reference/keywords/ref.md#ref-struct-types) so it can only be used in synchronous methods and can't be stored in fields.</span></span> <span data-ttu-id="055e7-216">Další informace najdete v tématu [Zápis bezpečného a C# efektivního kódu](../../csharp/write-safe-efficient-code.md).</span><span class="sxs-lookup"><span data-stu-id="055e7-216">For more information, see [Write safe and efficient C# code](../../csharp/write-safe-efficient-code.md).</span></span>
- <span data-ttu-id="055e7-217">`SequenceReader<T>` je optimalizovaná pro použití jako čtecí modul jenom pro přeposílání.</span><span class="sxs-lookup"><span data-stu-id="055e7-217">`SequenceReader<T>` is optimized for use as a forward-only reader.</span></span> <span data-ttu-id="055e7-218">`Rewind` je určený pro malé zálohy, které se nedají řešit s využitím jiných rozhraní API `Read`, `Peek`a `IsNext`.</span><span class="sxs-lookup"><span data-stu-id="055e7-218">`Rewind` is intended for small backups that can't be addressed utilizing other `Read`, `Peek`, and `IsNext` APIs.</span></span>
