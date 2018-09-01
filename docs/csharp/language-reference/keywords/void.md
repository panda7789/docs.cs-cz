---
title: void (Referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- void_CSharpKeyword
- void
helpviewer_keywords:
- void keyword [C#]
ms.assetid: 0d2d8a95-fe20-4fbd-bf5d-c1e54bce71d4
ms.openlocfilehash: 223db893dd42181c234d9a07c1a1c00af26f0c30
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43397084"
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

`void` slouží také v nezabezpečeném kontextu. Chcete-li deklarovat ukazatel na neznámého typu. Další informace najdete v tématu [typy ukazatelů](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md).

`void` je alias pro rozhraní .NET Framework <xref:System.Void?displayProperty=nameWithType> typu.

## <a name="c-language-specification"></a>Specifikace jazyka C#
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
- [Klíčová slova jazyka C#](../../../csharp/language-reference/keywords/index.md)  
- [Odkazové typy](../../../csharp/language-reference/keywords/reference-types.md)  
- [Typy hodnot](../../../csharp/language-reference/keywords/value-types.md)  
- [Metody](../../../csharp/programming-guide/classes-and-structs/methods.md)  
- [Nebezpečný kód a ukazatele](../../../csharp/programming-guide/unsafe-code-pointers/index.md)
