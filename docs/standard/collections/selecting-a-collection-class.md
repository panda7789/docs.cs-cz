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
ms.openlocfilehash: d79f1ca0d264a5a17306bb66f285b6fbe6b4e7ca
ms.sourcegitcommit: 7370aa8203b6036cea1520021b5511d0fd994574
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/02/2020
ms.locfileid: "82728485"
---
# <a name="selecting-a-collection-class"></a>Výběr třídy kolekce

Nezapomeňte si pečlivě zvolit třídu kolekce. Použití nesprávného typu může omezit použití kolekce.

> [!IMPORTANT]
> Vyhněte se použití typů v <xref:System.Collections> oboru názvů. Obecné a souběžné verze kolekcí se doporučují z důvodu jejich vyšší bezpečnosti typu a dalších vylepšení.

Zvažte následující otázky:

- Potřebujete sekvenční seznam, ve kterém je element obvykle zahozen po načtení jeho hodnoty?

  - Pokud ano, zvažte použití <xref:System.Collections.Queue> třídy nebo <xref:System.Collections.Generic.Queue%601> obecné třídy, pokud potřebujete chování first-in, First-out (FIFO). Zvažte použití <xref:System.Collections.Stack> třídy nebo <xref:System.Collections.Generic.Stack%601> obecné třídy, pokud potřebujete chování za poslední, první ven (LIFO). Pro bezpečný přístup z více vláken použijte souběžné verze <xref:System.Collections.Concurrent.ConcurrentQueue%601> a. <xref:System.Collections.Concurrent.ConcurrentStack%601> V případě neměnnosti zvažte neměnné verze <xref:System.Collections.Immutable.ImmutableQueue%601> a. <xref:System.Collections.Immutable.ImmutableStack%601>

  - V takovém případě zvažte použití dalších kolekcí.

- Potřebujete získat přístup k prvkům v určitém pořadí, jako je například FIFO, LIFO nebo Random?

  - <xref:System.Collections.Queue> Třída, jakož i obecné třídy <xref:System.Collections.Generic.Queue%601>, <xref:System.Collections.Concurrent.ConcurrentQueue%601>a <xref:System.Collections.Immutable.ImmutableQueue%601> , nabízí přístup FIFO. Další informace najdete v tématu [kdy použít kolekci bezpečnou pro přístup z více vláken](../../../docs/standard/collections/thread-safe/when-to-use-a-thread-safe-collection.md).

  - <xref:System.Collections.Stack> Třída, stejně jako <xref:System.Collections.Generic.Stack%601>, a <xref:System.Collections.Immutable.ImmutableStack%601> obecné třídy <xref:System.Collections.Concurrent.ConcurrentStack%601>, nabízí přístup LIFO. Další informace najdete v tématu [kdy použít kolekci bezpečnou pro přístup z více vláken](../../../docs/standard/collections/thread-safe/when-to-use-a-thread-safe-collection.md).

  - <xref:System.Collections.Generic.LinkedList%601> Obecná třída umožňuje sekvenční přístup buď od pozice k zakončení, nebo od konce k hlavnímu.

- Potřebujete ke každému elementu přistupovat podle indexu?

  - Třídy <xref:System.Collections.ArrayList> a <xref:System.Collections.Specialized.StringCollection> a <xref:System.Collections.Generic.List%601> obecná třída nabízejí přístup k jejich elementům pomocí indexu založeného na nule elementu. V případě neměnnosti zvažte neměnné obecné verze <xref:System.Collections.Immutable.ImmutableArray%601> a. <xref:System.Collections.Immutable.ImmutableList%601>

  - <xref:System.Collections.Hashtable> <xref:System.Collections.Generic.Dictionary%602> Třídy,, a a <xref:System.Collections.Generic.SortedDictionary%602> obecné třídy nabízejí přístup k jejich elementům pomocí klíče elementu. <xref:System.Collections.SortedList> <xref:System.Collections.Specialized.ListDictionary> <xref:System.Collections.Specialized.StringDictionary> Kromě toho existují neměnné verze několika odpovídajících typů <xref:System.Collections.Immutable.ImmutableHashSet%601>:, <xref:System.Collections.Immutable.ImmutableDictionary%602>, <xref:System.Collections.Immutable.ImmutableSortedSet%601>a. <xref:System.Collections.Immutable.ImmutableSortedDictionary%602>

  - Třídy <xref:System.Collections.Specialized.NameObjectCollectionBase> <xref:System.Collections.ObjectModel.KeyedCollection%602> <xref:System.Collections.Generic.SortedList%602> a <xref:System.Collections.Specialized.NameValueCollection> a obecné třídy nabízejí přístup k jejich elementům buď pomocí indexu založeného na nule, nebo klíče elementu.

