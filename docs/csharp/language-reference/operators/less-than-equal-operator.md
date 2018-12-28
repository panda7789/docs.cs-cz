---
title: '&lt;= – Operátor - C# odkaz'
ms.custom: seodec18
ms.date: 12/18/2018
f1_keywords:
- <=_CSharpKeyword
helpviewer_keywords:
- less than or equal to operator (<=) [C#]
- <= operator [C#]
ms.assetid: bb0caec9-d253-4105-b8bc-5252233251e4
ms.openlocfilehash: 30f42de68667756a8233fef4241bfd74ed4eff2a
ms.sourcegitcommit: 3d0c29b878f00caec288dfecb3a5c959de5aa629
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/20/2018
ms.locfileid: "53656086"
---
# <a name="lt-operator-c-reference"></a><span data-ttu-id="4c3fe-102">&lt;= – Operátor (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="4c3fe-102">&lt;= Operator (C# Reference)</span></span>

<span data-ttu-id="4c3fe-103">"Menší než nebo rovno" relační operátor `<=` vrátí `true` Pokud svůj první operand je menší nebo rovna svým druhým operandem, `false` jinak.</span><span class="sxs-lookup"><span data-stu-id="4c3fe-103">The "less than or equal" relational operator `<=` returns `true` if its first operand is less than or equal to its second operand, `false` otherwise.</span></span> <span data-ttu-id="4c3fe-104">Všechny typy číselné a výčet podporují `<=` operátor.</span><span class="sxs-lookup"><span data-stu-id="4c3fe-104">All numeric and enumeration types support the `<=` operator.</span></span> <span data-ttu-id="4c3fe-105">Pro operandy stejného [výčtu](../keywords/enum.md) porovnání typu hodnoty odpovídající základní celočíselného typu.</span><span class="sxs-lookup"><span data-stu-id="4c3fe-105">For operands of the same [enum](../keywords/enum.md) type, the corresponding values of the underlying integral type are compared.</span></span>

> [!NOTE]
> <span data-ttu-id="4c3fe-106">Pro relační operátory `==`, `>`, `<`, `>=`, a `<=`, pokud žádný z operandů není číslo (<xref:System.Double.NaN?displayProperty=nameWithType> nebo <xref:System.Single.NaN?displayProperty=nameWithType>) je výsledek operace `false`.</span><span class="sxs-lookup"><span data-stu-id="4c3fe-106">For relational operators `==`, `>`, `<`, `>=`, and `<=`, if any of the operands is not a number (<xref:System.Double.NaN?displayProperty=nameWithType> or <xref:System.Single.NaN?displayProperty=nameWithType>) the result of operation is `false`.</span></span> <span data-ttu-id="4c3fe-107">To znamená, že `NaN` hodnota není větší než, menší než, ani jakýkoli jiný roven `double` (nebo `float`) hodnotu.</span><span class="sxs-lookup"><span data-stu-id="4c3fe-107">That means that the `NaN` value is neither greater than, less than, nor equal to any other `double` (or `float`) value.</span></span> <span data-ttu-id="4c3fe-108">Další informace a příklady najdete v tématu <xref:System.Double.NaN?displayProperty=nameWithType> nebo <xref:System.Single.NaN?displayProperty=nameWithType> článku.</span><span class="sxs-lookup"><span data-stu-id="4c3fe-108">For more information and examples, see the <xref:System.Double.NaN?displayProperty=nameWithType> or <xref:System.Single.NaN?displayProperty=nameWithType> reference article.</span></span>

<span data-ttu-id="4c3fe-109">Následující příklad ukazuje použití `<=` operátor:</span><span class="sxs-lookup"><span data-stu-id="4c3fe-109">The following example demonstrates the usage of the `<=` operator:</span></span>

[!code-csharp-interactive[less than or equal example](~/samples/snippets/csharp/language-reference/operators/GreaterAndLessOperatorsExamples.cs#LessOrEqual)]

## <a name="operator-overloadability"></a><span data-ttu-id="4c3fe-110">Overloadability – operátor</span><span class="sxs-lookup"><span data-stu-id="4c3fe-110">Operator overloadability</span></span>

<span data-ttu-id="4c3fe-111">Uživatelem definované typy lze [přetížení](../keywords/operator.md) `<=` operátor.</span><span class="sxs-lookup"><span data-stu-id="4c3fe-111">User-defined types can [overload](../keywords/operator.md) the `<=` operator.</span></span> <span data-ttu-id="4c3fe-112">Pokud typ přetížení operátor "menší než nebo rovno" `<=`, musíte také přetížit [operátorem "větší než nebo rovno"](greater-than-equal-operator.md) `>=`.</span><span class="sxs-lookup"><span data-stu-id="4c3fe-112">If a type overloads the "less than or equal" operator `<=`, it must also overload the ["greater than or equal" operator](greater-than-equal-operator.md) `>=`.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="4c3fe-113">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="4c3fe-113">C# language specification</span></span>

<span data-ttu-id="4c3fe-114">Další informace najdete v tématu [relační a typové zkoušky operátory](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) část [ C# specifikace jazyka](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="4c3fe-114">For more information, see the [Relational and type-testing operators](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="4c3fe-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4c3fe-115">See also</span></span>

- [<span data-ttu-id="4c3fe-116">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="4c3fe-116">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="4c3fe-117">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="4c3fe-117">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="4c3fe-118">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="4c3fe-118">C# Operators</span></span>](index.md)
- [<span data-ttu-id="4c3fe-119">< – operátor</span><span class="sxs-lookup"><span data-stu-id="4c3fe-119">< Operator</span></span>](less-than-operator.md)
- [<span data-ttu-id="4c3fe-120">== – operátor</span><span class="sxs-lookup"><span data-stu-id="4c3fe-120">== Operator</span></span>](equality-comparison-operator.md)
- <xref:System.IComparable%601?displayProperty=nameWithType>
