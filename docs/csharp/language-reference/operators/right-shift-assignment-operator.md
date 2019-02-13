---
title: '>>= – operátor - C# odkaz'
ms.custom: seodec18
ms.date: 02/12/2019
f1_keywords:
- '>>=_CSharpKeyword'
helpviewer_keywords:
- right shift assignment operator (>>=) [C#]
- '>>= operator (right-shift assignment) [C#]'
ms.assetid: b593778c-b9b4-440d-8b29-c1ac22cb81c0
ms.openlocfilehash: 51914bb5e9ebffd5d868528b5a8d3072a956cea6
ms.sourcegitcommit: 30e2fe5cc4165aa6dde7218ec80a13def3255e98
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/13/2019
ms.locfileid: "56220910"
---
# <a name="-operator-c-reference"></a>>> = – operátor (C# odkaz)

Operátor přiřazení posunutí doprava.

Pomocí výrazu `>>=` operátorů, například

```csharp
x >>= y
```

je ekvivalentem

```csharp
x = x >> y
```

s tím rozdílem, že `x` se jenom vyhodnotí jednou.

[ `>>` Operátor](right-shift-operator.md) posune jeho prvního operandu vpravo počet bitů, které jsou určené svým druhým operandem.

Následující příklad ukazuje použití `>>=` operátor:

[!code-csharp-interactive[right shift assignment](~/samples/snippets/csharp/language-reference/operators/ShiftOperatorsExamples.cs#RightShiftAssignment)]

## <a name="operator-overloadability"></a>Overloadability – operátor

Pokud uživatelem definovaného typu [přetížení](../keywords/operator.md) [ `>>` operátor](right-shift-operator.md), operátor přiřazení posunutí doprava `>>=` je implicitně přetížena. Uživatelem definovaný typ nejde explicitně přetížit operátor přiřazení posunutí doprava.

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace najdete v tématu [složené přiřazení](~/_csharplang/spec/expressions.md#compound-assignment) část [ C# specifikace jazyka](../language-specification/index.md).

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka C#](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [C#operátory](index.md)