---
title: Operátory porovnání - C# odkaz
description: Další informace o C# operátory porovnání, které vám umožní zkontrolovat pořadí číselné hodnoty.
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
ms.openlocfilehash: 7d8a6b7f5bf83719f96009c301867056da755822
ms.sourcegitcommit: 5bc85ad81d96b8dc2a90ce53bada475ee5662c44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/12/2019
ms.locfileid: "67025220"
---
# <a name="comparison-operators-c-reference"></a>Operátory porovnání (C# odkaz)

[ `<` (Menší než)](#less-than-operator-), [ `>` (větší)](#greater-than-operator-), [ `<=` (menší než nebo rovno)](#less-than-or-equal-operator-), a [ `>=` () větší než nebo rovno)](#greater-than-or-equal-operator-) porovnání, také známé jako relační, operátory porovnání svých operandů. Tyto operátory podporují všechny [integrální](../keywords/integral-types-table.md) a [s plovoucí desetinnou čárkou](../keywords/floating-point-types-table.md) číselné typy.

> [!NOTE]
> Pro `==`, `<`, `>`, `<=`, a `>=` operátory, pokud žádný z operandů není číslo (<xref:System.Double.NaN?displayProperty=nameWithType> nebo <xref:System.Single.NaN?displayProperty=nameWithType>), je výsledek operace `false`. To znamená, že `NaN` hodnota není větší než, menší než, ani jakýkoli jiný roven `double` (nebo `float`) hodnotu, včetně `NaN`. Další informace a příklady najdete v tématu <xref:System.Double.NaN?displayProperty=nameWithType> nebo <xref:System.Single.NaN?displayProperty=nameWithType> článku.

Výčtové typy také podporují operátory porovnání. Pro operandy stejného [výčtu](../keywords/enum.md) porovnání typu hodnoty odpovídající základní celočíselného typu.

[ `==` a `!=` operátory](equality-operators.md) zkontrolujte, jestli operandy jsou stejné, nebo ne.

## <a name="less-than-operator-"></a>Operátor menší než \<

`<` Operátor vrátí `true` Pokud svůj první operand je menší než svým druhým operandem, `false` jinak:

[!code-csharp-interactive[less than example](~/samples/csharp/language-reference/operators/ComparisonOperators.cs#Less)]

## <a name="greater-than-operator-"></a>Operátor větší než >

`>` Operátor vrátí `true` Pokud svůj první operand je větší než jeho druhým operandem, `false` jinak:

[!code-csharp-interactive[greater than example](~/samples/csharp/language-reference/operators/ComparisonOperators.cs#Greater)]

## <a name="less-than-or-equal-operator-"></a>Menší než nebo rovno – operátor \<=

`<=` Operátor vrátí `true` Pokud svůj první operand je menší nebo rovna svým druhým operandem, `false` jinak:

[!code-csharp-interactive[less than or equal example](~/samples/csharp/language-reference/operators/ComparisonOperators.cs#LessOrEqual)]

## <a name="greater-than-or-equal-operator-"></a>Operátor větší než nebo rovna > =

`>=` Operátor vrátí `true` Pokud svůj první operand je větší než nebo rovna hodnotě svým druhým operandem, `false` jinak:

[!code-csharp-interactive[greater than or equal example](~/samples/csharp/language-reference/operators/ComparisonOperators.cs#GreaterOrEqual)]

## <a name="operator-overloadability"></a>Overloadability – operátor

Uživatelem definovaný typ může [přetížení](../keywords/operator.md) `<`, `>`, `<=`, a `>=` operátory.

Pokud typ jednoho z přetížení `<` nebo `>` operátory, ho musíte přetížení obě `<` a `>`. Pokud typ jednoho z přetížení `<=` nebo `>=` operátory, ho musíte přetížení obě `<=` a `>=`.

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace najdete v tématu [relační a typové zkoušky operátory](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) část [ C# specifikace jazyka](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Viz také:

- [C#referenční dokumentace](../index.md)
- [Operátory jazyka C#](index.md)
- <xref:System.IComparable%601?displayProperty=nameWithType>
- [Operátory rovnosti](equality-operators.md)
