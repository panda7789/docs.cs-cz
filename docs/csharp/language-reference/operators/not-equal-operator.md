---
title: '! = – Operátor - C# odkaz'
ms.custom: seodec18
ms.date: 12/14/2018
f1_keywords:
- '!=_CSharpKeyword'
helpviewer_keywords:
- inequality operator (!=) [C#]
- not equals operator (!=) [C#]
- '!= operator [C#]'
ms.assetid: eeff7a4e-ad6f-462d-9f8d-49e9b91c6c97
ms.openlocfilehash: 939b5664dba4345e62a43fb2f8d4d5379659d6aa
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/19/2018
ms.locfileid: "53610174"
---
# <a name="-operator-c-reference"></a>!= – operátor (Referenční dokumentace jazyka C#)

Operátor nerovnosti `!=` vrátí `true` Pokud nejsou stejné, jeho operandy `false` jinak. Pro operandy [předdefinovaných typů](../keywords/built-in-types-table.md), výraz `x != y` vytváří stejný výsledek jako výraz `!(x == y)`. Další informace najdete v tématu [== – operátor](equality-comparison-operator.md) článku.

Následující příklad ukazuje použití `!=` operátor:

[!code-csharp-interactive[non-equality examples](~/samples/snippets/csharp/language-reference/operators/EqualityAndNonEqualityExamples.cs#NonEquality)]

## <a name="operator-overloadability"></a>Overloadability – operátor

Uživatelem definované typy lze [přetížení](../keywords/operator.md) `!=` operátor. Pokud typ přetížení operátor nerovnosti `!=`, musíte také přetížit [operátor rovnosti](equality-comparison-operator.md) `==`.

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace najdete v tématu [relační a typové zkoušky operátory](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) část [ C# specifikace jazyka](../language-specification/index.md).

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka C#](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [Operátory jazyka C#](index.md)
- [Porovnání rovnosti](../../programming-guide/statements-expressions-operators/equality-comparisons.md)
