---
title: C#operátory – C# referenční informace
ms.date: 04/30/2019
f1_keywords:
- cs.operators
helpviewer_keywords:
- boolean operators [C#]
- expressions [C#], operators
- logical operators [C#]
- operators [C#]
- Visual C#, operators
- indirection operators [C#]
- assignment operators [C#]
- shift operators [C#]
- relational operators [C#]
- bitwise operators [C#]
- address operators [C#]
- keywords [C#], operators
- arithmetic operators [C#]
ms.assetid: 0301e31f-22ad-49af-ac3c-d5eae7f0ac43
ms.openlocfilehash: 7db61e530ba5c3e0b5ae0ee0002621e369e1833b
ms.sourcegitcommit: 29a9b29d8b7d07b9c59d46628da754a8bff57fa4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/17/2019
ms.locfileid: "69566837"
---
# <a name="c-operators-c-reference"></a>C#operátory (C# Referenční dokumentace)

C#poskytuje několik předdefinovaných operátorů podporovaných integrovanými typy. Například aritmetické [operátory](arithmetic-operators.md) provádějí aritmetické operace s operandy předdefinovaných číselných typů a logické [logické operátory](boolean-logical-operators.md) provádějí logické operace s logickými [](../keywords/bool.md) operandy.

Uživatelsky definovaný typ může přetížit určité operátory pro definování odpovídajícího chování pro operandy daného typu. Další informace naleznete v tématu [přetížení operátoru](operator-overloading.md).

V následující tabulce jsou uvedeny C# operátory od nejvyšší priority k nejnižší. Operátory v rámci každého řádku mají stejnou úroveň priority.

| Operátory | Kategorie nebo název |
| --------- | ---------------- |
| [x. y](member-access-operators.md#member-access-operator-), [x?. y](member-access-operators.md#null-conditional-operators--and-), [x? [ y]](member-access-operators.md#null-conditional-operators--and-), [f (x)](member-access-operators.md#invocation-operator-), [a&#91;i&#93;](member-access-operators.md#indexer-operator-), [x + +](arithmetic-operators.md#increment-operator-), [x--](arithmetic-operators.md#decrement-operator---), [New](new-operator.md), [typeof](type-testing-and-cast.md#typeof-operator), [zaškrtnutí](../keywords/checked.md), [nezaškrtnuto](../keywords/unchecked.md), [Default](default.md), [nameof](nameof.md), [Delegate](delegate-operator.md), [sizeof](sizeof.md), [stackalloc](stackalloc.md), [x-> y](pointer-related-operators.md#pointer-member-access-operator--) | Primární |
| [+ x](arithmetic-operators.md#unary-plus-and-minus-operators), [-x](arithmetic-operators.md#unary-plus-and-minus-operators), [ \!x](boolean-logical-operators.md#logical-negation-operator-), [~ x](bitwise-and-shift-operators.md#bitwise-complement-operator-), [+ + x](arithmetic-operators.md#increment-operator-), [--x](arithmetic-operators.md#decrement-operator---), [(T) x](type-testing-and-cast.md#cast-operator-), [await](../keywords/await.md), [& x](pointer-related-operators.md#address-of-operator-), [* x](pointer-related-operators.md#pointer-indirection-operator-), [true a false](true-false-operators.md) . | Unární |
| [x * y](arithmetic-operators.md#multiplication-operator-), [x/y](arithmetic-operators.md#division-operator-), [x% y](arithmetic-operators.md#remainder-operator-) | Multiplikativní|
| [x + y](arithmetic-operators.md#addition-operator-), [x – y](arithmetic-operators.md#subtraction-operator--) | Přičítáním |
| [ x\< y ,\< ](bitwise-and-shift-operators.md#left-shift-operator-) [x > > y](bitwise-and-shift-operators.md#right-shift-operator-) | SHIFT |
| [x\< y](comparison-operators.md#less-than-operator-), [x > y](comparison-operators.md#greater-than-operator-), [x \<= y](comparison-operators.md#less-than-or-equal-operator-), [x > = y](comparison-operators.md#greater-than-or-equal-operator-), [je](type-testing-and-cast.md#is-operator), [jako](type-testing-and-cast.md#as-operator) | Relační testování a testování typu |
| [x = = y](equality-operators.md#equality-operator-), [x! = y](equality-operators.md#inequality-operator-) | Rovnost |
| `x & y` | Logická [logický operátor and](boolean-logical-operators.md#logical-and-operator-) nebo [BITOVÝ logický operátor and](bitwise-and-shift-operators.md#logical-and-operator-) |
| `x ^ y` | [Logická logická hodnota XOR](boolean-logical-operators.md#logical-exclusive-or-operator-) nebo [bitový logický operátor XOR](bitwise-and-shift-operators.md#logical-exclusive-or-operator-) |
| <code>x &#124; y</code> | Logická nebo logická logická [hodnota](boolean-logical-operators.md#logical-or-operator-) [nebo](bitwise-and-shift-operators.md#logical-or-operator-) |
| [x & & y](boolean-logical-operators.md#conditional-logical-and-operator-) | Podmiňovací operátor AND |
| [× &#124; &#124; y](boolean-logical-operators.md#conditional-logical-or-operator-) | Podmiňovací operátor OR |
| [x?? požadované](null-coalescing-operator.md) | Operátor slučování null |
| [r? t: f](conditional-operator.md) | Podmíněný operátor |
| [x = y](assignment-operator.md), [x + = y](arithmetic-operators.md#compound-assignment), [x-= y](arithmetic-operators.md#compound-assignment), [x * = y](arithmetic-operators.md#compound-assignment), [x/= y](arithmetic-operators.md#compound-assignment), [x% = y](arithmetic-operators.md#compound-assignment), [x & = y](boolean-logical-operators.md#compound-assignment), [x &#124;= y](boolean-logical-operators.md#compound-assignment), [x ^ = y](boolean-logical-operators.md#compound-assignment), [x < < = y](bitwise-and-shift-operators.md#compound-assignment), [x > > = y](bitwise-and-shift-operators.md#compound-assignment),[=>](lambda-operator.md) | Přiřazení a deklarace lambda |

## <a name="see-also"></a>Viz také:

- [C#odkaz](../index.md)
- [Operátory](../../programming-guide/statements-expressions-operators/operators.md)
