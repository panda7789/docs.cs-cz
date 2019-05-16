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
ms.openlocfilehash: 6d3751ff1ee2c6ee2f058eeda4ffd5db188a988e
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2019
ms.locfileid: "65633764"
---
# <a name="comparison-operators-c-reference"></a>Operátory porovnání (C# odkaz)

[ `<` (Menší než)](#less-than-operator-), [ `>` (větší)](#greater-than-operator-), [ `<=` (menší než nebo rovno)](#less-than-or-equal-operator-), a [ `>=` () větší než nebo rovno)](#greater-than-or-equal-operator-) porovnání, také známé jako relační, operátory porovnání svých operandů. Tyto operátory podporují všechny [integrální](../keywords/integral-types-table.md) a [s plovoucí desetinnou čárkou](../keywords/floating-point-types-table.md) číselné typy.

> [!NOTE]
> Pro `==`, `<`, `>`, `<=`, a `>=` operátory, pokud žádný z operandů není číslo (<xref:System.Double.NaN?displayProperty=nameWithType> nebo <xref:System.Single.NaN?displayProperty=nameWithType>), je výsledek operace `false`. To znamená, že `NaN` hodnota není větší než, menší než, ani jakýkoli jiný roven `double` (nebo `float`) hodnotu, včetně `NaN`. Další informace a příklady najdete v tématu <xref:System.Double.NaN?displayProperty=nameWithType> nebo <xref:System.Single.NaN?displayProperty=nameWithType> článku.

Výčtové typy také podporují operátory porovnání. Pro operandy stejného [výčtu](../keywords/enum.md) porovnání typu hodnoty odpovídající základní celočíselného typu.

[ `==` a `!=` operátory](equality-operators.md) zkontrolujte, jestli operandy jsou stejné, nebo ne.

## <a name="less-than-operator-"></a>Operátor menší než \<

`<` Operátor vrátí `true` Pokud svůj první operand je menší než svým druhým operandem, `false` jinak:

[!code-csharp-interactive[less than example](~/samples/snippets/csharp/language-reference/operators/GreaterAndLessOperatorsExamples.cs#Less)]

## <a name="greater-than-operator-"></a>Operátor větší než >

`>` Operátor vrátí `true` Pokud svůj první operand je větší než jeho druhým operandem, `false` jinak:

[!code-csharp-interactive[greater than example](~/samples/snippets/csharp/language-reference/operators/GreaterAndLessOperatorsExamples.cs#Greater)]

## <a name="less-than-or-equal-operator-"></a>Menší než nebo rovno – operátor \<=

`<=` Operátor vrátí `true` Pokud svůj první operand je menší nebo rovna svým druhým operandem, `false` jinak:

[!code-csharp-interactive[less than or equal example](~/samples/snippets/csharp/language-reference/operators/GreaterAndLessOperatorsExamples.cs#LessOrEqual)]

## <a name="greater-than-or-equal-operator-"></a>Operátor větší než nebo rovna > =

`>=` Operátor vrátí `true` Pokud svůj první operand je větší než nebo rovna hodnotě svým druhým operandem, `false` jinak:

[!code-csharp-interactive[greater than or equal example](~/samples/snippets/csharp/language-reference/operators/GreaterAndLessOperatorsExamples.cs#GreaterOrEqual)]

## <a name="operator-overloadability"></a>Overloadability – operátor

Uživatelem definovaný typ může [přetížení](../keywords/operator.md) `<`, `>`, `<=`, a `>=` operátory.

Pokud typ jednoho z přetížení `<` nebo `>` operátory, ho musíte přetížení obě `<` a `>`. Pokud typ jednoho z přetížení `<=` nebo `>=` operátory, ho musíte přetížení obě `<=` a `>=`.

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace najdete v tématu [relační a typové zkoušky operátory](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) část [ C# specifikace jazyka](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka C#](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [Operátory jazyka C#](index.md)
- <xref:System.IComparable%601?displayProperty=nameWithType>
- [Operátory rovnosti](equality-operators.md)
