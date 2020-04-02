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
ms.openlocfilehash: dc590d712a49ea27fcc61181e0b8c9b3349e74e5
ms.sourcegitcommit: 961ec21c22d2f1d55c9cc8a7edf2ade1d1fd92e3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2020
ms.locfileid: "80588342"
---
# <a name="commonly-used-collection-types"></a>Běžně používané typy kolekcí
Typy kolekcí jsou běžné varianty kolekcí dat, jako jsou tabulky hash, fronty, zásobníky, tašky, slovníky a seznamy.  
  
 Kolekce jsou založeny <xref:System.Collections.ICollection> na <xref:System.Collections.IList> rozhraní, <xref:System.Collections.IDictionary> rozhraní, rozhraní nebo jejich obecné protějšky. Rozhraní <xref:System.Collections.IList> a <xref:System.Collections.IDictionary> rozhraní jsou odvozeny <xref:System.Collections.ICollection> z rozhraní; proto všechny kolekce jsou založeny na <xref:System.Collections.ICollection> rozhraní přímo nebo nepřímo. V kolekcích založených <xref:System.Collections.IList> na rozhraní <xref:System.Array> <xref:System.Collections.ArrayList>(například , , <xref:System.Collections.Generic.List%601>nebo ) <xref:System.Collections.Concurrent.ConcurrentQueue%601>nebo <xref:System.Collections.Stack> <xref:System.Collections.Concurrent.ConcurrentStack%601> přímo <xref:System.Collections.Generic.LinkedList%601>na <xref:System.Collections.ICollection> rozhraní (například <xref:System.Collections.Queue>, , nebo ), každý prvek obsahuje pouze hodnotu. V kolekcích založených <xref:System.Collections.IDictionary> na rozhraní <xref:System.Collections.Hashtable> (například <xref:System.Collections.SortedList> a <xref:System.Collections.Generic.SortedList%602> třídy, <xref:System.Collections.Concurrent.ConcurrentDictionary%602> <xref:System.Collections.Generic.Dictionary%602> a obecné třídy) nebo třídy, každý prvek obsahuje klíč a hodnotu.  Třída <xref:System.Collections.ObjectModel.KeyedCollection%602> je jedinečná, protože se jedná o seznam hodnot s klíči vloženými do hodnot, a proto se chová jako seznam a jako slovník.  
  
 Obecné kolekce jsou nejlepším řešením pro silné psaní. Pokud však váš jazyk nepodporuje <xref:System.Collections> obecné typy, obor názvů <xref:System.Collections.CollectionBase>obsahuje <xref:System.Collections.ReadOnlyCollectionBase>základní <xref:System.Collections.DictionaryBase>kolekce, například , , a , které jsou abstraktní základní třídy, které lze rozšířit k vytvoření tříd kolekce, které jsou silně zadali. Pokud je vyžadován efektivní přístup k kolekci s více <xref:System.Collections.Concurrent> vlákny, použijte obecné kolekce v oboru názvů.  
  
 Kolekce se mohou lišit v závislosti na způsobu uložení prvků, způsobu jejich řazení, způsobu provádění vyhledávání a způsobu porovnání. Třída <xref:System.Collections.Queue> a <xref:System.Collections.Generic.Queue%601> obecná třída poskytují seznamy first-in-first-out, zatímco <xref:System.Collections.Stack> třída a <xref:System.Collections.Generic.Stack%601> obecná třída poskytují seznamy last-in-first-out. Třída <xref:System.Collections.SortedList> a <xref:System.Collections.Generic.SortedList%602> obecná třída poskytují seřazené verze <xref:System.Collections.Hashtable> třídy a <xref:System.Collections.Generic.Dictionary%602> obecné třídy. Prvky <xref:System.Collections.Hashtable> nebo nebo <xref:System.Collections.Generic.Dictionary%602> jsou přístupné pouze klíč prvku, ale prvky <xref:System.Collections.SortedList> <xref:System.Collections.ObjectModel.KeyedCollection%602> nebo nebo jsou přístupné buď klíč nebo index prvku. Indexy ve všech kolekcích jsou založeny na nule, s výjimkou <xref:System.Array>, který umožňuje pole, která nejsou založeny na nule.  
  
 Funkce LINQ to Objects umožňuje používat dotazy LINQ pro přístup k objektům v <xref:System.Collections.IEnumerable> <xref:System.Collections.Generic.IEnumerable%601>paměti, pokud typ objektu implementuje nebo . Linq dotazy poskytují společný vzor pro přístup k datům; jsou obvykle stručnější a čitelnější `foreach` než standardní smyčky; a poskytují možnosti filtrování, řazení a seskupování. Linq dotazy můžete také zlepšit výkon. Další informace naleznete v [tématech LINQ to Objects (C#)](../../csharp/programming-guide/concepts/linq/linq-to-objects.md), [LINQ to Objects (Visual Basic)](../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)a [Parallel LINQ (PLINQ).](../../../docs/standard/parallel-programming/introduction-to-plinq.md)  
  
## <a name="related-topics"></a>Související témata  
  
|Nadpis|Popis|  
|-----------|-----------------|  
|[Kolekce a datové struktury](../../../docs/standard/collections/index.md)|Popisuje různé typy kolekcí, které jsou k dispozici v rozhraní .NET Framework, včetně zásobníků, front, seznamů, polí a slovníků.|  
|[Typy kolekce Hashtable a Dictionary](../../../docs/standard/collections/hashtable-and-dictionary-collection-types.md)|Popisuje funkce obecných a neobecných typů slovníků založených na hash.|  
|[Typy řazených kolekcí](../../../docs/standard/collections/sorted-collection-types.md)|Popisuje třídy, které poskytují funkce řazení pro seznamy a sady.|  
|[Obecné typy](../../../docs/standard/generics/index.md)|Popisuje funkci obecných typů, včetně obecných kolekcí, delegátů a rozhraní poskytovaných rozhraním .NET Framework. Obsahuje odkazy na dokumentaci k funkcím pro c#, visual basic a visual c++ a na podpůrné technologie, jako je reflexe.|  
  
## <a name="reference"></a>Odkaz  
 <xref:System.Collections?displayProperty=nameWithType>  
  
 <xref:System.Collections.Generic?displayProperty=nameWithType>  
  
 <xref:System.Collections.ICollection?displayProperty=nameWithType>  
  
 <xref:System.Collections.Generic.ICollection%601?displayProperty=nameWithType>  
  
 <xref:System.Collections.IList?displayProperty=nameWithType>  
  
 <xref:System.Collections.Generic.IList%601?displayProperty=nameWithType>  
  
 <xref:System.Collections.IDictionary?displayProperty=nameWithType>  
  
 <xref:System.Collections.Generic.IDictionary%602?displayProperty=nameWithType>
