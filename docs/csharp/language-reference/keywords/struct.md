---
title: struktura – C# referenční informace
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- struct_CSharpKeyword
helpviewer_keywords:
- struct keyword [C#]
- structs [C#], struct keyword
ms.assetid: ff3dd9b7-dc93-4720-8855-ef5558f65c7c
ms.openlocfilehash: 95c36cd039436dcddd3e2e2a3e1fae98ee885677
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69924670"
---
# <a name="struct-c-reference"></a>struct (Referenční dokumentace jazyka C#)

`struct` Typ je typ hodnoty, který se obvykle používá k zapouzdření malých skupin souvisejících proměnných, například souřadnicích obdélníku nebo vlastností položky v inventáři. Následující příklad ukazuje jednoduchou deklaraci struktury:

```csharp
public struct Book
{
    public decimal price;
    public string title;
    public string author;
}
```

## <a name="remarks"></a>Poznámky

Struktury mohou také obsahovat [konstruktory](../../programming-guide/classes-and-structs/constructors.md), [konstanty](../../programming-guide/classes-and-structs/constants.md), [pole](../../programming-guide/classes-and-structs/fields.md), [metody](../../programming-guide/classes-and-structs/methods.md), [vlastnosti](../../programming-guide/classes-and-structs/properties.md), [indexery](../../programming-guide/indexers/index.md), [operátory](../operators/index.md), [události](../../programming-guide/events/index.md)a [vnořené typy](../../programming-guide/classes-and-structs/nested-types.md), i když je několik takových členů požadováno, měli byste zvážit, že místo toho napište třídu typu.

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
- [Tabulka výchozích hodnot](default-values-table.md)
- [Tabulka předdefinovaných typů](built-in-types-table.md)
- [Typy](types.md)
- [Typy hodnot](value-types.md)
- [class](class.md)
- [interface](interface.md)
- [Třídy a struktury](../../programming-guide/classes-and-structs/index.md)
