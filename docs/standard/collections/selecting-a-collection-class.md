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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "75711347"
---
# <a name="selecting-a-collection-class"></a>Výběr třídy kolekce

Ujistěte se, že si pečlivě vyberete třídu kolekce. Použití nesprávného typu může omezit vaše použití kolekce.  

> [!IMPORTANT]
> Nepoužívejte typy v <xref:System.Collections> oboru názvů. Obecné a souběžné verze kolekcí se doporučuje z důvodu jejich větší bezpečnost typů a další vylepšení.  

 Zvažte následující otázky:  
  
- Potřebujete sekvenční seznam, kde je prvek obvykle zahozen po načtení jeho hodnoty?  
  
  - Pokud ano, zvažte <xref:System.Collections.Queue> použití <xref:System.Collections.Generic.Queue%601> třídy nebo obecné třídy, pokud potřebujete první dovnitř, první ven (FIFO) chování. Zvažte <xref:System.Collections.Stack> použití třídy nebo <xref:System.Collections.Generic.Stack%601> obecné třídy, pokud potřebujete chování last-in, first-out (LIFO). Pro bezpečný přístup z více vláken použijte souběžné verze <xref:System.Collections.Concurrent.ConcurrentQueue%601> a <xref:System.Collections.Concurrent.ConcurrentStack%601>.  
  
  - Pokud ne, zvažte použití jiných kolekcí.  
  
- Potřebujete přístup k prvkům v určitém pořadí, například FIFO, LIFO nebo náhodné?  
  
  - Třída <xref:System.Collections.Queue> a <xref:System.Collections.Generic.Queue%601> nebo <xref:System.Collections.Concurrent.ConcurrentQueue%601> obecné třídy nabízejí přístup FIFO. Další informace naleznete v [tématu Kdy použít kolekci bezpečné pro přístup z více vláken](../../../docs/standard/collections/thread-safe/when-to-use-a-thread-safe-collection.md).  
  
  - Třída <xref:System.Collections.Stack> a <xref:System.Collections.Generic.Stack%601> nebo <xref:System.Collections.Concurrent.ConcurrentStack%601> obecné třídy nabízejí přístup LIFO. Další informace naleznete v [tématu Kdy použít kolekci bezpečné pro přístup z více vláken](../../../docs/standard/collections/thread-safe/when-to-use-a-thread-safe-collection.md).  
  
  - Obecná <xref:System.Collections.Generic.LinkedList%601> třída umožňuje sekvenční přístup buď od hlavy k ocasu, nebo od ocasu k hlavě.  
  
- Potřebujete přístup ke každému prvku podle indexu?  
  
  - A <xref:System.Collections.ArrayList> <xref:System.Collections.Specialized.StringCollection> třídy <xref:System.Collections.Generic.List%601> a obecné třídy nabízejí přístup k jejich prvky index založený na nule prvku.  
  
  - , <xref:System.Collections.Hashtable> <xref:System.Collections.SortedList>, <xref:System.Collections.Specialized.ListDictionary>a <xref:System.Collections.Specialized.StringDictionary> třídy <xref:System.Collections.Generic.Dictionary%602> a <xref:System.Collections.Generic.SortedDictionary%602> a obecné třídy nabízejí přístup k jejich prvky klíčem prvku.  
  
  - A <xref:System.Collections.Specialized.NameObjectCollectionBase> <xref:System.Collections.Specialized.NameValueCollection> třídy a <xref:System.Collections.ObjectModel.KeyedCollection%602> <xref:System.Collections.Generic.SortedList%602> a obecné třídy nabízejí přístup k jejich prvky index založený na nule nebo klíč prvku.  
  
- Bude každý prvek obsahovat jednu hodnotu, kombinaci jednoho klíče a jedné hodnoty nebo kombinaci jednoho klíče a více hodnot?  
  
  - Jedna hodnota: Použijte některou z <xref:System.Collections.IList> kolekcí <xref:System.Collections.Generic.IList%601> na základě rozhraní nebo obecné rozhraní.  
  
  - Jeden klíč a jedna hodnota: Použijte některou <xref:System.Collections.IDictionary> z <xref:System.Collections.Generic.IDictionary%602> kolekcí na základě rozhraní nebo obecné rozhraní.  
  
  - Jedna hodnota s vloženým <xref:System.Collections.ObjectModel.KeyedCollection%602> klíčem: Použijte obecnou třídu.  
  
  - Jeden klíč a více <xref:System.Collections.Specialized.NameValueCollection> hodnot: Použijte třídu.  
  
