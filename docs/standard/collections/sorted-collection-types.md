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
ms.openlocfilehash: c49b3fcd5b50cc5b48497dcf97862e80b066ab46
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69957874"
---
# <a name="sorted-collection-types"></a>Typy řazených kolekcí
<xref:System.Collections.Hashtable> <xref:System.Collections.IDictionary> Třída, Obecnátřída<xref:System.Collections.Generic.Dictionary%602> a obecná třída jsou podobné třídě a obecné třídě v tom, že implementují rozhraní, ale udržují jejich <xref:System.Collections.Generic.SortedDictionary%602?displayProperty=nameWithType> <xref:System.Collections.SortedList?displayProperty=nameWithType> <xref:System.Collections.Generic.SortedList%602?displayProperty=nameWithType> prvky v pořadí řazení podle klíče a nemají pro vkládání a čtení zatřiďovacích tabulek charakteristickou hodnotu O (1). Tři třídy mají několik běžných funkcí:  
  
- Všechny tři třídy implementují <xref:System.Collections.IDictionary?displayProperty=nameWithType> rozhraní. Tyto dvě obecné třídy také implementují <xref:System.Collections.Generic.IDictionary%602?displayProperty=nameWithType> obecné rozhraní.  
  
- Každý prvek je dvojice klíč/hodnota pro účely výčtu.  
  
    > [!NOTE]
    > Neobecná <xref:System.Collections.SortedList> třída vrací <xref:System.Collections.DictionaryEntry> objekty při výčtu, i když dva obecné typy vracejí <xref:System.Collections.Generic.KeyValuePair%602> objekty.  
  
- Prvky jsou seřazeny podle <xref:System.Collections.IComparer?displayProperty=nameWithType> implementace (pro neobecné <xref:System.Collections.SortedList>) nebo <xref:System.Collections.Generic.IComparer%601?displayProperty=nameWithType> implementace (pro dvě obecné třídy).  
  
- Každá třída poskytuje vlastnosti, které vracejí kolekce obsahující pouze klíče, nebo pouze hodnoty.  
  
 V následující tabulce je uveden seznam rozdílů mezi dvěma seřazenými třídami seznamu a <xref:System.Collections.Generic.SortedDictionary%602> třídou.  
  
|<xref:System.Collections.SortedList>neobecná třída a <xref:System.Collections.Generic.SortedList%602> obecná třída|<xref:System.Collections.Generic.SortedDictionary%602>Obecná třída|  
|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|Vlastnosti, které vracejí klíče a hodnoty jsou indexované, což umožňuje efektivní indexované načítání.|Žádné indexované načtení.|  
|Načítání je O (protokol `n`).|Načítání je O (protokol `n`).|  
|Vložení a odebrání jsou obecně O (`n`). vložení však je o (log `n`) pro data, která jsou již v pořadí řazení, aby byl každý prvek přidán na konec seznamu. (Předpokládá se, že změna velikosti není nutná.)|Vkládání a odebírání se používá v ( `n`protokol).|  
|Používá méně paměti než <xref:System.Collections.Generic.SortedDictionary%602>.|Používá více paměti než <xref:System.Collections.SortedList> neobecnou třídu <xref:System.Collections.Generic.SortedList%602> a obecnou třídu.|  
  
 Pro seřazené seznamy nebo slovníky, které musí být přístupné souběžně z více vláken, můžete přidat logiku řazení ke třídě, která je odvozena <xref:System.Collections.Concurrent.ConcurrentDictionary%602>z.  
  
> [!NOTE]
> Pro hodnoty, které obsahují vlastní klíče (například záznamy zaměstnanců obsahující identifikační číslo zaměstnance), můžete vytvořit kolekci s klíčem, která obsahuje některé charakteristiky seznamu a některé charakteristiky slovníku, a to odvozením z <xref:System.Collections.ObjectModel.KeyedCollection%602> obecného Deník.  
  
 Počínaje .NET Framework 4 <xref:System.Collections.Generic.SortedSet%601> poskytuje třída samostatně vyvážení stromu, který uchovává data v seřazeném pořadí po vložení, odstranění a hledání. Tato třída a <xref:System.Collections.Generic.HashSet%601> třída <xref:System.Collections.Generic.ISet%601> implementuje rozhraní.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Collections.IDictionary?displayProperty=nameWithType>
- <xref:System.Collections.Generic.IDictionary%602?displayProperty=nameWithType>
- <xref:System.Collections.Concurrent.ConcurrentDictionary%602>
- [Běžně používané typy kolekcí](../../../docs/standard/collections/commonly-used-collection-types.md)
