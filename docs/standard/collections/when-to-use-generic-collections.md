---
title: Kdy použít generické kolekce
ms.date: 04/30/2020
ms.technology: dotnet-standard
helpviewer_keywords:
- collections [.NET Framework], generic
- generic collections [.NET Framework]
ms.assetid: e7b868b1-11fe-4ac5-bed3-de68aca47739
ms.openlocfilehash: c59a125a8df95e3c4fe6e1839956d800bd6ee910
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290380"
---
# <a name="when-to-use-generic-collections"></a>Kdy použít obecné kolekce

Pomocí obecných kolekcí získáte automatické výhody zabezpečení typu bez nutnosti odvozovat od základní kolekce typu a implementovat členy specifické pro typ. Obecné typy kolekcí také obecně provádějí lepší, než odpovídající typy neobecných kolekcí (a lepší než typy, které jsou odvozeny z neobecné typy kolekce), pokud jsou prvky kolekce typy hodnot, protože s obecnými prvky není nutné pole založit.

Pro programy, které cílí na .NET Standard 1,0 nebo novější, použijte obecné třídy kolekce v <xref:System.Collections.Concurrent> oboru názvů, pokud více vláken může přidat nebo odebrat položky z kolekce současně. Kromě toho, když je žádoucí neměnnosti, zvažte obecné třídy kolekce v <xref:System.Collections.Immutable> oboru názvů.

Následující obecné typy odpovídají existujícím typům kolekcí:

- <xref:System.Collections.Generic.List%601>je obecná třída, která odpovídá <xref:System.Collections.ArrayList> .

- <xref:System.Collections.Generic.Dictionary%602>a <xref:System.Collections.Concurrent.ConcurrentDictionary%602> jsou obecné třídy, které odpovídají <xref:System.Collections.Hashtable> .

- <xref:System.Collections.ObjectModel.Collection%601>je obecná třída, která odpovídá <xref:System.Collections.CollectionBase> . <xref:System.Collections.ObjectModel.Collection%601>lze použít jako základní třídu, ale na rozdíl od <xref:System.Collections.CollectionBase> , není abstraktní, což je mnohem jednodušší ho použít.

- <xref:System.Collections.ObjectModel.ReadOnlyCollection%601>je obecná třída, která odpovídá <xref:System.Collections.ReadOnlyCollectionBase> . <xref:System.Collections.ObjectModel.ReadOnlyCollection%601>není abstraktní a má konstruktor, který usnadňuje vystavení existující <xref:System.Collections.Generic.List%601> jako kolekce jen pro čtení.

- Obecné třídy,,,, a <xref:System.Collections.Generic.Queue%601> <xref:System.Collections.Concurrent.ConcurrentQueue%601> <xref:System.Collections.Immutable.ImmutableQueue%601> <xref:System.Collections.Immutable.ImmutableArray%601> <xref:System.Collections.Generic.SortedList%602> <xref:System.Collections.Immutable.ImmutableSortedSet%601> odpovídají příslušným neobecným třídám se stejnými názvy.

## <a name="additional-types"></a>Další typy

Některé typy obecných kolekcí nemají neobecné protějšky. Jsou to tyto:

- <xref:System.Collections.Generic.LinkedList%601>je obecný propojený seznam, který poskytuje operace O vkládání a odebírání.

- <xref:System.Collections.Generic.SortedDictionary%602>je setříděný slovník s `n` operacemi vkládání a načítání, což usnadňuje možnost použít pro <xref:System.Collections.Generic.SortedList%602> .

- <xref:System.Collections.ObjectModel.KeyedCollection%602>je hybrid mezi seznamem a slovníkem, který poskytuje způsob ukládání objektů, které obsahují vlastní klíče.

- <xref:System.Collections.Concurrent.BlockingCollection%601>implementuje třídu kolekce s funkcí ohraničování a blokování.

- <xref:System.Collections.Concurrent.ConcurrentBag%601>poskytuje rychlé vkládání a odebírání neuspořádaných prvků.

