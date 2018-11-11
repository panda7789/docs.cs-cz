---
title: + – Operátor (referenční dokumentace jazyka C#)
ms.date: 10/22/2018
f1_keywords:
- +_CSharpKeyword
helpviewer_keywords:
- + operator [C#]
- concatenation operator [C#]
- addition operator [C#]
ms.assetid: 93e56486-bb42-43c1-bd43-60af11e64e67
ms.openlocfilehash: 27ea47d698b20f112880750ec0bc931f1917f142
ms.sourcegitcommit: 3b1cb8467bd73dee854b604e306c0e7e3882d91a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2018
ms.locfileid: "50192294"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="e98c8-102">+ – operátor (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="e98c8-102">+ Operator (C# Reference)</span></span>

<span data-ttu-id="e98c8-103">`+` Operátor je podporován ve dvou formách: Unární plus operátor nebo operátor binární sčítání.</span><span class="sxs-lookup"><span data-stu-id="e98c8-103">The `+` operator is supported in two forms: a unary plus operator or a binary addition operator.</span></span>

## <a name="unary-plus-operator"></a><span data-ttu-id="e98c8-104">Jednočlenný operátor plus</span><span class="sxs-lookup"><span data-stu-id="e98c8-104">Unary plus operator</span></span>

<span data-ttu-id="e98c8-105">Unární `+` operátor vrátí hodnotu svého operandu.</span><span class="sxs-lookup"><span data-stu-id="e98c8-105">The unary `+` operator returns the value of its operand.</span></span> <span data-ttu-id="e98c8-106">Podporuje všechny číselné typy.</span><span class="sxs-lookup"><span data-stu-id="e98c8-106">It's supported by all numeric types.</span></span>

## <a name="numeric-addition"></a><span data-ttu-id="e98c8-107">Číselné sčítání</span><span class="sxs-lookup"><span data-stu-id="e98c8-107">Numeric addition</span></span>

<span data-ttu-id="e98c8-108">Pro číselné typy `+` operátor vypočítá součet operandů:</span><span class="sxs-lookup"><span data-stu-id="e98c8-108">For numeric types, the `+` operator computes the sum of its operands:</span></span>

[!code-csharp-interactive[numeric addition](~/samples/snippets/csharp/language-reference/operators/AdditionExamples.cs#AddNumerics)]

## <a name="string-concatenation"></a><span data-ttu-id="e98c8-109">Zřetězení řetězců</span><span class="sxs-lookup"><span data-stu-id="e98c8-109">String concatenation</span></span>

<span data-ttu-id="e98c8-110">Když se jeden nebo oba operandy typu [řetězec](../keywords/string.md), `+` zřetězí řetězcové reprezentace jeho operandy operátoru:</span><span class="sxs-lookup"><span data-stu-id="e98c8-110">When one or both operands are of type [string](../keywords/string.md), the `+` operator concatenates the string representations of its operands:</span></span>

[!code-csharp-interactive[string concatenation](~/samples/snippets/csharp/language-reference/operators/AdditionExamples.cs#AddStrings)]

<span data-ttu-id="e98c8-111">Počínaje C# 6, [interpolace](../tokens/interpolated.md) poskytuje pohodlnější způsob, jak formátovací řetězce:</span><span class="sxs-lookup"><span data-stu-id="e98c8-111">Starting with C# 6, [string interpolation](../tokens/interpolated.md) provides a more convenient way to format strings:</span></span>

[!code-csharp-interactive[string interpolation](~/samples/snippets/csharp/language-reference/operators/AdditionExamples.cs#UseStringInterpolation)]

## <a name="delegate-combination"></a><span data-ttu-id="e98c8-112">Kombinaci delegátů</span><span class="sxs-lookup"><span data-stu-id="e98c8-112">Delegate combination</span></span>

<span data-ttu-id="e98c8-113">Pro [delegovat](../keywords/delegate.md) typy, `+` operátor vrátí novou instanci delegáta, která při vyvolání, vyvolá prvním operandem a poté vyvolá druhého operandu.</span><span class="sxs-lookup"><span data-stu-id="e98c8-113">For [delegate](../keywords/delegate.md) types, the `+` operator returns a new delegate instance that, when invoked, invokes the first operand and then invokes the second operand.</span></span> <span data-ttu-id="e98c8-114">Pokud kterýkoli z operandů `null`, `+` operátor vrátí hodnotu jiný operand (která může být také `null`).</span><span class="sxs-lookup"><span data-stu-id="e98c8-114">If any of the operands is `null`, the `+` operator returns the value of another operand (which also might be `null`).</span></span> <span data-ttu-id="e98c8-115">Následující příklad ukazuje, jak mohou být kombinovány delegáty s `+` operátor:</span><span class="sxs-lookup"><span data-stu-id="e98c8-115">The following example shows how delegates can be combined with the `+` operator:</span></span>

[!code-csharp-interactive[delegate combination](~/samples/snippets/csharp/language-reference/operators/AdditionExamples.cs#AddDelegates)]

<span data-ttu-id="e98c8-116">Další informace o typech delegáta, naleznete v tématu [delegáti](../../programming-guide/delegates/index.md).</span><span class="sxs-lookup"><span data-stu-id="e98c8-116">For more information about delegate types, see [Delegates](../../programming-guide/delegates/index.md).</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="e98c8-117">Overloadability – operátor</span><span class="sxs-lookup"><span data-stu-id="e98c8-117">Operator overloadability</span></span>

<span data-ttu-id="e98c8-118">Uživatelem definované typy lze [přetížení](../keywords/operator.md) jednočlenné a binární `+` operátory.</span><span class="sxs-lookup"><span data-stu-id="e98c8-118">User-defined types can [overload](../keywords/operator.md) the unary and binary `+` operators.</span></span> <span data-ttu-id="e98c8-119">Když binární soubor `+` je operátor přetížen, [operátor přiřazení sčítání](addition-assignment-operator.md) `+=` je také implicitně přetížená.</span><span class="sxs-lookup"><span data-stu-id="e98c8-119">When a binary `+` operator is overloaded, the [addition assignment operator](addition-assignment-operator.md) `+=` is also implicitly overloaded.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="e98c8-120">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="e98c8-120">C# language specification</span></span>

<span data-ttu-id="e98c8-121">Další informace najdete v tématu [unární operátor plus](~/_csharplang/spec/expressions.md#unary-plus-operator) a [operátor sčítání](~/_csharplang/spec/expressions.md#addition-operator) oddíly [ C# specifikace jazyka](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="e98c8-121">For more information, see the [Unary plus operator](~/_csharplang/spec/expressions.md#unary-plus-operator) and [Addition operator](~/_csharplang/spec/expressions.md#addition-operator) sections of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e98c8-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e98c8-122">See also</span></span>

- [<span data-ttu-id="e98c8-123">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="e98c8-123">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="e98c8-124">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="e98c8-124">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="e98c8-125">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="e98c8-125">C# Operators</span></span>](index.md)
- [<span data-ttu-id="e98c8-126">Interpolace řetězců</span><span class="sxs-lookup"><span data-stu-id="e98c8-126">String interpolation</span></span>](../tokens/interpolated.md)
- [<span data-ttu-id="e98c8-127">Postupy: Zřetězení více řetězců</span><span class="sxs-lookup"><span data-stu-id="e98c8-127">How to: Concatenate Multiple Strings</span></span>](../../how-to/concatenate-multiple-strings.md)
- [<span data-ttu-id="e98c8-128">Delegáti</span><span class="sxs-lookup"><span data-stu-id="e98c8-128">Delegates</span></span>](../../programming-guide/delegates/index.md)
- [<span data-ttu-id="e98c8-129">Zaškrtnuto a nezaškrtnuto</span><span class="sxs-lookup"><span data-stu-id="e98c8-129">Checked and unchecked</span></span>](../keywords/checked-and-unchecked.md)
