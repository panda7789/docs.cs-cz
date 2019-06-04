---
title: Typy řazených kolekcí
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- SortedDictionary collection type
- SortedList class, grouping data in collections
- grouping data in collections, SortedList collection type
- SortedList collection type
- collections [.NET Framework], SortedList collection type
ms.assetid: 3db965b2-36a6-4b12-b76e-7f074ff7275a
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 96841d23da342fdb4da6c7d53420d6c3319f75c6
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2019
ms.locfileid: "66491016"
---
# <a name="sorted-collection-types"></a>Typy řazených kolekcí
<xref:System.Collections.SortedList?displayProperty=nameWithType> Třídy, <xref:System.Collections.Generic.SortedList%602?displayProperty=nameWithType> obecné třídy a <xref:System.Collections.Generic.SortedDictionary%602?displayProperty=nameWithType> obecné třídy jsou podobné <xref:System.Collections.Hashtable> třídy a <xref:System.Collections.Generic.Dictionary%602> obecná třída v tom, že je implementovat <xref:System.Collections.IDictionary> rozhraní, ale zachovat jejich pořadí prvků v řazení podle klíče a nemají O(1) vkládání a načítání charakteristické zatřiďovacích tabulek. Tři třídy mají společnou několik funkcí:  
  
- Implementovat všechny tři třídy <xref:System.Collections.IDictionary?displayProperty=nameWithType> rozhraní. Dvě obecné třídy implementovat taky <xref:System.Collections.Generic.IDictionary%602?displayProperty=nameWithType> obecného rozhraní.  
  
- Každý prvek je dvojice klíč/hodnota pro výčet účely.  
  
    > [!NOTE]
    >  Neobecná <xref:System.Collections.SortedList> třídy vrátí <xref:System.Collections.DictionaryEntry> objekty při výčtu, i když se dvě obecné typy vrátit <xref:System.Collections.Generic.KeyValuePair%602> objekty.  
  
- Prvky jsou seřazeny podle <xref:System.Collections.IComparer?displayProperty=nameWithType> implementace (pro neobecný <xref:System.Collections.SortedList>) nebo <xref:System.Collections.Generic.IComparer%601?displayProperty=nameWithType> implementaci (pro dvě obecné třídy).  
  
- Každá třída obsahuje vlastnosti, které vracejí kolekce obsahující pouze klíče nebo hodnoty.  
  
 V následující tabulce jsou uvedeny některé rozdíly mezi dvěma třídami seřazený seznam a <xref:System.Collections.Generic.SortedDictionary%602> třídy.  
  
|<xref:System.Collections.SortedList> Neobecná třída a <xref:System.Collections.Generic.SortedList%602> obecné třídy|<xref:System.Collections.Generic.SortedDictionary%602> Obecné třídy|  
|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|Vlastnosti, které vracejí klíče a hodnoty jsou indexovány, umožňující efektivní indexovaného načítání.|Žádné indexované načítání.|  
|Načítání je O (log `n`).|Načítání je O (log `n`).|  
|Vkládání a odstranění jsou obecně O (`n`), nicméně vložení je O (log `n`) pro data, která se již nacházejí v pořadí, řazení, tak, aby každý prvek přidán na konec seznamu. (Předpokladem je, že změna velikosti se nevyžaduje.)|Vkládání a odstranění jsou O (log `n`).|  
|Vyžaduje méně paměti než <xref:System.Collections.Generic.SortedDictionary%602>.|Větší spotřebu paměti než <xref:System.Collections.SortedList> neobecná třída a <xref:System.Collections.Generic.SortedList%602> obecnou třídu.|  
  
 Seřazené seznamy nebo slovníky, které musí být přístupné z více vláken současně, můžete přidat logiku řazení na třídu, která je odvozena z <xref:System.Collections.Concurrent.ConcurrentDictionary%602>.  
  
> [!NOTE]
>  Pro hodnoty, které obsahují vlastní klíče (například záznamy zaměstnanců, které obsahují číslo ID zaměstnance), můžete vytvořit kolekci s klíčem, který má některé vlastnosti seznamu a některé vlastnosti slovník odvozením z <xref:System.Collections.ObjectModel.KeyedCollection%602> obecné Třída.  
  
 Od verze rozhraní .NET Framework 4 <xref:System.Collections.Generic.SortedSet%601> třída poskytuje svým vyrovnávání stromové struktury, která data udržuje v seřazeném pořadí po vložení, odstranění a vyhledávání. Tato třída a <xref:System.Collections.Generic.HashSet%601> implementaci třídy <xref:System.Collections.Generic.ISet%601> rozhraní.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Collections.IDictionary?displayProperty=nameWithType>
- <xref:System.Collections.Generic.IDictionary%602?displayProperty=nameWithType>
- <xref:System.Collections.Concurrent.ConcurrentDictionary%602>
- [Běžně používané typy kolekcí](../../../docs/standard/collections/commonly-used-collection-types.md)
