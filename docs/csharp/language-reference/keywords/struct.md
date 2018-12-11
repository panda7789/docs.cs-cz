---
title: struct – C# odkaz
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- struct_CSharpKeyword
helpviewer_keywords:
- struct keyword [C#]
- structs [C#], struct keyword
ms.assetid: ff3dd9b7-dc93-4720-8855-ef5558f65c7c
ms.openlocfilehash: 2d0cba75e067e4d75ca5b544a664d7dede153c73
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53237529"
---
# <a name="struct-c-reference"></a>struct (Referenční dokumentace jazyka C#)

A `struct` typ je typ hodnoty, které se obvykle používá k zapouzdření malé skupiny příbuzných proměnných, jako je například souřadnice obdélník nebo vlastnosti položky v inventář. Následující příklad ukazuje deklaraci jednoduchá struktura:

```csharp
public struct Book
{
    public decimal price;
    public string title;
    public string author;
}
```

## <a name="remarks"></a>Poznámky

Struktury mohou také obsahovat [konstruktory](../../programming-guide/classes-and-structs/constructors.md), [konstanty](../../programming-guide/classes-and-structs/constants.md), [pole](../../programming-guide/classes-and-structs/fields.md), [metody](../../programming-guide/classes-and-structs/methods.md), [vlastnosti](../../programming-guide/classes-and-structs/properties.md), [indexery](../../programming-guide/indexers/index.md), [operátory](../../programming-guide/statements-expressions-operators/operators.md), [události](../../programming-guide/events/index.md), a [vnořené typy](../../programming-guide/classes-and-structs/nested-types.md), i když je-li několik těchto členů jsou povinné, můžete Zvažte, Příprava vašeho typu třídy místo toho.

Příklady najdete v tématu [pomocí struktury](../../programming-guide/classes-and-structs/using-structs.md).

Struktury můžou implementovat rozhraní, ale nemůže dědit z jiné struktury. Z tohoto důvodu členy struktury nelze deklarovat jako `protected`.

Další informace najdete v tématu [struktury](../../programming-guide/classes-and-structs/structs.md).

## <a name="examples"></a>Příklady

Příklady a další informace najdete v tématu [pomocí struktury](../../programming-guide/classes-and-structs/using-structs.md).

## <a name="c-language-specification"></a>specifikace jazyka C#

Příklady najdete v tématu [pomocí struktury](../../programming-guide/classes-and-structs/using-structs.md).

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka C#](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [Klíčová slova jazyka C#](index.md)
- [Tabulka výchozích hodnot](default-values-table.md)
- [Tabulka předdefinovaných typů](built-in-types-table.md)
- [Typy](types.md)
- [Typy hodnot](value-types.md)
- [class](class.md)
- [interface](interface.md)
- [Třídy a struktury](../../programming-guide/classes-and-structs/index.md)