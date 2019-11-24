---
title: Fixed Size Buffers - C# Programming Guide
ms.custom: seodec18
ms.date: 04/20/2018
helpviewer_keywords:
- fixed size buffers [C#]
- unsafe buffers [C#]
- unsafe code [C#], fixed size buffers
ms.openlocfilehash: 33af43a69587ffaadd7fcb42fa1d30ee9fc41989
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74429401"
---
# <a name="fixed-size-buffers-c-programming-guide"></a><span data-ttu-id="29658-102">Vyrovnávací paměti pevné velikosti (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="29658-102">Fixed Size Buffers (C# Programming Guide)</span></span>

<span data-ttu-id="29658-103">In C#, you can use the [fixed](../../language-reference/keywords/fixed-statement.md) statement to create a buffer with a fixed size array in a data structure.</span><span class="sxs-lookup"><span data-stu-id="29658-103">In C#, you can use the [fixed](../../language-reference/keywords/fixed-statement.md) statement to create a buffer with a fixed size array in a data structure.</span></span> <span data-ttu-id="29658-104">Fixed size buffers are useful when you write methods that interop with data sources from other languages or platforms.</span><span class="sxs-lookup"><span data-stu-id="29658-104">Fixed size buffers are useful when you write methods that interop with data sources from other languages or platforms.</span></span> <span data-ttu-id="29658-105">The fixed array can take any attributes or modifiers that are allowed for regular struct members.</span><span class="sxs-lookup"><span data-stu-id="29658-105">The fixed array can take any attributes or modifiers that are allowed for regular struct members.</span></span> <span data-ttu-id="29658-106">The only restriction is that the array type must be `bool`, `byte`, `char`, `short`, `int`, `long`, `sbyte`, `ushort`, `uint`, `ulong`, `float`, or `double`.</span><span class="sxs-lookup"><span data-stu-id="29658-106">The only restriction is that the array type must be `bool`, `byte`, `char`, `short`, `int`, `long`, `sbyte`, `ushort`, `uint`, `ulong`, `float`, or `double`.</span></span>

```csharp
private fixed char name[30];
```

## <a name="remarks"></a><span data-ttu-id="29658-107">Poznámky</span><span class="sxs-lookup"><span data-stu-id="29658-107">Remarks</span></span>

<span data-ttu-id="29658-108">In safe code, a C# struct that contains an array does not contain the array elements.</span><span class="sxs-lookup"><span data-stu-id="29658-108">In safe code, a C# struct that contains an array does not contain the array elements.</span></span> <span data-ttu-id="29658-109">Instead, the struct contains a reference to the elements.</span><span class="sxs-lookup"><span data-stu-id="29658-109">Instead, the struct contains a reference to the elements.</span></span> <span data-ttu-id="29658-110">You can embed an array of fixed size in a [struct](../../language-reference/keywords/struct.md) when it is used in an [unsafe](../../language-reference/keywords/unsafe.md) code block.</span><span class="sxs-lookup"><span data-stu-id="29658-110">You can embed an array of fixed size in a [struct](../../language-reference/keywords/struct.md) when it is used in an [unsafe](../../language-reference/keywords/unsafe.md) code block.</span></span>

<span data-ttu-id="29658-111">The following `struct` is 8 bytes in size.</span><span class="sxs-lookup"><span data-stu-id="29658-111">The following `struct` is 8 bytes in size.</span></span> <span data-ttu-id="29658-112">The `pathName` array is a reference:</span><span class="sxs-lookup"><span data-stu-id="29658-112">The `pathName` array is a reference:</span></span>

[!code-csharp[Struct with embedded array](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#6)]

<span data-ttu-id="29658-113">A `struct` can contain an embedded array in unsafe code.</span><span class="sxs-lookup"><span data-stu-id="29658-113">A `struct` can contain an embedded array in unsafe code.</span></span> <span data-ttu-id="29658-114">In the following example, the `fixedBuffer` array has a fixed size.</span><span class="sxs-lookup"><span data-stu-id="29658-114">In the following example, the `fixedBuffer` array has a fixed size.</span></span> <span data-ttu-id="29658-115">You use a `fixed` statement to establish a pointer to the first element.</span><span class="sxs-lookup"><span data-stu-id="29658-115">You use a `fixed` statement to establish a pointer to the first element.</span></span> <span data-ttu-id="29658-116">You access the elements of the array through this pointer.</span><span class="sxs-lookup"><span data-stu-id="29658-116">You access the elements of the array through this pointer.</span></span> <span data-ttu-id="29658-117">The `fixed` statement pins the `fixedBuffer` instance field to a specific location in memory.</span><span class="sxs-lookup"><span data-stu-id="29658-117">The `fixed` statement pins the `fixedBuffer` instance field to a specific location in memory.</span></span>

[!code-csharp[Struct with embedded inline array](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#7)]

<span data-ttu-id="29658-118">The size of the 128 element `char` array is 256 bytes.</span><span class="sxs-lookup"><span data-stu-id="29658-118">The size of the 128 element `char` array is 256 bytes.</span></span> <span data-ttu-id="29658-119">Fixed size [char](../../language-reference/builtin-types/char.md) buffers always take two bytes per character, regardless of the encoding.</span><span class="sxs-lookup"><span data-stu-id="29658-119">Fixed size [char](../../language-reference/builtin-types/char.md) buffers always take two bytes per character, regardless of the encoding.</span></span> <span data-ttu-id="29658-120">This is true even when char buffers are marshaled to API methods or structs with `CharSet = CharSet.Auto` or `CharSet = CharSet.Ansi`.</span><span class="sxs-lookup"><span data-stu-id="29658-120">This is true even when char buffers are marshaled to API methods or structs with `CharSet = CharSet.Auto` or `CharSet = CharSet.Ansi`.</span></span> <span data-ttu-id="29658-121">Další informace najdete v tématu <xref:System.Runtime.InteropServices.CharSet>.</span><span class="sxs-lookup"><span data-stu-id="29658-121">For more information, see <xref:System.Runtime.InteropServices.CharSet>.</span></span>

<span data-ttu-id="29658-122">The  preceding example demonstrates accessing `fixed` fields without pinning, which is available starting with C# 7.3.</span><span class="sxs-lookup"><span data-stu-id="29658-122">The  preceding example demonstrates accessing `fixed` fields without pinning, which is available starting with C# 7.3.</span></span>

<span data-ttu-id="29658-123">Another common fixed-size array is the [bool](../../language-reference/keywords/bool.md) array.</span><span class="sxs-lookup"><span data-stu-id="29658-123">Another common fixed-size array is the [bool](../../language-reference/keywords/bool.md) array.</span></span> <span data-ttu-id="29658-124">The elements in a `bool` array are always one byte in size.</span><span class="sxs-lookup"><span data-stu-id="29658-124">The elements in a `bool` array are always one byte in size.</span></span> <span data-ttu-id="29658-125">`bool` arrays are not appropriate for creating bit arrays or buffers.</span><span class="sxs-lookup"><span data-stu-id="29658-125">`bool` arrays are not appropriate for creating bit arrays or buffers.</span></span>

> [!NOTE]
> <span data-ttu-id="29658-126">Except for memory created by using [stackalloc](../../language-reference/operators/stackalloc.md), the C# compiler and the common language runtime (CLR) do not perform any security buffer overrun checks.</span><span class="sxs-lookup"><span data-stu-id="29658-126">Except for memory created by using [stackalloc](../../language-reference/operators/stackalloc.md), the C# compiler and the common language runtime (CLR) do not perform any security buffer overrun checks.</span></span> <span data-ttu-id="29658-127">As with all unsafe code, use caution.</span><span class="sxs-lookup"><span data-stu-id="29658-127">As with all unsafe code, use caution.</span></span>

<span data-ttu-id="29658-128">Unsafe buffers differ from regular arrays in the following ways:</span><span class="sxs-lookup"><span data-stu-id="29658-128">Unsafe buffers differ from regular arrays in the following ways:</span></span>

- <span data-ttu-id="29658-129">You can only use unsafe buffers in an unsafe context.</span><span class="sxs-lookup"><span data-stu-id="29658-129">You can only use unsafe buffers in an unsafe context.</span></span>
- <span data-ttu-id="29658-130">Unsafe buffers are always vectors, or one-dimensional arrays.</span><span class="sxs-lookup"><span data-stu-id="29658-130">Unsafe buffers are always vectors, or one-dimensional arrays.</span></span>
- <span data-ttu-id="29658-131">The declaration of the array should include a count, such as `char id[8]`.</span><span class="sxs-lookup"><span data-stu-id="29658-131">The declaration of the array should include a count, such as `char id[8]`.</span></span> <span data-ttu-id="29658-132">You cannot use `char id[]`.</span><span class="sxs-lookup"><span data-stu-id="29658-132">You cannot use `char id[]`.</span></span>
- <span data-ttu-id="29658-133">Unsafe buffers can only be instance fields of structs in an unsafe context.</span><span class="sxs-lookup"><span data-stu-id="29658-133">Unsafe buffers can only be instance fields of structs in an unsafe context.</span></span>

## <a name="see-also"></a><span data-ttu-id="29658-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="29658-134">See also</span></span>

- [<span data-ttu-id="29658-135">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="29658-135">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="29658-136">Nebezpečný kód a ukazatele</span><span class="sxs-lookup"><span data-stu-id="29658-136">Unsafe Code and Pointers</span></span>](index.md)
- [<span data-ttu-id="29658-137">fixed – příkaz</span><span class="sxs-lookup"><span data-stu-id="29658-137">fixed Statement</span></span>](../../language-reference/keywords/fixed-statement.md)
- [<span data-ttu-id="29658-138">Interoperabilita</span><span class="sxs-lookup"><span data-stu-id="29658-138">Interoperability</span></span>](../interop/index.md)
