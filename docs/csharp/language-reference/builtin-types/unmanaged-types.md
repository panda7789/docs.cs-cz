---
description: 'Další informace o nespravovaných typech v jazyce C #'
title: Nespravované typy – reference jazyka C#
ms.date: 09/06/2019
helpviewer_keywords:
- unmanaged type [C#]
ms.openlocfilehash: b5a689ca3ade36ef77da958549894f76e074986e
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89143529"
---
# <a name="unmanaged-types-c-reference"></a>Nespravované typy (Referenční dokumentace jazyka C#)

Typ je **nespravovaný typ** , pokud se jedná o některý z následujících typů:

- `sbyte`, `byte` , `short` , `ushort` , `int` , `uint` , `long` , `ulong` , `char` , `float` , `double` , `decimal` nebo `bool`
- Libovolný typ [výčtu](enum.md)
- Libovolný typ [ukazatele](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- Libovolný uživatelsky definovaný typ [struktury](struct.md) , který obsahuje pouze pole nespravovaných typů a v jazyce C# 7,3 a starší není konstruovaný typ (typ, který obsahuje alespoň jeden argument typu).

Počínaje jazykem C# 7,3 můžete použít [ `unmanaged` omezení](../../programming-guide/generics/constraints-on-type-parameters.md#unmanaged-constraint) , chcete-li určit, že parametr typu je nespravovaný typ bez hodnoty null.

Počínaje jazykem C# 8,0 je typ *konstruované* struktury obsahující pole pouze nespravovaných typů také nespravovaný, jak ukazuje následující příklad:

[!code-csharp[unmanaged constructed types](snippets/UnmanagedTypes.cs#ProgramExample)]

Obecná struktura může být zdrojem nespravovaných i nespravovaných konstruovaných typů. Předchozí příklad definuje obecnou strukturu `Coords<T>` a prezentuje příklady nespravovaných konstruovaných typů. Příkladem nespravovaného typu je `Coords<object>` . Není nespravované, protože má pole `object` typu, která nejsou nespravována. Pokud chcete, aby *všechny* vytvořené typy byly nespravované typy, použijte `unmanaged` omezení v definici obecné struktury:

[!code-csharp[unmanaged constraint in type definition](snippets/UnmanagedTypes.cs#AlwaysUnmanaged)]

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace naleznete v části [typy ukazatelů](~/_csharplang/spec/unsafe-code.md#pointer-types) v tématu [specifikace jazyka C#](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Viz také

- [Referenční dokumentace k jazyku C#](../index.md)
- [Typy ukazatelů](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [Typy související s Memory a Span](../../../standard/memory-and-spans/index.md)
- [sizeof – operátor](../operators/sizeof.md)
- [stackalloc](../operators/stackalloc.md)
