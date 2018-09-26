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
ms.openlocfilehash: d84bc5ac2256139626311ff7c848170c28ffbd5b
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2018
ms.locfileid: "47087275"
---
# <a name="selecting-a-collection-class"></a>Výběr třídy kolekce
Je nutné pečlivě zvolit třídy kolekce. Pomocí nesprávného typu můžete omezit používání kolekce. Obecně platí, vyhněte se použití typů v <xref:System.Collections> obor názvů Pokud jsou specificky cílené na rozhraní .NET Framework verze 1.1. Obecné a souběžné verze kolekce jsou upřednostňovány kvůli jejich vyšší bezpečnost typů a dalších vylepšení.  
  
 Vezměte v úvahu následující otázky:  
  
-   Je třeba seznam sekvenční, kde prvek je obvykle odstraněn po jeho hodnota se načítá?  
  
    -   Pokud ano, zvažte použití <xref:System.Collections.Queue> třídy nebo <xref:System.Collections.Generic.Queue%601> obecnou třídu, pokud potřebujete first-in, chování FIFO (FIFO). Zvažte použití <xref:System.Collections.Stack> třídy nebo <xref:System.Collections.Generic.Stack%601> obecnou třídu, pokud potřebujete poslední dovnitř, první (ven LIFO) chování. Bezpečný přístup z více vláken, použít souběžné verze <xref:System.Collections.Concurrent.ConcurrentQueue%601> a <xref:System.Collections.Concurrent.ConcurrentStack%601>.  
  
    -   Pokud ne, zvažte použití jiné kolekce.  
  
-   Je potřeba pro přístup k prvkům v určitém pořadí, jako je například FIFO LIFO, nebo náhodného?  
  
    -   <xref:System.Collections.Queue> Třídy a <xref:System.Collections.Generic.Queue%601> nebo <xref:System.Collections.Concurrent.ConcurrentQueue%601> obecné třídy nabízejí FIFO přístup. Další informace najdete v tématu [kdy použít kolekci s bezpečnými vlákny](../../../docs/standard/collections/thread-safe/when-to-use-a-thread-safe-collection.md).  
  
    -   <xref:System.Collections.Stack> Třídy a <xref:System.Collections.Generic.Stack%601> nebo <xref:System.Collections.Concurrent.ConcurrentStack%601> obecné třídy nabízejí LIFO přístup. Další informace najdete v tématu [kdy použít kolekci s bezpečnými vlákny](../../../docs/standard/collections/thread-safe/when-to-use-a-thread-safe-collection.md).  
  
    -   <xref:System.Collections.Generic.LinkedList%601> Obecná třída umožňuje sekvenční přístup z první pozice na konci nebo od první pozice.  
  
-   Je potřeba pro přístup ke každému prvku podle indexu?  
  
    -   <xref:System.Collections.ArrayList> a <xref:System.Collections.Specialized.StringCollection> třídy a <xref:System.Collections.Generic.List%601> obecnou třídu nabídku přístupu k jejich prvky podle index elementu založený na nule.  
  
    -   <xref:System.Collections.Hashtable>, <xref:System.Collections.SortedList>, <xref:System.Collections.Specialized.ListDictionary>, A <xref:System.Collections.Specialized.StringDictionary> třídy a <xref:System.Collections.Generic.Dictionary%602> a <xref:System.Collections.Generic.SortedDictionary%602> obecné třídy nabízejí přístup k jejich prvky klíčem elementu.  
  
    -   <xref:System.Collections.Specialized.NameObjectCollectionBase> a <xref:System.Collections.Specialized.NameValueCollection> třídy a <xref:System.Collections.ObjectModel.KeyedCollection%602> a <xref:System.Collections.Generic.SortedList%602> obecné třídy nabízejí přístup k jejich prvky buď index založený na nule nebo klíč elementu.  
  
