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
# <a name="memory--and-span-related-types"></a><span data-ttu-id="f27f0-102">Typy související s pamětí a rozsahy</span><span class="sxs-lookup"><span data-stu-id="f27f0-102">Memory- and span-related types</span></span>

<span data-ttu-id="f27f0-103">Počínaje rozhraním .NET Core 2,1 obsahuje .NET řadu vzájemně souvisejících typů, které reprezentují souvislou a silně typovou oblast libovolné paměti.</span><span class="sxs-lookup"><span data-stu-id="f27f0-103">Starting with .NET Core 2.1, .NET includes a number of interrelated types that represent a contiguous, strongly typed region of arbitrary memory.</span></span> <span data-ttu-id="f27f0-104">Tady jsou některé z nich:</span><span class="sxs-lookup"><span data-stu-id="f27f0-104">These include:</span></span>

- <span data-ttu-id="f27f0-105"><xref:System.Span%601?displayProperty=nameWithType>, typ, který se používá pro přístup k souvislé oblasti paměti.</span><span class="sxs-lookup"><span data-stu-id="f27f0-105"><xref:System.Span%601?displayProperty=nameWithType>, a type that is used to access a contiguous region of memory.</span></span> <span data-ttu-id="f27f0-106"><xref:System.Span%601>Instance může být zálohována polem typu `T` , a <xref:System.String> , vyrovnávací paměti přidělenou [stackalloc](../../csharp/language-reference/operators/stackalloc.md)nebo ukazatelem na nespravovanou paměť.</span><span class="sxs-lookup"><span data-stu-id="f27f0-106">A <xref:System.Span%601> instance can be backed by an array of type `T`, a <xref:System.String>, a buffer allocated with [stackalloc](../../csharp/language-reference/operators/stackalloc.md), or a pointer to unmanaged memory.</span></span> <span data-ttu-id="f27f0-107">Vzhledem k tomu, že se musí v zásobníku přidělit, má několik omezení.</span><span class="sxs-lookup"><span data-stu-id="f27f0-107">Because it has to be allocated on the stack, it has a number of restrictions.</span></span> <span data-ttu-id="f27f0-108">Například pole ve třídě nemůže být typu <xref:System.Span%601> , ani nemůže být použito v asynchronních operacích.</span><span class="sxs-lookup"><span data-stu-id="f27f0-108">For example, a field in a class cannot be of type <xref:System.Span%601>, nor can span be used in asynchronous operations.</span></span>

- <span data-ttu-id="f27f0-109"><xref:System.ReadOnlySpan%601?displayProperty=nameWithType>, neproměnlivá verze <xref:System.Span%601> struktury.</span><span class="sxs-lookup"><span data-stu-id="f27f0-109"><xref:System.ReadOnlySpan%601?displayProperty=nameWithType>, an immutable version of the <xref:System.Span%601> structure.</span></span>

- <span data-ttu-id="f27f0-110"><xref:System.Memory%601?displayProperty=nameWithType>, souvislá oblast paměti, která je přidělena na spravované haldě, nikoli v zásobníku.</span><span class="sxs-lookup"><span data-stu-id="f27f0-110"><xref:System.Memory%601?displayProperty=nameWithType>, a contiguous region of memory that is allocated on the managed heap rather than the stack.</span></span> <span data-ttu-id="f27f0-111"><xref:System.Memory%601>Instance může být zálohována polem typu `T` nebo <xref:System.String> .</span><span class="sxs-lookup"><span data-stu-id="f27f0-111">A <xref:System.Memory%601> instance can be backed by an array of type `T` or a <xref:System.String>.</span></span> <span data-ttu-id="f27f0-112">Vzhledem k tomu, že může být uložen na spravované haldě, <xref:System.Memory%601> nemá žádná omezení <xref:System.Span%601> .</span><span class="sxs-lookup"><span data-stu-id="f27f0-112">Because it can be stored on the managed heap, <xref:System.Memory%601> has none of the limitations of <xref:System.Span%601>.</span></span>

- <span data-ttu-id="f27f0-113"><xref:System.ReadOnlyMemory%601?displayProperty=nameWithType>, neproměnlivá verze <xref:System.Memory%601> struktury.</span><span class="sxs-lookup"><span data-stu-id="f27f0-113"><xref:System.ReadOnlyMemory%601?displayProperty=nameWithType>, an immutable version of the <xref:System.Memory%601> structure.</span></span>

- <span data-ttu-id="f27f0-114"><xref:System.Buffers.MemoryPool%601?displayProperty=nameWithType>, které přidělují silné typové bloky paměti z fondu paměti vlastníkovi.</span><span class="sxs-lookup"><span data-stu-id="f27f0-114"><xref:System.Buffers.MemoryPool%601?displayProperty=nameWithType>, which allocates strongly typed blocks of memory from a memory pool to an owner.</span></span> <span data-ttu-id="f27f0-115"><xref:System.Buffers.IMemoryOwner%601>instance lze z fondu pronajímat voláním <xref:System.Buffers.MemoryPool%601.Rent%2A?displayProperty=nameWithType> a uvolněním do fondu voláním <xref:System.Buffers.MemoryPool%601.Dispose?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="f27f0-115"><xref:System.Buffers.IMemoryOwner%601> instances can be rented from the pool by calling <xref:System.Buffers.MemoryPool%601.Rent%2A?displayProperty=nameWithType> and released back to the pool by calling <xref:System.Buffers.MemoryPool%601.Dispose?displayProperty=nameWithType>.</span></span>

