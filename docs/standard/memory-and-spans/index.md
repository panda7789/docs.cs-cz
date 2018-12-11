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
ms.openlocfilehash: 116c08872385406224972e34feaddfe44122355e
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53130879"
---
# <a name="memory--and-span-related-types"></a><span data-ttu-id="42761-102">Typy související s pamětí a rozpětí</span><span class="sxs-lookup"><span data-stu-id="42761-102">Memory- and span-related types</span></span>

<span data-ttu-id="42761-103">Počínaje .NET Core 2.1, .NET obsahuje několik vzájemně souvisejících typů, které reprezentují souvislé, silného typu oblast libovolného paměti.</span><span class="sxs-lookup"><span data-stu-id="42761-103">Starting with .NET Core 2.1, .NET includes a number of interrelated types that represent a contiguous, strongly-typed region of arbitrary memory.</span></span> <span data-ttu-id="42761-104">Zde jsou některé z nich:</span><span class="sxs-lookup"><span data-stu-id="42761-104">These include:</span></span>

- <span data-ttu-id="42761-105"><xref:System.Span%601?displayProperty=nameWithType>, typ, který se používá pro přístup k oblasti souvislé paměti.</span><span class="sxs-lookup"><span data-stu-id="42761-105"><xref:System.Span%601?displayProperty=nameWithType>, a type that is used to access a contiguous region of memory.</span></span> <span data-ttu-id="42761-106">A <xref:System.Span%601> instance může být se opírá o pole typu `T`, <xref:System.String>, vyrovnávací paměť přidělena pomocí [stackalloc](~/docs/csharp/language-reference/keywords/stackalloc.md), nebo ukazatel nespravované paměti.</span><span class="sxs-lookup"><span data-stu-id="42761-106">A <xref:System.Span%601> instance can be backed by an array of type `T`, a <xref:System.String>, a buffer allocated with [stackalloc](~/docs/csharp/language-reference/keywords/stackalloc.md), or a pointer to unmanaged memory.</span></span> <span data-ttu-id="42761-107">Protože má přidělené v zásobníku, má několik omezení.</span><span class="sxs-lookup"><span data-stu-id="42761-107">Because it has to be allocated on the stack, it has a number of restrictions.</span></span> <span data-ttu-id="42761-108">Například nemůže být typu pole ve třídě <xref:System.Span%601>, ani rozpětí slouží v asynchronních operací.</span><span class="sxs-lookup"><span data-stu-id="42761-108">For example, a field in a class cannot be of type <xref:System.Span%601>, nor can span be used in asynchronous operations.</span></span>

- <span data-ttu-id="42761-109"><xref:System.ReadOnlySpan%601?displayProperty=nameWithtype>, neměnné verzi <xref:System.Span%601> struktury.</span><span class="sxs-lookup"><span data-stu-id="42761-109"><xref:System.ReadOnlySpan%601?displayProperty=nameWithtype>, an immutable version of the <xref:System.Span%601> structure.</span></span>

- <span data-ttu-id="42761-110"><xref:System.Memory%601?displayProperty=nameWithType>, souvislý oblast paměti, která je přidělena na spravované haldě, namísto zásobníku.</span><span class="sxs-lookup"><span data-stu-id="42761-110"><xref:System.Memory%601?displayProperty=nameWithType>, a contiguous region of memory that is allocated on the managed heap rather than the stack.</span></span> <span data-ttu-id="42761-111">A <xref:System.Memory%601> instance může být se opírá o pole typu `T` nebo <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="42761-111">A <xref:System.Memory%601> instance can be backed by an array of type `T` or a <xref:System.String>.</span></span> <span data-ttu-id="42761-112">Protože je možné ho uložit na spravované haldě, <xref:System.Memory%601> nemá žádná omezení <xref:System.Span%601>.</span><span class="sxs-lookup"><span data-stu-id="42761-112">Because it can be stored on the managed heap, <xref:System.Memory%601> has none of the limitations of <xref:System.Span%601>.</span></span>

- <span data-ttu-id="42761-113"><xref:System.ReadOnlyMemory%601?displayProperty=nameWithtype>, neměnné verzi <xref:System.Memory%601> struktury.</span><span class="sxs-lookup"><span data-stu-id="42761-113"><xref:System.ReadOnlyMemory%601?displayProperty=nameWithtype>, an immutable version of the <xref:System.Memory%601> structure.</span></span>

