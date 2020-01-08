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
ms.openlocfilehash: 8701991542f1e950914d5b4275ae8dcd68ad83a1
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75345370"
---
# <a name="arithmetic-operators-c-reference"></a>Aritmetické operátoryC# (referenční)

Následující operátory provádějí aritmetické operace s operandy číselných typů:

- Unární operátory [`++` (přírůstek)](#increment-operator-), [`--` (snížení)](#decrement-operator---), [`+` (plus)](#unary-plus-and-minus-operators)a [`-` (mínus)](#unary-plus-and-minus-operators)
- Binární [`*` (násobení)](#multiplication-operator-), [`/` (dělení)](#division-operator-), [`%` (zbytek)](#remainder-operator-), [`+` (sčítání](#addition-operator-)) a [`-`ch (odčítání)](#subtraction-operator--) operátorů

Tyto operátory jsou podporovány všemi [celočíselnými](../builtin-types/integral-numeric-types.md) typy a čísly [s plovoucí desetinnou](../builtin-types/floating-point-numeric-types.md) čárkou.

## <a name="increment-operator-"></a>Operátor přírůstku + +

Unární operátor přírůstku `++` zvyšuje svůj operand o 1. Operandem musí být proměnná, přístup k [vlastnosti](../../programming-guide/classes-and-structs/properties.md) nebo přístup [indexeru](../../programming-guide/indexers/index.md) .

Operátor přírůstku je podporován ve dvou formách: operátor přírůstku přípony, `x++`a operátor přírůstku předpony `++x`.

### <a name="postfix-increment-operator"></a>Příponový operátor inkrementace

Výsledek `x++` je hodnota `x` *před* operací, jak ukazuje následující příklad:

[!code-csharp-interactive[postfix increment](~/samples/csharp/language-reference/operators/ArithmeticOperators.cs#PostfixIncrement)]

### <a name="prefix-increment-operator"></a>Operátor přírůstku předpony

Výsledek `++x` je hodnota `x` *po* operaci, jak ukazuje následující příklad:

[!code-csharp-interactive[prefix increment](~/samples/csharp/language-reference/operators/ArithmeticOperators.cs#PrefixIncrement)]

## <a name="decrement-operator---"></a>Operátor snížení--

Operátor unárního snížení `--` sníží svůj operand o 1. Operandem musí být proměnná, přístup k [vlastnosti](../../programming-guide/classes-and-structs/properties.md) nebo přístup [indexeru](../../programming-guide/indexers/index.md) .

Operátor snížení je podporován ve dvou formulářích: operátor snížení přípony, `x--`a operátor snížení prefixu `--x`.

### <a name="postfix-decrement-operator"></a>Příponový operátor dekrementace

Výsledek `x--` je hodnota `x` *před* operací, jak ukazuje následující příklad:

[!code-csharp-interactive[postfix decrement](~/samples/csharp/language-reference/operators/ArithmeticOperators.cs#PostfixDecrement)]

### <a name="prefix-decrement-operator"></a>Operátor snížení předpony

Výsledek `--x` je hodnota `x` *po* operaci, jak ukazuje následující příklad:

[!code-csharp-interactive[prefix decrement](~/samples/csharp/language-reference/operators/ArithmeticOperators.cs#PrefixDecrement)]

## <a name="unary-plus-and-minus-operators"></a>Unární operátory plus a mínus

Unární operátor `+` vrací hodnotu jeho operandu. Operátor unární `-` vypočítá číselnou negaci svého operandu.

[!code-csharp-interactive[unary plus and minus](~/samples/csharp/language-reference/operators/ArithmeticOperators.cs#UnaryPlusAndMinus)]

Typ [ulong](../builtin-types/integral-numeric-types.md) nepodporuje unární operátor `-`.

## <a name="multiplication-operator-"></a>Operátor násobení *

Operátor násobení `*` Vypočítá součin jeho operandů:

[!code-csharp-interactive[multiplication operator](~/samples/csharp/language-reference/operators/ArithmeticOperators.cs#Multiplication)]

Unární operátor `*` je [operátor dereference ukazatele](pointer-related-operators.md#pointer-indirection-operator-).

## <a name="division-operator-"></a>Operátor dělení/

Operátor dělení `/` rozdělí svůj operand na levé straně svým operandem na pravé straně.

### <a name="integer-division"></a>Dělení celého čísla

U operandů typu integer je výsledkem operátoru `/` celočíselný typ a rovná se podíl dvou operandů zaokrouhlených směrem k nule:

[!code-csharp-interactive[integer division](~/samples/csharp/language-reference/operators/ArithmeticOperators.cs#IntegerDivision)]

Chcete-li získat podíl dvou operandů jako číslo s plovoucí desetinnou čárkou, použijte `float`, `double`nebo `decimal` typ:

[!code-csharp-interactive[integer as floating-point division](~/samples/csharp/language-reference/operators/ArithmeticOperators.cs#IntegerAsFloatingPointDivision)]

### <a name="floating-point-division"></a>Dělení plovoucí desetinné čárky

V případě typů `float`, `double`a `decimal` je výsledkem operátoru `/` podíl dvou operandů:

[!code-csharp-interactive[floating-point division](~/samples/csharp/language-reference/operators/ArithmeticOperators.cs#FloatingPointDivision)]

Pokud je jeden z operandů `decimal`, jiný operand nemůže být `float` ani `double`, protože ani `float` ani `double` není implicitně převoditelná na `decimal`. Je nutné explicitně převést `float` nebo operand `double` na typ `decimal`. Další informace o převodech mezi číselnými typy naleznete v tématu [vestavěné číselné převody](../builtin-types/numeric-conversions.md).

## <a name="remainder-operator-"></a>Operátor zbývajícího%

Operátor zbývající `%` vypočítá zbytek po dělení jeho levého operandu jeho pravým operandem.

### <a name="integer-remainder"></a>Celočíselný zbytek

U operandů typu integer je výsledkem `a % b` hodnota vytvořená `a - (a / b) * b`. Znaménko nenulového zbytku je stejné jako u levého operandu, jak ukazuje následující příklad:

[!code-csharp-interactive[integer remainder](~/samples/csharp/language-reference/operators/ArithmeticOperators.cs#IntegerRemainder)]

Použijte metodu <xref:System.Math.DivRem%2A?displayProperty=nameWithType> k výpočtu celočíselného dělení i zbývajících výsledků.

### <a name="floating-point-remainder"></a>Zbytek s plovoucí desetinnou čárkou

U operandů `float` a `double` je výsledkem `x % y` pro konečnou `x` a `y` hodnota `z` tak, aby

- Znaménko `z`, pokud není nula, je stejné jako znaménko `x`.
- Absolutní hodnota `z` je hodnota vytvořená `|x| - n * |y|`, kde `n` je největší možné celé číslo, které je menší nebo rovno `|x| / |y|` a `|x|` a `|y|` jsou absolutní hodnoty `x` a `y`v uvedeném pořadí.

> [!NOTE]
> Tato metoda výpočtu zbytku je podobná, jako by se použila pro celočíselné operandy, ale liší se od specifikace IEEE 754. Pokud potřebujete zbývající operaci, která je v souladu se specifikací IEEE 754, použijte metodu <xref:System.Math.IEEERemainder%2A?displayProperty=nameWithType>.

Informace o chování operátoru `%` s nekonečnými operandy naleznete v části [operátor zbytek](~/_csharplang/spec/expressions.md#remainder-operator) ve [ C# specifikaci jazyka](~/_csharplang/spec/introduction.md).

U operandů `decimal` je operátor zbývající `%` ekvivalentní k [operátoru zbývajícího](<xref:System.Decimal.op_Modulus(System.Decimal,System.Decimal)>) typu <xref:System.Decimal?displayProperty=nameWithType>.

Následující příklad ukazuje chování operátoru zbytek s operandy s plovoucí desetinnou čárkou:

[!code-csharp-interactive[floating-point remainder](~/samples/csharp/language-reference/operators/ArithmeticOperators.cs#FloatingPointRemainder)]

## <a name="addition-operator-"></a>Operátor sčítání +

Operátor sčítání `+` vypočítá součet jeho operandů:

[!code-csharp-interactive[addition operator](~/samples/csharp/language-reference/operators/ArithmeticOperators.cs#Addition)]

Můžete také použít operátor `+` pro kombinaci řetězení řetězců a delegáta. Další informace najdete v článku [operátory`+` a `+=`](addition-operator.md) .

## <a name="subtraction-operator--"></a>Operátor odčítání –

Operátor odčítání `-` odečte svůj pravý operand od jeho levého operandu:

[!code-csharp-interactive[subtraction operator](~/samples/csharp/language-reference/operators/ArithmeticOperators.cs#Subtraction)]

K odebrání delegáta můžete také použít operátor `-`. Další informace najdete v článku [operátory`-` a `-=`](subtraction-operator.md) .

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

Následující příklad ukazuje použití složeného přiřazení s aritmetickými operátory:

[!code-csharp-interactive[compound assignment](~/samples/csharp/language-reference/operators/ArithmeticOperators.cs#CompoundAssignment)]

Z důvodu [numerických propagačních akcí](~/_csharplang/spec/expressions.md#numeric-promotions)nemusí být výsledek operace `op` implicitně převoditelný na typ `T` `x`. V takovém případě, pokud je `op` předdefinovaným operátorem a výsledek operace je explicitně převoditelné na typ `T` `x`, výraz složeného přiřazení `x op= y` formuláře je ekvivalentní `x = (T)(x op y)`, s tím rozdílem, že `x` vyhodnocuje pouze jednou. Následující příklad ukazuje toto chování:

[!code-csharp-interactive[compound assignment with cast](~/samples/csharp/language-reference/operators/ArithmeticOperators.cs#CompoundAssignmentWithCast)]

Pomocí operátorů `+=` a `-=` se můžete přihlásit k odběru a zrušit odběr [události](../keywords/event.md)v uvedeném pořadí. Další informace najdete v tématu [jak se přihlásit k odběru událostí a odhlásit se z](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md)nich.

## <a name="operator-precedence-and-associativity"></a>Priorita operátorů a asociativita

Následující seznam řadí aritmetické operátory počínaje od nejvyšší priority k nejnižší:

- Přírůstek přípony `x++` a snížení `x--` operátory
- Zvýšení prefixu `++x` a snížení `--x` a unární operátory `+` a `-`
- Multiplikativní operátory `*`, `/`a `%`
- Aditivní `+` a `-` operátory

Binární aritmetické operátory jsou asociativní zleva. To znamená, že operátory se stejnou úrovní priority jsou vyhodnocovány zleva doprava.

Pomocí závorek, `()`můžete změnit pořadí vyhodnocování stanovené prioritou operátora a asociativita.

[!code-csharp-interactive[precedence and associativity](~/samples/csharp/language-reference/operators/ArithmeticOperators.cs#PrecedenceAndAssociativity)]

Úplný seznam C# operátorů seřazených podle priority najdete v části [Priorita operátorů](index.md#operator-precedence) [ C# v článku věnovaném operátorům](index.md) .

## <a name="arithmetic-overflow-and-division-by-zero"></a>Aritmetické přetečení a dělení nulou

Pokud je výsledek aritmetické operace mimo rozsah možných konečných hodnot typu, který je součástí daného číselného typu, chování aritmetického operátoru závisí na typu jeho operandů.

### <a name="integer-arithmetic-overflow"></a>Aritmetické přetečení typu Integer

Celočíselné dělení nulou vždy vyvolá <xref:System.DivideByZeroException>.

V případě celočíselného přetečení aritmetického přetečení, které může být [zaškrtnuto nebo nezaškrtnuto](../keywords/checked-and-unchecked.md), ovládací prvky výsledného chování:

- V kontrolovaném kontextu dojde k chybě při kompilaci, pokud dojde k přetečení v konstantním výrazu. V opačném případě, pokud je operace provedena v době běhu, je vyvolána <xref:System.OverflowException>.
- V nekontrolovaném kontextu se výsledek zkrátí tak, že zahodí jakékoli bity s vysokým pořadím, které se nevejdou do cílového typu.

Spolu s [zaškrtnutými a nekontrolovanými](../keywords/checked-and-unchecked.md) příkazy můžete použít operátory `checked` a `unchecked` k řízení kontextu kontroly přetečení, ve kterém je výraz vyhodnocen:

[!code-csharp-interactive[checked and unchecked](~/samples/csharp/language-reference/operators/ArithmeticOperators.cs#CheckedUnchecked)]

Ve výchozím nastavení se aritmetické operace vyskytují v nekontrolovaném *kontextu.*

### <a name="floating-point-arithmetic-overflow"></a>Aritmetické přetečení s plovoucí desetinnou čárkou

Aritmetické operace s typy `float` a `double` nikdy nevyvolávají výjimku. Výsledkem aritmetických operací s těmito typy může být jedna z speciálních hodnot, které reprezentují nekonečno a nikoli-a-číslo:

[!code-csharp-interactive[double non-finite values](~/samples/csharp/language-reference/operators/ArithmeticOperators.cs#FloatingPointOverflow)]

Pro operandy typu `decimal` aritmetické přetečení vždy vyvolá <xref:System.OverflowException> a dělení nulou vždy vyvolá <xref:System.DivideByZeroException>.

## <a name="round-off-errors"></a>Chyby zaokrouhlení

Z důvodu obecného omezení reprezentace reálných čísel s plovoucí desetinnou čárkou a aritmetických operací s plovoucí desetinnou čárkou mohou být při výpočtech s typy s plovoucí desetinnou čárkou zjištěny chyby zaokrouhlení. To znamená, že získaný výsledek výrazu se může lišit od očekávaného matematického výsledku. Následující příklad ukazuje několik takových případů:

[!code-csharp-interactive[round-off errors](~/samples/csharp/language-reference/operators/ArithmeticOperators.cs#RoundOffErrors)]

Další informace najdete v tématu poznámky na referenčních stránkách [System. Double](/dotnet/api/system.double#remarks), [System. Single](/dotnet/api/system.single#remarks)nebo [System. Decimal](/dotnet/api/system.decimal#remarks) .

## <a name="operator-overloadability"></a>Přetížení operátoru

Uživatelsky definovaný typ může [přetížit](operator-overloading.md) unární operátory (`++`, `--`, `+`a `-`) a binární (`*`, `/`, `%`, `+`a `-`). Při přetížení binárního operátoru je také implicitně přetížen odpovídající operátor složeného přiřazení. Uživatelsky definovaný typ nemůže explicitně přetížit operátor složeného přiřazení.

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
