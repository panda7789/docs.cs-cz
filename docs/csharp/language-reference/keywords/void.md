---
title: void (Referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- void_CSharpKeyword
- void
helpviewer_keywords:
- void keyword [C#]
ms.assetid: 0d2d8a95-fe20-4fbd-bf5d-c1e54bce71d4
ms.openlocfilehash: e66efc287fc3ed0fcc15963a827fccb788c38753
ms.sourcegitcommit: 60645077dc4b62178403145f8ef691b13ffec28e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2018
ms.locfileid: "37960557"
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
 [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Klíčová slova jazyka C#](../../../csharp/language-reference/keywords/index.md)  
 [Odkazové typy](../../../csharp/language-reference/keywords/reference-types.md)  
 [Typy hodnot](../../../csharp/language-reference/keywords/value-types.md)  
 [Metody](../../../csharp/programming-guide/classes-and-structs/methods.md)  
 [Nebezpečný kód a ukazatele](../../../csharp/programming-guide/unsafe-code-pointers/index.md)
