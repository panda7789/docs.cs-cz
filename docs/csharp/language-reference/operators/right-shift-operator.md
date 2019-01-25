---
title: '&gt;&gt; Operator - C# odkaz'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '>>_CSharpKeyword'
helpviewer_keywords:
- '>> operator [C#]'
- right shift operator (>>) [C#]
ms.assetid: a07f8679-d318-4ef8-b38b-65903efb8056
ms.openlocfilehash: f7cacd740966f0716e125887568a39abf0d9e454
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54725425"
---
# <a name="gtgt-operator-c-reference"></a>&gt;&gt; – Operátor (referenční dokumentace jazyka C#)

Operátor posunutí doprava (`>>`) posune jeho prvního operandu vpravo o počet bitů určený svým druhým operandem.

## <a name="remarks"></a>Poznámky

Pokud je první operand [int](../keywords/int.md) nebo [uint](../keywords/uint.md) (množství 32-bit), počet posunů je dán pět bity nižšího řádu druhého operandu (Druhý operand & 0x1f).

Pokud je první operand [dlouhé](../keywords/long.md) nebo [ulong](../keywords/ulong.md) (množství 64-bit), počet posunů je dán šest bity nižšího řádu druhého operandu (Druhý operand & 0x3f).

Pokud je první operand [int](../keywords/int.md) nebo [dlouhé](../keywords/long.md), pravého posunutí je aritmetické posun (horní prázdnou bity jsou nastaveny na bit znaménka). Pokud je první operand je typu [uint](../keywords/uint.md) nebo [ulong](../keywords/ulong.md), pravého posunutí je logický posun (bity nejvyšším jsou vyplněny nulami).

Lze přetěžovat uživatelsky definované typy `>>` operátor; typ první operand musí být uživatelem definovaný typ, a musí být typu druhého operandu [int](../keywords/int.md). Další informace najdete v tématu [operátor](../keywords/operator.md). Při je binární operátor přetížen, odpovídající operátor přiřazení, pokud existuje, je také implicitně přetížená.

## <a name="example"></a>Příklad

[!code-csharp[csRefOperators#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#26)]

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka C#](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [C#operátory](index.md)