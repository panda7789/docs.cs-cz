---
title: void – C# odkaz
ms.date: 07/20/2015
f1_keywords:
- void_CSharpKeyword
- void
helpviewer_keywords:
- void keyword [C#]
ms.assetid: 0d2d8a95-fe20-4fbd-bf5d-c1e54bce71d4
ms.openlocfilehash: 0624b547ee2586334ac35d366ae3c8dfd14963ee
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742770"
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

- [C#odkaz](../index.md)
- [Klíčová slova jazyka C#](index.md)
- [Typy odkazů](reference-types.md)
- [Typy hodnot](../builtin-types/value-types.md)
- [Metody](../../programming-guide/classes-and-structs/methods.md)
- [Nezabezpečený kód a ukazatele](../../programming-guide/unsafe-code-pointers/index.md)
