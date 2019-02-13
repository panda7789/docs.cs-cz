---
title: '>> Operator - C# odkaz'
ms.custom: seodec18
ms.date: 02/12/2019
f1_keywords:
- '>>_CSharpKeyword'
helpviewer_keywords:
- '>> operator [C#]'
- right shift operator (>>) [C#]
ms.assetid: a07f8679-d318-4ef8-b38b-65903efb8056
ms.openlocfilehash: 809cd2cab29d3378892ea224cf846e9d0909b073
ms.sourcegitcommit: 30e2fe5cc4165aa6dde7218ec80a13def3255e98
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/13/2019
ms.locfileid: "56219721"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="dbec5-102">>> – operátor (C# odkaz)</span><span class="sxs-lookup"><span data-stu-id="dbec5-102">>> operator (C# Reference)</span></span>

<span data-ttu-id="dbec5-103">Operátor pravého posunutí `>>` posune jeho prvního operandu vpravo počet bitů, které jsou určené svým druhým operandem.</span><span class="sxs-lookup"><span data-stu-id="dbec5-103">The right-shift operator `>>` shifts its first operand right by the number of bits defined by its second operand.</span></span> <span data-ttu-id="dbec5-104">Podporují všechny typy celých čísel `>>` operátor.</span><span class="sxs-lookup"><span data-stu-id="dbec5-104">All integer types support the `>>` operator.</span></span> <span data-ttu-id="dbec5-105">Však musí být typu druhého operandu [int](../keywords/int.md) nebo typ, který má [předdefinované implicitní převod čísla](../keywords/implicit-numeric-conversions-table.md) k `int`.</span><span class="sxs-lookup"><span data-stu-id="dbec5-105">However, the type of the second operand must be [int](../keywords/int.md) or a type that has a [predefined implicit numeric conversion](../keywords/implicit-numeric-conversions-table.md) to `int`.</span></span>

<span data-ttu-id="dbec5-106">Operace pravého posunutí zahodí bity nižšího řádu.</span><span class="sxs-lookup"><span data-stu-id="dbec5-106">The right-shift operation discards the low-order bits.</span></span> <span data-ttu-id="dbec5-107">Nejvyšším prázdný bitové pozice jsou nastaveny na základě typu prvního operandu následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="dbec5-107">The high-order empty bit positions are set based on the type of the first operand as follows:</span></span>

- <span data-ttu-id="dbec5-108">Pokud je první operand je typu [int](../keywords/int.md) nebo [dlouhé](../keywords/long.md), operátor pravého posunutí provádí **aritmetické** shift: hodnota nejvýznamnější bit (bit znaménka) prvního operand je postoupena do nejvyšším prázdný bitové pozice.</span><span class="sxs-lookup"><span data-stu-id="dbec5-108">If the first operand is of type [int](../keywords/int.md) or [long](../keywords/long.md), the right-shift operator performs an **arithmetic** shift: the value of the most significant bit (the sign bit) of the first operand is propagated to the high-order empty bit positions.</span></span> <span data-ttu-id="dbec5-109">To znamená, implikovaný prázdný bitové pozice nastavení na hodnotu nula, pokud je první operand je nastaven na nezáporné a nastavit na jednu, pokud je záporné.</span><span class="sxs-lookup"><span data-stu-id="dbec5-109">That is, the high-order empty bit positions are set to zero if the first operand is non-negative and set to one if it's negative.</span></span>

- <span data-ttu-id="dbec5-110">Pokud je první operand je typu [uint](../keywords/uint.md) nebo [ulong](../keywords/ulong.md), operátor pravého posunutí provádí **logické** shift: nejvyšším prázdný bitové pozice jsou vždy nastaveny na hodnotu nula.</span><span class="sxs-lookup"><span data-stu-id="dbec5-110">If the first operand is of type [uint](../keywords/uint.md) or [ulong](../keywords/ulong.md), the right-shift operator performs a **logical** shift: the high-order empty bit positions are always set to zero.</span></span>

<span data-ttu-id="dbec5-111">Následující příklad ukazuje toto chování:</span><span class="sxs-lookup"><span data-stu-id="dbec5-111">The following example demonstrates that behavior:</span></span>

[!code-csharp-interactive[right shift example](~/samples/snippets/csharp/language-reference/operators/ShiftOperatorsExamples.cs#RightShift)]

## <a name="shift-count"></a><span data-ttu-id="dbec5-112">Počet posunutí</span><span class="sxs-lookup"><span data-stu-id="dbec5-112">Shift count</span></span>

<span data-ttu-id="dbec5-113">Pro výraz `x >> count`, počet skutečné posunutí závisí na typu `x` následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="dbec5-113">For the expression `x >> count`, the actual shift count depends on the type of `x` as follows:</span></span>

- <span data-ttu-id="dbec5-114">Pokud typ `x` je [int](../keywords/int.md) nebo [uint](../keywords/uint.md), počet posunů je dán nižšího řádu *pět* bits druhého operandu.</span><span class="sxs-lookup"><span data-stu-id="dbec5-114">If the type of `x` is [int](../keywords/int.md) or [uint](../keywords/uint.md), the shift count is given by the low-order *five* bits of the second operand.</span></span> <span data-ttu-id="dbec5-115">To znamená, že počet posunů je vypočítán z `count & 0x1F` (nebo `count & 0b_1_1111`).</span><span class="sxs-lookup"><span data-stu-id="dbec5-115">That is, the shift count is computed from `count & 0x1F` (or `count & 0b_1_1111`).</span></span>

- <span data-ttu-id="dbec5-116">Pokud typ `x` je [dlouhé](../keywords/long.md) nebo [ulong](../keywords/ulong.md), počet posunů je dán nižšího řádu *šest* bits druhého operandu.</span><span class="sxs-lookup"><span data-stu-id="dbec5-116">If the type of `x` is [long](../keywords/long.md) or [ulong](../keywords/ulong.md), the shift count is given by the low-order *six* bits of the second operand.</span></span> <span data-ttu-id="dbec5-117">To znamená, že počet posunů je vypočítán z `count & 0x3F` (nebo `count & 0b_11_1111`).</span><span class="sxs-lookup"><span data-stu-id="dbec5-117">That is, the shift count is computed from `count & 0x3F` (or `count & 0b_11_1111`).</span></span>

<span data-ttu-id="dbec5-118">Následující příklad ukazuje toto chování:</span><span class="sxs-lookup"><span data-stu-id="dbec5-118">The following example demonstrates that behavior:</span></span>

[!code-csharp-interactive[shift count example](~/samples/snippets/csharp/language-reference/operators/ShiftOperatorsExamples.cs#RightShiftByLargeCount)]

## <a name="remarks"></a><span data-ttu-id="dbec5-119">Poznámky</span><span class="sxs-lookup"><span data-stu-id="dbec5-119">Remarks</span></span>

<span data-ttu-id="dbec5-120">Operace posunutí nikdy způsobit přetečení a produkuje stejné výsledky v [zaškrtnuto a nezaškrtnuto](../keywords/checked-and-unchecked.md) kontexty.</span><span class="sxs-lookup"><span data-stu-id="dbec5-120">Shift operations never cause overflows and produce the same results in [checked and unchecked](../keywords/checked-and-unchecked.md) contexts.</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="dbec5-121">Overloadability – operátor</span><span class="sxs-lookup"><span data-stu-id="dbec5-121">Operator overloadability</span></span>

<span data-ttu-id="dbec5-122">Uživatelem definované typy lze [přetížení](../keywords/operator.md) `>>` operátor.</span><span class="sxs-lookup"><span data-stu-id="dbec5-122">User-defined types can [overload](../keywords/operator.md) the `>>` operator.</span></span> <span data-ttu-id="dbec5-123">Pokud uživatelský typ `T` přetížení `>>` operátoru musí být typu prvního operandu `T` a musí být typu druhého operandu `int`.</span><span class="sxs-lookup"><span data-stu-id="dbec5-123">If a user-defined type `T` overloads the `>>` operator, the type of the first operand must be `T` and the type of the second operand must be `int`.</span></span> <span data-ttu-id="dbec5-124">Když `>>` je operátor přetížen, [operátor přiřazení posunutí doprava](right-shift-assignment-operator.md) `>>=` je také implicitně přetížené.</span><span class="sxs-lookup"><span data-stu-id="dbec5-124">When the `>>` operator is overloaded, the [right-shift assignment operator](right-shift-assignment-operator.md) `>>=` is also implicitly overloaded.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="dbec5-125">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="dbec5-125">C# language specification</span></span>

<span data-ttu-id="dbec5-126">Další informace najdete v tématu [operátory posunutí](~/_csharplang/spec/expressions.md#shift-operators) část [ C# specifikace jazyka](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="dbec5-126">For more information, see the [Shift operators](~/_csharplang/spec/expressions.md#shift-operators) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="dbec5-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="dbec5-127">See also</span></span>

- [<span data-ttu-id="dbec5-128">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="dbec5-128">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="dbec5-129">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="dbec5-129">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="dbec5-130">C#operátory</span><span class="sxs-lookup"><span data-stu-id="dbec5-130">C# operators</span></span>](index.md)
- [<span data-ttu-id="dbec5-131"><< – operátor</span><span class="sxs-lookup"><span data-stu-id="dbec5-131"><< operator</span></span>](left-shift-operator.md)