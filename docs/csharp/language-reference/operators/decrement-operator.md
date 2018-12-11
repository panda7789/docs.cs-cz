---
title: --– Operátor - C# odkaz
ms.custom: seodec18
ms.date: 11/26/2018
f1_keywords:
- --_CSharpKeyword
helpviewer_keywords:
- -- operator [C#]
- decrement operator (--) [C#]
ms.assetid: 6b9cfe86-63c7-421f-9379-c9690fea8720
ms.openlocfilehash: 4fba014e8dabc13cd874e17f23515dc29d93f24b
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53236918"
---
# <a name="---operator-c-reference"></a><span data-ttu-id="2a7a3-102">-- – operátor (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="2a7a3-102">-- Operator (C# Reference)</span></span>

<span data-ttu-id="2a7a3-103">Unární operátor dekrementace `--` sníží svého operandu o 1.</span><span class="sxs-lookup"><span data-stu-id="2a7a3-103">The unary decrement operator `--` decrements its operand by 1.</span></span> <span data-ttu-id="2a7a3-104">Je podporován ve dvou formách: příponového operátoru dekrementace `x--`a operátor dekrementace předpony `--x`.</span><span class="sxs-lookup"><span data-stu-id="2a7a3-104">It's supported in two forms: the postfix decrement operator, `x--`, and the prefix decrement operator, `--x`.</span></span>

## <a name="postfix-decrement-operator"></a><span data-ttu-id="2a7a3-105">Příponový operátor dekrementace</span><span class="sxs-lookup"><span data-stu-id="2a7a3-105">Postfix decrement operator</span></span>

<span data-ttu-id="2a7a3-106">Výsledek `x--` je hodnota `x` *před* operace, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="2a7a3-106">The result of `x--` is the value of `x` *before* the operation, as the following example shows:</span></span>

[!code-csharp-interactive[postfix decrement](~/samples/snippets/csharp/language-reference/operators/DecrementAndIncrementExamples.cs#PostfixDecrement)]

## <a name="prefix-decrement-operator"></a><span data-ttu-id="2a7a3-107">Operátor dekrementace předpony</span><span class="sxs-lookup"><span data-stu-id="2a7a3-107">Prefix decrement operator</span></span>

<span data-ttu-id="2a7a3-108">Výsledek `--x` je hodnota `x` *po* operace, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="2a7a3-108">The result of `--x` is the value of `x` *after* the operation, as the following example shows:</span></span>

[!code-csharp-interactive[prefix decrement](~/samples/snippets/csharp/language-reference/operators/DecrementAndIncrementExamples.cs#PrefixDecrement)]

## <a name="remarks"></a><span data-ttu-id="2a7a3-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2a7a3-109">Remarks</span></span>

<span data-ttu-id="2a7a3-110">Operátor dekrementace je předdefinovaný pro všechny [celočíselných typů](../keywords/integral-types-table.md) (včetně [char](../keywords/char.md) typu), [typy s plovoucí desetinnou čárkou](../keywords/floating-point-types-table.md)a jakékoli [výčtu](../keywords/enum.md) Zadejte.</span><span class="sxs-lookup"><span data-stu-id="2a7a3-110">The decrement operator is predefined for all [integral types](../keywords/integral-types-table.md) (including the [char](../keywords/char.md) type), [floating-point types](../keywords/floating-point-types-table.md), and any [enum](../keywords/enum.md) type.</span></span>

<span data-ttu-id="2a7a3-111">Operand operátoru dekrementace musí být proměnná, [vlastnost](../../programming-guide/classes-and-structs/properties.md) přístup, nebo [indexer](../../../csharp/programming-guide/indexers/index.md) přístup.</span><span class="sxs-lookup"><span data-stu-id="2a7a3-111">An operand of the decrement operator must be a variable, a [property](../../programming-guide/classes-and-structs/properties.md) access, or an [indexer](../../../csharp/programming-guide/indexers/index.md) access.</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="2a7a3-112">Overloadability – operátor</span><span class="sxs-lookup"><span data-stu-id="2a7a3-112">Operator overloadability</span></span>

<span data-ttu-id="2a7a3-113">Uživatelem definované typy lze [přetížení](../keywords/operator.md) `--` operátor.</span><span class="sxs-lookup"><span data-stu-id="2a7a3-113">User-defined types can [overload](../keywords/operator.md) the `--` operator.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="2a7a3-114">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="2a7a3-114">C# language specification</span></span>

<span data-ttu-id="2a7a3-115">Další informace najdete v tématu [Příponové operátory Inkrementace a dekrementace operátory](~/_csharplang/spec/expressions.md#postfix-increment-and-decrement-operators) a [předpony Inkrementace a dekrementace operátory](~/_csharplang/spec/expressions.md#prefix-increment-and-decrement-operators) oddíly [ C# specifikace jazyka](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="2a7a3-115">For more information, see the [Postfix increment and decrement operators](~/_csharplang/spec/expressions.md#postfix-increment-and-decrement-operators) and [Prefix increment and decrement operators](~/_csharplang/spec/expressions.md#prefix-increment-and-decrement-operators) sections of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="2a7a3-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2a7a3-116">See also</span></span>

- [<span data-ttu-id="2a7a3-117">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="2a7a3-117">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="2a7a3-118">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="2a7a3-118">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="2a7a3-119">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="2a7a3-119">C# Operators</span></span>](index.md)
- [<span data-ttu-id="2a7a3-120">++ – operátor</span><span class="sxs-lookup"><span data-stu-id="2a7a3-120">++ Operator</span></span>](increment-operator.md)
- [<span data-ttu-id="2a7a3-121">Postupy: přírůstek a úbytek ukazatelů</span><span class="sxs-lookup"><span data-stu-id="2a7a3-121">How to: increment and decrement pointers</span></span>](../../programming-guide/unsafe-code-pointers/how-to-increment-and-decrement-pointers.md)
