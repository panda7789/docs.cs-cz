---
title: '> Operator - C# odkaz'
ms.custom: seodec18
ms.date: 12/18/2018
f1_keywords:
- '>_CSharpKeyword'
helpviewer_keywords:
- '> operator [C#]'
- greater than operator (>) [C#]
ms.assetid: 26d3cb69-9c0b-4cc5-858b-5be1abd6659d
ms.openlocfilehash: 3b036c491d9663bf4ab0971d84a0a8d58d902ee6
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55287206"
---
# <a name="-operator-c-reference"></a>> – operátor (Referenční dokumentace jazyka C#)

Relační operátor "větší než" `>` vrátí `true` Pokud svůj první operand je větší než jeho druhým operandem, `false` jinak. Všechny typy číselné a výčet podporují `>` operátor. Pro operandy stejného [výčtu](../keywords/enum.md) porovnání typu hodnoty odpovídající základní celočíselného typu.

> [!NOTE]
> Pro relační operátory `==`, `>`, `<`, `>=`, a `<=`, pokud žádný z operandů není číslo (<xref:System.Double.NaN?displayProperty=nameWithType> nebo <xref:System.Single.NaN?displayProperty=nameWithType>) je výsledek operace `false`. To znamená, že `NaN` hodnota není větší než, menší než, ani jakýkoli jiný roven `double` (nebo `float`) hodnotu. Další informace a příklady najdete v tématu <xref:System.Double.NaN?displayProperty=nameWithType> nebo <xref:System.Single.NaN?displayProperty=nameWithType> článku.

Následující příklad ukazuje použití `>` operátor:

[!code-csharp-interactive[greater than example](~/samples/snippets/csharp/language-reference/operators/GreaterAndLessOperatorsExamples.cs#Greater)]

## <a name="operator-overloadability"></a>Overloadability – operátor

Uživatelem definované typy lze [přetížení](../keywords/operator.md) `>` operátor. Pokud typ přetížení operátoru "větší než" `>`, musíte také přetížit [operátor "menší než"](less-than-operator.md) `<`.

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace najdete v tématu [relační a typové zkoušky operátory](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) část [ C# specifikace jazyka](../language-specification/index.md).

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka C#](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [Operátory jazyka C#](index.md)
- [>= – operátor](greater-than-equal-operator.md)
- <xref:System.IComparable%601?displayProperty=nameWithType>
