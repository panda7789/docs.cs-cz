---
title: Bitové operátory a operátory posunutí - C# odkaz
description: Další informace o C# operátory, které provádějí operace bitový logický nebo operace posunutí se operandy integrální typy.
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
ms.openlocfilehash: c18a06971887049a443f0bd1af7c77610a787a27
ms.sourcegitcommit: eaa6d5cd0f4e7189dbe0bd756e9f53508b01989e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/07/2019
ms.locfileid: "67609943"
---
# <a name="bitwise-and-shift-operators-c-reference"></a>Bitový operátor a operátory posunutí (C# odkaz)

Následující operátory provádějí operace bitový nebo shift operací s operandy [celočíselných typů](../builtin-types/integral-numeric-types.md):

- Unární [ `~` (bitový doplněk)](#bitwise-complement-operator-) – operátor
- Binární [ `<<` (levý shift)](#left-shift-operator-) a [ `>>` (posunutí doprava)](#right-shift-operator-) operátory posunutí
- Binární [ `&` (logický operátor a)](#logical-and-operator-), [ `|` (logický operátor nebo)](#logical-or-operator-), a [ `^` (logické XOR)](#logical-exclusive-or-operator-) operátory

Tyto operátory jsou definovány pro `int`, `uint`, `long`, a `ulong` typy. Pokud jsou oba operandy jiné typy celých čísel (`sbyte`, `byte`, `short`, `ushort`, nebo `char`), jejich hodnoty se převedou na `int` typ, který je také typ výsledku operace. Když operandy jsou odlišnými typy celých čísel, jejich hodnoty se převedou na nejbližší obsahující integrálního typu. Další informace najdete v tématu [číselné propagace](~/_csharplang/spec/expressions.md#numeric-promotions) část [ C# specifikace jazyka](~/_csharplang/spec/introduction.md).

`&`, `|`, A `^` operátory jsou také definovány pro operandy `bool` typu. Další informace najdete v tématu [logické logické operátory](boolean-logical-operators.md).

Bitový operátor a operace posunutí nikdy způsobit přetečení a produkuje stejné výsledky v [zaškrtnuto a nezaškrtnuto](../keywords/checked-and-unchecked.md) kontexty.

## <a name="bitwise-complement-operator-"></a>Operátor bitového doplňku ~

`~` Operátor vytvoří bitový doplněk svého operandu přehozením každý bit:

[!code-csharp-interactive[bitwise NOT](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#BitwiseComplement)]

Můžete také použít `~` symbol finalizační metody deklarovat. Další informace najdete v tématu [finalizační metody](../../programming-guide/classes-and-structs/destructors.md).

## <a name="left-shift-operator-"></a>Operátor posunutí doleva \<\<

`<<` Operátor posune jeho levý operand doleva o počet bitů, které jsou určené jeho operand pravé strany.

Operace levého posunutí zahodí implikovaný bitů, které jsou mimo rozsah typu výsledku a nastaví nižšího řádu prázdný bitové pozice na nulu, jako v následujícím příkladu:

[!code-csharp-interactive[left shift](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#LeftShift)]

Protože operátory posunutí jsou určená jenom pro `int`, `uint`, `long`, a `ulong` obsahuje typy, výsledek operace vždy alespoň 32 bitů. Pokud levý operand je jiný celočíselný typ (`sbyte`, `byte`, `short`, `ushort`, nebo `char`), jeho hodnota je převedena na `int` typu, jak ukazuje následující příklad:

[!code-csharp-interactive[left shift with promotion](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#LeftShiftPromoted)]

Informace o tom, pravém operand `<<` operátor definuje počet posunů naleznete v tématu [Shift počet operátory posunutí](#shift-count-of-the-shift-operators) oddílu.

## <a name="right-shift-operator-"></a>Operátor pravého posunutí >>

`>>` Jeho levý operand operátoru přímo posune počet bitů, které jsou určené jeho zpracovával pravý operand.

Operace pravého posunutí zahodí bity nižšího řádu jako v následujícím příkladu:

[!code-csharp-interactive[right shift](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#RightShift)]

Nejvyšším prázdný bitové pozice jsou nastavena na základě typu levý operand následujícím způsobem:

- Pokud levý operand je typu [int](../builtin-types/integral-numeric-types.md) nebo [dlouhé](../builtin-types/integral-numeric-types.md), operátor pravého posunutí provádí *aritmetické* shift: hodnota nejvýznamnější bit (bit znaménka) Levý operand je postoupena do nejvyšším prázdný bitové pozice. To znamená, implikovaný prázdný bitové pozice jsou nastaveny na nulu pokud levý operand je nastaven na nezáporné a nastavit na jednu, pokud je záporné.

  [!code-csharp-interactive[arithmetic right shift](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#ArithmeticRightShift)]

- Pokud levý operand je typu [uint](../builtin-types/integral-numeric-types.md) nebo [ulong](../builtin-types/integral-numeric-types.md), operátor pravého posunutí provádí *logické* shift: nejvyšším prázdný bitové pozice jsou vždy nastaveny na hodnotu nula.

  [!code-csharp-interactive[logical right shift](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#LogicalRightShift)]

Informace o tom, pravém operand `>>` operátor definuje počet posunů naleznete v tématu [Shift počet operátory posunutí](#shift-count-of-the-shift-operators) oddílu.

## <a name="logical-and-operator-"></a> Logický operátor AND &amp;

`&` Vypočítá bitové logické AND jeho operandy operátoru:

[!code-csharp-interactive[bitwise AND](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#BitwiseAnd)]

Pro operandy `bool` typ, `&` operátor výpočetní prostředí [logický operátor AND](boolean-logical-operators.md#logical-and-operator-) z operandů. Unární `&` operátor je [operátoru address-of](pointer-related-operators.md#address-of-operator-).

## <a name="logical-exclusive-or-operator-"></a>Logický exkluzivní operátor OR ^

`^` Operátor vypočítá bitový logický exkluzivní OR označované také jako bitové logické XOR z operandů:

[!code-csharp-interactive[bitwise XOR](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#BitwiseXor)]

Pro operandy `bool` typ, `^` operátor výpočetní prostředí [logické XOR](boolean-logical-operators.md#logical-exclusive-or-operator-) z operandů.

## <a name="logical-or-operator-"></a>Logický operátor OR |

`|` Vypočítá bitové logické OR jeho operandy operátoru:

[!code-csharp-interactive[bitwise OR](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#BitwiseOr)]

Pro operandy `bool` typ, `|` operátor výpočetní prostředí [logický operátor OR](boolean-logical-operators.md#logical-or-operator-) z operandů.

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

Následující příklad ukazuje použití složeného přiřazení s bitovým a operátory posunutí:

[!code-csharp-interactive[compound assignment](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#CompoundAssignment)]

Z důvodu [číselné propagace](~/_csharplang/spec/expressions.md#numeric-promotions), výsledek `op` operace může být implicitně převést na typ `T` z `x`. V takovém případě pokud `op` je předdefinovaný operátor a výsledek operace je výslovně převeditelný na typ `T` z `x`, výraz složeného přiřazení formuláře `x op= y` je ekvivalentní `x = (T)(x op y)`, s výjimkou který `x` se jenom vyhodnotí jednou. Následující příklad ukazuje toto chování:

[!code-csharp-interactive[compound assignment with cast](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#CompoundAssignmentWithCast)]

## <a name="operator-precedence"></a>Priorita operátorů

Následující seznam objednávky bitové a operátory posunutí od nejvyšší priority k nejnižší:

- Operátor bitového doplňku `~`
- Operátory posunutí `<<` a `>>`
- Logický operátor AND `&`
- Logické exkluzivní OR – operátor `^`
- Logický operátor OR `|`

Použít závorky, `()`, chcete-li změnit pořadí vyhodnocování stanovené prioritou operátorů:

[!code-csharp-interactive[operator precedence](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#Precedence)]

Pro úplný seznam C# operátory seřazené podle úrovně priority, naleznete v tématu [ C# operátory](index.md).

## <a name="shift-count-of-the-shift-operators"></a>Počet posunů operátorů posunutí

Pro operátory posunutí `<<` a `>>`, musí být typu zpracovával pravý operand [int](../builtin-types/integral-numeric-types.md) nebo typ, který má [předdefinované implicitní převod čísla](../keywords/implicit-numeric-conversions-table.md) k `int`.

Pro `x << count` a `x >> count` výrazy, počet skutečné posunutí závisí na typu `x` následujícím způsobem:

- Pokud typ `x` je [int](../builtin-types/integral-numeric-types.md) nebo [uint](../builtin-types/integral-numeric-types.md), počet posunů je definován nižšího řádu *pět* bits operand pravé strany. To znamená, že počet posunů je vypočítán z `count & 0x1F` (nebo `count & 0b_1_1111`).

- Pokud typ `x` je [dlouhé](../builtin-types/integral-numeric-types.md) nebo [ulong](../builtin-types/integral-numeric-types.md), počet posunů je definován nižšího řádu *šest* bits operand pravé strany. To znamená, že počet posunů je vypočítán z `count & 0x3F` (nebo `count & 0b_11_1111`).

Následující příklad ukazuje toto chování:

[!code-csharp-interactive[shift count example](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#ShiftCount)]

## <a name="enumeration-logical-operators"></a>Výčet logické operátory

`~`, `&`, `|`, A `^` operátory jsou také definovány pro všechny [výčet](../keywords/enum.md) typu. Pro operandy stejný typ výčtu se provádí logické operace na odpovídající hodnoty základní celočíselného typu. Například pro všechny `x` a `y` výčtového typu `T` s podkladovým typem `U`, `x & y` výraz vytvoří stejný výsledek jako `(T)((U)x & (U)y)` výrazu.

Obvykle použijete bitové logické operátory s typem výčtu, která je definována s [příznaky](xref:System.FlagsAttribute) atribut. Další informace najdete v tématu [výčtové typy jako bitové příznaky](../../programming-guide/enumeration-types.md#enumeration-types-as-bit-flags) část [výčtové typy](../../programming-guide/enumeration-types.md) článku.

## <a name="operator-overloadability"></a>Overloadability – operátor

Uživatelem definovaný typ může [přetížení](operator-overloading.md) `~`, `<<`, `>>`, `&`, `|`, a `^` operátory. Pokud je binární operátor přetížen, je také implicitně přetížené odpovídající operátor složeného přiřazení. Uživatelem definovaný typ nejde explicitně přetížit operátor složeného přiřazení.

Pokud uživatelský typ `T` přetížení `<<` nebo `>>` operátoru musí být typu levý operand `T` a musí být typu zpracovával pravý operand `int`.

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace najdete v následující částech [ C# specifikace jazyka](~/_csharplang/spec/introduction.md):

- [Operátor bitového doplňku](~/_csharplang/spec/expressions.md#bitwise-complement-operator)
- [Operátory posunutí](~/_csharplang/spec/expressions.md#shift-operators)
- [Logické operátory](~/_csharplang/spec/expressions.md#logical-operators)
- [Složené přiřazení](~/_csharplang/spec/expressions.md#compound-assignment)
- [Číselné propagačních akcí](~/_csharplang/spec/expressions.md#numeric-promotions)

## <a name="see-also"></a>Viz také:

- [C#referenční dokumentace](../index.md)
- [Operátory jazyka C#](index.md)
- [Logická logické operátory](boolean-logical-operators.md)
