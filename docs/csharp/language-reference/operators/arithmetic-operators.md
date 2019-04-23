---
title: 'Aritmetické operátory: - C# odkaz'
description: Další informace o C# operátory, které provádějí operace násobení, dělení, zbývající, sčítání a odčítání s číselnými typy.
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
ms.openlocfilehash: dc817fdb9684f794efc6599444e80be1ef7f9654
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2019
ms.locfileid: "59978039"
---
# <a name="arithmetic-operators-c-reference"></a>Aritmetické operátory (C# odkaz)

Následující operátory provádění aritmetických operací s číselnými typy:

- Unární [ `++` (přírůstek)](#increment-operator-), [ `--` (snížení)](#decrement-operator---), [ `+` (plus)](#unary-plus-and-minus-operators), a [ `-` (minus)](#unary-plus-and-minus-operators) operátory
- Binární [ `*` (násobení)](#multiplication-operator-), [ `/` (dělení)](#division-operator-), [ `%` (zbytek)](#remainder-operator-), [ `+` () Přidání)](#addition-operator-), a [ `-` (odčítání)](#subtraction-operator--) operátory

Tyto operátory podporují všechny [integrální](../keywords/integral-types-table.md) a [s plovoucí desetinnou čárkou](../keywords/floating-point-types-table.md) číselné typy.

## <a name="increment-operator-"></a>Operátor Inkrementace ++

Unární operátor Inkrementace `++` svého operandu zvýší o hodnotu 1. Operand musí být proměnná [vlastnost](../../programming-guide/classes-and-structs/properties.md) přístup, nebo [indexer](../../../csharp/programming-guide/indexers/index.md) přístup.

Operátor Inkrementace se podporuje ve dvou formách: příponového operátoru Inkrementace `x++`a prefixový operátor Inkrementace `++x`.

### <a name="postfix-increment-operator"></a>Příponový operátor inkrementace

Výsledek `x++` je hodnota `x` *před* operace, jako v následujícím příkladu:

[!code-csharp-interactive[postfix increment](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#PostfixIncrement)]

### <a name="prefix-increment-operator"></a>Prefixový operátor Inkrementace

Výsledek `++x` je hodnota `x` *po* operace, jako v následujícím příkladu:

[!code-csharp-interactive[prefix increment](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#PrefixIncrement)]

## <a name="decrement-operator---"></a>Operátor dekrementace--

Unární operátor dekrementace `--` sníží svého operandu o 1. Operand musí být proměnná [vlastnost](../../programming-guide/classes-and-structs/properties.md) přístup, nebo [indexer](../../../csharp/programming-guide/indexers/index.md) přístup.

Operátor dekrementace je podporován ve dvou formách: příponového operátoru dekrementace `x--`a operátor dekrementace předpony `--x`.

### <a name="postfix-decrement-operator"></a>Příponový operátor dekrementace

Výsledek `x--` je hodnota `x` *před* operace, jako v následujícím příkladu:

[!code-csharp-interactive[postfix decrement](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#PostfixDecrement)]

### <a name="prefix-decrement-operator"></a>Operátor dekrementace předpony

Výsledek `--x` je hodnota `x` *po* operace, jako v následujícím příkladu:

[!code-csharp-interactive[prefix decrement](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#PrefixDecrement)]

## <a name="unary-plus-and-minus-operators"></a>Unární plus a minus operátory

Unární `+` operátor vrátí hodnotu svého operandu. Unární `-` operátor vypočítá negaci číselného svého operandu.

[!code-csharp-interactive[unary plus and minus](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#UnaryPlusAndMinus)]

Unární `-` operátor nepodporuje [ulong](../keywords/ulong.md) typu.

## <a name="multiplication-operator-"></a>Operátor násobení *

Operátor násobení `*` vypočítá součin z operandů:

[!code-csharp-interactive[multiplication operator](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#Multiplication)]

Unární `*` operátor je [operátor dereference ukazatele](multiplication-operator.md#pointer-indirection-operator).

## <a name="division-operator-"></a>Operátor dělení /

Operátor dělení `/` rozděluje svůj první operand tak svým druhým operandem.

### <a name="integer-division"></a>Celočíselné dělení

Pro operandy typy celých čísel, výsledek `/` operátor je typu integer a rovnosti podílu dvou operandů zaokrouhlena směrem k nule.:

[!code-csharp-interactive[integer division](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#IntegerDivision)]

Chcete-li získat podílu dvou operandů jako číslo s plovoucí desetinnou čárkou, použijte `float`, `double`, nebo `decimal` typu:

[!code-csharp-interactive[integer as floating-point division](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#IntegerAsFloatingPointDivision)]

### <a name="floating-point-division"></a>S plovoucí desetinnou čárkou dělení

Pro `float`, `double`, a `decimal` typy, výsledek `/` operátor odpovídá podílu dvou operandů:

[!code-csharp-interactive[floating-point division](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#FloatingPointDivision)]

Pokud jeden z operandů je `decimal`, může být jiný operand ani `float` ani `double`, protože ani `float` ani `double` implicitně převést na `decimal`. Je nutné explicitně převést `float` nebo `double` operand `decimal` typu. Další informace o implicitní převody mezi číselnými typy najdete v tématu [tabulka implicitních číselných převodů](../keywords/implicit-numeric-conversions-table.md).

## <a name="remainder-operator-"></a>Zbývající % – operátor

Operátor zbytku `%` vypočítá zbytek po dělení svůj první operand tak svým druhým operandem.

### <a name="integer-remainder"></a>Zbývající celé číslo
  
Pro operandy typy celých čísel, výsledek `a % b` hodnota vytvořil `a - (a / b) * b`. Znaménko nenulové zbývající je stejný jako první operand, jako v následujícím příkladu:

[!code-csharp-interactive[integer remainder](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#IntegerRemainder)]

Použití <xref:System.Math.DivRem%2A?displayProperty=nameWithType> metodu za účelem výpočtu dělení celého čísla a zbytek výsledky.

### <a name="floating-point-remainder"></a>Zbytek s plovoucí desetinnou čárkou

Pro `float` a `double` operandy, výsledek `x % y` pro omezenou `x` a `y` je hodnota `z` tak, aby

- Znaménko `z`nenulová, pokud je stejný jako znaménko `x`.
- absolutní hodnota `z` hodnota vytvořil `|x| - n * |y|` kde `n` je největší možné číslo, které je menší než nebo rovna hodnotě `|x| / |y|` a `|x|` a `|y|` jsou absolutní hodnoty `x` a `y`v uvedeném pořadí.

> [!NOTE]
> Tato metoda výpočetních zbytek je obdobou, který používá pro celočíselné operandy, ale se liší od IEEE 754. Pokud potřebujete zbývající operace, která splňuje IEEE 754, použijte <xref:System.Math.IEEERemainder%2A?displayProperty=nameWithType> metody.

Informace o chování `%` operátor s nekonečnou operandy, najdete v článku [operátor zbytku](~/_csharplang/spec/expressions.md#remainder-operator) část [ C# specifikace jazyka](~/_csharplang/spec/introduction.md).

Pro `decimal` operandy, operátor zbytku `%` odpovídá [operátor zbytku](<xref:System.Decimal.op_Modulus(System.Decimal,System.Decimal)>) z <xref:System.Decimal?displayProperty=nameWithType> typu.

Následující příklad ukazuje chování operátoru zbytek s plovoucí desetinnou čárkou operandy:

[!code-csharp-interactive[floating-point remainder](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#FloatingPointRemainder)]

## <a name="addition-operator-"></a>Operátor sčítání +

Operátor sčítání `+` kód vypočítá součet operandů:

[!code-csharp-interactive[addition operator](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#Addition)]

Můžete také použít `+` operátoru pro zřetězení a delegátem kombinaci řetězec. Další informace najdete v tématu [ `+` operátor](addition-operator.md) článku.

## <a name="subtraction-operator--"></a>Operátor odčítání-

Operátor odčítání `-` odečte jeho druhého operandu od jeho prvního operandu:

[!code-csharp-interactive[subtraction operator](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#Subtraction)]

Můžete také použít `-` operátor pro odebrání delegátů. Další informace najdete v tématu [ `-` operátor](subtraction-operator.md) článku.

## <a name="operator-precedence-and-associativity"></a>Priorita a asociativita operátora

V následujícím seznamu objednávek od nejvyšší priority k nejnižší aritmetické operátory:

- Zvýšení příponového operátora `x++` a dekrementace `x--` operátory
- Předponového `++x` a dekrementace `--x` a unární `+` a `-` operátory
- Multiplikativní `*`, `/`, a `%` operátory
- Additive `+` a `-` operátory

Binární aritmetické operátory jsou asociativní zprava doleva. To znamená, že operátory se stejnou úrovní priority jsou vyhodnoceny zleva doprava.

Použít závorky, `()`, chcete-li změnit pořadí vyhodnocování stanovené prioritou operátorů a asociativity.

[!code-csharp-interactive[precedence and associativity](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#PrecedenceAndAssociativity)]

Pro úplný seznam C# operátory seřazené podle úrovně priority, naleznete v tématu [ C# operátory](index.md).

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

Následující příklad ukazuje použití aritmetické operátory složeného přiřazení:

[!code-csharp-interactive[compound assignment](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#CompoundAssignment)]

Z důvodu [číselné propagace](~/_csharplang/spec/expressions.md#numeric-promotions), výsledek `op` operace může být implicitně převést na typ `T` z `x`. V takovém případě pokud `op` je předdefinovaný operátor a výsledek operace je výslovně převeditelný na typ `T` z `x`, výraz složeného přiřazení formuláře `x op= y` je ekvivalentní `x = (T)(x op y)`, s výjimkou který `x` se jenom vyhodnotí jednou. Následující příklad ukazuje toto chování:

[!code-csharp-interactive[compound assignment with cast](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#CompoundAssignmentWithCast)]

Můžete také použít `+=` a `-=` operátorů sloužící k přihlášení a odhlášení [události](../keywords/event.md). Další informace najdete v tématu [postupy: přihlášení k odběru a zrušit její odběr události](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).

## <a name="arithmetic-overflow-and-division-by-zero"></a>Aritmetické přetečení a dělení nulou

Když výsledek aritmetické operace je mimo rozsah možných hodnot omezené zahrnutých číselného typu, chování aritmetickém operátoru závisí na typu operandů.

### <a name="integer-arithmetic-overflow"></a>Aritmetické přetečení celého čísla

Dělení celého čísla nulou vždy vyvolá <xref:System.DivideByZeroException>.

V případě aritmetické přetečení celého čísla, přetečení kontrola kontextu, což může být [zaškrtnuté nebo nezaškrtnuté](../keywords/checked-and-unchecked.md), řídí výsledné chování:

- Ve zkontrolovaném kontextu Pokud v konstantním výrazu se stane přetečení, dojde k chybě kompilace. Jinak, pokud se operace provádí za běhu, <xref:System.OverflowException> je vyvolána výjimka.
- V nekontrolovaném kontextu výsledek je rozdělená do se zahodí všechny bity nejvyšším, které se nehodí do cílového typu.

Spolu s [zaškrtnuto a nezaškrtnuto](../keywords/checked-and-unchecked.md) příkazy, můžete použít `checked` a `unchecked` operátory ovládající kontroly kontext, ve kterém je výraz vyhodnocen přetečení:

[!code-csharp-interactive[checked and unchecked](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#CheckedUnchecked)]

Ve výchozím nastavení, aritmetické operace prováděny v *Nekontrolovaná* kontextu.

### <a name="floating-point-arithmetic-overflow"></a>Plovoucí aritmetické přetečení

Aritmetické operace s `float` a `double` typy nikdy nevyvolají výjimku. Výsledek aritmetické operace s těmito typy může být jedna z speciálními hodnotami, které představují nekonečno a not-a-number:

[!code-csharp-interactive[double non-finite values](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#FloatingPointOverflow)]

Pro operandy `decimal` typ aritmetické přetečení vždy vyvolá výjimku <xref:System.OverflowException> a dělení nulou vždy vyvolá výjimku <xref:System.DivideByZeroException>.

## <a name="round-off-errors"></a>Zaokrouhlovací chyby

Z důvodu obecné omezení reprezentace plovoucí desetinné čárky reálná čísla a aritmetické operace s plovoucí desetinnou čárkou může dojít k chybám zaokrouhlovací ve výpočtech s typy s plovoucí desetinnou čárkou. Vyprodukované výsledek výrazu tedy mohou lišit od očekávaný výsledek matematické. Následující příklad ukazuje několik těchto případech:

[!code-csharp-interactive[round-off errors](~/samples/snippets/csharp/language-reference/operators/ArithmeticOperators.cs#RoundOffErrors)]

Další informace najdete v části poznámky v [System.Double](/dotnet/api/system.double#remarks), [System.Single](/dotnet/api/system.single#remarks), nebo [System.Decimal](/dotnet/api/system.decimal#remarks) odkazují na stránky.

## <a name="operator-overloadability"></a>Overloadability – operátor

Uživatelem definovaný typ může [přetížení](../keywords/operator.md) unární (`++`, `--`, `+`, a `-`) a binární (`*`, `/`, `%`, `+`a `-`) aritmetické operátory. Pokud je binární operátor přetížen, je také implicitně přetížené odpovídající operátor složeného přiřazení. Uživatelem definovaný typ nejde explicitně přetížit operátor složeného přiřazení.

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace najdete v následující částech [ C# specifikace jazyka](~/_csharplang/spec/introduction.md):

- [Příponové operátory Inkrementace a dekrementace operátory](~/_csharplang/spec/expressions.md#postfix-increment-and-decrement-operators)
- [Předpona Inkrementace a dekrementace operátory](~/_csharplang/spec/expressions.md#prefix-increment-and-decrement-operators)
- [Unárního operátoru plus](~/_csharplang/spec/expressions.md#unary-plus-operator)
- [Unární operátor minus](~/_csharplang/spec/expressions.md#unary-minus-operator)
- [Operátor násobení](~/_csharplang/spec/expressions.md#multiplication-operator)
- [Operátor dělení](~/_csharplang/spec/expressions.md#division-operator)
- [Operátor zbytku](~/_csharplang/spec/expressions.md#remainder-operator)
- [Operátor sčítání](~/_csharplang/spec/expressions.md#addition-operator)
- [Operátor odčítání](~/_csharplang/spec/expressions.md#subtraction-operator)
- [Složené přiřazení](~/_csharplang/spec/expressions.md#compound-assignment)
- [Operátory zaškrtnuto a nezaškrtnuto](~/_csharplang/spec/expressions.md#the-checked-and-unchecked-operators)
- [Číselné propagačních akcí](~/_csharplang/spec/expressions.md#numeric-promotions)

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka C#](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [Operátory jazyka C#](index.md)
- <xref:System.Math?displayProperty=nameWithType>
- <xref:System.MathF?displayProperty=nameWithType>
- [Číslovky v technologii .NET](../../../standard/numerics.md)
