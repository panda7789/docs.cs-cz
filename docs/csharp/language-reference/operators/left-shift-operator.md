---
title: << operátor - C# odkaz
ms.custom: seodec18
ms.date: 02/12/2019
f1_keywords:
- <<_CSharpKeyword
helpviewer_keywords:
- left shift operator (<<) [C#]
- << operator [C#]
ms.assetid: a654eb56-1ff7-4bf3-9064-b631be0cdccc
ms.openlocfilehash: deea2d0f720ba7f096e65c67378586bc88f24673
ms.sourcegitcommit: 30e2fe5cc4165aa6dde7218ec80a13def3255e98
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/13/2019
ms.locfileid: "56219432"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="87c81-102">\<\< – Operátor (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="87c81-102">\<\< operator (C# Reference)</span></span>

<span data-ttu-id="87c81-103">Operátor posunutí doleva `<<` staffhubu svůj první operand doleva o počet bitů, které jsou určené svým druhým operandem.</span><span class="sxs-lookup"><span data-stu-id="87c81-103">The left-shift operator `<<` shifts its first operand left by the number of bits defined by its second operand.</span></span> <span data-ttu-id="87c81-104">Podporují všechny typy celých čísel `<<` operátor.</span><span class="sxs-lookup"><span data-stu-id="87c81-104">All integer types support the `<<` operator.</span></span> <span data-ttu-id="87c81-105">Však musí být typu druhého operandu [int](../keywords/int.md) nebo typ, který má [předdefinované implicitní převod čísla](../keywords/implicit-numeric-conversions-table.md) k `int`.</span><span class="sxs-lookup"><span data-stu-id="87c81-105">However, the type of the second operand must be [int](../keywords/int.md) or a type that has a [predefined implicit numeric conversion](../keywords/implicit-numeric-conversions-table.md) to `int`.</span></span>

<span data-ttu-id="87c81-106">Horní bity, které jsou mimo rozsah typu výsledku ignorovány a nižšího řádu prázdný bitové pozice jsou nastaveny na nulu, jak ukazuje následující příklad:</span><span class="sxs-lookup"><span data-stu-id="87c81-106">The high-order bits that are outside the range of the result type are discarded, and the low-order empty bit positions are set to zero, as the following example shows:</span></span>

[!code-csharp-interactive[left shift example](~/samples/snippets/csharp/language-reference/operators/ShiftOperatorsExamples.cs#LeftShift)]

## <a name="shift-count"></a><span data-ttu-id="87c81-107">Počet posunutí</span><span class="sxs-lookup"><span data-stu-id="87c81-107">Shift count</span></span>

<span data-ttu-id="87c81-108">Pro výraz `x << count`, počet skutečné posunutí závisí na typu `x` následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="87c81-108">For the expression `x << count`, the actual shift count depends on the type of `x` as follows:</span></span>

- <span data-ttu-id="87c81-109">Pokud typ `x` je [int](../keywords/int.md) nebo [uint](../keywords/uint.md), počet posunů je dán nižšího řádu *pět* bits druhého operandu.</span><span class="sxs-lookup"><span data-stu-id="87c81-109">If the type of `x` is [int](../keywords/int.md) or [uint](../keywords/uint.md), the shift count is given by the low-order *five* bits of the second operand.</span></span> <span data-ttu-id="87c81-110">To znamená, že počet posunů je vypočítán z `count & 0x1F` (nebo `count & 0b_1_1111`).</span><span class="sxs-lookup"><span data-stu-id="87c81-110">That is, the shift count is computed from `count & 0x1F` (or `count & 0b_1_1111`).</span></span>

- <span data-ttu-id="87c81-111">Pokud typ `x` je [dlouhé](../keywords/long.md) nebo [ulong](../keywords/ulong.md), počet posunů je dán nižšího řádu *šest* bits druhého operandu.</span><span class="sxs-lookup"><span data-stu-id="87c81-111">If the type of `x` is [long](../keywords/long.md) or [ulong](../keywords/ulong.md), the shift count is given by the low-order *six* bits of the second operand.</span></span> <span data-ttu-id="87c81-112">To znamená, že počet posunů je vypočítán z `count & 0x3F` (nebo `count & 0b_11_1111`).</span><span class="sxs-lookup"><span data-stu-id="87c81-112">That is, the shift count is computed from `count & 0x3F` (or `count & 0b_11_1111`).</span></span>

<span data-ttu-id="87c81-113">Následující příklad ukazuje toto chování:</span><span class="sxs-lookup"><span data-stu-id="87c81-113">The following example demonstrates that behavior:</span></span>

[!code-csharp-interactive[shift count example](~/samples/snippets/csharp/language-reference/operators/ShiftOperatorsExamples.cs#LeftShiftByLargeCount)]

## <a name="remarks"></a><span data-ttu-id="87c81-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="87c81-114">Remarks</span></span>

<span data-ttu-id="87c81-115">Operace posunutí nikdy způsobit přetečení a produkuje stejné výsledky v [zaškrtnuto a nezaškrtnuto](../keywords/checked-and-unchecked.md) kontexty.</span><span class="sxs-lookup"><span data-stu-id="87c81-115">Shift operations never cause overflows and produce the same results in [checked and unchecked](../keywords/checked-and-unchecked.md) contexts.</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="87c81-116">Overloadability – operátor</span><span class="sxs-lookup"><span data-stu-id="87c81-116">Operator overloadability</span></span>

<span data-ttu-id="87c81-117">Uživatelem definované typy lze [přetížení](../keywords/operator.md) `<<` operátor.</span><span class="sxs-lookup"><span data-stu-id="87c81-117">User-defined types can [overload](../keywords/operator.md) the `<<` operator.</span></span> <span data-ttu-id="87c81-118">Pokud uživatelský typ `T` přetížení `<<` operátoru musí být typu prvního operandu `T` a musí být typu druhého operandu `int`.</span><span class="sxs-lookup"><span data-stu-id="87c81-118">If a user-defined type `T` overloads the `<<` operator, the type of the first operand must be `T` and the type of the second operand must be `int`.</span></span> <span data-ttu-id="87c81-119">Když `<<` je operátor přetížen, [operátor přiřazení posunutí doleva](left-shift-assignment-operator.md) `<<=` je také implicitně přetížené.</span><span class="sxs-lookup"><span data-stu-id="87c81-119">When the `<<` operator is overloaded, the [left-shift assignment operator](left-shift-assignment-operator.md) `<<=` is also implicitly overloaded.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="87c81-120">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="87c81-120">C# language specification</span></span>

<span data-ttu-id="87c81-121">Další informace najdete v tématu [operátory posunutí](~/_csharplang/spec/expressions.md#shift-operators) část [ C# specifikace jazyka](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="87c81-121">For more information, see the [Shift operators](~/_csharplang/spec/expressions.md#shift-operators) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="87c81-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="87c81-122">See also</span></span>

- [<span data-ttu-id="87c81-123">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="87c81-123">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="87c81-124">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="87c81-124">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="87c81-125">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="87c81-125">C# Operators</span></span>](index.md)
- [<span data-ttu-id="87c81-126">>> – operátor</span><span class="sxs-lookup"><span data-stu-id="87c81-126">>> operator</span></span>](right-shift-operator.md)
