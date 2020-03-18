---
title: sizeof operátor - c# odkaz
ms.date: 07/25/2019
f1_keywords:
- sizeof_CSharpKeyword
- sizeof
helpviewer_keywords:
- sizeof keyword [C#]
ms.assetid: c548592c-677c-4f40-a4ce-e613f7529141
ms.openlocfilehash: a9e80ecb3288479a2ca81b43c9d088809ed5f2f0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "78847284"
---
# <a name="sizeof-operator-c-reference"></a>sizeof operátor (odkaz C# )

Operátor `sizeof` vrátí počet bajtů obsazených proměnnou daného typu. Argument emitovaný `sizeof` operátorem musí být název [nespravovaného typu](../builtin-types/unmanaged-types.md) nebo parametr typu, který je [omezen](../../programming-guide/generics/constraints-on-type-parameters.md#unmanaged-constraint) na nespravovaný typ.

Operátor `sizeof` vyžaduje [nebezpečný](../keywords/unsafe.md) kontext. Výrazy uvedené v následující tabulce jsou však vyhodnocovány v době kompilace na odpovídající konstantní hodnoty a nevyžadují nebezpečný kontext:

|Expression|Konstantní hodnota|
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

Také není nutné použít nebezpečný kontext, pokud operand `sizeof` operátoru je název typu [výčtu.](../builtin-types/enum.md)

Následující příklad ukazuje použití operátoru: `sizeof`

[!code-csharp[sizeof examples](snippets/SizeOfOperator.cs)]

Operátor `sizeof` vrátí počet bajtů, které by byly přiděleny za běhu společného jazyka ve spravované paměti. Pro [typy struktury](../builtin-types/struct.md) tato hodnota zahrnuje všechny odsazení, jak ukazuje předchozí příklad. Výsledek operátoru `sizeof` se může lišit od <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType> výsledku metody, která vrací velikost typu v *nespravované* paměti.

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace naleznete v části [sizeof operator](~/_csharplang/spec/unsafe-code.md#the-sizeof-operator) [specifikace jazyka C#](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Viz také

- [Referenční dokumentace k jazyku C#](../index.md)
- [Operátory jazyka C#](index.md)
- [Operátory související s ukazatelem](pointer-related-operators.md)
- [Typy ukazatelů](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [Typy související s Memory a Span](../../../standard/memory-and-spans/index.md)
- [Obecné typy v .NET](../../../standard/generics/index.md)