- <span data-ttu-id="42761-114"><xref:System.Buffers.MemoryPool%601?displayProperty=nameWithType>, který přiděluje silného typu bloky paměti z fondu paměti na vlastníka.</span><span class="sxs-lookup"><span data-stu-id="42761-114"><xref:System.Buffers.MemoryPool%601?displayProperty=nameWithType>, which allocates strongly-typed blocks of memory from a memory pool to an owner.</span></span> <span data-ttu-id="42761-115"><xref:System.Buffers.IMemoryOwner%601> instance může být pronajatých z fondu voláním <xref:System.Buffers.MemoryPool%601.Rent%2A?displayProperty=nameWithType> a vydávají se zpět do fondu voláním <xref:System.Buffers.MemoryPool%601.Dispose?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="42761-115"><xref:System.Buffers.IMemoryOwner%601> instances can be rented from the pool by calling <xref:System.Buffers.MemoryPool%601.Rent%2A?displayProperty=nameWithType> and released back to the pool by calling <xref:System.Buffers.MemoryPool%601.Dispose?displayProperty=nameWithType>.</span></span>

- <span data-ttu-id="42761-116"><xref:System.Buffers.IMemoryOwner%601?displayProperty=nameWithType>, který představuje vlastníka blok paměti a ovládací prvky pro jeho správu životního cyklu.</span><span class="sxs-lookup"><span data-stu-id="42761-116"><xref:System.Buffers.IMemoryOwner%601?displayProperty=nameWithType>, which represents the owner of a block of memory and controls its lifetime management.</span></span> 

- <span data-ttu-id="42761-117"><xref:System.Buffers.MemoryManager%601>, abstraktní základní třídu, která lze použít k nahrazení provádění <xref:System.Memory%601> tak, aby <xref:System.Memory%601> lze zálohovat další typy, jako je například bezpečné popisovače.</span><span class="sxs-lookup"><span data-stu-id="42761-117"><xref:System.Buffers.MemoryManager%601>, an abstract base class that can be used to replace the implementation of <xref:System.Memory%601> so that <xref:System.Memory%601> can be backed by additional types, such as safe handles.</span></span> <span data-ttu-id="42761-118"><xref:System.Buffers.MemoryManager%601> je určené pro pokročilé scénáře.</span><span class="sxs-lookup"><span data-stu-id="42761-118"><xref:System.Buffers.MemoryManager%601> is intended for advanced scenarios.</span></span>

- <span data-ttu-id="42761-119"><xref:System.ArraySegment%601>, obálku po dobu určitého počtu prvků pole, počínaje konkrétním indexem.</span><span class="sxs-lookup"><span data-stu-id="42761-119"><xref:System.ArraySegment%601>, a wrapper for a particular number of array elements starting at a particular index.</span></span>

- <span data-ttu-id="42761-120"><xref:System.MemoryExtensions?displayProperty=nameWithType>, kolekce rozšiřující metody pro převod řetězce, pole a pole segmenty <xref:System.Memory%601> bloky.</span><span class="sxs-lookup"><span data-stu-id="42761-120"><xref:System.MemoryExtensions?displayProperty=nameWithType>, a collection of extension methods for converting strings, arrays, and array segments to <xref:System.Memory%601> blocks.</span></span>

> [!NOTE]
> <span data-ttu-id="42761-121">Pro starší rozhraní <xref:System.Span%601> a <xref:System.Memory%601> jsou k dispozici v [balíček System.Memory NuGet](https://www.nuget.org/packages/System.Memory/).</span><span class="sxs-lookup"><span data-stu-id="42761-121">For earlier frameworks, <xref:System.Span%601> and <xref:System.Memory%601> are available in the [System.Memory NuGet package](https://www.nuget.org/packages/System.Memory/).</span></span>

<span data-ttu-id="42761-122">Další informace najdete v tématu <xref:System.Buffers?displayProperty=nameWithType> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="42761-122">For more information, see the <xref:System.Buffers?displayProperty=nameWithType> namespace.</span></span>

## <a name="working-with-memory-and-span"></a><span data-ttu-id="42761-123">Práce s pamětí a rozpětí</span><span class="sxs-lookup"><span data-stu-id="42761-123">Working with memory and span</span></span>

<span data-ttu-id="42761-124">Typy související s pamětí a rozsah se obvykle používají k ukládání dat v kanálu zpracování, proto je důležité, že vývojáři následovat sadu osvědčených postupů při použití <xref:System.Span%601>, <xref:System.Memory%601>a souvisejících typů.</span><span class="sxs-lookup"><span data-stu-id="42761-124">Because the memory- and span-related types are typically used to store data in a processing pipeline, it is important that developers follow a set of best practices when using <xref:System.Span%601>, <xref:System.Memory%601>, and related types.</span></span> <span data-ttu-id="42761-125">Tyto osvědčené postupy popsané v [paměti\<T > a rozpětí\<T > Pokyny k používání](memory-t-usage-guidelines.md).</span><span class="sxs-lookup"><span data-stu-id="42761-125">These best practices are documented in [Memory\<T> and Span\<T> usage guidelines](memory-t-usage-guidelines.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="42761-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="42761-126">See also</span></span>

- <xref:System.Memory%601?displayProperty=nameWithType>
- <xref:System.ReadOnlyMemory%601?displayProperty=nameWithType>
- <xref:System.Span%601?displayProperty=nameWithType>
- <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>
- <xref:System.Buffers?displayProperty=nameWithType>