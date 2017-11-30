---
title: "Obecná rozhraní (Průvodce programováním v C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- C# language, generic interfaces
- generics [C#], interfaces
ms.assetid: a8fa49a1-6e78-4a09-87e5-84a0b9f5ffbe
caps.latest.revision: "28"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 0326a7bc459c641cbfafe39fe36525a947051c16
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="generic-interfaces-c-programming-guide"></a>Obecná rozhraní (Průvodce programováním v C#)
Je často užitečné k definování rozhraní pro obecné kolekce třídy, nebo pro obecné třídy, které představují položky v kolekci. Předvolby pro obecné třídy je pomocí obecných rozhraní, jako například <xref:System.IComparable%601> místo <xref:System.IComparable>, aby se zabránilo operace zabalení a rozbalení u typů hodnot. Definuje několik obecných rozhraní pro použití s třídy kolekce v knihovně tříd rozhraní .NET Framework <xref:System.Collections.Generic> oboru názvů.  
  
 Pokud je zadána jako parametr typu omezení, lze použít pouze typy, které implementují rozhraní. Následující příklad kódu ukazuje `SortedList<T>` třídu odvozenou od `GenericList<T>` třídy. Další informace najdete v tématu [Úvod do obecných typů](../../../csharp/programming-guide/generics/introduction-to-generics.md). `SortedList<T>`Přidá omezení `where T : IComparable<T>`. Díky tomu `BubbleSort` metoda v `SortedList<T>` používat obecná <xref:System.IComparable%601.CompareTo%2A> metoda v seznamu elementů. V tomto příkladu jsou seznamu elementů třídu jednoduché `Person`, která implementuje `IComparable<Person>`.  
  
 [!code-csharp[csProgGuideGenerics#29](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-interfaces_1.cs)]  
  
 Více rozhraní lze zadat jako omezení typu, následujícím způsobem:  
  
 [!code-csharp[csProgGuideGenerics#30](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-interfaces_2.cs)]  
  
 Rozhraní můžete definovat více než jeden parametr typu následujícím způsobem:  
  
 [!code-csharp[csProgGuideGenerics#31](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-interfaces_3.cs)]  
  
 Pravidla dědičnosti, které se vztahují na třídy platí i pro rozhraní:  
  
 [!code-csharp[csProgGuideGenerics#32](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-interfaces_4.cs)]  
  
 Obecná rozhraní může dědit vlastnosti z rozhraní neobecnou, pokud obecné rozhraní opravné položky ke variant, což znamená, že její parametr typu se použije pouze jako návratová hodnota. V knihovně tříd rozhraní .NET Framework <xref:System.Collections.Generic.IEnumerable%601> dědí z <xref:System.Collections.IEnumerable> protože <xref:System.Collections.Generic.IEnumerable%601> používá jenom `T` v návratové hodnotě <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> a v <xref:System.Collections.Generic.IEnumerator%601.Current%2A> metoda getter vlastnosti.  
  
 Konkrétní třídy můžete implementovat uzavřené sestavené rozhraní, následujícím způsobem:  
  
 [!code-csharp[csProgGuideGenerics#33](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-interfaces_5.cs)]  
  
 Obecné třídy můžete implementovat obecné rozhraní nebo uzavřených sestavené rozhraní také seznam parametrů třída poskytuje všechny argumenty, které vyžadují rozhraní, následujícím způsobem:  
  
 [!code-csharp[csProgGuideGenerics#34](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-interfaces_6.cs)]  
  
 Pravidla, která řídí přetěžování metody jsou stejné pro metody v obecné třídy, struktury obecné nebo obecná rozhraní. Další informace najdete v tématu [obecné metody](../../../csharp/programming-guide/generics/generic-methods.md).  
  
## <a name="see-also"></a>Viz také  
 [Průvodce programováním v C#](../../../csharp/programming-guide/index.md)  
 [Úvod do obecných typů](../../../csharp/programming-guide/generics/introduction-to-generics.md)  
 [rozhraní](../../../csharp/language-reference/keywords/interface.md)  
 [Obecné typy](~/docs/standard/generics/index.md)
