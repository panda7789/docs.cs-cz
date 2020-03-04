---
title: Logické logické operátory – C# referenční informace
description: Přečtěte C# si o operátorech, které provádějí logické negace, spojení (a) a včetně a exkluzivní operace disjunkce (nebo) s logickými operandy.
ms.date: 09/27/2019
author: pkulikov
f1_keywords:
- '!_CSharpKeyword'
- '&_CSharpKeyword'
- ^_CSharpKeyword
- '|_CSharpKeyword'
- '&&_CSharpKeyword'
- '||_CSharpKeyword'
helpviewer_keywords:
- logical operators [C#]
- short-circuiting operators [C#]
- logical negation operator [C#]
- NOT operator [C#]
- '! operator [C#]'
- AND operator [C#]
- ampersand operator [C#]
- conjunction operator [C#]
- '& operator [C#]'
- exclusive OR operator [C#]
- XOR operator [C#]
- ^ operator [C#]
- OR operator [C#]
- disjunction operator [C#]
- '| operator [C#]'
- conditional AND operator [C#]
- short-circuiting AND operator [C#]
- '&& operator [C#]'
- conditional OR operator [C#]
- short-circuiting OR operator [C#]
- '|| operator [C#]'
ms.openlocfilehash: d8fe68fc04300b65bea9b66a6dc6c20e3c69abf4
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/03/2020
ms.locfileid: "78239440"
---
# <a name="boolean-logical-operators-c-reference"></a>Logické logické operátory (C# referenční)

Následující operátory provádějí logické [operace s](../builtin-types/bool.md) logickými operandy:

- Unární operátor [`!` (logická negace)](#logical-negation-operator-)
- Binární [`&` (Logical and)](#logical-and-operator-), [`|` (Logical or)](#logical-or-operator-)a [`^` (Logical or)](#logical-exclusive-or-operator-) Operators. Tyto operátory vždy vyhodnotí oba operandy.
- Binární [`&&` (Podmíněné logické a)](#conditional-logical-and-operator-) a operátory [`||` (Podmíněné logické nebo)](#conditional-logical-or-operator-) . Tyto operátory vyhodnotí operand na pravé straně, pokud je to nezbytné.

Pro operandy [integrálních číselných typů](../builtin-types/integral-numeric-types.md)provádí operátory `&`, `|`a `^` bitové logické operace. Další informace naleznete v tématu [operátory bitových a posunutí](bitwise-and-shift-operators.md).

## <a name="logical-negation-operator-"></a>Logický operátor negace!

Unární předpona `!` operátor vypočítá logickou negaci svého operandu. To znamená, že vytváří `true`, pokud je operand vyhodnocen jako `false`a `false`, pokud je operand vyhodnocen jako `true`:

[!code-csharp-interactive[logical negation](~/samples/snippets/csharp/language-reference/operators/BooleanLogicalOperators.cs#Negation)]

Počínaje C# 8,0, unární přípona `!` operátor je [operátor null-striktní](null-forgiving.md).

## <a name="logical-and-operator-"></a>Logický operátor AND &amp;

Operátor `&` vypočítá logickou a jeho operandy. Výsledek `x & y` je `true`, pokud `x` a `y` vyhodnotit na `true`. V opačném případě je výsledek `false`.

Operátor `&` vyhodnocuje oba operandy i v případě, že je levý operand vyhodnocen jako `false`, aby byl výsledek operace `false` bez ohledu na hodnotu operandu na pravé straně.

V následujícím příkladu je pravý operand operátoru `&` volání metody, která je provedena bez ohledu na hodnotu operandu na levé straně:

[!code-csharp-interactive[logical AND](~/samples/snippets/csharp/language-reference/operators/BooleanLogicalOperators.cs#And)]

[Podmíněný logický operátor and](#conditional-logical-and-operator-) `&&` také vypočítá logickou a jeho operandy, ale nevyhodnotí operand pravého operandu, je-li operand na levé straně vyhodnocen jako `false`.

Pro operandy [integrálních číselných typů](../builtin-types/integral-numeric-types.md)operátor `&` vypočítá [bitovou logickou a](bitwise-and-shift-operators.md#logical-and-operator-) jeho operandy. Unární operátor `&` je [operátor address-of](pointer-related-operators.md#address-of-operator-).

## <a name="logical-exclusive-or-operator-"></a>Logický exkluzivní operátor OR ^

Operátor `^` vypočítá logickou exkluzivní nebo, označovanou také jako logická XOR, z jeho operandů. Výsledek `x ^ y` je `true`, pokud `x` vyhodnocuje `true` a `y` vyhodnocuje jako `false`, nebo `x` vyhodnocuje `false` a `y` vyhodnocuje `true`. V opačném případě je výsledek `false`. To znamená, že pro operandy `bool` `^` operátor vypočítá stejný výsledek jako [operátor nerovnosti](equality-operators.md#inequality-operator-) `!=`.

[!code-csharp-interactive[logical exclusive OR](~/samples/snippets/csharp/language-reference/operators/BooleanLogicalOperators.cs#Xor)]

Pro operandy [integrálních číselných typů](../builtin-types/integral-numeric-types.md)operátor `^` vypočítá [bitový logický typ Exclusive nebo](bitwise-and-shift-operators.md#logical-exclusive-or-operator-) jeho operandů.

## <a name="logical-or-operator-"></a>Logický operátor OR |

Operátor `|` vypočítá logické nebo jeho operandy. Výsledek `x | y` je `true`, pokud je `x` nebo `y` vyhodnocen jako `true`. V opačném případě je výsledek `false`.

Operátor `|` vyhodnocuje oba operandy i v případě, že je levý operand vyhodnocen jako `true`, aby byl výsledek operace `true` bez ohledu na hodnotu operandu na pravé straně.

V následujícím příkladu je pravý operand operátoru `|` volání metody, která je provedena bez ohledu na hodnotu operandu na levé straně:

[!code-csharp-interactive[logical OR](~/samples/snippets/csharp/language-reference/operators/BooleanLogicalOperators.cs#Or)]

[Podmíněný logický operátor or](#conditional-logical-or-operator-) `||` také VYPOČÍTÁ logické nebo jeho operandy, ale nevyhodnotí pravý operand, pokud je levý operand vyhodnocen jako `true`.

Pro operandy [integrálních číselných typů](../builtin-types/integral-numeric-types.md)operátor `|` vypočítá [bitovou logickou nebo](bitwise-and-shift-operators.md#logical-or-operator-) jeho operandy.

## <a name="conditional-logical-and-operator-"></a>Podmíněný &amp;logický operátor AND &amp;

Podmíněný logický operátor AND `&&`, označovaný také jako "" krátkodobého okruhu ", jsou vypočítány logickým operátorem and z jeho operandů. Výsledek `x && y` je `true`, pokud `x` a `y` vyhodnotit na `true`. V opačném případě je výsledek `false`. Pokud se `x` vyhodnotí jako `false`, `y` se nevyhodnotí.

V následujícím příkladu je pravý operand operátoru `&&` voláním metody, která není provedena, pokud je operand na levé straně vyhodnocen jako `false`:

[!code-csharp-interactive[conditional logical AND](~/samples/snippets/csharp/language-reference/operators/BooleanLogicalOperators.cs#ConditionalAnd)]

[Logický operátor and](#logical-and-operator-) `&` také vypočítá logickou a jeho operandy, ale vždy vyhodnotí oba operandy.

## <a name="conditional-logical-or-operator-"></a>Podmíněný logický operátor OR | |

Podmíněný logický operátor OR `||`, označovaný také jako "" krátkodobého okruhu ", je vypočítán logický nebo jeho operandů. Výsledek `x || y` je `true`, pokud je `x` nebo `y` vyhodnocen jako `true`. V opačném případě je výsledek `false`. Pokud se `x` vyhodnotí jako `true`, `y` se nevyhodnotí.

V následujícím příkladu je pravý operand operátoru `||` voláním metody, která není provedena, pokud je operand na levé straně vyhodnocen jako `true`:

[!code-csharp-interactive[conditional logical OR](~/samples/snippets/csharp/language-reference/operators/BooleanLogicalOperators.cs#ConditionalOr)]

[Logický operátor or](#logical-or-operator-) `|` také VYPOČÍTÁ logické nebo jeho operandy, ale vždy vyhodnotí oba operandy.

## <a name="nullable-boolean-logical-operators"></a>Logické operátory s možnou hodnotou null

U operandů `bool?` operátor `&` a `|` podporuje logiku se třemi hodnotami. Sémantika těchto operátorů je definována v následující tabulce:  
  
|x|Y|x & y|×&#124;y|  
|----|----|----|----|  
|true (pravda)|true (pravda)|true (pravda)|true (pravda)|  
|true (pravda)|false (nepravda)|false (nepravda)|true (pravda)|  
|true (pravda)|null|null|true (pravda)|  
|false (nepravda)|true (pravda)|false (nepravda)|true (pravda)|  
|false (nepravda)|false (nepravda)|false (nepravda)|false (nepravda)|  
|false (nepravda)|null|false (nepravda)|null|  
|null|true (pravda)|null|true (pravda)|  
|null|false (nepravda)|false (nepravda)|null|  
|null|null|null|null|  

Chování těchto operátorů se liší od typického chování operátoru s typy s možnou hodnotou null. Obvykle operátor, který je definován pro operandy typu hodnoty, lze také použít s operandy odpovídajícího typu hodnoty s možnou hodnotou null. Takový operátor vytvoří `null`, pokud se některý z jeho operandů vyhodnocuje jako `null`. Operátory `&` a `|` však mohou vygenerovat jinou hodnotu než null, i když je jeden z operandů vyhodnocen jako `null`. Další informace o chování operátora s povolenými typy hodnot s možnou hodnotou null naleznete v části "předané [operátory](../builtin-types/nullable-value-types.md#lifted-operators) " v článku [typy s možnou hodnotou null](../builtin-types/nullable-value-types.md) .

Můžete také použít operátory `!` a `^` s `bool?` operandy, jak ukazuje následující příklad:

[!code-csharp-interactive[lifted negation and xor](~/samples/snippets/csharp/language-reference/operators/BooleanLogicalOperators.cs#WithNullableBoolean)]

Podmíněné logické operátory `&&` a `||` nepodporují `bool?` operandy.

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

Operátory `&`, `|`a `^` podporují složené přiřazení, jak ukazuje následující příklad:

[!code-csharp-interactive[compound assignment](~/samples/snippets/csharp/language-reference/operators/BooleanLogicalOperators.cs#CompoundAssignment)]

Podmíněné logické operátory `&&` a `||` nepodporují složené přiřazení.

## <a name="operator-precedence"></a>Priorita operátorů

Následující seznam uvádí logické operátory od nejvyšší priority k nejnižší:

- Logický operátor negace `!`
- Logický operátor AND `&`
- `^` logický exkluzivní operátor OR
- Logický operátor OR `|`
- Podmíněný `&&` logický operátor AND
- Podmíněný `||` logického operátoru OR

Chcete-li změnit pořadí vyhodnocování stanovené předností operátorů, použijte závorky `()`.

[!code-csharp-interactive[operator precedence](~/samples/snippets/csharp/language-reference/operators/BooleanLogicalOperators.cs#Precedence)]

Úplný seznam C# operátorů seřazených podle priority najdete v části [Priorita operátorů](index.md#operator-precedence) [ C# v článku věnovaném operátorům](index.md) .

## <a name="operator-overloadability"></a>Přetížení operátoru

Uživatelsky definovaný typ může [přetížit](operator-overloading.md) operátory `!`, `&`, `|`a `^`. Při přetížení binárního operátoru je také implicitně přetížen odpovídající operátor složeného přiřazení. Uživatelsky definovaný typ nemůže explicitně přetížit operátor složeného přiřazení.

Uživatelsky definovaný typ nemůže přetížit Podmíněné logické operátory `&&` a `||`. Pokud však uživatelsky definovaný typ přetěžuje [operátory true a false](true-false-operators.md) a operátor `&` nebo `|` určitým způsobem, může být `&&` nebo `||` operace vyhodnocena pro operandy daného typu. Další informace naleznete v části [uživatelsky definované Podmíněné logické operátory](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) [ C# specifikace jazyka](~/_csharplang/spec/introduction.md).

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace najdete v následujících oddílech [ C# specifikace jazyka](~/_csharplang/spec/introduction.md):

- [Logický operátor negace](~/_csharplang/spec/expressions.md#logical-negation-operator)
- [Logické operátory](~/_csharplang/spec/expressions.md#logical-operators)
- [Podmíněné logické operátory](~/_csharplang/spec/expressions.md#conditional-logical-operators)
- [Složené přiřazení](~/_csharplang/spec/expressions.md#compound-assignment)

## <a name="see-also"></a>Viz také

- [C#odkaz](../index.md)
- [Operátory jazyka C#](index.md)
- [Bitové operátory a posunutí](bitwise-and-shift-operators.md)
