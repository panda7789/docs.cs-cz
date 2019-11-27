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
ms.openlocfilehash: bb231df9ed33b89fa15cde998379b2964cf32ff9
ms.sourcegitcommit: 81ad1f09b93f3b3e6706a7f2e4ddf50ef229ea3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/20/2019
ms.locfileid: "74204775"
---
# <a name="collections-and-data-structures"></a>Kolekce a datové struktury
Podobná data je často možné zpracovávat efektivněji, když jsou uložená a manipulována jako kolekce. Můžete použít třídu <xref:System.Array?displayProperty=nameWithType> nebo třídy v <xref:System.Collections>, <xref:System.Collections.Generic>, <xref:System.Collections.Concurrent>, System. Collections. neproměnlivé obory názvů pro přidání, odebrání a úpravu individuálních prvků nebo rozsahu prvků v kolekci.  
  
 Existují dva hlavní typy kolekcí; Obecné kolekce a jiné než obecné kolekce. V .NET Framework 2,0 byly přidány obecné kolekce a poskytovaly kolekce, které jsou typově bezpečné v době kompilace. Z tohoto důvodu obecné kolekce obvykle nabízejí lepší výkon. Obecné kolekce přijímají parametr typu při jejich sestavení a nevyžadují, abyste přetypování do a z <xref:System.Object>ho typu při přidávání nebo odebírání položek z kolekce.  Kromě toho jsou v aplikacích pro Windows Store podporovány většinou obecné kolekce. Neobecné kolekce ukládají položky jako <xref:System.Object>, vyžadují přetypování a většina nejsou podporované pro vývoj aplikací pro Windows Store. V starším kódu ale můžete vidět neobecné kolekce.  
  
 Počínaje .NET Framework 4 poskytují kolekce v oboru názvů <xref:System.Collections.Concurrent> efektivní operace bezpečné pro přístup z více vláken pro přístup k položkám kolekce z více vláken. Neměnné třídy kolekce v System. Collections. neměnný obor názvů ([balíček NuGet](https://www.nuget.org/packages/System.Collections.Immutable)) jsou podstatou bezpečné pro přístup z více vláken, protože operace jsou prováděny na kopii původní kolekce a původní kolekci nelze změnit.  

<a name="BKMK_Commoncollectionfeatures"></a>   
## <a name="common-collection-features"></a>Společné funkce kolekcí  
 Všechny kolekce poskytují metody pro přidání, odebrání nebo vyhledání položek v kolekci. Kromě toho všechny kolekce, které přímo nebo nepřímo implementují rozhraní <xref:System.Collections.ICollection> nebo rozhraní <xref:System.Collections.Generic.ICollection%601> sdílejí tyto funkce:  
  
- **Možnost vytvořit výčet kolekce**  
  
     Kolekce .NET Framework buď implementují <xref:System.Collections.IEnumerable?displayProperty=nameWithType> nebo <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType>, aby bylo možné kolekci vyiterovat pomocí. Enumerátor lze představit jako pohyblivý ukazatel na libovolný prvek v kolekci. Příkaz [foreach, v](../../csharp/language-reference/keywords/foreach-in.md) příkazu a [pro každý... Další příkaz](../../visual-basic/language-reference/statements/for-each-next-statement.md) použijte enumerátor vystavený metodou <xref:System.Collections.IEnumerable.GetEnumerator%2A> a skryjte složitost manipulace s enumerátorem. Kromě toho jakákoli kolekce, která implementuje <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType>, je považována za *typ Queryable* a může se dotazovat pomocí LINQ. Dotazy LINQ poskytují společný vzor pro přístup k datům. Jsou obvykle stručnější a čitelné než standardní `foreach` smyčky a poskytují možnosti filtrování, řazení a seskupování. Dotazy LINQ mohou také zlepšit výkon. Další informace naleznete v tématu [LINQ to Objects (C#)](../../csharp/programming-guide/concepts/linq/linq-to-objects.md), [LINQ to Objects (Visual Basic)](../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md), [Paralelní LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md), [Úvod do dotazů LINQ (C#)](../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md)a [základní operace dotazů (Visual Basic)](../../visual-basic/programming-guide/concepts/linq/basic-query-operations.md).  
  
- **Možnost Kopírovat obsah kolekce do pole**  
  
     Všechny kolekce lze zkopírovat do pole pomocí metody **CopyTo** ; pořadí prvků v novém poli je však založeno na pořadí, ve kterém je vrací enumerátor. Výsledné pole je vždy jednorozměrné s dolní mezí nula.  
  
 Kromě toho mnoho tříd kolekcí obsahuje následující funkce:  
  
- **Vlastnosti kapacity a počtu**  
  
     Kapacita kolekce je počet prvků, které může obsahovat. Počet prvků v kolekci je počet prvků, které ve skutečnosti obsahují. Některé kolekce skrývají kapacitu nebo počet nebo obojí.  
  
     Většina kolekcí se při dosažení aktuální kapacity automaticky zvětšuje v kapacitě. Paměť je znovu přidělena a prvky jsou zkopírovány z staré kolekce do nové. Tím se snižuje kód potřebný k použití kolekce; výkon kolekce však může negativně ovlivnit. Například pro <xref:System.Collections.Generic.List%601>, pokud <xref:System.Collections.Generic.List%601.Count%2A> je menší než <xref:System.Collections.Generic.List%601.Capacity%2A>, přidání položky je operace O (1). Pokud je potřeba zvýšit kapacitu tak, aby vyhovovala novému prvku, přidání položky se změní na operaci O (n), kde n je <xref:System.Collections.Generic.List%601.Count%2A>. Nejlepším způsobem, jak zabránit špatnému výkonu způsobenému více přerozdělením, je nastavit počáteční kapacitu na odhadovanou velikost kolekce.  
  
     <xref:System.Collections.BitArray> je zvláštní případ; jeho kapacita je shodná s délkou, která je stejná jako počet.  
  
- **Konzistentní dolní mez**  
  
     Dolní mez kolekce je index jeho prvního prvku. Všechny indexované kolekce v oborech názvů <xref:System.Collections> mají dolní mez nula, což znamená, že jsou 0 – indexované. ve výchozím nastavení má <xref:System.Array> nižší mez nula, ale při vytváření instance třídy **Array** pomocí <xref:System.Array.CreateInstance%2A?displayProperty=nameWithType>může být definována jiná dolní mez.  
  
- **Synchronizace pro přístup z více vláken** (pouze<xref:System.Collections> třídy).  
  
     Neobecné typy kolekcí v oboru názvů <xref:System.Collections> poskytují určitou bezpečnost vlákna při synchronizaci. obvykle zveřejněná prostřednictvím <xref:System.Collections.ICollection.SyncRoot%2A> a <xref:System.Collections.ICollection.IsSynchronized%2A>ch členů. Ve výchozím nastavení nejsou tyto kolekce bezpečné pro přístup z více vláken. Pokud vyžadujete škálovatelný a efektivní vícevláknový přístup ke kolekci, použijte jednu z tříd v oboru názvů <xref:System.Collections.Concurrent> nebo zvažte použití neměnné kolekce. Další informace najdete v tématu [kolekce bezpečné](../../../docs/standard/collections/thread-safe/index.md)pro přístup z více vláken.  
  
<a name="BKMK_Choosingacollection"></a>   
## <a name="choosing-a-collection"></a>Výběr kolekce  
 Obecně byste měli použít obecné kolekce. Následující tabulka popisuje některé běžné scénáře shromažďování a třídy kolekcí, které můžete pro tyto scénáře použít. Pokud s obecnými kolekcemi začínáte, tato tabulka vám pomůže vybrat obecnou kolekci, která bude pro váš úkol fungovat nejlépe.  
 
|Chci...|Možnosti Obecné kolekce|Možnosti bez obecné kolekce|Možnosti bezpečného a neměnného přístupu k vláknům|  
|-|-|-|-|  
|Ukládat položky jako páry klíč/hodnota pro rychlé vyhledání podle klíče|<xref:System.Collections.Generic.Dictionary%602>|<xref:System.Collections.Hashtable><br /><br /> (Kolekce párů klíč/hodnota, které jsou uspořádány na základě hash kódu klíče.)|<xref:System.Collections.Concurrent.ConcurrentDictionary%602><br /><br /> <xref:System.Collections.ObjectModel.ReadOnlyDictionary%602><br /><br /> <xref:System.Collections.Immutable.ImmutableDictionary%602>|  
|Přístup k položkám podle indexu|<xref:System.Collections.Generic.List%601>|<xref:System.Array><br /><br /> <xref:System.Collections.ArrayList>|<xref:System.Collections.Immutable.ImmutableList%601><br /><br /> <xref:System.Collections.Immutable.ImmutableArray>|  
|Použití položek first-in-first-out (FIFO)|<xref:System.Collections.Generic.Queue%601>|<xref:System.Collections.Queue>|<xref:System.Collections.Concurrent.ConcurrentQueue%601><br /><br /> <xref:System.Collections.Immutable.ImmutableQueue%601>|  
|Použití dat Last-in-first-out (LIFO)|<xref:System.Collections.Generic.Stack%601>|<xref:System.Collections.Stack>|<xref:System.Collections.Concurrent.ConcurrentStack%601><br /><br /> <xref:System.Collections.Immutable.ImmutableStack%601>|  
|Sekvenční přístup k položkám|<xref:System.Collections.Generic.LinkedList%601>|Bez doporučení|Bez doporučení|  
|Dostávat oznámení, když se položky odeberou nebo přidají do kolekce (implementuje <xref:System.ComponentModel.INotifyPropertyChanged> a <xref:System.Collections.Specialized.INotifyCollectionChanged>)|<xref:System.Collections.ObjectModel.ObservableCollection%601>|Bez doporučení|Bez doporučení|  
|Seřazená kolekce|<xref:System.Collections.Generic.SortedList%602>|<xref:System.Collections.SortedList>|<xref:System.Collections.Immutable.ImmutableSortedDictionary%602><br /><br /> <xref:System.Collections.Immutable.ImmutableSortedSet%601>|  
|Sada pro matematické funkce|<xref:System.Collections.Generic.HashSet%601><br /><br /> <xref:System.Collections.Generic.SortedSet%601>|Bez doporučení|<xref:System.Collections.Immutable.ImmutableHashSet%601><br /><br /> <xref:System.Collections.Immutable.ImmutableSortedSet%601>|  
  
<a name="BKMK_RelatedTopics"></a>   
## <a name="related-topics"></a>Související témata  
  
|Název|Popis|  
|-----------|-----------------|  
|[Výběr třídy kolekce](../../../docs/standard/collections/selecting-a-collection-class.md)|V této části najdete popis různých kolekcí a pomůže vám to vybrat pro váš scénář.|  
|[Běžně používané typy kolekcí](../../../docs/standard/collections/commonly-used-collection-types.md)|Popisuje běžně používané obecné a neobecné typy kolekce, například <xref:System.Array?displayProperty=nameWithType>, <xref:System.Collections.Generic.List%601?displayProperty=nameWithType>a <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType>.|  
|[Kdy použít generické kolekce](../../../docs/standard/collections/when-to-use-generic-collections.md)|Popisuje použití obecných typů kolekcí.|  
|[Porovnávání a řazení v kolekcích](../../../docs/standard/collections/comparisons-and-sorts-within-collections.md)|Popisuje použití porovnávání rovnosti a porovnávání řazení v kolekcích.|  
|[Typy řazených kolekcí](../../../docs/standard/collections/sorted-collection-types.md)|Popisuje výkon a charakteristiky seřazených kolekcí.|  
|[Typy kolekce Hashtable a Dictionary](../../../docs/standard/collections/hashtable-and-dictionary-collection-types.md)|Popisuje funkce obecných a neobecných typů slovníků založených na hodnotách hash.|  
|[Kolekce se zabezpečenými vlákny](../../../docs/standard/collections/thread-safe/index.md)|Popisuje typy kolekce, například <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType> a <xref:System.Collections.Concurrent.ConcurrentBag%601?displayProperty=nameWithType>, které podporují bezpečný a efektivní souběžný přístup z více vláken.|  
|System.Collections.Immutable|Zavádí neměnné kolekce a poskytuje odkazy na typy kolekcí.|  
  
<a name="BKMK_Reference"></a>   
## <a name="reference"></a>Odkaz  
 <xref:System.Array?displayProperty=nameWithType>  
 <xref:System.Collections?displayProperty=nameWithType>  
 <xref:System.Collections.Concurrent?displayProperty=nameWithType>  
 <xref:System.Collections.Generic?displayProperty=nameWithType>  
 <xref:System.Collections.Specialized?displayProperty=nameWithType>  
 <xref:System.Linq?displayProperty=nameWithType>  
 <xref:System.Collections.Immutable>
