---
title: Operátory rovnosti – odkaz jazyka C#
description: Další informace o operátory porovnání rovnosti Jazyka C# a rovnosti typu C#.
ms.date: 06/26/2019
author: pkulikov
f1_keywords:
- ==_CSharpKeyword
- '!=_CSharpKeyword'
helpviewer_keywords:
- comparison operators [C#]
- relational operators [C#]
- equality operator [C#]
- equals operator [C#]
- == operator [C#]
- inequality operator [C#]
- not equals operator [C#]
- '!= operator [C#]'
ms.openlocfilehash: 079522b18afdf86a942d502672174516d45d37fc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399565"
---
# <a name="equality-operators-c-reference"></a>Operátory rovnosti (odkaz C#)

Operátory [ `==` (rovnosti)](#equality-operator-) a [ `!=` (nerovnosti)](#inequality-operator-) kontrolují, zda jsou jejich operandy stejné nebo ne.

## <a name="equality-operator-"></a>Operátor rovnosti ==

Operátor `==` rovnosti `true` vrátí, pokud jeho operandy jsou stejné, `false` jinak.

### <a name="value-types-equality"></a>Rovnost typů hodnot

Operandy [předdefinovaných typů hodnot](../builtin-types/value-types.md#built-in-value-types) jsou stejné, pokud jsou jejich hodnoty stejné:

[!code-csharp-interactive[value types equality](snippets/EqualityOperators.cs#ValueTypesEquality)]

> [!NOTE]
> Pro `==`, [ `<` `>`, `<=`, `>=` , , a](comparison-operators.md) operátory, pokud některý z operandů `false`není číslo (<xref:System.Double.NaN?displayProperty=nameWithType> nebo <xref:System.Single.NaN?displayProperty=nameWithType>), výsledek operace je . To znamená, `NaN` že hodnota není větší než, menší než, `float`ani rovna `NaN`žádné jiné `double` (nebo ) hodnotu, včetně . Další informace a příklady <xref:System.Double.NaN?displayProperty=nameWithType> naleznete <xref:System.Single.NaN?displayProperty=nameWithType> v článku nebo odkazu.

Dva operandy stejného typu [výčtu](../builtin-types/enum.md) jsou stejné, pokud jsou stejné odpovídající hodnoty základního integrálního typu.

Uživatelem definované typy [struktury](../builtin-types/struct.md) ve `==` výchozím nastavení nepodporují operátor. Pro podporu `==` operátoru musí být struktura definovaná uživatelem [přetížena.](operator-overloading.md)

Počínaje C# 7.3 `==` a `!=` operátory jsou podporovány c# [řazené kolekce členů](../../tuples.md). Další informace naleznete v části [rovnosti a řazené kolekce členů](../../tuples.md#equality-and-tuples) [c# řazené kolekce členů](../../tuples.md) článku.

### <a name="reference-types-equality"></a>Rovnost referenčních typů

Ve výchozím nastavení jsou dva operandy referenčního typu stejné, pokud odkazují na stejný objekt:

[!code-csharp[reference type equality](snippets/EqualityOperators.cs#ReferenceTypesEquality)]

Jak ukazuje příklad, uživatelem definované `==` typy odkazů podporují operátor ve výchozím nastavení. Typ odkazu však může `==` přetížit operátor. Pokud typ odkazu přetíží `==` operátor, použijte metodu <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> ke kontrole, pokud dva odkazy tohoto typu odkazují na stejný objekt.

### <a name="string-equality"></a>Rovnoprávnost řetězců

Dva [řetězcové](../builtin-types/reference-types.md#the-string-type) operandy jsou stejné, když jsou obě instance řetězce `null` nebo obě instance řetězce mají stejnou délku a mají stejné znaky v každé pozici znaku:

[!code-csharp-interactive[string equality](snippets/EqualityOperators.cs#StringEquality)]

To je případově rozlišující řadové srovnání. Další informace o porovnání řetězců naleznete v tématu [Porovnání řetězců v c#](../../how-to/compare-strings.md).

### <a name="delegate-equality"></a>Rovnost delegátů

Dva [operandy delegáta](../../programming-guide/delegates/index.md) stejného typu runtime jsou `null` stejné, když oba jsou nebo jejich seznamy vyvolání mají stejnou délku a mají stejné položky v každé pozici:

[!code-csharp-interactive[delegate equality](snippets/EqualityOperators.cs#DelegateEquality)]

Další informace naleznete v části [Operátory rovnosti delegáta](~/_csharplang/spec/expressions.md#delegate-equality-operators) [specifikace jazyka C#](~/_csharplang/spec/introduction.md).

Delegáti, které jsou vyrobeny z hodnocení sémanticky identické [lambda výrazy](../../programming-guide/statements-expressions-operators/lambda-expressions.md) nejsou stejné, jak ukazuje následující příklad:

[!code-csharp-interactive[from identical lambdas](snippets/EqualityOperators.cs#IdenticalLambdas)]

## <a name="inequality-operator-"></a>Operátor nerovnosti !=

Operátor `!=` nerovnostvrátí, `true` pokud jeho operandy `false` nejsou stejné, jinak. Pro operandy [předdefinovaných typů](../builtin-types/built-in-types.md)výraz `x != y` vytváří stejný výsledek jako `!(x == y)`výraz . Další informace o rovnosti typů naleznete v části [Operátor rovnosti.](#equality-operator-)

Následující příklad ukazuje použití operátoru: `!=`

[!code-csharp-interactive[non-equality examples](snippets/EqualityOperators.cs#NonEquality)]

## <a name="operator-overloadability"></a>Přetížení obsluhy

Uživatelem definovaný typ může `==` `!=` [přetížit](operator-overloading.md) operátory a. Pokud typ přetíží jeden ze dvou operátorů, musí také přetížení jiný.

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace naleznete v části [Relační a typové testovací operátory](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) [specifikace jazyka C#](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Viz také

- [Referenční dokumentace k jazyku C#](../index.md)
- [Operátory jazyka C#](index.md)
- <xref:System.IEquatable%601?displayProperty=nameWithType>
- <xref:System.Object.Equals%2A?displayProperty=nameWithType>
- <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType>
- [Porovnání rovnosti](../../programming-guide/statements-expressions-operators/equality-comparisons.md)
- [Operátory porovnání](comparison-operators.md)
