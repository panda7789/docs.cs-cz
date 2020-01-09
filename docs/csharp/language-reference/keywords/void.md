---
title: void – C# odkaz
ms.date: 07/20/2015
f1_keywords:
- void_CSharpKeyword
- void
helpviewer_keywords:
- void keyword [C#]
ms.assetid: 0d2d8a95-fe20-4fbd-bf5d-c1e54bce71d4
ms.openlocfilehash: 465aaeadca603f14432478a7e5496a9ef4589ebe
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712855"
---
# <a name="void-c-reference"></a>void (Referenční dokumentace jazyka C#)

Při použití jako návratový typ pro metodu `void` určuje, že metoda nevrací hodnotu.

`void` není povolen v seznamu parametrů metody. Metoda, která nepřijímá žádné parametry a nevrací žádnou hodnotu, je deklarována takto:

```csharp
public void SampleMethod()
{
    // Body of the method.
}
```

`void` se používá také v nezabezpečeném kontextu k deklaraci ukazatele na neznámý typ. Další informace naleznete v tématu [typy ukazatelů](../../programming-guide/unsafe-code-pointers/pointer-types.md).

`void` je alias pro typ <xref:System.Void?displayProperty=nameWithType> .NET Framework.

## <a name="c-language-specification"></a>specifikace jazyka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Viz také:

- [C#Odkaz](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [Klíčová slova jazyka C#](index.md)
- [Odkazové typy](reference-types.md)
- [Typy hodnot](value-types.md)
- [Metody](../../programming-guide/classes-and-structs/methods.md)
- [Nebezpečný kód a ukazatele](../../programming-guide/unsafe-code-pointers/index.md)
