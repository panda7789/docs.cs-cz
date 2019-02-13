---
title: '>> Operator - C# odkaz'
ms.custom: seodec18
ms.date: 02/12/2019
f1_keywords:
- '>>_CSharpKeyword'
helpviewer_keywords:
- '>> operator [C#]'
- right shift operator (>>) [C#]
ms.assetid: a07f8679-d318-4ef8-b38b-65903efb8056
ms.openlocfilehash: 809cd2cab29d3378892ea224cf846e9d0909b073
ms.sourcegitcommit: 30e2fe5cc4165aa6dde7218ec80a13def3255e98
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/13/2019
ms.locfileid: "56219721"
---
# <a name="-operator-c-reference"></a>>> – operátor (C# odkaz)

Operátor pravého posunutí `>>` posune jeho prvního operandu vpravo počet bitů, které jsou určené svým druhým operandem. Podporují všechny typy celých čísel `>>` operátor. Však musí být typu druhého operandu [int](../keywords/int.md) nebo typ, který má [předdefinované implicitní převod čísla](../keywords/implicit-numeric-conversions-table.md) k `int`.

Operace pravého posunutí zahodí bity nižšího řádu. Nejvyšším prázdný bitové pozice jsou nastaveny na základě typu prvního operandu následujícím způsobem:

- Pokud je první operand je typu [int](../keywords/int.md) nebo [dlouhé](../keywords/long.md), operátor pravého posunutí provádí **aritmetické** shift: hodnota nejvýznamnější bit (bit znaménka) prvního operand je postoupena do nejvyšším prázdný bitové pozice. To znamená, implikovaný prázdný bitové pozice nastavení na hodnotu nula, pokud je první operand je nastaven na nezáporné a nastavit na jednu, pokud je záporné.

- Pokud je první operand je typu [uint](../keywords/uint.md) nebo [ulong](../keywords/ulong.md), operátor pravého posunutí provádí **logické** shift: nejvyšším prázdný bitové pozice jsou vždy nastaveny na hodnotu nula.

Následující příklad ukazuje toto chování:

[!code-csharp-interactive[right shift example](~/samples/snippets/csharp/language-reference/operators/ShiftOperatorsExamples.cs#RightShift)]

## <a name="shift-count"></a>Počet posunutí

Pro výraz `x >> count`, počet skutečné posunutí závisí na typu `x` následujícím způsobem:

- Pokud typ `x` je [int](../keywords/int.md) nebo [uint](../keywords/uint.md), počet posunů je dán nižšího řádu *pět* bits druhého operandu. To znamená, že počet posunů je vypočítán z `count & 0x1F` (nebo `count & 0b_1_1111`).

- Pokud typ `x` je [dlouhé](../keywords/long.md) nebo [ulong](../keywords/ulong.md), počet posunů je dán nižšího řádu *šest* bits druhého operandu. To znamená, že počet posunů je vypočítán z `count & 0x3F` (nebo `count & 0b_11_1111`).

Následující příklad ukazuje toto chování:

[!code-csharp-interactive[shift count example](~/samples/snippets/csharp/language-reference/operators/ShiftOperatorsExamples.cs#RightShiftByLargeCount)]

## <a name="remarks"></a>Poznámky

Operace posunutí nikdy způsobit přetečení a produkuje stejné výsledky v [zaškrtnuto a nezaškrtnuto](../keywords/checked-and-unchecked.md) kontexty.

## <a name="operator-overloadability"></a>Overloadability – operátor

Uživatelem definované typy lze [přetížení](../keywords/operator.md) `>>` operátor. Pokud uživatelský typ `T` přetížení `>>` operátoru musí být typu prvního operandu `T` a musí být typu druhého operandu `int`. Když `>>` je operátor přetížen, [operátor přiřazení posunutí doprava](right-shift-assignment-operator.md) `>>=` je také implicitně přetížené.

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace najdete v tématu [operátory posunutí](~/_csharplang/spec/expressions.md#shift-operators) část [ C# specifikace jazyka](../language-specification/index.md).

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka C#](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [C#operátory](index.md)
- [<< – operátor](left-shift-operator.md)