---
title: '&amp;= – Operátor - C# odkaz'
ms.custom: seodec18
ms.date: 10/29/2018
f1_keywords:
- '&=_CSharpKeyword'
helpviewer_keywords:
- AND assignment operator (&=) [C#]
- '&= operator [C#]'
ms.assetid: e8d58f3f-72dd-4b5a-b995-452fcce7e6bb
ms.openlocfilehash: 223d2f30ee77457e1f9d5304ec299517932499d0
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53237022"
---
# <a name="amp-operator-c-reference"></a>&amp;= – Operátor (referenční dokumentace jazyka C#)

Operátor přiřazení AND.

Pomocí výrazu `&=` operátorů, například

```csharp
x &= y
```

je ekvivalentem

```csharp
x = x & y
```

s tím rozdílem, že `x` se jenom vyhodnotí jednou.

Pro celočíselné operandy [ `&` operátor](and-operator.md) vypočítá bitové logické AND operandů; pro [bool](../keywords/bool.md) operandy, vypočítá logický operátor AND operandů.

Následující příklad ukazuje použití `&=` operátor:

[!code-csharp-interactive[AND assignment example](~/samples/snippets/csharp/language-reference/operators/AndOperatorExamples.cs#AndAssignmentExample)]

## <a name="operator-overloadability"></a>Overloadability – operátor

Pokud uživatelem definovaného typu [přetížení](../keywords/operator.md) [ `&` operátor](and-operator.md), operátor přiřazení AND `&=` je implicitně přetížena. Uživatelem definovaný typ nejde explicitně přetížit operátor přiřazení AND.

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace najdete v tématu [složené přiřazení](~/_csharplang/spec/expressions.md#compound-assignment) část [ C# specifikace jazyka](../language-specification/index.md).

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka C#](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [Operátory jazyka C#](index.md)
