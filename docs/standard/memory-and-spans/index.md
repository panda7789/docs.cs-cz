---
title: Paměť a rozsahy
ms.date: 10/03/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- Memory<T>
- Span<T>
- buffers"
- pipeline processing
ms.openlocfilehash: c60c08d27c0e41228a15e8acdf01a9af28a23762
ms.sourcegitcommit: 71b8f5a2108a0f1a4ef1d8d75c5b3e129ec5ca1e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/29/2020
ms.locfileid: "84201970"
---
# <a name="memory--and-span-related-types"></a>Typy související s pamětí a rozsahy

Počínaje rozhraním .NET Core 2,1 obsahuje .NET řadu vzájemně souvisejících typů, které reprezentují souvislou a silně typovou oblast libovolné paměti. Tady jsou některé z nich:

- <xref:System.Span%601?displayProperty=nameWithType>, typ, který se používá pro přístup k souvislé oblasti paměti. <xref:System.Span%601>Instance může být zálohována polem typu `T` , a <xref:System.String> , vyrovnávací paměti přidělenou [stackalloc](../../csharp/language-reference/operators/stackalloc.md)nebo ukazatelem na nespravovanou paměť. Vzhledem k tomu, že se musí v zásobníku přidělit, má několik omezení. Například pole ve třídě nemůže být typu <xref:System.Span%601> , ani nemůže být použito v asynchronních operacích.

- <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>, neproměnlivá verze <xref:System.Span%601> struktury.

- <xref:System.Memory%601?displayProperty=nameWithType>, souvislá oblast paměti, která je přidělena na spravované haldě, nikoli v zásobníku. <xref:System.Memory%601>Instance může být zálohována polem typu `T` nebo <xref:System.String> . Vzhledem k tomu, že může být uložen na spravované haldě, <xref:System.Memory%601> nemá žádná omezení <xref:System.Span%601> .

- <xref:System.ReadOnlyMemory%601?displayProperty=nameWithType>, neproměnlivá verze <xref:System.Memory%601> struktury.

- <xref:System.Buffers.MemoryPool%601?displayProperty=nameWithType>, které přidělují silné typové bloky paměti z fondu paměti vlastníkovi. <xref:System.Buffers.IMemoryOwner%601>instance lze z fondu pronajímat voláním <xref:System.Buffers.MemoryPool%601.Rent%2A?displayProperty=nameWithType> a uvolněním do fondu voláním <xref:System.Buffers.MemoryPool%601.Dispose?displayProperty=nameWithType> .

- <xref:System.Buffers.IMemoryOwner%601?displayProperty=nameWithType>, který představuje vlastníka bloku paměti a řídí jeho správu životnosti.

- <xref:System.Buffers.MemoryManager%601>, abstraktní základní třída, která může být použita k nahrazení implementace <xref:System.Memory%601> tak, aby <xref:System.Memory%601> mohla být zajištěna dalšími typy, jako jsou například bezpečné popisovače. <xref:System.Buffers.MemoryManager%601>je určený pro pokročilé scénáře.

- <xref:System.ArraySegment%601>, obálka pro určitý počet prvků pole začínajících na konkrétním indexu.

- <xref:System.MemoryExtensions?displayProperty=nameWithType>, kolekce metod rozšíření pro převod řetězců, polí a segmentů pole na <xref:System.Memory%601> bloky.

> [!NOTE]
> V dřívějších rozhraních <xref:System.Span%601> a <xref:System.Memory%601> jsou k dispozici v [balíčku NuGet System. Memory](https://www.nuget.org/packages/System.Memory/).

Další informace najdete v tématu <xref:System.Buffers?displayProperty=nameWithType> obor názvů.

## <a name="working-with-memory-and-span"></a>Práce s pamětí a rozsahem

Vzhledem k tomu, že typy související s pamětí a rozsahy se obvykle používají k ukládání dat do zpracovatelského kanálu, je důležité, aby vývojáři při použití <xref:System.Span%601> , a souvisejících typech dodržovali sadu osvědčených postupů <xref:System.Memory%601> . Tyto osvědčené postupy jsou popsány v článku [ \<T> pokyny k \<T> využití paměti a rozsahu](memory-t-usage-guidelines.md).

## <a name="see-also"></a>Viz také

- <xref:System.Memory%601?displayProperty=nameWithType>
- <xref:System.ReadOnlyMemory%601?displayProperty=nameWithType>
- <xref:System.Span%601?displayProperty=nameWithType>
- <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>
- <xref:System.Buffers?displayProperty=nameWithType>
