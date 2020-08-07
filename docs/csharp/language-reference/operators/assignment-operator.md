---
title: Operátory přiřazení – reference jazyka C#
ms.date: 09/10/2019
f1_keywords:
- =_CSharpKeyword
helpviewer_keywords:
- = operator [C#]
ms.assetid: d802a6d5-32f0-42b8-b180-12f5a081bfc1
ms.openlocfilehash: 7b4f3b3f4d6b697903461f08435552f2df36bfe4
ms.sourcegitcommit: ef50c99928183a0bba75e07b9f22895cd4c480f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/07/2020
ms.locfileid: "87916928"
---
# <a name="assignment-operators-c-reference"></a>Operátory přiřazení (Referenční dokumentace jazyka C#)

Operátor přiřazení `=` přiřadí hodnotu jeho pravého operandu proměnné, [vlastnosti](../../programming-guide/classes-and-structs/properties.md)nebo prvku [indexeru](../../programming-guide/indexers/index.md) , který je dán jeho levým operandem. Výsledkem výrazu přiřazení je hodnota přiřazená k levému operandu. Typ operandu na pravé straně musí být stejný jako typ operandu na levé straně nebo implicitně převést na něj.

Operátor přiřazení `=` je asociativní zprava, tj. výraz formuláře.

```csharp
a = b = c
```

je vyhodnocen jako

```csharp
a = (b = c)
```

Následující příklad ukazuje použití operátoru přiřazení s lokální proměnnou, vlastností a prvkem indexeru jako jeho levý operand:

[!code-csharp-interactive[simple assignment](snippets/shared/AssignmentOperator.cs#Simple)]

## <a name="ref-assignment-operator"></a>operátor přiřazení ref

Počínaje jazykem C# 7,3 můžete použít operátor přiřazení odkazu `= ref` k opětovnému přiřazení místní proměnné typu [ref](../keywords/ref.md#ref-locals) nebo [ref jen pro čtení](../keywords/ref.md#ref-readonly-locals) . Následující příklad ukazuje použití operátoru přiřazení ref:

[!code-csharp[ref assignment operator](snippets/shared/AssignmentOperator.cs#RefAssignment)]

V případě operátoru přiřazení odkazu musí být oba operandy stejného typu.

## <a name="compound-assignment"></a>Složené přiřazení

Pro binární operátor `op` , výraz složeného přiřazení formuláře

```csharp
x op= y
```

je ekvivalentem

```csharp
x = x op y
```

s výjimkou, že `x` je vyhodnocena pouze jednou.

Složené přiřazení je podporováno [aritmetickými](arithmetic-operators.md#compound-assignment)a [logickými logickými](boolean-logical-operators.md#compound-assignment)a operátory [SHIFT a Shift](bitwise-and-shift-operators.md#compound-assignment) .

## <a name="null-coalescing-assignment"></a>Přiřazení slučování s hodnotou null

Počínaje jazykem C# 8,0 můžete použít operátor přiřazení s použitím hodnoty null `??=` k přiřazení hodnoty jeho pravého operandu k jeho levému operandu pouze v případě, že je operand na levé straně vyhodnocen `null` . Další informace najdete v tématu [?? a?? =](null-coalescing-operator.md) – článek o operátorech

## <a name="operator-overloadability"></a>Přetížení operátoru

Uživatelsky definovaný typ nemůže [přetížit](operator-overloading.md) operátor přiřazení. Uživatelsky definovaný typ však může definovat implicitní převod na jiný typ. Tímto způsobem lze hodnotu uživatelsky definovaného typu přiřadit proměnné, vlastnosti nebo prvku indexeru jiného typu. Další informace naleznete v tématu [uživatelsky definované operátory převodu](user-defined-conversion-operators.md).

Uživatelsky definovaný typ nemůže explicitně přetížit operátor složeného přiřazení. Pokud však uživatelsky definovaný typ přetěžuje binární operátor `op` , `op=` je operátor, pokud existuje, také implicitně přetížený.

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace naleznete v části [operátory přiřazení](~/_csharplang/spec/expressions.md#assignment-operators) v tématu [specifikace jazyka C#](~/_csharplang/spec/introduction.md).

Další informace o operátoru přiřazení odkazu `= ref` najdete v [poznámce k návrhu funkcí](~/_csharplang/proposals/csharp-7.3/ref-local-reassignment.md).

## <a name="see-also"></a>Viz také

- [Referenční dokumentace k jazyku C#](../index.md)
- [Operátory a výrazy v C#](index.md)
- [ref – klíčové slovo](../keywords/ref.md)
