---
title: C#operátory – C# referenční informace
ms.date: 08/20/2019
f1_keywords:
- cs.operators
helpviewer_keywords:
- operators [C#]
- operator precedence [C#]
- operator associativity [C#]
- expressions [C#]
ms.assetid: 0301e31f-22ad-49af-ac3c-d5eae7f0ac43
ms.openlocfilehash: 75697a7a52fbfb04e1b44ecf591e271217a69bf4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69924650"
---
# <a name="c-operators-c-reference"></a>C#operátory (C# Referenční dokumentace)

C#poskytuje několik operátorů podporovaných integrovanými typy. Například aritmetické [operátory](arithmetic-operators.md) provádějí aritmetické operace s numerickými operandy a logické [logické operátory](boolean-logical-operators.md) provádějí logické operace s [](../keywords/bool.md) logickými operandy. Některé operátory mohou být [přetíženy](operator-overloading.md). S přetížením operátorů můžete určit chování operátoru pro operandy uživatelsky definovaného typu.

Ve [výrazu](../../programming-guide/statements-expressions-operators/expressions.md), priority operátoru a asociativita určují pořadí, ve kterém jsou operace prováděny. Pomocí závorek můžete změnit pořadí vyhodnocování stanovené prioritou operátoru a asociativita.

## <a name="operator-precedence"></a>Priorita operátorů

Ve výrazu s více operátory jsou operátory s vyšší prioritou vyhodnocovány před operátory s nižší prioritou. V následujícím příkladu je násobení provedeno jako první, protože má vyšší prioritu než přidání:

```csharp-interactive
var a = 2 + 2 * 2;
Console.WriteLine(a); //  output: 6
```

Chcete-li změnit pořadí vyhodnocování stanovené předností operátorů, použijte závorky:

```csharp-interactive
var a = (2 + 2) * 2;
Console.WriteLine(a); //  output: 8
```

V následující tabulce jsou uvedeny C# operátory od nejvyšší priority k nejnižší. Operátory v rámci jednotlivých řádků mají stejnou prioritu.

| Operátory | Kategorie nebo název |
| --------- | ---------------- |
| [x. y](member-access-operators.md#member-access-operator-), [x?. y](member-access-operators.md#null-conditional-operators--and-), [x? [ y]](member-access-operators.md#null-conditional-operators--and-), [f (x)](member-access-operators.md#invocation-operator-), [a&#91;i&#93;](member-access-operators.md#indexer-operator-), [x + +](arithmetic-operators.md#increment-operator-), [x--](arithmetic-operators.md#decrement-operator---), [New](new-operator.md), [typeof](type-testing-and-cast.md#typeof-operator), [zaškrtnutí](../keywords/checked.md), [nezaškrtnuto](../keywords/unchecked.md), [Default](default.md), [nameof](nameof.md), [Delegate](delegate-operator.md), [sizeof](sizeof.md), [stackalloc](stackalloc.md), [x-> y](pointer-related-operators.md#pointer-member-access-operator--) | Primární |
| [+ x](arithmetic-operators.md#unary-plus-and-minus-operators), [-x](arithmetic-operators.md#unary-plus-and-minus-operators), [ \!x](boolean-logical-operators.md#logical-negation-operator-), [~ x](bitwise-and-shift-operators.md#bitwise-complement-operator-), [+ + x](arithmetic-operators.md#increment-operator-), [--x](arithmetic-operators.md#decrement-operator---), [(T) x](type-testing-and-cast.md#cast-operator-), [await](../keywords/await.md), [& x](pointer-related-operators.md#address-of-operator-), [* x](pointer-related-operators.md#pointer-indirection-operator-), [true a false](true-false-operators.md) . | Unární |
| [x * y](arithmetic-operators.md#multiplication-operator-), [x/y](arithmetic-operators.md#division-operator-), [x% y](arithmetic-operators.md#remainder-operator-) | Multiplikativní|
| [x + y](arithmetic-operators.md#addition-operator-), [x – y](arithmetic-operators.md#subtraction-operator--) | Přičítáním |
| [ x\< y ,\< ](bitwise-and-shift-operators.md#left-shift-operator-) [x > > y](bitwise-and-shift-operators.md#right-shift-operator-) | SHIFT |
| [x\< y](comparison-operators.md#less-than-operator-), [x > y](comparison-operators.md#greater-than-operator-), [x \<= y](comparison-operators.md#less-than-or-equal-operator-), [x > = y](comparison-operators.md#greater-than-or-equal-operator-), [je](type-testing-and-cast.md#is-operator), [jako](type-testing-and-cast.md#as-operator) | Relační testování a testování typu |
| [x = = y](equality-operators.md#equality-operator-), [x! = y](equality-operators.md#inequality-operator-) | Rovnost |
| `x & y` | Logická [logický operátor and](boolean-logical-operators.md#logical-and-operator-) nebo [BITOVÝ logický operátor and](bitwise-and-shift-operators.md#logical-and-operator-) |
| `x ^ y` | [Logická logická hodnota XOR](boolean-logical-operators.md#logical-exclusive-or-operator-) nebo [bitový logický operátor XOR](bitwise-and-shift-operators.md#logical-exclusive-or-operator-) |
| <code>x &#124; y</code> | Logická nebo logická logická [hodnota](boolean-logical-operators.md#logical-or-operator-) [nebo](bitwise-and-shift-operators.md#logical-or-operator-) |
| [x & & y](boolean-logical-operators.md#conditional-logical-and-operator-) | Podmiňovací operátor AND |
| [× &#124; &#124; y](boolean-logical-operators.md#conditional-logical-or-operator-) | Podmiňovací operátor OR |
| [x?? požadované](null-coalescing-operator.md) | Operátor slučování null |
| [r? t: f](conditional-operator.md) | Podmíněný operátor |
| [x = y](assignment-operator.md), [x + = y](arithmetic-operators.md#compound-assignment), [x-= y](arithmetic-operators.md#compound-assignment), [x * = y](arithmetic-operators.md#compound-assignment), [x/= y](arithmetic-operators.md#compound-assignment), [x% = y](arithmetic-operators.md#compound-assignment), [x & = y](boolean-logical-operators.md#compound-assignment), [x &#124;= y](boolean-logical-operators.md#compound-assignment), [x ^ = y](boolean-logical-operators.md#compound-assignment), [x < < = y](bitwise-and-shift-operators.md#compound-assignment), [x > > = y](bitwise-and-shift-operators.md#compound-assignment),[=>](lambda-operator.md) | Přiřazení a deklarace lambda |

## <a name="operator-associativity"></a>Operátor asociativita

Pokud mají operátory stejnou prioritu, asociativita operátor určuje pořadí, ve kterém jsou operace provedeny:

- Operátory *asociativní zleva* jsou vyhodnocovány v pořadí zleva doprava. S výjimkou operátorů [přiřazení](assignment-operator.md) a [ `??`operátoru slučování null ](null-coalescing-operator.md)jsou všechny binární operátory asociativní. Například `a + b - c` je vyhodnocen jako `(a + b) - c`.
- Operátory *asociativní zprava* jsou vyhodnocovány v pořadí zprava doleva. Operátory přiřazení, operátor `??`slučování null a [podmíněný operátor `?:` ](conditional-operator.md) jsou asociativní zprava. Například `x = y = z` je vyhodnocen jako `x = (y = z)`.

Pomocí závorek změňte pořadí hodnocení, které je asociativita operátorem:

```csharp-interactive
int a = 13 / 5 / 2;
int b = 13 / (5 / 2);
Console.WriteLine($"a = {a}, b = {b}");  // output: a = 1, b = 6
```

## <a name="operand-evaluation"></a>Vyhodnocení operandu

Nesouvisí s prioritou operátorů a asociativita, jsou operandy ve výrazu vyhodnocovány zleva doprava. Následující příklady ukazují pořadí, ve kterém jsou operátory a operandy vyhodnocovány:

| Výraz | Pořadí vyhodnocení |
| ---------- | ------------------- |
|`a + b`|a, b, +|
|`a + b * c`|a, b, c, *, +|
|`a / b + c * d`|a, b,/, c, d, *, +|
|`a / (b + c) * d`|a, b, c, +,/, d, *|

Obvykle jsou vyhodnocovány všechny operandy operátoru. Některé operátory vyhodnocují operandy podmíněně. To znamená, že hodnota prvního operandu takového operátoru definuje, zda (nebo které) by měly být vyhodnoceny jiné operandy. Tyto operátory jsou podmínkou podmíněného logického operátoru [and (`&&`)](boolean-logical-operators.md#conditional-logical-and-operator-) a [OR`||`()](boolean-logical-operators.md#conditional-logical-or-operator-) , operátoru [ `??`nulového ](null-coalescing-operator.md)sjednocení, [podmíněné operátory `?.` s hodnotou null a `?[]` ](member-access-operators.md#null-conditional-operators--and-)a [podmíněný operátor `?:` ](conditional-operator.md). Další podrobnosti najdete v popisu každého operátoru.

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace naleznete v části [operátory](~/_csharplang/spec/expressions.md#operators) ve [ C# specifikaci jazyka](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Viz také:

- [C#odkaz](../index.md)
- [Výrazy](../../programming-guide/statements-expressions-operators/expressions.md)
