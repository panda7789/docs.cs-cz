---
title: Operátory rovnosti C# – reference
description: Přečtěte C# si o operátorech C# porovnání rovnosti a typu rovnosti.
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
ms.openlocfilehash: 4a30068293bef3adb9f58cc7f61e7e24e144f31b
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395137"
---
# <a name="equality-operators-c-reference"></a><span data-ttu-id="e4c23-103">Operátory rovnostiC# (Referenční dokumentace)</span><span class="sxs-lookup"><span data-stu-id="e4c23-103">Equality operators (C# reference)</span></span>

<span data-ttu-id="e4c23-104">Operátory [`==` (rovnost)](#equality-operator-) a [`!=` (nerovnost)](#inequality-operator-) kontrolují, jestli jsou jejich operandy stejné nebo ne.</span><span class="sxs-lookup"><span data-stu-id="e4c23-104">The [`==` (equality)](#equality-operator-) and [`!=` (inequality)](#inequality-operator-) operators check if their operands are equal or not.</span></span>

## <a name="equality-operator-"></a><span data-ttu-id="e4c23-105">Operátor rovnosti = =</span><span class="sxs-lookup"><span data-stu-id="e4c23-105">Equality operator ==</span></span>

<span data-ttu-id="e4c23-106">Operátor rovnosti `==` vrátí `true`, pokud se jeho operandy rovnají, `false` v opačném případě.</span><span class="sxs-lookup"><span data-stu-id="e4c23-106">The equality operator `==` returns `true` if its operands are equal, `false` otherwise.</span></span>

### <a name="value-types-equality"></a><span data-ttu-id="e4c23-107">Rovnost typů hodnot</span><span class="sxs-lookup"><span data-stu-id="e4c23-107">Value types equality</span></span>

<span data-ttu-id="e4c23-108">Operandy [předdefinovaných hodnotových typů](../keywords/value-types-table.md) jsou stejné, pokud se jejich hodnoty rovnají:</span><span class="sxs-lookup"><span data-stu-id="e4c23-108">Operands of the [built-in value types](../keywords/value-types-table.md) are equal if their values are equal:</span></span>

[!code-csharp-interactive[value types equality](~/samples/csharp/language-reference/operators/EqualityOperators.cs#ValueTypesEquality)]

> [!NOTE]
> <span data-ttu-id="e4c23-109">U operátorů `==`, [`<`, `>`, `<=` a `>=`](comparison-operators.md) nejsou v případě žádného operandu číslo (<xref:System.Double.NaN?displayProperty=nameWithType> nebo <xref:System.Single.NaN?displayProperty=nameWithType>), výsledkem operace je @no__t 8.</span><span class="sxs-lookup"><span data-stu-id="e4c23-109">For the `==`, [`<`, `>`, `<=`, and `>=`](comparison-operators.md) operators, if any of the operands is not a number (<xref:System.Double.NaN?displayProperty=nameWithType> or <xref:System.Single.NaN?displayProperty=nameWithType>), the result of operation is `false`.</span></span> <span data-ttu-id="e4c23-110">To znamená, že hodnota `NaN` není větší než, menší nebo rovna žádné jiné hodnotě `double` (nebo `float`), včetně `NaN`.</span><span class="sxs-lookup"><span data-stu-id="e4c23-110">That means that the `NaN` value is neither greater than, less than, nor equal to any other `double` (or `float`) value, including `NaN`.</span></span> <span data-ttu-id="e4c23-111">Další informace a příklady najdete v článku referenční článek o <xref:System.Double.NaN?displayProperty=nameWithType> nebo <xref:System.Single.NaN?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e4c23-111">For more information and examples, see the <xref:System.Double.NaN?displayProperty=nameWithType> or <xref:System.Single.NaN?displayProperty=nameWithType> reference article.</span></span>

<span data-ttu-id="e4c23-112">Dva operandy stejného typu [výčtu](../keywords/enum.md) jsou stejné, pokud jsou odpovídající hodnoty základního integrálního typu stejné.</span><span class="sxs-lookup"><span data-stu-id="e4c23-112">Two operands of the same [enum](../keywords/enum.md) type are equal if the corresponding values of the underlying integral type are equal.</span></span>

<span data-ttu-id="e4c23-113">Uživatelsky definované typy [struktur](../keywords/struct.md) nepodporují ve výchozím nastavení operátor `==`.</span><span class="sxs-lookup"><span data-stu-id="e4c23-113">User-defined [struct](../keywords/struct.md) types don't support the `==` operator by default.</span></span> <span data-ttu-id="e4c23-114">Aby bylo možné podporovat operátor `==`, musí být tato uživatelsky definovanou strukturou [přetížena](#operator-overloadability) .</span><span class="sxs-lookup"><span data-stu-id="e4c23-114">To support the `==` operator, a user-defined struct must [overload](#operator-overloadability) it.</span></span>

<span data-ttu-id="e4c23-115">Počínaje C# 7,3 jsou operátory `==` a `!=` podporovány C# [řazenými kolekcemi členů](../../tuples.md).</span><span class="sxs-lookup"><span data-stu-id="e4c23-115">Beginning with C# 7.3, the `==` and `!=` operators are supported by C# [tuples](../../tuples.md).</span></span> <span data-ttu-id="e4c23-116">Další informace naleznete v části [rovnost a řazené kolekce členů](../../tuples.md#equality-and-tuples) v článku [ C# typy řazené kolekce členů](../../tuples.md) .</span><span class="sxs-lookup"><span data-stu-id="e4c23-116">For more information, see the [Equality and tuples](../../tuples.md#equality-and-tuples) section of the [C# tuple types](../../tuples.md) article.</span></span>

### <a name="reference-types-equality"></a><span data-ttu-id="e4c23-117">Rovnost typů odkazů</span><span class="sxs-lookup"><span data-stu-id="e4c23-117">Reference types equality</span></span>

<span data-ttu-id="e4c23-118">Ve výchozím nastavení jsou dva operandy typu odkazu stejné, pokud odkazují na stejný objekt:</span><span class="sxs-lookup"><span data-stu-id="e4c23-118">By default, two reference-type operands are equal if they refer to the same object:</span></span>

[!code-csharp[reference type equality](~/samples/csharp/language-reference/operators/EqualityOperators.cs#ReferenceTypesEquality)]

<span data-ttu-id="e4c23-119">Jak ukazuje příklad, uživatelsky definované typy odkazů podporují ve výchozím nastavení operátor `==`.</span><span class="sxs-lookup"><span data-stu-id="e4c23-119">As the example shows, user-defined reference types support the `==` operator by default.</span></span> <span data-ttu-id="e4c23-120">Typ odkazu však může přetížit operátor `==`.</span><span class="sxs-lookup"><span data-stu-id="e4c23-120">However, a reference type can overload the `==` operator.</span></span> <span data-ttu-id="e4c23-121">Pokud typ odkazu přetěžuje operátor `==`, použijte metodu <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> a ověřte, zda dva odkazy tohoto typu odkazují na stejný objekt.</span><span class="sxs-lookup"><span data-stu-id="e4c23-121">If a reference type overloads the `==` operator, use the <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> method to check if two references of that type refer to the same object.</span></span>

### <a name="string-equality"></a><span data-ttu-id="e4c23-122">Rovnost řetězců</span><span class="sxs-lookup"><span data-stu-id="e4c23-122">String equality</span></span>

<span data-ttu-id="e4c23-123">Dva [řetězcové](../keywords/string.md) operandy jsou stejné, pokud jsou oba `null` nebo jsou obě instance řetězce stejné délky a mají stejné znaky v každé pozici znaku:</span><span class="sxs-lookup"><span data-stu-id="e4c23-123">Two [string](../keywords/string.md) operands are equal when both of them are `null` or both string instances are of the same length and have identical characters in each character position:</span></span>

[!code-csharp-interactive[string equality](~/samples/csharp/language-reference/operators/EqualityOperators.cs#StringEquality)]

<span data-ttu-id="e4c23-124">To je ordinální porovnání rozlišující malá a velká písmena.</span><span class="sxs-lookup"><span data-stu-id="e4c23-124">That is a case-sensitive ordinal comparison.</span></span> <span data-ttu-id="e4c23-125">Další informace o porovnání řetězců naleznete v tématu [jak porovnat řetězce v C# ](../../how-to/compare-strings.md).</span><span class="sxs-lookup"><span data-stu-id="e4c23-125">For more information about string comparison, see [How to compare strings in C#](../../how-to/compare-strings.md).</span></span>

### <a name="delegate-equality"></a><span data-ttu-id="e4c23-126">Rovnost delegáta</span><span class="sxs-lookup"><span data-stu-id="e4c23-126">Delegate equality</span></span>

<span data-ttu-id="e4c23-127">Dva operandy [delegáta](../../programming-guide/delegates/index.md) stejného typu modulu runtime jsou stejné, pokud jsou oba `null` nebo jsou jejich seznamy volání stejné délky a mají stejné položky na každé pozici:</span><span class="sxs-lookup"><span data-stu-id="e4c23-127">Two [delegate](../../programming-guide/delegates/index.md) operands of the same runtime type are equal when both of them are `null` or their invocation lists are of the same length and have equal entries in each position:</span></span>

[!code-csharp-interactive[delegate equality](~/samples/csharp/language-reference/operators/EqualityOperators.cs#DelegateEquality)]

<span data-ttu-id="e4c23-128">Další informace naleznete v části [operátory rovnosti delegátů](~/_csharplang/spec/expressions.md#delegate-equality-operators) ve [ C# specifikaci jazyka](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="e4c23-128">For more information, see the [Delegate equality operators](~/_csharplang/spec/expressions.md#delegate-equality-operators) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="e4c23-129">Delegáty vytvořené z vyhodnocení sémanticky identických [výrazů lambda](../../programming-guide/statements-expressions-operators/lambda-expressions.md) nejsou stejné, jak ukazuje následující příklad:</span><span class="sxs-lookup"><span data-stu-id="e4c23-129">Delegates that are produced from evaluation of semantically identical [lambda expressions](../../programming-guide/statements-expressions-operators/lambda-expressions.md) are not equal, as the following example shows:</span></span>

[!code-csharp-interactive[from identical lambdas](~/samples/csharp/language-reference/operators/EqualityOperators.cs#IdenticalLambdas)]

## <a name="inequality-operator-"></a><span data-ttu-id="e4c23-130">Operátor nerovnosti! =</span><span class="sxs-lookup"><span data-stu-id="e4c23-130">Inequality operator !=</span></span>

<span data-ttu-id="e4c23-131">Operátor nerovnosti `!=` vrátí `true`, pokud jeho operandy nejsou stejné, `false` v opačném případě.</span><span class="sxs-lookup"><span data-stu-id="e4c23-131">The inequality operator `!=` returns `true` if its operands are not equal, `false` otherwise.</span></span> <span data-ttu-id="e4c23-132">U operandů [předdefinovaných typů](../keywords/built-in-types-table.md)výraz `x != y` vytvoří stejný výsledek jako výraz `!(x == y)`.</span><span class="sxs-lookup"><span data-stu-id="e4c23-132">For the operands of the [built-in types](../keywords/built-in-types-table.md), the expression `x != y` produces the same result as the expression `!(x == y)`.</span></span> <span data-ttu-id="e4c23-133">Další informace o rovnosti typů naleznete v části [operátor rovnosti](#equality-operator-) .</span><span class="sxs-lookup"><span data-stu-id="e4c23-133">For more information about type equality, see the [Equality operator](#equality-operator-) section.</span></span>

<span data-ttu-id="e4c23-134">Následující příklad ukazuje použití operátoru `!=`:</span><span class="sxs-lookup"><span data-stu-id="e4c23-134">The following example demonstrates the usage of the `!=` operator:</span></span>

[!code-csharp-interactive[non-equality examples](~/samples/csharp/language-reference/operators/EqualityOperators.cs#NonEquality)]

## <a name="operator-overloadability"></a><span data-ttu-id="e4c23-135">Přetížení operátoru</span><span class="sxs-lookup"><span data-stu-id="e4c23-135">Operator overloadability</span></span>

<span data-ttu-id="e4c23-136">Uživatelsky definovaný typ může [přetížit](operator-overloading.md) operátory `==` a `!=`.</span><span class="sxs-lookup"><span data-stu-id="e4c23-136">A user-defined type can [overload](operator-overloading.md) the `==` and `!=` operators.</span></span> <span data-ttu-id="e4c23-137">Pokud typ přetěžuje jednu ze dvou operátorů, musí také přetížit další.</span><span class="sxs-lookup"><span data-stu-id="e4c23-137">If a type overloads one of the two operators, it must also overload another one.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="e4c23-138">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="e4c23-138">C# language specification</span></span>

<span data-ttu-id="e4c23-139">Další informace naleznete v části [relační operátory and type-Testing](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) v [ C# tématu Specifikace jazyka](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="e4c23-139">For more information, see the [Relational and type-testing operators](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e4c23-140">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e4c23-140">See also</span></span>

- [<span data-ttu-id="e4c23-141">C#odkaz</span><span class="sxs-lookup"><span data-stu-id="e4c23-141">C# reference</span></span>](../index.md)
- [<span data-ttu-id="e4c23-142">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="e4c23-142">C# operators</span></span>](index.md)
- <xref:System.IEquatable%601?displayProperty=nameWithType>
- <xref:System.Object.Equals%2A?displayProperty=nameWithType>
- <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType>
- [<span data-ttu-id="e4c23-143">Porovnání rovnosti</span><span class="sxs-lookup"><span data-stu-id="e4c23-143">Equality comparisons</span></span>](../../programming-guide/statements-expressions-operators/equality-comparisons.md)
- [<span data-ttu-id="e4c23-144">Operátory porovnání</span><span class="sxs-lookup"><span data-stu-id="e4c23-144">Comparison operators</span></span>](comparison-operators.md)
