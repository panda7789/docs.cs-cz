---
title: Operátory porovnání – C# referenční informace
description: Přečtěte C# si o relačních operátorech, které můžete použít ke kontrole pořadí číselných hodnot.
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
ms.openlocfilehash: bb28e2adba896ae85b189858283376fbe3250dce
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/29/2019
ms.locfileid: "73039069"
---
# <a name="comparison-operators-c-reference"></a>Operátory porovnání (C# referenční)

[`<` (menší než)](#less-than-operator-), [`>` (je větší než)](#greater-than-operator-), [`<=` (menší nebo rovno)](#less-than-or-equal-operator-)a [`>=` (větší než nebo rovno](#greater-than-or-equal-operator-) ), které se označují také jako relační, operátory porovnávají jejich operandy. Tyto operátory jsou podporovány všemi [celočíselnými](../builtin-types/integral-numeric-types.md) typy a čísly [s plovoucí desetinnou](../builtin-types/floating-point-numeric-types.md) čárkou.

> [!NOTE]
> Pro operátory `==`, `<`, `>`, `<=`a `>=`, pokud některý z operandů není číslo (<xref:System.Double.NaN?displayProperty=nameWithType> nebo <xref:System.Single.NaN?displayProperty=nameWithType>), je výsledek operace `false`. To znamená, že hodnota `NaN` není větší než, menší nebo rovna žádné jiné hodnotě `double` (nebo `float`), včetně `NaN`. Další informace a příklady najdete v článku referenční článek o <xref:System.Double.NaN?displayProperty=nameWithType> nebo <xref:System.Single.NaN?displayProperty=nameWithType>.

Výčtové typy také podporují operátory porovnání. Pro operandy stejného typu [výčtu](../keywords/enum.md) jsou porovnány odpovídající hodnoty základního integrálního typu.

[Operátory`==` a `!=`](equality-operators.md) kontrolují, jestli jsou jejich operandy stejné.

## <a name="less-than-operator-"></a>Operátor menší než \<

Operátor `<` vrátí `true`, pokud je jeho levý operand menší než jeho pravý operand, `false` jinak:

[!code-csharp-interactive[less than example](~/samples/csharp/language-reference/operators/ComparisonOperators.cs#Less)]

## <a name="greater-than-operator-"></a>> Operátoru větší než

Operátor `>` vrátí `true`, pokud je jeho levý operand větší než jeho pravý operand, `false` jinak:

[!code-csharp-interactive[greater than example](~/samples/csharp/language-reference/operators/ComparisonOperators.cs#Greater)]

## <a name="less-than-or-equal-operator-"></a>\<= operátoru menší než nebo rovno

Operátor `<=` vrátí `true`, pokud je jeho levý operand menší nebo roven jeho pravému operandu, `false` jinak:

[!code-csharp-interactive[less than or equal example](~/samples/csharp/language-reference/operators/ComparisonOperators.cs#LessOrEqual)]

## <a name="greater-than-or-equal-operator-"></a>Operátor větší než nebo rovno > =

Operátor `>=` vrátí `true`, pokud je jeho levý operand větší nebo roven jeho pravému operandu, `false` jinak:

[!code-csharp-interactive[greater than or equal example](~/samples/csharp/language-reference/operators/ComparisonOperators.cs#GreaterOrEqual)]

## <a name="operator-overloadability"></a>Přetížení operátoru

Uživatelsky definovaný typ může [přetížit](operator-overloading.md) operátory `<`, `>`, `<=`a `>=`.

Pokud typ přetěžuje jednu z `<` nebo `>` operátory, musí přetížit jak `<`, tak `>`. Pokud typ přetěžuje jednu z `<=` nebo `>=` operátory, musí přetížit jak `<=`, tak `>=`.

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace naleznete v části [relační operátory and type-Testing](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) v [ C# tématu Specifikace jazyka](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Viz také:

- [C#odkaz](../index.md)
- [Operátory jazyka C#](index.md)
- <xref:System.IComparable%601?displayProperty=nameWithType>
- [Operátory rovnosti](equality-operators.md)
