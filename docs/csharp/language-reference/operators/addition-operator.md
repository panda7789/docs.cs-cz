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
ms.openlocfilehash: ae2774d96bc50afa271fffdea445e640e68c3647
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2018
ms.locfileid: "50192294"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="c2a8a-102">+ – operátor (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="c2a8a-102">+ Operator (C# Reference)</span></span>

<span data-ttu-id="c2a8a-103">`+` Operátor je podporován ve dvou formách: Unární plus operátor nebo operátor binární sčítání.</span><span class="sxs-lookup"><span data-stu-id="c2a8a-103">The `+` operator is supported in two forms: a unary plus operator or a binary addition operator.</span></span>

<span data-ttu-id="c2a8a-104">Uživatelem definované typy lze [přetížení](../keywords/operator.md) jednočlenné a binární `+` operátory.</span><span class="sxs-lookup"><span data-stu-id="c2a8a-104">User-defined types can [overload](../keywords/operator.md) the unary and binary `+` operators.</span></span> <span data-ttu-id="c2a8a-105">Když binární soubor `+` je operátor přetížen, [operátor přiřazení sčítání](addition-assignment-operator.md) `+=` je také implicitně přetížená.</span><span class="sxs-lookup"><span data-stu-id="c2a8a-105">When a binary `+` operator is overloaded, the [addition assignment operator](addition-assignment-operator.md) `+=` is also implicitly overloaded.</span></span>

## <a name="unary-plus-operator"></a><span data-ttu-id="c2a8a-106">Jednočlenný operátor plus</span><span class="sxs-lookup"><span data-stu-id="c2a8a-106">Unary plus operator</span></span>

<span data-ttu-id="c2a8a-107">Unární `+` operátor vrátí hodnotu svého operandu.</span><span class="sxs-lookup"><span data-stu-id="c2a8a-107">The unary `+` operator returns the value of its operand.</span></span> <span data-ttu-id="c2a8a-108">Podporuje všechny číselné typy.</span><span class="sxs-lookup"><span data-stu-id="c2a8a-108">It's supported by all numeric types.</span></span>

## <a name="numeric-addition"></a><span data-ttu-id="c2a8a-109">Číselné sčítání</span><span class="sxs-lookup"><span data-stu-id="c2a8a-109">Numeric addition</span></span>

<span data-ttu-id="c2a8a-110">Pro číselné typy `+` operátor vypočítá součet operandů:</span><span class="sxs-lookup"><span data-stu-id="c2a8a-110">For numeric types, the `+` operator computes the sum of its operands:</span></span>

[!code-csharp-interactive[numeric addition](~/samples/snippets/csharp/language-reference/operators/AdditionExamples.cs#AddNumerics)]

## <a name="string-concatenation"></a><span data-ttu-id="c2a8a-111">Zřetězení řetězců</span><span class="sxs-lookup"><span data-stu-id="c2a8a-111">String concatenation</span></span>

<span data-ttu-id="c2a8a-112">Když se jeden nebo oba operandy typu [řetězec](../keywords/string.md), `+` zřetězí řetězcové reprezentace jeho operandy operátoru:</span><span class="sxs-lookup"><span data-stu-id="c2a8a-112">When one or both operands are of type [string](../keywords/string.md), the `+` operator concatenates the string representations of its operands:</span></span>

[!code-csharp-interactive[string concatenation](~/samples/snippets/csharp/language-reference/operators/AdditionExamples.cs#AddStrings)]

<span data-ttu-id="c2a8a-113">Počínaje C# 6, [interpolace](../tokens/interpolated.md) poskytuje pohodlnější způsob, jak formátovací řetězce:</span><span class="sxs-lookup"><span data-stu-id="c2a8a-113">Starting with C# 6, [string interpolation](../tokens/interpolated.md) provides a more convenient way to format strings:</span></span>

[!code-csharp-interactive[string interpolation](~/samples/snippets/csharp/language-reference/operators/AdditionExamples.cs#UseStringInterpolation)]

## <a name="delegate-combination"></a><span data-ttu-id="c2a8a-114">Kombinaci delegátů</span><span class="sxs-lookup"><span data-stu-id="c2a8a-114">Delegate combination</span></span>

<span data-ttu-id="c2a8a-115">Pro [delegovat](../keywords/delegate.md) typy, `+` operátor vrátí novou instanci delegáta, která při vyvolání, vyvolá prvním operandem a poté vyvolá druhého operandu.</span><span class="sxs-lookup"><span data-stu-id="c2a8a-115">For [delegate](../keywords/delegate.md) types, the `+` operator returns a new delegate instance that, when invoked, invokes the first operand and then invokes the second operand.</span></span> <span data-ttu-id="c2a8a-116">Pokud kterýkoli z operandů `null`, `+` operátor vrátí hodnotu jiný operand (která může být také `null`).</span><span class="sxs-lookup"><span data-stu-id="c2a8a-116">If any of the operands is `null`, the `+` operator returns the value of another operand (which also might be `null`).</span></span> <span data-ttu-id="c2a8a-117">Následující příklad ukazuje, jak mohou být kombinovány delegáty s `+` operátor:</span><span class="sxs-lookup"><span data-stu-id="c2a8a-117">The following example shows how delegates can be combined with the `+` operator:</span></span>

[!code-csharp-interactive[delegate combination](~/samples/snippets/csharp/language-reference/operators/AdditionExamples.cs#AddDelegates)]

<span data-ttu-id="c2a8a-118">Další informace o typech delegáta, naleznete v tématu [delegáti](../../programming-guide/delegates/index.md).</span><span class="sxs-lookup"><span data-stu-id="c2a8a-118">For more information about delegate types, see [Delegates](../../programming-guide/delegates/index.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="c2a8a-119">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="c2a8a-119">C# language specification</span></span>

<span data-ttu-id="c2a8a-120">Další informace najdete v tématu [unární operátor plus](~/_csharplang/spec/expressions.md#unary-plus-operator) a [operátor sčítání](~/_csharplang/spec/expressions.md#addition-operator) oddíly [ C# specifikace jazyka](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="c2a8a-120">For more information, see the [Unary plus operator](~/_csharplang/spec/expressions.md#unary-plus-operator) and [Addition operator](~/_csharplang/spec/expressions.md#addition-operator) sections of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="c2a8a-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c2a8a-121">See also</span></span>

- [<span data-ttu-id="c2a8a-122">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="c2a8a-122">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="c2a8a-123">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="c2a8a-123">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="c2a8a-124">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="c2a8a-124">C# Operators</span></span>](index.md)
- [<span data-ttu-id="c2a8a-125">Interpolace řetězců</span><span class="sxs-lookup"><span data-stu-id="c2a8a-125">String interpolation</span></span>](../tokens/interpolated.md)
- [<span data-ttu-id="c2a8a-126">Postupy: Zřetězení více řetězců</span><span class="sxs-lookup"><span data-stu-id="c2a8a-126">How to: Concatenate Multiple Strings</span></span>](../../how-to/concatenate-multiple-strings.md)
- [<span data-ttu-id="c2a8a-127">Delegáti</span><span class="sxs-lookup"><span data-stu-id="c2a8a-127">Delegates</span></span>](../../programming-guide/delegates/index.md)
- [<span data-ttu-id="c2a8a-128">Zaškrtnuto a nezaškrtnuto</span><span class="sxs-lookup"><span data-stu-id="c2a8a-128">Checked and unchecked</span></span>](../keywords/checked-and-unchecked.md)
