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
ms.openlocfilehash: 31b40167be4f2760eb7c88155e1733266e34d11d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33569818"
---
# <a name="sorted-collection-types"></a>Typy řazených kolekcí
<xref:System.Collections.SortedList?displayProperty=nameWithType> Třídy, <xref:System.Collections.Generic.SortedList%602?displayProperty=nameWithType> – obecná třída a <xref:System.Collections.Generic.SortedDictionary%602?displayProperty=nameWithType> obecné třídy jsou podobné <xref:System.Collections.Hashtable> – třída a <xref:System.Collections.Generic.Dictionary%602> obecné třídy v tom, že implementují <xref:System.Collections.IDictionary> rozhraní, ale zachovávají jejich elementy v řazení pořadí pomocí klíče a nemají o(1), která vložení a načtení charakteristik zatřiďovacích tabulkách. Tři třídy mají společnou několik funkcí:  
  
-   Všechny tři třídy implementují <xref:System.Collections.IDictionary?displayProperty=nameWithType> rozhraní. Dvě obecné třídy také implementovat <xref:System.Collections.Generic.IDictionary%602?displayProperty=nameWithType> obecné rozhraní.  
  
-   Každý prvek je dvojice klíč/hodnota pro účely výčtu.  
  
    > [!NOTE]
    >  Neobecná <xref:System.Collections.SortedList> vrací <xref:System.Collections.DictionaryEntry> objekty při výčtu, i když dva obecné typy vracejí <xref:System.Collections.Generic.KeyValuePair%602> objekty.  
  
-   Elementy jsou seřazené podle <xref:System.Collections.IComparer?displayProperty=nameWithType> implementace (pro neobecný <xref:System.Collections.SortedList>) nebo <xref:System.Collections.Generic.IComparer%601?displayProperty=nameWithType> implementace (pro dvě obecné třídy).  
  
-   Každá třída poskytuje vlastnosti, které vracejí kolekce obsahující pouze klíče nebo hodnoty.  
  
 Následující tabulka uvádí některé rozdíly mezi dvěma třídami seřazený seznam a <xref:System.Collections.Generic.SortedDictionary%602> třídy.  
  
|<xref:System.Collections.SortedList> Neobecná třída a <xref:System.Collections.Generic.SortedList%602> – obecná třída|<xref:System.Collections.Generic.SortedDictionary%602> – Obecná třída|  
|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|Jsou indexované vlastnosti, které vracejí klíče a hodnoty, umožňuje efektivní indexované načtení.|Neindexované načítání.|  
|Načítání je O (protokolu `n`).|Načítání je O (protokolu `n`).|  
|Vložení a odebrání jsou obecně O (`n`), nicméně vložení je O (protokolu `n`) pro data, která jsou již v pořadí, řazení, aby každý prvek přidán na konec seznamu. (Předpokladem je, že není požadována změna velikosti.)|Vložení a odebrání jsou O (protokolu `n`).|  
|Vyžaduje méně paměti než <xref:System.Collections.Generic.SortedDictionary%602>.|Větší spotřebu paměti než <xref:System.Collections.SortedList> neobecné třídy a <xref:System.Collections.Generic.SortedList%602> – obecná třída.|  
  
 Seřazené seznamy nebo slovníky, které musí být přístupné z více vláken současně, můžete přidat logiku řazení na třídu, která je odvozena z <xref:System.Collections.Concurrent.ConcurrentDictionary%602>.  
  
> [!NOTE]
>  Hodnoty, které obsahují vlastní klíče (například záznamy zaměstnanců, které obsahují identifikační číslo zaměstnance), můžete vytvořit kolekci s klíčem, která má některé vlastnosti seznamu a některé vlastnosti slovníku odvozené z <xref:System.Collections.ObjectModel.KeyedCollection%602> obecné Třída.  
  
 Od verze [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], <xref:System.Collections.Generic.SortedSet%601> třída poskytuje samoobslužné vyrovnávání stromové struktury, která udržuje data seřazená po vložení, odstranění a vyhledávání. Tato třída a <xref:System.Collections.Generic.HashSet%601> implementaci třídy <xref:System.Collections.Generic.ISet%601> rozhraní.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Collections.IDictionary?displayProperty=nameWithType>  
 <xref:System.Collections.Generic.IDictionary%602?displayProperty=nameWithType>  
 <xref:System.Collections.Concurrent.ConcurrentDictionary%602>  
 [Běžně používané typy kolekcí](../../../docs/standard/collections/commonly-used-collection-types.md)
