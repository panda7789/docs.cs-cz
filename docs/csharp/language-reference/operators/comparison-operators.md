---
title: Operátory porovnání – C# referenční informace
description: Přečtěte C# si o relačních operátorech, které můžete použít ke kontrole pořadí číselných hodnot.
ms.date: 04/25/2019
author: pkulikov
f1_keywords:
- <_CSharpKeyword
- '>_CSharpKeyword'
- <=_CSharpKeyword
- '>=_CSharpKeyword'
helpviewer_keywords:
- comparison operators [C#]
- relational operators [C#]
- less than operator [C#]
- < operator [C#]
- greater than operator [C#]
- '> operator [C#]'
- less than or equal to operator [C#]
- <= operator [C#]
- greater than or equal to operator [C#]
- '>= operator [C#]'
ms.openlocfilehash: bb28e2adba896ae85b189858283376fbe3250dce
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/29/2019
ms.locfileid: "73039069"
---
# <a name="comparison-operators-c-reference"></a><span data-ttu-id="b2d9b-103">Operátory porovnání (C# referenční)</span><span class="sxs-lookup"><span data-stu-id="b2d9b-103">Comparison operators (C# reference)</span></span>

<span data-ttu-id="b2d9b-104">[`<` (menší než)](#less-than-operator-), [`>` (je větší než)](#greater-than-operator-), [`<=` (menší nebo rovno)](#less-than-or-equal-operator-)a [`>=` (větší než nebo rovno](#greater-than-or-equal-operator-) ), které se označují také jako relační, operátory porovnávají jejich operandy.</span><span class="sxs-lookup"><span data-stu-id="b2d9b-104">The [`<` (less than)](#less-than-operator-), [`>` (greater than)](#greater-than-operator-), [`<=` (less than or equal)](#less-than-or-equal-operator-), and [`>=` (greater than or equal)](#greater-than-or-equal-operator-) comparison, also known as relational, operators compare their operands.</span></span> <span data-ttu-id="b2d9b-105">Tyto operátory jsou podporovány všemi [celočíselnými](../builtin-types/integral-numeric-types.md) typy a čísly [s plovoucí desetinnou](../builtin-types/floating-point-numeric-types.md) čárkou.</span><span class="sxs-lookup"><span data-stu-id="b2d9b-105">Those operators are supported by all [integral](../builtin-types/integral-numeric-types.md) and [floating-point](../builtin-types/floating-point-numeric-types.md) numeric types.</span></span>

> [!NOTE]
> <span data-ttu-id="b2d9b-106">Pro operátory `==`, `<`, `>`, `<=`a `>=`, pokud některý z operandů není číslo (<xref:System.Double.NaN?displayProperty=nameWithType> nebo <xref:System.Single.NaN?displayProperty=nameWithType>), je výsledek operace `false`.</span><span class="sxs-lookup"><span data-stu-id="b2d9b-106">For the `==`, `<`, `>`, `<=`, and `>=` operators, if any of the operands is not a number (<xref:System.Double.NaN?displayProperty=nameWithType> or <xref:System.Single.NaN?displayProperty=nameWithType>), the result of operation is `false`.</span></span> <span data-ttu-id="b2d9b-107">To znamená, že hodnota `NaN` není větší než, menší nebo rovna žádné jiné hodnotě `double` (nebo `float`), včetně `NaN`.</span><span class="sxs-lookup"><span data-stu-id="b2d9b-107">That means that the `NaN` value is neither greater than, less than, nor equal to any other `double` (or `float`) value, including `NaN`.</span></span> <span data-ttu-id="b2d9b-108">Další informace a příklady najdete v článku referenční článek o <xref:System.Double.NaN?displayProperty=nameWithType> nebo <xref:System.Single.NaN?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b2d9b-108">For more information and examples, see the <xref:System.Double.NaN?displayProperty=nameWithType> or <xref:System.Single.NaN?displayProperty=nameWithType> reference article.</span></span>

<span data-ttu-id="b2d9b-109">Výčtové typy také podporují operátory porovnání.</span><span class="sxs-lookup"><span data-stu-id="b2d9b-109">Enumeration types also support comparison operators.</span></span> <span data-ttu-id="b2d9b-110">Pro operandy stejného typu [výčtu](../keywords/enum.md) jsou porovnány odpovídající hodnoty základního integrálního typu.</span><span class="sxs-lookup"><span data-stu-id="b2d9b-110">For operands of the same [enum](../keywords/enum.md) type, the corresponding values of the underlying integral type are compared.</span></span>

<span data-ttu-id="b2d9b-111">[Operátory`==` a `!=`](equality-operators.md) kontrolují, jestli jsou jejich operandy stejné.</span><span class="sxs-lookup"><span data-stu-id="b2d9b-111">The [`==` and `!=` operators](equality-operators.md) check if their operands are equal or not.</span></span>

## <a name="less-than-operator-"></a><span data-ttu-id="b2d9b-112">Operátor menší než \<</span><span class="sxs-lookup"><span data-stu-id="b2d9b-112">Less than operator \<</span></span>

<span data-ttu-id="b2d9b-113">Operátor `<` vrátí `true`, pokud je jeho levý operand menší než jeho pravý operand, `false` jinak:</span><span class="sxs-lookup"><span data-stu-id="b2d9b-113">The `<` operator returns `true` if its left-hand operand is less than its right-hand operand, `false` otherwise:</span></span>

[!code-csharp-interactive[less than example](~/samples/csharp/language-reference/operators/ComparisonOperators.cs#Less)]

## <a name="greater-than-operator-"></a><span data-ttu-id="b2d9b-114">> Operátoru větší než</span><span class="sxs-lookup"><span data-stu-id="b2d9b-114">Greater than operator ></span></span>

<span data-ttu-id="b2d9b-115">Operátor `>` vrátí `true`, pokud je jeho levý operand větší než jeho pravý operand, `false` jinak:</span><span class="sxs-lookup"><span data-stu-id="b2d9b-115">The `>` operator returns `true` if its left-hand operand is greater than its right-hand operand, `false` otherwise:</span></span>

[!code-csharp-interactive[greater than example](~/samples/csharp/language-reference/operators/ComparisonOperators.cs#Greater)]

## <a name="less-than-or-equal-operator-"></a><span data-ttu-id="b2d9b-116">\<= operátoru menší než nebo rovno</span><span class="sxs-lookup"><span data-stu-id="b2d9b-116">Less than or equal operator \<=</span></span>

<span data-ttu-id="b2d9b-117">Operátor `<=` vrátí `true`, pokud je jeho levý operand menší nebo roven jeho pravému operandu, `false` jinak:</span><span class="sxs-lookup"><span data-stu-id="b2d9b-117">The `<=` operator returns `true` if its left-hand operand is less than or equal to its right-hand operand, `false` otherwise:</span></span>

[!code-csharp-interactive[less than or equal example](~/samples/csharp/language-reference/operators/ComparisonOperators.cs#LessOrEqual)]

## <a name="greater-than-or-equal-operator-"></a><span data-ttu-id="b2d9b-118">Operátor větší než nebo rovno > =</span><span class="sxs-lookup"><span data-stu-id="b2d9b-118">Greater than or equal operator >=</span></span>

<span data-ttu-id="b2d9b-119">Operátor `>=` vrátí `true`, pokud je jeho levý operand větší nebo roven jeho pravému operandu, `false` jinak:</span><span class="sxs-lookup"><span data-stu-id="b2d9b-119">The `>=` operator returns `true` if its left-hand operand is greater than or equal to its right-hand operand, `false` otherwise:</span></span>

[!code-csharp-interactive[greater than or equal example](~/samples/csharp/language-reference/operators/ComparisonOperators.cs#GreaterOrEqual)]

## <a name="operator-overloadability"></a><span data-ttu-id="b2d9b-120">Přetížení operátoru</span><span class="sxs-lookup"><span data-stu-id="b2d9b-120">Operator overloadability</span></span>

<span data-ttu-id="b2d9b-121">Uživatelsky definovaný typ může [přetížit](operator-overloading.md) operátory `<`, `>`, `<=`a `>=`.</span><span class="sxs-lookup"><span data-stu-id="b2d9b-121">A user-defined type can [overload](operator-overloading.md) the `<`, `>`, `<=`, and `>=` operators.</span></span>

<span data-ttu-id="b2d9b-122">Pokud typ přetěžuje jednu z `<` nebo `>` operátory, musí přetížit jak `<`, tak `>`.</span><span class="sxs-lookup"><span data-stu-id="b2d9b-122">If a type overloads one of the `<` or `>` operators, it must overload both `<` and `>`.</span></span> <span data-ttu-id="b2d9b-123">Pokud typ přetěžuje jednu z `<=` nebo `>=` operátory, musí přetížit jak `<=`, tak `>=`.</span><span class="sxs-lookup"><span data-stu-id="b2d9b-123">If a type overloads one of the `<=` or `>=` operators, it must overload both `<=` and `>=`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="b2d9b-124">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="b2d9b-124">C# language specification</span></span>

<span data-ttu-id="b2d9b-125">Další informace naleznete v části [relační operátory and type-Testing](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) v [ C# tématu Specifikace jazyka](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="b2d9b-125">For more information, see the [Relational and type-testing operators](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="b2d9b-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b2d9b-126">See also</span></span>

- [<span data-ttu-id="b2d9b-127">C#odkaz</span><span class="sxs-lookup"><span data-stu-id="b2d9b-127">C# reference</span></span>](../index.md)
- [<span data-ttu-id="b2d9b-128">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="b2d9b-128">C# operators</span></span>](index.md)
- <xref:System.IComparable%601?displayProperty=nameWithType>
- [<span data-ttu-id="b2d9b-129">Operátory rovnosti</span><span class="sxs-lookup"><span data-stu-id="b2d9b-129">Equality operators</span></span>](equality-operators.md)
