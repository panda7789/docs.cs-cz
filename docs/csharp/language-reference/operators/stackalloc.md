---
title: operátor stackalloc – C# odkaz
ms.custom: seodec18
ms.date: 09/20/2019
f1_keywords:
- stackalloc_CSharpKeyword
helpviewer_keywords:
- stackalloc operator [C#]
ms.openlocfilehash: 4f3ba6594eb16cf16db6a1de78fe05509c5f4d7d
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75345274"
---
# <a name="stackalloc-operator-c-reference"></a><span data-ttu-id="ceca4-102">stackalloc – operátorC# (Referenční dokumentace)</span><span class="sxs-lookup"><span data-stu-id="ceca4-102">stackalloc operator (C# reference)</span></span>

<span data-ttu-id="ceca4-103">Operátor `stackalloc` přiděluje blok paměti v zásobníku.</span><span class="sxs-lookup"><span data-stu-id="ceca4-103">The `stackalloc` operator allocates a block of memory on the stack.</span></span> <span data-ttu-id="ceca4-104">Blok paměti přidělený zásobníkem, který byl vytvořen během provádění metody, je automaticky zahozen při návratu této metody.</span><span class="sxs-lookup"><span data-stu-id="ceca4-104">A stack allocated memory block created during the method execution is automatically discarded when that method returns.</span></span> <span data-ttu-id="ceca4-105">Nelze explicitně uvolnit paměť přidělenou operátorem `stackalloc`.</span><span class="sxs-lookup"><span data-stu-id="ceca4-105">You cannot explicitly free memory allocated with the `stackalloc` operator.</span></span> <span data-ttu-id="ceca4-106">Blok paměti přidělený zásobníku nepodléhá [uvolňování](../../../standard/garbage-collection/index.md) paměti a nemusí být připnutý s [příkazem`fixed`](../keywords/fixed-statement.md).</span><span class="sxs-lookup"><span data-stu-id="ceca4-106">A stack allocated memory block is not subject to [garbage collection](../../../standard/garbage-collection/index.md) and doesn't have to be pinned with a [`fixed` statement](../keywords/fixed-statement.md).</span></span>

<span data-ttu-id="ceca4-107">Výsledek operátoru `stackalloc` můžete přiřadit proměnné jednoho z následujících typů:</span><span class="sxs-lookup"><span data-stu-id="ceca4-107">You can assign the result of the `stackalloc` operator to a variable of one of the following types:</span></span>

- <span data-ttu-id="ceca4-108">Počínaje C# 7,2 <xref:System.Span%601?displayProperty=nameWithType> nebo <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>, jak ukazuje následující příklad:</span><span class="sxs-lookup"><span data-stu-id="ceca4-108">Beginning with C# 7.2, <xref:System.Span%601?displayProperty=nameWithType> or <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>, as the following example shows:</span></span>

  [!code-csharp[stackalloc span](~/samples/csharp/language-reference/operators/StackallocOperator.cs#AssignToSpan)]

  <span data-ttu-id="ceca4-109">Nemusíte používat [nezabezpečený](../keywords/unsafe.md) kontext, když přiřadíte blok paměti přidělené zásobníku k proměnné <xref:System.Span%601> nebo <xref:System.ReadOnlySpan%601>.</span><span class="sxs-lookup"><span data-stu-id="ceca4-109">You don't have to use an [unsafe](../keywords/unsafe.md) context when you assign a stack allocated memory block to a <xref:System.Span%601> or <xref:System.ReadOnlySpan%601> variable.</span></span>

  <span data-ttu-id="ceca4-110">Při práci s těmito typy můžete použít výraz `stackalloc` ve výrazech [podmíněného](conditional-operator.md) nebo přiřazení, jak ukazuje následující příklad:</span><span class="sxs-lookup"><span data-stu-id="ceca4-110">When you work with those types, you can use a `stackalloc` expression in [conditional](conditional-operator.md) or assignment expressions, as the following example shows:</span></span>

  [!code-csharp[stackalloc expression](~/samples/csharp/language-reference/operators/StackallocOperator.cs#AsExpression)]

  <span data-ttu-id="ceca4-111">Počínaje C# 8,0 můžete použít výraz `stackalloc` v jiných výrazech vždy, když je povolena proměnná <xref:System.Span%601> nebo <xref:System.ReadOnlySpan%601>, jak ukazuje následující příklad:</span><span class="sxs-lookup"><span data-stu-id="ceca4-111">Beginning with C# 8.0, you can use a `stackalloc` expression inside other expressions whenever a <xref:System.Span%601> or <xref:System.ReadOnlySpan%601> variable is allowed, as the following example shows:</span></span>

  [!code-csharp[stackalloc in nested expressions](~/samples/csharp/language-reference/operators/StackallocOperator.cs#Nested)]

  > [!NOTE]
  > <span data-ttu-id="ceca4-112">Pokud je to možné, doporučujeme používat <xref:System.Span%601> nebo <xref:System.ReadOnlySpan%601> typy pro práci s přidělenou pamětí stacku.</span><span class="sxs-lookup"><span data-stu-id="ceca4-112">We recommend using <xref:System.Span%601> or <xref:System.ReadOnlySpan%601> types to work with stack allocated memory whenever possible.</span></span>

- <span data-ttu-id="ceca4-113">[Typ ukazatele](../../programming-guide/unsafe-code-pointers/pointer-types.md), jak ukazuje následující příklad:</span><span class="sxs-lookup"><span data-stu-id="ceca4-113">A [pointer type](../../programming-guide/unsafe-code-pointers/pointer-types.md), as the following example shows:</span></span>

  [!code-csharp[stackalloc pointer](~/samples/csharp/language-reference/operators/StackallocOperator.cs#AssignToPointer)]

  <span data-ttu-id="ceca4-114">Jak ukazuje předchozí příklad, je nutné při práci s typy ukazatelů použít kontext `unsafe`.</span><span class="sxs-lookup"><span data-stu-id="ceca4-114">As the preceding example shows, you must use an `unsafe` context when you work with pointer types.</span></span>

  <span data-ttu-id="ceca4-115">V případě typů ukazatelů můžete použít výraz `stackalloc` pouze v deklaraci lokální proměnné pro inicializaci proměnné.</span><span class="sxs-lookup"><span data-stu-id="ceca4-115">In the case of pointer types, you can use a `stackalloc` expression only in a local variable declaration to initialize the variable.</span></span>

<span data-ttu-id="ceca4-116">Obsah nově přidělené paměti není definován.</span><span class="sxs-lookup"><span data-stu-id="ceca4-116">The content of the newly allocated memory is undefined.</span></span> <span data-ttu-id="ceca4-117">Počínaje C# 7,3 můžete použít syntaxi inicializátoru pole k definování obsahu nově přidělené paměti.</span><span class="sxs-lookup"><span data-stu-id="ceca4-117">Beginning with C# 7.3, you can use array initializer syntax to define the content of the newly allocated memory.</span></span> <span data-ttu-id="ceca4-118">Následující příklad ukazuje různé způsoby, jak to provést:</span><span class="sxs-lookup"><span data-stu-id="ceca4-118">The following example demonstrates various ways to do that:</span></span>

[!code-csharp[stackalloc initialization](~/samples/csharp/language-reference/operators/StackallocOperator.cs#StackallocInit)]

<span data-ttu-id="ceca4-119">Ve výrazu `stackalloc T[E]`musí být `T` [nespravovaného typu](../builtin-types/unmanaged-types.md) a `E` musí být výraz typu [int](../builtin-types/integral-numeric-types.md).</span><span class="sxs-lookup"><span data-stu-id="ceca4-119">In expression `stackalloc T[E]`, `T` must be an [unmanaged type](../builtin-types/unmanaged-types.md) and `E` must be an expression of type [int](../builtin-types/integral-numeric-types.md).</span></span>

## <a name="security"></a><span data-ttu-id="ceca4-120">Zabezpečení –</span><span class="sxs-lookup"><span data-stu-id="ceca4-120">Security</span></span>

<span data-ttu-id="ceca4-121">Použití `stackalloc` v modulu CLR (Common Language Runtime) automaticky povoluje funkce pro detekci přetečení vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="ceca4-121">The use of `stackalloc` automatically enables buffer overrun detection features in the common language runtime (CLR).</span></span> <span data-ttu-id="ceca4-122">Pokud se zjistí přetečení vyrovnávací paměti, proces se ukončí co nejrychleji, aby se minimalizovala pravděpodobnost spuštění škodlivého kódu.</span><span class="sxs-lookup"><span data-stu-id="ceca4-122">If a buffer overrun is detected, the process is terminated as quickly as possible to minimize the chance that malicious code is executed.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="ceca4-123">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="ceca4-123">C# language specification</span></span>

<span data-ttu-id="ceca4-124">Další informace naleznete v části [alokace zásobníku](~/_csharplang/spec/unsafe-code.md#stack-allocation) ve [ C# specifikaci jazyka](~/_csharplang/spec/introduction.md) a v poznámce k návrhu funkce pro [Povolení `stackalloc` ve vnořených kontextech](~/_csharplang/proposals/csharp-8.0/nested-stackalloc.md) .</span><span class="sxs-lookup"><span data-stu-id="ceca4-124">For more information, see the [Stack allocation](~/_csharplang/spec/unsafe-code.md#stack-allocation) section of the [C# language specification](~/_csharplang/spec/introduction.md) and the [Permit `stackalloc` in nested contexts](~/_csharplang/proposals/csharp-8.0/nested-stackalloc.md) feature proposal note.</span></span>

## <a name="see-also"></a><span data-ttu-id="ceca4-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ceca4-125">See also</span></span>

- [<span data-ttu-id="ceca4-126">C#odkaz</span><span class="sxs-lookup"><span data-stu-id="ceca4-126">C# reference</span></span>](../index.md)
- [<span data-ttu-id="ceca4-127">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="ceca4-127">C# operators</span></span>](index.md)
- [<span data-ttu-id="ceca4-128">Operátory související s ukazateli</span><span class="sxs-lookup"><span data-stu-id="ceca4-128">Pointer related operators</span></span>](pointer-related-operators.md)
- [<span data-ttu-id="ceca4-129">Typy ukazatelů</span><span class="sxs-lookup"><span data-stu-id="ceca4-129">Pointer types</span></span>](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="ceca4-130">Typy související s Memory a Span</span><span class="sxs-lookup"><span data-stu-id="ceca4-130">Memory and span-related types</span></span>](../../../standard/memory-and-spans/index.md)
