---
title: Paměť a rozpětí
ms.date: 10/03/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- Memory<T>
- Span<T>
- buffers"
- pipeline processing
ms.openlocfilehash: b61b1dbbedf4658fe113986fbb4a792a2f574534
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73121987"
---
# <a name="memory--and-span-related-types"></a>Typy související s pamětí a rozsahem

Počínaje rozhraním .NET Core 2.1 obsahuje rozhraní .NET řadu vzájemně propojených typů, které představují souvislou oblast silného typu libovolné paměti. Mezi ně patří:

- <xref:System.Span%601?displayProperty=nameWithType>, typ, který se používá pro přístup k souvislé oblasti paměti. Instance <xref:System.Span%601> může být zálohována polem `T` <xref:System.String>typu , a , vyrovnávací pamětí přidělenou [stackalloc](../../csharp/language-reference/operators/stackalloc.md)nebo ukazatelem na nespravovanou paměť. Vzhledem k tomu, že musí být přidělena v zásobníku, má řadu omezení. Například pole ve třídě nemůže být <xref:System.Span%601>typu , ani nelze použít v asynchronních operacích.

- <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>, neměnná verze <xref:System.Span%601> struktury.

- <xref:System.Memory%601?displayProperty=nameWithType>, souvislá oblast paměti, která je přidělena na spravované haldy spíše než zásobníku. Instance <xref:System.Memory%601> může být zálohována polem `T` <xref:System.String>typu nebo . Protože může být uložen na spravované <xref:System.Memory%601> haldy, nemá <xref:System.Span%601>žádné omezení .

- <xref:System.ReadOnlyMemory%601?displayProperty=nameWithType>, neměnná verze <xref:System.Memory%601> struktury.

- <xref:System.Buffers.MemoryPool%601?displayProperty=nameWithType>, který přiděluje silně zadaný bloky paměti z fondu paměti vlastníkovi. <xref:System.Buffers.IMemoryOwner%601>instance lze pronajmout z bazénu voláním <xref:System.Buffers.MemoryPool%601.Rent%2A?displayProperty=nameWithType> a uvolněna zpět <xref:System.Buffers.MemoryPool%601.Dispose?displayProperty=nameWithType>do bazénu voláním .

- <xref:System.Buffers.IMemoryOwner%601?displayProperty=nameWithType>, který představuje vlastníka bloku paměti a řídí jeho správu životnosti.

- <xref:System.Buffers.MemoryManager%601>, abstraktní základní třídy, která může <xref:System.Memory%601> být <xref:System.Memory%601> použita k nahrazení implementace tak, aby lze zálohovat další typy, jako jsou bezpečné popisovače. <xref:System.Buffers.MemoryManager%601>je určen pro pokročilé scénáře.

- <xref:System.ArraySegment%601>, obálka pro určitý počet prvků pole začínající na určitý index.

- <xref:System.MemoryExtensions?displayProperty=nameWithType>, kolekce metod rozšíření pro převod řetězců, polí a segmentů pole na <xref:System.Memory%601> bloky.

> [!NOTE]
> Pro dřívější architektury <xref:System.Span%601> <xref:System.Memory%601> a jsou k dispozici v [balíčku System.Memory NuGet](https://www.nuget.org/packages/System.Memory/).

Další informace naleznete <xref:System.Buffers?displayProperty=nameWithType> v oboru názvů.

## <a name="working-with-memory-and-span"></a>Práce s pamětí a rozpětím

Vzhledem k tomu, že typy související s pamětí a rozsahem se obvykle používají k ukládání dat <xref:System.Span%601>v <xref:System.Memory%601>kanálu zpracování, je důležité, aby vývojáři při použití , a souvisejících typů dodržovali sadu osvědčených postupů. Tyto osvědčené postupy jsou popsány v [> paměti\<T a pokyny pro použití> span\<t](memory-t-usage-guidelines.md).

## <a name="see-also"></a>Viz také

- <xref:System.Memory%601?displayProperty=nameWithType>
- <xref:System.ReadOnlyMemory%601?displayProperty=nameWithType>
- <xref:System.Span%601?displayProperty=nameWithType>
- <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>
- <xref:System.Buffers?displayProperty=nameWithType>
