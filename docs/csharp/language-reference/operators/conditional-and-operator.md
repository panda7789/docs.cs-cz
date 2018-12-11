---
title: '&amp;&amp; Operator - C# odkaz'
ms.custom: seodec18
ms.date: 11/06/2018
f1_keywords:
- '&&_CSharpKeyword'
helpviewer_keywords:
- '&& operator [C#]'
- logical AND operator [C#]
ms.assetid: 2e4f0a1c-92a3-40f8-8e3b-17b607f20c31
ms.openlocfilehash: 82442f50275f21e0a0748951dc50628a8d7e11bb
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53243581"
---
# <a name="ampamp-operator-c-reference"></a>&amp;&amp; – Operátor (referenční dokumentace jazyka C#)

Podmíněné logického operátoru AND `&&`, označované také jako "krátký cyklus" logického operátoru AND, vypočítá logický operátor AND z jeho [bool](../keywords/bool.md) operandy. Výsledek `x && y` je `true` Pokud mají oba `x` a `y` vyhodnotit `true`. V opačném případě je výsledek `false`. Pokud je první operand vyhodnocen jako `false`, druhý operand není vyhodnocen a výsledek operace `false`. Následující příklad ukazuje toto chování:

[!code-csharp-interactive[conditional logical AND](~/samples/snippets/csharp/language-reference/operators/ConditionalLogicalOperatorsExamples.cs#And)]

[Logického operátoru AND](and-operator.md) `&` také vypočítá logický operátor AND z jeho `bool` operandy, ale vždy vyhodnotí oba operandy.

## <a name="operator-overloadability"></a>Overloadability – operátor

Uživatelem definovaný typ nejde přetížit podmíněné logického operátoru AND. Ale pokud přetížení uživatelem definovaného typu [logický operátor AND](and-operator.md) a [operátory true a false](../keywords/true-false-operators.md) určitým způsobem, `&&` operace může být vyhodnocen pro operandy typu. Další informace najdete v tématu [podmíněné logické operátory definované uživatelem](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) část [ C# specifikace jazyka](../language-specification/index.md).

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace najdete v tématu [podmíněné logické operátory](~/_csharplang/spec/expressions.md#conditional-logical-operators) část [ C# specifikace jazyka](../language-specification/index.md).

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka C#](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [Operátory jazyka C#](index.md)
- [|| – operátor](conditional-or-operator.md)
- [\! – operátor](logical-negation-operator.md)
- [& – operátor](and-operator.md)
