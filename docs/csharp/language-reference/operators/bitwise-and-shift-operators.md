---
title: Bitové a směny operátory - C# odkaz
description: Další informace o operátorech jazyka C#, které provádějí bitové logické operace nebo operace směny s operandy integrálních typů.
ms.date: 04/18/2019
author: pkulikov
f1_keywords:
- ~_CSharpKeyword
- <<_CSharpKeyword
- '>>_CSharpKeyword'
- '&_CSharpKeyword'
- ^_CSharpKeyword
- '|_CSharpKeyword'
helpviewer_keywords:
- bitwise logical operators [C#]
- shift operators [C#]
- tilde operator [C#]
- one's complement operator [C#]
- bitwise complement operator [C#]
- ~ operator [C#]
- left shift operator [C#]
- << operator [C#]
- right shift operator [C#]
- '>> operator [C#]'
- bitwise logical AND operator [C#]
- ampersand operator [C#]
- '& operator [C#]'
- bitwise logical exclusive OR operator [C#]
- bitwise logical XOR operator [C#]
- ^ operator [C#]
- bitwise logical OR operator [C#]
- '| operator [C#]'
ms.openlocfilehash: 54198368672e0c9324210a232c7851b5a90402cb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399264"
---
# <a name="bitwise-and-shift-operators-c-reference"></a>Bitové operátory a operátory směny (odkaz C#)

Následující operátory provádějí bitové operace nebo operace směny s operandy [integrálních číselných typů](../builtin-types/integral-numeric-types.md) nebo typu [znaku:](../builtin-types/char.md)

- Operátor Unární [ `~` (bitový doplněk)](#bitwise-complement-operator-)
- Binární [ `<<` (levý posun)](#left-shift-operator-) a [ `>>` (posun vpravo)](#right-shift-operator-) operátory posunu
- Binární [ `&` (logické OPERÁTOR)](#logical-and-operator-) [ `|` , (logické OR)](#logical-or-operator-)a [ `^` (logické výhradní OPERÁTORy OR)](#logical-exclusive-or-operator-)

Tyto hospodářské subjekty `int` `uint`jsou `long`definovány pro , , , a `ulong` typy. Pokud jsou oba operandy jiných`sbyte` `byte`integrálních typů ( , , `short`, `ushort`, nebo `char`), jejich hodnoty jsou převedeny na `int` typ, který je také typ výsledku operace. Pokud operandy jsou různé integrální typy, jejich hodnoty jsou převedeny na nejbližší obsahující integrální typ. Další informace naleznete v části [Numerické propagační akce](~/_csharplang/spec/expressions.md#numeric-promotions) ve [specifikaci jazyka C#](~/_csharplang/spec/introduction.md).

V `&` `|`, `^` a operátory jsou také definovány pro operandy `bool` typu. Další informace naleznete v [tématu Logické operátory logické .](boolean-logical-operators.md)

Bitové operace a operace posunu nikdy nezpůsobí přetečení a v [kontrolovaných a nekontrolovaných](../keywords/checked-and-unchecked.md) kontextech vytvoří stejné výsledky.

## <a name="bitwise-complement-operator-"></a>Bitový operátor komplementu ~

Operátor `~` vytváří bitový doplněk svého operandu obrácením každého bitu:

[!code-csharp-interactive[bitwise NOT](snippets/BitwiseAndShiftOperators.cs#BitwiseComplement)]

`~` Symbol můžete také použít k deklarování finalizačních metod. Další informace naleznete v tématu [Finalizers](../../programming-guide/classes-and-structs/destructors.md).

## <a name="left-shift-operator-"></a>Operátor posunu doleva\<\<

Operátor `<<` posune svůj levý operand doleva podle [počtu bitů definovaných jeho pravostranný operand](#shift-count-of-the-shift-operators).

Operace po sazí po levém posunu zahodí bity vyššího řádu, které jsou mimo rozsah typu výsledek, a nastaví prázdné bitové pozice nízkého řádu na nulu, jak ukazuje následující příklad:

[!code-csharp-interactive[left shift](snippets/BitwiseAndShiftOperators.cs#LeftShift)]

Vzhledem k tomu, že `int` `uint`operátory směny jsou definovány pouze pro , , `long`a `ulong` typy, výsledek operace vždy obsahuje alespoň 32 bitů. Pokud je levostranný operand jiného `byte` `short`integrálního typu (`sbyte`, `int` , , `ushort`, nebo `char`), jeho hodnota je převedena na typ, jak ukazuje následující příklad:

[!code-csharp-interactive[left shift with promotion](snippets/BitwiseAndShiftOperators.cs#LeftShiftPromoted)]

Informace o tom, jak pravostranný `<<` operand operátordefinuje počet směn, naleznete v části [Počet směn operátorů směny.](#shift-count-of-the-shift-operators)

## <a name="right-shift-operator-"></a> >> operátora s pravou směnou

Obsluha `>>` posune svůj levý operand doprava o [počet bitů definovaný jeho pravostranný operand](#shift-count-of-the-shift-operators).

Operace pravého posunu zahodí bity nižšího řádu, jak ukazuje následující příklad:

[!code-csharp-interactive[right shift](snippets/BitwiseAndShiftOperators.cs#RightShift)]

Pozice prázdných bitů vyššího řádu jsou nastaveny na základě typu levého operandu takto:

- Pokud je levá operand `int` typu `long`nebo , operátor pravého posunu provede *aritmetický* posun: hodnota nejvýznamnějšího bitu (znaménkový bit) levého operandu je rozšířena do prázdných bitových pozic vyššího řádu. To znamená, že pozice prázdného bitu vyššího řádu jsou nastaveny na nulu, pokud je levá operand nezáporná a nastavena na hodnotu jedna, pokud je záporná.

  [!code-csharp-interactive[arithmetic right shift](snippets/BitwiseAndShiftOperators.cs#ArithmeticRightShift)]

- Pokud je levostranný operand typu `uint` nebo `ulong`, operátor pravého posunu provede *logický* posun: pozice prázdných bitů vyššího řádu jsou vždy nastaveny na nulu.

  [!code-csharp-interactive[logical right shift](snippets/BitwiseAndShiftOperators.cs#LogicalRightShift)]

Informace o tom, jak pravostranný `>>` operand operátordefinuje počet směn, naleznete v části [Počet směn operátorů směny.](#shift-count-of-the-shift-operators)

## <a name="logical-and-operator-"></a>Logický operátor AND&amp;

Operátor `&` vypočítá bitové logické and jeho operandů:

[!code-csharp-interactive[bitwise AND](snippets/BitwiseAndShiftOperators.cs#BitwiseAnd)]

Pro `bool` operandy `&` operátor vypočítá [logické AND](boolean-logical-operators.md#logical-and-operator-) jeho operandů. Unární `&` operátor je [operátor adresy](pointer-related-operators.md#address-of-operator-).

## <a name="logical-exclusive-or-operator-"></a>Logický výhradní operátor OR ^

Operátor `^` vypočítá bitové logické výhradní OR, také známý jako bitové logické XOR, jeho operandů:

[!code-csharp-interactive[bitwise XOR](snippets/BitwiseAndShiftOperators.cs#BitwiseXor)]

Pro `bool` operandy `^` operátor vypočítá [logické výhradní OR](boolean-logical-operators.md#logical-exclusive-or-operator-) jeho operandů.

## <a name="logical-or-operator-"></a>Logický operátor OR |

Operátor `|` vypočítá bitové logické OR jeho operandů:

[!code-csharp-interactive[bitwise OR](snippets/BitwiseAndShiftOperators.cs#BitwiseOr)]

Pro `bool` operandy `|` operátor vypočítá [logické NEBO](boolean-logical-operators.md#logical-or-operator-) jeho operandů.

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

Následující příklad ukazuje použití složené přiřazení s bitové a shift operátory:

[!code-csharp-interactive[compound assignment](snippets/BitwiseAndShiftOperators.cs#CompoundAssignment)]

Z důvodu [číselných propagačních](~/_csharplang/spec/expressions.md#numeric-promotions) `op` akcí nemusí být výsledek operace `T` implicitně převoditelný na typ . `x` V takovém případě, `op` pokud je předdefinovaný operátor a výsledek operace je `T` `x`explicitně převoditelný na `x op= y` typ `x = (T)(x op y)`, složený `x` výraz přiřazení formuláře je ekvivalentní , s výjimkou, že je vyhodnocenpouze jednou. Následující příklad ukazuje, že chování:

[!code-csharp-interactive[compound assignment with cast](snippets/BitwiseAndShiftOperators.cs#CompoundAssignmentWithCast)]

## <a name="operator-precedence"></a>Priorita operátorů

Následující seznam objednává bitové a operátory směny od nejvyšší priority k nejnižší:

- Bitový operátor komplementu`~`
- Operátory `<<` směn a`>>`
- Logický operátor AND`&`
- Logický výhradní operátor OR`^`
- Logický operátor OR`|`

Pomocí závorek `()`, můžete změnit pořadí hodnocení uloženého prioritou operátoru:

[!code-csharp-interactive[operator precedence](snippets/BitwiseAndShiftOperators.cs#Precedence)]

Úplný seznam operátorů jazyka C# seřazené podle úrovně priority naleznete v části [Priorita operátora](index.md#operator-precedence) v článku [operátorů jazyka C#.](index.md)

## <a name="shift-count-of-the-shift-operators"></a>Počet směn operátorů směn

Pro operátory `<<` `>>`směny a , typ pravéoperand `int` musí být nebo typ, který `int`má [předdefinovaný implicitní číselný převod](../builtin-types/numeric-conversions.md#implicit-numeric-conversions) na .

`x << count` Pro `x >> count` a výrazy skutečný počet směn závisí `x` na typu následujícím:

- Pokud `x` je typ `int` `uint`nebo , počet směn je definován low-order *pět* bitů pravé operand. To znamená, že počet směn `count & 0x1F` se `count & 0b_1_1111`vypočítá z (nebo).

- Pokud `x` je typ `long` `ulong`nebo , počet směn je definován low-order *šest* bitů pravé operand. To znamená, že počet směn `count & 0x3F` se `count & 0b_11_1111`vypočítá z (nebo).

Následující příklad ukazuje, že chování:

[!code-csharp-interactive[shift count example](snippets/BitwiseAndShiftOperators.cs#ShiftCount)]

> [!NOTE]
> Jak ukazuje předchozí příklad, výsledek operace posunu může být nenulový i v případě, že hodnota pravostranného operandu je větší než počet bitů v levém operandu.

## <a name="enumeration-logical-operators"></a>Logické operátory výčtu

Všechny `~` `&`typy `|`výčtů jsou podporovány také libovolným typem `^` [výčtu](../builtin-types/enum.md) , , a operátory. Pro operandy stejného typu výčtu se provádí logická operace na odpovídající hodnoty základního integrálního typu. Například pro `x` všechny `y` a typu `T` výčtu s `U`podkladovým typem `x & y` výraz vytváří `(T)((U)x & (U)y)` stejný výsledek jako výraz.

Obvykle používáte bitové logické operátory s typem výčtu, který je definován atributem [Flags.](xref:System.FlagsAttribute) Další informace naleznete v části [Výčet jako bitové příznaky](../builtin-types/enum.md#enumeration-types-as-bit-flags) v článku [Typy výčtu.](../builtin-types/enum.md)

## <a name="operator-overloadability"></a>Přetížení obsluhy

Uživatelem definovaný typ může `~` `<<` [přetížit](operator-overloading.md) operátory , , `>>` `&`, `|`, a. `^` Když je přetížený binární operátor, odpovídající složený operátor přiřazení je také implicitně přetížena. Uživatelem definovaný typ nemůže explicitně přetížit operátor složeného přiřazení.

Pokud uživatelem definovaný `T` typ `<<` přetíží operátor nebo, `>>` musí být `T` typ levého operandu a typ `int`pravostranného operandu .

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace naleznete v následujících částech [specifikace jazyka C#](~/_csharplang/spec/introduction.md):

- [Bitový operátor komplementu](~/_csharplang/spec/expressions.md#bitwise-complement-operator)
- [Operátory posunutí](~/_csharplang/spec/expressions.md#shift-operators)
- [Logické operátory](~/_csharplang/spec/expressions.md#logical-operators)
- [Složené přiřazení](~/_csharplang/spec/expressions.md#compound-assignment)
- [Číselné propagační akce](~/_csharplang/spec/expressions.md#numeric-promotions)

## <a name="see-also"></a>Viz také

- [Referenční dokumentace k jazyku C#](../index.md)
- [Operátory jazyka C#](index.md)
- [Logické operátory](boolean-logical-operators.md)
