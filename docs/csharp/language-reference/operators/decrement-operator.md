---
title: -- – operátor (Referenční dokumentace jazyka C#)
ms.date: 11/26/2018
f1_keywords:
- --_CSharpKeyword
helpviewer_keywords:
- -- operator [C#]
- decrement operator (--) [C#]
ms.assetid: 6b9cfe86-63c7-421f-9379-c9690fea8720
ms.openlocfilehash: 0858321d6fe192a55bc548f169c558542238a981
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53153331"
---
# <a name="---operator-c-reference"></a>-- – operátor (Referenční dokumentace jazyka C#)

Unární operátor dekrementace `--` sníží svého operandu o 1. Je podporován ve dvou formách: příponového operátoru dekrementace `x--`a operátor dekrementace předpony `--x`.

## <a name="postfix-decrement-operator"></a>Příponový operátor dekrementace

Výsledek `x--` je hodnota `x` *před* operace, jako v následujícím příkladu:

[!code-csharp-interactive[postfix decrement](~/samples/snippets/csharp/language-reference/operators/DecrementAndIncrementExamples.cs#PostfixDecrement)]

## <a name="prefix-decrement-operator"></a>Operátor dekrementace předpony

Výsledek `--x` je hodnota `x` *po* operace, jako v následujícím příkladu:

[!code-csharp-interactive[prefix decrement](~/samples/snippets/csharp/language-reference/operators/DecrementAndIncrementExamples.cs#PrefixDecrement)]

## <a name="remarks"></a>Poznámky

Operátor dekrementace je předdefinovaný pro všechny [celočíselných typů](../keywords/integral-types-table.md) (včetně [char](../keywords/char.md) typu), [typy s plovoucí desetinnou čárkou](../keywords/floating-point-types-table.md)a jakékoli [výčtu](../keywords/enum.md) Zadejte.

Operand operátoru dekrementace musí být proměnná, [vlastnost](../../programming-guide/classes-and-structs/properties.md) přístup, nebo [indexer](../../../csharp/programming-guide/indexers/index.md) přístup.

## <a name="operator-overloadability"></a>Overloadability – operátor

Uživatelem definované typy lze [přetížení](../keywords/operator.md) `--` operátor.

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace najdete v tématu [Příponové operátory Inkrementace a dekrementace operátory](~/_csharplang/spec/expressions.md#postfix-increment-and-decrement-operators) a [předpony Inkrementace a dekrementace operátory](~/_csharplang/spec/expressions.md#prefix-increment-and-decrement-operators) oddíly [ C# specifikace jazyka](../language-specification/index.md).

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka C#](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [Operátory jazyka C#](index.md)
- [++ – operátor](increment-operator.md)
- [Postupy: přírůstek a úbytek ukazatelů](../../programming-guide/unsafe-code-pointers/how-to-increment-and-decrement-pointers.md)
