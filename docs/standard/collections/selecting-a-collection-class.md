---
title: Výběr třídy kolekce
description: Naučte se, jak rozhodnout, kterou třídu kolekce v rozhraní .NET zvolit. Použití nesprávného typu může omezit použití kolekce.
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
ms.openlocfilehash: 52a839661a09d6fa7561d67b82d1c1bf854e3cfd
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84600812"
---
# <a name="selecting-a-collection-class"></a>Výběr třídy kolekce

Nezapomeňte si pečlivě zvolit třídu kolekce. Použití nesprávného typu může omezit použití kolekce.

> [!IMPORTANT]
> Vyhněte se použití typů v <xref:System.Collections> oboru názvů. Obecné a souběžné verze kolekcí se doporučují z důvodu jejich vyšší bezpečnosti typu a dalších vylepšení.

Zvažte následující otázky:

- Potřebujete sekvenční seznam, ve kterém je element obvykle zahozen po načtení jeho hodnoty?

  - Pokud ano, zvažte použití <xref:System.Collections.Queue> třídy nebo <xref:System.Collections.Generic.Queue%601> Obecné třídy, pokud potřebujete chování first-in, First-out (FIFO). Zvažte použití <xref:System.Collections.Stack> třídy nebo <xref:System.Collections.Generic.Stack%601> Obecné třídy, pokud potřebujete chování za poslední, první ven (LIFO). Pro bezpečný přístup z více vláken použijte souběžné verze <xref:System.Collections.Concurrent.ConcurrentQueue%601> a <xref:System.Collections.Concurrent.ConcurrentStack%601> . V případě neměnnosti zvažte neměnné verze <xref:System.Collections.Immutable.ImmutableQueue%601> a <xref:System.Collections.Immutable.ImmutableStack%601> .

  - V takovém případě zvažte použití dalších kolekcí.

- Potřebujete získat přístup k prvkům v určitém pořadí, jako je například FIFO, LIFO nebo Random?

  - <xref:System.Collections.Queue>Třída, jakož i <xref:System.Collections.Generic.Queue%601> <xref:System.Collections.Concurrent.ConcurrentQueue%601> Obecné třídy, a, <xref:System.Collections.Immutable.ImmutableQueue%601> nabízí přístup FIFO. Další informace najdete v tématu [kdy použít kolekci bezpečnou pro přístup z více vláken](thread-safe/when-to-use-a-thread-safe-collection.md).

  - <xref:System.Collections.Stack>Třída, stejně jako <xref:System.Collections.Generic.Stack%601> , <xref:System.Collections.Concurrent.ConcurrentStack%601> a <xref:System.Collections.Immutable.ImmutableStack%601> Obecné třídy, nabízí přístup LIFO. Další informace najdete v tématu [kdy použít kolekci bezpečnou pro přístup z více vláken](thread-safe/when-to-use-a-thread-safe-collection.md).

  - <xref:System.Collections.Generic.LinkedList%601>Obecná třída umožňuje sekvenční přístup buď od pozice k zakončení, nebo od konce k hlavnímu.

- Potřebujete ke každému elementu přistupovat podle indexu?

  - <xref:System.Collections.ArrayList>Třídy a <xref:System.Collections.Specialized.StringCollection> a <xref:System.Collections.Generic.List%601> Obecná třída nabízejí přístup k jejich elementům pomocí indexu založeného na nule elementu. V případě neměnnosti zvažte neměnné obecné verze <xref:System.Collections.Immutable.ImmutableArray%601> a <xref:System.Collections.Immutable.ImmutableList%601> .

  - Třídy,, a a <xref:System.Collections.Hashtable> <xref:System.Collections.SortedList> <xref:System.Collections.Specialized.ListDictionary> <xref:System.Collections.Specialized.StringDictionary> <xref:System.Collections.Generic.Dictionary%602> <xref:System.Collections.Generic.SortedDictionary%602> Obecné třídy nabízejí přístup k jejich elementům pomocí klíče elementu. Kromě toho existují neměnné verze několika odpovídajících typů: <xref:System.Collections.Immutable.ImmutableHashSet%601> , <xref:System.Collections.Immutable.ImmutableDictionary%602> , <xref:System.Collections.Immutable.ImmutableSortedSet%601> a <xref:System.Collections.Immutable.ImmutableSortedDictionary%602> .

  - <xref:System.Collections.Specialized.NameObjectCollectionBase>Třídy a a <xref:System.Collections.Specialized.NameValueCollection> <xref:System.Collections.ObjectModel.KeyedCollection%602> <xref:System.Collections.Generic.SortedList%602> Obecné třídy nabízejí přístup k jejich elementům buď pomocí indexu založeného na nule, nebo klíče elementu.