-   Každý element bude obsahovat jednu hodnotu, kombinaci jeden klíč a jednu hodnotu, nebo kombinací jeden klíč a více hodnot?  
  
    -   Jedna hodnota: použít některý z kolekcí založených na <xref:System.Collections.IList> rozhraní nebo <xref:System.Collections.Generic.IList%601> obecného rozhraní.  
  
    -   Jeden z klíčů a jedna hodnota: použít některý z kolekcí založených na <xref:System.Collections.IDictionary> rozhraní nebo <xref:System.Collections.Generic.IDictionary%602> obecného rozhraní.  
  
    -   Jednu hodnotu s vloženým klíčem: použití <xref:System.Collections.ObjectModel.KeyedCollection%602> obecnou třídu.  
  
    -   Jeden z klíčů a více hodnot: použití <xref:System.Collections.Specialized.NameValueCollection> třídy.  
  
-   Je třeba řadí prvky odlišně od jak byly zadány?  
  
    -   <xref:System.Collections.Hashtable> Třídy seřadí jeho prvky podle jejich kódů hash.  
  
    -   <xref:System.Collections.SortedList> Třídy a <xref:System.Collections.Generic.SortedDictionary%602> a <xref:System.Collections.Generic.SortedList%602> obecné třídy řadit podle klíče, jejich elementy na základě implementace <xref:System.Collections.IComparer> rozhraní a <xref:System.Collections.Generic.IComparer%601> obecného rozhraní.  
  
    -   <xref:System.Collections.ArrayList> poskytuje <xref:System.Collections.ArrayList.Sort%2A> metodu, která přebírá <xref:System.Collections.IComparer> implementace jako parametr. Jeho obecné protějšky <xref:System.Collections.Generic.List%601> poskytuje obecnou třídu <xref:System.Collections.Generic.List%601.Sort%2A> metodu, která přebírá implementace <xref:System.Collections.Generic.IComparer%601> obecné rozhraní jako parametr.  
  
-   Potřebujete rychle vyhledávat a načítání informací o?  
  
    -   <xref:System.Collections.Specialized.ListDictionary> je rychlejší než <xref:System.Collections.Hashtable> pro malé kolekce (10 položek nebo méně). <xref:System.Collections.Generic.Dictionary%602> Obecná třída poskytuje rychlejší vyhledávání, než <xref:System.Collections.Generic.SortedDictionary%602> obecnou třídu. Vícevláknová implementace je <xref:System.Collections.Concurrent.ConcurrentDictionary%602>. <xref:System.Collections.Concurrent.ConcurrentBag%601> poskytuje rychlé vkládání Vícevláknová pro neuspořádaná data. Další informace o obou vícevláknové typech naleznete v tématu [kdy použít kolekci s bezpečnými vlákny](../../../docs/standard/collections/thread-safe/when-to-use-a-thread-safe-collection.md).  
  
-   Je třeba kolekce, které přijímají pouze řetězce?  
  
    -   <xref:System.Collections.Specialized.StringCollection> (na základě <xref:System.Collections.IList>) a <xref:System.Collections.Specialized.StringDictionary> (na základě <xref:System.Collections.IDictionary>) jsou <xref:System.Collections.Specialized> oboru názvů.  
  
    -   Kromě toho můžete použít některý z obecné kolekce tříd v <xref:System.Collections.Generic> oboru názvů jako silně typované kolekce řetězec tak, že zadáte <xref:System.String> třídu pro své argumenty obecného typu.  
  
## <a name="linq-to-objects-and-plinq"></a>LINQ to Objects a PLINQ  
 LINQ na objekty umožňuje vývojářům používat dotazy LINQ pro přístup k objektům v paměti, dokud objektový typ implementuje <xref:System.Collections.IEnumerable> nebo <xref:System.Collections.Generic.IEnumerable%601>. Dotazy LINQ poskytují společný vzor pro přístup k datům, jsou obvykle stručnější a čitelnější než standardní `foreach` smyčky a poskytují filtrování, řazení a seskupování schopností. Další informace najdete v tématu [LINQ to Objects](https://msdn.microsoft.com/library/73cafe73-37cf-46e7-bfa7-97c7eea7ced9).  
  
 PLINQ poskytuje paralelní implementace LINQ na objekty, které můžou nabízet rychlejší provádění dotazu v mnoha scénářích zefektivnit tak využívání vícejádrových počítačích. Další informace najdete v tématu [paralelní LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Collections>  
- <xref:System.Collections.Specialized>  
- <xref:System.Collections.Generic>  
- [Kolekce se zabezpečenými vlákny](../../../docs/standard/collections/thread-safe/index.md)
