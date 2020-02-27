---
title: Nespravované typy C# – referenční informace
ms.date: 09/06/2019
helpviewer_keywords:
- unmanaged type [C#]
ms.openlocfilehash: 042cf382879cc4010a388fb75f41099b4342c9d9
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/26/2020
ms.locfileid: "77626942"
---
# <a name="unmanaged-types-c-reference"></a>Nespravované typyC# (Referenční dokumentace)

Typ je **nespravovaný typ** , pokud se jedná o některý z následujících typů:

- `sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `char`, `float`, `double`, `decimal`nebo `bool`
- Libovolný typ [výčtu](enum.md)
- Libovolný typ [ukazatele](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- Libovolný uživatelsky definovaný typ [struktury](struct.md) , který obsahuje pole nespravovaných typů a v C# 7,3 a starších verzích není konstruovaný typ (typ, který obsahuje alespoň jeden argument typu).

Počínaje C# 7,3 můžete použít [omezení`unmanaged`](../../programming-guide/generics/constraints-on-type-parameters.md#unmanaged-constraint) k určení toho, že parametr typu není ukazatel nespravovaného typu, který neumožňuje hodnotu null.

Počínaje C# 8,0, *konstruovaný* typ struktury obsahující pole pouze nespravovaných typů je také nespravovaný, jak ukazuje následující příklad:

[!code-csharp[unmanaged constructed types](~/samples/csharp/language-reference/builtin-types/UnmanagedTypes.cs#ProgramExample)]

Obecná struktura může být zdrojem nespravovaných i nespravovaných konstruovaných typů. Předchozí příklad definuje obecnou strukturu `Coords<T>` a prezentuje příklady nespravovaných konstruovaných typů. Příkladem nespravovaného typu je `Coords<object>`. Není nespravovaný, protože obsahuje pole `object` typu, který není nespravovaný. Pokud chcete, aby *všechny* vytvořené typy byly nespravované typy, použijte omezení `unmanaged` v definici obecné struktury:

[!code-csharp[unmanaged constraint in type definition](~/samples/csharp/language-reference/builtin-types/UnmanagedTypes.cs#AlwaysUnmanaged)]

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace naleznete v části [typy ukazatelů](~/_csharplang/spec/unsafe-code.md#pointer-types) ve [ C# specifikaci jazyka](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Viz také

- [C#odkaz](../index.md)
- [Typy ukazatelů](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [Typy související s Memory a Span](../../../standard/memory-and-spans/index.md)
- [sizeof – operátor](../operators/sizeof.md)
- [stackalloc – operátor](../operators/stackalloc.md)
