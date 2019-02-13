---
title: << = – operátor - C# odkaz
ms.custom: seodec18
ms.date: 02/12/2019
f1_keywords:
- <<=_CSharpKeyword
helpviewer_keywords:
- <<= operator (left-shift assignment) [C#]
- left shift assignment operator (<<=) [C#]
ms.assetid: 3bc99c78-1edb-4827-86fc-bce6c3048871
ms.openlocfilehash: d2105fbee4ddfe1b2cb3325d82b0f2f8c5559297
ms.sourcegitcommit: 30e2fe5cc4165aa6dde7218ec80a13def3255e98
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/13/2019
ms.locfileid: "56219446"
---
# <a name="-operator-c-reference"></a>\<\<= – operátor (C# odkaz)

Operátor přiřazení posunutí doleva.

Pomocí výrazu `<<=` operátorů, například

```csharp
x <<= y
```

je ekvivalentem

```csharp
x = x << y
```

s tím rozdílem, že `x` se jenom vyhodnotí jednou.

[ `<<` Operátor](left-shift-operator.md) staffhubu svůj první operand doleva o počet bitů, které jsou určené svým druhým operandem.

Následující příklad ukazuje použití `<<=` operátor:

[!code-csharp-interactive[left shift assignment](~/samples/snippets/csharp/language-reference/operators/ShiftOperatorsExamples.cs#LeftShiftAssignment)]

## <a name="operator-overloadability"></a>Overloadability – operátor

Pokud uživatelem definovaného typu [přetížení](../keywords/operator.md) [ `<<` operátor](left-shift-operator.md), operátor přiřazení posunutí doleva `<<=` je implicitně přetížena. Uživatelem definovaný typ nejde explicitně přetížit operátor přiřazení posunutí doleva.

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace najdete v tématu [složené přiřazení](~/_csharplang/spec/expressions.md#compound-assignment) část [ C# specifikace jazyka](../language-specification/index.md).

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka C#](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [Operátory jazyka C#](index.md)
