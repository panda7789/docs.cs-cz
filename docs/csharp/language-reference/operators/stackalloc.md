---
title: operátor stackalloc – C# odkaz
ms.custom: seodec18
ms.date: 06/10/2019
f1_keywords:
- stackalloc_CSharpKeyword
helpviewer_keywords:
- stackalloc operator [C#]
ms.openlocfilehash: f211acaa8c47ab42a1f7f06cff6c35570cd22b75
ms.sourcegitcommit: 1e7ac70be1b4d89708c0d9552897515f2cbf52c4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68433832"
---
# <a name="stackalloc-operator-c-reference"></a><span data-ttu-id="168ec-102">stackalloc – operátorC# (Referenční dokumentace)</span><span class="sxs-lookup"><span data-stu-id="168ec-102">stackalloc operator (C# reference)</span></span>

<span data-ttu-id="168ec-103">`stackalloc` Operátor přiděluje blok paměti v zásobníku.</span><span class="sxs-lookup"><span data-stu-id="168ec-103">The `stackalloc` operator allocates a block of memory on the stack.</span></span> <span data-ttu-id="168ec-104">Blok paměti přidělený zásobníkem, který byl vytvořen během provádění metody, je automaticky zahozen při návratu této metody.</span><span class="sxs-lookup"><span data-stu-id="168ec-104">A stack allocated memory block created during the method execution is automatically discarded when that method returns.</span></span> <span data-ttu-id="168ec-105">Nemůžete explicitně uvolnit paměť přidělenou `stackalloc` operátorem.</span><span class="sxs-lookup"><span data-stu-id="168ec-105">You cannot explicitly free memory allocated with the `stackalloc` operator.</span></span> <span data-ttu-id="168ec-106">Blok paměti přidělený zásobníku nepodléhá uvolňování [](../../../standard/garbage-collection/index.md) paměti a nemusí být připnutý s [ `fixed` příkazem](../keywords/fixed-statement.md).</span><span class="sxs-lookup"><span data-stu-id="168ec-106">A stack allocated memory block is not subject to [garbage collection](../../../standard/garbage-collection/index.md) and doesn't have to be pinned with the [`fixed` statement](../keywords/fixed-statement.md).</span></span>

<span data-ttu-id="168ec-107">Ve výrazu `stackalloc T[E]` `int` [](../builtin-types/unmanaged-types.md) `E` musí být nespravovaný typ a musí to být výraz typu. `T`</span><span class="sxs-lookup"><span data-stu-id="168ec-107">In expression `stackalloc T[E]`, `T` must be an [unmanaged type](../builtin-types/unmanaged-types.md) and `E` must be an expression of type `int`.</span></span>

<span data-ttu-id="168ec-108">Výsledek `stackalloc` operátoru můžete přiřadit proměnné jednoho z následujících typů:</span><span class="sxs-lookup"><span data-stu-id="168ec-108">You can assign the result of the `stackalloc` operator to a variable of one of the following types:</span></span>

- <span data-ttu-id="168ec-109">Počínaje C# 7,2, <xref:System.Span%601?displayProperty=nameWithType> nebo <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>, jak ukazuje následující příklad:</span><span class="sxs-lookup"><span data-stu-id="168ec-109">Starting with C# 7.2, <xref:System.Span%601?displayProperty=nameWithType> or <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>, as the following example shows:</span></span>

  [!code-csharp[stackalloc span](~/samples/csharp/language-reference/operators/StackallocOperator.cs#AssignToSpan)]

  <span data-ttu-id="168ec-110">Nemusíte používat nezabezpečený kontext, když přiřadíte blok paměti přidělené zásobníku <xref:System.Span%601> k <xref:System.ReadOnlySpan%601> proměnné nebo. [](../keywords/unsafe.md)</span><span class="sxs-lookup"><span data-stu-id="168ec-110">You don't have to use an [unsafe](../keywords/unsafe.md) context when you assign a stack allocated memory block to a <xref:System.Span%601> or <xref:System.ReadOnlySpan%601> variable.</span></span>

  <span data-ttu-id="168ec-111">Při práci s těmito typy můžete použít `stackalloc` výraz ve výrazech [podmíněného](conditional-operator.md) nebo přiřazení, jak ukazuje následující příklad:</span><span class="sxs-lookup"><span data-stu-id="168ec-111">When you work with those types, you can use a `stackalloc` expression in [conditional](conditional-operator.md) or assignment expressions, as the following example shows:</span></span>

  [!code-csharp[stackalloc expression](~/samples/csharp/language-reference/operators/StackallocOperator.cs#AsExpression)]

  > [!NOTE]
  > <span data-ttu-id="168ec-112">Pokud je to <xref:System.Span%601> možné <xref:System.ReadOnlySpan%601> , doporučujeme používat typy nebo pro práci s přidělenou pamětí zásobníku.</span><span class="sxs-lookup"><span data-stu-id="168ec-112">We recommend using <xref:System.Span%601> or <xref:System.ReadOnlySpan%601> types to work with stack allocated memory whenever possible.</span></span>

- <span data-ttu-id="168ec-113">[Typ ukazatele](../../programming-guide/unsafe-code-pointers/pointer-types.md), jak ukazuje následující příklad:</span><span class="sxs-lookup"><span data-stu-id="168ec-113">A [pointer type](../../programming-guide/unsafe-code-pointers/pointer-types.md), as the following example shows:</span></span>

  [!code-csharp[stackalloc pointer](~/samples/csharp/language-reference/operators/StackallocOperator.cs#AssignToPointer)]

  <span data-ttu-id="168ec-114">Jak ukazuje předchozí příklad, je nutné použít `unsafe` kontext při práci s typy ukazatelů.</span><span class="sxs-lookup"><span data-stu-id="168ec-114">As the preceding example shows, you must use an `unsafe` context when you work with pointer types.</span></span>

<span data-ttu-id="168ec-115">Obsah nově přidělené paměti není definován.</span><span class="sxs-lookup"><span data-stu-id="168ec-115">The content of the newly allocated memory is undefined.</span></span> <span data-ttu-id="168ec-116">Počínaje C# 7,3 můžete použít syntaxi inicializátoru pole k definování obsahu nově přidělené paměti.</span><span class="sxs-lookup"><span data-stu-id="168ec-116">Starting with C# 7.3, you can use array initializer syntax to define the content of the newly allocated memory.</span></span> <span data-ttu-id="168ec-117">Následující příklad ukazuje různé způsoby, jak to provést:</span><span class="sxs-lookup"><span data-stu-id="168ec-117">The following example demonstrates various ways to do that:</span></span>

[!code-csharp[stackalloc initialization](~/samples/csharp/language-reference/operators/StackallocOperator.cs#StackallocInit)]

## <a name="security"></a><span data-ttu-id="168ec-118">Zabezpečení</span><span class="sxs-lookup"><span data-stu-id="168ec-118">Security</span></span>

<span data-ttu-id="168ec-119">V modulu CLR `stackalloc` (Common Language Runtime) se použití funkce automaticky zapne k detekci přetečení vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="168ec-119">The use of `stackalloc` automatically enables buffer overrun detection features in the common language runtime (CLR).</span></span> <span data-ttu-id="168ec-120">Pokud se zjistí přetečení vyrovnávací paměti, proces se ukončí co nejrychleji, aby se minimalizovala pravděpodobnost spuštění škodlivého kódu.</span><span class="sxs-lookup"><span data-stu-id="168ec-120">If a buffer overrun is detected, the process is terminated as quickly as possible to minimize the chance that malicious code is executed.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="168ec-121">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="168ec-121">C# language specification</span></span>

<span data-ttu-id="168ec-122">Další informace naleznete v části [alokace zásobníku](~/_csharplang/spec/unsafe-code.md#stack-allocation) ve [ C# specifikaci jazyka](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="168ec-122">For more information, see the [Stack allocation](~/_csharplang/spec/unsafe-code.md#stack-allocation) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="168ec-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="168ec-123">See also</span></span>

- [<span data-ttu-id="168ec-124">C#odkaz</span><span class="sxs-lookup"><span data-stu-id="168ec-124">C# reference</span></span>](../index.md)
- [<span data-ttu-id="168ec-125">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="168ec-125">C# operators</span></span>](index.md)
- [<span data-ttu-id="168ec-126">Operátory související s ukazateli</span><span class="sxs-lookup"><span data-stu-id="168ec-126">Pointer related operators</span></span>](pointer-related-operators.md)
- [<span data-ttu-id="168ec-127">Typy ukazatelů</span><span class="sxs-lookup"><span data-stu-id="168ec-127">Pointer types</span></span>](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="168ec-128">Typy související s Memory a Span</span><span class="sxs-lookup"><span data-stu-id="168ec-128">Memory and span-related types</span></span>](../../../standard/memory-and-spans/index.md)
