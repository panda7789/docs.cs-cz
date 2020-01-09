---
title: Výběr třídy kolekce
ms.date: 03/18/2019
ms.technology: dotnet-standard
helpviewer_keywords:
- last-in-first-out collections
- first-in-first-out collections
- collections [.NET Framework], selecting collection class
- indexed collections
- Collections classes
- grouping data in collections, selecting collection class
ms.assetid: ba049f9a-ce87-4cc4-b319-3f75c8ddac8a
ms.openlocfilehash: fb03200c810290c970f7aa56a0e15d385aca7ca8
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75711347"
---
# <a name="selecting-a-collection-class"></a>Výběr třídy kolekce

Nezapomeňte si pečlivě zvolit třídu kolekce. Použití nesprávného typu může omezit použití kolekce.  

> [!IMPORTANT]
> Nepoužívejte typy v oboru názvů <xref:System.Collections>. Obecné a souběžné verze kolekcí se doporučují z důvodu jejich vyšší bezpečnosti typu a dalších vylepšení.  

 Zvažte následující otázky:  
  
- Potřebujete sekvenční seznam, ve kterém je element obvykle zahozen po načtení jeho hodnoty?  
  
  - Pokud ano, zvažte použití <xref:System.Collections.Queue> třídy nebo <xref:System.Collections.Generic.Queue%601> obecné třídy, pokud potřebujete chování first-in a First-out (FIFO). Zvažte použití třídy <xref:System.Collections.Stack> nebo obecné třídy <xref:System.Collections.Generic.Stack%601>, pokud potřebujete chování za poslední, první ven (LIFO). Pro bezpečný přístup z více vláken použijte souběžné verze <xref:System.Collections.Concurrent.ConcurrentQueue%601> a <xref:System.Collections.Concurrent.ConcurrentStack%601>.  
  
  - V takovém případě zvažte použití dalších kolekcí.  
  
- Potřebujete získat přístup k prvkům v určitém pořadí, jako je například FIFO, LIFO nebo Random?  
  
  - Třída <xref:System.Collections.Queue> a obecná třída <xref:System.Collections.Generic.Queue%601> nebo <xref:System.Collections.Concurrent.ConcurrentQueue%601> nabízí přístup k aplikaci FIFO. Další informace najdete v tématu [kdy použít kolekci bezpečnou pro přístup z více vláken](../../../docs/standard/collections/thread-safe/when-to-use-a-thread-safe-collection.md).  
  
  - Třída <xref:System.Collections.Stack> a obecná třída <xref:System.Collections.Generic.Stack%601> nebo <xref:System.Collections.Concurrent.ConcurrentStack%601> nabízí přístup LIFO. Další informace najdete v tématu [kdy použít kolekci bezpečnou pro přístup z více vláken](../../../docs/standard/collections/thread-safe/when-to-use-a-thread-safe-collection.md).  
  
  - <xref:System.Collections.Generic.LinkedList%601> obecná třída umožňuje sekvenční přístup buď od pozice k zakončení, nebo od konce až po hlavní.  
  
- Potřebujete ke každému elementu přistupovat podle indexu?  
  
  - Třídy <xref:System.Collections.ArrayList> a <xref:System.Collections.Specialized.StringCollection> a <xref:System.Collections.Generic.List%601> obecná třída nabízejí přístup k jejich elementům pomocí indexu založeného na nule elementu.  
  
  - Třídy <xref:System.Collections.Hashtable>, <xref:System.Collections.SortedList>, <xref:System.Collections.Specialized.ListDictionary>a <xref:System.Collections.Specialized.StringDictionary> a obecné třídy <xref:System.Collections.Generic.Dictionary%602> a <xref:System.Collections.Generic.SortedDictionary%602> nabízejí přístup ke svým prvkům pomocí klíče elementu.  
  
  - Třídy <xref:System.Collections.Specialized.NameObjectCollectionBase> a <xref:System.Collections.Specialized.NameValueCollection> a obecné třídy <xref:System.Collections.ObjectModel.KeyedCollection%602> a <xref:System.Collections.Generic.SortedList%602> nabízejí přístup k jejich elementům buď pomocí indexu založeného na nule, nebo klíče elementu.  
  
- Bude každý prvek obsahovat jednu hodnotu, kombinaci jednoho klíče a jednu hodnotu nebo kombinaci jednoho klíče a více hodnot?  
  
  - Jedna hodnota: použijte jakoukoli kolekci založenou na rozhraní <xref:System.Collections.IList> nebo <xref:System.Collections.Generic.IList%601> obecné rozhraní.  
  
  - Jedna klávesa a jedna hodnota: použijte jakoukoli kolekci založenou na rozhraní <xref:System.Collections.IDictionary> nebo <xref:System.Collections.Generic.IDictionary%602> obecném rozhraní.  
  
  - Jedna hodnota s vloženým klíčem: Použijte obecnou třídu <xref:System.Collections.ObjectModel.KeyedCollection%602>.  
  
  - Jeden klíč a více hodnot: použijte třídu <xref:System.Collections.Specialized.NameValueCollection>.  
  
