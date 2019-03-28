---
title: < = – operátor - C# odkaz
ms.custom: seodec18
ms.date: 12/18/2018
f1_keywords:
- <=_CSharpKeyword
helpviewer_keywords:
- less than or equal to operator (<=) [C#]
- <= operator [C#]
ms.assetid: bb0caec9-d253-4105-b8bc-5252233251e4
ms.openlocfilehash: 54c8300ad883e81cfb3d4886881984fd5a0ebdb3
ms.sourcegitcommit: 4a8c2b8d0df44142728b68ebc842575840476f6d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/28/2019
ms.locfileid: "58545374"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="c0da8-102">\<= – Operátor (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="c0da8-102">\<= Operator (C# Reference)</span></span>

<span data-ttu-id="c0da8-103">"Menší než nebo rovno" relační operátor `<=` vrátí `true` Pokud svůj první operand je menší nebo rovna svým druhým operandem, `false` jinak.</span><span class="sxs-lookup"><span data-stu-id="c0da8-103">The "less than or equal" relational operator `<=` returns `true` if its first operand is less than or equal to its second operand, `false` otherwise.</span></span> <span data-ttu-id="c0da8-104">Všechny typy číselné a výčet podporují `<=` operátor.</span><span class="sxs-lookup"><span data-stu-id="c0da8-104">All numeric and enumeration types support the `<=` operator.</span></span> <span data-ttu-id="c0da8-105">Pro operandy stejného [výčtu](../keywords/enum.md) porovnání typu hodnoty odpovídající základní celočíselného typu.</span><span class="sxs-lookup"><span data-stu-id="c0da8-105">For operands of the same [enum](../keywords/enum.md) type, the corresponding values of the underlying integral type are compared.</span></span>

> [!NOTE]
> <span data-ttu-id="c0da8-106">Pro relační operátory `==`, `>`, `<`, `>=`, a `<=`, pokud žádný z operandů není číslo (<xref:System.Double.NaN?displayProperty=nameWithType> nebo <xref:System.Single.NaN?displayProperty=nameWithType>) je výsledek operace `false`.</span><span class="sxs-lookup"><span data-stu-id="c0da8-106">For relational operators `==`, `>`, `<`, `>=`, and `<=`, if any of the operands is not a number (<xref:System.Double.NaN?displayProperty=nameWithType> or <xref:System.Single.NaN?displayProperty=nameWithType>) the result of operation is `false`.</span></span> <span data-ttu-id="c0da8-107">To znamená, že `NaN` hodnota není větší než, menší než, ani jakýkoli jiný roven `double` (nebo `float`) hodnotu.</span><span class="sxs-lookup"><span data-stu-id="c0da8-107">That means that the `NaN` value is neither greater than, less than, nor equal to any other `double` (or `float`) value.</span></span> <span data-ttu-id="c0da8-108">Další informace a příklady najdete v tématu <xref:System.Double.NaN?displayProperty=nameWithType> nebo <xref:System.Single.NaN?displayProperty=nameWithType> článku.</span><span class="sxs-lookup"><span data-stu-id="c0da8-108">For more information and examples, see the <xref:System.Double.NaN?displayProperty=nameWithType> or <xref:System.Single.NaN?displayProperty=nameWithType> reference article.</span></span>

<span data-ttu-id="c0da8-109">Následující příklad ukazuje použití `<=` operátor:</span><span class="sxs-lookup"><span data-stu-id="c0da8-109">The following example demonstrates the usage of the `<=` operator:</span></span>

[!code-csharp-interactive[less than or equal example](~/samples/snippets/csharp/language-reference/operators/GreaterAndLessOperatorsExamples.cs#LessOrEqual)]

## <a name="operator-overloadability"></a><span data-ttu-id="c0da8-110">Overloadability – operátor</span><span class="sxs-lookup"><span data-stu-id="c0da8-110">Operator overloadability</span></span>

<span data-ttu-id="c0da8-111">Uživatelem definované typy lze [přetížení](../keywords/operator.md) `<=` operátor.</span><span class="sxs-lookup"><span data-stu-id="c0da8-111">User-defined types can [overload](../keywords/operator.md) the `<=` operator.</span></span> <span data-ttu-id="c0da8-112">Pokud typ přetížení operátor "menší než nebo rovno" `<=`, musíte také přetížit [operátorem "větší než nebo rovno"](greater-than-equal-operator.md) `>=`.</span><span class="sxs-lookup"><span data-stu-id="c0da8-112">If a type overloads the "less than or equal" operator `<=`, it must also overload the ["greater than or equal" operator](greater-than-equal-operator.md) `>=`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="c0da8-113">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="c0da8-113">C# language specification</span></span>

<span data-ttu-id="c0da8-114">Další informace najdete v tématu [relační a typové zkoušky operátory](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) část [ C# specifikace jazyka](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="c0da8-114">For more information, see the [Relational and type-testing operators](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="c0da8-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c0da8-115">See also</span></span>

- [<span data-ttu-id="c0da8-116">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="c0da8-116">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="c0da8-117">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="c0da8-117">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="c0da8-118">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="c0da8-118">C# Operators</span></span>](index.md)
- [<span data-ttu-id="c0da8-119">< – operátor</span><span class="sxs-lookup"><span data-stu-id="c0da8-119">< Operator</span></span>](less-than-operator.md)
- [<span data-ttu-id="c0da8-120">== – operátor</span><span class="sxs-lookup"><span data-stu-id="c0da8-120">== Operator</span></span>](equality-operators.md#equality-operator-)
- <xref:System.IComparable%601?displayProperty=nameWithType>
