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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 21c708f63faaedb9fbce60d7e4aef314f7a41ef8
ms.sourcegitcommit: 462dc41a13942e467984e48f4018d1f79ae67346
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/19/2019
ms.locfileid: "58185555"
---
# <a name="selecting-a-collection-class"></a>Výběr třídy kolekce

Je nutné pečlivě zvolit třídy kolekce. Pomocí nesprávného typu můžete omezit používání kolekce.  

> [!IMPORTANT]
> Vyhněte se použití typů v <xref:System.Collections> oboru názvů. Obecné a souběžné verze kolekce se doporučuje kvůli jejich vyšší bezpečnost typů a dalších vylepšení.  

 Vezměte v úvahu následující otázky:  
  
- Je třeba seznam sekvenční, kde prvek je obvykle odstraněn po jeho hodnota se načítá?  
  
  - Pokud ano, zvažte použití <xref:System.Collections.Queue> třídy nebo <xref:System.Collections.Generic.Queue%601> obecnou třídu, pokud potřebujete first-in, chování FIFO (FIFO). Zvažte použití <xref:System.Collections.Stack> třídy nebo <xref:System.Collections.Generic.Stack%601> obecnou třídu, pokud potřebujete poslední dovnitř, první (ven LIFO) chování. Bezpečný přístup z více vláken, použít souběžné verze <xref:System.Collections.Concurrent.ConcurrentQueue%601> a <xref:System.Collections.Concurrent.ConcurrentStack%601>.  
  
  - Pokud ne, zvažte použití jiné kolekce.  
  
- Je potřeba pro přístup k prvkům v určitém pořadí, jako je například FIFO LIFO, nebo náhodného?  
  
  - <xref:System.Collections.Queue> Třídy a <xref:System.Collections.Generic.Queue%601> nebo <xref:System.Collections.Concurrent.ConcurrentQueue%601> obecné třídy nabízejí FIFO přístup. Další informace najdete v tématu [kdy použít kolekci s bezpečnými vlákny](../../../docs/standard/collections/thread-safe/when-to-use-a-thread-safe-collection.md).  
  
  - <xref:System.Collections.Stack> Třídy a <xref:System.Collections.Generic.Stack%601> nebo <xref:System.Collections.Concurrent.ConcurrentStack%601> obecné třídy nabízejí LIFO přístup. Další informace najdete v tématu [kdy použít kolekci s bezpečnými vlákny](../../../docs/standard/collections/thread-safe/when-to-use-a-thread-safe-collection.md).  
  
  - <xref:System.Collections.Generic.LinkedList%601> Obecná třída umožňuje sekvenční přístup z první pozice na konci nebo od první pozice.  
  
- Je potřeba pro přístup ke každému prvku podle indexu?  
  
  - <xref:System.Collections.ArrayList> a <xref:System.Collections.Specialized.StringCollection> třídy a <xref:System.Collections.Generic.List%601> obecnou třídu nabídku přístupu k jejich prvky podle index elementu založený na nule.  
  
  - <xref:System.Collections.Hashtable>, <xref:System.Collections.SortedList>, <xref:System.Collections.Specialized.ListDictionary>, A <xref:System.Collections.Specialized.StringDictionary> třídy a <xref:System.Collections.Generic.Dictionary%602> a <xref:System.Collections.Generic.SortedDictionary%602> obecné třídy nabízejí přístup k jejich prvky klíčem elementu.  
  
  - <xref:System.Collections.Specialized.NameObjectCollectionBase> a <xref:System.Collections.Specialized.NameValueCollection> třídy a <xref:System.Collections.ObjectModel.KeyedCollection%602> a <xref:System.Collections.Generic.SortedList%602> obecné třídy nabízejí přístup k jejich prvky buď index založený na nule nebo klíč elementu.  
  
- Každý element bude obsahovat jednu hodnotu, kombinaci jeden klíč a jednu hodnotu, nebo kombinací jeden klíč a více hodnot?  
  
  - Jedna hodnota: Použít některý z kolekcí založených na <xref:System.Collections.IList> rozhraní nebo <xref:System.Collections.Generic.IList%601> obecného rozhraní.  
  
  - Jeden z klíčů a jedna hodnota: Použít některý z kolekcí založených na <xref:System.Collections.IDictionary> rozhraní nebo <xref:System.Collections.Generic.IDictionary%602> obecného rozhraní.  
  
  - Jednu hodnotu s vloženým klíčem: Použití <xref:System.Collections.ObjectModel.KeyedCollection%602> obecnou třídu.  
  
  - Jeden z klíčů a více hodnot: Použití <xref:System.Collections.Specialized.NameValueCollection> třídy.  
  
