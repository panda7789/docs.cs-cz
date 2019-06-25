---
title: Operátory porovnání - C# odkaz
description: Další informace o C# operátory porovnání, které vám umožní zkontrolovat pořadí číselné hodnoty.
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
ms.openlocfilehash: 0e6edf9bcc0954bf06e76b238b2bb07dea040a9c
ms.sourcegitcommit: 127343afce8422bfa944c8b0c4ecc8f79f653255
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2019
ms.locfileid: "67347898"
---
# <a name="comparison-operators-c-reference"></a><span data-ttu-id="6e5ca-103">Operátory porovnání (C# odkaz)</span><span class="sxs-lookup"><span data-stu-id="6e5ca-103">Comparison operators (C# reference)</span></span>

<span data-ttu-id="6e5ca-104">[ `<` (Menší než)](#less-than-operator-), [ `>` (větší)](#greater-than-operator-), [ `<=` (menší než nebo rovno)](#less-than-or-equal-operator-), a [ `>=` () větší než nebo rovno)](#greater-than-or-equal-operator-) porovnání, také známé jako relační, operátory porovnání svých operandů.</span><span class="sxs-lookup"><span data-stu-id="6e5ca-104">The [`<` (less than)](#less-than-operator-), [`>` (greater than)](#greater-than-operator-), [`<=` (less than or equal)](#less-than-or-equal-operator-), and [`>=` (greater than or equal)](#greater-than-or-equal-operator-) comparison, also known as relational, operators compare their operands.</span></span> <span data-ttu-id="6e5ca-105">Tyto operátory podporují všechny [integrální](../keywords/integral-types-table.md) a [s plovoucí desetinnou čárkou](../keywords/floating-point-types-table.md) číselné typy.</span><span class="sxs-lookup"><span data-stu-id="6e5ca-105">Those operators support all [integral](../keywords/integral-types-table.md) and [floating-point](../keywords/floating-point-types-table.md) numeric types.</span></span>

> [!NOTE]
> <span data-ttu-id="6e5ca-106">Pro `==`, `<`, `>`, `<=`, a `>=` operátory, pokud žádný z operandů není číslo (<xref:System.Double.NaN?displayProperty=nameWithType> nebo <xref:System.Single.NaN?displayProperty=nameWithType>), je výsledek operace `false`.</span><span class="sxs-lookup"><span data-stu-id="6e5ca-106">For the `==`, `<`, `>`, `<=`, and `>=` operators, if any of the operands is not a number (<xref:System.Double.NaN?displayProperty=nameWithType> or <xref:System.Single.NaN?displayProperty=nameWithType>), the result of operation is `false`.</span></span> <span data-ttu-id="6e5ca-107">To znamená, že `NaN` hodnota není větší než, menší než, ani jakýkoli jiný roven `double` (nebo `float`) hodnotu, včetně `NaN`.</span><span class="sxs-lookup"><span data-stu-id="6e5ca-107">That means that the `NaN` value is neither greater than, less than, nor equal to any other `double` (or `float`) value, including `NaN`.</span></span> <span data-ttu-id="6e5ca-108">Další informace a příklady najdete v tématu <xref:System.Double.NaN?displayProperty=nameWithType> nebo <xref:System.Single.NaN?displayProperty=nameWithType> článku.</span><span class="sxs-lookup"><span data-stu-id="6e5ca-108">For more information and examples, see the <xref:System.Double.NaN?displayProperty=nameWithType> or <xref:System.Single.NaN?displayProperty=nameWithType> reference article.</span></span>

<span data-ttu-id="6e5ca-109">Výčtové typy také podporují operátory porovnání.</span><span class="sxs-lookup"><span data-stu-id="6e5ca-109">Enumeration types also support comparison operators.</span></span> <span data-ttu-id="6e5ca-110">Pro operandy stejného [výčtu](../keywords/enum.md) porovnání typu hodnoty odpovídající základní celočíselného typu.</span><span class="sxs-lookup"><span data-stu-id="6e5ca-110">For operands of the same [enum](../keywords/enum.md) type, the corresponding values of the underlying integral type are compared.</span></span>

<span data-ttu-id="6e5ca-111">[ `==` a `!=` operátory](equality-operators.md) zkontrolujte, jestli operandy jsou stejné, nebo ne.</span><span class="sxs-lookup"><span data-stu-id="6e5ca-111">The [`==` and `!=` operators](equality-operators.md) check if their operands are equal or not.</span></span>

## <a name="less-than-operator-"></a><span data-ttu-id="6e5ca-112">Operátor menší než \<</span><span class="sxs-lookup"><span data-stu-id="6e5ca-112">Less than operator \<</span></span>

<span data-ttu-id="6e5ca-113">`<` Operátor vrátí `true` pokud jeho levý operand je menší než jeho zpracovával pravý operand `false` jinak:</span><span class="sxs-lookup"><span data-stu-id="6e5ca-113">The `<` operator returns `true` if its left-hand operand is less than its right-hand operand, `false` otherwise:</span></span>

[!code-csharp-interactive[less than example](~/samples/csharp/language-reference/operators/ComparisonOperators.cs#Less)]

## <a name="greater-than-operator-"></a><span data-ttu-id="6e5ca-114">Operátor větší než ></span><span class="sxs-lookup"><span data-stu-id="6e5ca-114">Greater than operator ></span></span>

<span data-ttu-id="6e5ca-115">`>` Operátor vrátí `true` pokud jeho levý operand je větší než jeho zpracovával pravý operand `false` jinak:</span><span class="sxs-lookup"><span data-stu-id="6e5ca-115">The `>` operator returns `true` if its left-hand operand is greater than its right-hand operand, `false` otherwise:</span></span>

[!code-csharp-interactive[greater than example](~/samples/csharp/language-reference/operators/ComparisonOperators.cs#Greater)]

## <a name="less-than-or-equal-operator-"></a><span data-ttu-id="6e5ca-116">Menší než nebo rovno – operátor \<=</span><span class="sxs-lookup"><span data-stu-id="6e5ca-116">Less than or equal operator \<=</span></span>

<span data-ttu-id="6e5ca-117">`<=` Operátor vrátí `true` pokud jeho levý operand je menší nebo rovna zpracovával pravý operand, `false` jinak:</span><span class="sxs-lookup"><span data-stu-id="6e5ca-117">The `<=` operator returns `true` if its left-hand operand is less than or equal to its right-hand operand, `false` otherwise:</span></span>

[!code-csharp-interactive[less than or equal example](~/samples/csharp/language-reference/operators/ComparisonOperators.cs#LessOrEqual)]

## <a name="greater-than-or-equal-operator-"></a><span data-ttu-id="6e5ca-118">Operátor větší než nebo rovna > =</span><span class="sxs-lookup"><span data-stu-id="6e5ca-118">Greater than or equal operator >=</span></span>

<span data-ttu-id="6e5ca-119">`>=` Operátor vrátí `true` pokud jeho levý operand je větší než nebo rovna hodnotě zpracovával pravý operand, `false` jinak:</span><span class="sxs-lookup"><span data-stu-id="6e5ca-119">The `>=` operator returns `true` if its left-hand operand is greater than or equal to its right-hand operand, `false` otherwise:</span></span>

[!code-csharp-interactive[greater than or equal example](~/samples/csharp/language-reference/operators/ComparisonOperators.cs#GreaterOrEqual)]

## <a name="operator-overloadability"></a><span data-ttu-id="6e5ca-120">Overloadability – operátor</span><span class="sxs-lookup"><span data-stu-id="6e5ca-120">Operator overloadability</span></span>

<span data-ttu-id="6e5ca-121">Uživatelem definovaný typ může [přetížení](../keywords/operator.md) `<`, `>`, `<=`, a `>=` operátory.</span><span class="sxs-lookup"><span data-stu-id="6e5ca-121">A user-defined type can [overload](../keywords/operator.md) the `<`, `>`, `<=`, and `>=` operators.</span></span>

<span data-ttu-id="6e5ca-122">Pokud typ jednoho z přetížení `<` nebo `>` operátory, ho musíte přetížení obě `<` a `>`.</span><span class="sxs-lookup"><span data-stu-id="6e5ca-122">If a type overloads one of the `<` or `>` operators, it must overload both `<` and `>`.</span></span> <span data-ttu-id="6e5ca-123">Pokud typ jednoho z přetížení `<=` nebo `>=` operátory, ho musíte přetížení obě `<=` a `>=`.</span><span class="sxs-lookup"><span data-stu-id="6e5ca-123">If a type overloads one of the `<=` or `>=` operators, it must overload both `<=` and `>=`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="6e5ca-124">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="6e5ca-124">C# language specification</span></span>

<span data-ttu-id="6e5ca-125">Další informace najdete v tématu [relační a typové zkoušky operátory](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) část [ C# specifikace jazyka](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="6e5ca-125">For more information, see the [Relational and type-testing operators](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="6e5ca-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6e5ca-126">See also</span></span>

- [<span data-ttu-id="6e5ca-127">C#referenční dokumentace</span><span class="sxs-lookup"><span data-stu-id="6e5ca-127">C# reference</span></span>](../index.md)
- [<span data-ttu-id="6e5ca-128">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="6e5ca-128">C# operators</span></span>](index.md)
- <xref:System.IComparable%601?displayProperty=nameWithType>
- [<span data-ttu-id="6e5ca-129">Operátory rovnosti</span><span class="sxs-lookup"><span data-stu-id="6e5ca-129">Equality operators</span></span>](equality-operators.md)
