---
title: Booleovské logické operátory – reference jazyka C#
description: Přečtěte si o operátorech jazyka C#, které provádějí logické negace, spojení (a) a včetně a exkluzivní operace disjunkce (nebo) s logickými operandy.
ms.date: 06/29/2020
author: pkulikov
f1_keywords:
- '!_CSharpKeyword'
- '&_CSharpKeyword'
- ^_CSharpKeyword
- '|_CSharpKeyword'
- '&&_CSharpKeyword'
- '||_CSharpKeyword'
- '|=_CSharpKeyword'
- ^=_CSharpKeyword
- '&=_CSharpKeyword'
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
ms.openlocfilehash: 00b1523029ed6562fda6947415029cd3b7a9b405
ms.sourcegitcommit: ef50c99928183a0bba75e07b9f22895cd4c480f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/07/2020
ms.locfileid: "87916888"
---
# <a name="boolean-logical-operators-c-reference"></a>Logické logické operátory (Referenční dokumentace jazyka C#)

Následující operátory provádějí logické [operace s](../builtin-types/bool.md) logickými operandy:

- Unární operátor [ `!` (logická negace)](#logical-negation-operator-)
- Binary [ `&` (Logical and)](#logical-and-operator-), [ `|` (Logical or)](#logical-or-operator-)a [ `^` (Logical or)](#logical-exclusive-or-operator-) Operators. Tyto operátory vždy vyhodnotí oba operandy.
- Binární [ `&&` (Podmíněné logické a)](#conditional-logical-and-operator-) a [ `||` (Podmíněné logické OR)](#conditional-logical-or-operator-) operátory. Tyto operátory vyhodnotí operand na pravé straně, pokud je to nezbytné.

Pro operandy [integrálních číselných typů](../builtin-types/integral-numeric-types.md), `&` operátory, `|` a `^` provádějí bitové logické operace. Další informace naleznete v tématu [operátory bitových a posunutí](bitwise-and-shift-operators.md).

## <a name="logical-negation-operator-"></a>Logický operátor negace!

Unární operátor prefixu `!` vypočítá logickou negaci svého operandu. To znamená, že je `true` -li operand vyhodnocen `false` , a `false` , pokud je operand vyhodnocen jako `true` :

[!code-csharp-interactive[logical negation](snippets/shared/BooleanLogicalOperators.cs#Negation)]

Počínaje jazykem C# 8,0, unární příponový `!` operátor je [operátor null-striktní](null-forgiving.md).

## <a name="logical-and-operator-amp"></a><a name="logical-and-operator-"></a>Logický operátor AND&amp;

`&`Operátor vypočítá logickou a jeho operandy. Výsledek je, `x & y` `true` Pokud je `x` a `y` vyhodnocen jako `true` . V opačném případě je výsledkem `false` .

`&`Operátor vyhodnocuje oba operandy i v případě, že je levý operand vyhodnocen tak `false` , aby výsledek operace byl `false` bez ohledu na hodnotu operandu na pravé straně.

V následujícím příkladu je pravý operand `&` operátoru volání metody, která je provedena bez ohledu na hodnotu operandu na levé straně:

[!code-csharp-interactive[logical AND](snippets/shared/BooleanLogicalOperators.cs#And)]

[Podmíněný logický operátor and](#conditional-logical-and-operator-) `&&` také VYPOČÍTÁ logickou a jeho operandy, ale nevyhodnotí pravý operand, pokud je levý operand vyhodnocen jako `false` .

Pro operandy [integrálních číselných typů](../builtin-types/integral-numeric-types.md) `&` operátor vypočítá [bitovou logickou a](bitwise-and-shift-operators.md#logical-and-operator-) jeho operandy. Unární `&` operátor je [operátor address-of](pointer-related-operators.md#address-of-operator-).

## <a name="logical-exclusive-or-operator-"></a>Logický exkluzivní operátor OR ^

`^`Operátor vypočítá logickou výlučnou nebo, označovanou také jako logická XOR, z operandů. Výsledkem `x ^ y` je `true` , pokud je `x` vyhodnocena jako `true` a `y` `false` `x` `false` `y` `true` vyhodnocena jako nebo vyhodnocena jako a vyhodnocena jako. V opačném případě je výsledkem `false` . To znamená, že pro `bool` operandy `^` vypočítá operátor stejný výsledek jako [operátor nerovnosti](equality-operators.md#inequality-operator-) `!=` .

[!code-csharp-interactive[logical exclusive OR](snippets/shared/BooleanLogicalOperators.cs#Xor)]

Pro operandy [integrálních číselných typů](../builtin-types/integral-numeric-types.md) `^` operátor vypočítá [BITOVÝ logický typ Exclusive nebo](bitwise-and-shift-operators.md#logical-exclusive-or-operator-) jeho operandů.

## <a name="logical-or-operator-"></a>Logický operátor OR |

`|`Operátor vypočítá logický nebo jeho operandy. Výsledek je v `x | y` případě, že je `true` buď `x` nebo `y` vyhodnocen jako `true` . V opačném případě je výsledkem `false` .

`|`Operátor vyhodnocuje oba operandy i v případě, že je levý operand vyhodnocen tak `true` , aby výsledek operace byl `true` bez ohledu na hodnotu operandu na pravé straně.

V následujícím příkladu je pravý operand `|` operátoru volání metody, která je provedena bez ohledu na hodnotu operandu na levé straně:

[!code-csharp-interactive[logical OR](snippets/shared/BooleanLogicalOperators.cs#Or)]

[Podmíněný logický operátor OR](#conditional-logical-or-operator-) `||` také vypočítá logické nebo jeho operandy, ale nevyhodnotí operand pravého operandu, je-li operand na levé straně vyhodnocen `true` .

Pro operandy [integrálních číselných typů](../builtin-types/integral-numeric-types.md) `|` operátor vypočítá [bitovou logickou nebo](bitwise-and-shift-operators.md#logical-or-operator-) jeho operandy.

## <a name="conditional-logical-and-operator-ampamp"></a><a name="conditional-logical-and-operator-"></a>Podmíněný logický operátor AND&amp;&amp;

Podmíněný logický operátor AND `&&` , označovaný také jako "" krátkodobého okruhu ", je vypočítán logický operátor a jeho operandů. Výsledek je, `x && y` `true` Pokud je `x` a `y` vyhodnocen jako `true` . V opačném případě je výsledkem `false` . Pokud se `x` vyhodnotí jako `false` , `y` nevyhodnotí se.

V následujícím příkladu je pravý operand `&&` operátoru volání metody, které není provedeno, je-li operand na levé straně vyhodnocen jako `false` :

[!code-csharp-interactive[conditional logical AND](snippets/shared/BooleanLogicalOperators.cs#ConditionalAnd)]

[Logický operátor and](#logical-and-operator-) `&` také VYPOČÍTÁ logickou a jeho operandy, ale vždy vyhodnotí oba operandy.

## <a name="conditional-logical-or-operator-"></a>Podmíněný logický operátor OR | |

Podmíněný logický operátor OR `||` , označovaný také jako "" krátkodobého "logického okruhu, vypočítá logické nebo jeho operandy. Výsledek je v `x || y` případě, že je `true` buď `x` nebo `y` vyhodnocen jako `true` . V opačném případě je výsledkem `false` . Pokud se `x` vyhodnotí jako `true` , `y` nevyhodnotí se.

V následujícím příkladu je pravý operand `||` operátoru volání metody, které není provedeno, je-li operand na levé straně vyhodnocen jako `true` :

[!code-csharp-interactive[conditional logical OR](snippets/shared/BooleanLogicalOperators.cs#ConditionalOr)]

[Logický operátor OR](#logical-or-operator-) `|` také vypočítá logické nebo jeho operandy, ale vždy vyhodnotí oba operandy.

## <a name="nullable-boolean-logical-operators"></a>Logické operátory s možnou hodnotou null

U `bool?` operandů operátory [ `&` (Logical a)](#logical-and-operator-) a [ `|` (Logical a)](#logical-or-operator-) podporují logiku se třemi hodnotami takto:

- `&`Operátor vytvoří `true` pouze v případě, že se na jeho operandy vyhodnotí `true` . Pokud je `x` nebo `y` vyhodnocena jako `false` , `x & y` vytvoří (i když se `false` jiný operand vyhodnocuje `null` ). V opačném případě výsledek `x & y` je `null` .

- `|`Operátor vytvoří `false` pouze v případě, že se na jeho operandy vyhodnotí `false` . Pokud je `x` nebo `y` vyhodnocena jako `true` , `x | y` vytvoří (i když se `true` jiný operand vyhodnocuje `null` ). V opačném případě výsledek `x | y` je `null` .

Následující tabulka uvádí sémantiku:

|x|y|x&y|x&#124;y|  
|----|----|----|----|  
|true|true|true|true|  
|true|false (nepravda)|false (nepravda)|true|  
|true|null|null|true|  
|false (nepravda)|true|false (nepravda)|true|  
|false (nepravda)|false (nepravda)|false (nepravda)|false (nepravda)|  
|false (nepravda)|null|false (nepravda)|null|  
|null|true|null|true|  
|null|false (nepravda)|false (nepravda)|null|  
|null|null|null|null|  

Chování těchto operátorů se liší od typického chování operátoru s typy s možnou hodnotou null. Obvykle operátor, který je definován pro operandy typu hodnoty, lze také použít s operandy odpovídajícího typu hodnoty s možnou hodnotou null. Takový operátor vytvoří, `null` Pokud se některý z jeho operandů vyhodnotí jako `null` . Nicméně `&` `|` operátory a mohou vygenerovat jinou hodnotu než null, i když je jeden z operandů vyhodnocen jako `null` . Další informace o chování operátora s povolenými typy hodnot s možnou hodnotou null naleznete v části "předané [operátory](../builtin-types/nullable-value-types.md#lifted-operators) " v článku [typy s možnou hodnotou null](../builtin-types/nullable-value-types.md) .

Operátory a lze také použít `!` `^` s `bool?` operandy, jak ukazuje následující příklad:

[!code-csharp-interactive[lifted negation and xor](snippets/shared/BooleanLogicalOperators.cs#WithNullableBoolean)]

Podmíněné logické operátory `&&` a `||` nepodporují `bool?` operandy.

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

`&`Operátory, `|` a `^` podporují složené přiřazení, jak ukazuje následující příklad:

[!code-csharp-interactive[compound assignment](snippets/shared/BooleanLogicalOperators.cs#CompoundAssignment)]

> [!NOTE]
> Podmíněné logické operátory `&&` a `||` nepodporují složené přiřazení.

## <a name="operator-precedence"></a>Priorita operátorů

Následující seznam uvádí logické operátory od nejvyšší priority k nejnižší:

- Logický operátor negace`!`
- Logický operátor AND`&`
- Logický exkluzivní operátor OR`^`
- Logický operátor OR`|`
- Podmíněný logický operátor AND`&&`
- Podmíněný logický operátor OR`||`

Pomocí závorek `()` můžete změnit pořadí vyhodnocování stanovené předností operátorů:

[!code-csharp-interactive[operator precedence](snippets/shared/BooleanLogicalOperators.cs#Precedence)]

Úplný seznam operátorů jazyka C# seřazených podle priority úrovně naleznete v části [Priorita operátorů](index.md#operator-precedence) v článku [operátory jazyka c#](index.md) .

## <a name="operator-overloadability"></a>Přetížení operátoru

Uživatelsky definovaný typ může [přetížit](operator-overloading.md) `!` `&` operátory,, a `|` `^` . Při přetížení binárního operátoru je také implicitně přetížen odpovídající operátor složeného přiřazení. Uživatelsky definovaný typ nemůže explicitně přetížit operátor složeného přiřazení.

Uživatelsky definovaný typ nemůže přetížit Podmíněné logické operátory `&&` a `||` . Pokud však uživatelsky definovaný typ přetěžuje [operátory true a false](true-false-operators.md) a `&` `|` operátor OR určitým způsobem, `&&` `||` může být operace nebo v uvedeném pořadí vyhodnocena pro operandy daného typu. Další informace naleznete v části [Podmíněné logické operátory definované uživatelem](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) v tématu [specifikace jazyka C#](~/_csharplang/spec/introduction.md).

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace naleznete v následujících oddílech [specifikace jazyka C#](~/_csharplang/spec/introduction.md):

- [Logický operátor negace](~/_csharplang/spec/expressions.md#logical-negation-operator)
- [Logické operátory](~/_csharplang/spec/expressions.md#logical-operators)
- [Podmíněné logické operátory](~/_csharplang/spec/expressions.md#conditional-logical-operators)
- [Složené přiřazení](~/_csharplang/spec/expressions.md#compound-assignment)

## <a name="see-also"></a>Viz také

- [Referenční dokumentace k jazyku C#](../index.md)
- [Operátory a výrazy v C#](index.md)
- [Bitové operátory a operátory bitového posunu](bitwise-and-shift-operators.md)
