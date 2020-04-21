---
title: Aritmetické operátory - odkaz C#
description: Další informace o operátorech jazyka C#, které provádějí operace násobení, dělení, zbytek, sčítání a odčítání s číselnými typy.
ms.date: 03/27/2019
author: pkulikov
f1_keywords:
- ++_CSharpKeyword
- --_CSharpKeyword
- '*_CSharpKeyword'
- /_CSharpKeyword
- '%_CSharpKeyword'
- +_CSharpKeyword
- -_CSharpKeyword
helpviewer_keywords:
- arithmetic operators [C#]
- increment operator [C#]
- ++ operator [C#]
- decrement operator [C#]
- -- operator [C#]
- multiplication operator [C#]
- '* operator [C#]'
- division operator [C#]
- / operator [C#]
- remainder operator [C#]
- '% operator [C#]'
- addition operator [C#]
- + operator [C#]
- subtraction operator [C#]
- '- operator [C#]'
ms.openlocfilehash: ea9bf9e065b2953fd20e0503a19d1dc143064c5d
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/21/2020
ms.locfileid: "81738737"
---
# <a name="arithmetic-operators-c-reference"></a>Aritmetické operátory (odkaz C# )

Následující operátory provádějí aritmetické operace s operandy číselných typů:

- Unární [ `++` (přírůstek)](#increment-operator-), [ `--` (snížení)](#decrement-operator---), [ `+` (plus)](#unary-plus-and-minus-operators)a [ `-` (minus)](#unary-plus-and-minus-operators) operátory
- Binární [ `*` (násobení)](#multiplication-operator-), [ `/` (dělení)](#division-operator-), [ `%` (zbytek)](#remainder-operator-), [ `+` (sčítání)](#addition-operator-)a [ `-` (odčítání)](#subtraction-operator--) operátory

Tyto operátory jsou podporovány všechny [integrální](../builtin-types/integral-numeric-types.md) a [plovoucí desetinnou desetinnou desetinnou desetinnou](../builtin-types/floating-point-numeric-types.md) desetinnou hodnotu číselné typy.

## <a name="increment-operator-"></a>Operátor přírůstek ++

Unární přírůstek `++` operátor urychluje jeho operand o 1. Operand musí být proměnná, přístup k [vlastnostem](../../programming-guide/classes-and-structs/properties.md) nebo přístup [indexeru.](../../programming-guide/indexers/index.md)

Operátor přírůstek je podporován ve dvou formách: operátor `x++`přípona přírůstek , `++x`a operátor přírůstek předpony, .

### <a name="postfix-increment-operator"></a>Příponový operátor inkrementace

Výsledkem `x++` je hodnota `x` *před* operací, jak ukazuje následující příklad:

[!code-csharp-interactive[postfix increment](snippets/ArithmeticOperators.cs#PostfixIncrement)]

### <a name="prefix-increment-operator"></a>Operátor přírůstek předpony

Výsledkem `++x` je hodnota `x` *po* operaci, jak ukazuje následující příklad:

[!code-csharp-interactive[prefix increment](snippets/ArithmeticOperators.cs#PrefixIncrement)]

## <a name="decrement-operator---"></a>Operátor snížení --

Unární snížení operátor `--` sníží jeho operand o 1. Operand musí být proměnná, přístup k [vlastnostem](../../programming-guide/classes-and-structs/properties.md) nebo přístup [indexeru.](../../programming-guide/indexers/index.md)

Operátor snížení je podporován ve dvou formách: operátor snížení `x--`přípony a operátor snížení `--x`předpony .

### <a name="postfix-decrement-operator"></a>Příponový operátor dekrementace

Výsledkem `x--` je hodnota `x` *před* operací, jak ukazuje následující příklad:

[!code-csharp-interactive[postfix decrement](snippets/ArithmeticOperators.cs#PostfixDecrement)]

### <a name="prefix-decrement-operator"></a>Operátor snížení předpony

Výsledkem `--x` je hodnota `x` *po* operaci, jak ukazuje následující příklad:

[!code-csharp-interactive[prefix decrement](snippets/ArithmeticOperators.cs#PrefixDecrement)]

## <a name="unary-plus-and-minus-operators"></a>Unární plus a minus operátory

Unární `+` operátor vrátí hodnotu jeho operand. Unární `-` operátor vypočítá číselné negace jeho operandu.

[!code-csharp-interactive[unary plus and minus](snippets/ArithmeticOperators.cs#UnaryPlusAndMinus)]

Typ [ulong](../builtin-types/integral-numeric-types.md) nepodporuje unární `-` operátor.

## <a name="multiplication-operator-"></a>Operátor násobení *

Operátor `*` násobení vypočítá součin svých operandů:

[!code-csharp-interactive[multiplication operator](snippets/ArithmeticOperators.cs#Multiplication)]

Unární `*` operátor je [operátor dereference ukazatele](pointer-related-operators.md#pointer-indirection-operator-).

## <a name="division-operator-"></a>Provozovatel divize /

Operátor `/` divize rozděluje svůj levý operand pravostrannou obsluhou.

### <a name="integer-division"></a>Celá divize

Pro operandy typů celé číslo je výsledek `/` operátoru celého typu a rovná se podílu dvou operandů zaokrouhlených na nulu:

[!code-csharp-interactive[integer division](snippets/ArithmeticOperators.cs#IntegerDivision)]

Chcete-li získat podíl obou operandů jako číslo s plovoucí `float` `double`desetinnou tácek, použijte typ , nebo `decimal` zadejte:

[!code-csharp-interactive[integer as floating-point division](snippets/ArithmeticOperators.cs#IntegerAsFloatingPointDivision)]

### <a name="floating-point-division"></a>Divize s plovoucí desetinnou desetinnou desetinnou desetin

Pro `float`, `double`, `decimal` a typy je `/` výsledkem operátoru podíl obou operandů:

[!code-csharp-interactive[floating-point division](snippets/ArithmeticOperators.cs#FloatingPointDivision)]

`decimal`Pokud je jeden z operandů , může `float` být `double`jiný operand `double` ani jeden `decimal`, protože ani `float` není implicitně převoditelný na . Je nutné explicitně `double` převést `decimal` `float` nebo operand na typ. Další informace o převodech mezi číselnými typy naleznete [v tématu Předdefinované číselné převody](../builtin-types/numeric-conversions.md).

## <a name="remainder-operator-"></a>Zůstatek operátor %

Zbývající operátor `%` vypočítá zbytek po vydělením jeho levého operandu jeho pravostranným operandem.

### <a name="integer-remainder"></a>Zbytek celého čísla

Pro operandy celého čísla `a % b` typů, výsledkem je `a - (a / b) * b`hodnota produkovaná . Znaménko nenulového zbytku je stejné jako u levého operandu, jak ukazuje následující příklad:

[!code-csharp-interactive[integer remainder](snippets/ArithmeticOperators.cs#IntegerRemainder)]

Pomocí <xref:System.Math.DivRem%2A?displayProperty=nameWithType> metody můžete vypočítat výsledky dělení celého čísla i zbytku.

### <a name="floating-point-remainder"></a>Zbytek s plovoucí desetinnou tísní

Pro `float` a `double` operandy, výsledek `x % y` pro konečný `x` a `y` je `z` hodnota taková, že

- Znaménko `z`, pokud je nenulové, `x`je stejné jako znaménko .
- Absolutní hodnota `z` je hodnota produkovaná místem, `|x| - n * |y|` `n` kde je největší možné `|x| / |y|` celé `|x|` `|y|` číslo, které `x` je `y`menší nebo rovno a jsou absolutní hodnoty a , v uvedeném pořadí.

> [!NOTE]
> Tato metoda výpočtu zbytek je obdobou, která se používá pro celé číslo operandy, ale liší se od specifikace IEEE 754. Pokud potřebujete zbývající operaci, která je v souladu se specifikací IEEE 754, použijte metodu. <xref:System.Math.IEEERemainder%2A?displayProperty=nameWithType>

Informace o chování operátoru `%` s neomezenýmými operandy naleznete v části Operátor [Zbytek](~/_csharplang/spec/expressions.md#remainder-operator) ve [specifikaci jazyka C#](~/_csharplang/spec/introduction.md).

Pro `decimal` operandy je operátor `%` zbytek ekvivalentní [zbytku operátoru](<xref:System.Decimal.op_Modulus(System.Decimal,System.Decimal)>) <xref:System.Decimal?displayProperty=nameWithType> typu.

Následující příklad ukazuje chování operátoru zbytek s operandy s plovoucí desetinnou desetinnou desetinnou táhou:

[!code-csharp-interactive[floating-point remainder](snippets/ArithmeticOperators.cs#FloatingPointRemainder)]

## <a name="addition-operator-"></a>Operátor sčítání +

Operátor `+` sčítání vypočítá součet jeho operandů:

[!code-csharp-interactive[addition operator](snippets/ArithmeticOperators.cs#Addition)]

Operátor můžete také `+` použít pro kombinaci zřetězení řetězců a delegáta. Další informace naleznete [ `+` v `+=` článku a operátory.](addition-operator.md)

## <a name="subtraction-operator--"></a>Operátor odčítání -

Operátor `-` odčítání odečte svůj pravostranný operand od levého operandu:

[!code-csharp-interactive[subtraction operator](snippets/ArithmeticOperators.cs#Subtraction)]

Operátor můžete také `-` použít pro odebrání delegáta. Další informace naleznete [ `-` v `-=` článku a operátory.](subtraction-operator.md)

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

Následující příklad ukazuje použití složené přiřazení s aritmetické operátory:

[!code-csharp-interactive[compound assignment](snippets/ArithmeticOperators.cs#CompoundAssignment)]

Z důvodu [číselných propagačních](~/_csharplang/spec/expressions.md#numeric-promotions) `op` akcí nemusí být výsledek operace `T` implicitně převoditelný na typ . `x` V takovém případě, `op` pokud je předdefinovaný operátor a výsledek operace je `T` `x`explicitně převoditelný na `x op= y` typ `x = (T)(x op y)`, složený `x` výraz přiřazení formuláře je ekvivalentní , s výjimkou, že je vyhodnocenpouze jednou. Následující příklad ukazuje, že chování:

[!code-csharp-interactive[compound assignment with cast](snippets/ArithmeticOperators.cs#CompoundAssignmentWithCast)]

Můžete také `+=` použít `-=` a operátory přihlásit a odhlásit z [akce](../keywords/event.md), resp. Další informace naleznete v tématu [Jak se přihlásit k odběru a odhlásit z odběru událostí](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).

## <a name="operator-precedence-and-associativity"></a>Priorita operátora a asociativita

Následující seznam seřazuje aritmetické operátory od nejvyšší priority k nejnižší:

- Operátory přípona přírůstek `x++` a snížení `x--`
- Přírůstek `++x` a snížení předpony `--x` a `+` `-` unární a operátory
- Multiplikativní `*`, `/`a `%` operátory
- Doplňkové `+` `-` látky a obsluha

Binární aritmetické operátory jsou levosociativní. To znamená, že operátory se stejnou úrovní priority jsou vyhodnocovány zleva doprava.

Pomocí závorek `()`, můžete změnit pořadí hodnocení uloženého prioritou operátoru a asociativitou operátora.

[!code-csharp-interactive[precedence and associativity](snippets/ArithmeticOperators.cs#PrecedenceAndAssociativity)]

Úplný seznam operátorů jazyka C# seřazené podle úrovně priority naleznete v části [Priorita operátora](index.md#operator-precedence) v článku [operátorů jazyka C#.](index.md)

## <a name="arithmetic-overflow-and-division-by-zero"></a>Aritmetické přetečení a dělení nulou

Pokud je výsledek aritmetické operace mimo rozsah možných konečných hodnot zapojeného číselného typu, závisí chování aritmetického operátoru na typu jeho operandů.

### <a name="integer-arithmetic-overflow"></a>Integer aritmetický přetečení

Dělení celého čísla nulou <xref:System.DivideByZeroException>vždy vyvolá .

V případě integer aritmetické přetečení, přetečení kontrolní kontext, který lze [zkontrolovat nebo nezaškrtnuté](../keywords/checked-and-unchecked.md), řídí výsledné chování:

- V kontrolovaném kontextu, pokud dojde k přetečení v konstantním výrazu, dojde k chybě v době kompilace. V opačném případě při operaci se <xref:System.OverflowException> provádí v době běhu, je vyvolána.
- V nekontrolovaném kontextu je výsledek zkrácen zahozením všech bitů vyššího řádu, které se nevejdou do cílového typu.

Spolu s [zaškrtnuté a nezaškrtnuté příkazy,](../keywords/checked-and-unchecked.md) můžete použít `checked` a `unchecked` operátory k řízení kontextu kontroly přetečení, ve kterém je vyhodnocován výraz:

[!code-csharp-interactive[checked and unchecked](snippets/ArithmeticOperators.cs#CheckedUnchecked)]

Ve výchozím nastavení aritmetické operace dojít v *nekontrolovaném* kontextu.

### <a name="floating-point-arithmetic-overflow"></a>Přetečení aritmetiky s plovoucí desetinnou desetinnou desetinnou desetinnou desetinnou tísní

Aritmetické operace `float` s `double` a typy nikdy vyvolat výjimku. Výsledkem aritmetické operace s těmito typy může být jedna ze zvláštních hodnot, které představují nekonečno a ne-a-číslo:

[!code-csharp-interactive[double non-finite values](snippets/ArithmeticOperators.cs#FloatingPointOverflow)]

Pro operandy `decimal` typu aritmetické přetečení vždy <xref:System.OverflowException> vyvolá a dělení nulou <xref:System.DivideByZeroException>vždy vyvolá .

## <a name="round-off-errors"></a>Chyby zaokrouhlení

Z důvodu obecných omezení reprezentace s plovoucí desetinnou desetinnou rovinou reálných čísel a aritmetických aritmetických čísel s plovoucí desetinnou desetinnou, mohou při výpočtech s typy s plovoucí desetinnou desetinnou rovinou dojít k chybám zaokrouhlení. To znamená, že vytvořený výsledek výrazu se může lišit od očekávaného matematického výsledku. Následující příklad ukazuje několik takových případů:

[!code-csharp-interactive[round-off errors](snippets/ArithmeticOperators.cs#RoundOffErrors)]

Další informace naleznete v poznámkách na referenčních stránkách [System.Double](/dotnet/api/system.double#remarks), [System.Single](/dotnet/api/system.single#remarks)nebo [System.Decimal.](/dotnet/api/system.decimal#remarks)

## <a name="operator-overloadability"></a>Přetížení obsluhy

Uživatelem definovaný typ může [přetížit](operator-overloading.md) `+`unární `-`(`++`, `--`, `%` `+`, `-`a ) a binární (`*`, `/`, , a ) aritmetické operátory. Když je přetížený binární operátor, odpovídající složený operátor přiřazení je také implicitně přetížena. Uživatelem definovaný typ nemůže explicitně přetížit operátor složeného přiřazení.

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace naleznete v následujících částech [specifikace jazyka C#](~/_csharplang/spec/introduction.md):

- [Operátory přípona přírůstek a snížení](~/_csharplang/spec/expressions.md#postfix-increment-and-decrement-operators)
- [Operátory přírůstek a snížení předpona](~/_csharplang/spec/expressions.md#prefix-increment-and-decrement-operators)
- [Jednočlenný operátor plus](~/_csharplang/spec/expressions.md#unary-plus-operator)
- [Unární minus operátor](~/_csharplang/spec/expressions.md#unary-minus-operator)
- [Operátor násobení](~/_csharplang/spec/expressions.md#multiplication-operator)
- [Provozovatel divize](~/_csharplang/spec/expressions.md#division-operator)
- [Operátor zbytek](~/_csharplang/spec/expressions.md#remainder-operator)
- [Operátor sčítání](~/_csharplang/spec/expressions.md#addition-operator)
- [Operátor odčítání](~/_csharplang/spec/expressions.md#subtraction-operator)
- [Složené přiřazení](~/_csharplang/spec/expressions.md#compound-assignment)
- [Kontrolované a nekontrolované operátory](~/_csharplang/spec/expressions.md#the-checked-and-unchecked-operators)
- [Číselné propagační akce](~/_csharplang/spec/expressions.md#numeric-promotions)

## <a name="see-also"></a>Viz také

- [Referenční dokumentace k jazyku C#](../index.md)
- [Operátory jazyka C#](index.md)
- <xref:System.Math?displayProperty=nameWithType>
- <xref:System.MathF?displayProperty=nameWithType>
- [Číslovky v technologii .NET](../../../standard/numerics.md)
