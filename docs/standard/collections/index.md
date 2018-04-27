---
title: Kolekce a datové struktury
ms.date: 03/30/2017
ms.prod: .net
ms.technology: dotnet-standard
ms.topic: article
helpviewer_keywords:
- grouping data in collections
- objects [.NET Framework], grouping in collections
- Array class, grouping data in collections
- threading [.NET Framework], safety
- Collections classes
- collections [.NET Framework]
ms.assetid: 60cc581f-1db5-445b-ba04-a173396bf872
caps.latest.revision: 36
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: e36d23c6dfd89b54c86d0b6062813aeccb649579
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2018
---
# <a name="collections-and-data-structures"></a>Kolekce a datové struktury
Podobně jako data lze často zpracovávat efektivněji při uloženy a zpracovávány jako kolekce. Můžete použít <xref:System.Array?displayProperty=nameWithType> třídu nebo třídy v <xref:System.Collections>, <xref:System.Collections.Generic>, <xref:System.Collections.Concurrent>, System.Collections.Immutable oborů názvů pro přidání, odebrání a změna jednotlivé elementy nebo rozsah elementů v kolekci.  
  
 Existují dva hlavní typy kolekcí; Obecné kolekce a neobecné kolekce. Obecné kolekce byly přidány v rozhraní .NET Framework 2.0 a zadejte kolekce, které jsou bezpečnost typů v době kompilace. Z toho důvodu obecné kolekce běžně nabízí lepší výkon. Obecné kolekce přijímat parametr typu v případě, že se vytvářejí a nevyžadují vložíte do a z <xref:System.Object> zadejte při přidání nebo odebrání položky z kolekce.  Kromě toho většina obecné kolekce jsou podporovány v [!INCLUDE[win8_appstore_long](../../../includes/win8-appstore-long-md.md)] aplikace. Kolekce obecného bez uložení položky jako <xref:System.Object>, vyžadují přetypování a většina nejsou podporovány pro [!INCLUDE[win8_appstore_long](../../../includes/win8-appstore-long-md.md)] vývoj aplikací. Ale může se zobrazit neobecnou kolekce ve starším kódu.  
  
 Od verze [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], kolekce v <xref:System.Collections.Concurrent> obor názvů poskytují efektivní operace vláken pro přístup k položkám kolekce z více vláken. Neměnné kolekce třídy v oboru názvů System.Collections.Immutable ([balíček NuGet](https://www.nuget.org/packages/System.Collections.Immutable)) jsou ze své podstaty bezpečné pro přístup z více vláken, protože operací na kopii původní kolekci a původní kolekci nelze změnit.  
  
  
<a name="BKMK_Commoncollectionfeatures"></a>   
## <a name="common-collection-features"></a>Běžné funkce kolekce  
 Všechny kolekce poskytují metody pro přidání, odebrání nebo hledání položek v kolekci. Kromě toho všechny kolekce, přímo ani nepřímo implementovat <xref:System.Collections.ICollection> rozhraní nebo <xref:System.Collections.Generic.ICollection%601> rozhraní sdílet tyto funkce:  
  
-   **Umožňuje výčet kolekce**  
  
     Rozhraní .NET framework kolekce buď implementovat <xref:System.Collections.IEnumerable?displayProperty=nameWithType> nebo <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> jak povolit kolekce k být vstupní prostřednictvím. Enumerátor můžete představit jako pohyblivý ukazatel na libovolný element v kolekci. [Foreach v](~/docs/csharp/language-reference/keywords/foreach-in.md) příkaz a [For Each... Další příkaz](~/docs/visual-basic/language-reference/statements/for-each-next-statement.md) použít enumerátor vystavené <xref:System.Collections.IEnumerable.GetEnumerator%2A> metoda a skrýt složitosti manipulace s enumerátor. Kromě toho se jakoukoli kolekci, která implementuje <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> se považuje za *dotazovatelný typ* a může být dotazován s dotazy LINQ. Dotazy LINQ poskytují společný vzorek pro přístup k datům. Jsou obvykle více stručná a čitelná než standardní `foreach` v cyklu a poskytují filtrování, řazení a seskupování schopností. Výkon lze zvýšit rovněž dotazů LINQ. Další informace najdete v tématu [LINQ na objekty](https://msdn.microsoft.com/library/73cafe73-37cf-46e7-bfa7-97c7eea7ced9), [paralelní LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md) a [Úvod do dotazů LINQ (C#)](~/docs/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).  
  
-   **Možnost Kopírovat obsah kolekce do pole**  
  
     Všechny kolekce je možné zkopírovat do pole pomocí **CopyTo** metoda; však pořadí prvků v poli nové podle pořadí, ve kterém je vrátí enumerátor. Výsledné pole je vždy jednorozměrné s dolní mez 0.  
  
 Kromě toho mnoho třídy kolekce obsahují následující funkce:  
  
-   **Kapacita a počet vlastnosti**  
  
     Kapacita kolekce je počet elementů, které může obsahovat. Počet prvků kolekce je počet elementů, které aktuálně obsahuje. Některé kolekce skrýt kapacitu nebo počet nebo obojí.  
  
     Většiny kolekcí se automaticky rozšíří kapacity, když je dosaženo aktuální kapacitu. Je znovu přidělit paměť a prvky jsou zkopírovány z původní kolekce do nového. Tím se snižuje je kód potřebný k použití kolekce. ale může mít negativní vliv na výkon kolekce. Například pro <xref:System.Collections.Generic.List%601>, pokud <xref:System.Collections.Generic.List%601.Count%2A> je menší než <xref:System.Collections.Generic.List%601.Capacity%2A>, přidání položky je o(1), která operace. Pokud je kapacita musí být skutečnost zohlednit zvýšením nového elementu, přidání položky stane O(n) operace, kde n je <xref:System.Collections.Generic.List%601.Count%2A>. Nejlepší způsob, jak se vyhnout nízký výkon způsobené opakovaným přidělováním paměti je nastavená počáteční kapacita na odhadovanou velikost kolekce.  
  
     A <xref:System.Collections.BitArray> je zvláštní případ; své kapacity je stejný jako jeho délka, která je stejná jako jeho počet.  
  
-   **Konzistentní dolní mez**  
  
     Dolní mez kolekce je index jeho první prvek. Všechny kolekce v indexovaných <xref:System.Collections> obory názvů mít dolní mez nulové hodnoty, což znamená, jsou indexované 0. <xref:System.Array> má dolní mez nula ve výchozím nastavení, ale můžete definovat různé dolní meze, při vytváření instance **pole** pomocí <xref:System.Array.CreateInstance%2A?displayProperty=nameWithType>.  
  
-   **Synchronizace pro přístup z více vláken** (<xref:System.Collections> pouze třídy).  
  
     Kolekce non obecné typy v <xref:System.Collections> oboru názvů zadejte některé zabezpečení vlákna v synchronizaci; obvykle vystavenou přes <xref:System.Collections.ICollection.SyncRoot%2A> a <xref:System.Collections.ICollection.IsSynchronized%2A> členy. Tyto kolekce nejsou bezpečné pro přístup z více vláken ve výchozím nastavení. Pokud požadujete škálovatelný a efektivní vícevláknový přístup ke kolekci, použijte jednu z tříd v <xref:System.Collections.Concurrent> oboru názvů nebo zvažte použití neměnné kolekce. Další informace najdete v tématu [kolekce se zabezpečenými vlákny](../../../docs/standard/collections/thread-safe/index.md).  
  
<a name="BKMK_Choosingacollection"></a>   
## <a name="choosing-a-collection"></a>Výběr kolekce  
 Obecně platí měli byste použít obecné kolekce. Následující tabulka popisuje některé běžné scénáře, kolekce a třídy kolekce, které můžete použít pro tyto scénáře. Pokud jste pro obecné kolekce nové, tato tabulka vám pomůže vybrat obecnou kolekci, která je nejlepší pro úlohu.  
|Chci...|Možnosti Obecné kolekce|Možnosti non obecné kolekce|Možnosti vláken nebo neměnné kolekce|  
|-|-|-|-|  
|Uložení položek dvojic klíč/hodnota pro rychlé hledání pomocí klíče|<xref:System.Collections.Generic.Dictionary%602>|<xref:System.Collections.Hashtable><br /><br /> (Kolekce párů klíč/hodnota, které jsou uspořádat podle hodnota hash klíče.)|<xref:System.Collections.Concurrent.ConcurrentDictionary%602><br /><br /> <xref:System.Collections.ObjectModel.ReadOnlyDictionary%602><br /><br /> <xref:System.Collections.Immutable.ImmutableDictionary%602>|  
|Přístup k položkám podle indexu|<xref:System.Collections.Generic.List%601>|<xref:System.Array><br /><br /> <xref:System.Collections.ArrayList>|<xref:System.Collections.Immutable.ImmutableList%601><br /><br /> <xref:System.Collections.Immutable.ImmutableArray>|  
|Pomocí položky first-in-first-out (FIFO)|<xref:System.Collections.Generic.Queue%601>|<xref:System.Collections.Queue>|<xref:System.Collections.Concurrent.ConcurrentQueue%601><br /><br /> <xref:System.Collections.Immutable.ImmutableQueue%601>|  
|Možnost používat data Last-In-First-Out (LIFO)|<xref:System.Collections.Generic.Stack%601>|<xref:System.Collections.Stack>|<xref:System.Collections.Concurrent.ConcurrentStack%601><br /><br /> <xref:System.Collections.Immutable.ImmutableStack%601>|  
|Posloupnost položek přístup|<xref:System.Collections.Generic.LinkedList%601>|Žádná doporučení.|Žádná doporučení.|  
|Přijímat oznámení, když jsou odebrány nebo přidat do kolekce položky. (implementuje <xref:System.ComponentModel.INotifyPropertyChanged> a <xref:System.Collections.Specialized.INotifyCollectionChanged>)|<xref:System.Collections.ObjectModel.ObservableCollection%601>|Žádná doporučení.|Žádná doporučení.|  
|Řazených kolekcí|<xref:System.Collections.Generic.SortedList%602>|<xref:System.Collections.SortedList>|<xref:System.Collections.Immutable.ImmutableSortedDictionary%602><br /><br /> <xref:System.Collections.Immutable.ImmutableSortedSet%601>|  
|A nastavte pro matematické funkce|<xref:System.Collections.Generic.HashSet%601><br /><br /> <xref:System.Collections.Generic.SortedSet%601>|Žádná doporučení.|<xref:System.Collections.Immutable.ImmutableHashSet%601><br /><br /> <xref:System.Collections.Immutable.ImmutableSortedSet%601>|  
  
<a name="BKMK_RelatedTopics"></a>   
## <a name="related-topics"></a>Související témata  
  
|Název|Popis|  
|-----------|-----------------|  
|[Výběr třídy kolekce](../../../docs/standard/collections/selecting-a-collection-class.md)|Popisuje různé kolekce a umožňuje vybrat jednu pro váš scénář.|  
|[Běžně používané typy kolekcí](../../../docs/standard/collections/commonly-used-collection-types.md)|Popisuje běžně používané obecné a neobecné typy kolekcí, jako <xref:System.Array?displayProperty=nameWithType>, <xref:System.Collections.Generic.List%601?displayProperty=nameWithType>, a <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType>.|  
|[Kdy použít generické kolekce](../../../docs/standard/collections/when-to-use-generic-collections.md)|Popisuje použití obecné typy kolekcí.|  
|[Porovnávání a řazení v kolekcích](../../../docs/standard/collections/comparisons-and-sorts-within-collections.md)|Popisuje použití porovnání rovnosti a porovnání při řazení v kolekcích.|  
|[Typy řazených kolekcí](../../../docs/standard/collections/sorted-collection-types.md)|Popisuje výkonu řazených kolekcí a vlastnosti|  
|[Typy kolekce Hashtable a Dictionary](../../../docs/standard/collections/hashtable-and-dictionary-collection-types.md)|Popisuje funkce pro obecné a neobecné slovník na základě hodnoty hash typů.|  
|[Kolekce se zabezpečenými vlákny](../../../docs/standard/collections/thread-safe/index.md)|Popisuje typy kolekcí, například <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType> a <xref:System.Collections.Concurrent.ConcurrentBag%601?displayProperty=nameWithType> podporující bezpečný a efektivní souběžný přístup z více vláken.|  
|System.Collections.Immutable|Neměnné kolekce uvádí a poskytuje odkazy na typy kolekcí.|  
  
<a name="BKMK_Reference"></a>   
## <a name="reference"></a>Odkaz  
 <xref:System.Array?displayProperty=nameWithType>  
 <xref:System.Collections?displayProperty=nameWithType>  
 <xref:System.Collections.Concurrent?displayProperty=nameWithType>  
 <xref:System.Collections.Generic?displayProperty=nameWithType>  
 <xref:System.Collections.Specialized?displayProperty=nameWithType>  
 <xref:System.Linq?displayProperty=nameWithType>  
 <xref:System.Collections.Immutable>
