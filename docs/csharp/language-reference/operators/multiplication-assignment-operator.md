---
title: '* = – Operátor - C# odkaz'
ms.custom: seodec18
ms.date: 02/26/2019
f1_keywords:
- '*=_CSharpKeyword'
helpviewer_keywords:
- '*= operator [C#]'
- binary multiplication assignment operator (*=) [C#]
ms.assetid: 2e472155-59db-4dbf-bb94-bcccfa1a794d
ms.openlocfilehash: 70461f79e714e44354fe4137e5360769fa048d3e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61689603"
---
# <a name="-operator-c-reference"></a>\*= – Operátor (referenční dokumentace jazyka C#)

Operátor přiřazení násobení.

Pomocí výrazu `*=` operátorů, například

```csharp
x *= y
```

je ekvivalentem

```csharp
x = x * y
```

s tím rozdílem, že `x` se jenom vyhodnotí jednou.

Pro číselné typy [ \* operátor](multiplication-operator.md) vypočítá součin z operandů.

Následující příklad ukazuje použití `*=` operátor:

[!code-csharp-interactive[multiply and assign](~/samples/snippets/csharp/language-reference/operators/MultiplicationExamples.cs#MultiplyAndAssign)]

## <a name="operator-overloadability"></a>Overloadability – operátor

Pokud uživatelský typ [přetížení](../keywords/operator.md) [operátor násobení](multiplication-operator.md) `*`, operátor přiřazení násobení `*=` je implicitně přetížena. Uživatelem definovaný typ nejde explicitně přetížit operátor přiřazení násobení.

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace najdete v tématu [složené přiřazení](~/_csharplang/spec/expressions.md#compound-assignment) část [ C# specifikace jazyka](../language-specification/index.md).

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka C#](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [Operátory jazyka C#](index.md)
