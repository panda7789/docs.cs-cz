---
title: Kdy použít generické kolekce
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- collections [.NET Framework], generic
- generic collections [.NET Framework]
ms.assetid: e7b868b1-11fe-4ac5-bed3-de68aca47739
ms.openlocfilehash: 7d59259c1cab6842ef62888bf5326225394d8d44
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75711204"
---
# <a name="when-to-use-generic-collections"></a>Kdy použít generické kolekce
Obecně se doporučuje použití obecných kolekcí, protože získáte okamžitou výhodu zabezpečení typu bez nutnosti odvozovat od základní kolekce typu a implementovat členy specifické pro typ. Obecné typy kolekcí také obecně provádějí lepší, než odpovídající neobecné typy kolekcí (a lepší než typy, které jsou odvozeny z neobecné typy kolekce), pokud jsou prvky kolekce typy hodnot, protože s obecnými typy jsou prvky není nutné zakrabicit.  
  
 Pro programy, které cílí na .NET Framework 4 nebo novější, byste měli použít obecné třídy kolekce v oboru názvů <xref:System.Collections.Concurrent>, pokud více vláken může přidat nebo odebrat položky z kolekce současně.  
  
 Následující obecné typy odpovídají existujícím typům kolekcí:  
  
- <xref:System.Collections.Generic.List%601> je obecná třída, která odpovídá <xref:System.Collections.ArrayList>.  
  
- <xref:System.Collections.Generic.Dictionary%602> a <xref:System.Collections.Concurrent.ConcurrentDictionary%602> jsou obecné třídy, které odpovídají <xref:System.Collections.Hashtable>.  
  
- <xref:System.Collections.ObjectModel.Collection%601> je obecná třída, která odpovídá <xref:System.Collections.CollectionBase>. <xref:System.Collections.ObjectModel.Collection%601> lze použít jako základní třídu, ale na rozdíl od <xref:System.Collections.CollectionBase>není abstraktní. Díky tomu je to mnohem jednodušší.  
  
- <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> je obecná třída, která odpovídá <xref:System.Collections.ReadOnlyCollectionBase>. <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> není abstraktní a má konstruktor, který usnadňuje vystavení existující <xref:System.Collections.Generic.List%601> jako kolekce jen pro čtení.  
  
- Obecné třídy <xref:System.Collections.Generic.Queue%601>, <xref:System.Collections.Concurrent.ConcurrentQueue%601>, <xref:System.Collections.Generic.Stack%601>, <xref:System.Collections.Concurrent.ConcurrentStack%601>a <xref:System.Collections.Generic.SortedList%602> odpovídají příslušným neobecným třídám se stejnými názvy.  
  
## <a name="additional-types"></a>Další typy  
 Některé typy obecných kolekcí nemají neobecné protějšky. Mezi tyto typy patří:  
  
- <xref:System.Collections.Generic.LinkedList%601> je obecný propojený seznam, který poskytuje operace O vkládání a odebírání.  
  
- <xref:System.Collections.Generic.SortedDictionary%602> je setříděný slovník s operacemi vkládání a načítání v rámci (log `n`), což usnadňuje <xref:System.Collections.Generic.SortedList%602>.  
  
- <xref:System.Collections.ObjectModel.KeyedCollection%602> je hybrid mezi seznamem a slovníkem, který poskytuje způsob ukládání objektů, které obsahují vlastní klíče.  
  
- <xref:System.Collections.Concurrent.BlockingCollection%601> implementuje třídu kolekce s funkcí ohraničování a blokování.  
  
- <xref:System.Collections.Concurrent.ConcurrentBag%601> poskytuje rychlé vkládání a odebírání neuspořádaných prvků.  
  
## <a name="linq-to-objects"></a>LINQ na objekty  
 Funkce LINQ to Objects umožňuje používat dotazy LINQ pro přístup k objektům v paměti, pokud typ objektu implementuje rozhraní <xref:System.Collections.IEnumerable?displayProperty=nameWithType> nebo <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType>. Dotazy LINQ poskytují společný vzor pro přístup k datům; jsou obvykle stručnější a čitelné než standardní `foreach` smyčky; a poskytují funkce pro filtrování, řazení a seskupování. Dotazy LINQ mohou také zlepšit výkon. Další informace naleznete v tématu [LINQ to Objects (C#)](../../csharp/programming-guide/concepts/linq/linq-to-objects.md), [LINQ to Objects (Visual Basic)](../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)a [Paralelní LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md).  
  
## <a name="additional-functionality"></a>Další funkce  
 Některé obecné typy mají funkce, které se nenašly v neobecných typech kolekcí. Například třída <xref:System.Collections.Generic.List%601>, která odpovídá neobecné <xref:System.Collections.ArrayList> třídy, má řadu metod, které přijímají Obecné delegáty, jako je například delegát <xref:System.Predicate%601>, který umožňuje určit metody pro hledání v seznamu, delegáta <xref:System.Action%601>, který představuje metody, které fungují na jednotlivých prvcích seznamu, a delegáta <xref:System.Converter%602>, který umožňuje definovat převody mezi typy.  
  
 Třída <xref:System.Collections.Generic.List%601> umožňuje zadat vlastní <xref:System.Collections.Generic.IComparer%601> implementace obecného rozhraní pro řazení a hledání v seznamu. Tato funkce má také třídy <xref:System.Collections.Generic.SortedDictionary%602> a <xref:System.Collections.Generic.SortedList%602>. Kromě toho umožňují tyto třídy při vytváření kolekce určit porovnávače. Podobným způsobem umožňují třídy <xref:System.Collections.Generic.Dictionary%602> a <xref:System.Collections.ObjectModel.KeyedCollection%602> zadat vlastní porovnávače rovnosti.  
  
## <a name="see-also"></a>Viz také:

- [Kolekce a datové struktury](../../../docs/standard/collections/index.md)
- [Běžně používané typy kolekcí](../../../docs/standard/collections/commonly-used-collection-types.md)
- [Obecné typy](../../../docs/standard/generics/index.md)
