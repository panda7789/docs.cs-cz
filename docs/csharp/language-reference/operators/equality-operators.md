---
title: Operátory rovnosti – odkaz jazyka C#
description: Další informace o operátory porovnání rovnosti Jazyka C# a rovnosti typu C#.
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
ms.openlocfilehash: 079522b18afdf86a942d502672174516d45d37fc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399565"
---
# <a name="equality-operators-c-reference"></a><span data-ttu-id="3d78f-103">Operátory rovnosti (odkaz C#)</span><span class="sxs-lookup"><span data-stu-id="3d78f-103">Equality operators (C# reference)</span></span>

<span data-ttu-id="3d78f-104">Operátory [ `==` (rovnosti)](#equality-operator-) a [ `!=` (nerovnosti)](#inequality-operator-) kontrolují, zda jsou jejich operandy stejné nebo ne.</span><span class="sxs-lookup"><span data-stu-id="3d78f-104">The [`==` (equality)](#equality-operator-) and [`!=` (inequality)](#inequality-operator-) operators check if their operands are equal or not.</span></span>

## <a name="equality-operator-"></a><span data-ttu-id="3d78f-105">Operátor rovnosti ==</span><span class="sxs-lookup"><span data-stu-id="3d78f-105">Equality operator ==</span></span>

<span data-ttu-id="3d78f-106">Operátor `==` rovnosti `true` vrátí, pokud jeho operandy jsou stejné, `false` jinak.</span><span class="sxs-lookup"><span data-stu-id="3d78f-106">The equality operator `==` returns `true` if its operands are equal, `false` otherwise.</span></span>

### <a name="value-types-equality"></a><span data-ttu-id="3d78f-107">Rovnost typů hodnot</span><span class="sxs-lookup"><span data-stu-id="3d78f-107">Value types equality</span></span>

<span data-ttu-id="3d78f-108">Operandy [předdefinovaných typů hodnot](../builtin-types/value-types.md#built-in-value-types) jsou stejné, pokud jsou jejich hodnoty stejné:</span><span class="sxs-lookup"><span data-stu-id="3d78f-108">Operands of the [built-in value types](../builtin-types/value-types.md#built-in-value-types) are equal if their values are equal:</span></span>

[!code-csharp-interactive[value types equality](snippets/EqualityOperators.cs#ValueTypesEquality)]

> [!NOTE]
> <span data-ttu-id="3d78f-109">Pro `==`, [ `<` `>`, `<=`, `>=` , , a](comparison-operators.md) operátory, pokud některý z operandů `false`není číslo (<xref:System.Double.NaN?displayProperty=nameWithType> nebo <xref:System.Single.NaN?displayProperty=nameWithType>), výsledek operace je .</span><span class="sxs-lookup"><span data-stu-id="3d78f-109">For the `==`, [`<`, `>`, `<=`, and `>=`](comparison-operators.md) operators, if any of the operands is not a number (<xref:System.Double.NaN?displayProperty=nameWithType> or <xref:System.Single.NaN?displayProperty=nameWithType>), the result of operation is `false`.</span></span> <span data-ttu-id="3d78f-110">To znamená, `NaN` že hodnota není větší než, menší než, `float`ani rovna `NaN`žádné jiné `double` (nebo ) hodnotu, včetně .</span><span class="sxs-lookup"><span data-stu-id="3d78f-110">That means that the `NaN` value is neither greater than, less than, nor equal to any other `double` (or `float`) value, including `NaN`.</span></span> <span data-ttu-id="3d78f-111">Další informace a příklady <xref:System.Double.NaN?displayProperty=nameWithType> naleznete <xref:System.Single.NaN?displayProperty=nameWithType> v článku nebo odkazu.</span><span class="sxs-lookup"><span data-stu-id="3d78f-111">For more information and examples, see the <xref:System.Double.NaN?displayProperty=nameWithType> or <xref:System.Single.NaN?displayProperty=nameWithType> reference article.</span></span>

<span data-ttu-id="3d78f-112">Dva operandy stejného typu [výčtu](../builtin-types/enum.md) jsou stejné, pokud jsou stejné odpovídající hodnoty základního integrálního typu.</span><span class="sxs-lookup"><span data-stu-id="3d78f-112">Two operands of the same [enum](../builtin-types/enum.md) type are equal if the corresponding values of the underlying integral type are equal.</span></span>

<span data-ttu-id="3d78f-113">Uživatelem definované typy [struktury](../builtin-types/struct.md) ve `==` výchozím nastavení nepodporují operátor.</span><span class="sxs-lookup"><span data-stu-id="3d78f-113">User-defined [struct](../builtin-types/struct.md) types don't support the `==` operator by default.</span></span> <span data-ttu-id="3d78f-114">Pro podporu `==` operátoru musí být struktura definovaná uživatelem [přetížena.](operator-overloading.md)</span><span class="sxs-lookup"><span data-stu-id="3d78f-114">To support the `==` operator, a user-defined struct must [overload](operator-overloading.md) it.</span></span>

<span data-ttu-id="3d78f-115">Počínaje C# 7.3 `==` a `!=` operátory jsou podporovány c# [řazené kolekce členů](../../tuples.md).</span><span class="sxs-lookup"><span data-stu-id="3d78f-115">Beginning with C# 7.3, the `==` and `!=` operators are supported by C# [tuples](../../tuples.md).</span></span> <span data-ttu-id="3d78f-116">Další informace naleznete v části [rovnosti a řazené kolekce členů](../../tuples.md#equality-and-tuples) [c# řazené kolekce členů](../../tuples.md) článku.</span><span class="sxs-lookup"><span data-stu-id="3d78f-116">For more information, see the [Equality and tuples](../../tuples.md#equality-and-tuples) section of the [C# tuple types](../../tuples.md) article.</span></span>

### <a name="reference-types-equality"></a><span data-ttu-id="3d78f-117">Rovnost referenčních typů</span><span class="sxs-lookup"><span data-stu-id="3d78f-117">Reference types equality</span></span>

<span data-ttu-id="3d78f-118">Ve výchozím nastavení jsou dva operandy referenčního typu stejné, pokud odkazují na stejný objekt:</span><span class="sxs-lookup"><span data-stu-id="3d78f-118">By default, two reference-type operands are equal if they refer to the same object:</span></span>

[!code-csharp[reference type equality](snippets/EqualityOperators.cs#ReferenceTypesEquality)]

<span data-ttu-id="3d78f-119">Jak ukazuje příklad, uživatelem definované `==` typy odkazů podporují operátor ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="3d78f-119">As the example shows, user-defined reference types support the `==` operator by default.</span></span> <span data-ttu-id="3d78f-120">Typ odkazu však může `==` přetížit operátor.</span><span class="sxs-lookup"><span data-stu-id="3d78f-120">However, a reference type can overload the `==` operator.</span></span> <span data-ttu-id="3d78f-121">Pokud typ odkazu přetíží `==` operátor, použijte metodu <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> ke kontrole, pokud dva odkazy tohoto typu odkazují na stejný objekt.</span><span class="sxs-lookup"><span data-stu-id="3d78f-121">If a reference type overloads the `==` operator, use the <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> method to check if two references of that type refer to the same object.</span></span>

### <a name="string-equality"></a><span data-ttu-id="3d78f-122">Rovnoprávnost řetězců</span><span class="sxs-lookup"><span data-stu-id="3d78f-122">String equality</span></span>

<span data-ttu-id="3d78f-123">Dva [řetězcové](../builtin-types/reference-types.md#the-string-type) operandy jsou stejné, když jsou obě instance řetězce `null` nebo obě instance řetězce mají stejnou délku a mají stejné znaky v každé pozici znaku:</span><span class="sxs-lookup"><span data-stu-id="3d78f-123">Two [string](../builtin-types/reference-types.md#the-string-type) operands are equal when both of them are `null` or both string instances are of the same length and have identical characters in each character position:</span></span>

[!code-csharp-interactive[string equality](snippets/EqualityOperators.cs#StringEquality)]

<span data-ttu-id="3d78f-124">To je případově rozlišující řadové srovnání.</span><span class="sxs-lookup"><span data-stu-id="3d78f-124">That is a case-sensitive ordinal comparison.</span></span> <span data-ttu-id="3d78f-125">Další informace o porovnání řetězců naleznete v tématu [Porovnání řetězců v c#](../../how-to/compare-strings.md).</span><span class="sxs-lookup"><span data-stu-id="3d78f-125">For more information about string comparison, see [How to compare strings in C#](../../how-to/compare-strings.md).</span></span>

### <a name="delegate-equality"></a><span data-ttu-id="3d78f-126">Rovnost delegátů</span><span class="sxs-lookup"><span data-stu-id="3d78f-126">Delegate equality</span></span>

<span data-ttu-id="3d78f-127">Dva [operandy delegáta](../../programming-guide/delegates/index.md) stejného typu runtime jsou `null` stejné, když oba jsou nebo jejich seznamy vyvolání mají stejnou délku a mají stejné položky v každé pozici:</span><span class="sxs-lookup"><span data-stu-id="3d78f-127">Two [delegate](../../programming-guide/delegates/index.md) operands of the same runtime type are equal when both of them are `null` or their invocation lists are of the same length and have equal entries in each position:</span></span>

[!code-csharp-interactive[delegate equality](snippets/EqualityOperators.cs#DelegateEquality)]

<span data-ttu-id="3d78f-128">Další informace naleznete v části [Operátory rovnosti delegáta](~/_csharplang/spec/expressions.md#delegate-equality-operators) [specifikace jazyka C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="3d78f-128">For more information, see the [Delegate equality operators](~/_csharplang/spec/expressions.md#delegate-equality-operators) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="3d78f-129">Delegáti, které jsou vyrobeny z hodnocení sémanticky identické [lambda výrazy](../../programming-guide/statements-expressions-operators/lambda-expressions.md) nejsou stejné, jak ukazuje následující příklad:</span><span class="sxs-lookup"><span data-stu-id="3d78f-129">Delegates that are produced from evaluation of semantically identical [lambda expressions](../../programming-guide/statements-expressions-operators/lambda-expressions.md) are not equal, as the following example shows:</span></span>

[!code-csharp-interactive[from identical lambdas](snippets/EqualityOperators.cs#IdenticalLambdas)]

## <a name="inequality-operator-"></a><span data-ttu-id="3d78f-130">Operátor nerovnosti !=</span><span class="sxs-lookup"><span data-stu-id="3d78f-130">Inequality operator !=</span></span>

<span data-ttu-id="3d78f-131">Operátor `!=` nerovnostvrátí, `true` pokud jeho operandy `false` nejsou stejné, jinak.</span><span class="sxs-lookup"><span data-stu-id="3d78f-131">The inequality operator `!=` returns `true` if its operands are not equal, `false` otherwise.</span></span> <span data-ttu-id="3d78f-132">Pro operandy [předdefinovaných typů](../builtin-types/built-in-types.md)výraz `x != y` vytváří stejný výsledek jako `!(x == y)`výraz .</span><span class="sxs-lookup"><span data-stu-id="3d78f-132">For the operands of the [built-in types](../builtin-types/built-in-types.md), the expression `x != y` produces the same result as the expression `!(x == y)`.</span></span> <span data-ttu-id="3d78f-133">Další informace o rovnosti typů naleznete v části [Operátor rovnosti.](#equality-operator-)</span><span class="sxs-lookup"><span data-stu-id="3d78f-133">For more information about type equality, see the [Equality operator](#equality-operator-) section.</span></span>

<span data-ttu-id="3d78f-134">Následující příklad ukazuje použití operátoru: `!=`</span><span class="sxs-lookup"><span data-stu-id="3d78f-134">The following example demonstrates the usage of the `!=` operator:</span></span>

[!code-csharp-interactive[non-equality examples](snippets/EqualityOperators.cs#NonEquality)]

## <a name="operator-overloadability"></a><span data-ttu-id="3d78f-135">Přetížení obsluhy</span><span class="sxs-lookup"><span data-stu-id="3d78f-135">Operator overloadability</span></span>

<span data-ttu-id="3d78f-136">Uživatelem definovaný typ může `==` `!=` [přetížit](operator-overloading.md) operátory a.</span><span class="sxs-lookup"><span data-stu-id="3d78f-136">A user-defined type can [overload](operator-overloading.md) the `==` and `!=` operators.</span></span> <span data-ttu-id="3d78f-137">Pokud typ přetíží jeden ze dvou operátorů, musí také přetížení jiný.</span><span class="sxs-lookup"><span data-stu-id="3d78f-137">If a type overloads one of the two operators, it must also overload another one.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="3d78f-138">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="3d78f-138">C# language specification</span></span>

<span data-ttu-id="3d78f-139">Další informace naleznete v části [Relační a typové testovací operátory](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) [specifikace jazyka C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="3d78f-139">For more information, see the [Relational and type-testing operators](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="3d78f-140">Viz také</span><span class="sxs-lookup"><span data-stu-id="3d78f-140">See also</span></span>

- [<span data-ttu-id="3d78f-141">Referenční dokumentace k jazyku C#</span><span class="sxs-lookup"><span data-stu-id="3d78f-141">C# reference</span></span>](../index.md)
- [<span data-ttu-id="3d78f-142">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="3d78f-142">C# operators</span></span>](index.md)
- <xref:System.IEquatable%601?displayProperty=nameWithType>
- <xref:System.Object.Equals%2A?displayProperty=nameWithType>
- <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType>
- [<span data-ttu-id="3d78f-143">Porovnání rovnosti</span><span class="sxs-lookup"><span data-stu-id="3d78f-143">Equality comparisons</span></span>](../../programming-guide/statements-expressions-operators/equality-comparisons.md)
- [<span data-ttu-id="3d78f-144">Operátory porovnání</span><span class="sxs-lookup"><span data-stu-id="3d78f-144">Comparison operators</span></span>](comparison-operators.md)