- Je nutné prvky seřadit jinak, než byly zadány?  
  
  - Třída <xref:System.Collections.Hashtable> seřadí své prvky podle jejich kódů hash.  
  
  - Třída <xref:System.Collections.SortedList> a obecné třídy <xref:System.Collections.Generic.SortedList%602> a <xref:System.Collections.Generic.SortedDictionary%602> seřadí jejich prvky pomocí klíče. Pořadí řazení je založeno na implementaci rozhraní <xref:System.Collections.IComparer> pro třídu <xref:System.Collections.SortedList> a implementaci <xref:System.Collections.Generic.IComparer%601> obecné rozhraní pro <xref:System.Collections.Generic.SortedList%602> a <xref:System.Collections.Generic.SortedDictionary%602> obecné třídy. Ze dvou obecných typů <xref:System.Collections.Generic.SortedDictionary%602> nabízí lepší výkon než <xref:System.Collections.Generic.SortedList%602>, zatímco <xref:System.Collections.Generic.SortedList%602> spotřebovává méně paměti.  
  
  - <xref:System.Collections.ArrayList> poskytuje metodu <xref:System.Collections.ArrayList.Sort%2A>, která přebírá <xref:System.Collections.IComparer> implementaci jako parametr. Jeho obecný protějšek, <xref:System.Collections.Generic.List%601> obecná třída, poskytuje metodu <xref:System.Collections.Generic.List%601.Sort%2A>, která přebírá implementaci <xref:System.Collections.Generic.IComparer%601> obecného rozhraní jako parametr.  
  
- Potřebujete rychle vyhledávat a načítat informace?  
  
  - <xref:System.Collections.Specialized.ListDictionary> je rychlejší než <xref:System.Collections.Hashtable> pro malé kolekce (10 položek nebo méně). <xref:System.Collections.Generic.Dictionary%602> obecná třída poskytuje rychlejší vyhledávání než <xref:System.Collections.Generic.SortedDictionary%602> obecná třída. Implementace s více vlákny je <xref:System.Collections.Concurrent.ConcurrentDictionary%602>. <xref:System.Collections.Concurrent.ConcurrentBag%601> poskytuje rychlé vícevláknové vkládání pro Neseřazená data. Další informace o vícevláknových typech naleznete v tématu [kdy použít kolekci bezpečnou pro přístup z více vláken](../../../docs/standard/collections/thread-safe/when-to-use-a-thread-safe-collection.md).  
  
- Potřebujete kolekce, které přijímají pouze řetězce?  
  
  - <xref:System.Collections.Specialized.StringCollection> (na základě <xref:System.Collections.IList>) a <xref:System.Collections.Specialized.StringDictionary> (na základě <xref:System.Collections.IDictionary>) jsou v oboru názvů <xref:System.Collections.Specialized>.  
  
  - Kromě toho můžete použít libovolnou z obecných tříd kolekce v oboru názvů <xref:System.Collections.Generic> jako kolekce řetězců silného typu zadáním <xref:System.String> třídy pro jejich argumenty obecného typu. Například můžete deklarovat proměnnou, která má být typu [seznam\<řetězec >](xref:System.Collections.Generic.List%601) nebo [Dictionary < string, String >](xref:System.Collections.Generic.Dictionary%602).
  
## <a name="linq-to-objects-and-plinq"></a>LINQ to Objects a PLINQ  
 LINQ to Objects umožňuje vývojářům používat dotazy LINQ pro přístup k objektům v paměti, pokud typ objektu implementuje <xref:System.Collections.IEnumerable> nebo <xref:System.Collections.Generic.IEnumerable%601>. Dotazy LINQ poskytují společný vzor pro přístup k datům, jsou obvykle stručnější a čitelné než standardní `foreach` smyčky a poskytují možnosti filtrování, řazení a seskupování. Další informace najdete v tématu [LINQ to Objects (C#)](../../csharp/programming-guide/concepts/linq/linq-to-objects.md) a [LINQ to Objects (Visual Basic)](../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md).  
  
 PLINQ poskytuje paralelní implementaci LINQ to Objects, která může nabízet rychlejší provádění dotazů v mnoha scénářích, a to díky efektivnějšímu využívání vícejádrových počítačů. Další informace naleznete v tématu [PARALLEL LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Collections>
- <xref:System.Collections.Specialized>
- <xref:System.Collections.Generic>
- [Kolekce se zabezpečenými vlákny](../../../docs/standard/collections/thread-safe/index.md)
