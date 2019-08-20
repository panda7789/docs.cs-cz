---
title: Aritmetické operátory C# – referenční informace
description: Přečtěte C# si o operátorech, které provádějí operace násobení, dělení, zbytku, sčítání a odčítání s číselnými typy.
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
ms.openlocfilehash: ac04ba72ed0c25aa576bf10150fc80410890eda0
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69608368"
---
# <a name="arithmetic-operators-c-reference"></a>Aritmetické operátoryC# (referenční)

Následující operátory provádějí aritmetické operace s číselnými typy:

- [ Unární`++` (přírůstek)](#increment-operator-), [ `--` (snížená)](#decrement-operator---) [ `+` , (plus)](#unary-plus-and-minus-operators)a [ `-` (mínus)](#unary-plus-and-minus-operators) operátory
- [ Binary`*` (násobení)](#multiplication-operator-), [ `/` ](#division-operator-) [ `-` ](#subtraction-operator--) [ (dělení`%` ), (zbytek](#remainder-operator-)), [ (sčítání)a(odčítání)operátorů`+` ](#addition-operator-)

Tyto operátory podporují všechny [](../builtin-types/integral-numeric-types.md) číselné typy integrálních a [plovoucích bodů](../builtin-types/floating-point-numeric-types.md) .

## <a name="increment-operator-"></a>Operátor přírůstku + +

Operátor `++` unárního přírůstku zvyšuje svůj operand o 1. Operandem musí být proměnná, přístup k [vlastnosti](../../programming-guide/classes-and-structs/properties.md) nebo přístup indexeru [](../../programming-guide/indexers/index.md) .

Operátor přírůstku je podporován ve dvou formách: operátor přírůstku přípony, `x++`a operátor přírůstku předpony,. `++x`

### <a name="postfix-increment-operator"></a>Příponový operátor inkrementace

Výsledek `x++` je *hodnota před* operací, jak ukazuje následující příklad: `x`

[!code-csharp-interactive[postfix increment](~/samples/csharp/language-reference/operators/ArithmeticOperators.cs#PostfixIncrement)]

### <a name="prefix-increment-operator"></a>Operátor přírůstku předpony

Výsledek `++x` je *hodnota po* operaci, jak ukazuje následující příklad: `x`

[!code-csharp-interactive[prefix increment](~/samples/csharp/language-reference/operators/ArithmeticOperators.cs#PrefixIncrement)]

## <a name="decrement-operator---"></a>Operátor snížení--

Operátor `--` unárního snížení snižuje svůj operand o 1. Operandem musí být proměnná, přístup k [vlastnosti](../../programming-guide/classes-and-structs/properties.md) nebo přístup indexeru [](../../programming-guide/indexers/index.md) .

Operátor snížení je podporován ve dvou formách: operátor snížení přípony, `x--`a `--x`operátor snížení předpony.

### <a name="postfix-decrement-operator"></a>Příponový operátor dekrementace

Výsledek `x--` je *hodnota před* operací, jak ukazuje následující příklad: `x`

[!code-csharp-interactive[postfix decrement](~/samples/csharp/language-reference/operators/ArithmeticOperators.cs#PostfixDecrement)]

### <a name="prefix-decrement-operator"></a>Operátor snížení předpony

Výsledek `--x` je *hodnota po* operaci, jak ukazuje následující příklad: `x`

[!code-csharp-interactive[prefix decrement](~/samples/csharp/language-reference/operators/ArithmeticOperators.cs#PrefixDecrement)]

## <a name="unary-plus-and-minus-operators"></a>Unární operátory plus a mínus

Unární `+` operátor vrátí hodnotu jeho operandu. Unární `-` operátor vypočítá číselnou negaci svého operandu.

[!code-csharp-interactive[unary plus and minus](~/samples/csharp/language-reference/operators/ArithmeticOperators.cs#UnaryPlusAndMinus)]

Unární `-` operátor nepodporuje typ [ulong](../builtin-types/integral-numeric-types.md) .

## <a name="multiplication-operator-"></a>Operátor násobení *

Operátor `*` násobení Vypočítá součin jeho operandů:

[!code-csharp-interactive[multiplication operator](~/samples/csharp/language-reference/operators/ArithmeticOperators.cs#Multiplication)]

Unární `*` operátor je [operátor dereference ukazatele](pointer-related-operators.md#pointer-indirection-operator-).

## <a name="division-operator-"></a>Operátor dělení/

Operátor `/` dělení rozdělí svůj operand na levou stranu operandu na pravé straně.

### <a name="integer-division"></a>Dělení celého čísla

U operandů typu integer je výsledkem `/` operátoru typ Integer a rovná se podíl dvou operandů zaokrouhlených směrem k nule:

[!code-csharp-interactive[integer division](~/samples/csharp/language-reference/operators/ArithmeticOperators.cs#IntegerDivision)]

Chcete-li získat podíl dvou operandů jako číslo s plovoucí desetinnou čárkou, použijte `float`operátor `double`, nebo `decimal` :

[!code-csharp-interactive[integer as floating-point division](~/samples/csharp/language-reference/operators/ArithmeticOperators.cs#IntegerAsFloatingPointDivision)]

### <a name="floating-point-division"></a>Dělení plovoucí desetinné čárky

`double`Pro typy `float`, a`decimal` je výsledkem`/` operátoru podíl dvou operandů:

[!code-csharp-interactive[floating-point division](~/samples/csharp/language-reference/operators/ArithmeticOperators.cs#FloatingPointDivision)]

Pokud je `decimal`jeden z operandů, jiný operand nemůže `float` `float` být `double` ani `double`, protože ani není implicitně převoditelné na `decimal`. Je nutné explicitně převést `float` operand `decimal` nebo `double` na typ. Další informace o implicitních převodech mezi číselnými typy naleznete v [tabulce implicitní číselné převody](../keywords/implicit-numeric-conversions-table.md).

## <a name="remainder-operator-"></a>Operátor zbývajícího%

Operátor `%` zbytek vypočítá zbytek po dělení jeho levého operandu pomocí jeho pravého operandu.

### <a name="integer-remainder"></a>Celočíselný zbytek
  
U operandů typu Integer `a % b` je výsledkem hodnota hodnotu `a - (a / b) * b`vytvořenou hodnotou. Znaménko nenulového zbytku je stejné jako u levého operandu, jak ukazuje následující příklad:

[!code-csharp-interactive[integer remainder](~/samples/csharp/language-reference/operators/ArithmeticOperators.cs#IntegerRemainder)]

<xref:System.Math.DivRem%2A?displayProperty=nameWithType> Použijte metodu pro výpočet celočíselného dělení i zbývajících výsledků.

### <a name="floating-point-remainder"></a>Zbytek s plovoucí desetinnou čárkou

`x % y` `z` `y` Pro operandy `double` `x` a je výsledkem pro konečnou hodnotu a hodnota, například `float`

- Znaménko `z`, pokud není nula, je stejné jako `x`znaménko.
- Absolutní hodnota `z` je hodnota vytvořená v `|x| - n * |y|` místě, kde `n` je největší možné `|x| / |y|` celé číslo, které je menší než nebo rovno `|x|` a `|y|` a jsou absolutními hodnotami `x` a `y`v uvedeném pořadí.

> [!NOTE]
> Tato metoda výpočetního zbytku je podobná, jako se používá pro celočíselné operandy, ale liší se od IEEE 754. Pokud potřebujete zbývající operaci, která je v souladu s normou IEEE 754, <xref:System.Math.IEEERemainder%2A?displayProperty=nameWithType> použijte metodu.

Informace o chování `%` operátoru s nekonečnými operandy naleznete v části [operátor zbytek](~/_csharplang/spec/expressions.md#remainder-operator) ve [ C# specifikaci jazyka](~/_csharplang/spec/introduction.md).

U operandů je operátor `%` zbytku ekvivalentní k <xref:System.Decimal?displayProperty=nameWithType> operátoru zbývajícího typu. [](<xref:System.Decimal.op_Modulus(System.Decimal,System.Decimal)>) `decimal`

Následující příklad ukazuje chování operátoru zbytek s operandy s plovoucí desetinnou čárkou:

[!code-csharp-interactive[floating-point remainder](~/samples/csharp/language-reference/operators/ArithmeticOperators.cs#FloatingPointRemainder)]

## <a name="addition-operator-"></a>Operátor sčítání +

Operátor `+` sčítání vypočítá součet jeho operandů:

[!code-csharp-interactive[addition operator](~/samples/csharp/language-reference/operators/ArithmeticOperators.cs#Addition)]

Můžete také použít `+` operátor pro kombinaci řetězení řetězců a delegátů. Další informace naleznete [ `+` v článku operátory a `+=` ](addition-operator.md) .

## <a name="subtraction-operator--"></a>Operátor odčítání –

Operátor `-` odčítání odečte svůj pravý operand od jeho levého operandu:

[!code-csharp-interactive[subtraction operator](~/samples/csharp/language-reference/operators/ArithmeticOperators.cs#Subtraction)]

K odebrání delegáta můžete `-` také použít operátora. Další informace najdete v článku o [ `-` operátoru](subtraction-operator.md) .

## <a name="compound-assignment"></a>Složené přiřazení

Pro binární operátor `op`, výraz složeného přiřazení formuláře

```csharp
x op= y
```

je ekvivalentem

```csharp
x = x op y
```

s výjimkou, že `x` je vyhodnocena pouze jednou.

Následující příklad ukazuje použití složeného přiřazení s aritmetickými operátory:

[!code-csharp-interactive[compound assignment](~/samples/csharp/language-reference/operators/ArithmeticOperators.cs#CompoundAssignment)]

Z důvodu [numerických propagačních akcí](~/_csharplang/spec/expressions.md#numeric-promotions)nemusí být `op` výsledek operace implicitně převoditelný `x`na typ `T` . V takovém případě, pokud `op` je předdefinovaný operátor a výsledek operace je explicitně převoditelné na `x`typ `T` , je složený výraz `x = (T)(x op y)`přiřazení formuláře `x op= y` ekvivalentní s výjimkou to `x` je vyhodnoceno pouze jednou. Následující příklad ukazuje toto chování:

[!code-csharp-interactive[compound assignment with cast](~/samples/csharp/language-reference/operators/ArithmeticOperators.cs#CompoundAssignmentWithCast)]

Operátory `+=` a `-=` se používají také k přihlášení a odhlášení odběru [událostí](../keywords/event.md). Další informace najdete v tématu [Postup: přihlášení a](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md)odhlášení odběru událostí.

## <a name="operator-precedence-and-associativity"></a>Priorita operátorů a asociativita

Následující seznam řadí aritmetické operátory počínaje od nejvyšší priority k nejnižší:

- Operátory `x++` přírůstku `x--` a snížení přípony
- Zvýšení `++x` a snížení `--x` prefixu a `+` unární `-` operátory a
- Multiplikativní `*`operátory `/`, a`%`
- `+` Doplňková `-` a operátor

Binární aritmetické operátory jsou asociativní zleva. To znamená, že operátory se stejnou úrovní priority jsou vyhodnocovány zleva doprava.

Pomocí závorek `()`můžete změnit pořadí vyhodnocování stanovené prioritou operátoru a asociativita.

[!code-csharp-interactive[precedence and associativity](~/samples/csharp/language-reference/operators/ArithmeticOperators.cs#PrecedenceAndAssociativity)]

Úplný seznam C# operátorů seřazených podle priority úrovně naleznete v tématu [ C# operátory](index.md).

## <a name="arithmetic-overflow-and-division-by-zero"></a>Aritmetické přetečení a dělení nulou

Pokud je výsledek aritmetické operace mimo rozsah možných konečných hodnot typu, který je součástí daného číselného typu, chování aritmetického operátoru závisí na typu jeho operandů.

### <a name="integer-arithmetic-overflow"></a>Aritmetické přetečení typu Integer

Dělení celého čísla nulou vždy vyvolá <xref:System.DivideByZeroException>.

V případě celočíselného přetečení aritmetického přetečení, které může být [zaškrtnuto nebo nezaškrtnuto](../keywords/checked-and-unchecked.md), ovládací prvky výsledného chování:

- V kontrolovaném kontextu dojde k chybě při kompilaci, pokud dojde k přetečení v konstantním výrazu. V opačném případě, <xref:System.OverflowException> je-li operace provedena v době běhu, je vyvolána.
- V nekontrolovaném kontextu se výsledek zkrátí tak, že zahodí jakékoli bity s vysokým pořadím, které se nevejdou do cílového typu.

Spolu s [zaškrtnutými a](../keywords/checked-and-unchecked.md) nekontrolovanými příkazy lze pomocí `checked` operátorů a `unchecked` řídit kontext kontroly přetečení, ve kterém je výraz vyhodnocen:

[!code-csharp-interactive[checked and unchecked](~/samples/csharp/language-reference/operators/ArithmeticOperators.cs#CheckedUnchecked)]

Ve výchozím nastavení se aritmetické operace vyskytují v nekontrolovaném kontextu.

### <a name="floating-point-arithmetic-overflow"></a>Aritmetické přetečení s plovoucí desetinnou čárkou

Aritmetické operace s `float` typy `double` a nikdy nevyvolávají výjimku. Výsledkem aritmetických operací s těmito typy může být jedna z speciálních hodnot, které reprezentují nekonečno a nikoli-a-číslo:

[!code-csharp-interactive[double non-finite values](~/samples/csharp/language-reference/operators/ArithmeticOperators.cs#FloatingPointOverflow)]

U operandů `decimal` typu aritmetické přetečení vždy <xref:System.OverflowException> vyvolá výjimku a dělení nulou vždy vyvolá <xref:System.DivideByZeroException>.

## <a name="round-off-errors"></a>Chyby zaokrouhlení

Z důvodu obecného omezení reprezentace reálných čísel s plovoucí desetinnou čárkou a aritmetických operací s plovoucí desetinnou čárkou může dojít k chybám zaokrouhlení ve výpočtech s typy s plovoucí desetinnou čárkou. To znamená, že získaný výsledek výrazu se může lišit od očekávaného matematického výsledku. Následující příklad ukazuje několik takových případů:

[!code-csharp-interactive[round-off errors](~/samples/csharp/language-reference/operators/ArithmeticOperators.cs#RoundOffErrors)]

Další informace najdete v tématu poznámky na referenčních stránkách [System. Double](/dotnet/api/system.double#remarks), [System. Single](/dotnet/api/system.single#remarks)nebo [System. Decimal](/dotnet/api/system.decimal#remarks) .

## <a name="operator-overloadability"></a>Přetížení operátoru

Uživatelsky definovaný typ může [přetížit](operator-overloading.md) `++`unární (, `/` `-` `--` `+`,, `+``*` a)`%`a binární (,,, a )aritmetickéoperace.`-` logické. Při přetížení binárního operátoru je také implicitně přetížen odpovídající operátor složeného přiřazení. Uživatelsky definovaný typ nemůže explicitně přetížit operátor složeného přiřazení.

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace najdete v následujících oddílech [ C# specifikace jazyka](~/_csharplang/spec/introduction.md):

- [Operátory přírůstku a snížení přípony](~/_csharplang/spec/expressions.md#postfix-increment-and-decrement-operators)
- [Operátory přírůstku a snížení předpony](~/_csharplang/spec/expressions.md#prefix-increment-and-decrement-operators)
- [Unární operátor plus](~/_csharplang/spec/expressions.md#unary-plus-operator)
- [Unární operátor minus](~/_csharplang/spec/expressions.md#unary-minus-operator)
- [Operátor násobení](~/_csharplang/spec/expressions.md#multiplication-operator)
- [Operátor dělení](~/_csharplang/spec/expressions.md#division-operator)
- [Operátor zbývající](~/_csharplang/spec/expressions.md#remainder-operator)
- [Operátor sčítání](~/_csharplang/spec/expressions.md#addition-operator)
- [Operátor odčítání](~/_csharplang/spec/expressions.md#subtraction-operator)
- [Složené přiřazení](~/_csharplang/spec/expressions.md#compound-assignment)
- [Kontrolované a nezaškrtnuté operátory](~/_csharplang/spec/expressions.md#the-checked-and-unchecked-operators)
- [Číselné propagační akce](~/_csharplang/spec/expressions.md#numeric-promotions)

## <a name="see-also"></a>Viz také:

- [C#odkaz](../index.md)
- [Operátory jazyka C#](index.md)
- <xref:System.Math?displayProperty=nameWithType>
- <xref:System.MathF?displayProperty=nameWithType>
- [Číslovky v technologii .NET](../../../standard/numerics.md)
