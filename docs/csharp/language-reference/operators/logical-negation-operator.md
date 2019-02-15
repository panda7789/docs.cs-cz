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
# <a name="-operator-c-reference"></a>! operator (Referenční dokumentace jazyka C#)

Operátor logické negace `!` je unární operátor, který vypočítává Logická negace z jeho [bool](../keywords/bool.md) operand. To znamená, vytvoří `true`, je-li operand `false`, a `false`, je-li operand `true`:

[!code-csharp-interactive[logical negation](~/samples/snippets/csharp/language-reference/operators/LogicalNegationExamples.cs#Example)]

## <a name="operator-overloadability"></a>Overloadability – operátor

Uživatelem definované typy lze [přetížení](../keywords/operator.md) `!` operátor.

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace najdete v tématu [logický operátor negace](~/_csharplang/spec/expressions.md#logical-negation-operator) část [ C# specifikace jazyka](../language-specification/index.md).

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka C#](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [Operátory jazyka C#](index.md)