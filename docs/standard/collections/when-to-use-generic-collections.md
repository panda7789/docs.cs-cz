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
ms.openlocfilehash: 1ea40542b235dd51bfec38aae9718b2278d7073b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33572642"
---
# <a name="when-to-use-generic-collections"></a>Kdy použít generické kolekce
Pomocí obecné kolekce je obecně nedoporučuje, protože získáte okamžitý výhodou bezpečnost typů bez nutnosti odvozovat od typu základní kolekce a implementace konkrétní typ členů. Obecné typy kolekcí také obecně poskytují lepší výkon než odpovídající typy neobecné kolekcí (a lépe než typy, které jsou odvozeny od neobecné základní kolekci typů) při elementy z kolekce jsou typy hodnot, protože s obecnými typy není potřeba pole elementy.  
  
 Pro programy, které se zaměřují [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] nebo novější, byste měli použít obecné třídy kolekcí v <xref:System.Collections.Concurrent> obor názvů, když je více vláken může přidávat nebo odebírat současně položky z kolekce.  
  
 Následující obecné typy odpovídají existujícím typům kolekcí:  
  
-   <xref:System.Collections.Generic.List%601> je obecná třída, která odpovídá <xref:System.Collections.ArrayList>.  
  
-   <xref:System.Collections.Generic.Dictionary%602> a <xref:System.Collections.Concurrent.ConcurrentDictionary%602> jsou obecné třídy, které odpovídají <xref:System.Collections.Hashtable>.  
  
-   <xref:System.Collections.ObjectModel.Collection%601> je obecná třída, která odpovídá <xref:System.Collections.CollectionBase>. <xref:System.Collections.ObjectModel.Collection%601> lze použít jako základní třídy, ale na rozdíl od <xref:System.Collections.CollectionBase>, není abstraktní. Díky tomu je jednodušší použít.  
  
-   <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> je obecná třída, která odpovídá <xref:System.Collections.ReadOnlyCollectionBase>. <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> není abstraktní a má konstruktor, který usnadňuje vystavení existující <xref:System.Collections.Generic.List%601> jako kolekce jen pro čtení.  
  
-   <xref:System.Collections.Generic.Queue%601>, <xref:System.Collections.Concurrent.ConcurrentQueue%601>, <xref:System.Collections.Generic.Stack%601>, <xref:System.Collections.Concurrent.ConcurrentStack%601>, A <xref:System.Collections.Generic.SortedList%602> obecné třídy odpovídají příslušné neobecné třídy se stejnými názvy.  
  
## <a name="additional-types"></a>Další typy  
 Několik typů obecnou kolekci ještě nemá neobecné protějšky. Zahrnují následující:  
  
-   <xref:System.Collections.Generic.LinkedList%601> je pro obecné účely odkazovaného seznamu, který poskytuje vložení a odebrání o(1).  
  
-   <xref:System.Collections.Generic.SortedDictionary%602> je seřazený slovník s O (protokolu `n`) vložení a načtení operací, které je výhodná možnost pro <xref:System.Collections.Generic.SortedList%602>.  
  
-   <xref:System.Collections.ObjectModel.KeyedCollection%602> je hybridní mezi seznam a slovník, který poskytuje způsob, jak ukládat objekty, které obsahují vlastní klíče.  
  
-   <xref:System.Collections.Concurrent.BlockingCollection%601> implementuje třídu kolekce s funkcí ohraničování a blokování.  
  
-   <xref:System.Collections.Concurrent.ConcurrentBag%601> poskytuje rychlé vložení a odebrání neuspořádaný elementů.  
  
## <a name="linq-to-objects"></a>LINQ na objekty  
 LINQ na objekty funkce umožňuje používat dotazy LINQ pro přístup k objektům v paměti, dokud implementuje typ objektu <xref:System.Collections.IEnumerable?displayProperty=nameWithType> nebo <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> rozhraní. Dotazy LINQ poskytují společný vzorek pro přístup k datům; Obvykle se jedná o více stručná a čitelná než standardní `foreach` cyklu; a zadejte filtrování, řazení a seskupování schopností. Výkon lze zvýšit rovněž dotazů LINQ. Další informace najdete v tématu [LINQ na objekty](https://msdn.microsoft.com/library/73cafe73-37cf-46e7-bfa7-97c7eea7ced9) a [paralelní LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md).  
  
## <a name="additional-functionality"></a>Další funkce  
 Některé obecné typy mají funkce, které se nenachází ve typy neobecné kolekcí. Například <xref:System.Collections.Generic.List%601> třídy, která odpovídá neobecné <xref:System.Collections.ArrayList> třídu, má několik metod, které přijímají obecní delegáti, jako <xref:System.Predicate%601> delegáta, který vám umožní určit metody pro hledání v seznamu, <xref:System.Action%601>delegáta, který představuje metody, které působí na každý prvek v seznamu a <xref:System.Converter%602> delegáta, který umožňuje definovat převody mezi typy.  
  
 <xref:System.Collections.Generic.List%601> Třída umožňuje zadat vlastní <xref:System.Collections.Generic.IComparer%601> implementace obecné rozhraní pro řazení a hledání v seznamu. <xref:System.Collections.Generic.SortedDictionary%602> a <xref:System.Collections.Generic.SortedList%602> třídy také mají tuto možnost. Kromě toho tyto třídy umožňují určit komparátory při vytvoření kolekce. Podobně <xref:System.Collections.Generic.Dictionary%602> a <xref:System.Collections.ObjectModel.KeyedCollection%602> třídy umožňují určit vlastní komparátory rovnosti.  
  
## <a name="see-also"></a>Viz také  
 [Kolekce a datové struktury](../../../docs/standard/collections/index.md)  
 [Běžně používané typy kolekcí](../../../docs/standard/collections/commonly-used-collection-types.md)  
 [Obecné typy](../../../docs/standard/generics/index.md)
