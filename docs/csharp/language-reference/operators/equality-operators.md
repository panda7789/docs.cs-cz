---
title: Operátory rovnosti – reference jazyka C#
description: Přečtěte si o operátorech porovnání rovnosti jazyka C# a rovnosti typů jazyka C#.
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
ms.openlocfilehash: 1b87f7f6c1b22550e3df554572225b3fce6a1b56
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/04/2020
ms.locfileid: "87556615"
---
# <a name="equality-operators-c-reference"></a>Operátory rovnosti (Referenční dokumentace jazyka C#)

Operátory [ `==` (rovnost)](#equality-operator-) a [ `!=` (nerovnost)](#inequality-operator-) kontrolují, zda jsou jejich operandy stejné.

## <a name="equality-operator-"></a>Operátor rovnosti = =

Operátor rovnosti `==` `true` se vrátí, pokud jsou jeho operandy stejné, `false` jinak.

### <a name="value-types-equality"></a>Rovnost typů hodnot

Operandy [předdefinovaných hodnotových typů](../builtin-types/value-types.md#built-in-value-types) jsou stejné, pokud se jejich hodnoty rovnají:

[!code-csharp-interactive[value types equality](snippets/EqualityOperators.cs#ValueTypesEquality)]

> [!NOTE]
> Pro `==` operátory, [ `<` , `>` , `<=` a `>=` ](comparison-operators.md) , pokud některý z operandů není číslo ( <xref:System.Double.NaN?displayProperty=nameWithType> nebo <xref:System.Single.NaN?displayProperty=nameWithType> ), výsledek operace je `false` . To znamená, že `NaN` hodnota není větší než, menší nebo rovna žádné jiné `double` hodnotě (nebo `float` ), včetně `NaN` . Další informace a příklady naleznete v tématu <xref:System.Double.NaN?displayProperty=nameWithType> nebo v <xref:System.Single.NaN?displayProperty=nameWithType> referenčním článku.

Dva operandy stejného typu [výčtu](../builtin-types/enum.md) jsou stejné, pokud jsou odpovídající hodnoty základního integrálního typu stejné.

Uživatelsky definované typy [struktur](../builtin-types/struct.md) nepodporují `==` ve výchozím nastavení operátor. Pro podporu `==` operátoru musí být uživatelsky definovaná struktura [přetížena](operator-overloading.md) .

Počínaje jazykem C# 7,3 `==` `!=` jsou operátory a podporovány v [řazených kolekcích členů](../builtin-types/value-tuples.md)jazyka c#. Další informace naleznete v části [rovnost řazené kolekce členů](../builtin-types/value-tuples.md#tuple-equality) v článku [typy řazené kolekce členů](../builtin-types/value-tuples.md) .

### <a name="reference-types-equality"></a>Rovnost typů odkazů

Ve výchozím nastavení jsou dva operandy typu odkazu stejné, pokud odkazují na stejný objekt:

[!code-csharp[reference type equality](snippets/EqualityOperators.cs#ReferenceTypesEquality)]

Jak ukazuje příklad, uživatelsky definované typy odkazů podporují `==` operátor ve výchozím nastavení. Typ odkazu však může přetížit `==` operátor. Pokud typ odkazu přetěžuje `==` operátor, použijte <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> metodu ke kontrole, zda dva odkazy tohoto typu odkazují na stejný objekt.

### <a name="string-equality"></a>Rovnost řetězců

Dva [řetězcové](../builtin-types/reference-types.md#the-string-type) operandy jsou stejné, pokud jsou oba, `null` nebo obě řetězcové instance mají stejnou délku a mají stejné znaky v každé pozici znaku:

[!code-csharp-interactive[string equality](snippets/EqualityOperators.cs#StringEquality)]

To je ordinální porovnání rozlišující malá a velká písmena. Další informace o porovnání řetězců naleznete v tématu [jak porovnat řetězce v jazyce C#](../../how-to/compare-strings.md).

### <a name="delegate-equality"></a>Rovnost delegáta

Dva operandy [delegáta](../../programming-guide/delegates/index.md) stejného typu modulu runtime jsou stejné, pokud jsou oba `null` seznamy volání stejné délky a mají stejné položky na každé pozici:

[!code-csharp-interactive[delegate equality](snippets/EqualityOperators.cs#DelegateEquality)]

Další informace naleznete v části [operátory rovnosti delegátů](~/_csharplang/spec/expressions.md#delegate-equality-operators) [specifikace jazyka C#](~/_csharplang/spec/introduction.md).

Delegáty vytvořené z vyhodnocení sémanticky identických [výrazů lambda](../../programming-guide/statements-expressions-operators/lambda-expressions.md) nejsou stejné, jak ukazuje následující příklad:

[!code-csharp-interactive[from identical lambdas](snippets/EqualityOperators.cs#IdenticalLambdas)]

## <a name="inequality-operator-"></a>Operátor nerovnosti! =

Operátor nerovnosti `!=` vrátí `true` , pokud jeho operandy nejsou stejné, `false` jinak. U operandů [předdefinovaných typů](../builtin-types/built-in-types.md)výraz `x != y` vytvoří stejný výsledek jako výraz `!(x == y)` . Další informace o rovnosti typů naleznete v části [operátor rovnosti](#equality-operator-) .

Následující příklad ukazuje použití `!=` operátoru:

[!code-csharp-interactive[non-equality examples](snippets/EqualityOperators.cs#NonEquality)]

## <a name="operator-overloadability"></a>Přetížení operátoru

Uživatelsky definovaný typ může [přetížit](operator-overloading.md) `==` `!=` operátory a. Pokud typ přetěžuje jednu ze dvou operátorů, musí také přetížit druhý.

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace naleznete v části [relační operátory and type-Testing](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) v tématu [specifikace jazyka C#](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Viz také

- [Referenční dokumentace k jazyku C#](../index.md)
- [Operátory a výrazy v C#](index.md)
- <xref:System.IEquatable%601?displayProperty=nameWithType>
- <xref:System.Object.Equals%2A?displayProperty=nameWithType>
- <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType>
- [Porovnání rovnosti](../../programming-guide/statements-expressions-operators/equality-comparisons.md)
- [Operátory porovnávání](comparison-operators.md)
