---
title: Logické operátory logické hodnoty - odkaz jazyka C#
description: Další informace o operátorech jazyka C#, které provádějí logické negace, konjunkce (AND) a včetně a výhradní chod (OR) operace s logickými operandy.
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
ms.openlocfilehash: 930329b922f585ac4763e6a66d3b192ae839f14f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399495"
---
# <a name="boolean-logical-operators-c-reference"></a>Logické operátory logické položky (odkaz Jazyka C#)

Následující operátory provádějí logické operace s [buč](../builtin-types/bool.md) operandy:

- Unární [ `!` (logické negace)](#logical-negation-operator-) operátor.
- Binární [ `&` (logické AND)](#logical-and-operator-) [ `|` , (logické OR)](#logical-or-operator-)a [ `^` (logické výhradní OR)](#logical-exclusive-or-operator-) operátory. Tyto operátory vždy vyhodnocují oba operandy.
- Binární [ `&&` (podmíněné logické OPERÁTORy)](#conditional-logical-and-operator-) a [ `||` (podmíněné logické OPERÁTORy).](#conditional-logical-or-operator-) Tyto operátory vyhodnocují pravostranný operand pouze v případě, že je to nezbytné.

Pro operandy [integrálníčíselné typy](../builtin-types/integral-numeric-types.md), `&`, `|`a `^` operátory provádět bitové logické operace. Další informace naleznete v tématu [Bitwise and shift operators](bitwise-and-shift-operators.md).

## <a name="logical-negation-operator-"></a>Logický operátor negace !

Unární prefix `!` operátor vypočítá logické negace jeho operand. To znamená, že `true`vytvoří , pokud operand vyhodnotí `false`na , a `false`, pokud operand vyhodnotí: `true`

[!code-csharp-interactive[logical negation](snippets/BooleanLogicalOperators.cs#Negation)]

Počínaje C# 8.0, unární `!` přípona operátor je [null odpouštějící operátor](null-forgiving.md).

## <a name="logical-and-operator-"></a>Logický operátor AND&amp;

Operátor `&` vypočítá logické AND jeho operandů. Výsledkem `x & y` je `true` if `x` `y` both `true`a vyhodnotit na . V opačném případě `false`je výsledkem .

Operátor `&` vyhodnotí oba operandy i v případě, `false`že levá operand `false` vyhodnotí do , tak, aby výsledek operace je bez ohledu na hodnotu pravéoperand.

V následujícím příkladu je pravostranný `&` operand operátoru volání metody, které se provádí bez ohledu na hodnotu levého operandu:

[!code-csharp-interactive[logical AND](snippets/BooleanLogicalOperators.cs#And)]

[Podmíněný logický operátor](#conditional-logical-and-operator-) `&&` AND také vypočítá logické and jeho operandů, ale nevyhodnotí pravé operand, pokud levá `false`operand vyhodnotí .

Pro operandy [integrálních číselných typů](../builtin-types/integral-numeric-types.md) `&` operátor vypočítá [bitové logické and](bitwise-and-shift-operators.md#logical-and-operator-) jeho operandů. Unární `&` operátor je [operátor adresy](pointer-related-operators.md#address-of-operator-).

## <a name="logical-exclusive-or-operator-"></a>Logický výhradní operátor OR ^

Operátor `^` vypočítá logické výhradní NEBO, označované také jako logické XOR, jeho operandů. Výsledkem `x ^ y` `true` je, `x` pokud `true` vyhodnotí `y` a `x` vyhodnotí `false` `y` `false`, nebo `true`vyhodnotí a vyhodnotí . V opačném případě `false`je výsledkem . To znamená, `bool` že pro operandy `^` operátor vypočítá stejný výsledek jako operátor `!=` [nerovnosti](equality-operators.md#inequality-operator-) .

[!code-csharp-interactive[logical exclusive OR](snippets/BooleanLogicalOperators.cs#Xor)]

Pro operandy [integrálníčíselné typy](../builtin-types/integral-numeric-types.md)operátor `^` vypočítá [bitové logické exclusive OR](bitwise-and-shift-operators.md#logical-exclusive-or-operator-) jeho operandů.

## <a name="logical-or-operator-"></a>Logický operátor OR |

Operátor `|` vypočítá logické OR jeho operandů. Výsledkem `x | y` `true` je, `x` pokud `y` buď `true`nebo vyhodnotí . V opačném případě `false`je výsledkem .

Operátor `|` vyhodnotí oba operandy i v případě, `true`že levá operand `true` vyhodnotí do , tak, aby výsledek operace je bez ohledu na hodnotu pravéoperand.

V následujícím příkladu je pravostranný `|` operand operátoru volání metody, které se provádí bez ohledu na hodnotu levého operandu:

[!code-csharp-interactive[logical OR](snippets/BooleanLogicalOperators.cs#Or)]

[Podmíněný logický operátor](#conditional-logical-or-operator-) `||` OR také vypočítá logický operátor OR svých operandů, ale nevyhodnotí pravostranný operand, `true`pokud se levá operand vyhodnotí na .

Pro operandy [integrálních číselných typů](../builtin-types/integral-numeric-types.md) `|` operátor vypočítá [bitové logické OR](bitwise-and-shift-operators.md#logical-or-operator-) jeho operandů.

## <a name="conditional-logical-and-operator-"></a>Podmíněný logický operátor AND&amp;&amp;

Podmíněný logický operátor `&&`AND , označovaný také jako logický operátor AND "short-circuiting", vypočítá logické and jeho operandů. Výsledkem `x && y` je `true` if `x` `y` both `true`a vyhodnotit na . V opačném případě `false`je výsledkem . Pokud `x` je `false`vyhodnocena do , `y` není vyhodnocena.

V následujícím příkladu je pravostranný `&&` operand operátoru volání metody, které se neprovádí, pokud `false`se levá operand vyhodnotí na :

[!code-csharp-interactive[conditional logical AND](snippets/BooleanLogicalOperators.cs#ConditionalAnd)]

Logický [operátor](#logical-and-operator-) `&` AND také vypočítá logické and jeho operandy, ale vždy vyhodnotí oba operandy.

## <a name="conditional-logical-or-operator-"></a>Podmíněný logický operátor OR ||

Podmíněný logický operátor `||`OR , označovaný také jako logický operátor OR "short-circuiting", vypočítá logický operátor OR jeho operandů. Výsledkem `x || y` `true` je, `x` pokud `y` buď `true`nebo vyhodnotí . V opačném případě `false`je výsledkem . Pokud `x` je `true`vyhodnocena do , `y` není vyhodnocena.

V následujícím příkladu je pravostranný `||` operand operátoru volání metody, které se neprovádí, pokud `true`se levá operand vyhodnotí na :

[!code-csharp-interactive[conditional logical OR](snippets/BooleanLogicalOperators.cs#ConditionalOr)]

[Logický operátor](#logical-or-operator-) `|` OR také vypočítá logický operátor OR svých operandů, ale vždy vyhodnotí oba operandy.

## <a name="nullable-boolean-logical-operators"></a>Logické operátory logické hodnoty null

Pro `bool?` operandy `&` a `|` operátory podporují logiku se třemi hodnotami. Sémantiku těchto operátorů je definována následující tabulkou:  
  
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

Chování těchto operátorů se liší od typické chování operátoru s typy hodnot s hodnotou null. Operátor, který je definován pro operandy typu hodnoty, lze obvykle použít také s operandy odpovídajícího typu hodnoty s možnou hodnotou, kterou lze použít. Takový operátor vyprodukuje, `null` pokud některý z `null`jeho operandů vyhodnotí . Však `&` a `|` operátory můžete vyrábět nenull i v případě, `null`že jeden z operandů vyhodnotí . Další informace o chování operátoru s typy hodnot s možnou hodnotou s hodnotou null naleznete v části [Lifted operators](../builtin-types/nullable-value-types.md#lifted-operators) v článku [Typy hodnot S možnou hodnotou Null.](../builtin-types/nullable-value-types.md)

Můžete také použít `!` `^` a `bool?` operátory s operandy, jak ukazuje následující příklad:

[!code-csharp-interactive[lifted negation and xor](snippets/BooleanLogicalOperators.cs#WithNullableBoolean)]

Podmíněné logické `&&` `||` operátory a `bool?` nepodporují operandy.

## <a name="compound-assignment"></a>Složené přiřazení

Pro binární `op`operátor , složený výraz přiřazení formuláře

```csharp
x op= y
```

je ekvivalentem

```csharp
x = x op y
```

kromě `x` toho, že se vyhodnocuje pouze jednou.

Složené `&` `|`přiřazení `^` podporují , a operátory, jak ukazuje následující příklad:

[!code-csharp-interactive[compound assignment](snippets/BooleanLogicalOperators.cs#CompoundAssignment)]

Podmíněné logické `&&` `||` operátory a nepodporují složené přiřazení.

## <a name="operator-precedence"></a>Priorita operátorů

Následující seznam seřídí logické operátory od nejvyšší priority k nejnižší:

- Logický operátor negace`!`
- Logický operátor AND`&`
- Logický výhradní operátor OR`^`
- Logický operátor OR`|`
- Podmíněný logický operátor AND`&&`
- Podmíněný logický operátor OR`||`

Pomocí závorek `()`, můžete změnit pořadí hodnocení uloženého prioritou operátoru:

[!code-csharp-interactive[operator precedence](snippets/BooleanLogicalOperators.cs#Precedence)]

Úplný seznam operátorů jazyka C# seřazené podle úrovně priority naleznete v části [Priorita operátora](index.md#operator-precedence) v článku [operátorů jazyka C#.](index.md)

## <a name="operator-overloadability"></a>Přetížení obsluhy

Uživatelem definovaný typ může `!` `&` `|` [přetížit](operator-overloading.md) , , , a `^` operátory. Když je přetížený binární operátor, odpovídající složený operátor přiřazení je také implicitně přetížena. Uživatelem definovaný typ nemůže explicitně přetížit operátor složeného přiřazení.

Uživatelem definovaný typ nemůže přetížit podmíněné logické operátory `&&` a `||`. Pokud však uživatelem definovaný typ určitým způsobem přetíží [operátory true a false](true-false-operators.md) a operátor `&` nebo, `|` může být `&&` operace nebo `||` operace vyhodnocena pro operandy tohoto typu. Další informace naleznete v části [Uživatelem definované podmíněné logické operátory](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) [specifikace jazyka C#](~/_csharplang/spec/introduction.md).

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace naleznete v následujících částech [specifikace jazyka C#](~/_csharplang/spec/introduction.md):

- [Logický operátor negace](~/_csharplang/spec/expressions.md#logical-negation-operator)
- [Logické operátory](~/_csharplang/spec/expressions.md#logical-operators)
- [Podmíněné logické operátory](~/_csharplang/spec/expressions.md#conditional-logical-operators)
- [Složené přiřazení](~/_csharplang/spec/expressions.md#compound-assignment)

## <a name="see-also"></a>Viz také

- [Referenční dokumentace k jazyku C#](../index.md)
- [Operátory jazyka C#](index.md)
- [Bitové operátory a operátory bitového posunu](bitwise-and-shift-operators.md)
