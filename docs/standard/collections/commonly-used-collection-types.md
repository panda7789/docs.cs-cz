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
ms.openlocfilehash: 47e54bb76c65dd5acc8ce1921ee385a5cb55cf95
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287988"
---
# <a name="commonly-used-collection-types"></a>Běžně používané typy kolekcí
Typy kolekcí jsou běžné variace kolekcí dat, jako jsou zatřiďovací tabulky, fronty, zásobníky, penalty, slovníky a seznamy.  
  
 Kolekce jsou založené na <xref:System.Collections.ICollection> rozhraní, <xref:System.Collections.IList> rozhraní, <xref:System.Collections.IDictionary> rozhraní nebo jejich obecných protějškech. <xref:System.Collections.IList>Rozhraní a <xref:System.Collections.IDictionary> rozhraní jsou odvozeny z <xref:System.Collections.ICollection> rozhraní; proto jsou všechny kolekce založeny na <xref:System.Collections.ICollection> rozhraní, a to buď přímo, nebo nepřímo. V kolekcích založených na <xref:System.Collections.IList> rozhraní (například <xref:System.Array> , <xref:System.Collections.ArrayList> nebo <xref:System.Collections.Generic.List%601> ) nebo přímo na <xref:System.Collections.ICollection> rozhraní (například,,, <xref:System.Collections.Queue> <xref:System.Collections.Concurrent.ConcurrentQueue%601> <xref:System.Collections.Stack> <xref:System.Collections.Concurrent.ConcurrentStack%601> nebo <xref:System.Collections.Generic.LinkedList%601> ), každý prvek obsahuje pouze hodnotu. V kolekcích založených na <xref:System.Collections.IDictionary> rozhraní (například <xref:System.Collections.Hashtable> třídy a <xref:System.Collections.SortedList> , <xref:System.Collections.Generic.Dictionary%602> <xref:System.Collections.Generic.SortedList%602> Obecné třídy) nebo <xref:System.Collections.Concurrent.ConcurrentDictionary%602> třídy, každý prvek obsahuje klíč a hodnotu.  <xref:System.Collections.ObjectModel.KeyedCollection%602>Třída je jedinečná, protože se jedná o seznam hodnot s klíči vloženými v rámci hodnot a proto se chová jako seznam a jako slovník.  
  
 Obecné kolekce představují nejlepší řešení pro silné psaní. Nicméně pokud váš jazyk nepodporuje obecné typy, <xref:System.Collections> obor názvů obsahuje základní kolekce, například <xref:System.Collections.CollectionBase> , <xref:System.Collections.ReadOnlyCollectionBase> , a <xref:System.Collections.DictionaryBase> , které jsou abstraktní základní třídy, které lze rozšířit na vytváření tříd kolekcí, které jsou silného typu. Pokud je vyžadován přístup k více vláknům s více vlákny, použijte obecné kolekce v <xref:System.Collections.Concurrent> oboru názvů.  
  
 Kolekce se mohou lišit v závislosti na tom, jak jsou prvky uloženy, jak jsou seřazeny, jak jsou prováděna hledání a jak jsou provedena porovnávání. <xref:System.Collections.Queue>Třída a <xref:System.Collections.Generic.Queue%601> Obecná třída poskytují seznamy first-in-first-out, zatímco <xref:System.Collections.Stack> Třída a <xref:System.Collections.Generic.Stack%601> Obecná třída poskytují seznamy posledních-in-first-out. <xref:System.Collections.SortedList>Třída a <xref:System.Collections.Generic.SortedList%602> Obecná třída poskytují seřazené verze <xref:System.Collections.Hashtable> třídy a <xref:System.Collections.Generic.Dictionary%602> obecnou třídu. Prvky <xref:System.Collections.Hashtable> nebo <xref:System.Collections.Generic.Dictionary%602> jsou přístupné pouze pomocí klíče elementu, ale prvky <xref:System.Collections.SortedList> nebo <xref:System.Collections.ObjectModel.KeyedCollection%602> jsou přístupné buď pomocí klíče, nebo indexem elementu. Indexy ve všech kolekcích jsou počítány od nuly, s výjimkou <xref:System.Array> , která umožňuje pole, která nejsou založená na nule.  
  
 Funkce LINQ to Objects umožňuje používat dotazy LINQ pro přístup k objektům v paměti za předpokladu, že typ objektu implementuje <xref:System.Collections.IEnumerable> nebo <xref:System.Collections.Generic.IEnumerable%601> . Dotazy LINQ poskytují společný vzor pro přístup k datům; jsou obvykle stručnější a čitelné než standardní `foreach` smyčky a poskytují možnosti filtrování, řazení a seskupování. Dotazy LINQ mohou také zlepšit výkon. Další informace naleznete v tématu [LINQ to Objects (C#)](../../csharp/programming-guide/concepts/linq/linq-to-objects.md), [LINQ to Objects (Visual Basic)](../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)a [Paralelní LINQ (PLINQ)](../parallel-programming/introduction-to-plinq.md).  
  
## <a name="related-topics"></a>Související témata  
  
|Nadpis|Popis|  
|-----------|-----------------|  
|[Kolekce a datové struktury](index.md)|Popisuje různé typy kolekcí, které jsou k dispozici v .NET Framework, včetně zásobníků, front, seznamů, polí a slovníků.|  
|[Typy kolekce Hashtable a Dictionary](hashtable-and-dictionary-collection-types.md)|Popisuje funkce obecných a neobecných typů slovníků založených na hodnotách hash.|  
|[Typy seřazených kolekcí](sorted-collection-types.md)|Popisuje třídy, které poskytují funkce řazení pro seznamy a sady.|  
|[Obecné typy](../generics/index.md)|Popisuje funkci obecných typů, včetně obecných kolekcí, delegátů a rozhraní poskytovaných .NET Framework. Obsahuje odkazy na dokumentaci k funkcím pro C#, Visual Basic a Visual C++ a na podpůrné technologie, jako je reflexe.|  
  
## <a name="reference"></a>Reference  
 <xref:System.Collections?displayProperty=nameWithType>  
  
 <xref:System.Collections.Generic?displayProperty=nameWithType>  
  
 <xref:System.Collections.ICollection?displayProperty=nameWithType>  
  
 <xref:System.Collections.Generic.ICollection%601?displayProperty=nameWithType>  
  
 <xref:System.Collections.IList?displayProperty=nameWithType>  
  
 <xref:System.Collections.Generic.IList%601?displayProperty=nameWithType>  
  
 <xref:System.Collections.IDictionary?displayProperty=nameWithType>  
  
 <xref:System.Collections.Generic.IDictionary%602?displayProperty=nameWithType>
