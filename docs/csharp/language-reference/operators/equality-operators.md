---
title: Operátory rovnosti - C# odkaz
ms.date: 03/28/2019
author: pkulikov
f1_keywords:
- ==_CSharpKeyword
- '!=_CSharpKeyword'
helpviewer_keywords:
- equality operator [C#]
- equals operator [C#]
- == operator [C#]
- inequality operator [C#]
- not equals operator [C#]
- '!= operator [C#]'
ms.openlocfilehash: 297285ccb9aba7eae1d70a7d28a62241646a023c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59334156"
---
# <a name="equality-operators-c-reference"></a><span data-ttu-id="07b86-102">Operátory rovnosti (C# odkaz)</span><span class="sxs-lookup"><span data-stu-id="07b86-102">Equality operators (C# Reference)</span></span>

<span data-ttu-id="07b86-103">[ `==` (Rovnost)](#equality-operator-) a [ `!=` (nerovnost)](#inequality-operator-) operátory zkontrolujte, jestli operandy jsou stejné, nebo ne.</span><span class="sxs-lookup"><span data-stu-id="07b86-103">The [`==` (equality)](#equality-operator-) and [`!=` (inequality)](#inequality-operator-) operators check if their operands are equal or not.</span></span>

## <a name="equality-operator-"></a><span data-ttu-id="07b86-104">Operátor rovnosti ==</span><span class="sxs-lookup"><span data-stu-id="07b86-104">Equality operator ==</span></span>

<span data-ttu-id="07b86-105">Operátor rovnosti `==` vrátí `true` pokud jeho operandy jsou si rovny, `false` jinak.</span><span class="sxs-lookup"><span data-stu-id="07b86-105">The equality operator `==` returns `true` if its operands are equal, `false` otherwise.</span></span>

### <a name="value-types-equality"></a><span data-ttu-id="07b86-106">Rovnost pro typy hodnot</span><span class="sxs-lookup"><span data-stu-id="07b86-106">Value types equality</span></span>

<span data-ttu-id="07b86-107">Operandy [integrované hodnotách](../keywords/value-types-table.md) jsou si rovny, pokud jsou si rovny jejich hodnoty:</span><span class="sxs-lookup"><span data-stu-id="07b86-107">Operands of the [built-in value types](../keywords/value-types-table.md) are equal if their values are equal:</span></span>

[!code-csharp-interactive[value types equality](~/samples/snippets/csharp/language-reference/operators/EqualityAndNonEqualityExamples.cs#ValueTypesEquality)]

> [!NOTE]
> <span data-ttu-id="07b86-108">Rovnost a relační operátory `==`, `>`, `<`, `>=`, a `<=`, pokud žádný z operandů není číslo (<xref:System.Double.NaN?displayProperty=nameWithType> nebo <xref:System.Single.NaN?displayProperty=nameWithType>), je výsledek operace `false`.</span><span class="sxs-lookup"><span data-stu-id="07b86-108">For equality and relational operators `==`, `>`, `<`, `>=`, and `<=`, if any of the operands is not a number (<xref:System.Double.NaN?displayProperty=nameWithType> or <xref:System.Single.NaN?displayProperty=nameWithType>), the result of operation is `false`.</span></span> <span data-ttu-id="07b86-109">To znamená, že `NaN` hodnota není větší než, menší než, ani jakýkoli jiný roven `double` (nebo `float`) hodnotu, včetně `NaN`.</span><span class="sxs-lookup"><span data-stu-id="07b86-109">That means that the `NaN` value is neither greater than, less than, nor equal to any other `double` (or `float`) value, including `NaN`.</span></span> <span data-ttu-id="07b86-110">Další informace a příklady najdete v tématu <xref:System.Double.NaN?displayProperty=nameWithType> nebo <xref:System.Single.NaN?displayProperty=nameWithType> článku.</span><span class="sxs-lookup"><span data-stu-id="07b86-110">For more information and examples, see the <xref:System.Double.NaN?displayProperty=nameWithType> or <xref:System.Single.NaN?displayProperty=nameWithType> reference article.</span></span>

<span data-ttu-id="07b86-111">Dva operandy stejného [výčtu](../keywords/enum.md) typu jsou si rovny, pokud jsou si rovny odpovídající hodnoty základní celočíselného typu.</span><span class="sxs-lookup"><span data-stu-id="07b86-111">Two operands of the same [enum](../keywords/enum.md) type are equal if the corresponding values of the underlying integral type are equal.</span></span>

<span data-ttu-id="07b86-112">Uživatelem definované [struktura](../keywords/struct.md) typy se nepodporují `==` operátor ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="07b86-112">User-defined [struct](../keywords/struct.md) types don't support the `==` operator by default.</span></span> <span data-ttu-id="07b86-113">Pro podporu `==` operátor struktury definované uživatelem musí [přetížení](#operator-overloadability) ho.</span><span class="sxs-lookup"><span data-stu-id="07b86-113">To support the `==` operator, a user-defined struct must [overload](#operator-overloadability) it.</span></span>

<span data-ttu-id="07b86-114">Počínaje C# 7.3, `==` a `!=` operátory jsou podporovány C# [řazených kolekcí členů](../../tuples.md).</span><span class="sxs-lookup"><span data-stu-id="07b86-114">Beginning with C# 7.3, the `==` and `!=` operators are supported by C# [tuples](../../tuples.md).</span></span> <span data-ttu-id="07b86-115">Další informace najdete v tématu [rovnosti a n-tice](../../tuples.md#equality-and-tuples) část [ C# typy řazené kolekce členů](../../tuples.md) článku.</span><span class="sxs-lookup"><span data-stu-id="07b86-115">For more information, see the [Equality and tuples](../../tuples.md#equality-and-tuples) section of the [C# tuple types](../../tuples.md) article.</span></span>

### <a name="string-equality"></a><span data-ttu-id="07b86-116">Rovnosti řetězce</span><span class="sxs-lookup"><span data-stu-id="07b86-116">String equality</span></span>

<span data-ttu-id="07b86-117">Dvě [řetězec](../keywords/string.md) operandy jsou stejné, pokud jsou obě z nich `null` nebo obě instance řetězce se stejnou délkou a mají stejné znaky v každé pozici znaku:</span><span class="sxs-lookup"><span data-stu-id="07b86-117">Two [string](../keywords/string.md) operands are equal when both of them are `null` or both string instances are of the same length and have identical characters in each character position:</span></span>

[!code-csharp-interactive[string equality](~/samples/snippets/csharp/language-reference/operators/EqualityAndNonEqualityExamples.cs#StringEquality)]

<span data-ttu-id="07b86-118">Je to velká a malá písmena ordinálního porovnání.</span><span class="sxs-lookup"><span data-stu-id="07b86-118">That is case-sensitive ordinal comparison.</span></span> <span data-ttu-id="07b86-119">Další informace o porovnávání řetězců naleznete v tématu [porovnávání řetězců v C# ](../../how-to/compare-strings.md).</span><span class="sxs-lookup"><span data-stu-id="07b86-119">For more information about string comparison, see [How to compare strings in C#](../../how-to/compare-strings.md).</span></span>

### <a name="reference-types-equality"></a><span data-ttu-id="07b86-120">Referenční rovnost typy</span><span class="sxs-lookup"><span data-stu-id="07b86-120">Reference types equality</span></span>

<span data-ttu-id="07b86-121">Dvě jiných než `string` operandy typu odkaz jsou stejné, až si do stejného objektu:</span><span class="sxs-lookup"><span data-stu-id="07b86-121">Two other than `string` reference type operands are equal when they refer to the same object:</span></span>

[!code-csharp-interactive[reference type equality](~/samples/snippets/csharp/language-reference/operators/EqualityAndNonEqualityExamples.cs#ReferenceTypesEquality)]

<span data-ttu-id="07b86-122">Jak ukazuje příklad, uživatelem definované referenční typy podporu `==` operátor ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="07b86-122">As the example shows, user-defined reference types support the `==` operator by default.</span></span> <span data-ttu-id="07b86-123">Však můžete přetížit typ definovaný uživatelem odkazu `==` operátor.</span><span class="sxs-lookup"><span data-stu-id="07b86-123">However, a user-defined reference type can overload the `==` operator.</span></span> <span data-ttu-id="07b86-124">Pokud typ odkazu přetížení `==` operátoru, použijte <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> metodu ke kontrole, pokud dva odkazy tohoto typu odkazují na stejný objekt.</span><span class="sxs-lookup"><span data-stu-id="07b86-124">If a reference type overloads the `==` operator, use the <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> method to check if two references of that type refer to the same object.</span></span>

## <a name="inequality-operator-"></a><span data-ttu-id="07b86-125">Operátor nerovnosti! =</span><span class="sxs-lookup"><span data-stu-id="07b86-125">Inequality operator !=</span></span>

<span data-ttu-id="07b86-126">Operátor nerovnosti `!=` vrátí `true` Pokud nejsou stejné, jeho operandy `false` jinak.</span><span class="sxs-lookup"><span data-stu-id="07b86-126">The inequality operator `!=` returns `true` if its operands are not equal, `false` otherwise.</span></span> <span data-ttu-id="07b86-127">Pro operandy [předdefinovaných typů](../keywords/built-in-types-table.md), výraz `x != y` vytváří stejný výsledek jako výraz `!(x == y)`.</span><span class="sxs-lookup"><span data-stu-id="07b86-127">For the operands of the [built-in types](../keywords/built-in-types-table.md), the expression `x != y` produces the same result as the expression `!(x == y)`.</span></span> <span data-ttu-id="07b86-128">Další informace o typu rovnosti, najdete v článku [operátor rovnosti](#equality-operator-) oddílu.</span><span class="sxs-lookup"><span data-stu-id="07b86-128">For more information about type equality, see the [Equality operator](#equality-operator-) section.</span></span>

<span data-ttu-id="07b86-129">Následující příklad ukazuje použití `!=` operátor:</span><span class="sxs-lookup"><span data-stu-id="07b86-129">The following example demonstrates the usage of the `!=` operator:</span></span>

[!code-csharp-interactive[non-equality examples](~/samples/snippets/csharp/language-reference/operators/EqualityAndNonEqualityExamples.cs#NonEquality)]

## <a name="operator-overloadability"></a><span data-ttu-id="07b86-130">Overloadability – operátor</span><span class="sxs-lookup"><span data-stu-id="07b86-130">Operator overloadability</span></span>

<span data-ttu-id="07b86-131">Uživatelem definovaný typ může [přetížení](../keywords/operator.md) `==` a `!=` operátory.</span><span class="sxs-lookup"><span data-stu-id="07b86-131">A user-defined type can [overload](../keywords/operator.md) the `==` and `!=` operators.</span></span> <span data-ttu-id="07b86-132">Pokud typ přetížení mezi dva operátory, musíte také přetížit jiný.</span><span class="sxs-lookup"><span data-stu-id="07b86-132">If a type overloads one of the two operators, it must also overload another one.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="07b86-133">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="07b86-133">C# language specification</span></span>

<span data-ttu-id="07b86-134">Další informace najdete v tématu [relační a typové zkoušky operátory](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) část [ C# specifikace jazyka](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="07b86-134">For more information, see the [Relational and type-testing operators](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="07b86-135">Viz také:</span><span class="sxs-lookup"><span data-stu-id="07b86-135">See also</span></span>

- [<span data-ttu-id="07b86-136">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="07b86-136">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="07b86-137">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="07b86-137">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="07b86-138">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="07b86-138">C# Operators</span></span>](index.md)
- <xref:System.IEquatable%601?displayProperty=nameWithType>
- <xref:System.Object.Equals%2A?displayProperty=nameWithType>
- <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType>
- [<span data-ttu-id="07b86-139">Porovnání rovnosti</span><span class="sxs-lookup"><span data-stu-id="07b86-139">Equality comparisons</span></span>](../../programming-guide/statements-expressions-operators/equality-comparisons.md)
