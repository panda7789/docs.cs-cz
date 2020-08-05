---
title: Výraz stackalloc – Referenční dokumentace jazyka C#
ms.date: 03/13/2020
f1_keywords:
- stackalloc_CSharpKeyword
helpviewer_keywords:
- stackalloc expression [C#]
ms.openlocfilehash: 32ac85f678912cb7e5f506244265b1bf57d0b4aa
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/04/2020
ms.locfileid: "87555603"
---
# <a name="stackalloc-expression-c-reference"></a><span data-ttu-id="ce67c-102">stackalloc – výraz (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="ce67c-102">stackalloc expression (C# reference)</span></span>

<span data-ttu-id="ce67c-103">`stackalloc`Výraz přiděluje blok paměti v zásobníku.</span><span class="sxs-lookup"><span data-stu-id="ce67c-103">A `stackalloc` expression allocates a block of memory on the stack.</span></span> <span data-ttu-id="ce67c-104">Blok paměti přidělený zásobníkem, který byl vytvořen během provádění metody, je automaticky zahozen při návratu této metody.</span><span class="sxs-lookup"><span data-stu-id="ce67c-104">A stack allocated memory block created during the method execution is automatically discarded when that method returns.</span></span> <span data-ttu-id="ce67c-105">Paměť přidělená pomocí nelze explicitně uvolnit `stackalloc` .</span><span class="sxs-lookup"><span data-stu-id="ce67c-105">You cannot explicitly free the memory allocated with `stackalloc`.</span></span> <span data-ttu-id="ce67c-106">Blok paměti přidělený zásobníku nepodléhá [uvolňování](../../../standard/garbage-collection/index.md) paměti a nemusí být připnutý s [ `fixed` příkazem](../keywords/fixed-statement.md).</span><span class="sxs-lookup"><span data-stu-id="ce67c-106">A stack allocated memory block is not subject to [garbage collection](../../../standard/garbage-collection/index.md) and doesn't have to be pinned with a [`fixed` statement](../keywords/fixed-statement.md).</span></span>

<span data-ttu-id="ce67c-107">Výsledek výrazu můžete přiřadit `stackalloc` proměnné jednoho z následujících typů:</span><span class="sxs-lookup"><span data-stu-id="ce67c-107">You can assign the result of a `stackalloc` expression to a variable of one of the following types:</span></span>

- <span data-ttu-id="ce67c-108">Počínaje jazykem C# 7,2 <xref:System.Span%601?displayProperty=nameWithType> nebo <xref:System.ReadOnlySpan%601?displayProperty=nameWithType> , jak ukazuje následující příklad:</span><span class="sxs-lookup"><span data-stu-id="ce67c-108">Beginning with C# 7.2, <xref:System.Span%601?displayProperty=nameWithType> or <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>, as the following example shows:</span></span>

  [!code-csharp[stackalloc span](snippets/StackallocOperator.cs#AssignToSpan)]

  <span data-ttu-id="ce67c-109">Nemusíte používat [nezabezpečený](../keywords/unsafe.md) kontext, když přiřadíte blok paměti přidělené zásobníku <xref:System.Span%601> k <xref:System.ReadOnlySpan%601> proměnné nebo.</span><span class="sxs-lookup"><span data-stu-id="ce67c-109">You don't have to use an [unsafe](../keywords/unsafe.md) context when you assign a stack allocated memory block to a <xref:System.Span%601> or <xref:System.ReadOnlySpan%601> variable.</span></span>

  <span data-ttu-id="ce67c-110">Při práci s těmito typy můžete použít `stackalloc` výraz ve výrazech [podmíněného](conditional-operator.md) nebo přiřazení, jak ukazuje následující příklad:</span><span class="sxs-lookup"><span data-stu-id="ce67c-110">When you work with those types, you can use a `stackalloc` expression in [conditional](conditional-operator.md) or assignment expressions, as the following example shows:</span></span>

  [!code-csharp[stackalloc expression](snippets/StackallocOperator.cs#AsExpression)]

  <span data-ttu-id="ce67c-111">Počínaje jazykem C# 8,0 můžete použít `stackalloc` výraz uvnitř jiných výrazů vždy <xref:System.Span%601> <xref:System.ReadOnlySpan%601> , když je povolena proměnná nebo, jak je uvedeno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="ce67c-111">Beginning with C# 8.0, you can use a `stackalloc` expression inside other expressions whenever a <xref:System.Span%601> or <xref:System.ReadOnlySpan%601> variable is allowed, as the following example shows:</span></span>

  [!code-csharp[stackalloc in nested expressions](snippets/StackallocOperator.cs#Nested)]

  > [!NOTE]
  > <span data-ttu-id="ce67c-112"><xref:System.Span%601> <xref:System.ReadOnlySpan%601> Pokud je to možné, doporučujeme používat typy nebo pro práci s přidělenou pamětí zásobníku.</span><span class="sxs-lookup"><span data-stu-id="ce67c-112">We recommend using <xref:System.Span%601> or <xref:System.ReadOnlySpan%601> types to work with stack allocated memory whenever possible.</span></span>

- <span data-ttu-id="ce67c-113">[Typ ukazatele](../../programming-guide/unsafe-code-pointers/pointer-types.md), jak ukazuje následující příklad:</span><span class="sxs-lookup"><span data-stu-id="ce67c-113">A [pointer type](../../programming-guide/unsafe-code-pointers/pointer-types.md), as the following example shows:</span></span>

  [!code-csharp[stackalloc pointer](snippets/StackallocOperator.cs#AssignToPointer)]

  <span data-ttu-id="ce67c-114">Jak ukazuje předchozí příklad, je nutné použít `unsafe` kontext při práci s typy ukazatelů.</span><span class="sxs-lookup"><span data-stu-id="ce67c-114">As the preceding example shows, you must use an `unsafe` context when you work with pointer types.</span></span>

  <span data-ttu-id="ce67c-115">V případě typů ukazatelů můžete použít `stackalloc` výraz pouze v deklaraci lokální proměnné pro inicializaci proměnné.</span><span class="sxs-lookup"><span data-stu-id="ce67c-115">In the case of pointer types, you can use a `stackalloc` expression only in a local variable declaration to initialize the variable.</span></span>

<span data-ttu-id="ce67c-116">Velikost paměti, která je k dispozici v zásobníku, je omezená.</span><span class="sxs-lookup"><span data-stu-id="ce67c-116">The amount of memory available on the stack is limited.</span></span> <span data-ttu-id="ce67c-117">Pokud přidělíte příliš mnoho paměti v zásobníku, <xref:System.StackOverflowException> je vyvolána.</span><span class="sxs-lookup"><span data-stu-id="ce67c-117">If you allocate too much memory on the stack, a <xref:System.StackOverflowException> is thrown.</span></span> <span data-ttu-id="ce67c-118">Abyste tomu předešli, postupujte podle následujících pravidel:</span><span class="sxs-lookup"><span data-stu-id="ce67c-118">To avoid that, follow the rules below:</span></span>

- <span data-ttu-id="ce67c-119">Omezte velikost paměti, kterou přidělíte `stackalloc` :</span><span class="sxs-lookup"><span data-stu-id="ce67c-119">Limit the amount of memory you allocate with `stackalloc`:</span></span>

  [!code-csharp[limit stackalloc](snippets/StackallocOperator.cs#LimitStackalloc)]

  <span data-ttu-id="ce67c-120">Vzhledem k tomu, že množství paměti dostupné v zásobníku závisí na prostředí, ve kterém je kód spuštěný, je při definování skutečné mezní hodnoty konzervativní.</span><span class="sxs-lookup"><span data-stu-id="ce67c-120">Because the amount of memory available on the stack depends on the environment in which the code is executed, be conservative when you define the actual limit value.</span></span>

- <span data-ttu-id="ce67c-121">Nepoužívejte `stackalloc` uvnitř smyček smyčky.</span><span class="sxs-lookup"><span data-stu-id="ce67c-121">Avoid using `stackalloc` inside loops.</span></span> <span data-ttu-id="ce67c-122">Přidělte blok paměti mimo smyčku a znovu ho použijte uvnitř smyčky.</span><span class="sxs-lookup"><span data-stu-id="ce67c-122">Allocate the memory block outside a loop and reuse it inside the loop.</span></span>

<span data-ttu-id="ce67c-123">Obsah nově přidělené paměti není definován.</span><span class="sxs-lookup"><span data-stu-id="ce67c-123">The content of the newly allocated memory is undefined.</span></span> <span data-ttu-id="ce67c-124">Měli byste ji inicializovat před použitím.</span><span class="sxs-lookup"><span data-stu-id="ce67c-124">You should initialize it before the use.</span></span> <span data-ttu-id="ce67c-125">Například můžete použít <xref:System.Span%601.Clear%2A?displayProperty=nameWithType> metodu, která nastaví všechny položky na výchozí hodnotu typu `T` .</span><span class="sxs-lookup"><span data-stu-id="ce67c-125">For example, you can use the <xref:System.Span%601.Clear%2A?displayProperty=nameWithType> method that sets all the items to the default value of type `T`.</span></span>

<span data-ttu-id="ce67c-126">Počínaje jazykem C# 7,3 můžete použít syntaxi inicializátoru pole k definování obsahu nově přidělené paměti.</span><span class="sxs-lookup"><span data-stu-id="ce67c-126">Beginning with C# 7.3, you can use array initializer syntax to define the content of the newly allocated memory.</span></span> <span data-ttu-id="ce67c-127">Následující příklad ukazuje různé způsoby, jak to provést:</span><span class="sxs-lookup"><span data-stu-id="ce67c-127">The following example demonstrates various ways to do that:</span></span>

[!code-csharp[stackalloc initialization](snippets/StackallocOperator.cs#StackallocInit)]

<span data-ttu-id="ce67c-128">Ve výrazu `stackalloc T[E]` `T` musí být [nespravovaný typ](../builtin-types/unmanaged-types.md) a `E` musí se vyhodnotit jako nezáporná hodnota typu [int](../builtin-types/integral-numeric-types.md) .</span><span class="sxs-lookup"><span data-stu-id="ce67c-128">In expression `stackalloc T[E]`, `T` must be an [unmanaged type](../builtin-types/unmanaged-types.md) and `E` must evaluate to a non-negative [int](../builtin-types/integral-numeric-types.md) value.</span></span>

## <a name="security"></a><span data-ttu-id="ce67c-129">Zabezpečení</span><span class="sxs-lookup"><span data-stu-id="ce67c-129">Security</span></span>

<span data-ttu-id="ce67c-130">`stackalloc`V modulu CLR (Common Language Runtime) se použití funkce automaticky zapne k detekci přetečení vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="ce67c-130">The use of `stackalloc` automatically enables buffer overrun detection features in the common language runtime (CLR).</span></span> <span data-ttu-id="ce67c-131">Pokud se zjistí přetečení vyrovnávací paměti, proces se ukončí co nejrychleji, aby se minimalizovala pravděpodobnost spuštění škodlivého kódu.</span><span class="sxs-lookup"><span data-stu-id="ce67c-131">If a buffer overrun is detected, the process is terminated as quickly as possible to minimize the chance that malicious code is executed.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="ce67c-132">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="ce67c-132">C# language specification</span></span>

<span data-ttu-id="ce67c-133">Další informace naleznete v části [alokace zásobníku](~/_csharplang/spec/unsafe-code.md#stack-allocation) v tématu [specifikace jazyka C#](~/_csharplang/spec/introduction.md) a poznámky k návrhu [funkce `stackalloc` vnořené kontexty](~/_csharplang/proposals/csharp-8.0/nested-stackalloc.md) .</span><span class="sxs-lookup"><span data-stu-id="ce67c-133">For more information, see the [Stack allocation](~/_csharplang/spec/unsafe-code.md#stack-allocation) section of the [C# language specification](~/_csharplang/spec/introduction.md) and the [Permit `stackalloc` in nested contexts](~/_csharplang/proposals/csharp-8.0/nested-stackalloc.md) feature proposal note.</span></span>

## <a name="see-also"></a><span data-ttu-id="ce67c-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="ce67c-134">See also</span></span>

- [<span data-ttu-id="ce67c-135">Referenční dokumentace k jazyku C#</span><span class="sxs-lookup"><span data-stu-id="ce67c-135">C# reference</span></span>](../index.md)
- [<span data-ttu-id="ce67c-136">Operátory a výrazy v C#</span><span class="sxs-lookup"><span data-stu-id="ce67c-136">C# operators and expressions</span></span>](index.md)
- [<span data-ttu-id="ce67c-137">Operátory související s ukazatelem</span><span class="sxs-lookup"><span data-stu-id="ce67c-137">Pointer related operators</span></span>](pointer-related-operators.md)
- [<span data-ttu-id="ce67c-138">Typy ukazatelů</span><span class="sxs-lookup"><span data-stu-id="ce67c-138">Pointer types</span></span>](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="ce67c-139">Typy související s Memory a Span</span><span class="sxs-lookup"><span data-stu-id="ce67c-139">Memory and span-related types</span></span>](../../../standard/memory-and-spans/index.md)
- [<span data-ttu-id="ce67c-140">DOS a Don'ts z stackalloc</span><span class="sxs-lookup"><span data-stu-id="ce67c-140">Dos and Don'ts of stackalloc</span></span>](https://vcsjones.dev/2020/02/24/stackalloc/)
