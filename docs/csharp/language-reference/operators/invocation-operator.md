---
title: () – operátor - C# odkaz
ms.custom: seodec18
ms.date: 01/15/2019
f1_keywords:
- ()_CSharpKeyword
helpviewer_keywords:
- type conversion [C#], () operator
- cast operator [C#]
- () operator [C#]
ms.assetid: 846e1f94-8a8c-42fc-a42c-fbd38e70d8cc
ms.openlocfilehash: 412d3ac5296eaf7d67f4a5e84b7a42f6fa5bb8a5
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2019
ms.locfileid: "65633805"
---
# <a name="-operator-c-reference"></a>() – operátor (C# odkaz)

Závorky, `()`, se obvykle používají pro vyvolání delegáta nebo metody nebo výrazy přetypování.

Je také použít k určení pořadí, ve kterém se má vyhodnotit operací ve výrazu závorky. Další informace najdete v tématu [závorek](../../programming-guide/statements-expressions-operators/operators.md#adding-parentheses) část [operátory](../../programming-guide/statements-expressions-operators/operators.md) článku. Seznam operátorů seřazené podle úrovně priority, naleznete v tématu [ C# operátory](index.md).

## <a name="method-invocation"></a>Volání metody

Následující příklad ukazuje, jak vyvolat metodu, s nebo bez argumentů a delegáta:

[!code-csharp-interactive[use for invocation](~/samples/snippets/csharp/language-reference/operators/InvocationOperatorExamples.cs#Invocation)]

Můžete také použít závorky, při vyvolání [konstruktor](../../programming-guide/classes-and-structs/constructors.md) s [ `new` ](../keywords/new-operator.md) operátor.

Další informace o metodách, naleznete v tématu [metody](../../programming-guide/classes-and-structs/methods.md). Další informace o delegátech naleznete v tématu [delegáti](../../programming-guide/delegates/index.md).

## <a name="cast-expression"></a>Výraz CAST

Přetypování výrazu v podobě `(T)E` vyvolá operátor převodu se převést hodnotu výrazu `E` na typ `T`. Pokud neexistuje žádný explicitní převod z typu `E` na typ `T`, dojde k chybě kompilace. Informace o tom, jak definovat operátor převodu, najdete v článku [explicitní](../keywords/explicit.md) a [implicitní](../keywords/implicit.md) články – klíčové slovo.

Následující příklad ukazuje převodů mezi číselnými typy:

[!code-csharp-interactive[use for cast](~/samples/snippets/csharp/language-reference/operators/InvocationOperatorExamples.cs#Cast)]

Další informace o předdefinovaných explicitní převody mezi číselnými typy najdete v tématu [tabulka explicitních číselných převodů](../keywords/explicit-numeric-conversions-table.md).

Další informace najdete v tématu [přetypování a převody typu](../../programming-guide/types/casting-and-type-conversions.md) a [operátory převodu](../../programming-guide/statements-expressions-operators/conversion-operators.md).

## <a name="operator-overloadability"></a>Overloadability – operátor

Operátor `()` nemohou být přetíženy.

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace najdete v tématu [výrazy typu Invocation](~/_csharplang/spec/expressions.md#invocation-expressions) a [výrazy přetypování](~/_csharplang/spec/expressions.md#cast-expressions) oddíly [ C# specifikace jazyka](../language-specification/index.md).

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka C#](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [Operátory jazyka C#](index.md)
