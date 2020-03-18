---
title: operátor stackalloc - odkaz C#
ms.date: 09/20/2019
f1_keywords:
- stackalloc_CSharpKeyword
helpviewer_keywords:
- stackalloc operator [C#]
ms.openlocfilehash: 9c9767e0c9945a9589d049fa7abba192cb928ad5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "78846247"
---
# <a name="stackalloc-operator-c-reference"></a><span data-ttu-id="e495f-102">operátor stackalloc (odkaz C#</span><span class="sxs-lookup"><span data-stu-id="e495f-102">stackalloc operator (C# reference)</span></span>

<span data-ttu-id="e495f-103">Operátor `stackalloc` přiděluje blok paměti v zásobníku.</span><span class="sxs-lookup"><span data-stu-id="e495f-103">The `stackalloc` operator allocates a block of memory on the stack.</span></span> <span data-ttu-id="e495f-104">Blok přidělené paměti zásobníku vytvořený během spuštění metody je automaticky zahozen, když se tato metoda vrátí.</span><span class="sxs-lookup"><span data-stu-id="e495f-104">A stack allocated memory block created during the method execution is automatically discarded when that method returns.</span></span> <span data-ttu-id="e495f-105">Nelze explicitně uvolnit paměť `stackalloc` přidělenou operátoru.</span><span class="sxs-lookup"><span data-stu-id="e495f-105">You cannot explicitly free memory allocated with the `stackalloc` operator.</span></span> <span data-ttu-id="e495f-106">Blok přidělené paměti zásobníku nepodléhá [uvolňování paměti](../../../standard/garbage-collection/index.md) a nemusí být připnut [ `fixed` příkazem](../keywords/fixed-statement.md).</span><span class="sxs-lookup"><span data-stu-id="e495f-106">A stack allocated memory block is not subject to [garbage collection](../../../standard/garbage-collection/index.md) and doesn't have to be pinned with a [`fixed` statement](../keywords/fixed-statement.md).</span></span>

<span data-ttu-id="e495f-107">Výsledek operátoru `stackalloc` můžete přiřadit proměnné jednoho z následujících typů:</span><span class="sxs-lookup"><span data-stu-id="e495f-107">You can assign the result of the `stackalloc` operator to a variable of one of the following types:</span></span>

- <span data-ttu-id="e495f-108">Počínaje C# <xref:System.Span%601?displayProperty=nameWithType> 7.2, <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>nebo , jak ukazuje následující příklad:</span><span class="sxs-lookup"><span data-stu-id="e495f-108">Beginning with C# 7.2, <xref:System.Span%601?displayProperty=nameWithType> or <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>, as the following example shows:</span></span>

  [!code-csharp[stackalloc span](snippets/StackallocOperator.cs#AssignToSpan)]

  <span data-ttu-id="e495f-109">Není třeba používat [nebezpečný](../keywords/unsafe.md) kontext při přiřazení bloku přidělené paměti <xref:System.Span%601> zásobníku nebo <xref:System.ReadOnlySpan%601> proměnné.</span><span class="sxs-lookup"><span data-stu-id="e495f-109">You don't have to use an [unsafe](../keywords/unsafe.md) context when you assign a stack allocated memory block to a <xref:System.Span%601> or <xref:System.ReadOnlySpan%601> variable.</span></span>

  <span data-ttu-id="e495f-110">Při práci s těmito typy `stackalloc` můžete použít výraz ve [výrazech podmíněné](conditional-operator.md) nebo přiřazení, jak ukazuje následující příklad:</span><span class="sxs-lookup"><span data-stu-id="e495f-110">When you work with those types, you can use a `stackalloc` expression in [conditional](conditional-operator.md) or assignment expressions, as the following example shows:</span></span>

  [!code-csharp[stackalloc expression](snippets/StackallocOperator.cs#AsExpression)]

  <span data-ttu-id="e495f-111">Počínaje c# 8.0, můžete `stackalloc` použít výraz uvnitř jiných <xref:System.Span%601> <xref:System.ReadOnlySpan%601> výrazů vždy, když je povolena nebo proměnná, jak ukazuje následující příklad:</span><span class="sxs-lookup"><span data-stu-id="e495f-111">Beginning with C# 8.0, you can use a `stackalloc` expression inside other expressions whenever a <xref:System.Span%601> or <xref:System.ReadOnlySpan%601> variable is allowed, as the following example shows:</span></span>

  [!code-csharp[stackalloc in nested expressions](snippets/StackallocOperator.cs#Nested)]

  > [!NOTE]
  > <span data-ttu-id="e495f-112">Doporučujeme <xref:System.Span%601> používat <xref:System.ReadOnlySpan%601> nebo typy pro práci s přidělenou pamětí zásobníku, kdykoli je to možné.</span><span class="sxs-lookup"><span data-stu-id="e495f-112">We recommend using <xref:System.Span%601> or <xref:System.ReadOnlySpan%601> types to work with stack allocated memory whenever possible.</span></span>

- <span data-ttu-id="e495f-113">[Typ ukazatele](../../programming-guide/unsafe-code-pointers/pointer-types.md), jak ukazuje následující příklad:</span><span class="sxs-lookup"><span data-stu-id="e495f-113">A [pointer type](../../programming-guide/unsafe-code-pointers/pointer-types.md), as the following example shows:</span></span>

  [!code-csharp[stackalloc pointer](snippets/StackallocOperator.cs#AssignToPointer)]

  <span data-ttu-id="e495f-114">Jak ukazuje předchozí příklad, musíte `unsafe` použít kontext při práci s typy ukazatelů.</span><span class="sxs-lookup"><span data-stu-id="e495f-114">As the preceding example shows, you must use an `unsafe` context when you work with pointer types.</span></span>

  <span data-ttu-id="e495f-115">V případě typů ukazatelů můžete použít `stackalloc` výraz pouze v deklaraci místní proměnné k inicializaci proměnné.</span><span class="sxs-lookup"><span data-stu-id="e495f-115">In the case of pointer types, you can use a `stackalloc` expression only in a local variable declaration to initialize the variable.</span></span>

<span data-ttu-id="e495f-116">Obsah nově přidělené paměti není definován.</span><span class="sxs-lookup"><span data-stu-id="e495f-116">The content of the newly allocated memory is undefined.</span></span> <span data-ttu-id="e495f-117">Počínaje C# 7.3, můžete použít syntaxi inicializátoru pole k definování obsahu nově přidělené paměti.</span><span class="sxs-lookup"><span data-stu-id="e495f-117">Beginning with C# 7.3, you can use array initializer syntax to define the content of the newly allocated memory.</span></span> <span data-ttu-id="e495f-118">Následující příklad ukazuje různé způsoby, jak to provést:</span><span class="sxs-lookup"><span data-stu-id="e495f-118">The following example demonstrates various ways to do that:</span></span>

[!code-csharp[stackalloc initialization](snippets/StackallocOperator.cs#StackallocInit)]

<span data-ttu-id="e495f-119">Ve `stackalloc T[E]`výrazu musí `T` být [nespravovaný typ](../builtin-types/unmanaged-types.md) a `E` musí být výrazem typu [int](../builtin-types/integral-numeric-types.md).</span><span class="sxs-lookup"><span data-stu-id="e495f-119">In expression `stackalloc T[E]`, `T` must be an [unmanaged type](../builtin-types/unmanaged-types.md) and `E` must be an expression of type [int](../builtin-types/integral-numeric-types.md).</span></span>

## <a name="security"></a><span data-ttu-id="e495f-120">Zabezpečení</span><span class="sxs-lookup"><span data-stu-id="e495f-120">Security</span></span>

<span data-ttu-id="e495f-121">Použití `stackalloc` automaticky umožňuje funkce detekce přetečení vyrovnávací paměti v clr (COMMON Language runtime).</span><span class="sxs-lookup"><span data-stu-id="e495f-121">The use of `stackalloc` automatically enables buffer overrun detection features in the common language runtime (CLR).</span></span> <span data-ttu-id="e495f-122">Pokud je zjištěno přetečení vyrovnávací paměti, proces je ukončen co nejrychleji minimalizovat pravděpodobnost spuštění škodlivého kódu.</span><span class="sxs-lookup"><span data-stu-id="e495f-122">If a buffer overrun is detected, the process is terminated as quickly as possible to minimize the chance that malicious code is executed.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="e495f-123">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="e495f-123">C# language specification</span></span>

<span data-ttu-id="e495f-124">Další informace naleznete v části [Přidělení zásobníku](~/_csharplang/spec/unsafe-code.md#stack-allocation) [specifikace jazyka C#](~/_csharplang/spec/introduction.md) a [povolit `stackalloc` v vnořených kontextech](~/_csharplang/proposals/csharp-8.0/nested-stackalloc.md) poznámka k návrhu funkce.</span><span class="sxs-lookup"><span data-stu-id="e495f-124">For more information, see the [Stack allocation](~/_csharplang/spec/unsafe-code.md#stack-allocation) section of the [C# language specification](~/_csharplang/spec/introduction.md) and the [Permit `stackalloc` in nested contexts](~/_csharplang/proposals/csharp-8.0/nested-stackalloc.md) feature proposal note.</span></span>

## <a name="see-also"></a><span data-ttu-id="e495f-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="e495f-125">See also</span></span>

- [<span data-ttu-id="e495f-126">Referenční dokumentace k jazyku C#</span><span class="sxs-lookup"><span data-stu-id="e495f-126">C# reference</span></span>](../index.md)
- [<span data-ttu-id="e495f-127">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="e495f-127">C# operators</span></span>](index.md)
- [<span data-ttu-id="e495f-128">Operátory související s ukazatelem</span><span class="sxs-lookup"><span data-stu-id="e495f-128">Pointer related operators</span></span>](pointer-related-operators.md)
- [<span data-ttu-id="e495f-129">Typy ukazatelů</span><span class="sxs-lookup"><span data-stu-id="e495f-129">Pointer types</span></span>](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="e495f-130">Typy související s Memory a Span</span><span class="sxs-lookup"><span data-stu-id="e495f-130">Memory and span-related types</span></span>](../../../standard/memory-and-spans/index.md)
