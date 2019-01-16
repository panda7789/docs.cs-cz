---
title: '&lt;&lt; Operator - C# odkaz'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- <<_CSharpKeyword
helpviewer_keywords:
- left shift operator (<<) [C#]
- << operator [C#]
ms.assetid: a654eb56-1ff7-4bf3-9064-b631be0cdccc
ms.openlocfilehash: 79a48d88e2c83b5ad78804367ee3c07f78622c08
ms.sourcegitcommit: 5c36aaa8299a2437c155700c810585aff19edbec
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/16/2019
ms.locfileid: "54333522"
---
# <a name="ltlt-operator-c-reference"></a>&lt;&lt; – Operátor (referenční dokumentace jazyka C#)

Operátor posunutí doleva (`<<`) staffhubu jeho prvního operandu vlevo o počet bitů určený svým druhým operandem. Musí být typu druhého operandu [int](../keywords/int.md) nebo typ, který má předdefinované implicitní převod čísla na `int`.

## <a name="remarks"></a>Poznámky

Pokud je první operand [int](../keywords/int.md) nebo [uint](../keywords/uint.md) (množství 32-bit), počet posunů je dán pět bity nižšího řádu druhého operandu. To znamená, že počet skutečné posunutí je 0 až 31 bitů.

Pokud je první operand [dlouhé](../keywords/long.md) nebo [ulong](../keywords/ulong.md) (množství 64-bit), počet posunů je dán šest bity nižšího řádu druhého operandu. To znamená že počet skutečné posunutí je 0 až 63 bitů.

Všechny nejvyšším bity, které jsou v rozsahu typu prvního operandu po přesun se zahodí a prázdný bity nižšího řádu jsou vyplněny nulami. Operace posunutí nikdy nezpůsobí přetečení.

Lze přetěžovat uživatelsky definované typy `<<` – operátor (naleznete v tématu [operátor](../keywords/operator.md)); typ první operand musí být uživatelem definovaný typ, a musí být typu druhého operandu `int`. Při je binární operátor přetížen, odpovídající operátor přiřazení, pokud existuje, je také implicitně přetížená.

## <a name="example"></a>Příklad

[!code-csharp[csRefOperators#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#14)]

## <a name="comments"></a>Komentáře

Všimněte si, že `i<<1` a `i<<33` poskytují stejný výsledek, protože 1 a 33 mají stejné pět bity nižšího řádu.

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka C#](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [Operátory jazyka C#](index.md)