- <span data-ttu-id="f27f0-116"><xref:System.Buffers.IMemoryOwner%601?displayProperty=nameWithType>, který představuje vlastníka bloku paměti a řídí jeho správu životnosti.</span><span class="sxs-lookup"><span data-stu-id="f27f0-116"><xref:System.Buffers.IMemoryOwner%601?displayProperty=nameWithType>, which represents the owner of a block of memory and controls its lifetime management.</span></span>

- <span data-ttu-id="f27f0-117"><xref:System.Buffers.MemoryManager%601>, abstraktní základní třída, která může být použita k nahrazení implementace <xref:System.Memory%601> tak, aby <xref:System.Memory%601> mohla být zajištěna dalšími typy, jako jsou například bezpečné popisovače.</span><span class="sxs-lookup"><span data-stu-id="f27f0-117"><xref:System.Buffers.MemoryManager%601>, an abstract base class that can be used to replace the implementation of <xref:System.Memory%601> so that <xref:System.Memory%601> can be backed by additional types, such as safe handles.</span></span> <span data-ttu-id="f27f0-118"><xref:System.Buffers.MemoryManager%601>je určený pro pokročilé scénáře.</span><span class="sxs-lookup"><span data-stu-id="f27f0-118"><xref:System.Buffers.MemoryManager%601> is intended for advanced scenarios.</span></span>

- <span data-ttu-id="f27f0-119"><xref:System.ArraySegment%601>, obálka pro určitý počet prvků pole začínajících na konkrétním indexu.</span><span class="sxs-lookup"><span data-stu-id="f27f0-119"><xref:System.ArraySegment%601>, a wrapper for a particular number of array elements starting at a particular index.</span></span>

- <span data-ttu-id="f27f0-120"><xref:System.MemoryExtensions?displayProperty=nameWithType>, kolekce metod rozšíření pro převod řetězců, polí a segmentů pole na <xref:System.Memory%601> bloky.</span><span class="sxs-lookup"><span data-stu-id="f27f0-120"><xref:System.MemoryExtensions?displayProperty=nameWithType>, a collection of extension methods for converting strings, arrays, and array segments to <xref:System.Memory%601> blocks.</span></span>

> [!NOTE]
> <span data-ttu-id="f27f0-121">V dřívějších rozhraních <xref:System.Span%601> a <xref:System.Memory%601> jsou k dispozici v [balíčku NuGet System. Memory](https://www.nuget.org/packages/System.Memory/).</span><span class="sxs-lookup"><span data-stu-id="f27f0-121">For earlier frameworks, <xref:System.Span%601> and <xref:System.Memory%601> are available in the [System.Memory NuGet package](https://www.nuget.org/packages/System.Memory/).</span></span>

<span data-ttu-id="f27f0-122">Další informace najdete v tématu <xref:System.Buffers?displayProperty=nameWithType> obor názvů.</span><span class="sxs-lookup"><span data-stu-id="f27f0-122">For more information, see the <xref:System.Buffers?displayProperty=nameWithType> namespace.</span></span>

## <a name="working-with-memory-and-span"></a><span data-ttu-id="f27f0-123">Práce s pamětí a rozsahem</span><span class="sxs-lookup"><span data-stu-id="f27f0-123">Working with memory and span</span></span>

<span data-ttu-id="f27f0-124">Vzhledem k tomu, že typy související s pamětí a rozsahy se obvykle používají k ukládání dat do zpracovatelského kanálu, je důležité, aby vývojáři při použití <xref:System.Span%601> , a souvisejících typech dodržovali sadu osvědčených postupů <xref:System.Memory%601> .</span><span class="sxs-lookup"><span data-stu-id="f27f0-124">Because the memory- and span-related types are typically used to store data in a processing pipeline, it is important that developers follow a set of best practices when using <xref:System.Span%601>, <xref:System.Memory%601>, and related types.</span></span> <span data-ttu-id="f27f0-125">Tyto osvědčené postupy jsou popsány v článku [ \<T> pokyny k \<T> využití paměti a rozsahu](memory-t-usage-guidelines.md).</span><span class="sxs-lookup"><span data-stu-id="f27f0-125">These best practices are documented in [Memory\<T> and Span\<T> usage guidelines](memory-t-usage-guidelines.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f27f0-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="f27f0-126">See also</span></span>

- <xref:System.Memory%601?displayProperty=nameWithType>
- <xref:System.ReadOnlyMemory%601?displayProperty=nameWithType>
- <xref:System.Span%601?displayProperty=nameWithType>
- <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>
- <xref:System.Buffers?displayProperty=nameWithType>
