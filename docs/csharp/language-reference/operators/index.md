---
title: Operátory a výrazy jazyka c# – reference jazyka C#
description: Další informace o operátorech a výrazech jazyka C#, prioritě operátorů a operátoru asociativita
ms.date: 08/04/2020
f1_keywords:
- cs.operators
helpviewer_keywords:
- operators [C#]
- operator precedence [C#]
- operator associativity [C#]
- expressions [C#]
ms.assetid: 0301e31f-22ad-49af-ac3c-d5eae7f0ac43
ms.openlocfilehash: 854d7c1278319869104e1758ba91eb3594741126
ms.sourcegitcommit: 7476c20d2f911a834a00b8a7f5e8926bae6804d9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/11/2020
ms.locfileid: "88063182"
---
# <a name="c-operators-and-expressions-c-reference"></a>Operátory a výrazy jazyka c# (Referenční dokumentace jazyka C#)

Jazyk C# poskytuje řadu operátorů. Mnohé z nich jsou podporovány [integrovanými typy](../builtin-types/built-in-types.md) a umožňují provádět základní operace s hodnotami těchto typů. Tyto operátory zahrnují následující skupiny:

- [Aritmetické operátory](arithmetic-operators.md) , které provádějí aritmetické operace s číselnými operandy
- [Operátory porovnání](comparison-operators.md) , které porovnávají číselné operandy
- Logické [logické operátory](boolean-logical-operators.md) , které provádějí logické operace s [`bool`](../builtin-types/bool.md) operandy
- [Operátory bitových a posunutí](bitwise-and-shift-operators.md) , které provádějí operace bitového nebo posunutí s operandy integrálních typů
- [Operátory rovnosti](equality-operators.md) , které kontrolují, jestli jsou jejich operandy stejné

Obvykle můžete tyto operátory [přetížit](operator-overloading.md) , to znamená, určit chování operátoru pro operandy uživatelsky definovaného typu.

Nejjednodušší výrazy jazyka C# jsou literály (například [celočíselné](../builtin-types/integral-numeric-types.md#integer-literals) a [reálné](../builtin-types/floating-point-numeric-types.md#real-literals) číslo) a názvy proměnných. Můžete je kombinovat do složitých výrazů pomocí operátorů. [Priorita](#operator-precedence) operátorů a [asociativita](#operator-associativity) určují pořadí, ve kterém se provádí operace ve výrazu. Pomocí závorek můžete změnit pořadí vyhodnocování stanovené prioritou operátoru a asociativita.

V následujícím kódu jsou příklady výrazů na pravé straně přiřazení:

[!code-csharp[expression examples](snippets/shared/Overview.cs#Expressions)]

Výraz obvykle generuje výsledek a může být zahrnut do jiného výrazu. [`void`](../builtin-types/void.md)Volání metody je příklad výrazu, který neprodukuje výsledek. Dá se použít jenom jako [příkaz](../../programming-guide/statements-expressions-operators/statements.md), jak ukazuje následující příklad:

```csharp
Console.WriteLine("Hello, world!");
```

Tady jsou některé další druhy výrazů, které poskytuje jazyk C#:

- [Interpolované řetězcové výrazy](../tokens/interpolated.md) , které poskytují pohodlný Syntax pro vytváření formátovaných řetězců:

  [!code-csharp-interactive[interpolated string](snippets/shared/Overview.cs#InterpolatedString)]

- [Výrazy lambda](lambda-expressions.md) , které umožňují vytváření anonymních funkcí:

  [!code-csharp-interactive[lambda expression](snippets/shared/Overview.cs#Lambda)]

- [Výrazy dotazů](../keywords/query-keywords.md) , které umožňují použití možností dotazů přímo v jazyce C#:

  [!code-csharp-interactive[query expression](snippets/shared/Overview.cs#Query)]

[Definici těla výrazu](../../programming-guide/statements-expressions-operators/expression-bodied-members.md) můžete použít k poskytnutí stručné definice metody, konstruktoru, vlastnosti, indexeru nebo finalizační metody.

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

V následující tabulce jsou uvedeny operátory jazyka C# začínající nejvyšší prioritou až nejnižší. Operátory v rámci jednotlivých řádků mají stejnou prioritu.

| Operátory | Kategorie nebo název |
| --------- | ---------------- |
| [x. y](member-access-operators.md#member-access-expression-), [f (x)](member-access-operators.md#invocation-expression-), [&#91;i&#93;](member-access-operators.md#indexer-operator-), [`x?.y`](member-access-operators.md#null-conditional-operators--and-) , [`x?[y]`](member-access-operators.md#null-conditional-operators--and-) , [x + +](arithmetic-operators.md#increment-operator-), [x--](arithmetic-operators.md#decrement-operator---), [x!](null-forgiving.md), [New](new-operator.md), [typeof](type-testing-and-cast.md#typeof-operator), [checked](../keywords/checked.md), [unchecked](../keywords/unchecked.md), [Default](default.md), [nameof](nameof.md), [Delegate](delegate-operator.md), [sizeof](sizeof.md), [stackalloc](stackalloc.md), [x->y](pointer-related-operators.md#pointer-member-access-operator--) | Primární |
| [+ x](arithmetic-operators.md#unary-plus-and-minus-operators), [-x](arithmetic-operators.md#unary-plus-and-minus-operators), [ \! x](boolean-logical-operators.md#logical-negation-operator-), [~ x](bitwise-and-shift-operators.md#bitwise-complement-operator-), [+ + x](arithmetic-operators.md#increment-operator-), [--x](arithmetic-operators.md#decrement-operator---), [^ x](member-access-operators.md#index-from-end-operator-), [(T) x](type-testing-and-cast.md#cast-expression), [await](await.md), [&x](pointer-related-operators.md#address-of-operator-), [* x](pointer-related-operators.md#pointer-indirection-operator-), [true a false](true-false-operators.md) | Unární |
| [x.. požadované](member-access-operators.md#range-operator-) | Rozsah |
| [switch](switch-expression.md) | `switch`vyjádření |
| [x * y](arithmetic-operators.md#multiplication-operator-), [x/y](arithmetic-operators.md#division-operator-), [x% y](arithmetic-operators.md#remainder-operator-) | Multiplikativní|
| [x + y](arithmetic-operators.md#addition-operator-), [x – y](arithmetic-operators.md#subtraction-operator--) | Aditivní |
| [x \<\<  y](bitwise-and-shift-operators.md#left-shift-operator-), [x >> y](bitwise-and-shift-operators.md#right-shift-operator-) | Posouvá |
| [x \< y](comparison-operators.md#less-than-operator-), [x > y](comparison-operators.md#greater-than-operator-), [x \<= y](comparison-operators.md#less-than-or-equal-operator-), [x > = y](comparison-operators.md#greater-than-or-equal-operator-), [je](type-testing-and-cast.md#is-operator), [jako](type-testing-and-cast.md#as-operator) | Relační testování a testování typu |
| [x = = y](equality-operators.md#equality-operator-), [x! = y](equality-operators.md#inequality-operator-) | Rovnost |
| `x & y` | Logická [logický operátor and](boolean-logical-operators.md#logical-and-operator-) nebo [BITOVÝ logický operátor and](bitwise-and-shift-operators.md#logical-and-operator-) |
| `x ^ y` | [Logická logická hodnota XOR](boolean-logical-operators.md#logical-exclusive-or-operator-) nebo [bitový logický operátor XOR](bitwise-and-shift-operators.md#logical-exclusive-or-operator-) |
| <code>x &#124; y</code> | Logická nebo logická logická [hodnota](boolean-logical-operators.md#logical-or-operator-) [nebo](bitwise-and-shift-operators.md#logical-or-operator-) |
| [x && y](boolean-logical-operators.md#conditional-logical-and-operator-) | Podmiňovací operátor AND |
| [x &#124;&#124; y](boolean-logical-operators.md#conditional-logical-or-operator-) | Podmiňovací operátor OR |
| [x?? požadované](null-coalescing-operator.md) | Operátor slučování null |
| [r? t: f](conditional-operator.md) | Podmíněný operátor |
| [x = y](assignment-operator.md), [x + = y](arithmetic-operators.md#compound-assignment), [x-= y](arithmetic-operators.md#compound-assignment), [x * = y](arithmetic-operators.md#compound-assignment), [x/= y](arithmetic-operators.md#compound-assignment), [x% = y](arithmetic-operators.md#compound-assignment), [x &= y](boolean-logical-operators.md#compound-assignment), [x &#124;= y](boolean-logical-operators.md#compound-assignment), [x ^ = y](boolean-logical-operators.md#compound-assignment), [x <<= y](bitwise-and-shift-operators.md#compound-assignment), [x >>= y](bitwise-and-shift-operators.md#compound-assignment), x [?? = y](null-coalescing-operator.md),[=>](lambda-operator.md) | Přiřazení a deklarace lambda |

## <a name="operator-associativity"></a>Operátor asociativita

Pokud mají operátory stejnou prioritu, asociativita operátor určuje pořadí, ve kterém jsou operace provedeny:

- Operátory *asociativní zleva* jsou vyhodnocovány v pořadí zleva doprava. S výjimkou [operátorů přiřazení](assignment-operator.md) a [operátorů slučování null](null-coalescing-operator.md)jsou všechny binární operátory asociativní. Například `a + b - c` je vyhodnocen jako `(a + b) - c` .
- Operátory *asociativní zprava* jsou vyhodnocovány v pořadí zprava doleva. Operátory přiřazení, operátory slučování null a [podmíněný operátor `?:` ](conditional-operator.md) jsou asociativní zprava. Například `x = y = z` je vyhodnocen jako `x = (y = z)` .

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

Obvykle jsou vyhodnocovány všechny operandy operátoru. Některé operátory však vyhodnocuje operandy podmíněně. To znamená, že hodnota operandu úplně vlevo takového operátoru definuje, zda má být vyhodnocen (nebo které) jiné operandy. Tyto operátory jsou podmínkou podmíněného logického operátoru [and ( `&&` )](boolean-logical-operators.md#conditional-logical-and-operator-) a [OR ( `||` )](boolean-logical-operators.md#conditional-logical-or-operator-) , [operátory sloučení s hodnotou null `??` a `??=` ](null-coalescing-operator.md) [operátory `?.` `?[]` s hodnotou null ](member-access-operators.md#null-conditional-operators--and-)a [podmíněný operátor `?:` ](conditional-operator.md). Další informace naleznete v popisu každého operátoru.

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace naleznete v následujících oddílech [specifikace jazyka C#](~/_csharplang/spec/introduction.md):

- [Výrazy](~/_csharplang/spec/expressions.md)
- [Operátory](~/_csharplang/spec/expressions.md#operators)

## <a name="see-also"></a>Viz také

- [Referenční dokumentace k jazyku C#](../index.md)
- [Přetěžování operátoru](operator-overloading.md)
- [Stromy výrazů](../../programming-guide/concepts/expression-trees/index.md)