- Bude každý prvek obsahovat jednu hodnotu, kombinaci jednoho klíče a jednu hodnotu nebo kombinaci jednoho klíče a více hodnot?

  - Jedna hodnota: použijte jakoukoli kolekci založenou na <xref:System.Collections.IList> rozhraní nebo <xref:System.Collections.Generic.IList%601> obecném rozhraní. Pro neměnné možnosti zvažte <xref:System.Collections.Immutable.IImmutableList%601> obecné rozhraní.

  - Jedna klávesa a jedna hodnota: použijte jakoukoli kolekci založenou na <xref:System.Collections.IDictionary> rozhraní nebo <xref:System.Collections.Generic.IDictionary%602> obecném rozhraní. Pro neměnné možnosti zvažte Obecná rozhraní <xref:System.Collections.Immutable.IImmutableSet%601> nebo. <xref:System.Collections.Immutable.IImmutableDictionary%602>

  - Jedna hodnota s vloženým klíčem: použijte <xref:System.Collections.ObjectModel.KeyedCollection%602> obecnou třídu.

  - Jeden klíč a více hodnot: použijte <xref:System.Collections.Specialized.NameValueCollection> třídu.

- Je nutné prvky seřadit jinak, než byly zadány?

  - <xref:System.Collections.Hashtable> Třída seřadí své prvky podle jejich kódů hash.

  - <xref:System.Collections.SortedList> Třída a <xref:System.Collections.Generic.SortedList%602> <xref:System.Collections.Generic.SortedDictionary%602> obecné třídy seřadí jejich prvky podle klíče. Pořadí řazení je založeno <xref:System.Collections.IComparer> na implementaci rozhraní pro <xref:System.Collections.SortedList> třídu a implementaci <xref:System.Collections.Generic.IComparer%601> obecného rozhraní pro obecné třídy <xref:System.Collections.Generic.SortedList%602> a. <xref:System.Collections.Generic.SortedDictionary%602> Ze dvou obecných typů <xref:System.Collections.Generic.SortedDictionary%602> nabízí lepší výkon než <xref:System.Collections.Generic.SortedList%602>, zatímco <xref:System.Collections.Generic.SortedList%602> spotřebovává méně paměti.

  - <xref:System.Collections.ArrayList>poskytuje <xref:System.Collections.ArrayList.Sort%2A> metodu, která přijímá <xref:System.Collections.IComparer> implementaci jako parametr. Jeho obecný protějšek, <xref:System.Collections.Generic.List%601> obecná třída, poskytuje <xref:System.Collections.Generic.List%601.Sort%2A> metodu, která přebírá implementaci <xref:System.Collections.Generic.IComparer%601> obecného rozhraní jako parametr.

- Potřebujete rychle vyhledávat a načítat informace?

  - <xref:System.Collections.Specialized.ListDictionary>je rychlejší než <xref:System.Collections.Hashtable> u malých kolekcí (10 položek nebo méně). <xref:System.Collections.Generic.Dictionary%602> Obecná třída poskytuje rychlejší vyhledávání než <xref:System.Collections.Generic.SortedDictionary%602> obecná třída. Vícevláknová implementace je <xref:System.Collections.Concurrent.ConcurrentDictionary%602>. <xref:System.Collections.Concurrent.ConcurrentBag%601>poskytuje rychlé vícevláknové vkládání pro Neseřazená data. Další informace o vícevláknových typech naleznete v tématu [kdy použít kolekci bezpečnou pro přístup z více vláken](../../../docs/standard/collections/thread-safe/when-to-use-a-thread-safe-collection.md).

- Potřebujete kolekce, které přijímají pouze řetězce?

  - <xref:System.Collections.Specialized.StringCollection>(na základě <xref:System.Collections.IList>) a <xref:System.Collections.Specialized.StringDictionary> (na základě <xref:System.Collections.IDictionary>) jsou v <xref:System.Collections.Specialized> oboru názvů.

  - Kromě toho můžete použít libovolnou z obecných tříd kolekce v <xref:System.Collections.Generic> oboru názvů jako kolekce řetězců silného typu zadáním <xref:System.String> třídy pro jejich obecné typy argumentů. Například můžete deklarovat proměnnou, která má být typu [\<list>](xref:System.Collections.Generic.List%601) nebo [Dictionary<řetězec, String>](xref:System.Collections.Generic.Dictionary%602).

## <a name="linq-to-objects-and-plinq"></a>LINQ to Objects a PLINQ

LINQ to Objects umožňuje vývojářům používat dotazy LINQ pro přístup k objektům v paměti, pokud typ objektu implementuje <xref:System.Collections.IEnumerable> nebo. <xref:System.Collections.Generic.IEnumerable%601> Dotazy LINQ poskytují společný vzor pro přístup k datům, jsou obvykle stručnější a čitelné než standardní `foreach` smyčky a poskytují možnosti filtrování, řazení a seskupování. Další informace naleznete v tématu [LINQ to Objects (C#)](../../csharp/programming-guide/concepts/linq/linq-to-objects.md) a [LINQ to Objects (Visual Basic)](../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md).

PLINQ poskytuje paralelní implementaci LINQ to Objects, která může nabízet rychlejší provádění dotazů v mnoha scénářích, a to díky efektivnějšímu využívání vícejádrových počítačů. Další informace naleznete v tématu [PARALLEL LINQ (PLINQ)](../../../docs/standard/parallel-programming/introduction-to-plinq.md).

## <a name="see-also"></a>Viz také

- <xref:System.Collections>
- <xref:System.Collections.Specialized>
- <xref:System.Collections.Generic>
- [Kolekce bezpečné pro přístup z více vláken](../../../docs/standard/collections/thread-safe/index.md)
