---
title: operátor stackalloc – C# odkaz
ms.custom: seodec18
ms.date: 06/10/2019
f1_keywords:
- stackalloc_CSharpKeyword
helpviewer_keywords:
- stackalloc operator [C#]
ms.openlocfilehash: 3be4e827e75e4e26a34d9ed70423af5aa317e7fb
ms.sourcegitcommit: 5bc85ad81d96b8dc2a90ce53bada475ee5662c44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/12/2019
ms.locfileid: "67025003"
---
# <a name="stackalloc-operator-c-reference"></a><span data-ttu-id="0cf58-102">operátor stackalloc (C# odkaz)</span><span class="sxs-lookup"><span data-stu-id="0cf58-102">stackalloc operator (C# reference)</span></span>

<span data-ttu-id="0cf58-103">`stackalloc` Operátor přiděluje blok paměti v zásobníku.</span><span class="sxs-lookup"><span data-stu-id="0cf58-103">The `stackalloc` operator allocates a block of memory on the stack.</span></span> <span data-ttu-id="0cf58-104">Zásobníku přidělený blok paměti, vytvořené během provádění metody se automaticky zruší po návratu tato metoda.</span><span class="sxs-lookup"><span data-stu-id="0cf58-104">A stack allocated memory block created during the method execution is automatically discarded when that method returns.</span></span> <span data-ttu-id="0cf58-105">Nelze explicitně uvolnit paměť alokována `stackalloc` operátor.</span><span class="sxs-lookup"><span data-stu-id="0cf58-105">You cannot explicitly free memory allocated with the `stackalloc` operator.</span></span> <span data-ttu-id="0cf58-106">Blok paměti přidělené zásobník není podléhají [uvolňování](../../../standard/garbage-collection/index.md) a nemusí být připojená s [ `fixed` příkaz](../keywords/fixed-statement.md).</span><span class="sxs-lookup"><span data-stu-id="0cf58-106">A stack allocated memory block is not subject to [garbage collection](../../../standard/garbage-collection/index.md) and doesn't have to be pinned with the [`fixed` statement](../keywords/fixed-statement.md).</span></span>

<span data-ttu-id="0cf58-107">Můžete přiřadit výsledek `stackalloc` operátor proměnné jednu z následujících typů:</span><span class="sxs-lookup"><span data-stu-id="0cf58-107">You can assign the result of the `stackalloc` operator to a variable of one of the following types:</span></span>

- <span data-ttu-id="0cf58-108">Počínaje C# 7.2, <xref:System.Span%601?displayProperty=nameWithType> nebo <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>, jak je vidět v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="0cf58-108">Starting with C# 7.2, <xref:System.Span%601?displayProperty=nameWithType> or <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>, as the following example shows:</span></span>

  [!code-csharp[stackalloc span](~/samples/csharp/language-reference/operators/StackallocOperator.cs#AssignToSpan)]

  <span data-ttu-id="0cf58-109">Není nutné používat [nebezpečné](../keywords/unsafe.md) kontextu při přiřazování zásobníku přidělený blok paměti k <xref:System.Span%601> nebo <xref:System.ReadOnlySpan%601> proměnné.</span><span class="sxs-lookup"><span data-stu-id="0cf58-109">You don't have to use an [unsafe](../keywords/unsafe.md) context when you assign a stack allocated memory block to a <xref:System.Span%601> or <xref:System.ReadOnlySpan%601> variable.</span></span>

  <span data-ttu-id="0cf58-110">Při práci s těmito typy, můžete použít `stackalloc` výrazu v [podmíněného](conditional-operator.md) nebo výrazy přiřazení, jak ukazuje následující příklad:</span><span class="sxs-lookup"><span data-stu-id="0cf58-110">When you work with those types, you can use a `stackalloc` expression in [conditional](conditional-operator.md) or assignment expressions, as the following example shows:</span></span>

  [!code-csharp[stackalloc expression](~/samples/csharp/language-reference/operators/StackallocOperator.cs#AsExpression)]

  > [!NOTE]
  > <span data-ttu-id="0cf58-111">Doporučujeme používat <xref:System.Span%601> nebo <xref:System.ReadOnlySpan%601> typy pro práci s zásobníku přidělenou paměť, kdykoli je to možné.</span><span class="sxs-lookup"><span data-stu-id="0cf58-111">We recommend using <xref:System.Span%601> or <xref:System.ReadOnlySpan%601> types to work with stack allocated memory whenever possible.</span></span>

- <span data-ttu-id="0cf58-112">A [typ ukazatele](../../programming-guide/unsafe-code-pointers/pointer-types.md), jak je vidět v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="0cf58-112">A [pointer type](../../programming-guide/unsafe-code-pointers/pointer-types.md), as the following example shows:</span></span>

  [!code-csharp[stackalloc pointer](~/samples/csharp/language-reference/operators/StackallocOperator.cs#AssignToPointer)]

  <span data-ttu-id="0cf58-113">Jak ukazuje předchozí příklad, musíte použít `unsafe` kontextu při práci s typy ukazatelů.</span><span class="sxs-lookup"><span data-stu-id="0cf58-113">As the preceding example shows, you must use an `unsafe` context when you work with pointer types.</span></span>

<span data-ttu-id="0cf58-114">Obsah nově přidělenou paměť není definován.</span><span class="sxs-lookup"><span data-stu-id="0cf58-114">The content of the newly allocated memory is undefined.</span></span> <span data-ttu-id="0cf58-115">Počínaje C# 7.3, můžete použít syntaxi inicializátoru pole definovat obsah nově přidělenou paměť.</span><span class="sxs-lookup"><span data-stu-id="0cf58-115">Starting with C# 7.3, you can use array initializer syntax to define the content of the newly allocated memory.</span></span> <span data-ttu-id="0cf58-116">Následující příklad ukazuje různé způsoby, jak to udělat:</span><span class="sxs-lookup"><span data-stu-id="0cf58-116">The following example demonstrates various ways to do that:</span></span>

[!code-csharp[stackalloc initialization](~/samples/csharp/language-reference/operators/StackallocOperator.cs#StackallocInit)]

## <a name="security"></a><span data-ttu-id="0cf58-117">Zabezpečení</span><span class="sxs-lookup"><span data-stu-id="0cf58-117">Security</span></span>

<span data-ttu-id="0cf58-118">Použití `stackalloc` automaticky povoluje funkce detekce přetečení vyrovnávací paměti v modulu common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="0cf58-118">The use of `stackalloc` automatically enables buffer overrun detection features in the common language runtime (CLR).</span></span> <span data-ttu-id="0cf58-119">Pokud se zjistí přetečení vyrovnávací paměti, co nejrychleji, chcete-li minimalizovat pravděpodobnost, že je proveden škodlivý kód ukončení procesu.</span><span class="sxs-lookup"><span data-stu-id="0cf58-119">If a buffer overrun is detected, the process is terminated as quickly as possible to minimize the chance that malicious code is executed.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="0cf58-120">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="0cf58-120">C# language specification</span></span>

<span data-ttu-id="0cf58-121">Další informace najdete v tématu [zásobníku přidělení](~/_csharplang/spec/unsafe-code.md#stack-allocation) část [ C# specifikace jazyka](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="0cf58-121">For more information, see the [Stack allocation](~/_csharplang/spec/unsafe-code.md#stack-allocation) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="0cf58-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0cf58-122">See also</span></span>

- [<span data-ttu-id="0cf58-123">C#referenční dokumentace</span><span class="sxs-lookup"><span data-stu-id="0cf58-123">C# reference</span></span>](../index.md)
- [<span data-ttu-id="0cf58-124">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="0cf58-124">C# operators</span></span>](index.md)
- [<span data-ttu-id="0cf58-125">Ukazatel související s operátory</span><span class="sxs-lookup"><span data-stu-id="0cf58-125">Pointer related operators</span></span>](pointer-related-operators.md)
- [<span data-ttu-id="0cf58-126">Typy ukazatelů</span><span class="sxs-lookup"><span data-stu-id="0cf58-126">Pointer types</span></span>](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="0cf58-127">Typy související s Memory a Span</span><span class="sxs-lookup"><span data-stu-id="0cf58-127">Memory and span-related types</span></span>](../../../standard/memory-and-spans/index.md)
