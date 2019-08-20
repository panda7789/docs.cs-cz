---
title: = – odkaz C# – operátor
ms.custom: seodec18
ms.date: 06/21/2019
f1_keywords:
- =_CSharpKeyword
helpviewer_keywords:
- = operator [C#]
ms.assetid: d802a6d5-32f0-42b8-b180-12f5a081bfc1
ms.openlocfilehash: f30b48fc6bd1e896658a7234a58409ea9a0f5e6f
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69601952"
---
# <a name="-operator-c-reference"></a>= – operátorC# (Referenční dokumentace)

Operátor `=` přiřazení přiřadí hodnotu jeho pravého operandu proměnné, [vlastnosti](../../programming-guide/classes-and-structs/properties.md)nebo prvku indexeru, který je dán [](../../programming-guide/indexers/index.md) jeho levým operandem. Výsledkem výrazu přiřazení je hodnota přiřazená k levému operandu. Typ operandu na pravé straně musí být stejný jako typ operandu na levé straně nebo implicitně převést na něj.

Operátor přiřazení je asociativní zprava, tj. výraz formuláře.

```csharp
a = b = c
```

je vyhodnocen jako

```csharp
a = (b = c)
```

Následující příklad ukazuje použití operátoru přiřazení s lokální proměnnou, vlastností a prvkem indexeru jako jeho levý operand:

[!code-csharp-interactive[simple assignment](~/samples/csharp/language-reference/operators/AssignmentOperator.cs#Simple)]

## <a name="ref-assignment-operator"></a>operátor přiřazení ref

Počínaje C# 7,3 můžete použít operátor `= ref` přiřazení ref k opětovnému přiřazení místní proměnné typu [ref](../keywords/ref.md#ref-locals) nebo [ref jen pro čtení](../keywords/ref.md#ref-readonly-locals) . Následující příklad ukazuje použití operátoru přiřazení ref:

[!code-csharp[ref assignment operator](~/samples/csharp/language-reference/operators/AssignmentOperator.cs#RefAssignment)]

V případě operátoru přiřazení ref musí být typ obou operandů stejný.

Další informace najdete v poznámkách k [návrhu funkcí](~/_csharplang/proposals/csharp-7.3/ref-local-reassignment.md).

## <a name="compound-assignment"></a>Složené přiřazení

Pro binární operátor `op`, výraz složeného přiřazení formuláře

```csharp
x op= y
```

je ekvivalentem

```csharp
x = x op y
```

s výjimkou, že `x` je vyhodnocena pouze jednou.

Složené přiřazení je podporováno [aritmetickými](arithmetic-operators.md#compound-assignment)a [](boolean-logical-operators.md#compound-assignment)logickými logickými a operátory [SHIFT a Shift](bitwise-and-shift-operators.md#compound-assignment) .

## <a name="operator-overloadability"></a>Přetížení operátoru

Uživatelsky definovaný typ nemůže přetížit operátor přiřazení. Uživatelsky definovaný typ však může definovat implicitní převod na jiný typ. Tímto způsobem lze hodnotu uživatelsky definovaného typu přiřadit proměnné, vlastnosti nebo prvku indexeru jiného typu. Další informace naleznete v tématu [uživatelsky definované operátory převodu](user-defined-conversion-operators.md).

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace naleznete v části [operátory přiřazení](~/_csharplang/spec/expressions.md#assignment-operators) ve [ C# specifikaci jazyka](../language-specification/index.md).

## <a name="see-also"></a>Viz také:

- [C#odkaz](../index.md)
- [Operátory jazyka C#](index.md)
- [ref – klíčové slovo](../keywords/ref.md)
