---
title: sizeof – C# operátor odkazu
ms.custom: seodec18
ms.date: 07/25/2019
f1_keywords:
- sizeof_CSharpKeyword
- sizeof
helpviewer_keywords:
- sizeof keyword [C#]
ms.assetid: c548592c-677c-4f40-a4ce-e613f7529141
ms.openlocfilehash: 4852e1166a975b1a45c5bd905123a35fc846aa28
ms.sourcegitcommit: 463f3f050cecc0b6403e67f19a61f870fb8e7b7d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/26/2019
ms.locfileid: "68513160"
---
# <a name="sizeof-operator-c-reference"></a>sizeof – operátorC# (Referenční dokumentace)

`sizeof` Operátor vrátí počet bajtů obsazených proměnnou daného typu. Argumentem `sizeof` operátoru musí být název nespravovaného [typu](../builtin-types/unmanaged-types.md) nebo parametr typu, který je [omezený](../../programming-guide/generics/constraints-on-type-parameters.md#unmanaged-constraint) na nespravovaný typ.

Operátor vyžaduje nezabezpečený kontext. [](../keywords/unsafe.md) `sizeof` Výrazy uvedené v následující tabulce jsou však vyhodnocovány v době kompilace do odpovídajících konstantních hodnot a nevyžadují nezabezpečený kontext:

|Výraz|Hodnota konstanty|
|---------|---------------|
|`sizeof(sbyte)`|1|
|`sizeof(byte)`|1|
|`sizeof(short)`|2|
|`sizeof(ushort)`|2|
|`sizeof(int)`|4|
|`sizeof(uint)`|4|
|`sizeof(long)`|8|
|`sizeof(ulong)`|8|
|`sizeof(char)`|2|
|`sizeof(float)`|4|
|`sizeof(double)`|8|
|`sizeof(decimal)`|16|
|`sizeof(bool)`|1|

Nemusíte také používat nezabezpečený kontext, pokud je operandem `sizeof` operátoru název typu [výčtu](../keywords/enum.md) .

Následující příklad ukazuje použití `sizeof` operátoru:

[!code-csharp[sizeof examples](~/samples/csharp/language-reference/operators/SizeOfOperator.cs)]

`sizeof` Operátor vrátí počet bajtů, které by byly přiděleny modulem CLR (Common Language Runtime) ve spravované paměti. U typů [struktury](../keywords/struct.md) tato hodnota zahrnuje jakékoli odsazení, jak ukazuje předchozí příklad. Výsledek `sizeof` operátoru se může lišit od výsledku <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType> metody, která vrací velikost typu v nespravované paměti.

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace naleznete v části [operátor sizeof](~/_csharplang/spec/unsafe-code.md#the-sizeof-operator) ve [ C# specifikaci jazyka](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Viz také:

- [C#odkaz](../index.md)
- [Operátory jazyka C#](index.md)
- [Operátory související s ukazateli](pointer-related-operators.md)
- [Typy ukazatelů](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [Typy související s Memory a Span](../../../standard/memory-and-spans/index.md)
