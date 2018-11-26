---
title: Dynamické určování filtrů predikátů při běhu (LINQ v JAZYKU C#)
description: Zjistěte, jak dynamické určování filtrů predikátů při běhu pomocí jazyka LINQ v jazyce C#.
ms.date: 12/1/2016
ms.assetid: 90238470-0767-497c-916c-52d0d16845e0
ms.openlocfilehash: ece5940edd615f30acab06a429de300e27811a66
ms.sourcegitcommit: 35316b768394e56087483cde93f854ba607b63bc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/26/2018
ms.locfileid: "52296071"
---
# <a name="dynamically-specify-predicate-filters-at-runtime"></a>Dynamické určování filtrů predikátů při běhu

V některých případech neznáte až do běhu je nutné použít na zdrojové prvky v tom, kolik predikáty `where` klauzuli. Dynamické určování filtrů více predikátů jedním ze způsobů je použít <xref:System.Linq.Enumerable.Contains%2A> způsob, jak je znázorněno v následujícím příkladu. V příkladu je vytvořen dvěma způsoby. Projekt je nejprve spusťte pomocí filtrování podle hodnoty, které jsou k dispozici v programu. Potom projekt spusťte znovu s použitím vstup v době běhu.

## <a name="to-filter-by-using-the-contains-method"></a>Chcete-li filtrovat pomocí metody obsahuje

1. Otevřete novou konzolovou aplikaci a pojmenujte ho `PredicateFilters`.

2. Kopírovat `StudentClass` třídy z [dotazování na kolekci objektů](query-a-collection-of-objects.md) a vložte ho do oboru názvů `PredicateFilters` pod třídy `Program`. `StudentClass` obsahuje seznam `Student` objekty.

3. Okomentujte `Main` metoda ve `StudentClass`.

4. Změňte třídu `Program` následujícím kódem:

     [!code-csharp[csProgGuideLINQ#26](~/samples/snippets/csharp/concepts/linq/how-to-dynamically-specify-predicate-filters-at-runtime_1.cs)]

5. Přidejte následující řádek, který `Main` metody ve třídě `DynamicPredicates`, v části prohlášení o `ids`.

     ```csharp
     QueryById(ids);
     ```

6. Spusťte projekt.

7. V okně konzoly se zobrazí následující výstup:

     Garcia: 114

     O'Donnell: 112

     Omelchenko: 111

8. Dalším krokem je spusťte projekt znovu, tentokrát pomocí vstup zadaný v době běhu místo pole `ids`. Změna `QueryByID(ids)` k `QueryByID(args)` v `Main` metody.

9. Spustit projekt s argumenty příkazového řádku `122 117 120 115`. Při spuštění projektu, budou tyto hodnoty prvků `args`, parametr `Main` metody.

10. V okně konzoly se zobrazí následující výstup:

     Adams: 120

     Feng: 117

     Garcia: 115

     Tucker: 122

## <a name="to-filter-by-using-a-switch-statement"></a>Chcete-li filtrovat pomocí příkazu switch

1. Můžete použít `switch` příkaz k výběru mezi předdefinovány alternativní dotazy. V následujícím příkladu `studentQuery` používá jiný `where` klauzule v závislosti na tom, které na podnikové úrovni je zadána úroveň nebo rok v době běhu.

2. Následující metodu zkopírujte a vložte jej do třídy `DynamicPredicates`.

     [!code-csharp[csProgGuideLINQ#27](~/samples/snippets/csharp/concepts/linq//how-to-dynamically-specify-predicate-filters-at-runtime_2.cs)]

3. V `Main` metoda, nahraďte volání `QueryByID` s následující volání, která odešle první prvek z `args` pole jako svůj argument: `QueryByYear(args[0])`.

4. Spusťte projekt s argumentem příkazového řádku celočíselnou hodnotu mezi 1 a 4.

## <a name="see-also"></a>Viz také:

- [LINQ (Language Integrated Query)](index.md)
- [where – klauzule](../language-reference/keywords/where-clause.md)
