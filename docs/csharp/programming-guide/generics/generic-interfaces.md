---
title: Obecná rozhraní – Průvodce programováním v C#
description: Seznamte se s používáním obecných rozhraní v jazyce C#. Podívejte se na příklady kódu a zobrazte další dostupné prostředky.
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, generic interfaces
- generics [C#], interfaces
ms.assetid: a8fa49a1-6e78-4a09-87e5-84a0b9f5ffbe
ms.openlocfilehash: 43817a236e95b3ab8fd0ba94da98457eeec2396c
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/28/2020
ms.locfileid: "87301889"
---
# <a name="generic-interfaces-c-programming-guide"></a>Obecná rozhraní (Průvodce programováním v C#)
Často je užitečné definovat rozhraní buď pro obecné třídy kolekce, nebo pro obecné třídy, které reprezentují položky v kolekci. Preference pro obecné třídy je použití obecných rozhraní, například <xref:System.IComparable%601> spíše než <xref:System.IComparable> , aby se zabránilo zabalení a rozbalení operací na typech hodnot. Knihovna tříd .NET Framework definuje několik obecných rozhraní pro použití s třídami kolekce v <xref:System.Collections.Generic> oboru názvů.  
  
 Když je rozhraní zadáno jako omezení parametru typu, lze použít pouze typy, které implementují rozhraní. Následující příklad kódu ukazuje `SortedList<T>` třídu, která je odvozena od `GenericList<T>` třídy. Další informace najdete v tématu [Úvod do obecných typů](./index.md). `SortedList<T>`Přidá omezení `where T : IComparable<T>` . To umožňuje, aby `BubbleSort` metoda v nástroji `SortedList<T>` používala obecnou <xref:System.IComparable%601.CompareTo%2A> metodu pro prvky seznamu. V tomto příkladu jsou prvky seznamu jednoduchou třídou, `Person` , která implementuje `IComparable<Person>` .  
  
 [!code-csharp[csProgGuideGenerics#29](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics2.cs#29)]  
  
 Více rozhraní lze zadat jako omezení pro jeden typ následujícím způsobem:  
  
 [!code-csharp[csProgGuideGenerics#30](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#30)]  
  
 Rozhraní může definovat více než jeden parametr typu, a to následujícím způsobem:  
  
 [!code-csharp[csProgGuideGenerics#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#31)]  
  
 Pravidla dědičnosti, která se vztahují na třídy, se vztahují také na rozhraní:  
  
 [!code-csharp[csProgGuideGenerics#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#32)]  
  
 Obecná rozhraní mohou dědit z neobecných rozhraní, pokud je obecné rozhraní kontravariantní, což znamená, že používá pouze parametr typu jako návratovou hodnotu. V knihovně tříd .NET Framework <xref:System.Collections.Generic.IEnumerable%601> dědí z, <xref:System.Collections.IEnumerable> protože <xref:System.Collections.Generic.IEnumerable%601> používá pouze `T` v návratové hodnotě <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> a v <xref:System.Collections.Generic.IEnumerator%601.Current%2A> getter vlastnosti.  
  
 Konkrétní třídy mohou implementovat uzavřená vytvořená rozhraní, a to následujícím způsobem:  
  
 [!code-csharp[csProgGuideGenerics#33](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#33)]  
  
 Obecné třídy mohou implementovat Obecná rozhraní nebo uzavřená vytvořená rozhraní, pokud seznam parametrů třídy poskytuje všechny argumenty vyžadované rozhraním, a to takto:  
  
 [!code-csharp[csProgGuideGenerics#34](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#34)]  
  
 Pravidla, která řídí přetížení metody, jsou stejná pro metody v obecných třídách, obecných strukturách nebo obecných rozhraních. Další informace najdete v tématu [Obecné metody](./generic-methods.md).  
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním v C#](../index.md)
- [Úvod do obecných typů](./index.md)
- [prostředí](../../language-reference/keywords/interface.md)
- [Obecné typy](../../../standard/generics/index.md)
