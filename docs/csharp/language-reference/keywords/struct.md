---
title: struktura – C# referenční informace
ms.date: 07/20/2015
f1_keywords:
- struct_CSharpKeyword
helpviewer_keywords:
- struct keyword [C#]
- structs [C#], struct keyword
ms.assetid: ff3dd9b7-dc93-4720-8855-ef5558f65c7c
ms.openlocfilehash: 74e9909fda83c781b5a15727f79ff755e7682b0f
ms.sourcegitcommit: c01c18755bb7b0f82c7232314ccf7955ea7834db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/15/2020
ms.locfileid: "75963126"
---
# <a name="struct-c-reference"></a>struct (Referenční dokumentace jazyka C#)

Typ `struct` je typ hodnoty, který se obvykle používá k zapouzdření malých skupin souvisejících proměnných, například souřadnicích obdélníku nebo vlastností položky v inventáři. Následující příklad ukazuje jednoduchou deklaraci struktury:

```csharp
public struct Book
{
    public decimal price;
    public string title;
    public string author;
}
```

## <a name="remarks"></a>Poznámky

Struktury mohou také obsahovat [konstruktory](../../programming-guide/classes-and-structs/constructors.md), [konstanty](../../programming-guide/classes-and-structs/constants.md), [pole](../../programming-guide/classes-and-structs/fields.md), [metody](../../programming-guide/classes-and-structs/methods.md), [vlastnosti](../../programming-guide/classes-and-structs/properties.md), [indexery](../../programming-guide/indexers/index.md), [operátory](../operators/index.md), [události](../../programming-guide/events/index.md)a [vnořené typy](../../programming-guide/classes-and-structs/nested-types.md), i když Pokud je vyžadováno několik takových členů, měli byste zvážit místo toho, aby typ obsahoval třídu.

Příklady najdete v tématu [použití struktur](../../programming-guide/classes-and-structs/using-structs.md).

Struktury můžou implementovat rozhraní, ale nemůžou dědit z jiné struktury. Z tohoto důvodu členy struktury nelze deklarovat jako `protected`.

Další informace najdete v tématu [struktury](../../programming-guide/classes-and-structs/structs.md).

## <a name="examples"></a>Příklady

Příklady a další informace najdete v tématu [použití struktur](../../programming-guide/classes-and-structs/using-structs.md).

## <a name="c-language-specification"></a>specifikace jazyka C#

Příklady najdete v tématu [použití struktur](../../programming-guide/classes-and-structs/using-structs.md).

## <a name="see-also"></a>Viz také:

- [C#Odkaz](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [Klíčová slova jazyka C#](index.md)
- [Tabulka předdefinovaných typů](built-in-types-table.md)
- [Typy](/dotnet/csharp/language-reference/keywords)
- [Typy hodnot](value-types.md)
- [class](class.md)
- [interface](interface.md)
- [Třídy a struktury](../../programming-guide/classes-and-structs/index.md)
