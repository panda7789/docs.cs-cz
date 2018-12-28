---
title: void – C# odkaz
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- void_CSharpKeyword
- void
helpviewer_keywords:
- void keyword [C#]
ms.assetid: 0d2d8a95-fe20-4fbd-bf5d-c1e54bce71d4
ms.openlocfilehash: ce52e4d19335db0e21637b87bbd1589c86c06ae1
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/19/2018
ms.locfileid: "53613125"
---
# <a name="void-c-reference"></a>void (Referenční dokumentace jazyka C#)

Při použití jako návratový typ pro metodu, `void` Určuje, že metoda nevrací hodnotu.

`void` není povoleno v seznamu parametrů metody. Metoda, která nepřijímá žádné parametry a nevrací žádnou hodnotu, je deklarována následovně:

```csharp
public void SampleMethod()
{
    // Body of the method.
}
```

`void` slouží také v nezabezpečeném kontextu. Chcete-li deklarovat ukazatel na neznámého typu. Další informace najdete v tématu [typy ukazatelů](../../programming-guide/unsafe-code-pointers/pointer-types.md).

`void` je alias pro rozhraní .NET Framework <xref:System.Void?displayProperty=nameWithType> typu.

## <a name="c-language-specification"></a>specifikace jazyka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka C#](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [Klíčová slova jazyka C#](index.md)
- [Odkazové typy](reference-types.md)
- [Typy hodnot](value-types.md)
- [Metody](../../programming-guide/classes-and-structs/methods.md)
- [Nebezpečný kód a ukazatele](../../programming-guide/unsafe-code-pointers/index.md)