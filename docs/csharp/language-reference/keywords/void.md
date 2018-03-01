---
title: "void (Referenční dokumentace jazyka C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- void_CSharpKeyword
- void
helpviewer_keywords:
- void keyword [C#]
ms.assetid: 0d2d8a95-fe20-4fbd-bf5d-c1e54bce71d4
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: a71cac30132417abce60cdde54322b5f2067d39d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="void-c-reference"></a>void (Referenční dokumentace jazyka C#)
Když se použije jako návratový typ pro metodu, `void` Určuje, že metoda nevrací hodnotu.

`void`v seznamu parametrů metody není povolena. Metoda, která nepřijímá žádné parametry a nevrací žádnou hodnotu je deklarovaná následujícím způsobem:

```csharp
public void SampleMethod()
{
    // Body of the method.
}
```

`void`se také používá v kontextu unsafe deklarovat ukazatel na neznámého typu. Další informace najdete v tématu [typy ukazatelů](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md).

`void`je alias pro rozhraní .NET Framework <xref:System.Void?displayProperty=nameWithType> typu.

## <a name="c-language-specification"></a>Specifikace jazyka C#
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Viz také
 [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
 [Průvodce programováním v C#](../../../csharp/programming-guide/index.md)  
 [Klíčová slova jazyka C#](../../../csharp/language-reference/keywords/index.md)  
 [Odkazové typy](../../../csharp/language-reference/keywords/reference-types.md)  
 [Typy hodnot](../../../csharp/language-reference/keywords/value-types.md)  
 [Metody](../../../csharp/programming-guide/classes-and-structs/methods.md)  
 [Nezabezpečený kód a ukazatele](../../../csharp/programming-guide/unsafe-code-pointers/index.md)
