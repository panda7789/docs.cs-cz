---
title: Obecná rozhraní – programovací příručka jazyka C#
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, generic interfaces
- generics [C#], interfaces
ms.assetid: a8fa49a1-6e78-4a09-87e5-84a0b9f5ffbe
ms.openlocfilehash: 4cce23da7579e30ecff80b3afb92a5a58795c1bd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712205"
---
# <a name="generic-interfaces-c-programming-guide"></a>Obecná rozhraní (Průvodce programováním v C#)
Je často užitečné definovat rozhraní pro obecné třídy kolekce nebo pro obecné třídy, které představují položky v kolekci. Předvolbou pro obecné třídy je použití <xref:System.IComparable%601> obecných <xref:System.IComparable>rozhraní, například spíše než , aby se zabránilo zabalení a rozbalení operace na typy hodnot. Knihovna tříd rozhraní .NET Framework definuje několik obecných rozhraní <xref:System.Collections.Generic> pro použití s třídami kolekce v oboru názvů.  
  
 Pokud je rozhraní zadáno jako omezení parametru typu, lze použít pouze typy, které implementují rozhraní. Následující příklad kódu `SortedList<T>` ukazuje třídu, `GenericList<T>` která je odvozena od třídy. Další informace naleznete [v tématu Úvod do obecných typů](./index.md). `SortedList<T>`přidá omezení `where T : IComparable<T>`. To umožňuje `BubbleSort` metodu v `SortedList<T>` <xref:System.IComparable%601.CompareTo%2A> použití obecné metody na list prvky. V tomto příkladu jsou prvky `Person`seznamu jednoduchou třídou , která implementuje `IComparable<Person>`.  
  
 [!code-csharp[csProgGuideGenerics#29](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics2.cs#29)]  
  
 Více rozhraní lze zadat jako omezení pro jeden typ, takto:  
  
 [!code-csharp[csProgGuideGenerics#30](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#30)]  
  
 Rozhraní může definovat více než jeden parametr typu, a to následovně:  
  
 [!code-csharp[csProgGuideGenerics#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#31)]  
  
 Pravidla dědičnosti, která platí pro třídy platí také pro rozhraní:  
  
 [!code-csharp[csProgGuideGenerics#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#32)]  
  
 Obecná rozhraní mohou dědit z neobecných rozhraní, pokud je obecné rozhraní kontravariantní, což znamená, že používá pouze parametr typu jako vrácenou hodnotu. V knihovně tříd rozhraní <xref:System.Collections.Generic.IEnumerable%601> .NET <xref:System.Collections.IEnumerable> <xref:System.Collections.Generic.IEnumerable%601> Framework `T` dědí z, <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> protože <xref:System.Collections.Generic.IEnumerator%601.Current%2A> používá pouze v návratové hodnotě a v vlastnosti getter.  
  
 Konkrétní třídy mohou implementovat uzavřené konstruované rozhraní, a to následovně:  
  
 [!code-csharp[csProgGuideGenerics#33](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#33)]  
  
 Obecné třídy mohou implementovat obecná rozhraní nebo uzavřená konstruovaná rozhraní, pokud seznam parametrů třídy poskytuje všechny argumenty vyžadované rozhraním, a to následovně:  
  
 [!code-csharp[csProgGuideGenerics#34](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#34)]  
  
 Pravidla, která řídí přetížení metody jsou stejné pro metody v rámci obecných tříd, obecných struktur nebo obecných rozhraní. Další informace naleznete [v tématu Obecné metody](./generic-methods.md).  
  
## <a name="see-also"></a>Viz také

- [Programovací příručka jazyka C#](../index.md)
- [Úvod do obecných typů](./index.md)
- [Rozhraní](../../language-reference/keywords/interface.md)
- [Obecné typy](../../../standard/generics/index.md)
