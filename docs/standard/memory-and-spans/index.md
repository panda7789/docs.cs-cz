---
title: Paměť a rozsahy
ms.date: 10/03/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- Memory<T>
- Span<T>
- buffers"
- pipeline processing
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1a61f56eca242db65bd555553132450c3f8af7f6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61909438"
---
# <a name="memory--and-span-related-types"></a>Typy související s pamětí a rozpětí

Počínaje .NET Core 2.1, .NET obsahuje několik vzájemně souvisejících typů, které reprezentují souvislé, silného typu oblast libovolného paměti. Zde jsou některé z nich:

- <xref:System.Span%601?displayProperty=nameWithType>, typ, který se používá pro přístup k oblasti souvislé paměti. A <xref:System.Span%601> instance může být se opírá o pole typu `T`, <xref:System.String>, vyrovnávací paměť přidělena pomocí [stackalloc](~/docs/csharp/language-reference/keywords/stackalloc.md), nebo ukazatel nespravované paměti. Protože má přidělené v zásobníku, má několik omezení. Například nemůže být typu pole ve třídě <xref:System.Span%601>, ani rozpětí slouží v asynchronních operací.

- <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>, neměnné verzi <xref:System.Span%601> struktury.

- <xref:System.Memory%601?displayProperty=nameWithType>, souvislý oblast paměti, která je přidělena na spravované haldě, namísto zásobníku. A <xref:System.Memory%601> instance může být se opírá o pole typu `T` nebo <xref:System.String>. Protože je možné ho uložit na spravované haldě, <xref:System.Memory%601> nemá žádná omezení <xref:System.Span%601>.

- <xref:System.ReadOnlyMemory%601?displayProperty=nameWithType>, neměnné verzi <xref:System.Memory%601> struktury.

- <xref:System.Buffers.MemoryPool%601?displayProperty=nameWithType>, který přiděluje silného typu bloky paměti z fondu paměti na vlastníka. <xref:System.Buffers.IMemoryOwner%601> instance může být pronajatých z fondu voláním <xref:System.Buffers.MemoryPool%601.Rent%2A?displayProperty=nameWithType> a vydávají se zpět do fondu voláním <xref:System.Buffers.MemoryPool%601.Dispose?displayProperty=nameWithType>.

- <xref:System.Buffers.IMemoryOwner%601?displayProperty=nameWithType>, který představuje vlastníka blok paměti a ovládací prvky pro jeho správu životního cyklu.

- <xref:System.Buffers.MemoryManager%601>, abstraktní základní třídu, která lze použít k nahrazení provádění <xref:System.Memory%601> tak, aby <xref:System.Memory%601> lze zálohovat další typy, jako je například bezpečné popisovače. <xref:System.Buffers.MemoryManager%601> je určené pro pokročilé scénáře.

- <xref:System.ArraySegment%601>, obálku po dobu určitého počtu prvků pole, počínaje konkrétním indexem.

- <xref:System.MemoryExtensions?displayProperty=nameWithType>, kolekce rozšiřující metody pro převod řetězce, pole a pole segmenty <xref:System.Memory%601> bloky.

> [!NOTE]
> Pro starší rozhraní <xref:System.Span%601> a <xref:System.Memory%601> jsou k dispozici v [balíček System.Memory NuGet](https://www.nuget.org/packages/System.Memory/).

Další informace najdete v tématu <xref:System.Buffers?displayProperty=nameWithType> oboru názvů.

## <a name="working-with-memory-and-span"></a>Práce s pamětí a rozpětí

Typy související s pamětí a rozsah se obvykle používají k ukládání dat v kanálu zpracování, proto je důležité, že vývojáři následovat sadu osvědčených postupů při použití <xref:System.Span%601>, <xref:System.Memory%601>a souvisejících typů. Tyto osvědčené postupy popsané v [paměti\<T > a rozpětí\<T > Pokyny k používání](memory-t-usage-guidelines.md).

## <a name="see-also"></a>Viz také:

- <xref:System.Memory%601?displayProperty=nameWithType>
- <xref:System.ReadOnlyMemory%601?displayProperty=nameWithType>
- <xref:System.Span%601?displayProperty=nameWithType>
- <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>
- <xref:System.Buffers?displayProperty=nameWithType>