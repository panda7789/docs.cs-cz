---
title: "Obecné typy a pole (Průvodce programováním v C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- generics [C#], arrays
- arrays [C#], generics
ms.assetid: 7d956536-3851-41b5-94ad-3e7c0a5fe485
caps.latest.revision: "17"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 94b144075fac44ff749474a5bfa8e81aaadc0a0c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="generics-and-arrays-c-programming-guide"></a>Obecné typy a pole (Průvodce programováním v C#)
V C# 2.0 nebo novější, jednorozměrná pole, které mají dolní mez 0 automaticky implementovat <xref:System.Collections.Generic.IList%601>. To umožňuje vytvářet obecné metody, které můžete použít stejný kód k iteraci v rámci pole a dalších typů kolekce. Tento postup je užitečné hlavně pro čtení dat v kolekcích. <xref:System.Collections.Generic.IList%601> Rozhraní nelze použít k přidání nebo odebrání elementy z pole. Bude vyvolána výjimka, pokud se pokusíte volání <xref:System.Collections.Generic.IList%601> metoda jako <xref:System.Collections.Generic.IList%601.RemoveAt%2A> na pole v tomto kontextu.  
  
 Následující příklad kódu ukazuje, jak jeden obecná metoda, která přebírá <xref:System.Collections.Generic.IList%601> vstupní parametr můžete iteraci v rámci seznamu a pole, v tomto případě pole celých čísel.  
  
 [!code-csharp[csProgGuideGenerics#35](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-and-arrays_1.cs)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Collections.Generic>  
 [Průvodce programováním v C#](../../../csharp/programming-guide/index.md)  
 [Obecné typy](../../../csharp/programming-guide/generics/index.md)  
 [Pole](../../../csharp/programming-guide/arrays/index.md)  
 [Obecné typy](~/docs/standard/generics/index.md)
