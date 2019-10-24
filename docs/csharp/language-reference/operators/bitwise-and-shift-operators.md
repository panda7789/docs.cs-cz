---
title: Bitové operátory and Shift – C# referenční informace
description: Přečtěte C# si o operátorech, které provádějí bitové logické nebo posunuté operace s operandy integrálních typů.
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
ms.openlocfilehash: 0a251e8d04f31a736ee6acbf4b8e913cfb8ca6df
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72771725"
---
# <a name="bitwise-and-shift-operators-c-reference"></a>Operátory bitových a posunutí (C# referenční)

Následující operátory provádějí operace bitového nebo posunutí s operandy [integrálních typů](../builtin-types/integral-numeric-types.md):

- Unární operátor [`~` (bitový doplněk)](#bitwise-complement-operator-)
- Binární [`<<` (levý SHIFT)](#left-shift-operator-) a [`>>` (posunutí doprava)](#right-shift-operator-) – operátory posunu
- Binární [`&` (Logical and)](#logical-and-operator-), [`|` (Logical or)](#logical-or-operator-)a [`^` (Logical or)](#logical-exclusive-or-operator-) Operators

Tyto operátory jsou definovány pro typy `int`, `uint`, `long` a `ulong`. Pokud jsou oba operandy jiných integrálních typů (`sbyte`, `byte`, `short`, `ushort` nebo `char`), jejich hodnoty jsou převedeny na typ `int`, což je také výsledný typ operace. Pokud jsou operandy různých integrálních typů, jejich hodnoty jsou převedeny na nejbližší obsahující celočíselný typ. Další informace naleznete v části [Číselná propagace](~/_csharplang/spec/expressions.md#numeric-promotions) ve [ C# specifikaci jazyka](~/_csharplang/spec/introduction.md).

Operátory `&`, `|` a `^` jsou definovány také pro operandy `bool` typu. Další informace naleznete v tématu logické [logické operátory](boolean-logical-operators.md).

Operace bitového a posunutí nikdy nezpůsobí přetečení a vytvářejí stejné výsledky v [zaškrtnutých a nekontrolovaných](../keywords/checked-and-unchecked.md) kontextech.

## <a name="bitwise-complement-operator-"></a>Operátor bitového doplňku ~

Operátor `~` vytvoří bitový doplněk svého operandu převrácením každého bitu:

[!code-csharp-interactive[bitwise NOT](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#BitwiseComplement)]

K deklaraci finalizační metody můžete použít také symbol `~`. Další informace naleznete v tématu [finalizační metody](../../programming-guide/classes-and-structs/destructors.md).

## <a name="left-shift-operator-"></a>Operátor posunutí doleva \< \<

Operátor `<<` posune levý operand vlevo o počet bitů definovaných operandem na pravé straně.

Operace Left posunutí zahodí horních bitů, které jsou mimo rozsah výsledného typu, a nastavuje prázdné bitové pozice v dolním pořadí na nulu, jak ukazuje následující příklad:

[!code-csharp-interactive[left shift](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#LeftShift)]

Protože operátory posunutí jsou definovány pouze pro `int`, `uint`, `long` a `ulong` typy, výsledek operace vždy obsahuje alespoň 32 bitů. Pokud je levý operand jiného integrálního typu (`sbyte`, `byte`, `short`, `ushort` nebo `char`), jeho hodnota je převedena na typ `int`, jak ukazuje následující příklad:

[!code-csharp-interactive[left shift with promotion](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#LeftShiftPromoted)]

Informace o tom, jak operand pravého operátoru `<<` definuje počet posunutí, naleznete v části [posunutí operátorů Shift](#shift-count-of-the-shift-operators) .

## <a name="right-shift-operator-"></a>Operátor pravého posunutí > >

Operátor `>>` posune levý operand vpravo o počet bitů definovaných operandem na pravé straně.

Operace pravého posunutí zahodí bity nízkého řádu, jak ukazuje následující příklad:

[!code-csharp-interactive[right shift](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#RightShift)]

Horní pořadí prázdných bitových pozic je nastaveno na základě typu levého operandu následujícím způsobem:

- Pokud je levý operand typu [int](../builtin-types/integral-numeric-types.md) nebo [Long](../builtin-types/integral-numeric-types.md), operátor pravého posunutí provede *aritmetický* posun: hodnota nejvýznamnějšího bitu (bit znaménka) levého operandu je rozšířena na horní pořadí prázdných bitových pozic. To znamená, že horní pozice prázdných pozic je nastavena na hodnotu nula, je-li operand na levé straně nezáporný a je-li záporná, nastavte na jeden.

  [!code-csharp-interactive[arithmetic right shift](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#ArithmeticRightShift)]

- Pokud je levý operand typu [uint](../builtin-types/integral-numeric-types.md) nebo [ulong](../builtin-types/integral-numeric-types.md), provede operátor pravého posunutí *logický* posun: vysoké prázdné bitové pozice jsou vždy nastaveny na hodnotu nula.

  [!code-csharp-interactive[logical right shift](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#LogicalRightShift)]

Informace o tom, jak operand pravého operátoru `>>` definuje počet posunutí, naleznete v části [posunutí operátorů Shift](#shift-count-of-the-shift-operators) .

## <a name="logical-and-operator-"></a>Logický operátor AND &amp;

Operátor `&` vypočítá bitovou logickou a jeho operandy:

[!code-csharp-interactive[bitwise AND](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#BitwiseAnd)]

Pro operandy typu `bool` `&` operátor vypočítá [logickou a](boolean-logical-operators.md#logical-and-operator-) jeho operandy. Unární operátor `&` je [operátor address-of](pointer-related-operators.md#address-of-operator-).

## <a name="logical-exclusive-or-operator-"></a>Logický exkluzivní operátor OR ^

Operátor `^` Vypočítá bitový logický operátor exclusive OR, také označovaný jako bitový logický operátor XOR, z jeho operandů:

[!code-csharp-interactive[bitwise XOR](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#BitwiseXor)]

Pro operandy typu `bool` `^` operátor vypočítá [logickou výlučnou nebo](boolean-logical-operators.md#logical-exclusive-or-operator-) jeho operandy.

## <a name="logical-or-operator-"></a>Logický operátor OR |

Operátor `|` vypočítá bitovou logickou nebo jeho operandy:

[!code-csharp-interactive[bitwise OR](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#BitwiseOr)]

Pro operandy typu `bool` `|` operátor vypočítá [logickou nebo](boolean-logical-operators.md#logical-or-operator-) jeho operandy.

## <a name="compound-assignment"></a>Složené přiřazení

Pro binární operátor `op` se složený výraz přiřazení formuláře

```csharp
x op= y
```

je ekvivalentem

```csharp
x = x op y
```

s výjimkou, že `x` je vyhodnocena pouze jednou.

Následující příklad ukazuje použití složeného přiřazení s bitovým operátorem and Shift:

[!code-csharp-interactive[compound assignment](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#CompoundAssignment)]

Z důvodu [numerických propagačních akcí](~/_csharplang/spec/expressions.md#numeric-promotions)nemusí být výsledek operace `op` implicitně převoditelný na typ `T` `x`. V takovém případě, pokud je `op` předdefinovaným operátorem a výsledek operace je explicitně převoditelné na typ `T` `x`, výraz složeného přiřazení `x op= y` formuláře je ekvivalentní `x = (T)(x op y)` , s výjimkou toho, že `x` vyhodnocována pouze jednou. Následující příklad ukazuje toto chování:

[!code-csharp-interactive[compound assignment with cast](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#CompoundAssignmentWithCast)]

## <a name="operator-precedence"></a>Priorita operátorů

Následující seznam řadí operátory bitových operátorů and Shift počínaje nejvyšší prioritou až nejnižší:

- Operátor bitového doplňku `~`
- Operátory posunutí `<<` a `>>`
- Logický operátor AND `&`
- @No__t_0 logický exkluzivní operátor OR
- Logický operátor OR `|`

Chcete-li změnit pořadí vyhodnocování stanovené předností operátorů, použijte závorky `()`:

[!code-csharp-interactive[operator precedence](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#Precedence)]

Úplný seznam C# operátorů seřazených podle priority úrovně naleznete v tématu [ C# operátory](index.md).

## <a name="shift-count-of-the-shift-operators"></a>Počet posunutí operátorů Shift

Pro operátory Shift `<<` a `>>` musí být typ operandu na pravé straně [int](../builtin-types/integral-numeric-types.md) nebo typ, který má [předdefinovaný implicitní číselný převod](../builtin-types/numeric-conversions.md#implicit-numeric-conversions) na `int`.

Pro výrazy `x << count` a `x >> count` závisí skutečný počet posunutí na typ `x` následujícím způsobem:

- Pokud typ `x` je [int](../builtin-types/integral-numeric-types.md) nebo [uint](../builtin-types/integral-numeric-types.md), počet posunutí je definován pomocí *pěti* bitů pravého operandu v dolním pořadí. To znamená, že počet posunutí je vypočítán z `count & 0x1F` (nebo `count & 0b_1_1111`).

- Pokud je typ `x` [Long](../builtin-types/integral-numeric-types.md) nebo [ulong](../builtin-types/integral-numeric-types.md), je počet posunutí definován v dolním *šesti* bitech operandu na pravé straně. To znamená, že počet posunutí je vypočítán z `count & 0x3F` (nebo `count & 0b_11_1111`).

Následující příklad ukazuje toto chování:

[!code-csharp-interactive[shift count example](~/samples/csharp/language-reference/operators/BitwiseAndShiftOperators.cs#ShiftCount)]

## <a name="enumeration-logical-operators"></a>Logické operátory výčtu

Operátory `~`, `&`, `|` a `^` jsou definovány také pro libovolný typ [výčtu](../keywords/enum.md) . U operandů stejného výčtového typu je logická operace provedena na odpovídajících hodnotách základního integrálního typu. Například pro jakékoli `x` a `y` typu výčtu `T` s podkladovým typem `U` výraz `x & y` vytvoří stejný výsledek jako výraz `(T)((U)x & (U)y)`.

Obvykle používáte bitové logické operátory s výčtovým typem, který je definován pomocí atributu [Flags](xref:System.FlagsAttribute) . Další informace naleznete v části [výčtové typy jako bitové příznaky](../../programming-guide/enumeration-types.md#enumeration-types-as-bit-flags) v článku [výčtové typy](../../programming-guide/enumeration-types.md) .

## <a name="operator-overloadability"></a>Přetížení operátoru

Uživatelsky definovaný typ může [přetížit](operator-overloading.md) operátory `~`, `<<`, `>>`, `&`, `|` a `^`. Při přetížení binárního operátoru je také implicitně přetížen odpovídající operátor složeného přiřazení. Uživatelsky definovaný typ nemůže explicitně přetížit operátor složeného přiřazení.

Pokud uživatelsky definovaný typ `T` přetížení operátoru `<<` nebo `>>`, musí být typ operandu na levé straně `T` a typ operandu na pravé straně musí být `int`.

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace najdete v následujících oddílech [ C# specifikace jazyka](~/_csharplang/spec/introduction.md):

- [Operátor bitového doplňku](~/_csharplang/spec/expressions.md#bitwise-complement-operator)
- [Operátory posunutí](~/_csharplang/spec/expressions.md#shift-operators)
- [Logické operátory](~/_csharplang/spec/expressions.md#logical-operators)
- [Složené přiřazení](~/_csharplang/spec/expressions.md#compound-assignment)
- [Číselné propagační akce](~/_csharplang/spec/expressions.md#numeric-promotions)

## <a name="see-also"></a>Viz také:

- [C#odkaz](../index.md)
- [Operátory jazyka C#](index.md)
- [Logické logické operátory](boolean-logical-operators.md)
