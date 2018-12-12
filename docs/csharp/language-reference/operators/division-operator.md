---
title: / – Operátor - C# odkaz
ms.custom: seodec18
ms.date: 12/13/2018
f1_keywords:
- /_CSharpKeyword
helpviewer_keywords:
- / operator [C#]
- division operator [C#]
ms.assetid: d155e496-678f-4efa-bebe-2bd08da2c5af
ms.openlocfilehash: 45bcd64b60e7d13f389064faefeda815ea1f32c9
ms.sourcegitcommit: d6e419f9d9cd7e8f21ebf5acde6d016c16332579
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/12/2018
ms.locfileid: "53286530"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="39b8e-102">/ – operátor (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="39b8e-102">/ Operator (C# Reference)</span></span>

<span data-ttu-id="39b8e-103">Operátor dělení `/` rozděluje svůj první operand tak svým druhým operandem.</span><span class="sxs-lookup"><span data-stu-id="39b8e-103">The division operator `/` divides its first operand by its second operand.</span></span> <span data-ttu-id="39b8e-104">Všechny číselné typy podporují operátor dělení.</span><span class="sxs-lookup"><span data-stu-id="39b8e-104">All numeric types support the division operator.</span></span>

## <a name="integer-division"></a><span data-ttu-id="39b8e-105">Celočíselné dělení</span><span class="sxs-lookup"><span data-stu-id="39b8e-105">Integer division</span></span>

<span data-ttu-id="39b8e-106">Pro operandy typy celých čísel, výsledek `/` operátor je typu integer a rovnosti podílu dvou operandů zaokrouhlena směrem k nule.:</span><span class="sxs-lookup"><span data-stu-id="39b8e-106">For the operands of integer types, the result of the `/` operator is of an integer type and equals the quotient of the two operands rounded towards zero:</span></span>

[!code-csharp-interactive[integer division](~/samples/snippets/csharp/language-reference/operators/DivisionExamples.cs#Integer)]

<span data-ttu-id="39b8e-107">Chcete-li získat podílu dvou operandů jako číslo s plovoucí desetinnou čárkou, použijte `float`, `double`, nebo `decimal` typu:</span><span class="sxs-lookup"><span data-stu-id="39b8e-107">To obtain the quotient of the two operands as a floating-point number, use the `float`, `double`, or `decimal` type:</span></span>

[!code-csharp-interactive[integer as floating-point division](~/samples/snippets/csharp/language-reference/operators/DivisionExamples.cs#IntegerAsFloatingPoint)]

## <a name="floating-point-division"></a><span data-ttu-id="39b8e-108">S plovoucí desetinnou čárkou dělení</span><span class="sxs-lookup"><span data-stu-id="39b8e-108">Floating-point division</span></span>

<span data-ttu-id="39b8e-109">Pro `float`, `double`, a `decimal` typy, výsledek `/` operátor odpovídá podílu dvou operandů:</span><span class="sxs-lookup"><span data-stu-id="39b8e-109">For the `float`, `double`, and `decimal` types, the result of the `/` operator is the quotient of the two operands:</span></span>

[!code-csharp-interactive[floating-point division](~/samples/snippets/csharp/language-reference/operators/DivisionExamples.cs#FloatingPoint)]

<span data-ttu-id="39b8e-110">Pokud jeden z operandů je `decimal`, může být jiný operand ani `float` ani `double`, protože ani `float` ani `double` implicitně převést na `decimal`.</span><span class="sxs-lookup"><span data-stu-id="39b8e-110">If one of the operands is `decimal`, another operand can be neither `float` nor `double`, because neither `float` nor `double` is implicitly convertible to `decimal`.</span></span> <span data-ttu-id="39b8e-111">Je nutné explicitně převést `float` nebo `double` operand `decimal` typu.</span><span class="sxs-lookup"><span data-stu-id="39b8e-111">You must explicitly convert the `float` or `double` operand to the `decimal` type.</span></span> <span data-ttu-id="39b8e-112">Další informace o implicitní převody mezi číselnými typy najdete v tématu [tabulka implicitních číselných převodů](../keywords/implicit-numeric-conversions-table.md).</span><span class="sxs-lookup"><span data-stu-id="39b8e-112">For more information about implicit conversions between numeric types, see [Implicit numeric conversions table](../keywords/implicit-numeric-conversions-table.md).</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="39b8e-113">Overloadability – operátor</span><span class="sxs-lookup"><span data-stu-id="39b8e-113">Operator overloadability</span></span>

<span data-ttu-id="39b8e-114">Uživatelem definované typy lze [přetížení](../keywords/operator.md) `/` operátor.</span><span class="sxs-lookup"><span data-stu-id="39b8e-114">User-defined types can [overload](../keywords/operator.md) the `/` operator.</span></span> <span data-ttu-id="39b8e-115">Když `/` je operátor přetížen, [operátor přiřazení dělení](division-assignment-operator.md) `/=` je také implicitně přetížené.</span><span class="sxs-lookup"><span data-stu-id="39b8e-115">When the `/` operator is overloaded, the [division assignment operator](division-assignment-operator.md) `/=` is also implicitly overloaded.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="39b8e-116">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="39b8e-116">C# language specification</span></span>

<span data-ttu-id="39b8e-117">Další informace najdete v tématu [operátor dělení](~/_csharplang/spec/expressions.md#division-operator) část [ C# specifikace jazyka](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="39b8e-117">For more information, see the [Division operator](~/_csharplang/spec/expressions.md#division-operator) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="39b8e-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="39b8e-118">See also</span></span>

- [<span data-ttu-id="39b8e-119">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="39b8e-119">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="39b8e-120">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="39b8e-120">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="39b8e-121">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="39b8e-121">C# Operators</span></span>](index.md)
- [<span data-ttu-id="39b8e-122">% – operátor</span><span class="sxs-lookup"><span data-stu-id="39b8e-122">% Operator</span></span>](remainder-operator.md)
