---
title: Operátory jazyka C# – odkaz jazyka C#
ms.date: 04/22/2020
f1_keywords:
- cs.operators
helpviewer_keywords:
- operators [C#]
- operator precedence [C#]
- operator associativity [C#]
- expressions [C#]
ms.assetid: 0301e31f-22ad-49af-ac3c-d5eae7f0ac43
ms.openlocfilehash: fe4adf7df707eff0990e8c731a36d6177df228cf
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102018"
---
# <a name="c-operators-c-reference"></a>Operátory Jazyka C# (odkaz jazyka C#)

C# poskytuje počet operátorů podporovaných předdefinované typy. Například [aritmetické operátory](arithmetic-operators.md) provádějí aritmetické operace s číselnými operandy a [logické operátory boolean](boolean-logical-operators.md) provádějí logické operace s [pílovými](../builtin-types/bool.md) operandy. Některé operátory mohou být [přetížené](operator-overloading.md). S přetížení operátor, můžete určit chování operátoru pro operandy uživatelem definovaného typu.

Ve [výrazu](../../programming-guide/statements-expressions-operators/expressions.md)určuje priorita operátoru a asociativita pořadí, ve kterém jsou operace prováděny. Závorky můžete použít ke změně pořadí hodnocení uloženého prioritou operátora a asociativitou.

## <a name="operator-precedence"></a>Priorita operátorů

Ve výrazu s více operátory jsou operátory s vyšší prioritou vyhodnoceny před operátory s nižší prioritou. V následujícím příkladu se násobení provádí nejprve, protože má vyšší prioritu než sčítání:

```csharp-interactive
var a = 2 + 2 * 2;
Console.WriteLine(a); //  output: 6
```

Pomocí závorek můžete změnit pořadí hodnocení uloženého prioritou operátoru:

```csharp-interactive
var a = (2 + 2) * 2;
Console.WriteLine(a); //  output: 8
```

V následující tabulce jsou uvedeny operátory jazyka C#, které začínají nejvyšší prioritou na nejnižší. Operátory v rámci každého řádku mají stejnou prioritu.

| Operátory | Kategorie nebo název |
| --------- | ---------------- |
| [x.y](member-access-operators.md#member-access-expression-), [f(x)](member-access-operators.md#invocation-expression-), [a&#91;i&#93;](member-access-operators.md#indexer-operator-), [x++](arithmetic-operators.md#increment-operator-), [x--](arithmetic-operators.md#decrement-operator---), [x!](null-forgiving.md), [new](new-operator.md), [typeof](type-testing-and-cast.md#typeof-operator), [checked](../keywords/checked.md), [unchecked](../keywords/unchecked.md), [default](default.md), [nameof](nameof.md), [delegate](delegate-operator.md), [sizeof](sizeof.md), [stackalloc](stackalloc.md), [x->y](pointer-related-operators.md#pointer-member-access-operator--) | Primární |
| [+x](arithmetic-operators.md#unary-plus-and-minus-operators), [-x](arithmetic-operators.md#unary-plus-and-minus-operators), [ \!x](boolean-logical-operators.md#logical-negation-operator-), [~x](bitwise-and-shift-operators.md#bitwise-complement-operator-), [++x](arithmetic-operators.md#increment-operator-), [--x](arithmetic-operators.md#decrement-operator---), [^x](member-access-operators.md#index-from-end-operator-), [x?. y](member-access-operators.md#null-conditional-operators--and-), [x?[ y]](member-access-operators.md#null-conditional-operators--and-), [(T)x](type-testing-and-cast.md#cast-expression), [await](await.md), [&x](pointer-related-operators.md#address-of-operator-), [*x](pointer-related-operators.md#pointer-indirection-operator-), [true and false](true-false-operators.md) | Unární |
| [X.. Y](member-access-operators.md#range-operator-) | Rozsah |
| [switch](../../whats-new/csharp-8.md#switch-expressions) | `switch`Výraz |
| [x * y](arithmetic-operators.md#multiplication-operator-), [x / y](arithmetic-operators.md#division-operator-), x % [y](arithmetic-operators.md#remainder-operator-) | Multiplikativní|
| [x + y](arithmetic-operators.md#addition-operator-), [x – y](arithmetic-operators.md#subtraction-operator--) | Doplňkové látky |
| [ \< x \< y](bitwise-and-shift-operators.md#left-shift-operator-), [x >> y](bitwise-and-shift-operators.md#right-shift-operator-) | Shift |
| [x \< y](comparison-operators.md#less-than-operator-), [x > y](comparison-operators.md#greater-than-operator-), x [ \<= y](comparison-operators.md#less-than-or-equal-operator-), x >= [y](comparison-operators.md#greater-than-or-equal-operator-), [je](type-testing-and-cast.md#is-operator) [jako](type-testing-and-cast.md#as-operator) | Relační a typové testování |
| [x == y](equality-operators.md#equality-operator-), [x != y](equality-operators.md#inequality-operator-) | Rovnost |
| `x & y` | [Logická logická a](boolean-logical-operators.md#logical-and-operator-) nebo [bitová logická and](bitwise-and-shift-operators.md#logical-and-operator-) |
| `x ^ y` | [Logická logická XOR](boolean-logical-operators.md#logical-exclusive-or-operator-) nebo [bitová logická XOR](bitwise-and-shift-operators.md#logical-exclusive-or-operator-) |
| <code>x &#124; y</code> | [Logická logická nebo](boolean-logical-operators.md#logical-or-operator-) [bitová logická nebo](bitwise-and-shift-operators.md#logical-or-operator-) |
| [x && y](boolean-logical-operators.md#conditional-logical-and-operator-) | Podmiňovací operátor AND |
| [x &#124;&#124; y](boolean-logical-operators.md#conditional-logical-or-operator-) | Podmiňovací operátor OR |
| [X?? Y](null-coalescing-operator.md) | Operátor null-coalescing |
| [C? t : f](conditional-operator.md) | Podmíněný operátor |
| [x = y](assignment-operator.md), [x += y](arithmetic-operators.md#compound-assignment), x [-= y](arithmetic-operators.md#compound-assignment), x [*= y](arithmetic-operators.md#compound-assignment), x [/= y](arithmetic-operators.md#compound-assignment), x [%= y](arithmetic-operators.md#compound-assignment), x &= [y](boolean-logical-operators.md#compound-assignment), x &#124;[= y](boolean-logical-operators.md#compound-assignment), x [^= y](boolean-logical-operators.md#compound-assignment), x <<= [y](bitwise-and-shift-operators.md#compound-assignment), x >>[= y](bitwise-and-shift-operators.md#compound-assignment), x [x ?? = y](null-coalescing-operator.md),[=>](lambda-operator.md) | Prohlášení o postoupení a lambdě |

## <a name="operator-associativity"></a>Asociativita operátora

Pokud mají operátory stejnou prioritu, asociativity operátorů určuje pořadí, ve kterém jsou operace prováděny:

- *Levé asociativní* operátory jsou vyhodnocovány v pořadí zleva doprava. S výjimkou [operátorů přiřazení](assignment-operator.md) a [operátorů null-coalescing](null-coalescing-operator.md)jsou všechny binární operátory levosociativní. Například `a + b - c` je vyhodnocen jako `(a + b) - c`.
- *Pravoasociativní* operátory jsou vyhodnocovány v pořadí zprava doleva. Operátory přiřazení, null-coalescing operátory a [podmíněné operátory `?:` ](conditional-operator.md) jsou právo asociativní. Například `x = y = z` je vyhodnocen jako `x = (y = z)`.

Pomocí závorek můžete změnit pořadí hodnocení uloženého asociativitou operátora:

```csharp-interactive
int a = 13 / 5 / 2;
int b = 13 / (5 / 2);
Console.WriteLine($"a = {a}, b = {b}");  // output: a = 1, b = 6
```

## <a name="operand-evaluation"></a>Vyhodnocení operandu

Operandy ve výrazu, které nesouvisí s prioritou operátoru a asociátností, jsou vyhodnocovány zleva doprava. Následující příklady ukazují pořadí, ve kterém jsou vyhodnocovány operátory a operandy:

| Expression | Pořadí vyhodnocení |
| ---------- | ------------------- |
|`a + b`|a, b, +|
|`a + b * c`|a, b, c, *, +|
|`a / b + c * d`|a, b, /, c, d, *, +|
|`a / (b + c) * d`|a, b, c, +, /, d, *|

Obvykle jsou vyhodnocovány všechny operandy operátorů. Některé operátory však operaty vyhodnocují podmíněně. To znamená, že hodnota operandu zcela vlevo takového operátoru definuje, zda (nebo které) by měly být vyhodnoceny jiné operandy. Tyto operátory jsou podmíněné logické [operátory`&&`AND ( )](boolean-logical-operators.md#conditional-logical-and-operator-) a OR ( [),`||`](boolean-logical-operators.md#conditional-logical-or-operator-) [operátory `??` null-coalescing a `??=` ](null-coalescing-operator.md), [operátory `?.` s nulovým podmíněným podmínkami a `?[]` ](member-access-operators.md#null-conditional-operators--and-)operátor a podmíněný [operátor `?:` ](conditional-operator.md). Další informace naleznete v popisu každého operátora.

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace naleznete v části [Operátoři](~/_csharplang/spec/expressions.md#operators) ve [specifikaci jazyka C#](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Viz také

- [Referenční dokumentace k jazyku C#](../index.md)
- [Výrazy](../../programming-guide/statements-expressions-operators/expressions.md)
