---
title: Bitové operátory and Shift – reference jazyka C#
description: Přečtěte si o operátorech jazyka C#, které provádějí bitové logické nebo posunuté operace s operandy integrálních typů.
ms.date: 04/18/2019
author: pkulikov
f1_keywords:
- ~_CSharpKeyword
- <<_CSharpKeyword
- '>>_CSharpKeyword'
- '&_CSharpKeyword'
- ^_CSharpKeyword
- '|_CSharpKeyword'
- <<=_CSharpKeyword
- '>>=_CSharpKeyword'
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
ms.openlocfilehash: 99181855fdf8e937676e44e8b347510f9405aa3d
ms.sourcegitcommit: ef50c99928183a0bba75e07b9f22895cd4c480f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/07/2020
ms.locfileid: "87916907"
---
# <a name="bitwise-and-shift-operators-c-reference"></a>Bitové operátory and Shift (Referenční dokumentace jazyka C#)

Následující operátory provádějí operace bitového nebo posunutí s operandy [integrálních číselných typů](../builtin-types/integral-numeric-types.md) nebo typu [znaku](../builtin-types/char.md) :

- Unární [ `~` (bitový doplněk)](#bitwise-complement-operator-) – operátor
- Binární [ `<<` (levý SHIFT)](#left-shift-operator-) a [ `>>` (posun doprava)](#right-shift-operator-) operátory posunutí
- Binary [ `&` (Logical and)](#logical-and-operator-), [ `|` (Logical or)](#logical-or-operator-)a [ `^` (Logical or)](#logical-exclusive-or-operator-) – operátory

Tyto operátory jsou definovány pro `int` typy, `uint` , a `long` `ulong` . Pokud jsou oba operandy jiné celočíselné typy ( `sbyte` , `byte` , `short` , `ushort` nebo `char` ), jejich hodnoty jsou převedeny na `int` typ, což je také výsledný typ operace. Pokud jsou operandy různých integrálních typů, jejich hodnoty jsou převedeny na nejbližší obsahující celočíselný typ. Další informace naleznete v části [numerické propagace](~/_csharplang/spec/expressions.md#numeric-promotions) [specifikace jazyka C#](~/_csharplang/spec/introduction.md).

`&`Operátory, `|` a `^` jsou definovány také pro operandy `bool` typu. Další informace naleznete v tématu logické [logické operátory](boolean-logical-operators.md).

Operace bitového a posunutí nikdy nezpůsobí přetečení a vytvářejí stejné výsledky v [zaškrtnutých a nekontrolovaných](../keywords/checked-and-unchecked.md) kontextech.

## <a name="bitwise-complement-operator-"></a>Operátor bitového doplňku ~

`~`Operátor vytvoří bitový doplněk svého operandu převrácením každého bitu:

[!code-csharp-interactive[bitwise NOT](snippets/shared/BitwiseAndShiftOperators.cs#BitwiseComplement)]

Můžete také použít `~` symbol k deklaraci finalizační metody. Další informace naleznete v tématu [finalizační metody](../../programming-guide/classes-and-structs/destructors.md).

## <a name="left-shift-operator-"></a>Operátor posunutí doleva\<\<

`<<`Operátor posune levý operand vlevo o [počet bitů definovaných operandem na pravé straně](#shift-count-of-the-shift-operators).

Operace Left posunutí zahodí horních bitů, které jsou mimo rozsah výsledného typu, a nastavuje prázdné bitové pozice v dolním pořadí na nulu, jak ukazuje následující příklad:

[!code-csharp-interactive[left shift](snippets/shared/BitwiseAndShiftOperators.cs#LeftShift)]

Protože operátory posunutí jsou definovány pouze pro `int` typy, `uint` , a `long` `ulong` , výsledek operace vždy obsahuje alespoň 32 bitů. Pokud je levý operand jiného integrálního typu ( `sbyte` , `byte` ,, `short` `ushort` nebo `char` ), jeho hodnota je převedena na `int` typ, jak ukazuje následující příklad:

[!code-csharp-interactive[left shift with promotion](snippets/shared/BitwiseAndShiftOperators.cs#LeftShiftPromoted)]

Informace o tom, jak operátor na pravé straně `<<` operátoru definuje počet posunutí, naleznete v oddílu posunutí [operátorů Shift](#shift-count-of-the-shift-operators) .

## <a name="right-shift-operator-"></a>Operátor posunutí doprava >>

`>>`Operátor posune levý operand vpravo o [počet bitů definovaných operandem na pravé straně](#shift-count-of-the-shift-operators).

Operace pravého posunutí zahodí bity nízkého řádu, jak ukazuje následující příklad:

[!code-csharp-interactive[right shift](snippets/shared/BitwiseAndShiftOperators.cs#RightShift)]

Horní pořadí prázdných bitových pozic je nastaveno na základě typu levého operandu následujícím způsobem:

- Pokud je levý operand typu `int` nebo `long` , operátor pravého posunutí provede *aritmetický* posun: hodnota nejvýznamnějšího bitu (bit znaménka) levého operandu je rozšířena na horní pořadí prázdných bitových pozic. To znamená, že horní pozice prázdných pozic je nastavena na hodnotu nula, je-li operand na levé straně nezáporný a je-li záporná, nastavte na jeden.

  [!code-csharp-interactive[arithmetic right shift](snippets/shared/BitwiseAndShiftOperators.cs#ArithmeticRightShift)]

- Pokud je levý operand typu `uint` nebo `ulong` , operátor pravého posunutí provede *logický* posun: horní pořadí prázdných bitových pozic je vždy nastaveno na hodnotu nula.

  [!code-csharp-interactive[logical right shift](snippets/shared/BitwiseAndShiftOperators.cs#LogicalRightShift)]

Informace o tom, jak operátor na pravé straně `>>` operátoru definuje počet posunutí, naleznete v oddílu posunutí [operátorů Shift](#shift-count-of-the-shift-operators) .

## <a name="logical-and-operator-amp"></a><a name="logical-and-operator-"></a>Logický operátor AND&amp;

`&`Operátor vypočítá bitovou logickou logickou a jeho operandy:

[!code-csharp-interactive[bitwise AND](snippets/shared/BitwiseAndShiftOperators.cs#BitwiseAnd)]

Pro `bool` operandy `&` operátor vypočítá [logickou a](boolean-logical-operators.md#logical-and-operator-) jeho operandy. Unární `&` operátor je [operátor address-of](pointer-related-operators.md#address-of-operator-).

## <a name="logical-exclusive-or-operator-"></a>Logický exkluzivní operátor OR ^

`^`Operátor Vypočítá bitový logický operátor OR, označovaný také jako bitový logický operátor XOR, z jeho operandů:

[!code-csharp-interactive[bitwise XOR](snippets/shared/BitwiseAndShiftOperators.cs#BitwiseXor)]

U `bool` operandů `^` operátor vypočítá [logickou výlučnou nebo](boolean-logical-operators.md#logical-exclusive-or-operator-) jeho operandy.

## <a name="logical-or-operator-"></a>Logický operátor OR |

`|`Operátor vypočítá bitovou logickou nebo jeho operandy:

[!code-csharp-interactive[bitwise OR](snippets/shared/BitwiseAndShiftOperators.cs#BitwiseOr)]

Pro `bool` operandy `|` operátor vypočítá [logickou nebo](boolean-logical-operators.md#logical-or-operator-) jeho operandy.

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

Následující příklad ukazuje použití složeného přiřazení s bitovým operátorem and Shift:

[!code-csharp-interactive[compound assignment](snippets/shared/BitwiseAndShiftOperators.cs#CompoundAssignment)]

Z důvodu [numerických propagačních akcí](~/_csharplang/spec/expressions.md#numeric-promotions) `op` nemusí být výsledek operace implicitně převoditelný na typ `T` `x` . V takovém případě, pokud `op` je předdefinovaný operátor a výsledek operace je explicitně převoditelné na typ `T` `x` , je složený výraz přiřazení formuláře `x op= y` ekvivalentní s `x = (T)(x op y)` tím rozdílem, že `x` je pouze vyhodnocen pouze jednou. Následující příklad ukazuje toto chování:

[!code-csharp-interactive[compound assignment with cast](snippets/shared/BitwiseAndShiftOperators.cs#CompoundAssignmentWithCast)]

## <a name="operator-precedence"></a>Priorita operátorů

Následující seznam řadí operátory bitových operátorů and Shift počínaje nejvyšší prioritou až nejnižší:

- Operátor bitového doplňku`~`
- Operátory posunutí `<<` a`>>`
- Logický operátor AND`&`
- Logický exkluzivní operátor OR`^`
- Logický operátor OR`|`

Pomocí závorek `()` můžete změnit pořadí vyhodnocování stanovené předností operátorů:

[!code-csharp-interactive[operator precedence](snippets/shared/BitwiseAndShiftOperators.cs#Precedence)]

Úplný seznam operátorů jazyka C# seřazených podle priority úrovně naleznete v části [Priorita operátorů](index.md#operator-precedence) v článku [operátory jazyka c#](index.md) .

## <a name="shift-count-of-the-shift-operators"></a>Počet posunutí operátorů Shift

Pro operátory posunutí `<<` a `>>` musí být typ operandu na pravé straně `int` nebo typ, který má [předdefinovaný implicitní číselný převod](../builtin-types/numeric-conversions.md#implicit-numeric-conversions) na `int` .

Pro `x << count` výrazy a se `x >> count` skutečný počet posunutí závisí na typu následujícím `x` způsobem:

- Pokud `x` je typ `int` nebo, je `uint` počet posunutí definován pomocí dolního řádu *pět* bitů pravého operandu. To znamená, že počet posunutí je vypočítán z `count & 0x1F` (nebo `count & 0b_1_1111` ).

- Pokud `x` je typ `long` nebo, je `ulong` počet posunutí definován pomocí dolních *šesti* bitů operandu na pravé straně. To znamená, že počet posunutí je vypočítán z `count & 0x3F` (nebo `count & 0b_11_1111` ).

Následující příklad ukazuje toto chování:

[!code-csharp-interactive[shift count example](snippets/shared/BitwiseAndShiftOperators.cs#ShiftCount)]

> [!NOTE]
> Jak ukazuje předchozí příklad, výsledek operace posunutí může být nenulový, i když hodnota operandu na pravé straně je větší než počet bitů v operandu na levé straně.

## <a name="enumeration-logical-operators"></a>Logické operátory výčtu

`~`Operátory, `&` , a `|` `^` jsou podporovány také jakýmkoli [výčtovým](../builtin-types/enum.md) typem. Pro operandy se stejným výčtovým typem je logická operace provedena na odpovídajících hodnotách základního integrálního typu. Například pro jakýkoliv `x` a `y` Výčtový typ `T` s podkladovým typem `U` `x & y` výraz vytvoří stejný výsledek jako `(T)((U)x & (U)y)` výraz.

Obvykle používáte bitové logické operátory s výčtovým typem, který je definován pomocí atributu [Flags](xref:System.FlagsAttribute) . Další informace naleznete v části [výčtové typy jako bitové příznaky](../builtin-types/enum.md#enumeration-types-as-bit-flags) v článku [výčtové typy](../builtin-types/enum.md) .

## <a name="operator-overloadability"></a>Přetížení operátoru

Uživatelsky definovaný typ může [přetížit](operator-overloading.md) `~` operátory,,,, `<<` `>>` `&` `|` a `^` . Při přetížení binárního operátoru je také implicitně přetížen odpovídající operátor složeného přiřazení. Uživatelsky definovaný typ nemůže explicitně přetížit operátor složeného přiřazení.

Pokud uživatelsky definovaný typ `T` přetěžuje `<<` `>>` operátor OR, musí být typ operandu na levé straně `T` a typ operandu na pravé straně `int` .

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace naleznete v následujících oddílech [specifikace jazyka C#](~/_csharplang/spec/introduction.md):

- [Operátor bitového doplňku](~/_csharplang/spec/expressions.md#bitwise-complement-operator)
- [Operátory posunutí](~/_csharplang/spec/expressions.md#shift-operators)
- [Logické operátory](~/_csharplang/spec/expressions.md#logical-operators)
- [Složené přiřazení](~/_csharplang/spec/expressions.md#compound-assignment)
- [Číselné propagační akce](~/_csharplang/spec/expressions.md#numeric-promotions)

## <a name="see-also"></a>Viz také

- [Referenční dokumentace k jazyku C#](../index.md)
- [Operátory a výrazy v C#](index.md)
- [Logické operátory](boolean-logical-operators.md)
