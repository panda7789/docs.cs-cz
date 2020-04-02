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
ms.openlocfilehash: ec14cf30159dda1f2c67ef0c0f5f0a3e52000c45
ms.sourcegitcommit: 961ec21c22d2f1d55c9cc8a7edf2ade1d1fd92e3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2020
ms.locfileid: "80588645"
---
# <a name="collections-and-data-structures"></a>Kolekce a datové struktury
Podobná data mohou být často zpracovány efektivněji při ukládání a manipulaci jako kolekce. Třídu <xref:System.Array?displayProperty=nameWithType> nebo třídy v <xref:System.Collections>oblasti <xref:System.Collections.Generic> <xref:System.Collections.Concurrent>, , System.Collections.Immutable namespaces můžete přidat, odebrat a upravit buď jednotlivé prvky nebo rozsah prvků v kolekci.  
  
 Existují dva hlavní typy kolekcí; obecné kolekce a neobecné kolekce. Obecné kolekce byly přidány v rozhraní .NET Framework 2.0 a poskytují kolekce, které jsou bezpečné pro typ v době kompilace. Z tohoto důvodu obecné kolekce obvykle nabízejí lepší výkon. Obecné kolekce přijmout parametr typu, když jsou vytvořeny a nevyžadují, <xref:System.Object> že přetypovat do a z typu při přidávání nebo odebírá položky z kolekce.  Kromě toho je většina obecných kolekcí podporována v aplikacích pro Windows Store. Neobecné kolekce ukládat <xref:System.Object>položky jako , vyžadují přetypování a většina z nich nejsou podporovány pro vývoj aplikací pro Windows Store. Však může zobrazit neobecné kolekce ve starším kódu.  
  
 Počínaje rozhraním .NET Framework 4 poskytují <xref:System.Collections.Concurrent> kolekce v oboru názvů efektivní operace bezpečné pro přístup k položkám kolekce z více vláken. Neměnné třídy kolekce v oboru názvů System.Collections.Immutable ([NuGet balíček](https://www.nuget.org/packages/System.Collections.Immutable)) jsou ze své podstaty bezpečné pro přístup z více vláken, protože operace jsou prováděny na kopii původní kolekce a původní kolekci nelze změnit.  

<a name="BKMK_Commoncollectionfeatures"></a>
## <a name="common-collection-features"></a>Běžné funkce kolekce  
 Všechny kolekce poskytují metody pro přidávání, odebírání nebo hledání položek v kolekci. Kromě toho všechny kolekce, které přímo <xref:System.Collections.ICollection> nebo nepřímo <xref:System.Collections.Generic.ICollection%601> implementují rozhraní nebo rozhraní, sdílejí tyto funkce:  
  
- **Možnost výčet kolekce**  
  
     Kolekce rozhraní .NET <xref:System.Collections.IEnumerable?displayProperty=nameWithType> Framework <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> implementují nebo umožňují, aby byla kolekce iterována. Čítač výčtu si lze myslet jako pohyblivý ukazatel na libovolný prvek v kolekci. [Foreach, v](../../csharp/language-reference/keywords/foreach-in.md) prohlášení a [pro každý ... Další příkaz](../../visual-basic/language-reference/statements/for-each-next-statement.md) použít čítač <xref:System.Collections.IEnumerable.GetEnumerator%2A> výčtu vystavené metodou a skrýt složitost manipulace s čítač výčtu. Kromě toho všechny kolekce, <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> která implementuje je považován za *dotazovatelný typ* a může být dotazován s LINQ. Linq dotazy poskytují společný vzor pro přístup k datům. Jsou obvykle stručnější a čitelnější než `foreach` standardní smyčky a poskytují možnosti filtrování, řazení a seskupování. Linq dotazy můžete také zlepšit výkon. Další informace naleznete [v tématech LINQ to Objects (C#)](../../csharp/programming-guide/concepts/linq/linq-to-objects.md), [LINQ to Objects (Visual Basic),](../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md) [Parallel LINQ (PLINQ)](../../../docs/standard/parallel-programming/introduction-to-plinq.md), [Introduction to LINQ Queries (C#)](../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md)a [Basic Query Operations (Visual Basic).](../../visual-basic/programming-guide/concepts/linq/basic-query-operations.md)  
  
- **Možnost zkopírovat obsah kolekce do pole**  
  
     Všechny kolekce lze zkopírovat do pole pomocí **CopyTo** metody; však pořadí prvků v novém poli je založena na pořadí, ve kterém čítač je vrátí. Výsledné pole je vždy jednorozměrné s dolní mez nulou.  
  
 Kromě toho mnoho tříd kolekce obsahuje následující funkce:  
  
- **Vlastnosti kapacity a počtu**  
  
     Kapacita kolekce je počet prvků, které může obsahovat. Počet kolekce je počet prvků, které skutečně obsahuje. Některé kolekce skrýt kapacitu nebo počet nebo obojí.  
  
     Většina kolekcí automaticky rozšířit kapacitu při dosažení aktuální kapacity. Paměť je přerozdělena a prvky jsou zkopírovány ze staré kolekce do nové. To snižuje kód potřebný k použití kolekce; však může být negativně ovlivněna výkon kolekce. Například pro <xref:System.Collections.Generic.List%601>, <xref:System.Collections.Generic.List%601.Count%2A> Pokud <xref:System.Collections.Generic.List%601.Capacity%2A>je menší než , přidání položky je Operace O(1). Pokud je třeba zvýšit kapacitu tak, aby vyhovovala novému prvku, přidání položky se stane operací O(n), kde n je <xref:System.Collections.Generic.List%601.Count%2A>. Nejlepší způsob, jak se vyhnout špatný výkon způsobený více přerozdělení je nastavit počáteční kapacitu, která má být odhadovaná velikost kolekce.  
  
     A <xref:System.Collections.BitArray> je zvláštní případ; jeho kapacita je stejná jako jeho délka, která je stejná jako jeho počet.  
  
- **Konzistentní dolní mez**  
  
     Dolní mez kolekce je index jeho první prvek. Všechny indexované kolekce <xref:System.Collections> v oborech názvů mají dolní mez nula, což znamená, že jsou 0 indexovány. <xref:System.Array>má ve výchozím nastavení dolní mez nuly, ale při vytváření instance třídy **Array** pomocí aplikace <xref:System.Array.CreateInstance%2A?displayProperty=nameWithType>lze definovat jinou dolní mez .  
  
- **Synchronizace pro přístup z** <xref:System.Collections> více vláken (pouze třídy).  
  
     Neobecné typy kolekcí <xref:System.Collections> v oboru názvů poskytují zabezpečení vlákna se synchronizací; obvykle vystaveny <xref:System.Collections.ICollection.SyncRoot%2A> prostřednictvím <xref:System.Collections.ICollection.IsSynchronized%2A> a členy. Tyto kolekce nejsou ve výchozím nastavení bezpečné pro přístup z více vláken. Pokud požadujete škálovatelný a efektivní vícevláknový přístup ke kolekci, použijte jednu z tříd v oboru <xref:System.Collections.Concurrent> názvů nebo zvažte použití neměnné kolekce. Další informace naleznete v [tématu Thread-Safe Collections](../../../docs/standard/collections/thread-safe/index.md).  
  
<a name="BKMK_Choosingacollection"></a>
## <a name="choosing-a-collection"></a>Výběr kolekce  
 Obecně byste měli použít obecné kolekce. Následující tabulka popisuje některé běžné scénáře kolekce a třídy kolekce, které můžete použít pro tyto scénáře. Pokud jste novým obecnými kolekcemi, tato tabulka vám pomůže vybrat obecnou kolekci, která funguje nejlépe pro váš úkol.  

|Chci...|Obecné možnosti kolekce|Neobecné možnosti kolekce|Možnosti kolekce bezpečné pro přístup z více vláken nebo neměnné|  
|-|-|-|-|  
|Ukládat položky jako páry klíč/hodnota pro rychlé vyhledávání pomocí klíče|<xref:System.Collections.Generic.Dictionary%602>|<xref:System.Collections.Hashtable><br /><br /> (Kolekce párů klíč/hodnota, které jsou uspořádány na základě kódu hash klíče.)|<xref:System.Collections.Concurrent.ConcurrentDictionary%602><br /><br /> <xref:System.Collections.ObjectModel.ReadOnlyDictionary%602><br /><br /> <xref:System.Collections.Immutable.ImmutableDictionary%602>|  
|Přístup k položkám podle indexu|<xref:System.Collections.Generic.List%601>|<xref:System.Array><br /><br /> <xref:System.Collections.ArrayList>|<xref:System.Collections.Immutable.ImmutableList%601><br /><br /> <xref:System.Collections.Immutable.ImmutableArray>|  
|Použít položky první v prvním ven (FIFO)|<xref:System.Collections.Generic.Queue%601>|<xref:System.Collections.Queue>|<xref:System.Collections.Concurrent.ConcurrentQueue%601><br /><br /> <xref:System.Collections.Immutable.ImmutableQueue%601>|  
|Použití dat Last-In-First-Out (LIFO)|<xref:System.Collections.Generic.Stack%601>|<xref:System.Collections.Stack>|<xref:System.Collections.Concurrent.ConcurrentStack%601><br /><br /> <xref:System.Collections.Immutable.ImmutableStack%601>|  
|Postupný přístup k položkám|<xref:System.Collections.Generic.LinkedList%601>|Žádné doporučení|Žádné doporučení|  
|Přijímat oznámení při odebrání nebo přidání položek do kolekce. (nářadí <xref:System.ComponentModel.INotifyPropertyChanged> a <xref:System.Collections.Specialized.INotifyCollectionChanged>)|<xref:System.Collections.ObjectModel.ObservableCollection%601>|Žádné doporučení|Žádné doporučení|  
|Seřazená kolekce|<xref:System.Collections.Generic.SortedList%602>|<xref:System.Collections.SortedList>|<xref:System.Collections.Immutable.ImmutableSortedDictionary%602><br /><br /> <xref:System.Collections.Immutable.ImmutableSortedSet%601>|  
|Sada pro matematické funkce|<xref:System.Collections.Generic.HashSet%601><br /><br /> <xref:System.Collections.Generic.SortedSet%601>|Žádné doporučení|<xref:System.Collections.Immutable.ImmutableHashSet%601><br /><br /> <xref:System.Collections.Immutable.ImmutableSortedSet%601>|  
  
<a name="BKMK_RelatedTopics"></a>
## <a name="related-topics"></a>Související témata  
  
|Nadpis|Popis|  
|-----------|-----------------|  
|[Výběr třídy kolekce](../../../docs/standard/collections/selecting-a-collection-class.md)|Popisuje různé kolekce a pomáhá vybrat jeden pro váš scénář.|  
|[Běžně používané typy kolekcí](../../../docs/standard/collections/commonly-used-collection-types.md)|Popisuje běžně používané obecné a neobecné <xref:System.Array?displayProperty=nameWithType>typy <xref:System.Collections.Generic.List%601?displayProperty=nameWithType>kolekcí, například , a <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType>.|  
|[Kdy použít generické kolekce](../../../docs/standard/collections/when-to-use-generic-collections.md)|Popisuje použití obecných typů kolekce.|  
|[Porovnávání a řazení v kolekcích](../../../docs/standard/collections/comparisons-and-sorts-within-collections.md)|Popisuje použití porovnání rovnosti a řazení porovnání v kolekcích.|  
|[Typy řazených kolekcí](../../../docs/standard/collections/sorted-collection-types.md)|Popisuje výkon a charakteristiky seřazených kolekcí.|  
|[Typy kolekce Hashtable a Dictionary](../../../docs/standard/collections/hashtable-and-dictionary-collection-types.md)|Popisuje funkce obecných a neobecných typů slovníků založených na hash.|  
|[Kolekce bezpečné pro přístup z více vláken](../../../docs/standard/collections/thread-safe/index.md)|Popisuje typy kolekcí, jako <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType> je například a <xref:System.Collections.Concurrent.ConcurrentBag%601?displayProperty=nameWithType> které podporují bezpečný a efektivní souběžný přístup z více vláken.|  
|System.Collections.Neměnný|Zavádí neměnné kolekce a poskytuje odkazy na typy kolekce.|  
  
<a name="BKMK_Reference"></a>
## <a name="reference"></a>Odkaz  
 <xref:System.Array?displayProperty=nameWithType>  
 <xref:System.Collections?displayProperty=nameWithType>  
 <xref:System.Collections.Concurrent?displayProperty=nameWithType>  
 <xref:System.Collections.Generic?displayProperty=nameWithType>  
 <xref:System.Collections.Specialized?displayProperty=nameWithType>  
 <xref:System.Linq?displayProperty=nameWithType>  
 <xref:System.Collections.Immutable>
