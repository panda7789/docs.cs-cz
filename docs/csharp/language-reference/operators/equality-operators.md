---
title: Operátory rovnosti - C# odkaz
ms.date: 03/28/2019
author: pkulikov
f1_keywords:
- ==_CSharpKeyword
- '!=_CSharpKeyword'
helpviewer_keywords:
- equality operator [C#]
- equals operator [C#]
- == operator [C#]
- inequality operator [C#]
- not equals operator [C#]
- '!= operator [C#]'
ms.openlocfilehash: 98b96f5b4c6d6ea70687a97c849e89573c67c37e
ms.sourcegitcommit: 4a8c2b8d0df44142728b68ebc842575840476f6d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/28/2019
ms.locfileid: "58545878"
---
# <a name="equality-operators-c-reference"></a>Operátory rovnosti (C# odkaz)

[ `==` (Rovnost)](#equality-operator-) a [ `!=` (nerovnost)](#inequality-operator-) operátory zkontrolujte, jestli operandy jsou stejné, nebo ne.

## <a name="equality-operator-"></a>Operátor rovnosti ==

Operátor rovnosti `==` vrátí `true` pokud jeho operandy jsou si rovny, `false` jinak.

### <a name="value-types-equality"></a>Rovnost pro typy hodnot

Operandy [integrované hodnotách](../keywords/value-types-table.md) jsou si rovny, pokud jsou si rovny jejich hodnoty:

[!code-csharp-interactive[value types equality](~/samples/snippets/csharp/language-reference/operators/EqualityAndNonEqualityExamples.cs#ValueTypesEquality)]

> [!NOTE]
> Rovnost a relační operátory `==`, `>`, `<`, `>=`, a `<=`, pokud žádný z operandů není číslo (<xref:System.Double.NaN?displayProperty=nameWithType> nebo <xref:System.Single.NaN?displayProperty=nameWithType>), je výsledek operace `false`. To znamená, že `NaN` hodnota není větší než, menší než, ani jakýkoli jiný roven `double` (nebo `float`) hodnotu, včetně `NaN`. Další informace a příklady najdete v tématu <xref:System.Double.NaN?displayProperty=nameWithType> nebo <xref:System.Single.NaN?displayProperty=nameWithType> článku.

Dva operandy stejného [výčtu](../keywords/enum.md) typu jsou si rovny, pokud jsou si rovny odpovídající hodnoty základní celočíselného typu.

Uživatelem definované [struktura](../keywords/struct.md) typy se nepodporují `==` operátor ve výchozím nastavení. Pro podporu `==` operátor struktury definované uživatelem musí [přetížení](#operator-overloadability) ho.

Počínaje C# 7.3, `==` a `!=` operátory jsou podporovány C# [řazených kolekcí členů](../../tuples.md). Další informace najdete v tématu [rovnosti a n-tice](../../tuples.md#equality-and-tuples) část [ C# typy řazené kolekce členů](../../tuples.md) článku.

### <a name="string-equality"></a>Rovnosti řetězce

Dvě [řetězec](../keywords/string.md) operandy jsou stejné, pokud jsou obě z nich `null` nebo obě instance řetězce se stejnou délkou a mají stejné znaky v každé pozici znaku:

[!code-csharp-interactive[string equality](~/samples/snippets/csharp/language-reference/operators/EqualityAndNonEqualityExamples.cs#StringEquality)]

Je to velká a malá písmena ordinálního porovnání. Další informace o porovnávání řetězců naleznete v tématu [porovnávání řetězců v C# ](../../how-to/compare-strings.md).

### <a name="reference-types-equality"></a>Referenční rovnost typy

Dvě jiných než `string` operandy typu odkaz jsou stejné, až si do stejného objektu:

[!code-csharp-interactive[reference type equality](~/samples/snippets/csharp/language-reference/operators/EqualityAndNonEqualityExamples.cs#ReferenceTypesEquality)]

Jak ukazuje příklad, uživatelem definované referenční typy podporu `==` operátor ve výchozím nastavení. Však můžete přetížit typ definovaný uživatelem odkazu `==` operátor. Pokud typ odkazu přetížení `==` operátoru, použijte <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> metodu ke kontrole, pokud dva odkazy tohoto typu odkazují na stejný objekt.

## <a name="inequality-operator-"></a>Operátor nerovnosti! =

Operátor nerovnosti `!=` vrátí `true` Pokud nejsou stejné, jeho operandy `false` jinak. Pro operandy [předdefinovaných typů](../keywords/built-in-types-table.md), výraz `x != y` vytváří stejný výsledek jako výraz `!(x == y)`. Další informace o typu rovnosti, najdete v článku [operátor rovnosti](#equality-operator-) oddílu.

Následující příklad ukazuje použití `!=` operátor:

[!code-csharp-interactive[non-equality examples](~/samples/snippets/csharp/language-reference/operators/EqualityAndNonEqualityExamples.cs#NonEquality)]

## <a name="operator-overloadability"></a>Overloadability – operátor

Uživatelem definované typy lze [přetížení](../keywords/operator.md) `==` a `!=` operátory. Pokud typ přetížení mezi dva operátory, musíte také přetížit jiný.

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace najdete v tématu [relační a typové zkoušky operátory](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) část [ C# specifikace jazyka](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka C#](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [Operátory jazyka C#](index.md)
- <xref:System.IEquatable%601?displayProperty=nameWithType>
- <xref:System.Object.Equals%2A?displayProperty=nameWithType>
- <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType>
- [Porovnání rovnosti](../../programming-guide/statements-expressions-operators/equality-comparisons.md)