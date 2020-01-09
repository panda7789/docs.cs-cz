---
title: Operátory přiřazení – C# referenční informace
ms.date: 09/10/2019
f1_keywords:
- =_CSharpKeyword
helpviewer_keywords:
- = operator [C#]
ms.assetid: d802a6d5-32f0-42b8-b180-12f5a081bfc1
ms.openlocfilehash: 19f74e6835ae555a3a38aa6ca8679948c7f290dd
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712751"
---
# <a name="assignment-operators-c-reference"></a>Operátory přiřazení (C# Referenční dokumentace)

Operátor přiřazení `=` přiřadí hodnotu jeho pravého operandu proměnné, [vlastnosti](../../programming-guide/classes-and-structs/properties.md)nebo prvku [indexeru](../../programming-guide/indexers/index.md) , který je dán jeho levým operandem. Výsledkem výrazu přiřazení je hodnota přiřazená k levému operandu. Typ operandu na pravé straně musí být stejný jako typ operandu na levé straně nebo implicitně převést na něj.

Operátor přiřazení `=` je asociativní zprava, to znamená výraz formuláře.

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

Počínaje C# 7,3 můžete použít operátor přiřazení ref `= ref` k opětovnému přiřazení místní proměnné ref nebo [ref](../keywords/ref.md#ref-readonly-locals) pro [místní](../keywords/ref.md#ref-locals) typ. Následující příklad ukazuje použití operátoru přiřazení ref:

[!code-csharp[ref assignment operator](~/samples/csharp/language-reference/operators/AssignmentOperator.cs#RefAssignment)]

V případě operátoru přiřazení odkazu musí být oba operandy stejného typu.

## <a name="compound-assignment"></a>Složené přiřazení

Pro binární operátor `op`, výraz složeného přiřazení formuláře

```csharp
x op= y
```

je ekvivalentem

```csharp
x = x op y
```

s výjimkou `x` je vyhodnocena pouze jednou.

Složené přiřazení je podporováno [aritmetickými](arithmetic-operators.md#compound-assignment)a [logickými logickými](boolean-logical-operators.md#compound-assignment)a operátory [SHIFT a Shift](bitwise-and-shift-operators.md#compound-assignment) .

## <a name="null-coalescing-assignment"></a>Přiřazení slučování s hodnotou null

Počínaje C# 8,0 můžete použít operátor přiřazení s použitím hodnoty null `??=` k přiřazení hodnoty jeho pravého operandu k jeho levému operandu pouze v případě, že je operand na levé straně vyhodnocen jako `null`. Další informace najdete v tématu [?? a?? =](null-coalescing-operator.md) – článek o operátorech

## <a name="operator-overloadability"></a>Přetížení operátoru

Uživatelsky definovaný typ nemůže [přetížit](operator-overloading.md) operátor přiřazení. Uživatelsky definovaný typ však může definovat implicitní převod na jiný typ. Tímto způsobem lze hodnotu uživatelsky definovaného typu přiřadit proměnné, vlastnosti nebo prvku indexeru jiného typu. Další informace naleznete v tématu [uživatelsky definované operátory převodu](user-defined-conversion-operators.md).

Uživatelsky definovaný typ nemůže explicitně přetížit operátor složeného přiřazení. Pokud však uživatelsky definovaný typ převede binární operátor `op`, je-li objekt `op=`, pokud existuje, je také implicitně přetížený.

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace naleznete v části [operátory přiřazení](~/_csharplang/spec/expressions.md#assignment-operators) ve [ C# specifikaci jazyka](~/_csharplang/spec/introduction.md).

Další informace o operátoru přiřazení ref `= ref`naleznete v [poznámkách k návrhu funkcí](~/_csharplang/proposals/csharp-7.3/ref-local-reassignment.md).

## <a name="see-also"></a>Viz také:

- [C#odkaz](../index.md)
- [Operátory jazyka C#](index.md)
- [ref – klíčové slovo](../keywords/ref.md)
