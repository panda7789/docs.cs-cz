---
title: Operátory rovnosti C# – reference
description: Přečtěte C# si o operátorech C# porovnání rovnosti a typu rovnosti.
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
ms.openlocfilehash: 4a30068293bef3adb9f58cc7f61e7e24e144f31b
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72395137"
---
# <a name="equality-operators-c-reference"></a>Operátory rovnostiC# (Referenční dokumentace)

Operátory [`==` (rovnost)](#equality-operator-) a [`!=` (nerovnost)](#inequality-operator-) kontrolují, jestli jsou jejich operandy stejné nebo ne.

## <a name="equality-operator-"></a>Operátor rovnosti = =

Operátor rovnosti `==` vrátí `true`, pokud se jeho operandy rovnají, `false` v opačném případě.

### <a name="value-types-equality"></a>Rovnost typů hodnot

Operandy [předdefinovaných hodnotových typů](../keywords/value-types-table.md) jsou stejné, pokud se jejich hodnoty rovnají:

[!code-csharp-interactive[value types equality](~/samples/csharp/language-reference/operators/EqualityOperators.cs#ValueTypesEquality)]

> [!NOTE]
> U operátorů `==`, [`<`, `>`, `<=` a `>=`](comparison-operators.md) nejsou v případě žádného operandu číslo (<xref:System.Double.NaN?displayProperty=nameWithType> nebo <xref:System.Single.NaN?displayProperty=nameWithType>), výsledkem operace je @no__t 8. To znamená, že hodnota `NaN` není větší než, menší nebo rovna žádné jiné hodnotě `double` (nebo `float`), včetně `NaN`. Další informace a příklady najdete v článku referenční článek o <xref:System.Double.NaN?displayProperty=nameWithType> nebo <xref:System.Single.NaN?displayProperty=nameWithType>.

Dva operandy stejného typu [výčtu](../keywords/enum.md) jsou stejné, pokud jsou odpovídající hodnoty základního integrálního typu stejné.

Uživatelsky definované typy [struktur](../keywords/struct.md) nepodporují ve výchozím nastavení operátor `==`. Aby bylo možné podporovat operátor `==`, musí být tato uživatelsky definovanou strukturou [přetížena](#operator-overloadability) .

Počínaje C# 7,3 jsou operátory `==` a `!=` podporovány C# [řazenými kolekcemi členů](../../tuples.md). Další informace naleznete v části [rovnost a řazené kolekce členů](../../tuples.md#equality-and-tuples) v článku [ C# typy řazené kolekce členů](../../tuples.md) .

### <a name="reference-types-equality"></a>Rovnost typů odkazů

Ve výchozím nastavení jsou dva operandy typu odkazu stejné, pokud odkazují na stejný objekt:

[!code-csharp[reference type equality](~/samples/csharp/language-reference/operators/EqualityOperators.cs#ReferenceTypesEquality)]

Jak ukazuje příklad, uživatelsky definované typy odkazů podporují ve výchozím nastavení operátor `==`. Typ odkazu však může přetížit operátor `==`. Pokud typ odkazu přetěžuje operátor `==`, použijte metodu <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> a ověřte, zda dva odkazy tohoto typu odkazují na stejný objekt.

### <a name="string-equality"></a>Rovnost řetězců

Dva [řetězcové](../keywords/string.md) operandy jsou stejné, pokud jsou oba `null` nebo jsou obě instance řetězce stejné délky a mají stejné znaky v každé pozici znaku:

[!code-csharp-interactive[string equality](~/samples/csharp/language-reference/operators/EqualityOperators.cs#StringEquality)]

To je ordinální porovnání rozlišující malá a velká písmena. Další informace o porovnání řetězců naleznete v tématu [jak porovnat řetězce v C# ](../../how-to/compare-strings.md).

### <a name="delegate-equality"></a>Rovnost delegáta

Dva operandy [delegáta](../../programming-guide/delegates/index.md) stejného typu modulu runtime jsou stejné, pokud jsou oba `null` nebo jsou jejich seznamy volání stejné délky a mají stejné položky na každé pozici:

[!code-csharp-interactive[delegate equality](~/samples/csharp/language-reference/operators/EqualityOperators.cs#DelegateEquality)]

Další informace naleznete v části [operátory rovnosti delegátů](~/_csharplang/spec/expressions.md#delegate-equality-operators) ve [ C# specifikaci jazyka](~/_csharplang/spec/introduction.md).

Delegáty vytvořené z vyhodnocení sémanticky identických [výrazů lambda](../../programming-guide/statements-expressions-operators/lambda-expressions.md) nejsou stejné, jak ukazuje následující příklad:

[!code-csharp-interactive[from identical lambdas](~/samples/csharp/language-reference/operators/EqualityOperators.cs#IdenticalLambdas)]

## <a name="inequality-operator-"></a>Operátor nerovnosti! =

Operátor nerovnosti `!=` vrátí `true`, pokud jeho operandy nejsou stejné, `false` v opačném případě. U operandů [předdefinovaných typů](../keywords/built-in-types-table.md)výraz `x != y` vytvoří stejný výsledek jako výraz `!(x == y)`. Další informace o rovnosti typů naleznete v části [operátor rovnosti](#equality-operator-) .

Následující příklad ukazuje použití operátoru `!=`:

[!code-csharp-interactive[non-equality examples](~/samples/csharp/language-reference/operators/EqualityOperators.cs#NonEquality)]

## <a name="operator-overloadability"></a>Přetížení operátoru

Uživatelsky definovaný typ může [přetížit](operator-overloading.md) operátory `==` a `!=`. Pokud typ přetěžuje jednu ze dvou operátorů, musí také přetížit další.

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace naleznete v části [relační operátory and type-Testing](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) v [ C# tématu Specifikace jazyka](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Viz také:

- [C#odkaz](../index.md)
- [Operátory jazyka C#](index.md)
- <xref:System.IEquatable%601?displayProperty=nameWithType>
- <xref:System.Object.Equals%2A?displayProperty=nameWithType>
- <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType>
- [Porovnání rovnosti](../../programming-guide/statements-expressions-operators/equality-comparisons.md)
- [Operátory porovnání](comparison-operators.md)
