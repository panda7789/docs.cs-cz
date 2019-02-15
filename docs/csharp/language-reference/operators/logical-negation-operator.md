---
title: '! Operator - C# odkaz'
ms.custom: seodec18
ms.date: 02/14/2019
f1_keywords:
- '!_CSharpKeyword'
helpviewer_keywords:
- '! operator [C#]'
- logical negation operator (!) [C#]
- NOT operator [C#]
ms.assetid: f5ae133f-8f64-4560-b34f-cd9cd5eed4ad
ms.openlocfilehash: 464bd658c9bf430191d84d3d5ad8d57173ab87c5
ms.sourcegitcommit: bef803e2025642df39f2f1e046767d89031e0304
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/15/2019
ms.locfileid: "56303709"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="0db52-103">!</span><span class="sxs-lookup"><span data-stu-id="0db52-103">!</span></span> <span data-ttu-id="0db52-104">operator (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="0db52-104">operator (C# Reference)</span></span>

<span data-ttu-id="0db52-105">Operátor logické negace `!` je unární operátor, který vypočítává Logická negace z jeho [bool](../keywords/bool.md) operand.</span><span class="sxs-lookup"><span data-stu-id="0db52-105">The logical negation operator `!` is a unary operator that computes logical negation of its [bool](../keywords/bool.md) operand.</span></span> <span data-ttu-id="0db52-106">To znamená, vytvoří `true`, je-li operand `false`, a `false`, je-li operand `true`:</span><span class="sxs-lookup"><span data-stu-id="0db52-106">That is, it produces `true`, if the operand is `false`, and `false`, if the operand is `true`:</span></span>

[!code-csharp-interactive[logical negation](~/samples/snippets/csharp/language-reference/operators/LogicalNegationExamples.cs#Example)]

## <a name="operator-overloadability"></a><span data-ttu-id="0db52-107">Overloadability – operátor</span><span class="sxs-lookup"><span data-stu-id="0db52-107">Operator overloadability</span></span>

<span data-ttu-id="0db52-108">Uživatelem definované typy lze [přetížení](../keywords/operator.md) `!` operátor.</span><span class="sxs-lookup"><span data-stu-id="0db52-108">User-defined types can [overload](../keywords/operator.md) the `!` operator.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="0db52-109">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="0db52-109">C# language specification</span></span>

<span data-ttu-id="0db52-110">Další informace najdete v tématu [logický operátor negace](~/_csharplang/spec/expressions.md#logical-negation-operator) část [ C# specifikace jazyka](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="0db52-110">For more information, see the [Logical negation operator](~/_csharplang/spec/expressions.md#logical-negation-operator) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="0db52-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0db52-111">See also</span></span>

- [<span data-ttu-id="0db52-112">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="0db52-112">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="0db52-113">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="0db52-113">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="0db52-114">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="0db52-114">C# Operators</span></span>](index.md)