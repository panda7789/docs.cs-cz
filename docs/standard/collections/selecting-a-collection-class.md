---
title: Výběr třídy kolekce
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- last-in-first-out collections
- first-in-first-out collections
- collections [.NET Framework], selecting collection class
- indexed collections
- Collections classes
- grouping data in collections, selecting collection class
ms.assetid: ba049f9a-ce87-4cc4-b319-3f75c8ddac8a
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9d51f6c8e7dc03edb2823f61ab638fc669847dd6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33574930"
---
# <a name="selecting-a-collection-class"></a>Výběr třídy kolekce
Ujistěte se, že pečlivě zvolte třídě kolekce. Pomocí nesprávného typu může omezit použití kolekce. Obecně platí, nepoužívejte typy v <xref:System.Collections> obor názvů Pokud jsou konkrétně cílení na rozhraní .NET Framework verze 1.1. Obecné a souběžné verze kolekcí jsou upřednostňované z důvodu jejich vyšší bezpečnost typů a dalších vylepšení.  
  
 Zvažte následující otázky:  
  
-   Potřebujete seznam sekvenční, kde element obvykle odstraněn po načtení jeho hodnoty?  
  
    -   Pokud ano, zvažte použití <xref:System.Collections.Queue> třídy nebo <xref:System.Collections.Generic.Queue%601> obecné třídy, pokud potřebujete first in, chování použity. Zvažte použití <xref:System.Collections.Stack> třídy nebo <xref:System.Collections.Generic.Stack%601> obecné třídy, pokud potřebujete last-in, první ven (LIFO) chování. Pro bezpečný přístup z více vláken, použijte souběžné verze <xref:System.Collections.Concurrent.ConcurrentQueue%601> a <xref:System.Collections.Concurrent.ConcurrentStack%601>.  
  
    -   Pokud ne, zvažte použití jiné kolekce.  
  
-   Potřebujete přístup k elementům v určitém pořadí, jako je například FIFO, LIFO, nebo náhodné?  
  
    -   <xref:System.Collections.Queue> Třídy a <xref:System.Collections.Generic.Queue%601> nebo <xref:System.Collections.Concurrent.ConcurrentQueue%601> obecná třída nabízí přístup FIFO. Další informace najdete v tématu [kdy použít kolekci s bezpečnými vlákny](../../../docs/standard/collections/thread-safe/when-to-use-a-thread-safe-collection.md).  
  
    -   <xref:System.Collections.Stack> Třídy a <xref:System.Collections.Generic.Stack%601> nebo <xref:System.Collections.Concurrent.ConcurrentStack%601> obecná třída nabízí přístup LIFO. Další informace najdete v tématu [kdy použít kolekci s bezpečnými vlákny](../../../docs/standard/collections/thread-safe/when-to-use-a-thread-safe-collection.md).  
  
    -   <xref:System.Collections.Generic.LinkedList%601> Obecná třída umožňuje sekvenční přístup ze začátku na konec nebo z tail do hlavičky.  
  
-   Potřebujete přístup každý prvek index?  
  
    -   <xref:System.Collections.ArrayList> a <xref:System.Collections.Specialized.StringCollection> třídy a <xref:System.Collections.Generic.List%601> – obecná třída nabídka přístup k jejich elementů podle index elementu založený na nule.  
  
    -   <xref:System.Collections.Hashtable>, <xref:System.Collections.SortedList>, <xref:System.Collections.Specialized.ListDictionary>, A <xref:System.Collections.Specialized.StringDictionary> třídy a <xref:System.Collections.Generic.Dictionary%602> a <xref:System.Collections.Generic.SortedDictionary%602> obecné třídy nabízí přístup k jejich elementům pomocí klíče elementu.  
  
    -   <xref:System.Collections.Specialized.NameObjectCollectionBase> a <xref:System.Collections.Specialized.NameValueCollection> třídy a <xref:System.Collections.ObjectModel.KeyedCollection%602> a <xref:System.Collections.Generic.SortedList%602> obecné třídy nabízí přístup k jejich elementů buď index založený na nule nebo klíč elementu.  
  
