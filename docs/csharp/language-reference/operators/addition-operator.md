---
title: + and + = Operators-C# Reference
ms.date: 04/23/2020
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
ms.openlocfilehash: dac13e9e92a0fffa4aeba1053d07f832e245ca95
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/04/2020
ms.locfileid: "87555484"
---
# <a name="-and--operators-c-reference"></a>+ a + = – operátory (Referenční dokumentace jazyka C#)

`+`Operátory a `+=` jsou podporovány integrovanými [celočíselnými](../builtin-types/integral-numeric-types.md) typy a čísly s [plovoucí desetinnou](../builtin-types/floating-point-numeric-types.md) čárkou, typem [řetězce](../builtin-types/reference-types.md#the-string-type) a typy [delegátů](../builtin-types/reference-types.md#the-delegate-type) .

Informace o aritmetickém `+` operátoru naleznete v tématu [unární operátory plus a minus](arithmetic-operators.md#unary-plus-and-minus-operators) a [operátor sčítání](arithmetic-operators.md#addition-operator-) a další části v článku [aritmetické operátory](arithmetic-operators.md) .

## <a name="string-concatenation"></a>Zřetězení řetězců

Když je jeden nebo oba operandy typu [String](../builtin-types/reference-types.md#the-string-type), `+` operátor zřetězí řetězcové reprezentace svých operandů (řetězcové vyjádření `null` je prázdným řetězcem):

[!code-csharp-interactive[string concatenation](snippets/AdditionOperator.cs#AddStrings)]

Počínaje jazykem C# 6 poskytuje [interpolace řetězců](../tokens/interpolated.md) pohodlnější způsob formátování řetězců:

[!code-csharp-interactive[string interpolation](snippets/AdditionOperator.cs#UseStringInterpolation)]

## <a name="delegate-combination"></a>Kombinace delegátů

Pro operandy stejného typu [delegáta](../builtin-types/reference-types.md#the-delegate-type) `+` vrátí operátor novou instanci delegáta, která při vyvolání vyvolá levý operand a poté vyvolá operand na pravé straně. Pokud je některý z operandů `null` , `+` operátor vrátí hodnotu jiného operandu (což může být také `null` ). Následující příklad ukazuje, jak mohou být Delegáti kombinováni s `+` operátorem:

[!code-csharp-interactive[delegate combination](snippets/AdditionOperator.cs#AddDelegates)]

Chcete-li provést odebrání delegáta, použijte [ `-` operátor](subtraction-operator.md#delegate-removal).

Další informace o typech delegátů naleznete v tématu [Delegates](../../programming-guide/delegates/index.md).

## <a name="addition-assignment-operator-"></a>Operátor přiřazení sčítání + =

Výraz, který používá `+=` operátor, například

```csharp
x += y
```

je ekvivalentem

```csharp
x = x + y
```

s výjimkou, že `x` je vyhodnocena pouze jednou.

Následující příklad ukazuje použití `+=` operátoru:

[!code-csharp-interactive[+= examples](snippets/AdditionOperator.cs#AddAndAssign)]

Operátor můžete také použít `+=` k určení metody obslužné rutiny události při přihlášení k odběru [události](../keywords/event.md). Další informace najdete v tématu [Postup: přihlášení a](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md)odhlášení odběru událostí.

## <a name="operator-overloadability"></a>Přetížení operátoru

Uživatelsky definovaný typ může [přetížit](operator-overloading.md) `+` operátor. Při přetížení binárního `+` operátoru `+=` je operátor také implicitně přetížený. Uživatelsky definovaný typ nemůže explicitně přetížit `+=` operátor.

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace naleznete v částech [unárního operátoru plus](~/_csharplang/spec/expressions.md#unary-plus-operator) a [operátoru sčítání](~/_csharplang/spec/expressions.md#addition-operator) ve [specifikaci jazyka C#](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Viz také

- [Referenční dokumentace k jazyku C#](../index.md)
- [Operátory a výrazy v C#](index.md)
- [Jak zřetězit více řetězců](../../how-to/concatenate-multiple-strings.md)
- [Události](../../programming-guide/events/index.md)
- [Aritmetické operátory](arithmetic-operators.md)
- [-a-= – operátory](subtraction-operator.md)
