---
title: + a += operátory - c# odkaz
ms.date: 05/24/2019
f1_keywords:
- +_CSharpKeyword
- +=_CSharpKeyword
helpviewer_keywords:
- addition operator [C#]
- concatenation operator [C#]
- delegate combination [C#]
- + operator [C#]
- addition assignment operator [C#]
- event subscription [C#]
- += operator [C#]
ms.assetid: 93e56486-bb42-43c1-bd43-60af11e64e67
ms.openlocfilehash: cafd07f4b4aefdcc4b43750d61c155fe3d65aa46
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399299"
---
# <a name="-and--operators-c-reference"></a>+ a += operátory (odkaz C#)

A `+` `+=` operátory jsou podporovány předdefinované [integrální](../builtin-types/integral-numeric-types.md) a [plovoucí desetinnou desetinnou](../builtin-types/floating-point-numeric-types.md) hodnotou, typem [řetězce](../builtin-types/reference-types.md#the-string-type) a [delegací.](../builtin-types/reference-types.md#the-delegate-type)

Informace o `+` operátoru aritmetiky naleznete [unary plus a minus operátory](arithmetic-operators.md#unary-plus-and-minus-operators) a sčítání operátor [+](arithmetic-operators.md#addition-operator-) části [aritmetické operátory](arithmetic-operators.md) článku.

## <a name="string-concatenation"></a>Zřetězení řetězců

Pokud jeden nebo oba operandy jsou `+` typu [řetězce](../builtin-types/reference-types.md#the-string-type), operátor zřetězí řetězcové reprezentace jeho operandů:

[!code-csharp-interactive[string concatenation](snippets/AdditionOperator.cs#AddStrings)]

Počínaje C# 6, [řetězec interpolace](../tokens/interpolated.md) poskytuje pohodlnější způsob, jak formátovat řetězce:

[!code-csharp-interactive[string interpolation](snippets/AdditionOperator.cs#UseStringInterpolation)]

## <a name="delegate-combination"></a>Kombinace delegátů

Pro operandy stejného typu `+` [delegáta](../builtin-types/reference-types.md#the-delegate-type) operátor vrátí novou instanci delegáta, která při vyvolání vyvolá operand u levé ruky a potom vyvolá pravostranný operand. Pokud některý z operandů `null` `+` je , operátor vrátí hodnotu jiného `null`operandu (což může být také ). Následující příklad ukazuje, jak lze delegáty kombinovat s operátorem: `+`

[!code-csharp-interactive[delegate combination](snippets/AdditionOperator.cs#AddDelegates)]

Chcete-li provést odebrání [ `-` ](subtraction-operator.md#delegate-removal)delegáta, použijte operátor .

Další informace o typech delegátů naleznete v tématu [Delegáti](../../programming-guide/delegates/index.md).

## <a name="addition-assignment-operator-"></a>Operátor přiřazení sčítání +=

Výraz používající `+=` operátor, například

```csharp
x += y
```

je ekvivalentem

```csharp
x = x + y
```

kromě `x` toho, že se vyhodnocuje pouze jednou.

Následující příklad ukazuje použití operátoru: `+=`

[!code-csharp-interactive[+= examples](snippets/AdditionOperator.cs#AddAndAssign)]

`+=` Operátor můžete také použít k určení metody obslužné rutiny události při přihlášení k odběru [události](../keywords/event.md). Další informace naleznete v [tématu Jak: přihlásit se k odběru a odhlásit se z odběru událostí](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).

## <a name="operator-overloadability"></a>Přetížení obsluhy

Uživatelem definovaný typ může `+` [přetížit](operator-overloading.md) operátor. Když binární `+` operátor je přetížený, `+=` operátor je také implicitně přetížené. Uživatelem definovaný typ nemůže `+=` explicitně přetížit operátor.

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace naleznete [unary plus operátor](~/_csharplang/spec/expressions.md#unary-plus-operator) a [sčítání operátor](~/_csharplang/spec/expressions.md#addition-operator) části [c# specifikace jazyka](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Viz také

- [Referenční dokumentace k jazyku C#](../index.md)
- [Operátory jazyka C#](index.md)
- [Jak zřetězit více řetězců](../../how-to/concatenate-multiple-strings.md)
- [Akce](../../programming-guide/events/index.md)
- [Aritmetické operátory](arithmetic-operators.md)
- [- a -= operátoři](subtraction-operator.md)
