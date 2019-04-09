---
title: Kolekce a datové struktury
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- grouping data in collections
- objects [.NET Framework], grouping in collections
- Array class, grouping data in collections
- threading [.NET Framework], safety
- Collections classes
- collections [.NET Framework]
ms.assetid: 60cc581f-1db5-445b-ba04-a173396bf872
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d6b9e3d3f5ebc122e2031dac5999a80445ee03a8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59083831"
---
# <a name="collections-and-data-structures"></a>Kolekce a datové struktury
Podobná data může často být zpracována efektivněji při uloženy a zpracovávány jako kolekce. Můžete použít <xref:System.Array?displayProperty=nameWithType> třídu nebo třídy v <xref:System.Collections>, <xref:System.Collections.Generic>, <xref:System.Collections.Concurrent>, System.Collections.Immutable oborů názvů pro přidání, odebrání a změnu jednotlivých prvků nebo rozsahu prvků v kolekci.  
  
 Existují dva hlavní typy kolekcí; Obecné kolekce a obecné kolekce. Obecné kolekce byly přidány v rozhraní .NET Framework 2.0 a poskytují kolekcí, které jsou typově bezpečné v době kompilace. Z tohoto důvodu obecné kolekce běžně nabízí lepší výkon. Obecné kolekce přijímá parametr typu, když jsou vytvořeny a nevyžadují, že je převeden do a z <xref:System.Object> zadejte při přidání nebo odebrání položek z kolekce.  Kromě toho většina obecné kolekce jsou podporovány v [!INCLUDE[win8_appstore_long](../../../includes/win8-appstore-long-md.md)] aplikace. Neobecnou kolekce ukládá položky jako <xref:System.Object>, vyžaduje přetypování a většina nejsou podporovány pro [!INCLUDE[win8_appstore_long](../../../includes/win8-appstore-long-md.md)] vývoj aplikací. Ale může se zobrazit obecné kolekce ve starším kódu.  
  
 Počínaje [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], kolekce v <xref:System.Collections.Concurrent> obor názvů poskytují efektivní operace bezpečné pro vlákna pro přístup položky kolekce z více vláken. Neměnné kolekce tříd v oboru názvů System.Collections.Immutable ([balíček NuGet](https://www.nuget.org/packages/System.Collections.Immutable)) jsou ze své podstaty bezpečné pro vlákna, protože operace se provádějí na kopii původní kolekci a původní kolekci nelze změnit.  

<a name="BKMK_Commoncollectionfeatures"></a>   
## <a name="common-collection-features"></a>Běžné funkce kolekce  
 Všechny kolekce poskytují metody pro přidání, odebrání nebo hledání položek v kolekci. Kromě toho všechny kolekce, která přímo nebo nepřímo implementovat <xref:System.Collections.ICollection> rozhraní nebo <xref:System.Collections.Generic.ICollection%601> rozhraní sdílet tyto funkce:  
  
-   **Umožňuje vytvářet výčty kolekce**  
  
     Rozhraní .NET framework kolekce buď implementovat <xref:System.Collections.IEnumerable?displayProperty=nameWithType> nebo <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> povolit kolekce, kterou chcete provést iteraci pomocí. Čítače můžete představit jako přesouvatelný ukazatel na libovolný prvek v kolekci. [Foreach v](../../csharp/language-reference/keywords/foreach-in.md) příkazu a [For Each... Další příkaz](../../visual-basic/language-reference/statements/for-each-next-statement.md) použít enumerátor vystavené <xref:System.Collections.IEnumerable.GetEnumerator%2A> metoda a skrýt složitost manipulace s enumerátorem. Kromě toho se jakoukoli kolekci, která implementuje <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> se považuje za *dotazovatelný typ* a může být dotázán pomocí jazyka LINQ. Dotazy LINQ poskytují společný vzor pro přístup k datům. Jsou obvykle stručnější a čitelnější než standardní `foreach` smyčky a poskytují filtrování, řazení a seskupování schopností. Dotazy LINQ mohou také zvýšit výkon. Další informace najdete v tématu [LINQ to Objects (C#)](../../csharp/programming-guide/concepts/linq/linq-to-objects.md), [LINQ to Objects (Visual Basic)](../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md), [paralelní LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md), [Úvod do dotazů LINQ () C#)](../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md), a [základní operace dotazů (Visual Basic)](../../visual-basic/programming-guide/concepts/linq/basic-query-operations.md).  
  
-   **Možnost Kopírovat obsah kolekce do pole**  
  
     Všechny kolekce je možné zkopírovat do pole pomocí **CopyTo** metoda; ale pořadí prvků v poli nový podle pořadí, ve kterém je vrátí enumerátor. Výsledné pole je vždy jednorozměrný s dolní mez nula.  
  
 Kromě toho mnoho tříd kolekce obsahují následující funkce:  
  
-   **Vlastnosti kapacity a počet**  
  
     Kapacita kolekce je počet prvků, které může obsahovat. Počet prvků kolekce je počet prvků, které ve skutečnosti obsahuje. Některé kolekce skrýt kapacitu, počet nebo obojí.  
  
     Většina kolekce se automaticky rozšíří kapacity po dosažení aktuální kapacita. Je znovu přidělena paměť a prvky jsou zkopírovány z původní kolekce do nové. Tím se snižuje je kód potřebný k použití kolekce. však může být negativně ovlivněn výkon kolekce. Například pro <xref:System.Collections.Generic.List%601>, pokud <xref:System.Collections.Generic.List%601.Count%2A> je menší než <xref:System.Collections.Generic.List%601.Capacity%2A>, přidání položky je operace O(1). Pokud kapacita nového prvku skutečnost zohlednit zvýšením, přidání položky stane O(n) operace, kde n je <xref:System.Collections.Generic.List%601.Count%2A>. Nejlepší způsob, jak se vyhnout se špatným výkonem způsobené více přerozdělení je nastavit počáteční kapacitu na odhadovanou velikost kolekce.  
  
     A <xref:System.Collections.BitArray> je zvláštní případ; jeho kapacity je stejné jako jeho délka, což je stejná jako její vlastnosti count.  
  
-   **Konzistentní dolní mez**  
  
     Dolní mez kolekce je index svého prvního elementu. Všechny kolekce v indexovaných <xref:System.Collections> obory názvů mají dolní mez nula, to znamená jsou indexovány 0. <xref:System.Array> dolní mez nula ve výchozím nastavení má, ale jiné dolní mez lze definovat při vytváření instance objektu **pole** pomocí <xref:System.Array.CreateInstance%2A?displayProperty=nameWithType>.  
  
-   **Synchronizace pro přístup z více vláken** (<xref:System.Collections> pouze třídy).  
  
     Kolekce neobecné typy, které do <xref:System.Collections> obor názvů poskytuje některé zabezpečení vlákna se synchronizací; obvykle vystavenou přes <xref:System.Collections.ICollection.SyncRoot%2A> a <xref:System.Collections.ICollection.IsSynchronized%2A> členy. Tato kolekce nejsou bezpečné pro vlákna ve výchozím nastavení. Pokud potřebujete efektivní a škálovatelné vícevláknový přístup ke kolekci, použijte jednu z tříd v <xref:System.Collections.Concurrent> oboru názvů nebo zvažte použití neměnné kolekce. Další informace najdete v tématu [kolekce bezpečné pro vlákna](../../../docs/standard/collections/thread-safe/index.md).  
  
<a name="BKMK_Choosingacollection"></a>   
## <a name="choosing-a-collection"></a>Výběr kolekce  
 Obecně platí měli byste použít obecné kolekce. Následující tabulka popisuje některé obvyklé scénáře, kolekce a třídy kolekcí, které můžete použít pro tyto scénáře. Pokud jste ještě do obecné kolekce, tato tabulka vám pomůže zvolit obecné kolekce, která je nejvhodnější pro vaši úlohu.  
 
|Chci...|Možnosti Obecné kolekce|Možnosti neobecné shromažďování|Možnosti bezpečné pro vlákna nebo neměnné kolekce|  
|-|-|-|-|  
|Store položky jako páry klíč/hodnota pro rychlé vyhledávání pomocí klíče|<xref:System.Collections.Generic.Dictionary%602>|<xref:System.Collections.Hashtable><br /><br /> (Kolekce dvojic klíč/hodnota, které jsou uspořádány na základě kódu hodnoty hash klíče.)|<xref:System.Collections.Concurrent.ConcurrentDictionary%602><br /><br /> <xref:System.Collections.ObjectModel.ReadOnlyDictionary%602><br /><br /> <xref:System.Collections.Immutable.ImmutableDictionary%602>|  
|Přístup k položkám podle indexu|<xref:System.Collections.Generic.List%601>|<xref:System.Array><br /><br /> <xref:System.Collections.ArrayList>|<xref:System.Collections.Immutable.ImmutableList%601><br /><br /> <xref:System.Collections.Immutable.ImmutableArray>|  
|Pomocí položky first-in-first-out (FIFO)|<xref:System.Collections.Generic.Queue%601>|<xref:System.Collections.Queue>|<xref:System.Collections.Concurrent.ConcurrentQueue%601><br /><br /> <xref:System.Collections.Immutable.ImmutableQueue%601>|  
|Použití dat Last-In-First-Out (LIFO)|<xref:System.Collections.Generic.Stack%601>|<xref:System.Collections.Stack>|<xref:System.Collections.Concurrent.ConcurrentStack%601><br /><br /> <xref:System.Collections.Immutable.ImmutableStack%601>|  
|Postupně položky přístupu|<xref:System.Collections.Generic.LinkedList%601>|Žádné doporučení|Žádné doporučení|  
|Dostanete oznámení, pokud se přidá do kolekce nebo odebrat položky. (implementuje <xref:System.ComponentModel.INotifyPropertyChanged> a <xref:System.Collections.Specialized.INotifyCollectionChanged>)|<xref:System.Collections.ObjectModel.ObservableCollection%601>|Žádné doporučení|Žádné doporučení|  
|Řazených kolekcí|<xref:System.Collections.Generic.SortedList%602>|<xref:System.Collections.SortedList>|<xref:System.Collections.Immutable.ImmutableSortedDictionary%602><br /><br /> <xref:System.Collections.Immutable.ImmutableSortedSet%601>|  
|A nastavte pro matematické funkce|<xref:System.Collections.Generic.HashSet%601><br /><br /> <xref:System.Collections.Generic.SortedSet%601>|Žádné doporučení|<xref:System.Collections.Immutable.ImmutableHashSet%601><br /><br /> <xref:System.Collections.Immutable.ImmutableSortedSet%601>|  
  
<a name="BKMK_RelatedTopics"></a>   
## <a name="related-topics"></a>Související témata  
  
|Název|Popis|  
|-----------|-----------------|  
|[Výběr třídy kolekce](../../../docs/standard/collections/selecting-a-collection-class.md)|Popisuje různé typy kolekcí a umožňuje vybrat jednu pro váš scénář.|  
|[Běžně používané typy kolekcí](../../../docs/standard/collections/commonly-used-collection-types.md)|Popisuje běžně používané obecné a neobecné typy kolekce, jako <xref:System.Array?displayProperty=nameWithType>, <xref:System.Collections.Generic.List%601?displayProperty=nameWithType>, a <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType>.|  
|[Kdy použít generické kolekce](../../../docs/standard/collections/when-to-use-generic-collections.md)|Tento článek popisuje použití obecných typů kolekce.|  
|[Porovnávání a řazení v kolekcích](../../../docs/standard/collections/comparisons-and-sorts-within-collections.md)|Popisuje způsob používání porovnání rovnosti a porovnání řazení v kolekcích.|  
|[Typy řazených kolekcí](../../../docs/standard/collections/sorted-collection-types.md)|Popisuje charakteristiky a seřazené kolekce výkonu|  
|[Typy kolekce Hashtable a Dictionary](../../../docs/standard/collections/hashtable-and-dictionary-collection-types.md)|Popisuje funkce typů obecných a neobecných hash na základě slovníku.|  
|[Kolekce se zabezpečenými vlákny](../../../docs/standard/collections/thread-safe/index.md)|Popisuje typy kolekce, například <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType> a <xref:System.Collections.Concurrent.ConcurrentBag%601?displayProperty=nameWithType> , které podporují bezpečný a účinný souběžný přístup z více vláken.|  
|System.Collections.Immutable|Představuje neměnné kolekce a poskytuje odkazy na typy kolekcí.|  
  
<a name="BKMK_Reference"></a>   
## <a name="reference"></a>Odkaz  
 <xref:System.Array?displayProperty=nameWithType>  
 <xref:System.Collections?displayProperty=nameWithType>  
 <xref:System.Collections.Concurrent?displayProperty=nameWithType>  
 <xref:System.Collections.Generic?displayProperty=nameWithType>  
 <xref:System.Collections.Specialized?displayProperty=nameWithType>  
 <xref:System.Linq?displayProperty=nameWithType>  
 <xref:System.Collections.Immutable>
