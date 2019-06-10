---
title: Operátory rovnosti - C# odkaz
description: Další informace o C# operátory porovnání rovnosti.
ms.date: 03/28/2019
author: pkulikov
f1_keywords:
- ==_CSharpKeyword
- '!=_CSharpKeyword'
helpviewer_keywords:
- comparison operators [C#]
- relational operators [C#]
- equality operator [C#]
- equals operator [C#]
- == operator [C#]
- inequality operator [C#]
- not equals operator [C#]
- '!= operator [C#]'
ms.openlocfilehash: 3b2aeceae8371f0728da2bcebbbe597ee135f256
ms.sourcegitcommit: 904b98d8d706f0e2d5ceaa00ce17ffbd92adfb88
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/07/2019
ms.locfileid: "66758261"
---
# <a name="equality-operators-c-reference"></a><span data-ttu-id="09b48-103">Operátory rovnosti (C# odkaz)</span><span class="sxs-lookup"><span data-stu-id="09b48-103">Equality operators (C# Reference)</span></span>

<span data-ttu-id="09b48-104">[ `==` (Rovnost)](#equality-operator-) a [ `!=` (nerovnost)](#inequality-operator-) operátory zkontrolujte, jestli operandy jsou stejné, nebo ne.</span><span class="sxs-lookup"><span data-stu-id="09b48-104">The [`==` (equality)](#equality-operator-) and [`!=` (inequality)](#inequality-operator-) operators check if their operands are equal or not.</span></span>

## <a name="equality-operator-"></a><span data-ttu-id="09b48-105">Operátor rovnosti ==</span><span class="sxs-lookup"><span data-stu-id="09b48-105">Equality operator ==</span></span>

<span data-ttu-id="09b48-106">Operátor rovnosti `==` vrátí `true` pokud jeho operandy jsou si rovny, `false` jinak.</span><span class="sxs-lookup"><span data-stu-id="09b48-106">The equality operator `==` returns `true` if its operands are equal, `false` otherwise.</span></span>

### <a name="value-types-equality"></a><span data-ttu-id="09b48-107">Rovnost pro typy hodnot</span><span class="sxs-lookup"><span data-stu-id="09b48-107">Value types equality</span></span>

<span data-ttu-id="09b48-108">Operandy [integrované hodnotách](../keywords/value-types-table.md) jsou si rovny, pokud jsou si rovny jejich hodnoty:</span><span class="sxs-lookup"><span data-stu-id="09b48-108">Operands of the [built-in value types](../keywords/value-types-table.md) are equal if their values are equal:</span></span>

[!code-csharp-interactive[value types equality](~/samples/csharp/language-reference/operators/EqualityOperators.cs#ValueTypesEquality)]

> [!NOTE]
> <span data-ttu-id="09b48-109">Pro `==`, [ `<`, `>`, `<=`, a `>=` ](comparison-operators.md) operátory, pokud žádný z operandů není číslo (<xref:System.Double.NaN?displayProperty=nameWithType> nebo <xref:System.Single.NaN?displayProperty=nameWithType>), výsledkem operace je `false`.</span><span class="sxs-lookup"><span data-stu-id="09b48-109">For the `==`, [`<`, `>`, `<=`, and `>=`](comparison-operators.md) operators, if any of the operands is not a number (<xref:System.Double.NaN?displayProperty=nameWithType> or <xref:System.Single.NaN?displayProperty=nameWithType>), the result of operation is `false`.</span></span> <span data-ttu-id="09b48-110">To znamená, že `NaN` hodnota není větší než, menší než, ani jakýkoli jiný roven `double` (nebo `float`) hodnotu, včetně `NaN`.</span><span class="sxs-lookup"><span data-stu-id="09b48-110">That means that the `NaN` value is neither greater than, less than, nor equal to any other `double` (or `float`) value, including `NaN`.</span></span> <span data-ttu-id="09b48-111">Další informace a příklady najdete v tématu <xref:System.Double.NaN?displayProperty=nameWithType> nebo <xref:System.Single.NaN?displayProperty=nameWithType> článku.</span><span class="sxs-lookup"><span data-stu-id="09b48-111">For more information and examples, see the <xref:System.Double.NaN?displayProperty=nameWithType> or <xref:System.Single.NaN?displayProperty=nameWithType> reference article.</span></span>

<span data-ttu-id="09b48-112">Dva operandy stejného [výčtu](../keywords/enum.md) typu jsou si rovny, pokud jsou si rovny odpovídající hodnoty základní celočíselného typu.</span><span class="sxs-lookup"><span data-stu-id="09b48-112">Two operands of the same [enum](../keywords/enum.md) type are equal if the corresponding values of the underlying integral type are equal.</span></span>

<span data-ttu-id="09b48-113">Uživatelem definované [struktura](../keywords/struct.md) typy se nepodporují `==` operátor ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="09b48-113">User-defined [struct](../keywords/struct.md) types don't support the `==` operator by default.</span></span> <span data-ttu-id="09b48-114">Pro podporu `==` operátor struktury definované uživatelem musí [přetížení](#operator-overloadability) ho.</span><span class="sxs-lookup"><span data-stu-id="09b48-114">To support the `==` operator, a user-defined struct must [overload](#operator-overloadability) it.</span></span>

<span data-ttu-id="09b48-115">Počínaje C# 7.3, `==` a `!=` operátory jsou podporovány C# [řazených kolekcí členů](../../tuples.md).</span><span class="sxs-lookup"><span data-stu-id="09b48-115">Beginning with C# 7.3, the `==` and `!=` operators are supported by C# [tuples](../../tuples.md).</span></span> <span data-ttu-id="09b48-116">Další informace najdete v tématu [rovnosti a n-tice](../../tuples.md#equality-and-tuples) část [ C# typy řazené kolekce členů](../../tuples.md) článku.</span><span class="sxs-lookup"><span data-stu-id="09b48-116">For more information, see the [Equality and tuples](../../tuples.md#equality-and-tuples) section of the [C# tuple types](../../tuples.md) article.</span></span>

### <a name="string-equality"></a><span data-ttu-id="09b48-117">Rovnosti řetězce</span><span class="sxs-lookup"><span data-stu-id="09b48-117">String equality</span></span>

<span data-ttu-id="09b48-118">Dvě [řetězec](../keywords/string.md) operandy jsou stejné, pokud jsou obě z nich `null` nebo obě instance řetězce se stejnou délkou a mají stejné znaky v každé pozici znaku:</span><span class="sxs-lookup"><span data-stu-id="09b48-118">Two [string](../keywords/string.md) operands are equal when both of them are `null` or both string instances are of the same length and have identical characters in each character position:</span></span>

[!code-csharp-interactive[string equality](~/samples/csharp/language-reference/operators/EqualityOperators.cs#StringEquality)]

<span data-ttu-id="09b48-119">Je to velká a malá písmena ordinálního porovnání.</span><span class="sxs-lookup"><span data-stu-id="09b48-119">That is case-sensitive ordinal comparison.</span></span> <span data-ttu-id="09b48-120">Další informace o porovnávání řetězců naleznete v tématu [porovnávání řetězců v C# ](../../how-to/compare-strings.md).</span><span class="sxs-lookup"><span data-stu-id="09b48-120">For more information about string comparison, see [How to compare strings in C#](../../how-to/compare-strings.md).</span></span>

### <a name="reference-types-equality"></a><span data-ttu-id="09b48-121">Referenční rovnost typy</span><span class="sxs-lookup"><span data-stu-id="09b48-121">Reference types equality</span></span>

<span data-ttu-id="09b48-122">Dvě jiných než `string` operandy typu odkaz jsou stejné, až si do stejného objektu:</span><span class="sxs-lookup"><span data-stu-id="09b48-122">Two other than `string` reference type operands are equal when they refer to the same object:</span></span>

[!code-csharp-interactive[reference type equality](~/samples/csharp/language-reference/operators/EqualityOperators.cs#ReferenceTypesEquality)]

<span data-ttu-id="09b48-123">Jak ukazuje příklad, uživatelem definované referenční typy podporu `==` operátor ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="09b48-123">As the example shows, user-defined reference types support the `==` operator by default.</span></span> <span data-ttu-id="09b48-124">Však můžete přetížit typ definovaný uživatelem odkazu `==` operátor.</span><span class="sxs-lookup"><span data-stu-id="09b48-124">However, a user-defined reference type can overload the `==` operator.</span></span> <span data-ttu-id="09b48-125">Pokud typ odkazu přetížení `==` operátoru, použijte <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> metodu ke kontrole, pokud dva odkazy tohoto typu odkazují na stejný objekt.</span><span class="sxs-lookup"><span data-stu-id="09b48-125">If a reference type overloads the `==` operator, use the <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> method to check if two references of that type refer to the same object.</span></span>

## <a name="inequality-operator-"></a><span data-ttu-id="09b48-126">Operátor nerovnosti! =</span><span class="sxs-lookup"><span data-stu-id="09b48-126">Inequality operator !=</span></span>

<span data-ttu-id="09b48-127">Operátor nerovnosti `!=` vrátí `true` Pokud nejsou stejné, jeho operandy `false` jinak.</span><span class="sxs-lookup"><span data-stu-id="09b48-127">The inequality operator `!=` returns `true` if its operands are not equal, `false` otherwise.</span></span> <span data-ttu-id="09b48-128">Pro operandy [předdefinovaných typů](../keywords/built-in-types-table.md), výraz `x != y` vytváří stejný výsledek jako výraz `!(x == y)`.</span><span class="sxs-lookup"><span data-stu-id="09b48-128">For the operands of the [built-in types](../keywords/built-in-types-table.md), the expression `x != y` produces the same result as the expression `!(x == y)`.</span></span> <span data-ttu-id="09b48-129">Další informace o typu rovnosti, najdete v článku [operátor rovnosti](#equality-operator-) oddílu.</span><span class="sxs-lookup"><span data-stu-id="09b48-129">For more information about type equality, see the [Equality operator](#equality-operator-) section.</span></span>

<span data-ttu-id="09b48-130">Následující příklad ukazuje použití `!=` operátor:</span><span class="sxs-lookup"><span data-stu-id="09b48-130">The following example demonstrates the usage of the `!=` operator:</span></span>

[!code-csharp-interactive[non-equality examples](~/samples/csharp/language-reference/operators/EqualityOperators.cs#NonEquality)]

## <a name="operator-overloadability"></a><span data-ttu-id="09b48-131">Overloadability – operátor</span><span class="sxs-lookup"><span data-stu-id="09b48-131">Operator overloadability</span></span>

<span data-ttu-id="09b48-132">Uživatelem definovaný typ může [přetížení](../keywords/operator.md) `==` a `!=` operátory.</span><span class="sxs-lookup"><span data-stu-id="09b48-132">A user-defined type can [overload](../keywords/operator.md) the `==` and `!=` operators.</span></span> <span data-ttu-id="09b48-133">Pokud typ přetížení mezi dva operátory, musíte také přetížit jiný.</span><span class="sxs-lookup"><span data-stu-id="09b48-133">If a type overloads one of the two operators, it must also overload another one.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="09b48-134">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="09b48-134">C# language specification</span></span>

<span data-ttu-id="09b48-135">Další informace najdete v tématu [relační a typové zkoušky operátory](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) část [ C# specifikace jazyka](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="09b48-135">For more information, see the [Relational and type-testing operators](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="09b48-136">Viz také:</span><span class="sxs-lookup"><span data-stu-id="09b48-136">See also</span></span>

- [<span data-ttu-id="09b48-137">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="09b48-137">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="09b48-138">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="09b48-138">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="09b48-139">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="09b48-139">C# Operators</span></span>](index.md)
- <xref:System.IEquatable%601?displayProperty=nameWithType>
- <xref:System.Object.Equals%2A?displayProperty=nameWithType>
- <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType>
- [<span data-ttu-id="09b48-140">Porovnání rovnosti</span><span class="sxs-lookup"><span data-stu-id="09b48-140">Equality comparisons</span></span>](../../programming-guide/statements-expressions-operators/equality-comparisons.md)
- [<span data-ttu-id="09b48-141">Operátory porovnání</span><span class="sxs-lookup"><span data-stu-id="09b48-141">Comparison operators</span></span>](comparison-operators.md)
