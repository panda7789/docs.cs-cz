---
title: Dynamické určování filtrů predikátů při běhu
description: Jak dynamické určování filtrů predikátů při běhu.
ms.date: 12/1/2016
ms.assetid: 90238470-0767-497c-916c-52d0d16845e0
ms.openlocfilehash: fa3426a513758d8c30bf381ec480b9b8d12a5f81
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33287937"
---
# <a name="dynamically-specify-predicate-filters-at-runtime"></a>Dynamické určování filtrů predikátů při běhu

V některých případech si nejste jisti, dokud běhu musíte použít zdrojové elementy v tom, kolik predikáty `where` klauzule. Dynamické určování filtrů několik predikátů jedním ze způsobů je používat <xref:System.Linq.Enumerable.Contains%2A> metoda, jak je znázorněno v následujícím příkladu. V příkladu je vytvořen dvěma způsoby. Nejprve spustit projekt na filtrování na hodnotách, které jsou součástí programu. Projekt je pak spusťte znovu pomocí vstup za běhu.  
  
## <a name="to-filter-by-using-the-contains-method"></a>Chcete-li filtrovat pomocí metody obsahuje  
  
1.  Otevřete novou konzolovou aplikaci a pojmenujte ji `PredicateFilters`.  
  
2.  Kopírování `StudentClass` třídy z [dotazování na kolekci objektů](query-a-collection-of-objects.md) a vložte jej do oboru názvů `PredicateFilters` pod Třída `Program`. `StudentClass` obsahuje seznam `Student` objekty.  
  
3.  Komentář `Main` metoda v `StudentClass`.  
  
4.  Změňte třídu `Program` následujícím kódem.  
  
     [!code-csharp[csProgGuideLINQ#26](../../../samples/snippets/csharp/concepts/linq/how-to-dynamically-specify-predicate-filters-at-runtime_1.cs)]  
  
5.  Přidejte následující řádek na `Main` metodu v třídě `DynamicPredicates`, v části prohlášení o `ids`.  
  
     ```csharp
     QueryById(ids);
     ```

6.  Spusťte projekt.  
  
7.  V okně konzoly se zobrazí následující výstup:  
  
     Garcia: 114  
  
     O'Donnell: 112  
  
     Omelchenko: 111  
  
8.  Dalším krokem je spusťte projekt znovu, tentokrát pomocí vstup zadaný v době běhu místo pole `ids`. Změna `QueryByID(ids)` k `QueryByID(args)` v `Main` metoda.  
  
9. Spusťte projekt s argumenty příkazového řádku `122 117 120 115`. Při spuštění projektu tyto hodnoty stát prvky `args`, parametr `Main` metoda...  
  
10. V okně konzoly se zobrazí následující výstup:  
  
     Adams: 120.  
  
     Feng: 117  
  
     Garcia: 115  
  
     Tucker: 122  
  
## <a name="to-filter-by-using-a-switch-statement"></a>Chcete-li filtrovat pomocí příkazu switch  
  
1.  Můžete použít `switch` příkaz chcete vybrat z předem určeny alternativní dotazy. V následujícím příkladu `studentQuery` používá jiné `where` klauzule v závislosti na tom, které úrovni úroveň nebo rok, je zadána v době běhu.  
  
2.  Zkopírujte následující metodu a vložte ho do třídy `DynamicPredicates`.  
  
     [!code-csharp[csProgGuideLINQ#27](../../../samples/snippets/csharp/concepts/linq//how-to-dynamically-specify-predicate-filters-at-runtime_2.cs)]  
  
3.  V `Main` metoda, nahraďte volání `QueryByID` s následující volání, která odešle první prvek z `args` pole jako její argument: `QueryByYear(args[0])`.  
  
4.  Spusťte projekt s argumentem příkazového řádku ve celočíselnou hodnotu mezi 1 a 4.  
  
 
## <a name="see-also"></a>Viz také  
 [LINQ – výrazy dotazů](index.md)  
 [where – klauzule](../language-reference/keywords/where-clause.md)
