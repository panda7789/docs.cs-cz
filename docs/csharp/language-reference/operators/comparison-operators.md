---
title: Operátory porovnání – odkaz jazyka C#
description: Další informace o operátory porovnání Jazyka C#, které můžete použít ke kontrole pořadí číselných hodnot.
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
ms.openlocfilehash: 68502205193a1fc8ab7410053e13274560ffffb0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399243"
---
# <a name="comparison-operators-c-reference"></a><span data-ttu-id="55e9f-103">Operátory porovnání (odkaz C#</span><span class="sxs-lookup"><span data-stu-id="55e9f-103">Comparison operators (C# reference)</span></span>

<span data-ttu-id="55e9f-104">[ `<` Porovnání (menší než)](#less-than-operator-), [ `>` (větší než)](#greater-than-operator-) [ `<=` , (menší než nebo stejné)](#less-than-or-equal-operator-)a [ `>=` (větší než nebo stejné)](#greater-than-or-equal-operator-) porovnání, označované také jako relační, operátory porovnávají jejich operandy.</span><span class="sxs-lookup"><span data-stu-id="55e9f-104">The [`<` (less than)](#less-than-operator-), [`>` (greater than)](#greater-than-operator-), [`<=` (less than or equal)](#less-than-or-equal-operator-), and [`>=` (greater than or equal)](#greater-than-or-equal-operator-) comparison, also known as relational, operators compare their operands.</span></span> <span data-ttu-id="55e9f-105">Tyto operátory jsou podporovány všechny [integrální](../builtin-types/integral-numeric-types.md) a [plovoucí desetinnou desetinnou desetinnou desetinnou](../builtin-types/floating-point-numeric-types.md) desetinnou hodnotu číselné typy.</span><span class="sxs-lookup"><span data-stu-id="55e9f-105">Those operators are supported by all [integral](../builtin-types/integral-numeric-types.md) and [floating-point](../builtin-types/floating-point-numeric-types.md) numeric types.</span></span>

> [!NOTE]
> <span data-ttu-id="55e9f-106">Pro `==`, `<` `>`, `<=`, `>=` , , a operátory, pokud některý<xref:System.Double.NaN?displayProperty=nameWithType> <xref:System.Single.NaN?displayProperty=nameWithType>z operandů `false`není číslo ( nebo ), výsledek operace je .</span><span class="sxs-lookup"><span data-stu-id="55e9f-106">For the `==`, `<`, `>`, `<=`, and `>=` operators, if any of the operands is not a number (<xref:System.Double.NaN?displayProperty=nameWithType> or <xref:System.Single.NaN?displayProperty=nameWithType>), the result of operation is `false`.</span></span> <span data-ttu-id="55e9f-107">To znamená, `NaN` že hodnota není větší než, menší než, `float`ani rovna `NaN`žádné jiné `double` (nebo ) hodnotu, včetně .</span><span class="sxs-lookup"><span data-stu-id="55e9f-107">That means that the `NaN` value is neither greater than, less than, nor equal to any other `double` (or `float`) value, including `NaN`.</span></span> <span data-ttu-id="55e9f-108">Další informace a příklady <xref:System.Double.NaN?displayProperty=nameWithType> naleznete <xref:System.Single.NaN?displayProperty=nameWithType> v článku nebo odkazu.</span><span class="sxs-lookup"><span data-stu-id="55e9f-108">For more information and examples, see the <xref:System.Double.NaN?displayProperty=nameWithType> or <xref:System.Single.NaN?displayProperty=nameWithType> reference article.</span></span>

<span data-ttu-id="55e9f-109">Typy výčtu také podporují operátory porovnání.</span><span class="sxs-lookup"><span data-stu-id="55e9f-109">Enumeration types also support comparison operators.</span></span> <span data-ttu-id="55e9f-110">Pro operandy stejného typu [výčtu](../builtin-types/enum.md) jsou porovnány odpovídající hodnoty základního integrálního typu.</span><span class="sxs-lookup"><span data-stu-id="55e9f-110">For operands of the same [enum](../builtin-types/enum.md) type, the corresponding values of the underlying integral type are compared.</span></span>

<span data-ttu-id="55e9f-111">[ `==` A `!=` operátoři](equality-operators.md) kontrolují, zda jsou jejich operandy stejné nebo ne.</span><span class="sxs-lookup"><span data-stu-id="55e9f-111">The [`==` and `!=` operators](equality-operators.md) check if their operands are equal or not.</span></span>

## <a name="less-than-operator-"></a><span data-ttu-id="55e9f-112">Menší než operátor\<</span><span class="sxs-lookup"><span data-stu-id="55e9f-112">Less than operator \<</span></span>

<span data-ttu-id="55e9f-113">Operátor `<` se `true` vrátí, je-li jeho levostranný operand `false` menší než jeho pravostranný operand, jinak:</span><span class="sxs-lookup"><span data-stu-id="55e9f-113">The `<` operator returns `true` if its left-hand operand is less than its right-hand operand, `false` otherwise:</span></span>

[!code-csharp-interactive[less than example](snippets/ComparisonOperators.cs#Less)]

## <a name="greater-than-operator-"></a><span data-ttu-id="55e9f-114">Větší než > operátora</span><span class="sxs-lookup"><span data-stu-id="55e9f-114">Greater than operator ></span></span>

<span data-ttu-id="55e9f-115">Operátor `>` se `true` vrátí, je-li jeho levostranný operand `false` větší než jeho pravostranný operand, jinak:</span><span class="sxs-lookup"><span data-stu-id="55e9f-115">The `>` operator returns `true` if its left-hand operand is greater than its right-hand operand, `false` otherwise:</span></span>

[!code-csharp-interactive[greater than example](snippets/ComparisonOperators.cs#Greater)]

## <a name="less-than-or-equal-operator-"></a><span data-ttu-id="55e9f-116">Operátor menší nebo stejný\<=</span><span class="sxs-lookup"><span data-stu-id="55e9f-116">Less than or equal operator \<=</span></span>

<span data-ttu-id="55e9f-117">Operátor `<=` vrátí, `true` pokud jeho levostranný operand je menší nebo `false` roven jeho pravé operandu, jinak:</span><span class="sxs-lookup"><span data-stu-id="55e9f-117">The `<=` operator returns `true` if its left-hand operand is less than or equal to its right-hand operand, `false` otherwise:</span></span>

[!code-csharp-interactive[less than or equal example](snippets/ComparisonOperators.cs#LessOrEqual)]

## <a name="greater-than-or-equal-operator-"></a><span data-ttu-id="55e9f-118">Větší než nebo rovno operátor >=</span><span class="sxs-lookup"><span data-stu-id="55e9f-118">Greater than or equal operator >=</span></span>

<span data-ttu-id="55e9f-119">Operátor `>=` vrátí, `true` pokud jeho levé operandu větší nebo rovno jeho `false` pravé operand, jinak:</span><span class="sxs-lookup"><span data-stu-id="55e9f-119">The `>=` operator returns `true` if its left-hand operand is greater than or equal to its right-hand operand, `false` otherwise:</span></span>

[!code-csharp-interactive[greater than or equal example](snippets/ComparisonOperators.cs#GreaterOrEqual)]

## <a name="operator-overloadability"></a><span data-ttu-id="55e9f-120">Přetížení obsluhy</span><span class="sxs-lookup"><span data-stu-id="55e9f-120">Operator overloadability</span></span>

<span data-ttu-id="55e9f-121">Uživatelem definovaný typ může `<` `>` `<=` [přetížit](operator-overloading.md) , , , a `>=` operátory.</span><span class="sxs-lookup"><span data-stu-id="55e9f-121">A user-defined type can [overload](operator-overloading.md) the `<`, `>`, `<=`, and `>=` operators.</span></span>

<span data-ttu-id="55e9f-122">Pokud typ přetíží `<` jeden `>` z operátorů `<` nebo, musí přetížit oba a `>`.</span><span class="sxs-lookup"><span data-stu-id="55e9f-122">If a type overloads one of the `<` or `>` operators, it must overload both `<` and `>`.</span></span> <span data-ttu-id="55e9f-123">Pokud typ přetíží `<=` jeden `>=` z operátorů `<=` nebo, musí přetížit oba a `>=`.</span><span class="sxs-lookup"><span data-stu-id="55e9f-123">If a type overloads one of the `<=` or `>=` operators, it must overload both `<=` and `>=`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="55e9f-124">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="55e9f-124">C# language specification</span></span>

<span data-ttu-id="55e9f-125">Další informace naleznete v části [Relační a typové testovací operátory](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) [specifikace jazyka C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="55e9f-125">For more information, see the [Relational and type-testing operators](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="55e9f-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="55e9f-126">See also</span></span>

- [<span data-ttu-id="55e9f-127">Referenční dokumentace k jazyku C#</span><span class="sxs-lookup"><span data-stu-id="55e9f-127">C# reference</span></span>](../index.md)
- [<span data-ttu-id="55e9f-128">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="55e9f-128">C# operators</span></span>](index.md)
- <xref:System.IComparable%601?displayProperty=nameWithType>
- [<span data-ttu-id="55e9f-129">Operátory rovnosti</span><span class="sxs-lookup"><span data-stu-id="55e9f-129">Equality operators</span></span>](equality-operators.md)
