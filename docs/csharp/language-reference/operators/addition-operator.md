---
title: + Operator - C# odkaz
ms.custom: seodec18
ms.date: 10/22/2018
f1_keywords:
- +_CSharpKeyword
helpviewer_keywords:
- + operator [C#]
- concatenation operator [C#]
- addition operator [C#]
ms.assetid: 93e56486-bb42-43c1-bd43-60af11e64e67
ms.openlocfilehash: 0f04ba837f9c03107acd0b2174cbd07c14a8c213
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61660161"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="eed02-102">+ – operátor (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="eed02-102">+ Operator (C# Reference)</span></span>

<span data-ttu-id="eed02-103">`+` Operátor je podporován ve dvou formách: Unární plus operátor nebo operátor binární sčítání.</span><span class="sxs-lookup"><span data-stu-id="eed02-103">The `+` operator is supported in two forms: a unary plus operator or a binary addition operator.</span></span>

## <a name="unary-plus-operator"></a><span data-ttu-id="eed02-104">Jednočlenný operátor plus</span><span class="sxs-lookup"><span data-stu-id="eed02-104">Unary plus operator</span></span>

<span data-ttu-id="eed02-105">Unární `+` operátor vrátí hodnotu svého operandu.</span><span class="sxs-lookup"><span data-stu-id="eed02-105">The unary `+` operator returns the value of its operand.</span></span> <span data-ttu-id="eed02-106">Podporuje všechny číselné typy.</span><span class="sxs-lookup"><span data-stu-id="eed02-106">It's supported by all numeric types.</span></span>

## <a name="numeric-addition"></a><span data-ttu-id="eed02-107">Číselné sčítání</span><span class="sxs-lookup"><span data-stu-id="eed02-107">Numeric addition</span></span>

<span data-ttu-id="eed02-108">Pro číselné typy `+` operátor vypočítá součet operandů:</span><span class="sxs-lookup"><span data-stu-id="eed02-108">For numeric types, the `+` operator computes the sum of its operands:</span></span>

[!code-csharp-interactive[numeric addition](~/samples/snippets/csharp/language-reference/operators/AdditionExamples.cs#AddNumerics)]

<span data-ttu-id="eed02-109">Další informace o aritmetických operátorech naleznete v tématu [aritmetické operátory](arithmetic-operators.md).</span><span class="sxs-lookup"><span data-stu-id="eed02-109">For more information about arithmetic operators, see [Arithmetic operators](arithmetic-operators.md).</span></span>

## <a name="string-concatenation"></a><span data-ttu-id="eed02-110">Zřetězení řetězců</span><span class="sxs-lookup"><span data-stu-id="eed02-110">String concatenation</span></span>

<span data-ttu-id="eed02-111">Když se jeden nebo oba operandy typu [řetězec](../keywords/string.md), `+` zřetězí řetězcové reprezentace jeho operandy operátoru:</span><span class="sxs-lookup"><span data-stu-id="eed02-111">When one or both operands are of type [string](../keywords/string.md), the `+` operator concatenates the string representations of its operands:</span></span>

[!code-csharp-interactive[string concatenation](~/samples/snippets/csharp/language-reference/operators/AdditionExamples.cs#AddStrings)]

<span data-ttu-id="eed02-112">Počínaje C# 6, [interpolace](../tokens/interpolated.md) poskytuje pohodlnější způsob, jak formátovací řetězce:</span><span class="sxs-lookup"><span data-stu-id="eed02-112">Starting with C# 6, [string interpolation](../tokens/interpolated.md) provides a more convenient way to format strings:</span></span>

[!code-csharp-interactive[string interpolation](~/samples/snippets/csharp/language-reference/operators/AdditionExamples.cs#UseStringInterpolation)]

## <a name="delegate-combination"></a><span data-ttu-id="eed02-113">Kombinaci delegátů</span><span class="sxs-lookup"><span data-stu-id="eed02-113">Delegate combination</span></span>

<span data-ttu-id="eed02-114">Pro [delegovat](../keywords/delegate.md) typy, `+` operátor vrátí novou instanci delegáta, která při vyvolání, vyvolá prvním operandem a poté vyvolá druhého operandu.</span><span class="sxs-lookup"><span data-stu-id="eed02-114">For [delegate](../keywords/delegate.md) types, the `+` operator returns a new delegate instance that, when invoked, invokes the first operand and then invokes the second operand.</span></span> <span data-ttu-id="eed02-115">Pokud kterýkoli z operandů `null`, `+` operátor vrátí hodnotu jiný operand (která může být také `null`).</span><span class="sxs-lookup"><span data-stu-id="eed02-115">If any of the operands is `null`, the `+` operator returns the value of another operand (which also might be `null`).</span></span> <span data-ttu-id="eed02-116">Následující příklad ukazuje, jak mohou být kombinovány delegáty s `+` operátor:</span><span class="sxs-lookup"><span data-stu-id="eed02-116">The following example shows how delegates can be combined with the `+` operator:</span></span>

[!code-csharp-interactive[delegate combination](~/samples/snippets/csharp/language-reference/operators/AdditionExamples.cs#AddDelegates)]

<span data-ttu-id="eed02-117">Další informace o typech delegáta, naleznete v tématu [delegáti](../../programming-guide/delegates/index.md).</span><span class="sxs-lookup"><span data-stu-id="eed02-117">For more information about delegate types, see [Delegates](../../programming-guide/delegates/index.md).</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="eed02-118">Overloadability – operátor</span><span class="sxs-lookup"><span data-stu-id="eed02-118">Operator overloadability</span></span>

<span data-ttu-id="eed02-119">Uživatelem definované typy lze [přetížení](../keywords/operator.md) jednočlenné a binární `+` operátory.</span><span class="sxs-lookup"><span data-stu-id="eed02-119">User-defined types can [overload](../keywords/operator.md) the unary and binary `+` operators.</span></span> <span data-ttu-id="eed02-120">Když binární soubor `+` je operátor přetížen, [operátor přiřazení sčítání](addition-assignment-operator.md) `+=` je také implicitně přetížená.</span><span class="sxs-lookup"><span data-stu-id="eed02-120">When a binary `+` operator is overloaded, the [addition assignment operator](addition-assignment-operator.md) `+=` is also implicitly overloaded.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="eed02-121">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="eed02-121">C# language specification</span></span>

<span data-ttu-id="eed02-122">Další informace najdete v tématu [unární operátor plus](~/_csharplang/spec/expressions.md#unary-plus-operator) a [operátor sčítání](~/_csharplang/spec/expressions.md#addition-operator) oddíly [ C# specifikace jazyka](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="eed02-122">For more information, see the [Unary plus operator](~/_csharplang/spec/expressions.md#unary-plus-operator) and [Addition operator](~/_csharplang/spec/expressions.md#addition-operator) sections of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="eed02-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="eed02-123">See also</span></span>

- [<span data-ttu-id="eed02-124">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="eed02-124">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="eed02-125">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="eed02-125">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="eed02-126">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="eed02-126">C# Operators</span></span>](index.md)
- [<span data-ttu-id="eed02-127">Interpolace řetězců</span><span class="sxs-lookup"><span data-stu-id="eed02-127">String interpolation</span></span>](../tokens/interpolated.md)
- [<span data-ttu-id="eed02-128">Postupy: Řetězení více řetězců</span><span class="sxs-lookup"><span data-stu-id="eed02-128">How to: Concatenate Multiple Strings</span></span>](../../how-to/concatenate-multiple-strings.md)
- [<span data-ttu-id="eed02-129">Delegáti</span><span class="sxs-lookup"><span data-stu-id="eed02-129">Delegates</span></span>](../../programming-guide/delegates/index.md)
- [<span data-ttu-id="eed02-130">Zaškrtnuto a nezaškrtnuto</span><span class="sxs-lookup"><span data-stu-id="eed02-130">Checked and unchecked</span></span>](../keywords/checked-and-unchecked.md)