### <a name="immutable-builders"></a>Neměnné tvůrci

Pokud si přejete, aby neměnnosti funkce v aplikaci, <xref:System.Collections.Immutable> obor názvů nabízí obecné typy kolekce, které můžete použít. Všechny typy neměnné kolekce nabízí `Builder` třídy, které mohou optimalizovat výkon při provádění více mutací. `Builder`Operace dávek třídy v proměnlivém stavu. Po dokončení všech mutací volejte `ToImmutable` metodu pro zablokování všech uzlů a vytvořte neměnné obecné kolekce, například <xref:System.Collections.Immutable.ImmutableList%601> .

`Builder`Objekt lze vytvořit voláním neobecné `CreateBuilder()` metody. Z `Builder` instance můžete zavolat `ToImmutable()` . Podobně z `Immutable*` kolekce můžete zavolat `ToBuilder()` pro vytvoření instance Tvůrce z obecné neměnné kolekce. Následují různé `Builder` typy.

- <xref:System.Collections.Immutable.ImmutableArray%601.Builder>
- <xref:System.Collections.Immutable.ImmutableDictionary%602.Builder>
- <xref:System.Collections.Immutable.ImmutableHashSet%601.Builder>
- <xref:System.Collections.Immutable.ImmutableList%601.Builder>
- <xref:System.Collections.Immutable.ImmutableSortedDictionary%602.Builder>
- <xref:System.Collections.Immutable.ImmutableSortedSet%601.Builder>

## <a name="linq-to-objects"></a>LINQ na objekty

Funkce LINQ to Objects umožňuje používat dotazy LINQ pro přístup k objektům v paměti, pokud typ objektu implementuje <xref:System.Collections.IEnumerable?displayProperty=nameWithType> <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> rozhraní nebo. Dotazy LINQ poskytují společný vzor pro přístup k datům; jsou obvykle stručnější a čitelné než standardní `foreach` smyčky a poskytují možnosti filtrování, řazení a seskupování. Dotazy LINQ mohou také zlepšit výkon. Další informace naleznete v tématu [LINQ to Objects (C#)](../../csharp/programming-guide/concepts/linq/linq-to-objects.md), [LINQ to Objects (Visual Basic)](../../visual-basic/programming-guide/concepts/linq/linq-to-objects.md)a [Paralelní LINQ (PLINQ)](../parallel-programming/introduction-to-plinq.md).

## <a name="additional-functionality"></a>Další funkce
Některé obecné typy mají funkce, které se nenašly v neobecných typech kolekcí. Například <xref:System.Collections.Generic.List%601> třída, která odpovídá neobecné <xref:System.Collections.ArrayList> třídě, má řadu metod, které přijímají Obecné delegáty, jako je <xref:System.Predicate%601> delegát, který umožňuje určit metody pro hledání seznamu, <xref:System.Action%601> delegáta, který představuje metody, které fungují na jednotlivých prvcích seznamu, a <xref:System.Converter%602> delegát, který umožňuje definovat převody mezi typy.

<xref:System.Collections.Generic.List%601>Třída umožňuje zadat vlastní <xref:System.Collections.Generic.IComparer%601> implementace obecného rozhraní pro řazení a hledání v seznamu. <xref:System.Collections.Generic.SortedDictionary%602> <xref:System.Collections.Generic.SortedList%602> Tato funkce má také třídy a. Kromě toho umožňují tyto třídy při vytváření kolekce určit porovnávače. Podobným způsobem <xref:System.Collections.Generic.Dictionary%602> <xref:System.Collections.ObjectModel.KeyedCollection%602> třídy a umožňují zadat vlastní porovnávače rovnosti.

## <a name="see-also"></a>Viz také

- [Kolekce a datové struktury](index.md)
- [Běžně používané typy kolekcí](commonly-used-collection-types.md)
- [Obecné typy](../generics/index.md)
