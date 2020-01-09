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
ms.openlocfilehash: 1004a2f9a0594d9150d147dec1e16b56205e0d13
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75711399"
---
# <a name="commonly-used-collection-types"></a>Běžně používané typy kolekcí
Typy kolekcí jsou běžné variace kolekcí dat, jako jsou zatřiďovací tabulky, fronty, zásobníky, penalty, slovníky a seznamy.  
  
 Kolekce jsou založené na rozhraní <xref:System.Collections.ICollection>, rozhraní <xref:System.Collections.IList>, rozhraní <xref:System.Collections.IDictionary> nebo jejich obecné protějšky. Rozhraní <xref:System.Collections.IList> a rozhraní <xref:System.Collections.IDictionary> jsou odvozeny z rozhraní <xref:System.Collections.ICollection>; Proto jsou všechny kolekce založeny na rozhraní <xref:System.Collections.ICollection>, a to buď přímo, nebo nepřímo. V kolekcích založených na rozhraní <xref:System.Collections.IList> (například <xref:System.Array>, <xref:System.Collections.ArrayList>nebo <xref:System.Collections.Generic.List%601>) nebo přímo na <xref:System.Collections.ICollection> rozhraní (například <xref:System.Collections.Queue>, <xref:System.Collections.Concurrent.ConcurrentQueue%601>, <xref:System.Collections.Stack>, <xref:System.Collections.Concurrent.ConcurrentStack%601> nebo <xref:System.Collections.Generic.LinkedList%601>), každý prvek obsahuje pouze hodnotu. V kolekcích založených na rozhraní <xref:System.Collections.IDictionary> (například <xref:System.Collections.Hashtable> a <xref:System.Collections.SortedList> třídy, obecné třídy <xref:System.Collections.Generic.Dictionary%602> a <xref:System.Collections.Generic.SortedList%602>, nebo třídy <xref:System.Collections.Concurrent.ConcurrentDictionary%602>, každý prvek obsahuje klíč a hodnotu.  Třída <xref:System.Collections.ObjectModel.KeyedCollection%602> je jedinečná, protože se jedná o seznam hodnot s klíči vloženými v rámci hodnot a proto se chová jako seznam a jako slovník.  
  
 Obecné kolekce představují nejlepší řešení pro silné psaní. Nicméně pokud váš jazyk nepodporuje obecné typy, obor názvů <xref:System.Collections> zahrnuje základní kolekce, například <xref:System.Collections.CollectionBase>, <xref:System.Collections.ReadOnlyCollectionBase>a <xref:System.Collections.DictionaryBase>, které jsou abstraktní základní třídy, které lze rozšířit na vytváření tříd kolekcí, které jsou silného typu. Pokud je vyžadován přístup k více vláknům s více vlákny, použijte obecné kolekce v oboru názvů <xref:System.Collections.Concurrent>.  
  
 Kolekce se mohou lišit v závislosti na tom, jak jsou prvky uloženy, jak jsou seřazeny, jak jsou prováděna hledání a jak jsou provedena porovnávání. Třída <xref:System.Collections.Queue> a <xref:System.Collections.Generic.Queue%601> obecná třída poskytují seznamy first-in-first-out, zatímco třída <xref:System.Collections.Stack> a obecná třída <xref:System.Collections.Generic.Stack%601> poskytuje seznamy pro poslední vytvoření v prvním poli. Třída <xref:System.Collections.SortedList> a <xref:System.Collections.Generic.SortedList%602> obecná třída poskytují seřazené verze třídy <xref:System.Collections.Hashtable> a obecné třídy <xref:System.Collections.Generic.Dictionary%602>. Prvky <xref:System.Collections.Hashtable> nebo <xref:System.Collections.Generic.Dictionary%602> jsou přístupné pouze pomocí klíče elementu, ale prvky <xref:System.Collections.SortedList> nebo <xref:System.Collections.ObjectModel.KeyedCollection%602> jsou přístupné buď pomocí klíče, nebo indexu elementu. Indexy ve všech kolekcích jsou založené na nule, s výjimkou <xref:System.Array>, což umožňuje pole, která nejsou založená na nule.  
  
 Funkce LINQ to Objects umožňuje používat dotazy LINQ pro přístup k objektům v paměti, pokud typ objektu implementuje <xref:System.Collections.IEnumerable> nebo <xref:System.Collections.Generic.IEnumerable%601>. Dotazy LINQ poskytují společný vzor pro přístup k datům; jsou obvykle stručnější a čitelné než standardní `foreach` smyčky; a poskytují funkce pro filtrování, řazení a seskupování. Dotazy LINQ mohou také zlepšit výkon. Další informace naleznete v tématu [LINQ to Objects (C#)](../../csharp/programming-guide/concepts/linq/linq-to-objects.md), [LINQ to Objects (Visual Basic)](../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)a [Paralelní LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md).  
  
## <a name="related-topics"></a>Související témata  
  
|Název|Popis|  
|-----------|-----------------|  
|[Kolekce a datové struktury](../../../docs/standard/collections/index.md)|Popisuje různé typy kolekcí, které jsou k dispozici v .NET Framework, včetně zásobníků, front, seznamů, polí a slovníků.|  
|[Typy kolekce Hashtable a Dictionary](../../../docs/standard/collections/hashtable-and-dictionary-collection-types.md)|Popisuje funkce obecných a neobecných typů slovníků založených na hodnotách hash.|  
|[Typy řazených kolekcí](../../../docs/standard/collections/sorted-collection-types.md)|Popisuje třídy, které poskytují funkce řazení pro seznamy a sady.|  
|[Obecné typy](../../../docs/standard/generics/index.md)|Popisuje funkci obecných typů, včetně obecných kolekcí, delegátů a rozhraní poskytovaných .NET Framework. Obsahuje odkazy na dokumentaci k funkcím pro C#, Visual Basic a C++Visual a na podpůrné technologie, jako je například reflexe.|  
  
## <a name="reference"></a>Odkaz  
 <xref:System.Collections?displayProperty=nameWithType>  
  
 <xref:System.Collections.Generic?displayProperty=nameWithType>  
  
 <xref:System.Collections.ICollection?displayProperty=nameWithType>  
  
 <xref:System.Collections.Generic.ICollection%601?displayProperty=nameWithType>  
  
 <xref:System.Collections.IList?displayProperty=nameWithType>  
  
 <xref:System.Collections.Generic.IList%601?displayProperty=nameWithType>  
  
 <xref:System.Collections.IDictionary?displayProperty=nameWithType>  
  
 <xref:System.Collections.Generic.IDictionary%602?displayProperty=nameWithType>
