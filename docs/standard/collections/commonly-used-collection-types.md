---
title: Běžně používané typy kolekcí
ms.date: 03/30/2017
ms.technology: dotnet-standard
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c21a1303cd67f5f5de42241f4d5ada929e68bf2c
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2019
ms.locfileid: "65589899"
---
# <a name="commonly-used-collection-types"></a>Běžně používané typy kolekcí
Typy kolekcí jsou obvyklých variací kolekcí dat, jako je například zatřiďovacích tabulek, front, zásobníky, kontejnery objektů a dat, slovníky a seznamy.  
  
 Kolekce jsou založeny na <xref:System.Collections.ICollection> rozhraní, <xref:System.Collections.IList> rozhraní, <xref:System.Collections.IDictionary> rozhraní nebo jejich obecné protějšky. <xref:System.Collections.IList> Rozhraní a <xref:System.Collections.IDictionary> obě rozhraní jsou odvozeny od <xref:System.Collections.ICollection> rozhraní; proto jsou všechny kolekce na základě <xref:System.Collections.ICollection> rozhraní přímo nebo nepřímo. V kolekcích založených na <xref:System.Collections.IList> rozhraní (například <xref:System.Array>, <xref:System.Collections.ArrayList>, nebo <xref:System.Collections.Generic.List%601>) nebo přímo na <xref:System.Collections.ICollection> rozhraní (například <xref:System.Collections.Queue>, <xref:System.Collections.Concurrent.ConcurrentQueue%601>, <xref:System.Collections.Stack>, <xref:System.Collections.Concurrent.ConcurrentStack%601> nebo <xref:System.Collections.Generic.LinkedList%601>), každý prvek obsahuje jednu hodnotu. V kolekcích založených na <xref:System.Collections.IDictionary> rozhraní (například <xref:System.Collections.Hashtable> a <xref:System.Collections.SortedList> třídy, <xref:System.Collections.Generic.Dictionary%602> a <xref:System.Collections.Generic.SortedList%602> obecné třídy), nebo <xref:System.Collections.Concurrent.ConcurrentDictionary%602> třídy, každý prvek obsahuje klíč a hodnotu.  <xref:System.Collections.ObjectModel.KeyedCollection%602> Třídy je jedinečný, protože je seznam hodnot pomocí klíčů vloženy hodnoty, a proto se chová jako seznam a podobně jako slovník.  
  
 Obecné kolekce jsou nejlepší řešení pro silných typů. Nicméně, pokud váš jazyk nepodporuje obecné typy, <xref:System.Collections> obor názvů obsahuje základní kolekcí, jako například <xref:System.Collections.CollectionBase>, <xref:System.Collections.ReadOnlyCollectionBase>, a <xref:System.Collections.DictionaryBase>, které jsou abstraktní základní třídy, které je možné rozšířit na vytvoření tříd kolekcí, které jsou silného typu. Pokud je vyžadován přístup efektivní vícevláknové kolekce, použijte obecné kolekce v <xref:System.Collections.Concurrent> oboru názvů.  
  
 Kolekce se může lišit v závislosti na tom, jak prvky jsou uloženy, způsob řazení, jak se provádí vyhledávání a jak porovnávání. <xref:System.Collections.Queue> Třídy a <xref:System.Collections.Generic.Queue%601> obecnou třídu najdete seznamy first-in-first-out, zatímco <xref:System.Collections.Stack> třídy a <xref:System.Collections.Generic.Stack%601> obecnou třídu seznamy last-in-first-out. <xref:System.Collections.SortedList> Třídy a <xref:System.Collections.Generic.SortedList%602> obecné třídy poskytují seřazené verze <xref:System.Collections.Hashtable> třídy a <xref:System.Collections.Generic.Dictionary%602> obecnou třídu. Elementy <xref:System.Collections.Hashtable> nebo <xref:System.Collections.Generic.Dictionary%602> jsou přístupná jenom pro klíč prvku, ale elementy <xref:System.Collections.SortedList> nebo <xref:System.Collections.ObjectModel.KeyedCollection%602> jsou k dispozici klíč nebo index prvku. Indexy ve všech kolekcích jsou počítány od nuly, s výjimkou <xref:System.Array>, což umožňuje použití polí, které nejsou od nuly.  
  
 Funkce LINQ to Objects umožňuje použít dotazy LINQ pro přístup k objektům v paměti, dokud objektový typ implementuje <xref:System.Collections.IEnumerable> nebo <xref:System.Collections.Generic.IEnumerable%601>. Dotazy LINQ poskytují společný vzor pro přístup k datům; jsou obvykle stručnější a čitelnější než standardní `foreach` smyčky a poskytují filtrování, řazení a seskupování schopností. Dotazy LINQ mohou také zvýšit výkon. Další informace najdete v tématu [LINQ to Objects (C#)](../../csharp/programming-guide/concepts/linq/linq-to-objects.md), [LINQ to Objects (Visual Basic)](../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md), a [paralelní LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md).  
  
## <a name="related-topics"></a>Související témata  
  
|Název|Popis|  
|-----------|-----------------|  
|[Kolekce a datové struktury](../../../docs/standard/collections/index.md)|Tento článek popisuje různé typy kolekce, která je k dispozici v rozhraní .NET Framework, včetně zásobníků, front, seznamů, polí a slovníky.|  
|[Typy kolekce Hashtable a Dictionary](../../../docs/standard/collections/hashtable-and-dictionary-collection-types.md)|Popisuje funkce typů obecných a neobecných hash na základě slovníku.|  
|[Typy řazených kolekcí](../../../docs/standard/collections/sorted-collection-types.md)|Popisuje třídy, které poskytují funkce řazení pro seznamy a množiny.|  
|[Obecné typy](../../../docs/standard/generics/index.md)|Popisuje funkci obecných typů, včetně obecných kolekcí, delegátů a rozhraní poskytovaných rozhraním .NET Framework. Obsahuje odkazy na dokumentaci funkcí C#, Visual Basic a Visual C++ a na podpůrné technologie, jako je například reflexe.|  
  
## <a name="reference"></a>Odkaz  
 <xref:System.Collections?displayProperty=nameWithType>  
  
 <xref:System.Collections.Generic?displayProperty=nameWithType>  
  
 <xref:System.Collections.ICollection?displayProperty=nameWithType>  
  
 <xref:System.Collections.Generic.ICollection%601?displayProperty=nameWithType>  
  
 <xref:System.Collections.IList?displayProperty=nameWithType>  
  
 <xref:System.Collections.Generic.IList%601?displayProperty=nameWithType>  
  
 <xref:System.Collections.IDictionary?displayProperty=nameWithType>  
  
 <xref:System.Collections.Generic.IDictionary%602?displayProperty=nameWithType>