- Bude každý prvek obsahovat jednu hodnotu, kombinaci jednoho klíče a jednu hodnotu nebo kombinaci jednoho klíče a více hodnot?

  - Jedna hodnota: použijte jakoukoli kolekci založenou na <xref:System.Collections.IList> rozhraní nebo <xref:System.Collections.Generic.IList%601> obecném rozhraní. Pro neměnné možnosti zvažte <xref:System.Collections.Immutable.IImmutableList%601> Obecné rozhraní.

  - Jedna klávesa a jedna hodnota: použijte jakoukoli kolekci založenou na <xref:System.Collections.IDictionary> rozhraní nebo <xref:System.Collections.Generic.IDictionary%602> obecném rozhraní. Pro neměnné možnosti zvažte <xref:System.Collections.Immutable.IImmutableSet%601> <xref:System.Collections.Immutable.IImmutableDictionary%602> Obecná rozhraní nebo.

  - Jedna hodnota s vloženým klíčem: použijte <xref:System.Collections.ObjectModel.KeyedCollection%602> obecnou třídu.

  - Jeden klíč a více hodnot: použijte <xref:System.Collections.Specialized.NameValueCollection> třídu.

- Je nutné prvky seřadit jinak, než byly zadány?

  - <xref:System.Collections.Hashtable>Třída seřadí své prvky podle jejich kódů hash.

  - <xref:System.Collections.SortedList>Třída a <xref:System.Collections.Generic.SortedList%602> <xref:System.Collections.Generic.SortedDictionary%602> Obecné třídy seřadí jejich prvky podle klíče. Pořadí řazení je založeno na implementaci <xref:System.Collections.IComparer> rozhraní pro <xref:System.Collections.SortedList> třídu a implementaci <xref:System.Collections.Generic.IComparer%601> obecného rozhraní pro <xref:System.Collections.Generic.SortedList%602> <xref:System.Collections.Generic.SortedDictionary%602> Obecné třídy a. Ze dvou obecných typů <xref:System.Collections.Generic.SortedDictionary%602> nabízí lepší výkon než <xref:System.Collections.Generic.SortedList%602> , zatímco <xref:System.Collections.Generic.SortedList%602> spotřebovává méně paměti.

  - <xref:System.Collections.ArrayList>poskytuje <xref:System.Collections.ArrayList.Sort%2A> metodu, která přijímá <xref:System.Collections.IComparer> implementaci jako parametr. Jeho obecný protějšek, <xref:System.Collections.Generic.List%601> Obecná třída, poskytuje <xref:System.Collections.Generic.List%601.Sort%2A> metodu, která přebírá implementaci <xref:System.Collections.Generic.IComparer%601> obecného rozhraní jako parametr.

- Potřebujete rychle vyhledávat a načítat informace?

  - <xref:System.Collections.Specialized.ListDictionary>je rychlejší než <xref:System.Collections.Hashtable> u malých kolekcí (10 položek nebo méně). <xref:System.Collections.Generic.Dictionary%602>Obecná třída poskytuje rychlejší vyhledávání než <xref:System.Collections.Generic.SortedDictionary%602> Obecná třída. Vícevláknová implementace je <xref:System.Collections.Concurrent.ConcurrentDictionary%602> . <xref:System.Collections.Concurrent.ConcurrentBag%601>poskytuje rychlé vícevláknové vkládání pro Neseřazená data. Další informace o vícevláknových typech naleznete v tématu [kdy použít kolekci bezpečnou pro přístup z více vláken](thread-safe/when-to-use-a-thread-safe-collection.md).

- Potřebujete kolekce, které přijímají pouze řetězce?

  - <xref:System.Collections.Specialized.StringCollection>(na základě <xref:System.Collections.IList> ) a <xref:System.Collections.Specialized.StringDictionary> (na základě <xref:System.Collections.IDictionary> ) jsou v <xref:System.Collections.Specialized> oboru názvů.

  - Kromě toho můžete použít libovolnou z obecných tříd kolekce v <xref:System.Collections.Generic> oboru názvů jako kolekce řetězců silného typu zadáním <xref:System.String> třídy pro jejich obecné typy argumentů. Například můžete deklarovat proměnnou, která má být typu [seznam \<String> ](xref:System.Collections.Generic.List%601) nebo [slovník<řetězec,>řetězce ](xref:System.Collections.Generic.Dictionary%602).

## <a name="linq-to-objects-and-plinq"></a>LINQ to Objects a PLINQ

LINQ to Objects umožňuje vývojářům používat dotazy LINQ pro přístup k objektům v paměti, pokud typ objektu implementuje <xref:System.Collections.IEnumerable> nebo <xref:System.Collections.Generic.IEnumerable%601> . Dotazy LINQ poskytují společný vzor pro přístup k datům, jsou obvykle stručnější a čitelné než standardní `foreach` smyčky a poskytují možnosti filtrování, řazení a seskupování. Další informace naleznete v tématu [LINQ to Objects (C#)](../../csharp/programming-guide/concepts/linq/linq-to-objects.md) a [LINQ to Objects (Visual Basic)](../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md).

PLINQ poskytuje paralelní implementaci LINQ to Objects, která může nabízet rychlejší provádění dotazů v mnoha scénářích, a to díky efektivnějšímu využívání vícejádrových počítačů. Další informace naleznete v tématu [PARALLEL LINQ (PLINQ)](../parallel-programming/introduction-to-plinq.md).

## <a name="see-also"></a>Viz také

- <xref:System.Collections>
- <xref:System.Collections.Specialized>
- <xref:System.Collections.Generic>
- [Kolekce bezpečné pro přístup z více vláken](thread-safe/index.md)
