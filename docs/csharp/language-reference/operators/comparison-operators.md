---
title: Operátory porovnání – reference jazyka C#
description: Přečtěte si o relačních operátorech C#, které můžete použít ke kontrole pořadí číselných hodnot.
ms.date: 05/11/2020
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
ms.openlocfilehash: eda039d950e4be13d9c041c8bb95b6ea773b83f6
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83207231"
---
# <a name="comparison-operators-c-reference"></a><span data-ttu-id="70965-103">Operátory porovnání (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="70965-103">Comparison operators (C# reference)</span></span>

<span data-ttu-id="70965-104">Porovnání [ `<` (menší než)](#less-than-operator-), [ `>` (je větší než)](#greater-than-operator-), (je menší než [ `<=` nebo rovno)](#less-than-or-equal-operator-)a [ `>=` (větší než nebo rovno](#greater-than-or-equal-operator-) ), známé také jako relační, operátory porovnávají své operandy.</span><span class="sxs-lookup"><span data-stu-id="70965-104">The [`<` (less than)](#less-than-operator-), [`>` (greater than)](#greater-than-operator-), [`<=` (less than or equal)](#less-than-or-equal-operator-), and [`>=` (greater than or equal)](#greater-than-or-equal-operator-) comparison, also known as relational, operators compare their operands.</span></span> <span data-ttu-id="70965-105">Tyto operátory jsou podporovány všemi [celočíselnými](../builtin-types/integral-numeric-types.md) typy a čísly [s plovoucí desetinnou](../builtin-types/floating-point-numeric-types.md) čárkou.</span><span class="sxs-lookup"><span data-stu-id="70965-105">Those operators are supported by all [integral](../builtin-types/integral-numeric-types.md) and [floating-point](../builtin-types/floating-point-numeric-types.md) numeric types.</span></span>

> [!NOTE]
> <span data-ttu-id="70965-106">Pro `==` operátory, `<` , `>` , `<=` a `>=` , pokud některý z operandů není číslo ( <xref:System.Double.NaN?displayProperty=nameWithType> nebo <xref:System.Single.NaN?displayProperty=nameWithType> ), výsledek operace je `false` .</span><span class="sxs-lookup"><span data-stu-id="70965-106">For the `==`, `<`, `>`, `<=`, and `>=` operators, if any of the operands is not a number (<xref:System.Double.NaN?displayProperty=nameWithType> or <xref:System.Single.NaN?displayProperty=nameWithType>), the result of operation is `false`.</span></span> <span data-ttu-id="70965-107">To znamená, že `NaN` hodnota není větší než, menší nebo rovna žádné jiné `double` hodnotě (nebo `float` ), včetně `NaN` .</span><span class="sxs-lookup"><span data-stu-id="70965-107">That means that the `NaN` value is neither greater than, less than, nor equal to any other `double` (or `float`) value, including `NaN`.</span></span> <span data-ttu-id="70965-108">Další informace a příklady naleznete v tématu <xref:System.Double.NaN?displayProperty=nameWithType> nebo v <xref:System.Single.NaN?displayProperty=nameWithType> referenčním článku.</span><span class="sxs-lookup"><span data-stu-id="70965-108">For more information and examples, see the <xref:System.Double.NaN?displayProperty=nameWithType> or <xref:System.Single.NaN?displayProperty=nameWithType> reference article.</span></span>

<span data-ttu-id="70965-109">Typ [znaku](../builtin-types/char.md) také podporuje operátory porovnání.</span><span class="sxs-lookup"><span data-stu-id="70965-109">The [char](../builtin-types/char.md) type also supports comparison operators.</span></span> <span data-ttu-id="70965-110">V případě `char` operandů jsou porovnány odpovídající kódy znaků.</span><span class="sxs-lookup"><span data-stu-id="70965-110">In the case of `char` operands, the corresponding character codes are compared.</span></span>

<span data-ttu-id="70965-111">Výčtové typy také podporují operátory porovnání.</span><span class="sxs-lookup"><span data-stu-id="70965-111">Enumeration types also support comparison operators.</span></span> <span data-ttu-id="70965-112">Pro operandy stejného typu [výčtu](../builtin-types/enum.md) jsou porovnány odpovídající hodnoty základního integrálního typu.</span><span class="sxs-lookup"><span data-stu-id="70965-112">For operands of the same [enum](../builtin-types/enum.md) type, the corresponding values of the underlying integral type are compared.</span></span>

<span data-ttu-id="70965-113">[ `==` `!=` Operátory a](equality-operators.md) zkontrolují, zda jsou jejich operandy stejné.</span><span class="sxs-lookup"><span data-stu-id="70965-113">The [`==` and `!=` operators](equality-operators.md) check if their operands are equal or not.</span></span>

## <a name="less-than-operator-"></a><span data-ttu-id="70965-114">Operátor menší než\<</span><span class="sxs-lookup"><span data-stu-id="70965-114">Less than operator \<</span></span>

<span data-ttu-id="70965-115">`<`Operátor vrátí, `true` Pokud je jeho levý operand menší než jeho pravý operand, `false` jinak:</span><span class="sxs-lookup"><span data-stu-id="70965-115">The `<` operator returns `true` if its left-hand operand is less than its right-hand operand, `false` otherwise:</span></span>

[!code-csharp-interactive[less than example](snippets/ComparisonOperators.cs#Less)]

## <a name="greater-than-operator-"></a><span data-ttu-id="70965-116">> operátoru větší než</span><span class="sxs-lookup"><span data-stu-id="70965-116">Greater than operator ></span></span>

<span data-ttu-id="70965-117">`>`Operátor vrátí, `true` Pokud je jeho levý operand větší než jeho pravý operand, `false` jinak:</span><span class="sxs-lookup"><span data-stu-id="70965-117">The `>` operator returns `true` if its left-hand operand is greater than its right-hand operand, `false` otherwise:</span></span>

[!code-csharp-interactive[greater than example](snippets/ComparisonOperators.cs#Greater)]

## <a name="less-than-or-equal-operator-"></a><span data-ttu-id="70965-118">Operátor menší než nebo rovno\<=</span><span class="sxs-lookup"><span data-stu-id="70965-118">Less than or equal operator \<=</span></span>

<span data-ttu-id="70965-119">`<=`Operátor vrátí `true` , pokud je jeho levý operand menší nebo roven jeho pravému operandu, `false` jinak:</span><span class="sxs-lookup"><span data-stu-id="70965-119">The `<=` operator returns `true` if its left-hand operand is less than or equal to its right-hand operand, `false` otherwise:</span></span>

[!code-csharp-interactive[less than or equal example](snippets/ComparisonOperators.cs#LessOrEqual)]

## <a name="greater-than-or-equal-operator-"></a><span data-ttu-id="70965-120">Operátor větší než nebo rovno >=</span><span class="sxs-lookup"><span data-stu-id="70965-120">Greater than or equal operator >=</span></span>

<span data-ttu-id="70965-121">`>=`Operátor vrátí `true` , pokud je jeho levý operand větší než nebo roven jeho pravému operandu, `false` jinak:</span><span class="sxs-lookup"><span data-stu-id="70965-121">The `>=` operator returns `true` if its left-hand operand is greater than or equal to its right-hand operand, `false` otherwise:</span></span>

[!code-csharp-interactive[greater than or equal example](snippets/ComparisonOperators.cs#GreaterOrEqual)]

## <a name="operator-overloadability"></a><span data-ttu-id="70965-122">Přetížení operátoru</span><span class="sxs-lookup"><span data-stu-id="70965-122">Operator overloadability</span></span>

<span data-ttu-id="70965-123">Uživatelsky definovaný typ může [přetížit](operator-overloading.md) `<` `>` operátory,, a `<=` `>=` .</span><span class="sxs-lookup"><span data-stu-id="70965-123">A user-defined type can [overload](operator-overloading.md) the `<`, `>`, `<=`, and `>=` operators.</span></span>

<span data-ttu-id="70965-124">Pokud typ přetěžuje jeden z `<` `>` operátorů nebo, musí přetížit jak `<` a `>` .</span><span class="sxs-lookup"><span data-stu-id="70965-124">If a type overloads one of the `<` or `>` operators, it must overload both `<` and `>`.</span></span> <span data-ttu-id="70965-125">Pokud typ přetěžuje jeden z `<=` `>=` operátorů nebo, musí přetížit jak `<=` a `>=` .</span><span class="sxs-lookup"><span data-stu-id="70965-125">If a type overloads one of the `<=` or `>=` operators, it must overload both `<=` and `>=`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="70965-126">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="70965-126">C# language specification</span></span>

<span data-ttu-id="70965-127">Další informace naleznete v části [relační operátory and type-Testing](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) v tématu [specifikace jazyka C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="70965-127">For more information, see the [Relational and type-testing operators](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="70965-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="70965-128">See also</span></span>

- [<span data-ttu-id="70965-129">Referenční dokumentace k jazyku C#</span><span class="sxs-lookup"><span data-stu-id="70965-129">C# reference</span></span>](../index.md)
- [<span data-ttu-id="70965-130">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="70965-130">C# operators</span></span>](index.md)
- <xref:System.IComparable%601?displayProperty=nameWithType>
- [<span data-ttu-id="70965-131">Operátory rovnosti</span><span class="sxs-lookup"><span data-stu-id="70965-131">Equality operators</span></span>](equality-operators.md)
