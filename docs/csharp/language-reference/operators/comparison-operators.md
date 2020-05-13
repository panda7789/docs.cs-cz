---
title: Operátory porovnání – reference jazyka C#
description: Přečtěte si o relačních operátorech C#, které můžete použít ke kontrole pořadí číselných hodnot.
ms.date: 05/11/2020
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
ms.openlocfilehash: eda039d950e4be13d9c041c8bb95b6ea773b83f6
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/12/2020
ms.locfileid: "83207231"
---
# <a name="comparison-operators-c-reference"></a>Operátory porovnání (Referenční dokumentace jazyka C#)

Porovnání [ `<` (menší než)](#less-than-operator-), [ `>` (je větší než)](#greater-than-operator-), (je menší než [ `<=` nebo rovno)](#less-than-or-equal-operator-)a [ `>=` (větší než nebo rovno](#greater-than-or-equal-operator-) ), známé také jako relační, operátory porovnávají své operandy. Tyto operátory jsou podporovány všemi [celočíselnými](../builtin-types/integral-numeric-types.md) typy a čísly [s plovoucí desetinnou](../builtin-types/floating-point-numeric-types.md) čárkou.

> [!NOTE]
> Pro `==` operátory, `<` , `>` , `<=` a `>=` , pokud některý z operandů není číslo ( <xref:System.Double.NaN?displayProperty=nameWithType> nebo <xref:System.Single.NaN?displayProperty=nameWithType> ), výsledek operace je `false` . To znamená, že `NaN` hodnota není větší než, menší nebo rovna žádné jiné `double` hodnotě (nebo `float` ), včetně `NaN` . Další informace a příklady naleznete v tématu <xref:System.Double.NaN?displayProperty=nameWithType> nebo v <xref:System.Single.NaN?displayProperty=nameWithType> referenčním článku.

Typ [znaku](../builtin-types/char.md) také podporuje operátory porovnání. V případě `char` operandů jsou porovnány odpovídající kódy znaků.

Výčtové typy také podporují operátory porovnání. Pro operandy stejného typu [výčtu](../builtin-types/enum.md) jsou porovnány odpovídající hodnoty základního integrálního typu.

[ `==` `!=` Operátory a](equality-operators.md) zkontrolují, zda jsou jejich operandy stejné.

## <a name="less-than-operator-"></a>Operátor menší než\<

`<`Operátor vrátí, `true` Pokud je jeho levý operand menší než jeho pravý operand, `false` jinak:

[!code-csharp-interactive[less than example](snippets/ComparisonOperators.cs#Less)]

## <a name="greater-than-operator-"></a>> operátoru větší než

`>`Operátor vrátí, `true` Pokud je jeho levý operand větší než jeho pravý operand, `false` jinak:

[!code-csharp-interactive[greater than example](snippets/ComparisonOperators.cs#Greater)]

## <a name="less-than-or-equal-operator-"></a>Operátor menší než nebo rovno\<=

`<=`Operátor vrátí `true` , pokud je jeho levý operand menší nebo roven jeho pravému operandu, `false` jinak:

[!code-csharp-interactive[less than or equal example](snippets/ComparisonOperators.cs#LessOrEqual)]

## <a name="greater-than-or-equal-operator-"></a>Operátor větší než nebo rovno >=

`>=`Operátor vrátí `true` , pokud je jeho levý operand větší než nebo roven jeho pravému operandu, `false` jinak:

[!code-csharp-interactive[greater than or equal example](snippets/ComparisonOperators.cs#GreaterOrEqual)]

## <a name="operator-overloadability"></a>Přetížení operátoru

Uživatelsky definovaný typ může [přetížit](operator-overloading.md) `<` `>` operátory,, a `<=` `>=` .

Pokud typ přetěžuje jeden z `<` `>` operátorů nebo, musí přetížit jak `<` a `>` . Pokud typ přetěžuje jeden z `<=` `>=` operátorů nebo, musí přetížit jak `<=` a `>=` .

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace naleznete v části [relační operátory and type-Testing](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) v tématu [specifikace jazyka C#](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Viz také

- [Referenční dokumentace k jazyku C#](../index.md)
- [Operátory jazyka C#](index.md)
- <xref:System.IComparable%601?displayProperty=nameWithType>
- [Operátory rovnosti](equality-operators.md)
