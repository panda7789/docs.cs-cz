---
title: == – Operátor - C# odkaz
ms.custom: seodec18
ms.date: 12/14/2018
f1_keywords:
- ==_CSharpKeyword
helpviewer_keywords:
- == operator [C#]
- equality operator [C#]
ms.assetid: 34c6b597-caa2-4855-a7cd-38ecdd11bd07
ms.openlocfilehash: 6d86348eefc87e847267f262141ff49e5d51faae
ms.sourcegitcommit: 3d0c29b878f00caec288dfecb3a5c959de5aa629
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/20/2018
ms.locfileid: "53655956"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="275bf-102">== – operátor (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="275bf-102">== Operator (C# Reference)</span></span>

<span data-ttu-id="275bf-103">Operátor rovnosti `==` vrátí `true` pokud jeho operandy jsou si rovny, `false` jinak.</span><span class="sxs-lookup"><span data-stu-id="275bf-103">The equality operator `==` returns `true` if its operands are equal, `false` otherwise.</span></span>

## <a name="value-types-equality"></a><span data-ttu-id="275bf-104">Rovnost pro typy hodnot</span><span class="sxs-lookup"><span data-stu-id="275bf-104">Value types equality</span></span>

<span data-ttu-id="275bf-105">Operandy [integrované hodnotách](../keywords/value-types-table.md) jsou si rovny, pokud jsou si rovny jejich hodnoty:</span><span class="sxs-lookup"><span data-stu-id="275bf-105">Operands of the [built-in value types](../keywords/value-types-table.md) are equal if their values are equal:</span></span>

[!code-csharp-interactive[value types equality](~/samples/snippets/csharp/language-reference/operators/EqualityAndNonEqualityExamples.cs#ValueTypesEquality)]

> [!NOTE]
> <span data-ttu-id="275bf-106">Pro relační operátory `==`, `>`, `<`, `>=`, a `<=`, pokud žádný z operandů není číslo (<xref:System.Double.NaN?displayProperty=nameWithType> nebo <xref:System.Single.NaN?displayProperty=nameWithType>) je výsledek operace `false`.</span><span class="sxs-lookup"><span data-stu-id="275bf-106">For relational operators `==`, `>`, `<`, `>=`, and `<=`, if any of the operands is not a number (<xref:System.Double.NaN?displayProperty=nameWithType> or <xref:System.Single.NaN?displayProperty=nameWithType>) the result of operation is `false`.</span></span> <span data-ttu-id="275bf-107">To znamená, že `NaN` hodnota není větší než, menší než, ani jakýkoli jiný roven `double` (nebo `float`) hodnotu.</span><span class="sxs-lookup"><span data-stu-id="275bf-107">That means that the `NaN` value is neither greater than, less than, nor equal to any other `double` (or `float`) value.</span></span> <span data-ttu-id="275bf-108">Další informace a příklady najdete v tématu <xref:System.Double.NaN?displayProperty=nameWithType> nebo <xref:System.Single.NaN?displayProperty=nameWithType> článku.</span><span class="sxs-lookup"><span data-stu-id="275bf-108">For more information and examples, see the <xref:System.Double.NaN?displayProperty=nameWithType> or <xref:System.Single.NaN?displayProperty=nameWithType> reference article.</span></span>

<span data-ttu-id="275bf-109">Dva operandy stejného [výčtu](../keywords/enum.md) typu jsou si rovny, pokud jsou si rovny odpovídající hodnoty základní celočíselného typu.</span><span class="sxs-lookup"><span data-stu-id="275bf-109">Two operands of the same [enum](../keywords/enum.md) type are equal if the corresponding values of the underlying integral type are equal.</span></span>

<span data-ttu-id="275bf-110">Ve výchozím nastavení `==` operátor není definovaný pro uživatelem definované [struktura](../keywords/struct.md) typu.</span><span class="sxs-lookup"><span data-stu-id="275bf-110">By default, the `==` operator is not defined for a user-defined [struct](../keywords/struct.md) type.</span></span> <span data-ttu-id="275bf-111">Uživatelem definovaný typ může [přetížení](#operator-overloadability) `==` operátor.</span><span class="sxs-lookup"><span data-stu-id="275bf-111">A user-defined type can [overload](#operator-overloadability) the `==` operator.</span></span>

<span data-ttu-id="275bf-112">Počínaje C# 7.3, `==` a [ `!=` ](not-equal-operator.md) operátory jsou podporovány C# [řazených kolekcí členů](../../tuples.md).</span><span class="sxs-lookup"><span data-stu-id="275bf-112">Beginning with C# 7.3, the `==` and [`!=`](not-equal-operator.md) operators are supported by C# [tuples](../../tuples.md).</span></span> <span data-ttu-id="275bf-113">Další informace najdete v tématu [rovnosti a n-tice](../../tuples.md#equality-and-tuples) část [ C# typy řazené kolekce členů](../../tuples.md) článku.</span><span class="sxs-lookup"><span data-stu-id="275bf-113">For more information, see the [Equality and tuples](../../tuples.md#equality-and-tuples) section of the [C# tuple types](../../tuples.md) article.</span></span>

## <a name="string-equality"></a><span data-ttu-id="275bf-114">Rovnosti řetězce</span><span class="sxs-lookup"><span data-stu-id="275bf-114">String equality</span></span>

<span data-ttu-id="275bf-115">Dvě [řetězec](../keywords/string.md) operandy jsou stejné, pokud jsou obě z nich `null` nebo obě instance řetězce se stejnou délkou a mají stejné znaky v každé pozici znaku:</span><span class="sxs-lookup"><span data-stu-id="275bf-115">Two [string](../keywords/string.md) operands are equal when both of them are `null` or both string instances are of the same length and have identical characters in each character position:</span></span>

[!code-csharp-interactive[string equality](~/samples/snippets/csharp/language-reference/operators/EqualityAndNonEqualityExamples.cs#StringEquality)]

<span data-ttu-id="275bf-116">Je to velká a malá písmena ordinálního porovnání.</span><span class="sxs-lookup"><span data-stu-id="275bf-116">That is case-sensitive ordinal comparison.</span></span> <span data-ttu-id="275bf-117">Další informace o tom, jak porovnat řetězce najdete v tématu [porovnávání řetězců v C# ](../../how-to/compare-strings.md).</span><span class="sxs-lookup"><span data-stu-id="275bf-117">For more information about how to compare strings, see [How to compare strings in C#](../../how-to/compare-strings.md).</span></span>

## <a name="reference-types-equality"></a><span data-ttu-id="275bf-118">Referenční rovnost typy</span><span class="sxs-lookup"><span data-stu-id="275bf-118">Reference types equality</span></span>

<span data-ttu-id="275bf-119">Dvě jiných než `string` operandy typu odkaz jsou stejné, až si do stejného objektu:</span><span class="sxs-lookup"><span data-stu-id="275bf-119">Two other than `string` reference type operands are equal when they refer to the same object:</span></span>

[!code-csharp-interactive[reference type equality](~/samples/snippets/csharp/language-reference/operators/EqualityAndNonEqualityExamples.cs#ReferenceTypesEquality)]

<span data-ttu-id="275bf-120">Tento příklad ukazuje, že `==` operátor podporuje typy odkazů definované uživatelem.</span><span class="sxs-lookup"><span data-stu-id="275bf-120">The example shows that the `==` operator is supported by user-defined reference types.</span></span> <span data-ttu-id="275bf-121">Však můžete přetížit typ definovaný uživatelem odkazu `==` operátor.</span><span class="sxs-lookup"><span data-stu-id="275bf-121">However, a user-defined reference type can overload the `==` operator.</span></span> <span data-ttu-id="275bf-122">Pokud typ odkazu přetížení `==` operátoru, použijte <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> metodu ke kontrole, pokud dva odkazy tohoto typu odkazují na stejný objekt.</span><span class="sxs-lookup"><span data-stu-id="275bf-122">If a reference type overloads the `==` operator, use the <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> method to check if two references of that type refer to the same object.</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="275bf-123">Overloadability – operátor</span><span class="sxs-lookup"><span data-stu-id="275bf-123">Operator overloadability</span></span>

<span data-ttu-id="275bf-124">Uživatelem definované typy lze [přetížení](../keywords/operator.md) `==` operátor.</span><span class="sxs-lookup"><span data-stu-id="275bf-124">User-defined types can [overload](../keywords/operator.md) the `==` operator.</span></span> <span data-ttu-id="275bf-125">Pokud typ přetížení operátoru rovnosti `==`, musíte také přetížit [operátor nerovnosti](not-equal-operator.md) `!=`.</span><span class="sxs-lookup"><span data-stu-id="275bf-125">If a type overloads the equality operator `==`, it must also overload the [inequality operator](not-equal-operator.md) `!=`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="275bf-126">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="275bf-126">C# language specification</span></span>

<span data-ttu-id="275bf-127">Další informace najdete v tématu [relační a typové zkoušky operátory](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) část [ C# specifikace jazyka](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="275bf-127">For more information, see the [Relational and type-testing operators](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="275bf-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="275bf-128">See also</span></span>

- [<span data-ttu-id="275bf-129">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="275bf-129">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="275bf-130">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="275bf-130">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="275bf-131">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="275bf-131">C# Operators</span></span>](index.md)
- [<span data-ttu-id="275bf-132">Porovnání rovnosti</span><span class="sxs-lookup"><span data-stu-id="275bf-132">Equality comparisons</span></span>](../../programming-guide/statements-expressions-operators/equality-comparisons.md)