- Je třeba řadí prvky odlišně od jak byly zadány?  
  
  - <xref:System.Collections.Hashtable> Třídy seřadí jeho prvky podle jejich kódů hash.  
  
  - <xref:System.Collections.SortedList> Třídy a <xref:System.Collections.Generic.SortedList%602> a <xref:System.Collections.Generic.SortedDictionary%602> obecné třídy řadit jejich prvky podle klíče. Pořadí řazení je založena na implementaci <xref:System.Collections.IComparer> rozhraní <xref:System.Collections.SortedList> třídy a v provádění <xref:System.Collections.Generic.IComparer%601> obecné rozhraní pro <xref:System.Collections.Generic.SortedList%602> a <xref:System.Collections.Generic.SortedDictionary%602> obecné třídy. Dva obecných typů <xref:System.Collections.Generic.SortedDictionary%602> nabízí vyšší výkon než <xref:System.Collections.Generic.SortedList%602>, zatímco <xref:System.Collections.Generic.SortedList%602> využívá méně paměti.  
  
  - <xref:System.Collections.ArrayList> poskytuje <xref:System.Collections.ArrayList.Sort%2A> metodu, která přebírá <xref:System.Collections.IComparer> implementace jako parametr. Jeho obecné protějšky <xref:System.Collections.Generic.List%601> poskytuje obecnou třídu <xref:System.Collections.Generic.List%601.Sort%2A> metodu, která přebírá implementace <xref:System.Collections.Generic.IComparer%601> obecné rozhraní jako parametr.  
  
- Potřebujete rychle vyhledávat a načítání informací o?  
  
  - <xref:System.Collections.Specialized.ListDictionary> je rychlejší než <xref:System.Collections.Hashtable> pro malé kolekce (10 položek nebo méně). <xref:System.Collections.Generic.Dictionary%602> Obecná třída poskytuje rychlejší vyhledávání, než <xref:System.Collections.Generic.SortedDictionary%602> obecnou třídu. Vícevláknová implementace je <xref:System.Collections.Concurrent.ConcurrentDictionary%602>. <xref:System.Collections.Concurrent.ConcurrentBag%601> poskytuje rychlé vkládání Vícevláknová pro neuspořádaná data. Další informace o obou vícevláknové typech naleznete v tématu [kdy použít kolekci s bezpečnými vlákny](../../../docs/standard/collections/thread-safe/when-to-use-a-thread-safe-collection.md).  
  
- Je třeba kolekce, které přijímají pouze řetězce?  
  
  - <xref:System.Collections.Specialized.StringCollection> (na základě <xref:System.Collections.IList>) a <xref:System.Collections.Specialized.StringDictionary> (na základě <xref:System.Collections.IDictionary>) jsou <xref:System.Collections.Specialized> oboru názvů.  
  
  - Kromě toho můžete použít některý z obecné kolekce tříd v <xref:System.Collections.Generic> oboru názvů jako silně typované kolekce řetězec tak, že zadáte <xref:System.String> třídu pro své argumenty obecného typu. Například můžete deklarovat proměnnou typu [seznamu\<řetězec >](xref:System.Collections.Generic.List%601) nebo [Dictionary < String, String >](xref:System.Collections.Generic.Dictionary%602).
  
## <a name="linq-to-objects-and-plinq"></a>LINQ to Objects a PLINQ  
 LINQ na objekty umožňuje vývojářům používat dotazy LINQ pro přístup k objektům v paměti, dokud objektový typ implementuje <xref:System.Collections.IEnumerable> nebo <xref:System.Collections.Generic.IEnumerable%601>. Dotazy LINQ poskytují společný vzor pro přístup k datům, jsou obvykle stručnější a čitelnější než standardní `foreach` smyčky a poskytují filtrování, řazení a seskupování schopností. Další informace najdete v tématu [LINQ to Objects (C#)](../../csharp/programming-guide/concepts/linq/linq-to-objects.md) a [LINQ to Objects (Visual Basic)](../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md).  
  
 PLINQ poskytuje paralelní implementace LINQ na objekty, které můžou nabízet rychlejší provádění dotazu v mnoha scénářích zefektivnit tak využívání vícejádrových počítačích. Další informace najdete v tématu [paralelní LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Collections>
- <xref:System.Collections.Specialized>
- <xref:System.Collections.Generic>
- [Kolekce se zabezpečenými vlákny](../../../docs/standard/collections/thread-safe/index.md)
