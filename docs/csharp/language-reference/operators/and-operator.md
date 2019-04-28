---
title: '&amp; Operator - C# odkaz'
ms.custom: seodec18
ms.date: 10/29/2018
f1_keywords:
- '&_CSharpKeyword'
helpviewer_keywords:
- bitwise AND operator [C#]
- ampersand operator (&) [C#]
- '& operator [C#]'
- AND operator (&) [C#]
ms.assetid: afa346d5-90ec-4b1f-a2c8-3881f018741d
ms.openlocfilehash: 7aac0af93efb3d72496df13a64afb7840993b22c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61660128"
---
# <a name="amp-operator-c-reference"></a>&amp; – Operátor (referenční dokumentace jazyka C#)

`&` Operátor je podporován ve dvou formách: operátor address-of unární nebo binární logický operátor.

## <a name="unary-address-of-operator"></a>Unární operátor address-of

Unární `&` operátor vrátí adresu svého operandu. Další informace najdete v tématu [postupy: získávání adresy proměnné](../../programming-guide/unsafe-code-pointers/how-to-obtain-the-address-of-a-variable.md).

Operátor address-of `&` vyžaduje [nebezpečné](../keywords/unsafe.md) kontextu.

## <a name="integer-logical-bitwise-and-operator"></a>Celé číslo logického bitového operátoru AND

Pro celočíselné typy `&` vypočítá logické bitové operace AND jeho operandy operátoru:

[!code-csharp-interactive[integer logical bitwise AND](~/samples/snippets/csharp/language-reference/operators/AndOperatorExamples.cs#IntegerOperands)]

> [!NOTE]
> V předchozím příkladu binární literály: [zavedený C# 7.0](../../whats-new/csharp-7.md#numeric-literal-syntax-improvements) a [rozšířené v C# 7.2](../../whats-new/csharp-7-2.md#leading-underscores-in-numeric-literals).

Vzhledem k tomu, že operace s celočíselnými typy jsou obecně povoleny na typy výčtu `&` operátor také podporuje [výčtu](../keywords/enum.md) operandy.

## <a name="boolean-logical-and-operator"></a>Logická logického operátoru AND

Pro [bool](../keywords/bool.md) operandy, `&` operátor vypočítá logický operátor AND operandů. Výsledek `x & y` je `true` Pokud mají oba `x` a `y` jsou `true`. V opačném případě je výsledek `false`.

`&` Operátor vyhodnotí oba operandy i v případě, že první operand vyhodnocen jako `false`tak, aby výsledek musí být `false` bez ohledu na hodnotu druhého operandu. Následující příklad ukazuje toto chování:

[!code-csharp-interactive[bool logical AND](~/samples/snippets/csharp/language-reference/operators/AndOperatorExamples.cs#BooleanOperands)]

[Podmiňovací operátor AND](boolean-logical-operators.md#conditional-logical-and-operator-) `&&` také vypočítá logický operátor a jeho operandy, ale nebude vyhodnocení druhého operandu, jestli je první operand vyhodnocen jako `false`.

Pro operandy typu s možnou hodnotou Null bool, chování `&` operátor je konzistentní s logikou s hodnotou tři SQL. Další informace najdete v tématu [logické operátory s povolenou hodnotou Null logická](boolean-logical-operators.md#nullable-boolean-logical-operators) část [logické logické operátory](boolean-logical-operators.md) článku.

## <a name="operator-overloadability"></a>Overloadability – operátor

Uživatelem definované typy lze [přetížení](../keywords/operator.md) binárního souboru `&` operátor. Když binární soubor `&` je operátor přetížen, [operátor přiřazení AND](and-assignment-operator.md) `&=` je také implicitně přetížená.

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace najdete v tématu [operátoru address-of](~/_csharplang/spec/unsafe-code.md#the-address-of-operator) a [logické operátory](~/_csharplang/spec/expressions.md#logical-operators) oddíly [ C# specifikace jazyka](../language-specification/index.md).

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka C#](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [Operátory jazyka C#](index.md)
- [Logická logické operátory](boolean-logical-operators.md)
- [Bitový operátor a operátory posunutí](bitwise-and-shift-operators.md)
- [Typy ukazatelů](../../programming-guide/unsafe-code-pointers/pointer-types.md)