---
title: Paměť a rozsahy
ms.date: 10/03/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- Memory<T>
- Span<T>
- buffers"
- pipeline processing
ms.openlocfilehash: b61b1dbbedf4658fe113986fbb4a792a2f574534
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121987"
---
# <a name="memory--and-span-related-types"></a>Typy související s pamětí a rozsahy

Počínaje rozhraním .NET Core 2,1 obsahuje .NET řadu vzájemně souvisejících typů, které znázorňují souvislou a silně typovou oblast libovolné paměti. Zde jsou některé z nich:

- <xref:System.Span%601?displayProperty=nameWithType>typ, který se používá pro přístup k souvislé oblasti paměti. Instance <xref:System.Span%601> může být zálohována polem typu `T`, <xref:System.String>, vyrovnávací pamětí přidělenou [stackalloc](../../csharp/language-reference/operators/stackalloc.md)nebo ukazatelem na nespravovanou paměť. Vzhledem k tomu, že se musí v zásobníku přidělit, má několik omezení. Například pole ve třídě nemůže být typu <xref:System.Span%601>, ani nemůže být použito v asynchronních operacích.

- <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>, neproměnlivá verze <xref:System.Span%601> struktury.

- <xref:System.Memory%601?displayProperty=nameWithType>, souvislou oblast paměti, která je přidělena na spravované haldě, nikoli v zásobníku. Instance <xref:System.Memory%601> může být zálohována polem typu `T` nebo <xref:System.String>. Protože může být uložen na spravované haldě, <xref:System.Memory%601> nemá žádná omezení <xref:System.Span%601>.

- <xref:System.ReadOnlyMemory%601?displayProperty=nameWithType>, neproměnlivá verze <xref:System.Memory%601> struktury.

- <xref:System.Buffers.MemoryPool%601?displayProperty=nameWithType>, které přidělují silné typové bloky paměti z fondu paměti vlastníkovi. instance <xref:System.Buffers.IMemoryOwner%601> můžou být pronajaté z fondu tím, že se zavolají <xref:System.Buffers.MemoryPool%601.Rent%2A?displayProperty=nameWithType> a uvolní se zpátky do fondu voláním <xref:System.Buffers.MemoryPool%601.Dispose?displayProperty=nameWithType>.

- <xref:System.Buffers.IMemoryOwner%601?displayProperty=nameWithType>, který představuje vlastníka bloku paměti a řídí jeho správu životnosti.

- <xref:System.Buffers.MemoryManager%601>, abstraktní základní třída, která může být použita k nahrazení implementace <xref:System.Memory%601>, aby <xref:System.Memory%601> mohla být zajištěna dalšími typy, jako jsou bezpečné popisovače. <xref:System.Buffers.MemoryManager%601> jsou určené pro pokročilé scénáře.

- <xref:System.ArraySegment%601>, obálka pro určitý počet prvků pole začínající na základě konkrétního indexu.

- <xref:System.MemoryExtensions?displayProperty=nameWithType>kolekce metod rozšíření pro převod řetězců, polí a segmentů pole na bloky <xref:System.Memory%601>.

> [!NOTE]
> Pro starší architektury jsou <xref:System.Span%601> a <xref:System.Memory%601> k dispozici v [balíčku System. Memory NuGet](https://www.nuget.org/packages/System.Memory/).

Další informace najdete v tématu obor názvů <xref:System.Buffers?displayProperty=nameWithType>.

## <a name="working-with-memory-and-span"></a>Práce s pamětí a rozsahem

Vzhledem k tomu, že typy související s pamětí a rozsahy se obvykle používají k ukládání dat do zpracovatelského kanálu, je důležité, aby vývojáři při použití <xref:System.Span%601>, <xref:System.Memory%601>a souvisejících typů dodržovali sadu osvědčených postupů. Tyto osvědčené postupy jsou popsány v článku [paměť\<t > a rozpětí\<t >](memory-t-usage-guidelines.md).

## <a name="see-also"></a>Viz také:

- <xref:System.Memory%601?displayProperty=nameWithType>
- <xref:System.ReadOnlyMemory%601?displayProperty=nameWithType>
- <xref:System.Span%601?displayProperty=nameWithType>
- <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>
- <xref:System.Buffers?displayProperty=nameWithType>
