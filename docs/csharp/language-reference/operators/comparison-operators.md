---
title: Operátory porovnání – odkaz jazyka C#
description: Další informace o operátory porovnání Jazyka C#, které můžete použít ke kontrole pořadí číselných hodnot.
ms.date: 04/25/2019
author: pkulikov
f1_keywords:
- <_CSharpKeyword
- '>_CSharpKeyword'
- <=_CSharpKeyword
- '>=_CSharpKeyword'
helpviewer_keywords:
- comparison operators [C#]
- relational operators [C#]
- less than operator [C#]
- < operator [C#]
- greater than operator [C#]
- '> operator [C#]'
- less than or equal to operator [C#]
- <= operator [C#]
- greater than or equal to operator [C#]
- '>= operator [C#]'
ms.openlocfilehash: 68502205193a1fc8ab7410053e13274560ffffb0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399243"
---
# <a name="comparison-operators-c-reference"></a>Operátory porovnání (odkaz C#

[ `<` Porovnání (menší než)](#less-than-operator-), [ `>` (větší než)](#greater-than-operator-) [ `<=` , (menší než nebo stejné)](#less-than-or-equal-operator-)a [ `>=` (větší než nebo stejné)](#greater-than-or-equal-operator-) porovnání, označované také jako relační, operátory porovnávají jejich operandy. Tyto operátory jsou podporovány všechny [integrální](../builtin-types/integral-numeric-types.md) a [plovoucí desetinnou desetinnou desetinnou desetinnou](../builtin-types/floating-point-numeric-types.md) desetinnou hodnotu číselné typy.

> [!NOTE]
> Pro `==`, `<` `>`, `<=`, `>=` , , a operátory, pokud některý<xref:System.Double.NaN?displayProperty=nameWithType> <xref:System.Single.NaN?displayProperty=nameWithType>z operandů `false`není číslo ( nebo ), výsledek operace je . To znamená, `NaN` že hodnota není větší než, menší než, `float`ani rovna `NaN`žádné jiné `double` (nebo ) hodnotu, včetně . Další informace a příklady <xref:System.Double.NaN?displayProperty=nameWithType> naleznete <xref:System.Single.NaN?displayProperty=nameWithType> v článku nebo odkazu.

Typy výčtu také podporují operátory porovnání. Pro operandy stejného typu [výčtu](../builtin-types/enum.md) jsou porovnány odpovídající hodnoty základního integrálního typu.

[ `==` A `!=` operátoři](equality-operators.md) kontrolují, zda jsou jejich operandy stejné nebo ne.

## <a name="less-than-operator-"></a>Menší než operátor\<

Operátor `<` se `true` vrátí, je-li jeho levostranný operand `false` menší než jeho pravostranný operand, jinak:

[!code-csharp-interactive[less than example](snippets/ComparisonOperators.cs#Less)]

## <a name="greater-than-operator-"></a>Větší než > operátora

Operátor `>` se `true` vrátí, je-li jeho levostranný operand `false` větší než jeho pravostranný operand, jinak:

[!code-csharp-interactive[greater than example](snippets/ComparisonOperators.cs#Greater)]

## <a name="less-than-or-equal-operator-"></a>Operátor menší nebo stejný\<=

Operátor `<=` vrátí, `true` pokud jeho levostranný operand je menší nebo `false` roven jeho pravé operandu, jinak:

[!code-csharp-interactive[less than or equal example](snippets/ComparisonOperators.cs#LessOrEqual)]

## <a name="greater-than-or-equal-operator-"></a>Větší než nebo rovno operátor >=

Operátor `>=` vrátí, `true` pokud jeho levé operandu větší nebo rovno jeho `false` pravé operand, jinak:

[!code-csharp-interactive[greater than or equal example](snippets/ComparisonOperators.cs#GreaterOrEqual)]

## <a name="operator-overloadability"></a>Přetížení obsluhy

Uživatelem definovaný typ může `<` `>` `<=` [přetížit](operator-overloading.md) , , , a `>=` operátory.

Pokud typ přetíží `<` jeden `>` z operátorů `<` nebo, musí přetížit oba a `>`. Pokud typ přetíží `<=` jeden `>=` z operátorů `<=` nebo, musí přetížit oba a `>=`.

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace naleznete v části [Relační a typové testovací operátory](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) [specifikace jazyka C#](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Viz také

- [Referenční dokumentace k jazyku C#](../index.md)
- [Operátory jazyka C#](index.md)
- <xref:System.IComparable%601?displayProperty=nameWithType>
- [Operátory rovnosti](equality-operators.md)
