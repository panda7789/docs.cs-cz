---
title: Obecná rozhraní – C# Průvodce programováním
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, generic interfaces
- generics [C#], interfaces
ms.assetid: a8fa49a1-6e78-4a09-87e5-84a0b9f5ffbe
ms.openlocfilehash: 4cce23da7579e30ecff80b3afb92a5a58795c1bd
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712205"
---
# <a name="generic-interfaces-c-programming-guide"></a>Obecná rozhraní (Průvodce programováním v C#)
Často je užitečné definovat rozhraní buď pro obecné třídy kolekce, nebo pro obecné třídy, které reprezentují položky v kolekci. Preference pro obecné třídy je použití obecných rozhraní, například <xref:System.IComparable%601> spíše než <xref:System.IComparable>, aby se předešlo zabalení a rozbalení operací na typech hodnot. Knihovna tříd .NET Framework definuje několik obecných rozhraní pro použití s třídami kolekce v oboru názvů <xref:System.Collections.Generic>.  
  
 Když je rozhraní zadáno jako omezení parametru typu, lze použít pouze typy, které implementují rozhraní. Následující příklad kódu ukazuje třídu `SortedList<T>`, která je odvozena od `GenericList<T>` třídy. Další informace najdete v tématu [Úvod do obecných typů](./index.md). `SortedList<T>` přidá omezení `where T : IComparable<T>`. To umožňuje, aby metoda `BubbleSort` v `SortedList<T>` používala obecnou <xref:System.IComparable%601.CompareTo%2A> metodu pro prvky seznamu. V tomto příkladu jsou prvky seznamu jednoduchou třídou, `Person`, která implementuje `IComparable<Person>`.  
  
 [!code-csharp[csProgGuideGenerics#29](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics2.cs#29)]  
  
 Více rozhraní lze zadat jako omezení pro jeden typ následujícím způsobem:  
  
 [!code-csharp[csProgGuideGenerics#30](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#30)]  
  
 Rozhraní může definovat více než jeden parametr typu, a to následujícím způsobem:  
  
 [!code-csharp[csProgGuideGenerics#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#31)]  
  
 Pravidla dědičnosti, která se vztahují na třídy, se vztahují také na rozhraní:  
  
 [!code-csharp[csProgGuideGenerics#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#32)]  
  
 Obecná rozhraní mohou dědit z neobecných rozhraní, pokud je obecné rozhraní kontravariantní, což znamená, že používá pouze parametr typu jako návratovou hodnotu. V knihovně tříd .NET Framework <xref:System.Collections.Generic.IEnumerable%601> dědí z <xref:System.Collections.IEnumerable> protože <xref:System.Collections.Generic.IEnumerable%601> používá pouze `T` v návratové hodnotě <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> a ve vlastnosti getter metody <xref:System.Collections.Generic.IEnumerator%601.Current%2A>.  
  
 Konkrétní třídy mohou implementovat uzavřená vytvořená rozhraní, a to následujícím způsobem:  
  
 [!code-csharp[csProgGuideGenerics#33](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#33)]  
  
 Obecné třídy mohou implementovat Obecná rozhraní nebo uzavřená vytvořená rozhraní, pokud seznam parametrů třídy poskytuje všechny argumenty vyžadované rozhraním, a to takto:  
  
 [!code-csharp[csProgGuideGenerics#34](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#34)]  
  
 Pravidla, která řídí přetížení metody, jsou stejná pro metody v obecných třídách, obecných strukturách nebo obecných rozhraních. Další informace najdete v tématu [Obecné metody](./generic-methods.md).  
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../index.md)
- [Úvod do obecných typů](./index.md)
- [interface](../../language-reference/keywords/interface.md)
- [Obecné typy](../../../standard/generics/index.md)
