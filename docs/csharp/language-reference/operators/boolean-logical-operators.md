---
title: Logické operátory logické - C# odkaz
description: Další informace o C# operátory, které provádějí operace disjunkce výhradními i zahrnutými (nebo) logická operandy, spojení (a) a Logická negace.
ms.date: 04/08/2019
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
ms.openlocfilehash: 3ac3479de0bd3c95256741a8b3075f2e5786b65c
ms.sourcegitcommit: 621a5f6df00152006160987395b93b5b55f7ffcd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/29/2019
ms.locfileid: "66300104"
---
# <a name="boolean-logical-operators-c-reference"></a>Logická logické operátory (C# odkaz)

Následující operátory provádí logické operace s [bool](../keywords/bool.md) operandy:

- Unární [ `!` (Logická negace)](#logical-negation-operator-) operátor.
- Binární [ `&` (logický operátor a)](#logical-and-operator-), [ `|` (logický operátor nebo)](#logical-or-operator-), a [ `^` (logické XOR)](#logical-exclusive-or-operator-) operátory. Tyto operátory jsou vždy vyhodnoceny oba operandy.
- Binární [ `&&` (logický operátor podmíněného AND)](#conditional-logical-and-operator-) a [ `||` (logický operátor podmíněného OR)](#conditional-logical-or-operator-) operátory. Tyto operátory vyhodnocení druhého operandu, pouze pokud je nutné.

Pro operandy [integrální](../keywords/integral-types-table.md) typy, `&`, `|`, a `^` operátory provádějí operace bitový logický. Další informace najdete v tématu [operátory bitové a shift](bitwise-and-shift-operators.md).

## <a name="logical-negation-operator-"></a>Logický operátor negace!

`!` Vypočítá operátor logické negace svého operandu. To znamená, vytvoří `true`, pokud je operand vyhodnocen jako `false`, a `false`, pokud je operand vyhodnocen jako `true`:

[!code-csharp-interactive[logical negation](~/samples/snippets/csharp/language-reference/operators/LogicalOperators.cs#Negation)]

## <a name="logical-and-operator-amp"></a>Logický operátor AND &amp;

`&` Operátor vypočítá logický operátor AND operandů. Výsledek `x & y` je `true` Pokud mají oba `x` a `y` vyhodnotit `true`. V opačném případě je výsledek `false`.

`&` Operátor vyhodnotí oba operandy i v případě, že první operand vyhodnocen jako `false`tak, aby výsledek musí být `false` bez ohledu na hodnotu druhého operandu.

V následujícím příkladu, druhý operand `&` operátor je volání metody, která se provádí bez ohledu na hodnotu prvního operandu:

[!code-csharp-interactive[logical AND](~/samples/snippets/csharp/language-reference/operators/LogicalOperators.cs#And)]

[Podmíněné logického operátoru AND](#conditional-logical-and-operator-) `&&` také vypočítá logický operátor a jeho operandy, ale nebude vyhodnocení druhého operandu, jestli je první operand vyhodnocen jako `false`.

Pro operandy integrální typy `&` operátor výpočetní prostředí [bitové logické AND](bitwise-and-shift-operators.md#logical-and-operator-) z operandů. Unární `&` operátor je [operátoru address-of](pointer-related-operators.md#address-of-operator-).

## <a name="logical-exclusive-or-operator-"></a>Logický exkluzivní operátor OR ^

`^` Operátor vypočítá logické exkluzivní OR označované také jako logický operátor XOR z operandů. Výsledek `x ^ y` je `true` Pokud `x` vyhodnotí jako `true` a `y` vyhodnotí jako `false`, nebo `x` vyhodnotí jako `false` a `y` vyhodnotí jako `true`. V opačném případě je výsledek `false`. To znamená pro `bool` operandy, `^` operátor vypočítá stejný výsledek jako [operátor nerovnosti](equality-operators.md#inequality-operator-) `!=`.

[!code-csharp-interactive[logical exclusive OR](~/samples/snippets/csharp/language-reference/operators/LogicalOperators.cs#Xor)]

Pro operandy integrální typy `^` operátor výpočetní prostředí [logický bitový exkluzivní operátor OR](bitwise-and-shift-operators.md#logical-exclusive-or-operator-) z operandů.

## <a name="logical-or-operator-"></a>Logický operátor OR |

`|` Operátor vypočítá logický operátor OR operandů. Výsledek `x | y` je `true` Pokud `x` nebo `y` vyhodnotí jako `true`. V opačném případě je výsledek `false`.

`|` Operátor vyhodnotí oba operandy i v případě, že první operand vyhodnocen jako `true`tak, aby výsledek musí být `true` bez ohledu na hodnotu druhého operandu.

V následujícím příkladu, druhý operand `|` operátor je volání metody, která se provádí bez ohledu na hodnotu prvního operandu:

[!code-csharp-interactive[logical OR](~/samples/snippets/csharp/language-reference/operators/LogicalOperators.cs#Or)]

[Podmíněné logického operátoru OR](#conditional-logical-or-operator-) `||` také vypočítá logický operátor OR jeho operandy, ale nebude vyhodnocení druhého operandu, jestli je první operand vyhodnocen jako `true`.

Pro operandy integrální typy `|` operátor výpočetní prostředí [bitové logické OR](bitwise-and-shift-operators.md#logical-or-operator-) z operandů.

## <a name="conditional-logical-and-operator-ampamp"></a>Podmíněné logického operátoru AND &amp;&amp;

Podmíněné logického operátoru AND `&&`, označované také jako "krátký cyklus" logického operátoru AND, vypočítá logický operátor AND operandů. Výsledek `x && y` je `true` Pokud mají oba `x` a `y` vyhodnotit `true`. V opačném případě je výsledek `false`. Pokud je první operand vyhodnocen jako `false`, není vyhodnocen Druhý operand.

V následujícím příkladu, druhý operand `&&` operátor je volání metody, které se neprovádí, pokud je první operand vyhodnocen jako `false`:

[!code-csharp-interactive[conditional logical AND](~/samples/snippets/csharp/language-reference/operators/LogicalOperators.cs#ConditionalAnd)]

[Logického operátoru AND](#logical-and-operator-) `&` také vypočítá logický operátor a jeho operandy, ale vždy vyhodnotí oba operandy.

## <a name="conditional-logical-or-operator-"></a>Podmíněné logického operátoru OR ||

Podmíněné logického operátoru OR `||`, označované také jako "krátký cyklus" logického operátoru OR, vypočítá logický operátor OR operandů. Výsledek `x || y` je `true` Pokud `x` nebo `y` vyhodnotí jako `true`. V opačném případě je výsledek `false`. Pokud je první operand vyhodnocen jako `true`, není vyhodnocen Druhý operand.

V následujícím příkladu, druhý operand `||` operátor je volání metody, které se neprovádí, pokud je první operand vyhodnocen jako `true`:

[!code-csharp-interactive[conditional logical OR](~/samples/snippets/csharp/language-reference/operators/LogicalOperators.cs#ConditionalOr)]

[Logického operátoru OR](#logical-or-operator-) `|` také vypočítá logický operátor OR jeho operandy, ale vždy vyhodnotí oba operandy.

## <a name="nullable-boolean-logical-operators"></a>Logická logické operátory s povolenou hodnotou Null

Pro `bool?` operandy, `&` a `|` operátory podporu logiky s hodnotou tři. Sémantika těchto operátorů je definována v následující tabulce:  
  
|x|y|x & y|x&#124;y|  
|----|----|----|----|  
|true|true|true|true|  
|true|false|false|true|  
|true|null|null|true|  
|false|true|false|true|  
|false|false|false|false|  
|false|null|false|null|  
|null|true|null|true|  
|null|false|false|null|  
|null|null|null|null|  

Tyto operátory chování se liší od chování typické operátor s typy s možnou hodnotou Null. Obvykle operátor, který je definován pro operandy typu hodnoty je také možné s operandy odpovídající typ s možnou hodnotou Null. Takové operátor vytvoří `null` Pokud kterýkoli z operandů `null`. Ale `&` a `|` operátory lze vytvořit jinou hodnotu než null, i v případě, že jeden z operandů je `null`. Další informace o chování operátoru s typy s možnou hodnotou Null, najdete v článku [operátory](../../programming-guide/nullable-types/using-nullable-types.md#operators) část [použití typů s povolenou hodnotou Null](../../programming-guide/nullable-types/using-nullable-types.md) článku.

Můžete také použít `!` a `^` operátory se `bool?` operandy, jako v následujícím příkladu:

[!code-csharp-interactive[lifted negation and xor](~/samples/snippets/csharp/language-reference/operators/LogicalOperators.cs#WithNullableBoolean)]

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

s tím rozdílem, že `x` se jenom vyhodnotí jednou.

`&`, `|`, A `^` podporují operátory složeného přiřazení jako v následujícím příkladu:

[!code-csharp-interactive[compound assignment](~/samples/snippets/csharp/language-reference/operators/LogicalOperators.cs#CompoundAssignment)]

Podmíněné logické operátory `&&` a `||` nepodporují složeného přiřazení.

## <a name="operator-precedence"></a>Priorita operátorů

V následujícím seznamu objednávek od nejvyšší priority k nejnižší logické operátory:

- Logický operátor negace `!`
- Logický operátor AND `&`
- Logické exkluzivní OR – operátor `^`
- Logický operátor OR `|`
- Podmíněné logického operátoru AND `&&`
- Podmíněné logický operátor OR `||`

Použít závorky, `()`, chcete-li změnit pořadí vyhodnocování stanovené prioritou operátorů:

[!code-csharp-interactive[operator precedence](~/samples/snippets/csharp/language-reference/operators/LogicalOperators.cs#Precedence)]

Pro úplný seznam C# operátory seřazené podle úrovně priority, naleznete v tématu [ C# operátory](index.md).

## <a name="operator-overloadability"></a>Overloadability – operátor

Uživatelem definovaný typ může [přetížení](../keywords/operator.md) `!`, `&`, `|`, a `^` operátory. Pokud je binární operátor přetížen, je také implicitně přetížené odpovídající operátor složeného přiřazení. Uživatelem definovaný typ nejde explicitně přetížit operátor složeného přiřazení.

Uživatelem definovaný typ nejde přetížit podmíněné logické operátory `&&` a `||`. Ale pokud přetížení uživatelem definovaného typu [operátory true a false](true-false-operators.md) a `&` nebo `|` operátor určitým způsobem, `&&` nebo `||` operace, respektive, může být vyhodnocen pro operandy typu. Další informace najdete v tématu [podmíněné logické operátory definované uživatelem](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) část [ C# specifikace jazyka](~/_csharplang/spec/introduction.md).

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace najdete v následující částech [ C# specifikace jazyka](~/_csharplang/spec/introduction.md):

- [Logický operátor negace](~/_csharplang/spec/expressions.md#logical-negation-operator)
- [Logické operátory](~/_csharplang/spec/expressions.md#logical-operators)
- [Podmíněné logické operátory](~/_csharplang/spec/expressions.md#conditional-logical-operators)
- [Složené přiřazení](~/_csharplang/spec/expressions.md#compound-assignment)

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka C#](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [Operátory jazyka C#](index.md)
- [Bitový operátor a operátory posunutí](bitwise-and-shift-operators.md)
