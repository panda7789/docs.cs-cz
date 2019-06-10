---
title: + operátory a operátory += – C# odkaz
ms.custom: seodec18
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
ms.openlocfilehash: 2c99065dacbf391e94c97092336f5dda3adda5b0
ms.sourcegitcommit: 5ae6affa0b171be3bb5f4729fb68ea4fe799f959
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/10/2019
ms.locfileid: "66815979"
---
# <a name="-and--operators-c-reference"></a>+ a operátory += (C# odkaz)

`+` Předdefinovaných číselných typů, podporuje operátor [řetězec](../keywords/string.md) typ, a [delegovat](../keywords/delegate.md) typy.

Informace o aritmetické operace `+` operátoru, najdete v článku [Unární plus a minus operátory](arithmetic-operators.md#unary-plus-and-minus-operators) a [operátor sčítání +](arithmetic-operators.md#addition-operator-) oddíly [aritmetické operátory](arithmetic-operators.md)článku.

## <a name="string-concatenation"></a>Zřetězení řetězců

Když se jeden nebo oba operandy typu [řetězec](../keywords/string.md), `+` zřetězí řetězcové reprezentace jeho operandy operátoru:

[!code-csharp-interactive[string concatenation](~/samples/csharp/language-reference/operators/AdditionOperator.cs#AddStrings)]

Počínaje C# 6, [interpolace](../tokens/interpolated.md) poskytuje pohodlnější způsob, jak formátovací řetězce:

[!code-csharp-interactive[string interpolation](~/samples/csharp/language-reference/operators/AdditionOperator.cs#UseStringInterpolation)]

## <a name="delegate-combination"></a>Kombinaci delegátů

Pro operandy stejného [delegovat](../keywords/delegate.md) typ, `+` operátor vrátí novou instanci delegáta, která při vyvolání, vyvolá prvním operandem a poté vyvolá druhého operandu. Pokud kterýkoli z operandů `null`, `+` operátor vrátí hodnotu jiný operand (která může být také `null`). Následující příklad ukazuje, jak mohou být kombinovány delegáty s `+` operátor:

[!code-csharp-interactive[delegate combination](~/samples/csharp/language-reference/operators/AdditionOperator.cs#AddDelegates)]

Chcete-li provést odebrání delegátů, použijte [ `-` operátor](subtraction-operator.md#delegate-removal).

Další informace o typech delegáta, naleznete v tématu [delegáti](../../programming-guide/delegates/index.md).

## <a name="addition-assignment-operator-"></a>+= – Operátor přiřazení sčítání

Pomocí výrazu `+=` operátorů, například

```csharp
x += y
```

je ekvivalentem

```csharp
x = x + y
```

s tím rozdílem, že `x` se jenom vyhodnotí jednou.
  
Následující příklad ukazuje použití `+=` operátor:

[!code-csharp-interactive[+= examples](~/samples/csharp/language-reference/operators/AdditionOperator.cs#AddAndAssign)]

Můžete také použít `+=` operátor zadat metodu obslužné rutiny události, když se přihlásíte k odběru [události](../keywords/event.md). Další informace najdete v tématu [postupy: přihlášení k odběru a zrušit její odběr události](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).

## <a name="operator-overloadability"></a>Overloadability – operátor

Uživatelem definovaný typ může [přetížení](../keywords/operator.md) `+` operátor. Když do binárního souboru `+` je operátor přetížen, `+=` je také implicitně přetížený operátor. Uživatelem definovaný typ nejde přetížit explicitně `+=` operátor.

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace najdete v tématu [unární operátor plus](~/_csharplang/spec/expressions.md#unary-plus-operator) a [operátor sčítání](~/_csharplang/spec/expressions.md#addition-operator) oddíly [ C# specifikace jazyka](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka C#](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [Operátory jazyka C#](index.md)
- [Interpolace řetězců](../tokens/interpolated.md)
- [Postupy: řetězení více řetězců](../../how-to/concatenate-multiple-strings.md)
- [Delegáti](../../programming-guide/delegates/index.md)
- [Události](../../programming-guide/events/index.md)
- [Zaškrtnuto a nezaškrtnuto](../keywords/checked-and-unchecked.md)
- [Aritmetické operátory](arithmetic-operators.md)
- [– operátory a operátory-=](subtraction-operator.md)
