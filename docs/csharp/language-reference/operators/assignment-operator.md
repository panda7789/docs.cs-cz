---
title: = – operátor - C# odkaz
ms.custom: seodec18
ms.date: 06/21/2019
f1_keywords:
- =_CSharpKeyword
helpviewer_keywords:
- = operator [C#]
ms.assetid: d802a6d5-32f0-42b8-b180-12f5a081bfc1
ms.openlocfilehash: 1277b35723777760deebb6606ddc90bd21e654ec
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67744114"
---
# <a name="-operator-c-reference"></a>= – operátor (C# odkaz)

Operátor přiřazení `=` hodnota jeho operandu pravé přiřadí proměnné, [vlastnost](../../programming-guide/classes-and-structs/properties.md), nebo [indexer](../../../csharp/programming-guide/indexers/index.md) element Dal jeho levý operand. Výsledkem výrazu přiřazení je hodnota přiřazená k levý operand. Typ operandu pravé musí být stejný jako typ levý operand nebo implicitně převeditelné na ni.

Operátor přiřazení je asociativní zprava, to znamená, výraz ve tvaru

```csharp
a = b = c
```

je vyhodnocen jako

```csharp
a = (b = c)
```

Následující příklad ukazuje použití operátoru přiřazení s místní proměnná, vlastnost a indexer elementu jako jeho operand na levé straně:

[!code-csharp-interactive[simple assignment](~/samples/csharp/language-reference/operators/AssignmentOperator.cs#Simple)]

## <a name="ref-assignment-operator"></a>operátoru přiřazení odkazu

Počínaje C# 7.3, můžete pomocí operátoru přiřazení odkazu `= ref` přiřazení [lokální proměnná podle odkazu](../keywords/ref.md#ref-locals) nebo [lokální proměnná podle odkazu jen pro čtení](../keywords/ref.md#ref-readonly-locals) proměnné. Následující příklad ukazuje použití operátoru přiřazení odkazu:

[!code-csharp[ref assignment operator](~/samples/csharp/language-reference/operators/AssignmentOperator.cs#RefAssignment)]

V případě operátoru přiřazení odkazu typ i jeho operandy musí být stejné.

Další informace najdete v tématu [Poznámka návrh funkce](~/_csharplang/proposals/csharp-7.3/ref-local-reassignment.md).

## <a name="compound-assignment"></a>Složené přiřazení

Pro binární operátor `op`, výraz složeného přiřazení formuláře

```csharp
x op= y
```

je ekvivalentem

```csharp
x = x op y
```

s tím rozdílem, že `x` se jenom vyhodnotí jednou.

Složené přiřazení podporuje [aritmetické](arithmetic-operators.md#compound-assignment), [logický datový typ Boolean](boolean-logical-operators.md#compound-assignment), a [bitové logické a shift](bitwise-and-shift-operators.md#compound-assignment) operátory.

## <a name="operator-overloadability"></a>Overloadability – operátor

Uživatelem definovaný typ nejde přetížit operátor přiřazení. Uživatelem definovaný typ však můžete definovat implicitní převod na jiného typu. Tímto způsobem hodnota uživatelem definovaného typu lze přiřadit k proměnné, vlastnosti nebo elementu indexeru jiného typu. Další informace najdete v tématu [uživatelsky definovaný převod operátorů](user-defined-conversion-operators.md).

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace najdete v tématu [operátory přiřazení](~/_csharplang/spec/expressions.md#assignment-operators) část [ C# specifikace jazyka](../language-specification/index.md).

## <a name="see-also"></a>Viz také:

- [C#referenční dokumentace](../index.md)
- [Operátory jazyka C#](index.md)
- [ref keyword](../keywords/ref.md)
