---
title: Nespravované typy C# – referenční informace
ms.date: 09/06/2019
helpviewer_keywords:
- unmanaged type [C#]
ms.openlocfilehash: 25aa42ba8c8f0023b4f818feb2edbb325f805fb6
ms.sourcegitcommit: c70542d02736e082e8dac67dad922c19249a8893
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2019
ms.locfileid: "70374106"
---
# <a name="unmanaged-types-c-reference"></a>Nespravované typyC# (Referenční dokumentace)

Typ je **nespravovaný typ** , pokud se jedná o některý z následujících typů:

- `sbyte`, `byte` ,`short`, ,`int`, ,`long`,,,, ,`double`nebo `uint` `ulong` `char` `float` `ushort` `decimal``bool`
- Libovolný typ [výčtu](../keywords/enum.md)
- Libovolný typ [ukazatele](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- Libovolný uživatelsky definovaný typ [struktury](../keywords/struct.md) , který obsahuje pole nespravovaných typů a v C# 7,3 a starších verzích není konstruovaný typ (typ, který obsahuje alespoň jeden argument typu).

Počínaje C# 7,3 můžete [ `unmanaged` omezení](../../programming-guide/generics/constraints-on-type-parameters.md#unmanaged-constraint) použít k určení toho, že parametr typu je nespravovaný typ bez ukazatele.

Počínaje C# 8,0, *konstruovaný* typ struktury obsahující pole pouze nespravovaných typů je také nespravovaný, jak ukazuje následující příklad:

[!code-csharp[unmanaged constructed types](~/samples/csharp/language-reference/builtin-types/UnmanagedTypes.cs#ProgramExample)]

Obecná struktura může být zdrojem nespravovaných i nespravovaných konstruovaných typů. Předchozí příklad definuje obecnou strukturu `Coords<T>` a prezentuje příklady nespravovaných konstruovaných typů. Příkladem nespravovaného typu je `Coords<object>`. Není nespravované, protože má pole `object` typu, která nejsou nespravována. Pokud chcete, aby *všechny* vytvořené typy byly nespravované typy, použijte `unmanaged` omezení v definici obecné struktury:

[!code-csharp[unmanaged constraint in type definition](~/samples/csharp/language-reference/builtin-types/UnmanagedTypes.cs#AlwaysUnmanaged)]

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace naleznete v části [typy ukazatelů](~/_csharplang/spec/unsafe-code.md#pointer-types) ve [ C# specifikaci jazyka](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Viz také:

- [C#odkaz](../index.md)
- [Typy ukazatelů](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [Typy související s Memory a Span](../../../standard/memory-and-spans/index.md)
- [sizeof – operátor](../operators/sizeof.md)
- [stackalloc – operátor](../operators/stackalloc.md)
