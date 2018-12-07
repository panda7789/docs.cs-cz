---
title: ++ – operátor (Referenční dokumentace jazyka C#)
ms.date: 11/26/2018
f1_keywords:
- ++_CSharpKeyword
helpviewer_keywords:
- increment operator (++) [C#]
- ++ operator [C#]
ms.assetid: e9dec353-070b-44fb-98ed-eb8fdf753feb
ms.openlocfilehash: b29f4f1ab00c0f8026f118cb72b090e3b728bfc5
ms.sourcegitcommit: 6ae7cdd0437a32884556dd4826ca90e957b7a4e3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/06/2018
ms.locfileid: "48030467"
---
# <a name="-operator-c-reference"></a>++ – operátor (Referenční dokumentace jazyka C#)

Unární operátor Inkrementace `++` svého operandu zvýší o hodnotu 1. Je podporován ve dvou formách: příponového operátoru Inkrementace `x++`a prefixový operátor Inkrementace `++x`.

## <a name="postfix-increment-operator"></a>Příponový operátor inkrementace

Výsledek `x++` je hodnota `x` *před* operace, jako v následujícím příkladu:

[!code-csharp-interactive[postfix increment](~/samples/snippets/csharp/language-reference/operators/DecrementAndIncrementExamples.cs#PostfixIncrement)]

## <a name="prefix-increment-operator"></a>Prefixový operátor Inkrementace

Výsledek `++x` je hodnota `x` *po* operace, jako v následujícím příkladu:

[!code-csharp-interactive[prefix increment](~/samples/snippets/csharp/language-reference/operators/DecrementAndIncrementExamples.cs#PrefixIncrement)]

## <a name="remarks"></a>Poznámky

Operátor Inkrementace je předdefinovaný pro všechny [celočíselných typů](../keywords/integral-types-table.md) (včetně [char](../keywords/char.md) typu), [typy s plovoucí desetinnou čárkou](../keywords/floating-point-types-table.md)a jakékoli [výčtu](../keywords/enum.md) Zadejte.

Operand operátoru Inkrementace musí být proměnná, [vlastnost](../../programming-guide/classes-and-structs/properties.md) přístup, nebo [indexer](../../../csharp/programming-guide/indexers/index.md) přístup.

## <a name="operator-overloadability"></a>Overloadability – operátor

Uživatelem definované typy lze [přetížení](../keywords/operator.md) `++` operátor.

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace najdete v tématu [Příponové operátory Inkrementace a dekrementace operátory](~/_csharplang/spec/expressions.md#postfix-increment-and-decrement-operators) a [předpony Inkrementace a dekrementace operátory](~/_csharplang/spec/expressions.md#prefix-increment-and-decrement-operators) oddíly [ C# specifikace jazyka](../language-specification/index.md).

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka C#](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [Operátory jazyka C#](index.md)
- [-- – operátor](decrement-operator.md)
- [Postupy: přírůstek a úbytek ukazatelů](../../programming-guide/unsafe-code-pointers/how-to-increment-and-decrement-pointers.md)
