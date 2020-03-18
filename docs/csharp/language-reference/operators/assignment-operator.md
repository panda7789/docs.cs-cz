---
title: Operátory přiřazení – odkaz jazyka C#
ms.date: 09/10/2019
f1_keywords:
- =_CSharpKeyword
helpviewer_keywords:
- = operator [C#]
ms.assetid: d802a6d5-32f0-42b8-b180-12f5a081bfc1
ms.openlocfilehash: 420b41f586a6980d40cf1171eef00dad37bf5abf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399250"
---
# <a name="assignment-operators-c-reference"></a>Operátory přiřazení (odkaz C# )

Operátor `=` přiřazení přiřadí hodnotu svého pravostranného operandu proměnné, [vlastnosti](../../programming-guide/classes-and-structs/properties.md)nebo prvku [indexeru](../../programming-guide/indexers/index.md) daného jeho levostranným operandem. Výsledkem výrazu přiřazení je hodnota přiřazená levostranné operaci. Typ pravostranného operandu musí být stejný jako typ levého operandu nebo k němu implicitně převoditelný.

Operátor `=` přiřazení je právo-asociativní, to znamená výraz formuláře

```csharp
a = b = c
```

je vyhodnocována jako

```csharp
a = (b = c)
```

Následující příklad ukazuje použití operátoru přiřazení s místní proměnnou, vlastností a indexerovým prvkem jako jeho levostranným operandem:

[!code-csharp-interactive[simple assignment](snippets/AssignmentOperator.cs#Simple)]

## <a name="ref-assignment-operator"></a>operátor přiřazení ref

Počínaje C# 7.3, můžete použít operátor `= ref` přiřazení ref znovu přiřadit [ref místní](../keywords/ref.md#ref-locals) nebo [ref pouze místní](../keywords/ref.md#ref-readonly-locals) proměnné. Následující příklad ukazuje použití operátoru přiřazení ref:

[!code-csharp[ref assignment operator](snippets/AssignmentOperator.cs#RefAssignment)]

V případě operátoru přiřazení ref musí být oba jeho operandy stejného typu.

## <a name="compound-assignment"></a>Složené přiřazení

Pro binární `op`operátor , složený výraz přiřazení formuláře

```csharp
x op= y
```

je ekvivalentem

```csharp
x = x op y
```

kromě `x` toho, že se vyhodnocuje pouze jednou.

Složené přiřazení je podporováno [aritmetickými](arithmetic-operators.md#compound-assignment), [logickými logickými](boolean-logical-operators.md#compound-assignment)a [bitovými logickými operátory a operátory směn.](bitwise-and-shift-operators.md#compound-assignment)

## <a name="null-coalescing-assignment"></a>Přiřazení null-coalescing

Počínaje C# 8.0, můžete použít null-coalescing `??=` přiřazení operátor přiřadit hodnotu jeho pravé operand u jeho levé operand pouze v `null`případě, že levé operandu vyhodnotí . Pro více informací, viz [?? a ?? = článek operátorů.](null-coalescing-operator.md)

## <a name="operator-overloadability"></a>Přetížení obsluhy

Uživatelem definovaný typ nemůže [přetížit](operator-overloading.md) operátor přiřazení. Typ definovaný uživatelem však může definovat implicitní převod na jiný typ. Tímto způsobem lze hodnotu uživatelem definovaného typu přiřadit proměnné, vlastnosti nebo prvku indexeru jiného typu. Další informace naleznete v [tématu User-defined operátory převodu](user-defined-conversion-operators.md).

Uživatelem definovaný typ nemůže explicitně přetížit operátor složeného přiřazení. Však pokud uživatelem definovaný typ přetížení `op`binární `op=` operátor , operátor, pokud existuje, je také implicitně přetížena.

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace naleznete v části [Operátory přiřazení](~/_csharplang/spec/expressions.md#assignment-operators) ve [specifikaci jazyka C#](~/_csharplang/spec/introduction.md).

Další informace o operátoru `= ref`přiřazení ref naleznete v [poznámce k návrhu funkce](~/_csharplang/proposals/csharp-7.3/ref-local-reassignment.md).

## <a name="see-also"></a>Viz také

- [Referenční dokumentace k jazyku C#](../index.md)
- [Operátory jazyka C#](index.md)
- [klíčové slovo ref](../keywords/ref.md)
