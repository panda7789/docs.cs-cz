---
title: << operátor - C# odkaz
ms.custom: seodec18
ms.date: 02/12/2019
f1_keywords:
- <<_CSharpKeyword
helpviewer_keywords:
- left shift operator (<<) [C#]
- << operator [C#]
ms.assetid: a654eb56-1ff7-4bf3-9064-b631be0cdccc
ms.openlocfilehash: deea2d0f720ba7f096e65c67378586bc88f24673
ms.sourcegitcommit: 30e2fe5cc4165aa6dde7218ec80a13def3255e98
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/13/2019
ms.locfileid: "56219432"
---
# <a name="-operator-c-reference"></a>\<\< – Operátor (referenční dokumentace jazyka C#)

Operátor posunutí doleva `<<` staffhubu svůj první operand doleva o počet bitů, které jsou určené svým druhým operandem. Podporují všechny typy celých čísel `<<` operátor. Však musí být typu druhého operandu [int](../keywords/int.md) nebo typ, který má [předdefinované implicitní převod čísla](../keywords/implicit-numeric-conversions-table.md) k `int`.

Horní bity, které jsou mimo rozsah typu výsledku ignorovány a nižšího řádu prázdný bitové pozice jsou nastaveny na nulu, jak ukazuje následující příklad:

[!code-csharp-interactive[left shift example](~/samples/snippets/csharp/language-reference/operators/ShiftOperatorsExamples.cs#LeftShift)]

## <a name="shift-count"></a>Počet posunutí

Pro výraz `x << count`, počet skutečné posunutí závisí na typu `x` následujícím způsobem:

- Pokud typ `x` je [int](../keywords/int.md) nebo [uint](../keywords/uint.md), počet posunů je dán nižšího řádu *pět* bits druhého operandu. To znamená, že počet posunů je vypočítán z `count & 0x1F` (nebo `count & 0b_1_1111`).

- Pokud typ `x` je [dlouhé](../keywords/long.md) nebo [ulong](../keywords/ulong.md), počet posunů je dán nižšího řádu *šest* bits druhého operandu. To znamená, že počet posunů je vypočítán z `count & 0x3F` (nebo `count & 0b_11_1111`).

Následující příklad ukazuje toto chování:

[!code-csharp-interactive[shift count example](~/samples/snippets/csharp/language-reference/operators/ShiftOperatorsExamples.cs#LeftShiftByLargeCount)]

## <a name="remarks"></a>Poznámky

Operace posunutí nikdy způsobit přetečení a produkuje stejné výsledky v [zaškrtnuto a nezaškrtnuto](../keywords/checked-and-unchecked.md) kontexty.

## <a name="operator-overloadability"></a>Overloadability – operátor

Uživatelem definované typy lze [přetížení](../keywords/operator.md) `<<` operátor. Pokud uživatelský typ `T` přetížení `<<` operátoru musí být typu prvního operandu `T` a musí být typu druhého operandu `int`. Když `<<` je operátor přetížen, [operátor přiřazení posunutí doleva](left-shift-assignment-operator.md) `<<=` je také implicitně přetížené.

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace najdete v tématu [operátory posunutí](~/_csharplang/spec/expressions.md#shift-operators) část [ C# specifikace jazyka](../language-specification/index.md).

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka C#](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [Operátory jazyka C#](index.md)
- [>> – operátor](right-shift-operator.md)
