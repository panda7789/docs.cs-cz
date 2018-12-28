---
title: '&lt; Operator - C# odkaz'
ms.custom: seodec18
ms.date: 12/18/2018
f1_keywords:
- <_CSharpKeyword
helpviewer_keywords:
- less than operator (<) [C#]
- < operator [C#]
ms.assetid: 38cb91e6-79a6-48ec-9c1e-7b71fd8d2b41
ms.openlocfilehash: bb0f590bb547c4e632bd14c773f095435c8986f0
ms.sourcegitcommit: 3d0c29b878f00caec288dfecb3a5c959de5aa629
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/20/2018
ms.locfileid: "53655943"
---
# <a name="lt-operator-c-reference"></a><span data-ttu-id="9b5de-102">&lt; – Operátor (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="9b5de-102">&lt; Operator (C# Reference)</span></span>

<span data-ttu-id="9b5de-103">"Menší než" relační operátor `<` vrátí `true` Pokud svůj první operand je menší než svým druhým operandem, `false` jinak.</span><span class="sxs-lookup"><span data-stu-id="9b5de-103">The "less than" relational operator `<` returns `true` if its first operand is less than its second operand, `false` otherwise.</span></span> <span data-ttu-id="9b5de-104">Všechny typy číselné a výčet podporují `<` operátor.</span><span class="sxs-lookup"><span data-stu-id="9b5de-104">All numeric and enumeration types support the `<` operator.</span></span> <span data-ttu-id="9b5de-105">Pro operandy stejného [výčtu](../keywords/enum.md) porovnání typu hodnoty odpovídající základní celočíselného typu.</span><span class="sxs-lookup"><span data-stu-id="9b5de-105">For operands of the same [enum](../keywords/enum.md) type, the corresponding values of the underlying integral type are compared.</span></span>

> [!NOTE]
> <span data-ttu-id="9b5de-106">Pro relační operátory `==`, `>`, `<`, `>=`, a `<=`, pokud žádný z operandů není číslo (<xref:System.Double.NaN?displayProperty=nameWithType> nebo <xref:System.Single.NaN?displayProperty=nameWithType>) je výsledek operace `false`.</span><span class="sxs-lookup"><span data-stu-id="9b5de-106">For relational operators `==`, `>`, `<`, `>=`, and `<=`, if any of the operands is not a number (<xref:System.Double.NaN?displayProperty=nameWithType> or <xref:System.Single.NaN?displayProperty=nameWithType>) the result of operation is `false`.</span></span> <span data-ttu-id="9b5de-107">To znamená, že `NaN` hodnota není větší než, menší než, ani jakýkoli jiný roven `double` (nebo `float`) hodnotu.</span><span class="sxs-lookup"><span data-stu-id="9b5de-107">That means that the `NaN` value is neither greater than, less than, nor equal to any other `double` (or `float`) value.</span></span> <span data-ttu-id="9b5de-108">Další informace a příklady najdete v tématu <xref:System.Double.NaN?displayProperty=nameWithType> nebo <xref:System.Single.NaN?displayProperty=nameWithType> článku.</span><span class="sxs-lookup"><span data-stu-id="9b5de-108">For more information and examples, see the <xref:System.Double.NaN?displayProperty=nameWithType> or <xref:System.Single.NaN?displayProperty=nameWithType> reference article.</span></span>

<span data-ttu-id="9b5de-109">Následující příklad ukazuje použití `<` operátor:</span><span class="sxs-lookup"><span data-stu-id="9b5de-109">The following example demonstrates the usage of the `<` operator:</span></span>

[!code-csharp-interactive[less than example](~/samples/snippets/csharp/language-reference/operators/GreaterAndLessOperatorsExamples.cs#Less)]

## <a name="operator-overloadability"></a><span data-ttu-id="9b5de-110">Overloadability – operátor</span><span class="sxs-lookup"><span data-stu-id="9b5de-110">Operator overloadability</span></span>

<span data-ttu-id="9b5de-111">Uživatelem definované typy lze [přetížení](../keywords/operator.md) `<` operátor.</span><span class="sxs-lookup"><span data-stu-id="9b5de-111">User-defined types can [overload](../keywords/operator.md) the `<` operator.</span></span> <span data-ttu-id="9b5de-112">Pokud typ přetížení operátor "menší než" `<`, musíte také přetížit ["větší než" operátor](greater-than-operator.md) `>`.</span><span class="sxs-lookup"><span data-stu-id="9b5de-112">If a type overloads the "less than" operator `<`, it must also overload the ["greater than" operator](greater-than-operator.md) `>`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="9b5de-113">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="9b5de-113">C# language specification</span></span>

<span data-ttu-id="9b5de-114">Další informace najdete v tématu [relační a typové zkoušky operátory](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) část [ C# specifikace jazyka](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="9b5de-114">For more information, see the [Relational and type-testing operators](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="9b5de-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9b5de-115">See also</span></span>

- [<span data-ttu-id="9b5de-116">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="9b5de-116">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="9b5de-117">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="9b5de-117">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="9b5de-118">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="9b5de-118">C# Operators</span></span>](index.md)
- [<span data-ttu-id="9b5de-119"><= – operátor</span><span class="sxs-lookup"><span data-stu-id="9b5de-119"><= Operator</span></span>](less-than-equal-operator.md)
- <xref:System.IComparable%601?displayProperty=nameWithType>
