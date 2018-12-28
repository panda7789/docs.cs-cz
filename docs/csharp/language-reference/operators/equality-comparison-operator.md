---
title: == – Operátor - C# odkaz
ms.custom: seodec18
ms.date: 12/14/2018
f1_keywords:
- ==_CSharpKeyword
helpviewer_keywords:
- == operator [C#]
- equality operator [C#]
ms.assetid: 34c6b597-caa2-4855-a7cd-38ecdd11bd07
ms.openlocfilehash: 6d86348eefc87e847267f262141ff49e5d51faae
ms.sourcegitcommit: 3d0c29b878f00caec288dfecb3a5c959de5aa629
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/20/2018
ms.locfileid: "53655956"
---
# <a name="-operator-c-reference"></a>== – operátor (Referenční dokumentace jazyka C#)

Operátor rovnosti `==` vrátí `true` pokud jeho operandy jsou si rovny, `false` jinak.

## <a name="value-types-equality"></a>Rovnost pro typy hodnot

Operandy [integrované hodnotách](../keywords/value-types-table.md) jsou si rovny, pokud jsou si rovny jejich hodnoty:

[!code-csharp-interactive[value types equality](~/samples/snippets/csharp/language-reference/operators/EqualityAndNonEqualityExamples.cs#ValueTypesEquality)]

> [!NOTE]
> Pro relační operátory `==`, `>`, `<`, `>=`, a `<=`, pokud žádný z operandů není číslo (<xref:System.Double.NaN?displayProperty=nameWithType> nebo <xref:System.Single.NaN?displayProperty=nameWithType>) je výsledek operace `false`. To znamená, že `NaN` hodnota není větší než, menší než, ani jakýkoli jiný roven `double` (nebo `float`) hodnotu. Další informace a příklady najdete v tématu <xref:System.Double.NaN?displayProperty=nameWithType> nebo <xref:System.Single.NaN?displayProperty=nameWithType> článku.

Dva operandy stejného [výčtu](../keywords/enum.md) typu jsou si rovny, pokud jsou si rovny odpovídající hodnoty základní celočíselného typu.

Ve výchozím nastavení `==` operátor není definovaný pro uživatelem definované [struktura](../keywords/struct.md) typu. Uživatelem definovaný typ může [přetížení](#operator-overloadability) `==` operátor.

Počínaje C# 7.3, `==` a [ `!=` ](not-equal-operator.md) operátory jsou podporovány C# [řazených kolekcí členů](../../tuples.md). Další informace najdete v tématu [rovnosti a n-tice](../../tuples.md#equality-and-tuples) část [ C# typy řazené kolekce členů](../../tuples.md) článku.

## <a name="string-equality"></a>Rovnosti řetězce

Dvě [řetězec](../keywords/string.md) operandy jsou stejné, pokud jsou obě z nich `null` nebo obě instance řetězce se stejnou délkou a mají stejné znaky v každé pozici znaku:

[!code-csharp-interactive[string equality](~/samples/snippets/csharp/language-reference/operators/EqualityAndNonEqualityExamples.cs#StringEquality)]

Je to velká a malá písmena ordinálního porovnání. Další informace o tom, jak porovnat řetězce najdete v tématu [porovnávání řetězců v C# ](../../how-to/compare-strings.md).

## <a name="reference-types-equality"></a>Referenční rovnost typy

Dvě jiných než `string` operandy typu odkaz jsou stejné, až si do stejného objektu:

[!code-csharp-interactive[reference type equality](~/samples/snippets/csharp/language-reference/operators/EqualityAndNonEqualityExamples.cs#ReferenceTypesEquality)]

Tento příklad ukazuje, že `==` operátor podporuje typy odkazů definované uživatelem. Však můžete přetížit typ definovaný uživatelem odkazu `==` operátor. Pokud typ odkazu přetížení `==` operátoru, použijte <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> metodu ke kontrole, pokud dva odkazy tohoto typu odkazují na stejný objekt.

## <a name="operator-overloadability"></a>Overloadability – operátor

Uživatelem definované typy lze [přetížení](../keywords/operator.md) `==` operátor. Pokud typ přetížení operátoru rovnosti `==`, musíte také přetížit [operátor nerovnosti](not-equal-operator.md) `!=`.

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace najdete v tématu [relační a typové zkoušky operátory](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) část [ C# specifikace jazyka](../language-specification/index.md).

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka C#](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [Operátory jazyka C#](index.md)
- [Porovnání rovnosti](../../programming-guide/statements-expressions-operators/equality-comparisons.md)
