---
title: '> Operator - C# odkaz'
ms.custom: seodec18
ms.date: 12/18/2018
f1_keywords:
- '>_CSharpKeyword'
helpviewer_keywords:
- '> operator [C#]'
- greater than operator (>) [C#]
ms.assetid: 26d3cb69-9c0b-4cc5-858b-5be1abd6659d
ms.openlocfilehash: 3b036c491d9663bf4ab0971d84a0a8d58d902ee6
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55287206"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="dfa81-102">> – operátor (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="dfa81-102">> Operator (C# Reference)</span></span>

<span data-ttu-id="dfa81-103">Relační operátor "větší než" `>` vrátí `true` Pokud svůj první operand je větší než jeho druhým operandem, `false` jinak.</span><span class="sxs-lookup"><span data-stu-id="dfa81-103">The "greater than" relational operator `>` returns `true` if its first operand is greater than its second operand, `false` otherwise.</span></span> <span data-ttu-id="dfa81-104">Všechny typy číselné a výčet podporují `>` operátor.</span><span class="sxs-lookup"><span data-stu-id="dfa81-104">All numeric and enumeration types support the `>` operator.</span></span> <span data-ttu-id="dfa81-105">Pro operandy stejného [výčtu](../keywords/enum.md) porovnání typu hodnoty odpovídající základní celočíselného typu.</span><span class="sxs-lookup"><span data-stu-id="dfa81-105">For operands of the same [enum](../keywords/enum.md) type, the corresponding values of the underlying integral type are compared.</span></span>

> [!NOTE]
> <span data-ttu-id="dfa81-106">Pro relační operátory `==`, `>`, `<`, `>=`, a `<=`, pokud žádný z operandů není číslo (<xref:System.Double.NaN?displayProperty=nameWithType> nebo <xref:System.Single.NaN?displayProperty=nameWithType>) je výsledek operace `false`.</span><span class="sxs-lookup"><span data-stu-id="dfa81-106">For relational operators `==`, `>`, `<`, `>=`, and `<=`, if any of the operands is not a number (<xref:System.Double.NaN?displayProperty=nameWithType> or <xref:System.Single.NaN?displayProperty=nameWithType>) the result of operation is `false`.</span></span> <span data-ttu-id="dfa81-107">To znamená, že `NaN` hodnota není větší než, menší než, ani jakýkoli jiný roven `double` (nebo `float`) hodnotu.</span><span class="sxs-lookup"><span data-stu-id="dfa81-107">That means that the `NaN` value is neither greater than, less than, nor equal to any other `double` (or `float`) value.</span></span> <span data-ttu-id="dfa81-108">Další informace a příklady najdete v tématu <xref:System.Double.NaN?displayProperty=nameWithType> nebo <xref:System.Single.NaN?displayProperty=nameWithType> článku.</span><span class="sxs-lookup"><span data-stu-id="dfa81-108">For more information and examples, see the <xref:System.Double.NaN?displayProperty=nameWithType> or <xref:System.Single.NaN?displayProperty=nameWithType> reference article.</span></span>

<span data-ttu-id="dfa81-109">Následující příklad ukazuje použití `>` operátor:</span><span class="sxs-lookup"><span data-stu-id="dfa81-109">The following example demonstrates the usage of the `>` operator:</span></span>

[!code-csharp-interactive[greater than example](~/samples/snippets/csharp/language-reference/operators/GreaterAndLessOperatorsExamples.cs#Greater)]

## <a name="operator-overloadability"></a><span data-ttu-id="dfa81-110">Overloadability – operátor</span><span class="sxs-lookup"><span data-stu-id="dfa81-110">Operator overloadability</span></span>

<span data-ttu-id="dfa81-111">Uživatelem definované typy lze [přetížení](../keywords/operator.md) `>` operátor.</span><span class="sxs-lookup"><span data-stu-id="dfa81-111">User-defined types can [overload](../keywords/operator.md) the `>` operator.</span></span> <span data-ttu-id="dfa81-112">Pokud typ přetížení operátoru "větší než" `>`, musíte také přetížit [operátor "menší než"](less-than-operator.md) `<`.</span><span class="sxs-lookup"><span data-stu-id="dfa81-112">If a type overloads the "greater than" operator `>`, it must also overload the ["less than" operator](less-than-operator.md) `<`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="dfa81-113">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="dfa81-113">C# language specification</span></span>

<span data-ttu-id="dfa81-114">Další informace najdete v tématu [relační a typové zkoušky operátory](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) část [ C# specifikace jazyka](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="dfa81-114">For more information, see the [Relational and type-testing operators](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="dfa81-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="dfa81-115">See also</span></span>

- [<span data-ttu-id="dfa81-116">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="dfa81-116">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="dfa81-117">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="dfa81-117">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="dfa81-118">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="dfa81-118">C# Operators</span></span>](index.md)
- [<span data-ttu-id="dfa81-119">>= – operátor</span><span class="sxs-lookup"><span data-stu-id="dfa81-119">>= Operator</span></span>](greater-than-equal-operator.md)
- <xref:System.IComparable%601?displayProperty=nameWithType>
