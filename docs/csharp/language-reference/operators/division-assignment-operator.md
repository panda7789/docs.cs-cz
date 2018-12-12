---
title: / = – Operátor - C# odkaz
ms.custom: seodec18
ms.date: 12/13/2018
f1_keywords:
- /=_CSharpKeyword
helpviewer_keywords:
- division assignment operator (/=) [C#]
- /= (division assignment operator) [C#]
ms.assetid: 50fc02b0-ee9c-4c3e-b58d-d591282caf1c
ms.openlocfilehash: ed4dd6c0c944b77543aae4de8d51534b4df4f4ef
ms.sourcegitcommit: d6e419f9d9cd7e8f21ebf5acde6d016c16332579
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/12/2018
ms.locfileid: "53286517"
---
# <a name="-operator-c-reference"></a>/= – operátor (Referenční dokumentace jazyka C#)

Operátor přiřazení dělení.

Pomocí výrazu `/=` operátorů, například

```csharp
x /= y
```

je ekvivalentem

```csharp
x = x / y
```

s tím rozdílem, že `x` se jenom vyhodnotí jednou.

[Operátor dělení](division-operator.md) `/` rozděluje svůj první operand tak svým druhým operandem. Podporuje všechny číselné typy.

Následující příklad ukazuje použití `/=` operátor:

[!code-csharp-interactive[divide and assign](~/samples/snippets/csharp/language-reference/operators/DivisionExamples.cs#DivisionAssignment)]

## <a name="operator-overloadability"></a>Overloadability – operátor

Pokud uživatelský typ [přetížení](../keywords/operator.md) [operátor dělení](division-operator.md) `/`, operátor přiřazení dělení `/=` je implicitně přetížena. Uživatelem definovaný typ nejde explicitně přetížit operátor přiřazení dělení.

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace najdete v tématu [složené přiřazení](~/_csharplang/spec/expressions.md#compound-assignment) část [ C# specifikace jazyka](../language-specification/index.md).

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka C#](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [Operátory jazyka C#](index.md)
