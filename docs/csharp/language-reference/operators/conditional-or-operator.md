---
title: '|| Operator - C# odkaz'
ms.custom: seodec18
ms.date: 11/06/2018
f1_keywords:
- '||_CSharpKeyword'
helpviewer_keywords:
- logical OR operator [C#]
- conditional-OR operator (||) [C#]
- '|| operator [C#]'
ms.assetid: 7d442d8e-400d-421f-b4d2-034bf82bcbdc
ms.openlocfilehash: 079c021eb68ece097c7f644416f1e9469a82dcea
ms.sourcegitcommit: b56d59ad42140d277f2acbd003b74d655fdbc9f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2019
ms.locfileid: "54415426"
---
# <a name="-operator-c-reference"></a>|| – operátor (Referenční dokumentace jazyka C#)

Podmíněné logického operátoru OR `||`, označované také jako "krátký cyklus" logického operátoru OR, vypočítá logický operátor OR z jeho [bool](../keywords/bool.md) operandy. Výsledek `x || y` je `true` Pokud `x` nebo `y` vyhodnotí jako `true`. V opačném případě je výsledek `false`. Pokud je první operand vyhodnocen jako `true`, druhý operand není vyhodnocen a výsledek operace `true`. Následující příklad ukazuje toto chování:

[!code-csharp-interactive[conditional logical OR](~/samples/snippets/csharp/language-reference/operators/ConditionalLogicalOperatorsExamples.cs#Or)]

[Logického operátoru OR](or-operator.md) `|` také vypočítá logický operátor OR z jeho `bool` operandy, ale vždy vyhodnotí oba operandy.

## <a name="operator-overloadability"></a>Overloadability – operátor

Uživatelem definovaný typ nejde přetížit podmíněné logický operátor OR. Ale pokud přetížení uživatelem definovaného typu [logický operátor OR](or-operator.md) a [operátory true a false](../keywords/true-false-operators.md) určitým způsobem, `||` operace může být vyhodnocen pro operandy typu. Další informace najdete v tématu [podmíněné logické operátory definované uživatelem](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) část [ C# specifikace jazyka](../language-specification/index.md).

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace najdete v tématu [podmíněné logické operátory](~/_csharplang/spec/expressions.md#conditional-logical-operators) část [ C# specifikace jazyka](../language-specification/index.md).

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka C#](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [Operátory jazyka C#](index.md)
- [& & – operátor](conditional-and-operator.md)
- [\! – Operátor](logical-negation-operator.md)
- [| – operátor](or-operator.md)