- Potřebujete třídit prvky jinak, než jak byly zadány?  
  
  - Třída <xref:System.Collections.Hashtable> seřadí své prvky podle jejich hash kódů.  
  
  - Třída <xref:System.Collections.SortedList> a <xref:System.Collections.Generic.SortedList%602> a <xref:System.Collections.Generic.SortedDictionary%602> obecné třídy seřazují jejich prvky podle klíče. Pořadí řazení je založeno na <xref:System.Collections.IComparer> implementaci rozhraní <xref:System.Collections.SortedList> pro třídu a <xref:System.Collections.Generic.IComparer%601> na implementaci <xref:System.Collections.Generic.SortedList%602> <xref:System.Collections.Generic.SortedDictionary%602> obecného rozhraní pro obecné třídy a. Ze dvou obecných <xref:System.Collections.Generic.SortedDictionary%602> typů nabízí <xref:System.Collections.Generic.SortedList%602>lepší <xref:System.Collections.Generic.SortedList%602> výkon než , zatímco spotřebovává méně paměti.  
  
  - <xref:System.Collections.ArrayList>poskytuje <xref:System.Collections.ArrayList.Sort%2A> metodu, <xref:System.Collections.IComparer> která bere implementaci jako parametr. Jeho obecný protějšek, <xref:System.Collections.Generic.List%601> obecná <xref:System.Collections.Generic.List%601.Sort%2A> třída, poskytuje metodu, která přebírá implementaci <xref:System.Collections.Generic.IComparer%601> obecného rozhraní jako parametr.  
  
- Potřebujete rychlé vyhledávání a vyhledávání informací?  
  
  - <xref:System.Collections.Specialized.ListDictionary>je rychlejší <xref:System.Collections.Hashtable> než u malých kolekcí (10 položek nebo méně). Obecná <xref:System.Collections.Generic.Dictionary%602> třída poskytuje rychlejší vyhledávání <xref:System.Collections.Generic.SortedDictionary%602> než obecná třída. Vícevláknová implementace je <xref:System.Collections.Concurrent.ConcurrentDictionary%602>. <xref:System.Collections.Concurrent.ConcurrentBag%601>poskytuje rychlé vložení více vlákny pro neuspořádaná data. Další informace o obou typech s více vlákny naleznete v [tématu When to Use a Thread-Safe Collection](../../../docs/standard/collections/thread-safe/when-to-use-a-thread-safe-collection.md).  
  
- Potřebujete kolekce, které přijímají pouze řetězce?  
  
  - <xref:System.Collections.Specialized.StringCollection>(na <xref:System.Collections.IList>základě <xref:System.Collections.Specialized.StringDictionary> ) a <xref:System.Collections.IDictionary>(na <xref:System.Collections.Specialized> základě) jsou v oboru názvů.  
  
  - Kromě toho můžete použít některou z obecných tříd kolekce v oboru <xref:System.Collections.Generic> názvů jako <xref:System.String> kolekce řetězců silného typu zadáním třídy pro jejich argumenty obecného typu. Můžete například deklarovat proměnnou typu [Řetězec\<seznamu>](xref:System.Collections.Generic.List%601) nebo Slovník<[řetězec,Řetězec>](xref:System.Collections.Generic.Dictionary%602).
  
## <a name="linq-to-objects-and-plinq"></a>LINQ k objektům a PLINQ  
 LINQ to Objects umožňuje vývojářům používat dotazy LINQ pro přístup k objektům v paměti, pokud typ objektu implementuje <xref:System.Collections.IEnumerable> nebo <xref:System.Collections.Generic.IEnumerable%601>. LINQ dotazy poskytují společný vzor pro přístup k datům, jsou obvykle `foreach` stručnější a čitelnější než standardní smyčky a poskytují možnosti filtrování, řazení a seskupování. Další informace naleznete [v tématu LINQ na objekty (C#)](../../csharp/programming-guide/concepts/linq/linq-to-objects.md) a [LINQ na objekty (Visual Basic).](../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)  
  
 PLINQ poskytuje paralelní implementaci LINQ na objekty, které mohou nabídnout rychlejší provádění dotazů v mnoha scénářích, a to prostřednictvím efektivnějšího využití vícejádrových počítačů. Další informace naleznete [v tématu Paralelní LINQ (PLINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md).  
  
## <a name="see-also"></a>Viz také

- <xref:System.Collections>
- <xref:System.Collections.Specialized>
- <xref:System.Collections.Generic>
- [Kolekce se zabezpečenými vlákny](../../../docs/standard/collections/thread-safe/index.md)
