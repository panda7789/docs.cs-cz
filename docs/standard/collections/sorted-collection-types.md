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
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75711334"
---
# <a name="sorted-collection-types"></a>Typy řazených kolekcí
Třída <xref:System.Collections.SortedList?displayProperty=nameWithType>, <xref:System.Collections.Generic.SortedList%602?displayProperty=nameWithType> obecná třída a <xref:System.Collections.Generic.SortedDictionary%602?displayProperty=nameWithType> obecná třída jsou podobné třídě <xref:System.Collections.Hashtable> a <xref:System.Collections.Generic.Dictionary%602> obecné třídě v tom, že implementují rozhraní <xref:System.Collections.IDictionary>, ale udržují jejich prvky v pořadí řazení podle klíče a nemají k dispozici vkládání a načítání hodnot hashových tabulek. Tři třídy mají několik běžných funkcí:  
  
- Všechny tři třídy implementují rozhraní <xref:System.Collections.IDictionary?displayProperty=nameWithType>. Tyto dvě obecné třídy také implementují obecné rozhraní <xref:System.Collections.Generic.IDictionary%602?displayProperty=nameWithType>.  
  
- Každý prvek je dvojice klíč/hodnota pro účely výčtu.  
  
    > [!NOTE]
    > Neobecná <xref:System.Collections.SortedList> třída vrací <xref:System.Collections.DictionaryEntry> objekty při výčtu, i když dva obecné typy vrátí <xref:System.Collections.Generic.KeyValuePair%602> objektů.  
  
- Prvky jsou seřazeny podle implementace <xref:System.Collections.IComparer?displayProperty=nameWithType> (pro neobecné <xref:System.Collections.SortedList>) nebo implementace <xref:System.Collections.Generic.IComparer%601?displayProperty=nameWithType> (pro dvě obecné třídy).  
  
- Každá třída poskytuje vlastnosti, které vracejí kolekce obsahující pouze klíče, nebo pouze hodnoty.  
  
 V následující tabulce je uveden seznam rozdílů mezi dvěma seřazenými třídami seznamu a třídou <xref:System.Collections.Generic.SortedDictionary%602>.  
  
|<xref:System.Collections.SortedList> neobecnou třídu a <xref:System.Collections.Generic.SortedList%602>ou obecnou třídu|<xref:System.Collections.Generic.SortedDictionary%602> obecná třída|  
|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|Vlastnosti, které vracejí klíče a hodnoty jsou indexované, což umožňuje efektivní indexované načítání.|Žádné indexované načtení.|  
|Načtení je O (log `n`).|Načtení je O (log `n`).|  
|Vložení a odebrání jsou obecně O (`n`); vložení však je O (log `n`) pro data, která jsou již v pořadí řazení, aby byl každý prvek přidán na konec seznamu. (Předpokládá se, že změna velikosti není nutná.)|Vkládání a odebírání je O (log `n`).|  
|Používá méně paměti než <xref:System.Collections.Generic.SortedDictionary%602>.|Používá více paměti než <xref:System.Collections.SortedList> neobecnou třídu a <xref:System.Collections.Generic.SortedList%602>ou obecnou třídu.|  
  
 Pro seřazené seznamy nebo slovníky, které musí být přístupné souběžně z více vláken, můžete přidat logiku řazení ke třídě, která je odvozena z <xref:System.Collections.Concurrent.ConcurrentDictionary%602>.  
  
> [!NOTE]
> Pro hodnoty, které obsahují vlastní klíče (například záznamy zaměstnanců obsahující identifikační číslo zaměstnance), můžete vytvořit kolekci s klíčem, která obsahuje některé charakteristiky seznamu a některé charakteristiky slovníku odvozenou z <xref:System.Collections.ObjectModel.KeyedCollection%602> obecné třídy.  
  
 Počínaje .NET Framework 4 poskytuje <xref:System.Collections.Generic.SortedSet%601> třída samostatně vyvážení stromu, který uchovává data v seřazeném pořadí po vložení, odstranění a hledání. Tato třída a třída <xref:System.Collections.Generic.HashSet%601> implementuje rozhraní <xref:System.Collections.Generic.ISet%601>.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Collections.IDictionary?displayProperty=nameWithType>
- <xref:System.Collections.Generic.IDictionary%602?displayProperty=nameWithType>
- <xref:System.Collections.Concurrent.ConcurrentDictionary%602>
- [Běžně používané typy kolekcí](../../../docs/standard/collections/commonly-used-collection-types.md)
