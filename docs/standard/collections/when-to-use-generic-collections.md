---
title: Kdy použít generické kolekce
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- collections [.NET Framework], generic
- generic collections [.NET Framework]
ms.assetid: e7b868b1-11fe-4ac5-bed3-de68aca47739
ms.openlocfilehash: 131787c30e5249111f86f2793981e2b75e8f3862
ms.sourcegitcommit: 961ec21c22d2f1d55c9cc8a7edf2ade1d1fd92e3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2020
ms.locfileid: "80588533"
---
# <a name="when-to-use-generic-collections"></a>Kdy použít generické kolekce
Obecně se doporučuje používat obecné kolekce, protože získáte okamžitou výhodu bezpečnosti typů, aniž byste museli odvodit ze základního typu kolekce a implementovat členy specifické pro typ. Obecné typy kolekce také obecně provádět lépe než odpovídající typy neobecných kolekcí (a lepší než typy, které jsou odvozeny z neobecných typů základní kolekce) při kolekce prvky jsou typy hodnot, protože s obecnými typy není nutné zabalení prvků.  
  
 Pro programy, které cílí na rozhraní .NET Framework 4 <xref:System.Collections.Concurrent> nebo novější, byste měli použít obecné třídy kolekce v oboru názvů, když může současně přidávat nebo odebírat položky z kolekce více vláken.  
  
 Následující obecné typy odpovídají existujícím typům kolekce:  
  
- <xref:System.Collections.Generic.List%601>je obecná třída, která <xref:System.Collections.ArrayList>odpovídá .  
  
- <xref:System.Collections.Generic.Dictionary%602>a <xref:System.Collections.Concurrent.ConcurrentDictionary%602> jsou obecné třídy, které odpovídají <xref:System.Collections.Hashtable>.  
  
- <xref:System.Collections.ObjectModel.Collection%601>je obecná třída, která <xref:System.Collections.CollectionBase>odpovídá . <xref:System.Collections.ObjectModel.Collection%601>lze použít jako základní třídu, ale na rozdíl od <xref:System.Collections.CollectionBase>, není abstraktní. Díky tomu je mnohem jednodušší použití.  
  
- <xref:System.Collections.ObjectModel.ReadOnlyCollection%601>je obecná třída, která <xref:System.Collections.ReadOnlyCollectionBase>odpovídá . <xref:System.Collections.ObjectModel.ReadOnlyCollection%601>není abstraktní a má konstruktor, který usnadňuje vystavit <xref:System.Collections.Generic.List%601> existující jako kolekci jen pro čtení.  
  
- <xref:System.Collections.Generic.Queue%601>Třídy <xref:System.Collections.Concurrent.ConcurrentQueue%601> <xref:System.Collections.Generic.Stack%601>, <xref:System.Collections.Concurrent.ConcurrentStack%601>, <xref:System.Collections.Generic.SortedList%602> , a obecné odpovídají příslušným neobecným třídám se stejnými názvy.  
  
## <a name="additional-types"></a>Další typy  
 Několik typů obecné kolekce nemají neobecné protějšky. Patří mezi ně následující:  
  
- <xref:System.Collections.Generic.LinkedList%601>je propojený seznam pro obecné účely, který poskytuje operace vkládání a odebírání O(1).  
  
- <xref:System.Collections.Generic.SortedDictionary%602>je seřazený slovník `n`s operacemi vkládání a načítání O(log), <xref:System.Collections.Generic.SortedList%602>což z něj činí užitečnou alternativu k .  
  
- <xref:System.Collections.ObjectModel.KeyedCollection%602>je hybrid mezi seznam a slovník, který poskytuje způsob, jak ukládat objekty, které obsahují vlastní klíče.  
  
- <xref:System.Collections.Concurrent.BlockingCollection%601>implementuje třídu kolekce s funkcí ohraničování a blokování.  
  
- <xref:System.Collections.Concurrent.ConcurrentBag%601>umožňuje rychlé vkládání a odstraňování neuspořádaných prvků.  
  
## <a name="linq-to-objects"></a>LINQ na objekty  
 Funkce LINQ to Objects umožňuje používat dotazy LINQ pro přístup k objektům v <xref:System.Collections.IEnumerable?displayProperty=nameWithType> paměti, pokud typ objektu implementuje rozhraní nebo. <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> Linq dotazy poskytují společný vzor pro přístup k datům; jsou obvykle stručnější a čitelnější `foreach` než standardní smyčky; a poskytují možnosti filtrování, řazení a seskupování. Linq dotazy můžete také zlepšit výkon. Další informace naleznete v [tématech LINQ to Objects (C#)](../../csharp/programming-guide/concepts/linq/linq-to-objects.md), [LINQ to Objects (Visual Basic)](../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)a [Parallel LINQ (PLINQ).](../../../docs/standard/parallel-programming/introduction-to-plinq.md)  
  
## <a name="additional-functionality"></a>Další funkce  
 Některé obecné typy mají funkce, které nejsou nalezeny v neobecných typech kolekcí. Například <xref:System.Collections.Generic.List%601> třída, která odpovídá neobecné <xref:System.Collections.ArrayList> třídě, má řadu metod, které přijímají obecné <xref:System.Predicate%601> delegáty, jako je například delegát, který umožňuje zadat metody pro vyhledávání v seznamu, <xref:System.Action%601> delegát, který představuje metody, které působí na každý prvek seznamu, a <xref:System.Converter%602> delegát, který umožňuje definovat převody mezi typy.  
  
 Třída <xref:System.Collections.Generic.List%601> umožňuje zadat vlastní <xref:System.Collections.Generic.IComparer%601> implementace obecného rozhraní pro řazení a prohledávání seznamu. A <xref:System.Collections.Generic.SortedDictionary%602> <xref:System.Collections.Generic.SortedList%602> třídy mají také tuto schopnost. Kromě toho tyto třídy umožňují určit porovnávání při vytvoření kolekce. Podobným způsobem <xref:System.Collections.Generic.Dictionary%602> a <xref:System.Collections.ObjectModel.KeyedCollection%602> třídy umožňují zadat vlastní rovnosti porovnávání.  
  
## <a name="see-also"></a>Viz také

- [Kolekce a datové struktury](../../../docs/standard/collections/index.md)
- [Běžně používané typy kolekcí](../../../docs/standard/collections/commonly-used-collection-types.md)
- [Obecné typy](../../../docs/standard/generics/index.md)
