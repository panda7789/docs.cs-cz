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
ms.openlocfilehash: adabda4801abc7a11a9b22181701eb233b35a251
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "75711334"
---
# <a name="sorted-collection-types"></a>Typy řazených kolekcí
Třída, <xref:System.Collections.SortedList?displayProperty=nameWithType> <xref:System.Collections.Generic.SortedList%602?displayProperty=nameWithType> obecná třída a <xref:System.Collections.Generic.SortedDictionary%602?displayProperty=nameWithType> obecná třída jsou <xref:System.Collections.Hashtable> podobné třídě <xref:System.Collections.Generic.Dictionary%602> a obecné třídě <xref:System.Collections.IDictionary> v tom, že implementují rozhraní, ale udržují své prvky v pořadí řazení podle klíče a nemají vkládání a načítání Charakteristika O(1 tabulky hash. Tyto tři třídy mají několik společných funkcí:  
  
- Všechny tři třídy implementovat <xref:System.Collections.IDictionary?displayProperty=nameWithType> rozhraní. Dvě obecné třídy <xref:System.Collections.Generic.IDictionary%602?displayProperty=nameWithType> také implementovat obecné rozhraní.  
  
- Každý prvek je pár klíč/hodnota pro účely výčtu.  
  
    > [!NOTE]
    > Neobecná <xref:System.Collections.SortedList> třída <xref:System.Collections.DictionaryEntry> vrátí objekty při výčtu, i <xref:System.Collections.Generic.KeyValuePair%602> když dva obecné typy vrátí objekty.  
  
- Prvky jsou seřazeny <xref:System.Collections.IComparer?displayProperty=nameWithType> podle <xref:System.Collections.SortedList>implementace <xref:System.Collections.Generic.IComparer%601?displayProperty=nameWithType> (pro neobecné) nebo implementace (pro dvě obecné třídy).  
  
- Každá třída poskytuje vlastnosti, které vracejí kolekce obsahující pouze klíče nebo pouze hodnoty.  
  
 V následující tabulce jsou uvedeny některé rozdíly mezi dvěma třídami seřazených seznamů a třídou. <xref:System.Collections.Generic.SortedDictionary%602>  
  
|<xref:System.Collections.SortedList>neobecná třída <xref:System.Collections.Generic.SortedList%602> a obecná třída|<xref:System.Collections.Generic.SortedDictionary%602>obecná třída|  
|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|Vlastnosti, které vracejí klíče a hodnoty, jsou indexovány, což umožňuje efektivní indexované načítání.|Žádné indexované načítání.|  
|Načítání je O(log). `n`|Načítání je O(log). `n`|  
|Vkládání a demontáž jsou`n`obecně O( ); však vložení je O(log) `n`pro data, která jsou již v pořadí řazení, tak, aby každý prvek je přidán na konec seznamu. (To předpokládá, že změna velikosti není vyžadována.)|Vložení a odebrání jsou O(log `n`).|  
|Používá méně paměti <xref:System.Collections.Generic.SortedDictionary%602>než .|Používá více paměti <xref:System.Collections.SortedList> než neobecná <xref:System.Collections.Generic.SortedList%602> třída a obecná třída.|  
  
 U seřazených seznamů nebo slovníků, které musí být přístupné současně z více vláken, můžete přidat logiku řazení do třídy, která je odvozena z aplikace <xref:System.Collections.Concurrent.ConcurrentDictionary%602>.  
  
> [!NOTE]
> Pro hodnoty, které obsahují vlastní klíče (například záznamy zaměstnanců, které obsahují číslo ID zaměstnance), můžete vytvořit kolekci klíčů, která má některé <xref:System.Collections.ObjectModel.KeyedCollection%602> charakteristiky seznamu a některé charakteristiky slovníku odvozením z obecné třídy.  
  
 Počínaje rozhraním .NET Framework <xref:System.Collections.Generic.SortedSet%601> 4 poskytuje třída vlastní vyvažovací strom, který udržuje data v seřazené pořadí po vložení, odstranění a vyhledávání. Tato třída <xref:System.Collections.Generic.HashSet%601> a třída <xref:System.Collections.Generic.ISet%601> implementovat rozhraní.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Collections.IDictionary?displayProperty=nameWithType>
- <xref:System.Collections.Generic.IDictionary%602?displayProperty=nameWithType>
- <xref:System.Collections.Concurrent.ConcurrentDictionary%602>
- [Běžně používané typy kolekcí](../../../docs/standard/collections/commonly-used-collection-types.md)
