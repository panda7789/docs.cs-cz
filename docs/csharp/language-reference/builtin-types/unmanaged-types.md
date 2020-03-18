---
title: Nespravované typy – odkaz jazyka C#
ms.date: 09/06/2019
helpviewer_keywords:
- unmanaged type [C#]
ms.openlocfilehash: 8a4599514115aa21f17c32848ce203fea704072e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "78846458"
---
# <a name="unmanaged-types-c-reference"></a>Nespravované typy (odkaz Jazyka C#)

Typ je **nespravovaný typ,** pokud se jedná o některý z následujících typů:

- `sbyte`, `byte` `short`, `ushort` `int`, `uint` `long`, `ulong` `char`, `float` `double`, `decimal`, , , , , , nebo`bool`
- Libovolný typ [výčtu](enum.md)
- Libovolný typ [ukazatele](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- Jakýkoli uživatelem definovaný typ [struktury,](struct.md) který obsahuje pouze pole nespravovaných typů a v c# 7.3 a starších není konstruovaným typem (typ, který obsahuje alespoň jeden argument typu)

Počínaje C# 7.3, můžete použít [ `unmanaged` omezení](../../programming-guide/generics/constraints-on-type-parameters.md#unmanaged-constraint) k určení, že parametr typu je neukazatel, nenulelný nespravovaný typ.

Počínaje C# 8.0, *konstruované* struct typ, který obsahuje pouze pole nespravovaných typů je také nespravované, jak ukazuje následující příklad:

[!code-csharp[unmanaged constructed types](snippets/UnmanagedTypes.cs#ProgramExample)]

Obecná struktura může být zdrojem nespravovaných i nespravovaných konstrukčních typů. Předchozí příklad definuje obecnou strukturu `Coords<T>` a představuje příklady nespravovaných konstruovaných typů. Příkladem nespravovaného typu je `Coords<object>`. Není nespravované, protože má pole `object` typu, který není nespravované. Pokud *chcete,* aby všechny konstruované typy byly `unmanaged` nespravované typy, použijte omezení v definici obecné struktury:

[!code-csharp[unmanaged constraint in type definition](snippets/UnmanagedTypes.cs#AlwaysUnmanaged)]

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace naleznete v části [Typy ukazatelů](~/_csharplang/spec/unsafe-code.md#pointer-types) [ve specifikaci jazyka C#](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Viz také

- [Referenční dokumentace k jazyku C#](../index.md)
- [Typy ukazatelů](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [Typy související s Memory a Span](../../../standard/memory-and-spans/index.md)
- [sizeof – operátor](../operators/sizeof.md)
- [Operátor stackalloc](../operators/stackalloc.md)
