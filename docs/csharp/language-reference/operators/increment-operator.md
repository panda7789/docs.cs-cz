---
title: ++ – operátor (Referenční dokumentace jazyka C#)
ms.date: 11/26/2018
f1_keywords:
- ++_CSharpKeyword
helpviewer_keywords:
- increment operator (++) [C#]
- ++ operator [C#]
ms.assetid: e9dec353-070b-44fb-98ed-eb8fdf753feb
ms.openlocfilehash: b29f4f1ab00c0f8026f118cb72b090e3b728bfc5
ms.sourcegitcommit: 6ae7cdd0437a32884556dd4826ca90e957b7a4e3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/06/2018
ms.locfileid: "48030467"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="cc7ab-102">++ – operátor (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="cc7ab-102">++ Operator (C# Reference)</span></span>

<span data-ttu-id="cc7ab-103">Unární operátor Inkrementace `++` svého operandu zvýší o hodnotu 1.</span><span class="sxs-lookup"><span data-stu-id="cc7ab-103">The unary increment operator `++` increments its operand by 1.</span></span> <span data-ttu-id="cc7ab-104">Je podporován ve dvou formách: příponového operátoru Inkrementace `x++`a prefixový operátor Inkrementace `++x`.</span><span class="sxs-lookup"><span data-stu-id="cc7ab-104">It's supported in two forms: the postfix increment operator, `x++`, and the prefix increment operator, `++x`.</span></span>

## <a name="postfix-increment-operator"></a><span data-ttu-id="cc7ab-105">Příponový operátor inkrementace</span><span class="sxs-lookup"><span data-stu-id="cc7ab-105">Postfix increment operator</span></span>

<span data-ttu-id="cc7ab-106">Výsledek `x++` je hodnota `x` *před* operace, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="cc7ab-106">The result of `x++` is the value of `x` *before* the operation, as the following example shows:</span></span>

[!code-csharp-interactive[postfix increment](~/samples/snippets/csharp/language-reference/operators/DecrementAndIncrementExamples.cs#PostfixIncrement)]

## <a name="prefix-increment-operator"></a><span data-ttu-id="cc7ab-107">Prefixový operátor Inkrementace</span><span class="sxs-lookup"><span data-stu-id="cc7ab-107">Prefix increment operator</span></span>

<span data-ttu-id="cc7ab-108">Výsledek `++x` je hodnota `x` *po* operace, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="cc7ab-108">The result of `++x` is the value of `x` *after* the operation, as the following example shows:</span></span>

[!code-csharp-interactive[prefix increment](~/samples/snippets/csharp/language-reference/operators/DecrementAndIncrementExamples.cs#PrefixIncrement)]

## <a name="remarks"></a><span data-ttu-id="cc7ab-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="cc7ab-109">Remarks</span></span>

<span data-ttu-id="cc7ab-110">Operátor Inkrementace je předdefinovaný pro všechny [celočíselných typů](../keywords/integral-types-table.md) (včetně [char](../keywords/char.md) typu), [typy s plovoucí desetinnou čárkou](../keywords/floating-point-types-table.md)a jakékoli [výčtu](../keywords/enum.md) Zadejte.</span><span class="sxs-lookup"><span data-stu-id="cc7ab-110">The increment operator is predefined for all [integral types](../keywords/integral-types-table.md) (including the [char](../keywords/char.md) type), [floating-point types](../keywords/floating-point-types-table.md), and any [enum](../keywords/enum.md) type.</span></span>

<span data-ttu-id="cc7ab-111">Operand operátoru Inkrementace musí být proměnná, [vlastnost](../../programming-guide/classes-and-structs/properties.md) přístup, nebo [indexer](../../../csharp/programming-guide/indexers/index.md) přístup.</span><span class="sxs-lookup"><span data-stu-id="cc7ab-111">An operand of the increment operator must be a variable, a [property](../../programming-guide/classes-and-structs/properties.md) access, or an [indexer](../../../csharp/programming-guide/indexers/index.md) access.</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="cc7ab-112">Overloadability – operátor</span><span class="sxs-lookup"><span data-stu-id="cc7ab-112">Operator overloadability</span></span>

<span data-ttu-id="cc7ab-113">Uživatelem definované typy lze [přetížení](../keywords/operator.md) `++` operátor.</span><span class="sxs-lookup"><span data-stu-id="cc7ab-113">User-defined types can [overload](../keywords/operator.md) the `++` operator.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="cc7ab-114">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="cc7ab-114">C# language specification</span></span>

<span data-ttu-id="cc7ab-115">Další informace najdete v tématu [Příponové operátory Inkrementace a dekrementace operátory](~/_csharplang/spec/expressions.md#postfix-increment-and-decrement-operators) a [předpony Inkrementace a dekrementace operátory](~/_csharplang/spec/expressions.md#prefix-increment-and-decrement-operators) oddíly [ C# specifikace jazyka](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="cc7ab-115">For more information, see the [Postfix increment and decrement operators](~/_csharplang/spec/expressions.md#postfix-increment-and-decrement-operators) and [Prefix increment and decrement operators](~/_csharplang/spec/expressions.md#prefix-increment-and-decrement-operators) sections of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="cc7ab-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cc7ab-116">See also</span></span>

- [<span data-ttu-id="cc7ab-117">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="cc7ab-117">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="cc7ab-118">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="cc7ab-118">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="cc7ab-119">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="cc7ab-119">C# Operators</span></span>](index.md)
- [<span data-ttu-id="cc7ab-120">-- – operátor</span><span class="sxs-lookup"><span data-stu-id="cc7ab-120">-- Operator</span></span>](decrement-operator.md)
- [<span data-ttu-id="cc7ab-121">Postupy: přírůstek a úbytek ukazatelů</span><span class="sxs-lookup"><span data-stu-id="cc7ab-121">How to: increment and decrement pointers</span></span>](../../programming-guide/unsafe-code-pointers/how-to-increment-and-decrement-pointers.md)
