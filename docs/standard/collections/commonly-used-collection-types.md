---
title: "Běžně používané typy kolekcí"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- collections [.NET Framework], generic
- objects [.NET Framework], grouping in collections
- generics [.NET Framework], collections
- IList interface, grouping data in collections
- IDictionary interface, grouping data in collections
- grouping data in collections, generic collection types
- Collections classes
- generic collections
ms.assetid: f5d4c6a4-0d7b-4944-a9fb-3b12d9ebfd55
caps.latest.revision: "29"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: cdc4e0660c5eae0a9550cf73d273d394ed71b823
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="commonly-used-collection-types"></a>Běžně používané typy kolekcí
Typy kolekcí jsou běžné varianty kolekcí dat, jako je například hash – tabulky, fronty, zásobníky, sáčky, slovníky a seznamy.  
  
 Kolekce jsou založeny na <xref:System.Collections.ICollection> rozhraní, <xref:System.Collections.IList> rozhraní, <xref:System.Collections.IDictionary> rozhraní nebo jejich obecné protějšky. <xref:System.Collections.IList> Rozhraní a <xref:System.Collections.IDictionary> i rozhraní jsou odvozeny od <xref:System.Collections.ICollection> rozhraní; proto jsou všechny kolekce založené na <xref:System.Collections.ICollection> rozhraní přímo nebo nepřímo. V kolekcích založených na <xref:System.Collections.IList> rozhraní (například <xref:System.Array>, <xref:System.Collections.ArrayList>, nebo <xref:System.Collections.Generic.List%601>) nebo přímo na <xref:System.Collections.ICollection> rozhraní (například <xref:System.Collections.Queue>, <xref:System.Collections.Concurrent.ConcurrentQueue%601>, <xref:System.Collections.Stack>, <xref:System.Collections.Concurrent.ConcurrentStack%601> nebo <xref:System.Collections.Generic.LinkedList%601>), každý element, obsahuje pouze hodnotu. V kolekcích založených na <xref:System.Collections.IDictionary> rozhraní (například <xref:System.Collections.Hashtable> a <xref:System.Collections.SortedList> třídy, <xref:System.Collections.Generic.Dictionary%602> a <xref:System.Collections.Generic.SortedList%602> obecné třídy), nebo <xref:System.Collections.Concurrent.ConcurrentDictionary%602> třídy, každý element obsahuje klíč a hodnotu.  <xref:System.Collections.ObjectModel.KeyedCollection%602> Třída je jedinečný, protože je seznam hodnot s klíči vloženými do hodnoty, a proto se chová jako seznam a podobně jako slovník.  
  
 Obecné kolekce jsou nejlepším řešením silného typování. Ale v případě, že váš jazyk nepodporuje obecné typy, <xref:System.Collections> obor názvů obsahuje základní kolekce, jako například <xref:System.Collections.CollectionBase>, <xref:System.Collections.ReadOnlyCollectionBase>, a <xref:System.Collections.DictionaryBase>, které jsou abstraktní základní třídy, které lze rozšířit pro vytvoření kolekce tříd, které jsou silného typu. Pokud je vyžadován přístup efektivní vícevláknové kolekce, použít generické kolekce v <xref:System.Collections.Concurrent> oboru názvů.  
  
 Kolekce se mohou lišit v závislosti na tom, jak jsou uložené elementy, způsob řazení, jak se provádí vyhledávání a tvorba porovnání. <xref:System.Collections.Queue> – Třída a <xref:System.Collections.Generic.Queue%601> – obecná třída zadejte first-in-first-out seznamy při <xref:System.Collections.Stack> – třída a <xref:System.Collections.Generic.Stack%601> – obecná třída poskytují last in first out seznamy. <xref:System.Collections.SortedList> Třídy a <xref:System.Collections.Generic.SortedList%602> – obecná třída poskytují seřazené verze <xref:System.Collections.Hashtable> – třída a <xref:System.Collections.Generic.Dictionary%602> – obecná třída. Elementy <xref:System.Collections.Hashtable> nebo <xref:System.Collections.Generic.Dictionary%602> jsou přístupné jenom pro klíč elementu, ale elementy <xref:System.Collections.SortedList> nebo <xref:System.Collections.ObjectModel.KeyedCollection%602> jsou přístupné pomocí klíče nebo index elementu. Indexy ve všech kolekcích jsou od nuly, s výjimkou <xref:System.Array>, což umožňuje pole, které nejsou od nuly.  
  
 LINQ na objekty funkce umožňuje používat dotazy LINQ pro přístup k objektům v paměti, dokud typ objektu implementuje <xref:System.Collections.IEnumerable> nebo <xref:System.Collections.Generic.IEnumerable%601>. Dotazy LINQ poskytují společný vzorek pro přístup k datům; Obvykle se jedná o více stručná a čitelná než standardní `foreach` cyklu; a zadejte filtrování, řazení a seskupování schopností. Výkon lze zvýšit rovněž dotazů LINQ. Další informace najdete v tématu [LINQ na objekty](http://msdn.microsoft.com/library/73cafe73-37cf-46e7-bfa7-97c7eea7ced9) a [paralelní LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md).  
  
## <a name="related-topics"></a>Související témata  
  
|Název|Popis|  
|-----------|-----------------|  
|[Kolekce a datové struktury](../../../docs/standard/collections/index.md)|Popisuje různé typy kolekce, která je k dispozici v [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)], včetně zásobníky, fronty, seznamy, pole a slovník.|  
|[Typy kolekce Hashtable a Dictionary](../../../docs/standard/collections/hashtable-and-dictionary-collection-types.md)|Popisuje funkce pro obecné a neobecné slovník na základě hodnoty hash typů.|  
|[Typy řazených kolekcí](../../../docs/standard/collections/sorted-collection-types.md)|Popisuje třídy, které poskytují funkce řazení pro seznamy a sad.|  
|[Obecné typy](../../../docs/standard/generics/index.md)|Popisuje funkce obecných typů, včetně obecné kolekce, delegáti a rozhraní poskytované [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]. Obsahuje odkazy na dokumentaci funkcí jazyka C#, Visual Basic a Visual C++ a podpůrné technologie, jako je například reflexe.|  
  
## <a name="reference"></a>Odkaz  
 <xref:System.Collections?displayProperty=nameWithType>  
  
 <xref:System.Collections.Generic?displayProperty=nameWithType>  
  
 <xref:System.Collections.ICollection?displayProperty=nameWithType>  
  
 <xref:System.Collections.Generic.ICollection%601?displayProperty=nameWithType>  
  
 <xref:System.Collections.IList?displayProperty=nameWithType>  
  
 <xref:System.Collections.Generic.IList%601?displayProperty=nameWithType>  
  
 <xref:System.Collections.IDictionary?displayProperty=nameWithType>  
  
 <xref:System.Collections.Generic.IDictionary%602?displayProperty=nameWithType>
