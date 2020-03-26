---
title: stackalloc výraz - C# odkaz
ms.date: 03/13/2020
f1_keywords:
- stackalloc_CSharpKeyword
helpviewer_keywords:
- stackalloc expression [C#]
ms.openlocfilehash: 2e99ce8b1e44dfa040c1acac799a3a55b375bd91
ms.sourcegitcommit: 34dc3c0d0d0a1cc418abff259d9daa8078d00b81
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/19/2020
ms.locfileid: "79546598"
---
# <a name="stackalloc-expression-c-reference"></a><span data-ttu-id="2fa6b-102">stackalloc výraz (C# odkaz)</span><span class="sxs-lookup"><span data-stu-id="2fa6b-102">stackalloc expression (C# reference)</span></span>

<span data-ttu-id="2fa6b-103">Výraz `stackalloc` přiděluje blok paměti v zásobníku.</span><span class="sxs-lookup"><span data-stu-id="2fa6b-103">A `stackalloc` expression allocates a block of memory on the stack.</span></span> <span data-ttu-id="2fa6b-104">Blok přidělené paměti zásobníku vytvořený během spuštění metody je automaticky zahozen, když se tato metoda vrátí.</span><span class="sxs-lookup"><span data-stu-id="2fa6b-104">A stack allocated memory block created during the method execution is automatically discarded when that method returns.</span></span> <span data-ttu-id="2fa6b-105">Paměť přidělenou aplikaci `stackalloc`.</span><span class="sxs-lookup"><span data-stu-id="2fa6b-105">You cannot explicitly free the memory allocated with `stackalloc`.</span></span> <span data-ttu-id="2fa6b-106">Blok přidělené paměti zásobníku nepodléhá [uvolňování paměti](../../../standard/garbage-collection/index.md) a nemusí být připnut [ `fixed` příkazem](../keywords/fixed-statement.md).</span><span class="sxs-lookup"><span data-stu-id="2fa6b-106">A stack allocated memory block is not subject to [garbage collection](../../../standard/garbage-collection/index.md) and doesn't have to be pinned with a [`fixed` statement](../keywords/fixed-statement.md).</span></span>

<span data-ttu-id="2fa6b-107">Výsledek výrazu `stackalloc` můžete přiřadit proměnné jednoho z následujících typů:</span><span class="sxs-lookup"><span data-stu-id="2fa6b-107">You can assign the result of a `stackalloc` expression to a variable of one of the following types:</span></span>

- <span data-ttu-id="2fa6b-108">Počínaje C# <xref:System.Span%601?displayProperty=nameWithType> 7.2, <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>nebo , jak ukazuje následující příklad:</span><span class="sxs-lookup"><span data-stu-id="2fa6b-108">Beginning with C# 7.2, <xref:System.Span%601?displayProperty=nameWithType> or <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>, as the following example shows:</span></span>

  [!code-csharp[stackalloc span](snippets/StackallocOperator.cs#AssignToSpan)]

  <span data-ttu-id="2fa6b-109">Není třeba používat [nebezpečný](../keywords/unsafe.md) kontext při přiřazení bloku přidělené paměti <xref:System.Span%601> zásobníku nebo <xref:System.ReadOnlySpan%601> proměnné.</span><span class="sxs-lookup"><span data-stu-id="2fa6b-109">You don't have to use an [unsafe](../keywords/unsafe.md) context when you assign a stack allocated memory block to a <xref:System.Span%601> or <xref:System.ReadOnlySpan%601> variable.</span></span>

  <span data-ttu-id="2fa6b-110">Při práci s těmito typy `stackalloc` můžete použít výraz ve [výrazech podmíněné](conditional-operator.md) nebo přiřazení, jak ukazuje následující příklad:</span><span class="sxs-lookup"><span data-stu-id="2fa6b-110">When you work with those types, you can use a `stackalloc` expression in [conditional](conditional-operator.md) or assignment expressions, as the following example shows:</span></span>

  [!code-csharp[stackalloc expression](snippets/StackallocOperator.cs#AsExpression)]

  <span data-ttu-id="2fa6b-111">Počínaje c# 8.0, můžete `stackalloc` použít výraz uvnitř jiných <xref:System.Span%601> <xref:System.ReadOnlySpan%601> výrazů vždy, když je povolena nebo proměnná, jak ukazuje následující příklad:</span><span class="sxs-lookup"><span data-stu-id="2fa6b-111">Beginning with C# 8.0, you can use a `stackalloc` expression inside other expressions whenever a <xref:System.Span%601> or <xref:System.ReadOnlySpan%601> variable is allowed, as the following example shows:</span></span>

  [!code-csharp[stackalloc in nested expressions](snippets/StackallocOperator.cs#Nested)]

  > [!NOTE]
  > <span data-ttu-id="2fa6b-112">Doporučujeme <xref:System.Span%601> používat <xref:System.ReadOnlySpan%601> nebo typy pro práci s přidělenou pamětí zásobníku, kdykoli je to možné.</span><span class="sxs-lookup"><span data-stu-id="2fa6b-112">We recommend using <xref:System.Span%601> or <xref:System.ReadOnlySpan%601> types to work with stack allocated memory whenever possible.</span></span>

- <span data-ttu-id="2fa6b-113">[Typ ukazatele](../../programming-guide/unsafe-code-pointers/pointer-types.md), jak ukazuje následující příklad:</span><span class="sxs-lookup"><span data-stu-id="2fa6b-113">A [pointer type](../../programming-guide/unsafe-code-pointers/pointer-types.md), as the following example shows:</span></span>

  [!code-csharp[stackalloc pointer](snippets/StackallocOperator.cs#AssignToPointer)]

  <span data-ttu-id="2fa6b-114">Jak ukazuje předchozí příklad, musíte `unsafe` použít kontext při práci s typy ukazatelů.</span><span class="sxs-lookup"><span data-stu-id="2fa6b-114">As the preceding example shows, you must use an `unsafe` context when you work with pointer types.</span></span>

  <span data-ttu-id="2fa6b-115">V případě typů ukazatelů můžete použít `stackalloc` výraz pouze v deklaraci místní proměnné k inicializaci proměnné.</span><span class="sxs-lookup"><span data-stu-id="2fa6b-115">In the case of pointer types, you can use a `stackalloc` expression only in a local variable declaration to initialize the variable.</span></span>

<span data-ttu-id="2fa6b-116">Množství paměti dostupné v zásobníku je omezené.</span><span class="sxs-lookup"><span data-stu-id="2fa6b-116">The amount of memory available on the stack is limited.</span></span> <span data-ttu-id="2fa6b-117">Pokud přidělíte příliš mnoho paměti <xref:System.StackOverflowException> v zásobníku, je vyvolána.</span><span class="sxs-lookup"><span data-stu-id="2fa6b-117">If you allocate too much memory on the stack, a <xref:System.StackOverflowException> is thrown.</span></span> <span data-ttu-id="2fa6b-118">Chcete-li tomu zabránit, postupujte podle následujících pravidel:</span><span class="sxs-lookup"><span data-stu-id="2fa6b-118">To avoid that, follow the rules below:</span></span>

- <span data-ttu-id="2fa6b-119">Omezte velikost paměti, kterou přidělujete pomocí `stackalloc`:</span><span class="sxs-lookup"><span data-stu-id="2fa6b-119">Limit the amount of memory you allocate with `stackalloc`:</span></span>

  [!code-csharp[limit stackalloc](snippets/StackallocOperator.cs#LimitStackalloc)]

  <span data-ttu-id="2fa6b-120">Vzhledem k tomu, že množství paměti, které jsou k dispozici v zásobníku závisí na prostředí, ve kterém je spuštěn kód, být konzervativní při definování skutečné mezní hodnoty.</span><span class="sxs-lookup"><span data-stu-id="2fa6b-120">Because the amount of memory available on the stack depends on the environment in which the code is executed, be conservative when you define the actual limit value.</span></span>

- <span data-ttu-id="2fa6b-121">Vyhněte se použití `stackalloc` vnitřních smyček.</span><span class="sxs-lookup"><span data-stu-id="2fa6b-121">Avoid using `stackalloc` inside loops.</span></span> <span data-ttu-id="2fa6b-122">Přidělit blok paměti mimo smyčku a znovu jej použít uvnitř smyčky.</span><span class="sxs-lookup"><span data-stu-id="2fa6b-122">Allocate the memory block outside a loop and reuse it inside the loop.</span></span>

<span data-ttu-id="2fa6b-123">Obsah nově přidělené paměti není definován.</span><span class="sxs-lookup"><span data-stu-id="2fa6b-123">The content of the newly allocated memory is undefined.</span></span> <span data-ttu-id="2fa6b-124">Před použitím byste jej měli inicializovat.</span><span class="sxs-lookup"><span data-stu-id="2fa6b-124">You should initialize it before the use.</span></span> <span data-ttu-id="2fa6b-125">Můžete například použít <xref:System.Span%601.Clear%2A?displayProperty=nameWithType> metodu, která nastaví všechny položky na výchozí hodnotu typu `T`.</span><span class="sxs-lookup"><span data-stu-id="2fa6b-125">For example, you can use the <xref:System.Span%601.Clear%2A?displayProperty=nameWithType> method that sets all the items to the default value of type `T`.</span></span>

<span data-ttu-id="2fa6b-126">Počínaje C# 7.3, můžete použít syntaxi inicializátoru pole k definování obsahu nově přidělené paměti.</span><span class="sxs-lookup"><span data-stu-id="2fa6b-126">Beginning with C# 7.3, you can use array initializer syntax to define the content of the newly allocated memory.</span></span> <span data-ttu-id="2fa6b-127">Následující příklad ukazuje různé způsoby, jak to provést:</span><span class="sxs-lookup"><span data-stu-id="2fa6b-127">The following example demonstrates various ways to do that:</span></span>

[!code-csharp[stackalloc initialization](snippets/StackallocOperator.cs#StackallocInit)]

<span data-ttu-id="2fa6b-128">Ve `stackalloc T[E]`výrazu musí `T` být [nespravovaný typ](../builtin-types/unmanaged-types.md) a `E` musí být vyhodnocen na nezápornou [hodnotu int.](../builtin-types/integral-numeric-types.md)</span><span class="sxs-lookup"><span data-stu-id="2fa6b-128">In expression `stackalloc T[E]`, `T` must be an [unmanaged type](../builtin-types/unmanaged-types.md) and `E` must evaluate to a non-negative [int](../builtin-types/integral-numeric-types.md) value.</span></span>

## <a name="security"></a><span data-ttu-id="2fa6b-129">Zabezpečení</span><span class="sxs-lookup"><span data-stu-id="2fa6b-129">Security</span></span>

<span data-ttu-id="2fa6b-130">Použití `stackalloc` automaticky umožňuje funkce detekce přetečení vyrovnávací paměti v clr (COMMON Language runtime).</span><span class="sxs-lookup"><span data-stu-id="2fa6b-130">The use of `stackalloc` automatically enables buffer overrun detection features in the common language runtime (CLR).</span></span> <span data-ttu-id="2fa6b-131">Pokud je zjištěno přetečení vyrovnávací paměti, proces je ukončen co nejrychleji minimalizovat pravděpodobnost spuštění škodlivého kódu.</span><span class="sxs-lookup"><span data-stu-id="2fa6b-131">If a buffer overrun is detected, the process is terminated as quickly as possible to minimize the chance that malicious code is executed.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="2fa6b-132">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="2fa6b-132">C# language specification</span></span>

<span data-ttu-id="2fa6b-133">Další informace naleznete v části [Přidělení zásobníku](~/_csharplang/spec/unsafe-code.md#stack-allocation) [specifikace jazyka C#](~/_csharplang/spec/introduction.md) a [povolit `stackalloc` v vnořených kontextech](~/_csharplang/proposals/csharp-8.0/nested-stackalloc.md) poznámka k návrhu funkce.</span><span class="sxs-lookup"><span data-stu-id="2fa6b-133">For more information, see the [Stack allocation](~/_csharplang/spec/unsafe-code.md#stack-allocation) section of the [C# language specification](~/_csharplang/spec/introduction.md) and the [Permit `stackalloc` in nested contexts](~/_csharplang/proposals/csharp-8.0/nested-stackalloc.md) feature proposal note.</span></span>

## <a name="see-also"></a><span data-ttu-id="2fa6b-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="2fa6b-134">See also</span></span>

- [<span data-ttu-id="2fa6b-135">Referenční dokumentace k jazyku C#</span><span class="sxs-lookup"><span data-stu-id="2fa6b-135">C# reference</span></span>](../index.md)
- [<span data-ttu-id="2fa6b-136">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="2fa6b-136">C# operators</span></span>](index.md)
- [<span data-ttu-id="2fa6b-137">Operátory související s ukazatelem</span><span class="sxs-lookup"><span data-stu-id="2fa6b-137">Pointer related operators</span></span>](pointer-related-operators.md)
- [<span data-ttu-id="2fa6b-138">Typy ukazatelů</span><span class="sxs-lookup"><span data-stu-id="2fa6b-138">Pointer types</span></span>](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="2fa6b-139">Typy související s Memory a Span</span><span class="sxs-lookup"><span data-stu-id="2fa6b-139">Memory and span-related types</span></span>](../../../standard/memory-and-spans/index.md)
- [<span data-ttu-id="2fa6b-140">Co dělat a co nedělat stackalloc</span><span class="sxs-lookup"><span data-stu-id="2fa6b-140">Dos and Don'ts of stackalloc</span></span>](https://vcsjones.dev/2020/02/24/stackalloc/)