-   Každý prvek bude obsahovat jednu hodnotu, kombinace jeden klíč a jednu hodnotu, nebo kombinací jeden klíč a více hodnot?  
  
    -   Jednu hodnotu: použijte některou z kolekce, na základě <xref:System.Collections.IList> rozhraní nebo <xref:System.Collections.Generic.IList%601> obecné rozhraní.  
  
    -   Jeden klíč a jednu hodnotu: použijte některou z kolekce, na základě <xref:System.Collections.IDictionary> rozhraní nebo <xref:System.Collections.Generic.IDictionary%602> obecné rozhraní.  
  
    -   Jednu hodnotu s vloženým klíčem: použití <xref:System.Collections.ObjectModel.KeyedCollection%602> obecná třída.  
  
    -   Jeden klíč a více hodnot: použití <xref:System.Collections.Specialized.NameValueCollection> třídy.  
  
-   Je třeba seřadit prvky jinak, než jak byly zadány?  
  
    -   <xref:System.Collections.Hashtable> Třída seřadí její prvky podle jejich hash.  
  
    -   <xref:System.Collections.SortedList> Třídy a <xref:System.Collections.Generic.SortedDictionary%602> a <xref:System.Collections.Generic.SortedList%602> obecné třídy řadit jejich elementy pomocí klíče, na základě implementace <xref:System.Collections.IComparer> rozhraní a <xref:System.Collections.Generic.IComparer%601> obecné rozhraní.  
  
    -   <xref:System.Collections.ArrayList> poskytuje <xref:System.Collections.ArrayList.Sort%2A> metody, která použije <xref:System.Collections.IComparer> implementace jako parametr. Jeho obecný protějšek <xref:System.Collections.Generic.List%601> obecná třída poskytuje <xref:System.Collections.Generic.List%601.Sort%2A> metoda, která přebírá implementaci <xref:System.Collections.Generic.IComparer%601> obecné rozhraní jako parametr.  
  
-   Potřebujete rychle vyhledávat a načítat informace?  
  
    -   <xref:System.Collections.Specialized.ListDictionary> je rychlejší než <xref:System.Collections.Hashtable> pro kolekce malé (10 položek nebo méně). <xref:System.Collections.Generic.Dictionary%602> Obecná třída poskytuje rychlejší vyhledávání, než <xref:System.Collections.Generic.SortedDictionary%602> obecná třída. Vícevláknová implementace je <xref:System.Collections.Concurrent.ConcurrentDictionary%602>. <xref:System.Collections.Concurrent.ConcurrentBag%601> poskytuje rychlé vícevláknové vkládání pro neuspořádaný data. Další informace o obou vícevláknových typech najdete v tématu [kdy použít kolekci s bezpečnými vlákny](../../../docs/standard/collections/thread-safe/when-to-use-a-thread-safe-collection.md).  
  
-   Potřebujete kolekce, které přijímají pouze řetězce?  
  
    -   <xref:System.Collections.Specialized.StringCollection> (na základě <xref:System.Collections.IList>) a <xref:System.Collections.Specialized.StringDictionary> (na základě <xref:System.Collections.IDictionary>) jsou v <xref:System.Collections.Specialized> oboru názvů.  
  
    -   Kromě toho můžete použít jakékoli třídy obecnou kolekci v <xref:System.Collections.Generic> oboru názvů jako silného typu řetězec kolekce tak, že zadáte <xref:System.String> třídy pro jejich argumenty obecného typu.  
  
## <a name="linq-to-objects-and-plinq"></a>LINQ na objekty a PLINQ  
 LINQ na objekty umožňuje vývojářům používat dotazy LINQ pro přístup k objektům v paměti, dokud typ objektu implementuje <xref:System.Collections.IEnumerable> nebo <xref:System.Collections.Generic.IEnumerable%601>. Dotazy LINQ poskytují společný vzorek pro přístup k datům, jsou obvykle více stručná a čitelná než standardní `foreach` v cyklu a poskytují filtrování, řazení a seskupování schopností. Další informace najdete v tématu [LINQ na objekty](https://msdn.microsoft.com/library/73cafe73-37cf-46e7-bfa7-97c7eea7ced9).  
  
 PLINQ poskytuje paralelní provádění LINQ na objekty, které nabízejí rychlejší spuštění dotazu v mnoha scénářích efektivněji využívat počítačů s více jádry. Další informace najdete v tématu [paralelní LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Collections>  
 <xref:System.Collections.Specialized>  
 <xref:System.Collections.Generic>  
 [Kolekce se zabezpečenými vlákny](../../../docs/standard/collections/thread-safe/index.md)
