---
title: Kdy použít generické kolekce
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- collections [.NET Framework], generic
- generic collections [.NET Framework]
ms.assetid: e7b868b1-11fe-4ac5-bed3-de68aca47739
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9831212cf65e3913bae2431e4746b5def03430b6
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2018
ms.locfileid: "47084758"
---
# <a name="when-to-use-generic-collections"></a>Kdy použít generické kolekce
Použitím obecných kolekcí se obecně nedoporučuje, protože výhod získáte tak okamžitý bezpečnosti typů bez nutnosti odvozen od typu základní kolekce a implementovat typ konkrétní členy. Obecné typy kolekcí také obecně poskytují vyšší výkon než odpovídající kolekci neobecné typy (a lepší než u typů, které jsou odvozeny ze základních typů neobecných kolekcí) při elementy z kolekce jsou typy hodnot, protože u obecných typů už není potřeba pole prvků.  
  
 Pro programy, které se zaměřují [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] nebo novější, byste měli použít obecné kolekce tříd v <xref:System.Collections.Concurrent> obor názvů při více vláken může přidávat nebo odebírat položky z kolekce současně.  
  
 Následující obecné typy odpovídají typům existující kolekce:  
  
-   <xref:System.Collections.Generic.List%601> je obecná třída, která odpovídá <xref:System.Collections.ArrayList>.  
  
-   <xref:System.Collections.Generic.Dictionary%602> a <xref:System.Collections.Concurrent.ConcurrentDictionary%602> jsou obecné třídy, které odpovídají <xref:System.Collections.Hashtable>.  
  
-   <xref:System.Collections.ObjectModel.Collection%601> je obecná třída, která odpovídá <xref:System.Collections.CollectionBase>. <xref:System.Collections.ObjectModel.Collection%601> lze použít jako základní třídy, ale na rozdíl od <xref:System.Collections.CollectionBase>, není abstraktní. Díky tomu je mnohem jednodušší.  
  
-   <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> je obecná třída, která odpovídá <xref:System.Collections.ReadOnlyCollectionBase>. <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> není abstraktní a nemá konstruktor, který umožňuje snadno vystavit existující <xref:System.Collections.Generic.List%601> jako kolekce jen pro čtení.  
  
-   <xref:System.Collections.Generic.Queue%601>, <xref:System.Collections.Concurrent.ConcurrentQueue%601>, <xref:System.Collections.Generic.Stack%601>, <xref:System.Collections.Concurrent.ConcurrentStack%601>, A <xref:System.Collections.Generic.SortedList%602> obecné třídy odpovídají příslušné neobecné třídy se stejnými názvy.  
  
## <a name="additional-types"></a>Další typy  
 Několik typů obecných kolekcí protějšků, které nemají. Jsou to tyto země:  
  
-   <xref:System.Collections.Generic.LinkedList%601> je pro obecné účely propojený seznam, který poskytuje vkládání a odstranění operace O(1).  
  
-   <xref:System.Collections.Generic.SortedDictionary%602> je seřazený slovník pomocí O (log `n`) vkládání a načítání operace, které umožňuje užitečnou alternativou k <xref:System.Collections.Generic.SortedList%602>.  
  
-   <xref:System.Collections.ObjectModel.KeyedCollection%602> je hybridní mezi seznamem a slovník, který poskytuje způsob, jak ukládat objekty, které obsahují vlastní klíče.  
  
-   <xref:System.Collections.Concurrent.BlockingCollection%601> implementuje třídu kolekce s funkcí ohraničování a blokování.  
  
-   <xref:System.Collections.Concurrent.ConcurrentBag%601> poskytuje rychlé vkládání a odstranění prvků Neseřazený.  
  
## <a name="linq-to-objects"></a>LINQ na objekty  
 Funkce LINQ to Objects umožňuje použít dotazy LINQ pro přístup k objektům v paměti, dokud objektový typ implementuje <xref:System.Collections.IEnumerable?displayProperty=nameWithType> nebo <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> rozhraní. Dotazy LINQ poskytují společný vzor pro přístup k datům; jsou obvykle stručnější a čitelnější než standardní `foreach` smyčky a poskytují filtrování, řazení a seskupování schopností. Dotazy LINQ mohou také zvýšit výkon. Další informace najdete v tématu [LINQ to Objects](https://msdn.microsoft.com/library/73cafe73-37cf-46e7-bfa7-97c7eea7ced9) a [paralelní LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md).  
  
## <a name="additional-functionality"></a>Další funkce  
 Některé obecné typy mají funkce, který se nenachází v kolekci neobecné typy. Například <xref:System.Collections.Generic.List%601> třídu, která odpovídá neobecné <xref:System.Collections.ArrayList> třídu, má několik metod, které přijímají obecných delegátů, jako <xref:System.Predicate%601> delegáta, který vám umožní určit metody pro hledání v seznamu <xref:System.Action%601>delegáta, který představuje metody, které působí na každý prvek seznamu a <xref:System.Converter%602> delegáta, který umožňuje definovat převody mezi typy.  
  
 <xref:System.Collections.Generic.List%601> Třídy můžete zadat vlastní <xref:System.Collections.Generic.IComparer%601> implementace obecné rozhraní pro řazení a hledání v seznamu. <xref:System.Collections.Generic.SortedDictionary%602> a <xref:System.Collections.Generic.SortedList%602> třídy také mají tuto funkci. Kromě toho tyto třídy umožňují určit komparátory při vytvoření kolekce. Podobně <xref:System.Collections.Generic.Dictionary%602> a <xref:System.Collections.ObjectModel.KeyedCollection%602> třídy umožňují zadat vlastní porovnávači rovnosti klíčů.  
  
## <a name="see-also"></a>Viz také:

- [Kolekce a datové struktury](../../../docs/standard/collections/index.md)  
- [Běžně používané typy kolekcí](../../../docs/standard/collections/commonly-used-collection-types.md)  
- [Obecné typy](../../../docs/standard/generics/index.md)
