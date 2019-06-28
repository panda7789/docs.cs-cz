---
title: Operátory rovnosti - C# odkaz
description: Další informace o C# operátory porovnání rovnosti a C# zadejte rovnosti.
ms.date: 06/26/2019
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
ms.openlocfilehash: 72e790dc008857a48602c92c9236588c531b64f9
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/28/2019
ms.locfileid: "67423930"
---
# <a name="equality-operators-c-reference"></a><span data-ttu-id="c3839-103">Operátory rovnosti (C# odkaz)</span><span class="sxs-lookup"><span data-stu-id="c3839-103">Equality operators (C# reference)</span></span>

<span data-ttu-id="c3839-104">[ `==` (Rovnost)](#equality-operator-) a [ `!=` (nerovnost)](#inequality-operator-) operátory zkontrolujte, jestli operandy jsou stejné, nebo ne.</span><span class="sxs-lookup"><span data-stu-id="c3839-104">The [`==` (equality)](#equality-operator-) and [`!=` (inequality)](#inequality-operator-) operators check if their operands are equal or not.</span></span>

## <a name="equality-operator-"></a><span data-ttu-id="c3839-105">Operátor rovnosti ==</span><span class="sxs-lookup"><span data-stu-id="c3839-105">Equality operator ==</span></span>

<span data-ttu-id="c3839-106">Operátor rovnosti `==` vrátí `true` pokud jeho operandy jsou si rovny, `false` jinak.</span><span class="sxs-lookup"><span data-stu-id="c3839-106">The equality operator `==` returns `true` if its operands are equal, `false` otherwise.</span></span>

### <a name="value-types-equality"></a><span data-ttu-id="c3839-107">Rovnost pro typy hodnot</span><span class="sxs-lookup"><span data-stu-id="c3839-107">Value types equality</span></span>

<span data-ttu-id="c3839-108">Operandy [integrované hodnotách](../keywords/value-types-table.md) jsou si rovny, pokud jsou si rovny jejich hodnoty:</span><span class="sxs-lookup"><span data-stu-id="c3839-108">Operands of the [built-in value types](../keywords/value-types-table.md) are equal if their values are equal:</span></span>

[!code-csharp-interactive[value types equality](~/samples/csharp/language-reference/operators/EqualityOperators.cs#ValueTypesEquality)]

> [!NOTE]
> <span data-ttu-id="c3839-109">Pro `==`, [ `<`, `>`, `<=`, a `>=` ](comparison-operators.md) operátory, pokud žádný z operandů není číslo (<xref:System.Double.NaN?displayProperty=nameWithType> nebo <xref:System.Single.NaN?displayProperty=nameWithType>), výsledkem operace je `false`.</span><span class="sxs-lookup"><span data-stu-id="c3839-109">For the `==`, [`<`, `>`, `<=`, and `>=`](comparison-operators.md) operators, if any of the operands is not a number (<xref:System.Double.NaN?displayProperty=nameWithType> or <xref:System.Single.NaN?displayProperty=nameWithType>), the result of operation is `false`.</span></span> <span data-ttu-id="c3839-110">To znamená, že `NaN` hodnota není větší než, menší než, ani jakýkoli jiný roven `double` (nebo `float`) hodnotu, včetně `NaN`.</span><span class="sxs-lookup"><span data-stu-id="c3839-110">That means that the `NaN` value is neither greater than, less than, nor equal to any other `double` (or `float`) value, including `NaN`.</span></span> <span data-ttu-id="c3839-111">Další informace a příklady najdete v tématu <xref:System.Double.NaN?displayProperty=nameWithType> nebo <xref:System.Single.NaN?displayProperty=nameWithType> článku.</span><span class="sxs-lookup"><span data-stu-id="c3839-111">For more information and examples, see the <xref:System.Double.NaN?displayProperty=nameWithType> or <xref:System.Single.NaN?displayProperty=nameWithType> reference article.</span></span>

<span data-ttu-id="c3839-112">Dva operandy stejného [výčtu](../keywords/enum.md) typu jsou si rovny, pokud jsou si rovny odpovídající hodnoty základní celočíselného typu.</span><span class="sxs-lookup"><span data-stu-id="c3839-112">Two operands of the same [enum](../keywords/enum.md) type are equal if the corresponding values of the underlying integral type are equal.</span></span>

<span data-ttu-id="c3839-113">Uživatelem definované [struktura](../keywords/struct.md) typy se nepodporují `==` operátor ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="c3839-113">User-defined [struct](../keywords/struct.md) types don't support the `==` operator by default.</span></span> <span data-ttu-id="c3839-114">Pro podporu `==` operátor struktury definované uživatelem musí [přetížení](#operator-overloadability) ho.</span><span class="sxs-lookup"><span data-stu-id="c3839-114">To support the `==` operator, a user-defined struct must [overload](#operator-overloadability) it.</span></span>

<span data-ttu-id="c3839-115">Počínaje C# 7.3, `==` a `!=` operátory jsou podporovány C# [řazených kolekcí členů](../../tuples.md).</span><span class="sxs-lookup"><span data-stu-id="c3839-115">Beginning with C# 7.3, the `==` and `!=` operators are supported by C# [tuples](../../tuples.md).</span></span> <span data-ttu-id="c3839-116">Další informace najdete v tématu [rovnosti a n-tice](../../tuples.md#equality-and-tuples) část [ C# typy řazené kolekce členů](../../tuples.md) článku.</span><span class="sxs-lookup"><span data-stu-id="c3839-116">For more information, see the [Equality and tuples](../../tuples.md#equality-and-tuples) section of the [C# tuple types](../../tuples.md) article.</span></span>

### <a name="string-equality"></a><span data-ttu-id="c3839-117">Rovnosti řetězce</span><span class="sxs-lookup"><span data-stu-id="c3839-117">String equality</span></span>

<span data-ttu-id="c3839-118">Dvě [řetězec](../keywords/string.md) operandy jsou stejné, pokud jsou obě z nich `null` nebo obě instance řetězce se stejnou délkou a mají stejné znaky v každé pozici znaku:</span><span class="sxs-lookup"><span data-stu-id="c3839-118">Two [string](../keywords/string.md) operands are equal when both of them are `null` or both string instances are of the same length and have identical characters in each character position:</span></span>

[!code-csharp-interactive[string equality](~/samples/csharp/language-reference/operators/EqualityOperators.cs#StringEquality)]

<span data-ttu-id="c3839-119">Je to velká a malá písmena ordinálního porovnání.</span><span class="sxs-lookup"><span data-stu-id="c3839-119">That is case-sensitive ordinal comparison.</span></span> <span data-ttu-id="c3839-120">Další informace o porovnávání řetězců naleznete v tématu [porovnávání řetězců v C# ](../../how-to/compare-strings.md).</span><span class="sxs-lookup"><span data-stu-id="c3839-120">For more information about string comparison, see [How to compare strings in C#](../../how-to/compare-strings.md).</span></span>

### <a name="reference-types-equality"></a><span data-ttu-id="c3839-121">Referenční rovnost typy</span><span class="sxs-lookup"><span data-stu-id="c3839-121">Reference types equality</span></span>

<span data-ttu-id="c3839-122">Dvě jiných než `string` operandy typu odkaz jsou stejné, až si do stejného objektu:</span><span class="sxs-lookup"><span data-stu-id="c3839-122">Two other than `string` reference type operands are equal when they refer to the same object:</span></span>

[!code-csharp[reference type equality](~/samples/csharp/language-reference/operators/EqualityOperators.cs#ReferenceTypesEquality)]

<span data-ttu-id="c3839-123">Jak ukazuje příklad, uživatelem definované referenční typy podporu `==` operátor ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="c3839-123">As the example shows, user-defined reference types support the `==` operator by default.</span></span> <span data-ttu-id="c3839-124">Však můžete přetížit typ definovaný uživatelem odkazu `==` operátor.</span><span class="sxs-lookup"><span data-stu-id="c3839-124">However, a user-defined reference type can overload the `==` operator.</span></span> <span data-ttu-id="c3839-125">Pokud typ odkazu přetížení `==` operátoru, použijte <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> metodu ke kontrole, pokud dva odkazy tohoto typu odkazují na stejný objekt.</span><span class="sxs-lookup"><span data-stu-id="c3839-125">If a reference type overloads the `==` operator, use the <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> method to check if two references of that type refer to the same object.</span></span>

## <a name="delegate-equality"></a><span data-ttu-id="c3839-126">Delegát rovnosti</span><span class="sxs-lookup"><span data-stu-id="c3839-126">Delegate equality</span></span>

<span data-ttu-id="c3839-127">Dvě [delegovat](../../programming-guide/delegates/index.md) operandy stejného typu modulu runtime jsou stejné, pokud jsou obě z nich `null` nebo jejich vyvolání seznamy se stejnou délkou a mají stejné položky v každé pozici:</span><span class="sxs-lookup"><span data-stu-id="c3839-127">Two [delegate](../../programming-guide/delegates/index.md) operands of the same runtime type are equal when both of them are `null` or their invocation lists are of the same length and have equal entries in each position:</span></span>

[!code-csharp-interactive[delegate equality](~/samples/csharp/language-reference/operators/EqualityOperators.cs#DelegateEquality)]

<span data-ttu-id="c3839-128">Další informace najdete v tématu [delegovat operátory rovnosti](~/_csharplang/spec/expressions.md#delegate-equality-operators) část [ C# specifikace jazyka](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="c3839-128">For more information, see the [Delegate equality operators](~/_csharplang/spec/expressions.md#delegate-equality-operators) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="c3839-129">Delegáty, které jsou vytvářeny ze zkušební verze sémanticky identických [výrazy lambda](../../programming-guide/statements-expressions-operators/lambda-expressions.md) nejsou stejné, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="c3839-129">Delegates that are produced from evaluation of semantically identical [lambda expressions](../../programming-guide/statements-expressions-operators/lambda-expressions.md) are not equal, as the following example shows:</span></span>

[!code-csharp-interactive[from identical lambdas](~/samples/csharp/language-reference/operators/EqualityOperators.cs#IdenticalLambdas)]

## <a name="inequality-operator-"></a><span data-ttu-id="c3839-130">Operátor nerovnosti! =</span><span class="sxs-lookup"><span data-stu-id="c3839-130">Inequality operator !=</span></span>

<span data-ttu-id="c3839-131">Operátor nerovnosti `!=` vrátí `true` Pokud nejsou stejné, jeho operandy `false` jinak.</span><span class="sxs-lookup"><span data-stu-id="c3839-131">The inequality operator `!=` returns `true` if its operands are not equal, `false` otherwise.</span></span> <span data-ttu-id="c3839-132">Pro operandy [předdefinovaných typů](../keywords/built-in-types-table.md), výraz `x != y` vytváří stejný výsledek jako výraz `!(x == y)`.</span><span class="sxs-lookup"><span data-stu-id="c3839-132">For the operands of the [built-in types](../keywords/built-in-types-table.md), the expression `x != y` produces the same result as the expression `!(x == y)`.</span></span> <span data-ttu-id="c3839-133">Další informace o typu rovnosti, najdete v článku [operátor rovnosti](#equality-operator-) oddílu.</span><span class="sxs-lookup"><span data-stu-id="c3839-133">For more information about type equality, see the [Equality operator](#equality-operator-) section.</span></span>

<span data-ttu-id="c3839-134">Následující příklad ukazuje použití `!=` operátor:</span><span class="sxs-lookup"><span data-stu-id="c3839-134">The following example demonstrates the usage of the `!=` operator:</span></span>

[!code-csharp-interactive[non-equality examples](~/samples/csharp/language-reference/operators/EqualityOperators.cs#NonEquality)]

## <a name="operator-overloadability"></a><span data-ttu-id="c3839-135">Overloadability – operátor</span><span class="sxs-lookup"><span data-stu-id="c3839-135">Operator overloadability</span></span>

<span data-ttu-id="c3839-136">Uživatelem definovaný typ může [přetížení](../keywords/operator.md) `==` a `!=` operátory.</span><span class="sxs-lookup"><span data-stu-id="c3839-136">A user-defined type can [overload](../keywords/operator.md) the `==` and `!=` operators.</span></span> <span data-ttu-id="c3839-137">Pokud typ přetížení mezi dva operátory, musíte také přetížit jiný.</span><span class="sxs-lookup"><span data-stu-id="c3839-137">If a type overloads one of the two operators, it must also overload another one.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="c3839-138">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="c3839-138">C# language specification</span></span>

<span data-ttu-id="c3839-139">Další informace najdete v tématu [relační a typové zkoušky operátory](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) část [ C# specifikace jazyka](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="c3839-139">For more information, see the [Relational and type-testing operators](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="c3839-140">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c3839-140">See also</span></span>

- [<span data-ttu-id="c3839-141">C#referenční dokumentace</span><span class="sxs-lookup"><span data-stu-id="c3839-141">C# reference</span></span>](../index.md)
- [<span data-ttu-id="c3839-142">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="c3839-142">C# operators</span></span>](index.md)
- <xref:System.IEquatable%601?displayProperty=nameWithType>
- <xref:System.Object.Equals%2A?displayProperty=nameWithType>
- <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType>
- [<span data-ttu-id="c3839-143">Porovnání rovnosti</span><span class="sxs-lookup"><span data-stu-id="c3839-143">Equality comparisons</span></span>](../../programming-guide/statements-expressions-operators/equality-comparisons.md)
- [<span data-ttu-id="c3839-144">Operátory porovnání</span><span class="sxs-lookup"><span data-stu-id="c3839-144">Comparison operators</span></span>](comparison-operators.md)
