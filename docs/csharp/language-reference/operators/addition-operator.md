---
title: + a + = operátory – C# referenční informace
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
ms.openlocfilehash: 0c468f0fe56c68a16de660dbb3bd6356b4b6a00f
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712764"
---
# <a name="-and--operators-c-reference"></a>+ a + = – operátoryC# (Referenční dokumentace)

Operátory `+` a `+=` jsou podporovány integrovanými čísly [integrálních](../builtin-types/integral-numeric-types.md) typů a čísel s [plovoucí desetinnou](../builtin-types/floating-point-numeric-types.md) čárkou, typu [řetězce](../builtin-types/reference-types.md#the-string-type) a typy [delegátů](../builtin-types/reference-types.md#the-delegate-type) .

Informace o aritmetickém operátoru `+` naleznete v části [unární operátory plus a minus](arithmetic-operators.md#unary-plus-and-minus-operators) a [operátor sčítání](arithmetic-operators.md#addition-operator-) a další části v článku [aritmetické operátory](arithmetic-operators.md) .

## <a name="string-concatenation"></a>Zřetězení řetězců

Když je jeden nebo oba operandy typu [String](../builtin-types/reference-types.md#the-string-type), operátor `+` zřetězí řetězcové reprezentace svých operandů:

[!code-csharp-interactive[string concatenation](~/samples/csharp/language-reference/operators/AdditionOperator.cs#AddStrings)]

Počínaje C# 6, [interpolace řetězců](../tokens/interpolated.md) poskytuje pohodlnější způsob formátování řetězců:

[!code-csharp-interactive[string interpolation](~/samples/csharp/language-reference/operators/AdditionOperator.cs#UseStringInterpolation)]

## <a name="delegate-combination"></a>Kombinace delegátů

U operandů stejného typu [delegát](../builtin-types/reference-types.md#the-delegate-type) vrací operátor `+` novou instanci delegáta, která při vyvolání vyvolá levý operand a poté vyvolá operand na pravé straně. Pokud je některý z operandů `null`, vrátí operátor `+` hodnotu jiného operandu (který také může být `null`). Následující příklad ukazuje, jak mohou být Delegáti kombinováni s operátorem `+`:

[!code-csharp-interactive[delegate combination](~/samples/csharp/language-reference/operators/AdditionOperator.cs#AddDelegates)]

Chcete-li provést odebrání delegáta, použijte [operátor`-`](subtraction-operator.md#delegate-removal).

Další informace o typech delegátů naleznete v tématu [Delegates](../../programming-guide/delegates/index.md).

## <a name="addition-assignment-operator-"></a>Operátor přiřazení sčítání + =

Výraz používající operátor `+=`, například

```csharp
x += y
```

je ekvivalentem

```csharp
x = x + y
```

s výjimkou `x` je vyhodnocena pouze jednou.

Následující příklad ukazuje použití operátoru `+=`:

[!code-csharp-interactive[+= examples](~/samples/csharp/language-reference/operators/AdditionOperator.cs#AddAndAssign)]

Operátor `+=` lze také použít k určení metody obslužné rutiny události při přihlášení k odběru [události](../keywords/event.md). Další informace najdete v tématu [Postup: přihlášení a](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md)odhlášení odběru událostí.

## <a name="operator-overloadability"></a>Přetížení operátoru

Uživatelsky definovaný typ může [přetížit](operator-overloading.md) operátor `+`. Je-li operátor binárního `+` přetížen, je operátor `+=` také implicitně přetížený. Uživatelsky definovaný typ nemůže explicitně přetížit operátor `+=`.

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace naleznete v částech [unárního operátoru plus](~/_csharplang/spec/expressions.md#unary-plus-operator) a [operátoru sčítání](~/_csharplang/spec/expressions.md#addition-operator) ve [ C# specifikaci jazyka](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Viz také:

- [C#odkaz](../index.md)
- [Operátory jazyka C#](index.md)
- [Jak zřetězit více řetězců](../../how-to/concatenate-multiple-strings.md)
- [Události](../../programming-guide/events/index.md)
- [Aritmetické operátory](arithmetic-operators.md)
- [-a-= – operátory](subtraction-operator.md)
